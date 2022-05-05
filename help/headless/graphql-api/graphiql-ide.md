---
title: Verwenden der GraphiQL-IDE in AEM
description: Erfahren Sie, wie Sie die GraphiQL IDE in Adobe Experience Manager verwenden.
feature: Content Fragments,GraphQL API
exl-id: be2ebd1b-e492-4d77-b6ef-ffdea9a9c775
source-git-commit: 5f0221fad6086f8d5c5e9bd5164d05ea8d6e7d2c
workflow-type: tm+mt
source-wordcount: '978'
ht-degree: 1%

---

# Verwenden der GraphiQL-IDE {#graphiql-ide}

Implementierung des Standards [GraphiQL](https://graphql.org/learn/serving-over-http/#graphiql) IDE ist für die Verwendung mit der GraphQL-API von Adobe Experience Manager (AEM) as a Cloud Service verfügbar.

>[!NOTE]
>
>Einige der Funktionen dieser Funktion sind im Kanal der Vorabversion verfügbar. Insbesondere Funktionen im Zusammenhang mit persistenten Abfragen.
> 
>Siehe [Dokumentation zum Vorabversionskanal](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html#enable-prerelease) für Informationen zur Aktivierung der Funktion für Ihre Umgebung.

>[!NOTE]
>
>GraphiQL ist in AEM enthalten, ist jedoch standardmäßig nur auf der `dev-authors` Umgebungen.

>[!NOTE]
>Sie müssen [-Endpunkte konfiguriert haben](/help/headless/graphql-api/graphql-endpoint.md) im [Konfigurationsbrowser](/help/assets/content-fragments/content-fragments-configuration-browser.md) vor der Verwendung der GraphiQL IDE.


Die **GraphiQL** Mit können Sie Ihre GraphQL-Abfragen testen und debuggen, indem Sie:
* wählen Sie die **Endpunkt** passend zur Sites-Konfiguration, die Sie für Ihre Abfragen verwenden möchten
* direkt neue Abfragen eingeben
* Erstellen und Zugreifen auf **[Beständige Abfragen](/help/headless/graphql-api/persisted-queries.md)**
* Führen Sie Ihre Abfragen aus, um die Ergebnisse sofort anzuzeigen
* verwalten **Abfragevariablen**
* Speichern und verwalten **Beständige Abfragen**
* Veröffentlichung oder Rückgängigmachen der Veröffentlichung, **Beständige Abfragen** (nach/von `dev-publish`)
* sehen Sie die **Geschichte** der vorherigen Abfragen
* die **Dokumentation-Explorer** Zugriff auf die Dokumentation; hilft Ihnen zu lernen und zu verstehen, welche Methoden verfügbar sind.

Sie können auf den Abfrageeditor wie folgt zugreifen:

* **Instrumente** -> **Allgemein** -> **GraphQL-Abfrage-Editor**
* direkt; Beispiel: `http://localhost:4502/aem/graphiql.html`

![GraphiQL-Schnittstelle](assets/cfm-graphiql-interface.png "GraphiQL-Schnittstelle")

Sie können GraphiQL in Ihrem Entwicklungsautorensystem verwenden, damit diese von Ihrer Clientanwendung mithilfe von GET-Anfragen und Veröffentlichungs-Abfragen angefordert werden können. Zur Verwendung in der Produktion müssen Sie dann [Ihre Abfragen in Ihre Produktionsumgebung verschieben](/help/headless/graphql-api/persisted-queries.md#transfer-persisted-query-production). Zunächst zum Produktionsautor für die Validierung neu erstellter Inhalte mit den Abfragen und schließlich zur Produktionsveröffentlichung für den Live-Verbrauch.

## Endpunkt auswählen {#selecting-endpoint}

Als ersten Schritt müssen Sie die **[Endpunkt](/help/headless/graphql-api/graphql-endpoint.md)** die Sie für die Abfragen verwenden möchten. Der Endpunkt ist der Sites-Konfiguration angemessen, die Sie für Ihre Abfragen verwenden möchten.

Diese ist in der Dropdown-Liste oben rechts verfügbar.

## Neue Abfrage erstellen und beibehalten {#creating-new-query}

Sie können Ihre neue Abfrage im Editor eingeben, der sich in der Mitte links im Bedienfeld befindet, direkt unter dem GraphiQL-Logo.

>[!NOTE]
>
>Wenn Sie bereits eine persistente Abfrage ausgewählt und im Editor angezeigt haben, wählen Sie `+` (neben **Beständige Abfragen**), um den Editor für Ihre neue Abfrage zu leeren.

Beginnen Sie mit der Eingabe des Editors auch:

* verwendet den Mauszeiger, um zusätzliche Informationen zu Elementen anzuzeigen
* bietet Funktionen wie Syntaxhervorhebung, automatische Vervollständigung, automatische Empfehlung

>[!NOTE]
>
>GraphQL-Abfragen beginnen normalerweise mit einer `{` Zeichen.
>
>Zeilen, die mit einer `#` werden ignoriert.

Verwendung **Speichern unter** , um Ihre neue Abfrage beizubehalten.

## Persistente Abfrage aktualisieren {#updating-persisted-query}

Wählen Sie die zu aktualisierende Abfrage aus der Liste im **Beständige Abfragen** Bedienfeld (ganz links).

Die Abfrage wird im Editor angezeigt. Nehmen Sie die erforderlichen Änderungen vor und verwenden Sie dann **Speichern** , um Ihre Aktualisierungen in die persistente Abfrage zu übertragen.

## Ausführen von Abfragen {#running-queries}

Sie können eine neue Abfrage sofort ausführen oder eine persistente Abfrage laden und ausführen. Um eine persistente Abfrage zu laden, wählen Sie sie aus der Liste aus. Die Abfrage wird daraufhin im Editor angezeigt.

In beiden Fällen ist die im Editor angezeigte Abfrage die Abfrage, die ausgeführt wird, wenn Sie entweder:

* Klicken/tippen Sie auf die **Ausführen der Abfrage** icon
* Verwenden der Tastaturkombination `Control-Enter`

## Abfragevariablen {#query-variables}

<!-- more details needed here? -->

Mit der GraphiQL IDE können Sie auch Ihre [Abfragevariablen](/help/headless/graphql-api/content-fragments.md#graphql-variables).

Beispiel:

![GraphQL-Variablen](assets/cfm-graphqlapi-03.png "GraphQL-Variablen")

## Veröffentlichen persistenter Abfragen (dev-publish) {#publishing-persisted-queries}

Nachdem Sie die beibehaltene Abfrage aus der Liste (linker Bereich) ausgewählt haben, können Sie die **Veröffentlichen** und **Veröffentlichung rückgängig machen** Aktionen. Dadurch werden sie in Ihrer Entwicklungs-Veröffentlichungsumgebung aktiviert (`dev-publish`) für einfachen Zugriff durch Ihre Anwendungen beim Testen.

>[!NOTE]
>
>Die Definition des Cache der gespeicherten Abfrage `Time To Live` {&quot;cache-control&quot;:&quot;parameter&quot;:value} hat einen Standardwert von 2 Stunden (7200 Sekunden).

## Zwischenspeichern persistenter Abfragen {#caching-persisted-queries}

AEM macht den CDN-Cache (Content Delivery Network) basierend auf einer standardmäßigen Time To Live (TTL) ungültig.

Dieser Wert wird auf Folgendes festgelegt:

* 7200 Sekunden ist die standardmäßige TTL für den Dispatcher und CDN. auch bekannt als *freigegebene Cache*
   * default: s-maxage=7200
* 60 ist die Standard-TTL für den Client (z. B. ein Browser)
   * default: maxage=60

AEM GraphQL-Abfragen, die mit der GraphiQL-Benutzeroberfläche persistiert wurden, verwenden bei der Ausführung die standardmäßige TTL. Wenn Sie die TTL für Ihre GraphLQ-Abfrage ändern möchten, muss die Abfrage stattdessen mit der API-Methode persistiert werden. Hierzu gehört das Posten der Abfrage an AEM mithilfe von CURL in Ihrer Befehlszeilenschnittstelle.

Beispiel:

```xml
curl -X PUT \
    -H 'authorization: Basic YWRtaW46YWRtaW4=' \
    -H "Content-Type: application/json" \
    "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-max-age" \
    -d \
'{ "query": "{articleList { items { _path author main { json } referencearticle { _path } } } }", "cache-control": { "max-age": 300 }}'
```

Die `cache-control` kann zum Zeitpunkt der Erstellung (PUT) oder später (z. B. über eine POST-Anfrage) festgelegt werden. Das Cache-Steuerelement ist beim Erstellen der persistenten Abfrage optional, da AEM den Standardwert angeben kann. Siehe [Beibehalten einer GraphQL-Abfrage](/help/headless/graphql-api/persisted-queries.md#how-to-persist-query), zum Beispiel für die Beibehaltung einer Abfrage mit curl.

## URL kopieren, um direkt auf die Abfrage zuzugreifen {#copy-url}

Die **URL kopieren** -Option können Sie eine Abfrage simulieren, indem Sie die URL kopieren, die zum direkten Zugriff auf die beibehaltene Abfrage verwendet wird, und die Ergebnisse anzeigen. Dies kann dann zum Testen verwendet werden. Beispielsweise durch Zugriff in einem Browser:

<!--
  >[!NOTE]
  >
  >The URL will need [encoding before using programmatically](/help/headless/graphql-api/persisted-queries.md#encoding-query-url).
  >
  >The target environment might need adjusting, depending on your requirements.
-->

Beispiel:

`http://localhost:4502/graphql/execute.json/global/article-list-01`

Durch die Verwendung dieser URL in einem Browser können Sie die Ergebnisse bestätigen:

![GraphiQL - URL kopieren](assets/cfm-graphiql-copy-url.png "GraphiQL - URL kopieren")

Die **URL kopieren** -Option können Sie über die drei vertikalen Punkte rechts neben dem beibehaltenen Abfragenamen (ganz links) aufrufen:

![GraphiQL - URL kopieren](assets/cfm-graphiql-persisted-query-options.png "GraphiQL - URL kopieren")

## Löschen persistenter Abfragen {#deleting-persisted-queries}

Die **Löschen** ist auch über die drei vertikalen Punkte rechts neben dem beibehaltenen Abfragenamen (ganz links) verfügbar.

<!-- what happens if you try to delete something that is still published? -->


## Installieren der beständigen Abfrage in der Produktion {#installing-persisted-query-production}

Nach dem Entwickeln und Testen Ihrer persistenten Abfrage mit GraphiQL besteht das Endziel darin, [Übertragen in die Produktionsumgebung](/help/headless/graphql-api/persisted-queries.md#transfer-persisted-query-production) zur Verwendung durch Ihre Anwendungen.

## Tastaturbefehle {#keyboard-shortcuts}

Es gibt eine Auswahl von Tastaturbefehlen, die direkten Zugriff auf Aktionssymbole in der IDE bieten:

* Abfrage konfigurieren:  `Shift-Control-P`
* Zusammenführungsabfrage:  `Shift-Control-M`
* Ausführen der Abfrage:  `Control-Enter`
* Automatisch abschließen:  `Control-Space`

>[!NOTE]
>
>Auf einigen Tastaturen `Control` Schlüssel wird als `Ctrl`.
