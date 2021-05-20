---
title: Wie Sie mit Ihrer Headless-Anwendung live gehen
description: In diesem Teil der AEM Headless-Entwickler-Journey erfahren Sie, wie Sie eine Headless-Anwendung live bereitstellen, indem Sie Ihren lokalen Code in Git übernehmen und für die CI/CD-Pipeline in Cloud Manager Git verschieben.
hide: true
hidefromtoc: true
index: false
exl-id: f79b5ada-8f59-4706-9f90-bc63301b2b7d
source-git-commit: bc717c544bd4f0449d358b831a5132f85fa85e86
workflow-type: tm+mt
source-wordcount: '1818'
ht-degree: 1%

---

# Wie Sie mit Ihrer Headless-Anwendung live gehen {#go-live}

>[!CAUTION]
>
>OUTDATED - Dieser Inhaltsentwurf wurde durch die neue [Headless-Entwickler-Journey-Dokumentation ersetzt.](/help/journey-headless/developer/overview.md)

In diesem Teil der [AEM Headless-Entwickler-Journey](overview.md) erfahren Sie, wie Sie eine Headless-Anwendung live bereitstellen, indem Sie Ihren lokalen Code in Git übernehmen und für die CI/CD-Pipeline in Cloud Manager Git verschieben.

## Die Geschichte bisher {#story-so-far}

Im vorherigen Dokument der AEM Headless-Journey [Aktualisierung Ihres Inhalts über AEM Assets-APIs](update-your-content.md) haben Sie erfahren, wie Sie Ihren vorhandenen Headless-Inhalt in AEM über die API aktualisieren können. Nun sollten Sie:

* Grundlegendes zur AEM Assets HTTP-API.

Dieser Artikel baut auf diesen Grundlagen auf, damit Sie verstehen, wie Sie Ihr eigenes AEM Headless-Projekt für die Live-Schaltung vorbereiten können.

## Vorgabe {#objective}

In diesem Dokument erhalten Sie Informationen zur AEM Headless-Publishing-Pipeline und zu den Leistungsaspekten, die Sie beachten müssen, bevor Sie mit Ihrer Anwendung live gehen.

* Erfahren Sie mehr über das AEM SDK und die erforderlichen Entwicklungs-Tools
* Richten Sie eine lokale Entwicklungslaufzeit ein, um Ihren Inhalt zu simulieren, bevor Sie live gehen
* Grundlagen zur AEM Inhaltsreplikation und Zwischenspeicherung
* Sichern und Skalieren der Anwendung vor Launch
* Überwachen von Leistungs- und Debug-Problemen

## Das AEM SDK {#the-aem-sdk}

Das AEM SDK wird zum Erstellen und Bereitstellen von benutzerdefiniertem Code verwendet. Es ist das Hauptwerkzeug, das Sie benötigen, um Ihre Headless-Anwendung zu entwickeln und zu testen, bevor Sie live gehen. Sie enthält die folgenden Artefakte:

* Die Schnellstart-JAR-Datei - eine ausführbare JAR-Datei, die sowohl zum Einrichten einer Autoren- als auch einer Veröffentlichungsinstanz verwendet werden kann
* Dispatcher Tools - das Dispatcher-Modul und seine Abhängigkeiten für Windows- und UNIX-basierte Systeme
* Java-API-JAR - Die Java-JAR-/Maven-Abhängigkeit, die alle zulässigen Java-APIs verfügbar macht, die für die Entwicklung mit AEM verwendet werden können
* Javadoc-JAR - die Javadocs für die Java-API-JAR

## Zusätzliche Entwicklungs-Tools {#additional-development-tools}

Zusätzlich zum AEM SDK benötigen Sie zusätzliche Tools, die die lokale Entwicklung und Prüfung von Code und Inhalt erleichtern:

* Java
* Git
* Apache Maven
* Die Node.js-Bibliothek
* Die IDE Ihrer Wahl

Da AEM eine Java-Anwendung ist, müssen Sie Java und das Java-SDK installieren, um die Entwicklung von AEM als Cloud Service zu unterstützen.

Git wird verwendet, um die Quellcodeverwaltung zu verwalten, die Änderungen in Cloud Manager einzuchecken und sie dann in einer Produktionsinstanz bereitzustellen.

AEM verwendet Apache Maven zum Erstellen von Projekten, die aus dem AEM Maven-Projektarchetyp generiert wurden. Alle wichtigen IDEs bieten Integrationsunterstützung für Maven.

