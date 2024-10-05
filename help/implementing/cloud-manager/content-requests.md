---
title: Grundlegendes zu Cloud Service-Inhaltsanfragen
description: Wenn Sie Lizenzen für Inhaltsanfragen von Adobe erworben haben, können Sie mehr über die Arten von Inhaltsanfragen, die Adobe Experience Cloud as a Service misst, und über die Abweichungen von den Analytics-Reporting-Tools eines Unternehmens erfahren.
exl-id: 3666328a-79a7-4dd7-b952-38bb60f0967d
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 16941385a05358d9a5cf3f57405b8f2174902af2
workflow-type: tm+mt
source-wordcount: '1278'
ht-degree: 53%

---

# Grundlegendes zu Inhaltsanforderungen von Cloud Services

## Einführung {#introduction}

Inhaltsanfragen beziehen sich auf Anfragen an AEM Sites, einschließlich Anforderungen im Zusammenhang mit Edge Delivery Services oder kundenbereitgestellten Caching-Systemen wie einem Content Delivery Network. Diese Anfragen stellen HTML-Inhalte oder -Daten über Seitenansichten (z. B. Seiten und Experience Fragments) oder per API-Aufrufen Headless-Art im JSON-Format bereit. Inhaltsanfragen werden entweder als Seitenansichten oder fünf API-Aufrufe gezählt und an der Einfahrt des ersten Caching-Systems gemessen, das eine Inhaltsanfrage erhält. Bestimmte HTTP-Anfragen werden beim Zählen von Inhaltsanfragen ein- oder ausgeschlossen. Die vollständige Liste der eingeschlossenen und ausgeschlossenen HTTP-Anfragen sowie deren technische Definitionen finden Sie in der Dokumentation.

## Über Inhaltsanforderungen von Cloud Services {#understanding-cloud-service-content-requests}

Für Kundinnen und Kunden, die das vordefinierte CDN verwenden, werden Cloud Service-Inhaltsanfragen über die Server-seitige Datenerfassung gemessen. Diese Erfassung wird über die Analyse des CDN-Protokolls aktiviert.  AEM (Adobe Experience Manager) as a Cloud Service erfasst Inhaltsanforderungen automatisch Server-seitig am Edge. Es analysiert Protokolldateien, die vom AEM as a Cloud Service CDN generiert wurden. Dieser Vorgang erfolgt durch Isolieren der Anforderungen, die HTML `(text/html)`- oder JSON `(application/json)`-Inhalte aus dem CDN zurückgeben, und basiert auf mehreren unten beschriebenen Einschluss- und Ausschlussregeln. Eine Inhaltsanforderung erfolgt unabhängig davon, ob der Inhalt von den CDN-Caches bereitgestellt oder an die CDN-Herkunft (AEM Dispatcher) zurückgegeben wird.

<!-- REMOVED AS PER EMAIL REQUEST FROM SHWETA DUA, JULY 30, 2024 TO RICK BROUGH AND ALEXANDRU SARCHIZ   For customers employing their own CDN, client-side collection offers a more precise reflection of interactions, ensuring a reliable measure of website engagement via the [Real Use Monitoring](/help/sites-cloud/administering/real-use-monitoring-for-aem-as-a-cloud-service.md) service. This gives customers advanced insights into their page traffic and performance. While it is beneficial for all customers, it offers a representative reflection of user interactions, ensuring a reliable measure of website engagement by capturing the number of page views from the client side. 

For customers that bring their own CDN on top of AEM as a Cloud Service, server-side reporting results in numbers that cannot be used to compare with the licensed content requests. With the [Real Use Monitoring](/help/sites-cloud/administering/real-use-monitoring-for-aem-as-a-cloud-service.md), Adobe can reflect a reliable measure of website engagement. -->

### Varianten von Inhaltsanfragen für Cloud Service {#content-requests-variances}

Inhaltsanfragen können innerhalb der Analytics-Reporting-Tools eines Unternehmens Abweichungen aufweisen, wie in der folgenden Tabelle zusammengefasst. Vermeiden Sie im Allgemeinen die Verwendung von Analysetools, die auf clientseitige Instrumentierung angewiesen sind, um die Anzahl der Inhaltsanforderungen für eine Site zu melden. Bei diesen Tools wird häufig ein großer Teil des Traffics verpasst, da sie von der Aktivierung der Benutzerzustimmung abhängen. Analytics-Tools, die Daten Server-seitig in Protokolldateien sammeln, oder CDN-Berichte für Kunden, die ihr eigenes CDN zusätzlich zu AEM as a Cloud Service hinzufügen, bieten bessere Zählungen.

