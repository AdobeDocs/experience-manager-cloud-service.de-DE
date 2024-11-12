---
title: Laufende Sites-Funktionen für Edge Delivery Services
description: Erfahren Sie, welche AEM Sites-Funktionen und -Anwendungsfälle in Bearbeitung sind, und lernen Sie alternative Lösungen bei der Verwendung von Edge Delivery Services kennen.
solution: Experience Manager Sites
feature: Edge Delivery Services
role: User
exl-id: 21745f53-a7ef-4eec-9170-b267c2f4314e
source-git-commit: dbe4cd619f4dc680e6fc4826f6a4fea92bab9707
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 4%

---

# Laufende Sites-Funktionen für Edge Delivery Services {#wip-sites-features}

Erfahren Sie, welche AEM Sites-Funktionen und -Anwendungsfälle in Bearbeitung sind, und lernen Sie alternative Lösungen bei der Verwendung von Edge Delivery Services kennen.

>[!TIP]
>
>Laufende Arbeiten bedeuten nicht das Ende des Weges. Wenn Sie eine Funktion oder einen Anwendungsfall benötigen, die bzw. der in diesem Dokument als derzeit in Bearbeitung aufgeführt ist, wenden Sie sich an Ihren Adobe-Support-Mitarbeiter. Sie und Adobe können zusammenarbeiten, um Ihre besonderen Bedürfnisse zu verstehen und alternative Lösungen zu finden.

## Laufende Funktionen {#wip-features}

Bei der Verwendung von Edge Delivery Services mit AEM Sites sind die meisten Sites-Funktionen verfügbar. So kann beispielsweise fast jede in der [Sites-Konsole](/help/sites-cloud/authoring/sites-console/introduction.md) verfügbare Aktion auf Edge Delivery Services angewendet werden.

Bei einigen Funktionen handelt es sich jedoch um laufende Arbeiten (WIP). WIP-Funktionen sind Funktionen der Sites-Konsole, die entweder noch nicht für Edge Delivery Services mit AEM Sites verfügbar sind oder nur teilweise verfügbar sind. Aus diesem Grund können WIP-Funktionen anders als ihre Sites-Gegenstücke dargestellt werden oder es gibt alternative Lösungen für den Anwendungsfall.

Die folgende Liste enthält solche WIP-Funktionen und alternative Lösungen. Wenn für Ihr Projekt eine WIP-Funktion erforderlich ist, lesen Sie bitte die unten vorgeschlagenen Alternativen und wenden Sie sich an Adobe, um zusammenzuarbeiten, um Ihren Anwendungsfall zu verstehen.

| Sites-Funktion | Status in Edge | Anmerkungen | Dokumentation zu Edge |
|---|---|---|---|
| [Seitenvererbung](/help/sites-cloud/administering/msm-and-translation.md) | Verfügbar |  | [Inhaltsvererbung im universellen Editor](/help/sites-cloud/authoring/universal-editor/inheritance.md) |
| [Komponentenvererbung](/help/sites-cloud/administering/msm-and-translation.md) | Teilweise verfügbar | Komponenten übernehmen Inhalte, die Vererbung kann jedoch nur auf Seitenebene rückgängig gemacht werden | [Inhaltsvererbung im universellen Editor](/help/sites-cloud/authoring/universal-editor/inheritance.md) |
| [Sprachkopie](/help/sites-cloud/administering/translation/overview.md) | Teilweise verfügbar | Komponenten übernehmen Inhalte, die Vererbung kann jedoch nur auf Seitenebene rückgängig gemacht werden | [Inhaltsvererbung im universellen Editor](/help/sites-cloud/authoring/universal-editor/inheritance.md) |
| [Multi-Site-Management](/help/sites-cloud/administering/msm/overview.md) | Teilweise verfügbar | Komponenten übernehmen Inhalte, die Vererbung kann jedoch nur auf Seitenebene rückgängig gemacht werden | [Inhaltsvererbung im universellen Editor](/help/sites-cloud/authoring/universal-editor/inheritance.md) |
| [Launches](/help/sites-cloud/authoring/launches/overview.md) | Teilweise verfügbar | Komponenten übernehmen Inhalte, die Vererbung kann jedoch nur auf Seitenebene rückgängig gemacht werden | [Inhaltsvererbung im universellen Editor](/help/sites-cloud/authoring/universal-editor/inheritance.md) |
| [Seitenvorlagen](/help/sites-cloud/authoring/page-editor/templates.md) | Bald! | Aus Vorlagen erstellte Seiten sind unabhängige Kopien der ursprünglichen Vorlage. | [Verwenden von Seitenvorlagen mit dem universellen Editor](/help/sites-cloud/authoring/universal-editor/templates.md) |
| [ContextHub und Targeting](/help/sites-cloud/authoring/personalization/overview.md) | Nicht verfügbar |  |  |
| [Timewarp](/help/sites-cloud/authoring/launches/preview.md) | Nicht verfügbar |  |  |
| [Zugehörige Inhalte](/help/sites-cloud/authoring/page-editor/editor-side-panel.md#associated-content-browser) | Nicht verfügbar |  |  |
| [Experience Fragments](/help/sites-cloud/authoring/fragments/experience-fragments.md) | Alternative | Erstellen einer Seite und Verwenden einer Fragmentkomponente |  |

## Nutzungsszenarios für laufende Arbeiten {#wip-use-cases}

Da Edge Delivery Services auf einem völlig neuen und modernen Technologiestapel basieren, sind die folgenden Anwendungsfälle von AEM Sites noch nicht vollständig abgedeckt und werden derzeit bearbeitet. Wenn für Ihr Projekt ein WIP-Anwendungsfall erforderlich ist, wenden Sie sich an Adobe, um zusammenzuarbeiten und die Anforderungen Ihres Projekts zu verstehen.

| Nutzungsszenario für Sites | Details |
|---|---|
| Serverseitige Logik zum Rendern von Seiten | Verwenden AEM Laufzeitumgebung als Anwendungsserver |
| Dynamische Seiten | SSI oder jede dynamische Include-Technik |
| Benutzerverwaltung | Verwenden von AEM als IdP |
| Authentifizierung | Verwenden von AEM für sichere Inhalte |
| Inhaltsberechtigungen | AEM als sicheres Extranet |
