---
title: Komponentendefinition
description: Machen Sie sich mit dem JSON-Vertrag zwischen der Komponentendefinition und dem universellen Editor im Detail vertraut.
feature: Developing
role: Admin, Architect, Developer
exl-id: e1bb1a54-50c0-412a-a8fd-8167c6f47d2b
source-git-commit: b4e61ec6abcaf73119f8963d72317759b2bd7c76
workflow-type: ht
source-wordcount: '611'
ht-degree: 100%

---

# Komponentendefinition {#component-definition}

Machen Sie sich mit dem JSON-Vertrag zwischen der Komponentendefinition und dem universellen Editor im Detail vertraut.

## Überblick {#overview}

Die Datei `component-definition.json` definiert die Komponenten, die den Inhaltsautorinnen und -autoren für das Projekt zur Verfügung stehen. In diesem Dokument wird der Zweck dieser Datei und seine Verwendung durch den universellen Editor zur Darstellung der Komponenten zur Seitenerstellung für Autorinnen und Autoren ausführlich erläutert.

>[!TIP]
>
>Einen Überblick über den Inhaltsmodellierungsprozess finden Sie im Dokument zur [Inhaltsmodellierung für das WYSIWYG-Authoring mit Edge Delivery Services-Projekten.](https://www.aem.live/developer/component-model-definitions)

>[!TIP]
>
>Sie müssen keine eigene `component-definition.json`-Datei von Grund auf neu erstellen. Der Projekt-Textbaustein, den Sie zum [Bootstrapping Ihres Projekts](https://www.aem.live/developer/ue-tutorial)verwenden, enthält eine [voll funktionsfähige `component-definition.json`-Datei](https://github.com/adobe-rnd/aem-boilerplate-xwalk/blob/main/component-definition.json), die Sie an Ihre Anforderungen anpassen können.

## Beispiel einer Komponentendefinition {#example}

Im Folgenden finden Sie eine vollständige, aber einfache `component-definition.json` als Beispiel.

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

`groups` definiert die Komponentengruppen, die die Autorin bzw. der Autor im universellen Editor sieht, wenn sie bzw. er auf das Symbol **Hinzufügen** im Eigenschaftenbereich des Editors klickt, um [einer Seite eine neue Komponente hinzuzufügen](/help/sites-cloud/authoring/universal-editor/authoring.md#adding-components). Gruppen helfen beim Organisieren der Komponenten. Häufige Gruppen sind **Allgemeine Komponenten** und **Erweiterte Komponenten**.

* `title` definiert die Textbeschreibung der Gruppe, die in der Benutzeroberfläche des Editors angezeigt wird.
* `id` identifiziert die Gruppe eindeutig.

## `components` {#components}

`components` definiert, welche Komponenten zu einer Gruppe gehören.

* `title` definiert die Textbeschreibung der Komponente, die in der Benutzeroberfläche angezeigt wird.
* `id` identifiziert die Komponente eindeutig.
   * Das [Komponentenmodell](/help/implementing/universal-editor/field-types.md#model-structure) derselben `id` definiert die Felder der Komponente.
   * Da es eindeutig ist, kann es z. B. in einer [Filterdefinition](/help/implementing/universal-editor/filtering.md) verwendet werden, um zu bestimmen, welche Komponenten einem Container hinzugefügt werden können.
* `model` definiert, welches [Modell](/help/implementing/universal-editor/field-types.md#model-structure) mit der Komponente verwendet wird.
   * Das Modell wird dabei zentral in der Komponentendefinition verwaltet und muss nicht in [der Instrumentierung angegeben werden](/help/implementing/universal-editor/field-types.md#instrumentation).
   * Dies ermöglicht es Ihnen, Komponenten über Container hinweg zu verschieben.
* `filter` definiert welcher[Filter](/help/implementing/universal-editor/filtering.md) mit der Komponente verwendet werden soll.

## `plugins` {#plugins}

`plugins` definiert, welches Plug-in für das Persistieren der Komponente verantwortlich ist. Häufige Plug-ins sind:

* `aem` für [AEM as a Cloud Service.](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service)
* `aem65` für [AEM 6.5.](https://experienceleague.adobe.com/de/docs/experience-manager-65) und [AEM 6.5 LTS](https://experienceleague.adobe.com/de/docs/experience-manager-65-lts)
* `xwalk` für [Authoring mit AEM Sites für Edge Delivery Services.](https://www.aem.live/developer/ue-tutorial)

## `page` oder `cf` {#page-cf}

Nachdem `plugin` definiert wurde, müssen Sie angeben, ob es seitenbezogen oder fragmentbezogen ist.

* `page` gibt an, dass sich die Komponente auf der aktuellen Seite befindet.
* `cf` gibt an, dass die Komponente sich auf Inhalten in einem [Inhaltsfragment](/help/assets/content-fragments/content-fragments.md) bezieht.

### `page` {#page}

Wenn es sich bei der Komponente um Inhalt auf der Seite handelt, können Sie die folgenden Informationen angeben.

* `resourceType` definiert den [Sling](/help/implementing/developing/introduction/sling-cheatsheet.md)-`resourceType`, der zum Rendern der Komponente verwendet wird.
* `template` definiert optionale Schlüssel/Werte, die automatisch in die neu erstellte Komponente geschrieben werden, und definiert, welcher Filter und/oder welches Modell auf die Komponente angewendet werden soll.
   * Nützlich für Erklärungs-, Beispiel- oder Platzhaltertext.

#### `template` {#template}

Durch Bereitstellung optionaler Schlüssel-Wert-Paare kann `template` diese automatisch in die neue Komponente schreiben. Darüber hinaus können auch die folgenden optionalen Werte angegeben werden.

### `cf` {#cf}

Wenn sich die Komponente auf Inhalte in einem Inhaltsfragment bezieht, können Sie die folgenden Informationen bereitstellen.

* `name` definiert einen optionalen Namen, der im JCR für die neu erstellte Komponente gespeichert wird.
   * Nur informativ und wird in der Benutzeroberfläche im Gegensatz zu `title` normalerweise nicht angezeigt.
* `cfModel` definiert das [Inhaltsfragmentmodell](/help/assets/content-fragments/content-fragments-models.md) für die neu erstellte Komponente.
* `cfFolder` definiert, in welchem Ordner das Inhaltsfragment erstellt werden soll.
* `title` definiert den Titel des neuen Inhaltsfragments.
* `description` definiert eine Beschreibung des neuen Inhaltsfragments.
* `template` definiert optionale Schlüssel/Werte, die automatisch in das neu erstellte Inhaltsfragment geschrieben werden.
   * Nützlich für Erklärungs-, Beispiel- oder Platzhaltertext.

### `cf` kann impliziert sein {#cf-implied}

Wenn die Seite so [instrumentiert](/help/implementing/universal-editor/getting-started.md#instrument-page), dass sie auf ein Referenzfeld verweist, wird `cf` angenommen.

```html
<div data-aue-resource="urn:aem:/content" data-aue-type="container" data-aue-prop="field"></div>
```

In diesem Fall wird `cf` angenommen, da `data-aue-prop` auf ein Referenzfeld verweist. Ohne `data-aue-prop` nimmt der universelle Editor `page` an, da in diesem Fall die Komponenten nicht über ein Referenzfeld verknüpft sind.

```html
<div data-aue-resource="urn:aem:/content" data-aue-type="container"></div>
```

Komponenten sind lediglich Unterknoten unter der Ressource.
