---
title: Inhaltssuche und -indizierung
description: Inhaltssuche und -indizierung
translation-type: tm+mt
source-git-commit: c915580247e1b99db8a9f5228eec8cffece8a003
workflow-type: tm+mt
source-wordcount: '1521'
ht-degree: 100%

---


# Inhaltssuche und -indizierung {#indexing}

## Änderungen in AEM as a Cloud Service {#changes-in-aem-as-a-cloud-service}

Mit AEM as a Cloud Service stellt Adobe von einem AEM-Instanz-zentrierten Modell auf eine Service-basierte Ansicht mit n-x AEM-Containern um, unterstützt von CI/CD-Pipelines in Cloud Manager. Anstatt Indizes für einzelne AEM-Instanzen zu konfigurieren und zu verwalten, muss die Indexkonfiguration vor der Implementierung angegeben werden. Konfigurationsänderungen in der Produktion verstoßen eindeutig gegen CI/CD-Richtlinien. Dasselbe gilt für Indexänderungen, da sie sich auf die Systemstabilität und -leistung auswirken können, wenn sie nicht speziell getestet werden, bevor sie in die Produktion aufgenommen werden.

Nachstehend finden Sie eine Liste der wichtigsten Änderungen im Vergleich zu AEM 6.5 und früheren Versionen:

1. Anwender haben keinen Zugriff mehr auf den Index-Manager einer einzelnen AEM-Instanz, wenn sie die Indizierung debuggen, konfigurieren oder verwalten möchten. Er wird nur für lokale Entwicklungsumgebungen und On-Premise-Implementierungen verwendet.

1. Anwender werden Indizes nicht in einer einzelnen AEM-Instanz ändern; außerdem müssen sie sich keine Gedanken mehr über Konsistenzprüfungen oder Neuindizierungen machen.

1. In der Regel werden Indexänderungen vor der Produktion eingeleitet, um Qualitäts-Gateways in den CI/CD-Pipelines von Cloud Manager nicht zu umgehen und geschäftliche KPIs in der Produktion nicht zu beeinträchtigen.

1. Alle damit zusammenhängenden Metriken, einschließlich der Suchleistung in der Produktion, stehen Kunden zur Laufzeit zur Verfügung, um eine ganzheitliche Ansicht der Themen Suche und Indizierung zu erhalten.

1. Kunden können entsprechend ihren Bedürfnissen Warnungen einrichten.

1. SREs überwachen den Systemzustand rund um die Uhr und ergreifen bei Bedarf so früh wie möglich Maßnahmen.

1. Die Indexkonfiguration wird über Implementierungen geändert. Änderungen an der Indexdefinition werden wie andere Inhaltsänderungen konfiguriert.

