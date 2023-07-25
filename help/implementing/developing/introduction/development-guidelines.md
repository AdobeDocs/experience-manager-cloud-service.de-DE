---
title: Entwicklungsrichtlinien für AEM as a Cloud Service
description: Lernen Sie die Richtlinien für die Entwicklung mit AEM as a Cloud Service kennen und erfahren Sie, worin sich dieser Dienst von AEM vor Ort und AEM in AMS unterscheidet.
exl-id: 94cfdafb-5795-4e6a-8fd6-f36517b27364
source-git-commit: f69b348b7de6c6537a9945793e3397bf4fe30f98
workflow-type: tm+mt
source-wordcount: '2655'
ht-degree: 86%

---

# Entwicklungsrichtlinien für AEM as a Cloud Service {#aem-as-a-cloud-service-development-guidelines}

>[!CONTEXTUALHELP]
>id="development_guidelines"
>title="Entwicklungsrichtlinien für AEM as a Cloud Service"
>abstract="Lernen Sie die Richtlinien für die Entwicklung mit AEM as a Cloud Service kennen und erfahren Sie, worin sich dieser Dienst von AEM vor Ort und AEM in AMS unterscheidet."
>additional-url="https://video.tv.adobe.com/v/330555/?captions=ger" text="Demo zur Paketstruktur"

Dieses Dokument enthält Richtlinien für die Entwicklung von AEM as a Cloud Service und wichtige Unterschiede zu AEM vor Ort und AEM in AMS.

## Code muss Cluster-fähig sein {#cluster-aware}

Code, der in AEM as a Cloud Service ausgeführt wird, muss wissen, dass er immer in einem Cluster ausgeführt wird. Das bedeutet, dass immer mehr als eine Instanz ausgeführt wird. Der Code muss robust sein, insbesondere da eine Instanz jederzeit gestoppt werden kann.

Während der Aktualisierung AEM as a Cloud Service gibt es Instanzen mit altem und neuem Code, die parallel ausgeführt werden. Daher darf der alte Code nicht mit dem durch den neuen Code erzeugten Inhalt abstürzen, und der neue Code muss mit dem alten Inhalt umgehen können.

Wenn die Primärinstanz im Cluster identifiziert werden muss, kann die Apache Sling Discovery-API verwendet werden, um sie zu erkennen.

## Status im Speicher {#state-in-memory}

Der Status darf nicht im Speicher gehalten werden, sondern muss im Repository verbleiben. Andernfalls geht dieser Status möglicherweise verloren, wenn eine Instanz beendet wird.

## Status im Dateisystem {#state-on-the-filesystem}

Das Dateisystem der Instanz sollte in AEM as a Cloud Service verwendet werden. Der Datenträger ist temporär und wird bei der Wiederverwertung der Instanzen entsorgt. Eine beschränkte Nutzung des Dateisystems für die temporäre Datenspeicherung im Zusammenhang mit der Verarbeitung einzelner Anfragen ist möglich, sollte aber nicht für riesige Dateien missbraucht werden. Dies liegt daran, dass sich dies negativ auf das Ressourcennutzungskontingent auswirken und zu Datenträgerbeschränkungen führen kann.

Wenn beispielsweise die Nutzung des Dateisystems nicht unterstützt wird, sollte die Veröffentlichungsebene sicherstellen, dass alle Daten, die beibehalten werden müssen, zur längeren Datenspeicherung an einen externen Service gesendet werden.

## Beobachrung {#observation}

In ähnlicher Weise kann nicht garantiert werden, dass alles, was asynchron geschieht, wie z. B. die Reaktion auf Beobachtungsereignisse, lokal ausgeführt wird. Daher sollte man bei der Verwendung vorsichtig sein. Dies gilt sowohl für JCR-Ereignisse als auch für Sling-Ressourcen-Ereignisse. Zum Zeitpunkt einer Änderung kann die Instanz heruntergefahren und durch eine andere Instanz ersetzt werden. Andere zu diesem Zeitpunkt aktive Instanzen in der Topologie können auf dieses Ereignis reagieren. In diesem Fall handelt es sich jedoch nicht um ein lokales Ereignis und es kann sogar sein, dass es bei einer zum Zeitpunkt der Veranlassung des Ereignisses laufenden Auswahl der führenden Instanz keine aktive führende Instanz gibt.

