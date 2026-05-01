---
title: Anwenden von smartem Zuschneiden für Videos auf genehmigte Videos
description: Dynamic Media mit OpenAPI-Funktionen ermöglichen es Ihnen, in Adobe Experience Manager (AEM) automatisch Smart-Crop-Ausgaben für genehmigte Video-Assets zu generieren.
role: Admin, User
badgeSaas: label="AEM Assets" type="Positive" tooltip="Gilt für AEM Assets)."
exl-id: video-smartcrop-dmwoapi
source-git-commit: 8ddd2ade491069e4592becf3b77c04e6bbb2c06a
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 7%

---


# Anwenden von smartem Zuschneiden für Videos auf genehmigte Videos {#apply-video-smart-crops-dmwoapi}

[!DNL Dynamic Media with OpenAPI capabilities] können Sie in [!DNL Adobe Experience Manager (AEM)] automatisch die Ausgabe für das smarte Zuschneiden von Videos für Video-Assets generieren. Smartes Zuschneiden von Videos analysiert Videoinhalte und passt das Framing dynamisch an, um das Hauptthema auf verschiedenen Seitenverhältnissen und Geräten im Fokus zu halten.

Smartes Zuschneiden von Videos wird automatisch generiert, wenn die Funktion aktiviert ist und das Video-Asset genehmigt wurde

## Voraussetzungen {#prerequisites-for-video-smart-crops}

Stellen Sie sicher, dass Sie über Folgendes verfügen:

* Sie haben Zugriff auf [!DNL AEM Assets as a Cloud Service].
* Berechtigung zum Bearbeiten von Metadatenschemata.
* Dynamic Media mit für Ihre Umgebung aktivierten OpenAPI-Funktionen.
* Video-Assets, die als „Genehmigt **[!UICONTROL markiert]** können.

## Aktivieren von smartem Zuschneiden für Videos {#enable-video-smart-crops}

Um smartes Zuschneiden für Videos zu aktivieren, konfigurieren Sie das Metadatenschema, das für Video-Assets verwendet wird:

1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadatenschemata]**.
2. Öffnen Sie das entsprechende Metadatenschema (z. B. **default**).
3. Wählen Sie das **Video**-Formular aus und klicken Sie auf **[!UICONTROL Bearbeiten]**.
4. Fügen Sie ein neues **[!UICONTROL Dropdown-Feld]** hinzu und konfigurieren Sie Folgendes:

   * **Feldbezeichnung**: Erstellen von Video-SmartCrops
   * **Zu Eigenschaft zuordnen**: `./jcr:content/dam:applyVideoSmartCrop`

5. Fügen Sie die folgenden Werte manuell hinzu:

   * Ja → wahr
   * Keine → falsch

6. Speichern Sie das Schema.

Die **Erstellen von Video-**&quot; ist jetzt im Metadatenformular für Video-Assets verfügbar.

![Feld Video-SmartCrop erstellen](/help/assets/assets/video-smartcrop-metadata-field.png)

## Anwenden von smartem Zuschneiden für Videos auf genehmigte Videos {#apply-video-smart-crops}

Sie können smartes Zuschneiden von Videos auf Video-Assets anwenden, indem Sie das Metadatenfeld aktivieren und das Asset genehmigen.

Führen Sie die folgenden Schritte aus:

1. Wählen Sie in [!DNL Assets View] **[!UICONTROL Assets]** aus und navigieren Sie zu Ihrem Ordner.
2. Wählen Sie das Video-Asset aus.
3. Klicken Sie auf **[!UICONTROL Details]**.
4. Suchen Sie im Metadaten-Bedienfeld nach **[!UICONTROL Video-Smartcards erstellen]**.
5. Setzen Sie den Wert auf **Ja** und klicken Sie dann auf **[!UICONTROL Speichern]**.
6. Setzen Sie den Asset-Status auf **[!UICONTROL Genehmigt]**.

Nachdem das Asset genehmigt wurde, werden automatisch die Ausgaben für das smarte Zuschneiden von Videos generiert.

## Video-Smart-Zugeschnittene Ausgaben anzeigen {#view-video-smart-crops}

Sobald das intelligente Zuschneiden für Videos generiert wurde:

* Die Ausgänge sind während der Videowiedergabe verfügbar.
* Der Dynamic Media-Viewer wählt automatisch den am besten geeigneten Zuschnitt auf der Grundlage des Geräts und des Seitenverhältnisses aus.
* Die Videowiedergabe wird dynamisch angepasst, um das Hauptmotiv im Fokus zu halten.

## Verwenden von Videos mit smartem Zuschneiden {#use-video-smart-crops}

Sie können die Ausgabe für das smarte Zuschneiden von Videos überall dort verwenden, wo das Video-Asset bereitgestellt wird, z. B.:

* Web-Seiten
* Anwendungen
* Eingebettete Video-Player

Der Viewer wendet während der Wiedergabe automatisch den entsprechenden smarten Zuschnitt an.

>[!NOTE]
>
>* Smartes Zuschneiden von Videos wird nur für **genehmigte** Video-Assets generiert.
>* Stellen Sie sicher **dass das Feld „Video-** erstellen“ auf &quot;**&quot;** ist, bevor Sie das Asset genehmigen.
>* Smartes Zuschneiden von Videos ändert das ursprüngliche Asset nicht. Der Zuschnitt wird während der Wiedergabe dynamisch angewendet.