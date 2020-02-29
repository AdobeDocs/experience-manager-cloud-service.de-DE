---
title: Konfigurieren von Einschränkungen beim Hochladen von Assets
description: Erfahren Sie mehr darüber, wie Sie Adobe Experience Manager (AEM) Assets so konfigurieren können, dass der von den Benutzern hochladbare Typ von Assets (Dateien) eingeschränkt ist.
contentOwner: AG
translation-type: tm+mt
source-git-commit: f2e257ff880ca2009c3ad6c8aadd055f28309289

---


# Konfigurieren von Einschränkungen beim Hochladen von Assets {#configuring-asset-upload-restrictions}

Sie können Adobe Experience Manager (AEM) Assets so konfigurieren, dass der von den Benutzern hochladbare Typ von Assets (Dateien) eingeschränkt ist. Mit dieser Funktion können Sie verhindern, dass Benutzer Assets in einem unerwünschten Format oder schädliche Dateien hochladen. The `Day CQ DAM Asset Upload Restriction` service enables you to control the type of files that users can upload. Standardmäßig lässt es AEM Assets zu, dass Benutzer Assets aller MIME-Typen hochladen. Sie können jedoch den Dienst so konfigurieren, dass Benutzer auf den Upload von Dateien bestimmter MIME-Typen beschränkt werden.

1. Öffnen Sie die Configuration Manager-Webkonsole. Zugriff `https://[aem_server]:[port]/system/console/configMgr`.
1. Open the **[!UICONTROL Day CQ DAM Asset Upload Restriction]** service in Edit mode. By default, the **Allow all MIME** option is selected, which allows users to upload files of all MIME types.

   ![chlimage_1-378](assets/chlimage_1-378.png)

1. Um zu beschränken, dass Benutzer nur Dateien mit bestimmten MIME-Typen hochladen können, heben Sie die Auswahl der Option **[!UICONTROL Alle MIME zulassen]** auf und geben Sie in den Feldern **[!UICONTROL Zulässige Asset-MIMEs (regex)]** zulässige MIME-Typen mit regulären Ausdrücken an.

   ![chlimage_1-379](assets/chlimage_1-379.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern. Wenn Sie MIME-Zeichenfolgen für zulässige MIME-Typen angeben, schlägt der Uploadvorgang bei allen Assets mit MIME-Typ fehl, die nicht mit den konfigurierten MIME-Zeichenfolgen in diesen Feldern übereinstimmen.
