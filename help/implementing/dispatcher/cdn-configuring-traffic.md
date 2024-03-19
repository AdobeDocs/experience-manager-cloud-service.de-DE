---
title: Konfigurieren von Traffic im CDN
description: Erfahren Sie, wie Sie den CDN-Traffic konfigurieren, indem Sie Regeln und Filter in einer Konfigurationsdatei deklarieren und sie mithilfe der Cloud Manager Configuration Pipeline im CDN bereitstellen.
feature: Dispatcher
source-git-commit: 0a0c9aa68b192e8e2a612f50a58ba5f9057c862d
workflow-type: tm+mt
source-wordcount: '974'
ht-degree: 2%

---


# Konfigurieren von Traffic im CDN {#cdn-configuring-cloud}

>[!NOTE]
>Diese Funktion ist noch nicht allgemein verfügbar. Um dem Programm für frühe Anwender beizutreten, senden Sie eine E-Mail `aemcs-cdn-config-adopter@adobe.com` und beschreiben Sie Ihren Anwendungsfall.

AEM as a Cloud Service bietet eine Reihe von Funktionen, die im Abschnitt [Adobe-verwaltetes CDN](/help/implementing/dispatcher/cdn.md#aem-managed-cdn) -Ebene, die die Natur von eingehenden oder ausgehenden Anforderungen ändert. Die folgenden Regeln, die auf dieser Seite detailliert beschrieben werden, können deklariert werden, um das folgende Verhalten zu erreichen:

* [Umwandlungen anfordern](#request-transformations) - Änderung von Aspekten eingehender Anfragen, einschließlich Kopfzeilen, Pfaden und Parametern.
* [Reaktionstransformationen](#response-transformations) - Ändern Sie Kopfzeilen, die sich auf dem Weg zum Client befinden (z. B. einen Webbrowser).
* [Clientseitige Weiterleitungen](#client-side-redirectors) - Trigger einer Browser-Umleitung.
* [Origin-Selektoren](#origin-selectors) - Proxy zu einem anderen Ursprungs-Backend.

Ebenfalls im CDN konfigurierbar sind Traffic-Filterregeln (einschließlich WAF), die steuern, welcher Traffic vom CDN erlaubt oder verweigert wird. Diese Funktion wurde bereits veröffentlicht. Weitere Informationen dazu finden Sie unter [Traffic-Filterregeln, einschließlich WAF-Regeln](/help/security/traffic-filter-rules-including-waf.md) Seite.

Wenn das CDN nicht in der Lage ist, seine Herkunft zu erreichen, können Sie außerdem eine Regel schreiben, die auf eine selbstgehostete benutzerdefinierte Fehlerseite verweist (die dann gerendert wird). Weitere Informationen hierzu finden Sie im Abschnitt [Konfigurieren von CDN-Fehlerseiten](/help/implementing/dispatcher/cdn-error-pages.md) Artikel.

Alle diese Regeln, die in einer Konfigurationsdatei in der Quell-Code-Verwaltung deklariert sind, werden mithilfe von [Cloud Manager-Konfigurations-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#config-deployment-pipeline). Beachten Sie, dass die kumulative Größe der Konfigurationsdatei 100 KB nicht überschreiten darf.

## Reihenfolge der Bewertung {#order-of-evaluation}

Funktionell werden die verschiedenen oben erwähnten Funktionen in der folgenden Sequenz ausgewertet:

![Bild](/help/implementing/dispatcher/assets/order.png)

## Setup {#initial-setup}

Bevor Sie Traffic im CDN konfigurieren können, müssen Sie Folgendes tun:

* Erstellen Sie zunächst diesen Ordner und die Dateistruktur im Ordner der obersten Ebene Ihres Git-Projekts:

```
config/
     cdn.yaml
```

* Zweitens, die `cdn.yaml` -Konfigurationsdatei sollte sowohl Metadaten als auch die Regeln enthalten, die in den folgenden Beispielen beschrieben werden.

## Anforderungsumwandlungen {#request-transformations}

Mit Umwandlungsregeln für Anforderungen können Sie eingehende Anforderungen ändern. Die Regeln unterstützen das Festlegen, Aufheben und Ändern von Pfaden, Abfrageparametern und Kopfzeilen (einschließlich Cookies) basierend auf verschiedenen Bedingungen, einschließlich regulärer Ausdrücke. Sie können auch Variablen festlegen, die später in der Auswertungssequenz referenziert werden können.

Anwendungsfälle sind unterschiedlich und enthalten URL-Neuschreibungen zur Vereinfachung der Anwendung oder zur Zuordnung von veralteten URLs.

Wie bereits erwähnt, gibt es eine Größenbeschränkung für die Konfigurationsdatei, sodass Organisationen mit größeren Anforderungen Regeln in der `apache/dispatcher` Ebene.

Konfigurationsbeispiel:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["prod", "dev"]
data:  
  experimental_requestTransformations:
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
 
      - name: set-query-param-rule
        when:
          reqProperty: path
          equals: /set-query-param
        actions:
          - type: set
            queryParam: someParam
            value: someValue
 
      - name: unset-query-param-rule
        when:
          reqProperty: path
          equals: /unset-query-param
        actions:
          - type: unset
            queryParam: someParam
 
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
 
      - name: set-req-cookie-rule
        when:
          reqProperty: path
          equals: /set-req-cookie
        actions:
          - type: set
            reqCookie: someParam
            value: someValue
 
      - name: unset-req-cookie-rule
        when:
          reqProperty: path
          equals: /unset-req-cookie
        actions:
          - type: unset
            reqCookie: someParam
 
      - name: set-variable-rule
        when:
          reqProperty: path
          equals: /set-variable
        actions:
          - type: set
            var: some_var_name
            value: some value
 
      - name: unset-variable-rule
        when:
          reqProperty: path
          equals: /unset-variable
        actions:
          - type: unset
            var: some_var_name
 
      - name: replace-segment
        when:
          reqProperty: path
          like: /replace-segment/*
        actions:
          - type: replace
            reqProperty: path
            match: /replace-segment/
            value: /segment-was-replaced/
 
      - name: replace-extension
        when:
          reqProperty: path
          like: /replace-extension/*.html
        actions:
          - type: replace
            reqProperty: path
            match: \.html
            value: ''
 
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
```

**Aktionen**

In der folgenden Tabelle werden die verfügbaren Aktionen erläutert.

| Name | Eigenschaften | Bedeutung |
|-----------|--------------------------|-------------|
| **set** | reqHeader, Wert | Legt einen angegebenen Header auf einen angegebenen Wert fest. |
|     | queryParam, value | Legt einen angegebenen Abfrageparameter auf einen angegebenen Wert fest. |
|     | reqCookie, Wert | Legt für ein angegebenes Cookie einen bestimmten Wert fest. |
|     | var, Wert | Legt eine angegebene Variable auf einen angegebenen Wert fest. |
| **unset** | reqHeader | Entfernt eine angegebene Kopfzeile. |
|         | queryParam | Entfernt einen angegebenen Abfrageparameter. |
|         | reqCookie | Entfernt ein angegebenes Cookie. |
|         | var | Entfernt eine angegebene Variable. |
|         | queryParamMatch | Entfernt alle Abfrageparameter, die einem angegebenen regulären Ausdruck entsprechen. |
| **replace** | reqProperty, match, value | Ersetzt einen Teil der Anfrageeigenschaft durch einen neuen Wert. Derzeit wird nur die Eigenschaft &quot;path&quot;unterstützt. |

### Variablen {#variables}

Sie können Variablen während der Anforderungsumwandlung festlegen und später in der Auswertungssequenz darauf verweisen. Siehe [Bewertungsordnung](#order-of-evaluation) Diagramm für weitere Details.

Konfigurationsbeispiel:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["prod", "dev"]
data:   
  experimental_requestTransformations:
    rules:
      - name: set-variable-rule
        when:
          reqProperty: path
          equals: /set-variable
        actions:
          - type: set
            var: some_var_name
            value: some_value
 
  experimental_responseTransformations:
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

## Reaktionskonvertierungen {#response-transformations}

Mit Regeln zur Antwortumwandlung können Sie Kopfzeilen der ausgehenden Antworten des CDN festlegen und aufheben. Siehe auch das obige Beispiel für Verweise auf eine Variable, die zuvor in einer Anfrageumwandlungsregel festgelegt wurde.

Konfigurationsbeispiel:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["prod", "dev"]
data:
  experimental_responseTransformations:
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
| **set** | reqHeader, Wert | Legt einen angegebenen Header auf einen angegebenen Wert in der Antwort fest. |
| **unset** | respHeader | Entfernt einen angegebenen Header aus der Antwort. |

## Ursprüngliche Selektoren {#origin-selectors}

Sie können das AEM CDN nutzen, um Traffic an verschiedene Backends zu leiten, einschließlich Nicht-Adobe-Anwendungen (möglicherweise pro Pfad oder Subdomain).

Konfigurationsbeispiel:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  experimental_originSelectors:
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
| **selectOrigin** | originName | Name des definierten Ursprungs. |
|     | useCache (optional, Standardeinstellung ist &quot;true&quot;) | Flag, ob für Anforderungen, die dieser Regel entsprechen, Zwischenspeicherung verwendet werden soll. |

**Ursprung**

Verbindungen zu Quellen sind nur SSL-Anschluss und verwenden Port 443.

| Eigenschaft | Bedeutung |
|------------------|--------------------------------------|
| **name** | Name, der durch &quot;action.originName&quot;referenziert werden kann. |
| **domain** | Domänenname, der für die Verbindung mit dem benutzerdefinierten Backend verwendet wird. Es wird auch für SSL-SNI und -Validierung verwendet. |
| **ip** (optional, unterstützt iv4 und ipv6) | Sofern angegeben, wird sie zum Herstellen einer Verbindung mit dem Backend anstelle von &quot;Domäne&quot;verwendet. &quot;Domäne&quot;wird weiterhin für SSL-SNI und -Validierung verwendet. |
| **forwardHost** (optional, Standardeinstellung ist &quot;false&quot;) | Wenn der Wert auf &quot;true&quot;gesetzt ist, wird der &quot;Host&quot;-Header aus der Clientanforderung an das Backend übergeben, andernfalls wird der &quot;domain&quot;-Wert in der &quot;Host&quot;-Kopfzeile übergeben. |
| **forwardCookie** (optional, Standardeinstellung ist &quot;false&quot;) | Wenn der Wert auf &quot;true&quot;gesetzt ist, wird der Header &quot;Cookie&quot;aus der Clientanforderung an das Backend übergeben, andernfalls wird der Cookie-Header entfernt. |
| **forwardAuthorization** (optional, Standardeinstellung ist &quot;false&quot;) | Wenn der Wert auf &quot;true&quot;gesetzt ist, wird der Header &quot;Authorization&quot;aus der Clientanforderung an das Backend übergeben, andernfalls wird der Autorisierungs-Header entfernt. |
| **timeout** (optional, in Sekunden ist der Standardwert 60) | Anzahl der Sekunden, die das CDN darauf warten sollte, dass ein Backend-Server das erste Byte eines HTTP-Antworttextes bereitstellt. Dieser Wert wird auch als Zwischen-Byte-Timeout zum Backend-Server verwendet. |

## Clientseitige Weiterleitungen {#client-side-redirectors}

Sie können clientseitige Weiterleitungsregeln für 301, 302 und ähnliche clientseitige Weiterleitungen verwenden. Wenn eine Regel übereinstimmt, antwortet das CDN mit einer Statuszeile, die den Statuscode und die Meldung enthält (z. B. HTTP/1.1 301 Permanent verschoben), sowie mit dem Speicherort-Header-Satz.

Sowohl absolute als auch relative Positionen mit festen Werten sind zulässig.

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
| **umleiten** | location | Wert für die Kopfzeile &quot;Position&quot;. |
|     | status (optional, Standard ist 301) | Der HTTP-Status, der in der Umleitungsnachricht verwendet werden soll, standardmäßig 301, die zulässigen Werte sind: 301, 302, 303, 307, 308. |
