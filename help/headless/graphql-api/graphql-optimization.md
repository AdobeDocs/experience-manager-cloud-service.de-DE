---
title: GraphQL-Abfragen optimieren
description: Erfahren Sie, wie Sie Ihre GraphQL-Abfragen beim Filtern, Paging und Sortieren Ihrer Inhaltsfragmente in Adobe Experience Manager as a Cloud Service für die Headless-Content-Bereitstellung optimieren können.
source-git-commit: 0fe0bd301fb09cdc631878926f2e40df51a2cc23
workflow-type: tm+mt
source-wordcount: '1192'
ht-degree: 0%

---


# Optimieren von GraphQL-Abfragen {#optimizing-graphql-queries}

>[!NOTE]
>
>Bevor Sie diese Optimierungsempfehlungen anwenden, sollten Sie [Aktualisieren Ihrer Inhaltsfragmente für Paging und Sortierung in GraphQL-Filterung](/help/headless/graphql-api/graphql-optimized-filtering-content-update.md) für beste Leistung.

Auf einer AEM Instanz mit einer großen Anzahl von Inhaltsfragmenten, die dasselbe Modell verwenden, können GraphQL-Listenabfragen zu hohen Kosten führen (im Hinblick auf Ressourcen).

Dies liegt daran, dass *all* Fragmente, die ein in der GraphQL-Abfrage verwendetes Modell gemeinsam verwenden, müssen in den Speicher geladen werden. Dies verbraucht sowohl Zeit als auch Speicher. Filterung, die die Anzahl der Elemente in der (endgültigen) Ergebnismenge verringern kann, kann nur angewendet werden **after** Laden des gesamten Ergebnissatzes in den Speicher.

Dies kann den Eindruck erwecken, dass auch kleine Ergebnismengen (kann) zu schlechter Leistung führen. In Wirklichkeit wird die Langsamkeit jedoch durch die Größe des ursprünglichen Ergebnissatzes verursacht, da diese intern verarbeitet werden muss, bevor die Filterung angewendet werden kann.

Um Leistungs- und Speicherprobleme zu reduzieren, muss diese anfängliche Ergebnismenge so klein wie möglich gehalten werden.

AEM bietet zwei Ansätze zur Optimierung von GraphQL-Abfragen:

