---
title: Inhaltssuche und -indizierung
description: Inhaltssuche und -indizierung
translation-type: tm+mt
source-git-commit: 0d83e1d956d65fe27b1cf7bce758fc7fa8adf6b2
workflow-type: tm+mt
source-wordcount: '1430'
ht-degree: 3%

---


# Inhaltssuche und -indizierung {#indexing}

## Änderungen in AEM als Cloud-Dienst {#changes-in-aem-as-a-cloud-service}

Mit AEM als Cloud-Dienst verlagert Adobe von einem AEM-Instanzenmodell zu einer dienstbasierten Ansicht mit n-x-AEM-Containern, die von CI/CD-Pipelines im Cloud Manager gesteuert wird. Statt Indizes für einzelne AEM-Instanzen zu konfigurieren und zu verwalten, muss die Indexkonfiguration vor einer Bereitstellung angegeben werden. Konfigurationsänderungen in der Produktion brechen eindeutig die CI/CD-Richtlinien. Dasselbe gilt für Indexänderungen, da sie sich auf die Systemstabilität und -leistung auswirken können, wenn sie nicht spezifiziert sind, bevor sie in die Produktion aufgenommen werden.

Nachstehend eine Liste der wichtigsten Änderungen im Vergleich zu AEM 6.5 und früheren Versionen:

1. Benutzer haben keinen Zugriff auf den Index-Manager einer einzelnen AEM-Instanz, um die Indexierung zu debuggen, zu konfigurieren oder zu verwalten. Es wird nur für lokale Entwicklungs- und Bereitstellungen vor Ort verwendet.

1. Benutzer ändern die Indizes nicht auf einer einzigen AEM-Instanz, und sie müssen sich auch keine Gedanken mehr über Konsistenzprüfungen oder das erneute Dekodieren machen.

1. In der Regel werden Indexänderungen vor der Produktion eingeleitet, um Qualitätssicherungen in den CI/CD-Pipelines von Cloud Manager nicht zu umgehen und keine Auswirkungen auf die Business KPIs in der Produktion zu haben.

1. Alle damit zusammenhängenden Metriken, einschließlich der Suchleistung in der Produktion, stehen Kunden zur Laufzeit zur Verfügung, um die ganzheitliche Ansicht zu den Themen Suche und Indizierung bereitzustellen.

1. Kunden können Warnungen entsprechend ihren Bedürfnissen einrichten.

1. Die SRE überwachen den Systemzustand rund um die Uhr und werden nach Bedarf und so früh wie möglich Maßnahmen ergreifen.

1. Die Indexkonfiguration wird über Bereitstellungen geändert. Änderungen der Indexdefinition werden wie andere Inhaltsänderungen konfiguriert.

