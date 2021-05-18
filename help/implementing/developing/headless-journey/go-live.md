---
title: So gehen Sie mit Ihrer Headless-Anwendung live
description: In diesem Teil der AEM Headless Developer-Journey erfahren Sie, wie Sie eine kostenlose Anwendung live bereitstellen, indem Sie Ihren lokalen Code in Git übernehmen und für die CI/CD-Pipeline auf Cloud Manager Git verschieben.
hide: true
hidefromtoc: true
index: false
exl-id: f79b5ada-8f59-4706-9f90-bc63301b2b7d
source-git-commit: 4c743eede23f09f285d9da84b149226f7288fcc3
workflow-type: tm+mt
source-wordcount: '1886'
ht-degree: 1%

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

* Erfahren Sie mehr über das AEM SDK und die erforderlichen Entwicklungswerkzeuge
* Richten Sie eine lokale Entwicklungs-Laufzeit ein, um Ihre Inhalte zu simulieren, bevor Sie live gehen
* Grundlagen zur AEM Content-Replikation und -Zwischenspeicherung
* Sichern und skalieren Sie Ihre Anwendung vor dem Start
* Leistungs- und Debugprobleme überwachen

## Das AEM SDK {#the-aem-sdk}

Das AEM SDK wird zum Erstellen und Bereitstellen von benutzerspezifischem Code verwendet. Es ist das Hauptwerkzeug, das Sie benötigen, um Ihre kostenlose Anwendung zu entwickeln und zu testen, bevor Sie live gehen. Es enthält die folgenden Artefakte:

* Die Schnellstart-JAR-Datei - eine ausführbare JAR-Datei, mit der sowohl eine Autoren- als auch eine Veröffentlichungsinstanz eingerichtet werden kann
* Dispatcher-Tools - das Dispatcher-Modul und seine Abhängigkeiten für Windows- und UNIX-basierte Systeme
* Java-API-JAR - Die Java-Jar-/Maven-Abhängigkeit, die alle zulässigen Java-APIs verfügbar macht, die für die Entwicklung gegen AEM verwendet werden können
* Javadoc jar - die JavaScript-Dateien für die Java API-JAR

## Zusätzliche Entwicklungstools {#additional-development-tools}

Zusätzlich zum AEM SDK benötigen Sie zusätzliche Werkzeuge, mit denen Sie Code und Inhalte lokal entwickeln und testen können:

* Java
* Git
* Apache Maven
* Die Node.js-Bibliothek
* Die IDE Ihrer Wahl

Da AEM eine Java-Anwendung ist, müssen Sie Java und das Java-SDK installieren, um die Entwicklung von AEM als Cloud Service zu unterstützen.

Git wird verwendet, um Quellcodeverwaltung zu verwalten, die Änderungen in Cloud Manager einzuchecken und sie dann in einer Produktionsinstanz bereitzustellen.

AEM nutzt Apache Maven zum Erstellen von Projekten, die aus dem AEM Maven Project Archetyp generiert wurden. Alle wichtigen IDEs bieten Integrationsunterstützung für Maven.

Node.js ist eine JavaScript-Laufzeitumgebung, die zum Arbeiten mit den Front-End-Assets des Unterprojekts `ui.frontend` eines AEM verwendet wird. Node.js wird mit npm verteilt, ist der De-facto-Paketmanager von Node.js, der zum Verwalten von JavaScript-Abhängigkeiten verwendet wird.

## Komponenten eines AEM Systems auf einen Blick {#components-of-an-aem-system-at-a-glance}

Als Nächstes schauen wir uns die Bestandteile einer AEM Umgebung an.

Eine vollständige AEM Umgebung besteht aus einem Autor, einem Veröffentlichen und einem Dispatcher. Diese Komponenten werden in der lokalen Entwicklungslaufzeit bereitgestellt, um Ihnen die Vorschau Ihres Codes und Inhalts vor der Live-Schaltung zu erleichtern.

* **Der Authoring-** Dienst, bei dem interne Benutzer Inhalte erstellen, verwalten und Vorschauen erstellen.

* **Der Publish-** Dienst wird als &quot;Live&quot;-Umgebung betrachtet und ist in der Regel das, mit dem Endbenutzer interagieren. Nach der Bearbeitung und Genehmigung im Autorendienst werden Inhalte an den Veröffentlichungsdienst verteilt. Das häufigste Bereitstellungsmuster bei AEM kostenlosen Anwendungen besteht darin, dass die Produktionsversion der Anwendung mit einem AEM Publish-Dienst verbunden wird.

