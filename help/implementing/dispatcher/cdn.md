---
title: CDN in AEM as a Cloud Service
description: CDN in AEM as a Cloud Service
feature: Dispatcher
exl-id: a3f66d99-1b9a-4f74-90e5-2cad50dc345a
source-git-commit: b71299a08c6dec8e88c4259b3d03481b20b310cb
workflow-type: tm+mt
source-wordcount: '926'
ht-degree: 98%

---

# CDN in AEM as a Cloud Service {#cdn}


>[!CONTEXTUALHELP]
>id="aemcloud_golive_cdn"
>title="CDN in AEM as a Cloud Service"
>abstract="AEM as Cloud Service wird mit einem integrierten CDN ausgeliefert. Der Hauptzweck besteht darin, die Latenz zu verringern, indem zwischengespeicherte Inhalte von den CDN-Knoten in der Nähe des Browsers bereitgestellt werden. Es ist vollständig verwaltet und für eine optimale Leistung von AEM-Programmen konfiguriert."

AEM as Cloud Service wird mit einem integrierten CDN ausgeliefert. Der Hauptzweck besteht darin, die Latenz zu verringern, indem zwischengespeicherte Inhalte von den CDN-Knoten in der Nähe des Browsers bereitgestellt werden. Es ist vollständig verwaltet und für eine optimale Leistung von AEM-Programmen konfiguriert.

Das von AEM verwaltete CDN erfüllt die meisten Leistungs- und Sicherheitsanforderungen des Kunden. Für die Veröffentlichungsebene können Kunden optional von ihrem eigenen CDN darauf verweisen, welches sie verwalten müssen. Dies wird von Fall zu Fall auf der Grundlage der Erfüllung bestimmter Voraussetzungen gestattet, insbesondere dass der Kunde eine Altintegration mit seinem CDN-Anbieter hat, die schwer aufzugeben ist.

## In AEM verwaltetes CDN  {#aem-managed-cdn}

Befolgen Sie die nachstehenden Abschnitte, um mithilfe der Cloud Manager-Self-Service-Benutzeroberfläche die Bereitstellung von Inhalten mit dem vorkonfigurierten CDN von AEM vorzubereiten:

1. [Verwalten von SSL-Zertifikaten](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md)
1. [Verwalten von benutzerdefinierten Domain-Namen](/help/implementing/cloud-manager/custom-domain-names/introduction.md)

**Beschränken des Traffic**

Standardmäßig kann bei einem von AEM verwalteten CDN-Setup der gesamte öffentliche Traffic zum Veröffentlichungs-Service geleitet werden, sowohl für Produktions- als auch für Nicht-Produktions-Umgebungen (Entwicklung und Staging). Wenn Sie den Traffic für eine bestimmte Umgebung auf den Veröffentlichungs-Service beschränken möchten (z. B. eine Beschränkung der Staging-Umgebung auf eine Reihe von IP-Adressen), können Sie dies mittels Self-Service-Verfahren über die Cloud Manager-Benutzeroberfläche tun.

Weitere Informationen finden Sie unter [Verwalten von IP-Zulassungslisten](/help/implementing/cloud-manager/ip-allow-lists/introduction.md).

>[!CAUTION]
>
>Nur Anfragen von den zulässigen IPs werden vom verwalteten CDN von AEM bearbeitet. Wenn Sie Ihr eigenes CDN auf das verwaltete CDN von AEM verweisen, stellen Sie sicher, dass die IPs Ihres CDN in der Zulassungsliste enthalten sind.

## Kunden-CDN verweist auf AEM-verwaltetes CDN {#point-to-point-CDN}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_byocdn"
>title="Kunden-CDN verweist auf AEM-verwaltetes CDN"
>abstract="AEM as a Cloud Service bietet Kunden eine Option, ihr bestehendes CDN zu verwenden. Für die Veröffentlichungsebene können Kunden optional von ihrem eigenen CDN darauf verweisen, welches sie verwalten müssen. Dies wird von Fall zu Fall auf der Grundlage der Erfüllung bestimmter Voraussetzungen gestattet, insbesondere dass der Kunde eine Altintegration mit seinem CDN-Anbieter hat, die schwer aufzugeben ist."

Wenn ein Kunde sein bestehendes CDN verwenden muss, kann er es verwalten und auf das von AEM verwaltete CDN verweisen, sofern folgende Voraussetzungen erfüllt sind:

* Der Kunde muss über ein vorhandenes CDN verfügen, dessen Ersetzung aufwendig wäre.
* Der Kunde muss es verwalten.
* Der Kunde muss in der Lage sein, das CDN für die Verwendung mit AEM as a Cloud Service zu konfigurieren – siehe Konfigurationsanweisungen unten.
* Der Kunde muss über technische CDN-Experten verfügen, die im Falle von Problemen im Zusammenhang mit dem Projekt auf Anfrage zur Verfügung stehen.
* Der Kunde muss einen Belastungstest durchführen und erfolgreich bestehen, bevor er zur Produktion übergeht.

Konfigurationsanweisungen:

1. Verweisen Sie Ihr CDN auf den Eingang des Adobe-CDN als Ursprungs-Domain. Beispiel: `publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com`.
1. SNI muss auch auf den Eingang des Adobe-CDN eingestellt werden.
1. Legen Sie die Host-Kopfzeile auf die Ursprungs-Domain fest. Beispiel: `Host:publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com`.
1. Legen Sie die Kopfzeile `X-Forwarded-Host` mit dem Domain-Namen fest, damit AEM die Host-Kopfzeile ermitteln kann. Beispiel: `X-Forwarded-Host:example.com`.
1. Satz `X-AEM-Edge-Key`. Der Wert muss von Adobe stammen.
   * Dies ist erforderlich, damit das Adobe-CDN die Anfragequelle überprüfen und die `X-Forwarded-*`-Header an die AEM-Anwendung übergeben kann. Beispielsweise wird `X-Forwarded-For` verwendet, um die Client-IP zu bestimmen. Somit liegt es in der Verantwortung des vertrauenswürdigen Aufrufers (d. h. des vom Kunden verwalteten CDN), die Korrektheit der `X-Forwarded-*`-Header sicherzustellen (siehe Hinweis unten).
   * Optional kann der Zugriff auf den Eingang zum Adobe CDN blockiert werden, wenn kein `X-AEM-Edge-Key` vorhanden ist. Bitte informieren Sie Adobe, wenn Sie direkten Zugriff auf den Eingang zum Adobe CDN benötigen (oder um ihn zu blockieren).

Bevor Sie Live-Traffic akzeptieren, sollten Sie beim Adobe-Support überprüfen, ob das End-to-End-Traffic-Routing ordnungsgemäß funktioniert.

Nach dem Abrufen der `X-AEM-Edge-Key`können Sie wie folgt testen, ob die Anfrage korrekt weitergeleitet wird:

```
curl https://publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com -H 'X-Forwarded-Host: example.com' -H 'X-AEM-Edge-Key: <PROVIDED_EDGE_KEY>'
```

Beachten Sie, dass bei der Verwendung Ihres eigenen CDN keine Notwendigkeit besteht, die Domains und Zertifikate in Cloud Manager zu installieren. Das Routing in Adobe-CDN erfolgt über die Standard-Domain `publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com`.

>[!NOTE]
>
>Kunden, die ein eigenes CDN verwalten, müssen die Integrität der Kopfzeilen sicherstellen, die an das CDN von AEM gesendet werden. Beispielsweise empfehlen wir, dass Kunden alle `X-Forwarded-*`-Kopfzeilen löschen und für sie bekannte und kontrollierte Werte festlegen. Beispiel: `X-Forwarded-For` muss die IP-Adresse des Kunden enthalten, während `X-Forwarded-Host` den Host der Website enthalten muss.

>[!NOTE]
>
>Sandbox-Programmumgebungen unterstützen kein vom Kunden bereitgestelltes CDN.

Aufgrund des zusätzlichen Wechsels kann zu einem kleinen Leistungseinbruch kommen, obwohl Wechsel vom Kunden-CDN zum von AEM verwalteten CDN wahrscheinlich effizient sind.

Beachten Sie, dass diese kundenspezifische CDN-Konfiguration für die Veröffentlichungsebene unterstützt wird, jedoch nicht vor der Autorenebene.

## Geolocation-Kopfzeilen {#geo-headers}

Das AEM-verwaltete CDN fügt jeder Anfrage Kopfzeilen hinzu. Diese enthalten:

* Länder-Code: `x-aem-client-country`
* Kontinental-Code: `x-aem-client-continent`

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
