---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: cf8b5d8b11452268b2839053c1e05cc2ec107a91
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 53%

---

# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 13173 {#release-13173}

Nachfolgend sind die kontinuierlichen Verbesserungen für das Maintenance Release 13173 zusammengefasst, das am 18. August 2023 veröffentlicht wurde. Diese Wartungsversion ist eine Aktualisierung der vorherigen Wartungsversion 13099.

2023.8.0 Die Funktionsaktivierung stellt das vollständige Funktionssatz für dieses Maintenance Release bereit. Siehe [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=de) für weitere Informationen.

### Verbesserungen {#enhancements-13173}

Keine

### Behobene Probleme {#fixed-issues-13173}

- SITES-15463: Sites-Vorlagen - Vorlagen können nicht veröffentlicht werden.

### Bekannte Probleme {#known-issues-13173}

- SITES-15359: Inhaltsfragmente - Das Variantennamensmuster stimmt nicht mit Varianten überein, die ```'_'``` in ihren Ressourcennamen.
- FORMS-10444: Adaptive Forms-Vorlagen - Vorlagen können nicht veröffentlicht werden (Problemumgehung: Verwenden Sie die Verteilungskonsole).
- CQ-4354191: Workflows - Benutzerdefinierter Starter kann aufgrund von auf nt:unstrukturierten Knoten vorhandenen Replikations-Metadaten mehrmals Trigger werden (Problemumgehung: Aktualisieren Sie Starter, um Replikations-Metadateneigenschaften auszuschließen, um Überschneidungen zu vermeiden).

### Eingebettete Technologien {#embedded-tech-13173}

| Technologie | Version | Link |
|---|---|---|
| AEM OAK | 1.52-T20230629133256-25c01b8 | [Oak-API 1.52.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.52.0/index.html) |
| AEM SLING-API | Version: 2.27.2 | [Apache Sling-API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version: 1.4.20-1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | Version: 2.23.2 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
