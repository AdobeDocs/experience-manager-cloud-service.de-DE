---
title: Wie der universelle Editor Inhalte veröffentlicht
description: Erfahren Sie, wie der universelle Editor seine Inhalte veröffentlicht, wie er sich vom Prozess in der Sites-Konsole unterscheidet und Überlegungen bei der Entwicklung eigener Apps, mit denen er arbeiten kann.
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 0ee6689460ac0ecc5c025fb6a940d69a16699c85
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 45%

---


# Wie der universelle Editor Inhalte veröffentlicht {#publishing}

Erfahren Sie, wie der universelle Editor seine Inhalte veröffentlicht, wie er sich vom Prozess in der Sites-Konsole unterscheidet und Überlegungen bei der Entwicklung eigener Apps, mit denen er arbeiten kann.

>[!TIP]
>
>Dieser Artikel behandelt Details zum Veröffentlichungsprozess des universellen Editors für Entwickler. Für Inhaltsautorinnen und -autoren [der Prozess der Veröffentlichung Ihrer Inhalte wird hier beschrieben.](/help/sites-cloud/authoring/universal-editor/publishing.md)

## Ähnlichkeiten mit dem Prozess der Sites-Konsole {#similarities}

Für Benutzer des [AEM-Seiteneditors](/help/sites-cloud/authoring/page-editor/introduction.md) und der [Sites-Konsole funktioniert ](/help/sites-cloud/authoring/sites-console/introduction.md) Prozess zum Veröffentlichen von Inhalten mit dem universellen Editor wie gewohnt: Bei der Veröffentlichung in AEM wird der Inhalt vom Autoren-Service zum Veröffentlichungs-Service (oder [zum Vorschau-Service) repliziert, ](/help/sites-cloud/authoring/sites-console/previewing-content.md) verfügbar und abhängig von den Optionen, die der Autor beim Veröffentlichen auswählt.

## Unterschiede {#differences}

Was die Veröffentlichung mit dem universellen Editor geringfügig unterscheidet, ist nicht so sehr der Editor selbst, sondern vielmehr das externe Hosten der App, was durch den universellen Editor möglich gemacht wird.

Wenn die Web-App extern gehostet wird, muss sichergestellt werden, dass Inhalte vom Autoren-Service geladen werden, wenn die App von Autoren im Editor geöffnet wird, und dass sie vom Veröffentlichungs-Service geladen werden, wenn Besuchende auf die App zugreifen.

## Erkennen des Service in der App {#detecting}

Um zu bestimmen, ob auf den Autoren- oder Veröffentlichungs-Service zugegriffen werden soll, können Sie durch eine einfache bedingte Anweisung in der App festlegen, dass der entsprechende Autoren- oder Veröffentlichungs-Endpunkt ausgewählt wird, wenn festgestellt wird, dass er im Editor geöffnet wird.

Eine weitere Option besteht darin, die App in zwei verschiedenen Umgebungen bereitzustellen, die unterschiedlich konfiguriert sind, sodass eine Umgebung ihren Inhalt vom Autoren-Service und die andere Umgebung ihn vom Veröffentlichungs-Service abruft. Damit Autorinnen und Autoren die veröffentlichte URL im universellen Editor öffnen können, kann ein kleines Skript erstellt werden, um die URL auf der Veröffentlichungsseite in die entsprechende URL in der Autorenumgebung zu „konvertieren“ (z. B. durch Voranstellen einer `author`-Sub-Domain), sodass die Autorinnen und Autoren automatisch umgeleitet werden.

## Zusammenfassung {#summary}

Ziel des universellen Editors ist es, kein bestimmtes Muster vorzuschreiben, damit die Implementierung ihre Ziele am besten vollständig entkoppelt erreichen kann und dabei alles für die Implementierung einfach und unkompliziert bleibt.

Ebenso stellt der universelle Editor keine Anforderungen daran, wie ein bestimmtes Projekt die Bestimmung durchführt, von welchem Service die Inhalte bereitgestellt werden sollen. Stattdessen bietet er verschiedene Möglichkeiten und ermöglicht es dem Projekt, zu bestimmen, welche Lösung für seine eigenen Anforderungen am besten geeignet ist.

## Zusätzliche Ressourcen {#additional-resources}

Weitere Informationen zu den technischen Details zum universellen Editor finden Sie in diesen Entwicklerdokumenten.

* [Einführung in den universellen Editor](/help/implementing/universal-editor/introduction.md) – Erfahren Sie, wie der universelle Editor die Bearbeitung beliebiger Inhalte in jeder Implementierung ermöglicht, um außergewöhnliche Erlebnisse bereitzustellen, die Inhaltsgeschwindigkeit zu erhöhen und ein modernes Entwicklererlebnis zu bieten.
* [Erste Schritte mit dem universellen Editor in AEM](/help/implementing/universal-editor/getting-started.md) – Erfahren Sie, wie Sie Zugriff auf den universellen Editor erhalten und wie Sie mit der Instrumentierung Ihrer ersten AEM-App beginnen, um ihn zu verwenden.
* [Architektur des universellen Editors](/help/implementing/universal-editor/architecture.md) – Erfahren Sie mehr über die Architektur des universellen Editors und darüber, wie Daten zwischen seinen Diensten und Ebenen fließen.
* [Attribute und Typen](/help/implementing/universal-editor/attributes-types.md) – Erfahren Sie mehr über die Datenattribute und -typen, die der universelle Editor erfordert.
* [Authentifizierung beim universellen Editor](/help/implementing/universal-editor/authentication.md) – Erfahren Sie, wie beim universellen Editor authentifiziert wird.
