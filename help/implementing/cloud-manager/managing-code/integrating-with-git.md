---
title: Verwenden von Git mit Cloud Manager
description: Erfahren Sie, wie Sie die Git-Repositorys von Cloud Manager verwenden und Ihr eigenes, On-Premise kundenverwaltetes Git-Repository in Cloud Manager integrieren.
exl-id: 57e71b8a-4546-4d7f-825c-a1637d08e608
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 100%

---

# Verwenden von Git mit Cloud Manager {#git-integration}

Adobe Cloud Manager verfügt über ein einzelnes Git-Repository, das der Bereitstellung von Code unter Verwendung der CI/CD-Pipelines von Cloud Manager dient.

Sie können das Git-Repository von Cloud Manager vorkonfiguriert verwenden. Sie haben aber auch die Möglichkeit, ein kundenverwaltetes Git-Repository in Cloud Manager zu integrieren.

## Überblick über die Git-Integration {#git-integration-overview}

In dieser Videoreihe werden verschiedene Anwendungsfälle für die Integration eines kundenverwalteten Git-Repositorys in Cloud Manager untersucht, darunter:

* [Erstsynchronisierung](#initial-sync)
* [Grundlegende Verzweigungsstrategie](#branching-strategy)
* [Entwicklung von Funktionsverzweigungen](#feature-development)
* [Produktionsbereitstellung](#production-deployment)
* [Synchronisieren von Versions-Tags](#sync-tags)

Die Videoreihe setzt grundlegende Kenntnisse der Git- und Quell-Code-Verwaltung voraus. Weitere Informationen zu Git finden Sie in den [folgenden zusätzlichen Ressourcen](#additional-resources).

>[!VIDEO](https://video.tv.adobe.com/v/33718?captions=ger)

Die Schritte und Benennungskonventionen in dieser Videoreihe präsentieren mehrere Best Practices für die Arbeit mit einem kundenverwalteten Git-Repository und Cloud Manager. Es wird erwartet, dass die dargestellten Konventionen und Workflows für einzelne Anwendungsfälle angepasst werden.

## Erstsynchronisierung {#initial-sync}

In diesem Video erfahren Sie die ersten Schritte zum Synchronisieren eines kundenverwalteten Git-Repositorys mit dem Git-Repository von Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/33717/?captions=ger&quality=12)

## Grundlegende Verzweigungsstrategie {#branching-strategy}

In diesem Video erfahren Sie grundlegende Verzweigungsstrategien.

>[!VIDEO](https://video.tv.adobe.com/v/33716/?captions=ger&quality=12)

## Entwicklung von Funktionsverzweigungen {#feature-development}

Verwenden Sie eine Funktionsverzweigung, um Code-Änderungen in einem kundenverwalteten Git-Repository zu isolieren und mit dem Git-Repository von Cloud Manager zu synchronisieren. So können Sie eine produktionsfremde Pipeline für Code-Qualität- und Validierungstests verwenden.

>[!VIDEO](https://video.tv.adobe.com/v/33715/?captions=ger&quality=12)

## Produktionsbereitstellung {#production-deployment}

Bereiten Sie Code für die Produktionsfreigabe in einem kundenverwalteten Git-Repository vor und synchronisieren Sie mit dem Git-Repository von Cloud Manager, um eine Bereitstellung in Staging- und Produktionsumgebungen vorzunehmen.

>[!VIDEO](https://video.tv.adobe.com/v/328889/?captions=ger&quality=12)

## Synchronisieren von Versions-Tags {#sync-tags}

Synchronisieren Sie Versions-Tags aus einem Cloud Manager-Git-Repository in einem kundenverwalteten Git-Repository, um für Sichtbarkeit des in Staging- und Produktionsumgebungen bereitgestellten Codes zu sorgen.

>[!VIDEO](https://video.tv.adobe.com/v/33713/?captions=ger&quality=12)

## Zusätzliche Ressourcen {#additional-resources}

* [GitHub-Ressourcen](https://docs.github.com/de/get-started/getting-started-with-git/set-up-git)
* [Git-Tutorials von Atlassian](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Git-Schnellübersicht](https://education.github.com/git-cheat-sheet-education.pdf)
