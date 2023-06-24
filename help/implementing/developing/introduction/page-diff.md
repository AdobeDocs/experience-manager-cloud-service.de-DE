---
title: Entwicklung und Seitenvergleich
description: Verstehen Sie, wie die Seitenvergleichsfunktion funktioniert und wie sie sich auf einen Entwickler auswirken kann.
exl-id: 03c08616-2203-4b90-bed6-4836266e2507
source-git-commit: 7260649eaab303ba5bab55ccbe02395dc8159949
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 34%

---

# Entwicklung und Seitenvergleich {#developing-and-page-diff}

## Funktionsübersicht {#feature-overview}

Die Inhaltserstellung ist ein iterativer Prozess. Damit ein Autor effizient arbeiten kann, muss er sehen können, was sich von Iteration zu Iteration verändert hat. Es ist ineffizient und bringt Fehler mit sich, wenn eine Seitenversion und danach die andere geprüft wird. Ein Autor möchte die aktuelle Seite mit einer früheren Version nebeneinander vergleichen können, wobei die Unterschiede hervorgehoben werden.

Der Seitenvergleich ermöglicht es einem Benutzer, die aktuelle Seite mit Starts, früheren Versionen usw. zu vergleichen. Weitere Informationen zu dieser Benutzerfunktion finden Sie unter [Seitenvergleich](/help/sites-cloud/authoring/features/page-diff.md).

## Details zum Vorgang {#operation-details}

Beim Vergleichen von Seitenversionen wird die vorherige Version, die der Benutzer vergleichen möchte, durch AEM im Hintergrund neu erstellt, um den Vergleich zu erleichtern. Diese vorherige Version ist zum Rendern des Inhalts erforderlich. [für einen Direktvergleich](/help/sites-cloud/authoring/features/page-diff.md).

Dieser Wiederherstellungsvorgang wird intern von AEM durchgeführt und ist für den Benutzer transparent und erfordert keinen Eingriff. Administratoren, die das Repository anzeigen, beispielsweise in CRXDE Lite, sehen diese neu erstellten Versionen jedoch in der Inhaltsstruktur.

Beim Vergleich von Inhalten wird die gesamte Baumstruktur bis zur zu vergleichenden Seite an der folgenden Stelle neu erstellt:

`/tmp/versionhistory/`

Es wird automatisch eine Bereinigungsaufgabe ausgeführt, um diesen temporären Inhalt zu bereinigen.

## Beschränkungen {#limitations}

Der Vergleich erfolgt Client-seitig über einen DOM-Vergleich, wodurch der Vergleichsprozess vereinfacht wird. Es gibt jedoch mehrere Einschränkungen, die vom Entwickler berücksichtigt werden müssen.

* Diese Funktion verwendet CSS-Klassen, die nicht dem AEM Produkt zugewiesen sind. Wenn andere benutzerdefinierte CSS-Klassen oder CSS-Klassen von Drittanbietern mit denselben Namen auf der Seite enthalten sind, kann sich dies auf die Anzeige des Vergleichs auswirken.

   * `html-added`
   * `html-removed`
   * `cq-component-added`
   * `cq-component-removed`
   * `cq-component-moved`
   * `cq-component-changed`

* Da der Vergleich Client-seitig ist und beim Laden der Seite ausgeführt wird, werden alle Anpassungen des DOM nach Ausführung des clientseitigen Vergleichs-Service nicht berücksichtigt. Dieser Prozess kann sich auf Folgendes auswirken:

   * Komponenten, die AJAX verwenden, um Inhalte einzubeziehen
   * Single Page Applications
   * JavaScript-basierte Komponenten, die das DOM bei Benutzerinteraktionen manipulieren.
