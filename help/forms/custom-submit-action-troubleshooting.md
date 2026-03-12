---
title: Fehlerbehebung für 502-Fehler in benutzerdefinierter Übermittlungsaktion für adaptive Forms
description: Erfahren Sie, wie Sie 502-Fehlerseiten identifizieren und beheben können, die bei der Verwendung benutzerdefinierter Übermittlungsaktionen in Adaptive Forms (Kernkomponenten) auftreten. In diesem Handbuch werden häufige Ursachen wie nicht behandelte Ausnahmen erläutert und Schritte zur Behebung von Fehlern beschrieben.
feature: Adaptive Forms, Core Components
role: Developer
level: Intermediate
badgeSaas: label="AEM Forms" type="Positive" tooltip="Gilt für AEM Forms)."
exl-id: a7469926-7059-4aca-90ff-2554d14c3944
source-git-commit: 89b0f2a8ca9d2f60365a5c3962b0b4e826f79b3e
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 2%

---

# Fehlerbehebung: 502-Fehlerseite in benutzerdefinierter Übermittlungsaktion

Beim Arbeiten mit adaptiven Forms (Kernkomponenten) kann eine **502-Fehlerseite für HTML auftreten** nachdem Sie ein Formular übermittelt haben, das eine benutzerdefinierte Übermittlungsaktion verwendet.

## Problem

**Fehler:** Eine 502-Fehlerseite HTML wird angezeigt, wenn ein benutzerdefinierter Sendeaktions-Service fehlschlägt.

**Grund:** Dies geschieht, wenn die benutzerdefinierte Übermittlungsaktion einen nicht behandelten Fehler auslöst, z. B. einen Nullzeiger, eine ungültige API-Antwort oder einen Laufzeitfehler.

## Auflösung

Um die 502-Fehlerseite zu verhindern, schließen Sie die Übermittlungslogik in try-catch-Blöcke ein, um Fehler kontrolliert zu behandeln.

Ausführliche Anweisungen finden Sie unter [Erstellen einer benutzerdefinierten Übermittlungsaktion für adaptive Forms (Kernkomponenten)](/help/forms/custom-submit-action-for-adaptive-forms-based-on-core-components.md).
