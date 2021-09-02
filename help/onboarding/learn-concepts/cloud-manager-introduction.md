---
title: Erfahren Sie mehr über Cloud Manager
description: Auf dieser Seite erfahren Sie mehr über Cloud Manager, Cloud Manager-Programme und -Umgebungen.
exl-id: b743f126-b34e-4f48-a3f0-5dbd4e1ac34e
source-git-commit: a37b460d467e6e86394ae4baa61f044486c73b24
workflow-type: tm+mt
source-wordcount: '756'
ht-degree: 23%

---

# Einführung in Cloud Manager {#intro-cloud-manager}

Cloud Manager ist eine wesentliche Komponente von AEM als Cloud Service und dient als zentraler Einstiegspunkt für Ihr Team.

Zur Unterstützung von Kunden mit Enterprise-Entwicklungs-Setups integriert AEM as a Cloud Service vollständig in Cloud Manager und die speziell hierfür vorgesehenen CI/CD-Pipelines. Diese sind mit umfassenden Tests und höchster Code-Qualität ausgestattet und bieten außergewöhnliche Erlebnisse.

Um sicherzustellen, dass Kunden schnell mit AEM as a Cloud Service beginnen können, bietet Cloud Manager alles, was für die ersten Schritte auf Self-Service-Art erforderlich ist, einschließlich der Möglichkeit, Cloud-Ressourcen und -Umgebungen zu erstellen. Auf diese Weise können Ihre AEM-Entwickler über Cloud Manager auf das Git-Repository zugreifen. Mithilfe von Cloud Manager können Entwicklungsteams häufig darauf hinarbeiten, Änderungen auf Self-Service-Weise zu übernehmen.

Ihr Systemadministrator ist für die Einrichtung Ihres Cloud Manager-Teams verantwortlich, das auch Personen umfasst, die Ihre Cloud-Ressourcen und -Entwickler erstellen. Unter [Einrichten der Enterprise-Team-Entwicklung für AEM as a Cloud Service](/help/implementing/cloud-manager/enterprise-team-dev-setup.md) erfahren Sie, wie Cloud Manager bei der Einrichtung der Enterprise-Team-Entwicklung unterstützt.

## Navigieren zur Übersichtsseite von Cloud Manager {#navigate-cloud-manager}

Gehen Sie wie folgt vor, um zu Cloud Manager zu navigieren:

1. Navigieren Sie von [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) direkt zur Anmeldeseite von Cloud Manager.

   >[!NOTE]
   >Bitte Lesezeichen für diese Seite einfügen, um Sie bei der Navigation zur Landingpage von Cloud Manager zu unterstützen.

1. Wählen Sie auf der Seite **Programme und Produkte** von Cloud Manager das Programm aus, um die Seite **Übersicht** zu öffnen.

Darüber hinaus können Sie von der Adobe Experience Cloud-Startseite aus zur Seite Programme und Produkte von Cloud Manager navigieren. Führen Sie dazu folgende Schritte durch:

1. Navigieren Sie direkt zu [Adobe Experience Cloud](https://experience.adobe.com/#/@foundationinternal/home) und melden Sie sich mit Ihrer Adobe ID an.

1. Wählen Sie **Experience Manager** aus.

1. Klicken Sie auf der Karte „Cloud Manager“ auf **Launch**. Nachdem Sie sich erfolgreich bei Cloud Manager angemeldet haben, können Sie die Benutzeroberfläche verwenden.

   Nach erfolgreicher Anmeldung werden Sie zur Landingpage von Cloud Manager weitergeleitet.

## Cloud Manager-Programme {#cloud-manager-programs}

Cloud Manager-Programme stellen eine Reihe von Cloud Manager-Umgebungen dar, die logische Gruppen von Geschäftsinitiativen unterstützen. Diese entsprechen in der Regel einem erworbenen Service Level Agreement (SLA). Beispielsweise kann ein Programm die AEM Ressourcen zur Unterstützung der globalen öffentlichen Websites darstellen, während ein anderes Programm einen internen zentralen DAM darstellt. Sehen Sie sich dieses [Video](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html?lang=en) an, um mehr über die Verwendung von Cloud Manager-Programmen zu erfahren.

Ein Benutzer kann ein **Sandbox-** oder ein **Produktionsprogramm** erstellen.

* Ein *Produktionsprogramm* wird erstellt, um Live-Traffic zum richtigen Zeitpunkt in der Zukunft zu aktivieren.
Weitere Informationen finden Sie unter [Einführung in Produktionsprogramme](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/production-programs/introduction-production-programs.html?lang=en).

* Ein *Sandbox-Programm* wird normalerweise für Schulungen, Demos, Aktivierungen, Konzeptnachweise oder Dokumentation erstellt. Es soll keinen Live-Traffic verarbeiten und hat Einschränkungen eingeführt, die ein Produktionsprogramm nicht hat. Es umfasst Sites und Assets und wird automatisch mit einer Git-Verzweigung geliefert, die Beispiel-Code, eine Entwicklungsumgebung und eine produktionsfremde Pipeline enthält.
Weitere Informationen finden Sie unter [Einführung in Sandbox-Programme](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/sandbox-programs/introduction-sandbox-programs.html?lang=en).

## Cloud Manager-Umgebungen {#cloud-manager-environments}

Ihre Cloud-Umgebungen werden über Cloud Manager erstellt, aufgerufen und angezeigt. Dabei kann es sich um eine Produktions-, Staging- oder Entwicklungsumgebung handeln. Verschiedene Umgebungen unterstützen unterschiedliche Zwecke und können mit verschiedenen CI/CD-Pipelines interagiert werden. Umgebungen bestehen aus Diensten wie:

* [AEM-Autorendienste](#author-services)
* [AEM Publish Services](#publish-services)
* [Dispatcher Services](#dispatcher-services)

   >[!NOTE]
   > Weitere Informationen zu den verfügbaren Umgebungen finden Sie im Video [Verwenden von Adobe Cloud Manager-Umgebungen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html?lang=de#cloud-manager) . Weitere Informationen zu den Umgebungstypen, die ein Benutzer erstellen kann, und dazu, wie der Benutzer eine Umgebung erstellen kann, finden Sie unter [Umgebungen verwalten](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html?lang=de) .

### AEM-Autorendienst {#author-services}

Der AEM-Autorendienst ist in einer Umgebung enthalten, in der Site-Inhalte und digitale Assets erstellt, verwaltet und aktualisiert werden. In der Regel haben nur interne Benutzer Zugriff auf den Autorendienst und befinden sich hinter einem Anmeldebildschirm. Der Authoring-Dienst ist sowohl als Authoring- als auch als Vorschau-Umgebung konzipiert.

### AEM Publish Service {#publish-services}

Der AEM-Veröffentlichungsdienst ist in einer Umgebung wie einer Website enthalten, in der das Endbenutzererlebnis gehostet wird. Dies ist der Dienst, den Besucher der Site anzeigen und damit interagieren. In der Regel ist der Veröffentlichungsdienst öffentlich verfügbar.

### AEM Dispatcher-Dienst {#dispatcher-services}

Der Dispatcher ist ein `Apache HTTP Web server`-Modul, das eine Sicherheits- und Leistungsschicht bietet, die sich vor dem AEM Publish Service befindet.
