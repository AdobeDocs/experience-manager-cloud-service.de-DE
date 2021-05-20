---
title: Headless-Entwicklung für AEM Sites as a Cloud Service
description: Erfahren Sie, wie AEM leistungsstarke Headless-Funktionen wie Inhaltsmodelle, Inhaltsfragmente und die GraphQL-API eines Cloud Service zusammenarbeiten, um Ihnen die zentrale Verwaltung Ihrer Erlebnisse und deren kanalübergreifende Bereitstellung zu ermöglichen.
exl-id: 24300499-ae9c-49d0-aa25-f51e14d9cf79
source-git-commit: 469579cfe10227ab22bbe055d4c503d8ea978150
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 61%

---


# Headless-Entwicklung für AEM Sites as a Cloud Service {#headless-development}

Erfahren Sie, wie AEM leistungsstarke Headless-Funktionen wie Inhaltsmodelle, Inhaltsfragmente und die GraphQL-API eines Cloud Service zusammenarbeiten, um Ihnen die zentrale Verwaltung Ihrer Erlebnisse und deren kanalübergreifende Bereitstellung zu ermöglichen.

## Überblick {#overview}

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

## Ihre ersten Schritte mit AEM Headless {#first-steps}

Es stehen eine Reihe von Ressourcen zur Verfügung, mit denen Sie mit AEM Headless-Funktionen beginnen können. Sie sind für verschiedene Anwendungsfälle vorgesehen, bieten jedoch alle einen umfassenden Überblick über AEM Headless-Funktionen.

| Ressource | Beschreibung | Typ | Audience | Est. Zeit |
|---|---|---|---|---|
| [Headless-Entwickler-Journey](/help/implementing/developing/headless-journey/overview.md) | Beginnen Sie hier für einen umfassenden Überblick über AEM Headless-Features aus der Headless-Theorie bis hin zum Live-Start mit Ihrem ersten Headless-Projekt. | -Anleitung  | Entwickler | 1 Stunde |
| [Headless-Erste-Schritte-Handbuch](/help/implementing/developing/headless/getting-started/introduction.md) | Eine kurze Zusammenfassung der wichtigsten AEM Headless-Funktionen finden Sie in dieser Kurzanleitung. | Schnellstart | Entwickler, Administratoren | 20 Minuten |
| [Tutorial zu den ersten Schritten mit AEM Headless-Hands](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/overview.html) | Wenn Sie einen praxisnahen Ansatz bevorzugen, taucht dieses Tutorial direkt in die Erstellung eines einfachen Headless-Projekts ein. | Tutorial | Entwickler | 2 Stunden |
