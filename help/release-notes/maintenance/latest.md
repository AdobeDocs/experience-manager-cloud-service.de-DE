---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: b83d8736d47778ed133e0cc07207e02e581bbc69
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 36%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 24893 {#release-24893}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 24893, die am Mittwoch, 17. März 2026 veröffentlicht wurde. Die vorherige Wartungsversion war Version 24678.

Die Funktionsaktivierung von 2026.3.0 bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-24893}

* CNTBF-613: Zugriff verweigert (JCR-101) - Fehler beim Registrieren von Knotentypen.
* GRANITE-53957: Aktualisieren Sie Azure SDK V8 auf V12 für oak-blob-azure.
* GRANITE-57035: Verwenden Sie Bouncy Castle als standardmäßigen Sicherheitsanbieter.
* GRANITE-59249: Vermeiden Sie es, einen Sicherheitsanbieter in JVM zu registrieren.
* GRANITE-61564: Anzeigeeinstellungen für `/security/users.html` können nicht für Administratoren geöffnet werden.
* GRANITE-64748: OIDC: konfigurierbar `sling.oauth-request-key` Ablauf von Cookies.
* SITES-39767: Unterstützt den Nonce-Wert über das Anforderungsattribut (CSP).
* SKYOPS-129301: Setzen Sie die JavaDoc-Konformitätsstufe der APIs auf 17.
* GRANITE-64962: Aktualisieren Sie Apache Jackrabbit Oak auf 1.92.0.
* GRANITE-64963: Aktualisieren Sie Apache Jackrabbit Filevault auf 4.2.0.
* GRANITE-64764: Aktualisieren Sie den Apache Commons-Text auf Version 1.15.0.
* SKYOPS-131412: Aktualisieren Sie Apache Commons Exec auf 1.6.0.
* SKYOPS-131432: Felix SCR auf 2.2.14 aktualisieren.
* SKYOPS-131907: Aktualisieren der Sling-API-Region auf 1.1.10.
* SKYOPS-131938: GSON auf 2.13.2 aktualisieren.
* SKYOPS-132173: Aktualisieren des Apache Commons-Codecs auf 1.21.0.
* SKYOPS-132182: Sling-Mandant auf 1.1.8 aktualisieren.
* SKYOPS-132267: Aktualisieren Sie org.osgi.service.component auf 1.5.1.
* SKYOPS-132272: Sling-Funktionsmodell auf 2.0.4 aktualisieren.
* SKYOPS-133689: Aktualisieren Sie Dispatcher für die Verwendung von Apache httpd 2.4.66.

### Behobene Probleme {#fixed-issues-24893}

* GRANITE-64443: `workflow.core` veraltete Exporte von `log4j` entfernen.
* GRANITE-64543: Die Antwort auf Berechtigungsbeschränkungen sollte mit dem API-Vertrag übereinstimmen.

#### AEM Guides {#guides-24893}

* GUIDES-38412 : Beim Bearbeiten einer Schematron-`(*.sch)` und bei Verwendung der Funktion zum Suchen und Ersetzen wird das Bedienfeld „Suchen und Ersetzen“ unten teilweise außerhalb des Bildschirms angezeigt, wodurch der Zugriff auf die Eingabefelder und Steuerelemente verhindert wird.
* GUIDES-37806: Wenn dasselbe Thema in mehreren Zuordnungen mit unterschiedlichen bedingten Vorgaben wiederverwendet wird, überschreibt die Veröffentlichung der neuesten Zuordnung in Salesforce den Themeninhalt, was dazu führt, dass Benutzenden zuvor veröffentlichter Zuordnungen falsche Daten angezeigt werden.
* GUIDES-39394: Wenn ein Bild, das ursprünglich als sprachspezifisches Asset mit einer bestimmten Version (z. B. unter `/en/`) verwaltet wurde, in einen globalen Ordner mit einer aktualisierten Version verschoben und ein Baseline-Export durchgeführt wird, verweist die neue Baseline weiterhin auf veraltete sprachspezifische Versionen dieses Bildes, was zu einem fehlgeschlagenen Baseline-Export führt.
* GUIDES-39054: Beim Erstellen einer dynamischen Baseline reagiert der Editor manchmal aufgrund mehrerer gleichzeitiger API-Anfragen nicht mehr, wodurch alle anderen Vorgänge angehalten werden.
* GUIDES-37781: Wenn Sie einen Benutzer einer Prüfungsaufgabe zuweisen, werden in der Dropdown-Liste alle Benutzer und nicht nur die mit den ausgewählten Projekten verknüpften aufgelistet. Dies führt zu ungültigen Benutzeroptionen.
* GUIDES-39385: Beim Öffnen eines Berichts für eine Zuordnung tritt beim Laden des Bedienfelds „Filter“ eine Verzögerung auf.

Weitere Informationen zu den neuen und verbesserten Funktionen sowie zu den Problemen, die in der Version behoben wurden, finden Sie in der [Roadmap für Experience Manager Guides-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

### Bekannte Probleme {#known-issues-24893}

Keine.

### Eingestellte Funktionen und APIs {#deprecated-24893}

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

### Sicherheitskorrekturen {#security-24893}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. In dieser Wartungsversion wurden 9 identifizierte Schwachstellen behoben, was für einen noch robusteren Systemschutz sorgt.

### Eingebettete Technologien {#embedded-tech-24893}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1,92,0 | [Oak 1.92.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.92.0/index.html) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| Apache HTTP Server | 2.4.66 | [Apache httpd 2.4.66](https://apache.googlesource.com/httpd/+/refs/tags/2.4.66/CHANGES) |
| AEM-Kernkomponenten | 2,30,4 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (Standard) | [Unterstützte Node.js-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
