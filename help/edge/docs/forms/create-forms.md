---
title: Erste Schritte mit dem AEM Forms Edge Delivery Service. Erstellen Sie ein Formular.
description: Handwerkliche perfekte Formen, schnell! ⚡ AEM Forms Edge Delivery doc-basiertes Authoring = Blazing Speed & SEO-freundliche Formulare für glücklichere Benutzer und Suchmaschinen.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
exl-id: 0cf881a2-3784-45eb-afe8-3435e5e95cf4
source-git-commit: 2aa70e78764616f41fe64e324c017873cfba1d5b
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 1%

---

# Erstellen eines Formulars mithilfe des adaptiven Forms-Blocks

Die AEM Forms Edge-Bereitstellung bietet einen Block, der als Adaptiver Forms-Block bezeichnet wird und mit dem Sie mühelos Formulare erstellen können, um erfasste Daten zu erfassen und zu speichern. Sie können [Erstellen Sie ein neues AEM Projekt, das bereits mit Adaptive Forms Block ausgestattet ist.](/help/edge/docs/forms/tutorial.md#create-a-new-aem-project-pre-equipped-with-adaptive-forms-block) oder [Fügen Sie den adaptiven Forms-Block zu einem bestehenden AEM hinzu.](/help/edge/docs/forms/tutorial.md#add-adaptive-forms-block-to-your-existing-aem-project).

Diese Formulare senden Daten direkt an eine Microsoft Excel- oder Google Tabellen-Datei, sodass Sie ein dynamisches Ökosystem und robuste APIs von Google Tabellen, Microsoft Excel und Microsoft SharePoint verwenden können, um gesendete Daten einfach zu verarbeiten oder einen bestehenden Geschäftsarbeitsablauf zu initiieren.

![Dokumentenbasiertes Authoring-Ökosystem](/help/edge/assets/document-based-authoring-workflow-create-form.png)




## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie die folgenden Schritte ausgeführt haben:

* Richten Sie eine [AEM von Projekten mithilfe der AEM Forms-Vorlage](/help/edge/docs/forms/tutorial.md#create-a-new-aem-project-pre-equipped-with-adaptive-forms-block) oder [Adaptiver Forms-Block zu Ihrem bestehenden AEM hinzugefügt.](/help/edge/docs/forms/tutorial.md#add-adaptive-forms-block-to-your-existing-aem-project) und klonen Sie das entsprechende GitHub-Repository auf Ihrem lokalen Computer.
In diesem Dokument wird der lokale Ordner Ihres Edge Delivery Services-Projekts (EDS) als `[EDS Project repository]` .
* Stellen Sie sicher, dass Sie Zugriff auf Google Tabellen oder Microsoft SharePoint haben. Informationen zum Einrichten von Microsoft SharePoint als Inhaltsquelle finden Sie unter [Verwendung von Sharepoint](https://www.aem.live/docs/setup-customer-sharepoint)



## Formular erstellen

<!-- 

+++ Step 1: Add the Adaptive Forms Block to your Edge Delivery Services (EDS) project.

The Adaptive  empowers users to create forms for an Edge Delivery ServicesSite. However, this block isn't included in the default AEM boilerplate (used to create an Edge Delivery Services project). To seamlessly integrate the Adaptive Forms Block into your Edge Delivery Services project:

1. **Clone the Adaptive Forms Block repository**: Clone the [Adaptive Forms Block repository](https://github.com/adobe-rnd/form-block) on your local machine. It contains the code to render the form on an EDS webpage. In this document, the local folder of your Forms Block repository is referred as `[Adaptive Forms Block repository]`.
1. **Locate the Adaptive Forms Block Repository:** Access the [Adaptive Forms Block repository]/blocks/src folder and copy its content. 

1. on your local machine and copy the `form` folder. 
1. **Paste the Adaptive Forms Block's code into your EDS Project:**
Navigate to the [EDS Project repository]/blocks/ folder on your local machine and create a 'form' folder. Paste the `[Adaptive Forms Block repository]/blocks/src content`, copied in perevious step to the `[EDS Project repository]/blocks/form` folder.
1. **Commit Changes to GitHub:** Check in the `[EDS Project repository]/blocks/form` folder and its underlying files to your Edge Delivery Services project on GitHub.

After completing these steps, the Adaptive Forms Block is successfully added to your Edge Delivery Services (EDS) project repository on GitHub. You can now create and add forms to a EDS Sites page.
 

**Troubleshooting GitHub build issues**

Ensure a smooth GitHub build process by addressing potential issues:

* **Resolve Module Path Error:**
    If you encounter the error "Unable to resolve path to module "'../../scripts/lib-franklin.js'", navigate to the [EDS Project]/blocks/forms/form.js file. Update the import statement by replacing the lib-franklin.js file with the aem.js file.

* **Handle Linting Errors:**
    Should you come across any linting errors, you can bypass them. Open the [EDS Project]/package.json file and modify the "lint" script from "lint": "npm run lint:js && npm run lint:css" to "lint": "echo 'skipping linting for now'". Save the file and commit the changes to your GitHub project.

+++

-->

+++ Schritt 1: Erstellen Sie ein Formular mit Microsoft Excel oder Google Sheet.

Anstatt durch komplexe Prozesse zu navigieren, kann das Erstellen eines Formulars mühelos mithilfe einer Tabelle erfolgen. Sie können die Zeilen und Spalten definieren, aus denen die Formularstruktur besteht. Jede Zeile stellt eine einzelne [Formularfeld](/help/edge/docs/forms/form-components.md#available-components) und die Spaltenüberschriften definieren die entsprechenden [Feldeigenschaften](/help/edge/docs/forms/form-components.md#components-properties).

Betrachten Sie beispielsweise die folgende Tabelle, in der die Zeilen Felder für eine `enquiry` Formular- und Spaltenüberschriften definieren ihre Eigenschaften:

![Abfragetabelle](/help/edge/assets/enquiry-form-spreadsheet.png)

So fahren Sie mit der Formularerstellung fort:

1. Rufen Sie den Ordner AEM Edge-Bereitstellungsprojekt auf Microsoft SharePoint oder Google Drive auf.

1. Erstellen Sie eine Microsoft Excel-Arbeitsmappe oder ein Google-Blatt an einer beliebigen Stelle in Ihrem AEM Edge-Bereitstellungsprojektverzeichnis. Erstellen Sie beispielsweise eine Tabelle mit dem Namen `enquiry` im Projektverzeichnis AEM Edge-Bereitstellung auf Google Drive.

1. Stellen Sie sicher, dass das Blatt für den entsprechenden AEM Benutzer freigegeben ist (z. B. `helix@adobe.com`) [gemäß den für Ihr Projekt angegebenen Konfigurationen](https://www.aem.live/docs/setup-customer-sharepoint). Gewähren Sie der Benutzer Bearbeitungsberechtigung für das Blatt.

1. Öffnen Sie die erstellte Tabelle und benennen Sie das Standardblatt in &quot;Standard freigegeben&quot; um.

   ![Standard-Arbeitsblatt in &quot;shared-default&quot;umbenennen](/help/edge/assets/rename-sheet-to-shared-default.png)

1. Fügen Sie zum Hinzufügen der Formularfelder Zeilen und Spaltenüberschriften in das &quot;shared-default&quot;-Blatt ein. Jede Zeile sollte eine [Formularfeld](/help/edge/docs/forms/form-components.md#available-components), wobei die Spaltenüberschriften das entsprechende Feld definieren [properties](/help/edge/docs/forms/form-components.md#components-properties).

   Für einen schnellen Start sollten Sie den Inhalt der [Abfragetabelle](https://docs.google.com/spreadsheets/d/196lukD028RDK_evBelkOonPxC7w0l_IiJ-Yx3DvMfNk/edit#gid=0) in Ihre Tabelle ein. Nachdem Sie den Inhalt kopiert haben, speichern Sie das Arbeitsblatt.

   >[!VIDEO](https://video.tv.adobe.com/v/3427468?quality=12&learn=on)


1. Verwendung [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) um eine Vorschau des Blattes anzuzeigen.

   ![Verwenden Sie AEM Sidekick, um eine Vorschau der Tabelle anzuzeigen](/help/edge/assets/preview-form.png)

   Bei der Vorschau werden die Inhalte der Seite in neuen Browser-Registerkarten im JSON-Format angezeigt. Stellen Sie sicher, dass Sie die Vorschau-URL erfassen, da dies für die Wiedergabe des Formulars im nächsten Abschnitt erforderlich ist. Die URL hat das folgende Format:


   ```JSON
       https://<branch>--<repository>--<owner>.hlx.live/<form-path>/<form-file-name>.json
   ```

   * `<branch>` bezieht sich auf die Verzweigung Ihres GitHub-Repository.
   * `<repository>` bezeichnet Ihr GitHub-Repository.
   * `<owner>` bezieht sich auf den Benutzernamen Ihres GitHub-Kontos, das Ihr GitHub-Repository hostet.

   Wenn das Repository Ihres Projekts beispielsweise &quot;Portal&quot;heißt, befindet es sich unter dem Konto &quot;wkndforms&quot;und Sie die Verzweigung &quot;main&quot;verwenden, sieht die URL wie folgt aus:

   `https://main--portal--wkndforms.hlx.page/enquiry.json`


+++

+++ Schritt 2: Anzeigen einer Vorschau des Formulars mithilfe Ihrer Edge Delivery Services (EDS)-Seite.


Bis jetzt haben Sie den Adaptive Forms Block zu Ihrem EDS-Projekt hinzugefügt und die Formularstruktur vorbereitet. Nun können Sie eine Vorschau des Formulars anzeigen:

1. **Zugriff auf Ihr Projektverzeichnis:** Öffnen Sie Ihr Microsoft SharePoint- oder Google Drive-Konto und navigieren Sie zu Ihrem AEM Edge Delivery-Projektverzeichnis.

1. **Betten Sie das Formular in ein Dokument ein:** Öffnen Sie eine Dokumentdatei (z. B. eine Indexdatei), um das Formular einzubetten. Alternativ können Sie ein neues Dokument erstellen.

1. **Navigieren Sie zum gewünschten Speicherort:** Wechseln Sie an die gewünschte Stelle im Dokument, an der Sie das Formular hinzufügen möchten.

1. **Fügen Sie den adaptiven Forms-Block hinzu:** So erstellen Sie einen Formularblock zum Rendern des Formulars. Wählen Sie &quot;Einfügen&quot;> &quot;Tabelle&quot;und erstellen Sie eine Spalte (zwei Zeilentabellen). Nennen Sie die Tabelle &quot;Formular&quot;und fügen Sie die Vorschau-URL in die zweite Zeile ein. Stellen Sie sicher, dass die URL als Hyperlink formatiert ist, nicht als Nur-Text, wie unten dargestellt:

   | Formular |
   |---|
   | [https://main—portal—wkndforms.hlx.live/inquiry.json](https://main--portal--wkndforms.hlx.live/enquiry.json) |

   Dieser Block dient als Platzhalter, in den das Formular eingebettet ist. Fügen Sie in der zweiten Zeile des Blocks die Vorschau-URL Ihrer `<form>.json` als Hyperlink.

   >[!IMPORTANT]
   >
   >
   > Stellen Sie sicher, dass die URL als Hyperlink formatiert ist, anstatt als Nur-Text angezeigt zu werden.


1. Verwendung [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) , um eine Vorschau des Dokuments anzuzeigen. Auf der Seite wird nun das Formular angezeigt. Hier ist beispielsweise das Formular, das auf der Variablen [Fragenübersicht](https://docs.google.com/spreadsheets/d/196lukD028RDK_evBelkOonPxC7w0l_IiJ-Yx3DvMfNk/edit#gid=0):


   [![Beispiel-EDS-Formular](/help/edge/assets/eds-form.png)](https://main--portal--wkndforms.hlx.live/)

   Füllen Sie nun das Formular aus und klicken Sie auf die Senden-Schaltfläche. Es tritt ein Fehler ähnlich dem folgenden auf, da die Tabelle noch nicht für die Annahme der Daten konfiguriert ist.

   ![Fehler bei Formularübermittlung](/help/edge/assets/form-error.png)

+++


## Nächster Schritt

[Tabellenkalkulation vorbereiten](/help/edge/docs/forms/submit-forms.md) , um Daten bei der Formularübermittlung zu akzeptieren.



