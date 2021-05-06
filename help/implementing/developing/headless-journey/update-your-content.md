---
title: Aktualisierung Ihrer Inhalte über AEM Assets APIs
description: In diesem Teil der AEM Developer-Journey lernen Sie, wie Sie mit der REST-API auf den Inhalt Ihrer Inhaltsfragmente zugreifen und ihn aktualisieren können.
hide: true
hidefromtoc: true
index: false
exl-id: 8d133b78-ca36-4c3b-815d-392d41841b5c
translation-type: tm+mt
source-git-commit: 0c47dec1e96fc3137d17fc3033f05bf1ae278141
workflow-type: tm+mt
source-wordcount: '1657'
ht-degree: 72%

---

# Aktualisierung Ihrer Inhalte über AEM Assets APIs {#update-your-content}

>[!CAUTION]
>
>ARBEITEN IN FORTSCHRITTEN - Die Schaffung dieses Dokuments ist im Gange und sollte nicht als vollständig oder endgültig betrachtet werden und auch nicht für Produktionszwecke verwendet werden.

In diesem Teil der [AEM Headless Developer-Journey lernen Sie, wie Sie mit der REST-API auf den Inhalt Ihrer Inhaltsfragmente zugreifen und ihn aktualisieren können.](overview.md)

## Die Meldung bisher {#story-so-far}

Im vorherigen Dokument der AEM-Journey [Wie Sie über AEM Versand-APIs ](access-your-content.md) auf Ihre Inhalte zugreifen können, haben Sie gelernt, wie Sie über die AEM GraphQL-API auf Ihre kostenlosen Inhalte in AEM zugreifen können. Jetzt sollten Sie:

* Sie haben ein fundiertes Verständnis von GraphQL.
* Verstehen Sie, wie die AEM GraphQL API funktioniert.
* Machen Sie sich mit einigen praktischen Abfragen vertraut.

Dieser Artikel baut auf diesen Grundlagen auf, damit Sie verstehen, wie Sie Ihre vorhandenen Kopflosen Inhalte in AEM über die REST-API aktualisieren können.

## Vorgabe {#objective}

* **Audience**: Erweitert
* **Zielsetzung**: Erfahren Sie, wie Sie mit der REST API auf den Inhalt Ihrer Inhaltsfragmente zugreifen und diese aktualisieren können:
   * Einführung der AEM Assets HTTP API.
   * Einführung und Diskussion der Unterstützung von Inhaltsfragmenten in der API.
   * Erläuterung der API.

<!--
  * Look at sample code to see how things work in practice.
-->

## Warum benötigen Sie die Asset HTTP-API für Inhaltsfragment {#why-http-api}

In der vorherigen Phase der Journey ohne Kopfdaten haben Sie gelernt, wie Sie mit der AEM GraphQL API Ihre Inhalte mithilfe von Abfragen abrufen können.

Warum wird also eine weitere API benötigt?

Die Asset-HTTP-API ermöglicht Ihnen zwar, **Lesen** Ihren Inhalt zu lesen, ermöglicht Ihnen aber auch, **Inhalte erstellen**, **Aktualisieren** und **Löschen** zu löschen - Aktionen, die mit der Grafik-QL-API nicht möglich sind.

## Assets-HTTP-API {#assets-http-api}

Die [Assets-HTTP-API](/help/assets/mac-api-assets.md) umfasst:

* Assets-REST-API
* einschließlich Unterstützung für Inhaltsfragmente

Die aktuelle Implementierung der Assets-HTTP API basiert auf dem **REST**-Architekturstil.

Die Assets REST API ermöglicht Entwicklern von Adobe Experience Manager als Cloud Service den direkten Zugriff auf (in AEM gespeicherte) Inhalte über die HTTP-API über **CRUD**-Vorgänge (Erstellen, Lesen, Aktualisieren, Löschen).

