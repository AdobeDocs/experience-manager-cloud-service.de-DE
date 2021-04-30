---
title: So gehen Sie mit Ihrer Headless-Anwendung live
description: In diesem Teil der AEM Headless Developer-Journey erfahren Sie, wie Sie eine kostenlose Anwendung live bereitstellen, indem Sie Ihren lokalen Code in Git übernehmen und für die CI/CD-Pipeline auf Cloud Manager Git verschieben.
hide: true
hidefromtoc: true
index: false
exl-id: f79b5ada-8f59-4706-9f90-bc63301b2b7d
translation-type: tm+mt
source-git-commit: dc4f1e916620127ebf068fdcc6359041b49891cf
workflow-type: tm+mt
source-wordcount: '1039'
ht-degree: 2%

---

# Wie Sie mit Ihrer Headless-Anwendung live gehen können {#go-live}

>[!CAUTION]
>
>ARBEITEN IN FORTSCHRITTEN - Die Schaffung dieses Dokuments ist im Gange und sollte nicht als vollständig oder endgültig betrachtet werden und auch nicht für Produktionszwecke verwendet werden.

In diesem Teil der [AEM Headless Developer-Journey lernen Sie, wie Sie eine kostenlose Anwendung live bereitstellen, indem Sie Ihren lokalen Code in Git übernehmen und sie für die CI/CD-Pipeline in Cloud Manager Git verschieben.](overview.md)

## Die Meldung bisher {#story-so-far}

Im vorherigen Dokument der AEM koplosen Journey [Wie Sie alles zusammenstellen - Ihre App und Ihr Inhalt in AEM Headless](put-it-all-together.md) haben Sie gelernt, wie Sie Ihr eigenes AEM kopflosen Projekt für die Live-Veröffentlichung vorbereiten können. Jetzt sollten Sie:

* Machen Sie sich mit den Anforderungen vertraut, die Sie erfüllen müssen.

Dieser Artikel baut auf diesen Grundlagen auf, damit Sie verstehen, wie Sie Ihr AEM Headless-Projekt tatsächlich aktivieren können.

## Vorgabe {#objective}

Dieses Dokument hilft Ihnen, die AEM freizügige Veröffentlichungspipeline und die Leistungsaspekte zu verstehen, die Sie beachten müssen, bevor Sie mit der Anwendung live gehen.

* Grundlagen zur AEM Content-Replikation und -Zwischenspeicherung
* Konfigurieren Sie die Werkzeuge, die zum Simulieren der Funktion &quot;Los&quot;für Ihre kostenlose Anwendung erforderlich sind.
* Sichern und skalieren Sie Ihre Anwendung vor dem Start
* Leistungs- und Debugprobleme überwachen

## Grundlagen zur Inhaltsreplikation und -zwischenspeicherung {#content-replication-and-caching}

Eine vollständige AEM Umgebung besteht aus einem Autor, einem Veröffentlichen und einem Dispatcher.

* **Der Authoring-** Dienst, bei dem interne Benutzer Inhalte erstellen, verwalten und Vorschauen erstellen.

* **Der Publish-** Dienst wird als &quot;Live&quot;-Umgebung betrachtet und ist in der Regel das, mit dem Endbenutzer interagieren. Nach der Bearbeitung und Genehmigung im Autorendienst werden Inhalte an den Veröffentlichungsdienst verteilt.

* **Der** Dispatcher ist ein statischer Webserver, der mit dem AEM Dispatcher-Modul erweitert wird. Er speichert durch die Veröffentlichungsinstanz generierte Webseiten zwischen, um die Leistung zu verbessern.

Das häufigste Bereitstellungsmuster bei AEM kostenlosen Anwendungen besteht darin, dass die Produktionsversion der Anwendung mit einem AEM Publish-Dienst verbunden wird.

## Anforderungen und Konfiguration {#requirements-and-configuration}

