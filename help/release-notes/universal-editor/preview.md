---
title: Versionshinweise zur Vorschau des universellen Editors
description: Dies sind die Versionshinweise für die Vorabversion des universellen Editors.
feature: Release Information
role: Admin
exl-id: e8d031aa-4676-4e45-977b-e5dffcc404c4
source-git-commit: 39137052e9fa409f7f5494be53fa7693aaa60b17
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---

# Versionshinweise zur Vorschau des universellen Editors {#preview}

Dies sind die Versionshinweise für die **Vorschauversion** des universellen Editors. Diese Funktionen sind derzeit in der „Vorschau-Umgebung“ **universellen Editors**. Diese Funktionen werden voraussichtlich am 26. Februar 2026 allgemein verfügbar sein.

Diese **Vorschau**-Versionshinweise werden bereitgestellt, damit Sie wissen, welche Änderungen am universellen Editor bevorstehen, und sie testen können, indem Sie [zu Ihrer Vorschauversion wechseln.](/help/sites-cloud/authoring/universal-editor/navigation.md#user-properties)

>[!TIP]
>
>Die **aktuellen Versionshinweise** für den universellen Editor finden Sie im Dokument [Versionshinweise zum universellen Editor.](/help/release-notes/universal-editor/current.md)

>[!NOTE]
>
>Der Inhalt der aktuellen Version sowie das Veröffentlichungsdatum können sich ändern.

## Anstehende Verbesserungen {#other-improvements}

* Der Editor setzt den Inhalt nicht mehr standardmäßig auf `{}`, bevor der Inhalt eintrifft, wodurch in bestimmten Situationen ein Datenverlust verhindert wird.
* Änderungen gehen beim Bearbeiten im linken Bereich und der anschließenden Auswahl eines anderen Elements im Editor-Fenster nicht mehr verloren.
* Bei Verwendung von `headless-canvas` ist kein manueller CSS-Import mehr erforderlich.
* Für CORS-Zwecke werden die richtigen Endpunkte für die Staging-, Vorschau- und Produktionsumgebung verwendet.
* Beschreibung wurde allen Schemafeldern hinzugefügt.
* Aktualisierungen an Inhaltsfragmenten mit mehreren Feldern werden jetzt für kontextbezogene Bearbeitungen unterstützt.
* Die Persistenz von Daten, wenn das Feld im Fokus ist, wurde robuster gemacht.
