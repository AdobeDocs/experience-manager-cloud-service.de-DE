---
title: Protokollierung
description: Erfahren Sie, wie Sie globale Parameter für den zentralen Protokollierungsdienst konfigurieren, bestimmte Einstellungen für einzelne Dienste festlegen oder eine Datenprotokollierung anfordern können.
translation-type: tm+mt
source-git-commit: 86103b40e931ec00e0c15e9dbcbdf396c8eb05c9
workflow-type: tm+mt
source-wordcount: '2212'
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

>[!NOTE]
>
>HTTP-Anforderungen, die aus dem Dispatcher-Cache der Veröffentlichungsstufe oder dem Upstream-CDN bereitgestellt werden, werden in diesen Protokollen nicht übernommen.

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

**Beispielprotokollausgabe**

```
22.06.2020 18:33:30.120 [cm-p12345-e6789-aem-author-86657cbb55-xrnzq] *ERROR* [qtp501076283-1809] io.prometheus.client.dropwizard.DropwizardExports Failed to get value from Gauge
22.06.2020 18:33:30.229 [cm-p12345-e6789-aem-author-86657cbb55-xrnzq] *INFO* [qtp501076283-1805] org.apache.sling.auth.core.impl.SlingAuthenticator getAnonymousResolver: Anonymous access not allowed by configuration - requesting credentials
22.06.2020 18:33:30.370 [cm-p12345-e6789-aem-author-86657cbb55-xrnzq] *INFO* [73.91.59.34 [1592850810364] GET /libs/granite/core/content/login.html HTTP/1.1] org.apache.sling.i18n.impl.JcrResourceBundle Finished loading 0 entries for 'en_US' (basename: <none>) in 4ms
22.06.2020 18:33:30.372 [cm-p12345-e6789-aem-author-86657cbb55-xrnzq] *INFO* [FelixLogListener] org.apache.sling.i18n Service [5126, [java.util.ResourceBundle]] ServiceEvent REGISTERED
22.06.2020 18:33:30.372 [cm-p12345-e6789-aem-author-86657cbb55-xrnzq] *WARN* [73.91.59.34 [1592850810364] GET /libs/granite/core/content/login.html HTTP/1.1] libs.granite.core.components.login.login$jsp j_reason param value 'unknown' cannot be mapped to a valid reason message: ignoring
```

**Protokollformat**

<table>
<tbody>
<tr>
<td>Datum und Uhrzeit</td>
<td>29.04.2020 21:50:13.398</td>
</tr>
<tr>
<td>AEM als Cloud Service-Node-ID</td>
<td>[cm-p1234-e5678-aem-author-59555cb5b8-q7l9s]</td>
</tr>
<tr>
<td>Protokollebene</td>
<td>DEBUG</td>
</tr>
<tr>
<td>Thread</td>
<td>qtp2130572036-1472</td>
</tr>
<tr>
<td>Java-Klasse</td>
<td>com.example.approval.workflow.impl.CustomApprovalWorkflow</td>
</tr>
<tr>
<td>Protokollmeldung</td>
<td>Kein angegebener Genehmiger, Standard: [ Creative Genehmiger-Benutzergruppe ]</td>
</tr>
</tbody>
</table>

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

**Protokollformat**

<table>
<tbody>
<tr>
<td>Datum und Uhrzeit</td>
<td>29/April/2020:19:14:21 +0000</td>
</tr>
<tr>
<td>Antrags-/Antwortseiten-ID</td>
<td><code>[137]</code></td>
</tr>
<tr>
<td>HTTP-Methode</td>
<td>POST</td>
</tr>
<tr>
<td>URL</td>
<td>/conf/global/settings/dam/adminui-extension/metadataProfile/</td>
</tr>
<tr>
<td>Protokoll</td>
<td>HTTP/1.1
</td>
</tr>
<tr>
<td>AEM als Cloud Service-Node-ID</td>
<td>[cm-p1234-e5678-aem-author-59555cb5b8-q7l9s]</td>
</tr>
</tbody>
</table>

### Protokoll konfigurieren {#configuring-the-log}

Das AEM HTTP-Anforderungsprotokoll ist in AEM als Cloud Service nicht konfigurierbar.

## AEM HTTP Access Logging {#aem-http-access-logging}

AEM als Cloud Service-HTTP-Zugriffsprotokollierung zeigt HTTP-Anforderungen in der Reihenfolge der Zeit an. Jeder Protokolleintrag stellt die HTTP-Anforderung dar, die auf AEM zugreift.

