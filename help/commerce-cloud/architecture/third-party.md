---
title: AEM- und Drittanbieter-Commerce-Integration mithilfe von Commerce Integration Framework
description: Unternehmen benötigen möglicherweise zusätzliche kommerzielle Lösungen von Drittanbietern, um ihre Schaufenster zu bedienen. Das Commerce Integration Framework (CIF) kann in solchen Integrationsszenarien verwendet werden, um eine Commerce-Lösung eines Drittanbieters mit Adobe Experience Manager über die I/O-Laufzeit zu verbinden.
thumbnail: cif-third-party-architecture.jpg
translation-type: tm+mt
source-git-commit: 72d98c21a3c02b98bd2474843b36f499e8d75a03
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 1%

---


# AEM- und Drittanbieter-Commerce-Integration mithilfe von Commerce Integration Framework {#aem-third-party}

Unternehmen benötigen möglicherweise zusätzliche kommerzielle Lösungen von Drittanbietern, um ihre Schaufenster zu bedienen. Das Commerce Integration Framework (CIF) kann in solchen Integrationsszenarien verwendet werden, in denen neben Magento auch eine Commerce-Lösung von Drittanbietern in AEM integriert werden muss. CIF bietet Elemente wie einen Beschleuniger-Referenzspeicher, AEM CIF-Kernkomponenten und Authoring-Werkzeuge, die mit Magento sofort einsetzbar sind. Um AEM und eine kommerzielle Lösung von Drittanbietern zu integrieren und diese CIF-Elemente wiederzuverwenden, ist eine zusätzliche Entwicklung erforderlich.

## Architektur {#architecture}

Die Gesamtarchitektur ist wie folgt:

![Übersicht über AEM Architektur von Nicht-Magentos/Drittanbietern](/help/commerce-cloud/assets/AEM_nonMagento_Architecture.JPG)

Der Hauptunterschied zwischen der Integrationsarchitektur für AEM - Magento- und AEM - Drittanbieter-Commerce ist der Zusatz einer Integrations- und Datentransformationsebene, wie im Bild oben dargestellt. Die Integrationsebene muss auf der Adobe I/O Runtime-Plattform gehostet werden, die von der Adobe als serverlustfreie Plattform genutzt wird. Mehr über Adobe I/O Runtime erfahren Sie [hier](https://www.adobe.io/apis/experienceplatform/runtime.html).

Diese Integrationsebene dient der Zuordnung von APIs von Drittanbietern zu Adobe Commerce-APIs (Magento GraphQL APIs). Diese Zuordnung ermöglicht es den [AEM CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) und CIF-Authoring-Werkzeugen, Daten aus der Nicht-Magento-Lösung abzurufen. Bei diesem Ansatz enthält die Integrationsebene die Integrationslogik und schafft eine Trennung zwischen AEM und der Drittanbieterlösung. Dies ermöglicht die Verwendung der CIF-Elemente auf agnostische Weise mit verschiedenen Lösungen von Drittanbietern. Die Vorteile der Verwendung von CIF-Elementen in Ihrem Projekt wurden in der [Einführung](/help/commerce-cloud/overview.md)beschrieben.

## Entwickeln einer Integration {#develop-integration}

Um Ihnen beim Erstellen der erforderlichen Integrationsebene zu helfen, eine Nicht-Magento-/Drittanbieter-Lösung mit AEM zu integrieren, haben wir eine [Referenz-Implementierung](https://github.com/adobe/commerce-cif-graphql-integration-reference) erstellt, um dies zu demonstrieren. Diese Referenz kann als Ausgangspunkt in Ihrem Projekt verwendet werden.
