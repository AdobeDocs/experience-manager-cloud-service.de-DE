---
title: Anzeigen und Verwalten von Ausgabedarstellungen in Experience Manager Assets
description: Erfahren Sie, wie AEM Assets und Dynamic Media die effektive Bildverwaltung mit statischen und dynamischen Bild-Ausgabedarstellungen vereinfachen.
exl-id: 006dc493-c400-4d0f-b314-c1978582b7fb
feature: Renditions
role: User
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: tm+mt
source-wordcount: '646'
ht-degree: 100%

---

# Anzeigen und Verwalten von Ausgabedarstellungen in Experience Manager Assets{#renditions}

Ausgabedarstellungen in Adobe Experience Manager (AEM) sind benutzerdefinierte Versionen digitaler Assets, z. B. Bilder, die für verschiedene Geräte und Plattformen entwickelt wurden, um eine optimale Leistung zu gewährleisten. AEM ermöglicht die einfache Erstellung und Verwaltung dieser Ausgabedarstellungen und verbessert so das Anwendererlebnis. Sie können unter anderem Miniaturansichten erstellen, Bilder für Web oder Mobilgeräte optimieren, Wasserzeichen hinzufügen und dynamische Ausgabedarstellungen oder Ausgabedarstellungen mit intelligentem Zuschnitt anzeigen und herunterladen.

Dynamic Media-Bildvorgaben und Ausgabedarstellungen mit intelligentem Zuschnitt fördern eine systematische Bildverwaltung, die auf Markenstandards ausgerichtet ist, und maximieren so die Markenkohärenz. Dies vereinfacht den Prozess der schnellen Suche und Verwendung dynamischer Bild-Ausgabedarstellungen nach Bedarf ohne Admin-Zugriff.

Ausgabedarstellungen werden zwischen statisch und dynamisch klassifiziert, wobei jeder Typ einzigartige Funktionen und Funktionen aufweist, die weiter unten ausführlicher erläutert werden.

## Statische Ausgabeformate {#static-renditions}