Dieses Protokoll ist hilfreich, um schnell zu verstehen, welche HTTP-Anforderungen an AEM gesendet werden, ob sie erfolgreich sind, indem Sie sich den zugehörigen HTTP-Antwortstatuscode ansehen und wie lange die HTTP-Anforderung dauerte. Dieses Protokoll kann auch hilfreich sein, um die Aktivität eines bestimmten Benutzers zu debuggen, indem die Protokolleinträge nach Benutzern gefiltert werden.

**Beispielprotokollausgabe**

```
cm-p1234-e26813-aem-author-59555cb5b8-8kgr2 - example@adobe.com 30/Apr/2020:17:37:14 +0000  "GET /libs/granite/ui/references/clientlibs/references.lc-5188e85840c529149e6cd29d94e74ad5-lc.min.css HTTP/1.1" 200 1141 "https://author-p10711-e26813.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/en/images/example.jpeg&_charset_=utf8" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.122 Safari/537.36"
cm-p1234-e26813-aem-author-59555cb5b8-8kgr2 - example@adobe.com 30/Apr/2020:17:37:14 +0000  "GET /libs/dam/gui/coral/components/admin/customthumb/clientlibs.lc-60e4443805c37afa0c74b674b141f1df-lc.min.css HTTP/1.1" 200 809 "https://author-p10711-e26813.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/en/images/example.jpeg&_charset_=utf8" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.122 Safari/537.36"
cm-p1234-e26813-aem-author-59555cb5b8-8kgr2 - example@adobe.com 30/Apr/2020:17:37:14 +0000  "GET /libs/dam/gui/coral/components/admin/metadataeditor/clientlibs/metadataeditor.lc-4a2226d8232f8b7ab27d24820b9ddd64-lc.min.js HTTP/1.1" 200 7965 "https://author-p10711-e26813.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/en/images/example.jpeg&_charset_=utf8" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.122 Safari/537.36"
```

**Protokollformat**

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

**Beispielprotokollausgabe**

```
cm-p1234-e5678-aem-publish-b86c6b466-qpfvp - - 17/Jul/2020:09:14:41 +0000  "GET /etc.clientlibs/wknd/clientlibs/clientlib-site/resources/images/favicons/favicon-32.png HTTP/1.1" 200 715 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:78.0) Gecko/20100101 Firefox/78.0"
cm-p1234-e5678-aem-publish-b86c6b466-qpfvp - - 17/Jul/2020:09:14:41 +0000  "GET /etc.clientlibs/wknd/clientlibs/clientlib-site/resources/images/favicons/favicon-512.png HTTP/1.1" 200 9631 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:78.0) Gecko/20100101 Firefox/78.0"
cm-p1234-e5678-aem-publish-b86c6b466-qpfvp - - 17/Jul/2020:09:14:42 +0000  "GET /etc.clientlibs/wknd/clientlibs/clientlib-site/resources/images/country-flags/US.svg HTTP/1.1" 200 810 "https://publish-p6902-e30226.adobeaemcloud.com/content/wknd/us/en.html" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:78.0) Gecko/20100101 Firefox/78.0"
```

**Protokollformat**

<table>
<tbody>
<tr>
<td>AEM als Cloud-Dienst-Knoten-ID</td>
<td>cm-p1234-e26813-aem-publish-5c787687c-lqlxr</td>
</tr>
<tr>
<td>IP-Adresse des Kunden</td>
<td>-</td>
</tr>
<tr>
<td>User</td>
<td>-</td>
</tr>
<tr>
<td>Datum und Uhrzeit</td>
<td>01/Mai/2020:00:09:46 +000</td>
</tr>
<tr>
<td>HTTP-Methode</td>
<td>GET</td>
</tr>
<tr>
<td>URL</td>
<td>/content/example.html</td>
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
<td>Größe</td>
<td>310</td>
</tr>
<tr>
<td>Referenz</td>
<td>-</td>
</tr>
<tr>
<td>Benutzeragent</td>
<td>"Mozilla/5.0 (Macintosh) Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, wie Gecko) Chrome/81.0.4044.122 Safari/537.36"</td>
</tr>
</tbody>
</table>

### Apache HTTPD Web Server Access Log konfigurieren {#configuring-the-apache-httpd-webs-server-access-log}

Dieses Protokoll ist in AEM als Cloud Service nicht konfigurierbar.

