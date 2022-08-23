---
title: Best Practices für Abfragen und Indizierung
description: Erfahren Sie, wie Sie Ihre Indizes und Abfragen anhand der Best Practice-Richtlinien von Adobe optimieren können.
topic-tags: best-practices
exl-id: 37eae99d-542d-4580-b93f-f454008880b1
source-git-commit: afeff7cfb8606eb58126a4ca62ce9e6e58c44215
workflow-type: tm+mt
source-wordcount: '1563'
ht-degree: 25%

---

# Best Practices für Abfragen und Indizierung {#query-and-indexing-best-practices}

In AEM as a Cloud Service werden alle betrieblichen Aspekte der Indizierung automatisiert. Dadurch können sich Entwickler auf die Erstellung effizienter Abfragen und der entsprechenden Indexdefinitionen konzentrieren.

## Verwenden von Abfragen {#when-to-use-queries}

Abfragen sind eine Möglichkeit, auf Inhalte zuzugreifen, aber nicht die einzige Möglichkeit. In vielen Fällen ist der Zugriff auf Inhalte im Repository auf andere Weise effektiver. Sie sollten überlegen, ob Abfragen der beste und effizienteste Weg sind, auf Inhalte für Ihren Anwendungsfall zuzugreifen.

### Repository- und Taxonomiedesign {#repository-and-taxonomy-design}

Beim Entwerfen der Taxonomie für ein Repository müssen verschiedene Faktoren berücksichtigt werden. Dazu gehören Zugriffssteuerungen, Lokalisierung, Vererbung von Komponenten- und Seiteneigenschaften und mehr.

In ein Taxonomiedesign, das auf diese Punkte eingeht, muss zudem auch die „Durchlauffähigkeit“ des Indexdesigns einfließen. In diesem Zusammenhang ist die Durchlaufbarkeit die Fähigkeit einer Taxonomie, den Zugriff auf Inhalte auf Grundlage ihres Pfads vorhersehbar zu machen. Dies ermöglicht ein effizienteres System, das einfacher zu verwalten ist als ein System, für das mehrere Abfragen ausgeführt werden müssen.

Darüber hinaus muss beim Entwerfen einer Taxonomie bedacht werden, ob sortiert werden muss. Wenn auf eine explizite Sortierung verzichtet werden kann und eine große Anzahl gleichgeordneter Knoten erwartet wird, sind unsortierte Knotentypen wie `sling:Folder` oder `oak:Unstructured` vorzuziehen. In den Fällen, in denen eine Bestellung erforderlich ist, `nt:unstructured` und `sling:OrderedFolder` wäre angemessener.

### Abfragen in Komponenten {#queries-in-components}

Da Abfragen zu den schwierigeren Vorgängen in einem AEM-System gehören können, empfiehlt es sich, diese in Komponenten zu vermeiden. Wenn beim Rendering einer Seite mehrere Abfragen gleichzeitig ausgeführt werden, kann dies die Leistung des Systems beeinträchtigen. Es gibt zwei Strategien, mit denen sich beim Rendering von Komponenten die Ausführung von Abfragen vermeiden lässt: **[Durchlaufen von Knoten](#traversing-nodes)** und **[Vorabrufen von Ergebnissen.](#prefetching-results)**

### Durchlaufen von Knoten {#traversing-nodes}

Wenn das Repository so aufgebaut ist, dass eine Vorabkenntnis des Speicherorts der erforderlichen Daten zulässig ist, kann der Code, der diese Daten von den notwendigen Pfaden abruft, ohne Abfragen gefunden und bereitgestellt werden.

Ein Beispiel hierfür wäre etwa das Rendering von Inhalt, der zu einer bestimmten Kategorie passt. Ein möglicher Ansatz: den Inhalt mit einer Kategorieeigenschaft zu organisieren, die abgefragt werden kann, um eine Komponente mit Elementen einer Kategorie aufzufüllen.

Besser wäre es allerdings, diesen Inhalt in einer Taxonomie nach Kategorie zu strukturieren, damit er manuell abgerufen werden kann.

Angenommen, der Inhalt wird in einer Taxonomie wie der folgenden gespeichert:

```xml
/content/myUnstructuredContent/parentCategory/childCategory/contentPiece
```

die `/content/myUnstructuredContent/parentCategory/childCategory` -Knoten können einfach abgerufen werden, seine untergeordneten Elemente können analysiert und zum Rendern der Komponente verwendet werden.

Bei einem kleinen oder homogenen Ergebnissatz kann es außerdem schneller sein, das Repository zu durchlaufen und die erforderlichen Knoten zu erfassen, statt eine Abfrage zu erstellen, die denselben Ergebnissatz zurückgibt. Generell gilt, dass Abfragen nach Möglichkeit vermieden werden sollten.

### Vorabruf von Ergebnissen {#prefetching-results}

Manchmal ist die Verwendung von Knotendurchlauf zum Abrufen der erforderlichen Daten durch den Inhalt oder die Anforderungen an die Komponente nicht zulässig. In solchen Fällen müssen die erforderlichen Abfragen vor dem Rendern der Komponente ausgeführt werden, damit eine optimale Leistung gewährleistet ist.

Wenn die für die Komponente erforderlichen Ergebnisse zum Zeitpunkt der Erstellung berechnet werden können und es nicht zu erwarten ist, dass sich der Inhalt ändert, kann die Abfrage ausgeführt werden, nachdem eine Änderung vorgenommen wurde.

Wenn sich Daten oder Inhalte regelmäßig ändern, kann die Abfrage nach einem Plan oder über einen Listener für Updates der zugrundeliegenden Daten ausgeführt werden. Anschließend können die Ergebnisse in einen freigegebenen Speicherort im Repository geschrieben werden. Alle Komponenten, die diese Daten benötigen, können dann die Werte aus diesem einzelnen Knoten beziehen, ohne eine Abfrage zur Laufzeit auszuführen.

Eine ähnliche Strategie kann verwendet werden, um das Ergebnis in einem Arbeitsspeichercache zu speichern, der beim Start gefüllt und bei jeder Änderung aktualisiert wird (mithilfe eines JCR-Elements) `ObservationListener` oder Sling `ResourceChangeListener`).

