---
title: Ihr Posteingang
description: Verwalten Ihrer Aufgaben mit dem Posteingang
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# Ihr Posteingang {#your-inbox}

Sie können Benachrichtigungen aus verschiedenen Bereichen von AEM erhalten, einschließlich Workflows und Projekte. Sie erhalten beispielsweise Benachrichtigungen zu folgenden Themen:

* Aufgaben:
   * These can also be created at various points within the AEM UI, for example, under **Projects**.
   * These can be the product of a workflow **Create Task** or **Create Project Task** step.
* Workflows:
   * Arbeitselemente, die Aktionen darstellen, die Sie am Seiteninhalt ausführen müssen
      * These are the product of workflow **Participant** steps.
   * Fehlgeschlagene Elemente, damit Administratoren den fehlgeschlagenen Schritt wiederholen können

Sie erhalten diese Benachrichtigung in Ihrem eigenen Posteingang, in dem Sie diese anzeigen und darauf reagieren können.

>[!NOTE]
>
>Weitere Informationen zu den Elementtypen finden Sie außerdem unter:
>
>* [Projekte](/help/sites-cloud/authoring/projects/overview.md)
>* [Projekte – Arbeiten mit Aufgaben](/help/sites-cloud/authoring/projects/tasks.md)
>* [Workflows](/help/sites-cloud/authoring/workflows/overview.md)


## Posteingang in der Kopfzeile {#inbox-in-the-header}

In sämtlichen Konsolen wird in der Kopfzeile die Anzahl der aktuell in Ihrem Posteingang vorhandenen Elemente angezeigt. Sie können diese Anzeige auch öffnen, um schnell auf die Seiten zuzugreifen, auf denen Aktionen nötig sind, oder um den Posteingang aufzurufen.

![Übersicht über Postins in der Kopfzeile](/help/sites-cloud/authoring/assets/inbox-header.png)

