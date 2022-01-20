---
title: Inhaltssuche und -indizierung
description: Inhaltssuche und -indizierung
exl-id: 4fe5375c-1c84-44e7-9f78-1ac18fc6ea6b
source-git-commit: 6c223af722c24e96148146da9a2aa1c055486407
workflow-type: tm+mt
source-wordcount: '2224'
ht-degree: 93%

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

1. Beschränkungen:
* Derzeit wird die Indexverwaltung in AEM as a Cloud Service nur für Indizes des Typs Lucene unterstützt.
* Es werden nur Standard-Analyzer unterstützt (d. h. diejenigen, die mit dem Produkt geliefert werden). Benutzerdefinierte Analyzer werden nicht unterstützt.

## Verwendung {#how-to-use}

Die Definition von Indizes kann aus diesen drei Anwendungsfällen bestehen:

1. Hinzufügen einer neuen kundenspezifischen Indexdefinition.
1. Aktualisieren einer vorhandenen Indexdefinition. Das bedeutet effektiv, einer vorhandenen Indexdefinition eine neue Version hinzuzufügen..
1. Entfernen eines vorhandenen Index, der redundant oder veraltet ist.

Für die Punkte 1 und 2 müssen Sie als Teil Ihrer benutzerspezifischen Code-Basis im jeweiligen Release-Plan für Cloud Manager eine neue Indexdefinition erstellen. Weitere Informationen finden Sie in der Dokumentation [Bereitstellen in AEM as a Cloud Service](/help/implementing/deploying/overview.md).

## Indexnamen {#index-names}

Eine Indexdefinition kann wie folgt lauten:

1. Ein vordefinierter Index. Ein Beispiel dafür ist `/oak:index/cqPageLucene-2`.
1. Eine Anpassung eines vordefinierten Index. Solche Anpassungen werden vom Kunden definiert. Ein Beispiel dafür ist `/oak:index/cqPageLucene-2-custom-1`.
1. Ein vollständig benutzerdefinierter Index. Ein Beispiel dafür ist `/oak:index/acme.product-1-custom-2`. Um Namenskollisionen zu vermeiden, müssen vollständig benutzerdefinierte Indizes über ein Präfix verfügen, z. B. `acme.`

Beachten Sie, dass sowohl die Anpassung eines nativen Index als auch vollständig benutzerdefinierte Indizes Folgendes enthalten müssen: `-custom-`. Nur vollständig benutzerdefinierte Indizes müssen mit einem Präfix beginnen.

### Vorbereiten der neuen Indexdefinition {#preparing-the-new-index-definition}

>[!NOTE]
>
>Wenn Sie beispielsweise einen vordefinierten Index anpassen `damAssetLucene-6`, kopieren Sie bitte die neueste vordefinierte Indexdefinition aus einem *Cloud Service-Umgebung* und fügen Sie Ihre Anpassungen oben hinzu, damit die erforderlichen Konfigurationen nicht versehentlich entfernt werden. Beispielsweise ist der Knoten `tika` unter `/oak:index/damAssetLucene-6/tika` ein erforderlicher Knoten und sollte auch Teil Ihres anwenderdefinierten Index sein und nicht im Cloud Service-SDK vorhanden sein.

Sie müssen ein neues Indexdefinitionspaket erstellen, das die tatsächliche Indexdefinition gemäß folgendem Benennungsmuster enthält:

`<indexName>[-<productVersion>]-custom-<customVersion>`

das dann unter `ui.apps/src/main/content/jcr_root` aufgeführt werden muss. Unterstammordner werden ab sofort nicht mehr unterstützt.

Das Paket aus dem obigen Beispiel wird als `com.adobe.granite:new-index-content:zip:1.0.0-SNAPSHOT` erstellt.

>[!NOTE]
>
>Für jedes Inhaltspaket, das Indexdefinitionen enthält, sollte die folgende Eigenschaft in der Eigenschaftendatei des Inhaltspakets unter `/META-INF/vault/properties.xml` festgelegt sein:
>
>`noIntermediateSaves=true`

### Bereitstellen von Indexdefinitionen {#deploying-index-definitions}

>[!NOTE]
>
>Es gibt ein bekanntes Problem mit Jackrabbit Filevault Maven Package Plugin Version **1.1.0**, das es Ihnen unmöglich macht, `oak:index` zu Modulen von `<packageType>application</packageType>` hinzuzufügen. Sie sollten ein Update auf eine neuere Version dieses Plug-ins durchführen.

Indexdefinitionen werden jetzt als benutzerdefiniert und versioniert gekennzeichnet:

* Die Indexdefinition selbst (z. B. `/oak:index/ntBaseLucene-custom-1`)

