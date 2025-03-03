---
title: Erste Schritte mit Edge Delivery Services für AEM Forms – Entwickler-Tutorial
description: In diesem Tutorial lernen Sie alles über ein neues Adobe Experience Manager (AEM) Forms-Projekt. In zehn bis zwanzig Minuten haben Sie Ihre eigenen Formulare erstellt.
feature: Edge Delivery Services
exl-id: bb7e93ee-0575-44e1-9c5e-023284c19490
role: Admin, Architect, Developer
source-git-commit: 744f505c8e97b6ca6947b685ddb1eba41b370cfa
workflow-type: tm+mt
source-wordcount: '1656'
ht-degree: 98%

---

# Erste Schritte – Entwickler-Tutorial

Im heutigen digitalen Zeitalter ist die Erstellung benutzerfreundlicher Formulare für jedes Unternehmen schlicht unverzichtbar. Mit Edge Delivery Services für AEM Forms können Sie Formulare mit vertrauten Tools wie Google Docs und Microsoft Office erstellen.

Diese Formulare senden Daten direkt an eine Microsoft Excel- oder Google Tabellen-Datei, sodass Sie ein dynamisches Ökosystem und robuste APIs von Google Tabellen, Microsoft Excel und Microsoft SharePoint verwenden können, um die übermittelten Daten einfach zu verarbeiten oder einen bestehenden Business-Workflow zu initiieren.

