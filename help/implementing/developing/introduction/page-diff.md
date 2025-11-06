---
title: Entwicklung und Seitenvergleich
description: Verstehen Sie, wie die Seitenvergleichsfunktion funktioniert und wie sie sich auf einen Entwickler auswirken kann.
exl-id: 03c08616-2203-4b90-bed6-4836266e2507
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 100%

---

# Entwicklung und Seitenvergleich {#developing-and-page-diff}

## Funktionsübersicht {#feature-overview}

Die Inhaltserstellung ist ein iterativer Prozess. Damit ein Autor effizient arbeiten kann, muss er sehen können, was sich von Iteration zu Iteration verändert hat. Es ist ineffizient und bringt Fehler mit sich, wenn eine Seitenversion und danach die andere geprüft wird. Eine Autorin bzw. ein Autor möchte die aktuelle Seite mit einer früheren Version nebeneinander vergleichen können, wobei die Unterschiede hervorgehoben werden.

Der Seitenvergleich ermöglicht es Benutzenden, die aktuelle Seite mit Launches, früheren Versionen usw. zu vergleichen. Weitere Informationen zu dieser Benutzerfunktion finden Sie unter [Seitenvergleich](/help/sites-cloud/authoring/sites-console/page-diff.md).

## Details zum Vorgang {#operation-details}

Beim Vergleichen von Versionen einer Seite wird die vorherige Version, die jemand vergleichen möchte, von AEM im Hintergrund neu erstellt, um den Vergleich zu erleichtern. Diese frühere Version ist notwendig, um den Inhalt [für den Vergleich nebeneinander zu rendern](/help/sites-cloud/authoring/sites-console/page-diff.md).

Dieser Wiederherstellungsvorgang wird intern von AEM durchgeführt und ist für die Benutzenden transparent, ohne dass sie eingreifen müssen. Admins, die das Repository beispielsweise in CRXDE Lite anzeigen, würden diese neu erstellten Versionen jedoch in der Inhaltsstruktur sehen.

Beim Vergleich von Inhalten wird die gesamte Baumstruktur bis zur zu vergleichenden Seite an der folgenden Stelle neu erstellt:

`/tmp/versionhistory/`

Es wird automatisch eine Bereinigungsaufgabe ausgeführt, um diesen temporären Inhalt zu bereinigen.

## Einschränkungen {#limitations}

Der Vergleich erfolgt Client-seitig über einen DOM-Vergleich, wodurch der Vergleichsprozess vereinfacht wird. Es gibt jedoch mehrere Einschränkungen, die von der Entwicklungsperson berücksichtigt werden müssen.

* Diese Funktion verwendet CSS-Klassen ohne Namespace im AEM-Produkt. Wenn andere benutzerdefinierte oder externe CSS-Klassen mit denselben Namen auf der Seite verwendet werden, kann dies die Anzeige des Vergleichs beeinflussen.

   * `html-added`
   * `html-removed`
   * `cq-component-added`
   * `cq-component-removed`
   * `cq-component-moved`
   * `cq-component-changed`

* Da der Vergleich Client-seitig ist und beim Laden der Seite ausgeführt wird, werden keine Änderungen am DOM berücksichtigt, die vorgenommen wurden, nachdem der Cient-seitige Vergleichsdienst ausgeführt wurde. Dieser Prozess kann sich auf Folgendes auswirken:

   * Komponenten, die AJAX verwenden, um Inhalte einzubeziehen
   * Single Page Applications
   * JavaScript-basierte Komponenten, die das DOM bei Benutzerinteraktionen manipulieren.
