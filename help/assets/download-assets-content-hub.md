---
title: Herunterladen von Assets aus Content Hub
description: Erfahren Sie, wie Sie einzelne oder mehrere Assets und deren Ausgabedarstellungen aus dem Content Hub-Portal herunterladen.
role: User
exl-id: 96d4ffba-4e3e-4496-9da2-6eb36be8331f
source-git-commit: fb7ce7dbb58be9fef5ab087441457770828d73c8
workflow-type: ht
source-wordcount: '814'
ht-degree: 100%

---

# Herunterladen von Assets aus Content Hub {#download-assets}

Mit [!DNL Content Hub] können Sie Assets herunterladen und freigeben. Auf der [!DNL Content Hub]-Benutzeroberfläche werden nur genehmigte Assets angezeigt. Bei diesen Assets kann es sich um Bilder, Videos oder andere digitale Inhalte handeln. [!DNL Content Hub] verbessert die Barrierefreiheit und Anpassungsfähigkeit und ermöglicht so eine effektive Asset-Verteilung.

Sie können mit [!DNL Content Hub] einzelne oder mehrere Assets und ihre verfügbaren Ausgabedarstellungen herunterladen.

Siehe [Typen von in Content Hub verfügbaren Ausgabedarstellungen](#types-of-renditions).

## Herunterladen von Assets und deren Ausgabedarstellungen {#download-asset-renditions}

Um ein oder mehrere Assets und ihre Ausgabedarstellungen herunterzuladen, führen Sie die folgenden Schritte aus:

1. Um ein Asset herunterzuladen, wählen Sie ![Herunterladen](/help/assets/assets/download-icon.svg) auf der Asset-Karte aus, um eine Vorschau des Assets anzuzeigen, wählen Sie die verfügbaren Ausgabedarstellungen aus und klicken Sie im Dialogfeld auf die Option **[!UICONTROL Herunterladen]**, um die ausgewählten Ausgabedarstellungen als ZIP-Datei herunterzuladen. Wenn im Dialogfeld eine Asset-Lizenz angezeigt wird (für lizenzierte Assets), akzeptieren Sie die Lizenzbedingungen und klicken Sie auf **[!UICONTROL Herunterladen]**.
   ![](/help/assets/assets/download-an-asset-CH-from-asset-card.png)

   Klicken Sie alternativ auf die Asset-Miniaturansicht und wählen Sie ![Herunterladen](/help/assets/assets/download-icon.svg) aus, um die verfügbaren Ausgabedarstellungen auszuwählen und im Dialogfeld anzuzeigen, bevor Sie sie herunterladen.

1. Um mehrere Assets herunterzuladen, wählen Sie die Assets aus, klicken Sie auf ![Herunterladen](/help/assets/assets/download-icon.svg) **[!UICONTROL Herunterladen]** und überprüfen Sie die Liste der ausgewählten Assets im Dialogfeld **[!UICONTROL Assets herunterladen]**. Klicken Sie auf ![Auswahl aufheben](/help/assets/assets/Close.svg) neben einem Asset, um dessen Auswahl aus der Liste wieder aufzuheben. Wählen Sie mindestens eine Ausgabedarstellung aus und klicken Sie auf **[!UICONTROL Herunterladen]**, um sie als einzelne ZIP-Datei herunterzuladen. Wenn Sie **[!UICONTROL Intelligenter Zuschnitt]** und **[!UICONTROL Statische Ausgabedarstellungen]** auswählen, werden für jedes der ausgewählten Assets alle verfügbaren Ausgabedarstellungen heruntergeladen, sowohl die statischen als auch die mit intelligentem Zuschnitt.
   ![Herunterladen mehrerer Assets](/help/assets/assets/download-multiple-assets-CH.png)
Sie können [!DNL Content Hub] während des Downloads weiter verwenden. Content Hub unterbricht Ihren Workflow während des Download-Prozesses nicht.
   ![Herunterladen mehrerer Assets](/help/assets/assets/download-assets-notification-ch.png)
Wenn das Dialogfeld **[!UICONTROL Assets herunterladen]** Asset-Lizenzen anzeigt, wählen Sie im linken Bereich (Abschnitt [!UICONTROL T&amp;C-Dokumente]) jede Lizenz aus, um im mittleren Bereich des Dialogfelds eine Vorschau der jeweiligen Lizenz und die mit der Lizenz verknüpften Assets anzuzeigen. Wählen Sie nach dem Überprüfen jeder Lizenz die Ausgabedarstellungen aus, klicken Sie auf **[!UICONTROL Ich habe die oben genannten Nutzungsbedingungen gelesen und akzeptiert]** und wählen Sie **[!UICONTROL Herunterladen]** aus, um sie herunterzuladen.
   ![herunterladen mehrerer Assets](/help/assets/assets/download-multiple-licensed-assets-CH.png)

   >[!NOTE]
   >
   >* Die Ausgabedarstellungen werden nur angezeigt, wenn ihre Sichtbarkeit über die Benutzeroberfläche [[!UICONTROL Konfiguration]](/help/assets/configure-content-hub-ui-options.md#renditions-content-hub) aktiviert wird.
   >* Benutzerinnen und Benutzer mit Zugriff auf [[!DNL Dynamic Media with Open API capabilities]](/help/assets/dynamic-media-open-apis-overview.md) können dynamische Ausgabedarstellungen und solche mit intelligentem Zuschnitt anzeigen und herunterladen.
   >* Die Vorschau der Lizenz wird nur angezeigt, wenn das Asset mithilfe der Authoring-Umgebung von [!DNL Assets as a Cloud Service] genehmigt wurde. Weitere Informationen finden Sie unter [Verwalten lizenzierter Assets in Content Hub](/help/assets/manage-licensed-assets-on-content-hub.md).

<!--

## Download an asset and its renditions {#download-asset-renditions} 

To download an asset and its renditions, execute the following steps: 

1. Click the asset to view its properties.

1. Click ![download](/help/assets/assets/download-icon.svg) to see the list of available asset renditions in the **[!UICONTROL Download]** panel.

   >[!NOTE]
   >
   >* The renditions display only if their visibility is enabled using the [Configuration](/help/assets/configure-content-hub-ui-options.md#renditions-content-hub) User Interface.
   >* You can download all [static, dynamic, and smart crop renditions](#types-of-renditions) while downloading an asset.

1. Select one or more renditions and click **[!UICONTROL Download]** to download the selected renditions as a zip file. 
While downloading a licensed asset, select **[!UICONTROL I have read and accepted the terms & conditions mentioned above]** before clicking **[!UICONTROL Download]**. You can also click **[!UICONTROL terms & conditions]** to view the asset license. The preview of the license displays only if the asset is approved using Assets as a Cloud Service authoring environment. For more information, see [Manage licensed assets on Content Hub](/help/assets/manage-licensed-assets-on-content-hub.md).

   ![Download single asset renditions](/help/assets/assets/download-single-asset-renditions.png)


If you are downloading a licensed asset, select **[!UICONTROL I have read and accepted the terms & conditions mentioned above]** and then click **[!UICONTROL Download]**. You can also click **[!UICONTROL terms & conditions]** to view the asset license. The preview of the license displays only if the asset is approved using Assets as a Cloud Service authoring environment. For more information, see [Manage licensed assets on Content Hub](/help/assets/manage-licensed-assets-on-content-hub.md).

>[!NOTE]
>
> The users with access to [Dynamic Media with Open API capabilities](/help/assets/dynamic-media-open-apis-overview.md) can view and download dynamic and smart crop renditions.

## Download multiple assets and their renditions {#download-multiple-assets-renditions} 

To download multiple assets and their renditions, execute the following steps: 

1. Select the assets and click ![download](/help/assets/assets/download-icon.svg) **[!UICONTROL Download]**. The [!UICONTROL Download assets] screen displays listing all the selected assets. 
1. Click **[!UICONTROL Download]** to select from the various download options to begin download:

    * **Download [!UICONTROL Originals]**: Select this option to download the selected assets in the original form.
    * **Download [!UICONTROL Static Renditions only]**: Select this option to download all available static renditions of assets except the original assets.
    * **Download [!UICONTROL Originals & Static Renditions]**: Select this option to download both original and static renditions of the selected assets. 

      ![Download multiple renditions](/help/assets/assets/download-multiple-renditions.png)

      >[!NOTE]
      >
      >* The renditions display only if their visibility is enabled using the [Configuration](/help/assets/configure-content-hub-ui-options.md#renditions-content-hub) User Interface.
      >* You can only download [static renditions](#types-of-renditions) while downloading multiple assets.

    If any of the selected asset is a licensed asset, click the license of the asset in left pane to see its preview, which enables you to select **[!UICONTROL I have read and accepted the terms & conditions mentioned above]** and then click **[!UICONTROL Download]**. The preview of the license displays only if the asset is approved using Assets as a Cloud Service authoring environment. For more information, see [Manage licensed assets on Content Hub](/help/assets/manage-licensed-assets-on-content-hub.md).

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

Erfahren Sie mehr über das [Anzeigen und Verwalten von Ausgabedarstellungen in [!DNL Experience Manager Assets]](/help/assets/renditions.md).

[!DNL Experience Manager Assets] unterstützt die folgenden Typen von Ausgabedarstellungen:

* [Statische Ausgabedarstellungen](/help/assets/renditions.md#static-renditions): Statische Ausgabedarstellungen sind vorab erstellte Versionen digitaler Assets, die normalerweise bei der Aufnahme oder Änderung von Assets generiert werden. Sie sind für bestimmte Zwecke und Plattformen optimiert, wie Web-Miniaturansichten, mobile Formate für responsive Designs oder hochauflösende Dateiversionen für den Druck, und sorgen für ein effizientes und konsistentes Erlebnis.

* [Dynamische Ausgabedarstellungen](/help/assets/renditions.md#dynamic-renditions): Dynamische Ausgabedarstellungen sind benutzerdefinierte Echtzeitversionen von Assets, um verschiedene Aktionen auszuführen, z. B. die Größenanpassung von Bildern an verschiedene Geräteauflösungen oder das Zuschneiden auf verschiedene Seitenverhältnisse. Mit diesen Ausgabedarstellungen können Sie personalisierte und optimierte Erlebnisse für breitere Anforderungen anbieten. Dynamische Ausgabedarstellungen von Assets werden in der [!DNL Adobe Experience Manager Assets]-Autorenumgebung erstellt. Informationen zu den Schritten, die zum Aktivieren dynamischer Ausgabedarstellungen erforderlich sind, finden Sie unter [Aktivieren dynamischer Ausgabedarstellungen](#enable-dynamic-media-renditions).

* [Intelligenter Zuschnitt](/help/assets/dynamic-media/image-profiles.md#creating-image-profiles): Der intelligente Zuschnitt legt den Fokus während des Zuschneidevorgangs ausschließlich auf den wesentlichen Teil eines Assets. Der intelligente Zuschnitt in Dynamic Media nutzt die künstliche Intelligenz von Adobe Sensei, um den interessantesten Punkt zu verfolgen und sicherzustellen, dass Assets auf allen Bildschirmgrößen ideal aussehen. Der intelligente Zuschnitt in [!DNL Adobe Experience Manager] zeigt die Breite und Höhe von Asset-Ausgabedarstellungen zusammen mit dem Titel an. Siehe [Verwenden von smartem Zuschneiden mit AEM Assets Dynamic Media](https://experienceleague.adobe.com/de/docs/experience-manager-learn/assets/dynamic-media/images/smart-crop-feature-video-use).

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



