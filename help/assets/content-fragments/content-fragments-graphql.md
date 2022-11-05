---
title: Headless-Bereitstellung von Inhalten mithilfe von Inhaltsfragmenten mit GraphQL (Assets - Inhaltsfragmente)
description: Lernen Sie die grundlegenden Konzepte zur Realisierung eines AEM Headless CMS unter Verwendung von Inhaltsfragmenten mit GraphQL für die Bereitstellung von Headless-Inhalten kennen.
feature: Content Fragments, GraphQL API
exl-id: 4a3b030d-ed59-4920-bf94-e00a45f85b51
source-git-commit: 944665bc7cac1f00811187a508a18800c3d73f2a
workflow-type: tm+mt
source-wordcount: '734'
ht-degree: 95%

---

# Headless-Bereitstellung von Inhalten mithilfe von Inhaltsfragmenten mit GraphQL {#headless-content-delivery-using-content-fragments-with-graphQL}

Mit Inhaltsfragmenten und der GraphQL-API können Sie Adobe Experience Manager (AEM) as a Cloud Service als Headless-Content Management System (CMS) verwenden.

Dies wird durch die Verwendung von Inhaltsfragmenten in Verbindung mit der AEM GraphQL-API (eine benutzerdefinierte Implementierung, die auf Standard-GraphQL basiert) erreicht, um strukturierte Inhalte für die Verwendung in Ihren Programmen ohne Probleme „headless“ bereitzustellen. Durch die Möglichkeit, eine einzelne API-Abfrage anzupassen, können Sie den spezifischen Inhalt, den Sie (als Antwort auf die einzelne API-Abfrage) rendern möchten/benötigen, abrufen und bereitstellen.

>[!NOTE]
>
>Siehe auch:
>
>* [Was ist Headless?](/help/headless/what-is-headless.md) für eine Einführung in Headless-Konzepte und -Terminologie.
>
>* Eine Einführung in die Headless-Entwicklung für AEM Sites as a Cloud Service finden Sie unter [Headless und AEM](/help/headless/introduction.md).


>[!NOTE]
>
>GraphQL wird derzeit in zwei (separaten) Szenarien in Adobe Experience Manager (AEM) as a Cloud Service verwendet:
>
>* [AEM Commerce nutzt Daten von einer Commerce-Plattform über GraphQL](/help/commerce-cloud/integrating/magento.md).
>* [AEM-Inhaltsfragmente stellen in Kombination mit der AEM-GraphQL-API (einer auf GraphQL basierenden benutzerdefinierten Implementierung) strukturierte Inhalte für die Verwendung in Ihren Programmen](/help/headless/graphql-api/content-fragments.md) bereit.


## Headless-CMS {#headless-cms}

Ein Headless Content Management System (CMS) ist ein reines Back-End-Content-Management-System, das explizit als Inhalts-Repository konzipiert und entwickelt wurde, das Inhalte über eine API für die Anzeige auf jedem Gerät zugänglich macht.

In Bezug auf das Erstellen von Inhaltsfragmenten in AEM bedeutet dies Folgendes:

* Sie können Inhaltsfragmente verwenden, um Inhalte zu erstellen, die nicht primär für die direkte Veröffentlichung (1:1) auf formatierten Seiten vorgesehen sind.

* Der Inhalt Ihrer Inhaltsfragmente wird in einer vorgegebenen Art und Weise strukturiert – entsprechend den Inhaltsfragmentmodellen. Dies vereinfacht den Zugriff für Ihre Programme, die Ihre Inhalte weiterverarbeiten werden.

## Ein Übersicht über GraphQL {#graphql-overview}

GraphQL ist:

