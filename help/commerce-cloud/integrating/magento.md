---
title: AEM- und Adobe Commerce-Integration mithilfe des Commerce Integration Framework
description: AEM und Adobe Commerce werden mithilfe des Commerce Integration Framework (CIF) nahtlos integriert. CIF ermöglicht AEM den Zugriff auf eine Adobe Commerce-Instanz und die Kommunikation mit Adobe Commerce über GraphQL. Außerdem können AEM-Autoren Produkt- und Kategorieauswahlen sowie die Produktkonsole verwenden, um Produkt- und Kategoriedaten zu durchsuchen, die bei Bedarf aus Adobe Commerce abgerufen werden. Darüber hinaus bietet CIF eine vordefinierte Storefront, die Geschäftsprojekte beschleunigen kann.
thumbnail: aem-magento-architecture.jpg
exl-id: 110ceef5-2c35-4b81-8e89-26929c0da91b,1cdfda88-a728-432f-b24a-f81347572bcf
source-git-commit: 05a412519a2d2d0cba0a36c658b8fed95e59a0f7
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 62%

---

# Integration von AEM und Adobe Commerce mithilfe des Commerce Integration Framework {#aem-framework}

Der Experience Manager und Adobe Commerce werden mithilfe des Commerce Integration Framework (CIF) nahtlos integriert. CIF ermöglicht AEM direkten Zugriff auf die Commerce-Instanz und deren direkte Kommunikation mit der Commerce-Instanz mithilfe von Adobe Commerce [GraphQL-APIs](https://devdocs.magento.com/guides/v2.4/graphql/).

>[!NOTE]
>
> Zur Unterstützung der GraphQL-API ist mindestens die Version 2.3.5 erforderlich. Bestimmte Funktionen werden nur von neueren Versionen oder nur von der Adobe Commerce-Edition unterstützt.

>[!NOTE]
>
>GraphQL wird derzeit in zwei (separaten) Szenarios in Adobe Experience Manager (AEM) as a Cloud Service verwendet:
>
>* In diesem Szenario, in dem CIF über GraphQL mit Commerce kommuniziert.
>* [AEM-Inhaltsfragmente arbeiten mit der AEM-GraphQL-API (einer auf GraphQL basierenden benutzerdefinierten Implementierung) zusammen, um strukturierte Inhalte für die Verwendung in Ihren Programmen bereitzustellen](/help/assets/content-fragments/graphql-api-content-fragments.md).


## Architekturüberblick {#overview}

Die Gesamtarchitektur sieht wie folgt aus:

![CIF-Architekturübersicht](../assets/AEM_Magento_Architecture.png)

In CIF werden serverseitige und Client-seitige Kommunikationsmuster unterstützt.
Server-seitige APIs werden mithilfe des integrierten, generischen [GraphQL-Client](https://github.com/adobe/commerce-cif-graphql-client) in Kombination mit [Satz generierter Datenmodelle](https://github.com/adobe/commerce-cif-magento-graphql) für das Commerce-GraphQL-Schema. Zusätzlich können alle GraphQL-Abfragen oder Mutationen im GQL-Format verwendet werden.

Für die clientseitigen Komponenten, die mit [React](https://reactjs.org/), die [Apollo Client](https://www.apollographql.com/docs/react/) verwendet.

## Architektur mit den AEM CIF-Kernkomponenten {#cif-core-components}

![Architektur mit den AEM CIF-Kernkomponenten](../assets/cif-component-architecture.jpg)

[AEM CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) folgen sehr ähnlichen Design-Mustern und Best Practices wie die [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components).

Die Geschäftslogik und Backend-Kommunikation mit Adobe Commerce für die AEM CIF-Kernkomponenten werden in Sling-Modellen implementiert. Falls es notwendig ist, diese Logik an projektspezifische Anforderungen anzupassen, kann das Delegationsmuster für Sling-Modelle verwendet werden.

>[!TIP]
>
>Die Seite [Anpassen von AEM CIF-Kernkomponenten](../customizing/customize-cif-components.md) enthält ein detailliertes Beispiel und Best Practices zur Anpassung von CIF-Kernkomponenten.

Innerhalb von Projekten können AEM CIF-Kernkomponenten und benutzerdefinierte Projektkomponenten den konfigurierten Client für einen mit einer AEM-Seite verknüpften Adobe Commerce-Store über eine Sling-kontextsensible Konfiguration abrufen.
