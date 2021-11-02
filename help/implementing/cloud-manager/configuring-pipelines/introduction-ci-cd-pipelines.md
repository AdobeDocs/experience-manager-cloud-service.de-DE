---
title: CI/CD Pipelines
description: CI/CD Pipelines
index: false
source-git-commit: 1887cc7374ece840b2dcca4482924b14c4793567
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 18%

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
