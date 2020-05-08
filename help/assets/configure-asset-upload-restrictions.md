---
title: Konfigurieren von Einschränkungen beim Hochladen von Assets
description: Erfahren Sie mehr darüber, wie Sie Adobe Experience Manager (AEM) Assets so konfigurieren können, dass der von den Benutzern hochladbare Typ von Assets (Dateien) eingeschränkt ist.
contentOwner: AG
translation-type: ht
source-git-commit: f2e257ff880ca2009c3ad6c8aadd055f28309289

---


# Konfigurieren von Einschränkungen beim Hochladen von Assets {#configuring-asset-upload-restrictions}

Sie können Adobe Experience Manager (AEM) Assets so konfigurieren, dass der von den Benutzern hochladbare Typ von Assets (Dateien) eingeschränkt ist. Mit dieser Funktion können Sie verhindern, dass Benutzer Assets in einem unerwünschten Format oder schädliche Dateien hochladen. Der Dienst `Day CQ DAM Asset Upload Restriction` ermöglicht es Ihnen, den Typ von Dateien, die Benutzer hochladen können, zu steuern. Standardmäßig lässt es AEM Assets zu, dass Benutzer Assets aller MIME-Typen hochladen. Sie können jedoch den Dienst so konfigurieren, dass Benutzer auf den Upload von Dateien bestimmter MIME-Typen beschränkt werden.

1. Öffnen Sie die Web-Konsole „Configuration Manager“. Greife Sie auf `https://[aem_server]:[port]/system/console/configMgr` zu.
1. Öffnen Sie den Dienst **[!UICONTROL Day CQ DAM Asset Upload Restriction]** im Bearbeitungsmodus. Standardmäßig ist die Option **Alle MIME-Typen zulassen** aktiviert, sodass Benutzer Dateien aller MIME-Typen hochladen können.

   ![chlimage_1-378](assets/chlimage_1-378.png)

1. Um Benutzer auf den Upload von Dateien bestimmter MIME-Typen zu beschränken, deaktivieren Sie die Option **[!UICONTROL Alle MIME-Typen zulassen]** und legen Sie die zulässigen MIME-Typen mithilfe regulärer Ausdrücke im Feld **[!UICONTROL Zulässige Asset-MIME-Typen (regex)]** an.

   ![chlimage_1-379](assets/chlimage_1-379.png)

1. Klicken oder tippen Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern. Wenn Sie MIME-Zeichenfolgen für zulässige MIME-Typen angeben, schlägt der Upload-Vorgang für alle Assets fehl, deren MIME-Typ nicht den in diesen Feldern konfigurierten MIME-Zeichenfolgen entspricht.
