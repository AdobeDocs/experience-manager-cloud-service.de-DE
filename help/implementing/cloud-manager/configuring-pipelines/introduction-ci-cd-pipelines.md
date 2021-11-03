---
title: CI/CD Pipelines
description: Auf dieser Seite erfahren Sie mehr über CI/CD-Pipelines von Cloud Manager
index: false
source-git-commit: b6749b149e2166a6f2881817368e418d8b2adb00
workflow-type: tm+mt
source-wordcount: '826'
ht-degree: 3%

---


# CI/CD-Pipelines von Cloud Manager {#intro-cicd}

## Einführung {#introduction}

Eine CI/CD-Pipeline in Cloud Manager kann durch eine Art Ereignis ausgelöst werden, z. B. eine Pull-Anforderung aus einem Quellcode-Repository, d. h. eine Codeänderung oder eine Art regulärer Zeitplan, um eine Release-Cadence abzugleichen.

>[!NOTE]
>Zur Konfiguration der Pipeline müssen Sie:
>* den Trigger definieren, der die Pipeline starten soll
>* Parameter zur Steuerung der Produktionsbereitstellung definieren
>* Leistungstestparameter konfigurieren


In Cloud Manager gibt es zwei Arten von Pipelines:

* [Produktions-Pipeline](#prod-pipeline)
* [Produktionsfremde Pipeline](#non-prod-pipeline)

## Produktions-Pipeline {#prod-pipeline}

Eine Produktions-Pipelines ist eine speziell entwickelte Pipeline, die eine Reihe aufeinander abgestimmter Schritte umfasst, um Quellcode vollständig in die Produktion zu übernehmen. Zu den Schritten gehören das Erstellen, Verpacken, Testen, Validieren und Bereitstellen in allen Staging-Umgebungen. Eine Produktions-Pipeline kann selbstverständlich erst hinzugefügt werden, nachdem ein Satz aus Produktions- und Staging-Umgebung erstellt wurde.

Siehe [Konfigurieren einer Produktions-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) für weitere Details.


## Produktionsfremde Pipeline {#non-prod-pipeline}

Eine produktionsfremde Pipeline dient dazu, Code-Qualitätsprüfungen durchzuführen oder Quellcode in einer Entwicklungsumgebung bereitzustellen.

Siehe [Konfigurieren einer produktionsfremden Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) für weitere Details.

## Grundlegendes zu CI/CD-Pipelines in Cloud Manager {#understand-pipelines}

Die folgende Tabelle fasst alle Pipelines in Cloud Manager zusammen mit ihrer Verwendung zusammen.

| Pipeline-Typ | Bereitstellung oder Codequalität | Quell-Code | Verwendungsbereiche | Wann oder warum sollte ich verwenden? |
|--- |--- |--- |---|---|---|
| Produktion oder Nicht-Produktion | Bereitstellung | Front-End | So stellen Sie Frontend-Code bereit. Frontend-Code ist jeder Code, der als statische Datei bereitgestellt wird. Sie ist nicht mit dem von AEM bereitgestellten UI-Code identisch. Sie umfasst Sites-Designs, vom Kunden definierte SPA, Firefly-SPA und andere Lösungen. Muss in AEM Version vorliegen. | Schnelle Bereitstellungszeiten<br> Mehrere Front-End-Pipelines können konfiguriert und gleichzeitig pro Umgebung ausgeführt werden |
|  | Bereitstellung | Voller Stapel | Um die Back-End-, Front-End- und HTTPD/Dispatcher-Konfiguration gleichzeitig bereitzustellen, Es gelten einige Einschränkungen. | Wenn noch keine Frontend-Pipelines angenommen wurden. |
| Produktionsfremd | Code-Qualität | Front-End | Ausführen von Code-Qualitätsprüfungen für Frontend-Code | Schnelle Bereitstellungszeiten<br> Es können mehrere Pipelines konfiguriert und ausgeführt werden |
|  | Code-Qualität | Voller Stapel | Führen Sie eine Code-Qualitätsprüfung für den vollständigen Stack-Code durch. | Schnelle Bereitstellungszeiten<br> Es können mehrere Pipelines konfiguriert und ausgeführt werden |

Die folgende Abbildung zeigt Cloud Manager-Pipeline-Konfigurationen mit herkömmlichem Single-End-Repository oder unabhängigem Front-End-Repository-Setup:

![](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-configurations.png)

## Cloud Manager-Frontend-Pipelines {#front-end}

Frontend-Pipelines helfen Ihren Teams, Ihren Design- und Entwicklungsprozess zu optimieren, indem sie beschleunigte Front-End-Pipelines zur Bereitstellung von Frontend-Code aktivieren. Diese differenzierte Pipeline stellt JavaScript und CSS als Thema auf der AEM-Verteilungsschicht bereit, was zu einer neuen Designversion führt, die von Seiten referenziert werden kann, die von der AEM Laufzeit bereitgestellt werden. Frontend-Code ist jeder Code, der als statische Datei bereitgestellt wird. Sie ist nicht mit dem von AEM bereitgestellten UI-Code identisch. Sie umfasst Sites-Designs, vom Kunden definierte SPA, Firefly-SPA und andere Lösungen.

>[!NOTE]
>Ein Benutzer, der als Bereitstellungsmanager-Rolle angemeldet ist, kann mehrere Frontend-Pipelines gleichzeitig erstellen und ausführen. Es gibt jedoch eine Obergrenze von 300 Pipelines pro Programm (für alle Arten).

Diese können vom Typ Front-End-Codequalität oder Front-End-Bereitstellungs-Pipelines sein.

### Vor der Konfiguration von Frontend-Pipelines {#before-start}

Bevor Sie mit der Konfiguration der Front-End-Pipelines beginnen, lesen Sie AEM Journey zur schnellen Site-Erstellung , um einen End-to-End-Workflow mit dem einfach zu verwendenden AEM Tool zur schnellen Site-Erstellung zu erhalten. Diese Dokumentations-Website hilft Ihnen, die Front-End-Entwicklung Ihrer AEM-Site zu optimieren und Ihre Site ohne AEM Backend-Wissen schnell anzupassen.

### Konfigurieren Ihrer Front-End-Pipeline {#configure-front-end}

Informationen zum Konfigurieren der Frontend-Pipeline finden Sie unter:

* Hinzufügen einer Produktions-Pipeline
* Hinzufügen einer produktionsfremden Pipeline

## Vollständige Stapel-Pipelines {#full-stack-pipeline}

Die Full Stack-Pipeline bietet Benutzern die Möglichkeit, Back-End-, Front-End- und HTTPD/Dispatcher-Konfigurationen gleichzeitig bereitzustellen.  Es stellt Code und Inhalte für die AEM-Laufzeit bereit, einschließlich Frontend-Code (JavaScript/CSS), der als AEM Client-Bibliotheken gepackt ist. Es kann eine Webebenenkonfiguration bereitstellen, wenn keine Web-Tier-Pipeline konfiguriert ist. Dies stellt die &quot;uber&quot;-Pipeline dar und gibt Benutzern die Möglichkeit, ihren Frontend-Code oder ihre Dispatcher-Konfiguration ausschließlich über die Front End-Pipeline bzw. die Web Tier Config-Pipeline bereitzustellen.

Folgende Einschränkungen gelten:

1. Ein Benutzer muss als Bereitstellungsmanager angemeldet sein, um Pipelines konfigurieren oder ausführen zu können.

1. Es kann immer nur eine Full Stack Pipeline pro Umgebung geben.

1. Der Benutzer kann die vollständige Stack-Pipeline für eine Umgebung so konfigurieren, dass die Dispatcher-Konfiguration ignoriert oder nicht ignoriert wird. Wenn die entsprechende Web-Tier-Konfigurationspipeline für die Umgebung nicht vorhanden ist.

1. Die vollständige Stack-Pipeline für eine Umgebung ignoriert die Dispatcher-Konfiguration, wenn die entsprechende Web Tier Config-Pipeline für die Umgebung vorhanden ist.

Diese können vom Typ Full Stack - Code Quality oder Full Stack - Deployment-Pipeline sein.

### Konfigurieren der vollständigen Stapel-Pipeline {#configure-full-stack}

Informationen zum Konfigurieren der Full Stack Pipeline finden Sie unter:

* Hinzufügen einer Produktions-Pipeline
* Hinzufügen einer produktionsfremden Pipeline