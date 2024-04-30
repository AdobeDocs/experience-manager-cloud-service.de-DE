---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 60952db4172b882b71a0b230fc8f4c27154e9cc0
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 72%

---

# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 15977 {#release-15977}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 15977, die am 19. April 2024 veröffentlicht wurde. Die vorherige Wartungsversion war Version 15939.

2024.4.0: Die Funktionsaktivierung bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-15977}

* GRANITE-51335: Optimieren der AEM-Konsistenzprüfung zum Erhöhen der Instanzstabilität.

### Behobene Probleme {#fixed-issues-15977}

* CQ-4357226: Behebung der Regression in der Unterstützung der IMS-Konfiguration für OAuth-Anmeldeinformationen.
* GRANITE-51335: Ratenbegrenzungs-Upgrade auf 5.0.4 behebt Registrierungen für die Felix-Konsistenzprüfung.

### Bekannte Probleme {#known-issues-15977}

* **(Nur für AEM Forms)** Nach der Installation von AEM Cloud Foundation Maintenance Release 15977 werden die Felder des adaptiven Formulars beim Erstellen von Formularen und für veröffentlichte Formulare in der falschen Reihenfolge angezeigt. Wenn Sie AEM Forms verwenden, empfiehlt Adobe, kein Upgrade auf die Version 15977 durchzuführen, bis das Problem in der bevorstehenden Wartungsversion behoben ist. Auf diese Weise können Sie Unannehmlichkeiten vermeiden.

### Eingestellte Funktionen und APIs {#deprecated-15977}

* [Einstellung der JWT-Anmeldedaten in Adobe Developer Console](/help/security/jwt-credentials-deprecation-in-adobe-developer-console.md)

* Ab dem Donnerstag, 1. Mai 2024 wird Adobe Dynamic Media die Unterstützung für Folgendes einstellen:

   * SSL (Secure Socket Layer) 2.0
   * SSL 3.0
   * TLS (Transport Layer Security) 1.0 und 1.1
   * Die folgenden schwachen Verschlüsselungsverfahren in TLS 1.2:
      * `TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384`
      * `TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA`
      * `TLS_RSA_WITH_AES_256_GCM_SHA384`
      * `TLS_RSA_WITH_AES_256_CBC_SHA256`
      * `TLS_RSA_WITH_AES_256_CBC_SHA`
      * `TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256`
      * `TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA`
      * `TLS_RSA_WITH_AES_128_GCM_SHA256`
      * `TLS_RSA_WITH_AES_128_CBC_SHA256`
      * `TLS_RSA_WITH_AES_128_CBC_SHA`
      * `TLS_RSA_WITH_CAMELLIA_256_CBC_SHA`
      * `TLS_RSA_WITH_CAMELLIA_128_CBC_SHA`
      * `TLS_ECDHE_RSA_WITH_3DES_EDE_CBC_SHA`
      * `TLS_RSA_WITH_SDES_EDE_CBC_SHA`


Informationen zu veralteten oder entfernten Elementen in AEM as a Cloud Service finden Sie unter [Eingestellte und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md).

### Eingebettete Technologien {#embedded-tech-15977}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1.62.0 | [Oak-API 1.62.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.62.0/index.html) |
| AEM SLING-API | 2.27.2 | [Apache Sling-API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.20–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | 2.24.6 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
