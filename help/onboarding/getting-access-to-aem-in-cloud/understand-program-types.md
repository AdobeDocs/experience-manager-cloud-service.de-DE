---
title: Informationen zu Programm- und Programm-Typen
description: Programm- und Programm-Typen - Cloud-Services
translation-type: tm+mt
source-git-commit: 14da491cf09ed46ea425a8d65670d8b851aef388
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 3%

---


# Grundlegendes zu Programmen und Programmtypen {#understanding-programs}

In Cloud Manager befindet sich die Mandant-Entität ganz oben, die mehrere Programm enthalten kann.  Jedes Programm kann maximal eine Produktions-Umgebung und mehrere Nicht-Produktions-Umgebung enthalten.

Das folgende Diagramm zeigt die Hierarchie der Entitäten in Cloud Manager.

![image](assets/program-types1.png)

## Programm {#program-types}

Ein Benutzer kann eine **Sandbox** oder ein **reguläres** Programm erstellen.

Eine *Sandbox* wird normalerweise für Schulungszwecke, die Ausführung von Demos, die Aktivierung, POCs oder Dokumentation erstellt. Es soll keinen Live-Traffic transportieren und wird Beschränkungen unterliegen, die ein reguläres Programm nicht hat. Es umfasst Sites und Assets und wird automatisch mit einer Git-Verzweigung geliefert, die Beispielcode, eine Dev-Umgebung und eine Nicht-Produktions-Pipeline enthält.

Es wird ein *reguläres Programm* erstellt, um Live-Traffic zum richtigen Zeitpunkt in der Zukunft zu aktivieren.