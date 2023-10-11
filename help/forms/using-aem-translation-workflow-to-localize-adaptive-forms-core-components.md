---
title: Wie können wir ein auf Kernkomponenten basierendes adaptives Formular übersetzen?
description: Erfahren Sie, wie Sie ein Formulardatenmodell in AEM Forms erstellen, das Modell mit Beispieldaten und -diensten testen und verschiedene Optionen für ein Modell konfigurieren.
feature: Adaptive Forms
exl-id: ad46bf0f-e6ec-4c52-9695-5768a9968e16
source-git-commit: 7a65aa82792500616f971df52b8ddb6d893ab89d
workflow-type: tm+mt
source-wordcount: '894'
ht-degree: 21%

---

# Verwenden Sie maschinelle Übersetzung oder menschliche Übersetzung, um ein auf Kernkomponenten basierendes adaptives Formular zu übersetzen. {#using-aem-translation-workflow-to-localize-adaptive-forms-and-document-of-record}

Mit lokalisierten Formularen können Sie eine größere Zielgruppe über Ländergrenzen hinweg ansprechen. Mit den Adobe Experience Manager-Übersetzungs-Workflows können Sie adaptive Formulare und die entsprechenden Datensatzdokumente lokalisieren. Sie können zum Lokalisieren adaptiver Formulare **maschinelle Übersetzung** nutzen oder **Übersetzer** beauftragen.

## Übersetzen eines adaptiven Formulars und Datensatzdokuments mithilfe der maschinellen Übersetzung {#localizing-an-adaptive-form-and-document-of-record-using-machine-translation}

Der Dienst für maschinelle Übersetzung übersetzt Ihre Inhalte sofort in das adaptive Formular und [Datensatzdokument](/help/forms/generate-document-of-record-core-components.md). AEM Forms as a Cloud Service ist für die Verwendung einer Testversion von Microsoft Translator für maschinelle Übersetzung vorkonfiguriert. Führen Sie zum Aktivieren des Dienstes für Ihre adaptiven Formulare und Datensatzdokumente folgende Schritte durch:

1. Wählen Sie auf der Benutzeroberfläche von AEM Forms ein Formular aus und tippen Sie auf die Option **[!UICONTROL Wörterbuch hinzufügen]**.
1. Im Bildschirm &quot;Wörterbuch zum Übersetzungsprojekt hinzufügen&quot;für **[!UICONTROL Projekt]** option

   * Um ein Übersetzungsprojekt zu erstellen, wählen Sie die **[!UICONTROL Neues Übersetzungsprojekt erstellen]** und in der **Projekttitel** -Feld geben Sie den Titel an. Zum Beispiel: `Government Reference Site - German locale.`
   * Um einem vorhandenen Übersetzungsprojekt ein neues Wörterbuch hinzuzufügen, wählen Sie die **[!UICONTROL Hinzufügen zu einem vorhandenen Übersetzungsprojekt]** und wählen Sie eine **[!UICONTROL Vorhandenes Übersetzungsprojekt]**.
1. Im **Zielsprachen** ein Gebietsschema (z. B. `German(de)`). Sie können mehrere Gebietsschemas angeben. Das Formular wird in alle im Feld **Zielsprachen** angegebenen Gebietsschemas übersetzt. Klicken Sie auf **Fertig**.
1. Klicken Sie im Dialogfeld Wörterbuch hinzugefügt auf **Projekte öffnen**.
1. Klicken Sie im Bildschirm &quot;Projekte&quot;auf das neu erstellte Projekt. Klicken Sie beispielsweise auf die **Referenzseite für Behörden - Gebietsschema Deutsch** Kachel.
1. Klicken Sie auf der Kachel **Übersetzungsauftrag** auf das Symbol ![aem62forms_downarrow](assets/aem62forms_downarrow.png) und dann auf **Start**. Der Status der Kachel ändert sich in Entwurf. Nach Abschluss der Übersetzung ändert sich der Status in **Genehmigt**. Aktualisieren Sie die Seite nach einigen Minuten und überprüfen Sie den Status.

   ![Übersetzung starten](/help/forms/assets/adaptive-forms-core-components-start-translation.png)
1. Nachdem sich der Status in **Genehmigt** auf **Übersetzungsauftrag** klicken Sie auf die ![aem62forms_downarrow](assets/aem62forms_downarrow.png) und klicken Sie auf **Fertig**.

1. Um das lokalisierte Formular in der AEM Forms-Benutzeroberfläche als Vorschau anzuzeigen, wählen Sie das lokalisierte Formular aus. Klicks **[!UICONTROL Vorschau]** >**[!UICONTROL Vorschau als HTML]**. Öffnen Sie das Formular erneut, nachdem Sie die `afAcceptLang=<locale code>` zur URL des Formulars. Fügen Sie beispielsweise `afAcceptLang=de`, um die deutsche Version des Formulars zu öffnen.


   >[!NOTE]
   >
   >* Bevor Sie die lokalisierte Version des Formulars im Browserfenster öffnen, stellen Sie sicher, dass das Gebietsschema des Browsers auf das Gebietsschema des Formulars eingestellt ist. Wenn das Formular beispielsweise in die Sprache Deutsch(de) übersetzt wird, setzen Sie das Gebietsschema des Browsers auf Deutsch(de).
   >* Komponenten für adaptive Formulare unterstützen keine RTL-Sprachen (Right to Left – von rechts nach links). Zum Beispiel Hebräisch.

