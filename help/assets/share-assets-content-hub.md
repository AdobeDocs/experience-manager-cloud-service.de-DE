---
title: Freigeben von Assets in [!DNL the Content Hub]
description: Freigeben von Assets in [!DNL the Content Hub]
role: User
badgeSaas: label="AEM Assets" type="Positive" tooltip="Gilt für AEM Assets)."
exl-id: 5284d229-1596-40bf-aa5f-af4b6500ebdf
source-git-commit: 59f97fc6ded4274c27400f56b50b4a3329cc471a
workflow-type: tm+mt
source-wordcount: '931'
ht-degree: 44%

---

# Freigeben von Assets im Content Hub {#search-assets-as-a-link}

Erstellen Sie einen Link zu ausgewählten Assets, um sie einfach für andere freizugeben. Wählen Sie als autorisierte Benutzerin bzw. autorisierter Benutzer von [!DNL Content Hub] ein oder mehrere Assets aus, die in Ihrer [!DNL Content Hub]-Umgebung verfügbar sind, generieren Sie einen Link und senden Sie diesen an andere private oder öffentliche Benutzende.

>[!VIDEO](https://video.tv.adobe.com/v/3474890/?learn=on&enablevpops=on){transcript=true}

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

## Häufig gestellte Fragen {#faqs-share-assets-content-hub}

### Was bedeutet die Freigabe von Assets in AEM Assets Content Hub?

Durch die Freigabe von Assets in AEM Assets Content Hub können autorisierte Benutzende problemlos ein oder mehrere Assets oder ganze Sammlungen für andere freigeben, indem sie einen Link generieren. Dieser Link kann an private Benutzer (die sich anmelden müssen) oder öffentliche Benutzer (die als Gäste zugreifen können) gesendet werden, sodass Empfängerinnen und Empfänger direkten Zugriff zum Anzeigen und Herunterladen der ausgewählten Assets erhalten.

### Wie kann ich Assets oder Sammlungen mithilfe von AEM Assets Content Hub für andere freigeben?

Um Assets oder Sammlungen in AEM Assets Content Hub freizugeben, gehen Sie zur Startseite von Content Hub, wählen Sie ein oder mehrere Assets aus (oder gehen Sie zur Registerkarte „Sammlungen“ für Sammlungen) und klicken Sie auf das Symbol Freigeben . Im Dialogfeld Freigeben können Sie eine Vorschau der Assets anzeigen, bei Bedarf entfernen, einen Titel und eine Beschreibung hinzufügen, auswählen, wer auf den Link (privat oder öffentlich) zugreifen kann, einen Ablaufzeitraum festlegen und dann auf Link abrufen klicken, um die freigabefähige URL zu generieren und zu kopieren. Der Link kann dann an Team-Mitglieder oder Stakeholder gesendet werden.

### Welche Zugriffsoptionen stehen beim Freigeben von Assets in AEM Assets Content Hub zur Verfügung und worin unterscheiden sie sich?

Content Hub ermöglicht die Auswahl von zwei Zugriffsoptionen für freigegebene Links: Privat und Öffentlich. Für private Links müssen sich Empfangende bei ihrer Content Hub-Umgebung anmelden, um Assets anzuzeigen und herunterzuladen und so zusätzliche Sicherheit zu bieten. Öffentliche Links können von jedem über den Link aufgerufen werden, ohne dass eine Anmeldung erforderlich ist. Jeder Link-Typ verfügt über seine eigenen Ablaufeinstellungen, z. B. 24 Stunden bis zu einer Woche für öffentliche Links und benutzerdefinierte Datumsangaben für private Links.

### Gibt es Konfigurationen, die vom Administrator verwaltet werden, um öffentliche Links für Assets in AEM Assets Content Hub generieren zu können?

Ja, Administratoren können den Umschalter **Öffentlichen Link aktivieren** auf der Registerkarte **Sammlungen und Freigabe** der Konfigurations-Benutzeroberfläche aktivieren oder deaktivieren, um die Erstellung öffentlicher Links für Assets in AEM Assets Content Hub zu verwalten.

### Kann ich in AEM Assets Content Hub Ablaufdaten für freigegebene Asset-Links festlegen und warum ist dies wichtig?

Ja, Sie können in AEM Assets Content Hub Ablaufdaten für private und öffentliche freigegebene Links festlegen. Bei öffentlichen Links können Sie aus Vorgaben wie 24 Stunden bis zu einer Woche auswählen, während Sie mit privaten Links aus Vorgaben auswählen oder ein benutzerdefiniertes Ablaufdatum festlegen können. Ablaufdaten sind wichtig, da der Link nach Ablauf nicht mehr zum Zugreifen auf oder Herunterladen der Assets verwendet werden kann, was die Sicherheit und Kontrolle Ihres Inhalts unterstützt.

### Was können Empfänger mit dem freigegebenen Asset-Link tun, der mit AEM Assets Content Hub erstellt wurde, und gibt es Optionen zum Herunterladen verschiedener Ausgabedarstellungen?

Empfänger, die einen freigegebenen Asset-Link erhalten, können diesen in ihrem Browser öffnen, um die bereitgestellten Assets in der Vorschau anzuzeigen, auszuwählen und herunterzuladen. Wenn Asset-Ausgabedarstellungen in AEM Assets Content Hub aktiviert sind, können Empfängerinnen und Empfänger auswählen, welche Ausgabedarstellungen (z. B. original oder statisch) sie herunterladen möchten. Die Assets und Ausgabedarstellungen werden als ZIP-Datei heruntergeladen, und die Metadaten können durch Klicken auf die Miniaturansicht des Assets angezeigt werden. Der Link bleibt bis zum festgelegten Ablaufdatum funktionsfähig.




