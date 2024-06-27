---
title: Bearbeiten von Bildern
description: Bearbeiten Sie Bilder mit von  [!DNL Adobe Express]  unterstützten Optionen und speichern Sie aktualisierte Bilder als Versionen.
role: User
exl-id: cfc4c7b7-da8c-4902-9935-0e3d4388b975
feature: Best Practices, Interactive Images, Smart Crop, Smart Imaging
source-git-commit: 9a21c9218e45bb6ce91263c9798e3b1c99f369b4
workflow-type: tm+mt
source-wordcount: '1089'
ht-degree: 35%

---

# Bearbeiten von Bildern in [!DNL Assets view] {#edit-images-in-assets-view}

Die Asset-Ansicht ermöglicht die grundlegende Bildbearbeitung, einschließlich Größenanpassung, Hintergrundentfernt, Beschneiden und Konvertieren zwischen JPEG- und PNG-Formaten. Darüber hinaus ermöglicht sie die erweiterte Bearbeitung durch die Integration mit Adobe Express. Nachdem Sie ein Bild bearbeitet haben, können Sie das neue Bild als neue Version speichern. Mit der Versionierung können Sie bei Bedarf später zum Original-Asset zurückkehren. Um ein Bild zu bearbeiten, [öffnen Sie seine Vorschau](https://experienceleague.adobe.com/en/docs/experience-manager-assets-essentials/help/navigate-view#preview-assets) und klicken Sie auf **Bild bearbeiten**.

>[!NOTE]
>
>Sie können mit [!DNL Adobe Express] Bilder vom Dateityp PNG und JPEG bearbeiten.

<!--The editing actions that are available are Spot healing, Crop and straighten, Resize image, and Adjust image.-->

## Bild bearbeiten {#edit-image}

Landing on Asset View (Landing on Asset View, Asset-Ansicht) über den Link - [Asset-Ansicht](https://experience.adobe.com/#/assets) und das richtige Repository auswählen. Wenden Sie sich an den Administrator Ihres Unternehmens, um Zugriff zu erhalten.
Weitere Referenzinformationen finden Sie unter [Erste Schritte mit Adobe Experience Manager Assets View](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/assets-view/get-started-assets-view), [Die Benutzeroberfläche der Assets-Ansicht](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/assets-view/navigate-assets-view#understand-interface-navigation), und [Anwendungsfälle für die Assets-Ansicht](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/assets-view/get-started-assets-view#use-cases).
<!--
>[!CONTEXTUALHELP]
>id="assets_express_integration"
>title="Adobe Express Integration"
>abstract="Easy and intuitive image-editing tools powered by Adobe Express available directly within AEM Assets to increase content reuse and accelerate content velocity."-->

### Bild in Assets-Ansicht mit Adobe Express bearbeiten {#edit-image-on-assets-view-using-adobe-express}

Klicken Sie nach dem Landing in der Assets-Ansicht auf **Assets**, wählen Sie ein Bild aus und klicken Sie auf **Bearbeiten** aus der oberen Leiste. Im neuen Bildschirm werden die verfügbaren Bearbeitungsoptionen angezeigt, darunter Größenanpassung, Hintergrundentfernt, Beschneiden und Konvertieren zwischen JPEG- und PNG-Formaten.

#### Ändern der Bildgröße {#resize-image-using-express}

Ein beliebtes Anwendungsbeispiel ist die Größenanpassung eines Bildes auf eine bestimmte Größe. Mit der Assets-Ansicht können Sie die Bildgröße schnell an die gängigen Bildgrößen anpassen, indem Sie vorab berechnete neue Auflösungen für bestimmte Bildgrößen bereitstellen. Gehen Sie wie folgt vor, um die Bildgröße mithilfe der Assets-Ansicht zu ändern:

1. Klicks **Bild vergrößern** aus dem linken Bereich.
1. Wählen Sie die entsprechende Social-Media-Plattform aus der Dropdownliste Größe ändern aus und wählen Sie die Bildgröße aus den angezeigten Optionen aus.
1. Falls erforderlich, skalieren Sie das Bild mithilfe des Feldes **Bildskala**.
1. Klicken Sie auf **[!UICONTROL Anwenden]**, um Ihre Änderungen anzuwenden.
   ![Bildbearbeitung mit Adobe Express](assets/adobe-express-resize-image.png)

   Ihr bearbeitetes Bild kann heruntergeladen werden. Sie können das bearbeitete Asset entweder als neue Version desselben Assets oder als neues Asset speichern.
   ![Speichern des Bildes mit Adobe Express](assets/adobe-express-resize-save.png)

#### Entfernen des Hintergrunds {#remove-background-using-express}

Sie können einen Hintergrund aus einem Bild entfernen, indem Sie die unten beschriebenen Schritte ausführen:

1. Klicks **Hintergrund entfernen** aus dem linken Bereich. Experience Manager Assets zeigt das Bild ohne Hintergrund an.
1. Klicken Sie auf **[!UICONTROL Anwenden]**, um Ihre Änderungen anzuwenden.
   ![Speichern des Bildes mit Adobe Express](assets/adobe-express-remove-background.png)

   Ihr bearbeitetes Bild kann heruntergeladen werden. Sie können das bearbeitete Asset entweder als neue Version desselben Assets oder als neues Asset speichern.

#### Zuschneiden eines Bildes {#crop-image-using-express}

Die Umwandlung eines Bildes in eine perfekte Größe ist einfach mit eingebettetem [!DNL Adobe Express] Schnellaktionen.

1. Klicks **[!UICONTROL Bild beschneiden]** aus dem linken Bereich.
2. Ziehen Sie die Griffe an den Ecken des Bildes, um den gewünschten Zuschnitt zu erstellen.
3. Klicken Sie auf **[!UICONTROL Übernehmen]**.
   ![Speichern Sie das Bild mit Adobe Express](assets/adobe-express-crop-image.png)
Das zugeschnittene Bild kann heruntergeladen werden. Sie können das bearbeitete Asset entweder als neue Version desselben Assets oder als neues Asset speichern.

#### Konvertieren zwischen Bilddateitypen {#convert-image-types-using-express}

Mithilfe von Adobe Express können Sie schnell zwischen JPEG- und PNG-Bildformaten konvertieren. Führen Sie die folgenden Schritte aus:

1. Klicks **JPEG in PNG** oder **PNG zu JPEG** aus dem linken Bereich.
   <!--![Convert to PNG with Adobe Express](/help/using/assets/adobe-express-convert-image.png)-->
1. Klicken Sie auf **[!UICONTROL Herunterladen]**.

#### Einschränkungen {#limitations-adobe-express}

* Unterstützte Bildauflösung: Minimum – 50 Pixel, Maximum – 6000 Pixel pro Dimension.

* Maximal unterstützte Dateigröße: 17 MB.

### Bearbeiten von Bildern im eingebetteten Adobe Express-Editor {#edit-images-in-adobe-express-embedded-editor}

Benutzer mit Express-Berechtigung können den eingebetteten Express-Editor in der Assets-Ansicht verwenden, um Inhalte einfach zu bearbeiten und neue Inhalte mit GenAI von Adobe Firefly aus zu erstellen. Dies verbessert die Wiederverwendung von Inhalten und beschleunigt die Geschwindigkeit von Inhalten. Sie können auch vordefinierte Elemente verwenden, um Ihr Asset atemberaubend aussehen zu lassen oder durch schnelle Aktionen Ihr Bild mit nur wenigen Klicks zu bearbeiten.
![in der grundlegenden Benutzeroberfläche ausdrücken](/help/assets/assets/express-in-essentials-ui.jpg)
So bearbeiten Sie Bilder mit [!DNL Adobe Express] Führen Sie die folgenden Schritte aus:

1. Starten Sie über den Link zur AEM Assets-Ansicht - [AEM Asset-Ansicht](https://experience.adobe.com/#/assets) und wählen Sie das richtige Repository aus.
1. Klicks **Assets**, geben Sie einen Ordner ein und wählen Sie ein Bild aus.
1. Klicks **In Adobe Expreß öffnen**. Das Bild wird auf einer Expressarbeitsfläche geöffnet.
1. Nehmen Sie die erforderlichen Änderungen am Bild vor.
1. Wenn Sie für Ihr Projekt weitere Seiten hinzufügen müssen, klicken Sie auf **Hinzufügen**, wählen Sie Assets aus, geben Sie einen Ordner ein, wählen Sie ein Bild aus, das auf die Leinwandseite geladen werden soll, und führen Sie dann die erforderlichen Bildbearbeitungen durch.
1. Klicken Sie zum Speichern der Bilder auf **Speichern**. Das Dialogfeld &quot;Speichern&quot;wird angezeigt.

   >[!NOTE]
   >
   > **1. Für Einzelseiten**
   >
   > **Als Version speichern:** Diese Funktion unterstützt nur das Speichern eines einzelnen Assets. Wählen Sie diese Option aus, um das Bild als neue Version zu exportieren (wobei das Originalformat beibehalten wird) und im selben Ordner zu speichern.
   > **Als neues Asset speichern:** Wählen Sie diese Option, um das Asset in einem anderen Format als das Original zu exportieren und es als neues Asset in einem beliebigen Ordner zu speichern.
   >  
   > **2. Für mehrere Seiten**
   >
   > **Als Version speichern:** Diese Funktion unterstützt nur das Speichern eines einzelnen Assets. Wenn Sie eine einzelne Seite von mehreren Seiten speichern möchten, wählen Sie diese Option, um das Asset in seinem ursprünglichen Format und an seinem Speicherort zu speichern.\
   > **Als neues Asset speichern:** Mit dieser Option exportieren Sie entweder mehrere Assets oder ein einzelnes Asset in einen beliebigen Ordner und speichern sie als neue Assets mit ihrem Dateiformat als Original oder anders.

1. Im Dialogfeld &quot;Speichern&quot;:
   1. Geben Sie einen Namen für die Datei im **Speichern unter** -Feld.
   1. Wählen Sie einen Zielordner aus.
   1. Optional: Geben Sie Details wie Projekt- oder Kampagnenname, Suchbegriffe, Kanäle, Zeitraum und Region an.
1. Klicks **Als Version speichern** oder **Als neues Asset speichern** zum Speichern der Assets.

#### Einschränkungen beim Bearbeiten von Bildern im Express Editor {#limitations-of-editing-images-in-the-express-editor}

* Unterstützter Dateityp: JPEG oder PNG.
* Maximal unterstützte Dateigröße: 40 MB.
* Unterstützte Breite und Höhe: zwischen 50 und 8000 Pixel.
* Laden Sie die Seite neu, um das zuletzt gespeicherte neue Asset im Quellordner anzuzeigen.

### Erstellen neuer Assets in Adobe Express {#create-new-embedded-editor}

In [!DNL Assets view] können Sie mithilfe des in [!DNL Adobe Express] integrierten Editors eine komplett neue Vorlage erstellen. Gehen Sie wie folgt vor, um in [!DNL Adobe Express] ein neues Asset zu erstellen:

1. Navigieren Sie zu **[!UICONTROL Mein Arbeitsbereich]** und klicken Sie im Adobe Express-Banner ganz oben auf **[!UICONTROL Erstellen]**. [!DNL Adobe Express] leere Arbeitsfläche wird in der [!DNL Assets view]-Benutzeroberfläche angezeigt.
1. Erstellen Sie Inhalte mithilfe von [Vorlagen](https://helpx.adobe.com/de/express/using/work-with-templates.html). Navigieren Sie andernfalls zu **[!UICONTROL Ihr Inhalt]**, um vorhandene Inhalte zu ändern.
1. Klicken Sie nach Abschluss der Bearbeitung auf **[!UICONTROL Speichern]**.
1. Geben Sie den Zielpfad für das erstellte Asset an und klicken Sie auf **[!UICONTROL Als neues Asset speichern]**.

#### Einschränkungen {#limitations}

* Sie können nur Bilder mit den Formattypen `JPEG` und `PNG` ändern.
* Das Asset muss kleiner als 40 MB sein.
* Sie können ein Bild im Format `PDF`, `JPEG` oder `PNG` speichern.

<!--
## Edit images using [!DNL Adobe Photoshop Express] {#edit-using-photoshop-express}

<!--
After editing an image, you can save the new image as a new version. Versioning helps you to revert to the original asset later, if needed. To edit an image, [open its preview](navigate-assets-view.md#preview-assets) and click **[!UICONTROL Edit Image]** ![edit icon](assets/do-not-localize/edit-icon.png) from the rail on the right.

![Options to edit an image](assets/edit-image2.png)

*Figure: The options to edit images are powered by [!DNL Adobe Photoshop Express].*
-->
<!--
### Touch up images {#spot-heal-images-using-photoshop-express}

If there are minor spots or small objects on an image, you can edit and remove the spots using the spot healing feature provided by Adobe Photoshop.

The brush samples the retouched area and makes the repaired pixels blend seamlessly into the rest of the image. Use a brush size that is only slightly larger than the spot you want to fix.

![Spot healing edit option](assets/edit-spot-healing.png)

<!-- 
TBD: See if we should give backlinks to PS docs for these concepts.
For more information about how Spot Healing works in Photoshop, see [retouching and repairing photos](https://helpx.adobe.com/photoshop/using/retouching-repairing-images.html). 
-->
<!-- 
### Crop and straighten images {#crop-straighten-images-using-photoshop-express}

Using the crop and straighten option that you can do basic cropping, rotate image, flip it horizontally or vertically, and crop it to dimensions suitable for popular social media websites.

To save your edits, click **[!UICONTROL Crop Image]**. After editing, you can save the new image as a version.

![Option to crop and straighten](assets/edit-crop-straighten.png)

Many default options let you crop your image to the best proportions that fit various social media profiles and posts.

### Resize image {#resize-image-using-photoshop-express}

You can view the common photo sizes in centimeters or inches to know the dimensions. By default, the resizing method retains the aspect ratio. To manually override the aspect ratio, click ![](assets/do-not-localize/lock-closed-icon.png).

Enter the dimensions and click **[!UICONTROL Resize Image]** to resize the image. Before you save the changes as a version, you can either undo all the changes done before saving by clicking [!UICONTROL Undo] or you can change the specific step in the editing process by clicking [!UICONTROL Revert].

![Options when resizing an image](assets/resize-image.png)

### Adjust image {#adjust-image-using-photoshop-express}

[!DNL Assets view] lets you adjust the color, tone, contrast, and more, with just a few clicks. Click **[!UICONTROL Adjust image]** in the edit window. The following options are available in the right sidebar:

* **Popular**: [!UICONTROL High Contrast & Detail], [!UICONTROL Desaturated Contrast], [!UICONTROL Aged Photo], [!UICONTROL B&W Soft], and [!UICONTROL B&W Sepia Tone].
* **Color**: [!UICONTROL Natural], [!UICONTROL Bright], [!UICONTROL High Contrast], [!UICONTROL High Contrast & Detail], [!UICONTROL Vivid], and [!UICONTROL Matte].
* **Creative**: [!UICONTROL Desaturated Contrast], [!UICONTROL Cool Light], [!UICONTROL Turquoise & Red], [!UICONTROL Soft Mist], [!UICONTROL Vintage Instant], [!UICONTROL Warm Contrast], [!UICONTROL Flat & Green], [!UICONTROL Red Lift Matte], [!UICONTROL Warm Shadows], and [!UICONTROL Aged Photo].
* **B&W**: [!UICONTROL B&W Landscape], [!UICONTROL B&W High Contrast], [!UICONTROL B&W Punch], [!UICONTROL B&W Low Contrast], [!UICONTROL B&W Flat], [!UICONTROL B&W Soft], [!UICONTROL B&W Infrared], [!UICONTROL B&W Selenium Tone], [!UICONTROL B&W Sepia Tone], and [!UICONTROL B&W Split Tone].
* **Vignetting**: [!UICONTROL None], [!UICONTROL Light], [!UICONTROL Medium], and [!UICONTROL Heavy].

![Adjust image by editing](assets/adjust-image.png)

<!--
TBD: Insert a video of the available social media options.
-->

### Nächste Schritte {#next-steps}

* Stellen Sie mithilfe der [!UICONTROL Feedback] in der Benutzeroberfläche der Assets-Ansicht verfügbar.

* Geben Sie Feedback zur Dokumentation durch ![Bearbeiten der Seite](assets/do-not-localize/edit-page.png) über die Option [!UICONTROL Diese Seite bearbeiten] oder durch ![Erstellen eines GitHub-Themas](assets/do-not-localize/github-issue.png) über die Option [!UICONTROL Problem protokollieren] in der rechten Seitenleiste

* Kontaktieren Sie die [Kundenunterstützung](https://experienceleague.adobe.com/?support-solution=General&amp;lang=de#support)

>[!MORELIKETHIS]
>
>* [Schnellaktionen in Adobe Express](https://helpx.adobe.com/de/express/using/resize-image.html)
>* [Anzeigen des Versionsverlaufs eines Assets](navigate-assets-view.md)
