---
title: Erste Schritte mit dem AEM Forms Edge Delivery Service
description: Handwerkliche perfekte Formen, schnell! ⚡ AEM Forms Edge Delivery doc-basiertes Authoring = Blazing Speed & SEO-freundliche Formulare für glücklichere Benutzer und Suchmaschinen.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: f37a99cd5cbfb745cb591e3be2a46a5f52139cb2
workflow-type: tm+mt
source-wordcount: '792'
ht-degree: 1%

---


# Erstellen eines Formulars im AEM Forms Edge Delivery Service

Im heutigen digitalen Zeitalter ist die Erstellung benutzerfreundlicher Formulare für jedes Unternehmen von entscheidender Bedeutung. Mit AEM Forms Edge Delivery können Sie Formulare mit vertrauten Tools wie Word- oder Google-Dokumenten erstellen.

Diese Formulare senden Daten direkt an eine Microsoft Excel- oder Google Tabellen-Datei, sodass Sie ein dynamisches Ökosystem und robuste APIs von Google Tabellen, Microsoft Excel und Microsoft SharePoint verwenden können, um gesendete Daten einfach zu verarbeiten oder einen bestehenden Geschäftsarbeitsablauf zu initiieren.

## Voraussetzungen

* Sie haben ein Github-Konto.
* Sie haben Zugriff auf Google Tabellen oder Microsoft SharePoint.
* Sie verstehen die Grundlagen von Git, HTML, CSS und JavaScript.
* Sie haben Node und NPM für die lokale Entwicklung installiert.

## Bevor Sie beginnen

