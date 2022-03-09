---
title: Cloud Manager-Repositorys
description: Erfahren Sie, wie Sie Ihre Git-Repositorys in Cloud Manager erstellen, anzeigen und löschen.
exl-id: 6e1cf636-78f5-4270-9a21-38b4d5e5a0b0
source-git-commit: 6cf164093cc543fe4847859b248e70efd86efbb1
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 29%

---


# Cloud Manager-Repositorys {#cloud-manager-repos}

Erfahren Sie, wie Sie Ihre Git-Repositorys in Cloud Manager erstellen, anzeigen und löschen.

>[!NOTE]
>
>Es gibt eine Grenze von 300 Repositorys für alle Programme eines Unternehmens oder einer IMS-Organisation.

## Hinzufügen und Verwalten von Repositorys {#add-manage-repos}

Führen Sie diese Schritte aus, um Repositorys in Cloud Manager anzuzeigen und zu verwalten.

1. Klicken Sie auf der Seite **Programmübersicht** auf die Registerkarte **Repositorys** und gehen Sie zur Seite **Repositorys**.

1. Klicken Sie auf **Repository hinzufügen** um den Assistenten zu starten.

   ![Schaltfläche &quot;Repository hinzufügen&quot;](/help/implementing/cloud-manager/assets/repos/create-repo2.png)

1. Geben Sie den Namen und die Beschreibung wie gewünscht ein und klicken Sie auf **Speichern**.

   ![Dialogfeld &quot;Repository hinzufügen&quot;](/help/implementing/cloud-manager/assets/repos/repo-1.png)

Wenn der Assistent geschlossen wird, wird Ihr neues Repository in der Tabelle angezeigt.

Sie können das Repository in der Tabelle auswählen, auf die Suchschaltfläche klicken und **Repository-URL kopieren**, **Anzeigen und Aktualisieren** oder **Löschen**.

![Repository-Optionen](/help/implementing/cloud-manager/assets/repos/create-repo3.png)

In Cloud Manager erstellte Repositorys stehen Ihnen auch zur Auswahl beim Hinzufügen oder Bearbeiten von Pipelines zur Verfügung. Weitere Informationen finden Sie im Dokument . [CI/CD Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) , um mehr zu erfahren.

Für jede Pipeline gibt es ein einzelnes primäres Repository oder eine Verzweigung. Mit [Unterstützung von Git-Untermodulen](#git-submodule-support), können zur Build-Zeit viele sekundäre Verzweigungen eingeschlossen werden.

>[!NOTE]
>
>Ein Benutzer muss die Rolle **Bereitstellungsmanager** oder **Business Owner** , um ein Repository hinzufügen zu können.

## Löschen eines Repositorys {#delete-repo}

Das Löschen eines Repositorys führt dazu, dass:

* der Name des gelöschten Repositorys für neue Repositorys, die in Zukunft erstellt werden, unbrauchbar gemacht wird.
   * Die Fehlermeldung `Repository name should be unique within organization.` wird in solchen Fällen angezeigt.
* Stellen Sie sicher, dass das gelöschte Repository in Cloud Manager nicht verfügbar und nicht für die Verknüpfung mit einer Pipeline verfügbar ist.

Führen Sie diese Schritte aus, um ein Repository in Cloud Manager zu löschen.

1. Klicken Sie auf der Seite **Programmübersicht** auf die Registerkarte **Repositorys** und gehen Sie zur Seite **Repositorys**.

1. Wählen Sie das Repository aus, klicken Sie auf die Suchschaltfläche und wählen Sie **Löschen** , um das Repository zu löschen.

   ![Repository löschen](/help/implementing/cloud-manager/assets/repos/delete-repo.png)

## Unterstützung von Git-Untermodulen {#git-submodule-support}

Git-Untermodule können verwendet werden, um den Inhalt mehrerer Verzweigungen zum Build-Zeitpunkt über Git-Repositorys hinweg zusammenzuführen.

Wenn der Build-Prozess von Cloud Manager ausgeführt wird, nachdem das für die Pipeline konfigurierte Repository geklont und die konfigurierte Verzweigung ausgecheckt wurde, wird der Befehl ausgeführt, sofern die Verzweigung eine `.gitmodules`-Datei im Stammverzeichnis enthält.

Der folgende Befehl checkt jedes Untermodul in das entsprechende Verzeichnis ein.

```
$ git submodule update --init
```

Diese Technik ist eine potenzielle Alternative zur im Dokument beschriebenen Lösung. [Arbeiten mit mehreren Quell-Git-Repositorys](/help/implementing/cloud-manager/managing-code/working-with-multiple-source-git-repositories.md) für Organisationen, die mit der Verwendung von Git-Untermodulen vertraut sind und keinen externen Zusammenführungsprozess verwalten möchten.

Angenommen, es gibt drei Repositorys, die jeweils eine einzelne Verzweigung mit dem Namen `main`. Im primären Repository, d. h. dem in den Pipelines konfigurierten, wird die `main` Verzweigung hat `pom.xml` Datei, in der die in den beiden anderen Repositorys enthaltenen Projekte deklariert werden.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
    <modelVersion>4.0.0</modelVersion>
   
    <groupId>customer.group.id</groupId>
    <artifactId>customer-reactor</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <packaging>pom</packaging>
   
    <modules>
        <module>project-a</module>
        <module>project-b</module>
    </modules>
   
</project>
```

Anschließend fügen Sie Untermodule für die beiden anderen Repositorys hinzu.

```shell
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectA/ project-a
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectB/ project-b
```

Dies führt zu einer `.gitmodules` -Datei ähnlich der folgenden.

```text
[submodule "project-a"]
    path = project-a
    url = https://git.cloudmanager.adobe.com/ProgramName/projectA/
    branch = main
[submodule "project-b"]
    path = project-b
    url = https://git.cloudmanager.adobe.com/ProgramName/projectB/
    branch = main
```

Weitere Informationen zu Git-Untermodulen finden Sie im [Git-Referenzhandbuch.](https://git-scm.com/book/de/v2/Git-Tools-Submodules)

### Einschränkungen und Empfehlungen {#limitations-recommendations}

Beachten Sie bei der Verwendung von Git-Untermodulen die folgenden Einschränkungen.

* Die Git-URL muss sich genau in der im vorherigen Abschnitt beschriebenen Syntax befinden.
* Es werden nur Untermodule im Stammverzeichnis der Verzweigung unterstützt.
* Betten Sie aus Sicherheitsgründen keine Anmeldeinformationen in Git-URLs ein.
* Sofern nicht anders erforderlich, wird dringend empfohlen, flache Untermodule zu verwenden.
   * Führen Sie dazu `git config -f .gitmodules submodule.<submodule path>.shallow true` für jedes Untermodul aus.
* Git-Untermodulverweise werden für bestimmte Git-Commits gespeichert. Wenn also Änderungen am Submodul-Repository vorgenommen werden, muss der referenzierte Commit aktualisiert werden.
   * Verwenden Sie beispielsweise `git submodule update --remote`
