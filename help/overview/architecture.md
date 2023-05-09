---
title: Einführung in die Architektur von Adobe Experience Manager as a Cloud Service
description: Einführung in die Architektur von Adobe Experience Manager as a Cloud Service.
exl-id: 3fe856b7-a0fc-48fd-9c03-d64c31a51c5d
source-git-commit: c67be5b7f5dc454511753faa16bc46b10e72dde4
workflow-type: tm+mt
source-wordcount: '1807'
ht-degree: 96%

---

# Einführung in die Architektur von Adobe Experience Manager as a Cloud Service {#an-introduction-to-the-architecture-adobe-experience-manager-as-a-cloud-service}

>[!CONTEXTUALHELP]
>id="intro_aem_cloudservice_architecture"
>title="Einführung in die Architektur von AEM as a Cloud Service"
>abstract="Auf dieser Registerkarte können Sie die neue Architektur von AEM as a Cloud Service anzeigen und die Änderungen verstehen. AEM hat zu einer dynamischen Architektur mit einer variablen Anzahl von Bildern geführt, sodass es wichtig ist, sich die Zeit zum Verständnis zu nehmen. Die Cloud-Architektur"
>additional-url="https://video.tv.adobe.com/v/330542/" text="Architekturüberblick"


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

* den Status des Service kontinuierlich überwacht.

* die einzelnen Service-Instanzen entsprechend den tatsächlichen Anforderungen dynamisch skaliert (entweder nach oben oder unten).

Dies:

* gilt für die Anzahl der Knoten, die Speichermenge und die zugewiesene CPU-Kapazität auf jedem Knoten.

* ermöglicht es AEM as a Cloud Service, Ihren Traffic-Mustern bei deren Änderung Rechnung zu tragen.

Die Skalierung von Instanzen pro Mandant des Dienstes gilt für die beiden Achsen:

* Horizontal: Die Anzahl der Knoten für einen bestimmten Dienst wird automatisch erhöht oder verringert, wobei die einzelnen Standardkonfigurationen weiterhin berücksichtigt werden.

* Vertikal: zugewiesener Arbeitsspeicher und CPU-Kapazität kann über die Konfiguration für eine feste Anzahl von Knoten skaliert oder heruntergefahren werden, um die individuellen Anforderungen zu erfüllen.

## Umgebungen {#environments}

