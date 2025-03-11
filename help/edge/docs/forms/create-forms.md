---
title: Erste Schritte mit Edge Delivery Services für AEM Forms. Erstellen Sie ein Formular.
description: Perfekte Formulare im Handumdrehen! ⚡ Dokumentenbasierte Inhaltserstellung mit AEM Forms Edge Delivery = Atemberaubende Geschwindigkeit und SEO-freundliche Formulare für glücklichere Benutzende und Suchmaschinen.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 0cf881a2-3784-45eb-afe8-3435e5e95cf4
source-git-commit: ccadacb5db3c0dd57e61a9a1404049dbe7aa98d2
workflow-type: tm+mt
source-wordcount: '781'
ht-degree: 100%

---

# Erstellen eines Formulars mithilfe des adaptiven Formularbausteins

>[!VIDEO](https://video.tv.adobe.com/v/3427881?quality=12&learn=on)

AEM Forms Edge Delivery bietet einen Baustein, der als adaptiver Formularbaustein bezeichnet wird und mit dem Sie mühelos Formulare erstellen können, um erfasste Daten zu erfassen und zu speichern. Sie können [ein neues AEM-Projekt vorkonfiguriert mit einem Block für ein adaptives Formular erstellen](/help/edge/docs/forms/tutorial.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block) oder [den Block für ein adaptives Formular zu einem bestehenden AEM-Projekt hinzufügen.](/help/edge/docs/forms/tutorial.md#add-adaptive-forms-block-to-your-existing-aem-project).

Diese Formulare senden Daten direkt an eine Microsoft Excel- oder Google Tabellen-Datei, sodass Sie ein dynamisches Ökosystem und robuste APIs von Google Tabellen, Microsoft Excel und Microsoft SharePoint verwenden können, um die übermittelten Daten einfach zu verarbeiten oder einen bestehenden Business-Workflow zu initiieren.

![Ökosystem des dokumentenbasierten Authorings](/help/edge/assets/document-based-authoring-workflow-create-form.png)


## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie die folgenden Schritte ausgeführt haben:

* Richten Sie ein [AEM-Projekt mit der AEM Forms-Bausteinvorlage](/help/edge/docs/forms/tutorial.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block) [ein, fügen Sie einen adaptiven Formularblock zu Ihrem bestehenden AEM-Projekt hinzu](/help/edge/docs/forms/tutorial.md#add-adaptive-forms-block-to-your-existing-aem-project) und klonen Sie das entsprechende GitHub-Repository auf Ihrem lokalen Computer.
<!--In this document, the local folder of your Edge Delivery Services (EDS) project is referred as `[EDS Project repository]`.  -->
* Stellen Sie sicher, dass Sie Zugriff auf Google Tabellen oder Microsoft SharePoint haben. Informationen zum Einrichten von Microsoft SharePoint als Inhaltsquelle finden Sie unter [Verwenden von Sharepoint](https://www.aem.live/docs/setup-customer-sharepoint).



## Erstellen eines Formulars

<!--
+++ Step 1: Add the Adaptive Forms Block to your Edge Delivery Services (EDS) project.

The Adaptive  empowers users to create forms for an Edge Delivery Service Site. However, this block isn't included in the default AEM boilerplate (used to create an Edge Delivery Services project). To seamlessly integrate the Adaptive Forms Block into your Edge Delivery Services project:

1. **Clone the Adaptive Forms Block repository**: Clone the [Adaptive Forms Block repository](https://github.com/adobe-rnd/form-block) on your local machine. It contains the code to render the form on an EDS webpage. In this document, the local folder of your Forms Block repository is referred as `[Adaptive Forms Block repository]`.
2. **Locate the Adaptive Forms Block Repository:** Access the [Adaptive Forms Block repository]/blocks/src folder and copy its content. 

3. on your local machine and copy the `form` folder. 
4. **Paste the Adaptive Forms Block's code into your EDS Project:**
Navigate to the [EDS Project repository]/blocks/ folder on your local machine and create a 'form' folder. Paste the `[Adaptive Forms Block repository]/blocks/src content`, copied in perevious step to the `[EDS Project repository]/blocks/form` folder.
1. **Commit Changes to GitHub:** Check in the `[EDS Project repository]/blocks/form` folder and its underlying files to your Edge Delivery Services project on GitHub.

After completing these steps, the Adaptive Forms Block is successfully added to your Edge Delivery Services (EDS) project repository on GitHub. You can now create and add forms to a EDS Sites page.
 

**Troubleshooting GitHub build issues**

Ensure a smooth GitHub build process by addressing potential issues:

* **Resolve Module Path Error:**
    If you encounter the error "Unable to resolve path to module "'../../scripts/lib-franklin.js'", navigate to the [EDS Project]/blocks/forms/form.js file. Update the import statement by replacing the lib-franklin.js file with the aem.js file.

* **Handle Linting Errors:**
    Should you come across any linting errors, you can bypass them. Open the [EDS Project]/package.json file and modify the "lint" script from "lint": "npm run lint:js && npm run lint:css" to "lint": "echo 'skipping linting for now'". Save the file and commit the changes to your GitHub project. -->

+++ Schritt 1: Erstellen Sie ein Formular mit Microsoft Excel oder Google Tabellen.

Anstatt durch komplexe Prozesse zu navigieren, kann das Erstellen eines Formulars mühelos mithilfe einer Tabelle erfolgen. Sie können die Zeilen und Spalten definieren, aus denen die Formularstruktur besteht. Jede Zeile stellt ein einzelnes [Formularfeld](/help/edge/docs/forms/form-components.md#available-components) dar und die Spaltenüberschriften definieren die entsprechenden [Feldeigenschaften](/help/edge/docs/forms/form-components.md#components-properties).

Sehen Sie sich beispielsweise die folgende Tabelle an, bei der die Zeilen Felder für eine Tabelle [enquiry](/help/edge/assets/enquiry.xlsx) darstellen und die Spaltenüberschriften ihre Eigenschaften definieren:

![Abfragetabelle](/help/edge/assets/enquiry-form-spreadsheet.png)

So setzen Sie die Formularerstellung fort:

1. Rufen Sie den AEM Edge Delivery-Projektordner in Microsoft SharePoint oder Google Drive auf.

1. Erstellen Sie eine Microsoft Excel-Arbeitsmappe oder ein Google-Blatt an einer beliebigen Stelle in Ihrem AEM Edge Delivery-Projektverzeichnis. Erstellen Sie beispielsweise eine Tabelle mit dem Namen `enquiry` im AEM Edge Delivery-Projektverzeichnis auf Google Drive.

   <!-- ![Sample Content on Google Drive](/help/edge/assets/upload-sample-files-to-your-content-folder.png)-->

1. Stellen Sie sicher, dass das Blatt für die entsprechenden AEM-Benutzenden (z. B. `forms@adobe.com`) [gemäß den für Ihr Projekt angegebenen Konfigurationen freigegeben ist](https://www.aem.live/docs/setup-customer-sharepoint). Gewähren Sie für das Blatt die Berechtigung zum Bearbeiten durch Benutzende.

1. Öffnen Sie die erstellte Tabelle und benennen Sie das Standardblatt in „shared-aem“ um.

   ![Umbenennen des Standardblatts in „shared-default“](/help/edge/assets/rename-sheet-to-shared-default.png)

1. Fügen Sie zum Hinzufügen der Formularfelder Zeilen und Spaltenüberschriften in das Blatt „shared-aem“ ein. Jede Zeile sollte ein [Formularfeld](/help/edge/docs/forms/form-components.md#available-components) darstellen, wobei die Spaltenüberschriften die entsprechenden [Feldeigenschaften](/help/edge/docs/forms/form-components.md#components-properties) definieren.


   Für einen schnellen Start können Sie den Inhalt der [Abfragetabelle](/help/edge/assets/enquiry.xlsx) in Ihre Tabelle kopieren. Speichern Sie die Tabelle, nachdem Sie den Inhalt kopiert haben.

   >[!VIDEO](https://video.tv.adobe.com/v/3427468?quality=12&learn=on)


1. Verwenden Sie [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content), um eine Vorschau des Blattes anzuzeigen.

   ![Verwenden von AEM Sidekick, um eine Vorschau der Tabelle anzuzeigen](/help/edge/assets/preview-form.png)

   Bei der Vorschau werden die Inhalte des Blattes in neuen Browser-Registerkarten im JSON-Format angezeigt. Stellen Sie sicher, dass Sie die Vorschau-URL erfassen, da dies für das Rendern des Formulars im nächsten Abschnitt erforderlich ist. Die URL hat das folgende Format:


   ```JSON
       https://<branch>--<repository>--<owner>.aem.live/<form-path>/<form-file-name>.json
   ```

   * `<branch>` bezieht sich auf die Verzweigung Ihres GitHub-Repositorys.
   * `<repository>` bezeichnet Ihr GitHub-Repository.
   * `<owner>` bezieht sich auf den Benutzernamen Ihres GitHub-Kontos, das Ihr GitHub-Repository hostet.

   Wenn das Repository Ihres Projekts beispielsweise „wefinance“ heißt, sich unter dem Konto „wkndform“ befindet und Sie die Verzweigung „main“ verwenden, sieht die URL wie folgt aus:

`https://main--wefinance--wkndform.aem.page/enquiry.json`
&lt;!--(https://main--wefinance--wkndform.aem.page/enquiry.json)-->


+++

+++ Schritt 2: Zeigen Sie mithilfe Ihrer Edge Delivery Service-Seite eine Vorschau des Formulars an.


Bis jetzt haben Sie die Struktur des Formulars vorbereitet. So zeigen Sie nun eine Vorschau des Formulars an:

1. Öffnen Sie Ihr Microsoft SharePoint- oder Google Drive-Konto und navigieren Sie zu Ihrem AEM Edge Delivery-Projektverzeichnis.



1. Öffnen Sie eine Dokumentdatei (zum Beispiel die Index-Datei), um das Formular einzubetten. Sie können auch ein [neues Dokument erstellen](/help/edge/assets/enquiry-form.docx).

1. Wechseln Sie an die gewünschte Stelle im Dokument, an der Sie das Formular hinzufügen möchten.

1. Erstellen eines Formularbausteins zum Rendern des Formulars. Wählen Sie „Einfügen“ > „Tabelle“ und erstellen Sie eine Tabelle mit einer Spalte und zwei Zeilen. Nennen Sie die Tabelle „Formular“ und fügen Sie die Vorschau-URL in die zweite Zeile ein. Stellen Sie sicher, dass die URL als Hyperlink und nicht als reiner Text formatiert ist, wie unten dargestellt:

   | Formular |
   |---|
   | `https://main--wefinance--wkndform.aem.live/enquiry.json` |


   ![Hinzufügen eines adaptiven Formularbausteins zu Ihrer Web-Seite](/help/edge/assets/enquiry-doc-to-embed-form.png)

   Dieser Block dient als Platzhalter, in den das Formular eingebettet ist. Fügen Sie in der zweiten Zeile des Bausteins die Vorschau-URL Ihrer `<form>.json`-Datei als Hyperlink ein.

   >[!IMPORTANT]
   >
   >
   > Stellen Sie sicher, dass die URL als Hyperlink formatiert ist und nicht nur als reiner Text angezeigt wird.


1. Verwenden Sie [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content), um eine Vorschau des Dokuments anzuzeigen. Das Formular wird jetzt auf der Seite angezeigt. Hier basiert das Formular beispielsweise auf der [Abfragetabelle](/help/edge/assets/enquiry-form.docx):


   [![Beispiel für ein EDS-Formular](/help/edge/assets/updated-form.png)](https://main--wefinance--wkndform.aem.page/enquiry-form)

   Füllen Sie nun das Formular aus und klicken Sie auf die Schaltfläche „Absenden“. Es tritt ein Fehler ähnlich dem folgenden auf, da die Tabelle noch nicht für das Akzeptieren der Daten konfiguriert ist.

   ![Fehler bei Formularübermittlung](/help/edge/assets/form-error.png)

+++


## Nächster Schritt

[Bereiten Sie die Tabellenkalkulation vor](/help/edge/docs/forms/submit-forms.md), um Daten bei der Formularübermittlung zu akzeptieren.


## Siehe auch

{{see-more-forms-eds}}
