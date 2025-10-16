---
title: Erstellen einer API-Anfrage – Headless-Einrichtung
description: Erfahren Sie, wie Sie die GraphQL-API für die Headless-Bereitstellung von Inhaltsfragmentinhalten und die Assets-REST-API von AEM zur Verwaltung von Inhaltsfragmenten verwenden.
exl-id: 2b72f222-2ba5-4a21-86e4-40c763679c32
feature: Headless, Content Fragments,GraphQL API
role: Admin, Developer
source-git-commit: 38a4bf89e099432163163e90e08aa0f47407724f
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 92%

---

# Erstellen einer API-Anfrage – Headless-Einrichtung {#accessing-delivering-content-fragments}

Erfahren Sie, wie Sie die GraphQL-API für die Headless-Bereitstellung von Inhaltsfragmentinhalten und die Assets-REST-API von AEM zur Verwaltung von Inhaltsfragmenten verwenden.

## Was sind GraphQL- und Assets-REST-APIs? {#what-are-the-apis}

[Nachdem Sie einige Inhaltsfragmente erstellt haben](create-content-fragment.md), können Sie die APIs von AEM verwenden, um sie headless bereitzustellen.

* Mit der [GraphQL-API](/help/headless/graphql-api/content-fragments.md) können Sie Anfragen für den Zugriff auf und die Bereitstellung von Inhaltsfragmenten erstellen. Diese API bietet die zuverlässigsten Funktionen zum Abfragen und Verwenden von Inhaltsfragmentinhalten.
   * Um die API zu verwenden, [definieren Sie Endpunkte und aktivieren Sie sie in AEM](/help/headless/graphql-api/graphql-endpoint.md), und aktivieren Sie gegebenenfalls die [installierte GraphiQL-Oberfläche](/help/headless/graphql-api/graphiql-ide.md).
* Eine Auswahl von [AEM-APIs für die Bereitstellung und Verwaltung strukturierter Inhalte ](/help/headless/apis-headless-and-content-fragments.md) für die Verwendung mit Inhaltsfragmenten verfügbar.

Der Rest dieses Handbuchs konzentriert sich auf den GraphQL-Zugriff und die Bereitstellung von Inhaltsfragmenten.

## Aktivieren eines GraphQL-Endpunkts {#enable-graphql-endpoint}

Bevor die GraphQL-APIs verwendet werden können, muss ein GraphQL-Endpunkt erstellt werden.

Weitere Informationen finden Sie unter [Verwalten von GraphQL-Endpunkten in AEM](/help/headless/graphql-api/graphql-endpoint.md).

## Abfragen von Inhalten unter Verwendung von GraphQL mit GraphiQL

Informationsarchitektinnen und -architekten entwerfen Abfragen für ihre Kanalendpunkte, um Inhalte bereitzustellen. Berücksichtigen Sie diese Abfragen pro Endpunkt und Modell nur einmal. Für die Zwecke dieses Erste-Schritte-Handbuchs müssen Sie nur eine erstellen.

GraphiQL ist eine IDE, die in Ihrer AEM-Umgebung integriert ist; sie wird verfügbar/sichtbar, nachdem Sie [Ihre Endpunkte konfiguriert haben](#enable-graphql-endpoint).

Weitere Informationen finden Sie unter [Verwenden der GraphiQL-IDE](/help/headless/graphql-api/graphiql-ide.md).

GraphQL ermöglicht strukturierte Abfragen, die nicht nur auf bestimmte Datensätze oder einzelne Datenobjekte abzielen, sondern auch bestimmte Elemente der Objekte und verschachtelte Ergebnisse bereitstellen können, Unterstützung für Abfragevariablen bieten und vieles mehr.

GraphQL kann sowohl iterative API-Anfragen als auch Überbereitstellungen vermeiden und ermöglicht stattdessen eine Massenbereitstellung von genau dem, was zum Rendern als Antwort auf eine einzelne API-Abfrage benötigt wird. Das resultierende JSON kann verwendet werden, um Daten in anderen Sites oder Mobile Apps bereitzustellen.

## Nächste Schritte {#next-steps}

Das war´s! Sie haben nun ein grundlegendes Verständnis für das Headless-Content-Management in AEM. Es gibt viele weitere Ressourcen, mit deren Hilfe Sie sich ein umfassendes Verständnis der verfügbaren Funktionen aneignen können.

* **[Inhaltsfragmente](/help/sites-cloud/administering/content-fragments/managing.md)** – Weitere Informationen zum Erstellen und Verwalten von Inhaltsfragmenten
* **[Unterstützung von Inhaltsfragmenten in der AEM Assets-HTTP-API](/help/assets/content-fragments/assets-api-content-fragments.md)** – Weitere Informationen zum direkten Zugriff auf AEM-Inhalte über die HTTP-API über CRUD-Vorgänge (Erstellen, Lesen, Aktualisieren, Löschen)
* **[GraphQL-API](/help/headless/graphql-api/content-fragments.md)** – Weitere Informationen zum Headless-Bereitstellen von Inhaltsfragmenten

>[!NOTE]
>
>Die [OpenAPIs für Inhaltsfragmente und Inhaltsfragmentmodelle](/help/headless/content-fragment-openapis.md) sind ebenfalls verfügbar.
