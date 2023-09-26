---
title: Unterstützung von Adobe Experience Manager as a Cloud Service-Inhaltsfragmenten in der Assets-HTTP-API
description: Erfahren Sie mehr über die Unterstützung für Inhaltsfragmente in der Assets-HTTP-API, einem wichtigen Teil der Adobe Experience Manager-Funktion zur Headless-Bereitstellung.
feature: Content Fragments,Assets HTTP API
exl-id: d72cc0c0-0641-4fd6-9f87-745af5f2c232
source-git-commit: 78ead5f15c2613d9c3bed3025b43423a66805c59
workflow-type: tm+mt
source-wordcount: '1793'
ht-degree: 58%

---

# Unterstützung von Inhaltsfragmenten in der AEM Assets-HTTP-API {#content-fragments-support-in-aem-assets-http-api}

## Übersicht {#overview}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/assets/extending/assets-api-content-fragments.html?lang=de) |
| AEM as a Cloud Service | Dieser Artikel |

Erfahren Sie mehr über die Unterstützung für Inhaltsfragmente in der Assets-HTTP-API, einem wichtigen Teil der Adobe Experience Manager-Funktion zur (AEM) Headless-Bereitstellung.

>[!NOTE]
>
>Die [Assets-HTTP-API](/help/assets/mac-api-assets.md) umfasst die:
>
>* Assets-REST-API
>* einschließlich Unterstützung für Inhaltsfragmente
>
>Die aktuelle Implementierung der Assets-HTTP API basiert auf dem [REST](https://de.wikipedia.org/wiki/Representational_State_Transfer)-Architekturstil.

Die [Assets REST API](/help/assets/mac-api-assets.md) ermöglicht Entwicklern von Adobe Experience Manager as a Cloud Service den direkten Zugriff auf (in AEM gespeicherte) Inhalte über die HTTP-API über CRUD-Vorgänge (Erstellen, Lesen, Aktualisieren, Löschen).

Mit der API können Sie Adobe Experience Manager as a Cloud Service als Headless-CMS (Content Management System) betreiben, indem Sie einer JavaScript-Frontend-Anwendung Content Services bereitstellen. Oder jedem anderen Programm, das HTTP-Anfragen ausführen und JSON-Antworten verarbeiten kann.

[Single Page Applications (SPA, Einzelseiten-Webanwendungen)](/help/implementing/developing/hybrid/introduction.md), ob Framework-basiert oder benutzerdefiniert, erfordern beispielsweise Inhalte, die über die HTTP-API bereitgestellt werden, häufig im JSON-Format.

while [AEM Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) stellen eine anpassbare API bereit, die erforderliche Lesevorgänge für diesen Zweck durchführen kann und deren JSON-Ausgabe angepasst werden kann. Für die Implementierung sind jedoch AEM WCM (Web Content Management)-Know-how erforderlich. Dies liegt daran, dass sie auf Seiten gehostet werden müssen, die auf dedizierten AEM basieren. Nicht jede SPA-Entwicklungsorganisation hat direkten Zugriff auf dieses Wissen.

Hier kann die Assets-REST-API eingesetzt werden. Damit können Entwickler direkt auf Assets (z. B. Bilder und Inhaltsfragmente) zugreifen, ohne sie zuerst in eine Seite einzubetten, und ihre Inhalte im serialisierten JSON-Format bereitstellen.

>[!NOTE]
>
>Es ist nicht möglich, die JSON-Ausgabe über die Assets-REST-API anzupassen.

Die Assets-REST-API ermöglicht es Entwicklern auch, Inhalte zu ändern, indem sie neue Assets, Inhaltsfragmente und Ordner erstellen, aktualisieren oder vorhandene Assets, Inhaltsfragmente und Ordner löschen.

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
* **POST** - zum Erstellen von Assets oder Ordnern
* **PUT**: Zum Aktualisieren der Eigenschaften eines Assets oder Ordners
* **DELETE**: Zum Löschen eines Assets oder Ordners

>[!NOTE]
>
>Mit dem Anfragetext und/oder den URL-Parametern können Sie einige dieser Vorgänge konfigurieren. Sie definieren damit beispielsweise, dass ein Ordner oder ein Asset über eine **POST**-Anfrage erstellt werden soll.

Das genaue Format der unterstützten Anforderungen ist in der [API-Referenzdokumentation](/help/assets/content-fragments/assets-api-content-fragments.md#api-reference) definiert.

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
   <td><p>Optimiert für den Einsatz in einer Single Page Application (SPA) oder in einem beliebigen anderen Kontext (Inhalt verbrauchend).</p> <p>Sie kann auch Layoutinformationen enthalten.</p> </td>
  </tr>
  <tr>
   <td>Unterstützte Vorgänge</td>
   <td><p>Erstellen, Lesen, Aktualisieren, Löschen.</p> <p>Bei zusätzlichen Vorgängen, je nach Entitätstyp.</p> </td>
   <td>Schreibgeschützt.</td>
  </tr>
  <tr>
   <td>Zugriff</td>
   <td><p>Sie können direkt darauf zugreifen.</p> <p>Verwendet den Endpunkt <code>/api/assets </code> und ist <code>/content/dam</code> zugeordnet (im Repository).</p> 
   <p>Ein Beispielpfad würde wie folgt aussehen: <code>/api/assets/wknd/en/adventures/cycling-tuscany.json</code></p>
   </td>
    <td><p>Sie muss über eine AEM Komponente auf einer AEM Seite referenziert werden.</p> <p>Verwendet den Selektor <code>.model</code>, um die JSON-Darstellung zu erstellen.</p> <p>Ein Beispielpfad würde wie folgt aussehen:<br/> <code>/content/wknd/language-masters/en/adventures/cycling-tuscany.model.json</code></p> 
   </td>
  </tr>
  <tr>
   <td>Sicherheit</td>
   <td><p>Mehrere Optionen sind möglich.</p> <p>OAuth wird vorgeschlagen; kann separat von der Standardeinrichtung konfiguriert werden.</p> </td>
   <td>Verwendet die oben beschriebene Standardeinrichtung von AEM.</td>
  </tr>
  <tr>
   <td>Anmerkungen zur Architektur</td>
   <td><p>Der Schreibzugriff richtet sich normalerweise an eine Autoreninstanz.</p> <p>Der Lesevorgang kann auch an eine Veröffentlichungsinstanz weitergeleitet werden.</p> </td>
   <td>Da dieser Ansatz schreibgeschützt ist, wird er normalerweise für Veröffentlichungsinstanzen verwendet.</td>
  </tr>
  <tr>
   <td>Ausgabe</td>
   <td>JSON-basierte SIREN-Ausgabe: ausführlich, aber leistungsstark. Sie ermöglicht die Navigation innerhalb des Inhalts.</td>
   <td>JSON-basierte proprietäre Ausgabe über Sling-Modelle konfigurierbar. Die Navigation durch die Inhaltsstruktur ist schwer zu implementieren (jedoch nicht unmöglich).</td>
  </tr>
 </tbody>
</table>

### Sicherheit {#security}

Wenn die Assets-REST-API in einer Umgebung ohne spezifische Authentifizierungsanforderungen verwendet wird, muss AEM CORS-Filter korrekt konfiguriert werden.

>[!NOTE]
>
>Weitere Informationen finden Sie unter:
>
>* [Erklärung: CORS/AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing.html?lang=de?lang=de)
>* [Video - Entwicklung für CORS mit AEM (04:06)](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/develop-for-cross-origin-resource-sharing.html?lang=en)
>

In Umgebungen mit bestimmten Authentifizierungsanforderungen wird OAuth empfohlen.

## Verfügbare Funktionen {#available-features}

Inhaltsfragmente sind eine bestimmte Art von Assets. Informationen finden Sie unter [Arbeiten mit Inhaltsfragmenten](/help/assets/content-fragments/content-fragments.md).

Weitere Informationen zu den über die API verfügbaren Funktionen finden Sie unter:

* Die [Assets-REST-API](/help/assets/mac-api-assets.md)
* [Entitätstypen](/help/assets/content-fragments/assets-api-content-fragments.md#entity-types), bei denen die für jeden unterstützten Typ spezifischen Funktionen (soweit für Inhaltsfragmente relevant) erläutert werden.

### Paging {#paging}

Die Assets-REST-API unterstützt Paging (für GET-Anfragen) über die URL-Parameter:

* `offset`: Die Nummer der ersten (untergeordneten) Entität, die abgerufen werden soll
* `limit`: Die maximale Anzahl von zurückgegebenen Entitäten.

Die Antwort enthält Paging-Informationen als Teil der `properties` -Abschnitt der SIREN-Ausgabe. Diese `srn:paging` -Eigenschaft enthält die Gesamtzahl der (untergeordneten) Entitäten ( `total`), den Offset und die Begrenzung ( `offset`, `limit`), wie in der Anfrage angegeben.

>[!NOTE]
>
>Paging wird normalerweise auf Container-Entitäten angewendet (d. h. Ordner oder Assets mit Ausgabedarstellungen), da es sich auf die untergeordneten Elemente der angeforderten Entität bezieht.

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

Die Assets-REST-API stellt Zugriff auf die Eigenschaften eines Ordners bereit. Beispielsweise sein Name und Titel. Assets werden als untergeordnete Entitäten von Ordnern und Unterordnern bereitgestellt.

>[!NOTE]
>
>Je nach Asset-Typ der untergeordneten Assets und Ordner enthält die Liste der untergeordneten Entitäten möglicherweise bereits den vollständigen Satz von Eigenschaften, die die entsprechende untergeordnete Entität definieren. Alternativ werden einer Entität in dieser Liste der untergeordneten Entitäten möglicherweise nicht alle Eigenschaften bereitgestellt.

### Assets {#assets}

Wenn ein Asset angefordert wird, gibt die Antwort die Metadaten (z. B. Titel, Name und andere Informationen) zurück, die vom jeweiligen Asset-Schema definiert wurden.

Die Binärdaten eines Assets werden als SIREN-Link vom Typ `content` dargestellt.

Assets können mehrere Ausgabedarstellungen aufweisen. Diese werden in der Regel als untergeordnete Entitäten bereitgestellt. Eine Ausnahme stellt die Ausgabedarstellung der Miniaturen dar, die als Link vom Typ `thumbnail` (`rel="thumbnail"`) bereitgestellt wird.

### Inhaltsfragmente {#content-fragments}

Ein [Inhaltsfragment](/help/assets/content-fragments/content-fragments.md) ist ein spezieller Asset-Typ. Sie können für den Zugriff auf strukturierte Daten wie Texte, Zahlen und Daten verwendet werden.

Da es einige Unterschiede zu *Standard*-Assets (z. B. Bildern oder Audio) aufweist, gelten einige zusätzliche Regeln für die Verarbeitung.

#### Darstellung {#representation}

Inhaltsfragmente:

* stellen keine Binärdaten bereit.
* sind in der JSON-Ausgabe enthalten (innerhalb der `properties` -Eigenschaft).

* Sie werden auch als atomisch betrachtet. Das heißt, die Elemente und Varianten werden als Teil der Eigenschaften des Fragments im Vergleich zu Links oder untergeordneten Entitäten bereitgestellt. Dies ermöglicht einen effiziente Zugriff auf die Payload eines Fragments.

#### Inhaltsmodelle und Inhaltsfragmente {#content-models-and-content-fragments}

Derzeit werden die Modelle, die die Struktur eines Inhaltsfragments definieren, nicht über eine HTTP-API bereitgestellt. Daher wird die *Verbraucher* muss über das Modell eines Fragments wissen (mindestens) - obwohl die meisten Informationen aus der Payload abgeleitet werden können; da Datentypen usw. Teil der Definition sind.

Um ein Inhaltsfragment zu erstellen, muss der Pfad (internes Repository) des Modells angegeben werden.

#### Zugehörige Inhalte {#associated-content}

Zugehörige Inhalte werden nicht bereitgestellt.

## Verwenden {#using}

Die Verwendung kann davon abhängen, ob Sie eine AEM Autoren- oder Veröffentlichungsumgebung zusammen mit Ihrem spezifischen Anwendungsfall verwenden.

* Es wird empfohlen, die Erstellung an eine Autoreninstanz ([und derzeit gibt es keine Möglichkeit, ein Fragment mit dieser API zur Veröffentlichung zu replizieren](/help/assets/content-fragments/assets-api-content-fragments.md#limitations)).
* Die Bereitstellung ist in beiden Umgebungen möglich, da AEM angeforderte Inhalte nur im JSON-Format bereitstellt.

   * Die Speicherung und Bereitstellung von einer AEM-Autoreninstanz sollte für Anwendungen hinter der Firewall und der Medienbibliothek ausreichen.

   * Für einen Live-Webversand wird eine AEM Veröffentlichungsinstanz empfohlen.

>[!CAUTION]
>
>Die Dispatcher-Konfiguration in AEM Cloud-Instanzen blockiert möglicherweise den Zugriff auf `/api`.

>[!NOTE]
>
>Weitere Informationen finden Sie in der [API-Referenz](/help/assets/content-fragments/assets-api-content-fragments.md#api-reference). Besonders interessant: [Adobe Experience Manager Assets API – Inhaltsfragmente](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/assets-api-content-fragments/index.html).

## Beschränkungen {#limitations}

Es gibt einige Beschränkungen:

* **Inhaltsfragmentmodelle werden derzeit nicht unterstützt**: sie können weder gelesen noch erstellt werden. Zum Erstellen eines neuen oder Aktualisieren eines vorhandenen Inhaltsfragments müssen Entwickler den richtigen Pfad zum Inhaltsfragmentmodell kennen. Derzeit ist dies lediglich über die Verwaltungsoberfläche möglich.
* **Verweise werden ignoriert**. Zurzeit sind keine Überprüfungen für Verweise auf vorhandene Inhaltsfragmente verfügbar. Wenn Sie beispielsweise ein Inhaltsfragment löschen, treten möglicherweise Probleme auf einer Seite auf, die einen Verweis auf das gelöschte Inhaltsfragment enthält.
* **JSON-Datentyp** Die REST-API-Ausgabe der *JSON-Datentyp* is *Zeichenfolgenbasierte Ausgabe*.

## Status-Codes und Fehlermeldungen {#status-codes-and-error-messages}

Unter den entsprechenden Voraussetzungen werden möglicherweise die folgenden Status-Codes angezeigt:

* **200** (OK)

  Wird zurückgegeben, wenn:

   * ein Inhaltsfragment mittels `GET`
   * ein Inhaltsfragment mithilfe von `PUT`

* **201** (Erstellt)

  Wird zurückgegeben, wenn:

   * ein Inhaltsfragment mithilfe von `POST`

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

   * Übergeordneter Ordner ist nicht vorhanden (beim Erstellen eines Inhaltsfragments über `POST`)
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

  Die detaillierten Fehlermeldungen werden wie folgt zurückgegeben:

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

* [Adobe Experience Manager Assets API – Inhaltsfragmente](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/assets-api-content-fragments/index.html)

* [Assets-HTTP-API](/help/assets/mac-api-assets.md)

   * [Verfügbare Funktionen](/help/assets/mac-api-assets.md#available-features)

## Zusätzliche Ressourcen {#additional-resources}

Weitere Informationen finden Sie unter:

* [Assets-HTTP-API – Dokumentation](/help/assets/mac-api-assets.md)
* [AEM Gems-Sitzung: OAuth](https://experienceleague.adobe.com/docs/events/experience-manager-gems-recordings/gems2014/aem-oauth-server-functionality-in-aem.html?lang=en)
