---
title: Veröffentlichen von Seiten
description: Veröffentlichen und Rückgängigmachen der Veröffentlichung von Seiten mit AEM
translation-type: tm+mt
source-git-commit: f04dd39a5a22f44f976f2e473689780099f10f9a

---


# Veröffentlichen von Seiten {#publishing-pages}

Nachdem Sie Ihren Inhalt in der Autorenumgebung erstellt und geprüft haben, [muss dieser auf der öffentlichen Website (der Veröffentlichungsumgebung) verfügbar gemacht werden](/help/sites-cloud/authoring/getting-started/concepts.md).

Dies wird als Veröffentlichung einer Seite bezeichnet. Wenn Sie eine Seite aus der Veröffentlichungsumgebung entfernen, wird dies als Rückgängigmachen der Veröffentlichung bezeichnet. Während der Veröffentlichung und des Rückgängigmachens der Veröffentlichung bleibt die Seite so lange in der Bearbeitungsumgebung verfügbar und kann geändert werden, bis Sie sie löschen.

Sie können eine Seite sofort oder zu einem vordefinierten Datum/einer vordefinierten Uhrzeit veröffentlichen oder die Veröffentlichung rückgängig machen.

## Terminologie {#terminology}

Während der Arbeit mit AEM stehen Ihnen möglicherweise unterschiedliche Begriffe im Zusammenhang mit der Veröffentlichung zur Verfügung.

* **Veröffentlichen/Veröffentlichung rückgängig machen**
   * Dies sind die Hauptbegriffe für die Aktionen, mit denen Sie Ihre Inhalte auf Ihrer Umgebung veröffentlichen können (oder nicht).
   * Dies sind die in der AEM-Dokumentation verwendeten Begriffe.
* **Aktivieren/Deaktivieren**
   * Diese Begriffe sind gleichbedeutend mit Veröffentlichung/Rückgängigmachen der Veröffentlichung.
   * Diese Begriffe wurden in früheren Versionen von AEM verwendet.
* **Wiederholen/Replikation**
   * Dies sind die technischen Begriffe, die die Datenbewegung (z. B. Seiteninhalt, Dateiinhalt, Code, Benutzerkommentare) von einer Umgebung zur anderen beschreiben, wenn Sie eine Seite veröffentlichen.
   * Diese Begriffe werden hauptsächlich von Entwicklern verwendet.

## Veröffentlichen von Seiten {#publishing-pages-1}

Abhängig davon, wo Sie sich gerade befinden, können Sie Veröffentlichungen folgendermaßen vornehmen:

* [Im Seiten-Editor](#publishing-from-the-editor)
* [In der Sites-Konsole](#publishing-from-the-console)

>[!NOTE]
>
>Wenn Sie nicht über die erforderlichen Berechtigungen für das Veröffentlichen einer bestimmten Seite verfügen:
>
>* Ein Workflow wird ausgelöst, der die entsprechende Person über Ihre Veröffentlichungsanfrage informiert.
>* Dieser Workflow wurde möglicherweise von Ihrem Entwicklerteam angepasst.
>* Sie werden in einer Mitteilung darüber informiert, dass der Workflow ausgelöst wurde.


<!--
>* This [workflow may have been customized](/help/sites-developing/workflows-models.md#main-pars-procedure-6fe6) by your development team.
>* A message will be displayed briefly to notify you that the workflow was triggered.
-->

### Veröffentlichungen im Editor {#publishing-from-the-editor}

Wenn Sie eine Seite bearbeiten, kann sie direkt im Editor veröffentlicht werden.

1. Select the **Page Information** icon to open the menu and then the **Publish Page** option.

   ![Veröffentlichen einer Seite über Seitenoptionen](/help/sites-cloud/authoring/assets/publishing-page-options.png)

1. Je nachdem, ob die Seite Verweise enthält, die veröffentlicht werden müssen, geschieht Folgendes:

   * Die Seite wird direkt veröffentlicht, wenn keine Verweise veröffentlicht werden müssen.
   * Wenn die Seite Verweise enthält, die veröffentlicht werden müssen, werden diese im **Veröffentlichungsassistenten** aufgeführt und Sie können eine der folgenden Aktionen ausführen:
      * Specify which of the assets/tags/etc. you want to publish together with the page, then use **Publish** to complete the process.
      * Mit **Abbrechen** können Sie den Vorgang abbrechen.
   ![Veröffentlichen von Verweisen mit der Seite](/help/sites-cloud/authoring/assets/publishing-references.png)

1. Selecting **Publish** will replicate the page to the publish environment. Im Seiteneditor wird ein Hinweis angezeigt, in dem die Veröffentlichung bestätigt wird.

   ![Statusinfo-Banner veröffentlichen](/help/sites-cloud/authoring/assets/publishing-info.png)

   Wird diese Seite in der Konsole dargestellt, ist der aktualisierte Veröffentlichungsstatus sichtbar.

   ![Seitenveröffentlichungsstatus in der Ansicht der Spalten in der Sites-Konsole](/help/sites-cloud/authoring/assets/publishing-status-console-column.png)

>[!NOTE]
>
>Beim Veröffentlichen im Editor handelt es sich um eine oberflächliche Veröffentlichung, d. h. nur die ausgewählte Seite/die ausgewählten Seiten werden veröffentlicht und untergeordnete Seiten werden/sind nicht veröffentlicht.

### Veröffentlichungen über die Konsole {#publishing-from-the-console}

In der Sites-Konsole gibt es zwei Möglichkeiten zur Veröffentlichung:

* [Schnell veröffentlichen](#quick-publish)
* [Veröffentlichung verwalten](#manage-publication)

#### Schnell veröffentlichen {#quick-publish}

**Die Schnellveröffentlichung** ist in einfachen Fällen erforderlich und veröffentlicht die ausgewählten Seiten sofort ohne weitere Interaktionen. Aus diesem Grund werden auch alle nicht-veröffentlichten Verweise ebenfalls automatisch veröffentlicht.

So veröffentlichen Sie eine Seite mit der Funktion „Schnell veröffentlichen“:

1. Select the page or pages in the sites console and click on the **Quick Publish** button.

   ![Auswählen von Seiten zur Veröffentlichung](/help/sites-cloud/authoring/assets/publishing-select-pages.png)

1. In the Quick Publish dialog, confirm the publication by clicking on **Publish** or cancel by clicking on **Cancel**. Beachten Sie, dass auch alle unveröffentlichten Verweise ebenfalls automatisch veröffentlicht werden.

   ![Schnellveröffentlichungsbestätigung](/help/sites-cloud/authoring/assets/publishing-quick-publish.png)

1. Bei der Veröffentlichung der Seite erscheint eine Warnmeldung, in der die Veröffentlichung bestätigt wird.

>[!NOTE]
>
>Die Option „Schnell veröffentlichen“ ermöglicht nur die teilweise Veröffentlichung, d. h. nur die ausgewählten und keine untergeordneten Seiten werden veröffentlicht.

#### Veröffentlichung verwalten {#manage-publication}

**Angebote für Veröffentlichungen** können mit mehr Optionen als mit der Funktion &quot;Schnelle Veröffentlichung&quot;verwaltet werden. Dadurch können untergeordnete Seiten einbezogen, die Verweise angepasst und relevante Workflows gestartet werden. Außerdem können Sie die Veröffentlichung zu einem späteren Zeitpunkt vornehmen.

So veröffentlichen Sie eine Seite bzw. machen ihre Veröffentlichung rückgängig mit „Veröffentlichung verwalten“:

1. Select the page or pages in the sites console and click on the **Manage Publication** button.

   ![Auswählen von Seiten zur Veröffentlichung](/help/sites-cloud/authoring/assets/publishing-select-pages.png)

1. Der Assistent zum **Verwalten von Veröffentlichungen** wird gestartet. The first step, **Options**, allows you to:

   * Veröffentlichen Sie die ausgewählte Seite oder machen Sie die Veröffentlichung rückgängig.
   * Führen Sie diese Aktion sofort oder zu einem späteren Zeitpunkt aus.
   Bei der späteren Veröffentlichung wird ein Workflow gestartet, mit dem die ausgewählten Seiten zur angegebenen Zeit veröffentlicht werden. Entsprechend wird durch die Auswahl des Rückgängigmachens der Veröffentlichung zu einem späteren Zeitpunkt der entsprechende Workflow für die ausgewählten Seiten zum angegebenen Zeitpunkt gestartet.

   Wenn Sie eine Veröffentlichung/rückgängig gemachte Veröffentlichung später abbrechen möchten, gehen Sie zur Konsole Workflow, um den entsprechenden Workflow zu beenden. <!--If you want to cancel a publish/unpublish later, go to the [Workflow Console](/help/sites-administering/workflows.md) to terminate the corresponding workflow.-->

   ![Veröffentlichungsoptionen verwalten](/help/sites-cloud/authoring/assets/publishing-manage-publication-options.png)

   Klicken Sie auf **Weiter**, um fortzufahren.

1. In the next step of the Manage Publication wizard, **Scope**, you can define the scope of the publication/un-publication such as including to include child pages and/or including references.

   ![Veröffentlichungsbereich verwalten](/help/sites-cloud/authoring/assets/publishing-manage-publication-scope.png)

   Mit der Schaltfläche **Inhalt hinzufügen** können Sie der Liste der zu veröffentlichenden Seiten weitere Seiten hinzufügen, falls Sie die Auswahl vernachlässigt haben, bevor Sie den Assistenten „Veröffentlichung verwalten“ starten.

   Durch Klicken auf die Schaltfläche „Inhalt hinzufügen“ wird der [Pfadbrowser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#path-browser) gestartet, mit dem Inhalte ausgewählt werden können.

   Select the required pages and then click **Select** to add the content to the wizard or **Cancel **to cancel the selection and return to the wizard.

   Im Assistenten können Sie dann ein Element in der Liste auswählen, um es weiter zu konfigurieren:

   * Untergeordnete Elemente einschließen
   * Das Element aus der Auswahl entfernen
   * Seine veröffentlichten Verweise verwalten
   ![Verwalten von Seiten zur Auswahl von Veröffentlichungen](/help/sites-cloud/authoring/assets/publishing-manage-publication-select.png)

   Clicking **Include Children** opens a dialogue allowing you to:

   * Nur unmittelbar untergeordnete Elemente einbeziehen.
   * Nur geänderte Seiten einbeziehen.
   * Nur bereits veröffentlichte Seiten einbeziehen.
   Click **Add** to add the children pages to the list of pages to be published or unpublished based on the selection options. Click **Cancel** to cancel the selection and return to the wizard.

   ![Veröffentlichung einschließlich untergeordneter Elemente verwalten](/help/sites-cloud/authoring/assets/publishing-include-children.png)

   Dort sehen Sie die hinzugefügten Seiten entsprechend Ihrer Auswahl im Dialogfeld „Untergeordnete Elemente einbeziehen“.

   You can view and modify the references to be published or unpublished for a page by selecting it and then clicking the **Published References** button.

   ![Veröffentlichungsoptionen verwalten](/help/sites-cloud/authoring/assets/publishing-manage-publication-references.png)

   The **Published References** dialog displays the references for the selected content. Standardmäßig sind sie alle ausgewählt und werden veröffentlicht/Veröffentlichung rückgängig gemacht. Sie können die Auswahl jedoch aufheben, damit sie nicht in der Aktion enthalten sind.

   Click **Done** to save your changes or **Cancel** to cancel the selection and return to the wizard.

   Im Assistenten wird die Spalte **Verweise** aktualisiert und zeigt Ihre Auswahl von Verweisen an, die veröffentlicht werden sollen bzw. deren Veröffentlichung rückgängig gemacht werden soll.

   ![Verwalten von Seiten zur Auswahl von Veröffentlichungen](/help/sites-cloud/authoring/assets/publishing-manage-publication-select.png)

1. Click **Publish** to complete.

   In der Sites-Konsole wird die Veröffentlichung durch eine Benachrichtigung bestätigt.

1. If the published pages are associated with workflows, they may be shown in a final **Workflows** step of the publication wizard.

   >[!NOTE]
   >
   >The **Workflows** step will be shown based on what rights your user may or may not have. See the previous note on this page regarding publishing privileges as well as Managing Access to Workflows and [Applying Workflows to Pages](/help/sites-cloud/authoring/workflows/applying.md) for details.
   <!--
   >The **Workflows** step will be shown based on what rights your user may or may not have. See the previous note on this page regarding publishing privileges as well as [Managing Access to Workflows](/help/sites-administering/workflows-managing.md) and [Applying Workflows to Pages](/help/sites-cloud/authoring/workflows/applying.md) for details.
   -->

   Die Ressourcen werden gemäß den ausgelösten Workflows gruppiert, wobei Sie für jede Ressource folgende Möglichkeiten haben:

   * Definieren des Workflow-Titels
   * Behalten Sie das Workflow-Paket bei, sofern der Workflow Unterstützung für mehrere Ressourcen bietet.
   <!--Keep the workflow package, provided that the workflow has [multi-resource support](/help/sites-developing/workflows-models.md#configuring-a-workflow-for-multi-resource-support).
    -->

   * Definieren des Titels des Workflow-Pakets, sofern die Option zum Beibehalten des Workflow-Pakets ausgewählt wurde
   Klicken Sie auf **Veröffentlichen** oder **Später veröffentlichen**, um die Veröffentlichung abzuschließen.

## Veröffentlichen von Seiten rückgängig machen {#unpublishing-pages}

Wenn Sie die Veröffentlichung einer Seite rückgängig machen, wird sie aus der Veröffentlichungsumgebung gelöscht, sodass sie nicht mehr für Ihre Leser verfügbar ist.

In a [manner similar to publishing](#publishing-pages), one or more pages can be unpublished:

* [Im Seiten-Editor](#unpublishing-from-the-editor)
* [In der Sites-Konsole](#unpublishing-from-the-console)

### Rückgängigmachen der Veröffentlichung im Editor {#unpublishing-from-the-editor}

Wenn Sie die Veröffentlichung einer von Ihnen bearbeiteten Seite rückgängig machen möchten, wählen Sie analog zur [Veröffentlichung einer Seite](#publishing-from-the-editor) im Menü **Seiteninformationen** die Option **Veröffentlichung der Seite rückgängig machen** aus.

### Rückgängigmachen der Veröffentlichung in der Konsole {#unpublishing-from-the-console}

Ebenso wie Sie [die Option „Veröffentlichung verwalten“ zur Veröffentlichung verwenden](#manage-publication), können Sie damit auch eine Veröffentlichung rückgängig machen.

1. Select the page or pages in the sites console and click on the **Manage Publication** button.
1. Der Assistent zum **Verwalten von Veröffentlichungen** wird gestartet. Wählen Sie im ersten Schritt **Optionen** die Option **Veröffentlichung rückgängig machen** anstelle der Standardoption **Veröffentlichen** aus.

   ![Veröffentlichung wird rückgängig gemacht](/help/sites-cloud/authoring/assets/publishing-unpublish.png)

   Die Auswahl von „Später veröffentlichen“ startet einen Workflow zur Veröffentlichung der Seite zum angegebenen Zeitpunkt. Entsprechend startet die Auswahl von „Später deaktivieren“ einen Workflow zum Rückgängigmachen der Veröffentlichung der ausgewählten Seiten zum angegebenen Zeitpunkt.

   Wenn Sie eine Veröffentlichung/rückgängig gemachte Veröffentlichung später abbrechen möchten, gehen Sie zur Konsole Workflow, um den entsprechenden Workflow zu beenden. <!--If you want to cancel a publish/unpublish later, go to the [Workflow Console](/help/sites-administering/workflows.md) to terminate the corresponding workflow.-->

1. To complete the un-publication, continue through the wizard as you would to [publish the page](#manage-publication).

## Veröffentlichen und Rückgängigmachen der Veröffentlichung eines Baums {#publishing-and-unpublishing-a-tree}

Wenn Sie allerdings eine große Zahl von Inhaltsseiten erstellt bzw. aktualisiert haben, die sich alle unter derselben Stammseite befinden, kann es praktischer sein, mit einer einzigen Aktion den gesamten Baum zu veröffentlichen.

Dazu können Sie in der Sites-Konsole die Option [Veröffentlichung verwalten](#manage-publication) verwenden.

1. Wählen Sie in der Sites-Konsole die Stammseite des Baums aus, den Sie veröffentlichen möchten bzw. dessen Veröffentlichung Sie rückgängig machen möchten, und danach **Veröffentlichung verwalten**.
1. Der Assistent zum **Verwalten von Veröffentlichungen** wird gestartet. Wählen Sie „Veröffentlichen“ oder „Veröffentlichung rückgängig machen“ sowie den Zeitpunkt aus und danach **Weiter**, um fortzufahren.
1. Wählen Sie im Schritt **Bereich** die Stammseite aus und danach **Untergeordnete Elemente einbeziehen**.

   ![Verwalten von Seiten zur Auswahl von Veröffentlichungen](/help/sites-cloud/authoring/assets/publishing-manage-publication-select.png)

1. In the **Include Children** dialogue, un-check the options:

   * Nur unmittelbar untergeordnete Elemente einbeziehen
   * Nur bereits veröffentlichte Seiten einschließen
   Diese Optionen sind standardmäßig ausgewählt. Sie müssen also darauf achten, diese Auswahl aufzuheben. Click **Add** to confirm and add the content to the publication/un-publication.

   ![Untergeordnete Elemente beim Rückgängigmachen der Veröffentlichung einschließen](/help/sites-cloud/authoring/assets/publishing-tree-children.png)

1. Im Assistenten **Veröffentlichung verwalten** wird der Inhalt des Baums zur Überprüfung aufgelistet. Sie können die Auswahl weiter anpassen, indem Sie zusätzliche Seiten hinzuzufügen oder ausgewählte Seiten entfernen.

   ![Veröffentlichungsoptionen verwalten](/help/sites-cloud/authoring/assets/publishing-tree-select.png)

   Remember that you can also review the references to be published via the **Published References** option.

1. [Fahren Sie mit dem Assistenten zum Verwalten von Veröffentlichungen wie gewohnt](#manage-publication) fort, um die Veröffentlichung der Struktur abzuschließen oder die Veröffentlichung rückgängig zu machen.

## Bestimmen des Veröffentlichungsstatus {#determining-publication-status}

Sie können den Veröffentlichungsstatus einer Seite festlegen:

* In der [Ressourcenübersicht in der Sites-Konsole](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources) 

   ![Veröffentlichungsstatus in der Ansicht der Karte](/help/sites-cloud/authoring/assets/publishing-status-console-card.png)

   Der Veröffentlichungsstatus wird in den Ansichten [Karten](/help/sites-cloud/authoring/getting-started/basic-handling.md#card-view), [Spalten](/help/sites-cloud/authoring/getting-started/basic-handling.md#column-view) und [Listen](/help/sites-cloud/authoring/getting-started/basic-handling.md#list-view) in der Sites Console angezeigt.

* In the [timeline](/help/sites-cloud/authoring/getting-started/basic-handling.md#timeline)

   ![Veröffentlichungsstatus in der Ansicht der Zeitschiene](/help/sites-cloud/authoring/assets/publishing-status-timeline.png)

* In the [Page Information menu](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-information) when editing a page

   ![Veröffentlichungsstatus im Menü &quot;Seiteninformationen&quot;](/help/sites-cloud/authoring/assets/publishing-status-page-information.png)
