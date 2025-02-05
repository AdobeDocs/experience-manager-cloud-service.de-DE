---
title: Aufgaben von Entwickelnden und Bereitstellungs-Managern
description: Erfahren Sie, wie Entwicklende und Implementierungs-Manager auf Git zugreifen können, um Anwendungen zu entwickeln und Pipelines zur Bereitstellung zu verwenden, nachdem der Systemadministrator bzw. die Systemadministratorin die erforderlichen Cloud-Ressourcen eingerichtet hat.
feature: Onboarding
role: Admin, User, Developer
exl-id: f57a856b-0932-4e8f-be59-a19fe692e2ab
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '1397'
ht-degree: 94%

---


# Aufgaben von Entwickelnden und Bereitstellungs-Managern {#developer-deployment-manager}

In diesem optionalen Teil der [Onboarding-Journey](overview.md) erfahren Sie, wie Entwicklende und Bereitstellungs-Manager auf Git zugreifen können, um Anwendungen zu entwickeln und Pipelines zur Bereitstellung zu verwenden.

## Ihre bisherige Tour {#story-so-far}

Sie sind in Ihrer Onboarding-Tour weit gekommen! Herzlichen Glückwunsch! Der Systemadministrator bzw. die Systemadministratorin hat die Onboarding-Journey abgeschlossen, indem er/sie die erforderlichen Cloud-Ressourcen eingerichtet und Zugriff auf das Dokument [Zuweisen von AEM-Produktprofilen](assign-profiles-aem.md) gewährt hat.

Jetzt können Ihre Entwickelnden und Bereitstellungs-Manager mit der Erstellung eigener Anwendungen beginnen und Ihre AEM-Benutzenden mit der Erstellung von Inhalten. Ihr Onboarding ist jetzt abgeschlossen und Sie können Ihr neues AEM as a Cloud Service-System verwenden, das in diesem Dokument veranschaulicht wird.

## Zielgruppe {#audience}

Dieses Dokument wurde daher aus der Perspektive der **Entwickelnden** und **Bereitstellungs-Manager** geschrieben.

Der Systemadministrator bzw. die Systemadministratorin kann auch diese Aufgaben ausführen, doch diese Rollen haben normalerweise verschiedene Personen inne.

## Ziel {#objective}

Dieses Dokument dient als Ergänzung zur Onboarding-Tour und zeigt die grundlegenden Aufgaben eines Entwickelnden und Bereitstellungs-Managers, wenn der Systemadministrator bzw. die Systemadministratorin alle Benutzenden integriert und die erforderlichen Cloud-Ressourcen erstellt hat.

Nach dem Lesen dieses Dokuments sollten Sie Folgendes können:

* Entwickelnde müssen wissen, wie Sie auf Ihre Cloud Manager-Git-Repositorys zugreifen und diese verwalten können.
* Implementierungs-Manager müssen verstehen, wie sie Pipelines einrichten und Ihren Code in Cloud Manager bereitstellen können.

## Entwickelnde und Bereitstellungs-Manager {#roles}

Nachdem der Systemadministrator bzw. die Systemadministratorin die wichtigsten Onboarding-Aufgaben für die Erstellung von Benutzenden und die Einrichtung von Cloud-Ressourcen abgeschlossen hat, sind die Entwickelnden und Bereitstellungs-Manager normalerweise die Nächsten, die Zugriff auf das System benötigen. Dies liegt daran, dass sie dafür verantwortlich sind, Ihre benutzerdefinierten Programme auf AEM as a Cloud Service zu erstellen.

* **Entwickelnde**: Diese Benutzenden greifen auf die Cloud Manager-Git-Repositorys zu, wo sie den Code für Ihre benutzerdefinierten AEM-Anwendungen verwalten.
* **Bereitstellungs-Manager**: Diese Benutzenden verwenden Cloud Manager zum Erstellen und Ausführen von Pipelines, über die der Code aus den Git-Repositorys an Ihre aktiven AEM-Umgebungen übermittelt wird.

Je nach den betrieblichen Anforderungen können Benutzende beide Rollen haben.

## Voraussetzungen {#prerequisites}

Bevor Sie mit den in diesem Dokument beschriebenen Aufgaben als Entwickelnde oder Bereitstellungs-Manager beginnen, stellen Sie sicher, dass Ihr Systemadministrator bzw. Ihre Systemadministratorin alle in dieser Tour beschriebenen Schritte ausgeführt hat. Das heißt:

* Ihr Systemadministrator bzw. Ihre Systemadministratorin hat die Entwickelnden und Bereitstellungs-Manager ihren jeweiligen Produktprofilen zugewiesen.
* Entwicklungspersonen müssen zusätzlich den Produktprofilen **AEM-Benutzer** oder **AEM-Admins** zugewiesen werden, um AEM ebenfalls verwenden zu können.
* Cloud-Ressourcen wurden eingerichtet.

