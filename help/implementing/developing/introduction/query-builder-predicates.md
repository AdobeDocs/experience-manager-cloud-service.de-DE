---
title: Query Builder-Prädikatsreferenz
description: Prädikatsreferenz für die Query Builder-API.
exl-id: 77118ef7-4d29-470d-9c4b-20537a408940
source-git-commit: a446efacb91f1a620d227b9413761dd857089c96
workflow-type: tm+mt
source-wordcount: '2219'
ht-degree: 99%

---

# Query Builder-Prädikatsreferenz {#query-builder-predicate-reference}

## Allgemein {#general}

### root {#root}

Das ist die Prädikatsgruppe „root“. Sie unterstützt alle Eigenschaften einer Gruppe und ermöglicht das Festlegen globaler Abfrageparameter.

Der Name „root“ wird in Abfragen nie verwendet, er ist impliziert.

#### Eigenschaften {#properties-18}

* **`p.offset`** – Zahl, die den Anfang der Ergebnisseite anzeigt, d. h. wie viele Elemente übersprungen werden sollen.
* **`p.limit`** – Zahl, die die Seitengröße anzeigt.
* **`p.guessTotal`** – Empfohlen: Vermeiden Sie die Berechnung des vollständigen Ergebnisses, da dies aufwendig sein kann. Entweder ein Maximalwert, zu dem gezählt werden soll (z. B. 1000, eine Zahl, die Benutzern ausreichendes Feedback zur groben Größe und exakte Zahlen bei kleineren Ergebnissen liefert) oder `true`, um nur bis zum kleinsten notwendigen `p.offset` zu zählen + `p.limit`.
* **`p.excerpt`** – Ist hierfür `true` festgelegt, wird dem Ergebnis ein Volltextauszug hinzugefügt.
* **`p.hits`** – (nur für das JSON-Servlet) Legt fest, wie Treffer als JSON geschrieben werden. Folgende Standardmethoden stehen zur Auswahl (erweiterbar über den Service „ResultHitWriter“):
   * **`simple`** – Minimale Elemente wie `path`, `title`, `lastmodified`, `excerpt` (falls festgelegt).
   * **`full`** – Sling-JSON-Rendering des Knotens, wobei `jcr:path` den Pfad des Treffers anzeigt: Standardmäßig werden nur die direkten Eigenschaften des Knotens aufgeführt, weiter unten befindliche Teilbäume werden mit `p.nodedepth=N` eingeschlossen, wobei 0 den vollständigen Teilbaum bedeutet. Fügen Sie `p.acls=true` hinzu, um die JCR-Berechtigungen der aktuellen Sitzung für das jeweilige Ergebniselement einzuschließen (Zuordnungen: `create` = `add_node`, `modify` = `set_property`, `delete` = `remove`).
   * **`selective`** – Nur in `p.properties` angegebene Eigenschaften. Dabei handelt es sich um eine mit Leerzeichen (verwenden Sie `+` in URLs) getrennte Liste relativer Pfade. Wenn der relative Pfad eine Tiefe `>1` aufweist, werden sie als untergeordnete Elemente angezeigt. Die spezielle Eigenschaft `jcr:path` umfasst den Pfad des Treffers.

### group {#group}

Dieses Prädikat ermöglicht die Erstellung verschachtelter Bedingungen. Gruppen können verschachtelte Gruppen enthalten. Alles in einer Query Builder-Abfrage gehört zu einer root-Gruppe, die auch `p.or`- und `p.not`-Parameter aufweisen kann.

Das folgende Beispiel zeigt, wie eine von zwei Eigenschaften mit einem Wert abgeglichen wird:

```text
group.p.or=true
group.1_property=jcr:title
group.1_property.value=My Page
group.2_property=navTitle
group.2_property.value=My Page
```

Dies ist konzeptionell `(1_property` ODER `2_property)`.

Das folgende Beispiel zeigt verschachtelte Gruppen:

```text
fulltext=Management
group.p.or=true
group.1_group.path=/content/wknd/ch/de
group.1_group.type=cq:Page
group.2_group.path=/content/dam/wknd
group.2_group.type=dam:Asset
```

Hierbei wird nach dem Begriff **Management** innerhalb von Seiten in `/content/wknd/ch/de` oder in Assets in `/content/dam/wknd` gesucht.

Dies ist konzeptionell `fulltext AND ( (path AND type) OR (path AND type) )`. Beachten Sie, dass solche ODER-Verknüpfungen aus Leistungsgründen gute Indizes benötigen.

