---
title: Java-API-Richtlinien
description: AEM basiert auf umfassender Open-Source-Software-Technologie, über die zahlreiche Java-APIs zur Verwendung bereitgestellt werden.
exl-id: 0be33ec9-a4c3-4400-99d3-ed8366c5b5f9
source-git-commit: 856266faf4cb99056b1763383d611e9b2c3c13ea
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 97%

---

# Java-API-Richtlinien {#java-api-guidelines}

Adobe Experience Manager (AEM) basiert auf umfassender Open-Source-Software-Technologie, über die zahlreiche Java-APIs zur Verwendung während der Entwicklung bereitgestellt werden.

AEM basiert auf den folgenden vier primären Java-API-Sätzen in absteigender Reihenfolge der Bevorzugung.

1. **[Adobe Experience Manager (AEM)](https://experienceleague.adobe.com/docs/experience-manager-cloud-service-javadoc/index.html)** – Produktabstraktionen wie Seiten, Assets, Workflows usw.
1. **[Apache Sling-Web-Framework](https://sling.apache.org/apidocs/sling11/)** – REST- und ressourcenbasierte Abstraktionen wie Ressourcen, Wertzuordnungen und HTTP-Anfragen.
1. **[JCR (Apache Jackrabbit Oak)](http://jackrabbit.apache.org/oak/docs/oak_api/overview.html)** – Daten- und Inhaltsabstraktionen wie Knoten, Eigenschaften und Sitzungen.
1. **[OSGi (Apache Felix)](https://felix.apache.org)** – OSGi-Programm-Container-Abstraktionen wie Services und (OSGi-)Komponenten.

Wenn eine API von AEM bereitgestellt wird, sollten Sie sie Sling-, JCR- und OSGi-APIs vorziehen. Wenn AEM keine API bereitstellt, sollten Sie die Sling-API JCR- und OSGi-APIs vorziehen.

Weitere Informationen zu diesen Richtlinien finden Sie im Dokument [Grundlegendes zu den Best Practices für Java-APIs](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/understand-java-api-best-practices.html?lang=de).
