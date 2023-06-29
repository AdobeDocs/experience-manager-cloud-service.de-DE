---
title: Handelsintegration von AEM und Drittanbietern mithilfe des Commerce Integration Framework
description: Unternehmen benötigen möglicherweise zusätzliche Commerce-Lösungen von Drittanbietern, um ihre Storefront zu betreiben. Das Commerce Integration Framework (CIF) kann in solchen Integrationsszenarios verwendet werden, um mithilfe von I/O Runtime eine Commerce-Lösung von Drittanbietern mit Adobe Experience Manager zu verbinden.
thumbnail: cif-third-party-architecture.jpg
exl-id: 3ebdb8eb-65ba-46be-aca3-6c06c8d1600c
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 57%

---

# Handelsintegration von AEM und Drittanbietern mithilfe des Commerce Integration Framework {#aem-third-party}

Die Integration von Lösungen außerhalb von Adobe Commerce ist ein häufiges Szenario für CIF. Drittanbieterlösungen mit verschiedenen APIs und Schemas werden über eine Integrationsschicht verbunden.

## Architektur {#architecture}

Die Gesamtarchitektur sieht wie folgt aus:

![AEM Überblick über die Nicht-Magento-/Drittanbieter-Architektur](../assets//AEM_nonMagento_Architecture.png)

Der Zweck dieser Integrationsebene ist es, APIs und Schemas von Drittanbietern auf die unterstützten Adobe Commerce-GraphQL-APIs und -Schemas außerhalb von Experience Manager abzubilden. Dank dieser Kapselung können die Integrationslogik und die Systeme aktualisiert werden, ohne den Code im Experience Manager zu ändern.

## Lösungsanforderungen für eine Integration

Da Experience Manager Daten bei Bedarf abruft, sind für den Produktkatalog Echtzeit-APIs erforderlich.

>[!TIP]
>
>Wenn keine Echtzeit-APIs verfügbar sind, sollte für die Integration ein externer Produkt-Cache mit APIs verwendet werden. Beispiel [Adobe Commerce Open Source](https://business.adobe.com/de/products/magento/open-source.html).

Es ist nicht erforderlich, das vollständige GraphQL-Schema zu implementieren, sondern nur die Objekte des Schemas, um die gewünschten Anwendungsfälle zu ermöglichen.

## Backend-Anwendungsfälle

CIF erweitert Experience Manager mit Echtzeit-Produktkatalogzugriff und Tools für das Erlebnis-Management. Diese nahtlose Integration ermöglicht es Autoren, bei Bedarf über eingebettete Benutzeroberflächen auf Commerce-Daten zuzugreifen, ohne den Inhaltskontext verlassen zu müssen.

Die Integrationen von Produktkatalog-APIs sind erforderlich, um diese Anwendungsfälle zu entsperren.

## Frontend-Anwendungsfälle

[AEM CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) rufen Daten über die CIF-unterstützten Adobe Commerce-APIs ab und tauschen sie aus. Um Komponenten wiederzuverwenden, müssen die entsprechenden APIs implementiert sein.

Die Empfehlung für leistungskritische clientseitige Komponenten besteht darin, direkt mit der Drittanbieterlösung zu kommunizieren, um Latenzzeiten zu vermeiden.

## Entwickeln einer Integration {#develop-integration}

Adobe empfiehlt die Verwendung von [Adobe Developer Runtime](https://developer.adobe.com/runtime/) für die Integrationsschicht. Es ist im CIF-Add-on für Drittanbieter enthalten. Da sie mit einem Microservice-artigen Ansatz arbeitet, ist sie gut geeignet, einfach mehrere Lösungen zu integrieren.

Die [Referenzimplementierung](https://github.com/adobe/commerce-cif-graphql-integration-reference) ist ein guter Ausgangspunkt für die Erstellung der Integration in Ihre Commerce-Lösung. Sie unterstützt zwar GraphQL, kann aber auch mit jeder anderen Art von API wie REST integriert werden.

Diese Integrationsschicht ist nicht erforderlich, wenn eine Drittanbieterschicht verfügbar ist (z. B. Mulesoft) oder die Integration auf der Drittanbieterlösung aufbaut.

## Vorkonfigurierte Connectoren {#connectors}

Connectoren bieten einen guten Ausgangspunkt für Projekte. Sie enthalten eine Commerce-lösungsspezifische Verbindung und Standard-API-Zuordnung. Diese Connectoren werden von Dritten erstellt und nicht von Adobe gepflegt. Wenden Sie sich zur Information an den jeweiligen Partner.

* [SAP Commerce](https://github.com/diconium/commerce-cif-graphql-integration-hybris), erstellt von Diconium
* [Commercetools](https://github.com/diconium/commerce-cif-graphql-integration-commercetool), erstellt von Diconium

>[!TIP]
>
>Obwohl Connectoren in Projekten helfen, die Commerce-Integration zu beschleunigen, sind sie nicht Plug-and-Play. Enterprise Commerce-Lösungen sind stark angepasst und erfordern eine benutzerdefinierte Integration. Es sind gute Kenntnisse der Commerce-Plattform, der Adobe Commerce GraphQL-Schemata und von Adobe I/O Runtime erforderlich.
