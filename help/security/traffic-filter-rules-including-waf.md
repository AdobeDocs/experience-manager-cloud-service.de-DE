---
title: Traffic-Filterregeln, einschließlich WAF-Regeln
description: Konfigurieren von Traffic-Filterregeln, einschließlich WAF-Regeln (Web Application Firewall).
exl-id: 6a0248ad-1dee-4a3c-91e4-ddbabb28645c
feature: Security
role: Admin
source-git-commit: 199c11b6f6655f9a0c790501b0aa554119ea0998
workflow-type: tm+mt
source-wordcount: '4257'
ht-degree: 69%

---


# Traffic-Filterregeln, einschließlich WAF-Regeln {#traffic-filter-rules-including-waf-rules}

Traffic-Filterregeln blockieren oder erlauben Anfragen auf CDN-Ebene. Dies ist in Szenarien wie den folgenden nützlich:

* Beschränken des Zugriffs auf bestimmte Domains auf den internen Unternehmens-Traffic, bevor eine neue Site live geschaltet wird
* Um weniger anfällig für volumetrische DoS-Angriffe zu sein, richten Sie Ratenbeschränkungen ein.
* Verhindern, dass Ihre Seiten von bekannten bösartigen IP-Adressen angesprochen werden.

Viele dieser Traffic-Filterregeln stehen allen Kundinnen und Kunden von AEM as a Cloud Service Sites und Forms zur Verfügung. Als *Standard-Traffic-Filterregeln* werden sie für Anfrageeigenschaften verwendet: IP, Hostname, Pfad und Benutzeragent. Standard-Traffic-Filterregeln umfassen Ratenbegrenzungsregeln zum Schutz vor Traffic-Spitzen.

