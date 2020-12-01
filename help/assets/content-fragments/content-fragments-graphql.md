---
title: Versand ohne Inhalt mit Inhaltsfragmenten mit GraphQL
description: Erfahren Sie, wie Sie Inhaltsfragmente in Adobe Experience Manager (AEM) als Cloud Service mit GraphQL für den Versand "Headless Content"verwenden.
translation-type: tm+mt
source-git-commit: ae918d074d4bacfc207d4dca2c67f41a3118aff4
workflow-type: tm+mt
source-wordcount: '807'
ht-degree: 0%

---


# Versand ohne Inhalt mit Inhaltsfragmenten mit GraphQL {#headless-content-delivery-using-content-fragments-with-graphQL}

>[!CAUTION]
>
>Die AEM GraphQL API für Content Fragment Versand wird Anfang 2021 veröffentlicht.
>
>Die entsprechende Dokumentation steht bereits zur Vorschau zur Verfügung.

Mit Adobe Experience Manager (AEM) als Cloud Service können Sie Inhaltsfragmente zusammen mit der AEM GraphQL API (eine auf GraphQL basierende benutzerdefinierte Implementierung) verwenden, um strukturierte Inhalte für Ihre Anwendungen bereitzustellen.

## Headless CMS {#headless-cms}

Ein Headless-Content-Management-System (CMS) ist:

