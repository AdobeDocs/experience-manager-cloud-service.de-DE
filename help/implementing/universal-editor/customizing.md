---
title: Anpassen und Erweitern des universellen Editors
description: Erfahren Sie mehr über die verschiedenen Erweiterungspunkte und anderen Funktionen, mit denen Sie die Benutzeroberfläche des universellen Editors anpassen können, um die Anforderungen Ihrer Inhaltsautorinnen und Inhaltsautoren zu unterstützen.
exl-id: 8d6523c8-b266-4341-b301-316d5ec224d7
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 732b0648e7114594cb8d35df03f83b842d62736e
workflow-type: tm+mt
source-wordcount: '646'
ht-degree: 89%

---


# Anpassen und Erweitern des universellen Editors {#customizing-extending}

Erfahren Sie mehr über die verschiedenen Erweiterungspunkte und anderen Funktionen, mit denen Sie das Inhaltserstellungserlebnis des universellen Editors anpassen können, um die Anforderungen Ihrer Inhaltsautorinnen und Inhaltsautoren zu unterstützen.

## Überblick {#overview}

Der universelle Editor ermöglicht zwei Arten der Anpassung an die Anforderungen Ihres Projekts.

* [Anpassen des universellen Editors](#customizing) – Die Standardfunktionen des universellen Editors können über verschiedene Anpassungskonfigurationen angepasst werden.
* [Erweitern der Benutzeroberfläche des universellen Editors](#extending) – Die Benutzeroberfläche des universellen Editors kann auch mit App Builder erweitert werden, damit sie die Anforderungen Ihrer Projekte erfüllt.

Beide Arten werden in den folgenden Abschnitten beschrieben.

## Anpassen des universellen Editors {#customizing}

Der universelle Editor bietet mehrere integrierte Optionen zur Anpassung seiner Funktionen.

### Deaktivieren der Veröffentlichung {#disable-publish}

Bestimmte Authoring-Workflows erfordern, dass Inhalte vor der Veröffentlichung überprüft werden. In solchen Fällen sollte die Option zur Veröffentlichung für Autorinnen und Autoren nicht verfügbar sein.

Die Schaltfläche **Veröffentlichen** kann daher in einer App vollständig unterdrückt werden, indem die folgenden Metadaten hinzugefügt werden.

```html
<meta name="urn:adobe:aue:config:disable" content="publish"/>
```

### Filtern von Komponenten {#filtering-components}

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

### Bedingtes Anzeigen und Ausblenden von Komponenten im Eigenschaftenbedienfeld {#conditionally-hide}

Obwohl eine oder mehrere Komponenten allgemein für Ihre Autorinnen und Autoren verfügbar sein können, kann es in bestimmten Situationen vorkommen, dass dies nicht sinnvoll ist. In solchen Fällen können Sie Komponenten im Eigenschaftenbedienfeld ausblenden, indem Sie den Feldern [des Komponentenmodells das Attribut `condition` hinzufügen.](/help/implementing/universal-editor/field-types.md#fields)

Bedingungen können mithilfe des [JsonLogic-Schemas definiert werden.](https://jsonlogic.com/) Wenn die Bedingung zutrifft, wird das Feld angezeigt. Wenn die Bedingung nicht zutrifft, wird das Feld ausgeblendet.

>[!BEGINTABS]

>[!TAB Beispielmodell]

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

>[!TAB Bedingung trifft nicht zu]

![Ausgeblendetes Textfeld](assets/hidden.png)

>[!TAB Bedingung trifft zu]

![Eingeblendetes Textfeld](assets/shown.png)

>[!ENDTABS]

### Benutzerdefinierte Vorschau-URLs {#custom-preview-urls}

Sie können eine benutzerdefinierte Vorschau-URL über eine Meta-Konfiguration `urn:adobe:aue:config:preview` angeben, die beim Klicken auf die Schaltfläche **Seite öffnen** in der [oberen rechten Symbolleiste des Editors](/help/sites-cloud/authoring/universal-editor/navigation.md#universal-editor-toolbar) geöffnet wird.

Dies ist besonders nützlich für Anwendungen mit bestimmten Vorschauanforderungen, z. B. bei der Verwendung von [Edge Delivery Services mit WYSIWYG-Authoring.](/help/edge/wysiwyg-authoring/authoring.md)

Fügen Sie dazu einfach die gewünschte Vorschau-URL wie im folgenden Beispiel in ein Meta-Tag der instrumentierten App ein.

```html
<meta name="urn:adobe:aue:config:preview" content="https://wknd.site"/>
```

## Erweitern der Benutzeroberfläche des universellen Editors {#extending}

Als Adobe Experience Cloud-Service kann die Benutzeroberfläche des universellen Editors mit App Builder und Experience Manager erweitert werden.

Benutzeroberflächenerweiterungen sind JavaScript-Anwendungen, die mit Adobe App Builder erstellt wurden und in Benutzeroberflächenanwendungen eingebettet werden können, die unter Unified Shell in Adobe Experience Cloud ausgeführt werden, z. B. im universellen Editor. Sie können Ihre eigenen Schaltflächen und Aktionen zum Kopfzeilenmenü und Eigenschaftenbereich hinzufügen sowie eigene Ereignisse für den universellen Editor erstellen.

Weitere Informationen zu diesen Möglichkeiten finden Sie in den folgenden Ressourcen:

1. [Erweiterbarkeit der Benutzeroberfläche](https://developer.adobe.com/uix/docs/) – Dies ist die Entwicklerdokumentation für die Benutzeroberflächenerweiterung.
1. [Anleitung für die Erweiterung der Benutzeroberfläche](https://developer.adobe.com/uix/docs/guides/) – Schritt-für-Schritt-Anleitung zur Entwicklung Ihrer eigenen Erweiterung
1. [Erweiterungspunkte für den universellen Editor](https://developer.adobe.com/uix/docs/services/aem-universal-editor/) – Dokumentation zu den Erweiterungspunkten spezifisch für den universellen Editor

>[!TIP]
>
>Wenn Sie es vorziehen, anhand von Beispielen zu lernen, sehen Sie sich bitte das folgende Tutorial an: [Tutorial zur Erweiterbarkeit der AEM-Benutzeroberfläche.](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/developing/extensibility/ui/overview) Obwohl der Fokus des Tutorials auf der Erweiterung der Inhaltsfragment-Konsole liegt, ist das Konzept zur Implementierung einer Benutzeroberflächenerweiterung im universellen Editor identisch.

Mit dem [Extension Manager in AEM Sites](https://developer.adobe.com/uix/docs/extension-manager/) können Sie Ihre Erweiterungen auf Instanzbasis aktivieren oder deaktivieren, auf Erweiterungen von Adobe zugreifen, einschließlich der Erweiterungen für den universellen Editor, und vieles mehr.
