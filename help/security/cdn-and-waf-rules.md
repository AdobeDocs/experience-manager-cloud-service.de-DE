---
title: Konfigurieren von CDN- und WAF-Regeln zum Filtern des Traffics
description: Verwenden der Firewall-Regeln CDN und Web Application , um bösartigen Traffic zu filtern
source-git-commit: 27165ce7d6259f5b5fc9915349d87f551076389e
workflow-type: tm+mt
source-wordcount: '2391'
ht-degree: 2%

---


# Konfigurieren von CDN- und WAF-Regeln zum Filtern des Traffics {#configuring-cdn-and-waf-rules-to-filter-traffic}

>[!NOTE]
>
>Diese Funktion ist noch nicht allgemein verfügbar. Um dem laufenden Programm für frühe Nutzer beizutreten, senden Sie eine E-Mail **aemcs-waf-adopter@adobe.com**, einschließlich des Namens Ihrer Organisation und des Kontexts, in dem Sie an der Funktion interessiert sind.

Adobe versucht, Angriffe auf Kunden-Websites zu vermeiden. Es kann jedoch nützlich sein, Anfragen, die bestimmten Mustern entsprechen, proaktiv zu filtern, sodass böswilliger Traffic Ihre Anwendung nicht erreicht. Mögliche Ansätze sind:

* Apache-Ebenenmodule wie `mod_security`
* Konfigurieren von Regeln, die über die Cloud Manager-Konfigurationspipeline im CDN bereitgestellt werden.

In diesem Artikel wird der letztgenannte Ansatz beschrieben, der zwei Kategorien von Regeln vorsieht:

1. **CDN-Regeln**: blockiert oder lässt Anfragen basierend auf Anforderungseigenschaften und Anforderungsheadern zu, einschließlich IP, Pfaden und Benutzeragent. Diese Regeln können von allen AEM as a Cloud Service Kunden konfiguriert werden
1. **WAF** (Web Application Firewall)-Regeln: blockieren Anforderungen, die verschiedenen Mustern entsprechen, von denen bekannt ist, dass sie mit böswilligem Traffic verbunden sind. Diese Regeln können von Kunden konfiguriert werden, die das WAF-Add-on lizenzieren. Weitere Informationen erhalten Sie von Ihrem Adobe-Account-Team. Beachten Sie, dass während des Programms für frühe Anwender keine zusätzliche Lizenz erforderlich ist.

Diese Regeln können für Entwicklungs-, Staging- und Produktions-Cloud-Umgebungstypen bereitgestellt werden, und zwar für Produktionsprogramme (ohne Sandbox). Unterstützung für RDE-Umgebungen wird in Zukunft verfügbar sein.

## Einrichtung {#setup}

1. Erstellen Sie zunächst den folgenden Ordner und die Dateistruktur des Ordners der obersten Ebene in Git:

   ```
   config/
        cdn/
           cdn.yaml
           _config.yaml
   ```

1. `_config.yaml` beschreibt einige Metadaten zur Konfiguration. Der Parameter &quot;type&quot;sollte auf &quot;CDN&quot;gesetzt werden und die Version sollte auf die Schemaversion festgelegt werden, die derzeit &quot;1&quot;ist. Siehe unten stehendes Snippet:

   ```
   kind: "CDN"
   version: "1"
   ```

   <!-- Two properties -- `envType` and `envId` -- may be included to limit the scope of the rules. The envType property may have values "dev", "stage", or "prod", while the envId property is the environment (e.g., "53245"). This approach is useful if it is desired to have a single configuration pipeline, even if some environments have different rules. However, a different approach could be to have multiple configuration pipelines, each pointing to different repositories or git branches. -->

1. `cdn.yaml` sollte eine Liste der CDN-Regeln und WAF-Regeln enthalten, wie in den folgenden Abschnitten beschrieben.
1. Um den WAF-Regeln zu entsprechen, muss WAF in Cloud Manager aktiviert werden, wie unten für die neuen und bestehenden Programmszenarien beschrieben. Beachten Sie, dass eine separate Lizenz für WAF erworben werden muss.

   1. Um WAF für ein neues Programm zu konfigurieren, überprüfen Sie die **WAF-DDOS-Schutz** Kontrollkästchen im **Sicherheit** wie unten dargestellt. Fahren Sie mit den Schritten fort, die unter [Hinzufügen von Produktionsprogrammen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) zum Erstellen Ihres Programms

   1. Um WAF für ein vorhandenes Programm zu konfigurieren, wählen Sie die **Programm bearbeiten** , indem Sie die im Abschnitt [Bearbeiten von Programmen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md) Dokumentation. Dann in der **Sicherheit** im Assistenten, können Sie die WAF-DDOS-Option jederzeit deaktivieren oder aktivieren

