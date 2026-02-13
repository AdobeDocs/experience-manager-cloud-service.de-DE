---
title: Versionshinweise zur Vorschau des universellen Editors
description: Dies sind die Versionshinweise für die Vorabversion des universellen Editors.
feature: Release Information
role: Admin
exl-id: e8d031aa-4676-4e45-977b-e5dffcc404c4
source-git-commit: 374c8045043f67f06d4ae68aef499bb594f1c08c
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---

# Versionshinweise zur Vorschau des universellen Editors {#preview}

Dies sind die Versionshinweise für die **Vorschauversion** des universellen Editors. Diese Funktionen sind derzeit in der „Vorschau-Umgebung“ **universellen Editors**. Diese Funktionen werden voraussichtlich am 19. Februar 2026 allgemein verfügbar sein.

Diese **Vorschau**-Versionshinweise werden bereitgestellt, damit Sie wissen, welche Änderungen am universellen Editor bevorstehen, und sie testen können, indem Sie [zu Ihrer Vorschauversion wechseln.](/help/sites-cloud/authoring/universal-editor/navigation.md#user-properties)

>[!TIP]
>
>Die **aktuellen Versionshinweise** für den universellen Editor finden Sie im Dokument [Versionshinweise zum universellen Editor.](/help/release-notes/universal-editor/current.md)

>[!NOTE]
>
>Der Inhalt der aktuellen Version sowie das Veröffentlichungsdatum können sich ändern.

## Künftige neue Funktionen {#what-is-new}

* Der RTE wurde verbessert.
   * Das Ausblenden von Symbolleistenelementen im Kontext in RTE wird jetzt unterstützt.
   * Das Umbrechen von Text in Tabellen mit Absätzen wird jetzt unterstützt.
   * Nicht unterstützte RTE-Tags werden jetzt beibehalten.
   * Die RTE-Logik wird jetzt von einer separaten Datei bereitgestellt.
   * Tabellen können jetzt mit dem RTE erstellt und bearbeitet werden.
* Wenn keine Beschriftung festgelegt ist, wird jetzt der Komponententitel aus der Komponentendefinition verwendet.
* `setEditorMode` ist jetzt über Erweiterungen verfügbar.

## Anstehende Verbesserungen {#other-improvements}

* Die Funktion zum Kopieren und Einfügen zwischen Seiten wurde behoben.
* `universal-editor-extensibility` wurde nach `universal-editor` verschoben.
* Die Anzahl der Anfragen an den Extensions-Endpunkt wurde reduziert.
* RemoteApp Unmounts wurden von drei auf eins reduziert.
* RTE-Endpunkte werden jetzt für den Editor für die Bearbeitung im Kontext bereitgestellt.
* Die Bearbeitung verschachtelter Felder führt nicht mehr zum Überschreiben von Peer-Einträgen aus diesen Strukturen.
* Erforderliche RTE-Felder können nicht mehr als leer gespeichert werden.
* Die In-Place-Formatierung wird beim Hinzufügen von Links nach der Formatierung nicht mehr falsch angewendet.
