---
title: Versionshinweise für Migrations-Tools in AEM as a Cloud Service Version 2024.05.0
description: Versionshinweise für Migrations-Tools in AEM as a Cloud Service Version 2024.05.0
feature: Release Information
role: Admin
exl-id: f50a74fa-ad7d-4837-b0a1-9945c32af02f
source-git-commit: 3b2ed44b438fe8587a9b9603ddfacc41111fb903
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 100%

---

# Versionshinweise für Migrations-Tools in AEM as a Cloud Service Version 2024.05.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Migrations-Tools in AEM as a Cloud Service Version 2024.05.0.

## Best Practices Analyzer {#bpa-release}

### Veröffentlichungsdatum {#release-date-bpa}

Best Practices Analyzer v2.1.50 wurde im Mai 2024 veröffentlicht.

### Neue Funktionen {#what-is-new-bpa}

* Der Best Practices Analyzer (BPA) unterstützt jetzt das automatische Hochladen von BPA-generierten Berichten direkt in Cloud Acceleration Manager (CAM). Benutzende müssen den Bericht nicht mehr manuell herunterladen und in CAM hochladen. Weitere Informationen finden Sie unter [Verwenden von Best Practices Analyzer](/help/journey-migration/best-practices-analyzer/using-best-practices-analyzer.md)

### Fehlerbehebungen {#bug-fixes-bpa}

* Der Best Practices Analyzer erkennt jetzt alle Knoten, die größer sind als 16 MB
* Eine Wettlaufsituation, die zu sporadischen Vorkommnissen von NCC-Befunden führte, wurde korrigiert.

## Cloud Acceleration Manager {#cam-release}

### Neue Funktionen {#what-is-new-cam}

* Cloud Acceleration Manager (CAM) unterstützt jetzt das automatische Hochladen von BPA-generierten Berichten direkt in CAM. Weitere Informationen finden Sie unter [Phase „Bereitschaft“ in Cloud Acceleration Manager – Verwenden der Karte „Best-Practices-Analyse“](/help/journey-migration/cloud-acceleration-manager/using-cam/cam-readiness-phase.md#best-practices-analysis)

* Cloud Acceleration Manager bietet jetzt eine Schätzung der möglichen Dauer einer Aufnahme, abhängig von Faktoren wie Knotenanzahl, Datenspeichergröße usw. Erfahren Sie mehr über das [Aufnehmen von Inhalten in Cloud Service](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md)
