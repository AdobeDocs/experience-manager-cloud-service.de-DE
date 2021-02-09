---
title: Java-API-Richtlinien
description: AEM basiert auf umfassender Open-Source-Software-Technologie, über die zahlreiche Java-APIs zur Verwendung bereitgestellt werden.
translation-type: tm+mt
source-git-commit: b927992107d7e7e4df5511a366c71449ff73ec93
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 100%

---


# Java-API-Richtlinien {#java-api-guidelines}

Adobe Experience Manager (AEM) basiert auf umfassender Open-Source-Software-Technologie, über die zahlreiche Java-APIs zur Verwendung während der Entwicklung bereitgestellt werden.

AEM basiert auf den folgenden vier primären Java-API-Sätzen in absteigender Reihenfolge der Bevorzugung.

1. **Adobe Experience Manager (AEM)** – Produktabstraktionen wie Seiten, Assets, Workflows usw.
1. **[Apache Sling-Web-Framework](https://sling.apache.org/apidocs/sling11/)** – REST- und ressourcenbasierte Abstraktionen wie Ressourcen, Wertzuordnungen und HTTP-Anfragen.
1. **[JCR (Apache Jackrabbit Oak)](http://jackrabbit.apache.org/oak/docs/oak_api/overview.html)** – Daten- und Inhaltsabstraktionen wie Knoten, Eigenschaften und Sitzungen.
1. **[OSGi (Apache Felix)](https://felix.apache.org)** – OSGi-Programm-Container-Abstraktionen wie Services und (OSGi-)Komponenten.

Wenn eine API von AEM bereitgestellt wird, sollten Sie sie Sling-, JCR- und OSGi-APIs vorziehen. Wenn AEM keine API bereitstellt, sollten Sie die Sling-API JCR- und OSGi-APIs vorziehen.

Weitere Informationen zu diesen Richtlinien finden Sie im Dokument [Grundlegendes zu den Best Practices für Java-APIs](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/understand-java-api-best-practices.html?lang=de).
