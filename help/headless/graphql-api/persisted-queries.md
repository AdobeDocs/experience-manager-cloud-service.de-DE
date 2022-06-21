---
title: Persistente GraphQL-Abfragen
description: Erfahren Sie, wie Sie GraphQL-Abfragen in Adobe Experience Manager as a Cloud Service beibehalten, um die Leistung zu optimieren. Persistente Abfragen können von Client-Programmen mithilfe der HTTP-GET-Methode angefragt werden. Die Antwort kann dann auf der Dispatcher- und CDN-Ebene zwischengespeichert werden, wodurch die Leistung der Client-Programme verbessert wird.
feature: Content Fragments,GraphQL API
exl-id: 080c0838-8504-47a9-a2a2-d12eadfea4c0
source-git-commit: 6529b4b874cd7d284b92546996e2373e59075dfd
workflow-type: tm+mt
source-wordcount: '1109'
ht-degree: 30%

---

# Persistente GraphQL-Abfragen {#persisted-queries-caching}

Beständige Abfragen sind GraphQL-Abfragen, die auf dem as a Cloud Service Adobe Experience Manager-Server (AEM) erstellt und gespeichert werden. Sie können mit einer GET-Anfrage von Clientanwendungen angefordert werden. Die Antwort einer GET-Anfrage kann auf den Dispatcher- und CDN-Ebenen zwischengespeichert werden, was letztendlich die Leistung des anfragenden Client-Programms verbessert. Dies unterscheidet sich von standardmäßigen GraphQL-Abfragen, die mit POST-Anfragen ausgeführt werden, bei denen die Antwort nicht einfach zwischengespeichert werden kann.

