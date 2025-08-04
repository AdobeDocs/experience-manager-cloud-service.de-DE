---
title: Integrieren von Edge Delivery Services mit Adobe Managed CDN in Cloud Manager
description: null
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
hide: true
hidefromtoc: true
source-git-commit: 2d2a206fea14d7e786a98e848bc2f2592ac65429
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---


# Integrieren von Edge Delivery Services mit Adobe Managed CDN in Cloud Manager {#integrate-adbe-cdn-with-edservices-in-cm}

Adobe Managed CDN (AMC-D) wird nativ mit Edge Delivery Services integriert, um Ihnen leistungsstarke, global verteilte Erlebnisse für Adobe Experience Manager (AEM)-Sites zu bieten.

Zusammen bieten sie Ihnen die folgenden Vorteile:

* Ein schlüsselfertiges CDN auf Unternehmensniveau, das von Adobe verwaltet wird.
* Eine moderne Edge-Bereitstellungsebene, die Anfragen beschleunigt, das Caching optimiert und vor häufigen Angriffen schützt.
* Ein einheitlicher Cloud Manager-Workflow für die Domain-Verwaltung, SSL-Zertifikate und Pipeline-gesteuerte Bereitstellungen.

<!--
Adobe's Edge Delivery Services (EDS) can take advantage of an Adobe managed CDN. EDS is a framework that optimizes website delivery for speed, simplicity, and scalability by pushing content closer to the user through edge nodes. It is not a replacement for a CDN, but rather a way to enhance content delivery, especially when you use the Adobe managed CDN. It offers you the following benefits:

* Adobe-Managed CDN: EDS can use an Adobe-managed CDN, offering features like self-service CDN management and automatic certificate renewal. 
* EDS and AEM: EDS is a feature of AEM as a Cloud Service and works alongside the AEM authoring environment. 
* Performance enhancement: EDS, in conjunction with an Adobe Managed CDN, improves website performance by caching content at edge locations closer to users, reducing latency. 
* Flexibility: EDS provides flexibility in content delivery, allowing your organization to choose between the Adobe-managed CDN or their own CDN setup, based on their needs and existing infrastructure. 
Self-Service CDN Management:
Adobe-managed CDN within EDS enables self-service configuration and management tasks like SSL certificate setup. 
 
Use Cases:
EDS with CDN integration is beneficial for various scenarios, including e-commerce storefronts and websites requiring high performance and scalability. -->

## Edge Delivery Services-Bereitstellungsoptionen in Adobe Managed CDN in Cloud Manager {#deployment-options}

In diesem Abschnitt werden die beiden Möglichkeiten erläutert, wie Sie Edge Delivery Services in Adobe im verwalteten CDN in Cloud Manager bereitstellen können, und, was genauso wichtig ist, wie Sie entscheiden können, welche Option für Ihren Anwendungsfall am besten geeignet ist.

Edge Delivery Services kann mit einer der beiden folgenden Optionen eingerichtet werden. Jede Version verfügt über unterschiedliche Funktionen.

|  | Bereitstellungsoption | Schlüsseldokument | Funktion | Am besten geeignet für |
| --- | --- | --- | --- | --- |
| Option 1 | *Mit* einer bestehenden AEM as a Cloud Service-Umgebung (AEMaaCS) | [Einrichten eines Proxys aus einer vorhandenen Umgebung](https://www.aem.live/docs/byo-cdn-adobe-managed#option-1-setup-a-proxy-from-an-existing-environment) | Die Konfigurations-Pipeline ist für AEMaaCS-Umgebungen allgemein verfügbar | Teams, die bereits Sites in Cloud Manager ausführen und eine schnelle, risikoarme Leistungssteigerung wünschen. |
| Option 2 | *Ohne* bestehende AEMaaCS-Umgebung, auch als eigenständige &quot;Edge-Umgebung“ bezeichnet. | [Einrichten einer Edge Delivery-Site ohne vorhandene Umgebung](https://www.aem.live/docs/byo-cdn-adobe-managed#option-2-setup-an-edge-delivery-site-without-an-existing-environment) | Die Konfigurations-Pipeline ist derzeit nur für Edge-Umgebungen über das eingeschränkte Beta-Programm verfügbar.<br>Siehe [Edge Delivery-Konfigurations-Pipeline hinzufügen](help/implementing/cloud-manager/release-notes/current.md##add-eds-pipeline). | Neue Builds oder Migrationen, die die vollständige Edge Delivery-Architektur und granulares Routing umfassen möchten. |

<!-- Ultimately this URL above will need to be updated on GA -->

| Option | Zusammenfassung | Am besten geeignet für | Wichtige Dokumente |
| --- | --- | --- | --- |
| Adobe Managed CDN Proxy | Adobe Managed CDN stellt eine vorhandene AEM Sites-Umgebung bereit. Ihre aktuelle Sites-Pipeline bleibt der „Ursprung“, während AMC-D das Edge-Caching und die TLS-Beendigung übernimmt. | Teams, die bereits Sites in Cloud Manager ausführen und eine schnelle, risikoarme Leistungssteigerung wünschen. | Einrichten eines AMC-D Proxy |
| Pipeline mit OriginSelectors konfigurieren | Eine dedizierte Edge Delivery Config-Pipeline veröffentlicht statische und dynamische Inhalte direkt am Edge. `originSelectors` Routing des Traffics zwischen AMC-D und Ihren AEM-Autoren-/Veröffentlichungsebenen | Neue Builds oder Migrationen, die die vollständige Edge Delivery-Architektur und granulares Routing umfassen möchten. | Konfigurieren der Edge Delivery-Pipeline |

>[!TIP]
>
>Unsicher, welchen Pfad Sie wählen sollen? Entscheidungsrichtlinien [ Sie unten unter ](#choose-deployment-model)Wählen eines Bereitstellungsmodells“.

## Bereitstellungsmodell auswählen {#choose-deployment-model}

Beide Modelle können innerhalb desselben Cloud Manager-Programms koexistieren, sodass stufenweise Migrationen möglich sind.

| Wenn Sie… | Verwenden Sie dann … |
| :--- | :--- |
| Ein schneller Rollout mit minimalen Änderungen ist erforderlich und Sites werden bereits in Cloud Manager gehostet | AMC-D Proxy |
| Planen Sie die Neustrukturierung von Inhalten für Edge Delivery oder wünschen Sie sich ein differenziertes Routing zwischen mehreren Ursprüngen | Konfiguration der Edge-Bereitstellungs-Pipeline + `originSelectors` |

## Voraussetzungen {#prerequisites}

1. Onboarding Ihrer Site in Cloud Manager
- Erforderlich für beide Bereitstellungsmodelle. Begleiten Sie eine AEM-Site.

2. Eigenes Git hinzufügen (BYOG) (optional)
- Wenn Sie Website-Code außerhalb von Adobe Git speichern, schließen Sie das BYOG-Onboarding ab.

3. Edge Delivery-Lizenz
- Stellen Sie sicher, dass Ihr Programm für Edge Delivery Services lizenziert ist.


