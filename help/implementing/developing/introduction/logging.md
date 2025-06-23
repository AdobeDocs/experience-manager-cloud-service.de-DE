---
title: Protokollieren für AEM as a Cloud Service
description: Erfahren Sie, wie Sie die Protokollierung für AEM as a Cloud Service verwenden können, um globale Parameter für den zentralen Protokollierungs-Dienst zu konfigurieren, bestimmte Einstellungen für die einzelnen Dienste festzulegen oder die Datenprotokollierung anzufordern.
exl-id: 262939cc-05a5-41c9-86ef-68718d2cd6a9
feature: Log Files, Developing
role: Admin, Architect, Developer
source-git-commit: 5c32a088cf7e334ba6497a595b5176e5389ce9ed
workflow-type: ht
source-wordcount: '2556'
ht-degree: 100%

---

# Protokollieren für AEM as a Cloud Service {#logging-for-aem-as-a-cloud-service}

AEM as a Cloud Service ist eine Plattform, auf der Kunden benutzerdefinierten Code einbinden können, um einzigartige Erlebnisse für ihre Kunden zu erstellen. Vor diesem Hintergrund ist der Protokollierungs-Service eine wichtige Funktion, um die Code-Ausführung in lokalen Entwicklungs- und Cloud-Umgebungen, insbesondere den Entwicklungsumgebungen von AEM as a Cloud Service, zu debuggen und zu verstehen.

Die Protokollierung und Protokollierungsebenen in AEM as a Cloud Service werden in Konfigurationsdateien verwaltet, die als Teil des AEM-Projekts in Git gespeichert und als Teil des AEM-Projekts über Cloud Manager bereitgestellt werden. Die Protokollierung in AEM as a Cloud Service kann in drei logische Gruppen unterteilt werden:

* AEM-Protokollierung, die die Protokollierung auf AEM-Programmebene durchführt,
* Apache HTTPD Web Server-/Dispatcher-Protokollierung, die die Protokollierung des Webservers und Dispatchers in der Veröffentlichungsstufe durchführt.
* Die CDN-Protokollierung, die, wie ihr Name besagt, die Protokollierung im CDN durchführt.

## AEM-Protokollierung {#aem-logging}

Die Protokollierung auf der AEM-Programmebene erfolgt über drei Protokolle:

1. AEM-Java-Protokolle, die Java-Protokolleinträge für das AEM-Programm darstellen.
1. HTTP-Anfrageprotokolle, die Informationen zu HTTP-Anfragen und deren von AEM bereitgestellten Antworten protokollieren
1. HTTP-Zugriffsprotokolle, in denen zusammengefasste Informationen und von AEM bereitgestellte HTTP-Anfragen protokolliert werden

>[!NOTE]
>
>HTTP-Anfragen, die aus dem Dispatcher-Cache der Veröffentlichungsstufe oder dem vorgelagerten CDN bedient werden, werden in diesen Protokollen nicht berücksichtigt.

## AEM-Java-Protokollierung {#aem-java-logging}

AEM as a Cloud Service bietet Zugriff auf Java-Protokolleinträge. Entwickler von Programmen für AEM sollten sich an die allgemeinen Best Practices für die Java-Protokollierung halten und relevante Einträge zur Ausführung von benutzerdefiniertem Code auf den folgenden Protokollebenen protokollieren:

<table>
<tr>
<td>
<b>AEM-Umgebung</b></td>
<td>
<b>Protokollebene</b></td>
<td>
<b>Beschreibung</b></td>
<td>
<b>Verfügbarkeit der Protokolleinträge</b></td>
</tr>
<tr>
<td>
Entwicklung</td>
<td>
DEBUG</td>
<td>
Beschreibt, was im Programm geschieht.<br>
Wenn die DEBUG-Protokollierung aktiv ist, werden Einträge protokolliert, die ein klares Bild davon vermitteln, welche Aktivitäten stattfinden, sowie alle Schlüsselparameter, die die Verarbeitung beeinflussen.</td>
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
Wenn die WARN-Protokollierung aktiv ist, werden nur Einträge protokolliert, die auf Zustände hinweisen, die sich einer Suboptimalität nähern.</td>
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
ERROR</td>
<td>
Beschreibt Bedingungen, die auf einen Fehler hinweisen und gelöst werden müssen.<br>
Wenn die ERROR-Protokollierung aktiv ist, werden nur Einträge protokolliert, die auf Fehler hinweisen. ERROR-Protokolleinträge weisen auf ein ernstes Problem hin, das so schnell wie möglich behoben werden sollte.</td>
<td>
<ul>
<li> Lokale Entwicklung</li>
<li>Entwicklung</li>
<li>Staging</li>
<li>Produktion</li>
</ul></td>
</tr>
</table>

