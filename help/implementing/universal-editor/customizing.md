---
title: Anpassen des universellen Editors
description: Erfahren Sie mehr über die verschiedenen Optionen zum Anpassen des universellen Editors, um die Anforderungen bei der Inhaltserstellung zu unterstützen.
exl-id: 8d6523c8-b266-4341-b301-316d5ec224d7
feature: Developing
role: Admin, Architect, Developer
source-git-commit: cb3cf5ee6bb17c33c118c6463272922e0e212c1a
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 67%

---


# Anpassen des universellen Editors {#customizing}

Erfahren Sie mehr über die verschiedenen Optionen zum Anpassen des universellen Editors, um die Anforderungen bei der Inhaltserstellung zu unterstützen.

>[!TIP]
>
>Der universelle Editor bietet außerdem viele [Erweiterungspunkte](/help/implementing/universal-editor/extending.md), sodass Sie seine Funktionalität entsprechend Ihren Projektanforderungen erweitern können.

## Verwenden von Meta Config-Tags {#meta-tags}

Bestimmte Authoring-Workflows erfordern möglicherweise die Verwendung einiger Funktionen des universellen Editors und nicht anderer. Um diese Anwendungsfälle zu unterstützen, stehen Meta-Tags zur Verfügung, mit denen bestimmte Funktionen oder Schaltflächen des Editors konfiguriert oder deaktiviert werden können.

Verwenden Sie dieses Tag im `<head>` Abschnitt der Seite, um eine oder mehrere Funktionen zu deaktivieren:

```html
<meta name="urn:adobe:aue:config:disable" content="..." />
```

Wenn Sie mehrere Funktionen deaktivieren möchten, stellen Sie eine kommagetrennte Liste von Werten bereit.

Im Folgenden finden Sie die unterstützten Werte für `content`, d. h. die Funktionen, die mit Meta-Tags deaktiviert werden können.

| Inhaltswert | Beschreibung |
|---|---|
| `publish` | Deaktivieren Sie alle [Publishing](/help/sites-cloud/authoring/universal-editor/publishing.md)-Funktionen, d. h. die [Publish](/help/sites-cloud/authoring/universal-editor/navigation.md#publish) und [Unpublish](/help/sites-cloud/authoring/universal-editor/navigation.md#ellipsis) |
| `publish-live` | Live ([) &#x200B;](/help/sites-cloud/authoring/universal-editor/publishing.md) |
| `publish-preview` | Vorschauveröffentlichung deaktivieren (wenn der [Vorschau-Service](/help/sites-cloud/authoring/sites-console/previewing-content.md) verfügbar ist) |
| `unpublish` | Deaktivieren Sie die [Veröffentlichung rückgängig machen](/help/sites-cloud/authoring/universal-editor/publishing.md#unpublishing-content) ([Vorschaufunktion](/help/release-notes/universal-editor/preview.md)) |
| `copy` | Deaktiviert die [Kopieren und Einfügen](/help/sites-cloud/authoring/universal-editor/authoring.md#copy-paste) |
| `duplicate` | Deaktiviert die Schaltfläche [Duplizieren](/help/sites-cloud/authoring/universal-editor/navigation.md#duplicate) |
| `header-open-page` | Deaktiviert die Schaltfläche [Seite öffnen](/help/sites-cloud/authoring/universal-editor/navigation.md#open-page) |

## Ändern des Endpunkts {#custom-endpoint}

Wenn Sie nicht den von Adobe gehosteten Dienst „Universeller Editor“, sondern Ihre eigene gehostete Version verwenden möchten, können Sie dies in einem Meta-Tag festlegen. Weitere Informationen finden Sie im Dokument [Erste Schritte mit dem universellen Editor in AEM](/help/implementing/universal-editor/getting-started.md##configuration-settings).

## Filtern von Komponenten {#filtering-components}

Sie können die zulässigen Komponenten pro Container im universellen Editor mithilfe von Komponentenfiltern einschränken. Weitere Informationen finden unter [&#x200B; Filtern von Komponenten](/help/implementing/universal-editor/filtering.md).

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

Fügen Sie dazu einfach die gewünschte Vorschau-URL wie im folgenden Beispiel in ein Meta-Tag der instrumentierten App ein.

```html
<meta name="urn:adobe:aue:config:preview" content="https://wknd.site"/>
```
