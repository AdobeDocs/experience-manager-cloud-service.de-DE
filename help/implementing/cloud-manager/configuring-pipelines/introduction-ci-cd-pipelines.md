---
title: CI/CD Pipelines
description: CI/CD Pipelines
index: false
source-git-commit: 76cff84003576cf23eb1d23674ce6eaf082bbbb1
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 5%

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

Weitere Informationen finden Sie unter Konfigurieren der Produktions-Pipeline .


## Produktionsfremde Pipeline {#non-prod-pipeline}

Eine produktionsfremde Pipeline dient dazu, Code-Qualitätsprüfungen durchzuführen oder Quellcode in einer Entwicklungsumgebung bereitzustellen.

Weitere Informationen finden Sie unter Produktionsfremde Pipelines und Pipelines für Tests der Code-Qualität.

## Grundlegendes zu CI/CD-Pipelines in Cloud Manager {#understand-pipelines}

In der folgenden Tabelle werden die Pipelines in Cloud Manager zusammen mit ihrer Verwendung kategorisiert.

| Pipeline-Typ | Bereitstellung oder Codequalität | Quell-Code | Verwendungsbereiche | Wann oder warum sollte ich verwenden? |
|--- |--- |--- |---|---|---|
| Produktion oder Nichtproduktion | Bereitstellung | Front-End | So stellen Sie Frontend-Code bereit. Frontend-Code ist jeder Code, der als statische Datei bereitgestellt wird. Sie ist nicht mit dem von AEM bereitgestellten UI-Code identisch. Sie umfasst Sites-Designs, vom Kunden definierte SPA, Firefly-SPA und andere Lösungen. Muss in AEM Version vorliegen. | Schnelle Bereitstellungszeiten.<br> Es können mehrere Front-End-Pipelines konfiguriert und gleichzeitig pro Umgebung ausgeführt werden. |
|  | Bereitstellung | Voller Stapel | Um die Back-End-, Front-End- und HTTPD/Dispatcher-Konfiguration gleichzeitig bereitzustellen, Hinweis: Es gelten einige Einschränkungen. | Wenn die Pipelines für die Konfiguration der Frontend- oder Webebene noch nicht übernommen wurden. |
|  | Bereitstellung | Web-Stufen-Konfiguration | So stellen Sie die HTTPD-/Dispatcher-Konfiguration nur innerhalb weniger Minuten bereit.  Diese optimierte Pipeline bietet Benutzern, die nur Änderungen an der Dispatcher-Konfiguration bereitstellen möchten, was eine beschleunigte Möglichkeit darstellt. Hinweis: Muss in AEM Version vorliegen [version] | Schnelle Bereitstellungszeiten. |



## Cloud Manager-Frontend-Pipelines {#front-end}

Frontend-Pipelines helfen Ihren Teams, Ihren Design- und Entwicklungsprozess zu optimieren, indem sie beschleunigte Front-End-Pipelines zur Bereitstellung von Frontend-Code aktivieren. Diese differenzierte Pipeline stellt JavaScript und CSS als Thema auf der AEM-Verteilungsschicht bereit, was zu einer neuen Designversion führt, die von Seiten referenziert werden kann, die von der AEM Laufzeit bereitgestellt werden. Frontend-Code ist jeder Code, der als statische Datei bereitgestellt wird. Sie ist nicht mit dem von AEM bereitgestellten UI-Code identisch. Sie umfasst Sites-Designs, vom Kunden definierte SPA, Firefly-SPA und andere Lösungen.

>[!NOTE]
>Ein Benutzer, der als Bereitstellungsmanager-Rolle angemeldet ist, kann mehrere Frontend-Pipelines gleichzeitig erstellen und ausführen. Es gibt jedoch eine Obergrenze von 300 Pipelines pro Programm (für alle Arten).

Es gibt zwei Arten von Frontend-Pipelines:

* Frontend-Codequalität
* Frontend-Implementierung

## Vollständige Stapel-Pipelines {#full-stack-pipeline}

Die Full Stack-Pipeline bietet Benutzern die Möglichkeit, Back-End-, Front-End- und HTTPD/Dispatcher-Konfigurationen gleichzeitig bereitzustellen.  Es stellt Code und Inhalte für die AEM-Laufzeit bereit, einschließlich Frontend-Code (JavaScript/CSS), der als AEM Client-Bibliotheken gepackt ist. Es kann eine Webebenenkonfiguration bereitstellen, wenn keine Web-Tier-Pipeline konfiguriert ist. Dies stellt die &quot;uber&quot;-Pipeline dar und gibt Benutzern die Möglichkeit, ihren Frontend-Code oder ihre Dispatcher-Konfiguration ausschließlich über die Front End-Pipeline bzw. die Web Tier Config-Pipeline bereitzustellen.


Folgende Einschränkungen gelten:

1. Ein Benutzer muss als Bereitstellungsmanager angemeldet sein, um Pipelines konfigurieren oder ausführen zu können.

1. Es kann immer nur eine Full Stack Pipeline pro Umgebung geben.

1. Der Benutzer kann die vollständige Stack-Pipeline für eine Umgebung so konfigurieren, dass die Dispatcher-Konfiguration ignoriert oder nicht ignoriert wird. Wenn die entsprechende Web-Tier-Konfigurationspipeline für die Umgebung nicht vorhanden ist.

1. Die vollständige Stack-Pipeline für eine Umgebung ignoriert die Dispatcher-Konfiguration, wenn die entsprechende Web Tier Config-Pipeline für die Umgebung vorhanden ist.

Es gibt zwei Arten von Full Stack Pipelines:

* Vollständige Pipeline für die Stack-Codequalität
* Pipeline für die Bereitstellung eines vollständigen Stapels

