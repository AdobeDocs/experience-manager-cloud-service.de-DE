---
title: Anwenden von Workflows auf Seiten
description: Beim Authoring können Sie Workflows aufrufen, um auf Ihren Seiten Aktionen auszuführen. Es ist auch möglich, mehrere Workflows anzuwenden.
exl-id: 86e71f0e-e53e-40bc-901d-2a1ab347bd0a
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '662'
ht-degree: 100%

---

# Anwenden von Workflows auf Seiten {#applying-workflows-to-pages}

Beim Authoring können Sie Workflows aufrufen, um auf Ihren Seiten Maßnahmen zu ergreifen. Es ist auch möglich, mehrere Workflows anzuwenden.

Wenn Sie den Workflow anwenden, geben Sie die folgenden Informationen an:

* Der anzuwendende Workflow.
   * Sie können jeden beliebigen Workflow anwenden (auf den Sie Zugriff haben, wie von Ihrem AEM-Administrator zugewiesen).
* Optional: Ein Titel, der dabei hilft, die Workflow-Instanz im Posteingang eines Benutzers zu erkennen.
* Die Workflow-Nutzlast. Hierbei kann es sich um eine oder mehrere Seiten handeln.

Workflows können wie folgt gestartet werden:

* [von der Sites-Konsole aus](#starting-a-workflow-from-the-sites-console).
* [beim Bearbeiten einer Seite von den Seiteninformationen](#starting-a-workflow-from-the-page-editor) aus.

>[!NOTE]
>
>Siehe auch:
>
>* Anwenden von Workflows auf DAM-Assets.
>* [Arbeiten mit Projekt-Workflows](/help/sites-cloud/authoring/projects/workflows.md).


<!-- 
>* [How to apply workflows to DAM assets](/help/assets/assets-workflow.md).
>* [Working with Project Workflows](/help/sites-cloud/authoring/projects/workflows.md).
-->

>[!NOTE]
>
>AEM-Administratoren können Workflows mithilfe mehrerer anderer Methoden starten.

<!-- 
>AEM administrators can [start workflows using several other methods](/help/sites-administering/workflows-starting.md).
-->

## Starten eines Workflows von der Sites-Konsole aus {#starting-a-workflow-from-the-sites-console}

Sie können einen Workflow wie folgt starten:

* [die Option Erstellen der Sites-Symbolleiste.](#starting-a-workflow-from-the-sites-toolbar)
* [die Timeline-Leiste der Sites-Konsole](#starting-a-workflow-from-the-timeline).

In beiden Fällen ist Folgendes zu tun:

* [Geben Sie die Workflow-Details im Workflow-Erstellungs-Assistenten an](#specifying-workflow-details-in-the-create-workflow-wizard).

### Starten eines Workflows von der Sites-Symbolleiste aus {#starting-a-workflow-from-the-sites-toolbar}

Sie können einen Workflow von der Symbolleiste der **Sites**-Konsole aus starten:

1. Gehen Sie zur gewünschten Seite und wählen Sie sie aus.

1. Von der Option **Erstellen** in der Symbolleiste aus können Sie jetzt **Workflow** auswählen.

   ![Erstellen von Workflows über die Symbolleiste](/help/sites-cloud/authoring/assets/workflows-create-from-toolbar.png)

1. Der Assistent **Workflow erstellen** hilft Ihnen, [die Workflow-Details anzugeben](#specifying-workflow-details-in-the-create-workflow-wizard).

### Starten eines Workflows aus der Timeline {#starting-a-workflow-from-the-timeline}

Aus der **Timeline** können Sie einen Workflow starten, der auf Ihre ausgewählte Ressource angewendet werden soll.

1. [Wählen Sie die Ressource aus](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources) und öffnen Sie die [Timeline](/help/sites-cloud/authoring/getting-started/basic-handling.md#timeline) (oder öffnen Sie die Timeline und wählen Sie dann die Ressource aus).
1. Der Pfeil neben dem Kommentarfeld kann verwendet werden, um **Workflow starten** anzuzeigen:

   ![Erstellen von Workflows über die Timeline](/help/sites-cloud/authoring/assets/workflows-create-from-timeline.png)

1. Der Assistent **Workflow erstellen** hilft Ihnen, [die Workflow-Details anzugeben](#specifying-workflow-details-in-the-create-workflow-wizard).

### Angeben von Workflow-Details im Assistenten „Workflow erstellen“ {#specifying-workflow-details-in-the-create-workflow-wizard}

Der Assistent **Workflow erstellen** hilft Ihnen, den Workflow auszuwählen und die erforderlichen Details anzugeben.

Öffnen Sie den Assistenten **Workflow erstellen** über

* [die Option Erstellen der Sites-Symbolleiste.](#starting-a-workflow-from-the-sites-toolbar)
* [die Timeline-Leiste der Sites-Konsole](#starting-a-workflow-from-the-timeline).

Anschließend können Sie Details angeben:

1. Unter **Eigenschaften** werden die grundlegenden Optionen des Workflows definiert:

   * **Workflow-Modell**
   * **Workflow-Titel**

      * Sie können einen Titel für diese Instanz angeben, damit Sie sie zu einem späteren Zeitpunkt identifizieren können.

   Abhängig vom Workflow-Modell stehen die folgenden Optionen zur Verfügung. Diese erlauben, das als Payload erstellte Paket zu behalten, nachdem der Workflow beendet ist.

   * **Workflow-Paket behalten**
   * **Paketname**

      * Sie können einen Titel für das Paket festlegen, um die Identifizierung erleichtern.
   >[!NOTE]
   >
   >Die Option **Workflow-Paket behalten** ist verfügbar, wenn der Workflow für Unterstützung für mehrere Ressourcen konfiguriert wurde und mehrere Ressourcen ausgewählt wurden.

   <!--
   >The **Keep workflow package** option is available when the workflow has been configured for [Multi Resource Support](/help/sites-developing/workflows-models.md#configuring-a-workflow-for-multi-resource-support) and multiple resources have been selected.
   -->

   Wenn Sie fertig sind, klicken Sie auf **Weiter**, um fortzufahren.

   ![Festlegen von Workflow-Eigenschaften](/help/sites-cloud/authoring/assets/workflows-properties.png)

1. Im Schritt **Umfang** können Sie Folgendes auswählen:

   * **Inhalt hinzufügen**, um den [Pfad-Browser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#path-browser) zu öffnen und zusätzliche Ressourcen auszuwählen; im Browser klicken/tippen Sie auf **Auswählen**, um den Inhalt zur Workflow-Instanz hinzuzufügen.

   * Eine vorhandene Ressource, um weitere Aktionen zu sehen:

      * **Untergeordnete Elemente einbeziehen**, um anzugeben, dass untergeordnete Elemente der betreffenden Ressource im Workflow enthalten sind.
Ein Dialogfeld wird geöffnet, in dem Sie die Auswahl verfeinern können:

         * Nur unmittelbar untergeordnete Elemente einbeziehen.
         * Nur geänderte Seiten einbeziehen.
         * Nur bereits veröffentlichte Seiten einbeziehen.

         Alle angegebenen untergeordneten Elemente werden der Liste der Ressourcen hinzugefügt, auf die der Workflow angewendet wird.

      * **Auswahl entfernen**, um die betreffende Ressource aus dem Workflow zu entfernen.

   ![Definieren des Workflow-Umfangs](/help/sites-cloud/authoring/assets/workflows-scope.png)

   >[!NOTE]
   >
   >Wenn Sie zusätzliche Ressourcen hinzufügen, können Sie **Zurück** verwenden, um die Einstellung für **Workflow-Paket behalten** im Schritt **Eigenschaften** anzupassen.

1. Verwenden Sie **Erstellen**, um den Assistenten zu schließen und die Workflow-Instanz zu erstellen. In der Sites-Konsole wird eine Benachrichtigung angezeigt.

## Starten eines Workflows aus dem Seiten-Editor {#starting-a-workflow-from-the-page-editor}

Wenn Sie eine Seite bearbeiten, können Sie die **Seiteninformationen** von der Symbolleiste aus aufrufen. Das Dropdown-Menü enthält die Option **Im Workflow starten**. Ein Dialogfeld wird geöffnet, in dem Sie den gewünschten Workflow ggf. zusammen mit einem Titel angeben können:

![Starten eines Workflows aus dem Seiten-Editor](/help/sites-cloud/authoring/assets/workflows-create-page-editor.png)
