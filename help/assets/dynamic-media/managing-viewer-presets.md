---
title: Verwalten von Viewer-Vorgaben
description: 'Erstellen und Verwalten von Viewer-Vorgaben '
translation-type: tm+mt
source-git-commit: 1713cddf713afc24103a841a7dbae923941f6322
workflow-type: tm+mt
source-wordcount: '4263'
ht-degree: 99%

---


# Verwalten von Viewer-Vorgaben{#managing-viewer-presets}

Eine Viewer-Vorgabe ist eine Sammlung aus Einstellungen, die bestimmen, wie Benutzer Rich-Media-Assets auf ihren Computer-Bildschirmen und Mobilgeräten anzeigen. Viewer-Vorgaben können von Administratoren erstellt werden. Einstellungen sind für eine Vielzahl an Viewer-Konfigurationsoptionen verfügbar. Sie können beispielsweise die Viewer-Anzeigegröße oder das Zoom-Verhalten ändern.

<!-- SDK withdrawn from public view. Available internally only at `http://staging.scene7.com/s7sdk/3.8/docs/jsdoc/symbols/_s7sdk.html` 

For instructions on creating and customizing your own HTML5 viewer presets, see the *Adobe Scene7 HTML5 Viewer SDK*. The SDK is available on the IS publish server embedded in the SDK itself. Each library version has its own SDK documentation included.

