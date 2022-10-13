---
title: CDN in AEM as a Cloud Service
description: CDN in AEM as a Cloud Service
feature: Dispatcher
exl-id: a3f66d99-1b9a-4f74-90e5-2cad50dc345a
source-git-commit: 95ec89fa4bb71a63121bc86a74a15cc7812ae342
workflow-type: tm+mt
source-wordcount: '1163'
ht-degree: 72%

---

# CDN in AEM as a Cloud Service {#cdn}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_cdn"
>title="CDN in AEM as a Cloud Service"
>abstract="AEM as Cloud Service wird mit einem integrierten CDN ausgeliefert. Der Hauptzweck besteht darin, die Latenz zu reduzieren, indem zwischenspeicherbare Inhalte von den CDN-Knoten in der Nähe des Browsers bereitgestellt werden. Es ist vollständig verwaltet und für eine optimale Leistung von AEM-Programmen konfiguriert."

AEM as Cloud Service wird mit einem integrierten CDN ausgeliefert. Der Hauptzweck besteht darin, die Latenz zu verringern, indem zwischengespeicherte Inhalte von den CDN-Knoten in der Nähe des Browsers bereitgestellt werden. Es ist vollständig verwaltet und für eine optimale Leistung von AEM-Programmen konfiguriert.

Das von AEM verwaltete CDN erfüllt die meisten Leistungs- und Sicherheitsanforderungen des Kunden. Für die Veröffentlichungsebene können Kunden optional von ihrem eigenen CDN darauf verweisen, welches sie verwalten müssen. Dies wird von Fall zu Fall auf der Grundlage der Erfüllung bestimmter Voraussetzungen gestattet, insbesondere dass der Kunde eine Altintegration mit seinem CDN-Anbieter hat, die schwer aufzugeben ist.

Sehen Sie sich auch die folgenden Videos [Cloud 5 AEM CDN Teil 1](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-5/cloud5-aem-cdn-part1.html?lang=de) und [Cloud 5 AEM CDN Teil 2](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-5/cloud5-aem-cdn-part2.html?lang=de) an, um zusätzliche Informationen über CDN in AEM as a Cloud Service zu erhalten.

## In AEM verwaltetes CDN  {#aem-managed-cdn}

Befolgen Sie die folgenden Abschnitte, um die Cloud Manager-Self-Service-Benutzeroberfläche zur Vorbereitung der Inhaltsbereitstellung mithilfe AEM vordefinierten CDN zu verwenden:

1. [Verwalten von SSL-Zertifikaten](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md)
1. [Verwalten von benutzerdefinierten Domain-Namen](/help/implementing/cloud-manager/custom-domain-names/introduction.md)

