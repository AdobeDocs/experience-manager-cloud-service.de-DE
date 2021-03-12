---
title: Selbe Site-Cookie-Unterstützung für Adobe Experience Manager als Cloud Service
description: Selbe Site-Cookie-Unterstützung für Adobe Experience Manager als Cloud Service
translation-type: tm+mt
source-git-commit: e51d9c3e4691fb58f3c4b6a2565cc8cad2a1acb0
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---


# Selbe Site-Cookie-Unterstützung für Adobe Experience Manager als Cloud Service {#same-site-cookie-support-for-adobe-experience-manager-as-a-cloud-service}

Seit Version 80 haben Chrome und Safari ein neues Modell für die Sicherheit von Cookies eingeführt. Dieser Modus ist so konzipiert, dass Sicherheitskontrollen zur Verfügbarkeit von Cookies für Drittanbieter-Sites eingeführt werden, indem die Einstellung `SameSite` festgelegt wird. Weitere Informationen finden Sie in diesem [Artikel](https://web.dev/samesite-cookies-explained/).

Der Standardwert dieser Einstellung (`SameSite=Lax`) kann dazu führen, dass die Authentifizierung zwischen AEM Instanzen oder Diensten nicht funktioniert. Dies liegt daran, dass die Domänen oder URL-Strukturen dieser Dienste möglicherweise nicht unter die Beschränkungen dieser Cookie-Richtlinie fallen.

Um dies zu umgehen, müssen Sie für das Login-Token das Attribut SameSite-Cookie auf `None` setzen.

Gehen Sie dazu wie folgt vor:

1. Installieren Sie eine Version des AEM SDK QuickStart lokal
1. Gehen Sie zur Web-Konsole unter `http://serveraddress:serverport/system/console/configMgr`
1. Suchen Sie nach dem **Adobe Granite Token Authentication Handler** und klicken Sie darauf
1. Setzen Sie das Attribut **SameSite für das Cookie login-token** auf `None`, wie in der Abbildung unten dargestellt
   ![samesite](/help/security/assets/samesite1.png)
1. Klicken Sie auf „Speichern“.
1. Generieren Sie die JSON-Formatkonfigurationen für diese bestimmte Einstellung, indem Sie die unter [OSGi-Konfigurationen mit dem AEM SDK Quickstart](/help/implementing/deploying/configuring-osgi.md#generating-osgi-configurations-using-the-aem-sdk-quickstart) beschriebenen Schritte ausführen.
1. Wenden Sie die Einstellungen an, indem Sie die Schritte in der Dokumentation [Cloud Manager-API-Format für das Festlegen von Eigenschaften](/help/implementing/deploying/configuring-osgi.md#cloud-manager-api-format-for-setting-properties) OSGi befolgen.