#### Eigenschaften {#properties-6}

* **`p.or`** – Ist hierfür `true` festgelegt, muss nur ein Prädikat in der Gruppe übereinstimmen. Standardmäßig ist `false` festgelegt, was bedeutet, dass alle übereinstimmen müssen.
* **`p.not`** – Ist hierfür `true` festgelegt, wird die Gruppe nicht beachtet (standardmäßig `false`).
* **`<predicate>`** – fügt verschachtelte Prädikate hinzu.
* **`N_<predicate>`** – fügt mehrere verschachtelte Prädikate gleichzeitig hinzu, z. B. `1_property, 2_property, ...`.

### orderby {#orderby}

Dieses Prädikat ermöglicht die Sortierung der Ergebnisse. Wenn nach mehreren Eigenschaften geordnet werden muss, muss dieses Prädikat anhand des Präfix mehrfach hinzugefügt werden, z. B. `1_orderby=first`, `2_oderby=second`.

#### Eigenschaften {#properties-13}

* **`orderby`** – Entweder der JCR-Eigenschaftsname, angezeigt durch ein vorangestelltes „@“, z. B. `@jcr:lastModified` bzw. `@jcr:content/jcr:title`, oder ein anderes Prädikat in der Abfrage, z. B. `2_property`, nach dem sortiert werden soll.
* **`sort`** – Sortierrichtung, entweder `desc` für absteigend oder `asc` für aufsteigend (Standard).
* **`case`** – Wird hierfür `ignore` festgelegt, wird die Groß-/Kleinschreibung nicht beachtet, `a` kommt also vor `B`. Wird dies leer- oder ausgelassen, wird bei der Sortierung die Groß-/Kleinschreibung beachtet, `B` kommt also vor `a`.

## Prädikate {#predicates}

### boolproperty {#boolproperty}

Dieses Prädikat stimmt mit den booleschen JCR-Eigenschaften überein. Akzeptiert nur die Werte `true` und `false`. Im Fall von `false` besteht eine Übereinstimmung, falls die Eigenschaft über den Wert `false` verfügt oder überhaupt nicht vorhanden ist. Dies kann für die Prüfung auf boolesche Flags nützlich sein, die nur festgelegt werden, wenn sie aktiviert sind.

Der übernommene Parameter `operation` hat keine Bedeutung.

Dieses Prädikat unterstützt die Facettenextraktion und liefert Buckets für jeden `true`- oder `false`-Wert, aber nur für vorhandene Eigenschaften.

#### Eigenschaften {#properties}

* **`boolproperty`** – relativer Pfad der Eigenschaft, z. B. `myFeatureEnabled` oder `jcr:content/myFeatureEnabled`.
* **`value`** – Wert, auf den die Eigenschaft geprüft wird, `true` oder `false`.

### contentfragment {#contentfragment}

Dieses Prädikat schränkt das Ergebnis auf Inhaltsfragmente ein.

* Filtern wird nicht unterstützt.
* Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-1}

* **`contentfragment`** – Kann mit jedem Wert verwendet werden, um auf Inhaltsfragmente zu prüfen.

### `dateComparison` {#datecomparison}

Dieses Prädikat vergleicht zwei JCR-Datumseigenschaften miteinander. Kann testen, ob sie gleich, ungleich, größer oder größer-oder-gleich sind.

Dies ist ein reines Filterprädikat und kann keine Suchindizes nutzen.

#### Eigenschaften {#properties-2}

* **`property1`** – Pfad zur Eigenschaft mit dem ersten Datum.
* **`property2`** – Pfad zur Eigenschaft mit dem zweiten Datum.
* **`operation`**
   * `=` für exakte Übereinstimmung (Standard)
   * `!=` für unterschiedliche Werte
   * `>` für `property1` größer als `property2`
   * `>=` für `property1` größer als oder gleich `property2`

### daterange {#daterange}

Dieses Prädikat gleicht JCR-Datumseigenschaften mit einem Datums-/Zeitintervall ab. Hierbei wird das ISO8601-Format für Daten und Uhrzeiten (`YYYY-MM-DDTHH:mm:ss.SSSZ`) verwendet, wobei auch Teildarstellungen möglich sind, z. B. `YYYY-MM-DD`. Alternativ kann der Zeitstempel auch als POSIX-Zeit angegeben werden.

