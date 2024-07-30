---
title: AEM Sites und Edge Delivery Services
description: Erfahren Sie, wie Edge Delivery Services die Authoring- und Publishing-Möglichkeiten für AEM Sites erweitern, um die Inhaltserstellung zu beschleunigen und Sites mit einer Leistung von 100 % bereitzustellen.
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: b3497f87446ca4c1c71d48f29aebcaa882feb898
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 5%

---


# AEM Sites und Edge Delivery Services {#sites-and-edge}

Erfahren Sie, wie Edge Delivery Services die Authoring- und Publishing-Möglichkeiten für AEM Sites erweitern, um die Inhaltserstellung zu beschleunigen und Sites mit einer Leistung von 100 % bereitzustellen.

## Überblick {#overview}

Zusätzlich zu allen Funktionen und Leistungsmerkmalen, die AEM Sites as a Cloud Service](/help/sites-cloud/sites-cloud-changes.md) als Teil der Cloud-nativen AEM as a Cloud Service-Plattform bietet, bieten Edge Delivery Services zusätzliche Möglichkeiten zum Erstellen und Veröffentlichen von Inhalten, um die Erstellung von Inhalten zu beschleunigen und Sites mit einer Leistung von 100 % bereitzustellen.[

## Was sind Edge Delivery Services? {#what-is-edge}

Edge Delivery Services bieten außergewöhnliche Erlebnisse, die Interaktionen und Konversionen fördern, indem sie wirkungsvolle Erlebnisse bereitstellen, die schnell zu erstellen und zu entwickeln sind. Edge Delivery Services ist ein zusammenstellbarer Satz von Diensten, der eine schnelle Entwicklungsumgebung ermöglicht, in der Autorinnen und Autoren schnell aktualisieren und veröffentlichen können und neue Sites schnell live geschaltet werden können. Weitere Informationen zu Edge Delivery Services finden Sie in der [Übersicht über Edge Delivery Services](/help/edge/overview.md) -Dokumentation.

Durch die Verwendung von Edge Delivery Services zusammen mit AEM Sites as a Cloud Service können Ihre Projekte von folgenden Vorteilen profitieren:

* [Neues Entwicklererlebnis](#developer-experience)
* [Eine neue Veröffentlichungsstufe](#publish-tier)
* [Zusätzliche Bearbeitungsoptionen](#authoring-options)

## Neues Entwicklererlebnis {#developer-experience}

Eine Kernphilosophie von Edge Delivery Services ist *Velocity*. Dies beginnt mit dem Entwicklererlebnis. Wenn Ihre Entwickler:

* Git-Grundlagen verstehen und
* Grundlegendes zu HTML, CSS und JavaScript

Sie können in weniger als dreißig Minuten ein eigenes Projekt und eigene Komponenten für Edge Delivery Services einrichten. Klonen Sie zunächst unser Bausteinprojekt auf GitHub und übernehmen Sie dann Ihre Änderungen. Ihre Anpassung ist sofort online!

Weitere Informationen zur Entwicklung für Edge Delivery Services finden Sie im Dokument [Erste Schritte - Entwickler-Tutorial](https://www.aem.live/developer/tutorial) .

## Eine neue Publish-Ebene {#publish-tier}

Die Entwicklungszeit wird nicht nur drastisch reduziert, sondern auch Edge Delivery Services bringen auch schnellstmögliche Websites.

## Zusätzliche Bearbeitungsoptionen {#authoring-options}

Edge Delivery Services erhöhen auch die Geschwindigkeit der Inhaltserstellung, indem sie neue Bearbeitungsoptionen anbieten.

### Der universelle Editor {#universal-editor}

Der universelle Editor bietet ein nahtloses WYSIWYG-Authoring-Erlebnis (What-you-see-is-what-you-get), das zum Erstellen von Inhalten verwendet werden kann.

Weitere Informationen zur Inhaltserstellung mit dem universellen Editor finden Sie im Dokument [WYSIWYG Content Authoring für Edge Delivery Services](/help/edge/wysiwyg-authoring/authoring.md) .

### Dokumentenbasiertes Authoring {#document-authoring}

Dokumentbasiertes Authoring ermöglicht es jedem, ohne Training Inhalte zu erstellen, indem alle bekannten Tools genutzt werden: Word- und Google-Dokumente. Mit diesen einfachen Tools können Edge Delivery Services eine Änderung sofort in ein Word-Dokument umwandeln, um den Inhalt auf Ihrer Live-Site zu aktualisieren.

Weitere Informationen zur Verwendung von dokumentbasiertem Authoring finden Sie im Dokument [Authoring und Veröffentlichen von Inhalten](https://www.aem.live/docs/authoring) .

## Ist Edge richtig für Sie? {#decision}

Adobe hat erlebt, dass seine Kunden und ihre beteiligten Interessengruppen von Edge Delivery Services über Projekte aller Größenordnungen hinweg massiv profitieren. Aus diesem Grund empfiehlt Adobe die Nutzung von Edge Delivery Services als Ausgangspunkt für jedes neue Projekt.

Es ist auch möglich, eine Untergruppe von Sites oder Seiten in Edge Delivery bereitzustellen, während der Rest auf dem aktuellen Stapel verbleibt. Dies wird immer dann empfohlen, wenn Leistungsverbesserungen, organischer Traffic, Kundeninteraktion, Entwickler oder Content Velocity erforderlich sind.

Wenden Sie sich an Ihren Adobe-Support-Mitarbeiter, wenn Sie sich nicht sicher sind, ob Edge Delivery für Sie geeignet ist.

### Was ist mit Edge Delivery und Headless? (#headless)

Edge Delivery ist ein leistungsorientierter Kopf, der vom Backend entkoppelt ist. Wenn Sie über einen benutzerdefinierten Kopf verfügen, z. B. React SPA, empfiehlt Adobe das AEM Headless-Integrationsmuster. Weitere Informationen finden Sie in der Dokumentation zu [AEM Headless](/help/headless/introduction.md) .

Im Allgemeinen empfiehlt Adobe jedoch die Verwendung von Edge Delivery als Standardkopfbereich, um von der Geschwindigkeit und Leistung zu profitieren und den Headless-Teil Ihres Projekts (in der Regel die Geschäftsanwendung) über einen Headless-Ansatz (z. B. React oder SPA) zu integrieren.
