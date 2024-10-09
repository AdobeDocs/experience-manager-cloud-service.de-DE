---
title: Unterstützung von Git-Untermodulen
description: Erfahren Sie, wie Sie Git-Untermodule dazu verwenden können, den Inhalt mehrerer Verzweigungen zum Build-Zeitpunkt über Git-Repositorys hinweg zusammenzuführen.
exl-id: fa5b0f49-4b87-4f39-ad50-7e62094d85f4
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: dc4008a33f6a786884a9aad30096ff4f0561346c
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 24%

---

# Unterstützung von Git-Untermodulen für Adobe-Repositorys {#git-submodule-support}

Git-Untermodule können verwendet werden, um zum Build-Zeitpunkt den Inhalt mehrerer Verzweigungen über Git-Repositorys hinweg zusammenzuführen.

Wenn der Build-Prozess von Cloud Manager ausgeführt wird, klont er das Repository der Pipeline und checkt die Verzweigung aus. Wenn eine `.gitmodules` -Datei im Stammverzeichnis der Verzweigung vorhanden ist, wird der entsprechende Befehl ausgeführt.

Der folgende Befehl checkt jedes Untermodul in das entsprechende Verzeichnis aus.

```
$ git submodule update --init
```

Diese Technik bietet eine Alternative zu der unter [Arbeiten mit mehreren Source-Git-Repositorys](/help/implementing/cloud-manager/managing-code/working-with-multiple-source-git-repositories.md) beschriebenen Lösung. Es ist ideal für Unternehmen, die sich mit Git-Untermodulen auskennen und es vorziehen, keinen externen Zusammenführungsprozess zu verwalten.

Angenommen, es gibt drei Repositorys. Jedes Repository enthält eine einzelne Verzweigung mit dem Namen `main`. Im primären Repository, d. h. dem in den Pipelines konfigurierten, verfügt die `main` -Verzweigung über eine `pom.xml` -Datei, die die in den anderen beiden Repositorys enthaltenen Projekte deklariert:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="https://maven.apache.org/POM/4.0.0" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="https://maven.apache.org/POM/4.0.0 https://maven.apache.org/maven-v4_0_0.xsd">
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

Anschließend fügen Sie Untermodule für die beiden anderen Repositorys hinzu:

```shell
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectA/ project-a
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectB/ project-b
```

Das Ergebnis ist eine `.gitmodules` -Datei ähnlich der folgenden:

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

Weitere Informationen zu Git-Untermodulen finden Sie im [Git-Referenzhandbuch](https://git-scm.com/book/de/v2/Git-Tools-Submodules) .

## Einschränkungen und Empfehlungen {#limitations-recommendations}

Beachten Sie bei der Verwendung von Git-Untermodulen mit von Adobe verwalteten Repositorys die folgenden Einschränkungen.

* Die Git-URL muss sich genau in der im vorherigen Abschnitt beschriebenen Syntax befinden.
* Es werden nur Untermodule im Stammverzeichnis der Verzweigung unterstützt.
* Betten Sie aus Sicherheitsgründen keine Anmeldeinformationen in Git-URLs ein.
* Sofern nicht anders erforderlich, empfiehlt Adobe die Verwendung von flachen Untermodulen, indem Sie Folgendes ausführen:
  `git config -f .gitmodules submodule.<submodule path>.shallow true` für jedes Untermodul.
* Für bestimmte Git-Commits werden Git-Untermodulverweise gespeichert. Wenn also Änderungen am Submodul-Repository vorgenommen werden, muss die referenzierte Commit aktualisiert werden.
Verwenden Sie beispielsweise Folgendes:

  `git submodule update --remote`

## Unterstützung von Git-Untermodulen für private Repositorys {#private-repositories}

Die Unterstützung für Git-Untermodule in [privaten Repositorys](private-repositories.md) ähnelt im Allgemeinen ihrer Verwendung mit Adobe-Repositorys.

Nachdem Sie jedoch Ihre `pom.xml` -Datei konfiguriert und die `git submodule` -Befehle ausgeführt haben, müssen Sie eine `.gitmodules` -Datei zum Stammverzeichnis des Aggregator-Repositorys hinzufügen, damit Cloud Manager die Konfiguration des Untermoduls erkennt.

![.gitmodules-Datei](assets/gitmodules.png)

![Aggregator](assets/aggregator.png)

### Einschränkungen und Empfehlungen {#limitations-recommendations-private-repos}

Beachten Sie bei der Verwendung von Git-Untermodulen mit privaten Repositorys die folgenden Einschränkungen:

* Git-URLs von Untermodulen können im HTTPS- oder SSH-Format vorliegen, müssen aber auf ein GitHub.com -Repository verweisen. Das Hinzufügen eines Adobe-Repository-Untermoduls zu einem GitHub-Aggregator-Repository oder umgekehrt wird nicht unterstützt.
* GitHub-Untermodule müssen über die Adobe GitHub-App zugänglich sein.
* [Die Einschränkungen bei der Verwendung von Git-Untermodulen mit von Adobe verwalteten Repositorys](#limitations-recommendations) gelten ebenfalls.
