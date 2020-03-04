---
title: Hinzufügen von Assets mit dynamischen Medien zu Seiten
description: Erfahren Sie, wie Sie in AEM einer Seite Komponenten für dynamische Medien hinzufügen können.
translation-type: tm+mt
source-git-commit: 8464d5fa5dd1b8a8a2d5ce47321e1062b536408b

---


# Hinzufügen von Assets mit dynamischen Medien zu Seiten{#adding-dynamic-media-assets-to-pages}

Um die Funktion für dynamische Medien zu Assets hinzuzufügen, die Sie auf Ihren Websites verwenden, können Sie die Komponente **Dynamische Medien**, **Interaktive Medien**, **Panoramamedien** oder **Video-360-Medien** direkt auf der Seite hinzufügen. Wechseln Sie dazu in den Layoutmodus und aktivieren Sie die Komponenten für dynamische Medien. Anschließend können Sie der Seite diese Komponenten und der Komponente Assets hinzufügen. Die Komponenten für dynamische Medien sind smart – sie erkennen, ob Sie ein Bild oder ein Video hinzufügen. Die verfügbaren Konfigurationsoptionen ändern sich entsprechend.

Wenn Sie AEM als WCM verwenden, fügen Sie Assets für dynamische Medien direkt zur Seite hinzu. Wenn Sie einen Drittanbieter für Ihr WCM verwenden, [verknüpfen](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) Sie Ihre Assets oder [betten](/help/assets/dynamic-media/embed-code.md) Sie sie ein. Eine responsive Website von Drittanbietern finden Sie unter [Bereitstellen optimierter Bilder für eine responsive Site](/help/assets/dynamic-media/responsive-site.md).

