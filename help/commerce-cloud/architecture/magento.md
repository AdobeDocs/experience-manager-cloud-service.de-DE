---
title: AEM- und Magento-Integration mithilfe von Commerce Integration Framework
description: AEM- und Magento-Integration mithilfe von Commerce Integration Framework
translation-type: tm+mt
source-git-commit: 48805b21500ff3f2629efd6aecb40bb1cdc38cd6
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 1%

---


# AEM and Magento Integration using Commerce Integration Framework {#aem-magento-framework}

AEM und Magento werden mithilfe des Commerce Integration Framework (CIF) nahtlos integriert. CIF ermöglicht AEM Zugriff auf eine Magento-Instanz und die Kommunikation mit Magento über GraphQL. Darüber hinaus können AEM Author Produkt- und Kategorie-Picker und die Produktkonsole verwenden, um Produkt- und Kategorie-Daten zu durchsuchen, die bei Bedarf aus Magento abgerufen werden. Darüber hinaus bietet CIF eine vordefinierte Storefront, die Geschäftsprojekte beschleunigen kann.

## Architekturüberblick {#overview}

Die Gesamtarchitektur ist wie folgt:

![CIF-Architekturübersicht](../assets/AEM_Magento_Architecture.JPG)

CIF baut auf der GraphQL-Unterstützung auf. Der wichtigste Kanal für die Kommunikation zwischen AEM und Magento ist die [GraphQL API](https://devdocs.magento.com/guides/v2.4/graphql/) in Magento. Es gibt verschiedene Möglichkeiten, die Kommunikation zwischen AEM als Cloud Service und Magento zu konfigurieren. Weitere Informationen finden Sie auf der Seite [Erste Schritte](../getting-started.md) .

CIF unterstützt serverseitige und clientseitige Kommunikationsmuster.
Serverseitige APIs werden mithilfe des integrierten, generischen [GraphQL-Clients](https://github.com/adobe/commerce-cif-graphql-client) in Kombination mit einem [Satz generierter Datenmodelle](https://github.com/adobe/commerce-cif-magento-graphql) für das Magento GraphQL-Schema implementiert. Zusätzlich können alle GraphQL Abfragen oder Mutationen im GQL Format verwendet werden.

Bei clientseitigen Komponenten, die mit [React](https://reactjs.org/)erstellt werden, wird der [Apollo-Client](https://www.apollographql.com/docs/react/) verwendet.

## Architektur AEM CIF-Kernkomponenten {#cif-core-components}

![Architektur AEM CIF-Kernkomponenten](../assets/cif-component-architecture.jpg)

[AEM CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) folgen sehr ähnlichen Designmustern und Best Practices wie die [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components).

Die Geschäftslogik und die Backend-Kommunikation mit Magento für die AEM CIF-Kernkomponenten werden in Sling Modellen implementiert. Falls es notwendig ist, diese Logik an die projektspezifischen Anforderungen anzupassen, kann das Delegationsmuster für Sling-Modelle verwendet werden.

>[!TIP]
>
>Die Seite [Anpassen AEM CIF-Kernkomponenten](../customizing/customize-cif-components.md) enthält ein detailliertes Beispiel und eine Best Practice zur Anpassung der CIF-Kernkomponenten.

Innerhalb von Projekten können AEM CIF-Kernkomponenten und benutzerdefinierte Projektkomponenten den konfigurierten Client für einen mit einer AEM verknüpften Magento-Store über eine Sling Context-Aware-Konfiguration abrufen.
