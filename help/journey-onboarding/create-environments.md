---
title: Erstellen von Umgebungen
description: Erfahren Sie, wie Sie mit Cloud Manager Ihre ersten Umgebungen erstellen.
role: Admin, User, Developer
exl-id: 31940e1e-fe27-4c5f-b67f-41affebea63a
feature: Onboarding
source-git-commit: 9c5838a01ceecf094aea19578e6560a5e5ca8c4c
workflow-type: tm+mt
source-wordcount: '775'
ht-degree: 63%

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

Wenn Sie sich an das Beispiel der theoretischen WKND-Reise- und Erlebnisunternehmen erinnern, handelt es sich um einen Mandanten, der sich auf Medien zum Thema Reisen konzentriert. Er könnte zwei Programme haben. Das heißt, ein Sites-Programm für den WKND-Magazinbereich und ein Assets-Programm für den WKND-Medienbereich. Jedes Programm würde wahrscheinlich über zwei Umgebungen verfügen: eine Produktionsumgebung, in der der tatsächliche Traffic der Site gehandhabt wird, und eine Entwicklungsumgebung zum Testen von neuem Programm-Code.

Es gibt fünf verschiedene Arten von Umgebungen:

* **Produktion und Staging**: Die Produktions- und Staging-Umgebungen sind als Paar verfügbar und werden für Produktions- bzw. Testzwecke verwendet.
* **Entwicklung**: Die Entwicklungsumgebung kann zu Entwicklungs- und Testzwecken erstellt werden und wird ausschließlich produktionsfremden Pipelines zugeordnet.
* **Schnelle Entwicklung**: Eine schnelle Entwicklungsumgebung (RDE) ermöglicht es Entwickelnden, Änderungen schnell bereitzustellen und zu überprüfen. Dadurch wird der Zeitaufwand für das Testen von Funktionen minimiert, die nachweislich in einer lokalen Entwicklungsumgebung funktionieren.
* **Spezialisierte Testumgebung**: Bietet einen dedizierten Raum zur Validierung von Funktionen unter produktionsnahen Bedingungen, ideal für Belastungstests und erweiterte Prüfungen vor der Bereitstellung.

Für die Zwecke dieser Onboarding-Tour erstellen Sie eine Entwicklungsumgebung, mit der Sie AEM as a Cloud Service-Funktionen untersuchen können, um mit einem Minimum zu beginnen.

## Erstellen einer Umgebung {#creating-environments}

>[!NOTE]
>
>Das System zeichnet den Benutzer, der eine Umgebung erstellt, als seinen Ersteller auf. Da gelöschte Benutzer manchmal wiederhergestellt werden können, wählen Sie den Ersteller der Umgebung sorgfältig aus.

**So erstellen Sie eine Umgebung:**

1. Melden Sie sich bei Cloud Manager unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) an und wählen Sie die entsprechende Organisation aus.

1. Wählen Sie das Programm aus, für das Sie eine Umgebung hinzufügen möchten.

1. Um eine Umgebung hinzuzufügen, wählen Sie auf der **&quot;**&quot; auf der Karte **Umgebungen** die Option **Umgebung hinzufügen** aus.

   ![Karte „Umgebung“](/help/implementing/cloud-manager/assets/no-environments.png)

   * Die Option **Umgebung hinzufügen** ist auch auf der Registerkarte **Umgebungen** verfügbar.

     ![Registerkarte Umgebungen](/help/implementing/cloud-manager/assets/environments-tab.png)

   * Die Option **Umgebung hinzufügen** kann aufgrund fehlender Berechtigungen oder abhängig von den lizenzierten Ressourcen deaktiviert werden.

1. Gehen Sie im Dialogfeld **Umgebung hinzufügen** wie folgt vor:

   * Wählen Sie einen **Umgebungstyp** aus.
      * Die Anzahl der verfügbaren/verwendeten Umgebungen wird in Klammern hinter dem Umgebungstyp „Entwicklung“ angezeigt.
   * Geben Sie einen **Umgebungsnamen** an.
   * Geben Sie eine **Umgebungsbeschreibung** an.
   * Wählen Sie eine **Cloud-Region**.

   ![Dialogfeld „Umgebung hinzufügen“](/help/implementing/cloud-manager/assets/add-environment2.png)

1. Klicken Sie auf **Speichern**, um die angegebene Umgebung hinzuzufügen.

Sobald die Umgebung verfügbar ist, können sich Mitglieder Ihrer Organisation, die dem Produktprofil **Entwickler** zugewiesen sind, bei Cloud Manager anmelden und Cloud Manager-Git-Repositorys verwalten.

## Wie geht es weiter {#whats-next}

Nachdem Sie nun diesen Teil der Onboarding-Tour abgeschlossen haben, sollten Sie Folgendes können:

* Verstehen, was eine Umgebung ist.
* Den Unterschied zwischen den verschiedenen Umgebungen erkennen.
* Ihre eigene Umgebung erstellen.

Ihr Team kann jetzt auf die von Ihnen erstellten Cloud-Ressourcen zugreifen. Als System-Administratorin oder -Administrator müssen Sie Ihren Team-Mitgliedern zunächst über die Adobe Admin Console Produktprofile in AEM as a Cloud Service zuweisen, damit sie auf diese Ressourcen zugreifen können.

Sie sollten daher Ihre Onboarding-Journey fortsetzen, indem Sie das Dokument „Zuweisen von Team[Mitgliedern zu AEM as a Cloud Service-Produktprofilen“ ](assign-profiles-aem.md). In diesem Dokument erfahren Sie, wie Sie Ihren Team-Mitgliedern Rechte an Ihren neuen Umgebungen gewähren.

## Zusätzliche Ressourcen {#additional-resources}

Im Folgenden finden Sie zusätzliche optionale Ressourcen, wenn Sie über den Inhalt der Onboarding-Tour hinausgehen möchten.

* [Verwaltung von Umgebungen](/help/implementing/cloud-manager/manage-environments.md): Erfahren Sie mehr über die Arten von Umgebungen, die Sie erstellen können, und wie Sie sie für Ihr Cloud Manager-Projekt erstellen.
* [Verwenden von Adobe Cloud Manager-Umgebungen](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/cloud-manager/environments): Cloud Manager-Umgebungen bestehen aus Authoring-, Publishing- und Dispatcher-Services von AEM. Erfahren Sie, wie verschiedene Umgebungen Rollen unterstützen und mit verschiedenen CI/CD-Pipelines interagieren können.
* [Schnelle Entwicklungsumgebungen](/help/implementing/developing/introduction/rapid-development-environments.md): Weitere Informationen zur Verwendung eines RDE finden Sie in dieser Dokumentation.
<!-- ERROR: Not Found (HTTP error 404) FIND AN ALTERNATE RESOURCE? * [AEM Champion Tips and Tricks - Cloud Manager Environment Types](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/expert-resources/aem-champions/environment-types.md) - Watch this video for an overview of Cloud Manager environment types from an AEM champion. -->

