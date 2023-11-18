---
title: Erstellen eines Programms
description: Erfahren Sie, wie Sie ein neues Programm und eine neue Pipeline einrichten, um das Add-on bereitzustellen.
exl-id: 06287618-0328-40b1-bba8-84002283f23f
source-git-commit: bc3c054e781789aa2a2b94f77b0616caec15e2ff
workflow-type: tm+mt
source-wordcount: '696'
ht-degree: 39%

---


# Erstellen eines Programms {#creating-a-program}

Erfahren Sie, wie Sie ein neues Programm und eine neue Pipeline einrichten, um das Add-on bereitzustellen.

## Die bisherige Entwicklung {#story-so-far}

Im vorherigen Dokument der Adobe Experience Manager (AEM) Referenz-Demos-Add-on-Journey, [Grundlegendes zur Installation des Referenz-Demo-Add-ons,](installation.md) Sie haben gelernt, wie der Installationsprozess des Referenz-Demos-Add-ons funktioniert und gezeigt, wie die verschiedenen Teile zusammenarbeiten. Sie sollten jetzt folgende Punkte erfüllen:

* Sollten Sie über grundlegende Kenntnisse zu Cloud Manager verfügen.
* Wissen Sie, wie Pipelines Inhalte und Konfigurationen für AEM bereitstellen.
* Sehen, wie mit Vorlagen in nur wenigen Klicks neue Sites erstellt werden können, die mit Demo-Inhalten gefüllt sind.

Dieser Artikel baut auf diesen Grundlagen auf und führt den ersten Konfigurationsschritt durch, um ein Programm für Testzwecke zu erstellen. Dabei wird eine Pipeline zum Bereitstellen des Add-on-Inhalts verwendet.

## Ziel {#objective}

In diesem Dokument erfahren Sie, wie Sie ein neues Programm und eine neue Pipeline einrichten, um das Add-on bereitzustellen. Nach dem Lesen sollten Sie Folgendes tun können:

* Machen Sie sich mit der Verwendung von Cloud Manager zur Erstellung eines Programms vertraut und erläutern Sie sie.
* Aktivieren Sie das Referenz-Demos-Add-on für das neue Programm.
* Führen Sie eine Pipeline aus, um den Add-On-Inhalt bereitzustellen.

## Erstellen eines Programms {#create-program}

Nach der Anmeldung bei Cloud Manager können Sie ein Sandbox-Programm für Ihre Test- und Demozwecke erstellen.

>[!NOTE]
>
>Ihre Benutzerin bzw. Ihr Benutzer muss in Cloud Manager in Ihrem Unternehmen die Rolle **Geschäftsinhaber** innehaben, um Programme zu erstellen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Adobe Cloud Manager an.

1. Stellen Sie nach der Anmeldung sicher, dass Sie sich in der richtigen Organisation befinden, indem Sie diese in der oberen rechten Ecke des Bildschirms prüfen. Wenn Sie nur Mitglied einer Organisation sind, ist dieser Schritt nicht erforderlich.

   ![Übersicht über Cloud Manager](assets/cloud-manager.png)

1. Auswählen **Programm hinzufügen** oben rechts im Fenster.

1. Im **Erstellen wir Ihr Programm** dialog:

   1. Geben Sie einen **Programmnamen** zur Beschreibung Ihres Programms an.
   1. Auswählen **Sandbox einrichten** für Ihre **Programmziel**
   1. Klicken Sie auf **Weiter**.

   ![Dialogfeld „Programm erstellen“](assets/create-program.png)

1. Im **Sandbox einrichten** im Dialogfeld **Lösungen und Add-ons** -Tabelle, erweitern Sie die **Sites** durch Tippen oder Klicken auf einen Eintrag in der Liste und dann **Referenz-Demos**.

   * Wenn Sie auch Demos für AEM Screens erstellen möchten, überprüfen Sie die **Screens** in der Liste. Auswählen **Aktualisieren**.

   ![Auswählen des Add-ons für eine Referenzdemo bei der Programmeinrichtung](assets/select-reference-demo-add-on.png)


1. Auswählen **Erstellen** und Cloud Manager beginnt mit der Einrichtung Ihres Sandbox-Programms. Sie gelangen zum Bildschirm mit der Programmübersicht. Eine kurze Bannerbenachrichtigung zeigt an, dass der Prozess gestartet wurde. Auf der Übersichtsseite für Ihr neues Programm wurde eine Karte hinzugefügt. Der Einrichtungsprozess dauert einige Minuten.

1. Sobald die Einrichtung abgeschlossen ist, zeigt die Karte für die Umgebung auf der Übersichtsseite ihren Status als **Bereit**. Wählen Sie die Karte aus, damit Sie die Umgebung öffnen können.

   ![Erstellung des Programms abgeschlossen](assets/ready.png)

1. Ihre Umgebung ist bereit und das Add-on ist jetzt als Option aktiviert, aber die Inhalte der Demo müssen in bereitgestellt AEM werden, damit sie verfügbar sind. Wählen Sie dazu die Suchschaltfläche neben der Pipeline In der **Pipelines** Karte und wählen Sie **Ausführen**.

   ![Starten](assets/run.png)

1. Die Pipeline wird gestartet und Sie gelangen zu einer Seite, auf der der Fortschritt der Bereitstellung detailliert beschrieben wird. Sie können von diesem Bildschirm weg navigieren, während das Programm erstellt wird, und bei Bedarf später zurückkehren.

   ![Bereitstellung](assets/deployment.png)

Die Fertigstellung der Pipeline kann mehrere Minuten dauern. Nach Abschluss sind das Add-on und die zugehörigen Demoinhalte für die Verwendung in der AEM Authoring-Umgebung verfügbar.

## Wie geht es weiter {#what-is-next}

Nachdem Sie nun diesen Teil der Tour durch das AEM-Referenzdemo-Add-on abgeschlossen haben, sollten Sie:

* Erfahren Sie, wie Sie mit Cloud Manager ein Programm erstellen.
* Erfahren Sie, wie Sie das Referenz-Demos-Add-on für das Programm aktivieren.
* Sie können eine Pipeline ausführen, damit Sie den Add-On-Inhalt bereitstellen können.

Auf diesem Wissen aufbauen und Ihre AEM Referenz-Demo-Add-on-Journey fortsetzen, bevor Sie die [Erstellen einer Demosite](create-site.md). Hier erfahren Sie, wie Sie in AEM eine Demosite erstellen, die auf einer Bibliothek vorkonfigurierter Vorlagen basiert, die von der Pipeline bereitgestellt wurden.

## Zusätzliche Ressourcen {#additional-resources}

* [Dokumentation zu Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/onboarding-concepts/cloud-manager-introduction.html?lang=de) – Wenn Sie an weiteren Details zu den Funktionen von Cloud Manager interessiert sind, sehen Sie sich die ausführlichen technischen Dokumente an.
