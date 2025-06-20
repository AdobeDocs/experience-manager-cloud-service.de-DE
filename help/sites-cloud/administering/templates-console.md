---
title: Die Vorlagenkonsole
description: Erfahren Sie, wie die Vorlagenkonsole als zentraler Ort zum Anzeigen und Verwalten Ihrer Seitenvorlagen dient.
solution: Experience Manager Sites
feature: Administering
role: User
exl-id: d11d7176-dd35-4855-9dcd-dd40ff096510
source-git-commit: 3238b11cdd891cf18048199d4103397e3af75edf
workflow-type: tm+mt
source-wordcount: '857'
ht-degree: 97%

---

# Die Vorlagenkonsole {#templates-console}

Erfahren Sie, wie die Vorlagenkonsole als zentraler Ort zum Anzeigen und Verwalten Ihrer Seitenvorlagen dient.

## Überblick {#overview}

Beim Erstellen einer Seite müssen Sie eine Vorlage auswählen. Die Seitenvorlage wird als Basis für die neue Seite genutzt. Die [bearbeitbaren Vorlagen von AEM](/help/implementing/developing/components/templates.md) können die Struktur der Seite, anfängliche Inhalte und die Komponenten, die verwendet werden können (Design-Eigenschaften), definieren.

Inhaltsautorinnen und -autoren werden eine Auswahl verfügbarer Vorlagen angezeigt, wenn sie [neue Seiten in der Sites-Konsole erstellen](/help/sites-cloud/authoring/sites-console/creating-pages.md). Mit Vorlagen können Seiten erstellt werden, die wie folgt bearbeitbar sind:

* Über den [Seiteneditor](/help/sites-cloud/authoring/page-editor/templates.md) oder
* [den universellen Editor](/help/sites-cloud/authoring/universal-editor/templates.md)

Die Vorlagenkonsole ermöglicht es Admins, alle Seitenvorlagen zentral anzuzeigen und zu verwalten.

## Zugreifen auf die Vorlagenkonsole {#accessing}

1. Melden Sie sich bei AEM as a Cloud Service an.
1. Öffnen Sie die globale Navigation und wählen Sie das Panel **Tools** und dann **Allgemein** -> **Vorlagen** aus.

## Ausrichtung {#orientation}

Die Vorlagenkonsole ist in Form von Ordnern mit einem Ordner pro [Konfiguration](/help/implementing/developing/introduction/configurations.md) organisiert, in dem bearbeitbare Vorlagen für die Konfiguration aktiviert wurden.

![Die Vorlagenkonsole](assets/templates-console/templates-console.png)

[Die Standardansicht](/help/sites-cloud/authoring/quick-start.md) der Konsole ist die Kartenansicht. Tippen oder klicken Sie auf einen Ordner, um dessen Inhalt zu erkunden.

![Inhalt des Vorlagenordners in der Vorlagenkonsole](assets/templates-console/templates-console-templates.png)

Wählen Sie eine Vorlage aus, um die in der Symbolleiste verfügbaren Optionen anzuzeigen.

![Symbolleiste der Vorlagenkonsole](assets/templates-console/templates-console-toolbar.png)

