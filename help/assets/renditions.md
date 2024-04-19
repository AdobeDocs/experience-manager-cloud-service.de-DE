---
title: Anzeigen und Verwalten von Ausgabedarstellungen in Experience Manager Assets
description: Erfahren Sie, wie AEM Assets und Dynamic Media die effektive Bildverwaltung mit statischen und dynamischen Bildausgabeformaten vereinfachen.
exl-id: 006dc493-c400-4d0f-b314-c1978582b7fb
source-git-commit: 4627eb00ba910d1ad2920db15a87761bd7e4a0c0
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 1%

---

# Anzeigen und Verwalten von Ausgabedarstellungen in Experience Manager Assets{#renditions}

Bei Ausgabeformaten in Adobe Experience Manager (AEM) handelt es sich um benutzerdefinierte Versionen digitaler Assets, z. B. Bilder, die für verschiedene Geräte und Plattformen entwickelt wurden, um eine optimale Leistung zu gewährleisten. AEM erleichtert die einfache Erstellung und Verwaltung dieser Ausgabedarstellungen und verbessert so das Benutzererlebnis. Sie können Miniaturansichten erstellen, Bilder für Web oder Mobilgeräte optimieren, Wasserzeichen hinzufügen, dynamische Ausgabedarstellungen oder Ausgabedarstellungen mit smartem Zuschneiden anzeigen und herunterladen und vieles mehr.

Dynamic Media-Bildvorgaben und Ausgabedarstellungen für smartes Zuschneiden fördern ein systematisches Bildmanagement, das mit den Markenstandards übereinstimmt, und maximieren so den Markenkonsum. Dies vereinfacht den Prozess der schnellen Suche und Verwendung dynamischer Bildausgabeformate bei Bedarf ohne Administratorzugriff.

Ausgabedarstellungen werden als statisch und dynamisch klassifiziert, wobei jeder Typ einzigartige Funktionen und Funktionen aufweist, die ausführlicher erläutert werden.

## Statische Ausgabeformate {#static-renditions}

Statische Ausgabeformate sind vorgenerierte Versionen digitaler Assets, die normalerweise bei der Erfassung oder Änderung von Assets erstellt werden. Diese Ausgabedarstellungen sind für bestimmte Zwecke und Plattformen optimiert, wie Webminiaturen, mobile Formate für responsives Design oder hochauflösende Druckversionen, um ein effizientes und konsistentes Erlebnis zu gewährleisten.
Lernen [Anzeigen und Herunterladen](#view-dynamic-renditions) statische Ausgabeformate in [!DNL Experience Manager Assets].

## Dynamische Ausgabedarstellungen {#dynamic-renditions}

Dynamische Ausgabeformate sind benutzerdefinierte Versionen von Assets, die in Echtzeit erstellt werden, um bestimmten Anforderungen zu entsprechen, z. B. Größenanpassung von Bildern basierend auf der Geräteauflösung oder Zuschneiden, um verschiedene Seitenverhältnisse anzupassen.
Mit diesen Ausgabedarstellungen können Unternehmen personalisierte und optimierte Erlebnisse für unterschiedliche Zielgruppenanforderungen bereitstellen. Sie können dynamische Ausgabedarstellungen in anzeigen und herunterladen. [!DNL Experience Manager Assets].

### Vorbereitung

* Sie müssen eine Lizenz AEM Dynamic Media-Benutzer haben.

* Verwendung [!UICONTROL Admin-Ansicht] einzurichten:
   * [Smartes Zuschneiden von Bildprofilen](/help/assets/dynamic-media/image-profiles.md#creating-image-profiles)
   * [Bildvorgaben](/help/assets/dynamic-media/managing-image-presets.md)

  Sie können [Ansicht wechseln](/help/assets/assets-view-introduction.md#how-to-access-assets-view) später, um eine Vorschau von dynamischen Ausgabeformaten in der Assets-Ansicht anzuzeigen.

### Dynamische Ausgabeformate anzeigen und herunterladen {#view-renditions}

So zeigen Sie dynamische Ausgabeformate von Bildern an oder laden sie herunter [!DNL Experience Manager Assets]führen Sie die folgenden Schritte aus:

1. Navigieren Sie zu **[!UICONTROL Asset-Verwaltung]** > **[!UICONTROL Assets]**.

1. Navigieren Sie zum entsprechenden Asset-Ordner.

1. Klicken Sie auf das gewünschte Bild und klicken Sie auf **[!UICONTROL Details]**.

1. Klicken Sie im rechten Menü auf **[!UICONTROL Ausgabeformate]**. <br> Die **[!UICONTROL Ausgabeformate]** -Bedienfeld mit der verfügbaren **[!UICONTROL Dynamik]** und **[!UICONTROL Smartes Zuschneiden]** Ausgabedarstellungen.

   ![dynamische Ausgabeformate](assets/preset_smart_crop.png)
   <!-- ![dynamic renditions](assets/preset_smart_crop_view.png) -->

1. Klicken Sie auf die Ausgabedarstellung, die Sie anzeigen oder herunterladen möchten.

1. Klicken Sie auf ![Download-Symbol](assets/do-not-localize/download-icon.png) neben der dynamischen Ausgabedarstellung, die Sie herunterladen müssen. <br> Alternativ können Sie die Bilddarstellung auswählen und auf **[!UICONTROL Ausgabedarstellung herunterladen]** -Option unten.

   Sie können auf die ![Download-Symbol](assets/do-not-localize/download-icon.png) -Symbol oben in **[!UICONTROL Smartes Zuschneiden]** Ausgabedarstellungsabschnitt verwenden, um alle verfügbaren Ausgabedarstellungen für das Asset mit smartem Zuschneiden herunterzuladen.

>[!NOTE]
>
>Dynamische Ausgabeformate sind nur sichtbar, wenn die Assets aus der Admin-Ansicht hochgeladen wurden.
