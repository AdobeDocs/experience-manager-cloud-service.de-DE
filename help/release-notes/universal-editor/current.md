---
title: Universeller Editor – Versionshinweise für 2025.07.09
description: Dies sind die Versionshinweise für die Version 2025.07.09 des universellen Editors.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: 199ee7e11f6706773bd426c3d27236d6ea791a6c
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 25%

---


# Universeller Editor – Versionshinweise für 2025.07.09 {#release-notes}

Dies sind die Versionshinweise für die Version vom 9. Juli 2025 des universellen Editors.

>[!TIP]
>
>Auf [dieser Seite](/help/release-notes/release-notes-cloud/release-notes-current.md) finden Sie die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service.

## Neue Funktionen {#what-is-new}

* [Wenn auf die Schaltfläche **Hinzufügen** in Containern geklickt wird, ](/help/sites-cloud/authoring/universal-editor/authoring.md#adding-components) nur ein Komponententyp zulässig ist, wird er sofort eingefügt, ohne dass eine Auswahl aus dem Dropdown-Menü erforderlich ist.
* [Die Option „Authentifizierungs-Kopfzeilen](/help/sites-cloud/authoring/universal-editor/navigation.md#autentication-settings) wurde hinter einem Feature-Umschalter platziert, da sie in den meisten Fällen nicht nützlich ist.
* [Da die Container-Verschachtelung für mehrere Felder im Eigenschaftenbereich nicht zulässig ist, filtert ](/help/implementing/universal-editor/field-types.md#fields) Rendering-Routine jetzt verschachtelte Container aus der Feldliste heraus, um eine ungültige Verschachtelung zu verhindern.

## Funktionen des Early-Adoption-Programms {#early-adopter}

Wenn Sie diese kommenden Funktionen testen und Ihr Feedback geben möchten, senden Sie eine E-Mail an Ihren Adobe Customer Success Manager über die mit Ihrer Adobe ID verknüpfte E-Mail-Adresse.

### Neuer RTE {#new-rte}

Der neue ProseMirror RTE mit Seitenauswahl im Link-Dialog ist jetzt im rechten Panel verfügbar.

### Rückgängig/Wiederholen {#undo-redo}

Die Funktionen „Rückgängig“ und „Wiederherstellen“ sind jetzt für Autorinnen und Autoren von Inhalten im universellen Editor verfügbar.

* Sie können auf kontextbezogene Bearbeitungen, Bearbeitungen über das Panel „Eigenschaften“ sowie beim Hinzufügen (oder Duplizieren), Verschieben und Löschen von Blöcken angewendet werden.
* Die Funktionen „Rückgängig“ und „Wiederherstellen“ sind auf die aktuelle Browser-Sitzung beschränkt.

## Andere Verbesserungen {#other-improvements}

* Es wurde ein Problem behoben, bei dem das Entfernen einzelner Asset-Verweise bei der Bearbeitung über die Eigenschaftenleiste nicht möglich war.
* Es wurde ein Problem behoben, bei dem das Bedienfeld Eigenschaften unbegrenzt geladen wurde, da Asset-Verweise automatisch in Arrays konvertiert wurden, was zu einem unendlichen Ladestatus führte.
   * Asset-Referenzwerte werden jetzt unverändert gespeichert, ohne dass sie automatisch in Arrays konvertiert werden.
* Es wurde ein Problem behoben, bei dem im Bedienfeld Eigenschaften beim Definieren eines Modells keine Felder angezeigt wurden, die jedoch keinen Inhalt enthielten.
   * Dies führte zu einem unendlichen Ladestatus für den Bereich „Eigenschaften“ für leere Detailantworten, wie leere Inhaltsfragmente.
* Die ESLint-Konfiguration wurde aus Gründen der Kompatibilität mit Version 9 überarbeitet, einschließlich aktualisierter Regeln und Plug-in-Unterstützung.

## Veraltete Funktionen {#deprecations}

* Die `text-input` Komponente ist jetzt offiziell veraltet.
   * Verwenden Sie in `model-definition.json` die Textkomponente , um Texteingaben für das Bedienfeld Eigenschaften zu erstellen.
