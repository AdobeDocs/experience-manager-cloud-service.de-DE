---
title: Grundlegendes zu Cloud Service-Inhaltsanfragen
description: Wenn Sie Lizenzen für Inhaltsanfragen von Adobe erworben haben, können Sie mehr über die Arten von Inhaltsanfragen, die Adobe Experience Cloud as a Service misst, und über die Abweichungen von den Analytics-Reporting-Tools eines Unternehmens erfahren.
exl-id: 3666328a-79a7-4dd7-b952-38bb60f0967d
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: f9a767e3d5ae33cd46dc100c2ee59ec9ce8f63ac
workflow-type: tm+mt
source-wordcount: '1918'
ht-degree: 79%

---

# Grundlegendes zu Cloud Service-Inhaltsanfragen

## Einführung {#introduction}

Inhaltsanfragen umfassen an AEM Sites gesendete Anfragen. Diese Anfragen können über Edge Delivery Services oder kundenseitig bereitgestellte Caching-Systeme wie ein Content Delivery Network (CDN) weitergeleitet werden. Diese Anfragen liefern strukturierte Daten im HTML- oder JSON-Format und unterstützen Seitenansichten (z. B. Seiten und Experience Fragments) oder JSON-Rückgaben über APIs (Headless).

Das System zählt die Inhaltsanfragen, wenn eine Benutzerin oder ein Benutzer eine Seite mithilfe von HTML oder JSON anzeigt. Es erfasst die Anfrage dort, wo das erste Caching-System sie erhält. Bestimmte HTTP-Anfragen werden beim Zählen von Inhaltsanfragen ein- bzw. ausgeschlossen. Siehe die vollständige Liste der [eingeschlossenen HTTP-Inhaltsanfragen](#included-content-requests) und der [ausgeschlossenen HTTP-Inhaltsanfragen](#excluded-content-request).

>[!NOTE]
>
>Die in der Ansicht „Inhaltsanfragen“ angezeigten Daten werden alle 24 Stunden aktualisiert.

## Über Cloud Service-Inhaltsanfragen {#understanding-cloud-service-content-requests}

Eine *Seitenanfrage* bezieht sich auf eine HTTP-Anfrage, die strukturierte Kerninhalte (z. B. HTML oder JSON) zum Rendern der Hauptseite abruft. Dazu gehören keine Anfragen für Assets wie Bilder oder Skripte.

Für Kundinnen und Kunden, die das vorkonfigurierte CDN verwenden, zählt AEM as a Cloud Service Inhaltsanfragen so, wie sie Server-seitig erfasst werden. Diese Messung erfolgt automatisch und ist nicht auf Client-seitiges Analyse-Tracking angewiesen.

AEM (Adobe Experience Manager) as a Cloud Service identifiziert Inhaltsanfragen anhand der von der AEM-Instanz generierten und im CDN empfangenen Antworttypen. Insbesondere werden Anfragen gezählt, die HTML (`text/html`) oder JSON (`application/json`) zurückgeben. Diese Formate liefern in der Regel primäre Seiteninhalte zum herkömmlichen Rendern von Sites oder zur Headless-Bereitstellung.

Anfragen für statische Assets wie JavaScript-Dateien, CSS-Stylesheets und Bilder werden nicht als Inhaltsanfragen gezählt.

>[!NOTE]
>Wenn eine API-Anfrage HTML oder JSON zurückgibt, das als Inhalt auf Seitenebene dient (z. B. bei der Headless-Bereitstellung), kann sie je nach Kontext dennoch als Inhaltsanfrage gezählt werden.

Inhaltsanfragen werden unabhängig davon gemessen, ob die Antwort vom CDN-Cache bereitgestellt oder an die ursprüngliche AEM-Umgebung weitergeleitet wurde.

<!-- REMOVED AS PER EMAIL REQUEST FROM SHWETA DUA, JULY 30, 2024 TO RICK BROUGH AND ALEXANDRU SARCHIZ   For customers employing their own CDN, client-side collection offers a more precise reflection of interactions, ensuring a reliable measure of website engagement via the [Real Use Monitoring](/help/sites-cloud/administering/real-use-monitoring-for-aem-as-a-cloud-service.md) service. This gives customers advanced insights into their page traffic and performance. While it is beneficial for all customers, it offers a representative reflection of user interactions, ensuring a reliable measure of website engagement by capturing the number of page views from the client side. 

For customers that bring their own CDN on top of AEM as a Cloud Service, server-side reporting results in numbers that cannot be used to compare with the licensed content requests. With the [Real Use Monitoring](/help/sites-cloud/administering/real-use-monitoring-for-aem-as-a-cloud-service.md), Adobe can reflect a reliable measure of website engagement. -->

### Abweichungen von Cloud Service-Inhaltsanfragen {#content-requests-variances}

Inhaltsanfragen können Abweichungen von den Analyseberichts-Tools einer Organisation aufweisen, die in der folgenden Tabelle zusammengefasst sind. Vermeiden Sie im Allgemeinen die Verwendung von Analyse-Tools, die auf eine Client-seitige Instrumentation angewiesen sind, um die Anzahl der Inhaltsanfragen für eine Site zu melden. Bei diesen Tools wird häufig ein großer Teil des Traffics verpasst, da ihre Aktivierung von einer Benutzerzustimmung abhängt. Analyse-Tools, die Daten Server-seitig in Protokolldateien sammeln, oder CDN-Berichte für Kundinnen und Kunden, die zusätzlich zu AEM as a Cloud Service ihr eigenes CDN hinzufügen, bieten bessere Zählungen. 

| Grund für die Abweichung | Erklärung |
|---|---|
| Zustimmung der Endbenutzenden | Für Analytics-Tools, die auf eine Client-seitige Instrumentation angewiesen sind, ist die Auslösung häufig von einer Benutzerzustimmung abhängig. Dieser Workflow könnte den Großteil des Traffics ausmachen, der nicht erfasst wird. Für Kundinnen und Kunden, die Inhaltsanfragen selbst messen möchten, empfiehlt Adobe Analyse-Tools zur Server-seitigen Datenerfassung oder CDN-Berichte. |
| Tagging | Alle Seiten oder API-Aufrufe, die als Adobe Experience Manager-Inhaltsanfragen erfasst werden, können nicht zum Analytics-Tracking getaggt werden. |
| Tag-Management-Regeln | Die Einstellungen von Tag-Management-Regeln können auf einer Seite unterschiedliche Datenerfassungskonfigurationen zur Folge haben, was zu einigen Diskrepanzen beim Tracking von Inhaltsanfragen führt. |
| Bots | Unbekannte Bots, die nicht vorab von AEM identifiziert und entfernt wurden, können zu Tracking-Diskrepanzen führen. |
| Report Suites | Seiten innerhalb derselben AEM-Instanz können an verschiedene Analytics Report Suites berichten. Dabei können Daten je nach Konfiguration auf mehrere Suites aufgeteilt werden. |
| Überwachungs- und Sicherheits-Tools von Drittanbietern | Überwachungs- und Sicherheitsprüfungs-Tools (z. B. Uptime Checker oder Vulnerability Scanner) können Seiten anfordern und so Server-seitige Inhaltsanfragen generieren, die in Analyseberichten nicht sichtbar sind. |
| API-Zugriff | Anfragen an AEM-Seiten oder -Inhalte über APIs (z. B. über Adobe Experience Manager as a Headless CMS) zählen weiterhin als Inhaltsanfragen, lösen allerdings kein Analyse-Tracking aus. |
| Vorheriges Abrufen von Anfragen | Ein Vorabruf (z. B. mittels einer Service-Worker- oder Edge-Funktion) kann das Traffic-Volumen erhöhen, indem Seiten im Voraus angefordert werden. Diese Anfragen werden Server-seitig gezählt, führen jedoch keinen Client-seitigen Analyse-Code aus. |
| DDOS | Adobe verwendet Filter, um zahlreiche DDoS-Angriffe zu erkennen und zu blockieren. Einige im Rahmen eines Angriffs gestellte Anfragen werden jedoch möglicherweise noch als Inhaltsanfragen gezählt, bevor diese Filter angewendet werden. |
| Traffic-Blocker | Browser-interne Datenschutzfunktionen oder Unternehmens-Firewalls können das Laden von Analyseskripten blockieren. Diese Benutzenden generieren weiterhin Server-seitige Inhaltsanfragen. |
| Firewalls | Unternehmens- oder regionale Firewalls können verhindern, dass Analyse-Aufrufe die Adobe-Server erreichen, was zu einem unzureichenden Reporting in Analysen führen kann. Die Server-seitige Zählung ist davon nicht betroffen. |

Informationen zum Anzeigen und Nachverfolgen der Nutzung von Inhaltsanfragen anhand Ihres Lizenz-Limits finden Sie im [Lizenz-Dashboard](/help/implementing/cloud-manager/license-dashboard.md).

## Regeln für die Server-seitige Sammlung {#serverside-collection}

AEM as a Cloud Service wendet Server-seitige Sammlungsregeln an, um Inhaltsanfragen zu zählen. Diese Regeln schließen bekannte Bots (wie Suchmaschinen-Crawler) und eine Reihe von Überwachungs-Services aus, die die Website regelmäßig pingen. Anderer synthetischer oder Monitoring-artiger Traffic, der nicht auf dieser Ausschlussliste steht, wird als abrechnungsfähige Inhaltsanfrage gezählt.

In der folgenden Tabelle sind die Typen der eingeschlossenen und ausgeschlossenen Inhaltsanfragen mit jeweils kurzen Beschreibungen aufgeführt.

### Arten von enthaltenen Inhaltsanfragen {#included-content-requests}

>[!NOTE]
>Wenn eine API-Anfrage eine HTML-Antwort zurückgibt, kann sie je nach Nutzungskontext als Inhaltsanfrage klassifiziert werden. API-Anfragen, die Nicht-UI-Daten zurückgeben, werden in der Regel ausgeschlossen.

| Abfragetyp | Inhaltsanfrage | Beschreibung |
| --- | --- | --- |
| HTTP-Code 100–299 | Einschließlich | Umfasst erfolgreiche Anfragen, die HTML- oder JSON-Inhalte vollständig oder teilweise zurückgeben.<br>HTTP-Code 206: Diese Anfragen liefern nur einen Teil des gesamten Inhalts, z. B. ein Video oder ein großes Bild. Partielle Inhaltsanfragen werden eingeschlossen, wenn sie einen Teil einer HTML- oder JSON-Antwort bereitstellen, die beim Rendern des Seiteninhalts verwendet wird. |
| HTTP-Bibliotheken für die Automatisierung | Einschließlich | Anfragen durch Tools oder Bibliotheken, die Seiteninhalte abrufen. Beispiele dafür sind: <br>• Amazon CloudFront<br>• Apache Http Client<br>• Asynchronous HTTP Client<br>• Axios<br>• Azureus<br>• Curl<br>• GitHub Node Fetch<br>• Guzzle<br>• Go-http-client<br>• Headless Chrome<br>• Java™ Client<br>• Jersey<br>• Node Oembed<br>• okhttp<br>• Python Requests<br>• Reactor Netty<br>• Wget<br>• WinHTTP<br>• Fast HTTP<br>• GitHub Node Fetch<br>• Reactor Netty |
| Tools für die Überwachung und Konsistenzprüfung | Einschließlich | Anfragen, die zur Überwachung des Zustands oder der Verfügbarkeit von Seiten verwendet werden.<br>Siehe [Typen von ausgeschlossenen Inhaltsanfragen](#excluded-content-request).<br>Beispiele dafür sind:<br>• `Amazon-Route53-Health-Check-Service`<br>• EyeMonIT_bot_version_0.1_[(https://eyemonit.com/)](https://eyemonit.com/)<br>• Investis-Site24x7<br>• Mozilla/5.0+(compatible; UptimeRobot/2.0; [https://uptimerobot.com/](https://uptimerobot.com/))<br>• ThousandEyes-Dragonfly-x1<br>• OmtrBot/1.0<br>• WebMon/2.0.0 |
| `<link rel="prefetch">`-Anfragen | Einschließlich | Wenn Kundinnen und Kunden Inhalte vorab laden oder abrufen (z. B. mit `<link rel="prefetch">`), zählt das System diese Server-seitigen Anfragen. Denken Sie daran: Dadurch kann der Traffic zunehmen, abhängig davon, wie viele dieser Seiten vorab abgerufen werden. |
| Traffic, der das Adobe Analytics- oder Google Analytics-Reporting blockiert | Einschließlich | Es kommt häufiger vor, dass Menschen, die Sites besuchen, Datenschutz-Software installiert haben (Adblocker usw.), die die Genauigkeit von Google Analytics oder Adobe Analytics beeinträchtigt. AEM as a Cloud Service zählt Anfragen beim ersten Einstiegspunkt in die von Adobe betriebene Infrastruktur und nicht auf der Client-Seite. |

Siehe auch [Lizenz-Dashboard](/help/implementing/cloud-manager/license-dashboard.md).

### Typen von ausgeschlossenen Inhaltsanfragen {#excluded-content-request}

| Abfragetyp | Inhaltsanfrage | Beschreibung |
| --- | --- | --- |
| HTTP-Code 500+ | Ausgeschlossen | Fehler, die an Besucherinnen und Besucher zurückgegeben werden, wenn bei AEM as a Cloud Service oder im benutzerspezifischen Code ein Fehler auftritt. |
| HTTP-Code 400–499 | Ausgeschlossen | Fehler, die an Besucherinnen und Besucher zurückgegeben werden, wenn der Inhalt nicht vorhanden ist (404) oder andere inhalts- oder anfragebezogene Probleme vorliegen. |
| HTTP-Code 300–399 | Ausgeschlossen | Nützliche Anfragen, die entweder überprüfen, ob sich auf dem Server etwas geändert hat, oder die Anfrage an eine andere Ressource weiterleiten. Sie enthalten selbst keine Inhalte, daher sind sie nicht abrechenbar. |
| Anfragen für `/libs/`* | Ausgeschlossen | AEM interne JSON-Anfragen, z. B. das CSRF-Token, das nicht abrechenbar ist. |
| Traffic durch DDOS-Angriffe | Ausgeschlossen | DDOS-Schutz. AEM erkennt einige DDOS-Angriffe automatisch und blockiert sie. DDOS-Angriffe, die erkannt werden, sind nicht abrechenbar. |
| NewRelic-Überwachung für AEM as a Cloud Service | Ausgeschlossen | Globale AEM as a Cloud Service-Überwachung. |
| URL für Kundinnen und Kunden zur Überwachung ihres Cloud Service-Programms | Ausgeschlossen | Adobe empfiehlt, die URL zu verwenden, um die Verfügbarkeit oder Konsistenzprüfung extern zu überwachen.<br><br>`/system/probes/health` |
| Pod-Warm-up-Service für AEM as a Cloud Service | Ausgeschlossen | Agent: skyline-service-warmup/1.* |
| Bekannte Suchmaschinen, soziale Netzwerke und HTTP-Bibliotheken (mit Tags von Fastly) | Ausgeschlossen | Bekannte Dienste, die die Site regelmäßig besuchen, um ihren Suchindex oder Dienst zu aktualisieren:<br><br>Beispiele:<br>• AddSearchBot<br>• AhrefsBot<br>• Applebot<br>• Ask Jeeves Corporate Spider<br>• Bingbot<br>• BingPreview<br>• BLEXBot<br>• BuiltWith<br>• Bytespider<br>• CrawlerKengo<br>• Facebookexternalhit<br>• Google AdsBot<br>• Google AdsBot Mobile<br>• Googlebot<br>• Googlebot Mobile<br>• lmspider<br>• LucidWorks<br>• `MJ12bot`<br>• Pinterest<br>• SemrushBot<br>• SiteImprove<br>• StashBot<br>• StatusCake<br>• YandexBot<br>• ContentKing<br>• Claudebot |
| Commerce Integration Framework-Aufrufe | Ausgeschlossen | Anfragen an AEM, die an das Commerce Integration Framework weitergeleitet werden. Die URL beginnt mit `/api/graphql`. Um eine doppelte Zählung zu vermeiden, sind sie für den Cloud-Service nicht abrechenbar. |
| Ausschließen von `manifest.json` | Ausgeschlossen | Manifest ist kein API-Aufruf. Es bietet Informationen zur Installation von Websites auf Desktops oder Mobiltelefonen. Adobe sollte eine JSON-Anfrage an `/etc.clientlibs/*/manifest.json` nicht zählen |
| Ausschließen von `favicon.ico` | Ausgeschlossen | Obwohl der zurückgegebene Inhalt nicht HTML oder JSON sein sollte, wurde festgestellt, dass in einigen Szenarien wie bei SAML-Authentifizierungsabläufen Favicons als HTML zurückgegeben wurden. Daher werden Favicons explizit aus der Zählung ausgeschlossen. |
| Experience Fragment (XF) – Wiederverwendung derselben Domain | Ausgeschlossen | Anfragen an XF-Pfade (z. B. `/content/experience-fragments/...`) von Seiten, die auf derselben Domain gehostet werden (wie durch den Referrer-Header identifiziert, der mit dem Anfrage-Host übereinstimmt).<br><br> Beispiel: Eine Homepage auf `aem.customer.com`, die ein XF für ein Banner oder eine Karte aus derselben Domain abruft.<br><br>・ URL stimmt überein mit /content/experience-fragments/…<br>・ Referrer-Domain stimmt überein mit `request_x_forwarded_host`<br><br>**Hinweis:** Wenn der Experience Fragment-Pfad angepasst wird (z. B. mithilfe von `/XFrags/...` oder einem Pfad außerhalb von `/content/experience-fragments/`), wird die Anfrage nicht ausgeschlossen und kann gezählt werden, selbst wenn es sich um dieselbe Domain handelt. Es wird empfohlen, die standardmäßige XF-Pfadstruktur von Adobe zu verwenden, um sicherzustellen, dass die Ausschlusslogik korrekt angewendet wird. |

## Verwalten von Inhaltsanfragen {#managing-content-requests}

Wie im obigen Abschnitt [Varianzen von Cloud Service-Inhaltsanfragen](#content-requests-variances) erwähnt, können Inhaltsanfragen aus mehreren Gründen höher als erwartet sein, wobei ein gemeinsamer Thread im CDN-Traffic auftritt.  Als AEM-Kunde können Sie Ihre Inhaltsanfragen so überwachen und verwalten, dass sie in Ihr Lizenzbudget passen.  Die Verwaltung von Inhaltsanfragen ist im Allgemeinen eine Kombination aus Implementierungstechniken [ Traffic-Filterregeln](/help/security/traffic-filter-rules-including-waf.md).

### Implementierungstechniken für die Verwaltung von Inhaltsanfragen {#implementation-techniques-to-manage-crs}

* Stellen Sie sicher, dass alle Antworten vom Typ „Seite nicht gefunden“ mit dem HTTP-Status 404 zugestellt werden.  Wenn sie mit dem Status 200 zurückgegeben werden, werden sie für Inhaltsanfragen gezählt.
* Leiten Sie Konsistenzprüfungs- oder Überwachungs-Tools an die URL unter /system/probes/health oder verwenden Sie die HEAD-Methode anstelle von GET, um aufkommende Inhaltsanfragen zu vermeiden.
* Schaffen Sie ein ausgewogenes Verhältnis zwischen Ihren Anforderungen an die Aktualität von Inhalten und den AEM-Lizenzkosten für jeden benutzerdefinierten Such-Crawler, den Sie in Ihre Site integriert haben.  Ein übermäßig aggressiver Crawler kann viele Inhaltsanfragen verarbeiten.
* Behandeln Sie alle Weiterleitungen als Server-seitig (Status 301 oder 302) und nicht Client-seitig (Status 200 mit JavaScript-Weiterleitung), um zwei separate Inhaltsanfragen zu vermeiden.
* Kombinieren oder reduzieren Sie API-Aufrufe, bei denen es sich um JSON-Antworten von AEM handelt, die geladen werden können, um die Seite zu rendern.

### Traffic-Filterregeln zur Verwaltung von Inhaltsanfragen {#traffic-filter-rules-to-manage-crs}

* Ein gängiges Bot-Muster besteht darin, einen leeren Benutzeragenten zu verwenden.  Sie müssen Ihre Implementierung und Traffic-Muster überprüfen, um festzustellen, ob der leere Benutzeragent nützlich ist oder nicht.  Wenn Sie diesen Traffic blockieren möchten, wird folgende [ (Syntax](/help/security/traffic-filter-rules-including-waf.md#rules-syntax) empfohlen:

```
trafficFilters:
  rules:
    - name: block-missing-user-agent
      when:
        anyOf:
          - { reqHeader: user-agent, exists: false }
          - { reqHeader: user-agent, equals: '' }
      action: block
```

* Einige Bots haben eine Seite sehr schwer an einem Tag und verschwinden am nächsten Tag.  Dies kann jeden Versuch vereiteln, eine bestimmte IP-Adresse oder einen Benutzeragenten zu blockieren.  Ein generischer Ansatz besteht in der Einführung einer [Regel für Limits](/help/security/traffic-filter-rules-including-waf.md#rate-limit-rules).  Sehen Sie sich die [Beispiele](/help/security/traffic-filter-rules-including-waf.md#ratelimiting-examples) an und erstellen Sie eine Regel, die Ihrer Toleranz für eine schnelle Anfragerate entspricht.  Überprüfen Sie die [Bedingungsstruktur](/help/security/traffic-filter-rules-including-waf.md#condition-structure)-Syntax für alle Ausnahmen, die Sie möglicherweise zulassen möchten, um eine allgemeine Ratenbeschränkung zuzulassen.
