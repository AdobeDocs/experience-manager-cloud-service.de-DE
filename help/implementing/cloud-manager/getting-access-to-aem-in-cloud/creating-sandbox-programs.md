---
title: Erstellen von Sandbox-Programmen
description: Erfahren Sie, wie Sie mit Cloud Manager Ihr eigenes Sandbox-Programm für Schulungs-, Demo-, POC- oder andere produktionsfremde Zwecke erstellen.
exl-id: 10011392-3059-4bb0-88db-0af1d390742e
source-git-commit: 8ed477ec0c54bb0913562b9581e699c0bdc973ec
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 90%

---

# Erstellen von Sandbox-Programmen {#create-sandbox-program}

Sandbox-Programme werden normalerweise für Schulungen, das Ausführen von Demos, Aktivierungen, POCs oder Dokumentationen erstellt und sind nicht für Live-Traffic vorgesehen.

Weitere Informationen zu Programmtypen finden Sie im Dokument [Programm- und Programmtypen](program-types.md).

## Erstellen eines Sandbox-Programms {#create}

1. Melden Sie sich bei Cloud Manager unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie auf der Landingpage von Cloud Manager oben rechts im Bildschirm auf **Programm hinzufügen**.

   ![Cloud Manager-Landingpage](assets/cloud-manager-my-programs.png)

1. Wählen Sie im Assistenten zum Erstellen von Programmen die Option **Sandbox einrichten** und geben Sie einen Programmnamen ein.

   ![Erstellen von Programmtypen](assets/create-sandbox.png)

1. Optional können Sie ein Bild zum Programm hinzufügen, indem Sie eine Bilddatei per Drag-and-Drop auf das Ziel **Programmbild hinzufügen** ziehen oder darauf klicken, um ein Bild aus einem Dateibrowser auszuwählen. Klicken Sie auf **Weiter**.

   * Das Bild dient nur als Kachel im Programmübersichtsfenster und hilft bei der Identifizierung des Programms.

1. Im **Sandbox einrichten** auswählen, welche Lösungen Sie in Ihrem Sandbox-Programm aktivieren möchten, indem Sie die Optionen im **Lösungen und Add-ons** Tabelle.

   * Verwenden Sie die Pfeile neben den Lösungsnamen, um zusätzliche, optionale Add-ons für die Lösungen anzuzeigen.

   * Die **Sites**- und **Assets**-Lösungen sind immer in Sandbox-Programmen enthalten und können nicht deaktiviert werden.

   ![Lösungen und Add-ons für eine Sandbox auswählen](assets/sandbox-solutions-add-ons.png)

1. Nachdem Sie die Lösungen und Add-ons für Ihr Sandbox-Programm ausgewählt haben, tippen Sie auf **Erstellen**.

Auf der Landingpage wird eine neue Sandbox-Programmkarte mit einer Statusanzeige angezeigt, während der Einrichtungsprozess fortgesetzt wird.

![Erstellen von Sandboxes von der Übersichtsseite](assets/sandbox-setup.png)

## Sandbox-Zugriff {#access}

Sie können die Details Ihrer Sandbox-Einrichtung anzeigen und auf die Umgebung zugreifen (sobald sie verfügbar ist), indem Sie die Seite „Programmübersicht“ aufrufen.

1. Klicken Sie auf der Landingpage von Cloud Manager auf die Suchschaltfläche in Ihrem erstellten Programm.

   ![Zugriff auf die Programmübersicht](assets/program-overview-sandbox.png)

1. Sobald der Schritt zur Projekterstellung abgeschlossen ist, können Sie den Link **Zugriff auf Repo-Info** verwenden, um Ihr Git-Repo verwenden zu können.

   ![Konfiguration von Programmen](assets/create-program4.png)

   >[!TIP]
   >
   >Weitere Informationen zum Zugriff auf und zur Verwaltung Ihres Git-Repositorys finden Sie unter [Zugriff auf Git](/help/implementing/cloud-manager/managing-code/accessing-repos.md).

1. Nachdem die Entwicklungsumgebung erstellt wurde, können Sie den Link **Zugriff auf AEM** verwenden, um sich bei AEM anzumelden.

   ![Link „Zugriff auf AEM“](assets/create-program-5.png)

1. Sobald die Bereitstellung der produktionsfremden Pipeline in der Entwicklungsumgebung abgeschlossen ist, führt der Assistent den Benutzer entweder zum Zugriff auf AEM (in der Entwicklungsumgebung) oder zur Bereitstellung von Code in der Entwicklungsumgebung.

   ![Bereitstellen einer Sandbox](assets/create-program-setup-deploy.png)

Wenn Sie irgendwann zu einem anderen Programm wechseln oder zur Übersichtsseite zurückkehren möchten, um ein anderes Programm zu erstellen, klicken Sie auf den Namen Ihres Programms oben links im Bildschirm, um die Option **Navigieren zu** aufzurufen.

![Navigieren zu](assets/create-program-a1.png)
