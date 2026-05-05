---
title: CDN-Konfigurations-Snippets für gängige Szenarien
description: Kopierfertige YAML-Muster für das von Adobe verwaltete CDN und kundenverwaltete CDN-Setups, einschließlich Edge-Authentifizierung, Umleitungen, Cache-Variation, Traffic-Formung und Ratenbeschränkungen.
feature: Dispatcher
role: Admin
source-git-commit: ab43facbd4c34c92878e303acf2fef9cc127e28a
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---


# CDN-Konfigurations-Snippets für gängige Szenarien {#cdn-configuration-snippets}

Dieser Artikel sammelt praktische `cdn.yaml` für AEM as a Cloud Service. Verwenden Sie sie zusammen mit der Funktionsdokumentation für [CDN-Traffic](/help/implementing/dispatcher/cdn-configuring-traffic.md)-Regeln, [kundenverwaltete CDN-](/help/implementing/dispatcher/cdn-credentials-authentication.md) und [Traffic-Filterregeln einschließlich WAF](/help/security/traffic-filter-rules-including-waf.md). Bereitstellen von Snippets mit einer Cloud Manager [Konfigurations-Pipeline](/help/operations/config-pipeline.md).

>[!NOTE]
>
>Ersetzen Sie Hostnamen, Pfade, IP-Bereiche, Schlüssel und Schwellenwerte durch Werte, die Ihrem Programm entsprechen. Testen Sie Änderungen in einer Nicht-Produktionsumgebung, bevor Sie sie weiterleiten.

## Vom Kunden verwaltetes CDN {#customer-managed-cdn}

### Einrichten der Edge-Schlüsselauthentifizierung nur für einige Domains {#edge-auth-selected-hosts}

