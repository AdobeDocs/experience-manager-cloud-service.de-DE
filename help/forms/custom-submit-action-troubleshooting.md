---
title: Fehlerbehebung für 502-Fehler in benutzerdefinierter Übermittlungsaktion für adaptive Forms
description: Erfahren Sie, wie Sie 502-Fehlerseiten identifizieren und beheben können, die bei der Verwendung benutzerdefinierter Übermittlungsaktionen in Adaptive Forms (Kernkomponenten) auftreten. In diesem Handbuch werden häufige Ursachen wie nicht behandelte Ausnahmen erläutert und Schritte zur Behebung von Fehlern beschrieben.
feature: Adaptive Forms, Core Components
role: Developer
level: Intermediate
source-git-commit: 03e46bb43e684a6b7057045cf298f40f9f1fe622
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 1%

---


# Fehlerbehebung: 502-Fehlerseite in benutzerdefinierter Übermittlungsaktion

Beim Arbeiten mit adaptiven Forms (Kernkomponenten) kann eine **502-Fehlerseite für HTML auftreten** nachdem Sie ein Formular übermittelt haben, das eine benutzerdefinierte Übermittlungsaktion verwendet.

## Problem

**Fehler:** Eine 502-Fehlerseite HTML wird angezeigt, wenn ein benutzerdefinierter Sendeaktions-Service fehlschlägt.

**Grund:** Dies geschieht, wenn die benutzerdefinierte Übermittlungsaktion einen nicht behandelten Fehler auslöst, z. B. einen Nullzeiger, eine ungültige API-Antwort oder einen Laufzeitfehler.

## Auflösung

Um die 502-Fehlerseite zu verhindern, schließen Sie die Übermittlungslogik in try-catch-Blöcke ein, um Fehler kontrolliert zu behandeln.

Ausführliche Anweisungen finden Sie unter [Erstellen einer benutzerdefinierten Übermittlungsaktion für adaptive Forms (Kernkomponenten)](/help/forms/custom-submit-action-for-adaptive-forms-based-on-core-components.md).
