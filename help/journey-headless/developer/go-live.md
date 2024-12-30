---
title: Live-Schalten Ihres Headless-Programms
description: In diesem Teil der AEM Headless-Entwickler-Tour erfahren Sie, wie Sie ein Headless-Programm live bereitstellen, indem Sie Ihren lokalen Code in Git in das Git-Repository von Cloud Manager für die CI/CD-Pipeline verschieben.
exl-id: 81616e31-764b-44b0-94a6-3ae24ce56bf6
solution: Experience Manager
feature: Headless, Content Fragments,GraphQL API
role: Admin, Architect, Developer
source-git-commit: 6719e0bcaa175081faa8ddf6803314bc478099d7
workflow-type: tm+mt
source-wordcount: '1071'
ht-degree: 100%

---

# Live-Schalten Ihres Headless-Programms {#go-live}

In diesem Teil der [AEM Headless-Entwickler-Tour](overview.md) erfahren Sie, wie Sie ein Headless-Programm live bereitstellen, indem Sie Ihren lokalen Code in Git in das Git-Repository von Cloud Manager für die CI/CD-Pipeline verschieben.

## Die bisherige Entwicklung {#story-so-far}

Im vorherigen Dokument der AEM Headless-Tour, [So stellen Sie alles zusammen – Ihre Mobile App und Ihren Inhalt in AEM Headless](put-it-all-together.md), haben Sie gelernt, wie Sie mit den AEM-Entwicklungs-Tools alle Facetten Ihres Projekts zusammenführen können.

Dieser Artikel baut auf diesen Grundlagen auf, damit Sie verstehen, wie Sie Ihr eigenes AEM Headless-Projekt für die Live-Schaltung vorbereiten können.

## Ziel {#objective}

In diesem Dokument erhalten Sie Informationen zur AEM Headless-Veröffentlichungs-Pipeline und zu den Leistungsaspekten, die Sie vor der Live-Schaltung Ihres Programms beachten müssen.

* Sichern und skalieren Sie Ihr Programm vor dem Launch.
* Überwachen Sie Performance- und Debugging-Probleme.

<!-- Alexandru: this is a bit redundant, to review again later

## Prepare your AEM Headless Application for Go-Live {#prepare-your-aem-headless-application-for-golive}

-->
Befolgen Sie die unten beschriebenen Best Practices, um Ihr AEM Headless-Programm für den Launch vorzubereiten.

## Sichern und Skalieren Ihres Headless-Programms vor dem Launch {#secure-and-scale-before-launch}

1. Konfigurieren Sie die [Token-basierte Authentifizierung](/help/headless/security/authentication.md) mit Ihren GraphQL-Anfragen.
1. Konfigurieren Sie das [Caching](/help/implementing/dispatcher/caching.md).

## Modellstruktur und GraphQL-Ausgabe im Vergleich {#structure-vs-output}

* Erstellen Sie möglichst keine Abfragen, die JSON-Dateien mit einer Größe von mehr als 15 KB ausgeben (gzip-komprimiert). Die Analyse großer JSON-Dateien ist für Client-Programme ressourcenintensiv.
* Vermeiden Sie mehr als fünf verschachtelte Ebenen in Fragmenthierarchien. Zusätzliche Ebenen erschweren es Inhaltsautoren, die Auswirkungen ihrer Änderungen zu berücksichtigen.
* Verwenden Sie Abfragen mit mehreren Objekten, anstatt Abfragen mit Abhängigkeitshierarchien innerhalb der Modelle zu modellieren. Dies ermöglicht eine langfristigere Flexibilität bei der Neustrukturierung der JSON-Ausgabe, ohne dass viele Inhaltsänderungen erforderlich sind.

## Maximieren der CDN-Cache-Trefferquote {#maximize-cdn}

* Verwenden Sie keine direkten GraphQL-Abfragen, es sei denn, Sie fordern Live-Inhalte von der Oberfläche an.
   * Verwenden Sie nach Möglichkeit persistente Abfragen.
   * Geben Sie eine CDN-TTL von mehr als 600 Sekunden an, damit das CDN sie zwischenspeichert.
   * AEM kann die Auswirkungen einer Modelländerung auf vorhandene Abfragen berechnen.
* Teilen Sie JSON-Dateien/GraphQL-Abfragen nach niedriger und hoher Inhaltsänderungsrate auf, um den Client-Traffic zum CDN zu reduzieren und eine längere TTL zuzuweisen. Dies minimiert den Aufwand für das CDN, die JSON-Dateien beim Ursprungs-Server erneut zu validieren.
* Inhalte aus dem CDN können Sie aktiv per Soft Purge ungültig machen. Dadurch kann das CDN die Inhalte erneut herunterladen, ohne dass es zu Cache-Fehlern kommt.

## Verkürzen der Download-Zeit für Headless-Content {#improve-download-time}

* Stellen Sie sicher, dass HTTP-Clients HTTP/2 verwenden.
* Stellen Sie sicher, dass HTTP-Clients Header-Anfragen für gzip akzeptieren.
* Minimieren Sie die Anzahl der Domains, die zum Hosten von JSON und referenzierten Artefakten verwendet werden.
* Nutzen Sie `Last-modified-since`, um Ressourcen zu aktualisieren.
* Verwenden Sie die `_reference`-Ausgabe in der JSON-Datei, um mit dem Herunterladen von Assets zu beginnen, ohne vollständige JSON-Dateien analysieren zu müssen.

## Bereitstellung für Produktion {#deploy-to-production}

Nachdem Sie sichergestellt haben, dass alles getestet wurde und ordnungsgemäß funktioniert, können Sie Code-Aktualisierungen an ein [zentralisiertes Git-Repository in Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/setup-cloud-manager-git-integration.html?lang=de) übertragen.

