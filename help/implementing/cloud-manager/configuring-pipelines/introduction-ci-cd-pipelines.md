---
title: Einführung in CI/CD-Pipelines
description: Erfahren Sie mehr über CI/CD-Pipelines in Cloud Manager und darüber, wie Sie mit diesen Ihren Code effizient bereitstellen können.
index: true
exl-id: 40d6778f-65e0-4612-bbe3-ece02905709b
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: bd129278f5885bd0eb1a25372bba80e863fcc5e7
workflow-type: tm+mt
source-wordcount: '1587'
ht-degree: 75%

---


# Cloud Manager CI/CD-Pipelines {#intro-cicd}

Erfahren Sie mehr über CI/CD(Continuous Integration/Continuous Delivery)-Pipelines in Cloud Manager und darüber, wie Sie mit diesen Ihren Code effizient bereitstellen können.

## Einführung in CI/CD-Pipelines {#introduction}

Eine CI/CD-Pipeline in Cloud Manager ist ein Mechanismus zum Erstellen von Code aus einem Quell-Repository und dessen Bereitstellung in einer Umgebung. Ein Ereignis löst eine Pipeline aus, z. B. eine Pull-Anfrage aus einem Quell-Code-Repository wie Git (d. h. eine Code-Änderung). Sie kann auch regelmäßig entsprechend einem Veröffentlichungsintervall ausgelöst werden.

Um eine Pipeline zu konfigurieren, müssen Sie wie folgt vorgehen:

* den Auslöser definieren, der die Pipeline startet
* die Parameter zur Steuerung der Produktionsbereitstellung definieren
* Die Leistungstestparameter konfigurieren.

Cloud Manager bietet zwei Pipelinetypen:

* [Produktions-Pipelines](#prod-pipeline)
* [Produktionsfremde Pipelines](#non-prod-pipeline)

![Pipeline-Typen](/help/implementing/cloud-manager/assets/configure-pipeline/ci-cd-config1.png)

## Produktions-Pipelines {#prod-pipeline}

Eine Produktions-Pipeline ist eine speziell entwickelte Pipeline, die eine Reihe aufeinander abgestimmter Schritte zum Bereitstellen von Quell-Code für die Verwendung in Produktionsumgebungen enthält. Die Schritte umfassen das Erstellen, Packen, Testen, Validieren und Bereitstellen in allen Staging-Umgebungen. Daher kann eine Produktions-Pipeline erst hinzugefügt werden, nachdem eine Gruppe von Produktions- und Staging-Umgebungen erstellt wurde.

>[!TIP]
>
>Siehe [Konfigurieren einer Produktions-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md).

## Produktionsfremde Pipelines {#non-prod-pipeline}

Eine produktionsfremde Pipeline dient dazu, Code-Qualitätsprüfungen durchzuführen oder Quell-Code in einer Entwicklungsumgebung bereitzustellen.

>[!TIP]
>
>Siehe [Konfigurieren einer produktionsfremden Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md).

## Code-Quellen {#code-sources}

Pipelines unterscheiden sich auch durch den Code, den sie bereitstellen, abgesehen von Produktions- und Nicht-Produktionsumgebungen.

* **[Full-Stack-Pipelines](#full-stack-pipeline)**: Diese Pipelines ermöglichen die gleichzeitige Bereitstellung von Backend- und Frontend-Codebuilds mit einer oder mehreren AEM-Server-Anwendungen zusammen mit HTTPD-/Dispatcher-Konfigurationen.
* **[Konfigurations-Pipelines](#config-deployment-pipeline)**: Sie können Konfigurationen für Funktionen wie Protokollweiterleitung und bereinigungsbezogene Wartungsaufgaben schnell bereitstellen. Dies umfasst zudem verschiedene CDN(Content Delivery Network)-Konfigurationen wie Traffic-Filterregeln, einschließlich Web Application Firewall(WAF)-Regeln. Darüber hinaus können Sie Anfrage- und Reaktionsumwandlungen, Ursprungs-Auswahl, Client-seitige Umleitungen, Fehlerseiten, CDN-Schlüssel, Bereinigungs-API-Schlüssel und grundlegende Authentifizierungsfunktionen verwalten. Weitere Informationen finden Sie unter [Verwenden von Konfigurations-Pipelines](/help/operations/config-pipeline.md).
* **[Frontend-Pipelines](#front-end)**: Diese Pipelines ermöglichen die Bereitstellung von Frontend-Codebuilds mit einer oder mehreren Client-seitigen Benutzeroberflächenanwendungen.
* **[Web-Stufen-Konfigurations-Pipelines](#web-tier-config-pipelines)**: Diese Pipelines ermöglichen die Bereitstellung von HTTPD-/Dispatcher-Konfigurationen.

Diese Pipeline-Typen werden später in diesem Dokument beschrieben.

### Grundlegendes zu CI/CD-Pipelines in Cloud Manager {#understand-pipelines}

In der folgenden Tabelle sind die in Cloud Manager verfügbaren Pipelines und deren Verwendungszwecke zusammengefasst.

| Pipeline-Typ | Bereitstellung oder Code-Qualität | Quell-Code | Zweck | Anmerkungen |
| --- | --- | --- | --- | ---|
| Produktion oder produktionsfremd | Bereitstellung | Full-Stack | Gleichzeitige Bereitstellung von Backend- und Frontend-Code-Builds zusammen mit HTTPD-/Dispatcher-Konfigurationen | Wird verwendet, wenn Frontend-Code gleichzeitig mit AEM-Servercode bereitgestellt werden muss. Wird verwendet, wenn Frontend-Pipelines oder Web-Stufen-Konfigurations-Pipelines noch nicht übernommen wurden. |
| Produktion oder produktionsfremd | Bereitstellung | Frontend | Bereitstellung von Frontend-Codebuilds, die eine oder mehrere Client-seitige Benutzeroberflächenanwendungen enthalten | Unterstützt mehrere gleichzeitige Frontend-Pipelines<br>Viel schneller als Full-Stack-Bereitstellungen. |
| Produktion oder produktionsfremd | Bereitstellung | Web-Stufen-Konfiguration | Bereitstellen von HTTPD-/Dispatcher-Konfigurationen | Bereitstellung in Minuten |
| Produktion oder produktionsfremd | Bereitstellung | Config | Stellt die [Konfiguration für eine Reihe von Funktionen](/help/operations/config-pipeline.md) bereit, die sich auf CDN-, Protokollweiterleitungs- und bereinigungsbezogene Wartungsaufgaben beziehen. | Bereitstellung in Minuten |
| Produktionsfremd | Code-Qualität | Full Stack | Führt Code-Qualitätsprüfungen für Full-Stack-Code ohne Bereitstellung durch | Unterstützt mehrere Pipelines |
| Produktionsfremd | Code-Qualität | Frontend | Führt Code-Qualitätsprüfungen für Frontend-Code ohne Bereitstellung durch | Unterstützt mehrere Pipelines |
| Produktionsfremd | Code-Qualität | Web-Stufen-Konfiguration | Führt Code-Qualitätsprüfungen für Dispatcher-Konfigurationen ohne Bereitstellung aus | Unterstützt mehrere Pipelines |

Die folgende Abbildung zeigt Pipeline-Konfigurationen in Cloud Manager mit traditionellen, einzelnen Frontend-Repository- oder unabhängigen Frontend-Repository-Setups.

![Cloud Manager-Pipeline-Konfigurationen](/help/implementing/cloud-manager/assets/configure-pipeline/cm-setup.png)

## Full-Stack-Pipelines {#full-stack-pipeline}

Full-Stack-Pipelines stellen Backend-Code, Frontend-Code und Web-Stufen-Konfigurationen für AEM Runtime gleichzeitig bereit.

* Backend-Code: Unveränderlicher Inhalt (Java-Code, OSGi-Konfigurationen, repoinit) und veränderlicher Inhalt
* Frontend-Code: Ressourcen der Programm-Benutzeroberfläche wie JavaScript, CSS, Schriftarten
* Web-Stufen-Konfiguration: HTTPD-/Dispatcher-Konfigurationen

Die Full-Stack-Pipeline stellt eine umfassende Pipeline dar. Sie verarbeitet alles gleichzeitig und ermöglicht es Benutzenden, ihren Frontend-Code oder ihre Dispatcher-Konfigurationen separat bereitzustellen. Diese Bereitstellung erfolgt über die Frontend-Pipeline bzw. die Web-Stufen-Konfigurations-Pipelines.

Full-Stack-Pipelines packen Frontend-Code (JavaScript/CSS) als [AEM Client-Bibliotheken](/help/implementing/developing/introduction/clientlibs.md).

Full-Stack-Pipelines stellen Web-Stufen-Konfigurationen bereit, wenn eine [Web-Stufen-Konfigurations](#web-tier-config-pipelines)Pipeline nicht konfiguriert ist.

Folgende Einschränkungen gelten.

* Ein Benutzer muss mit der Rolle „Bereitstellungs **Manager“ angemeldet sein** um Pipelines konfigurieren oder ausführen zu können.
* Es kann immer nur eine Full-Stack-Pipeline pro Umgebung geben.

Achten Sie außerdem darauf, wie sich die Full-Stack-Pipeline verhält, wenn Sie eine [Web-Stufen-Konfigurations-Pipeline](#web-tier-config-pipelines) einführen.

* Die Full-Stack-Pipeline für eine Umgebung ignoriert die Dispatcher-Konfiguration, wenn die entsprechende Web-Stufen-Konfigurations-Pipeline vorhanden ist.
* Um die Dispatcher-Konfiguration einzuschließen oder zu ignorieren, kann der Benutzer die Full-Stack-Pipeline konfigurieren, wenn die entsprechende Web-Stufen-Konfigurations-Pipeline für die Umgebung nicht vorhanden ist.

Full-Stack-Pipelines können Pipelines zur Code-Qualitätsprüfung oder für die Bereitstellung sein.

### Konfigurieren von Full-Stack-Pipelines {#configure-full-stack}

Siehe [Hinzufügen einer Produktions-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#full-stack-code).
Siehe [Hinzufügen einer produktionsfremden Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#full-stack-code).

## Konfigurations-Pipelines {#config-deployment-pipeline}

Mithilfe einer Konfigurations-Pipeline können Sie Einstellungen für die Protokollweiterleitung, bereinigungsbezogene Wartungsaufgaben sowie verschiedene CDN-Konfigurationen schnell bereitstellen, einschließlich Traffic-Filterregeln (z. B. WAF(Web Application Firewall)-Regeln). Darüber hinaus können Sie Anfrage- und Reaktionsumwandlungen, Ursprungs-Auswahl, Client-seitige Umleitungen, Fehlerseiten, kundenseitig verwaltete CDN-Schlüssel, Bereinigungs-API-Schlüssel und grundlegende Authentifizierungsfunktionen verwalten.

Unter [Verwenden von Konfigurations-Pipelines](/help/operations/config-pipeline.md) finden Sie eine umfassende Liste der unterstützten Funktionen und erfahren, wie Sie die Konfigurationen in Ihrem Repository verwalten, damit sie ordnungsgemäß bereitgestellt werden.

>[!NOTE]
>
>Edge Delivery-Konfigurations-Pipelines verfügen über keine separaten Entwicklungs-, Staging- und Produktionsumgebungen. In AEM as a Cloud Service durchlaufen die Änderungen Entwicklungs-, Staging- und Produktionsebenen. Eine Edge Delivery-Konfigurations-Pipeline wendet ihre Konfiguration dagegen direkt auf alle in Cloud Manager registrierten Edge Delivery Sites-Domains an. Weitere Informationen finden Sie unter [Hinzufügen einer Edge Delivery-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-edge-delivery-pipeline.md).


### Konfigurieren von Produktions-Pipelines {#configure-config-deployment}

Siehe [Hinzufügen einer Produktions-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#targeted-deployment).
Siehe [Hinzufügen einer produktionsfremden Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#targeted-deployment).

## Frontend-Pipelines {#front-end}

Frontend-Code ist jeder Code, der als statische Dateien bereitgestellt wird. Sie ist vom Benutzeroberflächen-Code, der von AEM bereitgestellt wird, getrennt und umfasst Site-Designs, kundendefinierte SPAs, SPAs und andere Lösungen.

Frontend-Pipelines helfen Ihren Teams, Ihren Design- und Entwicklungsprozess zu optimieren, indem sie eine beschleunigte Bereitstellung von Frontend-Code ermöglichen, asynchron von der Backend-Entwicklung. Diese dedizierte Pipeline stellt JavaScript und CSS als Design auf der AEM-Verteilungsebene bereit, was zu einer neuen Design-Version führt, die von Seiten referenziert wird, die von AEM bereitgestellt werden.

>[!NOTE]
>
>Eine Benutzerin bzw. ein Benutzer mit der Rolle **Bereitstellungs-Manager** kann mehrere Frontend-Pipelines gleichzeitig erstellen und ausführen.
>
>Es gibt jedoch eine Obergrenze von 300 Pipelines pro Programm (für alle Arten).

Frontend-Pipelines können Pipelines zur Code-Qualitätsprüfung oder Bereitstellung sein.

### Vor der Konfiguration von Frontend-Pipelines {#before-start}

Bevor Sie Frontend-Pipelines konfigurieren, lesen Sie die [Tour zur schnellen AEM-Site-Erstellung](/help/journey-sites/quick-site/overview.md). Dort erhalten Sie eine durchgängige Anleitung für das benutzerfreundliche Tool zur schnellen AEM-Site-Erstellung. Diese Tour hilft Ihnen, Ihre Frontend-Entwicklung zu optimieren und Ihre Site ohne AEM-Backend-Kenntnisse schnell anzupassen.

### Konfigurieren einer Frontend-Pipeline {#configure-front-end}

Siehe [Hinzufügen einer Produktions-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#adding-production-pipeline).
Siehe [Hinzufügen einer produktionsfremden Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#adding-non-production-pipeline).

### Entwickeln von Sites mit der Frontend-Pipeline {#developing-with-front-end-pipeline}

Mit Frontend-Pipelines erhalten Frontend-Entwickelnde mehr Unabhängigkeit, und der Entwicklungsprozess kann beschleunigt werden.

Unter [Entwickeln von Sites mit der Frontend-Pipeline](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md) finden Sie Informationen zur Funktionsweise dieses Prozesses sowie einige Überlegungen, die Sie beachten sollten, um das Potenzial dieses Prozesses zu maximieren.

## Web-Stufen-Konfigurations-Pipelines {#web-tier-config-pipelines}

Web-Stufen-Konfigurations-Pipelines ermöglichen die exklusive Bereitstellung der HTTPD-/Dispatcher-Konfiguration zur AEM-Runtime, indem sie sie von anderen Code-Änderungen entkoppeln. Es handelt sich dabei um eine optimierte Pipeline, die Benutzenden, die nur Dispatcher-Konfigurationsänderungen bereitstellen möchten, eine beschleunigte Möglichkeit bietet, dies zu tun.

>[!TIP]
>
>Mit Web-Stufen-Konfigurations-Pipelines können Sie Ihre Web-Konfiguration an demselben oder einem anderen Quellspeicherort wie die Full-Stack-Pipeline speichern, je nachdem, was für Ihre Projektstruktur am besten ist.

Folgende Einschränkungen gelten.

* Sie müssen die AEM-Version `2021.12.6151.20211217T120950Z` oder höher verwenden, um Web-Stufen-Konfigurations-Pipelines nutzen zu können.
* Sie müssen [in den flexiblen Modus der Dispatcher-Tools](/help/implementing/dispatcher/disp-overview.md#validation-debug) wechseln, um Web-Stufen-Konfigurations-Pipelines nutzen zu können.
* Ein Benutzer muss mit der Rolle „Bereitstellungs **Manager“ angemeldet sein** um Pipelines konfigurieren oder ausführen zu können.
* Es kann immer nur eine Web-Ebenen-Konfigurations-Pipeline pro Umgebung geben.
* Benutzende können eine Web-Ebenen-Konfigurations-Pipeline nicht konfigurieren, wenn die entsprechende Full-Stack-Pipeline ausgeführt wird.
* Die Web-Stufen-Struktur muss der in [ Dispatcher in der Cloud definierten flexiblen Modusstruktur ](/help/implementing/dispatcher/disp-overview.md#validation-debug).

Außerdem sollten Sie darauf achten, wie sich die [Full-Stack-Pipeline](#full-stack-pipeline) bei der Einführung einer Web-Stufen-Pipeline verhält.

* Wenn für eine Umgebung keine Web-Stufen-Konfigurations-Pipeline eingerichtet ist, kann die Benutzerin oder der Benutzer beim Konfigurieren der Full-Stack-Pipeline wählen, ob die Dispatcher-Konfiguration einbezogen oder ignoriert werden soll. Diese Auswahl erfolgt während der Ausführung und Bereitstellung.
* Sobald eine Web-Stufen-Konfigurations-Pipeline für eine Umgebung konfiguriert wurde, ignoriert die entsprechende Full-Stack-Pipeline (sofern vorhanden) die Dispatcher-Konfiguration während der Ausführung und Bereitstellung.
* Nachdem eine Web-Stufen-Konfigurations-Pipeline gelöscht wurde, wird die zugehörige Full-Stack-Pipeline zurückgesetzt, um während der Ausführung Dispatcher-Konfigurationen bereitzustellen.

Web-Stufen-Konfigurations-Pipelines können vom Typ `Code quality` oder `Deployment` sein.

### Konfigurieren von Web-Stufen-Pipelines {#configure-web-tier}

Siehe [Hinzufügen einer Produktions-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#targeted-deployment).
Siehe [Hinzufügen einer produktionsfremden Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#targeted-deployment).

## Videoüberblick über Pipeline-Typen {#video}

Einen schnellen Überblick über Pipeline-Typen erhalten Sie im folgenden Video (2 Minuten, 26 Sekunden).

>[!VIDEO](https://video.tv.adobe.com/v/342363)
