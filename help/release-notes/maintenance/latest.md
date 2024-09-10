---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 9323464610b804ff407f5eedf404ab2cca93a8da
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 50%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 17689 {#release-17689}

Im Folgenden finden Sie eine Zusammenfassung der kontinuierlichen Verbesserungen für die Wartungsversion 17689, die am Mittwoch, 10. September 2024 veröffentlicht wurde. Die vorherige Wartungsversion war Version 17569.

Die Funktionsaktivierung von 2024.9.0 bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-17689}

* ASSETS-41404: Änderungen zur Unterstützung von DRM-Verbesserungen.
* ASSETS-41621: Aktualisierter asynchroner Asset-Kopierauftrag.
* ASSETS-32166: Aktualisierter asynchroner Asset-Verschiebungsauftrag.
* ASSETS-41429: Bildvorgaben unterstützen DM OpenAPI.
* ASSETS-38968: Verbessern der Darstellung von Inhaltsfragmentverweisen.
* ASSETS-41787, ASSETS-41183: Verbesserungen für das Assets Bulk Operations-Framework.
* GRANITE-52917: Optimierungen zur Verbesserung der Installationszeiten von Inhaltspaketen.
* SCRNS-3980: Erkennen des grauen Bildschirms auf Playern mit Nachfolgen ohne Asset geplant.

### Behobene Probleme {#fixed-issues-17689}

* ASSETS-40875: Funkiöses NPE, das von AssetDeleteHandler protokolliert wird.
* ASSETS-42422: Vermeiden Sie das Auslösen eines asynchronen Auftrags für die einmalige Asset-Verschiebung.
* ASSETS-41234: Unified Shell - Globale Navigationsleiste funktioniert möglicherweise nicht, wenn sie geöffnet ist, wenn die Suchleiste geöffnet ist.
* ASSETS-42256: Unified Shell - Tag/Badge-Anzeigeumgebung funktioniert nur zeitweise.
* ASSETS-41271: Vermeidung unnötiger Neuveröffentlichungen von Assets beim Verschieben.
* ASSETS-38894: Einschränkende Wiederholungen durch Verarbeitung von Watchdog.
* ASSETS-40815: Verwenden Sie das PDF-Ausgabeformat der Vorschau zum Anzeigen der PPT-Datei in der Benutzeroberfläche für Linkfreigabe .
* ASSETS-37123: Asset-Vorschau kann nicht im Dialogfeld Linkfreigabe geladen werden.
* CQ-4358156: Aktualisieren Sie die Backlinks des gelöschten Tags.
* SCRNS-4495: Die Schaltfläche &quot;Fixiertes Einfügen&quot;funktioniert für verschiedene Benutzergruppen nicht ordnungsgemäß.
* SCRNS-4512: Entfernen Sie Komponenten, die sich auf ein Gerät beziehen, aus AEMaaCS-Bildschirmen.
* SCRNS-4466: Im Kanal-Dashboard ausgeblendet - Manifest anzeigen, Offline-Inhalt generieren, Manifestcache aktualisieren, Anzeigebereich.
* SCRNS-4513: Fügen Sie Spaltenüberschriften für die Suchergebnisseite in der Listenansicht hinzu.

### Bekannte Probleme {#known-issues-17689}

* FORMS-14340: Fehler bei der Instanziierung von FormsAndDocumentOmniSearchHandler und CloudStorageSubmitActionInserter. Dies sind harmlose Protokollanweisungen.
* FORMS-15818: Komponentendeskriptoreintrag &quot;OSGI-INF/com.adobe.aemfd.docmanager.impl.*.xml&quot;nicht gefundene Anweisungen in Serverprotokollen. Dies sind harmlose Protokollanweisungen.
* SITES-23662: Trigger, die eine Veröffentlichung vornehmen, können nicht aus JCR-Protokollanweisungen in Serverprotokollen extrahiert werden. Dies ist für eine Funktion in der Entwicklung, die zeitweise und harmlos Fehler &quot;Eine gültige Benutzer-ID kann im Batch der OSGi-Ereignisse nicht gefunden werden&quot;im Protokoll verursachen kann.

### Änderungshinweis {#change-notice-17689}

* AEM as a Cloud Service deaktiviert ab September 2024 die Serialisierung von Ressourcen-Konfliktlösern über das Sling Model Exporter-Framework. Weitere Informationen finden Sie in der [Dokumentation](/help/implementing/developing/hybrid/disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter.md).

### Eingestellte Funktionen und APIs {#deprecated-17689}

Beachten Sie, dass wir gerade dabei sind, `com.day.cq.wcm.api` zu aktualisieren. Mit der aktuellen Version haben wir einige der Methoden und Klassen als `@Deprecated` markiert. Diese werden in zukünftigen Versionen entfernt. Daher sollten Sie erwägen, zu den vorgeschlagenen Alternativen zu wechseln, wenn Sie eine davon verwenden.

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

### Sicherheitskorrekturen {#security-17689}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. Diese Wartungsversion behebt vier identifizierte Schwachstellen und sorgt somit für einen noch robusteren Systemschutz.

### Eingebettete Technologien {#embedded-tech-17689}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1.68.0 | [Oak-API 1.68.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.68.0/index.html) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | 2.26.0 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
