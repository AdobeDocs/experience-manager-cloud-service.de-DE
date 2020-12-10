---
title: CDN in AEM as a Cloud Service
description: CDN in AEM als Cloud Service
translation-type: tm+mt
source-git-commit: 40119f7b3bdf36af668b79afbcb2802a0b2a6033
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 84%

---


# CDN in AEM as a Cloud Service {#cdn}

AEM as Cloud Service wird mit einem integrierten CDN ausgeliefert. Der Hauptzweck besteht darin, die Latenz zu verringern, indem zwischengespeicherte Inhalte von den CDN-Knoten in der Nähe des Browsers bereitgestellt werden. Es ist vollständig verwaltet und für eine optimale Leistung von AEM-Anwendungen konfiguriert.

Das von AEM verwaltete CDN erfüllt die meisten Leistungs- und Sicherheitsanforderungen des Kunden. Für die Veröffentlichungsebene können Kunden optional von ihrem eigenen CDN darauf verweisen, welches sie verwalten müssen. Dies wird von Fall zu Fall auf der Grundlage der Erfüllung bestimmter Voraussetzungen gestattet, insbesondere dass der Kunde eine Altintegration mit seinem CDN-Anbieter hat, die schwer aufzugeben ist.

## AEM-verwaltetes CDN {#aem-managed-cdn}

Führen Sie die folgenden Schritte aus, um die Selbstbedienungs-Benutzeroberfläche von Cloud Manager zu verwenden, um sich auf den Content Versand vorzubereiten, indem Sie das vordefinierte CDN der Adobe verwenden:

1. [Verwalten von SSL-Zertifikaten](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md)
1. [Verwalten von benutzerdefinierten Domänennamen](/help/implementing/cloud-manager/custom-domain-names/introduction.md)

**Beschränken des Traffic**

Standardmäßig kann bei einem von Adobe verwalteten CDN-Setup der gesamte öffentliche Traffic zum Publish-Service geleitet werden, sowohl für Produktions- als auch für Nicht-Produktions-Umgebungen (Entwicklung und Staging). Wenn Sie den Traffic auf den Veröffentlichungsdienst für eine bestimmte Umgebung beschränken möchten (z. B. die Staging-Aktivität auf eine Reihe von IP-Adressen begrenzen), können Sie dies über die Benutzeroberfläche von Cloud Manager als Selbstbedienung durchführen.

Weitere Informationen finden Sie unter [Verwalten von IP-Zulassungslisten](/help/implementing/cloud-manager/ip-allow-lists/introduction.md).

## Kunden-CDN verweist auf AEM-verwaltetes CDN {#point-to-point-CDN}

Wenn ein Kunde sein bestehendes CDN verwenden muss, kann er es verwalten und auf das von Adobe verwaltete CDN verweisen, sofern folgende Voraussetzungen erfüllt sind:

* Der Kunde muss über ein vorhandenes CDN verfügen, dessen Ersetzung aufwendig wäre.
* Der Kunde muss es verwalten.
* Der Kunde muss in der Lage sein, das CDN für die Verwendung mit AEM as a Cloud Service zu konfigurieren – siehe Konfigurationsanweisungen unten.
* Der Kunde muss über technische CDN-Experten verfügen, die im Falle von Problemen im Zusammenhang mit dem Projekt auf Anfrage zur Verfügung stehen.
* Der Kunde muss einen Belastungstest durchführen und erfolgreich bestehen, bevor er zur Produktion übergeht.

Konfigurationsanweisungen:

1. Legen Sie die `X-Forwarded-Host`-Kopfzeile mit dem Domänennamen fest.
1. Legen Sie die Host-Kopfzeile mit der Ursprungsdomäne fest, bei der es sich um den CDN-Eingang von Adobe handelt. Der Wert sollte von Adobe stammen.
1. Senden Sie die SNI-Kopfzeile an den Ursprung. Wie die Host-Kopfzeile muss der SNI-Kopfzeile die Ursprungsdomäne sein.
1. Legen Sie die `X-Edge-Key`-Variable fest, die erforderlich ist, um den Traffic korrekt an die AEM-Server zu leiten. Der Wert sollte von Adobe stammen.

Bevor Sie Live-Traffic akzeptieren, sollten Sie beim Adobe-Support überprüfen, ob das End-to-End-Traffic-Routing ordnungsgemäß funktioniert.

Aufgrund des zusätzlichen Wechsels kann zu einem kleinen Leistungseinbruch kommen, obwohl Wechsel vom Kunden-CDN zum von Adobe verwalteten CDN wahrscheinlich effizient sind.

Beachten Sie, dass diese kundenspezifische CDN-Konfiguration für die Veröffentlichungsebene unterstützt wird, jedoch nicht vor der Autorenebene.
