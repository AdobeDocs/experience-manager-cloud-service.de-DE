---
title: Informationen zu Programm- und Programm-Typen
description: Programm- und Programm-Typen - Cloud Services
translation-type: tm+mt
source-git-commit: e1d805e1e5b5850ecf3154cd69a3955c4dbe1e65
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 3%

---


# Grundlegendes zu Programmen und Programmtypen {#understanding-programs}

In Cloud Manager befindet sich die Mandant-Entität ganz oben, die mehrere Programm enthalten kann. Jedes Programm kann maximal eine Produktions-Umgebung und mehrere Nicht-Produktions-Umgebung enthalten.

Das folgende Diagramm zeigt die Hierarchie der Entitäten in Cloud Manager.

![image](assets/program-types1.png)

## Programm-Typen {#program-types}

Ein Benutzer kann ein **Sandbox**- oder ein **Production**-Programm erstellen.

* Ein *Produktions-Programm* wird erstellt, um Live-Traffic zum richtigen Zeitpunkt in der Zukunft zu aktivieren.
Weitere Informationen finden Sie unter [Einführung in die Produktions-Programm](/help/onboarding/getting-access-to-aem-in-cloud/introduction-production-programs.md).


* Ein *Sandbox-Programm* wird normalerweise für Schulungszwecke, die Ausführung von Demos, die Aktivierung, POCs oder Dokumentation erstellt. Es soll keinen Live-Traffic transportieren und wird Beschränkungen unterliegen, die ein reguläres Programm nicht hat. Es umfasst Sites und Assets und wird automatisch mit einer Git-Verzweigung geliefert, die Beispielcode, eine Dev-Umgebung und eine Nicht-Produktions-Pipeline enthält.
Weitere Informationen finden Sie unter [Einführung in Sandbox-Programm](/help/onboarding/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md).

