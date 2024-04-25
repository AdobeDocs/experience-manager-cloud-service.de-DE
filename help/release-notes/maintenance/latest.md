---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: b7e7bc7546b836667fff9db0ea5419e751f492cb
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 78%

---

# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 15977 {#release-15977}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 15977, die am 19. April 2024 veröffentlicht wurde. Die vorherige Wartungsversion war Version 15939.

2024.4.0: Die Funktionsaktivierung bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=de).

### Verbesserungen {#enhancements-15977}

* GRANITE-51335: Optimieren der AEM-Konsistenzprüfung zum Erhöhen der Instanzstabilität.

### Behobene Probleme {#fixed-issues-15977}

* CQ-4357226: Behebung der Regression in der Unterstützung der IMS-Konfiguration für OAuth-Anmeldeinformationen.
* GRANITE-51335: Ratenbegrenzungs-Upgrade auf 5.0.4 behebt Registrierungen für die Felix-Konsistenzprüfung.

### Bekannte Probleme {#known-issues-15977}

* **(Nur für AEM Forms)** Nach der Installation von AEM Cloud Foundation Maintenance Release 15977 werden die Felder des adaptiven Formulars beim Erstellen von Formularen und für veröffentlichte Formulare in der falschen Reihenfolge angezeigt. Wenn Sie AEM Forms verwenden, um Unannehmlichkeiten zu vermeiden, wird empfohlen, kein Upgrade auf die Version 15977 durchzuführen, bis das Problem in der bevorstehenden Wartungsversion behoben ist.


### Eingestellte Funktionen und APIs {#deprecated-15977}

* [Einstellung der JWT-Anmeldedaten in Adobe Developer Console](/help/security/jwt-credentials-deprecation-in-adobe-developer-console.md)

Lesen Sie unter [Eingestellte und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) nach, um zu erfahren, welche Funktionen und APIs in AEM as a Cloud Service eingestellt oder entfernt wurden.

### Eingebettete Technologien {#embedded-tech-15977}

| Technologie | Version | Link |
|---|---|---|
| AEM OAK | 1.62.0 | [Oak-API 1.62.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.62.0/index.html) |
| AEM SLING-API | 2.27.2 | [Apache Sling-API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.20–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | 2.24.6 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
