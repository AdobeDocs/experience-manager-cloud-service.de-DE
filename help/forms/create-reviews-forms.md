---
title: Erstellen und Verwalten von Überprüfung in Formularen
seo-title: Creating and managing reviews in forms
description: Bei einer Überprüfung handelt es sich um einen Mechanismus, bei dem mindestens ein Prüfer Assets kommentieren kann, die in einem Formular verfügbar sind.
seo-description: A Review is a mechanism that allows one or more reviewers to comment on an asset that is available in a form.
topic-tags: forms-manager
source-git-commit: 400e9fa0263b3e9bdae10dc80d524b291f99496d
workflow-type: ht
source-wordcount: '670'
ht-degree: 100%

---

# Erstellen und Verwalten von Assetüberprüfungen in Formularen {#creating-and-managing-reviews-for-assets-in-forms}

## Überprüfung {#review}

Bei einer Überprüfung können ein oder mehrere Überprüfer bzw. Überprüferinnen zu einem in einem Formular verfügbaren Asset einen Kommentar abgeben.

## Einrichten einer Überprüfung {#setting-up-a-review}

1. Gehen Sie zur Registerkarte „Formulare“ und wählen Sie ein Formular aus.
1. Wenn für das Formular derzeit keine Überprüfung durchgeführt wird, wird in der Aktionsleiste das Symbol ![aem6forms_review_chat_comment](assets/aem6forms_review_chat_comment.png) zum Starten einer Überprüfung angezeigt. Klicken Sie auf das Symbol ![aem6forms_review_chat_comment](assets/aem6forms_review_chat_comment.png) zum Starten einer Überprüfung.
1. Geben Sie folgende Informationen ein:

   * Titel: obligatorisch, kann alphanumerische Zeichen, Bindestriche oder Unterstriche enthalten.
   * Beschreibung: optional, Beschreibung des Zwecks/Inhalts der Überprüfung.
   * Frist: optional, das Datum, an dem die Überprüfung endet. Wenn die Frist bereits abgelaufen ist, wird die Aufgabe als „überfällig“ angezeigt.
   * Reviewer: Es muss mindestens ein Reviewer angegeben werden. Wenn Sie einen Gruppennamen oder Benutzernamen eingeben, werden alle passenden Namen mit Ausnahme der Gruppe der Dienstbenutzenden aufgeführt. Wählen Sie einen Namen aus und klicken Sie auf „Hinzufügen“.

1. Klicken Sie auf Starten, um eine Überprüfung zu starten.

>[!NOTE]
>
>* Der Administrator bzw. die Administratorin kann auf alle Gruppen zugreifen, die mit den Formularbenutzenden verknüpft sind.
>* Die Gruppe der Dienstbenutzenden steht für die Überprüfung nicht zur Auswahl.


### Aktionen beim Einrichten von Überprüfungen {#actions-that-occur-when-a-review-is-set-up}

In diesem Abschnitt wird beschrieben, was passiert, wenn eine Überprüfung erstellt bzw. eingerichtet wird.

1. Eine neue Überprüfungsaufgabe wird erstellt und dem/der ausgewählten Überprüfenden zugewiesen.
1. Allen Reviewern wird eine Überprüfungsaufgabe zugeteilt. Die Aufgabe wird in ihrem Benachrichtigungsabschnitt angezeigt. Reviewer können auf eine Benachrichtigung klicken oder zum Posteingang wechseln, um die Aufgabe anzuzeigen. Reviewer können per Klick die Überprüfungsaufgabe öffnen, das Formular anzeigen und Kommentare hinzufügen.

   ![Warnung bei Reviewerbenachrichtigungen](assets/review-notification-img.png)

   Warnung bei Reviewerbenachrichtigungen

1. Das Kommentarfeld ist für Überprüfende des Formulars zugänglich. Andere können die Kommentare anzeigen, jedoch keine Kommentare schreiben.

## Verwalten einer Überprüfung {#managing-a-review}

