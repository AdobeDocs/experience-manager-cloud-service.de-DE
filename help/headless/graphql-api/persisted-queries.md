---
title: Beständige GraphQL-Abfragen
description: Erfahren Sie, wie Sie GraphQL-Abfragen in Adobe Experience Manager as a Cloud Service beibehalten, um die Leistung zu optimieren. Persistente Abfragen können von Clientanwendungen mithilfe der HTTP-GET-Methode angefordert werden. Die Antwort kann dann auf der Dispatcher- und CDN-Ebene zwischengespeichert werden, wodurch die Leistung der Clientanwendungen verbessert wird.
feature: Content Fragments,GraphQL API
exl-id: 080c0838-8504-47a9-a2a2-d12eadfea4c0
source-git-commit: dfcad7aab9dda7341de3dc4975eaba9bdfbd9780
workflow-type: tm+mt
source-wordcount: '768'
ht-degree: 41%

---

# Beständige GraphQL-Abfragen {#persisted-queries-caching}

Beständige Abfragen sind GraphQL-Abfragen, die auf dem as a Cloud Service Adobe Experience Manager-Server (AEM) erstellt und gespeichert werden. Sie können mit einer GET-Anfrage von Clientanwendungen angefordert werden. Die Antwort einer GET-Anfrage kann auf den Dispatcher- und CDN-Ebenen zwischengespeichert werden, was letztendlich die Leistung der anfragenden Client-Anwendung verbessert. Dies unterscheidet sich von standardmäßigen GraphQL-Abfragen, die mit POST-Anfragen ausgeführt werden, bei denen die Antwort nicht einfach zwischengespeichert werden kann.

