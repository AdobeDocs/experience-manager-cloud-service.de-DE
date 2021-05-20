---
title: Integrieren mit Git
description: Integrieren mit Git – Cloud Services
exl-id: 57e71b8a-4546-4d7f-825c-a1637d08e608
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 100%

---

# Integrieren von Git mit Adobe Cloud Manager {#git-integration}

Adobe Cloud Manager verfügt über ein einzelnes Git-Repository, das der Bereitstellung von Code unter Verwendung der CI/CD-Pipelines von Cloud Manager dient. Kunden können das Git-Repository von Cloud Manager sofort verwenden. Außerdem haben Kunden die Möglichkeit, ein On-Premise- oder **kundenverwaltetes** Git-Repository mit Cloud Manager zu integrieren.

## Übersicht über die Git-Integration     {#git-integration-overview}

>[!VIDEO](https://video.tv.adobe.com/v/28710/)

In dieser Videoreihe werden verschiedene Anwendungsfälle bei der Integration eines kundenverwalteten Git-Repository mit Cloud Manager untersucht, darunter:

* [Erstsynchronisierung](#initial-sync)
* [Standard-Verzweigungsstrategie](#branching-strategy)
* [Entwicklung von Funktionsverzweigungen](#feature-development)
* [Produktionsimplementierung](#production-deployment)
* [Synchronisieren von Release-Tags](#sync-tags)

Die Videoreihe setzt grundlegende Kenntnisse der Git- und Quellcodeverwaltung voraus. Weitere Informationen zu Git finden Sie in den [folgenden zusätzlichen Ressourcen](#additional-resources).

>[!NOTE]
>
>Die Schritte und Benennungskonventionen in dieser Videoreihe präsentieren mehrere Best Practices für die Arbeit mit einem kundenverwalteten Git-Repository und Cloud Manager. Es wird erwartet, dass die dargelegten Konventionen und Arbeitsabläufe für einzelne Entwicklungsteams angepasst werden.

## Erstsynchronisierung {#initial-sync}

Erste Schritte zum Synchronisieren eines kundenverwalteten Git-Repository mit dem Git-Repository von Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/28711/?quality=12)

## Standard-Verzweigungsstrategie {#branching-strategy}

Im folgenden Video erfahren Sie mehr über die Standard-Verzweigungsstrategien.

>[!VIDEO](https://video.tv.adobe.com/v/28712/?quality=12)

## Entwicklung von Funktionsverzweigungen {#feature-development}

Verwenden Sie eine Funktionsverzweigung, um Codeänderungen in einem kundenverwalteten Git-Repository zu isolieren und mit dem Git-Repository von Cloud Manager zu synchronisieren; so können Sie eine Nicht-Produktions-Pipeline für Codequalität- und Validierungstests verwenden.

>[!VIDEO](https://video.tv.adobe.com/v/28723/?quality=12)

## Produktionsbereitstellung {#production-deployment}

Bereiten Sie Code für die Produktionsfreigabe in einem kundenverwalteten Git-Repository vor und synchronisieren Sie mit dem Git-Repository von Cloud Manager, um eine Bereitstellung in Staging- und Produktionsumgebungen vorzunehmen.

>[!VIDEO](https://video.tv.adobe.com/v/28724/?quality=12)

## Synchronisieren von Release-Tags {#sync-tags}

Synchronisieren Sie Release-Tags aus einem Cloud Manager-Git-Repository in einem kundenverwalteten Git-Repository, um für Sichtbarkeit des in Staging- und Produktionsumgebungen bereitgestellten Codes zu sorgen.

>[!VIDEO](https://video.tv.adobe.com/v/28725/?quality=12)

## Zusätzliche Ressourcen {#additional-resources}

* [GitHub-Ressourcen](https://try.github.io)
* [Git-Tutorials von Atlassian](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Git-Schnellübersicht](https://education.github.com/git-cheat-sheet-education.pdf)
