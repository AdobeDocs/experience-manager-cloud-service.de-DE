---
title: Freigeben von Assets in [!DNL the Content Hub]
description: Freigeben von Assets in [!DNL the Content Hub]
role: User
exl-id: 5284d229-1596-40bf-aa5f-af4b6500ebdf
source-git-commit: 0e66b355d09e2fd2c4c8a5ddacc9b2d033b41bf2
workflow-type: ht
source-wordcount: '486'
ht-degree: 100%

---

# Freigeben von Assets im Content Hub {#search-assets-as-a-link}

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

![Bannerbild zum Freigeben von Assets](assets/share-assets-banner.png)

>[!AVAILABILITY]
>
>Das Content Hub-Handbuch ist jetzt im PDF-Format verfügbar. Laden Sie das gesamte Handbuch herunter und verwenden Sie den KI-Assistenten von Adobe Acrobat, um Ihre Fragen zu beantworten.
>
>[!BADGE Content Hub-Handbuch als PDF]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/content-hub.pdf"}

Erstellen Sie einen Link zu ausgewählten Assets, um sie einfach für andere freizugeben. Wählen Sie als autorisierte Benutzerin bzw. autorisierter Benutzer von [!DNL Content Hub] ein oder mehrere Assets aus, die in Ihrer [!DNL Content Hub]-Umgebung verfügbar sind, generieren Sie einen Link und senden Sie diesen an andere private oder öffentliche Benutzende.

## Voraussetzungen {#prerequisites}

[Content Hub-Benutzende](deploy-content-hub.md#onboard-content-hub-users) können einen Link zu ausgewählten Assets erstellen und ihn für andere Benutzende freigeben.

## Freigeben von Assets {#share-assets}

Um ein oder mehrere Assets für private oder öffentliche Benutzende freizugeben, führen Sie die folgenden Schritte aus:
1. Navigieren Sie zu Ihrer [!DNL Content Hub]-Homepage, wählen Sie ein oder mehrere Assets aus und klicken Sie auf ![Freigeben](/help/assets/assets/share.svg) **[!UICONTROL Freigeben]**, um ein einzelnes ausgewähltes Asset oder eine Liste mit mehreren ausgewählten Assets im Dialogfeld **[!UICONTROL Assets freigeben]** anzuzeigen.
Sie können auch Assets auswählen und freigeben, die in ![Sammlungen](/help/assets/assets/Smock_Collection_18_N.svg) **[!UICONTROL Sammlungen]** verfügbar sind.
1. Zeigen Sie ein Asset an oder überprüfen Sie im Dialogfeld **[!UICONTROL Assets freigeben]** die Liste der verfügbaren Assets. Klicken Sie auf ![Auswahl aufheben](/help/assets/assets/Close.svg) neben einem Asset, um dessen Auswahl aus der Liste aufzuheben.
1. Wählen Sie **[!UICONTROL Gültigkeitszeitraum]** aus und klicken Sie auf **[!UICONTROL Privaten Link erstellen]**, um einen Link zur Freigabe für private Benutzende zu generieren. Private Benutzende melden sich bei ihrer [!DNL Content Hub]-Umgebung an, um auf die Seite mit den freigegebenen Assets zuzugreifen.
   ![Privater und öffentlicher Link](/help/assets/assets/private-and-public-link.png)
Aktivieren Sie den Umschalter **[!UICONTROL Öffentlicher Link]**, wählen Sie einen **[!UICONTROL Gültigkeitszeitraum]** und klicken Sie auf **[!UICONTROL Öffentlichen Link generieren]**, um einen Link zu generieren, der für öffentliche Benutzende freigegeben werden kann. Öffentliche Benutzende können als Gäste auf die Seite mit freigegebenen Assets zugreifen, ohne sich bei [!DNL Content Hub] anzumelden.
   ![Privater und öffentlicher Link](/help/assets/assets/public-and-private-link.png)

   >[!NOTE]
   > 
   > [Aktivieren Sie die Freigabe öffentlicher Links über die Konfigurationsseite](/help/assets/configure-content-hub-ui-options.md#enable-public-link-sharing), um den Umschalter **[!UICONTROL Öffentlicher Link]** im Dialogfeld **[!UICONTROL Freigeben von Assets]** anzuzeigen.

## Freigeben eines Assets über dessen Vorschauseite {#share-asset-from-preview-page}

Führen Sie die folgenden Schritte aus, um ein Asset bei der Vorschau freizugeben:

1. Navigieren Sie zur [!DNL Content Hub]-Startseite und klicken Sie auf die Miniaturansicht des Assets, um eine Vorschau des Assets zu sehen und die Menüoptionen im rechten Bereich des Dialogfelds anzuzeigen.
1. Wählen Sie ![Freigeben](/help/assets/assets/share.svg) aus, um das Bedienfeld **[!UICONTROL Freigeben]** anzuzeigen.
   ![Freigeben von Assets während der Vorschau](/help/assets/assets/share-assets-from-share-panel.png)
1. Folgen Sie Schritt 3 im Abschnitt [Freigeben von Assets](#share-assets), um den Asset-Link (privat oder öffentlich) über dieses Bedienfeld **[!UICONTROL Freigeben]** zu generieren und freizugeben.

## Zugreifen auf die freigegebenen Assets {#access-shared-assets}

Rufen Sie die Seite mit freigegebenen Assets über den Link auf und führen Sie folgende Schritte aus:

* Wählen Sie mindestens ein Asset aus und klicken Sie auf ![Herunterladen](/help/assets/assets/download-icon.svg) **[!UICONTROL Herunterladen]**, um **[!UICONTROL Original]**, **[!UICONTROL Statisch]** oder beide Ausgabedarstellungen aus den verfügbaren Download-Optionen auszuwählen.
  ![](/help/assets/assets/download-shared-assets.png)
* Klicken Sie auf die Asset-Miniaturansicht, um die Metadaten des Assets anzuzeigen.
* Klicken Sie auf der Seite „Freigegebene Assets“ ([über einen privaten Link aufgerufen](#share-assets)) auf eine Asset-Miniaturansicht und wählen Sie ![Herunterladen](/help/assets/assets/download-icon.svg) aus, um die verfügbaren dynamischen Ausgabedarstellungen des Assets im Bedienfeld **[!UICONTROL Herunterladen]** auszuwählen und anzuzeigen, bevor Sie sie auswählen und herunterladen.
  ![](/help/assets/assets/download-renditions-shared-assets-page.png)





