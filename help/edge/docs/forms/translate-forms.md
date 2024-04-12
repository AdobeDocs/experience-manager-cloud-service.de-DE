---
title: Übersetzen und Lokalisieren eines AEM Forms Edge Delivery Service-Formulars
description: Übersetzen und Lokalisieren eines AEM Forms Edge Delivery Service-Formulars
feature: Edge Delivery Services
hide: true
hidefromtoc: true
exl-id: 8a0c826f-8acc-4a00-bd84-7b0df9a82457
source-git-commit: eadfc3d448bd2fadce08864ab65da273103a6212
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 6%

---


# Übersetzen und Lokalisieren eines AEM Forms Edge Delivery Service-Formulars

In Edge Delivery Services umfasst die Formularübersetzung die Konvertierung von Formularinhalten von einer Sprache in eine andere, wobei der Schwerpunkt auf Genauigkeit, Klarheit und Konsistenz liegt. Übersetzte oder lokalisierte Formulare ermöglichen eine breitere Reichweite der Zielgruppen über verschiedene geografische Standorte hinweg, wodurch das Benutzererlebnis verbessert und die Kommunikation über verschiedene Sprachpräferenzen hinweg erleichtert wird.


Am Ende des Artikels lernen Sie Folgendes:

* [Übersetzen von Formularen in Google Drive](#translate-form-google-drive)
* [Übersetzen von Formularen in SharePoint Site](#translate-form-sharepoint)

## Übersetzen von Formularen in Google Drive {#translate-form-google-drive}

Die `GOOGLETRANSLATE` -Funktion in Google-Arbeitsblättern übersetzt Formulare durch Tippen in ein integriertes Übersetzungstool, wobei Text direkt in einem Google-Arbeitsblatt von einer Sprache in eine andere geändert wird. So übersetzen Sie Formulare in Google Drive:

1. Wechseln Sie zu Ihrem AEM-Projektordner auf Google Drive und öffnen Sie Ihr Google-Blatt.
2. Benennen Sie das vorhandene Blatt um (`shared-default`) zu `shared-en`.
3. Fügen Sie ein Blatt mit dem Namen `shared-default`. Die `shared-default` Die Tabelle enthält den Inhalt für die Lokalisierung in eine bestimmte Sprache.
4. Fügen Sie den lokalisierten Inhalt im `shared-default` mit dem `GOOGLETRANSLATE` -Funktion.
Sie können eine Formel verwenden, um den Inhalt der Zelle D2 aus der `shared-en` Blatt in Französisch innerhalb der `shared-default` Blatt. Die Formel lautet wie folgt:
   `=GOOGLETRANSLATE('shared-en'!D2,"en","fr")`

   ![Abfrage Übersetzen von Tabellen](/help/forms/assets/translate-enquiry-spreadsheet.png)

5. Erstellen Sie eine Vorschau und veröffentlichen Sie das Blatt mit [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).

Weitere Informationen finden Sie unter [Tabellenblatt](/help/forms/assets/enquirytranslate.xlsx) mit der Formulardefinition für eine `enquiry` Formular übersetzt von Englisch in Französisch.

![Formular für übersetzte Abfrage](/help/forms/assets/translate-form-french.png)

Sehen Sie sich die folgende URL an, unter der Sie das Formular mit der französischen Übersetzung anzeigen können: https://main—portal—wkndforms.hlx.live/enquirytranslate

## Übersetzen von Formularen in SharePoint Site{#translate-form-sharepoint}

Um die Formulare auf der Microsoft® SharePoint-Site zu übersetzen, müssen Sie die Feldbezeichnungen mithilfe eines beliebigen Übersetzungsdienstes manuell ändern. So übersetzen Sie die Formulare auf der SharePoint-Site:

1. Wechseln Sie in Microsoft® SharePoint zu Ihrem AEM-Projektordner und öffnen Sie das Arbeitsblatt.
2. Benennen Sie das vorhandene Blatt um (`shared-default`) zu `shared-en`.
3. Fügen Sie ein Blatt mit dem Namen `shared-default`. Die `shared-default` Die Tabelle enthält den Inhalt für die Lokalisierung in eine bestimmte Sprache.
4. Fügen Sie den lokalisierten Inhalt im `shared-default` Blatt manuell.

   ![Abfrage Übersetzen von Tabellen](/help/forms/assets/translate-enquiry-sp-spreadsheet.png)

5. Erstellen Sie eine Vorschau und veröffentlichen Sie das Blatt mit [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).

Siehe Abschnitt [Tabellenblatt](/help/forms/assets/enquirytranslate-sp.xlsx) mit der Formulardefinition für eine `enquiry` Formular übersetzt von Englisch in Französisch.

![Formular für übersetzte Abfrage](/help/forms/assets/translate-form-french.png)

Sehen Sie sich die folgende URL an, unter der Sie das Formular mit der französischen Übersetzung anzeigen können: https://main—wefinance—wkndforms.hlx.live/enquirytranslate

## Bekannte Probleme {#known-issues}

* Die Beschriftungen des Formulars werden in die angegebene lokalisierte Sprache in der `shared-default` hinzugefügt, aber die Fehlermeldungen werden in der Standardsprache des Browsers angezeigt.

  ![Fehlermeldung](/help/forms/assets/translate-error-message.png)

* Wenn Sie den Kalender öffnen, wird die Dropdownliste Kalender in der Standardsprache des Browsers angezeigt.

  ![Fehlermeldung](/help/forms/assets/translate-calender-display.png)


## Häufig gestellte Fragen {#faq}

**Q**: Wie kann ich die Eingabe in die angegebene lokalisierte Sprache in ein Formular eingeben?

**A**: Um Text in einer bestimmten lokalisierten Sprache einzugeben, passen Sie die Tastatureinstellungen auf Ihrem Gerät an. Anweisungen dazu finden Sie unter den folgenden Links:

* [Einrichten der Mac für die Eingabe in einer anderen Sprache](https://support.apple.com/en-in/guide/mac-help/mchlp1406/mac)
* [Windows für die Eingabe in einer anderen Sprache einrichten](https://support.microsoft.com/en-us/windows/manage-the-input-and-display-language-settings-in-windows-12a10cb4-8626-9b77-0ccb-5013e0c7c7a2#:~:text=Select%20the%20Start%20%3E%20Settings%20%3E%20Time,you%20want%2C%20then%20select%20Options)
* [Richten Sie Ihre Android- oder iPhones/iPads ein, um Eingaben in einer anderen Sprache durchzuführen](https://support.google.com/gboard/answer/7068494?hl=en&amp;co=GENIE.Platform%3DAndroid)


**Q**: Wie kann ich eine Liste der Gebietsschemas abrufen, die in der Variablen `GOOGLETRANSLATE` Funktion?

**A**: Weitere Informationen finden Sie unter [Offizielle Dokumentation zu Google](https://cloud.google.com/translate/docs/languages) für eine umfassende Liste der Gebietsschemas, die im GOOGLETRANSLATE verwendet werden.

## Siehe auch

{{see-more-forms-eds}}

