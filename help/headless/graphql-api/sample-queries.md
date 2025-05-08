---
title: Verwenden von GraphQL mit AEM – Beispielinhalt und Abfragen
description: Erfahren Sie, wie Sie GraphQL mit AEM verwenden, um Inhalte „headless“ bereitzustellen, indem Sie Beispielinhalte und Abfragen untersuchen.
feature: Headless, Content Fragments,GraphQL API
exl-id: b60fcf97-4736-4606-8b41-4051b8b0c8a7
role: Admin, Developer
source-git-commit: fdfe0291ca190cfddf3bed363a8c2271a65593a1
workflow-type: ht
source-wordcount: '1938'
ht-degree: 100%

---

# Verwenden von GraphQL mit AEM – Beispielinhalt und Abfragen {#learn-graphql-with-aem-sample-content-queries}

Erfahren Sie, wie Sie GraphQL mit AEM verwenden, um Inhalte „headless“ bereitzustellen, indem Sie Beispielinhalte und Abfragen untersuchen.

>[!NOTE]
>
>Lesen Sie diese Seite sowie die folgenden Themen:
>
>* [Inhaltsfragmente](/help/sites-cloud/administering/content-fragments/overview.md)
>* [Inhaltsfragmentmodelle](/help/sites-cloud/administering/content-fragments/content-fragment-models.md)
>* [AEM GraphQL-API zur Verwendung mit Inhaltsfragmenten](/help/headless/graphql-api/content-fragments.md)

Um mit GraphQL-Abfragen zu beginnen und zu sehen, wie sie mit AEM-Inhaltsfragmenten funktionieren, ist es hilfreich, einige praktische Beispiele zu betrachten.

Sehen Sie dazu:

* eine [Beispielstruktur für Inhaltsfragmente](#content-fragment-structure-graphql)

* Und einige [GraphQL-Beispielabfragen](#graphql-sample-queries), die auf der Beispiel-Inhaltsfragmentstruktur basieren (Inhaltsfragmentmodelle und verwandte Inhaltsfragmente).

>[!CONTEXTUALHELP]
>id="aemcloud_headless_graphql_sample"
>title="Verwenden von GraphQL mit AEM – Beispielinhalt und Abfragen"
>abstract="Erfahren Sie, wie Sie GraphQL mit AEM verwenden, um Inhalte „headless“ bereitzustellen, indem Sie Beispielinhalte und Abfragen untersuchen."

## GraphQL – Beispielabfragen unter Verwendung der Beispielstruktur für Inhaltsfragmente {#graphql-sample-queries-sample-content-fragment-structure}

In diesen Beispielabfragen wird das Erstellen von Abfragen zusammen mit Beispielergebnissen veranschaulicht.

>[!NOTE]
>
>Abhängig von Ihrer Instanz können Sie direkt auf die [in der AEM-GraphQL-API enthaltene GraphiQL-Schnittstelle](/help/headless/graphql-api/graphiql-ide.md) zugreifen, um Abfragen zu senden und zu testen.
>
>Sie können auf den Abfrage-Editor wie folgt zugreifen:
>
>* **Tools** > **Allgemein** > **GraphQL-Abfrage-Editor**
>* direkt, zum Beispiel: `http://localhost:4502/aem/graphiql.html`

>[!NOTE]
>
>Die Beispielabfragen basieren auf der [Beispielstruktur für Inhaltsfragmente zur Verwendung mit GraphQL](#content-fragment-structure-graphql).

### Beispielabfrage – Alle verfügbaren Schemata und Datentypen {#sample-all-schemes-datatypes}

Sie gibt alle `types` für alle verfügbaren Schemata zurück.

**Beispielabfrage**

```graphql
{
  __schema {
    types {
      name
      description
    }
  }
}
```

**Beispielergebnis**

```json
{
  "data": {
    "__schema": {
      "types": [
        {
          "name": "AdventureModel",
          "description": null
        },
        {
          "name": "AdventureModelArrayFilter",
          "description": null
        },
        {
          "name": "AdventureModelFilter",
          "description": null
        },
        {
          "name": "AdventureModelResult",
          "description": null
        },
        {
          "name": "AdventureModelResults",
          "description": null
        },
        {
          "name": "AllFragmentModels",
          "description": null
        },
        {
          "name": "ArchiveRef",
          "description": null
        },
        {
          "name": "ArrayMode",
          "description": null
        },
        {
          "name": "ArticleModel",
          "description": null
        },

...more results...

        {
          "name": "__EnumValue",
          "description": null
        },
        {
          "name": "__Field",
          "description": null
        },
        {
          "name": "__InputValue",
          "description": null
        },
        {
          "name": "__Schema",
          "description": "A GraphQL Introspection defines the capabilities of a GraphQL server. It exposes all available types and directives on the server, the entry points for query, mutation, and subscription operations."
        },
        {
          "name": "__Type",
          "description": null
        },
        {
          "name": "__TypeKind",
          "description": "An enum describing what kind of type a given __Type is"
        }
      ]
    }
  }
}
```

### Beispielabfrage – Alle Informationen zu allen Städten {#sample-all-information-all-cities}

Um alle Informationen zu allen Städten abzurufen, können Sie die grundlegende Abfrage verwenden:
**Beispielabfrage**

```graphql
{
  cityList {
    items
  }
}
```

Wenn die Abfrage ausgeführt wird, erweitert das System sie automatisch, um alle Felder einzuschließen:

```graphql
{
  cityList {
    items {
      _path
      name
      country
      population
    }
  }
}
```

**Beispielergebnisse**

```json
{
  "data": {
    "cityList": {
      "items": [
        {
          "_path": "/content/dam/sample-content-fragments/cities/basel",
          "name": "Basel",
          "country": "Switzerland",
          "population": 172258
        },
        {
          "_path": "/content/dam/sample-content-fragments/cities/berlin",
          "name": "Berlin",
          "country": "Germany",
          "population": 3669491
        },
        {
          "_path": "/content/dam/sample-content-fragments/cities/bucharest",
          "name": "Bucharest",
          "country": "Romania",
          "population": 1821000
        },
        {
          "_path": "/content/dam/sample-content-fragments/cities/san-francisco",
          "name": "San Francisco",
          "country": "USA",
          "population": 883306
        },
        {
          "_path": "/content/dam/sample-content-fragments/cities/san-jose",
          "name": "San Jose",
          "country": "USA",
          "population": 1026350
        },
        {
          "_path": "/content/dam/sample-content-fragments/cities/stuttgart",
          "name": "Stuttgart",
          "country": "Germany",
          "population": 634830
        },
        {
          "_path": "/content/dam/sample-content-fragments/cities/zurich",
          "name": "Zurich",
          "country": "Switzerland",
          "population": 415367
        }
      ]
    }
  }
}
```

### Beispielabfrage – Namen aller Städte {#sample-names-all-cities}

Eine unkomplizierte Abfrage, um den `name`aller Einträge im `city`-Schema zurückzugeben.

**Beispielabfrage**

```graphql
query {
  cityList {
    items {
      name
    }
  }
}
```

**Beispielergebnisse**

```json
{
  "data": {
    "cityList": {
      "items": [
        {
          "name": "Basel"
        },
        {
          "name": "Berlin"
        },
        {
          "name": "Bucharest"
        },
        {
          "name": "San Francisco"
        },
        {
          "name": "San Jose"
        },
        {
          "name": "Stuttgart"
        },
        {
          "name": "Zurich"
        }
      ]
    }
  }
}
```

### Beispielabfrage – ein Einzelstadtfragment {#sample-single-specific-city-fragment}

Eine Abfrage, um die Details eines einzelnen Fragmenteintrags an einem bestimmten Speicherort im Repository zurückzugeben.

**Beispielabfrage**

```graphql
{
  cityByPath (_path: "/content/dam/sample-content-fragments/cities/berlin") {
    item {
      _path
      name
      country
      population
     categories
    }
  }
}
```

**Beispielergebnisse**

```json
{
  "data": {
    "cityByPath": {
      "item": {
        "_path": "/content/dam/sample-content-fragments/cities/berlin",
        "name": "Berlin",
        "country": "Germany",
        "population": 3669491,
        "categories": [
          "city:capital",
          "city:emea"
        ]
      }
    }
  }
}
```

### Beispielabfrage – alle Städte mit einer gegebenen Variante {#sample-cities-named-variation}

Wenn Sie eine Variante mit dem Namen „Berlin Centre“ (`berlin_centre`) für `city` Berlin erstellen, können Sie eine Abfrage verwenden, um Details zur Variante zurückzugeben.

**Beispielabfrage**

```graphql
{
  cityList (variation: "berlin_center") {
    items {
      _path
      name
      country
      population
      categories
    }
  }
}
```

**Beispielergebnisse**

```json
{
  "data": {
    "cityList": {
      "items": [
        {
          "_path": "/content/dam/sample-content-fragments/cities/berlin",
          "name": "Berlin",
          "country": "Germany",
          "population": 3669491,
          "categories": [
            "city:capital",
            "city:emea"
          ]
        }
      ]
    }
  }
}
```

### Beispielabfrage – Namen aller Städte, die als Städtereisen markiert sind {#sample-names-all-cities-tagged-city-breaks}

Wenn Sie:

* eine Vielzahl von Tags namens `Tourism` erstellen: `Business`, `City Break`, `Holiday`
* und sie der übergeordneten Variante verschiedener `City`-Instanzen zuweisen

Dann können Sie eine Abfrage verwenden, um Details zu `name` und `tags` aller Einträge mit dem Tag „Städtereisen“ im Schema `city` herauszugeben.

**Beispielabfrage**

```xml
query {
  cityList(
    includeVariations: true,
    filter: {_tags: {_expressions: [{value: "tourism:city-break", _operator: CONTAINS}]}}
  ){
    items {
      name,
      _tags
    }
  }
}
```

**Beispielergebnisse**

```xml
{
  "data": {
    "cityList": {
      "items": [
        {
          "name": "Berlin",
          "_tags": [
            "tourism:city-break",
            "tourism:business"
          ]
        },
        {
          "name": "Zurich",
          "_tags": [
            "tourism:city-break",
            "tourism:business"
          ]
        }
      ]
    }
  }
}
```

### Beispielabfrage – Vollständige Details des CEO und der Mitarbeiter einer Firma {#sample-full-details-company-ceos-employees}

Unter Verwendung der Struktur der verschachtelten Fragmente gibt diese Abfrage die vollständigen Details des CEO eines Unternehmens und aller seiner Mitarbeiter zurück.

**Beispielabfrage**

```graphql
query {
  companyList {
    items {
      name
      ceo {
        _path
        name
        firstName
        awards {
        id
          title
        }
      }
      employees {
       name
        firstName
       awards {
         id
          title
        }
      }
    }
  }
}
```

**Beispielergebnisse**

```json
{
  "data": {
    "companyList": {
      "items": [
        {
          "name": "Apple Inc.",
          "ceo": {
            "_path": "/content/dam/sample-content-fragments/persons/steve-jobs",
            "name": "Jobs",
            "firstName": "Steve",
            "awards": []
          },
          "employees": [
            {
              "name": "Marsh",
              "firstName": "Duke",
              "awards": []
            },
            {
              "name": "Caulfield",
              "firstName": "Max",
              "awards": [
                {
                  "id": "GB",
                  "title": "Gameblitz"
                }
              ]
            }
          ]
        },
        {
          "name": "Little Pony, Inc.",
          "ceo": {
            "_path": "/content/dam/sample-content-fragments/persons/adam-smith",
            "name": "Smith",
            "firstName": "Adam",
            "awards": []
          },
          "employees": [
            {
              "name": "Croft",
              "firstName": "Lara",
              "awards": [
                {
                  "id": "GS",
                  "title": "Gamestar"
                }
              ]
            },
            {
              "name": "Slade",
              "firstName": "Cutter",
              "awards": [
                {
                  "id": "GB",
                  "title": "Gameblitz"
                },
                {
                  "id": "GS",
                  "title": "Gamestar"
                }
              ]
            }
          ]
        },
        {
          "name": "NextStep Inc.",
          "ceo": {
            "_path": "/content/dam/sample-content-fragments/persons/steve-jobs",
            "name": "Jobs",
            "firstName": "Steve",
            "awards": []
          },
          "employees": [
            {
              "name": "Smith",
              "firstName": "Joe",
              "awards": []
            },
            {
              "name": "Lincoln",
              "firstName": "Abraham",
              "awards": []
            }
          ]
        }
      ]
    }
  }
}
```

### Beispielabfrage – Alle Personen mit dem Namen „Jobs“ oder „Smith“ {#sample-all-persons-jobs-smith}

Eine Abfrage, die alle `persons` nach denen filtert, die den Namen `Jobs` oder `Smith` haben.

**Beispielabfrage**

```graphql
query {
  personList(filter: {
    name: {
      _logOp: OR
      _expressions: [
        {
          value: "Jobs"
        },
        {
          value: "Smith"
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

**Beispielergebnisse**

```json
{
  "data": {
    "personList": {
      "items": [
        {
          "name": "Smith",
          "firstName": "Adam"
        },
        {
          "name": "Smith",
          "firstName": "Joe"
        },
        {
          "name": "Jobs",
          "firstName": "Steve"
        }
      ]
    }
  }
}
```

### Beispielabfrage – Alle Personen, die nicht den Namen „Jobs“ haben  {#sample-all-persons-not-jobs}

Eine Abfrage, die alle `persons` nach denen filtert, die den Namen `Jobs` oder `Smith` haben.

**Beispielabfrage**

```graphql
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

**Beispielergebnisse**

```json
{
  "data": {
    "personList": {
      "items": [
        {
          "name": "Lincoln",
          "firstName": "Abraham"
        },
        {
          "name": "Smith",
          "firstName": "Adam"
        },
        {
          "name": "Slade",
          "firstName": "Cutter"
        },
        {
          "name": "Marsh",
          "firstName": "Duke"
        },
        {
          "name": "Smith",
          "firstName": "Joe"
        },
        {
          "name": "Croft",
          "firstName": "Lara"
        },
        {
          "name": "Caulfield",
          "firstName": "Max"
        }
      ]
    }
  }
}
```

### Beispielabfrage – Alle Abenteuer, deren `_path` mit einem bestimmten Präfix beginnt {#sample-wknd-all-adventures-cycling-path-filter}

Alle `adventures`, bei denen `_path` mit einem bestimmten Präfix (`/content/dam/wknd/en/adventures/cycling`) beginnt.

**Beispielabfrage**

```graphql
query {
  adventureList(
    filter: {
      _path: {
        _expressions: [
        {
          value: "/content/dam/wknd/en/adventures/cycling"
         _operator: STARTS_WITH
        }]
       }
    })
    {
    items {
      _path
    }
  }
}
```

**Beispielergebnisse**

```json
{
  "data": {
    "adventureList": {
      "items": [
        {
          "_path": "/content/dam/wknd/en/adventures/cycling-southern-utah/cycling-southern-utah"
        },
        {
          "_path": "/content/dam/wknd/en/adventures/cycling-tuscany/cycling-tuscany"
        }
      ]
    }
  }
}
```

### Beispielabfrage – Alle Städte in Deutschland oder der Schweiz mit einer Einwohnerzahl zwischen 400.000 und 999.999 {#sample-all-cities-d-ch-population}

Hier wird nach einer Kombination von Feldern gefiltert. Ein `AND` (implizit) wird verwendet, um den `population`-Bereich auszuwählen, während ein `OR` (explizit) zur Auswahl der erforderlichen Städte verwendet wird.

**Beispielabfrage**

```graphql
query {
  cityList(filter: {
    population: {
      _expressions: [
        {
          value: 400000
          _operator: GREATER_EQUAL
        }, {
          value: 1000000
          _operator: LOWER
        }
      ]
    },
    country: {
      _logOp: OR
      _expressions: [
        {
          value: "Germany"
        }, {
          value: "Switzerland"
        }
      ]
    }
  }) {
    items {
      name
      population
      country
    }
  }
}
```

**Beispielergebnisse**

```json
{
  "data": {
    "cityList": {
      "items": [
        {
          "name": "Stuttgart",
          "population": 634830,
          "country": "Germany"
        },
        {
          "name": "Zurich",
          "population": 415367,
          "country": "Switzerland"
        }
      ]
    }
  }
}
```

### Beispielabfrage – Alle Städte mit SAN im Namen, unabhängig von der Groß-/Kleinschreibung {#sample-all-cities-san-ignore-case}

Diese Abfrage durchsucht alle Städte mit `SAN` im Namen, unabhängig von der Groß-/Kleinschreibung.

**Beispielabfrage**

```graphql
query {
  cityList(filter: {
    name: {
      _expressions: [
        {
          value: "SAN"
          _operator: CONTAINS
          _ignoreCase: true
        }
      ]
    }
  }) {
    items {
      name
      population
      country
    }
  }
}
```

**Beispielergebnisse**

```json
{
  "data": {
    "cityList": {
      "items": [
        {
          "name": "San Francisco",
          "population": 883306,
          "country": "USA"
        },
        {
          "name": "San Jose",
          "population": 1026350,
          "country": "USA"
        }
      ]
    }
  }
}
```

### Beispielabfrage – Filtern eines Arrays nach einem Element, das mindestens einmal vorkommen muss {#sample-array-item-occur-at-least-once}

Diese Abfrage filtert ein Array nach einem Element (`city:na`), das mindestens einmal vorkommen muss.

**Beispielabfrage**

```graphql
query {
  cityList(filter: {
    categories: {
      _expressions: [
        {
          value: "city:na"
          _apply: AT_LEAST_ONCE
        }
      ]
    }
  }) {
    items {
      name
      population
      country
      categories
    }
  }
}
```

**Beispielergebnisse**

```json
{
  "data": {
    "cityList": {
      "items": [
        {
          "name": "San Francisco",
          "population": 883306,
          "country": "USA",
          "categories": [
            "city:beach",
            "city:na"
          ]
        },
        {
          "name": "San Jose",
          "population": 1026350,
          "country": "USA",
          "categories": [
            "city:na"
          ]
        }
      ]
    }
  }
}
```

### Beispielabfrage – Filtern nach einem exakten Array-Wert {#sample-array-exact-value}

Diese Abfrage filtert nach einem exakten Array-Wert.

**Beispielabfrage**

```graphql
query {
  cityList(filter: {
    categories: {
      _expressions: [
        {
          values: [
            "city:beach",
            "city:na"
          ]
        }
      ]
    }
  }) {
    items {
      name
      population
      country
      categories
    }
  }
}
```

**Beispielergebnisse**

```json
{
  "data": {
    "cityList": {
      "items": [
        {
          "name": "San Francisco",
          "population": 883306,
          "country": "USA",
          "categories": [
            "city:beach",
            "city:na"
          ]
        }
      ]
    }
  }
}
```

### Beispielabfrage für verschachtelte Inhaltsfragmente – Alle Unternehmen mit mindestens einem Mitarbeiter mit dem Namen „Smith“  {#sample-companies-employee-smith}

Diese Abfrage veranschaulicht die Filterung nach `person` von `name` „Smith“, wobei Informationen aus zwei verschachtelten Fragmenten – `company` und `employee` – zurückgegeben werden.

**Beispielabfrage**

```graphql
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

**Beispielergebnisse**

```json
{
  "data": {
    "companyList": {
      "items": [
        {
          "name": "NextStep Inc.",
          "ceo": {
            "name": "Jobs",
            "firstName": "Steve"
          },
          "employees": [
            {
              "name": "Smith",
              "firstName": "Joe"
            },
            {
              "name": "Lincoln",
              "firstName": "Abraham"
            }
          ]
        }
      ]
    }
  }
}
```

### Beispielabfrage für verschachtelte Inhaltsfragmente – Alle Unternehmen, bei denen alle Mitarbeiter die Auszeichnung „Gamestar“ erhalten haben {#sample-all-companies-employee-gamestar-award}

Diese Abfrage veranschaulicht die Filterung von drei verschachtelten Fragmenten – `company`, `employee` und `award`.

**Beispielabfrage**

```graphql
query {
  companyList(filter: {
    employees: {
      _apply: ALL
      _match: {
        awards: {
          _match: {
            id: {
              _expressions: [
                {
                  value: "GS"
                  _operator:EQUALS
                }
              ]
            }
          }
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
        awards {
          id
          title
        }
      }
    }
  }
}
```

**Beispielergebnisse**

```json
{
  "data": {
    "companyList": {
      "items": [
        {
          "name": "Little Pony, Inc.",
          "ceo": {
            "name": "Smith",
            "firstName": "Adam"
          },
          "employees": [
            {
              "name": "Croft",
              "firstName": "Lara",
              "awards": [
                {
                  "id": "GS",
                  "title": "Gamestar"
                }
              ]
            },
            {
              "name": "Slade",
              "firstName": "Cutter",
              "awards": [
                {
                  "id": "GB",
                  "title": "Gameblitz"
                },
                {
                  "id": "GS",
                  "title": "Gamestar"
                }
              ]
            }
          ]
        }
      ]
    }
  }
}
```

### Beispielabfrage für Metadaten – Liste der Metadaten für Auszeichnungen mit dem Titel „GB“ {#sample-metadata-awards-gb}

Diese Abfrage veranschaulicht die Filterung von drei verschachtelten Fragmenten – `company`, `employee` und `award`.

**Beispielabfrage**

```graphql
query {
  awardList(filter: {
      id: {
        _expressions: [
          {
            value:"GB"
          }
        ]
    }
  }) {
    items {
      _metadata {
        stringMetadata {
          name,
          value
        }
      }
      id
      title
    }
  }
}
```

**Beispielergebnisse**

```json
{
  "data": {
    "awardList": {
      "items": [
        {
          "_metadata": {
            "stringMetadata": [
              {
                "name": "title",
                "value": "Gameblitz Award"
              },
              {
                "name": "description",
                "value": ""
              }
            ]
          },
          "id": "GB",
          "title": "Gameblitz"
        }
      ]
    }
  }
}
```

## Beispielabfragen unter Verwendung des WKND-Projekts {#sample-queries-using-wknd-project}

Diese Beispielabfragen basieren auf dem WKND-Projekt. Es umfasst Folgendes:

* Inhaltsfragmentmodelle verfügbar unter:
  `http://<hostname>:<port>/libs/dam/cfm/models/console/content/models.html/conf/wknd`

* Inhaltsfragmente (und anderere Inhalte) verfügbar unter:
  `http://<hostname>:<port>/assets.html/content/dam/wknd/en`
  `http://<hostname>:<port>/assets.html/content/dam/wknd-shared/en`

>[!NOTE]
>
>Da die Ergebnisse sehr umfangreich sein können, werden sie hier nicht wiedergegeben.

### Beispielabfrage für alle Inhaltsfragmente eines bestimmten Modells mit den angegebenen Eigenschaften {#sample-wknd-all-model-properties}

Diese Beispielabfrage untersucht:

* Alle Inhaltsfragmente vom Typ `article`
* mit `_path` und `authorFragment`-Eigenschaften.

**Beispielabfrage**

```graphql
{
  articleList {
    items {
      _path
      authorFragment {
        _path
        firstName
        lastName
        birthDay
      }
    }
 }
}
```

### Beispielabfrage für Metadaten {#sample-wknd-metadata}

Diese Abfrage untersucht:

* Alle Inhaltsfragmente vom Typ `adventure`
* Metadaten

**Beispielabfrage**

```graphql
{
  adventureList {
    items {
      _path,
      _metadata {
        stringMetadata {
          name,
          value
        }
        stringArrayMetadata {
          name,
          value
        }
        intMetadata {
          name,
          value
        }
        intArrayMetadata {
          name,
          value
        }
        floatMetadata {
          name,
          value
        }
        floatArrayMetadata {
          name,
          value
        }
        booleanMetadata {
          name,
          value
        }
        booleanArrayMetadata {
          name,
          value
        }
        calendarMetadata {
          name,
          value
        }
        calendarArrayMetadata {
          name,
          value
        }
      }
    }
  }
}
```

### Beispielabfrage für ein einzelnes Inhaltsfragment eines bestimmten Modells {#sample-wknd-single-content-fragment-of-given-model}

Diese Beispielabfrage untersucht:

* Ein einzelnes Inhaltsfragment vom Typ `article` an einem bestimmten Pfad
   * innerhalb des Fragments, alle Inhaltsformate:
      * HTML
      * Markdown
      * Nur Text
      * JSON

**Beispielabfrage**

```graphql
{
  articleByPath(_path: "/content/dam/wknd-shared/en/magazine/alaska-adventure/alaskan-adventures") {
    item {
        _path
        authorFragment {
          _path
          firstName
          lastName
          birthDay
        }
        main {
          html
          markdown
          plaintext
          json
        }
    }
  }
}
```

### Beispielabfrage für ein Inhaltsfragmentmodell anhand eines Modells {#sample-wknd-content-fragment-model-from-model}

Diese Beispielabfrage untersucht:

* Für ein einzelnes Inhaltsfragment
   * Details des zugrunde liegenden Inhaltsfragmentmodells

**Beispielabfrage**

```graphql
{
  adventureByPath(_path: "/content/dam/wknd-shared/en/magazine/western-australia/western-australia-by-camper-van") {
    item {
      _path
      title
      _model {
        _path
        title
      }
    }
  }
}
```

### Beispielabfrage für ein verschachteltes Inhaltsfragment – Typ mit einem einzigen Modell{#sample-wknd-nested-fragment-single-model}

Diese Abfrage untersucht:

* Ein einzelnes Inhaltsfragment vom Typ `article` an einem bestimmten Pfad
   * innerhalb des Fragments, Pfad und Autorin bzw. Autor des referenzierten (verschachtelten) Fragments

>[!NOTE]
>
>Das Feld `referencearticle` hat den Datentyp `fragment-reference`.

**Beispielabfrage**

```graphql
{
  adventureByPath(_path: "/content/dam/wknd-shared/en/magazine/western-australia/western-australia-by-camper-van") {
    item {
      _path
      title
      _model {
        _path
        title
      }
    }
  }
}
```

### Beispielabfrage für ein verschachteltes Inhaltsfragment – Typ mit mehreren Modellen{#sample-wknd-nested-fragment-multiple-model}

#### Einzelner referenzierter Modelltyp

Diese Abfrage untersucht:

* Mehrere Inhaltsfragmente vom Typ `bookmark`
   * Mit Fragmentverweisen auf andere Fragmente des spezifischen Modelltyps `Article`

>[!NOTE]
>
>Das Feld `fragments` hat den Datentyp `fragment-reference`, wobei das Modell `Article` ausgewählt wurde. Die Abfrage liefert `fragments` als ein Array von `[Article]`.

```graphql
{
  bookmarkList {
    items {
        fragments {
          _path
          author
        }
     }
  }
}
```

#### Mehrere referenzierte Modelltypen

Diese Abfrage untersucht:

* Mehrere Inhaltsfragmente vom Typ `bookmark`
   * Mit Fragmentreferenzen auf andere Fragmente der spezifischen Modelltypen `Article` und `Adventure`

>[!NOTE]
>
>Das Feld `fragments` hat den Datentyp `fragment-reference`, wobei die Modelle `Article`, `Adventure` ausgewählt sind. Die Abfrage liefert `fragments` als ein Array von `[AllFragmentModels]`, das mit Vereinigungstyp dereferenziert wird.

```graphql
{
  bookmarkList {
    items {
        fragments {
          ... on ArticleModel {
            _path
            author
          }
          ... on AdventureModel {
            _path
            adventureTitle
          }
        }
     }
  }
}
```

### Beispielabfrage für ein Inhaltsfragment eines bestimmten Modells mit Inhaltsreferenzen{#sample-wknd-fragment-specific-model-content-reference}

Es gibt zwei Varianten dieser Abfrage:

1. Zurückgeben aller Inhaltsreferenzen.
1. Zurückgeben der spezifischen Inhaltsreferenzen vom Typ `attachments`.

Diese Abfragen untersuchen:

* Mehrere Inhaltsfragmente vom Typ `bookmark`
   * Mit Inhaltsreferenzen auf andere Fragmente.

#### Beispielabfrage für mehrere Inhaltsfragmente mit vorab abgerufenen Verweisen {#sample-wknd-multiple-fragments-prefetched-references}

Die folgende Abfrage gibt alle Inhaltsreferenzen mit `_references` zurück:

<!-- need replacement query -->

```graphql
{
  bookmarkList {
     _references {
         ... on ImageRef {
          _path
          type
          height
        }
        ... on MultimediaRef {
          _path
          type
          size
        }
        ... on DocumentRef {
          _path
          type
          author
        }
        ... on ArchiveRef {
          _path
          type
          format
        }
    }
    items {
        _path
    }
  }
}
```

#### Beispielabfrage für mehrere Inhaltsfragmente mit Anhängen {#sample-wknd-multiple-fragments-attachments}

Die folgende Abfrage gibt alle `attachments` zurück – ein bestimmtes Feld (Untergruppe) vom Typ `content-reference`:

>[!NOTE]
>
>Das Feld `attachments` hat den Datentyp `content-reference`, wobei verschiedene Formen ausgewählt sind.

<!-- need replacement query -->

```graphql
{
  bookmarkList {
    items {
      attachments {
        ... on PageRef {
          _path
          type
        }
        ... on ImageRef {
          _path
          width
        }
        ... on MultimediaRef {
          _path
          size
        }
        ... on DocumentRef {
          _path
          author
        }
        ... on ArchiveRef {
          _path
          format
        }
      }
    }
  }
}
```

### Beispielabfrage für ein Inhaltsfragment eines bestimmten Modells mit UUID-Referenzen {#sample-wknd-fragment-specific-model-uuid-references}

Diese Abfragen untersuchen:

* die UUID für ein Inhaltsfragment und für referenzierte Inhaltsfragmente oder Assets;
* das Ergebnis wird über die JSON-Eigenschaft `_id` zurückgegeben.

#### Beispielabfrage für ein Inhaltsfragment eines bestimmten Modells mit einer UUID-Referenz {#sample-wknd-fragment-specific-model-using-a-uuid-reference}

Die folgende Abfrage gibt alle Inhaltsreferenzen mit `_id` und `_path` zurück:

```graphql
{
  articleList {
    items {
        _id
        _path
        title
        featuredImage {
          ... on ImageRef {
            _id
            _path           
          }
        }
        authorFragment {
          firstName
          lastName
          profilePicture {
            ... on ImageRef {
              _id
              _path
            }
          }
        }
      }
  }
}
```

#### Beispielabfrage für Inhaltsfragmente nach UUID-Referenz {#sample-wknd-fragment-specific-model-by-uuid-reference}

Die folgende Abfrage gibt alle Inhaltsreferenzen zurück, die sich auf eine bestimmte `_id` beziehen:

```graphql
{
  articleById(_id: "3ce2bf53-7436-4d3e-b19a-2793bc2ca63e") {
    item {
      _id
      _path
      title
      featuredImage {
        ... on ImageRef {
          _id
          _path
        }
      }
      authorFragment {
        firstName
        lastName
        profilePicture {
          ... on ImageRef {
            _id
            _path
          }
        }
      }
    }
  }
}
```

### Beispielabfrage für ein einzelnes Inhaltsfragment mit RTE-Inline-Verweis {#sample-wknd-single-fragment-rte-inline-reference}

Diese Abfrage untersucht:

* Ein einzelnes Inhaltsfragment vom Typ `bookmark` an einem bestimmten Pfad
   * Darin die RTE-Inline-Verweise

>[!NOTE]
>
>Die RTE-Inline-Verweise werden in `_references` realisiert.

<!-- need replacement query -->

**Beispielabfrage**

```graphql
{
  bookmarkByPath(_path: "/content/dam/wknd/en/bookmarks/skitouring") {
    item {
      _path
      description {
        json
      }
    }
    _references {
      ... on ArticleModel {
        _path
      }
      ... on AdventureModel {
        _path
      }
      ... on ImageRef {
        _path
      }
      ... on MultimediaRef {
        _path
      }
      ... on DocumentRef {
        _path
      }
      ... on ArchiveRef {
        _path
      }
    }
  }
}
```

### Beispielabfrage für eine einzelne Variante eines Inhaltsfragments eines bestimmten Modells {#sample-wknd-single-fragment-given-model}

Diese Abfrage untersucht:

* Ein einzelnes Inhaltsfragment vom Typ `author` an einem bestimmten Pfad
   * innerhalb des Fragments, die Daten im Zusammenhang mit der Variante: `another`

**Beispielabfrage**

```graphql
{
  authorByPath(_path: "/content/dam/wknd-shared/en/contributors/ian-provo", variation: "another") {
    item {
        _path
        _variation
        firstName
        lastName
        birthDay
    }
  }
}
```

### Beispielabfrage für eine gegebene Variante mehrerer Inhaltsfragmente eines bestimmten Modells {#sample-wknd-variation-multiple-fragment-given-model}

Diese Abfrage untersucht:

* Inhaltsfragmente vom Typ `author` mit einer bestimmten Variante: `another`

>[!NOTE]
>
>Diese Abfrage stellt ein Fallback für Inhaltsfragmente dar, für die keine [Variante](/help/headless/graphql-api/content-fragments.md#variations) des angegebenen Namens vorhanden ist.

**Beispielabfrage**

```graphql
{
  authorList(variation: "another") {
    items {
        _path
        _variation
        firstName
        lastName
        birthDay
    }
  }
}
```

### Beispielabfrage für mehrere Inhaltsfragmente und deren Varianten eines bestimmten Modells {#sample-wknd-multiple-fragment-variations-given-model}

Diese Abfrage untersucht:

* für Inhaltsfragmente vom Typ `article` und alle Varianten

**Beispielabfrage**

```xml
query {
  articleList(
    includeVariations: true  ){
    items {
      _variation
      _path
      _tags
      _metadata {
        stringArrayMetadata {
          name
          value
        }
      }
    }
  }
}
```

### Beispielabfrage für Inhaltsfragmentvarianten eines bestimmten Modells, an das ein bestimmtes Tag angehängt ist{#sample-wknd-fragment-variations-given-model-specific-tag}

Diese Abfrage untersucht:

* für Inhaltsfragmente vom Typ `article` mit einer oder mehreren Varianten mit dem Tag `WKND : Activity / Hiking`

**Beispielabfrage**

```xml
{
  articleList(
    includeVariations: true,
    filter: {_tags: {_expressions: [{value: "wknd:activity/hiking", _operator: CONTAINS}]}}
  ){
    items {
      _variation
      _path
      _tags
      _metadata {
        stringArrayMetadata {
          name
          value
        }
      }
    }
  }
}
```

### Beispielabfrage für mehrere Inhaltsfragmente eines bestimmten Gebietsschemas {#sample-wknd-multiple-fragments-given-locale}

Diese Abfrage untersucht:

* Inhaltsfragmente vom Typ `article` innerhalb des Gebietsschemas `fr`

**Beispielabfrage**

```graphql
{ 
  articleList(_locale: "fr") {
    items {
      _path
      authorFragment {
        _path
        firstName
        lastName
        birthDay
      }
      main {
        html
        markdown
        plaintext
        json
      }
    }
  }
}
```

### Beispiel für eine Listenabfrage unter Verwendung von „offset“ und „limit“ {#sample-list-offset-limit}

Diese Abfrage fragt Folgendes ab:

* die Ergebnisseite mit bis zu fünf Artikeln, beginnend mit dem fünften Artikel aus der *vollständigen* Ergebnisliste

**Beispielabfrage**

```graphql
{
   articleList(offset: 5, limit: 5) {
    items {
      authorFragment {
        _path
        firstName
        lastName
        birthDay
      }
      _path
    }
  }
}
```

### Beispielhafte Paginierungsabfrage mit „first“ und „after“  {#sample-pagination-first-after}

Diese Abfrage fragt Folgendes ab:

* die Ergebnisseite mit bis zu fünf Abenteuern, beginnend mit dem angegebenen Cursor-Element in der *vollständigen* Ergebnisliste

**Beispielabfrage**

```graphql
{
    adventurePaginated(first: 5, after: "ODg1MmMyMmEtZTAzMy00MTNjLThiMzMtZGQyMzY5ZTNjN2M1") {
        edges {
          cursor
          node {
            title
          }
        }
        pageInfo {
          endCursor
          hasNextPage
        }
    }
}
```

### Beispielabfrage mit Filterung nach _tags-ID und Ausschluss von Varianten {#sample-filtering-tag-not-variations}

Diese Abfrage fragt Folgendes ab:

* für Inhaltsfragmente vom Typ `vehicle` mit dem Tag `big-block`
* ausschließlich Varianten

**Beispielabfrage**

```graphql
query {
  vehicleList(
    filter: {
    _tags: {
      _expressions: [
        {
          value: "vehicles:big-block"
          _operator: CONTAINS
        }
      ]
    }
  }) {
    items {
      _variation
      _path
      type
      name
      model
      fuel
      _tags
    }
  }
} 
```

### Beispielabfrage mit Filterung nach _tags-ID und Einschluss von Varianten {#sample-filtering-tag-with-variations}

Diese Abfrage fragt Folgendes ab:

* für Inhaltsfragmente vom Typ `vehicle` mit dem Tag `big-block`
* einschließlich Varianten

**Beispielabfrage**

```graphql
{
  enginePaginated(after: "SjkKNmVkODFmMGQtNTQyYy00NmQ4LTljMzktMjhlNzQwZTY1YWI2Cmo5", first: 9 ,includeVariations:true, sort: "name",
    filter: {
    _tags: {
      _expressions: [
        {
          value: "vehicles:big-block"
          _operator: CONTAINS
        }
      ]
    }
  }) {
    edges{
    node {
        _variation
        _path
        name
        type
        size
        _tags
        _metadata {
          stringArrayMetadata {
            name
            value
          }
        }
    }
      cursor
    }
  }
} 
```

## Beispielabfragen für die Bereitstellung von DAM- und Dynamic Media-Assets {#sample-queries-delivery-DAM-DM}

Für die Web-optimierte Bildbereitstellung (von DAM-Assets):

* [Beispielabfrage für die Web-optimierte Bereitstellung von Bildern mit allen Parametern](/help/headless/graphql-api/content-fragments.md#web-optimized-image-delivery-full-parameters)

* [Beispielabfrage für die Web-optimierte Bereitstellung von Bildern mit einem einzigen angegebenen Parameter](/help/headless/graphql-api/content-fragments.md#web-optimized-image-delivery-single-query-variable)

Für die Bereitstellung der URL an ein Dynamic Media-Asset

* Siehe [Beispielabfrage für die Bereitstellung von Dynamic Media-Assets nach URL – Bildverweis](/help/headless/graphql-api/content-fragments.md#sample-query-dynamic-media-asset-delivery-by-url-imageref)

* Siehe [Beispielabfrage für die Bereitstellung von Dynamic Media-Assets nach URL – Mehrere Verweise](/help/headless/graphql-api/content-fragments.md#sample-query-dynamic-media-asset-delivery-by-url-multiple-refs)

Für die Bereitstellung von Remote-Assets, die nicht lokal in der aktuellen AEM-Instanz vorhanden sind, über den Inhaltsfragmenteditor.

* Siehe [Beispielabfrage für Dynamic Media für die Unterstützung von OpenAPI-Assets (Remote-Assets)](/help/headless/graphql-api/content-fragments.md#sample-query-dynamic-media-for-openapi-asset-support)

## Die Struktur des Beispielinhaltsfragments (verwendet mit GraphQL) {#content-fragment-structure-graphql}

Die Abfragen basieren auf der folgenden Struktur, die Folgendes verwendet:

* Ein oder mehrere [Beispielmodelle für Inhaltsfragmente](#sample-content-fragment-models-schemas) bilden die Grundlage für die GraphQL-Schemata

* [Beispielinhaltsfragmente](#sample-content-fragments) basierend auf den oben genannten Modellen

### Beispielmodelle für Inhaltsfragmente (Schemata) {#sample-content-fragment-models-schemas}

Für die Beispielabfragen verwenden Sie die folgenden Inhaltsmodelle und ihre Wechselbeziehungen (Verweise ->):

* [Unternehmen](#model-company)
> [Person](#model-person)
> [Auszeichnung](#model-award)

* [Stadt](#model-city)

#### Unternehmen {#model-company}

Die grundlegenden Felder, die das Unternehmen definieren, sind:

| Feldname | Datentyp | Verweis |
|--- |--- |--- |
| Unternehmensname | Einzeiliger Text | |
| CEO | Fragmentreferenz (Einzelfeld) | [Person](#model-person) |
| Mitarbeiter | Fragmentreferenz (Mehrfeld) | [Person](#model-person) |

#### Person {#model-person}

Die Felder, die eine Person definieren, die auch ein Mitarbeiter sein kann:

| Feldname | Datentyp | Verweis |
|--- |--- |--- |
| Name | Einzeiliger Text | |
| Vorname | Einzeiliger Text | |
| Auszeichnungen | Fragmentreferenz (Mehrfeld) | [Auszeichnung](#model-award) |

#### Auszeichnung {#model-award}

Die Felder, die eine Auszeichnung definieren, sind:

| Feldname | Datentyp | Verweis |
|--- |--- |--- |
| Kürzel/Kennung | Einzeiliger Text | |
| Titel | Einzeiliger Text | |

#### Stadt {#model-city}

Die Felder zur Definition einer Stadt sind:

| Feldname | Datentyp | Verweis |
|--- |--- |--- |
| Name | Einzeiliger Text | |
| Land | Einzeiliger Text | |
| Einwohnerzahl | Zahl | |
| Kategorien | Tags | |

### Beispielinhaltsfragmente {#sample-content-fragments}

Die folgenden Fragmente werden für das entsprechende Modell verwendet.

#### Unternehmen {#fragment-company}

| Unternehmensname | CEO | Mitarbeiter |
|--- |--- |--- |
| Apple | Steve Jobs | Duke Marsh<br>Max Caulfield |
| Little Pony Inc. | Adam Smith | Lara Croft<br>Cutter Slade |
| NextStep Inc. | Steve Jobs | Joe Smith<br>Abe Lincoln |

#### Person {#fragment-person}

| Name | Vorname | Auszeichnungen |
|--- |--- |--- |
| Lincoln | Abe | |
| Smith | Adam | |
| Slade | Cutter | Gameblitz<br>Gamestar |
| Marsh | Duke | |
| Smith | Joe | |
| Croft | Lara | Gamestar |
| Caulfield | Max | Gameblitz |
| Jobs | Steve | |

#### Auszeichnung {#fragment-award}

| Kürzel/Kennung | Titel |
|--- |--- |
| GB | Gameblitz |
| GS | Gamestar |
| OSC | Oscar |

#### Stadt {#fragment-city}

| Name | Land | Einwohnerzahl | Kategorien |
|--- |--- |--- |--- |
| Basel | Schweiz | 172258 | city:emea |
| Berlin | Deutschland | 3669491 | city:capital<br>city:emea |
| Bukarest | Rumänien | 1821000 | city:capital<br>city:emea |
| San Francisco | USA | 883306 | city:beach<br>city:na |
| San Jose | USA | 102635 | city:na |
| Stuttgart | Deutschland | 634830 | city:emea |
| Zürich | Schweiz | 415367 | city:capital<br>city:emea |
