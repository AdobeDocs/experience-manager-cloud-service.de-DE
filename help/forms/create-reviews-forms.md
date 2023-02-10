---
title: Erstellen und Verwalten von Überprüfungen in Formularen
seo-title: Creating and managing reviews in forms
description: Bei einer Überprüfung handelt es sich um einen Mechanismus, bei dem mindestens ein Prüfer Assets kommentieren kann, die in einem Formular verfügbar sind.
seo-description: A Review is a mechanism that allows one or more reviewers to comment on an asset that is available in a form.
topic-tags: forms-manager
source-git-commit: 400e9fa0263b3e9bdae10dc80d524b291f99496d
workflow-type: tm+mt
source-wordcount: '670'
ht-degree: 64%

---

# Erstellen und Verwalten von Assetüberprüfungen in Formularen {#creating-and-managing-reviews-for-assets-in-forms}

## Überprüfung {#review}

Eine Überprüfung ist ein Mechanismus, mit dem ein oder mehrere Überprüfer zu einem Asset, das in einem Formular verfügbar ist, Kommentare abgeben können.

## Einrichten einer Überprüfung {#setting-up-a-review}

1. Gehen Sie zur Registerkarte „Formulare“ und wählen Sie ein Formular aus.
1. Wenn keine Überprüfung im Formular durchgeführt wird, wird eine Überprüfung starten ![aem6forms_review_chat_comment](assets/aem6forms_review_chat_comment.png) in der Symbolleiste angezeigt. Klicken Sie auf Überprüfung starten . ![aem6forms_review_chat_comment](assets/aem6forms_review_chat_comment.png) Symbol.
1. Geben Sie folgende Informationen ein:

   * Titel: Obligatorisch kann es alphanumerische Zeichen, Bindestriche oder Unterstriche enthalten.
   * Beschreibung: Optional, Beschreibung des Zwecks/Inhalts für die Überprüfung.
   * Frist: Optional: das Datum, an dem die Überprüfung endet. Wenn der Termin bereits abgelaufen ist, wird die Aufgabe als „überfällig“ angezeigt.
   * Reviewer: Es muss mindestens ein Reviewer angegeben werden. Wenn Sie einen Gruppennamen oder Benutzernamen eingeben, werden alle übereinstimmenden Namen mit Ausnahme der Gruppe der Dienstbenutzer aufgeführt. einen Namen auswählen und auf Hinzufügen klicken.

1. Klicken Sie auf Starten , um eine Überprüfung zu starten.

>[!NOTE]
>
>* Der Administrator kann auf alle Gruppen zugreifen, die mit den Formularbenutzern verknüpft sind.
>* Die Gruppe Dienstbenutzer steht nicht zur Auswahl zur Überprüfung zur Verfügung.


### Aktionen beim Einrichten von Überprüfungen {#actions-that-occur-when-a-review-is-set-up}

In diesem Abschnitt wird beschrieben, was passiert, wenn eine Überprüfung erstellt bzw. eingerichtet wird.

1. Eine neue Überprüfungsaufgabe wird erstellt und dem ausgewählten Überprüfer zugewiesen.
1. Allen Reviewern wird eine Überprüfungsaufgabe zugeteilt. Die Aufgabe wird in ihrem Benachrichtigungsabschnitt angezeigt. Reviewer können auf eine Benachrichtigung klicken oder zum Posteingang wechseln, um die Aufgabe anzuzeigen. Reviewer können per Klick die Überprüfungsaufgabe öffnen, das Formular anzeigen und Kommentare hinzufügen.

   ![Warnung bei Reviewerbenachrichtigungen](assets/review-notification-img.png)

   Warnung bei Reviewerbenachrichtigungen

1. Das Kommentarfeld steht den Validierern des Formulars zur Verfügung. Andere können die Kommentare anzeigen, jedoch keine Kommentare schreiben.

## Verwalten einer Überprüfung {#managing-a-review}

