---
title: Veröffentlichen von Inhalten mit dem universellen Editor
description: Erfahren Sie, wie Inhalte mit dem universellen Editor veröffentlicht werden und wie Ihre Apps mit den veröffentlichten Inhalten umgehen können.
exl-id: aee34469-37c2-4571-806b-06c439a7524a
source-git-commit: 0ad9f349c997c35862e4f571b4741ed4c0c947e2
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 100%

---


# Veröffentlichen von Inhalten mit dem universellen Editor {#publishing}

Erfahren Sie, wie Inhalte mit dem universellen Editor veröffentlicht werden und wie Ihre Apps mit den veröffentlichten Inhalten umgehen können.

{{universal-editor-status}}

## Ähnlichkeiten mit AEM {#similarities}

Für AEM-Benutzende funktioniert der Prozess zum Veröffentlichen von Inhalten mit dem universellen Editor wie gewohnt: Bei der Veröffentlichung in AEM wird der Inhalt von der Autorenebene in die Veröffentlichungsebene repliziert.

## Unterschiede {#differences}

Was die Veröffentlichung mit dem universellen Editor geringfügig unterscheidet, ist nicht so sehr der Editor selbst, sondern vielmehr das externe Hosten der App, was durch den universellen Editor möglich gemacht wird.

Wenn die Web-App extern gehostet wird, muss sichergestellt werden, dass Inhalte von der Autorenebene geladen werden, wenn die App von Autorinnen oder Autoren im Editor geöffnet wird, und dass sie von der Veröffentlichungsebene geladen werden, wenn Besuchende auf die App zugreifen.

## Erkennen der Ebene in der App {#detecting}

Um zu bestimmen, ob auf die Autoren- oder Veröffentlichungsebene zugegriffen werden soll, können Sie durch eine einfache bedingte Anweisung in der App festlegen, dass der entsprechende Autoren- oder Veröffentlichungsendpunkt ausgewählt wird, wenn festgestellt wird, dass der Endpunkt im Editor geöffnet wird.

Eine andere Möglichkeit besteht darin, die App in zwei verschiedenen Umgebungen bereitzustellen, die unterschiedlich konfiguriert sind, sodass eine Umgebung ihren Inhalt von der Autorenebene und die andere Umgebung ihn von der Veröffentlichungsebene abruft. Damit Autorinnen und Autoren die veröffentlichte URL im universellen Editor öffnen können, kann ein kleines Skript erstellt werden, um die URL auf der Veröffentlichungsseite in die entsprechende URL in der Autorenumgebung zu „konvertieren“ (z. B. durch Voranstellen einer `author`-Sub-Domain), sodass die Autorinnen und Autoren automatisch umgeleitet werden.

## Zusammenfassung {#summary}

Ziel des universellen Editors ist es, kein bestimmtes Muster vorzuschreiben, damit die Implementierung ihre Ziele am besten vollständig entkoppelt erreichen kann und dabei alles für die Implementierung einfach und unkompliziert bleibt.

Gleichermaßen stellt der universelle Editor keine Anforderungen daran, wie ein bestimmtes Projekt die Bestimmung der Ebene durchführt, von der der Inhalt bereitgestellt werden soll. Stattdessen bietet er verschiedene Möglichkeiten und ermöglicht es dem Projekt, zu bestimmen, welche Lösung für seine eigenen Anforderungen am besten geeignet ist.
