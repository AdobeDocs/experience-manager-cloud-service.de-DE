---
title: Grundlegendes zu Cloud Service-Inhaltsanfragen
description: Wenn Sie Lizenzen für Inhaltsanfragen von Adobe erworben haben, können Sie mehr über die Arten von Inhaltsanfragen, die Adobe Experience Cloud as a Service misst, und über die Abweichungen von den Analytics-Reporting-Tools eines Unternehmens erfahren.
exl-id: 3666328a-79a7-4dd7-b952-38bb60f0967d
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: f57d90078b5fc0e0c8a79ca60cbc19e7b37323cd
workflow-type: tm+mt
source-wordcount: '1250'
ht-degree: 96%

---

# Grundlegendes zu Cloud Service-Inhaltsanfragen

## Einführung {#introduction}

Inhaltsanfragen beziehen sich auf Anfragen an AEM Sites, einschließlich Anfragen im Zusammenhang mit Edge Delivery Services oder kundenseitig bereitgestellten Caching-Systemen wie einem Content Delivery Network. Diese Anfragen stellen Inhalte oder Daten im HTML-Format über Seitenansichten (z. B. Seiten und Experience Fragments) oder im JSON-Format über API-Aufrufe (Headless) bereit. Inhaltsanfragen werden entweder als ein Seitenaufruf oder als fünf API-Aufrufe gezählt, gemessen am Eingang des ersten Caching-Systems, das eine Inhaltsanfrage erhält.  Bestimmte HTTP-Anfragen werden beim Zählen von Inhaltsanfragen ein- bzw. ausgeschlossen. Die vollständige Liste der ein- und ausgeschlossenen HTTP-Anfragen sowie deren technische Definitionen finden Sie in der Dokumentation.

## Über Cloud Service-Inhaltsanfragen {#understanding-cloud-service-content-requests}

Für Kundinnen und Kunden, die das vordefinierte CDN verwenden, werden Cloud Service-Inhaltsanfragen über die Server-seitige Datenerfassung gemessen. Diese Erfassung wird über die Analyse des CDN-Protokolls aktiviert.  AEM (Adobe Experience Manager) as a Cloud Service erfasst Inhaltsanfragen automatisch Server-seitig am Edge. Es analysiert Protokolldateien, die vom AEM as a Cloud Service-CDN generiert wurden. Dies geschieht durch Isolieren der Anfragen, die HTML-Inhalte `(text/html)` oder JSON-Inhalte `(application/json)` aus dem CDN zurückgeben, und basiert auf verschiedenen Ein- und Ausschlussregeln, die im Folgenden erläutert werden. Eine Inhaltsanfrage erfolgt unabhängig davon, ob der Inhalt von den CDN-Caches bereitgestellt oder an den CDN-Ursprung (AEM-Dispatcher) zurückgeht.

<!-- REMOVED AS PER EMAIL REQUEST FROM SHWETA DUA, JULY 30, 2024 TO RICK BROUGH AND ALEXANDRU SARCHIZ   For customers employing their own CDN, client-side collection offers a more precise reflection of interactions, ensuring a reliable measure of website engagement via the [Real Use Monitoring](/help/sites-cloud/administering/real-use-monitoring-for-aem-as-a-cloud-service.md) service. This gives customers advanced insights into their page traffic and performance. While it is beneficial for all customers, it offers a representative reflection of user interactions, ensuring a reliable measure of website engagement by capturing the number of page views from the client side. 

For customers that bring their own CDN on top of AEM as a Cloud Service, server-side reporting results in numbers that cannot be used to compare with the licensed content requests. With the [Real Use Monitoring](/help/sites-cloud/administering/real-use-monitoring-for-aem-as-a-cloud-service.md), Adobe can reflect a reliable measure of website engagement. -->

### Abweichungen von Cloud Service-Inhaltsanfragen {#content-requests-variances}

Inhaltsanfragen können Abweichungen von den Analytics-Reporting-Tools eines Unternehmens aufweisen, die in der folgenden Tabelle zusammengefasst sind. Vermeiden Sie im Allgemeinen die Verwendung von Analyse-Tools, die auf eine Client-seitige Instrumentation angewiesen sind, um die Anzahl der Inhaltsanfragen für eine Site zu melden. Bei diesen Tools wird häufig ein großer Teil des Traffics verpasst, da ihre Aktivierung von einer Benutzerzustimmung abhängt. Analyse-Tools, die Daten Server-seitig in Protokolldateien sammeln, oder CDN-Berichte für Kundinnen und Kunden, die zusätzlich zu AEM as a Cloud Service ihr eigenes CDN hinzufügen, bieten bessere Zählungen. 

