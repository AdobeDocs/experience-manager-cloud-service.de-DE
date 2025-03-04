---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 30b5d5838087a35a457939cdbaa13c5735df144e
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 53%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 19823 {#19823}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 19823, die am Mittwoch, 4. März 2025 veröffentlicht wurde. Die vorherige Wartungsversion war Version 19687.

Die Funktionsaktivierung von 2025.3.0 wird den vollen Funktionsumfang für diese Wartungsversion bieten. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-19823}

* ASSETS-46491: OSGi-Ereignis-Handler für die Statusänderung der Asset-Verarbeitung.
* ASSETS-45613: Senden von Ereignissen zum Rückgängigmachen der Veröffentlichung, wenn Assets gelöscht oder verschoben werden.
* ASSETS-45131: Unterstützung benutzerdefinierter Tag-Eigenschaften in Content Hub.

### Behobene Probleme {#fixed-issues-19823}

* ASSETS-20433: Probleme bei der Dynamic Media-Aufnahme mit kennwortgeschützten PDFs.
* ASSETS-24675: Bildverarbeitungsoptionen werden für reine Musterbildprofile nicht angezeigt.
* ASSETS-41257: Asset-Versionsvergleich rendert Assets mit einem falschen Seitenverhältnis. Asset-Versionen werden in der Zeitleiste in falscher Reihenfolge angezeigt.
* ASSETS-44894: Lesezeichen für die Assets-Ansicht sind möglicherweise nicht anklickbar.
* ASSETS-45015: Breite und Höhe des smarten Zuschnitts werden auf null festgelegt, wenn der Asset-Handler für smartes Zuschneiden nicht gefunden wird.
* ASSETS-45192: Reduzieren Sie die Pulsanforderungsfrequenz.
* ASSETS-45724: Stellen Sie sicher, dass der DM-Upload wiederholt wird, wenn kein Upload-Auftrag zugewiesen ist.
* ASSETS-46425: Probleme bei der Adobe Stock-Integrationssuche.
* ASSETS-27400: Der Ordnervorschau-Generator versucht möglicherweise, das Original zu öffnen.
* CQ-4358722: Verarbeiten Sie verschiedene Gebietsschema-Codes in Java 11 und Java 17.
* SITES-29369: Nach der Aktivierung/Deaktivierung eines Assets ausgelöste Ereignisse für die Veröffentlichung/Rückgängigmachung der Veröffentlichung der Seite.
* SITES-24074: Beheben der Barrierefreiheit von Tastaturen unter Unified Shell.
* SITES-28058: Assets-Ordnertitel wird nicht in die Live Copy übertragen.

### Bekannte Probleme {#known-issues-19823}

Keine.

### Eingestellte Funktionen und APIs {#deprecated-19823}

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

### Sicherheitskorrekturen {#security-19823}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. Diese Wartungsversion behebt 6 identifizierte Schwachstellen und sorgt somit für einen noch robusteren Systemschutz.

### Eingebettete Technologien {#embedded-tech-19823}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1.76.0 | [Oak-API 1.76.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.76.0/index.html) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.26–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | 2.27.0 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