Sie können nach allen Elementen zwischen zwei Zeitstempeln suchen, nach allem, was neuer oder älter als ein jeweiliges Datum ist, und aus inklusiven oder offenen Intervallen auswählen.

Es unterstützt die Facettenextraktion und stellt die Buckets `today`, `this week`, `this month`, `last 3 months`, `this year`, `last year` und `earlier than last year` bereit.

Filtern wird nicht unterstützt.

#### Eigenschaften {#properties-3}

* **`property`** – Relativer Pfad zu einer `DATE`-Eigenschaft, z. B. `jcr:lastModified`.
* **`lowerBound`** – Untere Datumsgrenze, auf welche die Eigenschaft überprüft werden soll, z. B. `2014-10-01`.
* **`lowerOperation`** – `>` (neuer) oder `>=` (gleich alt oder neuer), gilt für `lowerBound`. Standard: `>`
* **`upperBound`** – Obere Datumsgrenze, auf welche die Eigenschaft überprüft werden soll, z. B. `2014-10-01T12:15:00`.
* **`upperOperation`** – `<` (älter) oder `<=` (gleich alt oder älter), gilt für `upperBound`. Standard: `<`
* **`timeZone`** – Kennung der Zeitzone, die verwendet werden soll, wenn keine ISO-8601-Datumszeichenfolge angegeben wird. Der Standardwert ist die standardmäßige Zeitzone des Systems.

### excludepaths  {#excludepaths}

Dieses Prädikat schließt Knoten aus dem Ergebnis aus, wenn ihr Pfad mit einem regulären Ausdruck übereinstimmt.

Dies ist ein reines Filterprädikat und kann keine Suchindizes nutzen.

Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-4}

* **`excludepaths`** – Regulärer Ausdruck, der anhand von Ergebnispfaden ausgewertet wird, wobei übereinstimmende aus dem Ergebnis ausgeschlossen werden.

### fulltext {#fulltext}

Dieses Prädikat sucht nach Ausdrücken im Volltextindex.

Filtern wird nicht unterstützt.

Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-5}

* **`fulltext`** – Die Begriffe für die Volltextsuche.
* **`relPath`** – Der relative Pfad, der in der Eigenschaft oder dem Teilknoten durchsucht werden soll. Diese Eigenschaft ist optional.

### hasPermission {#haspermission}

Dieses Prädikat beschränkt das Ergebnis auf Elemente, bei denen die aktuelle Sitzung die angegebenen [JCR-Privilegien](https://docs.adobe.com/content/docs/en/spec/jcr/2.0/16_Access_Control_Management.html#16.2.3%20Standard%20Privileges) aufweist.

Dies ist ein reines Filterprädikat und kann keine Suchindizes nutzen. Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-7}

* **`hasPermission`** – Kommagetrennte JCR-Berechtigungen, die die aktuelle Benutzersitzung für den jeweiligen Knoten ALLE aufweisen muss, z. B. `jcr:write`, `jcr:modifyAccessControl`.

### language {#language}

Dieses Prädikat findet AEM-Seiten in einer bestimmten Sprache. Hierbei wird sowohl die Spracheigenschaft der Seite als auch der Seitenpfad betrachtet, der häufig die Sprache oder das Gebietsschema in einer Site-Struktur der höchsten Ebene enthält.

Dies ist ein reines Filterprädikat und kann keine Suchindizes nutzen.

Es unterstützt die Facettenextraktion und stellt Buckets für jeden eindeutigen Sprach-Code zur Verfügung.

#### Eigenschaften {#properties-8}

* **`language`** – ISO-Sprach-Code, z. B. `de`.

### mainasset {#mainasset}

Dieses Prädikat prüft, ob ein Knoten ein DAM-Haupt-Asset und kein Unter-Asset ist. Dies ist im Allgemeinen jeder Knoten, der sich nicht in einem Unter-Asset-Knoten befindet. Hierbei wird nicht auf den Knotentyp `dam:Asset` geprüft. Um dieses Prädikat zu verwenden, legen Sie einfach `mainasset=true` oder `mainasset=false` fest. Es gibt keine weiteren Eigenschaften.

Dies ist ein reines Filterprädikat und kann keine Suchindizes nutzen.

Es unterstützt die Facettenextraktion und bietet zwei Buckets für Haupt- und Unter-Assets.

#### Eigenschaften {#properties-9}

* **`mainasset`** – Boolescher Wert, `true` für Haupt-Assets, `false` für Unter-Assets.

### memberOf {#memberof}

