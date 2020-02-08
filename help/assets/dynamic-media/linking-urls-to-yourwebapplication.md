---
title: Verknüpfen von URLs mit einer Webanwendung
description: Verknüpfen von URLs mit einer Webanwendung in dynamischen Medien
translation-type: tm+mt
source-git-commit: 6224d193adfb87bd9b080f48937e0af1f03386d6

---


# Verknüpfen von URLs mit einer Webanwendung {#linking-urls-to-your-web-application}

Ihre Websites und Anwendungen greifen mithilfe von URL-Aufrufen auf dynamische Mediendienste zu. Wenn Sie ein Asset veröffentlichen, wird eine URL-Zeichenfolge, die auf das Asset verweist, von „Dynamische Medien“ aktiviert. Sie können diese URLs zu Testzwecken in einen Webbrowser einfügen.

Sie verknüpfen nur dann zu URLs, wenn Sie AEM *nicht* als Ihren WCM verwenden. &quot;Verknüpfen mit&quot;oder &quot;Einbetten&quot;wird verwendet, wenn Sie einen Videoplayer als Popup- oder modales Fenster bereitstellen möchten. Wenn Sie AEM als Ihren WCM verwenden, [fügen Sie die Assets direkt zu Ihrer Seite hinzu](adding-dynamic-media-assets-to-pages.md).

Um diese URL-Zeichenfolgen auf Ihren Webseiten und Anwendungen zu platzieren, müssen Sie sie aus „Dynamische Medien“ kopieren.

>[!NOTE]
>
>URL-Zeichenfolgen sind nur für dynamische Ausgabeformate von Assets verfügbar. Sie sind derzeit nicht für statische Assets verfügbar, die in DAM und nicht im Server für dynamische Medien aufbewahrt werden. Für statische Ausgabeformate wird die URL-Schaltfläche nicht angezeigt.

Siehe auch [Einbetten des Video- oder Bild-Viewers auf einer Webseite](embed-code.md).

Siehe auch [Verknüpfen von YouTube-URLs mit einer Webanwendung.](video.md)

Siehe auch [Bereitstellen von optimierten Bildern für eine responsive Site](responsive-site.md)

