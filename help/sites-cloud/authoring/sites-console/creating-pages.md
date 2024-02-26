---
title: Erstellen von Seiten
description: Erfahren Sie, wie Sie mithilfe der Sites-Konsole neue Seiten für Ihre Website erstellen.
source-git-commit: bbd845079cb688dc3e62e2cf6b1a63c49a92f6b4
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 84%

---


# Erstellen von Seiten {#creating-pages}

Erfahren Sie, wie Sie mit der **Sites** Konsole.

>[!TIP]
>
>Bevor Sie mit der Erstellung neuer Seiten beginnen, sollten Sie sich mit [wie Ihre Seiten in AEM organisiert sind.](/help/sites-cloud/authoring/sites-console/organizing-pages.md)

## Zugriffsberechtigungen {#access-privileges}

Ihr Konto muss über die entsprechenden Zugriffsrechte und Berechtigungen verfügen, um Seiten erstellen zu können.

Wenn Sie auf Probleme stoßen, empfehlen wir Ihnen, sich an die Systemadmins zu wenden.

## Erstellen einer neuen Seite {#creating-a-new-page}

Bevor Sie mit der Erstellung von Inhalten beginnen können, müssen Sie eine Seite erstellen, es sei denn, alle Seiten wurden bereits für Sie erstellt:

1. Öffnen [die **Sites** Konsole.](/help/sites-cloud/authoring/sites-console/introduction.md)
1. Navigieren Sie zu der Position, an der Sie die neue Seite erstellen möchten.
1. Öffnen Sie das Dropdown-Menü über **Erstellen** in der Symbolleiste und wählen Sie **Seite** aus der Liste aus:

   ![Erstellen von Seiten](/help/sites-cloud/authoring/assets/organizing-create-page.png)

1. Im ersten Schritt des Assistenten haben Sie folgende Möglichkeiten:

   * Wählen Sie die Vorlage, die Sie zum Erstellen der neuen Seite verwenden möchten, und wählen Sie **Weiter**, um fortzufahren.

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
      * Die **Eingabe von ungültigen Zeichen** im Feld **Name** ist nicht zulässig. Wenn AEM ungültige Zeichen erkennt, wird das Feld markiert und eine erklärende Meldung angezeigt, die auf zu entfernende/ersetzende Zeichen verweist.

   >[!TIP]
   >
   >Siehe [Seitenbenennungskonventionen](#page-naming-conventions)

   Zum Erstellen einer neuen Seite muss mindestens der **Titel** angegeben werden.

   ![Angeben des Seitentitels](/help/sites-cloud/authoring/assets/organizing-create-page-title.png)

1. Verwenden Sie **Erstellen**, um den Vorgang abzuschließen und die neue Seite zu erstellen. Im Bestätigungs-Dialogfeld werden Sie gefragt, ob Sie die Seite sofort **öffnen** oder zur Konsole zurückkehren möchten (**Fertig**):

   ![Erfolgreiche Seitenerstellung](/help/sites-cloud/authoring/assets/organizing-create-page-success.png)

   >[!NOTE]
   >
   >Wenn Sie eine Seite erstellen und dabei einen in diesem Verzeichnis bereits vorhandenen Namen verwenden, erstellt das System automatisch eine Variation des Namens, indem eine Zahl angehängt wird. Wenn beispielsweise `beach` bereits vorhanden ist, wird eine neue Seite `beach1` genannt.

1. Wenn Sie zur Konsole zurückkehren, wird die neue Seite angezeigt:

   ![Neu erstellte Seite](/help/sites-cloud/authoring/assets/organizing-create-page-result.png)

>[!CAUTION]
>
>Nachdem eine Seite erstellt wurde, kann ihre Vorlage nicht mehr geändert werden – es sei denn, Sie [erstellen einen Launch mit einer neuen Vorlage](/help/sites-cloud/authoring/launches/creating.md#create-launch-with-new-template), wobei aber der gesamte bereits vorhandene Inhalt verloren geht.
