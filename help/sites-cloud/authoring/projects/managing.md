---
title: Verwalten von Projekten
description: In „Projekte“ können Sie ein Projekt organisieren, indem Sie Ressourcen zu einer Einheit zusammenfassen. Der Zugriff und die Verwaltung erfolgen über die Projektekonsole.
exl-id: be4616e7-18bc-4b2d-89f6-d04178ac7f3a
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 6719e0bcaa175081faa8ddf6803314bc478099d7
workflow-type: tm+mt
source-wordcount: '876'
ht-degree: 100%

---

# Verwalten von Projekten {#managing-projects}

Mithilfe von Projekten können Sie Ressourcen zu einer Einheit gruppieren.

In der **Projektekonsole** können Sie auf Ihre Projekte zugreifen und sie bearbeiten:

![Die Projektekonsole](/help/sites-cloud/authoring/assets/projects-console.png)

In „Projekte“ können Sie ein Projekt erstellen, Ressourcen mit Ihrem Projekt verknüpfen sowie Projekte oder Ressourcenlinks löschen. Sie können eine Kachel öffnen, um ihren Inhalt anzuzeigen und Elemente zu einer Kachel hinzuzufügen. In diesem Thema werden diese Vorgehensweisen beschrieben.

## Erstellen eines Projekts {#creating-a-project}

Standardmäßig enthält AEM folgende Vorlagen für die Projekterstellung:

* Einfaches Projekt
* Medienprojekt
* Übersetzungsprojekt

<!-- Hiding product photoshoot via cqdoc-18072 as it is not available in Skyline.
* Product Photo Shoot Project 
-->

Die Vorgehensweise beim Erstellen eines Projekts ist für jedes Projekt identisch. Unterschiede zwischen den Projekttypen gibt es in Bezug auf verfügbare [Benutzerrollen](/help/sites-cloud/authoring/projects/overview.md) und [Workflows](/help/sites-cloud/authoring/projects/workflows.md).  So erstellen Sie ein Projekt:

1. Wählen Sie in **Projekte** die Option **Erstellen** aus, um den Assistenten zur **Projekterstellung** zu öffnen:
1. Wählen Sie eine Vorlage aus und klicken Sie auf **Weiter**.

   ![Erstellen eines Projekts](/help/sites-cloud/authoring/assets/projects-create.png)

1. Definieren Sie den **Titel** und die **Beschreibung** und fügen Sie eine **Miniaturansicht** hinzu, falls erforderlich. Hier können Sie auch Benutzer und deren Gruppenzugehörigkeit hinzufügen oder löschen. Sie können darüber hinaus auf **Erweitert** klicken, um einen Namen anzugeben, der in der URL verwendet werden soll.

   ![Hinzufügen von Projektdetails](/help/sites-cloud/authoring/assets/projects-add-team.png)

1. Wählen Sie **Erstellen** aus. Daraufhin werden Sie gefragt, ob Sie ein neues Projekt öffnen oder zur Konsole zurückkehren möchten.

### Zuordnen von Ressourcen zum Projekt {#associating-resources-with-your-project}