>[!NOTE]
>Weitere Informationen finden Sie unter [Bereitstellen – Laufzeitmodi](/help/implementing/deploying/overview.md#runmodes).

AEM as a Cloud Service wird als Einzelinstanzen bereitgestellt, wobei jede Instanz eine vollständige AEM-Umgebung darstellt.

Es gibt drei Arten von Umgebungen, die mit AEM as a Cloud Service verfügbar sind:

* **Produktionsumgebung**: hostet die Anwendungen für Geschäftsleute.

* **Staging-Umgebung**: ist immer in einer 1:1-Beziehung an eine einzige Produktionsumgebung gekoppelt. Die Staging-Umgebung wird für verschiedene Leistungs- und Qualitätstests verwendet, bevor Änderungen an der Anwendung in die Produktionsumgebung übertragen werden.

* **Entwicklungsumgebung**: ermöglicht Entwicklern die Implementierung von AEM-Anwendungen unter denselben Laufzeitbedingungen wie bei den Staging- und Produktionsumgebungen.

   Weitere Informationen finden Sie unter [Verwalten von Umgebungen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html?lang=de#using-cloud-manager).

* **Schnelle Entwicklungsumgebung**: Ermöglicht schnelle Entwicklungsiterationen zum Debugging von neuem oder vorhandenem Code.

## Programme {#programs}

Jedes neue AEM-Projekt ist immer an genau eine bestimmte Code-Basis gebunden, in der Sie sowohl Konfigurations- als auch benutzerdefinierten Code für Ihr Projekt speichern können. Diese Informationen werden in einem Code-Repository gespeichert, auf das über die üblichen Git-Clients zugegriffen werden kann und das Ihnen zum Zeitpunkt der Erstellung neuer Programme zur Verfügung gestellt wird.

Ein AEM-Programm ist der Container, der Folgendes enthält:

|  Programmelement |  Zahl |
|--- |--- |
| Code-Repository (Git) |  1 |
| Grundlinienbild (Sites oder Assets) |  1 |
| Staging- und Produktionsumgebung eingestellt (1:1) | 0 oder 1 |
| Produktionsfremde Umgebungen (RDE, Entwicklung oder Demonstration) | 0 bis N |
| Pipeline für jede Umgebung | 0 oder 1 |

Für AEM as a Cloud Service stehen zunächst zwei Arten von Programmen zur Verfügung:

* AEM Cloud Sites-Service

* AEM Cloud Assets-Service

Beide ermöglichen den Zugriff auf eine Reihe von Funktionen. Die Autorenebene enthält alle Sites- und Assets-Funktionen für alle Programme, aber die Assets-Programme haben standardmäßig keine Veröffentlichungs- oder Vorschauebene.

## Laufzeitarchitektur {#runtime-architecture}

Diese neue Architektur verfügt über verschiedene Hauptkomponenten:

<!--- needs reworking -->

![AEM as a Cloud Service – Laufzeitarchitektur](assets/concepts-03.png "AEM as a Cloud Service – Laufzeitarchitektur")

* Für AEM Sites as a Cloud Service:

   * Es gibt weiterhin das Konzept einer Autorenebene und einer Veröffentlichungsebene für jede Umgebung (auf hohem Niveau).

   * Die Autorenebene besteht aus zwei oder mehr Knoten in einem Cluster mit nur einem Autor. Die Skalierung erfolgt automatisch, je nach Autorenaktivität.

      * Inhaltsautoren/-ersteller melden sich bei der AEM-Autorenebene an, um Inhalte zu erstellen, zu bearbeiten und zu verwalten.

      * Die Anmeldung bei der Autorenebene wird den Adobe Identity Management Services (IMS) verwaltet.

      * Die Integration und Verarbeitung von Assets erfolgt über einen dedizierten Asset-Berechnungs-Service.
   * Die Vorschauebene besteht aus einem einzelnen Vorschauknoten. Dies wird zur Qualitätssicherung von Inhalten vor der Veröffentlichung in der Veröffentlichungsebene verwendet.

   * Die Veröffentlichungsebene besteht aus zwei oder mehr Knoten in einer einzelnen Veröffentlichungsfarm: sie können unabhängig voneinander arbeiten. Jeder Knoten besteht aus einem AEM-Publisher und einem Webserver, der mit dem AEM-Dispatcher-Modul ausgestattet ist. Die Skalierung erfolgt automatisch entsprechend den Anforderungen des Sitetraffic.

      * Endbenutzer oder Site-Besucher besuchen die Website über den AEM-Veröffentlichungs-Service.


* Für AEM Assets as a Cloud Service:

   * Die Architektur umfasst nur eine Autorenumgebung.

* Sowohl die Autoren-, die Vorschau-als auch die Veröffentlichungsebene lesen Inhalte von und speichern Inhalte in einem Content Repository Service.

   * Die Veröffentlichungsebene und die Vorschauebene lesen nur Inhalte aus der Persistenzschicht.

   * Die Autorenebene liest und schreibt Inhalte aus der und in die Persistenzschicht.

   * Der Blobs-Speicher wird in der Veröffentlichungs-, der Vorschu- und Autorenebene gemeinsam genutzt. Die Dateien werden nicht *verschoben*.

   * Wenn Inhalte von der Autorenebene genehmigt werden, ist dies ein Hinweis darauf, dass sie aktiviert und daher in die Persistenzschicht der Veröffentlichungsebene oder optional in die Vorschauebene verschoben werden können. Dies geschieht über den Replikations-Service, eine Middleware-Pipeline. Diese Pipeline empfängt den neuen Inhalt, wobei die einzelnen Veröffentlichungs- (oder Vorschau-)Service-Knoten den Inhalt abonnieren, der an die Pipeline gesendet wird.

      >[!NOTE]
      >
      >Weitere Informationen finden Sie unter [Replikation](/help/operations/replication.md).

   * Entwickler und Administratoren verwalten die AEM as a Cloud Service-Anwendung mit einem CI/CD-Service (Continuous Integration/Continuous Delivery), der über [Cloud Manager](/help/overview/what-is-new-and-different.md#cloud-manager) bereitgestellt wird. Dazu gehören Code- und Konfigurationsbereitstellungen unter Verwendung der CI/CD-Pipeline von Cloud Manager. Alles, was mit der Überwachung, Wartung und Fehlerbehebung zu tun hat (z. B. Protokolldateien), wird Kunden in Cloud Manager bereitgestellt.

   * Der Zugriff auf die Autoren- und Veröffentlichungsebenen erfolgt immer über einen Lastenausgleich. Dieser ist immer auf dem neuesten Stand mit den aktiven Knoten in jeder der Ebenen.

   * Für die Veröffentlichungs. Und die Vorschauebene ist auch ein CDN-Service (Continuous Delivery Network) als erster Einstiegspunkt verfügbar.

* Bei Demonstrationsinstanzen von AEM as a Cloud Service wird die Architektur auf einen einzelnen Autorenknoten vereinfacht. Sie weisen daher nicht alle Merkmale von standardmäßigen Entwicklungs-, Staging- und Produktionsumgebungen auf. Dies bedeutet auch, dass es einige Ausfallzeiten geben kann und dass es keine Unterstützung für Backup-/Wiederherstellungsvorgänge gibt.

## Bereitstellungsarchitektur {#deployment-architecture}

Cloud Manager verwaltet alle Aktualisierungen der Instanzen von AEM as a Cloud Service. Er ist obligatorisch, da nur auf diese Weise die Kundenanwendung erstellt, getestet und bereitgestellt werden kann, und zwar sowohl für die Autoren-, die Vorschau als auch für die Veröffentlichungsebene. Diese Updates können von Adobe, wenn eine neue Version von AEM Cloud Service verfügbar ist, oder vom Kunden ausgelöst werden, wenn eine neue Version seiner Anwendung verfügbar ist.

Technisch wird dies aufgrund des Konzepts einer Bereitstellungs-Pipeline implementiert, die an jede Umgebung innerhalb eines Programms gekoppelt ist. Wenn eine Cloud Manager-Pipeline ausgeführt wird, wird eine neue Version der Kundenanwendung erstellt, sowohl für die Autoren-, die Vorschau- als auch für die Veröffentlichungsebene. Dies wird erreicht, indem die neuesten Kundenpakete mit dem neuesten Adobe-Grundbild kombiniert werden. Wenn die neuen Bilder erfolgreich erstellt und getestet wurden, automatisiert Cloud Manager die Umstellung auf die neueste Version des Bildes vollständig, indem alle Service-Knoten mithilfe eines kontinuierlichen Aktualisierungsmusters aktualisiert werden. Dies führt zu keiner Ausfallzeit, weder für den Autoren- noch für den Veröffentlichungs-Service.

<!--- needs reworking -->

![AEM as a Cloud Service – Implementierungsarchitektur](assets/concepts-04.png "AEM as a Cloud Service – Implementierungsarchitektur")

## Inhaltsverteilung {#content-distribution}

Adobe Experience Manager as a Cloud Service hat die Art und Weise verändert, auf die Inhalte veröffentlicht werden. Mit AEM as a Cloud Service wird das Replikations-Framework aus früheren Versionen von AEM nicht mehr zum Veröffentlichen von Seiten verwendet (Änderungen werden von der Autoreninstanz in die Veröffentlichungsinstanzen verschoben).

AEM as a Cloud Service nutzt jetzt die Funktion [Sling Content Distribution](https://sling.apache.org/documentation/bundles/content-distribution.html), um die entsprechenden Inhalte zu verschieben. Hierbei wird ein Pipeline-Service verwendet, der außerhalb der AEM-Laufzeit auf Adobe I/O ausgeführt wird.

Die Einrichtung wird automatisiert, einschließlich der automatischen Selbstkonfiguration, wenn Veröffentlichungsknoten während der Laufzeit hinzugefügt, entfernt oder recycelt werden.

Eine einzelne Anfrage zum Veröffentlichen oder Rückgängigmachen der Veröffentlichung kann mehrere Ressourcen enthalten, gibt jedoch einen einzigen Status zurück, der für alle gilt; sie ist für alle Ressourcen im AEM-Veröffentlichungs-Service erfolgreich oder schlägt für alle fehlt. Dadurch wird sichergestellt, dass die Ressourcen im AEM-Veröffentlichungs-Service nie inkonsistent sind.

**Architekturdiagramm zur Inhaltsverteilung**

![Architekturdiagramm zur Inhaltsverteilung](assets/architecture-diagram.png "Architekturdiagramm zur Inhaltsverteilung")

## Wichtige Entwicklungen {#key-evolutions}

Die neue Architektur von AEM as a Cloud Service führt einige grundlegende Änderungen und Innovationen im Vergleich zu früheren Generationen ein:

* Alle Dateien (Blobs) werden direkt aus einem Cloud-Datenspeicher hochgeladen und bereitgestellt. Der zugehörige Bitstrom durchläuft niemals die JVM der AEM-Autoren- und Veröffentlichungs-Services. Daher können die Knoten der AEM-Autoren- und -Veröffentlichungs-Services kleiner und mit der Erwartung einer schnellen automatischen Skalierung besser kompatibel sein. Für Geschäftsleute führt dies zu einem schnelleren Erlebnis beim Hochladen und Herunterladen von Bildern, Videos usw.

* Alle Vorgänge, die aus der Veröffentlichung von Inhalten bestehen, beinhalten jetzt eine Pipeline nach einem Abonnementmuster. Veröffentlichte Inhalte werden an verschiedene Warteschlangen in der Pipeline gesendet, die von allen Knoten des Veröffentlichungs-Service abonniert werden. Daher muss die Autorenebene nicht wissen, wie viele Knoten im Veröffentlichungs-Service vorhanden sind. Dies ermöglicht eine schnelle automatische Skalierung der Veröffentlichungsebene.

* Zur Automatisierung des Lebenszyklus der Veröffentlichungsknoten wurde das Konzept eines Golden Masters eingeführt. Der Golden Master ist ein spezieller Veröffentlichungsknoten, auf den kein Endbenutzer zugreifen kann und von dem aus alle Knoten des Veröffentlichungs-Service erstellt werden. Wartungsoperationen wie die Komprimierung werden an dem Content-Repository ausgeführt, das an den Golden Master angehängt ist. Die Veröffentlichungsknoten werden täglich wiederverwendet und erfordern keine routinemäßige Wartung; in der Vergangenheit machte diese Wartung einige Ausfallzeiten nötig, insbesondere für die Autoreninstanz.

* Die Architektur trennt den Anwendungsinhalt vollständig vom Anwendungs-Code und der Konfiguration. Der gesamte Code und die Konfiguration sind praktisch unveränderlich und werden in das Grundlinienbild zur Erstellung der verschiedenen Knoten des Autoren- und Veröffentlichungs-Service zurückgeschrieben. Daher gibt es eine absolute Garantie, dass jeder Knoten identisch ist und die Änderungen am Code und der Konfiguration nur global vorgenommen werden können, indem eine Cloud Manager-Pipeline ausgeführt wird.
