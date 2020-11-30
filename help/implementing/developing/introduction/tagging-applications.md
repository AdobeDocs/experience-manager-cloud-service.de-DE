---
title: Erstellen von Tags in AEM Anwendungen
description: Programmatisch mit Tags oder erweiterten Tags innerhalb einer benutzerdefinierten AEM-Anwendung arbeiten
translation-type: tm+mt
source-git-commit: ce55065c3ae6a2350ed06811af76477df7c11291
workflow-type: tm+mt
source-wordcount: '769'
ht-degree: 35%

---


# Erstellen von Tags in AEM Anwendungen {#building-tagging-into-aem-applications}

Zum programmgesteuerten Arbeiten mit Tags oder Erweitern von Tags in einer benutzerdefinierten AEM wird in diesem Dokument die Verwendung der Variablen

* [Tagging-API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/tagging/package-summary.html),

die mit der

* [Tagging-Framework](tagging-framework.md) interagiert, beschrieben.

Weitere Informationen zum Tagging:

* Informationen zum Taggen von Inhalten als Inhaltsautor finden Sie unter [Verwenden von Tags](/help/sites-cloud/authoring/features/tags.md) .
* Informationen zum Erstellen und Verwalten von Tags sowie zu den angewendeten Inhalts-Tags finden Sie unter Verwalten von Tags.

## Übersicht über die Tagging-API {#overview-of-the-tagging-api}

Die Implementierung des [Tagging-Frameworks](tagging-framework.md) in AEM ermöglicht die Verwaltung von Tags und Tag-Inhalten mithilfe der JCR-API. `TagManager` stellt sicher, dass Tags, die als Werte in der `cq:tags` String-Array-Eigenschaft eingegeben wurden, nicht dupliziert werden. Dadurch werden `TagID`s entfernt, die auf nicht vorhandene Tags verweisen, und es werden Updates `TagID`für verschobene oder zusammengeführte Tags entfernt. `TagManager` verwendet einen JCR Observation Listener, der alle falschen Änderungen zurückgesetzt. Die wichtigsten Klassen befinden sich im Paket [com.day.cq.tagging](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/tagging/package-summary.html):

* `JcrTagManagerFactory` - gibt eine JCR-basierte Implementierung einer `TagManager`zurück. Es ist die Referenzimplementierung der Tagging-API.
* `TagManager` - ermöglicht das Auflösen und Erstellen von Tags anhand von Pfaden und Namen.
* `Tag` - definiert das Tag-Objekt.

### Abrufen eines JCR-basierten TagManagers {#getting-a-jcr-based-tagmanager}

To retrieve a `TagManager` instance, you need to have a JCR `Session` and to call `getTagManager(Session)`:

```java
@Reference
JcrTagManagerFactory jcrTagManagerFactory;

TagManager tagManager = jcrTagManagerFactory.getTagManager(session);
```

Im typischen Sling-Kontext können Sie sich auch mit dem `TagManager` an einen `ResourceResolver` anpassen:

```java
TagManager tagManager = resourceResolver.adaptTo(TagManager.class);
```

### Abrufen eines Tag-Objekts {#retrieving-a-tag-object}

Ein `Tag` kann über den `TagManager` abgerufen werden, indem entweder ein vorhandenes Tag aufgelöst oder ein neues erstellt wird:

```java
Tag tag = tagManager.resolve("my/tag"); // for existing tags

Tag tag = tagManager.createTag("my/tag"); // for new tags
```

For the JCR-based implementation, which maps `Tags` onto JCR `Nodes`, you can directly use Sling&#39;s `adaptTo` mechanism if you have the resource (e.g. such as `/content/cq:tags/default/my/tag`):

```java
Tag tag = resource.adaptTo(Tag.class);
```

Während ein Tag nur *von* einer Ressource (kein Knoten) konvertiert werden kann, kann ein Tag sowohl *in* einen Knoten als auch in eine Ressource konvertiert werden:

```java
Node node = tag.adaptTo(Node.class);
Resource node = tag.adaptTo(Resource.class);
```

>[!NOTE]
>
>Directly adapting from `Node` to `Tag` is not possible, because `Node` does not implement the Sling `Adaptable.adaptTo(Class)` method.

### Abrufen und Festlegen von Tags {#getting-and-setting-tags}

```java
// Getting the tags of a Resource:
Tag[] tags = tagManager.getTags(resource);

// Setting tags to a Resource:
tagManager.setTags(resource, tags);
```

### Suchen nach Tags {#searching-for-tags}

```java
// Searching for the Resource objects that are tagged with the tag object:
Iterator<Resource> it = tag.find();

// Retrieving the usage count of the tag object:
long count = tag.getCount();

// Searching for the Resource objects that are tagged with the tagID String:
 RangeIterator<Resource> it = tagManager.find(tagID);
```