Die API ermöglicht es Ihnen, Adobe Experience Manager as a Cloud Service als Headless-CMS (Content-Management-System) auszuführen, indem Sie einem JavaScript-Frontend-Programm Inhalts-Services bereitstellen. Oder jedem anderen Programm, das HTTP-Anfragen ausführen und JSON-Antworten verarbeiten kann.

Beispielsweise erfordern Einzelseitenanwendungen (SPA), Framework- oder benutzerdefinierte, Inhalte, die über eine API bereitgestellt werden, häufig im JSON-Format.

AEM-Kernkomponenten stellen eine sehr umfassende, flexible und anpassbare API bereit, die erforderliche Lesevorgänge für diesen Zweck durchführen kann und deren JSON-Ausgabe angepasst werden kann. Dazu sind jedoch Kenntnisse von AEM WCM (Web Content Management) für die Implementierung erforderlich, da sie in (API-)Seiten gehostet werden müssen, die auf dedizierten AEM-Vorlagen basieren. Nicht jede SPA-Entwicklungsorganisation hat direkten Zugriff auf dieses Wissen.

Hier kann die Assets-REST-API eingesetzt werden. Damit können Entwickler direkt auf Assets (z. B. Bilder und Inhaltsfragmente) zugreifen, ohne sie zuerst in eine Seite einzubetten, und ihre Inhalte im serialisierten JSON-Format bereitstellen.

>[!NOTE]
>
>Es ist nicht möglich, die JSON-Ausgabe über die Assets-REST-API anzupassen.

Mit der Assets-REST-API können Entwickler Inhalte ändern, indem sie neue Assets, Inhaltsfragmente und Ordner erstellen, aktualisieren oder vorhandene Assets, Inhaltsfragmente und Ordner löschen.

Die Assets-REST-API:

* folgt dem HATEOAS-Prinzip
* implementiert das SIREN-Format

## Voraussetzungen {#prerequisites}

Die Assets-REST-API ist in jeder standardmäßigen Installation einer aktuellen Adobe Experience Manager as a Cloud Service-Version verfügbar.

## Schlüsselkonzepte {#key-concepts}

Der REST-API-Angebot im REST-Stil ermöglicht den Zugriff auf Assets, die in einer AEM-Instanz gespeichert sind.

Sie verwendet den `/api/assets`-Endpunkt und benötigt für den Zugriff auf das Asset dessen Pfad (ohne das Präfix `/content/dam`).

* Das bedeutet, dass Sie für den Zugriff auf das Asset unter
   * `/content/dam/path/to/asset`
* Folgendes anfordern müssen:
   * `/api/assets/path/to/asset`

Um beispielsweise auf `/content/dam/wknd/en/adventures/cycling-tuscany`zuzugreifen, fordern Sie `/api/assets/wknd/en/adventures/cycling-tuscany.json` an.

>[!NOTE]
>Der Zugriff über:
>
>* `/api/assets` **erfordert keine** Verwendung des `.model`-Selektors.
>* `/content/path/to/page` **erfordert keine** Verwendung des `.model`-Selektors.


Die HTTP-Methode ermittelt den auszuführenden Vorgang:

* **GET**: Zum Abrufen einer JSON-Darstellung eines Assets bzw. Ordners
* **POST**: Zum Erstellen neuer Assets oder Ordner
* **PUT**: Zum Aktualisieren der Eigenschaften eines Assets oder Ordners
* **DELETE**: Zum Löschen eines Assets oder Ordners

>[!NOTE]
>
>Mit dem Anfragetext und/oder den URL-Parametern können Sie einige dieser Vorgänge konfigurieren. Sie definieren damit beispielsweise, dass ein Ordner oder ein Asset über eine **POST**-Anfrage erstellt werden soll.

