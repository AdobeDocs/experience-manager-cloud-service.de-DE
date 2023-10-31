---
title: Grundlegendes zu Cloud Service-Inhaltsanforderungen
description: Wenn Sie Lizenzen für Inhaltsanforderungen von Adobe erworben haben, erfahren Sie mehr über die Arten von Inhaltsanforderungen, die Adobe Experience Cloud as a Service misst, und über die Abweichungen mit den Analytics-Reporting-Tools eines Unternehmens.
exl-id: 3666328a-79a7-4dd7-b952-38bb60f0967d
source-git-commit: 25a4a6b9ae09cb71f50317990af1718db1e14355
workflow-type: tm+mt
source-wordcount: '1171'
ht-degree: 12%

---

# Cloud Service-Inhaltsanforderungen

## Varianzen von Inhaltsanforderungen von Cloud Services{#content-requests-variances}

Inhaltsanforderungen können Abweichungen von den Analytics-Reporting-Tools eines Unternehmens aufweisen, wie in der folgenden Tabelle zusammengefasst. Im Allgemeinen können Analytics-Tools Daten mithilfe Client-seitiger Instrumentierung erfassen <b>darf nicht angewendet werden</b> um über die Anzahl der Inhaltsanfragen für eine bestimmte Site zu berichten, einfach weil sie häufig davon abhängen, dass die Endnutzerzustimmung ausgelöst wird, sodass sie bei einem erheblichen Teil des Traffics fehlen. Analytics-Tools, die Daten Server-seitig in Protokolldateien sammeln, oder CDN-Berichte für Kunden, die zusätzlich zu AEM as a Cloud Service ihr eigenes CDN hinzufügen, bieten bessere Zählungen. Für die Berichterstellung über Seitenansichten und die damit verbundene Leistung ist der Adobe RUM-Datendienst die Adobe empfohlene Option.

| Grund für die Abweichung | Erklärung |
|---|---|
| Zustimmung des Endbenutzers | Analytics-Tools, die auf clientseitige Instrumente angewiesen sind, hängen häufig davon ab, dass die Zustimmung des Endbenutzers ausgelöst wird. Dies könnte den Großteil des Traffics ausmachen, der nicht verfolgt wird. Kunden, die Inhaltsanfragen allein messen möchten, sollten sich auf Analytics-Tools verlassen, die Daten Server-seitig oder CDN-Berichte erfassen. |
| Tagging | Alle Seiten oder API-Aufrufe, die als Adobe Experience Manager (AEM)-Inhaltsanfragen verfolgt werden, werden möglicherweise nicht mit Analytics-Tracking getaggt. |
| Tag-Management-Regeln | Die Einstellungen von Tag-Management-Regeln können zu verschiedenen Datenerfassungskonfigurationen auf einer Seite führen, was zu einigen Kombinationen von Diskrepanzen beim Tracking von Inhaltsanforderungen führt. |
| Bots | Unbekannte Bots, die nicht vorab identifiziert und von AEM entfernt wurden, können zu Tracking-Diskrepanzen führen. |
| Report Suites | Seiten, die Teil derselben AEM-Instanz und -Domain sind, können Daten an verschiedene Analytics Report Suites senden. |
| Überwachungs- und Sicherheits-Tools von Drittanbietern | Überwachungs- und Sicherheitsüberprüfungs-Tools können Inhaltsanfragen für AEM generieren, die in Analytics-Berichten nicht erfasst werden. |
| API-Zugriff | Der programmatische Zugriff auf Seiten oder Adobe Experience Manager-APIs kann Inhaltsanforderungen für AEM generieren, die in Analytics-Berichten nicht verfolgt werden. |
| Vorheriges Abrufen von Anfragen | Die Verwendung eines Vorabruf-Services zum Vorladen von Seiten, um die Geschwindigkeit zu erhöhen, kann zu erheblichen Traffic-Zunahmen bei Inhaltsanfragen führen. |
| DDOS | Adobe unternimmt zwar alle Anstrengungen, um Traffic durch DDOS-Angriffe automatisch zu erkennen und herauszufiltern, aber es gibt keine Garantie dafür, dass alle möglichen DDOS-Angriffe erkannt werden |
| Traffic-Blocker | Die Verwendung eines Tracker-Blockers in einem Browser kann die Nachverfolgung mancher Anfragen verhindern. |
| Firewalls | Firewalls können das Analytics-Tracking blockieren. Dieses Szenario tritt bei Firewalls des Unternehmens häufiger auf. |