>[!NOTE]
>
>Der gültige zu verwendete `RangeIterator` ist:
>
>`com.day.cq.commons.RangeIterator`

### Löschen von Tags {#deleting-tags}

```java
tagManager.deleteTag(tag);
```

### Replizieren von Tags {#replicating-tags}

It is possible to use the replication service (`Replicator`) with tags because tags are of type `nt:hierarchyNode`:

```java
replicator.replicate(session, replicationActionType, tagPath);
```

## Der Tag Garbage Collector {#the-tag-garbage-collector}

Der Tag-Müll-Collector ist ein Hintergrunddienst, der die Tags bereinigt, die ausgeblendet und nicht verwendet werden. Ausgeblendete und nicht verwendete Tags sind Tags unterhalb `/content/cq:tags` der Tags, die eine `cq:movedTo` Eigenschaft aufweisen und nicht auf einem Inhaltsknoten verwendet werden. Sie zählen Null. Durch Verwenden dieses Lazy-Deletion-Prozesses muss der Inhaltsknoten (d. h. die Eigenschaft `cq:tags`) nicht als Teil der Verschiebung oder dem Zusammenführungsvorgang aktualisiert werden. Die Verweise in der Eigenschaft `cq:tags` werden automatisch aktualisiert, wenn die Eigenschaft `cq:tags` aktualisiert wird, z. B. durch das Seiteneigenschaften-Dialogfeld.

Das Garbage Collector Tag wird standardmäßig einmal am Tag ausgeführt. Dies kann konfiguriert werden unter:

`http://<host>:<port>/system/console/configMgr/com.day.cq.tagging.impl.TagGarbageCollector`

## Tag-Suche und Tag-Auflistung {#tag-search-and-tag-listing}

Die Tag-Suche und die Tag-Auflistung funktionieren folgendermaßen:

* The search for `TagID` searches for the tags that have the property `cq:movedTo` set to `TagID` and follows through the `cq:movedTo` `TagID`s.
* The search for tag title only searches the tags that do not have a `cq:movedTo` property.

## Tags in verschiedenen Sprachen {#tags-in-different-languages}

Ein Tag `title` kann in verschiedenen Sprachen definiert werden. Eine sprachempfindliche Eigenschaft wird dann dem Tag-Knoten hinzugefügt. Diese Eigenschaft hat das Format `jcr:title.<locale>`, z.B. `jcr:title.fr` für die französische Übersetzung. `<locale>` muss eine ISO-Gebietsschema-Zeichenfolge in Kleinbuchstaben sein und den Unterstrich (`_`) anstelle von Bindestrich/Bindestrich (`-`) verwenden. Beispiel: `de_ch`.

Wenn beispielsweise der Seite &quot; **Produkte** &quot;das Tag &quot; **Tiere** &quot;hinzugefügt wird, `stockphotography:animals` wird der Wert der Eigenschaft `cq:tags` der Node hinzugefügt `/content/wknd/en/products/jcr:content`. Die Übersetzung wird vom Tag-Knoten referenziert.

The server-side API has localized `title`-related methods:

* [`com.day.cq.tagging.Tag`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/tagging/Tag.html)
   * `getLocalizedTitle(Locale locale)`
   * `getLocalizedTitlePaths()`
   * `getLocalizedTitles()`
   * `getTitle(Locale locale)`
   * `getTitlePath(Locale locale)`
* [`com.day.cq.tagging.TagManager`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/tagging/TagManager.html)
   * `canCreateTagByTitle(String tagTitlePath, Locale locale)`
   * `createTagByTitle(String tagTitlePath, Locale locale)`
   * `resolveByTitle(String tagTitlePath, Locale locale)`

In AEM kann die Sprache entweder aus der Seitensprache oder aus der Benutzersprache abgerufen werden.

For tagging, localization depends on the context as tag `titles` can be displayed in the page language, in the user language or in any other language.

### Hinzufügen einer neuen Sprache zum Dialogfeld „Tag bearbeiten“{#adding-a-new-language-to-the-edit-tag-dialog}

The following procedure describes how to add a new language (e.g. Finnish) to the **Tag Edit** dialog:

1. In **CRXDE**, edit the multi-value property `languages` of the node `/content/cq:tags`.
1. Add `fi_fi`, which represents the Finnish locale, and save the changes.

Finnish is now available in the tag dialog of the page properties and in the **Edit Tag** dialog when editing a tag in the **Tagging** console.

>[!NOTE]
>
>The new language needs to be one of the AEM recognized languages, i.e. it needs to be available as a node below `/libs/wcm/core/resources/languages`.
