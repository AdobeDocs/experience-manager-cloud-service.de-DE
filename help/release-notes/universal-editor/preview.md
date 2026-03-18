---
title: Versionshinweise zur Vorschau des universellen Editors
description: Dies sind die Versionshinweise für die Vorabversion des universellen Editors.
feature: Release Information
role: Admin
exl-id: e8d031aa-4676-4e45-977b-e5dffcc404c4
source-git-commit: bbf371dbf8102611345f2d289a3eaba56ee1d87c
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---


# Versionshinweise zur Vorschau des universellen Editors {#preview}

Dies sind die Versionshinweise für die **Vorschauversion** des universellen Editors. Diese Funktionen sind derzeit in der „Vorschau-Umgebung“ **universellen Editors**. Diese Funktionen werden voraussichtlich am 12. März 2026 allgemein verfügbar sein.

Diese **Vorschau**-Versionshinweise werden bereitgestellt, damit Sie wissen, welche Änderungen am universellen Editor bevorstehen, und sie testen können, indem Sie [zu Ihrer Vorschauversion wechseln.](/help/sites-cloud/authoring/universal-editor/navigation.md#user-properties)

>[!TIP]
>
>Die **aktuellen Versionshinweise** für den universellen Editor finden Sie im Dokument [Versionshinweise zum universellen Editor.](/help/release-notes/universal-editor/current.md)

>[!NOTE]
>
>Der Inhalt der aktuellen Version sowie das Veröffentlichungsdatum können sich ändern.

## Künftige Funktionen {#upcoming-features}

* Die Elemente in der rechten Leiste können jetzt auf dem Startbildschirm reduziert werden.
* Der Asset-Selektor unterstützt jetzt Filterdefinitionen.
* Wenn für das ausgewählte Element keine Aktionen verfügbar sind, wird im Kontextmenü kein Pfeil mehr für den Zugriff auf Aktionen angezeigt.

## Anstehende Verbesserungen {#upcoming-improvements}

* Wenn eine Modell-/Filter-/Komponentendefinition vorhanden ist, wird sie beim Wechsel von einer App zu einer anderen im Editor erneut abgerufen.
* Wenn Sie ein Bild entfernen, bleiben keine Bild-Tags mehr leer, wenn Sie DAM als Backend verwenden.
* Klassen in Blöcken werden jetzt bei Verwendung von DA als Backend ordnungsgemäß verarbeitet.
* Die Open API speichert jetzt Remote-Assets ordnungsgemäß als -Objekte.

## Bevorstehende grundlegende Änderung {#breaking-change}

* Alle Erweiterungen sollten auf `@adobe/uix-guest` >= `1.1.7` aktualisiert werden, um die Stabilität zu verbessern.
