---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 573de431328650778b3ef0979a24190477382310
workflow-type: ht
source-wordcount: '332'
ht-degree: 100%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 17098 {#release-17098}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 17098, die am 16. Juli 2024 veröffentlicht wurde. Die vorherige Wartungsversion war Version 16971.

Die Funktionsaktivierung von 2024.7.0 bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-17098}

- SKYOPS-79817: Aktivieren der Sling Feature Analyzer-Aufgabe für Dienstbenutzerzuordnungen

### Behobene Probleme {#fixed-issues-17098}

- ASSETS-39665: Smart Crops Sync funktioniert nach der Migration von 6.5 zu AEMCS nicht mehr
- FORMS-14993: Forms-API gibt „500“ für das zuvor verwendete Material zurück
- GRANITE-52120: CRXDE gibt „500“ zurück, wenn Zugriffskontrolllistendaten angezeigt werden
- GRANITE-52573: Anfragen geben „400“ zurück, wenn // in neu geschriebenen URLs verwendet wird
- GRANITE-52746: „Alle Knotentypen“ werden im Dialogfeld „Knoten erstellen“ nicht geladen
- GRANITE-52777: Fehlerhafte Verarbeitung von 404er-Meldungen beim Einbetten der Anfrage
- GRANITE-52871: Sicherstellen, dass publish-worker mit golden-publish synchronisiert ist und vor der Komprimierung abgeschlossen wird
- SKYOPS-79173: Replikator repliziert nicht auf mehrere Agenten, die einem bestimmten AgentIdFilter entsprechen
- SKYOPS-80075: Probleme mit Umlauten in Asset-Namen lösen eine Blockierung der Veröffentlichungswarteschlange aus (Mac)
- SKYOPS-81032: Herausfiltern von Protokollen, die durch Anfragen generierten werden, die Protokolle bei Verwendung der erweiterten Protokollierung abrufen sollen

### Bekannte Probleme {#known-issues-17098}

Keine

### Änderungshinweis {#change-notice-17098}

- AEM as a Cloud Service deaktiviert ab September 2024 die Serialisierung von Ressourcen-Konfliktlösern über das Sling Model Exporter-Framework. Weitere Informationen finden Sie in der [Dokumentation](/help/implementing/developing/hybrid/disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter.md).

### Eingestellte Funktionen und APIs {#deprecated-17098}

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

### Eingebettete Technologien {#embedded-tech-17098}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1.66.0 | [Oak-API 1.66.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.66.0/index.html) |
| AEM SLING-API | 2.27.2 | [Apache Sling-API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | 2.25.4 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
