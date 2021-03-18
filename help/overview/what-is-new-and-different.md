---
title: Unterschiede und neue Funktionen – Adobe Experience Manager as a Cloud Service
description: 'Unterschiede und neue Funktionen – Adobe Experience Manager (AEM) as a Cloud Service '
translation-type: tm+mt
source-git-commit: b77113ccc55f2063c684d49e2babdd7563b9d6fc
workflow-type: tm+mt
source-wordcount: '1885'
ht-degree: 98%

---


# Neue Funktionen und Unterschiede {#what-is-new-and-what-is-different}

Seit vielen Jahren steht AEM in den folgenden zwei Versionen zur Verfügung:

* On-Premise

* als Managed Service

Es gibt wesentliche Unterschiede zwischen diesen bisherigen Ansätzen und AEM as a Cloud Service:

* [Architektur](#architecture)
* [Upgrades](#upgrades)
* [Cloud Manager](#cloud-manager)
* [Einstieg](#onboarding)
* [Entwickeln](#developing)
* [Vorgänge und Leistung](#operations-and-performance)
* [Identitäts-Management](#identity-management)
* [Authoring-Benutzeroberfläche](#authoring-user-interface)
* [AEM Sites](#aem-sites)
* [AEM Assets](#aem-assets)

>[!NOTE]
>
>Diese Übersichten erheben keinen Anspruch auf Vollständigkeit, sollen jedoch eine Einführung bieten.

>[!NOTE]
>
>Weitere Informationen zu den Versionen On-Premise und Managed Service finden Sie in der Dokumentation zu [AEM 6.5](https://experienceleague.adobe.com/docs/experience-manager-65.html?lang=de).

## Architektur {#architecture}

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Architektur](/help/core-concepts/architecture.md).

AEM as a Cloud Service verfügt jetzt über:

* eine dynamische Architektur mit einer variablen Anzahl von AEM-Bildern.

![Dynamische Architektur](assets/introduction-03.png "Dynamische Architektur")

Diese Architektur:

* wird basierend auf dem *tatsächlichen* Traffic und der *tatsächlichen* Aktivität skaliert.

* enthält einzelne Instanzen, die nur bei Bedarf ausgeführt werden.

* verwendet modulare Anwendungen.

* enthält einen Autoren-Cluster als Standard; dadurch werden Ausfallzeiten für Wartungsaufgaben vermieden.

Dies ermöglicht die automatische Skalierung für verschiedene Nutzungsmuster:

![Automatische Skalierung für verschiedene Nutzungsmuster](assets/introduction-04.png "Automatische Skalierung für verschiedene Nutzungsmuster")


## AEM-Aktualisierungen {#aem-updates}

>[!NOTE]
>Weitere Informationen finden Sie unter [AEM-Versionsaktualisierungen](/help/implementing/deploying/aem-version-updates.md).

AEM as a Cloud Service verwendet jetzt CI/CD (Continuous Integration und Continuous Delivery), um sicherzustellen, dass Ihre Projekte auf der aktuellen AEM-Version basieren. Dies bedeutet, dass Produktions- und Staging-Instanzen ohne Unterbrechung des Service für Benutzer auf die aktuelle AEM-Version aktualisiert werden.

>[!NOTE]
> Wenn die Aktualisierung der Produktionsumgebung fehlschlägt, setzt Cloud Manager automatisch auf die Staging-Umgebung zurück. Dies erfolgt automatisch, um sicherzustellen, dass nach Abschluss der Aktualisierung die Staging- und Produktionsumgebung auf derselben AEM-Version basieren.

Es gibt zwei Arten von AEM-Versionsaktualisierungen:

* **AEM-Push-Aktualisierungen**

   * Können täglich veröffentlicht werden.
   * Vor allem zu Wartungszwecken, einschließlich der neuesten Fehlerkorrekturen und Sicherheitsaktualisierungen.

      Da die Änderungen regelmäßig durchgeführt werden, sind die Auswirkungen inkrementell, was die Auswirkungen auf Ihren Service verringert.

* **Neue Funktionsaktualisierungen**

   * Werden über einen vorhersehbaren monatlichen Zeitplan veröffentlicht.

## Cloud Manager {#cloud-manager}

Adobe Cloud Manager ist integraler Bestandteil des kontinuierlichen Upgrade-Ansatzes von AEM as a Cloud Service, da er alle Aktualisierungen Ihrer Instanzen steuert – dies ist obligatorisch.

Aktualisierungen können von Adobe ausgelöst werden, wenn eine neue Version des Cloud Service verfügbar ist. Alternativ können Sie Ihre Anwendungsaktualisierungen über die von Cloud Manager bereitgestellten Pipelines auslösen.

Cloud Manager:

* wird zur Verwaltung von AEM-Programmen und -Umgebungen verwendet,

* ist ein wesentlicher Bestandteil von AEM as a Cloud Service; jeder neue Mandant wird zunächst für den Zugriff auf Cloud Manager bereitgestellt,

* ist die zentrale Anlaufstelle für Ihr Betriebs- und Entwicklungspersonal.

Konkret werden die Anzahl und die Art der AEM-Programme, die aus Cloud Manager erstellt werden können, abgeleitet:

* von der Lizenzvereinbarung des Kunden,

* von intern gesteuerten Akteuren, wenn AEM as a Cloud Service zur Befähigung oder Schulung eingesetzt wird,

* von extern gesteuerten Prozessen, wie z. B. auf Adobe.com gestarteten Probe-Abos,

Cloud Manager hat sich zu einem Selbstbedienungsportal entwickelt, in dem die Hauptkomponenten von AEM as a Cloud Service erstellt und konfiguriert werden können:

* Erstellen und Verwalten neuer Programme. Weitere Informationen finden Sie unter [Grundlegendes zu Programmen und Programmtypen](/help/onboarding/getting-access-to-aem-in-cloud/understand-program-types.md).

* Erstellen und Verwalten der AEM-Umgebungen in diesen Programmen. Weitere Informationen finden Sie unter [Verwalten von Umgebungen](/help/implementing/cloud-manager/manage-environments.md).

* Erstellen und Verwalten der Pipelines für die Bereitstellung des Kunden-Codes und der zugehörigen Konfiguration in einer bestimmten Umgebung. Weitere Informationen finden Sie unter [Konfigurieren der CI/CD-Pipeline](/help/implementing/cloud-manager/configure-pipeline.md).

* Benachrichtigung über wichtige Lebenszyklusereignisse für diese Komponenten (z. B. Produktaktualisierungen).

Cloud Manager erstellt Umgebung in Rechenzentren in vielen geografischen Regionen und ermöglicht so eine globale Abdeckung. CDN Points of Presence (PoPs) sorgen für den Versand von Inhalten mit niedriger Latenz für Kunden in der ganzen Welt.

>[!NOTE]
>Informationen zu den ersten Schritten mit Cloud Manager in AEM as a Cloud Service finden Sie unter [Zugriff auf Experience Manager as a Cloud Service](/help/onboarding/getting-access-to-aem-in-cloud/navigation.md).

## Einstieg {#onboarding}

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Einstieg](/help/onboarding/home.md).

Das Starten und Verwalten eines AEM-Projekts ist bei Verwendung von AEM as a Cloud Service unkompliziert, da Adobe für viele Aspekte verantwortlich ist:

* AEM-Basisbilder werden für bestimmte Anwendungsfälle optimiert.

* Viele der manuellen Konfigurationsaufgaben wurden überflüssig gemacht.

Weitere wichtige Unterschiede sind:

* Eine Bewertungsphase, um sicherzustellen, dass alle Voraussetzungen erfüllt sind; einschließlich:

   * Rechtliche Anforderungen

   * Vertragliche Vereinbarungen

   * Technische Anforderungen für alle bestehenden Inhalte und/oder vom Kunden angepassten Code

* Implementierungsanforderungen:

   * Code-Aktualisierungen; alle Kundenanwendungen, die für eine frühere Version von AEM entwickelt wurden, müssen überprüft und gegebenenfalls aktualisiert werden.

   * Inhaltsmigration

## Entwickeln {#developing}

>[!NOTE]
>
>Für weitere Informationen beginnen Sie mit den [Entwicklungsrichtlinien](/help/implementing/developing/introduction/development-guidelines.md) und [Entwickeln – Das WKND-Tutorial](/help/implementing/developing/introduction/develop-wknd-tutorial.md).

Die neue Architektur, die AEM as a Cloud Service unterstützt, beinhaltet einige wichtige Änderungen am gesamten Entwicklererlebnis. Eines der Hauptziele von AEM as a Cloud Service besteht darin, erfahrenen Kunden (die AEM entweder in der On-Premise-Version oder im Kontext von Adobe Managed Services verwendet haben) die Möglichkeit zu geben, so schnell wie möglich zu AEM as a Cloud Service zu wechseln, ohne den Großteil ihres angepassten Codes neu schreiben zu müssen. Es könnten jedoch noch einige Anpassungen erforderlich sein.

### Cloud-Entwicklung {#aem-as-a-cloud-service-developing-cloud-development}

Für bestehende AEM-Anwendungen, die mit AEM as a Cloud Service laufen sollen, werden die folgenden Schritte erwartet:

* Der Anwendungs-Code und die Konfiguration müssen im Git-Code-Repository des zugehörigen Cloud Manager-Programms gespeichert werden.
* Der Anwendungs-Code und die Konfiguration müssen mit der neuesten Version des AEM-Basisbildes (das sich möglicherweise täglich ändert) kompatibel sein.
   * Die Kundenanwendung muss mithilfe der Cloud Manager-Pipeline, die mit der Cloud Manager-Umgebung verknüpft ist, erstellt und bereitgestellt werden.
* Die Kundenanwendung muss alle in der Pipeline erzwungenen Code-Qualitäts-, Sicherheits- und Leistungstests bestehen.
* Die für die Kundenanwendung erstellten Bilder müssen von der Cloud Manager-Pipeline bereitgestellt werden.

Dieser Prozess wird häufig als Cloud-First-Entwicklung bezeichnet. Da die End-to-End-Dauer voraussichtlich Minuten dauern wird (je nach Komplexität der Anwendung zwischen 20 und 50 Minuten), ist es notwendig, schnelle Entwicklungsmethoden einzusetzen, bevor die anstehenden Code- und Konfigurationsänderungen in der Cloud versucht werden.

Die Web-Konsole, in der OSGi-Pakete und die zugehörige Konfiguration verwaltet werden und die früher Teil von AEM Quickstart war, ist für Benutzer einer AEM as a Cloud Service-Umgebung nicht mehr direkt zugänglich. Auf diese Schnittstelle kann weiterhin im schreibgeschützten Modus über eine neue Entwicklerkonsole zugegriffen werden. Mit dieser Konsole können Entwickler direkt einen bestimmten Knoten eines Autoren- oder Veröffentlichungs-Service auswählen und sich dort anmelden und dann auf die standardmäßig gesperrten Bereiche zugreifen.

>[!NOTE]
>
>Weitere Informationen finden Sie unter [OSGi-Konfiguration](/help/implementing/deploying/overview.md#osgi-configuration).

Eine weitere gängige Voraussetzung für Entwickler ist der schnelle Zugriff auf die Protokolldateien der verschiedenen Umgebungen. Bei AEM as a Cloud Service werden die Protokolldateien der verschiedenen Knoten in den Autoren- und Veröffentlichungsknoten über Cloud Manager zur Verfügung gestellt, entweder in Form von Dateien, die heruntergeladen werden können, oder über APIs.

Aufgrund der klaren Trennung von Code und Inhalt können Entwickler ein bestimmtes Verfahren zur Aktualisierung von Inhalten im Rahmen einer Implementierung verwenden. Typische Anwendungsfälle für veränderliche Inhalte sind:

* *Standardinhalt*, der Teil des Kundenprojekts sind (z. B. Ordner, Vorlagen, Workflows usw.)

* Suchindexdefinitionen

* ACLs und Berechtigungen

* Service-Benutzer und -Benutzergruppen

### Lokale Entwicklung {#aem-as-a-cloud-service-developing-local-development}

Um schnelle Iterationen und Entwicklungen zu unterstützen, ist es auch möglich, AEM-Applikationen außerhalb von AEM as a Cloud Service zu entwickeln. Zu diesem Zweck werden den Entwicklern die folgenden Artefakte zur Verfügung gestellt:

* AEM as a Cloud Service QuickStart: ein `.jar`-basiertes, eigenständiges Installationsprogramm der neuesten AEM-Code-Basis, mit der gleichen Funktions- und API-Oberfläche.

* AEM as a Cloud Service SDK: ein bildbasiertes Verfahren zum lokalen Testen und Validieren von Dispatcher-Konfigurationen.

>[!NOTE]
>
>Beachten Sie, dass Cloud QuickStart nicht alle Funktionen von AEM Sites und AEM Assets zulässt. Es besteht aus einer einfachen Autorenumgebung, in der die meisten Erweiterungen entwickelt und getestet werden können.

## Vorgänge und Leistung {#operations-and-performance}

>[!NOTE]
>
>Für weitere Informationen beginnen Sie mit [Backup](/help/operations/backup.md), [Indizierung](/help/operations/indexing.md) und [anderen Wartungsaufgaben](/help/operations/maintenance.md).

Bei AEM as a Cloud Service werden solche Vorgänge automatisiert, sodass eine Unterbrechung des Service nicht mehr erforderlich ist.

In diesen Bereichen:

* Viele Aufgaben wurden automatisiert.

* Die Topologien sind auf maximale Ausfallsicherheit und Effizienz optimiert. Beispielsweise ist die binärlose Replikation die Standardeinstellung.

* Aufgaben mit hoher Auslastung wie Warteschlangen, Vorgänge und Massenverarbeitungsaufgaben wurden aus der AEM-Kerninstanz verschoben, um von gemeinsam genutzten und dedizierten Microservices ausgeführt zu werden.

Der Betrieb von AEM as a Cloud Service wird auch durch eine neue Überwachungs-, Berichts- und Warninfrastruktur unterstützt. Auf diese Weise können die Adobe-SREs (Site Reliability Engineers) den Service proaktiv aufrechterhalten. Die verschiedenen Elemente der Architektur sind mit einer Vielzahl von Konsistenzprüfungen ausgestattet. Wenn ein bestimmter Knoten der Architektur aus irgendeinem Grund als fehlerhaft erachtet wird, wird er aus dem Service entfernt und durch einen neuen, funktionierenden ersetzt.

## Identitäts-Management {#identity-management}

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Sicherheit – IMS-Unterstützung](/help/security/ims-support.md).

Eine wichtige Änderung an AEM as a Cloud Service ist die vollständig integrierte Verwendung von Adobe IDs für den Zugriff auf die Autorenebene.

Dies erfordert die Verwendung der [Adobe Admin Console](https://helpx.adobe.com/de/enterprise/using/admin-console.html) zum Verwalten von Benutzern und Benutzergruppen. Die Benutzerkonten ermöglichen Ihren Benutzern den Zugriff auf Produkte und Services von Adobe, da die Benutzerprofilinformationen im Identitäts-Management System (IMS) von Adobe zentralisiert sind und von allen Cloud Services gemeinsam genutzt werden können. Nach der Zuweisung des Zugriffs auf AEM können die Benutzerkonten in AEM as a Cloud Service (wie bisher) referenziert werden, z. B. zur Definition von Rollen und Berechtigungen über die AEM Security-Benutzeroberflächen.

Dies kombiniert die folgenden Vorteile:

* Verwendung des Adobe-Identitäts-Management Systems (IMS), um eine einheitliche Anmeldung für alle Adobe-Cloud-Anwendungen zu ermöglichen.

* Lokale Benutzervoreinstellungen für jede bestimmte Instanz von AEM as a Cloud Service.

## Authoring-Benutzeroberfläche {#authoring-user-interface}

>[!NOTE]
>
>Für weitere Informationen beginnen Sie mit [Grundlegende Handhabung](/help/sites-cloud/authoring/getting-started/basic-handling.md).

Die Grundprinzipien der Authoring-Benutzeroberfläche, sowohl für Sites als auch für Assets, werden jedem, der AEM in der Vergangenheit verwendet hat, sehr vertraut sein.

Der Hauptunterschied besteht darin, dass die Benutzeroberfläche exklusiv Touch-fähig ist. Die klassische Benutzeroberfläche ist nicht mehr verfügbar. Ansonsten bleiben die Grundlagen unverändert, wobei nur kleine Änderungen sichtbar sind.

## AEM Sites {#aem-sites}

Adobe Experience Manager Sites as a Cloud Service ermöglicht es Ihnen, Ihren Kunden personalisierte, inhaltsgesteuerte Erlebnisse bereitzustellen, indem das Potenzial des AEM-Content-Management-Systems mit AEM Digital Asset Management kombiniert wird.

Weitere Informationen finden Sie in der Übersicht über die [Änderungen an Sites](/help/sites-cloud/sites-cloud-changes.md).

## AEM Assets {#aem-assets}

Adobe Experience Manager Assets as a Cloud Service bietet eine Cloud-native PaaS-Lösung für Unternehmen, mit der sie nicht nur ihre Digital-Asset-Management- und Dynamic-Media-Vorgänge schnell und effektiv durchführen können, sondern auch intelligente Funktionen der nächsten Generation wie künstliche Intelligenz und maschinelles Lernen nutzen können, und zwar innerhalb eines Systems, das immer aktuell, verfügbar und lernbereit ist.

Das Asset-Angebot umfasst die Verarbeitung von Assets der nächsten Generation in der Cloud sowie die hochleistungsfähige Erfassung und Suche von Assets.

Weitere Informationen finden Sie unter [Übersicht und Einführung in Assets as a Cloud Service](/help/assets/overview.md).

## Erste Schritte mit Adobe Experience Manager as a Cloud Service {#getting-to-know-aem-as-cloud-service}

Weitere Informationen finden Sie unter:

* [Einführung in Adobe Experience Manager as a Cloud Service](/help/overview/introduction.md)
* [Architektur](/help/core-concepts/architecture.md) von Adobe Experience Manager as a Cloud Service
* [Wesentliche Änderungen an AEM as a Cloud Service (Versionshinweise)](/help/release-notes/aem-cloud-changes.md)
* [Wesentliche Änderungen an AEM Sites as a Cloud Service](/help/sites-cloud/sites-cloud-changes.md)
* [Wesentliche Änderungen an AEM Assets as a Cloud Service](/help/assets/assets-cloud-changes.md)
* [Einführung in AEM Assets as a Cloud Service](/help/assets/overview.md)
* [Tutorials zu Adobe Experience Manager as a Cloud Service](https://docs.adobe.com/content/help/de/experience-manager-learn/cloud-service/overview.html)
