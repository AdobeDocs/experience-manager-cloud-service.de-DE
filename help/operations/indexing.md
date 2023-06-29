---
title: Inhaltssuche und -indizierung
description: Inhaltssuche und -indizierung
exl-id: 4fe5375c-1c84-44e7-9f78-1ac18fc6ea6b
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '2427'
ht-degree: 43%

---

# Inhaltssuche und -indizierung {#indexing}

## Änderungen in AEM as a Cloud Service {#changes-in-aem-as-a-cloud-service}

Mit AEM as a Cloud Service stellt Adobe von einem AEM-Instanz-zentrierten Modell auf eine Service-basierte Ansicht mit n-x AEM-Containern um, unterstützt von CI/CD-Pipelines in Cloud Manager. Anstatt Indizes für einzelne AEM-Instanzen zu konfigurieren und zu verwalten, muss die Indexkonfiguration vor der Bereitstellung angegeben werden. Konfigurationsänderungen in der Produktion verstoßen eindeutig gegen CI/CD-Richtlinien. Dasselbe gilt für Indexänderungen, da sie sich auf die Systemstabilität und -leistung auswirken können, wenn sie nicht speziell getestet werden, bevor sie in die Produktion aufgenommen werden.

Nachstehend finden Sie eine Liste der wichtigsten Änderungen im Vergleich zu AEM 6.5 und früheren Versionen:

