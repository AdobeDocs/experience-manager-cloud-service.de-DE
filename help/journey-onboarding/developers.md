---
title: Aufgaben für Entwickler und Bereitstellungs-Manager
description: Sobald der Systemadministrator die erforderlichen Cloud-Ressourcen eingerichtet hat, erfahren Sie, wie Entwickler und Bereitstellungsmanager auf Git zugreifen können, um Anwendungen zu entwickeln und Pipelines zur Bereitstellung zu verwenden.
feature: Onboarding
role: Admin, User, Developer
exl-id: f57a856b-0932-4e8f-be59-a19fe692e2ab
source-git-commit: 709a80683357b0d56280ff14aa5f4ba6bf2c6b23
workflow-type: tm+mt
source-wordcount: '1400'
ht-degree: 19%

---


# Aufgaben für Entwickler und Bereitstellungs-Manager {#developer-deployment-manager}

In diesem optionalen Teil des [Onboarding-Journey,](overview.md) Hier erfahren Sie, wie Entwickler und Bereitstellungsmanager auf Git zugreifen können, um Anwendungen zu entwickeln und Pipelines zur Bereitstellung zu verwenden.

## Die bisherige Entwicklung {#story-so-far}

Sie sind in Ihrer Onboarding-Journey weit gekommen! Herzlichen Glückwunsch! Der Systemadministrator hat die Onboarding-Journey abgeschlossen, indem er die erforderlichen Cloud-Ressourcen eingerichtet und Zugriff auf das Dokument gewährt hat [Zuweisen AEM Produktprofilen.](assign-profiles-aem.md)

An dieser Stelle können Ihre Entwickler und Bereitstellungsmanager mit der Erstellung eigener Anwendungen beginnen, während Ihre AEM mit der Erstellung von Inhalten beginnen können. In diesem Sinne ist Ihr Onboarding abgeschlossen und jetzt ist es an der Zeit, Ihr neues AEM as a Cloud Service System zu verwenden, das dieses Dokument veranschaulichen wird.

## Zielgruppe {#audience}

Dieses Dokument wird daher aus der Perspektive der **Entwickler** und **Bereitstellungsmanager**.

Der Systemadministrator kann auch diese Aufgaben ausführen, aber diese Rollen werden im Allgemeinen von verschiedenen Benutzern verwaltet.

## Ziel {#objective}

Dieses Dokument ergänzt die Onboarding-Journey, um die grundlegenden Aufgaben eines Entwicklers und Bereitstellungsmanagers zu demonstrieren, sobald der Systemadministrator alle Benutzer integriert und die erforderlichen Cloud-Ressourcen erstellt hat.

Nach Lesen dieses Dokuments sollten Sie Folgendes können:

* Entwickler müssen wissen, wie Sie auf Ihre Cloud Manager-Git-Repositorys zugreifen und diese verwalten können.
* Als Bereitstellungsmanager können Sie Pipelines einrichten und Ihren Code in Cloud Manager bereitstellen.

## Entwickler und Bereitstellungsmanager {#roles}

Sobald der Systemadministrator die wichtigsten Onboarding-Aufgaben für die Erstellung von Benutzern und die Einrichtung von Cloud-Ressourcen abgeschlossen hat, sind die Entwickler und Bereitstellungsmanager für den Zugriff auf das System in der Regel am stärksten interessiert. Dies liegt daran, dass sie die Benutzer sind, die dafür verantwortlich sind, Ihre benutzerdefinierten Programme auf AEM as a Cloud Service zu erstellen.

* **Entwickler** - Diese Benutzer greifen auf die Cloud Manager-Git-Repositorys zu, in denen sie den Code für Ihre AEM benutzerdefinierten Anwendungen verwalten.
* **Bereitstellungsmanager** - Diese Benutzer verwenden Cloud Manager zum Erstellen und Ausführen von Pipelines, die den Code aus den Git-Repositorys in Ihren laufenden AEM bereitstellen.

Je nach Ihren organisatorischen Anforderungen können dieselben Benutzer beide Rollen haben.

## Voraussetzungen {#prerequisites}

Bevor Sie mit den in diesem Dokument beschriebenen Aufgaben als Entwickler oder Bereitstellungsmanager beginnen, stellen Sie sicher, dass Ihr Systemadministrator alle in dieser Journey beschriebenen Schritte ausgeführt hat. Das heißt:

* Ihr Systemadministrator hat Entwickler und Bereitstellungsmanager ihren jeweiligen Produktprofilen zugewiesen.
* Entwickler müssen zusätzlich zu **AEM** oder **AEM Administratoren** Produktprofile , um auch AEM zu verwenden.
* Cloud-Ressourcen wurden eingerichtet.

