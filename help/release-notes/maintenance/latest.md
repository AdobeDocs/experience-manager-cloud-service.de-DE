---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: fd0b8ca281f35a92876f3c31baa4e17884f23948
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 39%

---

# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 12441 {#release-12441}

Nachfolgend sind die kontinuierlichen Verbesserungen für die Wartungsversion 12441 zusammengefasst, die am 27. Juni 2023 veröffentlicht wurde. Diese Wartungsversion ist eine Aktualisierung der vorherigen Wartungsversion 12255.

2023.7.0 Die Funktionsaktivierung stellt den vollständigen Funktionsumfang für dieses Maintenance Release bereit. Siehe [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=de) für weitere Informationen.

### Verbesserungen {#enhancements-12441}

- SITES-8769: Verbessern von StyleImpl-Aufrufen in ResponsiveGrid

### Behobene Probleme {#fixed-issues-12441}

- Verschiedene Aktualisierungen zur Barrierefreiheit
- SITES-12688: Seiten-Editor: Logischer Operator ODER in der Asset Finder-Suche nicht ordnungsgemäß funktioniert
- SITES-4951: Seiten-Editor: Die Tag-Suche im Seiteneditor findet keine Untertags
- SITES-12465: Experience Fragments: Pfeiltasten funktionieren nicht im Dialogfeld Experience Fragment-Komponente
- SITES-12893: Experience Fragments: Anwenden einer zirkulären Referenzvalidierung für Experience Fragments
- SITES-12715: Experience Fragments: Cloud Service-Konfigurationen, die auf den Experience Fragments-Ordner angewendet werden, bleiben nicht bestehen
- SITES-13097: Experience Fragments: Es ist nicht möglich, Experience Fragments zu einem Übersetzungsprojekt hinzuzufügen
- SITES-13165: GraphQL: Standardverhalten für das Filtern von Nullwerten wiederherstellen
- SITES-12577: Link-Checker: Transformator schreibt Links nicht gelegentlich um
- SITES-13559: MSM: Beim Rollout einer Komponente wird die Ausnahme &quot;Ist nicht änderbar&quot;ausgelöst
- SITES-11757: MSM: Rollout-Konfiguration von übergeordneter Seite übernehmen wird für untergeordnete Seiten nicht zurückgesetzt
- SITES-14073: Sites-Admin: CSV-Bericht schlägt mit 500 fehl, wenn keine zu exportierende Eigenschaft ausgewählt wird

### Bekannte Probleme {#known-issues-12441}

Keine

### Eingebettete Technologien {#embedded-tech-12441}

| Technologie | Version | Link |
|---|---|---|
| AEM OAK | 1.50-T20230405052634-f9df4aa | [Oak-API 1.50.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.50.0/index.html) |
| AEM SLING-API | Version: 2.27.0 | [Apache Sling-API 2.27.0 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version: 1.4.20-1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | Version: 2.23.0 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
