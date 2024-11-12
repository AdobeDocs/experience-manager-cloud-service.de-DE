---
title: Die Vorlagenkonsole
description: Erfahren Sie, wie die Vorlagenkonsole als zentraler Ort für die Anzeige und Verwaltung Ihrer Seitenvorlagen dient.
solution: Experience Manager Sites
feature: Administering
role: User
source-git-commit: 993f81e0ff2b71ce2edf59a2c74398db3abe8f06
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 3%

---


# Die Vorlagenkonsole {#templates-console}

Erfahren Sie, wie die Vorlagenkonsole als zentraler Ort für die Anzeige und Verwaltung Ihrer Seitenvorlagen dient.

## Überblick {#overview}

Beim Erstellen einer Seite müssen Sie eine Vorlage auswählen. Die Seitenvorlage wird als Basis für die neue Seite genutzt. [AEM bearbeitbare Vorlagen](/help/implementing/developing/components/templates.md) können die Struktur der resultierenden Seite, den anfänglichen Inhalt und die Komponenten definieren, die verwendet werden können (Designeigenschaften).

Autoren von Inhalten wird eine Auswahl verfügbarer Vorlagen angezeigt, wenn sie [neue Seiten in der Sites-Konsole erstellen.](/help/sites-cloud/authoring/sites-console/creating-pages.md) Vorlagen können verwendet werden, um Seiten zu erstellen, die bearbeitet werden können mit:

* [Der Seiten-Editor](/help/sites-cloud/authoring/page-editor/templates.md) oder
* [Der universelle Editor](/help/sites-cloud/authoring/universal-editor/templates.md)

Die Vorlagenkonsole ermöglicht es einem Administrator, alle Seitenvorlagen zentral anzuzeigen und zu verwalten.

## Zugriff auf die Vorlagenkonsole {#accessing}

1. Melden Sie sich bei AEM as a Cloud Service an.
1. Öffnen Sie die globale Navigation und wählen Sie das Bedienfeld **Tools** und dann **Allgemein** -> **Vorlagen** aus.

## Ausrichtung {#orientation}

Die Vorlagenkonsole ist in Ordner mit einem Ordner pro [Konfiguration](/help/implementing/developing/introduction/configurations.md) unterteilt, in dem bearbeitbare Vorlagen für die Konfiguration aktiviert wurden.

![Die Vorlagenkonsole](assets/templates-console/templates-console.png)

[Die Standardansicht](/help/sites-cloud/authoring/quick-start.md) der Konsole ist die Kartenansicht. Tippen oder klicken Sie auf einen Ordner, um dessen Inhalt zu durchsuchen.

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

Durch Bearbeiten einer Vorlage wird der Editor geöffnet, der zum Erstellen der Vorlage verwendet wurde. Sie haben folgende Möglichkeiten:

* [Der Vorlagen-Editor](/help/sites-cloud/authoring/page-editor/templates.md)
* [Der universelle Editor](/help/sites-cloud/authoring/universal-editor/templates.md)

Mit jedem Editor können Sie die erforderlichen Änderungen an der Vorlage vornehmen. Beachten Sie, dass sich die Bearbeitung einer verwendeten Vorlage auf Ihre Autoren auswirken kann.

* Bei Vorlagen, die mit dem Vorlagen-Editor erstellt werden, können sich die vorgenommenen Änderungen auf Live-Seiten auswirken, die auf der ausgewählten Vorlage basieren.
* Bei Vorlagen, die mit dem universellen Editor erstellt werden, wirken sich die vorgenommenen Änderungen nur auf neue Seiten aus, die Ihre Autoren basierend auf der ausgewählten Vorlage erstellen.

Wenn ein Autor mit einer Vorlage beginnt, die mit dem bereits aktivierten Vorlageneditor erstellt wurde, wird eine Warnung angezeigt.

>[!TIP]
>
>Nachdem Sie eine Vorlage in der Konsole ausgewählt haben, verwenden Sie den Hotkey `e` , um die ausgewählte Vorlage zu bearbeiten.

## Eigenschaften {#properties}

Sie können die [Eigenschaften der Vorlage](/help/sites-cloud/authoring/page-editor/templates.md) auf dieselbe Weise bearbeiten wie die [Seiteneigenschaften bearbeiten.](/help/sites-cloud/authoring/sites-console/page-properties.md) Vorlageneigenschaften beinhalten:

* Vorlagentitel
* Beschreibung
* Bild

>[!TIP]
>
>Nachdem Sie eine Vorlage in der Konsole ausgewählt haben, verwenden Sie den Hotkey `p` , um die Eigenschaften der ausgewählten Vorlage zu öffnen.

## Aktivieren und Deaktivieren {#enable-disable}

