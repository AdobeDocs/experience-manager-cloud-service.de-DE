---
title: Komponentendefinition
description: Machen Sie sich mit dem JSON-Vertrag zwischen der Komponentendefinition und dem universellen Editor im Detail vertraut.
feature: Developing
role: Admin, Architect, Developer
exl-id: e1bb1a54-50c0-412a-a8fd-8167c6f47d2b
source-git-commit: afb59345b48b39376b62a13cce8910bc9bc42c38
workflow-type: tm+mt
source-wordcount: '600'
ht-degree: 1%

---

# Komponentendefinition {#component-definition}

Machen Sie sich mit dem JSON-Vertrag zwischen der Komponentendefinition und dem universellen Editor im Detail vertraut.

## Überblick {#overview}

Die `component-definition.json` definiert die Komponenten, die den Inhaltsautoren für das Projekt zur Verfügung stehen. In diesem Dokument wird der Zweck dieser Datei und die Verwendung durch den universellen Editor zur Darstellung der Komponenten zur Seitenerstellung für Ihre Autoren ausführlich erläutert.

>[!TIP]
>
>Einen Überblick über den Inhaltsmodellierungsprozess finden Sie im Dokument [Inhaltsmodellierung für das WYSIWYG-Authoring mit Edge Delivery Services-Projekten](/help/edge/wysiwyg-authoring/content-modeling.md).