>[!NOTE]
>
>Sie müssen Assets veröffentlichen, um sie Seiten in AEM hinzufügen zu können. Siehe [Veröffentlichen von Assets mit dynamischen Medien](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

## Hinzufügen einer Dynamic Media-Komponente zu einer Seite {#adding-a-dynamic-media-component-to-a-page}

Beim Hinzufügen einer Komponente für dynamische Medien, interaktive Medien, Panoramamedien oder 360-Grad-Videomedien gehen Sie genauso vor wie beim Hinzufügen einer Komponente zu einer beliebigen Seite. Die Dynamic Media-Komponenten werden in den folgenden Abschnitten beschrieben.

**Hinzufügen einer Dynamic Media-Komponente zu einer Seite**

1. Öffnen Sie in AEM die Seite, auf der Sie die Dynamic Media-Komponente hinzufügen möchten.
1. In the left pane, tap the **[!UICONTROL Components]** icon, then filter for Dynamic Media.

   Wenn keine Komponenten für dynamische Medien verfügbar sind, müssen Sie die Komponenten für dynamische Medien aktivieren bzw. aktivieren. Weitere Informationen finden Sie unter [Bearbeiten von Vorlagen - Vorlagenautoren](/help/sites-cloud/authoring/features/templates.md) .

   ![6_5_360video_wcmcomponent](assets/6_5_360video_wcmcomponent.png)

1. Ziehen Sie eine **[!UICONTROL Dynamic Media]**-Komponente per Drag-and-Drop an die gewünschte Position auf der Seite.

   Im folgenden Beispiel wird die Komponente für **[!UICONTROL 360-Grad-Videomedien]** verwendet.

   ![6_5_360video_wcmcomponentDrag](assets/6_5_360video_wcmcomponentdrag.png)

1. Bewegen Sie den Mauszeiger direkt über die Komponente. Wenn die Komponente blau hervorgehoben wird, tippen Sie einmal darauf, um die Symbolleiste der Komponente anzuzeigen. Tap the **[!UICONTROL Configuration (wrench)]** icon.

   ![6_5_360video_wcmcomponentconfigure](assets/6_5_360video_wcmcomponentconfigure.png)

1. Je nachdem, welche Dynamic Media-Komponente Sie auf der Seite abgelegt haben, wird ein Konfigurationsdialogfeld geöffnet. [Legen Sie die Optionen der Komponente](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md#dynamic-media-components) wie gewünscht fest.

   Im folgenden Beispiel sehen Sie das Dialogfeld der Dynamic Media-Komponente **[!UICONTROL 360-Grad-Videomedien]** und die verfügbaren Optionen in der Dropdownliste für Viewer-Vorgaben.

   ![Komponente für 360-Grad-Videomedien](assets/6_5_360video_wcmcomponentviewerpreset.png)

   Die Dynamic Media-Komponente für 360-Grad-Videomedien

1. Wenn Sie fertig sind, tippen Sie in der oberen rechten Ecke des Dialogfelds auf das Kontrollkästchen, um Ihre Änderungen zu speichern.

## Lokalisieren von Komponenten vom Typ „Dynamische Medien“{#localizing-dynamic-media-components}

Zum Lokalisieren von Komponenten vom Typ „Dynamische Medien“ stehen Ihnen zwei Möglichkeiten zur Verfügung:

* Öffnen Sie auf einer Webseite in Sites **[!UICONTROL Eigenschaften]** und wählen Sie die Registerkarte **[!UICONTROL Erweitert]**. Wählen Sie die gewünschte Sprache für die Lokalisierung aus.

   ![chlimage_1-172](assets/chlimage_1-538.png)

* Wählen Sie über den Site-Selector die gewünschte Seite oder Seitengruppe aus. Tap **[!UICONTROL Properties]** and select the **[!UICONTROL Advanced]** tab. Wählen Sie die gewünschte Sprache für die Lokalisierung aus.

   >[!NOTE]
   >
   >Please note that not all languages available in the **[!UICONTROL Language]** menu currently have tokens assigned.

## Verfügbare dynamische Medienkomponenten {#dynamic-media-components}

Dynamic Media-Komponenten sind verfügbar, wenn Sie auf das Symbol **[!UICONTROL Komponenten]** tippen und nach **[!UICONTROL Dynamic Media]** filtern.

Zu den verfügbaren Dynamic Media-Komponenten zählen:

* **[!UICONTROL Dynamische Medien]**: Wird für Assets wie Bilder, Videos, E-Kataloge und Rotationssets verwendet.
* **[!UICONTROL Interaktive Medien]** : Verwenden Sie diese Option für alle interaktiven Assets wie interaktive Videos, interaktive Bilder oder Karussell-Sets.
* **[!UICONTROL Panoramaaufnahme]** - Verwendung für Panoramabilder oder Panoramabilder mit VR.
* **[!UICONTROL Video 360-Medien]** - Wird für Video-Assets mit 360 und 360 VR verwendet.

>[!NOTE]
>
>Diese Komponenten sind nicht standardmäßig verfügbar und müssen zunächst über den Vorlagen-Editor bereitgestellt werden. Nachdem sie im Vorlageneditor zur Verfügung gestellt wurden, können Sie die Komponenten wie jede andere AEM-Komponente Ihrer Seite hinzufügen.

![6_5_dynamicmediawcmcomponents](assets/6_5_dynamicmediawcmcomponents.png)

### Komponente: Dynamische Medien {#dynamic-media-component}

Die Komponente für dynamische Medien ist intelligent. Je nachdem, ob Sie ein Bild oder ein Video hinzufügen, stehen Ihnen verschiedene Optionen zur Verfügung. Die Komponente unterstützt Bildvorgaben, bildbasierte Viewer wie Bildsets sowie Rotationssets, gemischte Mediensets und Videos. Darüber hinaus reagiert der Viewer sofort - die Bildschirmgröße ändert sich automatisch je nach Bildschirmgröße. Bei allen Viewern handelt es sich um HTML5-Viewer.

>[!NOTE]
>
>Wenn Folgendes auf Ihre Webseite zutrifft:
>
>* Mehrere Instanzen der Dynamic Media-Komponente werden auf derselben Seite verwendet.
>* Jede Instanz verwendet denselben Asset-Typ.
>
>
Beachten Sie, dass Sie den einzelnen Dynamic Media-Komponenten auf dieser Seite nicht unterschiedliche Viewer-Vorgaben zuweisen können.
>
>Sie können jedoch dieselbe Viewer-Vorgabe für alle Dynamic Media-Komponenten, die Assets desselben Typs verwenden, auf der Seite verwenden.

Wenn Sie die Dynamic Media-Komponente hinzufügen und **[!UICONTROL Einstellungen für dynamische Medien]** leer ist, ist es nicht möglich, ein Asset ordnungsgemäß hinzuzufügen. Überprüfen Sie Folgendes:

* das Bild eine Pyramid TIFF-Datei aufweist. Bilder, die vor der Aktivierung von dynamischen Medien importiert wurden, verfügen nicht über eine Pyramid TIFF-Datei.

#### Arbeiten mit Bildern {#when-working-with-images}

Mit der Komponente „Dynamische Medien“ können Sie dynamische Bilder, einschließlich Bildsets, Rotationssets und Sets für gemischte Medien, hinzufügen. Sie können Vergrößerungen sowie Verkleinerungen vornehmen und (sofern zutreffend) ein Bild in einem Rotationsset drehen oder ein Bild aus einem anderen Set auswählen.

Sie können zudem die Viewer-Vorgabe, Bildvorgabe oder das Bildformat direkt in der Komponente konfigurieren. Um ein Bild dynamisch zu machen, können Sie die Haltepunkte festlegen oder eine dynamische Bildvorgabe anwenden.

You can edit the following Dynamic Media Settings by tapping the **[!UICONTROL Edit]** icon in the component and then **[!UICONTROL Dynamic Media Settings]**.

![dm-settings-image-preset](assets/dm-settings-image-preset.png)

>[!NOTE]
>
>Standardmäßig ist die Bildkomponente für dynamische Medien adaptiv. Wenn Sie eine feste Größe einrichten möchten, legen Sie sie auf der Registerkarte **[!UICONTROL Erweitert]** in der Komponente mit der **[!UICONTROL Breite]** und **[!UICONTROL Höhe]** fest.

* **[!UICONTROL Viewer-Vorgabe]**: Wählen Sie im Dropdown-Menü eine vorhandene Viewer-Vorgabe aus. Wenn die gewünschte Viewer-Vorgabe nicht sichtbar ist, müssen Sie sie möglicherweise sichtbar machen. Siehe Verwalten von Viewer-Vorgaben. Es ist nicht möglich, eine Viewer-Vorgabe auszuwählen, wenn Sie eine Bildvorgabe verwenden, und umgekehrt.

   Dies ist die einzig verfügbare Option beim Anzeigen von Bildsets, Rotationssets oder Sets für gemischte Medien. Die angezeigten Viewer-Vorgaben sind ebenfalls intelligent – es werden nur relevante Viewer-Vorgaben angezeigt.

* **[!UICONTROL Viewer-Modifikatoren]**- Viewer-Modifikatoren haben die Form des Paars name=value mit einem &amp;-Trennzeichen und ermöglichen das Ändern von Viewern, wie im Viewer-Referenzhandbuch beschrieben. An example of a viewer modifier is `posterimage=img.jpg&caption=text.vtt,1` which sets a different image for the video thumbnail and associates a closed caption/subtitle file with the video.

* **[!UICONTROL Bildvorgabe]**: Wählen Sie im Dropdown-Menü eine vorhandene Bildvorgabe aus. Wenn die gewünschte Bildvorgabe nicht sichtbar ist, müssen Sie sie möglicherweise sichtbar machen. Siehe Verwalten von Bildvorgaben. Es ist nicht möglich, eine Viewer-Vorgabe auszuwählen, wenn Sie eine Bildvorgabe verwenden, und umgekehrt.

   Diese Option ist beim Anzeigen von Bildsets, Rotationssets oder Sets für gemischte Medien nicht verfügbar.

* **[!UICONTROL Bildmodifikatoren]**: Sie können Bildeffekte anwenden, indem Sie zusätzliche Bildbefehle bereitstellen. Diese werden unter Bildvorgaben und in der Referenz zum Image-Serving-Befehl beschrieben.

   Diese Option ist beim Anzeigen von Bildsets, Rotationssets oder Sets für gemischte Medien nicht verfügbar.

* **[!UICONTROL Haltepunkte]**: Wenn Sie dieses Asset auf einer responsiven Site verwenden, müssen Sie die Bild-Haltepunkte hinzufügen. Bildhaltepunkte müssen durch Kommas (,) voneinander getrennt werden. Diese Option kann verwendet werden, wenn in einer Bildvorgabe keine Höhe oder Breite festgelegt ist.

   Diese Option ist beim Anzeigen von Bildsets, Rotationssets oder Sets für gemischte Medien nicht verfügbar.

   You can edit the following Advanced Settings by tapping **[!UICONTROL Edit]** in the component.

* **[!UICONTROL Titel]**: Ändern Sie den Titel des Bilds.

* **[!UICONTROL Alt-Text]**- Fügen Sie dem Bild einen Titel für Benutzer hinzu, die Grafiken deaktiviert haben.

   Diese Option ist beim Anzeigen von Bildsets, Rotationssets oder Sets für gemischte Medien nicht verfügbar.

* **[!UICONTROL URL, Öffnen in]**: Sie können ein Asset so einrichten, dass ein Link geöffnet wird. Legen Sie die URL fest. Geben Sie in Öffnen in an, ob der Link im selben oder einem neuen Fenster geöffnet werden soll.

   Diese Option ist beim Anzeigen von Bildsets, Rotationssets oder Sets für gemischte Medien nicht verfügbar.

* **[!UICONTROL Breite]**: Geben Sie einen Wert in Pixel ein, wenn das Bild eine feste Größe haben soll. Wenn Sie diesen Wert leer lassen, wird das Asset adaptiv.

* **[!UICONTROL Höhe]**: Geben Sie einen Wert in Pixel ein, wenn das Bild eine feste Größe haben soll. Wenn Sie diesen Wert leer lassen, wird das Asset adaptiv.


#### Arbeiten mit Videos {#when-working-with-video}

Verwenden Sie die Komponente &quot;Dynamische Medien&quot;, um Ihren Webseiten dynamische Videos hinzuzufügen. Beim Bearbeiten der Komponente können Sie eine vordefinierte Video-Viewer-Vorgabe für das Wiedergeben des Videos auf der Seite verwenden.

![chlimage_1-173](assets/chlimage_1-540.png)

You can edit the following Dynamic Media Settings by clicking **[!UICONTROL Edit]** in the component.

>[!NOTE]
>
>Die „Videokomponente für dynamische Medien“ ist standardmäßig adaptiv. If you want to make it a fixed size, set it in the component with the **[!UICONTROL Width]** and **[!UICONTROL Height]** in the **[!UICONTROL Advanced]** tab.

* **[!UICONTROL-Viewer-Vorgabe**- Wählen Sie eine vorhandene Video-Viewer-Vorgabe aus dem Dropdown-Menü. Wenn die gewünschte Viewer-Vorgabe nicht sichtbar ist, müssen Sie sie möglicherweise sichtbar machen. Siehe Verwalten von Viewer-Vorgaben.

* **[!UICONTROL Viewer-Modifikatoren**- Viewer-Modifikatoren haben die Form eines &quot;name=value&quot;-Paars mit einem &amp;-Trennzeichen und ermöglichen das Ändern von Viewern, wie im Adobe Viewer-Referenzhandbuch beschrieben. An example of a viewer modifier is `posterimage=img.jpg&caption=text.vtt,1`

   Viewer-Modifikatoren ermöglichen z. B. Folgendes:

   * Verknüpfen Sie eine Untertiteldatei mit einem Video: [caption](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-caption.html)
   * Verknüpfen Sie eine Navigationsdatei mit einem Video: [Navigation](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-navigation.html)
   You can edit the following Advanced Settings by clicking **[!UICONTROL Edit]** in the component.

* **[!UICONTROL Title**- Ändern Sie den Titel des Videos.

* **[!UICONTROL Breite]**: Geben Sie einen Wert in Pixel ein, wenn das Bild eine feste Größe haben soll. Wenn Sie diesen Wert leer lassen, wird das Asset adaptiv.

* **[!UICONTROL Höhe]**: Geben Sie einen Wert in Pixel ein, wenn das Bild eine feste Größe haben soll. Wenn Sie diesen Wert leer lassen, wird das Asset adaptiv.

#### Bei der Arbeit mit Smart-Zuschnitt {#when-working-with-smart-crop}

Verwenden Sie die Komponente &quot;Dynamische Medien&quot;, um Ihren Webseiten Bild-Assets für intelligente Zuschnitte hinzuzufügen. Beim Bearbeiten der Komponente können Sie eine vordefinierte Video-Viewer-Vorgabe für das Wiedergeben des Videos auf der Seite verwenden.

Siehe [Verwenden von intelligentem Beschneiden mit dynamischen AEM Assets](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/dynamic-media/smart-crop-feature-video-use.html)

Weitere Informationen finden Sie unter [Bildprofile](/help/assets/dynamic-media/image-profiles.md).

![dm-settings-smart-cut](assets/dm-settings-smart-crop.png)

You can edit the following Dynamic Media Setting by clicking **[!UICONTROL Edit]** in the component.

>[!NOTE]
>
>Standardmäßig ist die Bildkomponente für dynamische Medien adaptiv. Wenn Sie eine feste Größe einrichten möchten, legen Sie sie auf der Registerkarte **[!UICONTROL Erweitert]** in der Komponente mit der **[!UICONTROL Breite]** und **[!UICONTROL Höhe]** fest.

* **[!UICONTROL Bildmodifikatoren]**: Sie können Bildeffekte anwenden, indem Sie zusätzliche Bildbefehle bereitstellen. Diese werden unter Bildvorgaben und in der Referenz zum Image-Serving-Befehl beschrieben.

   Diese Option ist beim Anzeigen von Bildsets, Rotationssets oder Sets für gemischte Medien nicht verfügbar.

   You can edit the following Advanced Settings by clicking **[!UICONTROL Edit]** in the component.

* **[!UICONTROL Seitenverhältnis]** aktivieren: Wählen Sie diese Option, um eine intelligente Schnittdarstellung mit einem Seitenverhältnis auszuwählen, das dem Seitenverhältnis des Originalbilds am besten entspricht.

* **[!UICONTROL Titel]**: Ändern Sie den Titel des Smart-Freistellungsbilds.

* **[!UICONTROL Alt-Text]**: Fügen Sie dem Bild für intelligente Beschneidung einen Titel für Benutzer hinzu, die Grafiken deaktiviert haben.

   Diese Option ist beim Anzeigen von Bildsets, Rotationssets oder Sets für gemischte Medien nicht verfügbar.

* **[!UICONTROL URL, Öffnen in]**: Sie können ein Asset so einrichten, dass ein Link geöffnet wird. Legen Sie die URL fest. Geben Sie in Öffnen in an, ob der Link im selben oder einem neuen Fenster geöffnet werden soll.

   Diese Option ist beim Anzeigen von Bildsets, Rotationssets oder Sets für gemischte Medien nicht verfügbar.

* **[!UICONTROL Breite]**: Geben Sie einen Wert in Pixel ein, wenn das Bild eine feste Größe haben soll. Wenn Sie diesen Wert leer lassen, wird das Asset adaptiv.

* **[!UICONTROL Höhe]**: Geben Sie einen Wert in Pixel ein, wenn das Bild eine feste Größe haben soll. Wenn Sie diesen Wert leer lassen, wird das Asset adaptiv.

### Komponente: Interaktive Medien {#interactive-media-component}

Die Komponente „Interaktive Medien“ ist für Assets mit interaktiven Elementen wie Hotspots oder Imagemaps vorgesehen. Verwenden Sie bei interaktiven Bildern, interaktiven Videos oder Karussellbannern die Komponente **[!UICONTROL Interaktive Medien]**.

Die Komponente Interaktive Medien ist intelligent. Je nachdem, ob Sie ein Bild oder ein Video hinzufügen, stehen Ihnen verschiedene Optionen zur Verfügung. Darüber hinaus reagiert der Viewer sofort - die Bildschirmgröße ändert sich automatisch je nach Bildschirmgröße. Bei allen Viewern handelt es sich um HTML5-Viewer.

>[!NOTE]
>
>Wenn Folgendes auf Ihre Webseite zutrifft:
>
>* Mehrere Instanzen der Komponente für interaktive Medien werden auf derselben Seite verwendet.
>* Jede Instanz verwendet denselben Asset-Typ.
>
>
Beachten Sie, dass Sie den einzelnen Komponenten für interaktive Medien auf dieser Seite nicht unterschiedliche Viewer-Vorgaben zuweisen können.
>
>Sie können jedoch dieselbe Viewer-Vorgabe für alle interaktiven Medienkomponenten, die Assets desselben Typs verwenden, auf der Seite verwenden.

![chlimage_1-174](assets/chlimage_1-541.png)

You can edit the following **[!UICONTROL General]** settings by tapping **[!UICONTROL Edit]** in the component.

* **[!UICONTROL Viewer-Vorgabe]**: Wählen Sie im Dropdown-Menü eine vorhandene Viewer-Vorgabe aus. Wenn die gewünschte Viewer-Vorgabe nicht sichtbar ist, müssen Sie sie möglicherweise sichtbar machen. Viewer-Vorgaben müssen veröffentlicht werden, bevor sie verwendet werden können. Siehe Verwalten von Viewer-Vorgaben.

* **[!UICONTROL Titel]**: Ändern Sie den Titel des Videos.

* **[!UICONTROL Breite]**: Geben Sie einen Wert in Pixel ein, wenn das Bild eine feste Größe haben soll. Wenn Sie diesen Wert leer lassen, wird das Asset adaptiv.

* **[!UICONTROL Höhe]**: Geben Sie einen Wert in Pixel ein, wenn das Bild eine feste Größe haben soll. Wenn Sie diesen Wert leer lassen, wird das Asset adaptiv.

   Sie können die folgenden Einstellungen zum Hinzufügen zum Warenkorb **** bearbeiten, indem Sie in der Komponente auf **[!UICONTROL Bearbeiten]** klicken.

* **[!UICONTROL Produkt-Asset]** anzeigen: Standardmäßig ist dieser Wert ausgewählt. Das Produkt-Asset zeigt ein Bild des Produkts, wie im Commerce-Modul definiert. Deaktivieren Sie das Kontrollkästchen, um das Produkt-Asset nicht anzuzeigen.

* **[!UICONTROL Produktpreis]** anzeigen: Dieser Wert ist standardmäßig ausgewählt. Der Produktpreis gibt den Preis des Artikels an, wie im Commerce-Modul definiert. Deaktivieren Sie das Kontrollkästchen, um den Produktpreis nicht anzuzeigen.

* **[!UICONTROL Produktformular]** anzeigen: Standardmäßig ist dieser Wert nicht ausgewählt. Das Produktformular beinhaltet jegliche Produktvarianten, etwa hinsichtlich der Größe und der Farbe. Deaktivieren Sie das Kontrollkästchen, um die Produktvarianten nicht anzuzeigen.

### Komponente: Panoramabilder {#panoramic-media-component}

Die Panoramamedienkomponente bezieht sich auf Kugelpanoramen. Solche Bilder bieten ein 360°-Zuschauererlebnis eines Raums, einer Immobile, eines Ortes oder einer Landschaft. Damit ein Bild als Kugelpanorama gilt, muss MINDESTENS eine der beiden folgenden Eigenschaften zutreffen:

* Ein Seitenverhältnis von 2:1.
* Tagged with the keywords `equirectangular` or (`spherical` + `panorama`) or (`spherical` + `panoramic`). Weitere Informationen finden Sie unter [Verwenden von Tags](/help/sites-cloud/authoring/features/tags.md).

Sowohl das Seitenverhältnis als auch die Keywordkriterien gelten für Panorama-Assets für die Seite mit den Asset-Details und die WCM-Komponente mit den **[!UICONTROL Panoramamedien]**.

>[!NOTE]
>
>Wenn Folgendes auf Ihre Webseite zutrifft:
>
>* Multiple instances of the **[!UICONTROL Panoramic Media]** component being used on the same page.
>* Jede Instanz verwendet denselben Asset-Typ.
>
>
Beachten Sie, dass das Zuweisen einer anderen Viewer-Voreinstellung zu jeder **[!UICONTROL Panoramamedien]**-Komponente auf dieser Seite nicht unterstützt wird.
>
>Sie können jedoch dieselbe Viewer-Vorgabe für alle Komponenten für Panoramamedien, die Assets desselben Typs verwenden, auf der Seite verwenden.

![panoramic-media-viewer-preset](assets/panoramic-media-viewer-preset.png)

You can edit the following setting by tapping **[!UICONTROL Configure]** in the component.

* **[!UICONTROL Viewer-Vorgabe]**: Wählen Sie im Dropdown-Menü &quot;Viewer-Vorgabe&quot;einen vorhandenen Viewer aus.

Wenn die gesuchte Viewer-Vorgabe nicht angezeigt wird, stellen Sie sicher, dass sie veröffentlicht wurde. Sie müssen Viewer-Vorgaben veröffentlichen, bevor Sie sie verwenden können. Siehe [Verwalten von Viewer-Vorgaben](/help/assets/dynamic-media/managing-viewer-presets.md).

### Komponente: Video 360-Medien {#video-media-component}

Use the **[!UICONTROL Video 360 Media]** component to render equirectangular video on your web page for an immersive viewing experience of a room, property, location, landscape, or medical procedure.

Während der Wiedergabe auf einer flachen Anzeige kann der Benutzer den Anzeigewinkel bestimmen; bei der Wiedergabe auf Mobilgeräten werden in der Regel die integrierten gyroskopischen Funktionen verwendet.

Der Viewer bietet native Unterstützung für die Bereitstellung von 360-Grad-Videoassets. Standardmäßig ist keine weitere Konfiguration für die Anzeige oder die Wiedergabe erforderlich. 360-Grad-Videos werden mit Standardvideoerweiterungen wie .mp4, .mkv und .mov bereitgestellt. Der am häufigsten verwendete Codec ist H.264.

![6_5_360video_wcmcomponent-1](assets/6_5_360video_wcmcomponent-1.png)

You can edit the following setting by tapping **[!UICONTROL Configure]** in the component.

* **[!UICONTROL Viewer-Vorgabe]**: Wählen Sie im Dropdown-Menü &quot;Viewer-Vorgabe&quot;einen vorhandenen Viewer aus. Verwenden Sie Video360VR für Endbenutzer, die Virtual-Reality-Brillen verwenden. Enthält grundlegende Steuerelemente für die Videowiedergabe und Social-Media-Eigenschaften. Verwenden Sie Video360_social mit grundlegenden Steuerelementen für die Videowiedergabe. Videorendering erfolgt im Stereomodus. Die manuelle Blickwinkelsteuerung ist deaktiviert, aber gyroskopische Steuerelemente sind aktiviert. Social-Media-Eigenschaften sind nicht verfügbar.

Wenn die gesuchte Viewer-Vorgabe nicht angezeigt wird, stellen Sie sicher, dass sie veröffentlicht wurde. Sie müssen Viewer-Vorgaben veröffentlichen, bevor Sie sie verwenden können. Siehe [Verwalten von Viewer-Vorgaben](/help/assets/dynamic-media/managing-viewer-presets.md).

### Bereitstellen von Assets mit dynamischen Medien mit HTTP/2 {#using-http-to-delivery-dynamic-media-assets}

HTTP/2 ist das neue, aktualisierte Webprotokoll, das die Kommunikation zwischen Browser und Servern verbessert. Es beschleunigt die Übertragung von Informationen und reduziert die erforderliche Prozessorleistung. Es ist jetzt möglich, Dynamic Media-Assets über HTTP/2 bereitzustellen, das schnellere Reaktions- und Ladezeiten bietet.

Vollständige Informationen zu den ersten Schritten mit HTTP/2 und Ihrem Dynamic Media-Konto finden Sie unter [Bereitstellung von Inhalt über HTTP/2](/help/assets/dynamic-media/http2faq.md).

>[!MORELIKETHIS]
>
>* [Verwenden des Video-Players in AEM Dynamic Media](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/dynamic-media/dynamic-media-video-player-feature-video-use.html)
>* [Interaktive Videos mit AEM Dynamic Media](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/dynamic-media/dynamic-media-interactive-video-feature-video-use.html)
>* [Erläuterungen zum Asset Viewer mit AEM Dynamic Media](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/dynamic-media/dynamic-media-viewer-feature-video-understand.html)
>* [Verwenden der benutzerdefinierten Videominiatur mit AEM Dynamic Media](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/dynamic-media/dynamic-media-video-thumbnails-feature-video-use.html)
>* [Farbmanagement mit AEM Dynamic Media](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/dynamic-media/dynamic-media-color-management-technical-video-setup.html)
>* [Verwenden des Scharfzeichnens von Bildern mit AEM Dynamic Media](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/dynamic-media/dynamic-media-image-sharpening-feature-video-use.html)

