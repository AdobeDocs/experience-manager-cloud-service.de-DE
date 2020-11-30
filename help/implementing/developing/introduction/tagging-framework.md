---
title: AEM-Tagging-Framework
description: Versehen Sie Inhalte mit Tags und nutzen Sie die AEM-Tagging-Infrastruktur. um es zu kategorisieren und zu organisieren.
translation-type: tm+mt
source-git-commit: 4bf023068aa69fb6b69c6f2443703ea2bbbf7d42
workflow-type: tm+mt
source-wordcount: '1567'
ht-degree: 25%

---


# The AEM Tagging Framework {#aem-tagging-framework}

Tagging ermöglicht die Kategorisierung und Organisation von Inhalten. Tags können anhand eines Namespace und einer Taxonomie klassifiziert werden. Ausführliche Informationen zur Verwendung von Tags:

* Informationen zum Taggen von Inhalten als Inhaltsautor finden Sie unter [Verwenden von Tags](/help/sites-cloud/authoring/features/tags.md) .
* Informationen zum Erstellen und Verwalten von Tags sowie zu den angewendeten Inhalts-Tags finden Sie unter Verwalten von Tags.

Dieser Artikel konzentriert sich auf das zugrunde liegende Framework, das Tagging in AEM unterstützt, und darauf, wie es als Entwickler genutzt werden kann.

## Einführung {#introduction}

Versehen Sie Inhalte mit Tags und nutzen Sie die AEM-Tagging-Infrastruktur wie folgt:

