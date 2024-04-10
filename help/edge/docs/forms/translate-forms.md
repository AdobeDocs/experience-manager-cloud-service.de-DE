---
title: Übersetzen und Lokalisieren eines AEM Forms Edge Delivery ServicesForm
description: Übersetzen und Lokalisieren eines AEM Forms Edge Delivery ServicesForm
feature: Edge Delivery Services
hide: true
hidefromtoc: true
exl-id: 8a0c826f-8acc-4a00-bd84-7b0df9a82457
source-git-commit: eadfc3d448bd2fadce08864ab65da273103a6212
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 1%

---


# Übersetzen und Lokalisieren eines AEM Forms Edge Delivery ServicesForm

Bei Edge Delivery Services umfasst die Formularübersetzung das Konvertieren von Formularinhalten von einer Sprache in eine andere mit dem Schwerpunkt auf Genauigkeit, Klarheit und Konsistenz. Übersetzte oder lokalisierte Formulare ermöglichen eine breitere Reichweite der Zielgruppe über verschiedene geografische Standorte hinweg und verbessern so das Benutzererlebnis und die Kommunikation über verschiedene Sprachpräferenzen hinweg.


Am Ende des Artikels erfahren Sie Folgendes:

* [Übersetzen von Formularen in Google Drive](#translate-form-google-drive)
* [Übersetzen von Formularen innerhalb der SharePoint-Site](#translate-form-sharepoint)

## Übersetzen von Formularen in Google Drive {#translate-form-google-drive}

Die `GOOGLETRANSLATE` -Funktion bei Google Sheets übersetzt Formulare, indem sie auf das integrierte Übersetzungs-Tool tippt und Text direkt in einem Google-Blatt von einer Sprache in eine andere wechselt. So übersetzen Sie Formulare in Google Drive:

1. Wechseln Sie zum AEM-Projektordner auf Google Drive und öffnen Sie das Google-Arbeitsblatt.
2. Umbenennen des vorhandenen Blatts (`shared-default`) bis `shared-en`.
3. Eine Tabelle mit dem Namen hinzufügen `shared-default`. Die `shared-default` Tabelle enthält den Inhalt für die Lokalisierung in eine bestimmte Sprache.
4. Hinzufügen lokalisierter Inhalte in der `shared-default` Blatt mit dem `GOOGLETRANSLATE` Funktion.
Sie können eine Formel verwenden, um den Inhalt der Zelle D2 aus der `shared-en` Blatt in Französisch innerhalb der `shared-default` Blatt. Die folgende Formel ist zu verwenden:
   `=GOOGLETRANSLATE('shared-en'!D2,"en","fr")`

   ![Übersetzungstabelle für Anfragen](/help/forms/assets/translate-enquiry-spreadsheet.png)

5. Anzeigen einer Vorschau und Veröffentlichen des Arbeitsblatts mithilfe von [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).

Weitere Informationen finden Sie im [Kalkulationstabelle](/help/forms/assets/enquirytranslate.xlsx) enthält die Formulardefinition für ein `enquiry` Formular in englischer Sprache übersetzt.

![Übersetztes Anfrageformular](/help/forms/assets/translate-form-french.png)

Unter der folgenden URL sehen Sie das Formular mit der französischen Übersetzung: https://main--portal--wkndforms.hlx.live/enquirytranslate

## Übersetzen von Formularen innerhalb der SharePoint-Site{#translate-form-sharepoint}

Um die Formulare auf der Microsoft® SharePoint-Website zu übersetzen, müssen Sie die Feldbezeichnungen mithilfe eines beliebigen Übersetzungsdienstes manuell ändern. So übersetzen Sie die Formulare auf der SharePoint-Site:

1. Wechseln Sie in Microsoft® SharePoint zu Ihrem AEM-Projektordner und öffnen Sie Ihre Tabelle.
2. Umbenennen des vorhandenen Blatts (`shared-default`) bis `shared-en`.
3. Eine Tabelle mit dem Namen hinzufügen `shared-default`. Die `shared-default` Tabelle enthält den Inhalt für die Lokalisierung in eine bestimmte Sprache.
4. Hinzufügen lokalisierter Inhalte in der `shared-default` Manuell ablegen.

   ![Übersetzungstabelle für Anfragen](/help/forms/assets/translate-enquiry-sp-spreadsheet.png)

5. Anzeigen einer Vorschau und Veröffentlichen des Arbeitsblatts mithilfe von [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).

Siehe [Kalkulationstabelle](/help/forms/assets/enquirytranslate-sp.xlsx) enthält die Formulardefinition für ein `enquiry` Formular in englischer Sprache übersetzt.

![Übersetztes Anfrageformular](/help/forms/assets/translate-form-french.png)

Unter der folgenden URL sehen Sie das Formular mit der französischen Übersetzung: https://main--wefinance--wkndforms.hlx.live/enquirytranslate

## Bekannte Probleme {#known-issues}

* Die Beschriftungen des Formulars werden in die angegebene lokalisierte Sprache in der `shared-default` -Tabelle, aber die Fehlermeldungen werden in der Standardsprache des Browsers angezeigt.

  ![Fehlermeldung](/help/forms/assets/translate-error-message.png)

* Wenn Sie den Kalender öffnen, wird die Dropdown-Liste Kalender in der Standardsprache des Browsers angezeigt.

  ![Fehlermeldung](/help/forms/assets/translate-calender-display.png)


## Häufig gestellte Fragen {#faq}

**Q**: Wie kann ich Eingaben in der angegebenen lokalisierten Sprache in ein Formular eingeben?

**A**: Um Text in einer bestimmten lokalisierten Sprache einzugeben, passen Sie die Tastatureinstellungen auf dem Gerät an. Anweisungen dazu finden Sie unter den folgenden Links:

* [Mac so einrichten, dass Eingaben in einer anderen Sprache erfolgen](https://support.apple.com/en-in/guide/mac-help/mchlp1406/mac)
* [Windows so einrichten, dass Eingaben in einer anderen Sprache erfolgen](https://support.microsoft.com/en-us/windows/manage-the-input-and-display-language-settings-in-windows-12a10cb4-8626-9b77-0ccb-5013e0c7c7a2#:~:text=Select%20the%20Start%20%3E%20Settings%20%3E%20Time,you%20want%2C%20then%20select%20Options)
* [Richten Sie Ihre Android- oder iPhones/iPads so ein, dass Eingaben in einer anderen Sprache erfolgen.](https://support.google.com/gboard/answer/7068494?hl=en&amp;co=GENIE.Platform%3DAndroid)


**Q**: Wie kann ich eine Liste der in der Datei verwendeten Gebietsschemata abrufen? `GOOGLETRANSLATE` Funktion?

**A**: Sie können auf die Datei [Offizielle Dokumentation zu Google](https://cloud.google.com/translate/docs/languages) für eine umfassende Liste der in GOOGLE TRANSLATE verwendeten Sprachen.

## Siehe auch

{{see-more-forms-eds}}

