---
title: Einführung in AEM Handel als Cloud Service
description: Neue Funktionen in AEM Commerce als Cloud Service.
translation-type: tm+mt
source-git-commit: c5694cf8651cf8ba5331c730fa1b1180310dd35a
workflow-type: tm+mt
source-wordcount: '1331'
ht-degree: 1%

---


# Introducing AEM Commerce as a Cloud Service {#commerce-intro}

Experience Manager Commerce als Cloud Service besteht aus Commerce Integration Framework (CIF), das von der Adobe empfohlen wird, Commerce-Dienstleistungen von Magento und anderen Drittanbieter-Commerce-Lösungen mit dem Experience Cloud zu integrieren und zu erweitern. Dies ermöglicht es Adobe Kunden, außergewöhnliche und personalisierte Omniannel-Shopping-Erlebnisse auf der Grundlage modernster Technologie zu liefern.

Das Commerce Integration Framework ist ein Add-On-Modul für Experience Manager als Cloud Service und bietet eine Reihe von Authoring-Werkzeugen, Komponenten und einen Referenz Store, um die Entwicklung von Integrationen zwischen Experience Manager als Cloud Service- und Commerce-Lösungen zu beschleunigen.

## CIF-Vorteile {#cif-benefits}

Die wichtigsten Vorteile sind:

* Die Integration ist eine Abstraktionsebene zur Standardisierung und Kapselung von Integrationen mit mehreren Systemen.

* CIF unterstützt kopflose/omnichannel-Erlebnisse:

   * Einzelseitenanwendungen und mehrseitige Anwendungen
   * GraphQL-Endpunkte

* CIF bietet serverless-, mikroservice-basierte Prozess- und Business-Logikschicht zur Anpassung und Erweiterung von Commerce-Dienstleistungen.

* CIF bietet vordefinierte Integrationen mit Adobe-Lösungen wie AEM und Magento

## CIF-Elemente {#cif-elements}

![CIF-Elemente](/help/commerce-cloud/assets/cif-overview1.jpg)


### CIF-Add-On für Authoring-Werkzeuge {#add-on-authoring-tools}

Das CIF-Add-On bietet Zugriff auf kommerzielle Authoring-Werkzeuge wie Produktkonsole, Produkt- und Produktauswahl oder Produktsuche für Autoren, um sie in die Lage zu versetzen, umfangreiche Erlebnisse mit Marketing- und Commerce-Inhalten zu erstellen. Das Add-on verwaltet auch die Backend-Verbindung mit Magento (oder alternativem Commerce-System) über GraphQL. Sobald das Add-on bereitgestellt wurde, wird es automatisch auf AEM Umgebung als Cloud Service bereitgestellt.

### AEM CIF-Kernkomponenten {#aem-cif-core}

Die AEM CIF-Core-Komponenten sind serverseitige und clientseitige gerenderte Komponenten mit Magento GraphQL-Unterstützung. Sie werden dazu verwendet, statische, speicherbare und SEO-freundliche Commerce-Stores zu erstellen, die auf AEM Technologien basieren.

Grundlegende Komponenten werden bereitgestellt, die in Commerce-Implementierungen wie Produktdetails, Produktnavigation, Liste usw. verwendet werden. Sie können unverändert verwendet oder erweitert werden.

Die [AEM CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) funktionieren wie die [AEM Sites Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) , sind aber auf kommerzielle Anwendungsfälle spezialisiert.

Die folgenden Komponenten bieten folgende Hauptvorteile:

* Sie sind einfach in Ihren Projekten zu verwenden.
* Sie können wie vorhanden oder mit sehr minimalen Änderungen verwendet werden.
* Sie bieten Best Practices für die Verbindung mit Magento über GraphQL-APIs oder REST-APIs.

Komponenten wie Product Teaser und Product Carousel werden bereitgestellt, damit AEM Author Erlebnisseiten in AEM erstellen können, indem Marketing- und Commerce-Inhalte kombiniert werden. Diese Komponenten können einfach per Drag &amp; Drop auf eine Inhaltsseite gezogen werden, die in AEM erstellt wurde und mit bestimmten Produkten oder Kategorien verknüpft ist. Dazu verwenden Sie die CIF-Authoring-Werkzeuge wie die Produkt- oder Kategorie-Auswahl in Cloud Service.

