---
title: Einführung in die Architektur von Adobe Experience Manager as a Cloud Service
description: 'Einführung in die Architektur von Adobe Experience Manager as a Cloud Service. '
translation-type: tm+mt
source-git-commit: 6b68c52235bae033b429a2d4c84f7c31c75b0fa2
workflow-type: tm+mt
source-wordcount: '1671'
ht-degree: 98%

---


# Einführung in die Architektur von Adobe Experience Manager as a Cloud Service {#an-introduction-to-the-architecture-adobe-experience-manager-as-a-cloud-service}

Adobe Experience Manager (AEM) as a Cloud Service hat zu Änderungen an der Architektur geführt.

## Skalierung {#scaling}

AEM as a Cloud Service verfügt jetzt über:

* eine dynamische Architektur mit einer variablen Anzahl von AEM-Bildern.

![Dynamische Architektur](assets/concepts-01.png "Dynamische Architektur")

Diese Architektur:

* wird basierend auf dem *tatsächlichen* Traffic und der *tatsächlichen* Aktivität skaliert.

* enthält einzelne Instanzen, die nur bei Bedarf ausgeführt werden.

* verwendet modulare Anwendungen.

* enthält einen Autoren-Cluster als Standard; dadurch werden Ausfallzeiten für Wartungsaufgaben vermieden.

Dies ermöglicht die automatische Skalierung für verschiedene Nutzungsmuster:

![Automatische Skalierung für verschiedene Nutzungsmuster](assets/concepts-02.png "Automatische Skalierung für verschiedene Nutzungsmuster")

Um dies zu erreichen, werden alle Instanzen von AEM as a Cloud Service gleich erstellt, jede mit denselben standardmäßigen Größenmerkmalen in Bezug auf die Anzahl der Knoten, den zugewiesenen Speicher und die zugewiesene Rechenkapazität.

AEM as a Cloud Service basiert auf der Verwendung einer Orchestrierung, die:

* den Status des Dienstes kontinuierlich überwacht.

* die einzelnen Dienstinstanzen entsprechend den tatsächlichen Anforderungen dynamisch skaliert (entweder nach oben oder unten).

Dies:

* gilt für die Anzahl der Knoten, die Speichermenge und die zugewiesene CPU-Kapazität auf jedem Knoten.

* ermöglicht es AEM as a Cloud Service, Ihren Traffic-Mustern bei deren Änderung Rechnung zu tragen.

Die Skalierung von Instanzen pro Mandant des Dienstes kann automatisch oder manuell auf zwei Achsen erfolgen:

* Vertikal: zugewiesener Arbeitsspeicher und CPU-Kapazität kann für eine feste Anzahl von Knoten hoch- oder herunterskaliert werden.

* Horizontal: die Anzahl der Knoten für einen bestimmten Dienst kann erhöht oder verringert werden.

## Umgebungen {#environments}

