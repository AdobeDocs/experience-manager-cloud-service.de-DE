---
title: Query Builder-Prädikatsreferenz
description: Prädikatreferenz für die Query Builder-API in AEM as a Cloud Service.
exl-id: 77118ef7-4d29-470d-9c4b-20537a408940
source-git-commit: 8c73805b6ed1b7a03c65b4d21a4252c1412a5742
workflow-type: tm+mt
source-wordcount: '2252'
ht-degree: 58%

---

# Query Builder-Prädikatsreferenz {#query-builder-predicate-reference}

## Allgemein {#general}

### root {#root}

Die Stammprädikatgruppe. Sie unterstützt alle Eigenschaften einer Gruppe und ermöglicht das Festlegen globaler Abfrageparameter.

Der Name &quot;root&quot;wird in einer Abfrage nie verwendet; er ist implizit.

#### Eigenschaften {#properties-18}

* **`p.offset`** - Zahl, die den Anfang der Ergebnisseite angibt, d. h. wie viele Elemente übersprungen werden sollen.
* **`p.limit`** - Zahl, die die Seitengröße angibt.
* **`p.guessTotal`** - empfohlen: Vermeidung der Berechnung der vollständigen Ergebnissumme, was kostspielig sein kann. Entweder eine Zahl, die die maximal zu zählende Summe angibt (z. B. 1000, eine Zahl, die Benutzern genügend Feedback zur groben Größe und exakten Zahlen für kleinere Ergebnisse gibt). Oder `true` nur bis zum erforderlichen Minimum zählen `p.offset` + `p.limit`.
* **`p.excerpt`** - wenn auf `true`, fügen Sie einen Volltextextextrakt in das Ergebnis ein.
* **`p.hits`** - (nur für das JSON-Servlet) Wählen Sie die Art und Weise aus, wie die Treffer als JSON geschrieben werden, mit diesen Standardtreffern (erweiterbar über den ResultHitWriter-Dienst).
   * **`simple`** - Minimale Elemente wie `path`, `title`, `lastmodified`, `excerpt` (falls festgelegt).
   * **`full`** - Sling JSON-Rendering des Knotens mit `jcr:path` gibt den Pfad des Treffers an. Standardmäßig werden nur die direkten Eigenschaften des Knotens aufgelistet und eine tiefere Struktur mit `p.nodedepth=N`, wobei 0 die gesamte, unendliche Unterstruktur bedeutet. Hinzufügen `p.acls=true` , um die JCR-Berechtigungen der aktuellen Sitzung für das angegebene Ergebniselement (Zuordnungen: `create` = `add_node`, `modify` = `set_property`, `delete` = `remove`).
   * **`selective`** - nur Eigenschaften, die in `p.properties`, das durch ein Leerzeichen getrennt ist (verwenden Sie `+` in URLs) Liste der relativen Pfade. Wenn der relative Pfad eine Tiefe hat `>1`, werden diese Eigenschaften als untergeordnete Objekte dargestellt. Die Sonderaktion `jcr:path` -Eigenschaft enthält den Pfad des Treffers.

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

Das ist `(1_property` ODER `2_property)`.

Das folgende Beispiel zeigt verschachtelte Gruppen:

```text
fulltext=Management
group.p.or=true
group.1_group.path=/content/wknd/ch/de
group.1_group.type=cq:Page
group.2_group.path=/content/dam/wknd
group.2_group.type=dam:Asset
```

Sucht nach dem Begriff **Management** innerhalb von Seiten in `/content/wknd/ch/de` oder in Assets `/content/dam/wknd`.

Das ist `fulltext AND ( (path AND type) OR (path AND type) )`. Solche ODER-Verknüpfungen benötigen aus Leistungsgründen gute Indizes.

#### Eigenschaften {#properties-6}

* **`p.or`** – Ist hierfür `true` festgelegt, muss nur ein Prädikat in der Gruppe übereinstimmen. Standardwert ist `false`, was bedeutet, dass alle übereinstimmen müssen
* **`p.not`** – Ist hierfür `true` festgelegt, wird die Gruppe nicht beachtet (standardmäßig `false`).
* **`<predicate>`** – fügt verschachtelte Prädikate hinzu.
* **`N_<predicate>`** – fügt mehrere verschachtelte Prädikate gleichzeitig hinzu, z. B. `1_property, 2_property, ...`.

