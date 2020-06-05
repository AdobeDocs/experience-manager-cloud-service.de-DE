---
title: CDN in AEM als Cloud-Dienst
description: CDN in AEM als Cloud-Dienst
translation-type: tm+mt
source-git-commit: 0080ace746f4a7212180d2404b356176d5f2d72c
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 95%

---


# CDN in AEM als Cloud-Dienst {#cdn}

AEM as Cloud Service wird mit einem integrierten CDN ausgeliefert. Der Hauptzweck besteht darin, die Latenz zu verringern, indem zwischengespeicherte Inhalte von den CDN-Knoten in der Nähe des Browsers bereitgestellt werden. Es ist vollständig verwaltet und für eine optimale Leistung von AEM-Anwendungen konfiguriert.

AEM bietet zwei Optionen an:

1. AEM-verwaltetes CDN – Das vorkonfigurierte CDN von AEM. Es handelt sich um eine eng integrierte Option, die keine umfangreichen Kundeninvestitionen zur Unterstützung der CDN-Integration mit AEM erfordert.
1. Das vom Kunden verwaltete CDN verweist auf das AEM-verwaltete CDN – der Kunde verweist sein eigenes CDN auf das vorkonfigurierte CDN von AEM. Der Kunde muss weiterhin sein eigenes CDN verwalten, aber die Investitionen in die Integration mit AEM sind gering.

Die erste Option sollte die meisten Leistungs- und Sicherheitsanforderungen des Kunden erfüllen. Darüber hinaus erfordert sie minimalen Kundenaufwand.

Die zweite Option ist von Fall zu Fall zulässig. Die Entscheidung basiert auf der Erfüllung bestimmter Voraussetzungen, insbesondere dass der Kunde eine Altintegration mit seinem CDN-Anbieter hat, die schwer aufzugeben ist.

Nachfolgend finden Sie eine Entscheidungsmatrix zum Vergleich der beiden Optionen. Weitere Informationen finden Sie in den folgenden Abschnitten.

| Details | AEM-verwaltetes CDN | Vom Kunden verwaltetes CDN verweist auf AEM-CDN |
|---|---|---|
| **Kundenaufwand** | Kein Aufwand, vollständig integriert. Nur CNAME muss auf AEM-verwaltetes CDN verweisen. | Moderate Kundeninvestition. Der Kunde muss sein eigenes CDN verwalten. |
| **Voraussetzungen** | Keine | Vorhandenes CDN, das nur schwer zu ersetzen ist. Vor der Live-Schaltung muss ein erfolgreicher Belastungstest durchgeführt werden. |
| **CDN-Kompetenz** | Keine | Benötigt mindestens eine technische Teilzeitressource mit detailliertem CDN-Wissen, die das CDN des Kunden konfigurieren kann. |
| **Sicherheit** | Verwaltet von Adobe. | Verwaltet von Adobe (und optional vom Kunden bei seinem eigenen CDN). |
| **Leistung** | Optimiert von Adobe. | Profitiert von einigen AEM-CDN-Funktionen, aber möglicherweise kleiner Leistungseinbruch aufgrund des zusätzlichen Wechsels. **Hinweis**: Hops vom Kunden-CDN bis zum Adobe-Out-of-the-Box-CDN (wahrscheinlich effizient). |
| **Caching** | Unterstützt Cache-Kopfzeilen, die auf den Dispatcher angewendet werden. | Unterstützt Cache-Kopfzeilen, die auf den Dispatcher angewendet werden. |
| **Funktionen zur Bild- und Videokomprimierung** | Kann mit Adobe Dynamic Media verwendet werden. | Kann mit Adobe Dynamic Media oder einer kundenverwalteten CDN-Bild-/Videolösung verwendet werden. |

## AEM-verwaltetes CDN {#aem-managed-cdn}

Die Vorbereitung der Inhaltsbereitstellung mithilfe des vorkonfigurierten CDN von Adobe ist einfach, wie nachfolgend beschrieben:

1. Sie stellen Adobe das signierte SSL-Zertifikat und den geheimen Schlüssel zur Verfügung, indem Sie einen Link zu einem sicheren Formular mit diesen Informationen teilen. Koordinieren Sie diese Aufgabe mit dem Support.
   **Hinweis:** AEM as a Cloud Service unterstützt keine DV (Domain Validated)-Zertifikate.
1. Sie sollten den Support informieren:
   * welche benutzerdefinierte Domäne einer bestimmten Umgebung zugeordnet werden soll, wie durch die Programm-ID und die Umgebung-ID definiert.
   * wenn eine IP-Whitelist erforderlich ist, um den Traffic auf eine bestimmte Umgebung zu beschränken.
1. Der Support koordiniert dann mit Ihnen den Zeitpunkt für einen CNAME-DNS-Eintrag und verweist dessen FQDN auf `cdn.adobeaemcloud.com`.
1. Sie werden benachrichtigt, wenn SSL-Zertifikate ablaufen, damit Sie neue SSL-Zertifikate senden können.

**Beschränken des Traffic**

Standardmäßig kann bei einem von Adobe verwalteten CDN-Setup der gesamte öffentliche Traffic zum Publish-Dienst geleitet werden, sowohl für Produktions- als auch für Nicht-Produktions-Umgebungen (Entwicklung und Staging). Wenn Sie den Traffic für eine bestimmte Umgebung auf Publish-Dienst beschränken möchten (z. B. eine Beschränkung der Staging-Umgebung auf eine Reihe von IP-Adressen), sollten Sie sich an den Support wenden, um diese Beschränkungen zu konfigurieren.

## Kunden-CDN verweist auf AEM-verwaltetes CDN {#point-to-point-CDN}

Wird unterstützt, wenn Sie Ihr vorhandenes CDN verwenden möchten, die Anforderungen eines vom Kunden verwalteten CDN jedoch nicht erfüllen können. In diesem Fall verwalten Sie Ihr eigenes CDN, verweisen aber auf das von Adobe verwaltete CDN.

Beachten Sie Folgendes:

1. Sie müssen über ein bestehendes CDN verfügen.
1. Sie müssen es verwalten.
1. Sie müssen in der Lage sein, das CDN für die Verwendung mit AEM as a Cloud Service zu konfigurieren – siehe Konfigurationsanweisungen unten.
1. Sie benötigen technische CDN-Experten, die im Falle von Problemen im Zusammenhang mit dem Projekt auf Anfrage zur Verfügung stehen.
1. Sie müssen einen Belastungstest durchführen und erfolgreich bestehen, bevor Sie zur Produktion übergehen.

Konfigurationsanweisungen:

1. Legen Sie die `X-Forwarded-Host`-Kopfzeile mit dem Domänennamen fest.
1. Legen Sie die Host-Kopfzeile mit der Ursprungsdomäne fest, bei der es sich um den CDN-Eingang von Adobe handelt. Der Wert sollte von Adobe stammen.
1. Senden Sie die SNI-Kopfzeile an den Ursprung. Wie die Host-Kopfzeile muss der SNI-Kopfzeile die Ursprungsdomäne sein.
1. Legen Sie die `X-Edge-Key`-Variable fest, die erforderlich ist, um den Traffic korrekt an die AEM-Server zu leiten. Der Wert sollte von Adobe stammen.

Bevor Sie Live-Traffic akzeptieren, sollten Sie beim Adobe-Support überprüfen, ob das End-to-End-Traffic-Routing ordnungsgemäß funktioniert.
