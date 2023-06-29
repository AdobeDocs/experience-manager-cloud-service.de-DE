---
title: Unterschiede und neue Funktionen – Adobe Experience Manager as a Cloud Service
description: Unterschiede und neue Funktionen – Adobe Experience Manager (AEM) as a Cloud Service
exl-id: d1ce126e-960c-4367-b741-af709dd81010
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '1896'
ht-degree: 95%

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
* [Identity Management](#identity-management)
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
>Weitere Informationen finden Sie unter [Architektur](/help/overview/architecture.md).

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

AEM as a Cloud Service verwendet jetzt die kontinuierliche Integration und Bereitstellung (Continuous Integration und Continuous Delivery, CI/CD), um sicherzustellen, dass Ihre Projekte auf der aktuellen AEM-Version basieren. Dies bedeutet, dass Produktions- und Staging-Instanzen ohne Unterbrechung des Services für Benutzende auf die aktuelle AEM-Version aktualisiert werden.

>[!NOTE]
>
>Wenn die Aktualisierung der Produktionsumgebung fehlschlägt, setzt Cloud Manager sie automatisch auf die Staging-Umgebung zurück. Dies erfolgt automatisch, um sicherzustellen, dass nach Abschluss einer Aktualisierung die Staging- und Produktionsumgebung beide auf derselben AEM-Version basieren.

Es gibt zwei Arten von AEM-Versionsaktualisierungen:

* **AEM-Wartungsaktualisierungen**

   * Können täglich veröffentlicht werden.
   * Sie dienen hauptsächlich Wartungszwecken, einschließlich aktueller Fehlerbehebungen und Sicherheitsupdates.
   * Sie haben nur geringe Auswirkungen, da Änderungen regelmäßig angewendet werden.

* **Neue Funktionsaktualisierungen**

   * Werden über einen vorhersehbaren monatlichen Zeitplan veröffentlicht.

>[!TIP]
>
>Weitere Informationen finden Sie unter [AEM-Versionsaktualisierungen](/help/implementing/deploying/aem-version-updates.md).

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

* Erstellen und Verwalten neuer Programme. Siehe [Grundlegendes zu Programmen und Programmtypen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) für weitere Details.

* Erstellen und Verwalten der AEM-Umgebungen in diesen Programmen. Siehe [Verwalten von Umgebungen](/help/implementing/cloud-manager/manage-environments.md) für weitere Details.

* Erstellen und Verwalten der Pipelines für die Bereitstellung des Kunden-Codes und der zugehörigen Konfiguration in einer bestimmten Umgebung. Siehe [Konfigurieren der CI/CD-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) für weitere Details.

* Benachrichtigung über wichtige Lebenszyklusereignisse für diese Komponenten (z. B. Produktaktualisierungen).

Cloud Manager erstellt Umgebungen in Rechenzentren in vielen geografischen Regionen und ermöglicht so eine globale Abdeckung. CDN Points of Presence (PoPs) sorgen für die Bereitstellung von Inhalten mit niedriger Latenz für Kunden in der ganzen Welt.


## Onboarding  {#onboarding}

Das Starten und Verwalten eines AEM-Projekts ist bei Verwendung von AEM as a Cloud Service unkompliziert, da Adobe für viele Aspekte verantwortlich ist:

* AEM-Basisbilder werden für bestimmte Anwendungsfälle optimiert.

* Viele der manuellen Konfigurationsaufgaben wurden überflüssig gemacht.

Weitere wichtige Unterschiede sind:

* Eine Bewertungsphase, um sicherzustellen, dass alle Voraussetzungen erfüllt sind; einschließlich:

   * Rechtliche Anforderungen

   * Vertragliche Vereinbarungen

   * Technische Anforderungen für alle bestehenden Inhalte und/oder vom Kunden angepassten Code

* Bereitstellungsanforderungen:

   * Code-Aktualisierungen; alle Kundenanwendungen, die für eine frühere Version von AEM entwickelt wurden, müssen überprüft und gegebenenfalls aktualisiert werden.

   * Inhaltsmigration

>[!TIP]
>
>Eine vollständige Übersicht über den Onboarding-Prozess erhalten Sie in der [Onboarding-Tour](/help/journey-onboarding/overview.md).

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

Die Web-Konsole, in der OSGI-Bundles und ihre zugehörige Konfiguration verwaltet werden und die früher Teil des AEM QuickStart war, ist in AEM as a Cloud Service nicht mehr verfügbar. Die neue Entwicklerkonsole bietet eine Oberfläche, die nur lesen kann, für die meisten Laufzeitinformationen. Mit dieser Konsole können Entwickler einen bestimmten Knoten eines Autoren- oder Veröffentlichungs-Services auswählen und sich direkt dort anmelden, um die relevanten Informationen anzuzeigen.

>[!NOTE]
>
>Weitere Informationen finden Sie unter [OSGi-Konfiguration](/help/implementing/deploying/overview.md#osgi-configuration).

Eine weitere gängige Voraussetzung für Entwickler ist der schnelle Zugriff auf die Protokolldateien der verschiedenen Umgebungen. Bei AEM as a Cloud Service werden die Protokolldateien der verschiedenen Knoten in den Autoren- und Veröffentlichungsknoten über Cloud Manager zur Verfügung gestellt, entweder in Form von Dateien, die heruntergeladen werden können, oder über APIs.

Aufgrund der klaren Trennung von Code und Inhalt können Entwickler ein bestimmtes Verfahren zur Aktualisierung von Inhalten im Rahmen einer Bereitstellung verwenden. Typische Anwendungsfälle für veränderliche Inhalte sind:

* *Standardinhalt*, der Teil des Kundenprojekts sind (z. B. Ordner, Vorlagen, Workflows usw.)

* Suchindexdefinitionen

* ACLs und Berechtigungen

* Service-Benutzer und -Benutzergruppen

### Lokale Entwicklung {#aem-as-a-cloud-service-developing-local-development}

Um schnelle Iterationen und Entwicklungen zu unterstützen, ist es auch möglich, AEM Anwendungen außerhalb des AEM as a Cloud Service Kontextes zu entwickeln. Zu diesem Zweck werden den Entwicklern die folgenden Artefakte zur Verfügung gestellt:

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

## Identity Management {#identity-management}

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Sicherheit – IMS-Unterstützung](/help/security/ims-support.md).

Eine wichtige Änderung an AEM as a Cloud Service ist die vollständig integrierte Verwendung von Adobe IDs für den Zugriff auf die Autorenebene.

Dies erfordert die Verwendung der [Adobe Admin Console](https://helpx.adobe.com/de/enterprise/using/admin-console.html) zum Verwalten von Benutzern und Benutzergruppen. Die Benutzerkonten ermöglichen Ihren Benutzern den Zugriff auf Produkte und Services von Adobe, da die Benutzerprofilinformationen im Identity Management System (IMS) von Adobe zentralisiert sind und von allen Cloud Services gemeinsam genutzt werden können. Nach der Zuweisung des Zugriffs auf AEM können die Benutzerkonten in AEM as a Cloud Service (wie bisher) referenziert werden, z. B. zur Definition von Rollen und Berechtigungen über die AEM Security-Benutzeroberflächen.

Dies kombiniert die folgenden Vorteile:

* Verwendung des Adobe Identity Management Systems (IMS), um eine einheitliche Anmeldung für alle Adobe-Cloud-Anwendungen zu ermöglichen.

* Lokale Benutzervoreinstellungen für jede bestimmte Instanz von AEM as a Cloud Service.

## Authoring-Benutzeroberfläche {#authoring-user-interface}

>[!NOTE]
>
>Für weitere Informationen beginnen Sie mit [Grundlegende Handhabung](/help/sites-cloud/authoring/getting-started/basic-handling.md).

Die Grundprinzipien der Authoring-Benutzeroberfläche (Benutzeroberfläche) für sowohl Sites als auch Assets kennen alle, die AEM in der Vergangenheit verwendet haben.

Der Hauptunterschied besteht darin, dass die Benutzeroberfläche exklusiv Touch-fähig ist. Die klassische Benutzeroberfläche ist nicht mehr verfügbar. Ansonsten bleiben die Grundlagen unverändert, wobei nur kleine Änderungen sichtbar sind.

## AEM Sites {#aem-sites}

Adobe Experience Manager Sites as a Cloud Service ermöglicht es Ihnen, Ihren Kunden personalisierte, inhaltsgesteuerte Erlebnisse bereitzustellen, indem das Potenzial des AEM-Content-Management-Systems mit AEM Digital Asset Management kombiniert wird.

Weitere Informationen finden Sie in der Übersicht über die [Änderungen an Sites](/help/sites-cloud/sites-cloud-changes.md).

## AEM Assets {#aem-assets}

Adobe Experience Manager Assets as a Cloud Service bietet eine Cloud-native PaaS-Lösung für Unternehmen, mit der sie nicht nur ihre Vorgänge in Digital Asset Management und Dynamic Media schnell und effektiv durchführen können, sondern auch intelligente Funktionen der nächsten Generation wie künstliche Intelligenz und maschinelles Lernen nutzen können, und zwar innerhalb eines Systems, das immer aktuell, verfügbar und lernbereit ist.

Das Asset-Angebot umfasst die Verarbeitung von Assets der nächsten Generation in der Cloud sowie die hochleistungsfähige Erfassung und Suche von Assets.

Weitere Informationen finden Sie unter [Übersicht und Einführung in Assets as a Cloud Service](/help/assets/overview.md).

## Kennenlernen von Adobe Experience Manager as a Cloud Service {#getting-to-know-aem-as-cloud-service}

Weitere Informationen finden Sie unter:

* [Einführung in Adobe Experience Manager as a Cloud Service](/help/overview/introduction.md)
* [Architektur](/help/overview/architecture.md) von Adobe Experience Manager as a Cloud Service
* [Wesentliche Änderungen an AEM as a Cloud Service (Versionshinweise)](/help/release-notes/aem-cloud-changes.md)
* [Wesentliche Änderungen an AEM Sites as a Cloud Service](/help/sites-cloud/sites-cloud-changes.md)
* [Wesentliche Änderungen an AEM Assets as a Cloud Service](/help/assets/assets-cloud-changes.md)
* [Einführung in AEM Assets as a Cloud Service](/help/assets/overview.md)
* [Tutorials zu Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/overview.html?lang=de)

>[!TIP]
>
>Sobald Sie einen Überblick über AEM as a Cloud Service haben, können Sie schnell eingebunden werden, indem Sie die [Onboarding-Journey](/help/journey-onboarding/overview.md).
>
>Sind Sie bereits dabei oder bereit, die Funktionen von AEM zu testen? Installieren Sie das [AEM-Referenzdemo-Add-on](/help/journey-sites/demos-add-on/overview.md), um die leistungsstarken Funktionen von AEM anhand von umfangreichen Beispielen zu erkunden.
