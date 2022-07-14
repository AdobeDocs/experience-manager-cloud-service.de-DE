---
title: Einführung in Cloud Manager
description: Erfahren Sie, wie Cloud Manager Ihr AEM-Projekt über seine Programme, Umgebungen und Pipelines unterstützt.
exl-id: b743f126-b34e-4f48-a3f0-5dbd4e1ac34e
source-git-commit: 2d793f22e554c2a4bde8831b5053d1640ba07c70
workflow-type: tm+mt
source-wordcount: '834'
ht-degree: 26%

---

# Einführung in Cloud Manager {#intro-cloud-manager}

Cloud Manager ist eine wesentliche Komponente von AEM as a Cloud Service und dient als zentraler Einstiegspunkt für Ihr Team. Die speziell entwickelten CI/CD-Pipelines sind für gründliche Tests und höchste Code-Qualität ausgelegt, um außergewöhnliche Erlebnisse zu bieten. Um sicherzustellen, dass Kunden ihre Projekte schnell starten können, bietet Cloud Manager alles, was für einen Self-Service erforderlich ist, einschließlich der Möglichkeit, Cloud-Ressourcen und -Umgebungen zu erstellen und auf Ihre Git-Repositorys zuzugreifen. Diese Funktionen unterstützen Entwicklungs-Setups in Unternehmen, sodass Teams daran arbeiten können, häufig Änderungen vorzunehmen, rasch außergewöhnliche digitale Erlebnisse bereitzustellen und die Time-to-Value zu verkürzen.

Ihr Systemadministrator ist für die Einrichtung Ihres Cloud Manager-Teams zuständig, das auch Einzelanwender umfasst, die Ihre Cloud-Ressourcen und -Entwickler erstellen. Weitere Informationen zum Einrichten und Skalieren Ihres Entwicklungsteams für Unternehmen und dazu, wie AEM as a Cloud Service Ihren Entwicklungsprozess unterstützen kann, finden Sie im Dokument . [Einrichten der Enterprise-Team-Entwicklung für AEM as a Cloud Service.](/help/implementing/cloud-manager/managing-code/enterprise-team-dev-setup.md)

## Navigieren zur Übersichtsseite von Cloud Manager {#navigate-cloud-manager}

Führen Sie die folgenden Schritte aus, um zu Cloud Manager zu navigieren.

