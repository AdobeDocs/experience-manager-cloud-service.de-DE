---
title: CDN in AEM as a Cloud Service
description: CDN in AEM as a Cloud Service
translation-type: tm+mt
source-git-commit: dd32e9357bfbd8a9b23db1167cecc4e713cccd99
workflow-type: tm+mt
source-wordcount: '646'
ht-degree: 100%

---


# CDN in AEM as a Cloud Service {#cdn}

AEM as Cloud Service wird mit einem integrierten CDN ausgeliefert. Der Hauptzweck besteht darin, die Latenz zu verringern, indem zwischengespeicherte Inhalte von den CDN-Knoten in der Nähe des Browsers bereitgestellt werden. Es ist vollständig verwaltet und für eine optimale Leistung von AEM-Anwendungen konfiguriert.

Das von AEM verwaltete CDN erfüllt die meisten Leistungs- und Sicherheitsanforderungen des Kunden. Kunden können optional von ihrem eigenen CDN darauf verweisen, welches sie verwalten müssen. Dies wird von Fall zu Fall auf der Grundlage der Erfüllung bestimmter Voraussetzungen gestattet, insbesondere dass der Kunde eine Altintegration mit seinem CDN-Anbieter hat, die schwer aufzugeben ist.

## AEM-verwaltetes CDN {#aem-managed-cdn}

Befolgen Sie diese Anweisungen, um die Bereitstellung von Inhalten mithilfe des vorkonfigurierten CDN von Adobe vorzubereiten:

1. Stellen Sie Adobe das signierte SSL-Zertifikat und den geheimen Schlüssel zur Verfügung, indem Sie einen Link zu einem sicheren Formular mit diesen Informationen teilen. Koordinieren Sie diese Aufgabe mit dem Support.
   **Hinweis:** AEM as a Cloud Service unterstützt keine DV (Domain Validated)-Zertifikate.
1. Teilen Sie dem Support mit:
   * welche benutzerdefinierte Domäne einer bestimmten Umgebung zugeordnet werden soll, wie durch die Programm-ID und die Umgebung-ID definiert. Beachten Sie, dass benutzerdefinierte Domänen auf der Autorenseite nicht unterstützt werden.
   * Wenn eine IP-Whitelist erforderlich ist, um den Datenverkehr auf eine bestimmte Umgebung zu beschränken.
1. Stimmen Sie sich mit dem Support über den Zeitpunkt der notwendigen Änderungen an den DNS-Einträgen ab. Die Anweisungen unterscheiden sich je nachdem, ob ein Apex-Eintrag erforderlich ist:
   * Wenn kein Apex-Eintrag erforderlich ist, sollten Kunden den CNAME-DNS-Eintrag so einstellen, dass ihr FQDN auf `cdn.adobeaemcloud.com` verweist.
   * Wenn ein Apex-Eintrag erforderlich ist, erstellen Sie einen A-Eintrag, der auf die folgenden IPs verweist: 151.101.3.10, 151.101.67.10, 151.101.131.10, 151.101.195.10. Kunden benötigen einen Apex-Eintrag, wenn der gewünschte FQDN mit der DNS-Zone übereinstimmt. Dies kann mithilfe des Unix-Befehls „dig“ getestet werden, um zu sehen, ob der SOA-Wert der Ausgabe mit der Domäne übereinstimmt. Der Befehl `dig anything.dev.adobeaemcloud.com` gibt beispielsweise eine SOA („Start of Authority“, d. h. die Zone) von `dev.adobeaemcloud.com` zurück – es ist also kein APEX-Eintrag, während `dig dev.adobeaemcloud.com` eine SOA von `dev.adobeaemcloud.com` zurückgibt – es ist also ein APEX-Eintrag.
1. Sie werden benachrichtigt, wenn SSL-Zertifikate ablaufen, damit Sie neue SSL-Zertifikate senden können.

**Beschränken des Traffic**

Standardmäßig kann bei einem von Adobe verwalteten CDN-Setup der gesamte öffentliche Traffic zum Publish-Dienst geleitet werden, sowohl für Produktions- als auch für Nicht-Produktions-Umgebungen (Entwicklung und Staging). Wenn Sie den Traffic für eine bestimmte Umgebung auf Publish-Dienst beschränken möchten (z. B. eine Beschränkung der Staging-Umgebung auf eine Reihe von IP-Adressen), sollten Sie sich an den Support wenden, um diese Beschränkungen zu konfigurieren.

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

Beachten Sie, dass es aufgrund des zusätzlichen Wechsels möglicherweise zu einem kleinen Leistungseinbruch kommt, obwohl Wechsel vom Kunden-CDN zum von Adobe verwalteten CDN wahrscheinlich effizient sind.