Da Projekte es Ihnen ermöglichen, Ressourcen zu einer Einheit zu gruppieren, können Sie diese Ressourcen nun Ihrem Projekt hinzufügen. Die Ressourcen werden als **Kacheln** bezeichnet. Die Ressourcentypen, die Sie mit einem Projekt verknüpfen können, werden unter [Projektkacheln](/help/sites-cloud/authoring/projects/overview.md#project-tiles) beschrieben.

So ordnen Sie Ihrem Projekt Ressourcen zu:

1. Öffnen Sie das Projekt in der **Projektekonsole**.
1. Wählen Sie **Titel hinzufügen** und wählen Sie den Titel aus, den Sie mit Ihrem Projekt verknüpfen möchten. Sie können mehrere Arten von Kacheln auswählen.

   ![Hinzufügen einer Kachel zu einem Projekt](/help/sites-cloud/authoring/assets/projects-add-tile.png)

   >[!NOTE]
   >
   >Die Projektkacheln, die mit einem Projekt verknüpft werden können, werden ausführlich unter [Projektkacheln](/help/sites-cloud/authoring/projects/overview.md#project-tiles) beschrieben.

1. Wählen Sie **Erstellen** aus. Die Ressource wird mit Ihrem Projekt verknüpft und danach können Sie über Ihr Projekt auf sie zugreifen.

### Löschen eines Projekts oder Ressourcen-Links {#deleting-a-project-or-resource-link}

Dieselbe Methode wird zum Löschen eines Projekts aus der Konsole oder einer verknüpften Ressource aus Ihrem Projekt angewendet:

1. Navigieren Sie zum entsprechenden Ort:

   * Um ein Projekt zu löschen, gehen Sie zur obersten Ebene der **Projektekonsole**.
   * Um einen Ressourcen-Link innerhalb eines Projekts zu löschen, öffnen Sie das Projekt in der **Projektekonsole**.

1. Aktivieren Sie den Auswahlmodus, indem Sie auf **Auswahl** klicken und Ihr Projekt oder Ihren Ressourcen-Link auswählen.
1. Wählen Sie **Löschen** aus.

1. Sie müssen den Löschvorgang in einem Dialogfeld bestätigen. Nach der Bestätigung wird das Projekt oder der Ressourcenlink gelöscht. Wählen Sie **Auswahl aufheben** aus, um den Auswahlmodus zu beenden.

>[!NOTE]
>
>Wenn Sie das Projekt erstellen und den verschiedenen Rollen Benutzer hinzufügen, werden mit dem Projekt verknüpfte Gruppen automatisch erstellt, um die zugehörigen Berechtigungen zu verwalten. Ein Projekt mit dem Namen Myproject könnte z. B. drei Gruppen **Myproject-Eigentümer**, **MyProject-Editor**, **MyProject-Beobachter** haben. Wird das Projekt jedoch gelöscht, werden diese Gruppen nicht automatisch gelöscht. Die Gruppen unter **Tools** > **Sicherheit** > **Gruppen** müssen von Admins manuell gelöscht werden.

### Hinzufügen von Elementen zu einer Kachel {#adding-items-to-a-tile}

In einigen Kacheln benötigen Sie möglicherweise mehr als ein Element. Dies ist zum Beispiel der Fall, wenn Sie mehr als einen gleichzeitig ausgeführten Workflow oder mehr als ein Erlebnis haben.

So fügen Sie einer Kachel Elemente hinzu:

1. Navigieren Sie unter **Projekte** zum Projekt und wählen Sie den nach unten zeigenden Pfeil auf der Kachel aus, der ein Element hinzugefügt werden soll.

   ![Element zu einer Kachel hinzufügen](/help/sites-cloud/authoring/assets/project-workflows.png)

1. Fügen Sie der Kachel ein Element so hinzu, wie Sie eine neue Kachel erstellen würden. Weitere Informationen finden Sie unter [Projektkacheln](/help/sites-cloud/authoring/projects/overview.md#project-tiles). In diesem Beispiel wurde ein Workflow hinzugefügt.

### Öffnen einer Kachel {#opening-a-tile}

Manchmal kann es nötig sein zu wissen, welche Elemente in einer aktuellen Kachel enthalten sind, oder die Elemente in einer Kachel zu ändern oder zu löschen.

Dazu öffnen Sie die Kachel, sodass Sie ihre Elemente anzeigen und ändern können:

1. Wählen Sie in der Projektkonsole unten auf der Karte das Symbol mit den Auslassungspunkten (…) aus.

   ![Öffnen einer Kachel](/help/sites-cloud/authoring/assets/project-links.png)

1. In AEM wird eine Liste mit den Elementen in der Kachel angezeigt. Sie können den Auswahlmodus aktivieren, um die Elemente zu ändern oder zu löschen.

   ![Geöffnete Kachel](/help/sites-cloud/authoring/assets/projects-add-link.png)

## Anzeigen von Projektstatistiken {#viewing-project-statistics}

Sie können die Projektstatistiken in der Konsole **Projekte** einsehen.

### Anzeigen einer Projekt-Zeitleiste {#viewing-a-project-timeline}

Die Projekt-Zeitleiste enthält Informationen dazu, wann Assets des Projekts zuletzt verwendet wurden. Wählen Sie zum Anzeigen der Projekt-Timeline die Option **Timeline** aus, aktivieren Sie den Auswahlmodus und wählen Sie das Projekt aus. Die Assets werden im linken Bereich angezeigt. Wählen Sie **Timeline** aus, um zur **Projektkonsole** zurückzukehren.

![Projekt-Zeitleiste](/help/sites-cloud/authoring/assets/projects-timeline.png)

### Anzeigen aktiver/inaktiver Projekte {#viewing-active-inactive-projects}

Um zwischen aktiven und inaktiven Projekten zu wechseln, klicken Sie in der **Projektekonsole** auf **Aktive Projekte ein/aus**. Wenn neben dem Symbol ein Häkchen zu sehen ist, werden die aktiven Projekte angezeigt.

![Schaltfläche „Aktive Projekte ein/aus“](/help/sites-cloud/authoring/assets/projects-active.png)

Wenn neben dem Symbol ein x zu sehen ist, werden die inaktiven Projekte angezeigt.

![Schaltfläche „Inaktive Projekte ein/aus“](/help/sites-cloud/authoring/assets/projects-inactive.png)

## Festlegen von Projekten als inaktiv oder aktiv {#making-projects-inactive-or-active}

Sie können ein Projekt als inaktiv festlegen, wenn Sie es abgeschlossen haben, aber die Informationen weiter beibehalten möchten.

So legen Sie ein Projekt als inaktiv (oder aktiv) fest:

1. Öffnen Sie das Projekt in der **Projektekonsole** und suchen Sie die Kachel **Projektinformationen**.

   >[!NOTE]
   >
   >Möglicherweise müssen Sie diese Kachel erst noch einfügen, wenn sie nicht bereits in Ihrem Projekt enthalten ist. Weitere Informationen finden Sie unter [Hinzufügen von Kacheln](#adding-items-to-a-tile).

1. Wählen Sie **Bearbeiten** aus.
1. Ändern Sie die Auswahl von **Aktiv** zu **Inaktiv** (oder umgekehrt).

   ![Aktivieren eines Projekts](/help/sites-cloud/authoring/assets/projects-add-team.png)

1. Wählen Sie **Fertig** aus, um Ihre Änderungen zu speichern.
