---
title: Einführung in AEM Commerce as a Cloud Service
description: Adobe Experience Manager Commerce as a Cloud Service besteht aus dem Commerce Integration Framework (CIF). Dabei handelt es sich um das von Adobe empfohlene Muster für die Integration und Erweiterung von Commerce-Services von Magento und Drittanbieter-Commerce-Lösungen mit Experience Cloud.
thumbnail: introducing-aem-commerce.jpg
translation-type: tm+mt
source-git-commit: 72d98c21a3c02b98bd2474843b36f499e8d75a03
workflow-type: tm+mt
source-wordcount: '1357'
ht-degree: 100%

---


# Einführung in AEM Commerce as a Cloud Service {#commerce-intro}

Adobe Experience Manager Commerce as a Cloud Service besteht aus dem Commerce Integration Framework (CIF). Dabei handelt es sich um das von Adobe empfohlene Muster für die Integration und Erweiterung von Commerce-Services von Magento und Drittanbieter-Commerce-Lösungen mit Experience Cloud. Dies ermöglicht es Adobe-Kunden, außergewöhnliche und personalisierte Omni-Channel-Shopping-Erlebnisse auf der Grundlage modernster Technologie bereitzustellen.

Das Commerce Integration Framework ist ein Add-on-Modul für Adobe Experience Manager as a Cloud Service und bietet eine Reihe von Authoring-Tools, Komponenten und eine Referenz-Storefront, um die Entwicklung von Integrationen zwischen Adobe Experience Manager as a Cloud Service und Commerce-Lösungen zu beschleunigen.

## Vorteile des CIF {#cif-benefits}

Die wichtigsten Vorteile:

* Die Integration ist eine Abstraktionsschicht zur Standardisierung und Kapselung von Integrationen mit mehreren Systemen.

* Das CIF unterstützt Headless-/Omni-Channel-Erlebnisse:

   * Single Page Applications und Multi Page Applications
   * GraphQL-Endpunkte

* Das CIF bietet Server-lose-, Microservice-basierte Prozess- und Geschäftslogikschicht zur Anpassung und Erweiterung von Commerce-Services.

* Das CIF bietet vordefinierte Integrationen mit Adobe-Lösungen wie AEM und Magento

## CIF-Elemente {#cif-elements}

![CIF-Elemente](/help/commerce-cloud/assets/cif-overview1.jpg)


### CIF-Add-on für Authoring-Tools {#add-on-authoring-tools}

Das CIF-Add-on bietet Autoren Zugriff auf Commerce-Authoring-Tools wie die Produktkonsole, den Produkt- und Kategorie-Wähler oder die Produktsuche, um vielfältige Erlebnisse mit Marketing- und Commerce-Inhalten zu erstellen. Das Add-on verwaltet auch die Backend-Verbindung mit Magento (oder einem alternativem Commerce-System) über GraphQL. Sobald das Add-on bereitgestellt wurde, wird es automatisch in AEM as a Cloud Service-Umgebungen implementiert.

### AEM-CIF-Kernkomponenten {#aem-cif-core}

Die AEM-CIF-Kernkomponenten sind Server- und Client-seitig gerenderte Komponenten mit Magento GraphQL-Unterstützung. Sie werden dazu verwendet, statische, zwischenspeicherbare und SEO-freundliche Commerce-Storefronts zu erstellen, die auf AEM-Technologien basieren.

Es werden grundlegende Komponenten bereitgestellt, die in Commerce-Implementierungen wie Produktdetails, Produktliste, Navigation und Suche verwendet werden. Sie können wie bereitgestellt verwendet oder erweitert werden.

Die [AEM-CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) funktionieren wie die [AEM Sites-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components), sind aber auf Commerce-spezifische Anwendungsfälle ausgelegt.

Diese Komponenten bieten folgende Vorteile:

* Sie lassen sich einfach in Ihren Projekten verwenden.
* Sie können wie bereitgestellt verwendet werden, bzw. erfordern nur geringfügige Änderungen.
* Sie bieten Best Practices für das Verbinden mit Magento über GraphQL-APIs oder REST-APIs.

