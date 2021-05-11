---
title: Zugriff auf Ihre Inhalte über AEM Versand-APIs
description: Erfahren Sie in diesem Teil der AEM Headless Developer-Journey, wie Sie mit GraphQL-Abfragen auf Ihre Inhaltsfragmente zugreifen können.
hide: true
hidefromtoc: true
index: false
exl-id: 5ef557ff-e299-4910-bf8c-81c5154ea03f
translation-type: tm+mt
source-git-commit: c9b8e14a3beca11b6f81f2d5e5983d6fd801bf3f
workflow-type: tm+mt
source-wordcount: '846'
ht-degree: 15%

---

# Zugriff auf Ihre Inhalte über AEM Versand-APIs {#access-your-content}

>[!CAUTION]
>
>ARBEITEN IN FORTSCHRITTEN - Die Schaffung dieses Dokuments ist im Gange und sollte nicht als vollständig oder endgültig betrachtet werden und auch nicht für Produktionszwecke verwendet werden.

In diesem Teil der [AEM Headless Developer-Journey lernen Sie, wie Sie mit den GraphQL-Abfragen auf den Inhalt Ihrer Inhaltsfragmente zugreifen und sie in Ihre App einspeisen können (kopfloser Versand).](overview.md)

## Die Meldung bisher {#story-so-far}

Im vorherigen Dokument der AEM Journey [So modellieren Sie Ihren Inhalt](model-your-content.md), haben Sie die Grundlagen der Inhaltsmodellierung in AEM gelernt. Sie sollten nun verstehen, wie Sie Ihre Inhaltsstruktur modellieren, und diese Struktur dann mithilfe AEM Inhaltsfragmentmodelle und Inhaltsfragmente realisieren:

* Erkennen Sie die Konzepte und Terminologie im Zusammenhang mit der Inhaltsmodellierung.
* Verstehen Sie, warum Inhaltsmodellierung für den Versand von Headless-Inhalten erforderlich ist.
* Verstehen Sie, wie Sie diese Struktur mithilfe von AEM Inhaltsfragmentmodellen (und Erstellen von Inhalten mit Inhaltsfragmenten) realisieren.
* Verstehen Sie, wie Sie Ihren Inhalt modellieren können. Grundprinzipien mit Basisproben.

Dieser Artikel baut auf diesen Grundlagen auf, damit Sie verstehen, wie Sie mit der AEM GraphQL-API auf Ihre vorhandenen Kopflosen-Inhalte in AEM zugreifen können.

* **Audience**: Anfänger
* **Zielsetzung**: Erfahren Sie, wie Sie mithilfe AEM GraphQL-Abfragen auf den Inhalt Ihrer Inhaltsfragmente zugreifen können:
   * Einführung in GraphQL und die AEM GraphQL API.
   * Tauchen Sie ein in die Details der AEM GraphQL API.
   * Sehen Sie sich einige Abfragen an, um zu sehen, wie die Dinge in der Praxis funktionieren.

## Sie möchten also auf Ihre Inhalte zugreifen? {#so-youd-like-to-access-your-content}

Also...Sie haben all diesen Inhalt, ordentlich strukturiert (in Inhaltsfragmenten), und warten darauf, Ihre neue App mit Feeds zu versehen. Frage ist - wie man es dorthin bringt?

Sie benötigen eine Möglichkeit, bestimmte Inhalte Zielgruppe, auszuwählen, was Sie benötigen, und diese zur weiteren Verarbeitung an Ihre App zurückzugeben.

Mit Adobe Experience Manager (AEM) als Cloud Service können Sie mithilfe der AEM GraphQL API selektiv auf Inhaltsfragmente zugreifen, um nur die benötigten Inhalte zurückzugeben. Dies bedeutet, dass Sie den kopflosen Versand von strukturierten Inhalten zur Verwendung in Ihren Anwendungen realisieren können.

>[!NOTE]
>
>AEM GraphQL API ist eine benutzerdefinierte Implementierung, die auf der Standard-GraphQL API-Spezifikation basiert.

<!--
## GraphQL - An Introduction {#graphql-introduction}

GraphQL is an open-source specification that provides:

* a query language that enables you to select specific content from structured objects.
* a runtime to fulfill these queries with your structured content.

