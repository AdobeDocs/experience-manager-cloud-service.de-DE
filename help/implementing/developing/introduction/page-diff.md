---
title: Entwicklung und Seitenvergleich
description: Verstehen Sie, wie die Funktion "Seitenabweichung"funktioniert und wie sie einen Entwickler beeinflussen kann.
translation-type: tm+mt
source-git-commit: fee73b5f5ba69422494efe554ac5aa62c046ad86
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 52%

---


# Entwicklung und Seitenvergleich {#developing-and-page-diff}

## Funktionsübersicht {#feature-overview}

Inhaltserstellung ist ein iterativer Vorgang. Damit ein Autor effizient arbeiten kann, muss er sehen können, was sich von Iteration zu Iteration verändert hat. Es ist ineffizient und bringt Fehler mit sich, wenn eine Seitenversion und danach die andere geprüft wird. Autoren möchten die aktuelle Seite mit einer vorherigen Version parallel vergleichen, wobei die Unterschiede hervorgehoben werden.

Mit dem Seitenvergleich können Benutzer die aktuelle Seite mit Launches, früheren Versionen usw. vergleichen. Weitere Informationen zu dieser Benutzerfunktion finden Sie unter [Seitenvergleich](/help/sites-cloud/authoring/features/page-diff.md).

## Vorgangsdetails {#operation-details}

Beim Vergleich von Seitenversionen wird die vorherige Version, die der Benutzer vergleichen möchte, von AEM im Hintergrund neu erstellt, um den Unterschied zu erleichtern. Dies ist erforderlich, damit der Inhalt [für einen Vergleich](/help/sites-cloud/authoring/features/page-diff.md)nebeneinander gerendert werden kann.

Dieser Erholungsvorgang wird intern von AEM durchgeführt und ist für den Benutzer transparent und erfordert kein Eingreifen. Administratoren, die das Repository beispielsweise in CRX DE Lite anzeigen, sehen diese neu erstellten Versionen jedoch in der Inhaltsstruktur.

Beim Vergleich von Inhalten wird die gesamte Struktur bis zur zu vergleichenden Seite an der folgenden Stelle neu erstellt:

`/tmp/versionhistory/`

Eine Bereinigungs-Aufgabe wird automatisch ausgeführt, um diesen temporären Inhalt zu bereinigen.

## Berechtigungen {#permissions}

Der Unterschied erfolgt clientseitig über DOM-Vergleich, was den diff-Prozess einfach macht, es gibt jedoch eine Reihe von Einschränkungen, die vom Entwickler zu berücksichtigen sind.

* Diese Funktion verwendet CSS-Klassen ohne Namespace im AEM-Produkt. Wenn andere benutzerdefinierte oder externe CSS-Klassen mit denselben Namen auf der Seite verwendet werden, kann dies die Anzeige des Vergleichs beeinflussen.

   * `html-added`
   * `html-removed`
   * `cq-component-added`
   * `cq-component-removed`
   * `cq-component-moved`
   * `cq-component-changed`

* Da der Vergleich clientseitig ist und beim Laden der Seite ausgeführt wird, werden keine Änderungen am DOM berücksichtigt, die vorgenommen wurden, nachdem der clientseitige Vergleichsdienst ausgeführt wurde. Dies kann Folgendes beeinflussen:

   * Komponenten, die AJAX zum Einschließen von Inhalten verwenden
   * Einzelseiten-Webanwendungen
   * JavaScript-basierte Komponenten, die den DOM bei Benutzerinteraktionen manipulieren.
