---
title: Zugriff auf Ihre Inhalte über AEM Versand-APIs
description: Erfahren Sie in diesem Teil der AEM Headless Developer-Journey, wie Sie mit GraphQL-Abfragen auf Ihre Inhaltsfragmente zugreifen können.
hide: true
hidefromtoc: true
index: false
exl-id: 5ef557ff-e299-4910-bf8c-81c5154ea03f
translation-type: tm+mt
source-git-commit: d21d5a496d4a82dd569e582b5b7d7425bd50077f
workflow-type: tm+mt
source-wordcount: '2155'
ht-degree: 32%

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

## GraphQL - Eine Einführung {#graphql-introduction}

GraphQL ist eine Open-Source-Spezifikation, die Folgendes bietet:

* eine Abfrage, mit der Sie bestimmte Inhalte aus strukturierten Objekten auswählen können.
* eine Laufzeit, um diese Abfragen mit Ihrem strukturierten Inhalt zu erfüllen.

GraphQL ist eine *stark* eingegebene API. Das bedeutet, dass *alle*-Inhalte klar strukturiert und nach Typ geordnet sein müssen, sodass GraphQL *versteht, was auf* zugegriffen und wie es funktioniert. Die Datenfelder werden in GraphQL-Schemas definiert, die die Struktur Ihrer Inhaltsobjekte definieren.

GraphQL-Endpunkte stellen dann die Pfade bereit, die auf die GraphQL-Abfragen reagieren.

Dies bedeutet, dass Ihre App den benötigten Inhalt präzise, zuverlässig und effizient auswählen kann - genau das, was Sie bei AEM benötigen.

>[!NOTE]
>
>Siehe *GraphQL*.org und *GraphQL*.com.

## AEM und GraphQL {#aem-graphql}

GraphQL wird an verschiedenen Stellen in AEM verwendet. Beispiel:

* Inhaltsfragmente
   * Für diesen Anwendungsfall wurde eine benutzerdefinierte API entwickelt (Headless-Versand zu Ihrer App).
      * Dies ist die AEM GraphQL API.
* Commerce
   * AEM Commerce nutzt Daten von einer Commerce-Plattform über GraphQL.
   * Es gibt GraphQL-Integrationen zwischen AEM und verschiedenen Commerce-Lösungen von Drittanbietern, die mit den Erweiterungshaken der CIF-Kernkomponenten verwendet werden.
      * Dabei wird nicht die AEM GraphQL API verwendet.

>[!NOTE]
>
>Dieser Schritt der Journey ohne Kopfdaten betrifft nur die AEM GraphQL API und Inhaltsfragmente.

## AEM GraphQL-API {#aem-graphql-api}

Die AEM GraphQL API ist eine benutzerdefinierte Version, die auf der standardmäßigen GraphQL API-Spezifikation basiert und speziell so konfiguriert wurde, dass Sie (komplexe) Abfragen an Inhaltsfragmenten durchführen können.

Inhaltsfragmente werden verwendet, da der Inhalt nach Inhaltsfragmentmodellen strukturiert ist. Dies erfüllt eine Grundvoraussetzung für GraphQL.

* Ein Inhaltsfragmentmodell besteht aus einem oder mehreren Feldern.
   * Jedes Feld wird entsprechend einem Datentyp definiert.
* Mithilfe von Inhaltsfragmentmodellen werden die entsprechenden AEM GraphQL-Schema generiert.

Um tatsächlich auf GraphQL für AEM (und den Inhalt) zuzugreifen, wird ein Endpunkt verwendet, um den Zugriffspfad bereitzustellen.

Die über die AEM GraphQL API zurückgegebenen Inhalte können dann von Ihren Anwendungen verwendet werden.

>[!NOTE]
>
>Die Implementierung der AEM GraphQL-API basiert auf den GraphQL-Java-Bibliotheken.

### Anwendungsfälle für Autoren- und Veröffentlichungsumgebungen {#use-cases-author-publish-environments}

Die Anwendungsfälle für die AEM GraphQL API können vom Typ der AEM als Cloud Service-Umgebung abhängen:

* Veröffentlichungsumgebung; wird verwendet, um:
   * Inhalt der Abfrage für JS-Anwendungen (Standard-Anwendungsfall)

* Autorenumgebung; wird verwendet, um:
   * Abfragen für &quot;Content-Management&quot;:
      * GraphQL in AEM as a Cloud Service ist derzeit eine schreibgeschützte API.
      * Die REST-API kann für CR(u)D-Vorgänge verwendet werden.

## Inhaltsfragmente zur Verwendung mit der AEM GraphQL-API {#content-fragments-use-with-aem-graphql-api}

Inhaltsfragmente können als Grundlage für GraphQL für AEM Schema und Abfragen wie:

* Sie ermöglichen Ihnen das Entwerfen, Erstellen, Kuratieren und Veröffentlichen seitenunabhängiger Inhalte.
* Sie basieren auf einem Inhaltsfragmentmodell, das die Struktur für das resultierende Fragment mithilfe definierter Datentypen vordefiniert.
* Mit dem Datentyp &quot;Fragmentverweis&quot;können weitere Strukturebenen erstellt werden, die beim Definieren eines Modells verfügbar sind.

### Inhaltsfragmentmodelle {#content-fragments-models}

Diese Inhaltsfragmentmodelle:

* werden verwendet, um die Schemas zu erzeugen, sobald sie **aktiviert** sind.

* stellen die für GraphQL erforderlichen Datentypen und Felder bereit. Sie stellen sicher, dass Ihr Programm nur das anfordert, was möglich ist, und das erhält, was erwartet wird.

* Der Datentyp **Fragmentreferenzen** kann in Ihrem Modell verwendet werden, um auf ein anderes Inhaltsfragment zu verweisen und so zusätzliche Strukturebenen einzuführen.

### Fragmentreferenzen {#fragment-references}

Die **Fragmentreferenz**:

* Ist ein bestimmter Datentyp verfügbar, wenn ein Inhaltsfragmentmodell definiert wird.

* verweist auf ein anderes Fragment, abhängig von einem bestimmten Inhaltsfragmentmodell,

* Ermöglicht Ihnen das Erstellen und Abrufen strukturierter Daten.

   * Wenn als **multifeed** definiert, können mehrere Unterfragmente vom primären Fragment referenziert (abgerufen) werden.

### JSON-Vorschau {#json-preview}

Um beim Entwerfen und Entwickeln Ihrer Inhaltsfragmentmodelle zu helfen, können Sie die JSON-Ausgabe im Inhaltsfragment-Editor Vorschau haben.

## GraphQL-Schema-Generierung aus Inhaltsfragmenten {#graphql-schema-generation-content-fragments}

GraphQL ist eine stark typisierte API, was bedeutet, dass Inhalte klar strukturiert und nach Typ geordnet sein müssen. Die GraphQL-Spezifikation enthält eine Reihe von Richtlinien zum Erstellen einer robusten API zum Abfragen von Inhalten in einer bestimmten Instanz. Dazu muss ein Client das Schema abrufen, das alle für eine Abfrage erforderlichen Typen enthält.

Bei Inhaltsfragmenten basieren die GraphQL-Schemas (Struktur und Typen) auf **aktivierten** Inhaltsfragmentmodellen und deren Datentypen.

>[!CAUTION]
>
>Alle GraphQL-Schemas (abgeleitet von Inhaltsfragmentmodellen, die **aktiviert** wurden) sind über den GraphQL-Endpunkt lesbar.
>
>Dies bedeutet, dass Sie sicherstellen müssen, dass keine vertraulichen Inhalte verfügbar sind, um sicherzustellen, dass keine sensiblen Daten über GraphQL-Endpunkte verfügbar sind. Dazu gehören beispielsweise Informationen, die als Feldnamen in der Modelldefinition vorhanden sein könnten.

Wenn ein Benutzer beispielsweise ein Inhaltsfragmentmodell mit dem Namen `Article` erstellt hat, generiert AEM das Objekt `article`, das dem Typ `ArticleModel` entspricht. Die Felder dieses Typs entsprechen den im Modell definierten Feldern und Datentypen.

1. Ein Inhaltsfragmentmodell:

   ![Inhaltsfragmentmodell zur Verwendung mit GraphQL](assets/graphqlapi-cfmodel.png "Inhaltsfragmentmodell zur Verwendung mit GraphQL")

