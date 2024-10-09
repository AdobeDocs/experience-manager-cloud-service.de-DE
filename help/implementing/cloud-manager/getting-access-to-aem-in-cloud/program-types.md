---
title: Programme und Programmtypen
description: Erfahren Sie mehr über die Hierarchie von Cloud Manager und darüber, wie die verschiedenen Arten von Programmen in die Struktur passen und wie sie sich unterscheiden.
exl-id: 507df619-a5b5-419a-9e38-db77541425a2
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: dc4008a33f6a786884a9aad30096ff4f0561346c
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 52%

---


# Programme und Programmtypen {#understanding-programs}

Cloud Manager basiert auf einer Hierarchie von Entitäten. Die Details sind für Ihre alltägliche Arbeit in Cloud Manager nicht von entscheidender Bedeutung, aber ein Überblick kann Ihnen dabei helfen, Programme zu verstehen und eigene einzurichten.

![Cloud Manager-Hierarchie](assets/program-types1.png)

* **TENANT** - Der Anfang der Hierarchie. Jedem Kunden wird ein Mandant zugewiesen.
* **PROGRAMME**: Jeder Mandant verfügt über ein oder mehrere Programme, [die häufig die lizenzierten Lösungen der Kundin bzw. des Kunden widerspiegeln](introduction-production-programs.md).
* **UMGEBUNGEN**: Jedes Programm verfügt über mehrere Umgebungen, z. B. die Produktion für Live-Inhalte, eine für Staging und eine für Entwicklungszwecke.
   * Jedes Programm kann nur eine Produktionsumgebung, aber mehrere produktionsfremde Umgebungen haben.
* **REPOSITORY** - Programme verfügen über Git-Repositorys, in denen Anwendung und Frontend-Code für die Umgebungen verwaltet werden.
* **TOOLS UND WORKFLOWS**: Pipelines verwalten die Bereitstellung von Code aus den Repositorys in die Umgebungen, während andere Tools den Zugriff auf Protokolle, Überwachung und Umgebungsverwaltung ermöglichen.

Oft ist ein Beispiel hilfreich, um diese Hierarchie zu kontextualisieren.

* WKND Travel and Adventure Enterprises könnte ein **Mandant** sein, der sich auf Medien zum Thema Reisen konzentriert.
* Der Mandant WKND Travel and Adventure Enterprises könnte über zwei **Programme** verfügen: ein Sites-Programm für WKND Magazine und ein Assets-Programm für WKND Media.
* Die Programme WKND Magazine und WKND Media hätten beide Entwicklungs-, Staging- und Produktions-**Umgebungen**.

## Quell-Code-Repository {#source-code-repository}

Ein Cloud Manager-Programm wird automatisch mit einem eigenen Git-Repository bereitgestellt.

Benutzer können über einen Git-Client mit einem Befehlszeilen-Tool oder einem eigenständigen visuellen Git-Client auf das Cloud Manager-Git-Repository zugreifen. Alternativ können sie ihre bevorzugte integrierte Entwicklungsumgebung (IDE) wie Eclipse, IntelliJ oder NetBeans verwenden.

Nachdem ein Git-Client eingerichtet wurde, können Sie Ihr Git-Repository über die Cloud Manager-Benutzeroberfläche verwalten. Weitere Informationen zum Verwalten von Git mithilfe der Cloud Manager-Benutzeroberfläche finden Sie unter [Zugriff auf Git](/help/implementing/cloud-manager/managing-code/accessing-repos.md).

Um mit der Entwicklung der AEM Cloud-Anwendung zu beginnen, überprüfen Sie den Anwendungscode aus dem Cloud Manager-Repository auf Ihren lokalen Computer.

```java
$ git clone {URL}
```

Der Workflow folgt einem standardmäßigen Git-Prozess:

1. Ein Benutzer klont das Remote-Git-Repository lokal.
1. Der Benutzer nimmt Änderungen an seinem lokalen Repository vor.
1. Wenn die Änderungen fertig sind, sendet der Benutzer sie zurück in das Remote-Git-Repository.

Der einzige Unterschied besteht darin, dass das Remote-Git-Repository Teil von Cloud Manager ist, das für Entwickler transparent ist.

## Programmtypen {#program-types}

Benutzende können ein **Produktionsprogramm** oder ein **Sandbox-Programm** erstellen.

* Ein **Produktionsprogramm** wird erstellt, um Live-Traffic für Ihre Site zu ermöglichen.
   * Weitere Informationen finden Sie in der [Einführung in Produktionsprogramme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-production-programs.md).
* Ein **Sandbox-Programm** wird normalerweise für Schulungen, Ausführungen von Demos, Aktivierungen, Konzeptnachweise oder Dokumentation erstellt.
   * Eine Sandbox-Umgebung ist nicht dafür vorgesehen, Live-Traffic zu verarbeiten, und hat Einschränkungen, die ein Produktionsprogramm nicht hat.
   * Es umfasst Sites, Assets und Edge Delivery Services und wird vorab mit einer Git-Verzweigung gefüllt, die Beispielcode, eine Entwicklungsumgebung und eine Nicht-Produktions-Pipeline enthält.
   * Weitere Informationen finden Sie in der [Einführung in Sandbox-Programme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md).
