---
title: Erstellen eines Programms - Cloud-Dienst
description: Erstellen eines Programms - Cloud-Dienst
translation-type: tm+mt
source-git-commit: b2549ac13f996449bc41ac18ba6afbf22e116597
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 0%

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


1. Nachdem die Entwicklungs-Umgebung erstellt wurde, kann der Benutzer **auf AEM** -Link zugreifen, wie in der folgenden Abbildung dargestellt:

   ![](assets/create-program-5.png)

1. Nach Abschluss der Bereitstellung für die Entwicklungspipeline für die Nicht-Produktion führt der Assistent den Benutzer dazu, entweder auf AEM (in der Entwicklungsphase) zuzugreifen oder Code für die Entwicklungs-Umgebung bereitzustellen:

   ![](assets/create-program-setup-deploy.png)

   >[!NOTE]
   >Sie können ein Programm auch auf der Seite Übersicht über Cloud Manager bearbeiten, wechseln oder hinzufügen, wie unten dargestellt:

   ![](assets/create-program-a1.png)

## Löschen eines Sandbox-Programms {#delete-sandbox-program}

Sandbox-Programm-Benutzer in *Business Owner* oder *Deployment Manager* -Rolle in Cloud Manager können ihre Produktions- und Stage-Umgebung löschen, die über die Benutzeroberfläche von Cloud Manager festgelegt wurde.

Die Löschoption ist sowohl auf der Seite &quot;Umgebung&quot;auf der Seite &quot; *Übersicht* &quot;als auch auf der Seite &quot; **Umgebung** &quot;verfügbar. Wenn Sie die Option zum Löschen entweder auf der Produktions- oder der Stufe auswählen, wird auch die andere Option im Satz gelöscht.

## Erstellen eines regulären Programms {#create-regular-program}

Ein *reguläres* Programm ist für Benutzer gedacht, die mit AEM und Cloud Manager vertraut sind und Beginn zum Schreiben, Erstellen und Testen von Code mit dem Ziel der Bereitstellung für die Produktion bereitstellen können.

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





