---
title: Query-Builder-API
description: Die Funktionalität der Query-Builder-Komponente für die Asset-Freigabe wird über eine Java-API und eine REST-API verfügbar gemacht.
translation-type: tm+mt
source-git-commit: cfd54f0cd84cef72b6f2fad1a85132c312a19348
workflow-type: tm+mt
source-wordcount: '2069'
ht-degree: 44%

---


# Query-Builder-API {#query-builder-api}

Die Abfrage Builder-Angebote bieten eine einfache Möglichkeit, das Inhalts-Repository der AEM abzurufen. Die Funktionalität wird über eine Java-API und eine REST-API bereitgestellt. In diesem Dokument werden diese APIs beschrieben.

Der serverseitige Query Builder ([`QueryBuilder`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/QueryBuilder.html)) akzeptiert eine Abfragebeschreibung, erstellt eine XPath-Abfrage und führt sie aus, filtert das Resultset und extrahiert bei Bedarf auch Facetten.

Die Abfragebeschreibung ist einfach eine Gruppe mit Eigenschaften ([`Predicate`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/Predicate.html)). Beispiele sind Volltextprädikate, die der Funktion `jcr:contains()` in XPath entsprechen.

Für jeden Eigenschaftentyp ist eine Auswertungskomponente ([`PredicateEvaluator`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/eval/PredicateEvaluator.html)) vorhanden, die weiß, wie die jeweilige Eigenschaft für XPath, die Filterung und die Facettenextrahierung verarbeitet werden muss. Es ist sehr einfach, benutzerdefinierte Auswertungskomponenten zu erstellen, die über die OSGi-Komponentenlaufzeit verknüpft werden.

Die REST-API ermöglicht den Zugriff auf genau die gleichen Funktionen per HTTP, wobei die Antworten per JSON gesendet werden.