## Zugriff auf Git {#accessing-git}

Sie können über die Benutzeroberfläche von Cloud Manager über die Self-Service-Git-Kontoverwaltung auf Ihr Git-Repository zugreifen und es verwalten.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie in der **Programmübersicht** zur Karte **Pipelines** und verwenden Sie die Schaltfläche **Zugriff auf Repo Info**, um auf Ihr Git-Repository zuzugreifen und es zu verwalten.

   ![Schaltfläche „Zugriff auf Repo Info“ auf der Karte „Umgebungen“](/help/implementing/cloud-manager/assets/repos/access-repo1.png)

1. Klicken Sie auf die Schaltfläche **Repo-Info anzeigen**, um ein Dialogfeld mit folgenden Inhalten zu öffnen:

   * Die URL zum Git-Repository von Cloud Manager.
   * Der Git-Benutzername.
   * Das Git-Kennwort, dessen Wert durch Klicken auf die Schaltfläche **Kennwort generieren** angezeigt wird.

   ![Repository-Informationen](/help/implementing/cloud-manager/assets/repos/access-repo-create.png)

Mithilfe dieser Anmeldeinformationen können Benutzende eine lokale Kopie des Repositorys klonen und Änderungen an diesem lokalen Repository vornehmen und etwaige Code-Änderungen wieder in das remote Code-Repository in Cloud Manager übertragen.

## Einrichten der Pipeline {#setup-pipeline}

Nachdem Entwickelnde ihren benutzerdefinierten Code zu Ihren Git-Repositorys hinzugefügt haben, kann der Bereitstellungs-Manager Pipelines erstellen und ausführen, um diesen Code in Ihren AEM-Umgebungen bereitzustellen.

Führen Sie diese Schritte aus, um Ihre erste produktionsfremde Bereitstellungs-Pipeline zu erstellen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Rufen Sie die Karte **Pipelines** über den Startbildschirm von Cloud Manager auf. Klicken Sie auf **+Hinzufügen** und wählen Sie **Produktionsfremde Pipeline hinzufügen** aus.

   ![Produktionsfremde Pipeline hinzufügen](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add1.png)

1. Wählen Sie im Dialogfeld **Hinzufügen einer produktionsfremden Pipeline** auf der Registerkarte **Konfiguration** den Typ der produktionsfremden Pipeline aus, die Sie hinzufügen möchten. Wählen Sie für dieses Beispiel **Bereitstellungs-Pipeline** aus.

   ![Dialogfeld „Produktionsfremde Pipeline hinzufügen“](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-config.png)

1. Geben Sie einen **Namen für die produktionsfremde Pipeline** an, um Ihre Pipeline zu identifizieren, sowie die folgenden zusätzlichen Informationen.

1. Wählen Sie für **Bereitstellungsauslöser** die Option **Manuell** aus, damit die Pipeline nur ausgeführt wird, wenn Sie sie starten.

1. Klicken Sie auf **Weiter**.

1. Wählen Sie im Dialogfeld **Produktionsfremde Pipeline hinzufügen** auf der Registerkarte **Quell-Code** aus, welche Art von Code die Pipeline verarbeiten soll. Wählen Sie für dieses Beispiel **Vollständiger Stack-Code** aus.

1. Definieren Sie in der Registerkarte **Quell-Code** die folgenden Optionen.

   * **Mögliche Bereitstellungsumgebungen**: Sie müssen auswählen, in welche Umgebung die Pipeline den Code liefern soll.
   * **Repository**: Diese Option definiert, aus welchem Git-Repository die Pipeline den Code abrufen soll.
   * **Git-Verzweigung**: Mit dieser Option wird festgelegt, von welchem Zweig in der ausgewählten Pipeline der Code abgerufen werden soll.
      * Geben Sie die ersten Zeichen des Verzweigungsnamens ein und die Funktion zum automatischen Vervollständigen dieses Feldes findet die entsprechenden Verzweigungen, um Ihnen bei der Auswahl zu helfen.

   ![Full-Stack-Pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-full-stack.png)

1. Klicken Sie auf **Speichern**.

Sie haben jetzt Ihre erste Pipeline erstellt! Benutzende mit der Rolle „Bereitstellungs-Manager“ können die Pipeline jetzt über die Cloud Manager-Benutzeroberfläche starten.

## Bereitstellen {#deploy}

Nachdem Entwickler bzw. Entwicklerinnen ihren benutzerdefinierten Code zu den Git-Repositorys hinzugefügt haben und Sie eine Pipeline erstellt haben, um diesen Code bereitzustellen, ist es an der Zeit, die Pipeline auszuführen, um diesen Code tatsächlich aus Git in Ihre Umgebung zu verschieben.

![Karte „Pipelines“ in Cloud Manager](/help/implementing/cloud-manager/assets/configure-pipeline/pipelines-card.png)

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie zur Karte **Pipelines** in der **Programmübersicht**, klicken Sie auf die Schaltfläche mit den Auslassungspunkten neben der Pipeline, die Sie im vorherigen Abschnitt erstellt haben, und wählen Sie im Menü **Ausführen** aus.