### orderby {#orderby}

Dieses Prädikat ermöglicht die Sortierung der Ergebnisse. Wenn die Sortierung durch mehrere Eigenschaften erforderlich ist, muss dieses Präfix mehrmals mit dem Zahlenpräfix hinzugefügt werden, z. B. `1_orderby=first`, `2_oderby=second`.

#### Eigenschaften {#properties-13}

* **`orderby`** – Entweder der JCR-Eigenschaftsname, angezeigt durch ein vorangestelltes „@“, z. B. `@jcr:lastModified` bzw. `@jcr:content/jcr:title`, oder ein anderes Prädikat in der Abfrage, z. B. `2_property`, nach dem sortiert werden soll.
* **`sort`** – Sortierrichtung, entweder `desc` für absteigend oder `asc` für aufsteigend (Standard).
* **`case`** - wenn auf `ignore`wird bei der Sortierung nicht zwischen Groß- und Kleinschreibung unterschieden, d. h. `a` vor `B`; wenn leer oder ausgelassen, wird bei der Sortierung die Groß-/Kleinschreibung beachtet, d. h. `B` vor `a`

## Prädikate {#predicates}

### boolproperty {#boolproperty}

Dieses Prädikat stimmt mit den booleschen JCR-Eigenschaften überein. Akzeptiert nur die Werte `true` und `false`. Wenn der Wert `false`, stimmt sie überein, wenn die Eigenschaft den Wert aufweist. `false`, oder wenn es überhaupt nicht vorhanden ist. Diese Eigenschaft ist nützlich für die Überprüfung auf boolesche Flags, die nur bei Aktivierung festgelegt werden.

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

Nur-Filter-Prädikat; Suchindex kann nicht verwendet werden.

#### Eigenschaften {#properties-2}

* **`property1`** – Pfad zur Eigenschaft mit dem ersten Datum.
* **`property2`** – Pfad zur Eigenschaft mit dem zweiten Datum.
* **`operation`**
   * `=` für exakte Übereinstimmung (Standard)
   * `!=` für unterschiedliche Werte
   * `>` für `property1` größer als `property2`
   * `>=` für `property1` größer als oder gleich `property2`

### daterange {#daterange}

Dieses Prädikat gleicht JCR-Datumseigenschaften mit einem Datums-/Zeitintervall ab. Verwendet das ISO8601-Format für Datum und Uhrzeit (`YYYY-MM-DDTHH:mm:ss.SSSZ`) und erlaubt auch partielle Darstellungen, wie `YYYY-MM-DD`. Alternativ kann der Zeitstempel auch als POSIX-Zeit angegeben werden.

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

### excludepaths {#excludepaths}

Dieses Prädikat schließt Knoten aus dem Ergebnis aus, wenn ihr Pfad mit einem regulären Ausdruck übereinstimmt.

Nur-Filter-Prädikat; Suchindex kann nicht verwendet werden.

Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-4}

* **`excludepaths`** – Regulärer Ausdruck, der anhand von Ergebnispfaden ausgewertet wird, wobei übereinstimmende aus dem Ergebnis ausgeschlossen werden.

### fulltext {#fulltext}

Sucht nach Begriffen im Volltext-Index.

Filtern wird nicht unterstützt.

Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-5}

* **`fulltext`** - die Volltext-Suchbegriffe.
* **`relPath`** – Der relative Pfad, der in der Eigenschaft oder dem Teilknoten durchsucht werden soll. Diese Eigenschaft ist optional.

### hasPermission {#haspermission}

Dieses Prädikat beschränkt das Ergebnis auf Elemente, bei denen die aktuelle Sitzung die angegebenen [JCR-Privilegien](https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/2.0/16_Access_Control_Management.html#16.2.3%20Standard%20Privileges) aufweist.

Nur-Filter-Prädikat; Suchindex kann nicht verwendet werden. Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-7}

* **`hasPermission`** - alle kommagetrennten JCR-Berechtigungen, die die aktuelle Benutzersitzung für den betreffenden Knoten haben muss. Beispiel, `jcr:write`, `jcr:modifyAccessControl`

### language {#language}