>[!NOTE]
>
>Bestimmte Aktionen werden auch in der [Kartenansicht der jeweiligen Ressource angezeigt](/help/sites-cloud/authoring/getting-started/basic-handling.md#card-view).

## Öffnen des Posteingangs {#opening-the-inbox}

So öffnen Sie den Benachrichtigungs-Posteingang in AEM:

1. Klicken/tippen Sie auf die Anzeige in der Symbolleiste.

1. Wählen Sie **Alle anzeigen**. Der **AEM-Posteingang** wird geöffnet. Im Posteingang werden Elemente aus den Bereichen Workflows, Projekte und Aufgaben angezeigt.
1. Standardmäßig wird die [Listenansicht](#inbox-list-view) verwendet, Sie können aber auch zur [Kalenderansicht](#inbox-calendar-view) wechseln. Dies erfolgt über den Ansichtselektor oben rechts in der Symbolleiste.

   For both views you can also define [View Settings](#inbox-view-settings). The options available are dependent on the current view.

   ![Einstellungen für die Inbox-Ansicht](/help/sites-cloud/authoring/assets/inbox-view-settings.png)

>[!NOTE]
>
>The Inbox operates as a console, so use [Global Navigation](/help/sites-cloud/authoring/getting-started/basic-handling.md#global-navigation) or [Search](/help/sites-cloud/authoring/getting-started/search.md) to navigate to another location when you are finished.

### Posteingang – Listenansicht {#inbox-list-view}

Diese Ansicht listet alle Elemente zusammen mit relevanten Informationen auf:

![Ansicht der Posteingangsliste](/help/sites-cloud/authoring/assets/inbox-list-view.png)

### Posteingang – Kalenderansicht {#inbox-calendar-view}

In dieser Ansicht werden die Elemente entsprechend ihrer Position im Kalender dargestellt:

![Ansicht des Posteingangskalenders](/help/sites-cloud/authoring/assets/inbox-calendar-view.png)

Sie haben folgende Möglichkeiten:

* Select a specific view: **Timeline**, **Column**, **List**
* Specify the tasks to display according to **Schedule**: **All**, **Planned**, **In Progress**, **Due Soon**, **Past Due**
* Drilldown für detailliertere Informationen zu einem Element
* Wählen Sie einen Datumsbereich aus, um die Ansicht zu fokussieren:

![Datumsbereich der Inbox-Kalenderansicht](/help/sites-cloud/authoring/assets/inbox-calendar-range.png)

### Posteingang – Anzeigeeinstellungen {#inbox-view-settings}

Sie können für beide Ansichten (Liste und Kalender) Einstellungen festlegen:

* **Kalenderansicht**

   Für die **Kalenderansicht** können Sie Folgendes konfigurieren:

   * **Gruppieren nach**
   * **Plan** oder **Ohne**
   * **Kartengröße**
   ![Einstellungen für die Ansicht im Posteingang](/help/sites-cloud/authoring/assets/inbox-calendar-settings.png)

* **Listenansicht**

   Für die **Listenansicht** können Sie die Art der Sortierung konfigurieren:

   * **Sortieren nach**
   * **Sortierreihenfolge**
   ![Einstellungen für die Listenansicht im Posteingang](/help/sites-cloud/authoring/assets/inbox-list-settings.png)

   Sie können Ihren Kalender auch an andere Zwecke delegieren und auch eine Delegation von anderen Benutzern beantragen und Ihre Delegationen verwalten.

   ![Einstellungen für die Delegierung der Postliste](/help/sites-cloud/authoring/assets/inbox-delegation.png)

## Anwenden von Aktionen auf ein Element {#taking-action-on-an-item}

1. Um eine Aktion auf ein Element anzuwenden, wählen Sie die Miniatur des gewünschten Elements aus. In der Symbolleiste werden Symbole für die Aktionen angezeigt, die auf das Element angewendet werden können.

   ![Posteingangselement auswählen](/help/sites-cloud/authoring/assets/inbox-select-item.png)

   Die entsprechend dem ausgewählten Element verfügbaren Aktionen können Folgendes umfassen:

   * **Abschließen** der Aktion
   * **Element delegieren**
   * **Öffnen** Sie ein Element, je nach Elementtyp, den diese Aktion ausführen kann:

      * Elementeigenschaften anzeigen
      * Öffnen Sie ein geeignetes Dashboard oder einen Assistenten für weitere Aktionen
      * Offene Dokumentation
   * **Zurück** zu einem vorherigen Schritt
   * Nutzlast für einen Workflow anzeigen
   * Erstellen eines Projekts aus dem Element
   >[!NOTE]
   >
   >Weitere Informationen finden Sie unter:
   >
   >* Workflow-Elemente – [Teilnehmen an Workflows](/help/sites-cloud/authoring/workflows/participating.md)


1. Je nach ausgewähltem Element wird beispielsweise eine Aktion gestartet:

   * Ein Dialogfeld für die jeweilige Aktion wird geöffnet
   * Ein Aktionsassistent wird gestartet
   * Eine Dokumentationsseite wird geöffnet
   For example, **Delegate** will open a dialog:

   ![Posteingangsaufgabe delegieren](/help/sites-cloud/authoring/assets/inbox-assign-task.png)

   Je nachdem, ob ein Dialogfeld, ein Assistent oder eine Dokumentationsseite geöffnet wurde, können Sie Folgendes durchführen:

   * Bestätigen Sie die entsprechende Aktion, z. B. die erneute Zuweisung.
   * Die Aktion abbrechen
   * Wählen Sie den Pfeil nach hinten aus, um zum Posteingang zurückzukehren. Wenn beispielsweise ein Aktionsassistent oder eine Dokumentationsseite geöffnet wurde, können Sie zum Posteingang zurückkehren.


## Erstellen einer Aufgabe {#creating-a-task}

Sie können vom Posteingang aus Aufgaben erstellen:

1. Klicken Sie auf **Erstellen** und anschließend auf **Aufgabe**.
1. Complete the necessary fields in the **Basic** and **Advanced** tabs (only the **Title** is mandatory, all others are optional):

   * **Einfach**:

      * **Titel**
      * **Projekt**
      * **Bevollmächtigter**
      * **Content**, ähnlich wie Payload, ist dies ein Verweis von der Aufgabe zu einem Speicherort im Repository
      * **Beschreibung**
      * **Aufgabenpriorität**
      * **Startdatum**
      * **Fälligkeitsdatum**
   ![Aufgabe zum Hinzufügen per Posteingang](/help/sites-cloud/authoring/assets/inbox-create-task.png)

   * **Erweitert**

      * **Name**: Hiermit wird die URL gebildet, und wenn das Feld leer ist, basiert es auf dem **Titel**.
   ![Erweiterte Optionen zum Hinzufügen von Aufgaben im Posteingang](/help/sites-cloud/authoring/assets/inbox-add-task-advanced.png)

1. Klicken Sie auf **Übermitteln**.

## Erstellen eines Projekts {#creating-a-project}

Bei einigen Aufgaben besteht die Möglichkeit, auf deren Basis ein [Projekt](/help/sites-cloud/authoring/projects/overview.md) zu erstellen:

1. Wählen Sie die gewünschte Aufgabe aus, indem Sie auf die Miniatur tippen/klicken.

   >[!NOTE]
   >
   >Only tasks created using the **Create** option of the **Inbox** can be used to create a project.
   >
   >Arbeitselemente (aus einem Workflow) können nicht zum Erstellen eines Projekts verwendet werden.

1. Klicken Sie in der Symbolleiste auf **Projekt erstellen**, um den Assistenten zu öffnen.
1. Wählen Sie die gewünschte Vorlage und klicken Sie auf **Weiter**.
1. Geben Sie die gewünschten Eigenschaften an:

   * **Einfach**

      * **Titel**
      * **Beschreibung**
      * **Startdatum**
      * **Fälligkeitsdatum**
      * **Benutzer** und Rolle
   * **Erweitert**

      * **Name**
   >[!NOTE]
   >
   >Ausführliche Informationen hierzu finden Sie unter [Erstellen eines Projekts](/help/sites-cloud/authoring/projects/managing.md#creating-a-project).

1. Klicken Sie auf **Erstellen**, um die Aktion zu bestätigen.

## Filtern von Elementen im AEM-Posteingang {#filtering-items-in-the-aem-inbox}

Sie können die aufgeführten Elemente filtern:

1. Öffnen Sie den **AEM-Posteingang**.

1. Öffnen Sie die Filterauswahl:

   ![Posteingangssuche](/help/sites-cloud/authoring/assets/inbox-search.png)

1. Sie können die aufgelisteten Elemente nach verschiedenen Kriterien filtern, von denen viele verfeinert werden können.Beispiel:

   ![Posteingangssuchfilter](/help/sites-cloud/authoring/assets/inbox-search-filter.png)

   >[!NOTE]
   >
   >Bei Verwendung der [Listenansicht](#inbox-list-view) können Sie außerdem über die [Anzeigeeinstellungen](#inbox-view-settings) die Sortierreihenfolge festlegen.