1. Richten Sie eine [Lokale Laufzeitumgebung](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/aem-runtime.html#install-java) mit [AEM als Cloud-Dienst-SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md) ein.
2. Installieren Sie den [WKND-Beispielinhalt](/help/implementing/developing/introduction/develop-wknd-tutorial.md) und die folgenden GraphQL-Endpunkte
3. Stellen Sie einen [statischen Knoten Server](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/production-deployment.html?lang=en#static-server) bereit und konfigurieren Sie ihn.

## Sichern und skalieren Sie Ihre Headless-Anwendung vor dem Start von {#secure-and-scale-before-launch}

1. [Token-basierte Authentifizierung](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) konfigurieren
2. Sichere Webhows
3. Zwischenspeicherung und Skalierbarkeit konfigurieren

## Bereitstellung für Produktion {#deploy-to-production}

Nachdem Sie den gesamten Code und Inhalt lokal getestet haben, können Sie jetzt mit der Bereitstellung einer Produktion mit AEM beginnen.

### Modellstruktur vs. GraphQL-Ausgabe {#structure-vs-output}

* Vermeiden Sie das Erstellen von Abfragen, die mehr als 15 KB JSON ausgeben (gzip-komprimiert). Lange JSON-Dateien sind ressourcenintensiv, damit die Clientanwendung analysiert werden kann.
* Vermeiden Sie mehr als fünf verschachtelte Ebenen von Fragmenthierarchien. Zusätzliche Ebenen erschweren es Inhaltserstellern, die Auswirkungen ihrer Änderungen zu berücksichtigen.
* Verwenden Sie Abfragen mit mehreren Objekten, anstatt Abfragen mit Abhängigkeitshierarchien innerhalb der Modelle zu modellieren. Dadurch erhalten Sie mehr langfristige Flexibilität bei der Neustrukturierung der JSON-Ausgabe, ohne dass eine Menge Inhaltsänderungen vorgenommen werden müssen.

### CDN-Cache-Trefferverhältnis maximieren {#maximize-cdn}

* Verwenden Sie keine direkten GraphQL-Abfragen, es sei denn, Sie fordern Live-Inhalte von der Oberfläche an.
   * Verwenden Sie stattdessen persistente Abfragen.
   * Stellen Sie CDN TTL über 600 Sekunden bereit, damit das CDN sie zwischenspeichern kann.
   * AEM können die Auswirkungen einer Modelländerung auf bestehende Abfragen berechnen.
* Teilen Sie JSON-Dateien/GraphQL-Abfragen zwischen niedriger und hoher Inhaltsänderungsrate, um den Client-Traffic zu CDN zu reduzieren und höhere TTL zuzuweisen. Dadurch wird das CDN, das JSON mit dem Herkunft-Server erneut validiert, minimiert.
* Verwenden Sie Soft Purge, um Inhalte aus dem CDN aktiv für ungültig zu erklären. Dadurch kann das CDN den Inhalt erneut herunterladen, ohne dass ein Cache fehlschlägt.

### Verbessern Sie die Zeit zum Herunterladen von Headless Content {#improve-download-time}

* Stellen Sie sicher, dass HTTP-Clients HTTP/2 verwenden.
* Vergewissern Sie sich, dass HTTP-Clients die Header-Anforderung für gzip akzeptieren.
* Minimieren Sie die Anzahl der Domänen, die zum Hosten von JSON und referenzierten Artefakten verwendet werden.
* Nutzen Sie `Last-modified-since`, um Ressourcen zu aktualisieren.
* Verwenden Sie `_reference`-Ausgabe in der JSON-Datei, um Beginn beim Herunterladen von Assets zu verwenden, ohne vollständige JSON-Dateien analysieren zu müssen.

## Überwachung {#monitoring}

### So überprüfen Sie die Gesamtleistung {#check-overall-performance}

* Vorschauen- und Produktionsversionen der App überprüfen
* Statusseiten AEM aktuellen Status der Dienstverfügbarkeit überprüfen
* Zugriff auf Leistungsberichte
   * Leistung des Versands
      * Fastly (CDN) - Überprüfung der Anzahl der Aufrufe, Cache-Rate, Fehlerraten, Nutzlastverkehr
      * Herkunft-Server - Anzahl der Aufrufe, Fehlerquoten, CPU-Lasten, Nutzlastverkehr
   * Autorenleistung
      * Anzahl der Benutzer, Anforderungen und Ladevorgänge prüfen
* Zugriff auf App- und Space-spezifische Leistungsberichte
   * Überprüfen Sie, ob die allgemeinen Metriken grün/orange/rot sind, und identifizieren Sie dann spezifische App-Probleme.
   * Öffnen Sie dieselben oben gefilterten Berichte nach App/Raum (z. B. Photoshop Desktop, Paywall usw.)
   * Verwenden Sie Splunk-Protokoll-APIs, um auf Dienst- und Anwendungsleistung zuzugreifen
   * Wenden Sie sich an den Kundensupport, falls es andere Probleme gibt.

## Fehlerbehebung {#troubleshooting}

### Debugging {#debugging}

Um sicherzustellen, dass Ihre Anwendung vor dem Start ordnungsgemäß funktioniert, sollten Sie folgende Schritte als allgemeine Vorgehensweise zum Debugging ausführen:

* Funktionalität und Leistung mit der Anwendungsversion der Vorschau überprüfen
* Funktionalität und Leistung mit der Produktionsversion der Anwendung überprüfen
* Validieren mit der JSON-Vorschau des Inhaltsfragment-Editors
* Inspect Sie JSON in der Clientanwendung, um zu prüfen, ob Probleme mit der Clientanwendung oder dem Versand auftreten
* Inspect Sie JSON mit GraphQL, um zu prüfen, ob Probleme im Zusammenhang mit zwischengespeicherten Inhalten oder AEM auftreten.

### Protokollieren eines Fehlers mit Unterstützung {#logging-a-bug-with-support}

Gehen Sie wie folgt vor, um einen Fehler beim Support effizient zu protokollieren, falls Sie weitere Unterstützung benötigen:

* Machen Sie ggf. Screenshots des Problems
* Dokument zur Reproduktion des Problems
* Dokument des Inhalts, mit dem das Problem wiedergegeben wird
* Melden Sie ein Problem mit der entsprechenden Priorität über das AEM Support-Portal an

## Wie geht es weiter {#what-is-next}

Nachdem Sie nun die AEM Journey zum kostenlosen Entwickler abgeschlossen haben, sollten Sie:

* Grundlegendes zur AEM Inhaltsreplikation und -zwischenspeicherung.
* Erfahren Sie, wie Sie die Werkzeuge konfigurieren, die für die Simulation erforderlich sind, gehen Sie live für Ihre kopflose Anwendung.
* Erfahren Sie, wie Sie Ihre Anwendung vor dem Start sichern und skalieren können.
* Verstehen Sie, wie Sie Leistungs- und Debugprobleme überwachen.

Sie sollten Ihre AEM kopflosen Journey fortsetzen, indem Sie sich das Dokument [Post Launch](post-launch.md) ansehen, in dem Sie lernen, wie Sie Ihr Headless-Erlebnis erhalten.

## Zusätzliche Ressourcen {#additional-resources}
