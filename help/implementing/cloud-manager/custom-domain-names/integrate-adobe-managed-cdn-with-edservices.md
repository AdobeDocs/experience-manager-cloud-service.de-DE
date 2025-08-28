---
title: Integrieren von Edge Delivery Services mit Adobe Managed CDN in Cloud Manager
description: null
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
hide: true
hidefromtoc: true
source-git-commit: 2d2a206fea14d7e786a98e848bc2f2592ac65429
workflow-type: ht
source-wordcount: '477'
ht-degree: 100%

---


# Integrieren von Edge Delivery Services mit Adobe Managed CDN in Cloud Manager {#integrate-adbe-cdn-with-edservices-in-cm}

Adobe Managed CDN (AMC-D) ist nativ mit Edge Delivery Services integriert, um Ihnen leistungsstarke, global verteilte Erlebnisse für Adobe Experience Manager(AEM)-Sites zu bieten.

Zusammen bieten Ihnen die Lösungen folgende Vorteile:

* Ein schlüsselfertiges CDN auf Unternehmensniveau, das von Adobe verwaltet wird.
* Eine moderne Edge-Bereitstellungsebene, die Anfragen beschleunigt, das Caching optimiert und vor gängigen Angriffen schützt.
* Einen einheitlichen Cloud Manager-Workflow für die Domain-Verwaltung, SSL-Zertifikate und Pipeline-gesteuerte Bereitstellungen.

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

In diesem Abschnitt werden die beiden Möglichkeiten erläutert, wie Sie Edge Delivery Services in Adobe Managed CDN in Cloud Manager bereitstellen können. Zudem erfahren Sie, wie Sie entscheiden können, welche Option für Ihren Anwendungsfall am besten geeignet ist.

Edge Delivery Services lässt sich mit einer der beiden folgenden Optionen einrichten. Jede Option verfügt über unterschiedliche Merkmale.

|  | Bereitstellungsoption | Schlüsseldok. | Funktion | Am besten geeignet für |
| --- | --- | --- | --- | --- |
| Option 1 | *Mit* einer bestehenden AEM as a Cloud Service-Umgebung (AEMaaCS) | [Einrichten eines Proxys in einer vorhandenen Umgebung](https://www.aem.live/docs/byo-cdn-adobe-managed#option-1-setup-a-proxy-from-an-existing-environment) | Die Konfigurations-Pipeline ist für AEMaaCS-Umgebungen allgemein verfügbar | Teams, die bereits Sites in Cloud Manager ausführen und eine schnelle, risikoarme Leistungssteigerung wünschen. |
| Option 2 | *Ohne* bestehende AEMaaCS-Umgebung, auch als eigenständige „Edge-Umgebung“ bezeichnet. | [Einrichten einer Edge Delivery-Site ohne vorhandene Umgebung](https://www.aem.live/docs/byo-cdn-adobe-managed#option-2-setup-an-edge-delivery-site-without-an-existing-environment) | Die Konfigurations-Pipeline ist für Edge-Umgebungen derzeit nur über das eingeschränkte Beta-Programm verfügbar.<br>Siehe [Hinzufügen einer Konfigurations-Pipeline für Edge Delivery](help/implementing/cloud-manager/release-notes/current.md##add-eds-pipeline). | Neue Builds oder Migrationen, die die vollständige Edge Delivery-Architektur und granulares Routing umfassen sollen. |

<!-- Ultimately this URL above will need to be updated on GA -->

| Option | Zusammenfassung | Am besten geeignet für | Schlüsseldok. |
| --- | --- | --- | --- |
| Adobe Managed CDN Proxy | Adobe Managed CDN stellt eine vorhandene AEM Sites-Umgebung bereit. Ihre aktuelle Sites-Pipeline bleibt der „Ursprung“, während AMC-D das Edge-Caching und die TLS-Terminierung übernimmt. | Teams, die bereits Sites in Cloud Manager ausführen und eine schnelle, risikoarme Leistungssteigerung wünschen. | Einrichten eines AMC-D-Proxys |
| Konfigurations-Pipeline mit originSelectors | Eine dedizierte Konfigurations-Pipeline für Edge Delivery veröffentlicht statische und dynamische Inhalte direkt am Edge. `originSelectors` Routing des Traffics zwischen AMC-D und Ihren AEM-Autoren-/Veröffentlichungsebenen. | Neue Builds oder Migrationen, die die vollständige Edge Delivery-Architektur und granulares Routing umfassen sollen. | Konfigurieren der Edge Delivery-Pipeline |

>[!TIP]
>
>Sie sind unsicher, welchen Pfad Sie wählen sollen? Entscheidungsrichtlinien finden Sie unten unter [Wählen eines Bereitstellungsmodells](#choose-deployment-model).

## Auswählen eines Bereitstellungsmodells {#choose-deployment-model}

Beide Modelle können innerhalb desselben Cloud Manager-Programms koexistieren, sodass stufenweise Migrationen möglich sind.

| Wenn Sie: | Dann verwenden Sie: |
| :--- | :--- |
| Einen schnellen Rollout mit minimalen Änderungen wünschen und Sites bereits in Cloud Manager gehostet wird | AMC-D-Proxy |
| Eine Neustrukturierung von Inhalten für Edge Delivery oder differenziertes Routing zwischen verschiedenen Ursprüngen wünschen | Konfigurations-Pipeline für Edge Delivery + `originSelectors` |

## Voraussetzungen {#prerequisites}

1. Onboarding Ihrer Site in Cloud Manager
– Bei beiden Bereitstellungsmodellen erforderlich. Folgen Sie „Onboarding einer AEM-Site“.

2. Bring Your Own Git (BYOG) (optional)
- Wenn Sie Sitecode außerhalb von Adobe Git speichern, schließen Sie das BYOG-Onboarding ab.

3. Edge Delivery-Lizenz
- Stellen Sie sicher, dass Ihr Programm für Edge Delivery Services lizenziert ist.


