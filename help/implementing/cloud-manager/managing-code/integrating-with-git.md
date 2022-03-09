---
title: Verwenden von Git mit Cloud Manager
description: Erfahren Sie, wie Sie die Git-Repositorys von Cloud Manager verwenden und wie Sie Ihr eigenes On-Premise-kundenverwaltetes Git-Repository mit Cloud Manager integrieren.
exl-id: 57e71b8a-4546-4d7f-825c-a1637d08e608
source-git-commit: a9303c659730022b7417fc9082dedd26d7cbccca
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 47%

---

# Verwenden von Git mit Cloud Manager {#git-integration}

Adobe Cloud Manager verfügt über ein einzelnes Git-Repository, das der Bereitstellung von Code unter Verwendung der CI/CD-Pipelines von Cloud Manager dient.

Sie können das Git-Repository von Cloud Manager vorkonfiguriert verwenden. Sie haben aber auch die Möglichkeit, ein kundenverwaltetes Git-Repository in Cloud Manager zu integrieren.

## Übersicht über die Git-Integration {#git-integration-overview}

In dieser Videoreihe werden verschiedene Anwendungsfälle bei der Integration eines kundenverwalteten Git-Repositorys in Cloud Manager untersucht, darunter:

* [Erstsynchronisierung](#initial-sync)
* [Standard-Verzweigungsstrategie](#branching-strategy)
* [Entwicklung von Funktionsverzweigungen](#feature-development)
* [Produktionsimplementierung](#production-deployment)
* [Synchronisieren von Versions-Tags](#sync-tags)

Die Videoreihe setzt grundlegende Kenntnisse der Git- und Quell-Code-Verwaltung voraus. Weitere Informationen zu Git finden Sie in den [folgenden zusätzlichen Ressourcen](#additional-resources).

>[!VIDEO](https://video.tv.adobe.com/v/28710/)

Die Schritte und Benennungskonventionen, die in dieser Videoreihe beschrieben werden, stellen einige Best Practices für die Arbeit mit einem kundenverwalteten Git-Repository in Cloud Manager dar. Es wird erwartet, dass die dargestellten Konventionen und Workflows für einzelne Anwendungsfälle angepasst werden.

## Erstsynchronisierung {#initial-sync}

In diesem Video erfahren Sie die ersten Schritte zum Synchronisieren eines kundenverwalteten Git-Repositorys mit dem Git-Repository von Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/28711/?quality=12)

## Standard-Verzweigungsstrategie {#branching-strategy}

In diesem Video erfahren Sie grundlegende Verzweigungsstrategien.

>[!VIDEO](https://video.tv.adobe.com/v/28712/?quality=12)

## Entwicklung von Funktionsverzweigungen {#feature-development}

Verwenden Sie eine Funktionsverzweigung, um Code-Änderungen in einem kundenverwalteten Git-Repository zu isolieren und mit dem Git-Repository von Cloud Manager zu synchronisieren. So können Sie eine produktionsfremde Pipeline für Code-Qualität- und Validierungstests verwenden.

>[!VIDEO](https://video.tv.adobe.com/v/28723/?quality=12)

## Produktionsimplementierung {#production-deployment}

Bereiten Sie Code für die Produktionsfreigabe in einem kundenverwalteten Git-Repository vor und synchronisieren Sie mit dem Git-Repository von Cloud Manager, um eine Bereitstellung in Staging- und Produktionsumgebungen vorzunehmen.

>[!VIDEO](https://video.tv.adobe.com/v/28724/?quality=12)

## Synchronisieren von Versions-Tags {#sync-tags}

Synchronisieren Sie Release-Tags aus einem Cloud Manager-Git-Repository in einem kundenverwalteten Git-Repository, um die Sichtbarkeit des Codes zu gewährleisten, der in Staging- und Produktionsumgebungen bereitgestellt wurde.

>[!VIDEO](https://video.tv.adobe.com/v/28725/?quality=12)

## Zusätzliche Ressourcen {#additional-resources}

* [GitHub-Ressourcen](https://try.github.io)
* [Git-Tutorials von Atlassian](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Git-Schnellübersicht](https://education.github.com/git-cheat-sheet-education.pdf)
