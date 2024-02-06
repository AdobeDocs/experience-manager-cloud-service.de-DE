---
title: Anpassen des Authoring-Erlebnisses für den universellen Editor
description: Erfahren Sie mehr über die verschiedenen Erweiterungspunkte und andere Funktionen, mit denen Sie die Benutzeroberfläche des universellen Editors anpassen können, um die Anforderungen Ihrer Inhaltsautoren zu unterstützen.
exl-id: 8d6523c8-b266-4341-b301-316d5ec224d7
source-git-commit: f04ab32093371ff425c4e196872738867d9ed528
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---


# Anpassen des Authoring-Erlebnisses für den universellen Editor {#customizing-ue}

Erfahren Sie mehr über die verschiedenen Erweiterungspunkte und andere Funktionen, mit denen Sie das Authoring-Erlebnis des universellen Editors anpassen können, um die Anforderungen Ihrer Inhaltsautoren zu unterstützen.

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

## Bedingtes Anzeigen und Ausblenden von Komponenten in der Eigenschaftenleiste {#conditionally-hide}

Obwohl eine oder mehrere Komponenten allgemein für Ihre Autoren verfügbar sein können, kann es in bestimmten Situationen vorkommen, dass dies nicht sinnvoll ist. In solchen Fällen können Sie Komponenten in der Eigenschaftenleiste ausblenden, indem Sie eine `condition` -Attribut [-Felder des Komponentenmodells.](/help/implementing/universal-editor/field-types.md#fields)

Bedingungen können mithilfe von [JsonLogic-Schema.](https://jsonlogic.com/) Wenn die Bedingung wahr ist, wird das Feld angezeigt. Wenn die Bedingung falsch ist, wird das Feld ausgeblendet.

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

#### Bedingung falsch {#false}

![Ausgeblendetes Textfeld](assets/hidden.png)

#### Bedingung wahr {#true}

![Angezeigtes Textfeld](assets/shown.png)
