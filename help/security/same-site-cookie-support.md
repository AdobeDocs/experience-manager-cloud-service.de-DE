---
title: Cookie-Unterstützung für Adobe Experience Manager as a Cloud Service
description: Cookie-Unterstützung für Adobe Experience Manager as a Cloud Service
exl-id: 2cec7202-4450-456f-8e62-b7ed3791505c
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 100%

---

# Cookie-Unterstützung für Adobe Experience Manager as a Cloud Service {#same-site-cookie-support-for-adobe-experience-manager-as-a-cloud-service}

Seit Version 80 ist in Chrome und Safari ein neues Modell für die Sicherheit von Cookies enthalten. Dieser Modus führt mittels der Einstellung `SameSite` Sicherheitskontrollen für Cookies auf Drittanbieter-Sites ein. Weitere Informationen finden Sie in diesem [Artikel](https://web.dev/samesite-cookies-explained/).

Der Standardwert dieser Einstellung (`SameSite=Lax`) kann dazu führen, dass die Authentifizierung zwischen AEM-Instanzen oder -Diensten nicht funktioniert. Dies liegt daran, dass die Domains oder URL-Strukturen dieser Dienste möglicherweise nicht unter die Beschränkungen dieser Cookie-Richtlinie fallen.

Um dies zu umgehen, müssen Sie das SameSite-Cookie-Attribut für das Anmelde-Token auf `None` festlegen.

Gehen Sie dazu wie folgt vor:

1. Installieren Sie lokal eine Version des AEM SDK-QuickStart.
1. Wechseln Sie zur Web-Konsole unter `http://serveraddress:serverport/system/console/configMgr`
1. Suchen Sie nach dem **Adobe Granite Token Authentication Handler** und klicken Sie darauf.
1. Legen Sie das **SameSite-Attribut für das Cookie des Anmelde-Tokens** auf `None` fest, wie in der Abbildung unten dargestellt.
   ![samesite](/help/security/assets/samesite1.png)
1. Klicken Sie auf „Speichern“.
1. Generieren Sie die JSON-Formatkonfigurationen für diese bestimmte Einstellung, indem Sie die unter [Generieren von OSGi-Konfigurationen mit dem AEM SDK-QuickStart](/help/implementing/deploying/configuring-osgi.md#generating-osgi-configurations-using-the-aem-sdk-quickstart) beschriebenen Schritte ausführen.
1. Wenden Sie die Einstellungen an, indem Sie die in der OSGI-Dokumentation [Cloud Manager-API-Format für das Festlegen von Eigenschaften](/help/implementing/deploying/configuring-osgi.md#cloud-manager-api-format-for-setting-properties) beschriebenen Schritte ausführen.

Sobald diese Einstellung aktualisiert wurde und Benutzer sich abgemeldet und erneut angemeldet haben, ist für `login-token`-Cookies das `None`-Attribut festgelegt und sie sind in den Site-übergreifenden Anforderungen enthalten.
