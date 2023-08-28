---
title: Bearbeiten von Bildern
description: Bearbeiten Sie Bilder mit von  [!DNL Adobe Photoshop Express]  unterstützten Optionen und speichern Sie aktualisierte Bilder als Versionen.
role: User
exl-id: fc21a6ee-bf23-4dbf-86b0-74695a315b2a
source-git-commit: 30b8c9b8eaee6292323dde4b436c29fe8290c910
workflow-type: tm+mt
source-wordcount: '896'
ht-degree: 50%

---

# Bearbeiten von Bildern in [!DNL Assets view] {#edit-images}

[!DNL Assets view] bietet benutzerfreundliche Bearbeitungsoptionen, die von [!DNL Adobe Express] und [!DNL Adobe Photoshop Express]. Die Bearbeitungsaktionen, die mit [!DNL Adobe Express] sind Bildgröße ändern, Hintergrund entfernen, Bild beschneiden und JPEG in PNG konvertieren.

Nachdem Sie ein Bild bearbeitet haben, können Sie das neue Bild als neue Version speichern. Mit der Versionierung können Sie bei Bedarf später zum Original-Asset zurückkehren. So bearbeiten Sie ein Bild: [Vorschau öffnen](/help/assets/navigate-assets-view.md) und klicken **[!UICONTROL Bild bearbeiten]**.

>[!NOTE]
>
>Sie können Bilder von PNG- und JPEG-Dateitypen mit [!DNL Adobe Express].

<!--The editing actions that are available are Spot healing, Crop and straighten, Resize image, and Adjust image.-->

## Bilder mit Adobe Expreß bearbeiten {#edit-using-express}

>[!CONTEXTUALHELP]
>id="assets_express_integration"
>title="Integration mit Adobe Express"
>abstract="Einfache und intuitive Bildbearbeitungswerkzeuge mit Adobe Expreß, die direkt in AEM Assets verfügbar sind, um die Wiederverwendung von Inhalten zu steigern und die Geschwindigkeit der Inhaltswiedergabe zu beschleunigen."

### Ändern der Bildgröße {#resize-image-using-express}

Ein beliebtes Anwendungsbeispiel ist die Größenanpassung eines Bildes auf eine bestimmte Größe. [!DNL Assets view] ermöglicht es Ihnen, die Größe des Bildes schnell an die gängigen Bildgrößen anzupassen, indem es vorab berechnete neue Auflösungen für bestimmte Bildgrößen bereitstellt. So ändern Sie die Bildgröße mithilfe von [!DNL Assets view]führen Sie die folgenden Schritte aus:

1. Bild auswählen und auf **Bearbeiten**.
2. Klicks **[!DNL Resize Image]** über die im linken Bereich verfügbaren Schnellaktionen.
3. Wählen Sie die entsprechende Social-Media-Plattform aus dem **[!UICONTROL Größe ändern für]** und wählen Sie die Bildgröße aus den angezeigten Optionen aus.
4. Falls erforderlich, skalieren Sie das Bild mithilfe der **[!UICONTROL Bildskala]** -Feld.
5. Klicks **[!DNL Apply]** , um Ihre Änderungen anzuwenden.
   ![Bildbearbeitung mit Adobe Expreß](assets/adobe-express-resize-image.png)

   Ihr bearbeitetes Bild kann heruntergeladen werden. Sie können das bearbeitete Asset entweder als neue Version desselben Assets speichern oder als neues Asset speichern.
   ![Bild mit Adobe Expreß speichern](assets/adobe-express-resize-save.png)

### Hintergrund entfernen {#remove-background-using-express}

Sie können den Hintergrund aus einem Bild in einigen einfachen Schritten entfernen, wie unten beschrieben:

1. Bild auswählen und auf **Bearbeiten**.
2. Klicks **[!DNL Remove Background]** über die im linken Bereich verfügbaren Schnellaktionen. Experience Manager Assets zeigt das Bild ohne Hintergrund an.
3. Klicks **[!DNL Apply]** , um Ihre Änderungen anzuwenden.
   ![Bild mit Adobe Expreß speichern](assets/adobe-express-remove-background.png)

   Ihr bearbeitetes Bild kann heruntergeladen werden. Sie können das bearbeitete Asset entweder als neue Version desselben Assets speichern oder als neues Asset speichern.

