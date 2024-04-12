---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 1dd2eae9201c86d2cdac78ff99634eff8ca57a05
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 94%

---

# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 15860 {#release-15860}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 15860, die am Donnerstag, 10. April 2024 veröffentlicht wurde. Die vorherige Wartungsversion war Version 15787.

2024.3.0: Die Funktionsaktivierung bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=de).

### Verbesserungen {#enhancements-15860}

Keine

### Behobene Probleme {#fixed-issues-15860}

* Korrekturen der Regression zur Anzeige der Konsole &quot;Launches&quot;, wenn ein Launch auf eine gelöschte oder verschobene Seite verweist.

### Bekannte Probleme {#known-issues-15860}

Keine

### Eingestellte Funktionen und APIs {#deprecated-15860}

* [Einstellung der JWT-Anmeldedaten in Adobe Developer Console](/help/security/jwt-credentials-deprecation-in-adobe-developer-console.md)

Lesen Sie unter [Eingestellte und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) nach, um zu erfahren, welche Funktionen und APIs in AEM as a Cloud Service eingestellt oder entfernt wurden.

### Änderungshinweis {#change-notice-15860}

**Erforderliche Aktionen**

#### Festlegen der CM-Java-Version auf 11 {#set-java-version-11}

Die neue aem-sdk-api-Version enthält Klassen, die mit einem Java 11-Ziel kompiliert wurden und nicht mit der standardmäßigen JDK-Version 1.8 der Cloud Manager-Build-Umgebung kompatibel sind. Diese Aktualisierung erfordert, dass Maven mit JDK 11 ausgeführt wird.

Kundinnen und Kunden wird empfohlen, eine `.cloudmanager/java-version`-Datei im Stammverzeichnis ihres Git-Repositorys mit den folgenden Inhalten hinzuzufügen: `11`. Siehe [Build-Umgebung/Festlegen der Maven-JDK-Version](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#alternate-maven-jdk-version).


### Eingebettete Technologien {#embedded-tech-15860}

| Technologie | Version | Link |
|---|---|---|
| AEM OAK | 1.60-T20240131102219-0cde853 | [Oak API 1.60.0-API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.60.0/index.html) |
| AEM SLING-API | Version: 2.27.2 | [Apache Sling-API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version: 1.4.20-1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | Version 2.24.4 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
