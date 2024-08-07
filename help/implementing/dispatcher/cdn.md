---
title: CDN in AEM as a Cloud Service
description: Erfahren Sie, wie Sie das AEM-verwaltete CDN verwenden und wie Sie Ihr eigenes CDN auf das AEM-verwaltete CDN verweisen lassen.
feature: Dispatcher
exl-id: a3f66d99-1b9a-4f74-90e5-2cad50dc345a
role: Admin
source-git-commit: 655b92f0fd3c6fb69bdd9343719537d6328fa7be
workflow-type: tm+mt
source-wordcount: '1552'
ht-degree: 69%

---


# CDN in AEM as a Cloud Service {#cdn}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_cdn"
>title="CDN in AEM as a Cloud Service"
>abstract="AEM as Cloud Service wird mit einem integrierten CDN ausgeliefert. Der Hauptzweck besteht darin, die Latenz zu verringern, indem zwischengespeicherte Inhalte von den CDN-Knoten in der Nähe des Browsers bereitgestellt werden. Es ist vollständig verwaltet und für eine optimale Leistung von AEM-Programmen konfiguriert."

AEM as Cloud Service wird mit einem integrierten CDN ausgeliefert. Der Hauptzweck besteht darin, die Latenz zu verringern, indem zwischengespeicherte Inhalte von den CDN-Knoten in der Nähe des Browsers bereitgestellt werden. Es ist vollständig verwaltet und für eine optimale Leistung von AEM-Programmen konfiguriert.

Das von AEM verwaltete CDN erfüllt die meisten Leistungs- und Sicherheitsanforderungen des Kunden oder der Kundin. Für die Veröffentlichungsebene können Kundinnen und Kunden optional von ihrem eigenen CDN aus darauf verweisen, welches sie verwalten müssen. Dieses Szenario wird von Fall zu Fall bei Erfüllung bestimmter Voraussetzungen gestattet, insbesondere dass die Kundin bzw. der Kunde eine Altintegration mit einem CDN-Anbieter hat, die schwer aufzugeben ist.

<!-- ERROR: NEITHER URL IS FOUND (HTTP ERROR 404) Also, see the following videos [Cloud 5 AEM CDN Part 1](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-5/cloud5-aem-cdn-part1.html) and [Cloud 5 AEM CDN Part 2](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-5/cloud5-aem-cdn-part2.html) for additional information about CDN in AEM as a Cloud Service. -->

## AEM-verwaltetes CDN  {#aem-managed-cdn}

Befolgen Sie die nachstehenden Abschnitte, um mithilfe der Self-Service-Benutzeroberfläche von Cloud Manager die Bereitstellung von Inhalten mit dem vorkonfigurierten CDN von AEM vorzubereiten:

1. [Verwalten von SSL-Zertifikaten](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md)
1. [Verwalten von benutzerdefinierten Domain-Namen](/help/implementing/cloud-manager/custom-domain-names/introduction.md)

**Beschränken des Traffic**

Standardmäßig kann bei einem von AEM verwalteten CDN-Setup der gesamte öffentliche Traffic zum Veröffentlichungs-Service geleitet werden, sowohl für Produktions- als auch für Nicht-Produktions-Umgebungen (Entwicklung und Staging). Über die Benutzeroberfläche von Cloud Manager können Sie den Traffic für eine bestimmte Umgebung auf den Veröffentlichungs-Service beschränken (z. B. die Beschränkung der Staging-Umgebung auf einen Bereich von IP-Adressen).

Weitere Informationen finden Sie unter [Verwalten von IP-Zulassungslisten](/help/implementing/cloud-manager/ip-allow-lists/introduction.md).

>[!CAUTION]
>
>Nur Anfragen von den zulässigen IPs werden vom in AEM verwalteten CDN bearbeitet. Wenn Sie Ihr eigenes CDN auf das von AEM verwaltete CDN verweisen, stellen Sie sicher, dass die IPs Ihres CDN in der Zulassungsliste enthalten sind.

### Konfigurieren von Traffic im CDN {#cdn-configuring-cloud}

Sie können Traffic im CDN auf verschiedene Arten konfigurieren, wie zum Beispiel:

* Blockieren von böswilligem Traffic mit [Traffic-Filterregeln](/help/security/traffic-filter-rules-including-waf.md) (einschließlich optional lizenzierbarer erweiterter WAF-Regeln)
* Ändern der Art der [Anforderung und Antwort](/help/implementing/dispatcher/cdn-configuring-traffic.md#request-transformations)
* Anwendung von 301/302 [clientseitigen Umleitungen](/help/implementing/dispatcher/cdn-configuring-traffic.md#client-side-redirectors)
* Deklarieren von [Ursprungsselektoren](/help/implementing/dispatcher/cdn-configuring-traffic.md#client-side-redirectors) zum Reverse-Proxy einer Anforderung an Nicht-AEM-Backends

Erfahren Sie, wie Sie diese Funktionen konfigurieren, indem Sie YAML-Dateien in Git verwenden und sie mithilfe der Cloud Manager [Config Pipeline](/help/implementing/dispatcher/cdn-configuring-traffic.md) bereitstellen.

### Konfigurieren von CDN-Fehlerseiten {#cdn-error-pages}

Eine CDN-Fehlerseite kann so konfiguriert werden, dass sie die ungebrandete Standardseite außer Kraft setzt, die dem Browser in dem seltenen Fall ausgegeben wird, dass AEM nicht erreicht werden kann. Weitere Informationen finden Sie unter [Konfigurieren von CDN-Fehlerseiten](/help/implementing/dispatcher/cdn-error-pages.md).

### Löschen zwischengespeicherter Inhalte im CDN {#purge-cdn}

Das Festlegen von TTL mithilfe des HTTP Cache-Control-Headers ist ein effektiver Ansatz, um die Leistung bei der Inhaltsbereitstellung und die Aktualität der Inhalte aufeinander abzustimmen. In Fällen, in denen es wichtig ist, aktualisierte Inhalte sofort bereitzustellen, kann es jedoch von Vorteil sein, den CDN-Cache direkt zu bereinigen.

Lesen Sie mehr über das Konfigurieren eines Bereinigungs-API-Tokens](/help/implementing/dispatcher/cdn-credentials-authentication.md/#purge-API-token) und das Löschen des zwischengespeicherten CDN-Inhalts [.[](/help/implementing/dispatcher/cdn-cache-purge.md)

### Grundlegende Authentifizierung beim CDN {#basic-auth}

Für einfache Authentifizierungsfälle, einschließlich geschäftlicher Interessengruppen, die Inhalte überprüfen, schützen Sie Inhalte, indem Sie ein einfaches Authentifizierungsdialogfeld anzeigen, das einen Benutzernamen und ein Kennwort erfordert. [Weitere Infos](/help/implementing/dispatcher/cdn-credentials-authentication.md) und Teilnahme am frühen Adopter-Programm.

## Kunden-CDN verweist auf AEM-verwaltetes CDN {#point-to-point-CDN}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_byocdn"
>title="Kunden-CDN verweist auf AEM-verwaltetes CDN"
>abstract="AEM as a Cloud Service bietet Kunden eine Option, ihr bestehendes CDN zu verwenden. Für die Veröffentlichungsebene können Kundinnen und Kunden optional von ihrem eigenen CDN aus darauf verweisen, welches sie verwalten müssen. Dieses Szenario wird von Fall zu Fall bei Erfüllung bestimmter Voraussetzungen gestattet, insbesondere dass die Kundin bzw. der Kunde eine Altintegration mit einem CDN-Anbieter hat, die schwer aufzugeben ist."

Wenn ein Kunde oder eine Kundin sein/ihr bestehendes CDN verwenden muss, kann es verwaltet werden und auf das von AEM verwaltete CDN verweisen, sofern folgende Voraussetzungen erfüllt sind:

* Der Kunde muss über ein vorhandenes CDN verfügen, dessen Ersetzung aufwendig wäre.
* Der Kunde muss es verwalten.
* Der Kunde muss in der Lage sein, das CDN für die Verwendung mit AEM as a Cloud Service zu konfigurieren. Weitere Informationen finden Sie in den Konfigurationsanweisungen unten.
* Der Kunde oder die Kundin muss über technische CDN-Experten oder -Expertinnen verfügen, die auf Abruf bereitstehen, falls Probleme auftreten.
* Der Kunde muss einen Belastungstest durchführen und erfolgreich bestehen, bevor er zur Produktion übergeht.

Konfigurationsanweisungen:

1. Verweisen Sie in Ihrem CDN auf den Eingang des Adobe-CDN als Ursprungs-Domain. Beispiel: `publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com`.
1. Setzen Sie die SNI auf den Eingang des Adobe CDN.
1. Legen Sie die Host-Kopfzeile auf die Ursprungs-Domain fest. Beispiel: `Host:publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com`.
1. Legen Sie die Kopfzeile `X-Forwarded-Host` mit dem Domain-Namen fest, damit AEM die Host-Kopfzeile ermitteln kann. Beispiel: `X-Forwarded-Host:example.com`.
1. Satz `X-AEM-Edge-Key`. Der Wert sollte mithilfe einer Cloud Manager-Konfigurationspipeline konfiguriert werden, wie in [diesem Artikel](/help/implementing/dispatcher/cdn-credentials-authentication.md#CDN-HTTP-value) beschrieben.

   * Erforderlich, damit das Adobe-CDN die Quelle der Anfragen validieren und die `X-Forwarded-*`-Header an die AEM-Applikation weitergeben kann. Beispielsweise wird `X-Forwarded-For` verwendet, um die Client-IP zu bestimmen. Somit liegt es in der Verantwortung des vertrauenswürdigen Aufrufers (d. h. des von Kunden oder Kundinnen verwalteten CDN), die Korrektheit der `X-Forwarded-*`-Header sicherzustellen (siehe Hinweis unten).
   * Optional kann der Zugriff auf den Eingang zum Adobe CDN blockiert werden, wenn kein `X-AEM-Edge-Key` vorhanden ist. Bitte informieren Sie Adobe, wenn Sie direkten Zugriff auf den Eingang zum Adobe-CDN benötigen (der blockiert werden soll).

Konfigurationsbeispiele von führenden CDN-Anbietern finden Sie im Abschnitt [Beispielkonfigurationen von CDN-Anbietern](#sample-configurations).

Bevor Sie Live-Traffic akzeptieren, sollten Sie beim Adobe-Support überprüfen, ob das Traffic-Routing End-to-End ordnungsgemäß funktioniert.

Nach dem Festlegen von `X-AEM-Edge-Key` können Sie testen, ob die Anfrage wie folgt richtig weitergeleitet wird.

Unter Linux®:

```
curl https://publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com -H "X-Forwarded-Host: example.com" -H "X-AEM-Edge-Key: <PROVIDED_EDGE_KEY>"
```

Unter Windows: 

```
curl https://publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com --header "X-Forwarded-Host: example.com" --header "X-AEM-Edge-Key: <PROVIDED_EDGE_KEY>"
```

>[!NOTE]
>
>Wenn Sie Ihr eigenes CDN verwenden, müssen Sie keine Domänen und Zertifikate in Cloud Manager installieren. Das Routing im Adobe-CDN erfolgt unter Verwendung der Standarddomäne `publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com`, die im Header der Anfrage `Host` gesendet werden sollte. Das Überschreiben des Anfragen-Headers `Host` mit einem benutzerdefinierten Domänennamen kann dazu führen, dass die Anfrage vom Adobe CDN falsch weitergeleitet wird.


>[!NOTE]
>
>Kunden, die ein eigenes CDN verwalten, müssen die Integrität der Kopfzeilen sicherstellen, die an das CDN von AEM gesendet werden. Beispielsweise empfehlen wir, dass Kunden alle `X-Forwarded-*`-Kopfzeilen löschen und für sie bekannte und kontrollierte Werte festlegen. Beispiel: `X-Forwarded-For` muss die IP-Adresse des Kunden enthalten, während `X-Forwarded-Host` den Host der Website enthalten muss.

>[!NOTE]
>
>Sandbox-Programmumgebungen unterstützen kein vom Kunden bereitgestelltes CDN.

Der zusätzliche Sprung zwischen dem Kunden-CDN und dem AEM-CDN ist nur im Fall eines Cache-Fehlers erforderlich. Durch die Verwendung der in diesem Artikel beschriebenen Cache-Optimierungsstrategien sollte das Hinzufügen eines Kunden-CDN nur eine vernachlässigbare Latenzzeit verursachen.

Diese kundenspezifische CDN-Konfiguration wird für die Veröffentlichungsebene unterstützt, aber nicht vor der Autorenebene.

### Beispielkonfigurationen von CDN-Anbietern {#sample-configurations}

Im Folgenden werden einige Konfigurationsbeispiele von mehreren führenden CDN-Anbietern vorgestellt.

**Akamai**

![Akamai1](assets/akamai1.png "Akamai")
![Akamai2](assets/akamai2.png "Akamai")

**Amazon CloudFront**

![CloudFront1](assets/cloudfront1.png "Amazon CloudFront")
![CloudFront2](assets/cloudfront2.png "Amazon CloudFront")

**Cloudflare**

![Cloudflare1](assets/cloudflare1.png "Cloudflare")
![Cloudflare2](assets/cloudflare2.png "Cloudflare")

### Häufige Fehler {#common-errors}

Die bereitgestellten Beispielkonfigurationen zeigen die erforderlichen Basiseinstellungen an, aber eine Kundenkonfiguration kann andere Einflussregeln haben, die die Header entfernen, ändern oder neu anordnen, die erforderlich sind, damit AEM as a Cloud Service den Traffic bereitstellt. Im Folgenden finden Sie häufige Fehler, die beim Konfigurieren eines kundenverwalteten CDN auftreten, um auf AEM as a Cloud Service zu verweisen.

**Weiterleitung zum Publish-Dienstendpunkt**

Wenn eine Anfrage eine unzulässige Antwort vom Typ 403 erhält, bedeutet dies, dass in der Anfrage einige erforderliche Kopfzeilen fehlen. Eine häufige Ursache dafür ist, dass das CDN sowohl den Apex- als auch den `www`-Domänentraffic verwaltet, jedoch nicht die richtige Kopfzeile für die Domäne `www` hinzufügt. Dieses Problem kann gelöst werden, indem Sie Ihre AEM as a Cloud Service-CDN-Protokolle überprüfen und die erforderlichen Anforderungsheader überprüfen.

**Zu viele Umleitungsschleife**

Wenn eine Seite eine Schleife &quot;Zu viele Umleitungen&quot;erhält, wird ein Anforderungsheader im CDN hinzugefügt, der mit einer Umleitung übereinstimmt, die sie zu sich selbst zwingt. Beispiel:

* Es wird eine CDN-Regel erstellt, die entweder mit der Apex-Domäne oder der www-Domäne übereinstimmt, und die X-Forwarded-Host-Kopfzeile der Apex-Domäne wird nur hinzugefügt.
* Eine Anfrage für eine Apex-Domäne entspricht dieser CDN-Regel, die die Apex-Domäne als Header X-Forwarded-Host hinzufügt.
* Eine Anfrage wird an die Quelle gesendet, wo eine Weiterleitung explizit mit der Host-Kopfzeile für die Apex-Domäne übereinstimmt (z. B. ^example.com).
* Es wird eine Neuschreibungsregel ausgelöst, die die Anfrage für die Apex-Domäne mit der Subdomäne www in https umschreibt.
* Diese Umleitung wird dann an den Edge des Kunden gesendet, wo die CDN-Regel erneut ausgelöst wird und der Header &quot;X-Forwarded-Host&quot;für die Apex-Domäne und nicht die Subdomäne &quot;www&quot;hinzugefügt wird. Anschließend wird der Prozess neu gestartet, bis die Anfrage fehlschlägt.

Um dieses Problem zu beheben, bewerten Sie Ihre SSL-Umleitungsstrategie, CDN-Regeln, Umleitungs- und Umschreibungsregelkombinationen.

## Geolocation-Kopfzeilen {#geo-headers}

Das AEM-verwaltete CDN fügt jeder Anfrage Header hinzu. Diese enthalten:

* Länder-Code: `x-aem-client-country`
* Kontinental-Code: `x-aem-client-continent`

>[!NOTE]
>
>Wenn es ein vom Kunden verwaltetes CDN gibt, spiegeln diese Header den Standort des CDN-Proxy-Servers des Kunden und nicht den des eigentlichen Clients wider. Daher sollten bei einem vom Kunden verwalteten CDN die Geolocation-Header vom CDN des Kunden verwaltet werden.

Die Werte für die Länder-Codes sind die [hier](https://de.wikipedia.org/wiki/ISO_3166-1) beschriebenen Alpha-2-Codes.

Die Werte für die Kontinental-Codes lauten:

* AF Afrika
* AN Antarktika
* AS Asien
* EU Europa
* NA Nordamerika
* OC Ozeanien
* SA Südamerika

Diese Informationen können für Anwendungsfälle nützlich sein, wie z. B. die Weiterleitung zu einer anderen URL basierend auf dem Ursprung (Land) der Anfrage. Verwenden Sie den Abweichungs-Header für die Zwischenspeicherung von Antworten, die von geografischen Daten abhängen. Umleitungen zu einer bestimmten Landingpage müssen beispielsweise immer `Vary: x-aem-client-country` enthalten. Bei Bedarf können Sie `Cache-Control: private` verwenden, um das Caching zu verhindern. Weitere Informationen finden Sie unter [Caching](/help/implementing/dispatcher/caching.md#html-text).
