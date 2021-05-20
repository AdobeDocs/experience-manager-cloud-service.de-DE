---
title: Übermitteln eines AEM-Connectors
description: Übermitteln eines AEM-Connectors
exl-id: 9be1f00e-3666-411c-9001-c047e90b6ee5
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 100%

---

Übermitteln eines AEM-Connectors
===========================

Im Folgenden finden Sie nützliche Informationen zum Übermitteln von AEM-Connectoren. Lesen Sie diese zusammen mit den Artikeln zum [Implementieren](implement.md) und [Warten](maintain.md) von Connectoren.

AEM-Connectoren werden bei [Adobe Exchange](https://partners.adobe.com/exchangeprogram/experiencecloud) aufgeführt.

In vorherigen AEM-Lösungen wurde Package Manager verwendet, um Connectoren auf verschiedenen AEM-Instanzen zu installieren. Im Fall von AEM as a Cloud Service werden Connectoren jedoch während des CI/CD-Prozesses in Cloud Manager bereitgestellt. Damit die Connectoren bereitgestellt werden können, müssen sie in der Datei „pom.xml“ des Maven-Projekts referenziert werden.

Es gibt mehrere Möglichkeiten, wie die Pakete in ein Projekt eingebunden werden können:

1. Öffentliches Repository eines Partners: Ein Partner hostet das Inhaltspaket in einem öffentlich zugänglichen Maven-Repository.
1. Kennwortgeschütztes Repository eines Partners: Ein Partner hostet das Inhaltspaket in einem kennwortgeschützten Maven-Repository. Anweisungen finden Sie unter [Kennwortgeschützte Maven-Repositorys unter](/help/onboarding/getting-access-to-aem-in-cloud/setting-up-project.md#password-protected-maven-repositories).
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