GraphQL is a *strongly* typed API. This means that *all* content must be clearly structured and organized by type, so that GraphQL *understands* what to access and how. The data fields are defined within GraphQL schemas, that define the structure of your content objects. 

GraphQL endpoints then provide the paths that respond to the GraphQL queries.

All this means that your app can accurately, reliably and efficiently select the content that it needs - just what you need when used with AEM.

>[!NOTE]
>
>See *GraphQL*.org and *GraphQL*.com.

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

## AEM GraphQL API {#aem-graphql-api}

The AEM GraphQL API is a customized version based on the standard GraphQL API specification, specially configured to allow you to perform (complex) queries on your Content Fragments.

Content Fragments are used, as the content is structured according to Content Fragment Models. This fulfills a basic requirement of GraphQL.

* A Content Fragment Model is built up of one, or more, fields. 
  * Each field is defined according to a Data Type.
* Content Fragment Models are used to generate the corresponding AEM GraphQL Schemas.

To actually access GraphQL for AEM (and the content) an endpoint is used to provide the access path. 

The content returned, via the AEM GraphQL API, can then be used by your applications. 

>[!NOTE]
>
>The AEM GraphQL API implementation is based on the GraphQL Java libraries.

### Use Cases for Author and Publish Environments {#use-cases-author-publish-environments}

The use cases for the AEM GraphQL API can depend on the type of AEM as a Cloud Service environment:

* Publish environment; used to: 
  * Query content for JS application (standard use-case)

* Author environment; used to: 
  * Query content for "content management purposes":
    * GraphQL in AEM as a Cloud Service is currently a read-only API.
    * The REST API can be used for CR(u)D operations.

## Content Fragments for use with the AEM GraphQL API {#content-fragments-use-with-aem-graphql-api}

Content Fragments can be used as a basis for GraphQL for AEM schemas and queries as:

* They enable you to design, create, curate and publish page-independent content.
* They are based on a Content Fragment Model, which pre-defines the structure for the resulting fragment by means of defined data types.
* Additional layers of structure can be achieved with the Fragment Reference data type, available when defining a model.
 
### Content Fragment Models {#content-fragments-models}

These Content Fragment Models:

* Are used to generate the Schemas, once **Enabled**.

* Provide the data types and fields required for GraphQL. They ensure that your application only requests what is possible, and receives what is expected.

* The data type **Fragment References** can be used in your model to reference another Content Fragment, and so introduce additional levels of structure.

### Fragment References {#fragment-references}

The **Fragment Reference**:

* Is a specific data type available when defining a Content Fragment Model.

* References another fragment, dependent on a specific Content Fragment Model.

* Allows you to create, and then retrieve, structured data.

  * When defined as a **multifeed**, multiple sub-fragments can be referenced (retrieved) by the prime fragment.

### JSON Preview {#json-preview}

To help with designing and developing your Content Fragment Models, you can preview JSON output in the Content Fragment Editor.

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

## Tatsächlich mit der AEM GraphQL API {#actually-using-aem-graphiql}

### Initial-Setup {#initial-setup}

Bevor Sie mit Abfragen zu Ihren Inhalten beginnen, müssen Sie Folgendes tun:

* Endpunkt aktivieren
   * Tools -> Sites -> GraphQL

* GraphiQL installieren (falls erforderlich)
   * Als dediziertes Paket installiert

### Beispielstruktur {#sample-structure}

Um die AEM GraphQL-API in einer Abfrage zu verwenden, können wir die beiden grundlegenden Inhaltsfragmentmodellstrukturen verwenden:

* Unternehmen
   * Name
   * CEO (Person)
   * Arbeitnehmer/innen
* Person
   * Name
   * Vorname

Wie Sie sehen können, verweisen die Felder CEO und Mitarbeiter auf die Fragmente Person.

Die Fragmentmodelle werden verwendet:

* beim Erstellen des Inhalts im Inhaltsfragment-Editor
* zur Generierung der GraphQL-Schema, die Sie Abfrage

### Testen Ihrer Abfragen {#where-to-test-your-queries}

Die Abfragen können in die GraphiQL-Oberfläche eingegeben werden, z. B. unter:

* `http://localhost:4502/content/graphiql.html `

### Erste Schritte mit Abfragen {#getting-Started-with-queries}

