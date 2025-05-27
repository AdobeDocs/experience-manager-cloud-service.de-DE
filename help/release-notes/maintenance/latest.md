---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: e1fa4b3bcb04ab3e834b34f507f1350fb536b513
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 51%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 21005 {#21005}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 21005, die am Mittwoch, 27. Mai 2025 veröffentlicht wurde. Die vorherige Wartungsversion war Version 20626.

Die Funktionsaktivierung von 2025.5.0 wird den vollen Funktionsumfang für diese Wartungsversion bieten. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-21005}

* GRANITE-58927: Verbesserungen am Umschalter für die semantische Suche.
* GRANITE-58800: Aktualisierung von Apache Commons-Sammlungen auf Version 4.5.0.
* GRANITE-58866: Update von Oak auf 1.80.0.
* SKYOPS-106509: Verbesserte GSON-Kompatibilität durch reflektierenden Zugriff in Java 21.
* SKYOPS-107761: Aktualisierung der Sling-Modelle Jackson Exporter auf 1.1.6.
* SKYOPS-107813: Update auf Sling ResourceResolver 1.12.8.

### Behobene Probleme {#fixed-issues-21005}

* CNTBF-443: Die SearchSlingJob-`EVENT_JOB_TOPIC` wurde korrigiert.
* GRANITE-57853: Es wurden Probleme bei der Dropdown-Ausrichtung in der Benutzeroberfläche behoben.
* GRANITE-58107: Es wurden 404-Fehler bei der Veröffentlichung behoben, indem die benutzerbasierte Pod-Affinität im OAuth-Handler deaktiviert wurde.
* GRANITE-58276, SLING-12755: Es wurden OSGi-Abhängigkeitszyklen korrigiert, die verhindern konnten, dass die HTL Script Engine-Factory korrekt gestartet wurde, was zu zeitweiligen Server-seitigen Rendering-Fehlern führte.
* SKYOPS-105151: NPE beim Zugriff auf die Bundle-Liste wurde korrigiert.
* SKYOPS-83910, SKYOPS-82371 - Es wurden Probleme mit gleichzeitiger JSP-Kompilierung behoben.

#### AEM Guides {#guides}

* GUIDES-26919 : Beim Öffnen einer DITA-Map mit aktivierter Unified Shell wird der Editor gelegentlich aktualisiert.
* GUIDES-26282: Wenn JCR-Sitzungsverbindungen beim Aktualisieren oder Erstellen von Themen nicht geschlossen werden, führt dies zu Speicherlecks und Service-Ausfallzeiten.
* GUIDES-26434: Die native PDF-Veröffentlichung wird auf unbestimmte Zeit fortgesetzt, wenn der DITA-Inhalt über einen Weblink verfügt, ohne über den `external` Umfang zu verfügen.
* GUIDES-26516: Die Veröffentlichung von nativen PDFs und AEM-Sites verzögert sich und wird in die Warteschlange gestellt, wenn Fehler im Inhalt auftreten.

Weitere Informationen zu den neuen und verbesserten Funktionen sowie zu den Problemen, die in der Version behoben wurden, finden Sie in der [Roadmap für Experience Manager Guides-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

### Bekannte Probleme {#known-issues-21005}

Keine.

### Eingestellte Funktionen und APIs {#deprecated-21005}

* GRANITE-54164: `org.apache.jackrabbit.oak.plugins.blob` aus der öffentlichen API entfernt.
* GRANITE-54280: `org.apache.jackrabbit.oak.cache` aus der öffentlichen API entfernt.
* GRANITE-58332: Veraltete `org.apache.jackrabbit.oak.plugins.memory` in der öffentlichen API.
* Die Funktion [Experience Cloud Setup Automation](/help/sites-cloud/integrating/adobe-analytics-exc-setup-automation.md) wird nicht mehr unterstützt.

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

### Sicherheitskorrekturen {#security-21005}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. Diese Wartungsversion behebt 5 identifizierte Schwachstellen und sorgt somit für einen noch robusteren Systemschutz.

### Änderungshinweis {#change-notice-21005}

* Diese Version enthält die folgenden neuen Produktindex-Versionen:
   * **damAssetLucene-12**

Benutzerdefinierte Versionen der vorherigen Indexversionen werden automatisch mit der neuen Produktindex-Version zusammengeführt. Wenden Sie weitere benutzerdefinierte Aktualisierungen auf die zusammengeführte Version an.

#### Aktualisieren von aem-cloud-testing-clients {#update-aem-cloud-testing-clients-21005}

Für bevorstehende Änderungen muss die Bibliothek [aem-cloud-testing-clients](https://github.com/adobe/aem-testing-clients), die in Ihren benutzerdefinierten Funktionstests verwendet wird, mindestens auf Version **1.2.1 aktualisiert werden** (empfohlen: neueste Version 1.2.9)

Stellen Sie sicher, dass Ihre Abhängigkeit in `it.tests/pom.xml` aktualisiert wurde.

```xml
<dependency>
   <groupId>com.adobe.cq</groupId>
   <artifactId>aem-cloud-testing-clients</artifactId>
   <version>1.2.9</version>
</dependency>
```

Diese Änderung muss vor dem 15. Juni 2025 durchgeführt werden.
Wenn die Abhängigkeitsbibliothek nicht aktualisiert wird, treten Pipeline-Fehler beim Schritt „Benutzerdefinierte Funktionstests“ auf.

### Eingebettete Technologien {#embedded-tech-21005}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1,80,0 | [Oak-API 1.80.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.80.0/index.html) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28-1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | 2.29.0 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
