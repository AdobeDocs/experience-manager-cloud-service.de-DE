---
title: Best Practices für Abfragen und Indizierung
seo-title: Best Practices for Queries and Indexing
description: Dieser Artikel liefert Richtlinien zum Optimieren Ihrer Indizes und Abfragen.
seo-description: This article provides guidelines on how to optimize your indexes and queries.
topic-tags: best-practices
source-git-commit: 85cbdaa6e6d01856005cb47f289d391fb44bd65e
workflow-type: tm+mt
source-wordcount: '1573'
ht-degree: 31%

---


# Best Practices für Abfragen und Indizierung{#best-practices-for-queries-and-indexing}

Im Gegensatz zu früheren Versionen in AEM sind alle betrieblichen Aspekte der Indizierung automatisiert. Dadurch können sich Entwickler auf die Erstellung effizienter Abfragen und der entsprechenden Indexdefinitionen konzentrieren.

## Verwendung von Abfragen {#when-to-use-queries}

Abfragen sind eine Möglichkeit, auf Inhalte zuzugreifen, aber nicht die einzige. Aus diesem Grund muss geprüft werden, ob Abfragen die beste und leistungsfähigste Methode für den Zugriff auf Inhalte sind. In vielen Fällen kann auf Inhalte im Repository mit anderen Mitteln zugegriffen werden, um die Leistung zu steigern.

### Repository- und Taxonomiedesign {#repository-and-taxonomy-design}

Beim Entwerfen der Taxonomie für ein Repository müssen verschiedene Faktoren berücksichtigt werden. Hierzu gehören u. a. die Zugriffssteuerung, Lokalisierung, Vererbung von Komponenten- und Seiteneigenschaften.

In ein Taxonomiedesign, das auf diese Punkte eingeht, muss zudem auch die „Durchlauffähigkeit“ des Indexdesigns einfließen. In diesem Kontext bezeichnet dieser Begriff die Fähigkeit einer Taxonomie zuzulassen, dass auf Inhalt, basierend auf seinem Pfad, planbar zugegriffen werden kann. Dies ermöglicht ein leistungsfähigeres System, das einfacher unterhalten werden kann als ein System, für das eine Vielzahl von Abfragen ausgeführt werden muss.

Darüber hinaus muss beim Entwerfen einer Taxonomie bedacht werden, ob sortiert werden muss. Wenn auf eine explizite Sortierung verzichtet werden kann und eine große Anzahl gleichgeordneter Knoten erwartet wird, sind unsortierte Knotentypen wie `sling:Folder` oder `oak:Unstructured` vorzuziehen. In den Fällen, in denen eine Bestellung erforderlich ist, `nt:unstructured` und `sling:OrderedFolder` wäre angemessener.

### Abfragen in Komponenten {#queries-in-components}

Da Abfragen zu den schwierigeren Vorgängen in einem AEM-System gehören können, empfiehlt es sich, diese in Komponenten zu vermeiden. Wenn beim Rendering einer Seite mehrere Abfragen gleichzeitig ausgeführt werden, kann dies die Leistung des Systems beeinträchtigen. Es gibt zwei Strategien, mit denen sich beim Rendering von Komponenten die Ausführung von Abfragen vermeiden lässt: **Durchlaufen von Knoten** und **Vorabrufen von Ergebnissen**.

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

Mitunter lassen die Inhalte oder Anforderungen im Zusammenhang mit der Komponente nicht zu, dass Knoten zum Abrufen der erforderlichen Daten durchlaufen werden. In diesen Fällen müssen die erforderlichen Abfragen vor dem Rendern der Komponente ausgeführt werden, damit eine optimale Leistung gewährleistet ist.

Wenn die für die Komponente erforderlichen Ergebnisse zum Zeitpunkt der Erstellung berechnet werden können und es nicht zu erwarten ist, dass sich der Inhalt ändert, kann die Abfrage ausgeführt werden, nachdem eine Änderung vorgenommen wurde.

Wenn sich Daten oder Inhalte regelmäßig ändern, kann die Abfrage nach einem Plan oder über einen Listener für Updates der zugrundeliegenden Daten ausgeführt werden. Anschließend können die Ergebnisse in einen freigegebenen Speicherort im Repository geschrieben werden. Alle Komponenten, die diese Daten benötigen, können dann die Werte aus diesem einzelnen Knoten beziehen, ohne eine Abfrage zur Laufzeit auszuführen.
Eine ähnliche Strategie kann verwendet werden, um das Ergebnis in einem Arbeitsspeichercache zu speichern, der beim Start gefüllt und aktualisiert wird, sobald Änderungen vorgenommen werden (mithilfe eines JCR ObservationListener oder eines Sling ResourceChangeListener).