Während die Java-Protokollierung mehrere andere Ebenen der Protokollierungsgranularität unterstützt, empfiehlt AEM as a Cloud Service die Verwendung der drei oben beschriebenen Ebenen.

Die AEM-Protokollstufen werden pro Umgebungstyp über die OSGi-Konfiguration festgelegt, die wiederum an Git gebunden sind, und über den Cloud Manager an AEM as a Cloud Service bereitgestellt. Aus diesem Grund ist es am besten, die Protokolleinträge für die Umgebungstypen konsistent und bekannt zu halten, um sicherzustellen, dass die über AEM as Cloud Service verfügbaren Protokolle auf der optimalen Protokollebene verfügbar sind, ohne dass eine Neubereitstellung der Anwendung für eine aktualisierte Protokollebenen-Konfiguration erforderlich ist.

>[!NOTE]
>
>Um eine effektive Überwachung von Kundenumgebungen zu gewährleisten, darf die standardmäßige Protokollebene nicht geändert werden. Auch das standardmäßige Protokollierungsformat darf nicht geändert werden. Die Protokollausgabe muss an die Standarddateien weitergeleitet bleiben. Spezifische Richtlinien finden Sie [im folgenden Abschnitt](#configuration-loggers).

**Beispiel einer Protokollausgabe**

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
<td>AEM as a Cloud Service-Knoten-ID</td>
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
<td>Protokolleintrag</td>
<td>Kein angegebener Genehmigender, standardmäßig [Creative Genehmigende-Benutzergruppe]</td>
</tr>
</tbody>
</table>

### Konfigurations-Logger {#configuration-loggers}

AEM-Java-Protokolle werden als OSGi-Konfiguration definiert und zielen daher mithilfe von Ordnern im Ausführungsmodus auf bestimmte AEM as a Cloud Service-Umgebungen ab.

Konfigurieren Sie die Java-Protokollierung für benutzerdefinierte Java-Pakete über OSGi-Konfigurationen für die Sling LogManager-Factory. Es werden drei Konfigurationseigenschaften unterstützt:

| OSGi-Konfigurationseigenschaft | Beschreibung |
|---|---|
| `org.apache.sling.commons.log.names` | Die Java-Pakete, für die Protokolleinträge gesammelt werden sollen. |
| `org.apache.sling.commons.log.level` | Die Protokollebene, auf der die Java-Pakete protokolliert werden sollen, angegeben durch: `org.apache.sling.commons.log.names` |

Das Ändern anderer LogManager OSGi-Konfigurationseigenschaften kann zu Verfügbarkeitsproblemen in AEM as a Cloud Service führen.

Wie im vorherigen Abschnitt erwähnt, ist Folgendes erforderlich, um eine effektive Überwachung von Kundenumgebungen sicherzustellen:
* Für die Protokollebene der standardmäßigen Protokollkonfiguration für AEM (Apache Sling-Protokollierungskonfiguration) darf der Standardwert „INFO“ nicht geändert werden.
* Es ist akzeptabel, die Protokollebenen für einzelne Pakete von Produkt-Code (unter Verwendung von Instanzen der OSGi-Konfigurations-Factory „Apache Sling Logging Logger Configuration“) auf DEBUG zu setzen. Verwenden Sie diese Einstellung jedoch sparsam, um eine Leistungsbeeinträchtigung zu verhindern, und setzen Sie sie wieder auf „INFO“ zurück, sobald nicht mehr benötigt.
* Es ist akzeptabel, die Protokollebenen für den von der Kundin oder dem Kunden entwickelten Code anzupassen.
* Alle Protokolle müssen das standardmäßige Protokollierungsformat beibehalten. Dies gilt sowohl für den AEM-Produkt-Code als auch für den von der Kundin oder dem Kunden entwickelten Code.
* Die Protokollausgabe muss an die Standarddatei „logs/error.log“ weitergeleitet bleiben. 

Zu diesem Zweck dürfen keine Änderungen an den folgenden OSGi-Eigenschaften vorgenommen werden:
* **Apache Sling Log Configuration** (PID: `org.apache.sling.commons.log.LogManager`) – *alle Eigenschaften*
* **Apache Sling Logging Logger Configuration** (werksseitige PID: `org.apache.sling.commons.log.LogManager.factory.config`):
   * `org.apache.sling.commons.log.file`
   * `org.apache.sling.commons.log.pattern`

Im Folgenden finden Sie Beispiele für die empfohlenen Protokollierungskonfigurationen (unter Verwendung des Platzhalter-Java-Pakets `com.example`) für die drei Umgebungstypen von AEM as a Cloud Service.

### Entwicklung {#development}

/apps/my-app/config/org.apache.sling.commons.log.LogManager.factory.config-example.cfg.json

```
{
    "org.apache.sling.commons.log.names": ["com.example"],
    "org.apache.sling.commons.log.level": "debug"
    "org.apache.sling.commons.log.file": "logs/error.log"
}
```

### Staging {#stage}

/apps/my-app/config.stage/org.apache.sling.commons.log.LogManager.factory.config-example.cfg.json

```
{
    "org.apache.sling.commons.log.names": ["com.example"],
    "org.apache.sling.commons.log.level": "warn"
    "org.apache.sling.commons.log.file": "logs/error.log"
}
```

### Produktion {#productiomn}

/apps/my-app/config.prod/org.apache.sling.commons.log.LogManager.factory.config-example.cfg.json

```
{
    "org.apache.sling.commons.log.names": ["com.example"],
    "org.apache.sling.commons.log.level": "error"
    "org.apache.sling.commons.log.file": "logs/error.log"
}
```

## AEM-Protokollierung von HTTP-Anfragen {#aem-http-request-logging}

Die HTTP-Anfrageprotokollierung von AEM as a Cloud Service bietet Einblick in die an AEM gesendeten HTTP-Anfragen und deren HTTP-Antworten in zeitlicher Reihenfolge. Dieses Protokoll ist hilfreich, um die HTTP-Anfragen an AEM und die Reihenfolge zu verstehen, in der sie verarbeitet und beantwortet werden.

Der Schlüssel zum Verständnis dieses Protokolls liegt in der Zuordnung der HTTP-Anfrage- und Antwortpaare anhand ihrer Kennungen, die durch den numerischen Wert in den Klammern angegeben werden. Oft werden zwischen Anfragen und den entsprechenden Antworten andere HTTP-Anfragen und Antworten in das Protokoll eingefügt.

**Beispielprotokoll**

```
29/Apr/2020:19:14:21 +0000 [137] > POST /conf/global/settings/dam/adminui-extension/metadataprofile/ HTTP/1.1 [cm-p1234-e5678-aem-author-59555cb5b8-q7l9s]
...
29/Apr/2020:19:14:22 +0000 [139] > GET /mnt/overlay/dam/gui/content/processingprofilepage/metadataprofiles/editor.html/conf/global/settings/dam/adminui-extension/metadataprofile/main HTTP/1.1 [cm-p1234-e5678-aem-author-59555cb5b8-q7l9s]
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
<td>29. April 2020:19:14:21 +0000</td>
</tr>
<tr>
<td>Kennung des Anfrage-/Antwortpaares</td>
<td><code>[137]</code></td>
</tr>
<tr>
<td>HTTP-Methode</td>
<td>POST</td>
</tr>
<tr>
<td>URL</td>
<td>/conf/global/settings/dam/adminui-extension/metadataprofile/</td>
</tr>
<tr>
<td>Protokoll</td>
<td>HTTP/1.1
</td>
</tr>
<tr>
<td>AEM as a Cloud Service-Knoten-ID</td>
<td>[cm-p1234-e5678-aem-author-59555cb5b8-q7l9s]</td>
</tr>
</tbody>
</table>

### Konfigurieren des Protokolls {#configuring-the-log}

Das AEM-Protokoll für HTTP-Anfragen kann in AEM as a Cloud Service nicht konfiguriert werden.

## AEM-Protokollierung von HTTP-Zugriffen {#aem-http-access-logging}

Die Protokollierung von HTTP-Zugriffen in AEM as a Cloud Service zeigt HTTP-Anfragen in zeitlicher Reihenfolge an. Jeder Protokolleintrag stellt die HTTP-Anfrage dar, die auf AEM zugreift.

Dieses Protokoll ist hilfreich, um schnell zu verstehen, welche HTTP-Anfragen an AEM gesendet werden, ob sie erfolgreich sind, indem man sich den zugehörigen Status-Code der HTTP-Antwort ansieht, und wie lange es dauerte, bis die HTTP-Anfrage abgeschlossen war. Dieses Protokoll kann auch hilfreich sein, um die Aktivität eines bestimmten Benutzers zu debuggen, indem die Protokolleinträge nach Benutzern gefiltert werden.

**Beispiel einer Protokollausgabe**

```
cm-p1234-e26813-aem-author-59555cb5b8-8kgr2 - example@adobe.com 30/Apr/2020:17:37:14 +0000  "GET /libs/granite/ui/references/clientlibs/references.lc-5188e85840c529149e6cd29d94e74ad5-lc.min.css HTTP/1.1" 200 1141 "https://author-p10711-e26813.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/en/images/example.jpeg&_charset_=utf8" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.122 Safari/537.36"
cm-p1234-e26813-aem-author-59555cb5b8-8kgr2 - example@adobe.com 30/Apr/2020:17:37:14 +0000  "GET /libs/dam/gui/coral/components/admin/customthumb/clientlibs.lc-60e4443805c37afa0c74b674b141f1df-lc.min.css HTTP/1.1" 200 809 "https://author-p10711-e26813.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/en/images/example.jpeg&_charset_=utf8" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.122 Safari/537.36"
cm-p1234-e26813-aem-author-59555cb5b8-8kgr2 - example@adobe.com 30/Apr/2020:17:37:14 +0000  "GET /libs/dam/gui/coral/components/admin/metadataeditor/clientlibs/metadataeditor.lc-4a2226d8232f8b7ab27d24820b9ddd64-lc.min.js HTTP/1.1" 200 7965 "https://author-p10711-e26813.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/en/images/example.jpeg&_charset_=utf8" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.122 Safari/537.36"
```

| AEM as a Cloud Service-Knoten-ID | cm-p1235-e2644-aem-author-59555cb5b8-8kgr2 |
|---|---|
| IP-Adresse des Clients | – |
| User | myuser@adobe.com |
| Datum und Uhrzeit | &#x200B;30. April 2020:17:37:14 +0000 |
| HTTP-Methode | GET |
| URL | `/libs/granite/ui/references/clientlibs/references.lc-5188e85840c529149e6cd29d94e74ad5-lc.min.css` |
| Protokoll | HTTP/1.1 |
| HTTP-Antwortstatus | 200 |
| Größe des Antworttextes in Byte | 1141 |
| Referrer | `"https://author-p1234-e4444.adobeaemcloud.com/mnt/overlay/dam/gui/content/assets/metadataeditor.external.html?item=/content/dam/wknd/en/adventures/surf-camp-in-costa-rica/adobestock_266405335.jpeg&_charset_=utf8"` |
| Benutzeragent | `"Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.122 Safari/537.36"` |

### Konfigurieren des HTTP-Zugriffsprotokolls {#configuring-the-http-access-log}

Das HTTP-Zugriffsprotokoll kann in AEM as a Cloud Service nicht konfiguriert werden.

## Apache Web Server- und Dispatcher-Protokollierung {#apache-web-server-and-dispatcher-logging}

AEM as a Cloud Service stellt drei Protokolle für die Apache-Webserver- und Dispatcher-Schicht der Veröffentlichungsebene bereit:

* Apache HTTPD Web Server-Zugriffsprotokoll
* Apache HTTPD Web Server-Fehlerprotokoll
* Dispatcher-Protokoll

Diese Protokolle sind nur für die Veröffentlichungsebene verfügbar.

Dieser Satz an Protokollen bietet Einblicke in HTTP-Anfragen an die Veröffentlichungsstufe von AEM as a Cloud Service, bevor diese Anfragen das AEM-Programm erreichen. Dies ist wichtig, da im Idealfall die meisten HTTP-Anfragen an die Server der Veröffentlichungsstufe von Inhalten bereitgestellt werden, die von Apache HTTPD Web Server und AEM Dispatcher zwischengespeichert werden und niemals das AEM-Programm selbst erreichen. Daher gibt es keine Protokolleinträge für diese Anfragen in Java-, Anfrage- oder Zugriffsprotokollen in AEM.

### Apache HTTPD Web Server-Zugriffsprotokoll {#apache-httpd-web-server-access-log}

Das Apache HTTP Web Server-Zugriffsprotokoll enthält Einträge für jede HTTP-Anfrage, die den Webserver/Dispatcher der Veröffentlichungsstufe erreicht. Anfragen, die von einem vorgelagerten CDN bereitgestellt werden, sind in diesen Protokollen nicht enthalten.

Informationen zum Fehlerprotokollformat finden Sie in der [offiziellen Dokumentation von Apache](https://httpd.apache.org/docs/2.4/logs.html#accesslog).

**Beispiel einer Protokollausgabe**

```
cm-p1234-e5678-aem-publish-b86c6b466-qpfvp - - 17/Jul/2020:09:14:41 +0000  "GET /etc.clientlibs/wknd/clientlibs/clientlib-site/resources/images/favicons/favicon-32.png HTTP/1.1" 200 715 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:78.0) Gecko/20100101 Firefox/78.0"
cm-p1234-e5678-aem-publish-b86c6b466-qpfvp - - 17/Jul/2020:09:14:41 +0000  "GET /etc.clientlibs/wknd/clientlibs/clientlib-site/resources/images/favicons/favicon-512.png HTTP/1.1" 200 9631 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:78.0) Gecko/20100101 Firefox/78.0"
cm-p1234-e5678-aem-publish-b86c6b466-qpfvp - - 17/Jul/2020:09:14:42 +0000  "GET /etc.clientlibs/wknd/clientlibs/clientlib-site/resources/images/country-flags/US.svg HTTP/1.1" 200 810 "https://publish-p6902-e30226.adobeaemcloud.com/content/wknd/us/en.html" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:78.0) Gecko/20100101 Firefox/78.0"
```

**Protokollformat**

<table>
<tbody>
<tr>
<td>AEM as a Cloud Service-Knoten-ID</td>
<td>cm-p1234-e26813-aem-publish-5c787687c-lqlxr</td>
</tr>
<tr>
<td>IP-Adresse des Clients</td>
<td>–</td>
</tr>
<tr>
<td>User</td>
<td>–</td>
</tr>
<tr>
<td>Datum und Uhrzeit</td>
<td>01. Mai 2020:00:09:46 +0000</td>
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
<td>–</td>
</tr>
<tr>
<td>Benutzeragent</td>
<td>„Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, wie Gecko) Chrome/81.0.4044.122 Safari/537.36“</td>
</tr>
</tbody>
</table>

### Konfigurieren des Apache HTTPD Web Server-Zugriffsprotokolls {#configuring-the-apache-httpd-webs-server-access-log}

Dieses Protokoll kann in AEM as a Cloud Service nicht konfiguriert werden.

## Apache HTTPD Web Server-Fehlerprotokoll {#apache-httpd-web-server-error-log}

Das Apache HTTP Web Server-Fehlerprotokoll enthält Einträge für jeden Fehler im Webserver/Dispatcher der Veröffentlichungsstufe.

Informationen zum Fehlerprotokollformat finden Sie in der [offiziellen Dokumentation von Apache](https://httpd.apache.org/docs/2.4/logs.html#errorlog).

**Beispiel einer Protokollausgabe**

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
<td>Freitag, 17. Juli 02:16:42.608913 2020</td>
</tr>
<tr>
<td>Ereignisebene</td>
<td>[mpm_worker:notice]</td>
</tr>
<tr>
<td>Prozess-ID</td>
<td>[pid 1:tid 140715149343624]</td>
</tr>
<tr>
<td>Pod-Name</td>
<td>[cm-p1234-e56789-aem-publish-b86c6b466-qpfvp]</td>
</tr>
<tr>
<td>Meldung</td>
<td>AH00094: Befehlszeile: 'httpd -d /etc/httpd -f /etc/httpd/conf/httpd.conf -D FOREGROUND -D </td>
</tr>
</tbody>
</table>

### Konfigurieren des Apache HTTPD Web Server-Fehlerprotokolls {#configuring-the-apache-httpd-web-server-error-log}

Die Protokollierungsebenen „mod_rewrite“ werden durch die Variable „REWRITE_LOG_LEVEL“ in der Datei `conf.d/variables/global.var` definiert.

Sie kann auf „Error“, „Warn“, „Info“, „Debug“ und „Trace1“ bis „Trace8“ eingestellt werden, wobei der Standardwert „Warn“ ist. Zum Debuggen Ihrer Neuschreibungsregeln wird empfohlen, die Protokollebene auf „Trace2“ zu erhöhen. Es wird empfohlen, Neuschreibungsregeln mit dem [Dispatcher SDK](../../dispatcher/validation-debug.md) zu debuggen. Die maximale Protokollebene für AEM as a Cloud Service ist `debug`. Daher ist es derzeit nicht effektiv möglich, Neuschreibungsregeln in der Cloud zu debuggen.

Weitere Informationen finden Sie in der [Dokumentation zum mod_rewrite-Modul](https://httpd.apache.org/docs/current/mod/mod_rewrite.html#logging).

Verwenden Sie zum Festlegen der Protokollstufe pro Umgebung den entsprechenden bedingten Zweig in der Datei „global.var“, wie unten beschrieben:

```
Define REWRITE_LOG_LEVEL debug

<IfDefine ENVIRONMENT_STAGE>
  ...
  Define REWRITE_LOG_LEVEL warn
  ...
</IfDefine>
<IfDefine ENVIRONMENT_PROD>
  ...
  Define REWRITE_LOG_LEVEL error
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
<td>[17. Juli 2020:23:48:16 +0000]</td>
</tr>
<tr>
<td>Pod-Name</td>
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
<td>Status-Code der Dispatcher-Antwort</td>
<td>/content/experience-fragments/wknd/language-masters/en/contributors/sofia-sjoeberg/master/_jcr_content/root/responsivegrid/image.coreimg.100.500.jpeg/1572236359031/ayo-ogunseinde-237739.jpeg</td>
</tr>
<tr>
<td>Dauer</td>
<td>1949ms</td>
</tr>
<tr>
<td>Farm</td>
<td>[publishfarm/0]</td>
</tr>
<tr>
<td>Cache-Status</td>
<td>[action miss]</td>
</tr>
<tr>
<td>Host</td>
<td>"publish-p12904-e25628.adobeaemcloud.com"</td>
</tr>
</tbody>
</table>

### Konfigurieren des Dispatcher-Fehlerprotokolls {#configuring-the-dispatcher-error-log}

Die Dispatcher-Protokollebenen werden durch die Variable „DISP_LOG_LEVEL“ in der Datei `conf.d/variables/global.var` definiert.

