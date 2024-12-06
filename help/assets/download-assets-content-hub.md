---
title: Herunterladen von Assets aus Content Hub
description: Erfahren Sie, wie Sie Assets aus dem Content Hub-Portal herunterladen
role: User
exl-id: 96d4ffba-4e3e-4496-9da2-6eb36be8331f
source-git-commit: 28424cb184d0378669498c78e571961227f6539a
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Herunterladen von Assets aus Content Hub {#download-assets}

| [Best Practices für die Suche](/help/assets/search-best-practices.md) | [Best Practices für Metadaten](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [Dynamic Media mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md) | [Entwicklerdokumentation zu AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

<!-- ![Download assets](assets/download-asset.jpg) -->
![Herunterladen von Assets](assets/download-asset-genstudio.jpeg)

>[!AVAILABILITY]
>
>Das Content Hub-Handbuch ist jetzt im PDF-Format verfügbar. Laden Sie das gesamte Handbuch herunter und verwenden Sie den KI-Assistenten von Adobe Acrobat, um Ihre Fragen zu beantworten.
>
>[!BADGE Content Hub-Handbuch als PDF]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/content-hub.pdf"}

Mit Content Hub können Sie Assets herunterladen und freigeben. In der Content Hub-Benutzeroberfläche werden nur genehmigte Assets angezeigt. Bei diesen Assets kann es sich um Bilder, Videos oder andere digitale Inhalte handeln. Content Hub verbessert die Barrierefreiheit und Anpassungsfähigkeit und ermöglicht so eine effektive Asset-Verteilung.

Sie können einzelne oder mehrere Assets und deren verfügbare Ausgabeformate mit Content Hub herunterladen.

## Herunterladen eines Assets und seiner Ausgabeformate {#download-asset-renditions}

Führen Sie die folgenden Schritte aus, um ein Asset und seine Ausgabeformate herunterzuladen:

1. Klicken Sie auf das Asset, um seine Eigenschaften anzuzeigen.

1. Klicken Sie auf ![Download](/help/assets/assets/download-icon.svg) , um den Download-Prozess zu starten. Im Bereich Download werden alle verfügbaren Asset-Ausgabedarstellungen (Original und andere Ausgabedarstellungen) aufgelistet.

   >[!NOTE]
   >
   Die Ausgabedarstellungen werden nur angezeigt, wenn ihre Sichtbarkeit über die Benutzeroberfläche von [Konfiguration](/help/assets/configure-content-hub-ui-options.md#renditions-content-hub) aktiviert ist.

1. Wählen Sie die Ausgabedarstellungen aus und klicken Sie auf **[!UICONTROL Download]**.

   ![Herunterladen einzelner Asset-Ausgabedarstellungen](/help/assets/assets/download-single-asset-renditions.png)


Wenn Sie ein lizenziertes Asset herunterladen, wählen Sie **[!UICONTROL Ich habe die oben genannten Nutzungsbedingungen gelesen und akzeptiert]** und klicken Sie dann auf **[!UICONTROL Herunterladen]**. Sie können auch auf **[!UICONTROL Nutzungsbedingungen]** klicken, um die Asset-Lizenz anzuzeigen. Die Lizenzvorschau wird nur angezeigt, wenn das Asset mithilfe der Assets as a Cloud Service Authoring-Umgebung genehmigt wurde. Weitere Informationen finden Sie unter [Verwalten von lizenzierten Assets auf Content Hub](/help/assets/manage-licensed-assets-on-content-hub.md).

## Herunterladen mehrerer Assets und ihrer Ausgabeformate {#download-multiple-assets-renditions}

Führen Sie die folgenden Schritte aus, um mehrere Assets und deren Ausgabedarstellungen herunterzuladen:

1. Wählen Sie die Assets aus und klicken Sie auf ![download](/help/assets/assets/download-icon.svg) **[!UICONTROL Download]**. Der Bildschirm [!UICONTROL Assets herunterladen] zeigt eine Liste aller ausgewählten Assets an.
1. Klicken Sie auf **[!UICONTROL Download]** , um unter den verschiedenen Download-Optionen auszuwählen, mit denen der Download beginnen soll:

   * **Download [!UICONTROL Originale]**: Wählen Sie diese Option, um die ausgewählten Assets im Originalformular herunterzuladen.
   * **Nur Ausgabedarstellungen herunterladen [!UICONTROL Nur Ausgabedarstellungen]**: Wählen Sie diese Option, um alle verfügbaren Ausgabedarstellungen der Assets mit Ausnahme der Original-Assets herunterzuladen.
   * **Download [!UICONTROL Originale und alle Ausgabeformate]**: Wählen Sie diese Option, um sowohl Original- als auch Ausgabeformate der ausgewählten Assets herunterzuladen.

     ![Mehrere Ausgabedarstellungen herunterladen](/help/assets/assets/download-multiple-renditions.png)

     >[!NOTE]
     >
     Die Ausgabedarstellungen werden nur angezeigt, wenn ihre Sichtbarkeit über die Benutzeroberfläche von [Konfiguration](/help/assets/configure-content-hub-ui-options.md#renditions-content-hub) aktiviert ist.

   Wenn eines der ausgewählten Assets ein lizenziertes Asset ist, klicken Sie im linken Bereich auf die Lizenz des Assets, um dessen Vorschau anzuzeigen. Dadurch können Sie &quot;**[!UICONTROL Ich habe die oben genannten Nutzungsbedingungen gelesen und akzeptiert&quot;]** auswählen und dann auf &quot;**[!UICONTROL Herunterladen]**&quot; klicken. Die Lizenzvorschau wird nur angezeigt, wenn das Asset mithilfe der Assets as a Cloud Service Authoring-Umgebung genehmigt wurde. Weitere Informationen finden Sie unter [Verwalten von lizenzierten Assets auf Content Hub](/help/assets/manage-licensed-assets-on-content-hub.md).

   ![Herunterladen mehrerer Lizenzen](/help/assets/assets/download-multiple-license.png)

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







