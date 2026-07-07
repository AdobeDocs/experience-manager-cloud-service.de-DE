---
title: Anwenden von smartem Zuschneiden für Videos auf genehmigte Videos
description: Mit den Dynamic Media-Funktionen mit OpenAPI können Sie in Adobe Experience Manager (AEM) Smart-Crop-Ausgaben für Video-Assets generieren.
role: Admin, User
badgeSaas: label="AEM Assets" type="Positive" tooltip="Gilt für AEM Assets."
source-git-commit: bcdfc9bb418ab405faa82c55820a6ec6062c2b17
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 17%

---

# Anwenden von smartem Zuschneiden für Videos auf genehmigte Videos {#apply-video-smart-crops-dmwoapi}

[!DNL Dynamic Media with OpenAPI capabilities] können Sie in [!DNL Adobe Experience Manager (AEM)] intelligente zugeschnittene Videoausgänge für Video-Assets generieren.

Smartes Zuschneiden von Videos analysiert Videoinhalte und passt das Framing dynamisch an, um das Hauptthema auf verschiedenen Seitenverhältnissen und Geräten im Fokus zu halten.

Um diese Funktion zu verwenden, konfigurieren Sie das Metadatenschema für Video-Assets. Nach der Aktivierung können Benutzer smartes Zuschneiden für Videos anwenden, indem sie die Asset-Metadaten aktualisieren und das Asset genehmigen.

## Voraussetzungen {#prerequisites-for-video-smart-crops}

Stellen Sie sicher, dass Sie über Folgendes verfügen:

* Sie haben Zugriff auf [!DNL AEM Assets as a Cloud Service].
* Berechtigung zum Bearbeiten von Metadatenschemata.
* Dynamic Media mit für Ihre Umgebung aktivierten OpenAPI-Funktionen.
* In AEM Assets verfügbare Video-Assets

## Aktivieren von smartem Zuschneiden für Videos (Admin) {#enable-video-smart-crops}

Um smartes Zuschneiden für Videos zu aktivieren, konfigurieren Sie das Metadatenschema, das für Video-Assets verwendet wird.

Führen Sie die folgenden Schritte aus:

1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadatenschemata]**.
1. Öffnen Sie das auf Ihre Video-Assets angewendete Metadatenschema und klicken Sie auf **[!UICONTROL Bearbeiten]**.
1. Wählen Sie im Metadatenschema-Editor die Registerkarte **[!UICONTROL Video]** aus.
1. Ziehen Sie aus dem **[!UICONTROL Formular erstellen]** die Komponente **[!UICONTROL Dropdown]** in das Formular.

   ![Feld „Video-SmartCrops erstellen“ zum Metadatenschema hinzugefügt](/help/assets/assets/metadata-schema-form.png)

1. Wählen Sie das neu hinzugefügte Feld aus und konfigurieren Sie Folgendes im Bedienfeld **[!UICONTROL Einstellungen]**:

   * **Feldbezeichnung**: Geben Sie eine Feldbezeichnung Ihrer Wahl an.
   * **Zu Eigenschaft zuordnen**: `./jcr:content/dam:applyVideoSmartCrop`

1. Fügen **[!UICONTROL im Abschnitt]** die folgenden Werte hinzu:

   * Ja → wahr
   * Keine → falsch

   ![Konfigurieren des SmartCrop-Felds „Video erstellen“](/help/assets/assets/edit-setting1.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**.

>[!NOTE]
>
>Wenn das `dm_video` Metadatenschema in Ihrer Umgebung verwendet wird, stellen Sie sicher, dass dieselbe Konfiguration auch auf das `dm_video` angewendet wird. Dadurch wird ein konsistentes Verhalten von smartem Zuschneiden für alle Videoschematypen sichergestellt.

## Anwenden von smartem Zuschneiden für Videos auf genehmigte Videos {#apply-video-smart-crops}

Sie können smartes Zuschneiden von Videos auf Video-Assets anwenden, indem Sie das Metadatenfeld aktivieren und das Asset genehmigen.

Führen Sie die folgenden Schritte aus:

1. Wählen Sie in [!DNL Assets View] **[!UICONTROL Assets]** aus und navigieren Sie zu Ihrem Ordner.
1. Wählen Sie das Video-Asset aus.
1. Klicken Sie auf **[!UICONTROL Eigenschaften]**.
1. Legen Sie im Metadatenbedienfeld **[!UICONTROL Video-SmartCrops erstellen]** auf **Ja** fest, aktualisieren Sie den Asset-Status auf **[!UICONTROL Genehmigt]** und klicken Sie auf **[!UICONTROL Speichern]**.

   ![Genehmigte Video-Assets mit aktiviertem Video-SmartCrop](/help/assets/assets/assets-create-video-smartcrops1.png)

Nach erfolgreicher Aktualisierung der Eigenschaften wird eine Bestätigungsmeldung angezeigt.

## Video-Smart-Zugeschnittene Ausgaben anzeigen {#view-video-smart-crops}

Sobald das smarte Zuschneiden für Videos generiert wurde, schließen Sie den `mode=smartcrop` in die Videobereitstellungsanfrage des `/play`-Endpunkts ein, um sie zu rendern.

* Smartes Zuschneiden von Videos wird während der Wiedergabe dynamisch angewendet, wenn der `mode=smartcrop` verwendet wird.
* Der Dynamic Media-Viewer wählt automatisch den am besten geeigneten Zuschnitt auf der Grundlage des Geräts und des Seitenverhältnisses aus.
* Die Videowiedergabe wird dynamisch angepasst, um das Hauptmotiv im Fokus zu halten.


**Siehe auch**

* [Assets übersetzen](/help/assets/translate-assets.md)
* [Assets-HTTP-API](/help/assets/mac-api-assets.md)
* [Von AEM Assets unterstützte Dateiformate](/help/assets/file-format-support.md)
* [Suchen von Assets](/help/assets/search-assets.md)
* [Connected Assets](/help/assets/use-assets-across-connected-assets-instances.md)
* [Asset-Berichte](/help/assets/asset-reports.md)
* [Metadatenschemata](/help/assets/metadata-schemas.md)
* [Herunterladen von Assets](/help/assets/download-assets-from-aem.md)
* [Verwalten von Metadaten](/help/assets/manage-metadata.md)
* [Verwalten von Dynamic Media-Vorlagen](/help/assets/dynamic-media/manage-dynamic-media-templates.md)
* [Verwalten von Berichten](/help/assets/manage-reports-assets-view.md)
* [Suchfacetten](/help/assets/search-facets.md)
* [Verwalten von Sammlungen](/help/assets/manage-collections.md)
* [Massenimport von Metadaten](/help/assets/metadata-import-export.md)
* [Veröffentlichen von Assets in AEM und Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

