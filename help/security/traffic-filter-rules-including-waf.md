---
title: Traffic-Filterregeln, einschließlich WAF-Regeln
description: Konfigurieren von Traffic-Filterregeln einschließlich Web Application Firewall (WAF)-Regeln
exl-id: 6a0248ad-1dee-4a3c-91e4-ddbabb28645c
source-git-commit: 221f6df73fe660c6f8dbf79affdccdd081ad3906
workflow-type: tm+mt
source-wordcount: '4210'
ht-degree: 1%

---


# Traffic-Filterregeln, einschließlich WAF-Regeln {#traffic-filter-rules-including-waf-rules}

>[!NOTE]
>
>Diese Funktion ist noch nicht allgemein verfügbar. Um dem laufenden Programm für frühe Nutzer beizutreten, senden Sie eine E-Mail **aemcs-waf-adopter@adobe.com**, einschließlich des Namens Ihrer Organisation und des Kontexts, in dem Sie an der Funktion interessiert sind.

Traffic-Filterregeln können verwendet werden, um Anforderungen auf der CDN-Ebene zu blockieren oder zuzulassen. Dies kann in Szenarien wie den folgenden nützlich sein:

* Einschränken des Zugriffs auf bestimmte Domänen auf den internen Unternehmensdatenverkehr, bevor eine neue Site live geschaltet wird
* Festlegung von Ratenbeschränkungen, um weniger anfällig für volumetrische DDoS-Angriffe zu sein
* Verhindern von IP-Adressen, von denen bekannt ist, dass sie bösartig auf Seiten sind

Einige dieser Traffic-Filterregeln stehen allen AEM as a Cloud Service Sites- und Forms-Kunden zur Verfügung. Sie funktionieren hauptsächlich mit Anforderungseigenschaften und Anforderungsheadern, einschließlich IP, Hostname, Pfad und Benutzeragent.