>[!NOTE]
>
>Die QueryBuilder-API wird mit der JCR-API erstellt. Sie können die AEM JCR auch über die JCR-API in einem OSGi-Bundle Abfrage haben. Weitere Informationen erhalten Sie unter [Abfragen von Adobe Experience Manager-Daten mit der JCR-API](https://helpx.adobe.com/experience-manager/using/querying-experience-manager-data-using1.html).

## Gem-Sitzung  {#gem-session}

[AEM Gems](https://helpx.adobe.com/de/experience-manager/kt/eseminars/gems/aem-index.html) ist eine Serie mit ausführlichen technischen Erläuterungen zu Adobe Experience Manager von Adobe-Experten.

Sie können [die dem Abfrage Builder gewidmete Sitzung für eine Übersicht und Verwendung des Tools überprüfen.](https://helpx.adobe.com/experience-manager/kt/eseminars/gems/aem-search-forms-using-querybuilder.html)

## Beispielabfragen {#sample-queries}

Diese Beispiele sind in der Notation des Java-Eigenschaftenstils angegeben. Für die Nutzung mit der Java-API können Sie ein Java-`HashMap`-Element im folgenden API-Beispiel verwenden.

Für das JSON-Servlet `QueryBuilder` enthält jedes Beispiel einen Beispiellink zu einer AEM Installation (am Standardspeicherort `http://<host>:<port>`). Beachten Sie, dass Sie sich bei Ihrer AEM-Instanz anmelden müssen, bevor Sie diese Links verwenden.

>[!CAUTION]
>
>Standardmäßig zeigt das JSON-Servlet von Abfrage Builder maximal 10 Treffer an.
>
>Wenn der folgende Parameter hinzugefügt wird, kann das Servlet alle Abfrageergebnisse anzeigen:
>
>`p.limit=-1`

>[!NOTE]
>
>Zum Anzeigen der zurückgegebenen JSON-Daten in Ihrem Browser kann die Verwendung eines Plug-ins nützlich sein, z. B. JSONView für Firefox.

### Alle Ergebnisse zurückgeben {#returning-all-results}

Mit der folgenden Abfrage werden **zehn Ergebnisse zurückgegeben** (bzw. genauer gesagt maximal zehn), aber es wird die **Anzahl von Treffern** angegeben, die tatsächlich verfügbar sind:

`http://<host>:<port>/bin/querybuilder.json?path=/content&1_property=sling:resourceType&1_property.value=wknd/components/structure/page&1_property.operation=like&orderby=path`

```xml
path=/content
1_property=sling:resourceType
1_property.value=wknd/components/structure/page
1_property.operation=like
orderby=path
```

Mit derselben Abfrage (mit dem Parameter `p.limit=-1`) werden **alle Ergebnisse zurückgegeben** (dies kann je nach Instanz eine relativ große Zahl sein):

`http://<host>:<port>/bin/querybuilder.json?path=/content&1_property=sling:resourceType&1_property.value=wknd/components/structure/page&1_property.operation=like&orderby=path&p.limit=-1`

```xml
path=/content
1_property=sling:resourceType
1_property.value=wknd/components/structure/page
1_property.operation=like
p.limit=-1
orderby=path
```

### Verwenden von p.measureTotal zum Zurückgeben der Ergebnisse {#using-p-guesstotal-to-return-the-results}

Der Zweck des Parameters `p.guessTotal` besteht darin, die entsprechende Anzahl von Ergebnissen zurückzugeben, die angezeigt werden können, indem die minimalen Werte `p.offset` und `p.limit` kombiniert werden. Der Vorteil der Nutzung dieses Parameters ist eine verbesserte Leistung bei großen Resultsets. Dadurch wird vermieden, dass der gesamte Gesamtwert berechnet (z.B. `result.getSize()`) und der gesamte Ergebnissatz gelesen wird, der bis zur OAK-Engine und -Indexposition optimiert wurde. Dies kann ein bedeutender Unterschied sein, wenn Hunderttausende Ergebnisse vorliegen, sowohl bei der Ausführungszeit als auch bei der Speicherbelegung.

Der Nachteil besteht bei diesem Parameter darin, dass Benutzern die genaue Gesamtsumme nicht angezeigt wird. Sie können jedoch eine Mindestzahl wie `p.guessTotal=1000` festlegen, sodass immer bis zu 1000 gelesen wird, sodass Sie exakte Summen für kleinere Ergebnismengen erhalten, aber wenn es mehr ist, können Sie nur &quot;und mehr&quot;anzeigen.

Fügen Sie der Abfrage unten `p.guessTotal=true` hinzu, um die Funktionsweise zu testen:

`http://<host>:<port>/bin/querybuilder.json?path=/content&1_property=sling:resourceType&1_property.value=wknd/components/structure/page&1_property.operation=like&p.guessTotal=true&orderby=path`

```xml
path=/content
1_property=sling:resourceType
1_property.value=wknd/components/structure/page
1_property.operation=like
p.guessTotal=true
orderby=path
```

Die Abfrage gibt gemäß dem Standardwert `p.limit` `10` Ergebnisse mit einem Offset von `0` zurück:

```xml
"success": true,
"results": 10,
"total": 10,
"more": true,
"offset": 0,
```

Sie können auch einen numerischen Wert verwenden, um bis zu einer benutzerdefinierten Anzahl von maximalen Ergebnissen zu zählen. Verwenden Sie die gleiche Abfrage wie oben, aber ändern Sie den Wert von `p.guessTotal` in `50`:

`http://<host>:<port>/bin/querybuilder.json?path=/content&1_property=sling:resourceType&1_property.value=wknd/components/structure/page&1_property.operation=like&p.guessTotal=50&orderby=path`

Es wird eine Zahl mit der gleichen Standardgrenze von 10 Ergebnissen mit einem 0-Offset zurückgegeben, es werden jedoch nur maximal 50 Ergebnisse angezeigt:

```xml
"success": true,
"results": 10,
"total": 50,
"more": true,
"offset": 0,
```

### Implementierung der Paginierung {#implementing-pagination}

Standardmäßig würde der Query Builder auch die Anzahl von Treffern angeben. Je nach Ergebnisgröße kann dies lange dauern, da das Ermitteln der genauen Anzahl auch das Prüfen jedes Ergebnisses in Bezug auf die Zugriffssteuerung umfasst. Meist wird die Gesamtsumme verwendet, um Seitenumbrüche für die Benutzeroberfläche für Endbenutzer zu implementieren. Da die Ermittlung der genauen Anzahl lange dauern kann, wird empfohlen, die Funktion „guessTotal“ zum Implementieren von Seitenumbrüchen zu verwenden.

Beispielsweise kann für die Benutzeroberfläche der folgende Ansatz genutzt werden:

* die genaue Anzahl der Treffer abrufen und anzeigen ([SearchResult.getTotalMatches()](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/result/SearchResult.html#gettotalmatches) oder die Gesamtzahl in der `querybuilder.json`-Antwort) kleiner als oder gleich 100 sind;
* Legen Sie `guessTotal` auf 100 fest, während Sie den Query-Builder-Aufruf durchführen.

* Die Antwort kann das folgende Ergebnis enthalten:

   * `total=43`,  `more=false` - Zeigt an, dass die Gesamtzahl der Treffer 43 beträgt. Auf der Benutzeroberfläche können auf der ersten Seite bis zu zehn Ergebnisse angezeigt werden und für die nächsten drei Seiten können Seitenumbrüche genutzt werden. Sie können diese Implementierung auch verwenden, um einen beschreibenden Text wie **„43 Ergebnisse gefunden“** anzuzeigen.
   * `total=100`,  `more=true` - Gibt an, dass die Gesamtzahl der Treffer größer als 100 ist und die genaue Anzahl nicht bekannt ist. Auf der Benutzeroberfläche können auf der ersten Seite bis zu zehn Ergebnisse angezeigt werden und für die nächsten zehn Seiten können Seitenumbrüche genutzt werden. Sie können diese Option auch verwenden, um einen Text wie **„Mehr als 100 Ergebnisse gefunden“** anzuzeigen. Wenn der Benutzer auf die nächsten Seiten zugreift, würden Query-Builder-Aufrufe dazu führen, dass sich die Beschränkung von `guessTotal` und auch die Parameter `offset` und `limit` erhöhen.

`guessTotal` sollte auch in Fällen verwendet werden, in denen die Benutzeroberfläche das unendliche Scrollen nutzen muss, um zu vermeiden, dass der Query Builder die genaue Trefferanzahl ermittelt.

### Suchen Sie die JAR-Dateien und ordnen Sie sie an, die neuesten {#find-jar-files-and-order-them-newest-first}

`http://<host>:<port>/bin/querybuilder.json?type=nt:file&nodename=*.jar&orderby=@jcr:content/jcr:lastModified&orderby.sort=desc`

```xml
type=nt:file
nodename=*.jar
orderby=@jcr:content/jcr:lastModified
orderby.sort=desc
```

### Alle Seiten suchen und nach zuletzt geänderten {#find-all-pages-and-order-them-by-last-modified} sortieren

`http://<host>:<port>/bin/querybuilder.json?type=cq:Page&orderby=@jcr:content/cq:lastModified`

```xml
type=cq:Page
orderby=@jcr:content/cq:lastModified
```

### Alle Seiten suchen und nach zuletzt bearbeiteten Seiten ordnen, Absteigend {#find-all-pages-and-order-them-by-last-modified-but-descending}

`http://<host>:<port>/bin/querybuilder.json?type=cq:Page&orderby=@jcr:content/cq:lastModified&orderby.sort=desc`

```xml
type=cq:Page
orderby=@jcr:content/cq:lastModified
orderby.sort=desc
```

### Volltextsuche, sortiert nach Ergebnis {#fulltext-search-ordered-by-score}

`http://<host>:<port>/bin/querybuilder.json?fulltext=Management&orderby=@jcr:score&orderby.sort=desc`

```xml
fulltext=Management
orderby=@jcr:score
orderby.sort=desc
```

### Suchen nach Seiten mit einem bestimmten Tag {#search-for-pages-tagged-with-a-certain-tag}

`http://<host>:<port>/bin/querybuilder.json?type=cq:Page&tagid=wknd:activity/cycling&tagid.property=jcr:content/cq:tags`

```xml
type=cq:Page
tagid=wknd:activity/cycling
tagid.property=jcr:content/cq:tags
```

Verwenden Sie die Prädikate `tagid` wie im Beispiel, wenn Sie die explizite Tag-ID kennen.

Verwenden Sie die Eigenschaft `tag` für den Tag-Titelpfad (ohne Leerstellen).

Da Sie im vorherigen Beispiel nach Seiten (`cq:Page`-Knoten) suchen, müssen Sie den relativen Pfad von diesem Knoten für die `tagid.property`-Vorhersage verwenden, die `jcr:content/cq:tags` lautet. Standardmäßig ist `tagid.property` einfach `cq:tags`.

### Mehrere Pfade suchen (mit Gruppen) {#search-under-multiple-paths-using-groups}

`http://<host>:<port>/bin/querybuilder.json?fulltext=Experience&group.1_path=/content/wknd/us/en/magazine&group.2_path=/content/wknd/us/en/adventures&group.p.or=true`

```xml
fulltext=Experience
group.p.or=true
group.1_path=/content/wknd/us/en/magazine
group.2_path=/content/wknd/us/en/adventures
```

Diese Abfrage verwendet eine *group* (mit dem Namen `group`), mit der Subausdrücke innerhalb einer Abfrage abgegrenzt werden, ähnlich wie Klammern in mehr Standardnotationen. Beispielweise kann die vorherige Abfrage wie folgt auf vertrautere Weise ausgedrückt werden:

`"Experience" and ("/content/wknd/us/en/magazine" or "/content/wknd/us/en/adventures")`

Im Beispiel wird in der Gruppe die Eigenschaft `path` mehrere Male genutzt. Um die beiden Instanzen des Prädikats zu unterscheiden und anzuordnen (für einige Prädikate ist eine Reihenfolge erforderlich), müssen Sie den Präfix für die Prädikate `N_` voranstellen, wobei `N` der Sortierindex ist. Im vorherigen Beispiel sind die resultierenden Vorhersagen `1_path` und `2_path`.

Das `p` in `p.or` ist ein spezielles Trennzeichen, das angibt, dass Folgendes (in diesem Fall ein `or`) ein *Parameter* der Gruppe ist, im Gegensatz zu einer Untervorhersage der Gruppe, z. B. `1_path`.

Wenn kein `p.or` angegeben wird, werden alle Vorhersagen UNDed zusammen, d. h., jedes Ergebnis muss alle Vorhersagen erfüllen.

>[!NOTE]
>
>Sie können dasselbe numerische Präfix nicht in einer einzelnen Abfrage verwenden – auch nicht für verschiedene Eigenschaften.

### Suchen nach Eigenschaften {#search-for-properties}

Hier suchen Sie nach allen Seiten einer bestimmten Vorlage, indem Sie die Eigenschaft `cq:template` verwenden:

`http://<host>:<port>/bin/querybuilder.json?property=cq%3atemplate&property.value=%2fconf%2fwknd%2fsettings%2fwcm%2ftemplates%2fadventure-page-template&type=cq%3aPageContent`

```xml
type=cq:PageContent
property=cq:template
property.value=/conf/wknd/settings/wcm/templates/adventure-page-template
```

Dies hat den Nachteil, dass nicht die Seiten selbst, sondern die `jcr:content`-Knoten der Seiten zurückgegeben werden. Die Lösung besteht hierbei darin, nach dem relativen Pfad zu suchen:

`http://<host>:<port>/bin/querybuilder.json?property=jcr%3acontent%2fcq%3atemplate&property.value=%2fconf%2fwknd%2fsettings%2fwcm%2ftemplates%2fadventure-page-template&type=cq%3aPage`

```xml
type=cq:Page
property=jcr:content/cq:template
property.value=/conf/wknd/settings/wcm/templates/adventure-page-template
```

### Suchen nach mehreren Eigenschaften {#search-for-multiple-properties}

Beim mehrfachen Verwenden des Eigenschaftsprädikats müssen Sie die Präfixe für die Anzahl erneut hinzufügen:

`http://<host>:<port>/bin/querybuilder.json?1_property=jcr%3acontent%2fcq%3atemplate&1_property.value=%2fconf%2fwknd%2fsettings%2fwcm%2ftemplates%2fadventure-page-template&2_property=jcr%3acontent%2fjcr%3atitle&2_property.value=Cycling%20Tuscany&type=cq%3aPage`

```xml
type=cq:Page
1_property=jcr:content/cq:template
1_property.value=/conf/wknd/settings/wcm/templates/adventure-page-template
2_property=jcr:content/jcr:title
2_property.value=Cycling Tuscany
```

### Suchen nach mehreren Eigenschaftswerten {#search-for-multiple-property-values}

Um große Gruppen zu vermeiden, wenn Sie nach mehreren Werten einer Eigenschaft (`"A" or "B" or "C"`) suchen möchten, können Sie der Prognose `property` mehrere Werte hinzufügen:

`http://<host>:<port>/bin/querybuilder.json?property=jcr%3atitle&property.1_value=Cycling%20Tuscany&property.2_value=Ski%20Touring&property.3_value=Whistler%20Mountain%20Biking`

```xml
property=jcr:title
property.1_value=Cycling Tuscany
property.2_value=Ski Touring
property.3_value=Whistler Mountain Biking
```

Bei Eigenschaften mit mehreren Werten können Sie auch verlangen, dass mehrere Werte übereinstimmen (`"A" and "B" and "C"`):

`http://<host>:<port>/bin/querybuilder.json?property=jcr%3atitle&property.and=true&property.1_value=Cycling%20Tuscany&property.2_value=Ski%20Touring&property.3_value=Whistler%20Mountain%20Biking`

```xml
property=jcr:title
property.and=true
property.1_value=Cycling Tuscany
property.2_value=Ski Touring
property.3_value=Whistler Mountain Biking
```

## {#refining-what-is-returned}

Standardmäßig gibt das QueryBuilder-JSON-Servlet einen Standardsatz mit Eigenschaften für jeden Knoten zurück, der im Suchergebnis enthalten ist (z. B. Pfad, Name, Titel usw.). Wenn Sie steuern möchten, welche Eigenschaften zurückgegeben werden, können Sie eine der folgenden Vorgehensweisen wählen:

Geben Sie Folgendes an

```xml
p.hits=full
```

In diesem Fall werden alle Eigenschaften für jeden Knoten eingeschlossen:

`http://<host>:<port>/bin/querybuilder.json?p.hits=full&property=jcr%3atitle&property.value=Cycling%20Tuscany`

```xml
property=jcr:title
property.value=Cycling Tuscany
p.hits=full
```

Verwenden

```xml
p.hits=selective
```

und geben Sie die Eigenschaften an, die Sie abrufen möchten

```xml
p.properties
```

durch ein Leerzeichen getrennt:

`http://<host>:<port>/bin/querybuilder.json?p.hits=selective&p.properties=sling%3aresourceType%20jcr%3aprimaryType&property=jcr%3atitle&property.value=Cycling%20Tuscany`

```xml
property=jcr:title
property.value=Cycling Tuscany
p.hits=selective
p.properties=sling:resourceType jcr:primaryType
```

Eine andere Möglichkeit besteht darin, untergeordnete Knoten in die Abfrage Builder-Antwort aufzunehmen. Dazu müssen Sie Folgendes angeben:

```xml
p.nodedepth=n
```

wobei `n` die Anzahl der Ebenen ist, die die Abfrage zurückgeben soll. Beachten Sie, dass ein untergeordneter Knoten nur dann zurückgegeben werden kann, wenn er von der Eigenschaftenauswahl angegeben wird

```xml
p.hits=full
```

Beispiel:

`http://<host>:<port>/bin/querybuilder.json?p.hits=full&p.nodedepth=5&property=jcr%3atitle&property.value=Cycling%20Tuscany`

```xml
property=jcr:title
property.value=Cycling Tuscany
p.hits=full
p.nodedepth=5
```

## Weitere Eigenschaften {#morepredicates}

Weitere Eigenschaften (Prädikate) finden Sie auf der [Seite mit der Referenz zu Query-Builder-Eigenschaften](query-builder-predicates.md)..

Sie können auch [Javadoc für die `PredicateEvaluator`-Klassen](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/eval/PredicateEvaluator.html) überprüfen. Das Javadoc für diese Klassen enthält die Liste mit den Eigenschaften, die Sie verwenden können.

Das Präfix des Klassennamens (z. B. `similar` in [`SimilarityPredicateEvaluator`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/eval/SimilarityPredicateEvaluator.html)) ist die *Haupteigenschaft* der Klasse. Diese Eigenschaft ist auch der Name der Eigenschaft, die in der Abfrage verwendet wird (in Kleinbuchstaben).

Für diese Haupteigenschaften können Sie die Abfrage verkürzen und `similar=/content/en` anstelle der vollständig qualifizierten Variante `similar.similar=/content/en` verwenden. Die vollqualifizierte Form muss für alle Eigenschaften einer Klasse genutzt werden, bei denen es sich nicht um die Haupteigenschaften handelt.

## Beispiel für die Nutzung der Query-Builder-API  {#example-query-builder-api-usage}

```java
   String fulltextSearchTerm = "WKND";

    // create query description as hash map (simplest way, same as form post)
    Map<String, String> map = new HashMap<String, String>();

// create query description as hash map (simplest way, same as form post)
    map.put("path", "/content");
    map.put("type", "cq:Page");
    map.put("group.p.or", "true"); // combine this group with OR
    map.put("group.1_fulltext", fulltextSearchTerm);
    map.put("group.1_fulltext.relPath", "jcr:content");
    map.put("group.2_fulltext", fulltextSearchTerm);
    map.put("group.2_fulltext.relPath", "jcr:content/@cq:tags");

    // can be done in map or with Query methods
    map.put("p.offset", "0"); // same as query.setStart(0) below
    map.put("p.limit", "20"); // same as query.setHitsPerPage(20) below

    Query query = builder.createQuery(PredicateGroup.create(map), session);
    query.setStart(0);
    query.setHitsPerPage(20);

    SearchResult result = query.getResult();

    // paging metadata
    int hitsPerPage = result.getHits().size(); // 20 (set above) or lower
    long totalMatches = result.getTotalMatches();
    long offset = result.getStartIndex();
    long numberOfPages = totalMatches / 20;

    //Place the results in XML to return to client
    DocumentBuilderFactory factory = DocumentBuilderFactory.newInstance();
    DocumentBuilder builder = factory.newDocumentBuilder();
    Document doc = builder.newDocument();

    //Start building the XML to pass back to the AEM client
    Element root = doc.createElement( "results" );
    doc.appendChild( root );

    // iterating over the results
    for (Hit hit : result.getHits()) {
       String path = hit.getPath();

      //Create a result element
      Element resultel = doc.createElement( "result" );
      root.appendChild( resultel );

      Element pathel = doc.createElement( "path" );
      pathel.appendChild( doc.createTextNode(path ) );
      resultel.appendChild( pathel );
    }
```

Ausführung der gleichen Abfrage per HTTP mit dem Query-Builder-Servlet (JSON):

`http://<host>:<port>/bin/querybuilder.json?path=/content&type=cq:Page&group.p.or=true&group.1_fulltext=WKND&group.1_fulltext.relPath=jcr:content&group.2_fulltext=WKND&group.2_fulltext.relPath=jcr:content/@cq:tags&p.offset=0&p.limit=20`

## Speichern und Laden von Abfragen {#storing-and-loading-queries}

Abfragen können zur späteren Verwendung im Repository gespeichert werden. `QueryBuilder` stellt die `storeQuery`-Methode mit der folgenden Signatur bereit:

```java
void storeQuery(Query query, String path, boolean createFile, Session session) throws RepositoryException, IOException;
```

Bei Verwendung der [`QueryBuilder#storeQuery`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/QueryBuilder.html#storequerycomdaycqsearchqueryjavalangstringbooleanjavaxjcrsession)-Methode wird die jeweilige Abfrage (`Query`) gemäß dem Argumentwert `createFile` im Repository als Datei oder als Eigenschaft gespeichert. Das folgende Beispiel zeigt, wie ein `Query` als Datei im Pfad `/mypath/getfiles` gespeichert wird:

```java
builder.storeQuery(query, "/mypath/getfiles", true, session);
```

Alle zuvor gespeicherten Abfragen können mit der [`QueryBuilder#loadQuery`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/QueryBuilder.html#loadqueryjavalangstringjavaxjcrsession)-Methode aus dem Repository geladen werden:

```java
Query loadQuery(String path, Session session) throws RepositoryException, IOException
```

Beispielsweise kann ein `Query`, der im Pfad `/mypath/getfiles` gespeichert ist, mit dem folgenden Codefragment geladen werden:

```java
Query loadedQuery = builder.loadQuery("/mypath/getfiles", session);
```

## Testen und Debuggen {#testing-and-debugging}

Für die Wiedergabe und das Debugging von Abfrage Builder-Abfragen können Sie die Abfrage Builder-Debugger-Konsole unter

`http://<host>:<port>/libs/cq/search/content/querydebug.html`

oder alternativ das JSON-Servlet von Abfrage Builder unter

`http://<host>:<port>/bin/querybuilder.json?path=/tmp`

`path=/tmp` ist nur ein Beispiel.

### Allgemeine Empfehlungen für das Debuggen {#general-debugging-recommendations}

### Erläuterung von XPath über Protokollierung {#obtain-explain-able-xpath-via-logging}

Erläutern Sie **alle** Abfragen während des Entwicklungszyklus für den festgelegten Zielindex.

1. Aktivieren Sie DEBUG-Protokolle für QueryBuilder, um eine zugrunde liegende erläuterbare XPath-Abfrage zu erhalten.
   * Navigieren Sie zu `https://<host>:<port>/system/console/slinglog`. Erstellen Sie eine neue Protokollfunktion für `com.day.cq.search.impl.builder.QueryImpl` unter **DEBUG**.
1. Nachdem DEBUG für die obige Klasse aktiviert wurde, zeigen die Protokolle den von Query Builder generierten XPath an.
1. Kopieren Sie die XPath-Abfrage aus dem Protokolleintrag für die zugehörige Abfrage Builder-Abfrage. Beispiel:
   * `com.day.cq.search.impl.builder.QueryImpl XPath query: /jcr:root/content//element(*, cq:Page)[(jcr:contains(jcr:content, "WKND") or jcr:contains(jcr:content/@cq:tags, "WKND"))]`
1. Fügen Sie die XPath-Abfrage in Abfrage &quot;Explain&quot;als XPath ein, um den Abfrage-Plan abzurufen.

### Erklärbaren XPath über den Abfrage Builder-Debugger {#obtain-explain-able-xpath-via-the-query-builder-debugger} abrufen

Verwenden Sie den Debugger AEM Abfrage Builder, um eine erklärbare XPath-Abfrage zu generieren.

![Query Builder-Debugger](assets/query-builder-debugger.png)

1. Geben Sie die Abfrage Builder-Abfrage im Abfrage Builder-Debugger an
1. Führen Sie die Suche durch.
1. Rufen Sie den generierten XPath ab.
1. Fügen Sie die XPath-Abfrage in Abfrage als XPath erklären ein, um den Abfrage-Plan zu erhalten.

>[!NOTE]
>
>Nicht-Abfrage Builder-Abfragen (XPath, JCR-SQL2) können direkt zur Erläuterung der Abfrage bereitgestellt werden.

## Debuggen von Abfragen per Protokollierung {#debugging-queries-with-logging}

>[!NOTE]
>
>Die Konfiguration der Protokollfunktionen wird im Dokument [Protokollierung](/help/implementing/developing/introduction/logging.md) beschrieben.

Die Protokollausgabe (INFO-Ebene) der Abfrage Builder-Implementierung bei der Ausführung der im vorherigen Abschnitt [Testen und Debuggen:](#testing-and-debugging) beschriebenen Abfrage

```xml
com.day.cq.search.impl.builder.QueryImpl executing query (predicate tree):
null=group: limit=20, offset=0[
    {group=group: or=true[
        {1_fulltext=fulltext: fulltext=WKND, relPath=jcr:content}
        {2_fulltext=fulltext: fulltext=WKND, relPath=jcr:content/@cq:tags}
    ]}
    {path=path: path=/content}
    {type=type: type=cq:Page}
]
com.day.cq.search.impl.builder.QueryImpl XPath query: /jcr:root/content//element(*, cq:Page)[(jcr:contains(jcr:content, "WKND") or jcr:contains(jcr:content/@cq:tags, "WKND"))]
com.day.cq.search.impl.builder.QueryImpl no filtering predicates
com.day.cq.search.impl.builder.QueryImpl query execution took 69 ms
```

Wenn Sie eine Abfrage mit Auswertungen von Eigenschaften verwenden, bei denen eine Filterung durchgeführt oder ein benutzerdefinierter Order-By-Vergleich verwendet wird, wird dies auch in der Abfrage angegeben:

```xml
com.day.cq.search.impl.builder.QueryImpl executing query (predicate tree):
null=group: [
    {nodename=nodename: nodename=*.jar}
    {orderby=orderby: orderby=@jcr:content/jcr:lastModified}
    {type=type: type=nt:file}
]
com.day.cq.search.impl.builder.QueryImpl custom order by comparator: jcr:content/jcr:lastModified
com.day.cq.search.impl.builder.QueryImpl XPath query: //element(*, nt:file)
com.day.cq.search.impl.builder.QueryImpl filtering predicates: {nodename=nodename: nodename=*.jar}
com.day.cq.search.impl.builder.QueryImpl query execution took 272 ms
```

## Javadoc-Links  {#javadoc-links}

| **Javadoc** | **Beschreibung** |
|---|---|
| [com.day.cq.search](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/package-summary.html) | Grundlegende Abfrage Builder- und Abfrage-API |
| [com.day.cq.search.result](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/result/package-summary.html) | Ergebnis-API |
| [com.day.cq.search.facets](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/facets/package-summary.html) | Facets |
| [com.day.cq.search.facets.buckets](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/facets/buckets/package-summary.html) | Behälter (in Facetten enthalten) |
| [com.day.cq.search.eval](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/eval/package-summary.html) | Predicate Evaluators |
| [com.day.cq.search.facets.extractors](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/facets/extractors/package-summary.html) | Facettenextraktoren (für Bewertungsfaktoren) |
| [com.day.cq.search.writer](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/writer/package-summary.html) | JSON Result Hit Writer for Abfrage Builder servlet (`/bin/querybuilder.json`) |