Problem: In einem [vom Kunden verwalteten CDN](/help/implementing/dispatcher/cdn.md#point-to-point-cdn) müssen Sie die Authentifizierung für einige Kunden-Hostnamen erzwingen, während andere Hostnamen, die die Veröffentlichung erreichen, ohne diese Kopfzeile verfügbar bleiben sollten (z. B. während des Rollouts oder wenn sich nur eine Marken-Domain hinter Ihrem CDN befindet).

Lösung: `X-AEM-Edge-Key` Authentifizierung ist nur erforderlich, wenn der erste Host-Name von `X-Forwarded-Host` Ihrem Ziel-Host-Namen entspricht (z. B. `example.com`). Die Regel verwendet die `forwardedDomain`-Anfrageeigenschaft, um diese Übereinstimmung durchzuführen, und führt die `authenticate` Aktion für Ihren Edge-Authentifizierer aus. Ersetzen Sie Host-Namen, Authentifizierungsnamen und Schlüssel-Platzhalter für Ihr Programm.

```yaml
kind: "CDN"
version: "1"
data:
  authentication:
    authenticators:
      - name: edge-key-auth
        type: edge
        edgeKey1: ${{CDN_EDGEKEY_1}}
        edgeKey2: ${{CDN_EDGEKEY_2}}
    rules:
      - name: edge-key-auth-rule
        when: { reqProperty: forwardedDomain, equals: "example.com" }
        action:
          type: authenticate
          authenticator: edge-key-auth
```

### Einrichten der Edge-Schlüsselauthentifizierung für Anfragen, die nicht von VPN-IPs stammen {#edge-auth-trusted-ips}

Problem: Einrichten der Edge-Schlüsselauthentifizierung für BYOCDN, aber direkten Zugriff auf die Veröffentlichungsdomäne nur für VPN-IPs zulassen

Lösung: Authentifizierung mit X-AEM-Edge-Key nur dann erforderlich, wenn die Client-IP nicht in der Liste der VPN-IPs enthalten ist

```yaml
kind: "CDN"
version: "1"
data:
  authentication:
    authenticators:
      - name: edge-key-auth
        type: edge
        edgeKey1: ${{CDN_EDGEKEY_1}}
        edgeKey2: ${{CDN_EDGEKEY_2}}
    rules:
      - name: edge-key-auth-rule
        when: { reqProperty: clientIp, notIn: ["10.0.0.1", "11.0.0.0/24", "<other VPN IPs>"] }
        action:
          type: authenticate
          authenticator: edge-key-auth
```

## Umleitungen {#redirects}

### Weiterleitung von APEX Domain zu www {#apex-to-www}

```yaml
kind: "CDN"
version: "1"
data:
 redirects:
   rules:
     - name: non-www-to-www-redirect
       when:
         reqProperty: domain
         doesNotMatch: '^www\.'
       action:
         type: redirect
         status: 301
         location:
           join:
             format: 'https://www.%s%s'
             args:
               - reqProperty: domain
               - reqProperty: url
```

### Ändern des Cache-Schlüssels {#cache-key}

Das CDN stellt kein separates Feld „Cache-Schlüssel“ zur Verfügung. Da die URL an der Zwischenspeicherung beteiligt ist, können Sie Cache-Einträge aufteilen, indem Sie die URL ändern - z. B. indem Sie einen Abfrageparameter über eine [Anfragetransformation“ ](/help/implementing/dispatcher/cdn-configuring-traffic.md#request-transformations).

```yaml
kind: "CDN"
version: "1"
data:
  requestTransformations:
    rules:
      - name: set-request-different-cache-curl
        when:
          allOf:
            - reqProperty: tier
              equals: publish
            - reqHeader: user-agent
              matches: curl
        actions:
          - type: set
            queryParam: cache
            value: 'curl'
```

### Zu einem normalisierten Pfad umleiten {#trailing-slash}

Senden Sie eine permanente Umleitung, wenn ein Browser bei der Veröffentlichung einen Schrägstrich anfordert, z. B. von `https://www.example.com/path/` zu `https://www.example.com/path`.

```yaml
kind: "CDN"
version: "1"
data:
  redirects:
    rules:
      - name: remove-trailing-slash
        when:
          allOf:
            - reqProperty: tier
              equals: publish
            - reqProperty: domain
              equals: www.example.com
            - reqProperty: originalPath
              matches: ^/(.+)/$
        action:
          type: redirect
          status: 301
          location:
            reqProperty: originalPath
            transform:
              - op: replace
                match: ^/(.+)/$
                replacement: https://www.example.com/\1
```

### Extrahieren von Informationen aus einem JSON-Cookie {#json-cookie}

```yaml
kind: "CDN"
version: "1"
data:
  requestTransformations:
    rules:
      - name: options-response
        when: { reqProperty: tier, equals: publish }
        actions:
        - type: set
          reqHeader: x-mycookie-info
          value:
            reqCookie: mycookie
            transform: 
            - 'base64decode'
            - { op: 'replace', match: '"info":\s*"([^"]*)"', replacement: '\1'} 
```

## Cross Origin Setup {#cross-origin}

### Bedienen von OPTIONS-Anfragen vom CDN {#options-from-cdn}

```yaml
kind: "CDN"
version: "1"
data:
  requestTransformations:
    rules:
      - name: options-response
        when:
          allOf: 
            - { reqProperty: path, like: /mypathi*  }
            - { reqProperty: method, equals: "OPTIONS" }
            - { reqHeader: Origin, equals: "https://example.com" }
        actions:
          - type: respond
            status: 200
            reason: "OK"
            headers:
              content-type: 'text/plain'
              access-control-allow-origin: { reqHeader: Origin }
              access-control-allow-methods: "*"
              access-control-allow-headers: "*"
```

## Traffic-Filter {#traffic-filters}

### Ratenbegrenzungs-ASN {#rate-limit-asn}

Problem: Bei den Ratenbeschränkungen pro IP kann ein verteiltes Denial-of-Service (DDoS)-Muster übersehen werden: Jede Adresse bleibt unter dem Schwellenwert, sodass legitimer und missbräuchlicher Traffic auf der IP-Ebene gleich aussieht.

Lösung: Anzahl der Anfragen nach autonomem Systemnamen (`clientAsName`), sodass der Begrenzer Hosts aggregiert, die denselben Netzwerknamen haben. Der Ausschnitt schreibt bei jeder Anfrage `clientAsName` in eine Protokolleigenschaft und wendet dann eine Ratenbeschränkung auf „author“ und „publish“ an, die nach diesem Wert gruppiert sind. Viele Benutzer können ein SAN gemeinsam nutzen (z. B. ein großer ISP oder ein VPN-Ausgang eines Unternehmens). Stimmen Sie daher die Grenzwerte sorgfältig ab und überwachen Sie die CDN-Protokolle auf falsch positive Ergebnisse.

```yaml
kind: "CDN"
version: "1"
data:
  requestTransformations:
    rules:
      - name: log-on-request
        when: "*"
        actions:
          - type: set
            logProperty: client_as_name
            value:
              reqProperty: clientAsName
  trafficFilters:
    rules:
    - name: limit-requests-client-as-name
      when:
        reqProperty: tier
        matches: "author|publish"
      rateLimit:
        limit: 60
        window: 10
        penalty: 300
        count: all
        groupBy:
          - reqProperty: clientAsName
      action: block
```
