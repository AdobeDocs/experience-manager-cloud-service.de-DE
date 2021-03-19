---
title: Integration von AEM und Magento mithilfe des Commerce Integration Framework
description: AEM und Magento werden über das Commerce Integration Framework (CIF) nahtlos integriert. CIF ermöglicht AEM Zugriff auf eine Magento-Instanz und die Kommunikation mit Magento über GraphQL. Darüber hinaus können AEM-Autoren Produkt- und Kategorieauswahlen sowie die Produktkonsole verwenden, um Produkt- und Kategoriedaten zu durchsuchen, die bei Bedarf aus Magento abgerufen werden. Darüber hinaus bietet CIF eine vordefinierte Storefront, die Geschäftsprojekte beschleunigen kann.
thumbnail: aem-magento-architecture.jpg
translation-type: tm+mt
source-git-commit: 0f2b7176b44bb79bdcd1cecf6debf05bd652a1a1
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 88%

---


# Integration von AEM und Magento mithilfe des Commerce Integration Framework {#aem-magento-framework}

AEM und Magento werden über das Commerce Integration Framework (CIF) nahtlos integriert. CIF ermöglicht AEM Zugriff auf eine Magento-Instanz und die Kommunikation mit Magento über GraphQL. Darüber hinaus können AEM-Autoren Produkt- und Kategorieauswahlen sowie die Produktkonsole verwenden, um Produkt- und Kategoriedaten zu durchsuchen, die bei Bedarf aus Magento abgerufen werden. Darüber hinaus bietet CIF eine vordefinierte Storefront, die Geschäftsprojekte beschleunigen kann.

>[!NOTE]
>
>GraphQL wird derzeit in zwei (separaten) Szenarien in Adobe Experience Manager (AEM) als Cloud Service verwendet:
>
>* AEM Commerce nutzt Daten von einer Commerce-Plattform über GraphQL.
>* [AEM Inhaltsfragmente arbeiten mit der AEM GraphQL API (einer auf GraphQL basierenden benutzerdefinierten Implementierung) zusammen, um strukturierte Inhalte für die Verwendung in Ihren Anwendungen](/help/assets/content-fragments/graphql-api-content-fragments.md) bereitzustellen.


## Architekturüberblick {#overview}

Die Gesamtarchitektur sieht wie folgt aus:

![CIF-Architekturübersicht](../assets/AEM_Magento_Architecture.JPG)

CIF baut auf GraphQL-Unterstützung auf. Der wichtigste Kommunikationskanal zwischen AEM und Magento ist die [GraphQL-API](https://devdocs.magento.com/guides/v2.4/graphql/) von Magento. Es gibt verschiedene Möglichkeiten, die Kommunikation zwischen AEM as a Cloud Service und Magento zu konfigurieren. Weitere Informationen finden Sie auf der Seite [Erste Schritte](../getting-started.md).

CIF unterstützt Server-seitige und Client-seitige Kommunikationsmuster.

Server-seitige APIs werden mithilfe des integrierten, generischen [GraphQL-Clients](https://github.com/adobe/commerce-cif-graphql-client) in Kombination mit einem [Satz generierter Datenmodelle](https://github.com/adobe/commerce-cif-magento-graphql) für das Magento GraphQL-Schema implementiert. Zusätzlich können alle GraphQL-Abfragen oder Mutationen im GQL-Format verwendet werden.

Bei Client-seitigen Komponenten, die mit [React](https://reactjs.org/) erstellt werden, kommt der [Apollo-Client](https://www.apollographql.com/docs/react/) zum Einsatz.

## Architektur mit den AEM CIF-Kernkomponenten {#cif-core-components}

![Architektur mit den AEM CIF-Kernkomponenten](../assets/cif-component-architecture.jpg)

[AEM CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) folgen sehr ähnlichen Design-Mustern und Best Practices wie die [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components).

Die Geschäftslogik und Backend-Kommunikation mit Magento für die AEM CIF-Kernkomponenten werden in Sling-Modellen implementiert. Falls es notwendig ist, diese Logik an projektspezifische Anforderungen anzupassen, kann das Delegationsmuster für Sling-Modelle verwendet werden.

>[!TIP]
>
>Die Seite [Anpassen von AEM CIF-Kernkomponenten](../customizing/customize-cif-components.md) enthält ein detailliertes Beispiel und Best Practices zur Anpassung von CIF-Kernkomponenten.

Innerhalb von Projekten können AEM CIF-Kernkomponenten und benutzerdefinierte Projektkomponenten den konfigurierten Client für einen mit einer AEM-Seite verknüpften Magento-Store über eine Sling-kontextsensible Konfiguration abrufen.
