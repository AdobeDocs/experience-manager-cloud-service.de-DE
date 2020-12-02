---
title: AEM-Tagging-Framework
description: Versehen Sie Inhalte mit Tags und nutzen Sie die AEM-Tagging-Infrastruktur. um es zu kategorisieren und zu organisieren.
translation-type: tm+mt
source-git-commit: 4bf023068aa69fb6b69c6f2443703ea2bbbf7d42
workflow-type: tm+mt
source-wordcount: '1567'
ht-degree: 25%

---


# Das AEM Tagging Framework {#aem-tagging-framework}

Tagging ermöglicht die Kategorisierung und Organisation von Inhalten. Tags können anhand eines Namespace und einer Taxonomie klassifiziert werden. Ausführliche Informationen zur Verwendung von Tags:

* Informationen zum Taggen von Inhalten als Inhaltsersteller finden Sie unter [Tags](/help/sites-cloud/authoring/features/tags.md) verwenden.
* Informationen zum Erstellen und Verwalten von Tags sowie zu den angewendeten Inhalts-Tags finden Sie unter Verwalten von Tags.

Dieser Artikel konzentriert sich auf das zugrunde liegende Framework, das Tagging in AEM unterstützt, und darauf, wie es als Entwickler genutzt werden kann.

## Einführung {#introduction}

Versehen Sie Inhalte mit Tags und nutzen Sie die AEM-Tagging-Infrastruktur wie folgt:

