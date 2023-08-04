---
title: Inhaltssuche und -indizierung
description: Erfahren Sie mehr über die Inhaltssuche und -indizierung in AEM as a Cloud Service.
exl-id: 4fe5375c-1c84-44e7-9f78-1ac18fc6ea6b
source-git-commit: 8c73805b6ed1b7a03c65b4d21a4252c1412a5742
workflow-type: tm+mt
source-wordcount: '2325'
ht-degree: 39%

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
1. Auf hoher Ebene auf AEM as a Cloud Service mit der Einführung der [Rollierendes Bereitstellungsmodell](#index-management-using-rolling-deployments), gibt es zwei Indexsätze: einen für die alte Version und einen für die neue Version.
1. Kunden können sehen, ob der Indizierungsauftrag auf der Build-Seite von Cloud Manager abgeschlossen ist, und erhalten eine Benachrichtigung, wenn die neue Version für den Traffic bereit ist.

Beschränkungen:

* Derzeit wird die Indexverwaltung in AEM as a Cloud Service nur für Indizes des Typs `lucene` unterstützt.
* Es werden nur Standard-Analyzer unterstützt (d. h. die Analyzer, die im Lieferumfang des Produkts enthalten sind). Benutzerdefinierte Analyzer werden nicht unterstützt.
* Intern können andere Indizes konfiguriert und für Abfragen verwendet werden. Zum Beispiel Abfragen, die gegen für den `damAssetLucene`-Index geschrieben wurden, können auf Skyline tatsächlich für eine Elasticsearch-Version dieses Index ausgeführt werden. Dieser Unterschied ist normalerweise für die Anwendung und den Benutzer nicht sichtbar. Allerdings sind bestimmte Tools wie die `explain` -Funktion einen anderen Index anzeigen. Unterschiede zwischen Lucene-Indizes und Elastic-Indizes finden Sie unter [die Elastic-Dokumentation in Apache Jackrabbit Oak](https://jackrabbit.apache.org/oak/docs/query/elastic.html). Kunden müssen und können keine Elasticsearch-Indizes direkt konfigurieren.
* Suche nach ähnlichen Funktionsvektoren (`useInSimilarity = true`) wird nicht unterstützt.

## Verwendung {#how-to-use}

Indexdefinitionen können wie folgt in drei primäre Anwendungsfälle kategorisiert werden:

1. **Hinzufügen** eine neue benutzerdefinierte Indexdefinition.
2. **Aktualisieren** eine vorhandene Indexdefinition durch Hinzufügen einer neuen Version.
3. **Entfernen** eine Indexdefinition, die nicht mehr erforderlich ist.

Für die Punkte 1 und 2 müssen Sie als Teil Ihrer benutzerspezifischen Code-Basis im jeweiligen Release-Plan für Cloud Manager eine neue Indexdefinition erstellen. Weitere Informationen finden Sie unter [Bereitstellen in AEM as a Cloud Service](/help/implementing/deploying/overview.md) Dokumentation.

## Indexnamen {#index-names}

Eine Indexdefinition kann in eine der folgenden Kategorien unterteilt werden:

1. Vordefinierter OOTB-Index. Beispiel: `/oak:index/cqPageLucene-2` oder `/oak:index/damAssetLucene-8`.

2. Anpassung eines OOTB-Index. Diese werden durch Anfügen von `-custom-` gefolgt von einer numerischen Kennung zum ursprünglichen Indexnamen. Beispiel: `/oak:index/damAssetLucene-8-custom-1`.

3. Vollständig benutzerdefinierter Index: Es ist möglich, einen völlig neuen Index von Grund auf neu zu erstellen. Ihr Name muss über ein Präfix verfügen, um Namenskonflikte zu vermeiden. Beispiel: `/oak:index/acme.product-1-custom-2`, wobei das Präfix `acme.`

## Vorbereiten der neuen Indexdefinition {#preparing-the-new-index-definition}

>[!NOTE]
>
>Wenn Sie beispielsweise einen vorkonfigurierten Index anpassen, z. B. `damAssetLucene-8`, kopieren Sie bitte die neueste vorkonfigurierte Indexdefinition aus einer *Cloud Service-Umgebung* mithilfe des CRX DE Package Manager (`/crx/packmgr/`). Umbenennen in `damAssetLucene-8-custom-1` (oder höher) und fügen Sie Ihre Anpassungen in die XML-Datei ein. Dadurch wird sichergestellt, dass die erforderlichen Konfigurationen nicht versehentlich entfernt werden. Beispiel: der Knoten `tika` unter `/oak:index/damAssetLucene-8/tika` ist im angepassten Index des Cloud-Service erforderlich. Er existiert nicht im Cloud-SDK.

Für Anpassungen eines OOTB-Index erstellen Sie ein neues Paket, das die tatsächliche Indexdefinition enthält, die diesem Namensmuster folgt:

`<indexName>-<productVersion>-custom-<customVersion>`

Für einen vollständig angepassten Index erstellen Sie ein neues Indexdefinitionspaket, das die Indexdefinition enthält, die diesem Namensmuster folgt:

`<prefix>.<indexName>-<productVersion>-custom-<customVersion>`

<!-- Alexandru: temporarily drafting this statement due to CQDOC-17701

The package from the above sample is built as `com.adobe.granite:new-index-content:zip:1.0.0-SNAPSHOT`. -->

>[!NOTE]
>
>Für jedes Inhaltspaket, das Indexdefinitionen enthält, sollten die folgenden Eigenschaften in der Eigenschaftendatei des Inhaltspakets festgelegt sein, das sich unter `<package_name>/META-INF/vault/properties.xml`:
>
> * `noIntermediateSaves=true`
>
> * `allowIndexDefinitions=true`

## Bereitstellen von benutzerdefinierten Indexdefinitionen {#deploying-custom-index-definitions}

So veranschaulichen Sie die Bereitstellung einer angepassten Version des vordefinierten Index `damAssetLucene-8`, werden wir eine schrittweise Anleitung geben. In diesem Beispiel werden wir ihn umbenennen in `damAssetLucene-8-custom-1`. Dann läuft der Prozess wie folgt ab:

1. Erstellen Sie einen neuen Ordner mit dem aktualisierten Indexnamen im `ui.apps` directory:
   * Beispiel: `ui.apps/src/main/content/jcr_root/_oak_index/damAssetLucene-8-custom-1/`

2. Konfigurationsdatei hinzufügen `.content.xml` mit den benutzerdefinierten Konfigurationen im neu erstellten Ordner. Nachfolgend finden Sie ein Beispiel für eine Anpassung: Dateiname: `ui.apps/src/main/content/jcr_root/_oak_index/damAssetLucene-8-custom-1/.content.xml`

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:jcr="http://www.jcp.org/jcr/1.0" xmlns:dam="http://www.day.com/dam/1.0" xmlns:nt="http://www.jcp.org/jcr/nt/1.0" xmlns:oak="http://jackrabbit.apache.org/oak/ns/1.0" xmlns:rep="internal"
       jcr:mixinTypes="[rep:AccessControllable]"
       jcr:primaryType="oak:QueryIndexDefinition"
       async="[async,nrt]"
       compatVersion="{Long}2"
       evaluatePathRestrictions="{Boolean}true"
       includedPaths="[/content/dam]"
       maxFieldLength="{Long}100000"
       type="lucene">
       <facets
           jcr:primaryType="nt:unstructured"
           secure="statistical"
           topChildren="100"/>
       <indexRules jcr:primaryType="nt:unstructured">
           <dam:Asset jcr:primaryType="nt:unstructured">
               <properties jcr:primaryType="nt:unstructured">
                   <cqTags
                       jcr:primaryType="nt:unstructured"
                       name="jcr:content/metadata/cq:tags"
                       nodeScopeIndex="{Boolean}true"
                       propertyIndex="{Boolean}true"
                       useInSpellcheck="{Boolean}true"
                       useInSuggest="{Boolean}true"/>
               </properties>
           </dam:Asset>
       </indexRules>
       <tika jcr:primaryType="nt:folder">
           <config.xml jcr:primaryType="nt:file"/>
       </tika>
   </jcr:root>
   ```

3. Hinzufügen eines Eintrags zum FileVault-Filter in `ui.apps/src/main/content/META-INF/vault/filter.xml`:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <workspaceFilter version="1.0">
       ...
       <filter root="/oak:index/damAssetLucene-8-custom-1"/> 
   </workspaceFilter>
   ```

4. Fügen Sie eine Konfigurationsdatei für Apache Tika in hinzu: `ui.apps/src/main/content/jcr_root/_oak_index/damAssetLucene-8-custom-1/tika/config.xml`:

   ```xml
   <properties>
       <detectors>
           <detector class="org.apache.tika.detect.TypeDetector"/>
       </detectors>
       <parsers>
           <parser class="org.apache.tika.parser.DefaultParser">
           <mime>text/plain</mime>
           </parser>
       </parsers>
       <service-loader initializableProblemHandler="ignore" dynamic="true"/>
   </properties>
   ```

5. Stellen Sie sicher, dass Ihre Konfiguration den Richtlinien entspricht, die im Abschnitt [Projektkonfiguration](#project-configuration) Abschnitt. Nehmen Sie die erforderlichen Anpassungen vor.

## Projektkonfiguration

Es wird dringend empfohlen, Version >= zu verwenden. `1.3.2` des Jackrabbit `filevault-package-maven-plugin`. Die Schritte zur Integration in Ihr Projekt lauten wie folgt:

1. Aktualisieren der Version auf der obersten Ebene `pom.xml`:

   ```xml
   <plugin>
       <groupId>org.apache.jackrabbit</groupId>
           <artifactId>filevault-package-maven-plugin</artifactId>
           ...
           <version>1.3.2</version>
       ...
   </plugin>
   ```

2. Fügen Sie der obersten Ebene Folgendes hinzu: `pom.xml`:

   ```xml
   <jackrabbit-packagetype>
       <options>   
           <immutableRootNodeNames>apps,libs,oak:index</immutableRootNodeNames>
       </options>
   </jackrabbit-packagetype>
   ```

   Hier finden Sie ein Beispiel für die oberste Ebene des Projekts `pom.xml` -Datei mit den oben genannten Konfigurationen enthalten:

   Dateiname: `pom.xml`

   ```xml
   <plugin>
       <groupId>org.apache.jackrabbit</groupId>
           <artifactId>filevault-package-maven-plugin</artifactId>
           ...
           <version>1.3.2</version>
           <configuration>
               ...
               <validatorsSettings>
                   <jackrabbit-packagetype>
                       <options>
                           <immutableRootNodeNames>apps,libs,oak:index</immutableRootNodeNames>
                       </options>
                   </jackrabbit-packagetype>
                   ...
               ...
   </plugin>
   ```

3. In `ui.apps/pom.xml` und `ui.apps.structure/pom.xml` es erforderlich ist, die `allowIndexDefinitions` und `noIntermediateSaves` Optionen in `filevault-package-maven-plugin`. Aktivieren `allowIndexDefinitions` ermöglicht benutzerdefinierte Indexdefinitionen, während `noIntermediateSaves` stellt sicher, dass die Konfigurationen automatisch hinzugefügt werden.

   Dateinamen: `ui.apps/pom.xml` und `ui.apps.structure/pom.xml`

   ```xml
   <plugin>
       <groupId>org.apache.jackrabbit</groupId>
           <artifactId>filevault-package-maven-plugin</artifactId>
           <configuration>
               <allowIndexDefinitions>true</allowIndexDefinitions>
               <properties>
                   <cloudManagerTarget>none</cloudManagerTarget>
                   <noIntermediateSaves>true</noIntermediateSaves>
               </properties>
       ...
   </plugin>
   ```

4. Filter hinzufügen für `/oak:index` in `ui.apps.structure/pom.xml`:

   ```xml
   <filters>
       ...
       <filter><root>/oak:index</root></filter>
   </filters>
   ```

Stellen Sie nach dem Hinzufügen der neuen Indexdefinition die neue Anwendung mithilfe von Cloud Manager bereit. Diese Bereitstellung initiiert zwei Aufträge, die für das Hinzufügen (und gegebenenfalls das Zusammenführen) der Indexdefinitionen zu MongoDB und Azure Segment Store für Autoren- und Veröffentlichungszwecke verantwortlich sind. Vor dem Wechsel werden die zugrunde liegenden Repositorys einer Neuindizierung mit den aktualisierten Indexdefinitionen unterzogen.

>[!TIP]
>
>Weitere Informationen zur erforderlichen Paketstruktur für AEM as a Cloud Service finden Sie im Dokument [AEM-Projektstruktur](/help/implementing/developing/introduction/aem-project-content-package-structure.md).

## Indexverwaltung mithilfe von rollierenden Implementierungen {#index-management-using-rolling-deployments}

### Was ist Indexverwaltung? {#what-is-index-management}

Bei der Indexverwaltung geht es darum, Indizes hinzuzufügen, zu entfernen und zu ändern. Eine Änderung der *Definition* eines Index geht schnell, doch die Anwendung der Änderung (häufig als „Erstellen eines Index“ oder bei vorhandenen Indizes als „Neuindizierung“ bezeichnet) erfordert Zeit. Es ist nicht sofort: Das Repository muss auf indizierte Daten überprüft werden.

### Rollierende Implementierungen {#what-are-rolling-deployments}

Eine rollierende Implementierung kann Ausfallzeiten reduzieren. Sie ermöglicht Upgrades ohne Ausfallzeiten sowie schnelle Rollbacks. Die alte Version der Anwendung wird gleichzeitig mit der neuen Version der Anwendung ausgeführt.

### Schreibgeschützte Bereiche und Bereiche mit Lese-Schreib-Zugriff {#read-only-and-read-write-areas}

Bestimmte Bereiche des Repositorys (schreibgeschützte Teile des Repositorys) können in der alten und in der neuen Version der Anwendung unterschiedlich sein. Die schreibgeschützten Bereiche des Repositorys sind normalerweise `/app` und `/libs`. Im folgenden Beispiel wird Kursivschrift verwendet, um schreibgeschützte Bereiche zu markieren, während Fettschrift für Bereiche mit Lese-Schreib-Zugriff steht.

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

Bei rollierenden Implementierungen gibt es keine Ausfallzeiten. Während einer Aktualisierung werden sowohl die alte Version (z. B. Version 1) der Anwendung als auch die neue Version (Version 2) gleichzeitig für dasselbe Repository ausgeführt. Wenn für Version 1 ein bestimmter Index verfügbar sein muss, darf dieser Index in Version 2 nicht entfernt werden. Der Index sollte später entfernt werden, z. B. in Version 3. Ab diesem Zeitpunkt ist garantiert, dass Version 1 der Anwendung nicht mehr ausgeführt wird. Außerdem sollten Programme so geschrieben werden, dass Version 1 gut funktioniert, auch wenn Version 2 ausgeführt wird und Indizes von Version 2 verfügbar sind.

Nach Abschluss der Aktualisierung auf die neue Version können alte Indizes vom System entfernt werden. Die alten Indizes bleiben möglicherweise noch einige Zeit, um Rollbacks zu beschleunigen (falls ein Rollback erforderlich sein sollte).

Die folgende Tabelle zeigt fünf Indexdefinitionen: der Index `cqPageLucene` wird in beiden Versionen verwendet, während der Index `damAssetLucene-custom-1` nur in Version 2 zum Einsatz kommt.

>[!NOTE]
>
>Die `<indexName>-custom-<customerVersionNumber>` ist erforderlich, damit AEM as a Cloud Service als Ersatz für einen vorhandenen Index markiert werden kann.

| Index | Vordefinierter Index | Verwendung in Version 1 | Verwendung in Version 2 |
|---|---|---|---|
| /oak:index/damAssetLucene | Ja | Ja | Nein |
| /oak:index/damAssetLucene-custom-1 | Ja (angepasst) | Nein | Ja |
| /oak:index/acme.product-custom-1 | Nein | Ja | Nein |
| /oak:index/acme.product-custom-2 | Nein | Nein | Ja |
| /oak:index/cqPageLucene | Ja | Ja | Ja |

Die Versionsnummer wird bei jeder Indexänderung inkrementiert. Um zu vermeiden, dass benutzerspezifische Indexnamen mit den Indexnamen des Produkts selbst kollidieren, müssen benutzerdefinierte Indizes und Änderungen an vordefinierten Indizes mit `-custom-<number>`.

### Änderungen an vordefinierten Indizes {#changes-to-out-of-the-box-indexes}

Nachdem die Adobe einen vordefinierten Index wie &quot;damAssetLucene&quot;oder &quot;cqPageLucene&quot;ändert, wird ein neuer Index mit dem Namen `damAssetLucene-2` oder `cqPageLucene-2` erstellt wird. Oder wenn der Index bereits angepasst wurde, wird die angepasste Indexdefinition mit den Änderungen im vordefinierten Index zusammengeführt, wie unten dargestellt. Die Zusammenführung von Änderungen erfolgt automatisch. Das bedeutet, dass Sie nichts tun müssen, wenn sich ein vordefinierter Index ändert. Der Index lässt sich jedoch später erneut anpassen.

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

Manchmal ist es erforderlich, eine Änderung in einer Indexdefinition rückgängig zu machen. Dies kann auf einen versehentlichen Fehler zurückzuführen sein oder die Änderung ist nicht mehr erforderlich. Nehmen wir beispielsweise die Indexdefinition `damAssetLucene-8-custom-3,` , die versehentlich erstellt wurde und bereits bereitgestellt wurde. Daher möchten Sie zur vorherigen Indexdefinition zurückkehren. `damAssetLucene-8-custom-2.` Dazu müssen Sie einen neuen Index mit dem Namen `damAssetLucene-8-custom-4` die die Definition aus dem vorherigen Index enthält, `damAssetLucene-8-custom-2.`

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
