---
title: Universeller Editor – Versionshinweise für 2026.03.19
description: Dies sind die Versionshinweise für die Version 2026.03.19 des universellen Editors.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: 8d9d162ec5bba99afb1ae86252a49a9880be4e68
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 34%

---


# Universeller Editor – Versionshinweise für 2026.03.19 {#release-notes}

Dies sind die Versionshinweise für die Version vom 19. März 2026 des universellen Editors.

>[!TIP]
>
>Informationen zum Testen von **zukünftigen** Funktionen des universellen Editors vor ihrer Veröffentlichung finden Sie in den [Vorschauversionshinweisen zum universellen Editor](/help/release-notes/universal-editor/preview.md).

>[!TIP]
>
>Auf [dieser Seite](/help/release-notes/release-notes-cloud/release-notes-current.md) finden Sie die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service.

## Neue Funktionen {#what-is-new}

* Die Elemente in den Eigenschaften werden jetzt ausgeblendet, wenn Sie zurück zum [Startbildschirm“ navigieren](/help/sites-cloud/authoring/universal-editor/navigation.md#home-button)
* [Der Asset-Selektor](/help/implementing/universal-editor/configure-assets-selector.md) unterstützt jetzt [Filterdefinitionen.](/help/implementing/universal-editor/filtering.md)
* Wenn für das ausgewählte Element keine Aktionen verfügbar sind, wird [Kontextmenü](/help/sites-cloud/authoring/universal-editor/authoring.md#context-menu) kein Pfeil mehr für den Zugriff auf Aktionen angezeigt.

## Andere Verbesserungen {#other-improvements}

* Wenn eine Modell-/Filter-/Komponentendefinition vorhanden ist, wird sie beim Wechsel von einer App zu einer anderen im Editor erneut abgerufen.
* Wenn Sie ein Bild entfernen, bleiben keine Bild-Tags mehr leer, wenn Sie DAM als Backend verwenden.
* Klassen in Blöcken werden jetzt bei Verwendung von DA als Backend ordnungsgemäß verarbeitet.
* Die Open API speichert jetzt Remote-Assets ordnungsgemäß als -Objekte.

## grundlegende Veränderung {#breaking-change}

* Alle Erweiterungen sollten auf `@adobe/uix-guest` >= `1.1.7` aktualisiert werden, um die Stabilität zu verbessern.
