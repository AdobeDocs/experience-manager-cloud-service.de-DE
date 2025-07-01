---
title: Überblick über Edge Delivery Services
description: Erfahren Sie, wie AEM as a Cloud Service von der Leistung und den perfekten Lighthouse-Werten profitieren kann, die von Edge Delivery Services geboten werden.
feature: Edge Delivery Services
exl-id: 03a1aa93-d2e6-4175-9cf3-c7ae25c0d24e
role: Admin, Architect, Developer
source-git-commit: 207926d68f42f5b398841b92c0a8c72a3f852292
workflow-type: tm+mt
source-wordcount: '963'
ht-degree: 37%

---


# Überblick über Edge Delivery Services {#edge-delivery-services}

## Was ist Edge Delivery Services? {#what-is-edge}

Edge Delivery Services ist ein modernes Framework zur Inhaltsbereitstellung, das die Erstellung und Bereitstellung von Websites neu definiert und die Geschwindigkeit, Einfachheit und Skalierbarkeit optimiert. Es ist ein Kernbestandteil von Adobe Experience Manager und ermöglicht schnellere digitale Erlebnisse, indem das Rendering und die Bereitstellung näher an den Benutzenden am Rand des Netzwerks verschoben werden.

Es ist kein Ersatz für ein Content Delivery Network (CDN), sondern lässt sich nahtlos in Ihr eigenes CDN oder das enthaltene [von Adobe verwaltete CDN integrieren](/help/implementing/dispatcher/cdn.md)

