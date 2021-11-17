---
title: Integration von AEM und Adobe Commerce (Magento) mithilfe des Commerce Integration Framework
description: AEM und Adobe Commerce (Magento) werden über das Commerce Integration Framework (CIF) nahtlos integriert. CIF ermöglicht AEM Zugriff auf eine Magento-Instanz und die Kommunikation mit Magento über GraphQL. Darüber hinaus können AEM-Autoren Produkt- und Kategorieauswahlen sowie die Produktkonsole verwenden, um Produkt- und Kategoriedaten zu durchsuchen, die bei Bedarf aus Magento abgerufen werden. Darüber hinaus bietet CIF eine vordefinierte Storefront, die Geschäftsprojekte beschleunigen kann.
thumbnail: aem-magento-architecture.jpg
exl-id: 110ceef5-2c35-4b81-8e89-26929c0da91b,1cdfda88-a728-432f-b24a-f81347572bcf
source-git-commit: 52cfd60cde3165fde6b0167783c16b0fc1efc950
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 82%

---

# Integration von AEM und Adobe Commerce (Magento) mithilfe des Commerce Integration Framework {#aem-magento-framework}

Adobe Experience Manager und Adobe Commerce (Magento) werden über das Commerce Integration Framework (CIF) nahtlos integriert. CIF ermöglicht AEM direkten Zugriff auf und die direkte Kommunikation mit der Commerce-Instanz mithilfe der [GraphQL-APIs](https://devdocs.magento.com/guides/v2.4/graphql/) von Adobe Commerce.

>[!NOTE]
>
> Die Mindestversion der GraphQL-API wird 2.3.5 unterstützt. Bestimmte Funktionen werden nur in neueren Versionen oder nur in der Adobe Commerce-Version unterstützt.

>[!NOTE]
>
>GraphQL wird derzeit in zwei (separaten) Szenarios in Adobe Experience Manager (AEM) as a Cloud Service verwendet:
>
>* In diesem Szenario, in dem CIF über GraphQL mit Commerce kommuniziert.
>* [AEM-Inhaltsfragmente arbeiten mit der AEM-GraphQL-API (einer auf GraphQL basierenden benutzerdefinierten Implementierung) zusammen, um strukturierte Inhalte für die Verwendung in Ihren Programmen bereitzustellen](/help/assets/content-fragments/graphql-api-content-fragments.md).


## Architekturüberblick {#overview}

Die Gesamtarchitektur sieht wie folgt aus:

![CIF-Architekturübersicht](../assets/AEM_Magento_Architecture.png)

CIF unterstützt Server-seitige und Client-seitige Kommunikationsmuster.
Server-seitige APIs werden mithilfe des integrierten, generischen [GraphQL-Client](https://github.com/adobe/commerce-cif-graphql-client) in Kombination mit [Satz generierter Datenmodelle](https://github.com/adobe/commerce-cif-magento-graphql) für das Commerce-GraphQL-Schema Zusätzlich können alle GraphQL-Abfragen oder Mutationen im GQL-Format verwendet werden.

Für die clientseitigen Komponenten, die mit [React](https://reactjs.org/), die [Apollo Client](https://www.apollographql.com/docs/react/) verwendet.

## Architektur mit den AEM CIF-Kernkomponenten {#cif-core-components}

![Architektur mit den AEM CIF-Kernkomponenten](../assets/cif-component-architecture.jpg)

[AEM CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) folgen sehr ähnlichen Design-Mustern und Best Practices wie die [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components).

Die Geschäftslogik und Backend-Kommunikation mit Adobe Commerce für die AEM CIF-Kernkomponenten werden in Sling-Modellen implementiert. Falls es notwendig ist, diese Logik an projektspezifische Anforderungen anzupassen, kann das Delegationsmuster für Sling-Modelle verwendet werden.

>[!TIP]
>
>Die Seite [Anpassen von AEM CIF-Kernkomponenten](../customizing/customize-cif-components.md) enthält ein detailliertes Beispiel und Best Practices zur Anpassung von CIF-Kernkomponenten.

Innerhalb von Projekten können AEM CIF-Kernkomponenten und benutzerdefinierte Projektkomponenten den konfigurierten Client für einen mit einer AEM-Seite verknüpften Adobe Commerce-Store über eine Sling-kontextsensible Konfiguration abrufen.
