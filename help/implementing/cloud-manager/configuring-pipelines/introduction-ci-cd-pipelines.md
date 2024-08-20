---
title: CI/CD-Pipelines
description: Erfahren Sie mehr über die CI/CD-Pipelines von Cloud Manager und wie sie zur effizienten Bereitstellung Ihres Codes verwendet werden können.
index: true
exl-id: 40d6778f-65e0-4612-bbe3-ece02905709b
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: f4c6331491bb08e81964476ad58065c1ee022967
workflow-type: tm+mt
source-wordcount: '1482'
ht-degree: 40%

---


# CI/CD-Pipelines in Cloud Manager {#intro-cicd}

Erfahren Sie mehr über die CI/CD-Pipelines von Cloud Manager (Continuous Integration/Continuous Delivery) und wie sie zur effizienten Bereitstellung Ihres Codes verwendet werden können.

## Einführung {#introduction}

Eine CI/CD-Pipeline in Cloud Manager ist ein Mechanismus zum Erstellen von Code aus einem Quell-Repository und dessen Bereitstellung in einer Umgebung. Ein Ereignis Trigger eine Pipeline, z. B. eine Pull-Anforderung aus einem Quellcode-Repository wie Git (d. h. eine Codeänderung). Oder sie kann in einem regulären Zeitplan ausgelöst werden, um eine Release-Kadenz abzugleichen.

Um eine Pipeline zu konfigurieren, müssen Sie folgende Schritte ausführen:

* Definieren Sie den Trigger, der die Pipeline startet.
* Definieren Sie die Parameter, die die Produktionsbereitstellung steuern.
* Die Leistungstestparameter konfigurieren.

Cloud Manager bietet zwei Pipelinetypen:

* [Produktions-Pipelines](#prod-pipeline)
* [Produktionsfremde Pipelines](#non-prod-pipeline)

![Pipelinetypen](/help/implementing/cloud-manager/assets/configure-pipeline/ci-cd-config1.png)

## Produktions-Pipelines {#prod-pipeline}

Eine Produktions-Pipeline ist eine speziell entwickelte Pipeline, die eine Reihe aufeinander abgestimmter Schritte zum Bereitstellen von Quell-Code für die Verwendung in Produktionsumgebungen enthält. Die Schritte umfassen das Erstellen, Packen, Testen, Validieren und Bereitstellen in allen Staging-Umgebungen. Daher kann eine Produktions-Pipeline erst hinzugefügt werden, nachdem eine Reihe von Produktions- und Staging-Umgebungen erstellt wurde.

>[!TIP]
>
>Siehe [Konfigurieren einer Produktions-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md).

## Produktionsfremde Pipelines {#non-prod-pipeline}

Eine produktionsfremde Pipeline dient hauptsächlich dazu, Code-Qualitätsprüfungen durchzuführen oder Quell-Code in einer Entwicklungsumgebung bereitzustellen.

>[!TIP]
>
>Siehe [Konfigurieren einer Nicht-Produktions-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md).

## Codequellen {#code-sources}

Pipelines können zusätzlich zu Produktions- und Nicht-Produktionsumgebungen auch nach dem Typ des von ihnen bereitgestellten Codes unterschiedlich sein.

* **[Vollständige Stapel-Pipelines](#full-stack-pipeline)** - Stellen Sie gleichzeitig Back-End- und Front-End-Code-Builds bereit, die eine oder mehrere AEM Serveranwendungen zusammen mit HTTPD/Dispatcher-Konfigurationen enthalten.
* **[Konfigurations-Pipelines](#config-deployment-pipeline)** - Sie können Konfigurationen für Funktionen wie die Protokollweiterleitung und Bereinigungsaufgaben schnell bereitstellen. Es enthält auch verschiedene CDN (Content Delivery Network)-Konfigurationen, wie z. B. Traffic-Filterregeln, einschließlich Web Application Firewall (WAF)-Regeln. Darüber hinaus können Sie Anforderungs- und Antworttransformationen, Herkunftsselektoren, clientseitige Umleitungen, Fehlerseiten, CDN-Schlüssel, API-Schlüssel für die Bereinigung und einfache Authentifizierung verwalten. Weitere Informationen finden Sie unter [Verwenden von Konfigurations-Pipelines](/help/operations/config-pipeline.md) .
* **[Frontend-Pipelines](#front-end)** - Stellen Sie Frontend-Code-Builds bereit, die eine oder mehrere clientseitige Anwendungen enthalten.
* **[Web-Tier-Konfigurationspipelines](#web-tier-config-pipelines)** - Bereitstellung von HTTPD-/Dispatcher-Konfigurationen.

Diese Pipelinetypen werden weiter unten in diesem Dokument ausführlich beschrieben.

### CI/CD-Pipelines in Cloud Manager {#understand-pipelines}

In der folgenden Tabelle sind die in Cloud Manager verfügbaren Pipelines und deren Verwendungszwecke zusammengefasst.

| Pipeline-Typ | Bereitstellung oder Code-Qualität | Source-Code | Zweck | Anmerkungen |
| --- | --- | --- | --- | ---|
| Produktion oder Nichtproduktion | Bereitstellung | Full-Stack | Gleichzeitige Bereitstellung von Backend- und Frontend-Code-Builds zusammen mit HTTPD-/Dispatcher-Konfigurationen | Wird verwendet, wenn Frontend-Code gleichzeitig mit AEM Server-Code bereitgestellt werden muss. Wird verwendet, wenn die Frontend-Pipelines oder Web-Tier-Konfigurationspipelines noch nicht übernommen wurden. |
| Produktion oder Nichtproduktion | Bereitstellung | Frontend | Bereitstellung von Frontend-Code-Builds, die eine oder mehrere Client-seitige Benutzeroberflächenanwendungen enthalten | Unterstützt mehrere gleichzeitige Front-End-Pipelines<br>viel schneller als vollständige Implementierungen. |
| Produktion oder Nichtproduktion | Bereitstellung | Web-Tier-Konfiguration | Bereitstellen von HTTPD-/Dispatcher-Konfigurationen | Bereitstellung in Minuten |
| Produktion oder Nichtproduktion | Bereitstellung | Config | Stellt die [Konfiguration für eine Reihe von Funktionen](/help/operations/config-pipeline.md) bereit, die sich auf CDN-, Protokollweiterleitungs- und bereinigungsbezogene Wartungsaufgaben beziehen. | Bereitstellung in Minuten |
| Nicht Produktion | Codequalität | Vollständiger Stapel | Führt Code-Qualitätsprüfungen für Full-Stack-Code ohne Bereitstellung durch | Unterstützt mehrere Pipelines |
| Produktionsfremd | Codequalität | Frontend | Führt Code-Qualitätsprüfungen für Frontend-Code ohne Bereitstellung durch | Unterstützt mehrere Pipelines |
| Produktionsfremd | Codequalität | Web-Tier-Konfiguration | Führt Code-Qualitätsprüfungen für Dispatcher-Konfigurationen ohne Implementierung durch | Unterstützt mehrere Pipelines |

Die folgende Abbildung zeigt Pipeline-Konfigurationen in Cloud Manager mit traditionellen, einzelnen Frontend-Repository- oder unabhängigen Frontend-Repository-Setups.

![Cloud Manager-Pipeline-Konfigurationen](/help/implementing/cloud-manager/assets/configure-pipeline/cm-setup.png)

## Vollstapelpipelines {#full-stack-pipeline}

Vollstapel-Pipelines stellen gleichzeitig Backend-Code-, Front-End-Code- und Webebenenkonfigurationen für die AEM-Laufzeit bereit.

* Backend-Code: Unveränderliche Inhalte wie Java-Code, OSGi-Konfigurationen, RepoInit sowie veränderliche Inhalte
* Frontend-Code: Ressourcen der Programm-Benutzeroberfläche wie JavaScript, CSS, Schriftarten
* Web-Stufen-Konfiguration: HTTPD-/Dispatcher-Konfigurationen

Die Full-Stack-Pipeline stellt eine Uber-Pipeline dar. Es verarbeitet alles gleichzeitig und ermöglicht es Benutzern, ihren Frontend-Code oder ihre Dispatcher-Konfigurationen separat bereitzustellen. Diese Bereitstellung erfolgt über die Front-End-Pipeline und die Web-Tier-Konfigurationspipelines.

Full-Stack-Pipelines packen Frontend-Code (JavaScript/CSS) als [AEM Client-Bibliotheken](/help/implementing/developing/introduction/clientlibs.md).

Full-Stack-Pipelines können Web-Stufen-Konfigurationen bereitstellen, wenn eine [Web-Stufen-Konfigurations-Pipeline](#web-tier-config-pipelines) nicht konfiguriert ist.

Folgende Einschränkungen gelten.

* Eine Benutzerin bzw. ein Benutzer muss mit der Rolle **Bereitstellungs-Manager** angemeldet sein, um Pipelines konfigurieren oder ausführen zu können.
* Es kann immer nur eine Full-Stack-Pipeline pro Umgebung geben.

Achten Sie außerdem darauf, wie sich die Full-Stack-Pipeline verhält, wenn Sie eine [Web-Stufen-Konfigurations-Pipeline](#web-tier-config-pipelines) einführen.

* Die Vollstack-Pipeline für eine Umgebung ignoriert die Dispatcher-Konfiguration, wenn die entsprechende Web-Tier-Konfigurationspipeline vorhanden ist.
* Wenn die entsprechende Web-Stufen-Konfigurations-Pipeline für die Umgebung nicht vorhanden ist, kann der Benutzer die Full-Stack-Pipeline so konfigurieren, dass sie die Dispatcher-Konfiguration einschließt oder ignoriert.

Full-Stack-Pipelines können Pipelines zur Code-Qualitätsprüfung oder für die Bereitstellung sein.

### Konfigurieren von Vollstapelpipelines {#configure-full-stack}

Siehe [Hinzufügen einer Produktions-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#full-stack-code).
Siehe [Hinzufügen einer Nicht-Produktions-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#full-stack-code).

## Konfigurations-Pipelines {#config-deployment-pipeline}

Mithilfe einer Konfigurationspipeline können Sie Einstellungen für die Protokollweiterleitung, Bereinigungsaufgaben sowie verschiedene CDN-Konfigurationen schnell bereitstellen, einschließlich Traffic-Filterregeln (wie WAF (Web Application Firewall)-Regeln). Darüber hinaus können Sie Anforderungs- und Antworttransformationen, Ursprungsselektoren, clientseitige Umleitungen, Fehlerseiten, kundenverwaltete CDN-Schlüssel, Bereinigungs-API-Schlüssel und einfache Authentifizierung verwalten.

Unter [Verwenden von Konfigurations-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) finden Sie eine umfassende Liste der unterstützten Funktionen und erfahren, wie Sie die Konfigurationen in Ihrem Repository verwalten, damit sie ordnungsgemäß bereitgestellt werden.

### Konfigurieren von Pipelines {#configure-config-deployment}

Siehe [Hinzufügen einer Produktions-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#targeted-deployment).
Siehe [Hinzufügen einer Nicht-Produktions-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#targeted-deployment).

## Front-End-Pipelines {#front-end}

Frontend-Code ist jeder Code, der als statische Datei bereitgestellt wird. Er ist nicht mit dem von AEM bereitgestellten UI-Code identisch und kann Site-Designs, kundendefinierte SPAs, SPAs und andere Lösungen umfassen.

Frontend-Pipelines helfen Ihren Teams, Ihren Design- und Entwicklungsprozess zu optimieren, indem sie eine beschleunigte Implementierung von Frontend-Code ermöglichen, der asynchron zur Backend-Entwicklung ist. Diese dedizierte Pipeline stellt JavaScript und CSS als Thema auf der AEM-Verteilungsschicht bereit, was zu einer neuen Designversion führt, auf die von Seiten verwiesen werden kann, die von AEM bereitgestellt werden.

>[!NOTE]
>
>Eine Benutzerin bzw. ein Benutzer mit der Rolle **Bereitstellungs-Manager** kann mehrere Frontend-Pipelines gleichzeitig erstellen und ausführen.
>
>Es gibt jedoch eine Obergrenze von 300 Pipelines pro Programm (für alle Arten).

Frontend-Pipelines können Pipelines zur Code-Qualitätsprüfung oder Bereitstellung sein.

### Vor der Konfiguration von Front-End-Pipelines {#before-start}

Bevor Sie Frontend-Pipelines konfigurieren, lesen Sie die [Tour zur schnellen AEM-Site-Erstellung](/help/journey-sites/quick-site/overview.md). Dort erhalten Sie eine durchgängige Anleitung für das benutzerfreundliche Tool zur schnellen AEM-Site-Erstellung. Mit dieser Journey können Sie Ihre Front-End-Entwicklung optimieren und Ihre Site schnell anpassen, ohne über Back-End-AEM verfügen zu müssen.

### Konfigurieren einer Front-End-Pipeline {#configure-front-end}

Siehe [Hinzufügen einer Produktions-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#adding-production-pipeline).
Siehe [Hinzufügen einer Nicht-Produktions-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#adding-non-production-pipeline).

### Entwickeln von Sites mit der Frontend-Pipeline {#developing-with-front-end-pipeline}

Mit Frontend-Pipelines erhalten Frontend-Entwickelnde mehr Unabhängigkeit, und der Entwicklungsprozess kann beschleunigt werden.

Unter [Entwickeln von Sites mit der Front-End-Pipeline](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md) finden Sie Informationen dazu, wie dieser Prozess funktioniert, sowie einige Überlegungen, die Sie beachten sollten, um das gesamte Potenzial dieses Prozesses zu nutzen.

## Web-Tier-Konfigurationspipelines {#web-tier-config-pipelines}

Web-Tier-Konfigurationspipelines ermöglichen die exklusive Bereitstellung der HTTPD/Dispatcher-Konfiguration zur AEM-Laufzeit und entkoppeln sie von anderen Codeänderungen. Es handelt sich dabei um eine optimierte Pipeline, über die Benutzer, die nur Dispatcher-Konfigurationsänderungen bereitstellen möchten, schneller und in wenigen Minuten darauf zugreifen können.

>[!TIP]
>
>Mit Web-Tier-Konfigurations-Pipelines können Sie Ihre Web-Konfiguration in demselben oder einem anderen Quellspeicherort wie die vollständige Stack-Pipeline speichern, je nachdem, was Ihrer Projektstruktur am besten entspricht.

Folgende Einschränkungen gelten.

* Verwenden Sie AEM Version `2021.12.6151.20211217T120950Z` oder höher, um Konfigurationspipelines der Web-Ebene zu verwenden.
* [Opt-in in den flexiblen Modus der Dispatcher-Tools](/help/implementing/dispatcher/disp-overview.md#validation-debug), um Konfigurationspipelines auf der Web-Ebene zu verwenden.
* Eine Benutzerin bzw. ein Benutzer muss mit der Rolle **Bereitstellungs-Manager** angemeldet sein, um Pipelines konfigurieren oder ausführen zu können.
* Es kann immer nur eine Web-Ebenen-Konfigurations-Pipeline pro Umgebung geben.
* Benutzende können eine Web-Ebenen-Konfigurations-Pipeline nicht konfigurieren, wenn die entsprechende Full-Stack-Pipeline ausgeführt wird.
* Die Web-Stufen-Struktur muss der im Dokument [Dispatcher in der Cloud](/help/implementing/dispatcher/disp-overview.md#validation-debug) definierten flexiblen Modusstruktur entsprechen.

Außerdem sollten Sie darauf achten, wie sich die [Full-Stack-Pipeline](#full-stack-pipeline) bei der Einführung einer Web-Stufen-Pipeline verhält.

* Wenn für eine Umgebung keine Web-Tier-Konfigurationspipeline eingerichtet ist, kann der Benutzer die Dispatcher-Konfiguration beim Konfigurieren der Vollstapel-Pipeline einbeziehen oder ignorieren. Diese Auswahl erfolgt während der Ausführung und Bereitstellung.
* Sobald eine Web-Tier-Konfigurationspipeline für eine Umgebung konfiguriert ist, ignoriert die zugehörige Full-Stack-Pipeline (sofern vorhanden) die Dispatcher-Konfiguration während der Ausführung und Bereitstellung.
* Nachdem eine Web-Stufen-Konfigurations-Pipeline gelöscht wurde, wird die zugehörige Full-Stack-Pipeline zurückgesetzt, um während der Ausführung Dispatcher-Konfigurationen bereitzustellen.

Konfigurationspipelines der Webstufe können vom Typ `Code quality` oder `Deployment` sein.

### WebTier-Pipelines konfigurieren {#configure-web-tier}

Siehe [Hinzufügen einer Produktions-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#targeted-deployment).
Siehe [Hinzufügen einer Nicht-Produktions-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#targeted-deployment).

## Videoüberblick über Pipeline-Typen {#video}

Ein kurzer Überblick über Pipeline-Typen erhalten Sie im folgenden Video (2 Minuten, 26 Sekunden).

>[!VIDEO](https://video.tv.adobe.com/v/342363)
