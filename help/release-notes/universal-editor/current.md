---
title: Universeller Editor – Versionshinweise für 2025.07.09
description: Dies sind die Versionshinweise für die Version 2025.07.09 des universellen Editors.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: 199ee7e11f6706773bd426c3d27236d6ea791a6c
workflow-type: ht
source-wordcount: '368'
ht-degree: 100%

---


# Universeller Editor – Versionshinweise für 2025.07.09 {#release-notes}

Dies sind die Versionshinweise für die Version des universellen Editors vom 9. Juli 2025.

>[!TIP]
>
>Auf [dieser Seite](/help/release-notes/release-notes-cloud/release-notes-current.md) finden Sie die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service.

## Neue Funktionen {#what-is-new}

* [Beim Klicken auf die Symbolleistenschaltfläche **Hinzufügen** in Containern](/help/sites-cloud/authoring/universal-editor/authoring.md#adding-components), bei denen nur ein Komponententyp zulässig ist, wird dieser ohne weitere Auswahl aus dem Dropdown-Menü sofort eingefügt.
* [Die Symbolleistenoption „Authentifizierungs-Header“](/help/sites-cloud/authoring/universal-editor/navigation.md#autentication-settings) befindet sich jetzt hinter einem Funktionsumschalter, da sie in den meisten Fällen nicht nützlich ist.
* [Da im Panel „Eigenschaften“ die Container-Verschachtelung für mehrere Felder nicht zulässig ist](/help/implementing/universal-editor/field-types.md#fields), filtert die Rendering-Routine jetzt verschachtelte Container aus der Feldliste heraus, um ungültige Verschachtelungen zu verhindern.

## Funktionen des Early-Adoption-Programms {#early-adopter}

Wenn Sie diese kommenden Funktionen testen und Ihr Feedback teilen möchten, senden Sie bitte über die mit Ihrer Adobe ID verknüpfte E-Mail-Adresse eine E-Mail an Ihren Adobe-Kontakt für Customer Success.

### Neuer RTE {#new-rte}

Der neue ProseMirror-RTE mit Seitenauswahl im Link-Dialog ist jetzt im rechten Panel verfügbar.

### Rückgängig/Wiederholen {#undo-redo}

Die Funktionen „Rückgängig“ und „Wiederherstellen“ sind jetzt für Autorinnen und Autoren von Inhalten im universellen Editor verfügbar.

* Sie können auf kontextbezogene Bearbeitungen, Bearbeitungen über das Panel „Eigenschaften“ sowie beim Hinzufügen (oder Duplizieren), Verschieben und Löschen von Blöcken angewendet werden.
* Die Funktionen „Rückgängig“ und „Wiederherstellen“ sind auf die aktuelle Browser-Sitzung beschränkt.

## Andere Verbesserungen {#other-improvements}

* Es wurde ein Problem behoben, durch das ein Entfernen einzelner Asset-Verweise bei der Bearbeitung über die Eigenschaftenleiste nicht möglich war.
* Es wurde ein Problem behoben, durch das das Panel „Eigenschaften“ unbegrenzt neu geladen wurde, da Asset-Verweise automatisch in Arrays konvertiert wurden, was zu einem unendlichen Ladestatus führte.
   * Asset-Referenzwerte werden jetzt unverändert gespeichert, ohne dass sie automatisch in Arrays konvertiert werden.
* Es wurde ein Problem behoben, durch das im Panel „Eigenschaften“ keine Felder angezeigt wurden, wenn ein Modell definiert wurde, das keine Inhalte hatte.
   * Dies führte zu einem unendlichen Ladestatus für das Panel „Eigenschaften“ bei leeren Detailantworten, zum Beispiel leeren Inhaltsfragmenten.
* Die ESLint-Konfiguration wurde aus Gründen der Kompatibilität mit Version 9 überarbeitet, einschließlich aktualisierter Regeln und Plug-in-Unterstützung.

## Veraltete Funktionen {#deprecations}

* Die Komponente `text-input` gilt jetzt offiziell als veraltet.
   * Verwenden Sie in `model-definition.json` die Textkomponente, um Texteingaben für das Panel „Eigenschaften“ zu erstellen.
