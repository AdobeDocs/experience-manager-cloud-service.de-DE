---
title: Filtern von Komponenten
description: Erfahren Sie, wie Sie die zulässigen Komponenten pro Container im universellen Editor mithilfe von Komponentenfiltern einschränken können.
feature: Developing
role: Admin, Architect, Developer
exl-id: eeae8d7c-c563-4d9b-8c54-1098a4e98c18
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 63%

---

# Filtern von Komponenten {#filtering-components}

Erfahren Sie, wie Sie die zulässigen Komponenten pro Container im universellen Editor mithilfe von Komponentenfiltern einschränken können.

## Filter {#filters}

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

>[!TIP]
>
>Weitere Informationen zu anderen Anpassungs- und Erweiterungsoptionen, die dem universellen Editor zur Verfügung stehen, finden Sie im Dokument [Anpassen und Erweitern des universellen Editors](/help/implementing/universal-editor/customizing.md).