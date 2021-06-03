---
title: Hinzufügen von Seitenanmerkungen
description: Verwenden Sie den Anmerkungsmodus, um Anmerkungen und Zeichnungen auf Seiten zu belassen, da Sie Notizen mit fixierbaren Anmerkungen den Prozess der Inhaltsüberprüfung unterstützen
exl-id: a9cb9745-8140-4795-a5f9-fb3a1a299bd8
source-git-commit: 5d533354a29237aeafc00e5570ede3ab00b721fd
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 35%

---

# Hinzufügen von Seitenanmerkungen {#adding-page-annotations}

Das Erstellen von Inhalten für Ihr digitales Erlebnis erfordert oft Diskussionen und Feedback vor der Veröffentlichung. Um diesen Feedback-Prozess zu unterstützen, können AEM Anmerkungen zu Ihrem Inhalt hinzufügen.

Eine Anmerkung platziert eine einfache Zeichnung oder Notiz (denken Sie an eine reale Kurznotiz) auf der Seite. Mit der Anmerkung können Sie Kommentare oder Fragen für andere Autoren und Prüfer hinterlassen.

>[!TIP]
>
>Beachten Sie, dass Sie auch mithilfe von [Kommentaren](/help/sites-cloud/authoring/getting-started/basic-handling.md#timeline) Feedback zu einer Seite geben können.

Zum Erstellen und Ansehen von Anmerkungen wird ein spezieller [Modus](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-modes) verwendet.

>[!TIP]
>
>Je nach Ihren Anforderungen können Sie auch einen [Workflow](/help/sites-cloud/authoring/workflows/overview.md) entwickeln, um Benachrichtigungen zu senden, wenn Anmerkungen hinzugefügt, aktualisiert oder gelöscht werden.

## Kennzeichnung von Anmerkungen {#annotation-indicator}

Anmerkungen werden nicht im Bearbeitungsmodus angezeigt, doch die Kennzeichnung oben rechts in der Symbolleiste gibt an, wie viele Anmerkungen auf der aktuellen Seite vorhanden sind. Die Kennzeichnung ersetzt das standardmäßige Anmerkungssymbol, dient jedoch ebenfalls als schneller Link, mit dem Sie den Anmerkungsmodus aktivieren/deaktivieren können:

![Kennzeichnung von Anmerkungen](/help/sites-cloud/authoring/assets/annotation-indicator.png)

## Anmerkungsmodus {#annotate-mode}

Anmerkungen sind nur im Anmerkungsmodus sichtbar.

1. Sie können den Anmerkungsmodus über das Symbol in der Symbolleiste (oben rechts) aufrufen, wenn Sie eine Seite bearbeiten:

   ![Schaltfläche „Anmerkungen“](/help/sites-cloud/authoring/assets/annotations.png)

   Sie können nun vorhandene Anmerkungen anzeigen.

   ![Anmerkungsbeispiele](/help/sites-cloud/authoring/assets/annotation-sketches.png)

1. Klicken oder tippen Sie auf die Anmerkung, um das Anmerkungsdialogfeld zu öffnen und dessen Details anzuzeigen.

   ![Anmerkungsdetails](/help/sites-cloud/authoring/assets/annotation-sketches.png)

1. Um den Anmerkungsmodus zu beenden und zum zuvor verwendeten Modus zurückzukehren, tippen/klicken Sie auf die Schaltfläche x rechts oben in der Symbolleiste.

## Hinzufügen und Bearbeiten von Anmerkungen {#annotating-a-component}

Neben der Anzeige der Anmerkungen können Sie im Anmerkungsmodus Anmerkungen für Ihren Inhalt erstellen, bearbeiten, verschieben oder löschen

1. [Starten Sie den ](#annotate-mode) Anmerkungsmodus auf der Seite.

1. Klicken oder tippen Sie auf das Symbol Anmerkung hinzufügen (Plussymbol links in der Symbolleiste), um mit dem Hinzufügen von Anmerkungen zu beginnen.

1. Klicken oder tippen Sie auf die gewünschte Komponente (Komponenten, die kommentiert werden können, werden mit einem blauen Rahmen markiert), um die Anmerkung hinzuzufügen und das Dialogfeld zu öffnen:

   ![Hinzufügen von Anmerkungen](/help/sites-cloud/authoring/assets/annotation-adding.png)

   Hier können Sie das entsprechende Feld und/oder Symbol für folgende Aktionen wählen:

   * Einen Anmerkungstext eingeben.
   * Eine Zeichnung (Linien und Formen) erstellen, um den Bereich der Komponente hervorzuheben.

      ![Schaltfläche „Anmerkungszeichnung“](/help/sites-cloud/authoring/assets/annotation-sketch.png)

      Der Mauszeiger ändert sich in ein Fadenkreuz, wenn Sie eine Zeichnung erstellen. Sie können mehrere separate Linien zeichnen. Die Zeichnungslinie hat dieselbe Farbe wie die Anmerkung und kann ein Pfeil, ein Kreis oder ein Oval sein.

   * Wählen oder ändern Sie die Farbe:

      ![Schaltfläche „Anmerkungsfarbfeld“](/help/sites-cloud/authoring/assets/annotation-color-swatch.png)

1. Sie können das Anmerkungsdialogfeld schließen, indem Sie außerhalb des Dialogfelds auf klicken oder tippen. Eine abgeschnittene Ansicht der Anmerkung wird zusammen mit allen Zeichnungen angezeigt:

   ![Anmerkungszeichnungen](/help/sites-cloud/authoring/assets/annotation-sketches.png)

1. Wenn Sie mit dem Bearbeiten einer bestimmten Anmerkung fertig sind, können Sie Folgendes tun:

   * Klicken oder tippen Sie auf die Textmarkierung, um die Anmerkung zu öffnen. Nach dem Öffnen können Sie den Volltext anzeigen, Änderungen vornehmen oder [die Anmerkung löschen.](#deleting-annotations)
   * Positionieren Sie die Textmarkierung neu.
   * Klicken oder tippen Sie auf eine Zeichnung, um diese Zeichnung auszuwählen und sie an die gewünschte Position zu ziehen.
   * Verschieben oder Kopieren einer Komponente
      * Alle zugehörigen Anmerkungen und deren Zeichnungen werden ebenfalls verschoben oder kopiert, ihre Position in Bezug auf den Absatz bleibt jedoch gleich.


>[!NOTE]
>
>Anmerkungen können nicht zu einer Seite hinzugefügt werden, die von einem anderen Benutzer gesperrt wurde.

>[!NOTE]
>
>Die Definition einer einzelnen Komponente bestimmt, ob Anmerkungen in Instanzen dieser Komponente möglich sind oder nicht.

## Löschen von Anmerkungen und Zeichnungen {#deleting-annotations}

Anmerkungen und zugehörige Zeichnungen können gelöscht werden.

1. [Starten Sie den ](#annotate-mode) Anmerkungsmodus auf der Seite.

1. Klicken/tippen Sie auf die Textmarkierung, um die Anmerkung zu öffnen.

1. Klicken oder tippen Sie auf das Symbol Löschen .

   ![Anmerkung löschen](/help/sites-cloud/authoring/assets/annotation-delete.png)

1. Die Anmerkung und alle zugehörigen Zeichnungen werden gelöscht.

>[!NOTE]
>
>Beim Löschen einer Komponente werden alle Anmerkungen und Zeichnungen gelöscht, die mit dieser Ressource verbunden sind, unabhängig von ihrer Position auf der Seite als Ganzes.

## Löschen von Zeichnungen nur {#deleting-sketches}

Sie können bei allen zugehörigen Zeichnungen nur bestimmte Zeichnungen anstelle der gesamten Anmerkung löschen.

1. [Starten Sie den ](#annotate-mode) Anmerkungsmodus auf der Seite.

1. Klicken oder tippen Sie auf die Zeichnung. AEM markiert es mit einem dunkelblauen Kasten.

   ![Zeichnung zum Löschen auswählen](/help/sites-cloud/authoring/assets/annotation-sketch-delete.png)

1. Drücken Sie die Entf-Taste auf Ihrer Tastatur.

1. Die Zeichnung wird gelöscht, die Anmerkung bleibt jedoch erhalten.

## Hinzufügen von Anmerkungen zu anderen Ressourcen {#annotating-other-resources}

Neben Komponenten können Sie zu einer Vielzahl von Ressourcen Anmerkungen hinzufügen:

* Hinzufügen von Anmerkungen zu Assets [Hinzufügen von Anmerkungen zu Assets](/help/assets/manage-digital-assets.md#annotating)
* Hinzufügen von Anmerkungen zu Video-Assets [Hinzufügen von Anmerkungen zu Video-Assets](/help/assets/manage-video-assets.md#annotate-video-assets)