>[!NOTE]
>
>Es können nur Überprüfungen geändert werden, die noch nicht abgeschlossen sind. Abgeschlossene Überprüfungen können nicht geändert werden.

1. Gehen Sie zur Registerkarte „Formulare“ und wählen Sie ein Formular aus.

1. Wenn bei einem Asset eine Überprüfung in Bearbeitung ist und Sie der Initiator der Überprüfung sind, wird in der Aktionsleiste das Symbol ![aem6forms_review_chat_comment](assets/aem6forms_review_chat_comment.png) zum Verwalten von Überprüfungen angezeigt. Nur Initiatoren von Überprüfungen können die Überprüfung verwalten (aktualisieren/beenden).

   Klicken Sie auf das Symbol ![aem6forms_review_chat_comment](assets/aem6forms_review_chat_comment.png) zum Verwalten der Überprüfung.

   Für Benutzer, die nicht der Initiator sind, ist das Symbol zum Verwalten von Überprüfungen deaktiviert.

1. Es wird ein Bildschirm mit folgenden Informationen anzeigt:

   * **Titel**: Kann nicht bearbeitet werden.

   * **Beschreibung**: Zur Bearbeitung verfügbar.

   * **Termin**: Zur Bearbeitung verfügbar. Die Werte für Datum und Uhrzeit des Termins können geändert werden, wenn sie in der Zukunft liegen.

   * **Überprüfungsname**: Zur Bearbeitung verfügbar. Sie können Reviewer hinzufügen oder entfernen. Wenn eine Aufgabe überfällig ist, können Sie Reviewer erst hinzufügen, wenn Sie den Termin verlängern und er über das aktuelle Datum hinausgeht.

1. Bearbeiten Sie die erforderlichen Felder und klicken Sie auf Fertig .

   ![Überprüfen des aktuellen Status im Task Manager](assets/manage-review-img.png)

   Überprüfen des aktuellen Status im Task Manager

1. Klicken Sie zum Beenden der Überprüfung auf Review beenden.

### Aktionen beim Bearbeiten einer Überprüfung {#actions-that-occur-when-a-review-is-modified}

In diesem Abschnitt wird beschrieben, was beim Aktualisieren/Ende von Überprüfungen passiert:

1. Wenn die Überprüfungsbeschreibung geändert wird, wird die entsprechende Aufgabe der Reviewer und des Initiators aktualisiert.
1. Wenn der Überprüfungstermin geändert wird, wird die entsprechende Aufgabe der Reviewer mit dem neuen Datum aktualisiert.

1. Wenn ein Reviewer entfernt wird:

   ![Entfernen eines Reviewers](assets/removeduser.png)

   Entfernen eines Reviewers

   1. Falls die zugewiesene Aufgabe unvollständig ist, wird sie beendet.
   1. Der Validierer kann das Formular nicht mehr kommentieren.

1. Wenn ein Reviewer hinzugefügt wird:

   ![Hinzufügen eines Reviewers](assets/addedreviewer.png)

   Hinzufügen eines Reviewers

   1. Eine Überprüfungsaufgabe wird erstellt und dem neu hinzugefügten Reviewer zugewiesen.
   1. Der neu hinzugefügte Überprüfer kann Kommentare zum Formular hinzufügen.

1. Wenn eine Überprüfung abgeschlossen wird:

   1. **Reviewer**: Bei allen Reviewern werden zugewiesene unvollständige Aufgaben beendet. Die Aufgabe wird im Benachrichtigungsabschnitt des Reviewers nicht mehr als „Ausstehend“ angezeigt.
   1. **Initiator**: Die dem Initiator der Überprüfung zugewiesene Aufgabe wird als abgeschlossen markiert. Die Aufgabe wird aus dem Benachrichtigungsabschnitt des Initiators von Überprüfungen entfernt.
   1. **Alle**: Die Überprüfung wird im Abschnitt für die vorherigen Überprüfungen angezeigt. Es können keine weiteren Kommentare hinzugefügt werden.
      ![Prüfung abgeschlossen](assets/review-complete-imgg.png)