| Grund für die Abweichung | Erklärung |
|---|---|
| Zustimmung der Endbenutzenden | Für Analytics-Tools, die auf eine Client-seitige Instrumentation angewiesen sind, ist die Auslösung häufig von einer Benutzerzustimmung abhängig. Dieser Workflow könnte den Großteil des Traffics ausmachen, der nicht erfasst wird. Für Kundinnen und Kunden, die Inhaltsanfragen selbst messen möchten, werden Analytics-Tools, die Daten Server-seitig erfassen, oder CDN-Berichte empfohlen. |
| Tagging | Alle Seiten oder API-Aufrufe, die als Adobe Experience Manager-Inhaltsanfragen erfasst werden, können nicht zum Analytics-Tracking getaggt werden. |
| Tag-Management-Regeln | Die Einstellungen von Tag-Management-Regeln können auf einer Seite unterschiedliche Datenerfassungskonfigurationen zur Folge haben, was zu einigen Diskrepanzen beim Tracking von Inhaltsanfragen führt. |
| Bots | Unbekannte Bots, die nicht vorab von AEM identifiziert und entfernt wurden, können zu Tracking-Diskrepanzen führen. |
| Report Suites | Seiten, die Teil derselben AEM-Instanz und -Domain sind, können Daten an verschiedene Analytics Report Suites senden. |
| Überwachungs- und Sicherheits-Tools von Drittanbietern | Überwachungs- und Sicherheitsüberprüfungs-Tools können Inhaltsanfragen für AEM generieren, die in Analytics-Berichten nicht erfasst werden. |
| API-Zugriff | Der programmgesteuerte Zugriff auf Seiten oder Adobe Experience Manager-APIs kann Inhaltsanfragen für AEM generieren, die in Analytics-Berichten nicht erfasst werden. |
| Vorheriges Abrufen von Anfragen | Die Verwendung eines Vorabruf-Services zum Vorladen von Seiten, um die Geschwindigkeit zu erhöhen, kann zu erheblichen Traffic-Zunahmen bei Inhaltsanfragen führen. |
| DDOS | Adobe unternimmt zwar Anstrengungen, um Traffic durch DDOS-Angriffe automatisch zu erkennen und herauszufiltern, aber es gibt keine Garantie dafür, dass alle möglichen DDOS-Angriffe erkannt werden. |
| Traffic-Blocker | Die Verwendung eines Tracker-Blockers in einem Browser kann die Nachverfolgung mancher Anfragen verhindern. |
| Firewalls | Firewalls können das Analytics-Tracking blockieren. Dies ist vor allem bei Unternehmens-Firewalls häufiger der Fall. |

Siehe auch [Lizenz-Dashboard](/help/implementing/cloud-manager/license-dashboard.md).

## Regeln für die Server-seitige Sammlung {#serverside-collection}

Es gibt Regeln, um bekannte Bots auszuschließen, einschließlich bekannter Services, die die Site regelmäßig besuchen, um ihren Suchindex oder -Service zu aktualisieren.

### Arten von enthaltenen Inhaltsanfragen {#included-content-requests}

