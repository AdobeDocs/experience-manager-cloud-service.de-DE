---
title: Herunterladen von Assets aus Content Hub
description: Erfahren Sie, wie Sie Assets aus dem Content Hub-Portal herunterladen
role: User
exl-id: 96d4ffba-4e3e-4496-9da2-6eb36be8331f
source-git-commit: 07d533962ae2922c8a467924361fdfefc5c594eb
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 50%

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

Mit Content Hub können Sie Assets herunterladen und freigeben. Auf der Content Hub-Benutzeroberfläche werden nur genehmigte Assets angezeigt. Bei diesen Assets kann es sich um Bilder, Videos oder andere digitale Inhalte handeln. Content Hub verbessert die Barrierefreiheit und Anpassungsfähigkeit und ermöglicht so eine effektive Asset-Verteilung.

Mit Content Hub können Sie einzelne oder mehrere Assets und ihre verfügbaren Ausgabedarstellungen herunterladen.

Siehe [In Content Hub verfügbare Ausgabedarstellungen](#types-of-renditions).

## Herunterladen von Assets und zugehörigen Ausgabedarstellungen {#download-asset-renditions}

Um ein Asset und seine Ausgabedarstellungen herunterzuladen, führen Sie die folgenden Schritte aus:

1. Klicken Sie auf das Asset, um dessen Eigenschaften anzuzeigen.

1. Klicken Sie auf ![Herunterladen](/help/assets/assets/download-icon.svg), um den Download-Prozess zu starten. Im Bedienfeld Herunterladen werden alle verfügbaren Asset-Ausgabedarstellungen aufgelistet.

   >[!NOTE]
   >
   * Die Ausgabedarstellungen werden nur angezeigt, wenn ihre Sichtbarkeit über die Benutzeroberfläche [Konfiguration](/help/assets/configure-content-hub-ui-options.md#renditions-content-hub) aktiviert wird.
   * Sie können alle ([, dynamischen und smarten Zuschnitt-Ausgabedarstellungen) ](#types-of-renditions) Herunterladen eines Assets herunterladen.

1. Wählen Sie mindestens eine Ausgabedarstellung aus und klicken Sie auf **[!UICONTROL Herunterladen]**.

   ![Herunterladen von Ausgabedarstellungen einzelner Assets](/help/assets/assets/download-single-asset-renditions.png)


Wenn Sie ein lizenziertes Asset herunterladen, wählen Sie **[!UICONTROL Ich habe die oben genannten Nutzungsbedingungen gelesen und akzeptiert]** aus und klicken Sie dann auf **[!UICONTROL Herunterladen]**. Sie können auch auf **[!UICONTROL Nutzungsbedingungen]** klicken, um die Asset-Lizenz anzuzeigen. Die Vorschau der Lizenz wird nur angezeigt, wenn das Asset mithilfe der Authoring-Umgebung von Assets as a Cloud Service genehmigt wurde. Weitere Informationen finden Sie unter [Verwalten von lizenzierten Assets auf Content Hub](/help/assets/manage-licensed-assets-on-content-hub.md).

>[!NOTE]
>
Benutzerinnen und Benutzer mit Zugriff auf [Dynamic Media mit Open API-Funktionen](/help/assets/dynamic-media-open-apis-overview.md) können Ausgabedarstellungen für dynamisches und smartes Zuschneiden anzeigen und herunterladen.

## Herunterladen mehrerer Assets und ihrer Ausgabedarstellungen {#download-multiple-assets-renditions}

Um mehrere Assets und ihre Ausgabedarstellungen herunterzuladen, führen Sie die folgenden Schritte aus:

1. Wählen Sie die Assets aus und klicken Sie auf ![Herunterladen](/help/assets/assets/download-icon.svg) **[!UICONTROL Herunterladen]**. Der Bildschirm [!UICONTROL Assets herunterladen] zeigt eine Liste aller ausgewählten Assets an.
1. Klicken Sie auf **[!UICONTROL Herunterladen]**, um eine der verschiedenen Download-Optionen auszuwählen und mit dem Herunterladen zu beginnen:

   * **[!UICONTROL Originale herunterladen]**: Wählen Sie diese Option aus, um die ausgewählten Assets im Originalformular herunterzuladen.
   * **Nur [!UICONTROL  Ausgabedarstellungen herunterladen]**: Wählen Sie diese Option, um alle verfügbaren statischen Ausgabedarstellungen von Assets mit Ausnahme der Original-Assets herunterzuladen.
   * **Herunterladen [!UICONTROL Originale und statische Ausgabedarstellungen]**: Wählen Sie diese Option, um sowohl ursprüngliche als auch statische Ausgabedarstellungen der ausgewählten Assets herunterzuladen.

     ![Mehrere Ausgabedarstellungen herunterladen](/help/assets/assets/download-multiple-renditions.png)

     >[!NOTE]
     >
     * Die Ausgabedarstellungen werden nur angezeigt, wenn ihre Sichtbarkeit über die Benutzeroberfläche [Konfiguration](/help/assets/configure-content-hub-ui-options.md#renditions-content-hub) aktiviert wird.
     * Sie können nur ([ Ausgabedarstellungen) ](#types-of-renditions) Herunterladen mehrerer Assets herunterladen.

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

Bei Asset-Ausgabedarstellungen handelt es sich um verschiedene Darstellungen der Originaldatei eines Assets. Dazu können Miniaturansichten, optimierte Versionen für Web- oder Mobilgeräte, mit Wasserzeichen oder DRM-geschützte Dateien oder sogar dynamische Elemente wie smartes Zuschneiden gehören. Sie müssen nicht mit dem ursprünglichen Dateityp übereinstimmen. Stattdessen dienen sie der Darstellung des Assets in verschiedenen Anwendungsfällen.

Weitere Informationen über [Anzeigen und Verwalten von Ausgabedarstellungen in Experience Manager Assets](/help/assets/renditions.md).

[!DNL Experience Manager Assets] unterstützt die folgenden Arten von Ausgabedarstellungen:

* [Statische Ausgabedarstellungen](/help/assets/renditions.md#static-renditions): Statische Ausgabedarstellungen sind vorerstellte Versionen digitaler Assets, die normalerweise während der Asset-Aufnahme oder -Änderung generiert werden. Sie sind für bestimmte Verwendungen und Plattformen optimiert, z. B. für Web-Miniaturansichten, für mobile Formate für responsive Designs oder für den Druck hochauflösender Dateien, was ein optimiertes und konsistentes Erlebnis bietet.

* [Dynamische Ausgabedarstellungen](/help/assets/renditions.md#dynamic-renditions): Dynamische Ausgabedarstellungen sind benutzerdefinierte Echtzeit-Versionen von Assets, um verschiedene Aktionen auszuführen, z. B. das Ändern der Bildgröße für verschiedene Geräteauflösungen oder das Zuschneiden zur Anpassung an verschiedene Seitenverhältnisse. Mit diesen Ausgabedarstellungen können Sie personalisierte und optimierte Erlebnisse für breitere Anforderungen anbieten. Dynamische Ausgabedarstellungen von Assets werden in [!DNL Adobe Experience Manager Assets] Autorenumgebung erstellt.

* [Smartes Zuschneiden](/help/assets/dynamic-media/image-profiles.md#creating-image-profiles): Das smarte Zuschneiden konzentriert sich während des Zuschneidevorgangs ausschließlich auf den wesentlichen Teil eines Assets. Dynamic Media Smart Crop for nutzt die von Adobe Sensei unterstützte künstliche Intelligenz zur Verfolgung des POI, um sicherzustellen, dass unsere Assets auf allen Bildschirmgrößen wie die besten aussehen. [!DNL Adobe Experience Manager] smartes Zuschneiden zeigt die Breite und Höhe von Asset-Ausgabedarstellungen zusammen mit dem Titel an. Weitere Informationen finden Sie unter [Verwenden von smartem Zuschneiden mit AEM Assets Dynamic Media](https://experienceleague.adobe.com/de/docs/experience-manager-learn/assets/dynamic-media/images/smart-crop-feature-video-use).

  ![Ausgabedarstellungstypen](/help/assets/assets/renditions-types.png)


>[!NOTE]
> 
* Um frühzeitig auf das Dynamic Media-Konto zugreifen zu können, [erstellen und senden Sie einen Adobe-Support-Fall](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html).
* Neu eingegliederte Kundinnen und Kunden auf [Open-API-Services für Dynamic Media](/help/assets/dynamic-media-open-apis-overview.md) müssen ihre vorhandenen Bildvorgaben überarbeiten, um sie zu genehmigen.



