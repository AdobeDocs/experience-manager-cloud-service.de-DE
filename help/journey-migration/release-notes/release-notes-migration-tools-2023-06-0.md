---
title: Versionshinweise für Migrations-Tools in AEM as a Cloud Service Version 2023.06.0
description: Versionshinweise für Migrations-Tools in AEM as a Cloud Service Version 2022.06.0
feature: Release Information
exl-id: 021b7472-d1e4-4ef6-a040-c612fed8d3c3
source-git-commit: 0109cea1be85e647fb6c04dde4714b162bdc75a5
workflow-type: ht
source-wordcount: '237'
ht-degree: 100%

---

# Versionshinweise für Migrations-Tools in AEM as a Cloud Service Version 2023.06.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Migrations-Tools in AEM as a Cloud Service Version 2022.06.0.

## Content Transfer Tool {#ctt-release}

### Veröffentlichungsdatum {#release-date-ctt}

Das Content Transfer Tool Version 2.0.20 wurde am 08. Juni 2023 veröffentlicht.

### Neue Funktionen {#what-is-new-ctt}

* Mit dieser Version wurde ein neues Migrationswerkzeug – Content Transformer (CT) – in das Content Transfer Tool (CTT) integriert. Der Content Transformer kann automatisch inhaltsbezogene Probleme erkennen und beheben, die vom [Best Practices Analyzer (BPA)](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=de) gemeldet werden, bevor Sie Inhalte von Ihrer aktuellen AEM-Implementierung (On-Premise oder über Managed Services) zu AEM as a Cloud Service migrieren.
Der Content Transformer bietet folgende Vorteile:
   * Ausfallsicher: Es wird vom Content Transformer jedes Mal ein Paket erstellt, wenn er Änderungen am Repository vornimmt, um Probleme zu beheben. Bei Bedarf können Sie den vorherigen Status wiederherstellen, indem Sie das Paket installieren.
   * Benutzerfreundlich: Der Content Transformer wurde in das Content Transfer Tool integriert und verfügt über eine einfache, intuitive Benutzeroberfläche.
   * Zeitsparend: Wenn Sie eine große Anzahl von Inhaltsproblemen haben, die unter eine Musterkategorie fallen, können Sie alle mit dem Content Transformer mit nur wenigen Klicks lösen, was den Zeitaufwand und die Komplexität der Migration erheblich reduziert.
