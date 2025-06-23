---
title: Unterstützung für Adobe Experience Manager as a Cloud Service-Inhaltsfragmente in der Assets-HTTP-API
description: Erfahren Sie mehr über die Unterstützung für Inhaltsfragmente in der Assets-HTTP-API, einem wichtigen Teil der Headless-Bereitstellungs-Funktion in Adobe Experience Manager.
feature: Content Fragments, Assets HTTP API
exl-id: d72cc0c0-0641-4fd6-9f87-745af5f2c232
role: User, Admin
source-git-commit: 1995c84bb669fd52ecd53c7e695acc518a5226e8
workflow-type: ht
source-wordcount: '1857'
ht-degree: 100%

---

# Unterstützung von Inhaltsfragmenten in der AEM Assets-HTTP-API {#content-fragments-support-in-aem-assets-http-api}

## Überblick {#overview}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/content/assets/extending/assets-api-content-fragments.html?lang=de) |
| AEM as a Cloud Service | Dieser Artikel |

>[!CAUTION]
>
>Die Unterstützung von Inhaltsfragmenten im Assets-HTTP-API ist jetzt [veraltet](/help/release-notes/deprecated-removed-features.md).
>
>Sie wurde ersetzt durch die [Bereitstellung von Inhaltsfragmenten mit OpenAPI](/help/headless/aem-content-fragment-delivery-with-openapi.md) zusammen mit [OpenAPIs für die Verwaltung von Inhaltsfragmentmodellen](/help/headless/content-fragment-openapis.md).

Erfahren Sie mehr über die Unterstützung für Inhaltsfragmente im Assets-HTTP-API, einem wichtigen Teil der Headless-Bereitstellungsfunktion in Adobe Experience Manager (AEM).

>[!NOTE]
>
>Unter [AEM-APIs für die Bereitstellung und Verwaltung strukturierter Inhalte](/help/headless/apis-headless-and-content-fragments.md) finden Sie einen Überblick über die verschiedenen verfügbaren APIs und einen Vergleich einiger der damit verbundenen Konzepte.
>
>Die [OpenAPIs für Inhaltsfragmente und Inhaltsfragmentmodelle](/help/headless/content-fragment-openapis.md) sind ebenfalls verfügbar.