Die [GraphiQL IDE](/help/headless/graphql-api/graphiql-ide.md) ist in AEM verfügbar (standardmäßig `dev-author`), damit Sie Ihre GraphQL-Abfragen entwickeln, testen und beibehalten können, bevor Sie [in die Produktionsumgebung übertragen](#transfer-persisted-query-production). Für Fälle, in denen eine Anpassung erforderlich ist (z. B. wenn [Cache anpassen](/help/headless/graphql-api/graphiql-ide.md#caching-persisted-queries)) können Sie die API verwenden; Siehe curl-Beispiel, bereitgestellt in [Beibehalten einer GraphQL-Abfrage](#how-to-persist-query).

## Beständige Abfragen und Endpunkte {#persisted-queries-and-endpoints}

Persistente Abfragen müssen immer den Endpunkt verwenden, der mit der [entsprechenden Sites-Konfiguration](graphql-endpoint.md) verknüpft ist. Sie können also entweder eine oder beide dieser Optionen verwenden:

* Globale Konfiguration und Endpunkt
Die Abfrage hat Zugriff auf alle Inhaltsfragmentmodelle.
* Spezifische Sites-Konfigurationen und -Endpunkte
Das Erstellen einer persistenten Abfrage für eine bestimmte Sites-Konfiguration erfordert einen entsprechenden Sites-konfigurationsspezifischen Endpunkt (um Zugriff auf die zugehörigen Inhaltsfragmentmodelle zu gewähren).
Um beispielsweise eine persistente Abfrage speziell für die WKND-Website-Konfiguration zu erstellen, müssen eine entsprechende WKND-spezifische Sites-Konfiguration und ein WKND-spezifischer Endpunkt im Voraus erstellt werden.

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Aktivieren der Inhaltsfragmentfunktionen im Konfigurations-Browser](/help/assets/content-fragments/content-fragments-configuration-browser.md#enable-content-fragment-functionality-in-configuration-browser).
>
>Die **GraphQL - Persistente Abfragen** für die entsprechende Sites-Konfiguration aktiviert werden.

Wenn es beispielsweise eine bestimmte Abfrage namens `my-query` gibt, die ein `my-model`-Modell aus der Sites-Konfiguration `my-conf` verwendet:

* Sie können eine Abfrage mit dem `my-conf`-spezifischen Endpunkt erstellen und die Abfrage wird dann wie folgt gespeichert:
   `/conf/my-conf/settings/graphql/persistentQueries/my-query`
* Sie können dieselbe Abfrage mit dem `global`-Endpunkt erstellen, die Abfrage wird dann jedoch wie folgt gespeichert:
   `/conf/global/settings/graphql/persistentQueries/my-query`

>[!NOTE]
>
>Hierbei handelt es sich um zwei verschiedene Abfragen, die unter verschiedenen Pfaden gespeichert werden.
>
>Sie verwenden zufällig dasselbe Modell – aber über verschiedene Endpunkte.

## Beibehalten einer GraphQL-Abfrage {#how-to-persist-query}

Es wird empfohlen, Abfragen zunächst in einer AEM Autorenumgebung zu speichern und dann [Abfrage übertragen](#transfer-persisted-query-production) in Ihre Produktions- AEM Veröffentlichungsumgebung für die Verwendung durch Anwendungen.

Es gibt verschiedene Methoden zum Speichern von Abfragen, darunter:

* GraphiQL IDE - siehe [Speichern persistenter Abfragen](/help/headless/graphql-api/graphiql-ide.md##saving-persisted-queries)
* curl - siehe folgendes Beispiel
* Andere Instrumente, einschließlich [Postman](https://www.postman.com/)

Im Folgenden finden Sie die Schritte zum Beibehalten einer bestimmten Abfrage mithilfe der **curl** Befehlszeilen-Tool:

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

1. Sie können dann die beibehaltene Abfrage anfordern, indem Sie die URL `/graphql/execute.json/<shortPath>`.

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

## Übertragen einer persistenten Abfrage in Ihre Produktionsumgebung  {#transfer-persisted-query-production}

Ihre persistente Abfrage muss sich letztendlich in Ihrer Produktionsveröffentlichungsumgebung (von AEM as a Cloud Service) befinden, in der sie von Clientanwendungen angefordert werden kann. Um eine persistente Abfrage in Ihrer Produktions-Veröffentlichungsumgebung zu verwenden, muss die zugehörige persistente Struktur repliziert werden:

* zunächst an den Produktionsautor für die Validierung neu erstellter Inhalte mit den Abfragen,
* dann zur Produktionsveröffentlichung für den Live-Verbrauch

Es gibt mehrere Ansätze zur Übertragung Ihrer persistenten Abfrage:

1. Verwenden eines Pakets:
   1. Erstellen Sie eine neue Paketdefinition.
   1. Fügen Sie die Konfiguration ein (z. B. `/conf/wknd/settings/graphql/persistentQueries`).
   1. Erstellen Sie das Paket.
   1. Übertragen Sie das Paket (herunterladen/hochladen oder replizieren).
   1. Installieren Sie das Paket.

1. Verwenden einer POST-Anfrage für die Replikation:

   ```xml
   $ curl -X POST   http://localhost:4502/bin/replicate.json \
   -H 'authorization: Basic YWRtaW46YWRtaW4=' \
   -F path=/conf/wknd/settings/graphql/persistentQueries/plain-article-query \
   -F cmd=activate
   ```

<!--
1. Using replication/distribution tool:
   1. Go to the Distribution tool.
   1. Select tree activation for the configuration (for example, `/conf/wknd/settings/graphql/persistentQueries`).

* Using a workflow (via workflow launcher configuration):
  1. Define a workflow launcher rule for executing a workflow model that would replicate the configuration on different events (for example, create, modify, amongst others).
-->

Sobald sich die Abfragekonfiguration in Ihrer Veröffentlichungsumgebung in der Produktion befindet, gelten dieselben Authentifizierungsprinzipien, nur unter Verwendung des Veröffentlichungsendpunkts.

>[!NOTE]
>
>Für den anonymen Zugriff geht das System davon aus, dass „jeder“ über die ACL Zugriff auf die Abfragekonfiguration hat.
>
>Ist dies nicht der Fall, kann sie nicht ausgeführt werden.

## Kodieren der Abfrage-URL zur Verwendung durch eine App {#encoding-query-url}

Zur Verwendung durch eine Anwendung müssen alle Semikolons (&quot;;&quot;) in den URLs kodiert werden.

Beispiel: Wie in der Anfrage zum Ausführen einer persistenten Abfrage:

```xml
curl -X GET \ "http://localhost:4502/graphql/execute.json/wknd/plain-article-query-parameters%3bapath=%2fcontent2fdam2fwknd2fen2fmagazine2falaska-adventure2falaskan-adventures;withReference=false"
```

Um eine persistente Abfrage in einer Client-App zu verwenden, sollte das AEM Headless Client SDK verwendet werden [AEM Headless-Client für JavaScript](https://github.com/adobe/aem-headless-client-js).