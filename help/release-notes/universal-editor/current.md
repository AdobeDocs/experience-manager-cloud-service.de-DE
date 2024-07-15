---
title: Universal Editor 2024.06.28 - Versionshinweise
description: Dies sind die Versionshinweise für die Version 2024.06.28 des universellen Editors.
feature: Release Information
role: Admin
source-git-commit: cc94ad2ba42707bb7541217f0225b995f64ad84f
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 1%

---


# Universal Editor 2024.06.28 - Versionshinweise {#release-notes}

Dies sind die Versionshinweise für die Version des universellen Editors vom 28. Juni 2024.

>[!TIP]
>
>Die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service finden Sie auf [dieser Seite.](/help/release-notes/release-notes-cloud/release-notes-current.md)

## Neue Funktionen {#what-is-new}

* **Startseite**: Die letzten Seiten werden als Liste ohne Vorschaubilder angezeigt.
* **Standortleiste**: Es wurde eine erweiterte URL-Validierung hinzugefügt, die HTTPS-URLs erzwingt und Hashes in URLs unterstützt, um Hash-geleitete Anwendungen zu berücksichtigen.
* **Tastaturnavigation**: Die Auswahl der Seitenüberlagerung wurde vom Fokus der Eigenschaftenleiste entkoppelt, um die Tastaturnavigation auf der Seite zu verbessern, ohne den Fokus zu verlieren.
* **Elementbeschriftungen**: Der Fallback-Wert für Beschriftungen verwendet jetzt `data-aue-prop` anstelle von `data-aue-type`, um eine klarere Identifizierung in Überlagerungen und der Inhaltsstruktur zu ermöglichen.
* **RTE Modal**: Beim Öffnen im Eigenschaftenbereich wurde dem Rich-Text-Editor-Modal eine Schaltfläche **Abbrechen** hinzugefügt.
* **UE Service on Node**: Die HTTP-Unterstützung für den universellen Editor-Dienst wurde neu eingeführt, da alle HTTPS-Verbindungen auf Dispatcher-Ebene beendet werden.
* **Interne Kopier-API**: Eine API zum Kopieren von Komponenten zum universellen Editor-Dienst wurde hinzugefügt, sodass in Zukunft Symbolleistenoptionen zum Kopieren und Duplizieren von Inhalten eingeführt werden können.

## Fehlerbehebungen {#bug-fixes}

* **Eigenschaften-Bedienfeld - Breadcrumb**: Das Breadcrumb-Menü im Eigenschaftenbedienfeld für tief verschachtelte Elemente, das nicht geöffnet blieb, wurde behoben.
* **Inhaltsfragmentauswahl**: Die Auswahl für Inhaltsfragmente wurde verbessert, um sicherzustellen, dass die im Inhaltsfragmentmodell oder im `data-aue-filter` definierten Regeln eingehalten werden.
* **Komponenteneinfügung**: Die Liste zum Einfügen neuer Komponenten, die nach dem Navigieren zu einer anderen Seite nicht korrekt aktualisiert wurden, wurde korrigiert.
* **Veröffentlichungsstatus**: Die Handhabung der Veröffentlichungsstatus wurde verbessert, um eine einheitlichere Funktionsweise zu gewährleisten.
* **Verschiedene Fehlerbehebungen**: Diese Version enthält auch verschiedene kleinere Fehlerbehebungen, technische Bereinigungen von Schulden, Sicherheitsverbesserungen und konsolidierte Tests zur Gesamtstabilität und -leistung.
