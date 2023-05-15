---
title: CDN in AEM as a Cloud Service
description: CDN in AEM as a Cloud Service
feature: Dispatcher
exl-id: a3f66d99-1b9a-4f74-90e5-2cad50dc345a
source-git-commit: 98eff568686c72c626d2bf77d82e8c3f224eda42
workflow-type: tm+mt
source-wordcount: '1023'
ht-degree: 52%

---

# CDN in AEM as a Cloud Service {#cdn}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_cdn"
>title="CDN in AEM as a Cloud Service"
>abstract="AEM as Cloud Service wird mit einem integrierten CDN ausgeliefert. Der Hauptzweck besteht darin, die Latenz zu verringern, indem zwischengespeicherte Inhalte von den CDN-Knoten in der Nähe des Browsers bereitgestellt werden. Es ist vollständig verwaltet und für eine optimale Leistung von AEM-Programmen konfiguriert."

AEM as Cloud Service wird mit einem integrierten CDN ausgeliefert. Der Hauptzweck besteht darin, die Latenz zu verringern, indem zwischengespeicherte Inhalte von den CDN-Knoten in der Nähe des Browsers bereitgestellt werden. Es ist vollständig verwaltet und für eine optimale Leistung von AEM-Programmen konfiguriert.

Das AEM verwaltete CDN erfüllt die meisten Leistungs- und Sicherheitsanforderungen des Kunden. Für die Veröffentlichungsstufe können Kunden optional von ihrem eigenen CDN darauf verweisen, das sie verwalten müssen. Dieses Szenario ist von Fall zu Fall zulässig, je nachdem, ob bestimmte Voraussetzungen erfüllt sind. Dazu gehört unter anderem, dass der Kunde über eine veraltete Integration mit seinem CDN-Anbieter verfügt, die schwer aufzugeben ist.

<!-- ERROR: NEITHER URL IS FOUND (HTTP ERROR 404) Also, see the following videos [Cloud 5 AEM CDN Part 1](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-5/cloud5-aem-cdn-part1.html) and [Cloud 5 AEM CDN Part 2](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-5/cloud5-aem-cdn-part2.html) for additional information about CDN in AEM as a Cloud Service. -->

## AEM-verwaltetes CDN  {#aem-managed-cdn}

Befolgen Sie die nachstehenden Abschnitte, um mithilfe der Self-Service-Benutzeroberfläche von Cloud Manager die Bereitstellung von Inhalten mit dem vorkonfigurierten CDN von AEM vorzubereiten:

1. [Verwalten von SSL-Zertifikaten](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md)
1. [Verwalten von benutzerdefinierten Domain-Namen](/help/implementing/cloud-manager/custom-domain-names/introduction.md)

**Beschränken des Traffic**

Standardmäßig kann bei einem AEM verwalteten CDN-Setup der gesamte öffentliche Traffic zum Veröffentlichungsdienst geleitet werden, sowohl für Produktions- als auch für Nicht-Produktions-Umgebungen (Entwicklung und Staging). Über die Benutzeroberfläche von Cloud Manager können Sie den Traffic für eine bestimmte Umgebung auf den Veröffentlichungsdienst beschränken (z. B. die Beschränkung der Staging-Umgebung auf einen Bereich von IP-Adressen).

Weitere Informationen finden Sie unter [Verwalten von IP-Zulassungslisten](/help/implementing/cloud-manager/ip-allow-lists/introduction.md).

>[!CAUTION]
>
>Nur Anforderungen von den zulässigen IPs werden von AEM verwalteten CDN bereitgestellt. Wenn Sie Ihr eigenes CDN auf das AEM verwaltete CDN verweisen, stellen Sie sicher, dass die IPs Ihres CDN in der Zulassungsliste enthalten sind.

## Kunden-CDN verweist auf AEM-verwaltetes CDN {#point-to-point-CDN}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_byocdn"
>title="Kunden-CDN verweist auf AEM-verwaltetes CDN"
>abstract="AEM as a Cloud Service bietet Kunden eine Option, ihr bestehendes CDN zu verwenden. Für die Veröffentlichungsstufe können Kunden optional von ihrem eigenen CDN darauf verweisen, das sie verwalten müssen. Dieses Szenario ist von Fall zu Fall zulässig, je nachdem, ob bestimmte Voraussetzungen erfüllt sind. Dazu gehört unter anderem, dass der Kunde über eine veraltete Integration mit seinem CDN-Anbieter verfügt, die schwer aufzugeben ist."

Wenn ein Kunde sein bestehendes CDN verwenden muss, kann er es verwalten und auf das AEM verwaltete CDN verweisen, sofern folgende Voraussetzungen erfüllt sind:

* Der Kunde muss über ein vorhandenes CDN verfügen, dessen Ersetzung aufwendig wäre.
* Der Kunde muss es verwalten.
* Der Kunde muss in der Lage sein, das CDN für die Verwendung mit AEM as a Cloud Service zu konfigurieren. Weitere Informationen finden Sie in den Konfigurationsanweisungen unten.
* Der Kunde muss über technische CDN-Experten verfügen, die im Fall von Problemen im Zusammenhang mit dem Fall auf Anfrage zur Verfügung stehen.
* Der Kunde muss einen Belastungstest durchführen und erfolgreich bestehen, bevor er zur Produktion übergeht.

Konfigurationsanweisungen:

1. Verweisen Sie in Ihrem CDN auf den Eingang des Adobe-CDN als Ursprungs-Domain. Beispiel: `publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com`.
1. Setzen Sie SNI auf den Eingang des Adobe CDN.
1. Legen Sie die Host-Kopfzeile auf die Ursprungs-Domain fest. Beispiel: `Host:publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com`.
1. Legen Sie die Kopfzeile `X-Forwarded-Host` mit dem Domain-Namen fest, damit AEM die Host-Kopfzeile ermitteln kann. Beispiel: `X-Forwarded-Host:example.com`.
1. Satz `X-AEM-Edge-Key`. Der Wert muss von Adobe stammen.

   * Erforderlich, damit das Adobe-CDN die Anforderungsquelle überprüfen und die `X-Forwarded-*` Kopfzeilen der AEM Anwendung. Beispielsweise wird `X-Forwarded-For` verwendet, um die Client-IP zu bestimmen. Daher ist der vertrauenswürdige Anrufer (d. h. das kundenverwaltete CDN) dafür verantwortlich, die Richtigkeit der `X-Forwarded-*` Kopfzeilen (siehe Hinweis unten).
   * Optional kann der Zugriff auf den Eingang zum Adobe CDN blockiert werden, wenn kein `X-AEM-Edge-Key` vorhanden ist. Informieren Sie die Adobe, wenn Sie direkten Zugriff auf den Eingang des Adobe CDN benötigen (um blockiert zu werden).

Konfigurationsbeispiele von führenden CDN-Anbietern finden Sie im Abschnitt [Beispielkonfigurationen von CDN-Anbietern](#sample-configurations).

Bevor Sie Live-Traffic akzeptieren, sollten Sie beim Adobe-Support überprüfen, ob das Traffic-Routing End-to-End ordnungsgemäß funktioniert.

Nach dem Abrufen des `X-AEM-Edge-Key` können Sie wie folgt testen, ob die Anfrage korrekt weitergeleitet wird.

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
>Bei Verwendung Ihres eigenen CDN müssen Sie keine Domänen und Zertifikate in Cloud Manager installieren. Das Routing im Adoben-CDN erfolgt mithilfe der Standarddomäne `publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com` die in der Anfrage gesendet werden sollen `Host` -Kopfzeile. Anforderung überschreiben `Host` -Kopfzeile mit einem benutzerdefinierten Domänennamen kann dazu führen, dass die Anfrage vom Adobe-CDN falsch gerendert wird.


>[!NOTE]
>
>Kunden, die ein eigenes CDN verwalten, müssen die Integrität der Kopfzeilen sicherstellen, die an das CDN von AEM gesendet werden. Beispielsweise empfehlen wir, dass Kunden alle `X-Forwarded-*`-Kopfzeilen löschen und für sie bekannte und kontrollierte Werte festlegen. Beispiel: `X-Forwarded-For` muss die IP-Adresse des Kunden enthalten, während `X-Forwarded-Host` den Host der Website enthalten muss.

>[!NOTE]
>
>Sandbox-Programmumgebungen unterstützen kein vom Kunden bereitgestelltes CDN.

Der zusätzliche Wechsel zwischen dem Kunden-CDN und dem AEM CDN ist nur erforderlich, wenn ein Cache fehlschlägt. Durch die Verwendung der in diesem Artikel beschriebenen Cache-Optimierungsstrategien sollte das Hinzufügen eines Kunden-CDN nur eine vernachlässigbare Latenzzeit verursachen.

Diese Kunden-CDN-Konfiguration wird für die Veröffentlichungsstufe unterstützt, jedoch nicht vor der Autorenstufe.

### Beispielkonfigurationen von CDN-Anbietern {#sample-configurations}

Nachfolgend finden Sie einige Konfigurationsbeispiele von mehreren führenden CDN-Anbietern.

**Akamai**

![Akamai1](assets/akamai1.png "Akamai")
![Akamai2](assets/akamai2.png "Akamai")

**Amazon CloudFront**

![CloudFront1](assets/cloudfront1.png "Amazon CloudFront")
![CloudFront2](assets/cloudfront2.png "Amazon CloudFront")

**Cloudflare**

![Cloudflare1](assets/cloudflare1.png "Cloudflare")
![Cloudflare2](assets/cloudflare2.png "Cloudflare")

## Geolocation-Kopfzeilen {#geo-headers}

Das AEM verwaltete CDN fügt jeder Anfrage Header mit folgenden Eigenschaften hinzu:

* Länder-Code: `x-aem-client-country`
* Kontinental-Code: `x-aem-client-continent`

>[!NOTE]
>
>Wenn ein kundenverwaltetes CDN vorhanden ist, spiegeln diese Header den Speicherort des CDN-Proxyservers des Kunden und nicht den tatsächlichen Client wider. Daher sollten für kundenverwaltetes CDN Geolocation-Header vom Kunden-CDN verwaltet werden.

Die Werte für die Länder-Codes sind die [hier](https://de.wikipedia.org/wiki/ISO_3166-1) beschriebenen Alpha-2-Codes.

Die Werte für die Kontinental-Codes lauten:

* AF Afrika
* AN Antarktika
* AS Asien
* EU Europa
* NA Nordamerika
* OC Ozeanien
* SA Südamerika

Diese Informationen können für Anwendungsfälle nützlich sein, wie z. B. die Weiterleitung zu einer anderen URL basierend auf dem Ursprung (Land) der Anfrage. Verwenden Sie den Header Vary zum Zwischenspeichern von Antworten, die von geografischen Informationen abhängig sind. Umleitungen zu einer bestimmten Landingpage müssen beispielsweise immer `Vary: x-aem-client-country` enthalten. Bei Bedarf können Sie `Cache-Control: private` verwenden, um das Caching zu verhindern. Weitere Informationen finden Sie unter [Caching](/help/implementing/dispatcher/caching.md#html-text).
