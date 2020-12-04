---
title: Query Builder-Eigenschaftsverweis
description: Eigene Referenz für die Abfrage Builder-API.
translation-type: tm+mt
source-git-commit: 90b635cb31af910e08bdee7925cec0c7beb05318
workflow-type: tm+mt
source-wordcount: '2221'
ht-degree: 19%

---


# Query Builder-Eigenschaftsverweis {#query-builder-predicate-reference}

## Allgemein {#general}

### root {#root}

Dies ist die Gruppe mit den root-Vorhersagen. Es unterstützt alle Gruppenfunktionen und ermöglicht das Festlegen globaler Abfragen.

Der Name „root“ wird in Abfragen nie verwendet, er ist impliziert.

#### Eigenschaften {#properties-18}

* **`p.offset`** - Zahl, die den Beginn der Ergebnisseite angibt, d. h. wie viele Elemente übersprungen werden sollen
* **`p.limit`** - Nummer zur Angabe des Seitenformats
* **`p.guessTotal`** - empfohlen: Vermeidung der Berechnung des Gesamtergebnisses, das kostspielig sein kann; entweder eine Zahl, die angibt, bis zu welcher Höchstzahl gezählt werden soll (z. B. 1000, eine Zahl, die den Benutzern genügend Rückmeldungen über die Rohgröße und genaue Zahlen für kleinere Ergebnisse gibt), oder  `true` um nur bis zu dem notwendigen Minimum zu zählen  `p.offset` +  `p.limit`
* **`p.excerpt`** - wenn auf  `true`Volltextausschnitt eingestellt
* **`p.hits`** - (nur für das JSON-Servlet) Wählen Sie die Art, wie die Treffer als JSON geschrieben werden, mit den folgenden Standardaufrufen (erweiterbar über den ResultHitWriter-Dienst):
   * **`simple`** - Minimale Elemente wie  `path`,  `title`,  `lastmodified`,  `excerpt` (falls festgelegt)
   * **`full`** - Sling JSON-Rendering des Knotens mit  `jcr:path` Angabe des Pfades des des Treffers: standardmäßig nur Listen der direkten Eigenschaften des Knotens, einschließlich eines tieferen Baumes mit  `p.nodedepth=N`0 Bedeutung des gesamten, unendlichen Unterbaums; hinzufügen,  `p.acls=true` um die JCR-Berechtigungen der aktuellen Sitzung für das angegebene Ergebniselement (Zuordnungen:  `create` =  `add_node`,  `modify` =  `set_property`,  `delete` =  `remove`)
   * **`selective`** - Nur Eigenschaften, die in  `p.properties`der Liste relativer Pfade angegeben sind (Verwendung  `+` in URLs); Wenn der relative Pfad eine Tiefe hat, werden  `>1` diese als untergeordnete Objekte dargestellt. Die  `jcr:path` Eigenschaft special enthält den Pfad des Treffers

### -Gruppe{#group}

Diese Prognose ermöglicht das Erstellen verschachtelter Bedingungen. Gruppen können verschachtelte Gruppen enthalten. Alles in einer Abfrage Builder-Abfrage befindet sich implizit in einer Stammgruppe, die auch die Parameter `p.or` und `p.not` haben kann.

Im Folgenden finden Sie ein Beispiel für die Zuordnung einer der beiden Eigenschaften zu einem Wert:

```text
group.p.or=true
group.1_property=jcr:title
group.1_property.value=My Page
group.2_property=navTitle
group.2_property.value=My Page
```

Dies ist konzeptionell `(1_property` ODER `2_property)`.

Folgendes ist ein Beispiel für verschachtelte Gruppen:

```text
fulltext=Management
group.p.or=true
group.1_group.path=/content/wknd/ch/de
group.1_group.type=cq:Page
group.2_group.path=/content/dam/wknd
group.2_group.type=dam:Asset
```

Dieser sucht nach dem Begriff **Management** innerhalb von Seiten in `/content/wknd/ch/de` oder in Assets in `/content/dam/wknd`.

Dies ist konzeptionell `fulltext AND ( (path AND type) OR (path AND type) )`. Beachten Sie, dass solche ODER-Verbindungen aus Leistungsgründen gute Indizes benötigen.

#### Eigenschaften {#properties-6}

