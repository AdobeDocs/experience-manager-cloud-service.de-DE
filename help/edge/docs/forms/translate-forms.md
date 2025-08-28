---
title: Übersetzen und Lokalisieren von Edge Delivery Services für AEM Forms
description: Übersetzen und Lokalisieren von Edge Delivery Services für AEM Forms
feature: Edge Delivery Services
hide: true
hidefromtoc: true
exl-id: 8a0c826f-8acc-4a00-bd84-7b0df9a82457
role: Admin, Architect, Developer
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: ht
source-wordcount: '544'
ht-degree: 100%

---


# Übersetzen und Lokalisieren von Edge Delivery Services für AEM Forms

In Edge Delivery Services umfasst die Formularübersetzung die Übertragung von Formularinhalten von einer Sprache in eine andere, wobei der Schwerpunkt auf Genauigkeit, Klarheit und Einheitlichkeit liegt. Übersetzte oder lokalisierte Formulare ermöglichen eine breitere Reichweite der Zielgruppen über verschiedene geografische Standorte hinweg, wodurch das Benutzererlebnis verbessert und die Kommunikation über verschiedene Sprachpräferenzen hinweg erleichtert wird.


Am Ende des Artikels werden Sie Folgendes gelernt haben:

- [das Übersetzen von Formularen in Google Drive](#translate-form-google-drive)
- [das Übersetzen von Formularen in einer SharePoint-Site](#translate-form-sharepoint)

## das Übersetzen von Formularen in Google Drive {#translate-form-google-drive}

Die Funktion `GOOGLETRANSLATE` in Google Sheets übersetzt Formulare, indem sie das native Übersetzungs-Tool nutzt und direkt in einem Google Sheet den Text von einer Sprache in eine andere ändert. So übersetzen Sie Formulare in Google Drive:

1. Wechseln Sie zu Ihrem AEM-Projektordner auf Google Drive und öffnen Sie Ihr Google Sheet.
2. Benennen Sie das vorhandene Sheet (`shared-default`) in `shared-en` um.
3. Fügen Sie ein Sheet mit dem Namen `shared-default` hinzu. Das Sheet `shared-default` enthält den Inhalt für die Lokalisierung in eine bestimmte Sprache.
4. Fügen Sie den lokalisierten Inhalt mithilfe der `GOOGLETRANSLATE`-Funktion im Sheet `shared-default` ein.
Sie können eine Formel verwenden, um den Inhalt der Zelle D2 aus dem Sheet `shared-en` ins Französische im Sheet `shared-default` zu übersetzen. Die Formel lautet wie folgt:
   `=GOOGLETRANSLATE('shared-en'!D2,"en","fr")`

   ![Abfrage – Tabelle übersetzen](/help/forms/assets/translate-enquiry-spreadsheet.png)

5. Erstellen Sie eine Vorschau und veröffentlichen Sie das Sheet mit [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).

Sehen Sie sich die [Tabelle](/help/forms/assets/enquirytranslate.xlsx) an, die die Formulardefinition für ein `enquiry`-Formular enthält, das vom Englischen ins Französische übersetzt wurde.

![Abfrage – übersetztes Formular](/help/forms/assets/translate-form-french.png)

Anhand der folgenden URL können Sie das Formular mit der französischen Übersetzung anzeigen:
https://main--portal--wkndforms.hlx.live/enquirytranslate

## das Übersetzen von Formularen in einer SharePoint-Site{#translate-form-sharepoint}

Um die Formulare auf der Microsoft® SharePoint-Site zu übersetzen, müssen Sie die Feldbezeichnungen mithilfe eines beliebigen Übersetzungsdienstes manuell ändern. So übersetzen Sie die Formulare auf der SharePoint-Site:

1. Navigieren Sie in Microsoft® SharePoint zu Ihrem AEM-Projektordner und öffnen Sie die Tabelle.
2. Benennen Sie das vorhandene Sheet (`shared-default`) in `shared-en` um.
3. Fügen Sie ein Sheet mit dem Namen `shared-default` hinzu. Das Sheet `shared-default` enthält den Inhalt für die Lokalisierung in eine bestimmte Sprache.
4. Fügen Sie den lokalisierten Inhalt im Sheet `shared-default` manuell ein.

   ![Abfrage – Kalkulationstabelle übersetzen](/help/forms/assets/translate-enquiry-sp-spreadsheet.png)

5. Erstellen Sie eine Vorschau und veröffentlichen Sie das Sheet mit [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).

Sehen Sie sich die [Kalkulationstabelle](/help/forms/assets/enquirytranslate-sp.xlsx) an, die die Formulardefinition für ein `enquiry`-Formular enthält, das vom Englischen ins Französische übersetzt wurde.

![Abfrage – übersetztes Formular](/help/forms/assets/translate-form-french.png)

Anhand der folgenden URL können Sie das Formular mit der französischen Übersetzung anzeigen:
https://main--wefinance--wkndforms.hlx.live/enquirytranslate

## Bekannte Probleme {#known-issues}

- Die Beschriftungen des Formulars werden in die angegebene lokalisierte Sprache im Sheet `shared-default` hinzugefügt, aber die Fehlermeldungen werden in der Standardsprache des Browsers angezeigt.

  ![Fehlermeldung](/help/forms/assets/translate-error-message.png)

- Wenn Sie den Kalender öffnen, wird die Kalender-Dropdown-Liste in der Standardsprache des Browsers angezeigt.

  ![Fehlermeldung](/help/forms/assets/translate-calender-display.png)


## Häufig gestellte Fragen {#faq}

**F**: Wie kann ich in einem Formular Eingaben in der angegebenen lokalisierten Sprache machen?

**A**: Um Text in einer bestimmten lokalisierten Sprache einzugeben, passen Sie die Tastatureinstellungen auf Ihrem Gerät an. Anweisungen dazu finden Sie unter den folgenden Links:

- [Einrichten Ihres Mac für die Eingabe in einer anderen Sprache](https://support.apple.com/en-in/guide/mac-help/mchlp1406/mac)
- [Einrichten von Windows für die Eingabe in einer anderen Sprache](https://support.microsoft.com/en-us/windows/manage-the-input-and-display-language-settings-in-windows-12a10cb4-8626-9b77-0ccb-5013e0c7c7a2#:~:text=Select%20the%20Start%20%3E%20Settings%20%3E%20Time,you%20want%2C%20then%20select%20Options)
- [Einrichten Ihres Android-Geräts oder iPhones/iPads für die Eingabe in einer anderen Sprache](https://support.google.com/gboard/answer/7068494?hl=en&co=GENIE.Platform%3DAndroid)


**F**: Wie kann ich eine Liste der in der `GOOGLETRANSLATE`-Funktion verwendeten Gebietsschemata abrufen?

**A**: Weitere Informationen finden Sie in der [offiziellen Dokumentation zu Google](https://cloud.google.com/translate/docs/languages) für eine umfassende Liste der Gebietsschemata, die in GOOGLETRANSLATE verwendet werden.