Informationen hierzu finden Sie auch unter [Hochladen von Assets](/help/assets/manage-digital-assets.md#uploading-assets).

## Abrufen einer URL für ein Asset {#obtaining-a-url-for-an-asset}

Sie können eine URL-Zeichenfolge abrufen, die von einer Bild- oder Viewer-Vorgabe generiert wird. Wenn Sie die URL kopieren, wird sie in der Zwischenablage abgelegt, sodass Sie sie nach Bedarf in Seiten einer Website oder Anwendung einfügen können.

>[!NOTE]
>
>Die URL kann erst kopiert werden, wenn Sie das gewählte Asset veröffentlicht haben. Darüber hinaus müssen Sie die Viewer-Vorgabe oder die Bildvorgabe veröffentlichen.
>
>Siehe [Veröffentlichen von Assets](publishing-dynamicmedia-assets.md).
>
>Siehe [Veröffentlichen von Viewer-Vorgaben](managing-viewer-presets.md#publishing-viewer-presets).
>
>Siehe [Veröffentlichen von Bildvorgaben](managing-image-presets.md#publishing-image-presets).

Sie können URL-Zeichenfolgen auf verschiedene Arten abrufen. Im Folgenden wird allerdings nur eine der möglichen Methoden beschrieben.

**So rufen Sie eine URL für ein Asset ab**

1. Navigate to the *published* asset whose image preset URL or viewer preset URL you want to copy, and tap the asset to open it.

   Denken Sie daran, dass URLs erst kopiert werden können, *nachdem* Sie die Assets *veröffentlicht* haben. Darüber hinaus müssen die Viewer-Vorgabe oder die Bildvorgabe ebenfalls veröffentlicht werden.

   Siehe [Veröffentlichen von Assets](publishing-dynamicmedia-assets.md).

   Siehe [Veröffentlichen von Viewer-Vorgaben](managing-viewer-presets.md#publishing-viewer-presets).

   Siehe [Veröffentlichen von Bildvorgaben](managing-image-presets.md#publishing-image-presets).

1. Führen Sie je nach gewähltem Asset eine der folgenden Aktionen aus:

   * If you selected an image, in the drop-down menu, tap **[!UICONTROL Renditions]**.

      Tippen Sie unter der Überschrift **[!UICONTROL Dynamisch]** auf einen Vorgabennamen, um das zugehörige Ausgabeformat im rechten Rahmen anzuzeigen. Möglicherweise müssen Sie in der Ausgabenformatsliste einen Bildlauf durchführen, um die Überschrift „Dynamisch“ anzuzeigen.

      Tippen Sie unten in der linken Seitenleiste auf **[!UICONTROL URL]**.

      ![chlimage_1-270](assets/chlimage_1-270.png)

   * If you selected a spin set, an image set, a carousel set, or a video, in the drop-down menu, tap **[!UICONTROL Viewers]**.

      Tippen Sie auf der linken Schiene auf einen Viewer-Vorgabennamen. Eine Vorschau des Sets oder Videos wird auf einer separaten Seite geöffnet.

      Tippen Sie auf der linken Schiene unten auf **[!UICONTROL URL]**.

      ![chlimage_1-271](assets/chlimage_1-271.png)

1. Markieren Sie den Text und kopieren Sie ihn in den Webbrowser, um eine Vorschau des Assets anzuzeigen oder es der Webinhaltsseite hinzuzufügen.

   Um das URL-Fenster zu verlassen, tippen Sie auf das **[!UICONTROL X]** oder auf **[!UICONTROL Schließen]**.

## Abrufen einer URL für ein statisches Asset {#obtaining-a-url-for-a-static-asset}

Dynamic Media unterstützt die Bereitstellung von statischen Assets, bei denen es sich neben Bildern und Videos um zusätzliche Assets handelt. Folgende unterstützte Formate von statischen Assets sind für die Bereitstellung verfügbar:

* Animiertes GIF
* Audiodateien 
* CSS
* JavaScript (wenn das Unternehmen mit einer eigenen Domäne konfiguriert wurde)
* PDF
* SVG
* XML
* ZIP

**So rufen Sie eine URL für ein statisches Asset ab**

1. Navigieren Sie zum *veröffentlichten *statischen Asset, dessen URL Sie kopieren möchten, und tippen Sie auf das Asset, um es zu öffnen.

   Beachten Sie, dass URLs erst kopiert werden können, *nachdem* Sie das statische Asset *veröffentlicht* haben.

   Siehe [Veröffentlichen von Assets](publishing-dynamicmedia-assets.md).

1. Verwenden Sie eine der folgenden Methoden, um die URL für das veröffentlichte statische Asset abzurufen:

   * `The URL of the published static is the following:`

      * `https://*<server_name>*/is/content/*<company_name>*/*<static_asset_filename>*.*<extension>*`

         Beispiel, `https://aem.com/is/content/adobe/image.gif`.
   * click **[!UICONTROL Asset > Dynamic Renditions]**, then tap a dynamic rendition of the static asset and copy the URL.

      Change the copied URL to use `is/content` in the path instead of `is/image/`.


## Abrufen einer Video-URL für ein veröffentlichtes Videoausgabeformat {#obtaining-a-video-url-for-a-published-video-rendition}

1. In AEM, navigate to **[!UICONTROL Tools > Deployment > Cloud > Cloud Services]**.
1. On the **[!UICONTROL Cloud Services]** page, scroll down to the **[!UICONTROL Dynamic Media Cloud Services]** heading, then tap **[!UICONTROL Show Configurations]**.
1. Under **[!UICONTROL Available Configurations]**, tap the name of the configuration you want.

1. On the **[!UICONTROL Dynamic Media Cloud Settings]** page, under **[!UICONTROL Video Service URL]**, copy down the entire URL path. Der kopierte URL-Pfad wird in nachfolgenden Schritten benötigt.

   Der URL-Pfad kann zum Beispiel folgendermaßen aussehen:

   `https://s7athens.macromedia.com:9090/DMGateway/`

   (Der oben angegebene Pfad dient nur zur Veranschaulichung. Es handelt sich nicht um den Pfad, den Sie kopieren.) 

1. Kopieren Sie unter **[!UICONTROL Registrierungs-ID]** den Kundennamen im letzten Teil der ID.

   For example, if the registration ID was `87654321|MyCompany`, the customer name would be `MyCompany`.

1. Near the upper-left corner of the page, tap **[!UICONTROL Cloud Services**, then tap the AEM icon and navigate to **[!UICONTROL General > CRXDE Lite]**.
1. Kopieren Sie den gesamten Pfad für das Video-Ausgabeformat aus dem JCR (Java Content Repository).

   Der Pfad für das Video-Ausgabeformat kann zum Beispiel folgendermaßen aussehen:

   `/_renditions_/0bd/0bd28743-a616-4fe6-92aa-6eae7c2112f/avs/Momentum_1080-0x720-2600k.mp4`

   (Der oben angegebene Pfad dient nur zur Veranschaulichung. Es handelt sich nicht um den Pfad, den Sie kopieren.) 

1. Ordnen Sie die kopierten Informationen in der folgenden Reihenfolge an, um einen vollständigen URL-Pfad anzulegen:

   `<Video_Service_URL>/public/<Customer_name_from_Registration_ID>/<Video_rendition_path>`

   Bei Verwendung der Beispielpfade und des Beispielkundennamens aus den oben genannten Schritten wird der vollständige Pfad wie folgt angezeigt:

   `https://s7athens.macromedia.com:9090/DMGateway/public/MyCompany/_renditions_/0bd/0bd28743-a616-4fe6-92aa-6eae7c2112ff/avs/Momentum_1080-0x720-2600k.mp4`

   Dies ist die vollständige Video-URL für ein veröffentlichtes Video-Ausgabeformat.

## Abrufen einer Video-URL für adaptives Streaming (HLS) {#obtaining-a-video-url-for-adaptive-streaming-hls}

1. In AEM, navigate to **[!UICONTROL Tools > Deployment > Cloud > Cloud Services]**.
1. On the **[!UICONTROL Cloud Services]** page, scroll down to the **[!UICONTROL Dynamic Media Cloud Services]** heading, then tap **[!UICONTROL Show Configurations]**.
1. Under **[!UICONTROL Available Configurations]**, tap the name of the configuration you want.
1. On the **[!UICONTROL Dynamic Media Cloud Services Settings]** page, do the following:

   * Unter **[!UICONTROL Videodienst-URL]** kopieren Sie den gesamten URL-Pfad. Der kopierte URL-Pfad wird in den nachfolgenden Schritten benötigt. Der URL-Pfad kann zum Beispiel folgendermaßen aussehen:
   `https://gateway-na.assetsadobe.com/DMGateway/`

   (Der oben angegebene Pfad dient nur zur Veranschaulichung. Es handelt sich nicht um den Pfad, den Sie kopieren.) 

   * Kopieren Sie unter **[!UICONTROL Registrierungs-ID]** den Kundennamen im letzten Teil der ID. Der kopierte Kundenname wird in den nachfolgenden Schritten benötigt.

       Beispiel: Für die Registrierungs-ID `87654321|demoCo` lautet der Name des Kunden, den Sie kopieren, `demoCo`.


1. Je nachdem, welches Videobereitstellungsprotokoll Sie verwenden möchten, kopieren Sie den entsprechenden Protokollselektor. Der kopierte Protokollselektor wird in den nachfolgenden Schritten benötigt.

   <table>
    <tbody>
      <tr>
      <td><strong>Von Ihnen verwendetes Videoverteilungsprotokoll</strong></td>
      <td><strong>Zu verwendende Protokollauswahl</strong></td>
      </tr>
      <tr>
      <td><p>HTTP</p> <p>Wenn Sie HTTP (nicht sichere Videobereitstellung) verwenden, stellen Sie sicher, dass Sie <code>https</code> in den zuvor kopierten Wert für die Video-Dienst-URL in <code>http</code> wechseln.</p> </td>
      <td><code>public/</code></td>
      </tr>
      <tr>
      <td>HTTPS</td>
      <td><code>public-ssl/</code></td>
      </tr>
    </tbody>
   </table>

1. Kopieren Sie den vollständigen Video-Asset-Pfad in AEM, wie mit Dynamic Media verarbeitet. Der kopierte Video-Asset-Pfad wird in den nachfolgenden Schritten benötigt.

   Beispiel:

   `/content/dam/marketing/MyVideo.mp4`

1. Kombinieren Sie alle Teile, die Sie zuvor kopiert haben, um eine Zeichenfolge in der folgenden Reihenfolge zu erstellen:

   &lt; `video service URL`>&lt; `protocol selector`>&lt; `customer name`>&lt; `video asset path`>

   Unter Verwendung der kopierten Informationen aus den obigen Beispielen würde die Zeichenfolge wie folgt aussehen:

   `https://gateway-na.assetsadobe.com/DMGateway/public-ssl/demoCo/content/dam/marketing/MyVideo.mp4`

1. Complete the URL by appending `.m3u8` to the end of the string. For example, appending `.m3u8` to the string from the previous step, the complete URL path would appear as follows:

   `https://gateway-na.assetsadobe.com/DMGateway/public-ssl/demoCo/content/dam/marketing/MyVideo.mp4.m3u8`

## Verwendung von HTTP/2 zur Bereitstellung von Dynamic Media-Assets {#using-http-to-deliver-your-dynamic-media-assets}

HTTP/2 ist das neue, aktualisierte Webprotokoll, das die Kommunikation zwischen Browser und Servern verbessert. Es beschleunigt die Übertragung von Informationen und reduziert die erforderliche Prozessorleistung. Es ist jetzt möglich, Dynamic Media-Assets über HTTP/2 bereitzustellen, das schnellere Reaktions- und Ladezeiten bietet.

Vollständige Informationen zu den ersten Schritten mit HTTP/2 und Ihrem Dynamic Media-Konto finden Sie unter [Bereitstellung von Inhalt über HTTP/2](http2.md).
