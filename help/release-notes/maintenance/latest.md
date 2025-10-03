---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 6cf380fd972888fa21f682b0e799cf5ab594e829
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 50%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 22758 {#22758}

Im Folgenden finden Sie eine Zusammenfassung der fortlaufenden Verbesserungen für die Wartungsversion 22758, die am Donnerstag, 1. Oktober 2025 veröffentlicht wurde. Die vorherige Wartungsversion war Version 22450.

Die Funktionsaktivierung von 2025.10.0 bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-22758}

* ASSETS-56227: Benennen Sie den Modifikator „adobe-countDown-timer“ um.
* CNTBF-493: Bump content-backflow-Bundle-Version auf 2.0.28.
* CQ-4361110: Granite-Übersetzungen.
* CQ-4361112: Neueste AEM-Übersetzungen.
* GRANITE-56026: Verbessern Sie die API-Status-Code-Antworten für Berechtigungen.
* GRANITE-61015: Paket `org.apache.commons.io.channels` der öffentlichen exportierten Liste hinzugefügt.
* GRANITE-61167: Das Felix-Protokoll wurde auf die neueste OSGI-Spezifikation aktualisiert.
* GRANITE-61167: Aktualisieren einer Reihe von Apache Felix-Abhängigkeiten.
* GRANITE-61169: Verbessern Sie die Prüfung auf geschützte Zeichenfolgen.
* GRANITE-61622: Aktualisieren einer Reihe von Apache Sling-Abhängigkeiten.
* GRANITE-61663: `com.adobe.granite.repository.indexdefs-1.0.2` zum Schnellstart hinzufügen.
* GRANITE-61811: `com.adobe.granite.repository-2.0.0` zum Schnellstart hinzufügen.
* SITES-32014: Überwachen Sie externe Ereignisse, um Service-Registrierungen zu aktualisieren.
* SITES-34277: Korrektur blockiert Fehler in Übersetzungs-Workflows für Seiten.
* SKYOPS-108706: Mit der aktualisierten Version wird das Bundle auf die neueste Version umgeschaltet (eTag-Caching).
* SKYOPS-114210: Aktualisierung auf die neueste Version des Bundles aem.pss.service .
* SKYOPS-116171: Update auf Sling ResourceResolver 1.12.12.
* SKYOPS-119811: Dispatcher-Publish 2.0.258 veröffentlicht.

### Behobene Probleme {#fixed-issues-22758}

* GRANITE-61875: Trigger für „ungültige Ausdrucksauswertung“ beheben - Inhaltsfragmente können nicht gespeichert werden und Assets können nicht heruntergeladen werden.
* SITES-22059: Beheben eines JS-Fehlers in PDF Viewer-Komponenten. Nicht lokalisierte Zeichenfolge „Dateivorschau nicht verfügbar“ in Kernkomponenten-Website > PDF-Viewer.
* GRANITE-59704: Behebung von htmllibmanager.debug, das dazu führte, dass der Bearbeitungsmodus fehlschlug.
* GRANITE-61042: Integrieren Sie FELIX-6796 (ServiceTracker NPE fix) in das AEM Felix Web Console-Bundle.
* GRANITE-61165: Workspace.copy() löst RepositoryException aus.
* GRANITE-61875: ui.commons auf 5.10.50 aktualisieren.

### Bekannte Probleme {#known-issues-22758}

Keine.

### Eingestellte Funktionen und APIs {#deprecated-22758}

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

### Sicherheitskorrekturen {#security-22758}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. In dieser Wartungsversion wurden 13 identifizierte Schwachstellen behoben, was für einen noch robusteren Systemschutz sorgt.

### Eingebettete Technologien {#embedded-tech-22758}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1,86,0 | [Oak 1.86.0-API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.86/index.html) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| Apache HTTP Server | 2.4.65 | [Apache Httpd 2.4.65](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| AEM-Kernkomponenten | 2,30,1 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (Standard) | [Unterstützte Node.js-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
