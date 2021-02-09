---
title: Handelsintegration von AEM und Drittanbietern mithilfe des Commerce Integration Framework
description: Unternehmen benötigen möglicherweise zusätzliche Drittanbieterlösungen für den Handel, um ihre Storefront zu betreiben. Das Commerce Integration Framework (CIF) kann in solchen Integrationsszenarien verwendet werden, um eine Drittanbieterlösungen für den Handel mit Adobe Experience Manager über I/O Runtime zu verbinden.
thumbnail: cif-third-party-architecture.jpg
translation-type: tm+mt
source-git-commit: 72d98c21a3c02b98bd2474843b36f499e8d75a03
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 100%

---


# Handelsintegration von AEM und Drittanbietern mithilfe des Commerce Integration Framework {#aem-third-party}

Unternehmen benötigen möglicherweise zusätzliche Drittanbieterlösungen für den Handel, um ihre Storefront zu betreiben. Das Commerce Integration Framework (CIF) kann in solchen Integrationsszenarien verwendet werden, in denen neben Magento auch eine Drittanbieterlösung für den Handel in AEM integriert werden muss. CIF bietet Elemente wie eine Beschleunigerreferenz-Storefront, AEM CIF-Kernkomponenten und Authoring-Tools, die für den Einsatz mit Magento vorkonfiguriert sind. Um AEM und eine Drittanbieterlösung für den Handel zu integrieren und diese CIF-Elemente wiederzuverwenden, ist eine zusätzliche Entwicklung erforderlich.

## Architektur {#architecture}

Die Gesamtarchitektur sieht wie folgt aus:

![Überblick über die AEM-Nicht-Magento-/-Drittanbieter-Struktur](/help/commerce-cloud/assets/AEM_nonMagento_Architecture.JPG)

Der Hauptunterschied zwischen der Integrationsarchitektur für AEM-Magento und AEM-Drittanbieterhandel besteht in der Hinzufügung einer Integrations- und Datenumwandlungsschicht, wie im obigen Bild gezeigt. Die Integrationsschicht muss auf der Adobe I/O Runtime-Plattform gehostet werden, bei der es sich um die Server-lose Plattform von Adobe handelt. Weitere Informationen zu Adobe I/O Runtime finden Sie [hier](https://www.adobe.io/apis/experienceplatform/runtime.html).

Diese Integrationsschicht dient der Zuordnung von Nicht-Magento- oder Drittanbieter-APIs zu Adobe Commerce-APIs (Magento GraphQL-APIs). Diese Zuordnung ermöglicht es den [AEM CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) und CIF-Authoring-Tools, Daten aus der Nicht-Magento-Lösung abzurufen. Bei diesem Ansatz enthält die Integrationsschicht die Integrationslogik und schafft eine Trennung zwischen AEM und der Drittanbieterlösung. Dies ermöglicht die unabhängige Verwendung der CIF-Elemente mit verschiedenen Drittanbieterlösungen. Die Vorteile der Verwendung von CIF-Elementen in Ihrem Projekt wurden in der [Einführung](/help/commerce-cloud/overview.md) beschrieben.

## Entwickeln einer Integration {#develop-integration}

Um Ihnen beim Erstellen der erforderlichen Integrationsschicht zu helfen, um eine Nicht-Magento-/Drittanbieterlösung mit AEM zu integrieren, haben wir zu Demonstrationszwecken eine [Referenzimplementierung](https://github.com/adobe/commerce-cif-graphql-integration-reference) erstellt. Diese Referenz kann als Ausgangspunkt in Ihrem Projekt verwendet werden.
