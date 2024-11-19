---
title: Assets in [!DNL the Content Hub] freigeben
description: Assets in [!DNL the Content Hub] freigeben
role: User
exl-id: 5284d229-1596-40bf-aa5f-af4b6500ebdf
source-git-commit: ed7331647ea2227e6047e42e21444b743ee5ce6d
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 6%

---

# Freigeben von Assets in Content Hub {#search-assets-as-a-link}

| [Best Practices für die Suche](/help/assets/search-best-practices.md) | [Best Practices für Metadaten](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [Dynamic Media mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md) | [Entwicklerdokumentation zu AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

![Asset-Bannerbild freigeben](assets/share-assets-banner.png)

>[!AVAILABILITY]
>
>Das Content Hub-Handbuch ist jetzt im PDF-Format verfügbar. Laden Sie das gesamte Handbuch herunter und verwenden Sie den Adobe Acrobat AI-Assistenten, um Ihre Fragen zu beantworten.
>
>[!BADGE Content Hub Guide PDF]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/content-hub.pdf"}

Die Freigabe von Assets über einen Link ist eine praktische Methode, um die Ressourcen für [!DNL the Content Hub] -Benutzer verfügbar zu machen. Mit der Funktion können autorisierte Benutzer auf die Assets zugreifen und diese herunterladen, die für sie freigegeben sind. Beim Herunterladen von Assets über einen freigegebenen Link verwendet [!DNL the Content Hub] einen asynchronen Dienst, der einen schnelleren und unterbrechungsfreien Download bietet.

## Voraussetzungen {#prerequisites}

[Content Hub-Benutzer](deploy-content-hub.md#onboard-content-hub-users) können die in diesem Artikel erwähnten Aktionen ausführen.

## Freigeben eines einzelnen Assets {#share-a-single-asset}

Sie können ein einzelnes Asset freigeben, indem Sie die folgenden Schritte ausführen:

1. Wählen Sie ein Asset aus und klicken Sie auf das Symbol ![Freigabe-Symbol](assets/share.svg) , um ein Asset freizugeben.

   ![Freigeben eines einzelnen Assets](assets/sharing-single-asset.png)

1. Verwenden Sie das Feld **[!UICONTROL Ablauf]** , um ein Ablaufdatum für den Link anzugeben. Wählen Sie eine der verfügbaren Optionen aus, z. B. 24 Stunden, 1 Woche, 30 Tage, 90 Tage, 1 Jahr oder geben Sie ein benutzerdefiniertes Datum an.

1. Klicken Sie auf **[!UICONTROL Freigabe-Link kopieren]**. Sie können den kopierten Link dann für den Empfänger freigeben.

## Freigeben mehrerer Assets {#share-multiple-assets}

Mit [!DNL The Content Hub] können Sie mehrere Assets über einen freigegebenen Link freigeben. Führen Sie die folgenden Schritte aus:

1. Wählen Sie Assets aus, die Sie für den autorisierten Empfänger freigeben müssen. Sie können mehrere Assets einzeln auswählen oder auf **[!UICONTROL Alle auswählen]** klicken, um alle verfügbaren Assets gleichzeitig auszuwählen. Die Option **[!UICONTROL Alle auswählen]** wird nur angezeigt, wenn Sie mindestens ein Asset auswählen.

1. Klicken Sie auf das Symbol ![Freigabe](assets/share.svg) .

   ![Freigeben mehrerer Assets](assets/sharing-multiple-assets.png)

1. Im Vorschaubereich können Sie Assets auch entsprechend Ihren Anforderungen löschen. Verwenden Sie das Feld **[!UICONTROL Ablauf]** , um ein Ablaufdatum für den Link anzugeben. Wählen Sie eine der verfügbaren Optionen aus, z. B. 24 Stunden, 1 Woche, 30 Tage, 90 Tage, 1 Jahr oder geben Sie ein benutzerdefiniertes Datum an.

1. Klicken Sie auf **[!UICONTROL Freigabe-Link kopieren]**. Sie können den kopierten Link dann für den Empfänger freigeben.

## Vorschau erstellen und Assets freigeben {#preview-assets}

Sie können eine Vorschau anzeigen, um zu sehen, wie ein digitales Asset, das Sie freigeben möchten, aussieht, bevor Sie es mit einem Link-Empfänger teilen. Klicken Sie auf das Asset, das Sie in der Vorschau anzeigen möchten. Der [!DNL Content Hub] zeigt die [Detailansicht für das Asset](asset-properties-content-hub.md) an.

Klicken Sie auf das Symbol ![Freigabe](assets/share.svg) , um ein Asset freizugeben. Verwenden Sie das Feld **[!UICONTROL Ablauf]** , um ein Ablaufdatum für den Link anzugeben. Wählen Sie eine der verfügbaren Optionen aus, z. B. 24 Stunden, 1 Woche, 30 Tage, 90 Tage, 1 Jahr oder geben Sie ein benutzerdefiniertes Datum an. Klicken Sie auf **[!UICONTROL Freigabe-Link kopieren]**. Sie können den kopierten Link dann für den Empfänger freigeben.

![Asset-Vorschau in Content Hub anzeigen](assets/preview-assets-content-hub.png)

## Zugreifen auf die freigegebenen Medienelemente {#access-shared-assets}

Nachdem Sie den Link für Assets freigegeben haben, können die autorisierten Empfänger auf den Link klicken, um die freigegebenen Assets in einem Webbrowser als Vorschau anzuzeigen oder herunterzuladen.

Klicken Sie auf den freigegebenen Link und dann auf das auf der Asset-Karte verfügbare Download-Symbol, um ein Asset herunterzuladen.  Sie können auch mehrere Assets auswählen und auf **[!UICONTROL Download]** <!--You can either download original assets or Original+Renditions of an asset.--> klicken. [!DNL The Content Hub] lädt jedes Asset einzeln in das lokale Dateisystem herunter.

![Auf freigegebene Links zugreifen](assets/content-hub-access-shared-links.png)
