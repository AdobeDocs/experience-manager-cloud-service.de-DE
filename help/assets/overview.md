---
title: Einführung in Assets as a Cloud Service
description: Neue Funktionen in Assets als Cloud-Dienst.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 26833f59f21efa4de33969b7ae2e782fe5db8a14

---


# Introducing Assets as a Cloud Service {#assets-cloud-service-introduction}

<!-- Need review information from gklebus -->

Adobe Experience Manager Assets als Cloud-Dienst-Angebot ist eine Cloud-native API-Lösung für Unternehmen, mit der sie nicht nur ihre Digital Asset Management- und Dynamic Media-Vorgänge schnell und wirkungsvoll durchführen können, sondern auch intelligente Funktionen der nächsten Generation wie AI/ML nutzen können, und zwar innerhalb eines Systems, das immer aktuell, immer verfügbar und immer lernfähig ist.

Die gleichzeitige Erfassung vieler Assets oder komplexer Assets ist eine ressourcenintensive Aufgabe für eine AEM Author-Instanz. Die primäre Instanz verbraucht erhebliche CPU-, Speicher- und I/O-Ressourcen, wenn Assets hinzugefügt, verarbeitet oder sogar migriert werden. Solche Leistungsprobleme wirken sich auf das Authoring und Browsen von Endbenutzern aus.

Unternehmen benötigen Unterstützung für eine Vielzahl von Dateiformaten und Inhaltsauflösungen für Anwendungen in mehreren Geräten, unterschiedlichen Geografien und mehreren Sprachen. Die Anforderungen an die Asset-Verarbeitung und -Datenspeicherung erfordern Ressourcen und Funktionen, die eine herkömmliche Lösung überfordern können. Manchmal führen technische Einschränkungen bei der Verarbeitung von Vermögenswerten nicht zu den gewünschten Ergebnissen, und manchmal behindern die Kosten der Datenspeicherung die Gewinnmargen.

Zunächst sollten Sie die [Vorteile eines Cloud-nativen Angebots](#solution-benefits)verstehen. Sehen Sie sich die bemerkenswerten [Änderungen an AEM als Cloud-Dienst](/help/release-notes/aem-cloud-changes.md) an, die sich auch auf Experience Manager Assets auswirken, und folgen Sie den bemerkenswerten [Änderungen an Assets](/help/assets/assets-cloud-changes.md).

Lesen Sie weiter, um die [Details der neuen Asset-Funktionen](#whats-new-assets) und die [bekannten Probleme](/help/release-notes/known-issues.md)zu erfahren. Sehen Sie sich eine Liste der [veralteten oder entfernten Funktionen](/help/release-notes/deprecated-removed-features.md) an, um zu erfahren, was in dieser Version entfernt wurde, und sehen Sie sich diese [Liste der kommenden Funktionen](/help/release-notes/known-issues.md#upcoming-assets-capabilities) an, um zu erfahren, was in Kürze geschieht. Verstehen Sie abschließend mithilfe dieses [Glossars](/help/overview/terminology.md)die AEM-Begriffe.

## Vorteile der Lösung {#solution-benefits}

Im Folgenden werden die wichtigsten Vorteile von Assets als Cloud-Dienst beschrieben. Weitere Informationen finden Sie unter [Übersicht über Experience Manager als Cloud-Dienst](/help/overview/introduction.md).

* **Moderner Cloud-Dienst für die Asset-Verarbeitung**: Die neuen Asset-Mikrodienste sind ein Cloud-basierter, skalierbarer, zuverlässiger und leicht zu bedienender Asset-Verarbeitungsdienst.
* **Hochgradig skalierbar**: Elastische Skalierbarkeit für alle Implementierungen. Praktisch unbegrenzte Ressourcen, die nach Bedarf verfügbar sind. Sparen Sie Kosten für Überdesign im Vergleich zu einem herkömmlichen System.
* **Neueste Software**: Immer aktuell und immer aktualisiert. Alle Benutzer haben nur die neueste Software mit allen Patches, Features, Sicherheit und Fehlerkorrekturen, die ihnen zur Verfügung stehen. Entwickler und Integratoren arbeiten mit den neuesten APIs, ohne dass Unterstützung für mehrere Versionen erforderlich ist.
* **Immer online**: Null Ausfallzeiten (0dt) dank der Instanz, die in einem Cluster mit Backups und Redundanz bereitgestellt wird. Upgrades sind auch 0dt.
* **Konstante Überwachung**: Die Überwachung des Systems erfolgt durch automatisierte und integrierte Prüfungen und Auslöser, um die Leistung, Verfügbarkeit und Stabilität insgesamt zu erhalten.
* **Problemlose Bereitstellungen**: AEM in Cloud-Vorgängen werden vollständig automatisiert, sodass keine manuelle Intervention erforderlich ist. Bei automatisierten Bereitstellungen automatisiert die Cloud Manager-Komponente (CM) die Erstellung bereitstellbarer Docker-Bilder, die Ihren benutzerdefinierten Code enthalten.

## Funktionen für neue Assets {#whats-new-assets}

Die wichtigsten neuen Funktionen sind:

* [Asset-Mikrodienste](/help/assets/asset-microservices-overview.md)
* [Methoden zum Hochladen von Assets](/help/assets/add-assets.md)
