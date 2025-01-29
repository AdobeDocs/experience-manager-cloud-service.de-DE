---
title: Traffic-Filterregeln, einschließlich WAF-Regeln
description: Konfigurieren von Traffic-Filterregeln, einschließlich WAF-Regeln (Web Application Firewall).
exl-id: 6a0248ad-1dee-4a3c-91e4-ddbabb28645c
feature: Security
role: Admin
source-git-commit: bc5dbee5b5accc747288638fd8e22ed8f2d12fd5
workflow-type: ht
source-wordcount: '4049'
ht-degree: 100%

---


# Traffic-Filterregeln, einschließlich WAF-Regeln {#traffic-filter-rules-including-waf-rules}

Traffic-Filterregeln können verwendet werden, um Anforderungen auf der CDN-Ebene zu blockieren oder zuzulassen. Dies kann in Szenarien wie den folgenden nützlich sein:

* Einschränken des Zugriffs auf bestimmte Domains auf den internen Unternehmensdatenverkehr, bevor eine neue Site live geschaltet wird
* Festlegen von Ratenbeschränkungen, um für volumetrische DoS-Angriffe weniger anfällig zu sein
* Verhindern, dass IP-Adressen, die als bösartig bekannt sind, auf Ihre Seiten zugreifen.

Die meisten dieser Traffic-Filterregeln stehen allen Kundinnen und Kunden von AEM as a Cloud Service Sites und Forms zur Verfügung. Sie arbeiten hauptsächlich mit den Eigenschaften und Kopfzeilen von Anfragen, einschließlich IP, Host-Name, Pfad und Benutzeragent.

