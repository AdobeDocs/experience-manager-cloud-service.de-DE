---
title: Adobe Experience Manager als Content Fragments-Unterstützung für Cloud-Dienste in der Assets-HTTP-API
description: Erfahren Sie mehr über Adobe Experience Manager als Unterstützung für Inhaltsfragmente der Cloud in der Asset-HTTP-API.
translation-type: tm+mt
source-git-commit: a5d6a072dfd8df887309f56ad4a61b6b38b32fa7

---


# Unterstützung von Inhaltsfragmenten in der AEM Assets-HTTP-API{#content-fragments-support-in-aem-assets-http-api}

## Übersicht {#overview}

>[!NOTE]
>
>Die [Assets-HTTP-API](/help/assets/mac-api-assets.md) umfasst:
>
>* Assets-REST-API
>* einschließlich Unterstützung für Inhaltsfragmente
>
>
Die aktuelle Implementierung der Assets HTTP API basiert auf dem [REST](https://de.wikipedia.org/wiki/Representational_State_Transfer) -Architekturstil.

Die REST-API [für](/help/assets/mac-api-assets.md) Assets ermöglicht Entwicklern von Adobe Experience Manager als Cloud-Dienst den direkten Zugriff auf (in AEM gespeicherte) Inhalte über die HTTP-API über CRUD-Vorgänge (Erstellen, Lesen, Aktualisieren, Löschen).

Mit der API können Sie Adobe Experience Manager als Cloud-Dienst als kostenloses CMS (Content-Management-System) betreiben, indem Sie Content Services für eine JavaScript-Frontend-Anwendung bereitstellen. Oder jeder anderen Applikation, die HTTP-Anforderungen ausführen und JSON-Antworten verarbeiten kann.

Beispielsweise benötigen frameworkbasierte oder benutzerdefinierte Single-Page-Applikationen (SPA), die über die HTTP-API bereitgestellten Inhalte häufig im JSON-Format.

While [AEM Core Components](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/introduction.html) provide a very comprehensive, flexible and customizable API that can serve required Read operations for this purpose, and whose JSON output can be customized, they do require AEM WCM (Web Content Management) know-how for implementation as they must be hosted in pages that are based on dedicated AEM templates. Nicht jede SPA-Entwicklungsorganisation hat direkten Zugang zu solchen Kenntnissen.

Hier kann die Assets-REST-API eingesetzt werden. Es ermöglicht Entwicklern, direkt auf Assets (z. B. Bilder und Inhaltsfragmente) zuzugreifen, ohne sie zuerst in eine Seite einbetten zu müssen, und ihre Inhalte im serialisierten JSON-Format bereitzustellen.

>[!NOTE]
>
>Es ist nicht möglich, die JSON-Ausgabe über die Assets REST API anzupassen.

Mit der Assets-REST-API können Entwickler Inhalte ändern, indem sie neue Assets erstellen, aktualisieren oder vorhandene Assets, Inhaltsfragmente und Ordner löschen.

Die Assets-REST-API:

* folgt dem [HATEOAS-Prinzip](https://en.wikipedia.org/wiki/HATEOAS)

* implementiert das [SIREN-Format](https://github.com/kevinswiber/siren)

## Voraussetzungen {#prerequisites}

Die REST-API für Assets steht bei jeder vordefinierten Installation von Adobe Experience Manager als Cloud-Service-Version zur Verfügung.

## Schlüsselkonzepte {#key-concepts}

Die Assets-REST-API bietet [REST](https://de.wikipedia.org/wiki/Representational_State_Transfer)-ähnlichen Zugriff auf Assets, die in einer AEM-Instanz gespeichert sind.

It uses the `/api/assets` endpoint and requires the path of the asset to access it (without the leading `/content/dam`).

* Das bedeutet, dass der Zugriff auf das Asset unter
   * `/content/dam/path/to/asset`
* Sie müssen Folgendes anfordern:
   * `/api/assets/path/to/asset`

Um beispielsweise auf `/content/dam/wknd/en/adventures/cycling-tuscany`die `/api/assets/wknd/en/adventures/cycling-tuscany.json`

>[!NOTE]
>Zugriff auf:
>* `/api/assets` Die Verwendung der **Auswahl** ist nicht `.model` erforderlich.
>* `/content/assets` Die **Verwendung der** Auswahl ist `.model` erforderlich.


Die HTTP-Methode ermittelt den auszuführenden Vorgang:

* **GET** - zum Abrufen einer JSON-Darstellung eines Assets oder Ordners
* **POST** - zum Erstellen neuer Assets oder Ordner
* **PUT** - zum Aktualisieren der Eigenschaften eines Assets oder Ordners
* **LÖSCHEN** - Löschen eines Assets oder Ordners

>[!NOTE]
>
>Mit dem Anforderungstext und/oder den URL-Parametern können Sie einige dieser Vorgänge konfigurieren. Sie definieren damit beispielsweise, dass ein Ordner oder ein Asset über eine **POST**-Anforderung erstellt werden soll.

<!--
The exact format of supported requests is defined in the [API Reference](/help/assets/assets-api-content-fragments.md#api-reference) documentation.
-->

### Transaktionsverhalten {#transactional-behavior}

Alle Anforderungen sind atomisch.

Dies bedeutet, dass die folgenden (`write`-)Anforderungen nicht in einer einzelnen Transaktion kombiniert werden können, die als einzelne Entität ausgeführt werden oder fehlschlagen könnte.

### AEM (Assets)-REST-API und AEM-Komponenten im Vergleich {#aem-assets-rest-api-versus-aem-components}

<table>
 <thead>
  <tr>
   <td>Aspekt</td>
   <td>Assets-REST-API<br/> </td>
   <td>AEM-Komponente<br/> (Komponenten mit Sling-Modellen)</td>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td>Geeignete Nutzungsszenarien</td>
   <td>Universell.</td>
   <td><p>Optimiert für den Einsatz in einer Single-Page-Applikation (SPA) oder in einem beliebigen anderen Kontext (Inhalt verbrauchend).</p> <p>Kann auch Layoutinformationen enthalten.</p> </td>
  </tr>
  <tr>
   <td>Unterstützte Vorgänge</td>
   <td><p>Erstellen, Lesen, Aktualisieren, Löschen.</p> <p>Weitere Vorgänge abhängig von Entitätstyp.</p> </td>
   <td>Schreibgeschützt.</td>
  </tr>
  <tr>
   <td>Zugriff</td>
   <td><p>Direkter Zugriff möglich.</p> <p>Uses the <code>/api/assets </code>endpoint, mapped to <code>/content/dam</code> (in the repository).</p> 
   <p>Ein Beispielpfad würde wie folgt aussehen: <code>/api/assets/wknd/en/adventures/cycling-tuscany.json</code></p>
   </td>
    <td><p>Muss über eine AEM-Komponente auf einer AEM-Seite referenziert werden.</p> <p>Uses the <code>.model</code> selector to create the JSON representation.</p> <p>Ein Beispielpfad würde wie folgt aussehen:<br/> <code>/content/wknd/language-masters/en/adventures/cycling-tuscany.model.json</code></p> 
   </td>
  </tr>
  <tr>
   <td>Sicherheit</td>
   <td><p>Mehrere Optionen sind möglich.</p> <p>OAuth wird vorgeschlagen und kann separat von der obigen Standardeinrichtung konfiguriert werden.</p> </td>
   <td>Verwendet die oben beschriebene Standardeinrichtung von AEM.</td>
  </tr>
  <tr>
   <td>Anmerkungen zur Architektur</td>
   <td><p>Der Schreibzugriff gilt in der Regel für eine Autoreninstanz.</p> <p>Der Lesezugriff kann auch an eine Veröffentlichungsinstanz weitergeleitet werden.</p> </td>
   <td>Da dieser Vorgang schreibgeschützt ist, wird er in der Regel für Veröffentlichungsinstanzen verwendet.</td>
  </tr>
  <tr>
   <td>Ausgabe</td>
   <td>JSON-basierte SIREN-Ausgabe: ausführlich, aber leistungsstark. Ermöglicht die Navigation innerhalb des Inhalts.</td>
   <td>JSON-basierte proprietäre Ausgabe über Sling-Modelle konfigurierbar. Die Navigation durch die Inhaltsstruktur ist schwer zu implementieren (jedoch nicht unmöglich).</td>
  </tr>
 </tbody>
</table>

### Sicherheit {#security}

Wenn die Assets-REST-API in einer Umgebung ohne spezifische Authentifizierungsanforderungen verwendet wird, muss der CORS-Filter von AEM richtig konfiguriert werden.

>[!NOTE]
>
>Weitere Informationen finden Sie unter:
>
>* [Erklärung: CORS/AEM](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/cors-security-article-understand.html) 
>* [Video: Entwicklung für CORS mit AEM](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/cors-security-technical-video-develop.html)
>



In Umgebungen mit bestimmten Authentifizierungsanforderungen wird OAuth empfohlen.

## Verfügbare Funktionen {#available-features}

Inhaltsfragmente sind eine bestimmte Art von Assets. Informationen finden Sie unter [Arbeiten mit Inhaltsfragmenten](/help/assets/content-fragments/content-fragments.md).

Weitere Informationen zu den über die APIs verfügbaren Funktionen:

* The [Assets REST API](/help/assets/mac-api-assets.md)
* [Entitätstypen](/help/assets/assets-api-content-fragments.md#entity-types), bei denen die für jeden unterstützten Typ spezifischen Funktionen (je nach Relevanz für Inhaltsfragmente) erläutert werden

### Paging {#paging}

Die Assets-REST-API unterstützt Paging (für GET-Anforderungen) über die URL-Parameter:

* `offset` - die Nummer der ersten abzurufenden (untergeordneten) Entität
* `limit` - die maximale Anzahl zurückgegebener Entitäten

The response will contain paging information as part of the `properties` section of the SIREN output. This `srn:paging` property contains the total number of (child) entities ( `total`), the offset and the limit ( `offset`, `limit`) as specified in the request.

>[!NOTE]
>
>Paging wird normalerweise auf Containerentitäten (d. h. Ordner oder Assets mit Ausgabeformaten) angewendet, da sie auf die untergeordneten Objekte des angeforderten Elements verweisen.

#### Beispiel: Paging {#example-paging}

`GET /api/assets.json?offset=2&limit=3`

```
...
"properties": {
    ...
    "srn:paging": {
        "total": 7,
        "offset": 2,
        "limit": 3
    }
    ...
}
...
```

## Entitätstypen {#entity-types}

### Ordner {#folders}

Ordner dienen als Container für Assets und andere Ordner. Ihre Struktur entspricht den Inhaltsrepositorys von AEM.

Die Assets-REST-API gewährt Zugriff auf die Eigenschaften eines Ordners, z. B. Name, Titel, usw. Assets werden als untergeordnete Entitäten von Ordnern und Unterordnern bereitgestellt.

>[!NOTE]
>
>Je nach Asset-Typ der untergeordneten Assets und Ordner enthält die Liste der untergeordneten Entitäten möglicherweise bereits den vollständigen Satz von Eigenschaften, die die jeweilige untergeordnete Entität definieren. Alternativ werden einer Entität in dieser Liste der untergeordneten Entitäten möglicherweise nicht alle Eigenschaften bereitgestellt.

### Assets {#assets}

Wenn ein Asset angefordert wird, gibt die Antwort die zugehörigen Metadaten zurück. wie Titel, Name und andere vom jeweiligen Asset-Schema definierte Informationen.

The binary data of an asset is exposed as a SIREN link of type `content` (also known as the `rel attribute`).

Assets können mehrere Ausgabeformate aufweisen. These are typically exposed as child entities, one exception being a thumbnail rendition, which is exposed as a link of type `thumbnail` ( `rel="thumbnail"`).

### Inhaltsfragmente {#content-fragments}

Ein [Inhaltsfragment](/help/assets/content-fragments/content-fragments.md) ist ein spezieller Asset-Typ. Sie können zum Zugriff auf strukturierte Daten wie Texte, Zahlen, Daten usw. verwendet werden.

Da es einige Unterschiede zu *Standard*-Assets (z. B. Bildern oder Audio) aufweist, gelten einige zusätzliche Regeln für die Verarbeitung.

#### Darstellung {#representation}

Inhaltsfragmente:

* stellen keine Binärdaten bereit.
* Are completely contained in the JSON output (within the `properties` property).

* Gelten auch als atomisch, d. h. die Elemente und Varianten werden als Teil der Eigenschaften des Fragments anstatt als Links oder untergeordnete Entitäten bereitgestellt. Dies ermöglicht einen effiziente Zugriff auf die Nutzlast eines Fragments.

#### Inhaltsmodelle und Inhaltsfragmente {#content-models-and-content-fragments}

Derzeit werden die Modelle, die die Struktur eines Inhaltsfragments definieren, nicht über eine HTTP-API bereitgestellt. Daher benötigt der *Benutzer* (zumindest einige) Informationen über das Modell eines Fragments. Die meisten Informationen kann er jedoch aus der Nutzlast ableiten. So sind z. B. Datentypen Teil der Definition.

Um ein neues Inhaltsfragment zu erstellen, muss der Pfad des Modells (internes Repository) angegeben werden.

#### Zugehörige Inhalte {#associated-content}

Zugehöriger Inhalt wird derzeit nicht bereitgestellt.

## Verwendung {#using}

Die Verwendung unterscheidet sich je nachdem, ob Sie eine AEM-Autoren- oder Veröffentlichungsumgebung zusammen mit Ihrem spezifischen Verwendungsszenario verwenden.

* Die Erstellung ist nur in einer Autoreninstanz möglich ([und derzeit gibt es keine Möglichkeit, ein Fragment mit dieser API für die Veröffentlichungsinstanz zu replizieren](/help/assets/assets-api-content-fragments.md#limitations)). 
* Die Bereitstellung ist in beiden Umgebungen möglich, da AEM angeforderte Inhalte nur im JSON-Format bereitstellt.

   * Das Speichern und Bereitstellen über eine AEM-Autoreninstanz sollte für Mediathekanwendungen hinter einer Firewall ausreichen.

   * Für die Live-Web-Bereitstellung wird eine AEM-Veröffentlichungsinstanz empfohlen.

>[!CAUTION]
>
>Die Dispatcher-Konfiguration auf AEM-Cloudinstanzen blockiert möglicherweise den Zugriff auf `/api`.

<!--
>[!NOTE]
>
>For further details, see the [API Reference](/help/assets/assets-api-content-fragments.md#api-reference). In particular, [Adobe Experience Manager Assets API - Content Fragments](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/assets-api-content-fragments/index.html). 
-->

### Lesen/Bereitstellen {#read-delivery}

Nutzung erfolgt über:

`GET /{cfParentPath}/{cfName}.json`

Beispiel:

`http://<host>/api/assets/wknd/en/adventures/cycling-tuscany.json`

Die Antwort ist serialisierter JSON mit dem im Inhaltsfragment strukturierten Inhalt. Verweise werden als Referenz-URLs bereitgestellt. 

Zwei Arten von Lesevorgängen sind möglich:

* Beim Lesen eines spezifischen Inhaltsfragments über einen Pfad gibt diese Methode die JSON-Darstellung des Inhaltsfragments zurück. 
* Ordner mit Inhaltsfragmenten nach Pfad lesen: gibt die JSON-Darstellungen aller Inhaltsfragmente im Ordner zurück.

### Erstellen {#create}

Nutzung erfolgt über:

`POST /{cfParentPath}/{cfName}`

Der Hauptteil muss eine JSON-Darstellung des zu erstellenden Inhaltsfragments enthalten – einschließlich des anfänglichen Inhalts, der für Inhaltsfragmentelemente festgelegt werden soll. It is mandatory to set the `cq:model` property and it must point to a valid content fragment model. Andernfalls tritt ein Fehler auf. It is also necessary to add a header `Content-Type` which is set to `application/json`.

### Update {#update}

Nutzung erfolgt über

`PUT /{cfParentPath}/{cfName}`

Der Hauptteil muss eine JSON-Darstellung davon enthalten, was für das angegebene Inhaltsfragment aktualisiert werden soll.

Dies kann einfach der Titel oder die Beschreibung eines Inhaltsfragments bzw. ein einzelnes Element oder alle Elementwerte und/oder Metadaten sein.

### Löschen Sie {#delete}

Nutzung erfolgt über:

`DELETE /{cfParentPath}/{cfName}`

## Beschränkungen {#limitations}

Es gibt einige Einschränkungen: 

* **Varianten können weder geschrieben noch aktualisiert werden.** Werden diese Varianten einer Nutzlast hinzugefügt (z. B. für Aktualisierungen), werden sie ignoriert. Jedoch ist die Variante über die Bereitstellung verfügbar ( `GET`).

* **Inhaltsfragmentmodelle werden derzeit nicht unterstützt**: sie können weder gelesen noch erstellt werden. Zum Erstellen eines neuen oder Aktualisieren eines vorhandenen Inhaltsfragments müssen Entwickler den richtigen Pfad zum Inhaltsfragmentmodell kennen. Derzeit ist dies lediglich über die Verwaltungsoberfläche möglich. 
* **Verweise werden ignoriert**. Zurzeit sind keine Überprüfungen für Verweise auf vorhandene Inhaltsfragmente verfügbar. Das Löschen eines Inhaltsfragments kann daher zu Problemen auf einer Seite führen, die einen Verweis auf das gelöschte Inhaltsfragment enthält.

## Statuscodes und Fehlermeldungen {#status-codes-and-error-messages}

Unter den entsprechenden Voraussetzungen werden möglicherweise die folgenden Statuscodes angezeigt:

1. 200 (OK)

   Wird zurückgegeben, wenn:

   * requesting a content fragment via `GET`

   * successfully updating a content fragment via `PUT`

1. 201 (Erstellt)

   Wird zurückgegeben, wenn:

   * successfully creating a content fragment via `POST`

1. 404 (Nicht gefunden)

   Wird zurückgegeben, wenn:

   * das angeforderte Inhaltsfragment nicht vorhanden ist

1. 500 (Interner Serverfehler)

   >[!NOTE]
   >
   >Dieser Fehler wird zurückgegeben:
   >
   >    * wenn ein Fehler, der mit keinem bestimmten Code identifiziert werden kann, aufgetreten ist 
   >    * wenn als Nutzlast „null“ angegeben ist


   Nachfolgend finden Sie allgemeine Szenarien, in denen dieser Fehlerstatus in Kombination mit der Fehlermeldung (monospace) zurückgegeben wird:

   * Übergeordneter Ordner ist nicht vorhanden (wenn ein Inhaltsfragment per `POST` erstellt wurde)
   * Es wird kein Inhaltsfragmentmodell bereitgestellt (cq:model fehlt), es kann nicht gelesen werden (aufgrund eines ungültigen Pfads oder eines Berechtigungsproblems) oder es gibt kein gültiges Fragmentmodell/keine gültige Vorlage:

      * `No content fragment model specified`
      * `Cannot create a resource of given model '/foo/bar/qux'`
      * `Cannot adapt the resource '/foo/bar/qux' to a content fragment template`
   * Das Inhaltsfragment konnte nicht erstellt werden (möglicherweise ein Berechtigungsproblem):

      * `Could not create content fragment`
   * Titel oder Beschreibung und konnte nicht aktualisiert werden:

      * `Could not set value on content fragment`
   * Metadaten konnten nicht festgelegt werden:

      * `Could not set metadata on content fragment`
   * Inhaltselement wurde nicht gefunden oder konnte nicht aktualisiert werden

      * `Could not update content element`
      * `Could not update fragment data of element`
   Die detaillierten Fehlermeldungen werden im Allgemeinen im folgenden Typ zurückgegeben:

   ```xml
   {
     "class": "core/response",
     "properties": {
       "path": "/api/assets/foo/bar/qux",
       "location": "/api/assets/foo/bar/qux.json",
       "parentLocation": "/api/assets/foo/bar.json",
       "status.code": 500,
       "status.message": "...{error message}.."
     }
   }
   ```

## API-Referenz {#api-reference}

Hier finden Sie detaillierte API-Referenzen:
<!--
* [Adobe Experience Manager Assets API - Content Fragments](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/assets-api-content-fragments/index.html)
-->

* [Assets-HTTP-API](/help/assets/mac-api-assets.md)

   * [Verfügbare Funktionen](/help/assets/mac-api-assets.md#available-features)

## Zusätzliche Ressourcen {#additional-resources}

Weitere Informationen finden Sie unter:

* [Assets-HTTP-API – Dokumentation ](/help/assets/mac-api-assets.md)
* [AEM Gem-Sitzung: OAuth](https://helpx.adobe.com/experience-manager/kt/eseminars/gems/aem-oauth-server-functionality-in-aem.html) 

