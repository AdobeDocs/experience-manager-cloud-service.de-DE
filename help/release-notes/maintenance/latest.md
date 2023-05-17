---
title: Aktuelle Versionshinweise zur Wartung [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise zur Wartung [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 4353f2a9f6cd649a4377adb9891e0873a51d6ab2
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 21%

---

# Wartungsversionshinweise {#maintenance-release-notes}

Im folgenden Abschnitt finden Sie die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 11873 {#release-11873}

Nachfolgend sind die kontinuierlichen Verbesserungen für das Maintenance Release 11873 zusammengefasst, das am 3. Mai 2023 veröffentlicht wurde. Dieses Maintenance Release ist eine Aktualisierung von dem vorherigen Maintenance Release 11835.

Mit der Aktivierung der Funktionen für diese Wartungsversion steht Ihnen der volle Funktionsumfang zur Verfügung. Detaillierte Informationen finden Sie in den [aktuellen Versionshinweisen](/help/release-notes/release-notes-cloud/release-notes-current.md).

### Verbesserungen {#enhancements}

- SITES-1200 - Verbesserungen der Such-API mit tags-basierter Filterung
- GRANITE-42939 - Hinzufügen von veralteten Anmerkungen und Warnungen zum oauth-server-Code

### Bekannte Probleme {#known-issues-11873}

- SITES-13253 - RecursionTooDeepException in Kernkomponenten v2.22.6
- SITES-13256 - WCM-Core-Teaser, der mit einer speziellen URL konfiguriert ist, unterbricht das Seiten-Rendering
- GRANITE-45462 - Konfiguration des Messaging-Clients für mehrere Regionen
- GRANITE-45562 - Probleme mit der Bildkombination, die 200 statt 404 zurückgeben

### Behobene Probleme {#fixed-issues-11873}

- SKYSI-19884/SKYOPS-53745 - Problem mit PublishPageRenderingErrorsHigh behoben
- GRANITE-4388 - Korrektur des Durchsatzabfalls nach einer großen Anzahl von DAM-Asset-Schreibvorgängen auf Mongo
- SITES-11922 - Problem mit dem Rückgängigmachen der Veröffentlichung in der Vorschau behoben, das den Synchronisierungsstatus nicht entfernt hat
- ASSETS-21648 - Berechtigungsproblem mit Asset Relate-Funktionen behoben

### Eingebettete Technologien {#embedded-tech-11873}

| Technologie | Version | Link |
|---|---|---|
| AEM OAK | 1.50-T20230405052634-f9df4aa | [Oak API 1.50.0-API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.50.0/index.html) |
| AEM SLING-API | Version: 2.27.0 | [Apache Sling API 2.27.0 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version 1.4.20-1.4.0 | [Sprachspezifikation für HTML-Vorlagen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | Version: 2.22.6 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
