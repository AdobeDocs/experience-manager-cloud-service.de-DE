---
title: Content Versand mit Inhaltsfragmenten mit dem Adobe Experience Manager als Cloud Service GraphQL API
description: Erfahren Sie, wie Sie Inhaltsfragmente in Adobe Experience Manager (AEM) als Cloud Service mit der AEM GraphQL API für Headless Content Versand verwenden.
translation-type: tm+mt
source-git-commit: da8fcf1288482d406657876b5d4c00b413461b21
workflow-type: tm+mt
source-wordcount: '2506'
ht-degree: 2%

---


# AEM GraphQL API zur Verwendung mit Inhaltsfragmenten {#graphql-api-for-use-with-content-fragments}

>[!CAUTION]
>
>Die AEM GraphQL-API für den Versand &quot;Inhaltsfragmente&quot;steht auf Anfrage zur Verfügung.
>
>Bitte wenden Sie sich an [Adobe Support](https://experienceleague.adobe.com/?lang=en&amp;support-solution=General#support), um die API für Ihre AEM als Cloud Service-Programm zu aktivieren.

Die Adobe Experience Manager als Cloud Service (AEM) GraphQL-API, die mit Inhaltsfragmenten verwendet wird, basiert stark auf der Standard-GraphQL-API.

Die Verwendung der GraphQL API in AEM ermöglicht den effizienten Versand von Inhaltsfragmenten an JavaScript-Clients in CMS-Implementierungen ohne Kopfzeileneinstellungen:

* Vermeiden von iterativen API-Anfragen wie bei REST,
* Gewährleistung, dass der Versand auf die spezifischen Anforderungen beschränkt ist,
* Ermöglicht den Massenzugriff auf genau das, was für die Wiedergabe als Antwort auf eine einzige API-Abfrage erforderlich ist.

## Die GraphQL API {#graphql-api}

*&quot;GraphQL ist eine Datensprache und -spezifikation, die 2012 intern von Facebook entwickelt wurde, bevor sie 2015 öffentlich zugänglich gemacht wurde. Es bietet eine Alternative zu REST-basierten Architekturen mit dem Ziel, die Entwicklerproduktivität zu erhöhen und die Datenmenge zu minimieren. GraphQL wird in der Produktion von Hunderten von Organisationen aller Größen verwendet...&quot;* Siehe [GraphQL Foundation](https://foundation.graphql.org/).

Weitere Informationen zur GraphQL API finden Sie in den folgenden Abschnitten (unter anderem):

* Bei [graphql.org](https://graphql.org):

   * [Einführung in GraphQL](https://graphql.org/learn)

   * [GraphQL-Spezifikation](http://spec.graphql.org/)

* Unter [graphql.com](https://graphql.com):

   * [Guides](https://www.graphql.com/guides/)

   * [Tutorials](https://www.graphql.com/tutorials/)

   * [Fallstudien](https://www.graphql.com/case-studies/)

Die GraphQL für AEM Implementierung basiert auf der standardmäßigen GraphQL Java Library. Siehe:

* [graphQL.org - Java](https://graphql.org/code/#java)

* [GraphQL Java bei GitHub](https://github.com/graphql-java)

## GraphiQL-Schnittstelle {#graphiql-interface}

AEM Grafik-API enthält eine Implementierung der Standard-Schnittstelle [GraphiQL](https://graphql.org/learn/serving-over-http/#graphiql). Auf diese Weise können Sie Abfragen direkt eingeben und testen.

Beispiel:

* `http://localhost:4502/content/graphiql.html`

Dazu gehören Funktionen wie Syntaxhervorhebung, automatische Vervollständigung und automatische Empfehlung sowie ein Verlauf und eine Online-Dokumentation:

![GraphiQL-](assets/cfm-graphiql-interface.png "SchnittstelleGraphiQL-Schnittstelle")

## Anwendungsfälle für Authoring- und Veröffentlichungseinstellungen {#use-cases-author-publish-environments}

Die Anwendungsfälle können vom Typ der AEM als Cloud Service-Umgebung abhängig sein:

* Umgebung veröffentlichen; verwendet, um
   * Daten zur Abfrage der JS-Anwendung (Standard-Anwendungsfall)

* Umgebung des Verfassers; verwendet, um
   * Abfragen für &quot;Content-Management&quot;:
      * GraphQL in AEM als Cloud Service ist derzeit eine schreibgeschützte API.
      * Die REST-API kann für CR(u)D-Vorgänge verwendet werden.

## Schema-Generierung {#schema-generation}

GraphQL ist eine stark typisierte API, was bedeutet, dass die Daten klar strukturiert und nach Typ geordnet sein müssen.

Die GraphQL-Spezifikation enthält eine Reihe von Richtlinien zum Erstellen einer robusten API zum Abfragen von Daten in einer bestimmten Instanz. Dazu muss ein Client das [Schema](#schema-generation) abrufen, das alle für eine Abfrage erforderlichen Typen enthält.

Bei Inhaltsfragmenten basieren die GraphQL-Schema (Struktur und Typen) auf [Inhaltsfragmentmodellen](/help/assets/content-fragments/content-fragments-models.md) und ihren Datentypen.

Wenn ein Benutzer beispielsweise ein Inhaltsfragmentmodell mit dem Namen `Article` erstellt hat, generiert AEM das Objekt `article`, das dem Typ `ArticleModel` entspricht. Die Felder dieses Typs entsprechen den im Modell definierten Feldern und Datentypen.

1. Ein Inhaltsfragmentmodell:

   ![Inhaltsfragmentmodell zur Verwendung mit ](assets/cfm-graphqlapi-01.png "GraphQLContent Fragment Model zur Verwendung mit GraphQL")

1. Das entsprechende GraphQL-Schema (Ausgabe aus der GraphiQL-Dokumentation):
   ![GraphQL-Schema basierend auf Content Fragment ](assets/cfm-graphqlapi-02.png "ModelGraphQL-Schema basierend auf Inhaltsfragmentmodell")

   Dies zeigt, dass der generierte Typ `ArticleModel` mehrere [Felder](#fields) enthält.

   * Drei davon wurden vom Benutzer kontrolliert: `author`, `main` und `linked_article`.

   * Die anderen Felder wurden automatisch von AEM hinzugefügt und stellen hilfreiche Methoden dar, um Informationen zu einem bestimmten Inhaltsfragment bereitzustellen. in diesem Beispiel `_path`, `_metadata`, `_variations`. Diese [Hilfefelder](#helper-fields) sind mit einem vorangestellten `_` gekennzeichnet, um zu unterscheiden, was vom Benutzer definiert wurde und was automatisch generiert wurde.

1. Nachdem ein Benutzer ein Inhaltsfragment auf Grundlage des Artikelmodells erstellt hat, kann es über GraphQL abgefragt werden. Beispiele finden Sie in den Abfragen [Beispiel](/help/assets/content-fragments/content-fragments-graphql-samples.md#graphql-sample-queries) (basierend auf einer [Beispiel-Inhaltsfragmentstruktur für die Verwendung mit GraphQL](/help/assets/content-fragments/content-fragments-graphql-samples.md#content-fragment-structure-graphql)).

In GraphQL für AEM ist das Schema flexibel. Dies bedeutet, dass sie jedes Mal automatisch generiert wird, wenn ein Inhaltsfragmentmodell erstellt, aktualisiert oder gelöscht wird. Die Schema-Cache-Speicher werden auch aktualisiert, wenn Sie ein Inhaltsfragmentmodell aktualisieren.

Der Sites GraphQL-Dienst überwacht (im Hintergrund) alle Änderungen, die an einem Inhaltsfragmentmodell vorgenommen wurden. Wenn Updates erkannt werden, wird nur dieser Teil des Schemas neu generiert. Diese Optimierung spart Zeit und bietet Stabilität.

Wenn Sie zum Beispiel:

1. Installieren Sie ein Paket, das `Content-Fragment-Model-1` und `Content-Fragment-Model-2` enthält:

   1. GraphQL-Typen für `Model-1` und `Model-2` werden generiert.

1. Ändern Sie dann `Content-Fragment-Model-2`:

   1. Nur der Typ `Model-2` GraphQL wird aktualisiert.

   1. Dagegen bleibt `Model-1` gleich.

>[!NOTE]
>
>Dies ist wichtig, wenn Sie Massenaktualisierungen zu Inhaltsfragmentmodellen über die REST-API oder anderweitig durchführen möchten.

Das Schema wird durch denselben Endpunkt wie die GraphQL-Abfragen bedient, wobei der Client die Tatsache behandelt, dass das Schema mit der Erweiterung `GQLschema` aufgerufen wird. Wenn Sie beispielsweise eine einfache `GET`-Anforderung für `/content/graphql/endpoint.GQLschema` ausführen, wird das Schema mit dem Content-Typ ausgegeben: `text/x-graphql-schema;charset=iso-8859-1`.

## Felder {#fields}

Innerhalb des Schemas gibt es einzelne Felder mit zwei grundlegenden Kategorien:

* Von Ihnen erstellte Felder.

   Eine Auswahl von [Feldtypen](#field-types) wird verwendet, um Felder basierend auf der Konfiguration des Inhaltsfragmentmodells zu erstellen. Die Feldnamen werden aus dem Feld **Eigenschaftsname** des **Datentyps** entnommen.

   * Es ist auch die Eigenschaft **Render As** zu berücksichtigen, da Benutzer bestimmte Datentypen konfigurieren können. z. B. als einzeiliger oder als mehrzeiliger Text.

* GraphQL für AEM generiert auch eine Reihe von [Helferfeldern](#helper-fields).

   Diese werden verwendet, um ein Inhaltsfragment zu identifizieren oder um weitere Informationen zu einem Inhaltsfragment abzurufen.

### Feldtypen {#field-types}

GraphQL für AEM unterstützt eine Liste von Typen. Alle unterstützten Datenarten des Inhaltsfragmentmodells und die entsprechenden GraphQL-Typen werden dargestellt:

| Inhaltsfragmentmodell - Datentyp | GraphQL-Typ | Beschreibung |
|--- |--- |--- |
| Einzelzeilentext | Zeichenfolge, [Zeichenfolge] |  Wird für einfache Zeichenfolgen wie Autorennamen, Ortsnamen usw. verwendet |
| Mehrzeiliger Text | Zeichenfolge |  Dient zum Ausgeben von Text, z. B. der Textkörper eines Artikels |
| Zahl |  Float, [Float] | Zur Anzeige von Gleitkommazahlen und regelmäßigen Zahlen |
| Boolesch |  Boolesch |  Dient zum Anzeigen von Kontrollkästchen → einfache true/false-Anweisungen |
| Datum und Uhrzeit | Kalender |  Wird verwendet, um Datum und Uhrzeit in einem ISO 8086-Format anzuzeigen |
| Aufzählung |  Zeichenfolge |  Dient zum Anzeigen einer Option aus einer Liste von Optionen, die bei der Modellerstellung definiert wurden |
|  Tags |  [Zeichenfolge] |  Dient zum Anzeigen einer Liste von Zeichenfolgen, die Tags darstellen, die in AEM verwendet werden |
| Inhaltsreferenz |  Zeichenfolge |  Wird verwendet, um den Pfad zu einem anderen Asset in AEM anzuzeigen |
| Fragmentreferenz |  *Ein Modelltyp* |  Wird verwendet, um auf ein anderes Inhaltsfragment eines bestimmten Modelltyps zu verweisen, das beim Erstellen des Modells definiert wurde |

### Helferfelder {#helper-fields}

Zusätzlich zu den Datentypen für vom Benutzer erstellte Felder generiert GraphQL für AEM auch eine Reihe von Feldern *helper*, um ein Inhaltsfragment zu identifizieren oder zusätzliche Informationen über ein Inhaltsfragment bereitzustellen.

#### Pfad {#path}

Das Pfadfeld wird als Bezeichner in GraphQL verwendet. Er stellt den Pfad des Inhaltsfragment-Assets im AEM Repository dar. Wir haben dieses Fragment als Bezeichner für ein Inhaltsfragment ausgewählt, da es:

* innerhalb von AEM eindeutig ist,
* kann leicht abgerufen werden.

Der folgende Code zeigt die Pfade aller Inhaltsfragmente an, die auf der Grundlage des Inhaltsfragmentmodells `Person` erstellt wurden.

```xml
{
  persons {
    items {
      _path
    }
  }
}
```

Um ein einzelnes Inhaltsfragment eines bestimmten Typs abzurufen, müssen Sie auch zuerst dessen Pfad festlegen. Beispiel:

```xml
{
    person(_path="/content/dam/path/to/fragment/john-doe") {
        _path
        name
        first-name
    }
}
```

Siehe [Abfrage &quot;Beispiel - Ein Einzelstadtfragment](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-single-city-fragment)&quot;.

#### Metadaten {#metadata}

Mit GraphQL stellt AEM auch die Metadaten eines Inhaltsfragments zur Verfügung. Metadaten sind die Informationen, die ein Inhaltsfragment beschreiben, z. B. den Titel eines Inhaltsfragments, den Pfad der Miniaturansicht, die Beschreibung eines Inhaltsfragments, das Erstellungsdatum usw.

Da Metadaten über den Schema-Editor generiert werden und daher keine bestimmte Struktur haben, wurde der Typ `TypedMetaData` GraphQL implementiert, um die Metadaten eines Inhaltsfragments anzuzeigen. `TypedMetaData` stellt die Informationen bereit, die nach den folgenden Skalartypen gruppiert sind:

| Feld |
|--- |
| `stringMetadata:[StringMetadata]!` |
| `stringArrayMetadata:[StringArrayMetadata]!` |
| `intMetadata:[IntMetadata]!` |
| `intArrayMetadata:[IntArrayMetadata]!` |
| `floatMetadata:[FloatMetadata]!` |
| `floatArrayMetadata:[FloatArrayMetadata]!` |
| `booleanMetadata:[BooleanMetadata]!` |
| `booleanArrayMetadata:[booleanArrayMetadata]!`  |
| `calendarMetadata:[CalendarMetadata]!` |
| `calendarArrayMetadata:[CalendarArrayMetadata]!` |

Jeder Skalartyp stellt entweder ein Paar aus Name und Wert oder ein Array aus Name-Wert-Paaren dar, wobei der Wert dieses Paars dem Typ entspricht, in dem es gruppiert wurde.

Wenn Sie beispielsweise den Titel eines Inhaltsfragments abrufen möchten, wissen wir, dass diese Eigenschaft eine String-Eigenschaft ist. Daher würden wir eine Abfrage für alle Zeichenfolgenmetadaten durchführen:

Abfrage für Metadaten:

```xml
{
  person(_path: "/content/dam/path/to/fragment/john-doe") {
    _path
    _metadata {
      stringMetadata {
        name
        value
      }
    }
  }
}
```

Sie können alle Metadaten des GraphQL-Typs Ansicht haben, wenn Sie das Generated GraphQL-Schema Ansicht haben. Alle Modelltypen haben die gleiche `TypedMetaData`.

>[!NOTE]
>
>**Unterschied zwischen normalen Metadaten und Array-Metadaten**
>Denken Sie daran, dass `StringMetadata` und `StringArrayMetadata` beide auf das beziehen, was im Repository gespeichert ist, und nicht darauf, wie Sie sie abrufen.
>
>Wenn Sie beispielsweise das Feld `stringMetadata` aufrufen, erhalten Sie ein Array aller im Repository gespeicherten Metadaten als `String` und wenn Sie `stringArrayMetadata` aufrufen, erhalten Sie ein Array aller Metadaten, die im Repository als `String[]` gespeichert wurden.

Siehe [Beispieldatei für Abfrage für Metadaten - Liste der Metadaten für Auszeichnungen mit dem Titel GB](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-metadata-awards-gb).

#### Varianten {#variations}

Das Feld `_variations` wurde implementiert, um die Abfrage der Varianten eines Inhaltsfragments zu vereinfachen. Beispiel:

```xml
{
  person(_path: "/content/dam/path/to/fragment/john-doe") {
    _variations
  }
}
```

Siehe [Beispielstadt - Alle Abfragen mit einer benannten Variation](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-cities-named-variation).

<!--
## Security Considerations {#security-considerations}
-->

## GraphQL-Variablen {#graphql-variables}

GraphQL ermöglicht die Platzierung von Variablen in der Abfrage. Weitere Informationen finden Sie in der [GraphQL-Dokumentation für GraphiQL](https://graphql.org/learn/queries/#variables).

Um beispielsweise alle Inhaltsfragmente des Typs `Article` abzurufen, die eine bestimmte Variation aufweisen, können Sie die Variable `variation` in GraphiQL angeben:

![GraphQL-](assets/cfm-graphqlapi-03.png "VariablenGraphQL-Variablen")

```xml
### query
query GetArticlesByVariation($variation: String!) {
    articles(variation: $variation) {
        items {
            _path
            author
        }
    }
}
 
### in query variables
{
    "variation": "uk"
}
```

## GraphQL-Richtlinien {#graphql-directives}

In GraphQL gibt es die Möglichkeit, die Abfrage anhand von Variablen zu ändern, die GraphQL Richtlinien genannt werden.

Sie können beispielsweise das Feld `adventurePrice` in eine Abfrage für alle `AdventureModels` einfügen, basierend auf einer Variablen `includePrice`.

![GraphQL-](assets/cfm-graphqlapi-04.png "RichtlinienGraphQL-Richtlinien")

```xml
query getAdventureByType($includePrice: Boolean!) {
  adventures {
    items {
      adventureType
      adventurePrice @include(if: $includePrice)
    }
  }
}
 
### in query variables
{
    "includePrice": true
}
```

## Beständige Abfragen (Zwischenspeicherung) {#persisted-queries-caching}

Nachdem Sie eine Abfrage mit einer POST-Anforderung vorbereitet haben, kann sie mit einer GET ausgeführt werden, die von HTTP-Caches oder einem CDN zwischengespeichert werden kann.

Dies ist erforderlich, da Abfragen der POST in der Regel nicht zwischengespeichert werden, und wenn GET mit der Abfrage als Parameter verwendet wird, besteht die große Gefahr, dass der Parameter für HTTP-Dienste und Zwischenprodukte zu groß wird.

Die folgenden Schritte sind erforderlich, um eine bestimmte Abfrage beizubehalten:

>[!NOTE]
>Zuvor müssen die **GraphQL Persistence Abfragen** für die entsprechende Konfiguration aktiviert werden. Weitere Informationen finden Sie unter [Funktion &quot;Inhaltsfragment aktivieren&quot;im Konfigurationsbrowser](/help/assets/content-fragments/content-fragments-configuration-browser.md#enable-content-fragment-functionality-in-configuration-browser).

1. Bereiten Sie die Abfrage durch PUTing an die neue Endpunkt-URL `/graphql/persist.json/<config>/<persisted-label>` vor.

   Erstellen Sie beispielsweise eine beständige Abfrage:

   ```xml
   $ curl -X PUT \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query" \
       -d \
   '{
     articleList {
       items{
           _path
           author
           main {
               json
           }
       }
     }
   }'
   ```

1. Überprüfen Sie an dieser Stelle die Antwort.

   Suchen Sie beispielsweise nach Erfolg:

   ```xml
   {
     "action": "create",
     "configurationName": "wknd",
     "name": "plain-article-query",
     "shortPath": "/wknd/plain-article-query",
     "path": "/conf/wknd/settings/graphql/persistentQueries/plain-article-query"
   }
   ```

1. Sie können die behaltene Abfrage dann erneut abspielen, indem Sie die URL `/graphql/execute.json/<shortPath>` aufrufen.

   Verwenden Sie zum Beispiel die persistente Abfrage:

   ```xml
   $ curl -X GET \
       http://localhost:4502/graphql/execute.json/wknd/plain-article-query
   ```

1. Aktualisieren Sie eine persistente Abfrage durch POSTing auf einen bereits vorhandenen Pfad der Abfrage.

   Verwenden Sie zum Beispiel die persistente Abfrage:

   ```xml
   $ curl -X POST \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query" \
       -d \
   '{
     articleList {
       items{
           _path
           author
           main {
               json
           }
         referencearticle {
           _path
         }
       }
     }
   }'
   ```

1. Erstellen Sie eine umhüllte Abfrage.

   Beispiel:

   ```xml
   $ curl -X PUT \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-wrapped" \
       -d \
   '{ "query": "{articleList { items { _path author main { json } referencearticle { _path } } } }"}'
   ```

1. Erstellen Sie eine umschlossene Abfrage mit Cachesteuerung.

   Beispiel:

   ```xml
   $ curl -X PUT \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-max-age" \
       -d \
   '{ "query": "{articleList { items { _path author main { json } referencearticle { _path } } } }", "cache-control": { "max-age": 300 }}'
   ```

1. Erstellen Sie eine persistente Abfrage mit Parametern:

   Beispiel:

   ```xml
   $ curl -X PUT \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-parameters" \
       -d \
   'query GetAsGraphqlModelTestByPath($apath: String!, $withReference: Boolean = true) {
     articleByPath(_path: $apath) {
       item {
         _path
           author
           main {
           plaintext
           }
           referencearticle @include(if: $withReference) {
           _path
           }
         }
       }
     }'
   ```

1. Ausführen einer Abfrage mit Parametern.

   Beispiel:

   ```xml
   $ curl -X POST \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/execute.json/wknd/plain-article-query-parameters;apath=%2fcontent2fdam2fwknd2fen2fmagazine2falaska-adventure2falaskan-adventures;withReference=false"
   
   $ curl -X GET \
       "http://localhost:4502/graphql/execute.json/wknd/plain-article-query-parameters;apath=%2fcontent2fdam2fwknd2fen2fmagazine2falaska-adventure2falaskan-adventures;withReference=false"
   ```

1. Um die Abfrage bei der Veröffentlichung auszuführen, muss der zugehörige Persistenzbaum repliziert werden

   * Verwenden einer POST für die Replikation:

      ```xml
      $curl -X POST   http://localhost:4502/bin/replicate.json \
        -H 'authorization: Basic YWRtaW46YWRtaW4=' \
        -F path=/conf/wknd/settings/graphql/persistentQueries/plain-article-query \
        -F cmd=activate
      ```

   * Verwenden eines Pakets:
      1. Erstellen Sie eine neue Paketdefinition.
      1. Schließen Sie die Konfiguration ein (z. B. `/conf/wknd/settings/graphql/persistentQueries`).
      1. Erstellen Sie das Paket.
      1. Replizieren Sie das Paket.
   * Einsatz des Replikations-/Verteilungstools.
      1. Wechseln Sie zum Distribution-Tool.
      1. Wählen Sie die Aktivierung tree for the configuration (z. B. `/conf/wknd/settings/graphql/persistentQueries`).
   * Verwenden eines Workflows (über die Konfiguration des Workflow-Starters):
      1. Definieren Sie eine Workflow-Starterregel zum Ausführen eines Workflow-Modells, das die Konfiguration auf verschiedenen Ereignissen repliziert (z. B. Erstellen, Ändern).



1. Sobald die Konfiguration der Abfrage veröffentlicht ist, gelten dieselben Grundsätze, nur mithilfe des Veröffentlichungsendpunkts.

   >[!NOTE]
   >
   >Für den anonymen Zugriff geht das System davon aus, dass die ACL &quot;jedermann&quot;Zugriff auf die Konfiguration der Abfrage erlaubt.
   >
   >Ist dies nicht der Fall, kann es nicht ausgeführt werden.

   >[!NOTE]
   >
   >Alle Semikolons (&quot;;&quot;) in den URLs müssen kodiert werden.
   >
   >So wie in der Anforderung zum Ausführen einer persistenten Abfrage:
   >
   >
   ```xml
   >curl -X GET \ "http://localhost:4502/graphql/execute.json/wknd/plain-article-query-parameters%3bapath=%2fcontent2fdam2fwknd2fen2fmagazine2falaska-adventure2falaskan-adventures;withReference=false"
   >```

## Abrufen des GraphQL-Endpunkts von einer externen Website {#query-graphql-endpoint-from-external-website}

>[!NOTE]
>
>Eine detaillierte Übersicht über die CORS-Richtlinie zur Ressourcenfreigabe finden Sie AEM [Verstehen Sie Cross-Herkunft Resource Sharing (CORS)](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing.html?lang=en#understand-cross-origin-resource-sharing-(cors)).

Damit eine Website eines Drittanbieters JSON-Ausgabe nutzen kann, muss eine CORS-Richtlinie im Customer Git-Repository konfiguriert werden. Dazu wird eine entsprechende OSGi CORS-Konfigurationsdatei für den gewünschten Endpunkt hinzugefügt. Diese Konfiguration sollte einen vertrauenswürdigen Website-Namen (oder regex) angeben, für den Zugriff gewährt werden sollte.

* Zugriff auf den GraphQL-Endpunkt:

   * Alloworigin: [Ihre Domäne] oder alloworiginregexp: [Ihr Domänenregex]
   * Unterstützte Methoden: [POST]
   * zulässige Pfade: [&quot;/apps/graphql-enablement/content/endpoint.gql(/persistent)?&quot;]

* Zugriff auf den GraphQL-Endpunkt für beständige Abfragen:

   * Alloworigin: [Ihre Domäne] oder alloworiginregexp: [Ihr Domänenregex]
   * Unterstützte Methoden: [GET]
   * zulässige Pfade: [&quot;/graphql/execute.json/.*&quot;]

>[!CAUTION]
>
>Es bleibt die Verantwortung des Kunden,
>
>* Nur Zugriff auf vertrauenswürdige Domänen gewähren
>* keine Platzhaltersyntax [*] verwenden; die die GraphQL-Endpunkte der ganzen Welt zugänglich machen.



## Filtern von {#filtering}

Sie können auch die Filterung in Ihren GraphQL-Abfragen verwenden, um bestimmte Daten zurückzugeben.

Beim Filtern wird eine Syntax verwendet, die auf logischen Operatoren und Ausdrücken basiert.

Beispiele finden Sie unter:

* Details des [GraphQL für AEM Erweiterungen](/help/assets/content-fragments/content-fragments-graphql-samples.md#graphql-some-extensions)

* [Beispielinhalt und -](/help/assets/content-fragments/content-fragments-graphql-samples.md#content-fragment-structure-graphql) struktur für die Verwendung in Abfragen

* [Beispielinhalt und -struktur für Abfragen](/help/assets/content-fragments/content-fragments-graphql-samples.md#graphql-sample-queries-sample-content-fragment-structure)

* [Abfragen anhand des WKND-Projekts](/help/assets/content-fragments/content-fragments-graphql-samples.md#sample-queries-using-wknd-project)

## Berechtigungen {#permission}

Die Berechtigungen entsprechen denen, die für den Zugriff auf Assets erforderlich sind.

<!-- to be addressed later -->

<!-- 
## Authentication {#authentication}
-->

<!-- to be addressed later -->

<!-- 
## Caching {#caching}
-->

<!-- to be addressed later -->

<!--
## Sorting {#sorting}
-->

<!-- to be addressed later -->

<!--
## Paging {#paging}
-->

## Endpunkte {#end-points}

Der Endpunkt ist der Pfad, der für den Zugriff auf GraphQL für AEM verwendet wird. Mit diesem Pfad können Sie (oder Ihre App):

* Zugriff auf das GraphQL-Schema,
* Ihre GraphQL-Abfragen senden,
* erhalten Sie die Antworten (auf Ihre GraphQL-Abfragen).

Um Zugriff auf GraphQL-Servlets zu haben, müssen Sie AEM einen Endpunkt konfigurieren. Dazu gehören auch zwei OSGi-Konfigurationen.

1. Das Sling-Schema-Servlet, das auf Anforderungen zum Abrufen des GraphQL-Schemas reagiert:

   ![AEM Sites GraphQL Schema Servlet](assets/cfm-endpoint-01.png)

   * **Selektoren** (`sling.servlet.selectors`) müssen leer gelassen werden.

   * **Ressourcentypen** (`sling.servlet.resourceTypes`) Definieren Sie den Ressourcentyp, auf den das GraphQL-Servlet achten soll.
Beispiel:
      `graphql-enablement/components/endpoint`.

   * **Methoden** (`sling.servlet.methods^)

      Die HTTP-Methode, die das Servlet überwachen soll; gewöhnlich `GET`.

   * **Erweiterungen** (`sling.servlet.extensions`)

      Geben Sie die Erweiterung an, auf die das Schema-Servlet reagieren soll. In diesem Fall ist `GQLschema` kompatibel mit den GraphQL Spezifikationen.

2. Das Servlet, das auf grafische Anforderungen reagiert:

   ![Apache Sling GraphQL Servlet](assets/cfm-endpoint-02.png)

   * **Selektoren** (`sling.servlet.selectors`) müssen leer gelassen werden.

   * **Ressourcentyp** (`sling.servlet.resourceTypes`) Der Ressourcentyp, auf den das GraphQL-Servlet reagieren soll.
Beispiel: `graphql-enablement/components/endpoint`.

   * **Methoden** (`sling.servlet.methods`) Die HTTP-Methoden, auf die das GraphQL-Servlet reagieren sollte, normalerweise  `GET` und  `POST`.

   * **Erweiterungen** (`sling.servlet.extensions`) Die Erweiterung, die auf GraphQL-Anforderungen überwacht werden soll, in der Regel  `gql`.

3. Sie müssen jetzt einen Endpunkt erstellen - einen Knoten des in diesen Konfigurationen definierten sling:resourceType.
Um beispielsweise einen Endpunkt zum Abrufen des GraphQL-Schemas zu erstellen, erstellen Sie einen neuen Knoten unter `/apps/<my-site>/graphql`:

   * Name: `endpoint`
   * Primär: `nt:unstructured`
   * sling:resourceType: `graphql-enablement/components/endpoint`

## Häufig gestellte Fragen {#faqs}

Es wurden folgende Fragen aufgeworfen:

1. **Frage**: &quot;*Wie unterscheidet sich die GraphQL-API AEM von der Abfrage Builder-API?*&quot;

   * **A**: &quot;*Die AEM GraphQL API-Angebot haben die vollständige Kontrolle über die JSON-Ausgabe und sind ein Industriestandard für die Inhaltsabfrage.
In Zukunft plant AEM, in die AEM GraphQL API zu investieren.*&quot;

## Tutorial - Erste Schritte mit AEM Headless und GraphQL {#tutorial}

Suchen Sie nach einem praktischen Tutorial? Sehen Sie sich [Erste Schritte mit AEM Headless und GraphQL](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html) End-to-End-Tutorial an, in dem erläutert wird, wie Inhalte mithilfe der GraphQL-APIs AEM erstellt und bereitgestellt werden können, die von einer externen App in einem kopflosen CMS-Szenario genutzt werden.