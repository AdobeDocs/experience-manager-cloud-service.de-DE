---
title: Konfigurieren von Asset-Upload-Beschränkungen
description: Konfigurieren Sie Adobe Experience Manager Assets, um die Art der Assets zu beschränken, die Benutzer basierend auf dem MIME-Typ hochladen können. Dadurch wird verhindert, dass versehentlich unerwünschte und böswillige Dateien hochgeladen werden.
exl-id: 094c31f3-f2e9-4b44-9995-c76fb78ca458
source-git-commit: 472b670623e77957ff9a366359ebef8c6c0604ae
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 3%

---

# Konfigurieren von Asset-Upload-Beschränkungen {#configure-asset-upload-restrictions}

Sie können Adobe Experience Manager Assets so konfigurieren, dass der Typ der Assets, die Benutzer hochladen können, anhand des MIME-Typs eingeschränkt wird.

>[!IMPORTANT]
>
>Experience Manager Assets ermöglicht es Benutzern standardmäßig, Assets aller MIME-Typen hochzuladen. Sie können die Einstellungen jedoch so konfigurieren, dass Benutzer nur auf das Hochladen von Dateien bestimmter MIME-Typen beschränkt sind.

## Voraussetzungen {#prerequisites-asset-upload-restrictions}

Sie müssen über Administratorberechtigungen verfügen, um Asset-Upload-Beschränkungen zu konfigurieren.

## Anwenden von Einschränkungen für Asset-Uploads {#apply-restrictions-asset-uploadsssssss}

So konfigurieren Sie [!DNL Experience Manager] , um Benutzer auf das Hochladen von Dateien bestimmter MIME-Typen zu beschränken:

1. Gehen Sie zu **[!UICONTROL Tools > Assets > Assets-Konfigurationen]**.

1. Klicken **[!UICONTROL Upload-Einschränkungen]**.

1. Klicken **[!UICONTROL Hinzufügen]** , um die zulässigen MIME-Typen zu definieren.

1. Geben Sie den MIME-Typ im Textfeld an. Sie können auf **[!UICONTROL Hinzufügen]** um weitere zulässige MIME-Typen anzugeben. Sie können auch auf ![Löschsymbol](assets/delete-icon.svg) um einen beliebigen MIME-Typ aus der Liste zu löschen.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

**Beispiel 1: Hochladen aller Bilder und PDF-Dateien in Experience Manager Assets zulassen**

Gehen Sie wie folgt vor, um das Hochladen von Bildern in allen Formaten und PDF-Dateien in Experience Manager Assets zu ermöglichen:

![Einschränkungen beim Asset-Upload](assets/asset-upload-restrictions.png)

`image/*` da der MIME-Typ das Hochladen von Bildern in allen Formaten ermöglicht. `application/pdf` da der MIME-Typ das Hochladen von PDF-Dateien in Experience Manager Assets ermöglicht.

**Beispiel 2: Hochladen bestimmter Bildformate in Experience Manager Assets zulassen**

Gehen Sie wie folgt vor, um den zulässigen MIME-Typen bestimmte Bildformate hinzuzufügen und das Hochladen aller anderen Asset-Formate zu beschränken:

![Asset-Einschränkungen](assets/asset-restrictions.png)

Basierend auf den im Bild dargestellten Einstellungen können Sie Bilder in den Formaten .JPG, .PNG und .GIF in Experience Manager Assets hochladen.