1. Der Pipeline-Ausführung beginnt. Dies wird in der Spalte **Status** angezeigt.

Sie können die Details der Ausführung sehen, indem Sie erneut auf die Schaltfläche mit den Auslassungspunkten klicken und **Details anzeigen** auswählen.

Herzlichen Glückwunsch! Sie haben jetzt Code aus Ihrem Git-Repository in einer Nicht-Produktionsumgebung bereitgestellt!

## Wie geht es weiter {#whats-next}

Nachdem Sie dieses Dokument gelesen haben, wissen Sie Folgendes:

* Entwickelnde müssen wissen, wie Sie auf Ihre Cloud Manager-Git-Repositorys zugreifen und diese verwalten können.
* Implementierungs-Manager müssen verstehen, wie sie Pipelines einrichten und Ihren Code in Cloud Manager bereitstellen können.

Sie haben als Entwickler bzw. Entwicklerin oder Bereitstellungs-Manager nicht nur Kenntnisse über Cloud Manager, sondern auch über Arbeitsumgebungen, Repositorys und Pipelines erhalten! Aber es gibt noch mehr über die leistungsstarken CI/CD-Tools von AEM as a Cloud Service zu erfahren. Weitere Details finden Sie im Abschnitt [Zusätzliche Ressourcen](#additional-resources).

Wenn Sie wissen möchten, wie Inhaltsautoren und -autorinnen auf AEM as a Cloud Service zugreifen und die entsprechenden Funktionen verwenden können, fahren Sie mit dem letzten Teil der Onboarding-Journey fort: [AEM-Benutzeraufgaben](aem-users.md).

>[!TIP]
>
>Da Sie nun über das nötige Wissen verfügen, können Sie [lernen, wie Sie das AEM-Referenzdemo-Add-on](/help/journey-sites/demos-add-on/overview.md) einfach einer Sandbox-Umgebung mit minimaler AEM-Konfiguration hinzufügen können und die leistungsstarken Funktionen von AEM mit umfangreichen Beispielen auf der Grundlage von Best Practices testen können.

## Zusätzliche Ressourcen {#additional-resources}

Im Folgenden finden Sie zusätzliche optionale Ressourcen, wenn Sie über den Inhalt der Onboarding-Tour hinausgehen möchten.

* [Zugreifen auf Repositorys](/help/implementing/cloud-manager/managing-code/accessing-repos.md) - Erfahren Sie, wie Sie mithilfe der Self-Service-Git-Kontoverwaltung über Cloud Manager auf Ihr Git-Repository zugreifen und es verwalten können.
* [Verwenden von Git mit Cloud Manager](/help/implementing/cloud-manager/managing-code/integrating-with-git.md) - Erfahren Sie, wie Sie die Git-Repositorys von Cloud Manager verwenden und Ihr eigenes On-Premise verwaltetes Git-Repository mit Cloud Manager integrieren.
* [Einrichten einer lokalen Entwicklungsumgebung](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html?lang=de) - Dieses Tutorial zeigt Ihnen, wie Sie mit dem AEM as a Cloud Service SDK eine lokale Entwicklungsumgebung für Adobe Experience Manager (AEM) einrichten.
* [Erste Schritte mit AEM Sites - WKND-Tutorial](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=de) - Dieses mehrteilige Tutorial wurde für Entwickler und Entwicklerinnen konzipiert, die neu in Adobe Experience Manager (AEM) sind. Dieses mehrteilige Tutorial führt durch die Implementierung einer AEM-Site für eine fiktive Lifestyle-Marke namens WKND. Das Tutorial geht auf grundlegende Themen wie Projekteinrichtung, Kernkomponenten, bearbeitbare Vorlagen, Client-Bibliotheken und Komponentenentwicklung mit Adobe Experience Manager Sites ein.
* [Erste Schritte mit SPAs in AEM mit React](/help/implementing/developing/hybrid/getting-started-react.md): Dieser Artikel beschreibt eine Beispiel-SPA und erläutert, wie sie eingerichtet wird. Außerdem ermöglicht er Ihnen, unter Verwendung des React-Frameworks rasch Ihre eigene SPA zu verwenden.
* [Erste Schritte mit SPAs in AEM mit Angular](/help/implementing/developing/hybrid/getting-started-angular.md): Dieser Artikel beschreibt eine Beispiel-SPA und erläutert, wie sie eingerichtet wird. Außerdem ermöglicht er Ihnen, unter Verwendung des Angular-Frameworks rasch Ihre eigene SPA zu verwenden.
* [Headless-Entwickler-Tour](/help/journey-headless/developer/overview.md): Beginnen Sie hier mit einem Kurs für die Entwicklung von Headless-Anwendungen mit AEM.
