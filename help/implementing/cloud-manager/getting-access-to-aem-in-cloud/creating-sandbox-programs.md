---
title: Erstellen von Sandbox-Programmen
description: Erfahren Sie, wie Sie mit Cloud Manager Ihr eigenes Sandbox-Programm für Schulungs-, Demo-, POC- oder andere produktionsfremde Zwecke erstellen.
exl-id: 10011392-3059-4bb0-88db-0af1d390742e
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: ht
source-wordcount: '434'
ht-degree: 100%

---

# Erstellen von Sandbox-Programmen {#create-sandbox-program}

Sandbox-Programme werden normalerweise für Schulungen, das Ausführen von Demos, Aktivierungen, POCs oder Dokumentationen erstellt und sind nicht für Live-Traffic vorgesehen.

Weitere Informationen zu Programmtypen finden Sie im Dokument [Programm- und Programmtypen](program-types.md).

## Erstellen eines Sandbox-Programms {#create}

1. Melden Sie sich bei Cloud Manager unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) an und wählen Sie die entsprechende Organisation aus.

1. Tippen oder klicken Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** oben rechts auf **Programm hinzufügen**.

   ![Cloud Manager-Landingpage](assets/log-in.png)

1. Wählen Sie im Assistenten zum Erstellen von Programmen die Option **Sandbox einrichten** und geben Sie einen Programmnamen ein.

   ![Erstellen von Programmtypen](assets/create-sandbox.png)

1. Optional können Sie ein Bild zum Programm hinzufügen, indem Sie eine Bilddatei per Drag-and-Drop auf das Ziel **Programmbild hinzufügen** ziehen oder darauf klicken, um ein Bild aus einem Datei-Browser auszuwählen. Wählen Sie **Weiter**.

   * Das Bild dient nur als Kachel im Programmübersichtsfenster und hilft bei der Identifizierung des Programms.

1. Wählen Sie im Dialogfeld **Sandbox einrichten**, welche Lösungen in Ihrem Sandbox-Programm aktiviert werden sollen, indem Sie die Optionen in der Tabelle **Lösungen und Add-ons** aktivieren.

   * Verwenden Sie die Pfeile neben den Lösungsnamen, um zusätzliche, optionale Add-ons für die Lösungen anzuzeigen.

   * Die **Sites**- und **Assets**-Lösungen sind immer in Sandbox-Programmen enthalten und können nicht deaktiviert werden.

   ![Lösungen und Add-ons für eine Sandbox auswählen](assets/sandbox-solutions-add-ons.png)

1. Nachdem Sie die Lösungen und Add-ons für Ihr Sandbox-Programm ausgewählt haben, tippen Sie auf **Erstellen**.

Auf der Landingpage wird eine neue Sandbox-Programmkarte mit einer Statusanzeige angezeigt, während der Einrichtungsprozess fortgesetzt wird.

![Erstellen von Sandboxes von der Übersichtsseite](assets/sandbox-setup.png)

## Sandbox-Zugriff {#access}

Sie können die Details Ihrer Sandbox-Einrichtung anzeigen und auf die Umgebung zugreifen (sobald sie verfügbar ist), indem Sie die Seite „Programmübersicht“ aufrufen.

1. Klicken Sie auf der Landingpage von Cloud Manager in Ihrem erstellten Programm auf die Schaltfläche mit den Auslassungspunkten.

   ![Zugriff auf die Programmübersicht](assets/program-overview-sandbox.png)

1. Sobald der Schritt zur Projekterstellung abgeschlossen ist, können Sie den Link **Zugriff auf Repo-Info** verwenden, um Ihr Git-Repo verwenden zu können.

   ![Konfiguration von Programmen](assets/create-program4.png)

   >[!TIP]
   >
   >Weitere Informationen zum Zugriff auf und zur Verwaltung Ihres Git-Repositorys finden Sie unter [Zugriff auf Git](/help/implementing/cloud-manager/managing-code/accessing-repos.md).

1. Nachdem die Entwicklungsumgebung erstellt wurde, können Sie den Link **Zugriff auf AEM** verwenden, um sich bei AEM anzumelden.

   ![Link „Zugriff auf AEM“](assets/create-program5.png)

1. Sobald die Bereitstellung der produktionsfremden Pipeline in der Entwicklungsumgebung abgeschlossen ist, führt Sie der Assistent in den Guides für Aktionsaufrufe entweder zum Zugriff auf die AEM-Entwicklungsumgebung oder zur Code-Bereitstellung in der Entwicklungsumgebung.

   ![Bereitstellen einer Sandbox](assets/create-program-setup-deploy.png)

>[!TIP]
>
>Weitere Informationen zum Navigieren in Cloud Manager und zum Verständnis der Konsole **Meine Programme** finden Sie unter [Navigation in der Cloud Manager-Benutzeroberfläche](/help/implementing/cloud-manager/navigation.md).