Um einen Index bereitzustellen, muss die Indexdefinition (`/oak:index/definitionname`) daher via `ui.apps` über Git und das Cloud Manager-Implementierungsverfahren bereitgestellt werden.

Nachdem die neue Indexdefinition hinzugefügt wurde, muss das neue Programm über Cloud Manager bereitgestellt werden. Bei der Implementierung werden zwei Aufträge gestartet, die für das Hinzufügen (und gegebenenfalls das Zusammenführen) der Indexdefinitionen zu MongoDB und Azure Segment Store verantwortlich sind (für Erstellungs- bzw. Veröffentlichungszwecke). Die zugrunde liegenden Repositorys werden mit den neuen Indexdefinitionen neu indiziert, bevor die Blau/Grün-Umstellung stattfindet.

>[!TIP]
>
>Weitere Informationen zur erforderlichen Paketstruktur für AEM as a Cloud Service finden Sie im Dokument [AEM-Projektstruktur](/help/implementing/developing/introduction/aem-project-content-package-structure.md).

## Indexverwaltung unter Verwendung von Blau/Grün-Implementierungen {#index-management-using-blue-green-deployments}

### Was ist Indexverwaltung? {#what-is-index-management}

Bei der Indexverwaltung geht es darum, Indizes hinzuzufügen, zu entfernen und zu ändern. Eine Änderung der *Definition* eines Index geht schnell, doch die Anwendung der Änderung (häufig als „Erstellen eines Index“ oder bei vorhandenen Indizes als „Neuindizierung“ bezeichnet) erfordert Zeit. Das geht nicht sofort: Das Repository muss zunächst auf zu indizierende Daten geprüft werden.

### Was ist eine Blau/Grün-Implementierung? {#what-is-blue-green-deployment}

Eine Blau/Grün-Implementierung kann Ausfallzeiten reduzieren. Sie ermöglicht Upgrades ohne Ausfallzeiten sowie schnelle Rollbacks. Die alte Version des Programms (blau) wird gleichzeitig mit der neuen Version des Programms (grün) ausgeführt.

### Schreibgeschützte Bereiche und Bereiche mit Lese-Schreib-Zugriff {#read-only-and-read-write-areas}

Bestimmte Bereiche des Repositorys (schreibgeschützte Teile des Repositorys) können sich in der alten (blauen) und der neuen (grünen) Version des Programms unterscheiden. Die schreibgeschützten Bereiche des Repositorys sind in der Regel `/app` und `/libs`. Im folgenden Beispiel wird Kursivschrift verwendet, um schreibgeschützte Bereiche zu markieren, während Fettschrift für Bereiche mit Lese-Schreib-Zugriff steht.

* **/**
* */apps (schreibgeschützt)*
* **/content**
* */libs (schreibgeschützt)*
* **/oak:index**
* **/oak:index/acme.**
* **/jcr:system**
* **/system**
* **/var**

Die Bereiche mit Lese- und Schreibzugriff des Repositorys werden von allen Versionen des Programms gemeinsam genutzt, während es für jede Version des Programms einen spezifischen Satz von `/apps` und `/libs` gibt.

### Indexverwaltung ohne Blau/Grün-Implementierung {#index-management-without-blue-green-deployment}

Bei der Entwicklung oder bei Verwendung von lokalen Installationen können Indizes zur Laufzeit hinzugefügt, entfernt oder geändert werden. Indizes werden verwendet, sobald sie verfügbar sind. Wenn ein Index noch nicht in der alten Version des Programms verwendet werden soll, wird der Index normalerweise während einer geplanten Ausfallzeit erstellt. Dasselbe gilt, wenn ein Index entfernt oder ein vorhandener Index geändert wird. Wenn Sie einen Index entfernen, steht er sofort nach der Entfernung nicht mehr zur Verfügung.

### Indexverwaltung mit Blau/Grün-Implementierung {#index-management-with-blue-green-deployment}

Bei Blau/Grün-Implementierungen gibt es keine Ausfallzeiten. Für die Indexverwaltung ist es jedoch erforderlich, dass Indizes nur von bestimmten Versionen des Programms verwendet werden. Wenn Sie beispielsweise einen Index in Version 2 des Programms hinzufügen, sollte dieser noch nicht von Version 1 des Programms genutzt werden. Das Gegenteil ist der Fall, wenn ein Index entfernt wird: Ein in Version 2 entfernter Index wird in Version 1 weiterhin benötigt. Beim Ändern einer Indexdefinition soll die alte Version des Index nur für Version 1 verwendet werden; die neue Version des Index soll nur für Version 2 genutzt werden.

