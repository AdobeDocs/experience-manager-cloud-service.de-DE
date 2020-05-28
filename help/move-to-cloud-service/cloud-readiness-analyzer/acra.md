---
title: AEM-Systemübersicht
description: AEM-Systemübersicht
translation-type: tm+mt
source-git-commit: 3478827949356c4a4f5133b54c6cf809f416efef
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 1%

---


# AEM-Systemübersicht {#aem-system}

Auf dieser Seite wird AEM als Cloud-Dienst beschrieben, der neue Funktionen mit einer Architektur bietet, die eine wesentliche Verbesserung gegenüber früheren AEM-Versionen darstellt. Die Aktualisierung auf diese neue Architektur erfordert erhebliche Anstrengungen.

## Beschreibung {#background}

Das ACRA-Metamuster wird verwendet, um mehrere Probleme im Zusammenhang mit Aktualisierungen von AEM als Cloud-Dienst zu identifizieren. Es unterstützt mehrere Arten von Beratungsinformationen durch eine Kombination der *Werte für Verweis* und ReferenzBy des Musters und des zugehörigen *context* -Objekts. Der *Typwert* im *context* -Objekt bestimmt das erkannte Problem.

Bei den im ACRA-Muster enthaltenen Bereitschaftsproblemen dürften relativ wenige Fälle auftreten, die die Beratung auslösen. Es gibt andere Bereitstellungsprobleme im Zusammenhang mit AEM als Cloud-Dienst, bei denen möglicherweise viele Instanzen beachtet werden müssen und denen ein eigener Mustercode zugewiesen wird. (Siehe UUI und URS.)

## Musterdaten {#pattern-data}

Die folgenden Objekte sind in der JSON-Darstellung des Musters enthalten:

* **item.message**: Der Typ des Bereitschaftsproblems. (Siehe unten.)
* **data**: Ein JSON-Objekt, das die dem Typ entsprechenden Daten enthält.

### Mögliche Auswirkungen und Risiken {#possible-implications}

TBD

### Mögliche Lösungen  {#possible-solutions}

TBD
