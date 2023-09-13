---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 57d818e3e89f17f829a6b51689f02e5f59614563
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 36%

---

# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 13420 {#release-13420}

Nachfolgend sind die kontinuierlichen Verbesserungen für das Maintenance Release 13420 zusammengefasst, das am 11. September 2023 veröffentlicht wurde. Dieses Maintenance Release ersetzt Version 13323.

2023.9.0 Die Funktionsaktivierung stellt den vollständigen Funktionsumfang für dieses Maintenance Release bereit. Siehe [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=de) für weitere Informationen.

### Verbesserungen {#enhancements-13420}

- ASSETS-19544: Assets, die zuletzt von der Eigenschaft geändert wurden, sind jetzt auf den Benutzer festgelegt, der die Verarbeitung anfordert.

### Behobene Probleme {#fixed-issues-13420}

- ASSETS-27628: Fehlerhafter Knoten &quot;Kanäle&quot;, der beim Anpassen des Asset-Suchbereichs erstellt wird
- ASSETS-27539: Upload-Beschränkungen für die Übereinstimmung regulärer Ausdrücke.
- ASSETS-26530: Unified Shell bringt Benutzer nicht zurück zur Originalseite.
- ASSETS-22719: Brackets bei der Benennung von Breakpoints für Smartes Zuschneiden beschädigen die Bearbeitungsfunktion für smartes Zuschneiden.
- ASSETS-27726: linkshare.html sollte nicht von Google indiziert werden.
- ASSETS-27791: Die Validierung des Metadatenschemas erfolgt nur für das erste Feld.
- ASSETS-25544: Schaltfläche zur Invalidierung des CDN-Cache wurde korrigiert.
- ASSETS-26575: Kürzung von Namen beim Erstellen von Bildsets korrigiert.
- ASSETS-26705: Es wurde eine unnötige Verarbeitung von Nicht-DM-Ordner-Assets und Inhaltsfragmenten behoben.
- ASSETS-25740: Korrektur der Bildschirmlesehilfen, die den Namen und die Rolle für Steuerelemente zum Bearbeiten/Zuschneiden auf der Seite &quot;Smartes Zuschneiden bearbeiten&quot;nicht mit Pfeiltasten nach unten kommentieren.
- CQ-4354266: Posteingangselemente können nicht geöffnet werden.
- CQ-4354347: Aktualisierte AEM Übersetzungen.
- DISP-1009: User-Agent als nicht erster Header trims X-Forwarded-Host.
- Verschiedene Fehlerbehebungen zur Barrierefreiheit und Sicherheit.

### Bekannte Probleme {#known-issues-13420}

Keine

### Eingebettete Technologien {#embedded-tech-13420}

| Technologie | Version | Link |
|---|---|---|
| AEM OAK | 1.54-T20230817132355-3800a65 | [Oak-API 1.54.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.54.0/index.html) |
| AEM SLING-API | Version: 2.27.2 | [Apache Sling-API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version: 1.4.20-1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | Version: 2.23.2 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
