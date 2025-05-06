---
title: Herunterladen von Assets aus Content Hub
description: Erfahren Sie, wie Sie Assets aus dem Content Hub-Portal herunterladen
role: User
exl-id: 96d4ffba-4e3e-4496-9da2-6eb36be8331f
source-git-commit: e108d25f3cdc025e0fbe8010854f245f62786baf
workflow-type: ht
source-wordcount: '938'
ht-degree: 100%

---

# Herunterladen von Assets aus Content Hub {#download-assets}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime und Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b>AEM Assets-Integration mit Edge Delivery Services</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>Erweiterbarkeit der Benutzeroberfläche</b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b>Aktivieren von Dynamic Media Prime und Ultimate</b></a>
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b>Best Practices für die Suche</b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b>Best Practices für Metadaten</b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b>Content Hub</b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b>Dynamic Media mit OpenAPI-Funktionen</b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b>Entwicklerdokumentation zu AEM Assets</b></a>
        </td>
    </tr>
</table>

<!-- ![Download assets](assets/download-asset.jpg) -->
![Herunterladen von Assets](assets/download-asset-genstudio.jpeg)

>[!AVAILABILITY]
>
>Das Content Hub-Handbuch ist jetzt im PDF-Format verfügbar. Laden Sie das gesamte Handbuch herunter und verwenden Sie den KI-Assistenten von Adobe Acrobat, um Ihre Fragen zu beantworten.
>
>[!BADGE Content Hub-Handbuch als PDF]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/content-hub.pdf"}

Mit Content Hub können Sie Assets herunterladen und freigeben. Auf der Content Hub-Benutzeroberfläche werden nur genehmigte Assets angezeigt. Bei diesen Assets kann es sich um Bilder, Videos oder andere digitale Inhalte handeln. Content Hub verbessert die Barrierefreiheit und Anpassungsfähigkeit und ermöglicht so eine effektive Asset-Verteilung.

Mit Content Hub können Sie einzelne oder mehrere Assets und ihre verfügbaren Ausgabedarstellungen herunterladen.

