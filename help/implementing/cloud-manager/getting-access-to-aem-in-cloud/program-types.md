---
title: Programme und Programmtypen
description: Erfahren Sie mehr über die Hierarchie von Cloud Manager und darüber, wie die verschiedenen Arten von Programmen in die Struktur passen und wie sie sich unterscheiden.
exl-id: 507df619-a5b5-419a-9e38-db77541425a2
source-git-commit: 74e17ccb93c97dd6881c9b63d9a2d784d3add430
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 100%

---


# Programme und Programmtypen {#understanding-programs}

Cloud Manager basiert auf einer Hierarchie von Entitäten. Die Details dazu sind für Ihre alltägliche Arbeit in Cloud Manager nicht entscheidend. Ein Überblick darüber hilft Ihnen jedoch, Programme zu verstehen und Ihre eigenen einzurichten.

![Cloud Manager-Hierarchie](assets/program-types1.png)

* **MANDANT**: Dies ist die Spitze der Hierarchie. Jedem Kunden wird ein Mandant zugewiesen.
* **PROGRAMME**: Jeder Mandant verfügt über ein oder mehrere Programme, [die häufig die lizenzierten Lösungen des Kunden widerspiegeln](introduction-production-programs.md).
* **UMGEBUNGEN**: Jedes Programm verfügt über mehrere Umgebungen, z. B. die Produktion für Live-Inhalte, eine für Staging und eine für Entwicklungszwecke.
   * Jedes Programm kann nur eine Produktionsumgebung, aber mehrere produktionsfremde Umgebungen haben.
* **REPOSITORY**: Programme verfügen über Git-Repositorys, in denen Programme und Frontend-Code für die Umgebungen gepflegt werden.
* **TOOLS UND WORKFLOWS**: Pipelines verwalten die Implementierung von Code aus den Repositorys in die Umgebungen, während andere Tools den Zugriff auf Protokolle, Überwachung und Umgebungsverwaltung ermöglichen.

Oft ist ein Beispiel hilfreich, um diese Hierarchie zu kontextualisieren.

* WKND Travel and Adventure Enterprises könnte ein **Mandant** sein, der sich auf Medien zum Thema Reisen konzentriert.
* Der Mandant WKND Travel and Adventure Enterprises könnte über zwei **Programme** verfügen: ein Sites-Programm für WKND Magazine und ein Assets-Programm für WKND Media.
* Die Programme WKND Magazine und WKND Media hätten beide Entwicklungs-, Staging- und Produktions-**Umgebungen**.

## Quell-Code-Repository {#source-code-repository}

Das Cloud Manager-Programm wird automatisch mit seinem eigenen Git-Repository bereitgestellt.

Damit ein Benutzer auf das Git-Repository von Cloud Manager zugreifen kann, muss er einen Git-Client mit einem Befehlszeilen-Tool, einen eigenständigen visuellen Git-Client oder die IDE des Benutzers wie Eclipse, IntelliJ oder NetBeans verwenden.

Nachdem ein Git-Client eingerichtet wurde, können Sie Ihr Git-Repository über die Cloud Manager-Benutzeroberfläche verwalten. Weitere Informationen zum Verwalten von Git mithilfe der Cloud Manager-Benutzeroberfläche finden Sie im Dokument [Zugriff auf Git.](/help/implementing/cloud-manager/managing-code/accessing-repos.md)

Um mit der Entwicklung der AEM Cloud-Anwendung zu beginnen, muss eine lokale Kopie des Anwendungs-Codes erstellt werden, indem Sie ihn aus dem Cloud Manager-Repository an einen Speicherort auf dem lokalen Computer auschecken.

```java
$ git clone {URL}
```

Der Workflow ist somit ein standardmäßiger Git-Workflow.

1. Ein Benutzer klont eine lokale Kopie des Git-Repositorys.
1. Der Benutzer nimmt Änderungen am lokalen Code-Repository vor.
1. Wenn er damit fertig sind, sendet der Benutzer sie zurück zum Remote-Git-Repository.

Der einzige Unterschied besteht darin, dass das Remote-Git-Repository Teil von Cloud Manager ist, der für Entwickler transparent ist.

## Programmtypen {#program-types}

Ein Benutzer kann ein **Produktions-** oder ein **Sandbox-** Programm erstellen.

* Ein **Produktionsprogramm** wird erstellt, um Live-Traffic für Ihre Site zu ermöglichen.
   * Weitere Informationen finden Sie im Dokument [Einführung in Produktionsprogramme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-production-programs.md).
* Ein **Sandbox-Programm** wird normalerweise für Schulungen, Ausführungen von Demos, Aktivierungen, Konzeptnachweise oder Dokumentation erstellt.
   * Eine Sandbox-Umgebung soll keinen Live-Traffic verarbeiten und hat Einschränkungen, die ein Produktionsprogramm nicht hat.
   * Sie umfasst Sites und Assets und wird automatisch mit einer Git-Verzweigung geliefert, die Beispiel-Code, eine Entwicklungsumgebung und eine produktionsfremde Pipeline enthält.
   * Weitere Informationen finden Sie im Dokument [Einführung in Sandbox-Programme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md).
