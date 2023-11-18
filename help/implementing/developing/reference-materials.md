---
title: API-Referenzmaterial
description: AEM verfügt über umfangreiche und leistungsstarke APIs, die Sie für Ihr Digital-Experience-Projekt nutzen können.
exl-id: d4ef3040-5a0a-4149-9e99-09eda9605038
source-git-commit: bc3c054e781789aa2a2b94f77b0616caec15e2ff
workflow-type: tm+mt
source-wordcount: '662'
ht-degree: 91%

---

# API-Referenzmaterial {#api-reference-materials}

Adobe Experience Manager (AEM) stellt zahlreiche APIs zum Entwickeln von Anwendungen und Erweitern von AEM bereit. AEM basiert auf mehreren Open-Source-Technologien, die auch verwendet werden können.

## AEM-Kern-APIs {#core-aem-apis}

Die folgenden APIs sind zentraler Bestandteil von AEM.

| API | Beschreibung |
|---|---|
| [Adobe Experience Manager as a Cloud Service](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/index.html) | Produktabstraktionen wie Seiten, Assets, Workflows usw. |
| [Granite-Benutzeroberfläche](https://helpx.adobe.com/de/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/index.html#) | Adobe&#39;s Open Web Stack mit verschiedenen wesentlichen Komponenten (die 6.5 Granite-Materialien gelten für AEMaaCS) |
| [Coral-Benutzeroberfläche](https://opensource.adobe.com/coral-spectrum/documentation/) | Der visuelle Stil von Adobe für Cloud-Benutzeroberflächen und ein konsistentes Benutzererlebnis |

<!---
|Editor core JavaScript API reference|Provides all the base objects and concepts to support authoring of content resources|
--->

## Weitere Frameworks {#additional-apis}

AEM benötigt mehrere zusätzliche Open-Source-APIs.

| API | Beschreibung |
|---|---|
| [Apache Sling](https://sling.apache.org/apidocs/sling11/) | Webframework, das ein Java Content Repository (JCR) zum Speichern und Verwalten von Inhalten verwendet |
| [Apache Jackrabbit Oak](https://jackrabbit.apache.org/oak/docs/oak_api/overview.html) | Implementierung eines skalierbaren und leistungsstarken hierarchischen Java Content Repository (JCR) als Grundlage für moderne Websites von Weltklasse |
| [Java Content Repository](https://www.adobe.io/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/index.html) | Spezifikation für die JCR-Version 2.0 |
| [Apache Felix](https://felix.apache.org) | Implementierung des OSGi-Frameworks (Open Services Gateway Initiative) und der OSGi-Service-Plattform |

## Richtlinien für API-Voreinstellungen {#guidelines}

AEM basiert auf den folgenden vier primären Java-API-Sätzen in absteigender Reihenfolge der Bevorzugung.

| Priorität | API | Beschreibung |
|---|---|---|
| 1 | [Adobe Experience Manager as a Cloud Service](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/index.html) | Produktabstraktionen wie Seiten, Assets, Workflows usw. |
| 2 | [Apache Sling](https://sling.apache.org/apidocs/sling11/) | REST- und ressourcenbasierte Abstraktionen wie Ressourcen, Wertzuordnungen und HTTP-Anforderungen. |
| 3 | [Apache Jackrabbit Oak](https://jackrabbit.apache.org/oak/docs/oak_api/overview.html) | Daten- und Inhaltsabstraktionen wie Knoten, Eigenschaften und Sitzungen. |
| 4 | [Apache Felix](https://felix.apache.org/) | OSGi-Programm-Container-Abstraktionen wie Services und (OSGi-) Komponenten. |

Wenn eine API von AEM bereitgestellt wird, sollten Sie sie Sling-, JCR- und OSGi-APIs vorziehen. Wenn AEM keine API bereitstellt, sollten Sie die Sling-API JCR- und OSGi-APIs vorziehen.

>[!TIP]
>
>Weitere Informationen zu diesen Richtlinien finden Sie im Dokument [Grundlegendes zu den Best Practices für Java-APIs](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/understand-java-api-best-practices.html?lang=de).

## AEM-Bereitstellungs- und -Content-Management-Services und -APIs {#delivery-apis}

AEM bietet anpassbare Komponenten- und Inhaltsbereitstellungsoptionen.

| Funktion | Beschreibung |
|---|---|
| [Die Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) | Standardisierte WCM-Komponenten (Web Content Management) für AEM, um die Entwicklungszeit zu verkürzen und die Wartungskosten Ihrer Websites zu senken |
| [JSON Exporter](/help/implementing/developing/components/json-exporter.md) | Bereitstellen des Inhalts einer beliebigen AEM-Seite im JSON-Datenmodellformat |
| [Aktivieren eines JSON-Exports für eine Komponente](/help/implementing/developing/components/enabling-json-exporter.md) | Generieren eines JSON-Exports von Komponenteninhalten basierend auf einem Modeler-Framework |
| [Assets-API](/help/assets/mac-api-assets.md) | Ermöglicht CRUD-Vorgänge (Create-Read-Update-Delete, Erstellen-Lesen-Aktualisieren-Löschen) für Assets, einschließlich Binärdateien, Metadaten, Ausgabedarstellungen und Kommentaren. Siehe AEM Assets-HTTP-API |
| [Inhaltsfragment-HTTP-API](/help/assets/content-fragments/assets-api-content-fragments.md) | Zugreifen auf Inhaltsfragmentinhalte direkt über die HTTP-API über CRUD-Vorgänge |
| [Inhaltsfragment-GraphQL-API](/help/headless/graphql-api/content-fragments.md) | Effiziente Bereitstellung von Inhaltsfragmenten für JavaScript-Clients in Headless-CMS-Implementierungen |
| [HTTP-API für Inhaltsfragment- Assets](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/admin/mac-api-assets.html?lang=de) | Exaktes Format unterstützter HTTP-Asset-Anforderungen |

## SPA-spezifische APIs {#spa-apis}

AEM Single-Page Application (SPA) Editor – SDK-Framework stellt spezifische JavaScript-API-Referenzen bereit.

| API | Beschreibung |
|---|---|
| [Komponentenzuordnung](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping) | Bietet eine Möglichkeit für die Single Page Application, Frontend-Komponenten Adobe Experience Manager-Ressourcentypen (AEM-Komponenten) zuzuordnen |
| [Seitenmodell-Manager](https://www.npmjs.com/package/@adobe/aem-spa-page-model-manager) | Interpreter zwischen Adobe Experience Manager Editor und Adobe Experience Manager Single-Page Application (SPA) Editor |
| [Bearbeitbare React-Komponenten](https://www.npmjs.com/package/@adobe/aem-react-editable-components) | Stellt die React-Komponenten und die Integrationsschicht bereit, um Ihnen die ersten Schritte mit dem Adobe Experience Manager Site Editor zu ermöglichen |
| [Bearbeitbare Angular-Komponenten](https://www.npmjs.com/package/@adobe/aem-angular-editable-components) | Stellt die Angular-Komponenten und Integrationsschicht bereit, um Ihnen die ersten Schritte mit dem Adobe Experience Manager Site Editor zu ermöglichen |

>[!TIP]
>
>Weitere Informationen zu Single Page Applications finden Sie in [SPA-Einführung und exemplarische Anleitung](/help/implementing/developing/hybrid/introduction.md).