Siehe [Typen von in Content Hub verfügbaren Ausgabedarstellungen](#types-of-renditions).

## Herunterladen von Assets und zugehörigen Ausgabedarstellungen {#download-asset-renditions}

Um ein Asset und seine Ausgabedarstellungen herunterzuladen, führen Sie die folgenden Schritte aus:

1. Klicken Sie auf das Asset, um dessen Eigenschaften anzuzeigen.

1. Klicken Sie auf ![Herunterladen](/help/assets/assets/download-icon.svg), um den Download-Prozess zu starten. Im Panel „Herunterladen“ werden alle verfügbaren Asset-Ausgabedarstellungen aufgelistet.

   >[!NOTE]
   >
   >* Die Ausgabedarstellungen werden nur angezeigt, wenn ihre Sichtbarkeit über die Benutzeroberfläche [Konfiguration](/help/assets/configure-content-hub-ui-options.md#renditions-content-hub) aktiviert wird.
   >* Sie können alle [statischen bzw. dynamischen Ausgabedarstellungen und Ausgabedarstellungen für den intelligenten Zuschnitt](#types-of-renditions) beim Download eines Assets herunterladen.

1. Wählen Sie mindestens eine Ausgabedarstellung aus und klicken Sie auf **[!UICONTROL Herunterladen]**.

   ![Herunterladen von Ausgabedarstellungen einzelner Assets](/help/assets/assets/download-single-asset-renditions.png)


Wenn Sie ein lizenziertes Asset herunterladen, wählen Sie **[!UICONTROL Ich habe die oben genannten Nutzungsbedingungen gelesen und akzeptiert]** aus und klicken Sie dann auf **[!UICONTROL Herunterladen]**. Sie können auch auf **[!UICONTROL Nutzungsbedingungen]** klicken, um die Asset-Lizenz anzuzeigen. Die Vorschau der Lizenz wird nur angezeigt, wenn das Asset mithilfe der Authoring-Umgebung von Assets as a Cloud Service genehmigt wurde. Weitere Informationen finden Sie unter [Verwalten von lizenzierten Assets auf Content Hub](/help/assets/manage-licensed-assets-on-content-hub.md).

>[!NOTE]
>
> Benutzende mit Zugriff auf [Dynamic Media mit Open API-Funktionen](/help/assets/dynamic-media-open-apis-overview.md) können dynamische Ausgabedarstellungen und Ausgabedarstellungen für den intelligenten Zuschnitt anzeigen und herunterladen.

## Herunterladen mehrerer Assets und ihrer Ausgabedarstellungen {#download-multiple-assets-renditions}

Um mehrere Assets und ihre Ausgabedarstellungen herunterzuladen, führen Sie die folgenden Schritte aus:

1. Wählen Sie die Assets aus und klicken Sie auf ![Herunterladen](/help/assets/assets/download-icon.svg) **[!UICONTROL Herunterladen]**. Der Bildschirm [!UICONTROL Assets herunterladen] zeigt eine Liste aller ausgewählten Assets an.
1. Klicken Sie auf **[!UICONTROL Herunterladen]**, um eine der verschiedenen Download-Optionen auszuwählen und mit dem Herunterladen zu beginnen:

   * **[!UICONTROL Originale herunterladen]**: Wählen Sie diese Option aus, um die ausgewählten Assets im Originalformular herunterzuladen.
   * **[!UICONTROL Nur statische Ausgabedarstellungen herunterladen]**: Wählen Sie diese Option aus, um alle verfügbaren statischen Ausgabedarstellungen der Assets mit Ausnahme der Original-Assets herunterzuladen.
   * **[!UICONTROL Originale und statische Ausgabedarstellungen herunterladen]**: Wählen Sie diese Option aus, um sowohl Original- als auch statische Ausgabedarstellungen der ausgewählten Assets herunterzuladen.

     ![Mehrere Ausgabedarstellungen herunterladen](/help/assets/assets/download-multiple-renditions.png)

     >[!NOTE]
     >
     >* Die Ausgabedarstellungen werden nur angezeigt, wenn ihre Sichtbarkeit über die Benutzeroberfläche [Konfiguration](/help/assets/configure-content-hub-ui-options.md#renditions-content-hub) aktiviert wird.
     >* Beim Download mehrerer Assets können Sie nur [statische Ausgabedarstellungen](#types-of-renditions) herunterladen.

   Wenn es sich bei einem der ausgewählten Assets um ein lizenziertes Asset handelt, klicken Sie auf die Lizenz des Assets im linken Bereich, um die Vorschau anzuzeigen. Damit können Sie **[!UICONTROL Ich habe die oben genannten Nutzungsbedingungen gelesen und akzeptiert]** auswählen und dann auf **[!UICONTROL Herunterladen]** klicken. Die Vorschau der Lizenz wird nur angezeigt, wenn das Asset mithilfe der Authoring-Umgebung von Assets as a Cloud Service genehmigt wurde. Weitere Informationen finden Sie unter [Verwalten von lizenzierten Assets auf Content Hub](/help/assets/manage-licensed-assets-on-content-hub.md).

   <!--![download-multiple-license](/help/assets/assets/download-multiple-license.png)-->

<!--1. On the Content Hub homepage, select the asset and click **Download**. The **Download assets** dialog box displays a license or list of licenses associated with the selected assets in the left pane. 
1. Click a license in the left pane to see its PDF in the middle pane and the associated assets with it in the right pane. The license PDF preview is displayed only if the license is approved in your Assets as a Cloud Service environment. [Approve the license PDFs](/help/assets/approve-assets-content-hub.md) of the selected assets to see their previews.
1. Optional: Click ![remove-icon](/help/assets/assets/remove-icon.svg) to remove a license from the dialog box.
1. Select **I have read and accept all the terms and conditions mentioned above.** 
1. Click **Download** to download the selected assets.-->

<!---This dialog box displays the list of licenses associated with the selected assets in the left pane. Select a license to preview its terms and conditions (in pdf format) in the middle pane and the preview of the associated assets to the license in the right. Reviewed licenses are highlighted in light blue.


The dialog box that displays depends on whether the download list includes expired assets or only non-expired assets. <br/>
**Download expired assets dialog box:** This dialog box displays the expired assets' preview along with their expiry date in the left pane. The expired assets' count out of total selected displays in the right pane. Click **Proceed with all assets** to download expired assets with other assets (if present). The Download assets dialog box displays. See the [Download assets dialog box](#Download-asset-dialog-box) to proceed further.
    
    >[!NOTE]
    >
    >[Enable the download option for expired assets](/help/assets/configure-content-hub-ui-options.md#expired-assets-content-hub) to download them. Only expired assets that have enabled downloading are available for download.

   <a id="Download-asset-dialog-box"></a> **Download assets dialog box:** This dialog box displays the list of licenses associated with the selected assets in the left pane. Select a license to preview its terms and conditions (in pdf format) in the middle pane and the associated assets' preview and their count in the right pane. Reviewed licenses are highlighted in light blue.

    >[!NOTE]
    >
    > The **Download Asset dialog box** previews licensing terms and conditions only for approved licenses. [Approve the assets' licenses](/help/assets/approve-assets-content-hub.md) before downloading them to preview their licensing terms in the **Download Asset dialog box**.

1. Click  ![remove-icon](/help/assets/assets/remove-icon.svg) to remove a license from the download dialog box. 

1. Accept the terms and conditions and then click **Download** to download assets associated with the available licenses in the left pane.-->
<!--![download-multiple-license](/help/assets/assets/download-multiple-license.png)-->

<!---
### Download non-licensed Assets {#download-non-licensed-assets}

 To download non-licensed assets, select the assets and click ![download](/help/assets/assets/download-icon.svg) from the top rail.-->


## Typen von Ausgabedarstellungen {#types-of-renditions}

Bei Asset-Ausgabedarstellungen handelt es sich um verschiedene Darstellungen der Originaldatei eines Assets. Dazu können Miniaturansichten, optimierte Versionen für Web oder Mobilgeräte, mit Wasserzeichen versehene bzw. DRM-geschützte Dateien oder sogar dynamische Elemente wie intelligente Zuschnitte gehören. Sie müssen nicht mit dem ursprünglichen Dateityp übereinstimmen. Vielmehr dienen sie zur Darstellung des Assets in verschiedenen Anwendungsfällen.

Erfahren Sie mehr über das [Anzeigen und Verwalten von Ausgabedarstellungen in Experience Manager Assets](/help/assets/renditions.md).

[!DNL Experience Manager Assets] unterstützt die folgenden Typen von Ausgabedarstellungen:

* [Statische Ausgabedarstellungen](/help/assets/renditions.md#static-renditions): Statische Ausgabedarstellungen sind vorab erstellte Versionen digitaler Assets, die normalerweise bei der Aufnahme oder Änderung von Assets generiert werden. Sie sind für bestimmte Zwecke und Plattformen optimiert, wie Web-Miniaturansichten, mobile Formate für responsive Designs oder hochauflösende Dateiversionen für den Druck, und sorgen für ein effizientes und konsistentes Erlebnis.

* [Dynamische Ausgabedarstellungen](/help/assets/renditions.md#dynamic-renditions): Dynamische Ausgabedarstellungen sind benutzerdefinierte Echtzeitversionen von Assets, um verschiedene Aktionen auszuführen, z. B. die Größenanpassung von Bildern an verschiedene Geräteauflösungen oder das Zuschneiden auf verschiedene Seitenverhältnisse. Mit diesen Ausgabedarstellungen können Sie personalisierte und optimierte Erlebnisse für breitere Anforderungen anbieten. Dynamische Ausgabedarstellungen von Assets werden in der [!DNL Adobe Experience Manager Assets]-Autorenumgebung erstellt. Informationen zu den Schritten, die zum Aktivieren dynamischer Ausgabedarstellungen erforderlich sind, finden Sie unter [Aktivieren dynamischer Ausgabedarstellungen](#enable-dynamic-media-renditions).

* [Intelligenter Zuschnitt](/help/assets/dynamic-media/image-profiles.md#creating-image-profiles): Der intelligente Zuschnitt legt den Fokus während des Zuschneidevorgangs ausschließlich auf den wesentlichen Teil eines Assets. Der intelligente Zuschnitt in Dynamic Media nutzt die künstliche Intelligenz von Adobe Sensei, um einen Point of Interest zu verfolgen und sicherzustellen, dass Assets auf allen Bildschirmgrößen ideal aussehen. Der intelligente Zuschnitt in [!DNL Adobe Experience Manager] zeigt die Breite und Höhe von Asset-Ausgabedarstellungen zusammen mit dem Titel an. Siehe [Verwenden von smartem Zuschneiden mit AEM Assets Dynamic Media](https://experienceleague.adobe.com/de/docs/experience-manager-learn/assets/dynamic-media/images/smart-crop-feature-video-use).

  Ausgabedarstellungen für smartes Zuschneiden werden angezeigt und stehen nur dann zum Download zur Verfügung, wenn Sie Zugriff auf [Dynamic Media mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md) haben. Diese Ausgabedarstellungen sind nur für Bild-Assets verfügbar.

  ![Ausgabedarstellungstypen](/help/assets/assets/renditions-types.png)

### Aktivieren von dynamischen Ausgabedarstellungen {#enable-dynamic-media-renditions}

So aktivieren Sie dynamische Ausgabedarstellungen:

1. Stellen Sie sicher, dass Sie Zugriff auf [Dynamic Media mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md) haben.

   Sobald Sie Zugriff auf Dynamic Media mit OpenAPI-Funktionen haben, sind alle als `Approved` markierten Assets für die öffentliche Bereitstellung mit Dynamic Media verfügbar.

1. Legen Sie das [Genehmigungsziel des Assets](/help/assets/approve-assets-content-hub.md#set-approval-target) auf Content Hub fest, um Assets nur für Content Hub zu genehmigen.

1. Aktivieren Sie den Umschalter **[!UICONTROL Verfügbarkeit von Ausgabedarstellungen aktivieren]** auf der Registerkarte **[!UICONTROL Ausgabedarstellungen]** der Benutzeroberfläche [Konfiguration](/help/assets/configure-content-hub-ui-options.md#access-configuration-options-content-hub).

1. Speichern Sie die vorhandenen Bildvorgaben erneut, um sie in Content Hub verfügbar zu machen. Dies gilt nur, wenn Sie gerade das Onboarding bei Dynamic Media mit OpenAPI durchgeführt haben.

   Um die vorhandenen Bildvorgaben erneut zu speichern, navigieren Sie zur Admin-Ansicht und wählen Sie **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Bildvorgaben]** aus. Wählen Sie eine Vorgabe aus, klicken Sie auf **[!UICONTROL Bearbeiten]** und dann auf **[!UICONTROL Speichern]**.



   >[!NOTE]
   > 
   > Dynamische Ausgabedarstellungen sind nur für Bild-Assets verfügbar.