Alle Komponenten sind Open-Source auf [GitHub](https://github.com/adobe/aem-core-cif-components). Dies zeigt volle Transparenz über die in Zukunft vorgenommenen Änderungen und ermöglicht Ihnen, die neueste Version sehr einfach zu bekommen. Sie können auch Pull-Anforderungen für Verbesserungen und Fehlerbehebungen bereitstellen, die integriert werden können.

### AEM Venedig-Storefront {#aem-venia-storefront}

Die [AEM Venia Storefront](https://github.com/adobe/aem-cif-guides-venia) ist ein moderner, produktionsfertiger Referenzspeicher, der eine einfache B2C-Geschäftsreise zeigt. Es kann verwendet werden, um kommerzielle Projekte zu starten und Projekte mithilfe von AEM, CIF und Magento zu beschleunigen. Es zeigt Best Practices für die Integration von AEM und Magento und zeigt, wie die [AEM CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) und - [AEM Sites Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) verwendet werden und unterstützt Adobe Commerce GraphQL-Endpunkte. Es bietet auch eine Pre-Sales-Website mit einer Referenz-Website, um die Integration zwischen AEM und Magento zu demonstrieren.

Die AEM Venia Storefront ist eine gemischte Anwendung, bei der AEM das Glas besitzt und das Magento das Commerce-Backend auf eine kopflose Weise beherrscht. Sowohl das serverseitige Rendering als auch das clientseitige Rendering werden im Store verwendet. Das serverseitige Rendering wird verwendet, um statischen Inhalt bereitzustellen, und das clientseitige Rendering wird zur Bereitstellung dynamischer Inhalte verwendet.

Produkt- und Katalogseiten sind relativ statisch und werden serverseitig mit AEM CIF-Kernkomponenten wie Produktdetails und Produktdokumentation auf generischen Vorlagen dargestellt, die in AEM erstellt wurden. Diese Komponenten erhalten Daten von Magento über GraphQL APIs.
Diese Seiten werden dynamisch erstellt, auf dem Server wiedergegeben, im Cache des AEM Dispatchers zwischengespeichert und dann an den Browser gesendet.
Für dynamischere Attribute wie Bestand oder Preis werden hingegen clientseitige Komponenten verwendet. Clientseitige Komponenten oder Webkomponenten rufen Daten direkt aus dem Magento über GraphQL-APIs ab, und der Inhalt wird dann im Browser wiedergegeben.

#### Auschecken {#checkout}

Dieser Referenzspeicher verwendet eine clientseitige Warenkorbkomponente, mit der der Warenkorb und das Kassengangsformular gerendert werden, um ein vollständiges Erlebnisintegrationsmuster zu demonstrieren, mit dem Sie Geschäftserlebnisse mit Magento bereitstellen können, das völlig kopfüber läuft und AEM das Glas besitzt. Es wird empfohlen, die bereitgestellten abstrakten Zahlungsmethoden zu verwenden. Dadurch wird der Browser-Client direkt mit dem Payment Gateway Provider kommuniziert, sodass weder Adobe noch Magento-Clouds PCI-sensible Daten speichern oder weitergeben.

#### Kontoverwaltung {#account-management}

Die Kontoverwaltung wird von Magento verwaltet, und der Referenz Store nutzt clientseitige react-basierte Komponenten, um AEM Erlebnis für die folgenden Funktionen wiederzugeben: Konto erstellen, Anmelden und Kennwort vergessen.

Das Projekt AEM Venia Storefront ist Open Source und für weitere Details siehe [AEM Venia Storefront](https://github.com/adobe/aem-cif-guides-venia).

### AEM-Projektarchetyp {#aem-project-archtype}

The [AEM Project Archetype](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/overview.html) can be used to create a minimal, best-practices-based Adobe Experience Manager project as a starting point for your own AEM projects. Optional können [AEM CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) in ein neu erstelltes Projekt eingebunden werden.

### CIF-Erweiterungsschicht {#cif-extension}

Die CIF-Erweiterungsschicht ist eine mittlere Ebene, um komplexe Geschäftslogik zu hosten. Es läuft auf der Adobe I/O Runtime-Plattform, der Serverplattform der Adobe. Es ermöglicht Ihnen, End-to-End-Service-Aufrufe zu erweitern, indem Sie Geschäfts- und Prozesslogik auf einer Mikrodienstebene einfügen. Geschäftslogik wäre beispielsweise die Verwendung von Standort und Kanal zur Bestimmung einer Bestandsstrategie. Die Prozesslogik wäre z. B. das Abrufen personalisierter Informationen.

### CIF-Integrationsschicht {#cif-integration-layer}

Die CIF-Integrationsschicht dient zur Standardisierung von Integrationen mit anderen Commerce-Lösungen. Es wird auf der Adobe I/O Runtime-Plattform ausgeführt, die von der Adobe als serverlustfreie Plattform dient und Integrationen auf Mikrodienstebene ermöglicht, indem Drittanbieter-APIs mit den Adobe Commerce-APIs abgeglichen werden. Um Ihnen beim Aufbau von Drittanbieter-Integrationen mit AEM zu helfen, haben wir eine [Referenz-Implementierung](https://github.com/adobe/commerce-cif-graphql-integration-reference) erstellt, um zu zeigen, wie ein Commerce-Back-End ohne Magento über Adobe Commerce-APIs (Magento GraphQL APIs) integriert werden kann.

## AEM Commerce-Integrationsmuster {#aem-commerce-integration}

Einige der häufig implementierten AEM Commerce-Integrationsmuster sind unten dargestellt.

![AEM CIF-Integrationsmuster](/help/commerce-cloud/assets/aem-cif-integration-patterns-updated.JPG)


### Integrationsmuster 1 {#integration-pattern-one}

Dies ist unser empfohlenes Integrationsmuster, bei dem AEM das gesamte Glas besitzt und über Adobe Commerce GraphQL APIs Commerce Services integriert. Dieses Muster bietet AEM volle Flexibilität, um Rich-Media-Site-Designs geräteübergreifend anzupassen. Dieses Integrationsmuster wird von CIF als vordefinierte Lösung unterstützt.


### Integrationsmuster 2 {#integration-pattern-two}

Dieses Muster zeigt eine völlig kopflose Art und Weise, Inhalte und Commerce bereitzustellen. Der Versand ist vollständig clientseitig. In diesem Muster werden Inhalte über API bereitgestellt und HTML- und Commerce-Daten werden über GraphQL bereitgestellt. Dieses Muster wird derzeit nicht standardmäßig von CIF unterstützt.


### Integrationsmuster 3 {#integration-pattern-three}

In diesem Muster besitzt Magento das Glas und bettet AEM verfassten Inhalt ein. Die AEM erstellten Inhalte können über Erlebnisfragmente oder Inhaltsfragmente bereitgestellt werden. Dieses Integrationsmuster erfordert projektspezifische Arbeit und kann nicht standardmäßig mit CIF implementiert werden.


### Integrationsmuster 4 {#integration-pattern-four}

Dies ist ein gängiges Integrationsmuster, bei dem die Glas- oder Präsentationsebene zwischen AEM und einer Commerce-Lösung aufgeteilt wird. Normalerweise liefert die Commerce-Lösung die Nicht-Marketing-Seiten wie Kasse und mein Konto und AEM liefert die Marketing-Seiten und Schaufenster Katalog-Erlebnis. In diesem Muster müssen Sie sicherstellen, dass Einkaufswagen und Benutzersitzungen zwischen den beiden Systemen ordnungsgemäß verarbeitet werden, um eine uneinheitliche Benutzererfahrung zu vermeiden. Zum Beispiel speichert Magento die Einkaufswagen- und Benutzersitzung in einem Cookie, das zwischen AEM &amp; Magento freigegeben werden kann. Dieses Muster erfordert projektspezifische Arbeit und kann nicht sofort mit CIF implementiert werden.
