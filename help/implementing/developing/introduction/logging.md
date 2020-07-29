---
title: Protokollierung
description: Erfahren Sie, wie Sie globale Parameter für den zentralen Protokollierungsdienst konfigurieren, bestimmte Einstellungen für einzelne Dienste festlegen oder eine Datenprotokollierung anfordern können.
translation-type: tm+mt
source-git-commit: 161dc733d335fc62d7c3017647fe27c64a8dd26f
workflow-type: tm+mt
source-wordcount: '1077'
ht-degree: 10%

---


# Protokollierung {#logging}

AEM as a Cloud Service ist eine Plattform, auf der Kunden benutzerdefinierten Code einbinden können, um einzigartige Erlebnisse für ihre Kunden zu erstellen. Vor diesem Hintergrund ist die Protokollierung eine wichtige Funktion, um die Codeausführung bei lokalen Entwicklungs- und Cloud-Umgebung zu debuggen und zu verstehen, insbesondere die AEM als Dev-Umgebung eines Cloud Service.

AEM Protokollierungs- und Protokollierungsebenen werden in Konfigurationsdateien verwaltet, die als Teil des AEM Projekts in Git gespeichert und als Teil des AEM Projekts über Cloud Manager bereitgestellt werden. Die Anmeldung AEM als Cloud Service kann in zwei logische Sätze unterteilt werden:

* AEM Protokollierung, die die Protokollierung auf AEM Anwendungsebene durchführt
* Apache HTTPD Web Server/Dispatcher-Protokollierung, die die Protokollierung des Webservers und des Dispatchers auf der Veröffentlichungsstufe durchführt.

## AEM {#aem-loggin}

Die Protokollierung auf AEM Anwendungsebene erfolgt über drei Protokolle:

1. AEM Java-Protokolle, die Java-Protokollanweisungen für die AEM Anwendung wiedergeben.
1. HTTP-Anforderungsprotokolle, die Informationen zu HTTP-Anforderungen und deren Antworten AEM
1. HTTP-Zugriffsprotokolle, in denen zusammengefasste Informationen und HTTP-Anforderungen, die von AEM bereitgestellt werden, protokolliert werden

Beachten Sie, dass HTTP-Anforderungen, die vom Dispatcher-Cache der Veröffentlichungsstufe oder vom Upstream-CDN bereitgestellt werden, nicht in diesen Protokollen angezeigt werden.

## AEM Java-Protokollierung {#aem-java-logging}

AEM als Cloud Service bietet Zugriff auf Java-Protokollanweisungen. Entwickler von Anwendungen für AEM sollten sich an die allgemeinen Best Practices für die Java-Protokollierung halten und relevante Anweisungen zur Ausführung von benutzerdefiniertem Code auf den folgenden Protokollebenen protokollieren:

<table>
<tr>
<td>
<b>AEM Umgebung</b></td>
<td>
<b>Protokollebene</b></td>
<td>
<b>Beschreibung</b></td>
<td>
<b>Verfügbarkeit der Protokollerklärung</b></td>
</tr>
<tr>
<td>
Entwicklung</td>
<td>
DEBUG</td>
<td>
Beschreibt, was in der Anwendung geschieht.<br>
Wenn die DEBUG-Protokollierung aktiv ist, werden Anweisungen protokolliert, die ein klares Bild von den auftretenden Aktivitäten sowie allen wichtigen Parametern, die sich auf die Verarbeitung auswirken, vermitteln.</td>
<td>
<ul>
<li> Lokale Entwicklung</li>
<li>Entwicklung</li>
</ul></td>
</tr>
<tr>
<td>
Staging</td>
<td>
WARN</td>
<td>
Beschreibt Bedingungen, bei denen Fehler auftreten können.<br>
Wenn die WARN-Protokollierung aktiv ist, werden nur Anweisungen protokolliert, die auf Bedingungen hinweisen, die sich der Unter-Optimalität nähern.</td>
<td>
<ul>
<li> Lokale Entwicklung</li>
<li>Entwicklung</li>
<li>Staging</li>
</ul></td>
</tr>
<tr>
<td>
Produktion</td>
<td>
FEHLER</td>
<td>
Beschreibt Bedingungen, die auf einen Fehler hinweisen und gelöst werden müssen.<br>
Wenn die ERROR-Protokollierung aktiv ist, werden nur Anweisungen protokolliert, die auf Fehler hinweisen. ERROR-Protokollerklärungen deuten auf ein schwerwiegendes Problem hin, das so bald wie möglich gelöst werden sollte.</td>
<td>
<ul>
<li> Lokale Entwicklung</li>
<li>Entwicklung</li>
<li>Staging</li>
<li>Produktion</li>
</ul></td>
</tr>
</table>

Während die Java-Protokollierung mehrere andere Stufen der Protokollierungsgranularität unterstützt, empfiehlt AEM Cloud Service die Verwendung der drei oben beschriebenen Stufen.

AEM Protokollierungsstufen werden über die OSGi-Umgebung festgelegt, die wiederum Git zugewiesen und über Cloud Manager bereitgestellt wird, um als Cloud Service AEM zu werden. Aus diesem Grund sollten Protokollanweisungen konsistent und für die Umgebung-Typen gut bekannt sein, um sicherzustellen, dass die Protokolle, die über AEM verfügbar sind, auf der optimalen Protokollebene verfügbar sind, ohne dass eine erneute Bereitstellung der Anwendung mit der aktualisierten Protokollstufenkonfiguration erforderlich ist.

### Protokollformat {#log-format}

| Datum und Uhrzeit | AEM als Cloud Service-ID | Protokollebene | Thread | Java-Klasse | Protokollmeldung |
|---|---|---|---|---|---|
| 29.04.2020 21:50:13.398 | `[cm-p1234-e5678-aem-author-59555cb5b8-q7l9s]` | `*DEBUG*` | qtp2130572036-1472 | com.example.approval.workflow.impl.CustomApprovalWorkflow | `No specified approver, defaulting to [ Creative Approvers user group ]` |

**Beispielprotokollausgabe**

```
22.06.2020 18:33:30.120 [cm-p12345-e6789-aem-author-86657cbb55-xrnzq] *ERROR* [qtp501076283-1809] io.prometheus.client.dropwizard.DropwizardExports Failed to get value from Gauge
22.06.2020 18:33:30.229 [cm-p12345-e6789-aem-author-86657cbb55-xrnzq] *INFO* [qtp501076283-1805] org.apache.sling.auth.core.impl.SlingAuthenticator getAnonymousResolver: Anonymous access not allowed by configuration - requesting credentials
22.06.2020 18:33:30.370 [cm-p12345-e6789-aem-author-86657cbb55-xrnzq] *INFO* [73.91.59.34 [1592850810364] GET /libs/granite/core/content/login.html HTTP/1.1] org.apache.sling.i18n.impl.JcrResourceBundle Finished loading 0 entries for 'en_US' (basename: <none>) in 4ms
22.06.2020 18:33:30.372 [cm-p12345-e6789-aem-author-86657cbb55-xrnzq] *INFO* [FelixLogListener] org.apache.sling.i18n Service [5126, [java.util.ResourceBundle]] ServiceEvent REGISTERED
22.06.2020 18:33:30.372 [cm-p12345-e6789-aem-author-86657cbb55-xrnzq] *WARN* [73.91.59.34 [1592850810364] GET /libs/granite/core/content/login.html HTTP/1.1] libs.granite.core.components.login.login$jsp j_reason param value 'unknown' cannot be mapped to a valid reason message: ignoring
```

### Konfigurationsprotokolle {#configuration-loggers}

AEM Java-Protokolle werden als OSGi-Konfiguration definiert und somit für die Zielgruppe spezifische AEM als Cloud Service-Umgebung unter Verwendung von Ausführungsmodusordnern.

Konfigurieren Sie die Java-Protokollierung für benutzerdefinierte Java-Pakete über OSGi-Konfigurationen für die Sling LogManager-Factory. Es gibt zwei unterstützte Konfigurationseigenschaften:

| OSGi-Konfigurationseigenschaft | Beschreibung |
|---|---|
| org.apache.sling.commons.log.names | Die Java-Pakete, für die Protokollanweisungen gesammelt werden sollen. |
| org.apache.sling.commons.log.level | Die Protokollierungsebene, auf der die Java-Pakete protokolliert werden sollen, angegeben von org.apache.sling.commons.log.names |

Das Ändern anderer LogManager OSGi-Konfigurationseigenschaften kann zu Verfügbarkeitsproblemen in AEM als Cloud Service führen.

Die folgenden Beispiele zeigen die empfohlenen Protokollierungskonfigurationen (unter Verwendung des Platzhalter-Java-Pakets von `com.example`) für die drei AEM als Cloud Service-Umgebung.

### Entwicklung {#development}

/apps/my-app/config/org.apache.sling.commons.log.LogManager.factory.config-example.cfg.json

```
{
    "org.apache.sling.commons.log.names": ["com.example"],
    "org.apache.sling.commons.log.level": "debug"
}
```

### Staging {#stage}

/apps/my-app/config.stage/org.apache.sling.commons.log.LogManager.factory.config-example.cfg.json

```
{
    "org.apache.sling.commons.log.names": ["com.example"],
    "org.apache.sling.commons.log.level": "warn"
}
```

### Produktion {#productiomn}

/apps/my-app/config.prod/org.apache.sling.commons.log.LogManager.factory.config-example.cfg.json

```
{
    "org.apache.sling.commons.log.names": ["com.example"],
    "org.apache.sling.commons.log.level": "error"
}
```

## AEM HTTP-Anforderungsprotokoll {#aem-http-request-logging}

AEM als HTTP-Anforderungsprotokoll eines Cloud Service bietet einen Einblick in die HTTP-Anforderungen an AEM und ihre HTTP-Antworten in der Reihenfolge der Zeit. Dieses Protokoll ist hilfreich, um die HTTP-Anfragen an AEM und die Reihenfolge zu verstehen, in der sie verarbeitet und beantwortet werden.

Der Schlüssel zum Verständnis dieses Protokolls ist die Zuordnung der HTTP-Anforderungs- und -Antwortpaare zu ihren IDs, gekennzeichnet durch den numerischen Wert in den Klammern. Beachten Sie, dass bei Anforderungen und den zugehörigen Antworten häufig andere HTTP-Anforderungen und -Antworten im Protokoll interagiert werden.

### Protokollformat {#http-request-logging-format}

| Datum und Uhrzeit | Antrags-/Antwortseiten-ID |  | HTTP-Methode | URL | Protokoll | AEM als Cloud Service-Node-ID |
|---|---|---|---|---|---|---|
| 29/April/2020:19:14:21 +0000 | `[137]` | -> | POST | /conf/global/settings/dam/adminui-extension/metadataProfile/ | HTTP/1.1 | `[cm-p1234-e5678-aem-author-59555cb5b8-q7l9s]` |

**Beispielprotokoll**

```
29/Apr/2020:19:14:21 +0000 [137] -> POST /conf/global/settings/dam/adminui-extension/metadataprofile/ HTTP/1.1 [cm-p1234-e5678-aem-author-59555cb5b8-q7l9s]
...
29/Apr/2020:19:14:22 +0000 [139] -> GET /mnt/overlay/dam/gui/content/processingprofilepage/metadataprofiles/editor.html/conf/global/settings/dam/adminui-extension/metadataprofile/main HTTP/1.1 [cm-p1234-e5678-aem-author-59555cb5b8-q7l9s]
...
29/Apr/2020:19:14:21 +0000 [137] <- 201 text/html 111ms [cm-p1234-e5678-aem-author-59555cb5b8-q7l9s]
...
29/Apr/2020:19:14:22 +0000 [139] <- 200 text/html;charset=utf-8 637ms [cm-p1234-e5678-aem-author-59555cb5b8-q7l9s]
```

### Protokoll konfigurieren {#configuring-the-log}

Das AEM HTTP-Anforderungsprotokoll ist in AEM als Cloud Service nicht konfigurierbar.

## AEM HTTP Access Logging {#aem-http-access-logging}

AEM als Cloud Service-HTTP-Zugriffsprotokollierung zeigt HTTP-Anforderungen in der Reihenfolge der Zeit an. Jeder Protokolleintrag stellt die HTTP-Anforderung dar, die auf AEM zugreift.

Dieses Protokoll ist hilfreich, um schnell zu verstehen, welche HTTP-Anforderungen an AEM gesendet werden, ob sie erfolgreich sind, indem Sie sich den zugehörigen HTTP-Antwortstatuscode ansehen und wie lange die HTTP-Anforderung dauerte. Dieses Protokoll kann auch hilfreich sein, um die Aktivität eines bestimmten Benutzers zu debuggen, indem die Protokolleinträge nach Benutzern gefiltert werden.

### Protokollformat {#access-log-format}

| AEM als Cloud Service-Node-ID | IP-Adresse des Kunden | User |  | Datum und Uhrzeit |  | HTTP-Methode | URL | Protokoll |  | HTTP-Antwort | HTTP-Anforderungszeit in Millisekunden | Referrer | Benutzeragent |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| cm-p1235-e2644-aem-author-59555cb5b8-8kgr2 | - | `myuser@adobe.com` | 30/April/2020:17:37:14 +000 | &quot; | GET | /libs/granite/ui/references/clientlibs/references.lc-5188e85840c529149e6cd29d94e74ad5-lc.min.css |  | HTTP/1.1 | &quot; | 200 | 1141 | `"https://author-p1234-e4444.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/wknd/en/adventures/surf-camp-in-costa-rica/adobestock_266405335.jpeg&_charset_=utf8"` | &quot;Mozilla/5.0 (Macintosh) Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, wie Gecko) Chrome/81.0.4044.122 Safari/537.36&quot; |

**Beispiel**

```
cm-p1234-e26813-aem-author-59555cb5b8-8kgr2 - example@adobe.com 30/Apr/2020:17:37:14 +0000  "GET /libs/granite/ui/references/clientlibs/references.lc-5188e85840c529149e6cd29d94e74ad5-lc.min.css HTTP/1.1" 200 1141 "https://author-p10711-e26813.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/en/images/example.jpeg&_charset_=utf8" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.122 Safari/537.36"
cm-p1234-e26813-aem-author-59555cb5b8-8kgr2 - example@adobe.com 30/Apr/2020:17:37:14 +0000  "GET /libs/dam/gui/coral/components/admin/customthumb/clientlibs.lc-60e4443805c37afa0c74b674b141f1df-lc.min.css HTTP/1.1" 200 809 "https://author-p10711-e26813.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/en/images/example.jpeg&_charset_=utf8" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.122 Safari/537.36"
cm-p1234-e26813-aem-author-59555cb5b8-8kgr2 - example@adobe.com 30/Apr/2020:17:37:14 +0000  "GET /libs/dam/gui/coral/components/admin/metadataeditor/clientlibs/metadataeditor.lc-4a2226d8232f8b7ab27d24820b9ddd64-lc.min.js HTTP/1.1" 200 7965 "https://author-p10711-e26813.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/en/images/example.jpeg&_charset_=utf8" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.122 Safari/537.36"
```

### HTTP-Zugriffsprotokoll konfigurieren {#configuring-the-http-access-log}

Das HTTP-Zugriffsprotokoll ist in AEM als Cloud Service nicht konfigurierbar.

## Apache Web Server-/Dispatcher-Protokollierung {#dispatcher-logging}

AEM als Cloud Service stellt drei Protokolle für die Apache-Webserver- und Dispatcher-Ebene im Bereich Veröffentlichen bereit:

* Apache HTTPD Web Server Access-Protokoll
* Apache HTTPD Web Server-Fehlerprotokoll
* Dispatcher-Protokoll

Beachten Sie, dass diese Protokolle nur für die Veröffentlichungsstufe verfügbar sind.

Dieser Protokollsatz bietet Einblicke in HTTP-Anforderungen an die AEM als Cloud Service-Veröffentlichungsstufe, bevor diese Anforderungen die AEM Anwendung erreichen. Dies ist wichtig, da im Idealfall die meisten HTTP-Anforderungen an die Server der Veröffentlichungsstufe vom Apache HTTPD-Webserver und AEM Dispatcher im Cache verarbeitet werden und niemals die AEM Anwendung selbst erreichen. Daher gibt es keine Protokollanweisungen für diese Anforderungen in AEM Java-, Anforderungs- oder Zugriffsprotokollen.