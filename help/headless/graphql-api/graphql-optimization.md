---
title: Optimieren von GraphQL-Abfragen
description: Erfahren Sie, wie Sie Ihre GraphQL-Abfragen beim Filtern, Paging und Sortieren Ihrer Inhaltsfragmente in Adobe Experience Manager as a Cloud Service optimieren können, um Headless-Inhalte bereitzustellen.
source-git-commit: 0fe0bd301fb09cdc631878926f2e40df51a2cc23
workflow-type: ht
source-wordcount: '1192'
ht-degree: 100%

---


# Optimieren von GraphQL-Abfragen {#optimizing-graphql-queries}

>[!NOTE]
>
>Bevor Sie diese Optimierungsempfehlungen anwenden, empfehlen wir Ihnen, [Ihre Inhaltsfragmente für Paging und Sortierung in der GraphQL-Filterung zu aktualisieren](/help/headless/graphql-api/graphql-optimized-filtering-content-update.md), um eine optimale Leistung zu erzielen.

Auf einer AEM-Instanz mit einer großen Anzahl von Inhaltsfragmenten, die dasselbe Modell verwenden, können GraphQL-Listenabfragen kostenintensiv sein (im Hinblick auf Ressourcen).

Das liegt daran, dass *alle* Fragmente, die dasselbe in der GraphQL-Abfrage verwendete Modell nutzen, in den Speicher geladen werden müssen. Dies erfordert Zeit und Speicherplatz. Eine Filterung, die die Anzahl der Elemente in der (endgültigen) Ergebnismenge verringern kann, kann nur **nach** dem Laden des gesamten Ergebnissatzes in den Speicher angewendet werden.

Dies kann den Eindruck erwecken, dass die Leistung auch bei kleinen Ergebnismengen schlecht ist. In Wirklichkeit wird das langsame Tempo jedoch durch die Größe des ursprünglichen Ergebnissatzes verursacht, da dieser intern verarbeitet werden muss, bevor die Filterung angewendet werden kann.

Um Leistungs- und Speicherprobleme zu vermeiden, muss diese anfängliche Ergebnismenge so klein wie möglich gehalten werden.

AEM bietet zwei Methoden zur Optimierung von GraphQL-Abfragen:

