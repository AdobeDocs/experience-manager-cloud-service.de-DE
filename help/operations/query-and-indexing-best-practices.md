---
title: Best Practices für Abfragen und Indizierung
description: Erfahren Sie, wie Sie Ihre Indizes und Abfragen anhand der Best-Practice-Richtlinien von Adobe optimieren können.
topic-tags: best-practices
exl-id: 37eae99d-542d-4580-b93f-f454008880b1
source-git-commit: ddd67a69bea2e2109ce93a91f42e8f365424f80f
workflow-type: tm+mt
source-wordcount: '3144'
ht-degree: 46%

---

# Best Practices für Abfragen und Indizierung {#query-and-indexing-best-practices}

In AEM as a Cloud Service sind alle operativen Aspekte der Indizierung automatisiert. Dadurch können sich Personen, die mit der Entwicklung befasst sind, auf das Erstellen effizienter Abfragen und der entsprechenden Indexdefinitionen konzentrieren.

## Verwenden von Abfragen {#when-to-use-queries}

Abfragen sind eine Möglichkeit, auf Inhalte zuzugreifen, aber nicht die einzige. In vielen Fällen ist der Zugriff auf Inhalte im Repository auf eine andere Weise effektiver. Sie sollten überlegen, ob Abfragen der beste und effizienteste Weg sind, für Ihren Anwendungsfall auf Inhalte zuzugreifen.

### Repository- und Taxonomie-Design {#repository-and-taxonomy-design}

Bei der Erstellung der Taxonomie eines Repositorys müssen mehrere Faktoren berücksichtigt werden. Hierzu gehören die Zugriffssteuerung, Lokalisierung, Vererbung von Komponenten- und Seiteneigenschaften und vieles mehr.

In einem Taxonomie-Design, in dem diese Punkte berücksichtigt werden, muss zudem auch die „Durchlauffähigkeit“ des Index-Designs beachtet werden. In diesem Zusammenhang ist die Durchlauffähigkeit die Fähigkeit einer Taxonomie, einen vorhersehbaren Zugriff auf Inhalte auf der Grundlage ihres Pfads zu ermöglichen. Dies ermöglicht ein effizienteres System, das einfacher zu verwalten ist als ein System, für das mehrere Abfragen ausgeführt werden müssen.

Darüber hinaus muss beim Entwerfen einer Taxonomie bedacht werden, ob eine Sortierung wichtig ist. Wenn auf eine explizite Sortierung verzichtet werden kann und eine große Anzahl gleichgeordneter Knoten erwartet wird, sind unsortierte Knotentypen wie `sling:Folder` oder `oak:Unstructured` vorzuziehen. Ist eine Sortierung erforderlich, wären `nt:unstructured` und `sling:OrderedFolder` besser geeignet.

### Abfragen in Komponenten {#queries-in-components}

