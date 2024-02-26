---
title: Erste Schritte mit dem AEM Forms Edge Delivery Service
description: Handwerkliche perfekte Formen, schnell! ⚡ AEM Forms Edge Delivery doc-basiertes Authoring = Blazing Speed & SEO-freundliche Formulare für glücklichere Benutzer und Suchmaschinen.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: 4a3ebcf7985253ebca24e90ab57ae7eaf3e924e9
workflow-type: tm+mt
source-wordcount: '980'
ht-degree: 1%

---


# Erstellen eines Formulars im AEM Forms Edge Delivery Service

Im heutigen digitalen Zeitalter ist die Erstellung benutzerfreundlicher Formulare für jedes Unternehmen von entscheidender Bedeutung. Mit AEM Forms Edge Delivery können Sie Formulare mit vertrauten Tools wie Word- oder Google-Dokumenten erstellen.

Diese Formulare senden Daten direkt an eine Microsoft Excel- oder Google Tabellen-Datei, sodass Sie ein dynamisches Ökosystem und robuste APIs von Google Tabellen, Microsoft Excel und Microsoft SharePoint verwenden können, um gesendete Daten einfach zu verarbeiten oder einen bestehenden Geschäftsarbeitsablauf zu initiieren.

AEM Forms Edge Delivery bietet einen Formularblock, mit dem Sie mühelos Formulare erstellen können, um erfasste Daten zu erfassen und zu speichern. Sie können den Formularblock in Ihr AEM EDS-Projekt einbeziehen, um mit der Erstellung eines Formulars zu beginnen. Fangen wir an:


## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie die folgenden Schritte ausgeführt haben:

* Richten Sie das GitHub-Projekt des Edge Delivery Service (EDS) mithilfe AEM Textbausteine ein und klonen Sie das entsprechende GitHub-Repository auf Ihrem lokalen Computer. Siehe [Entwickler-Tutorial](https://www.aem.live/developer/tutorial) für Details. In diesem Dokument wird der lokale Ordner Ihres Edge Delivery Service-Projekts (EDS) als `[EDS Project repository]` .
* Klonen Sie die [Forms Block-Repository](https://github.com/adobe/afb) auf Ihrem lokalen Computer. Es enthält den Code zum Rendern des Formulars auf einer EDS-Webseite. In diesem Dokument wird der lokale Ordner Ihres Forms Block-Repositorys als `[Forms Block repository]`.
* Stellen Sie sicher, dass Sie Zugriff auf Google Tabellen oder Microsoft SharePoint haben.


## Formular erstellen

+++ Schritt 1: Fügen Sie den Formularblock zu Ihrem EDS-Projekt (Edge Delivery Service) hinzu.

Die `Form block` umfasst die Möglichkeit, ein Formular zu einer EDS-Site hinzuzufügen. Der Baustein ist nicht in einem Projekt enthalten, das mit AEM Bausteinvorlage erstellt wurde. So fügen Sie den Formularblock in Ihr Edge Delivery Service-Projekt ein:

1. Navigieren Sie zum `[Forms Block repository]/blocks` Ordner auf Ihrem lokalen Computer und kopieren Sie die `form` Ordner.

1. Navigieren Sie zum `[EDS Project repository]/blocks/` Ordner auf Ihrem lokalen Computer und fügen Sie den `form` Ordner.

1. Checkin `form` Ordner und die zugrunde liegenden Dateien in Ihrem Edge Delivery Service-Projekt auf GitHub.

   Der Formularblock wird Ihrem EDS-Projekt-Repository auf GitHub hinzugefügt. Stellen Sie sicher, dass der GitHub-Build nicht fehlschlägt:

   * Wenn der Fehler &quot;Pfad zum Modul kann nicht aufgelöst werden &quot;&#39;../../scripts/lib-franklin.js&#39;&quot; auftritt, öffnen Sie die `[EDS Project]/blocks/forms/form.js` -Datei. Ersetzen Sie in der Importanweisung die `lib-franklin.js` -Datei mit der `aem.js` -Datei.

   * Sollten Sie auf Linkingfehler stoßen, können Sie diese ignorieren. Um die Linting-Prüfungen zu umgehen, öffnen Sie die `[EDS Project]\package.json` und aktualisieren Sie das Skript &quot;lint&quot;von `"lint": "npm run lint:js && npm run lint:css"` nach `"lint": "echo 'skipping linting for now'"`. Speichern Sie die Datei und übertragen Sie sie in Ihr GitHub-Projekt.

Sie können jetzt ein Formular erstellen und es zu Ihrer Site hinzufügen.

+++

+++ Schritt 2: Erstellen Sie ein Formular mit Microsoft Excel oder Google Sheet.

Anstelle komplexer Prozesse können Sie ein Formular einfach mithilfe einer Tabelle erstellen. Zunächst können Sie die Zeilen- und Spaltenüberschriften zu einem Arbeitsblatt hinzufügen, wobei jede Zeile ein Formularfeld definiert und jede Spaltenüberschrift die Eigenschaften der entsprechenden Formularfelder definiert.

In der folgenden Tabelle definieren Zeilen beispielsweise die Felder für eine `contact us` Formular- und Spaltenüberschrift definiert Eigenschaften der entsprechenden Felder.

![Kontaktaufnahme mit uns - Tabelle](/help/edge/assets/contact-us-form-spreadsheet.png)

So erstellen Sie ein Formular:

1. Öffnen Sie den Ordner AEM Edge-Bereitstellungsprojekt auf Microsoft SharePoint oder Google Drive.

1. Erstellen Sie eine Microsoft Excel-Arbeitsmappe oder ein Google-Blatt an einer beliebigen Stelle im Verzeichnis Ihres AEM Edge-Bereitstellungsprojekts. Erstellen Sie beispielsweise eine Tabelle mit dem Namen `contact-us` im Projektverzeichnis AEM Edge-Bereitstellung auf Google Drive.

1. Stellen Sie sicher, dass das Blatt für AEM Benutzer freigegeben ist (z. B. `helix@adobe.com`) [für Ihr Projekt konfiguriert wurde](https://www.aem.live/docs/setup-customer-sharepoint) und der Benutzer über Bearbeitungsberechtigungen für das Blatt verfügt.

1. Öffnen Sie die von Ihnen erstellte Tabelle und ändern Sie den Namen des Standardblatts in &quot;Standard freigegeben&quot;.

   ![Standard-Arbeitsblatt in &quot;shared-default&quot;umbenennen](/help/edge/assets/rename-sheet-to-shared-default.png)

1. Um die Felder des Formulars hinzuzufügen, fügen Sie die Zeilen- und Spaltenüberschriften zum `shared-default` Arbeitsblatt, wobei jede Zeile ein Formularfeld definiert und jede Spaltenüberschrift die [properties](/help/edge/docs/forms/eds-form-field-properties)) der entsprechenden Formularfelder.

   Um schnell zu beginnen, können Sie den Inhalt der [Kontaktaufnahme mit uns - Tabelle](https://docs.google.com/spreadsheets/d/12jvYjo1a3GOV30IqPY6_7YaCQtUmzWpFhoiOHDcjB28/edit?usp=drive_link) in Ihre Tabelle ein.

   >[!VIDEO](https://video.tv.adobe.com/v/3427468?quality=12&learn=on)

1. Verwendung [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) , um das Blatt in der Vorschau anzuzeigen und zu veröffentlichen.

   ![Verwenden Sie AEM Sidekick, um eine Vorschau anzuzeigen und das Blatt zu veröffentlichen.](/help/edge/assets/preview-form.png)

   Bei der Vorschau und Veröffentlichung öffnet der Browser neue Registerkarten, auf denen der Inhalt des Blatts im JSON-Format angezeigt wird. Notieren Sie sich die Live-URL, da sie für die spätere Wiedergabe des Formulars erforderlich ist.

   Das Format der URL ist:

   ```JSON
   https://<branch>--<repository>--<owner>.hlx.live/<form>.json
   
   For example, https://main--portal--wkndforms.hlx.live/contact-us.json
   ```

+++

+++ Schritt 3: Anzeigen einer Vorschau des Formulars mit Ihrer Edge Delivery Service-Seite (EDS).


Bis jetzt haben Sie den Formularblock zu Ihrem EDS-Projekt hinzugefügt und die Struktur des Formulars vorbereitet. Nun können Sie eine Vorschau des Formulars anzeigen:

1. Wechseln Sie zu Ihrem Microsoft SharePoint- oder Google Drive-Konto und öffnen Sie das Projektverzeichnis AEM Edge-Bereitstellung .

1. Öffnen Sie eine Dokumentdatei, um das Formular darin einzubetten. Öffnen Sie beispielsweise die Indexdatei. Sie können auch eine neue Dokumentendatei erstellen.

1. Navigieren Sie zum gewünschten Speicherort im Dokument, dem Sie das Formular hinzufügen möchten.

1. Fügen Sie der Datei einen Baustein mit dem Namen &quot;Formular&quot;hinzu, der dem unten dargestellten ähnelt.

   ![](/help/edge/assets/form-block-in-sites-page-example.png)

   Schließen Sie in der zweiten Zeile die URL ein, die Sie im vorherigen Abschnitt als Hyperlink aufgezeichnet haben. Verwenden Sie die Vorschau-URL (.page-URL) für Entwicklungs- oder Testzwecke oder die Veröffentlichungs-URL (.live) für die Produktion.

   >[!IMPORTANT]
   >
   >
   > Stellen Sie sicher, dass die URL per Hyperlink anstatt als Nur-Text angezeigt wird.


1. Verwendung [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) um eine Vorschau der Seite anzuzeigen. Auf der Seite wird nun das Formular angezeigt.

   Hier ist beispielsweise das Formular, das auf der Variablen [Kontaktaufnahme mit uns - Tabelle](https://docs.google.com/spreadsheets/d/12jvYjo1a3GOV30IqPY6_7YaCQtUmzWpFhoiOHDcjB28/edit?usp=drive_link):


   ![Beispiel-EDS-Formular](/help/edge/assets/eds-form.png)

   Füllen Sie nun das Formular aus und klicken Sie auf die Senden-Schaltfläche. Es tritt ein Fehler ähnlich dem folgenden auf, da die Tabelle noch nicht für die Annahme der Daten konfiguriert ist.

   ![Fehler bei Formularübermittlung](/help/edge/assets/form-error.png)

+++


## Nächster Schritt

[Tabellenkalkulation vorbereiten](/help/edge/docs/forms/submit-forms.md) , um Daten bei der Formularübermittlung zu akzeptieren.



## Mehr anzeigen

* [Formularfeldeigenschaften](/help/edge/docs/forms/eds-form-field-properties)
* [Erstellen und Anzeigen einer Vorschau eines Formulars](/help/edge/docs/forms/create-forms.md)
* [Formular zum Senden von Daten aktivieren](/help/edge/docs/forms/submit-forms.md)
* [Veröffentlichen eines Formulars auf der Siteseite](/help/edge/docs/forms/publish-eds-forms.md)
* [Hinzufügen von Überprüfungen zu Formularfeldern](/help/edge/docs/forms/validate-forms.md)
* [Designs und Formularstil ändern](/help/edge/docs/forms/style-theme-forms.md)