1. Navigieren Sie zur Anmeldeseite von Cloud Manager unter [`https://my.cloudmanager.adobe.com`.](https://my.cloudmanager.adobe.com/).

1. Wählen Sie das Programm aus der Cloud Manager - **Programme und Produkte** Seite, um die **Übersicht** Seite.

Sie können auch von der Adobe Experience Cloud-Startseite aus zur Seite Programme und Produkte von Cloud Manager navigieren, indem Sie die folgenden Schritte ausführen.

1. Navigieren Sie zu Adobe Experience Cloud unter [`https://experience.adobe.com`](https://experience.adobe.com) und melden Sie sich mit Ihrer Adobe ID an.

1. Stellen Sie sicher, dass Sie sich in der richtigen Organisation befinden, indem Sie auf den Organisationsnamen verweisen, der oben rechts in der Symbolleiste angezeigt wird.

1. Wählen Sie **Experience Manager** aus.

1. Im **Cloud Manager** Karte, klicken Sie auf **Launch**

## Rollenbasierte Berechtigungen in Cloud Manager {#role-based-permissions}

| Berechtigung | Beschreibung | Geschäftsinhaber | Bereitstellungs-Manager | Programm-Manager | Entwickler |
|--- |--- |--- |--- |--- |--- |
| Programm hinzufügen<br>Programm bearbeiten | Neues Programm hinzufügen<br>Lösungen oder Add-ons hinzufügen oder entfernen | x |  |  |  |
| Umgebung einrichten | Erstellen von Produktions-, Staging- und Entwicklungsumgebungen | x | x |  |  |
| Umgebung aktualisieren | Produktions-, Staging- und Entwicklungsumgebungen aktualisieren | x | x |  |  |
| Entwicklungsumgebung löschen | Löschen von Entwicklungsumgebungen | x | x |  |  |
| Einrichten der Pipeline | Einrichten und Bearbeiten von Pipelines |  | x |  |  |
| Pipeline-Ausführung | Pipelines starten | x | x |  |  |
| Pipeline-Ausführung | Ablehnen/Genehmigen wichtiger 3-Tier-Qualitäts-Gate-Fehler | x | x | x |  |
| Pipeline-Ausführung | Live-Genehmigung einreichen | x | x | x |  |
| Pipeline-Ausführung | Produktionsbereitstellungen planen | x | x | x |  |
| Pipeline löschen | Löschen der Pipeline zulassen |  | x |  |  |
| Ausführung abbrechen | Abbrechen der aktuellen Ausführung |  | x |  |  |
| Persönliches Zugriffs-Token erstellen | Git-Zugriff |  | x |  | x |

>[!NOTE]
>
>Ein Anwender kann mehreren Rollen zugewiesen werden. Beispielsweise können Sie beide **Business Owner** und **Bereitstellungsmanager** Benutzerrollen gibt dem Benutzer die Summe dieser Berechtigungen.

## Cloud Manager-Programme {#cloud-manager-programs}

Cloud Manager-Programme stellen eine Reihe von Cloud Manager-Umgebungen dar, die logische Gruppierungen von Geschäftsinitiativen unterstützen. Diese Gruppierungen entsprechen in der Regel einem erworbenen Service Level Agreement (SLA). Beispielsweise kann ein Programm die AEM Ressourcen zur Unterstützung der öffentlichen Website eines Unternehmens darstellen, während ein anderes Programm ein internes DAM darstellt.


Sehen Sie sich dieses [Video](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html?lang=de) an, um mehr über die Verwendung von Cloud Manager-Programmen zu erfahren.

Ein Benutzer kann ein **Sandbox-** oder ein **Produktionsprogramm** erstellen.

* A **Produktionsprogramm** wird erstellt, um Live-Traffic zum richtigen Zeitpunkt in der Zukunft zu aktivieren.
   * Weitere Informationen finden Sie im Dokument [Einführung in Produktionsprogramme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-production-programs.md).

* A **Sandbox-Programm** wird normalerweise für Schulungen, laufende Demos, Aktivierungen, das Erstellen von POCs oder für Dokumentationen erstellt.
   * Es ist nicht dazu gedacht, Live-Traffic zu übertragen, und es gibt Einschränkungen, die ein Produktionsprogramm nicht hat.
   * Es umfasst Sites und Assets und wird automatisch mit einer Git-Verzweigung bereitgestellt, die Beispielcode, eine Entwicklungsumgebung und eine Nicht-Produktions-Pipeline enthält.
   * Weitere Informationen finden Sie im Dokument [Einführung in Sandbox-Programme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md).

## Cloud Manager-Umgebungen {#cloud-manager-environments}

Ihre Cloud-Umgebungen werden über Cloud Manager erstellt, aufgerufen und angezeigt. Diese Umgebungen können Produktions-, Staging- oder Entwicklungsumgebungen sein. Verschiedene Umgebungen dienen unterschiedlichen Zwecken und können mit verschiedenen CI/CD-Pipelines verwendet werden. Umgebungen bestehen aus Services wie:

* [AEM Authoring-Dienste](#author-services)
* [AEM Publishing Services](#publish-services)
* [Dispatcher-Services](#dispatcher-services)

>[!TIP]
>
> Siehe Video. [Verwenden von Adobe Cloud Manager-Umgebungen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html?lang=de) einen Überblick über die verfügbaren Umgebungen.
>
>Siehe Dokument . [Verwalten von Umgebungen](/help/implementing/cloud-manager/manage-environments.md) , um mehr über die Umgebungstypen zu erfahren, die ein Benutzer erstellen kann, und darüber, wie der Benutzer eine Umgebung erstellen kann.

### AEM Authoring-Dienst {#author-services}

Ein AEM Authoring-Dienst ist in Umgebungen enthalten, in denen Site-Inhalte und digitale Assets erstellt, verwaltet und aktualisiert werden. In der Regel haben nur interne Benutzer Zugriff auf den Authoring-Dienst und er wird hinter einem Anmeldebildschirm verwaltet. Der Authoring-Dienst dient sowohl als Authoring- als auch als Vorschau-Umgebung.

### AEM Publishing Service {#publish-services}

Ein AEM Publishing-Dienst ist in Umgebungen enthalten, in denen das Endbenutzererlebnis gehostet wird, z. B. auf einer Website. Dies ist der Service, den Besucher der Website anzeigen und mit dem Sie interagieren. In der Regel ist der Veröffentlichungsdienst öffentlich verfügbar.

### AEM-Dispatcher-Service {#dispatcher-services}

Der Dispatcher ist ein `Apache HTTP Web server` -Modul, das eine Sicherheits- und Leistungsschicht bietet, die sich vor dem AEM Publishing-Dienst befindet.
