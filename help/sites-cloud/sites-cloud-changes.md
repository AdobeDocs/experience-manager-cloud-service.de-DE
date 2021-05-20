---
title: Wesentliche Änderungen an AEM Sites in AEM Cloud Service
description: Wesentliche Änderungen an AEM Sites in AEM Cloud Service
exl-id: 60b1aec4-75a0-459f-bf77-8d8c1af757ce
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 100%

---

# Wesentliche Änderungen an AEM Sites as a Cloud Service{#notable-changes}

AEM Sites as a Cloud Service stellt Experience-Management-Funktionen als Teil der Cloud-nativen Plattform AEM as a Cloud Service bereit. Neben den wichtigsten Vorteilen von AEM as a Cloud Service, wie der Cloud-nativen Skalierbarkeit, der Betriebszeit und der Aktualität, bietet AEM Sites as a Cloud Service auch eine Reihe von Sites-spezifischen Änderungen und Ergänzungen.

>[!NOTE]
>In diesem Dokument werden die wesentlichen Änderungen an AEM Sites aufgeführt. Allgemeine Änderungen an AEM as a Cloud Service und anderen Modulen finden Sie unter:
>
>* [Einführung in Adobe Experience Manager as a Cloud Service](/help/overview/introduction.md)
* [Übersicht über AEM as a Cloud Service – neue Funktionen und Unterschiede](/help/overview/what-is-new-and-different.md)
* [Architektur](/help/core-concepts/architecture.md) von Adobe Experience Manager as a Cloud Service
* [Wesentliche Änderungen an AEM as a Cloud Service (Versionshinweise)](/help/release-notes/aem-cloud-changes.md)
* [Wesentliche Änderungen an AEM Assets as a Cloud Service](/help/assets/assets-cloud-changes.md)
* [Einführung in AEM Assets as a Cloud Service](/help/assets/overview.md)
* [Tutorials zu Adobe Experience Manager as a Cloud Service](https://docs.adobe.com/content/help/en/experience-manager-learn/cloud-service/overview.html)


Änderungen und Ergänzungen an AEM Sites as a Cloud Service:

* [Asynchrone Seitenvorgänge](#asynchronous-page-operations)
* [Neue Referenz-Site und Tutorial](#new-reference-site-and-tutorial)

## Asynchrone Seitenvorgänge{#asynchronous-page-operations}

In AEM Cloud Service wurden Vorgänge, die die Benutzeroberfläche zuvor blockiert haben, in kleinere Aufgaben unterteilt, die im Hintergrund ausgeführt werden.

* Verschieben von Seiten
* Rollout von Seiten

Der Initiator solcher Aktionen kann ihren Status in einer neuen Benutzeroberfläche unter `/mnt/overlay/dam/gui/content/asyncjobs.html` überprüfen.

>[!NOTE]
Der Benutzer muss keine Änderungen am System vornehmen, um diese neue Funktion zu nutzen. Dies wird hier lediglich als eine Abweichung vom Verhalten vorheriger lokal bereitgestellten Versionen von AEM aufgeführt.

## Neue Referenz-Site und Tutorial{#new-reference-site-and-tutorial}

[WKND](https://wknd.site/), eine neue AEM-Referenz-Site, wurde aktualisiert und veröffentlicht, um die Best Practices für den Aufbau einer Website mit AEM sowie die umfassenden Funktionen, Komponenten und Bereitstellungsmodelle widerzuspiegeln, die in AEM verfügbar sind. Die neue Referenz-Site und das [dazugehörige Tutorial](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html) gehen auf grundlegende Themen wie Projekteinrichtung, Kernkomponenten, bearbeitbare Vorlagen, Client-Bibliotheken und Komponentenentwicklung mit Adobe Experience Manager Sites ein.

Zuvor wurde We.Retail standardmäßig mit AEM installiert (sofern die Site nicht im Produktionsmodus gestartet wurde). Von nun an erfolgt keine standardmäßige Installation einer Referenz-Site mehr. Stattdessen werden das [Git-Repository](https://github.com/adobe/aem-guides-wknd/) und das [zugehörige Tutorial](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html) mit dem aktualisierten Code der WKND-Referenz-Site bereitgestellt.

## Funktionen zur Laufzeit nicht verfügbar {#capabilities-not-available-at-runtime}

AEM as a Cloud Service ist immer verfügbar und auf dem neuesten Stand. Um dies zu erreichen, muss das AEM-Repository in unveränderliche und veränderliche Inhalte unterteilt und der Zugriff auf unveränderliche Inhalte zur Laufzeit unterbunden werden. Weitere Informationen zu veränderlichen und unveränderlichen Inhalten finden Sie unter [Veränderliche und unveränderliche Bereiche des Repositorys im Vergleich](/help/implementing/developing/introduction/aem-project-content-package-structure.md#mutable-vs-immutable).

Da zur Laufzeit nicht auf unveränderliche Inhalte zugegriffen werden kann, sind die folgenden AEM Sites-Vorgänge zur Laufzeit nicht verfügbar:

* I18n-Wörterbuch-Übersetzung
* Entwicklermodus im Seiten-Editor von AEM Sites

Diese Funktionen können über lokale, eigenständige Entwicklerinstanzen von AEM as a Cloud Service verwendet werden, um Inhalte und Code in AEM als GIT-Repository von AEM as a Cloud Service zu aktualisieren, jedoch nicht in gehosteten Laufzeitinstanzen.
