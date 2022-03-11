---
title: Beständige GraphQL-Abfragen
description: Erfahren Sie, wie Sie GraphQL-Abfragen in Adobe Experience Manager beibehalten, um die Leistung zu optimieren. Persistente Abfragen können von Clientanwendungen mithilfe der HTTP-GET-Methode angefordert werden. Die Antwort kann dann auf der Dispatcher- und CDN-Ebene zwischengespeichert werden, wodurch die Leistung der Clientanwendungen verbessert wird.
feature: Content Fragments,GraphQL API
exl-id: 080c0838-8504-47a9-a2a2-d12eadfea4c0
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 60%

---

# Beständige GraphQL-Abfragen {#persisted-queries-caching}

Beständige Abfragen sind GraphQL-Abfragen, die auf dem AEM-Server erstellt und gespeichert werden. Standardmäßige GraphQL-Abfragen werden mit POST-Anforderungen ausgeführt und die Antwort kann nicht einfach zwischengespeichert werden. Beständige Abfragen können von Clientanwendungen mit einer GET-Anfrage angefordert werden. Die Antwort einer GET-Anfrage kann auf den Dispatcher- und CDN-Ebenen zwischengespeichert werden, was letztendlich die Leistung der anfragenden Client-Anwendung verbessert.

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
>Die **GraphQL-Persistenzabfragen** für die entsprechende Sites-Konfiguration müssen aktiviert werden.

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

## Beibehalten einer GraphQL-Abfrage

Es wird empfohlen, Abfragen zunächst in einer AEM Autorenumgebung zu speichern und dann [Abfrage veröffentlichen](#publish-persisted-query) in eine AEM Veröffentlichungsumgebung. Tools wie [Postman](https://www.postman.com/) oder Befehlszeilen-Tools wie [curl](https://curl.se/) verwendet werden.

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

## Persistente Abfrage veröffentlichen {#publish-persisted-query}

Beständige Abfragen können in einer AEM-Veröffentlichungsumgebung veröffentlicht werden, in der sie von Clientanwendungen angefordert werden können. Um eine persistente Abfrage in der Veröffentlichungsinstanz zu verwenden, muss die zugehörige persistente Struktur repliziert werden.

Es gibt mehrere Ansätze zum Veröffentlichen einer persistenten Abfrage:

* **Verwenden einer POST-Anfrage für die Replikation**:

   ```xml
   $ curl -X POST   http://localhost:4502/bin/replicate.json \
   -H 'authorization: Basic YWRtaW46YWRtaW4=' \
   -F path=/conf/wknd/settings/graphql/persistentQueries/plain-article-query \
   -F cmd=activate
   ```

* **Verwenden eines Pakets**:
   1. Erstellen Sie eine neue Paketdefinition.
   1. Fügen Sie die Konfiguration ein (z. B. `/conf/wknd/settings/graphql/persistentQueries`).
   1. Erstellen Sie das Paket.
   1. Replizieren Sie das Paket.

* **Replikations-/Verteilungstool verwenden**:
   1. Wechseln Sie zum Verteilungs-Tool.
   1. Wählen Sie die Baumaktivierung für die Konfiguration (z. B. `/conf/wknd/settings/graphql/persistentQueries`) aus.

* **Verwenden eines Workflows (über die Workflow-Starter-Konfiguration)**:
   1. Definieren Sie eine Workflow-Starterregel zum Ausführen eines Workflow-Modells, das die Konfiguration für verschiedene Ereignisse repliziert (z. B. Erstellen, Ändern).

Sobald sich die Konfiguration der Abfrage auf der Veröffentlichungsinstanz befindet, gelten dieselben Authentifizierungsprinzipien, nur unter Verwendung des Veröffentlichungsendpunkts.

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
