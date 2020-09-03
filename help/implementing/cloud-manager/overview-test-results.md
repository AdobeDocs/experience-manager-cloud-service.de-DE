---
title: Übersicht über Testergebnisse - Cloud Services
description: Übersicht über Testergebnisse - Cloud Services
translation-type: tm+mt
source-git-commit: d03ef0afe91760e35ef4e8fb3e3f2c833cbf945c
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 2%

---


# Überblick {#overview}

Es gibt drei große Kategorien von Tests, die von Cloud Manager für Cloud Services-Pipeline unterstützt werden:

1. [Testen der Code-Qualität](/help/implementing/cloud-manager/code-quality-testing.md)

   Die Codequalitätsprüfung bewertet die Qualität Ihres Anwendungscodes. Die Code-Quality-Pipeline wird unmittelbar nach dem Build-Schritt in allen Nicht-Produktions- und Produktionsleitungen ausgeführt.

   The [Custom Code Quality Rules](/help/implementing/cloud-manager/custom-code-quality-rules.md) executed by Cloud Manager are created based on best practices from AEM Engineering.

1. [Funktionstests](/help/implementing/cloud-manager/functional-testing.md)

   Der Funktionstest ist Teil der Testphase einer Produktionsleitung.

1. [Test der Erlebnis-Prüfung](/help/implementing/cloud-manager/experience-audit-testing.md)

   Der Experience Audit-Test ist in allen Cloud Manager-Produktionsleitungen aktiviert und kann nicht übersprungen werden.

Folgende Tests sind möglich:

* Vom Kunden geschriebene
* Adobe geschrieben
* Open Source-Tool

   >[!NOTE]
   > Sowohl kundengeschriebene Tests als auch Adoben werden in einer Containerinfrastruktur ausgeführt, die für diese Testtypen entwickelt wurde.