### Bild beschneiden {#crop-image-using-express}

Das Umwandeln eines Bildes in eine perfekte Größe ist einfach durch Einbetten [!DNL Adobe Express] Schnellaktionen.

1. Bild auswählen und auf **Bearbeiten**.
2. Klicks **[!DNL Crop Image]** über die im linken Bereich verfügbaren Schnellaktionen.
3. Ziehen Sie die Griffe an die Ecken des Bildes, um den gewünschten Zuschnitt zu erstellen.
4. Klicken Sie auf **[!DNL Apply]**.
   ![Bild mit Adobe Expreß speichern](assets/adobe-express-crop-image.png)
Das zugeschnittene Bild kann heruntergeladen werden. Sie können das bearbeitete Asset entweder als neue Version desselben Assets speichern oder als neues Asset speichern.

### JPEG in PNG konvertieren {#convert-jpeg-to-png-using-express}

Mithilfe von Adobe Expreß können Sie schnell ein JPEG-Bild in ein PNG-Format konvertieren. Führen Sie die folgenden Schritte aus:

1. Bild auswählen und auf **Bearbeiten**.
2. Klicks **[!DNL JPEG to PNG]** über die im linken Bereich verfügbaren Schnellaktionen.
   ![Konvertieren in PNG mit Adobe Expreß](assets/adobe-express-convert-image.png)
3. Klicken Sie auf **[!UICONTROL Download]**.

### Einschränkungen {#limitations-adobe-express}

* Unterstützte Bildauflösung: Mindestens - 50 Pixel, Maximum - 6000 Pixel pro Dimension

* Maximale Dateigröße: 17 MB

## Bilder bearbeiten mit [!DNL Adobe Photoshop Express] {#edit-using-photoshop-express}