| Grund für die Abweichung | Erklärung |
|---|---|
| Zustimmung der Endbenutzenden | Für Analytics-Tools, die auf eine Client-seitige Instrumentation angewiesen sind, ist die Auslösung häufig von einer Benutzerzustimmung abhängig. Dieser Workflow könnte den Großteil des nicht verfolgten Traffics ausmachen. Für Kundinnen und Kunden, die Inhaltsanfragen selbst messen möchten, werden Analytics-Tools, die Daten Server-seitig erfassen, oder CDN-Berichte empfohlen. |
| Tagging | Alle Seiten oder API-Aufrufe, die als Adobe Experience Manager-Inhaltsanfragen erfasst werden, können nicht zum Analytics-Tracking getaggt werden. |
| Tag-Management-Regeln | Die Einstellungen von Tag-Management-Regeln können auf einer Seite unterschiedliche Datenerfassungskonfigurationen zur Folge haben, was zu einigen Diskrepanzen beim Tracking von Inhaltsanfragen führt. |
| Bots | Unbekannte Bots, die nicht voridentifiziert und entfernt AEM, können zu Tracking-Diskrepanzen führen. |
| Report Suites | Seiten, die Teil derselben AEM-Instanz und -Domain sind, können Daten an verschiedene Analytics Report Suites senden. |
| Überwachungs- und Sicherheits-Tools von Drittanbietern | Überwachungs- und Sicherheitsüberprüfungs-Tools können Inhaltsanfragen für AEM generieren, die in Analytics-Berichten nicht erfasst werden. |
| API-Zugriff | Der programmgesteuerte Zugriff auf Seiten oder Adobe Experience Manager-APIs kann Inhaltsanfragen für AEM generieren, die in Analytics-Berichten nicht erfasst werden. |
| Vorheriges Abrufen von Anfragen | Die Verwendung eines Vorabruf-Services zum Vorladen von Seiten, um die Geschwindigkeit zu erhöhen, kann zu erheblichen Traffic-Zunahmen bei Inhaltsanfragen führen. |
| DDOS | Während Adobe versucht, Traffic automatisch aus DDOS-Angriffen zu erkennen und herauszufiltern, gibt es keine Garantie, dass alle möglichen DDOS-Angriffe erkannt werden. |
| Traffic-Blocker | Die Verwendung eines Tracker-Blockers in einem Browser kann die Nachverfolgung mancher Anfragen verhindern. |
| Firewalls | Firewalls können das Analytics-Tracking blockieren. Dies ist vor allem bei Unternehmens-Firewalls häufiger der Fall. |

Siehe auch [Lizenz-Dashboard](/help/implementing/cloud-manager/license-dashboard.md).

## Serverseitige Erfassungsregeln {#serverside-collection}

Es gibt Regeln, um bekannte Bots auszuschließen, einschließlich bekannter Services, die die Site regelmäßig besuchen, um ihren Suchindex oder -Service zu aktualisieren.

### Arten von enthaltenen Inhaltsanfragen {#included-content-requests}

