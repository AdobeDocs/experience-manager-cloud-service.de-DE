---
title: AEM REST OpenAPI für die Bereitstellung von Inhaltsfragmenten
description: Erfahren Sie mehr über die AEM REST OpenAPI für die Bereitstellung von Inhaltsfragmenten
feature: Headless, Content Fragments, Edge Delivery Services
role: Admin, Developer
source-git-commit: d98aa9d206486022d465ca19c8888088562d56c3
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---


# AEM REST OpenAPI für die Bereitstellung von Inhaltsfragmenten {#aem-rest-openapi-for-content-fragment-delivery}

>[!IMPORTANT]
>
>Diese API ist über das Early Adopter-Programm verfügbar.
>
>Informationen zum Status und zur Anwendung bei Interesse finden Sie in den [Versionshinweisen](/help/release-notes/release-notes-cloud/release-notes-current.md).

In Adobe Experience Manager (AEM) as a Cloud Service die AEM REST OpenAPI für die Bereitstellung von Inhaltsfragmenten:

* ist eine HTTP-REST-API für [AEM Edge Delivery Services](/help/edge/overview.md), mit der strukturierte Inhalte aus Inhaltsfragmenten im JSON-Format bereitgestellt werden können.
* bietet eine moderne CDN-Integration, die die Invalidierung aktiver Inhalte ermöglicht
* konzentriert sich auf die Bereitstellung von Inhalten (Leistung, Skalierbarkeit, CDN-Integration, optimierte JSON-Steuerung und -Ausgabe).
* umfasst die Möglichkeit, JSON für referenzierte Fragmente und Assets zu hydrieren.

Diese API:

* ist der Nachfolger von [Unterstützung von Inhaltsfragmenten in der AEM Assets HTTP API](/help/assets/content-fragments/assets-api-content-fragments.md)

* ergänzt die OpenAPIs für [Inhaltsfragmente und Inhaltsfragmentmodelle](/help/headless/content-fragment-openapis.md), mit denen Sie die Inhaltsfragmente und Inhaltsfragmentmodelle (CRUD) verwalten können.

* ist eine HTTP-REST-Alternative zur [AEM GraphQL-API zur Verwendung mit Inhaltsfragmenten](/help/headless/graphql-api/content-fragments.md)

Eine vollständige Dokumentation finden Sie unter [AEM Sites API-Schemas - Content Fragments Delivery API (2024.07-experimental)](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/sites/delivery/).

>[!NOTE]
>
>Unter [AEM APIs für die Bereitstellung und Verwaltung strukturierter Inhalte](/help/headless/apis-headless-and-content-fragments.md) finden Sie einen Überblick über die verschiedenen verfügbaren APIs und einen Vergleich einiger der damit verbundenen Konzepte.

## Caching {#caching}

AEM integriert sich in das AEM CDN Fastly. Das bedeutet, dass auf der Veröffentlichungsstufe bereitgestellte JSON-Antworten auf der Ebene Schnell zwischengespeichert werden.

Antworten werden dann zwischengespeichert, basierend auf vordefinierten Zwischenspeicherkopfzeilen (können nicht konfiguriert werden):

* Antworten werden 5 Minuten lang im Browser-/Client-Cache zwischengespeichert
   * `max-age`=`300`
* Antworten werden 1 Stunde lang im CDN-Cache zwischengespeichert
   * `s-maxage`=`3600`
* Veraltete Inhalte können bei der erneuten Validierung neuer Anforderungen für bis zu 1 Stunde bereitgestellt werden
   * `stale-while-revalidate`=`3600`
* Veraltete Inhalte können mit einem Fehler bis zu 1 Tag lang bereitgestellt werden
   * `stale-on-error`=`86400`

AEM enthält auch eine aktive CDN-Cache-Invalidierung. Das bedeutet, dass bei jeder Aktualisierung oder Veröffentlichung von Inhalten die entsprechenden JSON OpenAPI-Antworten über eine Soft-Bereinigungsanfrage an Fastly automatisch invalidiert werden. Auf diese Weise können Sie Änderungen sehen, die in der JSON-Ausgabe widergespiegelt werden, bevor die tatsächliche CDN-Cache-Seite (`s-maxage`) erreicht wird.