Sie kann auf „Error“, „Warn“, „Info“, „Debug“ und „Trace1“ eingestellt werden, wobei der Standardwert „Warn“ ist.

Während die Dispatcher-Protokollierung mehrere andere Ebenen der Protokollierungsgranularität unterstützt, empfiehlt AEM as a Cloud Service die Verwendung der unten beschriebenen Ebenen.

Verwenden Sie zum Festlegen der Protokollstufe pro Umgebung den entsprechenden bedingten Zweig in der Datei `global.var`, wie unten beschrieben:

```
Define DISP_LOG_LEVEL debug

<IfDefine ENVIRONMENT_STAGE>
  ...
  Define DISP_LOG_LEVEL warn
  ...
</IfDefine>
<IfDefine ENVIRONMENT_PROD>
  ...
  Define DISP_LOG_LEVEL error
  ...
</IfDefine>
```

>[!NOTE]
>
>Bei AEM as a Cloud Service-Umgebungen ist „debug“ die maximale Ausführlichkeitsstufe. Die Trace-Protokollebene wird nicht unterstützt. Daher sollten Sie beim Arbeiten in Cloud-Umgebungen vermeiden, sie festzulegen.

## CDN-Protokoll {#cdn-log}

AEM as a Cloud Service bietet Zugriff auf CDN-Protokolle, die für Anwendungsfälle nützlich sind, einschließlich der Optimierung der Cache-Trefferquote. Das CDN-Protokollformat kann nicht angepasst werden und es gibt kein Konzept, um es auf verschiedene Modi wie Info, Warnung oder Fehler festzulegen.

