---
title: Umgebungen erstellen
description: Erfahren Sie, wie Sie mit Cloud Manager Ihre ersten Umgebungen erstellen.
role: Admin, User, Developer
source-git-commit: 709a80683357b0d56280ff14aa5f4ba6bf2c6b23
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 26%

---


# Umgebungen erstellen {#create-environments}

In diesem Teil des [Onboarding-Journey,](overview.md) Hier erfahren Sie, wie Sie mit Cloud Manager Ihre ersten Umgebungen erstellen.

## Ziel {#objective}

Nach dem Lesen des vorherigen Dokuments in dieser Onboarding-Journey, [Erstellung von Programmen,](create-program.md) Sie verfügen jetzt über ein eigenes Cloud Manager-Programm. Jetzt können Sie lernen, wie Sie mit Cloud Manager Ihre ersten Umgebungen für dieses Programm erstellen können.

Nach dem Lesen dieses Dokuments werden Sie:

* Verstehen Sie, was eine Umgebung ist.
* Erkennen Sie den Unterschied zwischen den verschiedenen Umgebungen.
* Sie können Ihre eigene Umgebung erstellen.

## Was ist eine Umgebung? {#environments}

Umgebungen befinden sich unterhalb von Programmen in der Hierarchie von Cloud Manager. Während Programme es Ihnen ermöglichen, Ihre Adobe zu organisieren und bestimmten Teammitgliedern Zugriff auf diese Programme zu gewähren, gehören Umgebungen zu spezifischen Programmen und sind einzelne Instanzen der Programmlösungen. Umgebungen werden für einen bestimmten Zweck wie das Erstellen von Inhalten oder Testen neuer Entwicklungen verwendet. Die CI/CD-Pipelines von Cloud Manager erleichtern die Bereitstellung von Code in diesen Umgebungen aus Git-Repositorys.

Wenn Sie sich an das Beispiel der theoretischen WKND Travel and Adventure Enterprises erinnern, die ein Mandant ist, der sich auf reisebezogene Medien konzentriert, haben sie möglicherweise zwei Programme: ein Sites-Programm für die WKND Magazine-Division und ein Assets-Programm für den WKND Media-Bereich. Jedes Programm würde wahrscheinlich über mehrere Umgebungen verfügen, z. B. eine Produktionsumgebung, die den tatsächlichen Traffic der Site bereitstellt, und eine Entwicklungsumgebung zum Testen des neuen Anwendungs-Codes.

Es gibt drei verschiedene Arten von Umgebungen:

* **Produktion und Staging**: Die Produktions- und Staging-Umgebungen sind als Paar verfügbar und werden für Produktions- bzw. Testzwecke verwendet.
* **Entwicklung**: Die Entwicklungsumgebung kann zu Entwicklungs- und Testzwecken erstellt werden und wird ausschließlich produktionsfremden Pipelines zugeordnet.

Für diese Onboarding-Journey erstellen Sie eine Entwicklungsumgebung.

## Umgebungen erstellen {#creating-environments}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie auf das Programm, für das Sie eine Umgebung hinzufügen möchten.

1. Klicken Sie auf der Seite **Programmübersicht** auf der Karte **Umgebungen** auf **Umgebung hinzufügen**, um eine Umgebung hinzuzufügen.

   ![Karte „Umgebung“](/help/implementing/cloud-manager/assets/no-environments.png)

   * Die Option **Umgebung hinzufügen** ist auch auf der Registerkarte **Umgebungen** verfügbar.

      ![Registerkarte Umgebungen](/help/implementing/cloud-manager/assets/environments-tab.png)

   * Die Option **Umgebung hinzufügen** kann aufgrund fehlender Berechtigungen oder abhängig von den lizenzierten Ressourcen deaktiviert werden.

1. Im Dialogfeld **Umgebung hinzufügen** wird Folgendes angezeigt:

   * Wählen Sie einen **Umgebungstyp** aus.
      * Die Anzahl der verfügbaren/verwendeten Umgebungen wird in Klammern hinter dem Umgebungstyp &quot;Entwicklung&quot;angezeigt.
   * Geben Sie einen **Umgebungsnamen** an.
   * Geben Sie eine **Umgebungsbeschreibung** an.
   * Wählen Sie eine **Cloud-Region**.

   ![Dialogfeld „Umgebung hinzufügen“](/help/implementing/cloud-manager/assets/add-environment2.png)

1. Klicken Sie auf **Speichern**, um die angegebene Umgebung hinzuzufügen.

Sobald die Umgebung verfügbar ist, weisen die Mitglieder Ihrer Organisation der **Entwickler** Produktprofil kann sich bei Cloud Manager anmelden und Cloud Manager-Git-Repositorys verwalten.

## Wie geht es weiter? {#whats-next}

Nachdem Sie nun diesen Teil der Onboarding-Journey gelesen haben, sollten Sie:

* Verstehen Sie, was eine Umgebung ist.
* Erkennen Sie den Unterschied zwischen den verschiedenen Umgebungen.
* Sie können Ihre eigene Umgebung erstellen.

Ihre Cloud-Ressourcen wurden erstellt und stehen für den Zugriff durch Ihr Team zur Verfügung. Als Systemadministrator müssen Sie zunächst Ihre Teammitglieder AEM as a Cloud Service Produktprofilen aus Adobe Admin Console zuweisen, damit sie auf diese Ressourcen zugreifen können.

Daher sollten Sie Ihre Onboarding-Journey fortsetzen, indem Sie das Dokument erneut überprüfen. [Zuweisen von Team-Mitgliedern zu AEM as a Cloud Service Produktprofilen.](assign-profiles-aem.md)  In diesem Dokument erfahren Sie, wie Sie Ihren Teammitgliedern die Rechte gewähren, die sie für den Zugriff auf Ihre neuen Umgebungen benötigen.

## Zusätzliche Ressourcen {#additional-resources}

Folgen Sie den zusätzlichen Ressourcen, um mehr über Folgendes zu erfahren:

* [Verwalten von Umgebungen](/help/implementing/cloud-manager/manage-environments.md) - Erfahren Sie mehr über die Arten von Umgebungen, die Sie erstellen können, und wie Sie sie für Ihr Cloud Manager-Projekt erstellen
* [Verwenden von Adobe Cloud Manager - Umgebungen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html?lang=de) - Cloud Manager-Umgebungen bestehen aus AEM Authoring-, Publishing- und Dispatcher-Diensten. Erfahren Sie, wie verschiedene Umgebungen Rollen unterstützen und mit verschiedenen CI/CD-Pipelines interagieren können.
