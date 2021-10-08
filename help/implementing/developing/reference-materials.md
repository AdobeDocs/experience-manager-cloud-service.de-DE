---
title: API-Referenzmaterial
description: AEM verfügt über umfangreiche und leistungsstarke APIs, die Sie für Ihr digitales Erlebnisprojekt nutzen können.
exl-id: d4ef3040-5a0a-4149-9e99-09eda9605038
source-git-commit: c08e442e58a4ff36e89a213aa7b297b538ae3bab
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 28%

---

# API-Referenzmaterial {#api-reference-materials}

Adobe Experience Manager (AEM) bietet viele APIs für die Entwicklung von Anwendungen und die Erweiterung von AEM. AEM basiert auf einer Reihe von Open-Source-Technologien, die ebenfalls genutzt werden können.

## AEM Core-APIs {#core-aem-apis}

Die folgenden APIs sind von zentraler Bedeutung für AEM.

| API | Beschreibung |
|---|---|
| [Adobe Experience Manager as a Cloud Service](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/index.html) | Produktabstraktionen wie Seiten, Assets, Workflows usw. |
| [Granite-Benutzeroberfläche](https://helpx.adobe.com/de/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/index.html#) | Open Web Stack von Adobe mit verschiedenen wichtigen Komponenten (Beachten Sie, dass die 6.5 Granite-Materialien auf AEMaaCS angewendet werden) |
| [Coral-Benutzeroberfläche](https://opensource.adobe.com/coral-spectrum/documentation/) | Der visuelle Stil der Adobe für Cloud-Benutzeroberflächen, der Konsistenz im Benutzererlebnis bietet |

<!---
|Editor core JavaScript API reference|Provides all the base objects and concepts to support authoring of content resources|
--->

## Weitere Frameworks {#additional-apis}

AEM stützt sich auf eine Reihe zusätzlicher Open-Source-APIs.

| API | Beschreibung |
|---|---|
| [Apache Sling](https://sling.apache.org/apidocs/sling11/) | Webframework, das ein Java Content Repository (JCR) zum Speichern und Verwalten von Inhalten verwendet |
| [Apache Jackrabbit Oak](http://jackrabbit.apache.org/oak/docs/oak_api/overview.html) | Implementierung eines skalierbaren und leistungsstarken hierarchischen Java Content Repository (JCR) zur Verwendung als Grundlage für moderne Websites von Weltklasse |
| [Java Content Repository](https://www.adobe.io/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/index.html) | Spezifikation für die JCR-Version 2.0 |
| [Apache Felix](https://felix.apache.org) | Implementierung des OSGi-Frameworks (Open Services Gateway Initiative) und der Service-Plattform |

## Richtlinien für API-Voreinstellungen {#guidelines}

AEM basiert auf den folgenden vier primären Java-API-Sätzen in absteigender Reihenfolge der Bevorzugung.

| Priorität | API | Beschreibung |
|---|---|---|
| 1 | [Adobe Experience Manager as a Cloud Service](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/index.html) | Produktabstraktionen wie Seiten, Assets, Workflows usw. |
| 2 | [Apache Sling](https://sling.apache.org/apidocs/sling11/) | REST- und ressourcenbasierte Abstraktionen wie Ressourcen, Wertzuordnungen und HTTP-Anforderungen. |
| 3 | [Apache Jackrabbit Oak](http://jackrabbit.apache.org/oak/docs/oak_api/overview.html) | Daten- und Inhaltsabstraktionen wie Knoten, Eigenschaften und Sitzungen. |
| 4 | [Apache Felix](https://felix.apache.org/) | OSGi-Anwendungscontainer-Abstraktionen wie Dienste- und (OSGi-)Komponenten. |

Wenn eine API von AEM bereitgestellt wird, sollten Sie sie Sling-, JCR- und OSGi-APIs vorziehen. Wenn AEM keine API bereitstellt, sollten Sie die Sling-API JCR- und OSGi-APIs vorziehen.

>[!TIP]
>
>Weitere Informationen zu diesen Richtlinien finden Sie im Dokument [Grundlegendes zu den Best Practices für Java-APIs](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/understand-java-api-best-practices.html?lang=de).

## AEM und Content Management Services und APIs {#delivery-apis}

AEM bietet anpassbare Komponenten und Inhaltsbereitstellungsoptionen.

| Funktion | Beschreibung |
|---|---|
| [Die Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) | Standardisierte Web Content Management (WCM)-Komponenten für AEM, um die Entwicklungszeit zu verkürzen und die Wartungskosten Ihrer Websites zu senken |
| [JSON Exporter](/help/implementing/developing/components/json-exporter.md) | Bereitstellen des Inhalts einer beliebigen AEM Seite im JSON-Datenmodellformat |
| [Aktivieren eines JSON-Exports für eine Komponente](/help/implementing/developing/components/enabling-json-exporter.md) | JSON-Export von Komponenteninhalten basierend auf einem Modeler-Framework generieren |
| [Assets-API](/help/assets/mac-api-assets.md) | Ermöglicht CRUD-Vorgänge (Create-Read-Update-Delete, Erstellen/Lesen/Aktualisieren/Löschen) für Assets, einschließlich Binärdateien, Metadaten, Ausgabedarstellungen und Kommentaren. Siehe AEM Assets-HTTP-API |
| [HTTP-API für Inhaltsfragmente](/help/assets/content-fragments/assets-api-content-fragments.md) | Zugreifen auf Inhaltsfragmentinhalte direkt über die HTTP-API über CRUD-Vorgänge |
| [GraphQL-API für Inhaltsfragmente](/help/assets/content-fragments/graphql-api-content-fragments.md) | Effiziente Bereitstellung von Inhaltsfragmenten an JavaScript-Clients in Headless-CMS-Implementierungen |
| [Content Fragments Assets-HTTP-API](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/admin/mac-api-assets.html?lang=de) | Eexaktes Format unterstützter HTTP-Asset-Anforderungen |

## SPA-spezifische APIs {#spa-apis}

AEM Single Page Application (SPA) Editor SDK Framework stellt spezifische JavaScript-API-Referenzen bereit.

| API | Beschreibung |
|---|---|
| [Komponentenzuordnung](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping) | Bietet eine Möglichkeit für die Einzelseiten-App, Frontend-Komponenten Adobe Experience Manager-Ressourcentypen (AEM Komponenten) zuzuordnen |
| [Seitenmodell-Manager](https://www.npmjs.com/package/@adobe/aem-spa-page-model-manager) | Dolmetscher zwischen Adobe Experience Manager Editor und Adobe Experience Manager Single Page Application (SPA) Editor |
| [Bearbeitbare React-Komponenten](https://www.npmjs.com/package/@adobe/aem-react-editable-components) | Stellt die React-Komponenten und die Integrationsschicht bereit, um Ihnen die ersten Schritte mit dem Adobe Experience Manager Site Editor zu ermöglichen |
| [Bearbeitbare Angular-Komponenten](https://www.npmjs.com/package/@adobe/aem-angular-editable-components) | Bietet die Angular-Komponenten und Integrationsebene, um Ihnen die ersten Schritte mit dem Adobe Experience Manager Site Editor zu bieten |

>[!TIP]
>
>Weitere Informationen zu Einzelseitenanwendungen finden Sie in der SPA [Einführung und exemplarische Anleitung](/help/implementing/developing/hybrid/introduction.md) .
