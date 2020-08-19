---
title: Übersicht über Testergebnisse - Cloud Services
description: Übersicht über Testergebnisse - Cloud Services
translation-type: tm+mt
source-git-commit: 25ba5798de175b71be442d909ee5c9c37dcf10d4
workflow-type: tm+mt
source-wordcount: '112'
ht-degree: 41%

---


# Übersicht {#overview}

Cloud Manager für Cloud Services -Pipeline-Ausführungen unterstützen die Ausführung von Tests, die für die Staging-Umgebung ausgeführt werden. Dies steht im Gegensatz zu Tests, die während des Build- und Unit-Testschritts ausgeführt werden, die offline ohne Zugriff auf eine laufende AEM-Umgebung durchgeführt werden.

Es gibt drei große Kategorien von Tests, die von Cloud Manager für Cloud Services-Pipeline unterstützt werden:

1. [Testen der Codequalität](/help/implementing/cloud-manager/code-quality-testing.md)
1. [Funktionstests](/help/implementing/cloud-manager/functional-testing.md)
1. [Content Audit-Tests](/help/implementing/cloud-manager/content-audit-testing.md)

Folgende Tests sind möglich:

* Vom Kunden geschriebene
* Adobe geschrieben
* Open Source-Tool (powered by Lighthouse from Google)

   >[!NOTE]
   > Sowohl kundengeschriebene Tests als auch Adoben werden in einer Containerinfrastruktur ausgeführt, die für diese Testtypen entwickelt wurde.

