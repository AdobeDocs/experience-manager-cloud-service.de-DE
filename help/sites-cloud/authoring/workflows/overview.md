---
title: Arbeiten mit Workflows
description: Workflows in AEM ermöglichen es Ihnen, eine Reihe von Schritten zu automatisieren, die auf einer Seite oder bei einem Asset durchgeführt werden.
exl-id: ed157646-abb3-45c6-bafd-7889bd93fdf3
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 100%

---

# Arbeiten mit Workflows {#working-with-workflows}

AEM-Workflows ermöglichen es Ihnen, eine Reihe von Schritten zu automatisieren, die an Seiten und/oder Assets ausgeführt werden.

Beispielsweise muss beim Veröffentlichen ein Editor den Inhalt überprüfen, bevor ein Site-Administrator die Seite aktiviert. Ein Workflow, der dieses Beispiel automatisiert, benachrichtigt jeden Teilnehmer, wenn es Zeit ist, die erforderlichen Arbeiten auszuführen:

1. Der Autor wendet den Workflow auf der Seite an.
1. Der Editor erhält ein Arbeitselement, das angibt, dass er den Seiteninhalt überprüfen muss. Wenn er fertig ist, wird angegeben, dass sein Arbeitselement abgeschlossen ist.
1. Der Site-Administrator erhält dann ein Arbeitselement, das die Aktivierung der Seite anfordert. Wenn er fertig ist, wird angegeben, dass sein Arbeitselement abgeschlossen ist.

In der Regel gilt:

* Inhaltsautoren wenden Workflows auf Seiten an und nehmen an Workflows teil.
* Die Workflows, die Sie verwenden, sind für die Geschäftsprozesse Ihres Unternehmens spezifisch.

Die folgenden Seiten behandeln:

* [Anwenden von Workflows auf Seiten](/help/sites-cloud/authoring/workflows/applying.md)
* [Teilnehmen an Workflows](/help/sites-cloud/authoring/workflows/participating.md)