<!-- 
   Along with the Adaptive form, the auto-generated document of record is also localized.

   For more information on Document of Record settings and configuration, see:

   [Document of Record Template](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#p-document-of-record-template-configuration-p)

   [Document of Record settings](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#p-document-of-record-settings-p)

1. [Customize the branding information of the document of record](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md) and ensure that the browser locale is set to the same language to which you have localized the Adaptive Form using machine language. The browser locale helps localize the branding information in the document of record.
1. To view the localized document of record, tap Generate Preview. The document of record PDF is generated and opened in a new tab in your browser.

-->

## Lokalisieren eines adaptiven Formulars und seines Datensatzdokuments mithilfe der menschlichen Übersetzung {#localizing-an-adaptive-form-and-its-document-of-record-using-human-translation}

Bei der menschlichen Übersetzung werden die Inhalte an einen Übersetzungsanbieter gesendet und von professionellen Übersetzern übersetzt. Wenn die Inhalte übersetzt wurden, werden sie zurückgesendet und in AEM importiert. Ist Ihr Übersetzungsdienstleister in AEM integriert, werden die Inhalte automatisch von AEM an den Übersetzungsdienstleister gesendet.

Für die Übersetzung wird ein Wörterbuch mit Dateien im XLIFF-Format für die professionellen Übersetzer freigegeben. Das Wörterbuch enthält eine separate XLIFF-Datei für jedes Gebietsschema. Jede XLIFF-Datei enthält Text, der den Endbenutzern angezeigt wird, sowie Platzhalter für den entsprechenden lokalisierten Text.

Führen Sie die folgenden Schritte aus, um ein Formular und sein Datensatzdokument mithilfe von Übersetzern zu lokalisieren:

1. Wählen Sie auf der Benutzeroberfläche von AEM Forms ein Formular aus und tippen Sie auf die Option **[!UICONTROL Wörterbuch hinzufügen]**.
1. Im Bildschirm &quot;Wörterbuch zum Übersetzungsprojekt hinzufügen&quot;für **[!UICONTROL Projekt]** option

   * Um ein Übersetzungsprojekt zu erstellen, wählen Sie die **[!UICONTROL Neues Übersetzungsprojekt erstellen]** und in der **Projekttitel** -Feld geben Sie den Titel an. Zum Beispiel: `Government Reference Site - German locale.`
   * Um einem vorhandenen Übersetzungsprojekt ein neues Wörterbuch hinzuzufügen, wählen Sie die **[!UICONTROL Hinzufügen zu einem vorhandenen Übersetzungsprojekt]** und wählen Sie eine **[!UICONTROL Vorhandenes Übersetzungsprojekt]**.
1. Im **Zielsprachen** ein Gebietsschema (z. B. `German(de)`). Sie können mehrere Gebietsschemas angeben. Das Formular wird in alle im Feld **Zielsprachen** angegebenen Gebietsschemas übersetzt. Klicken Sie auf **Fertig**.
1. Klicken Sie im Dialogfeld Wörterbuch hinzugefügt auf **Projekte öffnen**.
1. Klicken Sie im Bildschirm &quot;Projekte&quot;auf das neu erstellte Projekt. Klicken Sie beispielsweise auf die **Referenzseite für Behörden - Gebietsschema Deutsch** Kachel.
1. Am unteren Rand des **Zusammenfassung** klicken Sie auf die **Ellipsen**. Der Bildschirm Eigenschaften des Übersetzungsprojekts wird geöffnet.
1. Öffnen Sie die **[!UICONTROL Erweitert]** Registerkarte oben im **Eigenschaften des Übersetzungsprojekts** angezeigt. Für **[!UICONTROL Übersetzungsfeld]** auswählen **[!UICONTROL Menschliche Übersetzung]**. Klicks **Speichern und schließen** oben auf dem Bildschirm.
1. Im **Übersetzungsauftrag** klicken Sie auf die ![aem62forms_downarrow](assets/aem62forms_downarrow.png) und klicken Sie auf **Export**. Klicken Sie im Dialogfeld Exportieren auf die Option Exportierte Datei herunterladen . Es lädt eine ZIP-Datei herunter.
   ![Übersetzungsdatei exportieren](/help/forms/assets/adaptive-forms-core-components-start-translation-export.png)
1. Extrahieren Sie die heruntergeladene ZIP-Datei. Der extrahierte Ordner hat zwei Dateien:
   * translation_export_summary.xml
   * [form-fields-file].xml
1. Öffnen Sie die [form-fields-file].xml zur Bearbeitung. Fügen Sie die lokalisierten Zeichenfolgen und Meldungen für Formularfelder hinzu. Speichern und schließen Sie die Datei.
1. Komprimieren Sie die Dateien &quot;translation_export_summary.xml&quot;und [form-fields-file].xml
1. Im **Übersetzungsauftrag** klicken Sie auf die ![aem62forms_downarrow](assets/aem62forms_downarrow.png) und klicken Sie auf **Import**. Wählen Sie das Archiv aus, das [form-fields-file].xml mit lokalisierten Zeichenfolgen und Meldungen für Formularfelder.

   ![Importieren einer Übersetzungsdatei](/help/forms/assets/adaptive-forms-core-components-start-translation-import.png)

1. Um das lokalisierte Formular in der AEM Forms-Benutzeroberfläche als Vorschau anzuzeigen, wählen Sie das lokalisierte Formular aus. Klicks **[!UICONTROL Vorschau]** >**[!UICONTROL Vorschau als HTML]**. Öffnen Sie das Formular erneut, nachdem Sie die `afAcceptLang=<locale code>` zur URL des Formulars. Fügen Sie beispielsweise `afAcceptLang=de`, um die deutsche Version des Formulars zu öffnen.
