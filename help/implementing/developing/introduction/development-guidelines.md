---
title: Entwicklungsrichtlinien für AEM as a Cloud Service
description: 'Noch auszufüllen '
translation-type: tm+mt
source-git-commit: 26833f59f21efa4de33969b7ae2e782fe5db8a14

---


# Entwicklungsrichtlinien für AEM as a Cloud Service {#aem-as-a-cloud-service-development-guidelines}

Code, der in AEM als Cloud-Dienst ausgeführt wird, muss wissen, dass er immer in einem Cluster ausgeführt wird. Das bedeutet, dass immer mehr als eine Instanz ausgeführt wird. Der Code muss robust sein, insbesondere da eine Instanz jederzeit gestoppt werden kann.

Während der Aktualisierung von AEM als Cloud-Dienst werden Instanzen mit altem und neuem Code parallel ausgeführt. Daher darf alter Code nicht mit Inhalten umgehen, die mit neuem Code erstellt wurden, und der neue Code muss mit alten Inhalten umgehen können.
<!--

>[!NOTE]
> All of the best practices mentioned here hold true for on-premise deployments of AEM, if not stated otherwise. An instance can always stop due to various reasons. However, with Skyline it is more likely to happen therefore an instance stopping is the rule not an exception.

-->

Wenn der Master im Cluster identifiziert werden muss, kann die Apache Sling Discovery API verwendet werden, um ihn zu erkennen.

## Speicherstatus {#state-in-memory}

Der Status darf nicht im Speicher verbleiben, sondern muss im Repository bestehen bleiben. Andernfalls wird dieser Status möglicherweise verloren, wenn eine Instanz beendet wird.

## Status auf dem Dateisystem {#state-on-the-filesystem}

Das Dateisystem der Instanz sollte in AEM nicht als Cloud-Dienst verwendet werden. Der Datenträger ist kurzlebig und wird entsorgt, wenn Instanzen recycelt werden. Eine beschränkte Nutzung des Dateisystems für die temporäre Datenspeicherung im Zusammenhang mit der Verarbeitung einzelner Anfragen ist möglich, sollte aber nicht für riesige Dateien missbraucht werden. Dies liegt daran, dass dies negative Auswirkungen auf das Ressourcenverbrauchskontingent haben kann und Datenträgerbeschränkungen unterliegt.

Wenn beispielsweise die Dateisystemnutzung nicht unterstützt wird, sollte die Veröffentlichungsstufe sicherstellen, dass alle Daten, die beibehalten werden müssen, für längere Datenspeicherung an einen externen Dienst gesendet werden.

## Überwachung {#observation}

Ähnlich wie alles, was asynchron passiert, wie das Handeln auf Beobachtungsdaten, kann nicht garantiert werden, dass es lokal ausgeführt wird und muss daher mit Sorgfalt verwendet werden. Dies gilt sowohl für JCR-Ereignis als auch für Sling-Ressourcen-Ereignis. Bei einer Änderung kann die Instanz heruntergefahren und durch eine andere Instanz ersetzt werden. Andere zu diesem Zeitpunkt aktive Instanzen in der Topologie können auf dieses Ereignis reagieren. In diesem Fall wird es sich jedoch nicht um ein örtliches Ereignis handeln, und es könnte sogar sein, dass es bei einer laufenden Präsidentschaftswahl, wenn das Ereignis ausgestellt wird, keine aktive Führung gibt.

## Aufgaben im Hintergrund und lange ausgeführte Aufträge {#background-tasks-and-long-running-jobs}

Als Hintergrundcode ausgeführter Aufgaben müssen davon ausgehen, dass die Instanz, in der sie ausgeführt werden, jederzeit heruntergefahren werden kann. Daher muss der Code widerstandsfähig sein und der größte Import wiederverwendbar sein. Das heißt, wenn der Code erneut ausgeführt wird, sollte er nicht von Anfang an erneut Beginn werden, sondern eher an der Stelle, an der er aufgegeben wurde. Dies ist zwar keine neue Anforderung für diese Art von Code, in AEM als Cloud-Dienst ist es jedoch wahrscheinlicher, dass eine Instanzentnahme erfolgt.

