---
title: Was ist anders und was ist neu - Adobe Experience Manager als Cloud-Dienst
description: 'Was ist anders und was ist neu - Adobe Experience Manager (AEM) als Cloud-Dienst. '
translation-type: tm+mt
source-git-commit: 27a16045ff0c22d65e61468036e6ee0b9ab1d826

---


# Neue Funktionen und Unterschiede {#what-is-new-and-what-is-different}

Seit vielen Jahren ist AEM sowohl verfügbar als auch:

* On-Premise

* als verwalteter Dienst

Es bestehen inhärente Unterschiede zwischen diesen vorherigen Ansätzen und AEM als Cloud-Dienst:

* [Architektur](#architecture)
* [Upgrades](#upgrades)
* [Cloud Manager](#cloud-manager)
* [Eingliederung](#onboarding)
* [Entwickeln](#developing)
* [Vorgänge und Leistung](#operations-and-performance)
* [Identitätsmanagement](#identity-management)
* [Authoring-Benutzeroberfläche](#authoring-user-interface)
* [AEM Sites](#aem-sites)
* [AEM Assets](#aem-assets)

>[!NOTE]
>
>Diese Übersichten sind nicht erschöpfend, sondern sollen eine Einführung geben.

<!-- change link when 6.5 hub page migrated -->

>[!NOTE]
>
>Weitere Informationen zu den Versionen &quot;On-Premise&quot;und &quot;Managed Service&quot;finden Sie in der Dokumentation zu [AEM 6.5](https://helpx.adobe.com/support/experience-manager/6-5.html).

<!-- * [Miscellaneous](#miscellaneous) -->

## Architektur {#architecture}

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Architektur](/help/core-concepts/architecture.md).

### Frühere Versionen {#previous-versions-architecture}

Sowohl AEM On-Premise als auch AEM unter Managed Services verwendeten eine statische Architektur, die aus einer festen Anzahl von Computern und Instanzen bestand.

![Statische](assets/introduction-01.png "ArchitekturStatische Architektur")

Diese:

* wurden nach *Spitzenverkehrsverkehr* (Internet) und *Spitzenaktivität* (Marketing) sortiert, was dazu führte, dass sie über längere Zeit untätig waren:
   ![Statische Struktur muss für unterschiedliche](assets/introduction-02.png "Nutzungsmuster ausgelegt seinStatische Struktur muss für unterschiedliche Nutzungsmuster ausgelegt sein")

* Es waren monolithische Anwendungen (der Schnellstart).

* hatte eine Instanz im Autorenmodus; die während des Wartungsfensters Ausfallzeiten hatten.

### AEM als Cloud-Dienst {#aem-as-a-cloud-service-architecture}

AEM als Cloud-Dienst verfügt jetzt über:

* Eine dynamische Architektur mit einer variablen Anzahl von AEM-Bildern.

![Dynamische](assets/introduction-03.png "ArchitekturDynamische Architektur")

Diese Architektur:

* Wird basierend auf dem *tatsächlichen* Traffic und der *tatsächlichen* Aktivität skaliert.

* Enthält einzelne Instanzen, die nur bei Bedarf ausgeführt werden.

* Verwendet modulare Anwendungen.

* Enthält einen Autorencluster als Standard; Dadurch werden Ausfallzeiten für Wartungsaufgaben vermieden.

Dies ermöglicht die automatische Skalierung für verschiedene Verwendungsmuster:

![Automatische Skalierung für verschiedene](assets/introduction-04.png "VerwendungsmusterAutomatische Skalierung für unterschiedliche Verwendungsmuster")


## Upgrades {#upgrades}

<!--
>[!NOTE]
>
>For further details see the [Deploying Introduction](/help/sites/deploying/introduction.md).
-->

### Frühere Versionen {#previous-versions-upgrades}

Sowohl AEM vor Ort als auch AEM unter Managed Services wurden einem festen Muster einer jährlichen Hauptversion unterzogen, die durch Service Packs, Feature Packs und Hotfixes erweitert wurde. Oft würden Instanzen eine Hauptversion zwei oder mehr Jahre lang ausführen.

Abhängig vom Aktualisierungstyp kann der Prozess eine wesentliche Vorbereitung erfordern, die aus Analyse, Entwicklung und Tests besteht, gefolgt von einer Ausfallzeit für die eigentliche Aktualisierung.

### AEM als Cloud-Dienst {#aem-as-a-cloud-service-upgrades}

AEM als Cloud-Dienst verwendet jetzt kontinuierliche Integration und kontinuierliche Bereitstellung (CI/CD), um sicherzustellen, dass Ihre Projekte vollständig auf dem neuesten Stand sind. Dies bedeutet, dass alle Aktualisierungsvorgänge vollständig automatisiert sind, sodass keine Unterbrechung des Diensts für Benutzer erforderlich ist.

Adobe übernimmt proaktiv die Aktualisierung aller operativen Instanzen des Dienstes auf die neueste Version der AEM-Codebasis:

* Fehlerbehebungen:

   * Kann täglich freigegeben werden.

   * Instanzen werden häufig mit den neuesten Fehlerkorrekturen aktualisiert. Da Änderungen regelmäßig vorgenommen werden, ist der Einfluss inkrementell, was die Auswirkungen auf Ihren Dienst verringert.

   * Die meisten Updates werden aus Gründen der Wartung und Sicherheit bereitgestellt.

* Neue Funktionen:

   * Wird über einen vorhersehbaren monatlichen Zeitplan veröffentlicht.

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Implementierungsarchitektur](/help/core-concepts/architecture.md#deployment-architecture).

## Cloud Manager {#cloud-manager}

Adobe Cloud Manager ist ein wesentlicher Bestandteil der kontinuierlichen Aktualisierung von AEM als Cloud-Dienst, da es alle Aktualisierungen Ihrer Instanzen steuert - dies ist obligatorisch.

Updates können von Adobe ausgelöst werden, wenn eine neue Version des Cloud-Dienstes verfügbar ist. Alternativ dazu können Sie Ihre Anwendungsupdates über die von Cloud Manager bereitgestellten Pipelines auslösen.

Cloud Manager ist:

* zur Verwaltung von AEM-Programmen und -Umgebungen verwendet werden,

* eine wesentliche Komponente von AEM als Cloud-Dienst; jeder neue Mandant wird zuerst für den Cloud Manager-Zugriff bereitgestellt,

* die zentrale Anlaufstelle für Ihr Betriebs- und Entwicklungspersonal.

Die Anzahl und der Typ der AEM-Programme, die mit Cloud Manager erstellt werden können, werden wie folgt abgeleitet:

* aus der Lizenzvereinbarung für Kunden in Form eines Kreditpools,

* von internen Akteuren, wenn AEM als Cloud-Dienst für Aktivierung oder Schulung verwendet wird,

* von externen Prozessen, wie Testversionen, die von Adobe.com gestartet wurden.

Cloud Manager wurde als Selbstbedienungsportal entwickelt, in dem die Hauptkomponenten von AEM als Cloud-Dienst erstellt und konfiguriert werden können:

* Erstellen und Verwalten neuer Programme.

* Erstellen und Verwalten der AEM-Umgebungen in diesen Programmen.

* Erstellen und Verwalten der Pipelines zur Bereitstellung des Kundencodes und der zugehörigen Konfiguration in einer bestimmten Umgebung.

* werden über wichtige Lebenszyklusereignisse für diese Komponenten (z. B. Produktupdates) benachrichtigt.

Derzeit ist Cloud Manager in der Lage, Umgebungen in 3 geografischen Regionen zu erstellen (weitere Regionen folgen):

* USA (Osten)

* EMEA (Niederlande)

* APAC (Australien)

## Eingliederung {#onboarding}

<!--
>[!NOTE]
>
>For further details see [Onboarding - An Overview](/help/onboarding/overview.md).
-->

### Frühere Versionen {#previous-versions-onboarding}

Die Implementierung eines AEM-Projekts befolgte im Wesentlichen traditionelle Projektmanagementmethoden.

### AEM als Cloud-Dienst {#aem-as-a-cloud-service-onboarding}

Das Starten und Verwalten eines AEM-Projekts ist wesentlich einfacher, wenn Sie AEM als Cloud-Dienst verwenden, da Adobe für viele Aspekte verantwortlich ist:

* AEM-Grundbilder werden für bestimmte Anwendungsfälle optimiert.

* Viele der manuellen Konfigurationsaufgaben wurden überflüssig.

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
>Für weitere Details beginnt die Dokumentation der [Entwicklungsleitlinien](/help/implementing/developing/introduction/development-guidelines.md) .

<!--
>[!NOTE]
>
>For further details start with [The Developing Experience](/help/sites/developing/introduction/developer-experience.md, [Developing - The Basics](/help/sites/developing/introduction/the-basics.md) and [Developing Best Practices](/help/sites/best-practices/developing.md).
-->

### Frühere Versionen {#previous-versions-developing}

<!-- needs more detail -->
Die Entwicklung war eine intensive Aufgabe, die lokal ausgeführt wurde, gefolgt von der Bereitstellung in der Produktionsinstanz.

### AEM als Cloud-Dienst {#aem-as-a-cloud-service-developing}

<!-- Will need information for new customers -->
Die neue Architektur, die AEM als Cloud-Dienst unterstützt, umfasst einige wichtige Änderungen am gesamten Entwicklererlebnis. Eines der Hauptziele von AEM als Cloud-Dienst besteht darin, erfahrenen Kunden (die AEM entweder vor Ort oder im Zusammenhang mit Adobe Managed Services verwendet haben) die schnellstmögliche Migration zu AEM als Cloud-Dienst zu ermöglichen, ohne den Großteil ihres benutzerspezifischen Codes neu schreiben zu müssen. Es könnten jedoch noch einige Anpassungen erforderlich sein.

#### Cloud-Entwicklung {#aem-as-a-cloud-service-developing-cloud-development}

Damit bestehende AEM-Anwendungen auf AEM als Cloud-Dienst ausgeführt werden, sind die folgenden Schritte zu erwarten:

* Der Anwendungscode und die Konfiguration müssen im Git-Code-Repository des zugehörigen Cloud Manager-Programms gespeichert werden.
* Der Anwendungscode und die Konfiguration müssen mit der neuesten Version des AEM-Basisbilds kompatibel sein (die sich möglicherweise täglich ändern wird).
   * Die Kundenanwendung muss mithilfe der Cloud Manager-Pipeline erstellt und bereitgestellt werden, die der Cloud Manager-Umgebung zugeordnet ist.
* Die Kundenanwendung muss alle in der Pipeline erzwungenen Code-Qualitäts-, Sicherheits- und Leistungsdaten übergeben.
* Die für die Kundenanwendung erstellten Bilder müssen von der Cloud Manager-Pipeline bereitgestellt werden.

<!-- duration of what? -->
Dieser Prozess wird häufig als Cloud-erste Entwicklung bezeichnet. Da die End-to-End-Dauer (je nach Komplexität der Anwendung von 20 bis 50 Minuten) in Anspruch nehmen wird, müssen schnelle Entwicklungsmethoden eingeführt werden, bevor die ausstehenden Code- und Konfigurationsänderungen in der Cloud versucht werden.

<!-- is this really relevant at this point? -->
Die Web-Konsole, in der OSGI-Pakete und ihre zugehörige Konfiguration verwaltet werden, und früher Teil von AEM QuickStart, ist für Benutzer von AEM nicht mehr direkt als Cloud-Service-Umgebung verfügbar. Über eine neue Entwicklerkonsole kann auf diese Schnittstelle weiterhin im schreibgeschützten Modus zugegriffen werden. Mit dieser Konsole können Entwickler einen bestimmten Knoten eines Autoren- oder Veröffentlichungsdiensts auswählen und sich direkt anmelden und dann auf die standardmäßig blockierten Bereiche zugreifen.

Eine weitere allgemeine Anforderung für Entwickler ist der schnelle Zugriff auf die Protokolldateien der verschiedenen Umgebungen. Mit AEM als Cloud-Dienst werden die Protokolldateien der verschiedenen Knoten im Autor- und Veröffentlichungsknoten über den Cloud Manager bereitgestellt, entweder in Form von Dateien, die heruntergeladen werden können, oder über APIs.

Aufgrund der klaren Trennung von Code und Inhalt können Entwickler einen bestimmten Prozess zum Aktualisieren von Inhalten im Rahmen einer Bereitstellung verwenden. Typische Anwendungsfälle für veränderliche Inhalte sind:

* Standardmäßige *Standardinhalte* , die Teil des Kundenprojekts sind (z. B. Ordner, Vorlagen, Arbeitsabläufe usw.)

* Suchindexdefinitionen

* ACLs und Berechtigungen

* Dienstbenutzer und Benutzergruppen

#### Lokale Entwicklung {#aem-as-a-cloud-service-developing-local-development}

Um schnelle Iterationen und Entwicklung zu unterstützen, ist es auch möglich, AEM-Anwendungen außerhalb von AEM als Cloud-Service-Kontext zu entwickeln. Zu diesem Zweck werden die folgenden Artefakte den Entwicklern zur Verfügung gestellt:

* AEM as a Cloud Service QuickStart: ein `.jar` basiertes, eigenständiges Installationsprogramm der neuesten AEM-Codebasis mit derselben funktionalen und API-Oberfläche.

* Das AEM als Cloud Service Dispatcher SDK: ein bildbasierter Prozess zum lokalen Testen und Validieren von Dispatcher-Konfigurationen

>[!NOTE]
>
>Beachten Sie, dass Cloud QuickStart nicht alle AEM-Sites und AEM Assets-Funktionen zulässt. Es besteht aus einer einfachen Autorenumgebung, in der die meisten Erweiterungen entwickelt und getestet werden können.

## Vorgänge und Leistung {#operations-and-performance}

>[!NOTE]
>
>Für weitere Details beginnen Sie mit [Sicherung](/help/operations/backup.md), [Indizierung](/help/operations/indexing.md)und [anderen Wartungsaufgaben](/help/operations/maintenance.md).

### Frühere Versionen {#previous-versions-operations-and-performance}

In der Vergangenheit war es insbesondere auf der Autorenseite notwendig, eine Instanz regelmäßig zu stoppen. für routinemäßige Wartungsarbeiten sowie für Aktualisierungen und Aktualisierungen. Für einige Kunden führte dies wöchentlich zu terminierten Ausfallzeiten.

### AEM als Cloud-Dienst {#aem-as-a-cloud-service-operatioms-and-performance}

Bei AEM als Cloud-Dienst werden solche Vorgänge automatisiert, sodass eine Unterbrechung des Dienstes nicht mehr erforderlich ist.

In diesen Bereichen:

* Viele Aufgaben wurden automatisiert.

* Topologien werden für maximale Widerstandsfähigkeit und Effizienz optimiert. Beispielsweise ist die binaryllose Replizierung der Standard.

* Aufgaben mit hoher Auslastung, wie Warteschlangen, Aufträge und Massenverarbeitungsaufgaben, wurden aus der AEM-Core-Instanz verschoben, um von freigegebenen und dedizierten Mikrodiensten verarbeitet zu werden.

Vorgänge für AEM als Cloud-Dienst werden auch von einer neuen Infrastruktur für Überwachung, Berichterstellung und Benachrichtigung unterstützt. Dies ermöglicht es den Adobe SREs (Site Reliability Engineers), den Service proaktiv zu erhalten. Die verschiedenen Elemente der Architektur sind mit verschiedenen Gesundheitskontrollen ausgestattet. Wenn ein bestimmter Knoten der Architektur aus irgendeinem Grund als ungesund gilt, wird er aus dem Dienst entfernt und still durch einen neuen, gesunden ersetzt.

## Identitätsmanagement {#identity-management}

<!--
>[!NOTE]
>
>For further details see [Security - Single Sign-On](/help/sites/security/single-sign-on.md).
-->

### Frühere Versionen {#previous-versions-identity-management}

Standardmäßig war die Identitätsverwaltung in AEM intern.

>[!NOTE]
>
>AEM 6.4.3.0 eingeführt:
>
>* Unterstützung der Admin-Konsole für AEM-Instanzen.
>* Adobe IMS (Identity Management System)-basierte Authentifizierung für AEM Managed Services-Kunden.


### AEM als Cloud-Dienst {#aem-as-a-cloud-service-identity-management}

Eine wichtige Änderung an AEM als Cloud-Dienst ist die vollständig integrierte Verwendung von Adobe-IDs für den Zugriff auf die Autorenebene.

Dies erfordert die Verwendung der [Adobe Admin Console](https://helpx.adobe.com/enterprise/using/admin-console.html) zum Verwalten von Benutzern und Benutzergruppen. Die Benutzerkonten ermöglichen es Ihren Benutzern, auf Adobe-Produkte und -Dienste zuzugreifen, da die Benutzerprofilinformationen im Adobe Identity Management System (IMS) zentralisiert und für alle Cloud-Dienste freigegeben werden. Nachdem der Zugriff auf AEM zugewiesen wurde, können die Benutzerkonten in AEM als Cloud-Dienst referenziert werden (wie zuvor). zum Beispiel zum Definieren von Rollen und Berechtigungen über die AEM Security-Benutzeroberflächen.

Dies kombiniert die Vorteile von:

* Verwenden des Adobe Identitätsmanagementsystems (IMS), um Single Sign-On für alle Adobe Cloud-Anwendungen bereitzustellen.

* Benutzervoreinstellungen bleiben lokal für jede bestimmte Instanz von AEM als Cloud-Dienst.

## Authoring-Benutzeroberfläche {#authoring-user-interface}

<!--
>[!NOTE]
>
>For further details, the [Basic Handling](/help/sites/authoring/getting-started/basic-handling.md) and [Best Practices](/help/sites/best-practices/authoring.md) are good starting points.
-->

### Frühere Versionen {#previous-versions-authoring}

Die Benutzeroberfläche der Autoreninstanz (UI) für Sites und Assets wurde schrittweise entwickelt und für alle Anwendungsfälle optimiert, wobei sowohl die touchfähige als auch die klassische Benutzeroberfläche verwendet wurden.

### AEM als Cloud-Dienst {#aem-as-a-cloud-service-authoring}

Die Grundprinzipien der Authoring-Benutzeroberfläche (UI) für Sites und Assets sind allen Benutzern, die AEM in der Vergangenheit verwendet haben, sehr vertraut.

Der Hauptunterschied besteht darin, dass die Benutzeroberfläche ausschließlich für die Touch-Funktion aktiviert ist. Die klassische Benutzeroberfläche ist nicht mehr verfügbar. Andernfalls bleiben die Grundlagen unverändert, wobei nur kleine Änderungen sichtbar sind.

## AEM Sites {#aem-sites}

Mit Adobe Experience Manager Sites als Cloud-Dienst können Sie Ihren Kunden personalisierte, inhaltsbasierte Erlebnisse bereitstellen, indem Sie die Leistungsfähigkeit des AEM Content Management Systems mit AEM Digital Asset Management kombinieren.

Weitere Informationen finden Sie in der Übersicht über [Änderungen an Sites](/help/sites-cloud/sites-cloud-changes.md).

## AEM Assets {#aem-assets}

Adobe Experience Manager Assets as a Cloud Service bietet eine Cloud-native SaaS-Lösung für Unternehmen, mit der sie nicht nur ihre Digital Asset Management- und Dynamic Media-Vorgänge schnell und wirkungsvoll durchführen können, sondern auch intelligente Funktionen der nächsten Generation wie AI/ML nutzen können, und zwar innerhalb eines Systems, das immer aktuell, immer verfügbar und immer lernfähig ist.

Das Asset-Angebot umfasst die Verarbeitung von Assets der nächsten Generation in der Cloud sowie die Erfassung und Suche von hochleistungsfähigen Assets.

Weitere Informationen finden Sie unter [Übersicht und Einführung zu Assets als Cloud-Dienst](/help/assets/overview.md).