| Abfragetyp | Inhaltsanfrage | Beschreibung |
| --- | --- | --- |
| HTTP-Code 100–299 | Einschließlich | Reguläre Anfragen, die vollständige oder partielle Inhalte bereitstellen. |
| HTTP-Bibliotheken für die Automatisierung | Einschließlich | Zum Beispiel:<br>• Amazon CloudFront<br>• Apache Http Client<br>• Asynchronous HTTP Client<br>• Axios<br>• Azureus<br>• Curl<br>• GitHub Node Fetch<br>• Guzzle<br>• Go-http-client<br>• Headless Chrome<br>• Java™ Client<br>• Jersey<br>• Node Oembed<br>• okhttp<br>• Python Requests<br>• Reactor Netty<br>• Wget<br>• WinHTTP<br>• Fast HTTP<br>• GitHub Node Fetch<br>• Reactor Netty |
| Tools für die Überwachung und Konsistenzprüfung | Einschließlich | Einrichtung auf Kundenseite, um einen bestimmten Aspekt der Site zu überwachen. Dazu gehören die Verfügbarkeit oder die tatsächliche Benutzerleistung. Wenn für Konsistenzprüfungen auf bestimmte Endpunkte wie `/system/probes/health` abgezielt werden soll, empfiehlt Adobe, den Endpunkt `/system/probes/health` und nicht die eigentlichen HTML-Seiten der Site zu verwenden. [Siehe die nachfolgenden](#excluded-content-request)<br>Beispiele:<br>• `Amazon-Route53-Health-Check-Service`<br>• EyeMonIT_bot_version_0.1_[(https://eyemonit.com/)](https://eyemonit.com/)<br>• Investis-Site24x7<br>• Mozilla/5.0+(compatible; UptimeRobot/2.0; [https://uptimerobot.com/](https://uptimerobot.com/))<br>• ThousandEyes-Dragonfly-x1<br>• OmtrBot/1.0<br>• WebMon/2.0.0 |
| `<link rel="prefetch">`-Anfragen | Einschließlich | Um das Laden der nächsten Seite zu beschleunigen, können Kundinnen und Kunden eine Reihe von Seiten in den Browser laden, bevor Benutzende auf den Link klicken, sodass sie sich bereits im Cache befinden. *Denken Sie daran: Dadurch nimmt der Traffic deutlich zu*, abhängig davon, wie viele dieser Seiten vorabgerufen werden. |
| Traffic, der das Adobe Analytics- oder Google Analytics-Reporting blockiert | Einschließlich | Es kommt häufiger vor, dass Menschen, die Sites besuchen, Datenschutz-Software installiert haben (Adblocker usw.), die die Genauigkeit von Google Analytics oder Adobe Analytics beeinträchtigt. AEM as a Cloud Service zählt Anfragen beim ersten Einstiegspunkt in die von Adobe betriebene Infrastruktur und nicht auf der Client-Seite. |

Siehe auch [Lizenz-Dashboard](/help/implementing/cloud-manager/license-dashboard.md).

### Typen von ausgeschlossenen Inhaltsanfragen {#excluded-content-request}

| Abfragetyp | Inhaltsanfrage | Beschreibung |
| --- | --- | --- |
| HTTP-Code 500+ | Ausgeschlossen | Fehler, die an Besucherinnen und Besucher zurückgegeben werden, wenn bei AEM as a Cloud Service oder im benutzerspezifischen Code ein Fehler auftritt. |
| HTTP-Code 400–499 | Ausgeschlossen | Fehler, die an Besucherinnen und Besucher zurückgegeben werden, wenn der Inhalt nicht vorhanden ist (404) oder andere inhalts- oder anfragebezogene Probleme vorliegen. |
| HTTP-Code 300–399 | Ausgeschlossen | Nützliche Anfragen, die entweder überprüfen, ob sich auf dem Server etwas geändert hat, oder die Anfrage an eine andere Ressource weiterleiten. Sie enthalten selbst keine Inhalte, daher sind sie nicht abrechenbar. |
| Anfragen für /libs/* | Ausgeschlossen | AEM interne JSON-Anfragen, z. B. das CSRF-Token, das nicht abrechenbar ist. |
| Traffic durch DDOS-Angriffe | Ausgeschlossen | DDOS-Schutz. AEM erkennt einige DDOS-Angriffe automatisch und blockiert sie. DDOS-Angriffe, die erkannt werden, sind nicht abrechenbar. |
| NewRelic-Überwachung für AEM as a Cloud Service | Ausgeschlossen | Globale AEM as a Cloud Service-Überwachung. |
| URL für Kundinnen und Kunden zur Überwachung ihres Cloud Service-Programms | Ausgeschlossen | Adobe empfiehlt, die URL zu verwenden, um die Verfügbarkeit oder Konsistenzprüfung extern zu überwachen.<br><br>`/system/probes/health` |
| Pod-Warm-up-Service für AEM as a Cloud Service | Ausgeschlossen |
| Agent: skyline-service-warmup/1.* |
| Bekannte Suchmaschinen, soziale Netzwerke und HTTP-Bibliotheken (mit Tags von Fastly) | Ausgeschlossen | Bekannte Dienste, die die Website regelmäßig besuchen, um ihren Suchindex oder -service zu aktualisieren:<br><br>Beispiele:<br>・ AddSearchBot<br>・ AhrefsBot<br>・ Applebot<br>・ Ask Jeeves Corporate Spider<br>・ Bingbot<br>・ BingPreview<br>・ BLEXBot<br>・ BuiltWith<br>・ Bytespider<br>・ CrawlerKengo<br>・ FacebookExternalhit<br>・ Google AdsBot<br> Google AdsBot Mobile<br>・ GoogleBot Mobile<br>・ lmspider<br>・ LucidWorks<br>・ `MJ12bot`<br>・ Pinterest<br>・ SiteImimproving<br>・ StashBot<br>・ StatusCake<br>・ YandexBot<br> <br> <br> <br>・ ContentKingBot |
| Commerce Integration Framework-Aufrufe | Ausgeschlossen | Anfragen an AEM, die an das Commerce Integration Framework weitergeleitet werden. Die URL beginnt mit `/api/graphql`. Um eine doppelte Zählung zu vermeiden, sind sie für den Cloud-Service nicht abrechenbar. |
| Ausschließen von `manifest.json` | Ausgeschlossen | Manifest ist kein API-Aufruf. Es bietet Informationen zur Installation von Websites auf Desktops oder Mobiltelefonen. Adobe sollte eine JSON-Anfrage an `/etc.clientlibs/*/manifest.json` nicht zählen |
| Ausschließen von `favicon.ico` | Ausgeschlossen | Obwohl der zurückgegebene Inhalt nicht HTML oder JSON sein sollte, wurde festgestellt, dass in einigen Szenarien wie bei SAML-Authentifizierungsabläufen Favicons als HTML zurückgegeben wurden. Daher werden Favicons explizit aus der Zählung ausgeschlossen. |
