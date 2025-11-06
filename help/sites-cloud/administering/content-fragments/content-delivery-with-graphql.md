---
title: Headless-Bereitstellung von Inhalten mithilfe von Inhaltsfragmenten mit GraphQL
description: Lernen Sie die grundlegenden Konzepte zur Realisierung eines AEM Headless CMS unter Verwendung von Inhaltsfragmenten mit GraphQL für die Bereitstellung von Headless-Inhalten kennen.
feature: Content Fragments, GraphQL API
role: Developer
exl-id: 3aa7073a-6c6b-47b7-99d8-bba2d9a00af5
solution: Experience Manager Sites
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '736'
ht-degree: 100%

---

# Headless-Bereitstellung von Inhalten mithilfe von Inhaltsfragmenten mit GraphQL {#headless-content-delivery-using-content-fragments-with-graphQL}

Mit Inhaltsfragmenten und der GraphQL-API können Sie Adobe Experience Manager (AEM) as a Cloud Service als Headless-Content-Management-System (CMS) verwenden.

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
>* [AEM Commerce nutzt Daten von einer Commerce-Plattform über GraphQL](/help/commerce-cloud/cif-storefront/integrating/magento.md).
>* [AEM-Inhaltsfragmente verwenden die AEM-GraphQL-API (eine auf Standard-GraphQL basierende benutzerdefinierte Implementierung), um strukturierte Inhalte für die Verwendung in Ihren Anwendungen bereitzustellen](/help/headless/graphql-api/content-fragments.md).

## Headless-CMS {#headless-cms}

Ein Headless-Content-Management-System (CMS) ist ein Back-End-Content-Management-System, das von Grund auf als Content-Repository erstellt wurde und Inhalte über eine API für die Anzeige auf jedem Gerät zugänglich macht.

In Bezug auf das Erstellen von Inhaltsfragmenten in AEM bedeutet dies Folgendes:

* Sie können Inhaltsfragmente verwenden, um Inhalte zu erstellen, die nicht primär für die direkte Veröffentlichung (1:1) auf formatierten Seiten vorgesehen sind.

* Der Inhalt Ihrer Inhaltsfragmente wird in einer vorgegebenen Art und Weise strukturiert – entsprechend den Inhaltsfragmentmodellen. Dies vereinfacht den Zugriff für Ihre Anwendungen, die Ihre Inhalte dann weiterverarbeiten.

## Ein Übersicht über GraphQL {#graphql-overview}

GraphQL ist:

* „*... eine Abfragesprache für APIs und eine Laufzeitumgebung zur Erfüllung dieser Abfragen mit Ihren vorhandenen Daten.*“

  Weitere Informationen finden Sie unter [GraphQL.org](https://graphql.org)

Mit der [AEM-GraphQL-API](#aem-graphql-api) können Sie (komplexe) Abfragen für Ihre [Inhaltsfragmente](/help/sites-cloud/administering/content-fragments/overview.md) durchführen, wobei jede Abfrage einem bestimmten Modelltyp entspricht. Die zurückgegebenen Inhalte können dann von Ihren Programmen verwendet werden.

## AEM-GraphQL-API {#aem-graphql-api}

Für Adobe Experience as a Cloud Service wurde eine benutzerdefinierte Implementierung der Standard-GraphQL-API entwickelt. Weitere Informationen finden Sie unter [AEM GraphQL-API zur Verwendung mit Inhaltsfragmenten](/help/headless/graphql-api/content-fragments.md).

Die Implementierung der AEM-GraphQL-API basiert auf den [GraphQL-Java-Bibliotheken](https://graphql.org/code/#java).

## Inhaltsfragmente zur Verwendung mit der AEM-GraphQL-API {#content-fragments-use-with-aem-graphql-api}

[Inhaltsfragmente](#content-fragments) können als Grundlage für GraphQL-Abfragen für AEM verwendet werden:

* Sie ermöglichen Ihnen das Entwerfen, Erstellen, Kuratieren und Veröffentlichen seitenunabhängiger Inhalte.
* Die [Inhaltsfragmentmodelle](#content-fragments-models) stellen mithilfe definierter Datentypen die erforderliche Struktur bereit.
* Die [Fragmentreferenz](#fragment-references), die beim Definieren eines Modells verfügbar ist, kann zum Definieren zusätzlicher Strukturebenen verwendet werden.

![Inhaltsfragmente zur Verwendung mit GraphQL](assets/cf-contentdelivery-cf-use-with-graphql.png "Inhaltsfragmente zur Verwendung mit GraphQL")

### Inhaltsfragmente {#content-fragments}

Inhaltsfragmente:

* enthalten strukturierten Inhalt,

* basieren auf einem [Inhaltsfragmentmodell](#content-fragments-models), das die Struktur für das daraus entstehende Fragment vordefiniert.

### Inhaltsfragmentmodelle {#content-fragments-models}

Diese [Inhaltsfragmentmodelle](/help/sites-cloud/administering/content-fragments/content-fragment-models.md):

* werden verwendet, um die [Schemata](https://graphql.org/learn/schema/) zu erzeugen, sobald sie **aktiviert** sind.

* stellen die für GraphQL erforderlichen Datentypen und Felder bereit. Sie stellen sicher, dass Ihr Programm nur das anfordert, was möglich ist, und das erhält, was erwartet wird.

* Der Datentyp **[Fragmentreferenzen](#fragment-references)** kann in Ihrem Modell verwendet werden, um auf ein anderes Inhaltsfragment zu verweisen und so zusätzliche Strukturebenen einzuführen.

### Fragmentreferenzen {#fragment-references}

Die **[Fragmentreferenz](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#fragment-reference-nested-fragments)**:

* ist vor allem in Verbindung mit GraphQL von Interesse,

* ist ein spezifischer Datentyp, der bei der Definition eines Inhaltsfragmentmodells verwendet werden kann,

* verweist auf ein anderes Fragment, abhängig von einem bestimmten Inhaltsfragmentmodell,

* ermöglicht Ihnen das Abrufen strukturierter Daten.

   * Wenn als **multifeed** definiert, können mehrere Unterfragmente vom primären Fragment referenziert (abgerufen) werden.

## Analysieren der Struktur von Inhaltsfragmenten {#analyzing-content-fragments-structure}

Um die Analyse zu unterstützen, bietet AEM mehrere Methoden, um die Struktur Ihrer Fragmente über den [Inhaltsfragment-Editor](/help/sites-cloud/administering/content-fragments/authoring.md) anzuzeigen.

Weitere Informationen finden Sie unter [Analysieren der Struktur von Inhaltsfragmenten](/help/sites-cloud/administering/content-fragments/analysis.md):

* [Baumstruktur](/help/sites-cloud/administering/content-fragments/analysis.md#structure-tree)

## Verwenden von GraphQL mit AEM – Beispielinhalt und Abfragen {#learn-graphql-with-aem-sample-content-queries}

Eine Einführung in die Verwendung der AEM GraphQL-API finden Sie unter [Verwendung von GraphQL mit AEM – Beispielinhalt und Abfragen](/help/headless/graphql-api/sample-queries.md).

## Tutorial – Erste Schritte mit AEM Headless und GraphQL

Suchen Sie nach einem praktischen Tutorial? Lesen Sie das umfassende Tutorial [Erste Schritte mit AEM Headless und GraphQL](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html?lang=de), in dem veranschaulicht wird, wie Inhalte mithilfe der GraphQL-APIs von AEM erstellt und verfügbar gemacht und von einem externen Programm in einem Headless CMS-Szenario verwendet werden.
