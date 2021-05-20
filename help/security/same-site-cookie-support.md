---
title: Selbe Site-Cookie-Unterstützung für Adobe Experience Manager as a Cloud Service
description: Selbe Site-Cookie-Unterstützung für Adobe Experience Manager as a Cloud Service
exl-id: 2cec7202-4450-456f-8e62-b7ed3791505c
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%

---

# Selbe Site-Cookie-Unterstützung für Adobe Experience Manager as a Cloud Service {#same-site-cookie-support-for-adobe-experience-manager-as-a-cloud-service}

Seit Version 80 hat Chrome und Safari ein neues Modell für die Cookie-Sicherheit eingeführt. Dieser Modus wurde entwickelt, um Sicherheitskontrollen für die Verfügbarkeit von Cookies auf Drittanbieter-Sites durch eine Einstellung namens `SameSite` einzuführen. Weitere Informationen finden Sie in diesem [Artikel](https://web.dev/samesite-cookies-explained/).

Der Standardwert dieser Einstellung (`SameSite=Lax`) kann dazu führen, dass die Authentifizierung zwischen AEM Instanzen oder Diensten nicht funktioniert. Dies liegt daran, dass die Domänen oder URL-Strukturen dieser Dienste möglicherweise nicht unter die Beschränkungen dieser Cookie-Richtlinie fallen.

Um dies zu umgehen, müssen Sie das SameSite-Cookie-Attribut für das Anmelde-Token auf `None` setzen.

Gehen Sie dazu wie folgt vor:

1. Lokales Installieren einer Version des AEM SDK-Schnellstarts
1. Wechseln Sie zur Web-Konsole unter `http://serveraddress:serverport/system/console/configMgr` .
1. Suchen Sie nach **Adobe Granite Token Authentication Handler** und klicken Sie darauf
1. Setzen Sie das Attribut **SameSite für das Anmelde-Token-Cookie** auf `None`, wie in der Abbildung unten dargestellt
   ![samesite](/help/security/assets/samesite1.png)
1. Klicken Sie auf „Speichern“.
1. Generieren Sie die JSON-Formatkonfigurationen für diese Einstellung, indem Sie die unter [Generieren von OSGi-Konfigurationen mit dem AEM SDK Quickstart](/help/implementing/deploying/configuring-osgi.md#generating-osgi-configurations-using-the-aem-sdk-quickstart) beschriebenen Schritte ausführen.
1. Wenden Sie die Einstellungen an, indem Sie die Schritte in der OSGi-Dokumentation [Cloud Manager-API-Format für das Festlegen von Eigenschaften](/help/implementing/deploying/configuring-osgi.md#cloud-manager-api-format-for-setting-properties) ausführen.

Sobald diese Einstellung aktualisiert und Benutzer abgemeldet und erneut angemeldet sind, wird für `login-token` -Cookies das `None` -Attribut festgelegt und in Site-übergreifende Anforderungen aufgenommen.