* **Der** Dispatcher ist ein statischer Webserver, der mit dem AEM Dispatcher-Modul erweitert wird. Er speichert durch die Veröffentlichungsinstanz generierte Webseiten zwischen, um die Leistung zu verbessern.

## Lokaler Entwicklungsarbeitsablauf {#the-local-development-workflow}

Das lokale Entwicklungsprojekt basiert auf Apache Maven und nutzt Git zur Quellcodeverwaltung. Um das Projekt zu aktualisieren, können Entwickler unter anderem ihre bevorzugte integrierte Entwicklungs-Umgebung wie Eclipse, Visual Studio Code oder IntelliJ verwenden.

Zum Testen von Code- oder Inhaltsaktualisierungen, die von Ihrer Anwendung ohne Kopfdaten erfasst werden, müssen Sie die Updates für die lokale AEM bereitstellen, die lokale Instanzen des AEM-Autors und der Veröffentlichungsdienste enthält.

Achten Sie darauf, die Unterschiede zwischen den einzelnen Komponenten in der lokalen AEM zu beachten, da es wichtig ist, Ihre Updates dort zu testen, wo sie am wichtigsten sind. Testen Sie beispielsweise Inhaltsaktualisierungen beim Autor oder testen Sie neuen Code in der Veröffentlichungsinstanz.

In einem Produktionssystem sitzen ein Dispatcher und ein HTTP-Apache-Server immer vor einer AEM Veröffentlichungsinstanz. Sie bieten Caching- und Sicherheitsdienste für das AEM System, daher ist es von größter Bedeutung, auch Code- und Inhaltsupdates für den Dispatcher zu testen.

## Lokale Vorschau von Code und Inhalt mit der Umgebung für lokale Entwicklung {#previewing-your-code-and-content-locally-with-the-local-development-environment}

Um Ihr AEM freizügiges Projekt auf den Start vorzubereiten, müssen Sie sicherstellen, dass alle Bestandteile Ihres Projekts gut funktionieren.

Dazu müssen Sie alles zusammensetzen: Code, Inhalt und Konfiguration und testen Sie es in einer lokalen Entwicklungs-Umgebung für die Live-Bereitschaft.

Die örtliche Umgebung umfasst drei Schwerpunkte:

1. Das AEM Projekt - enthält den gesamten benutzerspezifischen Code, die Konfiguration und den Inhalt, an dem die AEM Entwickler arbeiten werden
1. Die lokale AEM Runtime - lokale Versionen der AEM Autoren- und Veröffentlichungsdienste, die zum Bereitstellen des Codes aus dem AEM Projekt verwendet werden
1. Die lokale Dispatcher-Laufzeit - eine lokale Version des Apache htttpd-Webservers, der das Dispatcher-Modul enthält

Nachdem die lokale Entwicklungs-Umgebung eingerichtet wurde, können Sie Inhalte simulieren, die für die React-App bereitgestellt werden, indem Sie einen lokalen statischen Node-Server bereitstellen.