1. Auf einer übergeordneten Ebene von AEM as a Cloud Service wird es mit der Einführung des [Blau/Grün-Implementierungsmodells](#index-management-using-blue-green-deployments) zwei Indexsätze geben: einen Satz für die alte Version (blau) und einen Satz für die neue Version (grün).

1. Kunden können überprüfen, ob der Indizierungsauftrag auf der Build-Seite von Cloud Manager abgeschlossen wurde, und erhalten eine Benachrichtigung, sobald die neue Version Traffic aufnehmen kann.

1. Einschränkungen: Derzeit wird die Indexverwaltung in AEM as a Cloud Service nur für Indizes des Typs Lucene unterstützt.

## Verwendung {#how-to-use}

Eine Definition von Indizes kann drei Anwendungsfälle umfassen:

1. Hinzufügen einer neuen kundenspezifischen Indexdefinition.
1. Aktualisieren einer vorhandenen Indexdefinition. Das bedeutet effektiv, einer vorhandenen Indexdefinition eine neue Version hinzuzufügen.
1. Entfernen eines vorhandenen Index, der redundant oder veraltet ist.

Für die Punkte 1 und 2 müssen Sie als Teil Ihrer benutzerspezifischen Code-Basis im jeweiligen Release-Plan für Cloud Manager eine neue Indexdefinition erstellen. Weitere Informationen finden Sie in der Dokumentation [Bereitstellen in AEM as a Cloud Service](/help/implementing/deploying/overview.md).

### Vorbereiten der neuen Indexdefinition {#preparing-the-new-index-definition}

Sie müssen ein neues Indexdefinitionspaket erstellen, das die tatsächliche Indexdefinition gemäß folgendem Benennungsmuster enthält:

`<indexName>[-<productVersion>]-custom-<customVersion>`

das dann unter `ui.apps/src/main/content/jcr_root` aufgeführt werden muss. Unterstammordner werden ab sofort nicht mehr unterstützt.

Das Paket aus dem obigen Beispiel wird als `com.adobe.granite:new-index-content:zip:1.0.0-SNAPSHOT` erstellt.

### Bereitstellen von Indexdefinitionen {#deploying-index-definitions}

>[!NOTE]
>
>Es gibt ein bekanntes Problem mit Jackrabbit Filevault Maven Package Plugin Version **1.1.0**, das es Ihnen unmöglich macht, `oak:index` zu Modulen von `<packageType>application</packageType>` hinzuzufügen. Um dieses Problem zu umgehen, verwenden Sie Version **1.0.4**.

Indexdefinitionen werden jetzt als benutzerdefiniert und versioniert gekennzeichnet:

* Die Indexdefinition selbst (z. B. `/oak:index/ntBaseLucene-custom-1`)

Um einen Index bereitzustellen, muss die Indexdefinition (`/oak:index/definitionname`) daher via `ui.apps` über Git und das Cloud Manager-Implementierungsverfahren bereitgestellt werden.

Nachdem die neue Indexdefinition hinzugefügt wurde, muss die neue Anwendung über Cloud Manager bereitgestellt werden. Bei der Implementierung werden zwei Aufträge gestartet, die für das Hinzufügen (und gegebenenfalls das Zusammenführen) der Indexdefinitionen zu MongoDB und Azure Segment Store verantwortlich sind (für Erstellungs- bzw. Veröffentlichungszwecke). Die zugrunde liegenden Repositorys werden mit den neuen Indexdefinitionen neu indiziert, bevor die Blau/Grün-Umstellung stattfindet.

>[!TIP]
>
>Weitere Informationen zur erforderlichen Paketstruktur für AEM as a Cloud Service finden Sie im Dokument [AEM-Projektstruktur](/help/implementing/developing/introduction/aem-project-content-package-structure.md).

## Indexverwaltung unter Verwendung von Blau/Grün-Implementierungen {#index-management-using-blue-green-deployments}

### Was ist Indexverwaltung? {#what-is-index-management}

Bei der Indexverwaltung geht es darum, Indizes hinzuzufügen, zu entfernen und zu ändern. Eine Änderung der *Definition* eines Index geht schnell, doch die Anwendung der Änderung (häufig als „Erstellen eines Index“ oder bei vorhandenen Indizes als „Neuindizierung“ bezeichnet) erfordert Zeit. Das geht nicht sofort: Das Repository muss zunächst auf zu indizierende Daten geprüft werden.

### Was ist eine Blau/Grün-Implementierung? {#what-is-blue-green-deployment}

Eine Blau/Grün-Implementierung kann Ausfallzeiten reduzieren. Sie ermöglicht Upgrades ohne Ausfallzeiten sowie schnelle Rollbacks. Die alte Version der Anwendung (blau) wird gleichzeitig mit der neuen Version der Anwendung (grün) ausgeführt.

### Schreibgeschützte Bereiche und Bereiche mit Lese-Schreib-Zugriff {#read-only-and-read-write-areas}

Bestimmte Bereiche des Repositorys (schreibgeschützte Teile des Repositorys) können sich in der alten (blauen) und der neuen (grünen) Version der Anwendung unterscheiden. Die schreibgeschützten Bereiche des Repositorys sind in der Regel `/app` und `/libs`. Im folgenden Beispiel wird Kursivschrift verwendet, um schreibgeschützte Bereiche zu markieren, während Fettschrift für Bereiche mit Lese-Schreib-Zugriff steht.

* **/**
* */apps (schreibgeschützt)*
* **/content**
* */libs (schreibgeschützt)*
* **/oak:index**
* **/oak:index/acme.**
* **/jcr:system**
* **/system**
* **/var**

Die Bereiche mit Lese- und Schreibzugriff des Repositorys werden von allen Versionen der Anwendung gemeinsam genutzt, während es für jede Version der Anwendung einen spezifischen Satz von `/apps` und `/libs` gibt.

### Indexverwaltung ohne Blau/Grün-Implementierung {#index-management-without-blue-green-deployment}

Bei der Entwicklung oder bei Verwendung von lokalen Installationen können Indizes zur Laufzeit hinzugefügt, entfernt oder geändert werden. Indizes werden verwendet, sobald sie verfügbar sind. Wenn ein Index noch nicht in der alten Version der Anwendung verwendet werden soll, wird der Index normalerweise während einer geplanten Ausfallzeit erstellt. Dasselbe gilt, wenn ein Index entfernt oder ein vorhandener Index geändert wird. Wenn Sie einen Index entfernen, steht er sofort nach der Entfernung nicht mehr zur Verfügung.

### Indexverwaltung mit Blau/Grün-Implementierung {#index-management-with-blue-green-deployment}

Bei Blau/Grün-Implementierungen gibt es keine Ausfallzeiten. Für die Indexverwaltung ist es jedoch erforderlich, dass Indizes nur von bestimmten Versionen der Anwendung verwendet werden. Wenn Sie beispielsweise einen Index in Version 2 der Anwendung hinzufügen, sollte dieser noch nicht von Version 1 der Anwendung genutzt werden. Das Gegenteil ist der Fall, wenn ein Index entfernt wird: Ein in Version 2 entfernter Index wird in Version 1 weiterhin benötigt. Beim Ändern einer Indexdefinition soll die alte Version des Index nur für Version 1 verwendet werden; die neue Version des Index soll nur für Version 2 genutzt werden.

Die folgende Tabelle zeigt fünf Indexdefinitionen: Index `cqPageLucene` wird in beiden Versionen verwendet, während Index `damAssetLucene-custom-1` nur in Version 2 zum Einsatz kommt.

>[!NOTE]
>
>`<indexName>-custom-<customerVersionNumber>` ist erforderlich, damit AEM as a Cloud Service das als Ersatz für einen vorhandenen Index kennzeichnen kann.

| Index | Vordefinierter Index | Verwendung in Version 1 | Verwendung in Version 2 |
|---|---|---|---|
| /oak:index/damAssetLucene | Ja | Ja | Nein |
| /oak:index/damAssetLucene-custom-1 | Ja (angepasst) | Nein | Ja |
| /oak:index/acme.product-custom-1 | Nein | Ja | Nein |
| /oak:index/acme.product-custom-2 | Nein | Nein | Ja |
| /oak:index/cqPageLucene | Ja | Ja | Ja |

Die Versionsnummer wird bei jeder Indexänderung inkrementiert. Um zu vermeiden, dass benutzerspezifische Indexnamen mit den Indexnamen des Produkts selbst kollidieren, müssen benutzerspezifische Indizes sowie Änderungen an vordefinierten Indizes mit `-custom-<number>` enden.

### Änderungen an vordefinierten Indizes {#changes-to-out-of-the-box-indexes}

Sobald Adobe einen vordefinierten Index wie „damAssetLucene“ oder „cqPageLucene“ ändert, wird ein neuer Index mit dem Namen `damAssetLucene-2` oder `cqPageLucene-2` erstellt; falls der Index bereits angepasst wurde, wird die benutzerdefinierte Indexdefinition mit den Änderungen im vordefinierten Index zusammengeführt (wie unten dargestellt). Die Zusammenführung von Änderungen erfolgt automatisch. Das bedeutet, dass Sie nichts tun müssen, wenn sich ein vordefinierter Index ändert. Der Index lässt sich jedoch später erneut anpassen.

| Index | Vordefinierter Index | Verwendung in Version 2 | Verwendung in Version 3 |
|---|---|---|---|
| /oak:index/damAssetLucene-custom-1 | Ja (angepasst) | Ja | Nein |
| /oak:index/damAssetLucene-2-custom-1 | Ja (automatisch aus „damAssetLucene-custom-1“ und „damAssetLucene-2“ zusammengeführt) | Nein | Ja |
| /oak:index/cqPageLucene | Ja | Ja | Nein |
| /oak:index/cqPageLucene-2 | Ja | Nein | Ja |

### Beschränkungen {#limitations}

Die Indexverwaltung wird derzeit nur für Indizes vom Typ `lucene` unterstützt.

### Entfernen eines Index {#removing-an-index}

Wenn ein Index in einer späteren Version der Anwendung entfernt werden soll, können Sie einen leeren Index (einen Index ohne zu indizierende Daten) mit einem neuen Namen definieren. Sie können ihn beispielsweise `/oak:index/acme.product-custom-3` nennen. Dadurch wird der Index `/oak:index/acme.product-custom-2` ersetzt. Nachdem das System `/oak:index/acme.product-custom-2` entfernt hat, kann auch der leere Index `/oak:index/acme.product-custom-3` entfernt werden.

### Hinzufügen eines Index {#adding-an-index}

Um einen Index mit dem Namen „/oak:index/acme.product-custom-1“ hinzuzufügen, der in einer neuen Version der Anwendung und höher verwendet werden soll, muss der Index wie folgt konfiguriert werden:

`acme.product-1-custom-1`

Dies funktioniert, indem dem Indexnamen eine benutzerdefinierte Kennung vorangestellt wird, gefolgt von einem Punkt (**`.`**). Die Kennung muss zwischen 2 und 5 Zeichen lang sein.

Wie oben gezeigt, wird sichergestellt, dass der Index nur von der neuen Version der Anwendung verwendet wird.

### Ändern eines Index {#changing-an-index}

Wenn ein vorhandener Index geändert wird, muss ein neuer Index mit der geänderten Indexdefinition hinzugefügt werden. Angenommen, der vorhandene Index „/oak:index/acme.product-custom-1“ wird geändert. Der alte Index wird unter `/oak:index/acme.product-custom-1`, der neue Index unter `/oak:index/acme.product-custom-2` gespeichert.

Die alte Version der Anwendung nutzt die folgende Konfiguration:

`/oak:index/acme.product-custom-1`

Die neue Version der Anwendung nutzt die folgende (geänderte) Konfiguration:

`/oak:index/acme.product-custom-2`

### Indexverfügbarkeit/Fehlertoleranz {#index-availability}

Es wird empfohlen, für Funktionen, die besonders wichtig sind, Duplikate von Indizes zu erstellen (unter Berücksichtigung der oben genannten Benennungsregel für Indizes). So steht bei Beschädigung eines Index oder einem ähnlichen unvorhergesehenen Ereignis ein Fallback-Index zur Verfügung, sodass auf Abfragen reagiert werden kann.
