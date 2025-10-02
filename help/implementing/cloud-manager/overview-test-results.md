---
title: Übersicht über Cloud Manager-Tests
description: Verschaffen Sie sich einen Überblick über die drei Arten von Tests, die Cloud Manager automatisch durchführt, um die Qualität Ihres benutzerdefinierten Codes sicherzustellen.
exl-id: 5f5c97b1-4180-4f49-af8b-257d4744766e
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: ac918008c3f99d74e01be59c9841083abf3604aa
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 62%

---


# Übersicht über Cloud Manager-Tests {#overview}

Es gibt drei allgemeine Testkategorien, die von Cloud Manager für Cloud Services-Pipelines unterstützt werden.

1. [Testen der Code-Qualität](/help/implementing/cloud-manager/code-quality-testing.md)

   * Code-Qualitätstests bewerten die Qualität Ihres Anwendungs-Codes.
   * Die Code-Qualitäts-Pipeline wird unmittelbar nach dem Build-Schritt in allen produktionsfremden und Produktions-Pipelines ausgeführt.
   * Die [Qualitätsregeln für benutzerspezifischen Code](/help/implementing/cloud-manager/custom-code-quality-rules.md), die von Cloud Manager ausgeführt werden, werden auf der Grundlage bewährter Verfahren von AEM Engineering erstellt.

1. [Funktionstests](/help/implementing/cloud-manager/functional-testing.md)

   * Funktionstests werden während der Staging-Testphase einer [Produktions-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) ausgeführt. Optional kann sie auch während der Testphase einer [produktionsfremden Pipeline“ ausgeführt ](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md).

1. [Testen mit Erlebnis-Audit](/help/implementing/cloud-manager/reports/report-experience-audit.md)

   * Experience Audit-Tests sind in allen Cloud Manager-Produktions-Pipelines aktiviert und können nicht übersprungen werden.

Diese Tests können folgendermaßen sein:

* Vom Kunden geschrieben
* Von Adobe geschrieben
* Erstellt mit Open-Source-Tools

>[!NOTE]
>
> Sowohl von Kundinnen und Kunden als auch von Adobe geschriebene Tests werden in einer Container-Infrastruktur ausgeführt, die für die Durchführung solcher Tests konzipiert wurde.
