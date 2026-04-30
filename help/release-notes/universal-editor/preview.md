---
title: Versionshinweise zur Vorschau des universellen Editors
description: Dies sind die Versionshinweise für die Vorabversion des universellen Editors.
feature: Release Information
role: Admin
exl-id: e8d031aa-4676-4e45-977b-e5dffcc404c4
source-git-commit: f3ba70f276ab534e0becea47390fe58bf8a825d2
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---


# Versionshinweise zur Vorschau des universellen Editors {#preview}

Dies sind die Versionshinweise für die **Vorschauversion** des universellen Editors. Diese Funktionen sind derzeit in der „Vorschau-Umgebung“ **universellen Editors**. Diese Funktionen werden voraussichtlich am 7. Mai 2026 allgemein verfügbar sein.

Diese **Vorschau**-Versionshinweise werden bereitgestellt, damit Sie wissen, welche Änderungen am universellen Editor bevorstehen, und sie testen können, indem Sie [zu Ihrer Vorschauversion wechseln.](/help/sites-cloud/authoring/universal-editor/navigation.md#user-properties)

>[!TIP]
>
>Die **aktuellen Versionshinweise** für den universellen Editor finden Sie im Dokument [Versionshinweise zum universellen Editor.](/help/release-notes/universal-editor/current.md)

>[!NOTE]
>
>Der Inhalt der aktuellen Version sowie das Veröffentlichungsdatum können sich ändern.

## Künftige Funktionen {#upcoming-features}

* Ein Service Worker wurde eingeführt, um die Latenz zwischen der Benutzeroberfläche des universellen Editors und den Backend-Systemen zu reduzieren.
* Alle Adapter für Inhaltsfragmente (AEM 6.5, OpenAPI und GraphQL) enthalten jetzt Filter für den Asset-Wähler, um Konsistenz zu gewährleisten und Benutzenden zu ermöglichen, nur zulässige Assets auszuwählen.
* `content:patch` Absicht wird jetzt bereitgestellt.
* Um die Barrierefreiheit zu verbessern, wurden Autorenfluss und Orientierungspunkte definiert.

## Weitere bevorstehende Verbesserungen {#other-improvements}

* Unnötige Typbestätigungen in `assignImageDimensionFields` wurden entfernt.
* Es wurde ein Problem behoben, bei dem bei der Server-seitigen Verarbeitung des `add` der Zeichenfolgenwert iteriert und als -Objekt anstelle eines Patches behandelt wurde.