| Abfragetyp | Inhaltsanfrage | Beschreibung |
| --- | --- | --- |
| HTTP-Code 100–299 | Einschließlich | Regelmäßige Anforderungen, die den gesamten oder einen Teil des Inhalts bereitstellen. |
| HTTP-Bibliotheken für die Automatisierung | Einschließlich | Beispiele:<br> ・ Amazon CloudFront<br> ・ Apache Http Client<br> ・ asynchroner HTTP-Client<br> ・ Axios<br> ・ Azureus<br> ・ Curl<br> GitHub-Knotenabruf<br> x Guzzle<br> anstatt Go-Client<br> Headless Chrome<br> Java Client<br> Seitenjersey<br> Knoten x Oembed<br> x okhttp<br> x Python Requests<br> Reactor Netty<br> zwget<br> x WinHTTP<br> x Fast HTTP<br> x GitHub-Knoten Fetch<br> Reactor Netty |
| Tools für die Überwachung und Konsistenzprüfung | Einschließlich | Wird vom Kunden eingerichtet, um einen bestimmten Aspekt der Site zu überwachen. Dazu gehören die Verfügbarkeit oder die tatsächliche Benutzerleistung. Wenn sie für Konsistenzprüfungen auf bestimmte Endpunkte wie `/system/probes/health` abzielen, empfiehlt Adobe, den `/system/probes/health` -Endpunkt und nicht die eigentlichen HTML-Seiten der Site zu verwenden. [Siehe unten](#excluded-content-request)<br>Beispiele:<br> ・ `Amazon-Route53-Health-Check-Service`<br> ・ EyeMonIT_bot_version_0.1_[(https://eyemonit.com/)](https://eyemonit.com/)<br> ・ Investis-Site24x7<br> ・ Mozilla/5.0+(kompatibel; UptimeRobot/2.0; [https://uptimerobot.com/](https://uptimerobot.com/))<br> Tausend. yes-Dragonfly-x1<br> ・ OmtrBot/1.0<br> ・ WebMon/2.0.0 |
| `<link rel="prefetch">`-Anfragen | Einschließlich | Um das Laden der nächsten Seite zu beschleunigen, können Kundinnen und Kunden eine Reihe von Seiten in den Browser laden, bevor Benutzende auf den Link klicken, sodass sie sich bereits im Cache befinden. *Achtung: Dieser Ansatz erhöht den Traffic erheblich* - je nachdem, wie viele dieser Seiten vorabgerufen werden. |
| Traffic, der das Adobe Analytics- oder Google Analytics-Reporting blockiert | Einschließlich | Es kommt häufiger vor, dass Menschen, die Sites besuchen, Datenschutz-Software installiert haben (Adblocker usw.), die die Genauigkeit von Google Analytics oder Adobe Analytics beeinträchtigt. AEM as a Cloud Service zählt Anfragen beim ersten Einstiegspunkt in die von Adobe betriebene Infrastruktur und nicht auf der Client-Seite. |

Siehe auch [Lizenz-Dashboard](/help/implementing/cloud-manager/license-dashboard.md).

### Typen von ausgeschlossenen Inhaltsanfragen {#excluded-content-request}

| Abfragetyp | Inhaltsanfrage | Beschreibung |
| --- | --- | --- |
| HTTP-Code 500+ | Ausgeschlossen | Fehler, die an Besucherinnen und Besucher zurückgegeben werden, wenn bei AEM as a Cloud Service oder im benutzerspezifischen Code ein Fehler auftritt. |
| HTTP-Code 400–499 | Ausgeschlossen | Fehler, die an Besucherinnen und Besucher zurückgegeben werden, wenn der Inhalt nicht vorhanden ist (404) oder andere inhalts- oder anfragebezogene Probleme vorliegen. |
| HTTP-Code 300–399 | Ausgeschlossen | Gute Anforderungen, die entweder überprüfen, ob sich auf dem Server etwas geändert hat, oder die Anfrage an eine andere Ressource umleiten. Sie enthalten selbst keine Inhalte, daher sind sie nicht abrechenbar. |
| Anfragen für /libs/* | Ausgeschlossen | AEM interne JSON-Anfragen, z. B. das CSRF-Token, das nicht abrechenbar ist. |
| Traffic durch DDOS-Angriffe | Ausgeschlossen | DDOS-Schutz. AEM erkennt einige DDOS-Angriffe automatisch und blockiert sie. DDOS-Angriffe, die erkannt werden, sind nicht abrechenbar. |
| NewRelic-Überwachung für AEM as a Cloud Service | Ausgeschlossen | Globale AEM as a Cloud Service-Überwachung. |
| URL für Kundinnen und Kunden zur Überwachung ihres Cloud Service-Programms | Ausgeschlossen | Adobe empfiehlt, die URL zu verwenden, um die Verfügbarkeit oder Konsistenzprüfung extern zu überwachen.<br><br>`/system/probes/health` |
| Pod-Warm-up-Service für AEM as a Cloud Service | Ausgeschlossen |
| Agent: skyline-service-warmup/1.* |
| Bekannte Suchmaschinen, soziale Netzwerke und HTTP-Bibliotheken (mit Tags von Fastly) | Ausgeschlossen | Bekannte Dienste, die die Site regelmäßig besuchen, um ihren Suchindex oder -dienst zu aktualisieren:<br><br>Beispiele:<br> ・ AddSearchBot<br> ・ AhrefsBot<br> ・ Applebot<br> ・ Ask Jeeves Corporate Spider<br> ・ Bingbot<br> ・ BingPreview<br> ・ BLEXBot<br> espider<br> x CrawlerKengo<br> x Facebookexternalhit<br> x Google AdsBot<br> x Google AdsBot Mobile<br> x googlebot<br> x GoogleBot Mobile<br> x lmspider<br> x LucidWorks<br> 19} Pinterest<br> Seitenaufruf-Bot<br> Seitenverbesserungen<br> x StashBot<br> x StatusCake<br> nach YandexBot<br> nach Claudebot<br>`MJ12bot`<br> |
| Commerce Integration Framework-Aufrufe | Ausgeschlossen | Anfragen an AEM, die an die Commerce integration framework weitergeleitet werden - die URL beginnt mit `/api/graphql` -, um eine doppelte Zählung zu vermeiden, sind für den Cloud Service nicht abrechnungsfähig. |
| Ausschließen von `manifest.json` | Ausgeschlossen | Manifest ist kein API-Aufruf. Hier finden Sie Informationen zur Installation von Websites auf einem Desktop- oder Mobiltelefon. Adobe sollte eine JSON-Anfrage an `/etc.clientlibs/*/manifest.json` nicht zählen |
| Ausschließen von `favicon.ico` | Ausgeschlossen | Obwohl der zurückgegebene Inhalt nicht HTML oder JSON sein sollte, wurde festgestellt, dass bestimmte Szenarien wie SAML-Authentifizierungsflüsse Favicons als HTML zurückgeben. Daher werden Favicons explizit aus der Zählung ausgeschlossen. |
| CDN-Proxy zu einem anderen Backend | Ausgeschlossen | Anfragen, die mit der Methode[CDN-Ursprungs-Auswahlen](/help/implementing/dispatcher/cdn-configuring-traffic.md#origin-selectors) an andere AEM-fremde Backends weitergeleitet werden, werden ausgeschlossen, da sie AEM nicht treffen. |
