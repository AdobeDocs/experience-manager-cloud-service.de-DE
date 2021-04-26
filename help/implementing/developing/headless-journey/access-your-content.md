---
title: Zugriff auf Ihre Inhalte über AEM Versand-APIs
description: Erfahren Sie in diesem Teil der AEM Headless Developer-Journey, wie Sie mit GraphQL-Abfragen auf Ihre Inhaltsfragmente zugreifen können.
hide: true
hidefromtoc: true
index: false
translation-type: tm+mt
source-git-commit: 9fb18dbe60121f46dba1e11d4133e5264a6d538d
workflow-type: tm+mt
source-wordcount: '764'
ht-degree: 52%

---


# Zugriff auf Ihre Inhalte über AEM Versand-APIs {#access-your-content}

>[!CAUTION]
>
>ARBEITEN IN FORTSCHRITTEN - Die Schaffung dieses Dokuments ist im Gange und sollte nicht als vollständig oder endgültig betrachtet werden und auch nicht für Produktionszwecke verwendet werden.

In diesem Teil der [AEM Headless Developer-Journey lernen Sie, wie Sie mit den GraphQL-Abfragen auf den Inhalt Ihrer Inhaltsfragmente zugreifen können.](overview.md)

## Die Meldung bisher {#story-so-far}

Im vorherigen Dokument der AEM Journey [So modellieren Sie Ihren Inhalt](model-your-content.md), haben Sie die Grundlagen der Datenmodellierung in AEM gelernt und sollten jetzt:

* Machen Sie sich mit wichtigen Planungshinweisen zum Entwerfen Ihrer Inhalte vertraut.
* Machen Sie sich mit den Schritten vertraut, die Sie je nach den Anforderungen auf der Integrationsstufe durchführen möchten.
* Richten Sie die erforderlichen Werkzeuge und AEM Konfigurationen ein.
* Machen Sie sich mit Best Practices vertraut, um die Journey ohne Kopf zu glätten, die Inhaltserstellung effizient zu gestalten und sicherzustellen, dass Inhalte schnell bereitgestellt werden.

Dieser Artikel baut auf diesen Grundlagen auf, damit Sie verstehen, wie Sie über die API auf Ihre vorhandenen Kopflosen-Inhalte in AEM zugreifen können.

* **Audience**: Anfänger
* **Zielsetzung**: Erfahren Sie, wie Sie mithilfe AEM GraphQL-Abfragen auf den Inhalt Ihrer Inhaltsfragmente zugreifen können:
   * GraphQL einführen.
   * Einführung AEM GraphQL API.
   * Tauchen Sie ein in die Details der AEM GraphQL API.
   * Sehen Sie sich einige Abfragen an, um zu sehen, wie die Dinge in der Praxis funktionieren.

Mit Adobe Experience Manager (AEM) als Cloud Service können Sie Inhaltsfragmente zusammen mit der AEM GraphQL-API verwenden, um ohne Probleme strukturierte Inhalte für Ihre Anwendungen bereitzustellen. Durch die Möglichkeit, eine einzelne API-Abfrage anzupassen, können Sie den spezifischen Inhalt, den Sie rendern möchten/benötigen (als Antwort auf die einzelne API-Abfrage), abrufen und bereitstellen.

>[!NOTE]
>AEM GraphQL API ist eine benutzerdefinierte Implementierung, die auf dem Standard GraphQL basiert.

## GraphQL - Eine Einführung {#graphql-introduction}

GraphQL ist:

* „*... eine Abfragesprache für APIs und eine Laufzeitumgebung zur Erfüllung dieser Abfragen mit Ihren vorhandenen Daten.*“

   Siehe *GraphQL*.

### GraphQL - Typen {#graphql-types}

### GraphQL - Schemas {#graphql-schemas}

### GraphQL - Abfragen {#graphql-queries}

## AEM und GraphQL {#aem-graphql}

GraphQL wird an verschiedenen Stellen in AEM verwendet:

* Commerce
   * Platzhalter
* Inhaltsfragmente
   * Für diesen Anwendungsfall wurde eine benutzerdefinierte API entwickelt.
   * Dies ist die AEM GraphQL API.

## AEM GraphQL-API {#aem-graphql-api}

Für Adobe Experience as a Cloud Service wurde eine benutzerdefinierte Implementierung der Standard-GraphQL-API entwickelt.