Node.js ist eine JavaScript-Laufzeitumgebung, die zum Arbeiten mit den Frontend-Assets des Unterprojekts `ui.frontend` eines AEM verwendet wird. Node.js wird mit npm verteilt, dem De-facto-Paketmanager von Node.js, der zur Verwaltung von JavaScript-Abhängigkeiten verwendet wird.

## Komponenten eines AEM auf einen Blick {#components-of-an-aem-system-at-a-glance}

Als Nächstes sehen wir uns die Bestandteile einer AEM Umgebung an.

Eine vollständige AEM-Umgebung besteht aus einer Autoren-, Veröffentlichungs- und Dispatcher-Umgebung. Dieselben Komponenten werden zur Laufzeit der lokalen Entwicklung verfügbar gemacht, damit Sie Ihre Code- und Inhaltsvorschau vor der Live-Schaltung einfacher anzeigen können.

* **Der Autorendienst,** bei dem interne Benutzer Inhalte erstellen, verwalten und in der Vorschau anzeigen.

* **Der Veröffentlichungsdienst** gilt als &quot;Live&quot;-Umgebung und ist in der Regel die Aufgabe, mit der Endbenutzer interagieren. Inhalte werden nach der Bearbeitung und Anwendung im Autorendienst an den Veröffentlichungsdienst verteilt. Das häufigste Bereitstellungsmuster bei AEM Headless-Anwendungen besteht darin, die Produktionsversion der Anwendung mit einem AEM Publish-Dienst zu verbinden.

* **Der** Dispatcher ist ein statischer Webserver, der mit dem AEM Dispatcher-Modul erweitert wird. Er speichert durch die Veröffentlichungsinstanz generierte Webseiten zwischen, um die Leistung zu verbessern.

## Lokaler Entwicklungs-Workflow {#the-local-development-workflow}

Das lokale Entwicklungsprojekt basiert auf Apache Maven und verwendet Git für die Quellcodeverwaltung. Um das Projekt zu aktualisieren, können Entwickler ihre bevorzugte integrierte Entwicklungsumgebung wie Eclipse, Visual Studio Code oder IntelliJ verwenden.

Um Code- oder Inhaltsaktualisierungen zu testen, die von Ihrer Headless-Anwendung erfasst werden, müssen Sie die Aktualisierungen für die lokale AEM-Laufzeit bereitstellen, die lokale Instanzen der AEM-Autoren- und Veröffentlichungsdienste enthält.

Beachten Sie die Unterschiede zwischen den einzelnen Komponenten in der lokalen AEM-Laufzeit, da es wichtig ist, Ihre Aktualisierungen dort zu testen, wo sie am wichtigsten sind. Testen Sie beispielsweise Inhaltsaktualisierungen für Autor oder testen Sie neuen Code in der Veröffentlichungsinstanz.

In einem Produktionssystem sitzen ein Dispatcher und ein HTTP-Apache-Server immer vor einer AEM Veröffentlichungsinstanz. Sie bieten Caching- und Sicherheitsdienste für das AEM-System. Daher ist es von größter Bedeutung, Code- und Inhaltsaktualisierungen auch für den Dispatcher zu testen.

## Lokale Vorschau Ihres Codes und Inhalts mit der lokalen Entwicklungsumgebung {#previewing-your-code-and-content-locally-with-the-local-development-environment}

Um Ihr AEM Headless-Projekt auf den Start vorzubereiten, müssen Sie sicherstellen, dass alle Bestandteile Ihres Projekts gut funktionieren.

Dazu müssen Sie alles zusammenführen: Code, Inhalt und Konfiguration erstellen und in einer lokalen Entwicklungsumgebung testen, um live vorzugehen.

Die lokale Entwicklungsumgebung umfasst drei Hauptbereiche:

1. Das AEM-Projekt - enthält den gesamten benutzerdefinierten Code, die Konfiguration und den Inhalt, an dem die AEM-Entwickler arbeiten werden
1. Die lokale AEM Runtime - lokale Versionen der AEM Autoren- und Veröffentlichungsdienste, die zum Bereitstellen von Code aus dem AEM Projekt verwendet werden
1. Die lokale Dispatcher Runtime - eine lokale Version des Apache httpd-Webservers, der das Dispatcher-Modul enthält