* &quot;*Ein Headless-Content-Management-System oder ein kopless-CMS ist ein Back-End-Content-Management-System (CMS), das von Grund auf als Content-Repository aufgebaut wurde, das Inhalte über eine API für die Anzeige auf einem beliebigen Gerät zugänglich macht.*

   *Der Begriff &quot;Kopflos&quot;stammt aus dem Konzept, den &quot;Kopf&quot; (das Front-End, d.h. die Website) vom &quot;Körper&quot; (das Back-End, d.h. das Content-Repository) abzuschneiden.*&quot;

   Siehe [Wikipedia](https://en.wikipedia.org/wiki/Headless_content_management_system).

Was das Authoring von Inhaltsfragmenten in AEM betrifft, bedeutet dies:

* Sie können Inhaltsfragmente verwenden, um Inhalte zu erstellen, die nicht hauptsächlich für die direkte Veröffentlichung (1:1) auf formatierten Seiten vorgesehen sind.

* Der Inhalt Ihrer Inhaltsfragmente wird vorab nach den Inhaltsfragmentmodellen strukturiert. Dadurch wird der Zugriff auf Ihre Anwendungen vereinfacht, wodurch Ihre Inhalte weiter verarbeitet werden.

>[!NOTE]
>
>Eine Einführung in die Headless-Entwicklung für AEM Sites als Cloud Service finden Sie unter [Headless und AEM](/help/implementing/developing/headless/introduction.md).

## GraphQL - Eine Übersicht {#graphql-overview}

GraphQL ist:

* &quot;*...eine Abfrage für APIs und eine Laufzeit zur Erfüllung dieser Abfragen mit Ihren vorhandenen Daten. GraphQL bietet eine vollständige und verständliche Beschreibung der Daten in Ihrer API, gibt Kunden die Möglichkeit, nach genau dem zu fragen, was sie brauchen und nichts mehr, erleichtert die Entwicklung von APIs im Laufe der Zeit und ermöglicht leistungsstarke Entwicklerwerkzeuge.*&quot;

   Siehe [GraphQL.org](https://graphql.org)

* &quot;*...eine offene Spezifikation für eine flexible API-Ebene. Mit GraphQL können Sie Ihre bestehenden Backends schneller als je zuvor erstellen....*&quot;.

   Siehe [GraphQL](https://www.graphql.com) entdecken. &quot;*Explore GraphQL wird vom Apollo-Team verwaltet. Unser Ziel ist es, Entwicklern und technischen Führern weltweit alle Werkzeuge zur Verfügung zu stellen, die sie benötigen, um GraphQL.* zu verstehen und zu übernehmen.&quot;

Mit der [AEM GraphQL API](#aem-graphql-api) können Sie (komplexe) Abfragen an Ihren [Inhaltsfragmenten](/help/assets/content-fragments/content-fragments.md) durchführen. wobei jede Abfrage einem bestimmten Modelltyp entspricht. Die zurückgegebenen Inhalte können dann von Ihren Anwendungen verwendet werden.

### GraphQL Terminology {#graphql-terminology}

GraphQL verwendet Folgendes:

* **[Abfragen](https://graphql.org/learn/queries/)**

* **[Schemas und Typen](https://graphql.org/learn/schema/)**  - unter Verwendung dieser, GraphQL präsentiert die Typen und Vorgänge, die für die GraphQL für AEM Implementierung zulässig sind.

* **[Felder](https://graphql.org/learn/queries/#fields)**

* **GraphQL-Endpunkt**  - der Pfad in AEM, der auf GraphQL-Abfragen reagiert und Zugriff auf die GraphQL-Schema bietet.

Umfassende Details wie die [Best Practices](https://graphql.org/learn/best-practices/) finden Sie in der [(GraphQL.org) Einführung zu GraphQL](https://graphql.org/learn/).

### GraphQL Abfrage Types {#graphql-query-types}

Mit GraphQL können Sie Abfragen für Folgendes durchführen:

* **Einzelner Eintrag**

* **[Liste der Einträge](https://graphql.org/learn/schema/#lists-and-non-null)**

## AEM GraphQL API {#aem-graphql-api}

Für [Adobe Experience as a Cloud Experience wurde eine benutzerdefinierte Implementierung der Standard-GraphQL-API](/help/assets/content-fragments/graphql-api-content-fragments.md) implementiert.

Die Implementierung der AEM GraphQL API basiert auf den Java-Bibliotheken [GraphQL](https://graphql.org/code/#java).

## Inhaltsfragmente zur Verwendung mit der AEM GraphQL API {#content-fragments-use-with-aem-graphql-api}

[Inhaltsfragmente ](#content-fragments) können als Grundlage für GraphQL für AEM Abfragen wie:

* Sie ermöglichen Ihnen das Entwerfen, Erstellen, Kuratieren und Veröffentlichen seitenunabhängiger Inhalte.
* Die [Inhaltsfragmentmodelle](#content-fragments-models) stellen die erforderliche Struktur mithilfe definierter Datentypen bereit.
* Der [Fragmentverweis](#fragment-references), der beim Definieren eines Modells verfügbar ist, kann zum Definieren zusätzlicher Strukturebenen verwendet werden.

![Inhaltsfragmente zur Verwendung mit ](assets/cfm-nested-01.png "GraphQLContent-Fragmenten zur Verwendung mit GraphQL")

### Inhaltsfragmente {#content-fragments}

Inhaltsfragmente:

* Enthält strukturierten Inhalt.

* Sie basieren auf einem [Inhaltsfragmentmodell](#content-fragments-models), das die Struktur für das resultierende Fragment vordefiniert.

### Inhaltsfragmentmodelle {#content-fragments-models}

Diese [Inhaltsfragmentmodelle](/help/assets/content-fragments/content-fragments-models.md):

* Geben Sie die für GraphQL erforderlichen Datentypen und Felder ein. Sie stellen sicher, dass Ihre Anwendung nur anfordert, was möglich ist, und dass sie das Erwartet erhält.

* Der Datentyp **[Fragmentverweise](#fragment-references)** kann in Ihrem Modell verwendet werden, um auf ein anderes Inhaltsfragment zu verweisen und so zusätzliche Strukturebenen einzuführen.

### Fragmentverweise {#fragment-references}

Der **[Fragmentverweis](/help/assets/content-fragments/content-fragments-models.md#fragment-reference-nested-fragments)**:

* Ist in Verbindung mit GraphQL von besonderem Interesse.

* Ein bestimmter Datentyp, der beim Definieren eines Inhaltsfragmentmodells verwendet werden kann.

* Verweist auf ein anderes Fragment, das von einem bestimmten Inhaltsfragmentmodell abhängig ist.

* Ermöglicht Ihnen das Abrufen strukturierter Daten.

   * Wenn als **multifeed** definiert, können mehrere Subfragmente vom primären Fragment referenziert (abgerufen) werden.

### JSON-Vorschau {#json-preview}

Um beim Entwerfen und Entwickeln Ihrer Inhaltsfragmentmodelle zu helfen, können Sie die Vorschau [JSON-Ausgabe](/help/assets/content-fragments/content-fragments-json-preview.md) durchführen.

## Verwendung von GraphQL mit AEM - Beispielinhalt und Abfragen {#learn-graphql-with-aem-sample-content-queries}

Eine Einführung zur Verwendung der AEM GraphQL API finden Sie unter [Verwendung von GraphQL mit AEM - Beispielinhalt und Abfragen](/help/assets/content-fragments/content-fragments-graphql-samples.md).