---
title: Verwalten von Video-Assets
description: Hochladen, Anzeigen einer Vorschau, Kommentieren und Veröffentlichen von Video-Assets in [!DNL Adobe Experience Manager].
contentOwner: AG
feature: Asset Management,Publishing,Collaboration,Video
role: User
exl-id: 91edce4a-dfa0-4eca-aba7-d41ac907b81e
source-git-commit: 038dbc4b0febfa58f69e05f837760162210f8689
workflow-type: tm+mt
source-wordcount: '656'
ht-degree: 100%

---

# Verwalten von Video-Assets  {#manage-video-assets}

Das Videoformat ist ein wichtiger Bestandteil der digitalen Assets eines Unternehmens. [!DNL Adobe Experience Manager] bietet ausgereifte Produkte und Funktionen, mit denen Sie den gesamten Lebenszyklus von Video-Assets nach deren Erstellung verwalten können.

Lernen Sie, wie Sie die Video-Assets in [!DNL Adobe Experience Manager Assets] verwalten und bearbeiten. Videokodierung und -transkodierung, z. B. FFmpeg-Transkodierung, ist mit Verarbeitungsprofilen und [!DNL Dynamic Media]-Integration möglich. Ohne [!DNL Dynamic Media]-Lizenz bietet [!DNL Experience Manager] grundlegende Unterstützung für Videos, z. B. die Transkodierung mit FFmpeg, die Extraktion von Miniaturbildern für die unterstützten Dateiformate und die Vorschau in der Benutzeroberfläche für Formate, die direkt im Browser wiedergegeben werden.

## Hochladen und Anzeigen der Vorschau von Video-Assets {#upload-and-preview-video-assets}

[!DNL Adobe Experience Manager Assets] generiert eine Vorschau für Video-Assets mit der Erweiterung MP4. Sie können eine Vorschau dieser Ausgabedarstellungen in der Benutzeroberfläche von [!DNL Assets] anzeigen.

