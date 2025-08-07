---
title: Veröffentlichen von Edge Delivery Services für AEM Forms
description: Veröffentlichen von Edge Delivery Services für AEM Forms
feature: Edge Delivery Services
exl-id: dcb16da1-dcc2-4529-8859-0716e727b54d
role: Admin, Architect, Developer
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '585'
ht-degree: 100%

---

# Veröffentlichen des Formulars und Starten der Datenerfassung

Sobald Sie bereit sind, Ihr Formular für Ihre Kundschaft zur Datenerfassung oder -übermittlung freizugeben, können Sie es einfach veröffentlichen, sodass das Formular Ihrer Kundschaft zur Verfügung steht.

![Das Ökosystem des dokumentbasierten Authorings](/help/edge/assets/document-based-authoring-workflow-publish-form.png)

## Voraussetzungen

- Sie verfügen über ein AEM-Projekt, das auf einer [AEM Forms-Bausteinvorlage](/help/edge/docs/forms/tutorial.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block) basiert, oder Sie haben [einen adaptiven Formularbaustein zu Ihrem bestehenden AEM-Projekt hinzugefügt](/help/edge/docs/forms/tutorial.md#add-adaptive-forms-block-to-your-existing-aem-project)
- Ihr Formular ist vollständig getestet und einsatzbereit.
- Ihre [Tabelle ist konfiguriert](/help/edge/docs/forms/submit-forms.md), um Daten zu akzeptieren.


## Veröffentlichen Ihres Formulars

+++ &#x200B;1. Veröffentlichen Sie Ihre Tabelle

1. Öffnen Sie Ihr Microsoft SharePoint- oder Google Drive-Konto und navigieren Sie zu Ihrem AEM Edge Delivery-Projektverzeichnis.

1. Öffnen Sie die Tabelle, die Ihr Formular enthält. Beispiel: die Microsoft Excel-Arbeitsmappe des Formulars [enquiry](/help/edge/assets/enquiry.xlsx).

1. Verwenden Sie [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content), um eine Vorschau des Blattes anzuzeigen.

   ![Verwenden von AEM Sidekick zum Anzeigen einer Vorschau der Tabelle](/help/edge/assets/preview-form.png)

   Nach erfolgreichem Abschluss des Vorschauvorgangs wird der Tabelleninhalt in das JSON-Format konvertiert. Dieser Inhalt wird dann auf der Vorschauseite in einem strukturierten Tabellenformat dargestellt. Beispielsweise veranschaulicht das begleitende Bild den Inhalt eines „Anfrageformulars“.

   ![JSON-Format für die Formularvorschau](/help/edge/assets/forms-preview-json-format.png)

1. Verwenden Sie AEM Sidekick, um die Tabelle zu veröffentlichen. Stellen Sie sicher, dass Sie die Veröffentlichungs-URL erfassen, da diese für das Rendern des Formulars im nächsten Abschnitt erforderlich ist. Die URL hat das folgende Format:


   ```JSON
       https://<branch>--<repository>--<owner>.aem.live/<form>.json
   ```

   - `<branch>` bezieht sich auf die Verzweigung Ihres GitHub-Repositorys.
   - `<repository>` bezeichnet Ihr GitHub-Repository.
   - `<owner>` bezieht sich auf den Benutzernamen Ihres GitHub-Kontos, das Ihr GitHub-Repository hostet.

   Wenn das Repository Ihres Projekts beispielsweise „wefinance“ heißt, sich unter dem Konto „wkndform“ befindet und Sie die Verzweigung „main“ sowie das Formular „enquiry“ verwenden, sieht die URL wie folgt aus:

   `https://main--wefinance--wkndform.aem.live/enquiry.json`
&lt;!--(https://main--wefinance--wkndform.aem.live/enquiry.json)-->

+++

+++ &#x200B;2. Fügen Sie das Formular zu Ihrer Web-Seite hinzu.

Fügen Sie `<form>.json` zu einer Web-Seite hinzu, um die Kundeninteraktion zu erleichtern, indem Benutzende das Formular mühelos auszufüllen und versenden können.


So fügen Sie das Formular zu Ihrer Web-Seite hinzu:

1. Greifen Sie auf Ihr Microsoft SharePoint- oder Google Drive-Konto zu und navigieren Sie zu Ihrem `[AEM Edge Delivery project directory]`.

1. Öffnen Sie eine Dokumentdatei, in die Sie das Formular einbetten möchten. Sie können beispielsweise die Datei [enquiry-form.docx](/help/edge/assets/enquiry-form.docx) öffnen oder alternativ ein neues Dokument erstellen.

1. Identifizieren Sie den gewünschten Abschnitt im Dokument, in den Sie das Formular einfügen möchten, und navigieren Sie entsprechend zu diesem Abschnitt.

1. Fügen Sie der Datei einen Block mit dem Namen „Formular“ hinzu. Beispiel: Das Repository Ihres Projekts heißt „wefinance“, es befindet sich unter dem Konto „wkndform“ und Sie verwenden die Verzweigung „main“.

   | Formular |
   |---|
   | `https://main--wefinance--wkndform.aem.live/enquiry.json` |

   ![Hinzufügen eines Blocks mit dem Namen „Formular“ zu der Datei](/help/edge/assets/enquiry-doc-to-embed-form.png)

   Dieser Block dient als Platzhalter, in den das Formular eingebettet ist. Fügen Sie in der zweiten Zeile des Blocks die URL Ihrer `<form>.json`-Datei als Hyperlink hinzu.

   >[!IMPORTANT]
   >
   >
   > Stellen Sie sicher, dass die URL als Hyperlink formatiert ist und nicht nur als reiner Text angezeigt wird.

   Verwenden Sie die Vorschau-URL (.page-URL) für Entwicklungs- oder Testzwecke oder die Veröffentlichungs-URL (.live) für die Produktion.

   Beispiel: Das Repository Ihres Projekts heißt „wefinance“, es befindet sich unter dem Konto „wkndform“ und Sie verwenden die Verzweigung „main“.

   Im Folgenden finden Sie Beispiele für Vorschau- und Veröffentlichungs-URLs:

   **Vorschau-URL**

   | Formular |
   |---|
   | `https://main--wefinance--wkndform.aem.page/enquiry.json` |


   **Veröffentlichungs-URL**

   | Formular |
   |---|
   | `https://main--wefinance--wkndform.aem.live/enquiry.json` |

1. Verwenden Sie [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content), um eine Vorschau der Webseite anzuzeigen. Das Formular wird jetzt auf der Seite angezeigt. Hier basiert das Formular beispielsweise auf der [Abfragetabelle](/help/edge/assets/enquiry-form.docx):


   ![Beispiel für ein EDS-Formular](/help/edge/assets/updated-form.png)

1. Verwenden Sie AEM Sidekick, um das Formular zu veröffentlichen. Jetzt können Ihre Kundinnen und Kunden das Formular ausfüllen und absenden.

+++

## Fehlerbehebung

+++ Daten können nicht an ein Formular gesendet werden

Wenn ein Fehler auftritt, der der folgenden Meldung ähnelt, deutet dies darauf hin, dass die Tabelle noch nicht für das [Akzeptieren der übermittelten](/help/edge/docs/forms/submit-forms.md) Daten konfiguriert ist.

![Fehler bei Formularübermittlung](/help/edge/assets/form-error.png)

+++



