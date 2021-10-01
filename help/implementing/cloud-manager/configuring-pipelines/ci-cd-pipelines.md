---
title: CI/CD Pipelines
description: CI/CD Pipelines
index: false
source-git-commit: e51b995aebb053f38cb99879be70e23447f543c0
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 16%

---


# CI/CD-Pipelines von Cloud Manager {#intro-cicd}

In Cloud Manager gibt es zwei Arten von Pipelines:

* **Produktions-Pipeline**
* **Produktionsfremde Pipeline**

## Produktions-Pipeline {#prod-pipeline}

Eine Produktions-Pipelines ist eine speziell entwickelte Pipeline, die eine Reihe aufeinander abgestimmter Schritte umfasst, um Quellcode vollständig in die Produktion zu übernehmen. Zu den Schritten gehören das Erstellen, Verpacken, Testen, Validieren und Bereitstellen in allen Staging-Umgebungen. Eine Produktions-Pipeline kann selbstverständlich erst hinzugefügt werden, nachdem ein Satz aus Produktions- und Staging-Umgebung erstellt wurde.

>[!NOTE]
>Weitere Informationen finden Sie unter Konfigurieren der Produktions-Pipeline .


## Produktionsfremde Pipeline {#non-prod-pipeline}

Eine produktionsfremde Pipeline dient dazu, Code-Qualitätsprüfungen durchzuführen oder Quellcode in einer Entwicklungsumgebung bereitzustellen.

>[!NOTE]
>Weitere Informationen finden Sie unter Produktionsfremde Pipelines und Pipelines für Tests der Code-Qualität.

Die in der Produktions- und Nicht-Produktions-Pipeline in Cloud Manager unterstützten Implementierungs- und Codequalität sind in zwei verschiedene Typen unterteilt:

* Front-End
* Voller Stapel

Die folgende Tabelle fasst die Pipelines zusammen:


>[!NOTE]
>Eine CI/CD-Pipeline in Cloud Manager wird durch ein Ereignis ausgelöst, z. B. eine Pull-Anforderung aus einem Quellcode-Repository, d. h. eine Codeänderung oder einen regulären Zeitplan, um eine Release-Cadence abzugleichen.
>
>Zur Konfiguration der Pipeline müssen Sie:
>* den Trigger definieren, der die Pipeline starten soll
>* Parameter zur Steuerung der Produktionsbereitstellung definieren
>* Leistungstestparameter konfigurieren