---
title: Quellcode-Repository - Cloud-Dienste
description: Quellcode-Repository - Cloud-Dienste
translation-type: tm+mt
source-git-commit: 114bc678fc1c6e3570d6d2a29bc034feb68aa56d
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 23%

---


# Quellcode-Repository {#source-code-repository}

Cloud Manager-Programm wird automatisch mit seinem eigenen Git-Repository bereitgestellt.

Damit ein Benutzer auf das Cloud Manager-Git-Repository zugreifen kann, muss er einen Git-Client mit einem Befehlszeilenwerkzeug, einem eigenständigen visuellen Git-Client oder der IDE des Benutzers wie Eclipse, IntelliJ, NetBeans verwenden.

Nachdem ein Git-Client eingerichtet wurde, können Sie Ihr Git-Repository über die Benutzeroberfläche von Cloud Manager verwalten. Weitere Informationen zur Verwaltung von Git mithilfe der Benutzeroberfläche von Cloud Manager finden Sie unter [Zugriff auf Git](/help/implementing/cloud-manager/accessing-git.md).

Um mit der Entwicklung der AEM Cloud-Anwendung zu beginnen, muss der Anwendungscode lokal kopiert werden, indem er vom Cloud Manager-Repository an einen Speicherort auf dem lokalen Computer ausgecheckt wird, auf dem er sein Repository erstellen möchte.

```java
$ git clone {URL}
```

>[!NOTE]
>
> Ein Benutzer kann eine Kopie seines Codes auschecken und Änderungen am lokalen Code-Repository vornehmen. Sobald die Änderungen vorgenommen wurden, kann der Benutzer die Code-Änderungen wieder in das Remote-Code-Repository in Cloud Manager übertragen.