## Hintergrundaufgaben und Aufträge mit langer Laufzeit {#background-tasks-and-long-running-jobs}

Als Hintergrundaufgaben ausgeführter Code muss davon ausgehen, dass die Instanz, in der er ausgeführt wird, jederzeit heruntergefahren werden kann. Daher muss der Code stabil und vor allem verwendbar sein. Das bedeutet, dass der Code, wenn er erneut ausgeführt wird, nicht von vorne beginnen sollte, sondern eher nahe an der Stelle, an der er abgebrochen wurde. Dies ist zwar keine neue Anforderung für diese Art von Code, aber bei AEM as a Cloud Service ist es wahrscheinlicher, dass eine Instanz heruntergefahren wird.

Um die Probleme zu minimieren, sollten Aufträge mit langer Laufzeit nach Möglichkeit vermieden und zumindest wieder aufgenommen werden können. Verwenden Sie für die Ausführung solcher Aufträge Sling-Aufträge, die eine Garantie für mindestens einmaliges Ausführen haben und daher, falls sie unterbrochen werden, so schnell wie möglich wieder ausgeführt werden. Aber sie sollten wahrscheinlich nicht wieder von vorne anfangen. Für die Planung solcher Aufträge ist es am besten, die Planung von [Sling-Aufträgen](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#jobs-guarantee-of-processing) zu verwenden, da dies wiederum die mindestens einmalige Ausführung garantiert.

Der Sling Commons Scheduler sollte nicht für die Planung verwendet werden, da die Ausführung nicht garantiert werden kann. Es ist nur wahrscheinlicher, dass sie geplant wird.

In ähnlicher Weise kann nicht garantiert werden, dass alles, was asynchron geschieht, wie z. B. die Reaktion auf Beobachtungsereignisse (JCR-Ereignisse oder Sling-Ressourcenereignisse), ausgeführt wird. Daher sollte man bei der Verwendung vorsichtig sein. Dies gilt bereits jetzt für AEM-Bereitstellungen.

## Ausgehende HTTP-Verbindungen {#outgoing-http-connections}

Es wird dringend empfohlen, dass alle ausgehenden HTTP-Verbindungen angemessene Verbindungs- und Lesezeitüberschreitungen festlegen. Die vorgeschlagenen Werte sind 1 Sekunde für die Verbindungszeitüberschreitung und 5 Sekunden für die Lesezeitüberschreitung. Die genauen Werte müssen anhand der Leistung des Backend-Systems bestimmt werden, das diese Anfragen verarbeitet.

Für Code, der diese Zeitlimits nicht anwendet, erzwingen AEM-Instanzen, die in AEM as a Cloud Service ausgeführt werden, globale Zeitlimits. Diese Zeitüberschreitungswerte betragen 10 Sekunden für Verbindungsaufrufe und 60 Sekunden für Leseaufrufe für Verbindungen.

Adobe empfiehlt zum Herstellen von HTTP-Verbindungen die Verwendung der bereitgestellten [Apache HttpComponents Client 4.x-Bibliothek](https://hc.apache.org/httpcomponents-client-ga/).

Alternativen, von denen bekannt ist, dass sie funktionieren, für die Sie jedoch möglicherweise die Abhängigkeiten selbst bereitstellen müssen, sind:

* [java.net.URL](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/net/URL.html) und/oder [java.net.URLConnection](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/net/URLConnection.html) (bereitgestellt von AEM)
* [Apache Commons HttpClient 3.x](https://hc.apache.org/httpclient-3.x/) (nicht empfohlen, da veraltet und durch Version 4.x ersetzt)
* [OK HTTP](https://square.github.io/okhttp/) (nicht von AEM bereitgestellt)

Neben der Bereitstellung von Timeouts sollte auch eine ordnungsgemäße Verarbeitung solcher Timeouts und unerwartete HTTP-Status-Codes implementiert werden.

## Umgang mit Anforderungsratenbeschränkungen {#rate-limit-handling}

>[!NOTE]
>Die HTTP-Fehlerantwort ändert sich in der Woche vom 7. August 2023 von 503 auf 429.
>
Wenn die Rate eingehender Anfragen an AEM gesunde Ebenen überschreitet, antwortet AEM auf neue Anfragen mit dem HTTP-Fehlercode 429. Anwendungen, die programmatische Aufrufe an AEM durchführen, können eine defensive Programmierung in Erwägung ziehen und es nach einigen Sekunden mit einer exponentiellen Backoff-Strategie erneut versuchen. Vor Mitte August 2023 reagierte AEM auf dieselbe Bedingung mit dem HTTP-Fehlercode 503.

## Keine Anpassungen der klassischen Benutzeroberfläche {#no-classic-ui-customizations}

AEM as a Cloud Service unterstützt nur die Touch-Benutzeroberfläche für Kundencode von Drittanbietern. Die klassische Benutzeroberfläche kann nicht angepasst werden.

## Keine nativen Binärdateien oder native Bibliotheken {#avoid-native-binaries}

Native Binärdateien und Bibliotheken dürfen nicht in Cloud-Umgebungen bereitgestellt oder installiert werden.

Darüber hinaus sollte der Code nicht versuchen, native Binärdateien oder native Java-Erweiterungen (z. B. JNI) zur Laufzeit herunterzuladen.

## Keine Streaming-Binärdateien über AEM as a Cloud Service {#no-streaming-binaries}

Auf Binärdateien sollte über das CDN zugegriffen werden, das Binärdateien außerhalb der AEM-Kern-Services bereitstellt.

Verwenden Sie zum Beispiel nicht `asset.getOriginal().getStream()`, wodurch das Herunterladen einer Binärdatei auf den temporären Datenträger des AEM-Service ausgelöst wird.

## Keine Rückwärtsreplikations-Agenten {#no-reverse-replication-agents}

Die Rückwärtsreplikation von der Veröffentlichungs- auf die Autoreninstanz wird in AEM as a Cloud Service nicht unterstützt. Wenn eine solche Strategie erforderlich ist, können Sie einen externen Persistenzspeicher verwenden, der von der Farm der Veröffentlichungsinstanzen und möglicherweise vom Autoren-Cluster gemeinsam genutzt wird.

## Vorwärtsreplikationsagenten müssen möglicherweise portiert werden {#forward-replication-agents}

Inhalte werden über einen Herausgeber-Abonnenten-Mechanismus von der Autoren- auf die Veröffentlichungsinstanz repliziert. Benutzerdefinierte Replikationsagenten werden nicht unterstützt.

## Überwachung und Debugging {#monitoring-and-debugging}

### Protokolle {#logs}

Für die lokale Entwicklung werden Protokolleinträge in lokale Dateien im Ordner `/crx-quickstart/logs` geschrieben.

In Cloud-Umgebungen können Entwickler Protokolle über Cloud Manager herunterladen oder ein Befehlszeilen-Tool verwenden, um die Protokolle zu verfolgen. <!-- See the [Cloud Manager documentation](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html) for more details. Note that custom logs are not supported and so all logs should be output to the error log. -->

**Festlegen der Protokollebene**

Um die Protokollierungsstufen für Cloud-Umgebungen zu ändern, sollte die OSGi-Konfiguration für die Sling-Protokollierung geändert und anschließend vollständig neu bereitgestellt werden. Da dies nicht sofort geschieht, sollten Sie vorsichtig sein, ausführliche Protokolle zu Produktionsumgebungen zu aktivieren, die viel Traffic erhalten. In Zukunft ist es möglich, dass es Mechanismen gibt, um die Protokollebene schneller zu ändern.

>[!NOTE]
>
>Um die unten aufgeführten Konfigurationsänderungen durchzuführen, erstellen Sie sie in einer lokalen Entwicklungsumgebung und übertragen sie dann auf eine AEM as a Cloud Service Instanz. Weitere Informationen dazu finden Sie unter [Bereitstellen in AEM as a Cloud Service](/help/implementing/deploying/overview.md).

**Aktivieren der DEBUG-Protokollebene**

Die standardmäßige Protokollebene ist INFO, DEBUG-Meldungen werden also nicht protokolliert. Um die DEBUG-Protokollebene zu aktivieren, ändern Sie die folgende Eigenschaft in den Debugging-Modus.

`/libs/sling/config/org.apache.sling.commons.log.LogManager/org.apache.sling.commons.log.level`

Legen Sie beispielsweise `/apps/<example>/config/org.apache.sling.commons.log.LogManager.factory.config~<example>.cfg.json` auf den folgenden Wert fest.

```json
{
   "org.apache.sling.commons.log.names": [
      "com.example"
   ],
   "org.apache.sling.commons.log.level": "DEBUG",
   "org.apache.sling.commons.log.file": "logs/error.log",
   "org.apache.sling.commons.log.additiv": "false"
}
```

Lassen Sie die DEBUG-Protokollebene nicht länger als notwendig aktiviert, da hierdurch zahlreiche Protokolleinträge generiert werden.

Mithilfe des OSGi-Konfigurations-Targetings im Ausführungsmodus können diskrete Protokollebenen für die verschiedenen AEM-Umgebungen festgelegt werden, wenn es wünschenswert ist, während der Entwicklung immer bei `DEBUG` zu protokollieren. Beispiel:

| Umgebung | Speicherort der OSGi-Konfiguration nach Ausführungsmodus | `org.apache.sling.commons.log.level` Eigenschaftswert |
| - | - | - |
| Entwicklung | /apps/example/config/org.apache.sling.commons.log.LogManager.factory.config~example.cfg.json | DEBUG |
| Staging | /apps/example/config.stage/org.apache.sling.commons.log.LogManager.factory.config~example.cfg.json | WARN |
| Produktion | /apps/example/config.prod/org.apache.sling.commons.log.LogManager.factory.config~example.cfg.json | ERROR |

Eine Zeile in der Debugdatei beginnt gewöhnlich mit DEBUG, gefolgt von der Angabe der Protokollebene, der Aktion des Installationsprogramms und der Protokollmeldung. Beispiel:

```text
DEBUG 3 WebApp Panel: WebApp successfully deployed
```

Die Protokollebenen lauten wie folgt:

| 0 | Schwerwiegender Fehler | Die Aktion ist fehlgeschlagen und das Installationsprogramm kann nicht fortgesetzt werden. |
|---|---|---|
| 1 | Fehler | Die Aktion ist fehlgeschlagen. Die Installation wird fortgesetzt, aber ein CRX-Teil wurde nicht ordnungsgemäß installiert und funktioniert daher nicht. |
| 2 | Warnung | Die Aktion war erfolgreich, stieß aber auf Probleme. CRX funktioniert ggf. nicht ordnungsgemäß. |
| 3 | Informationen | Die Aktion war erfolgreich. |

### Thread-Dumps {#thread-dumps}

Thread-Dumps in Cloud-Umgebungen werden laufend gesammelt, können aber derzeit nicht selbst heruntergeladen werden. Wenden Sie sich in der Zwischenzeit an AEM Support, wenn Thread-Dumps zum Debuggen eines Problems erforderlich sind, und geben Sie das genaue Zeitfenster an.

## CRX/DE Lite und Developer Console {#crxde-lite-and-developer-console}

### Lokale Entwicklung {#local-development}

Für die lokale Entwicklung haben Entwickler uneingeschränkten Zugriff auf CRXDE Lite (`/crx/de`) und die AEM Web-Konsole (`/system/console`).

Beachten Sie, dass bei der lokalen Entwicklung (mit dem SDK) `/apps` und `/libs` direkt geschrieben werden können, was sich von Cloud-Umgebungen unterscheidet, in denen diese Ordner der obersten Ebene unveränderlich sind.

### Entwicklungs-Tools für AEM as a Cloud Service {#aem-as-a-cloud-service-development-tools}

Kunden können in der Entwicklungsumgebung der Autorenebene auf CRXDE Lite zugreifen, jedoch nicht in der Staging- oder Produktionsumgebung. Das unveränderliche Repository (`/libs`, `/apps`) kann zur Laufzeit nicht in beschrieben werden. Ein entsprechender Versuch führt zu Fehlern.

Stattdessen kann der Repository-Browser über die Entwicklerkonsole gestartet werden und eine schreibgeschützte Ansicht des Repositorys für alle Umgebungen auf den Ebenen „Autor“, „Veröffentlichung“ und „Vorschau“ bereitstellen. Mehr über den Repository-Browser erfahren Sie [hier](/help/implementing/developing/tools/repository-browser.md).

Eine Reihe von Tools zum Debugging von AEM as a Cloud Service-Entwicklungsumgebungen sind in der Developer Console für Entwicklungs-, Staging- und Produktionsumgebungen verfügbar. Die URL kann durch Anpassen der Autoren- oder Veröffentlichungs-Service-URLs wie folgt festgelegt werden:

`https://dev-console/-<namespace>.<cluster>.dev.adobeaemcloud.com`

Als Abkürzung kann der folgende Cloud Manager-CLI-Befehl verwendet werden, um die Entwicklerkonsole auf der Grundlage eines unten beschriebenen Umgebungsparameters zu starten:

`aio cloudmanager:open-developer-console <ENVIRONMENTID> --programId <PROGRAMID>`

Weitere Informationen finden Sie auf [dieser Seite](/help/release-notes/home.md).

Entwickler können Statusinformationen generieren und verschiedene Ressourcen auflösen.

Wie unten dargestellt, umfassen die verfügbaren Statusinformationen den Status von Paketen, Komponenten, OSGi-Konfigurationen, Oak-Indizes, OSGi-Services und Sling-Jobs.

![Developer Console 1](/help/implementing/developing/introduction/assets/devconsole1.png)

Wie unten dargestellt, können Entwickler Paketabhängigkeiten und Servlets auflösen:

![Developer Console 2](/help/implementing/developing/introduction/assets/devconsole2.png)

![Developer Console 3](/help/implementing/developing/introduction/assets/devconsole3.png)

Die Entwicklerkonsole ist auch für das Debugging nützlich und enthält einen Link zum Tool „Abfrage erläutern“:

![Developer Console 4](/help/implementing/developing/introduction/assets/devconsole4.png)

Bei Produktionsprogrammen wird der Zugriff auf die Entwicklerkonsole durch „Cloud Manager – Entwicklerrolle“ in der Admin Console definiert. Bei Sandbox-Programmen steht die Entwicklerkonsole jedem Benutzer mit einem Produktprofil zur Verfügung, das ihm Zugriff auf AEM as a Cloud Service gewährt. Für alle Programme ist &quot;Cloud Manager - Entwicklerrolle&quot;für Status-Dumps erforderlich und der Repository-Browser sowie Benutzer müssen auch im AEM Benutzer- oder AEM Administrator-Produktprofil für Autoren- und Veröffentlichungsdienste definiert sein, um Daten aus beiden Diensten anzuzeigen. Weitere Informationen zum Einrichten von Anwenderberechtigungen finden Sie in der [Dokumentation für Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html?lang=de).

### Performance-Überwachung {#performance-monitoring}

Adobe überwacht die Programmleistung und ergreift Maßnahmen, wenn eine Verschlechterung beobachtet wird. Derzeit können Programmmetriken nicht überwacht werden.

## Senden von E-Mails {#sending-email}

In den folgenden Abschnitten wird beschrieben, wie Sie E-Mails anfordern, konfigurieren und senden.

>[!NOTE]
>
>Der E-Mail-Service kann mit OAuth2-Unterstützung konfiguriert werden. Weitere Informationen finden Sie unter [OAuth2-Unterstützung für den E-Mail-Service](/help/security/oauth2-support-for-mail-service.md).

### Ausgehende E-Mails aktivieren {#enabling-outbound-email}

Standardmäßig sind zum Senden von E-Mails verwendete Ports deaktiviert. Um einen Port zu aktivieren, konfigurieren Sie die [erweiterten Netzwerkfunktionen](/help/security/configuring-advanced-networking.md) und stellen Sie sicher, dass Sie für jede benötigte Umgebung die Regeln für die Port-Weiterleitung des Endpunkts `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking` festlegen, die den beabsichtigten Port (z. B. 465 oder 587) einem Proxy-Port zuordnen.

Es wird empfohlen, das erweiterte Netzwerk mit einem auf `flexiblePortEgress` gesetzten `kind`-Parameter zu konfigurieren, da Adobe die Leistung des Ausgangs-Traffics des flexiblen Ports optimieren kann. Wenn eine eindeutige Ausgangs-IP-Adresse erforderlich ist, wählen Sie einen `kind`-Parameter von `dedicatedEgressIp`. Wenn Sie bereits aus anderen Gründen ein VPN konfiguriert haben, können Sie auch die eindeutige IP-Adresse verwenden, die von dieser erweiterten Netzwerkvariante bereitgestellt wird.

Sie müssen E-Mails über einen E-Mail-Server und nicht direkt an E-Mail-Clients senden. Andernfalls können die E-Mails blockiert werden.

### Senden von E-Mails {#sending-emails}

Der [Day CQ-E-Mail-Service-OSGi-Service](https://experienceleague.adobe.com/docs/experience-manager-65/administering/operations/notification.html?lang=de#configuring-the-mail-service) sollte verwendet werden und E-Mails müssen an den in der Support-Anfrage angegebenen Mailserver und nicht direkt an Empfänger gesendet werden.

### Konfiguration {#email-configuration}

E-Mails in AEM sollten mit dem [Day CQ-E-Mail-Service-OSGi-Service](https://experienceleague.adobe.com/docs/experience-manager-65/administering/operations/notification.html?lang=de#configuring-the-mail-service) gesendet werden.

Weitere Informationen zum Konfigurieren von E-Mail-Einstellungen finden Sie in der [AEM 6.5-Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-65/administering/operations/notification.html?lang=de). Beachten Sie für AEM as a Cloud Service die folgenden erforderlichen Anpassungen am `com.day.cq.mailer.DefaultMailService OSGI`-Service:

* Der Hostname des SMTP-Servers sollte auf $[env:AEM_PROXY_HOST;default=proxy.tunnel] eingestellt sein.
* Der SMTP-Server-Port sollte auf den Wert des ursprünglichen Proxy-Ports gesetzt werden, der im Parameter „portForwards“ festgelegt ist, der beim Konfigurieren des erweiterten Netzwerks im API-Aufruf verwendet wird. Beispiel: 30465 (anstatt 465)

Der SMTP-Server-Port sollte als `portDest`-Wert im portForwards-Parameter festgelegt werden, der im API-Aufruf bei der Konfiguration der erweiterten Vernetzung verwendet wird, und der `portOrig`-Wert sollte ein aussagekräftiger Wert sein, der innerhalb des erforderlichen Bereichs von 30000 bis 30999 liegt. Wenn der SMTP-Server-Port beispielsweise 465 ist, sollte der Port 30465 als `portOrig`-Wert verwendet werden.

In diesem Fall und unter der Annahme, dass SSL aktiviert werden muss, in der Konfiguration des **Day CQ Mail Service OSGI**-Services:

* Setzen Sie `smtp.port` auf `30465`
* Setzen Sie `smtp.ssl` auf `true`

Wenn der Ziel-Port 587 ist, sollte alternativ ein `portOrig`-Wert von 30587 verwendet werden. Und unter der Annahme, dass SSL deaktiviert sein sollte, ist die Konfiguration des Day CQ Mail Service OSGI-Services:

* Setzen Sie `smtp.port` auf `30587`
* Setzen Sie `smtp.ssl` auf `false`

Die `smtp.starttls`-Eigenschaft wird von AEM as a Cloud Service zur Laufzeit automatisch auf einen entsprechenden Wert eingestellt. Wenn `smtp.ssl` auf „true“ gesetzt ist, wird `smtp.startls` ignoriert. Wenn `smtp.ssl` auf „false“ gesetzt ist, wird `smtp.starttls` auf „true“ gesetzt. Dies gilt unabhängig von den in Ihrer OSGi-Konfiguration festgelegten `smtp.starttls`-Werten.


Der E-Mail-Service kann optional mit OAuth2-Unterstützung konfiguriert werden. Weitere Informationen finden Sie unter [OAuth2-Unterstützung für den E-Mail-Service](/help/security/oauth2-support-for-mail-service.md).

### Alte E-Mail-Konfiguration {#legacy-email-configuration}

Vor der Version 2021.9.0 wurde E-Mail über eine Anfrage an den Support konfiguriert. Beachten Sie die folgenden erforderlichen Anpassungen am `com.day.cq.mailer.DefaultMailService OSGI`-Service:

AEM as a Cloud Service erfordert, dass E-Mails über den Port 465 versendet werden. Wenn ein Mailserver Port 465 nicht unterstützt, kann Port 587 verwendet werden, solange die TLS-Option aktiviert ist.

Wenn Port 465 angefordert wurde:

* `smtp.port` auf `465` festlegen
* `smtp.ssl` auf `true` festlegen

und wenn Port 587 angefordert wurde:

* `smtp.port` auf `587` festlegen
* `smtp.ssl` auf `false` festlegen

Die `smtp.starttls`-Eigenschaft wird von AEM as a Cloud Service zur Laufzeit automatisch auf einen entsprechenden Wert eingestellt. Wenn `smtp.ssl` auf „true“ gesetzt ist, wird `smtp.startls` ignoriert. Wenn `smtp.ssl` auf „false“ gesetzt ist, wird `smtp.starttls` auf „true“ gesetzt. Dies gilt unabhängig von den in Ihrer OSGi-Konfiguration festgelegten `smtp.starttls`-Werten.

Der SMTP-Server-Host sollte auf den Host Ihres E-Mail-Servers eingestellt werden.

## Vermeidung von großen Eigenschaften mit mehreren Werten {#avoid-large-mvps}

Das Oak-Content-Repository, das AEM as a Cloud Service zugrunde liegt, ist nicht für die Verwendung mit einer übermäßigen Anzahl von mehrwertigen Eigenschaften (MVPs) vorgesehen. Eine Faustregel besagt, dass MVPs unter 1000 bleiben sollten. Die tatsächliche Leistung hängt jedoch von vielen Faktoren ab.

Warnungen werden standardmäßig nach mehr als 1000 protokolliert. Sie ähneln den folgenden.

```text
org.apache.jackrabbit.oak.jcr.session.NodeImpl Large multi valued property [/path/to/property] detected (1029 values). 
```

Große MVPs können zu Fehlern führen, da das MongoDB-Dokument mehr als 16 MB umfasst. Dies führt zu Fehlern wie den folgenden.

```text
Caused by: com.mongodb.MongoWriteException: Resulting document after update is larger than 16777216
```

Siehe [Apache Oak-Dokumentation](https://jackrabbit.apache.org/oak/docs/dos_and_donts.html#Large_Multi_Value_Property) für weitere Details.

## [!DNL Assets]-Entwicklungsrichtlinien und -Anwendungsfälle {#use-cases-assets}

Weitere Informationen zu den Anwendungsfällen, Empfehlungen und Referenzmaterialien für Assets as a Cloud Service finden Sie unter [Entwicklerreferenzen für Assets](/help/assets/developer-reference-material-apis.md#assets-cloud-service-apis).
