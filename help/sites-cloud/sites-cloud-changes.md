---
title: Wichtige Änderungen an AEM-Sites im AEM Cloud-Dienst
description: 'Wichtige Änderungen an AEM-Sites im AEM Cloud-Dienst '
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8

---


# Wichtige Änderungen an AEM-Sites als Cloud-Dienst {#notable-changes}

AEM-Sites als Cloud-Dienst bieten Erlebnisverwaltungsfunktionen als Teil der Cloud-nativen AEM als Cloud-Service-Plattform. Zusätzlich zu den wichtigsten Vorteilen von AEM als Cloud-Dienst wie Cloud-native Skalierbarkeit, Betriebszeit und immer auf dem neuesten Stand, bieten AEM-Sites als Cloud-Dienst eine Reihe von Site-spezifischen Änderungen und Ergänzungen.

>[!NOTE]
>In diesem Dokument werden die wesentlichen Änderungen an AEM-Sites hervorgehoben. Allgemeine Änderungen an AEM in der Cloud finden Sie unter:
>
>* [Wichtige Änderungen an Adobe Experience Manager (AEM) als Cloud-Dienst](/help/release-notes/aem-cloud-changes.md)


Änderungen und Ergänzungen an AEM-Sites als Cloud-Dienst:

* [Asynchrone Seitenvorgänge](#asynchronous-page-operations)
* [Neue Referenz-Website und Übung](#new-reference-site-and-tutorial)

## Asynchrone Seitenvorgänge {#asynchronous-page-operations}

Im AEM Cloud-Dienst wurden Vorgänge, die die Benutzeroberfläche traditionell blockiert haben, in kleinere Aufgaben unterteilt, die im Hintergrund ausgeführt werden.

* Seiten verschieben
* Roll-out-Seiten

Der Initiator solcher Aktionen kann ihren Status in einer neuen Benutzeroberfläche unter `/mnt/overlay/dam/gui/content/asyncjobs.html`.

>[!NOTE]
>
>Es sind keine Änderungen erforderlich, die der Benutzer des Systems benötigt, um diese neue Funktion zu nutzen. Es wird hier lediglich als Verhaltensänderung gegenüber früheren lokalen Versionen von AEM bezeichnet.

## Neue Referenz-Website und Übung {#new-reference-site-and-tutorial}

[WKND](https://wknd.site/), eine neue AEM-Referenz-Website, wurde aktualisiert und veröffentlicht, um die Best Practices für den Aufbau einer Website mit AEM sowie die umfassenden Funktionen, Komponenten und Bereitstellungsmodelle, die in AEM verfügbar sind, widerzuspiegeln. Die neue Referenz-Website und das [dazugehörige Lernprogramm](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html) behandeln grundlegende Themen wie Projekteinrichtung, Kernkomponenten, bearbeitbare Vorlagen, Client-Bibliotheken und Komponentenentwicklung mit Adobe Experience Manager-Sites.

Zuvor wurde Web.Retail standardmäßig mit AEM installiert (außer wenn es im Produktionsmodus gestartet wurde).  Jetzt wird eine Referenz-Website nicht standardmäßig installiert.  Stattdessen wird der [Git-Repo](https://github.com/adobe/aem-guides-wknd/) und das [zugehörige Lernprogramm](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html) mit dem aktualisierten WKND-Referenz-Website-Code bereitgestellt.

## Funktionen zur Laufzeit nicht verfügbar {#capabilities-not-available-at-runtime}

AEM als Cloud-Dienst ist immer auf dem neuesten Stand. Um dies zu erreichen, müssen Sie das AEM-Repository in unveränderbaren und veränderlichen Inhalten trennen und den Zugriff auf unveränderbaren Inhalt zur Laufzeit verbieten. Weitere Informationen zu veränderlichen oder unveränderlichen Inhalten finden Sie unter [Mutable und Immatable Bereiche des Repositorys](/help/implementing/developing/introduction/aem-project-content-package-structure.md#mutable-vs-immutable).

Da zur Laufzeit nicht auf unveränderlichen Inhalt zugegriffen werden kann, sind die folgenden AEM-Sites-Vorgänge zur Laufzeit nicht verfügbar:

* i18n-Wörterbuchübersetzung
* Entwicklermodus im AEM Sites-Seiten-Editor

Diese Funktionen können über lokale, eigenständige Entwicklerinstanzen von AEM als Cloud-Dienst verwendet werden, um Inhalte und Code in AEM als Cloud-Dienst-GIT-Repository zu aktualisieren, jedoch nicht in gehosteten Laufzeitinstanzen.