* **`p.or`** - Wenn auf  `true`festgelegt, muss nur eine Vorhersage in der Gruppe übereinstimmen. Der Standardwert ist `false`, d. h. alle müssen übereinstimmen
* **`p.not`** - Wenn auf  `true`gesetzt, wird die Gruppe umgekehrt (standardmäßig  `false`)
* **`<predicate>`** - fügt verschachtelte Prädikate hinzu.
* **`N_<predicate>`** - fügt mehrere verschachtelte Vorhersagen derselben Zeit hinzu, wie  `1_property, 2_property, ...`

### orderby {#orderby}

Diese Prognose ermöglicht das Sortieren der Ergebnisse. Wenn die Sortierung nach mehreren Eigenschaften erforderlich ist, muss diese Prognose mehrmals mit dem Zahlenpräfix hinzugefügt werden, z. B. `1_orderby=first`, `2_oderby=second`.

#### Eigenschaften {#properties-13}

* **`orderby`** - entweder der Name der JCR-Eigenschaft, der beispielsweise durch ein vorangestelltes @ angegeben wird,  `@jcr:lastModified` oder  `@jcr:content/jcr:title`, oder eine andere Vorhersage in der Abfrage,  `2_property`nach der die Sortierung erfolgen soll.
* **`sort`** - Sortierrichtung, entweder  `desc` für absteigend oder  `asc` aufsteigend (Standard)
* **`case`** - wenn die Sortierung so eingestellt  `ignore` wird, dass die Groß-/Kleinschreibung nicht berücksichtigt wird, d. h.  `a` sie liegt vor  `B`; Wenn leer oder ausgelassen, wird bei der Sortierung die Groß-/Kleinschreibung beachtet, d. h.  `B` vor  `a`

## Prädikate {#predicates}

### boolproperty {#boolproperty}

Diese Vorhersage stimmt mit den booleschen JCR-Eigenschaften überein. Akzeptiert nur die Werte `true` und `false`. Bei `false` stimmt sie überein, wenn die Eigenschaft den Wert `false` hat oder wenn sie überhaupt nicht vorhanden ist. Dies kann für die Prüfung auf boolesche Flags nützlich sein, die nur festgelegt werden, wenn sie aktiviert sind.

Der geerbte Parameter `operation` hat keine Bedeutung.

Diese Prognose unterstützt die Facettenanalyse und stellt Behälter für jeden `true`- oder `false`-Wert bereit, jedoch nur für vorhandene Eigenschaften.

#### Eigenschaften {#properties}

* **`boolproperty`** - relativer Pfad zu einer Eigenschaft, z. B.  `myFeatureEnabled` oder  `jcr:content/myFeatureEnabled`
* **`value`** - Wert, für den die Eigenschaft überprüft werden soll,  `true` oder  `false`

### contentfragment {#contentfragment}

Diese Prognose beschränkt das Ergebnis auf Inhaltsfragmente.

* Filterung wird nicht unterstützt.
* Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-1}

* **`contentfragment`** - Kann mit jedem Wert verwendet werden, um auf Inhaltsfragmente zu prüfen.

### `dateComparison` {#datecomparison}

Diese Prognose vergleicht zwei JCR-Datumseigenschaften miteinander. Kann testen, ob sie gleich, ungleich, größer oder größer-oder-gleich sind.

Dies ist eine reine Filtereigenschaft und kann keine Suchindizes nutzen.

#### Eigenschaften {#properties-2}

* **`property1`** - Pfad zur ersten Datumseigenschaft
* **`property2`** - Pfad zur zweiten Datumseigenschaft
* **`operation`**
   * `=` für exakte Übereinstimmung (Standard)
   * `!=` für Ungleichheitsvergleich
   * `>` für  `property1` größer als  `property2`
   * `>=` für  `property1` größer oder gleich  `property2`

### daterange {#daterange}

Diese Vorhersage stimmt mit den JCR-Datumseigenschaften mit einem Datums-/Uhrzeitintervall überein. Hierbei wird ISO8601 verwendet
Format für Daten und Uhrzeiten (`YYYY-MM-DDTHH:mm:ss.SSSZ`) und erlaubt auch partielle Darstellungen, wie `YYYY-MM-DD`. Alternativ kann der Zeitstempel als POSIX-Zeit angegeben werden.

Sie können nach allen Elementen zwischen zwei Zeitstempeln suchen, nach allem, was neuer oder älter als ein jeweiliges Datum ist, und aus inklusiven oder offenen Intervallen auswählen.

