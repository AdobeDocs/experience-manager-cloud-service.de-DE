---
title: CI/CD-Pipelines
description: Erfahren Sie mehr über die CI/CD-Pipelines in Cloud Manager und wie sie zur effizienten Bereitstellung Ihres Codes verwendet werden können.
index: true
exl-id: 40d6778f-65e0-4612-bbe3-ece02905709b
source-git-commit: 5ad33f0173afd68d8868b088ff5e20fc9f58ad5a
workflow-type: tm+mt
source-wordcount: '1337'
ht-degree: 98%

---


# CI/CD-Pipelines in Cloud Manager {#intro-cicd}

Erfahren Sie mehr über die CI/CD-Pipelines in Cloud Manager und wie sie zur effizienten Bereitstellung Ihres Codes verwendet werden können.

## Einführung {#introduction}

Eine CI/CD-Pipeline in Cloud Manager ist ein Mechanismus zum Erstellen von Code aus einem Quell-Repository und dessen Bereitstellung in einer Umgebung. Eine Pipeline wird durch ein Ereignis ausgelöst, z. B. eine Pull-Anfrage aus einem Quell-Code-Repository (d. h. eine Code-Änderung), oder nach einem regulären Zeitplan, um einen Veröffentlichungs-Rhythmus einzuhalten.

Zur Konfiguration einer Pipeline müssen Sie:

* Den Auslöser definieren, der die Pipeline startet.
* Den Parameter zur Steuerung der Produktionsbereitstellung definieren.
* Die Leistungstestparameter konfigurieren.

Cloud Manager bietet zwei Pipelinetypen:

* [Produktions-Pipelines](#prod-pipeline)
* [Produktionsfremde Pipelines](#non-prod-pipeline)

![Pipelinetypen](/help/implementing/cloud-manager/assets/configure-pipeline/ci-cd-config1.png)

## Videoüberblick {#video}

Ein kurzer Überblick über Pipeline-Typen erhalten Sie in diesem kurzen Video.

>[!VIDEO](https://video.tv.adobe.com/v/342363)

## Produktions-Pipelines {#prod-pipeline}

Eine Produktions-Pipeline ist eine speziell entwickelte Pipeline, die eine Reihe aufeinander abgestimmter Schritte zum Bereitstellen von Quell-Code für die Verwendung in Produktionsumgebungen enthält. Die Schritte umfassen das Erstellen, Packen, Testen, Validieren und Bereitstellen in allen Staging-Umgebungen. Daher kann eine Produktions-Pipeline erst hinzugefügt werden, nachdem eine Gruppe von Produktions- und Staging-Umgebungen erstellt wurde.

>[!TIP]
>
>Weitere Informationen finden Sie unter [Konfigurieren einer Produktions-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md).

## Produktionsfremde Pipeline {#non-prod-pipeline}

Eine produktionsfremde Pipeline dient hauptsächlich dazu, Code-Qualitätsprüfungen durchzuführen oder Quell-Code in einer Entwicklungsumgebung bereitzustellen.

>[!TIP]
>
>Weitere Informationen finden Sie unter [Konfigurieren einer produktionsfremden Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md).

## Code-Quellen {#code-sources}

Neben Produktion und produktionsfremd können Pipelines nach dem Typ des von ihnen bereitgestellten Codes unterschieden werden.

* **[Full-Stack-Pipelines](#full-stack-pipeline)**: Gleichzeitiges Bereitstellen von Backend- und Frontend-Code-Builds mit einer oder mehreren AEM-Serveranwendungen zusammen mit HTTPD-/Dispatcher-Konfigurationen
* **[Frontend-Pipelines](#front-end)**: Bereitstellen von Frontend-Code-Builds mit einer oder mehreren Client-seitigen Benutzeroberflächenanwendungen
* **[Web-Ebenen-Konfigurations-Pipelines](#web-tier-config-pipelines)**: Bereitstellung von HTTPD-/Dispatcher-Konfigurationen

Diese Typen werden später in diesem Dokument detailliert beschrieben.

### Grundlegendes zu CI/CD-Pipelines in Cloud Manager {#understand-pipelines}

In der folgenden Tabelle sind alle in Cloud Manager verfügbaren Pipelines und deren Verwendungszwecke zusammengefasst.

| Pipeline-Typ | Bereitstellung oder Code-Qualität | Quell-Code | Zweck | Anmerkungen |
|--- |--- |--- |---|---|
| Produktion oder produktionsfremd | Bereitstellung | Full-Stack | Gleichzeitige Bereitstellung von Backend- und Frontend-Code-Builds zusammen mit HTTPD-/Dispatcher-Konfigurationen | Wenn Frontend-Code gleichzeitig mit AEM-Servercode bereitgestellt werden muss.<br>Wenn Frontend-Pipelines oder Web-Stufen-Konfigurations-Pipelines noch nicht übernommen wurden. |
| Produktion oder produktionsfremd | Bereitstellung | Frontend | Bereitstellung von Frontend-Code-Builds, die eine oder mehrere Client-seitige Benutzeroberflächenanwendungen enthalten | Unterstützt mehrere gleichzeitige Frontend-Pipelines<br>Viel schneller als Full-Stack-Bereitstellungen |
| Produktion oder produktionsfremd | Bereitstellung | Web-Stufen-Konfiguration | Bereitstellen von HTTPD-/Dispatcher-Konfigurationen | Bereitstellung in Minuten |
| Produktionsfremd | Code-Qualität | Full-Stack | Führt Code-Qualitätsprüfungen für Full-Stack-Code ohne Bereitstellung durch | Unterstützt mehrere Pipelines |
| Produktionsfremd | Code-Qualität | Frontend | Führt Code-Qualitätsprüfungen für Frontend-Code ohne Bereitstellung durch | Unterstützt mehrere Pipelines |
| Produktionsfremd | Code-Qualität | Web-Stufen-Konfiguration | Führt Code-Qualitätsprüfungen für Dispatcher-Konfigurationen ohne Bereitstellung aus | Unterstützt mehrere Pipelines |

Die folgende Abbildung zeigt Pipeline-Konfigurationen in Cloud Manager mit traditionellen, einzelnen Frontend-Repository- oder unabhängigen Frontend-Repository-Setups.

![Cloud Manager-Pipeline-Konfigurationen](/help/implementing/cloud-manager/assets/configure-pipeline/cm-setup.png)

## Full-Stack-Pipelines {#full-stack-pipeline}

Full-Stack-Pipelines stellen Backend-Code, Frontend-Code und Web-Stufen-Konfigurationen für AEM Runtime gleichzeitig bereit.

* Backend-Code: Unveränderliche Inhalte wie Java-Code, OSGi-Konfigurationen, RepoInit sowie veränderliche Inhalte
* Frontend-Code: Ressourcen der Programm-Benutzeroberfläche wie JavaScript, CSS, Schriftarten
* Web-Stufen-Konfiguration: HTTPD-/Dispatcher-Konfigurationen

Die Full-Stack-Pipeline stellt eine „Über“-Pipeline dar, die alles auf einmal tut, während Benutzern die Möglichkeit gegeben wird, ihre Frontend-Code- oder Dispatcher-Konfigurationen ausschließlich über die Frontend-Pipeline bzw. die Web-Stufen-Konfigurations-Pipelines bereitzustellen.

Full-Stack-Pipelines packen Frontend-Code (JavaScript/CSS) als [AEM Client-Bibliotheken](/help/implementing/developing/introduction/clientlibs.md).

Full-Stack-Pipelines können Web-Stufen-Konfigurationen bereitstellen, wenn eine [Web-Stufen-Konfigurations-Pipeline](#web-tier-config-pipelines) nicht konfiguriert ist.

Folgende Einschränkungen gelten.

* Eine Benutzerin bzw. ein Benutzer muss mit der Rolle **Bereitstellungs-Manager** angemeldet sein, um Pipelines konfigurieren oder ausführen zu können.
* Es kann immer nur eine Full-Stack-Pipeline pro Umgebung geben.

Achten Sie außerdem darauf, wie sich die Full-Stack-Pipeline verhält, wenn Sie eine [Web-Stufen-Konfigurations-Pipeline](#web-tier-config-pipelines) einführen.

* Die Full-Stack-Pipeline für eine Umgebung ignoriert die Dispatcher-Konfiguration, wenn die entsprechende Web-Stufen-Konfigurations-Pipeline vorhanden ist.
* Wenn die entsprechende Web-Stufen-Konfigurations-Pipeline für die Umgebung nicht vorhanden ist, kann der Benutzer die Full-Stack-Pipeline so konfigurieren, dass sie die Dispatcher-Konfiguration einschließt oder ignoriert.

Full-Stack-Pipelines können Pipelines zur Code-Qualitätsprüfung oder für die Bereitstellung sein.

## Frontend-Pipelines {#front-end}

Frontend-Code ist jeder Code, der als statische Datei bereitgestellt wird. Er ist nicht mit dem von AEM bereitgestellten UI-Code identisch und kann Site-Designs, kundendefinierte SPAs, SPAs und andere Lösungen umfassen.

Frontend-Pipelines helfen Ihren Teams, Ihren Design- und Entwicklungsprozess zu optimieren, indem sie eine beschleunigte Bereitstellung von Frontend-Code ermöglichen, der asynchron von der Backend-Entwicklung ausgeführt wird. Diese dedizierte Pipeline stellt JavaScript und CSS als Design auf der AEM-Verteilungsebene bereit, was zu einer neuen Design-Version führt, die von Seiten referenziert werden kann, die von AEM bereitgestellt werden.

>[!IMPORTANT]
>
>Sie müssen mit der AEM-Version `2021.10.5933.20211012T154732Z ` oder höher arbeiten und AEM Sites aktivieren, um Frontend-Pipelines zu verwenden.

>[!NOTE]
>
>Eine Benutzerin bzw. ein Benutzer mit der Rolle **Bereitstellungs-Manager** kann mehrere Frontend-Pipelines gleichzeitig erstellen und ausführen.
>
>Es gibt jedoch eine Obergrenze von 300 Pipelines pro Programm (für alle Arten).

Frontend-Pipelines können Pipelines zur Code-Qualitätsprüfung oder Bereitstellung sein.

### Vor der Konfiguration von Frontend-Pipelines {#before-start}

Bevor Sie Frontend-Pipelines konfigurieren, lesen Sie die [Tour zur schnellen AEM-Site-Erstellung](/help/journey-sites/quick-site/overview.md). Dort erhalten Sie eine durchgängige Anleitung für das benutzerfreundliche Tool zur schnellen AEM-Site-Erstellung. Diese Tour hilft Ihnen, Ihre Frontend-Entwicklung zu optimieren und Ihre Site ohne AEM-Backend-Kenntnisse schnell anzupassen.

### Konfigurieren einer Frontend-Pipeline {#configure-front-end}

Informationen zum Konfigurieren von Frontend-Pipelines finden Sie unter folgenden Themen:

* [Hinzufügen einer Produktions-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#adding-production-pipeline)
* [Hinzufügen einer produktionsfremden Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#adding-non-production-pipeline)

### Entwickeln von Sites mit der Frontend-Pipeline {#developing-with-front-end-pipeline}

Mit Frontend-Pipelines erhalten Frontend-Entwicklern mehr Unabhängigkeit und der Entwicklungsprozess kann beschleunigt werden.

Wie dieser Prozess abläuft und was dabei zu beachten ist, um das volle Potenzial dieses Prozesses auszuschöpfen, erfahren Sie unter [Entwickeln von Sites mit der Frontend-Pipeline](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md).

### Konfigurieren von Full-Stack-Pipelines {#configure-full-stack}

Informationen zum Konfigurieren von Full-Stack-Pipelines finden Sie in den folgenden Dokumenten:

* [Hinzufügen einer Produktions-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#adding-production-pipeline)
* [Hinzufügen einer produktionsfremden Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#adding-non-production-pipeline)


## Web-Stufen-Konfigurations-Pipelines {#web-tier-config-pipelines}

Web-Stufen-Konfigurations-Pipelines ermöglichen die exklusive Bereitstellung der HTTPD-/Dispatcher-Konfiguration zu AEM Runtime, indem sie sie von anderen Code-Änderungen entkoppeln. Es handelt sich um eine optimierte Pipeline, die Benutzern, die nur Änderungen an der Dispatcher-Konfiguration bereitstellen möchten, eine beschleunigte Möglichkeit bietet, dies in nur wenigen Minuten zu tun.

>[!TIP]
>
>Bei Web-Stufen-Konfigurations-Pipelines können Sie zwischen dem Speichern Ihrer Web-Konfiguration am selben Quellspeicherort, wie für die Full-Stack-Pipeline, oder an einem anderen Speicherort wählen, je nachdem, welche Struktur Ihrem Projekt mehr entspricht.

Folgende Einschränkungen gelten.

* Sie müssen AEM-Version `2021.12.6151.20211217T120950Z` oder neuer verwenden, um Web-Stufen-Konfigurations-Pipelines zu nutzen.
* Sie müssen [in den flexiblen Modus der Dispatcher-Tools](/help/implementing/dispatcher/disp-overview.md#validation-debug) wechseln, um Web-Stufen-Konfigurations-Pipelines nutzen zu können.
* Eine Benutzerin bzw. ein Benutzer muss mit der Rolle **Bereitstellungs-Manager** angemeldet sein, um Pipelines konfigurieren oder ausführen zu können.
* Es kann immer nur eine Web-Stufen-Konfigurations-Pipeline pro Umgebung geben.
* Der Benutzer kann eine Web-Tier-Konfigurationspipeline nicht konfigurieren, wenn die entsprechende Full-Stack-Pipeline ausgeführt wird.
* Die Web-Stufen-Struktur muss der im Dokument [Dispatcher in der Cloud](/help/implementing/dispatcher/disp-overview.md#validation-debug) definierten flexiblen Modusstruktur entsprechen.

Außerdem sollten Sie darauf achten, wie sich die [Full-Stack-Pipeline](#full-stack-pipeline) bei der Einführung einer Web-Stufen-Pipeline verhält.

* Wenn für eine Umgebung keine Web-Stufen-Konfigurations-Pipeline konfiguriert wurde, kann der Benutzer beim Konfigurieren der entsprechenden Full-Stack-Pipeline eine Auswahl treffen, um die Dispatcher-Konfiguration während der Ausführung und Bereitstellung einzuschließen oder zu ignorieren.
* Sobald eine Web-Stufen-Konfigurations-Pipeline für eine Umgebung konfiguriert wurde, ignoriert die entsprechende Full-Stack-Pipeline (sofern vorhanden) die Dispatcher-Konfiguration während der Ausführung und Bereitstellung.
* Nachdem eine Web-Stufen-Konfigurations-Pipeline gelöscht wurde, wird die zugehörige Full-Stack-Pipeline zurückgesetzt, um während der Ausführung Dispatcher-Konfigurationen bereitzustellen.

Web-Stufen-Konfigurations-Pipelines können vom Typ Code-Qualitätsprüfung oder Bereitstellung sein.

### Konfigurieren von Web-Stufen-Konfigurations-Pipelines {#configure-web-tier-config-pipelines}

Informationen zum Konfigurieren von Web-Stufen-Konfigurations-Pipelines finden Sie in den folgenden Dokumenten:

* [Hinzufügen einer Produktions-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#adding-production-pipeline)
* [Hinzufügen einer produktionsfremden Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#adding-non-production-pipeline)
