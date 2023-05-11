---
title: Erstellen von Umgebungen
description: Erfahren Sie, wie Sie mit Cloud Manager Ihre ersten Umgebungen erstellen.
role: Admin, User, Developer
exl-id: 31940e1e-fe27-4c5f-b67f-41affebea63a
source-git-commit: 5c5db0d133adfbbb678930ef27d8ade10fd0c3be
workflow-type: tm+mt
source-wordcount: '773'
ht-degree: 86%

---

# Erstellen von Umgebungen {#create-environments}

In diesem Teil der [Onboarding-Tour](overview.md) erfahren Sie, wie Sie mit Cloud Manager Ihre ersten Umgebungen erstellen.

## Ziel {#objective}

Nach dem Lesen des vorherigen Dokuments in dieser Onboarding-Tour, [Erstellen von Programmen,](create-program.md), verfügen Sie jetzt über ein eigenes Cloud Manager-Programm. Jetzt können Sie lernen, wie Sie mit Cloud Manager Ihre ersten Umgebungen für dieses Programm erstellen.

Nach dem Lesen dieses Dokuments können Sie Folgendes:

* Verstehen, was eine Umgebung ist.
* Den Unterschied zwischen den verschiedenen Umgebungen erkennen.
* Ihre eigene Umgebung erstellen.

## Was ist eine Umgebung? {#environments}

Umgebungen befinden sich in der Cloud Manager-Hierarchie unterhalb von Programmen. Während Programme es Ihnen ermöglichen, Ihre Lösung zu organisieren und bestimmten Team-Mitgliedern Zugriff auf diese Programme zu gewähren, gehören Umgebungen zu bestimmten Programmen und sind individuelle Instanzen der Adobe-Lösungen innerhalb dieser Programme. Umgebungen werden für einen bestimmten Zweck wie etwa das Erstellen von Inhalten oder Testen neuer Entwicklungen verwendet. Die CI/CD-Pipelines von Cloud Manager erleichtern die Bereitstellung von Code in diesen Umgebungen aus Git-Repositorys.

Denken Sie an unser theoretisches Beispiel von WKND Travel and Adventure Enterprises. Dieser Mandant spezialisiert sich auf reisebezogene Medien. Dort könnte es zwei Programme geben: ein Sites-Programm für den WKND Magazine-Bereich und ein Assets-Programm für den WKND Media-Bereich. Jedes Programm würde wahrscheinlich über zwei Umgebungen verfügen: eine Produktionsumgebung, in der der tatsächliche Traffic der Site gehandhabt wird, und eine Entwicklungsumgebung zum Testen von neuem Programm-Code.

Es gibt vier verschiedene Arten von Umgebungen:

* **Produktion und Staging**: Die Produktions- und Staging-Umgebungen sind als Paar verfügbar und werden für Produktions- bzw. Testzwecke verwendet.
* **Entwicklung**: Die Entwicklungsumgebung kann zu Entwicklungs- und Testzwecken erstellt werden und wird ausschließlich produktionsfremden Pipelines zugeordnet.
* **Schnelle Entwicklung**: Eine schnelle Entwicklungsumgebung (RDE) ermöglicht es Entwickelnden, Änderungen schnell bereitzustellen und zu überprüfen, wodurch der Zeitaufwand für das Testen von Funktionen, die nachweislich in einer lokalen Entwicklungsumgebung funktionieren, minimiert wird.

Für die Zwecke dieser Onboarding-Journey erstellen Sie eine Entwicklungsumgebung, mit der Sie AEM as a Cloud Service Funktionen untersuchen können, um Ihre ersten Schritte zu beschleunigen.

## Erstellen von Umgebungen {#creating-environments}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie auf das Programm, für das Sie eine Umgebung hinzufügen möchten.

