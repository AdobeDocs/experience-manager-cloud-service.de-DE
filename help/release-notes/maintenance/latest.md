---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: dc7150c6ce971aa6f89fa24f7ca387cbb28db1f2
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 63%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 17258 {#release-17258}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 17258, die am Mittwoch, 30. Juli 2024 veröffentlicht wurde. Die vorherige Wartungsversion war Version 17098.

Die Funktionsaktivierung von 2024.8.0 bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-17258}

* ASSETS-31445 - Erste Dynamic Media-Vorlagenfunktionen
* ASSETS-40399 - Aktualisierte Warteschlangeneinstellungen für DM-automatische Transkribierung
* ASSETS-40873 - Zulassen, dass die maximalen Zeilen für den Metadatenexport über die OSGi-Konfiguration festgelegt werden

### Behobene Probleme {#fixed-issues-17258}

* ASSETS-30613 - Asset ersetzen löscht nicht und fügt Asset in der neuen Bereitstellungsstufe hinzu
* ASSETS-31882 - Zugriff auf Streaming-Manifestdatei im Autor ist verboten
* ASSETS-39598 - Massenimport kann keine Assets mit Sonderzeichen im Namen aus dem S3-Backend löschen
* CNTBF-209 - Verbesserungen beim Abbruch von Abläufen bei Rückläufen
* SCRNS-3762 - PlayerLogger im Sequenzkanal verbessern, um Protokolle bei der Vorschau des Kanals im Browser in die Konsole einzufügen
* SCRNS-4455 - Fehlende Schaltfläche &quot;Veröffentlichung verwalten&quot;und &quot;Quick Publish&quot;für Benutzer ohne ADMIN im Content Provider für Kanäle
* SITES-22940 - Inhaltsfragment kann nicht als Workflow-Payload angezeigt werden

### Bekannte Probleme {#known-issues-17258}

Keine

### Änderungshinweis {#change-notice-17258}

* AEM as a Cloud Service deaktiviert ab September 2024 die Serialisierung von Ressourcen-Konfliktlösern über das Sling Model Exporter-Framework. Weitere Informationen finden Sie in der [Dokumentation](/help/implementing/developing/hybrid/disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter.md).

### Eingestellte Funktionen und APIs {#deprecated-17258}

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

### Eingebettete Technologien {#embedded-tech-17258}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1.66.0 | [Oak-API 1.66.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.66.0/index.html) |
| AEM SLING-API | 2.27.2 | [Apache Sling-API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | 2.25.4 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
