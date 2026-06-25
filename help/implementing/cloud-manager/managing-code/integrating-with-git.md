---
title: Verwenden von Git mit Cloud Manager
description: Erfahren Sie, wie Sie die Git-Repositorys von Cloud Manager verwenden und Ihr eigenes, On-Premise kundenverwaltetes Git-Repository in Cloud Manager integrieren.
exl-id: 57e71b8a-4546-4d7f-825c-a1637d08e608
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: 922d77a0d93657b338581b38b086219b9ebee8cc
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 57%

---

# Verwenden von Git mit Cloud Manager {#git-integration}

Adobe Cloud Manager verfügt über ein einzelnes Git-Repository, das der Bereitstellung von Code unter Verwendung der CI/CD-Pipelines von Cloud Manager dient.

Sie können das Git-Repository von Cloud Manager wie bereitgestellt verwenden, aber Sie haben auch die Möglichkeit, ein vom Kunden verwaltetes Git-Repository mit Cloud Manager zu integrieren.

## Überblick über die Git-Integration {#git-integration-overview}

In dieser Videoreihe werden verschiedene Anwendungsfälle bei der Integration eines vom Kunden verwalteten Git-Repositorys mit Cloud Manager untersucht, darunter:

* [Erstsynchronisierung](#initial-sync)
* [Grundlegende Verzweigungsstrategie](#branching-strategy)
* [Entwicklung von Funktionsverzweigungen](#feature-development)
* [Produktionsbereitstellung](#production-deployment)
* [Synchronisieren von Versions-Tags](#sync-tags)

Die Videoreihe erfordert grundlegende Kenntnisse der Git- und Quell-Code-Verwaltung. Weitere Informationen zu Git finden Sie in den [folgenden zusätzlichen Ressourcen](#additional-resources).

>[!VIDEO](https://video.tv.adobe.com/v/28710/)

Die in dieser Videoreihe beschriebenen Schritte und Benennungskonventionen stellen einige Best Practices für die Arbeit mit einem vom Kunden verwalteten Git-Repository in Cloud Manager dar. Es wird erwartet, dass die dargestellten Konventionen und Workflows für einzelne Anwendungsfälle angepasst werden.

## Erstsynchronisierung {#initial-sync}

In diesem Video erfahren Sie die ersten Schritte zum Synchronisieren eines kundenverwalteten Git-Repositorys mit dem Git-Repository von Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/28711/?quality=12)

## Grundlegende Verzweigungsstrategie {#branching-strategy}

In diesem Video erfahren Sie grundlegende Verzweigungsstrategien.

>[!VIDEO](https://video.tv.adobe.com/v/28712/?quality=12)

## Entwicklung von Funktionsverzweigungen {#feature-development}

Verwenden Sie eine Funktionsverzweigung, um Code-Änderungen in einem kundenseitig verwalteten Git-Repository zu isolieren und mit dem Git-Repository von Cloud Manager zu synchronisieren. So können Sie eine produktionsfremde Pipeline für Code-Qualitäts- und Validierungstests verwenden.

>[!VIDEO](https://video.tv.adobe.com/v/28723/?quality=12)

## Produktionsbereitstellung {#production-deployment}

Bereiten Sie Code für eine Produktionsfreigabe in einem kundenverwalteten Git-Repository vor und synchronisieren Sie mit dem Git-Repository von Cloud Manager, um eine Bereitstellung in Staging- und Produktionsumgebungen vorzunehmen.

>[!VIDEO](https://video.tv.adobe.com/v/28724/?quality=12)

## Synchronisieren von Versions-Tags {#sync-tags}

Um Einblicke in den Code zu gewähren, der in Staging- und Produktionsumgebungen bereitgestellt wurde, synchronisieren Sie Release-Tags aus einem Cloud Manager-Git-Repository in einem kundenverwalteten Git-Repository.

>[!VIDEO](https://video.tv.adobe.com/v/28725/?quality=12)

## Zusätzliche Ressourcen {#additional-resources}

* [GitHub-Ressourcen](https://docs.github.com/de/get-started/getting-started-with-git/set-up-git)
* [Git-Tutorials von Atlassian](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Git-Spickzettel](https://education.github.com/git-cheat-sheet-education.pdf)
