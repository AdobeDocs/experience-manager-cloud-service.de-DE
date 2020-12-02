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

* Informationen zum Taggen von Inhalten als Inhaltsersteller finden Sie unter [Tags](/help/sites-cloud/authoring/features/tags.md) verwenden.
* Informationen zum Erstellen und Verwalten von Tags sowie zu den angewendeten Inhalts-Tags finden Sie unter Verwalten von Tags.

## Übersicht über die Tagging-API {#overview-of-the-tagging-api}

Die Implementierung des [Tagging-Frameworks](tagging-framework.md) in AEM ermöglicht die Verwaltung von Tags und Tag-Inhalten mithilfe der JCR-API. `TagManager` stellt sicher, dass Tags, die als Werte in der  `cq:tags` String-Array-Eigenschaft eingegeben wurden, nicht dupliziert werden. Dadurch werden  `TagID`Seiten entfernt, die auf nicht vorhandene Tags verweisen, und es werden Updates  `TagID`für verschobene oder zusammengeführte Tags entfernt. `TagManager` verwendet einen JCR Observation Listener, der alle falschen Änderungen zurückgesetzt. Die wichtigsten Klassen befinden sich im Paket [com.day.cq.tagging](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/tagging/package-summary.html):

* `JcrTagManagerFactory` - gibt eine JCR-basierte Implementierung einer  `TagManager`zurück. Es ist die Referenzimplementierung der Tagging-API.
* `TagManager` - ermöglicht das Auflösen und Erstellen von Tags anhand von Pfaden und Namen.
* `Tag` - definiert das Tag-Objekt.

### Abrufen eines JCR-basierten TagManagers {#getting-a-jcr-based-tagmanager}

Um eine `TagManager`-Instanz abzurufen, müssen Sie über eine JCR `Session`-Instanz verfügen und `getTagManager(Session)` aufrufen:

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

Für die JCR-basierte Implementierung, die `Tags` JCR `Nodes` zuordnet, können Sie den `adaptTo`-Mechanismus von Sling direkt verwenden, wenn Sie über die Ressource verfügen (z. B. `/content/cq:tags/default/my/tag`):

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
>Die direkte Anpassung von `Node` an `Tag` ist nicht möglich, da `Node` die Sling `Adaptable.adaptTo(Class)`-Methode nicht implementiert.

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

Es ist möglich, den Replizierungsdienst (`Replicator`) mit Tags zu verwenden, da Tags vom Typ `nt:hierarchyNode` sind:

```java
replicator.replicate(session, replicationActionType, tagPath);
```

## Der Tag Garbage Collector {#the-tag-garbage-collector}

Der Tag-Müll-Collector ist ein Hintergrunddienst, der die Tags bereinigt, die ausgeblendet und nicht verwendet werden. Ausgeblendete und nicht verwendete Tags sind Tags unterhalb von `/content/cq:tags`, die eine `cq:movedTo`-Eigenschaft haben und nicht auf einem Inhaltsknoten verwendet werden. Sie zählen Null. Durch Verwenden dieses Lazy-Deletion-Prozesses muss der Inhaltsknoten (d. h. die Eigenschaft `cq:tags`) nicht als Teil der Verschiebung oder dem Zusammenführungsvorgang aktualisiert werden. Die Verweise in der Eigenschaft `cq:tags` werden automatisch aktualisiert, wenn die Eigenschaft `cq:tags` aktualisiert wird, z. B. durch das Seiteneigenschaften-Dialogfeld.

Das Garbage Collector Tag wird standardmäßig einmal am Tag ausgeführt. Dies kann konfiguriert werden unter:

`http://<host>:<port>/system/console/configMgr/com.day.cq.tagging.impl.TagGarbageCollector`

## Tag-Suche und Tag-Auflistung {#tag-search-and-tag-listing}

Die Tag-Suche und die Tag-Auflistung funktionieren folgendermaßen:

* Die Suche nach `TagID` sucht nach den Tags, für die die Eigenschaft `cq:movedTo` auf `TagID` gesetzt ist, und folgt durch die `cq:movedTo` `TagID`s.
* Bei der Suche nach Tag-Titel werden nur die Tags durchsucht, die keine `cq:movedTo`-Eigenschaft haben.

## Tags in verschiedenen Sprachen {#tags-in-different-languages}

Ein Tag `title` kann in verschiedenen Sprachen definiert werden. Eine sprachempfindliche Eigenschaft wird dann dem Tag-Knoten hinzugefügt. Diese Eigenschaft hat das Format `jcr:title.<locale>`, z.B. `jcr:title.fr` für die französische Übersetzung. `<locale>` muss eine ISO-Gebietsschema-Zeichenfolge in Kleinbuchstaben sein und den Unterstrich (`_`) anstelle von Bindestrich/Bindestrich (`-`) verwenden. Beispiel:  `de_ch`.

Wenn beispielsweise das Tag **Tiere** der Seite **Produkte** hinzugefügt wird, wird der Wert `stockphotography:animals` der Eigenschaft `cq:tags` des Knotens `/content/wknd/en/products/jcr:content` hinzugefügt. Die Übersetzung wird vom Tag-Knoten referenziert.

Die serverseitige API hat lokalisierte `title`-bezogene Methoden:

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

Beim Tagging hängt die lokale Anpassung vom Kontext ab, da das Tag `titles` in der Seitensprache, in der Benutzersprache oder in jeder anderen Sprache angezeigt werden kann.

### Hinzufügen einer neuen Sprache zum Dialogfeld „Tag bearbeiten“{#adding-a-new-language-to-the-edit-tag-dialog}

Im folgenden Verfahren wird beschrieben, wie Sie eine neue Sprache (z. B. Finnisch) zum Dialogfeld **Tag bearbeiten** hinzufügen:

1. Bearbeiten Sie in **CRXDE** die Eigenschaft mit mehreren Werten `languages` des Knotens `/content/cq:tags`.
1. hinzufügen `fi_fi`, das das finnische Gebietsschema darstellt, und speichern Sie die Änderungen.

Finnisch ist jetzt im Tag-Dialogfeld der Seiteneigenschaften und im Dialogfeld **Tag bearbeiten** verfügbar, wenn ein Tag in der Konsole **Tagging** bearbeitet wird.

>[!NOTE]
>
>Die neue Sprache muss eine der AEM erkannten Sprachen sein, d.h. sie muss als Knoten unterhalb von `/libs/wcm/core/resources/languages` verfügbar sein.
