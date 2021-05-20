---
title: Grundlegendes zu Programm- und Programmtypen
description: Grundlegendes zu Programm- und Programmtypen - Cloud Services
exl-id: 507df619-a5b5-419a-9e38-db77541425a2
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 13%

---

# Grundlegendes zu Programmen und Programmtypen {#understanding-programs}

In Cloud Manager befindet sich die Mandantenentität ganz oben, die mehrere Programme enthalten kann. Jedes Programm kann nicht mehr als eine Produktionsumgebung und mehrere Nicht-Produktionsumgebungen enthalten.

Das folgende Diagramm zeigt die Hierarchie der Entitäten in Cloud Manager.

![image](assets/program-types1.png)

## Quellcode-Repository {#source-code-repository}

Das Cloud Manager-Programm wird automatisch mit seinem eigenen Git-Repository bereitgestellt.

Damit ein Benutzer auf das Git-Repository von Cloud Manager zugreifen kann, muss er einen Git-Client mit einem Befehlszeilen-Tool, einem eigenständigen visuellen Git-Client oder der IDE des Benutzers wie Eclipse, IntelliJ und NetBeans verwenden.

Nachdem ein Git-Client eingerichtet wurde, können Sie Ihr Git-Repository über die Cloud Manager-Benutzeroberfläche verwalten. Weitere Informationen zum Verwalten von Git mithilfe der Cloud Manager-Benutzeroberfläche finden Sie unter [Zugriff auf Git](/help/implementing/cloud-manager/accessing-git.md).

Um mit der Entwicklung der AEM Cloud-Anwendung zu beginnen, muss eine lokale Kopie des Anwendungs-Codes erstellt werden, indem Sie ihn aus dem Cloud Manager-Repository an einen Speicherort auf dem lokalen Computer auschecken, auf dem er sein Repository erstellen möchte.

```java
$ git clone {URL}
```

>[!NOTE]
>Ein Benutzer kann eine Kopie seines Codes auschecken und Änderungen am lokalen Code-Repository vornehmen. Sobald die Änderungen vorgenommen wurden, kann der Benutzer die Code-Änderungen wieder in das Remote-Code-Repository in Cloud Manager übertragen.

## Programmtypen {#program-types}

Ein Benutzer kann ein **Sandbox**- oder **Production**-Programm erstellen.

* Es wird ein *Produktionsprogramm* erstellt, um Live-Traffic zum richtigen Zeitpunkt in der Zukunft zu aktivieren.
Weitere Informationen finden Sie unter [Einführung in Produktionsprogramme](/help/onboarding/getting-access-to-aem-in-cloud/introduction-production-programs.md) .


* Ein *Sandbox-Programm* wird normalerweise erstellt, um Schulungen, Demos, Aktivierungen, POCs oder Dokumentationen durchzuführen. Es ist nicht für die Übertragung von Live-Traffic vorgesehen und wird Einschränkungen aufweisen, die ein Produktionsprogramm nicht hat. Sie umfasst Sites und Assets und wird automatisch mit einer Git-Verzweigung bereitgestellt, die Beispielcode, eine Entwicklungsumgebung und eine Nicht-Produktions-Pipeline enthält.
Weitere Informationen finden Sie unter [Einführung in Sandbox-Programme](/help/onboarding/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md) .