* „*... eine Abfragesprache für APIs und eine Laufzeitumgebung zur Erfüllung dieser Abfragen mit Ihren vorhandenen Daten.*“

   Weitere Informationen finden Sie unter [GraphQL.org](https://graphql.org)

Mit der [AEM-GraphQL-API](#aem-graphql-api) können Sie (komplexe) Abfragen für Ihre [Inhaltsfragmente](/help/assets/content-fragments/content-fragments.md) durchführen, wobei jede Abfrage einem bestimmten Modelltyp entspricht. Die zurückgegebenen Inhalte können dann von Ihren Programmen verwendet werden.

## AEM-GraphQL-API {#aem-graphql-api}

Für Adobe Experience as a Cloud Service wurde eine benutzerdefinierte Implementierung der Standard-GraphQL-API entwickelt. Weitere Informationen finden Sie unter [AEM GraphQL-API zur Verwendung mit Inhaltsfragmenten](/help/headless/graphql-api/content-fragments.md).

Die Implementierung der AEM-GraphQL-API basiert auf den [GraphQL-Java-Bibliotheken](https://graphql.org/code/#java).

## Inhaltsfragmente zur Verwendung mit der AEM-GraphQL-API {#content-fragments-use-with-aem-graphql-api}

[Inhaltsfragmente](#content-fragments) können als Grundlage für GraphQL-Abfragen für AEM verwendet werden:

* Sie ermöglichen Ihnen das Entwerfen, Erstellen, Kuratieren und Veröffentlichen seitenunabhängiger Inhalte.
* Die [Inhaltsfragmentmodelle](#content-fragments-models) stellen mithilfe definierter Datentypen die erforderliche Struktur bereit.
* Die [Fragmentreferenz](#fragment-references), die beim Definieren eines Modells verfügbar ist, kann zum Definieren zusätzlicher Strukturebenen verwendet werden.

![Inhaltsfragmente zur Verwendung mit GraphQL](assets/cfm-nested-01.png "Inhaltsfragmente zur Verwendung mit GraphQL")

### Inhaltsfragmente {#content-fragments}

Inhaltsfragmente:

* enthalten strukturierten Inhalt,

* basieren auf einem [Inhaltsfragmentmodell](#content-fragments-models), das die Struktur für das daraus entstehende Fragment vordefiniert.

### Inhaltsfragmentmodelle {#content-fragments-models}

Diese [Inhaltsfragmentmodelle](/help/assets/content-fragments/content-fragments-models.md):

* werden verwendet, um die [Schemata](https://graphql.org/learn/schema/) zu erzeugen, sobald sie **aktiviert** sind.

* stellen die für GraphQL erforderlichen Datentypen und Felder bereit. Sie stellen sicher, dass Ihr Programm nur das anfordert, was möglich ist, und das erhält, was erwartet wird.

* Der Datentyp **[Fragmentreferenzen](#fragment-references)** kann in Ihrem Modell verwendet werden, um auf ein anderes Inhaltsfragment zu verweisen und so zusätzliche Strukturebenen einzuführen.

### Fragmentreferenzen {#fragment-references}

Die **[Fragmentreferenz](/help/assets/content-fragments/content-fragments-models.md#fragment-reference-nested-fragments)**:

* ist vor allem in Verbindung mit GraphQL von Interesse,

* ist ein spezifischer Datentyp, der bei der Definition eines Inhaltsfragmentmodells verwendet werden kann,

* verweist auf ein anderes Fragment, abhängig von einem bestimmten Inhaltsfragmentmodell,

* ermöglicht Ihnen das Abrufen strukturierter Daten.

   * Wenn als **multifeed** definiert, können mehrere Unterfragmente vom primären Fragment referenziert (abgerufen) werden.

### JSON-Vorschau {#json-preview}

Als Hilfe beim Entwerfen und Entwickeln Ihrer Inhaltsfragmentmodelle können Sie eine Vorschau der [JSON-Ausgabe](/help/assets/content-fragments/content-fragments-json-preview.md) anzeigen.

## Verwenden von GraphQL mit AEM – Beispielinhalt und Abfragen {#learn-graphql-with-aem-sample-content-queries}

Eine Einführung in die Verwendung der AEM GraphQL-API finden Sie unter [Verwendung von GraphQL mit AEM – Beispielinhalt und Abfragen](/help/headless/graphql-api/sample-queries.md).

## Tutorial – Erste Schritte mit AEM Headless und GraphQL

Suchen Sie nach einem praktischen Tutorial? Lesen Sie das umfassende Tutorial [Erste Schritte mit AEM Headless und GraphQL](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html?lang=de), in dem veranschaulicht wird, wie Inhalte mithilfe der GraphQL-APIs von AEM erstellt und verfügbar gemacht und von einem externen Programm in einem Headless CMS-Szenario verwendet werden.