Das genaue Format der unterstützten Anforderungen ist in der API-Referenzdokumentation definiert.

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
   <td>Geeignete Nutzungsszenarien</td>
   <td>Universell.</td>
   <td><p>Optimiert für den Einsatz in einer Single Page Application (SPA) oder in einem beliebigen anderen Kontext (Inhalt verbrauchend).</p> <p>Kann auch Layoutinformationen enthalten.</p> </td>
  </tr>
  <tr>
   <td>Unterstützte Vorgänge</td>
   <td><p>Erstellen, Lesen, Aktualisieren, Löschen.</p> <p>Weitere Vorgänge abhängig von Entitätstyp.</p> </td>
   <td>Schreibgeschützt.</td>
  </tr>
  <tr>
   <td>Zugriff</td>
   <td><p>Direkter Zugriff möglich.</p> <p>Verwendet den Endpunkt <code>/api/assets </code> und ist <code>/content/dam</code> zugeordnet (im Repository).</p> 
   <p>Ein Beispielpfad würde wie folgt aussehen: <code>/api/assets/wknd/en/adventures/cycling-tuscany.json</code></p>
   </td>
    <td><p>Muss über eine AEM-Komponente auf einer AEM-Seite referenziert werden.</p> <p>Verwendet den Selektor <code>.model</code>, um die JSON-Darstellung zu erstellen.</p> <p>Ein Beispielpfad würde wie folgt aussehen:<br/> <code>/content/wknd/language-masters/en/adventures/cycling-tuscany.model.json</code></p> 
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
>* Erklärung: CORS/AEM
>* Video: Entwicklung für CORS mit AEM

>



In Umgebungen mit bestimmten Authentifizierungsanforderungen wird OAuth empfohlen.

## Verfügbare Funktionen {#available-features}

Inhaltsfragmente sind eine bestimmte Art von Assets. Informationen finden Sie unter Arbeiten mit Inhaltsfragmenten.

Weitere Informationen zu den über die APIs verfügbaren Funktionen:

* Die Assets-REST-API
* Entitätstypen, bei denen die für jeden unterstützten Typ spezifischen Funktionen (soweit für Inhaltsfragmente relevant) erläutert werden.

### Paging {#paging}

Die Assets-REST-API unterstützt Paging (für GET-Anfragen) über die URL-Parameter:

* `offset`: Die Nummer der ersten (untergeordneten) Entität, die abgerufen werden soll
* `limit`: Die maximale Anzahl von zurückgegebenen Entitäten.

Die Antwort enthält Paging-Informationen im Bereich `properties` der SIREN-Ausgabe. Diese Eigenschaft `srn:paging` enthält die Gesamtzahl der (untergeordneten) Entitäten (`total`), den Offset und das Limit ( `offset`, `limit`), wie in der Anfrage angegeben.

>[!NOTE]
>
>Paging wird normalerweise auf Container-Entitäten (d. h. Ordner oder Assets mit Ausgabedarstellungen) angewendet, da sie auf die untergeordneten Objekte des angeforderten Elements verweisen.

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

Ordner dienen als Container für Assets und andere Ordner. Ihre Struktur entspricht den Inhaltsrepositorys von AEM.

Die Assets-REST-API gewährt Zugriff auf die Eigenschaften eines Ordners, z. B. Name, Titel, usw. Assets werden als untergeordnete Entitäten von Ordnern und Unterordnern bereitgestellt.

>[!NOTE]
>
>Je nach Asset-Typ der untergeordneten Assets und Ordner enthält die Liste der untergeordneten Entitäten möglicherweise bereits die gesamten Eigenschaften, die die untergeordnete Entität definieren. Alternativ werden einer Entität in dieser Liste der untergeordneten Entitäten möglicherweise nicht alle Eigenschaften bereitgestellt.

### Assets {#assets}

Wenn ein Asset angefordert wird, gibt die Antwort die Metadaten (z. B. Titel, Name und andere Informationen) wie vom entsprechenden Asset-Schema definiert zurück.

Die Binärdaten eines Assets werden als SIREN-Link vom Typ `content` dargestellt.

