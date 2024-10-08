---
title: Asset-Selektor für [!DNL Adobe Experience Manager] als ein [!DNL Cloud Service]
description: Verwenden Sie die Asset-Auswahl, um die Metadaten und Ausgabeformate von Assets in Ihrer Anwendung zu suchen, zu suchen und abzurufen.
role: Admin,User
exl-id: d6ff601c-3111-421a-9a94-cc524ce7e432
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 1%

---

# Hochladen von Dateien und Ordnern in die Asset-Auswahl {#upload-files-folders}

| [Best Practices für die Suche](/help/assets/search-best-practices.md) | [Best Practices für Metadaten](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [Dynamic Media mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md) | [AEM Assets-Entwicklerdokumentation](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

Sie können Dateien oder Ordner aus Ihrem lokalen Dateisystem in die Asset-Auswahl hochladen. Um Dateien mit dem lokalen Dateisystem hochzuladen, müssen Sie im Allgemeinen eine Upload-Funktion verwenden, die von einer Asset-Auswahl-Mikro-Frontend-Anwendung bereitgestellt wird.

## Hochladen von Assets aus dem lokalen Dateisystem {#basic-upload}

Um Assets zur Asset-Auswahl hinzuzufügen, führen Sie die folgenden Schritte aus:

1. Wenn Sie die Schienenansicht verwenden, wechseln Sie zu den Auslassungspunkten und klicken Sie auf das Symbol ![Hochladen](assets/upload-icon.svg) **[!UICONTROL Hochladen]**. Klicken Sie auf der anderen Seite oben rechts im Fall einer modalen Ansicht auf das Symbol ![Hochladen](assets/upload-icon.svg) **[!UICONTROL Hochladen]** . Der Bildschirm [!UICONTROL Assets hochladen] wird angezeigt.

   ![Hochladen von Assets in die Asset-Auswahl](assets/upload-assets.png)

   Darüber hinaus können Sie im Abschnitt &quot;**[!UICONTROL Dateien oder Ordner hierher ziehen]**&quot;die Assets entweder aus dem lokalen Dateisystem ziehen oder auf &quot;**[!UICONTROL Durchsuchen]**&quot; klicken, um die im lokalen Dateisystem verfügbaren Dateien oder Ordner manuell auszuwählen. Diese Liste der Dateien, die Teil Ihres Uploads sind, ist als Liste verfügbar.

   ![Einfache Upload von Assets in die Asset-Auswahl](assets/basic-upload.png)

   Sie können auch mithilfe der Miniaturansichten eine Vorschau ausgewählter Bilder anzeigen und auf das X-Symbol klicken, um ein bestimmtes Bild aus der Liste zu entfernen. Das X-Symbol wird nur angezeigt, wenn Sie den Mauszeiger über den Bildnamen oder die Bildgröße bewegen. Sie können auch auf **[!UICONTROL Alle entfernen]** klicken, um alle Elemente aus Ihrer Upload-Liste zu löschen.

1. Um den Upload-Prozess abzuschließen, klicken Sie auf **[!UICONTROL Hochladen]**. Ihre hochgeladenen Assets werden angezeigt. Siehe [Grundlegender Upload](/help/assets/asset-selector-customization.md#basic-upload) für den konfigurierbaren Code.

## Hochladen von Assets mit Metadaten {#upload-assets-with-metadata}

Sie können den Assets Metadaten hinzufügen, während Sie sie sofort in Ihre Anwendung hochladen. Metadaten umfassen verschiedene Felder wie Geschäftsbetreffzeile, Produktdetails, Kampagne usw. Dazu wird die Eigenschaft `metadataSchema` verwendet. Wechseln Sie zu [Eigenschaften des Asset-Wählers](/help/assets/asset-selector-properties.md) , um mehr über die Eigenschaft `metadataSchema` zu erfahren.

Siehe [Upload mit Metadaten](/help/assets/asset-selector-customization.md#upload-with-metadata) für das für die Konfiguration erforderliche Codefragment.

![ Hochladen von Assets mit Metadaten](assets/upload-with-metadata.png)

1. Definieren Sie den Namen für Ihren Upload mithilfe des Felds **[!UICONTROL Kampagnenname]** . Sie können einen vorhandenen Namen verwenden oder einen neuen erstellen. Der Asset-Selektor bietet beim Eingeben des Namens weitere Optionen.

   Als Best Practice empfiehlt Adobe, Werte im Rest der Felder anzugeben und eine erweiterte Sucherfahrung für Ihre hochgeladenen Assets zu erstellen.

1. Definieren Sie auf ähnliche Weise Werte für die Felder **[!UICONTROL Keywords]**, **[!UICONTROL Kanäle]**, **[!UICONTROL Timeframe]** und **[!UICONTROL Region]** . Durch das Tagging und Gruppieren von Assets nach Keywords, Kanälen und Standorten können alle Benutzer, die Ihre genehmigten Unternehmensinhalte verwenden, diese Assets suchen und organisieren.

1. Klicken Sie auf **[!UICONTROL Hochladen]** , um Assets in die Asset-Auswahl hochzuladen. [!UICONTROL Überprüfungsdetails] wird das Bestätigungsfeld angezeigt. Klicken Sie auf [!UICONTROL Weiter].

1. Assets beginnt mit dem Hochladen. Klicken Sie auf [!UICONTROL Neu hochladen] , um den Upload-Vorgang neu zu starten. Klicken Sie auf [!UICONTROL Fertig] , um den Upload abzuschließen.


## Benutzerdefinierter Upload {#customize-upload}

Mit der Asset-Auswahl können Sie ein benutzerdefiniertes Upload-Formular hinzufügen. Es stehen verschiedene Anpassungen zur Verfügung. Beispielsweise können Sie mit der Eigenschaft [hideUploadButton](/help/assets/asset-selector-properties.md) die Upload-Schaltfläche ausblenden, die standardmäßig in der Anwendung angezeigt wird. Stattdessen können Sie es so anpassen, dass es gemäß den Anforderungen außerhalb der MFE-Anwendung gerendert wird. Siehe [angepasster Upload](/help/assets/asset-selector-customization.md#customized-upload) für die Konfiguration.

![ Benutzerdefinierter Upload](assets/customized-upload.png)

>[!MORELIKETHIS]
>
>* [Beispiele für die Asset-Auswahl](/help/assets/asset-selector-examples.md)
>* [Integrieren der Asset-Auswahl in verschiedene Anwendungen](/help/assets/integrate-asset-selector.md)
>* [Eigenschaften des Asset-Wählers](/help/assets/asset-selector-properties.md)
