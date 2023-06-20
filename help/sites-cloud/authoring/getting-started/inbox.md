---
title: Ihr Posteingang
description: Verwalten Ihrer Aufgaben im Posteingang
exl-id: 37d0cf43-192f-4a50-b174-42d7dced3b63
source-git-commit: f7525b6b37e486a53791c2331dc6000e5248f8af
workflow-type: tm+mt
source-wordcount: '909'
ht-degree: 80%

---

# Ihr Posteingang {#your-inbox}

Sie können Benachrichtigungen aus verschiedenen Bereichen von AEM erhalten (darunter auch aus Workflows und Projekten). Sie erhalten beispielsweise Benachrichtigungen zu folgenden Themen:

* Aufgaben:
   * Diese können in diversen Bereichen der Benutzeroberfläche von AEM erstellt werden, z. B. unter **Projekte**.
   * Diese können das Ergebnis der Workflow-Schritte **Aufgabe erstellen** oder **Projektaufgabe erstellen** sein.
* Workflows:
   * Arbeitselemente, die Aktionen darstellen, die Sie für Seiteninhalte ausführen müssen.
      * Diese sind das Ergebnis von **Teilnehmer**-Workflow-Schritten.
   * Fehlgeschlagene Elemente, die Administratoren darauf hinweisen, einen fehlgeschlagenen Schritt erneut auszuführen.

Sie erhalten diese Benachrichtigungen in Ihrem eigenen Posteingang, in dem Sie sie anzeigen und Maßnahmen ergreifen können.

>[!NOTE]
>
>Weitere Informationen zu den Elementtypen finden Sie unter:
>
>* [Projekte](/help/sites-cloud/authoring/projects/overview.md)
>* [Projekte – Arbeiten mit Aufgaben](/help/sites-cloud/authoring/projects/tasks.md)
>* [Workflows](/help/sites-cloud/authoring/workflows/overview.md)

## Posteingang in der Kopfzeile {#inbox-in-the-header}

In sämtlichen Konsolen wird in der Kopfzeile die Anzahl der aktuell in Ihrem Posteingang vorhandenen Elemente angezeigt. Die Anzeige kann auch geöffnet werden, um einen schnellen Zugriff auf die Seiten zu ermöglichen, für die Aktionen erforderlich sind, oder um auf den Posteingang zuzugreifen:

![Übersicht über Posteingang in der Kopfzeile](/help/sites-cloud/authoring/assets/inbox-header.png)

