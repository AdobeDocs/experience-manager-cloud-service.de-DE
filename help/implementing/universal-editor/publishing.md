---
title: Veröffentlichen von Inhalten mit dem universellen Visual Editor
description: Erfahren Sie, wie der universelle Visual Editor Inhalte veröffentlicht und wie Ihre Apps mit den veröffentlichten Inhalten umgehen können.
exl-id: aee34469-37c2-4571-806b-06c439a7524a
source-git-commit: 9cff6e94b38016f008fd8177be2e071a530d80b6
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# Veröffentlichen von Inhalten mit dem universellen Visual Editor {#publishing}

Erfahren Sie, wie der universelle Visual Editor Inhalte veröffentlicht und wie Ihre Apps mit den veröffentlichten Inhalten umgehen können.

## Ähnlichkeiten mit AEM {#similarities}

Für Benutzer von AEM funktioniert der Prozess zum Veröffentlichen von Inhalten mit dem universellen Visual Editor wie gewohnt: Bei der Veröffentlichung in AEM wird der Inhalt von der Autorenstufe auf die Veröffentlichungsstufe repliziert.

## Unterschiede {#differences}

Was die Veröffentlichung mit dem universellen Visual Editor etwas anders macht, ist nicht so sehr der Editor selbst, sondern vielmehr das externe Hosting der App, das der universelle Editor ermöglicht.

Wenn die Web-App extern gehostet wird, muss sichergestellt werden, dass Inhalte von der Autorenstufe geladen werden, wenn die App von Autoren im Editor geöffnet wird, und von der Veröffentlichungsstufe geladen werden, wenn Besucher auf die App zugreifen.

## Erkennen der Ebene in der App {#detecting}

Um zu bestimmen, ob die Autoren- oder Veröffentlichungsstufe auf zugreifen soll, können Sie durch eine einfache bedingte Anweisung in der App festlegen, dass der entsprechende Autoren- oder Veröffentlichungsendpunkt ausgewählt wird, wenn festgestellt wird, dass der Endpunkt im Editor geöffnet ist.

Eine andere Möglichkeit besteht darin, die App in zwei verschiedenen Umgebungen bereitzustellen, die unterschiedlich konfiguriert sind, sodass eine Umgebung ihren Inhalt aus der Autorenstufe abruft und eine Umgebung, die sie aus der Veröffentlichungsstufe abruft. Damit Autoren die veröffentlichte URL im universellen Editor öffnen können, kann ein kleines Skript erstellt werden, um die URL auf der Veröffentlichungsseite in die entsprechende URL in der Autorenumgebung zu &quot;konvertieren&quot;(z. B. durch Voranstellen einer `author` Subdomäne), sodass die Autoren automatisch umgeleitet werden.

## Zusammenfassung {#summary}

Ziel des universellen Editors ist es, kein bestimmtes Muster vorzuschreiben, damit die Implementierung ihre Ziele am besten vollständig entkoppelt erreichen kann und dabei alles für die Implementierung einfach und unkompliziert bleibt.

Gleichermaßen stellt der universelle Editor keine Anforderungen daran, wie ein bestimmtes Projekt die Bestimmung der Ebene durchführt, von der der Inhalt bereitgestellt werden soll. Stattdessen bietet es eine Reihe von Möglichkeiten und ermöglicht es dem Projekt zu bestimmen, welche Lösung für seine eigenen Anforderungen am besten geeignet ist.
