---
title: Einführung in AEM Headless
description: Lernen Sie Adobe Experience Manager (AEM) als Headless-CMS mit einer Kombination aus ausführlicher Dokumentation und Headless-Journeys kennen. Erfahren Sie, wie Funktionen wie Inhaltsmodelle, Inhaltsfragmente und eine GraphQL-API verwendet werden, um Headless-Erlebnisse zu ermöglichen.
landing-page-description: Erfahren Sie, wie Sie Experience Manager Headless as a Cloud Service verwenden und verwalten können.
exl-id: 24300499-ae9c-49d0-aa25-f51e14d9cf79
source-git-commit: 4e64683598ced4b9811e957082932971f0ec0bb1
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Einführung in Adobe Experience Manager as a Headless CMS {#introduction-aem-headless}

Erfahren Sie, wie Sie Adobe Experience Manager (AEM) als Headless-CMS mit Funktionen wie Inhaltsmodellen, Inhaltsfragmenten und einer GraphQL-API verwenden, die Headless-Erlebnisse skaliert bereitstellt.

Sie können die ausführliche Dokumentation der verschiedenen Funktionen lesen und/oder der Auswahl der [Headless-Journey für einen Überblick über die ersten Schritte](#first-steps).

>[!NOTE]
>
>Siehe auch [Was ist Headless?](/help/headless/what-is-headless.md) für eine Einführung in Headless-Konzepte und -Terminologie.

## Übersicht {#overview}

AEM Headless ist eine CMS-Lösung aus Experience Manager, mit der strukturierte Inhalte (Inhaltsfragmente) in AEM von jeder App über HTTP mithilfe von GraphQL genutzt werden können. Headless-Implementierungen ermöglichen die skalierte Bereitstellung von Erlebnissen über Plattformen und Kanäle hinweg.

Die Headless-Implementierung verzichtet auf das Seiten- und Komponenten-Management, wie es bei Full-Stack- und Hybrid-Lösungen üblich ist, und konzentriert sich auf die Erstellung kanalneutraler, wiederverwendbarer Inhaltsfragmente und deren kanalübergreifende Bereitstellung. Es handelt sich um ein modernes und dynamisches Entwicklungsmuster zur Implementierung von Web-Erlebnissen.

![AEM-Implementierungsmodelle](assets/aem-implementation-models.png)

## Funktionen von AEM Headless {#aem-headless-features}

AEM as a Cloud Service ist ein flexibles Tool für das Headless-Implementierungsmodell, das drei leistungsstarke Funktionen bietet:

1. **Inhaltsmodelle**
   * Inhaltsmodelle sind strukturierte Darstellungen von Inhalten.
   * Inhaltsmodelle werden von Informationsarchitekten im Inhaltsfragmentmodell-Editor in AEM definiert.
   * Inhaltsmodelle dienen als Grundlage für Inhaltsfragmente.
1. **Inhaltsfragmente**
   * Inhaltsfragmente werden basierend auf einem Inhaltsmodell erstellt.
   * Sie werden von Inhaltsautoren mit dem Inhaltsfragment-Editor in AEM erstellt.
   * Inhaltsfragmente werden in AEM Assets gespeichert und in der Administrator-Benutzeroberfläche von Assets verwaltet.
1. **Inhalts-API für die Bereitstellung**
   * Die AEM-GraphQL-API unterstützt die Bereitstellung von Inhaltsfragmenten.
   * Die AEM Assets-REST-API unterstützt CRUD-Vorgänge für Inhaltsfragmente.
   * Die direkte Bereitstellung von Inhalten ist auch mit dem [JSON-Export der Inhaltsfragment-Kernkomponente](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html?lang=de) möglich.

## Erste Schritte mit AEM Headless {#first-steps}

Für die ersten Schritte mit AEM Headless-Funktionen stehen verschiedene Ressourcen zur Verfügung. Jeder Leitfaden ist auf verschiedene Anwendungsfälle und Zielgruppen zugeschnitten.

| Ressource | Beschreibung | Typ | Zielgruppe | Schätzung Zeit |
|---|---|---|---|---|
| [Headless-Entwickler-Tour](/help/journey-headless/developer/overview.md) | **Entwickler, die noch nicht mit AEM- und Headless**-Technologien vertraut sind, erhalten hier eine umfassende Einführung in AEM und seine Headless-Funktionen, von der Theorie des Headless-Systems bis zum Go-Live Ihres ersten Headless-Projekts. | -Anleitung | Entwickler **neu für AEM und Headless** | 1 Stunde |
| [Headless-Einrichtung](/help/headless/setup/introduction.md) | **Erfahrene AEM-Anwender**, die eine kurze Zusammenfassung der wichtigsten AEM-Headless-Funktionen benötigen, sollten sich diesen Schnellstart-Überblick ansehen. | Referenz-Setup | Entwickler, Administratoren **mit AEM-Erfahrung** | 20 Minuten |
| [Praktisches Headless-Tutorial](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/overview.html?lang=de) | **Wenn Sie einen praxisnahen Ansatz bevorzugen und mit AEM vertraut sind**: dieses Tutorial steigt direkt in die Implementierung einer einfachen Headless-App ein. | Tutorial | Entwickler | 2 Stunden |
| [Headless-Architekten-Tour](/help/journey-headless/architect/overview.md) | **Architekten, die noch nicht mit AEM und Headless-Technologien vertraut sind**, beginnen hier mit einer Einführung in die leistungsstarken, flexiblen Headless-Funktionen von Adobe Experience Manager as a Cloud Service und erfahren, wie man Inhalte für ein Projekt modellieren kann. | -Anleitung | Architekten | 1 Stunde |
| [Headless-Authoring-Tour](/help/journey-headless/author/overview.md) | **Geschäftsanwender, die AEM und Headless-Technologien noch nicht kennen**, beginnen hier mit einer Einführung in die leistungsstarken, flexiblen, Headless-Funktionen von Adobe Experience Manager as a Cloud Service und wie man Inhalte für ein Projekt modellieren kann. | -Anleitung | Inhaltsersteller | 1 Stunde |
| [Headless-Übersetzungs-Tour](/help/journey-headless/translation/overview.md) | Für diejenigen, die sich für den **Übersetzungsansatz von AEM für Headless interessieren.**. Erfahren Sie mehr über Headless-Technologien und wie Sie Übersetzungsprojekte in AEM von A bis Z erstellen und aktualisieren können. | -Anleitung | Übersetzungsspezialisten | 1 Stunde |

## Vergleich von Headful und Headless {#headful-headless}

Diese Anleitung konzentriert sich auf das vollständige Headless-Implementierungsmodell von AEM. In AEM muss die Entscheidung zwischen Headful und Headless aber keine Entweder-Oder-Entscheidung sein. Headless-Funktionen können verwendet werden, um Inhalte zu verwalten und für verschiedene Endpunkte bereitzustellen sowie um Inhaltserstellern gleichzeitig die Bearbeitung von Einzelseiten-Webanwendungen zu ermöglichen. Alles in AEM.

>[!TIP]
>
>Weitere Informationen finden Sie im Dokument [Headful und Headless in AEM](/help/implementing/developing/headful-headless.md).