Es unterstützt die Extraktion von Facetten und stellt die Behälter `today`, `this week`, `this month`, `last 3 months`, `this year`, `last year` und `earlier than last year` bereit.

Filterung wird nicht unterstützt.

#### Eigenschaften {#properties-3}

* **`property`** - zum Beispiel relativer Pfad zu einer  `DATE` Eigenschaft  `jcr:lastModified`
* **`lowerBound`** - niedrigere Datumsgrenze zur Überprüfung der Eigenschaft, z. B.  `2014-10-01`
* **`lowerOperation`** -  `>` (neuer) oder  `>=` (ab oder neuer), gilt für die  `lowerBound`. Standard: `>`
* **`upperBound`** - Obergrenze zur Überprüfung der Eigenschaft, z. B.  `2014-10-01T12:15:00`
* **`upperOperation`** -  `<` (älter) oder  `<=` (älter), gilt für die  `upperBound`. Standard: `<`
* **`timeZone`** - Kennung der Zeitzone, die verwendet werden soll, wenn keine ISO-8601-Datumszeichenfolge angegeben wird. Der Standardwert ist die standardmäßige Zeitzone des Systems.

### excludepaths {#excludepaths}

Diese Prognose schließt Nodes aus dem Ergebnis aus, bei dem ihr Pfad mit einem regulären Ausdruck übereinstimmt.

Dies ist eine reine Filtereigenschaft und kann keine Suchindizes nutzen.

Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-4}

* **`excludepaths`** - Regulärer Ausdruck, der anhand von Ergebnispfaden ausgewertet wird, wobei übereinstimmende aus dem Ergebnis ausgeschlossen werden.

### fulltext {#fulltext}

Dadurch wird die Suche nach Begriffen im Volltext-Index prognostiziert.

Filterung wird nicht unterstützt.

Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-5}

* **`fulltext`** - Suchbegriff(e)
* **`relPath`** - Der relative Pfad, der in der Eigenschaft oder dem Teilknoten durchsucht werden soll. Diese Eigenschaft ist optional.

### hasPermission {#haspermission}

Diese Prognose beschränkt das Ergebnis auf Elemente, bei denen die aktuelle Sitzung über die angegebenen JCR-Berechtigungen verfügt.](https://docs.adobe.com/content/docs/en/spec/jcr/2.0/16_Access_Control_Management.html#16.2.3%20Standard%20Privileges)[

Dies ist eine reine Filtereigenschaft und kann keine Suchindizes nutzen. Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-7}

* **`hasPermission`** - kommagetrennte JCR-Berechtigungen, die die aktuelle Benutzersitzung ALLE für den betreffenden Knoten haben muss; z.  `jcr:write`B.  `jcr:modifyAccessControl`

### language {#language}

Diese Prognose findet AEM Seiten in einer bestimmten Sprache. Hierbei wird sowohl die Spracheigenschaft der Seite als auch der Seitenpfad betrachtet, der häufig die Sprache oder das Gebietsschema in einer Site-Struktur der höchsten Ebene enthält.

Dies ist eine reine Filtereigenschaft und kann keine Suchindizes nutzen.

Es unterstützt die Facetten-Extraktion und stellt Behälter für jeden einzelnen Sprachcode bereit.

#### Eigenschaften {#properties-8}

* **`language`** - ISO-Sprachcode, z. B.  `de`

### mainasset {#mainasset}

Diese Prognose prüft, ob ein Knoten ein DAM-Hauptasset und kein Unterasset ist. Dies ist im Grunde jeder Knoten, der sich nicht in einem Unter-Assets-Knoten befindet. Hierbei wird nicht auf den Knotentyp `dam:Asset` geprüft. Um diese Prognose zu verwenden, setzen Sie einfach `mainasset=true` oder `mainasset=false`. Es gibt keine weiteren Eigenschaften.

Dies ist eine reine Filtereigenschaft und kann keine Suchindizes nutzen.

Es unterstützt die Extraktion von Facetten und bietet zwei Behälter für Haupt- und Unterelemente.

#### Eigenschaften {#properties-9}

* **`mainasset`** - Boolescher Wert  `true` für Hauptelemente  `false` für Teilassets

### memberOf {#memberof}

Diese Prognose findet Elemente, die Mitglied einer bestimmten [Sling-Ressourcensammlung](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/resource/collection/ResourceCollection.html) sind.

