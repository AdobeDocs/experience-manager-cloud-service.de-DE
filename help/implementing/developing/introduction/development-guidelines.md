---
title: Entwicklungsrichtlinien für AEM as a Cloud Service
description: 'Noch auszufüllen '
translation-type: tm+mt
source-git-commit: 9777dd5772ab443b5b3dabbc74ed0d362e52df60

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

Das Dateisystem der Instanz sollte in AEM nicht als Cloud-Dienst verwendet werden. Der Datenträger ist kurzlebig und wird entsorgt, wenn Instanzen recycelt werden. Eine begrenzte Nutzung des Dateisystems für die temporäre Speicherung im Zusammenhang mit der Verarbeitung einzelner Anfragen ist möglich, sollte aber nicht für riesige Dateien missbraucht werden. Dies liegt daran, dass dies negative Auswirkungen auf das Ressourcenverbrauchskontingent haben kann und Datenträgerbeschränkungen unterliegt.

Als Beispiel, bei dem die Verwendung des Dateisystems nicht unterstützt wird, sollte die Veröffentlichungsstufe sicherstellen, dass alle Daten, die beibehalten werden müssen, für längere Zeit an einen externen Dienst gesendet werden.

## Überwachung {#observation}

Ähnlich wie bei allem, was asynchron passiert, wie bei Beobachtungsereignissen, kann nicht garantiert werden, dass es lokal ausgeführt wird, und muss daher mit Vorsicht verwendet werden. Dies gilt sowohl für JCR-Ereignisse als auch für Sling-Ressourcenereignisse. Bei einer Änderung kann die Instanz heruntergefahren und durch eine andere Instanz ersetzt werden. Andere zu diesem Zeitpunkt aktive Instanzen in der Topologie können auf dieses Ereignis reagieren. In diesem Fall wird es sich jedoch nicht um eine örtliche Veranstaltung handeln, und es könnte sogar sein, dass es bei einer laufenden Präsidentschaftswahl zum Zeitpunkt der Veranstaltung keinen aktiven Führer gibt.

## Hintergrundaufgaben und lange ausgeführte Aufträge {#background-tasks-and-long-running-jobs}

Bei Code, der als Hintergrundaufgaben ausgeführt wird, muss davon ausgegangen werden, dass die Instanz, in der er ausgeführt wird, jederzeit heruntergefahren werden kann. Daher muss der Code widerstandsfähig sein und der größte Import wiederverwendbar sein. Das bedeutet, dass der Code, wenn er erneut ausgeführt wird, nicht von vornherein beginnen sollte, sondern eher nahe an der Stelle, an der er aufgegeben wurde. Dies ist zwar keine neue Anforderung für diese Art von Code, in AEM als Cloud-Dienst ist es jedoch wahrscheinlicher, dass eine Instanzentnahme erfolgt.

