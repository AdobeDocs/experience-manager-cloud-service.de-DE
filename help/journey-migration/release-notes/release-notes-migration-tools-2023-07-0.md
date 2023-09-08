---
title: Versionshinweise für Migrations-Tools in AEM as a Cloud Service Version 2023.07.0
description: Versionshinweise für Migrations-Tools in AEM as a Cloud Service Version 2022.07.0
feature: Release Information
exl-id: 2f787321-f156-480d-bbe8-1a6d04f110c5
source-git-commit: 1f01408223a661c0149d959b1901293dc91ed7ee
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 46%

---

# Versionshinweise für Migrations-Tools in AEM as a Cloud Service Version 2023.07.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Migrations-Tools in AEM as a Cloud Service Version 2022.07.0.

## Best Practices Analyzer {#bpa-release}

### Veröffentlichungsdatum {#release-date-bpa}

Best Practices Analyzer v2.1.42 wurde am 06. Juli 2023 veröffentlicht.

### Neue Funktionen {#what-is-new-bpa}

* In dieser Version von Best Practices Analyzer wurden mehrere Best Practices-Muster hinzugefügt. Dazu gehören:
   * Ermitteln der Mindestkonfiguration für Wartungsaufgaben
   * Erkennung langwieriger/schwerer Abfragen
   * Erkennen einer hohen Anzahl von Autoren-Workflows im ausgeführten oder veralteten Zustand
   * Erkennen der OSGI-Apache Sling-Auftragskonfiguration
   * Erkennung benutzerdefinierter Guava-Caches

### Fehlerbehebungen {#bug-fixes-bpa}

* BPA wurde verbessert, um Fehler bei der Generierung von Berichten mit hoher Anzahl von Ergebnissen zu vermeiden.
* BPA wurde verbessert, um Escape-Zeichen in Pfaden zu erkennen, um Inhaltsaufnahmefehler bei der Migration von Inhalten auf AEM as a Cloud Service zu verhindern.
