---
title: Einführung und Überblick
description: Verstehen der verschiedenen Storefront-Optionen
thumbnail: introducing-aem-commerce.jpg
exl-id: 29410f76-a63f-4b0a-b817-2ed724ad1a3c
feature: Commerce Integration Framework
role: Admin
source-git-commit: 80f1c9548b8b87dc6280e0e95988d84a8376f7ab
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 100%

---


# Content and Commerce {#content-commerce}

Da die Kundenerwartungen an absichtsbasierte und effektive Commerce-Erlebnisse wachsen, stehen Marken unter Druck, mehr Inhalte schneller bereitzustellen – ohne Einbußen bei der Qualität. Mit Adobe Experience Manager können Marken schneller skalieren und Innovationen entwickeln, um beeindruckende Commerce-Erlebnisse zu schaffen sowie mehr Traffic und steigende Online-Ausgaben für sich zu gewinnen.

Adobe Experience Manager bietet leistungsstarke Tools zum Erstellen und Verwalten von inhaltsreichen, personalisierten Kundenerlebnissen. Durch die Integration von AEM mit einer Lösung für den Handel (wie Adobe Commerce, Salesforce Commerce, SAP Commerce Cloud oder einer anderen Lösung) können Marken Content und Commerce vereinheitlichen, um kanalübergreifend für nahtlose Shopping-Journeys zu sorgen.

## Überblick über Storefront-Ansätze {#overview}

AEM kann Sie je nach Ihrer Situation und Ihren Präferenzen gezielt unterstützen. Verwenden Sie die folgenden Anleitungen, um den richtigen Ansatz für Sie auszuwählen:

* [Verwenden von Edge Delivery Services (empfohlen)](#edge)
* [Verwenden Ihrer eigenen Storefront (Headless-AEM-Integration)](#own-storefront)
* [Verwenden von AEM CIF-Storefront](#cif)

### Verwenden von Edge Delivery Services (empfohlen) {#edge}

Wenn Ihr Unternehmen die schnellste und KI-freundlichste Storefront im Internet nutzen möchte und Ihr Entwicklungspersonal ein modernes Entwicklererlebnis wünscht, verwenden Sie [Edge Delivery Services.](../edge/overview.md) Edge Delivery Services erfüllt alle Anforderungen von heute und morgen. Je nach Backend und Lösung stehen Ihnen unterschiedliche Optionen zur Verfügung:

#### &#x200B;1. Integration mit Adobe Commerce as a Cloud Service {#acaacs}

Adobe empfiehlt, Edge Delivery und die [Adobe Commerce-Storefront](https://experienceleague.adobe.com/developer/commerce/storefront/?lang=de) als Ausgangspunkt zu verwenden. Die Storefront verfügt über einen Baustein, der mit Adobe Commerce-Services und -APIs vorintegriert ist und eine Vielzahl von Drop-in-Komponenten für Commerce bietet. So können Sie in kürzester Zeit eine Storefront einrichten.

Gut geeignet für: Typisches Storefront-Erlebnis mit Adobe Commerce as a Cloud Service

#### &#x200B;2. Integration mit Adobe Commerce Optimizer (für beliebige Drittanbieterlösungen) {#aco}

Wenn Sie Ihre bestehende Lösung für den Handel integrieren und die Leistung Ihres Katalogs steigern möchten, empfiehlt Adobe, als moderne Integrationsebene [Adobe Commerce Optimizer](https://experienceleague.adobe.com/de/docs/commerce-learn/tutorials/adobe-commerce-optimizer/overview) zu verwenden. Commerce Optimizer erweitert Ihre Lösung für den Handel um leistungsstarke SaaS-Services für Katalog und Merchandising. Wie bei Adobe Commerce as a Cloud Service funktioniert die [Adobe Commerce-Storefront](https://experienceleague.adobe.com/developer/commerce/storefront/?lang=de) damit standardmäßig.

Integrationen in kommerzielle Lösungen für den Handel wie Salesforce Commerce sind verfügbar. Wenden Sie sich an Ihren Adobe-Vertreter.

Gut geeignet für: Typisches Storefront-Erlebnis mit einer vorhandenen Lösung für den Handel

#### &#x200B;3. Benutzerdefinierte Integration {#custom}

Adobe empfiehlt zudem die Verwendung von Edge Delivery Services, wenn Sie eine benutzerdefinierte Integration erstellen möchten. Sie können in Ihrer Edge Delivery-Storefront entweder von Grund auf neu beginnen oder vorhandene JS-Framework-Commerce-Komponenten (z. B. für den Transaktionsteil) wiederverwenden. So erhalten Ihre Kundinnen und Kunden ein unglaublich schnelles Einkaufserlebnis, das agentenfreundlich ist, während Sie vorhandene Investitionen wiederverwenden können, um den TTV-Wert zu verbessern. Ihr Ausgangspunkt ist der standardmäßige [Edge Delivery-Baustein](https://www.aem.live/developer/tutorial).

Gut geeignet für: Geringer Nutzen aus der Edge Delivery-Storefront

### Verwenden Ihrer eigenen Storefront (Headless-AEM-Integration) {#own-storefront}

Sie haben eine bestehende Storefront (z. B. mit React JS erstellt) und möchten Adobe Experience Manager für das Content-Management und die Bereitstellung (Inhaltsfragmente), Assets und kontextbezogene Bearbeitung (universeller Editor) verwenden. Ihr Ausgangspunkt für eine Integration ist [Einführung in Adobe Experience Manager as a Headless CMS](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/headless/introduction) und das [CIF-Add-on](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/content-and-commerce/storefront/authoring/enrich-product-associated-content). Das CIF-Add-on ermöglicht eine nahtlose Integration Ihrer Produktdaten in AEM (Suchen, Durchsuchen und Finden von Produkten in der AEM-Benutzeroberfläche), wobei Sie AEM zum Erstellen Commerce-spezifischer Erlebnisse verwenden können.

### AEM CIF-Storefront {#cif}

Adobes Empfehlung und Referenzarchitektur besteht in der Verwendung von Edge Delivery Services. Die CIF-Storefront mit ihren AEM CIF-Kernkomponenten befindet sich aktuell im Wartungsmodus und sollte nicht in neuen Projekten verwendet werden. Weitere Informationen finden Sie in der [CIF-Dokumentation](/help/commerce-cloud/cif-storefront/introduction.md).

>[!NOTE]
>
>Bestehende Kundschaft, die neue AEM-/Commerce-Funktionen nutzen möchte, sollte ihre Website nach Edge Delivery migrieren. In einem gängigen Muster werden zunächst nur eine Teilmenge der Seiten nach Edge Delivery verschoben und die Edge Delivery- und CIF-Seiten nebeneinander ausgeführt. Es ist auch möglich, AEM CIF-Komponenten durch die neuen [Commerce-Drop-in-Komponenten](https://experienceleague.adobe.com/developer/commerce/storefront/dropins/all/introduction/?lang=de) zu ersetzen, um neue Commerce-Funktionen zu nutzen.