* [Bearbeiten](#edit-edit)
* [Eigenschaften](#properties)
* [Deaktivieren/Aktivieren](#enable-disable)
* [Veröffentlichen](#publish)
* [Kopieren](#copy)
* [Löschen](#delete)

## Bearbeiten {#edit}

Durch Bearbeiten einer Vorlage wird der Editor geöffnet, mit dem die Vorlage erstellt wurde. Sie haben folgende Möglichkeiten:

* [den Vorlageneditor](/help/sites-cloud/authoring/page-editor/templates.md)
* [den universellen Editor](/help/sites-cloud/authoring/universal-editor/templates.md)

Mit dem jeweiligen Editor können Sie die erforderlichen Änderungen an der Vorlage vornehmen. Beachten Sie, dass sich die Bearbeitung einer verwendeten Vorlage auf Ihre Autorinnen und Autoren auswirken kann.

* Bei Vorlagen, die mit dem Vorlageneditor erstellt wurden, können Änderungen Live-Seiten betreffen, die auf der ausgewählten Vorlage basieren.
* Bei Vorlagen, die mit dem universellen Editor erstellt wurden, wirken sich Änderungen nur auf neue Seiten aus, die Ihre Autorinnen und Autoren basierend auf der ausgewählten Vorlage erstellen.

Wenn eine Autorin bzw. ein Autor beginnt, eine mit dem Vorlageneditor erstellte Vorlage zu bearbeiten, die bereits aktiviert wurde, wird eine Warnung angezeigt. 

>[!TIP]
>
>Nachdem Sie eine Vorlage in der Konsole ausgewählt haben, verwenden Sie den Hotkey `e`, um die ausgewählte Vorlage zu bearbeiten.

## Eigenschaften {#properties}

Sie können die [Eigenschaften der Vorlage](/help/sites-cloud/authoring/page-editor/templates.md) ähnlich wie [Seiteneigenschaften bearbeiten.Zu den ](/help/sites-cloud/authoring/sites-console/edit-page-properties.md) gehören:

* Vorlagentitel
* Beschreibung
* Bild

>[!TIP]
>
>Nachdem Sie eine Vorlage in der Konsole ausgewählt haben, verwenden Sie den Hotkey `p`, um die Eigenschaften der ausgewählten Vorlage zu öffnen.

## Aktivieren und Deaktivieren {#enable-disable}

Eine Vorlage kann einen von drei Status aufweisen:

* **Entwurf**: Die Vorlage wird noch erstellt und steht zum Erstellen neuer Seiten nicht zur Verfügung.
* **Aktiviert**: Die Vorlage ist fertig und zum Erstellen neuer Seiten verfügbar.
* **Deaktiviert**: Die Vorlage ist fertig, aber für das Erstellen neuer Seiten nicht verfügbar.

Wenn eine Vorlage erstellt wird, befindet sie sich standardmäßig entweder im Status **Entwurf** (für Vorlagen, die mit dem [Vorlageneditor](/help/sites-cloud/authoring/page-editor/templates.md) erstellt wurden) oder **Aktiviert** (für Vorlagen, die mit dem [universellen Editor](/help/sites-cloud/authoring/universal-editor/templates.md) erstellt wurden).

Eine Vorlage muss aktiviert sein, damit sie von Inhaltsautorinnen und -autoren zum Erstellen von Seiten verwendet werden kann. Wenn eine Vorlage nicht mehr benötigt wird, kann sie deaktiviert werden, sodass sie nicht mehr im Assistenten für die Seitenerstellung angezeigt wird.

* Wählen Sie die Vorlage aus und klicken Sie auf **Deaktivieren**, um die Vorlage zu deaktivieren.
* Wählen Sie die Vorlage aus und klicken Sie auf **Aktivieren**, um die Vorlage zu aktivieren.

## Publishing {#publish}

Eine mit dem Vorlageneditor erstellte Vorlage kann erst nach ihrer Veröffentlichung verwendet werden. Wählen Sie die Vorlage aus und klicken Sie auf **Veröffentlichen**, um sie zu veröffentlichen.

Mit dem universellen Editor erstellte Vorlagen müssen nicht veröffentlicht werden, damit sie verwendet werden können.

## Kopieren {#copy}

Wenn Sie über mehrere Seiten mit einer ähnlichen Struktur verfügen, können Sie mit der Schaltfläche **Kopieren** einen Kopie einer Vorlage erstellen und die Kopie dann entsprechend Ihren Anforderungen variieren. Dies ist auch nützlich, wenn Sie eine Vorlage auf einer anderen Site verwenden möchten.

1. Wählen Sie die Vorlage aus und tippen oder klicken Sie auf **Kopieren**, um eine Kopie zu erstellen.
1. Navigieren Sie zu dem Ort, an dem Sie die Kopie erstellen möchten. 
1. Tippen oder klicken Sie in der Symbolleiste auf **Einfügen**.

Nach dem Einfügen haben Sie folgende Möglichkeiten:

* [Bearbeiten der Vorlage](#edit), um sie nach Bedarf anzupassen.
* [Verwenden des Fensters „Eigenschaften“](#properties), um den Vorlagentitel zu aktualisieren.
* [Aktivieren der Vorlage](#enable-disable), damit sie zum Erstellen von Seiten verwendet werden kann.
* [Veröffentlichen der Vorlage](#publish), falls erforderlich.

>[!TIP]
>
>Nachdem Sie eine Vorlage in der Konsole ausgewählt haben, verwenden Sie den Hotkey `Command+c` oder `ctrl+c`, um die ausgewählte Vorlage zu kopieren.

## Löschen {#delete}

Wenn eine Vorlage nicht mehr benötigt wird, kann sie gelöscht werden, sofern sie nicht von Seiten referenziert wird.

Wählen Sie die Vorlage aus und tippen oder klicken Sie auf **Löschen**, um sie zu löschen.

>[!TIP]
>
>Nachdem Sie eine Vorlage in der Konsole ausgewählt haben, verwenden Sie den Hotkey `Backspace`, um die ausgewählte Vorlage zu löschen.

## Erstellen von Vorlagen {#create}

Verwenden Sie die Schaltfläche **Erstellen** in der Konsole, um eine neue Vorlage an Ihrem aktuellen Speicherort zu erstellen. Weitere Informationen zum Erstellen einer Vorlage finden Sie im Dokument [Vorlagen zum Erstellen von Seiten, die mit dem Seiteneditor bearbeitet werden können](/help/sites-cloud/authoring/page-editor/templates.md).

Die Schaltfläche **Erstellen** wird nur verwendet, um Vorlagen zu erstellen, die mit dem Seiteneditor bearbeitet werden können. Weitere Informationen zum Erstellen von Vorlagen auf der Grundlage von Seiten, die mit dem universellen Editor erstellt wurden, finden Sie im Dokument [Vorlagen zum Erstellen von Seiten, die mit dem universellen Editor bearbeitbar sind](/help/sites-cloud/authoring/universal-editor/templates.md).