>[!NOTE]
>
>Benutzerdefinierte Domänen werden in Cloud Manager unterstützt **only** wenn Sie das AEM verwaltete CDN verwenden. Wenn Sie Ihr eigenes CDN und [verweisen auf das AEM verwaltete CDN](#point-to-point-CDN) Sie müssen dieses spezifische CDN verwenden, um Domänen zu verwalten, die nicht von Cloud Manager sind.

**Beschränken des Traffic**

Standardmäßig kann bei einem von AEM verwalteten CDN-Setup der gesamte öffentliche Traffic zum Veröffentlichungs-Service geleitet werden, sowohl für Produktions- als auch für produktionsfremde Umgebungen (Entwicklung und Staging). Wenn Sie den Traffic für eine bestimmte Umgebung auf den Veröffentlichungs-Service beschränken möchten (z. B. eine Beschränkung der Staging-Umgebung auf eine Reihe von IP-Adressen), können Sie dies mittels Self-Service-Verfahren über die Cloud Manager-Benutzeroberfläche tun.

Weitere Informationen finden Sie unter [Verwalten von IP-Zulassungslisten](/help/implementing/cloud-manager/ip-allow-lists/introduction.md).

>[!CAUTION]
>
>Nur Anforderungen von den zulässigen IPs werden von AEM verwalteten CDN bereitgestellt. Wenn Sie Ihr eigenes CDN auf das verwaltete CDN von AEM verweisen, stellen Sie sicher, dass die IPs Ihres CDN in der Zulassungsliste enthalten sind.

## Kunden-CDN verweist auf AEM-verwaltetes CDN {#point-to-point-CDN}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_byocdn"
>title="Kunden-CDN verweist auf AEM-verwaltetes CDN"
>abstract="AEM as a Cloud Service bietet Kunden eine Option, ihr bestehendes CDN zu verwenden. Für die Veröffentlichungsebene können Kunden optional von ihrem eigenen CDN darauf verweisen, welches sie verwalten müssen. Dies wird von Fall zu Fall auf der Grundlage der Erfüllung bestimmter Voraussetzungen gestattet, insbesondere dass der Kunde eine Altintegration mit seinem CDN-Anbieter hat, die schwer aufzugeben ist."

Wenn ein Kunde sein bestehendes CDN verwenden muss, kann er es verwalten und auf das von AEM verwaltete CDN verweisen, sofern folgende Voraussetzungen erfüllt sind:

* Der Kunde muss über ein vorhandenes CDN verfügen, dessen Ersetzung aufwendig wäre.
* Der Kunde muss es verwalten.
* Der Kunde muss in der Lage sein, das CDN für die Verwendung mit Adobe Experience Manager as a Cloud Service zu konfigurieren. Weitere Informationen finden Sie in den Konfigurationsanweisungen unten.
* Der Kunde muss über technische CDN-Experten verfügen, die im Falle von Problemen im Zusammenhang mit dem Projekt auf Anfrage zur Verfügung stehen.
* Der Kunde muss einen Belastungstest durchführen und erfolgreich bestehen, bevor er zur Produktion übergeht.

Konfigurationsanweisungen:

1. Weisen Sie Ihr CDN auf den Eingang des Adobe-CDN als Ursprungsdomäne zu. Beispiel: `publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com`.
1. SNI muss auch auf den Eingang des Adobe-CDN eingestellt werden..
1. Legen Sie die Host-Kopfzeile auf die Ursprungs-Domain fest. Beispiel: `Host:publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com`.
1. Legen Sie die Kopfzeile `X-Forwarded-Host` mit dem Domain-Namen fest, damit AEM die Host-Kopfzeile ermitteln kann. Beispiel: `X-Forwarded-Host:example.com`.
1. Satz `X-AEM-Edge-Key`. Der Wert muss von Adobe stammen.

   * Dies ist erforderlich, damit das Adobe-CDN die Anfragequelle überprüfen und die `X-Forwarded-*`-Header an die AEM-Anwendung übergeben kann. Beispielsweise wird `X-Forwarded-For` verwendet, um die Client-IP zu bestimmen. Somit liegt es in der Verantwortung des vertrauenswürdigen Aufrufers (d. h. des vom Kunden verwalteten CDN), die Korrektheit der `X-Forwarded-*`-Header sicherzustellen (siehe Hinweis unten).
   * Optional kann der Zugriff auf den Eingang zum Adobe CDN blockiert werden, wenn kein `X-AEM-Edge-Key` vorhanden ist. Bitte informieren Sie Adobe, wenn Sie direkten Zugriff auf den Eingang zum Adobe CDN benötigen (oder um ihn zu blockieren).

Siehe [Beispielkonfigurationen von CDN-Anbietern](#sample-configurations) für Konfigurationsbeispiele von führenden CDN-Anbietern.

Bevor Sie Live-Traffic akzeptieren, sollten Sie beim Adobe-Support überprüfen, ob das End-to-End-Traffic-Routing ordnungsgemäß funktioniert.

Nach dem Abrufen des `X-AEM-Edge-Key` können Sie wie folgt testen, ob die Anfrage korrekt weitergeleitet wird.

Unter Linux:

```
curl https://publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com -H "X-Forwarded-Host: example.com" -H "X-AEM-Edge-Key: <PROVIDED_EDGE_KEY>"
```

Windows:

```
curl https://publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com --header "X-Forwarded-Host: example.com" --header "X-AEM-Edge-Key: <PROVIDED_EDGE_KEY>"
```

>[!NOTE]
>
>Bei Verwendung Ihres eigenen CDN müssen die Domänen und Zertifikate nicht in Cloud Manager installiert werden. Das Routing im Adobe-CDN erfolgt mithilfe der Standarddomäne `publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com`.

>[!NOTE]
>
>Kunden, die ein eigenes CDN verwalten, müssen die Integrität der Kopfzeilen sicherstellen, die an das CDN von AEM gesendet werden. Beispielsweise empfehlen wir, dass Kunden alle `X-Forwarded-*`-Kopfzeilen löschen und für sie bekannte und kontrollierte Werte festlegen. Beispiel: `X-Forwarded-For` muss die IP-Adresse des Kunden enthalten, während `X-Forwarded-Host` den Host der Website enthalten muss.

>[!NOTE]
>
>Sandbox-Programmumgebungen unterstützen kein vom Kunden bereitgestelltes CDN.

Der zusätzliche Wechsel zwischen dem Kunden-CDN und dem AEM CDN ist nur erforderlich, wenn ein Cache fehlschlägt. Durch die Verwendung der in diesem Artikel beschriebenen Cache-Optimierungsstrategien sollte das Hinzufügen eines Kunden-CDN nur zu einer vernachlässigbaren Latenz führen.

Beachten Sie, dass diese kundenspezifische CDN-Konfiguration für die Veröffentlichungsebene unterstützt wird, jedoch nicht vor der Autorenebene.

### Beispielkonfigurationen von CDN-Anbietern {#sample-configurations}

Nachfolgend finden Sie einige Konfigurationsbeispiele von einer Reihe führender CDN-Anbieter.

**Akamai**

![Akamai1](assets/akamai1.png "Akamai")
![Akamai2](assets/akamai2.png "Akamai")

**Amazon CloudFront**

![CloudFront1](assets/cloudfront1.png "Amazon CloudFront")
![CloudFront2](assets/cloudfront2.png "Amazon CloudFront")

**Cloudflare**

![Cloudflare1](assets/cloudflare1.png "Cloudflare")
![Cloudflare2](assets/cloudflare2.png "Cloudflare")

## Inhaltsdisposition {#content-disposition}

Für die Veröffentlichungsstufe ist die Standardeinstellung für die Bereitstellung von Blobs als Anlage. Dies kann mit dem Standard [Content-Disposition-Header](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Disposition) im Dispatcher.

Im Folgenden finden Sie ein Beispiel dafür, wie die Konfiguration aussehen sollte:

```
<LocationMatch "^\/content\/dam.*\.(pdf).*">
 Header unset Content-Disposition
 Header set Content-Disposition inline
</LocationMatch>
```

## Geolocation-Kopfzeilen {#geo-headers}

Das AEM-verwaltete CDN fügt jeder Anfrage Kopfzeilen hinzu. Diese enthalten:

* Länder-Code: `x-aem-client-country`
* Kontinental-Code: `x-aem-client-continent`

>[!NOTE]
>
>Im Falle eines kundenverwalteten CDN spiegeln diese Header den Speicherort des CDN-Proxyservers des Kunden und nicht den tatsächlichen Client wider.  Daher sollten für kundenverwaltetes CDN Geolocation-Header vom Kunden-CDN verwaltet werden.

Die Werte für die Länder-Codes sind die [hier](https://de.wikipedia.org/wiki/ISO_3166-1) beschriebenen Alpha-2-Codes.

Die Werte für die Kontinental-Codes lauten:

* AF Afrika
* AN Antarktika
* AS Asien
* EU Europa
* NA Nordamerika
* OC Ozeanien
* SA Südamerika

Diese Informationen können für Anwendungsfälle nützlich sein, wie z. B. die Weiterleitung zu einer anderen URL basierend auf dem Ursprung (Land) der Anfrage. Verwenden Sie die Vary-Kopfzeile zum Zwischenspeichern von Antworten, die von geografischen Daten abhängig sind. Umleitungen zu einer bestimmten Landingpage müssen beispielsweise immer `Vary: x-aem-client-country` enthalten. Bei Bedarf können Sie `Cache-Control: private` verwenden, um das Caching zu verhindern. Weitere Informationen finden Sie unter [Caching](/help/implementing/dispatcher/caching.md#html-text).