* Richten Sie ein Projekt für Edge Delivery Service (EDS) ein und klonen Sie es. Siehe [Entwickler-Tutorial](https://www.aem.live/developer/tutorial) für Details.
* Klonen Sie die [Forms Block-Repository](https://github.com/adobe/afb). Sie enthält den Formularblock, der zum Rendern des Formulars erforderlich ist.

![Erste Schritte mit Edge Delivery Forms](/help/edge/assets/getting-started-with-eds-forms.png)

## Fügen Sie den Formularblock zu Ihrem Edge Delivery Service-Projekt (EDS) hinzu. {#add-forms-block-to-an-eds-project}

Die AEM Forms Edge-Bereitstellung enthält einen Formularblock, mit dem Sie mühelos Formulare erstellen können, um erfasste Daten zu erfassen und zu speichern. So fügen Sie den Formularblock in Ihr Edge Delivery Service-Projekt ein:

1. Navigieren Sie in Ihrer lokalen Entwicklungsumgebung zum Projektordner Ihres Edge Delivery Service (EDS).


   ```Shell
   cd [EDS Project folder]
   ```

1. Erstellen Sie einen Ordner mit dem Namen `form` im EDS-Projektverzeichnis. Beispielsweise im Ordner für das EDS-Projekt mit dem Namen `Portal`erstellen Sie einen Ordner mit dem Namen `form`.

   ```Shell
   mkdir form
   ```


1. Fügen Sie die [Forms Block](https://github.com/adobe/afb/tree/main/blocks/form) -Dateien in den Ordner &quot;form&quot;.

   ```shell
   cp -R <source:path of the form block> <destination: path of the form folder created in the previous step>
   
   For example
   
   cp -R Documents/afb/blocks/form Documents/portal/blocks/
   ```

1. Checken Sie den Ordner &quot;Formular&quot;und die zugrunde liegenden Dateien in Ihr Edge Delivery Service-Projekt auf GitHub ein.

   ```Shell
   git add .
   git commit -m "Added form block"
   git push origin
   ```

   Sie können jetzt ein EDS-Formular wiedergeben.

   >[!NOTE]
   >
   > * Wenn der Build Ihrer Pull-Anforderung/des Projekts fehlschlägt und ein Fehler im Zusammenhang mit dem Import der `franklin-lib.js` Datei, aktualisieren Sie die Importanweisung, um auf die `aem.js` -Datei anstelle der `franklin-lib.js` -Datei.
   > * Sollten Sie auf Linkingfehler stoßen, können Sie diese ignorieren. Um die Linting-Prüfungen zu umgehen, navigieren Sie zur Datei package.json und aktualisieren Sie das Skript &quot;lint&quot;von `"lint": "npm run lint:js && npm run lint:css"` nach `"lint": "echo 'skipping linting for now'"`. Übertragen Sie dann die Änderungen in die Datei package.json .

## Erstellen eines Formulars mit Microsoft Excel oder Google Sheet {#create-a-form-for-an-eds-project}

Es kann hilfreich sein, Website-Entwicklern zu ermöglichen, Formulare zu erstellen und zu wählen, welche Informationen von Website-Besuchern erfasst werden sollen. Anstelle komplexer Prozesse können Autoren ein Formular einfach mithilfe einer Tabelle einrichten. Sie müssen die richtigen Spaltenüberschriften hinzufügen und dann einen Formularblock verwenden, um ihn ohne Probleme auf der Website anzuzeigen. So erstellen Sie ein Formular:

1. Erstellen Sie eine Microsoft Excel-Arbeitsmappe oder ein Google-Blatt an einer beliebigen Stelle im Projektverzeichnis für die AEM Edge-Bereitstellung auf Microsoft SharePoint oder Google Drive.

1. Stellen Sie sicher, dass der AEM Benutzer (z. B. `helix@adobe.com`), die für Ihr Projekt konfiguriert sind, über Bearbeitungsberechtigungen für das Blatt verfügt.

1. Öffnen Sie die von Ihnen erstellte Arbeitsmappe und ändern Sie den Namen des Standardblatts in &quot;shared-default&quot;.

   ![Standard-Arbeitsblatt in &quot;shared-default&quot;umbenennen](/help/edge/assets/rename-sheet-to-helix-default.png)

1. Kopieren Sie den Inhalt der [Kontaktaufnahme mit uns - Tabelle](https://docs.google.com/spreadsheets/d/12jvYjo1a3GOV30IqPY6_7YaCQtUmzWpFhoiOHDcjB28/edit?usp=drive_link) in Ihre eigene Tabelle.

   ![Kontaktaufnahme mit uns - Tabelle](/help/edge/assets/contact-us-form-spreadsheet.png)

1. Verwendung [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) , um das Blatt in der Vorschau anzuzeigen und zu veröffentlichen.

   Bei der Vorschau und Veröffentlichung öffnet der Browser neue Registerkarten, auf denen der Inhalt des Blatts im JSON-Format angezeigt wird. Notieren Sie sich die Live-URL, da sie für die spätere Wiedergabe des Formulars erforderlich ist.

   Das Format der URL ist:

   ```shell
   https://<branch>--<repository>--<owner>.hlx.live/<form>.json
   
   For example, https://main--portal--wkndforms.hlx.live/contact-us.json
   ```

## Vorschau des Formulars mit der Seite &quot;Edge Delivery Service (EDS)&quot; {#add-a-form-to-your-eds-page}

Bis jetzt haben Sie den Formularblock für Ihr EDS-Projekt aktiviert und die Struktur des Formulars vorbereitet. Um das Formular nun in Ihre EDS-Seite einzuschließen und zu rendern, gehen Sie folgendermaßen vor:

1. Wechseln Sie zum Projektverzeichnis für die AEM Edge-Bereitstellung auf Microsoft SharePoint oder Google Drive.

1. Um das Formular einer Seite hinzuzufügen, öffnen Sie die entsprechende Dokumentendatei. Öffnen Sie beispielsweise die Indexdatei.

1. Navigieren Sie zum gewünschten Speicherort im Dokument, dem Sie das Formular hinzufügen möchten.

1. Fügen Sie der Datei einen Baustein mit dem Namen &quot;Formular&quot;hinzu, der dem unten dargestellten ähnelt.

   ![](/help/edge/assets/form-block-in-sites-page-example.png)

   Schließen Sie in der zweiten Zeile die URL, die Sie im vorherigen Abschnitt notiert haben, als Hyperlink ein.

1. Verwendung [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) , um die Seite in der Vorschau anzuzeigen und zu veröffentlichen. Das Formular wird wiedergegeben.

   Hier ist beispielsweise das Formular, das auf der Variablen [Kontaktaufnahme mit uns - Tabelle](https://docs.google.com/spreadsheets/d/12jvYjo1a3GOV30IqPY6_7YaCQtUmzWpFhoiOHDcjB28/edit?usp=drive_link):


   ![Kontakt (EDS-Formular)](/help/edge/assets/eds-form.png)

   Der Formularblock rendert das Formular, kann die Daten jedoch noch nicht akzeptieren. Beim Klicken auf die Senden-Schaltfläche tritt ein Fehler ähnlich dem folgenden auf:

   ![Fehler bei Formularübermittlung](/help/edge/assets/form-error.png)

   [Vorbereiten des Tabellenblattes auf die Datenaufnahme](/help/edge/docs/forms/submit-forms.md). Sie können die Daten an das Tabellenblatt senden, um es darauf vorzubereiten, Daten zu akzeptieren.


## Mehr anzeigen

* [Erstellen und Anzeigen einer Vorschau eines Formulars](/help/edge/docs/forms/create-forms.md)
* [Formular zum Senden von Daten aktivieren](/help/edge/docs/forms/submit-forms.md)
* [Veröffentlichen eines Formulars auf der Siteseite](/help/edge/docs/forms/publish-eds-forms.md)
* [Hinzufügen von Überprüfungen zu Formularfeldern](/help/edge/docs/forms/validate-forms.md)
* [Designs und Formularstil ändern](/help/edge/docs/forms/style-theme-forms.md)