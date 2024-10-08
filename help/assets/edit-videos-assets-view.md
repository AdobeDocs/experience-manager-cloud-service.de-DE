---
title: Bearbeiten von Videos
description: Bearbeiten Sie Videos mit [!DNL Adobe Express] eingeschalteten Optionen und speichern Sie aktualisierte Videos als Versionen.
role: User
exl-id: 42b25935-e2ff-444f-97c8-b4ed56f3ef9e
feature: Best Practices, Video, Interactive Videos
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '797'
ht-degree: 19%

---

# Bearbeiten von Videos in [!DNL Assets view] {#edit-videos}

| [Best Practices für die Suche](/help/assets/search-best-practices.md) | [Best Practices für Metadaten](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [Dynamic Media mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md) | [AEM Assets-Entwicklerdokumentation](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

Das Erstellen von Varianten von Videoinhalten ist für Assets-Benutzer mit den eingebetteten Schnellaktionen [!DNL Adobe Express] für Videos einfach. Schnellaktionen in [!DNL Assets view] mit [!DNL Adobe Express] bieten benutzerfreundliche Videobearbeitungsoptionen, einschließlich Zuschneiden von Videos, Größenanpassung von Videos, Zuschneiden von Videos und Konvertieren von Videos in GIF.

Um ein Video zu bearbeiten, navigieren Sie zu den Details des Videos und klicken Sie auf [!UICONTROL Video bearbeiten]. Alternativ können Sie das Asset auswählen und auf Details klicken und dann im rechten Bereich auf das Symbol ![Schere](assets/do-not-localize/cut.svg) klicken. Nach dem Bearbeiten eines Videos können Sie das neue Video als neue Version oder als neues Asset speichern.

## Voraussetzungen {#prerequisites}

Berechtigungen für den Zugriff auf [!DNL Adobe Express] und mindestens eine Umgebung in AEM Assets. Bei der Umgebung kann es sich um eines der Repositorys in [!DNL Assets as a Cloud Service] oder [!DNL Assets view] handeln.

## Bearbeiten von Videos mit Adobe Express {#edit-video-using-express}

Die Umwandlung eines Videos in eine perfekte Größe und Ausrichtung ist mit eingebetteten Schnellaktionen mit [!DNL Adobe Express] einfach.

### Zuschneiden von Videos {#crop-video-using-express}

Sie können unerwünschte Teile aus dem Video mit eingebetteten Schnellaktionen mit [!DNL Adobe Express] entfernen. Führen Sie dazu die folgenden Schritte aus:

1. Wählen Sie ein Video aus und klicken Sie auf **[!UICONTROL Bearbeiten]**.
2. Klicken Sie in den im linken Bereich verfügbaren Schnellaktionen auf **[!UICONTROL Video beschneiden]** .
3. Ziehen Sie die Griffe an die Ecken des Videos, um den gewünschten Zuschnitt zu erstellen, oder wählen Sie eine der vorhandenen Bildschirmgrößen aus.
4. Sie können das Video stummschalten oder die Stummschaltung aufheben.
5. Klicken Sie auf **[!UICONTROL Übernehmen]**.
   ![Beschneiden von Videos mit Adobe Express](assets/adobe-express-crop-video.png)

   Das zugeschnittene Video kann heruntergeladen werden. Sie können das bearbeitete Asset entweder als neue Version desselben Assets speichern oder als neues Asset speichern. ![Video mit Adobe Expreß speichern](assets/adobe-express-save-video.png)

### Größe des Videos ändern {#resize-video-using-express}

Die Größe des endgültigen Videoinhalts im DAM muss oft geändert werden, um an bestimmte Kanäle verteilt zu werden. Mit [!DNL Assets view] können Sie die Größe des Videos einfach an die für allgemeine soziale Kanäle erforderlichen Abmessungen anpassen und die Größe auch auf benutzerdefinierte Auflösungen anpassen. Um die Größe des Videos mit [!DNL Assets view] zu ändern, führen Sie die folgenden Schritte aus:

1. Wählen Sie ein Video aus und klicken Sie auf **[!UICONTROL Bearbeiten]**.
2. Klicken Sie in den im linken Bereich verfügbaren Schnellaktionen auf **[!UICONTROL Größe des Videos ändern]** .
3. Wählen Sie die entsprechenden Dimensionen aus der Social-Media-Plattform unter **[!UICONTROL Größe für die Dropdownliste]** ändern aus. Alternativ können Sie die Griffe an die Ecken des Videos ziehen, um den gewünschten Zuschnitt zu erstellen.
4. Falls erforderlich, skalieren Sie das Video mithilfe des Felds **[!UICONTROL Videoskalierung]**.
5. Sie können das Video stummschalten oder die Stummschaltung aufheben.
6. Klicken Sie auf **[!UICONTROL Anwenden]**, um Ihre Änderungen anzuwenden.
   ![Größe des Videos mit Adobe Expreß](assets/adobe-express-resize-video.png)

Ihr in der Größe angepasstes Video kann heruntergeladen werden. Sie können das bearbeitete Asset entweder als neue Version desselben Assets oder als neues Asset speichern.

### Video zuschneiden {#trim-video-using-express}

Wenn Sie einen Clip eines größeren Videos verwenden müssen, können Sie mit der Funktion **[!UICONTROL Video beschneiden]** einen Abschnitt des Videos auswählen und beschneiden. Führen Sie die folgenden Schritte aus:

1. Wählen Sie ein Video aus und klicken Sie auf **[!UICONTROL Bearbeiten]**.
2. Klicken Sie in den im linken Bereich verfügbaren Schnellaktionen auf **[!UICONTROL Video beschneiden]** .
3. Geben Sie die Start- und Endzeit des Videos an, um einen bestimmten Teil davon zu beschneiden. Alternativ können Sie die Griffe an die Ecken des Videos ziehen, um den gewünschten Schnitt zu erstellen.
4. Wählen Sie die entsprechenden Dimensionen aus der Dropdownliste **[!UICONTROL Größe]** aus.
5. Sie können das Video stummschalten oder die Stummschaltung aufheben.
6. Klicken Sie auf **[!UICONTROL Anwenden]**, um Ihre Änderungen anzuwenden.
   ![Größe des Videos mit Adobe Expreß](assets/adobe-express-trim-video.png)

Ihr zugeschnittenes Video kann heruntergeladen werden. Sie können das bearbeitete Asset entweder als neue Version desselben Assets oder als neues Asset speichern.

### Video in GIF konvertieren {#convert-mp4-to-gif-using-express}

Mithilfe von Adobe Express können Sie ein MP4-Video schnell in ein GIF-Format konvertieren. Führen Sie die folgenden Schritte aus:

1. Wählen Sie ein Video aus und klicken Sie auf **[!UICONTROL Bearbeiten]**.
2. Klicken Sie in den im linken Bereich verfügbaren Schnellaktionen auf **[!UICONTROL In GIF konvertieren]** .
3. Wählen Sie die gewünschte Dateigröße basierend auf der gewünschten Qualität aus. Wählen Sie außerdem die Ausrichtung von Querformat, Hochformat oder Quadrat aus.
4. Ziehen Sie die Griffe an die Ecken des Videos, um den gewünschten Zuschnitt zu erstellen.
5. Klicken Sie auf **[!UICONTROL Übernehmen]**.

   ![Video mit Adobe Expreß in GIF konvertieren](assets/adobe-express-convert-video-to-gif.png)

Ihr Video ist als GIF-Format zum Download verfügbar. Sie können das bearbeitete Asset entweder als neue Version desselben Assets oder als neues Asset speichern.

## Einschränkungen {#limitations-video-adobe-express}

* Nur Videos im MP4-Format werden zur Bearbeitung unterstützt.

* Die maximal unterstützte Quelldateigröße beträgt 1 GB.

* Unterstützte Videos sind auf jeder Seite größer als 46 Pixel und kleiner als 3840 Pixel.

* Unterstützte Webbrowser sind Google Chrome, Firefox, Safari und Edge.

* Die Funktion kann nicht in einem Inkognito-Modus eines Webbrowsers geöffnet werden.

### Nächste Schritte {#next-steps}

* Geben Sie Produkt-Feedback über die Option [!UICONTROL Feedback] in der Benutzeroberfläche der Assets-Ansicht.

* Geben Sie Feedback zur Dokumentation über die Option zum [!UICONTROL Bearbeiten der Seite] ![Seite bearbeiten](assets/do-not-localize/edit-page.png) oder zum [!UICONTROL Melden eines Problems] ![GitHub-Ticket erstellen](assets/do-not-localize/github-issue.png) in der rechten Seitenleiste.

* Kontaktieren Sie die [Kundenunterstützung](https://experienceleague.adobe.com/de?support-solution=General#support).

>[!MORELIKETHIS]
>
>* [Bearbeiten von Bildern in der Assets-Ansicht](edit-images-assets-view.md)
>* [Vorschau eines Assets](navigate-assets-view.md)
