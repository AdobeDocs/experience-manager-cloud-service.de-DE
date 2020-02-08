---
title: Einführung in die Architektur von Adobe Experience Manager als Cloud-Dienst
description: 'Einführung in die Architektur von Adobe Experience Manager als Cloud-Dienst. '
translation-type: tm+mt
source-git-commit: 5a846d34ee094e7d2f7fc71dbeef65f3fa58e86c

---


# Einführung in die Architektur von Adobe Experience Manager als Cloud-Dienst {#an-introduction-to-the-architecture-adobe-experience-manager-as-a-cloud-service}

Adobe Experience Manager (AEM) als Cloud-Dienst hat zu Änderungen an der Architektur geführt.

## Skalierung {#scaling}

AEM als Cloud-Dienst verfügt jetzt über:

* Eine dynamische Architektur mit einer variablen Anzahl von AEM-Bildern.

![Dynamische](assets/concepts-01.png "ArchitekturDynamische Architektur")

Diese Architektur:

* Wird basierend auf dem *tatsächlichen* Traffic und der *tatsächlichen* Aktivität skaliert.

* Enthält einzelne Instanzen, die nur bei Bedarf ausgeführt werden.

* Verwendet modulare Anwendungen.

* Enthält einen Autorencluster als Standard; Dadurch werden Ausfallzeiten für Wartungsaufgaben vermieden.

Dies ermöglicht die automatische Skalierung für verschiedene Verwendungsmuster:

![Automatische Skalierung für verschiedene](assets/concepts-02.png "VerwendungsmusterAutomatische Skalierung für unterschiedliche Verwendungsmuster")

Um dies zu erreichen, werden alle Instanzen von AEM als Cloud-Dienst gleich erstellt, wobei jede Instanz dieselben Merkmale wie die Standardgröße aufweist, was die Anzahl der Knoten, den zugewiesenen Speicher und die zugewiesene Rechenkapazität betrifft.

AEM als Cloud-Dienst basiert auf der Verwendung einer Orchestrierung, die:

* Überwachen Sie ständig den Status des Dienstes.

* Dynamische Skalierung der einzelnen Dienstinstanzen entsprechend den tatsächlichen Anforderungen; entweder nach oben oder unten skalieren.

Dieser Knoten:

* Gilt für die Anzahl der Knoten, die Speichermenge und die zugewiesene CPU-Kapazität auf jedem Knoten.

* Ermöglicht AEM als Cloud-Dienst, Ihren Traffic-Mustern bei deren Änderung Rechnung zu tragen.

Die Skalierung von Instanzen pro Mandant des Dienstes kann automatisch oder manuell auf zwei Achsen erfolgen:

* Vertikal: zugewiesener Arbeitsspeicher und CPU-Kapazität kann für eine feste Anzahl von Knoten hoch- oder herunterskaliert werden.

* Horizontal: die Anzahl der Knoten für einen bestimmten Dienst kann erhöht oder verringert werden.

## Umgebungen {#environments}