Siehe auch [Lizenz-Dashboard](/help/implementing/cloud-manager/license-dashboard.md).

## Grundlegendes zu Cloud Service-Inhaltsanforderungen {#about-content-request}

Inhaltsanforderungen werden automatisch am Rand von Adobe Experience Manager (AEM) as a Cloud Service verfolgt, indem die Protokolldateien aus dem AEM as a Cloud Service CDN automatisiert analysiert und die Anfragen isoliert werden, die HTML- (text/html) oder JSON-- (application/json) Inhalt aus dem CDN zurückgeben, und basierend auf einer Reihe von Einschluss- und Ausschlussregeln, die nachfolgend beschrieben werden. Eine Inhaltsanforderung erfolgt unabhängig vom zurückgegebenen Inhalt, der von den CDN-Caches bereitgestellt wird oder zurück an die Herkunft des CDN (AEM Dispatcher) geht.

Für Kunden, die ihr eigenes CDN über AEM as a Cloud Service bringen, führt dieses Tracking zu Zahlen, die nicht zum Vergleich mit den lizenzierten Inhaltsanfragen verwendet werden können und vom Kunden am Rand des äußeren CDN gemessen werden müssen.

Es gibt Regeln, um bekannte Bots auszuschließen, einschließlich bekannter Dienste, die die Site regelmäßig besuchen, um ihren Suchindex oder -dienst zu aktualisieren.

### Typen der enthaltenen Inhaltsanfragen{#included-content-requests}