Nachdem die lokale Entwicklungsumgebung eingerichtet wurde, können Sie die Bereitstellung von Inhalten für die React-Anwendung simulieren, indem Sie lokal einen statischen Knotenserver bereitstellen.

Weitere Informationen zum Einrichten einer lokalen Entwicklungsumgebung und allen Abhängigkeiten, die für die Inhaltsvorschau erforderlich sind, finden Sie in der [Dokumentation zur Produktionsbereitstellung](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/production-deployment.html?lang=en#prerequisites).

## Bereiten Sie Ihre AEM Headless-Anwendung für GoLive vor {#prepare-your-aem-headless-application-for-golive}

Jetzt ist es an der Zeit, Ihre AEM Headless App für den Start bereitzustellen, indem Sie die unten beschriebenen Best Practices befolgen.

### Sichern und skalieren Sie Ihre Headless-Anwendung vor Launch {#secure-and-scale-before-launch}

1. [Token-basierte Authentifizierung](/help/assets/content-fragments/graphql-authentication-content-fragments.md) mit Ihren GraphQL-Anforderungen konfigurieren
1. Konfigurieren Sie [Caching](/help/implementing/dispatcher/caching.md).

### Modellstruktur vs. GraphQL-Ausgabe {#structure-vs-output}

* Erstellen Sie keine Abfragen, die mehr als 15 KB JSON ausgeben (gzip-komprimiert). Lange JSON-Dateien sind ressourcenintensiv, damit die Clientanwendung analysiert werden kann.
* Vermeiden Sie mehr als fünf verschachtelte Ebenen von Fragmenthierarchien. Zusätzliche Ebenen erschweren es Inhaltsautoren, die Auswirkungen ihrer Änderungen zu berücksichtigen.
* Verwenden Sie Abfragen mit mehreren Objekten, anstatt Abfragen mit Abhängigkeitshierarchien innerhalb der Modelle zu modellieren. Dies ermöglicht eine langfristige Flexibilität bei der Neustrukturierung der JSON-Ausgabe, ohne dass viele Inhaltsänderungen erforderlich sind.

### Maximieren Sie das CDN Cache-Hit-Verhältnis {#maximize-cdn}

* Verwenden Sie keine direkten GraphQL-Abfragen, es sei denn, Sie fordern Live-Inhalte von der Oberfläche an.
   * Verwenden Sie nach Möglichkeit persistente Abfragen.
   * Stellen Sie CDN-TTL über 600 Sekunden bereit, damit das CDN sie zwischenspeichert.
   * AEM können die Auswirkungen einer Modelländerung auf vorhandene Abfragen berechnen.
* Teilen Sie JSON-Dateien/GraphQL-Abfragen zwischen niedriger und hoher Inhaltsänderungsrate auf, um den Client-Traffic zu CDN zu reduzieren und eine höhere TTL zuzuweisen. Dadurch wird das CDN minimiert, das die JSON-Datei mit dem Herkunftsserver erneut validiert.
* Um Inhalte aus dem CDN aktiv ungültig zu machen, verwenden Sie &quot;Soft Purge&quot;. Dadurch kann das CDN den Inhalt erneut herunterladen, ohne dass ein Cache fehlschlägt.

### Verbessern der Zeit zum Herunterladen von Headless Content {#improve-download-time}

* Stellen Sie sicher, dass HTTP-Clients HTTP/2 verwenden.
* Stellen Sie sicher, dass HTTP-Clients die Anfrage &quot;Accept Headers&quot;für gzip akzeptieren.
* Minimieren Sie die Anzahl der Domänen, die zum Hosten von JSON und referenzierten Artefakten verwendet werden.
* Nutzen Sie `Last-modified-since` , um Ressourcen zu aktualisieren.
* Verwenden Sie die `_reference`-Ausgabe in der JSON-Datei, um mit dem Herunterladen von Assets zu beginnen, ohne vollständige JSON-Dateien analysieren zu müssen.

## Bereitstellung für Produktion {#deploy-to-production}

Nachdem Sie sichergestellt haben, dass alles getestet wurde und ordnungsgemäß funktioniert, können Sie Codeaktualisierungen an ein [zentralisiertes Git-Repository in Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/setup-cloud-manager-git-integration.html) übertragen.

Nachdem die Aktualisierungen in Cloud Manager hochgeladen wurden, können sie mit der CI/CD-Pipeline von [Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html) AEM als Cloud Service bereitgestellt werden.

Sie können mit der Bereitstellung Ihres Codes beginnen, indem Sie die CI/CD-Pipeline von Cloud Manager nutzen, die ausführlich unter [hier](/help/implementing/deploying/overview.md) behandelt wird.

## Leistungsüberwachung {#performance-monitoring}

Damit Benutzer bei der Verwendung der AEM Headless-Anwendung das bestmögliche Erlebnis erhalten, müssen Sie die wichtigsten Leistungsmetriken überwachen, wie unten beschrieben:

* Vorschau- und Produktionsversionen der Anwendung überprüfen
* Überprüfen AEM Statusseiten für den aktuellen Status der Dienstverfügbarkeit
* Leistungsberichte aufrufen
   * Versandleistung
      * CDN-Leistung (schnell) - Anzahl der Aufrufe überprüfen, Cache-Rate, Fehlerraten und Nutzlasttraffic
      * Herkunftsserver - Anzahl der Aufrufe, Fehlerraten, CPU-Auslastung, Nutzlastverkehr
   * Autorenleistung
      * Anzahl der Benutzer, Anforderungen und Ladevorgänge überprüfen
* Auf Anwendungs- und Space-spezifische Leistungsberichte zugreifen
   * Sobald der Server eingerichtet ist, überprüfen Sie, ob die allgemeinen Metriken grün/orange/rot sind, und identifizieren Sie dann spezifische Anwendungsprobleme.
   * Öffnen Sie die oben genannten Berichte, filtern Sie sie jedoch nach der Anwendung oder dem Bereich (z. B. Photoshop-Desktop, Paywall).
   * [Splunk-Protokoll-](/help/implementing/developing/introduction/logging.md#splunk-logs) APIs verwenden, um auf Dienst- und Anwendungsleistung zuzugreifen
   * Wenden Sie sich an den Support, falls weitere Probleme auftreten.

## Fehlerbehebung {#troubleshooting}

### Debugging {#debugging}

Befolgen Sie diese Best Practices als allgemeinen Ansatz zum Debugging:

* Validieren der Funktionalität und Leistung mit der Vorschauversion der Anwendung
* Validieren der Funktionalität und Leistung mit der Produktionsversion der Anwendung
* Validieren Sie mit der [JSON-Vorschau](/help/assets/content-fragments/content-fragments-json-preview.md) des Inhaltsfragment-Editors.
* Inspect Sie die JSON-Datei in der Clientanwendung, um zu überprüfen, ob es Probleme mit der Clientanwendung oder dem Versand gibt.
* Inspect der JSON, die GraphQL verwendet, um zu überprüfen, ob Probleme im Zusammenhang mit zwischengespeicherten Inhalten oder AEM vorliegen

### Protokollieren eines Fehlers mit Unterstützung {#logging-a-bug-with-support}

Gehen Sie wie folgt vor, um einen Fehler effizient mit dem Support zu protokollieren, falls Sie weitere Unterstützung benötigen:

* Erstellen Sie bei Bedarf Screenshots des Problems.
* Dokumentieren einer Möglichkeit, das Problem zu reproduzieren
* Dokumentieren des Inhalts, mit dem das Problem reproduziert
* Melden Sie ein Problem über das AEM Support-Portal mit der Anwendungspriorität an.

## Die Journey endet - oder nicht? {#journey-ends}

Herzlichen Glückwunsch! Sie haben die AEM Headless Developer Journey abgeschlossen! Sie sollten jetzt Folgendes verstehen:

* Der Unterschied zwischen Headless- und Headful-Content-Bereitstellung.
* AEM Headless-Funktionen.
* Organisieren und AEM des Headless-Projekts.
* So erstellen Sie Headless-Inhalte in AEM.
* So rufen Sie Headless-Inhalte in AEM ab und aktualisieren sie.
* Wie man mit einem AEM Headless-Projekt live geht.
* Was macht man nach der Live-Schaltung?

## Zusätzliche Ressourcen {#additional-resources}

* [Eine Übersicht über die Bereitstellung in AEM als Cloud Service](/help/implementing/deploying/overview.md)
* [Das AEM as a Cloud Service-SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md)
* [Lokale AEM einrichten](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html)
* [Verwenden von Cloud Manager zum Bereitstellen Ihres Codes](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html)
* [Integrieren Sie das Cloud Manager-Git-Repository in ein externes Git-Repository und stellen Sie ein Projekt bereit, das als Cloud Service AEM wird.](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/devops/deploy-code.html)