Um die Probleme möglichst gering zu halten, sollten lang andauernde Aufträge möglichst vermieden werden, und sie sollten zumindest wieder aufgenommen werden können. Verwenden Sie für die Ausführung solcher Aufträge Sling Jobs, die mindestens einmal garantiert sind und daher, wenn sie unterbrochen werden, so bald wie möglich erneut ausgeführt werden. Aber sie sollten wahrscheinlich nicht von Anfang an wieder anfangen. Für die Planung solcher Aufträge ist es am besten, den [Sling Jobs](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#jobs-guarantee-of-processing) Scheduler so zu verwenden, wie dies bei mindestens einer Ausführung der Fall ist.

Der Sling Commons Scheduler sollte nicht für die Planung verwendet werden, da die Ausführung nicht garantiert werden kann. Es ist nur wahrscheinlicher, dass es geplant wird.

Ebenso kann nicht garantiert werden, dass alles, was asynchron geschieht, wie das Handeln bei Beobachtungsereignissen (JCR-Ereignisse oder Sling-Ressourcenereignisse), ausgeführt werden kann und daher mit Sorgfalt verwendet werden muss. Dies gilt bereits jetzt für AEM-Bereitstellungen.

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

* Für die lokale Entwicklung werden Protokolleinträge in lokale Dateien geschrieben
   * `./crx-quickstart/logs`
* In Cloud-Umgebungen können Entwickler Protokolle über Cloud Manager herunterladen oder ein Befehlszeilenwerkzeug verwenden, um die Protokolle zu verkleinern. <!-- See the [Cloud Manager documentation](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html) for more details. Note that custom logs are not supported and so all logs should be output to the error log. -->
* Um die Protokollierungsstufen für Cloud-Umgebungen zu ändern, sollte die Sling Logging OSGI-Konfiguration geändert und anschließend eine vollständige Neubereitstellung durchgeführt werden. Da dies nicht sofort geschieht, sollten Sie vorsichtig sein, ausführliche Protokolle über Produktionsumgebungen zu aktivieren, die viel Traffic erhalten. In Zukunft wird es möglicherweise Mechanismen geben, um die Protokollierungsstufe schneller zu ändern.

### Thread Dumps {#thread-dumps}

Thread-Dumps in Cloud-Umgebungen werden laufend gesammelt, können jedoch derzeit nicht auf Self-Service-Weise heruntergeladen werden. Wenden Sie sich in der Zwischenzeit an den AEM-Support, wenn Thread-Dumps zum Debuggen eines Problems erforderlich sind, und geben Sie das genaue Zeitfenster an.

## CRX/DE Lite und Systemkonsole {#crxde-lite-and-system-console}

### Lokale Entwicklung {#local-development}

Für die lokale Entwicklung haben Entwickler uneingeschränkten Zugriff auf CRXDE Lite (`/crx/de`) und die AEM Web Console (`/system/console`).

Beachten Sie, dass bei der lokalen Entwicklung (mit dem Cloud-fähigen Schnellstart) `/apps` und direkt geschrieben werden `/libs` können, was sich von Cloud-Umgebungen unterscheidet, in denen diese Ordner der obersten Ebene unveränderlich sind.

### AEM as a Cloud Service Development tools {#aem-as-a-cloud-service-development-tools}

Kunden können auf CRXDE Lite in der Entwicklungsumgebung zugreifen, jedoch nicht auf die Bühne oder Produktion. Das unveränderliche Repository (`/libs`, `/apps`) kann zur Laufzeit nicht in geschrieben werden. Daher führt der Versuch, dies zu tun, zu Fehlern.

Eine Reihe von Tools zum Debugging von AEM als Cloud-Service-Entwicklungsumgebungen stehen in der Developer Console für Entwicklungs-, Bereitstellungs- und Produktionsumgebungen zur Verfügung. Die URL kann wie folgt festgelegt werden, indem die URLs des Autoren- oder Veröffentlichungsdienstes angepasst werden:

`https://dev-console/-<namespace>.<cluster>.dev.adobeaemcloud.com`

Als Kurzbefehl kann der folgende CLI-Befehl für Cloud Manager verwendet werden, um die Developer Console basierend auf einem im Folgenden beschriebenen Umgebungsparameter zu starten:

`aio cloudmanager:open-developer-console <ENVIRONMENTID> --programId <PROGRAMID>`

See [this page](/help/release-notes/home.md) for more information.

Entwickler können Statusinformationen generieren und verschiedene Ressourcen auflösen.

Wie unten dargestellt, umfassen die verfügbaren Statusinformationen den Status von Paketen, Komponenten, OSGI-Konfigurationen, Eichenindizes, OSGI-Dienste und Sling-Aufträge.

![Dev Console 1](/help/implementing/developing/introduction/assets/devconsole1.png)

Wie unten dargestellt können Entwickler Paketabhängigkeiten und Servlets auflösen:

![Dev Console 2](/help/implementing/developing/introduction/assets/devconsole2.png)

![Dev Console 3](/help/implementing/developing/introduction/assets/devconsole3.png)

Die Developer Console ist auch für das Debugging nützlich und enthält einen Link zum Tool &quot;Anfrage erläutern&quot;:

![Dev Console 4](/help/implementing/developing/introduction/assets/devconsole4.png)

### AEM Staging- und Produktionsdienst {#aem-staging-and-production-service}

Kunden haben keinen Zugriff auf Entwicklerwerkzeuge für Staging- und Produktionsumgebungen.

### Leistungsüberwachung {#performance-monitoring}

Adobe überwacht die Anwendungsleistung und ergreift Maßnahmen, um bei auftretender Verschlechterung Abhilfe zu schaffen. Derzeit können Anwendungsmetriken nicht bereinigt werden.