## Zugriff auf Git {#accessing-git}

Sie können über Cloud Manager über die Self-Service-Git-Kontoverwaltung auf Ihre Git-Repositorys zugreifen und diese verwalten.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie zu **Pipelines** Karte aus **Programmübersicht** und suchen Sie nach **Zugriff auf Repo Info** -Schaltfläche, um auf Ihr Git-Repository zuzugreifen und es zu verwalten.

   ![Schaltfläche &quot;Repo Info&quot;auf der Karte &quot;Umgebungen&quot;aufrufen](/help/implementing/cloud-manager/assets/repos/access-repo1.png)

1. Klicken Sie auf **Repo Info anzeigen** Schaltfläche zum Öffnen eines Dialogfelds zur Ansicht:

   * Die URL zum Git-Repository von Cloud Manager.
   * Der Git-Benutzername.
   * Das Git-Kennwort, dessen Wert beim **Kennwort generieren** auf klicken.

   ![Repository-Informationen](/help/implementing/cloud-manager/assets/repos/access-repo-create.png)

Mithilfe dieser Anmeldeinformationen kann der Benutzer eine lokale Kopie des Repositorys klonen und Änderungen an diesem lokalen Repository vornehmen. Sobald dies möglich ist, kann er alle Code-Änderungen wieder in das Remote-Code-Repository in Cloud Manager übertragen.

## Einrichten der Pipeline {#setup-pipeline}

Sobald Entwickler Ihren benutzerdefinierten Code zu Ihren Git-Repositorys hinzugefügt haben, kann der Bereitstellungsmanager Pipelines erstellen und ausführen, um diesen Code in Ihren AEM-Umgebungen bereitzustellen.

Führen Sie diese Schritte aus, um Ihre erste Bereitstellungs-Pipeline zu erstellen, die keine Produktionsimplementierung ist.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Rufen Sie die Karte **Pipelines** über den Startbildschirm von Cloud Manager auf. Klicken Sie auf **+Hinzufügen** und wählen Sie **Hinzufügen einer produktionsfremden Pipeline** aus.

   ![Produktionsfremde Pipeline hinzufügen](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add1.png)

1. Im **Konfiguration** des **Hinzufügen einer produktionsfremden Pipeline** wählen Sie den Typ der produktionsfremden Pipeline aus, die Sie hinzufügen möchten. Wählen Sie für dieses Beispiel **Bereitstellungs-Pipeline**.

   ![Dialogfeld „Produktionsfremde Pipeline hinzufügen“](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-config.png)

1. Geben Sie einen **Namen für die produktionsfremde Pipeline** an, um Ihre Pipeline zu identifizieren, sowie die folgenden zusätzlichen Informationen.

1. Für **Deployment Trigger** select **Manuell** damit die Pipeline nur ausgeführt wird, wenn Sie sie starten.

1. Klicken Sie auf **Weiter**.

1. Auf der Registerkarte **Quell-Code** im Dialogfeld **Produktionsfremde Pipeline hinzufügen** müssen Sie auswählen, welche Art von Code die Pipeline verarbeiten soll. Wählen Sie für dieses Beispiel **Vollständiger Stack-Code**.

1. In der Registerkarte **Quell-Code** müssen Sie die folgenden Optionen definieren.

   * **Förderfähige Bereitstellungsumgebungen** - Sie müssen auswählen, in welcher Umgebung die Pipeline bereitgestellt werden soll.
   * **Repository**: Diese Option definiert, aus welchem Git-Repository die Pipeline den Code abrufen soll.
   * **Git-Verzweigung**: Mit dieser Option wird festgelegt, von welchem Zweig in der ausgewählten Pipeline der Code abgerufen werden soll.
      * Geben Sie die ersten Zeichen des Verzweigungsnamens ein und die Funktion zum automatischen Vervollständigen dieses Feldes findet die entsprechenden Verzweigungen, um Ihnen bei der Auswahl zu helfen.

   ![Full-Stack-Pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-full-stack.png)

1. Klicken Sie auf **Speichern**.

Sie haben jetzt Ihre erste Pipeline erstellt! Benutzer mit der Rolle &quot;Bereitstellungsmanager&quot;können die Pipeline jetzt über die Cloud Manager-Benutzeroberfläche starten.

## Implementieren von {#deploy}

Nachdem Entwickler ihren benutzerdefinierten Code zu den Git-Repositorys hinzugefügt haben und Sie eine Pipeline erstellt haben, um diesen Code bereitzustellen, ist es an der Zeit, die Pipeline auszuführen, um diesen Code tatsächlich aus Git in Ihre Umgebung zu verschieben.