Dieses Prädikat findet AEM-Seiten in einer bestimmten Sprache. Sie betrachtet sowohl die Seitenspracheigenschaft als auch den Seitenpfad, der häufig die Sprache oder das Gebietsschema in einer Site-Struktur der obersten Ebene enthält.

Nur-Filter-Prädikat; Suchindex kann nicht verwendet werden.

Es unterstützt die Facettenextraktion und stellt Buckets für jeden eindeutigen Sprach-Code zur Verfügung.

#### Eigenschaften {#properties-8}

* **`language`** – ISO-Sprach-Code, z. B. `de`.

### mainasset {#mainasset}

Dieses Prädikat prüft, ob ein Knoten ein DAM-Haupt-Asset und kein Unter-Asset ist. Es handelt sich im Grunde um jeden Knoten, der sich nicht in einem Unter-Asset-Knoten befindet. Es wird nicht auf die `dam:Asset` Knotentyp. Um diese Eigenschaft zu verwenden, legen Sie `mainasset=true` oder `mainasset=false`. Es gibt keine weiteren Eigenschaften.

Nur-Filter-Prädikat; Suchindex kann nicht verwendet werden.

Es unterstützt die Facettenextraktion und bietet zwei Buckets für Haupt- und Unter-Assets.

#### Eigenschaften {#properties-9}

* **`mainasset`** – Boolescher Wert, `true` für Haupt-Assets, `false` für Unter-Assets.

### memberOf {#memberof}

Dieses Prädikat sucht Objekte, die Mitglieder einer bestimmten [Sling-Ressourcensammlung](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/resource/collection/ResourceCollection.html) sind.

Nur-Filter-Prädikat; Suchindex kann nicht verwendet werden.

Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-10}

* **`memberOf`** – Pfad der Sling-Ressourcensammlung.

### nodename {#nodename}

Dieses Prädikat stimmt mit den JCR-Knotennamen überein.

Es unterstützt die Facettenextraktion und stellt Buckets für jeden eindeutigen Knotennamen (Dateinamen) bereit.

#### Eigenschaften {#properties-11}

* **`nodename`** – Knotennamenmuster, das Platzhalter ermöglicht: `*` = beliebiges oder kein Zeichen, `?` = beliebiges Zeichen, `[abc]`= nur die Zeichen in den eckigen Klammern.

### notexpired {#notexpired}

Dieses Prädikat wertet Elemente aus, indem überprüft wird, ob eine JCR-Datumseigenschaft größer oder gleich der aktuellen Server-Zeit ist. Er kann verwendet werden, um eine `expiresAt` -Wert und begrenzt die Ergebnisse nur auf die Werte, die noch nicht abgelaufen sind (`notexpired=true`) oder die bereits abgelaufen sind (`notexpired=false`).

Filtern wird nicht unterstützt.

Unterstützt die Facettenextraktion auf die gleiche Weise wie das Prädikat [`daterange`](#daterange).

#### Eigenschaften {#properties-12}

* **`notexpired`** – Boolescher Wert, `true` für noch nicht abgelaufen (Datum in der Zukunft oder gleich), `false` für abgelaufen (Datum in der Vergangenheit) (erforderlich).
* **`property`** – Relativer Pfad zur zu überprüfenden `DATE`-Eigenschaft (erforderlich).

### path {#path}

Dieses Prädikat sucht innerhalb eines gegebenen Pfades.

Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-14}

* **`path`** - Definiert das Pfadmuster.
   * Je nach `exact` -Eigenschaft, entweder entspricht die gesamte Unterstruktur (wie angehängt) `//*` in xpath, beachten Sie jedoch, dass es nicht den Basispfad enthält) oder nur ein exakter Pfad übereinstimmt, der Platzhalterzeichen (`*`).
      * Standardwert ist `true`.