Eine Unterkategorie von Traffic-Filterregeln erfordert entweder eine Lizenz für erweiterte Sicherheit oder eine WAF-DDoS Protection-Lizenz. Diese leistungsstarken Regeln werden als Traffic-Filterregeln für WAF (Web Application Firewall, kurz: WAF-Regeln) bezeichnet und haben Zugriff auf die [WAF-Flags](#waf-flags-list), die weiter unten in diesem Artikel beschrieben werden.

Traffic-Filterregeln können über Cloud Manager-Konfigurations-Pipelines in Entwicklungs-, Staging- und Produktionsumgebungen bereitgestellt werden. Die Konfigurationsdatei kann mithilfe von Befehlszeilenprogrammen in schnellen Entwicklungsumgebungen (Rapid Development Environments, RDEs) bereitgestellt werden.

[Absolvieren Sie ein Tutorial](#tutorial), um rasch konkrete Kenntnisse zu dieser Funktion zu erwerben.

>[!NOTE]
>Weitere Optionen zur Konfiguration des Traffics im CDN, einschließlich der Bearbeitung der Anfrage/Antwort, der Deklaration von Umleitungen und des Proxys zu einem Nicht-AEM-Ursprung, finden Sie im Artikel [Konfiguration von Traffic im CDN](/help/implementing/dispatcher/cdn-configuring-traffic.md).


## Wie dieser Artikel organisiert ist {#how-organized}

Dieser Artikel ist in die folgenden Abschnitte unterteilt:

* **Traffic-Schutz – Übersicht:** Erfahren Sie, wie Sie vor schädlichem Traffic geschützt werden.
* **Empfohlener Prozess zum Konfigurieren von Regeln:** Erfahren Sie mehr über allgemeine Methoden zum Schutz Ihrer Website.
* **Setup:** Erfahren Sie, wie Sie Traffic-Filterregeln einrichten, konfigurieren und bereitstellen, einschließlich der erweiterten WAF-Regeln.
* **Regelsyntax:** Erfahren Sie, wie Sie Traffic-Filterregeln in der Konfigurationsdatei von `cdn.yaml` deklarieren. Dazu gehören sowohl die Traffic-Filterregeln, die für alle Kundinnen und Kunden von Sites und Forms verfügbar sind, als auch die Unterkategorie der WAF-Regeln für diejenigen, die diese Funktion lizenzieren.
* **Regelbeispiele:** Sehen Sie sich zu Beginn Beispiele für deklarierte Regeln an.
* **Ratenbegrenzungsregeln:** Erfahren Sie, wie Sie Regeln zur Ratenbegrenzung verwenden, um Ihre Site vor Angriffen mit hohem Volumen zu schützen.
* **Warnhinweise zu Traffic-Filterregeln**: Konfigurieren Sie Warnhinweise, um benachrichtigt zu werden, wenn Ihre Regeln ausgelöst werden.
* **Warnhinweis zu Standard-Traffic-Spitze am Ursprung**: Lassen Sie sich benachrichtigen, wenn ein Anstieg des Traffics am Ursprung auf einen DDoS-Angriff hindeutet.
* **CDN-Protokolle:** Erfahren Sie, welche deklarierten Regeln und WAF-Flags mit Ihrem Traffic übereinstimmen.
* **Dashboard-Tooling:** Analysieren Sie Ihre CDN-Protokolle, um neue Traffic-Filterregeln zu erstellen.
* **Empfohlene Anfangsregeln:** Ein Regelsatz für die ersten Schritte.
* **Tutorial:** Praktisches Wissen bezüglich der Funktion, einschließlich der Verwendung der Dashboard-Werkzeuge zum Deklarieren der richtigen Regeln.

Adobe lädt Sie ein, Feedback zu geben oder Fragen zu Traffic-Filterregeln zu stellen, indem Sie eine E-Mail an **aemcs-waf-adopter@adobe.com** senden.

## Traffic-Schutz – Übersicht {#traffic-protection-overview}

In der aktuellen digitalen Landschaft stellt schädlicher Traffic eine immer präsente Bedrohung dar. Adobe ist sich der Ernsthaftigkeit des Risikos bewusst und bietet verschiedene Ansätze zum Schutz von Kundenanwendungen und zur Eindämmung von Angriffen.

Am Edge absorbiert das von Adobe verwaltete CDN DoS-Angriffe auf der Netzwerkschicht (Ebene 3 und 4), einschließlich Angriffe durch Überschwemmung oder Reflexion/Verstärkung.

Adobe ergreift standardmäßig Maßnahmen, um eine Leistungsbeeinträchtigung durch unerwartet hohes Traffic-Aufkommen über einen bestimmten Schwellenwert hinaus zu verhindern. Im Falle eines DoS-Angriffs, der die Verfügbarkeit der Website beeinträchtigt, werden die Betriebs-Teams von Adobe benachrichtigt und Maßnahmen zur Eindämmung des Problems ergriffen.

Kundinnen und Kunden können proaktive Maßnahmen ergreifen, um Angriffe auf Anwendungsebene (Ebene 7) zu minimieren, indem sie Regeln auf verschiedenen Ebenen des Inhaltsbereitstellungsflusses konfigurieren.

Auf der Apache-Ebene können Kundinnen und Kunden beispielsweise das [Dispatcher-Modul](https://experienceleague.adobe.com/de/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration#configuring-access-to-content-filter) oder [ModSecurity](https://experienceleague.adobe.com/de/docs/experience-manager-learn/foundation/security/modsecurity-crs-dos-attack-protection) konfigurieren, um den Zugriff auf bestimmte Inhalte zu beschränken.

Wie in diesem Artikel beschrieben, können Traffic-Filterregeln auf dem von Adobe verwalteten CDN bereitgestellt werden. Verwendet werden dazu die in Cloud Manager verfügbaren [Konfigurations-Pipelines.](/help/operations/config-pipeline.md) Zusätzlich zu Traffic-Filterregeln, die auf Eigenschaften wie IP-Adresse, Pfad und Headern basieren, oder Regeln, die auf der Festlegung von Ratenbeschränkungen beruhen, können Kundinnen und Kunden auch eine leistungsstarke Unterkategorie von Traffic-Filterregeln lizenzieren, die sogenannten WAF-Regeln.

## Vorgeschlagener Prozess {#suggested-process}

Im Folgenden finden Sie einen allgemein empfohlenen End-to-End-Prozess für die Erstellung der richtigen Traffic-Filterregeln:

1. Konfigurieren Sie Konfigurations-Pipelines für Nicht-Produktion und Produktion, wie im Abschnitt [Einrichtung](#setup) beschrieben.
1. Kundinnen und Kunden, die die Unterkategorie der WAF-Traffic-Filterregeln lizenziert haben, sollten sie in Cloud Manager aktivieren.
1. Lesen und probieren Sie das Tutorial aus, um genau zu verstehen, wie Traffic-Filterregeln verwendet werden, einschließlich WAF-Regeln, wenn sie lizenziert wurden. Das Tutorial führt Sie durch die Bereitstellung von Regeln in einer Entwicklungsumgebung, die Simulation von schädlichem Traffic sowie den Download der [CDN-Protokolle](#cdn-logs) und ihre Analyse in den [Dashboard-Tools](#dashboard-tooling).
1. Kopieren Sie die empfohlenen Anfangsregeln nach `cdn.yaml` und stellen Sie die Konfiguration in der Produktionsumgebung im Protokollmodus bereit.
1. Nachdem Sie etwas Traffic erfasst haben, analysieren Sie die Ergebnisse mit den [Dashboard-Tools](#dashboard-tooling), um zu sehen, ob es Übereinstimmungen gab. Suchen Sie nach Falsch-Positiv-Werten und nehmen Sie die erforderlichen Anpassungen vor, um schließlich die Anfangsregeln im Blockmodus zu aktivieren.
1. Fügen Sie benutzerdefinierte Regeln hinzu, die auf der Analyse der CDN-Protokolle basieren. Testen Sie sie zunächst mit simuliertem Traffic in Entwicklungsumgebungen, bevor Sie sie in Staging- und Produktionsumgebungen im Protokollmodus und dann im Blockmodus bereitstellen.
1. Überwachen Sie den Traffic auf fortlaufender Basis und nehmen Sie Änderungen an den Regeln vor, wenn sich die Bedrohungslage weiterentwickelt.

## Einrichtung {#setup}

1. Erstellen Sie eine Datei `cdn.yaml` mit einer Reihe von Traffic-Filterregeln, einschließlich WAF-Regeln.

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

   Eine Beschreibung der Eigenschaften oberhalb des Knotens `data` finden Sie unter [Verwenden von Konfigurations-Pipelines](/help/operations/config-pipeline.md#common-syntax). Der Eigenschaftswert `kind` sollte auf *CDN* und die Version auf `1` festgelegt werden.


1. Wenn WAF-Regeln lizenziert sind, sollten Sie die Funktion in Cloud Manager aktivieren, wie unten für sowohl neue als auch bestehende Programmszenarien beschrieben.

   1. Um WAF in einem neuen Programm zu konfigurieren, markieren Sie das Kontrollkästchen **WAF-DDOS-Schutz** auf der Registerkarte **Sicherheit**, wenn Sie [ein Produktionsprogramm hinzufügen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md).

   1. Um WAF für ein vorhandenes Programm zu konfigurieren, können Sie jederzeit Ihr [Programm bearbeiten](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md) und auf der Registerkarte **Sicherheit** die Option **WAF-DDOS** deaktivieren oder aktivieren.

1. Erstellen Sie in Cloud Manager eine Konfigurations-Pipeline. Folgen Sie dabei den Anweisungen im Artikel zu [Konfigurations-Pipelines.](/help/operations/config-pipeline.md#managing-in-cloud-manager) Die Pipeline verweist auf einen Ordner der obersten Ebene mit dem Namen `config`. Die Datei `cdn.yaml` ist in der Hierarchie darunter abgelegt, siehe [Verwenden von Konfigurations-Pipelines](/help/operations/config-pipeline.md#folder-structure).

## Syntax für Traffic-Filterregeln {#rules-syntax}

Sie können *Traffic-Filterregeln* konfigurieren, um Übereinstimmungen mit Mustern wie IPs, Benutzeragent, Anfrage-Headern, Host-Name, Geo und URL zu erhalten.

Kundinnen und Kunden mit einer Lizenz für die erweiterte Sicherheit oder die Sicherheitsoption zum Schutz vor WAF-DDoS können auch eine spezielle Kategorie von Traffic-Filterregeln namens *WAF-Traffic-Filterregeln* (oder kurz: WAF-Regeln) konfigurieren, die auf eine oder mehrere [WAF-Flags](#waf-flags-list) verweisen.

Im Folgenden finden Sie ein Beispiel für einen Satz von Traffic-Filterregeln, der auch eine WAF-Regel enthält.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
      - name: "path-rule"
        when:
          allOf:
            - { reqProperty: path, equals: /block-me }
            - { reqProperty: tier, equals: publish }
        action:
          type: block
      - name: "Enable-SQL-Injection-and-XSS-waf-rules-globally"
        when: { reqProperty: path, like: "*" }
        action:
          type: block
          wafFlags: [ SQLI, XSS]
```

Das Format der Traffic-Filterregeln in der Datei `cdn.yaml` wird im Folgenden beschrieben. Siehe einige [andere Beispiele](#examples) in einem späteren Abschnitt sowie einen separaten Abschnitt zu [Ratenbegrenzungsregeln](#rate-limit-rules).


| **Eigenschaft** | **Die meisten Traffic-Filterregeln** | **WAF-Traffic-Filterregeln** | **Typ** | **Standardwert** | **Beschreibung** |
|---|---|---|---|---|---|
| name | X | X | `string` | - | Regelname (64 Zeichen lang, darf nur alphanumerische Zeichen und „-“ enthalten.) |
| wenn | X | X | `Condition` | - | Die Grundstruktur ist:<br><br>`{ <getter>: <value>, <predicate>: <value> }`<br><br>[Siehe Syntax für Bedingungsstruktur](#condition-structure) weiter unten, in dem die Getter, Eigenschaften und die Kombination mehrerer Bedingungen beschrieben werden. |
| Aktion | X | X | `Action` | protokollieren | protokollieren, zulassen, blockieren oder Aktionsobjekt. Standard ist „protokollieren“ |
| rateLimit | X |   | `RateLimit` | nicht definiert | Ratenbegrenzungskonfiguration. Die Ratenbegrenzung ist deaktiviert, wenn sie nicht definiert ist.<br><br>Weiter unten finden Sie einen separaten Abschnitt mit einer Beschreibung der rateLimit-Syntax sowie Beispiele. |

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
| **allOf** | `array[Condition]` | **Und**-Vorgang. „True“, wenn alle aufgelisteten Bedingungen „true“ zurückgeben |
| **anyOf** | `array[Condition]` | **Oder** Vorgang. „True“, wenn eine der aufgelisteten Bedingungen „true“ zurückgibt |

**Getter**

| **Eigenschaft** | **Typ** | **Beschreibung** |
|---|---|---|
| reqProperty | `string` | Anfrageeigenschaft.<br><br>Eines von:<br><ul><li>`path`: Gibt den vollständigen Pfad einer URL ohne die Abfrageparameter zurück. (`pathRaw` für die Variante ohne Escape-Zeichen verwenden)</li><li>`url`: Gibt die vollständige URL, einschließlich der Abfrageparameter zurück. (`urlRaw` für die Variante ohne Escape-Zeichen verwenden)</li><li>`queryString`: Gibt den Abfrageteil einer URL zurück</li><li>`method`: Gibt die in der Anfrage verwendete HTTP-Methode zurück.</li><li>`tier`: Gibt entweder `author`, `preview` oder `publish` zurück.</li><li>`domain`: Gibt die Eigenschaft der Domain (wie in der `Host`-Kopfzeile definiert) in Kleinschreibung zurück</li><li>`clientIp`: Gibt die Client-IP zurück.</li><li>`forwardedDomain`: Gibt die erste Domain wie in der `X-Forwarded-Host`-Kopfzeile definiert in Kleinschreibung zurück</li><li>`forwardedIp`: Gibt die erste IP in der `X-Forwarded-For`-Kopfzeile zurück.</li><li>`clientCountry`: Gibt einen aus zwei Buchstaben bestehenden Code ([Regionales Indikatorsymbol](https://en.wikipedia.org/wiki/Regional_indicator_symbol)) zurück, der angibt, in welchem Land sich die Kundin bzw. der Kunde befindet.</li></ul> |
| reqHeader | `string` | Gibt die Anfragekopfzeile mit dem angegebenen Namen zurück |
| queryParam | `string` | Gibt den Abfrageparameter mit dem angegebenen Namen zurück |
| reqCookie | `string` | Gibt ein Cookie mit dem angegebenen Namen zurück |
| postParam | `string` | Gibt den Post-Parameter mit dem angegebenen Namen aus dem Anfragetext zurück. Funktioniert nur, wenn der Hauptteil vom Inhaltstyp `application/x-www-form-urlencoded` ist |

**Prädikat**

| **Eigenschaft** | **Typ** | **Bedeutung** |
|---|---|---|
| **gleich** | `string` | „True“, wenn das Getter-Ergebnis dem angegebenen Wert entspricht |
| **doesNotEqual** | `string` | „True“, wenn das Getter-Ergebnis nicht dem angegebenen Wert entspricht |
| **like** | `string` | „True“, wenn das Getter-Ergebnis mit dem angegebenen Muster übereinstimmt |
| **notLike** | `string` | „True“, wenn das Getter-Ergebnis nicht mit dem angegebenen Muster übereinstimmt |
| **matches** | `string` | „True“, wenn das Getter-Ergebnis mit dem angegebenen Regex übereinstimmt |
| **doesNotMatch** | `string` | „True“, wenn das Getter-Ergebnis nicht mit dem angegebenen Regex übereinstimmt |
| **in** | `array[string]` | „True“, wenn die angegebene Liste das Getter-Ergebnis enthält |
| **notIn** | `array[string]` | „True“, wenn die angegebene Liste das Getter-Ergebnis nicht enthält |
| **exists** | `boolean` | „True“, wenn auf es auf „true“ gesetzt ist und die Eigenschaft existiert, oder wenn es auf „false“ gesetzt ist und die Eigenschaft nicht vorhanden ist |

**Anmerkungen**

* Die Anfrageeigenschaft `clientIp` kann nur mit den folgenden Prädikaten verwendet werden: `equals`, `doesNotEqual`, `in`, `notIn`. `clientIp` kann bei auch mit IP-Bereichen verglichen werden, wenn die Prädikate `in` und `notIn` verwendet werden. Im folgenden Beispiel wird eine Bedingung implementiert, um zu bewerten, ob eine Client-IP im IP-Bereich von 192.168.0.0/24 liegt (also von 192.168.0.0 bis 192.168.0.255):

```
when:
  reqProperty: clientIp
  in: [ "192.168.0.0/24" ]
```

* Adobe empfiehlt die Verwendung von [regex101](https://regex101.com/) und [Fastly Fiddle](https://fiddle.fastly.dev/) bei der Arbeit mit Regex. Weitere Informationen darüber, wie Fastly mit Regex umgeht, finden Sie in der [Fastly-Dokumentation – Reguläre Ausdrücke in Fastly VCL](https://www.fastly.com/documentation/reference/vcl/regex/#best-practices-and-common-mistakes).


### Aktionsstruktur {#action-structure}

Ein `action` kann entweder eine Zeichenfolge sein, die die Aktion angibt (Zulassen, Blockieren oder Protokollieren), oder ein Objekt, das sowohl aus dem Aktionstyp (Zulassen, Blockieren oder Protokollieren) als auch aus Optionen wie wafFlags und/oder dem Status besteht.

**Aktionstypen**

Aktionen werden entsprechend ihren Typen in der folgenden Tabelle priorisiert, die entsprechend der Reihenfolge sortiert ist, in der die Aktionen ausgeführt werden.

| **Name** | **Zulässige Eigenschaften** | **Bedeutung** |
|---|---|---|
| **allow** | `wafFlags` (optional), `alert` (optional) | Wenn wafFlags nicht vorhanden ist, stoppt die weitere Regelverarbeitung und es wird mit der Bereitstellung der Antwort fortgefahren. Wenn wafFlags vorhanden ist, deaktiviert dies die angegebenen WAF-Schutzmechanismen und fährt mit der weiteren Regelverarbeitung fort. <br>Falls ein Warnhinweis angegeben wird, wird eine Benachrichtigung des Aktionszentrums gesendet, wenn die Regel zehnmal innerhalb eines 5-minütigen Zeitfensters ausgelöst wird. Sobald ein Warnhinweis für eine bestimmte Regel ausgelöst wurde, wird er erst am nächsten Tag (UTC) wieder ausgelöst. |
| **block** | `status, wafFlags` (optional und sich gegenseitig ausschließend), `alert` (optional) | Wenn wafFlags nicht vorhanden ist, wird der HTTP-Fehler unter Umgehung aller anderen Eigenschaften zurückgegeben. Der Fehler-Code wird durch die Statuseigenschaft definiert bzw. standardmäßig auf 406 gesetzt. Wenn wafFlags vorhanden ist, ermöglicht dies bestimmte WAF-Schutzmaßnahmen und fährt mit der weiteren Regelverarbeitung fort. <br>Falls ein Warnhinweis angegeben wird, wird eine Benachrichtigung des Aktionszentrums gesendet, wenn die Regel zehnmal innerhalb eines 5-minütigen Zeitfensters ausgelöst wird. Sobald ein Warnhinweis für eine bestimmte Regel ausgelöst wurde, wird er erst am nächsten Tag (UTC) wieder ausgelöst. |
| **log** | `wafFlags` (optional), `alert` (optional) | protokolliert die Tatsache, dass die Regel ausgelöst wurde, hat jedoch ansonsten keine Auswirkung auf die Verarbeitung. wafFlags hat keine Auswirkung. <br>Falls ein Warnhinweis angegeben wird, wird eine Benachrichtigung des Aktionszentrums gesendet, wenn die Regel zehnmal innerhalb eines 5-minütigen Zeitfensters ausgelöst wird. Sobald ein Warnhinweis für eine bestimmte Regel ausgelöst wurde, wird er erst am nächsten Tag (UTC) wieder ausgelöst. |

### WAF-Flags-Liste {#waf-flags-list}

Die `wafFlags`-Eigenschaft, die in den lizenzierbaren WAF-Traffic-Filterregeln verwendet werden kann, kann auf Folgendes verweisen:

| **Flag-ID** | **Flag-Name** | **Beschreibung** |
|---|---|---|
| SQLI | SQL-Injektion | SQL-Injektion ist der Versuch, durch die Ausführung beliebiger Datenbankabfragen Zugriff auf eine Anwendung zu erhalten oder privilegierte Informationen zu erhalten. |
| BACKDOOR | Backdoor | Ein Backdoor-Signal ist eine Anfrage, die versucht festzustellen, ob eine gemeinsame Backdoor-Datei auf dem System vorhanden ist. |
| CMDEXE | Befehlsausführung | Befehlsausführung ist der Versuch, durch beliebige Systembefehle mithilfe von Benutzereingaben die Kontrolle über ein Zielsystem zu erlangen oder ein Zielsystem zu beschädigen. |
| CMDEXE-NO-BIN | Befehlsausführung, außer für `/bin/` | Gewährleisten Sie das gleiche Schutzniveau wie `CMDEXE`, während falsch positive Ergebnisse für `/bin` aufgrund der AEM-Architektur deaktiviert werden. |
| XSS | Cross-Site-Scripting | Cross-Site-Scripting ist der Versuch, das Konto einer Benutzerin oder eines Benutzers oder die Webbrowsing-Sitzung durch schädlichen JavaScript-Code zu ersetzen. |
| TRAVERSAL | Verzeichnistraversierung | Verzeichnistraversierung ist der Versuch, in einem System durch privilegierte Ordner zu navigieren, in der Hoffnung, vertrauliche Informationen zu erhalten. |
| USERAGENT | Angriffs-Tooling | Angriffs-Tooling ist der Einsatz automatisierter Software zur Identifizierung von Sicherheitslücken oder zum Versuch, eine entdeckte Anfälligkeit auszunutzen. |
| LOG4J-JNDI | Log4J JNDI | Log4J JNDI-Angriffe versuchen, die [Log4Shell-Anfälligkeit](https://en.wikipedia.org/wiki/Log4Shell) in Log4J-Versionen vor 2.16.0 auszunutzen. |
| BHH | Bad Hop Headers | Bad Hop Headers weisen auf einen HTTP-Schmuggelversuch durch einen fehlerhaften Transfer-Encoding (TE)- oder Content-Length(CL)-Header oder einen korrekt formatierten TE- und CL-Header hin. |
| CODEINJECTION | Code-Injektion | Code-Injektion ist der Versuch, über beliebige Anwendungs-Code-Befehle mittels Benutzereingaben die Kontrolle über ein Zielsystem zu erlangen oder es zu beschädigen. |
| ABNORMALPATH | Anormaler Pfad | Anormaler Pfad bedeutet, dass der ursprüngliche Pfad vom normalisierten Pfad abweicht (z. B. `/foo/./bar` wird normalisiert in `/foo/bar`) |
| DOUBLEENCODE | Doppelte Codierung | Bei der doppelten Codierung wird geprüft, ob HTML-Zeichen doppelt codiert werden |
| NOTUTF8 | Ungültige Codierung | Eine ungültige Codierung kann dazu führen, dass der Server böswillige Zeichen aus einer Anfrage in eine Antwort übersetzt, was entweder zu einer Dienstverweigerung oder zu XSS führt |
| JSON-ERROR | JSON-Codierungsfehler | Ein POST-, PUT- oder PATCH-Anfragetext, für den angegeben ist, dass er JSON in der Anfragekopfzeile „Inhaltstyp“ enthält, der jedoch JSON-Parsing-Fehler enthält. Dies hängt häufig mit einem Programmierfehler oder einer automatisierten oder schädlichen Anfrage zusammen. |
| MALFORMED-DATA | Fehlerhafte Daten im Anfrageinhalt | Ein POST-, PUT- oder PATCH-Anfrageinhalt, der gemäß der Anfragekopfzeile „Inhaltstyp“ fehlerhaft ist. Wenn beispielsweise eine Anfragekopfzeile „Content-Type: application/x-www-form-urlencoded“ angegeben ist und ein POST-Hauptteil vorliegt, der JSON ist. Dies ist häufig ein Programmierfehler, eine automatisierte oder schädliche Anfrage. Erfordert Agent 3.2 oder höher. |
| SANS | Schädlicher IP-Traffic | [SANS Internet Storm Center](https://isc.sans.edu/): Liste der gemeldeten IP-Adressen, die in Verbindung mit bösartigen Aktivitäten stehen. |
| NO-CONTENT-TYPE | Fehlende Anfragekopfzeile „Content-Type“ | Eine Anfrage vom Typ POST, PUT oder PATCH, die keine Anfragekopfzeile vom Typ „Content-Type“ enthält. Standardmäßig sollten Anwendungs-Server in diesem Fall von „Content-Type: text/plain; charset=us-ascii“ ausgehen. Bei vielen automatisierten und böswilligen Anfragen fehlt möglicherweise „Content-Type“. |
| NOUA | Kein Benutzeragent | Gibt an, dass eine Anforderung keine „Benutzeragent“-Kopfzeile enthält bzw. dass der Kopfzeilenwert nicht festgelegt wurde. |
| TORNODE | Tor-Traffic | Tor ist eine Software, die die Identität einer Benutzerin oder eines Benutzers verschleiert. Eine Spitze im Tor-Traffic kann darauf hinweisen, dass eine angreifende Person versucht, ihren Standort zu verschleiern. |
| NULLBYTE | Null-Byte | Null-Bytes werden normalerweise nicht in einer Anfrage angezeigt und weisen darauf hin, dass die Anfrage falsch formatiert ist und möglicherweise schädlich ist. |
| PRIVATEFILE | Private Dateien | Private Dateien sind vertraulich, wie z. B. eine Apache `.htaccess`-Datei oder eine Konfigurationsdatei, der vertrauliche Informationen entnommen werden könnten. |
| SCANNER | Scanner | Identifiziert beliebte Scan-Dienste und -Werkzeuge. |
| RESPONSESPLIT | HTTP-Antwortaufteilung | Gibt an, wann CRLF-Zeichen als Eingabe an die Anwendung gesendet werden, um Kopfzeilen in die HTTP-Antwort einzufügen. |
| XML-ERROR | XML-Codierungsfehler | Ein POST-, PUT- oder PATCH-Anfrageinhalt, für den in der Anfragekopfzeile angegeben wird, dass der „Content-Type“ XML enthält, der jedoch XML-Parsing-Fehler aufweist. Dies hängt häufig mit einem Programmierfehler oder einer automatisierten oder schädlichen Anfrage zusammen. |
| DATACENTER | Rechenzentrum | Identifiziert die Anfrage als die eines bekannten Hosting-Anbieters. Diese Art von Traffic wird normalerweise nicht mit echten Endbenutzenden verbunden. |


## Überlegungen {#considerations}

* Wenn zwei in Konflikt stehende Regeln erstellt werden, haben die Zulassungsregeln immer Vorrang vor den Blockierungsregeln. Wenn Sie beispielsweise eine Regel erstellen, die einen bestimmten Pfad blockiert, und eine Regel, die eine bestimmte IP-Adresse zulässt, sind Anfragen von dieser IP-Adresse auf dem blockierten Pfad zulässig.

* Wenn eine Regel abgeglichen und blockiert wird, antwortet das CDN mit einem `406`-Rückgabe-Code.

* Die Konfigurationsdateien sollten keine Geheimnisse enthalten, da sie von allen Benutzenden gelesen werden können, die Zugriff auf das Git-Repository haben.

* In Cloud Manager definierte IP-Zulassungslisten haben Vorrang vor Traffic-Filterregeln.

* Übereintimmungen für eine WAF-Regel erscheinen nur in CDN-Protokollen bei Fehlschlägen und Durchgängen von CDN, nicht jedoch bei Treffern.

## Regelbeispiele {#examples}

Es folgen einige Regelbeispiele. Weitere Informationen zu Beispielen für Ratenbegrenzungsregeln finden Sie weiter unten im Abschnitt [Ratenbegrenzung](#rate-limit-rules).

**Beispiel 1**

Diese Regel blockiert Anfragen von der **IP 192.168.1.1**:

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

Diese Regel blockiert Anfragen auf dem Pfad `/helloworld` bei Veröffentlichung mit einem Benutzeragenten, der Chrome umfasst:

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

Diese Regel blockiert Anfragen bei der Veröffentlichung, die den Abfrageparameter `foo` enthalten, erlaubt jedoch jede Anfrage von der IP 192.168.1.1:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
      - name: "block-request-that-contains-query-parameter-foo"
        when:
          allOf:
            - { queryParam: url-param, equals: foo }
            - { reqProperty: tier, equals: publish }
        action:
          type: block
      - name: "allow-all-requests-from-ip"
        when: { reqProperty: clientIp, equals: 192.168.1.1 }
        action:
          type: allow
```

**Beispiel 4**

Diese Regel blockiert Anfragen bei der Veröffentlichung an den Pfad `/block-me` und blockiert alle Anfragen, die mit einem `SQLI`- oder `XSS`-Muster übereinstimmen. Dieses Beispiel enthält eine WAF-Traffic-Filterregel, die auf [WAF-Flags](#waf-flags-list) `SQLI` und `XSS` verweist und daher eine separate Lizenz erfordert.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
      - name: "path-rule"
        when:
          allOf:
            - { reqProperty: path, equals: /block-me }
            - { reqProperty: tier, equals: publish }
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

## Ratenbegrenzungsregeln

Manchmal ist es wünschenswert, Traffic zu blockieren, wenn er eine bestimmte Rate eingehender Anfragen überschreitet, basierend auf einer bestimmten Bedingung. Wenn Sie einen Wert für die Eigenschaft `rateLimit` festlegen, wird die Rate der Anfragen, die mit der Regelbedingung übereinstimmen, begrenzt.

Ratenbegrenzungsregeln können nicht auf WAF-Flags verweisen. Sie stehen allen Kundinnen und Kunden von Sites und Forms zur Verfügung.

Die Ratenbegrenzungen werden pro CDN-POP berechnet. Nehmen wir zum Beispiel an, dass die POPs in Montreal, Miami und Dublin eine Traffic-Rate von 80, 90 bzw. 120 Anfragen pro Sekunde haben. Außerdem ist die Regel zur Begrenzung der Rate auf einen Grenzwert von 100 festgelegt. In diesem Fall würde nur der Traffic nach Dublin begrenzt.

Ratenbegrenzungen werden entweder anhand von Traffic bewertet, der am Edge ankommt bzw. der am Ursprung ankommt, oder anhand der Anzahl der Fehler.

### rateLimit-Struktur {#ratelimit-structure}

| **Eigenschaft** | **Typ** | **Standard** | **BEDEUTUNG** |
|---|---|---|---|
| limit | Ganzzahl von 10 bis 10.000 | erforderlich | Anfragerate (pro CDN-POP) in Anfragen pro Sekunde, für die die Regel ausgelöst wird. |
| window | Ganzzahl: 1, 10 oder 60 | 10 | Stichprobenfenster in Sekunden, für das die Anfragerate berechnet wird. Die Genauigkeit der Zähler hängt von der Größe des Fensters ab (ein größeres Fenster liefert höhere Genauigkeit). Beispielsweise kann man für das 1-Sekunden-Fenster eine Genauigkeit von 50 % und für das 60-Sekunden-Fenster eine Genauigkeit von 90 % erwarten. |
| penalty | Ganzzahl von 60 bis 3600 | 300 (5 Minuten) | Ein Zeitraum in Sekunden, für den übereinstimmende Anfragen blockiert werden (auf die nächste Minute gerundet). |
| Anzahl | alle, Abrufe, Fehler | alle | wird basierend auf Traffic am Edge (alle), Ursprungs-Traffic (Abrufe) oder der Anzahl der Fehler (Fehler) bewertet. |
| groupBy | array[Getter] | keine | Der Zähler der Ratenbegrenzer wird durch eine Reihe von Anfrageeigenschaften aggregiert (z. B. clientIp). |

### Beispiele {#ratelimiting-examples}

**Beispiel 1**

Diese Regel blockiert einen Client für 5 Millisekunden, wenn er in den letzten 10 Sekunden durchschnittlich 60 Anfragen/Sek. (pro CDN-POP) überschreitet:

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
        count: all
        groupBy:
          - reqProperty: clientIp
      action: block
```

**Beispiel 2**

Blockiert Anfragen für 60 Sekunden für den Pfad „/critical/resource“, wenn in einem Zeitfenster von zehn Sekunden durchschnittlich 100 Anfragen pro Sekunde an den Ursprung (pro CDN-POP) überschritten werden:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
      - name: rate-limit-example
        when:
          allOf:
            - { reqProperty: path, equals: /critical/resource }
            - { reqProperty: tier, equals: publish }
        action:
          type: block
        rateLimit: { limit: 100, window: 10, penalty: 60, count: fetches }
```

## CVE-Regeln {#cve-rules}

Wenn WAF lizenziert ist, wendet Adobe automatisch Blockierungsregeln an, um vor vielen bekannten CVEs (Common Vulnerabilities and Exposures) zu schützen, und neue CVEs können kurz nach ihrer Entdeckung hinzugefügt werden. Kundinnen und Kunden sollten CVE-Regeln nicht selbst konfigurieren und brauchen es auch nicht.

Wenn eine Traffic-Anfrage einer CVE entspricht, wird sie im entsprechenden CDN-Protokolleintrag angezeigt.

Wenden Sie sich an den Adobe-Support, wenn Sie Fragen zu einer bestimmten CVE haben oder wenn eine bestimmte CVE-Regel vorliegt, die Ihre Organisation deaktivieren möchte.

## Warnhinweise für Traffic-Filterregeln {#traffic-filter-rules-alerts}

Eine Regel kann so konfiguriert werden, dass eine Benachrichtigung des Aktionszentrums gesendet wird, wenn sie innerhalb eines 5-minütigen Fensters zehnmal ausgelöst wird. Eine solche Regel warnt Sie, wenn bestimmte Traffic-Muster auftreten, sodass Sie die erforderlichen Maßnahmen treffen können. Sobald ein Warnhinweis für eine bestimmte Regel ausgelöst wurde, wird er erst am nächsten Tag (UTC) wieder ausgelöst.

Erfahren Sie mehr über das [Aktionszentrum](/help/operations/actions-center.md), einschließlich der Einrichtung der erforderlichen Benachrichtigungsprofile für den Empfang von E-Mails.

![Benachrichtigung des Aktionszentrums](/help/security/assets/traffic-filter-rules-actions-center-alert.png)


Die Eigenschaft „Warnhinweis“ kann für alle Aktionstypen (allow, block, log) auf den Knoten „Aktion“ angewendet werden.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
    rules:
      - name: "path-rule"
        when:
          allOf:
            - { reqProperty: path, equals: /block-me }
            - { reqProperty: tier, equals: publish }
        action:
          type: block
          alert: true
```

## Standard-Warnhinweis zu Traffic-Spitze am Ursprung {#traffic-spike-at-origin-alert}

Eine E-Mail-Benachrichtigung des [Aktionszentrums](/help/operations/actions-center.md) wird gesendet, wenn eine signifikante Menge an Traffic zum Ursprung gesendet wird, bei der eine hohe Anzahl von Anfragen von derselben IP-Adresse kommt, was auf einen DDoS-Angriff hindeutet.

Wenn dieser Schwellenwert erreicht wird, blockiert Adobe den Traffic von dieser IP-Adresse. Es wird jedoch empfohlen, zusätzliche Maßnahmen zu ergreifen, um Ihren Ursprung zu schützen, einschließlich der Konfiguration von Traffic-Filterregeln zur Ratenbegrenzung, um Traffic-Spitzen bei niedrigeren Schwellenwerten zu blockieren. Weitere Informationen finden Sie im [Tutorial zum Blockieren von DoS- und DDoS-Angriffen mithilfe von Traffic-Regeln](#tutorial-blocking-DDoS-with-rules), das Sie durch die einzelnen Schritte führt.

Dieser Warnhinweis ist standardmäßig aktiviert, kann aber durch Festlegen der Eigenschaft *defaultTrafficAlerts* auf „falsch“ deaktiviert werden. Sobald der Warnhinweis ausgelöst wurde, wird er erst wieder am nächsten Tag (UTC) ausgelöst.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  trafficFilters:
   defaultTrafficAlerts: false
```

## CDN-Protokolle {#cdn-logs}

AEM as a Cloud Service bietet Zugriff auf CDN-Protokolle, die für Anwendungsfälle nützlich sind, einschließlich der Optimierung der Cache-Trefferquote und der Konfiguration von Traffic-Filterregeln. CDN-Protokolle werden im Cloud Manager-Dialog **Protokolle herunterladen** angezeigt, wenn Sie den Author- oder Publish-Service auswählen.

CDN-Protokolle können sich bis zu fünf Minuten verzögern.

Die Eigenschaft `rules` beschreibt, welche Traffic-Filterregeln übereinstimmen, und weist folgendes Muster auf:

```
"rules": "match=<matching-customer-named-rules-that-are-matched>,waf=<matching-WAF-rules>,action=<action_type>"
```

Beispiel:

```
"rules": "match=Block-Traffic-under-private-folder,Enable-SQL-injection-everywhere,waf="SQLI,SANS",action=block"
```

Die Regeln verhalten sich wie folgt:

* Der auf Kundenseite deklarierte Regelname aller übereinstimmenden Regeln wird im Attribut `match` aufgeführt.
* Das Attribut `action` bestimmt, ob die Regeln etwas blockieren, erlauben oder protokollieren.
* Wenn die WAF lizenziert und aktiviert ist, listet das Attribut `waf` alle WAF-Flags (z. B. SQLI) auf, die entdeckt wurden. Dies gilt unabhängig davon, ob die WAF-Flags in Regeln aufgeführt wurden. Dies soll Aufschluss über potenzielle neue Regeln geben, die deklariert werden können.
* Wenn keine auf Kundenseite deklarierten Regeln übereinstimmen und keine WAF-Regeln übereinstimmen, ist die Eigenschaft `rules` leer.

Wie bereits erwähnt, erscheinen Übereinstimmungen für eine WAF-Regel nur in CDN-Protokollen für Fehlschläge und Durchgänge von CDN, nicht jedoch für Treffer.

Das folgende Beispiel zeigt eine beispielhafte `cdn.yaml` und zwei CDN-Protokolleinträge:


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
| *timestamp* | Der Zeitpunkt, zu dem die Anfrage nach der TLS-Beendigung gestartet wurde. |
| *ttfb* | Abkürzung für *Time To First Byte*. Das Zeitintervall vom Start der Anfrage bis zu dem Punkt, an dem das Streamen des Antworttexts begann. |
| *cli_ip* | Die Client-IP-Adresse. |
| *cli_country* | Der Alpha-2-Ländercode gemäß [ISO 3166-1](https://de.wikipedia.org/wiki/ISO_3166-1) mit zwei Buchstaben für das Client-Land. |
| *rid* | Der Wert der Anfragekopfzeile, der zur eindeutigen Identifizierung der Anfrage verwendet wird. |
| *req_ua* | Der Benutzeragent, der für die Ausführung einer bestimmten HTTP-Anfrage verantwortlich ist. |
| *host* | Die Stelle, für die die Anfrage bestimmt ist. |
| *url* | Der vollständige Pfad, einschließlich Abfrageparametern. |
| *Methode* | Die vom Client gesendete HTTP-Methode, z. B. „GET“ oder „POST“. |
| *res_ctype* | Der Content-Typ, der den ursprünglichen Medientyp der Ressource angibt. |
| *cache* | Der Status des Caches. Mögliche Werte sind HIT, MISS oder PASS |
| *status* | Der HTTP-Status-Code als ganzzahliger Wert. |
| *res_age* | Die Zeit in Sekunden, für die eine Antwort zwischengespeichert wurde (in allen Knoten). |
| *pop* | das Rechenzentrum des CDN-Cache-Servers. |
| *rules* | Der Name aller übereinstimmenden Regeln.<br><br>Gibt auch an, ob die Übereinstimmung zu einer Blockierung führte. <br><br>Beispiel: „`match=Enable-SQL-Injection-and-XSS-waf-rules-globally,waf=SQLI,action=blocked`“ <br><br>Leer, wenn keine Regeln übereinstimmten. |

## Dashboard-Tools {#dashboard-tooling}

Adobe bietet einen Mechanismus zum Herunterladen von Dashboard-Tools auf Ihren Computer, um CDN-Protokolle zu erfassen, die über Cloud Manager heruntergeladen wurden. Mit diesen Tools können Sie Ihren Traffic analysieren, um die entsprechenden Traffic-Filterregeln zu finden, die deklariert werden können, einschließlich WAF-Regeln.

Dashboard-Tools können direkt aus dem GitHub-Repository [AEMCS-CDN-Log-Analysis-Tooling](https://github.com/adobe/AEMCS-CDN-Log-Analysis-Tooling) heruntergeladen werden.

Für konkrete Anweisungen zum Verwenden der Dashboard-Tools verfügbar sind [Tutorials](#tutorial) verfügbar.

## Empfohlene Anfangsregeln {#recommended-starter-rules}

Sie können für den Anfang die folgenden empfohlenen Regeln in Ihre `cdn.yaml` kopieren. Starten Sie im Protokollmodus, analysieren Sie Ihren Traffic und wechseln Sie, wenn Sie zufrieden sind, in den Blockierungsmodus. Sie können die Regeln auf Grundlage der einzigartigen Merkmale des Live-Traffics Ihrer Website ändern.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev", "stage", "prod"]
data:
  trafficFilters:
    rules:
    #  Block client for 5m when it exceeds an average of 100 req/sec to origin on a time window of 10sec
    - name: limit-origin-requests-client-ip
      when:
        reqProperty: tier
        equals: 'publish'
      rateLimit:
        limit: 100
        window: 10
        count: fetches
        penalty: 300
        groupBy:
          - reqProperty: clientIp
      action: log
    #  Block client for 5m when it exceeds an average of 500 req/sec on a time window of 10sec
    - name: limit-requests-client-ip
      when:
        reqProperty: tier
        equals: 'publish'
      rateLimit:
        limit: 500
        window: 10
        count: all
        penalty: 300
        groupBy:
          - reqProperty: clientIp
      action: log
    # Block requests coming from OFAC countries
    - name: block-ofac-countries
      when:
        allOf:
          - { reqProperty: tier, in: ["author", "publish"] }
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
    # Enable recommended WAF protections (only works if WAF is licensed enabled for your environment)
    - name: block-waf-flags-globally
      when:
        reqProperty: tier
        in: ["author", "publish"]
      action:
        type: log
        wafFlags:
          - TRAVERSAL
          - CMDEXE-NO-BIN
          - XSS
          - LOG4J-JNDI
          - BACKDOOR
          - USERAGENT
          - SQLI
          - SANS
          - TORNODE
          - NOUA
          - SCANNER
          - PRIVATEFILE
          - NULLBYTE
```

## Tutorials {#tutorial}

Zwei Tutorials sind verfügbar.

### Schutz von Websites mit Traffic-Filterregeln (einschließlich WAF-Regeln) {#tutorial-protecting-websites}

[Arbeiten Sie ein Tutorial durch](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/security/traffic-filter-and-waf-rules/overview), um allgemeine, praktische Kenntnisse und Erfahrungen im Zusammenhang mit Traffic-Filterregeln zu sammeln, einschließlich WAF-Regeln.

Das Tutorial führt Sie durch folgende Themen:

* Einrichten der Konfigurations-Pipeline für Cloud Manager
* Verwenden von Tools zur Simulation von schädlichem Traffic
* Definieren von Traffic-Filterregeln, einschließlich WAF-Regeln
* Analyse von Ergebnissen mit Dashboard-Tools
* Best Practices

### Blockieren von DoS- und DDoS-Angriffen mithilfe von Traffic-Filterregeln {#tutorial-blocking-DDoS-with-rules}

[Umfassende Informationen zum Blockieren](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/security/blocking-dos-attack-using-traffic-filter-rules) von DoS- (Denial of Service) und DDoS-Angriffen (Distributed Denial of Service) mithilfe von Traffic-Filterregeln mit Ratenbegrenzungen und anderen Strategien.

Das Tutorial führt Sie durch folgende Themen:

* Grundlegendes zum Schutz
* Erhalten von Warnungen beim Überschreiten von Ratenbegrenzungen
* Analysieren von Traffic-Mustern mithilfe von Dashboard-Tools, um Schwellenwerte für Traffic-Filterregeln mit Ratenbegrenzungen zu konfigurieren



