---
title: AEM Forms Edge Delivery Services-Formular veröffentlichen
description: AEM Forms Edge Delivery Services-Formular veröffentlichen
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: 39bb45b285fcd938d44b9748aa8559b89a3636b2
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 1%

---


# Formular veröffentlichen

Sobald Sie bereit sind, Ihr Formular für Ihre Kunden zur Datenerfassung oder -übermittlung freizugeben, können Sie es einfach veröffentlichen, sodass das Formular für Ihre Kunden zur Verfügung steht.

## Voraussetzungen

* Die [Formularblock ist für Ihr EDS-Projekt auf Github aktiviert](/help/edge/docs/forms/create-forms.md).
* Ihr Formular ist vollständig getestet und einsatzbereit.
* Ihre [Tabelle ist konfiguriert](/help/edge/docs/forms/submit-forms.md) , um Daten zu akzeptieren.

## Formular veröffentlichen

So veröffentlichen Sie das Formular:

1. Greifen Sie auf Ihr Microsoft SharePoint- oder Google Drive-Konto zu und navigieren Sie zu Ihrem `[AEM Edge Delivery project directory]`.

1. Öffnen Sie eine Dokumentdatei, in die Sie das Formular einbetten möchten. Sie können beispielsweise die Indexdatei öffnen oder alternativ ein neues Dokument erstellen.

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

1. Verwendung [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) um eine Vorschau der Seite anzuzeigen. Auf der Seite wird nun das Formular angezeigt. Hier ist beispielsweise das Formular, das auf der Variablen [Fragenübersicht](https://docs.google.com/spreadsheets/d/196lukD028RDK_evBelkOonPxC7w0l_IiJ-Yx3DvMfNk/edit#gid=0):


   [![Beispiel-EDS-Formular](/help/edge/assets/eds-form.png)](https://main--portal--wkndforms.hlx.live/)

   Jetzt können Ihre Kunden das Formular ausfüllen und senden.

## Fehlerbehebung

+++ Daten können nicht an Formular gesendet werden

Wenn ein Fehler auftritt, der der folgenden Meldung ähnelt, deutet dies darauf hin, dass das Arbeitsblatt noch nicht für die Annahme der gesendeten Daten konfiguriert ist.

![Fehler bei Formularübermittlung](/help/edge/assets/form-error.png)

+++


## Mehr anzeigen

* [Erstellen und Anzeigen einer Vorschau eines Formulars](/help/edge/docs/forms/create-forms.md)
* [Formular zum Senden von Daten aktivieren](/help/edge/docs/forms/submit-forms.md)
* [Veröffentlichen eines Formulars auf der Siteseite](/help/edge/docs/forms/publish-eds-forms.md)
* [Hinzufügen von Überprüfungen zu Formularfeldern](/help/edge/docs/forms/validate-forms.md)
* [Designs und Formularstil ändern](/help/edge/docs/forms/style-theme-forms.md)
