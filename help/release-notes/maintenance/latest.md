---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 241dcc75e9f2c840be85c34800d8145457baa58d
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 43%

---

# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 12697 {#release-12697}

Nachfolgend sind die kontinuierlichen Verbesserungen für das Maintenance Release 12697 zusammengefasst, das am 14. Juli 2023 veröffentlicht wurde. Diese Wartungsversion ist eine Aktualisierung der vorherigen Wartungsversion 12549. Das Maintenance Release 12697 ersetzt 12585, um ein Problem zu beheben.

2023.7.0 Die Funktionsaktivierung stellt den vollständigen Funktionsumfang für dieses Maintenance Release bereit. Siehe [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=de) für weitere Informationen.

### Verbesserungen {#enhancements-12697}

- Allgemeine Verbesserungen der RDE-Stabilität (SKYOPS-61133, SKYOPS-55281, SKYOPS-61216 und SKYOPS-61401)
- DXML-12327: AEM: Unterstützung für Sprachvariablen in nativen PDF-Veröffentlichungen
- DXML-11518: AEM: Verbesserte Metadatenunterstützung beim nativen PDF-Publishing
- DXML-10093: AEM: Unterstützung für das Herstellen einer Verbindung zu externen Datenquellen und das Einfügen von Daten in Datenthemen
- DXML-10699: AEM: Unterstützung des XLIFF-Formats bei der Übersetzung
- DXML-10141: AEM: Option zur Verwendung der mikrodienstbasierten Veröffentlichung für PDF (Native und DITA-OT), HTML und benutzerdefinierte Vorgabetypen
- SKYOPS-61385 - Dispatcher so aktualisieren, dass bei der Auswertung von regulären Ausdrücken in Apache HTTPD libpcre2 verwendet wird

### Behobene Probleme {#fixed-issues-12697}

- AEM: Verschiedene Verbesserungen und Stabilisierungskorrekturen für native PDF
- SKYOPS-53130: Verbessern der Unterstützung des AC-Tools in RDE
- SKYOPS-57146: Sling-Deadlock beim Start AEM

### Bekannte Probleme {#known-issues-12697}

Keine

### Eingebettete Technologien {#embedded-tech-12697}

| Technologie | Version | Link |
|---|---|---|
| AEM OAK | 1.52-T20230629133256-25c01b8 | [Oak-API 1.52.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.52.0/index.html) |
| AEM SLING-API | Version: 2.27.2 | [Apache Sling-API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version: 1.4.20-1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | Version: 2.23.0 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
