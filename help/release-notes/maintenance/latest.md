---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 68444ac15513bad7c1eaee97c474e21d36992d49
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 42%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 23482 {#23482}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 23482, die am Donnerstag, 3. Dezember 2025 veröffentlicht wurde. Die vorherige Wartungsversion war Version 23385.

Die Funktionsaktivierung von 2025.12.0 bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).


### Verbesserungen {#enhancements-23482}

* ASSETS-49770: Quarantänebenachrichtigungen für Ergebnisse der Malware-Suche hinzufügen.
* ASSETS-54079: Benutzerdefiniertes Metadatenformular für Quarantäneordner anwenden.
* ASSETS-54083: Erstellen eines geplanten Quarantänebereinigungsmechanismus.
* ASSETS-54278: Entfernen der `dam:avScanTime` aus Assets.
* ASSETS-57284: Datei-Uploads auf Quarantäne-Ordner beschränken (Ziehen und Ablegen deaktivieren).
* ASSETS-57428: Quarantäneordner in der Benutzeroberfläche der Assets-Ansicht ausblenden.
* ASSETS-57626: Verbessern Sie das Wiederholungsverhalten für asynchrone Asset-Aufträge.
* ASSETS-57879: Zusammenführungsoption für asynchrone Aufträge zum Verschieben/Kopieren von Assets hinzufügen.
* ASSETS-58099: Fügen Sie die Konfiguration hinzu, um erweiterte Smart-Tags für die gesamte Umgebung zu deaktivieren.
* ASSETS-58136: Implementieren des Feedbacks zu Seitenumbrüchen in der OpenAPI-Suche.
* ASSETS-59402: Hinzufügen asynchroner Auftrags-Endpunkte für die Ordnerlöschungs-API: Exportieren von Paketen in eine interne Region.
* ASSETS-59966: Die Gruppe der Malware-Administratoren in Quarantäne-Administratoren umbenennen.
* ASSETS-60166: Verwenden Sie VideoViewer.js anstelle von iframe-basierten URLs.
* GRANITE-61378: Tools zum Debuggen von Berechtigungen - ListPrincipals-API.
* GRANITE-63235: Abfrage zur Identifizierung von Sites mithilfe `cq:conf` -Eigenschaft, unterstützt die Erkennung alter Seiten/Versionen.
* SITES-30452: Inhalts-API mit ASO - Vorschläge für Titel und Beschreibungen, XWalk-Unterstützung, JSON-Patch-Vorgänge, IMS-Service-Prinzipalbindung.

### Behobene Probleme {#fixed-issues-23482}

* ASSETS-57430: Fehlerbehebung beim Hochladen der Assets-Ansicht, Vorverarbeitung wird übersprungen: `repoapi.preprocessing`-Paket exportieren, RAPI auf den neuesten Stand aktualisieren.
* ASSETS-58190: Reduzieren Sie unnötigerweise hohe Schätzwerte in der Benutzeroberfläche für Sammlungen.
* ASSETS-58866: Korrigieren Sie den Asset-Titel/die Beschreibung/ID, die in OpenAPI-Antworten zurückgegeben wird.
* ASSETS-58868: Paginierung korrigieren, wenn in Assets Felder fehlen.
* ASSETS-58920: Korrektur des Massenimports von Assets, wobei die Vorverarbeitung übersprungen wird.
* ASSETS-59168: Die Start-/Endzeit für den Scan korrigieren, wenn eine falsche Zeitzone angezeigt wird.
* ASSETS-59702: Fehlerkorrektur - Die Ereignisreihenfolge wird nicht mehr korrigiert, wenn der Asset-Status auf „Kein Status“ gesetzt ist.
* ASSETS-59830: Asynchrone Aufträge in die Warteschlange stellen, die beim Beenden des Pod angehalten wurden.
* ASSETS-49757: Fehlerbehebungen bei Malware Detection Scan Events.
* GRANITE-61019: Fehlerbehebung `gcMonitor` beim ersten Ausführen nach einem Neustart von AEM nicht benachrichtigt.
* GRANITE-62717: Beheben `JSafe` Kennwortbehandlung mit Nicht-ASCII-Zeichen.
* SITES-34331: Rollout-Überlagerung beim Laden mit Timeout 503 für Benutzende ohne Administratorrechte (`cqLiveSyncCancelled index`) wurde behoben.

### Bekannte Probleme {#known-issues-23482}

Keine.

### Eingestellte Funktionen und APIs {#deprecated-23482}

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

### Sicherheitskorrekturen {#security-23482}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. Diese Wartungsversion behebt vier identifizierte Schwachstellen und sorgt somit für einen noch robusteren Systemschutz.

### Eingebettete Technologien {#embedded-tech-23482}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1,88,0 | [Oak 1.88.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.88/index.html) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| Apache HTTP Server | 2.4.65 | [Apache Httpd 2.4.65](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| AEM-Kernkomponenten | 2,30,2 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (Standard) | [Unterstützte Node.js-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |

