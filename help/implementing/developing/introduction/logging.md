---
title: Protokollierung
description: Erfahren Sie, wie Sie globale Parameter für den zentralen Protokollierungsdienst konfigurieren, bestimmte Einstellungen für einzelne Dienste festlegen oder eine Datenprotokollierung anfordern können.
translation-type: tm+mt
source-git-commit: 23f7b4b41abf9b909ec55a7f37b6b8e78c689b9b
workflow-type: tm+mt
source-wordcount: '1305'
ht-degree: 8%

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

**Beispiel**

```
cm-p1234-e26813-aem-author-59555cb5b8-8kgr2 - example@adobe.com 30/Apr/2020:17:37:14 +0000  "GET /libs/granite/ui/references/clientlibs/references.lc-5188e85840c529149e6cd29d94e74ad5-lc.min.css HTTP/1.1" 200 1141 "https://author-p10711-e26813.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/en/images/example.jpeg&_charset_=utf8" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.122 Safari/537.36"
cm-p1234-e26813-aem-author-59555cb5b8-8kgr2 - example@adobe.com 30/Apr/2020:17:37:14 +0000  "GET /libs/dam/gui/coral/components/admin/customthumb/clientlibs.lc-60e4443805c37afa0c74b674b141f1df-lc.min.css HTTP/1.1" 200 809 "https://author-p10711-e26813.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/en/images/example.jpeg&_charset_=utf8" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.122 Safari/537.36"
cm-p1234-e26813-aem-author-59555cb5b8-8kgr2 - example@adobe.com 30/Apr/2020:17:37:14 +0000  "GET /libs/dam/gui/coral/components/admin/metadataeditor/clientlibs/metadataeditor.lc-4a2226d8232f8b7ab27d24820b9ddd64-lc.min.js HTTP/1.1" 200 7965 "https://author-p10711-e26813.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/en/images/example.jpeg&_charset_=utf8" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.122 Safari/537.36"
```

<table>
<tbody>
<tr>
<td>AEM als Cloud Service-Node-ID</td>
<td>cm-p1235-e2644-aem-author-59555cb5b8-8kgr2</td>
</tr>
<tr>
<td>IP-Adresse des Kunden</td>
<td>-</td>
</tr>
<tr>
<td>User</td>
<td>myuser@adobe.com</td>
</tr>
<tr>
<td>Datum und Uhrzeit</td>
<td>30/April/2020:17:37:14 +000</td>
</tr>
<tr>
<td>HTTP-Methode</td>
<td>GET</td>
</tr>
<tr>
<td>URL</td>
<td>/libs/granite/ui/references/clientlibs/references.lc-5188e85840c529149e6cd29d94e74ad5-lc.min.css</td>
</tr>
<tr>
<td>Protokoll</td>
<td>HTTP/1.1</td>
</tr>
<tr>
<td>HTTP-Antwortstatus</td>
<td>200</td>
</tr>
<tr>
<td>HTTP-Anforderungszeit in Millisekunden</td>
<td>1141</td>
</tr>
<tr>
<td>Referrer</td>
<td><code>"https://author-p1234-e4444.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/wknd/en/adventures/surf-camp-in-costa-rica/adobestock_266405335.jpeg&_charset_=utf8"</code></td>
</tr>
<tr>
<td>Benutzeragent</td>
<td>"Mozilla/5.0 (Macintosh) Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, wie Gecko) Chrome/81.0.4044.122 Safari/537.36"</td>
</tr>
</tbody>
</table>

### HTTP-Zugriffsprotokoll konfigurieren {#configuring-the-http-access-log}

Das HTTP-Zugriffsprotokoll ist in AEM als Cloud Service nicht konfigurierbar.

## Apache Web Server and Dispatcher Logging {#apache-web-server-and-dispatcher-logging}

AEM als Cloud Service stellt drei Protokolle für die Apache-Webserver- und Dispatcher-Ebene im Bereich Veröffentlichen bereit:

* Apache HTTPD Web Server Access-Protokoll
* Apache HTTPD Web Server-Fehlerprotokoll
* Dispatcher-Protokoll

Beachten Sie, dass diese Protokolle nur für die Veröffentlichungsstufe verfügbar sind.

Dieser Protokollsatz bietet Einblicke in HTTP-Anforderungen an die AEM als Cloud Service-Veröffentlichungsstufe, bevor diese Anforderungen die AEM Anwendung erreichen. Dies ist wichtig, da im Idealfall die meisten HTTP-Anforderungen an die Server der Veröffentlichungsstufe von Inhalten verarbeitet werden, die vom Apache HTTPD-Webserver und AEM Dispatcher zwischengespeichert werden und niemals die AEM Anwendung selbst erreichen. Daher gibt es keine Protokollanweisungen für diese Anforderungen in AEM Java-, Anforderungs- oder Zugriffsprotokollen.

### Apache HTTPD Web Server Access Log {#apache-httpd-web-server-access-log}

Das Apache HTTP-Webserver-Zugriffsprotokoll enthält Anweisungen für jede HTTP-Anforderung, die den Webserver/Dispatcher der Veröffentlichungsstufe erreicht. Beachten Sie, dass Anforderungen, die von einem Upstream-CDN bereitgestellt werden, in diesen Protokollen nicht berücksichtigt werden.

Informationen zum Fehlerprotokollformat finden Sie in der [offiziellen Dokumentation](https://httpd.apache.org/docs/2.4/logs.html#accesslog)von Apache.

**Protokollformat**

<!--blank until prod build finishes-->

**Beispiel**

```
cm-p1234-e5678-aem-publish-b86c6b466-qpfvp - - 17/Jul/2020:09:14:41 +0000  "GET /etc.clientlibs/wknd/clientlibs/clientlib-site/resources/images/favicons/favicon-32.png HTTP/1.1" 200 715 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:78.0) Gecko/20100101 Firefox/78.0"
cm-p1234-e5678-aem-publish-b86c6b466-qpfvp - - 17/Jul/2020:09:14:41 +0000  "GET /etc.clientlibs/wknd/clientlibs/clientlib-site/resources/images/favicons/favicon-512.png HTTP/1.1" 200 9631 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:78.0) Gecko/20100101 Firefox/78.0"
cm-p1234-e5678-aem-publish-b86c6b466-qpfvp - - 17/Jul/2020:09:14:42 +0000  "GET /etc.clientlibs/wknd/clientlibs/clientlib-site/resources/images/country-flags/US.svg HTTP/1.1" 200 810 "https://publish-p6902-e30226.adobeaemcloud.com/content/wknd/us/en.html" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:78.0) Gecko/20100101 Firefox/78.0"
```

### Apache HTTPD Web Server Access Log konfigurieren {#configuring-the-apache-httpd-webs-server-access-log}

Dieses Protokoll ist in AEM als Cloud Service nicht konfigurierbar.

## Apache HTTPD Web Server-Fehlerprotokoll {#apache-httpd-web-server-error-log}

Das Apache HTTP-Webserver-Fehlerprotokoll enthält Anweisungen für jeden Fehler im Webserver/Dispatcher der Veröffentlichungsstufe.

Informationen zum Fehlerprotokollformat finden Sie in der [offiziellen Dokumentation](https://httpd.apache.org/docs/2.4/logs.html#errorlog)von Apache.

**Protokollformat**

<!--placeholder-->

**Beispiel**

```
Fri Jul 17 02:19:48.093820 2020 [mpm_worker:notice] [pid 1:tid 140272153361288] [cm-p1234-e30226-aem-publish-b86c6b466-b9427] AH00292: Apache/2.4.43 (Unix) Communique/4.3.4-20200424 mod_qos/11.63 configured -- resuming normal operations
Fri Jul 17 02:19:48.093874 2020 [core:notice] [pid 1:tid 140272153361288] [cm-p1234-e30226-aem-publish-b86c6b466-b9427] AH00094: Command line: 'httpd -d /etc/httpd -f /etc/httpd/conf/httpd.conf -D FOREGROUND -D ENVIRONMENT_PROD'
Fri Jul 17 02:29:34.517189 2020 [mpm_worker:notice] [pid 1:tid 140293638175624] [cm-p1234-e30226-aem-publish-b496f64bf-5vckp] AH00295: caught SIGTERM, shutting down
```

### Konfigurieren des Apache HTTPD Web Server-Fehlerprotokolls {#configuring-the-apache-httpd-web-server-error-log}

Die Protokollierungsstufen mod_rewrite werden durch die Variable REWRITE_LOG_LEVEL in der Datei definiert `conf.d/variables/global.var`.

Sie kann auf &quot;Fehler&quot;, &quot;Warn&quot;, &quot;Info&quot;, &quot;Debug&quot;und &quot;Trace1 - Trace8&quot;mit dem Standardwert &quot;Warn&quot;eingestellt werden. Zum Debugging Ihrer RewriteRules wird empfohlen, die Protokollebene auf Trace2 zu erhöhen.

Weitere Informationen finden Sie in der Dokumentation [zum Modul](https://httpd.apache.org/docs/current/mod/mod_rewrite.html#logging) mod_rewrite.

Um die Protokollebene pro Umgebung festzulegen, verwenden Sie den entsprechenden bedingten Zweig in der Datei &quot;global.var&quot;, wie nachfolgend beschrieben:

```
Define REWRITE_LOG_LEVEL Debug
  
<IfDefine ENVIRONMENT_STAGE>
  ...
  Define REWRITE_LOG_LEVEL Warn
  ...
</IfDefine>
<IfDefine ENVIRONMENT_PROD>
  ...
  Define REWRITE_LOG_LEVEL Error
  ...
</IfDefine>
```

## Dispatcher-Protokoll {#dispatcher-log}

**Protokollformat**

