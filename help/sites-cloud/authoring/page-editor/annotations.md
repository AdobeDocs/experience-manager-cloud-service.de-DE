---
title: Hinzufügen von Seitenanmerkungen
description: Verwenden Sie den Anmerkungsmodus, um Anmerkungen und Skizzen auf den Seiten zu hinterlassen, so wie Sie Haftnotizen verwenden würden, um Ihren Prozess der Inhaltsüberprüfung zu unterstützen.
exl-id: a9cb9745-8140-4795-a5f9-fb3a1a299bd8
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 97%

---

# Hinzufügen von Seitenanmerkungen {#adding-page-annotations}

Das Erstellen von Inhalten für Ihr digitales Erlebnis erfordert Diskussionen und Feedback vor der Veröffentlichung. Um diesen Feedback-Prozess zu unterstützen, können Sie mit AEM Anmerkungen zu Ihrem Inhalt hinzufügen.

Bei einer Anmerkung wird eine einfache Skizze oder Notiz (stellen Sie sich eine Haftnotiz vor) auf der Seite platziert. Mit der Anmerkung können Sie Kommentare oder Fragen für andere Autorinnen und Autoren sowie Prüferinnen und Prüfer hinterlassen.

>[!TIP]
>
>Beachten Sie, dass Sie auch mithilfe von [Kommentaren](/help/sites-cloud/authoring/basic-handling.md#timeline) Feedback zu einer Seite geben können.

Zum Erstellen und Ansehen von Anmerkungen wird ein spezieller [Modus](/help/sites-cloud/authoring/page-editor/introduction.md#mode-selector) verwendet.

>[!TIP]
>
>Je nach Ihren Anforderungen können Sie auch einen [Workflow](/help/sites-cloud/authoring/workflows/overview.md) erstellen, damit Benachrichtigungen gesendet werden, wenn Anmerkungen hinzugefügt, aktualisiert oder gelöscht werden.

## Kennzeichnung von Anmerkungen {#annotation-indicator}

Anmerkungen werden nicht im Bearbeitungsmodus angezeigt, doch die Kennzeichnung oben rechts in der Symbolleiste gibt an, wie viele Anmerkungen auf der aktuellen Seite vorhanden sind. Die Kennzeichnung ersetzt das standardmäßige Anmerkungssymbol, dient jedoch ebenfalls als schneller Link, mit dem Sie den Anmerkungsmodus aktivieren/deaktivieren können:

![Kennzeichnung von Anmerkungen](/help/sites-cloud/authoring/assets/annotation-indicator.png)

## Anmerkungsmodus {#annotate-mode}

Anmerkungen sind nur im Anmerkungsmodus sichtbar.

1. Sie können den Anmerkungsmodus über das Symbol in der Symbolleiste (rechts oben) aufrufen, wenn Sie eine Seite bearbeiten:

   ![Schaltfläche „Anmerkungen“](/help/sites-cloud/authoring/assets/annotations.png)

   Sie können nun vorhandene Anmerkungen anzeigen.

   ![Beispiele für Anmerkungen](/help/sites-cloud/authoring/assets/annotation-sketches.png)

1. Wählen Sie die Anmerkung aus, um das Dialogfeld „Anmerkung“ zu öffnen und seine Details anzuzeigen.

   ![Anmerkungsdetails](/help/sites-cloud/authoring/assets/annotation-adding.png)

1. Um den Anmerkungsmodus zu beenden und zum vorher verwendeten Modus zurückzukehren, wählen Sie die Schaltfläche „x“ oben rechts in der Symbolleiste aus.

## Hinzufügen und Bearbeiten von Anmerkungen {#annotating-a-component}

Neben der Anzeige der Anmerkungen können Sie im Anmerkungsmodus Anmerkungen für Ihre Inhalte erstellen, bearbeiten, verschieben oder löschen.

1. [Starten Sie den Anmerkungsmodus](#annotate-mode) auf der Seite.

1. Wählen Sie das Symbol „Anmerkung hinzufügen“ (Plussymbol links in der Symbolleiste) aus, um mit dem Hinzufügen von Anmerkungen zu beginnen.

1. Wählen Sie die erforderliche Komponente aus (Komponenten, denen eine Anmerkung hinzugefügt werden kann, sind mit einem blauen Rand gekennzeichnet), um die Anmerkung hinzuzufügen und das Dialogfeld zu öffnen:

   ![Hinzufügen von Anmerkungen](/help/sites-cloud/authoring/assets/annotation-adding.png)

   Hier können Sie das entsprechende Feld und/oder Symbol verwenden, um:

   * den Anmerkungstext einzugeben.
   * Eine Zeichnung (Linien und Formen) erstellen, um den Bereich der Komponente hervorzuheben.

     ![Schaltfläche „Anmerkungszeichnung“](/help/sites-cloud/authoring/assets/annotation-sketch.png)

     Der Mauszeiger ändert sich in ein Fadenkreuz, wenn Sie eine Zeichnung erstellen. Sie können mehrere separate Linien zeichnen. Die Zeichnungslinie hat dieselbe Farbe wie die Anmerkung und kann ein Pfeil, ein Kreis oder ein Oval sein.

   * Farbe wählen/ändern:

     ![Schaltfläche „Anmerkungsfarbfeld“](/help/sites-cloud/authoring/assets/annotation-color-swatch.png)

1. Sie können das Dialogfeld für die Anmerkungen schließen, indem Sie außerhalb des Dialogfelds klicken/tippen. Eine gekürzte Ansicht der Anmerkung wird zusammen mit sämtlichen Zeichnungen angezeigt:

   ![Anmerkungszeichnungen](/help/sites-cloud/authoring/assets/annotation-sketches.png)

1. Wenn Sie mit dem Bearbeiten einer bestimmten Anmerkung fertig sind, können Sie Folgendes tun:

   * Wählen Sie die Textmarkierung aus, um die Anmerkung zu öffnen. Sobald sie geöffnet ist, können Sie den vollständigen Text anzeigen, Änderungen vornehmen oder [die Anmerkung löschen](#deleting-annotations).
   * Positionieren Sie die Textmarkierung neu.
   * Wählen Sie eine Zeichnung aus, um diese Zeichnung auszuwählen und sie auf die gewünschte Position zu ziehen.
   * Verschieben oder Kopieren einer Komponente
      * Alle damit verbundenen Anmerkungen und deren Zeichnungen werden ebenfalls verschoben oder kopiert, ihre Position in Relation zum Absatz bleibt gleich.


>[!NOTE]
>
>Anmerkungen können nicht zu einer Seite hinzugefügt werden, die von einer anderen Person gesperrt wurde.

>[!NOTE]
>
>Die Definition einer einzelnen Komponente bestimmt, ob Anmerkungen in Instanzen dieser Komponente möglich sind oder nicht.

## Löschen von Anmerkungen und Zeichnungen {#deleting-annotations}

Anmerkungen und zugehörige Zeichnungen können gelöscht werden.

1. [Starten Sie den Anmerkungsmodus](#annotate-mode) auf der Seite.

1. Wählen Sie die Textmarkierung aus, um die Anmerkung zu öffnen.

1. Wählen Sie das Symbol „Löschen“ aus.

   ![Anmerkung löschen](/help/sites-cloud/authoring/assets/annotation-delete.png)

1. Die Anmerkung und alle zugehörigen Zeichnungen werden gelöscht.

>[!NOTE]
>
>Durch Löschen einer Komponente werden alle Anmerkungen und Zeichnungen gelöscht, die mit dieser Ressource verbunden sind (unabhängig von ihrer Position auf der Seite als Ganzes).

## Nur Zeichnungen löschen {#deleting-sketches}

Sie können bei allen zugehörigen Zeichnungen nur bestimmte Zeichnungen anstelle der gesamten Anmerkung löschen.

1. [Starten Sie den Anmerkungsmodus](#annotate-mode) auf der Seite.

1. Wählen Sie die Zeichnung aus. AEM hebt sie mit einem dunkelblauen Rand hervor.

   ![Zeichnung zum Löschen auswählen](/help/sites-cloud/authoring/assets/annotation-sketch-delete.png)

1. Drücken Sie die Entf-Taste auf Ihrer Tastatur.

1. Die Zeichnung wird gelöscht, die Anmerkung bleibt jedoch erhalten.

## Hinzufügen von Anmerkungen zu anderen Ressourcen {#annotating-other-resources}

Neben Komponenten können Sie zu einer Vielzahl von Ressourcen Anmerkungen hinzufügen:

* Hinzufügen von Anmerkungen zu Assets [Hinzufügen von Anmerkungen zu Assets](/help/assets/manage-digital-assets.md#annotating)
* Hinzufügen von Anmerkungen zu Video-Assets [Hinzufügen von Anmerkungen zu Video-Assets](/help/assets/manage-video-assets.md#annotate-video-assets)