* Das Tag muss als Knoten des Typs [`cq:Tag`](#cq-tag-node-type) unter dem [taxonomy-Stammknoten vorhanden sein.](#taxonomy-root-node)
* Die Node `NodeType` des getaggten Inhalts muss das Mixin [`cq:Taggable`](#taggable-content-cq-taggable-mixin) enthalten.
* Das [`TagID`](#tagid) wird der Eigenschaft [`cq:tags`](#cq-tags-property) des Inhaltsknotens hinzugefügt und wird zu einem Knoten des Typs [`cq:Tag` aufgelöst.](#cq-tag-node-type)

## cq:Tag-Node-Typ {#cq-tag-node-type}

Die Deklaration eines Tags wird im Repository in einem Knoten des Typs `cq:Tag.` erfasst

* Ein Tag kann ein einfaches Wort sein (z. `sky`) oder stellen eine hierarchische Taxonomie dar (z.B. `fruit/apple`, d. h. sowohl die generische Frucht als auch der spezifischere Apfel).
* Tags werden durch ein eindeutiges `TagID` gekennzeichnet.
* Ein Tag weist optionale Metadaten auf, z. B. einen Titel, lokalisierte Titel und eine Beschreibung. Der Titel sollte in Benutzeroberflächen anstelle von `TagID` angezeigt werden, wenn vorhanden.

Das Tagging-Framework bietet außerdem die Möglichkeit, Autoren und Websitebesuchern die Verwendung bestimmter, vordefinierter Tags vorzugeben.

### Tag-Eigenschaften {#tag-characteristics}

* Der Knotentyp ist `cq:Tag`.
* Der Knotenname ist eine Komponente von [`TagID`.](#tagid)
* Das [`TagID`](#tagid) enthält immer einen [Namensraum.](#tag-namespace)
* Die Eigenschaft `jcr:title` (der Titel, der in der Benutzeroberfläche angezeigt werden soll) ist optional.
* Die Eigenschaft `jcr:description` ist optional.
* Wenn untergeordnete Nodes enthalten, wird als [Container-Tag bezeichnet.](#container-tags)
* Das Tag wird im Repository unter einem Basispfad namens [taxonomy-Stammknoten gespeichert.](#taxonomy-root-node)

### Tag-ID {#tagid}

Ein `TagID` identifiziert einen Pfad, der zu einem Tag-Knoten im Repository aufgelöst wird.

Normalerweise ist `TagID` ein Kurzbefehl `TagID`, der mit dem Namensraum beginnt, oder es kann sich um ein absolutes `TagID` handeln, beginnend mit dem [taxonomy-Stammknoten.](#taxonomy-root-node)

Wenn Inhalt mit Tags versehen ist und noch nicht vorhanden ist, wird die [`cq:tags`](#cq-tags-property)-Eigenschaft dem Knoten content hinzugefügt und der `TagID` wird dem Array-Wert der Eigenschaft `String` hinzugefügt.

Das `TagID` besteht aus einem [Namensraum](#tag-namespace) gefolgt vom lokalen `TagID`. [Container-Tags](#container-tags) weisen untergeordnete Tags auf, die eine hierarchische Reihenfolge in der Taxonomie darstellen. Unter-Tags können verwendet werden, um Tags zu referenzieren, die mit allen lokalen `TagID` übereinstimmen. Beispielsweise ist das Taggen von Inhalten mit `fruit` zulässig, auch wenn es sich um ein Container-Tag mit Unter-Tags wie `fruit/apple` und `fruit/banana` handelt.

### Stammknoten der Taxonomie {#taxonomy-root-node}

Der Stammknoten der Taxonomie ist der Basispfad für alle Tags im Repository. Der taxonomische Stammknoten muss *nicht* ein Knoten des Typs `cq:Tag` sein.

In AEM ist der Basispfad `/content/cq:tags` und der Stammknoten vom Typ `cq:Folder`.

### Tag-Namespace {#tag-namespace}

Namespaces ermöglichen das Gruppieren von Elementen. Der typischste Anwendungsfall besteht darin, einen Namensraum pro Site (z. B. öffentlich oder intern) oder pro größere Anwendung (z. B. Sites oder Assets) zu haben, aber Namensraum können für verschiedene andere Anforderungen verwendet werden. Namensraum werden in der Benutzeroberfläche verwendet, um nur die Teilmenge der Tags (d. h. Tags eines bestimmten Namensraums) anzuzeigen, die für den aktuellen Inhalt gilt.

Der Namespace des Tags ist die erste Ebene im Teilbaum der Taxonomie, der den Knoten direkt unterhalb des [Stammknotens der Taxonomie darstellt.](#taxonomy-root-node) Ein Namensraum ist eine Node des Typs  `cq:Tag` dessen übergeordneter Knoten kein  `cq:Tag` Node-Typ ist.

Alle Tags haben einen Namespace. Wenn kein Namensraum angegeben ist, wird das Tag dem standardmäßigen Namensraum zugeordnet, der `TagID` `default` lautet, d.h. `/content/cq:tags/default`.  Der Titel ist in diesen Fällen standardmäßig auf `Standard Tags`eingestellt.

### Container-Tags {#container-tags}

Container-Tags sind Knoten vom Typ `cq:Tag`, die eine beliebige Anzahl untergeordneter Knoten von beliebigen Typen enthalten. Das ermöglicht die Erweiterung des Tag-Modells mit benutzerdefinierten Metadaten.

Darüber hinaus dienen Container-Tags (oder Super-Tags) in einer Taxonomie als Unterzusammenfassung aller Unter-Tags: Zum Beispiel wird Inhalt, der mit `fruit/apple` getaggt ist, auch mit `fruit` getaggt, d. h. die Suche nach Inhalten, die gerade mit `fruit` getaggt wurden, findet auch den mit `fruit/apple` getaggten Inhalt.

### Auflösen von Tag-IDs {#resolving-tagids}

Wenn die Tag-ID einen Doppelpunkt (`:`) enthält, trennt der Doppelpunkt den Namensraum vom Tag oder der Untertaxonomie, die dann durch normale Schrägstriche (`/`) getrennt werden. Wenn in der Tag-ID kein Doppelpunkt vorkommt, ist der Standard-Namespace impliziert.

Der Standard- und der einzige Speicherort von Tags liegt unter `/content/cq:tags`.

Tags, die auf nicht vorhandene Pfade oder Pfade verweisen, die nicht auf einen `cq:Tag`-Knoten verweisen, werden als ungültig betrachtet und ignoriert.

Die folgende Tabelle zeigt einige Beispiele `TagID`s, ihre Elemente und wie `TagID` zu einem absoluten Pfad im Repository aufgelöst werden:

| `TagID` | Namespace | Lokale ID | Container-Tag(s) | Leaf-Tag | Repository Absoluter Tag-Pfad |
|---|---|---|---|---|---|
| `dam:fruit/apple/braeburn` | `dam` | `fruit/apple/braeburn` | `fruit`,`apple` | `braeburn` | `content/cq:tags/dam/fruit/apple/braeburn` |
| `color/red` | `default` | `color/red` | `color` | `red` | `/content/cq:tags/default/color/red` |
| `sky` | `default` | `sky` | (keine) | `sky` | `/content/cq:tags/default/sky` |
| `dam:` | `dam` | (keine) | (keine) | (keine) | `/content/cq:tags/dam` |
| `content/cq:tags/category/car` | `category` | `car` | `car` | `car` | `content/cq:tags/category/car` |

### Lokalisierung des Tag-Titels {#localization-of-tag-title}

Wenn das Tag die optionale Titelzeichenfolge `jcr:title` enthält, kann der Titel für die Anzeige durch Hinzufügen der Eigenschaft `jcr:title.<locale>` lokalisiert werden.

Weitere Informationen finden Sie unter:

* [Tags in verschiedenen Sprachen, ](tagging-applications.md#tags-in-different-languages) in denen die Verwendung der APIs als Entwickler beschrieben wird
* Verwalten von Tags in verschiedenen Sprachen, in denen die Verwendung der Tagging-Konsole als Administrator beschrieben wird

### Zugriffssteuerung {#access-control}

Tags bestehen als Knoten im Repository unter dem [Stammknoten der Taxonomie.](#taxonomy-root-node) Es kann erreicht werden, dass Autoren und Site-Besucher Tags in einem bestimmten Namensraum erstellen oder verweigern können, indem entsprechende ACLs im Repository festgelegt werden.

Das Verweigern von Leseberechtigungen für bestimmte Tags oder Namensraum steuert die Fähigkeit, Tags auf bestimmte Inhalte anzuwenden.

Eine typische Vorgehensweise umfasst Folgendes:

* Zulassen des Gruppen-/Rollenschreibzugriffs auf alle Namensraum (Hinzufügen/Ändern unter `/content/cq:tags`). `tag-administrators` Diese Gruppe enthält AEM standardmäßig.
* Gewähren von Lesezugriff für Benutzer/Autoren auf alle Namespaces, die sie lesen können müssen (meist alle).
* Benutzern/Autoren Schreibzugriff auf die Namensraum zu gewähren, in denen Tags von Benutzern/Autoren frei definiert werden können (`add_node` unter `/content/cq:tags/some_namespace`)

## Tag-barer Inhalt: cq:Taggable-Mixin {#taggable-content-cq-taggable-mixin}

Damit Anwendungsentwickler Tagging an einen Inhaltstyp anhängen können, muss die Registrierung des Knotens ([CND](https://jackrabbit.apache.org/node-type-notation.html)) das `cq:Taggable`-Mixin oder das `cq:OwnerTaggable`-Mixin enthalten.

Das Mixin `cq:OwnerTaggable`, der von `cq:Taggable` übernimmt, soll anzeigen, dass der Inhalt vom Besitzer/Autor klassifiziert werden kann. In AEM ist es nur ein Attribut des Knotens `cq:PageContent`. Das `cq:OwnerTaggable`-Mixin ist für das Tagging-Framework nicht erforderlich.

>[!NOTE]
>
>Es wird empfohlen, nur Tags auf dem Knoten der obersten Ebene eines aggregierten Inhaltselements (oder auf dessen Knoten `jcr:content`) zu aktivieren. Beispiele dafür sind:
>
>* Seiten (`cq:Page`), auf denen der Knoten `jcr:content`vom Typ `cq:PageContent` ist, der das Mixin `cq:Taggable` enthält.
>* Assets (`cq:Asset`), bei denen der `jcr:content/metadata`-Knoten immer über das `cq:Taggable`-mixin verfügt.


### Knotentypnotation (CND) {#node-type-notation-cnd}

Knotentypdefinitionen sind im Repository als CND-Dateien vorhanden. Die CND-Notation ist als Teil der [JCR-Dokumentation definiert.](https://jackrabbit.apache.org/node-type-notation.html).

Die wichtigsten Definitionen für die Knotentypen in AEM sind wie folgt:

```xml
[cq:Tag] > mix:title, nt:base
    orderable
    - * (undefined) multiple
    - * (undefined)
    + * (nt:base) = cq:Tag version

[cq:Taggable]
    mixin
    - cq:tags (string) multiple

[cq:OwnerTaggable] > cq:Taggable
    mixin
```

## cq:tags-Eigenschaft {#cq-tags-property}

Die `cq:tags`-Eigenschaft ist ein `String`-Array, mit dem ein oder mehrere `TagID`s gespeichert werden, wenn sie von Autoren oder Site-Besuchern auf Inhalte angewendet werden. Die Eigenschaft hat nur dann eine Bedeutung, wenn sie einem Knoten hinzugefügt wird, der mit dem Mixin [`cq:Taggable`](#taggable-content-cq-taggable-mixin) definiert wird.

>[!NOTE]
>
>Um AEM Tagging-Funktion zu nutzen, sollten benutzerdefinierte Anwendungen keine anderen Tag-Eigenschaften als `cq:tags` definieren.

## Verschieben und Zusammenführen von Tags {#moving-and-merging-tags}

Im Folgenden finden Sie eine Beschreibung der Auswirkungen, die im Repository auftreten, wenn Sie Tags mit der Tagging-Konsole verschieben oder zusammenführen.

Wenn Tag A unter `/content/cq:tags` verschoben oder in Tag B zusammengeführt wird:

* Tag A wird nicht gelöscht und erhält eine `cq:movedTo`-Eigenschaft.
   * `cq:movedTo` verweist auf Tag B.
   * Diese Eigenschaft bedeutet, dass Tag A verschoben oder in Tag B zusammengeführt wurde.
   * Durch Verschieben von Tag B wird diese Eigenschaft entsprechend aktualisiert.
   * Tag A wird daher ausgeblendet und nur im Repository aufbewahrt, um Tag-IDs in Inhaltsknoten aufzulösen, die auf Tag A verweisen.
   * Der Tag-Garbage Collector entfernt Tags wie Tag A, sobald keine Inhaltsknoten mehr auf sie zeigen.
   * Ein besonderer Wert für die `cq:movedTo`-Eigenschaft ist `nirvana`, der angewendet wird, wenn das Tag gelöscht wird, aber nicht aus dem Repository entfernt werden kann, da Untertags mit einem `cq:movedTo` vorhanden sind, die beibehalten werden müssen.

      >[!NOTE]
      >
      >Die `cq:movedTo`-Eigenschaft wird dem verschobenen oder zusammengeführten Tag nur hinzugefügt, wenn eine der folgenden Bedingungen erfüllt ist:
      >
      > 1. Das Tag wird im Inhalt verwendet (d. h. es enthält einen Verweis). ODER
      > 1. Das Tag enthält bereits verschobene untergeordnete Elemente.


* Tag B wird erstellt (bei einer Verschiebung) und erhält eine `cq:backlinks`-Eigenschaft.
   * `cq:backlinks` behält die Verweise in die andere Richtung, d. h. es behält eine Liste aller Tags bei, die zu Tag B verschoben oder mit ihm zusammengeführt wurden.
   * Dies ist vor allem erforderlich, um die `cq:movedTo`-Eigenschaften beim Verschieben/Zusammenführen/Löschen von Tag B oder bei der Aktivierung von Tag B auf dem neuesten Stand zu halten. In diesem Fall müssen auch alle Backlinks-Tags aktiviert werden.

      >[!NOTE]
      >
      >Die `cq:backlinks`-Eigenschaft wird dem verschobenen oder zusammengeführten Tag nur hinzugefügt, wenn eine der folgenden Bedingungen erfüllt ist:
      >
      > 1. Das Tag wird im Inhalt verwendet (d. h. es enthält einen Verweis). ODER
      > 1. Das Tag enthält bereits verschobene untergeordnete Elemente.


Das Lesen einer `cq:tags`-Eigenschaft eines Inhaltsknotens erfordert die folgende Auflösung:

1. Wenn unter `/content/cq:tags` keine Übereinstimmung vorhanden ist, wird kein Tag zurückgegeben.
1. Wenn das Tag eine `cq:movedTo`-Eigenschaft aufweist, steht danach die referenzierte Tag-ID.
   * Dieser Schritt wird so lange wiederholt, wie das angehängte Tag eine `cq:movedTo`-Eigenschaft aufweist.
1. Falls das angehängte Tag nicht über eine `cq:movedTo`-Eigenschaft verfügt, wird das Tag gelesen.

Um die Änderung zu veröffentlichen, wenn ein Tag verschoben oder zusammengeführt wurde, müssen der `cq:Tag`-Knoten und alle zugehörigen Backlinks repliziert werden. Dies erfolgt automatisch, wenn das Tag in der Tag-Verwaltungskonsole aktiviert wird.

Spätere Aktualisierungen der `cq:tags`-Eigenschaft der Seite bereinigen automatisch die alten Verweise. Dies wird ausgelöst, da die Auflösung eines verschobenen Tags über die API das Ziel-Tag zurückgibt und so die Ziel-Tag-ID bereitstellt.
