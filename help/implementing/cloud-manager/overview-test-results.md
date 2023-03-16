---
title: Überblick über Cloud Manager-Tests
description: Verschaffen Sie sich einen Überblick über die drei Arten von Tests, die Cloud Manager automatisch durchführt, um die Qualität Ihres benutzerspezifischen Codes sicherzustellen.
exl-id: 5f5c97b1-4180-4f49-af8b-257d4744766e
source-git-commit: 94f818b7622e0f878d15ba30e2f07a169bd114c3
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 8%

---


# Überblick über Cloud Manager-Tests {#overview}

Es gibt drei Testkategorien, die von Cloud Manager für Cloud Services-Pipelines unterstützt werden.

1. [Testen der Code-Qualität](/help/implementing/cloud-manager/code-quality-testing.md)

   * Beim Code-Qualitätstest wird die Qualität Ihres Anwendungs-Codes bewertet.
   * Die Code-Qualitäts-Pipeline wird unmittelbar nach dem Build-Schritt in allen Nicht-Produktions- und Produktions-Pipelines ausgeführt.
   * Die [benutzerspezifische Code-Qualitätsregeln](/help/implementing/cloud-manager/custom-code-quality-rules.md) die von Cloud Manager ausgeführt werden, basieren auf Best Practices von AEM Engineering.

1. [Funktionstests](/help/implementing/cloud-manager/functional-testing.md)

   * Funktionstests sind Teil der Staging-Testphase eines [Produktions-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) und optional Teil der Testphase eines [produktionsfremde Pipeline.](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md)

1. [Testen mit Experience Audit](/help/implementing/cloud-manager/experience-audit-testing.md)

   * Der Erlebnisprüfungstest ist in allen Cloud Manager-Produktions-Pipelines aktiviert und kann nicht übersprungen werden.

Diese Tests können folgendermaßen sein:

* Vom Kunden geschrieben
* Von Adobe geschrieben
* Erstellt mit Open-Source-Tools

>[!NOTE]
>
> Sowohl von Kunden geschriebene Tests als auch von Adoben geschriebene Tests werden in einer Container-Infrastruktur ausgeführt, die für solche Tests entwickelt wurde.
