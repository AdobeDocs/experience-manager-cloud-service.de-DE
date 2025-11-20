---
title: Konfigurieren von Traffic im CDN
description: Erfahren Sie, wie Sie den CDN-Traffic konfigurieren, indem Sie Regeln und Filter in einer Konfigurationsdatei deklarieren und sie mithilfe der Cloud Manager-Konfigurations-Pipeline im CDN bereitstellen.
feature: Dispatcher
exl-id: e0b3dc34-170a-47ec-8607-d3b351a8658e
role: Admin
source-git-commit: 3a46db9c98fe634bf2d4cffd74b54771de748515
workflow-type: tm+mt
source-wordcount: '1698'
ht-degree: 92%

---


# Konfigurieren von Traffic im CDN {#cdn-configuring-cloud}

AEM as a Cloud Service bietet eine Reihe von Funktionen, die auf der Ebene [Adobe-verwaltetes CDN](/help/implementing/dispatcher/cdn.md#aem-managed-cdn) konfigurierbar sind und die Art von eingehenden Anfragen oder ausgehenden Antworten ändern. Die folgenden Regeln, die auf dieser Seite detailliert beschrieben werden, können deklariert werden, um das folgende Verhalten zu erreichen:

* [Anforderungsumwandlungen](#request-transformations) – Änderung von Aspekten eingehender Anfragen, einschließlich Kopfzeilen, Pfaden und Parametern.
* [Reaktionsumwandlungen](#response-transformations) – Änderung von Kopfzeilen, die sich auf dem Weg zurück zum Client befinden (z. B. einen Webbrowser).
* [Server-seitige Umleitungen](#server-side-redirectors) – Auslösen einer Browser-Umleitung.
* [Ursprungs-Auswahlen](#origin-selectors) – Proxy zu einem anderen Ursprungs-Backend.

Ebenfalls im CDN konfigurierbar sind Traffic-Filterregeln (einschließlich WAF), die steuern, welcher Traffic vom CDN erlaubt oder verweigert wird. Diese Funktion wurde bereits veröffentlicht. Weitere Informationen dazu finden Sie auf der Seite [Traffic-Filterregeln, einschließlich WAF-Regeln](/help/security/traffic-filter-rules-including-waf.md).

Wenn das CDN nicht in der Lage ist, seinen Ursprung zu erreichen, können Sie außerdem eine Regel schreiben, die auf eine selbstgehostete benutzerdefinierte Fehlerseite verweist (die dann gerendert wird). Weitere Informationen hierzu finden Sie im Artikel [Konfigurieren von CDN-Fehlerseiten](/help/implementing/dispatcher/cdn-error-pages.md).

Alle diese Regeln, die in einer Konfigurationsdatei in der Verwaltung der Quelle deklariert sind, werden mithilfe der Cloud Manager-[Konfigurations-Pipeline](/help/operations/config-pipeline.md) bereitgestellt. Beachten Sie, dass die kumulative Größe der Konfigurationsdatei, einschließlich Traffic-Filterregeln, 100 KB nicht überschreiten darf.

## Reihenfolge der Auswertung {#order-of-evaluation}

Funktionell werden die verschiedenen oben erwähnten Funktionen in der folgenden Sequenz ausgewertet:

![Reihenfolge der Auswertung](/help/implementing/dispatcher/assets/order.png)

## Setup {#initial-setup}

Bevor Sie Traffic im CDN konfigurieren können, müssen Sie Folgendes tun:

1. Erstellen Sie eine Datei mit dem Namen `cdn.yaml` oder ähnlich, die auf die verschiedenen Konfigurationsausschnitte in den nachfolgenden Abschnitten verweist.

   Alle Ausschnitte verfügen über diese allgemeinen Eigenschaften, die unter [Konfigurations-Pipeline](/help/operations/config-pipeline.md#common-syntax) beschrieben sind. Der Eigenschaftswert `kind` sollte *CDN* sein, und die Eigenschaft `version` sollte auf *1* festgelegt werden.

   ```
   kind: "CDN"
   version: "1"
   ```

1. Platzieren Sie die Datei unter einem Ordner der obersten Ebene mit dem Namen *config* oder ähnlich, wie unter [Konfigurations-Pipelines](/help/operations/config-pipeline.md#folder-structure) beschrieben.

1. Erstellen Sie in Cloud Manager eine Konfigurations-Pipeline, wie unter [Konfigurations-Pipelines](/help/operations/config-pipeline.md#managing-in-cloud-manager) beschrieben.

1. Stellen Sie die Konfiguration bereit.

## Regelsyntax {#configuration-syntax}

Die Regeltypen in den folgenden Abschnitten verwenden eine gemeinsame Syntax.

Eine Regel wird durch einen Namen, einen Bedingungssatz mit „Wenn“ und Aktionen referenziert.

Der Bedingungssatz „Wenn“ bestimmt basierend auf Eigenschaften wie Domain, Pfad, Abfragezeichenfolgen, Header und Cookies, ob eine Regel ausgewertet wird. Die Syntax ist für alle Regeltypen gleich. Weitere Informationen finden Sie im [Abschnitt „Bedingungsstruktur“](/help/security/traffic-filter-rules-including-waf.md#condition-structure) im Artikel zu Traffic-Filterregeln.

Die Details des Aktionsknotens unterscheiden sich je nach Regeltyp und sind in den einzelnen Abschnitten unten beschrieben.

In den Konfigurationsregeln können Sie auf geheime Daten verweisen, die als Umgebungsvariablen definiert sind (siehe [Konfigurationsgeheimnisse](/help/implementing/dispatcher/cdn-credentials-authentication.md)).

## Anforderungsumwandlungen {#request-transformations}

Mit Regeln für Anforderungsumwandlungen können Sie eingehende Anforderungen ändern. Die Regeln unterstützen das Festlegen, Aufheben und Ändern von Pfaden, Abfrageparametern und Kopfzeilen (einschließlich Cookies) basierend auf verschiedenen passenden Bedingungen, einschließlich regulärer Ausdrücke. Sie können auch Variablen festlegen, die später in der Auswertungssequenz referenziert werden können.

Die Anwendungsfälle sind unterschiedlich und enthalten URL-Neuschreibungen zur Vereinfachung der Anwendung oder zur Zuordnung von veralteten URLs.

Wie bereits erwähnt, gibt es eine Größenbeschränkung für die Konfigurationsdatei, sodass Organisationen mit größeren Anforderungen Regeln auf der `apache/dispatcher`-Ebene definieren sollten.

Konfigurationsbeispiel:

```
kind: "CDN"
version: "1"
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
      - name: set-header-with-reqproperty-rule
        when:
          reqProperty: path
          like: /set-header
        actions:
          - type: set
            reqHeader: x-some-header
            value: {reqProperty: path}
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
      - name: log-on-request
        when: "*"
        actions:
          - type: set
            logProperty: forwarded_host
            value:
              reqHeader: x-forwarded-host
```

**Aktionen**

In der folgenden Tabelle werden die verfügbaren Aktionen erläutert.

| Name | Eigenschaften | Bedeutung |
|-----------|--------------------------|-------------|
| **set** | reqProperty, Wert | Legt einen bestimmten Anforderungsparameter fest (nur die Eigenschaft „path“ wird unterstützt) |
|     | reqHeader, Wert | Legt einen bestimmten Anfrage-Header auf einen angegebenen Wert fest. |
|     | queryParam, Wert | Legt einen bestimmten Abfrageparameter auf einen angegebenen Wert fest. |
|     | reqCookie, Wert | Legt ein bestimmtes Anfrage-Cookie auf einen angegebenen Wert fest. |
|     | logProperty, Wert | Legt eine bestimmte CDN-Protokolleigenschaft auf einen angegebenen Wert fest. |
|     | var, Wert | Legt eine bestimmte Variable auf einen angegebenen Wert fest. |
| **unset** | reqProperty | Entfernt einen bestimmten Anfrageparameter (nur die Eigenschaft „path“ wird unterstützt) |
|     | reqHeader, Wert | Entfernt einen bestimmten Anfrage-Header. |
|     | queryParam, Wert | Entfernt einen angegebenen Abfrageparameter. |
|     | reqCookie, Wert | Entfernt ein bestimmtes Cookie. |
|     | logProperty, Wert | Entfernt eine bestimmte CDN-Protokolleigenschaft. |
|     | var | Entfernt eine angegebene Variable. |
|     | queryParamMatch | Entfernt alle Abfrageparameter, die einem angegebenen regulären Ausdruck entsprechen. |
|     | queryParamDoesNotMatch | Entfernt alle Abfrageparameter, die einem angegebenen regulären Ausdruck nicht entsprechen. |
| **Transformieren** | op:replace, (reqProperty oder reqHeader oder queryParam oder reqCookie or var), Übereinstimmung, Ersetzung | Ersetzt einen Teil des Anfrageparameters (nur die „Pfad“-Eigenschaft wird unterstützt) oder des Anfrage-Headers, des Abfrageparameters oder des Cookies oder der Variable durch einen neuen Wert. |
|              | op:tolower, (reqProperty oder reqHeader oder queryParam oder reqCookie oder var) | Setzt den Anfrageparameter (nur die „Pfad“-Eigenschaft wird unterstützt) oder Anfrage-Header, Abfrageparameter oder Cookie oder die Variable auf den entsprechenden Wert in Kleinbuchstaben. |

Aktionen zum Ersetzen unterstützen Erfassungsgruppen, wie unten dargestellt:

```
      - name: extract-country-code-from-path
        when:
          reqProperty: path
          matches: ^/([a-zA-Z]{2})(/.*|$)
        actions:
          - type: set
            var: country-code
            value:
              reqProperty: path
          - type: transform
            var: country-code
            op: replace
            match: ^/([a-zA-Z]{2})(/.*|$)
            replacement: \1
      - name: replace-jpg-with-jpeg
        when:
          reqProperty: path
          like: /mypath
        actions:
          - type: transform
            reqProperty: path
            op: replace
            match: (.*)(\.jpg)$
            replacement: "\1\.jpeg"
```

Aktionen können miteinander verkettet werden. Beispiel:

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

### Protokolleigenschaft {#logproperty}

Sie können Ihre eigenen Protokolleigenschaften in Ihren CDN-Protokollen hinzufügen, indem Sie Anfrage- und Antworttransformationen verwenden.

Konfigurationsbeispiel:

```
requestTransformations:
  rules:
    - name: log-on-request
      when: "*"
      actions:
        - type: set
          logProperty: forwarded_host
          value:
            reqHeader: x-forwarded-host
responseTransformations:
  rules:
    - name: log-on-response
      when: '*'
      actions:
        - type: set
          logProperty: cache_control
          value:
            respHeader: cache-control
```

Beispiel für ein Protokoll:

```
{
"timestamp": "2025-03-26T09:20:01+0000",
"ttfb": 19,
"cli_ip": "147.160.230.112",
"cli_country": "CH",
"rid": "974e67f6",
"req_ua": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/14.0.3 Safari/605.1.15",
"host": "example.com",
"url": "/content/hello.png",
"method": "GET",
"res_ctype": "image/png",
"cache": "PASS",
"status": 200,
"res_age": 0,
"pop": "PAR",
"rules": "",
"forwarded_host": "example.com",
"cache_control": "max-age=300"
}
```

## Reaktionsumwandlungen {#response-transformations}

Mit Regeln zur Reaktionsumwandlung können Sie Header, Cookies und Status der ausgehenden Antworten des CDN festlegen und aufheben. Siehe auch das Beispiel oben für Referenzen auf eine Variable, die zuvor in einer Regel zu Anfrageumwandlung festgelegt wurde.

Konfigurationsbeispiel:

```
kind: "CDN"
version: "1"
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
      - name: status-code-rule
        when:
          reqProperty: path
          like: status-code
        actions:
          - type: set
            respProperty: status
            value: '410'
      - name: set-response-cookie-with-attributes-as-object
        when: '*'
        actions:
          - type: set
            respCookie: first-name
            value: first-value
            attributes:
              expires: '2025-08-29T10:00:00'
              domain: example.com
              path: /some-path
              secure: true
              httpOnly: true
              extension: ANYTHING
      - name: unset-response-cookie
        when: '*'
        actions:
          - type: unset
            respCookie: third-name
```

**Aktionen**

In der folgenden Tabelle werden die verfügbaren Aktionen erläutert.

| Name | Eigenschaften | Bedeutung |
|-----------|--------------------------|-------------|
| **set** | respProperty, Wert | Legt eine Antworteigenschaft fest. Unterstützt nur die Eigenschaft „Status“, um den Status-Code festzulegen. |
|     | respHeader, Wert | Legt einen bestimmten Antwort-Header auf einen angegebenen Wert fest. |
|     | respCookie, Attribute (expires, domain, path, secure, httpOnly, extension), Wert | Legt ein bestimmtes Anfrage-Cookie mit bestimmten Attributen auf einen angegebenen Wert fest. |
|     | logProperty, Wert | Legt eine bestimmte CDN-Protokolleigenschaft auf einen angegebenen Wert fest. |
|     | var, Wert | Legt eine bestimmte Variable auf einen angegebenen Wert fest. |
| **unset** | respHeader | Entfernt eine bestimmte Kopfzeile aus der Antwort. |
|     | respCookie, Wert | Entfernt ein bestimmtes Cookie. |
|     | logProperty, Wert | Entfernt eine bestimmte CDN-Protokolleigenschaft. |
|     | var | Entfernt eine angegebene Variable. |

## Ursprungs-Auswahlen {#origin-selectors}

Sie können das AEM-CDN nutzen, um Traffic an verschiedene Backends zu leiten, einschließlich Adobe-fremder Anwendungen (möglicherweise pro Pfad oder Subdomain).

Konfigurationsbeispiel:

```
kind: "CDN"
version: "1"
data:
  originSelectors:
    rules:
      - name: example-com
        when: { reqProperty: path, like: /proxy* }
        action:
          type: selectOrigin
          originName: example-com
          # skipCache: true
          # headers:
          #   Authorization: ${{AUTH_TOKEN}}
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
|---------------------|--------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **selectOrigin** | originName | Name eines der definierten Ursprünge. |
|                     | skipCache (optional, Standardeinstellung ist „falsch“) | Markierung, ob Caching für Anfragen verwendet werden soll, die dieser Regel entsprechen. Standardmäßig werden Antworten gemäß dem Antwort-Caching-Header zwischengespeichert (z. B. Cache-Steuerung oder Ablaufdatum). |
|                     | Kopfzeilen (optional, Standard ist `{}`) | Schlüssel-Wert-Paare, die zusätzliche HTTP-Header enthalten, die beim Auslösen der Regel an das ausgewählte Backend gesendet werden. Mit Schlüsseln, die Kopfzeilennamen entsprechen, und Werten, die den Kopfzeilenwerten entsprechen |
| **selectAemOrigin** | originName | Name eines der vordefinierten AEM-Ursprünge (unterstützter Wert: `static`). |
|                     | skipCache (optional, Standardeinstellung ist „falsch“) | Markierung, ob Caching für Anfragen verwendet werden soll, die dieser Regel entsprechen. Standardmäßig werden Antworten gemäß dem Antwort-Caching-Header zwischengespeichert (z. B. Cache-Steuerung oder Ablaufdatum). |
|                     | Kopfzeilen (optional, Standard ist `{}`) | Schlüssel-Wert-Paare, die zusätzliche HTTP-Header enthalten, die beim Auslösen der Regel an das ausgewählte Backend gesendet werden. Mit Schlüsseln, die Kopfzeilennamen entsprechen, und Werten, die den Kopfzeilenwerten entsprechen |

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

### Proxys für benutzerdefinierte Domain an die statische AEM-Ebene {#proxy-custom-domain-static}

Mit Urspungs-Selektoren können Sie den AEM-Veröffentlichungs-Traffic an statische AEM-Inhalte weiterleiten, die mithilfe der [Frontend-Pipeline) bereitgestellt &#x200B;](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md). Anwendungsfälle sind die Bereitstellung von statischen Ressourcen auf derselben Domain wie die Seite (z. B. example.com/static) oder auf einer explizit anderen Domain (z. B. static.example.com).

Im Folgenden finden Sie ein Beispiel einer Ursprungs-Auswahlregel, mit der dies erreicht werden kann:

```
kind: CDN
version: '1'
data:
  originSelectors:
    rules:
      - name: select-aem-static-origin
        when:
          reqProperty: domain
          equals: static.example.com
        action:
          type: selectAemOrigin
          originName: static
```

### Proxys zu Edge Delivery Services {#proxying-to-edge-delivery}

Es gibt Fälle, in denen Ursprungs-Auswahlen verwendet werden sollten, um Traffic durch AEM Publish zu AEM Edge Delivery Services zu leiten:

* Einige Inhalte werden von einer von AEM Publish verwalteten Domain bereitgestellt, während andere aus derselben Domain stammenden Inhalte von Edge Delivery Services bereitgestellt werden.
* Von Edge Delivery Services bereitgestellte Inhalte würden von Regeln profitieren, die über die Konfigurations-Pipeline bereitgestellt werden, einschließlich Traffic-Filterregeln oder Anfrage-/Reaktionsumwandlungen.
* Mit der Edge Delivery-Konfigurations-Pipeline können Sie Einstellungen für von Adobe verwaltetes CDN konfigurieren, indem Sie Regeln wie `trafficFilters`, `originSelectors` und `redirects` definieren. <!-- https://wiki.corp.adobe.com/pages/editpage.action?pageId=3610084282 -->

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
              matches: "^(/scripts/.*|/styles/.*|/fonts/.*|/blocks/.*|/icons/.*|.*/media_.*|/favicon.ico)"
        action:
          type: selectOrigin
          originName: aem-live
    origins:
      - name: aem-live
        domain: main--repo--owner.aem.live
```

>[!NOTE]
>
>Da das von Adobe verwaltete CDN verwendet wird, konfigurieren Sie die Push-Invalidierung im **verwalteten** Modus. Befolgen Sie dazu die [Dokumentation zum Einrichten der Push-Invalidierung](https://www.aem.live/docs/byo-dns#setup-push-invalidation) für Edge Delivery Services.


## Server-seitige Umleitungen {#server-side-redirectors}

Sie können Regeln für die Client-seitige Weiterleitung für 301, 302 und ähnliche Client-seitige Weiterleitungen verwenden. Wenn eine Regel übereinstimmt, antwortet das CDN mit einer Statuszeile, die den Status-Code und die Meldung enthält (z. B. HTTP/1.1 301 Permanent verschoben), sowie mit dem Speicherort-Kopfzeilen-Satz.

Sowohl absolute als auch relative Speicherorte mit festen Werten sind zulässig.

Beachten Sie, dass die kumulative Größe der Konfigurationsdatei, einschließlich Traffic-Filterregeln, 100 KB nicht überschreiten darf.

Konfigurationsbeispiel:

```
kind: "CDN"
version: "1"
data:
  redirects:
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

Die Speicherorte einer Umleitung können entweder Zeichenfolgenliterale (z. B. https://www.example.com/page) oder das Ergebnis einer Eigenschaft (z. B. Pfad) sein, die optional mit der folgenden Syntax umgewandelt wird:

```
redirects:
  rules:
    - name: country-code-redirect
      when: { reqProperty: path, like: "/" }
      action:
        type: redirect
        location:
          reqProperty: clientCountry
          transform:
            - op: replace
              match: '^(.*)$'
              replacement: 'https://www.example.com/\1/home'
            - op: tolower
    - name: www-redirect
      when: { reqProperty: domain, equals: "example.com" }
      action:
        type: redirect
        location:
          reqProperty: url
          transform:
            - op: replace
              match: '^/(.*)$'
              replacement: 'https://www.example.com/\1'
```
