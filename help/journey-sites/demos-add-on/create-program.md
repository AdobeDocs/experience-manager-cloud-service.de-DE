---
title: Programm erstellen
description: Erfahren Sie, wie Sie ein neues Programm und eine neue Pipeline einrichten, um das Add-on bereitzustellen.
source-git-commit: 52d65251744ce0ae5cf7a7e0a45b39d8fe78f13a
workflow-type: tm+mt
source-wordcount: '696'
ht-degree: 3%

---


# Programm erstellen {#creating-a-program}

Erfahren Sie, wie Sie ein neues Programm und eine neue Pipeline einrichten, um das Add-on bereitzustellen.

## Die bisherige Entwicklung {#story-so-far}

Im vorherigen Dokument der AEM Schnellsite-Journey [Grundlegendes zur Installation des Referenz-Demo-Add-ons,](installation.md) Sie haben gelernt, wie der Installationsprozess des Referenz-Demos-Add-ons funktioniert, und haben gezeigt, wie die verschiedenen Teile zusammenarbeiten. Sie sollten jetzt:

* Sie verfügen über grundlegende Kenntnisse zu Cloud Manager.
* Erfahren Sie, wie Pipelines Inhalte und Konfigurationen für AEM bereitstellen.
* Erfahren Sie, wie mit Vorlagen neue Sites erstellt werden können, die mit Demoinhalten vorbelegt sind, aber nur wenige Klicks erfordern.

Dieser Artikel baut auf diesen Grundlagen auf und führt den ersten Konfigurationsschritt durch, um ein Programm für Testzwecke zu erstellen, und verwendet eine Pipeline zum Bereitstellen des Add-On-Inhalts.

## Ziel {#objective}

In diesem Dokument erfahren Sie, wie Sie ein neues Programm und eine neue Pipeline einrichten, um das Add-on bereitzustellen. Nach dem Lesen sollten Sie:

* Erfahren Sie, wie Sie mit Cloud Manager ein neues Programm erstellen können.
* Erfahren Sie, wie Sie das Referenz-Demos-Add-On für das neue Programm aktivieren.
* Sie können eine Pipeline zum Bereitstellen des Add-On-Inhalts ausführen.

## Programm erstellen {#create-program}

Nach der Anmeldung bei Cloud Manager können Sie ein neues Sandbox-Programm für Ihre Test- und Demozwecke erstellen.

>[!NOTE]
>
>Ihr Benutzer muss Mitglied der **Business Owner** Rolle in Cloud Manager in Ihrem Unternehmen verwenden, um Programme zu erstellen.

1. Melden Sie sich bei Adobe Cloud Manager an unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/).

1. Stellen Sie nach der Anmeldung sicher, dass Sie sich in der richtigen Organisation befinden, indem Sie sie in der oberen rechten Ecke des Bildschirms überprüfen. Wenn Sie nur Mitglied einer Organisation sind, ist dieser Schritt nicht erforderlich.

   ![Übersicht über Cloud Manager](assets/cloud-manager.png)

1. Tippen oder klicken Sie auf **Programm hinzufügen** oben rechts im Fenster.

1. Im **Erstellen wir Ihr Programm** Dialogfeld, stellen Sie sicher, dass **Adobe Experience Manager** ausgewählt unter **Produkte** und tippen oder klicken Sie dann auf **Weiter**.

   ![Dialogfeld &quot;Programm erstellen&quot;](assets/create-program.png)

1. Im nächsten Dialogfeld:

   * Bereitstellung einer **Programmname** zur Beschreibung Ihres Programms.
   * Tippen oder klicken Sie auf **Sandbox einrichten** für Ihre **Programmziel**

   Tippen oder klicken Sie dann auf **Erstellen**.

   ![Programmname](assets/program-name.png)

1. Sie gelangen in den Bildschirm mit der Programmübersicht, wo Sie den Prozess der Programmerstellung beobachten können. Cloud Manager bietet eine Schätzung der verbleibenden Zeit. Sie können von diesem Bildschirm weg navigieren, während das Programm erstellt wird, und bei Bedarf später zurückkehren.

   ![Programmerstellung](assets/program-creation.png)

1. Nach Abschluss des Vorgangs bietet Cloud Manager eine Übersicht mit den automatisch erstellten Umgebungen und Pipelines.

   ![Erstellung des Programms abgeschlossen](assets/creation-complete.png)

1. Bearbeiten Sie die Programmdetails, indem Sie auf den Programmnamen oben links auf der Seite klicken und im Dropdown-Menü die Option **Programm bearbeiten**.

   ![Programm bearbeiten](assets/edit-program.png)

1. Im **Programm bearbeiten** Dialogfeld, wechseln Sie zu **Lösungen und Add-ons** Registerkarte.

   ![Dialogfeld &quot;Programm bearbeiten&quot;](assets/edit-program-dialog.png)

1. Im **Lösungen und Add-ons** Registerkarte, erweitern Sie die **Sites** in die Liste ein und überprüfen Sie dann **Referenz-Demos**. Tippen oder klicken Sie auf **Aktualisieren**.

   ![Option &quot;Referenz-Demos&quot;aktivieren](assets/edit-program-add-on.png)

1. Das Add-on ist jetzt als Option aktiviert, seine Inhalte müssen jedoch in bereitgestellt AEM werden, damit sie verfügbar sind. Tippen oder klicken Sie auf der Programmübersichtsseite auf **Starten** , um die Pipeline zu starten und den Add-On-Inhalt für AEM bereitzustellen.

   ![Anfang](assets/deploy.png)

1. Die Pipeline wird gestartet und Sie gelangen zu einer Seite, auf der der Fortschritt der Bereitstellung detailliert beschrieben wird. Sie können von diesem Bildschirm weg navigieren, während das Programm erstellt wird, und bei Bedarf später zurückkehren.

   ![Bereitstellung](assets/deployment.png)

Sobald die Pipeline abgeschlossen ist, sind das Add-on und der zugehörige Demoinhalt für die Verwendung in der AEM Authoring-Umgebung verfügbar.

## Wie geht es weiter {#what-is-next}

Nachdem Sie diesen Teil der AEM Referenz-Demo-Add-On-Journey abgeschlossen haben, sollten Sie Folgendes tun:

* Erfahren Sie, wie Sie mit Cloud Manager ein neues Programm erstellen können.
* Erfahren Sie, wie Sie das Referenz-Demos-Add-On für das neue Programm aktivieren.
* Sie können eine Pipeline zum Bereitstellen des Add-On-Inhalts ausführen.

Auf diesem Wissen aufbauen und mit der Journey des AEM Referenz-Demo-Add-ons fortfahren, indem Sie das Dokument erneut überprüfen [Erstellen einer Demosite,](create-site.md) Hier erfahren Sie, wie Sie eine Demosite in AEM basierend auf einer Bibliothek vorkonfigurierter Vorlagen erstellen, die von der Pipeline bereitgestellt wurden.

## Zusätzliche Ressourcen {#additional-resources}

* [Dokumentation zu Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/cloud-manager-introduction.html) - Wenn Sie weitere Details zu den Funktionen von Cloud Manager wünschen, sollten Sie sich die ausführlichen technischen Dokumente direkt ansehen.
