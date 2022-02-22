---
title: 'Erstellen von Sandbox-Programmen '
description: Erfahren Sie, wie Sie mit Cloud Manager Ihr eigenes Sandbox-Programm für Trainings-, Demo-, POC- oder andere Nicht-Produktions-Zwecke erstellen.
exl-id: 10011392-3059-4bb0-88db-0af1d390742e
source-git-commit: cf6941759dfc1e50928009490c7c518a89ed093e
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 1%

---

# Erstellen von Sandbox-Programmen {#create-sandbox-program}

Sandbox-Programme werden normalerweise für Schulungen, laufende Demos, Aktivierungen, POCs oder Dokumentationen erstellt und sind nicht für Live-Traffic vorgesehen.

Weitere Informationen zu Programmtypen finden Sie im Dokument . [Grundlegendes zu Programm- und Programmtypen.](program-types.md)

## Erstellen eines Sandbox-Programms {#create}

Führen Sie die folgenden Schritte aus, um ein Sandbox-Programm zu erstellen.

1. Melden Sie sich bei Cloud Manager an unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie auf der Landingpage von Cloud Manager auf **Programm hinzufügen** in der oberen rechten Ecke des Bildschirms.

   ![Landingpage von Cloud Manager](assets/first_timelogin1.png)

1. Wählen Sie im Assistenten Programm erstellen die Option **Sandbox einrichten**, geben Sie einen Programmnamen ein und klicken Sie auf **Erstellen**.

   ![Erstellung von Programmtypen](assets/create-sandbox.png)

Auf der Landingpage wird eine neue Sandbox-Programmkarte mit einer Statusanzeige angezeigt, während der Einrichtungsprozess fortgesetzt wird.

![Sandbox-Erstellung auf der Übersichtsseite](assets/program-create-setupdemo2.png)

## Zugriff auf Ihre Sandbox {#access}

Sie können die Details Ihrer Sandbox-Einrichtung anzeigen und auf die Umgebung zugreifen (sobald sie verfügbar ist), indem Sie die Seite Programmübersicht aufrufen.

1. Klicken Sie auf der Landingpage von Cloud Manager in Ihrem neu erstellten Programm auf die Suchschaltfläche .

   ![Programmübersicht aufrufen](assets/program-overview-sandbox.png)

1. Sobald der Schritt zur Projekterstellung abgeschlossen ist, können Sie auf die **Zugriff auf Repo Info** -Link, um Ihr Git-Repo verwenden zu können.

   ![Programmkonfiguration](assets/create-program4.png)

   >[!TIP]
   >
   >Weitere Informationen zum Zugriff auf und zur Verwaltung Ihres Git-Repositorys finden Sie im Dokument . [Zugriff auf Git.](/help/implementing/cloud-manager/managing-code/accessing-repos.md)

1. Nachdem die Entwicklungsumgebung erstellt wurde, können Sie die **AEM** -Link, um sich bei AEM anzumelden.

   ![Auf AEM Link zugreifen](assets/create-program-5.png)

1. Sobald die in der Entwicklung bereitgestellte Nicht-Produktions-Pipeline abgeschlossen ist, führt der Assistent Sie zum Zugriff auf die AEM Entwicklungsumgebung oder zum Bereitstellen von Code in der Entwicklungsumgebung.

   ![Sandbox bereitstellen](assets/create-program-setup-deploy.png)

Wenn Sie zu einem anderen Programm wechseln oder zur Übersichtsseite zurückkehren müssen, um ein anderes Programm zu erstellen, klicken Sie auf den Programmnamen oben links im Bildschirm, um die **Navigieren Sie zu** -Option.

![Navigieren Sie zu](assets/create-program-a1.png)
