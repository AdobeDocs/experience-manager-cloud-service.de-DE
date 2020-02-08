---
title: AEM als Cloud Service Development Guidelines
description: 'Noch auszufüllen '
translation-type: tm+mt
source-git-commit: cedc14b0d71431988238d6cb4256936a5ceb759b

---


# AEM als Cloud Service Development Guidelines {#aem-as-a-cloud-service-development-guidelines}

## Hintergrundaufgaben und lange ausgeführte Aufträge {#background-tasks-and-long-running-jobs}

Als Hintergrundaufgaben ausgeführter Code muss davon ausgehen, dass die Instanz, in der er ausgeführt wird, jederzeit heruntergefahren werden kann. Daher muss der Code widerstandsfähig sein und der größte Import wiederverwendbar sein. Das bedeutet, dass der Code, wenn er erneut ausgeführt wird, nicht von vornherein beginnen sollte, sondern eher nahe an der Stelle, an der er aufgegeben wurde. Dies ist zwar keine neue Anforderung für diese Art von Code, in AEM als Cloud-Dienst ist es jedoch wahrscheinlicher, dass eine Instanzentnahme erfolgt.

Um die Probleme möglichst gering zu halten, sollten lang andauernde Aufträge möglichst vermieden werden, und sie sollten zumindest wieder aufgenommen werden können. Verwenden Sie für die Ausführung solcher Aufträge Sling Jobs, die mindestens einmal garantiert sind und daher, wenn sie unterbrochen werden, so bald wie möglich erneut ausgeführt werden. Aber sie sollten wahrscheinlich nicht von Anfang an wieder anfangen. Für die Planung solcher Aufträge ist es am besten, den [Sling Jobs](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#jobs-guarantee-of-processing) Scheduler so zu verwenden, wie dies bei mindestens einer Ausführung der Fall ist.

Der Sling Commons Scheduler sollte nicht für die Planung verwendet werden, da die Ausführung nicht garantiert werden kann. Es ist nur wahrscheinlicher, dass es geplant wird.

Ebenso kann nicht garantiert werden, dass alles, was asynchron geschieht, wie das Handeln bei Beobachtungsereignissen (JCR-Ereignisse oder Sling-Ressourcenereignisse), ausgeführt werden kann und daher mit Vorsicht verwendet werden muss. Dies gilt bereits jetzt für AEM-Bereitstellungen.

## Ausgehende HTTP-Verbindungen {#outgoing-http-connections}

Es wird dringend empfohlen, dass alle ausgehenden HTTP-Verbindungen angemessene Verbindungs- und Lesezeitlimits einrichten. Für Code, der diese Timeouts nicht anwendet, erzwingen AEM-Instanzen, die auf AEM als Cloud-Dienst ausgeführt werden, globale Timeouts. Diese Zeitüberschreitungswerte betragen 10 Sekunden für Verbindungsaufrufe und 60 Sekunden für Leseaufrufe für Verbindungen, die von den folgenden gängigen Java-Bibliotheken verwendet werden:

Adobe empfiehlt die Verwendung der bereitgestellten [Apache HttpComponents Client 4.x-Bibliothek](https://hc.apache.org/httpcomponents-client-ga/) zum Herstellen von HTTP-Verbindungen.

Es gibt folgende Alternativen, die bekanntermaßen funktionieren, aber die Bereitstellung der Abhängigkeit selbst erfordern:

* [java.net.URL](https://docs.oracle.com/javase/7/docs/api/java/net/URL.html) und/oder [java.net.URLConnection](https://docs.oracle.com/javase/7/docs/api/java/net/URLConnection.html) (bereitgestellt von AEM)
* [Apache Commons HttpClient 3.x](https://hc.apache.org/httpclient-3.x/) (nicht empfohlen, da es veraltet ist und durch Version 4.x ersetzt wird)
* [OK HTTP](OK HTTP (Nicht von AEM bereitgestellt)) (Nicht von AEM bereitgestellt)

## Überwachung und Debugging {#monitoring-and-debugging}

### Protokolle {#logs}

* Für die lokale Entwicklung werden Protokolleinträge in lokale Dateien geschrieben
   * `./crx-quickstart/logs`
* In Cloud-Umgebungen können Entwickler Protokolle über Cloud Manager herunterladen oder ein Befehlszeilenwerkzeug verwenden, um die Protokolle zu verkleinern. <!-- See the [Cloud Manager documentation](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html) for more details. Note that custom logs are not supported and so all logs should be output to the error log. -->
* Um die Protokollierungsstufen für Cloud-Umgebungen zu ändern, sollte die Sling Logging OSGI-Konfiguration geändert und anschließend eine vollständige Neubereitstellung durchgeführt werden. Da dies nicht sofort geschieht, sollten Sie vorsichtig sein, ausführliche Protokolle über Produktionsumgebungen zu aktivieren, die viel Traffic erhalten. In Zukunft wird es möglicherweise Mechanismen geben, um die Protokollierungsstufe schneller zu ändern.

### Thread Dumps {#thread-dumps}

Thread-Dumps in Cloud-Umgebungen werden laufend gesammelt, können jedoch derzeit nicht auf Self-Service-Weise heruntergeladen werden. Wenden Sie sich in der Zwischenzeit an den AEM-Support, wenn Thread-Dumps zum Debuggen eines Problems erforderlich sind, und geben Sie das genaue Zeitfenster an.

### CRX/DE Lite und Systemkonsole {#crxde-lite-and-system-console}

## Lokale Entwicklung {#local-development}

Für die lokale Entwicklung haben Entwickler uneingeschränkten Zugriff auf CRXDE Lite (`/crx/de`) und die AEM Web Console (`/system/console`).

Beachten Sie, dass bei der lokalen Entwicklung (mit dem Cloud-fähigen Schnellstart) `/apps` und direkt geschrieben werden `/libs` können, was sich von Cloud-Umgebungen unterscheidet, in denen diese Ordner der obersten Ebene unveränderlich sind.

## AEM als Tools zur Entwicklung von Cloud-Diensten {#aem-as-a-cloud-service-development-tools}

Kunden können auf CRXDE Lite in der Entwicklungsumgebung zugreifen, jedoch nicht auf die Bühne oder Produktion. Das unveränderliche Repository (`/libs`, `/apps`) kann zur Laufzeit nicht in geschrieben werden. Daher führt der Versuch, dies zu tun, zu Fehlern.

Eine Reihe von Tools zum Debugging von AEM als Cloud-Service-Entwicklungsumgebungen sind in der Developer Console für Entwicklungs-, Bereitstellungs- und Produktionsumgebungen verfügbar. Die URL kann wie folgt festgelegt werden, indem die Autor- oder Veröffentlichungsdienst-URLs angepasst werden:

`https://dev-console>-<namespace>.<cluster>.dev.adobeaemcloud.com`

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

**AEM Staging- und Produktionsdienst**

Kunden haben keinen Zugriff auf Entwicklerwerkzeuge für Staging- und Produktionsumgebungen.

### Diagnose {#diagnostics}

Die Systemkonsole ist für Entwicklungsumgebungen verfügbar. Diagnostische Deponien für Staging und Produktion sind jedoch nicht verfügbar.