Dies ist eine reine Filtereigenschaft und kann keine Suchindizes nutzen.

Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-10}

* **`memberOf`** - Pfad zur Sling-Ressourcensammlung

### nodename {#nodename}

Diese Vorhersage stimmt mit den JCR-Knotennamen überein.

Es unterstützt die facet-Extraktion und stellt Behälter für jeden eindeutigen Knotennamen (Dateinamen) bereit.

#### Eigenschaften {#properties-11}

* **`nodename`** - Namensmuster des Knotens, das Platzhalter zulässt:  `*` = beliebige oder keine Zeichen,  `?` = beliebige Zeichen,  `[abc]` = nur Zeichen in Klammern

### notexpired {#notexpired}

Diese Vorhersage stimmt mit Elementen überein, indem geprüft wird, ob eine JCR-Datumseigenschaft größer oder gleich der aktuellen Serverzeit ist. Dies kann verwendet werden, um einen `expiresAt`-Wert zu prüfen und die Ergebnisse auf diejenigen zu beschränken, die noch nicht abgelaufen sind (`notexpired=true`) oder die bereits abgelaufen sind (`notexpired=false`).

Filterung wird nicht unterstützt.

Es unterstützt Facetten-Extraktionen auf die gleiche Weise wie das Prädikat [`daterange`](#daterange).

#### Eigenschaften {#properties-12}

* **`notexpired`** - boolean,  `true` für noch nicht abgelaufen (Datum in der Zukunft oder gleich),  `false` für abgelaufen (Datum in der Vergangenheit) (erforderlich)
* **`property`** - Relativer Pfad zur zu prüfenden  `DATE` Eigenschaft (erforderlich)

### path {#path}

Dadurch werden Suchvorgänge innerhalb eines angegebenen Pfades vorhergesagt.

Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-14}

* **`path`** - Hiermit wird das Pfadmuster definiert.
   * Abhängig von der Eigenschaft `exact` stimmt entweder die gesamte Unterstruktur überein (z. B. `//*` in xpath anhängen, aber beachten Sie, dass dies nicht den Basispfad enthält) oder es wird nur ein exakter Pfad gefunden, der Platzhalter (`*`) enthalten kann.
      * Standardwert ist `true`
   * Wenn die Eigenschaft `self`festgelegt ist, wird die gesamte Unterstruktur einschließlich des Basisknotens durchsucht.
* **`exact`** - Wenn  `exact` dies  `true`der Fall ist, muss der genaue Pfad übereinstimmen, er kann jedoch einfache Platzhalter (`*`) enthalten, die mit Namen übereinstimmen, jedoch nicht  `/`; Wenn es  `false` (Standard) ist, werden alle untergeordneten Elemente einbezogen (optional)
* **`flat`** - durchsucht nur die direkten untergeordneten Elemente (z. B.  `/*` in xpath anhängen) (nur verwendet, wenn  `exact` nicht true, optional)
* **`self`** - Durchsucht den Teilbaum aber bezieht den als Pfad angegebenen Basisknoten mit ein (keine Platzhalter)

### property {#property}

Diese Vorhersage stimmt mit den JCR-Eigenschaften und deren Werten überein.

Es unterstützt die Facettenanalyse und stellt Behälter für jeden eindeutigen Eigenschaftswert in den Ergebnissen bereit.

#### Eigenschaften {#properties-15}

