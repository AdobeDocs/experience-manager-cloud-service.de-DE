---
title: Einführung in Cloud Manager
description: Erfahren Sie, wie Cloud Manager Ihr AEM-Projekt mittels seiner Programme, Umgebungen und Pipelines unterstützt.
exl-id: b743f126-b34e-4f48-a3f0-5dbd4e1ac34e
feature: Onboarding
role: Admin, User, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: ht
source-wordcount: '864'
ht-degree: 100%

---


# Einführung in Cloud Manager {#intro-cloud-manager}

Cloud Manager ist eine wesentliche Komponente von AEM as a Cloud Service und dient als zentraler Einstiegspunkt für Ihr Team. Die speziell entwickelten CI/CD-Pipelines gewährleisten gründliche Tests und höchste Code-Qualität, um außergewöhnliche Erfahrungen zu liefern. Um sicherzustellen, dass Kundinnen und Kunden ihre Projekte schnell starten können, bietet Cloud Manager alles, was für einen Self-Service erforderlich ist, einschließlich der Möglichkeit, Cloud-Ressourcen und -Umgebungen zu erstellen und auf Ihre Git-Repositorys zuzugreifen. Diese Funktionen unterstützen die Einrichtung von Unternehmensentwicklungen, sodass Teams häufig Änderungen vornehmen, schnell außergewöhnliche digitale Erlebnisse bereitstellen und die Wertschöpfungszeit verkürzen können.

Ihr Systemadministrator ist für die Einrichtung Ihres Cloud Manager-Teams verantwortlich, das auch Personen, die Ihre Cloud-Ressourcen erstellen, sowie Entwickler umfasst. Weitere Informationen zum Einrichten und Skalieren Ihres Unternehmensentwicklungs-Teams und dazu, wie AEM as a Cloud Service Ihren Entwicklungsprozess unterstützen kann, finden Sie im Dokument [Einrichten der Entwicklung von Unternehmens-Teams für AEM as a Cloud Service](/help/implementing/cloud-manager/managing-code/enterprise-team-dev-setup.md).

## Navigieren zur Übersichtsseite von Cloud Manager {#navigate-cloud-manager}

Folgen Sie diesen Schritten, um zu Cloud Manager zu navigieren.

1. Navigieren Sie zur Anmeldeseite von Cloud Manager unter [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com/).

1. Wählen Sie das Programm auf der Cloud Manager-Seite **Programme und Produkte** aus, um die Seite **Überblick** zu starten.

Darüber hinaus können Sie von der Adobe Experience Cloud-Startseite aus auch zur Seite „Programme und Produkte“ von Cloud Manager navigieren.

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
| Erstellen/Ändern von Content-Sets | Erstellen oder Ändern eines Content-Sets für eine Inhaltskopie |  | x |  |  |
| Starten/Abbrechen einer Inhaltskopie | Starten oder Abbrechen eines Inhaltskopie-Prozesses |  | x |  |  |

>[!NOTE]
>
>Ein Anwender kann mehreren Rollen zugewiesen werden. Wenn Sie beispielsweise einer Person die Rollen **Geschäftsinhaber** und **Bereitstellungs-Manager** zuweisen, erhält sie die Kombination oder Summe dieser Berechtigungen.

>[!TIP]
>
>Es sind auch benutzerdefinierte Berechtigungsprofile mit konfigurierbaren Berechtigungen verfügbar. Weitere Informationen finden Sie im Dokument [Benutzerdefinierte Berechtigungen](/help/implementing/cloud-manager/custom-permissions.md).

## Cloud Manager-Programme {#cloud-manager-programs}

Cloud Manager-Programme stellen eine Reihe von Cloud Manager-Umgebungen dar, die logische Gruppierungen von Geschäftsinitiativen unterstützen. Diese Gruppierungen entsprechen in der Regel einem erworbenen Service Level Agreement (SLA). Beispielsweise kann ein Programm die AEM-Ressourcen zur Unterstützung der öffentlichen Website eines Unternehmens darstellen, während ein anderes Programm ein internes zentrales DAM darstellt.


Sehen Sie sich dieses [Video](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html?lang=de) an, um mehr über die Verwendung von Cloud Manager-Programmen zu erfahren.

Ein Benutzer kann ein **Sandbox-** oder ein **Produktionsprogramm** erstellen.

* Ein **Produktionsprogramm** wird erstellt, um Live-Traffic zum richtigen Zeitpunkt in der Zukunft zu aktivieren.
   * Weitere Informationen finden Sie in der [Einführung in Produktionsprogramme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-production-programs.md).

* Ein **Sandbox-Programm** wird normalerweise für Schulungen, Ausführungen von Demos, Aktivierungen, Konzeptnachweise oder Dokumentation erstellt.
   * Es soll keinen Live-Traffic verarbeiten und hat Einschränkungen, die ein Produktionsprogramm nicht hat.
   * Sie umfasst Sites und Assets und wird automatisch mit einer Git-Verzweigung befüllt, die Beispiel-Code, eine Entwicklungsumgebung und eine produktionsfremde Pipeline enthält.
   * Weitere Informationen finden Sie in der [Einführung in Sandbox-Programme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md).

## Cloud Manager-Umgebungen {#cloud-manager-environments}

Ihre Cloud-Umgebungen werden über Cloud Manager erstellt, aufgerufen und angezeigt. Diese Umgebungen können Produktions-, Staging- oder Entwicklungsumgebungen sein. Verschiedene Umgebungen unterstützen unterschiedliche Zwecke und können mit verschiedenen CI/CD-Pipelines eingesetzt werden. Umgebungen bestehen aus Services wie:

* [AEM-Authoring-Services](#author-services)
* [AEM-Publishing-Services](#publish-services)
* [Dispatcher-Services](#dispatcher-services)

>[!TIP]
>
> Eine Übersicht über die verfügbaren Umgebungen finden Sie im Video [Verwenden von Adobe Cloud Manager-Umgebungen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html?lang=de).
>
>Weitere Informationen zu den Umgebungstypen, die eine Benutzerin bzw. ein Benutzer erstellen kann, und dazu, wie eine Umgebung erstellt wird, finden Sie unter [Verwalten von Umgebungen](/help/implementing/cloud-manager/manage-environments.md).

### AEM-Authoring-Service {#author-services}

Der AEM-Authoring-Service ist in Umgebungen enthalten, in denen Website-Inhalte und digitale Assets erstellt, verwaltet und aktualisiert werden. In der Regel haben nur interne Benutzer Zugriff auf den Authoring-Service, der sich hinter einem Anmeldebildschirm befindet. Der Authoring-Service dient sowohl als Authoring- als auch als Vorschau-Umgebung.

### AEM-Publishing-Service {#publish-services}

Ein AEM-Publishing-Service ist in Umgebungen enthalten, in denen das Endbenutzererlebnis gehostet wird, z. B. auf einer Website. Dies ist der Service, den Besucher der Website anzeigen und mit dem sie interagieren. In der Regel ist der Publishing-Service öffentlich verfügbar.

### AEM-Dispatcher-Service {#dispatcher-services}

Der Dispatcher ist ein `Apache HTTP Web server`-Modul, das eine Sicherheits- und Leistungsschicht bietet, die sich vor dem AEM-Publishing-Service befindet.