&lt;!— * Wenn die `self`-Eigenschaft festgelegt ist, wird die gesamte Unterstruktur einschließlich des Basisknotens durchsucht.—>
* **`exact`** - wenn `exact` is `true`muss der genaue Pfad übereinstimmen, kann jedoch einfache Platzhalter enthalten (`*`), die mit Namen übereinstimmen, jedoch nicht `/`, wenn dies `false` (Standard) alle untergeordneten Elemente sind eingeschlossen (optional).
* **`flat`** - durchsucht nur die direkten untergeordneten Elemente (wie &quot;anhängen&quot;) `/*` in xpath (nur verwendet, wenn `exact` ist nicht wahr, optional).
* **`self`** – Durchsucht den Teilbaum, aber bezieht den als Pfad angegebenen Basisknoten mit ein (keine Platzhalter).
   * *Wichtiger Hinweis*: Ein Problem wurde mit `self` -Eigenschaft in der aktuellen Implementierung von Query Builder verwendet und in Abfragen verwendet, führt dies möglicherweise nicht zu korrekten Suchergebnissen. Ändern der aktuellen Implementierung von `self` -Eigenschaft ist auch nicht möglich, da sie die bestehenden Anwendungen beschädigen kann, die darauf angewiesen sind. Aufgrund dieser Funktion `self` -Eigenschaft ist nun veraltet. Es wird empfohlen, die Verwendung zu vermeiden.

### property {#property}

Dieses Prädikat sucht nach JCR-Eigenschaften und ihren Werten.

Es unterstützt die Facettenextraktion und stellt für jeden eindeutigen Eigenschaftswert in den Ergebnissen einen Bucket zur Verfügung.

#### Eigenschaften {#properties-15}

* **`property`** – Relativer Pfad der Eigenschaft, z. B. `jcr:title`..
* **`value`** - Wert, für den die Eigenschaft überprüft werden soll; folgt dem JCR-Eigenschaftstyp auf Zeichenfolgenkonvertierungen.
* **`N_value`** - Anwendung `1_value`, `2_value`, um zu überprüfen, ob mehrere Werte vorliegen (kombiniert mit `OR` standardmäßig mit `AND` if `and=true`).
* **`and`** – Legen Sie hierfür `true` fest, um mehrere Werte (`N_value`) mit `AND` zu kombinieren.
* **`operation`**
   * `equals` für exakte Übereinstimmung (Standard).
   * `unequals` für unterschiedliche Werte.
   * `like` für die Verwendung der `jcr:like` xpath-Funktion (optional).
   * `not` für keine Übereinstimmung (z. B. `not(@prop)` in xpath wird der Wertparameter ignoriert).
   * `exists` zur Überprüfung des Vorhandenseins.
      * `true` Eigenschaft muss vorhanden sein.
      * `false` ist dasselbe wie `not` und ist der Standard.
* **`depth`** - Anzahl der Platzhalterebenen, unter denen die Eigenschaft/der relative Pfad vorhanden sein kann (z. B. `property=size depth=2` checks `node/size`, `node/*/size`, und `node/*/*/size`).

### rangeproperty {#rangeproperty}

