---
title: Veröffentlichen von Seiten über die Sites-Konsole
description: Erfahren Sie, wie Sie Ihre Seiten über die Sites-Konsole veröffentlichen oder ihre Veröffentlichung rückgängig machen können.
exl-id: 89f2363c-7922-4ca5-92cb-cbee6a393ee3
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 5ad91a32d705ef61e8b9799bf7fb1e136bb8bfa0
workflow-type: ht
source-wordcount: '1635'
ht-degree: 100%

---


# Veröffentlichen von Seiten über die Sites-Konsole {#publishing-pages}

Nachdem Sie Ihren Inhalt in der Authoring-Umgebung erstellt und überprüft haben, ist es Ihr Ziel, ihn auf Ihrer [öffentlichen Website (Ihrer Publishing-Umgebung) zur Verfügung zu stellen](/help/sites-cloud/authoring/author-publish.md).

Dies wird als Veröffentlichen einer Seite bezeichnet. Wenn Sie eine Seite aus der Publishing-Umgebung entfernen möchten, wird dies als Aufheben der Veröffentlichung bezeichnet. Beim Veröffentlichen und beim Aufheben der Veröffentlichung bleibt die Seite in der Autorenumgebung für weitere Änderungen verfügbar, bis Sie diese löschen.

Sie können die [**Sites-Konsole**](/help/sites-cloud/authoring/sites-console/introduction.md) verwenden, um eine Seite sofort oder zu einem vordefinierten Datum/Zeitpunkt in der Zukunft zu veröffentlichen oder die Veröffentlichung rückgängig zu machen.

>[!TIP]
>
>Sie können auch über andere Speicherorte als die Sites-Konsole veröffentlichen.
>
>* [Im Seiteneditor](/help/sites-cloud/authoring/page-editor/publishing.md)
>* [Im universellen Editor](/help/sites-cloud/authoring/universal-editor/publishing.md)
>* [Über die Experience Fragment-Konsole](/help/sites-cloud/authoring/fragments/experience-fragments.md) oder den -Editor
>
>Veröffentlichungen über diese Speicherorte bieten jeweils verschiedene Optionen, folgen jedoch ähnlichen Verfahren und allgemeinen Ideen, die hier beschrieben werden.

## Terminologie {#terminology}

Bei der Arbeit mit Adobe Experience Manager (AEM) as a Cloud Service können Sie auf unterschiedliche Begriffe im Zusammenhang mit der Veröffentlichung stoßen.

* **Veröffentlichen/Veröffentlichung rückgängig machen**
   * Dies sind die Hauptbegriffe für die Aktionen, mit denen Sie Ihren Inhalt in Ihrer Veröffentlichungs- und/oder Vorschauumgebung verfügbar machen (oder dies rückgängig machen).
   * Dies sind die in der AEM-Dokumentation verwendeten Begriffe.
* **Aktivieren/Deaktivieren**
   * Diese Begriffe sind Synonyme für das Veröffentlichen/Rückgängigmachen der Veröffentlichung.
   * Diese Begriffe wurden in früheren Versionen von AEM verwendet.
* **Replizieren/Replikation**
   * Dies sind die technischen Begriffe, die beim Veröffentlichen einer Seite für die Verschiebung von Daten (z. B. Seiteninhalte, Dateien, Code, Benutzerkommentare) zwischen Services verwendet werden (z. B. vom Erstellen zur Vorschau).
   * Diese Begriffe werden hauptsächlich von Entwicklerinnen und Entwicklern verwendet.

>[!NOTE]
>
>Wenn Sie nicht über die erforderlichen Berechtigungen zum Veröffentlichen einer bestimmten Seite verfügen, geschieht Folgendes:
>
>* Ein Workflow wird ausgelöst, um die zuständige Person über Ihren Antrag auf Veröffentlichung zu informieren.
>* Dieser Workflow wurde möglicherweise von Ihrem Entwickler-Team angepasst.
>* Sie werden in einer Mitteilung darüber informiert, dass der Workflow ausgelöst wurde.