Eine einfache Abfrage ist, den Namen aller Einträge im Schema Firma zurückzugeben. Hier fordern Sie eine Liste aller Firmen an:

```xml
query {
  companyList {
    items {
      name
    }
  }
}
```

Eine etwas komplexere Abfrage besteht darin, alle Personen auszuwählen, die nicht den Namen &quot;Aufträge&quot;haben. Dadurch werden alle Personen nach Personen gefiltert, die nicht den Namen Aufträge haben. Dies wird mit dem Operator EQUALS_NOT erreicht (es gibt viele weitere):

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

Sie können auch komplexere Abfragen erstellen. Abfrage für alle Firmen, die mindestens einen Mitarbeiter mit dem Namen &quot;Smith&quot;haben. Diese Abfrage veranschaulicht das Filtern nach allen Personen mit dem Namen &quot;Smith&quot;und gibt Informationen aus den verschachtelten Fragmenten zurück:

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

Die vollständigen Informationen zur Verwendung der AEM GraphQL API sowie zur Konfiguration der erforderlichen Elemente finden Sie unter:

* Verwendung von GraphQL mit AEM
* Die Struktur des Musterinhaltsfragments
* Verwendung von GraphQL mit AEM – Beispielinhalt und Abfragen

## Wie geht es weiter {#whats-next}

Nachdem Sie nun gelernt haben, wie Sie mit der AEM GraphQL API auf Ihre kostenlosen Inhalte zugreifen und diese Abfrage durchführen können, können Sie jetzt [lernen, wie Sie mit der REST-API auf den Inhalt Ihrer Inhaltsfragmente zugreifen und diese aktualisieren können.](/help/implementing/developing/headless-journey/update-your-content.md)

## Zusätzliche Ressourcen {#additional-resources}

* [GraphQL.org](https://graphql.org)
   * [Schemas](https://graphql.org/learn/Schema/)
   * [Variablen](https://graphql.org/learn/queries/#variables)
   * [GraphQL Java-Bibliotheken](https://graphql.org/code/#java)
* [GraphiQL](https://graphql.org/learn/serving-over-http/#graphiql)
* [Verwendung von GraphQL mit AEM](/help/assets/content-fragments/graphql-api-content-fragments.md)
   * [Aktivieren des GraphQL-Endpunkts](/help/assets/content-fragments/graphql-api-content-fragments.md#enabling-graphql-endpoint)
   * [AEM GraphiQL-Schnittstelle installieren](/help/assets/content-fragments/graphql-api-content-fragments.md#installing-graphiql-interface)
* [Die Struktur des Musterinhaltsfragments](/help/assets/content-fragments/content-fragments-graphql-samples.md#content-fragment-structure-graphql)
* [Verwendung von GraphQL mit AEM – Beispielinhalt und Abfragen](/help/assets/content-fragments/content-fragments-graphql-samples.md)
   * [Beispielabfrage – ein Einzelstadtfragment](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-single-specific-city-fragment)
   * [Beispielabfrage für Metadaten – Liste der Metadaten für Auszeichnungen mit dem Titel „GB“ ](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-metadata-awards-gb)
   * [Beispielabfrage – Alle Städte mit einer gegebenen Variante](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-cities-named-variation)
* [Aktivieren der Funktionen für Inhaltsfragmente im Konfigurations-Browser](/help/assets/content-fragments/content-fragments-configuration-browser.md#enable-content-fragment-functionality-in-configuration-browser)
* [Arbeiten mit Inhaltsfragmenten](/help/assets/content-fragments/content-fragments.md)
   * [Inhaltsfragmentmodelle](/help/assets/content-fragments/content-fragments-models.md)
   * [JSON-Ausgabe](/help/assets/content-fragments/content-fragments-json-preview.md)
* [Verstehen Sie Cross-Herkunft Resource Sharing (CORS).](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing.html?lang=de#understand-cross-origin-resource-sharing-(cors))
* [Erstellen von Zugriffs-Tokens für Server-seitige APIs](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md)
* [Erste Schritte mit AEM Headless](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html?lang=de)  - Eine kurze Videoschulung mit einem Überblick über die Verwendung AEM Funktionen ohne Kopfdaten, einschließlich Inhaltsmodellierung und GraphQL.
