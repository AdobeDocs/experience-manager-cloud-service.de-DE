---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: ff500e08e31e53f5452eed6cfe06539cabe2ecdd
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 62%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 21484 {#21484}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 21484, die am Mittwoch, 8. Juli 2025 veröffentlicht wurde. Die vorherige Wartungsversion war Version 21331.

Die Funktionsaktivierung von 2025.7.0 bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-21484}

Keine.

### Behobene Probleme {#fixed-issues-21484}

Keine.

#### AEM Guides {#guides-21484}

* GUIDES-29781: Wenn ein XML-Kommentar innerhalb eines Elements in der Source-Ansicht hinzugefügt wird, gehen die führenden und nachfolgenden Leerzeichen um den Kommentar verloren, wenn die Ansicht gewechselt wird.
* GUIDES-29078: Beim Öffnen eines Themas in der Autorenansicht nach einer Browser-Aktualisierung werden zuvor angewendete Tags im Bedienfeld Dateieigenschaften nicht beibehalten und das Hinzufügen neuer Tags überschreibt die vorhandenen, insbesondere wenn eine große Anzahl von Tags zur Auswahl verfügbar ist.
* GUIDES-28214: Versuche, Überprüfungsaufgaben über den AEM-Workflow zu erstellen, schlagen konsequent fehl, da der Überprüfungsknoten nicht erstellt wird.
* GUIDES-28104: Beim Veröffentlichen einer DITA-Zuordnung mit `chunk=to-content` Attribut werden doppelte JCR-Knoten in der neuen AEM Sites-Ausgabe erstellt, was zu einer redundanten Inhaltsstruktur in AEM Sites führt.
* GUIDES-29065, GUIDES-28793: Bei der Arbeit mit großen Sammlungen treten Leistungsprobleme wie längere Ladezeiten und intermittierende Zeitüberschreitungen auf.

Weitere Informationen zu den neuen und verbesserten Funktionen sowie zu den Problemen, die in der Version behoben wurden, finden Sie in der [Roadmap für Experience Manager Guides-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

### Bekannte Probleme {#known-issues-21484}

Keine.

### Eingestellte Funktionen und APIs {#deprecated-21484}

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

### Sicherheitskorrekturen {#security-21484}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. Diese Wartungsversion behebt 5 identifizierte Schwachstellen und sorgt somit für einen noch robusteren Systemschutz.

### Eingebettete Technologien {#embedded-tech-21484}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1.80.0 | [Oak-API 1.80.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.80.0/index.html) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.28–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | 2.29.0 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