Eine Vorlage kann einen von drei Status aufweisen:

* **Entwurf** - Die Vorlage wird noch erstellt und steht nicht zum Erstellen neuer Seiten zur Verfügung.
* **Aktiviert** - Die Vorlage ist abgeschlossen und steht zum Erstellen neuer Seiten zur Verfügung.
* **Deaktiviert** - Die Vorlage ist abgeschlossen, aber nicht für die Erstellung neuer Seiten verfügbar.

Wenn eine Vorlage erstellt wird, befindet sie sich standardmäßig entweder im Status **Entwurf** (für Vorlagen, die mit dem [Vorlagen-Editor](/help/sites-cloud/authoring/page-editor/templates.md) erstellt wurden) oder im Status **Aktiviert** (für Vorlagen, die mit dem [universellen Editor](/help/sites-cloud/authoring/universal-editor/templates.md) erstellt wurden).

Eine Vorlage muss aktiviert sein, bevor sie von Inhaltsautoren zum Erstellen von Seiten verwendet werden kann. Wenn eine Vorlage nicht mehr benötigt wird, kann sie deaktiviert werden, sodass sie nicht mehr im Seitenerstellungsassistenten angezeigt wird.

* Wählen Sie die Vorlage aus und klicken oder tippen Sie auf **Deaktivieren** , um die Vorlage zu deaktivieren.
* Wählen Sie die Vorlage aus und klicken oder tippen Sie auf **Aktivieren** , um die Vorlage zu aktivieren.

## Veröffentlichung {#publish}

Eine mit dem Vorlagen-Editor erstellte Vorlage kann erst nach ihrer Veröffentlichung verwendet werden. Wählen Sie die Vorlage aus und klicken oder tippen Sie auf **Publish** , um sie zu veröffentlichen.

Mit dem universellen Editor erstellte Vorlagen müssen nicht veröffentlicht werden, um verwendet werden zu können.

## Wird kopiert {#copy}

Wenn Sie eine Reihe von Seiten mit ähnlicher Struktur haben, können Sie die Schaltfläche **Kopieren** verwenden, um einen Umfang für eine Vorlage zu erstellen und die Kopie dann entsprechend Ihren Anforderungen zu variieren. Dies ist auch dann nützlich, wenn Sie eine Vorlage auf einer anderen Site verwenden möchten.

1. Wählen Sie die Vorlage aus und tippen oder klicken Sie auf **Kopieren** , um eine Kopie zu erstellen.
1. Navigieren Sie zu der Stelle, an der Sie die Kopie erstellen möchten.
1. Tippen oder klicken Sie in der Symbolleiste auf **Einfügen** .

Nach dem Einfügen können Sie:

* [Bearbeiten Sie die Vorlage](#edit), um sie nach Bedarf anzupassen.
* [Verwenden Sie das Eigenschaftenfenster](#properties), um den Vorlagentitel zu aktualisieren.
* [Aktivieren Sie die Vorlage](#enable-disable) , damit sie zum Erstellen einer Seite verwendet werden kann.
* [Publish Sie die Vorlage](#publish), falls erforderlich.

>[!TIP]
>
>Nachdem Sie eine Vorlage in der Konsole ausgewählt haben, verwenden Sie den Hotkey `Command+c` oder `ctrl+c`, um die ausgewählte Vorlage zu kopieren.

## Wird gelöscht {#delete}

Wenn eine Vorlage nicht mehr benötigt wird, kann sie gelöscht werden, sofern sie von keiner Seite referenziert wird.

Wählen Sie die Vorlage aus und tippen oder klicken Sie auf **Löschen** , um sie zu löschen.

>[!TIP]
>
>Nachdem Sie eine Vorlage in der Konsole ausgewählt haben, verwenden Sie den Hotkey `Backspace` , um die ausgewählte Vorlage zu löschen.

## Erstellen von Vorlagen {#create}

Verwenden Sie die Schaltfläche **Erstellen** in der Konsole, um eine neue Vorlage an Ihrem aktuellen Speicherort zu erstellen. Weitere Informationen zum Erstellen einer Vorlage finden Sie im Dokument [Vorlagen zum Erstellen von Seiten, die mit dem Seiteneditor bearbeitet werden können](/help/sites-cloud/authoring/page-editor/templates.md).

Die Schaltfläche **Erstellen** wird nur verwendet, um Vorlagen zu erstellen, die mit dem Seiteneditor bearbeitet werden können. Weitere Informationen zum Erstellen von Vorlagen auf der Basis von mit dem universellen Editor erstellten Seiten finden Sie im Dokument [Vorlagen zum Erstellen von Seiten, die mit dem universellen Editor bearbeitbar sind](/help/sites-cloud/authoring/universal-editor/templates.md) .
