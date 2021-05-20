---
title: Entwicklung und Seitenvergleich
description: Verstehen Sie, wie die Seitenvergleichsfunktion funktioniert und wie sie sich auf einen Entwickler auswirken kann.
exl-id: 03c08616-2203-4b90-bed6-4836266e2507
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 100%

---

# Entwicklung und Seitenvergleich {#developing-and-page-diff}

## Funktionsübersicht {#feature-overview}

Inhaltserstellung ist ein iterativer Vorgang. Damit ein Autor effizient arbeiten kann, muss er sehen können, was sich von Iteration zu Iteration verändert hat. Es ist ineffizient und bringt Fehler mit sich, wenn eine Seitenversion und danach die andere geprüft wird. Autoren möchten die aktuelle Seite mit einer vorherigen Version parallel vergleichen, wobei die Unterschiede hervorgehoben werden.

Mit dem Seitenvergleich können Benutzer die aktuelle Seite mit Launches, früheren Versionen usw. vergleichen. Weitere Informationen zu dieser Benutzerfunktion finden Sie unter [Seitenvergleich](/help/sites-cloud/authoring/features/page-diff.md).

## Details zum Vorgang {#operation-details}

Beim Vergleichen von Versionen einer Seite wird die vorherige Version, die der Benutzer vergleichen möchte, von AEM im Hintergrund neu erstellt, um den Vergleich zu erleichtern. Dies ist erforderlich, um den Inhalt für einen [direkten parallelen Vergleich](/help/sites-cloud/authoring/features/page-diff.md) rendern zu können.

Dieser Wiederherstellungsvorgang wird intern von AEM durchgeführt und ist für den Benutzer transparent und erfordert keinen Eingriff. Administratoren, die das Repository beispielsweise in CRX DE Lite anzeigen, sehen diese neu erstellten Versionen jedoch in der Inhaltsstruktur.

Beim Vergleich von Inhalten wird die gesamte Baumstruktur bis zur zu vergleichenden Seite an der folgenden Stelle neu erstellt:

`/tmp/versionhistory/`

Es wird automatisch eine Bereinigungsaufgabe ausgeführt, um diesen temporären Inhalt zu bereinigen.

## Beschränkungen {#limitations}

Der Vergleich erfolgt Client-seitig über einen DOM-Vergleich, was den Vergleichsprozess vereinfacht. Es gibt jedoch einige Einschränkungen, die der Entwickler beachten muss.

* Diese Funktion verwendet CSS-Klassen ohne Namespace im AEM-Produkt. Wenn andere benutzerdefinierte oder externe CSS-Klassen mit denselben Namen auf der Seite verwendet werden, kann dies die Anzeige des Vergleichs beeinflussen.

   * `html-added`
   * `html-removed`
   * `cq-component-added`
   * `cq-component-removed`
   * `cq-component-moved`
   * `cq-component-changed`

* Da der Vergleich Client-seitig ist und beim Laden der Seite ausgeführt wird, werden keine Änderungen am DOM berücksichtigt, die vorgenommen wurden, nachdem der Cient-seitige Vergleichs-Service ausgeführt wurde. Dies kann Folgendes beeinflussen:

   * Komponenten, die AJAX verwenden, um Inhalte einzubeziehen
   * Single Page Applications
   * JavaScript-basierte Komponenten, die den DOM bei Benutzerinteraktionen manipulieren.
