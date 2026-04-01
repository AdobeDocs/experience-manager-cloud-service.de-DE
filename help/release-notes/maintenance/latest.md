---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: e035c1c27f652af231034588eb1359354182dcb0
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 62%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 25194 {#25194}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 25194, die am Donnerstag, 1. April 2026 veröffentlicht wurde. Die vorherige Wartungsversion war Version 24678.

Die Funktionsaktivierung von 2026.4.0 bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Versions-Roadmap von Experience Manager](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

>[!NOTE]
>
>Version 24893 wurde als privat gekennzeichnet.

### Verbesserungen {#enhancements-25194}

* ASSETS-65127: Benutzerdefinierte Ereignis-Metadaten: Verbesserte Verarbeitung von Metadatennamen.
* ASSETS-63313: Erstellen Sie automatisch verknüpfte Links für exportierte Assets und übergeordnete Elemente basierend auf C2PA-Manifesten.
* ASSETS-10995: Anzahl der Assets in einer Download-Zip begrenzen.

### Behobene Probleme {#fixed-issues-25194}

* ASSETS-62882: Admin-Ansicht: Die Info-QuickInfo funktioniert nicht mehr, wenn mehrere ungültige Dateinamen hochgeladen werden.
* ASSETS-63642: Freigabe-Link kann Asset in einigen Entwicklungsumgebungen nicht rendern (SLA3).
* ASSETS-59267: NPE beim Laden von Anwendungsmetadaten für die Versand-Payload.
* ASSETS-59227: Metadatenexport: Nicht ausgewählte Eigenschaften sind aufgrund der Regex-Zuordnung nicht mehr enthalten.
* ASSETS-65187: CSV-Vorschau in der Cloud, wenn Spaltendaten Escape-Kommas enthalten.
* ASSETS-63441: Stellen Sie sicher, dass alle Benutzenden über Berechtigungen zum Lesen der Assets Omnisearch-Konfiguration verfügen.
* SITES-40095: Metadaten-Editor: Verweise auf lokale Inhaltsfragmente, die mehr als 10 Einträge umfassen.

### Bekannte Probleme {#known-issues-25194}

Keine.

### Eingestellte Funktionen und APIs {#deprecated-25194}

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

### Sicherheitskorrekturen {#security-25194}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. In dieser Wartungsversion wurden 9 identifizierte Schwachstellen behoben, was für einen noch robusteren Systemschutz sorgt.

### Eingebettete Technologien {#embedded-tech-25194}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1,90,0 | [Oak 1.90.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.90.0/index.html) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| Apache HTTP Server | 2.4.65 | [Apache Httpd 2.4.65](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| AEM-Kernkomponenten | 2,30,4 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (Standard) | [Unterstützte Node.js-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
