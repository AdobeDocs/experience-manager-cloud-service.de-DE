---
title: Verwenden von Edge Delivery Services mit vorhandenen AEM
description: Erfahren Sie, wie Sie die Vorteile von Edge Delivery Services für Ihre bestehenden AEM nutzen können.
feature: Edge Delivery Services
source-git-commit: 22a791311c618fcbd61f321b8efa79c3a52ec65d
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---


# Verwenden von Edge Delivery Services mit vorhandenen AEM {#existing-projects}

Sie müssen nicht warten, bis ein neues AEM-Projekt von den Edge Delivery Services profitiert. Edge Delivery Services können in Ihr bestehendes AEM integriert werden, damit Sie sofort die Leistungssteigerung nutzen können.

## Einschränkungen des AEM Seiteneditors {#page-editor}

Vor der Einführung von Edge Delivery Services wurden in AEM verwaltete Inhalte mit dem AEM Seiteneditor bearbeitet. Wenn Ihr Projekt vor der Einführung von Edge Delivery Services begann, ist es fast sicher, dass Sie den Seiteneditor verwenden.

Der AEM Seiteneditor funktioniert nur mit [AEM](/help/implementing/developing/components/overview.md) wie z. B. [Kernkomponenten.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) Diese Komponenten sind mit Edge Delivery Services inkompatibel. Daher sind zwei Phasen erforderlich, um Edge Delivery Services zu einem bestehenden AEM-Projekt einzuführen:

* [Phase 1 - Frontend ersetzen](#replace-front-end)
* [Phase 2: Wechsel zum universellen Editor](#switch-ue)

## Phase 1 - Frontend ersetzen {#replace-front-end}

In Phase 1 können Sie weiterhin Ihre vorhandene AEM Site-Struktur, Komponenten und Authoring-Tools verwenden. Das Website-Rendering wird mithilfe von Bausteinen mit JavaScript und CSS neu erstellt und über Edge Delivery Services bereitgestellt.

Lesen Sie hierzu die [Build-Abschnitt](/help/edge/developer/block-collection.md) Weitere Informationen zu Bausteinen und zur Entwicklung für Edge-Bereitstellungsdienste finden Sie in der Edge Delivery Services-Dokumentation .

Ein Konverter in App Builder ist erforderlich, um die AEM gerenderte HTML-Ausgabe zu konvertieren und an Edge Delivery Services zu senden.

![Der Inhaltskonverter im Veröffentlichungsfluss](assets/content-converter.png)

In Phase zwei wird der Prozess abgeschlossen, indem die Technologieüberschneidung beseitigt wird: AEM Kernkomponenten mit HTL und Java in AEM Author, JS-basierte Blöcke in der Edge-Bereitstellung und ein nodeJS-basierter Konverter.

## Phase 2: Wechsel zum universellen Editor {#switch-ue}

In dieser Phase wird der AEM Seiteneditor durch den universellen Editor ersetzt. Da der universelle Editor direkt mit Bausteinen arbeiten kann, sind die AEM Kernkomponenten und der Konverter nicht mehr erforderlich.

## Erste Schritte {#how-to-get-started}

Wenden Sie sich an Ihren Adobe-Support-Mitarbeiter, um Zugriff auf diese Funktion zu erhalten.
