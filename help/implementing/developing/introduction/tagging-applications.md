---
title: Einbinden von Tagging in AEM-Programme
description: Programmatisch mit Tags oder erweiterten Tags innerhalb eines benutzerdefinierten AEM-Programms arbeiten
exl-id: a106dce1-5d51-406a-a563-4dea83987343
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 100%

---

# Einbinden von Tagging in AEM-Programme {#building-tagging-into-aem-applications}

Zum Zwecke von programmatischem Arbeiten mit Tags oder zum Erweitern von Tags in einem benutzerdefinierten AEM-Programm wird in diesem Dokument die Verwendung der

* [Tagging-API](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/tagging/package-summary.html),

die mit dem

* [Tagging-Framework interagiert, beschrieben.](tagging-framework.md)

Weitere Informationen zum Tagging finden Sie unter:

* Weitere Informationen zum Tagging von Inhalten als Inhaltsersteller finden Sie unter [Verwenden von Tags](/help/sites-cloud/authoring/sites-console/tags.md).
* Informationen zur Erstellung und Verwaltung von Tags durch Admins sowie dazu, welchen Inhalten Tags zugewiesen werden, finden Sie unter „Verwalten von Tags“.

## Übersicht über die Tagging-API {#overview-of-the-tagging-api}

Die Implementierung des [Tagging-Frameworks](tagging-framework.md) in AEM ermöglicht die Verwaltung von Tags und Tag-Inhalten mithilfe der JCR-API. `TagManager` stellt sicher, dass Tags, die als Werte in der `cq:tags`String-Array-Eigenschaft eingegeben wurden, nicht dupliziert werden. Er entfernt `TagID`, die auf nicht vorhandene Tags verweisen, und aktualisiert `TagID`für verschobene oder zusammengeführte Tags. `TagManager` verwendet einen JCR Observation Listener, der alle falschen Änderungen zurückgesetzt. Die wichtigsten Klassen befinden sich im Paket [com.day.cq.tagging](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/tagging/package-summary.html):

* `JcrTagManagerFactory` – gibt eine JCR-basierte Implementierung eines `TagManager`s zurück. Es ist die Referenzimplementierung der Tagging-API.
* `TagManager` – ermöglicht das Auflösen und Erstellen von Tags nach Pfaden und Namen.
* `Tag` - definiert das Tag-Objekt.

### Abrufen eines JCR-basierten TagManagers {#getting-a-jcr-based-tagmanager}

Um eine `TagManager`-Instanz abzurufen, benötigen Sie eine JCR-`Session` und Sie müssen `getTagManager(Session)` aufrufen:

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

Ein `Tag` kann über den `TagManager` abgerufen werden, indem entweder ein vorhandenes Tag aufgelöst oder eines erstellt wird:

```java
Tag tag = tagManager.resolve("my/tag"); // for existing tags

Tag tag = tagManager.createTag("my/tag"); // for new tags
```

Für die JCR-basierte Implementierung, die `Tags` auf JCR-`Nodes` abbildet, können Sie den Mechanismus `adaptTo` von Sling direkt verwenden, wenn Sie die Ressource haben (z. B. `/content/cq:tags/default/my/tag`):

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
>Die direkte Anpassung von `Node` zu `Tag` ist nicht möglich, da `Node` die Sling-Methode `Adaptable.adaptTo(Class)` nicht implementiert.

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

Es ist möglich, den Replikations-Service (`Replicator`) mit Tags zu verwenden, da Tags vom Typ `nt:hierarchyNode` sind:

```java
replicator.replicate(session, replicationActionType, tagPath);
```

## Der Tag Garbage Collector {#the-tag-garbage-collector}

Der Tag Garbage Collector ist ein Hintergrund-Service, der die ausgeblendeten und nicht verwendeten Tags bereinigt. Ausgeblendete und nicht verwendete Tags sind Tags unter `/content/cq:tags`, die eine `cq:movedTo`-Eigenschaft aufweisen und nicht für einen Inhaltsknoten verwendet werden. Ihre Anzahl beträgt null. Durch Verwenden dieses Lazy-Deletion-Prozesses muss der Inhaltsknoten (d. h. die Eigenschaft `cq:tags`) nicht als Teil des Verschiebungs- oder des Zusammenführungsvorgangs aktualisiert werden. Die Verweise in der Eigenschaft `cq:tags` werden automatisch aktualisiert, wenn die Eigenschaft `cq:tags` aktualisiert wird, z. B. durch das Seiteneigenschaften-Dialogfeld.

