---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 1d6a54f87d55179c11c7ccc7766eeeb475674f05
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 49%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 19567 {#19567}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 19567, die am Mittwoch, 18. Februar 2025 veröffentlicht wurde. Die vorherige Wartungsversion war Version 19352.

Die Funktionsaktivierung von 2025.2.0 wird den vollen Funktionsumfang für diese Wartungsversion bieten. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-19567}

* GRANITE-56650: Inhaltsverteilung sollte blockierte Warteschlangen erst nach einigen weiteren Zustellversuchen signalisieren
* SKYOPS-89616: Bis zu 40 technische Konten in Adobe Developer Console erstellen

### Behobene Probleme {#fixed-issues-19567}

* CNTBF-232: Deep-Package-nt:file-Knoten, um obligatorische jcr:content-untergeordnete Knoten einzuschließen
* CQ-4358930: Leistungsproblem beim Laden von Seiteneigenschaften mit vielen Mehrfachfeldern
* GRANITE-55960: Leistungsproblem mit Coral Select Field in AEM as a Cloud Service
* GRANITE-56197: Beim neuen Workflow-Schritt TreeActivation werden keine Assets in einer großen flachen Ordnerstruktur in Batches verschoben

#### AEM-Handbücher {#guides}

* GUIDES-23526: Beim Aktualisieren von Bedingungen aus dem Ordnerprofil gehen alle Bedingungsgruppen verloren und die Bedingungen werden reduziert.
* GUIDES-22574: Wenn ein externer Link eine UUID enthält, geht er in die Nachbearbeitung und konvertiert den externen Link in einen UUID-Link, wodurch der Link im Editor und auch auf den Veröffentlichungsseiten unterbrochen wird.
* GUIDES-24983: Beim Kopieren eines Bildes aus einem externen Produkt (z. B. MS PowerPoint) und Einfügen in Guides wird die Funktion zum schnellen Hochladen des Assets zur Verwendung in der Datei unterbrochen.
* GUIDES-21772: Die native PDF-Generierung schlägt für Inhalte fehl **wobei das** chunk“ auf &quot;**-content“**.
* GUIDES-23964: Bei Auswahl von **Eigenschaften bearbeiten** werden im Baseline-Dialogfeld nicht die zuvor gespeicherten Kriterien für die dynamische Baseline angezeigt.
* GUIDES-19067: Beim Duplizieren eines Ordnerprofils wird dessen Administrator-Benutzerliste auch aus dem ursprünglichen Ordnerprofil kopiert

Weitere Informationen zu den neuen und verbesserten Funktionen sowie zu den Problemen, die in der Version behoben wurden, finden Sie in der [Roadmap für Experience Manager Guides-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

### Bekannte Probleme {#known-issues-19567}

Keine.

### Eingestellte Funktionen und APIs {#deprecated-19567}

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

### Sicherheitskorrekturen {#security-19567}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. Diese Wartungsversion behebt 21 identifizierte Schwachstellen und sorgt somit für einen noch robusteren Systemschutz.

### Eingebettete Technologien {#embedded-tech-19567}

| Technologie | Version | Link |
|---|--------------|-------------------------------------------------------------------------------------------------------------------|
| AEM Oak | 1,76,0 | [Oak-API 1.76.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.76.0/index.html) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.26-1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | 2.27.0 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
