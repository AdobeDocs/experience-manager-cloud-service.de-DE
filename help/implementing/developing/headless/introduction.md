---
title: Eigenständige Entwicklung für AEM Sites als Cloud Service
description: Mithilfe leistungsstarker Funktionen wie Inhaltsmodelle, Inhaltsfragmente und die Grafik-QL-API können AEM als Cloud Service Ihre Erlebnisse zentral verwalten und sie über Kanal hinweg bereitstellen.
translation-type: tm+mt
source-git-commit: e1db93e8f4cf8ef881b274879e800c9993753a66
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 4%

---


# Headless Development for AEM Sites as Cloud Service {#headless-development}

Mithilfe leistungsstarker Funktionen wie Inhaltsmodelle, Inhaltsfragmente und die Grafik-QL-API können AEM als Cloud Service Ihre Erlebnisse zentral verwalten und sie über Kanal hinweg bereitstellen.

## Überblick {#overview}

Die Implementierung ohne Kopf wird immer wichtiger, wenn Sie Erlebnisse für Ihre Audience bereitstellen möchten, egal wo sie sich befinden und unabhängig vom Kanal.

Die Implementierung ohne Kopf verzichtet auf das Seiten- und Komponentenmanagement, wie es bei Vollstapel- und Hybridlösungen üblich ist, und konzentriert sich auf die Erstellung von Kanal-neutralen, wiederverwendbaren Inhaltsfragmenten und deren Cross-Kanal-Versand. Es handelt sich um ein modernes und dynamisches Entwicklungsmuster zur Implementierung von Web-Erlebnissen.

![AEM](assets/aem-implementation-models.png)

## Vergleich von Headful und Headless {#headful-headless}

Dieses Dokument konzentriert sich auf das vollständige, kostenlose Implementierungsmodell von AEM. Egal, ob Kopf- oder Kopflos eine binäre Wahl in AEM sein müssen. Kopflose Funktionen können verwendet werden, um Inhalte zu verwalten und an verschiedene Endpunkte bereitzustellen und Ihren Inhaltserstellern gleichzeitig die Bearbeitung von Einzelseitenanwendungen zu ermöglichen. Alles in AEM.

>[!TIP]
>
>Weitere Informationen finden Sie im Dokument [Kopflos und Kopflos in AEM](/help/implementing/developing/headful-headless.md).

## AEM als Cloud Service und ohne Kopf {#aem-headless}

AEM als Cloud Service ist ein flexibles Instrument für das kostenlose Implementierungsmodell, das drei leistungsstarke Dienste anbietet:

1. Inhaltsmodelle
   * Inhaltsmodelle sind strukturierte Darstellungen von Inhalten.
   * Diese werden von Informationsarchitekten im Editor AEM Content Fragment Model definiert.
   * Inhaltsmodelle dienen als Grundlage für Inhaltsfragmente.
1. Inhaltsfragmente
   * Inhaltsfragmente sind Instanziierungen von Inhaltsmodellen.
   * Diese werden von Inhaltserstellern mit dem Content Fragment-Editor AEM.
   * Sie werden in AEM Assets gespeichert und in der Admin-Benutzeroberfläche von Assets verwaltet.
1. Content API für Versand
   * Die AEM GraphQL API unterstützt Content Fragment Versand.
   * Die AEM Assets REST API unterstützt Content Fragment CRUD-Vorgänge.
   * Der Versand für direkte Inhalte ist auch beim JSON-Export der [Inhaltsfragment-Core-Komponente möglich.](https://docs.adobe.com/content/help/de/experience-manager-core-components/using/components/content-fragment-component.html)

## Kopflose Erste Schritte - Guides {#getting-started}

Die Kopflosen-Anleitungen für erste Schritte beschreiben einen einfachen Weg zum Erstellen, Verwalten und Bereitstellen von Erlebnissen mithilfe von AEM als Cloud Service in fünf Schritten. Jeder Leitfaden baut auf dem vorherigen auf, daher wird empfohlen, sie gründlich und in der Reihenfolge zu erkunden.

1. [Erstellen einer Konfiguration](getting-started/create-configuration.md)
1. [Erstellen eines Inhaltsfragmentmodells](getting-started/create-content-model.md)
1. [Erstellen eines Asset-Ordners](getting-started/create-assets-folder.md)
1. [Erstellen eines Inhaltsfragments](getting-started/create-content-fragment.md)
1. [Zugriff auf Inhaltsfragmente und Bereitstellung](getting-started/create-api-request.md)

## Audience {#audience}

Die unter [Kopflose Erste Schritte](#getting-started) beschriebenen Aufgaben sind erforderlich für eine grundlegende durchgängige Demonstration AEM Kopflosen Funktionen. Jeder Benutzer mit Administratorzugriff auf eine AEM Testinstanz kann diesen Leitfäden folgen, um den Kopflosen Versand in AEM zu verstehen, obwohl jemand mit Entwicklererfahrung ideal ist.

In einer Produktionssituation werden die Aufgaben jedoch von verschiedenen Personen unterschiedlich oft ausgeführt. Beispiel:

* **** Administratoren müssen die anfängliche Konfigurations- und Ordnerstruktur für den Inhalt normalerweise nur einmal oder sporadisch einrichten.
* **Informationsarchitekten** werden im Allgemeinen neue Modelle hinzufügen, wenn sich die Bedürfnisse der Organisation entwickeln.
* **Inhaltsautoren** erstellen kontinuierlich neue Inhalte als Inhaltsfragmente basierend auf den von den Architekten definierten Modellen.

In den Kopflosen-Handbüchern &quot;Erste Schritte&quot;wird darauf hingewiesen, wer im Allgemeinen die beschriebenen Aufgaben durchführen würde und wie häufig.

## Nächster Schritt {#next-step}

Sind Sie bereit, mehr zu erfahren? Beginnen Sie dann mit dem ersten Teil des Leitfadens zu den kostenlosen Einstieg: [Erstellen einer Konfiguration.](getting-started/create-configuration.md)
