---
title: Einführung in AEM Headless
description: Erfahren Sie mehr über Adobe Experience Manager (AEM) als Headless-CMS mit einer Kombination aus detaillierter Dokumentation und Headless-Journey. Erfahren Sie, wie Funktionen wie Inhaltsmodelle, Inhaltsfragmente und eine GraphQL-API verwendet werden, um Headless-Erlebnisse mit AEM zu unterstützen.
landing-page-description: Erfahren Sie, wie Sie Experience Manager Headless as a Cloud Service verwenden und verwalten können.
exl-id: 24300499-ae9c-49d0-aa25-f51e14d9cf79
source-git-commit: 2771dfde3b20f3867bc96dedd744d8dd7ab4fed9
workflow-type: tm+mt
source-wordcount: '656'
ht-degree: 35%

---


# Einführung in Adobe Experience Manager Headless  {#introduction-aem-headless}

Erfahren Sie, wie Funktionen von Adobe Experience Manager (AEM) wie Inhaltsmodelle, Inhaltsfragmente und eine GraphQL-API verwendet werden, um Headless-Erlebnisse bedarfsgerecht zu nutzen.

Sie können die detaillierte Dokumentation aller Funktionen lesen und/oder der Auswahl von [Headless-Journey als Schnellstart](#first-steps).

## Übersicht {#overview}

AEM Headless ist eine CMS-Lösung aus Experience Manager, mit der strukturierte Inhalte (Inhaltsfragmente) in AEM von jeder App über HTTP mithilfe von GraphQL genutzt werden können. Headless-Implementierungen ermöglichen die skalierte Bereitstellung von Erlebnissen über Plattformen und Kanäle hinweg.

Die Headless-Implementierung verzichtet auf das Seiten- und Komponenten-Management, wie es bei Full-Stack- und Hybrid-Lösungen üblich ist, und konzentriert sich auf die Erstellung kanalneutraler, wiederverwendbarer Inhaltsfragmente und deren kanalübergreifende Bereitstellung. Es handelt sich um ein modernes und dynamisches Entwicklungsmuster zur Implementierung von Web-Erlebnissen.

![AEM-Implementierungsmodelle](assets/aem-implementation-models.png)

## Funktionen AEM Headless {#aem-headless-features}

AEM as a Cloud Service ist ein flexibles Tool für Headless-Implementierungsmodelle mit drei leistungsstarken Funktionen:

1. **Inhaltsmodelle**
   * Inhaltsmodelle sind strukturierte Darstellungen von Inhalten.
   * Inhaltsmodelle werden von Informationsarchitekten im Editor AEM Inhaltsfragmentmodell definiert.
   * Inhaltsmodelle dienen als Grundlage für Inhaltsfragmente.
1. **Inhaltsfragmente**
   * Inhaltsfragmente werden basierend auf einem Inhaltsmodell erstellt.
   * Wird von Inhaltsautoren mit dem Inhaltsfragment-Editor AEM erstellt.
   * Inhaltsfragmente werden in AEM Assets gespeichert und in der Assets Admin-Benutzeroberfläche verwaltet.
1. **Inhalts-API für die Bereitstellung**
   * Die AEM-GraphQL-API unterstützt die Bereitstellung von Inhaltsfragmenten.
   * Die AEM Assets-REST-API unterstützt CRUD-Vorgänge für Inhaltsfragmente.
   * Die Bereitstellung von direkten Inhalten ist auch mit der [JSON-Export der Inhaltsfragment-Kernkomponente](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html?lang=de).

## Erste Schritte mit AEM Headless {#first-steps}

Für die ersten Schritte mit AEM Headless-Funktionen stehen verschiedene Ressourcen zur Verfügung. Jeder Leitfaden ist auf verschiedene Anwendungsfälle und Zielgruppen zugeschnitten.

| Ressource | Beschreibung | Typ | Zielgruppe | Schätzung Zeit |
|---|---|---|---|---|
| [Headless-Entwickler-Tour](/help/journey-headless/developer/overview.md) | **Für Entwickler, die neu AEM und Headless sind** Technologien, beginnen Sie hier für eine umfassende Einführung in AEM und seine Headless-Features von der Theorie des Headless-Lebens bis hin zu Ihrem ersten Headless-Projekt. | -Anleitung | Entwickler   **neu bei AEM und Headless** | 1 Stunde |
| [Headless-Einrichtung](/help/headless/setup/introduction.md) | **Erfahrene AEM-Anwender**, die eine kurze Zusammenfassung der wichtigsten AEM-Headless-Funktionen benötigen, sollten sich diesen Schnellstart-Überblick ansehen. | Referenz-Setup | Entwickler, Administratoren **mit AEM Erlebnis** | 20 Minuten |
| [Headless-Handy-Tutorial](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/overview.html?lang=de) | **Wenn Sie einen praxisnahen Ansatz bevorzugen und mit AEM vertraut sind** verwendet wird, taucht dieses Tutorial direkt in die Implementierung einer einfachen Headless-App ein. | Tutorial | Entwickler | 2 Stunden |
| [Headless-Architekten-Tour](/help/journey-headless/architect/overview.md) | **Für Architekten, die neu AEM und Headless sind** Technologien, beginnen Sie hier mit einer Einführung in die leistungsstarken, flexiblen, Headless-Funktionen von Adobe Experience Manager as a Cloud Service und wie Sie Inhalte für Ihr Projekt modellieren können. | -Anleitung | Architekten | 1 Stunde |
| [Headless-Authoring-Tour](/help/journey-headless/author/overview.md) | **Für Geschäftsbenutzer, die neu AEM und Headless sind** Technologien, beginnen Sie hier mit einer Einführung in die leistungsstarken, flexiblen, Headless-Funktionen von Adobe Experience Manager as a Cloud Service und wie Sie Inhalte für Ihr Projekt modellieren können. | -Anleitung | Inhaltsersteller | 1 Stunde |
| [Headless-Übersetzungs-Tour](/help/journey-headless/translation/overview.md) | Für diese **Interesse an AEM Übersetzungskonzept für Headless**. Erfahren Sie mehr über Headless-Technologien und wie Sie Übersetzungsprojekte in AEM von A bis Z erstellen und aktualisieren können. | -Anleitung | Übersetzungsspezialisten | 1 Stunde |

## Vergleich von Headful und Headless {#headful-headless}

Dieses Handbuch konzentriert sich auf das vollständige Headless-Implementierungsmodell von AEM. In AEM muss die Entscheidung zwischen Headful und Headless aber keine Entweder-Oder-Entscheidung sein. Headless-Funktionen können verwendet werden, um Inhalte für mehrere Touchpoints zu verwalten und bereitzustellen und gleichzeitig Autoren von Inhalten die Bearbeitung von Single Page Applications zu ermöglichen. Alles in AEM.

>[!TIP]
>
>Weitere Informationen finden Sie im Dokument [Headful und Headless in AEM](/help/implementing/developing/headful-headless.md).