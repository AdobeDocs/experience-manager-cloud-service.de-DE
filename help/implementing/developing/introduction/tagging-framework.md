---
title: AEM-Tagging-Framework
description: Taggen Sie Inhalte und verwenden Sie die AEM Tagging-Infrastruktur, um sie zu kategorisieren und zu organisieren.
exl-id: 25418d44-aace-4e73-be1a-4b1902f40403
source-git-commit: 7260649eaab303ba5bab55ccbe02395dc8159949
workflow-type: tm+mt
source-wordcount: '1569'
ht-degree: 66%

---

# AEM-Tagging-Framework {#aem-tagging-framework}

Tagging ermöglicht die Kategorisierung und Organisation von Inhalten. Tags können anhand eines Namespace und einer Taxonomie klassifiziert werden. Ausführliche Informationen zur Verwendung von Tags:

* Informationen zum Taggen von Inhalten als Inhaltsersteller finden Sie unter [Verwenden von Tags](/help/sites-cloud/authoring/features/tags.md).
* Informationen zum Erstellen und Verwalten von Tags sowie dazu, auf welche Inhalts-Tags angewendet wurden, finden Sie unter Verwalten von Tags .

Dieser Artikel konzentriert sich auf das zugrunde liegende Framework, das Tagging in AEM unterstützt, und auf die Verwendung als Entwickler.

## Einführung {#introduction}

So taggen Sie Inhalte und verwenden die AEM Tagging-Infrastruktur :

