---
title: Headless-Entwicklung für AEM Sites as a Cloud Service
description: Mithilfe leistungsstarker Funktionen wie Inhaltsmodelle, Inhaltsfragmente und die GraphQL-API können Sie mit AEM as a Cloud Service Ihre Erlebnisse zentral verwalten und kanalübergreifend bereitstellen.
translation-type: tm+mt
source-git-commit: e1db93e8f4cf8ef881b274879e800c9993753a66
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 100%

---


# Headless-Entwicklung für AEM Sites as a Cloud Service {#headless-development}

Mithilfe leistungsstarker Funktionen wie Inhaltsmodelle, Inhaltsfragmente und die GraphQL-API können Sie mit AEM as a Cloud Service Ihre Erlebnisse zentral verwalten und kanalübergreifend bereitstellen.

## Übersicht {#overview}

Die Headless-Implementierung wird immer wichtiger, wenn es darum geht, Erlebnisse für Ihr Zielgruppe überall und unabhängig vom Kanal bereitzustellen.

Die Headless-Implementierung verzichtet auf das Seiten- und Komponenten-Management, wie es bei Full-Stack- und Hybrid-Lösungen üblich ist, und konzentriert sich auf die Erstellung kanalneutraler, wiederverwendbarer Inhaltsfragmente und deren kanalübergreifende Bereitstellung. Es handelt sich um ein modernes und dynamisches Entwicklungsmuster zur Implementierung von Web-Erlebnissen.

![AEM-Implementierungsmodelle](assets/aem-implementation-models.png)

## Vergleich von Headful und Headless {#headful-headless}

Dieses Dokument konzentriert sich auf das vollständige Headless-Implementierungsmodell von AEM. In AEM muss die Entscheidung zwischen Headful und Headless aber keine Entweder-Oder-Entscheidung sein. Headless-Funktionen können verwendet werden, um Content zu verwalten und für verschiedene Endpunkte bereitzustellen sowie um Inhaltserstellern gleichzeitig die Bearbeitung von Single Page Applications zu ermöglichen. Alles in AEM.

>[!TIP]
>
>Weitere Informationen finden Sie im Dokument [Headful und Headless in AEM](/help/implementing/developing/headful-headless.md).

## AEM as a Cloud Service und Headless {#aem-headless}

AEM as a Cloud Service ist ein flexibles Tool für das Headless-Implementierungsmodell, das drei leistungsstarke Services bietet:

1. Inhaltsmodelle
   * Inhaltsmodelle sind strukturierte Darstellungen von Inhalten.
   * Diese werden von Informationsarchitekten im Inhaltsfragmentmodell-Editor in AEM definiert.
   * Inhaltsmodelle dienen als Grundlage für Inhaltsfragmente.
1. Inhaltsfragmente
   * Inhaltsfragmente sind Instanziierungen von Inhaltsmodellen.
   * Diese werden von Inhaltsautoren mit dem Inhaltsfragment-Editor in AEM erstellt.
   * Sie werden in AEM Assets gespeichert und in der Administrator-Benutzeroberfläche von Assets verwaltet.
1. Inhalts-API für die Bereitstellung
   * Die AEM-GraphQL-API unterstützt die Bereitstellung von Inhaltsfragmenten.
   * Die AEM Assets-REST-API unterstützt CRUD-Vorgänge für Inhaltsfragmente.
   * Die direkte Bereitstellung von Inhalten ist auch mit dem [JSON-Export der Kernkomponenten für Inhaltsfragmente](https://docs.adobe.com/content/help/de/experience-manager-core-components/using/components/content-fragment-component.html) möglich.

## Erste Schritte für Headless {#getting-started}

Die ersten Schritte für Headless zeigen einen einfachen Weg zum Erstellen, Verwalten und Bereitstellen von Erlebnissen mit AEM as a Cloud Service in fünf Schritten auf. Jedes Handbuch baut auf dem vorherigen auf, daher wird empfohlen, sie gründlich und in der richtigen Reihenfolge zu lesen.

1. [Erstellen einer Konfiguration](getting-started/create-configuration.md)
1. [Erstellen eines Inhaltsfragmentmodells](getting-started/create-content-model.md)
1. [Erstellen eines Asset-Ordners](getting-started/create-assets-folder.md)
1. [Erstellen eines Inhaltsfragments](getting-started/create-content-fragment.md)
1. [Aufrufen und Bereitstellen von Inhaltsfragmenten](getting-started/create-api-request.md)

## Audience {#audience}

Die in den [ersten Schritten für Headless](#getting-started) beschriebenen Aufgaben sind für eine grundlegende durchgängige Demonstration der Headless-Funktionen von AEM erforderlich. Jeder Benutzer mit Administratorzugriff auf eine AEM-Testinstanz kann diesen Handbüchern folgen, um die Headless-Bereitstellung in AEM zu verstehen, obwohl jemand mit Entwicklererfahrung ideal ist.

In einer Produktionssituation werden die Aufgaben jedoch von verschiedenen Personen unterschiedlich oft ausgeführt. Beispiel:

* **Administratoren** müssen die anfängliche Konfiguration und Ordnerstruktur für den Inhalt normalerweise nur einmal oder sporadisch einrichten.
* **Informationsarchitekten** fügen im Allgemeinen neue Modelle hinzu, wenn sich die Anforderungen der Organisation ändern.
* **Inhaltsautoren** erstellen kontinuierlich neue Inhalte als Inhaltsfragmente basierend auf den von den Architekten definierten Modellen.

In den ersten Schritten für Headless wird aufgezeigt, wer die beschriebenen Aufgaben in der Regel und wie häufig durchführt.

## Nächster Schritt {#next-step}

An weiteren Informationen interessiert? Dann lesen Sie zunächst den ersten Teil der ersten Schritte für Headless: [Erstellen einer Konfiguration.](getting-started/create-configuration.md)
