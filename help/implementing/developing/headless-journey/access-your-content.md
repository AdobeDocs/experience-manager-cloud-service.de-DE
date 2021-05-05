---
title: Zugriff auf Ihre Inhalte über AEM Versand-APIs
description: Erfahren Sie in diesem Teil der AEM Headless Developer-Journey, wie Sie mit GraphQL-Abfragen auf Ihre Inhaltsfragmente zugreifen können.
hide: true
hidefromtoc: true
index: false
exl-id: 5ef557ff-e299-4910-bf8c-81c5154ea03f
translation-type: tm+mt
source-git-commit: 7b04ae2bfa75fe3d3af13271efe567a5fc401f49
workflow-type: tm+mt
source-wordcount: '4636'
ht-degree: 55%

---

# Zugriff auf Ihre Inhalte über AEM Versand-APIs {#access-your-content}

>[!CAUTION]
>
>ARBEITEN IN FORTSCHRITTEN - Die Schaffung dieses Dokuments ist im Gange und sollte nicht als vollständig oder endgültig betrachtet werden und auch nicht für Produktionszwecke verwendet werden.

In diesem Teil der [AEM Headless Developer-Journey, ](overview.md) erfahren Sie, wie Sie mit den GraphQL-Abfragen auf den Inhalt Ihrer Inhaltsfragmente zugreifen können.

## Die Meldung bisher {#story-so-far}

Im vorherigen Dokument der AEM Journey [So modellieren Sie Ihren Inhalt](model-your-content.md), haben Sie die Grundlagen der Datenmodellierung in AEM gelernt. Sie sollten nun verstehen, wie Sie Ihre Inhaltsstruktur modellieren und diese Struktur dann mithilfe AEM Inhaltsfragmentmodelle und Inhaltsfragmente erkennen:

* Erkennen Sie die Konzepte und Terminologie für [Datenmodellierung](#data-modeling).
* Verstehen Sie [warum Datenmodellierung für den Versand von Headless-Inhalten erforderlich ist.](#data-modeling-for-aem-headless)
* Verstehen Sie [wie Sie diese Struktur mithilfe von AEM Inhaltsfragmentmodellen](#create-structure-content-fragment-models) (und Erstellen von Inhalten mit [Inhaltsfragmenten](#use-content-to-author-content)) realisieren.
* Verstehen Sie [wie Ihr Inhalt modelliert wird](#getting-started-examples); Grundprinzipien mit Basisproben.

Dieser Artikel baut auf diesen Grundlagen auf, damit Sie verstehen, wie Sie mit der AEM GraphQL-API auf Ihre vorhandenen Kopflosen-Inhalte in AEM zugreifen können.

* **Audience**: Anfänger
* **Zielsetzung**: Erfahren Sie, wie Sie mithilfe AEM GraphQL-Abfragen auf den Inhalt Ihrer Inhaltsfragmente zugreifen können:
   * Einführung in GraphQL und die AEM GraphQL API.
   * Tauchen Sie ein in die Details der AEM GraphQL API.
   * Sehen Sie sich einige Abfragen an, um zu sehen, wie die Dinge in der Praxis funktionieren.

## Sie möchten also auf Ihre Daten zugreifen? {#so-youd-like-to-access-your-data}

Also...Sie haben all diesen Inhalt, ordentlich strukturiert (in Inhaltsfragmenten), und warten darauf, Ihre neue App mit Feeds zu versehen. Frage ist - wie man es dorthin bringt?

Sie benötigen eine Möglichkeit, bestimmte Inhalte Zielgruppe, auszuwählen, was Sie benötigen, und diese zur weiteren Verarbeitung an Ihre App zurückzugeben.

Mit Adobe Experience Manager (AEM) als Cloud Service können Sie mithilfe der AEM GraphQL API selektiv auf Inhaltsfragmente zugreifen, um nur die benötigten Inhalte zurückzugeben. Dies bedeutet, dass Sie den kopflosen Versand von strukturierten Inhalten zur Verwendung in Ihren Anwendungen realisieren können.

>[!NOTE]
>
>AEM GraphQL API ist eine benutzerdefinierte Implementierung, die auf dem Standard GraphQL basiert.

## GraphQL - Eine Einführung {#graphql-introduction}

GraphQL ist eine Open-Source-Spezifikation, die Folgendes bietet:

* eine Abfrage, mit der Sie bestimmte Inhalte aus strukturierten Objekten auswählen können.
* eine Laufzeit, um diese Abfragen mit Ihrem strukturierten Inhalt zu erfüllen.

GraphQL ist eine *stark* eingegebene API. Das bedeutet, dass *alle*-Inhalte klar strukturiert und nach Typ geordnet sein müssen, sodass GraphQL *versteht, was auf* zugegriffen und wie es funktioniert. Die Datenfelder werden in GraphQL-Schemas definiert, die die Struktur Ihrer Inhaltsobjekte definieren.

GraphQL-Endpunkte stellen dann die Pfade bereit, die auf die GraphQL-Abfragen reagieren.

Dies bedeutet, dass Ihre App die benötigten Daten präzise, zuverlässig und effizient auswählen kann - genau das, was Sie bei der Verwendung mit AEM benötigen.

>[!NOTE]
>
>Siehe *GraphQL*.org und *GraphQL*.com.

## AEM und GraphQL {#aem-graphql}

GraphQL wird an verschiedenen Stellen in AEM verwendet. Beispiel:

* Commerce
   * Es gibt GraphQL-Integrationen zwischen AEM und verschiedenen Commerce-Lösungen von Drittanbietern, die mit den Erweiterungshaken der CIF-Kernkomponenten verwendet werden.
* Inhaltsfragmente
   * Für diesen Anwendungsfall wurde eine benutzerdefinierte API entwickelt.
   * Dies ist die AEM GraphQL API.

>[!NOTE]
>
>Dieser Schritt der Journey ohne Kopfdaten betrifft nur die AEM GraphQL API und Inhaltsfragmente.

## AEM GraphQL-API {#aem-graphql-api}

Die AEM GraphQL API ist eine angepasste Version der Standard GraphQL API, die speziell für die Durchführung (komplexer) Abfragen an Inhaltsfragmenten konfiguriert wurde.

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
   * Daten für das JS-Programm (Standardanwendungsfall) abzufragen

* Autorenumgebung; wird verwendet, um:
   * Daten für „Content-Management-Zwecke“ abzufragen:
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

* ist vor allem in Verbindung mit GraphQL von Interesse,

* ist ein spezifischer Datentyp, der bei der Definition eines Inhaltsfragmentmodells verwendet werden kann,

* verweist auf ein anderes Fragment, abhängig von einem bestimmten Inhaltsfragmentmodell,

* ermöglicht Ihnen das Abrufen strukturierter Daten.

   * Wenn als **multifeed** definiert, können mehrere Unterfragmente vom primären Fragment referenziert (abgerufen) werden.

### JSON-Vorschau {#json-preview}

Um beim Entwerfen und Entwickeln Ihrer Inhaltsfragmentmodelle zu helfen, können Sie die JSON-Ausgabe im Inhaltsfragment-Editor Vorschau haben.

## GraphQL-Schema-Generierung aus Inhaltsfragmenten {#graphql-schema-generation-content-fragments}

GraphQL ist eine stark typisierte API, was bedeutet, dass die Daten klar strukturiert und nach Typ geordnet sein müssen. Die GraphQL-Spezifikation enthält eine Reihe von Richtlinien zum Erstellen einer robusten API zum Abfragen von Daten in einer bestimmten Instanz. Dazu muss ein Client das Schema abrufen, das alle für eine Abfrage erforderlichen Typen enthält.

Bei Inhaltsfragmenten basieren die GraphQL-Schemas (Struktur und Typen) auf **aktivierten** Inhaltsfragmentmodellen und deren Datentypen.

>[!CAUTION]
>
>Alle GraphQL-Schemas (abgeleitet von Inhaltsfragmentmodellen, die **aktiviert** wurden) sind über den GraphQL-Endpunkt lesbar.
>
>Das bedeutet, dass Sie sicherstellen müssen, dass keine vertraulichen Daten verfügbar sind, da sie auf diese Weise an die Öffentlichkeit gelangen könnten. Dazu gehören beispielsweise Informationen, die als Feldnamen in der Modelldefinition vorhanden sein könnten.

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

<!--
new page?
-->

## Verwenden der AEM GraphQL API {#using-aem-graphiql}

### Endpunkte {#endpoints}

Der Repository-Pfad des GraphQL für AEM globalen Endpunkt lautet:

`/content/cq:graphql/global/endpoint`

Für die Ihre App den folgenden Pfad in der Anforderungs-URL verwenden kann:

`/content/_cq_graphql/global/endpoint.json`

Für einen Mandanten-Endpunkt sind die Pfade vergleichbar:

`/content/cq:graphql/your-tenant/endpoint`
`/content/_cq_graphql/your-tenant/endpoint.json`

Vor der Verwendung müssen alle Endpunkte aktiviert sein. Um einen Endpunkt (global oder mieter) für GraphQL für AEM zu aktivieren, müssen Sie:

* Aktivieren des GraphQL-Endpunkts
* Endpunkt veröffentlichen

>[!CAUTION]
>
>Der Inhaltsfragment-Editor kann zulassen, dass ein Inhaltsfragment eines Mandanten (über Richtlinien) auf ein Inhaltsfragment eines anderen Mandanten verweist.
>
>In einem solchen Fall sind nicht alle Inhalte über einen Pächter-spezifischen Endpunkt abrufbar.
>
>Der Autor des Inhalts sollte dieses Szenario steuern. Es kann beispielsweise nützlich sein, die Platzierung von gemeinsamen Inhaltsfragmentmodellen unter den globalen Mandanten zu erwägen.

### Aktivieren des GraphQL-Endpunkts {#enabling-graphql-endpoint}

Um einen GraphQL-Endpunkt zu aktivieren, benötigen Sie zunächst eine entsprechende Konfiguration im Konfigurationsbrowser.

>[!CAUTION]
>
>Wenn die Verwendung von Inhaltsfragmentmodellen nicht aktiviert wurde, ist die Option **Erstellen** nicht verfügbar.

So aktivieren Sie den entsprechenden Endpunkt:

1. Navigieren Sie zu **Tools**, **Sites** und wählen Sie **GraphQL**.
1. Wählen Sie **Erstellen**.
1. Das Dialogfeld **Create new GraphQL Endpoint** wird geöffnet. Hier können Sie Folgendes angeben:
   * **Name**: Name des Endpunkts; Sie können beliebigen Text eingeben.
   * **GraphQL-Schema verwenden, bereitgestellt von**: Verwenden Sie das Dropdownmenü, um die gewünschte Site/das gewünschte Projekt auszuwählen.

   >[!NOTE]
   >
   >Die folgende Warnung wird im Dialogfeld angezeigt:
   >
   >* *GraphQL-Endpunkte können Datensicherheits- und Leistungsprobleme hervorrufen, wenn sie nicht sorgfältig verwaltet werden. Stellen Sie sicher, dass nach dem Erstellen eines Endpunkts die entsprechenden Berechtigungen festgelegt werden.*


1. Bestätigen Sie mit **Create**.
1. Das Dialogfeld **Nächste Schritte** stellt einen direkten Link zur Sicherheitskonsole bereit, damit Sie sicherstellen können, dass der neu erstellte Endpunkt über die entsprechenden Berechtigungen verfügt.

   >[!CAUTION]
   >
   >Der Endpunkt ist für jeden zugänglich. Dies kann – insbesondere bei Veröffentlichungsinstanzen – Sicherheitsbedenken aufwerfen, da GraphQL-Abfragen eine hohe Server-Belastung verursachen können.
   >
   >Sie können am Endpunkt geeignete ACLs für Ihre Anwendung einrichten.

### Veröffentlichen des GraphQL-Endpunkts {#publishing-graphql-endpoint}

Wählen Sie den neuen Endpunkt und **Veröffentlichen** aus, um ihn in allen Umgebung vollständig verfügbar zu machen.

>[!CAUTION]
>
>Der Endpunkt ist für jeden zugänglich.
>
>Bei Veröffentlichungsinstanzen kann dies Sicherheitsbedenken aufwerfen, da GraphQL-Abfragen eine hohe Serverbelastung verursachen können.
>
>Sie müssen ACLs entsprechend Ihrer Anwendungsfälle am Endpunkt einrichten.

### AEM GraphiQL-Schnittstelle installieren {#installing-graphiql-interface}

Die GraphiQL-Benutzeroberfläche kann mit einem dedizierten Paket auf AEM installiert werden: das [GraphiQL Content Package v0.0.6 (2021.3)](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?package=/content/software-distribution/en/details.html/content/dam/aemcloud/public/aem-graphql/graphiql-0.0.6.zip)-Paket.

### AEM GraphQL-Schema {#aem-graphql-schemas}

Um auf Ihre Daten zugreifen zu können, müssen Sie zunächst den erforderlichen Typ des Inhaltsfragmentmodells auswählen, der durch ein GraphQL-Schema repräsentiert wird. AEM GraphQL-Schema werden von Ihren Inhaltsfragmentmodellen abgeleitet - zur Verwendung in Ihren GraphQL-Abfragen.

<!--
Confirm is the schema city or CityModel? -->

Wenn Sie ein Inhaltsfragmentmodell mit dem Namen `City` haben, wird ein entsprechendes Schema mit dem Namen `city` angezeigt. Sie können die folgende Abfrage verwenden, um die `name` aller Inhaltsfragmente, die auf diesem Modell basieren, Liste.

```xml
query {
  cityList {
    items {
      name
    }
  }
}
```

Sie können die folgende Abfrage verwenden, um die `name` und `description` von allen `types` für alle verfügbaren Schema Liste:

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

### AEM GraphQL-Felder {#aem-graphql-fields}

Wenn Sie das gewünschte Schema ausgewählt haben, möchten Sie auf bestimmte Daten zugreifen, die durch Felder im Schema dargestellt werden.

Innerhalb des Schemas gibt es einzelne Felder, die zwei grundlegenden Kategorien angehören:

* Von Ihnen generierte Felder.

   Eine Auswahl von [Feldtypen](#field-types) wird verwendet, um Felder basierend auf der Konfiguration des Inhaltsfragmentmodells zu erstellen. Die Feldnamen werden aus dem Feld **Eigenschaftsname** des **Datentyps** entnommen.

   * Es ist auch die Eigenschaft **Rendern als** zu berücksichtigen, da Benutzer bestimmte Datentypen konfigurieren können, beispielsweise als einzeiligen oder mehrzeiligen Text.

* GraphQL für AEM generiert auch eine Reihe von Hilfsfeldern.

   Diese werden verwendet, um ein Inhaltsfragment zu identifizieren oder um weitere Informationen zu einem Inhaltsfragment abzurufen.

### Feldtypen {#field-types}

GraphQL für AEM unterstützt eine Liste von Typen. Alle unterstützten Datentypen für Inhaltsfragmentmodelle und die entsprechenden GraphQL-Typen werden dargestellt:

| Datentyp für Inhaltsfragmentmodelle | GraphQL-Typ | Beschreibung |
|--- |--- |--- |
| Einzelzeilentext | Zeichenfolge, [Zeichenfolge] | Wird für einfache Zeichenfolgen wie Autorennamen, Ortsnamen usw. verwendet. |
| Mehrzeiliger Text | Zeichenfolge | Dient zum Ausgeben von Text, wie z. B. den Text eines Artikels |
| Zahl | Gleitkommazahl, [Gleitkommazahl] | Wird für die Anzeige von Gleitkommazahlen und regulären Zahlen verwendet |
| Boolesch | Boolesch | Wird für die Anzeige von Kontrollkästchen → einfachen Wahr/Falsch-Aussagen verwendet |
| Datum und Uhrzeit | Kalender | Wird verwendet, um Datum und Uhrzeit in einem ISO 8086-Format anzuzeigen. Je nach ausgewähltem Typ sind in AEM GraphQL drei Varianten verfügbar: `onlyDate`, `onlyTime`, `dateTime` |
| Aufzählung | Zeichenfolge | Wird verwendet, um eine Option aus einer Liste von Optionen anzuzeigen, die bei der Modellerstellung definiert wurde |
| Tags | [Zeichenfolge] | Wird verwendet, um eine Liste von Zeichenfolgen anzuzeigen, die in AEM verwendete Tags darstellen |
| Inhaltsreferenz | Zeichenfolge | Wird verwendet, um den Pfad zu einem anderen Asset in AEM anzuzeigen |
| Fragmentreferenz | *Ein Modelltyp* | Wird verwendet, um auf ein anderes Inhaltsfragment eines bestimmten Modelltyps zu verweisen, das beim Erstellen des Modells definiert wurde |

### Hilfsfelder {#helper-fields}

Zusätzlich zu den Datentypen für benutzergenerierte Felder generiert GraphQL für AEM eine Reihe von *Hilfsfeldern*, um ein Inhaltsfragment zu identifizieren oder zusätzliche Informationen zu einem Inhaltsfragment bereitzustellen.

#### Pfad {#path}

Das Feld „path“ (Pfad) wird in GraphQL als Bezeichner verwendet. Es stellt den Pfad des Inhaltsfragment-Assets im AEM Repository dar. Wir haben es als Bezeichner für ein Inhaltsfragment ausgewählt, da es:

* innerhalb von AEM eindeutig ist,
* leicht abgerufen werden kann.

Der folgende Code zeigt die Pfade aller Inhaltsfragmente an, die auf der Grundlage des Inhaltsfragmentmodells `Person` erstellt wurden.

```xml
{
  personList {
    items {
      _path
    }
  }
}
```

Um ein einzelnes Inhaltsfragment eines bestimmten Typs abzurufen, müssen Sie auch zuerst dessen Pfad bestimmen. Beispiel:

```xml
{
  personByPath(_path: "/content/dam/path/to/fragment/john-doe") {
    item {
      _path
      firstName
      name
    }
  }
}
```

>[!NOTE]
>
>Siehe Beispielabfrage – ein Einzelstadtfragment.

#### Metadaten {#metadata}

Mit GraphQL stellt AEM auch die Metadaten eines Inhaltsfragments zur Verfügung. Metadaten sind die Informationen, die ein Inhaltsfragment beschreiben, z. B. der Titel eines Inhaltsfragments, der Pfad der Miniaturansicht, die Beschreibung eines Inhaltsfragments, das Erstellungsdatum usw.

Da Metadaten über den Schema-Editor generiert werden und daher keine bestimmte Struktur haben, wurde der GraphQL-Typ `TypedMetaData` implementiert, um die Metadaten eines Inhaltsfragments anzuzeigen. `TypedMetaData` stellt die Informationen gruppiert nach den folgenden Skalartypen bereit:

| Feld |
|--- |
| `stringMetadata:[StringMetadata]!` |
| `stringArrayMetadata:[StringArrayMetadata]!` |
| `intMetadata:[IntMetadata]!` |
| `intArrayMetadata:[IntArrayMetadata]!` |
| `floatMetadata:[FloatMetadata]!` |
| `floatArrayMetadata:[FloatArrayMetadata]!` |
| `booleanMetadata:[BooleanMetadata]!` |
| `booleanArrayMetadata:[booleanArrayMetadata]!` |
| `calendarMetadata:[CalendarMetadata]!` |
| `calendarArrayMetadata:[CalendarArrayMetadata]!` |

Jeder Skalartyp repräsentiert entweder ein einzelnes Name-Wert-Paar oder ein Array von Name-Wert-Paaren, wobei der Wert dieses Paares dem Typ entspricht, in dem er gruppiert wurde.

Wenn Sie beispielsweise den Titel eines Inhaltsfragments abrufen möchten, wissen wir, dass diese Eigenschaft eine Zeichenfolgeneigenschaft ist. Daher würden wir eine Abfrage für alle Zeichenfolgenmetadaten durchführen:

Abfragen von Metadaten:

```xml
{
  personByPath(_path: "/content/dam/path/to/fragment/john-doe") {
    item {
      _path
      _metadata {
        stringMetadata {
          name
          value
        }
      }
    }
  }
}
```

Sie können alle GraphQL-Typen für Metadaten anzeigen, wenn Sie das generierte GraphQL-Schema anzeigen. Alle Modelltypen haben dieselben `TypedMetaData`.

>[!NOTE]
>
>**Unterschied zwischen normalen und Array-Metadaten**
>Beachten Sie, dass sich `StringMetadata` und `StringArrayMetadata` beide auf das beziehen, was im Repository gespeichert ist, und nicht darauf, wie Sie sie abrufen.
>
>Wenn Sie beispielsweise das Feld `stringMetadata` aufrufen, erhalten Sie ein Array aller im Repository gespeicherten Metadaten als `String` und wenn Sie `stringArrayMetadata` aufrufen, erhalten Sie ein Array aller Metadaten, die im Repository als `String[]` gespeichert wurden.

>[!NOTE]
>
>Weitere Informationen finden Sie unter Beispielabfrage für Metadaten – Liste der Metadaten für Auszeichnungen mit dem Titel „GB“.

#### Varianten {#variations}

Das Feld `_variations` wurde implementiert, um die Abfrage der Varianten eines Inhaltsfragments zu vereinfachen. Beispiel:

```xml
{
  personByPath(_path: "/content/dam/path/to/fragment/john-doe") {
    item {
      _variations
    }
  }
}
```

>[!NOTE]
>
>Weitere Informationen finden Sie unter Beispielabfrage – Alle Städte mit einer gegebenen Variante.

### AEM GraphQL-Variablen {#aem-graphql-variables}

Variablen sind in jeder Form der Programmierung oder Abfrage nützlich, da sie es Ihnen ermöglichen, unterschiedliche Werte an einem Ort zu speichern. Für AEM GraphQL bedeutet dies, dass Sie, anstatt für jeden Wert eine separate Abfrage schreiben zu müssen, Ihre Abfrage für eine Variable schreiben können. Der Wert dieser Variable kann sich bei Bedarf ändern.

Mit GraphQL können Variablen in die Abfrage eingefügt werden.

>[!NOTE]
>
>Weitere Informationen finden Sie in der GraphQL-Dokumentation für Variablen.

Um beispielsweise alle Inhaltsfragmente vom Typ `Article` abzurufen, die eine bestimmte Variante aufweisen, können Sie die Variable `variation` in GraphiQL angeben. Alle Instanzen werden in `GetArticlesByVariation` abgerufen und dann für die Verwendung in `articleList` übergeben.

![GraphQL-Variablen](assets/graphqlapi-variables.png "GraphQL-Variablen")

```xml
### query
query GetArticlesByVariation($variation: String!) {
    articleList(variation: $variation) {
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

### AEM GraphQL-Richtlinien {#aem-graphql-directives}

In GraphQL besteht die Möglichkeit, die Abfrage basierend auf Variablen zu ändern, die als GraphQL-Anweisungen bezeichnet werden.

Sie können beispielsweise das Feld `adventurePrice` basierend auf einer Variablen `includePrice` in eine Abfrage für alle `AdventureModels` einfügen.

!![GraphQL Directives](assets/graphqlapi-policies .png &quot;GraphQL richtlinien&quot;)

```xml
### query
query GetAdventureByType($includePrice: Boolean!) {
  adventureList {
    items {
      adventureTitle
      adventurePrice @include(if: $includePrice)
    }
  }
}
 
### in query variables
{
    "includePrice": true
}
```

### AEM GraphQL-Filter {#aem-graphql-filters}

Sie können auch Filterung in Ihren GraphQL-Abfragen verwenden, um bestimmte Daten zurückzugeben.

Beim Filtern wird eine Syntax verwendet, die auf logischen Operatoren und Ausdrücken basiert.

Beispielsweise werden mit der folgenden (einfachen) Abfrage alle Personen mit dem Namen `Jobs` oder `Smith` gefiltert:

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

Weitere Beispiele finden Sie unter:

* Details zu den Erweiterungen von GraphQL für AEM

* Beispielabfragen unter Verwendung dieses Beispielinhalts und dieser Beispielstruktur

### AEM GraphQL-Erweiterungen {#aem-graphql-extensions}

Die grundlegende Funktionsweise von Abfragen mit GraphQL für AEM entspricht der Standard-GraphQL-Spezifikation. Für GraphQL-Abfragen mit AEM gibt es einige Erweiterungen:

* Wenn Sie ein einzelnes Ergebnis benötigen:
   * Verwenden Sie den Modellnamen, z. B. „city“

* Wenn Sie eine Ergebnisliste erwarten:
   * Fügen Sie `List` zum Modellnamen hinzu, z. B. `cityList`
   * Siehe [Beispielabfrage – Alle Informationen zu allen Städten](#sample-all-information-all-cities)

* Wenn Sie ein logisches ODER verwenden möchten:
   * Verwenden Sie ` _logOp: OR`
   * [Beispielabfrage – Alle Personen mit dem Namen „Jobs“ oder „Smith“](#sample-all-persons-jobs-smith)

* Es gibt ebenfalls ein logisches UND, es ist aber (oft) implizit.

* Sie können Feldnamen abfragen, die den Feldern im Inhaltsfragmentmodell entsprechen.
   * [Beispielabfrage – Vollständige Details über den CEO und die Mitarbeiter eines Unternehmens](#sample-full-details-company-ceos-employees)

* Zusätzlich zu den Feldern Ihres Modells gibt es einige systemgenerierte Felder (vor dem Unterstrich):

   * Für Inhalte:

      * `_locale`: Anzeigen der Sprache; basierend auf Language Manager
         * Siehe [Beispielabfrage für mehrere Inhaltsfragmente eines bestimmten Gebietsschemas](#sample-wknd-multiple-fragments-given-locale)
      * `_metadata`: Anzeigen von Metadaten für Ihr Fragment
         * Siehe [Beispielabfrage für Metadaten – Liste der Metadaten für Auszeichnungen mit dem Titel „GB“](#sample-metadata-awards-gb)
      * `_model`: Zulassen von Abfragen nach einem Inhaltsfragmentmodell (Pfad und Titel)
         * Siehe [Beispielabfrage für ein Inhaltsfragmentmodell anhand eines Modells](#sample-wknd-content-fragment-model-from-model)
      * `_path` : den Pfad zu Ihrem Inhaltsfragment im Repository
         * Siehe [Beispielabfrage – ein Einzelstadtfragment](#sample-single-specific-city-fragment)
      * `_reference`: Anzeigen von Verweisen; einschließlich Inline-Verweisen im Rich-Text-Editor
         * Siehe [Beispielabfrage für mehrere Inhaltsfragmente mit vorab abgerufenen Verweisen](#sample-wknd-multiple-fragments-prefetched-references)
      * `_variation`: Anzeige bestimmter Varianten in Ihrem Inhaltsfragment
         * Weitere Informationen finden Sie unter [Beispielabfrage – Alle Städte mit einer gegebenen Variante](#sample-cities-named-variation)
   * Und Operationen:

      * `_operator`: bestimmte Operatoren anwenden; `EQUALS`, `EQUALS_NOT`, `GREATER_EQUAL`, `LOWER`, `CONTAINS`, `STARTS_WITH`
         * Siehe [Beispielabfrage – Alle Personen, die nicht den Namen „Jobs“ haben](#sample-all-persons-not-jobs)
         * Siehe [Beispielversion - Alle Abenteuer, bei denen die `_path`-Beginn mit einem bestimmten Präfix](#sample-wknd-all-adventures-cycling-path-filter)
      * `_apply`: bestimmte Bedingungen anwenden; zum Beispiel `AT_LEAST_ONCE`
         * Siehe [Beispielabfrage – Filtern eines Arrays nach einem Element, das mindestens einmal vorkommen muss](#sample-array-item-occur-at-least-once)
      * `_ignoreCase`: Groß-/Kleinschreibung bei der Abfrage ignorieren
         * Siehe [Beispielabfrage – Alle Städte mit SAN im Namen, unabhängig von der Groß-/Kleinschreibung](#sample-all-cities-san-ignore-case)









* GraphQL-Vereinigungstypen werden unterstützt:

   * Verwenden Sie `... on`
      * Siehe [Beispielabfrage für ein Inhaltsfragment eines bestimmten Modells mit einer Inhaltsreferenz](#sample-wknd-fragment-specific-model-content-reference)

### Persistente Abfragen (Caching) {#persisted-queries-caching}

Nachdem eine Abfrage mit einer POST-Anfrage vorbereitet wurde, kann sie mit einer GET-Anfrage ausgeführt werden, die von HTTP-Caches oder einem CDN zwischengespeichert werden kann.

Dies ist erforderlich, da POST-Abfragen normalerweise nicht zwischengespeichert werden. Wenn Sie GET mit der Abfrage als Parameter verwenden, besteht ein erhebliches Risiko, dass der Parameter für HTTP-Services und Vermittler zu groß wird.

Beständige Abfragen müssen immer den Endpunkt für die entsprechende (Mandant-)Konfiguration verwenden. damit sie entweder

* Globale Konfiguration und Endpunkt
Die Abfrage hat Zugriff auf alle Inhaltsfragmentmodelle.
* Spezifische Mandantenkonfiguration(en) und Endpunkte
Zum Erstellen einer beständigen Abfrage für eine bestimmte Mandantenkonfiguration ist ein entsprechender tendenzieller Endpunkt erforderlich (um Zugriff auf die entsprechenden Inhaltsfragmentmodelle zu gewähren).
Um beispielsweise eine persistente Abfrage speziell für den WKND-Mandanten zu erstellen, müssen im Voraus eine entsprechende WKND-spezifische Mandantenkonfiguration und ein WKND-spezifischer Endpunkt erstellt werden.

>[!NOTE]
>
>Weitere Informationen finden Sie unter Aktivieren der Inhaltsfragmentfunktionen im Konfigurations-Browser.
>
>Die **GraphQL Persistence Abfragen** müssen für die entsprechende Mandantenkonfiguration aktiviert werden.

Wenn es beispielsweise eine bestimmte Abfrage namens `my-query` gibt, die ein Modell `my-model` aus der Mandant-Konfiguration `my-conf` verwendet:

* Sie können eine Abfrage mit dem spezifischen Endpunkt `my-conf` erstellen und die Abfrage wird wie folgt gespeichert:
   `/conf/my-conf/settings/graphql/persistentQueries/my-query`
* Sie können die gleiche Abfrage mit dem Endpunkt `global` erstellen. Anschließend wird die Abfrage jedoch wie folgt gespeichert:
   `/conf/global/settings/graphql/persistentQueries/my-query`

>[!NOTE]
>
>Dies sind zwei verschiedene Abfragen - die unter verschiedenen Pfaden gespeichert werden.
>
>Sie verwenden zufällig das gleiche Modell - aber über verschiedene Endpunkte.

Die folgenden Schritte sind erforderlich, um eine bestimmte Abfrage beizubehalten:

1. Bereiten Sie die Abfrage mittels einer PUT-Anfrage an die neue Endpunkt-URL `/graphql/persist.json/<config>/<persisted-label>` vor.

   Erstellen Sie beispielsweise eine persistente Abfrage:

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

   Prüfen Sie zum Beispiel auf Erfolg:

   ```xml
   {
     "action": "create",
     "configurationName": "wknd",
     "name": "plain-article-query",
     "shortPath": "/wknd/plain-article-query",
     "path": "/conf/wknd/settings/graphql/persistentQueries/plain-article-query"
   }
   ```

1. Sie können die persistente Abfrage dann erneut ausführen, indem Sie die URL `/graphql/execute.json/<shortPath>` per GET-Anfrage abrufen.

   Verwenden Sie zum Beispiel die persistente Abfrage:

   ```xml
   $ curl -X GET \
       http://localhost:4502/graphql/execute.json/wknd/plain-article-query
   ```

1. Aktualisieren Sie eine persistente Abfrage mittels POST-Anfrage an einen bereits vorhandenen Abfragepfad.

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

1. Erstellen Sie eine umschlossene einfache Abfrage.

   Beispiel:

   ```xml
   $ curl -X PUT \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-wrapped" \
       -d \
   '{ "query": "{articleList { items { _path author main { json } referencearticle { _path } } } }"}'
   ```

1. Erstellen Sie eine umschlossene Abfrage mit Cache-Steuerung.

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

   * Verwenden einer POST-Anfrage für die Replikation:

      ```xml
      $curl -X POST   http://localhost:4502/bin/replicate.json \
        -H 'authorization: Basic YWRtaW46YWRtaW4=' \
        -F path=/conf/wknd/settings/graphql/persistentQueries/plain-article-query \
        -F cmd=activate
      ```

   * Verwenden eines Pakets:
      1. Erstellen Sie eine neue Paketdefinition.
      1. Fügen Sie die Konfiguration ein (z. B. `/conf/wknd/settings/graphql/persistentQueries`).
      1. Erstellen Sie das Paket.
      1. Replizieren Sie das Paket.
   * Verwenden eines Replikations-/Verteilungs-Tools:
      1. Wechseln Sie zum Verteilungs-Tool.
      1. Wählen Sie die Baumaktivierung für die Konfiguration (z. B. `/conf/wknd/settings/graphql/persistentQueries`) aus.
   * Verwenden eines Workflows (über die Workflow-Starter-Konfiguration):
      1. Definieren Sie eine Workflow-Starterregel zum Ausführen eines Workflow-Modells, das die Konfiguration für verschiedene Ereignisse repliziert (z. B. Erstellen, Ändern).



1. Sobald die Abfragekonfiguration veröffentlicht wurde, gelten dieselben Prinzipien, nur unter Verwendung des Veröffentlichungsendpunkts.

   >[!NOTE]
   >
   >Für den anonymen Zugriff geht das System davon aus, dass „jeder“ über die ACL Zugriff auf die Abfragekonfiguration hat.
   >
   >Ist dies nicht der Fall, kann sie nicht ausgeführt werden.

   >[!NOTE]
   >
   >Alle Semikolons („;“) in den URLs müssen kodiert werden.
   >
   >Beispiel: Wie in der Anfrage zum Ausführen einer persistenten Abfrage:
   >
   >
   ```xml
   >curl -X GET \ "http://localhost:4502/graphql/execute.json/wknd/plain-article-query-parameters%3bapath=%2fcontent2fdam2fwknd2fen2fmagazine2falaska-adventure2falaskan-adventures;withReference=false"
   >```

### Abfragen des GraphQL-Endpunkts von einer externen Website {#query-graphql-endpoint-from-external-website}

Für den Zugriff auf den GraphQL-Endpunkt über eine externe Website müssen Sie Folgendes konfigurieren:

* CORS-Filter
* Werber-Filter

#### CORS-Filter {#cors-filter}

>[!NOTE]
>
>Einen detaillierten Überblick über die CORS-Richtlinie zur gemeinsamen Nutzung von Ressourcen in AEM finden Sie unter Grundlegendes zur gemeinsamen Nutzung gemeinsamer Ressourcen (Cross-Origin Resource Sharing – CORS).

Um auf den GraphQL-Endpunkt zugreifen zu können, muss eine CORS-Richtlinie im Customer Git-Repository konfiguriert werden. Dazu fügen Sie eine entsprechende OSGi CORS-Konfigurationsdatei für den/die gewünschten Endpunkt/en hinzu.

Diese Konfiguration muss eine vertrauenswürdige Website-Herkunft `alloworigin` oder `alloworiginregexp` angeben, für die der Zugriff gewährt werden muss.

Um beispielsweise Zugriff auf den GraphQL-Endpunkt und den Endpunkt für beständige Abfragen für `https://my.domain` zu gewähren, können Sie Folgendes verwenden:

```xml
{
  "supportscredentials":true,
  "supportedmethods":[
    "GET",
    "HEAD",
    "POST"
  ],
  "exposedheaders":[
    ""
  ],
  "alloworigin":[
    "https://my.domain"
  ],
  "maxage:Integer":1800,
  "alloworiginregexp":[
    ""
  ],
  "supportedheaders":[
    "Origin",
    "Accept",
    "X-Requested-With",
    "Content-Type",
    "Access-Control-Request-Method",
    "Access-Control-Request-Headers"
  ],
  "allowedpaths":[
    "/content/_cq_graphql/global/endpoint.json",
    "/graphql/execute.json/.*"
  ]
}
```

Wenn Sie einen Vanity-Pfad für den Endpunkt konfiguriert haben, können Sie ihn auch in `allowedpaths` verwenden.

#### Werber-Filter {#referrer-filter}

Zusätzlich zur CORS-Konfiguration muss ein Werber-Filter konfiguriert werden, um den Zugriff von Drittanbieterhosts zu ermöglichen.

Dazu fügen Sie eine entsprechende OSGi-Werber-Konfigurationsdatei hinzu, die Folgendes beinhaltet:

* gibt einen Hostnamen der vertrauenswürdigen Website an. entweder `allow.hosts` oder `allow.hosts.regexp`,
* gewährt Zugriff auf diesen Hostnamen.

Wenn Sie beispielsweise mit dem Werber `my.domain` Zugriff auf Anforderungen gewähren möchten, können Sie:

```xml
{
    "allow.empty":false,
    "allow.hosts":[
      "my.domain"
    ],
    "allow.hosts.regexp":[
      ""
    ],
    "filter.methods":[
      "POST",
      "PUT",
      "DELETE",
      "COPY",
      "MOVE"
    ],
    "exclude.agents.regexp":[
      ""
    ]
}
```

>[!CAUTION]
>
>Der Kunde ist für Folgendes verantwortlich:
>
>* Nur Zugriff auf vertrauenswürdige Domains gewähren
>* Sicherstellen, dass keine vertraulichen Informationen offengelegt werden
>* Keine Platzhaltersyntax [*] verwenden. Dadurch wird der authentifizierte Zugriff auf den GraphQL-Endpunkt deaktiviert und zusätzlich der Öffentlichkeit zugänglich gemacht.


>[!CAUTION]
>
>Alle GraphQL-Schemas (abgeleitet von Inhaltsfragmentmodellen, die **aktiviert** wurden) sind über den GraphQL-Endpunkt lesbar.
>
>Das bedeutet, dass Sie sicherstellen müssen, dass keine vertraulichen Daten verfügbar sind, da sie auf diese Weise an die Öffentlichkeit gelangen könnten. Dazu gehören beispielsweise Informationen, die als Feldnamen in der Modelldefinition vorhanden sein könnten.

### AEM GraphQL-Authentifizierung {#aem-graphql-authentication}

Ein primäres Anwendungsbeispiel für das Adobe Experience Manager als Cloud Service (AEM) GraphQL API für Content Fragment Versand ist die Annahme von Remote-Abfragen von Drittanbieteranwendungen oder -diensten. Diese Remote-Abfragen erfordern möglicherweise einen authentifizierten API-Zugriff, um den Versand von kostenlosen Inhalten zu sichern.

>[!NOTE]
>
>Für Tests und Entwicklung können Sie auch direkt über die GraphiQL-Schnittstelle auf die AEM GraphQL-API zugreifen.

Zur Authentifizierung muss der Drittanbieter-Service ein Zugriffs-Token verwenden, das dann in der GraphQL-Anfrage verwendet werden kann.

#### Abrufen eines Zugriffs-Tokens {#retrieving-access-token}

Ausführliche Informationen finden Sie unter Generieren von Zugriffs-Token für Server-seitige APIs.

#### Verwenden des Zugriffs-Tokens in einer GraphQL-Anfrage {#use-access-token-in-graphql-request}

Damit ein Drittanbieter-Service eine Verbindung mit einer AEM-Instanz herstellen kann, benötigt er ein *Zugriffs-Token*. Der Service muss dieses Token dann der `Authorization`-Kopfzeile in der POST-Anfrage hinzufügen.

Ein Beispiel für eine GraphQL-Autorisierungskopfzeile:

```xml
Authorization: Bearer <access_token>
```

#### Berechtigungsanforderungen {#permission-requirements}

Alle Anfragen, die mit dem Zugriffs-Token durchgeführt werden, werden tatsächlich *von dem Benutzerkonto ausgeführt, das das Token generiert hat*

Dies bedeutet, dass Sie überprüfen müssen, ob das Konto über die erforderlichen Berechtigungen zum Ausführen von GraphQL-Abfragen verfügt.

Sie können dies überprüfen, indem Sie GraphiQL auf der lokalen Instanz verwenden.

## Beispiele für AEM GraphQL-Abfragen {#samples-aem-graphql-queries}

Unter Verwendung von GraphQL mit AEM - Beispielinhalt und Abfragen finden Sie eine umfassende Palette von Abfragen.

<!--
## Code Samples for AEM GraphQL Queries {#code-samples-aem-graphql-queries}
-->

## Wie geht es weiter {#whats-next}

Nachdem Sie nun gelernt haben, wie Sie mit der AEM GraphQL API auf Ihre kostenlosen Inhalte zugreifen und diese Abfrage durchführen können, können Sie jetzt [lernen, wie Sie mit der REST-API auf den Inhalt Ihrer Inhaltsfragmente zugreifen und diese aktualisieren können.](/help/implementing/developing/headless-journey/update-your-content.md)

## Zusätzliche Ressourcen {#additional-resources}

* [GraphQL.org](https://graphql.org)
   * [Schemas](https://graphql.org/learn/Schema/)
   * [Variablen](https://graphql.org/learn/queries/#variables)
   * [GraphQL Java-Bibliotheken](https://graphql.org/code/#java)
* [GraphiQL](https://graphql.org/learn/serving-over-http/#graphiql)
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
* [Erste Schritte mit AEM Headless](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html?lang=de)  - Eine kurze Videoschulung, die einen Überblick über die Verwendung AEM kopflosen Funktionen bietet, einschließlich Datenmodellierung und GraphQL.