>[!NOTE]
>
>Es können nur Überprüfungen geändert werden, die noch nicht abgeschlossen sind. Abgeschlossene Überprüfungen können nicht geändert werden.

1. Gehen Sie zur Registerkarte „Formulare“ und wählen Sie ein Formular aus.

1. Wenn bei einem Asset eine Überprüfung in Bearbeitung ist und Sie der Initiator der Überprüfung sind, wird in der Aktionsleiste das Symbol ![aem6forms_review_chat_comment](assets/aem6forms_review_chat_comment.png) zum Verwalten von Überprüfungen angezeigt. Nur Initiierende von Überprüfungen können die Überprüfung verwalten (aktualisieren/beenden).

   Klicken Sie auf das Symbol ![aem6forms_review_chat_comment](assets/aem6forms_review_chat_comment.png) zum Verwalten der Überprüfung.

   Für Benutzer, die nicht der Initiator sind, ist das Symbol zum Verwalten von Überprüfungen deaktiviert.

1. Es wird ein Bildschirm mit folgenden Informationen anzeigt:

   * **Titel**: Kann nicht bearbeitet werden.

   * **Beschreibung**: Kann bearbeitet werden.

   * **Frist**: Kann bearbeitet werden. Die Werte für Datum und Uhrzeit der Frist können geändert werden, wenn sie in der Zukunft liegen.

   * **Name des/der Überprüfenden**: kann bearbeitet werden. Sie können Reviewer hinzufügen oder entfernen. Wenn eine Aufgabe überfällig ist, können Sie Reviewer erst hinzufügen, wenn Sie den Termin verlängern und er über das aktuelle Datum hinausgeht.

1. Bearbeiten Sie die erforderlichen Felder und klicken Sie dann auf „Fertig“.

   ![Überprüfen des aktuellen Status im Task Manager](assets/manage-review-img.png)

   Überprüfen des aktuellen Status im Task Manager

1. Zum Beenden der Überprüfung klicken Sie auf „Überprüfung beenden“.

### Aktionen beim Ändern einer Überprüfung {#actions-that-occur-when-a-review-is-modified}

In diesem Abschnitt wird beschrieben, was bei der Aktualisierung/Beendigung der Überprüfung geschieht:

1. Wenn die Überprüfungsbeschreibung geändert wird, wird die entsprechende Aufgabe der Reviewer und des Initiators aktualisiert.
1. Wenn der Überprüfungstermin geändert wird, wird die entsprechende Aufgabe der Reviewer mit dem neuen Datum aktualisiert.

1. Wenn ein Reviewer entfernt wird:

   ![Entfernen eines Reviewers](assets/removeduser.png)

   Entfernen eines Reviewers

   1. Falls die zugewiesene Aufgabe unvollständig ist, wird sie beendet.
   1. Der/die Überprüfende kann das Formular nicht mehr kommentieren.

1. Wenn ein Reviewer hinzugefügt wird:

   ![Hinzufügen eines Reviewers](assets/addedreviewer.png)

   Hinzufügen eines Reviewers

   1. Eine Überprüfungsaufgabe wird erstellt und dem neu hinzugefügten Reviewer zugewiesen.
   1. Der/die neu hinzugefügte Überprüfende kann Kommentare zum Formular hinzufügen.

1. Wenn eine Überprüfung abgeschlossen wird:

   1. **Reviewer**: Bei allen Reviewern werden zugewiesene unvollständige Aufgaben beendet. Die Aufgabe wird im Benachrichtigungsabschnitt des Reviewers nicht mehr als „Ausstehend“ angezeigt.
   1. **Initiator**: Die dem Initiator der Überprüfung zugewiesene Aufgabe wird als abgeschlossen markiert. Die Aufgabe wird aus dem Benachrichtigungsabschnitt des Initiators von Überprüfungen entfernt.
   1. **Alle**: Die Überprüfung wird im Abschnitt für die vorherigen Überprüfungen angezeigt. Es können keine weiteren Kommentare hinzugefügt werden.
      ![Überprüfung abgeschlossen](assets/review-complete-imgg.png)


