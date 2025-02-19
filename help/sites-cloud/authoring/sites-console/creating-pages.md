---
title: Erstellen von Seiten
description: Erfahren Sie, wie Sie mithilfe der Sites-Konsole neue Seiten für Ihre Website erstellen.
exl-id: 77264562-e76a-40c8-9878-847a8878fb8e
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: ht
source-wordcount: '477'
ht-degree: 100%

---


# Erstellen von Seiten {#creating-pages}

Erfahren Sie, wie Sie mithilfe der **Sites-Konsole** neue Seiten für Ihre Website erstellen.

>[!TIP]
>
>Bevor Sie mit der Erstellung neuer Seiten beginnen, sollten Sie sich damit vertraut machen, [wie Ihre Seiten in AEM organisiert sind](/help/sites-cloud/authoring/sites-console/organizing-pages.md).

## Zugriff auf Berechtigungen {#access-privileges}

Damit Sie Seiten erstellen können, muss Ihr Konto über die entsprechenden Zugriffsrechte und Berechtigungen verfügen.

Wenn Sie auf Probleme stoßen, wenden Sie sich an Ihre Systemadmins.

## Erstellen einer neuen Seite {#creating-a-new-page}

Bevor Sie mit der Erstellung von Inhalten beginnen können, müssen Sie eine Seite erstellen, es sei denn, alle Seiten wurden bereits für Sie erstellt:

1. Öffnen Sie [die **Sites**-Konsole](/help/sites-cloud/authoring/sites-console/introduction.md).
1. Navigieren Sie zum Speicherort, an dem Sie die neue Seite erstellen möchten.
1. Öffnen Sie das Dropdown-Menü über **Erstellen** in der Symbolleiste und wählen Sie **Seite** aus der Liste aus:

   ![Erstellen von Seiten](/help/sites-cloud/authoring/assets/organizing-create-page.png)

1. Im ersten Schritt des Assistenten haben Sie folgende Möglichkeiten:

   * Wählen Sie die zum Erstellen der neuen Seite gewünschte Vorlage aus und dann **Weiter**, um fortzufahren, oder **Abbrechen**, um den Vorgang abzubrechen.
   * Vorlagen werden sowohl für den [Seiteneditor](/help/sites-cloud/authoring/page-editor/introduction.md) als auch für den [universellen Editor](/help/sites-cloud/authoring/universal-editor/templates.md) unterstützt.

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

1. Tippen oder klicken Sie auf **Erstellen**, um den Vorgang abzuschließen und die neue Seite zu erstellen. Im Bestätigungs-Dialogfeld werden Sie gefragt, ob Sie die Seite sofort **öffnen** oder zur Konsole zurückkehren möchten (**Fertig**).  Wählen Sie eine Option aus, um den Seitenerstellungsprozess zu beenden.

   ![Erfolgreiche Seitenerstellung](/help/sites-cloud/authoring/assets/organizing-create-page-success.png)

   * Wenn Sie **Öffnen** auswählen, öffnet die **Sites-Konsole** den entsprechenden Editor basierend auf der Vorlage der neuen Seite:
      * [Der Seiteneditor](/help/sites-cloud/authoring/page-editor/introduction.md)
      * [Der universelle Editor](/help/sites-cloud/authoring/universal-editor/authoring.md)

Wenn Sie zur Konsole zurückkehren, wird die neue Seite angezeigt:

![Neu erstellte Seite](/help/sites-cloud/authoring/assets/organizing-create-page-result.png)

>[!NOTE]
>
>Wenn Sie eine Seite erstellen und dabei einen Namen verwenden, der bereits am selben Speicherort vorhandenen ist, erstellt AEM die Seite mit einer Variation des Namens, indem eine Zahl angehängt wird. Wenn beispielsweise `beach` bereits vorhanden ist, wird die neue Seite `beach1` genannt.

>[!CAUTION]
>
>Nachdem eine Seite erstellt wurde, kann ihre Vorlage nicht mehr geändert werden – es sei denn, Sie [erstellen einen Launch mit einer neuen Vorlage](/help/sites-cloud/authoring/launches/creating.md#create-launch-with-new-template), wobei aber der gesamte bereits vorhandene Inhalt verloren geht.
