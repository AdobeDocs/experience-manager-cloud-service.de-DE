---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 704f4e250975d8c0cbcfdc5e49b9c03d3a3e2939
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 62%

---

# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 12790 {#release-12790}

Nachfolgend sind die kontinuierlichen Verbesserungen für das Maintenance Release 12790 zusammengefasst, das am 21. Juli 2023 veröffentlicht wurde. Diese Wartungsversion ist eine Aktualisierung der vorherigen Wartungsversion 12697.

2023.7.0 Die Funktionsaktivierung stellt den vollständigen Funktionsumfang für dieses Maintenance Release bereit. Siehe [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=de) für weitere Informationen.

### Verbesserungen {#enhancements-12790}

Keine

### Behobene Probleme {#fixed-issues-112790}

- SLING-11974 - Regression in SlingHttpServletRequest#getUserPrincipal für nicht authentifizierte Anforderungen korrigiert. Die Korrektur stellt sicher, dass ein Prinzipal auch für nicht authentifizierte Anforderungen zurückgegeben wird.

### Bekannte Probleme {#known-issues-12790}

- GRANITE-46601 - Schnellstart-SDK startet nicht ohne JDK 11.0.20 `-Djdk.util.zip.disableZip64ExtraFieldValidation=true` Java-Option

### Eingebettete Technologien {#embedded-tech-12790}

| Technologie | Version | Link |
|---|---|---|
| AEM OAK | 1.52-T20230629133256-25c01b8 | [Oak-API 1.52.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.52.0/index.html) |
| AEM SLING-API | Version: 2.27.2 | [Apache Sling-API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version: 1.4.20-1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | Version: 2.23.0 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
