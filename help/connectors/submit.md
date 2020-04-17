---
title: Übermitteln eines AEM-Connectors
description: Übermitteln eines AEM-Connectors
translation-type: ht
source-git-commit: 629de3a9f55d2e4c52ef91c9e0bb5d439aebe84f

---


Übermitteln eines AEM-Connectors
===========================

Im Folgenden finden Sie nützliche Informationen zum Übermitteln von AEM-Connectoren. Lesen Sie diese zusammen mit den Artikeln zum [Implementieren](implement.md) und [Warten](maintain.md) von Connectoren.

AEM-Connectoren werden bei [Adobe Exchange](https://marketing.adobe.com/resources/content/resources/en/exchange/marketplace.html) aufgeführt.

In vorherigen AEM-Lösungen wurde Package Manager verwendet, um Connectoren auf verschiedenen AEM-Instanzen zu installieren. Im Fall von AEM as a Cloud Service werden Connectoren jedoch während des CI/CD-Prozesses in Cloud Manager bereitgestellt. Damit die Connectoren bereitgestellt werden können, müssen sie in der Datei „pom.xml“ des Maven-Projekts referenziert werden.

Es gibt mehrere Möglichkeiten, wie die Pakete in ein Projekt eingebunden werden können:

1. Öffentliches Repository eines Partners: Ein Partner hostet das Inhaltspaket in einem öffentlich zugänglichen Maven-Repository.
1. Gebündeltes Artefakt: In diesem Fall ist das Connector-Paket lokal im Maven-Projekt des Kunden enthalten.

Pakete müssen unabhängig davon, wo sie gehostet werden, als Abhängigkeiten in der Datei „pom.xml“ referenziert werden, wie vom Anbieter bereitgestellt.

```xml
<!-- UberJAR Dependency to be added to the project's Reactor pom.xml -->
<dependency>
  <groupId>com.partnername</groupId>
  <artifactId>my-artifact</artifactId>
  <version>V123</version> <!-- use the latest! -->
  <scope>provided</scope>
  <classifier>my_classifier</classifier>
</dependency>
```

Wenn der ISV-Partner den Connector auf einem über das Internet zugänglichen Maven-Repository hostet (beispielsweise Cloud Manager), sollte der ISV die Repository-Konfiguration bereitstellen, in der die Datei „pom.xml“ platziert werden kann, damit die (oben aufgeführten) Connector-Abhängigkeiten zur Build-Zeit (sowohl lokal als auch von Cloud Manager) aufgelöst werden können.

```xml
<repository>
    <id>the-repository</id>
    <name>The Repository Where the Connector is Hosted</name>
    <url>https://repo.partnername.com/repositories/aem_connector_repo</url>
    <releases>
        <enabled>true</enabled>
        <updatePolicy>never</updatePolicy>
    </releases>
    <snapshots>
        <enabled>false</enabled>
    </snapshots>
</repository>
```

Wenn der ISV-Partner den Connector als herunterladbare Dateien verteilt, sollte der ISV Anleitungen dazu bereitstellen, wie die Dateien in einem Maven-Repository des lokalen Dateisystems bereitgestellt werden können, das als Teil des AEM-Projekts in Git gespeichert werden muss, damit Cloud Manager diese Abhängigkeiten auflösen kann.
