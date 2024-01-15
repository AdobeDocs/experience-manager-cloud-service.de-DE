---
title: Übersetzen eines auf Kernkomponenten basierenden adaptiven Formulars?
description: Erfahren Sie, wie Sie ein Formulardatenmodell in AEM Forms erstellen, das Modell mit Beispieldaten und -diensten testen und verschiedene Optionen für ein Modell konfigurieren.
feature: Adaptive Forms, Core Components
exl-id: ad46bf0f-e6ec-4c52-9695-5768a9968e16
source-git-commit: eaab351460363b83c7d3667e048235506cc71c41
workflow-type: tm+mt
source-wordcount: '884'
ht-degree: 96%

---

# Verwenden Sie maschinelle Übersetzung oder menschliche Übersetzung, um ein auf Kernkomponenten basierendes adaptives Formular zu übersetzen. {#using-aem-translation-workflow-to-localize-adaptive-forms-and-document-of-record}

Mit lokalisierten Formularen können Sie eine größere Zielgruppe über Ländergrenzen hinweg ansprechen. Mit den Adobe Experience Manager-Übersetzungs-Workflows können Sie adaptive Formulare und die entsprechenden Datensatzdokumente lokalisieren. Sie können zum Lokalisieren adaptiver Formulare **maschinelle Übersetzung** nutzen oder **Übersetzer** beauftragen.

## Übersetzen eines adaptiven Formulars und Datensatzdokuments mithilfe maschineller Übersetzung {#localizing-an-adaptive-form-and-document-of-record-using-machine-translation}

Der Service für maschinelle Übersetzung übersetzt sofort Inhalte Ihrer adaptiven Formulare und [Datensatzdokumente](/help/forms/generate-document-of-record-core-components.md). AEM Forms as a Cloud Service ist für die Verwendung einer Testversion von Microsoft Translator für die maschinelle Übersetzung vorkonfiguriert. Führen Sie zum Aktivieren des Service für Ihre adaptiven Formulare und Datensatzdokumente folgende Schritte durch:

1. Wählen Sie auf der AEM Forms-Benutzeroberfläche ein Formular aus und wählen Sie die **[!UICONTROL Wörterbuch hinzufügen]** -Option.
1. Auf dem Bildschirm „Wörterbuch zum Übersetzungsprojekt hinzufügen“ für die Option **[!UICONTROL Projekt]**

   * Wählen Sie zum Erstellen eines Übersetzungsprojekts die Option **[!UICONTROL Neues Übersetzungsprojekt erstellen]** aus und legen Sie im Feld **Projekttitel** den Titel fest. Beispiel: `Government Reference Site - German locale.`
   * Um einem vorhandenen Übersetzungsprojekt ein neues Wörterbuch hinzuzufügen, wählen Sie die Option **[!UICONTROL Zu vorhandenem Übersetzungsprojekt hinzufügen]** aus und wählen Sie ein **[!UICONTROL vorhandenes Übersetzungsprojekt]** aus.
1. Geben Sie im Feld **Zielsprachen** ein Gebietsschema an (beispielsweise `German(de)`). Sie können mehrere Gebietsschemata angeben. Das Formular wird in alle im Feld **Zielsprachen** angegebenen Gebietsschemata übersetzt. Klicken Sie auf **Fertig**.
1. Klicken Sie im Dialogfeld „Wörterbuch hinzugefügt“ auf **Projekte öffnen**.
1. Klicken Sie auf dem Bildschirm „Projekte“ auf das erstellte Projekt. Klicken Sie beispielsweise auf den Titel **Referenz-Site Behörde – Gebietsschema Deutsch**.
1. Klicken Sie auf der Kachel **Übersetzungsauftrag** auf das Symbol ![aem62forms_downarrow](assets/aem62forms_downarrow.png) und dann auf **Start**. Der Status der Kachel ändert sich in „Entwurf“. Bei Fertigstellung der Übersetzung ändert sich der Status in **Genehmigt**. Aktualisieren Sie die Seite nach einigen Minuten und überprüfen Sie den Status.

   ![Übersetzung starten](/help/forms/assets/adaptive-forms-core-components-start-translation.png)
