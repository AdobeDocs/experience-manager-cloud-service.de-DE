---
title: Universeller Editor – Versionshinweise für 2025.09.04
description: Dies sind die Versionshinweise für die Version 2025.09.04 des universellen Editors.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: 0c380e0faca1db0966d22d056dd1f824a731a7bc
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 71%

---


# Universeller Editor – Versionshinweise für 2025.09.04 {#release-notes}

Dies sind die Versionshinweise für die Version vom 4. September 2025 des universellen Editors.

>[!TIP]
>
>Auf [dieser Seite](/help/release-notes/release-notes-cloud/release-notes-current.md) finden Sie die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service.

## Neue Funktionen {#what-is-new}

* Kopieren und Einfügen ist für [Early-Adopters“ verfügbar](#copy-paste)

### Rückgängig/Wiederholen {#undo-redo}

Die Funktionen „Rückgängig“ und „Wiederherstellen“ sind jetzt für Autorinnen und Autoren von Inhalten im universellen Editor verfügbar.

* Sie können auf kontextbezogene Bearbeitungen, Bearbeitungen über das Panel „Eigenschaften“ sowie beim Hinzufügen (oder Duplizieren), Verschieben und Löschen von Blöcken angewendet werden.
* Die Funktionen „Rückgängig“ und „Wiederherstellen“ sind auf die aktuelle Browser-Sitzung beschränkt.

## Funktionen des Early-Adoption-Programms {#early-adopter}

Wenn Sie diese kommenden Funktionen testen und Ihr Feedback teilen möchten, senden Sie bitte über die mit Ihrer Adobe ID verknüpfte E-Mail-Adresse eine E-Mail an Ihren Adobe-Kontakt für Customer Success.

### Neuer RTE {#new-rte}

Der neue ProseMirror-RTE mit Seitenauswahl im Link-Dialog ist jetzt im rechten Panel verfügbar.

### Kopieren/Einfügen {#copy-paste}

Das Kopieren und Einfügen von Komponenten innerhalb derselben Seite ist jetzt für Inhaltsautoren verfügbar.

## Andere Verbesserungen {#other-improvements}

* Der Stil der Editor-Symbolleiste wurde aktualisiert, um ihn besser an den bevorstehenden neuen RTE anzupassen.
* Die Filter im Dialogfeld für die Asset-Auswahl wurden wiederhergestellt.

## Veraltete Funktionen {#deprecations}

* Die Komponenten `text-input` und `text-area` sind seit [Version 2025.07.09.](/help/release-notes/universal-editor/2025/2025-07-09.md) offiziell veraltet
   * Verwenden Sie in `model-definition.json` die Textkomponente, um Texteingaben für das Panel „Eigenschaften“ zu erstellen.
