---
title: Best Practices für Abfragen und Indizierung
description: Erfahren Sie, wie Sie Ihre Indizes und Abfragen anhand der Best-Practice-Richtlinien von Adobe optimieren können.
topic-tags: best-practices
exl-id: 37eae99d-542d-4580-b93f-f454008880b1
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '1556'
ht-degree: 79%

---

# Best Practices für Abfragen und Indizierung {#query-and-indexing-best-practices}

In AEM as a Cloud Service sind alle operativen Aspekte der Indizierung automatisiert. Dadurch können sich Personen, die mit der Entwicklung befasst sind, auf das Erstellen effizienter Abfragen und der entsprechenden Indexdefinitionen konzentrieren.

## Verwenden von Abfragen {#when-to-use-queries}

Abfragen sind eine Möglichkeit, auf Inhalte zuzugreifen, aber nicht die einzige. In vielen Fällen ist der Zugriff auf Inhalte im Repository auf eine andere Weise effektiver. Sie sollten überlegen, ob Abfragen der beste und effizienteste Weg sind, für Ihren Anwendungsfall auf Inhalte zuzugreifen.

### Repository- und Taxonomiedesign {#repository-and-taxonomy-design}

Bei der Erstellung der Taxonomie eines Repositorys müssen mehrere Faktoren berücksichtigt werden. Hierzu gehören die Zugriffssteuerung, Lokalisierung, Vererbung von Komponenten- und Seiteneigenschaften und vieles mehr.

In einem Taxonomie-Design, in dem diese Punkte berücksichtigt werden, muss zudem auch die „Durchlauffähigkeit“ des Index-Designs beachtet werden. In diesem Zusammenhang ist die Durchlauffähigkeit die Fähigkeit einer Taxonomie, einen vorhersehbaren Zugriff auf Inhalte auf der Grundlage ihres Pfads zu ermöglichen. Dies ermöglicht ein effizienteres System, das einfacher zu verwalten ist als ein System, für das mehrere Abfragen ausgeführt werden müssen.

Darüber hinaus muss beim Entwerfen einer Taxonomie bedacht werden, ob eine Sortierung wichtig ist. Wenn auf eine explizite Sortierung verzichtet werden kann und eine große Anzahl gleichgeordneter Knoten erwartet wird, sind unsortierte Knotentypen wie `sling:Folder` oder `oak:Unstructured` vorzuziehen. Ist eine Sortierung erforderlich, wären `nt:unstructured` und `sling:OrderedFolder` besser geeignet.

### Abfragen in Komponenten {#queries-in-components}

Da Abfragen eine der steuerbareren Vorgänge in einem AEM sein können, ist es empfehlenswert, sie in Ihren Komponenten zu vermeiden. Die Ausführung mehrerer Abfragen bei jedem Rendern einer Seite kann häufig die Leistung des Systems beeinträchtigen. Es gibt zwei Strategien, mit denen sich beim Rendering von Komponenten die Ausführung von Abfragen vermeiden lässt: **[Durchlaufen von Knoten](#traversing-nodes)** und **[Vorabrufen von Ergebnissen](#prefetching-results)**.

### Durchlaufen von Knoten {#traversing-nodes}

Wenn das Repository so konzipiert ist, dass eine vorherige Kenntnis des Speicherorts der erforderlichen Daten möglich ist, kann Code, der diese Daten aus den erforderlichen Pfaden abruft, bereitgestellt werden, ohne Abfragen ausführen zu müssen, um sie zu finden.

Ein Beispiel hierfür wäre das Rendern von Inhalten, die zu einer bestimmten Kategorie passen. Ein Ansatz wäre, den Inhalt mit einer Kategorieeigenschaft zu organisieren, die abgefragt werden kann, um eine Komponente zu füllen, die Elemente in einer Kategorie anzeigt.

Ein besserer Ansatz wäre, diesen Inhalt in einer Taxonomie nach Kategorie zu strukturieren, damit er manuell abgerufen werden kann.

Wenn der Inhalt beispielsweise in einer Taxonomie gespeichert ist, die Folgendem ähnelt:

```xml
/content/myUnstructuredContent/parentCategory/childCategory/contentPiece
```

In diesem Fall lässt sich der Knoten `/content/myUnstructuredContent/parentCategory/childCategory` einfach abrufen und seine untergeordneten Elemente können analysiert und zum Rendern der Komponente verwendet werden.

Wenn Sie es mit einem kleinen oder homogenen Ergebnissatz zu tun haben, kann es außerdem schneller sein, das Repository zu durchlaufen und die erforderlichen Knoten zu sammeln, anstatt eine Abfrage zu erstellen, um denselben Ergebnissatz zurückzugeben. Generell sollten Abfragen vermieden werden, soweit dies möglich ist.

### Vorabruf der Ergebnisse {#prefetching-results}

Mitunter lassen die Inhalte oder Anforderungen im Zusammenhang mit der Komponente nicht zu, dass Knoten zum Abrufen der erforderlichen Daten durchlaufen werden. In solchen Fällen müssen die erforderlichen Abfragen vor dem Rendern der Komponente ausgeführt werden, damit eine optimale Leistung sichergestellt werden kann.

Sofern die für die Komponente erforderlichen Ergebnisse zum Zeitpunkt der Erstellung ermittelt werden können und nicht zu erwarten ist, dass sich der Inhalt ändert, kann die Abfrage nach einer Änderung ausgeführt werden.

Wenn sich die Daten oder Inhalte regelmäßig ändern, kann die Abfrage planmäßig oder über einen Listener für Aktualisierungen der zugrunde liegenden Daten ausgeführt werden. Anschließend können die Ergebnisse an einen freigegebenen Speicherort im Repository geschrieben werden. Alle Komponenten, die diese Daten benötigen, können dann die Werte aus diesem einzelnen Knoten beziehen, ohne eine Abfrage zur Laufzeit auszuführen.

Eine ähnliche Strategie kann verwendet werden, um das Ergebnis in einem Arbeitsspeicher-Cache zu speichern, der beim Start gefüllt und bei jeder Änderung aktualisiert wird (mithilfe eines JCR-Elements `ObservationListener` oder eines Sling-Elements `ResourceChangeListener`).

## Optimieren von Abfragen {#optimizing-queries}

Die Oak-Dokumentation bietet eine [allgemeine Übersicht über die Ausführung von Abfragen.](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#query-processing) Dies bildet die Grundlage für alle in diesem Dokument beschriebenen Optimierungsaktivitäten.

AEM as a Cloud Service verfügt über das Abfrageleistungs-Tool, das die Implementierung effizienter Abfragen unterstützt.

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

Wenn eine potenziell große Ergebnismenge vollständig verarbeitet werden muss, lesen Sie den Abschnitt [Abfragen mit großen Ergebnismengen](#queries-with-large-result-sets) in diesem Dokument.

## JCR-Abfrage-Schnellübersicht {#jcr-query-cheatsheet}

Um die Erstellung effizienter JCR-Abfragen und Indexdefinitionen zu unterstützen, kann die [JCR-Abfrage-Schnellübersicht](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/practices/best-practices-for-queries-and-indexing.html?lang=de#jcrquerycheatsheet) heruntergeladen und während der Entwicklung als Referenz verwendet werden.

Sie enthält Beispielabfragen für QueryBuilder, XPath und SQL-2, die mehrere Szenarien abdecken, welche sich hinsichtlich der Abfrageleistung unterschiedlich verhalten. Sie enthält auch Empfehlungen zum Erstellen oder Anpassen von Oak-Indizes. Der Inhalt dieses Spiegels gilt für AEM as a Cloud Service und AEM 6.5.

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
