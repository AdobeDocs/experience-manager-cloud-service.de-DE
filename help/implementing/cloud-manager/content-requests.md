---
title: Grundlegendes zu Cloud Service-Inhaltsanfragen
description: Wenn Sie Lizenzen für Inhaltsanfragen von Adobe erworben haben, können Sie mehr über die Arten von Inhaltsanfragen, die Adobe Experience Cloud as a Service misst, und über die Abweichungen von den Analytics-Reporting-Tools eines Unternehmens erfahren.
exl-id: 3666328a-79a7-4dd7-b952-38bb60f0967d
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: bd207a7c3e9e5e52202456fa95dd31293639725f
workflow-type: tm+mt
source-wordcount: '1464'
ht-degree: 46%

---

# Grundlegendes zu Cloud Service-Inhaltsanfragen

## Einführung {#introduction}

Inhaltsanfragen enthalten Anfragen, die an AEM Sites gesendet werden. Diese Anfragen können über Edge Delivery Services oder vom Kunden bereitgestellte Caching-Systeme wie ein Content Delivery Network (CDN) weitergeleitet werden. Diese Anfragen liefern strukturierte Daten im HTML- oder JSON-Format und unterstützen Seitenansichten (z. B. Seiten und Experience Fragments) oder JSON-Rückgaben über APIs auf Headless-Weise.

