---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 33468de99a3e77539f4bdc9435324c9f52a45d9f
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 70%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 22171 {#22171}

Im Folgenden finden Sie eine Zusammenfassung der kontinuierlichen Verbesserungen für die Wartungsversion 22171, die am Mittwoch, 2. September 2025 veröffentlicht wurde. Die vorherige Wartungsversion war Version 21994.

Die Funktionsaktivierung von 2025.9.0 bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Versions-Roadmap von Experience Manager](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Neue Funktionen  {#new-features-22171}

* ASSETS-53136: Vanity-ID-Unterstützung in Dynamic Media mit OpenAPI.

### Verbesserungen {#enhancements-22171}

Keine.

### Behobene Probleme {#fixed-issues-22171}

* ASSETS-52510: Die Erkennung doppelter Dateinamen schlägt für Dateinamen mit Unicode-`U+202F` fehl.
* ASSETS-53489: Beim Löschen von Ordnern aus der Assets-Ansichts-Benutzeroberfläche wird die Genehmigung nicht für alle enthaltenen Assets aufgehoben.
* ASSETS-54821: Zeitweise auftretender „Server-Fehler“ in Asset Link.
* ASSETS-55024: Beschädigtes Bild in der Vorlage „Download per E-Mail“ von AEM Assets.
* ASSETS-55325: Statische Dynamic Media-URLs lassen die Dateierweiterung nach dem Umbenennen des Assets weg.
* ASSETS-55334: Das Dialogfeld Linkfreigabe blinkt kurz und verschwindet oder wird nie angezeigt.
* ASSETS-55382: Asynchrone Asset-Vorgänge wurden neu gestartet, um einen doppelten Zielordner zu erstellen.
* ASSETS-55472: Option „Veröffentlichung verwalten“ „Nur bereits veröffentlichte Seiten einbeziehen“ ignoriert.
* SITES-31600: Die Personalisierung mit ContextHub JS ist fehlerhaft.

Weitere Informationen zu den neuen und verbesserten Funktionen sowie zu den Problemen, die in der Version behoben wurden, finden Sie in der [Roadmap für Experience Manager Guides-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

### Bekannte Probleme {#known-issues-22171}

Keine.

### Eingestellte Funktionen und APIs {#deprecated-22171}

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

### Sicherheitskorrekturen {#security-22171}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. Diese Wartungsversion behebt sieben identifizierte Schwachstellen und bestärkt dadurch unser Engagement für einen robusten Systemschutz.

### Eingebettete Technologien {#embedded-tech-22171}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1.84.0 | [Oak-API 1.84.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.84/index.html) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| Apache HTTP Server | 2.4.65 | [Apache Httpd 2.4.65](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| AEM-Kernkomponenten | 2.29.0 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (Standard) | [Unterstützte Node.js-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