Eine detaillierte Übersicht über die Einrichtung einer lokalen Entwicklungsumgebung und alle Abhängigkeiten, die für die Vorschau von Inhalten erforderlich sind, finden Sie in der [Produktionsbereitstellungsdokumentation](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/production-deployment.html?lang=en#prerequisites).

## Bereiten Sie Ihre AEM Headless-Anwendung für Go-Live {#prepare-your-aem-headless-application-for-golive} vor

Jetzt ist es an der Zeit, Ihre AEM kostenlose Anwendung für den Start bereitzustellen, indem Sie die unten beschriebenen Best Practices befolgen.

### Sichern und skalieren Sie Ihre Headless-Anwendung vor dem Start von {#secure-and-scale-before-launch}

1. [Token-basierte Authentifizierung](/help/assets/content-fragments/graphql-authentication-content-fragments.md) mit Ihren GraphQL-Anforderungen konfigurieren
1. Konfigurieren Sie [Zwischenspeicherung](/help/implementing/dispatcher/caching.md).

### Modellstruktur vs. GraphQL-Ausgabe {#structure-vs-output}

* Vermeiden Sie das Erstellen von Abfragen, die mehr als 15 KB JSON ausgeben (gzip-komprimiert). Lange JSON-Dateien sind ressourcenintensiv, damit die Clientanwendung analysiert werden kann.
* Vermeiden Sie mehr als fünf verschachtelte Ebenen von Fragmenthierarchien. Zusätzliche Ebenen erschweren es Inhaltserstellern, die Auswirkungen ihrer Änderungen zu berücksichtigen.
* Verwenden Sie Abfragen mit mehreren Objekten, anstatt Abfragen mit Abhängigkeitshierarchien innerhalb der Modelle zu modellieren. Dadurch erhalten Sie mehr langfristige Flexibilität bei der Neustrukturierung der JSON-Ausgabe, ohne dass eine Menge Inhaltsänderungen vorgenommen werden müssen.

### CDN-Cache-Trefferverhältnis maximieren {#maximize-cdn}

* Verwenden Sie keine direkten GraphQL-Abfragen, es sei denn, Sie fordern Live-Inhalte von der Oberfläche an.
   * Verwenden Sie nach Möglichkeit beständige Abfragen.
   * Geben Sie CDN-TTL über 600 Sekunden an, damit das CDN sie zwischenspeichert.
   * AEM können die Auswirkungen einer Modelländerung auf bestehende Abfragen berechnen.
* Teilen Sie JSON-Dateien/GraphQL-Abfragen zwischen niedriger und hoher Inhaltsänderungsrate, um den Client-Traffic zu CDN zu reduzieren und höhere TTL zuzuweisen. Dadurch wird das CDN, das JSON mit dem Herkunft-Server erneut validiert, minimiert.
* Verwenden Sie Soft Purge, um Inhalte aus dem CDN aktiv für ungültig zu erklären. Dadurch kann das CDN den Inhalt erneut herunterladen, ohne dass ein Cache fehlschlägt.

### Verbessern Sie die Zeit zum Herunterladen von Headless Content {#improve-download-time}

* Stellen Sie sicher, dass HTTP-Clients HTTP/2 verwenden.
* Vergewissern Sie sich, dass HTTP-Clients die Header-Anforderung für gzip akzeptieren.
* Minimieren Sie die Anzahl der Domänen, die zum Hosten von JSON und referenzierten Artefakten verwendet werden.
* Nutzen Sie `Last-modified-since`, um Ressourcen zu aktualisieren.
* Verwenden Sie `_reference`-Ausgabe in der JSON-Datei, um Beginn beim Herunterladen von Assets zu verwenden, ohne vollständige JSON-Dateien analysieren zu müssen.

## Bereitstellung für Produktion {#deploy-to-production}

Nachdem Sie sichergestellt haben, dass alles getestet wurde und ordnungsgemäß funktioniert, können Sie Codeaktualisierungen an ein [zentralisiertes Git-Repository in Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/setup-cloud-manager-git-integration.html) übertragen.

Nachdem die Updates in Cloud Manager hochgeladen wurden, können sie mit der CI/CD-Pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html) von Cloud Manager AEM als Cloud Service bereitgestellt werden.[

Sie können Beginn bei der Codebereitstellung mit der Cloud Manager CI/CD-Pipeline erstellen, die ausführlich unter [hier](/help/implementing/deploying/overview.md) behandelt wird.

## Leistungsüberwachung {#performance-monitoring}

Damit Benutzer bei der Verwendung der AEM Anwendung ohne Kopfdaten das bestmögliche Erlebnis erhalten, müssen Sie die wichtigsten Leistungsmetriken wie unten beschrieben überwachen:

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

Beachten Sie beim Debugging folgende Best Practices:

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

## Die Journey endet - oder nicht? {#journey-ends}

Herzlichen Glückwunsch! Sie haben die AEM Headless Developer Journey abgeschlossen! Sie sollten jetzt Folgendes verstehen:

* Der Unterschied zwischen dem Versand für kostenlose und kostenlose Inhalte.
* AEM Funktionen ohne Kopf.
* So organisieren und AEM Headless-Projekt.
* So erstellen Sie kostenlose Inhalte in AEM.
* So können Sie kostenlose Inhalte in AEM abrufen und aktualisieren.
* Wie man mit einem AEM Headless-Projekt live geht.
* Was macht man nach dem Go-Live?

## Zusätzliche Ressourcen {#additional-resources}

* [Übersicht über die Bereitstellung auf AEM als Cloud Service](/help/implementing/deploying/overview.md)
* [Das AEM as a Cloud Service-SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md)
* [Lokale AEM Umgebung einrichten](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html)
* [Verwenden Sie Cloud Manager, um Ihren Code bereitzustellen](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html)
* [Integrieren Sie das Cloud Manager-Git-Repository in ein externes Git-Repository und stellen Sie ein Projekt bereit, um es als Cloud Service zu AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/devops/deploy-code.html)