1. Führen Sie für andere Umgebungstypen als RDE die Cloud Manager-Konfigurationspipeline aus, die wie unten beschrieben konfiguriert werden kann.

   1. Wählen Sie auf der Pipeline-Karte auf Ihrer Cloud Manager-Startseite die Option **Produktions-Pipeline hinzufügen** oder **Hinzufügen einer produktionsfremden Pipeline** Starten des Assistenten zum Hinzufügen der Pipeline
   1. Auswählen **Bereitstellungs-Pipeline** im Tab Konfiguration

      ![Wählen Sie die Option Bereitstellungs-Pipeline .](/help/security/assets/deployment.png)

   1. Benennen Sie die Pipeline und wählen Sie Bereitstellungs-Trigger aus. Wählen Sie dann **Weiter**
   1. Im **Quellcode** Registerkarte auswählen **Zielgerichtete Implementierung**, wählen Sie **Konfiguration**

      ![Targeting-Bereitstellung auswählen](/help/security/assets/target-deployment.png)

   1. Wählen Sie das Repository und die Verzweigung nach Bedarf aus. Wenn für die ausgewählte Umgebung eine Config-Pipeline vorhanden ist, ist diese Auswahl deaktiviert.

      ![Übersicht über eine Konfigurations-Pipeline](/help/security/assets/config-pipeline.png)

      >[!NOTE]
      >
      >Sie können nur eine Config-Pipeline pro Umgebung konfigurieren und ausführen.

   1. Wählen Sie **Speichern** aus. Ihre neue Pipeline wird auf der Pipeline-Karte angezeigt und kann ausgeführt werden, wenn Sie bereit sind.
   1. Für RDE wird die Befehlszeile verwendet, RDE wird jedoch derzeit nicht unterstützt.

## Regelsyntax {#rules-syntax}

Das Format der Regeln wird unten beschrieben, gefolgt von einigen Beispielen in einem nachfolgenden Abschnitt.

| **Eigenschaft** | **CDN-Regeln** | **WAF-Regeln** | **Typ** | **Standardwert** | **Beschreibung** |
|---|---|---|---|---|---|
| name | X | X | `string` | - | Regelname (64 Zeichen lang, darf nur alphanumerische Zeichen und - enthalten.) |
| when | X | X | `Condition` | - | Die Grundstruktur lautet:<br><br>`{ <getter>: <value>, <predicate>: <value> }`<br><br>Siehe Syntax für Bedingungsstruktur unten, in der die Getter, Eigenschaften und die Kombination mehrerer Bedingungen beschrieben werden. |
| Aktion | X | X | `Enum` | log (CDN-Regeln) | Für CDN-Regeln: allow, block, log. Die Standardeinstellung ist log.<br><br>Für WAF-Regeln: `enableWafRules`, `disableWafRules`, log. Kein Standardwert. |
| rateLimit | X |   | `RateLimit` | nicht definiert | Ratenbegrenzungskonfiguration. Die Ratenbegrenzung ist deaktiviert, wenn sie nicht definiert ist.<br><br>Weiter unten finden Sie einen separaten Abschnitt mit einer Beschreibung der Syntax rateLimit sowie Beispiele. |
| wafRules |   | X | `array[Enum]` | - | Liste der WAF-Regeln, die aktiviert oder deaktiviert werden sollen.<br><br>Beispiele sind SQLI und XSS. Eine vollständige Liste finden Sie unten unter Liste der waf-Regeln . |

### Bedingungsstruktur {#condition-structure}

Eine Bedingung kann entweder eine einfache Bedingung oder eine Gruppe von Bedingungen sein.

**Einfache Bedingung**

Eine einfache Bedingung besteht aus einem Getter und einem Prädikat.