Der Garbage Collector für Tags wird standardmäßig einmal täglich ausgeführt. Dies kann konfiguriert werden unter:

`http://<host>:<port>/system/console/configMgr/com.day.cq.tagging.impl.TagGarbageCollector`

## Tag-Suche und Tag-Auflistung {#tag-search-and-tag-listing}

Die Tag-Suche und die Tag-Auflistung funktionieren folgendermaßen:

* Die Suche nach `TagID` sucht nach den Tags, für die die Eigenschaft `cq:movedTo` auf `TagID` gesetzt ist und `cq:movedTo`-`TagID`s folgt.
* Die Suche nach Tag-Titel sucht nur die Tags, die keine Eigenschaft `cq:movedTo` besitzen.

## Tags in verschiedenen Sprachen {#tags-in-different-languages}

Ein `title`-Tag kann in verschiedenen Sprachen definiert werden. Eine sprachempfindliche Eigenschaft wird dann dem Tag-Knoten hinzugefügt. Diese Eigenschaft weist das Format `jcr:title.<locale>` auf, beispielsweise `jcr:title.fr` für die französische Übersetzung. `<locale>` muss eine ISO-Gebietsschema-Zeichenfolge in Kleinbuchstaben sein und den Unterstrich (`_`) anstelle des Bindestrichs (`-`) verwenden. Beispiel: `de_ch`.

Wenn zum Beispiel das Tag **Tiere** zur Seite **Produkte** hinzugefügt wird, wird der Wert `stockphotography:animals` zur Eigenschaft `cq:tags` des Knotens `/content/wknd/en/products/jcr:content` hinzugefügt. Die Übersetzung wird vom Tag-Knoten referenziert.

Die Server-seitige API verfügt über lokalisierte `title`-bezogene Methoden:

* [`com.day.cq.tagging.Tag`](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/tagging/Tag.html)
   * `getLocalizedTitle(Locale locale)`
   * `getLocalizedTitlePaths()`
   * `getLocalizedTitles()`
   * `getTitle(Locale locale)`
   * `getTitlePath(Locale locale)`
* [`com.day.cq.tagging.TagManager`](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/tagging/TagManager.html)
   * `canCreateTagByTitle(String tagTitlePath, Locale locale)`
   * `createTagByTitle(String tagTitlePath, Locale locale)`
   * `resolveByTitle(String tagTitlePath, Locale locale)`

In AEM kann die Sprache entweder aus der Seitensprache oder aus der Anwendersprache abgerufen werden.

Beim Tagging hängt die Lokalisierung vom Kontext ab, da Tag-`titles` in der Seitensprache, in der Anwendersprache oder in jeder anderen Sprache angezeigt werden können.

### Hinzufügen einer neuen Sprache zum Dialogfeld „Tag bearbeiten“ {#adding-a-new-language-to-the-edit-tag-dialog}

Im folgenden Verfahren wird beschrieben, wie Sie dem Dialogfeld **Tag bearbeiten** eine neue Sprache (z. B. Finnisch) hinzufügen:

1. Bearbeiten Sie in **CRXDE** die Mehrwerteigenschaft `languages` des Knotens `/content/cq:tags`.
1. Fügen Sie `fi_fi` hinzu, das das finnische Gebietsschema darstellt, und speichern Sie die Änderungen.

Finnisch ist jetzt im Tag-Dialogfeld der Seiteneigenschaften und im Dialogfeld **Tag bearbeiten** verfügbar, wenn Sie ein Tag in der **Tagging-Konsole** bearbeiten.

>[!NOTE]
>
>Die neue Sprache muss eine der von AEM anerkannten Sprachen sein. Das heißt, sie muss als Knoten unterhalb von `/libs/wcm/core/resources/languages` verfügbar sein.
