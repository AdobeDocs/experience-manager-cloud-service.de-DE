---
title: Zugriff auf Ihre Inhalte über AEM Bereitstellungs-APIs
description: In diesem Teil der Journey für Entwickler ohne AEM Headless erfahren Sie, wie Sie mit GraphQL-Abfragen auf Ihre Inhaltsfragmente zugreifen können.
hide: true
hidefromtoc: true
index: false
exl-id: 5ef557ff-e299-4910-bf8c-81c5154ea03f
source-git-commit: 9e06419f25800199dea92b161bc393e6e9670697
workflow-type: tm+mt
source-wordcount: '1367'
ht-degree: 18%

---

# Zugriff auf Ihre Inhalte über AEM Bereitstellungs-APIs {#access-your-content}

>[!CAUTION]
>
>OUTDATED - Dieser Inhaltsentwurf wurde durch die neue [Headless-Entwickler-Journey-Dokumentation ersetzt.](/help/journey-headless/developer/overview.md)

In diesem Teil der [AEM Headless-Entwickler-Journey,](overview.md) erfahren Sie, wie Sie mit GraphQL-Abfragen auf den Inhalt Ihrer Inhaltsfragmente zugreifen und ihn an Ihre App weiterleiten können (Headless-Bereitstellung).

## Die Geschichte bisher {#story-so-far}

Im vorherigen Dokument der AEM Headless-Journey [So modellieren Sie Ihre Inhalte](model-your-content.md) haben Sie die Grundlagen der Inhaltsmodellierung in AEM gelernt. Daher sollten Sie jetzt verstehen, wie Sie Ihre Inhaltsstruktur modellieren, und dann diese Struktur mithilfe von AEM Inhaltsfragmentmodellen und Inhaltsfragmenten realisieren:

* Erkennen Sie Konzepte und Terminologie zur Inhaltsmodellierung.
* Erfahren Sie, warum eine Inhaltsmodellierung für die Bereitstellung Headless-Inhalts erforderlich ist.
* Erfahren Sie, wie Sie diese Struktur mithilfe von AEM Inhaltsfragmentmodellen (und Erstellern von Inhalten mit Inhaltsfragmenten) realisieren.
* Verstehen Sie, wie Sie Ihren Inhalt modellieren können. Grundprinzipien mit Grundproben.

Dieser Artikel baut auf diesen Grundlagen auf, sodass Sie verstehen, wie Sie mit der GraphQL-API auf Ihre vorhandenen Headless-Inhalte in AEM zugreifen können.

* **Zielgruppe**: Anfänger
* **Zielsetzung**: Erfahren Sie, wie Sie mithilfe AEM GraphQL-Abfragen auf den Inhalt Ihrer Inhaltsfragmente zugreifen können:
   * Einführung in GraphQL und die AEM GraphQL-API.
   * Informieren Sie sich über die Details der AEM GraphQL-API.
   * Sehen Sie sich einige Beispielabfragen an, um zu sehen, wie Dinge in der Praxis funktionieren.

## Sie möchten also auf Ihre Inhalte zugreifen? {#so-youd-like-to-access-your-content}

Also...Sie haben all diesen Inhalt, sauber strukturiert (in Inhaltsfragmenten) und warten nur darauf, Ihre neue App mit Feeds zu versehen. Frage ist: Wie kommt man dorthin?

Sie benötigen eine Möglichkeit, bestimmte Inhalte gezielt anzusprechen, auszuwählen, was Sie benötigen, und diese zur weiteren Verarbeitung an Ihre App zurückzugeben.

Mit Adobe Experience Manager (AEM) als Cloud Service können Sie mithilfe der AEM GraphQL-API selektiv auf Ihre Inhaltsfragmente zugreifen, um nur die benötigten Inhalte zurückzugeben. Dies bedeutet, dass Sie die Headless-Bereitstellung von strukturierten Inhalten zur Verwendung in Ihren Anwendungen realisieren können.

>[!NOTE]
>
>AEM GraphQL-API ist eine benutzerdefinierte Implementierung, die auf der standardmäßigen GraphQL-API-Spezifikation basiert.

## GraphQL - Eine Einführung {#graphql-introduction}

GraphQL ist eine Open-Source-Spezifikation, die Folgendes bietet:

* Abfragesprache, mit der Sie bestimmte Inhalte aus strukturierten Objekten auswählen können.
* eine Laufzeit, um diese Abfragen mit Ihrem strukturierten Inhalt zu erfüllen.

GraphQL ist eine *stark* eingegebene API. Das bedeutet, dass *alle*-Inhalte klar strukturiert und nach Typ organisiert sein müssen, sodass GraphQL *versteht*, was aufgerufen werden und wie. Die Datenfelder werden in GraphQL-Schemata definiert, die die Struktur Ihrer Inhaltsobjekte definieren.

GraphQL-Endpunkte geben dann die Pfade an, die auf die GraphQL-Abfragen reagieren.

Das bedeutet, dass Ihre App genau, zuverlässig und effizient den benötigten Inhalt auswählen kann - genau das, was Sie bei AEM benötigen.

>[!NOTE]
>
>Siehe *GraphQL*.org und *GraphQL*.com.

<!--
## AEM and GraphQL {#aem-graphql}

GraphQL is used in various locations in AEM; for example:

* Content Fragments
  * A customized API has been developed for this use-case (Headless Delivery to your app).
    * This is the AEM GraphQL API.
* Commerce
  * AEM Commerce consumes data from a Commerce platform via GraphQL.
  * There are GraphQL integrations between AEM and various third-party commerce solutions, used with the extension hooks provided by the CIF Core Components.
    * This does not use the AEM GraphQL API.

>[!NOTE]
>
>This step of the Headless Journey is only concerned with the AEM GraphQL API and Content Fragments.
-->

## AEM GraphQL-API {#aem-graphql-api}

Die AEM GraphQL-API ist eine angepasste Version, die auf der standardmäßigen GraphQL-API-Spezifikation basiert und speziell so konfiguriert wurde, dass Sie (komplexe) Abfragen Ihrer Inhaltsfragmente durchführen können.

Inhaltsfragmente werden verwendet, da der Inhalt nach Inhaltsfragmentmodellen strukturiert ist. Dies erfüllt eine Grundanforderung von GraphQL.

* Ein Inhaltsfragmentmodell besteht aus einem oder mehreren Feldern.
   * Jedes Feld wird anhand eines Datentyps definiert.
* Inhaltsfragmentmodelle werden verwendet, um die entsprechenden GraphQL-Schemas AEM.

Um tatsächlich auf GraphQL für AEM (und den Inhalt) zuzugreifen, wird ein Endpunkt verwendet, um den Zugriffspfad bereitzustellen.

Der über die AEM GraphQL-API zurückgegebene Inhalt kann dann von Ihren Anwendungen verwendet werden.

Um Ihnen beim direkten Eingeben und Testen von Abfragen zu helfen, ist auch eine Implementierung der standardmäßigen GraphiQL-Schnittstelle für die Verwendung mit AEM GraphQL verfügbar (kann mit AEM installiert werden). Es bietet Funktionen wie Syntaxhervorhebung, automatische Vervollständigung und automatische Vorschläge sowie einen Verlauf und eine Online-Dokumentation.

>[!NOTE]
>
>Die Implementierung der AEM GraphQL-API basiert auf den GraphQL-Java-Bibliotheken.

<!--
### Use Cases for Author and Publish Environments {#use-cases-author-publish-environments}

The use cases for the AEM GraphQL API can depend on the type of AEM as a Cloud Service environment:

* Publish environment; used to: 
  * Query content for JS application (standard use-case)

* Author environment; used to: 
  * Query content for "content management purposes":
    * GraphQL in AEM as a Cloud Service is currently a read-only API.
    * The REST API can be used for CR(u)D operations.
-->

## Inhaltsfragmente zur Verwendung mit der AEM GraphQL-API {#content-fragments-use-with-aem-graphql-api}

Inhaltsfragmente können als Grundlage für GraphQL für AEM Schemas und Abfragen wie folgt verwendet werden:

* Sie ermöglichen es Ihnen, seitenunabhängige Inhalte zu entwerfen, zu erstellen, zu kuratieren und zu veröffentlichen, die ohne Probleme bereitgestellt werden können.
* Sie basieren auf einem Inhaltsfragmentmodell, das die Struktur für das daraus entstehende Fragment mithilfe einer Auswahl von Datentypen vordefiniert.
* Zusätzliche Strukturebenen können mit dem Fragment-Referenzdatentyp erreicht werden, der beim Definieren eines Modells verfügbar ist.

