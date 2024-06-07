---
title: Versionshinweise für Migrations-Tools in AEM as a Cloud Service Version 2023.07.0
description: Versionshinweise für Migrations-Tools in AEM as a Cloud Service Version 2023.07.0
feature: Release Information
exl-id: 2f787321-f156-480d-bbe8-1a6d04f110c5
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: ht
source-wordcount: '164'
ht-degree: 100%

---

# Versionshinweise für Migrations-Tools in AEM as a Cloud Service Version 2023.07.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Migrations-Tools in AEM as a Cloud Service Version 2023.07.0.

## Best Practices Analyzer {#bpa-release}

### Veröffentlichungsdatum {#release-date-bpa}

Best Practices Analyzer v2.1.42 wurde am 06. Juli 2023 veröffentlicht.

### Neue Funktionen {#what-is-new-bpa}

* Dieser Version von Best Practices Analyzer wurden mehrere Best Practices-Muster hinzugefügt. Dazu gehören:
   * Ermitteln von Mindestkonfigurationen für Wartungsaufgaben
   * Erkennen langwieriger/umfangreicher Abfragen
   * Erkennen einer hohen Anzahl der laufenden und veralteten Autoren-Workflows.
   * Erkennen der OSGI-Apache Sling-Vorgangskonfiguration
   * Erkennen benutzerdefinierter Guava-Caches

### Fehlerbehebungen {#bug-fixes-bpa}

* BPA wurde verbessert, um Fehler bei der Generierung von Speicherberichten mit einer hohen Anzahl von Ergebnissen zu vermeiden.
* BPA wurde verbessert, um Escape-Zeichen in Pfaden zu erkennen, um Inhaltsaufnahmefehler bei der Migration von Inhalten auf AEM as a Cloud Service zu verhindern.