Die folgende Tabelle zeigt fünf Indexdefinitionen: der Index `cqPageLucene` wird in beiden Versionen verwendet, während der Index `damAssetLucene-custom-1` nur in Version 2 zum Einsatz kommt.

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

Die Versionsnummer wird bei jeder Indexänderung inkrementiert. Um zu vermeiden, dass es zu Überschneidungen zwischen anwenderspezifischen Indexnamen und den Indexnamen des Produkts selbst kommt, müssen anwenderspezifische Indizes sowie Änderungen an vordefinierten Indizes mit `-custom-<number>` enden.

### Änderungen an vordefinierten Indizes {#changes-to-out-of-the-box-indexes}

Sobald Adobe einen vordefinierten Index wie „damAssetLucene“ oder „cqPageLucene“ ändert, wird ein neuer Index mit dem Namen `damAssetLucene-2` oder `cqPageLucene-2` erstellt; falls der Index bereits angepasst wurde, wird die benutzerdefinierte Indexdefinition mit den Änderungen im vordefinierten Index zusammengeführt (wie unten dargestellt). Die Zusammenführung von Änderungen erfolgt automatisch. Das bedeutet, dass Sie nichts tun müssen, wenn sich ein vordefinierter Index ändert. Der Index lässt sich jedoch später erneut anpassen.

| Index | Vordefinierter Index | Verwendung in Version 2 | Verwendung in Version 3 |
|---|---|---|---|
| /oak:index/damAssetLucene-custom-1 | Ja (angepasst) | Ja | Nein |
| /oak:index/damAssetLucene-2-custom-1 | Ja (automatisch aus „damAssetLucene-custom-1“ und „damAssetLucene-2“ zusammengeführt) | Nein | Ja |
| /oak:index/cqPageLucene | Ja | Ja | Nein |
| /oak:index/cqPageLucene-2 | Ja | Nein | Ja |

### Aktuelle Einschränkungen {#current-limitations}

Die Indexverwaltung wird derzeit nur für Indizes vom Typ `lucene` unterstützt.

### Hinzufügen eines Index {#adding-an-index}

So fügen Sie einen vollständig benutzerdefinierten Index mit dem Namen `/oak:index/acme.product-custom-1` für die Verwendung in einer neuen Version der Anwendung und höher, muss der Index wie folgt konfiguriert werden:

`acme.product-1-custom-1`

Dies funktioniert, indem dem Indexnamen eine benutzerdefinierte Kennung vorangestellt wird, gefolgt von einem Punkt (**`.`**). Die Kennung muss zwischen 2 und 5 Zeichen lang sein.

Wie oben gezeigt, wird sichergestellt, dass der Index nur von der neuen Version des Programms verwendet wird.

### Ändern eines Index {#changing-an-index}

Wenn ein vorhandener Index geändert wird, muss ein neuer Index mit der geänderten Indexdefinition hinzugefügt werden. Angenommen, der vorhandene Index `/oak:index/acme.product-custom-1` wird geändert. Der alte Index wird unter `/oak:index/acme.product-custom-1`, der neue Index unter `/oak:index/acme.product-custom-2` gespeichert.

Die alte Version des Programms nutzt die folgende Konfiguration:

`/oak:index/acme.product-custom-1`

Die neue Version des Programms nutzt die folgende (geänderte) Konfiguration:

`/oak:index/acme.product-custom-2`

>[!NOTE]
>
>Die Indexdefinitionen für AEM as a Cloud Service stimmen möglicherweise nicht vollständig mit den Indexdefinitionen für eine lokale Entwicklungsinstanz überein. Die Entwicklungsinstanz verfügt im Gegensatz zu AEM as a Cloud Service-Instanzen nicht über eine Tika-Konfiguration. Wenn Sie einen Index mit einer Tika-Konfiguration anpassen, behalten Sie die Tika-Konfiguration bei.

### Rückgängigmachen einer Änderung {#undoing-a-change}

Manchmal muss eine Änderung der Indexdefinition rückgängig gemacht werden, etwa wenn eine Änderung versehentlich vorgenommen wurde oder aber nicht mehr erforderlich ist. Beispiel: Die Indexdefinition `damAssetLucene-8-custom-3` wurde versehentlich erstellt und bereits bereitgestellt. Daher empfiehlt es sich, zur vorherigen Indexdefinition `damAssetLucene-8-custom-2` zurückkehren. Dazu müssen Sie einen neuen Index namens `damAssetLucene-8-custom-4` hinzufügen, der die Definition des vorherigen Index – `damAssetLucene-8-custom-2` – enthält.

### Entfernen eines Index {#removing-an-index}

Nachfolgendes gilt nur für anwenderdefinierte Indizes. Produktindizes können nicht entfernt werden, da sie von AEM verwendet werden.

