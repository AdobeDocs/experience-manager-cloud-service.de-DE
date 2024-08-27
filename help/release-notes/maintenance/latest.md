---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 82be9b2b328343e827b90bd8266d93127757f477
workflow-type: tm+mt
source-wordcount: '675'
ht-degree: 37%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 17569 {#release-17569}

Im Folgenden finden Sie eine Zusammenfassung der kontinuierlichen Verbesserungen für die Wartungsversion 17569, die am Mittwoch, 27. August 2024 veröffentlicht wurde. Die vorherige Wartungsversion war Version 17465.

Die Funktionsaktivierung von 2024.9.0 bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-17569}

* CQ-4353778: Übersetzungsprozessereignisse.
* CQ-4354583: Senden Sie Übersetzungsprozessereignisse über die Adobe-Pipeline.
* CQ-4356479: Nur Adobe-Code darf den /adobe-Servlet-Kontext verwenden.
* CQ-4358133: Optimierung der Jenkins-Worker-Nutzung.
* CQ-4358226: Die Funktion &quot;Übersetzung speichern&quot;funktioniert nicht für bestimmte Zeichenfolgenformate.
* CQ-4358270: AEM Translation Kit: August 08.
* CQ-4358310: Fügen Sie oak-compat-query-spi-1.2 zum Schnellstart hinzu.
* GRANITE-36205: Automatisierte Aktualisierung für interne Oak-Versionen in QS.
* GRANITE-49833: Batch-Unterstützung für Ereignis-Absender und -Proxy.
* GRANITE-52053: Entfernen Sie die Verwendung von Commons Collections 3: Platform Other.
* GRANITE-52492: Elastic async catch the case of PIT restore.
* GRANITE-53086: Jacoco-Plugin-Version auf 0.8.12 in AEMaaCS aktualisieren.
* GRANITE-53099: Update auf Apache Felix HTTP Jetty 5.1.24.
* GRANITE-53125: Classification zu CloudEvent hinzufügen.
* GRANITE-53328: Update von Filevault auf 3.8.0-T20240726111512-3cc11d50 mit Verbesserungen bei der Stashing-Protokollierung.
* GRANITE-53340: AEM660: Ordnungsgemäße Versionierung und Verzweigung für 660 CQ/Platform.
* GRANITE-53341: Warnung zur Verwendung von ACS Commons 6.
* GRANITE-53453: commons-lang auf 3.15.0 aktualisieren.
* GRANITE-53473: Nicht veraltete Sling-Einstellungen.
* GRANITE-53478: Update von Filevault auf Version 3.8.0.
* GRANITE-53505: Aktualisierung der QS auf &quot;commons-collections-3.2.2-adobe-2&quot;.
* GRANITE-53528: Update der Version der Plattformartefakte .
* GRANITE-53547: Bieten Sie eine alternative API, um die Verwendung von Apache Commons Lang 2 zu vermeiden.
* GRANITE-53575: Verwenden Sie BSAFE 6.2.5 in CS.
* GRANITE-53608: Aktualisierung von Oak auf die neueste öffentliche Version (1.68.0).
* SITES-23583: Sites Evergreen-Tests schlagen auf Java 17 fehl.
* SKYOPS-79535: Aktualisierung auf das Rumskript v2.
* SKYOPS-79816: Aktivieren Sie die Sling Feature Analyzer-Aufgabe für Dienstbenutzerzuordnungen im FACT-Tool.
* SKYOPS-81179: AEM erstellt Tests für das Umschalten zwischen Bundles.
* SKYOPS-81866: Berichtwarnungen für Pakete, von denen bekannt ist, dass sie mit Java 21 inkompatibel sind.
* SKYOPS-82660: Aktualisierung der Sling-API auf Version 2.27.6.
* SKYOPS-82961: Aktualisierung auf Sling ResourceResolver 1.12.0-T20240723153354-a0270a0.
* SKYOPS-83356: Erstellen Sie ein globales Dashboard zur Verfolgung von JVM-Versionen, die in AEM -Bereitstellungen verwendet werden.
* SKYOPS-83436: Java Runtime 21-Rollout bricht die Erstellung von adaptiven Formularen in AEM Forms ab.
* SKYOPS-84272: Protokollieren Sie die beim Start des AEM-Starters verwendete Java-Version.

### Behobene Probleme {#fixed-issues-17569}

* CMGR-60225: Fehler bei der Pipeline-Ausführung beim AEM Sites CS-Kunden bei der Validierung der Aktualisierung auf AEM Version 17486.
* GRANITE-45919: Eingebettete Länder in die Liste &quot;Land/Region&quot;unter &quot;Benutzereinstellungen bearbeiten&quot;.
* GRANITE-51715: Die Auswahl gibt die Auswahl manchmal nicht in das Textfeld ein.
* GRANITE-53290: Prüfen Sie beim Analysieren der URL in der XSS-Prüfung das Protokoll ordnungsgemäß.
* GRANITE-53576: Falsche Definition des Service-Rangs in OSGi-Konfigurationen.
* SKYOPS-82129: MemoryLek in Sling-Modellen.

### Bekannte Probleme {#known-issues-17569}

Keine.

### Änderungshinweis {#change-notice-17569}

* AEM as a Cloud Service deaktiviert ab September 2024 die Serialisierung von Ressourcen-Konfliktlösern über das Sling Model Exporter-Framework. Weitere Informationen finden Sie in der [Dokumentation](/help/implementing/developing/hybrid/disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter.md).

### Eingestellte Funktionen und APIs {#deprecated-17569}

Beachten Sie, dass wir gerade dabei sind, `com.day.cq.wcm.api` zu aktualisieren. Mit der aktuellen Version haben wir einige der Methoden und Klassen als `@Deprecated` markiert. Diese werden in zukünftigen Versionen entfernt. Daher sollten Sie erwägen, zu den vorgeschlagenen Alternativen zu wechseln, wenn Sie eine davon verwenden.

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

### Sicherheitskorrekturen {#security-17569}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. In dieser Wartungsversion werden vier Schwachstellen behoben, die unser Engagement für einen robusten Systemschutz verstärken.

### Eingebettete Technologien {#embedded-tech-17569}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1,68,0 | [Oak-API 1.68.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.68.0/index.html) |
| AEM SLING-API | 2,27,6 | [Apache Sling API 2.27.6 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | 2,26,0 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
