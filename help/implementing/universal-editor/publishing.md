---
title: Inhaltsveröffentlichung durch den universellen Editor
description: Erfahren Sie, wie der universelle Editor seine Inhalte veröffentlicht, wie sich das Verfahren von dem der Sites-Konsole unterscheidet und was Sie berücksichtigen müssen, wenn Sie eigene Apps entwickeln, die Sie im universellen Editor bearbeiten möchten.
feature: Developing
role: Admin, Developer
exl-id: 60f0bb4a-ee60-4f73-83ae-8568735474ad
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 100%

---

# Inhaltsveröffentlichung durch den universellen Editor {#publishing}

Erfahren Sie, wie der universelle Editor seine Inhalte veröffentlicht, wie sich das Verfahren von dem der Sites-Konsole unterscheidet und was Sie berücksichtigen müssen, wenn Sie eigene Apps entwickeln, die Sie im universellen Editor bearbeiten möchten.

>[!TIP]
>
>Dieser Artikel behandelt Details für Entwicklerinnen und Entwickler zum Veröffentlichungsprozess des universellen Editors. Für Inhaltsautorinnen und -autoren [wird der Prozess der Veröffentlichung von Inhalten hier beschrieben](/help/sites-cloud/authoring/universal-editor/publishing.md).

## Ähnlichkeiten mit dem Prozess der Sites-Konsole {#similarities}

Für Benutzerinnen und Benutzer des [AEM-Seiteneditors](/help/sites-cloud/authoring/page-editor/introduction.md) und der [Sites-Konsole](/help/sites-cloud/authoring/sites-console/introduction.md) funktioniert der Prozess zum Veröffentlichen von Inhalten mit dem universellen Editor wie gewohnt: Bei der Veröffentlichung in AEM wird der Inhalt vom Autoren-Dienst an den Veröffentlichungsdienst (oder den [Vorschaudienst](/help/sites-cloud/authoring/sites-console/previewing-content.md)) repliziert, je nachdem, welche Optionen, die Autorin oder der Autor beim Veröffentlichen auswählt.

## Unterschiede {#differences}

Was die Veröffentlichung mit dem universellen Editor geringfügig unterscheidet, ist nicht so sehr der Editor selbst, sondern vielmehr das externe Hosten der App, was durch den universellen Editor möglich gemacht wird.

Wenn die Web-App extern gehostet wird, muss sichergestellt werden, dass Inhalte vom Autorendienst geladen werden, wenn die App von Autorinnen oder Autoren im Editor geöffnet wird, und dass sie vom Veröffentlichungsdienst geladen werden, wenn Besuchende auf die App zugreifen.

## Erkennen des Dienstes in der App {#detecting}

Um zu ermitteln, ob auf den Autoren- oder Veröffentlichungsdienst zugegriffen werden soll, können Sie durch eine einfache bedingte Anweisung in der App festlegen, dass der entsprechende Autoren- oder Veröffentlichungsendpunkt ausgewählt wird, wenn festgestellt wird, dass der Endpunkt im Editor geöffnet wird.

Eine andere Möglichkeit besteht darin, die App in zwei verschiedenen Umgebungen bereitzustellen, die unterschiedlich konfiguriert sind, sodass eine Umgebung ihren Inhalt vom Autorendienst und die andere Umgebung ihn vom Veröffentlichungsdienst abruft. Damit Autorinnen und Autoren die veröffentlichte URL im universellen Editor öffnen können, kann ein kleines Skript erstellt werden, um die URL auf der Veröffentlichungsseite in die entsprechende URL in der Autorenumgebung zu „konvertieren“ (z. B. durch Voranstellen einer `author`-Sub-Domain), sodass die Autorinnen und Autoren automatisch umgeleitet werden.

## Zusammenfassung {#summary}

Ziel des universellen Editors ist es, kein bestimmtes Muster vorzuschreiben, damit die Implementierung ihre Ziele am besten vollständig entkoppelt erreichen kann und dabei alles für die Implementierung einfach und unkompliziert bleibt.

Gleichermaßen stellt der universelle Editor keine Anforderungen daran, wie ein bestimmtes Projekt die Bestimmung des Dienstes durchführt, von der der Inhalt bereitgestellt werden soll. Stattdessen bietet er verschiedene Möglichkeiten und ermöglicht es dem Projekt, zu bestimmen, welche Lösung für seine eigenen Anforderungen am besten geeignet ist.

## Zusätzliche Ressourcen {#additional-resources}

Weitere Informationen zu den technischen Details zum universellen Editor finden Sie in diesen Entwicklerdokumenten.

* [Einführung in den universellen Editor](/help/implementing/universal-editor/introduction.md) – Erfahren Sie, wie der universelle Editor die Bearbeitung beliebiger Inhalte in jeder Implementierung ermöglicht, um außergewöhnliche Erlebnisse bereitzustellen, die Inhaltsgeschwindigkeit zu erhöhen und ein modernes Entwicklererlebnis zu bieten.
* [Erste Schritte mit dem universellen Editor in AEM](/help/implementing/universal-editor/getting-started.md) – Erfahren Sie, wie Sie Zugriff auf den universellen Editor erhalten und wie Sie mit der Instrumentierung Ihrer ersten AEM-App beginnen, um ihn zu verwenden.
* [Architektur des universellen Editors](/help/implementing/universal-editor/architecture.md) – Erfahren Sie mehr über die Architektur des universellen Editors und darüber, wie Daten zwischen seinen Diensten und Ebenen fließen.
* [Attribute und Typen](/help/implementing/universal-editor/attributes-types.md) – Erfahren Sie mehr über die Datenattribute und -typen, die der universelle Editor erfordert.
* [Authentifizierung beim universellen Editor](/help/implementing/universal-editor/authentication.md) – Erfahren Sie, wie beim universellen Editor authentifiziert wird.
