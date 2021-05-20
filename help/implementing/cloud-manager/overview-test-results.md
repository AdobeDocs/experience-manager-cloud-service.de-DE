---
title: Überblick über Testergebnisse – Cloud Services
description: Überblick über Testergebnisse – Cloud Services
exl-id: 5f5c97b1-4180-4f49-af8b-257d4744766e
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 100%

---

# Überblick {#overview}

Es gibt drei allgemeine Testkategorien, die von Cloud Manager für Cloud Services-Pipeline unterstützt werden:

1. [Testen der Code-Qualität](/help/implementing/cloud-manager/code-quality-testing.md)

   Beim Testen der Code-Qualität wird die Qualität Ihres Anwendungs-Codes bewertet. Die Code-Qualitäts-Pipeline wird in allen produktionsfremden und Produktions-Pipelines unmittelbar nach dem Build-Schritt ausgeführt.

   Auf dieser Seite werden die [benutzerspezifischen Regeln für die Code-Qualität](/help/implementing/cloud-manager/custom-code-quality-rules.md) beschrieben, die von Cloud Manager ausgeführt werden und auf bewährten Verfahren des AEM Engineering basieren.

1. [Funktionstests](/help/implementing/cloud-manager/functional-testing.md)

   Funktionstests sind Teil der Staging-Testphase einer Produktions-Pipeline.

1. [Testen mit Experience Audit](/help/implementing/cloud-manager/experience-audit-testing.md)

   Das Testen mit Experience Audit ist in allen Cloud Manager-Produktions-Pipelines aktiviert und kann nicht übersprungen werden.

Diese Tests können folgendermaßen sein:

* Vom Kunden geschrieben
* Von Adobe geschrieben
* Open-Source-Tool

   >[!NOTE]
   > Sowohl vom Kunden als auch von Adobe geschriebene Tests werden in einer Container-Infrastruktur ausgeführt, die für diese Testtypen entwickelt wurde.
