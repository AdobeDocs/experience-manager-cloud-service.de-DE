---
title: Universeller Editor – Versionshinweise für 2024.12.02
description: Dies sind die Versionshinweise für die Version 2024.12.02 des universellen Editors.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: 2aae8c63358680758e4f5324f38dea1bc2c47155
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 16%

---


# Universeller Editor – Versionshinweise für 2024.12.02 {#release-notes}

Dies sind die Versionshinweise für die Version des Universal Editors vom 2. Dezember 2024.

>[!TIP]
>
>Auf [dieser Seite](/help/release-notes/release-notes-cloud/release-notes-current.md) finden Sie die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service.

## Neue Funktionen {#what-is-new}

* **Tastaturnavigation der Inhaltsstruktur**: [Die Inhaltsstruktur,](/help/sites-cloud/authoring/universal-editor/navigation.md#content-tree-mode), die im Seitenbereich verfügbar ist, ist jetzt über die Tastatur vollständig zugänglich.
   * Autoren können mithilfe von Standardtastatursteuerelementen unter Einhaltung der [WCAG 2.1-Richtlinien](/help/sites-cloud/authoring/page-editor/accessible-content.md) für die Barrierefreiheit mit Baumansichtselementen navigieren und mit ihnen interagieren.
   * Diese Verbesserung stellt sicher, dass alle interaktiven Elemente im Baum mit der Tastatur bedient werden können, wodurch die Inklusivität für Benutzer verbessert wird, die auf die Tastaturnavigation angewiesen sind.
* **Abwahl der bearbeitbaren Elemente aufheben**: Autoren können jetzt die Auswahl der zuvor ausgewählten bearbeitbaren Elemente auf der Seite aufheben.
   * Dadurch werden Ablenkungen beseitigt, wenn Autoren die Seite ohne aktive Auswahlgrenzen anzeigen möchten.
* **Fragmentauswahl**: Auf AEM as a Cloud Service-Instanzen öffnen Fragmentverweise jetzt die Fragmentauswahl als Inhaltsauswahl. Dies bietet verbesserte Funktionen wie das Befolgen erlaubter Inhaltsfragmentmodelle, die Suche nach Inhaltsfragmenten und ein verbessertes Gesamterlebnis.
   * Dies passt zu anderen Adobe-Benutzeroberflächen und verbessert die Konsistenz.
   * [Für AEM 6.5-Umgebungen bleibt ](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/implementing/developing/headless/universal-editor/introduction) die vorhandene Inhaltsauswahl in Verwendung.
* **Container-Beschreibung**: [Die Container-Komponente](/help/implementing/universal-editor/field-types.md#container), die im Bereich [Eigenschaften} verwendet wird, ](/help/sites-cloud/authoring/universal-editor/navigation.md#properties-panel-properties-rail) zum Verweisen auf Inhalte, unterstützt jetzt ein Beschreibungsattribut, das über den Containerfeldern angezeigt wird.
   * Dieser Zusatz verbessert die Klarheit, indem er Autoren einen Kontext zu den gruppierten Feldern bereitstellt, die sie bearbeiten.

## Andere Verbesserungen {#other-improvements}

* **Rich-Text-Feldsynchronisierung**: Die Synchronisierung von Roh- und wiedergegebenen Inhalten in Rich-Text-Feldern im Eigenschaftenbereich wurde verbessert, um Probleme innerhalb von Edge Delivery Services-Projekten zu beheben, bei denen Rich-Text-Inhalte und die wiedergegebene Darstellung unterschiedlich sein können.
* **Bearbeitungsmodusereignisse**: Der Universal Editor sendet jetzt zuverlässig Bearbeitungsmodusereignisse, auch nach dem Neuladen von Remote-Apps.
