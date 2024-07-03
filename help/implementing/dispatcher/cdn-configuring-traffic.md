---
title: Konfigurieren von Traffic im CDN
description: Erfahren Sie, wie Sie den CDN-Traffic konfigurieren, indem Sie Regeln und Filter in einer Konfigurationsdatei deklarieren und sie mithilfe der Cloud Manager-Konfigurations-Pipeline im CDN bereitstellen.
feature: Dispatcher
exl-id: e0b3dc34-170a-47ec-8607-d3b351a8658e
role: Admin
source-git-commit: 1b4297c36995be7a4d305c3eddbabfef24e91559
workflow-type: ht
source-wordcount: '1310'
ht-degree: 100%

---

# Konfigurieren von Traffic im CDN {#cdn-configuring-cloud}

AEM as a Cloud Service bietet eine Reihe von Funktionen, die auf der Ebene [Adobe-verwaltetes CDN](/help/implementing/dispatcher/cdn.md#aem-managed-cdn) konfigurierbar sind und die Art von eingehenden Anfragen oder ausgehenden Antworten ändern. Die folgenden Regeln, die auf dieser Seite detailliert beschrieben werden, können deklariert werden, um das folgende Verhalten zu erreichen:

* [Anforderungsumwandlungen](#request-transformations) – Änderung von Aspekten eingehender Anfragen, einschließlich Kopfzeilen, Pfaden und Parametern.
* [Reaktionsumwandlungen](#response-transformations) – Änderung von Kopfzeilen, die sich auf dem Weg zurück zum Client befinden (z. B. einen Webbrowser).
* [Client-seitige Umleitungen](#client-side-redirectors) – Auslöser einer Browser-Umleitung. Diese Funktion ist noch nicht allgemein verfügbar, steht aber für Early-Adopter zur Verfügung. 
* [Ursprungs-Auswahlen](#origin-selectors) – Proxy zu einem anderen Ursprungs-Backend.

Ebenfalls im CDN konfigurierbar sind Traffic-Filterregeln (einschließlich WAF), die steuern, welcher Traffic vom CDN erlaubt oder verweigert wird. Diese Funktion wurde bereits veröffentlicht. Weitere Informationen dazu finden Sie auf der Seite [Traffic-Filterregeln, einschließlich WAF-Regeln](/help/security/traffic-filter-rules-including-waf.md).

Wenn das CDN nicht in der Lage ist, seinen Ursprung zu erreichen, können Sie außerdem eine Regel schreiben, die auf eine selbstgehostete benutzerdefinierte Fehlerseite verweist (die dann gerendert wird). Weitere Informationen hierzu finden Sie im Artikel [Konfigurieren von CDN-Fehlerseiten](/help/implementing/dispatcher/cdn-error-pages.md).

Alle diese Regeln, die in einer Konfigurationsdatei in der Verwaltung der Quelle deklariert sind, werden mithilfe der [Cloud Manager-Konfigurations-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#config-deployment-pipeline) bereitgestellt. Beachten Sie, dass die kumulative Größe der Konfigurationsdatei, einschließlich Traffic-Filterregeln, 100 KB nicht überschreiten darf.

## Reihenfolge der Auswertung {#order-of-evaluation}

Funktionell werden die verschiedenen oben erwähnten Funktionen in der folgenden Sequenz ausgewertet:

![Bild](/help/implementing/dispatcher/assets/order.png)

## Setup {#initial-setup}

Bevor Sie Traffic im CDN konfigurieren können, müssen Sie Folgendes tun:

* Erstellen Sie diesen Ordner und die Dateistruktur im obersten Ordner Ihres Git-Projekts:

```
config/
     cdn.yaml
```

* Die Konfigurationsdatei `cdn.yaml` sollte sowohl Metadaten als auch die Regeln enthalten, die in den nachfolgenden Beispielen beschrieben sind. Der Parameter `kind` sollte auf `CDN` und die Version auf die Schemaversion eingestellt sein (derzeit `1`). 

* Erstellen Sie eine zielgerichtete Bereitstellungskonfigurations-Pipeline in Cloud Manager. Siehe [Konfigurieren von Produktions-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) und [Konfigurieren von produktionsfremden Pipelines](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md).

**Anmerkungen**

* RDEs unterstützen derzeit nicht die Konfigurations-Pipeline.
* Sie können `yq` verwenden, um die YAML-Formatierung Ihrer Konfigurationsdatei lokal zu überprüfen (z. B. `yq cdn.yaml`).

## Syntax {#configuration-syntax}

Die Regeltypen in den folgenden Abschnitten verwenden eine gemeinsame Syntax.

Eine Regel wird durch einen Namen, einen Bedingungssatz mit „Wenn“ und Aktionen referenziert.

Der Bedingungssatz bestimmt, ob eine Regel basierend auf Eigenschaften wie Domain, Pfad, Abfragezeichenfolgen, Header und Cookies ausgewertet wird. Die Syntax ist für alle Regeltypen gleich. Weitere Informationen finden Sie im [Abschnitt „Bedingungsstruktur“](/help/security/traffic-filter-rules-including-waf.md#condition-structure) im Artikel zu Traffic-Filterregeln.

Die Details des Aktionsknotens unterscheiden sich je nach Regeltyp und sind in den einzelnen Abschnitten unten beschrieben.

## Anforderungsumwandlungen {#request-transformations}

Mit Regeln für Anforderungsumwandlungen können Sie eingehende Anforderungen ändern. Die Regeln unterstützen das Festlegen, Aufheben und Ändern von Pfaden, Abfrageparametern und Kopfzeilen (einschließlich Cookies) basierend auf verschiedenen passenden Bedingungen, einschließlich regulärer Ausdrücke. Sie können auch Variablen festlegen, die später in der Auswertungssequenz referenziert werden können.

Die Anwendungsfälle sind unterschiedlich und enthalten URL-Neuschreibungen zur Vereinfachung der Anwendung oder zur Zuordnung von veralteten URLs.

Wie bereits erwähnt, gibt es eine Größenbeschränkung für die Konfigurationsdatei, sodass Organisationen mit größeren Anforderungen Regeln auf der `apache/dispatcher`-Ebene definieren sollten.

Konfigurationsbeispiel:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev", "stage", "prod"]
data:  
  requestTransformations:
    removeMarketingParams: true
    rules:
      - name: set-header-rule
        when:
          reqProperty: path
          like: /set-header
        actions:
          - type: set
            reqHeader: x-some-header
            value: some value
            
      - name: unset-header-rule
        when:
          reqProperty: path
          like: /unset-header
        actions:
          - type: unset
            reqHeader: x-some-header
            
      - name: unset-matching-query-params-rule
        when:
          reqProperty: path
          equals: /unset-matching-query-params
        actions:
          - type: unset
            queryParamMatch: ^removeMe_.*$
            
      - name: unset-all-query-params-except-exact-two-rule
        when:
          reqProperty: path
          equals: /unset-all-query-params-except-exact-two
        actions:
          - type: unset
            queryParamMatch: ^(?!leaveMe$|leaveMeToo$).*$
            
      - name: multi-action
        when:
          reqProperty: path
          like: /multi-action
        actions:
          - type: set
            reqHeader: x-header1
            value: body set by transformation rule
          - type: set
            reqHeader: x-header2
            value: '201'
            
      - name: replace-html
        when:
          reqProperty: path
          like: /mypath
        actions:
          - type: transform
           reqProperty: path
           op: replace
           match: \.html$
           replacement: ""
```

**Aktionen**

In der folgenden Tabelle werden die verfügbaren Aktionen erläutert.

| Name | Eigenschaften | Bedeutung |
|-----------|--------------------------|-------------|
| **set** | (reqProperty oder reqHeader oder queryParam oder reqCookie), Wert | Legt einen angegebenen Anfrageparameter (nur die „Pfad“-Eigenschaft wird unterstützt) oder einen Anfrage-Header, Abfrageparameter oder Cookie auf einen bestimmten Wert fest. |
|     | var, Wert | Legt einen bestimmten Anfrageparameter auf einen angegebenen Wert fest. |
| **unset** | reqProperty | Entfernt einen angegebenen Anfrageparameter (nur die „Pfad“-Eigenschaft wird unterstützt) oder einen Anfrage-Header, Abfrageparameter oder Cookie auf einen bestimmten Wert. |
|         | var | Entfernt eine angegebene Variable. |
|         | queryParamMatch | Entfernt alle Abfrageparameter, die einem angegebenen regulären Ausdruck entsprechen. |
| **Transformieren** | op:replace, (reqProperty oder reqHeader oder queryParam oder reqCookie), Übereinstimmung, Ersatz | Ersetzt einen Teil des Anfrageparameters (nur die „Pfad“-Eigenschaft wird unterstützt) oder des Anfrage-Headers, des Abfrageparameters oder des Cookies durch einen neuen Wert. |
|              | op:tolower, (reqProperty oder reqHeader oder queryParam oder reqCookie) | Setzt den Anfrageparameter (nur die „Pfad“-Eigenschaft wird unterstützt) oder Anfrage-Header, Abfrageparameter oder Cookie auf seinen Wert in Kleinbuchstaben. |

Aktionen können miteinander verkettet werden. Zum Beispiel:

```
actions:
    - type: transform
      reqProperty: path
      op: replace
      match: \.html$
      replacement: ""
    - type: transform
      reqProperty: path
      op: tolower
```

### Variablen {#variables}

Sie können Variablen während der Anforderungsumwandlung festlegen und später in der Auswertungssequenz darauf verweisen. Weitere Informationen finden Sie im Diagramm [Reihenfolge der Auswertung](#order-of-evaluation).

Konfigurationsbeispiel:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["prod", "dev"]
data:   
  requestTransformations:
    rules:
      - name: set-variable-rule
        when:
          reqProperty: path
          equals: /set-variable
        actions:
          - type: set
            var: some_var_name
            value: some_value
 
  responseTransformations:
    rules:
      - name: set-response-header-while-variable
        when:
          var: some_var_name
          equals: some_value
        actions:
          - type: set
            respHeader: x-some-header
            value: some header value
```

## Reaktionsumwandlungen {#response-transformations}

Mit Regeln zur Reaktionsumwandlung können Sie Kopfzeilen der ausgehenden Antworten des CDN festlegen und aufheben. Siehe auch das Beispiel oben für Referenzen auf eine Variable, die zuvor in einer Regel zu Anfrageumwandlung festgelegt wurde.

Konfigurationsbeispiel:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["prod", "dev"]
data:
  responseTransformations:
    rules:
      - name: set-response-header-rule
        when:
          reqProperty: path
          like: /set-response-header
        actions:
          - type: set
            value: value-set-by-resp-rule
            respHeader: x-resp-header
 
      - name: unset-response-header-rule
        when:
          reqProperty: path
          like: /unset-response-header
        actions:
          - type: unset
            respHeader: x-header1
 
      # Example: Multi-action on response header
      - name: multi-action-response-header-rule
        when:
          reqProperty: path
          like: /multi-action-response-header
        actions:
          - type: set
            respHeader: x-resp-header-1
            value: value-set-by-resp-rule-1
          - type: set
            respHeader: x-resp-header-2
            value: value-set-by-resp-rule-2
```

**Aktionen**

In der folgenden Tabelle werden die verfügbaren Aktionen erläutert.

| Name | Eigenschaften | Bedeutung |
|-----------|--------------------------|-------------|
| **set** | reqHeader, Wert | Legt eine bestimmte Kopfzeile auf einen angegebenen Wert in der Antwort fest. |
| **nicht gesetzt** | respHeader | Entfernt eine bestimmte Kopfzeile aus der Antwort. |

## Ursprungs-Auswahlen {#origin-selectors}

Sie können das AEM-CDN nutzen, um Traffic an verschiedene Backends zu leiten, einschließlich Adobe-fremder Anwendungen (möglicherweise pro Pfad oder Subdomain).

Konfigurationsbeispiel:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  originSelectors:
    rules:
      - name: example-com
        when: { reqProperty: path, like: /proxy-me* }
        action:
          type: selectOrigin
          originName: example-com
          # useCache: false
    origins:
      - name: example-com
        domain: www.example.com
        # ip: '1.1.1.1'
        # forwardHost: true
        # forwardCookie: true 
        # forwardAuthorization: true
        # timeout: 20
```

**Aktionen**

In der folgenden Tabelle wird die verfügbare Aktion erläutert.

| Name | Eigenschaften | Bedeutung |
|-----------|--------------------------|-------------|
| **selectOrigin** | originName | Name eines der definierten Ursprünge. |
|     | useCache (optional, Standardeinstellung ist „true“) | Flag, ob Caching für Anforderungen verwendet werden soll, die dieser Regel entsprechen. |

**Ursprünge**

Verbindungen zu Ursprüngen sind nur SSL-Verbindungen und verwenden Port 443.

| Eigenschaft | Bedeutung |
|------------------|--------------------------------------|
| **name** | Name, der durch „action.originName“ referenziert werden kann. |
| **domain** | Domain-Name, der für die Verbindung mit dem benutzerdefinierten Backend verwendet wird. Er wird auch für SSL-SNI und -Validierung verwendet. |
| **ip** (optional, unterstützt iv4 und ipv6) | Sofern angegeben, wird sie zum Herstellen einer Verbindung mit dem Backend anstelle von „domain“ verwendet. „domain“ wird weiterhin für SSL-SNI und -Validierung verwendet. |
| **forwardHost** (optional, Standardeinstellung ist „false“) | Wenn die Eigenschaft auf „true“ gesetzt ist, wird die „Host“-Kopfzeile aus der Client-Anforderung an das Backend übergeben, andernfalls wird der Wert „domain“ in der Kopfzeile „Host“ übergeben. |
| **forwardCookie** (optional, Standardeinstellung ist „false“) | Wenn die Eigenschaft auf „true“ gesetzt ist, wird die „Cookie“-Kopfzeile aus der Client-Anforderung an das Backend übergeben, andernfalls wird die Kopfzeile „Cookie“ entfernt. |
| **forwardAuthorization** (optional, Standardeinstellung ist „false“) | Wenn die Eigenschaft auf „true“ gesetzt ist, wird die „Autorisierung“-Kopfzeile aus der Client-Anforderung an das Backend übergeben, andernfalls wird die Kopfzeile „Autorisierung“ entfernt. |
| **timeout** (optional, in Sekunden, Standardeinstellung ist „60“) | Anzahl der Sekunden, die das CDN darauf warten soll, dass ein Backend-Server das erste Byte eines HTTP-Antworttextes bereitstellt. Dieser Wert wird auch als Timeout zwischen Bytes zum Backend-Server verwendet. |

### Proxys zu Edge Delivery Services {#proxying-to-edge-delivery}

Es gibt Fälle, in denen Ursprungs-Auswahlen verwendet werden sollten, um Traffic durch AEM Publish zu AEM Edge Delivery Services zu leiten:

* Einige Inhalte werden von einer von AEM Publish verwalteten Domain bereitgestellt, während andere Inhalte, die aus derselben Domain stammen, von Edge Delivery Services bereitgestellt werden.
* Inhalte, die von Edge Delivery Services bereitgestellt werden, würden von Regeln profitieren, die über die Konfigurations-Pipeline bereitgestellt werden, einschließlich Traffic-Filterregeln oder Anfrage-/Reaktionsumwandlungen.

Im Folgenden finden Sie ein Beispiel einer Ursprungs-Auswahlregel, mit der dies erreicht werden kann:

```
kind: CDN
version: '1'
data:
  originSelectors:
    rules:
      - name: select-edge-delivery-services-origin
        when:
          allOf:
            - reqProperty: tier
              equals: publish
            - reqProperty: domain
              equals: <Production Host>
            - reqProperty: path
              matches: "^^(/scripts/.*|/styles/.*|/fonts/.*|/blocks/.*|/icons/.*|.*/media_.*|/favicon.ico)"
        action:
          type: selectOrigin
          originName: aem-live
    origins:
      - name: aem-live
        domain: main--repo--owner.aem.live
```

>[!NOTE]
> Da das von Adobe verwaltete CDN verwendet wird, konfigurieren Sie die Push-Invalidierung im Modus **managed**. Folgen Sie dazu der [Dokumentation zum Einrichten der Push-Invalidierung](https://www.aem.live/docs/byo-dns#setup-push-invalidation) für Edge Delivery Services.


## Client-seitige Umleitungen {#client-side-redirectors}

>[!NOTE]
>Diese Funktion ist noch nicht allgemein verfügbar.  Um dem Early-Adopter-Programm beizutreten, senden Sie eine E-Mail an `aemcs-cdn-config-adopter@adobe.com` und beschreiben Sie Ihren Anwendungsfall.

Sie können Regeln für die Client-seitige Weiterleitung für 301, 302 und ähnliche Client-seitige Weiterleitungen verwenden. Wenn eine Regel übereinstimmt, antwortet das CDN mit einer Statuszeile, die den Status-Code und die Meldung enthält (z. B. HTTP/1.1 301 Permanent verschoben), sowie mit dem Speicherort-Kopfzeilen-Satz.

Sowohl absolute als auch relative Speicherorte mit festen Werten sind zulässig.

Beachten Sie, dass die kumulative Größe der Konfigurationsdatei, einschließlich Traffic-Filterregeln, 100 KB nicht überschreiten darf.

Konfigurationsbeispiel:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  experimental_redirects:
    rules:
      - name: redirect-absolute
        when: { reqProperty: path, equals: "/page.html" }
        action:
          type: redirect
          status: 301
          location: https://example.com/page
      - name: redirect-relative
        when: { reqProperty: path, equals: "/anotherpage.html" }
        action:
          type: redirect
          location: /anotherpage
```

| Name | Eigenschaften | Bedeutung |
|-----------|--------------------------|-------------|
| **redirect** | location | Wert für die Kopfzeile „Speicherort“. |
|     | status (optional, Standardeinstellung ist 301) | Der HTTP-Status, der in der Umleitungsnachricht verwendet werden soll, standardmäßig 301, die zulässigen Werte sind: 301, 302, 303, 307, 308. |