AEM Forms bietet einen Bock, der als adaptiver Formularblock bezeichnet wird und mit dem Sie mühelos Formulare erstellen können, um aufgenommene Daten zu erfassen und zu speichern. Sie können [ein neues, mit dem adaptiven Formularblock vorkonfiguriertes AEM-Projekt erstellen](#create-a-new-aem-project-pre-configured-with-adaptive-forms-block) <!--or [add the Adaptive Forms Block to an existing AEM project](#add-adaptive-forms-block-to-your-existing-aem-project)-->.

Dieses AEM Forms-Tutorial führt Sie durch das Erstellen, Anzeigen einer Vorschau und Veröffentlichen Ihres eigenen benutzerdefinierten Formulars mit einem neuen Adobe Experience Manager (AEM) Forms-Projekt.

## Voraussetzungen

* Sie verfügen über ein GitHub-Konto und sind mit den Git-Grundlagen vertraut.
* Sie verfügen über ein Google- oder Microsoft SharePoint-Konto.
* Sie sind mit den Grundlagen von HTML, CSS und JavaScript vertraut.
* Sie haben Node/npm für die lokale Entwicklung installiert.

**Hinweis:** In diesem Tutorial werden macOS, Chrome und Visual Studio Code verwendet. Während sich die Schritte für andere Setups anpassen lassen, können sich die Screenshots und spezifischen Elemente der Benutzeroberfläche je nach Betriebssystem, Browser und Code-Editor unterscheiden.


## Erstellen eines neuen, mit adaptivem Formularblock vorkonfigurierten AEM-Projekt

Die AEM Forms-Bausteinvorlage ermöglicht einen schnellen Einstieg in ein AEM-Projekt, das mit dem adaptiven Formularblock vorkonfiguriert ist. Dies ist die schnellste und einfachste Methode, AEM Best Practices zu befolgen und direkt mit der Formularerstellung zu beginnen.

### Erste Schritte mit der AEM Forms-Baustein-Repository-Vorlage

1. Erstellen Sie ein GitHub-Repository für Ihr AEM-Projekt. So erstellen Sie ein Repository:
   1. Navigieren Sie zu [https://github.com/adobe-rnd/aem-boilerplate-forms](https://github.com/adobe-rnd/aem-boilerplate-forms).

      ![AEM Forms-Bausteinvorlage](/help/edge/assets/aem-forms-boilerplate.png)
   1. Klicken Sie auf **Use this template** (Diese Vorlage verwenden) und wählen Sie die Option **Create a new repository** (Neues Repository erstellen) aus. Der Bildschirm zum Erstellen eines neuen Repositorys wird geöffnet.

      ![Erstellen eines neuen Repositorys mithilfe der AEM Forms-Bausteinvorlage](/help/edge/assets/create-new-repository-using-aem-forms-boilerplate.png)

   1. Wählen Sie im Bildschirm zum Erstellen eines neuen Repositorys die **verantwortliche Person** aus und geben Sie den **Repository-Namen** an. Adobe empfiehlt, das Repository als **öffentlich** festzulegen. Wählen Sie daher die Option **Public** (öffentlich) aus und klicken Sie auf **Create Repository** (Repository erstellen).

   ![Festlegen des Repositorys als öffentlich](/help/edge/assets/create-a-new-repo-keep-it-public.png)


1. Installieren Sie die AEM Code Sync GitHub App in Ihrem Repository. So installieren Sie sie:
   1. Navigieren Sie zu [https://github.com/apps/aem-code-sync/installations/new](https://github.com/apps/aem-code-sync/installations/new).
   1. Wählen Sie im Bildschirm zum Installieren der AEM-Code-Synchronisierung die Option **Only select Repositories** (Nur ausgewählte Repositorys) und dann das neu erstellte Repository aus. Klicken Sie auf „Speichern“.

   ![Festlegen des Repositorys als öffentlich](/help/edge/assets/install-aem-code-sync-app-for-your-repo.png)

   >[!NOTE]
   >
   >
   > Wenn Sie GitHub Enterprise mit IP-Filterung verwenden, können Sie die folgende IP zur Zulassungsliste hinzufügen: 3.227.118.73

   Herzlichen Glückwunsch! Sie haben eine neue Website auf `https://<branch>--<repo>--<owner>.aem.page/`.

   * `<branch>` bezieht sich auf die Verzweigung Ihres GitHub-Repositorys.
   * `<repository>` bezeichnet Ihr GitHub-Repository.
   * `<owner>` bezieht sich auf den Benutzernamen Ihres GitHub-Kontos, das Ihr GitHub-Repository hostet.

   Wenn beispielsweise der Name der Verzweigung `main`, das Repository `wefinance` und die verantwortliche Person `wkndforms` lauten, wird die Website ausgeführt unter: `https://main--wefinance--wkndforms.aem.page`
&lt;!--(https://main--wefinance--wkndform.aem.page)-->

### Verknüpfen Ihrer eigenen Inhaltsquelle

<!--Your newly created GitHub repository points to [example content stored in a Google Drive folder](https://drive.google.com/drive/folders/1bvjfi6TqpYA7DvbX6kKc-m7FgHuJ4RUQ). This read-only content provides a great starting point for your forms. Feel free to copy it into your own Google Drive and customize it to fit your needs.

![Sample Content on Google Drive](/help/edge/assets/folder-with-sample-content.png)-->

Kopieren des Beispielinhalts in Ihren eigenen Inhaltsordner und Verweisen Ihres GitHub-Repositorys auf Ihren eigenen Inhaltsordner:

1. Erstellen Sie einen neuen Ordner speziell für Ihren AEM-Inhalt in Google Drive oder Microsoft SharePoint. In diesem Dokument wird ein Ordner verwendet, der in Microsoft SharePoint erstellt wurde.

1. Geben Sie den Ordner für die Benutzerin bzw. den Benutzer von Adobe Experience Manager frei (forms@adobe.com).

   ![SharePoint: Verwenden der Option „Zugriff verwalten“, um Ordner für die AEM-Benutzerin bzw. den Benutzer freizugeben](/help/edge/assets/share-folder-with-aem-user.png)

   ![Google Drive: Verwenden der Option „Zugriff verwalten“, um Ordner für die AEM-Benutzerin bzw. den Benutzer freizugeben](/help/edge/assets/share-google-drive-folder.png)


   Stellen Sie sicher, dass Sie der Adobe Experience Manager-Benutzerin bzw. dem -Benutzer Bearbeitungsrechte für den Ordner zugewiesen haben.

   ![Sharepoint: Freigeben des Ordners für die AEM-Benutzerin bzw. den AEM-Benutzer und Bereitstellen von Bearbeitungsrechten](/help/edge/assets/share-folder-with-aem-user-provide-editing-access.png){width=50%}

   ![Google Drive: Freigeben des Ordners für die AEM-Benutzerin bzw. den AEM-Benutzer und Bereitstellen von Bearbeitungsrechten](/help/edge/assets/add-aem-user-google-folder.png){width=50%}

1. Kopieren Sie den [Beispielinhalt](/help/edge/assets/wefinance1.zip) in Ihren Ordner. So kopieren Sie ihn:

   1. Entpacken Sie den heruntergeladenen Ordner und kopieren Sie den Inhalt.

      ![Herunterladen von Beispielinhalt](/help/edge/assets/download-sample-content.png)

      Die Dateien `nav` und `footer` definieren das grundlegende Layout Ihrer Seiten und ändern sich im gesamten Projekt nur selten. Sie haben auch eine bestimmte Struktur, die sich von den meisten anderen Inhaltsdateien unterscheidet. Indem Sie sich diese Dateien ansehen, werden Sie ein Gefühl dafür bekommen, wie Inhalte in AEM Projekten organisiert werden.


   1. Laden Sie diese Dateien in den Microsoft SharePoint- oder Google Drive-Ordner hoch.

      ![Beispielinhalt auf Google Drive](/help/edge/assets/upload-sample-files-to-your-content-folder.png)

      Stellen Sie sicher, dass Sie das Blatt `enquiry` aus dem Beispielinhalt in Ihren Ordner auf Google Drive oder Microsoft SharePoint kopieren. Es enthält die Struktur für ein Beispielformular.

1. Nachdem Sie Ihren Inhaltsordner eingerichtet haben, ist es an der Zeit, ihn mit Ihrem Projekt auf GitHub zu verknüpfen, das Sie zuvor mit dem AEM Forms-Textbaustein erstellt haben. So richten Sie die Verbindung ein:

   1. Wechseln Sie zum GitHub-Repository, das Sie zuvor mit dem AEM Forms-Textbaustein erstellt haben.
   1. Öffnen Sie `fstab.yaml` zur Bearbeitung.
   1. Ersetzen Sie die vorhandene Referenz durch den Pfad zum Ordner, den Sie für die AEM-Benutzerin bzw. den AEM-Benutzer freigegeben haben (forms@adobe.com).

      ![Beispielinhalt auf Google Drive](/help/edge/assets/replace-path-in-fstab-yaml-with-your-content-folder.png)


      Wenn Sie Microsoft SharePoint verwenden, verwendet der Ordnerpfad das folgende Format:

      ```HTML
      https://<tenant>.SharePoint.com/sites/<sp-site>/Shared%20Documents/<folder-name>
      ```

      Zum Beispiel:

      ```HTML
      https://adobe.SharePoint.com/sites/wkndforms/Shared%20Documents/wefinance
      ```

      Weitere Informationen zum Verwalten von Dateien in Microsoft SharePoint finden Sie unter [Verwenden von Adobe SharePoint](https://www.aem.live/docs/setup-customer-sharepoint).


   1. Übergeben Sie die aktualisierte Datei `fsatb.yaml`, sobald Sie die Referenz aktualisiert haben und alles gut aussieht. Wenn Build-Probleme auftreten, lesen Sie [Beheben von Build-Problemen in GitHub](#troubleshooting-github-build-issues).

      ![Übergeben der aktualisierten Datei fsatab.yaml](/help/edge/assets/commit-updated-fstab-yaml.png)

      Dadurch wird Ihr Inhaltsordner mit Ihrer Website verbunden. Nach der Aktualisierung der Referenz treten möglicherweise anfänglich Fehler vom Typ „404 nicht gefunden“ auf. Dies liegt daran, dass Ihre Inhalte noch nicht in der Vorschau angezeigt wurden. Im nächsten Abschnitt wird erläutert, wie Sie mit der Bearbeitung und Vorschau Ihres Inhalts beginnen können.



### Vorschau und Veröffentlichen Ihres Inhalts

Nach Abschluss des letzten Schritts ist Ihre neue Inhaltsquelle zwar nicht leer, sie wird jedoch erst auf Ihrer Website sichtbar, wenn sie in die Vorschau- oder Live-Phasen weitergeleitet wird. Derzeit kann dies zu 404-Fehlern führen.

So zeigen Sie nicht veröffentlichte Inhalte in einer Vorschau an:

1. Installieren Sie die Chrome-Erweiterung [AEM Sidekick](https://chrome.google.com/webstore/detail/helix-sidekick-beta/ccfggkjabjahcjoljmgmklhpaccedipo).

   ![Installieren von AEM Sidekick](/help/edge/assets/install-aem-sidekick.png)

   Nachdem Sie die Erweiterung in Chrome installiert haben, vergessen Sie nicht, sie anzuheften. So können Sie sie einfacher finden.

   ![Anheften von AEM Sidekick](/help/edge/assets/pin-aem-sidekick.png)

1. Um die Sidekick-Chrome-Erweiterung einzurichten, wechseln Sie zum zuvor freigegebenen Google Drive- oder Microsoft SharePoint-Ordner, klicken Sie in der Browser-Symbolleiste mit der rechten Maustaste auf das Erweiterungssymbol und wählen Sie `Add this project` aus.

   ![AEM Sidekick – Hinzufügen eines Projekts](/help/edge/assets/aem-sidekick-add-a-project.png)

   Wenn die Erweiterung installiert und Ihr Projekt hinzugefügt ist, können Sie Ihre Inhalte auf Ihrem Google Drive in einer Vorschau anzeigen und veröffentlichen.

1. Wählen Sie alle Dokumente im Microsoft SharePoint- oder Google Drive-Ordner aus. Sie können mehrere Dokumente auswählen, indem Sie mit gedrückter Strg-Taste (Windows/Linux) oder Befehlstaste (Mac) auf diese klicken.

   ![Auswählen aller Dateien](/help/edge/assets/select-all-files.png)

1. Klicken Sie auf das AEM Sidekick-Symbol, das an Ihrer Chrome-Erweiterungsleiste angeheftet ist. Auf dem Bildschirm wird eine Symbolleiste angezeigt. Sie können die Inhalte in einer Vorschau anzeigen oder veröffentlichen.

   Wenn Sie `index`-, `nav`-, `footer`- und `enquiry`-Dateien herüberkopiert haben, handelt es sich dabei um separate Dokumente mit eigenen Vorschau- und Veröffentlichungszyklen. Stellen Sie daher sicher, dass Sie alle Dokumente in einer Vorschau anzeigen (und veröffentlichen).

   Nach Vorschau der Dateien werden die Dokumente auf neuen Browser-Registerkarten angezeigt. Um das Beispielformular in einer Vorschau anzuzeigen, navigieren Sie zur folgenden URL:


   ```HTML
   https://<branch>--<repository>--<owner>.aem.live
   ```

   * `<branch>` bezieht sich auf die Verzweigung Ihres GitHub-Repositorys.
   * `<repository>` bezeichnet Ihr GitHub-Repository.
   * `<owner>` bezieht sich auf den Benutzernamen Ihres GitHub-Kontos, das Ihr GitHub-Repository hostet.


   URL.`https://<branch>--<repo>--<owner>.aem.page/enquiry`

   Wenn das Repository Ihres Projekts beispielsweise „wefinance“ heißt, sich unter dem Konto „wkndform“ befindet und Sie die Verzweigung „main“ und den Formularnamen `enquiry` verwenden, lautet die URL wie folgt:`https://main--wefinance--wkndform.aem.live/enquiry`.
&lt;!--(https://main--wefinance--wkndform.aem.live/enquiry).-->

### Erstellen eines Formulars

Der Beispielinhalt enthält ein Blatt „enquiry“, das als Vorlage für das Formular „enquiry“ dient. Jede Zeile des Blatts steht für ein [Formularfeld](/help/edge/docs/forms/form-components.md#available-components) und die Spaltenüberschriften definieren die [Feldeigenschaften](/help/edge/docs/forms/form-components.md#available-components). Mit diesem Beispielformular können Sie sofort mit der Formularerstellung loslegen.

![Formular „enquiry“](/help/edge/docs/forms/assets/enquiry-form-microsoft-sharepoint.png)

Aktualisieren wir zunächst einen Feldtitel. Öffnen Sie das Blatt „enquiry“ zur Bearbeitung, ändern Sie den Titel der Senden-Schaltfläche in `Let's Talk` und verwenden Sie AEM Sidekick, um die Datei in einer Vorschau anzuzeigen und zu veröffentlichen.

![Formular „enquiry“](/help/edge/assets/enquiry-form-preview-publish.png)

Wenn Sie die Datei in einer Vorschau anzeigen oder veröffentlichen, wird eine JSON-Version der Datei auf einer neuen Registerkarte angezeigt. Kopieren Sie die Vorschau-URL (.aem.page) oder die Veröffentlichungs-URL (.aem.live) der Datei.

![JSON des Formular-Arbeitsblatts](/help/edge/assets/preview-and-publish-enquiry-form.png)

Öffnen Sie die `enquiry`-Datei und ersetzen Sie die URL im Formularblock durch die URL der im vorherigen Schritt kopierten Datei. Stellen Sie sicher, dass die URL ein Hyperlink ist.

![„enquiry“-Datei mit der .json-URL der URL des Arbeitsblatts](/help/edge/assets/enquiry-doc-to-embed-form.png)

Verwenden Sie AEM Sidekick, um das „enquiry“-Dokument in einer Vorschau anzuzeigen und zu veröffentlichen.

![„enquiry“-Datei mit der .json-URL der URL des Arbeitsblatts](/help/edge/assets/preview-and-publish-enquiry-document.png)


Um eine Vorschau des aktualisierten Formulars „enquiry“ anzuzeigen, gehen Sie zur folgenden URL:


```HTML
    https://<branch>--<repository>--<owner>.aem.page/enquiry
       
```

Der Titel der Senden-Schaltfläche wird in `Let's Talk` geändert.

![Formular „enquiry“](/help/edge/assets/updated-form.png)

&lt;!--(https://main--wefinance--wkndform.aem.live/enquiry)-->

URL: `https://main--wefinance--wkndform.aem.live/enquiry`
&lt;!--(https://main--wefinance--wkndform.aem.live/enquiry)-->


Ausführliche Informationen zum Erstellen und Veröffentlichen eines neuen Formulars finden Sie in der Anleitung [Erstellen eines Formulars](/help/edge/docs/forms/create-forms.md).

### Entwickeln von Stilen und Funktionen


Gehen Sie wie folgt vor, um in kürzester Zeit über eine lokale AEM-Entwicklungsumgebung zu verfügen:

1. AEM-CLI installieren: Die AEM-CLI vereinfacht Entwicklungsaufgaben. Installieren Sie sie global mit npm:

   ```Bash
       npm install -g @adobe/aem-cli
   ```

1. GitHub-Projekt klonen: Klonen Sie Ihr Projekt-Repository von GitHub mithilfe des folgenden Befehls und ersetzen Sie <owner> durch die Repository-Besitzerin bzw. den Repository-Besitzer und <repo> mit dem Repository-Namen:

   ```
   git clone https://github.com/<owner>/<repo>
   ```

1. Starten Sie Ihre lokale Umgebung: Navigieren Sie zu Ihrem Projektverzeichnis und starten Sie Ihre lokale AEM-Instanz mit einem einzigen Befehl:

   ```
   cd <repo>
   aem up
   ```

Der Ordner `blocks/form` des adaptiven Formularblocks ist Ihr Spielplatz für Stile und Code für Ihre Formulare! Sie können alle `.css`- oder `.js`-Dateien in diesem Verzeichnis bearbeiten. Die Änderungen werden sofort in Ihrem Browser angezeigt.

Bereit zur Präsentation Ihrer Kreation? Verwenden Sie Git, um Ihre Änderungen zu bestätigen und zu übertragen. Dadurch werden Ihre Vorschau- und Produktionsumgebungen aktualisiert, auf die über diese URLs zugegriffen werden kann (Platzhalter durch Ihre Projektdetails ersetzen):

Vorschau: `https://<branch>--<repo>--<owner>.aem.page/`
Produktion: `https://<branch>--<repo>--<owner>.aem.live/`

Herzlichen Glückwunsch! Sie haben Ihre lokale Entwicklungsumgebung erfolgreich eingerichtet und Ihre Änderungen bereitgestellt.


<!--
## Add Adaptive Forms Block to your existing AEM project


>[!VIDEO](https://video.tv.adobe.com/v/3427789)

If you have an existing AEM Project, you can integrate the Adaptive Forms Block into your current project to get started on form creation. 

>[!NOTE]
>
>
> This step applies to projects built with the [AEM Boilerplate](https://github.com/adobe/aem-boilerplate). If you created your AEM project using the [AEM Forms Boilerplate](https://github.com/adobe-rnd/aem-boilerplate-forms), you can skip this step.

To Integrate:

1. **Add required files and folders**
   1. Copy and paste the following folders and files from the [AEM Forms Boilerplate](https://github.com/adobe-rnd/aem-boilerplate-forms) into your AEM Project:

      * [form block](https://github.com/adobe-rnd/aem-boilerplate-forms/tree/main/blocks/form)  folder
       * [form-common](https://github.com/adobe-rnd/aem-boilerplate-forms/tree/main/models/form-common)  folder
       * [form-components](https://github.com/adobe-rnd/aem-boilerplate-forms/tree/main/models/form-components) folder
       * [form-editor-support.js](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/scripts/form-editor-support.js) file
       * [form-editor-support.css](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/scripts/form-editor-support.css) file

1. **Update component definitions and models files**
    1. Navigate to the `../models/_component-definition.json` file in your AEM Project and update it with the changes from the [_component-definition.json file in the AEM Forms Boilerplate](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/models/_component-definition.json#L39-L48).
    
    1. Navigate to the `../models/_component-models.json` file in your AEM Project and update it with the changes from the [_component-models.json file in the AEM Forms Boilerplate](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/models/_component-models.json#L24-L26)

1. **Add Form Editor in editor script**
    1. Navigate to the `../scripts/editor-support.js` file in your AEM Project and update it with the changes from the [editor-support.js file in the AEM Forms Boilerplate](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/scripts/editor-support.js#L105-L106)
1. **Update ESLint configuration file**
    1. Navigate to the `../.eslintignore` file in your AEM Project and add the following line of codes to prevent errors related to the Form Block rule engine:
        ```
            blocks/form/rules/formula/*
            blocks/form/rules/model/*
        ```

1. Commit and push these changes to your AEM Project repository on GitHub.

That's it! The Adaptive Forms Block is now part of your AEM project. You can start creating and adding forms to your AEM pages.
-->

## Beheben von Build-Problemen in GitHub

Stellen Sie einen reibungslosen Build-Prozess in GitHub sicher, indem Sie potenzielle Probleme beheben:

* **Auflösen des Modulpfadfehlers:**
Wenn der Fehler „Pfad zum Modul ‚../../scripts/lib-franklin.js‘ kann nicht aufgelöst werden“ auftritt, navigieren Sie zu [EDS-Projekt]/blocks/forms/form.js. Aktualisieren Sie die Importanweisung, indem Sie die Datei „lib-franklin.js“ durch die Datei „aem.js“ ersetzen.

* **Beheben von Linting-Fehlern:**
Sollten Sie auf Linting-Fehler stoßen, können Sie diese umgehen. Öffnen Sie die Datei [EDS Project]/package.json und ändern Sie das Skript „lint“ von `"lint": "npm run lint:js && npm run lint:css"` zu `"lint": "echo 'skipping linting for now'"`. Speichern Sie die Datei und übertragen Sie die Änderungen auf Ihr GitHub-Projekt.


## Siehe auch

{{see-more-forms-eds}}