| Anfragetyp | Inhaltsanforderung | Beschreibung |
| --- | --- | --- |
| HTTP-Code 100-299 | Einschließlich | Hierbei handelt es sich um reguläre Anfragen, die alle oder nur teilweise Inhalte bereitstellen. |
| HTTP-Bibliotheken für Automatisierung | Einschließlich | Beispiele:<br>・ Amazon CloudFront<br>・ Apache Http Client<br>・ Asynchroner HTTP-Client<br>・ Axios<br>Azureus<br>・ Curl<br>・ GitHub-Knotenabruf<br>・ Guzzle<br>・ Gohttp-client<br>・ Headless-Chrome<br>・ Java™ Client<br>Jersey<br>・ Knoteneinbettung<br>・ okhttp<br>Python-Anfragen<br>・ Reactor Netty<br>・ Wget<br>・ WinHTTP |
| Tools zur Überwachung und Konsistenzprüfung | Einschließlich | Diese werden vom Kunden eingerichtet, um einen bestimmten Aspekt der Site zu überwachen. Beispielsweise Verfügbarkeit oder reale Benutzerleistung. Verwendung `/system/probes/health` -Endpunkt und nicht die eigentlichen HTML-Seiten von der Site.<br>Beispiele:<br>・ Amazon-Route53-Health-Check-Service<br>・ EyeMonIT_bot_version_0.1_[(https://www.eyemon.it/)](https://www.eyemon.it/)<br>・ Investis-Site24x7<br>・ Mozilla/5.0+(kompatibel; UptimeRobot/2.0; [https://uptimerobot.com/](https://uptimerobot.com/))<br>ThousandEyes-Dragonfly-x1<br>OmtrBot/1.0<br>・ WebMon/2.0.0 |
| `<link rel="prefetch">` requests | Einschließlich | Um das Laden der nächsten Seite zu beschleunigen, können Kunden vom Browser eine Reihe von Seiten laden lassen, bevor der Benutzer auf den Link klickt, sodass sie sich bereits im Cache befinden. *Denken: Dadurch wird der Traffic deutlich erhöht*- abhängig davon, wie viele dieser Seiten vorabgerufen werden. |
| Traffic, der die Berichterstellung für Adobe Analytics oder Google Analytics blockiert | Einschließlich | Es kommt häufiger vor, dass für Besucher von Websites Datenschutzsoftware installiert ist (Anzeigenblocker usw.), die die Genauigkeit von Google Analytics oder Adobe Analytics beeinträchtigt. AEM as a Cloud Service zählt Anforderungen beim ersten Einstiegspunkt in die von der Adobe betriebene Infrastruktur und nicht auf der Clientseite. |

Siehe auch [Lizenz-Dashboard](/help/implementing/cloud-manager/license-dashboard.md).

### Typen von ausgeschlossenen Inhaltsanfragen{#excluded-content-request}

| Anfragetyp | Inhaltsanforderung | Beschreibung |
| --- | --- | --- |
| HTTP-Code 500+ | Ausgeschlossen | Fehler, die an den Besucher zurückgegeben werden, wenn bei AEM as a Cloud Service Code oder dem benutzerspezifischen Code ein Fehler auftritt. |
| HTTP-Code 400-499 | Ausgeschlossen | Fehler, die an den Besucher zurückgegeben werden, wenn der Inhalt nicht vorhanden ist (404) oder andere Inhalte oder anfragebezogene Probleme vorliegen. |
| HTTP-Code 300-399 | Ausgeschlossen | Dies sind gute Anfragen, die entweder überprüfen, ob sich auf dem Server etwas geändert hat, oder die Anfrage an eine andere Ressource weiterleiten. Sie enthalten keine Inhalte selbst, daher sind sie nicht abrechnungsfähig. |
| Anforderungen für /libs/* | Ausgeschlossen | AEM interne JSON-Anforderungen, z. B. das CSRF-Token, das nicht abrechenbar ist. |
| Traffic durch DDOS-Angriffe | Ausgeschlossen | DDOS-Schutz. AEM erkennt einige DDOS-Angriffe automatisch und blockiert sie. DDOS-Angriffe werden nicht abgerechnet, wenn sie erkannt werden.<br><br>Automatisch erkannte DDOS-Typen:<br>・ DDOSBlockedCiphersSHA<br>・ DDOSBlockedPattern<br>・ DDOSSuspiciousRequest |
| AEM as a Cloud Service NewRelic-Überwachung | Ausgeschlossen | AEM as a Cloud Service globale Überwachung. |
| URL für Kunden zur Überwachung ihres Cloud Service-Programms | Ausgeschlossen | Empfohlene URL zur externen Überwachung der Verfügbarkeit.<br><br>`/system/probes/health` |
| AEM as a Cloud Service Warm-up-Dienst für Werbeunterbrechungen | Ausgeschlossen | Benutzeragent: skyline-service-warmup/1.* |
| Bekannte Suchmaschinen, soziale Netzwerke und HTTP-Bibliotheken (mit Tags von Fastly) | Ausgeschlossen | Bekannte Dienste, die die Site regelmäßig besuchen, um ihren Suchindex oder -dienst zu aktualisieren:<br><br>Beispiele:<br>・ AddSearchBot<br>AhrefsBot<br>Applebot<br>・ Fragen an Jeeves Corporate Spider<br>Bingbot<br>・ BingPreview<br>BLEXBot<br>・ BuiltWith<br>Bytespider<br>CrawlerKengo<br>・ Facebook-externalhit<br>・ Google AdsBot<br>・ Google AdsBot Mobile<br>・ GoogleBot<br>・ GoogleBot Mobile<br>lmspider<br>LucidWorks<br>・ MJ12bot<br>・ Pingom<br>・ Pinterest<br>SemrushBot<br>・ SiteVerbessern<br>StashBot<br>・ StatusCake<br>YandexBot |
| Commerce integration framework-Aufrufe ausschließen | Ausgeschlossen | Dies sind Anfragen an AEM, die an die Commerce integration framework weitergeleitet werden - die URL beginnt mit `/api/graphql`—um eine doppelte Zählung zu vermeiden, sind sie für den Cloud Service nicht abrechenbar. |
| Ausschließen `manifest.json` | Ausgeschlossen | Manifest ist kein API-Aufruf. Hier finden Sie Informationen zur Installation von Websites auf Desktop- oder Mobiltelefonen. Adobe sollte JSON-Anfrage nicht zählen zu `/etc.clientlibs/*/manifest.json` |
| Ausschließen `favicon.ico` | Ausgeschlossen | Obwohl der zurückgegebene Inhalt nicht HTML oder JSON sein sollte, stellen wir fest, dass in einigen Szenarien wie SAML-Authentifizierungsflüssen Favicons zurückgegeben werden können, da HTML daher explizit von der Zählung ausgeschlossen ist. |
