---
title: Versionshinweise zum universellen Editor 2026.05.28
description: Dies sind die Versionshinweise für die Version 2026.05.28 des universellen Editors.
feature: Release Information
role: Admin
exl-id: d16ed78d-d5a3-45bf-a415-5951e60b53f9
source-git-commit: 63c3a7e2ca28890370701fd388f6cc9f068c6dc5
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 14%

---


# Versionshinweise zum universellen Editor 2026.05.28 {#release-notes}

Dies sind die Versionshinweise für die Version vom 28. Mai 2026 des universellen Editors.

>[!TIP]
>
>Informationen zum Testen von **zukünftigen** Funktionen des universellen Editors vor ihrer Veröffentlichung finden Sie in den [Vorschauversionshinweisen zum universellen Editor](/help/release-notes/universal-editor/preview.md).

>[!TIP]
>
>Die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service finden Sie auf [dieser Seite.](/help/release-notes/release-notes-cloud/release-notes-current.md)

## Neue Funktionen {#what-is-new}

* Der Symbolleiste wurde eine neue Schaltfläche hinzugefügt ([ Zugriff auf die Seiteneigenschaften von AEM.](/help/sites-cloud/authoring/universal-editor/authoring.md#page-properties)
   * Dadurch werden die Funktionen der früheren `aem-page-properties` ([) ](/help/implementing/universal-editor/extending.md) universellen Editor hinzugefügt.
   * Die Schaltfläche wird nur angezeigt, wenn die Remote-Seite eine [Verbindung mit Protokoll](/help/implementing/universal-editor/component-definition.md#plugins) `aem` oder `xwalk` aufweist und ein eindeutiger Seitenpfad aus der aktuellen bearbeitbaren Datei aufgelöst werden kann.

## Andere Verbesserungen {#other-improvements}

* Die standardmäßige Hintergrundfarbe der Arbeitsfläche für die Bearbeitung ist jetzt weiß (#FFFFFF), wenn das Programm keine eigene Hintergrundfarbe festlegt.
* Es wurde ein Problem behoben, bei dem das Kopieren und Einfügen über Seiten hinweg nicht funktionierte.