Dieses Prädikat sucht Objekte, die Mitglieder einer bestimmten [Sling-Ressourcensammlung](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/org/apache/sling/resource/collection/ResourceCollection.html) sind.

Dies ist ein reines Filterprädikat und kann keine Suchindizes nutzen.

Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-10}

* **`memberOf`** – Pfad der Sling-Ressourcensammlung.

### nodename {#nodename}

Dieses Prädikat stimmt mit den JCR-Knotennamen überein.

Es unterstützt die Facettenextraktion und stellt Buckets für jeden eindeutigen Knotennamen (Dateinamen) bereit.

#### Eigenschaften {#properties-11}

* **`nodename`** – Knotennamenmuster, das Platzhalter ermöglicht: `*` = beliebiges oder kein Zeichen, `?` = beliebiges Zeichen, `[abc]`= nur die Zeichen in den eckigen Klammern.

### notexpired {#notexpired}

Dieses Prädikat wertet Elemente aus, indem überprüft wird, ob eine JCR-Datumseigenschaft größer oder gleich der aktuellen Server-Zeit ist. Dies kann verwendet werden, um einen `expiresAt`-Wert zu überprüfen und die Ergebnisse auf diejenigen zu beschränken, die noch nicht abgelaufen sind (`notexpired=true`) oder die bereits abgelaufen sind (`notexpired=false`).

Filtern wird nicht unterstützt.

Unterstützt die Facettenextraktion auf die gleiche Weise wie das Prädikat [`daterange`](#daterange).

#### Eigenschaften {#properties-12}

* **`notexpired`** – Boolescher Wert, `true` für noch nicht abgelaufen (Datum in der Zukunft oder gleich), `false` für abgelaufen (Datum in der Vergangenheit) (erforderlich).
* **`property`** – Relativer Pfad zur zu überprüfenden `DATE`-Eigenschaft (erforderlich).

### path {#path}

Dieses Prädikat sucht innerhalb eines gegebenen Pfades.

Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-14}

* **`path`** – Dies definiert das Pfadmuster.
   * Hängt von `exact` ab, entweder stimmt ein gesamter Teilbaum überein (wie wenn in xpath `//*` angehängt wird, wobei dabei der Basispfad nicht mit eingeschlossen wird) oder nur ein exakter Pfad stimmt überein, der Platzhalter (`*`) enthalten kann.
      * Standardwert ist `true`
   * Ist die Eigenschaft `self` festgelegt, wird der gesamte Teilbaum einschließlich des Basisknotens durchsucht.
* **`exact`** – Wenn `exact` `true` ist, muss der exakte Pfad übereinstimmen, darf aber bestimmte einfache Platzhalter (`*`) enthalten, die Namen entsprechen, aber nicht `/`. Wenn die Option `false` ist (Standard), werden alle untergeordneten Elemente berücksichtigt (optional).
* **`flat`** – Durchsucht nur die direkt untergeordneten Elemente (wie wenn in xpath `/*` angehängt wird). Wird nur verwendet, wenn `exact` nicht „true“ ist (optional).
* **`self`** – Durchsucht den Teilbaum, aber bezieht den als Pfad angegebenen Basisknoten mit ein (keine Platzhalter).

### property {#property}

Dieses Prädikat sucht nach JCR-Eigenschaften und ihren Werten.

Es unterstützt die Facettenextraktion und stellt für jeden eindeutigen Eigenschaftswert in den Ergebnissen einen Bucket zur Verfügung.

#### Eigenschaften {#properties-15}

* **`property`** – Relativer Pfad der Eigenschaft, z. B. `jcr:title`.
* **`value`** – Wert, auf den die Eigenschaft überprüft werden soll. Verarbeitet Umwandlungen anhand des JCR-Eigenschaftstyps als Zeichenfolgen.
* **`N_value`** – Verwenden Sie `1_value`, `2_value`, um auf mehrere Werte zu prüfen (standardmäßig kombiniert mit `OR`, mit `AND`, wenn `and=true`).
* **`and`** – Legen Sie hierfür `true` fest, um mehrere Werte (`N_value`) mit `AND` zu kombinieren.
* **`operation`**
   * `equals` für exakte Übereinstimmung (Standard)
   * `unequals` für unterschiedliche Werte
   * `like`, um die xpath-Funktion `jcr:like` zu verwenden (optional)
   * `not` wenn keine Übereinstimmung vorliegt (z. B. `not(@prop)` wenn keine Übereinstimmung vorliegt)
   * `exists` zur Überprüfung des Vorhandenseins
      * `true` Eigenschaft muss vorhanden sein
      * `false` ist dasselbe wie `not` und ist der Standard