<!--
After editing an image, you can save the new image as a new version. Versioning helps you to revert to the original asset later, if needed. To edit an image, [open its preview](//help/navigate-assets-view.md#preview-assets) and click **[!UICONTROL Edit Image]** ![edit icon](assets/do-not-localize/edit-icon.png) from the rail on the right.

![Options to edit an image](assets/edit-image2.png)

*Figure: The options to edit images are powered by [!DNL Adobe Photoshop Express].*
-->

### Bereichsreparatur von Bildern {#spot-heal-images-using-photoshop-express}

Wenn ein Bild kleine Flecken oder Objekte aufweist, können Sie die Flecken mithilfe der von Adobe Photoshop bereitgestellten Funktion zur Bereichsreparatur bearbeiten und entfernen.

Der Pinsel nimmt den retuschierten Bereich auf und lässt die reparierten Pixel nahtlos in den Rest des Bildes einfließen. Verwenden Sie eine Pinselgröße, die nur geringfügig größer ist als die Stelle, die Sie reparieren möchten.

![Bearbeitungsoption Bereichsreparatur](assets/edit-spot-healing.png)

<!-- 
TBD: See if we should give backlinks to PS docs for these concepts.
For more information about how Spot Healing works in Photoshop, see [retouching and repairing photos](https://helpx.adobe.com/photoshop/using/retouching-repairing-images.html). 
-->

### Bilder zuschneiden und gerade ausrichten {#crop-straighten-images-using-photoshop-express}

Mit der Option &quot;Zuschneiden und gerade ausrichten&quot;können Sie einfache Zuschnitte vornehmen, Bilder drehen, horizontal oder vertikal drehen und sie auf für beliebte Social-Media-Websites geeignete Dimensionen zuschneiden.

Um Ihre Änderungen zu speichern, klicken Sie auf **[!UICONTROL Bild zuschneiden]**. Nach der Bearbeitung können Sie das neue Bild als Version speichern.

![Option für das Zuschneiden und Ausrichten](assets/edit-crop-straighten.png)

Mit vielen Standardoptionen können Sie Ihr Bild auf die besten Proportionen zuschneiden, die für verschiedene Social-Media-Profile und -Posts geeignet sind.

### Ändern der Bildgröße {#resize-image-using-photoshop-express}

Sie können die gebräuchlichen Bildgrößen in Zentimetern oder Zoll anzeigen, um die Abmessungen zu erfahren. Standardmäßig behält die Methode zur Größenanpassung das Seitenverhältnis bei. Um das Seitenverhältnis manuell zu überschreiben, klicken Sie auf ![](assets/do-not-localize/lock-closed-icon.png).

Geben Sie die Dimensionen ein und klicken Sie auf **[!UICONTROL Bildgröße ändern]**, um die Bildgröße zu ändern. Bevor Sie die Änderungen als Version speichern, können Sie entweder alle vor dem Speichern vorgenommenen Änderungen rückgängig machen, indem Sie auf [!UICONTROL Rückgängig] klicken, oder Sie können den spezifischen Schritt im Bearbeitungsvorgang ändern, indem Sie auf [!UICONTROL Wiederherstellen] klicken.

![Optionen beim Ändern der Bildgröße](assets/resize-image.png)

### Anpassen von Bildern {#adjust-image-using-photoshop-express}

Mit [!DNL Assets view] können Sie die Farbe, den Ton, den Kontrast und mehr mit nur wenigen Klicks anpassen. Klicken Sie im Bearbeitungsfenster auf **[!UICONTROL Bild anpassen]**. Die folgenden Optionen sind in der rechten Seitenleiste verfügbar:

* **Beliebt**: [!UICONTROL Hoher Kontrast und Detail], [!UICONTROL Entsättigter Kontrast], [!UICONTROL Gealtertes Foto], [!UICONTROL S/W Soft] und [!UICONTROL S/W Sepia-Ton].
* **Farbe**: [!UICONTROL Natur], [!UICONTROL Hell], [!UICONTROL Hoher Kontrast], [!UICONTROL Hoher Kontrast und Detail], [!UICONTROL Lebhaft] und [!UICONTROL Matt].
* **Kreativ**: [!UICONTROL Entsättigter Kontrast], [!UICONTROL Kühles Licht], [!UICONTROL Türkis und Rot], [!UICONTROL Softnebel], [!UICONTROL Vintage Instant], [!UICONTROL Warmer Kontrast], [!UICONTROL Flach und Grün], [!UICONTROL Roter Lift Matt], [!UICONTROL Warme Schatten] und [!UICONTROL Gealtertes Foto].
* **S/W**: [!UICONTROL S/W Querformat], [!UICONTROL S/W Hoher Kontrast], [!UICONTROL S/W Punch], [!UICONTROL S/W Niedriger Kontrast], [!UICONTROL S/W Flach], [!UICONTROL S/W Soft], [!UICONTROL S/W Infrarot], [!UICONTROL S/W Selen-Ton], [!UICONTROL S/W Sepia-Ton] und [!UICONTROL S/W Split-Ton].
* **Vignettierung**: [!UICONTROL Keine], [!UICONTROL Licht], [!UICONTROL Mittel] und [!UICONTROL Stark].

![Bild durch Bearbeitung anpassen](assets/adjust-image.png)

<!--
TBD: Insert a video of the available social media options.
-->

### Nächste Schritte {#next-steps}

* Stellen Sie mithilfe der [!UICONTROL Feedback] Option in der Benutzeroberfläche der Assets-Ansicht verfügbar

* Geben Sie Feedback zur Dokumentation durch ![Bearbeiten der Seite](assets/do-not-localize/edit-page.png) über die Option [!UICONTROL Diese Seite bearbeiten] oder durch ![Erstellen eines GitHub-Themas](assets/do-not-localize/github-issue.png) über die Option [!UICONTROL Problem protokollieren] in der rechten Seitenleiste

* Kontaktieren Sie die [Kundenunterstützung](https://experienceleague.adobe.com/?support-solution=General&amp;lang=de#support)

>[!MORELIKETHIS]
>
>* [Anzeigen des Versionsverlaufs eines Assets](/help/assets/navigate-assets-view.md)
