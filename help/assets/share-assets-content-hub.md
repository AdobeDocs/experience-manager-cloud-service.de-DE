---
title: Freigeben von Assets in [!DNL the Content Hub]
description: Freigeben von Assets in [!DNL the Content Hub]
role: User
exl-id: 5284d229-1596-40bf-aa5f-af4b6500ebdf
source-git-commit: 655f84593adb1199bcfc21cb54071feb3c8523c5
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 100%

---

# Freigeben von Assets im Content Hub {#search-assets-as-a-link}

Erstellen Sie einen Link zu ausgewählten Assets, um sie einfach für andere freizugeben. Wählen Sie als autorisierte Benutzerin bzw. autorisierter Benutzer von [!DNL Content Hub] ein oder mehrere Assets aus, die in Ihrer [!DNL Content Hub]-Umgebung verfügbar sind, generieren Sie einen Link und senden Sie diesen an andere private oder öffentliche Benutzende.

>[!VIDEO](https://video.tv.adobe.com/v/3474928/?captions=ger&learn=on&enablevpops=on){transcript=true}

## Voraussetzungen {#prerequisites}

[Content Hub-Benutzende](deploy-content-hub.md#onboard-content-hub-users) können einen Link zu ausgewählten Assets erstellen und ihn für andere Benutzende freigeben.

## Freigeben von Assets {#share-assets}

Um ein oder mehrere Assets für private oder öffentliche Benutzende freizugeben, führen Sie die folgenden Schritte aus:

1. Navigieren Sie zu Ihrer [!DNL Content Hub]-Homepage, wählen Sie ein oder mehrere Assets aus und klicken Sie auf ![Freigeben](/help/assets/assets/share.svg) **[!UICONTROL Freigeben]**, um ein einzelnes ausgewähltes Asset oder eine Liste mit mehreren ausgewählten Assets im Dialogfeld **[!UICONTROL Assets freigeben]** anzuzeigen.

   Sie können auch Assets auswählen und freigeben, die in ![Sammlungen](/help/assets/assets/Smock_Collection_18_N.svg) **[!UICONTROL Sammlungen]** verfügbar sind.

1. Zeigen Sie ein Asset an oder überprüfen Sie im Dialogfeld **[!UICONTROL Assets freigeben]** die Liste der verfügbaren Assets. Klicken Sie auf ![Auswahl aufheben](/help/assets/assets/Close.svg) neben einem Asset, um es aus der Liste zu entfernen.

1. Geben Sie einen Titel und eine optionale Beschreibung an, die den Satz der ausgewählten Assets definieren.

1. Wählen Sie **[!UICONTROL Gültigkeitszeitraum]** aus.

1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Wer hat Zugriff]** die Zugriffsoptionen aus und klicken Sie auf **[!UICONTROL Link abrufen]**, um einen Link zu generieren, der sich für die ausgewählten Benutzenden freigeben lässt. Private Benutzende müssen sich bei ihrer [!DNL Content Hub]-Umgebung anmelden, um auf die Seite mit den freigegebenen Assets zugreifen zu können. Öffentliche Benutzende hingegen können als Gäste auf die Seite mit freigegebenen Assets zugreifen, ohne sich bei [!DNL Content Hub] anmelden zu müssen.

<!--1. Select a **[!UICONTROL period of expiration]** and click **[!UICONTROL Get Link]** to generate a link to share with private users. Private users sign in to their [!DNL Content Hub] environment to access the shared assets page.-->

![Privater und öffentlicher Link](/help/assets/assets/shared-link-for-assets.png)

<!--Enable the **[!UICONTROL Public Link]** toggle, select a **[!UICONTROL period of expiration]** and click **[!UICONTROL Generate Public Link]** to generate a link to share with public users. Public users, as guests, access the shared assets page without signing in to [!DNL Content Hub].-->

>[!NOTE]
> 
> [Aktivieren Sie die Freigabe öffentlicher Links über die Konfigurationsseite](/help/assets/configure-content-hub-ui-options.md#enable-public-link-sharing), um den Umschalter **[!UICONTROL Öffentlicher Link]** im Dialogfeld **[!UICONTROL Freigeben von Assets]** anzuzeigen.

## Freigeben eines Assets über dessen Vorschauseite {#share-asset-from-preview-page}

Führen Sie die folgenden Schritte aus, um ein Asset bei der Vorschau freizugeben:

1. Navigieren Sie zur [!DNL Content Hub]-Startseite und klicken Sie auf die Miniaturansicht des Assets, um eine Vorschau des Assets zu sehen und die Menüoptionen im rechten Bereich des Dialogfelds anzuzeigen.
1. Wählen Sie ![Freigeben](/help/assets/assets/share.svg) aus, um das Bedienfeld **[!UICONTROL Freigeben]** anzuzeigen.
   ![Freigeben von Assets während der Vorschau](/help/assets/assets/share-link-asset-preview.png)
1. Folgen Sie Schritten 3 bis 5 im Abschnitt [Freigeben von Assets](#share-assets), um den Asset-Link (privat oder öffentlich) über das Bedienfeld **[!UICONTROL Freigeben]** zu generieren und freizugeben.

## Zugreifen auf die freigegebenen Assets {#access-shared-assets}

Rufen Sie die Seite mit freigegebenen Assets über den Link auf und führen Sie folgende Schritte aus:

* Wählen Sie mindestens ein Asset aus und klicken Sie auf ![Herunterladen](/help/assets/assets/download-icon.svg) **[!UICONTROL Herunterladen]**, um **[!UICONTROL Original]**, **[!UICONTROL Statisch]** oder beide Ausgabedarstellungen aus den verfügbaren Download-Optionen auszuwählen.
  ![](/help/assets/assets/download-shared-assets.png)
* Klicken Sie auf die Asset-Miniaturansicht, um die Metadaten des Assets anzuzeigen.
* Klicken Sie auf der Seite „Freigegebene Assets“ ([über einen privaten Link aufgerufen](#share-assets)) auf eine Asset-Miniaturansicht und wählen Sie ![Herunterladen](/help/assets/assets/download-icon.svg) aus, um die verfügbaren dynamischen Ausgabedarstellungen des Assets im Bedienfeld **[!UICONTROL Herunterladen]** auszuwählen und anzuzeigen, bevor Sie sie auswählen und herunterladen.
  ![](/help/assets/assets/download-renditions-shared-assets-page.png)


