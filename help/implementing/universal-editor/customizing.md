---
title: Anpassen des Authoring-Erlebnisses mit dem universellen Editor
description: Erfahren Sie mehr über die verschiedenen Erweiterungspunkte und anderen Funktionen, mit denen Sie die Benutzeroberfläche des universellen Editors anpassen können, um die Anforderungen Ihrer Inhaltsautorinnen und Inhaltsautoren zu unterstützen.
exl-id: 8d6523c8-b266-4341-b301-316d5ec224d7
source-git-commit: 11a244b7dd4810fbfec92b3effc362102e7322dc
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 100%

---


# Anpassen des Authoring-Erlebnisses mit dem universellen Editor {#customizing-ue}

Erfahren Sie mehr über die verschiedenen Erweiterungspunkte und anderen Funktionen, mit denen Sie das Inhaltserstellungserlebnis des universellen Editors anpassen können, um die Anforderungen Ihrer Inhaltsautorinnen und Inhaltsautoren zu unterstützen.

## Deaktivieren der Veröffentlichung {#disable-publish}

Bestimmte Authoring-Workflows erfordern, dass Inhalte vor der Veröffentlichung überprüft werden. In solchen Fällen sollte die Option zur Veröffentlichung für Autorinnen und Autoren nicht verfügbar sein.

Die Schaltfläche **Veröffentlichen** kann daher in einer App vollständig unterdrückt werden, indem die folgenden Metadaten hinzugefügt werden.

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

Anschließend können Sie über Ihre Container-Komponente auf die Filterdefinition verweisen, indem Sie die Eigenschaft `data-aue-filter` hinzufügen, wobei die Kennung des zuvor definierten Filters übergeben wird.

```html
data-aue-filter="container-filter"
```

Durch das Festlegen des Attributs `components` in einer Filterdefinition auf `null` werden alle Komponenten zugelassen, als gäbe es keinen Filter.

```json
[
  {
    "id": "another-container-filter",
     "components": null
   }
]
```

## Bedingtes Anzeigen und Ausblenden von Komponenten in der Eigenschaftenleiste {#conditionally-hide}

Obwohl eine oder mehrere Komponenten allgemein für Ihre Autorinnen und Autoren verfügbar sein können, kann es in bestimmten Situationen vorkommen, dass dies nicht sinnvoll ist. In solchen Fällen können Sie Komponenten in der Eigenschaftenleiste ausblenden, indem Sie ein Attribut `condition` zu den Feldern [ des Komponentenmodells hinzufügen.](/help/implementing/universal-editor/field-types.md#fields)

Bedingungen können mithilfe des [JsonLogic-Schemas definiert werden.](https://jsonlogic.com/) Wenn die Bedingung zutrifft, wird das Feld angezeigt. Wenn die Bedingung nicht zutrifft, wird das Feld ausgeblendet.

### Beispielmodell {#sample-model}

```json
 {
    "id": "conditionally-revealed-component",
    "fields": [
      {
        "component": "boolean",
        "label": "Shall the text field be revealed?",
        "name": "reveal",
        "valueType": "boolean"
      },
      {
        "component": "text-input",
        "label": "Hidden text field",
        "name": "hidden-text",
        "valueType": "string",
        "condition": { "===": [{"var" : "reveal"}, true] }
      }
    ]
 }
```

#### Bedingung trifft nicht zu {#false}

![Ausgeblendetes Textfeld](assets/hidden.png)

#### Bedingung trifft zu {#true}

![Eingeblendetes Textfeld](assets/shown.png)