>[!NOTE]
>
>Wenn Sie die Seitenreihenfolge beibehalten möchten, müssen Sie [Veröffentlichung verwalten](#manage-publication) verwenden, um die übergeordnete Seite zusammen mit allen untergeordneten Seiten in einer einzigen Aktion zu veröffentlichen.
>
>Die Seitenreihenfolge ist in folgenden Situationen nicht garantiert:
>
>* wenn nur untergeordnete Seiten zur Veröffentlichung ausgewählt sind (die Informationen zur Reihenfolge sind nämlich auf der übergeordneten Seite gespeichert)
>* wenn die über- und untergeordneten Seiten in separaten Aktionen veröffentlicht werden

## Veröffentlichen von Seiten über die Sites-Konsole {#publishing-from-the-sites-console}

In der **Sites**-Konsole gibt es zwei Möglichkeiten zur Veröffentlichung:

* [Quick Publish](#quick-publish)
* [Veröffentlichung verwalten](#manage-publication)

### Quick Publish {#quick-publish}

**Quick Publish** wird für einfache Fälle verwendet. Die ausgewählten Seiten werden damit sofort ohne weitere Interaktion veröffentlicht. Aus diesem Grund werden alle nicht-veröffentlichten Verweise ebenfalls automatisch veröffentlicht.

So veröffentlichen Sie eine Seite mit der Funktion „Quick Publish“:

1. Wählen Sie die gewünschten Seiten in der Sites-Konsole aus und klicken Sie auf die Schaltfläche **Quick Publish**.

   ![Auswählen von Seiten zur Veröffentlichung](/help/sites-cloud/authoring/assets/publishing-select-pages.png)

1. Bestätigen Sie im Dialogfeld „Quick Publish“ die Veröffentlichung, indem Sie auf **Veröffentlichen** klicken, oder brechen Sie den Vorgang ab, indem Sie auf **Abbrechen** klicken. Beachten Sie, dass auch alle unveröffentlichten Verweise ebenfalls automatisch veröffentlicht werden.

   ![Quick Publish-Bestätigung](/help/sites-cloud/authoring/assets/publishing-quick-publish.png)

1. Bei der Veröffentlichung der Seite wird ein Warnhinweis angezeigt, in dem die Veröffentlichung bestätigt wird.

>[!NOTE]
>
>Die Option „Schnell veröffentlichen“ ermöglicht nur die teilweise Veröffentlichung, d. h. nur die ausgewählten Seiten werden veröffentlicht, aber keine untergeordneten Seiten.

### Veröffentlichung verwalten {#manage-publication}

**Veröffentlichung verwalten** bietet mehr Optionen als **Schnell veröffentlichen**. Mit diesen können Sie auch untergeordnete Seiten einschließen, Verweise anpassen, etwas in einem Vorschau-Service veröffentlichen (sofern verfügbar), alle nötigen Workflows starten und bei Bedarf zu einem späteren Zeitpunkt veröffentlichen.

So veröffentlichen Sie mit „Veröffentlichung verwalten“ eine Seite bzw. machen ihre Veröffentlichung rückgängig:

1. Wählen Sie in der Sites-Konsole die entsprechenden Seiten aus und klicken Sie auf die Schaltfläche **Veröffentlichung verwalten**.

   ![Auswählen von Seiten zur Veröffentlichung](/help/sites-cloud/authoring/assets/publishing-select-pages.png)

1. Der Assistent **Veröffentlichung verwalten** wird geöffnet. Im ersten Schritt, **Optionen**, haben Sie folgende Möglichkeiten:

   * **Aktion**

     Veröffentlichen Sie die ausgewählte Seite oder machen Sie die Veröffentlichung rückgängig.

   * **Ziel**

     Wählen Sie aus, ob Sie im Veröffentlichungs-Service (Standard) oder im Vorschau-Service veröffentlichen möchten. Nur verfügbar, wenn Sie einen [Vorschau-Service konfiguriert haben](/help/sites-cloud/authoring/sites-console/previewing-content.md).

   * **Zeitplan**

     Entscheiden Sie, ob Sie diese Aktion jetzt oder zu einem späteren Zeitpunkt durchführen möchten.

     Bei späterer Veröffentlichung wird ein Workflow gestartet, um die ausgewählte(n) Seite(n) zum angegebenen Zeitpunkt zu veröffentlichen. Umgekehrt startet „Veröffentlichung aufheben“ später einen Workflow zum Aufheben der Veröffentlichung der ausgewählte(n) Seite(n) zu einem angegebenen Zeitpunkt.

     >[!TIP]
     >
     >Wenn Sie eine Veröffentlichung/rückgängig gemachte Veröffentlichung später abbrechen möchten, gehen Sie zur Konsole [Workflow](/help/sites-cloud/administering/workflows-administering.md#suspending-resuming-and-terminating-a-workflow-instance), um den entsprechenden Workflow zu beenden.

     >[!TIP]
     >
     >Bei der Planung von Inhalten für die Veröffentlichung werden Inhalte repliziert und Veröffentlichungs-Workflows berücksichtigt. Wenn Sie bereits veröffentlichte Inhalte vorübergehend ausblenden möchten, ohne die Veröffentlichung rückgängig zu machen, sollten Sie die in den Seiteneigenschaften verfügbare [**Einschaltzeit** und **Ausschaltzeit** in Erwägung ziehen.](/help/sites-cloud/authoring/sites-console/page-properties.md#basic)

   ![Veröffentlichungsoptionen verwalten](/help/sites-cloud/authoring/assets/publishing-manage-publication-options.png)

1. Klicken Sie auf **Weiter**, um fortzufahren.

1. Im nächsten Schritt des Assistenten „Veröffentlichung verwalten“ können Sie den **Umfang** der Veröffentlichung/der rückgängig gemachten Veröffentlichung definieren, wie z. B. das Einschließen von untergeordneten Seiten und/oder von Verweisen.

   ![Umfang der Veröffentlichung verwalten](/help/sites-cloud/authoring/assets/publishing-manage-publication-scope.png)

   **Inhalt hinzufügen**

   Mit der Schaltfläche **Inhalt hinzufügen** können Sie zusätzliche Seiten zur Liste der zu veröffentlichenden Seiten hinzufügen, falls Sie dies noch nicht vor dem Starten des Assistenten „Veröffentlichung verwalten“ getan haben.

   Durch Klicken auf die Schaltfläche **Inhalt hinzufügen** wird der [Pfad-Browser](/help/sites-cloud/authoring/path-selection.md) gestartet, mit dem Inhalte ausgewählt werden können.

   Wählen Sie die gewünschten Seiten aus und klicken Sie dann auf **Auswählen**, um den Inhalt dem Assistenten hinzuzufügen, oder auf **Abbrechen**, um die Auswahl abzubrechen und zum Assistenten zurückzukehren.

   **Auswahl entfernen**

   Im Assistenten können Sie ein Element in der Liste auswählen, um es aus der Auswahl zu entfernen.

   ![Verwalten von Veröffentlichungen mit Seitenauswahl](/help/sites-cloud/authoring/assets/publishing-manage-publication-select.png)

   **Veröffentlichte Verweise**

   Zur Ansicht und zum Ändern der Verweise, die für eine Seite veröffentlicht werden sollen bzw. deren Veröffentlichung rückgängig gemacht werden soll, wählen Sie sie aus und klicken Sie anschließend auf die Schaltfläche **Veröffentlichte Verweise**.

   ![Veröffentlichungsoptionen verwalten](/help/sites-cloud/authoring/assets/publishing-manage-publication-references.png)

   Das Dialogfeld **Veröffentlichte Verweise** zeigt die Verweise für den ausgewählten Inhalt an. Standardmäßig sind alle ausgewählt und werden veröffentlicht bzw. die Veröffentlichung wird rückgängig gemacht. Sie können aber auch einzelne deaktivieren, um die Auswahl aufzuheben, sodass sie nicht in die Aktion einbezogen werden.

   Klicken Sie auf **Fertig**, um Ihre Änderungen zu speichern, oder auf **Abbrechen**, um die Auswahl abzubrechen und zum Assistenten zurückzukehren.

   Im Assistenten wird die Spalte **Verweise** aktualisiert und zeigt Ihre Auswahl von Verweisen an, die veröffentlicht werden sollen bzw. deren Veröffentlichung rückgängig gemacht werden soll.

   ![Verwalten von Veröffentlichungen mit Seitenauswahl](/help/sites-cloud/authoring/assets/publishing-manage-publication-select.png)

   **Untergeordnete Elemente einbeziehen**

   >[!NOTE]
   >
   >Siehe [Veröffentlichen und Rückgängigmachen der Veröffentlichung eines Baums](#publishing-and-unpublishing-a-tree)

   Wenn Sie auf **Untergeordnete Elemente einbeziehen** klicken, öffnet sich ein Dialogfeld, in dem Sie die entsprechenden Einstellungen vornehmen können:

   * **Untergeordnete Elemente einbeziehen**
   * **Nur unmittelbar untergeordnete Elemente einbeziehen**
   * **Nur geänderte Seiten einbeziehen**
   * **Nur bereits veröffentlichte Seiten einbeziehen**

   Aktivieren Sie die erforderlichen Optionen und bestätigen Sie mit **OK**, um die untergeordneten Seiten zur Liste der Seiten hinzuzufügen, die je nach Auswahloptionen veröffentlicht werden sollen oder deren Veröffentlichung rückgängig gemacht werden soll. Klicken Sie auf **Abbrechen**, um die Auswahl abzubrechen und zum Assistenten zurückzukehren.

   ![Verwalten von Veröffentlichungen einschließlich untergeordneter Elemente](/help/sites-cloud/authoring/assets/publishing-include-children.png)

1. Klicken Sie auf **Veröffentlichen**, um den Vorgang abzuschließen.

   In der Sites-Konsole wird die Veröffentlichung durch eine Benachrichtigung bestätigt.

1. Wenn die veröffentlichten Seiten mit Workflows verknüpft sind, werden diese im abschließenden **Workflow**-Schritt des Veröffentlichungsassistenten gezeigt.

   ![Verwalten von Veröffentlichungen mit Seitenauswahl](/help/sites-cloud/authoring/assets/publishing-manage-publication-workflow.png)

   >[!NOTE]
   >
   >Der gezeigte **Workflow**-Schritt hängt von den Rechten der jeweiligen Person ab. Weitere Informationen finden Sie im vorherigen Hinweis auf dieser Seite bezüglich Berechtigungen für die Veröffentlichung sowie unter „Verwaltung der Zugriffsrechte auf Workflows“ und unter [Anwenden von Workflows auf Seiten](/help/sites-cloud/authoring/workflows/applying.md).

   Die Ressourcen werden nach den ausgelösten Workflows gruppiert und erhalten jeweils folgende Optionen:

   * Definieren des Workflow-Titels
   * Beibehalten des Workflow-Pakets, vorausgesetzt der Workflow unterstützt mehrere Ressourcen.
   * Definieren des Titels des Workflow-Pakets, sofern die Option zum Beibehalten des Workflow-Pakets ausgewählt wurde

1. Klicken Sie auf **Veröffentlichen** oder **Später veröffentlichen**, um die Veröffentlichung abzuschließen.

## Veröffentlichen von Seiten rückgängig machen {#unpublishing-pages}

Wenn Sie die Veröffentlichung einer Seite rückgängig machen, wird sie aus der Veröffentlichungs- oder [Vorschauumgebung](/help/sites-cloud/authoring/sites-console/previewing-content.md) gelöscht, sodass sie nicht mehr für Ihre Leserschaft verfügbar ist.

Ebenso wie Sie [die Option „Veröffentlichung verwalten“ zur Veröffentlichung verwenden](#manage-publication), können Sie damit auch eine Veröffentlichung aufheben.

1. Wählen Sie in der Sites-Konsole die entsprechenden Seiten aus und klicken Sie auf die Schaltfläche **Veröffentlichung verwalten**.
1. Der Assistent **Veröffentlichung verwalten** wird geöffnet. Wählen Sie im ersten Schritt **Optionen** die Option **Veröffentlichung aufheben** anstelle der Standardoption **Veröffentlichen** aus.

   ![Veröffentlichung rückgängig machen – Optionen](/help/sites-cloud/authoring/assets/publishing-unpublish.png)

   Die Auswahl von „Später veröffentlichen“ startet einen Workflow zur Veröffentlichung der Seite zum angegebenen Zeitpunkt. Entsprechend startet die Auswahl von „Später deaktivieren“ einen Workflow zum Rückgängigmachen der Veröffentlichung der ausgewählten Seiten zum angegebenen Zeitpunkt.

   >[!NOTE]
   >
   >Wenn Sie eine Veröffentlichung/rückgängig gemachte Veröffentlichung später abbrechen möchten, gehen Sie zur Konsole [Workflow](/help/sites-cloud/administering/workflows-administering.md#suspending-resuming-and-terminating-a-workflow-instance), um den entsprechenden Workflow zu beenden.

   >[!NOTE]
   >Wenn Sie eine [Vorschau](/help/sites-cloud/authoring/sites-console/previewing-content.md)-Umgebung haben, können Sie das **Ziel** während des Schritts „Veröffentlichung verwalten“ auswählen.

1. Um das Rückgängigmachen der Veröffentlichung abzuschließen, fahren Sie mit dem Assistenten ähnlich wie beim [Veröffentlichen der Seite](#manage-publication) fort.

   ![Veröffentlichung rückgängig machen – Umfang](/help/sites-cloud/authoring/assets/publishing-unpublish-scope.png)

## Veröffentlichen und Rückgängigmachen der Veröffentlichung eines Baums {#publishing-and-unpublishing-a-tree}

Wenn Sie eine beträchtliche Anzahl von Inhaltsseiten eingegeben oder aktualisiert haben, die sich alle unter derselben Stammseite befinden, kann es praktischer sein, mit einer einzigen Aktion die gesamte Baumstruktur zu veröffentlichen.

Sie können dazu die Option [Veröffentlichung verwalten](#manage-publication) auf der Sites-Konsole verwenden.

1. Wählen Sie in der Sites-Konsole die Stammseite des Baums aus, den Sie veröffentlichen bzw. dessen Veröffentlichung Sie aufheben möchten, und wählen Sie **Veröffentlichung verwalten** aus.
1. Der Assistent **Veröffentlichung verwalten** wird geöffnet. Wählen Sie „Veröffentlichen“ oder „Veröffentlichung aufheben“ sowie den Zeitpunkt aus und danach **Weiter**, um fortzufahren.
1. Wählen Sie im Schritt **Umfang** die Stammseite aus und wählen Sie **Untergeordnete Elemente einschließen** aus.

   ![Verwalten von Veröffentlichungen mit Seitenauswahl](/help/sites-cloud/authoring/assets/publishing-manage-publication-select.png)

1. Führen Sie im Dialogfeld **Untergeordnete Elemente einschließen** folgende Schritte aus:

   * Wählen Sie **Untergeordnete Elemente einschließen** aus
   * Wählen Sie **Nur unmittelbar untergeordnete Elemente einbeziehen** ab
   * Wählen Sie **Nur bereits veröffentlichte Seiten einbeziehen** ab
   * Konfigurieren Sie **Nur geänderte Seiten einbeziehen** nach Bedarf

   Diese Optionen sind standardmäßig ausgewählt. Sie müssen also darauf achten, sie zu konfigurieren. Bestätigen Sie die Auswahl mit **OK**, um den Inhalt zur Veröffentlichung/Rückgängigmachung der Veröffentlichung hinzuzufügen.

   ![Untergeordnete Elemente für die Veröffentlichung eines Baums einschließen](/help/sites-cloud/authoring/assets/publishing-include-children-tree.png)

1. Im Assistenten **Veröffentlichung verwalten** können Sie die Auswahl weiter anpassen, indem Sie zusätzliche Seiten hinzufügen oder die ausgewählten Seiten entfernen.

   Sie können die zu veröffentlichenden Verweise auch in der Option **Veröffentlichte Verweise** überprüfen.

1. [Fahren Sie mit dem Assistenten „Veröffentlichung verwalten“ wie üblich fort](#manage-publication), um die Veröffentlichung oder das Rückgängigmachen der Veröffentlichung des Baums abzuschließen.

## Bestimmen des Veröffentlichungsstatus {#determining-publication-status}

Sie können den Veröffentlichungsstatus einer Seite bestimmen:

* In der [Ressourcenübersicht in der Sites-Konsole](/help/sites-cloud/authoring/basic-handling.md#viewing-and-selecting-resources)

  ![Veröffentlichungsstatus in der Kartenansicht](/help/sites-cloud/authoring/assets/publishing-status-console-card.png)

  Der Veröffentlichungsstatus wird in der Sites-Konsole in der Ansicht [Karte](/help/sites-cloud/authoring/basic-handling.md#card-view), [Spalte](/help/sites-cloud/authoring/basic-handling.md#column-view) und [Liste](/help/sites-cloud/authoring/basic-handling.md#list-view) angezeigt.

* in der [Zeitleisten](/help/sites-cloud/authoring/basic-handling.md#timeline)

  ![Veröffentlichungsstatus in der Zeitleisten-Ansicht](/help/sites-cloud/authoring/assets/publishing-status-timeline.png)

* im Menü [Seiteninformationen](/help/sites-cloud/authoring/page-editor/introduction.md#page-information) beim Bearbeiten einer Seite

  ![Veröffentlichungsstatus im Menü „Seiteninformationen“](/help/sites-cloud/authoring/assets/publishing-status-page-information.png)