Path: `<scene7_domain>/s7sdk/<library_version>/docs/jsdocs/index.html`.
For example, 3.5 SDK: [https://s7d1.scene7.com/s7sdk/3.5/docs/jsdoc/index.html](https://s7d1.scene7.com/s7sdk/3.5/docs/jsdoc/index.html)

-->

Siehe auch das [Adobe-Viewer-Referenzhandbuch](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/home.html). 

In diesem Abschnitt wird beschrieben, wie Viewer-Vorgaben erstellt, bearbeitet und verwaltet werden.  Sie können jederzeit bei der Vorschau eines Assets eine Viewer-Vorgabe darauf anwenden.  Siehe [Anwenden von Viewer-Vorgaben](#applying-a-viewer-preset-to-an-asset). 

>[!NOTE]
>
>Denken Sie daran, dass die Bearbeitung von *vordefinierten, standardmäßig vorhandenen Viewer-Vorgaben* als Szenario nicht unterstützt wird.  Wenn Sie versuchen, eine standardmäßig vorhandene Viewer-Vorgabe zu bearbeiten, werden Sie aufgefordert, die Viewer-Vorgabe unter einem neuen Namen zu speichern. 

## Möglichkeit des Zugriffs auf die Tastatur im Viewer   {#keyboard-accessibility-for-viewers}

Alle standardmäßigen Viewer unterstützen den Zugriff auf die Tastatur.

Weitere Informationen finden Sie unter [ Tastaturzugriff und Navigation](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/c-keyboard-accessibility.html).

## Verwalten von Viewer-Vorgaben {#managing-viewer-presets-1}

Sie können Viewer-Vorgaben in AEM hinzufügen, bearbeiten, löschen, veröffentlichen sowie Veröffentlichungen rückgängig machen und eine Vorschau für Viewer-Vorgaben anzeigen, indem Sie **Tools** (Hammersymbol) > **[!UICONTROL Assets > Viewer-Vorgaben]** auswählen.

![6_5_tools-assets-viewerpresets](assets/6_5_tools-assets-viewerpresets.png)

>[!NOTE]
>
>Standardmäßig zeigt das System 15 Viewer-Vorgaben, wenn Sie in einer Detailansicht eines Assets „Viewer“ auswählen.  Sie können diese Grenze erhöhen. Siehe [Erhöhen der Anzahl angezeigter Viewer-Vorgaben](#increasing-the-number-of-viewer-presets-that-display).

### Viewer-Unterstützung für Web-Seiten mit responsivem Design    {#viewer-support-for-responsive-designed-web-pages}

Unterschiedliche Webseiten haben unterschiedliche Anforderungen.  Mitunter möchten Sie vielleicht, dass eine Webseite über einen Link verfügt, der den HTML5-Viewer in einem separaten Browserfenster öffnet.  In anderen Fällen kann es aber auch erforderlich sein, den HTML5-Viewer direkt auf der Hostseite einzubetten. In letzterem Fall kann die Webseite ein statisches Layout aufweisen.  Oder sie kann „responsiv“ sein und auf verschiedenen Geräten oder bei verschieden großen Browserfenstern anders angezeigt werden.  Um all diese Anforderungen zu berücksichtigen, unterstützen sämtliche vordefinierten, standardmäßig vorhandenen HTML5-Viewer, die mit Dynamic Media bereitgestellt werden, sowohl statische als auch responsive Webseiten. 

Weitere Informationen zum Einbetten responsiver Viewer auf Webseiten finden Sie unter [Bibliothek responsiver Bilder](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-serving-api/image-serving-api/responsive-static-image-library/c-about-responsive-static-image-library.html) in der *Scene7 Image Serving-API-Hilfe*.

>[!NOTE]
>
>Sie müssen zunächst alle standardmäßig vorhandenen Viewer veröffentlichen, um sie verwenden zu können. 
>Siehe [Veröffentlichen von Viewer-Vorgaben](#publishing-viewer-presets).

### Systemkompatibilität der Viewer-Vorgaben {#viewer-preset-system-compatibility}

Alle standardmäßig vorhandenen Viewer-Vorgaben, die mit Dynamic Media bereitgestellt werden, sind mit den folgenden Systemen vollständig kompatibel: 

* Desktops 
* Apple iPhones 
* Apple iPads 
* Android-Smartphones 
* Android-Tablets 
* Videos: zusätzliche Unterstützung zur MP4-Wiedergabe für [Blackberry](https://developer.blackberry.com/devzone/develop/supported_media/bb_media_support_at_a_glance.html#kba1328730952678 ) und [Windows Phone](https://msdn.microsoft.com/library/windows/apps/ff462087%28v=vs.105%29.aspx)

### Rich-Media-Typen für Viewer-Vorgaben {#rich-media-types-for-viewer-presets}

Administratoren können bei der Erstellung von Viewer-Vorgaben die folgenden Rich-Media-Typen hinzufügen und anpassen. 

<table>
 <tbody>
  <tr>
   <td><strong>Karussell-Set</strong><br /> </td>
   <td><p>Hotspots, Imagemaps oder beide werden zu einer Serie von mindestens zwei Bildern hinzugefügt. Kunden können einen Bildschwenk nach links oder rechts durchführen und dann auf einen Hotspot auf einem Bild klicken, um zusätzliche Details aufzurufen oder direkt über eine Kategorie-, Start- oder Einstiegsseite einer Website zu kaufen.</p> </td>
  </tr>
    <tr>
   <td><strong>Dimensional</strong><br /> </td>
   <td><p>Zeigt 3D-Szenen an, mit denen Sie Ihre Kamera drehen, schwenken, zoomen oder neu zentrieren können.</p> </td>
  </tr>
  <tr>
   <td><strong>Flyout-Zoom</strong></td>
   <td><p>Zeigt ein zweites Bild des vergrößerten Bereichs neben dem Originalbild an. Dafür gibt es keine Steuerelemente. Benutzer verschieben die Auswahl auf den gewünschten Bereich.</p> <p>Bei der Bestimmung der vollständigen Bandbreitenauslastung für diesen Viewer müssen Sie berücksichtigen, dass sowohl das Hauptbild als auch das Flyout-Bild im Viewer verarbeitet werden. Die Größe des Hauptbildes (Anzeigenbreite und -höhe) und der Zoomfaktor bestimmen die Größe des Flyout-Bildes. Sie müssen ein Gleichgewicht zwischen diesen beiden Werten schaffen, um zu verhindern, dass die Flyout-Datei zu groß wird: Wenn das Hauptbild sehr groß ist, reduzieren Sie den Zoomfaktor-Wert. (Die Flyout-Breite und Flyout-Höhe bestimmen die Größe des Flyout-Fensters, aber nicht die Größe des Flyout-Bildes, das im Viewer verarbeitet wird.)</p> <p>Beispiel: Wenn das Hauptbild eine Größe von 350 x 350 Pixel und einen Zoomfaktor von 3 aufweist, hat das resultierende Flyout-Bild eine Größe von 1050 x 1050 Pixel. Wenn das Hauptbild eine Größe von 300 x 300 Pixel und einen Zoomfaktor von 4 aufweist, hat das Flyout-Bild eine Größe von 1200 x 1200 Pixel. Abhängig von der JPEG-Qualitätseinstellung (empfohlene Einstellungen liegen zwischen 80 und 90) können Sie die Dateigröße erheblich reduzieren. Als Zoomfaktor wird ein Wert zwischen 2,5 und 4 empfohlen, je nach Größe des Hauptbildes.</p> </td>
  </tr>
  <tr>
   <td><strong>Inline-Zoom</strong></td>
   <td>Zeigt ein Bild des hereingezoomten Bereichs im ursprünglichen Viewer an. Es stehen keinerlei Steuerelemente zur Verfügung.  Benutzer verschieben vielmehr die Auswahl über den Bereich, der angezeigt werden soll. </td>
  </tr>
  <tr>
   <td><strong>Bild-Set</strong></td>
   <td>Im Bildset-Viewer können Benutzer unterschiedliche Ansichten oder Farbvariationen eines Elements sehen, indem sie auf eine Miniaturansicht klicken. Dieser Viewer bietet auch Zoomtools, mit denen Bilder genauer untersucht werden können.</td>
  </tr>
  <tr>
   <td><strong>Interaktives Bild</strong></td>
   <td>Hotspots werden zu Teilmengen eines Bildes hinzugefügt, auf die ein Kunde anschließend klicken kann, um zusätzliche Informationen zu erhalten oder den Kauf direkt über die Kategorie einer Website, über die Startseite oder Landingpages vorzunehmen.</td>
  </tr>
  <tr>
   <td><strong>Interaktives Video</strong></td>
   <td>Miniaturansichten werden Timeline-Segmenten in einem Video hinzugefügt, auf die ein Kunde anschließend klicken kann, um zusätzliche Informationen zu erhalten oder den Kauf direkt über die Kategorie einer Website, über die Startseite oder Landingpages vorzunehmen.</td>
  </tr>
  <tr>
   <td><strong>Gemischte Medien</strong></td>
   <td>Zeigt unterschiedliche Medientypen in einem Viewer an. Dort können Sie Rotationssets, Bildsets, Bilder und Videos aufnehmen.</td>
  </tr>
  <tr>
   <td><strong>Panoramabild</strong></td>
   <td><p>Die Viewer für Panoramabilder und PanoramicVR geben Kugelpanoramen wieder, um Benutzern ein 360°-Betrachtererlebnis eines Zimmers, einer Immobilie, eines Orts oder einer Landschaft zu bieten.</p> <p>Damit ein hochgeladenes Bild als Kugelpanorama gilt, muss mindestens eine der beiden folgenden Eigenschaften zutreffen:</p>
    <ul>
     <li>Ein Seitenverhältnis von 2:1.</li>
     <li>Mit den Keywords <code>equirectangular</code> oder <code>spherical</code> und <code>panorama</code> oder <code>spherical </code> und <code>panoramic</code> als Tags versehen. Weitere Informationen finden Sie unter <a href="/help/sites-cloud/authoring/features/tags.md">Verwenden von Tags</a>.</li>
    </ul> <p>Die Kriterien für das Seitenverhältnis sowie die Keywords gelten für Panorama-Assets für die Asset-Detailseite und die WCM-Komponente „Panoramamedien“.</p></td>
  </tr>
    <tr>
   <td><strong>Video zu Smart-Zuschnitt</strong><br /> </td>
   <td><p>Verwenden Sie diesen Viewer, um den Brennpunkt eines Videos automatisch zu erkennen und zuzuschneiden.</p> </td>
  </tr>
  <tr>
   <td><strong>Rotations-Set</strong></td>
   <td>Stellt mehrere Ansichten eines Bildes bereit, sodass Benutzer den Gegenstand drehen können, um ihn von allen Seiten zu betrachten.</td>
  </tr>
  <tr>
   <td><strong>360-Grad-Video</strong></td>
   <td><p>Verwenden Sie den 360/VR-Video-Viewer, um ein Panoramavideo für eine interaktive Anzeige eines Raums, einer Eigenschaft, eines Standorts, einer Landschaft oder eines medizinischen Verfahrens zu rendern.</p> <p>Während der Wiedergabe auf einer flachen Anzeige kann der Benutzer den Anzeigewinkel bestimmen; bei der Wiedergabe auf Mobilgeräten werden in der Regel die integrierten gyroskopischen Funktionen verwendet.</p> <p>Der Viewer bietet native Unterstützung für die Bereitstellung von 360-Grad-Videoassets. Standardmäßig ist keine weitere Konfiguration für die Anzeige oder die Wiedergabe erforderlich. 360-Grad-Videos werden mit Standardvideoerweiterungen wie .mp4, .mkv und .mov bereitgestellt. Der am häufigsten verwendete Codec ist H.264.</p> </td>
  </tr>
  <tr>
   <td><strong>Video</strong></td>
   <td><p>Wiedergeben von Videos unter Verwendung des progressiven oder adaptiven Bitraten-Streamings. Beim Streaming mit adaptiver Bitrate wird eine automatische Geräte- und Brandbreitenerkennung durchgeführt, um Videos mit der richtigen Qualität und im richtigen Format bereitzustellen.</p> </td>
  </tr>
  <tr>
   <td><strong>Vertikaler Zoom</strong></td>
   <td><p>Mit dem Viewer für vertikalen Zoom können Sie das Betrachtererlebnis für Produktbilder optimieren, um Ihren Benutzern die bestmögliche Darstellung eines Produktes zu bieten. Die vertikale Positionierung von Farbfeldern:</p>
    <ul>
     <li>Stellt sicher, dass sich Farbfelder „oberhalb der Falte“ befinden.<br/> Bei einer horizontalen Platzierung von Farbfeldern sind die Farbfelder je nach Bildschirmgröße nicht sichtbar, bis der Benutzer auf der Seite nach unten scrollt. Wenn die Farbfelder vertikal im Viewer platziert werden, sind sie unabhängig von der Bildschirmgröße des Benutzers sichtbar.</li>
     <li>Maximiert die Größe des Hauptbildes.<br /> Bei horizontalen Farbfeldern ist es erforderlich, Platz auf der Seite zu lassen, um sicherzustellen, dass sie sichtbar sind. Diese Positionierung verringerte die mögliche Größe des Hauptbildes. Bei einer vertikalen Farbfeld-Platzierung ist es jedoch nicht notwendig, diesen Platz freizulassen. Somit können Sie die Größe des Hauptbildes maximieren.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Zoom</strong></td>
   <td>Damit können Benutzer den Bereich durch Klicken ein- und auszoomen. Benutzer können auf Steuerelemente klicken, um ein- und auszuzoomen und das Bild auf seine Standardgröße zurückzusetzen.</td>
  </tr>
 </tbody>
</table>

### Liste standardmäßig vorhandener Viewer-Vorgaben {#list-of-out-of-the-box-viewer-presets}

In der folgenden Tabelle werden alle vordefinierten, standardmäßig vorhandenen Viewer-Vorgaben, die mit Dynamic Media bereitgestellt werden, aufgeführt. 

Siehe auch <!-- KEEP REFERENCE [Viewers Reference Library Examples](https://marketing.adobe.com/resources/help/en_US/s7/vlist/vlist.html) and --> [Live-Demos](https://landing.adobe.com/en/na/dynamic-media/ctir-2755/live-demos.html).

Informationen zu unterstützten Webbrowsern und Betriebssystemversionen für Viewer finden Sie in den Viewer-Versionshinweisen. 

Weitere Informationen finden Sie in den Viewer-Versionshinweisen im Inhaltsverzeichnis des [Viewer-Referenzhandbuchs](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/home.html).

>[!NOTE]
>
>Alle standardmäßig vorhandenen Viewer-Vorgaben in Dynamic Media sind bereits aktiviert. Sie müssen sie allerdings noch veröffentlichen. 
>Siehe [Veröffentlichen von Viewer-Vorgaben](#publishing-viewer-presets).
>
>Alle neuen Viewer-Vorgaben, die Sie erstellen und hinzufügen, müssen aktiviert *und* veröffentlicht werden.
> Siehe [Aktivieren oder Deaktivieren von Viewer-Vorgaben](#activating-or-deactivating-viewer-presets) und [Veröffentlichen von Viewer-Vorgaben](#publishing-viewer-presets). 

<table>
 <tbody>
  <tr>
   <td><strong>Viewer-Vorgabentitel </strong></td>
   <td><strong>Typ</strong></td>
   <td><strong>CSS-Dateiname</strong><br /> </td>
  </tr>
  <tr>
   <td>Carousel_Dotted_dark</td>
   <td>Carousel_Set</td>
   <td><code>html5_carouselviewer_dotted_dark.css</code></td>
  </tr>
  <tr>
   <td>Carousel_Dotted_light</td>
   <td>Carousel_Set</td>
   <td><code>html5_carouselviewer_dotted_light.css</code></td>
  </tr>
  <tr>
   <td>Carousel_Numeric_dark</td>
   <td>Carousel_Set</td>
   <td><code>html5_carouselviewer_numeric_dark.css</code></td>
  </tr>
  <tr>
   <td>Carousel_Numeric_light</td>
   <td>Carousel_Set</td>
   <td><code>html5_carouselviewer_numeric_light.css</code></td>
  </tr>
  <tr>
   <td>Flyout</td>
   <td>Flyout_Zoom</td>
   <td><code>html5_flyoutviewer.css</code></td>
  </tr>
  <tr>
   <td>ImageSet_dark</td>
   <td>Bild-Set</td>
   <td><code>html5_zoomviewer_dark.css</code></td>
  </tr>
  <tr>
   <td>ImageSet_light</td>
   <td>Bild-Set</td>
   <td><code>html5_zoomviewer_light.css</code></td>
  </tr>
  <tr>
   <td>InlineMixedMedia_dark</td>
   <td>Mixed_Media</td>
   <td><code>html5_inlinemixedmediaviewer_dark.css</code></td>
  </tr>
  <tr>
   <td>InlineMixedMedia_light</td>
   <td>Mixed_Media</td>
   <td><code>html5_inlinemixedmediaviewer_light.css</code></td>
  </tr>
  <tr>
   <td>InlineZoom</td>
   <td>Flyout_Zoom</td>
   <td><code>html5_inlinezoomviewer.css</code></td>
  </tr>
  <tr>
   <td>MixedMedia_dark</td>
   <td>Mixed_Media</td>
   <td><code>html5_mixedmediaviewer_dark.css</code></td>
  </tr>
  <tr>
   <td>MixedMedia_light</td>
   <td>Mixed_Media</td>
   <td><code>html5_mixedmediaviewer_light.css</code></td>
  </tr>
  <tr>
   <td>PanoramicImage</td>
   <td>Panoramic_Image</td>
   <td><code>html5_panoramicimage.css</code></td>
  </tr>
  <tr>
   <td>PanoramicImageVR</td>
   <td>Panoramic_Image</td>
   <td><code>html5_panoramicimage.css</code></td>
  </tr>
  <tr>
   <td>Shoppable_Banner</td>
   <td>Interactive_Image</td>
   <td><code>html5_interactiveimage.css</code></td>
  </tr>
  <tr>
   <td>Shoppable_Video_dark</td>
   <td>Interactive_Video</td>
   <td><code>html5_interactivevideoviewer_dark.css</code></td>
  </tr>
  <tr>
   <td>Shoppable_Video_light</td>
   <td>Interactive_Video</td>
   <td><code>html5_interactivevideovewer_light.css</code></td>
  </tr>
  <tr>
   <td>SpinSet_dark</td>
   <td>Spin_Set</td>
   <td><code>html5_spinviewer_dark.css</code></td>
  </tr>
  <tr>
   <td>SpinSet_light</td>
   <td>Spin_Set</td>
   <td><code>html5_spinviewer_light.css</code></td>
  </tr>
  <tr>
   <td><p>Video</p> <p>(mit Unterstützung für Untertitel)</p> </td>
   <td>Video</td>
   <td><code>html5_videoviewer.css</code></td>
  </tr>
  <tr>
   <td><p>Video360_social</p> <p>(Enthält grundlegende Steuerelemente für die Videowiedergabe, das Video-Rendering erfolgt im Stereomodus, und die manuelle Blickwinkelsteuerung ist deaktiviert. Jedoch sind die gyroskopischen Funktionen aktiviert und die Social-Media-Eigenschaften deaktiviert)</p> </td>
   <td>Video_360</td>
   <td><code>html5_video360viewersocial.css</code></td>
  </tr>
  <tr>
   <td><p>Video360VR</p> <p>(Für Endbenutzer, die Virtual-Reality-Brillen verwenden. Enthält grundlegende Steuerelemente für die Videowiedergabe und Social-Media-Eigenschaften)</p> </td>
   <td>Video_360</td>
   <td><code>html5_video360viewer.css</code></td>
  </tr>
  <tr>
   <td><p>Video_social</p> <p>(mit Unterstützung für Untertitel und soziale Medien)</p> </td>
   <td>Video</td>
   <td><code>html5_videoviewersocial.css</code></td>
  </tr>
  <tr>
   <td>Zoom_dark<br /> </td>
   <td>Zoom<br /> </td>
   <td><code>html5_basiczoomviewer_dark.css</code></td>
  </tr>
  <tr>
   <td>Zoom_light<br /> </td>
   <td>Zoom</td>
   <td><code>html5_basiczoomviewer_light.css</code></td>
  </tr>
  <tr>
   <td>ZoomVertical_dark<br /> </td>
   <td>Vertical_Zoom</td>
   <td><code>html5_zoomverticalviewer_dark.css</code></td>
  </tr>
  <tr>
   <td>ZoomVertical_light</td>
   <td>Vertical_Zoom</td>
   <td><code>html5_zoomverticalviewer_light.css</code></td>
  </tr>
 </tbody>
</table>

### Matrix unterstützter Mobile Viewer-Gesten {#supported-mobile-viewers-gestures-matrix}

In der folgenden Tabelle werden die Mobile Viewer-Gesten aufgeführt, die auf iOS-, Android 2.x- und Android 3.x-Geräten unterstützt werden. 

<table>
 <tbody>
  <tr>
   <td><strong>Geste</strong></td>
   <td><strong>Flyout-Zoom</strong></td>
   <td><strong>Zoom</strong></td>
   <td><strong>Drehung</strong></td>
  </tr>
  <tr>
   <td><p><strong>Ziehen</strong></p> </td>
   <td><p>Schwenkt</p> </td>
   <td><p>Schwenkt</p> </td>
   <td><p>Schwenkt</p> </td>
  </tr>
  <tr>
   <td><p><strong>Tippen</strong></p> </td>
   <td><p>Blendet Flyout-Fenster ein</p> </td>
   <td><p>Blendet die Benutzeroberfläche ein oder aus</p> </td>
   <td><p>Blendet die Benutzeroberfläche ein oder aus</p> </td>
  </tr>
  <tr>
   <td><p><strong>Doppeltippen</strong></p> </td>
   <td><p>Trifft nicht zu</p> </td>
   <td><p>Zoomt ein oder setzt zurück</p> </td>
   <td><p>Zoomt ein oder setzt zurück</p> </td>
  </tr>
  <tr>
   <td><p><strong>Aufziehen</strong></p> </td>
   <td><p>Trifft nicht zu</p> </td>
   <td><p>Zoomt ein (nur iOS und Android 3x)</p> </td>
   <td><p>Zoomt ein (nur iOS und Android 3x)</p> </td>
  </tr>
  <tr>
   <td><p><strong>Zuziehen</strong></p> </td>
   <td><p>Trifft nicht zu</p> </td>
   <td><p>Zoomt aus (nur iOS und Android 3x)</p> </td>
   <td><p>Zoomt aus (nur iOS und Android 3x)</p> </td>
  </tr>
  <tr>
   <td><p><strong>Streichen</strong></p> </td>
   <td><p>Scrollt Farbfeldleiste</p> </td>
   <td><p>Scrollt Bilder</p> </td>
   <td><p>Dreht</p> </td>
  </tr>
  <tr>
   <td><p><strong>Schnippen</strong></p> </td>
   <td><p>Scrollt Farbfeldleiste</p> </td>
   <td><p>Scrollt Bilder</p> </td>
   <td><p>Dreht</p> </td>
  </tr>
 </tbody>
</table>

## Erhöhen der Anzahl angezeigter Viewer-Vorgaben {#increasing-the-number-of-viewer-presets-that-display}

AEM zeigt verschiedene Viewer-Vorgaben an, wenn Sie ein Asset unter **[!UICONTROL Detailansicht > Viewer]** anzeigen. Sie können die Anzahl der angezeigten Viewer erhöhen oder verringern.

**So erhöhen Sie die Anzahl angezeigter Viewer-Vorgaben**

1. Navigieren Sie zu CRXDE Lite ([https://localhost:4502/crx/de](https://localhost:4502/crx/de)).
1. Navigieren Sie zum Knoten mit der Viewer-Vorgabenliste unter `/libs/dam/gui/coral/content/commons/sidepanels/viewerpresets/viewerpresetslist`

   ![chlimage_1-221](/help/assets/dynamic-media/assets/chlimage_1-221.png)

1. Ändern Sie für die Eigenschaft **[!UICONTROL limit]** den **[!UICONTROL Wert]**, für den standardmäßig 15 festgelegt ist, in einen höheren Wert.
1. Navigieren Sie zur Datenquelle der Viewer-Vorgabe unter `/libs/dam/gui/coral/content/commons/sidepanels/viewerpresets/viewerpresetslist/datasource`

   ![chlimage_1-222](/help/assets/dynamic-media/assets/chlimage_1-222.png)

1. Ändern Sie in der Eigenschaft „limit“ den Wert auf die gewünschte Zahl, z. B. `{empty requestPathInfo.selectors[1] ? "20" : requestPathInfo.selectors[1]}`.
1. Tippen Sie auf **[!UICONTROL Alle speichern]**.

## Erstellen einer Viewer-Vorgabe {#creating-a-new-viewer-preset}

Durch Erstellen von Viewer-Vorgaben können Sie verschiedene Einstellungen anwenden, um Assets anzuzeigen und mit diesen zu interagieren.  Sie müssen jedoch keine neuen Viewer-Vorgaben erstellen.  Wenn Sie dies bevorzugen, können Sie auch die bereits standardmäßig in AEM Assets verfügbaren Viewer-Vorgaben verwenden. 

Wenn Sie eine neue Viewer-Vorgabe erstellen möchten, wird nach deren Speicherung der Viewer-Status auf der Seite „Viewer-Vorgaben“ automatisch aktiviert (auf **[!UICONTROL Ein]** gesetzt). Dieser Status bedeutet, dass die Vorgabe in der Komponente für dynamische Medien und in der Komponente für interaktive Medien sowie bei jeder Bild- oder Videovorschau sichtbar ist.

Bestimmte Viewer-Vorgaben weisen exklusive Einstellungen auf, die die Nutzung und das Gesamtverhalten des Viewers beeinflussen können. Je nach der von Ihnen erstellten Viewer-Vorgabe sollten Sie diese besonderen Hinweise berücksichtigen.

Siehe [Besondere Hinweise zum Erstellen von Vorgaben für interaktive Viewer](#special-considerations-for-creating-an-interactive-viewer-preset).

Siehe [Besondere Hinweise zum Erstellen von Viewer-Vorgaben für Karussellbanner](#special-considerations-for-creating-a-carousel-banner-viewer-preset). 

**So erstellen Sie eine Viewer-Vorgabe**

1. Tippen Sie in der linken oberen Ecke von AEM auf das AEM-Logo und tippen Sie dann in der linken Leiste auf **Tools** (Hammersymbol) > **Assets > Viewer-Vorgaben**.

   ![6_5_viewerpresets](assets/6_5_viewerpresets.png)

1. Tippen Sie auf der Seite „Viewer-Vorgaben“ in der Symbolleiste auf **[!UICONTROL Erstellen]**. 
1. Geben Sie im Dialogfeld **Neue Viewer-Vorgabe** in das Feld **[!UICONTROL Vorgabename]** den Namen der neuen Vorgabe ein. Achten Sie darauf, einen geeigneten Namen festzulegen, da dieser nach dem Tippen auf **[!UICONTROL Erstellen]** nicht mehr geändert werden kann.

   Wenn Sie die Vorgabe an späterer Stelle in diesen Schritten speichern, wird der Name auf der Seite „Viewer-Vorgaben“ unter der Spaltenüberschrift „Vorgabentitel“ angezeigt. 

1. Wählen Sie aus dem Dropdown-Menü „Rich-Media-Typ“ den Typ der zu erstellenden Viewer-Vorgabe aus und tippen Sie dann oben rechts auf der Seite auf **[!UICONTROL Erstellen]**.

   Siehe [Rich-Media-Typen für Viewer-Vorgaben](#rich-media-types-for-viewer-presets).

1. Tippen Sie auf der Seite „Viewer-Vorgabe bearbeiten“ auf die Registerkarte **[!UICONTROL Erscheinungsbild]**.
1. Führen Sie einen der folgenden Schritte aus:

   * Wählen Sie aus dem Pulldown-Menü **[!UICONTROL Ausgewählter Typ]** eine Komponente aus, deren visuelles Design angepasst werden soll. Sie können auch auf ein beliebiges visuelles Element im Viewer tippen oder klicken, um es zum Konfigurieren auszuwählen. 

        Der Visual Editor zeigt Ihnen, wie sich eine bestimmte Eigenschaft auf einen Stil auswirkt. Legen Sie eine beliebige Eigenschaft fest bzw. passen Sie diese an, um sofort anhand des Beispiels auf der linken Seite des Editors zu sehen, wie sich dies auf den Viewer auswirkt.

      Die CSS-Stileigenschaften für alle Viewer-Vorgabetypen werden im Abschnitt „Anpassen des *`<viewer name>`*-Viewers“ in den Hilfethemen im [Viewer-Referenzhandbuch](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/home.html) beschrieben. Wenn Sie z. B. eine Viewer-Vorgabe vom Typ `Mixed_Media` erstellen, finden Sie im Thema zum [Anpassen von Viewern für gemischte Medien](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/mixed-media/customing-mixed-media/c-html5-mixedmedia-viewer-customizingviewer.html) eine Aufstellung und Beschreibung jeder Eigenschaft.

   * Wenn Stileinstellungen in einer separaten CSS-Datei definiert sind, können Sie die CSS-Datei in AEM Assets hochladen. Tippen Sie auf **[!UICONTROL CSS importieren]** unter dem Pulldown-Menü **[!UICONTROL Ausgewählter Typ]** (ggf. müssen Sie hierzu einen Bildlauf im Visual Editor durchführen), um nach der hochgeladenen CSS-Datei zu suchen und diese mit der Viewer-Vorgabe zu verknüpfen.

        Beim Importieren einer CSS-Datei überprüft der Visual Editor, ob CSS die korrekten Viewer-Markierungen verwendet. Wenn Sie etwa einen Zoom-Viewer erstellen, müssen alle CSS-Regeln, die Sie importieren, mit dem zugehörigen Viewer-Klassennamen `.s7mixedmediaviewer` (definiert in einem übergeordneten Viewer-Element) festgelegt werden.

      Sie können beliebige, selbst definierte CSS-Dateien importieren, solange diese die CSS-Markierungen für den jeweiligen Viewer ordnungsgemäß definieren. (CSS-Markierungen werden im Hilfethema *Anpassen des &lt;Viewer-Name>-Viewers* im [Viewer-Referenzhandbuch](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/home.html) erläutert. Wenn Sie beispielsweise mehr über CSS-Markierungen für den Zoom-Viewer erfahren möchten, lesen Sie den Abschnitt [Anpassen des Zoom-Viewers](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/zoom/customizing-zoom/c-html5-20-zoom-viewer-customizingviewer.html).) Es ist jedoch möglich, dass der Visual Editor nicht alle CSS-Werte versteht. In diesem Fall versucht der Visual Editor, die Fehler zu überschreiben, damit CSS nach wie vor verwendet werden kann.
   >[!NOTE]
   >
   >Wenn Sie CSS lieber direkt im Rohformat bearbeiten möchten, tippen Sie im Pulldownmenü „Ausgewählter Typ“ auf **[!UICONTROL CSS ein-/ausblenden]** (Sie müssen ggf. im Visual Editor nach oben blättern, um diese Option anzuzeigen).
   >Wenn Sie eine Eigenschaft direkt in CSS ändern, können Sie wie im Visual Editor sofort sehen, wie sich dies auf das Viewer-Beispiel auswirkt. Außerdem wird zur gleichen Zeit genau diese Eigenschaft automatisch im Visual Editor aktualisiert.  Daher können Sie entweder den CSS-Editor, den Visual Editor oder beide abwechselnd verwenden. 

   >[!NOTE]
   >
   >Für Schaltflächengrafiken wählen Sie das 2x-Bild aus und laden Sie Grafiken mit hoher Auflösung hoch.  Beim Arbeiten mit interaktiven Bildern und Bannern mit Einkaufsfunktion können Sie auch aus verschiedenen standardmäßig vorhandenen Hotspot-Schaltflächen wählen. 

1. (Optional) Tippen Sie in der Nähe des oberen Bereichs der Seite „Viewer-Vorgabe bearbeiten“ auf **[!UICONTROL Desktop]**, **[!UICONTROL Tablet]** oder **[!UICONTROL Telefon]**, um visuelle Stile für verschiedene Geräte- und Bildschirmtypen individuell zu definieren. 
1. Tippen Sie auf der Seite „Viewer-Vorgabe bearbeiten“ auf die Registerkarte **[!UICONTROL Verhalten]**. Sie können auch auf ein beliebiges visuelles Element im Viewer tippen oder klicken, um es zum Konfigurieren auszuwählen. 
1. Wählen Sie im Pulldownmenü **[!UICONTROL Ausgewählter Typ]** eine Komponente aus, deren Verhalten Sie ändern möchten.

   Viele Komponenten im Visual Editor sind mit einer detaillierten Beschreibung verknüpft.  Diese Beschreibungen werden in blauen Feldern angezeigt, wenn Sie eine Komponente zum Anzeigen der mit ihr verknüpften Parameter einblenden. 

   Einige Viewer-Typen verfügen über Komponenten, mit denen Sie Befehle zum Image Serving in einem **[!UICONTROL IS-Befehl]**-Textfeld angeben können. Eine Liste der verfügbaren Befehle finden Sie in der [Image Serving API-Referenz](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-serving-api/image-serving-api/c-is-home.html).

   >[!NOTE]
   >
   >**Bei Nutzung eines Touchgeräts, etwa eines Telefons oder Tablets:** 
   >
   >
   >Nachdem Sie einen Wert in das Textfeld eingegeben haben, tippen Sie auf eine andere Stelle in der Benutzeroberfläche, um die Änderung weiterzuleiten und die virtuelle Tastatur zu schließen. Wenn Sie auf die Eingabetaste tippen, wird keine Aktion ausgeführt.

1. Tippen Sie oben rechts auf **[!UICONTROL Speichern]**.
1. Veröffentlichen Sie die neue Viewer-Vorgabe.  Sie müssen die Vorgabe veröffentlichen, um sie auf Ihrer Website verwenden zu können. 

   Siehe [Veröffentlichen von Viewer-Vorgaben](#publishing-viewer-presets).

### Besondere Hinweise zum Erstellen von Viewer-Vorgaben für interaktive Videos    {#special-considerations-for-creating-an-interactive-viewer-preset}

**Wissenswertes über Anzeigemodi für Bildminiaturansichten im Anzeigefeld** 

Beim Erstellen oder Bearbeiten einer Viewer-Vorgabe für interaktive Videos können Sie die zu verwendende Anzeigemodus-Einstellung festlegen, wenn Sie `InteractiveSwatches` aus dem Pulldown-Menü **[!UICONTROL Ausgewählte Komponente]** unter der Registerkarte **[!UICONTROL Verhalten]** auswählen. Der von Ihnen gewählte Anzeigemodus beeinflusst, wie und wann Miniaturansichten während der Videowiedergabe angezeigt werden. Sie können entweder den Anzeigemodus `segment` (Standard) oder den Anzeigemodus `continuous` auswählen.

<table>
 <tbody>
  <tr>
   <td><strong>Anzeigemodus</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>Segment</td>
   <td><p><code>Segment </code>ist der Standardanzeigemodus für die vordefinierten Viewer-Vorgaben für interaktive Videos <code>Shoppable_Video_light</code> und <code>Shoppable_Video_dark</code> sowie alle Viewer-Vorgaben für interaktive Videos, die Sie selbst erstellen.</p> <p>Wenn einem Videosegment weniger Miniaturansichten als sichtbare Spots im Anzeigefeld zugewiesen sind, werden in diesem Modus Miniaturansichten von den nächsten oder vorhergehenden Untersegmenten <i>nicht</i> herangezogen, um leere Spots im Feld aufzufüllen. So bleibt die Anzeige von einem bestimmten Videosegment zugewiesenen Mustern erhalten.</p> </td>
  </tr>
  <tr>
   <td>Kontinuierlich</td>
   <td><p>Wenn im Anzeigemodus <code>continuous </code> die Anzahl der Miniaturansichten in einem Segment kleiner ist als die Anzahl der im Feld sichtbaren, schließt der Viewer automatisch die Anzeige der Miniaturansichten aus dem nächsten oder vorherigen Segment mit ein. Dies erfolgt in den Fällen, in denen die letzte Miniaturansicht angezeigt wird.</p> <p>Das <a href="/help/assets/dynamic-media/interactive-videos.md">Video in diesem Thema</a> ist ein Beispiel für den Anzeigemodus <code>continuous </code>.</p> </td>
  </tr>
 </tbody>
</table>

**Wissenswertes über den automatischen Bildlauf im Viewer für interaktive Videos**

Das automatische Bildlaufverhalten von Miniaturansichten der Viewer-Funktionen für interaktive Videos erfolgt unabhängig vom gewählten Anzeigemodus. 

Wenn Sie eine interaktive Video-Viewer-Voreinstellung erstellen oder bearbeiten, können Sie über die Registerkarte „Verhalten“ auf „Auto-Bildlauf“ zugreifen. Tippen Sie auf der Registerkarte „Verhalten“ im Dropdownmenü **[!UICONTROL Ausgewählte Komponenten]** auf **[!UICONTROL InteractiveSwatches]**. Das Kontrollkästchen „Automatischer Bildlauf“ befindet sich unter dem Textfeld „IS-Befehl“. 

Wenn Sie in der Viewer-Vorgabe bei der Videowiedergabe durch den Benutzer die Option **[!UICONTROL Automatischer Bildlauf]** deaktivieren (das Kontrollkästchen abwählen), wird im Feld während der gesamten Videodauer nur das erste Miniaturbild angezeigt.  Allerdings kann der Benutzer ggf. mithilfe der Pfeilsymbole nach oben und nach unten einen manuellen Bildlauf durch die Miniaturansichten durchführen.

Wenn Sie während der Videowiedergabe die Option **[!UICONTROL Automatischer Bildlauf]** in der Viewer-Vorgabe aktivieren (auswählen), werden die Miniaturbilder, die einem Videosegment zugewiesen sind, zu Beginn eines Segments in die Ansicht verschoben.  Es gibt jedoch Fälle, in denen bestimmte Miniaturansichten innerhalb eines Segments doppelt so lange angezeigt werden wie andere Miniaturansichten vor oder nach dem Segment. Dieses Verhalten tritt auf, weil die Anzahl der Miniaturansichten in einem Segment größer ist als die Zahl, die im Bedienfeld sichtbar ist, und diese nicht gleichmäßig teilbar ist.

Gehen wir zu Illustrationszwecken von einem 30 Sekunden langen Videosegment aus.  Insgesamt gibt es neun Miniaturansichten, die im Laufe dieser 30 Sekunden angezeigt werden.  Die Größe Ihres Browsers wird dergestalt geändert, dass vier verfügbare Miniaturpositionen im Anzeigefeld vorliegen.  Das 30-sekündige Videozeitsegment ist in drei Untersegmente unterteilt.  In der folgenden Tabelle wird aufgeschlüsselt, welche Miniaturansichten für ein bestimmtes Zeituntersegment angezeigt werden: 

| **Video-Untersegment** | **Zeit des Untersegments in Sekunden** | **Im Feld sichtbare Miniaturen** |
|---|---|---|
| 1 | 0–10 | 1, 2, 3, 4 |
| 2 | 10-20 | 4, 5, 6, 7 |
| 3 | 20-30 | 6, 7, 8, 9 |

Das Videountersegment 3 wird nicht über die Miniaturansichten hinweg erweitert, die ihm zugewiesen sind.  Beachten Sie, dass die Miniaturansichten 4, 6 und 7 im Anzeigefeld doppelt so lang sichtbar sind wie die anderen.

Die durch den Viewer zum Bestimmen der Anzahl der im seitlichen Bedienfeld angezeigten Miniaturansichten verwendete Logik basiert wie folgt auf der Anzahl der verfügbaren Positionen:

* Anzahl der Untersegmente = Aufrundung auf das nächste Untersegment (Anzahl der Miniaturansichten : Anzahl der sichtbaren Spots im Miniaturansichtsfeld, auf Grundlage der Browser-Fenstergröße)
Unter Verwendung des Beispiels in der obigen Tabelle ergibt 9 Miniaturansichten : 4 Slots = 2,25, was die Viewer-Logik auf 3 Untersegmente aufrundet.

* Anzahl der Miniaturen = Aufrundung auf die nächste Miniaturansicht (Anzahl der Miniaturansichten : Anzahl der Videountersegmente)
Unter Verwendung des Beispiels in der obigen Tabelle ergibt 9 Miniaturansichten : 3 Videountersegmente = 3 Miniaturansichten.

* Dauer des Untersegments = gesamte Videodauer : Anzahl der Videountersegmente
Unter Verwendung des Beispiels in der obigen Tabelle ergibt 30 Sekunden : 3 Segmente = 10 Sekunden anhaltende Anzeige jedes Segments.

#### Besondere Hinweise zum Erstellen von Viewer-Vorgaben für Karussellbanner {#special-considerations-for-creating-a-carousel-banner-viewer-preset}

Beim Erstellen von Viewer-Vorgaben für Karussellbanner kann der Stil von Hotspots wie folgt geändert werden: 

|  | **Beschreibung** | **Aktionen** |
|---|---|---|
| **[!UICONTROL Hotspot-Symbol]** | Ändern des für Hotspots verwendeten Symbols | Um das Bild des Hotspot-Symbols zu ändern, tippen Sie auf der Registerkarte **[!UICONTROL Erscheinungsbild]** in **[!UICONTROL Ausgewählte Komponente]** auf **[!UICONTROL ImageMapEffect]**. Wählen Sie unter **[!UICONTROL Symbol]** die Option **[!UICONTROL Hintergrund]** und navigieren Sie im Feld **[!UICONTROL Bild]** zum gewünschten Hintergrundbild. |

## Aktivieren oder Deaktivieren von Viewer-Vorgaben {#activating-or-deactivating-viewer-presets}

Welche Viewer-Vorgaben in der Benutzeroberfläche verfügbar sind, hängt davon ab, welche Vorgaben im Autorenmodus aktiviert wurden. Nach dem Erstellen ist eine Viewer-Vorgabe standardmäßig auf „Ein“ eingestellt.  Wenn Sie die Vorgabe deaktivieren möchten, wird sie nicht im Autorenmodus angezeigt. Wenn die Vorgabe veröffentlicht wird. Sie wird immer veröffentlicht, unabhängig davon, ob sie aktiviert oder deaktiviert wurde. Ggf. müssen Sie Viewer-Vorgaben deaktivieren, wenn die Liste zu umfangreich wird oder wenn eine Viewer-Vorgabe nicht zur Verfügung gestellt werden soll.

**So aktivieren oder deaktivieren Sie Viewer-Vorgaben:**

1. Tippen Sie in der linken oberen Ecke von AEM auf das AEM-Logo und tippen Sie dann in der linken Leiste auf **Tools** (Hammersymbol) > **[!UICONTROL Assets > Viewer-Vorgaben]**.
1. Tippen Sie auf der Seite „Viewer-Vorgabe“ unter der Spaltenüberschrift **[!UICONTROL Status]** auf die Umschaltfläche zum Aktivieren bzw. Deaktivieren einer Viewer-Vorgabe. 

   Bei aktivierten Viewer-Vorgaben wird die Umschaltfläche rechts in einem blauen Feld angezeigt; bei deaktivierten Viewer-Vorgaben wird die Umschaltfläche links in einem hellgrauen Feld angezeigt. 

## Veröffentlichen von Viewer-Vorgaben    {#publishing-viewer-presets}

Wird der Status einer Viewer-Vorgabe aktiviert (auf „Ein“ gestellt), bedeutet dies, dass sie in der Dynamic Media-Komponente, in der Komponente für interaktive Medien und bei jeder Anzeige eines Assets sichtbar ist.

Um jedoch ein Asset mit einer Viewer-Vorgabe bereitzustellen, muss die Viewer-Vorgabe auch veröffentlicht werden. Alle Viewer-Vorgaben müssen aktiviert und veröffentlicht werden, um die URL oder den Einbettungs-Code für ein Asset zu beziehen. Sie müssen alle im Lieferumfang von dynamischen Medien enthaltenen sofort einsetzbaren Viewer-Voreinstellungen aktivieren und veröffentlichen. Benutzerdefinierte Viewer-Voreinstellungen, die Sie erstellen und hinzufügen, werden automatisch aktiviert, müssen aber auch veröffentlicht werden.

Siehe [Aktivieren oder Deaktivieren von Viewer-Vorgaben](#activating-or-deactivating-viewer-presets). 

Siehe auch [Anzeigen von Assets in einer Vorschau](/help/assets/dynamic-media/previewing-assets.md).

**So veröffentlichen Sie Viewer-Vorgaben:**

1. Tippen Sie in der linken oberen Ecke von AEM auf das AEM-Logo und tippen Sie dann in der linken Leiste auf **Tools** (Hammersymbol) > **[!UICONTROL Assets > Viewer-Vorgaben]**.
1. Wählen Sie eine oder mehrere Viewer-Vorgaben zum Veröffentlichen aus. 
1. Tippen Sie auf der Symbolleiste auf das Symbol **[!UICONTROL Veröffentlichen]**.

## Sortieren von Viewer-Vorgaben   {#sorting-viewer-presets}

1. Tippen Sie in der linken oberen Ecke von AEM auf das AEM-Logo und tippen Sie dann in der linken Leiste auf **Tools** (Hammersymbol) > **[!UICONTROL Assets > Viewer-Vorgaben]**.
1. Klicken Sie auf **[!UICONTROL Vorgabentitel]**, **[!UICONTROL Typ]**, **[!UICONTROL Veröffentlicht]** oder **[!UICONTROL Status]**, um nach dieser Spaltenüberschrift zu sortieren. Klicken Sie beispielsweise auf **[!UICONTROL Typ]**, um die Viewer-Vorgabentypen in alphabetischer oder in umgekehrt alphabetischer Reihenfolge zu sortieren. 

## Bearbeiten von Viewer-Vorgaben {#editing-viewer-presets}

Denken Sie daran, dass die Bearbeitung von *vordefinierten, standardmäßig vorhandenen Viewer-Vorgaben* als Szenario nicht unterstützt wird.  Wenn Sie eine standardmäßig vorhandene Viewer-Vorgabe bearbeiten, werden Sie aufgefordert, die Viewer-Vorgabe unter einem neuen Namen zu speichern. 

**So bearbeiten Sie Viewer-Vorgaben**

1. Tippen Sie in der linken oberen Ecke von AEM auf das AEM-Logo und tippen Sie dann in der linken Leiste auf **Tools** (Hammersymbol) **[!UICONTROL > Assets > Viewer-Vorgaben]**.
1. Wählen Sie eine Vorgabe aus, indem Sie das Kontrollkästchen links neben dem Viewer-Vorgabentitel aktivieren. 
1. Tippen Sie in der Symbolleiste auf **[!UICONTROL Bearbeiten]**.
1. Nehmen Sie auf der Seite **[!UICONTROL Editor für Viewer-Voreinstellungen]** die gewünschten Änderungen an der Viewer-Voreinstellung vor. Verwenden Sie dazu die Optionen auf den Registerkarten **[!UICONTROL Erscheinungsbild]** und **[!UICONTROL Verhalten]**.

   Tippen Sie auf der Registerkarte **[!UICONTROL Erscheinungsbild]** in der oberen linken Ecke der Seite „Editor für Viewer-Voreinstellungen“ auf **[!UICONTROL Desktop]**, **[!UICONTROL Tablet]** oder **[!UICONTROL Telefon]**, um den Präsentationsmodus des Assets zu ändern.

1. Führen Sie in der oberen rechten Ecke der Seite eine der folgenden Aktionen aus:

   * Tippen Sie auf **[!UICONTROL Speichern]**, um Ihre Änderungen zu speichern und zur Seite „Viewer-Vorgabe“ zurückzukehren.
   * Tippen Sie auf **[!UICONTROL Abbrechen]**, um alle von Ihnen vorgenommenen Änderungen rückgängig zu machen und zur Seite „Viewer-Vorgaben“ zurückzukehren.

## Löschen von benutzerdefinierten Viewer-Vorgaben {#deleting-custom-viewer-presets}

Sie können Viewer-Vorgaben löschen, die Sie erstellt und Dynamic Media hinzugefügt haben.

**So löschen Sie benutzerdefinierte Viewer-Vorgaben**

1. Tippen Sie in der linken oberen Ecke von AEM auf das AEM-Logo und tippen Sie dann in der linken Leiste auf **[!UICONTROL Tools]** (Hammersymbol) **[!UICONTROL > Assets > Viewer-Vorgaben]**.
1. Wählen Sie auf der Seite „Viewer-Vorgaben“ einen Vorgabentitel aus und tippen Sie dann auf das Symbol **[!UICONTROL Papierkorb]**.
1. Tippen Sie auf **[!UICONTROL Löschen]**. 

## Anwenden von Viewer-Vorgaben auf Assets {#applying-a-viewer-preset-to-an-asset}

Wenn Sie das Asset und den ausgewählten Viewer bereits veröffentlicht haben, werden nach Auswahl einer Viewer-Vorgabe die Schaltflächen **[!UICONTROL URL]** und **[!UICONTROL Einbetten]** angezeigt.

**So wenden Sie eine Viewer-Vorgabe auf ein Asset an**

1. Öffnen Sie das Asset, tippen Sie in der Nähe des oberen linken Bereichs der Seite auf das Dropdown-Menü und wählen Sie **[!UICONTROL Viewer]** aus.

   >[!NOTE]
   >
   >Wenn Sie das Asset und den ausgewählten Viewer bereits veröffentlicht haben, werden nach Auswahl einer Viewer-Vorgabe die Schaltflächen **[!UICONTROL URL]** und **[!UICONTROL Einbetten]** angezeigt.

1. Wählen Sie im linken Bereich eine Viewer-Vorgabe aus, um sie auf das Asset anzuwenden. 

   Sie können die [URL kopieren, um sie für andere Benutzer freizugeben](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md). 

## Bereitstellen von Assets mit Viewer-Vorgaben {#delivering-assets-with-viewer-presets}

Informationen zum Abrufen der URLs für Viewer-Vorgaben finden Sie unter [Verknüpfen von URLs mit Ihrer Web-Anwendung](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md). Informationen hierzu finden Sie unter [Einbetten des Video-Viewers auf einer Webseite](/help/assets/dynamic-media/embed-code.md).

Wenn Sie AEM als WCM verwenden, können Sie Assets mithilfe der Viewer-Vorgaben direkt auf der Seite hinzufügen.  Siehe [Hinzufügen von Dynamic Media-Assets zu Seiten](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md). 