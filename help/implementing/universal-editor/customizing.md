---
title: Anpassen des universellen Editors
description: Erfahren Sie mehr über die verschiedenen Optionen zum Anpassen des universellen Editors, um die Anforderungen Ihrer Inhaltsautoren zu unterstützen.
exl-id: 8d6523c8-b266-4341-b301-316d5ec224d7
feature: Developing
role: Admin, Architect, Developer
source-git-commit: cdad4954b13f5582bebfd604220da90529231ccd
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 81%

---


# Anpassen des universellen Editors {#customizing}

Erfahren Sie mehr über die verschiedenen Optionen zum Anpassen des universellen Editors, um die Anforderungen Ihrer Inhaltsautoren zu unterstützen.

>[!TIP]
>
>Der universelle Editor bietet außerdem viele [Erweiterungspunkte](/help/implementing/universal-editor/extending.md) sodass Sie seine Funktionalität entsprechend Ihren Projektanforderungen erweitern können.

## Deaktivieren der Veröffentlichung {#disable-publish}

Bestimmte Authoring-Workflows erfordern, dass Inhalte vor der Veröffentlichung überprüft werden. In solchen Fällen sollte die Option zur Veröffentlichung für Autorinnen und Autoren nicht verfügbar sein.

Die Schaltfläche **Veröffentlichen** kann daher in einer App vollständig unterdrückt werden, indem die folgenden Metadaten hinzugefügt werden.

```html
<meta name="urn:adobe:aue:config:disable" content="publish"/>
```

## Filtern von Komponenten {#filtering-components}

Sie können die zulässigen Komponenten pro Container im universellen Editor mithilfe von Komponentenfiltern einschränken. Weitere Informationen finden unter [ Filtern von Komponenten](/help/implementing/universal-editor/filtering.md).

## Bedingtes Anzeigen und Ausblenden von Komponenten im Bedienfeld „Eigenschaften“ {#conditionally-hide}

Obwohl eine oder mehrere Komponenten für Ihre Autorinnen und Autoren allgemein verfügbar sein können, kann es in bestimmten Situationen vorkommen, dass dies nicht sinnvoll ist. In solchen Fällen können Sie Komponenten im Bedienfeld „Eigenschaften“ ausblenden, indem Sie den [Feldern des Komponentenmodells](/help/implementing/universal-editor/field-types.md#fields) ein `condition`-Attribut hinzufügen.

Bedingungen können mithilfe des [JsonLogic-Schemas](https://jsonlogic.com/) definiert werden. Wenn die Bedingung zutrifft, wird das Feld angezeigt. Wenn die Bedingung nicht zutrifft, wird das Feld ausgeblendet.

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

## Benutzerdefinierte Vorschau-URLs {#custom-preview-urls}

Sie können eine benutzerdefinierte Vorschau-URL über eine Meta-Konfiguration `urn:adobe:aue:config:preview` angeben, die beim Klicken auf die Schaltfläche **Seite öffnen** in der [oberen rechten Symbolleiste des Editors](/help/sites-cloud/authoring/universal-editor/navigation.md#universal-editor-toolbar) geöffnet wird.

Dies ist besonders nützlich für Anwendungen mit bestimmten Vorschauanforderungen, z. B. bei der [Verwendung von Edge Delivery Services mit WYSIWYG-Authoring](/help/edge/wysiwyg-authoring/authoring.md).

Fügen Sie dazu einfach die gewünschte Vorschau-URL wie im folgenden Beispiel in ein Meta-Tag der instrumentierten App ein.

```html
<meta name="urn:adobe:aue:config:preview" content="https://wknd.site"/>
```
