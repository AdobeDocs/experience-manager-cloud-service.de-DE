---
title: Einführung und Übersicht
description: Grundlegendes zu den verschiedenen Storefront-Optionen
thumbnail: introducing-aem-commerce.jpg
exl-id: 29410f76-a63f-4b0a-b817-2ed724ad1a3c
feature: Commerce Integration Framework
role: Admin
source-git-commit: 80f1c9548b8b87dc6280e0e95988d84a8376f7ab
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 1%

---


# Content and Commerce {#content-commerce}

Da die Kundenerwartungen an absichtsbasierte und leistungsstarke Commerce-Erlebnisse wachsen, stehen Marken unter Druck, mehr Inhalte schneller bereitzustellen - ohne Qualitätseinbußen. Mit Adobe Experience Manager können Marken schneller skalieren und Innovationen entwickeln, um beeindruckende Commerce-Erlebnisse zu schaffen und mehr Traffic und wachsende Online-Ausgaben zu erfassen.

Adobe Experience Manager bietet leistungsstarke Tools zum Erstellen und Verwalten von inhaltsreichen, personalisierten Kundenerlebnissen. Durch die Integration von AEM mit einer Lösung für den Handel - wie Adobe Commerce, Salesforce Commerce, SAP Commerce Cloud oder einer anderen - können Marken Inhalte und Commerce vereinheitlichen, um kanalübergreifend nahtlose Shopping-Journey bereitzustellen.

## Ansätze für die Storefront-Übersicht {#overview}

AEM kann Sie je nach Ihrer Situation und Ihren Präferenzen unterstützen. Verwenden Sie die folgenden Anleitungen, um den richtigen Ansatz für Sie auszuwählen:

* [Verwenden von Edge Delivery Services (empfohlen)](#edge)
* [Eigene Storefront verwenden (Headless-AEM-Integration)](#own-storefront)
* [Verwenden der AEM CIF-Storefront](#cif)

### Verwenden von Edge Delivery Services (empfohlen) {#edge}

Wenn Ihr Unternehmen die schnellste und KI-freundlichste Storefront im Internet möchte und Ihre Entwickler ein modernes Entwicklererlebnis wünschen, verwenden Sie [Edge Delivery Services.](../edge/overview.md) Edge Delivery Services erfüllt alle Anforderungen von heute und morgen. Je nach Backend und Lösung stehen Ihnen unterschiedliche Optionen zur Verfügung:

#### &#x200B;1. Integration mit Adobe Commerce as a Cloud Service {#acaacs}

Adobe empfiehlt, Edge Delivery und die [Adobe Commerce-Storefront](https://experienceleague.adobe.com/developer/commerce/storefront/) als Ausgangspunkt zu verwenden. Die Storefront verfügt über ein Textbaustein, der mit Adobe Commerce-Services und -APIs vorintegriert ist und eine Vielzahl von Commerce-Dropdown-Komponenten bietet, um schnell eine Storefront zu erstellen.

Gute Passform: Typisches Storefront-Erlebnis mit Adobe Commerce as a Cloud Service

#### &#x200B;2. Integration mit Adobe Commerce Optimizer (für jede Drittanbieterlösung) {#aco}

Wenn Sie Ihre bestehende Commerce-Lösung integrieren und die Leistung Ihres Katalogs steigern möchten, empfiehlt Adobe, [Adobe Commerce Optimizer](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/adobe-commerce-optimizer/overview) als moderne Integrationsebene zu verwenden. Commerce Optimizer erweitert Ihre Commerce-Lösung mit leistungsstarken SaaS-Services für Katalog und Merchandising. Wie bei Adobe Commerce as a Cloud Service funktioniert [&#128279;](https://experienceleague.adobe.com/developer/commerce/storefront/)Adobe Commerce-Storefront standardmäßig damit.

Integrationen in kommerzielle Commerce-Lösungen wie Salesforce Commerce sind verfügbar. Wenden Sie sich an Ihren Adobe-Vertreter.

Gut geeignet: Typisches Storefront-Erlebnis mit einer vorhandenen Commerce-Lösung

#### &#x200B;3. Benutzerdefinierte Integration {#custom}

Adobe empfiehlt auch die Verwendung von Edge Delivery Services, wenn Sie eine benutzerdefinierte Integration erstellen möchten. Sie können in Ihrer Edge Delivery-Storefront entweder von Grund auf neu beginnen oder vorhandene JS-Commerce-Framework-Komponenten (z. B. für den Transaktionsteil) wiederverwenden. Auf diese Weise erhalten Ihre Kunden ein unglaublich schnelles Einkaufserlebnis, das agentenfreundlich ist, während Sie Ihre vorhandenen Investitionen wiederverwenden können, um das TV-Angebot zu steigern. Ihr Ausgangspunkt ist das standardmäßige [Edge Delivery-Textbaustein](https://www.aem.live/developer/tutorial).

Gute Passform: Geringer Wert aus der Edge Delivery-Storefront

### Eigene Storefront verwenden (Headless-AEM-Integration) {#own-storefront}

Sie haben eine bestehende Storefront (z. B. mit React JS erstellt) und möchten Adobe Experience Manager für die Inhaltsverwaltung und Bereitstellung (Inhaltsfragmente), Assets und kontextbezogene Bearbeitung (universeller Editor) verwenden. Ihr Ausgangspunkt für eine Integration ist [Einführung in Adobe Experience Manager as a Headless CMS](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/headless/introduction) und das [CIF-Add-on](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/content-and-commerce/storefront/authoring/enrich-product-associated-content). Das CIF-Add-on ermöglicht eine nahtlose Integration Ihrer Produktdaten in AEM (Suchen, Durchsuchen und Suchen von Produkten in der AEM-Benutzeroberfläche), die Sie zum Erstellen Commerce-spezifischer Erlebnisse verwenden können.

### AEM CIF-Storefront {#cif}

Adobes Empfehlung und Referenzarchitektur besteht in der Verwendung von Edge Delivery Services. Die CIF-Storefront mit ihren AEM CIF-Kernkomponenten befindet sich jetzt im Wartungsmodus und sollte nicht in neuen Projekten verwendet werden. Weitere Informationen finden Sie in der Dokumentation zu [CIF.](/help/commerce-cloud/cif-storefront/introduction.md)

>[!NOTE]
>
>Bestehende Kunden, die neue AEM-/Commerce-Funktionen nutzen möchten, sollten ihre Website nach Edge Delivery verschieben. In einem gängigen Muster werden zunächst nur eine Teilmenge der Seiten nach Edge Delivery verschoben und die Edge-Bereitstellungs- und CIF-Seiten nebeneinander ausgeführt. Es ist auch möglich, AEM CIF-Komponenten durch die neuen [Commerce-Dropdown-Komponenten zu ersetzen](https://experienceleague.adobe.com/developer/commerce/storefront/dropins/all/introduction/) um neue Commerce-Funktionen zu nutzen.
