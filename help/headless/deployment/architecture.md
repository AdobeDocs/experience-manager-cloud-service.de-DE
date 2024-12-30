---
title: Architektur von AEM Headless
description: Erfahren Sie mehr über die allgemeine Architektur für Adobe Experience Manager im Zusammenhang mit einer Headless-Bereitstellung. Machen Sie sich mit der Rolle der AEM-Autoren-, Vorschau- und Veröffentlichungs-Services und dem empfohlenen Bereitstellungsmuster für Headless-Programme vertraut.
feature: Headless, Content Fragments,GraphQL API
exl-id: 5ba6921f-b06e-463d-b956-d1fb434090c9
role: Admin, Developer
source-git-commit: 6719e0bcaa175081faa8ddf6803314bc478099d7
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 100%

---

# Architektur von AEM Headless

Eine typische AEM-Umgebung besteht aus einem Autoren-Service, einem Veröffentlichungs-Service und einem optionalen Vorschau-Service.

* **Der Autoren-Service**, mit dem interne Anwender Inhalte erstellen, verwalten und in der Vorschau anzeigen.

* **Der Veröffentlichungs-Service** fungiert als „Live-Umgebung“ und ist in der Regel der Bereich, mit die Endanwender interagieren. Inhalte werden nach der Bearbeitung und Genehmigung im Autoren-Service an den Veröffentlichungs-Service weitergeleitet. Das häufigste Bereitstellungsmuster bei AEM Headless-Programmen besteht darin, die Produktionsversion des Programms mit dem Veröffentlichungs-Service von AEM zu verbinden.

* **Der Vorschau-Service** ist funktionell identisch mit dem **Veröffentlichungs-Service**. Er wird jedoch nur internen Benutzern zur Verfügung gestellt. Das macht ihn zu einem idealen System für Genehmiger, die bevorstehende Inhaltsänderungen überprüfen, bevor sie für Endbenutzer live geschaltet werden.

* **Der Dispatcher** ist ein statischer Webserver, der durch das AEM Dispatcher-Modul erweitert wird. Er bietet Caching-Funktionen und eine weitere Sicherheitsebene. Der **Dispatcher** befindet sich vor den **Veröffentlichungs-** und **Vorschau-** Services.

Innerhalb eines AEM as a Cloud Service-Programms können Sie über mehrere Umgebungen verfügen: Entwicklung, Staging und Produktion. Jede Umgebung verfügt über ihre eigenen **Autoren-**, **Veröffentlichungs-** und **Vorschau-** Services. Weitere Informationen finden Sie unter [Verwalten von Umgebungen](/help/implementing/cloud-manager/manage-environments.md).

## Modell der Autoren- und Veröffentlichungsinstanz

Das häufigste Bereitstellungsmuster bei AEM Headless-Programmen besteht darin, die Produktionsversion des Programms mit dem Veröffentlichungs-Service von AEM zu verbinden.

![Architektur der Autoren- und Veröffentlichungsinstanz](assets/autho-publish-architecture-diagram.png)

Das obige Diagramm zeigt dieses allgemeine Bereitstellungsmuster.

1. Ein **Inhaltsautor** verwendet den AEM-Autoren-Service zum Erstellen, Bearbeiten und Verwalten von Inhalten.
1. Der **Inhaltsautor** und andere interne Benutzern können die Inhalte direkt im Autoren-Service in der Vorschau anzeigen. Es kann eine Vorschauversion des Programms eingerichtet werden, die eine Verbindung zum Autoren-Service herstellt.
1. Nachdem die Inhalte genehmigt wurden, können sie im AEM-Veröffentlichungs-Service veröffentlicht werden.
1. Der **Dispatcher** ist eine Ebene vor dem **Veröffentlichungs**-Service, die bestimmte Anforderungen zwischenspeichern kann und eine Sicherheitsebene bietet.
1. Endbenutzer interagieren mit der Produktionsversion des Programms. Das Produktionsprogramm stellt über den Dispatcher eine Verbindung zum Veröffentlichungs-Service her und verwendet die GraphQL-APIs, um Inhalte anzufragen und zu nutzen.

## Autorenvorschau der Bereitstellung der Veröffentlichungsinstanz

Eine weitere Option für Headless-Bereitstellungen besteht darin, einen **AEM-Vorschau**-Service einzubinden. Mit diesem Ansatz können Inhalte zuerst im **Vorschau**-Service veröffentlicht werden und eine Vorschauversion des Headless-Programms kann eine Verbindung dazu herstellen. Der Vorteil dieses Ansatzes besteht darin, dass der **Vorschau**-Service mit denselben Authentifizierungsanforderungen und -berechtigungen eingerichtet werden kann wie der **Veröffentlichungs-** Service, was die Simulation des Produktionserlebnisses erleichtert.

![Architektur der Autorenvorschau und Veröffentlichungsinstanz](assets/author-preview-publish-architecture-diagram.png)

1. Ein **Inhaltsautor** verwendet den AEM-Autoren-Service zum Erstellen, Bearbeiten und Verwalten von Inhalten.
1. Die Inhalte werden zuerst im AEM-Vorschau-Service veröffentlicht.
1. Es kann eine Vorschauversion des Programms eingerichtet werden, die eine Verbindung zum Vorschau-Service herstellt.
1. Sobald Inhalte geprüft und genehmigt wurden, können sie im AEM-Veröffentlichungs-Service veröffentlicht werden.
1. Endbenutzer interagieren mit der Produktionsversion des Programms. Das Produktionsprogramm stellt über den Dispatcher eine Verbindung zum Veröffentlichungs-Service her und verwendet die GraphQL-APIs, um Inhalte anzufragen und zu nutzen.
