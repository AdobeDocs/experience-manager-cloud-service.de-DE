---
title: Verwendung von GraphQL mit AEM - Beispielinhalt und Abfragen
description: GraphQL mit AEM - Beispielinhalt und Abfragen.
translation-type: tm+mt
source-git-commit: da8fcf1288482d406657876b5d4c00b413461b21
workflow-type: tm+mt
source-wordcount: '1298'
ht-degree: 6%

---


# Verwendung von GraphQL mit AEM - Beispielinhalt und Abfragen {#learn-graphql-with-aem-sample-content-queries}

>[!CAUTION]
>
>Die AEM GraphQL-API für den Versand &quot;Inhaltsfragmente&quot;steht auf Anfrage zur Verfügung.
>
>Bitte wenden Sie sich an [Adobe Support](https://experienceleague.adobe.com/?lang=en&amp;support-solution=General#support), um die API für Ihre AEM als Cloud Service-Programm zu aktivieren.

Für die ersten Schritte mit GraphQL-Abfragen und wie sie mit AEM Inhaltsfragmenten funktionieren, ist es hilfreich, einige praktische Beispiele zu sehen.

Hilfe hierzu finden Sie unter

* A [Muster-Inhaltsfragmentstruktur](#content-fragment-structure-graphql)

* Und einige [Beispiel-GraphQL-Abfragen](#graphql-sample-queries) basieren auf der Fragmentstruktur des Beispielinhalts (Inhaltsfragmentmodelle und zugehörige Inhaltsfragmente).

## GraphQL für AEM - Einige Erweiterungen {#graphql-some-extensions}

Die Grundfunktion von Abfragen mit GraphQL für AEM Einhaltung der Standard GraphQL Spezifikation. Für GraphQL-Abfragen mit AEM gibt es einige Erweiterungen:

* Wenn Sie ein einzelnes Ergebnis benötigen:
   * den Modellnamen verwenden; eg-Stadt

* Wenn Sie eine Liste der Ergebnisse erwarten:
   * dem Modellnamen &quot;Liste&quot;hinzufügen; zum Beispiel `cityList`

* Wenn Sie ein logisches ODER verwenden möchten:
   * Verwenden Sie &quot;_logOp: OR&quot;

* Logisches UND existiert auch, ist jedoch (oft) implizit

* Sie können Abfragen zu Feldnamen vornehmen, die den Feldern im Inhaltsfragmentmodell entsprechen.

* Zusätzlich zu den Feldern Ihres Modells gibt es einige systemgenerierte Felder (denen ein Unterstrich vorangestellt wird):

   * Für Inhalte:

      * `_locale` : die Sprache offen zu legen; auf Basis von Language Manager

      * `_metadata` : , um Metadaten für Ihr Fragment anzuzeigen

      * `_path` : den Pfad zu Ihrer Inhaltsfragment im Repository

      * `_references` : Verweise anzuzeigen; einschließlich Inline-Verweise im Rich Text Editor

      * `_variations` : um bestimmte Variationen in Ihrem Inhaltsfragment anzuzeigen
   * Und Operationen:

      * `_operator` : spezifische Betreiber anwenden;  `EQUALS`,  `EQUALS_NOT`,  `GREATER_EQUAL`,  `LOWER`,  `CONTAINS`,

      * `_apply` : Anwendung spezifischer Bedingungen; zum Beispiel   `AT_LEAST_ONCE`

      * `_ignoreCase` : die Groß-/Kleinschreibung bei der Abfrage ignorieren


* GraphQL-Vereinigungen werden unterstützt:

   * Verwenden Sie `...on`


## Eine Beispielinhaltsfragmentstruktur zur Verwendung mit GraphQL {#content-fragment-structure-graphql}

Ein einfaches Beispiel:

* Ein oder mehrere [Muster-Inhaltsfragmentmodelle](#sample-content-fragment-models-schemas) - bilden die Grundlage für die GraphQL-Schema

* [Beispielinhalt-](#sample-content-fragments) Fragmente basierend auf den oben genannten Modellen

### Musterinhalt-Fragmentmodelle (Schema) {#sample-content-fragment-models-schemas}

Für die Abfragen mit Beispielen verwenden wir die folgenden Inhaltsmodelle und deren Zusammenhänge (Referenzen ->):

* [Firma](#model-company)
->  [Person](#model-person)
    ->  [Prämie](#model-award)

* [Ort](#model-city)

#### Unternehmen {#model-company}

Die Grundfelder, die die Firma definieren, sind:

| Feldname | Datentyp | Verweis  |
|--- |--- |--- |
| Name der Firma | Einzeilentext |  |
| CEO | Fragmentverweis (Single) | [Person](#model-person) |
| ArbeitnehmerInnen | Fragmentverweis (multifield) | [Person](#model-person) |

#### Person {#model-person}

Die Felder, die eine Person definieren, die auch Angestellte sein kann:

| Feldname | Datentyp | Verweis  |
|--- |--- |--- |
| Name | Einzeilentext |  |
| Vorname | Einzeilentext |  |
| Awards | Fragmentverweis (multifield) | [Award](#model-award) |

#### Award {#model-award}

Die Felder, in denen eine Auszeichnung definiert wird, sind:

| Feldname | Datentyp | Verweis  |
|--- |--- |--- |
| Tastenkombination/ID | Einzeilentext |  |
| Titel | Einzeilentext |  |

#### Ort {#model-city}

Die Felder zur Definition einer Stadt sind:

| Feldname | Datentyp | Verweis  |
|--- |--- |--- |
| Name | Einzeilentext |  |
| Land | Einzeilentext |  |
| Bevölkerung | Zahl |  |
| Kategorien | Tags |  |

### Beispielinhalt-Fragmente {#sample-content-fragments}

Die folgenden Fragmente werden für das entsprechende Modell verwendet.

#### Unternehmen {#fragment-company}

| Name der Firma | CEO | ArbeitnehmerInnen |
|--- |--- |--- |
| Apple | Aufträge verschieben | Duke Marsh<br>Max Caulfield |
|  Little Pony Inc. | Adam Smith | Lara Croft<br>Cutter Slade |
| NextStep Inc. | Aufträge verschieben | Joe Smith<br>Abe Lincoln |

#### Person {#fragment-person}

| Name | Vorname | Awards |
|--- |--- |--- |
| Lincoln |  Abe |  |
| Smith | Adam |   |
| Sklade |  Cutter |  Gameblitz<br>Gamestar |
| Marsh |  Duke |   |   |
|  Smith |  Joe |   |
| Überlappend |  Lara | Gamestar |
| Caulfield |  Maximal |  Gameblitz |
|  Aufträge |  Steve |   |

#### Award {#fragment-award}

| Tastenkombination/ID | Titel |
|--- |--- |
| GB | Gameblitz |
|  GS | Gamestar |
|  OSC | Oscar |

#### Ort {#fragment-city}

| Name | Land | Bevölkerung | Kategorien |
|--- |--- |--- |--- |
| Basel | Schweiz | 172258 | Ort:emea |
| Berlin | Deutschland | 3669491 | city:capital<br>city:emea |
| Bukarest | Rumänien | 1821000 |  city:capital<br>city:emea |
| San Francisco |  USA |  883306 |  Ort:Strand<br>Stadt:na |
| San José |  USA |  102635 |  Ort:na |
| Stuttgart |  Deutschland |  634830 |  Ort:emea |
|  Zürich |  Schweiz |  415367 |  city:capital<br>city:emea |

## GraphQL - Abfragen mit Beispielinhalt-Fragmentstruktur {#graphql-sample-queries-sample-content-fragment-structure}

In den Beispielergebnissen finden Sie Abfragen zu Abbildungen der Abfragen zum Erstellen sowie Beispielergebnisse.

>[!NOTE]
>
>Abhängig von Ihrer Instanz können Sie direkt auf die [Grafik *i* QL-Schnittstelle zugreifen, die in AEM GraphQL API](/help/assets/content-fragments/graphql-api-content-fragments.md#graphiql-interface) enthalten ist, um Abfragen zu senden und zu testen.
>
>Beispiel: `http://localhost:4502/content/graphiql.html`

### Beispielversion - Alle verfügbaren Schema und Datentypen {#sample-all-schemes-datatypes}

Dadurch werden alle Typen für alle verfügbaren Schema zurückgegeben.

**Abfrage**

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

### Abfrage des Beispiels - Vollständige Angaben zum CEO und zu den Mitarbeitern einer Firma{#sample-full-details-company-ceos-employees}

Anhand der Struktur der verschachtelten Fragmente liefert diese Abfrage alle Details zum CEO einer Firma und allen Mitarbeitern.

**Abfrage**

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

### Abfrage des Beispiels - Alle Informationen zu allen Städten {#sample-all-information-all-cities}

Um alle Informationen über alle Städte abzurufen, können Sie die einfache Abfrage verwenden:
**BeispielAbfrage**

```xml
{
  cityList {
    items
  }
}
```

Wenn die Ausführung ausgeführt wird, erweitert das System automatisch die Abfrage, um alle Felder einzuschließen:

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

### Abfrage des Beispiels - Namen aller Städte {#sample-names-all-cities}

Dies ist eine unkomplizierte Abfrage, die `name`aller Einträge im `city`Schema zurückzugeben.

**Abfrage**

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

### Beispiel-Abfrage - Ein Einzelstadtfragment {#sample-single-city-fragment}

Dies ist eine Abfrage, um die Details zu einem einzelnen Fragment an einem bestimmten Speicherort im Repository zurückzugeben.

**Abfrage**

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

### Abfrage des Beispiels - Alle Städte mit einer benannten Variante {#sample-cities-named-variation}

Wenn Sie eine neue Variante mit dem Namen &quot;Berlin Center&quot; (`berlin_centre`) für das `city` Berlin erstellen, können Sie eine Abfrage verwenden, um Details zur Variante zurückzugeben.

**Abfrage**

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

### Abfrage des Beispiels - Alle Personen mit dem Namen &quot;Aufträge&quot;oder &quot;Schmied&quot; {#sample-all-persons-jobs-smith}

Dadurch werden alle `persons` für alle mit dem Namen `Jobs`oder `Smith` gefiltert.

**Abfrage**

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

### Abfrage des Beispiels - Alle Personen ohne den Namen &quot;Aufträge&quot; {#sample-all-persons-not-jobs}

Dadurch werden alle `persons` für alle mit dem Namen `Jobs`oder `Smith` gefiltert.

**Abfrage**

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

### Abfrage - Alle Städte in Deutschland oder der Schweiz mit einer Bevölkerung zwischen 400000 und 9999999 {#sample-all-cities-d-ch-population}

Hier wird eine Kombination von Feldern gefiltert. Ein `AND` (implizit) wird verwendet, um den `population`Bereich auszuwählen, während ein `OR` (explizit) zur Auswahl der erforderlichen Städte verwendet wird.

**Abfrage**

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

### BeispielAbfrage - Alle Städte mit SAN im Namen, unabhängig davon, ob {#sample-all-cities-san-ignore-case}

Diese Abfrage durchsucht alle Städte, die im Namen `SAN` stehen, unabhängig von der jeweiligen Sachlage.

**Abfrage**

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

### Beispieldatei - Abfrage auf einem Array mit einem Element, das mindestens einmal vorkommen muss{#sample-array-item-occur-at-least-once}

Diese Abfrage Filter auf einem Array mit einem Element (`city:na`), das mindestens einmal auftreten muss.

**Abfrage**

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

### Beispiel-Abfrage - Filterung nach einem exakten Array-Wert {#sample-array-exact-value}

Diese Abfrage Filter auf einen exakten Array-Wert.

**Abfrage**

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

### Abfrage für verschachtelte Inhaltsfragmente - Alle Firmen, bei denen mindestens ein Mitarbeiter mit dem Namen &quot;Smith&quot; {#sample-companies-employee-smith}

Diese Abfrage veranschaulicht die Filterung nach `person` von `name` &quot;Smith&quot;, wobei Informationen aus zwei verschachtelten Fragmenten - `company` und `employee` zurückgegeben werden.

**Abfrage**

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

### Abfrage für verschachtelte Inhaltsfragmente - Alle Firmen, in denen alle Mitarbeiter die Auszeichnung &quot;Gamestar&quot;erhalten haben{#sample-all-companies-employee-gamestar-award}

Diese Abfrage veranschaulicht die Filterung von drei verschachtelten Fragmenten - `company`, `employee` und `award`.

**Abfrage**

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

### Beispiel-Abfrage für Metadaten - Liste der Metadaten für Auszeichnungen mit dem Titel GB {#sample-metadata-awards-gb}

Diese Abfrage veranschaulicht die Filterung von drei verschachtelten Fragmenten - `company`, `employee` und `award`.

**Abfrage**

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

## Beispielprojekte für Abfragen mit dem WKND-Projekt {#sample-queries-using-wknd-project}

Diese Abfragen basieren auf dem WKND-Projekt.

>[!NOTE]
>
>Da die Ergebnisse umfangreich sein können, werden sie hier nicht reproduziert.

### Abfrage für alle Inhaltsfragmente eines bestimmten Modells mit den angegebenen Eigenschaften {#sample-wknd-all-model-properties}

Diese Abfrage des Beispiels fragt ab:

* für alle Inhaltsfragmente des Typs `article`
* mit den Eigenschaften `path`und `author`.

**Abfrage**

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

### Abfrage für Muster für Metadaten {#sample-wknd-metadata}

Diese Abfrage durchläuft:

* für alle Inhaltsfragmente des Typs `adventure`
* metadata

**Abfrage**

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

### Abfrage eines Beispiels für ein einzelnes Inhaltsfragment eines bestimmten Modells {#sample-wknd-single-content-fragment-of-given-model}

Diese Abfrage des Beispiels fragt ab:

* für ein einzelnes Inhaltsfragment eines bestimmten Modells
* für alle Inhaltsformate:
   * HTML
   * Markdown
   * Nur Text
   * JSON

**Abfrage**

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

### Abfrage eines Beispiels für ein verschachteltes Inhaltsfragment - Einzelmodelltyp{#sample-wknd-nested-fragment-single-model}

**Abfrage**

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

### Abfrage für ein verschachteltes Inhaltsfragment - Modelltyp mit mehreren Varianten{#sample-wknd-nested-fragment-multiple-model}

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

### Abfrage eines Beispiels für ein Inhaltsfragment eines bestimmten Modells mit einem Inhaltsverweis{#sample-wknd-fragment-specific-model-content-reference}

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

### Abfrage für mehrere Inhaltsfragmente mit vorab abgerufenen Referenzen {#sample-wknd-multiple-fragments-prefetched-references}

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
  }
}
```

### Abfrage eines Beispiels für eine einzelne Inhaltsfragmentvariation eines bestimmten Modells {#sample-wknd-single-fragment-given-model}

**Abfrage**

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

### Abfrage für mehrere Inhaltsfragmente eines bestimmten Gebietsschemas {#sample-wknd-multiple-fragments-given-locale}

**Abfrage**

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

### Abfrage für ein einzelnes Inhaltsfragment mit RTE Inline-Verweis {#sample-wknd-single-fragment-rte-inline-reference}

**Abfrage**

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

### Abfrage eines Beispiels für eine benannte Variation mehrerer Inhaltsfragmente eines bestimmten Modells {#sample-wknd-variation-multiple-fragment-given-model}

**Abfrage**

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