1. Nachdem der Status für die Kachel **Übersetzungsauftrag** in **Genehmigt** geändert wurde, klicken Sie auf das Symbol ![aem62forms_downarrow](assets/aem62forms_downarrow.png) und klicken Sie auf **Fertigstellen**.

1. Um eine Vorschau des lokalisierten Formulars in der AEM Forms-Benutzeroberfläche anzuzeigen, wählen Sie das lokalisierte Formular aus. Klicken Sie auf **[!UICONTROL Vorschau]** > **[!UICONTROL Vorschau als HTML]**. Öffnen Sie das Formular erneut, nachdem Sie `afAcceptLang=<locale code>` zur URL des Formulars hinzugefügt haben. Fügen Sie beispielsweise `afAcceptLang=de`hinzu, um die deutsche Version des Formulars zu öffnen.


   >[!NOTE]
   >
   >* Stellen Sie vor dem Öffnen der lokalisierten Version des Formulars im Browserfenster sicher, dass das Gebietsschema des Browsers so eingestellt ist, dass es mit dem Gebietsschema des Formulars übereinstimmt. Wenn beispielsweise das Formular in die Sprache Deutsch(de) übersetzt wird, stellen Sie für das Gebietsschema des Browsers „Deutsch(de)“ ein.
   >* Komponenten für adaptive Formulare unterstützen keine RTL-Sprachen (Right to Left – von rechts nach links). Zum Beispiel Hebräisch.