1. Klicken Sie auf der Seite **Programmübersicht** auf der Karte **Umgebungen** auf **Umgebung hinzufügen**, um eine Umgebung hinzuzufügen.

   ![Karte „Umgebung“](/help/implementing/cloud-manager/assets/no-environments.png)

   * Die Option **Umgebung hinzufügen** ist auch auf der Registerkarte **Umgebungen** verfügbar.

      ![Registerkarte Umgebungen](/help/implementing/cloud-manager/assets/environments-tab.png)

   * Die Option **Umgebung hinzufügen** kann aufgrund fehlender Berechtigungen oder abhängig von den lizenzierten Ressourcen deaktiviert werden.

1. Im Dialogfeld **Umgebung hinzufügen** wird Folgendes angezeigt:

   * Wählen Sie einen **Umgebungstyp** aus.
      * Die Anzahl der verfügbaren/verwendeten Umgebungen wird in Klammern hinter dem Umgebungstyp „Entwicklung“ angezeigt.
   * Geben Sie einen **Umgebungsnamen** an.
   * Geben Sie eine **Umgebungsbeschreibung** an.
   * Wählen Sie eine **Cloud-Region**.

   ![Dialogfeld „Umgebung hinzufügen“](/help/implementing/cloud-manager/assets/add-environment2.png)

1. Klicken Sie auf **Speichern**, um die angegebene Umgebung hinzuzufügen.

Sobald die Umgebung verfügbar ist, können sich Mitglieder Ihrer Organisation, die dem Produktprofil **Entwickler** zugeordnet sind, bei Cloud Manager anmelden und Cloud Manager-Git-Repositorys verwalten.

## Wie geht es weiter? {#whats-next}

Nachdem Sie nun diesen Teil der Onboarding-Tour abgeschlossen haben, sollten Sie Folgendes können:

* Verstehen, was eine Umgebung ist.
* Den Unterschied zwischen den verschiedenen Umgebungen erkennen.
* Ihre eigene Umgebung erstellen.

Ihre Cloud-Ressourcen wurden erstellt und stehen für den Zugriff durch Ihr Team zur Verfügung. Als System-Admin müssen Sie zunächst Ihren Team-Mitgliedern über die Adobe Admin Console Produktprofile in AEM as a Cloud Service zuweisen, damit sie auf diese Ressourcen zugreifen können.

Sie sollten deshalb Ihre Onboarding-Tour fortsetzen, indem Sie das Dokument [Zuweisen von Team-Mitgliedern zu Produktprofilen in AEM as a Cloud Service lesen.](assign-profiles-aem.md) In diesem Dokument erfahren Sie, wie Sie Ihren Team-Mitgliedern die Rechte gewähren, die sie für den Zugriff auf Ihre neuen Umgebungen benötigen.

## Zusätzliche Ressourcen {#additional-resources}

Im Folgenden finden Sie zusätzliche optionale Ressourcen, wenn Sie über den Inhalt des Onboarding-Journey hinausgehen möchten.

* [Verwaltung von Umgebungen](/help/implementing/cloud-manager/manage-environments.md) – Erfahren Sie mehr über die Arten von Umgebungen, die Sie erstellen können, und wie Sie sie für Ihr Cloud Manager-Projekt erstellen.
* [Verwenden von Adobe Cloud Manager-Umgebungen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html?lang=de) – Cloud Manager-Umgebungen bestehen aus Authoring-, Publishing- und Dispatcher-Services von AEM. Erfahren Sie, wie die verschiedene Umgebungen Rollen unterstützen und mit verschiedenen CI/CD-Pipelines interagieren können.
* [AEM Tipps und Tricks - Cloud Manager-Umgebungstypen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/expert-resources/aem-champions/environment-types.md) - In diesem Video erhalten Sie einen Überblick über die Cloud Manager-Umgebungstypen von einem AEM.
* [Schnelle Entwicklungsumgebungen](/help/implementing/developing/introduction/rapid-development-environments.md) - Weitere Informationen zur Verwendung eines RDE finden Sie in dieser Dokumentation .