## Optimierung von Abfragen {#optimizing-queries}

Die Oak-Dokumentation bietet eine [allgemeine Übersicht über die Ausführung von Abfragen.](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#query-processing) Dies bildet die Grundlage für alle in diesem Dokument beschriebenen Optimierungsaktivitäten.

AEM as a Cloud Service bietet das Tool für die Abfrageleistung, das die Implementierung effizienter Abfragen unterstützt.

* Er zeigt bereits ausgeführte Abfragen mit ihren jeweiligen Leistungsmerkmalen und dem Abfrageplan an.
* Sie ermöglicht die Durchführung von Ad-hoc-Abfragen auf verschiedenen Ebenen, von der bloßen Anzeige des Abfrageplans bis zur Ausführung der vollständigen Abfrage.

Das Tool für die Abfrageleistung ist über die [Entwicklerkonsole in Cloud Manager.](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html?lang=de#queries) AEM Tool für die Abfrageleistung von as a Cloud Service liefert weitere Informationen über die Details der Abfrageausführung im Vergleich zur AEM 6.x-Version.

Dieses Diagramm zeigt den allgemeinen Ablauf zur Verwendung des Tools für die Abfrageleistung zur Optimierung von Abfragen.

![Query Optimization-Fluss](assets/query-optimization-flow.png)

### Verwenden eines Index {#use-an-index}

Jede Abfrage sollte einen Index verwenden, um eine optimale Leistung zu erzielen. In den meisten Fällen sollten vorhandene vordefinierte Indizes für die Verarbeitung von Abfragen ausreichen.

Manchmal müssen benutzerdefinierte Eigenschaften zu einem vorhandenen Index hinzugefügt werden, damit zusätzliche Einschränkungen mithilfe des Index abgefragt werden können. Siehe Dokument . [Inhaltssuche und -indizierung](/help/operations/indexing.md#changing-an-index) für weitere Details. Die [JCR-Abfrage-Schnellübersicht](#jcr-query-cheatsheet) -Abschnitt dieses Dokuments beschreibt, wie eine Eigenschaftsdefinition in einem Index aussehen muss, um einen bestimmten Abfragetyp zu unterstützen.

### Verwenden der richtigen Kriterien {#use-the-right-criteria}

Die primäre Beschränkung für jede Abfrage sollte eine Eigenschaftsübereinstimmung sein, da dies der effizienteste Typ ist. Durch das Hinzufügen von mehr Eigenschaftsbeschränkungen wird das Ergebnis weiter eingeschränkt.

Die Abfrage-Engine berücksichtigt nur einen einzigen Index. Das bedeutet, dass ein vorhandener Index angepasst werden kann und sollte, indem weitere benutzerdefinierte Indexeigenschaften hinzugefügt werden.

Die [JCR-Abfrage-Cheatsheet](#jcr-query-cheatsheet) in diesem Dokument werden die verfügbaren Einschränkungen aufgelistet und außerdem erläutert, wie eine Indexdefinition aussehen muss, damit sie aufgenommen wird. Verwenden Sie die [Abfrageleistungswerkzeug](#query-performance-tool) , um die Abfrage zu testen und sicherzustellen, dass der richtige Index verwendet wird und dass die Abfrage-Engine keine Begrenzungen außerhalb des Index auswerten muss.

### Bestellung {#ordering}

Wenn eine bestimmte Reihenfolge des Ergebnisses angefordert wird, gibt es zwei Möglichkeiten, dies durch die Abfrage-Engine zu erreichen:

1. Der Index kann das Ergebnis vollständig und in der richtigen Reihenfolge liefern.
   * Dies funktioniert, wenn die Eigenschaften, die für die Sortierung verwendet werden, mit kommentiert sind. `ordered=true` in der Indexdefinition.
1. Die Abfrage-Engine führt den Bestellvorgang durch.
   * Dies kann vorkommen, wenn die Abfrage-Engine die Filterung außerhalb des Index durchführt oder die Sortiereigenschaft nicht mit der `ordered=true` -Eigenschaft.
   * Dies erfordert, dass der vollständige Ergebnissatz zum Sortieren in den Speicher gelesen wird, was viel langsamer ist als die erste Option.

### Ergebnisgröße beschränken {#restrict-result-size}

Die abgerufene Größe des Abfrageergebnisses ist ein wichtiger Faktor für die Abfrageleistung. Da das Ergebnis auf faule Weise abgerufen wird, gibt es einen Unterschied beim Abrufen der ersten 20 Ergebnisse im Vergleich zum Abrufen von 10.000 Ergebnissen, sowohl in der Laufzeit als auch im Speicher.

Dies bedeutet auch, dass die Größe der Ergebnismenge nur korrekt bestimmt werden kann, wenn alle Ergebnisse abgerufen werden. Aus diesem Grund sollte die abgerufene Ergebnismenge immer begrenzt sein, indem entweder die Abfrage erweitert wird (siehe [JCR-Abfrage-Cheatsheet](#jcr-query-cheatsheet) detailliert beschrieben) oder durch Eingrenzung der Ergebnisse.

Eine solche Beschränkung verhindert auch, dass die Abfrage-Engine die **Traversalgrenze** von 100.000 Knoten, was zu einem erzwungenen Stopp der Abfrage führt.

Siehe Abschnitt . [Abfragen mit großen Ergebnissen](#queries-with-large-result-sets) dieses Dokuments, wenn eine potenziell große Ergebnismenge vollständig verarbeitet werden muss.

## JCR-Abfrage-Schnellübersicht {#jcr-query-cheatsheet}

Um die Erstellung effizienter JCR-Abfragen und Indexdefinitionen zu unterstützen, muss die [JCR Query Cheat Sheet](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/practices/best-practices-for-queries-and-indexing.html#jcrquerycheatsheet) ist für den Download und die Verwendung als Referenz während der Entwicklung verfügbar.

Sie enthält Beispielabfragen für QueryBuilder, XPath und SQL-2, die mehrere Szenarien abdecken, die sich hinsichtlich der Abfrageleistung unterschiedlich verhalten. Es enthält auch Empfehlungen zum Erstellen oder Anpassen von Oak-Indizes. Der Inhalt dieses Spiegels gilt für AEM as a Cloud Service sowie für AEM 6.5.

## Abfragen mit großen Ergebnismengen {#queries-with-large-result-sets}

Es wird empfohlen, Abfragen mit großen Ergebnismengen zu vermeiden. Es gibt jedoch Fälle, in denen große Ergebnismengen verarbeitet werden müssen. Oft ist die Größe des Ergebnisses nicht vorher bekannt, daher sollten einige Vorsichtsmaßnahmen getroffen werden, um die Verarbeitung zuverlässig zu machen.

* Die Abfrage sollte nicht innerhalb einer Anfrage ausgeführt werden. Stattdessen sollte die Abfrage im Rahmen eines Sling-Auftrags oder eines AEM-Workflows ausgeführt werden. Diese haben keine Einschränkungen in Bezug auf ihre gesamte Laufzeit und werden neu gestartet, falls die Instanz während der Verarbeitung der Abfrage und ihrer Ergebnisse heruntergefahren wird.
* Um die Abfragegrenze von 100.000 Knoten zu überwinden, sollten Sie erwägen, [Keyset-Paginierung](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#Keyset_Pagination) und teilen Sie die Abfrage in mehrere Teilabfragen auf.

## Repository-Durchlauf {#repository-traversal}

Abfragen, die das Repository durchlaufen, verwenden keinen Index und protokollieren mit einer Meldung, die der folgenden ähnelt.

```text
28.06.2022 13:32:52.804 *WARN* [127.0.0.1 [1656415972414] POST /libs/settings/granite/operations/diagnosis/granite_queryperformance.explain.json HTTP/1.1] org.apache.jackrabbit.oak.plugins.index.Cursors$TraversingCursor Traversed 98000 nodes with filter Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a /* xpath: //* */, path=*) called by com.adobe.granite.queries.impl.explain.query.ExplainQueryServlet.getHeuristics; consider creating an index or changing the query
```

Mit diesem Protokollausschnitt können Sie Folgendes bestimmen:

* Die Abfrage selbst: `//*`
* Der Java-Code, der diese Abfrage ausgeführt hat: `com.adobe.granite.queries.impl.explain.query.ExplainQueryServlet::getHeuristics` um den Ersteller der Abfrage zu identifizieren.

Mit diesen Informationen ist es möglich, diese Abfrage mit den im Abschnitt [Optimierung von Abfragen](#optimizing-queries) Abschnitt dieses Dokuments.
