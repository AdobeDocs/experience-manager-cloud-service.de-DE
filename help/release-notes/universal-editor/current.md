---
title: Universeller Editor – Versionshinweise für 2025.07.31
description: Dies sind die Versionshinweise für die Version 2025.07.31 des universellen Editors.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: 91799e32f363aca268a89a7eebcb5001c5295cc5
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 56%

---


# Universeller Editor – Versionshinweise für 2025.07.31 {#release-notes}

Dies sind die Versionshinweise für die Version vom 31. Juli 2025 des universellen Editors.

>[!TIP]
>
>Auf [dieser Seite](/help/release-notes/release-notes-cloud/release-notes-current.md) finden Sie die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service.

## Neue Funktionen {#what-is-new}

* [Die Option für die Authentifizierungs-Kopfzeilen-](/help/sites-cloud/authoring/universal-editor/navigation.md#autentication-settings) befindet sich hinter einem Funktions-Umschalter, wie in [Version 2025.07.09.](/help/release-notes/universal-editor/2025/2025-07-09.md) eingeführt
   * Sie ist jetzt jedoch standardmäßig aktiviert.
* Neue Funktionen für [RTE-Early-Adopters](#new-rte)
   * Unterstützung für den Dunkelmodus wurde hinzugefügt.
   * Unterstützung für Textausrichtung wurde hinzugefügt.
      * Standardmäßig deaktiviert und nur für Headless-Projekte verfügbar
   * Unterstützung für Einzüge wurde hinzugefügt.
      * Standardmäßig deaktiviert und nur für Headless-Projekte verfügbar
   * Umbrüche (`<br>`) werden jetzt bei gedrückter Umschalt- und Eingabetaste eingefügt.

## Funktionen des Early-Adoption-Programms {#early-adopter}

Wenn Sie diese kommenden Funktionen testen und Ihr Feedback teilen möchten, senden Sie bitte über die mit Ihrer Adobe ID verknüpfte E-Mail-Adresse eine E-Mail an Ihren Adobe-Kontakt für Customer Success.

### Neuer RTE {#new-rte}

Der neue ProseMirror-RTE mit Seitenauswahl im Link-Dialog ist jetzt im rechten Panel verfügbar.

### Rückgängig/Wiederholen {#undo-redo}

Die Funktionen „Rückgängig“ und „Wiederherstellen“ sind jetzt für Autorinnen und Autoren von Inhalten im universellen Editor verfügbar.

* Sie können auf kontextbezogene Bearbeitungen, Bearbeitungen über das Panel „Eigenschaften“ sowie beim Hinzufügen (oder Duplizieren), Verschieben und Löschen von Blöcken angewendet werden.
* Die Funktionen „Rückgängig“ und „Wiederherstellen“ sind auf die aktuelle Browser-Sitzung beschränkt.

## Andere Verbesserungen {#other-improvements}

* Fehlerbehebungen für den RTE für frühzeitige Benutzende
   * Durch Drücken der Eingabetaste wird jetzt ein neues Listenelement (`<li>`) innerhalb einer Liste erstellt.
* Videos werden jetzt bei Verwendung des Remote-DAM ordnungsgemäß aktualisiert.
* Service-Unterstützung für 6.5 LTS hinzugefügt.

## Veraltete Funktionen {#deprecations}

* Die `text-input`- und `text-area`-Komponenten sind seit [Version 2025.07.09.](/help/release-notes/universal-editor/2025/2025-07-09.md) offiziell veraltet
   * Verwenden Sie in `model-definition.json` die Textkomponente, um Texteingaben für das Panel „Eigenschaften“ zu erstellen.