* Das Tag muss unterhalb des [Stammknotens der Taxonomie](#taxonomy-root-node) als Knoten vom Typ [`cq:Tag`](#cq-tag-node-type) vorhanden sein.
* Der `NodeType` des mit Tags versehenen Inhaltsknotens muss das Mixin [`cq:Taggable`](#taggable-content-cq-taggable-mixin) beinhalten.
* Die [`TagID`](#tagid) wird der Eigenschaft [`cq:tags`](#cq-tags-property) des Inhaltsknotens hinzugefügt und ergibt einen Knoten vom Typ [`cq:Tag`.](#cq-tag-node-type)

## Knotentyp cq:Tag {#cq-tag-node-type}

Die Funktion eines Tags wird im Repository in einem Knoten vom Typ `cq:Tag.` erfasst

* Ein Tag kann ein einfaches Wort (z. B. `sky`) sein oder eine hierarchische Taxonomie (z. B. `fruit/apple`, womit sowohl die Frucht im Allgemeinen als auch der Apfel im Speziellen gemeint sind) darstellen.
* Tags werden anhand einer eindeutigen `TagID` identifiziert.
* Ein Tag verfügt über optionale Metainformationen wie einen Titel, lokalisierte Titel und eine Beschreibung. Der Titel sollte, falls vorhanden, auf Benutzeroberflächen anstelle der `TagID` angezeigt werden.

Das Tagging-Framework schränkt Autoren und Site-Besucher auch dazu ein, nur bestimmte vordefinierte Tags zu verwenden.

### Tag-Eigenschaften {#tag-characteristics}

* Der Knotentyp ist `cq:Tag`.
* Der Knotenname ist eine Komponente der [`TagID`.](#tagid)
* Die [`TagID`](#tagid) umfasst immer einen [Namespace](#tag-namespace).
* Die Eigenschaft `jcr:title` (der Titel, der in der Benutzeroberfläche angezeigt werden soll) ist optional.
* Die Eigenschaft `jcr:description` ist optional.
* Wird als [Container-Tag](#container-tags) bezeichnet, wenn untergeordnete Knoten enthalten sind.
* Das Tag wird im Repository unterhalb eines Basispfads gespeichert, der als [Stammknoten der Taxonomie](#taxonomy-root-node) bezeichnet wird.

### TagID (Tag-ID) {#tagid}

Eine `TagID` identifiziert einen Pfad, der einen Tag-Knoten im Repository ergibt.

Normalerweise ist die `TagID` eine kurze `TagID`, die mit dem Namespace beginnt. Sie kann auch eine absolute `TagID` sein, die mit dem [Stammknoten der Taxonomie](#taxonomy-root-node) beginnt.

Wenn Inhalte mit Tags versehen werden, aber noch nicht vorhanden sind, wird dem Inhaltsknoten die Eigenschaft [`cq:tags`](#cq-tags-property) und dem `String`-Array-Wert der Eigenschaft die `TagID` hinzugefügt.

Die `TagID` besteht aus einem [Namespace](#tag-namespace) gefolgt von der lokalen `TagID`. [Container-Tags](#container-tags) untergeordnete Tags aufweisen, die eine hierarchische Reihenfolge in der Taxonomie darstellen. Subtags können verwendet werden, um Tags zu referenzieren, die mit allen lokalen `TagID`. Beispiel: Tagging von Inhalten mit `fruit` ist erlaubt, auch wenn es sich um ein Container-Tag mit Untertags handelt, wie z. B. `fruit/apple` und `fruit/banana`.

### Stammknoten der Taxonomie {#taxonomy-root-node}

Der Stammknoten der Taxonomie ist der Basispfad für alle Tags im Repository. Der Stammknoten der Taxonomie darf *kein* Knoten vom Typ `cq:Tag` sein.

In AEM ist der Basispfad `/content/cq:tags` und der Stammknoten ist vom Typ `cq:Folder`.

### Tag-Namespace {#tag-namespace}

Mithilfe von Namespaces können Sie Elemente gruppieren. Der vorherrschende Anwendungsfall besteht darin, einen Namespace pro Website (z. B. öffentlich versus intern) oder pro größerer Anwendung (z. B. Sites oder Assets) zu verwenden. Namespaces können aber auch anderweitig eingesetzt werden. Namespaces werden in der Benutzeroberfläche verwendet, um nur die Untergruppe von Tags (d. h. Tags eines bestimmten Namespace) anzuzeigen, die für den aktuellen Inhalt gültig ist.

Der Namespace des Tags ist die erste Ebene im Teilbaum der Taxonomie, der den Knoten direkt unterhalb des [Stammknotens der Taxonomie darstellt.](#taxonomy-root-node) Ein Namespace ist ein Knoten vom Typ `cq:Tag`, dessen übergeordnetes Element nicht vom Knotentyp `cq:Tag` ist.

Alle Tags haben einen Namespace. Wenn kein Namespace angegeben ist, wird das Tag dem Standard-Namespace zugewiesen, der `TagID` `default`, d. h. `/content/cq:tags/default`. Der Titel ist in diesen Fällen standardmäßig auf `Standard Tags` eingestellt.

### Container-Tags {#container-tags}

Container-Tags sind Knoten vom Typ `cq:Tag`, die eine beliebige Anzahl untergeordneter Knoten von beliebigen Typen enthalten. Das ermöglicht die Erweiterung des Tag-Modells mit benutzerdefinierten Metadaten.

Darüber hinaus dienen Container-Tags (oder Super-Tags) in einer Taxonomie als Subsummierung aller Unter-Tags. Beispielsweise Inhalte, die mit `fruit/apple` wird als mit `fruit`, auch. Das heißt, nach Inhalten suchen, die mit `fruit` auch den Inhalt finden, mit dem `fruit/apple`.

### Auflösen von Tag-IDs {#resolving-tagids}

Wenn die Tag-ID einen Doppelpunkt (`:`), trennt der Doppelpunkt den Namespace vom Tag oder der Subtaxonomie, die dann durch normale Schrägstriche (`/`). Wenn in der Tag-ID kein Doppelpunkt vorkommt, ist der Standard-Namespace impliziert.

Der standardmäßige und einzige Speicherort von Tags befindet sich unter `/content/cq:tags`.

Tags, die auf nicht vorhandene Pfade oder auf Pfade verweisen, an deren Ende sich kein `cq:Tag`-Knoten befindet, werden als ungültig betrachtet und werden ignoriert.

Die folgende Tabelle zeigt einige `TagID`-Beispiele, ihre Elemente und wie die `TagID` einen absoluten Pfad im Repository ergibt:

| `TagID` | Namespace | Lokale ID | Container-Tags | Leaf-Tag | Absoluter Tag-Pfad im Repository |
|---|---|---|---|---|---|
| `dam:fruit/apple/braeburn` | `dam` | `fruit/apple/braeburn` | `fruit`,`apple` | `braeburn` | `content/cq:tags/dam/fruit/apple/braeburn` |
| `color/red` | `default` | `color/red` | `color` | `red` | `/content/cq:tags/default/color/red` |
| `sky` | `default` | `sky` | (keine) | `sky` | `/content/cq:tags/default/sky` |
| `dam:` | `dam` | (keine) | (keine) | (keins) | `/content/cq:tags/dam` |
| `content/cq:tags/category/car` | `category` | `car` | `car` | `car` | `content/cq:tags/category/car` |

### Lokalisierung des Tag-Titels {#localization-of-tag-title}

Wenn das Tag die optionale Titelzeichenfolge enthält (`jcr:title`), ist es möglich, den Titel zur Anzeige zu lokalisieren, indem die Eigenschaft `jcr:title.<locale>` hinzugefügt wird.

Weitere Informationen finden Sie unter folgenden Themen:

* [Tags in verschiedenen Sprachen](tagging-applications.md#tags-in-different-languages) die Verwendung der APIs als Entwickler beschreiben
* Verwalten von Tags in verschiedenen Sprachen, in denen die Verwendung der Tagging-Konsole als Administrator beschrieben wird

### Zugriffssteuerung {#access-control}

Tags bestehen als Knoten im Repository unter dem [Stammknoten der Taxonomie.](#taxonomy-root-node) Sie erlauben oder verweigern Autoren und Website-Besuchern die Erstellung von Tags in einem jeweiligen Namespace, indem Sie im Repository entsprechende ACLs festlegen.

Durch das Verweigern von Leseberechtigungen für bestimmte Tags oder Namespaces wird die Fähigkeit gesteuert, Tags auf bestimmte Inhalte anzuwenden.

Eine typische Vorgehensweise umfasst Folgendes:

* Gewähren von Schreibzugriff auf alle Namespaces für die Gruppe/Rolle `tag-administrators` (unter `/content/cq:tags` hinzufügen/ändern). Diese Gruppe enthält AEM standardmäßig.
* Gewähren von Lesezugriff für Benutzer/Autoren auf alle Namespaces, die sie lesen können müssen (meist alle).
* Gewähren von Schreibzugriff für Benutzer/Autoren auf die Namespaces, bei denen Tags durch Benutzer/Autoren frei definierbar sein müssen (`add_node` unter `/content/cq:tags/some_namespace`).

## Tag-barer Inhalt: cq:Taggable-Mixin {#taggable-content-cq-taggable-mixin}

Damit Anwendungsentwickler Tagging an einen Inhaltstyp anhängen können, muss die Registrierung des Knotens ([CND](https://jackrabbit.apache.org/jcr/node-type-notation.html)) muss Folgendes enthalten: `cq:Taggable` Mixin oder `cq:OwnerTaggable` Mixin.

Das Mixin `cq:OwnerTaggable`, das von `cq:Taggable` übernimmt, soll anzeigen, dass der Inhalt vom Besitzer/Autor klassifiziert werden kann. In AEM handelt es sich hierbei nur um ein Attribut des Knotens `cq:PageContent`. Das Mixin `cq:OwnerTaggable` wird vom Tagging-Framework nicht benötigt.

>[!NOTE]
>
>Es wird empfohlen, Tags nur auf dem Knoten der obersten Ebene eines aggregierten Inhaltselements (oder dessen `jcr:content`-Knoten) zu aktivieren. Beispiele dafür sind:
>
>* Seiten (`cq:Page`), deren Knoten `jcr:content` vom Typ `cq:PageContent` sind, der das Mixin `cq:Taggable` umfasst
>* Assets (`cq:Asset`), deren Knoten `jcr:content/metadata` immer das Mixin `cq:Taggable` umfassen

### Knotentypnotation (CND) {#node-type-notation-cnd}

Knotentypdefinitionen sind im Repository als CND-Dateien vorhanden. Die CND-Notation wird als Teil der [JCR-Dokumentation](https://jackrabbit.apache.org/jcr/node-type-notation.html).

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

## Eigenschaft cq:tags {#cq-tags-property}

Die Eigenschaft `cq:tags` ist ein `String`-Array, das zum Speichern mindestens einer `TagID` verwendet wird, wenn diese von Autoren oder Website-Besuchern auf Inhalte angewendet werden. Die Eigenschaft hat nur dann eine Bedeutung, wenn sie einem Knoten hinzugefügt wird, der mit dem Mixin [`cq:Taggable`](#taggable-content-cq-taggable-mixin) definiert wird.

>[!NOTE]
>
>Um AEM Tagging-Funktionen zu verwenden, sollten benutzerdefinierte entwickelte Anwendungen keine anderen Tag-Eigenschaften definieren als `cq:tags`.

## Verschieben und Zusammenführen von Tags {#moving-and-merging-tags}

Im Folgenden finden Sie eine Beschreibung der Auswirkungen, die im Repository auftreten, wenn Sie Tags mit der Tagging-Konsole verschieben oder zusammenführen.

Wenn ein Tag A verschoben oder mit Tag B unter `/content/cq:tags` zusammengeführt wird:

* Tag A wird nicht gelöscht und erhält eine `cq:movedTo`-Eigenschaft.
   * `cq:movedTo` verweist auf Tag B.
   * Diese Eigenschaft bedeutet, dass Tag A in Tag B verschoben oder zusammengeführt wurde.
   * Durch Verschieben von Tag B wird diese Eigenschaft entsprechend aktualisiert.
   * Tag A ist daher ausgeblendet und wird nur im Repository beibehalten, damit Tag-IDs in Inhaltsknoten, die auf Tag A verweisen, aufgelöst werden können.
   * Der Garbage Collector für Tags entfernt Tags wie Tag A, sobald keine Inhaltsknoten mehr darauf verweisen.
   * Ein spezieller Wert für die Eigenschaft `cq:movedTo` ist `nirvana`: Er wird angewendet, wenn das Tag gelöscht wird, aber nicht aus dem Repository entfernt werden kann, weil untergeordnete Tags mit `cq:movedTo` vorhanden sind, die nicht entfernt werden dürfen.

     >[!NOTE]
     >
     >Die `cq:movedTo`-Eigenschaft wird dem verschobenen oder zusammengeführten Tag nur hinzugefügt, wenn eine der folgenden Bedingungen erfüllt ist:
     >
     > 1. Das Tag wird im Inhalt verwendet (d. h. es hat einen Verweis). ODER
     > 1. Das Tag enthält bereits verschobene untergeordnete Elemente.
     >
* Tag B wird erstellt (wenn es eine Verschiebung gibt) und erhält eine `cq:backlinks` -Eigenschaft.
   * `cq:backlinks` behält die Verweise in die andere Richtung. Das heißt, es enthält eine Liste aller Tags, die in Tag B verschoben oder mit ihm zusammengeführt wurden.
   * Diese Funktion ist hauptsächlich erforderlich, um `cq:movedTo` -Eigenschaften aktualisiert werden, wenn Tag B verschoben/zusammengeführt/gelöscht oder Tag B aktiviert wird. In diesem Fall müssen auch alle Backlinks-Tags aktiviert werden.

     >[!NOTE]
     >
     >Die `cq:backlinks`-Eigenschaft wird dem verschobenen oder zusammengeführten Tag nur hinzugefügt, wenn eine der folgenden Bedingungen erfüllt ist:
     >
     > 1. Das Tag wird im Inhalt verwendet (d. h. es hat einen Verweis) oder
     > 1. Das Tag enthält bereits verschobene untergeordnete Elemente.

Das Lesen einer `cq:tags`-Eigenschaft eines Inhaltsknotens umfasst die folgende Auflösung:

1. Wenn unter `/content/cq:tags` keine Übereinstimmung verfügbar ist, wird kein Tag zurückgegeben.
1. Wenn das Tag eine `cq:movedTo`-Eigenschaft aufweist, steht danach die referenzierte Tag-ID.
   * Dieser Schritt wird so lange wiederholt, wie das angehängte Tag eine `cq:movedTo`-Eigenschaft aufweist.
1. Falls das angehängte Tag nicht über eine `cq:movedTo`-Eigenschaft verfügt, wird das Tag gelesen.

Um eine Änderung zu veröffentlichen, wenn ein Tag verschoben oder zusammengeführt wurde, müssen der Knoten `cq:Tag` und all seine Backlinks repliziert werden. Diese Replikation erfolgt automatisch, wenn das Tag in der Tag-Verwaltungskonsole aktiviert wird.

Spätere Aktualisierungen der `cq:tags`-Eigenschaft der Seite bereinigen automatisch die alten Verweise. Die Bereinigung wird ausgelöst, da die Auflösung eines verschobenen Tags über die API das Ziel-Tag zurückgibt und so die Ziel-Tag-ID bereitstellt.
