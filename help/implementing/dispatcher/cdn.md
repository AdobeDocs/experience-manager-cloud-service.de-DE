---
title: CDN in AEM als Cloud Service
description: CDN in AEM als Cloud Service
translation-type: tm+mt
source-git-commit: dd32e9357bfbd8a9b23db1167cecc4e713cccd99
workflow-type: tm+mt
source-wordcount: '646'
ht-degree: 40%

---


# CDN in AEM als Cloud Service {#cdn}

AEM as Cloud Service wird mit einem integrierten CDN ausgeliefert. Der Hauptzweck besteht darin, die Latenz zu verringern, indem zwischengespeicherte Inhalte von den CDN-Knoten in der Nähe des Browsers bereitgestellt werden. Es ist vollständig verwaltet und für eine optimale Leistung von AEM-Anwendungen konfiguriert.

Das von AEM verwaltete CDN wird die meisten Leistungs- und Sicherheitsanforderungen des Kunden erfüllen. Kunden können optional von ihrem eigenen CDN aus darauf verweisen, das sie verwalten müssen. Dies ist von Fall zu Fall zulässig, wenn bestimmte Voraussetzungen erfüllt sind, unter anderem wenn der Kunde eine veraltete Integration mit seinem CDN-Anbieter hat, die schwer aufzugeben ist.

## AEM-verwaltetes CDN {#aem-managed-cdn}

Führen Sie folgende Schritte aus, um sich auf den Content Versand vorzubereiten, indem Sie das vordefinierte CDN von Adobe verwenden:

1. Stellen Sie Adobe das signierte SSL-Zertifikat und den geheimen Schlüssel zur Verfügung, indem Sie einen Link zu einem sicheren Formular mit diesen Informationen freigeben. Koordinieren Sie diese Aufgabe mit dem Support.
   **Hinweis:** AEM as a Cloud Service unterstützt keine DV (Domain Validated)-Zertifikate.
1. Informieren Sie den Kundensupport:
   * welche benutzerdefinierte Domäne einer bestimmten Umgebung zugeordnet werden soll, wie durch die Programm-ID und die Umgebung-ID definiert. Beachten Sie, dass benutzerdefinierte Domänen auf der Autorenseite nicht unterstützt werden.
   * wenn eine IP-auf die Zulassungsliste setz erforderlich ist, um den Traffic auf eine bestimmte Umgebung zu beschränken.
1. Koordinieren Sie sich mit dem Kundensupport über den Zeitpunkt der erforderlichen Änderungen an den DNS-Datensätzen. Die Anweisungen unterscheiden sich je nach Bedarf:
   * Wenn kein Beispieldatensatz benötigt wird, sollten Kunden den CNAME-DNS-Datensatz so einstellen, dass er auf den FQDN verweist `cdn.adobeaemcloud.com`.
   * Wenn ein Beispieldatensatz benötigt wird, erstellen Sie einen A-Datensatz, der auf die folgenden IPs verweist: 151.101.3.10, 151.101.67.10, 151.101.131.10, 151.101.195.10. Kunden benötigen einen ex Record, wenn der gewünschte FQDN mit der DNS-Zone übereinstimmt. Dies kann mithilfe des UNIX-Befehls dig getestet werden, um zu sehen, ob der SOA-Wert der Ausgabe mit der Domäne übereinstimmt. Der Befehl `dig anything.dev.adobeaemcloud.com` gibt beispielsweise eine SOA (den Beginn der Behörde, d. h. die Zone) zurück, `dev.adobeaemcloud.com` sodass es kein APEX-Datensatz gibt, während eine SOA zurückgegeben wird, `dig dev.adobeaemcloud.com` `dev.adobeaemcloud.com` sodass es sich um einen Apex-Datensatz handelt.
1. Sie werden benachrichtigt, wenn SSL-Zertifikate ablaufen, damit Sie neue SSL-Zertifikate senden können.

**Beschränken des Traffic**

Standardmäßig kann bei einem von Adobe verwalteten CDN-Setup der gesamte öffentliche Traffic zum Publish-Dienst geleitet werden, sowohl für Produktions- als auch für Nicht-Produktions-Umgebungen (Entwicklung und Staging). Wenn Sie den Traffic für eine bestimmte Umgebung auf Publish-Dienst beschränken möchten (z. B. eine Beschränkung der Staging-Umgebung auf eine Reihe von IP-Adressen), sollten Sie sich an den Support wenden, um diese Beschränkungen zu konfigurieren.

## Kunden-CDN verweist auf AEM-verwaltetes CDN {#point-to-point-CDN}

Wenn ein Kunde sein bestehendes CDN verwenden muss, kann er es verwalten und auf das von Adobe verwaltete CDN verweisen, sofern folgende Voraussetzungen erfüllt sind:

* Der Kunde muss über ein vorhandenes CDN verfügen, das nur mit Mühe ersetzt werden kann.
* Der Kunde muss es verwalten.
* Der Kunde muss in der Lage sein, das CDN für die Verwendung mit AEM als Cloud Service zu konfigurieren - siehe die Konfigurationsanweisungen unten.
* Kunden müssen über technische CDN-Experten verfügen, die im Falle von Problemen im Zusammenhang mit dem Kundenservice jederzeit erreichbar sind.
* Der Kunde muss vor der Produktion einen Lasttest durchführen und erfolgreich bestehen.

Konfigurationsanweisungen:

1. Legen Sie die `X-Forwarded-Host`-Kopfzeile mit dem Domänennamen fest.
1. Legen Sie die Host-Kopfzeile mit der Ursprungsdomäne fest, bei der es sich um den CDN-Eingang von Adobe handelt. Der Wert sollte von Adobe stammen.
1. Senden Sie die SNI-Kopfzeile an den Ursprung. Wie die Host-Kopfzeile muss der SNI-Kopfzeile die Ursprungsdomäne sein.
1. Legen Sie die `X-Edge-Key`-Variable fest, die erforderlich ist, um den Traffic korrekt an die AEM-Server zu leiten. Der Wert sollte von Adobe stammen.

Bevor Sie Live-Traffic akzeptieren, sollten Sie beim Adobe-Support überprüfen, ob das End-to-End-Traffic-Routing ordnungsgemäß funktioniert.

Beachten Sie, dass aufgrund des zusätzlichen Hosts möglicherweise ein kleiner Leistungseinbruch zu verzeichnen ist, auch wenn der Hopfen vom CDN des Kunden bis zum von Adobe verwalteten CDN wahrscheinlich effizient sein wird.