![Pipelines-Karte in Cloud Manager](/help/implementing/cloud-manager/assets/configure-pipeline/pipelines-card.png)

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie zum **Pipelines** der Karte **Programmübersicht** und klicken Sie auf die Suchschaltfläche neben der Pipeline, die Sie im vorherigen Abschnitt erstellt haben, und wählen Sie **Ausführen** aus dem Menü.

1. Der Pipeline-Ausführung beginnt und wird durch die Spalte **Status** angezeigt.

Sie können die Details der Ausführung sehen, indem Sie erneut auf die Suchschaltfläche klicken und **Details anzeigen**.

Herzlichen Glückwunsch! Sie haben jetzt Code aus Ihrem Git-Repository in einer Nicht-Produktionsumgebung bereitgestellt!

## Wie geht es weiter? {#whats-next}

Nachdem Sie dieses Dokument gelesen haben, sollten Sie Folgendes tun:

* Entwickler müssen wissen, wie Sie auf Ihre Cloud Manager-Git-Repositorys zugreifen und diese verwalten können.
* Als Bereitstellungsmanager können Sie Pipelines einrichten und Ihren Code in Cloud Manager bereitstellen.

Sie haben nicht nur Kenntnisse über Cloud Manager, sondern auch über Arbeitsumgebungen, Repositorys und Pipelines als Entwickler oder Bereitstellungsmanager erhalten! Aber es gibt noch mehr zu erfahren über AEM leistungsstarken CI/CD-Tools von as a Cloud Service. Sehen Sie sich die [Zusätzliche Ressourcen](#additional-resources) für weitere Details.

Wenn Sie möchten, wie Inhaltsautoren auf AEM as a Cloud Service zugreifen und diese verwenden, fahren Sie mit dem letzten Teil der Onboarding-Journey fort. [AEM Benutzeraufgaben.](aem-users.md)

>[!TIP]
>
>Da Sie nun über das nötige Wissen verfügen, können Sie [lernen, wie Sie das AEM-Referenzdemo-Add-on](/help/journey-sites/demos-add-on/overview.md) einfach einer Sandbox-Umgebung mit minimaler AEM-Konfiguration hinzufügen können und die leistungsstarken Funktionen von AEM mit umfangreichen Beispielen auf der Grundlage von Best Practices testen können.

## Zusätzliche Ressourcen {#additional-resources}

* [Zugreifen auf Repositorys](/help/implementing/cloud-manager/managing-code/accessing-repos.md) - Erfahren Sie, wie Sie mithilfe der Self-Service-Git-Kontoverwaltung über Cloud Manager auf Ihr Git-Repository zugreifen und es verwalten können.
* [Verwenden von Git mit Cloud Manager](/help/implementing/cloud-manager/managing-code/integrating-with-git.md) - Erfahren Sie, wie Sie die Git-Repositorys von Cloud Manager verwenden und wie Sie Ihr eigenes On-Premise-kundenverwaltetes Git-Repository mit Cloud Manager integrieren.
* [Lokale Entwicklungsumgebung einrichten](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html?lang=de) - Dieses Tutorial führt Sie durch die Einrichtung einer lokalen Entwicklungsumgebung für Adobe Experience Manager (AEM) mit dem AEM as a Cloud Service SDK.
* [Erste Schritte mit AEM Sites - WKND-Tutorial](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=de) - Dieses mehrteilige Tutorial wurde für Entwickler konzipiert, die neu in Adobe Experience Manager (AEM) sind. Dieses Tutorial führt Sie durch die Implementierung einer AEM Website für eine fiktive Lifestyle-Marke, die WKND. Das Tutorial behandelt grundlegende Themen wie Projekteinrichtung, Kernkomponenten, bearbeitbare Vorlagen, Client-seitige Bibliotheken und Komponentenentwicklung mit Adobe Experience Manager Sites.
* [Erste Schritte mit SPA in AEM Verwenden von React](/help/implementing/developing/hybrid/getting-started-react.md) - In diesem Artikel wird eine SPA-Beispielanwendung vorgestellt, erläutert, wie sie zusammengestellt wird, und es wird Ihnen ermöglicht, mithilfe des React-Frameworks schnell mit Ihren eigenen SPA zu arbeiten.
* [Erste Schritte mit SPA in AEM Verwenden von Angular](/help/implementing/developing/hybrid/getting-started-angular.md) - In diesem Artikel wird eine SPA-Beispielanwendung vorgestellt, erläutert, wie sie zusammengestellt wird, und ermöglicht es Ihnen, mithilfe des Angular-Frameworks schnell mit Ihren eigenen SPA zu arbeiten.
* [Headless-Entwickler-Journey](/help/journey-headless/developer/overview.md) - Beginnen Sie hier mit einem Kurs für die Entwicklung von Headless-Anwendungen mit AEM.
