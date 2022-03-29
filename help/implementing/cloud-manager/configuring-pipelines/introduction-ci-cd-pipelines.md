---
title: CI/CD-Pipelines
description: Erfahren Sie mehr über die CI/CD-Pipelines von Cloud Manager und wie sie zur effizienten Bereitstellung Ihres Codes verwendet werden können.
index: true
exl-id: 40d6778f-65e0-4612-bbe3-ece02905709b
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '1364'
ht-degree: 7%

---

# CI/CD-Pipelines in Cloud Manager {#intro-cicd}

Erfahren Sie mehr über die CI/CD-Pipelines von Cloud Manager und wie sie zur effizienten Bereitstellung Ihres Codes verwendet werden können.

## Einführung {#introduction}

Eine CI/CD-Pipeline in Cloud Manager ist ein Mechanismus zum Erstellen von Code aus einem Quell-Repository und dessen Bereitstellung in einer Umgebung. Eine Pipeline kann durch ein Ereignis ausgelöst werden, z. B. eine Pull-Anfrage aus einem Quellcode-Repository (d. h. eine Codeänderung) oder einen regulären Zeitplan, um eine Release-Cadence abzugleichen.

Um eine Pipeline zu konfigurieren, müssen Sie:

* Definieren Sie den Trigger, der die Pipeline startet.
* Definieren Sie die Parameter zur Steuerung der Produktionsbereitstellung.
* Konfigurieren Sie die Leistungstestparameter.

Cloud Manager bietet zwei Pipelinetypen:

* [Produktions-Pipelines](#prod-pipeline)
* [Produktionsfremde Pipelines](#non-prod-pipeline)

![Pipelinetypen](/help/implementing/cloud-manager/assets/configure-pipeline/ci-cd-config1.png)

## Produktions-Pipelines {#prod-pipeline}

Eine Produktions-Pipeline ist eine speziell entwickelte Pipeline, die eine Reihe aufeinander abgestimmter Schritte zum Bereitstellen von Quellcode für die Produktionsverwendung enthält. Die Schritte umfassen das Erstellen, Verpacken, Testen, Validieren und Bereitstellen in allen Staging-Umgebungen. Daher kann eine Produktions-Pipeline erst hinzugefügt werden, nachdem eine Reihe von Produktions- und Staging-Umgebungen erstellt wurde.

>[!TIP]
>
>Siehe Dokument . [Konfigurieren einer Produktions-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) für weitere Details.

## Produktionsfremde Pipeline {#non-prod-pipeline}

Eine Nicht-Produktions-Pipeline dient hauptsächlich dazu, Code-Qualitätsprüfungen durchzuführen oder Quellcode in einer Entwicklungsumgebung bereitzustellen.

>[!TIP]
>
>Siehe Dokument . [Konfigurieren einer produktionsfremden Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) für weitere Details.

## Code-Quellen {#code-sources}

Neben der Produktion und Nicht-Produktion können Pipelines nach dem Typ des von ihnen bereitgestellten Codes unterschieden werden.

* **[Vollständige Stapel-Pipelines](#full-stack-pipeline)** - Bereitstellen von Back-End- und Front-End-Code-Builds mit einer oder mehreren AEM Serveranwendungen zusammen mit HTTPD-/Dispatcher-Konfigurationen
* **[Front-End-Pipelines](#front-end)** - Bereitstellen von Frontend-Code-Builds mit einer oder mehreren clientseitigen Benutzeroberflächenanwendungen
* **[Web-Ebenen-Konfigurationspipelines](#web-tier-config-pipelines)** - Bereitstellung von HTTPD-/Dispatcher-Konfigurationen

Diese werden weiter unten in diesem Dokument beschrieben.

### Grundlegendes zu CI/CD-Pipelines in Cloud Manager {#understand-pipelines}

In der folgenden Tabelle sind alle in Cloud Manager verfügbaren Pipelines und deren Verwendungszwecke zusammengefasst.

| Pipeline-Typ | Bereitstellung oder Code-Qualität | Quell-Code | Zweck | Anmerkungen |
|--- |--- |--- |---|---|
| Produktion oder produktionsfremd | Implementierung | Full-Stack | Bereitstellung von Back-End- und Front-End-Code-Builds zusammen mit HTTPD-/Dispatcher-Konfigurationen | Wenn Frontend-Code gleichzeitig mit AEM Server-Code bereitgestellt werden muss.<br>Wenn Frontend-Pipelines oder Web-Tier-Konfigurationspipelines noch nicht übernommen wurden. |
| Produktion oder produktionsfremd | Implementierung | Front-End | Stellt Frontend-Code-Build bereit, der eine oder mehrere clientseitige Benutzeroberflächenanwendungen enthält | Unterstützt mehrere gleichzeitige Front-End-Pipelines<br>Viel schneller als vollständige Bereitstellungen |
| Produktion oder produktionsfremd | Implementierung | Web-Stufen-Konfiguration | Bereitstellen von HTTPD-/Dispatcher-Konfigurationen | Bereitstellung in Minuten |
| Produktionsfremd | Code-Qualität | Full-Stack | Führt Code-Qualitätsprüfungen für Vollstapelcode ohne Implementierung durch | Unterstützt mehrere Pipelines |
| Produktionsfremd | Code-Qualität | Front-End | Führt Code-Qualitätsprüfungen für Frontend-Code ohne Implementierung durch | Unterstützt mehrere Pipelines |
| Produktionsfremd | Code-Qualität | Web-Stufen-Konfiguration | Führt Code-Qualitätsprüfungen für Dispatcher-Konfigurationen ohne Bereitstellung aus | Unterstützt mehrere Pipelines |

Die folgende Abbildung zeigt die Pipeline-Konfigurationen von Cloud Manager mit herkömmlichen Single-Front-End-Repository- oder unabhängigen Front-End-Repository-Setups.

![Cloud Manager-Pipeline-Konfigurationen](/help/implementing/cloud-manager/assets/configure-pipeline/cm-setup.png)

## Pipelines mit Full-Stack {#full-stack-pipeline}

Vollstapelpipelines stellen Back-End-Code, Frontend-Code und Webstufenkonfigurationen gleichzeitig für AEM Laufzeitumgebung bereit.

* Back-End-Code - Unveränderlicher Inhalt wie Java-Code, OSGi-Konfigurationen, repoinit sowie veränderliche Inhalte
* Frontend-Code - Ressourcen der Anwendungs-Benutzeroberfläche wie JavaScript, CSS, Schriftarten
* Web-Tier-Konfiguration - HTTPD-/Dispatcher-Konfigurationen

Die Full-Stack-Pipeline stellt eine &quot;Uber&quot;-Pipeline dar, die alles auf einmal tut, während Benutzern die Möglichkeit gegeben wird, ihre Frontend-Code- oder Dispatcher-Konfigurationen ausschließlich über die Frontend-Pipeline bzw. die Web-Tier-Konfigurationspipelines bereitzustellen.

Vollstapelpipelines verpacken Frontend-Code (JavaScript/CSS) als [AEM Client-Bibliotheken.](/help/implementing/developing/introduction/clientlibs.md)

Vollstapelpipelines können Webstufenkonfigurationen bereitstellen, wenn eine [Web-Tier-Konfigurationspipeline](#web-tier-config-pipelines) nicht konfiguriert ist.

Es gelten die folgenden Einschränkungen.

* Ein Benutzer muss mit der **Bereitstellungsmanager** Rolle, um Pipelines zu konfigurieren oder auszuführen.
* Es kann immer nur eine Vollstack-Pipeline pro Umgebung geben.

Beachten Sie außerdem, wie sich die Full-Stack-Pipeline verhält, wenn Sie eine [Web-Ebene-Konfigurationspipeline.](#web-tier-config-pipelines)

* Die Vollstapel-Pipeline für eine Umgebung ignoriert die Dispatcher-Konfiguration, wenn die entsprechende Web-Tier-Konfigurationspipeline vorhanden ist.
* Wenn die entsprechende Web-Tier-Konfigurationspipeline für die Umgebung nicht vorhanden ist, kann der Benutzer die Vollstapel-Pipeline konfigurieren, um die Dispatcher-Konfiguration ein- oder zu ignorieren.

Vollstapelpipelines können Pipelines zur Codequalität oder Bereitstellung sein.

## Front-End-Pipelines {#front-end}

Frontend-Code ist jeder Code, der als statische Dateien bereitgestellt wird. Sie ist nicht mit dem von AEM bereitgestellten UI-Code identisch und kann Site-Designs, kundendefinierte SPA, Firefly-SPA und andere Lösungen umfassen.

Frontend-Pipelines helfen Ihren Teams, Ihren Design- und Entwicklungsprozess zu optimieren, indem sie eine beschleunigte Bereitstellung von Frontend-Code ermöglichen, der asynchron von der Back-End-Entwicklung ausgeführt wird. Diese dedizierte Pipeline stellt JavaScript und CSS als Thema auf der AEM-Verteilungsschicht bereit, was zu einer neuen Designversion führt, auf die von Seiten verwiesen werden kann, die von AEM bereitgestellt werden.

>[!IMPORTANT]
>
>Sie müssen AEM Version verwenden `2021.10.5933.20211012T154732Z ` oder höher, wenn AEM Sites für die Nutzung von Frontend-Pipelines aktiviert ist.

>[!NOTE]
>
>Ein Benutzer mit der **Bereitstellungsmanager** -Rolle kann mehrere Frontend-Pipelines gleichzeitig erstellen und ausführen.
>
>Es gibt jedoch eine Obergrenze von 300 Pipelines pro Programm (für alle Arten). Dabei kann es sich um Front-End-Code-Qualitäts- oder Front-End-Implementierungs-Pipelines handeln.

Frontend-Pipelines können Pipelines zur Code-Qualität oder Bereitstellung sein.

### Vor der Konfiguration von Frontend-Pipelines {#before-start}

Bevor Sie Frontend-Pipelines konfigurieren, lesen Sie bitte die [Journey zur AEM SchnellSite-Erstellung](/help/journey-sites/quick-site/overview.md) für eine durchgängige Anleitung durch das benutzerfreundliche AEM für die schnelle Site-Erstellung. Mit dieser Journey können Sie Ihre Front-End-Entwicklung optimieren und Ihre Site ohne Back-End-AEM schnell anpassen.

### Konfigurieren einer Front-End-Pipeline {#configure-front-end}

Informationen zum Konfigurieren von Front-End-Pipelines finden Sie in den folgenden Dokumenten.

* [Hinzufügen einer Produktions-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#adding-production-pipeline)
* [Hinzufügen einer produktionsfremden Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#adding-non-production-pipeline)

### Entwickeln von Sites mit der Frontend-Pipeline {#developing-with-front-end-pipeline}

Mit Front-End-Pipelines wird Frontend-Entwicklern mehr Unabhängigkeit gegeben und der Entwicklungsprozess kann beschleunigt werden.

Weitere Informationen finden Sie im Dokument . [Entwickeln von Sites mit der Frontend-Pipeline](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md) wie dieser Prozess funktioniert, zusammen mit einigen Überlegungen, die Sie beachten sollten, um das Potenzial dieses Prozesses voll auszuschöpfen.

### Konfigurieren von Full-Stack-Pipelines {#configure-full-stack}

Informationen zum Konfigurieren von Full-Stack-Pipelines finden Sie in den folgenden Dokumenten.

* [Hinzufügen einer Produktions-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#adding-production-pipeline)
* [Hinzufügen einer produktionsfremden Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#adding-non-production-pipeline)


## Web-Ebenen-Konfigurationspipelines {#web-tier-config-pipelines}

Web-Tier-Konfigurationspipelines ermöglichen die exklusive Bereitstellung der HTTPD-/Dispatcher-Konfiguration zur AEM-Laufzeit, indem sie sie von anderen Codeänderungen entkoppeln. Es handelt sich dabei um eine optimierte Pipeline, die Benutzern, die nur Änderungen der Dispatcher-Konfiguration bereitstellen möchten, zur Verfügung stellt. Dies bedeutet, dass dies in wenigen Minuten beschleunigt werden kann.

>[!TIP]
>
>Bei Web-Tier-Konfigurationspipelines können Sie zwischen dem Speichern Ihrer Web-Konfiguration am selben Quellspeicherort wie für die vollständige Stapel-Pipeline oder an einem anderen Speicherort wählen, je nachdem, welche Struktur Ihrem Projekt besser entspricht.

Es gelten die folgenden Einschränkungen.

* Sie müssen AEM Version verwenden `2021.12.6151.20211217T120950Z` oder neuer , um Konfigurations-Pipelines der Web-Ebene zu nutzen.
* Sie müssen [Aktivieren des flexiblen Modus der Dispatcher-Tools](/help/implementing/dispatcher/disp-overview.md#validation-debug) , um Konfigurationspipelines auf der Web-Ebene zu nutzen.
* Ein Benutzer muss mit der **Bereitstellungsmanager** Rolle, um Pipelines zu konfigurieren oder auszuführen.
* Es kann immer nur eine Web-Tier-Konfigurationspipeline pro Umgebung geben.
* Der Benutzer kann eine Web-Tier-Konfigurationspipeline nicht konfigurieren, wenn die entsprechende Full-Stack-Pipeline ausgeführt wird.
* Die Webstufenstruktur muss der im Dokument definierten flexiblen Modusstruktur entsprechen. [Dispatcher in der Cloud.](/help/implementing/dispatcher/disp-overview.md#validation-debug)

Beachten Sie außerdem, wie das [Vollständige Stack-Pipeline](#full-stack-pipeline) verhält sich bei der Einführung einer WebTier-Pipeline.

* Wenn für eine Umgebung keine Web-Tier-Konfigurationspipeline konfiguriert wurde, kann der Benutzer beim Konfigurieren der entsprechenden Full-Stack-Pipeline eine Auswahl treffen, um die Dispatcher-Konfiguration während der Ausführung und Bereitstellung ein- oder zu ignorieren.
* Sobald eine Web-Tier-Konfigurationspipeline für eine Umgebung konfiguriert wurde, ignoriert die entsprechende Full-Stack-Pipeline (sofern vorhanden) die Dispatcher-Konfiguration während der Ausführung und Bereitstellung.
* Nachdem eine Web-Tier-Konfigurationspipeline gelöscht wurde, wird die zugehörige Full-Stack-Pipeline zurückgesetzt, um während der Ausführung Dispatcher-Konfigurationen bereitzustellen.

Web-Tier-Konfigurationsleitungen können vom Typ Code-Qualität oder -Bereitstellung sein.

### Konfigurieren von Pipelines zur Web-Ebene {#configure-web-tier-config-pipelines}

Informationen zum Konfigurieren von Web-Tier-Konfigurations-Pipelines finden Sie in den folgenden Dokumenten.

* [Hinzufügen einer Produktions-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#adding-production-pipeline)
* [Hinzufügen einer produktionsfremden Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#adding-non-production-pipeline)
