---
title: Filter
description: Erfahren Sie, wie Sie Filter definieren können, um die im Editor verfügbaren Optionen wie verfügbare Komponenten, RTE-Optionen und Asset-Auswahl zu beschränken.
feature: Developing
role: Admin, Developer
exl-id: eeae8d7c-c563-4d9b-8c54-1098a4e98c18
source-git-commit: 8d9d162ec5bba99afb1ae86252a49a9880be4e68
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 15%

---


# Filter {#filters}

Erfahren Sie, wie Sie Filter definieren können, um die im Editor verfügbaren Optionen wie verfügbare Komponenten, RTE-Optionen und Asset-Auswahl zu beschränken.

## Filter konfigurieren {#configuring-filters}

Bei Verwendung des universellen Editors können Sie die für bestimmte Funktionen zulässigen Optionen einschränken, indem Sie einen Filter definieren. Ein Filter ist eine Liste von Elementen oder Aktionen, die für den jeweiligen Kontext verfügbar sind. Sie können beispielsweise die verfügbaren Komponenten filtern, um sie in einen Container einzufügen, Sie können [die im RTE verfügbaren Optionen filtern](/help/implementing/universal-editor/configure-rte.md) und Sie können [die verfügbaren Assets filtern](/help/implementing/universal-editor/configure-assets-selector.md) im Asset-Selektor auswählen.

Die Filter müssen alle ähnlich definiert sein.

1. [Skript-Tag hinzufügen, um auf Filterdefinition zu verweisen](#add-tag)
1. [Filter definieren](#define-filter)
1. [Referenzieren des Filters](#reference-filter)

Nehmen wir ein Beispiel für das Filtern von Komponenten pro Container-Komponente.

## Definition des Referenzfilters {#add-tag}

Führen Sie zunächst ein zusätzliches Skript-Tag ein, das auf die Filterdefinition verweist.

In unserem Beispiel könnte das Tag zum Filtern der zulässigen Komponenten pro Container wie folgt aussehen.

```html
<script type="application/vnd.adobe.aue.filter+json" src="/static/filter-definition.json"></script>
```

## Filter definieren {#define-filter}

Eine Filterdefinition enthält JSON mit einer für den Filter und die Filterkriterien eindeutigen ID.

In unserem Beispiel könnte das Filtern der zulässigen Komponenten pro Container wie folgt aussehen, wodurch ein Container darauf beschränkt würde, nur Text und Bilder hinzuzufügen.

```json
[
  {
    "id": "container-filter",
    "components": ["text", "image"]
   }
]
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

## Verweisen auf den Filter {#reference-filter}

Um den Filter zu verwenden, müssen Sie auf die Filterdefinition verweisen. Gehen Sie dazu wie folgt vor:

* Referenzieren des Filters aus Ihrer Container-Komponente durch Hinzufügen der Eigenschaft `data-aue-filter` und Übergeben der ID des Filters.

  ```html
  data-aue-filter="container-filter"
  ```

* Referenzieren des Filters aus Ihrer [Komponentendefinition ](/help/implementing/universal-editor/component-definition.md) Übergeben der ID des Filters.

  ```json
  {
     "title":"My Container",
     "id":"my-container",
     "model": "my-model",
     "filter": "container-filter",
     ...
  }
  ```

## Zusätzliche Ressourcen {#additional-resources}

Erfahren Sie mehr über andere Anpassungs- und Erweiterungsoptionen, die dem universellen Editor in den Dokumenten zur Verfügung stehen:

* [Konfigurieren des RTE für den universellen Editor](/help/implementing/universal-editor/configure-rte.md)
* [Konfigurieren von Filtern für die Assets-Auswahl](/help/implementing/universal-editor/configure-assets-selector.md)
* [Anpassen des universellen Editors](/help/implementing/universal-editor/customizing.md)
* [Erweitern des universellen Editors](/help/implementing/universal-editor/extending.md)