**Beispiel**

```
{
"timestamp": "2023-05-26T09:20:01+0000",
"ttfb": 19,
"cli_ip": "147.160.230.112",
"cli_country": "CH",
"rid": "974e67f6",
"req_ua": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/14.0.3 Safari/605.1.15",
"host": "example.com",
"url": "/content/hello.png",
"method": "GET",
"res_ctype": "image/png",
"cache": "PASS",
"status": 200,
"res_age": 0,
"pop": "PAR",
"rules": "match=Enable-SQL-Injection-and-XSS-waf-rules-globally,waf=SQLI,action=blocked"
}
```

**Protokollformat**

Die CDN-Protokolle unterscheiden sich von den anderen Protokollen insofern, als sie einem JSON-Format entsprechen.

| **Feldname** | **Beschreibung** |
|---|---|
| *timestamp* | Der Zeitpunkt, zu dem die Anfrage nach der TLS-Beendigung gestartet wurde |
| *ttfb* | Abkürzung für *Time To First Byte*. Das Zeitintervall vom Start der Anfrage bis zu dem Punkt, an dem das Streamen des Antworttexts begann. |
| *cli_ip* | Die Client-IP-Adresse. |
| *cli_country* | Der Alpha-2-Ländercode gemäß [ISO 3166-1](https://de.wikipedia.org/wiki/ISO_3166-1) mit zwei Buchstaben für das Client-Land. |
| *rid* | Der Wert der Anfragekopfzeile, der zur eindeutigen Identifizierung der Anfrage verwendet wird. |
| *req_ua* | Der Benutzeragent, der für die Ausführung einer bestimmten HTTP-Anfrage verantwortlich ist. |
| *host* | Die Stelle, für die die Anfrage bestimmt ist. |
| *url* | Der vollständige Pfad, einschließlich Abfrageparametern. |
| *Methode* | Die vom Client gesendete HTTP-Methode, z. B. „GET“ oder „POST“. |
| *res_ctype* | Der Content-Typ, der den ursprünglichen Medientyp der Ressource angibt. |
| *cache* | Der Status des Caches. Mögliche Werte sind HIT, MISS oder PASS |
| *status* | Der HTTP-Status-Code als ganzzahliger Wert. |
| *res_age* | Die Zeit in Sekunden, für die eine Antwort zwischengespeichert wurde (in allen Knoten). |
| *pop* | das Rechenzentrum des CDN-Cache-Servers. |
| *rules* | Die Namen aller übereinstimmenden [Traffic-Filterregeln](/help/security/traffic-filter-rules-including-waf.md) und WAF-Flags, die auch angeben, ob die Übereinstimmung zu einer Blockierung führte. Leer, wenn keine Regeln übereinstimmten. |

Die CDN-Protokolle können mit Ihren eigenen Eigenschaften mithilfe von [Anfrage-/Antworttransformationen](/help/implementing/dispatcher/cdn-configuring-traffic.md#logproperty) erweitert werden.

## Zugriff auf Protokolle {#how-to-access-logs}

### Cloud-Umgebungen {#cloud-environments}

Auf die Protokolle in AEM as a Cloud Service für Cloud-Services kann entweder durch Herunterladen über die Cloud Manager-Oberfläche oder durch Nachverfolgung der Protokolle über die Befehlszeile mithilfe der Adobe I/O-Befehlszeilenschnittstelle zugegriffen werden. Weitere Informationen finden Sie in der [Dokumentation zur Cloud Manager-Protokollierung](/help/implementing/cloud-manager/manage-logs.md).

### Protokolle für zusätzliche Veröffentlichungsregionen {#logs-for-additional-publish-regions}

Wenn für eine bestimmte Umgebung zusätzliche Veröffentlichungsregionen aktiviert sind, können, wie oben erwähnt, Protokolle für jede Region von Cloud Manager heruntergeladen werden.

Die AEM-Protokolle und die Dispatcher-Protokolle für die zusätzlichen Veröffentlichungsregionen geben die Region in den ersten drei Buchstaben nach der Umgebungs-ID an, wie dies in Form von **nld2** im folgenden Beispiel dargestellt ist, das sich auf eine zusätzliche AEM-Veröffentlichungsinstanz in den Niederlanden bezieht:

```
cm-p7613-e12700-nld2-aem-publish-bcbb77549-5qmmt 127.0.0.1 - 07/Nov/2023:23:57:11 +0000 "HEAD /libs/granite/security/currentuser.json HTTP/1.1" 200 - "-" "Java/11.0.19"
```

### Lokales SDK {#local-sdk}

Das AEM as a Cloud Service SDK stellt Protokolldateien zur Unterstützung der lokalen Entwicklung bereit.

AEM-Protokolle befinden sich im Ordner `crx-quickstart/logs`, in dem die folgenden Protokolle eingesehen werden können:

* AEM-Java-Protokoll: `error.log`
* AEM-Protokollierung von HTTP-Anfragen: `request.log`
* AEM-Protokollierung von HTTP-Zugriffen: `access.log`

Apache-Ebenenprotokolle, einschließlich Dispatcher, befinden sich im Docker-Container, in dem sich der Dispatcher befindet. Informationen zum Starten des Dispatchers finden Sie in der [Dispatcher-Dokumentation](/help/implementing/dispatcher/disp-overview.md).

Abrufen der Protokolle:

1. Geben Sie in der Befehlszeile `docker ps` ein, um Ihre Container aufzulisten
1. Geben Sie „`docker exec -it <container> /bin/sh`“ ein, um sich beim Container anzumelden, wobei `<container>` die Dispatcher-Container-ID aus dem vorherigen Schritt ist
1. Navigieren Sie zum Cache-Stammverzeichnis unter `/mnt/var/www/html`
1. Die Protokolle befinden sich unter `/etc/httpd/logs`
1. Überprüfen Sie die Protokolle: Sie sind im Ordner „XYZ“ zugänglich, wo die folgenden Protokolle eingesehen werden können:
   * Apache HTTPD Web Server-Zugriffsprotokoll – `httpd_access.log`
   * Apache HTTPD Web Server-Fehlerprotokoll – `httpd_error.log`
   * Dispatcher-Protokolle – `dispatcher.log`

Die Protokolle werden auch direkt an die Terminalausgabe gedruckt. Meistens sollten diese Protokolle DEBUG sein, was bei Ausführung von Docker durch Übergabe in der Debug-Ebene als Parameter erreicht werden kann. Zum Beispiel:

`DISP_LOG_LEVEL=Debug ./bin/docker_run.sh out docker.for.mac.localhost:4503 8080`

## Debuggen von Produktions- und Staging-Umgebung {#debugging-production-and-stage}

In Ausnahmefällen müssen die Protokollebenen geändert werden, um in Staging- oder Produktionsumgebungen mit einer feineren Granularität zu protokollieren.

Dies ist zwar möglich, erfordert jedoch Änderungen der Protokollebenen in den Konfigurationsdateien in Git von „Warn“ und „Error“ auf „Debug“ sowie eine Bereitstellung von AEM as a Cloud Service, um diese Konfigurationsänderungen in den Umgebungen zu registrieren.

Je nach Traffic und der Menge der von Debug geschriebenen Protokolleinträge kann dies zu Leistungsbeeinträchtigungen in der Umgebung führen. Daher wird empfohlen, Änderungen an den Debug-Ebenen für Staging- und Produktionsumgebungen wie folgt vorzunehmen:

* Mit Bedacht und nur dann, wenn dies unbedingt erforderlich ist
* Auf die entsprechenden Ebenen zurückgesetzt und so schnell wie möglich erneut bereitgestellt

## Protokollweiterleitung {#log-forwarding}

Die Protokolle können zwar von Cloud Manager heruntergeladen werden, aber einige Unternehmen ziehen es vor, diese Protokolle an ein bevorzugtes Protokollierungsziel weiterzuleiten. AEM unterstützt das Streamen von Protokollen an die folgenden Ziele:

* Azure Blob Storage
* Datadog
* HTTPD
* Elasticsearch (und OpenSearch)
* Splunk

Weitere Informationen zur Konfiguration dieser Funktion finden Sie im [Artikel zur Protokollweiterleitung](/help/implementing/developing/introduction/log-forwarding.md).

>[!NOTE]
>
>Die Protokollweiterleitung für Sandbox-Programmumgebungen wird nicht unterstützt.
