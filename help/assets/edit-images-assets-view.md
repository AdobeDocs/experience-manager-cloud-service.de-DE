---
title: Bearbeiten von Bildern
description: Bearbeiten Sie Bilder mit von [!DNL Adobe Express] unterstützten Optionen und speichern Sie aktualisierte Bilder als Versionen.
role: User
exl-id: cfc4c7b7-da8c-4902-9935-0e3d4388b975
feature: Best Practices, Interactive Images, Smart Crop, Smart Imaging
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '1145'
ht-degree: 100%

---

# Bearbeiten von Bildern in [!DNL Assets view] {#edit-images-in-assets-view}

| [Best Practices für die Suche](/help/assets/search-best-practices.md) | [Best Practices für Metadaten](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [Dynamic Media mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md) | [Entwicklerdokumentation zu AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

Die Benutzeroberfläche der Assets-Ansicht ermöglicht eine einfache Bildbearbeitung auf Basis von Adobe Express, das in die Benutzeroberfläche integriert ist. Diese Bearbeitung umfasst Größenanpassung, Hintergrundentfernung, Zuschneiden und Konvertierung zwischen JPEG- und PNG-Formaten. Darüber hinaus ist eine erweiterte Bearbeitung durch die Adobe Express-Benutzeroberfläche möglich, die in die Benutzeroberfläche der Assets-Ansicht integriert ist. 

Nachdem Sie ein Bild bearbeitet haben, können Sie das neue Bild als neue Version speichern. Mit der Versionierung können Sie bei Bedarf später zum Original-Asset zurückkehren. Um ein Bild zu bearbeiten, [öffnen Sie seine Vorschau](https://experienceleague.adobe.com/de/docs/experience-manager-assets-essentials/help/navigate-view#preview-assets) und klicken Sie auf **Bild bearbeiten**.

>[!NOTE]
>
>Sie können mit [!DNL Adobe Express] Bilder vom Dateityp PNG und JPEG bearbeiten.

<!--The editing actions that are available are Spot healing, Crop and straighten, Resize image, and Adjust image.-->

## Bearbeiten von Bildern {#edit-image}

Öffnen Sie die Benutzeroberfläche der Assets-Ansicht, indem Sie auf den Link für die [Assets-Ansicht](https://experience.adobe.com/#/assets) klicken und das richtige Repository auswählen. Wenden Sie sich an die Admins Ihrer Organisation, um Zugriff zu erhalten.
Weitere Informationen finden Sie unter [Erste Schritte mit der Assets-Ansicht von Adobe Experience Manager](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/assets-view/get-started-assets-view), [Grundlegendes zur Benutzeroberfläche der Assets-Ansicht](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/assets-view/navigate-assets-view#understand-interface-navigation) und [Anwendungsfälle für die Assets-Ansicht](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/assets-view/get-started-assets-view#use-cases).
<!--
>[!CONTEXTUALHELP]
>id="assets_express_integration"
>title="Adobe Express Integration"
>abstract="Easy and intuitive image-editing tools powered by Adobe Express available directly within AEM Assets to increase content reuse and accelerate content velocity."-->

### Bearbeiten von Bildern in der Assets-Ansicht mit Adobe Express {#edit-image-on-assets-view-using-adobe-express}

Nachdem Sie die Assets-Ansicht geöffnet haben, klicken Sie auf **Assets**. Wählen Sie ein Bild aus und klicken Sie in der oberen Leiste auf **Bearbeiten**. Im neuen Bildschirm werden die verfügbaren Bearbeitungsoptionen auf Basis von Adobe Express angezeigt, darunter Größenanpassung, Hintergrundentfernung, Zuschneiden und Konvertierung zwischen JPEG- und PNG-Formaten.

#### Ändern der Bildgröße {#resize-image-using-express}

Ein beliebtes Anwendungsbeispiel ist die Größenanpassung eines Bildes auf eine bestimmte Größe. Die Assets-Ansicht ermöglicht es Ihnen, die Größe von Bildern schnell an die gängigen Bildgrößen anzupassen, indem vorab berechnete, neue Auflösungen für bestimmte Bildgrößen bereitgestellt werden. Gehen Sie wie folgt vor, um mithilfe der Assets-Ansicht die Bildgröße zu ändern:

1. Klicken Sie im linken Bereich auf **Bildgröße ändern**. Es wird ein Dialogfeld mit den Größenanpassungsfunktionen für Bilder auf Grundlage von Adobe Express angezeigt.
1. Wählen Sie in der Dropdown-Liste „Größe ändern“ die entsprechende Social-Media-Plattform aus und wählen Sie in den angezeigten Optionen die Bildgröße aus.
1. Falls erforderlich, skalieren Sie das Bild mithilfe des Feldes **Bildskala**.
1. Klicken Sie auf **[!UICONTROL Anwenden]**, um Ihre Änderungen anzuwenden.
   ![Bildbearbeitung mit Adobe Express](assets/adobe-express-resize-image.png)

   Ihr bearbeitetes Bild kann heruntergeladen werden. Sie können das bearbeitete Asset entweder als neue Version desselben Assets oder als neues Asset speichern.
   ![Speichern des Bildes mit Adobe Express](assets/adobe-express-resize-save.png)

#### Entfernen des Hintergrunds {#remove-background-using-express}

Gehen Sie wie folgt vor, um den Hintergrund aus einem Bild zu entfernen:

1. Klicken Sie im linken Bereich auf **Hintergrund entfernen**. Experience Manager Assets zeigt das Bild ohne Hintergrund an.
1. Klicken Sie auf **[!UICONTROL Anwenden]**, um Ihre Änderungen anzuwenden.
   ![Speichern des Bildes mit Adobe Express](assets/adobe-express-remove-background.png)

   Ihr bearbeitetes Bild kann heruntergeladen werden. Sie können das bearbeitete Asset entweder als neue Version desselben Assets oder als neues Asset speichern.

#### Zuschneiden eines Bildes {#crop-image-using-express}

Mit den eingebetteten Schnellaktionen von [!DNL Adobe Express] ist es einfach, ein Bild in eine perfekte Größe umzuwandeln.

1. Klicken Sie im linken Bereich auf **[!UICONTROL Bild zuschneiden]**.
2. Ziehen Sie die Griffe an den Ecken des Bildes, um den gewünschten Zuschnitt zu erstellen.
3. Klicken Sie auf **[!UICONTROL Übernehmen]**.
   ![Speichern Sie das Bild mit Adobe Express](assets/adobe-express-crop-image.png)
Das zugeschnittene Bild kann heruntergeladen werden. Sie können das bearbeitete Asset entweder als neue Version desselben Assets oder als neues Asset speichern.

#### JPEG in PNG konvertieren {#convert-image-types-using-express}

Mithilfe von Adobe Express können Sie schnell zwischen JPEG- und PNG-Bildformaten konvertieren. Führen Sie die folgenden Schritte aus:

1. Klicken Sie im linken Bereich auf die Option zum Konvertieren von **JPEG in PNG** oder **PNG in JPEG**.
   <!--![Convert to PNG with Adobe Express](/help/using/assets/adobe-express-convert-image.png)-->
1. Klicken Sie auf **[!UICONTROL Herunterladen]**.

#### Einschränkungen {#limitations-adobe-express}

* Unterstützte Bildauflösung: Minimum – 50 Pixel, Maximum – 6000 Pixel pro Dimension.
* Maximal unterstützte Dateigröße: 17 MB.

### Bearbeiten von Bildern im eingebetteten Adobe Express-Editor {#edit-images-in-adobe-express-embedded-editor}

Benutzende mit Express-Berechtigung können den eingebetteten Express-Editor in der Assets-Ansicht verwenden, um Inhalte einfach zu bearbeiten und neue Inhalte mit GenAI von Adobe Firefly zu erstellen. Diese Funktion ermöglicht eine bessere Wiederverwendung von Inhalten und erhöht die Inhaltsgeschwindigkeit. Sie können auch vordefinierte Elemente verwenden, um Ihr Asset beeindruckend aussehen zu lassen, oder schnelle Aktionen durchführen, um Ihr Bild mit nur wenigen Klicks zu bearbeiten.

![Express in Essentials-Benutzeroberfläche](/help/assets/assets/express-in-essentials-ui.jpg)
Gehen Sie wie folgt vor, um Bilder mit dem eingebetteten [!DNL Adobe Express]-Editor zu bearbeiten:

1. Öffnen Sie die AEM-Assets-Ansicht, indem Sie auf den Link für die [AEM-Assets-Ansicht](https://experience.adobe.com/#/assets) klicken und das richtige Repository auswählen.
1. Klicken Sie auf **Assets**, geben Sie einen Ordner an und wählen Sie ein Bild aus.
1. Klicken Sie auf **In Adobe Express öffnen**. Das Bild wird in einer Express-Arbeitsfläche geöffnet.
1. Nehmen Sie die erforderlichen Änderungen am Bild vor.
1. Wenn Sie für Ihr Projekt weitere Seiten hinzufügen müssen, klicken Sie auf **Hinzufügen** und wählen Sie „Assets“ aus. Geben Sie einen Ordner an, wählen Sie ein Bild aus, das in die Arbeitsflächenseite geladen werden soll, und nehmen Sie dann die erforderlichen Änderungen am Bild vor.
1. Um ein oder mehrere Assets zu speichern, klicken Sie auf **Speichern**. Im Dialogfeld „Speichern“ werden die Speicheroptionen angezeigt. Um zwischen den Speicheroptionen zu wählen, folgen Sie einer der folgenden Anweisungen, die Ihren Anforderungen entspricht:
   1. Klicken Sie zum Speichern einer einzelnen Seite auf **Als Version speichern**, um das Bild als neue Version zu exportieren (wobei das Originalformat erhalten bleibt) und im selben Ordner zu speichern.

   1. Klicken Sie zum Speichern einer einzelnen Seite auf **Als neues Asset speichern**, um das Asset in einem anderen Format zu exportieren und als neues Asset in einem beliebigen Ordner zu speichern.

   1. Um eine einzelne Seite von mehreren Seiten zu speichern, klicken Sie auf **Als Version speichern**, um das Asset in seinem ursprünglichen Format und an seinem ursprünglichen Speicherort zu speichern.

   1. Um mehrere Seiten oder eine einzelne Seite von mehreren Seiten zu speichern, klicken Sie auf **Als neues Asset speichern**. Mit dieser Aktion werden ein einzelnes Asset oder mehrere Assets in einen beliebigen Ordner exportiert und als neue Assets in ihrem ursprünglichen oder einem anderen Format gespeichert.

1. Im Dialogfeld „Speichern“:
   1. Geben Sie einen Namen für die Datei in das Feld **Speichern unter** ein.
   1. Wählen Sie einen Zielordner aus.
   1. Optional: Geben Sie Details wie den Projekt- oder Kampagnennamen, Keywords, Kanäle, den Zeitrahmen und die Region an.
1. Klicken Sie auf **Als Version speichern** oder **Als neues Asset speichern**, um das Asset bzw. die Assets zu speichern.

#### Einschränkungen beim Bearbeiten von Bildern im Express-Editor {#limitations-of-editing-images-in-the-express-editor}

* Unterstützter Dateityp: JPEG oder PNG.
* Maximal unterstützte Dateigröße: 40 MB.
* Unterstützte Breite und Höhe: zwischen 50 und 8000 Pixel.
* Laden Sie die Seite neu, um das zuletzt gespeicherte neue Asset im Quellordner anzuzeigen.

### Erstellen neuer Assets in Adobe Express {#create-new-embedded-editor}

In [!DNL Assets view] können Sie mithilfe des in [!DNL Adobe Express] integrierten Editors eine komplett neue Vorlage erstellen. Gehen Sie wie folgt vor, um in [!DNL Adobe Express] ein neues Asset zu erstellen:

1. Navigieren Sie zu **[!UICONTROL Mein Arbeitsbereich]** und klicken Sie im Adobe Express-Banner ganz oben auf **[!UICONTROL Erstellen]**. [!DNL Adobe Express] leere Arbeitsfläche wird in der [!DNL Assets view]-Benutzeroberfläche angezeigt.
1. Erstellen Sie Inhalte mithilfe von [Vorlagen](https://helpx.adobe.com/de/express/using/work-with-templates.html). Navigieren Sie andernfalls zu **[!UICONTROL Ihr Inhalt]**, um vorhandene Inhalte zu ändern.
1. Klicken Sie nach Abschluss der Bearbeitung auf **[!UICONTROL Speichern]**.
1. Geben Sie einen Zielpfad für das erstellte Asset ein und klicken Sie auf **[!UICONTROL Als neues Asset speichern]**.

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

* Geben Sie Produkt-Feedback über die Option [!UICONTROL Feedback] in der Benutzeroberfläche der Assets-Ansicht.

* Geben Sie Feedback zur Dokumentation mithilfe der Option zum [!UICONTROL Bearbeiten der Seite] ![Seite bearbeiten](assets/do-not-localize/edit-page.png) oder zum [!UICONTROL Melden eines Problems] ![GitHub-Ticket erstellen](assets/do-not-localize/github-issue.png) in der rechten Seitenleiste.

* Kontaktieren Sie die [Kundenunterstützung](https://experienceleague.adobe.com/?support-solution=General?lang=de#support)

>[!MORELIKETHIS]
>
>* [Schnellaktionen in Adobe Express](https://helpx.adobe.com/de/express/using/resize-image.html)
>* [Anzeigen des Versionsverlaufs eines Assets](navigate-assets-view.md)
