---
title: Grundlegendes zu Cloud Service-Inhaltsanforderungen
description: Wenn Sie Lizenzen für Inhaltsanforderungen von Adobe erworben haben, erfahren Sie mehr über die Arten von Inhaltsanforderungen, die Adobe Experience Cloud as a Service misst, und über die Abweichungen mit den Analytics-Reporting-Tools eines Unternehmens.
exl-id: 3666328a-79a7-4dd7-b952-38bb60f0967d
source-git-commit: 949f0ec1aa89fd05813bc9ffb02a75fb0ad84a32
workflow-type: tm+mt
source-wordcount: '2690'
ht-degree: 4%

---

# Cloud Service-Inhaltsanforderungen

## Einführung {#introduction}

Inhaltsanforderungen von Cloud Services werden über die serverseitige Datenerfassung gemessen. Die Sammlung wird über die Analyse des CDN-Protokolls aktiviert.

>[!NOTE]
>Zusätzlich wird für eine begrenzte Anzahl von [Frühkindliche Betreuung](/help/release-notes/release-notes-cloud/release-notes-current.md#sites-early-adopter), wird auch die clientseitige Erfassung über die Messung von RUM (Real User Monitoring) aktiviert. Weitere Informationen finden Sie in der Dokumentation unter [diesem Artikel](#real-user-monitoring-for-aem-as-a-cloud-service).

## Grundlegendes zu Cloud Service-Inhaltsanforderungen {#understaing-cloud-service-content-requests}

Inhaltsanforderungen werden automatisch Server-seitig am Rande von Adobe Experience Manager as a Cloud Service erfasst, indem die Protokolldateien aus dem AEM as a Cloud Service CDN automatisiert analysiert werden. Dies geschieht durch Isolieren der Anfragen, die HTML zurückgeben `(text/html)` oder JSON `(application /Json)` Inhalt aus dem CDN und basierend auf verschiedenen unten beschriebenen Aufnahme- und Ausschlussregeln. Eine Inhaltsanforderung erfolgt unabhängig vom zurückgegebenen Inhalt, der von den CDN-Caches bereitgestellt wird, oder dem Inhalt, der an die Herkunft des CDN (AEM Dispatcher) zurückgeht.

Der Real User Monitoring (RUM) Data Service , die clientseitige Erfassung, bietet eine präzisere Darstellung der Benutzerinteraktionen und stellt eine zuverlässige Messung der Website-Interaktion sicher. Dadurch erhalten Kunden erweiterte Einblicke in ihren Seiten-Traffic und ihre Leistung. Dies ist zwar für beide Kunden von Vorteil, die entweder das von Adobe verwaltete CDN oder ein nicht von Adobe verwaltetes CDN verwenden. Darüber hinaus kann die automatische Traffic-Berichterstellung jetzt für Kunden aktiviert werden, die ein nicht von Adobe verwaltetes CDN verwenden. Dadurch entfällt die Notwendigkeit, Traffic-Berichte mit Adobe zu teilen.

Für Kunden, die ihr eigenes CDN auf AEM as a Cloud Service übertragen, führt die serverseitige Berichterstellung zu Zahlen, die nicht mit den lizenzierten Inhaltsanforderungen verglichen werden können. Diese Zahlen müssen vom Kunden am Rand des äußeren CDN gemessen werden. Bei diesen Kunden wird die clientseitige Berichterstellung und die zugehörige Leistung anhand der Variablen [Adobe RUM-Datendienst](#real-user-monitoring-for-aem-as-a-cloud-service) ist die von der Adobe empfohlene Option. Siehe [Versionshinweise](/help/release-notes/release-notes-cloud/release-notes-current.md#sites-early-adopter) Informationen zum Opt-in.

## Serverseitige Sammlung {#serverside-collection}

Es gibt Regeln, um bekannte Bots auszuschließen, einschließlich bekannter Dienste, die die Site regelmäßig besuchen, um ihren Suchindex oder -dienst zu aktualisieren.

### Varianzen von Inhaltsanforderungen von Cloud Services {#content-requests-variances}

Inhaltsanforderungen können Abweichungen von den Analytics-Reporting-Tools eines Unternehmens aufweisen, wie in der folgenden Tabelle zusammengefasst. Im Allgemeinen *nicht* Verwenden Sie Analysetools, die Daten mithilfe Client-seitiger Instrumentierung erfassen, um über die Anzahl der Inhaltsanforderungen für eine bestimmte Site zu berichten, einfach weil sie häufig davon abhängen, dass die Benutzerzustimmung ausgelöst wird, und daher bei einem erheblichen Teil des Traffics fehlen. Analytics-Tools, die Daten Server-seitig in Protokolldateien sammeln, oder CDN-Berichte für Kunden, die zusätzlich zu AEM as a Cloud Service ihr eigenes CDN hinzufügen, bieten bessere Zählungen. Für Berichte zu Seitenansichten und der zugehörigen Leistung ist der Adobe RUM-Datendienst die Adobe empfohlene Option.

| Grund für die Abweichung | Erklärung |
|---|---|
| Zustimmung des Endbenutzers | Analytics-Tools, die auf clientseitige Instrumente angewiesen sind, hängen häufig davon ab, dass die Benutzerzustimmung ausgelöst wird. Dies könnte den Großteil des Traffics ausmachen, der nicht verfolgt wird. Kunden, die Inhaltsanfragen allein messen möchten, sollten sich auf Analytics-Tools verlassen, die Daten Server-seitig oder CDN-Berichte erfassen. |
| Tagging | Alle Seiten oder API-Aufrufe, die als Adobe Experience Manager (AEM)-Inhaltsanfragen verfolgt werden, werden möglicherweise nicht mit Analytics-Tracking getaggt. |
| Tag-Management-Regeln | Die Einstellungen von Tag-Management-Regeln können zu verschiedenen Datenerfassungskonfigurationen auf einer Seite führen, was zu einigen Kombinationen von Diskrepanzen beim Tracking von Inhaltsanforderungen führt. |
| Bots | Unbekannte Bots, die nicht vorab identifiziert und von AEM entfernt wurden, können zu Tracking-Diskrepanzen führen. |
| Report Suites | Seiten, die Teil derselben AEM-Instanz und -Domain sind, können Daten an verschiedene Analytics Report Suites senden. |
| Überwachungs- und Sicherheits-Tools von Drittanbietern | Überwachungs- und Sicherheitsüberprüfungs-Tools können Inhaltsanfragen für AEM generieren, die in Analytics-Berichten nicht erfasst werden. |
| API-Zugriff | Der programmatische Zugriff auf Seiten oder Adobe Experience Manager-APIs kann Inhaltsanforderungen für AEM generieren, die in Analytics-Berichten nicht verfolgt werden. |
| Vorheriges Abrufen von Anfragen | Die Verwendung eines Vorabruf-Services zum Vorladen von Seiten, um die Geschwindigkeit zu erhöhen, kann zu erheblichen Traffic-Zunahmen bei Inhaltsanfragen führen. |
| DDOS | Während Adobe versucht, Traffic automatisch aus DDOS-Angriffen zu erkennen und herauszufiltern, gibt es keine Garantie, dass alle möglichen DDOS-Angriffe erkannt werden. |
| Traffic-Blocker | Die Verwendung eines Tracker-Blockers in einem Browser kann die Nachverfolgung mancher Anfragen verhindern. |
| Firewalls | Firewalls können das Analytics-Tracking blockieren. Dieses Szenario tritt bei Firewalls des Unternehmens häufiger auf. |

Siehe auch [Lizenz-Dashboard](/help/implementing/cloud-manager/license-dashboard.md).

### Typen der enthaltenen Inhaltsanfragen {#included-content-requests}

| Anfragetyp | Inhaltsanforderung | Beschreibung |
| --- | --- | --- |
| HTTP-Code 100-299 | Enthalten | Hierbei handelt es sich um reguläre Anfragen, die alle oder nur teilweise Inhalte bereitstellen. |
| HTTP-Bibliotheken für Automatisierung | Enthalten | Beispiele:<br>・ Amazon CloudFront<br>・ Apache Http Client<br>・ Asynchroner HTTP-Client<br>・ Axios<br>Azureus<br>・ Curl<br>・ GitHub-Knotenabruf<br>・ Guzzle<br>・ Gohttp-client<br>・ Headless-Chrome<br>・ Java™ Client<br>Jersey<br>・ Knoteneinbettung<br>・ okhttp<br>Python-Anfragen<br>・ Reactor Netty<br>・ Wget<br>・ WinHTTP |
| Tools zur Überwachung und Konsistenzprüfung | Enthalten | Diese werden vom Kunden eingerichtet, um einen bestimmten Aspekt der Site zu überwachen. Beispielsweise Verfügbarkeit oder reale Benutzerleistung. Verwendung `/system/probes/health` -Endpunkt und nicht die eigentlichen HTML-Seiten von der Site.<br>Beispiele:<br>・ Amazon-Route53-Health-Check-Service<br>・ EyeMonIT_bot_version_0.1_[(https://www.eyemon.it/)](https://www.eyemon.it/)<br>・ Investis-Site24x7<br>・ Mozilla/5.0+(kompatibel; UptimeRobot/2.0; [https://uptimerobot.com/](https://uptimerobot.com/))<br>ThousandEyes-Dragonfly-x1<br>OmtrBot/1.0<br>・ WebMon/2.0.0 |
| `<link rel="prefetch">` requests | Enthalten | Um das Laden der nächsten Seite zu beschleunigen, können Kunden vom Browser eine Reihe von Seiten laden lassen, bevor der Benutzer auf den Link klickt, sodass sie sich bereits im Cache befinden. *Denken: Dadurch wird der Traffic deutlich erhöht*- abhängig davon, wie viele dieser Seiten vorabgerufen werden. |
| Traffic, der die Berichterstellung für Adobe Analytics oder Google Analytics blockiert | Enthalten | Es kommt häufiger vor, dass für Besucher von Websites Datenschutzsoftware installiert ist (Anzeigenblocker usw.), die die Genauigkeit von Google Analytics oder Adobe Analytics beeinträchtigt. AEM as a Cloud Service zählt Anforderungen beim ersten Einstiegspunkt in die von der Adobe betriebene Infrastruktur und nicht auf der Clientseite. |

Siehe auch [Lizenz-Dashboard](/help/implementing/cloud-manager/license-dashboard.md).

### Typen von ausgeschlossenen Inhaltsanfragen {#excluded-content-request}

| Anfragetyp | Inhaltsanforderung | Beschreibung |
| --- | --- | --- |
| HTTP-Code 500+ | Ausgeschlossen | Fehler, die an den Besucher zurückgegeben werden, wenn bei AEM as a Cloud Service Code oder dem benutzerspezifischen Code ein Fehler auftritt. |
| HTTP-Code 400-499 | Ausgeschlossen | Fehler, die an den Besucher zurückgegeben werden, wenn der Inhalt nicht vorhanden ist (404) oder andere Inhalte oder anfragebezogene Probleme vorliegen. |
| HTTP-Code 300-399 | Ausgeschlossen | Dies sind gute Anfragen, die entweder überprüfen, ob sich auf dem Server etwas geändert hat, oder die Anfrage an eine andere Ressource weiterleiten. Sie enthalten keine Inhalte selbst, daher sind sie nicht abrechnungsfähig. |
| Anforderungen für /libs/* | Ausgeschlossen | AEM interne JSON-Anforderungen, z. B. das CSRF-Token, das nicht abrechenbar ist. |
| Traffic durch DDOS-Angriffe | Ausgeschlossen | DDOS-Schutz. AEM erkennt einige DDOS-Angriffe automatisch und blockiert sie. DDOS-Angriffe werden nicht abgerechnet, wenn sie erkannt werden. |
| AEM as a Cloud Service NewRelic-Überwachung | Ausgeschlossen | AEM as a Cloud Service globale Überwachung. |
| URL für Kunden zur Überwachung ihres Cloud Service-Programms | Ausgeschlossen | Empfohlene URL zur externen Überwachung der Verfügbarkeit.<br><br>`/system/probes/health` |
| AEM as a Cloud Service Warm-up-Dienst für Werbeunterbrechungen | Ausgeschlossen | Benutzeragent: skyline-service-warmup/1.* |
| Bekannte Suchmaschinen, soziale Netzwerke und HTTP-Bibliotheken (mit Tags von Fastly) | Ausgeschlossen | Bekannte Dienste, die die Site regelmäßig besuchen, um ihren Suchindex oder -dienst zu aktualisieren:<br><br>Beispiele:<br>・ AddSearchBot<br>AhrefsBot<br>Applebot<br>・ Fragen an Jeeves Corporate Spider<br>Bingbot<br>・ BingPreview<br>BLEXBot<br>・ BuiltWith<br>Bytespider<br>CrawlerKengo<br>・ Facebook-externalhit<br>・ Google AdsBot<br>・ Google AdsBot Mobile<br>・ GoogleBot<br>・ GoogleBot Mobile<br>lmspider<br>LucidWorks<br>・ MJ12bot<br>・ Pingom<br>・ Pinterest<br>SemrushBot<br>・ SiteVerbessern<br>StashBot<br>・ StatusCake<br>YandexBot |
| Commerce integration framework-Aufrufe ausschließen | Ausgeschlossen | Dies sind Anfragen an AEM, die an die Commerce integration framework weitergeleitet werden - die URL beginnt mit `/api/graphql`—um eine doppelte Zählung zu vermeiden, sind sie für den Cloud Service nicht abrechenbar. |
| Ausschließen `manifest.json` | Ausgeschlossen | Manifest ist kein API-Aufruf. Hier finden Sie Informationen zur Installation von Websites auf Desktop- oder Mobiltelefonen. Adobe sollte JSON-Anfrage nicht zählen zu `/etc.clientlibs/*/manifest.json` |
| Ausschließen `favicon.ico` | Ausgeschlossen | Obwohl der zurückgegebene Inhalt nicht HTML oder JSON sein sollte, stellen wir fest, dass in einigen Szenarien wie SAML-Authentifizierungsflüssen Favicons zurückgegeben werden können, da HTML daher explizit von der Zählung ausgeschlossen ist. |

## Clientseitige Sammlung {#cliendside-collection}

## Echtzeit-Benutzerüberwachung (RUM) für AEM as a Cloud Service {#real-user-monitoring-for-aem-as-a-cloud-service}

>[!INFO]
>
>Diese Funktion steht nur dem Programm für frühe Anwender zur Verfügung.
>Sie müssen die AEM Cloud Service-Version verwenden **2023.11.14227** und höher, um den RUM-Datendienst zu aktivieren.

### Übersicht {#overview}

Real User Monitoring (RUM) ist eine Art von Technologie zur Leistungsüberwachung, die die digitalen Benutzererlebnisse einer Website oder Anwendung in Echtzeit erfasst und analysiert. Es bietet Einblicke in die Echtzeit-Leistung einer Webanwendung und bietet genaue Einblicke in das Benutzererlebnis.

Die Echtzeit-Benutzerüberwachung (Real User Monitoring, RUM) bietet einen tiefen Einblick in die wichtigsten Leistungsmetriken von der Initiierung der URL bis zur Rückgabe der Anfrage an den Browser. Dies alles hilft den Entwicklern, die Anwendung zu erweitern, um die Verwendung für die Endbenutzer zu vereinfachen.

### Wer kann von RUM Data Monitoring Service profitieren? {#who-can-benefit-from-rum-data-monitoring-service}

RUM Data Service ist für diejenigen von Vorteil, die Adobe nutzen, da es eine präzisere Reflektion der Benutzerinteraktionen bietet und eine zuverlässige Messung der Website-Interaktion gewährleistet, indem die Anzahl der Seitenansichten auf Client-Seite widergespiegelt wird, die mit den vorhandenen serverseitigen CDN-Log-Seitenansichten verglichen werden können. Darüber hinaus kann Adobe für Kunden, die ihr eigenes CDN verwenden, die automatische Traffic-Berichterstellung optimieren, die Seitenansichten für sie enthält. Das bedeutet, dass sie keinen Traffic-Bericht mit Adobe teilen müssen.

Darüber hinaus bietet es eine hervorragende Möglichkeit, erweiterte Einblicke in Ihre Seitenleistung zu erhalten, und zwar sowohl für Kunden, die das CDN verwenden, als auch für Kunden, die ihr eigenes CDN verwenden.

### Erfahren Sie, wie der Datendienst für die Echtzeit-Benutzerüberwachung (RUM) funktioniert {#understand-how-the-rum-data-service-works}

Adobe Experience Manager verwendet die Echtzeit-Benutzerüberwachung (RUM), um Kunden und Adobe zu helfen, zu verstehen, wie Besucher mit Adobe Experience Manager-gestützten Sites interagieren, Leistungsprobleme zu diagnostizieren und die Effektivität von Experimenten zu messen. RUM bewahrt die Privatsphäre der Besucher durch Stichproben - nur ein kleiner Teil aller Seitenansichten wird überwacht - und einen umsichtigen Ausschluss aller persönlich identifizierbaren Informationen (PII).

### Echtzeit-Benutzerüberwachung (RUM) und Datenschutz {#rum-and-privacy}

Die Echtzeit-Benutzerüberwachung in Adobe Experience Manager dient der Wahrung des Datenschutzes der Besucher und der Minimierung der Datenerfassung. Als Besucher bedeutet dies, dass keine personenbezogenen Daten von der Website erfasst werden, die Sie besuchen, oder der Adobe zur Verfügung gestellt werden.

Als Site-Operator bedeutet dies, dass keine zusätzliche Anmeldung erforderlich ist, um die Überwachung über diese Funktion zu aktivieren. Daher gibt es kein zusätzliches Popup, das die Endbenutzer für die Aktivierung der RUM-Überwachung akzeptieren können.

### RUM-Datenstichproben {#rum-data-sampling}

Herkömmliche Web-Analytics-Lösungen versuchen, Daten zu jedem einzelnen Besucher zu erfassen. Die Echtzeit-Benutzerüberwachung von Adobe Experience Manager erfasst nur Informationen aus einem kleinen Bruchteil der Seitenansichten. Die Echtzeit-Benutzerüberwachung (Real User Monitoring, RUM) ist dazu gedacht, gesampelt und anonymisiert zu werden und nicht als Ersatz für die Analyse. Standardmäßig haben Seiten ein Stichprobenverhältnis von 1:100. Site-Operatoren können diese Zahl nicht so konfigurieren, dass die Sampling-Rate ab heute erhöht oder verringert wird. Um den gesamten Traffic genau zu schätzen, sammeln wir für jede 100 Seitenansichten detaillierte Daten von einer, um Ihnen eine zuverlässige Annäherung des gesamten Traffics zu ermöglichen.&quot;

Da die Entscheidung darüber, ob die Daten erfasst werden, auf Seitenansichtsbasis erfolgt, ist es praktisch unmöglich, Interaktionen auf mehreren Seiten zu verfolgen. RUM hat kein Konzept von Besuchen, Besuchern oder Sitzungen, nur von Seitenansichten. Das ist beabsichtigt.

### Welche Daten werden erfasst? {#what-data-is-being-collected}

Die Echtzeit-Benutzerüberwachung (Real User Monitoring, RUM) dient dazu, die Erfassung von personenbezogenen Daten zu verhindern. Die vollständigen Informationen, die von Adobe Experience Manager Real User Monitoring erfasst werden können, finden Sie unten:

* Der Hostname der besuchten Site, beispielsweise: `experienceleague.adobe.com`
* Der allgemeine Benutzeragenten-Typ, der zur Anzeige der Seite verwendet wird, z. B. Desktop oder Mobilgerät
* Der Zeitpunkt der Datenerfassung, z. B.: `2021-06-26 06:00:02.596000 UTC (in order to preserve privacy, we round all minutes to the previous hour, so that only seconds and milliseconds are tracked)`
* Die URL der besuchten Seite, z. B.: `https://experienceleague.adobe.com/docs`
* Die Referrer-URL (die URL der Seite, die mit der aktuellen Seite verknüpft ist, wenn der Benutzer einem Link gefolgt ist)
* Eine zufällig generierte ID der Seitenansicht in einem Format, das dem folgenden ähnelt: `2Ac6`
* Gewicht oder Umkehrung der Stichprobenrate, beispielsweise: `100`. Das bedeutet, dass nur ein von hundert Seitenansichten aufgezeichnet wird
* Checkpoint oder Name eines bestimmten Ereignisses in der Abfolge des Ladens der Seite oder der Interaktion mit ihr als Besucher
* Die Quelle oder die Kennung des DOM-Elements, mit dem der Benutzer für den oben genannten Checkpoint interagiert. Dies kann beispielsweise ein Bild sein.
* Die Zielgruppe oder der Link zu einer externen Seite oder Ressource, mit der der Benutzer für den oben genannten Checkpoint interagiert. Beispiel: `https://blog.adobe.com/jp/publish/2022/06/29/media_162fb947c7219d0537cce36adf22315d64fb86e94.png`
* Die Leistungsmetriken &quot;Core Web Vitals&quot;(CWV), &quot;Größter Content Paint&quot;(LCP), &quot;Erste Eingabe-Verzögerung&quot;(FID) und &quot;Kumulativer Layout-Umschalt&quot;(CLS), die die Erlebnisqualität des Besuchers beschreiben.

### Einrichten des Datendienstes für die Echtzeit-Benutzerüberwachung (RUM) {#how-to-set-up-them-rum-data-service}

* Wenn Sie Teil unseres Early Adopter-Programms sein möchten, senden Sie bitte eine E-Mail an `aemcs-rum-adopter@adobe.com`zusammen mit Ihrem Domänennamen für die Produktions-, Staging- und Entwicklungsumgebung von Ihrer E-Mail-Adresse aus, die mit Ihrer Adobe ID verknüpft ist. Das Produktteam von Adobe aktiviert dann den Datendienst für die Echtzeit-Benutzerüberwachung (RUM) für Sie.
* Sobald dies abgeschlossen ist, erstellt das Produktteam von Adobe einen Kanal für die Zusammenarbeit mit Kunden.
* Das Produktteam von Adobe kontaktiert Sie, indem es Ihnen den Domänenschlüssel und die Daten-Dashboard-URL zur Verfügung stellt, über die Sie die Seitenansichten und [Die wichtigsten Web-Vitals (CWV)](https://web.dev/vitals/) Metriken, die von der clientseitigen RUM (Real User Monitoring)-Sammlung erfasst werden.
* Anschließend erfahren Sie, wie Sie mit dem Domänenschlüssel auf die Daten-Dashboard-URL zugreifen und die Metriken anzeigen können.

### Verwendung von URL-Daten (Real User Monitoring) {#how-rum-data-is-being-used}

RUM-Daten sind für folgende Zwecke von Vorteil:

* Identifizieren und Beheben von Leistungsengpässen bei Kunden-Sites
* Optimierte, automatische Traffic-Berichte, die Seitenansichten für Kunden enthalten, die ihr eigenes CDN verwenden. Dies bedeutet, dass sie keinen Traffic-Bericht mit Adobe teilen müssen.
* Um zu verstehen, wie Adobe Experience Manager mit anderen Skripten (z. B. Analyse-, Targeting- oder externen Bibliotheken) auf derselben Seite interagiert, wird die Kompatibilität erhöht.

### Einschränkungen und Verstehen von Abweichungen bei Seitenansichten und Leistungsmetriken {#limitations-and-understanding-variance-in-page-views-and-performance-metrics}

Da Sie diese Daten analysieren werden, kann es Abweichungen bei Seitenansichten und anderen Leistungsmetriken geben, die von der Echtzeit-Benutzerüberwachung (RUM) gemeldet werden. Diese Abweichungen können verschiedenen Faktoren zugeschrieben werden, die mit der Echtzeit- und clientseitigen Überwachung verbunden sind. Im Folgenden finden Sie wichtige Hinweise, die Kunden bei der Interpretation ihrer RUM-Daten beachten sollten:

1. **Tracker-Blocker**

   * Endbenutzer, die Tracker-Blocker oder Datenschutzerweiterungen verwenden, können die Datenerfassung von Real User Monitoring (RUM) behindern, da diese Tools die Ausführung von Tracking-Skripten einschränken. Diese Einschränkung kann zu untergemeldeten Seitenansichten und Benutzerinteraktionen führen, was zu einer Diskrepanz zwischen der tatsächlichen Site-Aktivität und den von RUM erfassten Daten führen kann.

1. **Einschränkungen bei der Erfassung von API-/JSON-Aufrufen**

   * Der RUM-Datendienst konzentriert sich auf das clientseitige Erlebnis und erfasst derzeit nicht die Backend-API- oder JSON-Aufrufe. Der Ausschluss dieser Aufrufe aus RUM-Daten (Real User Monitoring) führt zu Abweichungen von den von CDN Analytics gemessenen Inhaltsanforderungen.

### Häufig gestellte Fragen {#faq}

1. **Wie kann ich Pfade konfigurieren, die in die Überwachung ein- oder ausgeschlossen werden?**

   Kunden können Pfade konfigurieren, um die URLs für die Überwachung ein- oder auszuschließen, indem sie die Umgebungsvariablen in der Konfiguration in Cloud Manager mithilfe der folgenden Variablen festlegen: `AEM_WEBVITALS_EXCLUDE` und `AEM_WEBVITALS_INCLUDE_PATHS`

   Beachten Sie, dass die Einstellung &quot;Einschließen&quot;standardmäßig für das Ziel &quot;/content&quot;konfiguriert ist. Beachten Sie dabei, dass es sich bei den Pfaden, die Sie hier konfigurieren müssen, um Inhaltspfade innerhalb des Systems handelt, nicht um die URL-Pfade, die Sie in Ihrem Browser sehen. Diese Unterscheidung ist für die genaue Einrichtung und Anpassung Ihrer Konfiguration an Ihre spezifischen Anforderungen von entscheidender Bedeutung.

1. **Kann Adobe alle Seitenansichten verfolgen, bevor die Interaktion das vom Kunden verwaltete CDN erreicht oder zu dem Zeitpunkt, zu dem die Interaktion das vom Kunden verwaltete CDN erreicht?**

   Ja.

1. **Können Kunden die RUM-Datendienstskripte in Drittanbietersysteme wie Dynatrace integrieren?**

   Ja.

1. **Werden die Metriken &quot;Interaktion mit der nächsten Farbe&quot;, &quot;Zeit bis zum ersten Byte&quot;und &quot;Erste contentful Farbe&quot;erfasst?**

   Interaktion mit der nächsten Farbe (INP) und Zeit bis zum ersten Byte (TTFB) werden erfasst.  Die erste Inhaltsfarbe wird derzeit nicht erfasst.
