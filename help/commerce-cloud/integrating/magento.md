---
title: Integration von AEM und Adobe Commerce (Magento) mithilfe von Commerce Integration Framework
description: AEM und Adobe Commerce (Magento) werden mithilfe des Commerce Integration Framework (CIF) nahtlos integriert. CIF ermöglicht AEM Zugriff auf eine Magento-Instanz und die Kommunikation mit Magento über GraphQL. Darüber hinaus können AEM-Autoren Produkt- und Kategorieauswahlen sowie die Produktkonsole verwenden, um Produkt- und Kategoriedaten zu durchsuchen, die bei Bedarf aus Magento abgerufen werden. Darüber hinaus bietet CIF eine vordefinierte Storefront, die Geschäftsprojekte beschleunigen kann.
thumbnail: aem-magento-architecture.jpg
exl-id: 1cdfda88-a728-432f-b24a-f81347572bcf
translation-type: tm+mt
source-git-commit: a4e53fdcb33eab8afabcb13d651155cd247bda1f
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 37%

---

# Integration von AEM und Adobe Commerce (Magento) mithilfe von Commerce Integration Framework {#aem-magento-framework}

Die Integration von Experience Manager und Adobe Commerce (Magento) erfolgt nahtlos über das Commerce Integration Framework (CIF). CIF ermöglicht AEM direkten Zugriff auf die komprimierte Instanz und die direkte Kommunikation mit dieser. Dazu verwenden Sie die [GraphQL-APIs](https://devdocs.magento.com/guides/v2.4/graphql/) von Adobe Commerce.

>[!NOTE]
>
>GraphQL wird derzeit in zwei (separaten) Szenarien in Adobe Experience Manager (AEM) als Cloud Service verwendet:
>
>* Dieses Szenario, bei dem CIF mit dem Handel über GraphQL kommuniziert.
>* [AEM Inhaltsfragmente arbeiten mit der AEM GraphQL API (einer auf GraphQL basierenden benutzerdefinierten Implementierung) zusammen, um strukturierte Inhalte für die Verwendung in Ihren Anwendungen](/help/assets/content-fragments/graphql-api-content-fragments.md) bereitzustellen.


## Architekturüberblick {#overview}

Die Gesamtarchitektur sieht wie folgt aus:

![CIF-Architekturübersicht](../assets/AEM_Magento_Architecture.png)

CIF unterstützt Server-seitige und Client-seitige Kommunikationsmuster.

Serverseitige APIs werden mit dem integrierten, generischen [GraphQL-Client](https://github.com/adobe/commerce-cif-graphql-client) in Kombination mit einem [Satz generierter Datenmodelle](https://github.com/adobe/commerce-cif-magento-graphql) für das kommerzielle GraphQL-Schema implementiert. Zusätzlich können alle GraphQL-Abfragen oder Mutationen im GQL-Format verwendet werden.

Bei Client-seitigen Komponenten, die mit [React](https://reactjs.org/) erstellt werden, kommt der [Apollo-Client](https://www.apollographql.com/docs/react/) zum Einsatz.

## Architektur mit den AEM CIF-Kernkomponenten {#cif-core-components}

![Architektur mit den AEM CIF-Kernkomponenten](../assets/cif-component-architecture.jpg)

[AEM CIF-Core-](https://github.com/adobe/aem-core-cif-components) Komponenten folgen sehr ähnlichen Designmustern und Best Practices wie die  [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components).

Die Business-Logik und Backend-Kommunikation mit Adobe Commerce für die AEM CIF Core Components ist in Sling Modellen implementiert. Falls es notwendig ist, diese Logik an die projektspezifischen Anforderungen anzupassen, kann das Delegationsmuster für Sling-Modelle verwendet werden.

>[!TIP]
>
>Die Seite [Anpassen von AEM CIF-Kernkomponenten](../customizing/customize-cif-components.md) enthält ein detailliertes Beispiel und Best Practices zur Anpassung von CIF-Kernkomponenten.

Innerhalb von Projekten können AEM CIF-Kernkomponenten und benutzerdefinierte Projektkomponenten den konfigurierten Client für einen mit einer AEM verknüpften Adobe Commerce Store über eine Sling Context-Aware-Konfiguration abrufen.
