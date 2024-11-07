---
title: Anzeigen und Verwalten von Ausgabedarstellungen in Experience Manager Assets
description: Erfahren Sie, wie AEM Assets und Dynamic Media die effektive Bildverwaltung mit statischen und dynamischen Bildausgabeformaten vereinfachen.
exl-id: 006dc493-c400-4d0f-b314-c1978582b7fb
feature: Renditions
role: User
source-git-commit: a3a6456dec178c36c9fe8acfb6f98915fc86e490
workflow-type: tm+mt
source-wordcount: '600'
ht-degree: 4%

---

# Anzeigen und Verwalten von Ausgabedarstellungen in Experience Manager Assets{#renditions}

| [Best Practices für die Suche](/help/assets/search-best-practices.md) | [Best Practices für Metadaten](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [Dynamic Media mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md) | [Entwicklerdokumentation zu AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

Bei Ausgabeformaten in Adobe Experience Manager (AEM) handelt es sich um benutzerdefinierte Versionen digitaler Assets, z. B. Bilder, die für verschiedene Geräte und Plattformen entwickelt wurden, um eine optimale Leistung zu gewährleisten. AEM erleichtert die einfache Erstellung und Verwaltung dieser Ausgabedarstellungen und verbessert so das Benutzererlebnis. Sie können Miniaturansichten erstellen, Bilder für Web oder Mobilgeräte optimieren, Wasserzeichen hinzufügen, dynamische Ausgabedarstellungen oder Ausgabedarstellungen für smartes Zuschneiden anzeigen und herunterladen und vieles mehr.

Dynamic Media-Bildvorgaben und Ausgabedarstellungen für smartes Zuschneiden fördern ein systematisches Bildmanagement, das mit den Markenstandards übereinstimmt, und maximieren so den Markenkonsum. Dies vereinfacht den Prozess der schnellen Suche und Verwendung dynamischer Bildausgabeformate bei Bedarf ohne Administratorzugriff.

Ausgabedarstellungen werden als statisch und dynamisch klassifiziert, wobei jeder Typ einzigartige Funktionen und Funktionen aufweist, die ausführlicher erläutert werden.

## Statische Ausgabeformate {#static-renditions}

Statische Ausgabeformate sind vorgenerierte Versionen digitaler Assets, die normalerweise bei der Erfassung oder Änderung von Assets erstellt werden. Diese Ausgabedarstellungen sind für bestimmte Zwecke und Plattformen optimiert, wie Webminiaturen, mobile Formate für responsives Design oder hochauflösende Druckversionen, um ein effizientes und konsistentes Erlebnis zu gewährleisten.
Erfahren Sie, wie Sie in [!DNL Experience Manager Assets] statische Ausgabeformate anzeigen und herunterladen können.[](#view-dynamic-renditions)

## Dynamische Ausgabedarstellungen {#dynamic-renditions}

Dynamische Ausgabeformate sind benutzerdefinierte Versionen von Assets, die in Echtzeit erstellt werden, um bestimmten Anforderungen zu entsprechen, z. B. Größenanpassung von Bildern basierend auf der Geräteauflösung oder Zuschneiden, um verschiedene Seitenverhältnisse anzupassen.
Mit diesen Ausgabedarstellungen können Unternehmen personalisierte und optimierte Erlebnisse für unterschiedliche Zielgruppenanforderungen bereitstellen. Sie können dynamische Ausgabedarstellungen in [!DNL Experience Manager Assets] anzeigen und herunterladen.

## Dynamic Media-Ausgabeformate {#dynamic-media-renditions}

### Vorbereitung

* Sie müssen eine Lizenz AEM Dynamic Media-Benutzer haben.
* Verwenden Sie die [!UICONTROL Admin-Ansicht], um Folgendes einzurichten:
   * [Bildprofile für smartes Zuschneiden](/help/assets/dynamic-media/image-profiles.md#creating-image-profiles)
   * [Bildvorgaben](/help/assets/dynamic-media/managing-image-presets.md)

  Sie können [ später die Ansicht wechseln](/help/assets/assets-view-introduction.md#how-to-access-assets-view), um dynamische Ausgabedarstellungen in der Assets-Ansicht in der Vorschau anzuzeigen.
* Publish-Assets in Dynamic Media verwenden, um Dynamic Media-Ausgabedarstellungen in der Assets-Ansicht verfügbar zu machen. Weitere Informationen finden Sie unter [Publish Assets to AEM and Dynamic Media](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/assets-view/publish-assets-to-aem-and-dm).


### Anzeigen und Herunterladen von Dynamic Media-Ausgabeformaten {#view-download-dm-renditions}

Gehen Sie wie folgt vor, um dynamische Ausgabeformate von Bildern in Experience Manager Assets anzuzeigen oder herunterzuladen:

1. Wechseln Sie zu **[!UICONTROL Assets-Verwaltung]** > **[!UICONTROL Assets]**.

1. Navigieren Sie zum entsprechenden Asset-Ordner.

1. Klicken Sie auf das Asset, das Sie anzeigen möchten, und klicken Sie auf **[!UICONTROL Details]**.

1. Klicken Sie im rechten Menü auf das Symbol **[!UICONTROL Dynamic Media]** . Im Bedienfeld **[!UICONTROL Dynamic Media]** werden Dynamic Media- und Smart Crop-Ausgabeformate angezeigt.

   ![dynamische Ausgabeformate](/help/assets/assets/dm-scene7-renditions.png)
   <!-- ![dynamic renditions](assets/preset_smart_crop_view.png) -->

1. Wählen Sie das Ausgabeformat aus, das in der Vorschau angezeigt werden soll, und klicken Sie auf **URL kopieren** , um die URL des ausgewählten Ausgabeformats zu kopieren. Klicken Sie auf **Ausgabedarstellung herunterladen** , um die Ausgabedarstellungen der Bild-Assets herunterzuladen.
1. Wählen Sie die Ausgabedarstellung für smartes Zuschneiden aus, um eine Vorschau anzuzeigen, und klicken Sie auf **URL kopieren** , um die URL der ausgewählten Ausgabedarstellung zu kopieren.
1. Klicken Sie auf das Symbol ![Download-Symbol](assets/do-not-localize/download-icon.png) , um alle verfügbaren Ausgabedarstellungen für smartes Zuschneiden als einzelne ZIP-Datei herunterzuladen.
   ![Symbol &quot;Herunterladen&quot;](/help/assets/assets/smartcrop-rendition.png)

   >[!NOTE]
   >
   >Diese Ausgabeformate sind nur für Bild-Assets verfügbar.

## Dynamic Media mit OpenAPI-Funktionen - Ausgabeformate {#dm-with-openapi-renditions}

### Vorbereitung

* Sie müssen eine Lizenz AEM Dynamic Media-Benutzer haben.
* Assets muss für die Anzeige von Dynamic Media mit OpenAPI-Funktionsausgabeformaten genehmigt werden. Weitere Informationen finden Sie unter [Genehmigen von Assets in Experience Manager](/help/assets/approve-assets.md#copy-delivery-url-approved-assets)
* Dynamic Media mit OpenAPI-Funktionen muss in Ihrer AEM as a Cloud Service-Instanz aktiviert sein.

### Anzeigen von Dynamic Media mit OpenAPI Capabilities-Ausgabeformaten {#view-download-dm-with-openapi-renditions}

1. Wählen Sie das Asset aus und klicken Sie auf **Details**.
1. Klicken Sie auf das Dynamic Media-Symbol im rechten Bereich. Im Dynamic Media-Bedienfeld wird die Dynamic Media mit OpenAPI Capabilities-Ausgabedarstellung für alle Asset-Typen angezeigt.
   ![Symbol &quot;Herunterladen&quot;](/help/assets/assets/dm-with-open-api-copy-url.png)
1. Wählen Sie die Option **Dynamic Media mit OpenAPI** und klicken Sie dann auf **URL kopieren** , um die Bereitstellungs-URL des Assets zu kopieren.


