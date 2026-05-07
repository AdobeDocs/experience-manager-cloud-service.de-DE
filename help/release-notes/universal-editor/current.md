---
title: Versionshinweise zum universellen Editor 2026.05.07
description: Dies sind die Versionshinweise für die Version 2026.05.07 des universellen Editors.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: 4f66cd6048d7a78bea33c0f9c21017983b9032d5
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 12%

---


# Versionshinweise zum universellen Editor 2026.05.07 {#release-notes}

Dies sind die Versionshinweise für die Version vom 7. Mai 2026 des universellen Editors.

>[!TIP]
>
>Informationen zum Testen von **zukünftigen** Funktionen des universellen Editors vor ihrer Veröffentlichung finden Sie in den [Vorschauversionshinweisen zum universellen Editor](/help/release-notes/universal-editor/preview.md).

>[!TIP]
>
>Die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service finden Sie auf [dieser Seite.](/help/release-notes/release-notes-cloud/release-notes-current.md)

## Neue Funktionen {#what-is-new}

* Sie können jetzt [Komponenten per Drag-and-Drop in den Editor ziehen, um sie zu verschieben.](/help/sites-cloud/authoring/universal-editor/authoring.md#drag-and-drop-move)
* Ein Service Worker wurde eingeführt, um die Latenz zwischen der Benutzeroberfläche des universellen Editors und den Backend-Systemen zu reduzieren.
* Alle Adapter für Inhaltsfragmente (AEM 6.5, OpenAPI und GraphQL) enthalten jetzt Filter für den Asset-Wähler, um Konsistenz zu gewährleisten und Benutzenden zu ermöglichen, nur zulässige Assets auszuwählen.
* `content:patch` Absicht wird jetzt bereitgestellt.
* Um die Barrierefreiheit zu verbessern, wurden Autorenfluss und Orientierungspunkte definiert.

## Weitere bevorstehende Verbesserungen {#other-improvements}

* Unnötige Typbestätigungen in `assignImageDimensionFields` wurden entfernt.
* Es wurde ein Problem behoben, bei dem bei der Server-seitigen Verarbeitung des `add` der Zeichenfolgenwert iteriert und als -Objekt anstelle eines Patches behandelt wurde.
