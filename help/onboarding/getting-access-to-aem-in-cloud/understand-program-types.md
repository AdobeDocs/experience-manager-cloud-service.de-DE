---
title: Informationen zu Programm- und Programm-Typen
description: Programm- und Programm-Typen - Cloud Services
translation-type: tm+mt
source-git-commit: 6e8cf08ec3f85437a8472a45895f3818e473e98c
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 13%

---


# Grundlegendes zu Programmen und Programmtypen {#understanding-programs}

In Cloud Manager befindet sich die Mandant-Entität ganz oben, die mehrere Programm enthalten kann. Jedes Programm kann maximal eine Produktions-Umgebung und mehrere Nicht-Produktions-Umgebung enthalten.

Das folgende Diagramm zeigt die Hierarchie der Entitäten in Cloud Manager.

![image](assets/program-types1.png)

## Quellcode-Repository {#source-code-repository}

Cloud Manager-Programm wird automatisch mit seinem eigenen Git-Repository bereitgestellt.

Damit ein Benutzer auf das Cloud Manager-Git-Repository zugreifen kann, muss er einen Git-Client mit einem Befehlszeilenwerkzeug, einem eigenständigen visuellen Git-Client oder der IDE des Benutzers wie Eclipse, IntelliJ, NetBeans verwenden.

Nachdem ein Git-Client eingerichtet wurde, können Sie Ihr Git-Repository über die Benutzeroberfläche von Cloud Manager verwalten. Weitere Informationen zum Verwalten von Git mithilfe der Benutzeroberfläche von Cloud Manager finden Sie unter [Zugriff auf Git](/help/implementing/cloud-manager/accessing-git.md).

Um mit der Entwicklung der AEM Cloud-Anwendung zu beginnen, muss der Anwendungscode lokal kopiert werden, indem er vom Cloud Manager-Repository an einen Speicherort auf dem lokalen Computer, auf dem er sein Repository erstellen möchte, ausgecheckt wird.

```java
$ git clone {URL}
```

>[!NOTE]
>Ein Benutzer kann eine Kopie seines Codes auschecken und Änderungen am lokalen Code-Repository vornehmen. Sobald die Änderungen vorgenommen wurden, kann der Benutzer die Code-Änderungen wieder in das Remote-Code-Repository in Cloud Manager übertragen.

## Programm-Typen {#program-types}

Ein Benutzer kann ein **Sandbox**- oder ein **Production**-Programm erstellen.

* Ein *Produktions-Programm* wird erstellt, um Live-Traffic zum richtigen Zeitpunkt in der Zukunft zu aktivieren.
Weitere Informationen finden Sie unter [Einführung in die Produktions-Programm](/help/onboarding/getting-access-to-aem-in-cloud/introduction-production-programs.md).


* Ein *Sandbox-Programm* wird normalerweise für Schulungszwecke, die Ausführung von Demos, die Aktivierung, POCs oder Dokumentation erstellt. Es soll keinen Live-Traffic transportieren, und es werden Beschränkungen eingeführt, die ein Production-Programm nicht hat. Es umfasst Sites und Assets und wird automatisch mit einer Git-Verzweigung geliefert, die Beispielcode, eine Dev-Umgebung und eine Nicht-Produktions-Pipeline enthält.
Weitere Informationen finden Sie unter [Einführung in Sandbox-Programm](/help/onboarding/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md).

