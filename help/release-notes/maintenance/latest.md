---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 437125b6819edf70539ebacb4a8beddb755fcb7a
workflow-type: tm+mt
source-wordcount: '568'
ht-degree: 39%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 20626 {#20626}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 20626, die am Mittwoch, 29. April 2025 veröffentlicht wurde. Die vorherige Wartungsversion war Version 20476.

Die Funktionsaktivierung von 2025.5.0 wird den vollen Funktionsumfang für diese Wartungsversion bieten. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-20626}

* ASSETS-46413, ASSETS-46580: Neuen Prüfungsstatus „Vorschau“ hinzugefügt.
* ASSETS-49542: Erweiterung der unterstützten Sprachen für Video- und Audiotranskribierung und -übersetzung.
* ASSETS-48264: Erweiterung der Unterstützung der PNG-Qualität für Ausgabedarstellungen.

### Behobene Probleme {#fixed-issues-20626}

* ASSETS-50387: Korrigieren Sie die Standardminiaturansicht des Inhaltsfragments zur Verwendung in GenStudio.
* ASSETS-49006: Videoeigenschaften anzeigen, wenn Benutzende keine Schreibberechtigungen haben.
* ASSETS-46757, ASSETS-46997: Verbessern der Barrierefreiheit im Editor für smartes Zuschneiden.
* ASSETS-48018: Verbessern Sie das Tracking von Asset-Verweisen im Assets-Veröffentlichungsbericht.
* ASSETS-35846: Verbesserte Konsistenz beim Zugriff zwischen Autoren- und Bereitstellungsebene.
* ASSETS-48171: Verbessern der Konsistenz von Dynamic Media-Vorlagen mit der Arbeitsfläche.
* ASSETS-49813: Verbessern der Ablaufbenachrichtigung.
* ASSETS-47768, ASSETS-49825, ASSETS-49008, ASSETS-48287: Verbessern Sie die Verwaltung und die Sichtbarkeit von Massenvorgängen.
* ASSETS-50003, ASSETS-50004: Verbessern Sie die Benennung und Kontrolle über die in einem Asset-Download enthaltenen Ausgabedarstellungen.
* ASSETS-47939: Verbesserte Organisation der Reaktionen auf Content Hub.
* ASSETS-46738: Verbessern Sie die Leistung bei sehr großen Sammlungen.
* ASSETS-50121: Erhöhen der Zuverlässigkeit veröffentlichter Asset-Ereignisse.
* ASSETS-48490: Verbessern Sie die Ausfallsicherheit der automatisierten Verarbeitung während der Bildaufnahme.
* ASSETS-28106, ASSETS-49404: Verbessern Sie die Stabilität der Volltextsuche.
* ASSETS-50006, ASSETS-50423: Verbessern der Such- und Durchlaufleistung in einem großen Ordner.
* ASSETS-46021: Verbesserte Videoanzeige für Safari- und mobile Browser.
* ASSETS-49002: Verbesserte Handhabung der Bearbeitung von Dynamic Media-Vorlagen.
* ASSETS-48376: Verschiedene Verbesserungen in der Benutzeroberfläche von Content Hub.
* ASSETS-48504, ASSETS-49378: Verschiedene Verbesserungen am Benutzeroberflächenverhalten.
* ASSETS-49540: Verschieben Sie die Asset Relations OpenAPI aus der Experimentierphase.
* ASSETS-40284: Aktualisieren der Dokumentation zur Adobe Stock-Integration.
* ASSETS-49739: Arbeiten zur Integration von Figma aus dem Asset-Wähler.

#### AEM-Handbücher {#guides}

* GUIDES-21734: Für -Elemente können keine neuen IDs generiert werden, wenn solche Elemente über Ausschnitte hinzugefügt oder über Vorlagen erstellt werden, selbst wenn die Option für die automatische Generierung von ID in XMLEditorConfig aktiviert ist.
* GUIDES-25969: Wenn das Attribut `scope=external` in externen Links in einem DITA-Thema fehlt, schlägt die Veröffentlichung von HTML5 fehl, ohne die Dateien anzugeben, in denen dieses Attribut in den Fehlerprotokollen fehlt, insbesondere wenn der Microservice aktiviert ist.
* GUIDES-27288: Die Metadateneigenschaften können nicht an Zuordnungslandseiten übergeben werden, die mit der neuen AEM Sites-Veröffentlichung generiert wurden.

Weitere Informationen zu den neuen und verbesserten Funktionen sowie zu den Problemen, die in der Version behoben wurden, finden Sie in der [Roadmap für Experience Manager Guides-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

### Bekannte Probleme {#known-issues-20626}

Keine.

### Eingestellte Funktionen und APIs {#deprecated-20626}

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

### Sicherheitskorrekturen {#security-20626}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. Diese Wartungsversion behebt 11 identifizierte Schwachstellen und sorgt somit für einen noch robusteren Systemschutz.

### Eingebettete Technologien {#embedded-tech-20626}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1.78.0 | [Oak-API 1.78.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.78.0/index.html) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.26–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | 2,29,0 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
