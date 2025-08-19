---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 90e92cfb15a6dfe5a8a474996f52c8a0c689f5e6
workflow-type: tm+mt
source-wordcount: '607'
ht-degree: 38%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 21994 {#21994}

Im Folgenden finden Sie eine Zusammenfassung der kontinuierlichen Verbesserungen für die Wartungsversion 21994, die am Mittwoch, 19. August 2025 veröffentlicht wurde. Die vorherige Wartungsversion war Version 21772.

Die Funktionsaktivierung von 2025.8.0 bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Neue Funktionen  {#new-features-21994}

Keine.

### Verbesserungen {#enhancements-21994}

* GRANITE-53488: Verbessern Sie die Fehlerbehandlung des Endpunkts „deleteconf.json“.
* GRANITE-59968: Konfigurieren von REPLICATION_FORCE_READY_MILLIES zulassen.
* GRANITE-60183: Apache commons-fileupload 1.6.0.
* GRANITE-60306: Apache commons-lang bis 3.18.0.
* GRANITE-60637: Apache commons-codec bis 1.19.0.
* GRANITE-60645: Apache commons-ui 2.20.0.
* GRANITE-60663: Apache commons-text 1.14.0.
* GRANITE-60714: Mongo Java-Treiber 5.2.
* GRANITE-60778: Filevault 4.0.0.
* GRANITE-60823: Jackrabbit 2.22.2.
* GRANITE-60967: Erstellen Sie Metriken zum Tracking der Kompilierungszeit der Client-Bibliothek.
* SKYOPS-105469: Unterstützung für acsredirectMgr in der Autofix-API hinzufügen.
* SKYOPS-113929: Metriken für replikationsbereite Prüfung hinzufügen.
* SKYOPS-84821: Sling-Engine 2.16.6.
* SKYOPS-114322: Bump up-Abschluss Compilersprache in Level bis `ECMASCRIPT_2018`.

### Behobene Probleme {#fixed-issues-21994}

* GRANITE-60167: Die asynchrone Indexaktualisierung in Skyline unterstützt keine CSV-Daten.
* GRANITE-60532: Die Änderung von Wert-Umschaltern wird nicht übernommen.
* SITES-34277: Behebung eines Blockierungsfehlers in Übersetzungs-Workflows für Seiten.
* SKYOPS-105471: Unterstützt DambaseRedirect Fix für aso autofix.
* SKYOPS-109532: Hinzufügen einer Funktion entfernt Link als Kommentar hinter Umschalter.

#### AEM Guides {#guides-21994}

* GUIDES-26688: CSS- und Seiten-Layout-Dateien in nativen PDF-Vorlagen weisen ein inkonsistentes Dateisperrverhalten auf, sodass sie selbst dann bearbeitet werden können, wenn die Dateien gesperrt sind.
* GUIDES-30900: Das Kopieren eines Ordners mit einer großen Anzahl von Assets aus der Assets-Benutzeroberfläche führt zu einer API-Zeitüberschreitung. Der Vorgang wird weiterhin im Backend ausgeführt und nach einiger Zeit abgeschlossen, aber in der Benutzeroberfläche wird keine Erfolgs- oder Fehlermeldung oder Benachrichtigung angezeigt.
* GUIDES-29090: In der nativen PDF-Ausgabe wird die Indexliste (LOI) in nicht alphabetischer Reihenfolge angezeigt und verschachtelte Indexbegriffe werden nicht ordnungsgemäß gruppiert, was die Navigation im Index erschwert.
* GUIDES-11227: Beim Kopieren einer DITA-Zuordnung über die Assets-Benutzeroberfläche wird auch die angehängte Baseline in die neue Zuordnung kopiert.
* GUIDES-31506: Die Startseite wird leer angezeigt, wenn eine der im Widget Letzte Dateien aufgelisteten Dateien auf einer Vorlage basiert, deren Quellvorlage keine Miniaturansicht enthält.

Weitere Informationen zu den neuen und verbesserten Funktionen sowie zu den Problemen, die in der Version behoben wurden, finden Sie in der [Roadmap für Experience Manager Guides-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

### Bekannte Probleme {#known-issues-21994}

* Apache HTTPD Version 2.4.65 führt Änderungen ein, die sich aufgrund neuer Einschränkungen, die im Rahmen von Sicherheitskorrekturen implementiert wurden, auf bestimmte Konfigurationen auswirken können. Diese Korrekturen beheben Sicherheitslücken, indem sichergestellt wird, dass Anweisungen wie `RequestHeader set`, `edit` und `edit_r`, die zum Ändern der Inhaltstyp-Kopfzeile verwendet werden, jetzt korrekt auf Anfragekopfzeilen beschränkt sind. Diese Änderung verhindert unbeabsichtigte Änderungen an Antwort-Headern, insbesondere für statische Inhalte.

### Eingestellte Funktionen und APIs {#deprecated-21994}

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

### Sicherheitskorrekturen {#security-21994}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. Diese Wartungsversion behebt 2 identifizierte Schwachstellen und sorgt somit für einen noch robusteren Systemschutz.

### Eingebettete Technologien {#embedded-tech-21994}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1,84,0 | [Oak-API 1.84.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.84/index.html) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| Apache HTTP Server | 2.4.65 | [Apache httpd 2.4.65](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| AEM-Kernkomponenten | 2.29.0 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (Standard) | [Unterstützte Node.js-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
