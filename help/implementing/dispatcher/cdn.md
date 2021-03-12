---
title: CDN in AEM as a Cloud Service
description: CDN in AEM als Cloud Service
translation-type: tm+mt
source-git-commit: c71117de502b1ee756e06e756a643c987113ea45
workflow-type: tm+mt
source-wordcount: '695'
ht-degree: 33%

---


# CDN in AEM as a Cloud Service {#cdn}

AEM as Cloud Service wird mit einem integrierten CDN ausgeliefert. Der Hauptzweck besteht darin, die Latenz zu verringern, indem zwischengespeicherte Inhalte von den CDN-Knoten in der Nähe des Browsers bereitgestellt werden. Es ist vollständig verwaltet und für eine optimale Leistung von AEM-Programmen konfiguriert.

Das von AEM verwaltete CDN erfüllt die meisten Leistungs- und Sicherheitsanforderungen des Kunden. Für die Veröffentlichungsebene können Kunden optional von ihrem eigenen CDN darauf verweisen, welches sie verwalten müssen. Dies wird von Fall zu Fall auf der Grundlage der Erfüllung bestimmter Voraussetzungen gestattet, insbesondere dass der Kunde eine Altintegration mit seinem CDN-Anbieter hat, die schwer aufzugeben ist.

## AEM-verwaltetes CDN {#aem-managed-cdn}

Befolgen Sie die folgenden Abschnitte, um die Selbstbedienungs-Benutzeroberfläche von Cloud Manager zu verwenden, um sich auf den Content Versand vorzubereiten, indem Sie AEM vorkonfiguriertes CDN verwenden:

1. [Verwalten von SSL-Zertifikaten](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md)
1. [Verwalten von benutzerdefinierten Domänennamen](/help/implementing/cloud-manager/custom-domain-names/introduction.md)

**Beschränken des Traffic**

Standardmäßig kann bei einem AEM verwalteten CDN-Setup der gesamte öffentliche Traffic zum Veröffentlichungsdienst wechseln, und zwar sowohl für Produktions- als auch für Nicht-Produktions- (Entwicklungs- und Bereitstellungsdienste) Umgebung. Wenn Sie den Traffic auf den Veröffentlichungsdienst für eine bestimmte Umgebung beschränken möchten (z. B. die Staging-Aktivität auf eine Reihe von IP-Adressen begrenzen), können Sie dies über die Benutzeroberfläche von Cloud Manager als Selbstbedienung durchführen.

Weitere Informationen finden Sie unter [Verwalten von IP-Zulassungslisten](/help/implementing/cloud-manager/ip-allow-lists/introduction.md).

>[!CAUTION]
>
>Nur Anfragen von den zulässigen IPs werden vom verwalteten CDN AEM bearbeitet. Wenn Sie Ihre eigene CDN auf die AEM verwaltete CDN verweisen, stellen Sie sicher, dass die IPs Ihrer CDN in der Zulassungsliste enthalten sind.

## Kunden-CDN verweist auf AEM-verwaltetes CDN {#point-to-point-CDN}

Muss ein Kunde sein bestehendes CDN verwenden, kann er es verwalten und auf das AEM verwaltete CDN verweisen, sofern folgende Voraussetzungen erfüllt sind:

* Der Kunde muss über ein vorhandenes CDN verfügen, dessen Ersetzung aufwendig wäre.
* Der Kunde muss es verwalten.
* Der Kunde muss in der Lage sein, das CDN für die Verwendung mit AEM as a Cloud Service zu konfigurieren – siehe Konfigurationsanweisungen unten.
* Der Kunde muss über technische CDN-Experten verfügen, die im Falle von Problemen im Zusammenhang mit dem Projekt auf Anfrage zur Verfügung stehen.
* Der Kunde muss einen Belastungstest durchführen und erfolgreich bestehen, bevor er zur Produktion übergeht.

Konfigurationsanweisungen:

1. Legen Sie die `X-Forwarded-Host`-Kopfzeile mit dem Domain-Namen fest.
1. Legen Sie Host-Header mit der Herkunft-Domäne fest, die die AEM CDN-Adresse ist. Der Wert sollte von Adobe stammen.
1. Senden Sie die SNI-Kopfzeile an den Ursprung. Wie der Host-Header muss der SNI-Header die Domäne der Herkunft sein.
1. Legen Sie entweder `X-Edge-Key` oder `X-AEM-Edge-Key` fest (wenn Ihr CDN X-Edge-* abschneidet), was erforderlich ist, um den Traffic ordnungsgemäß zu den AEM-Servern zu leiten. Der Wert sollte von Adobe stammen. Bitte informieren Sie die Adobe, wenn Sie direkten Zugriff auf die Adobe CDN&#39;s Ingress (zu blockieren, wenn `X-Edge-Key` nicht vorhanden).

Bevor Sie Live-Traffic akzeptieren, sollten Sie sich beim Kundensupport der Adobe vergewissern, dass das End-to-End-Traffic-Routing ordnungsgemäß funktioniert.

>[!NOTE]
>
>Kunden, die ihr eigenes CDN verwalten, sollten die Integrität der Header sicherstellen, die an AEM CDN gesendet werden. Es wird beispielsweise empfohlen, dass Kunden alle `X-Forwarded-*`-Kopfzeilen löschen und sie auf bekannte und kontrollierte Werte setzen. Beispiel: `X-Forwarded-For` sollte die IP-Adresse des Kunden enthalten, während `X-Forwarded-Host` den Host der Site enthalten sollte.

Es gibt möglicherweise einen kleinen Leistungsschlag aufgrund des zusätzlichen Hofes, obwohl Hopfen vom Kunden CDN bis zum AEM verwalteten CDN wahrscheinlich effizient sein werden.

Beachten Sie, dass diese CDN-Konfiguration des Kunden für die Veröffentlichungsstufe unterstützt wird, jedoch nicht vor der Autorenebene.

## Geolocation-Kopfzeilen {#geo-headers}

Das AEM verwaltete CDN fügt jeder Anforderung Kopfzeilen hinzu mit:

* Ländercode: `x-aem-client-country`
* Kontinentalcode: `x-aem-client-continent`

Die Werte für die Ländercodes sind die Alpha-2-Codes, die [hier](https://en.wikipedia.org/wiki/ISO_3166-1) beschrieben werden.

Die Werte für die Kontinentalcodes lauten:

* AF Afrika
* AN Antarktika
* AS Asien
* Europa
* NA Nordamerika
* OC Ozeanien
* SA Südamerika

Diese Informationen können in Anwendungsfällen nützlich sein, z. B. bei der Weiterleitung auf eine andere URL, die auf der Herkunft (Land) der Anforderung basiert. Verwenden Sie den Header &quot;Vary&quot;zum Zwischenspeichern von Antworten, die von geografischen Informationen abhängig sind. Umleitungen zu einer bestimmten Landingpage sollten beispielsweise immer `Vary: x-aem-client-country` enthalten. Bei Bedarf können Sie `Cache-Control: private` verwenden, um die Zwischenspeicherung zu verhindern. Siehe auch [Zwischenspeicherung](/help/implementing/dispatcher/caching.md#html-text).
