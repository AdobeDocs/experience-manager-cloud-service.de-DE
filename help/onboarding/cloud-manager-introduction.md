---
title: Einführung in Cloud Manager
description: Erfahren Sie, wie Cloud Manager Ihr AEM-Projekt mittels seiner Programme, Umgebungen und Pipelines unterstützt.
exl-id: b743f126-b34e-4f48-a3f0-5dbd4e1ac34e
source-git-commit: fe2b0eab36a3ecd6c731fe8c9ac23fd4a3175341
workflow-type: tm+mt
source-wordcount: '861'
ht-degree: 80%

---

# Einführung in Cloud Manager {#intro-cloud-manager}

Cloud Manager ist eine wesentliche Komponente von AEM as a Cloud Service und dient als zentraler Einstiegspunkt für Ihr Team. Die speziell entwickelten CI/CD-Pipelines gewährleisten gründliche Tests und höchste Code-Qualität, um außergewöhnliche Erfahrungen zu liefern. Um sicherzustellen, dass Kundinnen und Kunden ihre Projekte schnell starten können, bietet Cloud Manager alles, was für einen Self-Service erforderlich ist, einschließlich der Möglichkeit, Cloud-Ressourcen und -Umgebungen zu erstellen und auf Ihre Git-Repositorys zuzugreifen. Diese Funktionen unterstützen die Einrichtung von Unternehmensentwicklungen, sodass Teams häufig Änderungen vornehmen, schnell außergewöhnliche digitale Erlebnisse bereitstellen und die Wertschöpfungszeit verkürzen können.

Ihr Systemadministrator ist für die Einrichtung Ihres Cloud Manager-Teams verantwortlich, das auch Personen, die Ihre Cloud-Ressourcen erstellen, sowie Entwickler umfasst. Weitere Informationen zum Einrichten und Skalieren Ihres Entwicklungsteams für Unternehmen und dazu, wie AEM as a Cloud Service Ihren Entwicklungsprozess unterstützen kann, finden Sie unter [Einrichten der Enterprise-Team-Entwicklung für AEM as a Cloud Service](/help/implementing/cloud-manager/managing-code/enterprise-team-dev-setup.md).

## Navigieren zur Übersichtsseite von Cloud Manager {#navigate-cloud-manager}

Folgen Sie diesen Schritten, um zu Cloud Manager zu navigieren.

