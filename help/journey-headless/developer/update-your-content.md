---
title: Aktualisieren Ihres Inhalts über AEM-APIs
description: In diesem Teil der AEM Headless-Entwickler-Tour erfahren Sie, wie Sie mit den verfügbaren APIs auf die Inhalte Ihrer Inhaltsfragmente zugreifen und diese aktualisieren können.
exl-id: 84120856-fd1d-40f7-8df4-73d4cdfcc43b
solution: Experience Manager
feature: Headless, Content Fragments, GraphQL API
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 100%

---

# Aktualisieren Ihres Inhalts über AEM-APIs {#update-your-content}

In diesem Teil der [AEM Headless-Entwickler-Tour](overview.md) erfahren Sie, wie Sie mit den verfügbaren APIs auf die Inhalte Ihrer Inhaltsfragmente zugreifen und diese aktualisieren können.

## Ihre bisherige Tour {#story-so-far}

Im vorherigen Dokument der AEM Headless-Tour, [Zugriff auf Ihre Inhalte über AEM-Bereitstellungs-APIs](access-your-content.md) haben Sie erfahren, wie Sie über die AEM-GraphQL-API auf Ihre Headless-Inhalte in AEM zugreifen können. Nun sollten Sie:

* über ein hohes Maß an Verständnis von GraphQL verfügen,
* verstehen, wie die AEM-GraphQL-API funktioniert,
* einige praktische Beispielabfragen verstehen.

Dieser Artikel baut auf diesen Grundlagen auf, sodass Sie verstehen, wie Sie Ihre vorhandenen Headless-Inhalte in AEM über die verfügbaren APIs aktualisieren können.

## Ziel {#objective}

* **Zielgruppe**: Fortgeschrittene
* **Ziele**: Sie erfahren, wie Sie mit den verfügbaren APIs auf die Inhalte Ihrer Inhaltsfragmente zugreifen und diese aktualisieren können:

## AEM-APIs zur Verwendung mit Inhaltsfragmenten {#aem-apis-for-use-with-content-fragments}

Adobe Experience Manager (AEM) as a Cloud Service bietet mehrere APIs für die Bereitstellung strukturierter Inhalte über Inhaltsfragmente und die Verwaltung von Inhaltsfragmenten. Weitere Informationen zu den spezifischen APIs finden Sie auf den einzelnen Seiten.

* Bereitstellung von AEM-Inhaltsfragmenten mit OpenAPI
   * Diese API erstellt JSON-Antworten für die Bereitstellung strukturierter Inhalte aus Inhaltsfragmenten in AEM.
   * Sie verwendet einen Pfad zu einem Inhaltsfragment als Endpunkt.
   * Diese API basiert auf REST.
   * Sie ist für die Bereitstellung von Inhalten optimiert, einschließlich der CDN-Integration.
* AEM-GraphQL-API für die Bereitstellung von Inhaltsfragmenten
   * Diese API ist schemabasiert. API-Schemata werden durch Inhaltsfragmentmodelle dargestellt, die die Inhaltsstruktur definieren.
   * Diese API basiert auf GraphQL.
* OpenAPIs für Inhaltsfragmente und Inhaltsfragmentmodelle
   * Diese APIs sind für die Verwaltung strukturierter Inhalte vorgesehen.
   * Die jeweiligen GET-Operatoren sind nicht für die Inhaltsbereitstellung optimiert.
   * Diese API basiert auf REST.

>[!NOTE]
>
>Die [Unterstützung von Inhaltsfragmenten im Assets-HTTP-API](/help/assets/content-fragments/assets-api-content-fragments.md) ist jetzt [veraltet](/help/release-notes/deprecated-removed-features.md). Sie wurde ersetzt durch die [Bereitstellung von Inhaltsfragmenten mit OpenAPI](/help/headless/aem-content-fragment-delivery-with-openapi.md) zusammen mit [OpenAPIs für die Verwaltung von Inhaltsfragmentmodellen](/help/headless/content-fragment-openapis.md).

## So geht es weiter {#whats-next}

Nachdem Sie nun diesen Teil der AEM Headless-Entwickler-Tour abgeschlossen haben, sollten Sie über die folgenden Kenntnisse verfügen:

* Grundlegendes zu verfügbaren AEM-APIs.
* Grundlegendes dazu, wie Inhaltsfragmente in diesen APIs unterstützt werden.

Sie sollten Ihre AEM-Headless-Tour fortsetzen, indem Sie als Nächstes das Dokument [Wie man alles zusammenfügt – Ihre App und Ihre Inhalte in AEM Headless](put-it-all-together.md) lesen, in dem Sie sich mit den Grundlagen der AEM-Architektur und den Tools vertraut machen, die Sie zum Zusammenstellen Ihrer Anwendung benötigen.

## Zusätzliche Ressourcen {#additional-resources}

* [Adobe Experience Manager as a Cloud Service-APIs](https://developer.adobe.com/experience-cloud/experience-manager-apis/)
* [AEM-APIs für die Bereitstellung und Verwaltung strukturierter Inhalte](/help/headless/apis-headless-and-content-fragments.md)
* [Bereitstellung von AEM-Inhaltsfragmenten mit OpenAPI](/help/headless/aem-content-fragment-delivery-with-openapi.md)
* [AEM-GraphQL-API für die Bereitstellung von Inhaltsfragmenten](/help/headless/graphql-api/content-fragments.md)
* [OpenAPIs für Inhaltsfragmente und Inhaltsfragmentmodelle](/help/headless/content-fragment-openapis.md)
* [Unterstützung von Inhaltsfragmenten im AEM Assets-HTTP-API](/help/assets/content-fragments/assets-api-content-fragments.md)
* [Arbeiten mit Inhaltsfragmenten](/help/sites-cloud/administering/content-fragments/overview.md)
* [AEM-Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de)
* [Erklärung: CORS/AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing.html?lang=de)
* [Video: Entwicklung für CORS mit AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/develop-for-cross-origin-resource-sharing.html?lang=de)
* [Einführung in AEM als Headless-CMS](/help/headless/introduction.md)
* [AEM-Entwicklerportal](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html?lang=de)
* [Headless-Tutorials für AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html?lang=de)