1. Benutzer haben keinen Zugriff mehr auf den Index-Manager einer einzelnen AEM-Instanz, um die Indizierung zu debuggen, zu konfigurieren oder zu warten. Er wird nur für lokale Entwicklungsumgebungen und On-Premise-Bereitstellungen verwendet.
1. Benutzer ändern Indizes nicht in einer einzelnen AEM-Instanz und müssen sich auch keine Gedanken mehr über Konsistenzprüfungen oder Neuindizierungen machen.
1. Im Allgemeinen werden Indexänderungen vor der Produktion initiiert, um Qualitäts-Gateways in den CI/CD-Pipelines von Cloud Manager nicht zu umgehen und geschäftliche KPIs in der Produktion nicht zu beeinträchtigen.
1. Alle zugehörigen Metriken, einschließlich der Suchleistung in der Produktion, stehen Kunden zur Laufzeit zur Verfügung, um eine ganzheitliche Ansicht der Themen Suche und Indizierung bereitzustellen.
1. Kunden können entsprechend ihren Anforderungen Warnungen einrichten.
1. SREs überwachen den Systemzustand rund um die Uhr, und Maßnahmen werden so früh wie möglich ergriffen.
1. Die Indexkonfiguration wird über Bereitstellungen geändert. Änderungen an der Indexdefinition werden wie andere Inhaltsänderungen konfiguriert.
1. Auf hoher Ebene auf AEM as a Cloud Service mit der Einführung der [Rollierendes Bereitstellungsmodell](#index-management-using-rolling-deployments), gibt es zwei Indexsätze: eine für die alte Version und eine für die neue Version.
1. Kunden können sehen, ob der Indizierungsauftrag auf der Build-Seite von Cloud Manager abgeschlossen ist, und erhalten eine Benachrichtigung, wenn die neue Version für den Traffic bereit ist.

Beschränkungen:

* Derzeit wird die Indexverwaltung in AEM as a Cloud Service nur für Indizes des Typs `lucene` unterstützt.
* Es werden nur Standard-Analyzer unterstützt (d. h. die Analyzer, die im Lieferumfang des Produkts enthalten sind). Benutzerdefinierte Analyzer werden nicht unterstützt.
* Intern können andere Indizes konfiguriert und für Abfragen verwendet werden. Zum Beispiel Abfragen, die gegen für den `damAssetLucene`-Index geschrieben wurden, können auf Skyline tatsächlich für eine Elasticsearch-Version dieses Index ausgeführt werden. Dieser Unterschied ist normalerweise für die Anwendung und den Benutzer nicht sichtbar. Allerdings sind bestimmte Tools wie die `explain` -Funktion einen anderen Index anzeigen. Unterschiede zwischen Lucene-Indizes und Elastic-Indizes finden Sie unter [die Elastic-Dokumentation in Apache Jackrabbit Oak](https://jackrabbit.apache.org/oak/docs/query/elastic.html). Kunden müssen und können keine Elasticsearch-Indizes direkt konfigurieren.

## Verwendung {#how-to-use}

Die Definition von Indizes kann aus diesen drei Anwendungsfällen bestehen:

1. Hinzufügen einer kundenspezifischen Indexdefinition.
1. Aktualisieren einer vorhandenen Indexdefinition. Diese Aktualisierung bedeutet effektiv, dass eine neue Version einer vorhandenen Indexdefinition hinzugefügt wird.
1. Entfernen eines vorhandenen Index, der redundant oder veraltet ist.

Für die obigen Punkte 1 und 2 müssen Sie eine Indexdefinition als Teil Ihrer benutzerdefinierten Codebasis im entsprechenden Cloud Manager-Veröffentlichungszeitplan erstellen. Weitere Informationen finden Sie unter [Bereitstellen in AEM as a Cloud Service Dokumentation](/help/implementing/deploying/overview.md).

## Indexnamen {#index-names}

Eine Indexdefinition kann Folgendes sein:

1. Ein vordefinierter Index. Ein Beispiel dafür ist `/oak:index/cqPageLucene-2`.
1. Eine Anpassung eines vordefinierten Index. Solche Anpassungen werden vom Kunden definiert. Ein Beispiel dafür ist `/oak:index/cqPageLucene-2-custom-1`.
1. Ein vollständig benutzerdefinierter Index. Ein Beispiel dafür ist `/oak:index/acme.product-1-custom-2`. Um Namenskollisionen zu vermeiden, erfordert Adobe, dass vollständig benutzerdefinierte Indizes beispielsweise über ein -Präfix verfügen. `acme.`

Beachten Sie, dass sowohl die Anpassung eines nativen Index als auch vollständig benutzerdefinierte Indizes Folgendes enthalten müssen: `-custom-`. Nur vollständig benutzerdefinierte Indizes müssen mit einem Präfix beginnen.

## Vorbereiten der neuen Indexdefinition {#preparing-the-new-index-definition}

>[!NOTE]
>
>Wenn Sie beispielsweise einen vordefinierten Index anpassen `damAssetLucene-6`, kopieren Sie die neueste vordefinierte Indexdefinition aus einem *Cloud Service-Umgebung* mit dem CRX DE Package Manager (`/crx/packmgr/`) . Benennen Sie dann die Konfiguration um, z. B. in `damAssetLucene-6-custom-1`, und fügen Sie oben Ihre Anpassungen hinzu. Dadurch wird sichergestellt, dass erforderliche Konfigurationen nicht versehentlich entfernt werden. Beispiel: der Knoten `tika` unter `/oak:index/damAssetLucene-6/tika` ist im angepassten Index des Cloud-Service erforderlich. Sie ist im Cloud SDK nicht vorhanden.

Bereiten Sie ein Indexdefinitionspaket vor, das die tatsächliche Indexdefinition enthält, und befolgen Sie dabei dieses Namensmuster:

`<indexName>[-<productVersion>]-custom-<customVersion>`

Was muss dann unter `ui.apps/src/main/content/jcr_root`. Alle benutzerdefinierten und benutzerdefinierten Indexdefinitionen müssen unter `/oak:index`.

Der Filter für das Paket muss so festgelegt sein, dass vorhandene (vordefinierte Indizes) beibehalten werden. In der Datei `ui.apps/src/main/content/META-INF/vault/filter.xml`, sollte jeder benutzerdefinierte (oder angepasste) Index aufgeführt werden, z. B. als `<filter root="/oak:index/damAssetLucene-6-custom-1"/>`. Wenn die Indexversion später geändert wird, muss der Filter angepasst werden.

<!-- Alexandru: temporarily drafting this statement due to CQDOC-17701

The package from the above sample is built as `com.adobe.granite:new-index-content:zip:1.0.0-SNAPSHOT`. -->

>[!NOTE]
>
>Jedes Inhaltspaket, das Indexdefinitionen enthält, sollte die folgende Eigenschaft in der Eigenschaftendatei des Inhaltspakets unter `/META-INF/vault/properties.xml`:
>
>`noIntermediateSaves=true`

## Bereitstellen von Indexdefinitionen {#deploying-index-definitions}

Indexdefinitionen werden als benutzerdefiniert und versioniert gekennzeichnet:

* Die Indexdefinition selbst (z. B. `/oak:index/ntBaseLucene-custom-1`)

Um einen benutzerdefinierten oder benutzerdefinierten Index bereitzustellen, wird die Indexdefinition (`/oak:index/definitionname`) muss über `ui.apps` über Git und den Cloud Manager-Implementierungsprozess. Listen Sie im FileVault-Filter, z. B. `ui.apps/src/main/content/META-INF/vault/filter.xml`, jeden benutzerdefinierten und angepassten Index einzeln auf, z. B. `<filter root="/oak:index/damAssetLucene-7-custom-1"/>`. Die benutzerdefinierte/angepasste Indexdefinition selbst wird dann in der Datei gespeichert `ui.apps/src/main/content/jcr_root/_oak_index/damAssetLucene-7-custom-1/.content.xml`, wie folgt:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:oak="https://jackrabbit.apache.org/oak/ns/1.0" xmlns:dam="http://www.day.com/dam/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0" xmlns:nt="http://www.jcp.org/jcr/nt/1.0" xmlns:rep="internal"
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

Das obige Beispiel enthält eine Konfiguration für Apache Tika. Die Tika-Konfigurationsdatei würde unter `ui.apps/src/main/content/jcr_root/_oak_index/damAssetLucene-7-custom-1/tika/config.xml` gespeichert.

### Projektkonfiguration

Je nachdem, welche Version des Jackrabbit Filevault Maven Package-Plug-ins verwendet wird, ist eine weitere Konfiguration im Projekt erforderlich. Bei Verwendung der Jackrabbit Filevault Maven Package Plugin-Version **1.1.6** oder neuer, dann die Datei `pom.xml` muss den folgenden Abschnitt in der Plug-in-Konfiguration für die `filevault-package-maven-plugin`in `configuration/validatorsSettings` (kurz zuvor `jackrabbit-nodetypes`):

```xml
<jackrabbit-packagetype>
    <options>
        <immutableRootNodeNames>apps,libs,oak:index</immutableRootNodeNames>
    </options>
</jackrabbit-packagetype>
```

In diesem Fall wird außerdem die `vault-validation` -Version muss auf eine neuere Version aktualisiert werden:

```xml
<dependency>
    <groupId>org.apache.jackrabbit.vault</groupId>
    <artifactId>vault-validation</artifactId>
    <version>3.5.6</version>
</dependency>
```

Anschließend in `ui.apps.structure/pom.xml` und `ui.apps/pom.xml`, die Konfiguration der `filevault-package-maven-plugin` muss `allowIndexDefinitions` und `noIntermediateSaves` aktiviert. Die Option `noIntermediateSaves` stellt sicher, dass die Indexkonfigurationen automatisch hinzugefügt werden.

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

Nachdem die neue Indexdefinition hinzugefügt wurde, wird die neue Anwendung über Cloud Manager bereitgestellt. Bei der Bereitstellung werden zwei Aufträge gestartet, die für das Hinzufügen (und gegebenenfalls das Zusammenführen) der Indexdefinitionen zum MongoDB- bzw. Azure-Segmentspeicher für die Autoren- bzw. Veröffentlichungsinstanz verantwortlich sind. Die zugrunde liegenden Repositorys werden mit den neuen Indexdefinitionen neu indiziert, bevor der Wechsel erfolgt.

### HINWEIS

Wenn Sie bei der Validierung der Fehler folgende Fehlermeldung feststellen: <br>
`[ERROR] ValidationViolation: "jackrabbit-nodetypes: Mandatory child node missing: jcr:content [nt:base] inside node with types [nt:file]"` <br>
Anschließend kann einer der folgenden Schritte ausgeführt werden, um das Problem zu beheben: <br>

1. Aktualisieren Sie filevault auf Version 1.0.4 und fügen Sie Folgendes zum Pom auf oberster Ebene hinzu:

```xml
<allowIndexDefinitions>true</allowIndexDefinitions>
```

Unten finden Sie ein Beispiel dafür, wo die oben beschriebene Konfiguration in den POM platziert werden soll.

```xml
<plugin>
    <groupId>org.apache.jackrabbit</groupId>
    <artifactId>filevault-package-maven-plugin</artifactId>
    <configuration>
        <properties>
        ...
        </properties>
        ...
        <allowIndexDefinitions>true</allowIndexDefinitions>
        <repositoryStructurePackages>
        ...
        </repositoryStructurePackages>
        <dependencies>
        ...
        </dependencies>
    </configuration>
</plugin>
```

1. Deaktivieren Sie die Knotentyp-Validierung. Legen Sie die folgende Eigenschaft im Abschnitt jackrabbit-nodetypes der Konfiguration des filevault-Plug-ins fest:

```xml
<isDisabled>true</isDisabled>
```

Unten finden Sie ein Beispiel dafür, wo die oben beschriebene Konfiguration in den POM platziert werden soll.

```xml
<plugin>
    <groupId>org.apache.jackrabbit</groupId>
    <artifactId>filevault-package-maven-plugin</artifactId>
    ...
    <configuration>
    ...
        <validatorsSettings>
        ...
            <jackrabbit-nodetypes>
                <isDisabled>true</isDisabled>
            </jackrabbit-nodetypes>
        </validatorsSettings>
    </configuration>
</plugin>
```

>[!TIP]
>
>Weitere Informationen zur erforderlichen Paketstruktur für AEM as a Cloud Service finden Sie im Dokument [AEM-Projektstruktur](/help/implementing/developing/introduction/aem-project-content-package-structure.md).

## Indexverwaltung mithilfe von rollierenden Implementierungen {#index-management-using-rolling-deployments}

### Was ist Indexverwaltung? {#what-is-index-management}

Bei der Indexverwaltung geht es darum, Indizes hinzuzufügen, zu entfernen und zu ändern. Eine Änderung der *Definition* eines Index geht schnell, doch die Anwendung der Änderung (häufig als „Erstellen eines Index“ oder bei vorhandenen Indizes als „Neuindizierung“ bezeichnet) erfordert Zeit. Es ist nicht sofort: das Repository auf indizierte Daten überprüft werden muss.

### Was sind rollierende Implementierungen? {#what-are-rolling-deployments}

Eine rollierende Implementierung kann Ausfallzeiten reduzieren. Sie ermöglicht Upgrades ohne Ausfallzeiten sowie schnelle Rollbacks. Die alte Version der Anwendung wird gleichzeitig mit der neuen Version der Anwendung ausgeführt.

### Schreibgeschützte Bereiche und Bereiche mit Lese-Schreib-Zugriff {#read-only-and-read-write-areas}

Bestimmte Bereiche des Repositorys (schreibgeschützte Teile des Repositorys) können sich in der alten und in der neuen Version der Anwendung unterscheiden. Die schreibgeschützten Bereiche des Repositorys sind normalerweise `/app` und `/libs`. Im folgenden Beispiel wird Kursivschrift verwendet, um schreibgeschützte Bereiche zu markieren, während Fettschrift für Bereiche mit Lese-Schreib-Zugriff steht.

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

### Indexverwaltung ohne rollierende Implementierungen {#index-management-without-rolling-deployments}

Während der Entwicklung oder bei Verwendung von On-Premise-Installationen können Indizes zur Laufzeit hinzugefügt, entfernt oder geändert werden. Indizes werden verwendet, wenn sie verfügbar sind. Wenn ein Index noch nicht in der alten Version der Anwendung verwendet wird, wird der Index normalerweise während einer geplanten Ausfallzeit erstellt. Dasselbe gilt, wenn ein Index entfernt oder ein vorhandener Index geändert wird. Wenn ein Index entfernt wird, ist er beim Entfernen nicht mehr verfügbar.

### Indexverwaltung mit rollierenden Implementierungen {#index-management-with-rolling-deployments}

Bei rollierenden Implementierungen gibt es keine Ausfallzeiten. Während einer Aktualisierung werden sowohl die alte Version (z. B. Version 1) der Anwendung als auch die neue Version (Version 2) gleichzeitig für dasselbe Repository ausgeführt. Wenn für Version 1 ein bestimmter Index verfügbar sein muss, darf dieser Index nicht in Version 2 entfernt werden. Der Index sollte später entfernt werden, z. B. in Version 3. Ab diesem Zeitpunkt wird garantiert, dass Version 1 der Anwendung nicht mehr ausgeführt wird. Außerdem sollten Programme so geschrieben werden, dass Version 1 gut funktioniert, auch wenn Version 2 ausgeführt wird und Indizes von Version 2 verfügbar sind.

Nach Abschluss der Aktualisierung auf die neue Version können alte Indizes vom System entfernt werden. Die alten Indizes bleiben möglicherweise noch einige Zeit, um Rollbacks zu beschleunigen (falls ein Rollback erforderlich sein sollte).

Die folgende Tabelle zeigt fünf Indexdefinitionen: der Index `cqPageLucene` wird in beiden Versionen verwendet, während der Index `damAssetLucene-custom-1` nur in Version 2 zum Einsatz kommt.

>[!NOTE]
>
>Die `<indexName>-custom-<customerVersionNumber>` ist erforderlich, damit AEM as a Cloud Service ihn als Ersatz für einen vorhandenen Index kennzeichnen kann.

| Index | Vordefinierter Index | Verwendung in Version 1 | Verwendung in Version 2 |
|---|---|---|---|
| /oak:index/damAssetLucene | Ja | Ja | Nein |
| /oak:index/damAssetLucene-custom-1 | Ja (angepasst) | Nein | Ja |
| /oak:index/acme.product-custom-1 | Nein | Ja | Nein |
| /oak:index/acme.product-custom-2 | Nein | Nein | Ja |
| /oak:index/cqPageLucene | Ja | Ja | Ja |

Die Versionsnummer wird bei jeder Indexänderung inkrementiert. Um zu vermeiden, dass benutzerspezifische Indexnamen mit den Indexnamen des Produkts selbst kollidieren, müssen benutzerdefinierte Indizes und Änderungen an vordefinierten Indizes mit `-custom-<number>`.

### Änderungen an vordefinierten Indizes {#changes-to-out-of-the-box-indexes}

Nachdem die Adobe einen vordefinierten Index wie &quot;damAssetLucene&quot;oder &quot;cqPageLucene&quot;ändert, wird ein neuer Index mit dem Namen `damAssetLucene-2` oder `cqPageLucene-2` erstellt. Oder wenn der Index bereits angepasst wurde, wird die angepasste Indexdefinition mit den Änderungen im vordefinierten Index zusammengeführt, wie unten dargestellt. Die Zusammenführung von Änderungen erfolgt automatisch. Das bedeutet, dass Sie nichts tun müssen, wenn sich ein vordefinierter Index ändert. Der Index lässt sich jedoch später erneut anpassen.

| Index | Vordefinierter Index | Verwendung in Version 2 | Verwendung in Version 3 |
|---|---|---|---|
| /oak:index/damAssetLucene-custom-1 | Ja (angepasst) | Ja | Nein |
| /oak:index/damAssetLucene-2-custom-1 | Ja (automatisch aus „damAssetLucene-custom-1“ und „damAssetLucene-2“ zusammengeführt) | Nein | Ja |
| /oak:index/cqPageLucene | Ja | Ja | Nein |
| /oak:index/cqPageLucene-2 | Ja | Nein | Ja |

### Aktuelle Einschränkungen {#current-limitations}

Die Indexverwaltung wird nur für Indizes vom Typ `lucene`, mit `compatVersion` auf `2`. Intern können andere Indizes konfiguriert und für Abfragen verwendet werden, z. B. Elasticsearch-Indizes. Sie können Abfragen, die gegen den `damAssetLucene`-Index geschrieben werden, auf AEM as a Cloud Service tatsächlich für eine Elasticsearch-Version dieses Indexes ausführen. Dieser Unterschied ist für den Endbenutzer der Anwendung nicht sichtbar, jedoch sind bestimmte Tools wie die `explain` -Funktion einen anderen Index meldet. Unterschiede zwischen Lucene- und Elasticsearch-Indizes finden Sie in der [Elasticsearch-Dokumentation in Apache Jackrabbit Oak](https://jackrabbit.apache.org/oak/docs/query/elastic.html). Elasticsearch-Indizes können und müssen nicht direkt konfiguriert werden.

Es werden nur integrierte Analyzer unterstützt (d. h. die Analyzer, die im Lieferumfang des Produkts enthalten sind). Benutzerdefinierte Analyzer werden nicht unterstützt.

Um eine optimale Betriebsleistung zu erzielen, sollten Indizes nicht zu groß sein. Die Gesamtgröße aller Indizes kann als Leitfaden verwendet werden. Wenn diese Größe um mehr als 100 % zunimmt, nachdem benutzerdefinierte Indizes hinzugefügt und Standardindizes in einer Entwicklungsumgebung angepasst wurden, sollten benutzerdefinierte Indexdefinitionen angepasst werden. AEM as a Cloud Service kann die Bereitstellung von Indizes verhindern, die die Systemstabilität und -leistung negativ beeinflussen würden.

### Hinzufügen eines Index {#adding-an-index}

So fügen Sie einen vollständig benutzerdefinierten Index mit dem Namen `/oak:index/acme.product-custom-1`, um in einer neuen Version der Anwendung und höher verwendet zu werden, muss der Index wie folgt konfiguriert werden:

`acme.product-1-custom-1`

Diese Konfiguration funktioniert, indem dem Indexnamen eine benutzerdefinierte Kennung vorangestellt wird, gefolgt von einem Punkt (**`.`**). Der Bezeichner sollte zwischen 2 und 5 Zeichen lang sein.

Wie oben erläutert, stellt diese Konfiguration sicher, dass der Index nur von der neuen Version der Anwendung verwendet wird.

### Ändern eines Index {#changing-an-index}

Wenn ein vorhandener Index geändert wird, muss ein neuer Index mit der geänderten Indexdefinition hinzugefügt werden. Angenommen, der vorhandene Index `/oak:index/acme.product-custom-1` wird geändert. Der alte Index wird unter `/oak:index/acme.product-custom-1`, der neue Index unter `/oak:index/acme.product-custom-2` gespeichert.

Die alte Version des Programms nutzt die folgende Konfiguration:

`/oak:index/acme.product-custom-1`

Die neue Version des Programms nutzt die folgende (geänderte) Konfiguration:

`/oak:index/acme.product-custom-2`

>[!NOTE]
>
>Die Indexdefinitionen für AEM as a Cloud Service stimmen möglicherweise nicht vollständig mit den Indexdefinitionen für eine lokale Entwicklungsinstanz überein. Die Entwicklungsinstanz verfügt nicht über eine Tika-Konfiguration, während Instanzen von AEM as a Cloud Service eine haben. Wenn Sie einen Index mit einer Tika-Konfiguration anpassen, behalten Sie die Tika-Konfiguration bei.

### Rückgängigmachen einer Änderung {#undoing-a-change}

Manchmal muss eine Änderung der Indexdefinition rückgängig gemacht werden. etwa wenn eine Änderung versehentlich vorgenommen wurde oder aber nicht mehr erforderlich ist. Beispiel: Die Indexdefinition `damAssetLucene-8-custom-3` wurde versehentlich erstellt und bereits bereitgestellt. Daher empfiehlt es sich, zur vorherigen Indexdefinition `damAssetLucene-8-custom-2` zurückkehren. Fügen Sie dazu einen Index mit dem Namen `damAssetLucene-8-custom-4` , der die Definition des vorherigen Index enthält, `damAssetLucene-8-custom-2`.

### Entfernen eines Index {#removing-an-index}

Nachfolgendes gilt nur für anwenderdefinierte Indizes. Produktindizes können nicht entfernt werden, da sie von AEM verwendet werden.

Wenn ein Index in einer späteren Version der Anwendung entfernt wird, können Sie einen leeren Index (einen leeren Index, der nie verwendet wird und keine Daten enthält) mit einem neuen Namen definieren. Für dieses Beispiel können Sie ihn `/oak:index/acme.product-custom-3`. Dieser Name ersetzt den Index `/oak:index/acme.product-custom-2`. Nachher `/oak:index/acme.product-custom-2` vom System entfernt wird, wird der leere Index `/oak:index/acme.product-custom-3` kann dann entfernt werden. Beispiel für einen solchen leeren Index:

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

Apache Jackrabbit Oak ermöglicht flexible Indexkonfigurationen zur effizienten Verarbeitung von Suchabfragen. Indizes sind besonders für größere Repositorys wichtig. Stellen Sie sicher, dass alle Abfragen durch einen geeigneten Index gesichert werden. Abfragen ohne geeigneten Index können Tausende von Knoten lesen, die dann als Warnung protokolliert werden.

Siehe [dieses Dokuments](query-and-indexing-best-practices.md) für Informationen zur Optimierung von Abfragen und Indizes.