Wenn ein Index in einer späteren Version des Programms entfernt werden soll, können Sie einen leeren Index (einen leeren Index, der nie verwendet wird und keine Daten enthält) mit einem neuen Namen definieren. Für dieses Beispiels können Sie ihn `/oak:index/acme.product-custom-3` nennen. Dadurch wird der Index `/oak:index/acme.product-custom-2` ersetzt. Nachdem das System `/oak:index/acme.product-custom-2` entfernt hat, kann auch der leere Index `/oak:index/acme.product-custom-3` entfernt werden. Beispiel für einen solchen leeren Index:

```xml
<acme.product-custom-3
        jcr:primaryType="oak:QueryIndexDefinition"
        async="async"
        compatVersion="2"
        includedPaths="/dummy"
        queryPaths="/dummy"
        type="lucene">
        <indexRules jcr:primaryType="nt:unstructured">
            <rep:root jcr:primaryType="nt:unstructured">
                <properties jcr:primaryType="nt:unstructured">
                    <dummy
                        jcr:primaryType="nt:unstructured"
                        name="dummy"
                        propertyIndex="{Boolean}true"/>
                </properties>
            </rep:root>
        </indexRules>
    </acme.product-custom-3>
```

Wenn eine Anpassung eines vordefinierten Index nicht mehr erforderlich ist, müssen Sie die vordefinierte Indexdefinition kopieren. Wenn Sie beispielsweise `damAssetLucene-8-custom-3` bereits bereitgestellt haben, die Anpassungen jedoch nicht mehr benötigen und zum standardmäßigen `damAssetLucene-8`-Index zurückwechseln möchten, müssen Sie einen `damAssetLucene-8-custom-4`-Index hinzufügen, der die Indexdefinition von `damAssetLucene-8` enthält.

## Indexoptimierungen {#index-optimizations}

Apache Jackrabbit Oak ermöglicht flexible Indexkonfigurationen zur effizienten Verarbeitung von Suchabfragen. Indizes sind besonders für größere Repositorys wichtig. Stellen Sie sicher, dass alle Abfragen durch einen geeigneten Index gestützt werden. Abfragen ohne geeigneten Index können Tausende von Knoten lesen, was dann als Warnung protokolliert wird. Solche Abfragen sollten durch Analyse der Protokolldateien identifiziert werden, damit Indexdefinitionen optimiert werden können. Weitere Informationen finden Sie auf [dieser Seite](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/practices/best-practices-for-queries-and-indexing.html?lang=de#tips-for-creating-efficient-indexes).

### Lucene-Volltextindex in AEM as a Cloud Service {#index-lucene}

Der Volltextindex `/oak:index/lucene-2` kann sehr groß werden, da er standardmäßig alle Knoten im AEM-Repository indiziert. Nach der von Adobe geplanten Einstellung dieses Index wird dieser produktseitig nicht mehr in AEM as a Cloud Service verwendet und sollte nicht mehr zum Ausführen von Kundencode erforderlich sein. Für AEM as a Cloud Service-Umgebungen mit gemeinsamen Lucene-Indizes arbeitet Adobe mit den Kunden einzeln für einen koordinierten Ansatz zusammen, um einen Ersatz für diesen Index zu finden und bessere, optimierte Indizes zu verwenden. Ohne weitere Ankündigung seitens Adobe sind keine Maßnahmen erforderlich. AEM as a Cloud Service-Kunden werden von Adobe informiert, wenn ein Handlungsbedarf im Hinblick auf diese Optimierung besteht. Wenn dieser Index für benutzerdefinierte Abfragen als temporäre Lösung erforderlich ist, sollte eine Kopie dieses Index mit einem anderen Namen erstellt werden, z. B. `/oak:index/acme.lucene-1-custom-1`, wie [hier](/help/operations/indexing.md) beschrieben.
Diese Optimierung gilt nicht standardmäßig für andere AEM-Umgebungen, die entweder lokal gehostet oder von Adobe Managed Services verwaltet werden.

## Abfrageoptimierung {#index-query}

Mit dem **Abfrageleistungs**-Tool können Sie sowohl gängige als auch langsame JCR-Abfragen beobachten. Darüber hinaus kann es Abfragen analysieren und verschiedene Informationen anzeigen, insbesondere wenn für diese Abfrage ein Index verwendet wird oder nicht.

Anders als bei AEM On-Premise wird bei AEM as a Cloud Service das **Abfrageleistungs**-Tool nicht mehr in der Benutzeroberfläche angezeigt. Stattdessen ist sie jetzt über die Entwickler-Konsole (in Cloud Manager) auf der Registerkarte [Abfragen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html?lang=de#queries) verfügbar.
