---
title: Query Builder-API
description: Die Funktionalität von Asset Share Query Builder wird über einen Java&trade verfügbar gemacht. API und eine REST-API.
exl-id: d5f22422-c9da-4c9d-b81c-ffa5ea7cdc87
source-git-commit: d361ddc9a50a543cd1d5f260c09920c5a9d6d675
workflow-type: tm+mt
source-wordcount: '2008'
ht-degree: 50%

---

# Query Builder-API {#query-builder-api}

Mit dem Query Builder können Sie problemlos das Inhalts-Repository von AEM abfragen. Die Funktionalität wird über eine Java™-API und eine REST-API bereitgestellt. In diesem Dokument werden diese APIs beschrieben.

Der serverseitige Abfragegenerator ([`QueryBuilder`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/QueryBuilder.html)) akzeptiert eine Abfragebeschreibung, erstellt und führt eine XPath-Abfrage aus, filtert optional den Ergebnissatz und extrahiert bei Bedarf auch Facetten.

Die Abfragebeschreibung ist einfach eine Gruppe mit Eigenschaften ([`Predicate`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/Predicate.html)). Beispiel hierfür ist eine Volltexteigenschaft, die der Funktion `jcr:contains()` in XPath entspricht.

Für jeden Eigenschaftentyp ist eine Auswertungskomponente ([`PredicateEvaluator`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/eval/PredicateEvaluator.html)) vorhanden, die weiß, wie die jeweilige Eigenschaft für XPath, die Filterung und die Facettenextraktion verarbeitet werden muss. Es ist einfach, benutzerdefinierte Auswerter zu erstellen, die über die Laufzeit der OSGi-Komponente eingebunden werden.

Die REST-API bietet Zugriff auf dieselben Funktionen über HTTP, wobei Antworten in JSON gesendet werden.

