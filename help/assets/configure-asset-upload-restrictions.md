---
title: Konfigurieren von Asset-Upload-Beschränkungen
description: Konfigurieren Sie Adobe Experience Manager Assets, um die Art der Assets zu beschränken, die Benutzende basierend auf dem MIME-Typ hochladen können. Dadurch wird verhindert, dass versehentlich Dateien in unerwünschten Formaten oder böswillige Dateien hochgeladen werden.
exl-id: 094c31f3-f2e9-4b44-9995-c76fb78ca458
feature: Upload, Asset Ingestion
role: User, Admin, Developer
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 100%

---

# Konfigurieren von Asset-Upload-Beschränkungen {#configure-asset-upload-restrictions}

| [Best Practices für die Suche](/help/assets/search-best-practices.md) | [Best Practices für Metadaten](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [Dynamic Media mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md) | [Entwicklerdokumentation zu AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

Sie können Adobe Experience Manager Assets so konfigurieren, dass der Typ der Assets, die Benutzende hochladen können, anhand des MIME-Typs eingeschränkt wird.

>[!IMPORTANT]
>
>Standardmäßig erlaubt Experience Manager Assets Benutzenden das Hochladen von Assets aller MIME-Typen. Sie können die Einstellungen jedoch so konfigurieren, dass Benutzende auf das Hochladen von Dateien bestimmter MIME-Typen beschränkt werden.

## Voraussetzungen {#prerequisites-asset-upload-restrictions}

Sie müssen über Administratorberechtigungen verfügen, um Asset-Upload-Beschränkungen zu konfigurieren.

## Anwenden von Einschränkungen für Asset-Uploads {#apply-restrictions-asset-uploadsssssss}

So konfigurieren Sie [!DNL Experience Manager], sodass Benutzende auf das Hochladen von Dateien bestimmter MIME-Typen beschränkt sind:

1. Gehen Sie zu **[!UICONTROL Tools > Assets > Asset-Konfigurationen]**.

1. Klicken Sie auf **[!UICONTROL Upload-Einschränkungen]**.

1. Klicken Sie auf **[!UICONTROL Hinzufügen]**, um die zulässigen MIME-Typen zu definieren.

1. Geben Sie den MIME-Typ im Textfeld an. Sie können erneut auf **[!UICONTROL Hinzufügen]** klicken, um weitere zulässige MIME-Typen anzugeben. Durch Klicken auf das Symbol ![Löschen](assets/delete-icon.svg) können Sie auch einen beliebigen MIME-Typ aus der Liste löschen.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

**Beispiel 1: Hochladen aller Bilder und PDF-Dateien in Experience Manager Assets zulassen**

Gehen Sie wie folgt vor, um das Hochladen von Bildern in allen Formaten und PDF-Dateien in Experience Manager Assets zuzulassen:

![Einschränkungen beim Hochladen von Assets](assets/asset-upload-restrictions.png)

`image/*` als MIME-Typ lässt das Hochladen von Bildern in allen Formaten zu. `application/pdf` als MIME-Typ lässt das Hochladen von PDF-Dateien in Experience Manager Assets zu.

Wenn Sie versuchen, eine Datei hochzuladen, die nicht in der Liste der zulässigen MIME-Typen enthalten ist, zeigt Experience Manager Assets die folgende Fehlermeldung an:

![Eingeschränkte Dateien](assets/asset-upload-restricted-files.png)

`Screen Recording 2022-08-31 at 3.36.09 PM.mov` bezieht sich auf einen Dateinamen, der nicht in den zulässigen MIME-Typen enthalten ist.

**Beispiel 2: Hochladen bestimmter Bildformate in Experience Manager Assets zulassen**

Gehen Sie wie folgt vor, um den zulässigen MIME-Typen bestimmte Bildformate hinzuzufügen und das Hochladen aller anderen Asset-Formate zu beschränken:

![Asset-Einschränkungen](assets/asset-restrictions.png)

Basierend auf den im Bild dargestellten Einstellungen können Sie Bilder in den Formaten .JPG, .PNG und .GIF in Experience Manager Assets hochladen.

**Siehe auch**

* [Assets übersetzen](translate-assets.md)
* [Assets-HTTP-API](mac-api-assets.md)
* [Von AEM Assets unterstützte Dateiformate](file-format-support.md)
* [Suchen von Assets](search-assets.md)
* [Connected Assets](use-assets-across-connected-assets-instances.md)
* [Asset-Berichte](asset-reports.md)
* [Metadatenschemata](metadata-schemas.md)
* [Herunterladen von Assets](download-assets-from-aem.md)
* [Verwalten von Metadaten](manage-metadata.md)
* [Suchfacetten](search-facets.md)
* [Verwalten von Sammlungen](manage-collections.md)
* [Massenimport von Metadaten](metadata-import-export.md)
* [Veröffentlichen von Assets in AEM und Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)