```
{ <getter>: <value>, <predicate>: <value> }
```

**Gruppenbedingungen**

Eine Gruppe von Bedingungen besteht aus mehreren einfachen und/oder Gruppenbedingungen.

```
<allOf|anyOf>:
  - { <getter>: <value>, <predicate>: <value> }
  - { <getter>: <value>, <predicate>: <value> }
  - <allOf|anyOf>:
    - { <getter>: <value>, <predicate>: <value> }
```

| **Eigenschaft** | **Typ** | **Beschreibung** |
|---|---|---|
| **allOf** | `array[Condition]` | **und** Vorgang. true , wenn alle aufgelisteten Bedingungen &quot;true&quot;zurückgeben |
| **anyOf** | `array[Condition]` | **oder** Vorgang. true , wenn eine der aufgelisteten Bedingungen &quot;true&quot;zurückgibt |

**Getter**

| **Eigenschaft** | **Typ** | **Beschreibung** |
|---|---|---|
| reqProperty | `string` | Anfrageeigenschaft.<br><br>Eines von: `path` , `queryString`, `method`, `tier`, `domain`, `clientIp`, `clientCountry`<br><br>Die Domain-Eigenschaft ist eine Transformation der Host-Kopfzeile der Anfrage in Kleinbuchstaben. Dies ist für Zeichenfolgenvergleiche nützlich, sodass Übereinstimmungen aufgrund der Groß-/Kleinschreibung nicht übersehen werden.<br><br>Die `clientCountry` verwendet zwei Buchstaben-Codes, die unter [https://en.wikipedia.org/wiki/Regional_indicator_symbol](https://en.wikipedia.org/wiki/Regional_indicator_symbol) |
| reqHeader | `string` | Gibt den Anforderungsheader mit dem angegebenen Namen zurück |
| queryParam | `string` | Gibt Abfrageparameter mit dem angegebenen Namen zurück |
| Cookie | `string` | Gibt Cookie mit dem angegebenen Namen zurück |

**Prädikat**

| **Eigenschaft** | **Typ** | **Beschreibung** |
|---|---|---|
| **gleich** | `string` | true , wenn das Getter-Ergebnis dem bereitgestellten Wert entspricht |
| **doesNotEqual** | `string` | true , wenn das Getter-Ergebnis nicht dem bereitgestellten Wert entspricht |
| **Gefällt mir** | `string` | true , wenn das Getter-Ergebnis dem angegebenen Muster entspricht |
| **notLike** | `string` | true , wenn das Getter-Ergebnis nicht mit dem bereitgestellten Muster übereinstimmt |
| **Stimmt überein** | `string` | true , wenn das Getter-Ergebnis mit bereitgestelltem Regex übereinstimmt |
| **doesNotMatch** | `string` | true , wenn das Getter-Ergebnis nicht mit dem bereitgestellten Regex übereinstimmt |
| **in** | `array[string]` | true , wenn die bereitgestellte Liste das Getter-Ergebnis enthält |
| **notIn** | `array[string]` | true , wenn die bereitgestellte Liste kein Getter-Ergebnis enthält |

**wafRules List**

Die `wafRules` -Eigenschaft kann die folgenden Regeln umfassen:

| **Regel-ID** | **Regelname** | **Beschreibung** |
|---|---|---|
| SQLI | SQL-Injektion | SQL Injection ist der Versuch, durch die Ausführung beliebiger Datenbankabfragen Zugriff auf eine Anwendung zu erhalten oder privilegierte Informationen zu erhalten. |
| HINTERGRUND | Backend | Ein Backdoor-Signal ist eine Anfrage, die versucht festzustellen, ob eine gemeinsame Backdoor-Datei auf dem System vorhanden ist. |
| CMDEXE | Befehlsausführung | Befehlsausführung ist der Versuch, durch beliebige Systembefehle mithilfe von Benutzereingaben die Kontrolle über ein Zielsystem zu erlangen oder ein Zielsystem zu beschädigen. |
| XSS | Site-übergreifende Skripterstellung | Die Site-übergreifende Skripterstellung ist der Versuch, das Konto eines Benutzers oder die Webbrowsing-Sitzung durch schädlichen JavaScript-Code zu ersetzen. |
| TRAVERSAL | Verzeichnisdurchlauf | Directory Traversal ist der Versuch, in einem System durch privilegierte Ordner zu navigieren, in der Hoffnung, vertrauliche Informationen zu erhalten. |
| BENUTZERAGENT | Attack-Tools | Attack Tooling ist der Einsatz automatisierter Software zur Identifizierung von Sicherheitslücken oder zum Versuch, eine entdeckte Verwundbarkeit auszunutzen. |
| LOG4J-JNDI | Log4J JNDI | Log4J JNDI-Angriffe versuchen, die [Sicherheitslücke durch Log4Shell](https://en.wikipedia.org/wiki/Log4Shell) in Log4J-Versionen vor 2.16.0 vorhanden |
| AWS SSRF | AWS-SSRF | Server Side Request Forgery (SSRF) ist eine Anfrage, die versucht, von der Webanwendung gestellte Anforderungen an interne Systeme zu senden. AWS SSRF-Angriffe nutzen SSRF, um Amazon Web Services (AWS)-Schlüssel zu erhalten und Zugriff auf S3-Buckets und deren Daten zu erhalten. |
| BHH | Bad Hop Headers | Bad Hop-Header weisen auf einen HTTP-Schmuggelversuch durch einen fehlerhaften Transfer-Encoding (TE)- oder Content-Length (CL)-Header oder einen korrekt formatierten TE- und CL-Header hin. |
| ABNORMALPATH | Anormaler Pfad | Anormaler Pfad gibt an, dass der ursprüngliche Pfad vom normalisierten Pfad abweicht (z. B. `/foo/./bar` wird normalisiert in `/foo/bar`) |
| KOMPRIMIERT | Komprimierung erkannt | Der Hauptteil der POST-Anforderung ist komprimiert und kann nicht überprüft werden. Wenn beispielsweise ein Anforderungsheader &quot;Content-Encoding: gzip&quot;angegeben ist und der POST-Textkörper kein Normaltext ist. |
| DOUBLEENCODE | Doppelte Kodierung | Bei der doppelten Kodierung wird geprüft, ob HTML-Zeichen doppelt kodiert werden |
| FORCEFULBROWSING | Erzwungenes Browsen | Beim erzwungenen Browsen wird nicht versucht, auf Admin-Seiten zuzugreifen. |
| NOTUTF8 | Ungültige Kodierung | Eine ungültige Kodierung kann dazu führen, dass der Server böswillige Zeichen aus einer Anfrage in eine Antwort übersetzt, was entweder zu einer Dienstverweigerung oder XSS führt |
| JSON-FEHLER | JSON-Kodierungsfehler | Ein POST-, PUT- oder PATCH-Anforderungstext, der als JSON-Inhalt im Anforderungsheader &quot;Content-Type&quot;enthält, aber JSON-Parsing-Fehler enthält. Dies hängt häufig mit einem Programmierfehler oder einer automatisierten oder böswilligen Anfrage zusammen. |
| MALFORMED-DATA | Fehlerhafte Daten im Anfrageinhalt | Ein POST-, PUT- oder PATCH-Anfrageinhalt, der gemäß der Anfragekopfzeile &quot;Content-Type&quot;fehlerhaft ist. Wenn beispielsweise ein Anforderungsheader &quot;Content-Type: application/x-www-form-urlencoded&quot;angegeben ist und einen POST-Hauptteil enthält, der json ist. Dies ist häufig ein Programmierfehler, eine automatisierte oder böswillige Anfrage. Erfordert Agent 3.2 oder höher. |
| SANS | böswilliger IP-Traffic | [SANS Internet Storm Center](https://isc.sans.edu/) Liste der IP-Adressen, von denen berichtet wurde, dass sie schädliche Aktivitäten durchgeführt haben |
| SIGSCI-IP | Netzwerkeffekt | IP-Adresse, die von SignalSciences gekennzeichnet wird: Jedes Mal, wenn eine IP aufgrund eines bösartigen Signals von der Entscheidungs-Engine gekennzeichnet wird, wird diese IP an alle Kunden weitergeleitet. Nachfolgende Anfragen von den IP-Adressen, die ein zusätzliches Signal für die Dauer der Markierung enthalten, werden dann protokolliert |
| NO-CONTENT-TYPE | Fehlende Anfrage-Kopfzeile &quot;Content-Type&quot; | Eine Anfrage vom Typ POST, PUT oder PATCH, die keinen Anforderungsheader vom Typ &quot;Content-Type&quot;enthält. Standardmäßig sollten Anwendungsserver in diesem Fall von &quot;Content-Type: text/plain; charset=us-ascii&quot;ausgehen. Bei vielen automatisierten und böswilligen Anfragen fehlt möglicherweise &quot;Content Type&quot;. |
| NOUA | Kein Benutzeragent | Viele automatisierte und böswillige Anfragen verwenden gefälschte oder fehlende Benutzeragenten, um die Identifizierung des Gerätetyps zu erschweren, der die Anforderungen stellt. |
| TORNODE | Tor Traffic | Tor ist eine Software, die die Identität eines Benutzers verschleiert. Eine Spitze im Tor-Traffic kann darauf hinweisen, dass ein Angreifer versucht, seinen Standort zu verschleiern. |
| DATENZENTRUM | Datenverkehr in Rechenzentren | Datenzentrum-Traffic ist nicht organischer Traffic, der von identifizierten Hosting-Anbietern stammt. Diese Art von Traffic wird normalerweise nicht mit einem echten Endbenutzer verknüpft. |
| NULLBYTE | Null Byte | Null-Bytes werden normalerweise nicht in einer Anfrage angezeigt und weisen darauf hin, dass die Anfrage falsch formatiert ist und möglicherweise bösartig ist. |
| IMPOSTOR | SearchBot-Impostor | Suchbot-Impostor ist jemand, der vorgibt, ein Google- oder Bing-Suchbot zu sein, aber nicht legitim ist. Beachten Sie, dass nicht von einer Antwort allein abhängt, sondern zuerst in der Cloud aufgelöst werden muss. Daher sollte sie nicht in einer Vorregel verwendet werden. |
| PRIVATEFILE | Private Dateien | Private Dateien sind normalerweise vertraulich, wie z. B. ein Apache `.htaccess` -Datei oder einer Konfigurationsdatei, die vertrauliche Informationen übergeben kann |
| SCANNER | Scanner | Identifiziert beliebte Scandienste und -werkzeuge |
| RESPONSESPLIT | HTTP-Antwortaufteilung | Gibt an, wann CRLF-Zeichen als Eingabe an die Anwendung gesendet werden, um Header in die HTTP-Antwort einzufügen. |
| XML-FEHLER | XML-Kodierungsfehler | Ein POST-, PUT- oder PATCH-Anfrageinhalt, der im Anfrageheader &quot;Content-Type&quot;als XML-Inhalt mit XML-Parsing-Fehlern angegeben ist. Dies hängt häufig mit einem Programmierfehler oder einer automatisierten oder böswilligen Anfrage zusammen. |

## Überlegungen {#considerations}

* Wenn zwei in Konflikt stehende Regeln erstellt werden, haben die Zulassungsregeln immer Vorrang vor den Blockregeln. Wenn Sie beispielsweise eine Regel erstellen, die einen bestimmten Pfad blockiert, und eine Regel, die eine bestimmte IP-Adresse zulässt, sind Anforderungen von dieser IP-Adresse auf dem blockierten Pfad zulässig.

* Wenn eine Regel abgeglichen und blockiert wird, antwortet das CDN mit einer `406` Rückgabe-Code.

## Beispiele {#examples}

Es folgen einige Regelbeispiele. Siehe [Ratenbegrenzungsabschnitt](#rules-with-rate-limits) weiter unten für Beispiele für die Ratenbegrenzung.

**Beispiel 1**

Diese Regel blockiert Anforderungen aus IP 192.168.1.1:

```
data:
  rules:
    - name: "block-request-from-ip"
      when: { reqProperty: clientIp, equals: "192.168.1.1" }
      action: block
```

**Beispiel 2**

Diese Regel blockiert Anforderungen für den Pfad `/helloworld` bei Veröffentlichung mit einem Benutzeragenten, der Chrome enthält:

```
data:
  rules:
    - name: "block-request-from-chrome-on-path-helloworld-for-publish-tier"
      when:
        allOf:
          - { reqProperty: path, equals: /helloworld }
          - { reqProperty: tier, equals: publish }
          - { reqHeader: user-agent, matches: '.*Chrome.*'  }
      action: block
```

**Beispiel 3**

Diese Regel blockiert Anforderungen, die den Abfrageparameter enthalten `foo`, aber erlaubt jede Anfrage von IP 192.168.1.1:

```
data:
  rules:
    - name: "block-request-that-contains-query-parameter-foo"
      when: { queryParam: url-param, equals: foo }
      action: block
    - name: "allow-all-requests-from-ip"
      when: { reqProperty: clientIp, equals: 192.168.1.1 }
      action: allow
```

**Beispiel 4**

Diese Regel blockiert Anforderungen an den Pfad /block-me und blockiert alle Anforderungen, die mit einem SQLI- oder XSS-Muster übereinstimmen:

```
data:
  rules:
    - name: "path-rule"
      when: { reqProperty: path, equals: /block-me }
      action: block

    - name: "Enable-SQL-Injection-and-XSS-waf-rules-globally"
      when: { reqProperty: path, like: "*" }
      action: enableWafRules
      wafRules:
        - SQLI
        - XSS
```

## Regeln mit Ratenbeschränkungen {#rules-with-rate-limits}

Manchmal ist es wünschenswert, Traffic, der mit einer Regel übereinstimmt, nur zu blockieren, wenn die Übereinstimmung eine bestimmte Rate im Zeitverlauf überschreitet. Festlegen eines Werts für `rateLimit` -Eigenschaft begrenzt die Rate der Anforderungen, die mit der Regelbedingung übereinstimmen.

### rateLimit-Struktur {#ratelimit-structure}

| **Eigenschaft** | **Typ** | **Standardwert** | **Beschreibung** |
|---|---|---|---|
| limit | Ganzzahl von 10 bis 10000 | erforderlich | Anforderungsrate in Anforderungen pro Sekunde, für die die Regel ausgelöst wird |
| window | Ganzzahl-Enum: 1, 10 oder 60 | 10 | Sampling-Fenster in Sekunden, für die die Anforderungsrate berechnet wird |
| Sanktion | Ganzzahl von 60 bis 3600 | 300 (5 Minuten) | Ein Zeitraum in Sekunden, für den übereinstimmende Anforderungen blockiert werden (auf die nächste Minute gerundet) |

### Beispiele {#ratelimiting-examples}

Beispiel 1: Wenn die Anforderungsrate in den letzten 60 Sekunden 100 Anforderungen pro Sekunde überschreitet, blockieren Sie den `/critical/resource` für 60 Sekunden

```
- name: rate-limit-example
  when: { reqProperty: path, equals: /critical/resource }
  action: block
  rateLimit: { limit: 100, window: 60, penalty: 60 }
```

Beispiel 2: Wenn die Anforderungsrate 10 Anforderungen pro Sekunde in 10 Sekunden überschreitet, blockieren Sie die Ressource für 300 Sekunden:

```
- name: rate-limit-using-defaults
  when: { reqProperty: path, equals: /critical/resource }
  action: block
  rateLimit:
    limit: 10
```

## CDN-Protokolle {#cdn-logs}

AEM as a Cloud Service bietet Zugriff auf CDN-Protokolle, die für Anwendungsfälle nützlich sind, einschließlich der Optimierung der Cache-Trefferquote und der Konfiguration von CDN- und WAF-Regeln. CDN-Protokolle werden in Cloud Manager angezeigt **Protokolle herunterladen** angezeigt, wenn Sie den Autoren- oder Veröffentlichungsdienst auswählen.

Der Name der Regel wird in der Regeleigenschaft angezeigt, wenn die Anfrage mit der Regel übereinstimmt, auch wenn die Aktion &quot;allow&quot;ist und der Traffic daher nicht blockiert wird.

Übereinstimmende CDN-Regeln werden im Protokolleintrag für alle Anfragen an das CDN angezeigt, unabhängig davon, ob es sich um einen CDN-Treffer, einen CDN-Treffer, einen Pass- oder einen Fehler handelt. WAF-Regeln werden jedoch nur für Anfragen an das CDN im Protokolleintrag angezeigt, die als CDN-Fehlschläge oder -Übermittlungen gelten, nicht aber für CDN-Treffer.

Das folgende Beispiel zeigt ein Beispiel `cdn.yaml` und zwei CDN-Protokolleinträgen mit nicht leeren Werten in der Regeleigenschaft aufgrund von blockierten Anforderungen, die mit der CDN-Regel bzw. der WAF-Regel übereinstimmen.


```
data:
  rules:
    - name: "path-rule"
      when: { reqProperty: path, equals: /block-me }
      action: block

    - name: "Enable-SQL-Injection-and-XSS-waf-rules-globally"
      when: { reqProperty: path, like: "*" }
      action: enableWafRules
      wafRules:
        - SQLI
        - XSS
```

```
{
"timestamp": "2023-05-26T09:20:01+0000",
"ttfb": 19,
"cli_ip": "147.160.230.112",
"cli_country": "CH",
"rid": "974e67f6",
"req_ua": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/14.0.3 Safari/605.1.15",
"host": "example.com",
"url": "/block-me",
"method": "GET",
"res_ctype": "",
"cache": "PASS",
"status": 406,
"res_age": 0,
"pop": "PAR",
"rules": "cdn=path-rule;waf=;action=blocked"
}
```

```
{
"timestamp": "2023-05-26T09:20:01+0000",
"ttfb": 19,
"cli_ip": "147.160.230.112",
"cli_country": "CH",
"req_ua": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/14.0.3 Safari/605.1.15",
"rid": "974e67f6",
"host": "example.com",
"url": "/?sqli=%27%29%20UNION%20ALL%20SELECT%20NULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL--%20fAPK",
"method": "GET",
"res_ctype": "image/png",
"cache": "PASS",
"status": 406,
"res_age": 0,
"pop": "PAR",
"rules": "cdn=;waf=SQLI;action=blocked"
}
```

### Protokollformat {#cdn-log-format}

Nachfolgend finden Sie eine Liste der in CDN-Protokollen verwendeten Feldnamen sowie eine kurze Beschreibung.

| **Feldname** | **Beschreibung** |
|---|---|
| *timestamp* | Der Zeitpunkt, zu dem die Anfrage nach TLS-Beendigung gestartet wurde |
| *ttfb* | Abkürzung für *Zeit bis zum ersten Byte*. Das Zeitintervall zwischen der Anfrage begann bis zu dem Punkt, an dem der Antworttext mit dem Streaming begann. |
| *cli_ip* | Die Client-IP-Adresse. |
| *cli_country* | Zweibuchstaben [ISO 3166-1](https://de.wikipedia.org/wiki/ISO_3166-1) Alpha-2-Ländercode für das Client-Land. |
| *rid* | Der -Wert des Anforderungsheaders, der zur eindeutigen Identifizierung der Anfrage verwendet wird. |
| *req_ua* | Der Benutzeragent, der für die Ausführung einer bestimmten HTTP-Anforderung verantwortlich ist. |
| *host* | Die Behörde, für die der Antrag bestimmt ist. |
| *url* | Der vollständige Pfad, einschließlich Abfrageparametern. |
| *method* | Vom Client gesendete HTTP-Methode, z. B. &quot;GET&quot;oder &quot;POST&quot;. |
| *res_ctype* | Der Content-Type, der den ursprünglichen Medientyp der Ressource angibt. |
| *cache* | Status des Caches. Mögliche Werte sind HIT, MISS oder PASS |
| *status* | Der HTTP-Statuscode als ganzzahliger Wert. |
| *res_age* | Die Zeit (in Sekunden), die eine Antwort zwischengespeichert wurde (in allen Knoten). |
| *pop* | Rechenzentrum des CDN-Cache-Servers |
| *Regeln* | Der Name aller übereinstimmenden Regeln, sowohl für CDN-Regeln als auch für WAF-Regeln.<br><br>Übereinstimmende CDN-Regeln werden im Protokolleintrag für alle Anfragen an das CDN angezeigt, unabhängig davon, ob es sich um einen CDN-Treffer, einen CDN-Treffer, einen Pass- oder einen Fehler handelt.<br><br>Gibt auch an, ob die Übereinstimmung zu einem Block führte. <br><br>Beispiel: &quot;`cdn=;waf=SQLI;action=blocked`&quot;<br><br>Leer, wenn keine Regeln übereinstimmten. |
