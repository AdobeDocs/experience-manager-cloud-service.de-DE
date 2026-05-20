---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: c8303f6792f36e9d1942cf398909cbf0b3f3f90f
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 30%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## 26125 {#release-26125}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 26125, die am 20. Mai 2026 veröffentlicht wurde. Die vorherige Wartungsversion war Version 25892.

Die Aktivierung von Funktionen in 2026.5.0 stellt den vollständigen Funktionssatz für diese Wartungsversion bereit. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-26125}

* ASSETS-56957: Unterstützung für Mehrfach-Audiospuren und Mehrfach-Untertitel-Uploads für Videos in Dynamic Media mit OpenAPI hinzugefügt.
* ASSETS-58563: Adobe Commerce-Integration zu AEM Assets hinzugefügt.
* ASSETS-65603: Verbesserte Leistung bei der Ordnerauflistung in der Touch-optimierten Benutzeroberfläche durch Konfiguration einer reduzierten Asset-Anzahl.
* ASSETS-66032: Erweiterte Netzwerk-Proxy-Unterstützung für Assets Bulk Import für Umgebungen mit IP-eingeschränktem Cloud-Speicher hinzugefügt.
* CQ-4363346: Die Benutzeroberfläche für Übersetzungsrichtlinien wurde um Unterstützung für das Herunterladen von Beispielrichtlinien, das Hochladen von Richtliniendateien in den Formaten JSON, PDF und DOCX und das Löschen vorhandener Richtlinien erweitert.
* GRANITE-67514: Isoliert ein internes Caching-Bibliotheks-Bundle, um Fehler bei Transformationsvorgängen und Konflikte mit kundenbereitgestellten Bundles zu verhindern.
* SITES-42076: Experimentell: Es wurden Massenvorgänge zum Suchen und Ersetzen für Seiten als MCP-Primitive in der Inhalts-API hinzugefügt.
* SITES-42835: Experimentell: AEM Forms-Seiten, die außerhalb der Content-API erstellt wurden, sind jetzt über die AEM Sites Content-API zugänglich, ohne dass Migrations- oder Schemaänderungen erforderlich sind.
* SITES-44265: Der Inhalts-API wurde eine stabile replizierte Seitenkennung hinzugefügt, die nach Seitenverschiebungen gültig bleibt, sodass veraltete Referenz-404-Fehler vermieden werden.

### Behobene Probleme {#fixed-issues-26125}

* ASSETS-36208: Feste Bildprofile werden nicht in den Ordnereigenschaften angezeigt, wenn Dynamic Media deaktiviert ist.
* ASSETS-63240: Massenvorgänge zur Mehrfachauswahl im Append-Modus wurden korrigiert, bei denen Benutzende auf einer leeren Seite blieben, anstatt zur Assets-Konsole zurückzukehren.
* ASSETS-65076: Es wurde ein falscher Protokollwert behoben, der an die Externalizer-API übergeben wurde und zu Fehlern bei der Verwendung von Sling-Anfrage-Buildern führte.
* ASSETS-66102: Es wurde ein Problem mit Adobe I/O Runtime Asset-Veröffentlichungsereignissen behoben, bei denen ein falscher `repo:version` gemeldet wurde, was zu Fehlern bei nachgelagerten Integrationen führte.
* ASSETS-66226: Anlagen werden beim Löschen nicht aus der Versandebene entfernt, wenn ihr Genehmigungsstatus mit gemischten Werten gespeichert wurde.
* ASSETS-66669: Die Schaltfläche „Startseite“ auf der Suchergebnisseite navigiert jetzt, wenn Unified Shell aktiviert ist, nicht mehr zum Startbildschirm in der Touch-optimierten Benutzeroberfläche.
* ASSETS-66683: Es wurde eine Genehmigungsschleife in Dynamic Media behoben, bei der OpenAPI durch Upload-Fehler ausgelöst wurde, die zu Rückstaus und gestörten Asset-Genehmigungs-Workflows führten.
* ASSETS-67113: Massenimport wurde behoben, bei dem SVG-Assets beim Filtern nach MIME-Typ `image/svg+xml` ignoriert wurden.
* CQ-4363466: Es wurden Fehler bei der Auflösung des Cloud-Konfigurationspfads behoben, die Auswirkungen auf Übersetzungs-Connectoren von Drittanbietern hatten, die eine benutzerdefinierte Konfigurationsauflösung verwenden.
* CQ-4363355: Übersetzungsanfragen im GenAI Translation Connector wurden korrigiert, die aufgrund einer hartcodierten statischen URL an einen falschen regionalen Endpunkt weitergeleitet wurden.
* SITES-44186: Meta-Tag-Einschleusung in die Ereignisverarbeitung des Seiten-Editors durch Autoren wurde korrigiert.

### Bekannte Probleme {#known-issues-26125}

Keine.

### Eingestellte Funktionen und APIs {#deprecated-26125}

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

### Sicherheitskorrekturen {#security-26125}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. Diese Wartungsversion behebt 19 Schwachstellen und verstärkt unser Engagement für zuverlässigen Systemschutz.

### Eingebettete Technologien {#embedded-tech-26125}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 2.0.0 | [Oak 2.0.0-API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/2.0.0/index.html) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| Apache HTTP Server | 2.4.65 | [Apache Httpd 2.4.65](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| AEM-Kernkomponenten | 2.30.4 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (Standard) | [Unterstützte Node.js-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
