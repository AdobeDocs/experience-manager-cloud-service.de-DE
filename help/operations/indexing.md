---
title: Inhaltssuche und -indizierung
description: Inhaltssuche und -indizierung
exl-id: 4fe5375c-1c84-44e7-9f78-1ac18fc6ea6b
source-git-commit: 1544358f9a706574d8944fa92422240c46d62d2f
workflow-type: tm+mt
source-wordcount: '2253'
ht-degree: 85%

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
* Derzeit wird die Indexverwaltung in AEM as a Cloud Service nur für Indizes des Typs `lucene` unterstützt.
* Es werden nur Standard-Analyzer unterstützt (d. h. diejenigen, die mit dem Produkt geliefert werden). Benutzerdefinierte Analyzer werden nicht unterstützt.
* Intern können andere Indizes konfiguriert und für Abfragen verwendet werden. Zum Beispiel Abfragen, die gegen für den `damAssetLucene`-Index geschrieben wurden, können auf Skyline tatsächlich für eine Elasticsearch-Version dieses Index ausgeführt werden. Dieser Unterschied ist für das Programm und den Benutzer normalerweise nicht sichtbar, jedoch melden bestimmte Tools wie die `explain`-Funktion einen anderen Index. Unterschiede zwischen Lucene-Indizes und Elastic-Indizes finden Sie unter [die Elastic-Dokumentation in Apache Jackrabbit Oak](https://jackrabbit.apache.org/oak/docs/query/elastic.html). Elasticsearch-Indizes müssen und können vom Kunden nicht direkt konfiguriert werden.

## Verwendung {#how-to-use}

Eine Definition von Indizes kann die folgenden drei Anwendungsfälle umfassen:

1. Hinzufügen einer neuen kundenspezifischen Indexdefinition.
1. Aktualisieren einer vorhandenen Indexdefinition. Das bedeutet effektiv, einer vorhandenen Indexdefinition eine neue Version hinzuzufügen..
1. Entfernen eines vorhandenen Index, der redundant oder veraltet ist.

Für die Punkte 1 und 2 müssen Sie als Teil Ihrer benutzerspezifischen Code-Basis im jeweiligen Release-Plan für Cloud Manager eine neue Indexdefinition erstellen. Weitere Informationen finden Sie in der Dokumentation [Bereitstellen in AEM as a Cloud Service](/help/implementing/deploying/overview.md).

## Indexnamen {#index-names}

Eine Indexdefinition kann Folgendes sein:

1. Ein vordefinierter Index. Ein Beispiel dafür ist `/oak:index/cqPageLucene-2`.
1. Eine Anpassung eines vordefinierten Index. Solche Anpassungen werden vom Kunden definiert. Ein Beispiel dafür ist `/oak:index/cqPageLucene-2-custom-1`.
1. Ein vollständig benutzerdefinierter Index. Ein Beispiel dafür ist `/oak:index/acme.product-1-custom-2`. Um Namenskonflikte zu vermeiden, müssen vollständig benutzerdefinierte Indizes ein Präfix aufweisen, z. B. `acme.`

Beachten Sie, dass sowohl die Anpassung eines vordefinierten Index als auch vollständig benutzerdefinierte Indizes `-custom-` enthalten müssen. Nur vollständig benutzerdefinierte Indizes müssen mit einem Präfix beginnen.

## Vorbereiten der neuen Indexdefinition {#preparing-the-new-index-definition}

>[!NOTE]
>
>Wenn Sie beispielsweise einen vordefinierten Index anpassen `damAssetLucene-6`, kopieren Sie bitte die neueste vordefinierte Indexdefinition aus einem *Cloud Service-Umgebung* mit dem CRX DE Package Manager (`/crx/packmgr/`) . Benennen Sie dann die Konfiguration um, z. B. `damAssetLucene-6-custom-1`und fügen Sie oben Ihre Anpassungen hinzu. Dadurch wird sichergestellt, dass erforderliche Konfigurationen nicht versehentlich entfernt werden. Beispiel: die `tika` Knoten unter `/oak:index/damAssetLucene-6/tika` ist im angepassten Index des Cloud-Service erforderlich. Sie existiert nicht im Cloud SDK.

Sie müssen ein neues Indexdefinitionspaket erstellen, das die tatsächliche Indexdefinition gemäß folgendem Benennungsmuster enthält:

`<indexName>[-<productVersion>]-custom-<customVersion>`

das dann unter `ui.apps/src/main/content/jcr_root` aufgeführt werden muss. Alle benutzerdefinierten und benutzerdefinierten Indexdefinitionen müssen unter gespeichert werden. `/oak:index`.

Der Filter für das Paket muss so festgelegt sein, dass vorhandene (vordefinierte Indizes) beibehalten werden. In der Datei `ui.apps/src/main/content/META-INF/vault/filter.xml`, muss jeder benutzerdefinierte (oder benutzerdefinierte) Index aufgeführt werden, z. B. `<filter root="/oak:index/damAssetLucene-6-custom-1"/>`. Wenn die Indexversion später geändert wird, muss der Filter angepasst werden.

Das Paket aus dem obigen Beispiel wird als `com.adobe.granite:new-index-content:zip:1.0.0-SNAPSHOT` erstellt.

>[!NOTE]
>
>Für jedes Inhaltspaket, das Indexdefinitionen enthält, sollte die folgende Eigenschaft in der Eigenschaftendatei des Inhaltspakets unter `/META-INF/vault/properties.xml` festgelegt sein:
>
>`noIntermediateSaves=true`

## Bereitstellen von Indexdefinitionen {#deploying-index-definitions}

Indexdefinitionen werden als benutzerdefiniert und versioniert markiert:

* Die Indexdefinition selbst (z. B. `/oak:index/ntBaseLucene-custom-1`)

Um einen benutzerdefinierten oder benutzerdefinierten Index bereitzustellen, wird die Indexdefinition (`/oak:index/definitionname`) muss über bereitgestellt werden. `ui.apps` über Git und den Cloud Manager-Implementierungsprozess. Im FileVault-Filter, z. B. `ui.apps/src/main/content/META-INF/vault/filter.xml`, listen Sie jeden benutzerdefinierten und benutzerdefinierten Index einzeln auf, z. B. `<filter root="/oak:index/damAssetLucene-7-custom-1"/>`. Die benutzerdefinierte/angepasste Indexdefinition selbst wird dann in der Datei gespeichert `ui.apps/src/main/content/jcr_root/_oak_index/damAssetLucene-7-custom-1/.content.xml`, wie folgt:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:oak="http://jackrabbit.apache.org/oak/ns/1.0" xmlns:dam="http://www.day.com/dam/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0" xmlns:nt="http://www.jcp.org/jcr/nt/1.0" xmlns:rep="internal"
        jcr:primaryType="oak:QueryIndexDefinition"
        async="[async,nrt]"
        compatVersion="{Long}2"
        ...
        </indexRules>
        <tika jcr:primaryType="nt:unstructured">
            <config.xml jcr:primaryType="nt:file"/>
        </tika>
</jcr:root>
```

Das obige Beispiel enthält eine Konfiguration für Apache Tika. Die Tika-Konfigurationsdatei würde unter `ui.apps/src/main/content/jcr_root/_oak_index/damAssetLucene-7-custom-1/tika/config.xml`.

### Projektkonfiguration

Je nachdem, welche Version des Jackrabbit Filevault Maven Package Plugins verwendet wird, ist eine weitere Konfiguration im Projekt erforderlich. Bei Verwendung der Jackrabbit Filevault Maven Package Plugin-Version **1.1.6** oder neuer, dann die Datei `pom.xml` muss den folgenden Abschnitt in der Plug-in-Konfiguration für die `filevault-package-maven-plugin`in `configuration/validatorsSettings` (kurz zuvor `jackrabbit-nodetypes`):

```xml
<jackrabbit-packagetype>
    <options>
        <immutableRootNodeNames>apps,libs,oak:index</immutableRootNodeNames>
    </options>
</jackrabbit-packagetype>
```

Außerdem wird in diesem Fall die `vault-validation` -Version muss auf eine neuere Version aktualisiert werden:

```xml
<dependency>
    <groupId>org.apache.jackrabbit.vault</groupId>
    <artifactId>vault-validation</artifactId>
    <version>3.5.6</version>
</dependency>
```

Anschließend in `ui.apps.structure/pom.xml` und `ui.apps/pom.xml`, die Konfiguration der `filevault-package-maven-plugin` muss `allowIndexDefinitions` sowie `noIntermediateSaves` aktiviert. Die Option `noIntermediateSaves` stellt sicher, dass die Indexkonfigurationen automatisch hinzugefügt werden.

```xml
<groupId>org.apache.jackrabbit</groupId>
    <artifactId>filevault-package-maven-plugin</artifactId>
    <configuration>
        <allowIndexDefinitions>true</allowIndexDefinitions>
        <properties>
            <cloudManagerTarget>none</cloudManagerTarget>
            <noIntermediateSaves>true</noIntermediateSaves>
        </properties>
    ...
```

In `ui.apps.structure/pom.xml`, die `filters` -Abschnitt für dieses Plug-in muss einen Filterstamm wie folgt enthalten:

```xml
<filter><root>/oak:index</root></filter>
```

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

Bei Blau/Grün-Implementierungen gibt es keine Ausfallzeiten. Während eines Upgrades werden für einige Zeit sowohl die alte Version (z. B. Version 1) des Programms als auch die neue Version (Version 2) gleichzeitig für dasselbe Repository ausgeführt. Wenn für Version 1 ein bestimmter Index verfügbar sein muss, darf dieser Index in Version 2 nicht entfernt werden: Der Index sollte später entfernt werden, z. B. in Version 3. Ab diesem Zeitpunkt wird garantiert, dass Version 1 des Programms nicht mehr ausgeführt wird. Außerdem sollten Programme so geschrieben werden, dass Version 1 gut funktioniert, auch wenn Version 2 ausgeführt wird und Indizes von Version 2 verfügbar sind.

Nach Abschluss der Aktualisierung auf die neue Version können alte Indizes vom System entfernt werden. Die alten Indizes können möglicherweise noch einige Zeit bleiben, um Rollbacks zu beschleunigen (falls ein Rollback erforderlich sein sollte).

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

Die Indexverwaltung wird derzeit nur für Indizes vom Typ `lucene` unterstützt. Intern können andere Indizes konfiguriert und für Abfragen verwendet werden, z. B. Elastic-Indizes.

### Hinzufügen eines Index {#adding-an-index}

Um einen Index mit dem Namen `/oak:index/acme.product-custom-1` hinzuzufügen, der in einer neuen Version des Programms und höher verwendet werden soll, muss der Index wie folgt konfiguriert werden:

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

## Index- und Abfrageoptimierung {#index-query-optimizations}

Apache Jackrabbit Oak ermöglicht flexible Indexkonfigurationen zur effizienten Verarbeitung von Suchabfragen. Indizes sind besonders für größere Repositorys wichtig. Stellen Sie sicher, dass alle Abfragen durch einen geeigneten Index gestützt werden. Abfragen ohne geeigneten Index können Tausende von Knoten lesen, was dann als Warnung protokolliert wird.

Siehe [dieses Dokuments](query-and-indexing-best-practices.md) für Informationen zur Optimierung von Abfragen und Indizes.
