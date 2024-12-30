---
title: AEM REST OpenAPI für die Bereitstellung von Inhaltsfragmenten
description: Erfahren Sie mehr über die AEM REST OpenAPI für die Bereitstellung von Inhaltsfragmenten
feature: Headless, Content Fragments, Edge Delivery Services
role: Admin, Developer
exl-id: 838f7781-33e4-4cb1-8a58-8099863f7704
source-git-commit: 4eb0feecbc5d0f090789bd3023e366ef4eb620db
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 100%

---

# AEM REST OpenAPI für die Bereitstellung von Inhaltsfragmenten {#aem-rest-openapi-for-content-fragment-delivery}

>[!IMPORTANT]
>
>Diese API ist über ein Early-Adopter-Programm verfügbar.
>
>Den Status und Informationen zur Bewerbung finden Sie in den [Versionshinweisen](/help/release-notes/release-notes-cloud/release-notes-current.md).

In Adobe Experience Manager (AEM) as a Cloud Service umfasst die AEM REST OpenAPI für die Bereitstellung von Inhaltsfragmenten Folgendes:

* Sie ist eine HTTP-REST-API für [AEM Edge Delivery Services](/help/edge/overview.md), mit der strukturierte Inhalte aus Inhaltsfragmenten im JSON-Format bereitgestellt werden können.
* Sie bietet eine moderne CDN-Integration, die die Invalidierung aktiver Inhalte ermöglicht.
* Sie konzentriert sich auf die Bereitstellung von Inhalten (Leistung, Skalierbarkeit, CDN-Integration, optimierte JSON-Steuerung und -Ausgabe).
* Sie umfasst die Möglichkeit, JSON für referenzierte Fragmente und Assets einzubinden.

Diese API:

* ist die Nachfolgerin der [Unterstützung für Inhaltsfragmente in der AEM-Assets-HTTP-API](/help/assets/content-fragments/assets-api-content-fragments.md).

* ergänzt die OpenAPIs mit [Inhaltsfragmenten und Inhaltsfragmentmodellen](/help/headless/content-fragment-openapis.md), mit denen Sie die Inhaltsfragmente und Inhaltsfragmentmodelle (CRUD) verwalten können.

* ist eine HTTP-REST-Alternative zur [AEM-GraphQL-API zur Verwendung mit Inhaltsfragmenten](/help/headless/graphql-api/content-fragments.md).

Eine vollständige Dokumentation finden Sie unter [AEM Sites-API-Schemata – API für die Bereitstellung von Inhaltsfragmenten (2024.07-experimental)](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/sites/delivery/).

>[!NOTE]
>
>Unter [AEM-APIs für die Bereitstellung und Verwaltung strukturierter Inhalte](/help/headless/apis-headless-and-content-fragments.md) finden Sie einen Überblick über die verschiedenen verfügbaren APIs und einen Vergleich einiger der damit verbundenen Konzepte.

## Caching {#caching}

AEM integriert sich in das AEM CDN Fastly. Das bedeutet, dass auf der Veröffentlichungsstufe bereitgestellte JSON-Antworten auf der Fastly-Ebene zwischengespeichert werden.

Antworten werden dann zwischengespeichert, basierend auf vordefinierten Zwischenspeicherkopfzeilen (können nicht konfiguriert werden):

* Antworten werden 5 Minuten lang im Browser-/Client-Cache zwischengespeichert.
   * `max-age`=`300`
* Antworten werden 1 Stunde lang im CDN-Cache zwischengespeichert.
   * `s-maxage`=`3600`
* Veraltete Inhalte können bei der erneuten Validierung neuer Anforderungen für bis zu 1 Stunde bereitgestellt werden.
   * `stale-while-revalidate`=`3600`
* Veraltete Inhalte können mit einem Fehler bis zu 1 Tag lang bereitgestellt werden.
   * `stale-on-error`=`86400`

AEM umfasst auch eine aktive CDN-Cache-Invalidierung. Das bedeutet, dass bei jeder Aktualisierung oder Veröffentlichung von Inhalten die entsprechenden JSON OpenAPI-Antworten über eine Soft-Bereinigungsanfrage an Fastly automatisch invalidiert werden. Auf diese Weise können Sie Änderungen sehen, die sich in der JSON-Ausgabe widerspiegeln, bevor die tatsächliche CDN-Cache-Seite (`s-maxage`) erreicht wird.
