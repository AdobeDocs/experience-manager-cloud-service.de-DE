---
title: CDN in AEM as a Cloud Service
description: CDN in AEM als Cloud Service
translation-type: tm+mt
source-git-commit: c71117de502b1ee756e06e756a643c987113ea45
workflow-type: tm+mt
source-wordcount: '695'
ht-degree: 70%

---


# CDN in AEM as a Cloud Service {#cdn}

AEM as Cloud Service wird mit einem integrierten CDN ausgeliefert. Der Hauptzweck besteht darin, die Latenz zu verringern, indem zwischengespeicherte Inhalte von den CDN-Knoten in der Nähe des Browsers bereitgestellt werden. Es ist vollständig verwaltet und für eine optimale Leistung von AEM-Programmen konfiguriert.

Das von AEM verwaltete CDN erfüllt die meisten Leistungs- und Sicherheitsanforderungen des Kunden. Für die Veröffentlichungsebene können Kunden optional von ihrem eigenen CDN darauf verweisen, welches sie verwalten müssen. Dies wird von Fall zu Fall auf der Grundlage der Erfüllung bestimmter Voraussetzungen gestattet, insbesondere dass der Kunde eine Altintegration mit seinem CDN-Anbieter hat, die schwer aufzugeben ist.

## AEM-verwaltetes CDN {#aem-managed-cdn}

Befolgen Sie die nachstehenden Abschnitte, um mithilfe der Cloud Manager-Self-Service-Benutzeroberfläche die Bereitstellung von Inhalten mit dem vorkonfigurierten CDN von AEM vorzubereiten:

1. [Verwalten von SSL-Zertifikaten](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md)
1. [Verwalten benutzerdefinierter Domain-Namen](/help/implementing/cloud-manager/custom-domain-names/introduction.md)

**Beschränken des Traffic**

Standardmäßig kann bei einem von AEM verwalteten CDN-Setup der gesamte öffentliche Traffic zum Veröffentlichungs-Service geleitet werden, sowohl für Produktions- als auch für Nicht-Produktions-Umgebungen (Entwicklung und Staging). Wenn Sie den Traffic für eine bestimmte Umgebung auf den Veröffentlichungs-Service beschränken möchten (z. B. eine Beschränkung der Staging-Umgebung auf eine Reihe von IP-Adressen), können Sie dies mittels Self-Service-Verfahren über die Cloud Manager-Benutzeroberfläche tun.

Weitere Informationen finden Sie unter [Verwalten von IP-Zulassungslisten](/help/implementing/cloud-manager/ip-allow-lists/introduction.md).

>[!CAUTION]
>
>Nur Anfragen von den zulässigen IPs werden vom verwalteten CDN von AEM bearbeitet. Wenn Sie Ihre eigene CDN auf die AEM verwaltete CDN verweisen, stellen Sie sicher, dass die IPs Ihrer CDN in der Zulassungsliste enthalten sind.

## Kunden-CDN verweist auf AEM-verwaltetes CDN {#point-to-point-CDN}

Wenn ein Kunde sein bestehendes CDN verwenden muss, kann er es verwalten und auf das von AEM verwaltete CDN verweisen, sofern folgende Voraussetzungen erfüllt sind:

* Der Kunde muss über ein vorhandenes CDN verfügen, dessen Ersetzung aufwendig wäre.
* Der Kunde muss es verwalten.
* Der Kunde muss in der Lage sein, das CDN für die Verwendung mit AEM as a Cloud Service zu konfigurieren – siehe Konfigurationsanweisungen unten.
* Der Kunde muss über technische CDN-Experten verfügen, die im Falle von Problemen im Zusammenhang mit dem Projekt auf Anfrage zur Verfügung stehen.
* Der Kunde muss einen Belastungstest durchführen und erfolgreich bestehen, bevor er zur Produktion übergeht.

Konfigurationsanweisungen:

1. Legen Sie die `X-Forwarded-Host`-Kopfzeile mit dem Domain-Namen fest.
1. Legen Sie die Host-Kopfzeile mit der Ursprungs-Domain fest, bei der es sich um den CDN-Eingang von AEM handelt. Der Wert sollte von Adobe stammen.
1. Senden Sie die SNI-Kopfzeile an den Ursprung. Wie der Host-Header muss der SNI-Header die Domäne der Herkunft sein.
1. Legen Sie entweder `X-Edge-Key` oder `X-AEM-Edge-Key` fest (wenn Ihr CDN X-Edge-* abschneidet), was erforderlich ist, um den Traffic ordnungsgemäß zu den AEM-Servern zu leiten. Der Wert sollte von Adobe stammen. Bitte informieren Sie die Adobe, wenn Sie direkten Zugriff auf die Adobe CDN&#39;s Ingress (zu blockieren, wenn `X-Edge-Key` nicht vorhanden).

Bevor Sie Live-Traffic akzeptieren, sollten Sie sich beim Kundensupport der Adobe vergewissern, dass das End-to-End-Traffic-Routing ordnungsgemäß funktioniert.

>[!NOTE]
>
>Kunden, die ihr eigenes CDN verwalten, sollten die Integrität der Header sicherstellen, die an AEM CDN gesendet werden. Es wird beispielsweise empfohlen, dass Kunden alle `X-Forwarded-*`-Kopfzeilen löschen und sie auf bekannte und kontrollierte Werte setzen. Beispiel: `X-Forwarded-For` sollte die IP-Adresse des Kunden enthalten, während `X-Forwarded-Host` den Host der Site enthalten sollte.

Aufgrund des zusätzlichen Wechsels kann zu einem kleinen Leistungseinbruch kommen, obwohl Wechsel vom Kunden-CDN zum von AEM verwalteten CDN wahrscheinlich effizient sind.

Beachten Sie, dass diese CDN-Konfiguration des Kunden für die Veröffentlichungsstufe unterstützt wird, jedoch nicht vor der Autorenebene.

## Geolocation-Kopfzeilen {#geo-headers}

Das AEM verwaltete CDN fügt jeder Anforderung Kopfzeilen hinzu mit:

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

Diese Informationen können für Anwendungsfälle nützlich sein, wie z. B. die Weiterleitung zu einer anderen URL basierend auf dem Ursprung (Land) der Anfrage. Verwenden Sie den Header &quot;Vary&quot;zum Zwischenspeichern von Antworten, die von geografischen Informationen abhängig sind. Umleitungen zu einer bestimmten Landingpage sollten beispielsweise immer `Vary: x-aem-client-country` enthalten. Bei Bedarf können Sie `Cache-Control: private` verwenden, um das Caching zu verhindern. Weitere Informationen finden Sie unter [Caching](/help/implementing/dispatcher/caching.md#html-text).
