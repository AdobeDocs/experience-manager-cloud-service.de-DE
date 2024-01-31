---
title: Anpassen der Benutzeroberfläche
description: Erfahren Sie mehr über die verschiedenen Erweiterungspunkte, mit denen Sie die Benutzeroberfläche des universellen Editors anpassen können, um die Anforderungen Ihrer Inhaltsautoren zu unterstützen.
exl-id: 8d6523c8-b266-4341-b301-316d5ec224d7
source-git-commit: 1bc65e65e6ce074a050e21137ce538b5c086665f
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---


# Anpassen der Benutzeroberfläche {#customizing-ui}

Erfahren Sie mehr über die verschiedenen Erweiterungspunkte, mit denen Sie die Benutzeroberfläche des universellen Editors anpassen können, um die Anforderungen Ihrer Inhaltsautoren zu unterstützen.

## Publishing deaktivieren {#disable-publish}

Bestimmte Authoring-Workflows erfordern, dass Inhalte vor der Veröffentlichung überprüft werden. In solchen Fällen sollte die Option zur Veröffentlichung für Autoren nicht verfügbar sein.

Die **Veröffentlichen** -Schaltfläche kann daher in einer App vollständig unterdrückt werden, indem die folgenden Metadaten hinzugefügt werden.

```html
<meta name="urn:adobe:aue:config:disable" content="publish"/>
```

## Filtern von Komponenten {#filtering-components}

Bei Verwendung des universellen Editors können Sie die zulässigen Komponenten pro Container-Komponente einschränken. Dazu müssen Sie ein zusätzliches Skript-Tag einführen, das auf die Filterdefinition verweist.

```html
<script type="application/vnd.adobe.aue.filter+json" src="/static/filter-definition.json"></script>
```

Eine Filterdefinition könnte wie folgt aussehen, wodurch ein Container so eingeschränkt würde, dass nur Text und Bilder hinzugefügt werden können.

```json
[
  {
    "id": "container-filter",
     "components": ["text", "image"]
   }
]
```

Anschließend können Sie über Ihre Container-Komponente auf die Filterdefinition verweisen, indem Sie die Eigenschaft hinzufügen `data-aue-filter`, wobei die Kennung des zuvor definierten Filters übergeben wird.

```html
data-aue-filter="container-filter"
```

Festlegen der `components` -Attribut in einer Filterdefinition `null` lässt alle Komponenten zu, als gäbe es keinen Filter.

```json
[
  {
    "id": "another-container-filter",
     "components": null
   }
]
```