>[!NOTE]
>
>Die [Assets-HTTP-API](/help/assets/mac-api-assets.md) umfasst die:
>
>* Assets-REST-API
>* einschließlich Unterstützung für Inhaltsfragmente
>
>Die aktuelle Implementierung der Assets-HTTP API basiert auf dem [REST](https://de.wikipedia.org/wiki/Representational_State_Transfer)-Architekturstil.

>[!NOTE]
>
>Aktuelle Informationen zu Experience Manager-APIs finden Sie unter [Adobe Experience Manager as a Cloud Service-APIs](https://developer.adobe.com/experience-cloud/experience-manager-apis/).

Die [Assets-REST-API](/help/assets/mac-api-assets.md) ermöglicht Entwicklungspersonen von Adobe Experience Manager as a Cloud Service den direkten Zugriff auf (in AEM gespeicherte) Inhalte über die HTTP-API mit CRUD-Vorgängen (Erstellen, Lesen, Aktualisieren, Löschen).

Die API ermöglicht es Ihnen, Adobe Experience Manager as a Cloud Service als Headless-CMS (Content-Management-System) auszuführen, indem einer JavaScript-Frontend-Anwendung Content-Services zur Verfügung gestellt werden. Oder jedem anderen Programm, das HTTP-Anfragen ausführen und JSON-Antworten verarbeiten kann.

[Single Page Applications (SPA, Einzelseiten-Webanwendungen)](/help/implementing/developing/hybrid/introduction.md), ob Framework-basiert oder benutzerdefiniert, erfordern beispielsweise Inhalte, die über die HTTP-API bereitgestellt werden, häufig im JSON-Format.

[AEM-Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) stellen eine anpassbare API bereit, die erforderliche Lesevorgänge für diesen Zweck durchführen kann und deren JSON-Ausgabe angepasst werden kann. Dazu sind jedoch Kenntnisse von AEM WCM (Web Content Management) für die Implementierung erforderlich. Der Grund dafür ist, dass sie auf Seiten gehostet werden müssen, die auf dedizierten AEM-Vorlagen basieren. Nicht jede SPA-Entwicklungsorganisation hat direkten Zugriff auf dieses Wissen.

Hier kann die Assets-REST-API eingesetzt werden. Damit können Entwickler direkt auf Assets (z. B. Bilder und Inhaltsfragmente) zugreifen, ohne sie zuerst in eine Seite einzubetten, und ihre Inhalte im serialisierten JSON-Format bereitstellen.

>[!NOTE]
>
>Es ist nicht möglich, die JSON-Ausgabe über die Assets-REST-API anzupassen.

Mit der Assets-REST-API können Entwicklerinnen und Entwickler Inhalte ändern, indem sie neue Assets, Inhaltsfragmente und Ordner erstellen, aktualisieren oder vorhandene Assets, Inhaltsfragmente und Ordner löschen.

Die Assets-REST-API:

* folgt dem [HATEOAS-Prinzip](https://de.wikipedia.org/wiki/HATEOAS)

* implementiert das [SIREN-Format](https://github.com/kevinswiber/siren)

## Voraussetzungen {#prerequisites}

Die Assets-REST-API ist in jeder standardmäßigen Installation einer aktuellen Adobe Experience Manager as a Cloud Service-Version verfügbar.

## Wichtige Konzepte {#key-concepts}

Die Assets-REST-API bietet [REST](https://de.wikipedia.org/wiki/Representational_State_Transfer)-ähnlichen Zugriff auf Assets, die in einer AEM-Instanz gespeichert sind.

Sie verwendet den `/api/assets`-Endpunkt und benötigt für den Zugriff auf das Asset dessen Pfad (ohne das Präfix `/content/dam`).

* Das bedeutet, dass Sie für den Zugriff auf das Asset unter
   * `/content/dam/path/to/asset`
* Anfrage:
   * `/api/assets/path/to/asset`

Um beispielsweise auf `/content/dam/wknd/en/adventures/cycling-tuscany`zuzugreifen, fordern Sie `/api/assets/wknd/en/adventures/cycling-tuscany.json` an.

>[!NOTE]
>Der Zugriff über:
>
>* `/api/assets` **erfordert keine** Verwendung des `.model`-Selektors.
>* `/content/path/to/page` **erfordert** die Verwendung des `.model`-Selektors.

Die HTTP-Methode ermittelt den auszuführenden Vorgang:

* **GET**: Zum Abrufen einer JSON-Darstellung eines Assets bzw. Ordners
* **POST**: Zum Erstellen von Assets oder Ordnern
* **PUT**: Zum Aktualisieren der Eigenschaften eines Assets oder Ordners
* **DELETE**: Zum Löschen eines Assets oder Ordners

>[!NOTE]
>
>Mit dem Anfragetext und/oder den URL-Parametern können Sie einige dieser Vorgänge konfigurieren. Sie definieren damit beispielsweise, dass ein Ordner oder ein Asset über eine **POST**-Anfrage erstellt werden soll.

Das genaue Format der unterstützten Anforderungen ist in der [API-Referenzdokumentation](/help/assets/content-fragments/assets-api-content-fragments.md#api-reference) definiert.

>[!NOTE]
>
>Die [OpenAPIs für Inhaltsfragmente und Inhaltsfragmentmodelle](/help/headless/content-fragment-openapis.md) sind ebenfalls verfügbar.

### Transaktionsverhalten {#transactional-behavior}

Alle Anfragen sind atomisch.

Dies bedeutet, dass die folgenden (`write`)-Anfragen nicht in einer einzelnen Transaktion kombiniert werden können, die als einzelne Entität ausgeführt werden oder fehlschlagen könnte.

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
   <td>Unterstützte Anwendungsfälle</td>
   <td>Universell.</td>
   <td><p>Optimiert für den Einsatz in einer Single Page Application (SPA) oder in einem beliebigen anderen Kontext (Inhalt verbrauchend).</p> <p>Kann auch Layout-Informationen enthalten.</p> </td>
  </tr>
  <tr>
   <td>Unterstützte Vorgänge</td>
   <td><p>Erstellen, Lesen, Aktualisieren, Löschen.</p> <p>Weitere Vorgänge je nach Entitätstyp.</p> </td>
   <td>Schreibgeschützt.</td>
  </tr>
  <tr>
   <td>Zugriff</td>
   <td><p>Sie können direkt darauf zugreifen.</p> <p>Verwendet den Endpunkt <code>/api/assets </code> und ist <code>/content/dam</code> zugeordnet (im Repository).</p> 
   <p>Ein Beispielpfad würde wie folgt aussehen: <code>/api/assets/wknd/en/adventures/cycling-tuscany.json</code></p>
   </td>
    <td><p>Muss über eine AEM-Komponente auf einer AEM-Seite referenziert werden.</p> <p>Verwendet den Selektor <code>.model</code>, um die JSON-Darstellung zu erstellen.</p> <p>Ein Beispielpfad würde wie folgt aussehen:<br/> <code>/content/wknd/language-masters/en/adventures/cycling-tuscany.model.json</code></p> 
   </td>
  </tr>
  <tr>
   <td>Sicherheit</td>
   <td><p>Mehrere Optionen sind möglich.</p> <p>OAuth wird vorgeschlagen und kann separat von der Standardeinrichtung konfiguriert werden.</p> </td>
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
>* [Erklärung von CORS/AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing.html?lang=de)
>* [Video: Entwickeln für CORS mit AEM (04:06)](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/develop-for-cross-origin-resource-sharing.html?lang=de)
>

In Umgebungen mit bestimmten Authentifizierungsanforderungen wird OAuth empfohlen.

## Verfügbare Funktionen {#available-features}

Inhaltsfragmente sind eine bestimmte Art von Assets. Informationen finden Sie unter [Arbeiten mit Inhaltsfragmenten](/help/assets/content-fragments/content-fragments.md).

Weitere Informationen zu den über die APIs verfügbaren Funktionen:

* Die [Assets-REST-API](/help/assets/mac-api-assets.md)
* [Entitätstypen](/help/assets/content-fragments/assets-api-content-fragments.md#entity-types), bei denen die für jeden unterstützten Typ spezifischen Funktionen (soweit für Inhaltsfragmente relevant) erläutert werden.

>[!NOTE]
>
>Die [OpenAPIs für Inhaltsfragmente und Inhaltsfragmentmodelle](/help/headless/content-fragment-openapis.md) sind ebenfalls verfügbar.

### Paging {#paging}

Die Assets-REST-API unterstützt Paging (für GET-Anforderungen) über die URL-Parameter:

* `offset`: Die Nummer der ersten (untergeordneten) Entität, die abgerufen werden soll
* `limit`: Die maximale Anzahl von zurückgegebenen Entitäten.

Die Antwort enthält Paging-Informationen im Bereich `properties` der SIREN-Ausgabe. Diese Eigenschaft `srn:paging` enthält die Gesamtzahl der (untergeordneten) Entitäten (`total`), den Offset und das Limit (`offset`, `limit`), wie in der Anfrage angegeben.

>[!NOTE]
>
>Paging wird normalerweise auf Container-Entitäten (also Ordner oder Assets mit Ausgabedarstellungen) angewendet, da es die untergeordneten Objekte des angeforderten Elements betrifft.

#### Beispiel: Paging {#example-paging}

`GET /api/assets.json?offset=2&limit=3`

```json
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

Ordner dienen als Container für Assets und andere Ordner. Ihre Struktur entspricht den Inhalts-Repositorys von AEM.

Die Assets-REST-API gewährt Zugriff auf die Eigenschaften eines Ordners. Beispielsweise sein Name und Titel. Assets werden als untergeordnete Entitäten von Ordnern und Unterordnern bereitgestellt.

>[!NOTE]
>
>Je nach Asset-Typ der untergeordneten Assets und Ordner enthält die Liste der untergeordneten Entitäten möglicherweise bereits die gesamten Eigenschaften, die die untergeordnete Entität definieren. Alternativ werden einer Entität in dieser Liste der untergeordneten Entitäten möglicherweise nicht alle Eigenschaften bereitgestellt.

### Assets {#assets}

Wenn ein Asset angefordert wird, gibt die Antwort die Metadaten (z. B. Titel, Name und andere Informationen) wie vom entsprechenden Asset-Schema definiert zurück.

Die Binärdaten eines Assets werden als SIREN-Link vom Typ `content` dargestellt.

Assets können mehrere Ausgabedarstellungen aufweisen. Diese werden in der Regel als untergeordnete Entitäten bereitgestellt. Eine Ausnahme stellt die Ausgabedarstellung der Miniaturen dar, die als Link vom Typ `thumbnail` (`rel="thumbnail"`) bereitgestellt wird.

### Inhaltsfragmente {#content-fragments}

Ein [Inhaltsfragment](/help/assets/content-fragments/content-fragments.md) ist ein spezieller Asset-Typ. Es kann für den Zugriff auf strukturierte Daten wie Texte, Zahlen und Daten verwendet werden.

Da es einige Unterschiede zu *Standard*-Assets (z. B. Bildern oder Audio) aufweist, gelten einige zusätzliche Regeln für die Verarbeitung.

#### Darstellung {#representation}

Inhaltsfragmente:

* stellen keine Binärdaten bereit.
* sind in der JSON-Ausgabe enthalten (innerhalb der Eigenschaft `properties`).

* sie gelten auch als atomisch. Das bedeutet, dass die Elemente und Varianten als Teil der Eigenschaften des Fragments anstatt als Links oder untergeordnete Entitäten bereitgestellt werden. Dies ermöglicht einen effiziente Zugriff auf die Payload eines Fragments.

#### Inhaltsmodelle und Inhaltsfragmente {#content-models-and-content-fragments}

Derzeit werden die Modelle, die die Struktur eines Inhaltsfragments definieren, nicht über eine HTTP-API bereitgestellt. Daher benötigen *Verbraucher* (zumindest einige) Informationen über das Modell eines Fragments. Die meisten Informationen können jedoch aus der Nutzlast abgeleitet werden, da Datentypen usw. Teil der Definition sind.

Zum Erstellen eines Inhaltsfragments muss der Pfad (des internen Repositorys) für das Modell angegeben werden.

#### Zugehörige Inhalte {#associated-content}

Zugehörige Inhalte werden nicht bereitgestellt.

## Verwenden {#using}

Die Verwendung unterscheidet sich je nachdem, ob Sie eine AEM-Autoren- oder Veröffentlichungsumgebung zusammen mit Ihrem spezifischen Verwendungsszenario verwenden.

* Es wird empfohlen, dass die Erstellung in einer Autoreninstanz erfolgt ([und derzeit gibt es keine Möglichkeit, ein Fragment mit dieser API für die Veröffentlichungsinstanz zu replizieren](/help/assets/content-fragments/assets-api-content-fragments.md#limitations)).
* Die Bereitstellung ist in beiden Umgebungen möglich, da AEM angeforderte Inhalte nur im JSON-Format bereitstellt.

   * Das Speichern und Bereitstellen über eine AEM-Autoreninstanz sollte für Medienbibliotheksanwendungen hinter einer Firewall ausreichen.

   * Für die Live-Web-Bereitstellung wird eine AEM-Veröffentlichungsinstanz empfohlen.

>[!CAUTION]
>
>Die Dispatcher-Konfiguration auf AEM Cloud-Instanzen blockiert möglicherweise den Zugriff auf `/api`.

>[!NOTE]
>
>Siehe die [API-Referenz](/help/assets/content-fragments/assets-api-content-fragments.md#api-reference). Besonders interessant: [Adobe Experience Manager Assets API – Inhaltsfragmente](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/assets-api-content-fragments/index.html?lang=de).
>
>Die [OpenAPIs für Inhaltsfragmente und Inhaltsfragmentmodelle](/help/headless/content-fragment-openapis.md) sind ebenfalls verfügbar.

## Einschränkungen {#limitations}

Es gibt einige Beschränkungen:

* **Inhaltsfragmentmodelle werden derzeit nicht unterstützt**: sie können weder gelesen noch erstellt werden. Um ein Inhaltsfragment zu erstellen oder ein bestehendes zu aktualisieren, müssen Entwickelnde den richtigen Pfad zum Inhaltsfragmentmodell kennen. Derzeit ist dies lediglich über die Verwaltungsoberfläche möglich.
* **Verweise werden ignoriert**. Zurzeit sind keine Überprüfungen für Verweise auf vorhandene Inhaltsfragmente verfügbar. Wenn Sie beispielsweise ein Inhaltsfragment löschen, treten möglicherweise Probleme auf einer Seite auf, die einen Verweis auf das gelöschte Inhaltsfragment enthält.
* **JSON-Datentyp** Die REST-API-Ausgabe des *JSON-Datentyps* basiert auf *Zeichenfolgen*.

## Status-Codes und Fehlermeldungen {#status-codes-and-error-messages}

Unter den entsprechenden Voraussetzungen werden möglicherweise die folgenden Status-Codes angezeigt:

* **200** (OK)

  Wird zurückgegeben, wenn:

   * ein Inhaltsfragment per `GET` angefordert wurde
   * ein Inhaltsfragment mithilfe von `PUT` aktualisiert wurde

* **201** (Erstellt)

  Wird zurückgegeben, wenn:

   * ein Inhaltsfragment mithilfe von `POST` erstellt wurde

* **404** (Nicht gefunden)

  Wird zurückgegeben, wenn:

   * das angeforderte Inhaltsfragment nicht vorhanden ist

* **500** (Interner Server-Fehler)

  >[!NOTE]
  >
  >Dieser Fehler wird zurückgegeben:
  >
  >* wenn ein Fehler, der mit keinem bestimmten Code identifiziert werden kann, aufgetreten ist
  >* wenn als Payload „null“ angegeben ist

  Nachfolgend finden Sie allgemeine Szenarien, in denen dieser Fehlerstatus in Kombination mit der Fehlermeldung (monospace) zurückgegeben wird:

   * Übergeordneter Ordner ist nicht vorhanden (wenn ein Inhaltsfragment per `POST` erstellt wurde)
   * Es wird kein Inhaltsfragmentmodell bereitgestellt (cq:model fehlt), es kann nicht gelesen werden (aufgrund eines ungültigen Pfads oder eines Berechtigungsproblems) oder es gibt kein gültiges Fragmentmodell:

      * `No content fragment model specified`
      * `Cannot create a resource of given model '/foo/bar/qux'`

   * Das Inhaltsfragment konnte nicht erstellt werden (möglicherweise ein Berechtigungsproblem):

      * `Could not create content fragment`

   * Titel oder Beschreibung konnte nicht aktualisiert werden:

      * `Could not set value on content fragment`

   * Metadaten konnten nicht festgelegt werden:

      * `Could not set metadata on content fragment`

   * Inhaltselement wurde nicht gefunden oder konnte nicht aktualisiert werden

      * `Could not update content element`
      * `Could not update fragment data of element`

  Die detaillierten Fehlermeldungen werden auf folgende Art zurückgegeben:

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

* [Adobe Experience Manager Assets API – Inhaltsfragmente](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/assets-api-content-fragments/index.html?lang=de)

* [Assets-HTTP-API](/help/assets/mac-api-assets.md)

   * [Verfügbare Funktionen](/help/assets/mac-api-assets.md#available-features)

* Die [OpenAPIs für Inhaltsfragmente und Inhaltsfragmentmodelle](/help/headless/content-fragment-openapis.md) sind ebenfalls verfügbar.

## Zusätzliche Ressourcen {#additional-resources}

Weitere Informationen finden Sie unter:

* [Assets-HTTP-API – Dokumentation](/help/assets/mac-api-assets.md)
* [AEM Gems-Sitzung: OAuth](https://experienceleague.adobe.com/docs/events/experience-manager-gems-recordings/gems2014/aem-oauth-server-functionality-in-aem.html?lang=de)
