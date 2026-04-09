---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 881e7788c2ae8fd01fbe2c0af08228fd96179733
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 42%

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

#### AEM Guides {#guides-25194}

* GUIDES-38412 : Beim Bearbeiten einer Schematron-`(*.sch)` und bei Verwendung der Funktion zum Suchen und Ersetzen wird das Bedienfeld „Suchen und Ersetzen“ unten teilweise außerhalb des Bildschirms angezeigt, wodurch der Zugriff auf die Eingabefelder und Steuerelemente verhindert wird.
* GUIDES-37806: Wenn dasselbe Thema in mehreren Zuordnungen mit unterschiedlichen bedingten Vorgaben wiederverwendet wird, überschreibt die Veröffentlichung der neuesten Zuordnung in Salesforce den Themeninhalt, was dazu führt, dass Benutzenden zuvor veröffentlichter Zuordnungen falsche Daten angezeigt werden.
* GUIDES-39394: Wenn ein Bild, das ursprünglich als sprachspezifisches Asset mit einer bestimmten Version (z. B. unter `/en/`) verwaltet wurde, in einen globalen Ordner mit einer aktualisierten Version verschoben und ein Baseline-Export durchgeführt wird, verweist die neue Baseline weiterhin auf veraltete sprachspezifische Versionen dieses Bildes, was zu einem fehlgeschlagenen Baseline-Export führt.
* GUIDES-39054: Beim Erstellen einer dynamischen Baseline reagiert der Editor manchmal aufgrund mehrerer gleichzeitiger API-Anfragen nicht mehr, wodurch alle anderen Vorgänge angehalten werden.
* GUIDES-37781: Wenn Sie einen Benutzer einer Prüfungsaufgabe zuweisen, werden in der Dropdown-Liste alle Benutzer und nicht nur die mit den ausgewählten Projekten verknüpften aufgelistet. Dies führt zu ungültigen Benutzeroptionen.
* GUIDES-39385: Beim Öffnen eines Berichts für eine Zuordnung tritt beim Laden des Bedienfelds „Filter“ eine Verzögerung auf.

Weitere Informationen zu den neuen und verbesserten Funktionen sowie zu den Problemen, die in der Version behoben wurden, finden Sie in der [Roadmap für Experience Manager Guides-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

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