Assets können mehrere Ausgabedarstellungen aufweisen. Diese werden in der Regel als untergeordnete Entitäten bereitgestellt. Eine Ausnahme stellt die Ausgabedarstellung der Miniaturansichten dar, die als Link vom Typ `thumbnail` (`rel="thumbnail"`) bereitgestellt wird.

### Inhaltsfragmente {#content-fragments}

Ein Inhaltsfragment ist ein besonderer Asset-Typ. Es kann für den Zugriff auf strukturierte Daten wie Texte, Zahlen und Daten verwendet werden.

Da es einige Unterschiede zu *Standard*-Assets (z. B. Bildern oder Audio) aufweist, gelten einige zusätzliche Regeln für die Verarbeitung.

#### Darstellung  {#representation}

Inhaltsfragmente:

* stellen keine Binärdaten bereit.
* sind vollständig in der JSON-Ausgabe enthalten (innerhalb der Eigenschaft `properties`).

* Gelten auch als atomisch, d. h. die Elemente und Varianten werden als Teil der Eigenschaften des Fragments anstatt als Links oder untergeordnete Entitäten bereitgestellt. Dies ermöglicht einen effiziente Zugriff auf die Payload eines Fragments.

#### Inhaltsmodelle und Inhaltsfragmente   {#content-models-and-content-fragments}

Derzeit werden die Modelle, die die Struktur eines Inhaltsfragments definieren, nicht über eine HTTP-API bereitgestellt. Daher benötigt der *Benutzer* (zumindest einige) Informationen über das Modell eines Fragments. Die meisten Informationen kann er jedoch aus der Payload ableiten. So sind z. B. Datentypen Teil der Definition.

Zum Erstellen eines neuen Inhaltsfragments muss der Pfad (des internen Repositorys) für das Modell angegeben werden.

#### Zugehörige Inhalte {#associated-content}

Zugehöriger Inhalt wird derzeit nicht bereitgestellt.

## Verwenden der Asset REST API {#using-aem-assets-rest-api}

Einzelheiten zur Verwendung der AEM Assets REST API finden Sie unter:

* Adobe Experience Manager Assets HTTP API
* Unterstützung von Inhaltsfragmenten in der AEM Assets-HTTP-API 

## Wie geht es weiter {#whats-next}

Nachdem Sie nun die AEM Journey zum kostenlosen Entwickler abgeschlossen haben, sollten Sie:

* Machen Sie sich mit der AEM Assets HTTP API vertraut.
* Verstehen Sie, wie Inhaltsfragmente in dieser API unterstützt werden.

<!--
* Have experience with sample code and know how the API works in practice.
-->

Sie sollten Ihre AEM kopflosen Journey fortsetzen, indem Sie sich das Dokument [Wie Sie alles zusammenstellen - Ihre App und Ihr Inhalt in AEM Headless](put-it-all-together.md) ansehen, in dem Sie lernen, wie Sie Ihr AEM Headless-Projekt umsetzen und es für das Live-Leben vorbereiten können.

## Zusätzliche Ressourcen {#additional-resources}

* [REST](https://de.wikipedia.org/wiki/Representational_State_Transfer)
* [HATEOAS-Grundsatz](https://de.wikipedia.org/wiki/HATEOAS)
* [SIREN-Format](https://github.com/kevinswiber/siren)
* [Assets-HTTP-API](/help/assets/mac-api-assets.md)
* [Inhaltsfragment-REST-API](/help/assets/content-fragments/assets-api-content-fragments.md)
   * [API-Referenz ](/help/assets/content-fragments/assets-api-content-fragments.md#api-reference)
* [Arbeiten mit Inhaltsfragmenten](/help/assets/content-fragments/content-fragments.md)
* [AEM-Kernkomponenten](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/introduction.html)
* [Erklärung: CORS/AEM](https://helpx.adobe.com/de/experience-manager/kt/platform-repository/using/cors-security-article-understand.html)
* [Video: Entwicklung für CORS mit AEM](https://helpx.adobe.com/de/experience-manager/kt/platform-repository/using/cors-security-technical-video-develop.html)