Da Abfragen zu den stärker belastenden Vorgängen in einem AEM-System gehören können, empfiehlt es sich, diese in Ihren Komponenten zu vermeiden. Wenn beim Rendern einer Seite mehrere Abfragen gleichzeitig ausgeführt werden, kann dies die Leistung des Systems beeinträchtigen. Es gibt zwei Strategien, mit denen sich beim Rendering von Komponenten die Ausführung von Abfragen vermeiden lässt: **[Durchlaufen von Knoten](#traversing-nodes)** und **[Vorabrufen von Ergebnissen](#prefetching-results)**.

### Durchlaufen von Knoten {#traversing-nodes}

Wenn das Repository so konzipiert ist, dass eine vorherige Kenntnis des Speicherorts der erforderlichen Daten möglich ist, kann Code, der diese Daten aus den erforderlichen Pfaden abruft, bereitgestellt werden, ohne Abfragen ausführen zu müssen, um sie zu finden.

Ein Beispiel hierfür wäre das Rendern von Inhalten, die zu einer bestimmten Kategorie passen. Ein Ansatz wäre, den Inhalt mit einer Kategorieeigenschaft zu organisieren, die abgefragt werden kann, um eine Komponente mit Elementen einer Kategorie aufzufüllen.

Besser wäre es allerdings, diesen Inhalt in einer Taxonomie nach Kategorie zu strukturieren, damit er manuell abgerufen werden kann.

Angenommen, der Inhalt wird in einer Taxonomie wie der folgenden gespeichert:

```xml
/content/myUnstructuredContent/parentCategory/childCategory/contentPiece
```

In diesem Fall lässt sich der Knoten `/content/myUnstructuredContent/parentCategory/childCategory` einfach abrufen und seine untergeordneten Elemente können analysiert und zum Rendern der Komponente verwendet werden.

Bei einem kleinen oder homogenen Ergebnissatz kann es außerdem schneller sein, das Repository zu durchlaufen und dabei die erforderlichen Knoten zu erfassen, statt eine Abfrage zu erstellen, die denselben Ergebnissatz zurückgibt. Generell sollten Abfragen vermieden werden, soweit dies möglich ist.

### Vorabruf der Ergebnisse {#prefetching-results}

Mitunter lassen die Inhalte oder Anforderungen im Zusammenhang mit der Komponente nicht zu, dass Knoten zum Abrufen der erforderlichen Daten durchlaufen werden. In solchen Fällen müssen die erforderlichen Abfragen vor dem Rendern der Komponente ausgeführt werden, damit eine optimale Leistung sichergestellt werden kann.

Sofern die für die Komponente erforderlichen Ergebnisse zum Zeitpunkt der Erstellung ermittelt werden können und nicht zu erwarten ist, dass sich der Inhalt ändert, kann die Abfrage nach einer Änderung ausgeführt werden.

Wenn sich die Daten oder Inhalte regelmäßig ändern, kann die Abfrage planmäßig oder über einen Listener für Aktualisierungen der zugrunde liegenden Daten ausgeführt werden. Anschließend können die Ergebnisse in einen freigegebenen Speicherort im Repository geschrieben werden. Alle Komponenten, die diese Daten benötigen, können dann die Werte aus diesem einzelnen Knoten beziehen, ohne eine Abfrage zur Laufzeit auszuführen.

Eine ähnliche Strategie kann verwendet werden, um das Ergebnis in einem Arbeitsspeicher-Cache zu speichern, der beim Start gefüllt und bei jeder Änderung aktualisiert wird (mithilfe eines JCR-Elements `ObservationListener` oder eines Sling-Elements `ResourceChangeListener`).

## Optimieren von Abfragen {#optimizing-queries}

Die Oak-Dokumentation bietet eine [allgemeine Übersicht über die Ausführung von Abfragen.](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#query-processing) Dies bildet die Grundlage für alle in diesem Dokument beschriebenen Optimierungsaktivitäten.

AEM as a Cloud Service stellt die [Tool zur Abfrageleistung](#query-performance-tool), die die Implementierung effizienter Abfragen unterstützen soll.

* Dabei werden bereits ausgeführte Abfragen mit ihren jeweiligen Leistungsmerkmalen und dem Abfrageplan angezeigt.
* Die Durchführung von Ad-hoc-Abfragen ist auf verschiedenen Ebenen möglich, von der bloßen Anzeige des Abfrageplans bis zur Ausführung der vollständigen Abfrage.

Das Abfrageleistungs-Tool kann über die [Entwicklerkonsole in Cloud Manager aufgerufen werden.](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html?lang=de#queries) Das Abfrageleistungs-Tool von AEM as a Cloud Service liefert mehr Informationen über die Details der Abfrageausführung als die AEM 6.x-Versionen.

Dieses Diagramm zeigt den allgemeinen Ablauf zur Verwendung des Abfrageleistungs-Tools zur Optimierung von Abfragen.

![Fluss der Optimierung von Abfragen](assets/query-optimization-flow.png)

### Verwenden eines Index {#use-an-index}

Jede Abfrage sollte einen Index verwenden, um eine optimale Leistung zu erzielen. In den meisten Fällen sollten die vorhandenen, vordefinierten Indizes für die Verarbeitung von Abfragen ausreichen.

Manchmal müssen jedoch benutzerdefinierte Eigenschaften zu einem vorhandenen Index hinzugefügt werden, damit zusätzliche Einschränkungen mithilfe des Index abgefragt werden können. Weitere Informationen finden Sie im Dokument [Inhaltssuche und -indizierung](/help/operations/indexing.md#changing-an-index). Die [JCR-Abfrage-Schnellübersicht](#jcr-query-cheatsheet) -Abschnitt dieses Dokuments beschreibt, wie eine Eigenschaftsdefinition in einem Index aussehen muss, um einen bestimmten Abfragetyp zu unterstützen.

### Verwenden der richtigen Kriterien {#use-the-right-criteria}

Die primäre Beschränkung für jede Abfrage sollte eine Eigenschaftsübereinstimmung sein, da dies der effizienteste Typ ist. Durch das Hinzufügen von mehr Eigenschaftsbeschränkungen wird das Ergebnis weiter eingeschränkt.

Die Abfrage-Engine berücksichtigt nur einen einzigen Index. Das bedeutet, dass ein vorhandener Index angepasst werden kann und sollte, indem weitere benutzerdefinierte Indexeigenschaften hinzugefügt werden.

Im Abschnitt [JCR-Abfrage-Schnellübersicht](#jcr-query-cheatsheet) dieses Dokuments werden die verfügbaren Einschränkungen aufgelistet. Außerdem wird erläutert, wie eine Indexdefinition aussehen muss, damit sie aufgenommen wird. Verwenden Sie das [Abfrageleistungs-Tool](#query-performance-tool), um die Abfrage zu testen und sicherzustellen, dass der richtige Index verwendet wird und dass die Abfrage-Engine keine Begrenzungen außerhalb des Index auswerten muss.

### Reihenfolge {#ordering}

Wenn für das Ergebnis eine bestimmte Reihenfolge angefordert wird, gibt es zwei Möglichkeiten, dies durch die Abfrage-Engine zu erreichen:

1. Der Index kann das Ergebnis vollständig und in der richtigen Reihenfolge liefern.
   * Dies funktioniert, wenn die Eigenschaften, die für die Sortierung verwendet werden, in der Indexdefinition mit `ordered=true` annotiert sind.
1. Die Abfrage-Engine führt den Sortiervorgang durch.
   * Dies kann vorkommen, wenn die Abfrage-Engine die Filterung außerhalb des Index durchführt oder die Sortiereigenschaft nicht mit der Eigenschaft `ordered=true` annotiert ist.
   * Dies erfordert, dass der vollständige Ergebnissatz zum Sortieren in den Speicher gelesen wird, was viel langsamer ist als die erste Option.

### Beschränken der Ergebnisgröße {#restrict-result-size}

Die abgerufene Größe des Abfrageergebnisses ist ein wichtiger Faktor für die Abfrageleistung. Da das Abrufen des Ergebnisses nach einem wenig effektiven Verfahren erfolgt, gibt es einen Unterschied beim Abrufen der ersten 20 Ergebnisse im Vergleich zum Abrufen von 10.000 Ergebnissen, sowohl in Bezug auf die Laufzeit als auch den Speicherbedarf.

Dies bedeutet auch, dass die Größe der Ergebnismenge nur korrekt bestimmt werden kann, wenn alle Ergebnisse abgerufen werden. Aus diesem Grund sollte die Menge der abgerufenen Ergebnisse immer begrenzt werden, entweder durch Erweiterung der Abfrage (siehe die [JCR-Abfrage-Schnellübersicht](#jcr-query-cheatsheet) in diesem Dokument) oder durch Begrenzung der Lesezugriffe auf die Ergebnisse.

Eine solche Begrenzung verhindert auch, dass die Abfrage-Engine die **Ausnahmegrenze** von 100.000 Knoten erreicht, was zu einem erzwungenen Stopp der Abfrage führt.

Siehe Abschnitt . [Abfragen mit großen Ergebnismengen](#queries-with-large-result-sets) dieses Dokuments, wenn eine potenziell große Ergebnismenge vollständig verarbeitet werden muss.

## Tool zur Abfrageleistung {#query-performance-tool}

Das Tool zur Abfrageleistung (unter `/libs/granite/operations/content/diagnosistools/queryPerformance.html` und verfügbar über [Entwicklerkonsole in Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html?lang=de#queries)) bietet -
* Eine Liste aller &quot;Langsamen Abfragen&quot;; derzeit definiert als solche, die mehr als 5000 Zeilen lesen/scannen.
* Liste der &quot;beliebten Abfragen&quot;
* Das Tool &quot;Abfrage erläutern&quot;, um zu verstehen, wie eine bestimmte Abfrage von Oak ausgeführt wird.

![Tool zur Abfrageleistung](assets/query-performance-tool.png)

Die Tabellen &quot;Langsame Abfragen&quot;und &quot;Beliebte Abfragen&quot;umfassen:
* Die Abfrageanweisung selbst.
* Details des letzten Thread, der die Abfrage ausgeführt hat, sodass die Seite oder die Anwendungsfunktion identifiziert werden kann, die die Abfrage ausführt.
* Ein &quot;Leseoptimierungswert&quot;für die Abfrage.
   * Dies wird als Verhältnis zwischen der Anzahl der Zeilen/Knoten berechnet, die zur Ausführung der Abfrage überprüft werden, und der Anzahl der gelesenen übereinstimmenden Ergebnisse.
   * Eine Abfrage, für die jede Einschränkung (und jede Bestellung) am Index verarbeitet werden kann, ergibt in der Regel 90 % oder mehr.
* Details zur maximalen Zeilenanzahl -
   * Gelesen - gibt an, dass eine Zeile Teil eines Ergebnissatzes war.
   * Gescannt - gibt an, dass eine Zeile in den Ergebnissen der zugrunde liegenden Indexabfrage (im Fall einer indizierten Abfrage) enthalten oder aus dem Nodestore gelesen wurde (im Falle einer Repository-Durchlaufphase).

Diese Tabellen helfen bei der Identifizierung von Abfragen, die nicht vollständig indiziert sind (siehe [Verwenden eines Index](#use-an-index) oder lesen Sie zu viele Knoten (siehe auch [Repository-Durchlauf](#repository-traversal) und [Indexdurchlauf](#index-traversal)). Diese Fragen werden hervorgehoben, wobei die entsprechenden Problembereiche rot markiert sind.

Die `Reset Statistics` wird bereitgestellt, um alle in den Tabellen erfassten vorhandenen Statistiken zu entfernen. Dies ermöglicht die Ausführung einer bestimmten Abfrage (entweder über die Anwendung selbst oder das Tool Abfrage erläutern ) und die Analyse der Ausführungsstatistiken.

### Abfrage erläutern

Mit dem Tool Abfrage erklären können Entwickler den Ausführungsplan für Abfragen verstehen (siehe [Lesen des Abfrageausführungsplans](#reading-query-execution-plan)), einschließlich Details zu allen Indizes, die bei der Ausführung der Abfrage verwendet werden. Dies kann verwendet werden, um zu verstehen, wie effektiv eine Abfrage indiziert wird, um ihre Leistung vorherzusagen oder rückwirkend zu analysieren.

#### Abfrage erläutern

Gehen Sie wie folgt vor, um eine Abfrage zu erklären:
* Wählen Sie die entsprechende Abfragesprache mithilfe der `Language` Dropdown.
* Geben Sie die Abfrage-Anweisung in die `Query` -Feld.
* Wählen Sie bei Bedarf mithilfe der bereitgestellten Kontrollkästchen aus, wie die Abfrage ausgeführt werden soll.
   * Standardmäßig müssen keine JCR-Abfragen ausgeführt werden, um den Ausführungsplan für Abfragen zu identifizieren (dies ist bei QueryBuilder-Abfragen nicht der Fall).
   * Zur Ausführung der Abfrage stehen drei Optionen zur Verfügung:
      * `Include Execution Time` - Führen Sie die Abfrage aus, versuchen Sie jedoch nicht, Ergebnisse zu lesen.
      * `Read first page of results` - Führen Sie die Abfrage aus und lesen Sie die erste &quot;Seite&quot;mit 20 Ergebnissen (Replikation der Best Practices für die Ausführung von Abfragen).
      * `Include Node Count` - die Abfrage ausführen und die gesamte Ergebnismenge lesen (im Allgemeinen wird dies nicht empfohlen - siehe [Indexdurchlauf](#index-traversal)).

#### Popup für Abfrageerläuterung {#query-explanation-popup}

![Popup für Abfrageerläuterung](./assets/query-explanation-popup.png)

Nach Auswahl `Explain`, wird dem Benutzer ein Popup angezeigt, in dem das Ergebnis der Abfragebeschreibung (und der Ausführung, falls ausgewählt) beschrieben wird.
Dieses Popup enthält Details zu -
* Die Indizes, die bei der Ausführung der Abfrage verwendet werden (oder kein Index, wenn die Abfrage mit [Repository-Durchlauf](#repository-traversal)).
* Ausführungszeit (wenn `Include Execution Time` Kontrollkästchen aktiviert wurde) und Anzahl der gelesenen Ergebnisse (wenn `Read first page of results` oder `Include Node Count` -Kontrollkästchen aktiviert haben).
* Ausführungsplan, der eine detaillierte Analyse der Ausführung der Abfrage ermöglicht - siehe [Lesen des Abfrageausführungsplans](#reading-query-execution-plan) für die Interpretation.
* Die Pfade der ersten 20 Abfrageergebnisse (wenn `Read first page of results` Kontrollkästchen aktiviert)
* Die vollständigen Logs der Abfrageplanung, die die relativen Kosten der Indizes anzeigen, die für die Ausführung dieser Abfrage berücksichtigt wurden (der Index mit den niedrigsten Kosten ist der ausgewählte Index).

#### Lesen des Abfrageausführungsplans {#reading-query-execution-plan}

Der Abfrageausführungsplan enthält alle erforderlichen Informationen, um die Leistung einer bestimmten Abfrage vorherzusagen (oder zu erläutern). Verstehen Sie, wie effizient die Abfrage ausgeführt wird, indem Sie die Einschränkungen und die Reihenfolge in der ursprünglichen JCR- (oder Query Builder-) Abfrage mit der im zugrunde liegenden Index (Lucene, Elastic oder Property) ausgeführten Abfrage vergleichen.

Beachten Sie die folgende Abfrage:

```
/jcr:root/content/dam//element(*, dam:Asset) [jcr:content/metadata/dc:title = "My Title"] order by jcr:created
```

... enthält -
* 3 Beschränkungen
   * Knotentyp (`dam:Asset`)
   * Pfad (untergeordnete Elemente von `/content/dam`)
   * Eigenschaft (`jcr:content/metadata/dc:title = "My Title"`)
* Bestellung durch die `jcr:created` property

Erläuterung der Abfrageergebnisse im folgenden Plan -

```
[dam:Asset] as [a] /* lucene:damAssetLucene-9(/oak:index/damAssetLucene-9) +:ancestors:/content/dam +jcr:content/metadata/dc:title:My Title ordering:[{ propertyName : jcr:created, propertyType : UNDEFINED, order : ASCENDING }] where ([a].[jcr:content/metadata/dc:title] = 'My Title') and (isdescendantnode([a], [/content/dam])) */
```

In diesem Plan lautet der Abschnitt, der die im zugrunde liegenden Index ausgeführte Abfrage beschreibt:

```
lucene:damAssetLucene-9(/oak:index/damAssetLucene-9) +:ancestors:/content/dam +jcr:content/metadata/dc:title:My Title ordering:[{ propertyName : jcr:created, propertyType : UNDEFINED, order : ASCENDING }]
```

In diesem Abschnitt des Plans heißt es:
* Ein Index wird verwendet, um diese Abfrage auszuführen -
   * In diesem Fall den Lucene-Index `/oak:index/damAssetLucene-9` verwendet werden, sodass die verbleibenden Informationen in der Lucene-Abfrage-Syntax enthalten sind.
* Alle 3 Einschränkungen werden vom Index verarbeitet -
   * Die Knotentyp-Einschränkung
      * implizit, weil `damAssetLucene-9` Indiziert nur Knoten des Typs dam:Asset.
   * Pfadbeschränkung
      * because `+:ancestors:/content/dam` in der Lucene-Abfrage angezeigt.
   * Die Eigenschaftsbeschränkung
      * because `+jcr:content/metadata/dc:title:My Title` in der Lucene-Abfrage angezeigt.
* Die Reihenfolge wird vom Index verarbeitet
   * because `ordering:[{ propertyName : jcr:created, propertyType : UNDEFINED, order : ASCENDING }]`  in der Lucene-Abfrage angezeigt.

Eine solche Abfrage ist wahrscheinlich gut, da die aus der Indexabfrage zurückgegebenen Ergebnisse in der Abfrage-Engine nicht weiter gefiltert werden (abgesehen von der Filterung der Zugriffskontrolle ). Es ist jedoch weiterhin möglich, dass eine solche Abfrage langsam ausgeführt wird, wenn die Best Practices nicht befolgt werden - siehe [Indexdurchlauf](#index-traversal) unten.

Eine andere Abfrage berücksichtigen -

```
/jcr:root/content/dam//element(*, dam:Asset) [jcr:content/metadata/myProperty = "My Property Value"] order by jcr:created
```

... enthält -
* 3 Beschränkungen
   * Knotentyp (`dam:Asset`)
   * Pfad (untergeordnete Elemente von `/content/dam`)
   * Eigenschaft (`jcr:content/metadata/myProperty = "My Property Value"`)
* Bestellung durch die `jcr:created` property*

Erläuterung der Abfrageergebnisse im folgenden Plan -

```
[dam:Asset] as [a] /* lucene:damAssetLucene-9-custom-1(/oak:index/damAssetLucene-9-custom-1) :ancestors:/content/dam ordering:[{ propertyName : jcr:created, propertyType : UNDEFINED, order : ASCENDING }] where ([a].[jcr:content/metadata/myProperty] = 'My Property Value') and (isdescendantnode([a], [/content/dam])) */
```

In diesem Plan lautet der Abschnitt, der die im zugrunde liegenden Index ausgeführte Abfrage beschreibt:

```
lucene:damAssetLucene-9(/oak:index/damAssetLucene-9) :ancestors:/content/dam ordering:[{ propertyName : jcr:created, propertyType : UNDEFINED, order : ASCENDING }]
```

In diesem Abschnitt des Plans heißt es:
* Nur 2 (der 3) Einschränkungen werden vom Index verarbeitet -
   * Die Knotentyp-Einschränkung
      * implizit, weil `damAssetLucene-9` Indiziert nur Knoten des Typs dam:Asset.
   * Pfadbeschränkung
      * because `+:ancestors:/content/dam` in der Lucene-Abfrage angezeigt.
* Die Eigenschaftsbeschränkung `jcr:content/metadata/myProperty = "My Property Value"` wird nicht am Index ausgeführt, sondern als Abfrage-Engine-Filterung auf die Ergebnisse der zugrunde liegenden Lucene-Abfrage angewendet.
   * Dies liegt daran, dass `+jcr:content/metadata/myProperty:My Property Value` wird nicht in der Lucene-Abfrage angezeigt, da diese Eigenschaft nicht im `damAssetLucene-9` für diese Abfrage verwendeter Index.

Dieser Abfrageausführungsplan führt zu jedem Asset unter `/content/dam` aus dem Index gelesen und dann weiter durch die Abfrage-Engine gefiltert werden (die nur diejenigen enthält, die mit der nicht indizierten Eigenschaftsbeschränkung im Ergebnissatz übereinstimmen).

Selbst wenn nur ein kleiner Prozentsatz der Assets mit der Einschränkung übereinstimmt `jcr:content/metadata/myProperty = "My Property Value"`, muss die Abfrage eine große Anzahl von Knoten lesen, um die angeforderte &#39;Seite&#39; der Ergebnisse zu füllen. Dies kann zu einer schlecht ausgeführten Abfrage führen, bei der eine niedrige `Read Optimization` -Wert im Tool &quot;Abfrageleistung&quot;) und kann zu WARN-Meldungen führen, die darauf hinweisen, dass eine große Anzahl von Knoten durchlaufen wird (siehe [Indexdurchlauf](#index-traversal)).

Um die Leistung dieser zweiten Abfrage zu optimieren, erstellen Sie eine benutzerdefinierte Version der `damAssetLucene-9` index (`damAssetLucene-9-custom-1`) und fügen Sie die folgende Eigenschaftsdefinition hinzu -

```
"myProperty": {
  "jcr:primaryType": "nt:unstructured",
  "propertyIndex": true,
  "name": "jcr:content/metadata/myProperty"
}
```

## JCR Query Cheat Sheet {#jcr-query-cheatsheet}

Um die Erstellung effizienter JCR-Abfragen und Indexdefinitionen zu unterstützen, kann die [JCR-Abfrage-Schnellübersicht](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/practices/best-practices-for-queries-and-indexing.html?lang=de#jcrquerycheatsheet) heruntergeladen und während der Entwicklung als Referenz verwendet werden.

Sie enthält Beispielabfragen für QueryBuilder, XPath und SQL-2, die mehrere Szenarien abdecken, welche sich hinsichtlich der Abfrageleistung unterschiedlich verhalten. Sie enthält auch Empfehlungen zum Erstellen oder Anpassen von Oak-Indizes. Der Inhalt dieses Spiegels gilt für AEM as a Cloud Service und AEM 6.5.

## Best Practices für die Indexdefinition {#index-definition-best-practices}

Im Folgenden finden Sie einige Best Practices, die Sie beim Definieren oder Erweitern von Indizes beachten sollten.

* Für Knotentypen mit vorhandenen Indizes (z. B. `dam:Asset` oder `cq:Page`) die Erweiterung von OOTB-Indizes auf das Hinzufügen neuer Indizes vorziehen.
   * Hinzufügen neuer Indizes - insbesondere Volltext-Indizes - im `dam:Asset` Knotentyp wird dringend empfohlen (siehe [diese Anmerkung](/help/operations/indexing.md##index-names-index-names)).
* Beim Hinzufügen neuer Indizes
   * Definieren Sie immer Indizes des Typs &quot;Lucene&quot;.
   * Verwenden Sie ein Index-Tag in der Indexdefinition (und der zugehörigen Abfrage) und `selectionPolicy = tag` , um sicherzustellen, dass der Index nur für die vorgesehenen Abfragen verwendet wird.
   * Sichern `queryPaths` und `includedPaths` beide bereitgestellt werden (normalerweise mit denselben Werten).
   * Verwendung `excludedPaths` , um Pfade auszuschließen, die keine nützlichen Ergebnisse enthalten.
   * Verwendung `analyzed` -Eigenschaften nur bei Bedarf, z. B. wenn Sie eine Volltext-Abfragebeschränkung nur für diese Eigenschaft verwenden müssen.
   * Immer angeben `async = [ async, nrt ] `, `compatVersion = 2` und `evaluatePathRestrictions = true`.
   * Nur angeben `nodeScopeIndex = true` , wenn Sie einen Volltext-Index für Knotenteile benötigen.

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Dokumentation zu Oak Lucene Index](https://jackrabbit.apache.org/oak/docs/query/lucene.html).

Durch die automatisierten Cloud Manager-Pipeline-Prüfungen werden einige der oben beschriebenen Best Practices erzwungen.

## Abfragen mit großen Ergebnismengen {#queries-with-large-result-sets}

Es wird empfohlen, Abfragen mit großen Ergebnismengen zu vermeiden. Es gibt jedoch Fälle, in denen große Ergebnismengen verarbeitet werden müssen. Oft ist die Menge der Ergebnisse nicht vorher bekannt, daher sollten einige Vorsichtsmaßnahmen getroffen werden, um die Verarbeitung zuverlässig durchführen zu können.

* Die Abfrage sollte nicht innerhalb einer Anfrage ausgeführt werden. Stattdessen sollte die Abfrage im Rahmen eines Sling-Vorgangs oder eines AEM-Workflows ausgeführt werden. Bei diesen Methoden bestehen keine Einschränkungen in Bezug auf ihre gesamte Laufzeit und werden neu gestartet, falls die Instanz während der Verarbeitung der Abfrage und ihrer Ergebnisse abstürzt.
* Um das Problem der Abfragegrenze von 100.000 Knoten zu vermeiden, sollten Sie eine [Keyset-Paginierung](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#Keyset_Pagination) in Betracht ziehen und die Abfrage in mehrere Unterabfragen aufteilen.

## Repository-Durchlauf {#repository-traversal}

Abfragen, die das Repository durchlaufen, verwenden keinen Index und werden mit einer Meldung ähnlich der folgenden protokolliert.

```text
28.06.2022 13:32:52.804 *WARN* [127.0.0.1 [1656415972414] POST /libs/settings/granite/operations/diagnosis/granite_queryperformance.explain.json HTTP/1.1] org.apache.jackrabbit.oak.plugins.index.Cursors$TraversingCursor Traversed 98000 nodes with filter Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a /* xpath: //* */, path=*) called by com.adobe.granite.queries.impl.explain.query.ExplainQueryServlet.getHeuristics; consider creating an index or changing the query
```

Mit diesem Protokollausschnitt können Sie Folgendes bestimmen:

* Die Abfrage selbst: `//*`
* Den Java-Code, der diese Abfrage ausgeführt hat (`com.adobe.granite.queries.impl.explain.query.ExplainQueryServlet::getHeuristics`), um zu ermitteln, wer die Abfrage erstellt hat.

Mit diesen Informationen sind Sie in der Lage, diese Abfrage mit den Methoden zu optimieren, die im Abschnitt [Optimieren von Abfragen](#optimizing-queries) in diesem Dokument beschrieben sind.

### Indexdurchlauf {#index-traversal}

Abfragen, die einen Index verwenden, aber dennoch eine große Anzahl von Knoten lesen, werden mit einer Meldung ähnlich der folgenden protokolliert (beachten Sie den Begriff `Index-Traversed` anstelle von `Traversed`).

```text
05.10.2023 10:56:10.498 *WARN* [127.0.0.1 [1696502982443] POST /libs/settings/granite/operations/diagnosis/granite_queryperformance.explain.json HTTP/1.1] org.apache.jackrabbit.oak.plugins.index.search.spi.query.FulltextIndex$FulltextPathCursor Index-Traversed 60000 nodes with filter Filter(query=select [jcr:path], [jcr:score], * from [dam:Asset] as a where isdescendantnode(a, '/content/dam') order by [jcr:content/metadata/unindexedProperty] /* xpath: /jcr:root/content/dam//element(*, dam:Asset) order by jcr:content/metadata/unindexedProperty */, path=/content/dam//*)
```

Dies kann aus verschiedenen Gründen auftreten -
1. Nicht alle Einschränkungen in der Abfrage können am Index verarbeitet werden.
   * In diesem Fall wird eine Obermenge der Ergebnismenge aus dem Index gelesen und anschließend in der Abfrage-Engine gefiltert.
   * Dies ist um ein Vielfaches langsamer als das Anwenden von Einschränkungen in der zugrunde liegenden Indexabfrage.
1. Die Abfrage wird nach einer Eigenschaft sortiert, die im Index nicht als &quot;geordnet&quot;markiert ist.
   * In diesem Fall müssen alle vom Index zurückgegebenen Ergebnisse von der Abfrage-Engine gelesen und im Arbeitsspeicher sortiert werden.
   * Dies ist um ein Vielfaches langsamer als die Anwendung der Sortierung in der zugrunde liegenden Indexabfrage.
1. Der Executor der Abfrage versucht, eine große Ergebnismenge zu iterieren.
   * Diese Situation kann aus verschiedenen Gründen auftreten, wie unten aufgeführt:

| Ursache | Abmilderung |
|----------|--------------|
| Die Kommission `p.guessTotal` (oder die Verwendung einer sehr großen guessTotal), die dazu führt, dass QueryBuilder eine große Anzahl von Ergebnissen zählt | Bereitstellung `p.guessTotal` mit einem geeigneten Wert |
| Die Verwendung einer großen oder unbegrenzten Beschränkung in Query Builder (d. h. `p.limit=-1`) | Verwenden Sie einen geeigneten Wert für `p.limit` (idealerweise 1000 oder weniger) |
| Die Verwendung eines Filterprädikats in Query Builder, das eine große Anzahl von Ergebnissen aus der zugrunde liegenden JCR-Abfrage filtert | Ersetzen von Filtereigenschaften durch Einschränkungen, die in der zugrunde liegenden JCR-Abfrage angewendet werden können |
| Die Verwendung einer vergleicherbasierten Sortierung in QueryBuilder | Ersetzen Sie durch eigenschaftsbasierte Reihenfolge in der zugrunde liegenden JCR-Abfrage (unter Verwendung der als geordnet indizierten Eigenschaften). |
| Filtern einer großen Anzahl von Ergebnissen aufgrund der Zugriffskontrolle | Wenden Sie zusätzliche indizierte Eigenschaft oder Pfadbeschränkung auf die Abfrage an, um die Zugriffskontrolle zu spiegeln. |
| Die Verwendung von &#39;Offset-Paginierung&#39; mit einem großen Offset | Verwenden Sie [Keyset-Paginierung](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#Keyset_Pagination) |
| Iteration einer großen oder unbegrenzten Anzahl von Ergebnissen | Verwenden Sie [Keyset-Paginierung](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#Keyset_Pagination) |
| Falsch ausgewählter Index | Verwenden Sie Tags in der Abfrage- und Indexdefinition, um sicherzustellen, dass der erwartete Index verwendet wird. |
