---
title: Veröffentlichen von Seiten
description: Veröffentlichen und Rückgängigmachen der Veröffentlichung von Seiten mit AEM
exl-id: 89f2363c-7922-4ca5-92cb-cbee6a393ee3
source-git-commit: 66bc262b35f69b7877e4a01df9ab26395afd604d
workflow-type: tm+mt
source-wordcount: '1791'
ht-degree: 98%

---

# Veröffentlichen von Seiten {#publishing-pages}

Nachdem Sie Ihren Inhalt in der Autorenumgebung erstellt und geprüft haben, [muss dieser auf der öffentlichen Website (der Veröffentlichungsumgebung) verfügbar gemacht werden](/help/sites-cloud/authoring/getting-started/concepts.md).

Dies wird als Veröffentlichung einer Seite bezeichnet. Wenn Sie eine Seite aus der Veröffentlichungsumgebung entfernen, wird dies als Rückgängigmachen der Veröffentlichung bezeichnet. Während der Veröffentlichung und des Rückgängigmachens der Veröffentlichung bleibt die Seite so lange in der Bearbeitungsumgebung verfügbar und kann geändert werden, bis Sie sie löschen.

Sie können eine Seite sofort oder zu einem vordefinierten künftigen Zeitpunkt (Datum/Uhrzeit) veröffentlichen bzw. ihre Veröffentlichung rückgängig machen.

>[!NOTE]
>
>Das Veröffentlichen eines Experience Fragments folgt im Wesentlichen dem gleichen Verfahren wie das Veröffentlichen einer Seite, allerdings in der Konsole oder im Editor für Experience Fragments.

## Terminologie {#terminology}

Bei der Arbeit mit Adobe Experience Manager (AEM) as a Cloud Service können Sie auf unterschiedliche Begriffe im Zusammenhang mit der Veröffentlichung stoßen.

* **Veröffentlichen/Veröffentlichung rückgängig machen**
   * Dies sind die Hauptbegriffe für die Aktionen, mit denen Sie Ihren Inhalt in Ihrer Veröffentlichungsumgebung verfügbar machen (oder dies rückgängig machen).
   * Dies sind die in der AEM-Dokumentation verwendeten Begriffe.
* **Aktivieren/Deaktivieren**
   * Diese Begriffe sind Synonyme für das Veröffentlichen/Rückgängigmachen der Veröffentlichung.
   * Diese Begriffe wurden in früheren Versionen von AEM verwendet.
* **Replizieren/Replikation**
   * Dies sind die technischen Begriffe, die die Bewegung von Daten (z. B. Seiteninhalt, Dateien, Code, Benutzerkommentare) von einer Umgebung in eine andere beschreiben, wenn Sie eine Seite veröffentlichen.
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
>* Dieser Workflow wurde möglicherweise von Ihrem Entwickler-Team angepasst.
>* Sie werden in einer Mitteilung darüber informiert, dass der Workflow ausgelöst wurde.


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

1. Mit **Veröffentlichen** wird die Seite in der Veröffentlichungsumgebung repliziert. Im Seiteneditor wird ein Hinweis angezeigt, in dem die Veröffentlichung bestätigt wird.

   ![Statusinfo-Banner veröffentlichen](/help/sites-cloud/authoring/assets/publishing-info.png)

   Wird diese Seite in der Konsole dargestellt, ist der aktualisierte Veröffentlichungsstatus sichtbar.

   ![Status der Seitenveröffentlichung in der Spaltenansicht in der Site-Konsole](/help/sites-cloud/authoring/assets/publishing-status-console-column.png)

>[!NOTE]
>
>Im Editor kann nur eine teilweise Veröffentlichung vorgenommen werden, d. h. nur die ausgewählten und keine untergeordneten Seiten werden veröffentlicht.