Dieses Prädikat ordnet eine JCR-Eigenschaft einem Intervall zu. Dies gilt für Eigenschaften mit linearen Typen wie `LONG`, `DOUBLE`, und `DECIMAL`. Für `DATE`, siehe [`daterange`](#daterange) -Prädikat mit optimierter Datumsformateingabe.

Sie können eine untere Grenze, eine obere Grenze oder beide definieren. Der Vorgang (z. B. kleiner oder kleiner als oder gleich) kann auch einzeln für die untere und obere Grenze angegeben werden.

Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#properties-16}

* **`property`** – Relativer Pfad zur Eigenschaft
* **`lowerBound`** – Untergrenze zur Prüfung der Eigenschaft
* **`lowerOperation`** – `>` (Standard) oder `>=`, gilt für `lowerValue`.
* **`upperBound`** – Obergrenze zur Prüfung der Eigenschaft
* **`upperOperation`** – `<` (Standard) oder `<=`, gilt für `lowerValue`.
* **`decimal`** – `true`, wenn die überprüfte Eigenschaft vom Typ „DECIMAL“ ist.

### relativedaterange {#relativedaterange}

Dieses Prädikat gleicht `JCR DATE`-Eigenschaften anhand von Zeit-Offsets, die relativ zur aktuellen Server-Zeit sind, mit einem Datums-/Zeitintervall ab. Sie können `lowerBound` und `upperBound` entweder anhand eines Millisekundenwerts oder der Bugzilla-Syntax `1s 2m 3h 4d 5w 6M 7y` (eine Sekunde, zwei Minuten, drei Stunden, vier Tage, fünf Wochen, sechs Monate, sieben Jahre) angeben. Mit dem Präfix `-` geben Sie einen negativen Offset vor der aktuellen Zeit an. Wenn Sie nur `lowerBound` oder `upperBound`, die andere Standardeinstellung ist `0`, die die aktuelle Zeit darstellt.

Beispiel:

* `upperBound=1h` (und keine `lowerBound`) wählt alles in der nächsten Stunde aus.
* `lowerBound=-1d` (und keine `upperBound`) wählt alles in den letzten 24 Stunden aus.
* `lowerBound=-6M` (und keine `upperBound=-3M`) wählt alles in den letzten 3 bis 6 Monaten aus.
* `lowerBound=-1500` und `upperBound=5500` wählt alles aus, was im Zeitraum zwischen einschließlich 1500 Millisekunden in der Vergangenheit und einschließlich 5500 Millisekunden in der Zukunft liegt.
* `lowerBound=1d` und `upperBound=2d` wählt alles am übernächsten Tag aus.

Es werden keine Schaltjahre berücksichtigt und alle Monate sind 30 Tage.

Filtern wird nicht unterstützt.

Unterstützt die Facettenextraktion auf die gleiche Weise wie das Prädikat [`daterange`](#daterange).

#### Eigenschaften {#properties-17}

* **`upperBound`** – Obere Datumsgrenze in Millisekunden oder `1s 2m 3h 4d 5w 6M 7y` (eine Sekunde, zwei Minuten, drei Stunden, vier Tage, fünf Wochen, sechs Monate, sieben Jahre) relativ zur aktuellen Server-Zeit. Verwenden Sie `-` für einen negativen Offset.
* **`lowerBound`** – Untere Datumsgrenze in Millisekunden oder `1s 2m 3h 4d 5w 6M 7y` (eine Sekunde, zwei Minuten, drei Stunden, vier Tage, fünf Wochen, sechs Monate, sieben Jahre) relativ zur aktuellen Server-Zeit. Verwenden Sie `-` für einen negativen Offset.

### savedquery {#savedquery}

Dieses Prädikat fügt alle Eigenschaften einer beständigen Query Builder-Abfrage der aktuellen Abfrage als Untergruppen-Prädikat hinzu.

Es wird keine zusätzliche Abfrage ausgeführt, sondern die aktuelle Abfrage erweitert.

Abfragen können programmgesteuert anhand von `QueryBuilder#storeQuery()` beibehalten werden. Das Format kann entweder eine mehrzeilige sein `String` -Eigenschaft oder `nt:file` -Knoten, der die Abfrage als Textdatei im Java™-Eigenschaftenformat enthält.

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

Dieses Prädikat sucht nach Inhalten mit Tags, indem Keywords angegeben werden. Er sucht zunächst nach Tags, die diese Keywords in ihrem Titel enthalten, beschränkt dann das Ergebnis auf Elemente, die mit diesen Keywords getaggt sind.

Facettenextraktion wird nicht unterstützt.

#### Eigenschaften {#Properties-1}

* **`tagsearch`** – Keyword, nach dem in Tag-Titeln gesucht werden soll
* **`property`** – Eigenschaft (bzw. relativer Pfad zur Eigenschaft), die berücksichtigt werden soll (Standard: `cq:tags`).
* **`lang`**: Zum Suchen in einem bestimmten lokalisierten Tag-Titel (z. B. `de`).
* **`all`** - Boolescher Wert, um den gesamten Tag-Volltext zu durchsuchen, d. h. alle Titel, Beschreibungen usw. (hat Vorrang vor `lang`)

### Typ {#type}

Diese Eigenschaft beschränkt Ergebnisse auf einen bestimmten JCR-Knotentyp, sowohl primäre Knotentypen als auch `mixin` Typen. Es findet auch Untertypen dieses Knotentyps. Die Indizes der Repository-Suche müssen die Knotentypen abdecken, um eine effiziente Ausführung zu gewährleisten.

Es unterstützt die Facettenextraktion und stellt für jeden eindeutigen Typ in den Ergebnissen einen Bucket zur Verfügung.

#### Eigenschaften {#Properties-2}

* **`type`** - Knotentyp oder `mixin` Name, nach dem gesucht werden soll, beispielsweise `cq:Page`
