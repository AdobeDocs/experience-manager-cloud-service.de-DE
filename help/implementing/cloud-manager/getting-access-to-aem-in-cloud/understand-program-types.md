---
title: Grundlegendes zu Programmen und Programmtypen
description: Grundlegendes zu Programmen und Programmtypen – Cloud Services
exl-id: 507df619-a5b5-419a-9e38-db77541425a2
source-git-commit: 7e51fb98c76a5913ef237aca3b66c73a8263f4ff
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 100%

---

# Grundlegendes zu Programmen und Programmtypen {#understanding-programs}

In Cloud Manager befindet sich die Mandantenentität ganz oben. Sie kann mehrere Programme enthalten. Jedes Programm kann maximal eine Produktionsumgebung und mehrere produktionsfremde Umgebungen enthalten.

Das folgende Diagramm zeigt die Hierarchie der Entitäten in Cloud Manager.

![image](assets/program-types1.png)

## Quell-Code-Repository {#source-code-repository}

Das Cloud Manager-Programm wird automatisch mit seinem eigenen Git-Repository bereitgestellt.

Damit ein Benutzer auf das Git-Repository von Cloud Manager zugreifen kann, muss er einen Git-Client mit einem Befehlszeilen-Tool, einen eigenständigen visuellen Git-Client oder die IDE des Benutzers wie Eclipse, IntelliJ und NetBeans verwenden.

Nachdem ein Git-Client eingerichtet wurde, können Sie Ihr Git-Repository über die Cloud Manager-Benutzeroberfläche verwalten. Weitere Informationen zum Verwalten von Git mithilfe der Cloud Manager-Benutzeroberfläche finden Sie unter [Zugriff auf Git](/help/implementing/cloud-manager/managing-code/accessing-repos.md).

Um mit der Entwicklung der AEM Cloud-Anwendung zu beginnen, muss eine lokale Kopie des Anwendungs-Codes erstellt werden, indem Sie ihn aus dem Cloud Manager-Repository an einen Speicherort auf dem lokalen Computer, auf dem jemand sein Repository erstellen möchte, auschecken.

```java
$ git clone {URL}
```

>[!NOTE]
>Ein Benutzer kann eine Kopie seines Codes auschecken und Änderungen am lokalen Code-Repository vornehmen. Sobald die Änderungen vorgenommen wurden, kann der Benutzer die Code-Änderungen wieder in das Remote-Code-Repository in Cloud Manager übertragen.

## Programmtypen {#program-types}

Ein Benutzer kann ein **Sandbox-** oder ein **Produktionsprogramm** erstellen.

* Ein *Produktionsprogramm* wird erstellt, um Live-Traffic zum richtigen Zeitpunkt in der Zukunft zu aktivieren.
Weitere Informationen finden Sie unter [Einführung in Produktionsprogramme](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/production-programs/introduction-production-programs.html?lang=de).


* Ein *Sandbox-Programm* wird normalerweise für Schulungen, Demos, Aktivierungen, Konzeptnachweise oder Dokumentation erstellt. Es soll keinen Live-Traffic verarbeiten und hat Einschränkungen eingeführt, die ein Produktionsprogramm nicht hat. Es umfasst Sites und Assets und wird automatisch mit einer Git-Verzweigung geliefert, die Beispiel-Code, eine Entwicklungsumgebung und eine produktionsfremde Pipeline enthält.
Weitere Informationen finden Sie unter [Einführung in Sandbox-Programme](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/sandbox-programs/introduction-sandbox-programs.html?lang=de).
