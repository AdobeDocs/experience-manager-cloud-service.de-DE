---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 1a1eeb3b9aec839677baadf9bea67993a22f9519
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 45%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 22943 {#22943}

Im Folgenden finden Sie eine Zusammenfassung der fortlaufenden Verbesserungen für die Wartungsversion 22943, die am Mittwoch, 14. Oktober 2025 veröffentlicht wurde. Die vorherige Wartungsversion war Version 22758.

Die Funktionsaktivierung von 2025.10.0 bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-22943}

* ASSETS-57809: Aktualisierung der Indexdefinition für damAssetLucene-13.
* ASSETS-36521: Verbesserter Workflow zum erneuten Hochladen von DM, um eine konsistente Nachbearbeitung zu gewährleisten.
* ASSETS-56400: Neue vordefinierte Zoom-PNG-Ausgabedarstellung für Assets mit Transparenz hinzugefügt.
* ASSETS-55326: Die Konfigurationsansicht von AI-Metadatenordnern über HTTP-Ereignisse wurde aktiviert.
* ASSETS-56905: Unterstützt die Verbindung zu InDesign über einen Proxy.
* ASSETS-48286: Hinzufügen von CAI-Eigenschaften zu Algolia für GenStudio.
* ASSETS-48653: Wenden Sie das unsichtbare Wasserzeichen in der Vorverarbeitungsphase an.
* ASSETS-55874: Migrieren einer Bildvorgabe von Scene7 zu DMWithOpenapi.
* SITES-30452: Verbesserungen der Inhalts-API für ASO am Endpunkt /content/definition.

### Behobene Probleme {#fixed-issues-22943}

* ASSETS-56301: Selektiver Metadatenexport korrigiert, um PredictedTags in CSV einzuschließen.
* ASSETS-55543: Refaktorierte die asynchrone Verarbeitungslogik in einem wiederverwendbaren Bundle.
* ASSETS-54789: NPE in ACLPermissionsValidator wurde korrigiert, wenn DM-ACL aktiviert ist.
* ASSETS-55888: Im Bedienfeld Ausgabedarstellungen der Benutzeroberfläche werden jetzt keine Malware-Ausgabedarstellungen mehr angezeigt.
* GRANITE-62236: Lokalisierungsprobleme bei Keywords in gespeicherten Suchen nach Smart-Sammlungen wurden behoben.
* GRANITE-61875: Hotfix-Problem mit der „ungültigen Ausdrucksevaluierung“ behoben, das das Speichern von Inhaltsfragmenten und Asset-Downloads verhindert hat.
* SITES-24074: Die ausgeblendete mobile Navigation, die während der Tastaturregisterkartennavigation den Fokus erhält, wurde korrigiert.
* SITES-33611: Problem mit der Live Copy-Übersicht für Märkte mit hohem Volumen wurde behoben.

#### AEM Guides {#guides-22943}

* GUIDES-31421: Wenn mehrere DITA-Karten oder -Themen geöffnet und eines der Themen geschlossen ist, wird die Schaltfläche **>>** , die alle geöffneten Registerkarten anzeigt, mit den verbleibenden offenen Registerkarten in der Registerkartenleiste überlagert.
* GUIDES-33229: Beim Generieren von PDFs werden die Filterregeln in einer DITAVAL-Datei ignoriert, wenn ein Eigenschaftsname einen Punkt enthält.
* GUIDES-33720: Beim Vergrößern des Bildschirms der Übersetzungs-Benutzeroberfläche bewegt sich die Schaltfläche Zur Übersetzung senden unter den Auslassungspunkten und wird aktiviert, auch ohne dass ein Asset ausgewählt wird.
* GUIDES-33590: Wenn ein Reviewer eine Überprüfungsaufgabe abschließt oder Initiator die Überprüfungsaufgabe aktualisiert, ohne Kommentare einzugeben, zeigt die gesendete Benachrichtigungs-E-Mail den letzten vorherigen Kommentar an.

Weitere Informationen zu den neuen und verbesserten Funktionen sowie zu den Problemen, die in der Version behoben wurden, finden Sie in der [Roadmap für Experience Manager Guides-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

### Eingestellte Funktionen und APIs {#deprecated-22943}

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

### Sicherheitskorrekturen {#security-22943}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. In dieser Wartungsversion wurden 14 identifizierte Schwachstellen behoben, was für einen noch robusteren Systemschutz sorgt.

### Änderungshinweis

* Diese Version enthält die folgenden neuen Produktindex-Versionen:
* **damAssetLucene-13**

### Eingebettete Technologien {#embedded-tech-22943}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1.86.0 | [Oak 1.86.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.86/index.html) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| Apache HTTP Server | 2.4.65 | [Apache Httpd 2.4.65](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| AEM-Kernkomponenten | 2,30,2 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (Standard) | [Unterstützte Node.js-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
