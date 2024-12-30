---
title: Universeller Editor – Versionshinweise für 2024.12.02
description: Dies sind die Versionshinweise für die Version 2024.12.02 des universellen Editors.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: 2aae8c63358680758e4f5324f38dea1bc2c47155
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 100%

---


# Universeller Editor – Versionshinweise für 2024.12.02 {#release-notes}

Dies sind die Versionshinweise für die Version des universellen Editors vom 2. Dezember 2024.

>[!TIP]
>
>Auf [dieser Seite](/help/release-notes/release-notes-cloud/release-notes-current.md) finden Sie die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service.

## Neue Funktionen {#what-is-new}

* **Tastaturnavigation der Inhaltsstruktur**: [Die Inhaltsstruktur ](/help/sites-cloud/authoring/universal-editor/navigation.md#content-tree-mode), die im seitlichen Bedienfeld verfügbar ist, ist jetzt vollständig über die Tastatur zugänglich.
   * Autorinnen und Autoren können mithilfe von Standardtastatursteuerelementen unter Einhaltung der [WCAG 2.1-Richtlinien](/help/sites-cloud/authoring/page-editor/accessible-content.md) für die Barrierefreiheit in Elementen der Inhaltsstrukturansicht navigieren und mit ihnen interagieren.
   * Diese Verbesserung stellt sicher, dass alle interaktiven Elemente in der Inhaltsstruktur mit der Tastatur bedient werden können, wodurch die Zugänglichkeit für Benutzende verbessert wird, die auf die Tastaturnavigation angewiesen sind.
* **Abwahl von bearbeitbaren Elementen**: Autorinnen und Autoren können jetzt zuvor ausgewählte bearbeitbare Elemente auf der Seite abwählen.
   * Dadurch werden Ablenkungen beseitigt, wenn Autorinnen und Autoren die Seite ohne aktive Auswahlgrenzen anzeigen möchten.
* **Fragmentauswahl**: Auf Instanzen von AEM as a Cloud Service öffnen Fragmentverweise jetzt die Fragmentauswahl als Inhaltsauswahl. Dies bietet verbesserte Funktionen wie das Befolgen zulässiger Inhaltsfragmentmodelle, die Suche nach Inhaltsfragmenten und ein verbessertes Gesamterlebnis.
   * Dadurch wird die Konsistenz mit anderen Adobe-Benutzeroberflächen verbessert.
   * [Für AEM 6.5-Umgebungen](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/implementing/developing/headless/universal-editor/introduction) bleibt die vorhandene Inhaltsauswahl in Verwendung.
* **Container-Beschreibung**: [Die Container-Komponente](/help/implementing/universal-editor/field-types.md#container), die im [Bedienfeld „Eigenschaften“](/help/sites-cloud/authoring/universal-editor/navigation.md#properties-panel-properties-rail) zum Verweisen auf Inhalte verwendet wird, unterstützt jetzt ein Beschreibungsattribut, das über den Container-Feldern angezeigt wird.
   * Diese Ergänzung verbessert die Klarheit, indem sie Autorinnen und Autoren einen Kontext zu den gruppierten Feldern bereitstellt, die sie bearbeiten.

## Andere Verbesserungen {#other-improvements}

* **Rich-Text-Feldsynchronisierung**: Die Synchronisierung von Roh- und gerenderten Inhalten in Rich-Text-Feldern im Bedienfeld „Eigenschaften“ wurde verbessert, um Probleme innerhalb von Edge Delivery Services-Projekten zu beheben, bei denen Rich-Text-Inhalte und die gerenderte Darstellung unterschiedlich sein können.
* **Bearbeitungsmodus-Ereignisse**: Der universelle Editor sendet jetzt zuverlässig Bearbeitungsmodus-Ereignisse. Diese werden auch nach dem Neuladen von Remote-Apps gesendet.