## Abfragen optimieren {#optimizing-queries}

Die Oak-Dokumentation bietet eine [Überblick über die Ausführung von Abfragen](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#query-processing). Dies bildet die Grundlage für alle in diesem Dokument beschriebenen Optimierungsaktivitäten.

AEM as a Cloud Service bietet das Tool zur Abfrageleistung, das die Implementierung effizienter Abfragen unterstützt.
* Er zeigt bereits ausgeführte Abfragen mit ihren jeweiligen Leistungsmerkmalen und dem Abfrageplan an.
* Sie ermöglicht die Durchführung von Ad-hoc-Abfragen auf verschiedenen Ebenen, von der bloßen Anzeige des Abfrageplans bis zur Ausführung der vollständigen Abfrage.

Das Tool für die Abfrageleistung ist über die [Entwicklerkonsole in Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html?lang=de#queries). Im Gegensatz zum Query Performance Tool früherer Versionen von AEM 6.x liefert das für AEM as a Cloud Service bereitgestellte Performance-Abfragetool weitere Informationen über die Details der Abfrageausführung, die zur Verbesserung einer Abfrage nützlich sind.


Der allgemeine Ansatz zur Verwendung des Tools für die Abfrageleistung zur Optimierung von Abfragen wird in diesem Diagramm beschrieben.
![Query Optimization-Fluss](assets/query-optimization-flow.png)



### Verwenden eines Index {#use-an-index}

Jede Abfrage sollte einen Index verwenden, um eine optimale Leistung zu erzielen. In den meisten Fällen sollten bereits vorhandene native Indizes für die Verarbeitung von Abfragen ausreichen.
Manchmal müssen benutzerdefinierte Eigenschaften zu einem vorhandenen Index hinzugefügt werden, damit zusätzliche Einschränkungen mithilfe dieses Index abgefragt werden können. Siehe [Inhaltssuche und -indizierung](/help/operations/indexing.md#changing-an-index) für weitere Details. Die [JCR-Abfrage-Schnellübersicht](#jcr-query-cheatsheet) beschreibt, wie eine Eigenschaftsdefinition für einen Index aussehen muss, um einen bestimmten Abfragetyp zu unterstützen.



### Verwenden der richtigen Kriterien

Die primäre Beschränkung für jede Abfrage sollte eine Eigenschaftsübereinstimmung sein, da dies der effizienteste Typ ist. Durch das Hinzufügen von mehr Eigenschaftsbeschränkungen wird das Ergebnis weiter eingeschränkt.
Die Abfrage-Engine berücksichtigt nur einen einzigen Index; Dies bedeutet, dass ein vorhandener Index angepasst werden kann und sollte, indem weitere benutzerdefinierte Indexeigenschaften hinzugefügt werden.

Die [JCR-Abfrage-Cheatsheet](#jcr-query-cheatsheet) listet die verfügbaren Einschränkungen auf und beschreibt außerdem, wie eine Indexdefinition so aussehen muss, dass sie aufgenommen wurde. Verwenden Sie die [Abfrageleistungswerkzeug](#query-performance-tool) , um die Abfrage zu testen und sicherzustellen, dass der richtige Index verwendet wird und dass die Abfrage-Engine keine Begrenzungen außerhalb des Index auswerten muss.


### Bestellung

Wenn eine bestimmte Reihenfolge des Ergebnisses angefordert wird, gibt es 2 Möglichkeiten, dies durch die Abfrage-Engine zu erreichen:

1. Der Index kann das Ergebnis vollständig und in der richtigen Reihenfolge liefern. Dies funktioniert, wenn die Eigenschaften, die für die Sortierung verwendet werden, mit kommentiert sind. ```ordered=true``` in der Indexdefinition.
2. Wenn die Abfrage-Engine außerhalb des Index filtern muss oder wenn die Sortiereigenschaft nicht mit der ```ordered=true``` -Eigenschaft, führt die Abfrage-Engine auch den Bestellvorgang durch. In diesem Fall muss der vollständige Ergebnissatz zum Sortieren in den Speicher gelesen werden, was viel langsamer ist als die erste Option.





### Ergebnisgröße begrenzen

Die abgerufene Größe des Abfrageergebnisses ist ein wichtiger Faktor für die Abfrageleistung. Da das Ergebnis auf faule Weise abgerufen wird, gibt es einen Unterschied beim Abrufen der ersten 20 Ergebnisse im Vergleich zum Abrufen von 10&#39;000 Ergebnissen, sowohl in der Laufzeit als auch im Speicher.

Dies bedeutet auch, dass die Größe der Ergebnismenge nur korrekt bestimmt werden kann, wenn alle Ergebnisse abgerufen werden. Aus diesem Grund sollte die abgerufene Ergebnismenge immer begrenzt sein, indem entweder die Abfrage erweitert wird (siehe [JCR-Abfrage-Cheatsheet](#jcr-query-cheatsheet) für Details) oder durch Begrenzung der Ergebnisse.
Eine solche Beschränkung verhindert auch, dass die Abfrage-Engine die **Traversalgrenze** von 100.000 Knoten, was zu einem erzwungenen Stopp der Abfrage führt.

Siehe Abschnitt . [Abfragen mit großen Ergebnissen](#queries-with-large-result-sets) unten, wenn eine potenziell große Ergebnismenge vollständig verarbeitet werden muss.


## JCR-Abfrage-Schnellübersicht

Um die Erstellung effizienter JCR-Abfragen und Indexdefinitionen zu unterstützen, muss die [JCR Query Cheat Sheet](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/practices/best-practices-for-queries-and-indexing.html#jcrquerycheatsheet) ist für den Download und die Verwendung als Referenz während der Entwicklung verfügbar. Es enthält Beispielabfragen für QueryBuilder, XPath und SQL-2, die mehrere Szenarien abdecken, die sich hinsichtlich der Abfrageleistung unterschiedlich verhalten. Es enthält auch Empfehlungen zum Erstellen oder Anpassen von Oak-Indizes. Der Inhalt dieses Spiegels gilt für AEM 6.5 und AEM as a Cloud Service.


## Abfragen mit großen Ergebnismengen

Es wird empfohlen, Abfragen mit einer großen Ergebnismenge zu vermeiden. Es gibt jedoch Fälle, in denen große Ergebnisse verarbeitet werden müssen. Oft ist die Größe des Ergebnisses nicht im Voraus bekannt, daher sollten einige Vorsichtsmaßnahmen getroffen werden, um die Verarbeitung zuverlässig zu machen.

* die Abfrage sollte nicht innerhalb einer Anfrage ausgeführt werden; Stattdessen sollte die Abfrage im Rahmen eines Sling-Auftrags oder eines AEM-Workflows ausgeführt werden. Diese haben keine Einschränkungen in Bezug auf ihre gesamte Laufzeit und werden neu gestartet, falls die Instanz während der Verarbeitung der Abfrage und ihrer Ergebnisse heruntergefahren wird.
* Um die Abfragegrenze von 100.000 Knoten zu überwinden, sollten Sie [Keyset-Paginierung](https://jackrabbit.apache.org/oak/docs/query/query-engine.html#Keyset_Pagination) und teilen Sie die Abfrage in mehrere Unterabfragen auf.



## Abfrage im Repository

Abfragen, die das Repository durchlaufen, verwenden keinen Index und protokollieren eine Meldung wie die folgende:

```text
28.06.2022 13:32:52.804 *WARN* [127.0.0.1 [1656415972414] POST /libs/settings/granite/operations/diagnosis/granite_queryperformance.explain.json HTTP/1.1] org.apache.jackrabbit.oak.plugins.index.Cursors$TraversingCursor Traversed 98000 nodes with filter Filter(query=select [jcr:path], [jcr:score], * from [nt:base] as a /* xpath: //* */, path=*) called by com.adobe.granite.queries.impl.explain.query.ExplainQueryServlet.getHeuristics; consider creating an index or changing the query
```

Dieses Protokollfragment enthält relevante Informationen:

* die Abfrage selbst: ```//* ```
* den Java-Code, der diese Abfrage ausgeführt hat: ```com.adobe.granite.queries.impl.explain.query.ExplainQueryServlet::getHeuristics```; Dies hilft, den Ersteller dieser Abfrage zu identifizieren.

Mit diesen Informationen ist es möglich, diese Abfrage mit den in [Optimierung von Abfragen](#optimizing-queries).