Eine Unterkategorie von Traffic-Filterregeln erfordert entweder eine Lizenz für Enhanced Security oder eine Lizenz für WAF-DDoS Protection Security. Diese leistungsstarken Regeln werden als Traffic-Filterregeln für WAF (Web Application Firewall) (kurz WAF-Regeln) bezeichnet und haben Zugriff auf die [WAF-Flags](#waf-flags-list) weiter unten in diesem Artikel beschrieben. Sites- und Forms-Kunden können sich an ihr Adobe-Account-Team wenden, um mehr über die Lizenzierung dieser erweiterten Funktion zu erfahren.

Traffic-Filterregeln können über Cloud Manager-Konfigurations-Pipelines bereitgestellt werden, um Typen von Entwicklungs-, Staging- und Produktionsumgebungen in Produktionsprogrammen (ohne Sandbox) bereitzustellen. Die Unterstützung von RDEs wird in Zukunft stattfinden.

## Organisation dieses Artikels {#how-organized}

Dieser Artikel ist in die folgenden Abschnitte unterteilt:

* **Übersicht über den Traffic-Schutz:** Erfahren Sie, wie Sie vor schädlichem Traffic geschützt sind.
* **Empfohlener Prozess zum Konfigurieren von Regeln:** Erfahren Sie mehr über eine allgemeine Methode zum Schutz Ihrer Website.
* **Einrichtung:** Erfahren Sie, wie Sie Traffic-Filterregeln einrichten, konfigurieren und bereitstellen, einschließlich der erweiterten WAF-Regeln.
* **Regelsyntax:** Erfahren Sie, wie Sie Traffic-Filterregeln deklarieren im `cdn.yaml` Konfigurationsdatei. Dazu gehören sowohl die Traffic-Filterregeln, die für alle Sites- und Forms-Kunden verfügbar sind, als auch die Unterkategorie der WAF-Regeln für diejenigen, die diese Funktion lizenzieren.
* **Regelbeispiele:** Sehen Sie sich Beispiele für deklarierte Regeln an, um Sie auf den Weg zu bringen.
* **Regeln für die Begrenzung von Beträgen:** Erfahren Sie, wie Sie Regeln zur Ratenbegrenzung verwenden, um Ihre Site vor Angriffen mit hohem Volumen zu schützen.
* **CDN-Protokolle:** Erfahren Sie, welche deklarierten Regeln und WAF-Flags mit Ihrem Traffic übereinstimmen.
* **Dashboard-Tooling:** Analysieren Sie Ihre CDN-Protokolle, um neue Traffic-Filterregeln zu erstellen.
* **Tutorial:** Praktische Kenntnisse über die Funktion, einschließlich der Verwendung der Dashboard-Werkzeuge zur Deklarierung der richtigen Regeln.
<!-- About the tutorial: sets the context for a linked tutorial, which gives you practical knowledge about the feature, including how to use dashboard tooling to declare the right rules. -->

## Traffic Protection - Übersicht {#traffic-protection-overview}

In der aktuellen digitalen Landschaft stellt böswilliger Traffic eine immer präsente Bedrohung dar. Wir erkennen die Schwere des Risikos und bieten verschiedene Ansätze zum Schutz von Kundenanwendungen und zur Eindämmung von Angriffen, wenn diese auftreten.

Am Rande absorbiert das von Adobe verwaltete CDN DDoS-Angriffe auf der Netzwerkschicht (Ebenen 3 und 4), einschließlich Überschwemmungen und Reflektions-/Verstärkungsangriffe.

Adobe ergreift standardmäßig Maßnahmen, um eine Leistungsbeeinträchtigung durch unerwartet hohen Traffic-Aufkommen über einen bestimmten Schwellenwert hinaus zu verhindern. Wenn sich ein DDoS auf die Verfügbarkeit der Website auswirkt, werden die Teams von Adobe-Angriffen benachrichtigt und ergreifen Maßnahmen, um diese zu verringern.

Kunden können proaktive Maßnahmen ergreifen, um Anwendungsschichtangriffe (Ebene 7) zu minimieren, indem sie Regeln auf verschiedenen Ebenen des Inhaltsbereitstellungsflusses konfigurieren.

Auf der Apache-Ebene können Kunden beispielsweise die [Dispatcher-Modul](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=en#configuring-access-to-content-filter) oder [ModSecurity](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/modsecurity-crs-dos-attack-protection.html?lang=en) , um den Zugriff auf bestimmte Inhalte zu beschränken.

Wie in diesem Artikel beschrieben, können Traffic-Filterregeln mithilfe der Cloud Manager-Konfigurationspipeline im CDN bereitgestellt werden. Zusätzlich zu Traffic-Anforderungsbasierten Traffic-Filterregeln, die auf Eigenschaften wie IP-Adresse, Pfad und Kopfzeilen basieren, können Kunden auch eine leistungsstarke Unterkategorie von Traffic-Filterregeln lizenzieren, die als WAF-Regeln bezeichnet werden.

## Vorgeschlagener Prozess {#suggested-process}

Im Folgenden finden Sie einen allgemeinen empfohlenen End-to-End-Prozess für die Erstellung der richtigen Traffic-Filterregeln:

1. Konfigurieren Sie eine Konfigurations-Pipeline für Nicht-Produktion und Produktion, wie im Abschnitt [Einrichtung](#setup) Abschnitt.
1. Kunden, die die Unterkategorie der WAF-Traffic-Filterregeln lizenziert haben, sollten sie in Cloud Manager aktivieren.
1. Lesen und probieren Sie das Tutorial aus, um genau zu verstehen, wie Traffic-Filterregeln verwendet werden, einschließlich WAF-Regeln, wenn sie lizenziert wurden. Das Tutorial führt Sie durch die Bereitstellung von Regeln in einer Entwicklungsumgebung, die Simulation von schädlichem Traffic und den Download der [CDN-Protokolle](#cdn-logs)und analysieren sie in [Dashboard-Tools](#dashboard-tooling).
1. Kopieren Sie die empfohlenen anfänglichen Regeln in `cdn.yaml` und stellen Sie die Konfiguration im Protokollmodus für die Produktion bereit.
1. Nachdem Sie Traffic erfasst haben, analysieren Sie die Ergebnisse mit [Dashboard-Tools](#dashboard-tooling) um zu sehen, ob es Übereinstimmungen gab. Suchen Sie nach Falsch-Positiv-Werten und nehmen Sie die erforderlichen Anpassungen vor, um schließlich die Standardregeln im Blockmodus zu aktivieren.
1. Fügen Sie benutzerdefinierte Regeln hinzu, die auf der Analyse der CDN-Protokolle basieren, testen Sie zunächst mit simuliertem Traffic in Entwicklungsumgebungen, bevor Sie sie in der Staging- und Produktionsumgebung im Protokollmodus bereitstellen, und blockieren Sie dann den Modus.
1. Überwachung des Traffics auf fortlaufender Basis, Anpassung der Regeln im Zuge der Entwicklung der Bedrohungslandschaft.

## Setup {#setup}

1. Erstellen Sie zunächst den folgenden Ordner und die Dateistruktur des Ordners der obersten Ebene in Ihrem Projekt in Git:

   ```
   config/
        cdn.yaml
   ```

1. `cdn.yaml` sollte Metadaten sowie eine Liste von Traffic-Filterregeln und WAF-Regeln enthalten.

   ```
   kind: "CDN"
   version: "1"
   metadata:
     envTypes: ["dev"]
   data:
     trafficFilters:
       rules:
       # Block simple path
       - name: block-path
         when:
           allOf:
             - reqProperty: tier
               matches: "author|publish"
             - reqProperty: path
               equals: '/block/me'
         action: block
   ```

Die `kind` -Parameter auf `CDN` und die Version auf die Schemaversion eingestellt werden sollte, die derzeit `1`. Siehe Beispiele weiter unten.


<!-- Two properties -- `envType` and `envId` -- may be included to limit the scope of the rules. The envType property may have values "dev", "stage", or "prod", while the envId property is the environment (e.g., "53245"). This approach is useful if it is desired to have a single configuration pipeline, even if some environments have different rules. However, a different approach could be to have multiple configuration pipelines, each pointing to different repositories or git branches. -->

1. Um WAF-Regeln zu konfigurieren, muss WAF in Cloud Manager aktiviert werden, wie unten für die neuen und bestehenden Programmszenarien beschrieben. Beachten Sie, dass eine separate Lizenz für WAF erworben werden muss.

   1. Um WAF in einem neuen Programm zu konfigurieren, überprüfen Sie die **WAF-DDOS-Schutz** Kontrollkästchen auf der **Sicherheit** Registerkarte bei [ein Produktionsprogramm hinzufügen.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md)

   1. So konfigurieren Sie WAF für ein vorhandenes Programm: [Bearbeiten des Programms](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md) und auf **Sicherheit** Registerkarte deaktivieren oder überprüfen Sie **WAF-DDOS** jederzeit verfügbar.

1. Erstellen Sie für andere Umgebungstypen als RDE eine zielgerichtete Bereitstellungskonfigurations-Pipeline in Cloud Manager.

   * [Informationen zu Produktions-Pipelines finden Sie in diesem Dokument .](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md)
   * [Informationen zu produktionsfremden Pipelines finden Sie in diesem Dokument .](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md)

Für RDEs wird die Befehlszeile verwendet, RDE wird jedoch derzeit nicht unterstützt.

## Syntax für Traffic-Filterregeln {#rules-syntax}

Sie können `traffic filter rules` , um eine Übereinstimmung mit Mustern wie IPs, Benutzeragent, Anfragekopfzeilen, Hostname, Geo und URL zu erhalten.

Kunden, die das Angebot &quot;Enhanced Security&quot;oder &quot;WAF-DDoS Protection Security&quot;lizenzieren, können auch eine spezielle Kategorie von Traffic-Filterregeln konfigurieren, die als `WAF traffic filter rules` (oder WAF-Regeln für kurz), die auf eine oder mehrere [WAF-Flags](#waf-flags-list).

Im Folgenden finden Sie ein Beispiel für einen Satz von Traffic-Filterregeln, die auch eine WAF-Regel enthalten.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
      - name: "path-rule"
        when: { reqProperty: path, equals: /block-me }
        action:
          type: block
      - name: "Enable-SQL-Injection-and-XSS-waf-rules-globally"
        when: { reqProperty: path, like: "*" }
        action:
          type: block
          wafFlags: [ SQLI, XSS]
```

Das Format der Traffic-Filterregeln im `cdn.yaml` wird unten beschrieben. Siehe einige [andere Beispiele](#examples) in einem späteren Abschnitt sowie einem separaten Abschnitt zu [Regeln für Ratenbegrenzungen](#rate-limit-rules).


| **Eigenschaft** | **Die meisten Traffic-Filterregeln** | **WAF-Traffic-Filterregeln** | **Typ** | **Standardwert** | **Beschreibung** |
|---|---|---|---|---|---|
| name | X | X | `string` | - | Regelname (64 Zeichen lang, darf nur alphanumerische Zeichen und - enthalten.) |
| when | X | X | `Condition` | - | Die Grundstruktur lautet:<br><br>`{ <getter>: <value>, <predicate>: <value> }`<br><br>[Siehe Syntax für Bedingungsstruktur](#condition-structure) weiter unten, in dem die Getter, Eigenschaften und die Kombination mehrerer Bedingungen beschrieben werden. |
| Aktion | X | X | `Action` | log | log-, allow-, block-, log- oder action-Objekt Standard ist log |
| rateLimit | X |   | `RateLimit` | nicht definiert | Ratenbegrenzungskonfiguration. Die Ratenbegrenzung ist deaktiviert, wenn sie nicht definiert ist.<br><br>Weiter unten finden Sie einen separaten Abschnitt mit einer Beschreibung der Syntax rateLimit sowie Beispiele. |

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

| **Eigenschaft** | **Typ** | **Bedeutung** |
|---|---|---|
| **allOf** | `array[Condition]` | **und** Vorgang. true , wenn alle aufgelisteten Bedingungen &quot;true&quot;zurückgeben |
| **anyOf** | `array[Condition]` | **oder** Vorgang. true , wenn eine der aufgelisteten Bedingungen &quot;true&quot;zurückgibt |

**Getter**

| **Eigenschaft** | **Typ** | **Beschreibung** |
|---|---|---|
| reqProperty | `string` | Anfrageeigenschaft.<br><br>Eines von: `path` , `queryString`, `method`, `tier`, `domain`, `clientIp`, `clientCountry`<br><br>Die Domain-Eigenschaft ist eine Transformation der Host-Kopfzeile der Anfrage in Kleinbuchstaben. Dies ist für Zeichenfolgenvergleiche nützlich, sodass Übereinstimmungen aufgrund der Groß-/Kleinschreibung nicht übersehen werden.<br><br>Die `clientCountry` verwendet zwei Buchstaben-Codes, die unter [https://en.wikipedia.org/wiki/Regional_indicator_symbol](https://en.wikipedia.org/wiki/Regional_indicator_symbol) |
| reqHeader | `string` | Gibt den Anforderungsheader mit dem angegebenen Namen zurück |
| queryParam | `string` | Gibt Abfrageparameter mit dem angegebenen Namen zurück |
| reqCookie | `string` | Gibt Cookie mit dem angegebenen Namen zurück |
| postParam | `string` | Gibt den Parameter mit dem angegebenen Namen aus dem Hauptteil zurück. Nur funktionieren, wenn der Hauptteil vom Inhaltstyp ist `application/x-www-form-urlencoded` |

**Prädikat**

| **Eigenschaft** | **Typ** | **Bedeutung** |
|---|---|---|
| **gleich** | `string` | true , wenn das Getter-Ergebnis dem bereitgestellten Wert entspricht |
| **doesNotEqual** | `string` | true , wenn das Getter-Ergebnis nicht dem bereitgestellten Wert entspricht |
| **Gefällt mir** | `string` | true , wenn das Getter-Ergebnis dem angegebenen Muster entspricht |
| **notLike** | `string` | true , wenn das Getter-Ergebnis nicht mit dem bereitgestellten Muster übereinstimmt |
| **Stimmt überein** | `string` | true , wenn das Getter-Ergebnis mit bereitgestelltem Regex übereinstimmt |
| **doesNotMatch** | `string` | true , wenn das Getter-Ergebnis nicht mit dem bereitgestellten Regex übereinstimmt |
| **in** | `array[string]` | true , wenn die bereitgestellte Liste das Getter-Ergebnis enthält |
| **notIn** | `array[string]` | true , wenn die bereitgestellte Liste kein Getter-Ergebnis enthält |
| **vorhanden** | `boolean` | &quot;true&quot;, wenn auf &quot;true&quot;gesetzt und die Eigenschaft existiert oder auf &quot;false&quot;gesetzt ist und die Eigenschaft nicht vorhanden ist |

### Aktionsstruktur {#action-structure}

Wird durch `action` -Feld, das entweder eine Zeichenfolge sein kann, die den Aktionstyp (allow, block, log) angibt und Standardwerte für alle anderen Optionen übernimmt, oder ein Objekt, bei dem der Regeltyp über definiert wird `type` erforderliches Feld zusammen mit anderen für diesen Typ zutreffenden Optionen.

**Aktionstypen**

Aktionen werden entsprechend ihren Typen in der folgenden Tabelle priorisiert, die entsprechend der ausgeführten Bestellaktionen angeordnet ist:

| **Name** | **Zulässige Eigenschaften** | **Bedeutung** |
|---|---|---|
| **zulassen** | `wafFlags` (optional) | Wenn wafFlags nicht vorhanden ist, stoppt die weitere Regelverarbeitung und fährt mit der Bereitstellung der Antwort fort. Wenn wafFlags vorhanden ist, deaktiviert es die angegebenen WAF-Schutzmechanismen und fährt mit der weiteren Regelverarbeitung fort. |
| **block** | `status, wafFlags` (fakultativ und gegenseitig ausschließen) | Wenn wafFlags nicht vorhanden ist, wird der HTTP-Fehler unter Umgehung aller anderen Eigenschaften zurückgegeben. Der Fehlercode wird durch die Statuseigenschaft definiert oder standardmäßig auf 406 gesetzt. Wenn wafFlags vorhanden ist, ermöglicht es bestimmte WAF-Schutzmaßnahmen und fährt mit der weiteren Regelverarbeitung fort. |
| **log** | `wafFlags` (optional) | protokolliert die Tatsache, dass die Regel ausgelöst wurde, andernfalls hat dies keine Auswirkungen auf die Verarbeitung. wafFlags hat keine Auswirkung |

### WAF-Flags-Liste {#waf-flags-list}

Die `wafFlags` -Eigenschaft, die in den lizenzierbaren WAF-Traffic-Filterregeln verwendet werden kann, kann auf Folgendes verweisen:

| **Kennzeichen-ID** | **Flag Name** | **Beschreibung** |
|---|---|---|
| SQLI | SQL-Injektion | SQL Injection ist der Versuch, durch die Ausführung beliebiger Datenbankabfragen Zugriff auf eine Anwendung zu erhalten oder privilegierte Informationen zu erhalten. |
| HINTERGRUND | Backend | Ein Backdoor-Signal ist eine Anfrage, die versucht festzustellen, ob eine gemeinsame Backdoor-Datei auf dem System vorhanden ist. |
| CMDEXE | Befehlsausführung | Befehlsausführung ist der Versuch, durch beliebige Systembefehle mithilfe von Benutzereingaben die Kontrolle über ein Zielsystem zu erlangen oder ein Zielsystem zu beschädigen. |
| XSS | Site-übergreifende Skripterstellung | Die Site-übergreifende Skripterstellung ist der Versuch, das Konto eines Benutzers oder die Webbrowsing-Sitzung durch schädlichen JavaScript-Code zu ersetzen. |
| TRAVERSAL | Verzeichnisdurchlauf | Directory Traversal ist der Versuch, in einem System durch privilegierte Ordner zu navigieren, in der Hoffnung, vertrauliche Informationen zu erhalten. |
| BENUTZERAGENT | Attack-Tools | Attack Tooling ist der Einsatz automatisierter Software zur Identifizierung von Sicherheitslücken oder zum Versuch, eine entdeckte Verwundbarkeit auszunutzen. |
| LOG4J-JNDI | Log4J JNDI | Log4J JNDI-Angriffe versuchen, die [Sicherheitslücke durch Log4Shell](https://en.wikipedia.org/wiki/Log4Shell) in Log4J-Versionen vor 2.16.0 vorhanden |
| BHH | Bad Hop Headers | Bad Hop-Header weisen auf einen HTTP-Schmuggelversuch durch einen fehlerhaften Transfer-Encoding (TE)- oder Content-Length (CL)-Header oder einen korrekt formatierten TE- und CL-Header hin. |
| ABNORMALPATH | Anormaler Pfad | Anormaler Pfad gibt an, dass der ursprüngliche Pfad vom normalisierten Pfad abweicht (z. B. `/foo/./bar` wird normalisiert in `/foo/bar`) |
| DOUBLEENCODE | Doppelte Kodierung | Bei der doppelten Kodierung wird geprüft, ob HTML-Zeichen doppelt kodiert werden |
| NOTUTF8 | Ungültige Kodierung | Eine ungültige Kodierung kann dazu führen, dass der Server böswillige Zeichen aus einer Anfrage in eine Antwort übersetzt, was entweder zu einer Dienstverweigerung oder XSS führt |
| JSON-FEHLER | JSON-Kodierungsfehler | Ein POST-, PUT- oder PATCH-Anforderungstext, der als JSON-Inhalt im Anforderungsheader &quot;Content-Type&quot;enthält, aber JSON-Parsing-Fehler enthält. Dies hängt häufig mit einem Programmierfehler oder einer automatisierten oder böswilligen Anfrage zusammen. |
| MALFORMED-DATA | Fehlerhafte Daten im Anfrageinhalt | Ein POST-, PUT- oder PATCH-Anfrageinhalt, der gemäß der Anfragekopfzeile &quot;Content-Type&quot;fehlerhaft ist. Wenn beispielsweise ein Anforderungsheader &quot;Content-Type: application/x-www-form-urlencoded&quot;angegeben ist und einen POST-Hauptteil enthält, der json ist. Dies ist häufig ein Programmierfehler, eine automatisierte oder böswillige Anfrage. Erfordert Agent 3.2 oder höher. |
| SANS | böswilliger IP-Traffic | [SANS Internet Storm Center](https://isc.sans.edu/) Liste der IP-Adressen, von denen berichtet wurde, dass sie schädliche Aktivitäten durchgeführt haben |
| SIGSCI-IP | Netzwerkeffekt | IP-Adresse, die von SignalSciences gekennzeichnet wird: Jedes Mal, wenn eine IP aufgrund eines bösartigen Signals von der Entscheidungs-Engine gekennzeichnet wird, wird diese IP an alle Kunden weitergeleitet. Nachfolgende Anfragen von den IP-Adressen, die ein zusätzliches Signal für die Dauer der Markierung enthalten, werden dann protokolliert |
| NO-CONTENT-TYPE | Fehlende Anfrage-Kopfzeile &quot;Content-Type&quot; | Eine Anfrage vom Typ POST, PUT oder PATCH, die keinen Anforderungsheader vom Typ &quot;Content-Type&quot;enthält. Standardmäßig sollten Anwendungsserver in diesem Fall von &quot;Content-Type: text/plain; charset=us-ascii&quot;ausgehen. Bei vielen automatisierten und böswilligen Anfragen fehlt möglicherweise &quot;Content Type&quot;. |
| NOUA | Kein Benutzeragent | Viele automatisierte und böswillige Anfragen verwenden gefälschte oder fehlende Benutzeragenten, um die Identifizierung des Gerätetyps zu erschweren, der die Anforderungen stellt. |
| TORNODE | Tor Traffic | Tor ist eine Software, die die Identität eines Benutzers verschleiert. Eine Spitze im Tor-Traffic kann darauf hinweisen, dass ein Angreifer versucht, seinen Standort zu verschleiern. |
| NULLBYTE | Null Byte | Null-Bytes werden normalerweise nicht in einer Anfrage angezeigt und weisen darauf hin, dass die Anfrage falsch formatiert ist und möglicherweise bösartig ist. |
| PRIVATEFILE | Private Dateien | Private Dateien sind normalerweise vertraulich, wie z. B. ein Apache `.htaccess` -Datei oder einer Konfigurationsdatei, die vertrauliche Informationen übergeben kann |
| SCANNER | Scanner | Identifiziert beliebte Scandienste und -werkzeuge |
| RESPONSESPLIT | HTTP-Antwortaufteilung | Gibt an, wann CRLF-Zeichen als Eingabe an die Anwendung gesendet werden, um Header in die HTTP-Antwort einzufügen. |
| XML-FEHLER | XML-Kodierungsfehler | Ein POST-, PUT- oder PATCH-Anfrageinhalt, der im Anfrageheader &quot;Content-Type&quot;als XML-Inhalt mit XML-Parsing-Fehlern angegeben ist. Dies hängt häufig mit einem Programmierfehler oder einer automatisierten oder böswilligen Anfrage zusammen. |

## Überlegungen {#considerations}

* Wenn zwei in Konflikt stehende Regeln erstellt werden, haben die Zulassungsregeln immer Vorrang vor den Blockregeln. Wenn Sie beispielsweise eine Regel erstellen, die einen bestimmten Pfad blockiert, und eine Regel, die eine bestimmte IP-Adresse zulässt, sind Anforderungen von dieser IP-Adresse auf dem blockierten Pfad zulässig.

* Wenn eine Regel abgeglichen und blockiert wird, antwortet das CDN mit einer `406` Rückgabe-Code.

* Die Konfigurationsdateien sollten keine Geheimnisse enthalten, da sie von allen Benutzern gelesen werden können, die Zugriff auf das Git-Repository haben.

## Regelbeispiele {#examples}

Es folgen einige Regelbeispiele. Siehe [Ratenbegrenzungsabschnitt](#rules-with-rate-limits) weiter unten für Beispiele für Regeln zur Begrenzung der Steuersätze.

**Beispiel 1**

Diese Regel blockiert Anforderungen aus IP 192.168.1.1:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
     rules:
       - name: "block-request-from-ip"
         when: { reqProperty: clientIp, equals: "192.168.1.1" }
         action:
           type: block
```

**Beispiel 2**

Diese Regel blockiert Anforderungen für den Pfad `/helloworld` bei Veröffentlichung mit einem Benutzeragenten, der Chrome enthält:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
      - name: "block-request-from-chrome-on-path-helloworld-for-publish-tier"
        when:
          allOf:
          - { reqProperty: path, equals: /helloworld }
          - { reqProperty: tier, equals: publish }
          - { reqHeader: user-agent, matches: '.*Chrome.*'  }
        action:
          type: block
```

**Beispiel 3**

Diese Regel blockiert Anforderungen, die den Abfrageparameter enthalten `foo`, aber erlaubt jede Anfrage von IP 192.168.1.1:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
      - name: "block-request-that-contains-query-parameter-foo"
        when: { queryParam: url-param, equals: foo }
        action:
          type: block
      - name: "allow-all-requests-from-ip"
        when: { reqProperty: clientIp, equals: 192.168.1.1 }
        action:
          type: allow
```

**Beispiel 4**

Diese Regel blockiert Anforderungen an den Pfad `/block-me`und blockiert alle Anforderungen, die mit einer `SQLI` oder `XSS` Muster. Dieses Beispiel enthält eine WAF-Traffic-Filterregel, die auf die Variable `SQLI` und `XSS` [WAF-Flags](#waf-flags-list), für die eine separate Lizenz erforderlich ist.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
      - name: "path-rule"
        when: { reqProperty: path, equals: /block-me }
        action:
          type: block
      - name: "Enable-SQL-Injection-and-XSS-waf-rules-globally"
        when: { reqProperty: path, like: "*" }
        action:
          type: block
          wafFlags: [ SQLI, XSS]
```

**Beispiel 5**

Diese Regel blockiert den Zugriff auf OFAC-Länder:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
      - name: block-ofac-countries
        when:
          allOf:
            - reqProperty: tier
              matches: "author|publish"
            - reqProperty: clientCountry
              in:
                - SY
                - BY
                - MM
                - KP
                - IQ
                - CD
                - SD
                - IR
                - LR
                - ZW
                - CU
                - CI
        action: block
```

## Regeln für Ratenbegrenzungen {#rate-limits-rules}

Manchmal ist es wünschenswert, Traffic, der mit einer Regel übereinstimmt, nur zu blockieren, wenn die Übereinstimmung eine bestimmte Rate im Zeitverlauf überschreitet. Festlegen eines Werts für `rateLimit` -Eigenschaft begrenzt die Rate der Anforderungen, die mit der Regelbedingung übereinstimmen.

Regeln für die Begrenzung von Werten können nicht auf WAF-Flags verweisen. Sie stehen allen Sites- und Forms-Kunden zur Verfügung.

### rateLimit-Struktur {#ratelimit-structure}

| **Eigenschaft** | **Typ** | **Standard** | **BEDEUTUNG** |
|---|---|---|---|
| limit | Ganzzahl von 10 bis 10000 | erforderlich | Anforderungsrate (pro CDN POP) in Anforderungen pro Sekunde, für die die Regel ausgelöst wird. |
| window | Ganzzahl-Enum: 1, 10 oder 60 | 10 | Stichprobenfenster in Sekunden, für die die Anforderungsrate berechnet wird. |
| Sanktion | Ganzzahl von 60 bis 3600 | 300 (5 Minuten) | Ein Zeitraum in Sekunden, für den übereinstimmende Anforderungen blockiert werden (auf die nächste Minute gerundet). |
| groupBy | array[Getter] | keine | Der Zähler der Ratenbegrenzer wird durch eine Reihe von Anforderungseigenschaften aggregiert (z. B. clientIp). |

### Beispiele {#ratelimiting-examples}

**Beispiel 1**

Diese Regel blockiert einen Client für 5 m, wenn er in den letzten 60 Sekunden 100 Req/Sek (pro CDN POP) übersteigt:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
    - name: limit-requests-client-ip
      when:
        reqProperty: tier
        matches: "author|publish"
      rateLimit:
        limit: 60
        window: 10
        penalty: 300
        groupBy:
          - reqProperty: clientIp
      action: block
```

**Beispiel 2**

Blockanfragen für 60 s für den Pfad /critical/resource , wenn er in den letzten 60 Sekunden 100 Req/Sek (pro CDN POP) überschreitet:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
      - name: rate-limit-example
        when: { reqProperty: path, equals: /critical/resource }
        action:
          type: block
        rateLimit: { limit: 100, window: 60, penalty: 60 }
```

## CDN-Protokolle {#cdn-logs}

AEM as a Cloud Service bietet Zugriff auf CDN-Protokolle, die für Anwendungsfälle nützlich sind, einschließlich der Optimierung der Cache-Trefferquote und der Konfiguration von CDN- und WAF-Regeln. CDN-Protokolle werden in Cloud Manager angezeigt **Protokolle herunterladen** angezeigt, wenn Sie den Autoren- oder Veröffentlichungsdienst auswählen.

Beachten Sie, dass sich CDN-Protokolle möglicherweise um bis zu 5 Minuten verzögern.

Die `rules` -Eigenschaft beschreibt, welche Traffic-Filterregeln übereinstimmen, und weist folgendes Muster auf:

```
"rules": "match=<matching-customer-named-rules-that-are-matched>,waf=<matching-WAF-rules>,action=<action_type>"
```

Beispiel:

```
"rules": "match=Block-Traffic-under-private-folder,Enable-SQL-injection-everywhere,waf="SQLI,SANS",action=block"
```

Die Regeln verhalten sich wie folgt:

* Der vom Kunden deklarierte Regelname aller übereinstimmenden Regeln wird im Attribut stimmt überein mit .
* Das Aktionsattribut gibt an, ob die Regeln blockiert, zugelassen oder protokolliert wurden.
* Wenn die WAF lizenziert und aktiviert ist, listet das waf-Attribut alle WAF-Regeln (z. B. SQLI; beachten Sie, dass diese unabhängig vom vom vom Kunden deklarierten Namen sind) auf, die erkannt wurden, unabhängig davon, ob die WAF-Regeln in der Konfiguration aufgelistet wurden.
* Wenn keine vom Kunden deklarierten Regeln übereinstimmen und keine WAF-Regeln übereinstimmen, ist die Regelattributeigenschaft leer.

Im Allgemeinen werden die Übereinstimmungsregeln im Protokolleintrag für alle Anfragen an das CDN angezeigt, unabhängig davon, ob es sich um einen CDN-Treffer, einen CDN-Treffer, einen Pass- oder einen Fehler handelt. WAF-Regeln werden jedoch nur für Anfragen an das CDN im Protokolleintrag angezeigt, die als CDN-Fehlschläge oder -Übermittlungen gelten, nicht aber für CDN-Treffer.

Das folgende Beispiel zeigt ein Beispiel `cdn.yaml` und zwei CDN-Protokolleinträge:


```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
      - name: "path-rule"
        when: { reqProperty: path, equals: /block-me }
        action: block
      - name: "Enable-SQL-Injection-and-XSS-waf-rules-globally"
        when: { reqProperty: path, like: "*" }
        action:
          type: block
          wafFlags: [ SQLI, XSS ]
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
"rules": "match=path-rule,action=blocked"
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
"rules": "match=Enable-SQL-Injection-and-XSS-waf-rules-globally,waf=SQLI,action=blocked"
}
```

### Protokollformat {#cdn-log-format}

Nachfolgend finden Sie eine Liste der in CDN-Protokollen verwendeten Feldnamen sowie eine kurze Beschreibung.

| **Feldname** | **Beschreibung** |
|---|---|
| *timestamp* | Der Zeitpunkt, zu dem die Anfrage nach TLS-Beendigung gestartet wurde. |
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
| *Regeln* | Der Name aller übereinstimmenden Regeln.<br><br>Gibt auch an, ob die Übereinstimmung zu einem Block führte. <br><br>Beispiel: &quot;`match=Enable-SQL-Injection-and-XSS-waf-rules-globally,waf=SQLI,action=blocked`&quot;<br><br>Leer, wenn keine Regeln übereinstimmten. |

## Dashboard-Tooling {#dashboard-tooling}

Adobe bietet einen Mechanismus zum Herunterladen von Dashboard-Tools auf Ihren Computer, um CDN-Protokolle zu erfassen, die über Cloud Manager heruntergeladen wurden. Mit diesem Tool können Sie Ihren Traffic analysieren, um die entsprechenden Traffic-Filterregeln zu finden, die deklariert werden können, einschließlich WAF-Regeln.

Dashboard-Tools können direkt aus dem [AEMCS-CDN-Log-Analysis-ELK-Tool](https://github.com/adobe/AEMCS-CDN-Log-Analysis-ELK-Tool) GitHub-Repository

[Siehe Tutorial](#tutorial) für konkrete Anweisungen zur Verwendung der Dashboard-Werkzeuge.

## Tutorial {#tutorial}

Adobe bietet einen Mechanismus zum Herunterladen von Dashboard-Tools auf Ihren Computer, um CDN-Protokolle zu erfassen, die über Cloud Manager heruntergeladen wurden. Mit diesem Tool können Sie Ihren Traffic analysieren, um die entsprechenden Traffic-Filterregeln zu finden, die deklariert werden können, einschließlich WAF-Regeln. In diesem Abschnitt erhalten Sie zunächst Anweisungen, wie Sie sich mit den Dashboard-Tools in einer Entwicklungsumgebung vertraut machen können. Anschließend erhalten Sie Anleitungen dazu, wie Sie dieses Wissen nutzen können, um Regeln in einer Produktionsumgebung zu erstellen.

Dashboard-Tools können direkt aus dem [AEMCS-CDN-Log-Analysis-ELK-Tool](https://github.com/adobe/AEMCS-CDN-Log-Analysis-ELK-Tool) GitHub-Repository.


### Machen Sie sich mit den Dashboard-Tools vertraut {#dashboard-getting-familiar}

1. Erstellen Sie eine Cloud Manager-Konfigurations-Pipeline ohne Produktionscharakter, die mit einer Entwicklungsumgebung verknüpft ist. Wählen Sie zuerst die **Bereitstellungs-Pipeline** -Option. Wählen Sie anschließend **Zielgerichtete Implementierung**, Konfiguration, Ihr Repository, die Git-Verzweigung und legen Sie den Code-Speicherort auf /config fest.

   ![Implementierung von produktionsfremden Pipelines zur Auswahl hinzufügen](/help/security/assets/waf-select-pipeline1.png)

   ![Hinzufügen einer produktionsfremden Pipeline zur Auswahl einer Zielgruppe](/help/security/assets/waf-select-pipeline2.png)

[Weitere Informationen zum Einrichten von Nicht-Produktions-Pipelines finden Sie in diesem Dokument .](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md)

1. Erstellen Sie in Ihrem Arbeitsbereich eine Ordnerkonfiguration auf der Stammebene und fügen Sie eine Datei mit dem Namen `cdn.yaml`, wo Sie eine einfache Regel deklarieren und sie im Protokollmodus anstatt im Blockierungsmodus festlegen.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
    # Log request on simple path
    - name: log-rule-example
      when:
        allOf:
          - reqProperty: tier
            matches: "author|publish"
          - reqProperty: path
            equals: '/log/me'
      action: log
```

1. Übernehmen und pushen Sie Ihre Änderungen und stellen Sie Ihre Konfiguration mithilfe der Konfigurations-Pipeline bereit.

   ![Konfigurationspipeline ausführen](/help/security/assets/waf-run-pipeline.png)

1. Versuchen Sie nach der Bereitstellung Ihrer Konfiguration auf Folgendes zuzugreifen: `https://publish-pXXXXX-eYYYYYY.adobeaemcloud.com/log/me` mit Ihrem Webbrowser oder mit dem unten stehenden curl-Befehl. Sie sollten eine 404-Fehlerseite erhalten, da diese Seite nicht vorhanden ist.

   ```
   curl -svo /dev/null https://publish-pXXXXX-eYYYYYY.adobeaemcloud.com/log/me
   ```

1. Laden Sie die CDN-Protokolle aus Cloud Manager herunter und überprüfen Sie, ob die Regeln erwartungsgemäß übereinstimmen, wobei die Regeleigenschaft dem Regelnamen entspricht:

   ```
   "rules": "match=log-rule-example"
   ```

   ![Download-Protokolle auswählen](/help/security/assets/waf-download-logs1.png)

   ![Protokolle herunterladen](/help/security/assets/waf-download-logs2.png)

1. Laden Sie das Docker-Bild mit dem Dashboard-Tool und befolgen Sie die README-Anweisungen, um die CDN-Protokolle aufzunehmen. Wie in den folgenden Screenshots dargestellt, wählen Sie den richtigen Zeitraum, die richtige Umgebung und die richtigen Filter aus.

   ![Zeit aus Dashboard auswählen](/help/security/assets/dashboard-select-time.png)

   ![Umgebung aus Dashboard auswählen](/help/security/assets/dashboard-select-env.png)

1. Sobald die richtigen Filter angewendet wurden, sollte ein Dashboard mit den erwarteten Daten geladen werden. Im folgenden Screenshot wurde das Regelprotokollregelbeispiel in den letzten 2 Stunden dreimal durch dieselbe IP in Irland ausgelöst, die einen Webbrowser und curl verwendet.

   ![Anzeigen von Dashboard-Daten](/help/security/assets/dashboard-see-data-logmode.png)
   ![Anzeigen von Dashboard-Daten-Widgets](/help/security/assets/dashboard-see-data-logmode2.png)

1. Ändern Sie jetzt cdn.yaml, um die Regel in den Blockmodus zu versetzen, damit die Seiten wie erwartet blockiert werden. Übertragen Sie dann die Konfigurations-Pipeline, pushen Sie sie und Trigger wie zuvor beschrieben.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
    # Log request on simple path
    - name: log-rule-example
      when:
        allOf:
          - reqProperty: tier
            matches: "author|publish"
          - reqProperty: path
            equals: '/log/me'
      action: block
```

1. Versuchen Sie nach der Bereitstellung Ihrer Konfiguration auf Folgendes zuzugreifen: `https://publish-pXXXXX-eYYYYYY.adobeaemcloud.com/log/me` mit Ihrem Webbrowser oder mit dem unten stehenden curl-Befehl. Sie sollten eine 406-Fehlerseite erhalten, die angibt, dass die Anfrage blockiert wurde.

   ```
   curl -svo /dev/null https://publish-pXXXXX-eYYYYYY.adobeaemcloud.com/log/me
   ```

1. Laden Sie erneut Ihre CDN-Protokolle in Cloud Manager herunter (Hinweis: Es kann bis zu 5 Minuten dauern, bis die neuen Anforderungen in Ihren CDN-Protokollen angezeigt werden) und importieren Sie sie wie zuvor in das Dashboard-Tool. Aktualisieren Sie danach Ihr Dashboard. Wie Sie im folgenden Screenshot sehen können, werden Anfragen an `/log/me` von unserer Regel blockiert werden.

   ![Anzeigen von Produkt-Dashboard-Daten](/help/security/assets/dashboard-see-data-blockmode.png)
   ![Anzeigen von Produkt-Dashboard-Daten](/help/security/assets/dashboard-see-data-blockmode2.png)

1. Wenn Sie WAF-Traffic-Filter aktiviert haben (dies erfordert eine zusätzliche Lizenz, nachdem die Funktion GA ist), wiederholen Sie dies mit einer WAF-Traffic-Filterregel im Protokollmodus und stellen Sie die Regeln bereit.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
      - name: log-waf-flags
        when:
          reqProperty: tier
          matches: "author|publish"
        action:
          type: log
          wafFlags:
              - SANS
              - SIGSCI-IP
              - TORNODE
              - NOUA
              - SCANNER
              - USERAGENT
              - PRIVATEFILE
              - ABNORMALPATH
              - TRAVERSAL
              - NULLBYTE
              - BACKDOOR
              - LOG4J-JNDI
              - SQLI
              - XSS
              - CODEINJECTION
              - CMDEXE
              - NO-CONTENT-TYPE
              - UTF8
```

1. Verwenden Sie ein Tool wie [nikto](https://github.com/sullo/nikto/tree/master) , um übereinstimmende Anforderungen zu generieren. Der folgende Befehl sendet in weniger als 1 Minute etwa 550 böswillige Anfragen.

   ```
   ./nikto.pl -useragent "MyAgent (Demo/1.0)" -D V -Tuning 9 -ssl -h https://publish-pXXXXX-eYYYYY.adobeaemcloud.com
   ```

1. Laden Sie die CDN-Protokolle aus Cloud Manager herunter (denken Sie daran, dass es bis zu 5 Minuten dauern kann, bis sie angezeigt werden) und überprüfen Sie, ob sowohl die übereinstimmenden deklarierten Regeln als auch die WAF-Flags angezeigt werden.

   Wie Sie sehen, werden einige der von Nikto produzierten Anfragen von der WAF als bösartig gekennzeichnet. Wir sehen, dass Nikto versucht hat, CMDEXE-, SQLI- und NULL-BYTE-Schwachstellen auszunutzen. Wenn Sie jetzt die Aktion von log zu block ändern und einen Scan mit Nikto erneut Trigger machen, werden alle bisher gekennzeichneten Anfragen diesmal blockiert.

   ![WAF-Daten anzeigen](/help/security/assets/dashboard-see-data-waf.png)


   Beachten Sie, dass immer dann, wenn eine Anfrage mit einer der WAF-Flags übereinstimmt, diese WAF-Flags angezeigt werden, auch wenn sie nicht Teil der deklarierten Regel sind. Daher kennen Sie potenziell neuen böswilligen Traffic, für den Sie noch keine übereinstimmenden Regeln deklariert haben. Beispiel:

   ```
   "rules": "match=log-waf-flags,waf=SQLI,action=blocked"
   ```

1. Wiederholen Sie diesen Vorgang mit einer Regel, die die Ratenbegrenzung im Protokollmodus verwendet. Übergeben Sie die Konfigurations-Pipeline wie gewohnt, pushen Sie sie und Trigger, um sie zu konfigurieren.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
      - name: limit-requests-client-ip
        when:
          reqProperty: tier
          matches: "author|publish"
        rateLimit:
          limit: 10
          window: 1
          penalty: 60
          groupBy:
            - reqProperty: clientIp
        action: log
```

1. Verwenden Sie ein Tool wie [Vegeta](https://github.com/tsenart/vegeta) , um Traffic zu generieren.

   ```
   echo "GET https://publish-pXXXXX-eYYYYYY.adobeaemcloud.com" | vegeta attack -duration=5s | tee results.bin | vegeta report
   ```

1. Nachdem Sie das Tool ausgeführt haben, können Sie CDN-Protokolle herunterladen und sie im Dashboard erfassen, um zu überprüfen, ob die Regel zur Begrenzung der Rate ausgelöst wurde.

   ![WAF-Daten anzeigen](/help/security/assets/waf-dashboard-ratelimiter-1.png)

   ![WAF-Daten anzeigen](/help/security/assets/waf-dashboard-ratelimiter-2.png)

   Wie Sie unsere Regel sehen können **limit-requests-client-ip** ausgelöst wurde.

   Nachdem Sie sich mit der Funktionsweise von Traffic-Filterregeln vertraut gemacht haben, können Sie in die Produktionsumgebung wechseln.

### Bereitstellen von Regeln in der Produktionsumgebung {#dashboard-prod-env}

Vergewissern Sie sich, dass Sie Regeln zunächst im Protokollmodus deklarieren, um zu überprüfen, ob es keine falsch-positiven Werte gibt. Dies bedeutet legitimen Traffic, der fälschlicherweise blockiert würde.

1. Erstellen Sie eine mit Ihrer Produktionsumgebung verknüpfte Produktionskonfigurations-Pipeline.

1. Kopieren Sie die unten empfohlenen Regeln in Ihre cdn.yaml. Sie können die Regeln auf Grundlage der einzigartigen Merkmale des Live-Traffics Ihrer Website ändern. Übertragen, Push-Benachrichtigung und Trigger der Konfigurationspipeline. Stellen Sie sicher, dass sich die Regeln im Protokollmodus befinden.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
    #  Block client for 5m when it exceeds 100 req/sec on a time window of 1sec
    - name: limit-requests-client-ip
      when:
        reqProperty: path
        like: '*'
      rateLimit:
        limit: 100
        window: 1
        penalty: 300
        groupBy:
          - reqProperty: clientIp
      action: log
    # Block requests coming from OFAC countries
    - name: block-ofac-countries
      when:
        allOf:
          - { reqProperty: tier, equals: publish }
          - reqProperty: clientCountry
            in:
              - SY
              - BY
              - MM
              - KP
              - IQ
              - CD
              - SD
              - IR
              - LR
              - ZW
              - CU
              - CI
      action: log
    # Enable recommended WAF protections (only works if WAF is enabled for your environment)
    - name: block-waf-flags-globally
      when:
        reqProperty: tier
        matches: "author|publish"
      action:
        type: log
        wafFlags:
          - SANS
          - SIGSCI-IP
          - TORNODE
          - NOUA
          - SCANNER
          - USERAGENT
          - PRIVATEFILE
          - ABNORMALPATH
          - TRAVERSAL
          - NULLBYTE
          - BACKDOOR
          - LOG4J-JNDI
          - SQLI
          - XSS
          - CODEINJECTION
          - CMDEXE
          - NO-CONTENT-TYPE
          - UTF8
    # Disable protection against CMDEXE on /bin
    - name: allow-cdmexe-on-root-bin
      when:
        allOf:
          - reqProperty: tier
            matches: "author|publish"
          - reqProperty: path
            matches: "^/bin/.*"
      action:
        type: log
        wafFlags:
          - CMDEXE
```

1. Fügen Sie zusätzliche Regeln hinzu, um schädlichen Traffic zu verhindern, den Sie möglicherweise kennen. Beispielsweise bestimmte IPs, die Ihre Site angreifen.

1. Laden Sie nach einigen Minuten, Stunden oder Tagen abhängig vom Traffic-Volumen Ihrer Site CDN-Protokolle aus Cloud Manager herunter und analysieren Sie sie mit dem Dashboard.

1. Im Folgenden finden Sie einige Überlegungen:
   1. Traffic-Abgleich deklarierter Regeln wird in Diagrammen und Anforderungsprotokollen angezeigt. So können Sie einfach überprüfen, ob Ihre deklarierten Regeln ausgelöst werden.
   1. Traffic-Match-WAF-Flags werden in Diagrammen und Anforderungsprotokollen angezeigt, selbst wenn Sie sie nicht in einer Regel protokolliert haben. Dies bedeutet, dass Sie sich immer des potenziell neuen böswilligen Traffics bewusst sind und bei Bedarf neue Regeln erstellen können. Sehen Sie sich WAF-Flags an, die nicht in den deklarierten Regeln enthalten sind, und erwägen Sie, sie zu deklarieren.
   1. Prüfen Sie die Anfrageprotokolle auf Falsch-Positiv-Werte und prüfen Sie, ob Sie sie aus den Regeln herausfiltern können. Zum Beispiel sind sie vielleicht nur für bestimmte Pfade falsch positiv.

1. Legen Sie die entsprechenden Regeln auf den Blockierungsmodus fest und erwägen Sie auch das Hinzufügen zusätzlicher Regeln. Vielleicht sollten einige Regeln im Protokollmodus bleiben, wenn Sie weitere Analysen mit mehr Traffic durchführen.

1. Stellen Sie die Konfiguration erneut bereit.

1. Wiederholen Sie die Analyse der Dashboards häufig.

