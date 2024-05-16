---
title: Anpassen und Erweitern des universellen Editors
description: Erfahren Sie mehr über die verschiedenen Erweiterungspunkte und anderen Funktionen, mit denen Sie die Benutzeroberfläche des universellen Editors anpassen können, um die Anforderungen Ihrer Inhaltsautorinnen und Inhaltsautoren zu unterstützen.
exl-id: 8d6523c8-b266-4341-b301-316d5ec224d7
source-git-commit: bdd67fb383bf20399eacaf9b9c086ea8468ea742
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 50%

---


# Anpassen und Erweitern des universellen Editors {#customizing-extending}

Erfahren Sie mehr über die verschiedenen Erweiterungspunkte und anderen Funktionen, mit denen Sie das Inhaltserstellungserlebnis des universellen Editors anpassen können, um die Anforderungen Ihrer Inhaltsautorinnen und Inhaltsautoren zu unterstützen.

## Überblick {#overview}

Der universelle Editor ermöglicht zwei Arten der Anpassung an die Anforderungen Ihres Projekts.

* [Anpassen des universellen Editors](#customizing) - Die Standardfunktionalität des universellen Editors kann über verschiedene Anpassungskonfigurationen angepasst werden.
* [Erweitern der Benutzeroberfläche des universellen Editors](#extending) - Die Benutzeroberfläche des universellen Editors kann auch mit dem App Builder erweitert werden, um die Anforderungen Ihrer Projekte zu erfüllen.

Beide Typen werden in den folgenden Abschnitten beschrieben.

## Anpassen des universellen Editors {#customizing}

Der universelle Editor bietet mehrere integrierte Optionen, um seine Funktionen anzupassen.

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

### Bedingtes Anzeigen und Ausblenden von Komponenten in der Eigenschaftenleiste {#conditionally-hide}

Obwohl eine oder mehrere Komponenten allgemein für Ihre Autorinnen und Autoren verfügbar sein können, kann es in bestimmten Situationen vorkommen, dass dies nicht sinnvoll ist. In solchen Fällen können Sie Komponenten in der Eigenschaftenleiste ausblenden, indem Sie ein Attribut `condition` zu den Feldern [ des Komponentenmodells hinzufügen.](/help/implementing/universal-editor/field-types.md#fields)

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

>[!TAB Bedingung falsch]

![Ausgeblendetes Textfeld](assets/hidden.png)

>[!TAB Bedingung wahr]

![Eingeblendetes Textfeld](assets/shown.png)

>[!ENDTABS]

## Erweitern der Benutzeroberfläche des universellen Editors {#extending}

Als Adobe Experience Cloud-Dienst kann die Benutzeroberfläche des universellen Editors mit dem App Builder und dem Experience Manager erweitert werden.

UI-Erweiterungen sind JavaScript-Anwendungen, die mit Adobe App Builder erstellt wurden und in Benutzeroberflächenanwendungen eingebettet werden können, die unter der einheitlichen Adobe Experience Cloud-Shell ausgeführt werden, z. B. im universellen Editor. Sie können Ihre eigenen Schaltflächen und Aktionen zum Kopfzeilenmenü und zur Eigenschaftenleiste hinzufügen und eigene Ereignisse für den universellen Editor erstellen.

Weitere Informationen zu diesen Möglichkeiten finden Sie in den folgenden Ressourcen:

1. [UI-Erweiterung](https://developer.adobe.com/uix/docs/) - Dies ist die Entwicklerdokumentation für die UI-Erweiterung.
1. [Handbücher für die Benutzeroberflächen-Erweiterbarkeit](https://developer.adobe.com/uix/docs/guides/) - Schrittweise Anweisungen zur Entwicklung Ihrer eigenen Erweiterung
1. [Erweiterungspunkte für den universellen Editor](https://developer.adobe.com/uix/docs/services/aem-universal-editor/) - Dokumentation zu universellen Editor-spezifischen Erweiterungspunkten

>[!TIP]
>
>Wenn Sie es vorziehen, anhand von Beispielen zu lernen, lesen Sie bitte den Abschnitt [Tutorial zur AEM Benutzeroberflächenerweiterbarkeit.](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/developing/extensibility/ui/overview) Obwohl es sich auf die Erweiterung der Inhaltsfragment-Konsole konzentriert, sind die Konzepte zur Implementierung einer UI-Erweiterung im universellen Editor identisch.

[Verwenden von Extension Manager in AEM Sites,](https://developer.adobe.com/uix/docs/extension-manager/) Sie können Ihre Erweiterungen auf Instanzbasis aktivieren oder deaktivieren, auf Erstanbietererweiterungen zugreifen, einschließlich der Erweiterungen für den universellen Editor und vieles mehr.
