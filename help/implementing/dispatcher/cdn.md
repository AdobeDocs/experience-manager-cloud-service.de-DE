---
title: CDN in AEM as a Cloud Service
description: Erfahren Sie, wie Sie das AEM-verwaltete CDN verwenden und wie Sie Ihr eigenes CDN auf das AEM-verwaltete CDN verweisen lassen.
feature: Dispatcher
exl-id: a3f66d99-1b9a-4f74-90e5-2cad50dc345a
role: Admin
source-git-commit: 62af306bbf645c4d70d0f07f95aa90e4d53e20f8
workflow-type: ht
source-wordcount: '1744'
ht-degree: 100%

---


# CDN in AEM as a Cloud Service {#cdn}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_cdn"
>title="CDN in AEM as a Cloud Service"
>abstract="AEM as Cloud Service wird mit einem integrierten CDN ausgeliefert. Der Hauptzweck besteht darin, die Latenz zu verringern, indem zwischengespeicherte Inhalte von den CDN-Knoten in der Nähe des Browsers bereitgestellt werden. Es ist vollständig verwaltet und für eine optimale Leistung von AEM-Programmen konfiguriert."

AEM as a Cloud Service verfügt über ein integriertes CDN, das die Latenz verringert, indem zwischenspeicherbare Inhalte von Edge-Knoten in der Nähe des Browsers der Benutzerin bzw. des Benutzers bereitgestellt werden. Dieses vollständig verwaltete CDN ist für die Leistung der AEM-Anwendung optimiert.

Das von AEM verwaltete CDN erfüllt die meisten Leistungs- und Sicherheitsanforderungen des Kunden bzw. der Kundin. Für die Veröffentlichungsebene können Kundinnen und Kunden Traffic durch ihr eigenes CDN leiten, welches sie verwalten müssen. Diese Option ist von Fall zu Fall verfügbar, insbesondere wenn Kundinnen und Kunden über bestehende ältere Integrationen mit einem CDN-Anbieter verfügen, die schwer zu ersetzen sind.