>[!NOTE]
>
>Bestimmte Aktionen werden auch in der [Kartenansicht der jeweiligen Ressource](/help/sites-cloud/authoring/getting-started/basic-handling.md#card-view) angezeigt.

## Öffnen des Posteingangs {#opening-the-inbox}

So öffnen Sie den Benachrichtigungs-Posteingang in AEM:

1. Klicken/tippen Sie auf die Anzeige in der Symbolleiste.

1. Wählen Sie **Alle anzeigen** aus. Der **AEM-Posteingang** wird geöffnet. Im Posteingang werden Elemente aus den Bereichen Workflows, Projekte und Aufgaben angezeigt.
1. Die Standardansicht ist die [Listenansicht](#inbox-list-view), Sie können aber auch zur [Kalenderansicht ](#inbox-calendar-view)wechseln. Dies erfolgt mit der Ansichtsauswahl (Symbolleiste oben rechts).

   Für beide Ansichten können Sie die [Anzeigeeinstellungen](#inbox-view-settings) festlegen. Die verfügbaren Optionen hängen dabei von der aktuellen Ansicht ab.

   ![Anzeigeeinstellungen für den Posteingang](/help/sites-cloud/authoring/assets/inbox-view-settings.png)

>[!NOTE]
>
>Der Posteingang fungiert als Konsole. Verwenden Sie daher die [globale Navigation](/help/sites-cloud/authoring/getting-started/basic-handling.md#global-navigation) oder die [Suche](/help/sites-cloud/authoring/getting-started/search.md), um zu einer anderen Position zu navigieren, wenn Sie fertig sind.

### Posteingang – Listenansicht {#inbox-list-view}

In dieser Ansicht sind alle Elemente sowie deren relevanten Informationen aufgelistet:

![Listenansicht im Posteingang](/help/sites-cloud/authoring/assets/inbox-list-view.png)

### Posteingang – Kalenderansicht {#inbox-calendar-view}

In dieser Ansicht werden die Elemente entsprechend ihrer Position im Kalender dargestellt:

![Kalenderansicht im Posteingang](/help/sites-cloud/authoring/assets/inbox-calendar-view.png)

Sie haben folgende Möglichkeiten:

* Eine bestimmte Ansicht auswählen (**Timeline**,**Spalte** oder **Liste**)
* Aufgaben festlegen, die gemäß **Plan** angezeigt werden sollen (**Alle**, **Geplant**, **In Bearbeitung**, **Bald fällig** oder **Überfällig**)
* Detailliertere Informationen zu einem bestimmten Element anzeigen
* Einen Datumsbereich auswählen, um die Anzeige einzugrenzen:

![Datumsbereich der Kalenderansicht im Posteingang](/help/sites-cloud/authoring/assets/inbox-calendar-range.png)

### Posteingang – Anzeigeeinstellungen {#inbox-view-settings}

Für beide Ansichten (Liste und Kalender) können Sie Einstellungen definieren:

* **Kalenderansicht**

  Für **Kalenderansicht** Sie können Folgendes konfigurieren:

   * **Gruppieren nach**
   * **Zeitplan** oder **Ohne**
   * **Kartengröße**

  ![Einstellungen für die Kalenderansicht im Posteingang](/help/sites-cloud/authoring/assets/inbox-calendar-settings.png)

* **Listenansicht**

  Für **Listenansicht** Sie können den Sortiermechanismus konfigurieren:

   * **Sortieren nach**
   * **Sortierreihenfolge**

  ![Einstellungen für die Listenansicht im Posteingang](/help/sites-cloud/authoring/assets/inbox-list-settings.png)

  Sie können Ihren Kalender auch an andere Benutzer delegieren sowie die Delegierung von anderen Benutzern anfordern und Ihre Delegierungen verwalten.

  ![Delegierungseinstellungen für die Listenansicht im Posteingang](/help/sites-cloud/authoring/assets/inbox-delegation.png)

## Anwenden von Aktionen auf ein Element {#taking-action-on-an-item}

>[!NOTE]
>
>Obwohl es möglich ist, mehr als ein Element auszuwählen, können Aktionen immer nur für ein Element zur gleichen Zeit durchgeführt werden.

1. Um eine Aktion auf ein Element anzuwenden, wählen Sie die Miniatur des gewünschten Elements aus. In der Symbolleiste werden Symbole für die Aktionen angezeigt, die auf dieses Element anwendbar sind:

   ![Posteingangselement auswählen](/help/sites-cloud/authoring/assets/inbox-select-item.png)

   Die entsprechend dem ausgewählten Element verfügbaren Aktionen können Folgendes umfassen:

   * **Abschließen** einer Aktion
   * **Delegieren** eines Elements
   * **Öffnen** eines Elements, je nach Elementtyp bewirkt diese Aktion Folgendes:

      * Anzeigen der Eigenschaften des Elements
      * Öffnen des entsprechenden Dashboards oder Assistenten für weitere Aktionen
      * Aufrufen einer zugehörigen Dokumentation

   * **Schritt zurück** zu einem vorherigen Schritt
   * Anzeigen der Payload eines Workflows
   * Erstellen eines Projekts auf Basis des Elements

   >[!NOTE]
   >
   >Weitere Informationen finden Sie unter:
   >
   >* Workflow-Elemente - [Teilnehmen an Workflows](/help/sites-cloud/authoring/workflows/participating.md)

2. Abhängig vom ausgewählten Element wird eine bestimmte Aktion gestartet, z. B.:

   * Ein Dialogfeld für die jeweilige Aktion wird geöffnet
   * Ein Assistent für eine bestimmte Aktion wird gestartet
   * Eine Dokumentationsseite wird geöffnet

   Wird etwa die Aktion **Delegieren** ausgeführt, öffnet sich ein Dialogfeld:

   ![Posteingangsaufgabe delegieren](/help/sites-cloud/authoring/assets/inbox-assign-task.png)

   Je nachdem, ob ein Dialogfeld, ein Assistent oder eine Dokumentationsseite geöffnet wurde, können Sie Folgendes durchführen:

   * Die entsprechende Aktion (z. B. „Neu zuweisen“) bestätigen.
   * Die Aktion abbrechen.
   * Wählen Sie den Rückwärtspfeil aus, um zum Posteingang zurückzukehren. Wenn z. B. ein Assistent oder eine Dokumentationsseite geöffnet wurde, können Sie zum Posteingang zurückkehren.

## Erstellen einer Aufgabe {#creating-a-task}

Im Posteingang können Sie Aufgaben erstellen:

1. Auswählen **Erstellen**, dann **Aufgabe**.
1. Füllen Sie die Felder in den Registerkarten **Allgemein** und **Erweitert** aus. Obligatorisch ist hierbei nur der **Titel**, alle anderen sind optional:

   * **Allgemein**:

      * **Titel**
      * **Projekt**
      * **Bevollmächtigter**
      * **Inhalt**; dies dient, ähnlich wie bei der Payload, als Verweis von der Aufgabe auf eine Position im Repository.
      * **Beschreibung**
      * **Aufgabenpriorität**
      * **Startdatum**
      * **Fälligkeitsdatum**

   ![Posteingang – Aufgabe hinzufügen](/help/sites-cloud/authoring/assets/inbox-create-task.png)

   * **Erweitert**

      * **Name**: Wird verwendet, um die URL zu bilden, und wenn leer, basiert sie auf der **Titel**.

   ![Posteingang – Erweiterte Optionen zum Hinzufügen von Aufgaben](/help/sites-cloud/authoring/assets/inbox-add-task-advanced.png)

1. Klicken Sie auf **Übermitteln**.

## Erstellen eines Projekts {#creating-a-project}

Für bestimmte Aufgaben können Sie eine [Projekt](/help/sites-cloud/authoring/projects/overview.md) basierend auf dieser Aufgabe:

1. Wählen Sie die gewünschte Aufgabe aus, indem Sie auf die Miniaturansicht tippen/klicken.

   >[!NOTE]
   >
   >Für die Erstellung eines Projekts können nur Aufgaben verwendet werden, die im **Posteingang** über die Option **Erstellen** erstellt wurden.
   >
   >Arbeitselemente (aus einem Workflow) können nicht für die Erstellung eines Projekts verwendet werden.

1. Wählen Sie **Projekt erstellen** aus der Symbolleiste aus, um den Assistenten zu öffnen.
1. Wählen Sie die entsprechende Vorlage aus und **Nächste**.
1. Geben Sie die erforderlichen Eigenschaften an:

   * **Allgemein**

      * **Titel**
      * **Beschreibung**
      * **Startdatum**
      * **Fälligkeitsdatum**
      * **Benutzer** und Rolle

   * **Erweitert**

      * **Name**

   >[!NOTE]
   >
   >Siehe [Erstellen eines Projekts](/help/sites-cloud/authoring/projects/managing.md#creating-a-project) für vollständige Informationen.

1. Auswählen **Erstellen** , um die Aktion zu bestätigen.

## Filtern von Elementen im AEM-Posteingang {#filtering-items-in-the-aem-inbox}

Sie können die aufgeführten Elemente filtern:

1. Öffnen Sie den **AEM-Posteingang**.

1. Öffnen Sie die Filterauswahl:

   ![Posteingang – Suche](/help/sites-cloud/authoring/assets/inbox-search.png)

1. Sie können die Elemente nach verschiedenen Kriterien filtern, wobei viele davon weiter eingegrenzt werden können, z. B.:

   ![Posteingang – Suchfilter](/help/sites-cloud/authoring/assets/inbox-search-filter.png)

   >[!NOTE]
   >
   >Bei Verwendung der [Listenansicht](#inbox-list-view) können Sie außerdem über die [Anzeigeeinstellungen](#inbox-view-settings) die Sortierreihenfolge festlegen.
