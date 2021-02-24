---
title: Verwendung von GraphQL mit AEM – Beispielinhalt und Abfragen
description: Verwendung von GraphQL mit AEM – Beispielinhalt und Abfragen.
translation-type: tm+mt
source-git-commit: 6a60238b13d66ea2705063670295a62e3cbf6255
workflow-type: tm+mt
source-wordcount: '1707'
ht-degree: 68%

---


# Verwendung von GraphQL mit AEM – Beispielinhalt und Abfragen {#learn-graphql-with-aem-sample-content-queries}

>[!NOTE]
>
>Diese Seite sollte zusammen gelesen werden mit:
>
>* [Inhaltsfragmente](/help/assets/content-fragments/content-fragments.md)
>* [Inhaltsfragmentmodelle](/help/assets/content-fragments/content-fragments-models.md)
>* [AEM GraphQL-API zur Verwendung mit Inhaltsfragmenten](/help/assets/content-fragments/graphql-api-content-fragments.md)


Um mit GraphQL-Abfragen zu beginnen und wie sie mit AEM-Inhaltsfragmenten funktionieren, ist es hilfreich, einige praktische Beispiele zu sehen.

Sehen Sie dazu:

* eine [Beispielstruktur für Inhaltsfragmente](#content-fragment-structure-graphql)

* und einige [GraphQL-Beispielabfragen](#graphql-sample-queries), die auf der Beispielstruktur für Inhaltsfragmente basieren (Inhaltsfragmentmodelle und verwandte Inhaltsfragmente).

## GraphQL für AEM - Zusammenfassung der Erweiterungen {#graphql-extensions}

Die grundlegende Funktionsweise von Abfragen mit GraphQL für AEM entspricht der Standard-GraphQL-Spezifikation. Für GraphQL-Abfragen mit AEM gibt es einige Erweiterungen:

* Wenn Sie ein einzelnes Ergebnis benötigen:
   * Verwenden Sie den Modellnamen, z. B. „city“

* Wenn Sie eine Ergebnisliste erwarten:
   * dem Modellnamen `List` hinzufügen; zum Beispiel `cityList`
   * Siehe [Beispielseite - Alle Informationen zu allen Abfragen](#sample-all-information-all-cities)

* Wenn Sie ein logisches ODER verwenden möchten:
   * Verwenden Sie ` _logOp: OR`
   * Siehe [Beispieldaten - Alle Abfragen mit dem Namen &quot;Aufträge&quot;oder &quot;Schmidt&quot;](#sample-all-persons-jobs-smith)

* Es gibt ebenfalls ein logisches UND, es ist aber (oft) implizit.

* Sie können Feldnamen abfragen, die den Feldern im Inhaltsfragmentmodell entsprechen.
   * Siehe [Beispieldatei - Vollständige Abfrage der Geschäftsführer und Mitarbeiter einer Firma](#sample-full-details-company-ceos-employees)

* Zusätzlich zu den Feldern Ihres Modells gibt es einige systemgenerierte Felder (vor dem Unterstrich):

   * Für Inhalte:

      * `_locale` : die Sprache anzeigen; basierend auf dem Language Manager
         * Siehe [Abfrage für mehrere Inhaltsfragmente eines bestimmten Gebietsschemas](#sample-wknd-multiple-fragments-given-locale)
      * `_metadata` : Metadaten für Ihr Fragment anzeigen
         * Siehe [Beispieldatei-Abfrage für Metadaten - Liste der Metadaten für Prämien mit dem Titel GB](#sample-metadata-awards-gb)
      * `_model` : Suchen nach einem Inhaltsfragmentmodell zulassen (Pfad und Titel)
         * Siehe [Abfrage eines Inhaltsfragmentmodells eines Modells](#sample-wknd-content-fragment-model-from-model)
      * `_path` : den Pfad zu Ihrem Inhaltsfragment im Repository
         * Siehe [Abfrage eines Beispiels - Ein einzelnes spezifisches Stadtfragment](#sample-single-specific-city-fragment)
      * `_reference` : Verweise anzeigen; einschließlich Inline-Verweise im Rich-Text-Editor
         * Siehe [Abfrage für mehrere Inhaltsfragmente mit vorab abgerufenen Referenzen](#sample-wknd-multiple-fragments-prefetched-references)
      * `_variation` : bestimmte Varianten in Ihrem Inhaltsfragment anzeigen
         * Weitere Informationen finden Sie unter [Beispielabfrage – Alle Städte mit einer gegebenen Variante](#sample-cities-named-variation)
   * Und Operationen:

      * `_operator` : bestimmte Operatoren anwenden; `EQUALS`, `EQUALS_NOT`, `GREATER_EQUAL`, `LOWER`, `CONTAINS`
         * Siehe [Beispieldaten - Alle Abfragen ohne den Namen &quot;Aufträge&quot;](#sample-all-persons-not-jobs)
      * `_apply` : bestimmte Bedingungen anwenden; zum Beispiel `AT_LEAST_ONCE`
         * Siehe [Beispielfilter - Abfrage eines Arrays mit einem Element, das mindestens einmal auftreten muss](#sample-array-item-occur-at-least-once)
      * `_ignoreCase` : die Groß-/Kleinschreibung bei der Abfrage ignorieren
         * Siehe [BeispielAbfrage - Alle Städte mit SAN im Namen, unabhängig von case](#sample-all-cities-san-ignore-case)









* GraphQL-Vereinigungstypen werden unterstützt:

   * Verwenden Sie `... on`
      * Siehe [BeispielAbfrage für ein Inhaltsfragment eines bestimmten Modells mit einem Inhaltsverweis](#sample-wknd-fragment-specific-model-content-reference)

## GraphQL – Beispielabfragen unter Verwendung der Beispielstruktur für Inhaltsfragmente {#graphql-sample-queries-sample-content-fragment-structure}

In diesen Beispielergebnissen finden Sie Abfragen zur Veranschaulichung von Abfragen und Beispielergebnissen.

>[!NOTE]
>
>Abhängig von Ihrer Instanz können Sie direkt auf die in der [AEM GraphQL-API enthaltene Graph *i* QL-Schnittstelle](/help/assets/content-fragments/graphql-api-content-fragments.md#graphiql-interface) zugreifen, um Abfragen zu senden und zu testen.
>
>Beispiel: `http://localhost:4502/content/graphiql.html`

>[!NOTE]
>
>Die Abfragen basieren auf der Struktur des Musterinhaltsfragments für die Verwendung mit GraphQL](#content-fragment-structure-graphql)[

### Beispielabfrage – Alle verfügbaren Schemas und Datentypen {#sample-all-schemes-datatypes}

Dadurch werden alle `types` für alle verfügbaren Schema zurückgegeben.

**Beispielabfrage**

```xml
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

```xml
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

```xml
{
  cityList {
    items
  }
}
```

Bei der Ausführung erweitert das System die Abfrage automatisch um alle Felder:

```xml
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

```xml
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

Dies ist eine unkomplizierte Abfrage, um den `name` aller Einträge im `city`-Schema zurückzugeben.

**Beispielabfrage**

```xml
query {
  cityList {
    items {
      name
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

### Beispiel-Abfrage - Ein einzelnes spezifisches Stadtfragment {#sample-single-specific-city-fragment}

Dies ist eine Abfrage, um die Details eines einzelnen Fragmenteintrags an einem bestimmten Speicherort im Repository zurückzugeben.

**Beispielabfrage**

```xml
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

```xml
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

### Beispielabfrage – Alle Städte mit einer gegebenen Variante {#sample-cities-named-variation}

Wenn Sie eine neue Variante mit dem Namen „Berlin Centre“ (`berlin_centre`) für `city` Berlin erstellen, können Sie eine Abfrage verwenden, um Details zur Variante zurückzugeben.

**Beispielabfrage**

```xml
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

```xml
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

### Beispielabfrage – Vollständige Details des CEO und der Mitarbeiter eines Unternehmens {#sample-full-details-company-ceos-employees}

Unter Verwendung der Struktur der verschachtelten Fragmente gibt diese Abfrage die vollständigen Details des CEO eines Unternehmens und aller seiner Mitarbeiter zurück.

**Beispielabfrage**

```xml
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

```xml
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

### Beispielabfrage – - Alle Personen mit dem Namen „Jobs“ oder „Smith“ {#sample-all-persons-jobs-smith}

Dadurch werden alle `persons` mit dem Namen `Jobs`oder `Smith` gefiltert.

**Beispielabfrage**

```xml
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

```xml
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

### Beispielabfrage – Alle Personen, die nicht den Namen „Jobs“ haben {#sample-all-persons-not-jobs}

Dadurch werden alle `persons` mit dem Namen `Jobs`oder `Smith` gefiltert.

**Beispielabfrage**

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

**Beispielergebnisse**

```xml
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

### Beispielabfrage – Alle Städte in Deutschland oder der Schweiz mit einer Einwohnerzahl zwischen 400000 und 999999 {#sample-all-cities-d-ch-population}

Hier wird eine Kombination von Feldern gefiltert. Ein `AND` (implizit) wird verwendet, um den `population`-Bereich auszuwählen, während ein `OR` (explizit) zur Auswahl der erforderlichen Städte verwendet wird.

**Beispielabfrage**

```xml
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

```xml
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

```xml
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

```xml
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

```xml
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

```xml
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

```xml
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

```xml
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

### Beispielabfrage für verschachtelte Inhaltsfragmente – Alle Unternehmen mit mindestens einem Mitarbeiter mit dem Namen „Smith“ {#sample-companies-employee-smith}

Diese Abfrage veranschaulicht die Filterung nach `person` von `name` „Smith“, wobei Informationen aus zwei verschachtelten Fragmenten – `company` und `employee` – zurückgegeben werden.

**Beispielabfrage**

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

**Beispielergebnisse**

```xml
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

```xml
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

```xml
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

```xml
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

```xml
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

Diese Beispielabfragen basieren auf dem WKND-Projekt. Dies hat Folgendes:

* Inhaltsfragmentmodelle verfügbar unter:
   `http://<hostname>:<port>/libs/dam/cfm/models/console/content/models.html/conf/wknd`

* Inhaltsfragmente (und andere Inhalte) verfügbar unter:
   `http://<hostname>:<port>/assets.html/content/dam/wknd/en`

>[!NOTE]
>
>Da die Ergebnisse sehr umfangreich sein können, werden sie hier nicht wiedergegeben.

### Beispielabfrage für alle Inhaltsfragmente eines bestimmten Modells mit den angegebenen Eigenschaften {#sample-wknd-all-model-properties}

Diese Beispielabfrage untersucht:

* alle Inhaltsfragmente des Typs `article`
* mit den Eigenschaften `path`und `author`.

**Beispielabfrage**

```xml
{
  articleList {
    items {
      _path
      author
    }
  }
}
```

### Beispielabfrage für Metadaten {#sample-wknd-metadata}

Diese Abfrage untersucht:

* alle Inhaltsfragmente des Typs `adventure`
* metadata

**Beispielabfrage**

```xml
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

* für ein einzelnes Inhaltsfragment des Typs `article` an einem bestimmten Pfad
   * innerhalb dieses Rahmens alle Inhaltsformate:
      * HTML
      * Markdown
      * Nur Text
      * JSON

**Beispielabfrage**

```xml
{
  articleByPath (_path: "/content/dam/wknd/en/magazine/alaska-adventure/alaskan-adventures") {
    item {
        _path
        author
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

### Abfrage eines Beispiels für ein Inhaltsfragmentmodell aus einem Modell {#sample-wknd-content-fragment-model-from-model}

Diese Beispielabfrage untersucht:

* für ein einzelnes Inhaltsfragment
   * Details des zugrunde liegenden Inhaltsfragmentmodells

**Beispielabfrage**

```xml
{
  adventureByPath(_path: "/content/dam/wknd/en/adventures/riverside-camping-australia/riverside-camping-australia") {
    item {
      _path
      adventureTitle
      _model {
        _path
        title
      }
    }
  }
}
```

### Beispielabfrage für ein verschachteltes Inhaltsfragment – Typ mit einem Modell {#sample-wknd-nested-fragment-single-model}

Diese Abfrage untersucht:

* für ein einzelnes Inhaltsfragment des Typs `article` an einem bestimmten Pfad
   * in diesem Abschnitt der Pfad und der Autor des referenzierten (verschachtelten) Fragments

>[!NOTE]
>
>Das Feld `referencearticle` hat den Datentyp `fragment-reference`.

**Beispielabfrage**

```xml
{
  articleByPath (_path: "/content/dam/wknd/en/magazine/skitouring/skitouring") {
    item {
        _path
        author
        referencearticle {
          _path
          author
      }
    }
  }
}
```

### Beispielabfrage für ein verschachteltes Inhaltsfragment – Typ mit mehreren Modellen {#sample-wknd-nested-fragment-multiple-model}

Diese Abfrage untersucht:

* für mehrere Inhaltsfragmente des Typs `bookmark`
   * mit Fragmentverweisen auf andere Fragmente der spezifischen Modelltypen `article` und `adventure`

>[!NOTE]
>
>Das Feld `fragments` enthält den Datentyp `fragment-reference`, wobei die Modelle `Article`, `Adventure` ausgewählt sind.

```xml
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

### Abfrage eines Beispiels für ein Inhaltsfragment eines bestimmten Modells mit Inhaltsverweisen{#sample-wknd-fragment-specific-model-content-reference}

Es gibt zwei Varianten dieser Abfrage:

1. So geben Sie alle Inhaltsverweise zurück.
1. So geben Sie die spezifischen Inhaltsreferenzen des Typs `attachments` zurück.

Diese Abfragen durchlaufen:

* für mehrere Inhaltsfragmente des Typs `bookmark`
   * mit Inhaltsverweisen auf andere Fragmente

#### Beispielabfrage für mehrere Inhaltsfragmente mit vorab abgerufenen Verweisen {#sample-wknd-multiple-fragments-prefetched-references}

Die folgende Abfrage gibt alle Inhaltsverweise mit `_references` zurück:

```xml
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

#### Abfrage für mehrere Inhaltsfragmente mit Anhängen {#sample-wknd-multiple-fragments-attachments}

Die folgende Abfrage gibt alle `attachments` - ein bestimmtes Feld (Untergruppe) des Typs `content-reference` zurück:

>[!NOTE]
>
>Für das Feld `attachments` ist der Datentyp `content-reference` ausgewählt, wobei verschiedene Formulare ausgewählt sind.

```xml
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

### Beispielabfrage für ein einzelnes Inhaltsfragment mit RTE-Inline-Verweis {#sample-wknd-single-fragment-rte-inline-reference}

Diese Abfrage untersucht:

* für ein einzelnes Inhaltsfragment des Typs `bookmark` an einem bestimmten Pfad
   * in diesem Fall RTE Inline-Referenzen

>[!NOTE]
>
>Die Inline-Referenzen von RTE werden in `_references` hydriert.

**Beispielabfrage**

```xml
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

* für ein einzelnes Inhaltsfragment des Typs `article` an einem bestimmten Pfad
   * innerhalb dessen die Daten im Zusammenhang mit der Änderung: `variation1`

**Beispielabfrage**

```xml
{
  articleByPath (_path: "/content/dam/wknd/en/magazine/alaska-adventure/alaskan-adventures", variation: "variation1") {
    item {
      _path
      author
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

### Beispielabfrage für eine gegebene Variante mehrerer Inhaltsfragmente eines bestimmten Modells {#sample-wknd-variation-multiple-fragment-given-model}

Diese Abfrage untersucht:

* für Inhaltsfragmente des Typs `article` mit einer bestimmten Variante: `variation1`

**Beispielabfrage**

```xml
{
  articleList (variation: "variation1") {
    items {
      _path
      author
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

### Beispielabfrage für mehrere Inhaltsfragmente eines bestimmten Gebietsschemas {#sample-wknd-multiple-fragments-given-locale}

Diese Abfrage untersucht:

* für Inhaltsfragmente des Typs `article` innerhalb des Gebietsschemas `fr`

**Beispielabfrage**

```xml
{ 
  articleList (_locale: "fr") {
    items {
      _path
      author
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

## Die Struktur des Beispielinhaltsfragments (verwendet mit GraphQL) {#content-fragment-structure-graphql}

Die Abfragen basieren auf der folgenden Struktur, die Folgendes verwendet:

* Ein oder mehrere [Beispielmodelle für Inhaltsfragmente](#sample-content-fragment-models-schemas) bilden die Grundlage für die GraphQL-Schemas

* [Beispielinhaltsfragmente](#sample-content-fragments) basierend auf den oben genannten Modellen

### Beispielmodelle für Inhaltsfragmente (Schemas) {#sample-content-fragment-models-schemas}

Für die Beispielabfragen verwenden wir die folgenden Inhaltsmodelle und ihre Wechselbeziehungen (Verweise ->):

* [Unternehmen](#model-company)
-> [Person](#model-person)
    -> [Auszeichnung](#model-award)

* [Stadt](#model-city)

#### Unternehmen {#model-company}

Die grundlegenden Felder, die das Unternehmen definieren, sind:

| Feldname | Datentyp | Verweis |
|--- |--- |--- |
| Unternehmensname | Einzeilentext |  |
| CEO | Fragmentverweis (Einzelfeld) | [Person](#model-person) |
| Mitarbeiter | Fragmentverweis (Mehrfeld) | [Person](#model-person) |

#### Person {#model-person}

Die Felder, die eine Person definieren, die auch ein Mitarbeiter sein kann:

| Feldname | Datentyp | Verweis |
|--- |--- |--- |
| Name | Einzeilentext |  |
| Vorname | Einzeilentext |  |
| Auszeichnungen | Fragmentverweis (Mehrfeld) | [Auszeichnung](#model-award) |

#### Auszeichnung {#model-award}

Die Felder, die eine Auszeichnung definieren, sind:

| Feldname | Datentyp | Verweis |
|--- |--- |--- |
| Kürzel/Kennung | Einzeilentext |  |
| Titel | Einzeilentext |  |

#### Stadt {#model-city}

Die Felder zur Definition einer Stadt sind:

| Feldname | Datentyp | Verweis |
|--- |--- |--- |
| Name | Einzeilentext |  |
| Land | Einzeilentext |  |
| Einwohnerzahl | Zahl |  |
| Kategorien | Tags |  |

### Beispielinhaltsfragmente {#sample-content-fragments}

Die folgenden Fragmente werden für das entsprechende Modell verwendet.

#### Unternehmen {#fragment-company}

| Unternehmensname | CEO | Mitarbeiter |
|--- |--- |--- |
| Apple | Steve Jobs | Duke Marsh<br>Max Caulfield |
|  Little Pony Inc. | Adam Smith | Lara Croft<br>Cutter Slade |
| NextStep Inc. | Aufträge verschieben | Joe Smith<br>Abe Lincoln |

#### Person {#fragment-person}

| Name | Vorname | Auszeichnungen |
|--- |--- |--- |
| Lincoln |  Abe |  |
| Smith | Adam |   |
| Slade |  Cutter |  Gameblitz<br>Gamestar |
| Marsh |  Duke |   |   |
|  Smith |  Joe |   |
| Croft |  Lara | Gamestar |
| Caulfield |  Maximal |  Gameblitz |
|  Aufträge |  Steve |   |

#### Auszeichnung {#fragment-award}

| Kürzel/Kennung | Titel |
|--- |--- |
| GB | Gameblitz |
|  GS | Gamestar |
|  OSC | Oscar |

#### Stadt {#fragment-city}

| Name | Land | Einwohnerzahl | Kategorien |
|--- |--- |--- |--- |
| Basel | Schweiz | 172258 | city:emea |
| Berlin | Deutschland | 3669491 | city:capital<br>city:emea |
| Bukarest | Rumänien | 1821000 |  city:capital<br>city:emea |
| San Francisco |  USA |  883306 |  city:beach<br>city:na |
| San José |  USA |  102635 |  city:na |
| Stuttgart |  Deutschland |  634830 |  city:emea |
|  Zürich |  Schweiz |  415367 |  city:capital<br>city:emea |