Nachdem die Aktualisierungen in Cloud Manager hochgeladen wurden, können sie mit der [CI/CD-Pipeline von Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html?lang=de) in AEM as a Cloud Service bereitgestellt werden.

Sie können mit der Bereitstellung Ihres Codes beginnen, indem Sie die CI/CD-Pipeline von Cloud Manager nutzen, die ausführlich unter [Bereitstellen von Inhaltspaketen über Cloud Manager und Package Manager](/help/implementing/deploying/overview.md) erörtert wird.

## Leistungsüberwachung {#performance-monitoring}

Damit Benutzerinnen und Benutzern bei der Nutzung des AEM Headless-Programms das bestmögliche Erlebnis geboten wird, müssen Sie die wichtigsten Performance-Metriken überwachen, wie nachfolgend beschrieben:

* Validieren der Vorschau- und Produktionsversionen des Programms
* Prüfen der AEM-Statusseiten auf den aktuellen Status der Service-Verfügbarkeit
* Abrufen von Performance-Berichten
   * Bereitstellungs-Performance
      * CDN-Performance (Fastly) – Überprüfen der Anzahl der Aufrufe, Cache-Rate, Fehlerquoten und Payload-Traffic
      * Urspungs-Server – Anzahl der Aufrufe, Fehlerquoten, CPU-Auslastung, Payload-Traffic
   * Authoring-Performance
      * Überprüfen der Anzahl der Anwender, Anfragen sowie der Auslastung
* Abrufen programm- und speicherplatzspezifischer Performance-Berichte
   * Prüfen, ob die allgemeinen Metriken grün/orange/rot gekennzeichnet sind, sobald der Server hochgefahren ist, um anschließend spezifische Programmprobleme zu identifizieren
   * Öffnen der oben genannten Berichte, jedoch gefiltert nach Anwendung oder Speicherplatz. (z. B. Desktop-Version von Photoshop, Paywall).
   * Verwenden von Splunk-Protokoll-APIs, um Performance-Berichte zu Services und Programmen abzurufen
   * Wenden Sie sich an den Support, falls weitere Probleme auftreten.

## Fehlerbehebung {#troubleshooting}

### Debugging {#debugging}

Befolgen Sie die folgenden Best Practices als allgemeinen Debugging-Ansatz:

* Validieren der Funktionalität und Performance mit der Vorschauversion des Programms
* Validieren der Funktionalität und Performance mit der Produktionsversion des Programms
* Validieren mit der JSON-Vorschau des Inhaltsfragment-Editors
* Überprüfen der JSON-Dateien im Client-Programm, um Probleme im Programm oder bei der Bereitstellung festzustellen
* Überprüfen der JSON-Dateien, die GraphQL verwenden, um mögliche Probleme im Zusammenhang mit zwischengespeicherten Inhalten oder AEM festzustellen

### Protokollieren eines Fehlers beim Support {#logging-a-bug-with-support}

Führen Sie Folgendes aus, um einen Fehler effizient beim Support zu protokollieren, falls Sie weitere Unterstützung benötigen:

* Erstellen Sie ggf. Screenshots zum Problem.
* Dokumentieren Sie eine Methode, das Problem zu reproduzieren.
* Dokumentieren Sie, mit welchen Inhalten sich das Problem reproduzieren lässt.
* Protokollieren Sie das Problem über das AEM-Support-Portal mit der entsprechenden Priorität.

## Die Tour ist (fast) zu Ende {#journey-ends}

Herzlichen Glückwunsch! Sie haben die AEM Headless-Entwickler-Tour abgeschlossen! Sie sollten jetzt mit Folgendem vertraut sein:

* Unterschied zwischen Headless- und Headful-Inhaltsbereitstellung
* AEM Headless-Funktionen
* Organisieren eines AEM-Headless-Projekts
* Erstellen von Headless-Inhalten in AEM
* Abrufen und Aktualisieren von Headless-Inhalten in AEM
* Live-Schaltung mit einem AEM Headless-Projekt
* Wie geht es nach der Live-Schaltung weiter?

Sie haben entweder bereits Ihr erstes AEM Headless-Projekt gestartet oder verfügen nun über alle erforderlichen Kenntnisse. Gute Arbeit!

### Erkunden von Single Page Applications {#explore-spa}

Die Headless-Stores in AEM müssen hier jedoch nicht enden. Im Abschnitt mit den [ersten Schritten der AEM Headless-Entwickler-Tour](getting-started.md#integration-levels) haben wir kurz besprochen, inwiefern AEM nicht nur Headless-Bereitstellungen und herkömmliche Full-Stack-Modelle unterstützt, sondern auch Hybridmodelle unterstützen kann, die die Vorteile beider Modelle kombinieren.

Wenn Sie diese Flexibilität für Ihr Projekt benötigen, fahren Sie mit dem optionalen, zusätzlichen Teil der AEM Headless-Entwickler-Tour fort: [Erstellen von Single Page Applications (SPAs) mit AEM](create-spa.md).

## Zusätzliche Ressourcen {#additional-resources}

* [Einführung in AEM als Headless-CMS](/help/headless/introduction.md)
* [AEM-Entwicklerportal](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html?lang=de)
* [Headless-Tutorials für AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html?lang=de)
* [Ein Überblick über das Bereitstellen für AEM as a Cloud Service](/help/implementing/deploying/overview.md)
* [Verwenden von Cloud Manager zur Bereitstellung von Code](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html?lang=de)
* [Integrieren des Cloud Manager-Git-Repositorys mit einem externen Git-Repository und Bereitstellen eines Projekts in AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/devops/deploy-code.html?lang=de)
