---
title: Arbeiten mit Workflows
description: Mit Workflows in AEM können Sie eine Reihe von Schritten automatisieren, die auf einer Seite oder einem Asset ausgeführt werden.
exl-id: ed157646-abb3-45c6-bafd-7889bd93fdf3
source-git-commit: 5ad33f0173afd68d8868b088ff5e20fc9f58ad5a
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 72%

---

# Arbeiten mit Workflows {#working-with-workflows}

AEM Workflows ermöglichen die Automatisierung einer Reihe von Schritten, die auf (einer oder mehreren) Seiten und/oder Assets ausgeführt werden.

Beispielsweise muss beim Veröffentlichen ein Editor den Inhalt überprüfen, bevor eine oder ein Site-Admindie Seite aktiviert. Ein Workflow, der dieses Beispiel automatisiert, benachrichtigt jeden Teilnehmer, wenn es Zeit ist, die erforderlichen Arbeiten auszuführen:

1. Die Autorin oder der Autor wendet den Workflow auf die Seite an.
1. Der Editor erhält ein Arbeitselement, das angibt, dass er den Seiteninhalt überprüfen muss. Wenn sie fertig sind, geben sie an, dass ihr Arbeitselement abgeschlossen ist.
1. Die Site-Administratorin bzw. der Site-Administrator erhält dann ein Arbeitselement, das die Aktivierung der Seite anfordert. Wenn sie fertig sind, geben sie an, dass ihr Arbeitselement abgeschlossen ist.

In der Regel gilt Folgendes:

* Inhaltsautoren wenden Workflows auf Seiten an und nehmen an Workflows teil.
* Die von Ihnen verwendeten Workflows sind spezifisch für die Geschäftsprozesse Ihres Unternehmens.

Die folgenden Seiten behandeln:

* [Anwenden von Workflows auf Seiten](/help/sites-cloud/authoring/workflows/applying.md)
* [Teilnehmen an Workflows](/help/sites-cloud/authoring/workflows/participating.md)
