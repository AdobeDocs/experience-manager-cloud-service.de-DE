---
title: Erstellen eines Programms - Cloud Service
description: Erstellen eines Programms - Cloud Service
translation-type: tm+mt
source-git-commit: 5658b2cc853ff7e6222a7f35e56527577d2c7324
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 3%

---


# Erstellen eines Programms {#create-a-program}

Die Cloud-native Lösung bietet dem Benutzer die erforderlichen Berechtigungen und die Möglichkeit, ein Programm auf einem Selbstbedienungsmodell zu erstellen.

Ein Assistent zum Erstellen von Programmen fordert den Benutzer auf, Details zu übermitteln, je nachdem, welches Ziel der Benutzer beim Erstellen des Programms innerhalb der Grenzen dessen verfolgt, was dem jeweiligen Kunden oder Unternehmen zur Verfügung steht.

Im Ereignis des erstmaligen Zugriffs auf Cloud Manager oder wenn keine Programm im Mieter vorhanden sind, wird der Bildschirm &quot;Erstes Programm **erstellen** &quot;angezeigt. Wenn der Benutzer *Esc* auswählt oder außerhalb des Dialogfelds klickt, wird der folgende Bildschirm angezeigt:

![](assets/create-program1.png)


## Verwenden des Assistenten zum Erstellen von Programmen {#using-create-program-wizard}

Je nachdem, welches Ziel der Benutzer beim Erstellen des Programms innerhalb der Grenzen dessen verfolgt, was dem jeweiligen Kunden/Unternehmen zur Verfügung steht, wird der Programm-Erstellungsassistent aufgefordert, eine oder mehrere Angaben zu übermitteln.

![](assets/create-sandbox.png)

>[!NOTE]
>If a program already exists, then you will see **Add Program** on the top right of the landing page, as shown in the figure below.

![](assets/create-program-add.png)

## Erstellen eines Sandbox-Programms {#create-sandbox-program}

Gehen Sie wie folgt vor, um ein Sandbox-Programm zu erstellen:

1. Wählen Sie im Assistenten zum Erstellen von Programmen die Option **Sandbox** einrichten. Der Benutzer sendet den Programm-Namen, bevor er &quot; **Erstellen**&quot;auswählt.

   ![](assets/create-sandbox.png)

1. Der Benutzer sieht die neue Sandbox-Programm-Karte auf der Landingpage und kann den Mauszeiger darüber halten, um das Cloud Manager-Symbol auszuwählen, um zur Cloud Manager-Übersichtsseite zu navigieren. Die Karte informiert den Benutzer über den Status der automatischen Einrichtung des neu erstellten Sandbox-Programms. Der Benutzer sieht eine Progression.

   ![](assets/program-create-setupdemo2.png)

1. Nachdem das Programm eingerichtet und der Projekterstellungsschritt abgeschlossen ist, kann der Benutzer auf den Link Git **** verwalten zugreifen, wie in der folgenden Abbildung dargestellt:

   ![](assets/create-program4.png)

   >[!NOTE]
   >
   >Weitere Informationen zum Zugriff auf und zur Verwaltung des Git-Repositorys mithilfe der Self-Service-Git-Kontoverwaltung über die Cloud Manager-Benutzeroberfläche finden Sie unter [Zugriff auf Git](/help/implementing/cloud-manager/accessing-git.md).


1. Nachdem die Entwicklungs-Umgebung erstellt wurde, kann der Benutzer **auf AEM** Link zugreifen, wie in der folgenden Abbildung dargestellt:

   ![](assets/create-program-5.png)

1. Nach Abschluss der Bereitstellung für die Entwicklungspipeline für die Nicht-Produktion führt der Assistent den Benutzer zum Zugriff auf AEM (bei der Entwicklung) oder zum Bereitstellen von Code für die Umgebung der Entwicklung:

   ![](assets/create-program-setup-deploy.png)

   >[!NOTE]
   >Sie können ein Programm auch auf der Seite Übersicht über Cloud Manager bearbeiten, wechseln oder hinzufügen, wie unten dargestellt:

   ![](assets/create-program-a1.png)

## Deleting a Sandbox Program {#delete-sandbox-program}

A Sandbox Program user in *Business Owner* or *Deployment Manager* role in Cloud Manager can delete their Production and Stage environment set via the Cloud Manager UI.

>[!NOTE]
>Durch Auswahl der Löschoption für die Produktions- oder Staging-Umgebung wird die jeweils andere Umgebung im Satz auch gelöscht.

Die Option zum Löschen ist in der Landingpage verfügbar, wie unten dargestellt:

![](assets/delete-sandbox1.png)

Oder

Wählen Sie **Programm** löschen auf der Seite **Programm-Übersicht** , um Ihr Sandbox-Programm zu löschen.

![](assets/delete-sandbox2.png)


## Creating a Regular Program {#create-regular-program}

Ein *reguläres* Programm ist für Benutzer gedacht, die sich mit AEM und Cloud Manager auskennen und mit der Erstellung, dem Erstellen und dem Testen von Beginn-Code zur Bereitstellung in der Produktion vertraut sind.

Gehen Sie wie folgt vor, um ein reguläres Programm zu erstellen:

1. Wählen Sie im Assistenten &quot;Programm erstellen&quot;die Option &quot; **Zur Produktion** einrichten&quot;, um ein normales Programm zu erstellen. Der Benutzer kann den Standardnamen des Programms akzeptieren oder bearbeiten, bevor er &quot; **Weiter**&quot;auswählt.

   ![](assets/create-prod1.png)

1. Der Benutzer wählt die Lösungen aus, die in das Programm auf dem Bildschirm, der nach oben angezeigt wird, aufgenommen werden sollen.



   >[!NOTE]
   >
   >Der folgende Bildschirm wird nur für das Segment der Kunden angezeigt, die mehr als eine Lösung gekauft haben. Für Kunden, die nur eine Lösung gekauft haben, wird der Bildschirm zur Lösungsauswahl unten nicht angezeigt.

   ![](assets/set-up-prod2.png)

1. Once you have selected the solutions, click **Create**.

   ![](assets/set-up-prod3.png)

1. Sobald Sie Ihre Programm-Karte auf der Landingpage sehen, halten Sie den Mauszeiger darüber, um das Symbol Cloud Manager auszuwählen, um zur Seite &quot;Cloud Manager- **Übersicht** &quot;zu navigieren.

   ![](assets/set-up-prod4.png)

1. Die Hauptkarte für Aktionsaufrufe wird den Benutzer anleiten, eine Umgebung zu erstellen, eine Nicht-Produktions-Pipeline zu erstellen und schließlich eine Produktionspipeline zu erstellen.
   ![](assets/set-up-prod5.png)


   >[!NOTE]
   >
   >A regular program does not have **Auto-setup** feature.





