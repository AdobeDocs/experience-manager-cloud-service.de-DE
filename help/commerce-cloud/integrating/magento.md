---
title: Integration von AEM und Adobe Commerce (Magento) mithilfe des Commerce Integration Framework
description: AEM und Adobe Commerce (Magento) werden mithilfe des Commerce Integration Framework (CIF) nahtlos integriert. CIF ermöglicht AEM Zugriff auf eine Magento-Instanz und die Kommunikation mit Magento über GraphQL. Darüber hinaus können AEM-Autoren Produkt- und Kategorieauswahlen sowie die Produktkonsole verwenden, um Produkt- und Kategoriedaten zu durchsuchen, die bei Bedarf aus Magento abgerufen werden. Darüber hinaus bietet CIF eine vordefinierte Storefront, die Geschäftsprojekte beschleunigen kann.
thumbnail: aem-magento-architecture.jpg
exl-id: 110ceef5-2c35-4b81-8e89-26929c0da91b,1cdfda88-a728-432f-b24a-f81347572bcf
source-git-commit: ef4abc74b90da80bfe556306f8ac93078b4958c7
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 37%

---

# Integration von AEM und Adobe Commerce (Magento) mithilfe des Commerce Integration Framework {#aem-magento-framework}

Experience Manager und Adobe Commerce (Magento) werden mithilfe des Commerce Integration Framework (CIF) nahtlos integriert. CIF ermöglicht AEM direkten Zugriff auf und die direkte Kommunikation mit der Commerce-Instanz mithilfe der [GraphQL-APIs](https://devdocs.magento.com/guides/v2.4/graphql/) von Adobe Commerce.

>[!NOTE]
>
>GraphQL wird derzeit in zwei (separaten) Szenarien in Adobe Experience Manager (AEM) als Cloud Service verwendet:
>
>* Dieses Szenario, in dem CIF über GraphQL mit Commerce kommuniziert.
>* [AEM Inhaltsfragmente arbeiten mit der GraphQL-AEM-API (einer angepassten Implementierung, die auf GraphQL basiert) zusammen, um strukturierte Inhalte für die Verwendung in Ihren Anwendungen](/help/assets/content-fragments/graphql-api-content-fragments.md) bereitzustellen.


## Architekturüberblick {#overview}

Die Gesamtarchitektur sieht wie folgt aus:

![CIF-Architekturübersicht](../assets/AEM_Magento_Architecture.png)

CIF unterstützt Server-seitige und Client-seitige Kommunikationsmuster.

Server-seitige APIs werden mithilfe des integrierten, generischen [GraphQL-Clients](https://github.com/adobe/commerce-cif-graphql-client) in Kombination mit einem [Satz generierter Datenmodelle](https://github.com/adobe/commerce-cif-magento-graphql) für das Commerce-GraphQL-Schema implementiert. Darüber hinaus können alle GraphQL-Abfragen oder Mutationen im GQL-Format verwendet werden.

Bei Client-seitigen Komponenten, die mit [React](https://reactjs.org/) erstellt werden, kommt der [Apollo-Client](https://www.apollographql.com/docs/react/) zum Einsatz.

## Architektur mit den AEM CIF-Kernkomponenten {#cif-core-components}

![Architektur mit den AEM CIF-Kernkomponenten](../assets/cif-component-architecture.jpg)

[AEM CIF-Kernkomponenten ](https://github.com/adobe/aem-core-cif-components) folgen sehr ähnlichen Design-Mustern und Best Practices wie die  [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components).

Die Geschäftslogik und die Backend-Kommunikation mit Adobe Commerce für die AEM CIF-Kernkomponenten werden in Sling-Modelle implementiert. Falls es erforderlich ist, diese Logik anzupassen, um projektspezifische Anforderungen zu erfüllen, kann das Delegationsmuster für Sling-Modelle verwendet werden.

>[!TIP]
>
>Die Seite [Anpassen von AEM CIF-Kernkomponenten](../customizing/customize-cif-components.md) enthält ein detailliertes Beispiel und Best Practices zur Anpassung von CIF-Kernkomponenten.

Innerhalb von Projekten können AEM CIF-Kernkomponenten und benutzerdefinierte Projektkomponenten den konfigurierten Client für einen Adobe Commerce-Store, der mit einer AEM verknüpft ist, einfach über eine kontextabhängige Sling-Konfiguration abrufen.
