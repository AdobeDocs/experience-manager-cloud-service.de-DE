---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 5d00bed4008c70e81f3a70d219ddc411ec8bdc59
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 94%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 21484 {#21484}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 21484, die am Freitag, 10. Juli 2025 veröffentlicht wurde. Die vorherige Wartungsversion war Version 21331.

Die Funktionsaktivierung von 2025.7.0 bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-21484}

Keine.

### Behobene Probleme {#fixed-issues-21484}

Keine.

#### AEM Guides {#guides-21484}

* GUIDES-29781: Wenn ein XML-Kommentar innerhalb eines Elements in der Quellansicht hinzugefügt wird, gehen beim Wechseln der Ansicht die führenden und nachgestellten Leerzeichen um den Kommentar verloren.
* GUIDES-29078: Wenn nach einer Browser-Aktualisierung ein Thema in der Autorenansicht geöffnet wird, werden zuvor angewendete Tags im Bedienfeld „Dateieigenschaften“ nicht beibehalten. Außerdem werden beim Hinzufügen neuer Tags die vorhandenen Tags überschrieben, insbesondere wenn eine große Anzahl von Tags zur Auswahl verfügbar ist.
* GUIDES-28214: Versuche, Überprüfungsaufgaben über den AEM-Workflow zu erstellen, schlagen konsequent fehl, da der Überprüfungsknoten nicht erstellt wird.
* GUIDES-28104: Beim Veröffentlichen einer DITA Map mit dem Attribut `chunk=to-content` werden doppelte JCR-Knoten in der neuen AEM Sites-Ausgabe erstellt, was zu einer redundanten Inhaltsstruktur in AEM Sites führt.
* GUIDES-29065, GUIDES-28793: Bei der Arbeit mit großen Sammlungen treten Leistungsprobleme wie längere Ladezeiten und zeitweise Timeouts auf.

Weitere Informationen zu den neuen und verbesserten Funktionen sowie zu den Problemen, die in der Version behoben wurden, finden Sie in der [Roadmap für Experience Manager Guides-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

### Bekannte Probleme {#known-issues-21484}

* Bei der im Software Distribution-Portal bereitgestellten SDK treten Probleme bei der lokalen Ausführung auf. Bitte die vorherige SDK für lokale Tests weiter verwenden.

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
