---
title: What is Different and What is New - Adobe Experience Manager as a Cloud Service
description: 'Was ist anders und Was ist neu - Adobe Experience Manager (AEM) als Cloud Service. '
translation-type: tm+mt
source-git-commit: ff9823f3d083ebc1dc5d130919144fe3678a13ed
workflow-type: tm+mt
source-wordcount: '1834'
ht-degree: 11%

---


# Neue Funktionen und Unterschiede {#what-is-new-and-what-is-different}

Seit vielen Jahren stehen AEM beide zur Verfügung:

* On-Premise

* as a Managed Service

There are intrinsic differences between these previous approaches and AEM as a Cloud Service:

* [Architektur](#architecture)
* [Upgrades](#upgrades)
* [Cloud Manager](#cloud-manager)
* [Einstieg](#onboarding)
* [Entwickeln](#developing)
* [Vorgänge und Leistung](#operations-and-performance)
* [Identitätsmanagement](#identity-management)
* [Authoring User Interface](#authoring-user-interface)
* [AEM Sites](#aem-sites)
* [AEM Assets](#aem-assets)

>[!NOTE]
>
>These overviews are not exhaustive, but are intended to provide an introduction.

>[!NOTE]
>
>Weitere Informationen zu den Versionen &quot;On-Premise&quot;und &quot;Managed Service&quot;finden Sie in der Dokumentation zu [AEM 6.5](https://helpx.adobe.com/de/support/experience-manager/6-5.html).

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


## Upgrades {#upgrades}

>[!NOTE]
>
>Weitere Informationen finden Sie in der [Einführung](/help/implementing/deploying/overview.md)zur Bereitstellung.

AEM als Cloud Service verwendet jetzt Continuous Integration und Continuous Versand (CI/CD), um sicherzustellen, dass Ihre Projekte vollständig auf dem neuesten Stand sind. These mean that all upgrade operations are fully automated, so do not require any interruption of service for users.

Adobe sorgt proaktiv dafür, dass alle operativen Instanzen des Dienstes auf die neueste Version der AEM-Codebasis aktualisiert werden:

* Fehlerbehebungen:

   * Kann täglich freigegeben werden.

   * Instanzen werden häufig mit den neuesten Fehlerkorrekturen aktualisiert. Da Änderungen regelmäßig vorgenommen werden, ist der Einfluss inkrementell, was die Auswirkungen auf Ihren Dienst verringert.

   * Die meisten Updates werden aus Gründen der Wartung und Sicherheit bereitgestellt.

* Neue Funktionen:

   * Will be released via a predictable monthly schedule.

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Implementierungsarchitektur](/help/core-concepts/architecture.md#deployment-architecture).

## Cloud Manager {#cloud-manager}

Adobe Cloud Manager ist ein unverzichtbarer Bestandteil des kontinuierlichen Aktualisierungsansatzes von AEM als Cloud Service, da es alle Aktualisierungen Ihrer Instanzen steuert - dies ist obligatorisch.

Updates können durch eine Adobe ausgelöst werden, wenn eine neue Version des Cloud-Dienstes verfügbar ist. Alternativ dazu können Sie Ihre Anwendungsupdates über die von Cloud Manager bereitgestellten Pipelines auslösen.

Cloud Manager ist:

* zur Verwaltung von AEM Programmen und Umgebung verwendet werden,

* ein wesentlicher Bestandteil der AEM als Cloud Service; jeder neue Mandant wird zum ersten Mal für den Zugriff auf Cloud Manager bereitgestellt,

* the single entry point for your operations and development staff.

Specifically, the number of and the type of AEM programs that can be created from the Cloud Manager is derived either:

* from the customer licensing agreement,

* von internen Akteuren, wenn AEM als Cloud Service für die Aktivierung oder Ausbildung verwendet wird,

* von externen Prozessen, wie z. B. von Adobe.com gestarteten Testversionen.

Cloud Manager wurde zu einem Selbstbedienungsportal entwickelt, in dem die Hauptkomponenten von AEM als Cloud Service erstellt und konfiguriert werden können:

* Erstellen und Verwalten der AEM Umgebung in diesen Programmen.

* Erstellen und Verwalten der AEM Umgebung in diesen Programmen.

* Erstellen und Verwalten der Pipelines für die Bereitstellung des Kundencodes und der zugehörigen Konfiguration auf einer bestimmten Umgebung.

* werden über wichtige Lebenszykluskomponenten für diese Ereignis (z. B. Produktupdates) benachrichtigt.

Derzeit kann Cloud Manager Umgebung in drei geografischen Regionen erstellen (weitere Regionen folgen):

* USA (Osten)

* EMEA (Niederlande)

* APAC (Australien)

>[!NOTE]
>Informationen zum Einstieg in Cloud Manager in AEM Cloud Service finden Sie unter [Zugriff auf Experience Manager als Cloud Service](/help/onboarding/getting-access-to-aem-in-cloud/navigation.md) .

## Einstieg {#onboarding}

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Einstieg](/help/onboarding/home.md).

Das Starten und Verwalten eines AEM ist unkompliziert, wenn AEM als Cloud-Dienst verwendet wird, da die Adobe für viele Aspekte verantwortlich ist:

* Grundlegende AEM sind für bestimmte Anwendungsfälle optimiert.

* Viele der Aufgaben zur manuellen Konfiguration wurden überflüssig gemacht.

Er unterscheidet sich auch erheblich, da es jetzt Folgendes gibt:

* An assessment phase to ensure that all pre-requisites have been met; including, for example:

   * Rechtliche Anforderungen

   * Vertragsverträge

   * Technische Anforderungen für alle vorhandenen Inhalte und/oder vom Kunden angepassten Code

* Deployment requirements:

   * Code-Aktualisierungen; Alle Kundenanwendungen, die für eine frühere Version von AEM entwickelt wurden, müssen überprüft und gegebenenfalls aktualisiert werden.

   * Content migration

## Entwickeln {#developing}

>[!NOTE]
>
>Für weitere Informationen können Sie Beginn mit [Entwicklungsrichtlinien](/help/implementing/developing/introduction/development-guidelines.md) und [Entwicklungs-Tutorial](/help/implementing/developing/introduction/develop-wknd-tutorial.md)machen.

Die neue Architektur, die AEM als Cloud Service unterstützt, umfasst einige wichtige Änderungen am Gesamterlebnis für Entwickler. Eines der Hauptziele von AEM als Cloud Service besteht darin, erfahrenen Kunden (die AEM entweder vor Ort oder im Rahmen der Adobe Managed Services verwendet haben) die Möglichkeit zu geben, so schnell wie möglich zu AEM, ohne den Großteil ihres benutzerspezifischen Codes umschreiben zu müssen. However, some adjustments might still be needed.

### Cloud Development {#aem-as-a-cloud-service-developing-cloud-development}

Damit bestehende AEM-Anwendungen auf AEM als Cloud Service ausgeführt werden, sind folgende Schritte zu erwarten:

* The application code and configuration must be stored in the Git code repository of the associated Cloud Manager program.
* The application code and configuration must be compatible with the latest version of the baseline AEM image (which might be changing daily).
   * Die Kundenanwendung muss mithilfe der Cloud Manager-Pipeline erstellt und bereitgestellt werden, die der Cloud Manager-Umgebung zugeordnet ist.
* Die Kundenanwendung muss alle in der Pipeline erzwungenen Code-Qualitäts-, Sicherheits- und Leistungsdaten übergeben.
* The images built for the customer application must be deployed by the Cloud Manager pipeline.

This process is commonly referred to as Cloud-first development. Since the end-to-end duration is expected to take minutes (from 20 to 50 depending on the complexity of the application), it is necessary to embrace rapid development methodologies before the pending code and configuration changes are attempted in the cloud.

Die Web-Konsole, in der OSGI-Pakete und die zugehörige Konfiguration verwaltet werden und die zuvor Teil der AEM QuickStart war, ist für Benutzer einer AEM als Cloud Service-Umgebung nicht mehr direkt zugänglich. Über eine neue Entwicklerkonsole kann auf diese Schnittstelle weiterhin im schreibgeschützten Modus zugegriffen werden. Mit dieser Konsole können Entwickler einen bestimmten Knoten eines Autoren- oder Veröffentlichungsdiensts auswählen und sich direkt anmelden und dann auf die standardmäßig blockierten Bereiche zugreifen.

>[!NOTE]
>
>Siehe auch [OSGi-Konfiguration](/help/implementing/deploying/overview.md#osgi-configuration)

Eine weitere gängige Voraussetzung für Entwickler ist der schnelle Zugriff auf die Protokolldateien der verschiedenen Umgebung. With AEM as a Cloud Service, the log files of the different nodes in the author and publish nodes are made available via the Cloud Manager, either in the form of files that can be downloaded, or via APIs.

Aufgrund der klaren Trennung von Code und Inhalt können Entwickler einen bestimmten Prozess zum Aktualisieren von Inhalten im Rahmen einer Bereitstellung verwenden. Typische Anwendungsfälle für veränderliche Inhalte sind:

* Standardmäßige *Standardinhalte* , die Teil des Kundenprojekts sind (z. B. Ordner, Vorlagen, Workflows usw.)

* Suchindexdefinitionen

* ACLs und Berechtigungen

* Service users and user groups

### Lokale Entwicklung {#aem-as-a-cloud-service-developing-local-development}

Um schnelle Iterationen und Entwicklung zu unterstützen, ist es auch möglich, AEM Applikationen außerhalb des AEM als Cloud Service zu entwickeln. Zu diesem Zweck werden die folgenden Artefakte den Entwicklern zur Verfügung gestellt:

* Der AEM als Cloud Service QuickStart: ein `.jar` basiertes, eigenständiges Installationsprogramm der neuesten AEM Codebasis mit derselben funktionalen und API-Oberfläche.

* AEM als Cloud Service-Dispatcher-SDK: ein bildbasierter Prozess zum lokalen Testen und Validieren von Dispatcher-Konfigurationen

>[!NOTE]
>
>Beachten Sie, dass Cloud QuickStart nicht alle Funktionen von AEM Sites und AEM Assets zulässt. Es besteht aus einer einfachen Autorensoftware, bei der die meisten Erweiterungen entwickelt und getestet werden können.

## Vorgänge und Leistung {#operations-and-performance}

>[!NOTE]
>
>Für weitere Details beginnen Sie mit [Backup](/help/operations/backup.md), [Indizierung](/help/operations/indexing.md) und [anderen Wartungsaufgaben](/help/operations/maintenance.md).

Bei AEM als Cloud Service werden solche Vorgänge automatisiert, sodass eine Unterbrechung des Dienstes nicht mehr erforderlich ist.

In these areas:

* Viele Aufgaben wurden automatisiert.

* Topologies are optimized for maximum resilience and efficiency; for example, binaryless replication is the default.

* Heavy-load tasks, such as queues, jobs and bulk-processing tasks have been moved out of the core AEM instance to be handled by shared and dedicated micro-services.

Die AEM als Cloud Service werden auch durch eine neue Überwachungs-, Berichte- und Warninfrastruktur unterstützt. Dies ermöglicht es den Adobe SREs (Site Reliability Engineers), den Service proaktiv zu erhalten. Die verschiedenen Elemente der Architektur sind mit einer Vielzahl von Gesundheitskontrollen ausgestattet. Wenn ein bestimmter Knoten der Architektur aus irgendeinem Grund als ungesund gilt, wird er aus dem Dienst entfernt und still durch einen neuen, gesunden ersetzt.

## Identitätsmanagement {#identity-management}

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Sicherheit - IMS-Unterstützung](/help/security/ims-support.md).

Eine wichtige Änderung an AEM als Cloud Service ist die vollständig integrierte Verwendung von Adoben-IDs für den Zugriff auf die Autorenebene.

Dies erfordert die Verwendung der [Adobe Admin Console](https://helpx.adobe.com/de/enterprise/using/admin-console.html) zum Verwalten von Benutzern und Benutzergruppen. Die Benutzerkonten ermöglichen Ihren Benutzern den Zugriff auf Produkte und Dienste der Adobe, da die Benutzerinformationen im Adobe Identity Management System (IMS) zentralisiert sind und über alle Cloud-Profil hinweg freigegeben werden können. Nachdem AEM Zugriff zugewiesen wurde, können die Benutzerkonten in AEM als Cloud Service referenziert werden (wie zuvor). zum Beispiel zum Definieren von Rollen und Berechtigungen über die AEM Security-Benutzeroberflächen.

Dies kombiniert die Vorteile von:

* Verwenden der Adobe Identity Management System (IMS), um Single Sign-On für alle Adobe Cloud-Anwendungen bereitzustellen.

* Benutzervoreinstellungen bleiben lokal für jede bestimmte Instanz von AEM als Cloud Service.

## Authoring-Benutzeroberfläche {#authoring-user-interface}

>[!NOTE]
>
>Für weitere Details ist die [Grundlegende Handhabung](/help/sites-cloud/authoring/getting-started/basic-handling.md) ein guter Ausgangspunkt.

Die Grundprinzipien der Authoring-Benutzeroberfläche (UI), sowohl für Sites als auch für Assets, werden allen vertraut sein, die AEM in der Vergangenheit verwendet haben.

Der Hauptunterschied besteht darin, dass die Benutzeroberfläche ausschließlich für die Touch-Funktion aktiviert ist. Die klassische Benutzeroberfläche ist nicht mehr verfügbar. Otherwise the basics remain unchanged, with only small changes apparent.

## AEM Sites {#aem-sites}

Adobe Experience Manager Sites as a Cloud Service enables you to provide your customers with personalized, content-led experiences, by combining the power of the AEM Content Management System with AEM Digital Asset Management.

Weitere Informationen finden Sie in der Übersicht über [Änderungen an Sites](/help/sites-cloud/sites-cloud-changes.md).

## AEM Assets {#aem-assets}

Adobe Experience Manager Assets als Cloud Service Angebot eine Cloud-native SaaS-Lösung, mit der Unternehmen nicht nur ihre Digital Asset Management- und Dynamic Media-Vorgänge schnell und wirkungsvoll durchführen können, sondern auch intelligente Funktionen der nächsten Generation wie AI/ML nutzen können, und zwar innerhalb eines Systems, das immer aktuell, immer verfügbar und immer lernfähig ist.

Das Asset-Angebot umfasst die Verarbeitung von Assets der nächsten Generation in der Cloud sowie die Erfassung und Suche von hochleistungsfähigen Assets.

Weitere Informationen finden Sie unter [Übersicht und Einführung in Assets als Cloud Service](/help/assets/overview.md).

## Erste Schritte mit Adobe Experience Manager as a Cloud Service {#getting-to-know-aem-as-cloud-service}

Weitere Informationen finden Sie unter:

* [Einführung zu Adobe Experience Manager as a Cloud Service](/help/overview/introduction.md)
* [Architektur](/help/core-concepts/architecture.md) von Adobe Experience Manager as a Cloud Service
* [Wesentliche Änderungen an AEM as a Cloud Service (Versionshinweise)](/help/release-notes/aem-cloud-changes.md)
* [Wesentliche Änderungen an AEM Sites as a Cloud Service](/help/sites-cloud/sites-cloud-changes.md)
* [Wesentliche Änderungen an AEM Assets as a Cloud Service](/help/assets/assets-cloud-changes.md)
* [Einführung in AEM Assets as a Cloud Service](/help/assets/overview.md)
* [Tutorials zu Adobe Experience Manager as a Cloud Service](https://docs.adobe.com/content/help/en/experience-manager-learn/cloud-service/overview.html)