1. Auf einer hohen Ebene von AEM als Cloud-Dienst werden mit der Einführung des [Blue-Green-Bereitstellungsmodells](#index-management-using-blue-green-deployments) zwei Indizes vorhanden sein: ein Set für die alte Version (blau) und ein Set für die neue Version (grün).

<!-- The version of the index that is used is configured using flags in the index definitions via the `useIfExist` flag. An index may be used in only one version of the application (for example only blue or only green), or in both versions. Detailed documentation is available at [Index Management using Blue-Green Deployments](#index-management-using-blue-green-deployments). -->

1. Kunden können sehen, ob der Indexierungsauftrag auf der Buildseite von Cloud Manager abgeschlossen ist, und erhalten eine Benachrichtigung, wenn die neue Version Traffic aufnehmen kann.

1. Einschränkungen: Derzeit wird die Indexverwaltung für AEM als Cloud-Dienst nur für Indizes vom Typ lucene unterstützt.

<!-- ## Sizing Considerations {#sizing-considerations}

AEM as a Cloud Service comes with a default capacity model to provide sufficient performance for average web applications. This "average" measure relates to the repository size and even more relevant to the indexing size. If we have reasons to believe that we need extended capacity for a specific customer project, an evaluation with SREs and Engineering will take place to determine the required capacity settings.

AS NOTE: the above is internal for now.

-->

## Verwendung {#how-to-use}

Die Definition von Indizes kann aus drei Anwendungsfällen bestehen:

1. Hinzufügen einer neuen Kunden-Indexdefinition
1. Aktualisieren einer vorhandenen Indexdefinition. Dies bedeutet effektiv, eine neue Version einer vorhandenen Indexdefinition hinzuzufügen.
1. Entfernen eines vorhandenen, redundanten oder veralteten Indexes

Für die beiden obigen Punkte 1 und 2 müssen Sie eine neue Indexdefinition als Teil Ihrer benutzerspezifischen Codebasis im jeweiligen Cloud Manager-Veröffentlichungsplan erstellen. Weitere Informationen finden Sie in der Dokumentation [zur](/help/implementing/deploying/overview.md)Bereitstellung auf AEM als Cloud-Dienst.

### Vorbereiten der neuen Indexdefinition {#preparing-the-new-index-definition}

Sie müssen ein neues Indexdefinitionspaket mit der tatsächlichen Indexdefinition gemäß folgendem Benennungsmuster erstellen:

`<indexName>[-<productVersion>]-custom-<customVersion>`

die dann untergehen müssen `ui.apps/src/main/content/jcr_root`. Unterstammordner werden ab sofort nicht mehr unterstützt.

<!-- need to review and link info on naming convention from https://wiki.corp.adobe.com/display/WEM/Merging+Customer+and+OOTB+Index+Changes?focusedCommentId=1784917629#comment-1784917629 -->

Das Paket aus dem obigen Beispiel wird wie `com.adobe.granite:new-index-content:zip:1.0.0-SNAPSHOT`folgt erstellt.

### Bereitstellen von Indexdefinitionen {#deploying-index-definitions}

>[!NOTE]
>
> Es gibt ein bekanntes Problem mit Jackrabbit Filevault Maven Package Plugin Version **1.1.0** , das es Ihnen nicht erlaubt, `oak:index` zu Modulen von hinzuzufügen `<packageType>application</packageType>`. Um dies zu umgehen, verwenden Sie bitte Version **1.0.4**.

Indexdefinitionen sind jetzt als benutzerdefiniert und als Version gekennzeichnet:

* Die Indexdefinition selbst (z. B. `/oak:index/ntBaseLucene-custom-1`)

Um einen Index bereitzustellen, muss die Indexdefinition (`/oak:index/definitionname`) daher über Git und den `ui.apps` Cloud Manager-Bereitstellungsprozess bereitgestellt werden.

Nachdem die neue Indexdefinition hinzugefügt wurde, muss die neue Anwendung über Cloud Manager bereitgestellt werden. Bei der Bereitstellung werden zwei Aufträge gestartet, die für das Hinzufügen (und gegebenenfalls das Zusammenführen) der Indexdefinitionen zu MongoDB bzw. dem Azurblauen Segment Store für Autoren- bzw. Veröffentlichungszwecke verantwortlich sind. Die zugrunde liegenden Repositorys werden mit den neuen Indexdefinitionen neu deklariert, bevor der Blue-Green-Switch stattfindet.

## Indexverwaltung unter Verwendung von Blue-Green-Bereitstellungen {#index-management-using-blue-green-deployments}

### Was ist Indexverwaltung {#what-is-index-management}

Bei der Indexverwaltung geht es darum, Indizes hinzuzufügen, zu entfernen und zu ändern. Die Änderung der *Definition* eines Indexes ist schnell, aber die Anwendung der Änderung (häufig als &quot;Erstellen eines Indexes&quot;oder bei vorhandenen Indizes als &quot;Neudexing&quot;bezeichnet) erfordert Zeit. Es handelt sich nicht sofort: Das Repository muss gescannt werden, damit Daten indiziert werden.

### Was ist eine blaugrüne Implementierung {#what-is-blue-green-deployment}

Eine blaugrüne Implementierung kann Ausfallzeiten reduzieren. Es ermöglicht außerdem eine kostenlose Aktualisierung der Ausfallzeiten und bietet schnelle Rückläufe. Die alte Version der Anwendung (blau) wird gleichzeitig mit der neuen Version der Anwendung ausgeführt (grün).

### Schreibgeschützte und schreibgeschützte Bereiche {#read-only-and-read-write-areas}

Bestimmte Bereiche des Repositorys (schreibgeschützte Teile des Repositorys) können in der alten (blauen) und in der neuen (grünen) Version der Anwendung unterschiedlich sein. Die schreibgeschützten Bereiche des Repositorys sind in der Regel &quot;`/app`&quot;und &quot;`/libs`&quot;. Im folgenden Beispiel wird kursiv verwendet, um schreibgeschützte Bereiche zu markieren, während fett für schreibgeschützte Bereiche verwendet wird.

* **/**
* */apps (schreibgeschützt)*
* **/content**
* */libs (schreibgeschützt)*
* **/oak:index**
* **/oak:index/acme**
* **/jcr:system**
* **/system**
* **/var**

Die Lese- und Schreibbereiche des Repositorys werden von allen Versionen der Anwendung gemeinsam genutzt, während für jede Version der Anwendung ein bestimmter Satz `/apps` und `/libs`eine bestimmte Zeichenfolge vorhanden ist.

### Indexverwaltung ohne blaugrüne Bereitstellung {#index-management-without-blue-green-deployment}

Während der Entwicklung oder bei Verwendung von lokalen Installationen können Indizes zur Laufzeit hinzugefügt, entfernt oder geändert werden. Indizes werden verwendet, sobald sie verfügbar sind. Wenn ein Index in der alten Version der Anwendung noch nicht verwendet werden soll, wird der Index normalerweise während eines geplanten Ausfalls erstellt. Dasselbe gilt, wenn ein Index entfernt oder ein vorhandener Index geändert wird. Wenn Sie einen Index entfernen, steht er nicht mehr zur Verfügung, sobald er entfernt wurde.

### Indexverwaltung mit blaugrüner Implementierung {#index-management-with-blue-green-deployment}

Bei blau-grünen Implementierungen gibt es keine Ausfallzeiten. Für die Indexverwaltung ist es jedoch erforderlich, dass Indizes nur von bestimmten Versionen der Anwendung verwendet werden. Wenn Sie beispielsweise einen Index in Version 2 der Anwendung hinzufügen, sollte dieser noch nicht in Version 1 der Anwendung verwendet werden. Das Gegenteil ist der Fall, wenn ein Index entfernt wird: ein in Version 2 entfernter Index wird in Version 1 weiterhin benötigt. Beim Ändern einer Indexdefinition sollte die alte Version des Indexes nur für Version 1 verwendet werden, und die neue Version des Indexes darf nur für Version 2 verwendet werden.

Die folgende Tabelle zeigt fünf Indexdefinitionen: Index `cqPageLucene` wird in beiden Versionen verwendet, während Index nur in Version 2 verwendet `damAssetLucene-custom-1` wird.

>[!NOTE]
>
> `<indexName>-custom-<customerVersionNumber>` wird benötigt, damit AEM als Cloud-Dienst als Ersatz für einen vorhandenen Index markiert wird.

| Index | Vordefinierter Index | Verwendung in Version 1 | Verwendung in Version 2 |
|---|---|---|---|
| /oak:index/damAssetLucene | Ja | Ja | Nein |
| /oak:index/damAssetLucene-custom-1 | Ja (angepasst) | Nein | Ja |
| /oak:index/acmeProduct-custom-1 | Nein | Ja | Nein |
| /oak:index/acmeProduct-custom-2 | Nein | Nein | Ja |
| /oak:index/cqPageLucene | Ja | Ja | Ja |

Die Versionsnummer wird bei jeder Indexänderung inkrementiert. Um zu vermeiden, dass benutzerspezifische Indexnamen mit den Indexnamen des Produkts selbst kollidieren, müssen benutzerspezifische Indizes sowie Änderungen an vordefinierten Indizes mit enden `-custom-<number>`.

### Änderungen an den vordefinierten Indizes {#changes-to-out-of-the-box-indexes}

Sobald Adobe einen vordefinierten Index wie &quot;damAssetLucene&quot;oder &quot;cqPageLucene&quot;ändert, wird ein neuer Index mit dem Namen `damAssetLucene-2` oder `cqPageLucene-2` erstellt oder, falls der Index bereits angepasst wurde, die benutzerdefinierte Indexdefinition mit den Änderungen im vordefinierten Index zusammengeführt, wie unten dargestellt. Die Zusammenführung von Änderungen erfolgt automatisch. Das bedeutet, dass Sie nichts tun müssen, wenn sich ein vordefinierter Index ändert. Der Index kann jedoch später erneut angepasst werden.

| Index | Vordefinierter Index | Verwendung in Version 2 | Verwendung in Version 3 |
|---|---|---|---|
| /oak:index/damAssetLucene-custom-1 | Ja (angepasst) | Ja | Nein |
| /oak:index/damAssetLucene-2-custom-1 | Ja (automatisch aus damAssetLucene-custom-1 und damAssetLucene-2 zusammengeführt) | Nein | Ja |
| /oak:index/cqPageLucene | Ja | Ja | Nein |
| /oak:index/cqPageLucene-2 | Ja | Nein | Ja |

### Beschränkungen {#limitations}

Die Indexverwaltung wird derzeit nur für Indizes vom Typ `lucene`.

### Entfernen eines Indexes {#removing-an-index}

Wenn ein Index in einer späteren Version der Anwendung entfernt werden soll, können Sie einen leeren Index (einen Index ohne zu indexierende Daten) mit einem neuen Namen definieren. Sie können ihn beispielsweise benennen `/oak:index/acmeProduct-custom-3`. Dadurch wird der Index ersetzt `/oak:index/acmeProduct-custom-2`. Nach dem Entfernen durch das System `/oak:index/acmeProduct-custom-2` `/oak:index/acmeProduct-custom-3` kann auch der leere Index entfernt werden.

### Index hinzufügen {#adding-an-index}

Um einen Index mit dem Namen &quot;/oak:index/acmeProduct-custom-1&quot;hinzuzufügen, der in einer neuen Version der Anwendung und später verwendet werden soll, muss der Index wie folgt konfiguriert werden:

`/oak:index/acmeProduct-custom-1`

Wie oben gezeigt, stellt dies sicher, dass der Index nur von der neuen Version der Anwendung verwendet wird.

### Ändern eines Index {#changing-an-index}

Wenn ein vorhandener Index geändert wird, muss ein neuer Index mit der geänderten Indexdefinition hinzugefügt werden. Angenommen, der vorhandene Index &quot;/oak:index/acmeProduct-custom-1&quot;wurde geändert. Der alte Index wird unter gespeichert `/oak:index/acmeProduct-custom-1`und der neue Index unter `/oak:index/acmeProduct-custom-2`.

Die alte Version der Anwendung verwendet die folgende Konfiguration:

`/oak:index/acmeProduct-custom-1`

Die neue Version der Anwendung verwendet die folgende (geänderte) Konfiguration:

`/oak:index/acmeProduct-custom-2`