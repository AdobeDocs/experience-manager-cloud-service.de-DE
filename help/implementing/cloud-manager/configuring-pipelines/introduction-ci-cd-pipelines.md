---
title: CI-CD Pipelines
description: Auf dieser Seite erfahren Sie mehr über CI/CD-Pipelines von Cloud Manager
index: true
source-git-commit: 3d48bd507305e7a1d3efa2b61123afdae1f52ced
workflow-type: tm+mt
source-wordcount: '1006'
ht-degree: 3%

---


# CI/CD-Pipelines von Cloud Manager {#intro-cicd}

## Einführung {#introduction}

Eine CI/CD-Pipeline in Cloud Manager kann durch eine Art Ereignis ausgelöst werden, z. B. eine Pull-Anforderung aus einem Quellcode-Repository, d. h. eine Codeänderung oder eine Art regulärer Zeitplan, um eine Release-Cadence abzugleichen.

>[!NOTE]
>Zur Konfiguration der Pipeline müssen Sie:
>* den Trigger definieren, der die Pipeline starten soll
>* define the parameters controlling the production deployment
>* Leistungstestparameter konfigurieren


In Cloud Manager gibt es zwei Arten von Pipelines:

* [Produktions-Pipeline](#prod-pipeline)
* [Produktionsfremde Pipeline](#non-prod-pipeline)

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/ci-cd-config1.png)


## Produktions-Pipeline {#prod-pipeline}

Eine Produktions-Pipelines ist eine speziell entwickelte Pipeline, die eine Reihe aufeinander abgestimmter Schritte umfasst, um Quellcode vollständig in die Produktion zu übernehmen. Zu den Schritten gehören das Erstellen, Verpacken, Testen, Validieren und Bereitstellen in allen Staging-Umgebungen. Eine Produktions-Pipeline kann selbstverständlich erst hinzugefügt werden, nachdem ein Satz aus Produktions- und Staging-Umgebung erstellt wurde.

Siehe [Konfigurieren einer Produktions-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) für weitere Details.


## Produktionsfremde Pipeline {#non-prod-pipeline}

Eine produktionsfremde Pipeline dient dazu, Code-Qualitätsprüfungen durchzuführen oder Quellcode in einer Entwicklungsumgebung bereitzustellen.

Refer to [Configuring a Non-Production Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) for more details.

## Grundlegendes zu CI/CD-Pipelines in Cloud Manager {#understand-pipelines}

Die folgende Tabelle fasst alle Pipelines in Cloud Manager zusammen mit ihrer Verwendung zusammen.

| Pipeline-Typ | Bereitstellung oder Codequalität | Quell-Code | Verwendungsbereiche | Wann oder warum sollte ich verwenden? |
|--- |--- |--- |---|---|
| Produktion oder Nicht-Produktion | Bereitstellung | Front-End | Schnelle Bereitstellungszeiten.<br>Es können mehrere Front-End-Pipelines konfiguriert und gleichzeitig pro Umgebung ausgeführt werden.<br>Der Front-End-Pipeline-Build sendet den Build an einen Speicher. When an html page is served it may reference Frontend Code static files which will be served by the CDN using this storage as an origin. | So stellen Sie ausschließlich Frontend-Code bereit, der eine oder mehrere clientseitige Benutzeroberflächenanwendungen enthält. Frontend-Code ist jeder Code, der als statische Datei bereitgestellt wird. Sie ist nicht mit dem von AEM bereitgestellten UI-Code identisch. Sie umfasst Sites-Designs, vom Kunden definierte SPA, Firefly-SPA und andere Lösungen.<br>Muss in AEM Version 2021.10.5933.20211012T154732Z sein<br>Muss Sites aktiviert haben. |
| Produktion oder Nicht-Produktion | Bereitstellung | Voller Stapel | When Front end pipelines have not yet  been adopted.<br>In Fällen, in denen der Frontend-Code genau zur gleichen Zeit wie der AEM Server-Code bereitgestellt werden muss. | Um AEM Server-Code (unveränderlicher Inhalt, Java-Code, OSGi-Konfigurationen, HTTPD/Dispatcher-Konfiguration, repoinit, veränderlicher Inhalt, Schriftarten) bereitzustellen, der eine oder mehrere AEM Serveranwendungen gleichzeitig enthält. |
| Produktionsfremd | Code-Qualität | Front-End | To have Cloud Manager evaluate. Ihren Build-Erfolg und Ihre Code-Qualität ohne Implementierung.<br>Multiple pipelines can be configured and run. | Run code quality scans on front end code. |
| Produktionsfremd | Code-Qualität | Full Stack | Damit Cloud Manager ausgewertet wird. Ihren Build-Erfolg und Ihre Code-Qualität ohne Implementierung.<br>Es können mehrere Pipelines konfiguriert und ausgeführt werden. | Führen Sie eine Überprüfung der Code-Qualität für den vollständigen Stack-Code durch. |


Die folgende Abbildung zeigt Cloud Manager-Pipeline-Konfigurationen mit herkömmlichem Single-End-Repository oder unabhängigem Front-End-Repository-Setup:

![](/help/implementing/cloud-manager/assets/configure-pipeline/cm-setup.png)

## Cloud Manager-Frontend-Pipelines {#front-end}

Frontend-Pipelines helfen Ihren Teams, Ihren Design- und Entwicklungsprozess zu optimieren, indem sie beschleunigte Front-End-Pipelines zur Bereitstellung von Frontend-Code aktivieren. Diese differenzierte Pipeline stellt JavaScript und CSS als Thema auf der AEM-Verteilungsschicht bereit, was zu einer neuen Designversion führt, die von Seiten referenziert werden kann, die von der AEM Laufzeit bereitgestellt werden. Frontend-Code ist jeder Code, der als statische Datei bereitgestellt wird. It is separate from UI code served by AEM. Sie umfasst Sites-Designs, vom Kunden definierte SPA, Firefly-SPA und andere Lösungen.

>[!IMPORTANT]
>Sie müssen AEM Version verwenden `2021.10.5933.20211012T154732Z ` , um Front-End-Pipelines zu nutzen.

>[!NOTE]
>Ein Benutzer, der als Bereitstellungsmanager-Rolle angemeldet ist, kann mehrere Frontend-Pipelines gleichzeitig erstellen und ausführen. Es gibt jedoch eine Obergrenze von 300 Pipelines pro Programm (für alle Arten).

These can be of the type Front End Code Quality or Front End Deployment pipelines.

### Vor der Konfiguration von Frontend-Pipelines {#before-start}

Bevor Sie mit der Konfiguration der Front-End-Pipelines beginnen, lesen Sie [Journey zur AEM SchnellSite-Erstellung](/help/journey-sites/quick-site/overview.md) für einen End-to-End-Workflow mit dem einfach zu verwendenden AEM Tool zur schnellen Site-Erstellung. This documentation site will help you streamline the front-end development of your AEM Site and quickly customize your site with no AEM backend knowledge.

### Konfigurieren einer Front-End-Pipeline {#configure-front-end}

Informationen zum Konfigurieren der Frontend-Pipeline finden Sie unter:

* [Adding a Production Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#adding-production-pipeline)
* [Hinzufügen einer produktionsfremden Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#adding-non-production-pipeline)

### Entwickeln von Sites mit der Frontend-Pipeline {#developing-with-front-end-pipeline}

Mit der Front-End-Pipeline erhalten die Frontend-Entwickler mehr Unabhängigkeit, und der Entwicklungsprozess kann erheblich an Geschwindigkeit gewinnen.

Refer to [this document](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md) for how this process works along with some considerations to be aware of in order to get the full potential out of this process.

## Full Stack Pipelines {#full-stack-pipeline}

Die Full Stack-Pipeline bietet Benutzern die Möglichkeit, Back-End-, Front-End- und HTTPD/Dispatcher-Konfigurationen gleichzeitig bereitzustellen.  Es stellt Code und Inhalte für die AEM-Laufzeit bereit, einschließlich Frontend-Code (JavaScript/CSS), der als AEM Client-Bibliotheken gepackt ist. Es kann eine Webebenenkonfiguration bereitstellen, wenn keine Web-Tier-Pipeline konfiguriert ist. Dies stellt die &quot;uber&quot;-Pipeline dar und gibt Benutzern die Möglichkeit, ihren Frontend-Code oder ihre Dispatcher-Konfiguration ausschließlich über die Front End-Pipeline bzw. die Web Tier Config-Pipeline bereitzustellen.
Diese können vom Typ Full Stack - Code Quality oder Full Stack - Deployment-Pipeline sein.

Folgende Einschränkungen gelten:

1. Ein Benutzer muss als Bereitstellungsmanager angemeldet sein, um Pipelines konfigurieren oder ausführen zu können.

1. At any time, there can only be one Full Stack pipeline per environment.

1. The user can configure the Full Stack pipeline for an environment to ignore or not to ignore the dispatcher configuration, If the corresponding Web Tier Config pipeline for the environment does not exist.

1. Die vollständige Stack-Pipeline für eine Umgebung ignoriert die Dispatcher-Konfiguration, wenn die entsprechende Web Tier Config-Pipeline für die Umgebung vorhanden ist.


### Konfigurieren einer vollständigen Stapel-Pipeline {#configure-full-stack}

Informationen zum Konfigurieren der Full Stack Pipeline finden Sie unter:

* [Hinzufügen einer Produktions-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#adding-production-pipeline)
* [Hinzufügen einer produktionsfremden Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#adding-non-production-pipeline)