* [Hybride Filterung](#hybrid-filtering)
* [Paging](#paging) (oder Paginierung)

   * [Sortierung](#sorting) ist nicht direkt mit der Optimierung verbunden, sondern mit dem Paging

Jeder Ansatz hat seine eigenen Anwendungsfälle und Einschränkungen. In diesem Dokument finden Sie Informationen zum Hybrid-Filter und zum Paging sowie einige [Best Practices](#best-practices) , um GraphQL-Abfragen zu optimieren.

## Hybride Filterung {#hybrid-filtering}

Hybride Filter kombinieren JCR-Filterung mit AEM Filterung.

Es wendet einen JCR-Filter (in Form einer Abfragebegrenzung) an, bevor der Ergebnissatz zur AEM Filterung in den Speicher geladen wird. Dadurch soll der in den Speicher geladene Ergebnissatz reduziert werden, da der JCR-Filter überflüssige Ergebnisse vor diesem entfernt.

>[!NOTE]
>
>Aus technischen Gründen (z. B. Flexibilität, Verschachtelung von Fragmenten) kann AEM die gesamte Filterung nicht an JCR delegieren.

Diese Technik behält die Flexibilität bei, die GraphQL-Filter bieten, und delegiert gleichzeitig einen möglichst großen Teil der Filterung an JCR.

## Paging {#paging}

GraphQL in AEM unterstützt zwei Arten der Paginierung:

* [begrenzungs-/offset-basierte Paginierung](/help/headless/graphql-api/content-fragments.md#list-offset-limit)
Dies wird für Listenabfragen verwendet. diese enden mit 
`List`; Beispiel, `articleList`.
Um sie zu verwenden, müssen Sie die Position des ersten Elements angeben, das zurückgegeben werden soll (die `offset`) und die Anzahl der zurückzugebenden Elemente (die `limit`oder Seitengröße).

* [Cursorbasierte Paginierung](/help/headless/graphql-api/content-fragments.md#paginated-first-after) (vertreten durch `first`und `after`) Dies stellt eine eindeutige ID für jedes Element bereit. auch als Cursor bezeichnet.
In der Abfrage geben Sie den Cursor des letzten Elements der vorherigen Seite sowie die Seitengröße (die maximale Anzahl an zurückzugebenden Elementen) an.

   Da die Cursor-basierte Paginierung nicht in die Datenstrukturen von listenbasierten Abfragen passt, hat AEM `Paginated` Abfrageart; Beispiel: `articlePaginated`. Die verwendeten Datenstrukturen und Parameter folgen dem [GraphQL Cursor ConnectionSpecification](https://relay.dev/graphql/connections.htm).

   >[!NOTE]
   >
   >AEM unterstützt derzeit das Weiterleiten (mithilfe von `after`/`first` Parameter).
   >
   >Abwärtspaging (mithilfe von `before`/`last` Parameter) nicht unterstützt.

## Sortieren {#sorting}

Die Sortierung kann nur dann effizient sein, wenn alle Sortierungskriterien mit Fragmenten der obersten Ebene verbunden sind.

Wenn die Sortierreihenfolge ein oder mehrere Felder enthält, die sich auf einem verschachtelten Fragment befinden, müssen alle Fragmente, die das Modell der obersten Ebene gemeinsam verwenden, in den Speicher geladen werden. Dies führt zu negativen Leistungseinbußen.

>[!NOTE]
>
>Die Sortierung nach Feldern der obersten Ebene wirkt sich ebenfalls (wenn auch klein) auf die Leistung aus.

## Best Practices {#best-practices}

Das Hauptziel aller Optimierungen besteht darin, die anfängliche Ergebnismenge zu reduzieren. Die hier aufgeführten Best Practices bieten Möglichkeiten dazu. Sie können (und sollten) kombiniert werden.

### Nur nach Eigenschaften der obersten Ebene filtern {#filter-top-level-properties-only}

Derzeit funktioniert das Filtern auf JCR-Ebene nur für Fragmente der obersten Ebene.

Wenn ein Filter die Felder eines verschachtelten Fragments adressiert, muss AEM alle Fragmente, die das zugrunde liegende Modell gemeinsam nutzen, wieder in den Speicher laden.

Sie können diese GraphQL-Abfragen weiterhin optimieren, indem Sie Filterausdrücke für Felder von Fragmenten der obersten Ebene und für Felder verschachtelter Fragmente mit der [AND-Operator](#logical-operations-in-filter-expressions).

### Inhaltsstruktur verwenden {#use-content-structure}

In AEM wird es allgemein als Best Practice erachtet, die Repository-Struktur zu verwenden, um den Umfang der zu verarbeitenden Inhalte einzugrenzen.

Dieser Ansatz sollte auch auf GraphQL-Abfragen angewendet werden.

Dies kann durch Anwenden eines Filters auf die Variable `_path` -Feld des Fragments der obersten Ebene:

```graphql
{
  someList(filter: {
    _path: {
      _expressions: [ 
        {
          value: "/content/dam/some/sub/path/",
          _operator: STARTS_WITH
        }
      ]
    }
  }) {
    items {
      # ...
    }
  }
}
```

>[!NOTE]
>
>Die `/` on `value` ist erforderlich, um die beste Leistung zu erzielen.

### Paging verwenden {#use-paging}

Sie können auch Paging verwenden, um die anfängliche Ergebnismenge zu reduzieren. insbesondere dann, wenn Ihre Anforderungen keine Filterung und Sortierung verwenden.

Wenn Sie verschachtelte Fragmente filtern oder sortieren, können die Seitenabfragen immer noch langsam sein, da AEM möglicherweise noch größere Mengen von Fragmenten in den Speicher laden müssen. Wenn Sie also Filtern und Paging kombinieren, sollten Sie die Filterregeln beachten (wie oben beschrieben).

Für das Paging ist die Sortierung gleichermaßen wichtig, da paginierte Ergebnisse immer sortiert werden - entweder explizit oder implizit.

Wenn Sie in erster Linie daran interessiert sind, nur die ersten Seiten abzurufen, gibt es keinen signifikanten Unterschied zwischen der Verwendung der `...List` oder `...Paginated` Abfragen. Wenn Ihre Anwendung jedoch daran interessiert ist, mehr als ein oder zwei Seiten zu lesen, sollten Sie die `...Paginated` -Abfrage, da sie bei den späteren Seiten deutlich besser funktioniert.

### Logische Vorgänge in Filterausdrücken {#logical-operations-in-filter-expressions}

Wenn Sie nach verschachtelten Fragmenten filtern, können Sie weiterhin die JCR-Filterung nutzen, indem Sie einen begleitenden Filter für ein Feld der obersten Ebene bereitstellen, das mithilfe der `AND` Operator.

Ein typischer Anwendungsfall bestünde darin, den Umfang der Abfrage mithilfe eines Filters auf die `_path` -Feld des Fragments der obersten Ebene ein und filtern Sie dann nach zusätzlichen Feldern, die sich möglicherweise auf der obersten Ebene oder in einem verschachtelten Fragment befinden.

In diesem Fall würden die verschiedenen Filterausdrücke mit `AND`. Daher wird der Filter nach `_path` kann die anfängliche Ergebnismenge effektiv einschränken. Alle anderen Filter auf Feldern der obersten Ebene können ebenfalls dazu beitragen, den anfänglichen Ergebnissatz zu reduzieren, sofern sie mit `AND`.

Filterausdrücke in Kombination mit `OR` kann nicht optimiert werden, wenn verschachtelte Fragmente beteiligt sind. `OR` -Ausdrücke können nur optimiert werden, wenn *no* verschachtelte Fragmente sind beteiligt.

### Vermeiden von Filtern nach mehrzeiligen Textfeldern {#avoid-filtering-multiline-textfields}

Die Felder eines mehrzeiligen Textfelds (HTML, Markdown, Klartext, JSON) können nicht über eine JCR-Abfrage gefiltert werden, da der Inhalt dieser Felder dynamisch berechnet werden muss.

Wenn Sie weiterhin nach einem mehrzeiligen Textfeld filtern müssen, sollten Sie die Größe des ursprünglichen Ergebnissatzes einschränken, indem Sie zusätzliche Filterausdrücke hinzufügen und sie mit `AND`. Begrenzung des Umfangs durch Filterung der `_path` -Feld ist auch ein guter Ansatz.

### Vermeiden von Filtern nach virtuellen Feldern {#avoid-filtering-virtual-fields}

Virtuelle Felder (die meisten Felder beginnen mit `_`) während der Ausführung einer GraphQL-Abfrage berechnet werden und sich daher außerhalb des Bereichs der JCR-basierten Filterung befinden.

Eine wichtige Ausnahme bildet die `_path` -Feld, das effektiv verwendet werden kann, um die Größe der ursprünglichen Ergebnismenge zu reduzieren - wenn der Inhalt entsprechend strukturiert ist (siehe [Inhaltsstruktur verwenden](#use-content-structure)).

### Filter: Ausnahmen {#filtering-exclusions}

Es gibt mehrere andere Situationen, in denen ein Filterausdruck nicht auf der JCR-Ebene bewertet werden kann (und daher vermieden werden sollte, die beste Leistung zu erzielen):

* Ausdrücke in einer `Float` -Wert, der `_sensitiveness` Filteroption und wo `_sensitiveness` auf alles andere als `0.0` .

* Ausdrücke in einer `String` -Wert mithilfe des `_ignoreCase` Filteroption.

* Filtern nach `null` -Werte.

* Filter für Arrays mit `_apply: ALL_OR_EMPTY`.

* Filter für Arrays mit `_apply: INSTANCES`, `_instances: 0`.

* Filtern von Ausdrücken mithilfe der `CONTAINS_NOT` Operator.

* Ausdrücke in einer `Calendar`, `Date` oder `Time` -Wert, der `NOT_AT` Operator.
