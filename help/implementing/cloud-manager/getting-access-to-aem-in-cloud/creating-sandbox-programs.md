---
title: 'Erstellen von Sandbox-Programmen '
description: Erfahren Sie, wie Sie mit Cloud Manager Ihr eigenes Sandbox-Programm für Schulungs-, Demo-, POC- oder andere produktionsfremde Zwecke erstellen.
exl-id: 10011392-3059-4bb0-88db-0af1d390742e
source-git-commit: cf6941759dfc1e50928009490c7c518a89ed093e
workflow-type: ht
source-wordcount: '331'
ht-degree: 100%

---

# Erstellen von Sandbox-Programmen {#create-sandbox-program}

Sandbox-Programme werden normalerweise für Schulungen, das Ausführen von Demos, Aktivierungen, POCs oder Dokumentationen erstellt und sind nicht für Live-Traffic vorgesehen.

Weitere Informationen zu Programmtypen finden Sie im Dokument [Programm- und Programmtypen](program-types.md).

## Erstellen eines Sandbox-Programms {#create}

Gehen Sie wie folgt vor, um ein Sandbox-Programm zu erstellen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie auf der Landingpage von Cloud Manager in der oberen rechten Ecke des Bildschirms auf **Programm hinzufügen**.

   ![Cloud Manager-Landingpage](assets/first_timelogin1.png)

1. Wählen Sie im Assistenten „Programm erstellen“ die Option **Sandbox einrichten**, geben Sie einen Programmnamen ein und klicken Sie auf **Erstellen**.

   ![Erstellen von Programmtypen](assets/create-sandbox.png)

Auf der Landingpage wird eine neue Sandbox-Programmkarte mit einer Statusanzeige angezeigt, während der Einrichtungsprozess fortgesetzt wird.

![Erstellen von Sandboxes von der Übersichtsseite](assets/program-create-setupdemo2.png)

## Zugriff auf Sandboxes {#access}

Sie können die Details Ihrer Sandbox-Einrichtung anzeigen und auf die Umgebung zugreifen (sobald sie verfügbar ist), indem Sie die Seite „Programmübersicht“ aufrufen.

1. Klicken Sie auf der Landingpage von Cloud Manager in Ihrem neu erstellten Programm auf die Schaltfläche mit den Auslassungspunkten.

   ![Zugriff auf die Programmübersicht](assets/program-overview-sandbox.png)

1. Sobald der Schritt zur Projekterstellung abgeschlossen ist, können Sie den Link **Zugriff auf Repo-Info** verwenden, um Ihr Git-Repo verwenden zu können.

   ![Konfiguration von Programmen](assets/create-program4.png)

   >[!TIP]
   >
   >Weitere Informationen zum Zugriff auf und zur Verwaltung Ihres Git-Repositorys finden Sie im Dokument [Zugriff auf Git](/help/implementing/cloud-manager/managing-code/accessing-repos.md).

1. Nachdem die Entwicklungsumgebung erstellt wurde, können Sie den Link **Zugriff auf AEM** verwenden, um sich bei AEM anzumelden.

   ![Link „Zugriff auf AEM“](assets/create-program-5.png)

1. Sobald die Bereitstellung der produktionsfremden Pipeline in der Entwicklungsumgebung abgeschlossen ist, führt der Assistent den Benutzer entweder zum Zugriff auf AEM (in der Entwicklungsumgebung) oder zur Bereitstellung von Code in der Entwicklungsumgebung.

   ![Bereitstellen einer Sandbox](assets/create-program-setup-deploy.png)

Wenn Sie irgendwann zu einem anderen Programm wechseln oder zur Übersichtsseite zurückkehren möchten, um ein anderes Programm zu erstellen, klicken Sie auf den Namen Ihres Programms oben links im Bildschirm, um die Option **Navigieren zu** aufzurufen.

![Navigieren zu](assets/create-program-a1.png)