* **`depth`** – Anzahl der Platzhalterebenen, unter denen die Eigenschaft bzw. der relative Pfad bestehen kann (z. B. prüft `property=size depth=2`, `node/size`, `node/*/size` und `node/*/*/size`).

### rangeproperty {#rangeproperty}

Dieses Prädikat ordnet eine JCR-Eigenschaft einem Intervall zu. Dies gilt für Eigenschaften mit linearen Typen wie `LONG`, `DOUBLE` und `DECIMAL`. Details zu `DATE` finden Sie im Abschnitt zum Prädikat [`daterange`](#daterange), das für Eingaben im Datumsformat optimiert wurde.

Sie können eine untere Grenze, eine obere Grenze oder beide definieren. Der Vorgang (z. B. „kleiner als“ oder „kleiner gleich“) kann auch einzeln für die untere und obere Grenze festgelegt werden.

Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-16}

* **`property`** – Relativer Pfad zur Eigenschaft
* **`lowerBound`** – Untergrenze zur Prüfung der Eigenschaft
* **`lowerOperation`** – `>` (Standard) oder `>=`, gilt für `lowerValue`.
* **`upperBound`** – Obergrenze zur Prüfung der Eigenschaft
* **`upperOperation`** – `<` (Standard) oder `<=`, gilt für `lowerValue`.
* **`decimal`** – `true`, wenn die überprüfte Eigenschaft vom Typ „DECIMAL“ ist.

### relativedaterange {#relativedaterange}

Dieses Prädikat gleicht `JCR DATE`-Eigenschaften anhand von Zeit-Offsets, die relativ zur aktuellen Server-Zeit sind, mit einem Datums-/Zeitintervall ab. Sie können `lowerBound` und `upperBound` entweder anhand eines Millisekundenwerts oder der Bugzilla-Syntax `1s 2m 3h 4d 5w 6M 7y` (eine Sekunde, zwei Minuten, drei Stunden, vier Tage, fünf Wochen, sechs Monate, sieben Jahre) angeben. Mit dem Präfix `-` geben Sie einen negativen Offset vor der aktuellen Zeit an. Wenn Sie nur `lowerBound` oder `upperBound` angeben, wird für die jeweils andere Grenze standardmäßig `0` festgelegt, was die aktuelle Zeit bedeutet.

Beispiel:

* `upperBound=1h` (und keine `lowerBound`) wählt alles in der nächsten Stunde aus.
* `lowerBound=-1d` (und keine `upperBound`) wählt alles in den letzten 24 Stunden aus.
* `lowerBound=-6M` (und keine `upperBound=-3M`) wählt alles in den letzten 3 bis 6 Monaten aus.
* `lowerBound=-1500` und `upperBound=5500` wählt alles aus, was im Zeitraum zwischen einschließlich 1500 Millisekunden in der Vergangenheit und einschließlich 5500 Millisekunden in der Zukunft liegt.
* `lowerBound=1d` und `upperBound=2d` wählt alles am übernächsten Tag aus.

Hinweis: Schaltjahre werden nicht berücksichtigt und alle Monate haben 30 Tage.

Filtern wird nicht unterstützt.

