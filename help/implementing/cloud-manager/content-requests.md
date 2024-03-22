---
title: Grundlegendes zu Cloud Service-Inhaltsanfragen
description: Wenn Sie Lizenzen für Inhaltsanfragen von Adobe erworben haben, können Sie mehr über die Arten von Inhaltsanfragen, die Adobe Experience Cloud as a Service misst, und über die Abweichungen von den Analytics-Reporting-Tools eines Unternehmens erfahren.
exl-id: 3666328a-79a7-4dd7-b952-38bb60f0967d
source-git-commit: bae9a5178c025b3bafa8ac2da75a1203206c16e1
workflow-type: tm+mt
source-wordcount: '2688'
ht-degree: 100%

---

# Cloud Service-Inhaltsanfragen

## Einführung {#introduction}

Inhaltsanfragen von Cloud Services werden über die Server-seitige Datenerfassung gemessen. Die Sammlung wird über die Analyse des CDN-Protokolls aktiviert.

>[!NOTE]
>Zusätzlich wird für eine begrenzte Anzahl von [Early-Adoptern](/help/release-notes/release-notes-cloud/release-notes-current.md#sites-early-adopter) auch die Client-seitige Erfassung über die Messung von RUM (Real User Monitoring-Dienst) aktiviert. Weitere Informationen finden Sie in der Dokumentation unter [diesem Artikel](#real-user-monitoring-for-aem-as-a-cloud-service).

## Grundlegendes zu Cloud Service-Inhaltsanfragen {#understaing-cloud-service-content-requests}

Inhaltsanfragen werden automatisch Server-seitig am Edge von Adobe Experience Manager as a Cloud Service erfasst, indem die Protokolldateien aus dem AEM as a Cloud Service-CDN automatisiert analysiert werden. Dies geschieht durch Isolieren der Anfragen, die HTML- `(text/html)` oder JSON`(application /Json)`-Inhalt aus dem CDN zurückgeben, und basierend auf verschiedenen Aufnahme- und Ausschlussregeln, die im Folgenden erläutert werden. Eine Inhaltsanfrage erfolgt unabhängig davon, ob der zurückgegebene Inhalt von den CDN-Caches bereitgestellt wird oder ob er zurück an den Ursprung des CDN (AEM-Dispatcher) geht.

Der Real User Monitoring-Dienst, die Client-seitige Erfassung, bietet eine präzisere Darstellung der Benutzerinteraktionen und stellt eine zuverlässige Messung der Website-Interaktion sicher. Dadurch erhalten Kundinnen und Kunden erweiterte Einblicke in ihren Seiten-Traffic und ihre Leistung. Dies ist sowohl für Kundinnen und Kunden von Vorteil, die das von Adobe verwaltete CDN nutzen, als auch für solche, die ein nicht von Adobe verwaltetes CDN verwenden. Darüber hinaus kann die automatische Traffic-Berichterstellung jetzt für Kundinnen und Kunden aktiviert werden, die ein nicht von Adobe verwaltetes CDN verwenden. Dadurch entfällt die Notwendigkeit, Traffic-Berichte mit Adobe zu teilen.

Für Kundinnen und Kunden, die ihr eigenes CDN auf AEM as a Cloud Service anwenden, führt die Server-seitige Berichterstellung zu Zahlen, die nicht mit den lizenzierten Inhaltsanfragen verglichen werden können. Diese Zahlen müssen von den Kundinnen und Kunden am Edge des äußeren CDN gemessen werden. Für diese Kundinnen und Kunden, die Client-seitige Berichterstellung und die damit verbundene Leistung ist der [Adobe RUM-Datendienst](#real-user-monitoring-for-aem-as-a-cloud-service) die von Adobe empfohlene Option. Weitere Informationen zum Opt-in finden Sie in den [Versionshinweisen](/help/release-notes/release-notes-cloud/release-notes-current.md#sites-early-adopter).

## Server-seitige Sammlung {#serverside-collection}

Es gibt Regeln, um bekannte Bots auszuschließen, einschließlich bekannter Services, die die Site regelmäßig besuchen, um ihren Suchindex oder -Service zu aktualisieren.

### Abweichungen von Cloud Service-Inhaltsanfragen {#content-requests-variances}

Inhaltsanfragen können Abweichungen von den Analytics-Reporting-Tools eines Unternehmens aufweisen, die in dieser Tabelle zusammengefasst sind. Im Allgemeinen sollten Analyse-Tools, die Daten mithilfe Client-seitiger Instrumentierung erfassen, *nicht verwendet werden*, um über die Anzahl der Inhaltsanfragen für eine bestimmte Site zu berichten. Der Grund dafür ist, dass sie häufig von der Zustimmung von Benutzerinnen und Benutzern abhängig sind, um ausgelöst zu werden, wodurch sie einen erheblichen Anteil des Traffics nicht erfassen. Analyse-Tools, die Daten Server-seitig in Protokolldateien sammeln, oder CDN-Berichte für Kundinnen und Kunden, die zusätzlich zu AEM as a Cloud Service ihr eigenes CDN hinzufügen, bieten bessere Zählungen. Für die Berichterstellung über Seitenansichten und die damit verbundene Leistung ist der Adobe RUM-Datendienst die von Adobe empfohlene Option.

| Grund für die Abweichung | Erklärung |
|---|---|
| Zustimmung der Endbenutzenden | Analytics-Tools, die auf Client-seitige Instrumente angewiesen sind, sind häufig davon abhängig, dass eine Benutzerzustimmung ausgelöst wird. Dies könnte den Großteil des Traffics ausmachen, der nicht erfasst wird. Für Kundinnen und Kunden, die Inhaltsanfragen selbst messen möchten, werden Analytics-Tools, die Daten Server-seitig erfassen, oder CDN-Berichte empfohlen. |
| Tagging | Alle Seiten oder API-Aufrufe, die als Adobe Experience Manager(AEM)-Inhaltsanfragen erfasst werden, können nicht zum Analytics-Tracking getaggt werden. |
| Tag-Management-Regeln | Die Einstellungen von Tag-Management-Regeln können auf einer Seite unterschiedliche Datenerfassungskonfigurationen zur Folge haben, was zu einigen Diskrepanzen beim Tracking von Inhaltsanfragen führt. |
| Bots | Unbekannte Bots, die nicht vorab identifiziert und von AEM entfernt wurden, können zu Tracking-Diskrepanzen führen. |
| Report Suites | Seiten, die Teil derselben AEM-Instanz und -Domain sind, können Daten an verschiedene Analytics Report Suites senden. |
| Überwachungs- und Sicherheits-Tools von Drittanbietern | Überwachungs- und Sicherheitsüberprüfungs-Tools können Inhaltsanfragen für AEM generieren, die in Analytics-Berichten nicht erfasst werden. |
| API-Zugriff | Der programmgesteuerte Zugriff auf Seiten oder Adobe Experience Manager-APIs kann Inhaltsanfragen für AEM generieren, die in Analytics-Berichten nicht erfasst werden. |
| Vorheriges Abrufen von Anfragen | Die Verwendung eines Vorabruf-Services zum Vorladen von Seiten, um die Geschwindigkeit zu erhöhen, kann zu erheblichen Traffic-Zunahmen bei Inhaltsanfragen führen. |
| DDOS | Adobe unternimmt zwar Anstrengungen, um Traffic durch DDOS-Angriffe automatisch zu erkennen und herauszufiltern, aber es gibt keine Garantie dafür, dass alle möglichen DDOS-Angriffe erkannt werden. |
| Traffic-Blocker | Die Verwendung eines Tracker-Blockers in einem Browser kann die Nachverfolgung mancher Anfragen verhindern. |
| Firewalls | Firewalls können das Analytics-Tracking blockieren. Dies ist vor allem bei Unternehmens-Firewalls häufiger der Fall. |

Siehe auch [Lizenz-Dashboard](/help/implementing/cloud-manager/license-dashboard.md).

### Arten von enthaltenen Inhaltsanfragen {#included-content-requests}

| Abfragetyp | Inhaltsanfrage | Beschreibung |
| --- | --- | --- |
| HTTP-Code 100–299 | Einschließlich | Hierbei handelt es sich um reguläre Anfragen, die vollständige oder partielle Inhalte bereitstellen. |
| HTTP-Bibliotheken für die Automatisierung | Einschließlich | Beispiele:<br>• Amazon CloudFront<br>• Apache Http Client<br>• Asynchronous Http Client<br>• Axios<br>• Azureus<br>• Curl<br>• GitHub Node Fetch<br>• Guzzle<br>• Go-http-client<br>• Headless Chrome<br>• Java™ Client<br>• Jersey<br>• Node Oembed<br>• okhttp<br>• Python Requests<br>• Reactor Netty<br>• Wget<br>• WinHTTP |
| Tools für die Überwachung und Konsistenzprüfung | Einschließlich | Diese werden auf Kundenseite eingerichtet, um einen bestimmten Aspekt der Site zu überwachen. Dazu gehören die Verfügbarkeit oder die tatsächliche Benutzerleistung. Verwenden Sie den Endpunkt `/system/probes/health` und nicht die eigentlichen HTML-Seiten der Site.<br>Beispiele:<br>• Amazon-Route53-Health-Check-Service<br>• EyeMonIT_bot_version_0.1_[(https://www.eyemon.it/)](https://www.eyemon.it/)<br>• Investis-Site24x7<br>• Mozilla/5.0+(compatible; UptimeRobot/2.0; [https://uptimerobot.com/](https://uptimerobot.com/))<br>• ThousandEyes-Dragonfly-x1<br>• OmtrBot/1.0<br>• WebMon/2.0.0 |
| `<link rel="prefetch">`-Anfragen | Einschließlich | Um das Laden der nächsten Seite zu beschleunigen, können Kundinnen und Kunden eine Reihe von Seiten in den Browser laden, bevor Benutzende auf den Link klicken, sodass sie sich bereits im Cache befinden. *Denken Sie daran: Dadurch nimmt der Traffic deutlich zu*, abhängig davon, wie viele dieser Seiten vorabgerufen werden. |
| Traffic, der das Adobe Analytics- oder Google Analytics-Reporting blockiert | Einschließlich | Es kommt häufiger vor, dass Menschen, die Sites besuchen, Datenschutz-Software installiert haben (Adblocker usw.), die die Genauigkeit von Google Analytics oder Adobe Analytics beeinträchtigt. AEM as a Cloud Service zählt Anfragen beim ersten Einstiegspunkt in die von Adobe betriebene Infrastruktur und nicht auf der Client-Seite. |

Siehe auch [Lizenz-Dashboard](/help/implementing/cloud-manager/license-dashboard.md).

### Typen von ausgeschlossenen Inhaltsanfragen {#excluded-content-request}

| Abfragetyp | Inhaltsanfrage | Beschreibung |
| --- | --- | --- |
| HTTP-Code 500+ | Ausgeschlossen | Fehler, die an Besucherinnen und Besucher zurückgegeben werden, wenn bei AEM as a Cloud Service oder im benutzerspezifischen Code ein Fehler auftritt. |
| HTTP-Code 400–499 | Ausgeschlossen | Fehler, die an Besucherinnen und Besucher zurückgegeben werden, wenn der Inhalt nicht vorhanden ist (404) oder andere inhalts- oder anfragebezogene Probleme vorliegen. |
| HTTP-Code 300–399 | Ausgeschlossen | Dies sind nützliche Anfragen, die entweder überprüfen, ob sich auf dem Server etwas geändert hat, oder die Anfrage an eine andere Ressource weiterleiten. Sie enthalten selbst keine Inhalte, daher sind sie nicht abrechenbar. |
| Anfragen für /libs/* | Ausgeschlossen | AEM interne JSON-Anfragen, z. B. das CSRF-Token, das nicht abrechenbar ist. |
| Traffic durch DDOS-Angriffe | Ausgeschlossen | DDOS-Schutz. AEM erkennt einige DDOS-Angriffe automatisch und blockiert sie. DDOS-Angriffe, die erkannt werden, sind nicht abrechenbar. |
| AEM as a Cloud Service-NewRelic-Überwachung | Ausgeschlossen | Globale AEM as a Cloud Service-Überwachung. |
| URL für Kundinnen und Kunden zur Überwachung ihres Cloud Service-Programms | Ausgeschlossen | Empfohlene URL zur externen Überwachung der Verfügbarkeit.<br><br>`/system/probes/health` |
| Pod-Warm-up-Service für AEM as a Cloud Service | Ausgeschlossen | Benutzeragent: skyline-service-warmup/1.* |
| Bekannte Suchmaschinen, soziale Netzwerke und HTTP-Bibliotheken (mit Tags von Fastly) | Ausgeschlossen | Bekannte Dienste, die die Site regelmäßig besuchen, um ihren Suchindex oder Dienst zu aktualisieren:<br><br>Beispiele:<br>• AddSearchBot<br>• AhrefsBot<br>• Applebot<br>• Ask Jeeves Corporate Spider<br>• Bingbot<br>• BingPreview<br>• BLEXBot<br>• BuiltWith<br>• Bytespider<br>• CrawlerKengo<br>• Facebookexternalhit<br>• Google AdsBot<br>• Google AdsBot Mobile<br>• Googlebot<br>• Googlebot Mobile<br>• lmspider<br>• LucidWorks<br>• MJ12bot<br>• Pingdom<br>• Pinterest<br>• SemrushBot<br>• SiteImprove<br>• StashBot<br>• StatusCake<br>• YandexBot |
| Commerce Integration Framework-Aufrufe | Ausgeschlossen | Dabei handelt es sich um Anfragen an AEM, die an das Commerce Integration Framework weitergeleitet werden. Die URL beginnt mit `/api/graphql`. Um eine doppelte Zählung zu vermeiden, sind sie für den Cloud-Service nicht abrechenbar. |
| Ausschließen von `manifest.json` | Ausgeschlossen | Manifest ist kein API-Aufruf, sondern bietet Informationen zur Installation von Websites auf Desktops oder Mobiltelefonen. Adobe sollte eine JSON-Anfrage an `/etc.clientlibs/*/manifest.json` nicht zählen |
| Ausschließen von `favicon.ico` | Ausgeschlossen | Obwohl der zurückgegebene Inhalt nicht HTML oder JSON sein sollte, stellen wir fest, dass in einigen Szenarien wie SAML-Authentifizierungabläufen Favicons als HTML zurückgegeben werden können und daher explizit von der Zählung ausgeschlossen sind. |

## Client-seitige Sammlung {#cliendside-collection}

### Real User Monitoring-Dienst für AEM as a Cloud Service {#real-user-monitoring-service-for-aem-as-a-cloud-service}

>[!INFO]
>
>Diese Funktion ist nur für das Early-Adopter-Programm verfügbar.
>Sie müssen die AEM Cloud Service-Version **2023.11.14227** oder höher verwenden, um den RUM-Daten-Service zu aktivieren.

### Überblick {#overview}

Der Real User Monitoring-Dienst ist eine Art von Technologie zur Leistungsüberwachung, die die digitalen Benutzererlebnisse einer Website oder Anwendung in Echtzeit erfasst und analysiert. Er ermöglicht einen Einblick in die Echtzeit-Leistung einer Web-Anwendung und bietet genaue Einblicke in das Benutzererlebnis.

Der Real User Monitoring-Dienst bietet einen tiefen Einblick in die wichtigsten Leistungsmetriken von der Initiierung der URL bis zur Rückgabe der Anfrage an den Browser. Dies alles hilft den Entwicklerinnen und Entwicklern, die Anwendung zu verbessern, um die Verwendung für die Endbenutzenden zu vereinfachen.

### Wer kann vom Real User Monitoring-Dienst profitieren? {#who-can-benefit-from-rum-service}

Der RUM-Datendienst ist für alle Kundinnen und Kunden von Vorteil, unabhängig davon, ob sie Adobe oder ihr eigenes CDN verwenden. Er bietet eine präzisere Darstellung der Benutzerinteraktionen und gewährleistet eine zuverlässige Messung der Website-Interaktion, indem er die Anzahl der Seitenansichten auf Client-Seite widerspiegelt.

Insbesondere werden Benutzerinteraktionen für Adobe-CDN-Benutzende genau verfolgt, um einen direkten Vergleich zwischen Client-seitigen Seitenansichten und Server-seitigen CDN-Protokollen zu ermöglichen.

Kundinnen und Kunden, die ihr eigenes CDN verwenden, können von der vereinfachten Traffic-Berichterstellung profitieren, da Adobe jetzt diese Seitenansichten direkt integriert, sodass keine separaten Berichte mehr erforderlich sind.

Darüber hinaus erhalten alle Kundinnen und Kunden tiefe Einblicke in die Seitenleistung, um ihre digitalen Erlebnisse effektiv zu optimieren.

### Erfahren Sie, wie der Real User Monitoring-Dienst funktioniert {#understand-how-the-rum-service-works}

Adobe Experience Manager verwendet Real User Monitoring (RUM), um Kundinnen und Kunden sowie Adobe zu helfen, zu verstehen, wie Besucherinnen und Besucher mit Adobe Experience Manager-gestützten Sites interagieren, Leistungsprobleme zu diagnostizieren und die Effektivität von Experimenten zu messen. RUM bewahrt die Privatsphäre der Besucherinnen und Besucher durch Stichproben – nur ein kleiner Teil aller Seitenansichten wird überwacht – und den sorgfältigen Ausschluss aller persönlich identifizierbaren Informationen (PII).

### Real User Monitoring-Dienst und Datenschutz {#rum-service-and-privacy}

Der Real User Monitoring-Dienst in Adobe Experience Manager wurde so konzipiert, dass der Datenschutz der Besucherinnen und Besucher gewahrt und die Datenerfassung minimiert wird. Als Besucherin bzw. Besucher bedeutet dies für Sie, dass keine persönlichen Daten durch die von Ihnen besuchte Website erfasst oder an Adobe weitergegeben werden.

Als Site-Operator bedeutet dies für Sie, dass kein zusätzliches Opt-in erforderlich ist, um die Überwachung durch diese Funktion zu aktivieren. Daher gibt es kein zusätzliches Popup, das von den Benutzerinnen oder Benutzern für die Aktivierung der RUM-Überwachung akzeptieren werden muss.

### Daten-Sampling für den Real User Monitoring-Dienst {#rum-service-data-sampling}

Herkömmliche Web-Analyse-Lösungen versuchen, Daten zu allen Besucherinnen und Besuchern zu erfassen. Der Real User Monitoring-Dienst von Adobe Experience Manager erfasst nur Informationen aus einem kleinen Bruchteil der Seitenansichten. Die Daten des Real User Monitoring-Dienstes dienen dazu, gesampelt und anonymisiert zu werden, und gelten nicht als Ersatz für die Analyse. Standardmäßig haben Seiten ein Stichprobenverhältnis von 1:100. Site-Operatoren können diese Zahl nicht einfach so konfigurieren, dass die Sampling-Rate ab heute erhöht oder verringert wird. Um den gesamten Traffic genau zu schätzen, erfassen wir für jeweils 100 Seitenansichten detaillierte Daten von einer Ansicht, um Ihnen einen zuverlässigen Näherungswert des gesamten Traffics zu ermöglichen.“

Da die Entscheidung darüber, ob die Daten erfasst werden, für jede einzelne Seitenansicht erfolgt, ist es praktisch unmöglich, Interaktionen über mehrere Seiten hinweg zu verfolgen. RUM hat kein Konzept von Besuchen, Besucherinnen und Besuchern oder Sitzungen, nur von Seitenansichten. Das ist beabsichtigt.

### Welche Daten werden erfasst? {#what-data-is-being-collected}

Der Real User Monitoring-Dienst wurde so konzipiert, dass die Erfassung von personenbezogenen Daten verhindert wird. Die vollständigen Informationen, die durch den Real User Monitoring-Dienst von Adobe Experience Manager erfasst werden können, finden Sie im Folgenden:

* Der Host-Name der besuchten Site, beispielsweise: `experienceleague.adobe.com`
* Der allgemeine Benutzeragenten-Typ, der zur Anzeige der Seite verwendet wird, z. B. Desktop oder Mobilgerät
* Der Zeitpunkt der Datenerfassung, z. B.: `2021-06-26 06:00:02.596000 UTC (in order to preserve privacy, we round all minutes to the previous hour, so that only seconds and milliseconds are tracked)`
* Die URL der besuchten Seite, z. B.: `https://experienceleague.adobe.com/docs`
* Die Referrer-URL (die URL der Seite, die mit der aktuellen Seite verknüpft ist, wenn die Person einem Link gefolgt ist)
* Eine zufällig generierte ID der Seitenansicht in einem Format, das dem folgenden ähnelt: `2Ac6`
* Die Gewichtung oder der Kehrwert der Stichprobenrate, beispielsweise: `100`. Das bedeutet, dass nur eine von hundert Seitenansichten aufgezeichnet wird
* Der Checkpoint oder Name eines bestimmten Ereignisses in der Abfolge des Ladens der Seite oder der Interaktion mit ihr als Besucherin oder Besucher
* Die Quelle oder die Kennung des DOM-Elements, mit dem die Person für den oben genannten Checkpoint interagiert. Dies kann beispielsweise ein Bild sein.
* Die Zielgruppe oder der Link zu einer externen Seite oder Ressource, mit der die Person für den oben genannten Checkpoint interagiert. Beispiel: `https://blog.adobe.com/jp/publish/2022/06/29/media_162fb947c7219d0537cce36adf22315d64fb86e94.png`
* Die Leistungsmetriken „Core Web Vitals“ (CWV), „Largest Contentful Paint“ (LCP), „First Input Delay“ (FID) und „Cumulative Layout Shift“ (CLS), die die Erlebnisqualität der Besucherin oder des Besuchers beschreiben.

### Einrichten des Real User Monitoring-Dienstes {#how-to-set-up-the-rum-service}

* Wenn Sie Teil unseres Early Adopter-Programms sein möchten, senden Sie bitte eine E-Mail an `aemcs-rum-adopter@adobe.com` zusammen mit Ihrem Domain-Namen für die Produktions-, Staging- und Entwicklungsumgebung von Ihrer E-Mail-Adresse aus, die mit Ihrer Adobe-ID verknüpft ist. Das Produkt-Team von Adobe aktiviert dann für Sie den Datendienst für das Real User Monitoring (RUM).
* Sobald dies abgeschlossen ist, erstellt das Produkt-Team von Adobe einen Kanal für die Zusammenarbeit mit Kundinnen und Kunden.
* Das Produkt-Team von Adobe wird sich mit Ihnen in Verbindung setzen, um Ihnen den Domain-Schlüssel und die URL des Daten-Dashboards mitzuteilen, unter der Sie die Seitenansichten und die Metriken [Core Web Vitals (CWV)](https://web.dev/vitals/) einsehen können, die von der Client-seitigen Sammlung des Real User Monitoring-Dienstes erfasst wurden.
* Anschließend erfahren Sie, wie Sie mit dem Domain-Schlüssel auf die Daten-Dashboard-URL zugreifen und die Metriken anzeigen können.

### Wie die Daten des Real User Monitoring-Dienstes verwendet werden {#how-rum-service-data-is-being-used}

RUM-Daten sind für folgende Zwecke von Vorteil:

* Identifizieren und Beheben von Leistungsengpässen bei Kunden-Sites
* Optimierte, automatische Traffic-Berichte, die Seitenansichten für die Kundinnen und Kunden enthalten, die ihr eigenes CDN verwenden. Dies bedeutet, dass sie keinen Traffic-Bericht mit Adobe teilen müssen.
* Um zu verstehen, wie Adobe Experience Manager mit anderen Skripten (z. B. Analyse, Targeting oder externen Bibliotheken) auf derselben Seite interagiert, und die Kompatibilität zu erhöhen.

### Einschränkungen und Verstehen von Abweichungen bei Seitenansichten und Leistungsmetriken {#limitations-and-understanding-variance-in-page-views-and-performance-metrics}

Da Sie diese Daten analysieren werden, kann es Abweichungen bei Seitenansichten und anderen Leistungsmetriken geben, die von Real User Monitoring (RUM) gemeldet werden. Diese Abweichungen können verschiedenen Faktoren zugeschrieben werden, die mit der Client-seitigen Überwachung in Echtzeit verbunden sind. Im Folgenden finden Sie wichtige Hinweise, die Kundinnen und Kunden bei der Interpretation ihrer RUM-Daten beachten sollten:

1. **Tracker-Blocker**

   * Endbenutzende, die Tracker-Blocker oder Datenschutzerweiterungen verwenden, können die Datenerfassung des Real User Monitoring-Dienstes behindern, da diese Tools die Ausführung von Tracking-Skripten einschränken. Diese Einschränkung kann dazu führen, dass zu wenig Seitenaufrufe und Benutzerinteraktionen gemeldet werden, was zu einer Diskrepanz zwischen den tatsächlichen Aktivitäten auf der Website und den von RUM erfassten Daten führt.

1. **Einschränkungen bei der Erfassung von API-/JSON-Aufrufen**

   * Der RUM-Datendienst konzentriert sich auf das Client-seitige Erlebnis und erfasst derzeit nicht die Backend-API- oder JSON-Aufrufe. Der Ausschluss dieser Aufrufe aus den Daten des Real User Monitoring-Dienstes führt zu Abweichungen von den von CDN Analytics gemessenen Inhaltsanforderungen.

### FAQs {#faq}

1. **Wie kann ich Pfade konfigurieren, sodass sie für die Überwachung ein- oder ausgeschlossen werden?**

   Kundinnen und Kunden können Pfade konfigurieren, um die URLs für die Überwachung ein- oder auszuschließen, indem sie die Umgebungsvariablen in der Konfiguration in Cloud Manager mithilfe der folgenden Variablen festlegen: `AEM_WEBVITALS_EXCLUDE` und `AEM_WEBVITALS_INCLUDE_PATHS`.

   Bitte beachten Sie, dass die Einstellung „include“ standardmäßig auf „/content“ festgelegt ist. Denken Sie daran, dass es sich bei den Pfaden, die Sie hier konfigurieren müssen, um Inhaltspfade innerhalb des Systems handelt, nicht um die URL-Pfade, die Sie in Ihrem Browser sehen. Diese Unterscheidung ist für die genaue Einrichtung und Anpassung Ihrer Konfiguration an Ihre spezifischen Anforderungen von entscheidender Bedeutung.

1. **Wäre Adobe in der Lage, alle Seitenaufrufe zu verfolgen, bevor die Interaktion das kundenseitig verwaltete CDN erreicht, oder zu dem Zeitpunkt, an dem die Interaktion das kundenseitig verwaltete CDN erreicht?**

   Ja. 

1. **Kann die Kundschaft die RUM-Datendienstskripte in Drittanbietersysteme wie Dynatrace integrieren?**

   Ja. 

1. **Werden die Web Vitals-Metriken „Interaktion mit der nächsten Farbe“, „Zeit bis zum ersten Byte“ und „Erste inhaltsreiche Farbe“ erfasst?**

   Interaktion mit der nächsten Farbe (INP) und Zeit bis zum ersten Byte (TTFB) werden erfasst.  Die erste inhaltsreiche Farbe wird derzeit nicht erfasst.
