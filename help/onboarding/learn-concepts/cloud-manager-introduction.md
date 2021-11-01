---
title: Erfahren Sie, was Cloud Manager ist.
description: Auf dieser Seite erfahren Sie mehr über Cloud Manager, Cloud Manager-Programme und -Umgebungen.
exl-id: b743f126-b34e-4f48-a3f0-5dbd4e1ac34e
source-git-commit: c206bc241bccf6f8a5bfb4946d6231f53438861a
workflow-type: tm+mt
source-wordcount: '907'
ht-degree: 92%

---

# Einführung in Cloud Manager {#intro-cloud-manager}

Cloud Manager ist eine wesentliche Komponente von AEM as a Cloud Service und dient als zentraler Einstiegspunkt für Ihr Team.

Zur Unterstützung von Kunden mit Enterprise-Entwicklungs-Setups ist AEM as a Cloud Service vollständig in Cloud Manager und die speziell hierfür vorgesehenen CI/CD-Pipelines integriert. Diese sind so ausgestattet, dass gründliche Tests und höchste Codequalität gewährleistet sind, um ein außergewöhnliches Erlebnis zu bieten.

Um sicherzustellen, dass Kunden schnell mit AEM as a Cloud Service beginnen können, bietet Cloud Manager in einer Selbstbedienungsweise alles, was für die ersten Schritte erforderlich ist, einschließlich der Möglichkeit, Cloud-Ressourcen und -Umgebungen zu erstellen. Auf diese Weise können Ihre AEM-Entwickler über Cloud Manager auf das Git-Repository zugreifen. Mithilfe von Cloud Manager können Entwicklungs-Teams Änderungen häufig im Selbstbedienungsmodus einpflegen.

Ihr Systemadministrator ist für die Einrichtung Ihres Cloud Manager-Teams verantwortlich, das auch Personen umfasst, die Ihre Cloud-Ressourcen erstellen sowie Entwickler. Unter [Einrichten der Enterprise-Team-Entwicklung für AEM as a Cloud Service](/help/implementing/cloud-manager/managing-code/enterprise-team-dev-setup.md) erfahren Sie, wie Cloud Manager bei der Einrichtung der Enterprise-Team-Entwicklung unterstützt.

## Navigieren zur Übersichtsseite von Cloud Manager {#navigate-cloud-manager}

Führen Sie die nachfolgenden Schritte aus, um zu Cloud Manager zu gelangen:

1. Navigieren Sie von direkt zur Anmeldeseite von Cloud Manager. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/).

   >[!NOTE]
   >Bitte Lesezeichen für diese Seite einfügen, um Sie bei der Navigation zur Landingpage von Cloud Manager zu unterstützen.

1. Wählen Sie das Programm aus der Cloud Manager - **Programme und Produkte** Seite, um die **Übersicht** Seite.

Darüber hinaus können Sie von der Adobe Experience Cloud-Startseite aus zur Seite Programme und Produkte von Cloud Manager navigieren. Führen Sie dazu folgende Schritte durch:

1. Gehen Sie direkt zu [Adobe Experience Cloud](https://experience.adobe.com/#/@foundationinternal/home) und melden Sie sich mit Ihrer Adobe ID an.

1. Wählen Sie **Experience Manager** aus.

1. Klicken Sie auf der Karte „Cloud Manager“ auf **Launch**. Nachdem Sie sich erfolgreich bei Cloud Manager angemeldet haben, können Sie die Benutzeroberfläche verwenden.

   Nach erfolgreicher Anmeldung werden Sie zur Landingpage von Cloud Manager weitergeleitet.

## Rollenbasierte Berechtigungen in Cloud Manager {#role-based-permissions}

| Berechtigung | Beschreibung | Geschäftsinhaber | Bereitstellungs-Manager | Programm-Manager | Entwickler |
|--- |--- |--- |--- |--- |--- |
| Programm hinzufügen<br>Programm bearbeiten | Neues Programm hinzufügen.<br>Programm bearbeiten – Lösungen oder Add-ons hinzufügen oder entfernen | x |  |  |  |
| Umgebung einrichten | Kann Produktions-, Staging und Entwicklungs-Umgebungen erstellen. | x | x |  |  |
| Umgebung aktualisieren | Kann Produktions-, Staging und Entwicklungs-Umgebungen aktualisieren. | x | x |  |  |
| Entwicklungsumgebung löschen | Kann Entwicklungsumgebungen löschen. | x | x |  |  |
| Einrichten der Pipeline | Kann die Pipeline einrichten oder bearbeiten. |  | x |  |  |
| Pipeline-Ausführung | Kann die Pipeline starten. | x | x |  |  |
| Pipeline-Ausführung | Kann wichtige 3-Tier-Fehler ablehnen/akzeptieren. | x | x | x |  |
| Pipeline-Ausführung | Kann die GoLive-Genehmigung bereitstellen. | x | x | x |  |
| Pipeline-Ausführung | Kann die Bereitstellung für die Produktion planen. | x | x | x |  |
| Pipeline löschen | Kann eine Pipeline löschen. |  | x |  |  |
| Ausführung abbrechen | Kann die aktuelle Ausführung abbrechen. |  | x |  |  |
| Persönliches Zugriffs-Token erstellen | Kann auf Git zugreifen. |  | x |  | x |

>[!NOTE]
>Ein Anwender kann mehreren Rollen zugewiesen werden. Wenn Sie beispielsweise einem Anwender die Rollen „Geschäftsinhaber“ und „Implementierungs-Manager“ zuweisen, erhalten diese die Kombination oder Summe dieser Berechtigungen.

## Cloud Manager-Programme {#cloud-manager-programs}

Cloud Manager-Programme stellen eine Reihe von Cloud Manager-Umgebungen dar, die logische Gruppen von Geschäftsinitiativen unterstützen. Diese entsprechen in der Regel einem erworbenen Service Level Agreement (SLA). Beispielsweise kann ein Programm die AEM-Ressourcen zur Unterstützung der globalen öffentlichen Websites darstellen, während ein anderes Programm ein internes zentrales DAM darstellt. Sehen Sie sich dieses [Video](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html?lang=de) an, um mehr über die Verwendung von Cloud Manager-Programmen zu erfahren.

Ein Benutzer kann ein **Sandbox-** oder ein **Produktionsprogramm** erstellen.

* Ein *Produktionsprogramm* wird erstellt, um Live-Traffic zum richtigen Zeitpunkt in der Zukunft zu aktivieren.
Weitere Informationen finden Sie unter [Einführung in Produktionsprogramme](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/production-programs/introduction-production-programs.html?lang=de).

* Ein *Sandbox-Programm* wird normalerweise für Schulungen, Demos, Aktivierungen, Konzeptnachweise oder Dokumentation erstellt. Es soll keinen Live-Traffic verarbeiten und hat Einschränkungen eingeführt, die ein Produktionsprogramm nicht hat. Es umfasst Sites und Assets und wird automatisch mit einer Git-Verzweigung geliefert, die Beispiel-Code, eine Entwicklungsumgebung und eine produktionsfremde Pipeline enthält.
Weitere Informationen finden Sie unter [Einführung in Sandbox-Programme](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/sandbox-programs/introduction-sandbox-programs.html?lang=de).

## Cloud Manager-Umgebungen {#cloud-manager-environments}

Ihre Cloud-Umgebungen werden über Cloud Manager erstellt, aufgerufen und angezeigt. Dabei kann es sich um eine Produktions-, Staging- oder Entwicklungsumgebung handeln. Verschiedene Umgebungen unterstützen unterschiedliche Zwecke und können mit verschiedenen CI/CD-Pipelines eingesetzt werden. Umgebungen bestehen aus Services wie:

* [AEM-Autoren-Services](#author-services)
* [AEM-Publishing-Services](#publish-services)
* [Dispatcher-Services](#dispatcher-services)

   >[!NOTE]
   > Weitere Informationen zu den verfügbaren Umgebungen finden Sie im Video [Verwenden von Adobe Cloud Manager-Umgebungen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html?lang=de#cloud-manager). Weitere Informationen zu den Umgebungstypen, die ein Benutzer erstellen kann, und dazu, wie der Benutzer eine Umgebung erstellen kann, finden Sie unter [Umgebungen verwalten](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html?lang=de).

### AEM-Authoring-Service {#author-services}

Der AEM-Authoring-Service ist in einer Umgebung enthalten, in der Website-Inhalte und digitale Assets erstellt, verwaltet und aktualisiert werden. In der Regel haben nur interne Benutzer Zugriff auf den Authoring-Service, der sich hinter einem Anmeldebildschirm befindet. Der Authoring-Service ist sowohl als Authoring- als auch als Vorschau-Umgebung konzipiert.

### AEM-Publishing-Service {#publish-services}

Der AEM-Publishing-Service ist in einer Umgebung wie einer Website enthalten, in der das Endbenutzererlebnis gehostet wird. Dies ist der Service, den Besucher der Website anzeigen und mit dem Sie interagieren. In der Regel ist der Publishing-Service öffentlich verfügbar.

### AEM-Dispatcher-Service {#dispatcher-services}

Der Dispatcher ist ein `Apache HTTP Web server`-Modul, das eine Sicherheits- und Leistungsschicht bietet, die sich vor dem AEM-Publishing-Service befindet.