Unterstützt die Facettenextraktion auf die gleiche Weise wie das Prädikat [`daterange`](#daterange).

#### Eigenschaften {#properties-17}

* **`upperBound`** – Obere Datumsgrenze in Millisekunden oder `1s 2m 3h 4d 5w 6M 7y` (eine Sekunde, zwei Minuten, drei Stunden, vier Tage, fünf Wochen, sechs Monate, sieben Jahre) relativ zur aktuellen Server-Zeit. Verwenden Sie `-` für einen negativen Offset.
* **`lowerBound`** – Untere Datumsgrenze in Millisekunden oder `1s 2m 3h 4d 5w 6M 7y` (eine Sekunde, zwei Minuten, drei Stunden, vier Tage, fünf Wochen, sechs Monate, sieben Jahre) relativ zur aktuellen Server-Zeit. Verwenden Sie `-` für einen negativen Offset.

### savedquery {#savedquery}

Dieses Prädikat fügt alle Eigenschaften einer beständigen Query Builder-Abfrage der aktuellen Abfrage als Untergruppen-Prädikat hinzu.

Dabei wird keine zusätzliche Abfrage ausgeführt, sondern die aktuellen Abfrage erweitert.

Abfragen können programmgesteuert anhand von `QueryBuilder#storeQuery()` beibehalten werden. Das Format kann entweder eine `String`-Eigenschaft mit mehreren Zeilen oder ein `nt:file`-Knoten sein, der die Abfrage als Textdatei im Java-Eigenschaftsformat enthält.

Die Facettenextraktion wird für die Prädikate der gespeicherten Abfrage nicht unterstützt.

#### Eigenschaften {#properties-19}

* **`savedquery`** – Pfad zur gespeicherten Abfrage (`String`-Eigenschaft oder `nt:file`-Knoten).

### similar {#similar}

Dieses Prädikat ist eine Ähnlichkeitssuche unter Verwendung von `rep:similar()` von JCR XPath.

Filterung und Facettenextraktion werden nicht unterstützt.

#### Eigenschaften {#properties-20}

* **`similar`** – Absoluter Pfad zum Knoten, für den ähnliche Knoten gefunden werden sollen.
* **`local`** – Ein relativer Pfad zu einem untergeordneten Knoten oder `.` für den aktuellen Knoten (optional, der Standard lautet `.`).

### tag {#tag}

Dieses Prädikat sucht nach Inhalten mit Tags, indem Tag-Titelpfade angegeben werden.

Es unterstützt die Facettenextraktion und stellt Buckets für jedes einzigartige Tag bereit. Dazu wird jeweils der aktuelle Tag-Titelpfad verwendet.

#### Eigenschaften {#properties-21}

* **`tag`** – Tag-Titelpfad, nach dem gesucht werden soll, z. B. `properties:orientation/landscape`.
* **`N_value`** – Verwenden Sie `1_value`, `2_value`, um auf mehrere Tags zu prüfen (standardmäßig kombiniert mit `OR`, mit `AND`, wenn `and=true`).
* **`property`** – Eigenschaft (bzw. relativer Pfad zur Eigenschaft), die betrachtet werden soll (Standard: `cq:tags`).

### tagid {#tagid}

Dieses Prädikat sucht nach Inhalten mit Tags, indem Tag-IDs angegeben werden.

Es unterstützt die Facettenextraktion und stellt Buckets für jedes einzigartige Tag bereit. Dazu wird jeweils die aktuelle Tag-ID verwendet.

#### Eigenschaften {#properties-22}

* **`tagid`** – Tag-ID, nach der gesucht werden soll, z. B. `properties:orientation/landscape`.
* **`N_value`** – Verwenden Sie `1_value`, `2_value`, um auf mehrere Tag-IDs zu prüfen (standardmäßig kombiniert mit `OR`, mit `AND`, wenn `and=true`).
* **`property`** – Eigenschaft (bzw. relativer Pfad zur Eigenschaft), die betrachtet werden soll (Standard: `cq:tags`).

### tagsearch {#tagsearch}

Dieses Prädikat sucht nach Inhalten mit Tags, indem Keywords angegeben werden. Hierbei wird zunächst nach Tags gesucht, die diese Keywords in ihrem Titel enthalten, worauf das Ergebnis auf Elemente mit diesen Tags eingeschränkt wird.

Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#Properties-1}

* **`tagsearch`** – Keyword, nach dem in Tag-Titeln gesucht werden soll
* **`property`** – Eigenschaft (bzw. relativer Pfad zur Eigenschaft), die berücksichtigt werden soll (Standard: `cq:tags`).
* **`lang`** – Zum Suchen in einem bestimmten lokalisierten Tag-Titel (z. B. `de`).
* **`all`** – Boolescher Wert, um den gesamten Tag-Volltext zu durchsuchen, d. h. alle Titel, Beschreibung usw. (hat Priorität vor `lang`).

### type {#type}

Dieses Prädikat schränkt Ergebnisse auf einen bestimmten JCR-Knotentyp ein, sowohl auf primäre Knotentypen als auch auf Mixin-Typen. Hierbei werden auch Untertypen dieses Knotentyps gefunden. Zur effizienten Ausführung müssen Repository-Suchindizes die Knotentypen enthalten.

Es unterstützt die Facettenextraktion und stellt für jeden eindeutigen Typ in den Ergebnissen einen Bucket zur Verfügung.

#### Eigenschaften {#Properties-2}

* **`type`** – Knotentyp bzw. Mixin-Name, nach dem gesucht werden soll, z. B. `cq:Page`.
