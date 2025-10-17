---
title: Anpassen des universellen Editors
description: Erfahren Sie mehr über die verschiedenen Optionen zum Anpassen des universellen Editors, um die Anforderungen bei der Inhaltserstellung zu unterstützen.
exl-id: 8d6523c8-b266-4341-b301-316d5ec224d7
feature: Developing
role: Admin, Architect, Developer
source-git-commit: a72b4b7921a1a379bcd089682c02b0519fe3af8a
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 78%

---


# Anpassen des universellen Editors {#customizing}

Erfahren Sie mehr über die verschiedenen Optionen zum Anpassen des universellen Editors, um die Anforderungen bei der Inhaltserstellung zu unterstützen.

>[!TIP]
>
>Der universelle Editor bietet außerdem viele [Erweiterungspunkte](/help/implementing/universal-editor/extending.md), sodass Sie seine Funktionalität entsprechend Ihren Projektanforderungen erweitern können.

## Deaktivieren der Veröffentlichung {#disable-publish}

Bestimmte Authoring-Workflows erfordern, dass Inhalte vor der Veröffentlichung überprüft werden. In solchen Fällen sollte die Option zur Veröffentlichung für Autorinnen und Autoren nicht verfügbar sein.

Die Schaltfläche **Veröffentlichen** kann daher in einer App vollständig unterdrückt werden, indem die folgenden Metadaten hinzugefügt werden.

```html
<meta name="urn:adobe:aue:config:disable" content="publish"/>
```

## Deaktivieren der Veröffentlichung in der Vorschau {#publish-preview}

Bestimmte Authoring-Workflows schließen möglicherweise die Veröffentlichung im [Vorschau-Service](/help/sites-cloud/authoring/sites-console/previewing-content.md) (falls verfügbar) aus.

Die Schaltfläche **Vorschau** im Fenster „Veröffentlichen“ kann daher in einer App vollständig unterdrückt werden, indem die folgenden Metadaten hinzugefügt werden.

```html
<meta name="urn:adobe:aue:config:disable" content="publish-preview"/>
```

## Deaktivieren der Veröffentlichung in Live Copy {#publish-live}

Bestimmte Authoring-Workflows verhindern möglicherweise die Veröffentlichung im Live-Service.

Die **Live**-Option im Veröffentlichungsfenster kann daher in einer App vollständig unterdrückt werden, indem die folgenden Metadaten hinzugefügt werden.

```html
<meta name="urn:adobe:aue:config:disable" content="publish-live"/>
```

## Deaktivieren der Veröffentlichung {#unpublish}

Bestimmte Authoring-Workflows erfordern einen Genehmigungsprozess, bevor Inhalte veröffentlicht werden können. In solchen Fällen sollte die Option zum Rückgängigmachen der Veröffentlichung für keine Autorin bzw. keinen Autor verfügbar sein.

Die Schaltfläche **Veröffentlichung aufheben** kann daher in einer App vollständig unterdrückt werden, indem die folgenden Metadaten hinzugefügt werden.

```html
<meta name="urn:adobe:aue:config:disable" content="unpublish"/>
```

## Deaktivieren der Seitenöffnung {#open-page}

Die Schaltfläche **Seite öffnen** kann in einer App vollständig unterdrückt werden, indem die folgenden Metadaten hinzugefügt werden.

```html
<meta name="urn:adobe:aue:config:disable" content="header-open-page" />
```

## Deaktivieren der Schaltfläche „Duplizieren“ {#duplicate-button}

Für bestimmte Authoring-Workflows muss möglicherweise die Möglichkeit der Inhaltsautorin bzw. des Inhaltsautors eingeschränkt werden, Komponenten zu duplizieren. Sie können das Symbol [Duplizieren](/help/sites-cloud/authoring/universal-editor/navigation.md#duplicate) deaktivieren, indem Sie die folgenden Metadaten hinzufügen.

```html
<meta name="urn:adobe:aue:config:disable" content="duplicate"/>
```

## Deaktivieren von Kopieren und Einfügen {#copy-paste}

Bestimmte Authoring-Workflows müssen möglicherweise die Fähigkeit des Inhaltsautors einschränken, Komponenten zu kopieren und einzufügen. Sie können die Symbole [Kopieren und Einfügen](/help/sites-cloud/authoring/universal-editor/authoring.md#copy-paste) deaktivieren, indem Sie die folgenden Metadaten hinzufügen.

```html
<meta name="urn:adobe:aue:config:disable" content="copy"/>
```

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
