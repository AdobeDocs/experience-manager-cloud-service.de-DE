---
title: Teilnehmen an Workflows
description: Workflows enthalten normalerweise Schritte, bei denen eine Person eine Aktivität auf einer Seite oder in einem Asset ausführen muss.
exl-id: 62192da9-0b5b-4997-9c2b-d1aee04b01f9
source-git-commit: 635f4c990c27a7646d97ebd08b453c71133f01b3
workflow-type: tm+mt
source-wordcount: '1542'
ht-degree: 58%

---

# Teilnehmen an Workflows {#participating-in-workflows}

Workflows enthalten normalerweise Schritte, bei denen eine Person eine Aktivität auf einer Seite oder in einem Asset ausführen muss. Der Workflow wählt einen Benutzer oder eine Gruppe aus, um die Aktivität auszuführen, und weist dieser Person oder Gruppe ein Arbeitselement zu. Der Benutzer erhält eine Benachrichtigung und kann dann die entsprechenden Aktionen ausführen:

* [Ansehen der Benachrichtigungen](#notifications-of-available-workflow-actions)
* [Fertigstellen eines Teilnehmerschritts](#completing-a-participant-step)
* [Delegieren eines Teilnehmerschritts](#delegating-a-participant-step)
* [Wechseln zu einem vorherigen Teilnehmerschritt](#performing-step-back-on-a-participant-step)
* [Öffnen eines Workflow-Elements, um Details anzuzeigen (und Maßnahmen zu ergreifen)](#opening-a-workflow-item-to-view-details-and-take-actions)
* [Anzeigen der Workflow-Payload (mehrere Ressourcen)](#viewing-the-workflow-payload-multiple-resources)

## Benachrichtigungen über verfügbare Workflow-Aktionen {#notifications-of-available-workflow-actions}

Wenn Ihnen ein Arbeitselement zugewiesen wird (z. B. **Inhalte genehmigen**), werden verschiedene Warnungen und/oder Benachrichtigungen angezeigt:

* Ihre [Benachrichtigung](/help/sites-cloud/authoring/getting-started/inbox.md) Indikator (Symbolleiste) wird erhöht:

  ![Benachrichtigungssymbolleiste](/help/sites-cloud/authoring/assets/workflows-notifications.png)

* Das Element wird in Ihrer Benachrichtigung aufgeführt [Posteingang](/help/sites-cloud/authoring/getting-started/inbox.md):

  ![Benachrichtigungen im Posteingang](/help/sites-cloud/authoring/assets/workflows-inbox.png)

* Wenn Sie den Seiteneditor verwenden, wird in der Statusleiste Folgendes angezeigt:
   * Der Name des Workflows, der auf die Seite angewendet wird; z. B. Aktivierungsanfrage.
   * Alle Aktionen, die dem aktuellen Benutzer für den aktuellen Schritt des Workflows zur Verfügung stehen; z. B. Complete, Delegate, View details.
   * Die Anzahl der Workflows, denen die Seite unterliegt. Sie haben folgende Möglichkeiten:
      * Verwenden Sie die Links-/Rechtspfeile, um durch die Statusinformationen der verschiedenen Workflows zu navigieren.
      * Klicken/tippen Sie auf die tatsächliche Zahl, um eine Dropdown-Liste aller anwendbaren Workflows zu öffnen, und wählen Sie dann den Workflow aus, der in der Statusleiste angezeigt werden soll.

  ![Seite mit mehreren Workflows](/help/sites-cloud/authoring/assets/workflows-multiple.png)

  >[!NOTE]
  >
  >ie Statusleiste ist nur für Benutzer mit Workflow-Privilegien sichtbar, z. B. Mitglieder der Gruppe `workflow-users`.
  >
  >
  >Aktionen werden angezeigt, wenn der aktuelle Benutzer direkt am aktuellen Workflow-Schritt beteiligt ist.

* Wann **Timeline** für die Ressource geöffnet ist, wird der Workflow-Schritt angezeigt. Wenn Sie auf das Warnungsbanner klicken/tippen, werden auch die verfügbaren Aktionen angezeigt:

  ![Workflow in der Zeitleiste](/help/sites-cloud/authoring/assets/workflows-timeline.png)

### Fertigstellen eines Teilnehmerschritts {#completing-a-participant-step}

Sie können ein Element abschließen, damit der Workflow mit dem nächsten Schritt fortfahren kann.

Bei dieser Aktion können Sie Folgendes angeben:

* **Nächster Schritt**: den nächsten Schritt, der zu unternehmen ist; Sie können aus einer Liste auswählen, die
* **Kommentar**: falls erforderlich

Sie können einen Teilnehmerschritt wie folgt abschließen:

* [im Posteingang](#completing-a-participant-step-inbox)
* [im Seiten-Editor](#completing-a-participant-step-page-editor)
* [in der Timeline](#completing-a-participant-step-timeline)
* beim [Öffnen eines Workflow-Elements zur Ansicht von Details](#opening-a-workflow-item-to-view-details-and-take-actions).

#### Durchführen eines Teilnehmerschritts: Posteingang {#completing-a-participant-step-inbox}

Führen Sie die folgenden Schritte aus, um das Arbeitselement abzuschließen:

1. Öffnen Sie den **[AEM-Posteingang](/help/sites-cloud/authoring/getting-started/inbox.md)**.
1. Wählen Sie das Workflow-Element aus, für das Sie eine Aktion ausführen möchten (tippen/klicken Sie auf die Miniatur).
1. Wählen Sie in der Symbolleiste die Option **Fertig stellen** aus.
1. Das Dialogfeld **Arbeits-Element fertig stellen** wird geöffnet. Wählen Sie im Dropdown-Selektor die Option **Nächster Schritt** aus und fügen Sie bei Bedarf einen **Kommentar** hinzu.
1. Verwenden Sie **OK**, um den Schritt abzuschließen (oder **Abbrechen**, um den Vorgang abzubrechen).

#### Durchführen eines Teilnehmerschritts: Seiten-Editor {#completing-a-participant-step-page-editor}

Führen Sie die folgenden Schritte aus, um das Arbeitselement abzuschließen:

1. Öffnen Sie die [Seite zur Bearbeitung](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#opening-a-page-for-editing).
1. Wählen Sie in der Statusleiste oben im Bild **Fertig stellen** aus.
1. Das Dialogfeld **Arbeits-Element fertig stellen** wird geöffnet. Wählen Sie im Dropdown-Selektor die Option **Nächster Schritt** aus und fügen Sie bei Bedarf einen **Kommentar** hinzu.
1. Verwenden Sie **OK**, um den Schritt abzuschließen (oder **Abbrechen**, um den Vorgang abzubrechen).

#### Durchführen eines Teilnehmerschritts: Zeitleiste {#completing-a-participant-step-timeline}

Sie können auch die Zeitleiste verwenden, um einen Schritt abzuschließen und zum nächsten Schritt zu gelangen:

1. Wählen Sie die entsprechende Seite aus und öffnen Sie die **Timeline** (oder öffnen Sie die **Timeline** und wählen Sie die Seite aus):

   ![Fertigstellen eines Schritts](/help/sites-cloud/authoring/assets/workflows-timeline-completing.png)

1. Klicken/tippen Sie auf das Warnbanner, um die verfügbaren Aktionen anzuzeigen. Auswählen **Voranbringen**:

   ![Schritt voranbringen](/help/sites-cloud/authoring/assets/workflows-timeline-advance.png)

1. Je nach Workflow können Sie den nächsten Schritt auswählen:

   ![Auswählen des nächsten Schritts](/help/sites-cloud/authoring/assets/workflows-next-step.png)

1. Wählen Sie **Voranbringen**, um die Aktion zu bestätigen.

### Delegieren eines Teilnehmerschritts {#delegating-a-participant-step}

Wenn Ihnen ein Schritt zugewiesen wurde, Sie jedoch aus irgendeinem Grund keine Aktion ausführen können, können Sie den Schritt an einen anderen Benutzer oder eine andere Gruppe delegieren.

Die Benutzer, die für die Zuweisung verfügbar sind, hängen davon ab, wem das Arbeitselement zugewiesen wurde:

* Wenn das Arbeitselement einer Gruppe zugewiesen wurde, sind die Gruppenmitglieder verfügbar.
* Wenn das Arbeitselement einer Gruppe zugewiesen und dann an einen Benutzer delegiert wurde, sind die Gruppenmitglieder und die Gruppe verfügbar.
* Wenn das Arbeitselement einem einzelnen Benutzer zugewiesen wurde, kann es nicht delegiert werden.

Bei dieser Aktion können Sie Folgendes angeben:

* **Benutzer**: den Benutzer, an den Sie delegieren möchten; Sie können aus einer Liste auswählen, die
* **Kommentar**: falls erforderlich

Sie können einen Teilnehmerschritt delegieren, indem Sie entweder:

* [im Posteingang](#delegating-a-participant-step-inbox)
* [im Seiten-Editor](#delegating-a-participant-step-page-editor)
* [in der Timeline](#delegating-a-participant-step-timeline)
* beim [Öffnen eines Workflow-Elements zur Ansicht von Details](#opening-a-workflow-item-to-view-details-and-take-actions).

#### Delegieren eines Teilnehmerschritts: Posteingang {#delegating-a-participant-step-inbox}

Gehen Sie wie folgt vor, um ein Arbeitselement zu delegieren:

1. Öffnen Sie den **[AEM-Posteingang](/help/sites-cloud/authoring/getting-started/inbox.md)**.
1. Wählen Sie das Workflow-Element aus, für das Sie eine Aktion ausführen möchten (tippen/klicken Sie auf die Miniatur).
1. Wählen Sie in der Symbolleiste die Option **Delegieren** aus.
1. Das Dialogfeld wird geöffnet. Wählen Sie im Dropdown-Selektor den **Benutzer** aus (dabei kann es sich auch um eine Gruppe handeln) und fügen Sie bei Bedarf einen **Kommentar** hinzu.
1. Verwenden Sie **OK**, um den Schritt abzuschließen (oder **Abbrechen**, um den Vorgang abzubrechen).

#### Delegieren eines Teilnehmerschritts: Seiten-Editor {#delegating-a-participant-step-page-editor}

Gehen Sie wie folgt vor, um ein Arbeitselement zu delegieren:

1. Öffnen Sie die [Seite zur Bearbeitung](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#opening-a-page-for-editing).
1. Wählen Sie in der Statusleiste oben im Bild **Delegieren** aus.
1. Das Dialogfeld wird geöffnet. Wählen Sie im Dropdown-Selektor den **Benutzer** aus (dabei kann es sich auch um eine Gruppe handeln) und fügen Sie bei Bedarf einen **Kommentar** hinzu.
1. Verwenden Sie **OK**, um den Schritt abzuschließen (oder **Abbrechen**, um den Vorgang abzubrechen).

#### Delegieren eines Teilnehmerschritts: Zeitleiste {#delegating-a-participant-step-timeline}

Sie können auch die Zeitleiste verwenden, um einen Schritt zu delegieren und/oder zuzuweisen:

1. Wählen Sie die entsprechende Seite aus und öffnen Sie die **Zeitleiste** (oder öffnen Sie die **Zeitleiste** und wählen Sie die Seite aus).
1. Klicken/tippen Sie auf das Warnbanner, um die verfügbaren Aktionen anzuzeigen. Auswählen **Zuweisung ändern**:

   ![Schritt „Delegieren“](/help/sites-cloud/authoring/assets/workflows-delegate.png)

1. Legen Sie einen neuen Bevollmächtigten fest:

   ![Bevollmächtigten ändern](/help/sites-cloud/authoring/assets/workflows-assignee.png)

1. Wählen Sie **Zuweisen** aus, um die Aktion zu bestätigen.

### Wechseln zu einem vorherigen Teilnehmerschritt {#performing-step-back-on-a-participant-step}

Wenn Sie erkennen, dass ein Schritt oder eine Reihe von Schritten wiederholt werden muss, können Sie zu einem vorherigen Schritt zurückkehren. Auf diese Weise können Sie einen früheren Schritt im Workflow zur erneuten Verarbeitung auswählen. Der Workflow kehrt zu dem von Ihnen angegebenen Schritt zurück und fährt dann von dort fort.

Bei dieser Aktion können Sie Folgendes angeben:

* **Vorheriger Schritt**: der Schritt, der zurückgegeben werden soll; Sie können aus einer Liste auswählen, die
* **Kommentar**: falls erforderlich

Sie können einen Schritt zurück zu einem Teilnehmerschritt ausführen:

* [im Posteingang](#performing-step-back-on-a-participant-step-inbox)
* [im Seiten-Editor](#performing-step-back-on-a-participant-step-page-editor)
* [in der Timeline](#performing-step-back-on-a-participant-step-timeline)
* beim [Öffnen eines Workflow-Elements zur Ansicht von Details](#opening-a-workflow-item-to-view-details-and-take-actions).

#### Wechseln zu einem vorherigen Teilnehmerschritt: Posteingang {#performing-step-back-on-a-participant-step-inbox}

Gehen Sie wie folgt vor, um zurückzutreten:

1. Öffnen Sie den **[AEM-Posteingang](/help/sites-cloud/authoring/getting-started/inbox.md)**.
1. Wählen Sie das Workflow-Element aus, für das Sie eine Aktion ausführen möchten (tippen/klicken Sie auf die Miniatur).
1. Wählen Sie **Schritt zurück** aus, um das Dialogfeld zu öffnen.
1. Wählen Sie **Vorheriger Schritt** aus und fügen Sie bei Bedarf einen **Kommentar** hinzu.
1. Verwenden Sie **OK**, um den Schritt abzuschließen (oder **Abbrechen**, um den Vorgang abzubrechen).

#### Wechseln zu einem vorherigen Teilnehmerschritt: Seiten-Editor {#performing-step-back-on-a-participant-step-page-editor}

Gehen Sie wie folgt vor, um zurückzutreten:

1. Öffnen Sie die [Seite zur Bearbeitung](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#opening-a-page-for-editing).
1. Wählen Sie in der Symbolleiste oben im Bild **Schritt zurück** aus.
1. Wählen Sie **Vorheriger Schritt** aus und fügen Sie bei Bedarf einen **Kommentar** hinzu.
1. Verwenden Sie **OK**, um den Schritt abzuschließen (oder **Abbrechen**, um den Vorgang abzubrechen).

#### Wechseln zu einem vorherigen Teilnehmerschritt: Zeitleiste {#performing-step-back-on-a-participant-step-timeline}

Sie können auch die Zeitleiste verwenden, um zu einem vorherigen Schritt zurückzukehren:

1. Wählen Sie die entsprechende Seite aus und öffnen Sie die **Zeitleiste** (oder öffnen Sie die **Zeitleiste** und wählen Sie die Seite aus).
1. Klicken/tippen Sie auf das Warnbanner, um die verfügbaren Aktionen anzuzeigen. Auswählen **Zurücksetzen**:

   ![Schritt zurücksetzen](/help/sites-cloud/authoring/assets/workflows-roll-back.png)

1. Geben Sie den Schritt an, an den der Workflow zurückkehren soll:

   ![Schritt angeben](/help/sites-cloud/authoring/assets/workflows-roll-back-step.png)

1. Wählen Sie **Zurücksetzen** aus, um die Aktion zu bestätigen.

### Öffnen eines Workflow-Elements, um Details anzuzeigen (und Maßnahmen zu ergreifen) {#opening-a-workflow-item-to-view-details-and-take-actions}

Zeigen Sie Details zum Workflow-Arbeitselement an und ergreifen Sie die entsprechenden Aktionen.

Die Workflow-Details werden in Registerkarten angezeigt und die entsprechenden Aktionen sind in der Symbolleiste verfügbar:

* Registerkarte **ARBEITSELEMENT**:

  ![Registerkarte „ARBEITSELEMENT“](/help/sites-cloud/authoring/assets/workflows-work-item.png)

* Registerkarte **WORKFLOW-INFORMATIONEN**:

  ![Registerkarte „WORKFLOW“](/help/sites-cloud/authoring/assets/workflows-workflow-info.png)

  Wenn für das Modell die Option Workflow-Status konfiguriert wurde, können Sie den Fortschritt entsprechend dem Status anzeigen: <!--If [Workflow Stages](/help/sites-developing/workflows.md#workflow-stages) have been configured for the model, you can view the progress according to these:-->

  ![Workflow-Phasen](/help/sites-cloud/authoring/assets/workflows-workflow-stages.png)

* Registerkarte **KOMMENTARE**:

  ![Registerkarte „KOMMENTARE“](/help/sites-cloud/authoring/assets/workflows-comments.png)

Das Öffnen der Details der Arbeitselemente ist möglich:

* [im Posteingang](#performing-step-back-on-a-participant-step-inbox)
* [im Seiten-Editor](#performing-step-back-on-a-participant-step-page-editor)

#### Öffnen der Workflow-Details: Posteingang {#opening-workflow-details-inbox}

So öffnen Sie ein Workflow-Element und zeigen die Details an:

1. Öffnen Sie den **[AEM-Posteingang](/help/sites-cloud/authoring/getting-started/inbox.md)**.
1. Wählen Sie das Workflow-Element aus, für das Sie eine Aktion ausführen möchten (tippen/klicken Sie auf die Miniatur).
1. Wählen Sie **Öffnen** aus, um die Informationsregisterkarten zu öffnen.
1. Wählen Sie bei Bedarf die geeignete Aktion aus, geben Sie etwaige Details ein und bestätigen Sie mit **OK** (oder **Abbrechen**).
1. Mit **Speichern** oder **Abbrechen** schließen Sie das Dialogfeld.

#### Öffnen von Workflow-Details: Seiten-Editor {#opening-workflow-details-page-editor}

So öffnen Sie ein Workflow-Element und zeigen die Details an:

1. Öffnen Sie die [Seite zur Bearbeitung](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#opening-a-page-for-editing).
1. Wählen Sie aus der Statusleiste **Details anzeigen** aus, um die Informationsregisterkarten zu öffnen.
1. Wählen Sie bei Bedarf die geeignete Aktion aus, geben Sie etwaige Details ein und bestätigen Sie mit **OK** (oder **Abbrechen**).
1. Mit **Speichern** oder **Abbrechen** schließen Sie das Dialogfeld.

### Ansicht der Workflow-Payload (mehrere Ressourcen) {#viewing-the-workflow-payload-multiple-resources}

Sie können sich Details zur Payload anzeigen lassen, die mit der Workflow-Instanz verbunden ist. Zunächst werden die Ressourcen im Paket angezeigt. Anschließend können Sie einen Drilldown durchführen, um die einzelnen Seiten anzuzeigen.

So zeigen Sie die Payload und die Ressourcen der Workflow-Instanz an:

1. Öffnen Sie den **[AEM-Posteingang](/help/sites-cloud/authoring/getting-started/inbox.md)**.
1. Wählen Sie das Workflow-Element aus, für das Sie eine Aktion ausführen möchten (tippen/klicken Sie auf die Miniatur).
1. Wählen Sie in der Symbolleiste **Nutzdaten anzeigen** aus, um den Dialog zu öffnen.
   * Da ein Workflow-Paket lediglich eine Sammlung von Verweisen auf Pfade innerhalb des Repositorys ist, können Sie die Einträge hier hinzufügen/entfernen/ändern, um den Verweis des Workflow-Pakets anzupassen. Verwenden Sie die **Ressourcendefinition** -Komponente, um neue Einträge hinzuzufügen.
1. Mit den Links können die einzelnen Seiten geöffnet werden.