Eine Unterkategorie von Traffic-Filterregeln erfordert entweder eine Lizenz für erweiterte Sicherheit (früher WAF-DDoS-Schutz genannt) oder für erweiterte Sicherheit für das Gesundheitswesen (früher Enhanced Security genannt). Diese leistungsstarken Regeln werden als Traffic-Filterregeln für WAF (Web Application Firewall) (oder *WAF-Regeln*) bezeichnet und haben Zugriff auf die [WAF-Flags](#waf-flags-list) die weiter unten in diesem Artikel beschrieben werden.

Traffic-Filterregeln können über Cloud Manager-Konfigurations-Pipelines in Entwicklungs-, Staging- und Produktionsumgebungen bereitgestellt werden. Die Konfigurationsdatei kann mithilfe von Befehlszeilenprogrammen in schnellen Entwicklungsumgebungen (Rapid Development Environments, RDEs) bereitgestellt werden.

Um sich schnell mit dieser Funktion vertraut zu machen, [&#x200B; Sie ein Tutorial &#x200B;](#tutorial).

>[!NOTE]
>Weitere Konfigurationsoptionen für CDN-Traffic - z. B. das Bearbeiten von Anfragen/Antworten, das Deklarieren von Weiterleitungen und das Weiterleiten von Proxys an Nicht-AEM-Absender - finden Sie im Artikel [Konfigurieren von Traffic im CDN](/help/implementing/dispatcher/cdn-configuring-traffic.md) .


## Organisation dieses Artikels {#how-organized}

Dieser Artikel ist in die folgenden Abschnitte unterteilt:

* **Traffic-Schutz – Übersicht:** Erfahren Sie, wie Sie vor schädlichem Traffic geschützt werden.
* **Empfohlener Prozess zum Konfigurieren von Regeln:** Erfahren Sie mehr über allgemeine Methoden zum Schutz Ihrer Website.
* **Setup:** Erfahren Sie, wie Sie Traffic-Filterregeln, einschließlich der erweiterten WAF-Regeln, einrichten, konfigurieren und bereitstellen.
* **Regelsyntax:** Erfahren Sie, wie Sie Traffic-Filterregeln in der Konfigurationsdatei von `cdn.yaml` deklarieren. Dazu gehören sowohl die Traffic-Filterregeln, die für alle Kundinnen und Kunden von Sites und Forms verfügbar sind, als auch die Unterkategorie der WAF-Regeln für diejenigen, die diese Funktion lizenzieren.
* **Regelbeispiele:** Informationen zu den ersten Schritten finden Sie unter Beispiele für deklarierte Regeln.
* **Ratenbegrenzungsregeln:** Erfahren Sie, wie Sie Regeln zur Ratenbegrenzung verwenden, um Ihre Site vor Angriffen mit hohem Volumen zu schützen.
* **Warnhinweise zu Traffic-Filterregeln:** Konfigurieren Sie Warnhinweise, die benachrichtigt werden sollen, wenn Ihre Regeln ausgelöst werden.
* **Standard-Traffic-Spitze bei Ursprungs-Warnhinweis:** Benachrichtigung erhalten, wenn ein Anstieg des Traffics am Ursprung auf einen DDoS-Angriff hinweist.
* **CDN-Protokolle:** Erfahren Sie, welche deklarierten Regeln und WAF-Flags mit Ihrem Traffic übereinstimmen.
* **Dashboard-Tooling:** Analysieren Sie Ihre CDN-Protokolle, um neue Traffic-Filterregeln zu erstellen.
* **Empfohlene Anfangsregeln:** Ein Regelsatz für die ersten Schritte.
* **Tutorial:** Informationen über die Funktion, einschließlich der Verwendung von Dashboard-Tools zum Deklarieren der entsprechenden Regeln.

## Übersicht über den Traffic-Schutz {#traffic-protection-overview}

In der aktuellen digitalen Landschaft stellt schädlicher Traffic eine immer präsente Bedrohung dar. Adobe ist sich der Ernsthaftigkeit des Risikos bewusst und bietet verschiedene Ansätze zum Schutz von Kundenanwendungen und zur Eindämmung von Angriffen.

Am Edge absorbiert das von Adobe verwaltete CDN DoS-Angriffe auf der Netzwerkschicht (Ebene 3 und 4), einschließlich Angriffe durch Überschwemmung oder Reflexion/Verstärkung.

Adobe ergreift standardmäßig Maßnahmen, um eine Leistungsbeeinträchtigung durch unerwartet hohes Traffic-Aufkommen über einen bestimmten Schwellenwert hinaus zu verhindern. Im Falle eines DoS-Angriffs, der die Verfügbarkeit der Website beeinträchtigt, werden die Betriebs-Teams von Adobe benachrichtigt und Maßnahmen zur Eindämmung des Problems ergriffen.

Kunden ergreifen proaktive Maßnahmen, um Angriffe auf Anwendungsebene (Ebene 7) abzuschwächen, indem sie Regeln auf verschiedenen Ebenen des Inhaltsbereitstellungsflusses konfigurieren.

Auf der Apache-Ebene konfigurieren Kunden beispielsweise entweder das [Dispatcher-Modul](https://experienceleague.adobe.com/de/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration#configuring-access-to-content-filter) oder [ModSecurity](https://experienceleague.adobe.com/de/docs/experience-manager-learn/foundation/security/modsecurity-crs-dos-attack-protection), um den Zugriff auf bestimmte Inhalte zu beschränken.

In diesem Artikel wird beschrieben, wie Traffic-Filterregeln mithilfe der Cloud Manager-Pipelines (config[&#x200B; für das von Adobe verwaltete CDN bereitgestellt &#x200B;](/help/operations/config-pipeline.md). Neben *Standard-Traffic-Filterregeln* (IP, Pfad, Kopfzeilen, Ratenbeschränkungen) lizenzieren Kunden *WAF-Regeln*.

## Vorgeschlagener Prozess {#suggested-process}

Im Folgenden finden Sie einen allgemeinen empfohlenen End-to-End-Prozess zur Bestimmung der richtigen Traffic-Filterregeln:

1. Konfigurieren Sie Konfigurations-Pipelines für Nicht-Produktion und Produktion, wie im Abschnitt [Einrichtung](#setup) beschrieben.
1. Kunden, die die *Traffic-Filterregeln für WAF lizenziert haben* aktivieren sie in Cloud Manager.

   >[!IMPORTANT]
   >
   >Regeln für die Lizenzierung von WAF aktivieren sie nicht. Die Funktion bleibt inaktiv, bis **WAF-DDOS Protection** auf der Registerkarte **Security** in Cloud Manager aktiviert ist.

1. Lesen und absolvieren Sie das Tutorial, um zu verstehen, wie Sie Traffic-Filterregeln verwenden, einschließlich WAF-Regeln, wenn sie lizenziert wurden. Das Tutorial führt Sie durch die Bereitstellung von Regeln in einer Entwicklungsumgebung, die Simulation von schädlichem Traffic sowie den Download der [CDN-Protokolle](#cdn-logs) und ihre Analyse in den [Dashboard-Tools](#dashboard-tooling).
1. Kopieren Sie die empfohlenen Anfangsregeln nach `cdn.yaml` und stellen Sie die Konfiguration mit einigen der Regeln in der Produktionsumgebung im Protokollmodus bereit.
1. Nachdem Sie etwas Traffic erfasst haben, analysieren Sie die Ergebnisse mit den [Dashboard-Tools](#dashboard-tooling), um zu sehen, ob es Übereinstimmungen gab. Achten Sie auf falsch-positive Ergebnisse und nehmen Sie die erforderlichen Anpassungen vor, um letztendlich alle Starterregeln im Blockmodus zu aktivieren.
1. Fügen Sie bei Bedarf benutzerdefinierte Regeln hinzu, die auf der Analyse der CDN-Protokolle basieren. Testen Sie sie zunächst mit simuliertem Traffic in Entwicklungsumgebungen, bevor Sie sie in der Staging- und Produktionsumgebung im Protokollmodus und dann im Blockmodus bereitstellen.
1. Überwachen Sie den Traffic auf fortlaufender Basis und nehmen Sie Änderungen an den Regeln vor, wenn sich die Bedrohungslage weiterentwickelt.

## Einrichtung {#setup}

1. Erstellen Sie eine Datei `cdn.yaml` mit einer Reihe von Traffic-Filterregeln, einschließlich WAF-Regeln. Beispiel:

   ```
   kind: "CDN"
   version: "1"
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


1. Wenn WAF-Regeln lizenziert sind *müssen Sie* Funktion in Cloud Manager aktivieren. Lizenzierte WAF-Regeln sind nicht aktiv und bieten keinen Schutz, bis **WAF-DDOS-Schutz** aktiviert ist. Aktivieren Sie die Funktion sowohl für das neue als auch für das vorhandene Programmszenario, wie im Folgenden beschrieben:

   1. Um WAF in einem neuen Programm zu konfigurieren, aktivieren Sie das Kontrollkästchen **WAF-DDOS-Schutz** auf der Registerkarte **Sicherheit**, wenn Sie [ein Produktionsprogramm erstellen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md).

   1. Um WAF für ein vorhandenes Programm zu konfigurieren, [&#x200B; Sie „Programm bearbeiten](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md). Aktivieren Sie auf der **Sicherheit** die Option **WAF-DDOS-Schutz**, um die Funktion zu aktivieren, oder deaktivieren Sie sie, um die Funktion zu deaktivieren. Sie können diese Einstellung jederzeit ändern.

      Um zu bestätigen, dass die Funktion *aktiv* ist, nachdem Sie sie aktiviert haben, überprüfen Sie die [CDN-](#cdn-logs), sobald Traffic auf die Site fließt. Suchen Sie nach Protokolleinträgen, die eine `rules`-Eigenschaft mit einem `waf` enthalten. Beispiel:

      `"rules": "waf=SQLI" `

      Dieses Attribut wird angezeigt, sobald WAF aktiv ist, sogar bevor WAF-Regeln bereitgestellt werden.

1. Erstellen Sie in Cloud Manager eine Konfigurations-Pipeline. Folgen Sie dabei den Anweisungen im [Artikel zu Konfigurations-Pipelines](/help/operations/config-pipeline.md#managing-in-cloud-manager). Die Pipeline verweist auf einen `config` der obersten Ebene, wobei die `cdn.yaml` irgendwo unten abgelegt ist, siehe [Verwenden von Konfigurations-Pipelines](/help/operations/config-pipeline.md#folder-structure).

## Syntax von Traffic-Filterregeln {#rules-syntax}

Um Muster wie IP, Benutzeragent, Kopfzeilen, Hostname, Geografie oder URL abzugleichen, können Sie *Traffic-Filterregeln* konfigurieren.

Kunden mit einer Lizenz für erweiterte Sicherheit oder erweiterte Sicherheit für das Gesundheitswesen konfigurieren *WAF-Regeln* die auf [WAF-Flags &#x200B;](#waf-flags-list).

Im Folgenden finden Sie ein Beispiel für einen Satz von Traffic-Filterregeln, der auch eine WAF-Regel enthält.

```
kind: "CDN"
version: "1"
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
| wenn | X | X | `Condition` | - | Die grundlegende Struktur ist:<br><br>`{ <getter>: <value>, <predicate>: <value> }`<br><br>Siehe [Bedingungsstruktur](/help/implementing/dispatcher/cdn-configuring-traffic.md#condition-structure) unter „Konfigurieren von *im CDN* für Getter, Prädikate und die Kombination mehrerer Bedingungen. |
| Aktion | X | X | `Action` | protokollieren | protokollieren, zulassen, blockieren oder Aktionsobjekt. Standard ist „protokollieren“ |
| rateLimit | X |   | `RateLimit` | nicht definiert | Ratenbegrenzungskonfiguration. Die Ratenbegrenzung ist deaktiviert, wenn sie nicht definiert ist.<br><br>Weiter unten finden Sie einen separaten Abschnitt mit einer Beschreibung der rateLimit-Syntax sowie Beispiele. |

### Aktionsstruktur {#action-structure}

Ein `action` kann entweder eine Zeichenfolge sein, die die Aktion angibt (Zulassen, Blockieren oder Protokollieren), oder ein Objekt, das sowohl aus dem Aktionstyp (Zulassen, Blockieren oder Protokollieren) als auch aus Optionen wie wafFlags und/oder dem Status besteht.

**Aktionstypen**

Aktionen werden entsprechend ihren Typen in der folgenden Tabelle priorisiert, die entsprechend der Reihenfolge sortiert ist, in der die Aktionen ausgeführt werden.

| **Name** | **Zulässige Eigenschaften** | **Bedeutung** |
|---|---|---|
| **allow** | `wafFlags` (optional), `alert` (optional) | Wenn wafFlags nicht vorhanden ist, stoppt die weitere Regelverarbeitung und es wird mit der Bereitstellung der Antwort fortgefahren. Wenn wafFlags vorhanden ist, deaktiviert dies die angegebenen WAF-Schutzmechanismen und fährt mit der weiteren Regelverarbeitung fort. <br>Falls ein Warnhinweis angegeben wird, wird eine Benachrichtigung des Aktionszentrums gesendet, wenn die Regel zehnmal innerhalb eines 5-minütigen Zeitfensters ausgelöst wird. Sobald ein Warnhinweis für eine bestimmte Regel ausgelöst wurde, wird er erst am nächsten Tag (UTC) wieder ausgelöst. |
| **block** | `status, wafFlags` (optional und sich gegenseitig ausschließend), `alert` (optional) | Wenn wafFlags nicht vorhanden ist, wird der HTTP-Fehler unter Umgehung aller anderen Eigenschaften zurückgegeben. Der Fehler-Code wird durch die Statuseigenschaft definiert bzw. standardmäßig auf 406 gesetzt. Wenn wafFlags vorhanden ist, ermöglicht dies bestimmte WAF-Schutzmaßnahmen und fährt mit der weiteren Regelverarbeitung fort. <br>Falls ein Warnhinweis angegeben wird, wird eine Benachrichtigung des Aktionszentrums gesendet, wenn die Regel zehnmal innerhalb eines 5-minütigen Zeitfensters ausgelöst wird. Sobald ein Warnhinweis für eine bestimmte Regel ausgelöst wurde, wird er erst am nächsten Tag (UTC) wieder ausgelöst. |
| **log** | `wafFlags` (optional), `alert` (optional) | protokolliert die Tatsache, dass die Regel ausgelöst wurde, hat jedoch ansonsten keine Auswirkung auf die Verarbeitung. wafFlags hat keine Auswirkung. <br>Falls ein Warnhinweis angegeben wird, wird eine Benachrichtigung des Aktionszentrums gesendet, wenn die Regel zehnmal innerhalb eines 5-minütigen Zeitfensters ausgelöst wird. Sobald ein Warnhinweis für eine bestimmte Regel ausgelöst wurde, wird er erst am nächsten Tag (UTC) wieder ausgelöst. |

### WAF Flags-Liste {#waf-flags-list}

Die `wafFlags` -Eigenschaft, die in den lizenzierbaren Traffic-Filterregeln von WAF verwendet wird, verweist auf Folgendes:

#### böswilliger Datenverkehr

| **Flag-ID** | **Flag-Name** | **Beschreibung** |
|---|---|---|
| ATTACK | Angriff | Eine Aggregation von Markierungen für bösartigen Traffic (SQLI, CMDEXE, XSS usw.). Im [Abschnitt „Empfohlene WAF-Regeln“](#recommended-waf-starter-rules) finden Sie weitere Informationen, wie diese Markierung effektiv verwendet werden kann. |
| ATTACK-FROM-BAD-IP | Angriff von bösartiger IP | Ähnlich wie die Markierung ATTACK, aber per „logischem UND“ mit der Markierung `BAD-IP` verknüpft, damit Anfragen gekennzeichnet werden, die sowohl für ATTACK als auch BAD-IP eine Übereinstimmung aufweisen. Im [Abschnitt „Empfohlene WAF-Regeln“](#recommended-waf-starter-rules) finden Sie weitere Informationen, wie diese Markierung effektiv verwendet werden kann. |
| SQLI | SQL-Injektion | SQL-Injektion ist der Versuch, durch die Ausführung beliebiger Datenbankabfragen Zugriff auf eine Anwendung zu erhalten oder privilegierte Informationen zu erhalten. |
| BACKDOOR | Backdoor | Ein Backdoor-Signal ist eine Anfrage, die versucht festzustellen, ob eine gemeinsame Backdoor-Datei auf dem System vorhanden ist. |
| CMDEXE | Befehlsausführung | Befehlsausführung ist der Versuch, durch beliebige Systembefehle mithilfe von Benutzereingaben die Kontrolle über ein Zielsystem zu erlangen oder ein Zielsystem zu beschädigen. |
| CMDEXE-NO-BIN | Befehlsausführung, außer für `/bin/` | Gewährleisten Sie das gleiche Schutzniveau wie `CMDEXE`, während falsch positive Ergebnisse für `/bin` aufgrund der AEM-Architektur deaktiviert werden. |
| XSS | Cross-Site-Scripting | Cross-Site-Scripting ist der Versuch, das Konto einer Benutzerin oder eines Benutzers oder die Webbrowsing-Sitzung durch schädlichen JavaScript-Code zu ersetzen. |
| DURCHLAUF | Verzeichnisdurchlauf | Verzeichnisdurchlauf ist der Versuch, in einem System durch privilegierte Ordner zu navigieren, in der Hoffnung, vertrauliche Informationen zu erhalten. |
| USERAGENT | Angriffs-Tooling | Angriffs-Tooling ist der Einsatz automatisierter Software zur Identifizierung von Sicherheitslücken oder zum Versuch, eine entdeckte Anfälligkeit auszunutzen. |
| LOG4J-JNDI | Log4J JNDI | Log4J JNDI-Angriffe versuchen, die [Log4Shell-Anfälligkeit](https://en.wikipedia.org/wiki/Log4Shell) in Log4J-Versionen vor 2.16.0 auszunutzen. |
| CVE | CVE | Markierung zur Identifizierung eines CVE. Wird immer mit einer `CVE-<CVE Number>`-Markierung kombiniert. Wenden Sie sich an Adobe, um mehr darüber zu erfahren, vor welchen CVEs Adobe Sie schützt. |

#### Verdächtiger Traffic

| **Flag-ID** | **Flag-Name** | **Beschreibung** |
|---|---|---|
| ABNORMALPATH | Anormaler Pfad | Anormaler Pfad bedeutet, dass der ursprüngliche Pfad vom normalisierten Pfad abweicht (z. B. `/foo/./bar` wird normalisiert in `/foo/bar`) |
| BAD-IP | Bösartige IP | Identifiziert Anfragen, die von IP-Adressen stammen, von denen bekannt ist, dass sie bösartig sind, entweder aufgrund der Aufnahme in Datensätze wie `SANS` und `TORNODE` oder aufgrund einer vorherigen Erkennung von bösartigem Verhalten durch die WAF |
| BHH | Bad Hop Headers | Bad Hop Headers weisen auf einen HTTP-Schmuggelversuch durch einen fehlerhaften Transfer-Encoding (TE)- oder Content-Length(CL)-Header oder einen korrekt formatierten TE- und CL-Header hin. |
| CODEINJECTION | Code-Injektion | Code-Injektion ist der Versuch, über beliebige Anwendungs-Code-Befehle mittels Benutzereingaben die Kontrolle über ein Zielsystem zu erlangen oder es zu beschädigen. |
| COMPRESSED | Komprimierung erkannt | Der POST-Anfragetext ist komprimiert und kann nicht überprüft werden. Das trifft zu, wenn beispielsweise ein `Content-Encoding: gzip`-Anfrage-Header angegeben ist und der POST-Text normaler Text ist. |
| RESPONSESPLIT | HTTP-Antwortaufteilung | Gibt an, wann CRLF-Zeichen als Eingabe an die Anwendung gesendet werden, um Kopfzeilen in die HTTP-Antwort einzufügen. |
| NOTUTF8 | Ungültige Codierung | Eine ungültige Codierung kann dazu führen, dass der Server böswillige Zeichen aus einer Anfrage in eine Antwort übersetzt, was entweder zu einer Dienstverweigerung oder zu XSS führt |
| MALFORMED-DATA | Fehlerhafte Daten im Anfrageinhalt | Ein POST-, PUT- oder PATCH-Anfrageinhalt, der gemäß der Anfragekopfzeile „Inhaltstyp“ fehlerhaft ist. Wenn beispielsweise eine Anfragekopfzeile „Content-Type: application/x-www-form-urlencoded“ angegeben ist und ein POST-Hauptteil vorliegt, der JSON ist. Dies ist häufig ein Programmierfehler, eine automatisierte oder schädliche Anfrage. Erfordert Agent 3.2 oder höher. |
| SANS | Schädlicher IP-Traffic | [SANS Internet Storm Center](https://isc.sans.edu/): Liste der gemeldeten IP-Adressen, die in Verbindung mit bösartigen Aktivitäten stehen. |
| NO-CONTENT-TYPE | Fehlende Anfragekopfzeile „Content-Type“ | Eine Anfrage vom Typ POST, PUT oder PATCH, die keine Anfragekopfzeile vom Typ „Content-Type“ enthält. Standardmäßig sollten Anwendungs-Server in diesem Fall von „Content-Type: text/plain; charset=us-ascii“ ausgehen. Bei vielen automatisierten und böswilligen Anfragen fehlt möglicherweise „Content-Type“. |
| NOUA | Kein Benutzeragent | Gibt an, dass eine Anforderung keine „Benutzeragent“-Kopfzeile enthält bzw. dass der Kopfzeilenwert nicht festgelegt wurde. |
| NULLBYTE | Null-Byte | Null-Bytes werden normalerweise nicht in einer Anfrage angezeigt und weisen darauf hin, dass die Anfrage falsch formatiert ist und möglicherweise schädlich ist. |
| OOB-DOMAIN | Out-of-Band-Domain | Out-of-Band-Domains werden in der Regel bei Penetrationstests verwendet, um Sicherheitslücken zu identifizieren, bei denen Netzwerkzugriff erlaubt wird. |
| PRIVATEFILE | Private Dateien | Private Dateien sind vertraulich, wie z. B. eine Apache `.htaccess`-Datei oder eine Konfigurationsdatei, der vertrauliche Informationen entnommen werden könnten. |
| SCANNER | Scanner | Identifiziert beliebte Scan-Dienste und -Werkzeuge. |

#### sonstiger Verkehr

| **Flag-ID** | **Flag-Name** | **Beschreibung** |
|---|---|---|
| DATACENTER | Rechenzentrum | Identifiziert die Anfrage als die eines bekannten Hosting-Anbieters. Diese Art von Traffic wird normalerweise nicht mit echten Endbenutzenden verbunden. |
| DOUBLEENCODE | Doppelte Codierung | Bei der doppelten Codierung wird geprüft, ob HTML-Zeichen doppelt codiert werden |
| JSON-ERROR | JSON-Codierungsfehler | Ein POST-, PUT- oder PATCH-Anfragetext, für den angegeben ist, dass er JSON in der Anfragekopfzeile „Inhaltstyp“ enthält, der jedoch JSON-Parsing-Fehler enthält. Dies hängt häufig mit einem Programmierfehler oder einer automatisierten oder schädlichen Anfrage zusammen. |
| TORNODE | Tor-Traffic | Tor ist eine Software, die die Identität einer Benutzerin oder eines Benutzers verschleiert. Eine Spitze im Tor-Traffic kann darauf hinweisen, dass eine angreifende Person versucht, ihren Standort zu verschleiern. |
| XML-ERROR | XML-Codierungsfehler | Ein POST-, PUT- oder PATCH-Anfrageinhalt, für den in der Anfragekopfzeile angegeben wird, dass der „Content-Type“ XML enthält, der jedoch XML-Parsing-Fehler aufweist. Dies hängt häufig mit einem Programmierfehler oder einer automatisierten oder schädlichen Anfrage zusammen. |

## Überlegungen {#considerations}

* Wenn zwei in Konflikt stehende Regeln erstellt werden, haben die Zulassungsregeln immer Vorrang vor den Blockierungsregeln. Wenn Sie beispielsweise eine Regel erstellen, um einen bestimmten Pfad zu blockieren, und eine Regel, um eine bestimmte IP-Adresse zuzulassen, sind Anfragen von dieser IP-Adresse für den blockierten Pfad zulässig.

* Wenn eine Regel abgeglichen und blockiert wird, antwortet das CDN mit einem `406`-Rückgabe-Code.

* Die Konfigurationsdateien enthalten keine Geheimnisse, da sie von allen lesbar sind, die Zugriff auf das Git-Repository haben.

* In Cloud Manager definierte IP-Zulassungslisten haben Vorrang vor Traffic-Filterregeln.

* Übereintimmungen für eine WAF-Regel erscheinen nur in CDN-Protokollen bei Fehlschlägen und Durchgängen von CDN, nicht jedoch bei Treffern.

## Beispiele für Regeln {#examples}

Es folgen einige Regelbeispiele. Weitere Informationen zu Beispielen für Ratenbegrenzungsregeln finden Sie weiter unten im Abschnitt [Ratenbegrenzung](#rate-limit-rules).

**Beispiel 1**

Diese Regel blockiert Anfragen von der **IP192.168.1.1**:

```
kind: "CDN"
version: "1"
data:
  trafficFilters:
     rules:
       - name: "block-request-from-ip"
         when: { reqProperty: clientIp, equals: "192.168.1.1" }
         action:
           type: block
```

**Beispiel 2**

Diese Regel blockiert Anfragen an den Pfad `/helloworld` bei der Veröffentlichung mit einem Benutzeragenten, der Chrome enthält:

```
kind: "CDN"
version: "1"
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

Diese Regel blockiert Anfragen bei der Veröffentlichung an den Pfad `/block-me` und blockiert alle Anfragen, die mit einem `SQLI`- oder `XSS`-Muster übereinstimmen. Dieses Beispiel enthält eine Traffic-Filterregel für WAF, die auf die `SQLI` und `XSS` [WAF-](#waf-flags-list) verweist und daher eine separate Lizenz erfordert.

```
kind: "CDN"
version: "1"
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

## Regeln für Limits

Manchmal ist es wünschenswert, Traffic zu blockieren, wenn er eine bestimmte Rate eingehender Anfragen überschreitet, basierend auf einer bestimmten Bedingung. Wenn Sie einen Wert für die Eigenschaft `rateLimit` festlegen, wird die Rate der Anfragen, die mit der Regelbedingung übereinstimmen, begrenzt.

Ratenbegrenzungsregeln können nicht auf WAF-Flags verweisen. Sie stehen allen Kundinnen und Kunden von Sites und Forms zur Verfügung.

Die Ratenbegrenzungen werden pro CDN-POP berechnet. Nehmen wir zum Beispiel an, dass die POPs in Montreal, Miami und Dublin eine Traffic-Rate von 80, 90 bzw. 120 Anfragen pro Sekunde haben. Außerdem ist die Regel zur Begrenzung der Rate auf einen Grenzwert von 100 festgelegt. In diesem Fall ist nur der Verkehr nach Dublin beschränkt.

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

Diese Regel blockiert einen Client für 5 Minuten, wenn er in den letzten 10 Sekunden einen Durchschnitt von 60 req/sec (pro CDN-POP) überschreitet:

```
kind: "CDN"
version: "1"
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

Weitere Code-Snippets für erweiterte Szenarien finden Sie im Artikel [CDN-Konfigurations-Snippets für allgemeine Szenarien](/help/implementing/dispatcher/cdn-configuration-snippets-common-scenarios.md) .

## CVE-Regeln {#cve-rules}

Wenn WAF lizenziert ist, wendet Adobe automatisch Sperrregeln an, um sich vor vielen bekannten CVEs (Common Vulnerabilities and Expositions) zu schützen. Neue CVEs werden kurz nach ihrer Entdeckung hinzugefügt. Kunden konfigurieren keine CVE-Regeln selbst.

Wenn eine Traffic-Anfrage mit einer CVE übereinstimmt, wird sie im entsprechenden CDN-Protokolleintrag angezeigt.

Wenden Sie sich an den Adobe-Support, wenn Sie Fragen zu einem bestimmten CVE haben oder wenn es eine bestimmte CVE-Regel gibt, die Ihr Unternehmen deaktivieren möchte.

## Warnhinweise zu Traffic-Filterregeln {#traffic-filter-rules-alerts}

Eine Regel kann so konfiguriert werden, dass eine Benachrichtigung des Aktionszentrums gesendet wird, wenn sie innerhalb eines 5-minütigen Fensters zehnmal ausgelöst wird. Eine solche Regel warnt Sie, wenn bestimmte Traffic-Muster auftreten, sodass Sie die erforderlichen Maßnahmen treffen können. Nachdem ein Warnhinweis für eine bestimmte Regel ausgelöst wurde, wird er erst am nächsten Tag (UTC) erneut Trigger.

Erfahren Sie mehr über das [Aktionszentrum](/help/operations/actions-center.md), einschließlich der Einrichtung der erforderlichen Benachrichtigungsprofile für den Empfang von E-Mails.

![Benachrichtigung des Aktionszentrums](/help/security/assets/traffic-filter-rules-actions-center-alert.png)


Die Eigenschaft „Warnhinweis“ kann für alle Aktionstypen (allow, block, log) auf den Knoten „Aktion“ angewendet werden.

```
kind: "CDN"
version: "1"
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

## Standard-Traffic-Spitze bei Ursprungs-Warnhinweis {#traffic-spike-at-origin-alert}

Eine E[Mail](/help/operations/actions-center.md)Benachrichtigung des Aktionszentrums warnt Sie, wenn ein hoher Traffic von derselben IP-Adresse den Ursprung erreicht, was auf einen DDoS-Angriff hindeutet.

Wenn dieser Schwellenwert erreicht ist, blockiert Adobe den Traffic von dieser IP-Adresse. Ergreifen Sie zusätzliche Maßnahmen zum Schutz Ihrer Herkunft, z. B. die Konfiguration von Traffic-Filterregeln für das Ratenlimit. Eine [&#x200B; Anleitung finden Sie im Tutorial zum Blockieren von DoS- und DDoS](#tutorial-blocking-DDoS-with-rules)Angriffen mit Traffic-Regeln .

Das System aktiviert diesen Warnhinweis standardmäßig, Sie können ihn jedoch mit der Eigenschaft *defaultTrafficAlerts* deaktivieren und auf „false“ setzen. Sobald der Warnhinweis ausgelöst wurde, wird er erst am nächsten Tag (UTC) erneut Trigger.

```
kind: "CDN"
version: "1"
data:
  trafficFilters:
   defaultTrafficAlerts: false
```

## CDN-Protokolle {#cdn-logs}

AEM as a Cloud Service bietet Zugriff auf CDN-Protokolle, die für Anwendungsfälle nützlich sind, einschließlich der Optimierung der Cache-Trefferquote und der Konfiguration von Traffic-Filterregeln. CDN-Protokolle werden im Cloud Manager-Dialog **Protokolle herunterladen** angezeigt, wenn Sie den Author- oder Publish-Service auswählen.

CDN-Protokolle verzögern sich um bis zu fünf Minuten.

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
* Wenn die WAF lizenziert und aktiviert ist, listet das Attribut `waf` alle WAF-Flags (z. B. SQLI) auf, die entdeckt wurden. Dieses Verhalten gilt unabhängig davon, ob die WAF-Flags in Regeln aufgeführt wurden. Diese Protokollierung dient dazu, insight in potenzielle neue zu deklarierende Regeln zu integrieren.
* Wenn keine auf Kundenseite deklarierten Regeln übereinstimmen und keine WAF-Regeln übereinstimmen, ist die Eigenschaft `rules` leer.

Wie bereits erwähnt, erscheinen Übereinstimmungen für eine WAF-Regel nur in CDN-Protokollen für Fehlschläge und Durchgänge von CDN, nicht jedoch für Treffer.

Das folgende Beispiel zeigt eine beispielhafte `cdn.yaml` und zwei CDN-Protokolleinträge:


```
kind: "CDN"
version: "1"
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

Adobe bietet einen Mechanismus zum Herunterladen von Dashboard-Tools auf Ihren Computer, um CDN-Protokolle zu erfassen, die über Cloud Manager heruntergeladen wurden. Verwenden Sie dieses Tool, um Ihren Traffic zu analysieren und die entsprechenden zu deklarierenden Traffic-Filterregeln zu bestimmen, einschließlich WAF-Regeln.

Dashboard-Tools können direkt aus dem GitHub-Repository [AEMCS-CDN-Log-Analysis-Tooling](https://github.com/adobe/AEMCS-CDN-Log-Analysis-Tooling) heruntergeladen werden.

Für konkrete Anleitungen zum Verwenden der Dashboard-Tools ist [ein Tutorial](#tutorial) verfügbar.

## Empfohlene Startregeln {#recommended-starter-rules}

Adobe empfiehlt, mit den unten stehenden Traffic-Filterregeln zu beginnen und dann im Lauf der Zeit Optimierungen vorzunehmen. *Standardregeln* sind mit einer Sites- oder Forms-Lizenz verfügbar, während *WAF-Regeln* eine erweiterte Sicherheitslizenz (früher WAF-DDoS-Schutz genannt) oder eine erweiterte Sicherheitslizenz für das Gesundheitswesen (früher Enhanced Security genannt) erfordern.

### Empfohlene Standardregeln {#recommended-nonwaf-starter-rules}

Beginnen Sie mit diesen Regeln:

1. Ratenbegrenzung (Protokollmodus):
   * Protokollieren Sie, wenn der Traffic von einer bestimmten IP-Adresse eine Ratenbegrenzung überschreitet. Wechseln Sie in den Blockierungsmodus, nachdem Sie überprüft haben, ob Warnhinweise empfangen wurden. Wenn Warnhinweise empfangen wurden, bedeutet dies, dass der Grenzwert zu niedrig war.
2. bestimmte Länder (Blockmodus):
   * Blockieren Sie Traffic aus bestimmten Ländern (ändern Sie die Länder-Codes entsprechend Ihren Unternehmensanforderungen)

```
kind: "CDN"
version: "1"
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
      alert: true
    # Block requests coming from OFAC countries
    - name: ofac-countries
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
      action: block
```

### Empfohlene WAF-Regeln {#recommended-waf-starter-rules}

Fügen Sie Ihrer vorhandenen Konfiguration die folgenden Regeln hinzu:

1. Markierung ATTACK-FROM-BAD-IP (Blockmodus):
   * Blockieren Sie Traffic unmittelbar, wenn er sowohl verdächtige Muster aufweist (zum Beispiel mehrere aus der [Liste der WAF-Markierungen](#waf-flags-list)) als auch von bekanntermaßen bösartigen IP-Adressen stammt.
   * Das Flag ATTACK-FROM-BAD-IP erfüllt beide Bedingungen (Musterübereinstimmung und bekannte bösartige IP-Adresse), wodurch das Risiko falsch positiver Ergebnisse minimiert wird. So können Sie diese Regel im Sperrmodus sicher und sofort anwenden.
2. Markierung ATTACK (Protokollmodus):
   * Protokollieren Sie zunächst Traffic (anstatt ihn zu blockieren), der verdächtigen Mustern entspricht, aber nicht von bekannten bösartigen IP-Adressen stammt. Dieser vorsichtigere Ansatz mit Protokollierung statt Blockierung ist hilfreich, um unbeabsichtigtes Blockieren von legitimem Traffic (falsch-positive Ergebnisse) zu vermeiden.
   * Um sicherzustellen, dass rechtmäßige Anfragen nicht falsch gekennzeichnet werden, analysieren Sie CDN-Protokolle nach der Bereitstellung dieser Regel. Wechseln Sie in den Blockmodus, sobald Sie sicher sind, dass kein legitimer Traffic betroffen ist.

>[!NOTE]
>
> Die Erfahrung zeigt an, dass mit der ATTACK-Markierung verknüpfte falsch-positive Ergebnisse selten sind. Daher ist es eine praktische Strategie, jeden verdächtigen Traffic sofort zu blockieren und mithilfe der CDN-Protokollanalyse Regeln für legitimen Traffic zu identifizieren und einzuführen. Jede Organisation bewertet ihre eigene Risikotoleranz und wägt die Vorteile eines besseren Schutzes gegen das Risiko ab, versehentlich legitime Anfragen zu blockieren.

```
    # blocks likely attack traffic, which also comes from suspected IPs
    - name: attacks-from-bad-ips-globally
      when:
        reqProperty: tier
        in: ["author", "publish"]
      action:
        type: block
        wafFlags:
          - ATTACK-FROM-BAD-IP
    # log likely attack traffic, and later switch to block mode if false positives aren't observed
    - name: attacks-from-any-ips-globally
      when:
        reqProperty: tier
        in: ["author", "publish"]
      action:
        type: log
        wafFlags:
          - ATTACK
```

### Ältere empfohlenen WAF-Regeln {#previous-waf-starter-rules}

Vor Juli 2025 empfahl Adobe die unten aufgeführten WAF-Regeln, die weiterhin gültig und beim Schutz vor bösartigem Traffic wirksam sind. Im Tutorial finden Sie weitere Überlegungen bezüglich der Migration zu den neuen empfohlenen Regeln.

+++ Erweitern, um die älteren empfohlenen WAF-Regeln anzuzeigen.

```
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

+++

## Tutorial {#tutorial}

Um praktische Kenntnisse und Erfahrungen über Traffic-Filterregeln, einschließlich WAF-Regeln, zu sammeln, [&#x200B; Sie sich in (einer Reihe von Tutorials](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/security/traffic-filter-and-waf-rules/overview).

Folgende Tutorials sind verfügbar:

* Standard- und WAF-Traffic-Filterregeln – Überblick
* Um Angriffe, einschließlich Denial-of-Service (DoS), zu blockieren, konfigurieren Sie die empfohlenen Standard- und WAF-Traffic-Filterregeln.
* Bereitstellen von Regeln mit der Cloud Manager-Konfigurations-Pipeline
* Testen von Regeln mit Tools zur Simulation von bösartigem Traffic
* Analysieren der Ergebnisse mit den Tools für die Protokollanalyse
* Best Practices
