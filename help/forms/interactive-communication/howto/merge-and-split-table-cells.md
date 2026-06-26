---
title: Zusammenführen und Aufteilen von Tabellenzellen im Editor für interaktive Kommunikation
description: Erfahren Sie, wie Sie benachbarte Tabellenzellen in einer Zelle kombinieren und eine zusammengeführte Zelle wieder in mehrere Spalten aufteilen, um flexible Tabellen-Layouts im Editor für interaktive Kommunikation zu erstellen.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
badgeSaas: label="AEM Forms" type="Positive" tooltip="Gilt für AEM Forms."
exl-id: merge-split-table-cells-ic-editor
source-git-commit: b11e1b28aabba9e03553dc9e9394bff111facfee
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 3%

---


# Zusammenführen und Aufteilen von Tabellenzellen im Editor für interaktive Kommunikation

Standardmäßige Tabellenraster sind standardmäßig einheitlich, jede Zeile hat die gleiche Anzahl gleich großer Zellen. Viele reale Layouts erfordern mehr Flexibilität: eine übergreifende Kopfzeile über mehreren Spalten, eine Zusammenfassungszeile, die die gesamte Tabellenbreite einnimmt, oder gruppierte Zellen, die visuell verwandte Daten miteinander verknüpfen. Sie können benachbarte Zellen in einer Zeile zusammenführen, um diese Layouts zu erhalten, und jede zuvor zusammengeführte Zelle wieder in einzelne Spalten aufteilen, wenn Sie die Struktur überarbeiten müssen.

| Wer? | Vorteil |
|-----|---------|
| **Author (Designer für interaktive Kommunikation / Layout-Designer)** | Erstellen Sie Rechnungen, Zeitpläne und Vergleichstabellen mit übergreifenden Kopfzeilen oder gruppierten Zellen, ohne den Editor für interaktive Kommunikation zu verlassen. |

## Zellen zusammenführen

1. Klicken Sie im Editor für interaktive Kommunikation auf die erste Zelle, die Sie in die Zusammenführung einbeziehen möchten.

1. Halten Sie **Umschalt** gedrückt und klicken Sie auf die letzte Zelle im Bereich, um alle aufeinander folgenden Zellen in derselben Zeile auszuwählen.

1. Klicken Sie mit der rechten Maustaste auf die Auswahl, wählen Sie **Zusammenführen** und dann **Zellen zusammenführen**.

   ![Zellen zusammenführen](/help/forms/interactive-communication/assets/split-merge-table1.png)

   Die ausgewählten Zellen werden zu einer einzigen zusammengeführten Zelle zusammengefasst. Inhalt und Formatierung der ersten Zelle in der Auswahl bleiben erhalten. Inhalte aus nachfolgenden Zellen werden verworfen.

   Beispielsweise können Sie in einer Tabelle „Fahrzeugdetails“ aufeinander folgende Zellen in der Kopfzeile zusammenführen, um eine übergreifende Beschriftung wie „Fahrzeugdetails **zu**.

**Was Sie beachten sollten:**

- Sie können nur Zellen zusammenführen, die aufeinander folgen und sich in derselben Zeile befinden. Das Auswählen von Zellen über mehrere Zeilen hinweg wird nicht unterstützt.
- Nur der Inhalt und die Formatierung der ersten Zelle werden nach der Zusammenführung beibehalten.

## Aufteilen einer zusammengeführten Zelle

1. Klicken Sie mit der rechten Maustaste auf die zusammengeführte Zelle, die Sie aufteilen möchten.

1. Wählen Sie **Aufspaltung** und dann **Zelle teilen** aus.

   ![Zelle teilen](/help/forms/interactive-communication/assets/split-merge-table2.png)

1. Geben **im Dialogfeld** Zelle teilen“ die Anzahl der Spalten ein, in die die Zelle aufgeteilt werden soll.

1. Klicken Sie **OK**, um sie anzuwenden.

   ![Dialogfeld „Zelle teilen“](/help/forms/interactive-communication/assets/split-merge-table3.png)

   Der **Max. Spalten** Wert im Dialogfeld stellt das Maximum dar, in das Sie aufteilen können - gleich der Anzahl der Zellen, die ursprünglich zusammengeführt wurden. Wenn beispielsweise zwei Zellen zusammengeführt wurden, ist **Max. Spalten** 2.

   | Aufspaltungswert | Ergebnis |
   |-------------|--------|
   | 2 | Zelle wird in zwei einzelne Zellen aufgeteilt |
   | 1 | Zelle verbleibt als einzelne Zelle (keine Änderung) |

   Die Tabellenstruktur wird automatisch aktualisiert. Jeder Wert zwischen 1 und dem Wert **Max** ist gültig.

## Überlegung

Das Zusammenführen von Zellen, die sich über mehrere Zeilen erstrecken, wird nicht vollständig unterstützt und kann zu unerwarteten Ergebnissen führen. Führen Sie Zusammenführungsvorgänge nur für aufeinander folgende Zellen innerhalb derselben Zeile durch.

## Häufig gestellte Fragen

**Kann ich Zellen sowohl in Zeilen als auch in Spalten zusammenführen?**
Anzahl Es können nur aufeinander folgende Zellen innerhalb derselben Zeile zusammengeführt werden. Zeilenübergreifende (zeilenübergreifende) Zusammenführungen werden nicht vollständig unterstützt und können zu unerwarteten Ergebnissen führen.

**Was passiert mit dem Inhalt der Zellen, die ich zusammenführe?**
Inhalt und Formatierung der ersten Zelle in der Auswahl bleiben erhalten. Inhalte aus den verbleibenden Zellen werden bei der Anwendung der Zusammenführung verworfen.

**Wie erkenne ich die maximale Anzahl von Spalten, in die ich eine zusammengeführte Zelle aufteilen kann?**
Im Dialogfeld „Aufspaltung“ wird der Wert **Max. Spalten** angezeigt, der der Anzahl der Zellen entspricht, die ursprünglich zur Erstellung der Zelle zusammengeführt wurden.

## Siehe auch

- [Tabellenkomponente im Editor für interaktive Kommunikation](/help/forms/interactive-communication/table.md)
- [Erstellen einer dynamischen Tabelle im Editor für interaktive Kommunikation](/help/forms/interactive-communication/dynamic-table-in-interactive-communication-editor.md)
- [Erstellen einer interaktiven Kommunikation](/help/forms/interactive-communication/create-interactive-communication.md)