Kundinnen und Kunden, die auf Ebene der Edge Delivery Services veröffentlichen möchten, können von dem von Adobe verwalteten CDN profitieren. Siehe [Von Adobe verwaltetes CDN](#aem-managed-cdn). <!-- CQDOC-21758, 5b -->


<!-- ERROR: NEITHER URL IS FOUND (HTTP ERROR 404) Also, see the following videos [Cloud 5 AEM CDN Part 1](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-5/cloud5-aem-cdn-part1.html) and [Cloud 5 AEM CDN Part 2](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-5/cloud5-aem-cdn-part2.html) for additional information about CDN in AEM as a Cloud Service. -->

## Von Adobe verwaltetes CDN {#aem-managed-cdn}

<!-- CQDOC-21758, 5a -->

Zur Vorbereitung auf die Inhaltsbereitstellung mit dem integrierten CDN von AEM über die Self-Service-Benutzeroberfläche von Cloud Manager können Sie von den Funktionen des von Adobe verwalteten CDN profitieren. Mit dieser Funktion können Sie die Self-Service-CDN-Verwaltung nutzen, einschließlich der Konfiguration und Installation von SSL-Zertifikaten wie DV(Domain Validation)- oder EV/OV(Extended/Organization Validation)-Zertifikaten. Weitere Informationen zu diesen Methoden finden Sie unter:

* [Edge Delivery Services in Cloud Manager](/help/implementing/cloud-manager/edge-delivery/introduction-to-edge-delivery-services.md)
* [Einführung in benutzerdefinierte Domain-Namen](/help/implementing/cloud-manager/custom-domain-names/introduction.md)
* [Einführung in SSL-Zertifikate](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md)
* [Konfigurieren eines CDN](/help/implementing/cloud-manager/domain-mappings/add-domain-mapping.md)

**Beschränken des Traffics**

Standardmäßig kann bei einem von AEM verwalteten CDN-Setup der gesamte öffentliche Traffic zum Veröffentlichungs-Service geleitet werden, sowohl für Produktions- als auch für Nicht-Produktions-Umgebungen (Entwicklung und Staging). Über die Benutzeroberfläche von Cloud Manager können Sie den Traffic für eine bestimmte Umgebung auf den Veröffentlichungs-Service beschränken (z. B. die Beschränkung der Staging-Umgebung auf einen Bereich von IP-Adressen).

Weitere Informationen finden Sie unter [Verwalten von IP-Zulassungslisten](/help/implementing/cloud-manager/ip-allow-lists/introduction.md).

>[!CAUTION]
>
>Das verwaltete CDN von AEM stellt Anforderungen nur von zulässigen IPs bereit. Wenn Sie Ihr eigenes CDN auf das von AEM verwaltete CDN verweisen, stellen Sie sicher, dass die IPs Ihres CDN in der IP-Zulassungsliste enthalten sind.

### Konfigurieren von Traffic im CDN {#cdn-configuring-cloud}

Sie können Traffic im CDN auf verschiedene Arten konfigurieren, wie zum Beispiel:

* Blockieren von schädlichem Traffic mit [Traffic-Filterregeln](/help/security/traffic-filter-rules-including-waf.md) (einschließlich optional lizenzierbaren, erweiterten WAF-Regeln)
* Ändern der Art der [Anfrage und Antwort](/help/implementing/dispatcher/cdn-configuring-traffic.md#request-transformations)
* Anwenden der [Client-seitigen 301/302-Umleitungen](/help/implementing/dispatcher/cdn-configuring-traffic.md#client-side-redirectors)
* Deklarieren von [Ursprungs-Auswahlen](/help/implementing/dispatcher/cdn-configuring-traffic.md#client-side-redirectors) zum Reverse-Proxy einer Anfrage an Nicht-AEM-Backends

Verwenden Sie YAML-Dateien in Git, um diese Funktionen zu konfigurieren. Verwenden Sie außerdem die [Konfigurations-Pipeline](/help/implementing/dispatcher/cdn-configuring-traffic.md) von Cloud Manager, um sie bereitzustellen.

### Konfigurieren von CDN-Fehlerseiten {#cdn-error-pages}

Sie können eine CDN-Fehlerseite konfigurieren, um die (markenfreie) Standardseite zu ersetzen. Diese benutzerdefinierte Seite wird in dem seltenen Fall angezeigt, dass AEM nicht verfügbar ist. Weitere Informationen finden Sie unter [Konfigurieren von CDN-Fehlerseiten](/help/implementing/dispatcher/cdn-error-pages.md).

### Bereinigen zwischengespeicherter Inhalte im CDN {#purge-cdn}

Das Festlegen einer TTL mithilfe des HTTP Cache-Control-Headers ist ein effektiver Ansatz, um die Leistung bei der Inhaltsbereitstellung und die Aktualität der Inhalte aufeinander abzustimmen. Wenn aktualisierte Inhalte jedoch sofort bereitgestellt werden müssen, kann es von Vorteil sein, den CDN-Cache direkt zu bereinigen.

Lesen Sie mehr über das [Konfigurieren eines Bereinigungs-API-Tokens](/help/implementing/dispatcher/cdn-credentials-authentication.md/#purge-API-token) und das [Bereinigen von zwischengespeicherten CDN-Inhalten](/help/implementing/dispatcher/cdn-cache-purge.md).

### Grundlegende Authentifizierung im CDN {#basic-auth}

Schützen Sie Inhalte für einfache Authentifizierungsfälle, einschließlich Geschäfts-Stakeholdern, die Inhalte überprüfen, indem Sie ein einfaches Authentifizierungsdialogfeld anzeigen lassen, das einen Benutzernamen und ein Kennwort erfordert. [Weitere Informationen](/help/implementing/dispatcher/cdn-credentials-authentication.md).

## Kundenseitig verwaltetes CDN verweist auf ein von AEM verwaltetes CDN {#point-to-point-CDN}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_byocdn"
>title="Kunden-CDN (oder Proxy) verweist auf ein von AEM verwaltetes CDN"
>abstract="AEM as a Cloud Service bietet Kundinnen und Kunden eine Option, ihr bestehendes CDN zu verwenden. Für die Veröffentlichungsebene können Kundinnen und Kunden optional von ihrem eigenen CDN aus darauf verweisen, welches sie verwalten müssen. Dieses Szenario wird von Fall zu Fall bei Erfüllung bestimmter Voraussetzungen gestattet, insbesondere dass die Kundin bzw. der Kunde eine Altintegration mit einem CDN-Anbieter hat, die schwer aufzugeben ist."

Wenn Kundinnen oder Kunden ihr bestehendes CDN (oder jede Art von Reverse-Proxy, zum Beispiel einen Load Balancer oder eine WAF) verwenden müssen, können sie es verwalten und auf das von AEM verwaltete CDN verweisen lassen, sofern folgende Voraussetzungen erfüllt sind:

* Die Kundin bzw. der Kunde muss über ein vorhandenes CDN verfügen, dessen Ersetzung aufwendig wäre.
* Die Kundin bzw. der Kunde muss es verwalten.
* Die Kundin bzw. der Kunde muss in der Lage sein, das CDN für die Verwendung mit AEM as a Cloud Service zu konfigurieren. Weitere Informationen finden Sie in den Konfigurationsanweisungen unten.
* Die Kundin bzw. der Kunde muss über technische CDN-Fachleute verfügen, die auf Abruf bereitstehen, falls Probleme auftreten.
* Die Kundin bzw. der Kunde muss vor dem Übergang zur Produktion einen Belastungstest durchführen und erfolgreich bestehen.

Konfigurationsanweisungen:

1. Verweisen Sie in Ihrem CDN auf den Eingang des Adobe-CDN als Ursprungs-Domain. Beispiel: `publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com`.
1. Setzen Sie die SNI auf den Eingang des Adobe CDN.
1. Legen Sie die Host-Kopfzeile auf die Ursprungs-Domain fest. Beispiel: `Host:publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com`.
1. Legen Sie die Kopfzeile `X-Forwarded-Host` mit dem Domain-Namen fest, damit AEM die Host-Kopfzeile ermitteln kann. Beispiel: `X-Forwarded-Host:example.com`.
1. Satz `X-AEM-Edge-Key`. Der Wert sollte mithilfe einer Cloud Manager-Konfigurations-Pipeline konfiguriert werden, wie in [diesem Artikel](/help/implementing/dispatcher/cdn-credentials-authentication.md#CDN-HTTP-value) beschrieben.

   * Erforderlich, damit das Adobe-CDN die Quelle der Anfragen validieren und die `X-Forwarded-*`-Header an die AEM-Applikation weitergeben kann. Beispielsweise wird `X-Forwarded-For` verwendet, um die Client-IP zu bestimmen. Somit liegt es in der Verantwortung des vertrauenswürdigen Aufrufers (d. h. des kundenseitig verwalteten CDN), die Korrektheit der `X-Forwarded-*`-Header sicherzustellen (siehe Hinweis unten).
   * Optional kann der Zugriff auf den Eingang zum Adobe CDN blockiert werden, wenn kein `X-AEM-Edge-Key` vorhanden ist. Bitte informieren Sie Adobe, wenn Sie direkten Zugriff auf den Eingang zum Adobe-CDN benötigen (der blockiert werden soll).

Konfigurationsbeispiele von führenden CDN-Anbietern finden Sie im Abschnitt [Beispielkonfigurationen von CDN-Anbietern](#sample-configurations).

Bevor Sie Live-Traffic akzeptieren, sollten Sie beim Adobe-Support überprüfen, ob das Traffic-Routing End-to-End ordnungsgemäß funktioniert.

Nach dem Festlegen des `X-AEM-Edge-Key` können Sie wie folgt testen, ob die Anfrage korrekt weitergeleitet wird.

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
>Wenn Sie Ihr eigenes CDN verwenden, müssen Sie keine Domänen und Zertifikate in Cloud Manager installieren. Das Routing im Adobe-CDN erfolgt unter Verwendung der Standard-Domain `publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com`, die im `Host`-Header der Anfrage gesendet werden sollte. Das Überschreiben des `Host`-Headers der Anfrage mit einem benutzerdefinierten Domain-Namen kann dazu führen, dass die Anfrage vom Adobe-CDN falsch weitergeleitet wird oder 421-Fehler auftreten.

>[!NOTE]
>
>Kunden, die ein eigenes CDN verwalten, müssen die Integrität der Kopfzeilen sicherstellen, die an das CDN von AEM gesendet werden. Beispielsweise empfehlen wir, dass Kunden alle `X-Forwarded-*`-Kopfzeilen löschen und für sie bekannte und kontrollierte Werte festlegen. Beispiel: `X-Forwarded-For` muss die IP-Adresse des Kunden enthalten, während `X-Forwarded-Host` den Host der Website enthalten muss.

>[!NOTE]
>
>Sandbox-Programmumgebungen unterstützen kein kundenseitig bereitgestelltes CDN.

Der zusätzliche Sprung zwischen dem Kunden-CDN und dem AEM-CDN ist nur im Fall eines Cache-Fehlers erforderlich. Durch die Verwendung der in diesem Artikel beschriebenen Cache-Optimierungsstrategien sollte das Hinzufügen eines Kunden-CDN nur eine vernachlässigbare Latenzzeit verursachen.

Diese kundenspezifische CDN-Konfiguration wird für die Veröffentlichungsebene unterstützt, aber nicht vor der Autorenebene.

### Debuggen von Konfigurationen

Um eine BYOCDN-Konfiguration zu debuggen, verwenden Sie die Kopfzeile `x-aem-debug` mit dem Wert `edge=true`. Zum Beispiel:

Unter Linux®:

```
curl https://publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com -v -H "X-Forwarded-Host: example.com" -H "X-AEM-Edge-Key: <PROVIDED_EDGE_KEY>" -H "x-aem-debug: edge=true"
```

Unter Windows: 

```
curl https://publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com -v --header "X-Forwarded-Host: example.com" --header "X-AEM-Edge-Key: <PROVIDED_EDGE_KEY>" --header "x-aem-debug: edge=true"
```

Dieser Prozess spiegelt bestimmte Eigenschaften wider, die in der Anfrage im Antwort-Header `x-aem-debug` verwendet werden. Zum Beispiel:

```
x-aem-debug: byocdn=true,edge=true,edge-auth=edge-auth,edge-key=edgeKey1,X-AEM-Edge-Key=set,host=publish-p87058-e257304-cmstg.adobeaemcloud.com,x-forwarded-host=wknd.site,adobe_unlocked_byocdn=true
```

Dieser Prozess ermöglicht die Überprüfung von Details wie den Host-Werten, der Edge-Authentifizierungskonfiguration und dem Wert des Headers x-forwarded-host. Außerdem identifiziert er, ob ein Edge-Schlüssel festgelegt ist und welcher Schlüssel verwendet wird, falls eine Übereinstimmung vorliegt.

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

Die bereitgestellten Beispielkonfigurationen zeigen die grundlegenden erforderlichen Einstellungen an. Eine Kundenkonfiguration kann jedoch andere Einflussregeln haben, welche die Header entfernen, ändern oder neu anordnen, die erforderlich sind, damit AEM as a Cloud Service den Traffic bereitstellt. Im Folgenden finden Sie häufige Fehler, die auftreten, wenn ein kundenseitig verwaltetes CDN so konfiguriert wird, dass es auf AEM as a Cloud Service verweist.

**Weiterleitung zum Endpunkt des Veröffentlichungs-Services**

Wenn eine Anfrage eine unzulässige Antwort vom Typ 403 erhält, bedeutet dies, dass in der Anfrage einige erforderliche Header fehlen. Eine häufige Ursache dafür ist, dass das CDN sowohl den Apex- als auch den `www`-Domain-Traffic verwaltet, jedoch nicht den richtigen Header für die `www`-Domain hinzufügt. Dieses Problem kann gelöst werden, indem Sie Ihre CDN-Protokolle in AEM as a Cloud Service überprüfen und die erforderlichen Anforderungs-Header verifizieren.

**Fehler 421 Fehlgeleitete Weiterleitung**

Ein 421-Fehler mit der Meldung `Requested host does not match any Subject Alternative Names (SANs) on TLS certificate` gibt an, dass der HTTP-`Host` mit keinen der im Zertifikat aufgeführten Hosts übereinstimmt. Dieses Problem deutet in der Regel darauf hin, dass entweder der `Host` oder die SNI-Einstellung falsch ist. Stellen Sie sicher, dass sowohl `Host` als auch die SNI-Einstellungen auf den Host publish-p&lt;PROGRAM_ID>-e.adobeaemcloud.com verweisen.

**Schleife „Zu viele Umleitungen“**

Wenn eine Seite eine Schleife „Zu viele Umleitungen“ erhält, wird im CDN ein Anfrage-Header hinzugefügt, der einer Umleitung entspricht, die die Seite zu sich selbst zurückführt. Zum Beispiel:

* Es wird eine CDN-Regel erstellt, die entweder mit der Apex-Domain oder der www-Domain übereinstimmt und nur den X-Forwarded-Host-Header der Apex-Domain hinzufügt.
* Eine Anfrage für eine Apex-Domain entspricht dieser CDN-Regel, die die Apex-Domain als X-Forwarded-Host-Header hinzufügt.
* Eine Anfrage wird an die Quelle gesendet, an der eine Weiterleitung explizit mit dem Host-Header für die Apex-Domain übereinstimmt (z. B. ^example.com).
* Es wird eine Neuschreibungsregel ausgelöst, die die Anfrage für die Apex-Domain mit der www-Subdomain in https umschreibt.
* Diese Umleitung wird dann an den Edge der Kundin bzw. des Kunden gesendet, wenn die CDN-Regel erneut ausgelöst wird und der X-Forwarded-Host-Header für die Apex-Domain und nicht die www-Subdomain hinzugefügt wird. Anschließend fängt der Prozess von vorne an, bis die Anfrage fehlschlägt.

Um dieses Problem zu beheben, werten Sie Ihre SSL-Umleitungsstrategie, CDN-Regeln, Umleitungs- und Umschreibungsregelkombinationen aus.

## Geolocation-Header {#geo-headers}

Das AEM-verwaltete CDN fügt jeder Anfrage Kopfzeilen hinzu. Diese enthalten:

* Länder-Code: `x-aem-client-country`
* Kontinental-Code: `x-aem-client-continent`

>[!NOTE]
>
>Wenn es ein kundenseitig verwaltetes CDN gibt, spiegeln diese Header den Standort des CDN-Proxy-Servers der Kundin oder des Kunden und nicht den des eigentlichen Clients wider. Kundinnen und Kunden sollten Geolocation-Header über ihr eigenes CDN verwalten, wenn sie ein kundenseitig verwaltetes CDN verwenden.

Die Werte für die Länder-Codes sind die unter [ISO 3166-1](https://de.wikipedia.org/wiki/ISO_3166-1) beschriebenen Alpha-2-Codes.

Die Werte für die Kontinental-Codes lauten:

* AF Afrika
* AN Antarktika
* AS Asien
* EU Europa
* NA Nordamerika
* OC Ozeanien
* SA Südamerika

Diese Informationen sind nützlich, um basierend auf dem Herkunftsland der Anfrage zu einer anderen URL umzuleiten. Verwenden Sie den Abweichungs-Header für die Zwischenspeicherung von Antworten, die von geografischen Daten abhängen. Umleitungen zu einer bestimmten Landingpage müssen beispielsweise immer `Vary: x-aem-client-country` enthalten. Bei Bedarf können Sie `Cache-Control: private` verwenden, um das Caching zu verhindern. Weitere Informationen finden Sie unter [Caching](/help/implementing/dispatcher/caching.md#html-text).
