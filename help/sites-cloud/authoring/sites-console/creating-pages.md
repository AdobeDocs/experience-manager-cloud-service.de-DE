---
title: Erstellen von Seiten
description: Erfahren Sie, wie Sie mithilfe der Sites-Konsole neue Seiten für Ihre Website erstellen.
source-git-commit: 0ba8faaa14d09d09fce5846bfff77287bfbd94c7
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 40%

---


# Erstellen von Seiten {#creating-pages}

Erfahren Sie, wie Sie mit der **Sites** Konsole.

>[!TIP]
>
>Bevor Sie mit der Erstellung neuer Seiten beginnen, sollten Sie sich mit [wie Ihre Seiten in AEM organisiert sind.](/help/sites-cloud/authoring/sites-console/organizing-pages.md)

## Zugriffsberechtigungen {#access-privileges}

Ihr Konto muss über die entsprechenden Zugriffsrechte und Berechtigungen verfügen, um Seiten erstellen zu können.

Wenden Sie sich bei Problemen an Ihren Systemadministrator.

## Erstellen einer neuen Seite {#creating-a-new-page}

Bevor Sie mit der Erstellung von Inhalten beginnen können, müssen Sie eine Seite erstellen, es sei denn, alle Seiten wurden bereits für Sie erstellt:

1. Öffnen [die **Sites** Konsole.](/help/sites-cloud/authoring/sites-console/introduction.md)
1. Navigieren Sie zu der Position, an der Sie die neue Seite erstellen möchten.
1. Öffnen Sie das Dropdown-Menü über **Erstellen** in der Symbolleiste und wählen Sie **Seite** aus der Liste aus:

   ![Erstellen von Seiten](/help/sites-cloud/authoring/assets/organizing-create-page.png)

1. Im ersten Schritt des Assistenten haben Sie folgende Möglichkeiten:

   * Wählen Sie die Vorlage aus, die Sie zum Erstellen der neuen Seite verwenden möchten, und wählen Sie dann **Nächste** um fortzufahren.

   * Mit **Abbrechen** brechen Sie den Vorgang ab.

   ![Auswählen einer Vorlage für eine neue Seite](/help/sites-cloud/authoring/assets/organizing-create-page-template.png)

1. Im letzten Schritt des Assistenten haben Sie folgende Möglichkeiten:

   * Geben Sie auf den drei Registerkarten die [Seiteneigenschaften](/help/sites-cloud/authoring/sites-console/page-properties.md) ein, die Sie der neuen Seite zuweisen möchten, und wählen Sie dann **Erstellen**, um die Seite zu erstellen.

   * Verwenden Sie die **Rücktaste**, um zur Vorlagenauswahl zurückzukehren.

   Die Schlüsselfelder sind:

   * **Titel**:

      * Dieser wird den Benutzenden angezeigt und ist obligatorisch.

   * **Name**:

      * Mit diesem Wert wird der URI generiert. Wenn kein Name angegeben ist, wird der Name vom Titel abgeleitet.
      * Wenn Sie beim Erstellen einer neuen Seite einen **Namen** für die Seite angeben, [validiert AEM den Namen entsprechend den Konventionen](/help/implementing/developing/introduction/naming-conventions.md) von AEM und JCR.
      * Die **Eingabe von ungültigen Zeichen** im Feld **Name** ist nicht zulässig. Wenn AEM ungültige Zeichen erkennt, wird das Feld hervorgehoben und eine erläuternde Meldung angezeigt, die die Zeichen angibt, die entfernt/ersetzt werden müssen.

   >[!TIP]
   >
   >Siehe [Seitenbenennungskonventionen](#page-naming-conventions)

   Zum Erstellen einer neuen Seite muss mindestens der **Titel** angegeben werden.

   ![Angeben des Seitentitels](/help/sites-cloud/authoring/assets/organizing-create-page-title.png)

1. Tippen oder klicken **Erstellen** , um den Prozess abzuschließen und Ihre neue Seite zu erstellen. Im Bestätigungsdialogfeld werden Sie gefragt, ob Sie **Öffnen** die Seite sofort öffnen oder zur Konsole zurückkehren (**Fertig**). Wählen Sie einen aus, um den Seitenerstellungsprozess zu beenden.

   ![Erfolgreiche Seitenerstellung](/help/sites-cloud/authoring/assets/organizing-create-page-success.png)

   * Wenn Sie **Öffnen**, die **Sites** -Konsole öffnet den entsprechenden Editor basierend auf der Vorlage der neuen Seite, entweder:
      * [im Seiten-Editor](/help/sites-cloud/authoring/page-editor/introduction.md)
      * [Der Universal Editor](/help/sites-cloud/authoring/universal-editor/authoring.md)

Wenn Sie zur Konsole zurückkehren, wird Ihre neue Seite angezeigt:

![Neu erstellte Seite](/help/sites-cloud/authoring/assets/organizing-create-page-result.png)

>[!NOTE]
>
>Wenn Sie eine Seite mit einem Namen erstellen, der bereits an derselben Stelle vorhanden ist, AEM die Seite mit einer Variation des Namens erstellen, die durch Anhängen einer Zahl angegeben wird. Wenn beispielsweise `beach` bereits vorhanden ist, wird die neue Seite `beach1`.

>[!CAUTION]
>
>Nachdem eine Seite erstellt wurde, kann ihre Vorlage nur geändert werden, wenn Sie [Launch mit einer neuen Vorlage erstellen](/help/sites-cloud/authoring/launches/creating.md#create-launch-with-new-template), wobei jedoch alle vorhandenen Inhalte verloren gehen.