* **`property`** - zum Beispiel relativer Pfad zur Eigenschaft  `jcr:title`
* **`value`** - Wert, für den die Eigenschaft überprüft werden soll; folgt dem JCR-Eigenschaftstyp zu Zeichenfolgenkonvertierungen
* **`N_value`** - Verwendung  `1_value`,  `2_value`... , um nach mehreren Werten zu suchen ( `OR` standardmäßig mit  `AND` if  `and=true`)
* **`and`** -  `true` für die Kombination mehrerer Werte (`N_value`mit  `AND`
* **`operation`**
   * `equals` für exakte Übereinstimmung (Standard)
   * `unequals` für Ungleichheitsvergleich
   * `like` für die Verwendung der Funktion  `jcr:like` xpath (optional)
   * `not` für keine Übereinstimmung (z. B.  `not(@prop)` in xpath wird value param ignoriert)
   * `exists` für Existenzkontrolle
      * `true` Die Eigenschaft muss vorhanden sein
      * `false` ist identisch mit  `not` und ist Standard
* **`depth`** - Anzahl der Platzhalterebenen, unter denen die Eigenschaft/der relative Pfad vorhanden sein kann (z. B.  `property=size depth=2` überprüft  `node/size`werden  `node/*/size` und  `node/*/*/size`)

### rangeproperty {#rangeproperty}

Diese Prognose stimmt mit einer JCR-Eigenschaft für ein Intervall überein. Dies gilt für Eigenschaften mit linearen Typen wie `LONG`, `DOUBLE` und `DECIMAL`. Details zu `DATE`[`daterange`](#daterange) finden Sie im Abschnitt zur Eigenschaft „“, die für Eingaben im Datumsformat optimiert wurde.

Sie können eine Untergrenze, eine Obergrenze oder beides definieren. Der Vorgang (z. B. kleiner als oder gleich) kann auch einzeln für die untere und obere Grenze angegeben werden.

Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-16}

* **`property`** - relativer Pfad zur Eigenschaft
* **`lowerBound`** - Untergrenze für die Eigenschaft zur Überprüfung
* **`lowerOperation`** -  `>` (Standard) oder  `>=`, gilt für  `lowerValue`
* **`upperBound`** - Obergrenze für die Eigenschaft zur Überprüfung
* **`upperOperation`** -  `<` (Standard) oder  `<=`, gilt für  `lowerValue`
* **`decimal`** -  `true` wenn die geprüfte Eigenschaft vom Typ Decimal ist

### relativedaterange {#relativedaterange}

Diese Vorhersage stimmt mit den `JCR DATE`-Eigenschaften mit einem Datums-/Uhrzeitintervall überein, wobei Zeitabweichungen relativ zur aktuellen Serverzeit verwendet werden. Sie können `lowerBound` und `upperBound` entweder einen Millisekunden-Wert oder die Bugzilla-Syntax `1s 2m 3h 4d 5w 6M 7y` (eine Sekunde, zwei Minuten, drei Stunden, vier Tage, fünf Wochen, sechs Monate, sieben Jahre) angeben. Präfix mit `-`, um einen negativen Offset vor der aktuellen Zeit anzugeben. Wenn Sie nur `lowerBound` oder `upperBound` angeben, wird für die andere standardmäßig `0` verwendet, was die aktuelle Zeit darstellt.

Beispiel:

* `upperBound=1h` (und nein  `lowerBound`) wählt etwas in der nächsten Stunde aus
* `lowerBound=-1d` (und nein  `upperBound`) wählt in den letzten 24 Stunden irgendetwas aus
* `lowerBound=-6M` und  `upperBound=-3M` wählt in den letzten 3 bis 6 Monaten alles aus
* `lowerBound=-1500` und  `upperBound=5500` wählt in Zukunft alles zwischen 1500 und 500 Millisekunden aus
* `lowerBound=1d` und übermorgen alles  `upperBound=2d` auswählen

Hinweis: Schaltjahre werden nicht berücksichtigt und alle Monate haben 30 Tage.

Filterung wird nicht unterstützt.

Es unterstützt Facetten-Extraktionen auf die gleiche Weise wie das Prädikat [`daterange`](#daterange).

#### Eigenschaften {#properties-17}

* **`upperBound`** - oberes Datum in Millisekunden oder  `1s 2m 3h 4d 5w 6M 7y` (eine Sekunde, zwei Minuten, drei Stunden, vier Tage, fünf Wochen, sechs Monate, sieben Jahre) im Verhältnis zur aktuellen Serverzeit, Verwendung  `-` für negativen Offset
* **`lowerBound`** - niedrigere Datumsgrenze in Millisekunden oder  `1s 2m 3h 4d 5w 6M 7y` (eine Sekunde, zwei Minuten, drei Stunden, vier Tage, fünf Wochen, sechs Monate, sieben Jahre) im Verhältnis zur aktuellen Serverzeit, Verwendung  `-` für negativen Offset

### savedquery {#savedquery}

Diese Prognose umfasst alle Vorhersagen einer beständigen Abfrage Builder-Abfrage in die aktuelle Abfrage als Untergruppenvorhersage.

Dabei wird keine Extra-Abfrage ausgeführt, sondern die aktuellen Query erweitert.

Abfragen können programmgesteuert mit `QueryBuilder#storeQuery()` beibehalten werden. Das Format kann entweder eine mehrzeilige `String`-Eigenschaft oder ein `nt:file`-Knoten sein, der die Abfrage als Textdatei im Java-Eigenschaftenformat enthält.

Die Facetten-Extraktion für die Vorhersagen der gespeicherten Abfrage wird nicht unterstützt.

#### Eigenschaften {#properties-19}

* **`savedquery`** - Pfad zur gespeicherten Abfrage (`String` Eigenschaft oder  `nt:file` Node)

### similar {#similar}

Diese Prognose ist eine Ähnlichkeitssuche mit dem JCR XPath `rep:similar()`.

Die Filterung wird nicht unterstützt und die Extraktion von Facetten wird nicht unterstützt.

#### Eigenschaften {#properties-20}

* **`similar`** - absoluter Pfad zum Knoten, für den ähnliche Knoten gefunden werden
* **`local`** - einen relativen Pfad zu einem untergeordneten Knoten oder  `.` für den aktuellen Knoten (optional, Standard ist  `.`)

### tag {#tag}

Dadurch wird die Suche nach Inhalten, die mit einem oder mehreren Tags getaggt sind, durch Angabe von Tag-Titelpfaden vorhergesagt.

Es unterstützt die Extraktion von Facetten und stellt Behälter für jedes eindeutige Tag bereit, wobei der aktuelle Tag-Titelpfad verwendet wird.

#### Eigenschaften {#properties-21}

* **`tag`** - Tag-Titelpfad, nach dem gesucht werden soll, z. B.  `properties:orientation/landscape`
* **`N_value`** - Verwendung  `1_value`,  `2_value`... , um nach mehreren Tags zu suchen ( `OR` standardmäßig mit  `AND` if  `and=true`)
* **`property`** - Eigenschaft (oder relativer Pfad zur Eigenschaft), die Sie sich ansehen möchten (Standard  `cq:tags`)

### tagid {#tagid}

Dadurch wird die Suche nach Inhalten, die mit einem oder mehreren Tags getaggt sind, durch Angabe von Tag-IDs vorhergesagt.

Es unterstützt die Facetten-Extraktion und stellt Behälter für jedes eindeutige Tag bereit, wobei die aktuelle Tag-ID verwendet wird.

#### Eigenschaften {#properties-22}

* **`tagid`** - Tag-ID, nach der gesucht werden soll, z. B.  `properties:orientation/landscape`
* **`N_value`** - Verwendung  `1_value`,  `2_value`... , um nach mehreren Tag-IDs zu suchen ( `OR` standardmäßig mit  `AND` if  `and=true`)
* **`property`** - Eigenschaft (oder relativer Pfad zur Eigenschaft), die Sie sich ansehen möchten (Standard  `cq:tags`)

### tagsearch {#tagsearch}

Dadurch wird die Suche nach Inhalten, die mit einem oder mehreren Tags getaggt sind, durch Angabe von Suchbegriffen vorhergesagt. Dadurch wird zuerst nach Tags gesucht, die diese Suchbegriffe in ihren Titeln enthalten, und das Ergebnis dann auf die mit diesen markierten Elemente beschränkt.

Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#Properties-1}

* **`tagsearch`** - Suchbegriff, nach dem in Tag-Titeln gesucht werden soll
* **`property`** - zu berücksichtigende Eigenschaft (oder relativer Pfad zur Eigenschaft) (Standard  `cq:tags`)
* **`lang`** - nur in einem bestimmten lokalisierten Tag-Titel zu suchen (z.  `de`)
* **`all`** - boolescher Wert, um den gesamten Tag Volltext zu durchsuchen, d.h. alle Titel, Beschreibung usw. (hat Vorrang vor `lang`)

### Typ {#type}

Diese Prognose beschränkt die Ergebnisse auf einen bestimmten JCR-Knotentyp, sowohl primäre Node-Typen als auch Mixin-Typen. Dies findet auch Untertypen dieses Knotentyps. Zur effizienten Ausführung müssen Repository-Suchindizes die Knotentypen enthalten.

Es unterstützt die Extraktion von Facetten und stellt Behälter für jeden eindeutigen Ergebnistyp bereit.

#### Eigenschaften {#Properties-2}

* **`type`** - Node-Typ oder Mixin-Name, nach dem zum Beispiel gesucht werden soll  `cq:Page`
