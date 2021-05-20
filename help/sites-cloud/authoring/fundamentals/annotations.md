---
title: Hinzufügen von Seitenanmerkungen
description: Viele Komponenten, die direkt zur Handhabung von Inhalten verwendet werden, ermöglichen das Hinzufügen von Anmerkungen.
exl-id: a9cb9745-8140-4795-a5f9-fb3a1a299bd8
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 100%

---

# Hinzufügen von Seitenanmerkungen {#adding-page-annotations}

Oft muss das Hinzufügen von Inhalten zu den Seiten Ihrer Website vor der tatsächlichen Veröffentlichung besprochen werden. Um diesen Vorgang zu erleichtern, können Sie in vielen Komponenten, die direkt mit Inhalt (und nicht mit dem Layout) in Verbindung stehen, Anmerkungen hinzufügen.

Bei einer Anmerkung wird eine farbige Zeichnung/Haftnotiz auf der Seite platziert. Mit einer Anmerkung können Sie (oder andere Benutzer) Kommentare und/oder Fragen für andere Autoren/Prüfer hinterlassen.

>[!NOTE]
>
>Beachten Sie, dass Sie auch mithilfe von [Kommentaren](/help/sites-cloud/authoring/getting-started/basic-handling.md#timeline) Feedback zu einer Seite geben können.

## Anmerkungen {#annotations}

Zum Erstellen und Ansehen von Anmerkungen wird ein spezieller [Modus](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes) verwendet.

>[!CAUTION]
>
>Durch Löschen einer Ressource (z. B. einer Komponente) werden alle Anmerkungen und Zeichnungen gelöscht, die mit dieser Ressource verbunden sind (unabhängig von ihrer Position auf der Seite als Ganzes).

>[!NOTE]
>
>Je nach Ihren Anforderungen können Sie auch einen Workflow erstellen, damit Benachrichtigungen gesendet werden, wenn Anmerkungen hinzugefügt, aktualisiert oder gelöscht werden.

### Hinzufügen von Anmerkungen zu Komponenten {#annotating-a-component}

Im Anmerkungsmodus können Sie Anmerkungen für Ihre Inhalte erstellen, bearbeiten, verschieben oder löschen.

1. Sie können den Anmerkungsmodus über das Symbol in der Symbolleiste (rechts oben) aufrufen, wenn Sie eine Seite bearbeiten:

   ![Schaltfläche „Anmerkungen“](/help/sites-cloud/authoring/assets/annotations.png)

   Sie können nun vorhandene Anmerkungen anzeigen.

   >[!NOTE]
   >
   >Zum Beenden des Anmerkungsmodus tippen/klicken Sie auf das Anmerkungssymbol (x-Symbol) oben rechts in der Symbolleiste.

1. Klicken/tippen Sie auf das Symbol „Anmerkung hinzufügen“ (Plussymbol links in der Symbolleiste), um mit dem Hinzufügen von Anmerkungen zu beginnen.

   >[!NOTE]
   >
   >Wenn Sie keine weiteren Anmerkungen hinzufügen möchten (und zur Anzeige zurückkehren wollen), tippen/klicken Sie auf das Symbol „Abbrechen“ (x-Symbol in einem weißen Kreis) links in der Symbolleiste oben.

1. Tippen/klicken Sie auf die erforderliche Komponente (Komponenten, denen eine Anmerkung hinzugefügt werden kann, sind mit einem blauen Rand gekennzeichnet), um die Anmerkung hinzuzufügen und das Dialogfeld zu öffnen:

   ![Hinzufügen von Anmerkungen](/help/sites-cloud/authoring/assets/annotation-adding.png)

   Hier können Sie das entsprechende Feld und/oder Symbol für folgende Aktionen wählen:

   * Einen Anmerkungstext eingeben.
   * Eine Zeichnung (Linien und Formen) erstellen, um den Bereich der Komponente hervorzuheben.

      ![Schaltfläche „Anmerkungszeichnung“](/help/sites-cloud/authoring/assets/annotation-sketch.png)

      Der Mauszeiger ändert sich in ein Fadenkreuz, wenn Sie eine Zeichnung erstellen. Sie können mehrere separate Linien zeichnen. Die Zeichnungslinie hat dieselbe Farbe wie die Anmerkung und kann ein Pfeil, ein Kreis oder ein Oval sein.

   * Farbe wählen/ändern:

      ![Schaltfläche „Anmerkungsfarbfeld“](/help/sites-cloud/authoring/assets/annotation-color-swatch.png)

   * Die Anmerkung löschen.

      ![Schaltfläche zum Löschen von Anmerkungen](/help/sites-cloud/authoring/assets/annotation-delete.png)

1. Sie können das Dialogfeld für die Anmerkungen schließen, indem Sie außerhalb des Dialogfelds. Eine abgeschnittene Ansicht (das erste Wort) der Anmerkung wird zusammen mit sämtlichen Zeichnungen angezeigt:

   ![Anmerkungszeichnungen](/help/sites-cloud/authoring/assets/annotation-sketches.png)

1. Wenn Sie mit dem Bearbeiten einer bestimmten Anmerkung fertig sind, können Sie Folgendes tun:

   * Klicken/tippen Sie auf die Textmarkierung, um die Anmerkung zu öffnen. Sobald sie geöffnet ist, können Sie den vollständigen Text sehen, Änderungen vornehmen oder die Anmerkung löschen.

      * Zeichnungen können nicht unabhängig von der Anmerkung gelöscht werden.
   * Positionieren Sie die Textmarkierung neu.
   * Klicken/tippen Sie auf eine Zeichnung, um diese Zeichnung auszuwählen und sie auf die gewünschte Position zu ziehen.
   * Verschieben oder kopieren Sie eine Komponente.

      * Alle damit verbundenen Anmerkungen und deren Zeichnungen werden ebenfalls verschoben oder kopiert, ihre Position in Relation zum Absatz bleibt gleich.


1. Um den Anmerkungsmodus zu beenden und zum vorher verwendeten Modus zurückzukehren, tippen/klicken Sie auf das Anmerkungssymbol (x-Symbol) oben rechts in der Symbolleiste.

>[!NOTE]
>
>Anmerkungen können nicht zu einer Seite hinzugefügt werden, die von einem anderen Benutzer gesperrt wurde.

>[!NOTE]
>
>Die Definition einer einzelnen Komponente bestimmt, ob Anmerkungen in Instanzen dieser Komponente möglich sind oder nicht.

## Kennzeichnung von Anmerkungen {#annotation-indicator}

Anmerkungen werden nicht im Bearbeitungsmodus angezeigt, doch die Kennzeichnung oben rechts in der Symbolleiste gibt an, wie viele Anmerkungen auf der aktuellen Seite vorhanden sind. Die Kennzeichnung ersetzt das standardmäßige Anmerkungssymbol, dient jedoch ebenfalls als schneller Link, mit dem Sie den Anmerkungsmodus aktivieren/deaktivieren können:

![Kennzeichnung von Anmerkungen](/help/sites-cloud/authoring/assets/annotation-indicator.png)

## Hinzufügen von Anmerkungen zu anderen Ressourcen {#annotating-other-resources}

Neben Komponenten können Sie zu einer Vielzahl von Ressourcen Anmerkungen hinzufügen:

* Hinzufügen von Anmerkungen zu Assets [Hinzufügen von Anmerkungen zu Assets](/help/assets/manage-digital-assets.md#annotating)
* Hinzufügen von Anmerkungen zu Video-Assets [Hinzufügen von Anmerkungen zu Video-Assets](/help/assets/manage-video-assets.md#annotate-video-assets)