>[!TIP]
>
>**Wollen Sie sofort beginnen?**
>
>Wenn Sie sofort praktische Erfahrungen sammeln möchten, können Sie in weniger als 30 Minuten Ihr eigenes Edge Delivery Services-Projekt mit AEM-Authoring starten, indem Sie [sich das Tutorial auf aem.live ansehen.](https://www.aem.live/developer/ue-tutorial)


## Warum Edge Delivery Services? {#why-edge}

### Erhöht Auffindbarkeit und Traffic {#increase-traffic}

Edge Delivery-Websites sind für Suchmaschinen (SEO) und generative Engines (GEO) optimiert für LLMs. Dies gewährleistet eine hohe Sichtbarkeit und Auffindbarkeit auf allen vorhandenen und kommenden Quellen für organischen Traffic. Die **Performance-First-End-to-End-Architektur** sorgt für ein ansprechendes Kundenerlebnis, das sich positiv auf die Interaktion auswirken wird.

### Effizienz von Entwicklern {#developer-efficientcy}

Live-Schaltung in Tagen und Wochen statt Monaten und Jahren! Edge Delivery bietet alle Tools **moderne Webentwickler** die sie lieben: GitHub, lokale Entwicklung mit automatischem Neuladen, Leistung, Einfachheit und keine der Komplikationen: keine Übersetzung, keine Bundler, keine Konfigurationen, kein Overhead.

Die Einfachheit von Edge Delivery erfordert keine Verwendung komplizierter Frameworks, Tools oder Prozesse, was sich ideal für die Erstellung von KI-Code eignet. Verwenden Sie HTML, modernes CSS und Vanilla JavaScript, um außergewöhnliche Erlebnisse schneller als je zuvor zu erstellen. Konzentrieren Sie sich auf die Arbeit und verwenden Sie weniger Zeit für die Schulung und das Lernen neuer Tools.

Edge Delivery ermöglicht es jedem Entwickler, einen Lighthouse-Wert von 100 zu erreichen.

### Unterstützung mehrerer Inhaltsquellen {#multiple-content-sources}

Inhalte aus verschiedenen Lösungen können direkt in Edge Delivery integriert werden **einschließlich aller vorhandenen AEM-Instanzen**. Autorinnen und Autoren können Inhalte **jedem System wie SharePoint verwalten und in Edge Delivery veröffentlichen** um mit Tools, die sie bereits kennen, mehr Geschwindigkeit zu erzielen.

### Zusammensetzbare Architektur {#composable-architeture}

Ob Headless oder Headful, Sie können die richtigen Inhalte im richtigen Format bereitstellen und die richtige Dekoration hinzufügen, um es zu einem Erlebnis zu machen, das in jedem Kanal auffällt.

## Funktionsweise {#how-does-it-work}

Edge Delivery Services ist ein zusammenstellbarer Satz von Services, der eine hohe Flexibilität bei der Erstellung von Inhalten auf Ihrer Website ermöglicht. Es ersetzt AEM Publish/Dispatcher und die herkömmliche Methode zum Erstellen von Erlebnissen durch AEM-Kernkomponenten durch eine Multi-Cloud-SaaS-Lösung und einen reinen Frontend-Entwicklungsansatz.

![Architektur von Edge Delivery](assets/AEM-with-EDS-architecture.png)

Edge Delivery Services nutzt GitHub, damit Sie Code direkt über ihr GitHub-Repository verwalten und bereitstellen können. Neue Inhalte werden sofort und ohne Neuerstellungsprozess hinzugefügt.

## Authoring {#authoring}

### Kontextbezogenes Bearbeiten {#in-context-editing}

WYSIWYG [Der universelle Editor](/help/implementing/universal-editor/introduction.md) ist ein anpassbarer, zentraler Ort, an dem Sie Inhalte live und im Kontext mit einer visuellen Vorschau bearbeiten können.

* Mit AEM Authoring und dem universellen Editor erhöhen Sie die Autoreneffizienz, egal ob Headless oder Headful.
* Sie können die umfassenden Content-Management-Funktionen von AEM nutzen, einschließlich Workflow und Governance.
* Sie können zahlreiche Erweiterungspunkte nutzen, um Ihre eigenen Prozesse und Integrationen zu unterstützen.
* Die Funktionalität Ihrer Site kann mithilfe von CSS und JavaScript in GitHub entwickelt werden.

![AEM-Authoring mit dem universellen Editor](assets/wysiwyg-authoring.png)

### Dokumentenbasierte Bearbeitung {#document-based-editing}

[Ein weiterer Ansatz ist die dokumentbasierte Inhaltserstellung, ](https://www.aem.live/docs/authoring) Inhalte als Dokumente verwaltet werden. Microsoft Word ist eine beliebte Wahl, da viele Unternehmen SharePoint dort haben, wo die anfänglichen Inhalte erstellt werden. Es ist nicht erforderlich, ein neues Tool zu erlernen und Inhalte direkt aus SharePoint und Word zu veröffentlichen, wodurch das Kopieren und Einfügen von Inhalten in AEM entfällt. Kunden ohne SharePoint können Google Drive auch als Alternative verwenden.

## Betriebstelemetrie {#telemetry}

Adobe Experience Manager verwendet [Betriebstelemetrie](https://www.aem.live/docs/operational-telemetry), um Betriebsdaten zu erfassen, die unbedingt erforderlich sind, um Funktions- und Leistungsprobleme an Adobe Experience Manager-gestützten Sites zu erkennen und zu beheben. Operative Telemetriedaten können zur Diagnose von Leistungsproblemen und zur Messung der Effektivität von Experimenten verwendet werden. Operative Telemetrie bewahrt die Privatsphäre der Besucher durch [Sampling](https://www.aem.live/docs/operational-telemetry#operational-telemetry-data-is-sampled) (nur ein kleiner Teil aller Seitenansichten wird überwacht) und [vernünftigen Ausschluss von persönlich identifizierbaren Informationen](https://www.aem.live/docs/operational-telemetry#what-data-is-being-collected) (PII).

## Exploring starten {#start-exploring}

Erste Schritte mit dem AEM-Authoring mit dem universellen Editor und Edge Delivery Services:

* Dokumentation zu Edge Delivery Services [Edge Delivery Services](https://www.aem.live)
* Einen Überblick über das AEM-Authoring mit dem universellen Editor finden Sie im Dokument zum [AEM-Authoring für Edge Delivery Services](https://www.aem.live/docs/aem-authoring) in der Dokumentation zu aem.live.
* Eine Entwicklungsübersicht finden Sie im Dokument zum [Tutorial zu den ersten Schritten für Entwickelnde mit dem universellen Editor](https://www.aem.live/developer/ue-tutorial) in der Dokumentation zu aem.live.

## Edge Delivery Services und andere Adobe Experience Cloud-Produkte {#edge-other-products}

Edge Delivery Services sind Teil von Adobe Experience Manager. Daher können Edge Delivery Services und AEM Sites gemeinsam in derselben Domain vorhanden sein, was häufig bei größeren Websites der Fall ist. Darüber hinaus können Ihre AEM Sites-Seiten nahtlos Inhalte von Edge Delivery Services nutzen, und auch umgekehrt ist das möglich.

Sie können Edge Delivery Services auch mit [Adobe Target](https://www.aem.live/developer/target-integration) und [Launch.](https://experienceleague.adobe.com/de/docs/experience-platform/tags/home)

## So erhalten Sie Hilfe von Adobe {#getting-help}

Adobe bietet drei Ebenen, die Sie bei der Verwendung von Edge Delivery Services unterstützen:

* Interaktion mit [Community-Ressourcen](#community-resources) für allgemeine Anfragen,
* Zugriff auf Ihren [Kanal für die Produktzusammenarbeit](#collaboration-channel) für spezifische Fragen,
* [Erstellen Sie ein Support-Ticket](#support-ticket), um wichtige Probleme (**vertraglichen Support-SLA) zu**.

### Zugreifen auf Community-Ressourcen {#community-resources}

Adobe setzt sich dafür ein, Ihnen die bestmögliche Community-Interaktion und -Unterstützung für Edge Delivery Services sowie AEM-basiertes Authoring mit dem universellen Editor und dokumentenbasiertes Authoring zu bieten.

* Beteiligen Sie sich an der [Experience League-Community](https://adobe.ly/3Q6kTKl), um Fragen zu stellen, Feedback zu teilen, Diskussionen einzuleiten, Unterstützung von Adobe- und AEM-Fachleuten und -Champions zu erhalten und in Echtzeit mit Gleichgesinnten in Kontakt zu treten. 
* Schließen Sie sich unserem [Discord-Kanal](https://discord.gg/aem-live) an, einer lockereren Plattform für Echtzeitinteraktionen und schnellen Ideenaustausch.

### Einreichen eines Support-Tickets {#support-ticket}

{{support-ticket}}