>[!NOTE]
>
>Seiten, auf die im Editor über [Aliasnamen](/help/sites-cloud/authoring/fundamentals/page-properties.md#advanced) zugegriffen wird, können nicht veröffentlicht werden. Veröffentlichungsoptionen im Editor sind nur für Seiten verfügbar, auf die über ihre tatsächlichen Pfade zugegriffen wird.

### Veröffentlichungen über die Konsole {#publishing-from-the-console}

In der Sites-Konsole gibt es zwei Möglichkeiten zur Veröffentlichung:

* [Quick Publish](#quick-publish)
* [Veröffentlichung verwalten](#manage-publication)

#### Quick Publish {#quick-publish}

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

#### Veröffentlichung verwalten {#manage-publication}

**Veröffentlichung verwalten** bietet mehr Optionen als **Quick Publish**. Mit dieser Funktion können Sie auch untergeordnete Seiten einschließen, Verweise anpassen, alle nötigen Workflows starten und bei Bedarf zu einem späteren Zeitpunkt veröffentlichen.

So veröffentlichen Sie eine Seite bzw. machen ihre Veröffentlichung rückgängig mit „Veröffentlichung verwalten“:

1. Wählen Sie in der Sites-Konsole die entsprechenden Seiten aus und klicken Sie auf die Schaltfläche **Veröffentlichung verwalten**.

   ![Auswählen von Seiten zur Veröffentlichung](/help/sites-cloud/authoring/assets/publishing-select-pages.png)

1. Der Assistent **Veröffentlichung verwalten** wird geöffnet. Im ersten Schritt **Optionen** haben Sie folgende Möglichkeiten:

   * **Aktion**

      Veröffentlichen Sie die ausgewählte Seite oder machen Sie die Veröffentlichung rückgängig.

   * **Zeitplan**

      Führen Sie diese Aktion sofort oder zu einem späteren Zeitpunkt aus.

      Bei der späteren Veröffentlichung wird ein Workflow gestartet, mit dem die ausgewählten Seiten zur angegebenen Zeit veröffentlicht werden. Entsprechend wird durch die Auswahl des Rückgängigmachens der Veröffentlichung zu einem späteren Zeitpunkt der entsprechende Workflow für die ausgewählten Seiten zum angegebenen Zeitpunkt gestartet.

      >[!NOTE]
      >
      >Wenn Sie eine Veröffentlichung/rückgängig gemachte Veröffentlichung später abbrechen möchten, gehen Sie zur Konsole [Workflow](/help/sites-cloud/administering/workflows-administering.md#suspending-resuming-and-terminating-a-workflow-instance), um den entsprechenden Workflow zu beenden.
   ![Veröffentlichungsoptionen verwalten](/help/sites-cloud/authoring/assets/publishing-manage-publication-options.png)

1. Klicken Sie auf **Weiter**, um fortzufahren.

1. Im nächsten Schritt des Assistenten „Veröffentlichung verwalten“ können Sie den **Umfang** der Veröffentlichung/der rückgängig gemachten Veröffentlichung definieren, wie z. B. das Einschließen von untergeordneten Seiten und/oder von Verweisen.

   ![Umfang der Veröffentlichung verwalten](/help/sites-cloud/authoring/assets/publishing-manage-publication-scope.png)

   **Inhalt hinzufügen**

   Mit der Schaltfläche **Inhalt hinzufügen** können Sie zusätzliche Seiten zur Liste der zu veröffentlichenden Seiten hinzufügen, falls Sie dies noch nicht vor dem Starten des Assistenten „Veröffentlichung verwalten“ getan haben.

   Durch Klicken auf die Schaltfläche **Inhalt hinzufügen** wird der [Pfad-Browser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#path-browser) gestartet, mit dem Inhalte ausgewählt werden können.

   Wählen Sie die gewünschten Seiten aus und klicken Sie dann auf **Auswählen**, um den Inhalt dem Assistenten hinzuzufügen, oder auf **Abbrechen**, um die Auswahl abzubrechen und zum Assistenten zurückzukehren.

   **Auswahl entfernen**

   Im Assistenten können Sie ein Element in der Liste auswählen, um es aus der Auswahl zu entfernen.

   ![Verwalten von Veröffentlichungen mit Seitenauswahl](/help/sites-cloud/authoring/assets/publishing-manage-publication-select.png)

   **Veröffentlichte Verweise**

   Zur Ansicht und zum Ändern der Verweise, die für eine Seite veröffentlicht werden sollen bzw. deren Veröffentlichung rückgängig gemacht werden soll, wählen Sie sie aus und klicken Sie anschließend auf die Schaltfläche **Veröffentlichte Verweise**.

   ![Veröffentlichungsoptionen verwalten](/help/sites-cloud/authoring/assets/publishing-manage-publication-references.png)

   Das Dialogfeld **Veröffentlichte Verweise** zeigt die Verweise für den ausgewählten Inhalt an. Standardmäßig sind alle ausgewählt und werden veröffentlicht bzw. die Veröffentlichung wird rückgängig gemacht. Sie können sie aber auch deaktivieren, um die Auswahl aufzuheben, sodass sie nicht in die Aktion einbezogen werden.

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
   >Der gezeigte **Workflow**-Schritt hängt von den Rechten des jeweiligen Benutzers ab. Weitere Informationen finden Sie im vorherigen Hinweis auf dieser Seite bezüglich Berechtigungen für die Veröffentlichung sowie unter „Verwaltung der Zugriffsrechte auf Workflows“ und unter [Anwenden von Workflows auf Seiten](/help/sites-cloud/authoring/workflows/applying.md).

   Die Ressourcen werden gemäß den ausgelösten Workflows gruppiert, wobei Sie für jede Ressource folgende Möglichkeiten haben:

   * Definieren des Workflow-Titels
   * Beibehalten des Workflow-Pakets, vorausgesetzt der Workflow unterstützt mehrere Ressourcen.
   * Definieren des Titels des Workflow-Pakets, sofern die Option zum Beibehalten des Workflow-Pakets ausgewählt wurde

1. Klicken Sie auf **Veröffentlichen** oder **Später veröffentlichen**, um die Veröffentlichung abzuschließen.

## Veröffentlichen von Seiten rückgängig machen {#unpublishing-pages}

Wenn Sie die Veröffentlichung einer Seite rückgängig machen, wird sie aus der Veröffentlichungsumgebung gelöscht, sodass sie nicht mehr für Ihre Leser verfügbar ist.

[Ähnlich wie beim Veröffentlichen](#publishing-pages) können Sie auch die Veröffentlichung einer oder mehrerer Seiten aufheben:

* [Im Seiten-Editor](#unpublishing-from-the-editor)
* [In der Sites-Konsole](#unpublishing-from-the-console)

### Rückgängigmachen der Veröffentlichung im Editor {#unpublishing-from-the-editor}

Wenn Sie die Veröffentlichung einer von Ihnen bearbeiteten Seite rückgängig machen möchten, wählen Sie analog zur [Veröffentlichung einer Seite](#publishing-from-the-editor) im Menü **Seiteninformationen** die Option **Veröffentlichung der Seite rückgängig machen** aus.

>[!NOTE]
>
>Die Veröffentlichung von Seiten, auf die im Editor über [Aliasnamen](/help/sites-cloud/authoring/fundamentals/page-properties.md#advanced) zugegriffen wird, kann nicht rückgängig gemacht werden. Veröffentlichungsoptionen im Editor sind nur für Seiten verfügbar, auf die über ihre tatsächlichen Pfade zugegriffen wird.

### Rückgängigmachen der Veröffentlichung in der Konsole {#unpublishing-from-the-console}

Ebenso wie Sie [die Option „Veröffentlichung verwalten“ zur Veröffentlichung verwenden](#manage-publication), können Sie damit auch eine Veröffentlichung aufheben.

1. Wählen Sie in der Sites-Konsole die entsprechenden Seiten aus und klicken Sie auf die Schaltfläche **Veröffentlichung verwalten**.
1. Der Assistent **Veröffentlichung verwalten** wird geöffnet. Wählen Sie im ersten Schritt **Optionen** die Option **Veröffentlichung aufheben** anstelle der Standardoption **Veröffentlichen** aus.

   ![Veröffentlichung rückgängig machen – Optionen](/help/sites-cloud/authoring/assets/publishing-unpublish.png)

   Die Auswahl von „Später veröffentlichen“ startet einen Workflow zur Veröffentlichung der Seite zum angegebenen Zeitpunkt. Entsprechend startet die Auswahl von „Später deaktivieren“ einen Workflow zum Rückgängigmachen der Veröffentlichung der ausgewählten Seiten zum angegebenen Zeitpunkt.

   >[!NOTE]
   >
   >Wenn Sie eine Veröffentlichung/rückgängig gemachte Veröffentlichung später abbrechen möchten, gehen Sie zur Konsole [Workflow](/help/sites-cloud/administering/workflows-administering.md#suspending-resuming-and-terminating-a-workflow-instance), um den entsprechenden Workflow zu beenden.

1. Um das Rückgängigmachen der Veröffentlichung abzuschließen, fahren Sie mit dem Assistenten ähnlich wie beim [Veröffentlichen der Seite](#manage-publication) fort.

   ![Veröffentlichung rückgängig machen – Umfang](/help/sites-cloud/authoring/assets/publishing-unpublish-scope.png)

## Veröffentlichen und Rückgängigmachen der Veröffentlichung eines Baums {#publishing-and-unpublishing-a-tree}

Wenn Sie allerdings eine große Zahl von Inhaltsseiten erstellt bzw. aktualisiert haben, die sich alle unter derselben Stammseite befinden, kann es praktischer sein, mit einer einzigen Aktion den gesamten Baum zu veröffentlichen.

Dazu können Sie in der Sites-Konsole die Option [Veröffentlichung verwalten](#manage-publication) verwenden.

1. Wählen Sie in der Sites-Konsole die Stammseite des Baums aus, den Sie veröffentlichen möchten bzw. dessen Veröffentlichung Sie rückgängig machen möchten, und danach **Veröffentlichung verwalten**.
1. Der Assistent **Veröffentlichung verwalten** wird geöffnet. Wählen Sie „Veröffentlichen“ oder „Veröffentlichung aufheben“ sowie den Zeitpunkt aus und danach **Weiter**, um fortzufahren.
1. Wählen Sie im Schritt **Bereich** die Stammseite aus und danach **Untergeordnete Elemente einbeziehen**.

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

* In der [Ressourcenübersicht in der Sites-Konsole](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources)

   ![Veröffentlichungsstatus in der Kartenansicht](/help/sites-cloud/authoring/assets/publishing-status-console-card.png)

   Der Veröffentlichungsstatus wird in der Sites-Konsole in der Ansicht [Karte](/help/sites-cloud/authoring/getting-started/basic-handling.md#card-view), [Spalte](/help/sites-cloud/authoring/getting-started/basic-handling.md#column-view) und [Liste](/help/sites-cloud/authoring/getting-started/basic-handling.md#list-view) angezeigt.

* in der [Zeitleisten](/help/sites-cloud/authoring/getting-started/basic-handling.md#timeline)

   ![Veröffentlichungsstatus in der Zeitleisten-Ansicht](/help/sites-cloud/authoring/assets/publishing-status-timeline.png)

* im Menü [Seiteninformationen](/help/sites-cloud/authoring/fundamentals/environment-tools.md#page-information) beim Bearbeiten einer Seite

   ![Veröffentlichungsstatus im Menü „Seiteninformationen“](/help/sites-cloud/authoring/assets/publishing-status-page-information.png)
