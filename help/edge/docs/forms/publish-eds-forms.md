---
title: AEM Forms Edge Delivery Services-Formular veröffentlichen
description: AEM Forms Edge Delivery Services-Formular veröffentlichen
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: d0c4f2f880ef7c11b11144502d30430336ac682e
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 1%

---


# Formular veröffentlichen

Sobald Sie bereit sind, Ihr Formular für Ihre Kunden zur Datenerfassung oder -übermittlung freizugeben, können Sie es einfach veröffentlichen, sodass das Formular für Ihre Kunden zur Verfügung steht.

![Dokumentenbasiertes Authoring-Ökosystem](/help/edge/assets/document-based-authoring-workflow-publish-form.png)

## Voraussetzungen

* Die [Der adaptive Formularblock ist für Ihr EDS-Projekt auf GitHub aktiviert](/help/edge/docs/forms/create-forms.md).
* Ihr Formular ist vollständig getestet und einsatzbereit.
* Ihre [Tabelle ist konfiguriert](/help/edge/docs/forms/submit-forms.md) , um Daten zu akzeptieren.

## Formular veröffentlichen

+++ 1. Veröffentlichen Sie Ihr Arbeitsblatt

1. Öffnen Sie Ihr Microsoft SharePoint- oder Google Drive-Konto und navigieren Sie zu Ihrem AEM Edge Delivery-Projektverzeichnis.

1. Öffnen Sie die Tabelle, die Ihr Formular enthält. Beispiel: die `enquiry` aus der Microsoft Excel-Arbeitsmappe erstellen.

1. Verwendung [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) um eine Vorschau des Blattes anzuzeigen.

   ![Verwenden Sie AEM Sidekick, um eine Vorschau der Tabelle anzuzeigen](/help/edge/assets/preview-form.png)

   Nach erfolgreichem Abschluss des Vorschauvorgangs wird der Tabelleninhalt in das JSON-Format konvertiert. Auf der Vorschauseite wird dieser Inhalt dann in einem strukturierten Tabellenformat dargestellt. Beispielsweise veranschaulicht das begleitende Bild den Inhalt eines &#39;Anfrageformulars&#39;.

   ![Forms-Vorschau-JSON-Format](/help/edge/assets/forms-preview-json-format.png)

1. Verwenden Sie AEM Sidekick, um das Blatt zu veröffentlichen. Stellen Sie sicher, dass Sie die Veröffentlichungs-URL erfassen, da dies für die Wiedergabe des Formulars im nächsten Abschnitt erforderlich ist. Die URL hat das folgende Format:


   ```JSON
       https://<branch>--<repository>--<owner>.hlx.live/<form>.json
   ```

   * `<branch>` bezieht sich auf die Verzweigung Ihres GitHub-Repository.
   * `<repository>` bezeichnet Ihr GitHub-Repository.
   * `<owner>` bezieht sich auf den Benutzernamen Ihres GitHub-Kontos, das Ihr GitHub-Repository hostet.

   Wenn das Repository Ihres Projekts beispielsweise &quot;Portal&quot;heißt, befindet es sich unter dem Konto &quot;wkndforms&quot;und Sie die Verzweigung &quot;main&quot;verwenden, sieht die URL wie folgt aus:

   `https://main--portal--wkndforms.hlx.page/enquiry.json`

+++

+++ 2. Fügen Sie das Formular zu Ihrer Webseite hinzu.

Fügen Sie die `<form>.json` auf eine Webseite zu gelangen, um die Interaktion mit dem Kunden zu erleichtern und es dem Benutzer zu ermöglichen, das Formular mühelos auszufüllen und zu versenden.


So fügen Sie das Formular zu Ihrer Webseite hinzu:

1. Greifen Sie auf Ihr Microsoft SharePoint- oder Google Drive-Konto zu und navigieren Sie zu Ihrem `[AEM Edge Delivery project directory]`.

1. Öffnen Sie eine Dokumentdatei, in die Sie das Formular einbetten möchten. Sie können beispielsweise die `index.docx` -Datei oder erstellen Sie alternativ ein neues Dokument.

1. Identifizieren Sie den gewünschten Abschnitt im Dokument, in das Sie das Formular einfügen möchten, und navigieren Sie entsprechend zu ihm.

1. Fügen Sie der Datei einen Baustein mit dem Namen &quot;Formular&quot;hinzu, ähnlich wie im folgenden Beispiel:

   | Formular |
   |---|
   | [https://main—portal—wkndforms.hlx.live/inquiry.json](https://main--portal--wkndforms.hlx.live/enquiry.json) |

   Dieser Block dient als Platzhalter, in den das Formular eingebettet ist. Fügen Sie in der zweiten Zeile des Blocks die URL Ihrer `<form>.json` als Hyperlink.

   >[!IMPORTANT]
   >
   >
   > Stellen Sie sicher, dass die URL als Hyperlink formatiert ist, anstatt als Nur-Text angezeigt zu werden.

   Verwenden Sie die Vorschau-URL (.page-URL) für Entwicklungs- oder Testzwecke oder die Veröffentlichungs-URL (.live) für die Produktion. Im Folgenden finden Sie Beispiele für Vorschau- und Veröffentlichungs-URLs:

   **Vorschau-URL**
| Formular | |—| | [https://main—portal—wkndforms.hlx.page/inquiry.json](https://main--portal--wkndforms.hlx.page/enquiry.json)  |


   **Veröffentlichungs-URL**
| Formular | |—| | [https://main—portal—wkndforms.hlx.live/inquiry.json](https://main--portal--wkndforms.hlx.live/enquiry.json)  |

1. Verwendung [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) um eine Vorschau der Webseite anzuzeigen. Auf der Seite wird nun das Formular angezeigt. Hier ist beispielsweise das Formular, das auf der Variablen [Fragenübersicht](https://docs.google.com/spreadsheets/d/196lukD028RDK_evBelkOonPxC7w0l_IiJ-Yx3DvMfNk/edit#gid=0):


   [![Beispiel-EDS-Formular](/help/edge/assets/eds-form.png)](https://main--portal--wkndforms.hlx.live/)

1. Verwenden Sie AEM Sidekick, um das Formular zu veröffentlichen. Jetzt können Ihre Kunden das Formular ausfüllen und senden.

+++

## Fehlerbehebung

+++ Daten können nicht an Formular gesendet werden

Wenn ein Fehler auftritt, der der folgenden Meldung ähnelt, deutet dies darauf hin, dass das Arbeitsblatt nicht für [die übermittelten](/help/edge/docs/forms/submit-forms.md) -Daten.

![Fehler bei Formularübermittlung](/help/edge/assets/form-error.png)

+++


## Mehr anzeigen

* [Erstellen und Anzeigen einer Vorschau eines Formulars](/help/edge/docs/forms/create-forms.md)
* [Formular zum Senden von Daten aktivieren](/help/edge/docs/forms/submit-forms.md)
* [Veröffentlichen eines Formulars auf der Siteseite](/help/edge/docs/forms/publish-eds-forms.md)
* [Hinzufügen von Überprüfungen zu Formularfeldern](/help/edge/docs/forms/validate-forms.md)
* [Designs und Formularstil ändern](/help/edge/docs/forms/style-theme-forms.md)
