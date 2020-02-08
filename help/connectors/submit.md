---
title: Senden eines AEM Connector
description: Senden eines AEM Connector
translation-type: tm+mt
source-git-commit: 629de3a9f55d2e4c52ef91c9e0bb5d439aebe84f

---


Senden eines AEM Connector
===========================

Im Folgenden finden Sie nützliche Informationen zum Übermitteln von AEM Connectors. Sie sollten zusammen mit Artikeln zur [Implementierung](implement.md) und [Wartung](maintain.md) von Connectors gelesen werden.

AEM Connectors werden auf [Adobe Exchange](https://marketing.adobe.com/resources/content/resources/en/exchange/marketplace.html)aufgeführt.

In früheren AEM-Lösungen wurde Package Manager verwendet, um Connectors auf verschiedenen AEM-Instanzen zu installieren. Bei AEM als Cloud-Dienst werden jedoch während des CI/CD-Prozesses in Cloud Manager Connectors bereitgestellt. Damit die Connectors bereitgestellt werden können, müssen Sie in der Datei &quot;pom.xml&quot;des Maven-Projekts auf Connectors verweisen.

Es gibt verschiedene Optionen, wie die Pakete in ein Projekt eingebunden werden können:

1. Öffentliches Repository des Partners - ein Partner würde das Inhaltspaket in einem öffentlich zugänglichen Repository hosten
1. Bündeltes Artefakt - in diesem Fall ist das Connector-Paket lokal im Maven-Projekt des Kunden enthalten.

Unabhängig davon, wo sie gehostet werden, müssen Pakete als Abhängigkeiten in der Datei pom.xml referenziert werden, wie vom Anbieter bereitgestellt.

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

Wenn der ISV-Partner den Connector auf einem Internet zugänglichen (z. B. mit Cloud Manager verfügbaren) Repository hostet, sollte das ISV die Repository-Konfiguration bereitstellen, in der die Datei &quot;pom.xml&quot;platziert werden kann, damit die Connector-Abhängigkeiten (oben) zur Buildzeit (sowohl lokal als auch von Cloud Manager) aufgelöst werden können.

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

Wenn der ISV-Partner sich dafür entscheidet, den Connector als herunterladbare Dateien zu verteilen, sollte der ISV Anweisungen darüber geben, wie die Dateien in einem lokalen Dateisystem-Maven-Repository bereitgestellt werden können, das als Teil des AEM-Projekts in Git überprüft werden muss, damit Cloud Manager diese Abhängigkeiten lösen kann.
