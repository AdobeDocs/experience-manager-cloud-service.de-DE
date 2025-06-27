---
title: Universeller Editor – Versionshinweise für 2025.06.19
description: Dies sind die Versionshinweise für die Version 2025.06.19 des universellen Editors.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: 5ffae9e548ca952975b3ea805808e227102ec99f
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 26%

---


# Universeller Editor – Versionshinweise für 2025.06.19 {#release-notes}

Dies sind die Versionshinweise für die Version vom 19. Juni 2025 des universellen Editors.

>[!TIP]
>
>Auf [dieser Seite](/help/release-notes/release-notes-cloud/release-notes-current.md) finden Sie die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service.

## Neue Funktionen {#what-is-new}

* **Unterstützung für Mehrfachfelder in der Eigenschaftenleiste** -
  [Die Container-Komponente](/help/implementing/universal-editor/field-types.md#container) kann jetzt zum Erstellen von Eigenschaften für mehrere Felder verwendet werden.
* **Unterstützung für verschachtelte Eigenschaften** - Das [`name`-Feld ](/help/implementing/universal-editor/field-types.md#nesting) jetzt Pfade, um die Eigenschaftsverschachtelung zu aktivieren.
* **Größenänderbarer rechter Bereich** - Die Größe des Seitenbereichs kann jetzt geändert werden, um die im Seitenbereich angezeigten längeren Inhalte besser zu berücksichtigen.

## Early Adoption Features {#early-adopter}

Um einige neue Funktionen testen zu können, nehmen Sie am Early-Adopter-Programm von Adobe teil.

### **Rückgängig/Wiederholen** {#undo-redo}

„Rückgängig machen“ und „Wiederherstellen“ sind jetzt für Autoren von Inhalten im universellen Editor verfügbar.

* Dazu gehören kontextbezogene Bearbeitungen, Bearbeitungen über das Bedienfeld Eigenschaften sowie das Hinzufügen (oder Duplizieren), Verschieben und Löschen von Blöcken.
* Rückgängig machen und Wiederholen ist auf die aktuelle Browser-Sitzung beschränkt.

Wenn Sie diese neue Funktion testen und Ihr Feedback teilen möchten, senden Sie bitte über die mit Ihrer Adobe ID verknüpfte E-Mail-Adresse eine E-Mail an Ihren Adobe-Kontakt für Customer Success.

## Andere Verbesserungen {#other-improvements}

* Kollisionsfehler beim Verschieben von Blöcken zwischen Containern wurden behoben.
* Es wurde ein Problem behoben, durch das das Duplizieren des letzten Blocks eines Containers fehlschlug.
* In der Dropdown-Liste Aktion hinzufügen werden jetzt nur noch Komponenten aufgeführt, für die in der `component-definition.json`-Datei ein geeignetes Plug-in definiert ist.
* Das vom Dialogfeld „Veröffentlichen“ verwendete Änderungsdatum wurde korrigiert, bei dem Seiten unter bestimmten Umständen nicht als geändert erkannt und nicht erneut veröffentlicht wurden.
* Fehlerkorrektur - Das MSM-Vererbungsverhalten, bei dem durch Bearbeiten eines Containers die Vererbung für untergeordnete Knoten abgebrochen wurde, wurde korrigiert.
* `fetchUrl` wurde behoben, wodurch bewegte Blöcke von einem Container in einen anderen wiederhergestellt wurden.