>[!NOTE]
>
> Weitere Informationen finden Sie unter [Bereitstellen - Runmodi](/help/implementing/deploying/overview.md#runmodes)

AEM als Cloud-Dienst wird als einzelne Instanzen bereitgestellt, wobei jede Instanz eine vollständige AEM-Umgebung darstellt. Es gibt vier Arten von Umgebungen, die mit AEM als Cloud-Dienst verfügbar sind:

* **Produktionsumgebung**: die Anwendungen für die Geschäftspraktiker.

* **Stage-Umgebung**: ist immer an eine einzige Produktionsumgebung in einer 1:1-Beziehung gekoppelt. Die stage-Umgebung wird für verschiedene Leistungs- und Qualitätstests verwendet, bevor Änderungen an der Anwendung in die Produktionsumgebung verschoben werden.

* **Entwicklungsumgebung**: ermöglicht Entwicklern die Implementierung von AEM-Anwendungen unter denselben Laufzeitbedingungen wie die stage- und production-Umgebungen.

* **Demonstrationsumgebung**: kann für Evaluierungs-, Demonstrations-, Prototyping- und Schulungszwecke verwendet werden.

Die Entwicklungs- und Demonstrationsumgebungen werden häufig als *Nicht-Produktionsumgebungen* bezeichnet.

## Programme {#programs}

Jedes neue AEM-Projekt ist immer an genau eine bestimmte Codebasis gebunden, in der Sie sowohl Konfigurations- als auch benutzerdefinierten Code für Ihr Projekt speichern können. Diese Informationen werden in einem Code-Repository gespeichert, auf das über die üblichen Git-Clients zugegriffen werden kann und die Ihnen zum Zeitpunkt der Erstellung neuer Programme zur Verfügung gestellt werden.

Ein AEM-Programm ist der Container, der Folgendes enthält:

|  Programmelement |  Nummer |
|--- |--- |
| Code-Repository (Git) |  1 |
| Grundlinienbild (Sites oder Assets) |  1 |
| Einstellung für Phase und Produktionsumgebung (1:1) | 0 oder 1 |
| Nicht-Produktionsumgebungen (Entwicklung oder Demonstration) | 0 bis N |
| Pipeline für jede Umgebung | 0 oder 1 |

Für AEM als Cloud-Dienst stehen zunächst zwei Arten von Programmen zur Verfügung:

* AEM Cloud-Sitedienst

* AEM Cloud Assets-Dienst

Beide ermöglichen den Zugriff auf eine Reihe von Funktionen. Die Autorenebene enthält alle Sites und Assets-Funktionen für alle Programme, aber die Assets-Programme haben standardmäßig keine Veröffentlichungsstufe.

## Laufzeitarchitektur {#runtime-architecture}

Es gibt verschiedene Hauptkomponenten dieser neuen Architektur:

<!--- needs reworking -->

![AEM as a Cloud Service - Runtime](assets/concepts-03.png "ArchitectureAEM as a Cloud Service - Runtime Architecture")

* Für AEM-Sites als Cloud-Dienst:

   * Es gibt weiterhin das Konzept einer Authoring-Ebene und einer Veröffentlichungsstufe für jede Umgebung (auf hoher Ebene).

   * Die Autorenebene besteht aus zwei oder mehr Knoten in einem Cluster mit nur einem Autor. Die Skalierung erfolgt automatisch, je nach Autorenaktivität.

      * Inhaltsersteller/Ersteller melden sich auf der AEM-Autorenebene an, um Inhalte zu erstellen, zu bearbeiten und zu verwalten.

      * Die Anmeldung bei der Autorenebene wird von Adobe Identity Management Services (IMS) verwaltet.

      * Die Integration und Verarbeitung von Assets erfolgt über einen dedizierten Assets Compute Service.
   * Die Veröffentlichungsstufe besteht aus zwei oder mehr Knoten in einer einzelnen Veröffentlichungsfarm: sie können unabhängig voneinander arbeiten. Jeder Knoten besteht aus einem AEM-Herausgeber und einem Webserver, der mit dem AEM Dispatcher-Modul ausgestattet ist. Die Skalierung erfolgt automatisch entsprechend den Anforderungen des Site-Traffics.

      * Endbenutzer oder Site-Besucher besuchen die Website über den AEM Publish Service.


* Für AEM Assets als Cloud-Dienst:

   * Die Architektur umfasst nur eine Authoring-Umgebung.

* Sowohl die Autorenebene als auch die Veröffentlichungsstufe lesen und halten Inhalte von/zu einem Content Repository Service bestehen.

   * Die Veröffentlichungsstufe liest nur Inhalte aus der Persistenzebene.

   * Die Autorenebene liest und schreibt Inhalte aus und in die Persistenzebene.

   * Der Blockspeicher wird für die Veröffentlichungs- und die Autorenebene freigegeben. Dateien nicht *verschoben* werden.

   * Wenn Inhalte von der Autorenebene genehmigt werden, ist dies ein Hinweis darauf, dass sie aktiviert werden können und daher in die Persistenzebene der Veröffentlichungsstufe verschoben werden. Dies geschieht über den Replication Service, eine Middleware-Pipeline. Diese Pipeline empfängt den neuen Inhalt, wobei die einzelnen Veröffentlichungsdienstknoten den Inhalt abonnieren, der an die Pipeline gesendet wird.

      >[!NOTE]
      >
      >For more details see [Replication](/help/operations/replication.md).

   * Entwickler und Administratoren verwalten AEM als Cloud-Service-Anwendung mit einem Dienst für kontinuierliche Integration/kontinuierliche Bereitstellung (CI/CD), der über den [Cloud Manager](/help/overview/what-is-new-and-different.md#cloud-manager)bereitgestellt wird. Dazu gehören Code- und Konfigurationsbereitstellungen unter Verwendung der CI/CD-Pipeline des Cloud Manager. Alles, was mit Überwachung, Wartung und Fehlerbehebung zu tun hat (z. B. Protokolldateien), wird Kunden in Cloud Manager bereitgestellt.

   * Der Zugriff auf die Ebenen für Autor und Veröffentlichung erfolgt immer über einen Lastenausgleich. Dies ist stets auf dem neuesten Stand mit den aktiven Knoten in den einzelnen Stufen.

   * Für die Veröffentlichungsstufe ist auch ein CDN-Dienst (Continuous Delivery Network) als erster Einstiegspunkt verfügbar.

* Bei Demonstrationsinstanzen von AEM als Cloud-Dienst wird die Architektur auf einen einzelnen Autorenknoten vereinfacht. Sie weist daher nicht alle Merkmale der Standardisierung, der Stage- oder Produktionsumgebung auf. Dies bedeutet auch, dass es einige Ausfallzeiten geben kann und dass es keine Unterstützung für Sicherungs-/Wiederherstellungsvorgänge gibt.

## Bereitstellungsarchitektur {#deployment-architecture}

Cloud Manager verwaltet alle Aktualisierungen der AEM-Instanzen als Cloud-Dienst. Es ist obligatorisch, da nur auf diese Weise die Kundenanwendung erstellt, getestet und bereitgestellt werden kann, und zwar sowohl für den Autor- als auch für den Veröffentlichungsstatus. Diese Updates können von Adobe, wenn eine neue Version des AEM Cloud-Dienstes bereit ist, oder vom Kunden ausgelöst werden, wenn eine neue Version der Anwendung bereit ist.

Technisch gesehen wird dies aufgrund des Konzepts einer Bereitstellungspipeline in Verbindung mit jeder Umgebung innerhalb eines Programms umgesetzt. Wenn eine Cloud Manager-Pipeline ausgeführt wird, wird eine neue Version der Kundenanwendung erstellt, sowohl für die Autorenebene als auch für die Veröffentlichungsstufe. Dies wird erreicht, indem die neuesten Kundenpakete mit dem neuesten Adobe-Grundbild kombiniert werden. Wenn die neuen Bilder erfolgreich erstellt und getestet werden, automatisiert Cloud Manager den Übergang zur neuesten Version des Bildes vollständig, indem alle Dienstknoten mithilfe eines kontinuierlichen Aktualisierungsmusters aktualisiert werden. Dies führt zu keiner Ausfallzeit für Autor oder Veröffentlichungsdienst.

<!--- needs reworking -->

![AEM as a Cloud Service - Deployment](assets/concepts-04.png "ArchitectureAEM as a Cloud Service - Deployment Architecture")

## Inhaltsverteilung {#content-distribution}

Adobe Experience Manager als Cloud-Dienst hat die Funktionsweise der Veröffentlichung von Inhalten verändert. Mit AEM als Cloud-Dienst wird das Replizierungsframework aus früheren Versionen von AEM nicht mehr zum Veröffentlichen von Seiten verwendet (Änderungen werden von der Autoreninstanz in die Veröffentlichungsinstanzen verschoben).

AEM als Cloud-Dienst nutzt jetzt die [Sling Content Distribution](https://sling.apache.org/documentation/bundles/content-distribution.html) -Funktion, um die entsprechenden Inhalte zu verschieben. Hierbei wird ein Pipeline-Dienst verwendet, der auf Adobe I/O ausgeführt wird, das sich außerhalb der AEM-Laufzeit befindet.

Das Setup wird automatisiert, einschließlich der automatischen Selbstkonfiguration, wenn Veröffentlichungsknoten während der Laufzeit hinzugefügt, entfernt oder recycelt werden.

Eine einzelne Anforderung zum Veröffentlichen oder Rückgängigmachen der Veröffentlichung kann mehrere Ressourcen enthalten, gibt jedoch einen einzigen Status zurück, der für alle gilt; es wird für alle Ressourcen im AEM Publish-Dienst erfolgreich ausgeführt oder für alle Fehler ausgeführt. Dadurch wird sichergestellt, dass die Ressourcen im AEM Publish-Dienst nie inkonsistent sind.

**Architekturdiagramm zur Inhaltsverteilung auf hoher Ebene**

![Architekturdiagramm zur Inhaltsverteilung auf hoher Ebene](assets/architecture-diagram.png "Diagramm zur Inhaltsverteilung auf hoher Ebene")

## Wichtige Evolutionen {#key-evolutions}

Die neue Architektur von AEM als Cloud-Dienst führt einige grundlegende Änderungen und Innovationen im Vergleich zu früheren Generationen ein:

* Alle Dateien (Blobs) werden direkt aus einem Cloud-Datenspeicher hochgeladen und bereitgestellt. Der verknüpfte Stream von Bits durchläuft nie die JVM der AEM-Autoren- und -Veröffentlichungsdienste. Daher können die Knoten der AEM-Autor- und -Veröffentlichungsdienste kleiner sein und mit der Erwartung einer schnellen automatischen Skalierung besser kompatibel sein. Für Geschäftsleute führt dies zu einem schnelleren Erlebnis beim Hochladen und Herunterladen von Bildern, Videos usw.

* Alle Vorgänge, die aus der Veröffentlichung von Inhalten bestehen, beinhalten jetzt eine Pipeline nach einem Abonnementmuster. Veröffentlichte Inhalte werden an verschiedene Warteschlangen in der Pipeline gesendet, an die alle Knoten des Veröffentlichungsdienstes teilnehmen. Daher muss die Autorenebene nicht wissen, wie viele Knoten im Veröffentlichungsdienst vorhanden sind. Dies ermöglicht eine schnelle automatische Skalierung der Veröffentlichungsstufe.

* Das Konzept eines goldenen Masters wurde eingeführt, um den Lebenszyklus der Veröffentlichungsknoten zu automatisieren. Der goldene Master ist ein spezieller Veröffentlichungsknoten, auf den kein Endbenutzer zugreifen kann und von dem aus alle Knoten des Veröffentlichungsdienstes erstellt werden. Wartungsoperationen wie die Komprimierung werden an dem Inhaltsrepository ausgeführt, das an den goldenen Master angehängt ist. Die Veröffentlichungsknoten werden täglich wiederverwendet und erfordern keine routinemäßige Wartung; in der Vergangenheit benötigte diese Wartung einige Ausfallzeiten, insbesondere für die Autoreninstanz.

* Die Architektur trennt den Anwendungsinhalt vollständig vom Anwendungscode und der Konfiguration. Der gesamte Code und die Konfiguration sind praktisch unveränderlich und werden in das Grundbild zur Erstellung der verschiedenen Knoten des Autor- und Veröffentlichungsservices zurückgeschrieben. Daher gibt es eine absolute Garantie, dass jeder Knoten identisch ist und die Änderungen am Code und der Konfiguration nur global vorgenommen werden können, indem eine Cloud Manager-Pipeline ausgeführt wird.