* [Hybride Filterung](#hybrid-filtering)
* [Paging](#paging) (oder Paginierung)

   * [Sortierung](#sorting) ist nicht direkt mit der Optimierung verbunden, sondern mit dem Paging

Jede Methode beinhaltet eigene Anwendungsfälle und Einschränkungen. In diesem Dokument finden Sie Informationen zur hybriden Filterung und zum Paging sowie einige [Best Practices](#best-practices), um GraphQL-Abfragen zu optimieren.

## Hybride Filterung {#hybrid-filtering}

Hybride Filterung kombiniert JCR-Filterung mit AEM-Filterung.

Dabei wird ein JCR-Filter (in Form einer Abfragebegrenzung) angewendet, bevor der Ergebnissatz zur AEM-Filterung in den Speicher geladen wird. Dadurch soll der in den Speicher geladene Ergebnissatz verringert werden, da der JCR-Filter überflüssige Ergebnisse davor entfernt.

>[!NOTE]
>
>Aus technischen Gründen (z. B. Flexibilität, Verschachtelung von Fragmenten) kann AEM nicht die gesamte Filterung an JCR delegieren.

Bei dieser Methode wird die Flexibilität bewahrt, die GraphQL-Filter bieten, während gleichzeitig ein möglichst großer Teil der Filterung an JCR delegiert wird.

## Paging {#paging}

GraphQL in AEM unterstützt zwei Arten der Paginierung:

* [Limit-/Offset-basierte Paginierung](/help/headless/graphql-api/content-fragments.md#list-offset-limit)
Diese Methode wird für Listenabfragen verwendet; diese enden mit 
`List`; Beispiel: `articleList`.
Um sie zu verwenden, müssen Sie die Position des ersten Elements angeben, das zurückgegeben werden soll (`offset`) und die Anzahl der zurückzugebenden Elemente (`limit` oder Seitengröße).

* [Cursor-basierte Paginierung](/help/headless/graphql-api/content-fragments.md#paginated-first-after) (dargestellt durch `first` und `after`) 
Bei dieser Methode wird für jedes Element eine eindeutige ID bereitgestellt; auch als Cursor bezeichnet.
In der Abfrage geben Sie den Cursor des letzten Elements der vorherigen Seite sowie die Seitengröße (die maximale Anzahl der zurückzugebenden Elemente) an.

   Da die Cursor-basierte Paginierung nicht zu den Datenstrukturen von listenbasierten Abfragen passt, hat AEM den Abfragetyp `Paginated` eingeführt, zum Beispiel `articlePaginated`. Die verwendeten Datenstrukturen und Parameter entsprechen der [GraphQL Cursor ConnectionSpecification](https://relay.dev/graphql/connections.htm).

   >[!NOTE]
   >
   >AEM unterstützt derzeit Forward Paging (unter Verwendung der Parameter `after`/`first`).
   >
   >Backward Paging (mithilfe der Parameter `before`/`last`) wird nicht unterstützt.

## Sortierung {#sorting}

Die Sortierung ist nur dann effizient, wenn sich alle Sortierungskriterien auf Fragmente der obersten Ebene beziehen.

Wenn die Sortierreihenfolge ein oder mehrere Felder enthält, die sich auf einem verschachtelten Fragment befinden, müssen alle Fragmente, die das Modell der obersten Ebene gemeinsam verwenden, in den Speicher geladen werden. Dies führt zu Leistungseinbußen.

>[!NOTE]
>
>Die Sortierung der Felder der obersten Ebene wirkt sich ebenfalls (wenn auch geringfügig) auf die Leistung aus.

## Best Practices {#best-practices}

Das Hauptziel aller Optimierungsmaßnahmen besteht darin, die anfängliche Ergebnismenge zu reduzieren. Die hier aufgeführten Best Practices bieten Möglichkeiten dazu. Sie können (und sollten) kombiniert werden.

### Nur nach Eigenschaften der obersten Ebene filtern {#filter-top-level-properties-only}

Derzeit funktioniert das Filtern auf JCR-Ebene nur für Fragmente der obersten Ebene.

Wenn sich ein Filter auf die Felder eines verschachtelten Fragments bezieht, muss AEM alle Fragmente, die das zugrunde liegende Modell gemeinsam nutzen, wieder in den Speicher laden.

Sie können diese GraphQL-Abfragen dennoch optimieren, indem Sie Filterausdrücke für Felder von Fragmenten der obersten Ebene und für Felder verschachtelter Fragmente mit dem [AND-Operator](#logical-operations-in-filter-expressions) kombinieren.

### Inhaltsstruktur verwenden {#use-content-structure}

In AEM wird generell empfohlen, die Repository-Struktur zu verwenden, um den Umfang der zu verarbeitenden Inhalte einzugrenzen.

Diese Methode sollte auch auf GraphQL-Abfragen angewendet werden.

Dies kann durch Anwendung eines Filters auf das Feld `_path` des Fragments der obersten Ebene geschehen:

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
>Die Endung `/` auf `value` ist erforderlich, um die beste Leistung zu erzielen.

### Verwenden Sie Paging {#use-paging}

Sie können auch Paging verwenden, um die anfängliche Ergebnismenge zu reduzieren; insbesondere dann, wenn Ihre Anforderungen keine Filterung und Sortierung verwenden.

Wenn Sie verschachtelte Fragmente filtern oder sortieren, können die paginierten Abfragen immer noch langsam sein, da AEM möglicherweise weiterhin größere Mengen von Fragmenten in den Speicher laden muss. Wenn Sie also Filtern und Paging kombinieren, sollten Sie die Filterregeln beachten (wie oben erwähnt).

Für das Paging ist die Sortierung gleichermaßen wichtig, da paginierte Ergebnisse immer sortiert werden, entweder explizit oder implizit.

Wenn Sie in erster Linie daran interessiert sind, nur die ersten Seiten abzurufen, gibt es keinen signifikanten Unterschied zwischen der Verwendung der `...List`- oder `...Paginated`-Abfragen. Wenn Ihre Anwendung jedoch daran interessiert ist, mehr als ein oder zwei Seiten zu lesen, sollten Sie die `...Paginated`-Abfrage in Erwägung ziehen, da sie bei den späteren Seiten deutlich besser funktioniert.

### Logische Vorgänge in Filterausdrücken {#logical-operations-in-filter-expressions}

Wenn Sie verschachtelte Fragmente filtern, können Sie weiterhin die JCR-Filterung nutzen, indem Sie einen begleitenden Filter für ein Feld der obersten Ebene bereitstellen, der mithilfe des `AND`-Operators kombiniert wird.

Ein typischer Anwendungsfall bestünde darin, den Umfang der Abfrage mithilfe eines Filters auf das Feld `_path` des Fragments der obersten Ebene einzugrenzen und dann zusätzliche Felder zu filtern, die sich möglicherweise auf der obersten Ebene oder in einem verschachtelten Fragment befinden.

In diesem Fall würden die verschiedenen Filterausdrücke mit `AND` kombiniert. Daher kann der Filter auf `_path` die anfängliche Ergebnismenge effektiv einschränken. Alle anderen Filter auf Feldern der obersten Ebene können ebenfalls dazu beitragen, den anfänglichen Ergebnissatz zu reduzieren, sofern sie mit `AND` kombiniert werden.

Filterausdrücke, die mit `OR` kombiniert sind, können nicht optimiert werden, wenn verschachtelte Fragmente vorliegen. `OR`-Ausdrücke können nur optimiert werden, wenn *keine* verschachtelten Fragmente vorliegen.

### Vermeidung von Filtern bei mehrzeiliger Textfelder {#avoid-filtering-multiline-textfields}

Die Felder eines mehrzeiligen Textfelds (HTML, Markdown, Plain text, JSON) können nicht über eine JCR-Abfrage gefiltert werden, da der Inhalt dieser Felder dynamisch berechnet werden muss.

Wenn Sie weiterhin ein mehrzeiliges Textfeld filtern müssen, sollten Sie die Größe des ursprünglichen Ergebnissatzes einschränken, indem Sie zusätzliche Filterausdrücke hinzufügen und sie mit `AND` kombinieren. Die Begrenzung des Umfangs durch Filterung des Felds `_path` ist auch ein guter Ansatz.

### Vermeidung von Filtern bei virtueller Felder {#avoid-filtering-virtual-fields}

Virtuelle Felder (die meisten Felder, die mit `_` beginnen) werden während der Ausführung einer GraphQL-Abfrage berechnet und befinden sich daher außerhalb des Bereichs der JCR-basierten Filterung.

Eine wichtige Ausnahme bildet das Feld `_path`, das effektiv verwendet werden kann, um die Größe des ursprünglichen Ergebnissatzes zu reduzieren – falls der Inhalt entsprechend strukturiert ist (siehe [Verwenden der Inhaltsstruktur](#use-content-structure)).

### Filter: Ausnahmen {#filtering-exclusions}

Es gibt mehrere andere Situationen, in denen ein Filterausdruck nicht auf der JCR-Ebene bewertet werden kann (und daher vermieden werden sollte, um die beste Leistung zu erzielen):

* Filterausdrücke in einem `Float`-Wert, der die Filteroption `_sensitiveness` verwendet, wobei `_sensitiveness` auf alles andere als `0.0` festgelegt ist.

* Filterausdrücke in einem `String`-Wert, die die Filteroption `_ignoreCase` nutzen.

* Filtern von `null`-Werten.

* Filtern von Arrays mit `_apply: ALL_OR_EMPTY`.

* Filtern von Arrays mit `_apply: INSTANCES`, `_instances: 0`.

* Filterausdrücke mit dem `CONTAINS_NOT`-Operator.

* Filterausdrücke in einem `Calendar`-, `Date`- oder `Time`-Wert, die den `NOT_AT`-Operator nutzen.