Statische Ausgabedarstellungen sind vorgenerierte Versionen digitaler Assets, die normalerweise bei der Aufnahme oder Änderung von Assets erstellt werden. Diese Ausgabedarstellungen sind für bestimmte Zwecke und Plattformen optimiert, wie Web-Miniaturansichten, mobile Formate für responsives Design oder hochauflösende Druckversionen, um ein effizientes und konsistentes Erlebnis zu gewährleisten.
Erfahren Sie, wie Sie [statische Ausgabedarstellungen in Experience Manager Assets anzeigen und herunterladen](#view-and-download-static-renditions) können.

### Anzeigen und Herunterladen statischer Ausgabedarstellungen{#view-and-download-static-renditions}

Gehen Sie wie folgt vor, um die Ausgabedarstellungen eines Assets anzuzeigen und herunterzuladen:

1. Klicken Sie in der Assets-Ansicht auf **Assets**, navigieren Sie zu einem Ordner, wählen Sie ein Asset aus und klicken Sie auf **Details**.
1. Klicken Sie im rechten Bereich auf das Symbol „Ausgabedarstellungen“.
1. Wählen Sie eine Ausgabedarstellung aus, um sie in der Vorschau anzuzeigen, und klicken Sie auf ![Download-Symbol](/help/assets/assets/download-icon.svg), um sie herunterzuladen.

   ![Anzeigen und Herunterladen dynamischer Ausgabedarstellungen](/help/assets/assets/view-download-static-rendition.png)

## Dynamische Ausgabedarstellungen {#dynamic-renditions}

Dynamische Ausgabedarstellungen sind benutzerdefinierte Versionen von Assets, die in Echtzeit erstellt werden, um bestimmten Anforderungen zu entsprechen, z. B. die Größenanpassung von Bildern an die Auflösung des Geräts oder das Zuschneiden auf verschiedene Seitenverhältnisse.
Mit diesen Ausgabedarstellungen können Unternehmen personalisierte und optimierte Erlebnisse für unterschiedliche Zielgruppenanforderungen bereitstellen. Sie können dynamische Ausgabedarstellungen in Experience Manager Assets anzeigen und herunterladen.

## Dynamic Media-Ausgabedarstellungen {#dynamic-media-renditions}

### Voraussetzungen

* Sie müssen eine Benutzerin bzw. ein Benutzer mit AEM Dynamic Media-Lizenz sein.
* Verwenden Sie die [!UICONTROL Admin-Ansicht], um Folgendes einzurichten:
   * [Erstellen von Bildprofilen mit intelligentem Zuschnitt](/help/assets/dynamic-media/image-profiles.md#creating-image-profiles)
   * [Bildvorgaben](/help/assets/dynamic-media/managing-image-presets.md)

  Sie können später [die Ansicht wechseln](/help/assets/assets-view-introduction.md#how-to-access-assets-view), um dynamische Ausgabedarstellungen in der Assets-Ansicht in der Vorschau anzuzeigen.
* Veröffentlichen Sie Assets in Dynamic Media, um Ausgabedarstellungen mit Dynamic Media in der Asset-Ansicht verfügbar zu machen. Weitere Informationen finden Sie unter [Veröffentlichen von Assets in AEM und Dynamic Media](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/assets-view/publish-assets-to-aem-and-dm).


### Anzeigen und Herunterladen von Dynamic Media-Ausgabedarstellungen {#view-download-dm-renditions}

Gehen Sie folgendermaßen vor, um dynamische Ausgabedarstellungen von Bildern in Experience Manager Assets anzuzeigen oder herunterzuladen:

1. Navigieren Sie zu **[!UICONTROL Asset-Verwaltung]** > **[!UICONTROL Assets]**.

1. Navigieren Sie zu dem entsprechenden Asset-Ordner.

1. Klicken Sie auf das Asset, das Sie anzeigen möchten, und klicken Sie auf **[!UICONTROL Details]**.

1. Klicken Sie im rechten Menü auf das Symbol **[!UICONTROL Dynamic Media]**. Im Bedienfeld **[!UICONTROL Dynamic Media]** werden Dynamic Media-Ausgabedarstellungen und Ausgabedarstellungen für smartes Zuschneiden angezeigt.

   ![Dynamische Ausgabedarstellungen](/help/assets/assets/dm-scene7-renditions.png)
   <!-- ![dynamic renditions](assets/preset_smart_crop_view.png) -->

1. Wählen Sie die Ausgabedarstellung für die Vorschau aus und klicken Sie auf **URL kopieren**, um die URL der ausgewählten Ausgabedarstellung zu kopieren. Klicken Sie auf **Ausgabedarstellung herunterladen**, um die Ausgabedarstellungen der Bild-Assets herunterzuladen.
1. Wählen Sie die Ausgabedarstellung für das smarte Zuschneiden aus, um eine Vorschau anzuzeigen, und klicken Sie auf **URL kopieren**, um die URL der ausgewählten Ausgabedarstellung zu kopieren.
1. Klicken Sie auf das ![Download-Symbol](assets/do-not-localize/download-icon.png), um alle verfügbaren Ausgabedarstellungen für smartes Zuschneiden als einzelne ZIP-Datei herunterzuladen.
   ![Download-Symbol](/help/assets/assets/smartcrop-rendition.png)

   >[!NOTE]
   >
   >Diese Ausgabedarstellungen sind nur für Bild-Assets verfügbar.

## Ausgabedarstellungen durch Dynamic Media mit OpenAPI-Funktionen {#dm-with-openapi-renditions}

### Voraussetzungen {#prereqs-dm-with-openapi-renditions}

* Sie müssen eine Benutzerin bzw. ein Benutzer mit AEM Dynamic Media-Lizenz sein.
* Assets müssen für die Anzeige von Ausgabedarstellungen durch Dynamic Media mit OpenAPI-Funktionen genehmigt werden. Weitere Informationen finden Sie unter [Genehmigen von Assets in Experience Manager](/help/assets/approve-assets.md#copy-delivery-url-approved-assets).
* Dynamic Media mit OpenAPI-Funktionen muss in Ihrer AEM as a Cloud Service-Instanz aktiviert sein.

### Anzeigen von Ausgabedarstellungen durch Dynamic Media mit OpenAPI-Funktionen {#view-download-dm-with-openapi-renditions}

1. Wählen Sie das Asset aus und klicken Sie auf **Details**.
1. Klicken Sie auf das Symbol „Dynamic Media“ im rechten Bedienfeld. Im Dynamic Media-Bedienfeld wird die Ausgabedarstellung durch Dynamic Media mit OpenAPI-Funktionen für alle Asset-Typen angezeigt.
   ![Download-Symbol](/help/assets/assets/dm-with-open-api-copy-url.png)
1. Wählen Sie die Option **Dynamic Media mit OpenAPI** und klicken Sie dann auf **URL kopieren**, um die Bereitstellungs-URL des Assets zu kopieren.