>[!NOTE]
>
>Die QueryBuilder-API wird mithilfe der JCR-API erstellt. Sie können das AEM-JCR auch abfragen, indem Sie die JCR-API innerhalb eines OSGi-Bundles verwenden. Weitere Informationen erhalten Sie unter [Abfragen von Adobe Experience Manager-Daten mit der JCR-API](https://experienceleague.adobe.com/docs/experience-manager-65/developing/platform/query-builder/querybuilder-api.html).

## Gem-Sitzung {#gem-session}

[AEM Gems](https://experienceleague.adobe.com/docs/events/experience-manager-gems-recordings/overview.html?lang=en) ist eine Serie mit ausführlichen technischen Erläuterungen zu Adobe Experience Manager von Adobe-Experten.

In der [Sitzung zu Query Builder](https://experienceleague.adobe.com/docs/events/experience-manager-gems-recordings/gems2017/aem-search-forms-using-querybuilder.html?lang=en) erhalten Sie eine Übersicht und Informationen zur Verwendung des Tools.

## Beispielabfragen {#sample-queries}

Diese Beispiele werden in der Stilnotation der Java™-Eigenschaften angegeben. Verwenden Sie eine Java™-API, um sie mit der Java™-API zu verwenden. `HashMap` wie im folgenden API-Beispiel beschrieben.

Für das JSON-Servlet `QueryBuilder` umfasst jedes Beispiel einen Beispiel-Link zu einer AEM-Installation (am Standardspeicherort `http://<host>:<port>`). Melden Sie sich bei Ihrer AEM-Instanz an, bevor Sie diese Links verwenden.

>[!CAUTION]
>
>Standardmäßig zeigt das JSON-Servlet des Query Builder maximal zehn Treffer an.
>
>Wenn der folgende Parameter hinzugefügt wird, kann das Servlet alle Abfrageergebnisse anzeigen:
>
>`p.limit=-1`

>[!NOTE]
>
>Um die zurückgegebenen JSON-Daten in Ihrem Browser anzuzeigen, können Sie ein Plug-in wie JSONView für Firefox verwenden.

### Zurückgeben aller Ergebnisse {#returning-all-results}

Die folgende Abfrage **gibt zehn Ergebnisse zurück** (oder, um genau zu sein, maximal zehn), Sie jedoch über die **Anzahl der Treffer:** verfügbar ist:

`http://<host>:<port>/bin/querybuilder.json?path=/content&1_property=sling:resourceType&1_property.value=wknd/components/structure/page&1_property.operation=like&orderby=path`

```xml
path=/content
1_property=sling:resourceType
1_property.value=wknd/components/structure/page
1_property.operation=like
orderby=path
```

Dieselbe Abfrage (mit dem -Parameter `p.limit=-1`) **gibt alle Ergebnisse zurück** (Je nach Instanz kann es eine hohe Zahl geben):

`http://<host>:<port>/bin/querybuilder.json?path=/content&1_property=sling:resourceType&1_property.value=wknd/components/structure/page&1_property.operation=like&orderby=path&p.limit=-1`

```xml
path=/content
1_property=sling:resourceType
1_property.value=wknd/components/structure/page
1_property.operation=like
p.limit=-1
orderby=path
```

### Verwenden von „p.guessTotal“ zum Zurückgeben der Ergebnisse {#using-p-guesstotal-to-return-the-results}

Der Zweck des Parameters `p.guessTotal` ist das Zurückgeben der entsprechenden Ergebnisse, die angezeigt werden können, indem die richtigen Mindestwerte für `p.offset` und `p.limit` kombiniert werden. Der Vorteil der Nutzung dieses Parameters ist eine verbesserte Leistung bei großen Ergebnissätzen. Dieser Parameter vermeidet auch die Berechnung der vollständigen Summe (z. B. durch Aufruf von `result.getSize()`) und das Lesen der gesamten Ergebnismenge, optimiert bis hin zur Oak-Engine und dem Index. Dieser Prozess kann einen signifikanten Unterschied darstellen, wenn Hunderttausende von Ergebnissen vorliegen, sowohl bei der Ausführungszeit als auch bei der Speichernutzung.

Der Nachteil besteht bei diesem Parameter darin, dass Anwendern die genaue Gesamtsumme nicht angezeigt wird. Sie können jedoch eine Mindestanzahl von `p.guessTotal=1000` also liest es immer bis zu 1000. Auf diese Weise erhalten Sie genaue Summen für kleinere Ergebnismengen, aber wenn es mehr ist, können Sie nur &quot;und mehr&quot;anzeigen.

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

Die Abfrage gibt die `p.limit` Standardwert von `10` Ergebnisse mit `0` offset:

```xml
"success": true,
"results": 10,
"total": 10,
"more": true,
"offset": 0,
```

Sie können auch einen numerischen Wert verwenden, um bis zu einer benutzerdefinierten Anzahl von maximalen Ergebnissen zu zählen. Verwenden Sie die gleiche Abfrage wie oben, aber ändern Sie den Wert von `p.guessTotal` in `50`:

`http://<host>:<port>/bin/querybuilder.json?path=/content&1_property=sling:resourceType&1_property.value=wknd/components/structure/page&1_property.operation=like&p.guessTotal=50&orderby=path`

Es wird eine Zahl mit dem gleichen Standardwert von 10 Ergebnissen mit einem 0-Versatz zurückgegeben, es werden jedoch nur maximal 50 Ergebnisse angezeigt:

```xml
"success": true,
"results": 10,
"total": 50,
"more": true,
"offset": 0,
```

### Implementieren von Seitenumbrüchen {#implementing-pagination}

Standardmäßig stellt der Query Builder auch die Anzahl der Treffer bereit. Abhängig von der Ergebnisgröße kann diese Zahl lange dauern, da bei der Ermittlung der genauen Anzahl jedes Ergebnis auf Zugriffskontrolle überprüft werden muss. Meistens wird die Gesamtsumme verwendet, um die Paginierung für die Benutzeroberfläche des Endbenutzers zu implementieren. Da die Ermittlung der genauen Anzahl langsam sein kann, wird empfohlen, die Paginierung mit der Funktion guessTotal zu implementieren.

Die Benutzeroberfläche kann beispielsweise den folgenden Ansatz anpassen:

* Rufen Sie die genaue Anzahl der Gesamttreffer ([SearchResult.getTotalMatches()](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/result/SearchResult.html#getTotalMatches) oder die Summe in der querybuilder.json-Antwort) ab und zeigen Sie sie an (kleiner oder gleich 100).`querybuilder.json`
* Satz `guessTotal` auf 100 aufrufen, um Query Builder aufzurufen.

* Die Antwort kann das folgende Ergebnis enthalten:

   * `total=43`, `more=false` – gibt an, dass die Gesamtzahl der Treffer 43 beträgt. Auf der Benutzeroberfläche können auf der ersten Seite bis zu zehn Ergebnisse angezeigt werden und für die nächsten drei Seiten können Seitenumbrüche genutzt werden. Sie können diese Implementierung auch verwenden, um einen beschreibenden Text wie **„43 Ergebnisse gefunden“** anzuzeigen.
   * `total=100`, `more=true` – gibt an, dass die Gesamtzahl der Treffer größer als 100 und die genaue Anzahl unbekannt ist. Auf der Benutzeroberfläche können auf der ersten Seite bis zu zehn Ergebnisse angezeigt werden und für die nächsten zehn Seiten können Seitenumbrüche genutzt werden. Sie können diese Funktion auch verwenden, um Text wie **&quot;mehr als 100 Ergebnisse gefunden&quot;**. Wenn der Benutzer zur nächsten Seite wechselt, erhöhen Aufrufe an Query Builder die Beschränkung von `guessTotal` sowie der `offset` und `limit` Parameter.

Verwenden Sie außerdem `guessTotal` in Fällen, in denen die Benutzeroberfläche unendliches Scrollen verwenden muss, um zu verhindern, dass der Query Builder die genaue Trefferanzahl ermittelt.

### Suchen nach und Sortieren von JAR-Dateien (neueste zuerst) {#find-jar-files-and-order-them-newest-first}

`http://<host>:<port>/bin/querybuilder.json?type=nt:file&nodename=*.jar&orderby=@jcr:content/jcr:lastModified&orderby.sort=desc`

```xml
type=nt:file
nodename=*.jar
orderby=@jcr:content/jcr:lastModified
orderby.sort=desc
```

### Suchen nach allen Seiten und Sortieren nach der letzten Änderung {#find-all-pages-and-order-them-by-last-modified}

`http://<host>:<port>/bin/querybuilder.json?type=cq:Page&orderby=@jcr:content/cq:lastModified`

```xml
type=cq:Page
orderby=@jcr:content/cq:lastModified
```

### Suchen nach allen Seiten und Sortieren nach der letzten Änderung (in absteigender Reihenfolge) {#find-all-pages-and-order-them-by-last-modified-but-descending}

`http://<host>:<port>/bin/querybuilder.json?type=cq:Page&orderby=@jcr:content/cq:lastModified&orderby.sort=desc`

```xml
type=cq:Page
orderby=@jcr:content/cq:lastModified
orderby.sort=desc
```

### Volltextsuche, sortiert nach Bewertung {#fulltext-search-ordered-by-score}

`http://<host>:<port>/bin/querybuilder.json?fulltext=Management&orderby=@jcr:score&orderby.sort=desc`

```xml
fulltext=Management
orderby=@jcr:score
orderby.sort=desc
```

### Suchen nach Seiten, die mit einem bestimmten Tag versehen sind {#search-for-pages-tagged-with-a-certain-tag}

`http://<host>:<port>/bin/querybuilder.json?type=cq:Page&tagid=wknd:activity/cycling&tagid.property=jcr:content/cq:tags`

```xml
type=cq:Page
tagid=wknd:activity/cycling
tagid.property=jcr:content/cq:tags
```

Verwenden Sie die Eigenschaft `tagid` wie im Beispiel, wenn Sie die explizite Tag-ID kennen.

Verwenden Sie die Eigenschaft `tag` für den Tag-Titelpfad (ohne Leerstellen).

Im vorherigen Beispiel, weil Sie nach Seiten suchen (`cq:Page` -Knoten) verwenden Sie den relativen Pfad von diesem Knoten für die `tagid.property` predicate, was `jcr:content/cq:tags`. Standardmäßig wird die `tagid.property` würde `cq:tags`.

### Suchen unter mehreren Pfaden (mit Gruppen) {#search-under-multiple-paths-using-groups}

`http://<host>:<port>/bin/querybuilder.json?fulltext=Experience&group.1_path=/content/wknd/us/en/magazine&group.2_path=/content/wknd/us/en/adventures&group.p.or=true`

```xml
fulltext=Experience
group.p.or=true
group.1_path=/content/wknd/us/en/magazine
group.2_path=/content/wknd/us/en/adventures
```

Für diese Abfrage wird eine *Gruppe* (mit dem Namen `group`) verwendet. Dies dient dem Abtrennen von Unterausdrücken in einer Abfrage, ähnlich wie mit Klammern in Standardnotationen. Beispielweise kann die vorherige Abfrage wie folgt auf vertrautere Weise ausgedrückt werden:

`"Experience" and ("/content/wknd/us/en/magazine" or "/content/wknd/us/en/adventures")`

Im Beispiel wird in der Gruppe die Eigenschaft `path` mehrere Male genutzt. Um die beiden Instanzen der Eigenschaft zu unterscheiden und zu sortieren (die Sortierung ist für einige Eigenschaften erforderlich), müssen Sie den Eigenschaften `N_` voranstellen, wobei `N` für den Sortierungsindex steht. Im obigen Beispiel lauten die sich ergebenden Eigenschaften `1_path` und `2_path`.

Das `p` in `p.or` ist ein spezielles Trennzeichen, mit dem angezeigt wird, dass ein `or`Parameter *der Gruppe folgt (in diesem Fall ein*) und keine Untereigenschaft der Gruppe, z. B. `1_path`.

Wenn nicht `p.or` angegeben ist, werden alle Eigenschaften zusammen UNDed angegeben, d. h. jedes Ergebnis muss alle Eigenschaften erfüllen.

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

Der Nachteil ist, dass die `jcr:content` -Knoten der Seiten, nicht die Seiten selbst, werden zurückgegeben. Um dieses Problem zu beheben, können Sie nach relativem Pfad suchen:

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

So vermeiden Sie große Gruppen, wenn Sie nach mehreren Werten einer Eigenschaft suchen möchten (`"A" or "B" or "C"`), können Sie mehrere Werte für die `property` predicate:

`http://<host>:<port>/bin/querybuilder.json?property=jcr%3atitle&property.1_value=Cycling%20Tuscany&property.2_value=Ski%20Touring&property.3_value=Whistler%20Mountain%20Biking`

```xml
property=jcr:title
property.1_value=Cycling Tuscany
property.2_value=Ski Touring
property.3_value=Whistler Mountain Biking
```

Bei Eigenschaften mit mehreren Werten können Sie auch festlegen, dass mehrere Werte übereinstimmen müssen (`"A" and "B" and "C"`):

`http://<host>:<port>/bin/querybuilder.json?property=jcr%3atitle&property.and=true&property.1_value=Cycling%20Tuscany&property.2_value=Ski%20Touring&property.3_value=Whistler%20Mountain%20Biking`

```xml
property=jcr:title
property.and=true
property.1_value=Cycling Tuscany
property.2_value=Ski Touring
property.3_value=Whistler Mountain Biking
```

## Verfeinern der Rückgabe {#refining-what-is-returned}

Standardmäßig gibt das QueryBuilder-JSON-Servlet einen Standardsatz von Eigenschaften für jeden Knoten im Suchergebnis zurück (z. B. Pfad, Name und Titel). Um die Kontrolle darüber zu erhalten, welche Eigenschaften zurückgegeben werden, können Sie eine der folgenden Aktionen durchführen:

Geben Sie

```xml
p.hits=full
```

In diesem Fall sind alle Eigenschaften für jeden Knoten enthalten:

`http://<host>:<port>/bin/querybuilder.json?p.hits=full&property=jcr%3atitle&property.value=Cycling%20Tuscany`

```xml
property=jcr:title
property.value=Cycling Tuscany
p.hits=full
```

Verwenden Sie

```xml
p.hits=selective
```

Geben Sie die Eigenschaften an, in die Sie einsteigen möchten

```xml
p.properties
```

Durch ein Leerzeichen getrennt:

`http://<host>:<port>/bin/querybuilder.json?p.hits=selective&p.properties=sling%3aresourceType%20jcr%3aprimaryType&property=jcr%3atitle&property.value=Cycling%20Tuscany`

```xml
property=jcr:title
property.value=Cycling Tuscany
p.hits=selective
p.properties=sling:resourceType jcr:primaryType
```

Eine andere Möglichkeit besteht darin, untergeordnete Knoten in die Query Builder-Antwort einzufügen. Geben Sie

```xml
p.nodedepth=n
```

Wo `n` ist die Anzahl der Ebenen, die die Abfrage zurückgeben soll. Damit ein untergeordneter Knoten zurückgegeben wird, muss er durch den Eigenschaften-Selektor angegeben werden

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

Weitere Eigenschaften (Prädikate) finden Sie auf der [Seite mit der Referenz zu Query Builder-Eigenschaften](query-builder-predicates.md).

Sie können auch das [Javadoc für die `PredicateEvaluator`-Klassen](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/eval/PredicateEvaluator.html) überprüfen. Das Javadoc für diese Klassen enthält die Liste mit den Eigenschaften, die Sie verwenden können.

Das Präfix des Klassennamens (z. B. `similar` in [`SimilarityPredicateEvaluator`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/eval/SimilarityPredicateEvaluator.html)) ist die *Haupteigenschaft* der Klasse. Diese Eigenschaft ist auch der Name der Eigenschaft, die in der Abfrage verwendet wird (in Kleinbuchstaben).

Für Haupteigenschaften dieser Art können Sie die Abfrage verkürzen und anstelle der vollqualifizierten Variante `similar=/content/en` die Kurzversion `similar.similar=/content/en` verwenden. Die vollqualifizierte Form muss für alle Eigenschaften einer Klasse genutzt werden, bei denen es sich nicht um die Haupteigenschaften handelt.

## Beispiel für die Nutzung der Query Builder-API {#example-query-builder-api-usage}

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

Ausführung der gleichen Abfrage per HTTP mit dem Query Builder-Servlet (JSON):

`http://<host>:<port>/bin/querybuilder.json?path=/content&type=cq:Page&group.p.or=true&group.1_fulltext=WKND&group.1_fulltext.relPath=jcr:content&group.2_fulltext=WKND&group.2_fulltext.relPath=jcr:content/@cq:tags&p.offset=0&p.limit=20`

## Speichern und Laden von Abfragen {#storing-and-loading-queries}

Abfragen können zur späteren Verwendung im Repository gespeichert werden. Der `QueryBuilder` stellt die `storeQuery`-Methode mit der folgenden Signatur bereit:

```java
void storeQuery(Query query, String path, boolean createFile, Session session) throws RepositoryException, IOException;
```

Bei Verwendung der [`QueryBuilder#storeQuery`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/QueryBuilder.html#storeQuery-com.day.cq.search.Query-java.lang.String-boolean-javax.jcr.Session-)-Methode wird die jeweilige Abfrage (`Query`) gemäß dem Argumentwert `createFile` im Repository als Datei oder als Eigenschaft gespeichert. Im folgenden Beispiel wird veranschaulicht, wie Sie eine `Query` unter dem Pfad `/mypath/getfiles` als Datei speichern:

```java
builder.storeQuery(query, "/mypath/getfiles", true, session);
```

Alle zuvor gespeicherten Abfragen können mit der [`QueryBuilder#loadQuery`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/QueryBuilder.html#loadQuery-java.lang.String-javax.jcr.Session-)-Methode aus dem Repository geladen werden:

```java
Query loadQuery(String path, Session session) throws RepositoryException, IOException
```

Eine unter dem Pfad `/mypath/getfiles` gespeicherte `Query` kann beispielsweise mit dem folgenden Snippet geladen werden:

```java
Query loadedQuery = builder.loadQuery("/mypath/getfiles", session);
```

## Testen und Debuggen {#testing-and-debugging}

Zum Experimentieren mit und Debuggen von Query Builder-Abfragen können Sie die Query Builder-Debugger-Konsole verwenden:

`http://<host>:<port>/libs/cq/search/content/querydebug.html`

Oder alternativ das Query Builder-JSON-Servlet unter

`http://<host>:<port>/bin/querybuilder.json?path=/tmp`

Die `path=/tmp` ist nur ein Beispiel.

### Allgemeine Empfehlungen für das Debuggen {#general-debugging-recommendations}

### Abrufen eines erläuterbaren XPath per Protokollierung {#obtain-explain-able-xpath-via-logging}

Erklären **all** Abfragen während des Entwicklungszyklus mit dem Zielindex-Satz verknüpft.

1. Aktivieren Sie DEBUG-Protokolle für QueryBuilder, um eine zugrunde liegende, erklärbare XPath-Abfrage zu erhalten.
   * Navigieren Sie zu `https://<host>:<port>/system/console/slinglog`. Logger für `com.day.cq.search.impl.builder.QueryImpl` at **DEBUG**.
1. Nachdem DEBUG für die obige Klasse aktiviert wurde, zeigen die Protokolle den von Query Builder generierten XPath an.
1. Kopieren Sie die XPath-Abfrage aus dem Protokolleintrag für die zugeordnete Query Builder-Abfrage. Beispiel:
   * `com.day.cq.search.impl.builder.QueryImpl XPath query: /jcr:root/content//element(*, cq:Page)[(jcr:contains(jcr:content, "WKND") or jcr:contains(jcr:content/@cq:tags, "WKND"))]`
1. Fügen Sie die XPath-Abfrage in Abfrage erläutern als XPath ein, damit Sie den Abfrageplan abrufen können.

### Abrufen von erläuterbarem XPath über den Query Builder-Debugger {#obtain-explain-able-xpath-via-the-query-builder-debugger}

Verwenden Sie den AEM-Query Builder-Debugger, um eine erläuterbare XPath-Abfrage zu generieren.

![Query Builder-Debugger](assets/query-builder-debugger.png)

1. Stellen Sie die Query Builder-Abfrage im Query Builder-Debugger bereit.
1. Ausführen der Suche
1. Abrufen des generierten XPath
1. Fügen Sie die XPath-Abfrage in Abfrage erläutern als XPath ein, damit Sie den Abfrageplan abrufen können.

>[!NOTE]
>
>Abfragen, die keine Abfragen sind (XPath, JCR-SQL2), können direkt zur Erläuterung der Abfrage bereitgestellt werden.

## Debuggen von Abfragen per Protokollierung {#debugging-queries-with-logging}

>[!NOTE]
>
>Die Konfiguration der Protokollfunktionen wird im Dokument [Protokollierung](/help/implementing/developing/introduction/logging.md) beschrieben.

Die Protokollausgabe (INFO-Ebene) der Query Builder-Implementierung beim Ausführen der Abfrage, die im vorherigen Abschnitt unter [Testen und Debuggen](#testing-and-debugging) beschrieben wurde:

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

Wenn Sie über eine Abfrage mit Prädikat-Auswertern verfügen, die filtern oder eine benutzerdefinierte Reihenfolge nach Vergleichspräparaten verwenden, wird dies in der Abfrage angegeben:

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

## Javadoc-Links {#javadoc-links}

| **Javadoc** | **Beschreibung** |
|---|---|
| [com.day.cq.search](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/package-summary.html) | Grundlegende Query Builder- und Abfrage-API |
| [com.day.cq.search.result](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/result/package-summary.html) | Ergebnis-API |
| [com.day.cq.search.facets](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/facets/package-summary.html) | Facetten |
| [com.day.cq.search.facets.buckets](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/facets/buckets/package-summary.html) | Behälter (in Facetten enthalten) |
| [com.day.cq.search.eval](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/eval/package-summary.html) | Eigenschaftenauswertungen |
| [com.day.cq.search.facets.extractors](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/facets/extractors/package-summary.html) | Facettenextraktoren (für Auswertungen) |
| [com.day.cq.search.writer](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/search/writer/package-summary.html) | JSON Result Hit Writer für Query Builder-Servlet (`/bin/querybuilder.json`) |
