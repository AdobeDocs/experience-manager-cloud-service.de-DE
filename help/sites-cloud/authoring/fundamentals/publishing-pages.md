---
title: Veröffentlichen von Seiten
description: Veröffentlichen und Rückgängigmachen der Veröffentlichung von Seiten mit AEM
exl-id: 89f2363c-7922-4ca5-92cb-cbee6a393ee3
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '1717'
ht-degree: 100%

---

# Veröffentlichen von Seiten {#publishing-pages}

Nachdem Sie Ihren Inhalt in der Autorenumgebung erstellt und geprüft haben, [muss dieser auf der öffentlichen Website (der Veröffentlichungsumgebung) verfügbar gemacht werden](/help/sites-cloud/authoring/getting-started/concepts.md).

Dies wird als Veröffentlichung einer Seite bezeichnet. Wenn Sie eine Seite aus der Veröffentlichungsumgebung entfernen, wird dies als Rückgängigmachen der Veröffentlichung bezeichnet. Während der Veröffentlichung und des Rückgängigmachens der Veröffentlichung bleibt die Seite so lange in der Bearbeitungsumgebung verfügbar und kann geändert werden, bis Sie sie löschen.

Sie können eine Seite sofort oder zu einem vordefinierten künftigen Zeitpunkt (Datum/Uhrzeit) veröffentlichen bzw. ihre Veröffentlichung rückgängig machen.

## Terminologie {#terminology}

Bei der Arbeit mit Adobe Experience Manager (AEM) as a Cloud Service können Sie auf unterschiedliche Begriffe im Zusammenhang mit der Veröffentlichung stoßen.

* **Veröffentlichen/Veröffentlichung rückgängig machen**
   * Dies sind die Hauptbegriffe für die Aktionen, mit denen Sie Ihren Inhalt in Ihrer Publishing-Umgebung verfügbar machen (oder dies rückgängig machen).
   * Dies sind die in der AEM-Dokumentation verwendeten Begriffe.
* **Aktivieren/Deaktivieren**
   * Diese Begriffe sind Synonyme für das Veröffentlichen/Rückgängigmachen der Veröffentlichung.
   * Diese Begriffe wurden in früheren Versionen von AEM verwendet.
* **Replizieren/Replikation**
   * Dies sind die technischen Begriffe, die die Bewegung von Daten (z. B. Seiteninhalt, Dateien, Code, Benutzerkommentare) von einer Umgebung in eine andere beschreiben, wenn Sie eine Seite veröffentlichen.
   * Diese Begriffe werden hauptsächlich von Entwicklern verwendet.

## Veröffentlichen von Seiten {#publishing-pages-1}

Abhängig davon, wo Sie sich gerade befinden, können Sie Veröffentlichungen folgendermaßen vornehmen:

* [Im Seiteneditor](#publishing-from-the-editor)
* [In der Sites-Konsole](#publishing-from-the-console)

>[!NOTE]
>
>Wenn Sie nicht über die erforderlichen Berechtigungen für das Veröffentlichen einer bestimmten Seite verfügen:
>
>* Ein Workflow wird ausgelöst, der die entsprechende Person über Ihre Veröffentlichungsanfrage informiert.
>* Dieser Workflow wurde möglicherweise von Ihrem Entwickler-Team angepasst.
>* Sie werden in einer Mitteilung darüber informiert, dass der Workflow ausgelöst wurde.


<!--
>* This [workflow may have been customized](/help/sites-developing/workflows-models.md#main-pars-procedure-6fe6) by your development team.
>* A message will be displayed briefly to notify you that the workflow was triggered.
-->

>[!NOTE]
>
> Weitere Möglichkeiten finden Sie unter **Einschaltzeit** und **Ausschaltzeit** auf der [Registerkarte „Allgemein“ der Seiteneigenschaften](/help/sites-cloud/authoring/fundamentals/page-properties.md#basic).

### Veröffentlichungen im Editor {#publishing-from-the-editor}

Wenn Sie eine Seite bearbeiten, kann sie direkt im Editor veröffentlicht werden.

1. Wählen Sie das Symbol **Seiteninformationen** aus, um das Menü zu öffnen, und danach die Option **Seite veröffentlichen**.

   ![Veröffentlichen einer Seite über Seitenoptionen](/help/sites-cloud/authoring/assets/publishing-page-options.png)

1. Je nachdem, ob die Seite Verweise enthält, die veröffentlicht werden müssen, geschieht Folgendes:

   * Die Seite wird direkt veröffentlicht, wenn keine Verweise veröffentlicht werden müssen.
   * Wenn die Seite Verweise enthält, die veröffentlicht werden müssen, werden diese im **Veröffentlichungsassistenten** aufgeführt und Sie können eine der folgenden Aktionen ausführen:
      * Geben Sie an, welche Assets, Tags usw. Sie mit der Seite veröffentlichen möchten, und wählen Sie **Veröffentlichen** aus, um den Vorgang abzuschließen.
      * Mit **Abbrechen** können Sie den Vorgang abbrechen.

   ![Veröffentlichen von Verweisen mit der Seite](/help/sites-cloud/authoring/assets/publishing-references.png)

1. Mit **Veröffentlichen** wird die Seite in der Publishing-Umgebung repliziert. Im Seiteneditor wird ein Hinweis angezeigt, in dem die Veröffentlichung bestätigt wird.

   ![Statusinfo-Banner veröffentlichen](/help/sites-cloud/authoring/assets/publishing-info.png)

   Wird diese Seite in der Konsole dargestellt, ist der aktualisierte Veröffentlichungsstatus sichtbar.

   ![Status der Seitenveröffentlichung in der Spaltenansicht in der Site-Konsole](/help/sites-cloud/authoring/assets/publishing-status-console-column.png)

>[!NOTE]
>
>Im Editor kann nur eine teilweise Veröffentlichung vorgenommen werden, d. h. nur die ausgewählten und keine untergeordneten Seiten werden veröffentlicht.

### Veröffentlichungen über die Konsole {#publishing-from-the-console}

In der Sites-Konsole gibt es zwei Möglichkeiten zur Veröffentlichung:

* [Quick Publish ](#quick-publish)
* [Veröffentlichung verwalten ](#manage-publication)

#### Quick Publish  {#quick-publish}

**Quick Publish** wird für einfache Fälle verwendet. Die ausgewählten Seiten werden damit sofort ohne weitere Interaktion veröffentlicht. Aus diesem Grund werden auch alle nicht-veröffentlichten Verweise ebenfalls automatisch veröffentlicht.

So veröffentlichen Sie eine Seite mit der Funktion „Quick Publish“:

1. Wählen Sie die gewünschten Seiten in der Sites-Konsole aus und klicken Sie auf die Schaltfläche **Quick Publish**.

   ![Auswählen von Seiten zur Veröffentlichung](/help/sites-cloud/authoring/assets/publishing-select-pages.png)

1. Bestätigen Sie im Dialogfeld „Quick Publish“ die Veröffentlichung, indem Sie auf **Veröffentlichen** klicken, oder brechen Sie den Vorgang ab, indem Sie auf **Abbrechen** klicken. Beachten Sie, dass auch alle unveröffentlichten Verweise ebenfalls automatisch veröffentlicht werden.

   ![Quick Publish-Bestätigung](/help/sites-cloud/authoring/assets/publishing-quick-publish.png)

1. Bei der Veröffentlichung der Seite erscheint eine Warnmeldung, in der die Veröffentlichung bestätigt wird.

>[!NOTE]
>
>Die Option „Quick Publish“ ermöglicht nur die teilweise Veröffentlichung, d. h. nur die ausgewählten und keine untergeordneten Seiten werden veröffentlicht.

#### Veröffentlichung verwalten   {#manage-publication}

**Veröffentlichung verwalten** bietet mehr Optionen als „Quick Publish“. Mit dieser Funktion können Sie auch untergeordnete Seiten einschließen, Verweise anpassen, alle nötigen Workflows starten und bei Bedarf zu einem späteren Zeitpunkt veröffentlichen.

So veröffentlichen Sie eine Seite bzw. machen ihre Veröffentlichung rückgängig mit „Veröffentlichung verwalten“:

1. Wählen Sie in der Sites-Konsole die entsprechenden Seiten aus und klicken Sie auf die Schaltfläche **Veröffentlichung verwalten**.

   ![Auswählen von Seiten zur Veröffentlichung](/help/sites-cloud/authoring/assets/publishing-select-pages.png)

1. Der Assistent **Veröffentlichung verwalten** wird geöffnet. Im ersten Schritt **Optionen** haben Sie folgende Möglichkeiten:

   * Veröffentlichen Sie die ausgewählte Seite oder machen Sie die Veröffentlichung rückgängig.
   * Führen Sie diese Aktion sofort oder zu einem späteren Zeitpunkt aus.

   Bei der späteren Veröffentlichung wird ein Workflow gestartet, mit dem die ausgewählten Seiten zur angegebenen Zeit veröffentlicht werden. Entsprechend wird durch die Auswahl des Rückgängigmachens der Veröffentlichung zu einem späteren Zeitpunkt der entsprechende Workflow für die ausgewählten Seiten zum angegebenen Zeitpunkt gestartet.

   Wenn Sie eine Veröffentlichung/rückgängig gemachte Veröffentlichung später abbrechen möchten, gehen Sie zur Konsole „Workflow“, um den entsprechenden Workflow zu beenden. <!--If you want to cancel a publish/unpublish later, go to the [Workflow Console](/help/sites-administering/workflows.md) to terminate the corresponding workflow.-->

   ![Veröffentlichungsoptionen verwalten](/help/sites-cloud/authoring/assets/publishing-manage-publication-options.png)

   Klicken Sie auf **Weiter**, um fortzufahren.

1. Im nächsten Schritt des Assistenten „Veröffentlichung verwalten“ können Sie den **Umfang** der Veröffentlichung/der rückgängig gemachten Veröffentlichung definieren, wie z. B. das Einschließen von untergeordneten Seiten und/oder von Verweisen.

   ![Umfang der Veröffentlichung verwalten](/help/sites-cloud/authoring/assets/publishing-manage-publication-scope.png)

   Mit der Schaltfläche **Inhalt hinzufügen** können Sie zusätzliche Seiten zur Liste der zu veröffentlichenden Seiten hinzufügen, falls Sie dies noch nicht vor dem Starten des Assistenten „Veröffentlichung verwalten“ getan haben.

   Durch Klicken auf die Schaltfläche „Inhalt hinzufügen“ wird der [Pfad-Browser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#path-browser) gestartet, mit dem Inhalte ausgewählt werden können.

   Wählen Sie die gewünschten Seiten aus und klicken Sie dann auf **Auswählen**, um den Inhalt dem Assistenten hinzuzufügen, oder auf **Abbrechen**, um die Auswahl abzubrechen und zum Assistenten zurückzukehren.

   Im Assistenten können Sie dann ein Element in der Liste auswählen, um es weiter zu konfigurieren:

   * Untergeordnete Elemente einschließen
   * Das Element aus der Auswahl entfernen
   * Seine veröffentlichten Verweise verwalten

   ![Verwalten von Veröffentlichungen mit Seitenauswahl](/help/sites-cloud/authoring/assets/publishing-manage-publication-select.png)

   Durch Klicken auf **Untergeordnete Elemente einbeziehen** wird ein Dialogfeld geöffnet, in dem Sie folgende Möglichkeiten haben:

   * Nur unmittelbar untergeordnete Elemente einbeziehen.
   * Nur geänderte Seiten einbeziehen.
   * Nur bereits veröffentlichte Seiten einbeziehen.

   Klicken Sie auf **Hinzufügen**, um die untergeordneten Seiten zur Liste der Seiten hinzuzufügen, die je nach Auswahloptionen veröffentlicht werden sollen oder deren Veröffentlichung rückgängig gemacht werden soll. Klicken Sie auf **Abbrechen**, um die Auswahl abzubrechen und zum Assistenten zurückzukehren.

   ![Verwalten von Veröffentlichungen einschließlich untergeordneter Elemente](/help/sites-cloud/authoring/assets/publishing-include-children.png)

   Dort sehen Sie die hinzugefügten Seiten entsprechend Ihrer Auswahl im Dialogfeld „Untergeordnete Elemente einbeziehen“.

   Zur Ansicht und zum Ändern der Verweise, die für eine Seite veröffentlicht werden sollen bzw. deren Veröffentlichung rückgängig gemacht werden soll, wählen Sie sie aus und klicken Sie anschließend auf die Schaltfläche **Veröffentlichte Verweise**.

   ![Veröffentlichungsoptionen verwalten](/help/sites-cloud/authoring/assets/publishing-manage-publication-references.png)

   Das Dialogfeld **Veröffentlichte Verweise** zeigt die Verweise für den ausgewählten Inhalt an. Standardmäßig sind alle ausgewählt und werden veröffentlicht bzw. die Veröffentlichung wird rückgängig gemacht. Sie können sie aber auch deaktivieren, um die Auswahl aufzuheben, sodass sie nicht in die Aktion einbezogen werden.

   Klicken Sie auf **Fertig**, um Ihre Änderungen zu speichern, oder auf **Abbrechen**, um die Auswahl abzubrechen und zum Assistenten zurückzukehren.

   Im Assistenten wird die Spalte **Verweise** aktualisiert und zeigt Ihre Auswahl von Verweisen an, die veröffentlicht werden sollen bzw. deren Veröffentlichung rückgängig gemacht werden soll.

   ![Verwalten von Veröffentlichungen mit Seitenauswahl](/help/sites-cloud/authoring/assets/publishing-manage-publication-select.png)

1. Klicken Sie auf **Veröffentlichen**, um den Vorgang abzuschließen.

   In der Sites-Konsole wird die Veröffentlichung durch eine Benachrichtigung bestätigt.

1. Wenn die veröffentlichten Seiten mit Workflows verknüpft sind, werden diese im abschließenden **Workflow**-Schritt des Veröffentlichungsassistenten gezeigt.

   >[!NOTE]
   >
   >Der gezeigte **Workflow**-Schritt hängt von den Rechten des jeweiligen Benutzers ab. Weitere Informationen finden Sie im vorherigen Hinweis auf dieser Seite bezüglich Berechtigungen für die Veröffentlichung sowie unter „Verwaltung der Zugriffsrechte auf Workflows“ und unter [Anwenden von Workflows auf Seiten](/help/sites-cloud/authoring/workflows/applying.md).
   <!--
   >The **Workflows** step will be shown based on what rights your user may or may not have. See the previous note on this page regarding publishing privileges as well as [Managing Access to Workflows](/help/sites-administering/workflows-managing.md) and [Applying Workflows to Pages](/help/sites-cloud/authoring/workflows/applying.md) for details.
   -->

   Die Ressourcen werden gemäß den ausgelösten Workflows gruppiert, wobei Sie für jede Ressource folgende Möglichkeiten haben:

   * Definieren des Workflow-Titels
   * Beibehalten des Workflow-Pakets, vorausgesetzt der Workflow unterstützt mehrere Ressourcen.

   <!--Keep the workflow package, provided that the workflow has [multi-resource support](/help/sites-developing/workflows-models.md#configuring-a-workflow-for-multi-resource-support).
    -->

   * Definieren des Titels des Workflow-Pakets, sofern die Option zum Beibehalten des Workflow-Pakets ausgewählt wurde

   Klicken Sie auf **Veröffentlichen** oder **Später veröffentlichen**, um die Veröffentlichung abzuschließen.

## Veröffentlichen von Seiten rückgängig machen {#unpublishing-pages}

Wenn Sie die Veröffentlichung einer Seite rückgängig machen, wird sie aus der Veröffentlichungsumgebung gelöscht, sodass sie nicht mehr für Ihre Leser verfügbar ist.

[Ähnlich wie beim Veröffentlichen](#publishing-pages) können Sie auch die Veröffentlichung einer oder mehrerer Seiten rückgängig machen:

* [Im Seiteneditor](#unpublishing-from-the-editor)
* [In der Sites-Konsole](#unpublishing-from-the-console)

### Rückgängigmachen der Veröffentlichung im Editor   {#unpublishing-from-the-editor}

Wenn Sie die Veröffentlichung einer von Ihnen bearbeiteten Seite rückgängig machen möchten, wählen Sie analog zur [Veröffentlichung einer Seite](#publishing-from-the-editor) im Menü **Seiteninformationen** die Option **Veröffentlichung der Seite rückgängig machen** aus.

### Rückgängigmachen der Veröffentlichung in der Konsole   {#unpublishing-from-the-console}

Ebenso wie Sie [die Option „Veröffentlichung verwalten“ zur Veröffentlichung verwenden](#manage-publication), können Sie damit auch eine Veröffentlichung rückgängig machen.

1. Wählen Sie in der Sites-Konsole die entsprechenden Seiten aus und klicken Sie auf die Schaltfläche **Veröffentlichung verwalten**.
1. Der Assistent **Veröffentlichung verwalten** wird geöffnet. Wählen Sie im ersten Schritt **Optionen** die Option **Veröffentlichung rückgängig machen** anstelle der Standardoption **Veröffentlichen** aus.

   ![Veröffentlichung wird rückgängig gemacht](/help/sites-cloud/authoring/assets/publishing-unpublish.png)

   Die Auswahl von „Später veröffentlichen“ startet einen Workflow zur Veröffentlichung der Seite zum angegebenen Zeitpunkt. Entsprechend startet die Auswahl von „Später deaktivieren“ einen Workflow zum Rückgängigmachen der Veröffentlichung der ausgewählten Seiten zum angegebenen Zeitpunkt.

   Wenn Sie eine Veröffentlichung/rückgängig gemachte Veröffentlichung später abbrechen möchten, gehen Sie zur Konsole „Workflow“, um den entsprechenden Workflow zu beenden. <!--If you want to cancel a publish/unpublish later, go to the [Workflow Console](/help/sites-administering/workflows.md) to terminate the corresponding workflow.-->

1. Um das Rückgängigmachen der Veröffentlichung abzuschließen, fahren Sie mit dem Assistenten ähnlich wie beim [Veröffentlichen der Seite](#manage-publication) fort.

## Veröffentlichen und Rückgängigmachen der Veröffentlichung eines Baums {#publishing-and-unpublishing-a-tree}

Wenn Sie allerdings eine große Zahl von Inhaltsseiten erstellt bzw. aktualisiert haben, die sich alle unter derselben Stammseite befinden, kann es praktischer sein, mit einer einzigen Aktion den gesamten Baum zu veröffentlichen.

Dazu können Sie in der Sites-Konsole die Option [Veröffentlichung verwalten](#manage-publication) verwenden.

1. Wählen Sie in der Sites-Konsole die Stammseite des Baums aus, den Sie veröffentlichen möchten bzw. dessen Veröffentlichung Sie rückgängig machen möchten, und danach **Veröffentlichung verwalten**.
1. Der Assistent **Veröffentlichung verwalten** wird geöffnet. Wählen Sie „Veröffentlichen“ oder „Veröffentlichung rückgängig machen“ sowie den Zeitpunkt aus und danach **Weiter**, um fortzufahren.
1. Wählen Sie im Schritt **Bereich** die Stammseite aus und danach **Untergeordnete Elemente einbeziehen**.

   ![Verwalten von Veröffentlichungen mit Seitenauswahl](/help/sites-cloud/authoring/assets/publishing-manage-publication-select.png)

1. Deaktivieren Sie im Dialogfeld **Untergeordnete Elemente einbeziehen** die folgenden Optionen:

   * Nur unmittelbar untergeordnete Elemente einbeziehen
   * Nur bereits veröffentlichte Seiten einschließen

   Diese Optionen sind standardmäßig ausgewählt. Sie müssen also darauf achten, diese Auswahl aufzuheben. Klicken Sie auf **Hinzufügen**, um den Inhalt beim Veröffentlichen bzw. beim Rückgängigmachen der Veröffentlichung hinzuzufügen.

   ![Untergeordnete Elemente beim Rückgängigmachen der Veröffentlichung einbeziehen](/help/sites-cloud/authoring/assets/publishing-tree-children.png)

1. Im Assistenten **Veröffentlichung verwalten** wird der Inhalt des Baums zur Überprüfung aufgelistet. Sie können die Auswahl weiter anpassen, indem Sie zusätzliche Seiten hinzuzufügen oder ausgewählte Seiten entfernen.

   ![Veröffentlichungsoptionen verwalten](/help/sites-cloud/authoring/assets/publishing-tree-select.png)

   Sie können die zu veröffentlichenden Verweise auch in der Option **Veröffentlichte Verweise** überprüfen.

1. [Fahren Sie mit dem Assistenten „Veröffentlichung verwalten“ wie üblich fort](#manage-publication), um die Veröffentlichung oder das Rückgängigmachen der Veröffentlichung des Baums abzuschließen.

## Bestimmen des Veröffentlichungsstatus {#determining-publication-status}

Sie können den Veröffentlichungsstatus einer Seite bestimmen:

* In der [Ressourcenübersicht in der Sites-Konsole](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources)

   ![Veröffentlichungsstatus in der Kartenansicht](/help/sites-cloud/authoring/assets/publishing-status-console-card.png)

   Der Veröffentlichungsstatus wird in der Sites-Konsole in der Ansicht [Karte](/help/sites-cloud/authoring/getting-started/basic-handling.md#card-view), [Spalte](/help/sites-cloud/authoring/getting-started/basic-handling.md#column-view) und [Liste](/help/sites-cloud/authoring/getting-started/basic-handling.md#list-view) angezeigt.

* in der [Zeitleistensegment](/help/sites-cloud/authoring/getting-started/basic-handling.md#timeline)

   ![Veröffentlichungsstatus in der Zeitleistensegment-Ansicht](/help/sites-cloud/authoring/assets/publishing-status-timeline.png)

* im Menü [Seiteninformationen](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-information) beim Bearbeiten einer Seite

   ![Veröffentlichungsstatus im Menü „Seiteninformationen“](/help/sites-cloud/authoring/assets/publishing-status-page-information.png)