>[!NOTE]
>Weitere Informationen finden Sie unter [Bereitstellen – Laufzeitmodi](/help/implementing/deploying/overview.md#runmodes).

AEM as a Cloud Service wird in Foirm von Einzelinstanzen bereitgestellt, wobei jede Instanz eine vollständige AEM-Umgebung darstellt.

Es stehen drei Arten von Umgebung zur Verfügung, die AEM als Cloud Service verwenden:

* **Produktionsumgebung**: hostet die Anwendungen für Geschäftsleute.

* **Staging-Umgebung**: ist immer in einer 1:1-Beziehung an eine einzige Produktionsumgebung gekoppelt. Die Staging-Umgebung wird für verschiedene Leistungs- und Qualitätstests verwendet, bevor Änderungen an der Anwendung in die Produktionsumgebung übertragen werden.

* **Entwicklungsumgebung**: ermöglicht Entwicklern die Implementierung von AEM-Anwendungen unter denselben Laufzeitbedingungen wie bei den Staging- und Produktionsumgebungen.

   Weitere Informationen finden Sie unter [Verwalten von Umgebungen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html?lang=en#using-cloud-manager).

## Programme {#programs}

Jedes neue AEM-Projekt ist immer an genau eine bestimmte Code-Basis gebunden, in der Sie sowohl Konfigurations- als auch benutzerdefinierten Code für Ihr Projekt speichern können. Diese Informationen werden in einem Code-Repository gespeichert, auf das über die üblichen Git-Clients zugegriffen werden kann und das Ihnen zum Zeitpunkt der Erstellung neuer Programme zur Verfügung gestellt wird.

Ein AEM-Programm ist der Container, der Folgendes enthält:

|  Programmelement |  Nummer |
|--- |--- |
| Code-Repository (Git) |  1 |
| Grundlinienbild (Sites oder Assets) |  1 |
| Staging- und Produktionsumgebung eingestellt (1:1) | 0 oder 1 |
| Produktionsfremde Umgebungen (Entwicklung oder Demonstration) | 0 bis N |
| Pipeline für jede Umgebung | 0 oder 1 |

Für AEM as a Cloud Service stehen zunächst zwei Arten von Programmen zur Verfügung:

* AEM Cloud Sites-Dienst

* AEM Cloud Assets-Dienst

Beide ermöglichen den Zugriff auf eine Reihe von Funktionen. Die Autorenstufe enthält alle Sites und Assets-Funktionen für alle Programme, aber die Assets-Programme haben standardmäßig keine Veröffentlichungsstufe.

## Laufzeitarchitektur {#runtime-architecture}

Diese neue Architektur verfügt über verschiedene Hauptkomponenten:

<!--- needs reworking -->

![AEM as a Cloud Service – Laufzeitarchitektur](assets/concepts-03.png "AEM as a Cloud Service – Laufzeitarchitektur")

* Für AEM Sites as a Cloud Service:

   * Es gibt weiterhin das Konzept einer Autorenstufe und einer Veröffentlichungsstufe für jede Umgebung (auf hohem Niveau).

   * Die Autorenstufe besteht aus zwei oder mehr Knoten in einem Cluster mit nur einem Autor. Die Skalierung erfolgt automatisch, je nach Autorenaktivität.

      * Inhaltsautoren/-ersteller melden sich bei der AEM-Autorenstufe an, um Inhalte zu erstellen, zu bearbeiten und zu verwalten.

      * Die Anmeldung bei der Autorenstufe wird den Adobe Identity Management Services (IMS) verwaltet.

      * Die Integration und Verarbeitung von Assets erfolgt über einen dedizierten Asset-Berechnungsdienst.
   * Die Veröffentlichungsstufe besteht aus zwei oder mehr Knoten in einer einzelnen Veröffentlichungsfarm: sie können unabhängig voneinander arbeiten. Jeder Knoten besteht aus einem AEM-Publisher und einem Webserver, der mit dem AEM-Dispatcher-Modul ausgestattet ist. Die Skalierung erfolgt automatisch entsprechend den Anforderungen des Sitetraffic.

      * Endbenutzer oder Site-Besucher besuchen die Website über den AEM-Veröffentlichungsdienst.


* Für AEM Assets as a Cloud Service:

   * Die Architektur umfasst nur eine Autorenumgebung.

* Sowohl die Autorenstufe als auch die Veröffentlichungsstufe lesen Inhalte von und speichern Inhalte in einem Content Repository Service.

   * Die Veröffentlichungsstufe liest nur Inhalte aus der Persistenzschicht.

   * Die Autorenstufe liest und schreibt Inhalte aus der und in die Persistenzschicht.

   * Der Blobs-Speicher wird in der Veröffentlichungs- und Autorenstufe gemeinsam genutzt. Die Dateien werden nicht *verschoben*.

   * Wenn Inhalte von der Autorenstufe genehmigt werden, ist dies ein Hinweis darauf, dass sie aktiviert und daher in die Persistenzschicht der Veröffentlichungsstufe verschoben werden können. Dies geschieht über den Replikationsdienst, eine Middleware-Pipeline. Diese Pipeline empfängt den neuen Inhalt, wobei die einzelnen Veröffentlichungsdienstknoten den Inhalt abonnieren, der an die Pipeline gesendet wird.

      >[!NOTE]
      >
      >Weitere Informationen finden Sie unter [Replikation](/help/operations/replication.md).

   * Entwickler und Administratoren verwalten die AEM as a Cloud Service-Anwendung mit einem CI/CD-Dienst (Continuous Integration/Continuous Delivery), der über [Cloud Manager](/help/overview/what-is-new-and-different.md#cloud-manager)bereitgestellt wird. Dazu gehören Code- und Konfigurationsbereitstellungen unter Verwendung der CI/CD-Pipeline von Cloud Manager. Alles, was mit der Überwachung, Wartung und Fehlerbehebung zu tun hat (z. B. Protokolldateien), wird Kunden in Cloud Manager bereitgestellt.

   * Der Zugriff auf die Autoren- und Veröffentlichungsstufen erfolgt immer über einen Lastenausgleich. Dieser ist immer auf dem neuesten Stand mit den aktiven Knoten in jeder der Ebenen.

   * Für die Veröffentlichungsstufe ist auch ein CDN-Dienst (Continuous Delivery Network) als erster Einstiegspunkt verfügbar.

* Bei Demonstrationsinstanzen von AEM as a Cloud Service wird die Architektur auf einen einzelnen Autorenknoten vereinfacht. Sie weisen daher nicht alle Merkmale von standardmäßigen Entwicklungs-, Staging- und Produktionsumgebungen auf. Dies bedeutet auch, dass es einige Ausfallzeiten geben kann und dass es keine Unterstützung für Backup-/Wiederherstellungsvorgänge gibt.

## Bereitstellungsarchitektur {#deployment-architecture}

Cloud Manager verwaltet alle Aktualisierungen der Instanzen von AEM as a Cloud Service. Er ist obligatorisch, da nur auf diese Weise die Kundenanwendung erstellt, getestet und bereitgestellt werden kann, und zwar sowohl für die Autoren- als auch für die Veröffentlichungsstufe. Diese Updates können von Adobe, wenn eine neue Version von AEM Cloud Service verfügbar ist, oder vom Kunden ausgelöst werden, wenn eine neue Version seiner Anwendung verfügbar ist.

Technisch wird dies aufgrund des Konzepts einer Bereitstellungs-Pipeline implementiert, die an jede Umgebung innerhalb eines Programms gekoppelt ist. Wenn eine Cloud Manager-Pipeline ausgeführt wird, wird eine neue Version der Kundenanwendung erstellt, sowohl für die Autorenstufe als auch für die Veröffentlichungsstufe. Dies wird erreicht, indem die neuesten Kundenpakete mit dem neuesten Adobe-Grundbild kombiniert werden. Wenn die neuen Bilder erfolgreich erstellt und getestet wurden, automatisiert Cloud Manager die Umstellung auf die neueste Version des Bildes vollständig, indem alle Dienstknoten mithilfe eines kontinuierlichen Aktualisierungsmusters aktualisiert werden. Dies führt zu keiner Ausfallzeit, weder für den Autoren- noch für den Veröffentlichungsdienst.

<!--- needs reworking -->

![AEM as a Cloud Service – Implementierungsarchitektur](assets/concepts-04.png "AEM as a Cloud Service – Implementierungsarchitektur")

## Inhaltsverteilung {#content-distribution}

Adobe Experience Manager as a Cloud Service hat die Art und Weise verändert, auf die Inhalte veröffentlicht werden. Mit AEM as a Cloud Service wird das Replikations-Framework aus früheren Versionen von AEM nicht mehr zum Veröffentlichen von Seiten verwendet (Änderungen werden von der Autoreninstanz in die Veröffentlichungsinstanzen verschoben).

AEM as a Cloud Service nutzt jetzt die Funktion [Sling Content Distribution](https://sling.apache.org/documentation/bundles/content-distribution.html), um die entsprechenden Inhalte zu verschieben. Hierbei wird ein Pipeline-Dienst verwendet, der außerhalb der AEM-Laufzeit auf Adobe I/O ausgeführt wird.

Die Einrichtung wird automatisiert, einschließlich der automatischen Selbstkonfiguration, wenn Veröffentlichungsknoten während der Laufzeit hinzugefügt, entfernt oder recycelt werden.

Eine einzelne Anfrage zum Veröffentlichen oder Rückgängigmachen der Veröffentlichung kann mehrere Ressourcen enthalten, gibt jedoch einen einzigen Status zurück, der für alle gilt; sie ist für alle Ressourcen im AEM-Veröffentlichungsdienst erfolgreich oder schlägt für alle fehlt. Dadurch wird sichergestellt, dass die Ressourcen im AEM-Veröffentlichungsdienst nie inkonsistent sind.

**Architekturdiagramm zur Inhaltsverteilung**

![Architekturdiagramm zur Inhaltsverteilung](assets/architecture-diagram.png "Architekturdiagramm zur Inhaltsverteilung")

## Wichtige Entwicklungen {#key-evolutions}

Die neue Architektur von AEM as a Cloud Service führt einige grundlegende Änderungen und Innovationen im Vergleich zu früheren Generationen ein:

* Alle Dateien (Blobs) werden direkt aus einem Cloud-Datenspeicher hochgeladen und bereitgestellt. Der zugehörige Bitstrom durchläuft niemals die JVM der AEM-Autoren- und Veröffentlichungsdienste. Daher können die Knoten der AEM-Autoren- und -Veröffentlichungsdienste kleiner und mit der Erwartung einer schnellen automatischen Skalierung besser kompatibel sein. Für Geschäftsleute führt dies zu einem schnelleren Erlebnis beim Hochladen und Herunterladen von Bildern, Videos usw.

* Alle Vorgänge, die aus der Veröffentlichung von Inhalten bestehen, beinhalten jetzt eine Pipeline nach einem Abonnementmuster. Veröffentlichte Inhalte werden an verschiedene Warteschlangen in der Pipeline gesendet, die von allen Knoten des Veröffentlichungsdienstes abonniert werden. Daher muss die Autorenstufe nicht wissen, wie viele Knoten im Veröffentlichungsdienst vorhanden sind. Dies ermöglicht eine schnelle automatische Skalierung der Veröffentlichungsstufe.

* Zur Automatisierung des Lebenszyklus der Veröffentlichungsknoten wurde das Konzept eines Golden Masters eingeführt. Der Golden Master ist ein spezieller Veröffentlichungsknoten, auf den kein Endbenutzer zugreifen kann und von dem aus alle Knoten des Veröffentlichungsdienstes erstellt werden. Wartungsoperationen wie die Komprimierung werden an dem Content-Repository ausgeführt, das an den Golden Master angehängt ist. Die Veröffentlichungsknoten werden täglich wiederverwendet und erfordern keine routinemäßige Wartung; in der Vergangenheit machte diese Wartung einige Ausfallzeiten nötig, insbesondere für die Autoreninstanz.

* Die Architektur trennt den Anwendungsinhalt vollständig vom Anwendungs-Code und der Konfiguration. Der gesamte Code und die Konfiguration sind praktisch unveränderlich und werden in das Grundlinienbild zur Erstellung der verschiedenen Knoten des Autoren- und Veröffentlichungsdienstes zurückgeschrieben. Daher gibt es eine absolute Garantie, dass jeder Knoten identisch ist und die Änderungen am Code und der Konfiguration nur global vorgenommen werden können, indem eine Cloud Manager-Pipeline ausgeführt wird.
