---
title: Same-Site-Cookie-Unterstützung für Adobe Experience Manager as a Cloud Service
description: Same-Site-Cookie-Unterstützung für Adobe Experience Manager as a Cloud Service.
exl-id: 2cec7202-4450-456f-8e62-b7ed3791505c
feature: Security
role: Admin
source-git-commit: 85cef99dc7a8d762d12fd6e1c9bc2aeb3f8c1312
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 100%

---

# Same-Site-Cookie-Unterstützung für Adobe Experience Manager as a Cloud Service {#same-site-cookie-support-for-adobe-experience-manager-as-a-cloud-service}

Seit Version 80 ist in Chrome und Safari ein neues Modell für die Sicherheit von Cookies enthalten. Dieser Modus führt mittels der Einstellung `SameSite` Sicherheitskontrollen für Cookies auf Drittanbieter-Sites ein. Weitere Informationen finden Sie unter [web.dev – SameSite-Cookies erklärt](https://web.dev/articles/samesite-cookies-explained?hl=de).

Der Standardwert dieser Einstellung (`SameSite=Lax`) kann dazu führen, dass die Authentifizierung zwischen AEM-Instanzen oder -Services nicht funktioniert. Dies liegt daran, dass die Domains oder URL-Strukturen dieser Services möglicherweise nicht unter die Beschränkungen dieser Cookie-Richtlinie fallen.

Um dies zu umgehen, setzen Sie das SameSite-Cookie-Attribut für das Login-Token auf `None`.

>[!CAUTION]
>
>Die Einstellung `SameSite=None` wird nur angewendet, wenn das Protokoll sicher ist (HTTPS).
>
>Wenn das Protokoll nicht sicher ist (HTTP), wird die Einstellung ignoriert und der Server zeigt die folgende Warnmeldung an:
>
>`WARN com.day.crx.security.token.TokenCookie Skip 'SameSite=None'`

Sie können die Einstellung hinzufügen, indem Sie die folgenden Schritte ausführen:

1. Installieren Sie lokal eine Version des AEM SDK-QuickStart.
1. Wechseln Sie zur Web-Konsole unter `http://serveraddress:serverport/system/console/configMgr`
1. Suchen Sie nach dem **Adobe Granite Token Authentication Handler** und klicken Sie darauf.
1. Legen Sie das **SameSite-Attribut für das Cookie des Anmelde-Tokens** auf `None` fest, wie in der Abbildung unten dargestellt.
   ![samesite](/help/security/assets/samesite1.png)
1. Klicken Sie auf „Speichern“.
1. Generieren Sie die JSON-Formatkonfigurationen für diese bestimmte Einstellung, indem Sie die unter [Generieren von OSGi-Konfigurationen mit dem AEM SDK-QuickStart](/help/implementing/deploying/configuring-osgi.md#generating-osgi-configurations-using-the-aem-sdk-quickstart) beschriebenen Schritte ausführen.
1. Wenden Sie die Einstellungen an, indem Sie die in der OSGI-Dokumentation [Cloud Manager-API-Format für das Festlegen von Eigenschaften](/help/implementing/deploying/configuring-osgi.md#cloud-manager-api-format-for-setting-properties) beschriebenen Schritte ausführen.

Nachdem diese Einstellung aktualisiert wurde und die Benutzenden ab- und wieder angemeldet wurden, haben `login-token`-Cookies das Attribut `None` und werden in seitenübergreifende Anfragen einbezogen.