### Inhaltsfragmentmodelle {#content-fragments-models}

Diese Inhaltsfragmentmodelle:

* werden verwendet, um die Schemas zu erzeugen, sobald sie **aktiviert** sind.
* stellen die für GraphQL erforderlichen Datentypen und Felder bereit. Sie stellen sicher, dass Ihr Programm nur das anfordert, was möglich ist, und das erhält, was erwartet wird.
* Der Datentyp **Fragmentreferenzen** kann in Ihrem Modell verwendet werden, um auf ein anderes Inhaltsfragment zu verweisen und so zusätzliche Strukturebenen einzuführen.

### Fragmentreferenzen {#fragment-references}

Die **Fragmentreferenz**:

* Ist ein bestimmter Datentyp, der beim Definieren eines Inhaltsfragmentmodells verfügbar ist.
* verweist auf ein anderes Fragment, abhängig von einem bestimmten Inhaltsfragmentmodell,
* Ermöglicht das Erstellen und anschließende Abrufen strukturierter Daten.

   * Wenn als **multifeed** definiert, können mehrere Unterfragmente vom primären Fragment referenziert (abgerufen) werden.

### JSON-Vorschau {#json-preview}

Um Sie beim Entwerfen und Entwickeln Ihrer Inhaltsfragmentmodelle zu unterstützen, können Sie die JSON-Ausgabe im Inhaltsfragment-Editor in der Vorschau anzeigen.

![JSON-](assets/cfm-model-json-preview.png "Vorschau JSON-Vorschau")

<!--
## GraphQL Schema Generation from Content Fragments {#graphql-schema-generation-content-fragments}

GraphQL is a strongly typed API, which means that content must be clearly structured and organized by type. The GraphQL specification provides a series of guidelines on how to create a robust API for interrogating content on a certain instance. To do this, a client needs to fetch the Schema, which contains all the types necessary for a query. 

For Content Fragments, the GraphQL schemas (structure and types) are based on **Enabled** Content Fragment Models and their data types.

>[!CAUTION]
>
>All the GraphQL schemas (derived from Content Fragment Models that have been **Enabled**) are readable through the GraphQL endpoint.
>
>This means that you need to ensure that no sensitive content is available, to ensure that no sensitive data is exposed via GraphQL endpoints; for example, this includes information that could be present as field names in the model definition.

For example, if a user created a Content Fragment Model called `Article`, then AEM generates the object `article` that is of a type `ArticleModel`. The fields within this type correspond to the fields and data types defined in the model.

1. A Content Fragment Model:

   ![Content Fragment Model for use with GraphQL](assets/graphqlapi-cfmodel.png "Content Fragment Model for use with GraphQL")

