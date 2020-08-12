---
title: Was ist anders und was ist neu - Adobe Experience Manager als Cloud Service
description: 'Was ist anders und Was ist neu - Adobe Experience Manager (AEM) als Cloud Service. '
translation-type: tm+mt
source-git-commit: 9882c95972675ee1e0af5de30119d764638f53f3
workflow-type: tm+mt
source-wordcount: '1856'
ht-degree: 11%

---


# Neue Funktionen und Unterschiede {#what-is-new-and-what-is-different}

Seit vielen Jahren stehen AEM beide zur Verfügung:

* On-Premise

* als verwalteter Dienst

Es bestehen intrinsische Unterschiede zwischen diesen bisherigen Ansätzen und AEM als Cloud Service:

* [Architektur](#architecture)
* [Upgrades](#upgrades)
* [Cloud Manager](#cloud-manager)
* [Einstieg](#onboarding)
* [Entwickeln](#developing)
* [Vorgänge und Leistung](#operations-and-performance)
* [Identitätsmanagement](#identity-management)
* [Authoring-Benutzeroberfläche](#authoring-user-interface)
* [AEM Sites](#aem-sites)
* [AEM Assets](#aem-assets)

>[!NOTE]
>
>Diese Übersichten sind nicht erschöpfend, sondern sollen eine Einführung geben.

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
>For further details see the [Deploying Introduction](/help/implementing/deploying/overview.md).

AEM as a Cloud Service now uses Continuous Integration and Continuous Delivery (CI/CD) to ensure that your projects are fully up-to-date. These mean that all upgrade operations are fully automated, so do not require any interruption of service for users.

Adobe proactively takes care of updating all operational instances of the service to the latest version of the AEM code base:

* Bug-fixes:

   * Can be released on a daily basis.

   * Instances are frequently updated with the latest bug-fixes. As changes are applied regularly the impact is incremental, reducing the impact on your service.

   * Most updates are for maintenance and security reasons.

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

* die zentrale Anlaufstelle für Ihr Betriebs- und Entwicklungspersonal.

Die Anzahl und die Art der AEM Programm, die mit Cloud Manager erstellt werden können, werden wie folgt abgeleitet:

* aus der Lizenzvereinbarung für Kunden,

* von internen Akteuren, wenn AEM als Cloud Service für die Aktivierung oder Ausbildung verwendet wird,

* von externen Prozessen, wie z. B. von Adobe.com gestarteten Testversionen.

Cloud Manager wurde zu einem Selbstbedienungsportal entwickelt, in dem die Hauptkomponenten von AEM als Cloud Service erstellt und konfiguriert werden können:

* Erstellen und Verwalten neuer Programm. Weitere Informationen finden Sie unter [Einführung zu Programmen und Programmen](/help/onboarding/getting-access-to-aem-in-cloud/understand-program-types.md) .

* Erstellen und Verwalten der AEM Umgebung in diesen Programmen. Refer to [Managing Environments](/help/implementing/cloud-manager/manage-environments.md) for more details.

* Erstellen und Verwalten der Pipelines für die Bereitstellung des Kundencodes und der zugehörigen Konfiguration auf einer bestimmten Umgebung. Weitere Informationen finden Sie unter [Konfigurieren der CI-CD-Pipeline](/help/implementing/cloud-manager/configure-pipeline.md) .

* werden über wichtige Lebenszykluskomponenten für diese Ereignis (z. B. Produktupdates) benachrichtigt.

Derzeit kann Cloud Manager Umgebung in drei geografischen Regionen erstellen (weitere Regionen folgen):

* USA (Osten)

* EMEA (Niederlande)

* APAC (Australia)

>[!NOTE]
>Refer to [Accessing Experience Manager as a Cloud Service](/help/onboarding/getting-access-to-aem-in-cloud/navigation.md) to get started with Cloud Manager in AEM as a Cloud Service.

## Einstieg {#onboarding}

>[!NOTE]
>
>For further details see [Onboarding](/help/onboarding/home.md).

Starting and managing an AEM project is straightforward when using AEM as a Cloud service as Adobe is responsible for many aspects:

* Baseline AEM images are optimized for specific use-cases.

* Viele der Aufgaben zur manuellen Konfiguration wurden überflüssig gemacht.

Er unterscheidet sich auch erheblich, da es jetzt Folgendes gibt:

* eine Bewertungsphase, um sicherzustellen, dass alle Voraussetzungen erfüllt sind; einschließlich:

   * Rechtliche Anforderungen

   * Vertragsverträge

   * Technische Anforderungen für alle vorhandenen Inhalte und/oder vom Kunden angepassten Code

* Bereitstellungsanforderungen:

   * Code-Aktualisierungen; Alle Kundenanwendungen, die für eine frühere Version von AEM entwickelt wurden, müssen überprüft und gegebenenfalls aktualisiert werden.

   * Inhaltsmigration

## Entwickeln {#developing}

>[!NOTE]
>
>Für weitere Informationen können Sie Beginn mit [Entwicklungsrichtlinien](/help/implementing/developing/introduction/development-guidelines.md) und [Entwicklungs-Tutorial](/help/implementing/developing/introduction/develop-wknd-tutorial.md)machen.

Die neue Architektur, die AEM als Cloud Service unterstützt, umfasst einige wichtige Änderungen am Gesamterlebnis für Entwickler. Eines der Hauptziele von AEM als Cloud Service besteht darin, erfahrenen Kunden (die AEM entweder vor Ort oder im Rahmen der Adobe Managed Services verwendet haben) die Möglichkeit zu geben, so schnell wie möglich zu AEM, ohne den Großteil ihres benutzerspezifischen Codes umschreiben zu müssen. Es könnten jedoch noch einige Anpassungen erforderlich sein.

### Cloud-Entwicklung {#aem-as-a-cloud-service-developing-cloud-development}

Damit bestehende AEM-Anwendungen auf AEM als Cloud Service ausgeführt werden, sind folgende Schritte zu erwarten:

* Der Anwendungscode und die Konfiguration müssen im Git-Code-Repository des zugehörigen Cloud Manager-Programms gespeichert werden.
* Der Anwendungscode und die Konfiguration müssen mit der neuesten Version des AEM kompatibel sein (die sich möglicherweise täglich ändern wird).
   * Die Kundenanwendung muss mithilfe der Cloud Manager-Pipeline erstellt und bereitgestellt werden, die der Cloud Manager-Umgebung zugeordnet ist.
* Die Kundenanwendung muss alle in der Pipeline erzwungenen Code-Qualitäts-, Sicherheits- und Leistungsdaten übergeben.
* Die für die Kundenanwendung erstellten Bilder müssen von der Cloud Manager-Pipeline bereitgestellt werden.

Dieser Prozess wird häufig als Cloud-erste Entwicklung bezeichnet. Da die End-to-End-Dauer (je nach Komplexität der Anwendung von 20 bis 50 Minuten) in Anspruch nehmen wird, müssen schnelle Entwicklungsmethoden eingeführt werden, bevor die ausstehenden Code- und Konfigurationsänderungen in der Cloud versucht werden.

Die Web-Konsole, in der OSGI-Pakete und die zugehörige Konfiguration verwaltet werden und die zuvor Teil der AEM QuickStart war, ist für Benutzer einer AEM als Cloud Service-Umgebung nicht mehr direkt zugänglich. This interface can still be accessed in read-only mode by using a new developer console. With this console, developers can select and login directly to any particular node of an author or publish service, then access the areas blocked by default.

>[!NOTE]
>
>See also [OSGi Configuration](/help/implementing/deploying/overview.md#osgi-configuration)

Another common requirement for developers is quick access to the log files of the various environments. With AEM as a Cloud Service, the log files of the different nodes in the author and publish nodes are made available via the Cloud Manager, either in the form of files that can be downloaded, or via APIs.

Due to the clear separation of code and content, developers can use a particular process for updating content as part of a deployment. The typical use cases for mutable content are:

* Standard *default* content that is part of the customer project (for example, folders, templates, workflows, etc)

* Search index definitions

* ACLs and permissions

* Dienstbenutzer und Benutzergruppen

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

In diesen Bereichen:

* Viele Aufgaben wurden automatisiert.

* Topologien werden für maximale Widerstandsfähigkeit und Effizienz optimiert. Beispielsweise ist die binaryllose Replizierung der Standard.

* Aufgaben mit hoher Auslastung wie Warteschlangen, Aufträge und Aufgaben zur Massenverarbeitung wurden aus der Core-AEM-Instanz verschoben, um von freigegebenen und dedizierten Mikrodiensten verarbeitet zu werden.

Die AEM als Cloud Service werden auch durch eine neue Überwachungs-, Berichte- und Warninfrastruktur unterstützt. Dies ermöglicht es den Adobe SREs (Site Reliability Engineers), den Service proaktiv zu erhalten. Die verschiedenen Elemente der Architektur sind mit einer Vielzahl von Gesundheitskontrollen ausgestattet. Wenn ein bestimmter Knoten der Architektur aus irgendeinem Grund als ungesund gilt, wird er aus dem Dienst entfernt und still durch einen neuen, gesunden ersetzt.

## Identitätsmanagement {#identity-management}

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Sicherheit - IMS-Unterstützung](/help/security/ims-support.md).

Eine wichtige Änderung an AEM als Cloud Service ist die vollständig integrierte Verwendung von Adoben-IDs für den Zugriff auf die Autorenebene.

Dies erfordert die Verwendung der [Adobe Admin Console](https://helpx.adobe.com/de/enterprise/using/admin-console.html) zum Verwalten von Benutzern und Benutzergruppen. Die Benutzerkonten ermöglichen Ihren Benutzern den Zugriff auf Produkte und Dienste der Adobe, da die Benutzerinformationen im Adobe Identity Management System (IMS) zentralisiert sind und über alle Cloud-Profil hinweg freigegeben werden können. Nachdem AEM Zugriff zugewiesen wurde, können die Benutzerkonten in AEM als Cloud Service referenziert werden (wie zuvor). zum Beispiel zum Definieren von Rollen und Berechtigungen über die AEM Security-Benutzeroberflächen.

This combines the benefits of:

* Using the Adobe Identity Management System (IMS) to provide single-sign-on across all Adobe cloud applications.

* User preferences remaining local to each particular instance of AEM as a Cloud Service.

## Authoring User Interface {#authoring-user-interface}

>[!NOTE]
>
>For further details, the [Basic Handling](/help/sites-cloud/authoring/getting-started/basic-handling.md) is a good starting point.

Die Grundprinzipien der Authoring-Benutzeroberfläche (UI), sowohl für Sites als auch für Assets, werden allen vertraut sein, die AEM in der Vergangenheit verwendet haben.

Der Hauptunterschied besteht darin, dass die Benutzeroberfläche ausschließlich für die Touch-Funktion aktiviert ist. Die klassische Benutzeroberfläche ist nicht mehr verfügbar. Andernfalls bleiben die Grundlagen unverändert, wobei nur kleine Änderungen sichtbar sind.

## AEM Sites {#aem-sites}

Adobe Experience Manager Sites als Cloud Service ermöglicht es Ihnen, Ihren Kunden personalisierte, inhaltsbasierte Erlebnisse bereitzustellen, indem Sie die Leistungsfähigkeit des AEM Content-Management Systems mit AEM Digital Asset Management kombinieren.

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
