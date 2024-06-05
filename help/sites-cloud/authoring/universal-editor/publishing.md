---
title: Veröffentlichen von Inhalten mit dem universellen Editor
description: Erfahren Sie, wie Inhalte mit dem universellen Editor veröffentlicht werden und wie Ihre Apps mit den veröffentlichten Inhalten umgehen können.
exl-id: aee34469-37c2-4571-806b-06c439a7524a
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 100%

---


# Veröffentlichen von Inhalten mit dem universellen Editor {#publishing}

Erfahren Sie, wie Inhalte mit dem universellen Editor veröffentlicht werden und wie Ihre Apps mit den veröffentlichten Inhalten umgehen können.

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

## Zusätzliche Ressourcen {#additional-resources}

Informationen zum Erstellen von Inhalten mit dem universellen Editor finden Sie in diesem Dokument.

* [Inhaltserstellung mit dem universellen Editor](authoring.md) – Erfahren Sie, wie einfach und intuitiv es für Inhaltsautorinnen und Inhaltsautoren ist, Inhalte mit dem universellen Editor zu erstellen.

Weitere Informationen zu den technischen Details zum universellen Editor finden Sie in diesen Entwicklerdokumenten.

* [Einführung in den universellen Editor](/help/implementing/universal-editor/introduction.md) – Erfahren Sie, wie der universelle Editor die Bearbeitung beliebiger Inhalte in jeder Implementierung ermöglicht, um außergewöhnliche Erlebnisse bereitzustellen, die Inhaltsgeschwindigkeit zu erhöhen und ein modernes Entwicklererlebnis zu bieten.
* [Erste Schritte mit dem universellen Editor in AEM](/help/implementing/universal-editor/getting-started.md) – Erfahren Sie, wie Sie Zugriff auf den universellen Editor erhalten und wie Sie mit der Instrumentierung Ihrer ersten AEM-App beginnen, um ihn zu verwenden.
* [Architektur des universellen Editors](/help/implementing/universal-editor/architecture.md) – Erfahren Sie mehr über die Architektur des universellen Editors und darüber, wie Daten zwischen seinen Diensten und Ebenen fließen.
* [Attribute und Typen](/help/implementing/universal-editor/attributes-types.md) – Erfahren Sie mehr über die Datenattribute und -typen, die der universelle Editor erfordert.
* [Authentifizierung beim universellen Editor](/help/implementing/universal-editor/authentication.md) – Erfahren Sie, wie beim universellen Editor authentifiziert wird.