* The tag must exist as a node of type [`cq:Tag`](#cq-tag-node-type) under the [taxonomy root node.](#taxonomy-root-node)
* The tagged content node&#39;s `NodeType` must include the [`cq:Taggable`](#taggable-content-cq-taggable-mixin) mixin.
* The [`TagID`](#tagid) is added to the content node&#39;s [`cq:tags`](#cq-tags-property) property and resolves to a node of type [`cq:Tag`.](#cq-tag-node-type)

## cq:Tag Node Type {#cq-tag-node-type}

The declaration of a tag is captured in the repository in a node of type `cq:Tag.`

* A tag can be a simple word (e.g. `sky`) or represent a hierarchical taxonomy (e.g. `fruit/apple`, meaning both the generic fruit and the more specific apple).
* Tags are identified by a unique `TagID`.
* Ein Tag weist optionale Metadaten auf, z. B. einen Titel, lokalisierte Titel und eine Beschreibung. The title should be displayed in user interfaces instead of the `TagID`, when present.

Das Tagging-Framework bietet außerdem die Möglichkeit, Autoren und Websitebesuchern die Verwendung bestimmter, vordefinierter Tags vorzugeben.

### Tag-Eigenschaften {#tag-characteristics}

* Der Knotentyp ist `cq:Tag`.
* The node name is a component of the [`TagID`.](#tagid)
* The [`TagID`](#tagid) always includes a [namespace.](#tag-namespace)
* Die `jcr:title` Eigenschaft (der Titel, der in der Benutzeroberfläche angezeigt werden soll) ist optional.
* The `jcr:description` property is optional.
* When containing child nodes, is referred to as a [container tag.](#container-tags)
* The tag is stored in the repository below a base path called the [taxonomy root node.](#taxonomy-root-node)

### Tag-ID {#tagid}

A `TagID` identifies a path which resolves to a tag node in the repository.

Typically, the `TagID` is a shorthand `TagID` starting with the namespace or it can be an absolute `TagID` starting from the [taxonomy root node.](#taxonomy-root-node)

When content is tagged, if it does not yet exist, the [`cq:tags`](#cq-tags-property) property is added to the content node and the `TagID` is added to the property&#39;s `String` array value.

The `TagID` consists of a [namespace](#tag-namespace) followed by the local `TagID`. [Container-Tags](#container-tags) weisen untergeordnete Tags auf, die eine hierarchische Reihenfolge in der Taxonomie darstellen. Sub-tags can be used to reference tags same as any local `TagID`. For example tagging content with `fruit` is allowed, even if it is a container tag with sub-tags, such as `fruit/apple` and `fruit/banana`.

### Stammknoten der Taxonomie {#taxonomy-root-node}

Der Stammknoten der Taxonomie ist der Basispfad für alle Tags im Repository. The taxonomy root node must *not* be a node of type `cq:Tag`.

In AEM, the base path is `/content/cq:tags` and the root node is of type `cq:Folder`.

### Tag-Namespace {#tag-namespace}

Namespaces ermöglichen das Gruppieren von Elementen. Der typischste Anwendungsfall besteht darin, einen Namensraum pro Site (z. B. öffentlich oder intern) oder pro größere Anwendung (z. B. Sites oder Assets) zu haben, aber Namensraum können für verschiedene andere Anforderungen verwendet werden. Namensraum werden in der Benutzeroberfläche verwendet, um nur die Teilmenge der Tags (d. h. Tags eines bestimmten Namensraums) anzuzeigen, die für den aktuellen Inhalt gilt.

Der Namespace des Tags ist die erste Ebene im Teilbaum der Taxonomie, der den Knoten direkt unterhalb des [Stammknotens der Taxonomie darstellt.](#taxonomy-root-node) Ein Namensraum ist eine Node des Typs `cq:Tag` , deren übergeordneter Knoten kein `cq:Tag` Node-Typ ist.

Alle Tags haben einen Namespace. Wenn kein Namensraum angegeben ist, wird das Tag dem standardmäßigen Namensraum zugewiesen, d. `TagID` h. `default`dem Tag. `/content/cq:tags/default`.  Der Titel wird `Standard Tags`in solchen Fällen standardmäßig verwendet.

### Container-Tags {#container-tags}

Container-Tags sind Knoten vom Typ `cq:Tag`, die eine beliebige Anzahl untergeordneter Knoten von beliebigen Typen enthalten. Das ermöglicht die Erweiterung des Tag-Modells mit benutzerdefinierten Metadaten.

Furthermore, container tags (or super-tags) in a taxonomy serve as the sub-summation of all sub-tags: for example content tagged with `fruit/apple` is considered to be tagged with `fruit` as well, i.e. searching for content just tagged with `fruit` would also find the content tagged with `fruit/apple`.

### Auflösen von Tag-IDs {#resolving-tagids}

If the tag ID contains a colon (`:`), the colon separates the namespace from the tag or sub-taxonomy, which are then separated with normal slashes (`/`). Wenn in der Tag-ID kein Doppelpunkt vorkommt, ist der Standard-Namespace impliziert.

The standard and only location of tags is below `/content/cq:tags`.

Tags referencing non-existing paths or paths that do not point to a `cq:Tag` node are considered invalid and are ignored.

The following table shows some sample `TagID`s, their elements, and how the `TagID` resolves to an absolute path in the repository:

| `TagID` | Namespace | Lokale ID | Container-Tag(s) | Leaf-Tag | Repository Absoluter Tag-Pfad |
|---|---|---|---|---|---|
| `dam:fruit/apple/braeburn` | `dam` | `fruit/apple/braeburn` | `fruit`,`apple` | `braeburn` | `content/cq:tags/dam/fruit/apple/braeburn` |
| `color/red` | `default` | `color/red` | `color` | `red` | `/content/cq:tags/default/color/red` |
| `sky` | `default` | `sky` | (keine) | `sky` | `/content/cq:tags/default/sky` |
| `dam:` | `dam` | (keine) | (keine) | (keine) | `/content/cq:tags/dam` |
| `content/cq:tags/category/car` | `category` | `car` | `car` | `car` | `content/cq:tags/category/car` |

### Lokalisierung des Tag-Titels {#localization-of-tag-title}

When the tag includes the optional title string `jcr:title`, it is possible to localize the title for display by adding the property `jcr:title.<locale>`.

Weitere Informationen finden Sie unter:

* [Tags in verschiedenen Sprachen,](tagging-applications.md#tags-in-different-languages) in denen die Verwendung der APIs als Entwickler beschrieben wird
* Verwalten von Tags in verschiedenen Sprachen, in denen die Verwendung der Tagging-Konsole als Administrator beschrieben wird

### Zugriffssteuerung {#access-control}

Tags bestehen als Knoten im Repository unter dem [Stammknoten der Taxonomie.](#taxonomy-root-node) Es kann erreicht werden, dass Autoren und Site-Besucher Tags in einem bestimmten Namensraum erstellen oder verweigern können, indem entsprechende ACLs im Repository festgelegt werden.

Das Verweigern von Leseberechtigungen für bestimmte Tags oder Namensraum steuert die Fähigkeit, Tags auf bestimmte Inhalte anzuwenden.

Eine typische Vorgehensweise umfasst Folgendes:

* Allowing the `tag-administrators` group/role write access to all namespaces (add/modify under `/content/cq:tags`). Diese Gruppe enthält AEM standardmäßig.
* Gewähren von Lesezugriff für Benutzer/Autoren auf alle Namespaces, die sie lesen können müssen (meist alle).
* Allowing users/authors write access to those namespaces where tags should be freely definable by users/authors (`add_node` under `/content/cq:tags/some_namespace`)

## Tag-barer Inhalt: cq:Taggable-Mixin {#taggable-content-cq-taggable-mixin}

In order for application developers to attach tagging to a content type, the node&#39;s registration ([CND](https://jackrabbit.apache.org/node-type-notation.html)) must include the `cq:Taggable` mixin or the `cq:OwnerTaggable` mixin.

Das Mixin `cq:OwnerTaggable`, der von `cq:Taggable` übernimmt, soll anzeigen, dass der Inhalt vom Besitzer/Autor klassifiziert werden kann. In AEM, it is only an attribute of the `cq:PageContent` node. The `cq:OwnerTaggable` mixin is not required by the tagging framework.

>[!NOTE]
>
>It is recommended to only enable tags on the top-level node of an aggregated content item (or on its `jcr:content` node). Beispiele dafür sind:
>
>* Pages (`cq:Page`) where the `jcr:content`node is of type `cq:PageContent`, which includes the `cq:Taggable` mixin.
>* Assets (`cq:Asset`) where the `jcr:content/metadata` node always has the `cq:Taggable` mixin.


### Knotentypnotation (CND) {#node-type-notation-cnd}

Knotentypdefinitionen sind im Repository als CND-Dateien vorhanden. The CND notation is defined as part of the [JCR documentation.](https://jackrabbit.apache.org/node-type-notation.html).

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

The `cq:tags` property is a `String` array used to store one or more `TagID`s when they are applied to content by authors or site visitors. Die Eigenschaft hat nur dann eine Bedeutung, wenn sie einem Knoten hinzugefügt wird, der mit dem Mixin [`cq:Taggable`](#taggable-content-cq-taggable-mixin) definiert wird.

>[!NOTE]
>
>To leverage AEM tagging functionality, custom developed applications should not define tag properties other than `cq:tags`.

## Verschieben und Zusammenführen von Tags {#moving-and-merging-tags}

Im Folgenden finden Sie eine Beschreibung der Auswirkungen, die im Repository auftreten, wenn Sie Tags mit der Tagging-Konsole verschieben oder zusammenführen.

When tag A is moved or merged into tag B under `/content/cq:tags`:

* Tag A is not deleted and receives a `cq:movedTo` property.
   * `cq:movedTo` verweist auf Tag B.
   * Diese Eigenschaft bedeutet, dass Tag A verschoben oder in Tag B zusammengeführt wurde.
   * Durch Verschieben von Tag B wird diese Eigenschaft entsprechend aktualisiert.
   * Tag A wird daher ausgeblendet und nur im Repository aufbewahrt, um Tag-IDs in Inhaltsknoten aufzulösen, die auf Tag A verweisen.
   * Der Tag-Garbage Collector entfernt Tags wie Tag A, sobald keine Inhaltsknoten mehr auf sie zeigen.
   * A special value for the `cq:movedTo` property is `nirvana`, which is applied when the tag is deleted but cannot be removed from the repository because there are subtags with a `cq:movedTo` that must be kept.

      >[!NOTE]
      >
      >Die `cq:movedTo` Eigenschaft wird dem verschobenen oder zusammengeführten Tag nur hinzugefügt, wenn eine der folgenden Bedingungen erfüllt ist:
      >
      > 1. Das Tag wird im Inhalt verwendet (d. h. es enthält einen Verweis). ODER
      > 1. Das Tag enthält bereits verschobene untergeordnete Elemente.


* Tag B is created (in case of a move) and receives a `cq:backlinks` property.
   * `cq:backlinks` behält die Verweise in die andere Richtung, d. h. es behält eine Liste aller Tags bei, die zu Tag B verschoben oder mit ihm zusammengeführt wurden.
   * Dies ist vor allem erforderlich, um `cq:movedTo` Eigenschaften auf dem neuesten Stand zu halten, wenn Tag B verschoben/zusammengeführt/gelöscht wird oder wenn Tag B aktiviert wird. In diesem Fall müssen auch alle Backlinks-Tags aktiviert werden.

      >[!NOTE]
      >
      >Die `cq:backlinks` Eigenschaft wird dem verschobenen oder zusammengeführten Tag nur hinzugefügt, wenn eine der folgenden Bedingungen erfüllt ist:
      >
      > 1. Das Tag wird im Inhalt verwendet (d. h. es enthält einen Verweis). ODER
      > 1. Das Tag enthält bereits verschobene untergeordnete Elemente.


Reading a `cq:tags` property of a content node involves the following resolution:

1. If there is no match under `/content/cq:tags`, no tag is returned.
1. Wenn das Tag eine `cq:movedTo`-Eigenschaft aufweist, steht danach die referenzierte Tag-ID.
   * Dieser Schritt wird so lange wiederholt, wie das angehängte Tag eine `cq:movedTo`-Eigenschaft aufweist.
1. Falls das angehängte Tag nicht über eine `cq:movedTo`-Eigenschaft verfügt, wird das Tag gelesen.

Um die Änderung zu veröffentlichen, wenn ein Tag verschoben oder zusammengeführt wurde, müssen der `cq:Tag` Knoten und alle zugehörigen Backlinks repliziert werden. Dies erfolgt automatisch, wenn das Tag in der Tag-Verwaltungskonsole aktiviert wird.

Later updates to the page&#39;s `cq:tags` property automatically clean up the old references. Dies wird ausgelöst, da die Auflösung eines verschobenen Tags über die API das Ziel-Tag zurückgibt und so die Ziel-Tag-ID bereitstellt.