>[!NOTE]
>
>Beständige Abfragen werden empfohlen. Siehe [Best Practices für GraphQL-Abfrage (Dispatcher)](/help/headless/graphql-api/content-fragments.md#graphql-query-best-practices) für Details und die zugehörige Dispatcher-Konfiguration.

Die [GraphiQL IDE](/help/headless/graphql-api/graphiql-ide.md) steht in AEM zur Verfügung, damit Sie Ihre GraphQL-Abfragen entwickeln, testen und beibehalten können, bevor [in die Produktionsumgebung übertragen](#transfer-persisted-query-production). Für Fälle, in denen eine Anpassung erforderlich ist (z. B. wenn [Cache anpassen](/help/headless/graphql-api/graphiql-ide.md#caching-persisted-queries)) können Sie die API verwenden; Siehe curl-Beispiel, bereitgestellt in [Beibehalten einer GraphQL-Abfrage](#how-to-persist-query).

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

* GraphiQL IDE - siehe [Speichern persistenter Abfragen](/help/headless/graphql-api/graphiql-ide.md##saving-persisted-queries) (bevorzugte Methode)
* curl - siehe folgendes Beispiel
* Andere Instrumente, einschließlich [Postman](https://www.postman.com/)

Die GraphiQL-IDE ist die **preferred** -Methode zur Beibehaltung von Abfragen. So behalten Sie eine bestimmte Abfrage bei: **curl** Befehlszeilen-Tool:

1. Bereiten Sie die Abfrage mittels einer PUT-Anfrage an die neue Endpunkt-URL `/graphql/persist.json/<config>/<persisted-label>` vor.

   Erstellen Sie beispielsweise eine persistente Abfrage:

   ```shell
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

   ```json
   {
     "action": "create",
     "configurationName": "wknd",
     "name": "plain-article-query",
     "shortPath": "/wknd/plain-article-query",
     "path": "/conf/wknd/settings/graphql/persistentQueries/plain-article-query"
   }
   ```

1. Sie können die persistente Abfrage dann ausführen, indem Sie die URL `/graphql/execute.json/<shortPath>` per GET-Anfrage abrufen.

   Verwenden Sie zum Beispiel die persistente Abfrage:

   ```shell
   $ curl -X GET \
       http://localhost:4502/graphql/execute.json/wknd/plain-article-query
   ```

1. Aktualisieren Sie eine persistente Abfrage mittels POST-Anfrage an einen bereits vorhandenen Abfragepfad.

   Verwenden Sie zum Beispiel die persistente Abfrage:

   ```shell
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

   ```shell
   $ curl -X PUT \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-wrapped" \
       -d \
   '{ "query": "{articleList { items { _path author main { json } referencearticle { _path } } } }"}'
   ```

1. Erstellen Sie eine umschlossene Abfrage mit Cache-Steuerung.

   Beispiel:

   ```shell
   $ curl -X PUT \
       -H 'authorization: Basic YWRtaW46YWRtaW4=' \
       -H "Content-Type: application/json" \
       "http://localhost:4502/graphql/persist.json/wknd/plain-article-query-max-age" \
       -d \
   '{ "query": "{articleList { items { _path author main { json } referencearticle { _path } } } }", "cache-control": { "max-age": 300 }}'
   ```

1. Erstellen Sie eine persistente Abfrage mit Parametern:

   Beispiel:

   ```shell
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


## Ausführen einer beständigen Abfrage {#execute-persisted-query}

Um eine persistente Abfrage auszuführen, sendet eine Client-Anwendung eine GET-Anfrage mit der folgenden Syntax:

```
GET <AEM_HOST>/graphql/execute.json/<PERSISTENT_PATH>
```

Wo `PERSISTENT_PATH` ist ein verkürzter Pfad zum Speicherort der persistenten Abfrage.

1. Beispiel `wknd` ist der Konfigurationsname und `plain-article-query` ist der Name der persistenten Abfrage. So führen Sie die Abfrage aus:

   ```shell
   $ curl -X GET \
       https://publish-p123-e456.adobeaemcloud.com/graphql/execute.json/wknd/plain-article-query
   ```

1. Ausführen einer Abfrage mit Parametern.

   >[!NOTE]
   >
   > Abfragevariablen und -werte müssen ordnungsgemäß sein [kodiert](#encoding-query-url) beim Ausführen einer beständigen Abfrage.

   Beispiel:

   ```xml
   $ curl -X GET \
       "https://publish-p123-e456.adobeaemcloud.com/graphql/execute.json/wknd/plain-article-query-parameters%3Bapath%3D%2Fcontent%2Fdam%2Fwknd%2Fen%2Fmagazine%2Falaska-adventure%2Falaskan-adventures%3BwithReference%3Dfalse
   ```

   Siehe Verwenden [Abfragevariablen](#query-variables) für weitere Details.

## Verwenden von Abfragevariablen {#query-variables}

Abfragevariablen können mit persistenten Abfragen verwendet werden. Die Abfragevariablen werden an die Anfrage mit einem Semikolon (`;`) unter Verwendung des Variablennamens und -werts. Mehrere Variablen werden durch Semikolons getrennt.

Das Muster sieht wie folgt aus:

```
<AEM_HOST>/graphql/execute.json/<PERSISTENT_QUERY_PATH>;variable1=value1;variable2=value2
```

Die folgende Abfrage enthält beispielsweise eine Variable `activity` , um eine Liste nach einem Aktivitätswert zu filtern:

```graphql
query getAdventuresByActivity($activity: String!) {
      adventureList (filter: {
        adventureActivity: {
          _expressions: [
            {
              value: $activity
            }
          ]
        }
      }){
        items {
          _path
        adventureTitle
        adventurePrice
        adventureTripLength
      }
    }
  }
```

Diese Abfrage kann unter einem Pfad beibehalten werden `wknd/adventures-by-activity`. So rufen Sie die persistente Abfrage auf: `activity=Camping` Die Anfrage würde wie folgt aussehen:

```
<AEM_HOST>/graphql/execute.json/wknd/adventures-by-activity%3Bactivity%3DCamping
```

Beachten Sie Folgendes: `%3B` ist die UTF-8-Kodierung für `;` und `%3D` ist die Kodierung für `=`. Die Abfragevariablen und alle Sonderzeichen müssen [ordnungsgemäß kodiert](#encoding-query-url) für die Ausführung der persistenten Abfrage.

## Kodieren der Abfrage-URL zur Verwendung durch eine App {#encoding-query-url}

Für die Verwendung durch eine Anwendung werden alle Sonderzeichen verwendet, die beim Erstellen von Abfragevariablen verwendet werden (d. h. Semikolons (`;`), Gleichheitszeichen (`=`), Schrägstriche `/`) muss konvertiert werden, um die entsprechende UTF-8-Kodierung zu verwenden.

Beispiel:

```xml
curl -X GET \ "https://publish-p123-e456.adobeaemcloud.com/graphql/execute.json/wknd/adventure-by-path%3BadventurePath%3D%2Fcontent%2Fdam%2Fwknd%2Fen%2Fadventures%2Fbali-surf-camp%2Fbali-surf-camp"
```

Die URL kann in die folgenden Teile unterteilt werden:

| URL-Teil | Beschreibung |
|----------| -------------|
| `/graphql/execute.json` | Persistenter Abfrageendpunkt |
| `/wknd/adventure-by-path` | Persistenter Abfragepfad |
| `%3B` | Kodierung von `;` |
| `adventurePath` | Abfragevariable |
| `%3D` | Kodierung von `=` |
| `%2F` | Kodierung von `/` |
| `%2Fcontent%2Fdam...` | Kodierter Pfad zum Inhaltsfragment |

Im Klartext sieht der Anfrage-URI wie folgt aus:

```plaintext
/graphql/execute.json/wknd/adventure-by-path;adventurePath=/content/dam/wknd/en/adventures/bali-surf-camp/bali-surf-camp
```

Um eine persistente Abfrage in einer Client-App zu verwenden, sollte das AEM Headless-Client-SDK für [JavaScript](https://github.com/adobe/aem-headless-client-js), [Java](https://github.com/adobe/aem-headless-client-java)oder [NodeJS](https://github.com/adobe/aem-headless-client-nodejs). Das Headless Client SDK kodiert automatisch alle Abfragevariablen in der Anfrage entsprechend.

## Übertragen einer persistenten Abfrage in Ihre Produktionsumgebung  {#transfer-persisted-query-production}

Beständige Abfragen sollten immer in einem AEM-Autorendienst erstellt und dann in einem AEM-Veröffentlichungsdienst veröffentlicht (repliziert) werden. Häufig werden persistente Abfragen in niedrigeren Umgebungen wie lokalen Umgebungen oder Entwicklungsumgebungen erstellt und getestet. Anschließend müssen persistente Abfragen in Umgebungen auf höherer Ebene weitergeleitet werden, um sie letztendlich in einer AEM-Veröffentlichungsumgebung für die Produktion verfügbar zu machen, damit Clientanwendungen verwendet werden können.

### Persistente Paketabfragen

Persistente Abfragen können in [AEM Packages](/help/implementing/developing/tools/package-manager.md). AEM Pakete können dann heruntergeladen und in verschiedenen Umgebungen installiert werden. AEM Pakete können auch von einer AEM-Autorenumgebung in AEM-Veröffentlichungsumgebungen repliziert werden.

So erstellen Sie ein Package:

1. Navigieren Sie zu **Instrumente** > **Implementierung** > **Pakete**.
1. Erstellen Sie ein neues Paket durch Tippen auf **Paket erstellen**. Dadurch wird ein Dialogfeld zum Definieren des Pakets geöffnet.
1. Im Dialogfeld &quot;Package Definition&quot;unter **Allgemein** einen **Name** wie &quot;wknd-persistent-queries&quot;.
1. Geben Sie eine Versionsnummer wie &quot;1.0&quot;ein.
1. under **Filter** einen neuen **Filter**. Verwenden Sie die Pfadsuche, um die `persistentQueries` Ordner unter der Konfiguration. Beispiel für die `wknd` Konfiguration der vollständigen Pfad `/conf/wknd/settings/graphql/persistentQueries`.
1. Tippen **Speichern** , um die neue Paketdefinition zu speichern und das Dialogfeld zu schließen.
1. Tippen Sie auf **Build** in der neu erstellten Package-Definition.

Nachdem das Paket erstellt wurde, können Sie Folgendes tun:

* **Download** das -Paket erstellen und in einer anderen Umgebung erneut hochladen.
* **Replizieren** durch Tippen auf **Mehr** > **Replizieren**. Dadurch wird das Paket in der verbundenen AEM-Veröffentlichungsumgebung repliziert.

<!--
1. Using replication/distribution tool:
   1. Go to the Distribution tool.
   1. Select tree activation for the configuration (for example, `/conf/wknd/settings/graphql/persistentQueries`).

* Using a workflow (via workflow launcher configuration):
  1. Define a workflow launcher rule for executing a workflow model that would replicate the configuration on different events (for example, create, modify, amongst others).
-->