>[!TIP]
>
>Sie müssen keine eigene `component-definition.json` von Grund auf neu erstellen. Das Projekt-Textbaustein, den Sie zum Bootstrapping [ Projekts verwenden](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md) enthält eine [voll funktionsfähige `component-definition.json`-Datei](https://github.com/adobe-rnd/aem-boilerplate-xwalk/blob/main/component-definition.json) die Sie an Ihre Anforderungen anpassen können.

## Beispiel für eine Komponentendefinition {#example}

Im Folgenden finden Sie ein vollständiges, aber einfaches `component-definition.json` als Beispiel.

```json
{
  "groups":[
    {
      "title":"General Components",
      "id":"general",
      "components":[
        {
          "title":"Text",
          "id":"text",
          "model": "text",
          "filter": "texts",
          "plugins":{
            "aem":{
              "page":{
                "resourceType":"wknd/components/text",
                "template":{
                  "text":"Default Text",
                  "name":"Text"
                }
              }
            },
            "aem65":{
              "page":{
                "resourceType":"wknd/components/text",
                "template":{
                  "text":"Default Text",
                  "name":"Text"
                }
              }
            }
          }
        }
      ]
    }
  ]
}
```

## `groups` {#groups}

`groups` definiert die Komponentengruppen, die der Autor im universellen Editor sieht, wenn er auf das Symbol **Hinzufügen** im Eigenschaftenbereich des Editors klickt, um [einer Seite eine neue Komponente hinzuzufügen](/help/sites-cloud/authoring/universal-editor/authoring.md#adding-components). Gruppen helfen beim Organisieren der Komponenten. Häufige Gruppen sind **Allgemeine Komponenten** und **Erweiterte Komponenten**.

* `title` wird die textliche Beschreibung der Gruppe definiert, die in der Editor-Benutzeroberfläche angezeigt wird.
* `id` identifiziert die Gruppe eindeutig.

## `components` {#components}

`components` definiert, welche Komponenten zu einer Gruppe gehören.

* `title` definiert die textliche Beschreibung der Komponente, die in der Benutzeroberfläche angezeigt wird.
* `id` identifiziert die Komponente eindeutig.
   * Das [Komponentenmodell](/help/implementing/universal-editor/field-types.md#model-structure) desselben `id` definiert die Felder der Komponente.
   * Da es eindeutig ist, kann es z. B. in einer [Filterdefinition“ verwendet werden](/help/implementing/universal-editor/filtering.md) um zu bestimmen, welche Komponenten zu einem Container hinzugefügt werden können.
* `model` definiert, [Modell](/help/implementing/universal-editor/field-types.md#model-structure) mit der Komponente verwendet wird.
   * Das Modell wird dabei zentral in der Komponentendefinition gepflegt und muss nicht ([ der Instrumentierung) angegeben werden](/help/implementing/universal-editor/field-types.md#instrumentation)
   * Auf diese Weise können Sie Komponenten über Container hinweg verschieben.
* `filter` definiert[ welcher ](/help/implementing/universal-editor/filtering.md) mit der Komponente verwendet werden soll.

## `plugins` {#plugins}

`plugins` definiert, welches Plug-in für die Persistierung der Komponente verantwortlich ist. Zu den gängigen Plug-ins gehören:

* `aem` für AEM as a Cloud Service.
* `aem5` für AEM 6.5.
* `xwalk` für das Authoring mit AEM as a Cloud Service WYSIWYG.

## `page` oder `cf` {#page-cf}

Nachdem die `plugin` definiert wurde, müssen Sie angeben, ob sie seitenbezogen oder fragmentbezogen ist.

* `page` gibt an, dass sich die Komponente auf der aktuellen Seite befindet.
* `cf` gibt an, dass die Komponente mit Inhalten in einem [Inhaltsfragment“ ](/help/assets/content-fragments/content-fragments.md).

### `page` {#page}

Wenn es sich bei der Komponente um Inhalt auf der Seite handelt, können Sie die folgenden Informationen angeben.

* `resourceType` definiert den [Sling](/help/implementing/developing/introduction/sling-cheatsheet.md)-`resourceType`, der zum Rendern der Komponente verwendet wird.
* `template` definiert optionale Schlüssel/Werte, die automatisch in die neu erstellte Komponente geschrieben werden, und definiert, welcher Filter und/oder welches Modell auf die Komponente angewendet werden soll.
   * Nützlich für erklärenden Text, Beispiel- oder Platzhaltertext.

#### `template` {#template}

Durch Bereitstellung optionaler Schlüssel/Wert-Paare können `template` diese automatisch in die neue Komponente schreiben. Darüber hinaus können auch die folgenden optionalen Werte angegeben werden.

### `cf` {#cf}

Wenn sich die Komponente auf Inhalte in einem Inhaltsfragment bezieht, können Sie die folgenden Informationen bereitstellen.

* `name` definiert einen optionalen Namen, der im JCR für die neu erstellte Komponente gespeichert wird.
   * Nur informativ, wird aber in der Benutzeroberfläche nicht so angezeigt, wie die `title` ist.
* `cfModel` definiert das [Inhaltsfragmentmodell](/help/assets/content-fragments/content-fragments-models.md) für die neu erstellte Komponente.
* `cfFolder` definiert, in welchem Ordner das Inhaltsfragment erstellt werden soll.
* `title` definiert den Titel des neuen Inhaltsfragments.
* `description` definiert eine Beschreibung des neuen Inhaltsfragments.
* `template` definiert optionale Schlüssel/Werte, die automatisch in das neu erstellte Inhaltsfragment geschrieben werden.
   * Nützlich für erklärenden Text, Beispiel- oder Platzhaltertext.

### `cf` kann impliziert sein {#cf-implied}

Wenn die Seite [instrumentiert) ist](/help/implementing/universal-editor/getting-started.md#instrument-page) um auf ein Referenzfeld zu verweisen, wird die `cf` angenommen.

```html
<div data-aue-resource="urn:aem:/content" data-aue-type="container" data-aue-prop="field"></div>
```

In diesem Fall wird von `cf` ausgegangen, da der `data-aue-prop` auf ein Referenzfeld verweist. Ohne die `data-aue-prop` geht der universelle Editor von `page` aus, da in diesem Fall die Komponenten nicht über ein Referenzfeld verknüpft sind.

```html
<div data-aue-resource="urn:aem:/content" data-aue-type="container"></div>
```

Komponenten sind lediglich Unterknoten unterhalb der Ressource.