1. Das entsprechende GraphQL-Schema (Ausgabe aus der grafischen QL-Dokumentation):
   ![GraphQL-Schema basierend auf Inhaltsfragmentmodell](assets/graphqlapi-cfm-schema.png "GraphQL-Schema basierend auf Inhaltsfragmentmodell")

   Dies zeigt, dass der generierte Typ `ArticleModel` mehrere [Felder](#fields) enthält.

   * Drei davon wurden vom Benutzer kontrolliert: `author`, `main` und `referencearticle`.

   * Die anderen Felder wurden automatisch von AEM hinzugefügt und stellen hilfreiche Methoden dar, um Informationen zu einem bestimmten Inhaltsfragment bereitzustellen. In diesem Beispiel `_path`, `_metadata` und `_variations`. Diese [Hilfefelder](#helper-fields) sind mit einem vorangestellten `_` gekennzeichnet, um zu unterscheiden, was vom Benutzer definiert wurde und was automatisch generiert wurde.

1. Nachdem ein Benutzer ein Inhaltsfragment basierend auf dem Modell „Article“ erstellt hat, kann es über GraphQL abgefragt werden. Beispiele finden Sie unter Abfragen.md#graphql-sample-Abfragen (basierend auf einer Muster-Inhaltsfragmentstruktur zur Verwendung mit GraphQL).

In GraphQL für AEM ist das Schema flexibel. Dies bedeutet, dass es jedes Mal automatisch generiert wird, wenn ein Inhaltsfragmentmodell erstellt, aktualisiert oder gelöscht wird. Die Datenschema-Caches werden auch aktualisiert, wenn Sie ein Inhaltsfragmentmodell aktualisieren.

Der Sites GraphQL-Service überwacht (im Hintergrund) alle Änderungen, die an einem Inhaltsfragmentmodell vorgenommen werden. Wenn Aktualisierungen erkannt werden, wird nur dieser Teil des Schemas neu generiert. Diese Optimierung spart Zeit und bietet Stabilität.

Wenn Sie zum Beispiel:

1. ein Paket installieren, das `Content-Fragment-Model-1` und `Content-Fragment-Model-2` enthält:

   1. Es werden GraphQL-Typen für `Model-1` und `Model-2` generiert.

1. anschließend `Content-Fragment-Model-2` ändern:

   1. Nur der GraphQL-Typ `Model-2` wird aktualisiert.

   1. `Model-1` bleibt unverändert.

>[!NOTE]
>
>Dies ist wichtig, wenn Sie Massenaktualisierungen von Inhaltsfragmentmodellen über die REST-API oder auf andere Weise durchführen möchten.

Das Schema wird über denselben Endpunkt wie die GraphQL-Abfragen bereitgestellt, wobei der Client die Tatsache behandelt, dass das Schema mit der `GQLschema`-Erweiterung aufgerufen wird. Wenn Sie beispielsweise eine einfache `GET`-Anfrage an `/content/cq:graphql/global/endpoint.GQLschema` ausführen, wird das Schema mit dem Inhaltstyp ausgegeben: `text/x-graphql-schema;charset=iso-8859-1`.

### Schema-Generierung - unveröffentlichte Modelle {#schema-generation-unpublished-models}

Wenn Inhaltsfragmente verschachtelt sind, kann es vorkommen, dass ein übergeordnetes Inhaltsfragmentmodell veröffentlicht wird, aber kein referenziertes Modell.

>[!NOTE]
>
>Die AEM-Benutzeroberfläche verhindert dies, aber wenn die Veröffentlichung programmgesteuert oder mit Inhaltspaketen erfolgt, kann es dazu kommen.

In diesem Fall generiert AEM ein *unvollständiges*-Schema für das übergeordnete Inhaltsfragmentmodell. Das bedeutet, dass der Fragmentverweis, der vom unveröffentlichten Modell abhängt, aus dem Schema entfernt wird.

## AEM GraphQL Endpoints {#aem-graphql-endpoints}

<!--
need details/examples
-->

Ein Endpunkt ist der Pfad, der für den Zugriff auf GraphQL für AEM verwendet wird. Mit diesem Pfad können Sie (oder Ihr Programm):

* Zugriff auf die GraphQL-Schema,
* Ihre GraphQL-Abfragen senden,
* Antworten (auf Ihre GraphQL-Abfragen) empfangen.

AEM ermöglicht Folgendes:

* Ein globaler Endpunkt - für alle Sites verfügbar.
* Tenant-Endpunkte - die Sie je nach Standort/Projekt konfigurieren können.

## Berechtigungen {#permissions}

Die Berechtigungen sind diejenigen, die für den Zugriff auf Assets erforderlich sind.

## Die AEM GraphiQL-Schnittstelle {#aem-graphiql-interface}

Zur direkten Eingabe und zum Testen von Abfragen steht eine Implementierung der Standard-GraphiQL-Schnittstelle zur Verwendung mit AEM GraphQL zur Verfügung. Sie kann mit AEM installiert werden.

Es bietet Funktionen wie Syntaxhervorhebung, automatische Vervollständigung und automatische Empfehlung sowie einen Verlauf und eine Online-Dokumentation.

![GraphiQL-Schnittstelle](assets/graphiql-interface.png "GraphiQL-Schnittstelle")

## Tatsächlich mit der AEM GraphQL API {#actually-using-aem-graphiql}

Bevor Sie mit Abfragen zu Ihren Inhalten beginnen, müssen Sie Folgendes tun:

* Endpunkt aktivieren
   * Tools -> Sites -> GraphQL

* GraphiQL installieren (falls erforderlich)
   * Als dediziertes Paket installiert

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

Die Abfragen können in die GraphiQL-Oberfläche eingegeben werden, z. B. unter:

* `http://localhost:4502/content/graphiql.html `

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
