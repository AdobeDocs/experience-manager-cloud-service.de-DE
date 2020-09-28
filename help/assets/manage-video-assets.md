---
title: 'Verwalten von Video-Assets   '
description: Hochladen, Vorschau, Anmerkungen und Veröffentlichen von Video-Assets [!DNL Adobe Experience Manager].
contentOwner: AG
translation-type: tm+mt
source-git-commit: 8b1cc8af67c6d12d7e222e12ac4ff77e32ec7e0e
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 27%

---


# Verwalten von Video-Assets    {#manage-video-assets}

Das Videoformat ist ein wichtiger Bestandteil digitaler Assets eines Unternehmens. [!DNL Adobe Experience Manager] angebote bieten und verwalten den gesamten Lebenszyklus Ihrer Video-Assets nach deren Erstellung.

Learn how to manage and edit the video assets in [!DNL Adobe Experience Manager Assets]. Videokodierung und -transkodierung, z. B. FFmpeg-Transkodierung, ist mit Verarbeitungselementen und [!DNL Dynamic Media] Integrationsfunktionen möglich. Without [!DNL Dynamic Media] license, [!DNL Experience Manager] provides basic support for videos, such as transcoding using FFmpeg, extraction of preview thumbnails for the supported file formats, and preview in the user interface for formats that are supported for playback in the browser directly.

## Hochladen und Anzeigen der Vorschau von Video-Assets {#upload-and-preview-video-assets}

[!DNL Adobe Experience Manager Assets] generiert Vorschauen für Video-Assets mit der Erweiterung MP4. You can preview the renditions in the [!DNL Assets] user interface.

1. Navigieren Sie im Ordner oder in den Unterordnern für digitale Assets zu dem Speicherort, an dem Sie digitale Assets hinzufügen möchten.
1. To upload the asset, click **[!UICONTROL Create]** from the toolbar and choose **[!UICONTROL Files]**. Alternativ können Sie eine Datei auf die Benutzeroberfläche ziehen. Weitere Informationen finden Sie unter [Hochladen von Assets](manage-digital-assets.md#uploading-assets).
1. To preview a video in the card view, click the **[!UICONTROL Play]** ![play option](assets/do-not-localize/play.png) option on the video asset. Sie können Videos nur in der Kartenansicht anhalten oder wiedergeben. The [!UICONTROL Play] and [!UICONTROL Pause] options are not available in the list view.
1. To preview the video in the asset details page, select **[!UICONTROL Edit]** on the card. Das Video wird im systemeigenen Video-Player des Browsers wiedergegeben. Sie können das Video wiedergeben und anhalten, die Lautstärke regeln und in den Vollbildmodus wechseln.

## Veröffentlichen von Video-Assets {#publish-video-assets}

Nach der Veröffentlichung können Sie die Video-Assets als URL in eine Webseite einbetten oder die Assets direkt einbetten. Weitere Informationen finden Sie unter [Veröffentlichen von Dynamischen Medien-Assets](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

## Transkodieren mit Processing Profil {#transcode-video}

[!DNL Experience Manager] als Cloud Service können Sie eine grundlegende Transkodierung von MP4-Videodateien mithilfe von Verarbeitungsdateien durchführen. Die Funktion ermöglicht Ihnen nicht nur das Hochladen, sondern auch die Vorschau und Skalierung einer MP4-Videodatei.

![Erstellen von Verarbeitungselementen für Profile zum Transkodieren von Videos in Experience Manager](assets/video-processing-profile-for-mp4.png)

*Abbildung: Ein Profil zur Videoverarbeitung[!DNL Experience Manager].*

Wenn Sie nur Breite oder nur Höhe angeben und das andere Feld leer lassen, wird das Seitenverhältnis bei den Darstellungen beibehalten. Derzeit steht nur der h264-Codec für die Transkodierung zur Verfügung.

Um Assets mit einem verarbeitenden Profil zu verarbeiten, fügen Sie einem Ordner ein Profil hinzu. Siehe [Verwenden von Profilen zur Verarbeitung von Assets](/help/assets/asset-microservices-configure-and-use.md#use-profiles).

## Hinzufügen von Anmerkungen zu Video-Assets {#annotate-video-assets}

1. Wählen Sie in der [!DNL Assets] Konsole auf der Asset-Karte die Option **[!UICONTROL Bearbeiten]** , um die Seite mit den Asset-Details anzuzeigen.
1. Um das Video abzuspielen, klicken Sie auf **[!UICONTROL Vorschau]**.
1. To annotate the video, click **[!UICONTROL Annotate]**. Eine Anmerkung wird zur bestimmten Zeit (Frame) im Video hinzugefügt. Beim Hinzufügen von Anmerkungen können Sie auf der Arbeitsfläche zeichnen und einen Kommentar zur Zeichnung aufnehmen. Kommentare werden automatisch gespeichert. Um den Anmerkungsassistenten zu schließen, klicken Sie auf **[!UICONTROL Schließen]**.
1. Suchen Sie nach einem bestimmten Punkt im Video, indem Sie die Zeit in Sekunden in das **Textfeld** eingeben und auf **Springen** klicken. Um beispielsweise die ersten 20 Sekunden des Videos zu überspringen, geben Sie „20“ in das Textfeld ein.
1. Klicken Sie auf eine Anmerkung, um sie in der Zeitleiste anzuzeigen. Um die Anmerkung aus der Zeitleiste zu löschen, klicken Sie auf **[!UICONTROL Löschen]**.

## Best Practices und Einschränkungen {#tips-limitations}

* Ohne Dynamic Media-Lizenz können Sie nur MP4-Dateien mit verarbeitenden Profilen verarbeiten.
* Grundlagen der Transkodierung mit

>[!MORELIKETHIS]
>
>* [Dokumentation](/help/assets/dynamic-media/video.md)zu Videos zu dynamischen Medien
>* [Erfahren Sie mehr über die Verwendung, die Typen und die Konfiguration von Profilen](/help/assets/asset-microservices-configure-and-use.md).

