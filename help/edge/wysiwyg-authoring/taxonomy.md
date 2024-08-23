---
title: Verwalten von Taxonomiedaten
description: Erfahren Sie, wie Sie Taxonomiedaten für die Verwendung von Tags mit Ihren AEM mit Edge Delivery Services-Sites verwalten.
role: Admin, Architect, Developer
source-git-commit: f6716611efa3de845ead15048eab89243bdedcc1
workflow-type: tm+mt
source-wordcount: '829'
ht-degree: 7%

---


# Verwalten von Taxonomiedaten {#managing-taxonomy-data}

Erfahren Sie, wie Sie Taxonomiedaten für die Verwendung von Tags mit Ihren AEM mit Edge Delivery Services-Sites verwalten.

## Einführung {#introduction}

Tagging ist eine wichtige Funktion, mit der Sie Ihre Seiten organisieren und verwalten können. Mit der Tagging-Konsole ](/help/sites-cloud/administering/tags.md#tagging-console) in AEM können Sie eine umfangreiche Taxonomie von Tags erstellen, um Ihre Seiten zu organisieren.[

Diese Tags sind nicht nur für Sie und Ihre Autoren bei der Organisation Ihrer Inhalte nützlich, sondern können auch für Ihre Leser nützlich sein. Tags und ihre Taxonomie können in Komponenten auf der Seite verwendet werden, um Ihren Lesern bei der Navigation in Ihren Inhalten zu helfen.

Der universelle Editor funktioniert nur mit den IDs Ihrer Tags. Durch Erstellung einer Taxonomieseite für Ihren Inhalt stellen Sie die Beschreibungen dieser Tags in allen Sprachen für den universellen Editor bereit, damit diese Informationen beim Rendern von Inhalten verwendet werden können.

## Erstellen einer Taxonomieseite {#creating}

Eine Taxonomie wird wie [jede andere Seite in AEM erstellt.](/help/sites-cloud/authoring/sites-console/creating-pages.md)

1. Navigieren Sie zur Konsole [**Sites**.](/help/sites-cloud/authoring/sites-console/introduction.md)

1. Wählen Sie den Ort aus, an dem Sie Ihre Taxonomie erstellen möchten.

1. Tippen oder klicken Sie auf **Erstellen** > **Seite**.

   ![Seite erstellen](assets/taxonomy/create-page.png)

1. Wählen Sie auf der Registerkarte **Vorlage** des Assistenten **Seite erstellen** die Vorlage **Taxonomie** aus und tippen oder klicken Sie auf **Weiter**.

   ![Taxonomy template](assets/taxonomy/taxonomy-template.png)

1. Geben Sie auf der Registerkarte **Eigenschaften** des Assistenten **Seite erstellen** einen aussagekräftigen **Titel** für die Seite ein und verwenden Sie im Feld **Tags** den Tag-Picker](/help/sites-cloud/authoring/sites-console/tags.md), um die Tags oder Namespace auszuwählen, die Sie in Ihre Taxonomie aufnehmen möchten.[

   ![Taxonomieeigenschaften](assets/taxonomy/create-page-wizard-properties.png)

1. Tippen oder klicken Sie auf **Erstellen**.

Die Taxonomieseite wird erstellt. Im Dialogfeld **Erfolg** können Sie auf das Dialogfeld **Fertig** tippen oder klicken, um die Nachricht zu schließen, oder auf **Öffnen** , um die Seite im [Seiteneditor](/help/sites-cloud/authoring/page-editor/introduction.md) zu bearbeiten.

Notieren Sie sich den resultierenden Seitennamen der Taxonomieseite, der in den folgenden Schritten verwendet werden kann.

## Bearbeiten einer Taxonomieseite {#editing}

Sie beginnen mit der Bearbeitung einer Taxonomieseite wie jede andere Seite in AEM.

1. Navigieren Sie zur Konsole [**Sites**.](/help/sites-cloud/authoring/sites-console/introduction.md)

1. Wählen Sie die Taxonomie aus, die Sie bearbeiten möchten.

1. Tippen oder klicken Sie in der Aktionsleiste auf **Bearbeiten** .

1. Der Seiteneditor wird geöffnet und zeigt die Taxonomie an.

   * Die Taxonomieseite ist im Seiteneditor schreibgeschützt.

   ![Taxonomie bearbeiten](assets/taxonomy/edit-page.png)

1. Tippen oder klicken Sie in der Symbolleiste auf das Symbol **Seiteninformationen** und wählen Sie **Eigenschaften öffnen** aus.

   ![Eigenschaften öffnen](assets/taxonomy/open-properties.png)

1. Im Fenster **Seiteneigenschaften** können Sie den Namen der Seite aktualisieren und mithilfe der Tag-Auswahl die in Ihrer Taxonomie enthaltenen Tags und Namespace(s) aktualisieren.

   ![Seiteneigenschaften bearbeiten](assets/taxonomy/edit-properties.png)

1. Tippen oder klicken Sie auf **Speichern und schließen**.

Die im Seiteneditor angezeigte Seite ist schreibgeschützt, da der Inhalt der Taxonomie automatisch aus den ausgewählten Tags und Namespace(en) generiert wird. Sie dienen als Filter für die automatische Generierung des Inhalts der Taxonomie. Daher gibt es keinen Grund, die Seite direkt im Editor zu bearbeiten.

AEM aktualisiert automatisch den Inhalt der Taxonomieseite, wenn Sie die zugrunde liegenden Tags und Namespace(s) aktualisieren. Sie müssen die Taxonomie jedoch nach jeder Änderung [erneut veröffentlichen](#publishing) , um diese Änderungen Ihren Benutzern zur Verfügung zu stellen.

## Aktualisieren von paths.json für die Taxonomie-Veröffentlichung {#paths-json}

Wie beim Verwalten und Veröffentlichen von Tabellendaten für Ihre Edge Delivery Services-Site ](/help/edge/wysiwyg-authoring/tabular-data.md) müssen Sie Ihre `paths.json` -Datei Ihres Projekts aktualisieren, um die Veröffentlichung Ihrer Taxonomiedaten zu ermöglichen.[

1. Öffnen Sie den Stamm Ihres Projekts in GitHub.

1. Tippen oder klicken Sie auf die Datei `paths.json`, um ihre Details zu öffnen, und dann auf das Symbol **Bearbeiten**.

   ![Datei paths.json](assets/taxonomy/paths-json.png)

1. Fügen Sie eine Zeile hinzu, um Ihre neue Taxonomieseite einer `.json` -Ressource zuzuordnen.

   ```json
   {
     "mappings": [
      "/content/<site-name>/:/",
      "/content/<site-name>/<taxonomy-page-name>:/<taxonomy-json-name>.json"
     ]
   }
   ```

   * `<taxonomy-page-name>` muss mit dem Namen der von Ihnen erstellten [Taxonomy-Seite übereinstimmen.](#creating)
   * `<taxonomy-json-name>` kann ein beliebiger gültiger Name sein, den Sie auswählen.

1. Klicken Sie auf **Änderungen bestätigen…**, um die Änderungen an `main` zu speichern.

   * Bestätigen Sie entweder für `main` oder erstellen Sie eine Abruf-Anforderung gemäß Ihrem Prozess.

Dieser Prozess muss nur einmal pro Taxonomieseite durchgeführt werden. Danach können Sie Ihre Taxonomie veröffentlichen.

## Veröffentlichen einer Taxonomie {#publishing}

Eine Taxonomie steht dem universellen Editor oder Ihren Benutzern erst nach deren Veröffentlichung zur Verfügung.

Taxonomieseiten werden wie jede andere Seite von [mithilfe der Symbole **Quick Publish** oder **Veröffentlichung verwalten** in der Symbolleiste veröffentlicht.](/help/sites-cloud/authoring/sites-console/publishing-pages.md)

Sie müssen Ihre Taxonomieseite jedes Mal erneut veröffentlichen, wenn Sie:

* Bearbeiten Sie die Taxonomieseite.
* Bearbeiten Sie die Tags und Namespace(s) Ihrer Taxonomieseite oder fügen Sie sie hinzu.

Wenn Sie eine neue Taxonomieseite erstellen, müssen Sie zunächst [der Datei `paths.json` in Ihrem Projekt eine Zuordnung hinzufügen.](#paths-json)

## Zugreifen auf Taxonomieinformationen {#accessing}

Sobald Ihre Taxonomie veröffentlicht wurde, können ihre Informationen vom universellen Editor genutzt und für Ihre Benutzer sichtbar gemacht werden.

Sie können auf die Taxonomie als JSON-Daten unter der folgenden Adresse zugreifen.

`https://<branch>--<repository>--<owner>.hlx.page/<taxonomy-json-name>.json`

Verwenden Sie den `<taxonomy-json-name>` , den Sie beim Zuordnen Ihrer Taxonomie zur `paths.json` -Datei in Ihrem Projekt definiert haben.[](#paths-json) Die Taxonomiedaten werden wie im folgenden Beispiel als JSON-Daten zurückgegeben.

```json
{
  "total": 3,
  "offset": 0,
  "limit": 3,
  "data": [
    {
      "tag": "default:",
      "title": "Standard Tags"
    },
    {
      "tag": "do-not-translate",
      "title": "Do Not Translate"
    },
    {
      "tag": "translate",
      "title": "Translate"
    }
  ],
  ":type": "sheet"
}
```

Diese JSON-Daten werden automatisch aktualisiert, wenn Sie die Taxonomie aktualisieren und erneut veröffentlichen. Ihre App kann programmgesteuert auf diese Informationen für Ihre Benutzer zugreifen.

[Wenn Sie Tags in mehreren Sprachen verwalten, ](/help/sites-cloud/administering/tags.md#managing-tags-in-different-languages) können Sie auf diese Sprachen zugreifen, indem Sie den ISO2-Sprachcode als Wert eines `sheet=` -Parameters übergeben.
