---
title: Anpassung erkannt
description: Anpassung erkannt
translation-type: tm+mt
source-git-commit: 3478827949356c4a4f5133b54c6cf809f416efef
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 3%

---


# Anpassung erkannt {#cust-pattern}

Auf dieser Seite wird der Code für die Anpassung des erkannten Musters beschrieben.

## Hintergrund {#background}

Dieser Mustercode wird verwendet, um Anpassungen zu identifizieren, die an der AEM-Instanz vorgenommen wurden. Da AEM häufig angepasst wird, deutet dieses Muster nicht unbedingt auf ein Problem hin. Er identifiziert einen Datensatz mit Anpassungen, damit sie hinsichtlich ihrer Auswirkungen auf die Upgrade-Pläne bewertet werden können.

Folgende Anpassungen werden erkannt:

* Kundencode (Pakete) und Konfigurationen
* Pakete von Drittanbietern
* Integration mit Drittanbieterdiensten
* Nicht standardmäßige Oak-Indizes

## Musterdaten {#pattern-data}

Die folgenden Objekte sind in der JSON-Darstellung des Musters enthalten:

* **item.message**: bezieht sich auf die Meldung des Musters.
* **item.context**: bezieht sich auf zusätzliche Informationen über die Übersichtsinformationen:
   * *type*: customization.found.
   * *data*: Ein JSON-Objekt, das die Daten enthält, die die Anpassung beschreiben

### Mögliche Auswirkungen und Risiken {#possible-implications}

Nicht zutreffend.

### Mögliche Lösungen  {#possible-solutions}

Nicht zutreffend.
