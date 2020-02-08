---
title: Erstellen eines Programms - Cloud-Dienst
description: Erstellen eines Programms - Cloud-Dienst
translation-type: tm+mt
source-git-commit: 57206e36725e28051b2468d47da726e318bd763b

---


# Erstellen eines Programms {#create-a-program}

Die Cloud-native Lösung bietet dem Benutzer die erforderlichen Berechtigungen und die Möglichkeit, ein Programm auf einem Selbstbedienungsmodell zu erstellen.

Ein Programmerstellungsassistent fordert den Benutzer auf, Details zu übermitteln, je nachdem, welches Ziel der Benutzer beim Erstellen des Programms innerhalb der Grenzen dessen verfolgt wird, was dem jeweiligen Kunden oder Unternehmen zur Verfügung steht.

Beim erstmaligen Zugriff auf Cloud Manager oder wenn keine Programme im Mieter vorhanden sind, wird dem Benutzer der Bildschirm **Erstellen des ersten Programms** angezeigt. Wenn der Benutzer *Esc* auswählt oder außerhalb des Dialogfelds klickt, wird der folgende Bildschirm angezeigt:

![](assets/create-program1.png)


## Verwenden des Programmassistenten {#using-create-program-wizard}

Je nachdem, welches Ziel der Benutzer beim Erstellen des Programms innerhalb der Grenzen dessen verfolgt, was dem jeweiligen Kunden/Unternehmen zur Verfügung steht, fordert ein Programmerstellungsassistent den Benutzer auf, eine oder mehrere Details zu übermitteln.

![](assets/create-program-2.png)

>[!NOTE]
>Wenn bereits ein Programm vorhanden ist, sehen Sie oben rechts auf der Einstiegsseite das **Programm** hinzufügen, wie in der folgenden Abbildung dargestellt.

![](assets/create-program-add.png)

## Demoprogramm erstellen {#create-demo-program}

>[!NOTE]
>
Ein Demoprogramm entspricht einem Sandbox-Programm in der Benutzeroberfläche von Cloud Manager.

Gehen Sie wie folgt vor, um ein Sandbox-Programm zu erstellen:

1. Wählen Sie im Assistenten zum Erstellen des Programms die Option **Demo** einrichten. Der Benutzer sendet den Programmnamen, bevor er &quot; **Erstellen**&quot;auswählt.

   ![](assets/create-program-setupdemo.png)

1. Benutzer sehen die neue Sandbox-Programmkarte auf der Einstiegsseite und können mit dem Mauszeiger darauf zeigen, um das Cloud Manager-Symbol auszuwählen, um zur Übersichtsseite von Cloud Manager zu navigieren. Die Karte informiert den Benutzer über den Status der automatischen Einrichtung des neu erstellten Sandbox-Programms. Der Benutzer sieht eine Progression.

   ![](assets/program-create-setupdemo2.png)

1. Nachdem das Programm eingerichtet und der Projekterstellungsschritt abgeschlossen ist, kann der Benutzer auf den Link Git **** verwalten zugreifen, wie in der folgenden Abbildung gezeigt:

   ![](assets/create-program4.png)

   >[!NOTE]
   >
   >Weitere Informationen zum Zugriff auf und zur Verwaltung des Git-Repositorys mithilfe der Self-Service-Git-Kontoverwaltung über die Cloud Manager-Benutzeroberfläche finden Sie unter [Zugriff auf Git](/help/implementing/cloud-manager/accessing-git.md).


1. Nachdem die Entwicklungsumgebung erstellt wurde, kann der Benutzer **auf AEM** -Link zugreifen, wie in der folgenden Abbildung gezeigt:

   ![](assets/create-program-5.png)

1. Nach Abschluss der Bereitstellung für die Entwicklungsumgebung für die Nicht-Produktion leitet der Assistent den Benutzer zum Zugriff auf AEM (in der Entwicklung) oder zum Bereitstellen von Code in der Entwicklungsumgebung:

   ![](assets/create-program-setup-deploy.png)


## Erstellen eines regulären Programms {#create-regular-program}

Ein *reguläres* Programm ist für Benutzer gedacht, die mit AEM und Cloud Manager vertraut sind und damit beginnen können, Code zu schreiben, zu erstellen und zu testen, um ihn in der Produktion bereitzustellen.

Gehen Sie wie folgt vor, um ein reguläres Programm zu erstellen:

1. Wählen Sie im Assistenten &quot;Programm erstellen&quot;die Option &quot; **Zur Produktion** einrichten&quot;, um ein normales Programm zu erstellen. Der Benutzer kann den Standardprogrammnamen akzeptieren oder bearbeiten, bevor er **Weiter** auswählt.

   ![](assets/set-up-prod1.png)

1. Der Benutzer wählt Lösungen aus, die in das Programm in den Bildschirm aufgenommen werden sollen, der nach dem Bildschirm oben angezeigt wird.



   >[!NOTE]
   >
   >Der folgende Bildschirm wird nur für das Segment der Kunden angezeigt, die mehr als eine Lösung gekauft haben. Für Kunden, die nur eine Lösung gekauft haben, wird der Bildschirm zur Lösungsauswahl unten nicht angezeigt.

   ![](assets/set-up-prod2.png)

1. Once you have selected the solutions, click **Create**.

   ![](assets/set-up-prod3.png)

1. Sobald Sie Ihre Programmkarte auf der Einstiegsseite sehen, halten Sie den Mauszeiger darüber, um das Symbol Cloud Manager auszuwählen, um zur Seite &quot;Cloud Manager- **Übersicht** &quot;zu navigieren.

   ![](assets/set-up-prod4.png)

1. Die Hauptkarte für Aktionsaufrufe führt den Benutzer dazu, eine Umgebung zu erstellen, eine Nicht-Produktionspipeline zu erstellen und schließlich eine Produktionspipeline zu erstellen.
   ![](assets/set-up-prod5.png)


   >[!NOTE]
   >
   >Ein reguläres Programm verfügt nicht über eine **automatische Setup** -Funktion.





