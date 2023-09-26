---
title: Übermitteln eines AEM-Connectors
description: Erfahren Sie, wie Sie Connectoren in Adobe Experience Manager (AEM) as a Cloud Service richtig referenzieren und bereitstellen.
exl-id: 9be1f00e-3666-411c-9001-c047e90b6ee5
source-git-commit: 78ead5f15c2613d9c3bed3025b43423a66805c59
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 30%

---

# Übermitteln eines AEM-Connectors

Im Folgenden finden Sie nützliche Informationen zum Übermitteln von Adobe Experience Manager (AEM) Connectoren. Lesen Sie Artikel zu [Umsetzung](implement.md) und  [keep](maintain.md) Connectoren.

AEM-Connectoren werden bei [Adobe Exchange](https://partners.adobe.com/technologyprogram/experiencecloud.html) aufgeführt.

In vorherigen AEM-Lösungen wurde [Package Manager](/help/implementing/developing/tools/package-manager.md) verwendet, um Connectoren auf verschiedenen AEM-Instanzen zu installieren. Im Fall von AEM as a Cloud Service werden Connectoren jedoch während des CI/CD-Prozesses in Cloud Manager bereitgestellt. Damit die Connectoren bereitgestellt werden können, müssen sie in der Datei &quot;pom.xml&quot;des Maven-Projekts referenziert werden.

Es gibt mehrere Möglichkeiten, wie die Pakete in ein Projekt eingebunden werden können:

1. Öffentliches Repository eines Partners: Ein Partner hostet das Inhaltspaket in einem öffentlich zugänglichen Maven-Repository.
1. Kennwortgeschütztes Repository des Partners: Ein Partner hostet das Inhaltspaket in einem kennwortgeschützten Maven-Repository. Siehe [kennwortgeschützte Maven-Repositorys](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/create-application-project/setting-up-project.html?lang=en#password-protected-maven-repositories) für Anweisungen.
1. Gebündeltes Artefakt: In diesem Fall ist das Connector-Paket lokal im Maven-Projekt des Kunden enthalten.

Pakete müssen unabhängig davon, wo sie gehostet werden, als Abhängigkeiten in der pom.xml referenziert werden, wie vom Anbieter bereitgestellt.

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

Wenn der ISV-Partner den Connector in einem über das Internet zugänglichen Maven-Repository hostet (z. B. Cloud Manager-Zugriff), sollte der ISV die Repository-Konfiguration bereitstellen, in der der `pom.xml` kann platziert werden. Der Grund dafür ist, dass die (oben) Connector-Abhängigkeiten zur Build-Zeit sowohl lokal als auch von Cloud Manager aufgelöst werden können.

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

Wenn der ISV-Partner den Connector als herunterladbare Dateien verteilt, sollte der ISV Anweisungen geben. In der Anweisung sollte beschrieben werden, wie die Dateien in einem Maven-Repository des lokalen Dateisystems bereitgestellt werden können, das im Rahmen des AEM-Projekts in Git geprüft werden muss. Dadurch wird sichergestellt, dass Cloud Manager diese Abhängigkeiten auflösen kann.