Um die Probleme möglichst gering zu halten, sollten lang andauernde Aufträge möglichst vermieden werden, und sie sollten zumindest wieder aufgenommen werden können. Verwenden Sie für die Ausführung solcher Aufträge Sling Jobs, die mindestens einmal garantiert sind und daher, wenn sie unterbrochen werden, so bald wie möglich erneut ausgeführt werden. Aber sie sollten wahrscheinlich nicht von Anfang an wieder Beginn machen. Für die Planung solcher Aufträge ist es am besten, die Planung [Sling-Aufträge](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#jobs-guarantee-of-processing) so zu verwenden, dass sie mindestens einmal ausgeführt wird.

Die Planung Sling Commons sollte nicht für die Planung verwendet werden, da die Ausführung nicht garantiert werden kann. Es ist nur wahrscheinlicher, dass es geplant wird.

Ebenso kann nicht garantiert werden, dass alles, was asynchron passiert, wie das Handeln auf Beobachtungsdaten (wie JCR-Ereignisse oder Sling-Ressourcen-Ereignis) ausgeführt werden kann und daher mit Sorgfalt verwendet werden muss. Dies gilt bereits jetzt für AEM-Bereitstellungen.

## Ausgehende HTTP-Verbindungen {#outgoing-http-connections}

Es wird dringend empfohlen, dass alle ausgehenden HTTP-Verbindungen angemessene Verbindungs- und Lesezeitlimits einrichten. Für Code, der diese Timeouts nicht anwendet, erzwingen AEM-Instanzen, die auf AEM als Cloud-Dienst ausgeführt werden, globale Timeouts. Diese Zeitüberschreitungswerte betragen 10 Sekunden für Verbindungsaufrufe und 60 Sekunden für Leseaufrufe für Verbindungen, die von den folgenden gängigen Java-Bibliotheken verwendet werden:

Adobe empfiehlt die Verwendung der bereitgestellten [Apache HttpComponents Client 4.x-Bibliothek](https://hc.apache.org/httpcomponents-client-ga/) zum Herstellen von HTTP-Verbindungen.

Es gibt folgende Alternativen, die bekanntermaßen funktionieren, aber die Bereitstellung der Abhängigkeit selbst erfordern:

* [java.net.URL](https://docs.oracle.com/javase/7/docs/api/java/net/URL.html) und/oder [java.net.URLConnection](https://docs.oracle.com/javase/7/docs/api/java/net/URLConnection.html) (bereitgestellt von AEM)
* [Apache Commons HttpClient 3.x](https://hc.apache.org/httpclient-3.x/) (nicht empfohlen, da es veraltet ist und durch Version 4.x ersetzt wird)
* [OK HTTP](https://square.github.io/okhttp/) (nicht von AEM bereitgestellt)

## Keine klassischen Benutzeroberflächenanpassungen {#no-classic-ui-customizations}

AEM als Cloud-Dienst unterstützt nur die Touch-Benutzeroberfläche für Kundencode von Drittanbietern. Die klassische Benutzeroberfläche kann nicht angepasst werden.

## Native Binärdateien vermeiden {#avoid-native-binaries}

Code kann keine Binärdateien zur Laufzeit herunterladen oder ändern. Beispielsweise kann es keine Dateien entpacken `jar` oder `tar` Dateien.

## Keine Streaming-Binärdateien über AEM als Cloud-Dienst {#no-streaming-binaries}

Auf Binärdateien sollte über das CDN zugegriffen werden, das Binärdateien außerhalb der AEM-Hauptdienste bereitstellt.

Verwenden Sie zum Beispiel nicht `asset.getOriginal().getStream()`, was das Herunterladen einer Binärdatei auf die Kurzzeitplatte des AEM-Dienstes auslöst.

## Keine Rückwärtsreplikationsagenten {#no-reverse-replication-agents}

Die umgekehrte Replizierung von &quot;Veröffentlichen auf Autor&quot;wird in AEM nicht als Cloud-Dienst unterstützt. Wenn eine solche Strategie erforderlich ist, können Sie einen externen Persistenzspeicher verwenden, der von der Farm der Veröffentlichungsinstanzen und möglicherweise vom Autorencluster freigegeben wird.

## Forward Replication Agents müssen möglicherweise portiert werden. {#forward-replication-agents}

Inhalte werden von &quot;Autor&quot;zu &quot;Veröffentlichen&quot;über einen Pub-Unter-Mechanismus repliziert. Benutzerdefinierte Replizierungsagenten werden nicht unterstützt.

## Überwachung und Debugging {#monitoring-and-debugging}

### Protokolle {#logs}

Für die lokale Entwicklung werden Protokolleinträge in lokale Dateien im `/crx-quickstart/logs` Ordner geschrieben.

Auf Cloud-Umgebung können Entwickler Protokolle über Cloud Manager herunterladen oder ein Befehlszeilenwerkzeug verwenden, um die Protokolle zu verkleinern. <!-- See the [Cloud Manager documentation](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html) for more details. Note that custom logs are not supported and so all logs should be output to the error log. -->

**Protokollebene festlegen**

Um die Protokollierungsstufen für Cloud-Umgebung zu ändern, sollte die Sling Logging OSGI-Konfiguration geändert und anschließend eine vollständige Neubereitstellung durchgeführt werden. Da dies nicht sofort geschieht, sollten Sie vorsichtig sein, um ausführliche Protokolle zu Produktions-Umgebung zu aktivieren, die viel Traffic erhalten. In Zukunft wird es möglicherweise Mechanismen geben, um die Protokollierungsstufe schneller zu ändern.

> [!NOTE]
> 
> Um die unten aufgeführten Konfigurationsänderungen durchzuführen, müssen Sie sie auf einer lokalen Entwicklungs-Umgebung erstellen und dann als Cloud-Dienstinstanz an eine AEM-Instanz senden. Weitere Informationen dazu finden Sie unter [Bereitstellen auf AEM als Cloud-Dienst](/help/implementing/deploying/overview.md).

**Aktivieren der DEBUG-Protokollebene**

Die standardmäßige Protokollebene ist INFO, DEBUG-Meldungen werden also nicht protokolliert.
Um die DEBUG-Protokollebene zu aktivieren, legen Sie die Variable

``` /libs/sling/config/org.apache.sling.commons.log.LogManager/org.apache.sling.commons.log.level ```

auf „debug“ ein. Lassen Sie die DEBUG-Protokollebene nicht länger als notwendig aktiviert, da hierdurch zahlreiche Protokolle generiert werden.
Eine Zeile in der Debugdatei beginnt gewöhnlich mit DEBUG, gefolgt von der Angabe der Protokollebene, der Aktion des Installationsprogramms und der Protokollmeldung. Beispiel:

``` DEBUG 3 WebApp Panel: WebApp successfully deployed ```

Die Protokollebenen lauten wie folgt:

| 0 | Schwerwiegender Fehler | Die Aktion ist fehlgeschlagen, und das Installationsprogramm kann nicht fortgesetzt werden. |
|---|---|---|
| 1 | Fehler | Die Aktion ist fehlgeschlagen. Die Installation wird fortgesetzt, aber ein CRX-Teil wurde nicht ordnungsgemäß installiert und funktioniert daher nicht. |
| 2 | Warnung | Die Aktion war erfolgreich, hatte aber Probleme. CRX funktioniert ggf. nicht ordnungsgemäß. |
| 3 | Informationen | Die Aktion war erfolgreich. |

### Thread Dumps {#thread-dumps}

Thread-Dumps auf Cloud-Umgebung werden laufend gesammelt, können jedoch derzeit nicht auf Self-Service-Weise heruntergeladen werden. Wenden Sie sich in der Zwischenzeit an den AEM-Support, wenn Thread-Dumps zum Debuggen eines Problems erforderlich sind, und geben Sie das genaue Zeitfenster an.

## CRX/DE Lite und Systemkonsole {#crxde-lite-and-system-console}

### Lokale Entwicklung {#local-development}

Für die lokale Entwicklung haben Entwickler uneingeschränkten Zugriff auf CRXDE Lite (`/crx/de`) und die AEM Web Console (`/system/console`).

Beachten Sie, dass bei der lokalen Entwicklung (mit dem Cloud-fähigen Schnellstart) `/apps` und direkt geschrieben werden `/libs` können. Dies unterscheidet sich von Cloud-Umgebung, bei denen diese obersten Ordner unveränderlich sind.

### AEM as a Cloud Service Development tools {#aem-as-a-cloud-service-development-tools}

Kunden können auf CRXDE Lite auf der Entwicklungs-Umgebung zugreifen, jedoch nicht auf die Bühne oder Produktion. Das unveränderliche Repository (`/libs`, `/apps`) kann zur Laufzeit nicht in geschrieben werden. Daher führt der Versuch, dies zu tun, zu Fehlern.

Eine Reihe von Tools zum Debugging von AEM als Cloud Service Developer-Umgebung stehen in der Developer Console für Entwickler-, Bereitstellungs- und Produktionsfunktionen zur Verfügung. Die URL kann wie folgt festgelegt werden, indem die URLs des Autoren- oder Veröffentlichungsdienstes angepasst werden:

`https://dev-console/-<namespace>.<cluster>.dev.adobeaemcloud.com`

Als Kurzbefehl kann der folgende CLI-Befehl für Cloud Manager verwendet werden, um die Developer Console auf der Grundlage eines Umgebung-Parameters zu starten, der unten beschrieben wird:

`aio cloudmanager:open-developer-console <ENVIRONMENTID> --programId <PROGRAMID>`

See [this page](/help/release-notes/home.md) for more information.

Entwickler können Statusinformationen generieren und verschiedene Ressourcen auflösen.

Wie unten dargestellt, umfassen die verfügbaren Statusinformationen den Status von Paketen, Komponenten, OSGI-Konfigurationen, Eichenindizes, OSGI-Dienste und Sling-Aufträge.

![Dev Console 1](/help/implementing/developing/introduction/assets/devconsole1.png)

Wie unten dargestellt können Entwickler Paketabhängigkeiten und Servlets auflösen:

![Dev Console 2](/help/implementing/developing/introduction/assets/devconsole2.png)

![Dev Console 3](/help/implementing/developing/introduction/assets/devconsole3.png)

Die Developer Console ist auch für das Debugging nützlich und enthält einen Link zum Tool &quot;Abfrage erläutern&quot;:

![Dev Console 4](/help/implementing/developing/introduction/assets/devconsole4.png)

### AEM Staging- und Produktionsdienst {#aem-staging-and-production-service}

Kunden haben keinen Zugriff auf Entwicklerwerkzeuge für Staging- und Produktions-Umgebung.

### Leistungsüberwachung {#performance-monitoring}

Adobe überwacht die Anwendungsleistung und ergreift Maßnahmen, um bei auftretender Verschlechterung Abhilfe zu schaffen. Derzeit können Anwendungsmetriken nicht bereinigt werden.