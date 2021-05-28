---
title: Erfahren Sie mehr über Cloud Manager
description: Auf dieser Seite erfahren Sie mehr über Cloud Manager, Cloud Manager-Programme und -Umgebungen.
source-git-commit: 58d4626da9fccd405cbc32d4a562641359352157
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 20%

---


# Einführung in Cloud Manager {#intro-cloud-manager}

Cloud Manager ist eine wesentliche Komponente von AEM als Cloud Service und dient als zentraler Einstiegspunkt für Ihr Team.

Zur Unterstützung von Kunden mit Enterprise-Entwicklungs-Setups integriert AEM as a Cloud Service vollständig in Cloud Manager und die speziell hierfür vorgesehenen CI/CD-Pipelines. Diese sind mit umfassenden Tests und höchster Code-Qualität ausgestattet und bieten außergewöhnliche Erlebnisse.

Um sicherzustellen, dass Kunden schnell mit AEM as a Cloud Service beginnen können, bietet Cloud Manager alles, was für die ersten Schritte auf Self-Service-Art erforderlich ist, einschließlich der Möglichkeit, Cloud-Ressourcen und -Umgebungen zu erstellen. Auf diese Weise können Ihre AEM-Entwickler über Cloud Manager auf das Git-Repository zugreifen. Mithilfe von Cloud Manager können Entwicklungsteams häufig darauf hinarbeiten, Änderungen auf Self-Service-Weise zu übernehmen.

Ihr Systemadministrator ist für die Einrichtung Ihres Cloud Manager-Teams verantwortlich, das auch Personen umfasst, die Ihre Cloud-Ressourcen und -Entwickler erstellen. Unter [Einrichten der Enterprise-Team-Entwicklung für AEM as a Cloud Service](/help/implementing/cloud-manager/enterprise-team-dev-setup.md) erfahren Sie, wie Cloud Manager bei der Einrichtung der Enterprise-Team-Entwicklung unterstützt.

## Cloud Manager-Programme {#cloud-manager-programs}

Cloud Manager-Programme stellen eine Reihe von Cloud Manager-Umgebungen dar, die logische Gruppen von Geschäftsinitiativen unterstützen. Diese entsprechen in der Regel einem erworbenen Service Level Agreement (SLA). Beispielsweise kann ein Programm die AEM Ressourcen zur Unterstützung der globalen öffentlichen Websites darstellen, während ein anderes Programm einen internen zentralen DAM darstellt. Sehen Sie sich dieses Video an, um mehr zu erfahren.

Ein Benutzer kann ein **Sandbox-** oder ein **Produktionsprogramm** erstellen.

* Ein *Produktionsprogramm* wird erstellt, um Live-Traffic zum richtigen Zeitpunkt in der Zukunft zu aktivieren.
Weitere Informationen finden Sie unter [Einführung in Produktionsprogramme](/help/onboarding/getting-access-to-aem-in-cloud/introduction-production-programs.md).

* Ein *Sandbox-Programm* wird normalerweise für Schulungen, Demos, Aktivierungen, Konzeptnachweise oder Dokumentation erstellt. Es soll keinen Live-Traffic verarbeiten und hat Einschränkungen eingeführt, die ein Produktionsprogramm nicht hat. Es umfasst Sites und Assets und wird automatisch mit einer Git-Verzweigung geliefert, die Beispielcode, eine Entwicklungsumgebung und eine produktionsfremde Pipeline enthält.
Weitere Informationen finden Sie unter [Einführung in Sandbox-Programme](/help/onboarding/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md).

## Cloud Manager-Umgebungen {#cloud-manager-environments}

Ihre Cloud-Umgebungen werden über Cloud Manager erstellt, aufgerufen und angezeigt. Dabei kann es sich um eine Produktions-, Staging- oder Entwicklungsumgebung handeln. Verschiedene Umgebungen unterstützen unterschiedliche Zwecke und können mit verschiedenen CI/CD-Pipelines interagiert werden. Umgebungen bestehen aus Diensten wie:

* [AEM-Autorendienste](#author-services)
* [AEM Publish Services](publish-services)
* [Dispatcher Services](#dispatcher-services)

   >[!NOTE]
   > Weitere Informationen zu den verfügbaren Umgebungen finden Sie im Video [Verwenden von Adobe Cloud Manager-Umgebungen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html?lang=en#cloud-manager) . Weitere Informationen zu den Umgebungstypen, die ein Benutzer erstellen kann, und dazu, wie der Benutzer eine Umgebung erstellen kann, finden Sie unter [Umgebungen verwalten](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html?lang=de) .

### AEM-Autorendienst {#author-services}

Der AEM-Autorendienst ist in einer Umgebung enthalten, in der Site-Inhalte und digitale Assets erstellt, verwaltet und aktualisiert werden. In der Regel haben nur interne Benutzer Zugriff auf den Autorendienst und befinden sich hinter einem Anmeldebildschirm. Der Authoring-Dienst ist sowohl als Authoring- als auch als Vorschau-Umgebung konzipiert.

### AEM-Veröffentlichungsdienst {#publish-services}

Der AEM-Veröffentlichungsdienst ist in einer Umgebung wie einer Website enthalten, in der das Endbenutzererlebnis gehostet wird. Dies ist der Dienst, den Besucher der Site anzeigen und damit interagieren. In der Regel ist der Veröffentlichungsdienst öffentlich verfügbar.

### AEM Dispatcher-Dienst {#dispatcher-services}

Der Dispatcher ist ein `Apache HTTP Web server`-Modul, das eine Sicherheits- und Leistungsschicht bietet, die sich vor dem AEM Publish Service befindet.