Komponenten wie Produkt-Teaser und Produkt-Karussell werden bereitgestellt, damit AEM-Autoren Erlebnisseiten in AEM erstellen können, wobei Marketing- und Commerce-Inhalte kombiniert werden. Diese Komponenten können einfach per Drag-and-Drop auf eine Inhaltsseite gezogen werden, die in AEM erstellt wurde und mit bestimmten Produkten oder Kategorien verknüpft ist. Dazu verwenden Sie die CIF-Authoring-Tools wie den Produkt- oder Kategorie-Wähler in Cloud Service.

Alle Komponenten sind als Open-Source-Angebot über [GitHub](https://github.com/adobe/aem-core-cif-components) verfügbar. Damit profitieren Sie von umfassender Transparenz über künftige Änderungen und können einfach die neueste Version beziehen. Sie haben auch die Möglichkeit, Pull-Anfragen für Verbesserungen und Fehlerbehebungen bereitzustellen, die dort einfließen können.

### Venia-Storefront von AEM {#aem-venia-storefront}

Die [Venia-Storefront von AEM](https://github.com/adobe/aem-cif-guides-venia) ist eine moderne, produktionsbereite Referenz-Storefront mit einer einfachen B2C-Commerce-Journey. Sie kann verwendet werden, um Commerce-Projekte zu starten und Projekte mithilfe von AEM, CIF und Magento zu beschleunigen. Sie beinhaltet Best Practices für die Integration von AEM und Magento, zeigt, wie die [AEM-CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) und [AEM Sites-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) verwendet werden, und unterstützt Commerce-GraphQL-Endpunkte von Adobe. Mit einer Referenz-Website zielt sie außerdem auf Pre-Sales-Aspekte ab, um die Integration zwischen AEM und Magento zu demonstrieren.

Die Venia-Storefront von AEM ist eine Mixed Page Application, bei der AEM die Shop-Oberfläche bereitstellt und Magento per Headless-Implementierung das Commerce-Backend. In der Storefront werden sowohl das Server-seitige als auch das Client-seitige Rendering verwendet. Das Server-seitige Rendering wird für die Bereitstellung statischer Inhalte verwendet, das Client-seitige Rendering zur Bereitstellung dynamischer Inhalte.

Produkt- und Katalogseiten sind relativ statisch und werden Server-seitig mit AEM-CIF-Kernkomponenten wie Produktdetails und Produktliste über generischen Vorlagen dargestellt, die in AEM erstellt wurden. Diese Komponenten beziehen über GraphQL-APIs Daten aus Magento.
Diese Seiten werden dynamisch erstellt, auf dem Server gerendert, im Cache von AEM Dispatcher zwischengespeichert und dann an den Browser gesendet.
Für dynamischere Attribute wie „Bestand“ oder „Preis“ werden hingegen Client-seitige Komponenten verwendet. Client-seitige Komponenten oder Web-Komponenten rufen Daten über GraphQL-APIs direkt aus Magento ab und der Content wird dann im Browser gerendert.

#### Checkout {#checkout}

Diese Referenz-Storefront verwendet eine Client-seitige Warenkorbkomponente, mit der der Warenkorb und das Checkout-Formular gerendert werden. Dies ermöglicht es Ihnen, ein vollständiges Erlebnisintegrationsmuster zu demonstrieren, mit dem Sie mit Magento Commerce-Erlebnisse per Headless-Implementierung bereitstellen können, bei denen AEM die Shop-Oberfläche bereitstellt. Es empfiehlt sich, die bereitgestellten abstrahierten Zahlungsmethoden zu verwenden. Dadurch kommuniziert der Browser-Client direkt mit dem Payment Gateway Provider, sodass weder Adobe noch Magento-Clouds PCI-sensible Daten speichern oder weitergeben.

#### Account-Management {#account-management}

Das Account-Management wird von Magento verwaltet und die Referenz-Storefront nutzt Client-seitige, React-basierte Komponenten, sodass AEM Erlebnisse für die folgenden Funktionen rendern kann: „Konto erstellen“, „Anmelden“ und „Kennwort vergessen“.

Die Venia-Storefront-Projekt von AEM ist ein Open-Source-Projekt. Weitere Informationen finden Sie unter [Venia-Storefront von AEM](https://github.com/adobe/aem-cif-guides-venia).

### AEM-Projektarchetyp {#aem-project-archtype}

Mit dem [AEM-Projektarchetyp](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/developing/archetype/overview.html) lässt sich ein Adobe Experience Manager-Projekt mit minimalen Best Practices als Ausgangspunkt für Ihre eigenen AEM-Projekte erstellen. Optional können [AEM-CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) in neu erstellte Projekte eingebunden werden.

### CIF-Erweiterungsschicht {#cif-extension}

Die CIF-Erweiterungsschicht ist eine mittlere Schicht für das Hosten komplexer Geschäftslogik. Sie wird auf der Adobe I/O Runtime-Plattform ausgeführt, der Server-losen Plattform von Adobe. Sie ermöglicht es Ihnen, End-to-End-Service-Aufrufe zu erweitern, indem Sie Geschäfts- und Prozesslogik auf einer Microservice-Ebene einfügen. Geschäftslogik wäre beispielsweise die Verwendung von Standort und Kanal zur Festlegung einer Bestandsstrategie. Prozesslogik wäre das Abrufen personalisierter Informationen.

### CIF-Integrationsschicht {#cif-integration-layer}

Die CIF-Integrationsschicht dient zur Standardisierung von Integrationen mit anderen Commerce-Lösungen. Sie wird auf der Adobe I/O Runtime-Plattform ausgeführt, der Server-losen Plattform von Adobe, und ermöglicht Integrationen auf Microservice-Ebene, indem sie Drittanbieter-APIs den Commerce-APIs von Adobe zuordnet. Um Ihnen den Einstieg in die Entwicklung von Drittanbieter-Integrationen mit AEM zu erleichtern, haben wir eine [Referenz-Implementierung](https://github.com/adobe/commerce-cif-graphql-integration-reference) erstellt. Diese veranschaulicht, wie ein Commerce-Backend, das nicht von Magento stammt, über Commerce-APIs von Adobe (Magento GraphQL-APIs) integriert werden kann.

## AEM Commerce-Integrationsmuster {#aem-commerce-integration}

Im Folgenden sind einige der häufig implementierten AEM Commerce-Integrationsmuster dargestellt.

![AEM CIF-Integrationsmuster](/help/commerce-cloud/assets/aem-cif-integration-patterns-updated.JPG)


### Integrationsmuster 1 {#integration-pattern-one}

Dies ist unser empfohlenes Integrationsmuster, bei dem AEM die gesamte Shop-Oberfläche bereitstellt und über Commerce-GraphQL-APIs von Adobe Commerce-Services integriert. Mit diesem Muster wird die ganze Flexibilität von AEM freigesetzt, um Rich-Media-Site-Designs geräteübergreifend anzupassen. Dieses Integrationsmuster wird vom CIF als vordefinierte Lösung unterstützt.


### Integrationsmuster 2 {#integration-pattern-two}

Dieses Muster zeigt die Bereitstellung von Content und Commerce-Services, die gänzlich per Headless-Implementierung erfolgt. Die Bereitstellung erfolgt vollständig Client-seitig. Bei diesem Muster werden Inhalte über APIs und HTML- und Commerce-Daten über GraphQL bereitgestellt. Dieses Muster wird derzeit nicht standardmäßig vom CIF unterstützt.


### Integrationsmuster 3 {#integration-pattern-three}

Bei diesem Muster stellt Magento die Shop-Oberfläche bereit und bettet den in AEM erstellten Content ein. Der in AEM erstellte Content kann über Experience Fragments oder Inhaltsfragmente bereitgestellt werden. Dieses Integrationsmuster erfordert eine projektspezifische Bearbeitung und kann nicht standardmäßig mit dem CIF implementiert werden.


### Integrationsmuster 4 {#integration-pattern-four}

Dies ist ein gängiges Integrationsmuster, bei dem die Oberflächen- oder Präsentationsschicht zwischen AEM und einer Commerce-Lösung aufgeteilt wird. Normalerweise stellt die Commerce-Lösung die nicht auf Marketing bezogenen Seiten wie „Checkout“ und „Mein Konto“ bereit. AEM stellt die Marketing-Seiten und Storefront-Katalogerlebnisse bereit. Bei diesem Muster müssen Sie sicherstellen, dass Warenkorb- und Anwender-Sessions zwischen den beiden Systemen ordnungsgemäß verarbeitet werden, um unzusammenhängende Anwendererlebnisse zu vermeiden. Beispielsweise speichert Magento die Warenkorb- und Anwender-Sessions in einem Cookie, das von AEM und Magento gemeinsam genutzt werden kann. Dieses Muster erfordert eine projektspezifische Bearbeitung und kann nicht standardmäßig mit dem CIF implementiert werden.