1. Navigieren Sie im Ordner „Digitale Assets“ (oder dessen Unterordnern) zum Speicherort, an dem Sie digitale Assets hinzufügen möchten.
1. Um Assets hochzuladen, klicken Sie in der Symbolleiste auf **[!UICONTROL Erstellen]** und wählen dann **[!UICONTROL Dateien]** aus. Alternativ können Sie eine Datei auf die Benutzeroberfläche ziehen. Weitere Informationen finden Sie unter [Hochladen von Assets](manage-digital-assets.md#uploading-assets).
1. Rufen Sie die Vorschau eines Videos in der Kartenansicht auf, indem Sie auf die Schaltfläche **[!UICONTROL Wiedergabe]** ![Schaltfläche Wiedergabe](assets/do-not-localize/play.png) im Video-Asset klicken. Sie können Videos nur in der Kartenansicht anhalten oder wiedergeben. Die Optionen [!UICONTROL Wiedergabe] und [!UICONTROL Pause] sind in der Listenansicht nicht verfügbar.
1. Wählen Sie auf der Karte die Option **[!UICONTROL Bearbeiten]**, um eine Vorschau des Videos auf der Seite mit den Asset-Details anzuzeigen. Das Video wird im systemeigenen Video-Player des Browsers wiedergegeben. Sie können das Video wiedergeben und anhalten, die Lautstärke regeln und in den Vollbildmodus wechseln.

## Veröffentlichen von Video-Assets {#publish-video-assets}

Nach der Veröffentlichung können Sie die Video-Assets als URL in eine Web-Seite einbeziehen oder die Assets direkt einbetten. Details finden Sie unter [Veröffentlichen von [!DNL Dynamic Media] -Assets](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

## Transkodieren mit Verarbeitungsprofil {#transcode-video}

[!DNL Experience Manager] as a [!DNL Cloud Service] erlaubt Ihnen, mithilfe von Verarbeitungsprofilen eine grundlegende Transkodierung von MP4-Videodateien durchführen. Die Funktion ermöglicht Ihnen nicht nur das Hochladen, sondern auch das Anzeigen einer Vorschau und Skalieren einer MP4-Videodatei.

![Erstellen von Verarbeitungsprofilen zum Transkodieren von Videos in [!DNL Experience Manager]](assets/video-processing-profile-for-mp4.png)

*Abbildung: Ein Verarbeitungsprofil zur Videotranskodierung in [!DNL Experience Manager].*

Wenn Sie nur die Breite oder Höhe angeben und das andere Feld leer lassen, wird das Seitenverhältnis bei den Ausgabedarstellungen beibehalten. Der H.264-Video-Codec ist für die Transkodierung verfügbar.

Um Assets mit einem Verarbeitungsprofil zu verarbeiten, fügen Sie einem Ordner ein Profil hinzu. Siehe [Verwenden von Verarbeitungsprofilen zur Verarbeitung von Assets](/help/assets/asset-microservices-configure-and-use.md#use-profiles).

## Hinzufügen von Anmerkungen zu Video-Assets {#annotate-video-assets}

Sie können Anmerkungen zu Video-Assets hinzufügen. Während Videos mit Anmerkungen versehen werden, wird der Player angehalten, damit Sie einem Frame eine Anmerkung hinzufügen können. Details finden Sie unter [Verwalten von Video-Assets](manage-video-assets.md).

>[!NOTE]
>
>Anmerkungen zu Video-Assets im MXF-Videoformat werden noch nicht unterstützt.

1. Wählen Sie in der [!DNL Assets]-Konsole auf der Asset-Karte die Option **[!UICONTROL Bearbeiten]**, um die Seite mit den Asset-Details anzuzeigen.
1. Um das Video wiederzugeben, klicken Sie auf **[!UICONTROL Vorschau]**.
1. Um das Video zu kommentieren, klicken Sie auf **[!UICONTROL Kommentieren]**. Zu dem jeweiligen Zeitpunkt (Frame) im Video wird eine Anmerkung hinzugefügt. Beim Hinzufügen von Anmerkungen können Sie auf der Arbeitsfläche zeichnen und einen Kommentar zur Zeichnung aufnehmen. Kommentare werden automatisch gespeichert. Um den Anmerkungsassistenten zu schließen, klicken Sie auf **[!UICONTROL Schließen]**.
1. Suchen Sie nach einem bestimmten Punkt im Video, indem Sie die Zeit in Sekunden in das **Textfeld** eingeben und auf **Springen** klicken. Um beispielsweise die ersten 20 Sekunden des Videos zu überspringen, geben Sie „20“ in das Textfeld ein.
1. Klicken Sie auf eine Anmerkung, um sie in der Zeitleiste anzuzeigen. Um die Anmerkung aus der Zeitleiste zu löschen, klicken Sie auf **[!UICONTROL Löschen]**.

## Best Practices und Einschränkungen {#tips-limitations}

* Ohne [!DNL Dynamic Media]-Lizenz können Sie MP4-Dateien nur mit Verarbeitungsprofilen verarbeiten.
* Beim Transkodieren von MP4-Dateien mit Verarbeitungsprofilen gelten die folgenden Richtlinien und Einschränkungen:

   * Apple ProRes-Dateien können nur bis zu einer maximalen Auflösung von 1080p transkodiert werden.
   * Wenn die Quelldatei eine Bitrate von mehr als 200 Mbit/s aufweist, können Sie nur bis zu einer maximalen Auflösung von 1080p transkodieren.
   * Wenn die Quelldatei >=60 FPS ist, gelten folgende Maximalgrößen für die Quelldatei:

      * 400 MB für 4k-Transkodierung
      * 800 MB für 1080p-Transkodierung
      * 8 GB für 720p-Transkodierung
   * Die maximale Dateigröße für die Transkodierung mit 4k-Auflösung liegt bei 2,55 GB für eine MP4-Datei mit 4k-Auflösung, einer Bitrate von 12 Mbit/s und 23 FPS.


>[!MORELIKETHIS]
>
>* [Dokumentation zu Dynamic Media-Videos](/help/assets/dynamic-media/video.md).
>* [Erfahren Sie mehr über die Verwendung, Typen und Konfiguration von Verarbeitungsprofilen](/help/assets/asset-microservices-configure-and-use.md).