<!-- 
   Along with the Adaptive form, the auto-generated document of record is also localized.

   For more information on Document of Record settings and configuration, see:

   [Document of Record Template](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#p-document-of-record-template-configuration-p)

   [Document of Record settings](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#p-document-of-record-settings-p)

1. [Customize the branding information of the document of record](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md) and ensure that the browser locale is set to the same language to which you have localized the Adaptive Form using machine language. The browser locale helps localize the branding information in the document of record.
1. To view the localized document of record, select Generate Preview. The document of record PDF is generated and opened in a new tab in your browser.

-->

## Lokalisieren eines adaptiven Formulars und seines Datensatzdokuments mithilfe menschlicher Übersetzung {#localizing-an-adaptive-form-and-its-document-of-record-using-human-translation}

Bei der menschlichen Übersetzung wird der Inhalt an einen Übersetzungsanbieter gesendet und von professionellen Übersetzerinnen oder Übersetzern übersetzt. Wenn die Inhalte übersetzt wurden, werden sie zurückgesendet und in AEM importiert. Ist Ihr Übersetzungsdienstleister in AEM integriert, werden die Inhalte automatisch von AEM an den Übersetzungsdienstleister gesendet.

Für die Übersetzung wird den professionellen Übersetzerinnen oder Übersetzern ein Wörterbuch zur Verfügung gestellt, das Dateien im XLIFF-Format enthält. Das Wörterbuch enthält für jedes Gebietsschema eine separate XLIFF-Datei. Jede XLIFF-Datei enthält Text, der den Endbenutzenden angezeigt wird, und Platzhalter für den entsprechenden lokalisierten Text.

Führen Sie die folgenden Schritte zum Lokalisieren eines Formulars und seines Datensatzdokuments mit menschlicher Übersetzung durch:

1. Wählen Sie auf der AEM Forms-Benutzeroberfläche ein Formular aus und wählen Sie die **[!UICONTROL Wörterbuch hinzufügen]** -Option.
1. Auf dem Bildschirm „Wörterbuch zum Übersetzungsprojekt hinzufügen“ für die Option **[!UICONTROL Projekt]**

   * Wählen Sie zum Erstellen eines Übersetzungsprojekts die Option **[!UICONTROL Neues Übersetzungsprojekt erstellen]** aus und legen Sie im Feld **Projekttitel** den Titel fest. Beispiel: `Government Reference Site - German locale.`
   * Um einem vorhandenen Übersetzungsprojekt ein neues Wörterbuch hinzuzufügen, wählen Sie die Option **[!UICONTROL Zu vorhandenem Übersetzungsprojekt hinzufügen]** aus und wählen Sie ein **[!UICONTROL vorhandenes Übersetzungsprojekt]** aus.
1. Geben Sie im Feld **Zielsprachen** ein Gebietsschema an (beispielsweise `German(de)`). Sie können mehrere Gebietsschemata angeben. Das Formular wird in alle im Feld **Zielsprachen** angegebenen Gebietsschemata übersetzt. Klicken Sie auf **Fertig**.
1. Klicken Sie im Dialogfeld „Wörterbuch hinzugefügt“ auf **Projekte öffnen**.
1. Klicken Sie auf dem Bildschirm „Projekte“ auf das erstellte Projekt. Klicken Sie beispielsweise auf den Titel **Referenz-Site Behörde – Gebietsschema Deutsch**.
1. Klicken Sie am unteren Rand der Kachel **Zusammenfassung** auf die **Auslassungspunkte**. Der Bildschirm „Eigenschaften des Übersetzungsprojekts“ wird geöffnet.
1. Öffnen Sie oben auf dem Bildschirm **Eigenschaften des Übersetzungsprojekts** die Registerkarte **[!UICONTROL Erweitert]**. Wählen Sie für das **[!UICONTROL Übersetzungsfeld]** die Option **[!UICONTROL Menschliche Übersetzung]** aus. Klicken Sie oben auf dem Bildschirm auf **Speichern und schließen**.
1. Klicken Sie auf der Kachel **Übersetzungsauftrag** auf das Symbol ![aem62forms_downarrow](assets/aem62forms_downarrow.png) und dann auf **Exportieren**. Klicken Sie im Dialogfeld „Exportieren“ auf die Option „Exportierte Datei herunterladen“. Es wird eine ZIP-Datei heruntergeladen.
   ![Exportieren einer Übersetzungsdatei](/help/forms/assets/adaptive-forms-core-components-start-translation-export.png)
1. Entpacken Sie die heruntergeladene ZIP-Datei. Der extrahierte Ordner hat zwei Dateien:
   * translation_export_summary.xml
   * [form-fields-file].xml.
1. Öffnen Sie die [form-fields-file].xml zur Bearbeitung. Fügen Sie die lokalisierten Zeichenfolgen und Meldungen für Formularfelder hinzu. Speichern und schließen Sie die Datei.
1. Komprimieren Sie die Dateien „translation_export_summary.xml“ und [form-fields-file].xml.
1. Klicken Sie auf der Kachel **Übersetzungsauftrag** auf das Symbol ![aem62forms_downarrow](assets/aem62forms_downarrow.png) und dann auf **Importieren**. Wählen Sie das Archiv aus, das [form-fields-file].xml enthält. Außerdem sind die lokalisierten Zeichenfolgen und Meldungen für Formularfelder enthalten.

   ![Importieren einer Übersetzungsdatei](/help/forms/assets/adaptive-forms-core-components-start-translation-import.png)

1. Um eine Vorschau des lokalisierten Formulars in der AEM Forms-Benutzeroberfläche anzuzeigen, wählen Sie das lokalisierte Formular aus. Klicken Sie auf **[!UICONTROL Vorschau]** > **[!UICONTROL Vorschau als HTML]**. Öffnen Sie das Formular erneut, nachdem Sie `afAcceptLang=<locale code>` zur URL des Formulars hinzugefügt haben. Fügen Sie beispielsweise `afAcceptLang=de`hinzu, um die deutsche Version des Formulars zu öffnen.

## Siehe auch {#see-also}

{{see-also}}