1. The corresponding GraphQL schema (output from GraphiQL automatic documentation):
   ![GraphQL Schema based on Content Fragment Model](assets/graphqlapi-cfm-schema.png "GraphQL Schema based on Content Fragment Model")

   This shows that the generated type `ArticleModel` contains several [fields](#fields). 
   
   * Three of them have been controlled by the user: `author`, `main` and `referencearticle`.

   * The other fields were added automatically by AEM, and represent helpful methods to provide information about a certain Content Fragment; in this example, `_path`, `_metadata`, `_variations`. These [helper fields](#helper-fields) are marked with a preceding `_` to distinguish between what has been defined by the user and what has been auto-generated.

1. After a user creates a Content Fragment based on the Article model, it can then be interrogated through GraphQL. For examples, see the Sample Queries.md#graphql-sample-queries) (based on a sample Content Fragment structure for use with GraphQL.

In GraphQL for AEM, the schema is flexible. This means that it is auto-generated each and every time a Content Fragment Model is created, updated or deleted. The data schema caches are also refreshed when you update a Content Fragment Model.

The Sites GraphQL service listens (in the background) for any modifications made to a Content Fragment Model. When updates are detected, only that part of the schema is regenerated. This optimization saves time and provides stability.

So for example, if you:

1. Install a package containing `Content-Fragment-Model-1` and `Content-Fragment-Model-2`:
 
   1. GraphQL types for `Model-1` and `Model-2` will be generated.

1. Then modify `Content-Fragment-Model-2`:

   1. Only the `Model-2` GraphQL type will get updated.

   1. Whereas `Model-1` will remain the same. 

>[!NOTE]
>
>This is important to note in case you want to do bulk updates on Content Fragment Models through the REST api, or otherwise.

The schema is served through the same endpoint as the GraphQL queries, with the client handling the fact that the schema is called with the extension `GQLschema`. For example, performing a simple `GET` request on `/content/cq:graphql/global/endpoint.GQLschema` will result in the output of the schema with the Content-type: `text/x-graphql-schema;charset=iso-8859-1`.

### Schema Generation - Unpublished Models {#schema-generation-unpublished-models}

When Content Fragments are nested it can happen that a parent Content Fragment Model is published, but a referenced model is not.

>[!NOTE]
>
>The AEM UI prevents this happening, but if publishing is made programmatically, or with content packages, it can occur.

When this happens, AEM generates an *incomplete* Schema for the parent Content Fragment Model. This means that the Fragment Reference, which is dependent on the unpublished model, is removed from the schema.

## AEM GraphQL Endpoints {#aem-graphql-endpoints}

An endpoint is the path used to access GraphQL for AEM. Using this path you (or your app) can:

* access the GraphQL schemas,
* send your GraphQL queries,
* receive the responses (to your GraphQL queries).

AEM allows for:

* A global endpoint - available for use by all sites.
* Endpoints for specific Sites configurations - that you can configure (in the Configuration Browser), specific to a specified site/project.

## Permissions {#permissions}

The permissions are those required for accessing Assets.

## The AEM GraphiQL Interface {#aem-graphiql-interface}

To help you directly input, and test queries, an implementation of the standard GraphiQL interface is available for use with AEM GraphQL. This can be installed with AEM.

>[!NOTE]
>
>GraphiQL is bound the global endpoint (and does not work with other endpoints for specific Sites configurations).

It provides features such as syntax-highlighting, auto-complete, auto-suggest, together with a history and online documentation.

![GraphiQL Interface](assets/graphiql-interface.png "GraphiQL Interface")
-->

## Verwenden der AEM GraphQL-API {#actually-using-aem-graphiql}

### Ersteinrichtung {#initial-setup}

Bevor Sie mit Abfragen zu Ihrem Inhalt beginnen, müssen Sie Folgendes tun:

* Endpunkt aktivieren
   * Verwenden Sie Tools > Sites > GraphQL
   * [Aktivieren des GraphQL-Endpunkts](/help/assets/content-fragments/graphql-api-content-fragments.md#enabling-graphql-endpoint)

* Installieren Sie GraphiQL (falls erforderlich)
   * Als dediziertes Paket installiert
   * [AEM GraphiQL-Schnittstelle installieren](/help/assets/content-fragments/graphql-api-content-fragments.md#installing-graphiql-interface)

### Beispielstruktur {#sample-structure}

Um die AEM GraphQL-API in einer Abfrage zu verwenden, können wir die beiden sehr grundlegenden Strukturen des Inhaltsfragmentmodells verwenden:

* Unternehmen
   * Name - Text
   * CEO (Person) - Fragmentreferenz
   * Arbeitnehmer (Personen) - Fragmentverweis(e)
* Person
   * Name - Text
   * Vorname - Text

Wie Sie sehen können, verweisen die Felder CEO und Mitarbeiter auf die Personenfragmente.

Die Fragmentmodelle werden verwendet:

* beim Erstellen des Inhalts im Inhaltsfragment-Editor
* , um die von Ihnen abgefragten GraphQL-Schemas zu generieren.

### Testen Ihrer Abfragen {#where-to-test-your-queries}

Die Abfragen können in der Benutzeroberfläche von GraphiQL eingegeben werden, z. B. unter:

* `http://localhost:4502/content/graphiql.html `

![GraphiQL-Schnittstelle](assets/graphiql-interface.png "GraphiQL-Schnittstelle")

### Erste Schritte mit Abfragen {#getting-Started-with-queries}

Eine einfache Abfrage besteht darin, den Namen aller Einträge im Unternehmensschema zurückzugeben. Hier fordern Sie eine Liste aller Firmennamen an:

```xml
query {
  companyList {
    items {
      name
    }
  }
}
```

Eine etwas komplexere Abfrage besteht darin, alle Personen auszuwählen, die nicht den Namen &quot;Aufträge&quot;haben. Dadurch werden alle Personen nach Personen gefiltert, die nicht den Namen &quot;Jobs&quot;haben. Dies wird mit dem Operator EQUALS_NOT erreicht (es gibt viele weitere):

```xml
query {
  personList(filter: {
    name: {
      _expressions: [
        {
          value: "Jobs"
          _operator: EQUALS_NOT
        }
      ]
    }
  }) {
    items {
      name
      firstName
    }
  }
}
```

Sie können auch komplexere Abfragen erstellen. Abfrage beispielsweise für alle Unternehmen, die mindestens einen Mitarbeiter mit dem Namen &quot;Smith&quot;haben. Diese Abfrage zeigt die Filterung nach einer beliebigen Person mit dem Namen &quot;Smith&quot;und gibt Informationen aus allen verschachtelten Fragmenten zurück:

```xml
query {
  companyList(filter: {
    employees: {
      _match: {
        name: {
          _expressions: [
            {
              value: "Smith"
            }
          ]
        }
      }
    }
  }) {
    items {
      name
      ceo {
        name
        firstName
      }
      employees {
        name
        firstName
      }
    }
  }
}
```

<!-- need code / curl / cli examples-->

Ausführliche Informationen zur Verwendung der AEM GraphQL-API sowie zur Konfiguration der erforderlichen Elemente finden Sie unter:

* Verwenden von GraphQL mit AEM
* Die Struktur von Beispielinhaltsfragmenten
* Verwendung von GraphQL mit AEM – Beispielinhalt und Abfragen

## Wie geht es weiter {#whats-next}

Nachdem Sie nun gelernt haben, wie Sie mit der AEM GraphQL-API auf Ihren Headless Content zugreifen und ihn abfragen können, können Sie jetzt [erfahren, wie Sie mit der REST-API auf den Inhalt Ihrer Inhaltsfragmente zugreifen und diesen aktualisieren können.](/help/implementing/developing/headless-journey/update-your-content.md)

## Zusätzliche Ressourcen {#additional-resources}

* [GraphQL.org](https://graphql.org)
   * [Schemas](https://graphql.org/learn/Schema/)
   * [Variablen](https://graphql.org/learn/queries/#variables)
   * [GraphQL Java-Bibliotheken](https://graphql.org/code/#java)
* [GraphiQL](https://graphql.org/learn/serving-over-http/#graphiql)
* [Verwenden von GraphQL mit AEM](/help/assets/content-fragments/graphql-api-content-fragments.md)
   * [Aktivieren des GraphQL-Endpunkts](/help/assets/content-fragments/graphql-api-content-fragments.md#enabling-graphql-endpoint)
   * [AEM GraphiQL-Schnittstelle installieren](/help/assets/content-fragments/graphql-api-content-fragments.md#installing-graphiql-interface)
* [Die Struktur von Beispielinhaltsfragmenten](/help/assets/content-fragments/content-fragments-graphql-samples.md#content-fragment-structure-graphql)
* [Verwendung von GraphQL mit AEM – Beispielinhalt und Abfragen](/help/assets/content-fragments/content-fragments-graphql-samples.md)
   * [Beispielabfrage – ein Einzelstadtfragment](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-single-specific-city-fragment)
   * [Beispielabfrage für Metadaten – Liste der Metadaten für Auszeichnungen mit dem Titel „GB“ ](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-metadata-awards-gb)
   * [Beispielabfrage – Alle Städte mit einer gegebenen Variante](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-cities-named-variation)
* [Aktivieren der Funktionen für Inhaltsfragmente im Konfigurations-Browser](/help/assets/content-fragments/content-fragments-configuration-browser.md#enable-content-fragment-functionality-in-configuration-browser)
* [Arbeiten mit Inhaltsfragmenten](/help/assets/content-fragments/content-fragments.md)
   * [Inhaltsfragmentmodelle](/help/assets/content-fragments/content-fragments-models.md)
   * [JSON-Ausgabe](/help/assets/content-fragments/content-fragments-json-preview.md)
* [Verstehen Cross-Origin Resource Sharing (CORS)](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing.html?lang=de#understand-cross-origin-resource-sharing-(cors))
* [Erstellen von Zugriffs-Tokens für Server-seitige APIs](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md)
* [Erste Schritte mit AEM Headless](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html?lang=de)  - Eine kurze Video-Tutorial-Reihe, die einen Überblick über die Verwendung AEM Headless-Funktionen bietet, einschließlich Inhaltsmodellierung und GraphQL.