Mit der AEM GraphQL-API können Sie (komplexe) Abfragen für Ihre Inhaltsfragmente durchführen, wobei jede Abfrage einem bestimmten Modelltyp entspricht. Die zurückgegebenen Inhalte können dann von Ihren Programmen verwendet werden.

>[!NOTE]
>
>Die Implementierung der AEM GraphQL-API basiert auf den GraphQL-Java-Bibliotheken.

### AEM GraphQL API und Inhaltsfragmente {#aem-graphql-content-fragments}

## Inhaltsfragmente zur Verwendung mit der AEM GraphQL-API {#content-fragments-use-with-aem-graphql-api}

Inhaltsfragmente können als Grundlage für GraphQL-Abfragen für AEM verwendet werden:

* Sie ermöglichen Ihnen das Entwerfen, Erstellen, Kuratieren und Veröffentlichen seitenunabhängiger Inhalte.
* Die Inhaltsfragmentmodelle stellen mithilfe definierter Datentypen die erforderliche Struktur bereit.
* Die Fragmentreferenz, die beim Definieren eines Modells verfügbar ist, kann zum Definieren zusätzlicher Strukturebenen verwendet werden.

### Inhaltsfragmente {#content-fragments}

Inhaltsfragmente:

* enthalten strukturierten Inhalt,

* basieren auf einem Inhaltsfragmentmodell, das die Struktur für das daraus entstehende Fragment vordefiniert.

### Inhaltsfragmentmodelle {#content-fragments-models}

Diese Inhaltsfragmentmodelle:

* werden verwendet, um die Schemas zu erzeugen, sobald sie **aktiviert** sind.

* stellen die für GraphQL erforderlichen Datentypen und Felder bereit. Sie stellen sicher, dass Ihr Programm nur das anfordert, was möglich ist, und das erhält, was erwartet wird.

* Der Datentyp **Fragmentreferenzen** kann in Ihrem Modell verwendet werden, um auf ein anderes Inhaltsfragment zu verweisen und so zusätzliche Strukturebenen einzuführen.

### Fragmentreferenzen {#fragment-references}

Die **Fragmentreferenz**:

* ist vor allem in Verbindung mit GraphQL von Interesse,

* ist ein spezifischer Datentyp, der bei der Definition eines Inhaltsfragmentmodells verwendet werden kann,

* verweist auf ein anderes Fragment, abhängig von einem bestimmten Inhaltsfragmentmodell,

* ermöglicht Ihnen das Abrufen strukturierter Daten.

   * Wenn als **multifeed** definiert, können mehrere Unterfragmente vom primären Fragment referenziert (abgerufen) werden.

### JSON-Vorschau {#json-preview}

Als Hilfe beim Entwerfen und Entwickeln Ihrer Inhaltsfragmentmodelle können Sie eine Vorschau der [JSON-Ausgabe](/help/assets/content-fragments/content-fragments-json-preview.md) anzeigen.

## Wie geht es weiter {#whats-next}

[Erfahren Sie, wie Sie mit der REST-API auf den Inhalt Ihrer Inhaltsfragmente](/help/implementing/developing/headless-journey/update-your-content.md) zugreifen und diese aktualisieren können.

## Zusätzliche Ressourcen {#additional-resources}

* [Erste Schritte mit AEMHeadless](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html?lang=de) - Eine kurze Videoschulung mit einem Überblick über die Verwendung AEM kopflosen Funktionen, einschließlich Datenmodellierung und GraphQL
* [GraphQL.org](https://graphql.org)
   * [Schemas](https://graphql.org/learn/Schema/)
   * [GraphQL Java-Bibliotheken](https://graphql.org/code/#java)
* [AEM GraphQL-API zur Verwendung mit Inhaltsfragmenten](/help/assets/content-fragments/graphql-api-content-fragments.md)
   * [Verwendung von GraphQL mit AEM – Beispielinhalt und Abfragen](/help/assets/content-fragments/content-fragments-graphql-samples.md)
   * [Authentifizierung für AEM GraphQL-Remote-Abfragen in Inhaltsfragmenten](/help/assets/content-fragments/graphql-authentication-content-fragments.md)
* [Arbeiten mit Inhaltsfragmenten](/help/assets/content-fragments/content-fragments.md)
   * [Inhaltsfragmentmodelle](/help/assets/content-fragments/content-fragments-models.md)
   * [JSON-Ausgabe](/help/assets/content-fragments/content-fragments-json-preview.md)
