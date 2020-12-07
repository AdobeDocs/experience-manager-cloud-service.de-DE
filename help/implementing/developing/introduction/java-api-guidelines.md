---
title: Java API-Richtlinien
description: AEM basiert auf einem umfangreichen Open-Source-Softwarestapel, der viele Java-APIs zur Verwendung bereitstellt.
translation-type: tm+mt
source-git-commit: b927992107d7e7e4df5511a366c71449ff73ec93
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 6%

---


# Java API-Richtlinien {#java-api-guidelines}

Adobe Experience Manager (AEM) basiert auf einem umfangreichen Open-Source-Softwarestapel, der viele Java-APIs zur Verwendung während der Entwicklung bereitstellt.

AEM basiert auf den folgenden vier primären Java-API-Sätzen in absteigender Reihenfolge der Voreinstellungen.

1. **Adobe Experience Manager (AEM)**  - Produktabstraktionen wie Seiten, Assets, Workflows usw.
1. **[Apache Sling Web Framework](https://sling.apache.org/apidocs/sling11/)**  - REST- und ressourcenbasierte Abstraktionen wie Ressourcen, Wertkarten und HTTP-Anforderungen.
1. **[JCR (Apache Jackrabbit Oak)](http://jackrabbit.apache.org/oak/docs/oak_api/overview.html)** - Daten- und Inhaltsabstraktionen wie Knoten, Eigenschaften und Sitzungen.
1. **[OSGi (Apache Felix)](https://felix.apache.org)** - OSGi-Anwendungsabstraktionen wie Dienste und OSGi-Container.

Wenn eine API von AEM bereitgestellt wird, bevorzugen Sie sie lieber als Sling, JCR und OSGi. Wenn AEM keine API bereitstellt, bevorzugen Sie Sling anstelle von JCR und OSGi.

Weitere Informationen zu diesen Richtlinien finden Sie im Dokument [Best Practices für Java API verstehen.](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/understand-java-api-best-practices.html)