Das System zählt Inhaltsanfragen, wenn eine Benutzerin oder ein Benutzer eine Seite mithilfe von HTML oder JSON anzeigt. Er misst die Anfrage an der Stelle, an der das erste Caching-System sie erhält. Bestimmte HTTP-Anfragen werden beim Zählen von Inhaltsanfragen ein- bzw. ausgeschlossen. Siehe die vollständige Liste der HTTP[enthaltenen Inhaltsanfragen](#included-content-requests) und [ausgeschlossenen Inhaltsanfragen](#excluded-content-request).

## Über Cloud Service-Inhaltsanfragen {#understanding-cloud-service-content-requests}

Eine *Seitenanfrage* bezieht sich auf eine HTTP-Anfrage, die strukturierte Kerninhalte abruft (z. B. HTML oder JSON), die zum Rendern des Hauptseitenerlebnisses erforderlich sind. Es enthält keine Anfragen für Assets wie Bilder oder Skripte.

Für Kunden, die das vorkonfigurierte CDN verwenden, zählt AEM as a Cloud Service Inhaltsanfragen, gemessen auf Server-seitiger Ebene. Diese Messung erfolgt automatisch und ist nicht auf das Client-seitige Analytics-Tracking angewiesen.

AEM (Adobe Experience Manager) as a Cloud Service identifiziert Inhaltsanfragen anhand der von der AEM-Instanz generierten und im CDN empfangenen Antworttypen. Insbesondere werden Anfragen gezählt, die HTML (`text/html`) oder JSON (`application/json`) zurückgeben. Diese Formate stellen in der Regel primäre Seiteninhalte entweder für das herkömmliche Website-Rendering oder für die Headless-Bereitstellung bereit.

Anfragen für statische Assets wie JavaScript-Dateien, CSS-Stylesheets und Bilder werden nicht als Inhaltsanfragen gezählt.

>[!NOTE]
>Wenn eine API-Anfrage HTML oder JSON zurückgibt, die als Inhalt auf Seitenebene dienen (z. B. bei der Headless-Bereitstellung), kann sie je nach Kontext dennoch als Inhaltsanfrage gezählt werden.

Inhaltsanfragen werden unabhängig davon gemessen, ob die Antwort vom CDN-Cache bereitgestellt oder an die ursprüngliche AEM-Umgebung weitergeleitet wurde.

<!-- REMOVED AS PER EMAIL REQUEST FROM SHWETA DUA, JULY 30, 2024 TO RICK BROUGH AND ALEXANDRU SARCHIZ   For customers employing their own CDN, client-side collection offers a more precise reflection of interactions, ensuring a reliable measure of website engagement via the [Real Use Monitoring](/help/sites-cloud/administering/real-use-monitoring-for-aem-as-a-cloud-service.md) service. This gives customers advanced insights into their page traffic and performance. While it is beneficial for all customers, it offers a representative reflection of user interactions, ensuring a reliable measure of website engagement by capturing the number of page views from the client side. 

For customers that bring their own CDN on top of AEM as a Cloud Service, server-side reporting results in numbers that cannot be used to compare with the licensed content requests. With the [Real Use Monitoring](/help/sites-cloud/administering/real-use-monitoring-for-aem-as-a-cloud-service.md), Adobe can reflect a reliable measure of website engagement. -->

### Abweichungen von Cloud Service-Inhaltsanfragen {#content-requests-variances}

Inhaltsanfragen können innerhalb der Analytics-Reporting-Tools einer Organisation Abweichungen aufweisen, wie in der folgenden Tabelle zusammengefasst. Vermeiden Sie im Allgemeinen die Verwendung von Analyse-Tools, die auf eine Client-seitige Instrumentation angewiesen sind, um die Anzahl der Inhaltsanfragen für eine Site zu melden. Bei diesen Tools wird häufig ein großer Teil des Traffics verpasst, da ihre Aktivierung von einer Benutzerzustimmung abhängt. Analyse-Tools, die Daten Server-seitig in Protokolldateien sammeln, oder CDN-Berichte für Kundinnen und Kunden, die zusätzlich zu AEM as a Cloud Service ihr eigenes CDN hinzufügen, bieten bessere Zählungen. 

| Grund für die Abweichung | Erklärung |
|---|---|
| Zustimmung der Endbenutzenden | Für Analytics-Tools, die auf eine Client-seitige Instrumentation angewiesen sind, ist die Auslösung häufig von einer Benutzerzustimmung abhängig. Dieser Workflow könnte den Großteil des Traffics ausmachen, der nicht erfasst wird. Für Kunden, die Inhaltsanfragen eigenständig messen möchten, empfiehlt Adobe, sich zur Datenerfassung aus Server-seitigen oder CDN-Berichten auf Analytics-Tools zu verlassen. |
| Tagging | Alle Seiten oder API-Aufrufe, die als Adobe Experience Manager-Inhaltsanfragen erfasst werden, können nicht zum Analytics-Tracking getaggt werden. |
| Tag-Management-Regeln | Die Einstellungen von Tag-Management-Regeln können auf einer Seite unterschiedliche Datenerfassungskonfigurationen zur Folge haben, was zu einigen Diskrepanzen beim Tracking von Inhaltsanfragen führt. |
| Bots | Unbekannte Bots, die nicht vorab von AEM identifiziert und entfernt wurden, können zu Tracking-Diskrepanzen führen. |
| Report Suites | Seiten innerhalb derselben AEM-Instanz können an verschiedene Analytics Report Suites berichten. Dieser Prozess kann Daten je nach Konfiguration auf mehrere Suites aufteilen. |
| Überwachungs- und Sicherheits-Tools von Drittanbietern | Überwachungs- und Sicherheitsprüfungs-Tools (z. B. Uptime Checker oder Vulnerability Scanner) können Seiten anfordern und so Server-seitige Inhaltsanfragen generieren, die in Analytics-Berichten nicht sichtbar sind. |
| API-Zugriff | Anfragen an AEM-Seiten oder -Inhalte über APIs (z. B. über Adobe Experience Manager as a Headless CMS) zählen weiterhin als Inhaltsanfragen, jedoch nicht zum Trigger-Analyse-Tracking. |
| Vorheriges Abrufen von Anfragen | Ein Vorabruf (z. B. mit einem Service Worker oder einer Edge-Funktion) kann das Traffic-Volumen erhöhen, indem Seiten im Voraus angefordert werden. Diese Anfragen werden Server-seitig gezählt, führen jedoch keinen Client-seitigen Analytics-Code aus. |
| DDOS | Adobe verwendet Filter, um viele DDoS-Angriffe zu erkennen und zu blockieren. Einige Angriffsanfragen werden jedoch möglicherweise noch als Inhaltsanfragen gezählt, bevor Filter angewendet werden. |
| Traffic-Blocker | Browser-interne Datenschutzfunktionen oder Unternehmens-Firewalls können das Laden von Analytics-Skripten blockieren. Diese Benutzenden generieren weiterhin Server-seitige Inhaltsanfragen. |
| Firewalls | Unternehmens- oder regionale Firewalls können verhindern, dass Analytics-Aufrufe die Adobe-Server erreichen, was zu einem unzureichenden Reporting in Analytics führt, während die Server-seitige Anzahl nicht betroffen ist. |

Informationen [ Anzeigen und Nachverfolgen der Nutzung von Inhaltsanfragen anhand Ihrer ](/help/implementing/cloud-manager/license-dashboard.md) finden Sie im Lizenzdashboard.

## Regeln für die Server-seitige Sammlung {#serverside-collection}

AEM as a Cloud Service wendet Server-seitige Regeln an, um Inhaltsanfragen zu zählen. Zu diesen Regeln gehört die Logik, um bekannte Bots (wie Suchmaschinen-Crawler) und Nicht-Benutzer-Traffic wie Überwachungs-Services, die regelmäßig Ping auf der Website durchführen, auszuschließen.

In der folgenden Tabelle sind die Typen der eingeschlossenen und ausgeschlossenen Inhaltsanfragen mit kurzen Beschreibungen aufgeführt.

### Arten von enthaltenen Inhaltsanfragen {#included-content-requests}

>[!NOTE]
>Wenn eine API-Anfrage eine HTML-Antwort zurückgibt, kann sie je nach Nutzungskontext als Inhaltsanfrage klassifiziert werden. API-Anfragen, die Nicht-UI-Daten zurückgeben, sind in der Regel ausgeschlossen.

| Abfragetyp | Inhaltsanfrage | Beschreibung |
| --- | --- | --- |
| HTTP-Code 100–299 | Einschließlich | Umfasst erfolgreiche Anfragen, die HTML- oder JSON-Inhalte vollständig oder teilweise zurückgeben.<br>HTTP-Code 206: Diese Anfragen liefern nur einen Teil des gesamten Inhalts. Beispiel: ein Video oder ein großes Bild. Partielle Inhaltsanfragen sind enthalten, wenn sie einen Teil einer HTML- oder JSON-Antwort bereitstellen, die beim Rendern des Seiteninhalts verwendet wird. |
| HTTP-Bibliotheken für die Automatisierung | Einschließlich | Anfragen durch Tools oder Bibliotheken, die Seiteninhalte abrufen. Beispiele sind: <br>・ Amazon CloudFront<br>・ Apache HTTP Client<br>・ Asynchroner HTTP Client<br>・ Axios<br>・ Azureus<br>・ cURL<br>・ GitHub Node Fetch<br>・ Guzzle<br>・ Go-HTTP-Client<br>・ Headless Chrome<br>・ Java™ Client<br>・ Jersey<br>・ Oembed<br>・ Python-Anfragen<br> Reactor Netty<br>・ WGET<br> WinHTTP<br>・ Schneller HTTP<br> <br>・ GitHub Node Fetch<br> Reaktornetz |
| Tools für die Überwachung und Konsistenzprüfung | Einschließlich | Anfragen, die zur Überwachung des Zustands oder der Verfügbarkeit von Seiten verwendet werden.<br>Siehe [Typen ausgeschlossener Inhaltsanfragen](#excluded-content-request).<br>Beispiele: <br>・ `Amazon-Route53-Health-Check-Service`<br>・ EyeMonIT_bot_version_0.1_[(https://eyemonit.com/)](https://eyemonit.com/)<br>・ Investis-Site24x7<br>・ Mozilla/5.0+(kompatibel; UptimeRobot/2.0; [https://uptimerobot.com/](https://uptimerobot.com/))<br>・ ThousandEyes-Dragonfly-x1<br>・ OmtrBot/1.0<br>・ WebMon/2.0.0 |
| `<link rel="prefetch">`-Anfragen | Einschließlich | Wenn Kundinnen und Kunden Inhalte vorab laden oder abrufen (z. B. mit `<link rel="prefetch">`), zählt das System diese Server-seitigen Anfragen. Beachten Sie, dass dieser Ansatz den Traffic erhöhen kann, je nachdem, wie viele dieser Seiten vorab abgerufen werden. |
| Traffic, der das Adobe Analytics- oder Google Analytics-Reporting blockiert | Einschließlich | Es kommt häufiger vor, dass Menschen, die Sites besuchen, Datenschutz-Software installiert haben (Adblocker usw.), die die Genauigkeit von Google Analytics oder Adobe Analytics beeinträchtigt. AEM as a Cloud Service zählt Anfragen beim ersten Einstiegspunkt in die von Adobe betriebene Infrastruktur und nicht auf der Client-Seite. |

Siehe auch [Lizenz-Dashboard](/help/implementing/cloud-manager/license-dashboard.md).

### Typen von ausgeschlossenen Inhaltsanfragen {#excluded-content-request}

| Abfragetyp | Inhaltsanfrage | Beschreibung |
| --- | --- | --- |
| HTTP-Code 500+ | Ausgeschlossen | Fehler, die an Besucherinnen und Besucher zurückgegeben werden, wenn bei AEM as a Cloud Service oder im benutzerspezifischen Code ein Fehler auftritt. |
| HTTP-Code 400–499 | Ausgeschlossen | Fehler, die an Besucherinnen und Besucher zurückgegeben werden, wenn der Inhalt nicht vorhanden ist (404) oder andere inhalts- oder anfragebezogene Probleme vorliegen. |
| HTTP-Code 300–399 | Ausgeschlossen | Nützliche Anfragen, die entweder überprüfen, ob sich auf dem Server etwas geändert hat, oder die Anfrage an eine andere Ressource weiterleiten. Sie enthalten selbst keine Inhalte, daher sind sie nicht abrechenbar. |
| Anfragen an `/libs/`* | Ausgeschlossen | AEM interne JSON-Anfragen, z. B. das CSRF-Token, das nicht abrechenbar ist. |
| Traffic durch DDOS-Angriffe | Ausgeschlossen | DDOS-Schutz. AEM erkennt einige DDOS-Angriffe automatisch und blockiert sie. DDOS-Angriffe, die erkannt werden, sind nicht abrechenbar. |
| NewRelic-Überwachung für AEM as a Cloud Service | Ausgeschlossen | Globale AEM as a Cloud Service-Überwachung. |
| URL für Kundinnen und Kunden zur Überwachung ihres Cloud Service-Programms | Ausgeschlossen | Adobe empfiehlt, die URL zu verwenden, um die Verfügbarkeit oder Konsistenzprüfung extern zu überwachen.<br><br>`/system/probes/health` |
| Pod-Warm-up-Service für AEM as a Cloud Service | Ausgeschlossen |
| Agent: skyline-service-warmup/1.* |
| Bekannte Suchmaschinen, soziale Netzwerke und HTTP-Bibliotheken (mit Tags von Fastly) | Ausgeschlossen | Bekannte Dienste, die die Site regelmäßig besuchen, um ihren Suchindex oder Dienst zu aktualisieren:<br><br>Beispiele:<br>• AddSearchBot<br>• AhrefsBot<br>• Applebot<br>• Ask Jeeves Corporate Spider<br>• Bingbot<br>• BingPreview<br>• BLEXBot<br>• BuiltWith<br>• Bytespider<br>• CrawlerKengo<br>• Facebookexternalhit<br>• Google AdsBot<br>• Google AdsBot Mobile<br>• Googlebot<br>• Googlebot Mobile<br>• lmspider<br>• LucidWorks<br>• `MJ12bot`<br>• Pinterest<br>• SemrushBot<br>• SiteImprove<br>• StashBot<br>• StatusCake<br>• YandexBot<br>• ContentKing<br>• Claudebot |
| Commerce Integration Framework-Aufrufe | Ausgeschlossen | Anfragen an AEM, die an das Commerce Integration Framework weitergeleitet werden. Die URL beginnt mit `/api/graphql`. Um eine doppelte Zählung zu vermeiden, sind sie für den Cloud-Service nicht abrechenbar. |
| Ausschließen von `manifest.json` | Ausgeschlossen | Manifest ist kein API-Aufruf. Es bietet Informationen zur Installation von Websites auf Desktops oder Mobiltelefonen. Adobe sollte eine JSON-Anfrage an `/etc.clientlibs/*/manifest.json` nicht zählen |
| Ausschließen von `favicon.ico` | Ausgeschlossen | Obwohl der zurückgegebene Inhalt nicht HTML oder JSON sein sollte, wurde festgestellt, dass in einigen Szenarien wie bei SAML-Authentifizierungsabläufen Favicons als HTML zurückgegeben wurden. Daher werden Favicons explizit aus der Zählung ausgeschlossen. |
