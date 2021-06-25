---
title: Einführung zu Adobe Experience Manager as a Cloud Service – Terminologie
description: Einführung zu Adobe Experience Manager as a Cloud Service – Terminologie
exl-id: a76f68f1-4f84-4844-a099-0952707cd96d
source-git-commit: 4067db2234b29e4ffbe3e76f25afd9d8642a1973
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 97%

---

# Adobe Experience Manager as a Cloud Service – Terminologie {#adobe-experience-manager-as-a-cloud-service-terminology}

Die folgenden Begriffe werden in Bezug auf Adobe Experience Manager (AEM) as a Cloud Service verwendet:

## Produkte {#products}

| Produkt | Beschreibung |
|---|---|
| AEM as a Cloud Service | Die Cloud-native Lösung für die Nutzung von AEM-Anwendungen. |
| AEM Assets as a Cloud Service | Digital Asset Management (DAM) bietet die Möglichkeit, digitale Assets aufzunehmen, zu verarbeiten und zu verwalten, und ermöglicht gleichzeitig die Integration mit dem umfassenderen Adobe Experience Cloud- und Adobe Creative Cloud-Ökosystem. |
| AEM Sites as a Cloud Service | Eine Instanz von AEM as a Cloud Service mit der AEM Sites-Anwendung. |

## Instanzen und Pipelines {#instances-and-pipelines}

| Instanz | Beschreibung |
|---|---|
| Adobe-Pipeline | Mechanismus zum Veröffentlichen von Inhalten – von der Erstellung bis zur Veröffentlichung. |
| AEM-Autorenebene | Beschreibt die Autorenumgebung für AEM Sites und AEM Assets. |
| AEM Vorschauebene | Beschreibt die Vorschauumgebung für Sites. |
| AEM-Veröffentlichungsebene | Beschreibt die Veröffentlichungsumgebung für AEM Sites. |


<!-- This section of the table must be alphabetic -->

## Terminologie {#terminology}

| Begriff | Beschreibung |
|---|---|
| AEM-Bild | Ein bereitstellbares Artefakt, das den AEM-Produkt-Code zusammen mit dem Kunden-Code enthält. |
| Asset-Microservices | Cloud-basierte Services zur Verarbeitung digitaler Assets, die sich für verschiedene Anwendungsfälle für die Asset-Verarbeitung eignen, beispielsweise die Generierung von Ausgabeformaten, PDF-Verarbeitung, Bearbeitung von Teil-Assets und Textextrahierung. Weitere Informationen finden Sie in der [Übersicht über Asset-Microservices](/help/assets/asset-microservices-overview.md). |
| Cloud Manager-Git-Repository | Speicherort, an dem Kunden ihre Code- und Konfigurationseinstellungen speichern. |
| Cloud-Provider | AEM as a Cloud Service unterstützt derzeit Azure. Die Unterstützung von AWS ist auf der Roadmap. |
| Content Delivery Network (CDN) | AEM as Cloud Service wird mit einem Standard-CDN ausgeliefert. Der Hauptzweck besteht darin, die Latenz zu verringern, indem zwischengespeicherte Inhalte von den CDN-Knoten in der Nähe des Browsers bereitgestellt werden. Es ist vollständig verwaltet und für eine optimale Leistung von AEM-Anwendungen konfiguriert. |
| Content-Repository | Speicherort, an dem der Inhalt beibehalten wird. |
| Unternehmensisolation | Die einzelnen Instanzen von AEM as a Cloud Service werden voneinander isoliert. |
| Golden Master | Die AEM-Veröffentlichungsebene. |
| Orchestrierungs-Engine | AEM as a Cloud Service verwendet eine Orchestrierungs-Engine, um sicherzustellen, dass alle Autoren- und Veröffentlichungsdienste nach Bedarf skaliert werden. |