1. Navigieren Sie zur Anmeldeseite von Cloud Manager unter [`https://my.cloudmanager.adobe.com`.](https://my.cloudmanager.adobe.com/).

1. Wählen Sie das Programm aus der Cloud Manager-Seite **Programme und Produkte** aus, um die Seite **Überblick** zu starten.

Sie können auch von der Adobe Experience Cloud-Startseite aus zur Seite Programme und Produkte von Cloud Manager navigieren, indem Sie die folgenden Schritte ausführen.

1. Navigieren Sie zu Adobe Experience Cloud unter [`https://experience.adobe.com`](https://experience.adobe.com) und melden Sie sich mit Ihrer Adobe ID an.

1. Vergewissern Sie sich, dass Sie sich in der richtigen Organisation befinden, indem Sie auf den Organisationsnamen achten, der oben rechts in der Symbolleiste angezeigt wird.

1. Wählen Sie **Experience Manager** aus.

1. Klicken Sie auf der Karte **Cloud Manager** auf **Starten**

## Rollenbasierte Berechtigungen in Cloud Manager {#role-based-permissions}

| Berechtigung | Beschreibung | Geschäftsinhaber | Bereitstellungs-Manager | Programm-Manager | Entwickler |
|--- |--- |--- |--- |--- |--- |
| Programm hinzufügen<br>Programm bearbeiten | Ein neues Programm hinzufügen<br>Lösungen oder Add-ons hinzufügen oder entfernen | x |  |  |  |
| Umgebung einrichten | Erstellen von Produktions-, Staging- und Entwicklungsumgebungen | x | x |  |  |
| Umgebung aktualisieren | Aktualisieren von Produktions-, Staging- und Entwicklungsumgebungen | x | x |  |  |
| Entwicklungsumgebung löschen | Löschen von Entwicklungsumgebungen | x | x |  |  |
| Einrichten der Pipeline | Einrichten und Bearbeiten von Pipelines |  | x |  |  |
| Pipeline-Ausführung | Starten von Pipelines | x | x |  |  |
| Pipeline-Ausführung | Ablehnen/Genehmigen wichtiger dreistufiger Qualitäts-Gate-Fehler | x | x | x |  |
| Pipeline-Ausführung | Erteilen der Genehmigung einer Live-Schaltung | x | x | x |  |
| Pipeline-Ausführung | Planen von Produktionsbereitstellungen | x | x | x |  |
| Pipeline löschen | Löschen der Pipeline zulassen |  | x |  |  |
| Ausführung abbrechen | Abbrechen der aktuellen Ausführung |  | x |  |  |
| Persönliches Zugriffs-Token erstellen | Zugriff auf Git |  | x |  | x |
| Erstellen der RDE | Erstellen einer schnellen Entwicklungsumgebung | x |  |  | x |
| Zurücksetzen der RDE | Zurücksetzen einer schnellen Entwicklungsumgebung | x |  |  | x |
| Inhaltssätze erstellen/ändern | Inhaltssatz für Inhaltskopie erstellen oder ändern |  | x |  |  |
| Inhaltskopie starten/abbrechen | Starten oder Abbrechen eines Inhaltskopierprozesses |  | x |  |  |

>[!NOTE]
>
>Ein Anwender kann mehreren Rollen zugewiesen werden. Beispielsweise können Sie beide **Business Owner** und **Bereitstellungsmanager** Benutzerrollen gibt dem Benutzer die Summe dieser Berechtigungen.

## Cloud Manager-Programme {#cloud-manager-programs}

Cloud Manager-Programme stellen eine Reihe von Cloud Manager-Umgebungen dar, die logische Gruppierungen von Geschäftsinitiativen unterstützen. Diese Gruppierungen entsprechen in der Regel einem erworbenen Service Level Agreement (SLA). Beispielsweise kann ein Programm die AEM-Ressourcen zur Unterstützung der öffentlichen Website eines Unternehmens darstellen, während ein anderes Programm ein internes zentrales DAM darstellt.


Sehen Sie sich dieses [Video](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html?lang=de) an, um mehr über die Verwendung von Cloud Manager-Programmen zu erfahren.

Ein Benutzer kann ein **Sandbox-** oder ein **Produktionsprogramm** erstellen.

* Ein **Produktionsprogramm** wird erstellt, um Live-Traffic zum richtigen Zeitpunkt in der Zukunft zu aktivieren.
   * Siehe [Einführung in Produktionsprogramme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-production-programs.md) für weitere Details.

* Ein **Sandbox-Programm** wird normalerweise für Schulungen, Ausführungen von Demos, Aktivierungen, Konzeptnachweise oder Dokumentation erstellt.
   * Es soll keinen Live-Traffic verarbeiten und hat Einschränkungen, die ein Produktionsprogramm nicht hat.
   * Es umfasst Sites und Assets und wird automatisch mit einer Git-Verzweigung geliefert, die Beispiel-Code, eine Entwicklungsumgebung und eine produktionsfremde Pipeline enthält.
   * Siehe [Einführung in Sandbox-Programme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md) für weitere Details.

## Cloud Manager-Umgebungen {#cloud-manager-environments}

Ihre Cloud-Umgebungen werden über Cloud Manager erstellt, aufgerufen und angezeigt. Diese Umgebungen können Produktions-, Staging- oder Entwicklungsumgebungen sein. Verschiedene Umgebungen unterstützen unterschiedliche Zwecke und können mit verschiedenen CI/CD-Pipelines eingesetzt werden. Umgebungen bestehen aus Services wie:

* [AEM-Authoring-Services](#author-services)
* [AEM-Publishing-Services](#publish-services)
* [Dispatcher-Services](#dispatcher-services)

>[!TIP]
>
> Video anzeigen [Verwenden von Adobe Cloud Manager-Umgebungen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html?lang=de) einen Überblick über die verfügbaren Umgebungen.
>
>Siehe [Verwalten von Umgebungen](/help/implementing/cloud-manager/manage-environments.md) , um mehr über die Umgebungstypen zu erfahren, die ein Benutzer erstellen kann, und darüber, wie der Benutzer eine Umgebung erstellen kann.

### AEM-Authoring-Service {#author-services}

Der AEM-Authoring-Service ist in Umgebungen enthalten, in denen Website-Inhalte und digitale Assets erstellt, verwaltet und aktualisiert werden. In der Regel haben nur interne Benutzer Zugriff auf den Authoring-Service, der sich hinter einem Anmeldebildschirm befindet. Der Authoring-Service dient sowohl als Authoring- als auch als Vorschau-Umgebung.

### AEM-Publishing-Service {#publish-services}

Ein AEM-Publishing-Service ist in Umgebungen enthalten, in denen das Endbenutzererlebnis gehostet wird, z. B. auf einer Website. Dies ist der Service, den Besucher der Website anzeigen und mit dem sie interagieren. In der Regel ist der Publishing-Service öffentlich verfügbar.

### AEM-Dispatcher-Service {#dispatcher-services}

Der Dispatcher ist ein `Apache HTTP Web server`-Modul, das eine Sicherheits- und Leistungsschicht bietet, die sich vor dem AEM-Publishing-Service befindet.