## Apache HTTPD Web Server-Fehlerprotokoll {#apache-httpd-web-server-error-log}

Das Apache HTTP-Webserver-Fehlerprotokoll enthält Anweisungen für jeden Fehler im Webserver/Dispatcher der Veröffentlichungsstufe.

Informationen zum Fehlerprotokollformat finden Sie in der [offiziellen Dokumentation](https://httpd.apache.org/docs/2.4/logs.html#errorlog)von Apache.

**Beispielprotokollausgabe**

```
Fri Jul 17 02:19:48.093820 2020 [mpm_worker:notice] [pid 1:tid 140272153361288] [cm-p1234-e30226-aem-publish-b86c6b466-b9427] AH00292: Apache/2.4.43 (Unix) Communique/4.3.4-20200424 mod_qos/11.63 configured -- resuming normal operations
Fri Jul 17 02:19:48.093874 2020 [core:notice] [pid 1:tid 140272153361288] [cm-p1234-e30226-aem-publish-b86c6b466-b9427] AH00094: Command line: 'httpd -d /etc/httpd -f /etc/httpd/conf/httpd.conf -D FOREGROUND -D ENVIRONMENT_PROD'
Fri Jul 17 02:29:34.517189 2020 [mpm_worker:notice] [pid 1:tid 140293638175624] [cm-p1234-e30226-aem-publish-b496f64bf-5vckp] AH00295: caught SIGTERM, shutting down
```

**Protokollformat**

<table>
<tbody>
<tr>
<td>Datum und Uhrzeit</td>
<td>Fr. Juli 17 02:16:42.608913 2020</td>
</tr>
<tr>
<td>Ereignis-Ebene</td>
<td>[mpm_Worker:Notice]</td>
</tr>
<tr>
<td>Prozess-ID</td>
<td>[pid 1:tid 140715149343624]</td>
</tr>
<tr>
<td>Name der Werbeunterbrechung</td>
<td>[cm-p1234-e56789-aem-publish-b86c6b466-qpfvp]</td>
</tr>
<tr>
<td>Nachricht</td>
<td>AH00094: Befehlszeile: "httpd -d /etc/httpd -f /etc/httpd/conf/httpd.conf -D FOREGROUND -D </td>
</tr>
</tbody>
</table>

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

**Beispiel**

```
[17/Jul/2020:23:48:06 +0000] [I] [cm-p12904-e25628-aem-publish-6c5f7c9dbd-mzcvr] "GET /content/wknd/us/en/adventures.html" - 475ms [publishfarm/0] [action miss] "publish-p12904-e25628.adobeaemcloud.com"
[17/Jul/2020:23:48:07 +0000] [I] [cm-p12904-e25628-aem-publish-6c5f7c9dbd-mzcvr] "GET /content/wknd/us/en/adventures/climbing-new-zealand/_jcr_content/root/responsivegrid/carousel/item_1571266094599.coreimg.jpeg/1473680817282/sport-climbing.jpeg" 302 10ms [publishfarm/0] [action none] "publish-p12904-e25628.adobeaemcloud.com"
[17/Jul/2020:23:48:07 +0000] [I] [cm-p12904-e25628-aem-publish-6c5f7c9dbd-mzcvr] "GET /content/wknd/us/en/adventures/ski-touring-mont-blanc/_jcr_content/root/responsivegrid/carousel/item_1571168419252.coreimg.jpeg/1572047288089/adobestock-238230356.jpeg" 302 11ms [publishfarm/0] [action none] "publish-p12904-e25628.adobeaemcloud.com"
```

**Protokollformat**

<table>
<tbody>
<tr>
<td>Datum und Uhrzeit</td>
<td>[17/Juli/2020:23:48:16 +0000]</td>
</tr>
<tr>
<td>Name der Werbeunterbrechung</td>
<td>[cm-p12904-e25628-aem-publish-6c5f7c9dbd-mzcvr]</td>
</tr>
<tr>
<td>Protokoll</td>
<td>GET</td>
</tr>
<tr>
<td>URL</td>
<td>/content/experience-fragments/wknd/language-masters/en/contributors/sofia-sjoeberg/master/_jcr_content/root/responsivegrid/image.coreimg.100.500.jpeg/1572236359031/ayo-ogunseinde-237739.jpeg</td>
</tr>
<tr>
<td>Dispatcher-Antwortstatuscode</td>
<td>/content/experience-fragments/wknd/language-masters/en/contributors/sofia-sjoeberg/master/_jcr_content/root/responsivegrid/image.coreimg.100.500.jpeg/1572236359031/ayo-ogunseinde-237739.jpeg</td>
</tr>
<tr>
<td>Dauer</td>
<td>1949ms</td>
</tr>
<tr>
<td>Zuchtbetrieb</td>
<td>[publishfarm/0]</td>
</tr>
<tr>
<td>Cachestatus</td>
<td>[Aktionsmangel]</td>
</tr>
<tr>
<td>Host</td>
<td>"publish-p12904-e25628.adobeaemcloud.com"</td>
</tr>
</tbody>
</table>

### Konfigurieren des Dispatcher-Fehlerprotokolls {#configuring-the-dispatcher-error-log}

Die Loglevels des Dispatchers werden durch die Variable DISP_LOG_LEVEL in der Datei definiert `conf.d/variables/global.var`.

Sie kann auf &quot;Fehler&quot;, &quot;Warn&quot;, &quot;Info&quot;, &quot;Debug&quot;und &quot;Trace1&quot;mit dem Standardwert &quot;Warn&quot;eingestellt werden.

Während die Protokollierung von Dispatchern mehrere andere Stufen der Protokollierungsgranularität unterstützt, empfiehlt die AEM als Cloud Service die Verwendung der unten beschriebenen Stufen.

Um die Protokollierungsstufe pro Umgebung festzulegen, verwenden Sie den entsprechenden bedingten Zweig in der `global.var` Datei, wie nachfolgend beschrieben:

```
Define DISP_LOG_LEVEL Debug
  
<IfDefine ENVIRONMENT_STAGE>
  ...
  Define DISP_LOG_LEVEL Warn
  ...
</IfDefine>
<IfDefine ENVIRONMENT_PROD>
  ...
  Define DISP_LOG_LEVEL Error
  ...
</IfDefine>
```

## Zugriff auf Protokolle {#how-to-access-logs}

### Cloud-Umgebung {#cloud-environments}

AEM als Cloud Service-Protokolle für Cloud-Dienste können entweder über die Cloud Manager-Oberfläche heruntergeladen oder über die Befehlszeile über die Adobe-E/A-Befehlszeilenschnittstelle protokolliert werden. Weitere Informationen finden Sie in der Protokolldokumentation [zu](/help/implementing/cloud-manager/manage-logs.md)Cloud Manager.

### Lokales SDK {#local-sdk}

AEM als Cloud Service-SDK stellt Protokolldateien zur Unterstützung der lokalen Entwicklung bereit.

AEM Protokolle befinden sich im Ordner `crx-quickstart/logs`, in dem die folgenden Protokolle angezeigt werden können:

* AEM Java-Protokoll: `error.log`
* AEM HTTP-Anforderungsprotokoll: `request.log`
* AEM HTTP-Zugriffsprotokoll: `access.log`

Apache-Ebenenprotokolle, einschließlich Dispatcher, befinden sich im Docker-Container, der den Dispatcher enthält. Informationen zum Beginn des Dispatchers finden Sie in der Dokumentation zum [Dispatcher](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html) .

So rufen Sie die Protokolle ab:

1. Geben Sie in der Befehlszeile `docker ps` zur Liste Ihrer Container ein
1. Um sich beim Container anzumelden, geben Sie &quot;`docker exec -it <container> /bin/sh`&quot;ein, wobei `<container>` die Dispatcher-Container-ID aus dem vorherigen Schritt ist
1. Navigieren Sie zum Cache-Stammordner unter `/mnt/var/www/html`
1. Die Protokolle befinden sich unter `/etc/httpd/logs`
1. Inspect die Protokolle: Sie können unter dem Ordner XYZ aufgerufen werden, in dem die folgenden Protokolle angezeigt werden:
   * Apache HTTPD Web server access log - `httpd_access.log`
   * Apache HTTPD-Webserver-Fehlerprotokolle `httpd_error.log`
   * Dispatcher-Protokolle - `dispatcher.log`

Die Protokolle werden auch direkt an die Terminalausgabe gedruckt. Meistens sollten diese Protokolle DEBUG sein, was bei Ausführung von Docker durch Übergabe in der Debug-Ebene als Parameter erreicht werden kann. Beispiel:

`DISP_LOG_LEVEL=Debug ./bin/docker_run.sh out docker.for.mac.localhost:4503 8080`

## Debugging von Produktion und Phase {#debugging-production-and-stage}

Unter außergewöhnlichen Umständen müssen die Protokollebenen in Stage- oder Produktions-Umgebung geändert werden, um eine genauere Granularität zu erhalten.

Dies ist zwar möglich, erfordert jedoch Änderungen an den Protokollebenen in den Konfigurationsdateien in Git von Warn und Fehler zu Debug und eine Bereitstellung, um diese Konfigurationsänderungen als Cloud Service mit den Umgebung zu AEM.

Je nach Traffic und der Menge der von Debug geschriebenen Protokollanweisung kann dies zu Leistungsbeeinträchtigungen auf der Umgebung führen. Daher wird empfohlen, dass Änderungen an den Debugging-Stufen für die Phasen und die Produktion wie folgt vorgenommen werden:

* Vorsichtig und nur, wenn absolut notwendig
* auf die entsprechenden Ebenen zurückgeführt und so bald wie möglich wieder eingesetzt

## Splunk Logs {#splunk-logs}

Kunden mit Splunk-Konten können über das Kundensupport-Ticket beantragen, dass ihre AEM Cloud Service-Protokolle an den entsprechenden Index weitergeleitet werden. Die Protokollierungsdaten entsprechen den Protokolldownloads von Cloud Manager, es ist jedoch ggf. sinnvoll, die im Splunk-Produkt verfügbaren Abfragen zu nutzen.

Die Netzwerkbandbreite, die mit an Splunk gesendeten Protokollen verknüpft ist, wird als Teil der Netzwerk-E/A-Nutzung des Kunden betrachtet.

### Aktivieren der Splunk-Weiterleitung {#enabling-splunk-forwarding}

In der Supportanfrage sollten Kunden Folgendes angeben:

* Der Splunk-Host
* Splunk-Index
* Der Splunk-Port
* Das Splunk-HEC-Token. Weitere Informationen finden Sie auf [dieser Seite](https://docs.splunk.com/Documentation/Splunk/8.0.4/Data/HECExamples).

Die oben genannten Eigenschaften sollten für jede relevante Programm/Umgebung-Typkombination angegeben werden.  Wenn ein Kunde z. B. Entwicklungs-, Staging- und Produktions-Umgebung wünschte, sollte er drei Informationssätze bereitstellen, wie nachfolgend beschrieben.

>[!NOTE]
>
>Splunk-Weiterleitung für Sandbox-Programm-Umgebung wird nicht unterstützt.

Nachfolgend finden Sie eine Beispielanforderung für den Kundensupport:

Programm 123, Production Env

* Splunk-Host: `splunk-hec-ext.acme.com`
* Splunk-Index: acme_123prod (der Kunde kann die gewünschte Benennungsregel auswählen)
* Splunk-Anschluss: 443
* Splunk-HEC-Token: ABC 123

Programm 123, Stage Env

* Splunk-Host: `splunk-hec-ext.acme.com`
* Splunk-Index: acme_123stage
* Splunk-Anschluss: 443
* Splunk-HEC-Token: ABC 123

Programm 123, Dev Envs

* Splunk-Host: `splunk-hec-ext.acme.com`
* Splunk-Index: acme_123dev
* Splunk-Anschluss: 443
* Splunk-HEC-Token: ABC 123

Es kann ausreichen, dass für jede Umgebung derselbe Splunk-Index verwendet wird. In diesem Fall kann entweder das `aem_env_type` Feld verwendet werden, um basierend auf den Werten dev, stage und prod zu unterscheiden. Wenn mehrere dev-Umgebung vorhanden sind, kann auch das `aem_env_id` Feld verwendet werden. Einige Unternehmen können einen eigenen Index für die Protokolle der Produktions-Umgebung wählen, wenn der zugehörige Index den Zugriff auf eine reduzierte Gruppe von Splunk-Benutzern einschränkt.

Im Folgenden finden Sie einen Beispielprotokolleintrag:

```
aem_env_id: 1242
aem_env_type: dev
aem_program_id: 12314
aem_tier: author
file_path: /var/log/aem/error.log
host: 172.34.200.12 
level: INFO
msg: [FelixLogListener] com.adobe.granite.repository Service [5091, [org.apache.jackrabbit.oak.api.jmx.SessionMBean]] ServiceEvent REGISTERED
orig_time: 16.07.2020 08:35:32.346
pod_name: aemloggingall-aem-author-77797d55d4-74zvt
splunk_customer: true
```
