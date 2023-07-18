---
title: Versionshinweise für Migrations-Tools in AEM as a Cloud Service Version 2023.06.0
description: Versionshinweise für Migrations-Tools in AEM as a Cloud Service Version 2022.06.0
feature: Release Information
source-git-commit: 88227693b7dfc3cbd30751718dc85e55ee67bb96
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 33%

---

# Versionshinweise für Migrations-Tools in AEM as a Cloud Service Version 2023.06.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Migrations-Tools in AEM as a Cloud Service Version 2022.06.0.

## Content Transfer Tool {#ctt-release}

### Veröffentlichungsdatum {#release-date-ctt}

Das Content Transfer Tool 2.0.20 wurde am 08. Juni 2023 veröffentlicht.

### Neue Funktionen {#what-is-new-ctt}

* Mit dieser Version wurde ein neues Migrationswerkzeug - Content Transformer (CT) - in das Content Transfer Tool (CTT) integriert. Der Content Transformer kann Inhaltsbezogene Probleme, die von der [Best Practices Analyzer (BPA)](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=de) vor der Migration von Inhalten von Ihrer aktuellen AEM-Implementierung (On-Premise oder Managed Services) zu AEM as a Cloud Service.
Der Content Transformer bietet folgende Vorteile:
   * Fail-Safe: Ein Paket wird vom Content Transformer jedes Mal erstellt, wenn er Änderungen am Repository vornimmt, um Probleme zu beheben. Bei Bedarf können Sie den vorherigen Status wiederherstellen, indem Sie das Paket installieren.
   * Benutzerfreundlich: Der Content Transformer wurde in das Content Transfer Tool integriert und verfügt über eine intuitive, einfache Benutzeroberfläche.
   * Speichert Zeit: Wenn Sie eine große Anzahl von Inhaltsproblemen haben, die unter eine Musterkategorie fallen, können Sie alle mit nur wenigen Klicks mit dem Content Transformer beheben, wodurch Zeit und Migrationsprobleme erheblich reduziert werden.
