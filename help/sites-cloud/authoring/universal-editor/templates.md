---
title: Vorlagen zum Erstellen von Seiten, die mit dem universellen Editor bearbeitbar sind
description: Erfahren Sie, wie Sie Vorlagen erstellen, die zum Erstellen von Seiten verwendet werden können, die mit dem universellen Editor bearbeitbar sind. Dies spart Zeit und gewährleistet ein konsistentes Branding.
solution: Experience Manager Sites
feature: Authoring
role: User
exl-id: f0d60086-e92e-4492-ad50-bef84fed2a82
source-git-commit: bcf0940d3365ecde6788772d28d32f22f367816d
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 96%

---


# Vorlagen zum Erstellen von Seiten, die mit dem universellen Editor bearbeitbar sind {#page-templates}

Erfahren Sie, wie Sie Vorlagen erstellen, die zum Erstellen von Seiten verwendet werden können, die mit dem universellen Editor bearbeitbar sind. Dies spart Zeit und gewährleistet ein konsistentes Branding.

>[!NOTE]
>
>[Vorlagen sind auch für das Erstellen von Seiten verfügbar, die mit dem Seiteneditor bearbeitet werden können](/help/sites-cloud/authoring/page-editor/templates.md).

## Was sind Seitenvorlagen? {#what-are}

Branding- und Marketing-Richtlinien schreiben häufig bestimmte Layouts für Ihre Inhaltsseiten vor. Zudem weisen viele Ihrer Seiten in der täglichen Praxis dieselbe Struktur und dasselbe Layout auf. Seiten können aus Vorlagen erstellt werden, sodass Ihre Inhaltsautorinnen und -autoren Zeit sparen.

Seitenvorlagen dienen als Musterkopien Ihrer Seiten-Layouts. Wenn Sie eine Seite aus einer Vorlage erstellen, wird der ursprüngliche Inhalt der Vorlage auf die neue Seite kopiert, wodurch das grundlegende Layout und der Inhalt der Seite für die Inhaltsautorin bzw. den Inhaltsautor vordefiniert werden, was Zeit spart.

## Aktivieren von Seitenvorlagen {#enabling-templates}

Um Vorlagen zum Erstellen von Seiten zu verwenden, die mit dem universellen Editor bearbeitet werden können, müssen Sie die Option aktivieren.

Aktivieren Sie zunächst bearbeitbare Vorlagen für die Konfiguration Ihrer Site.

1. Verwenden Sie die **Sites**-Konsole und [wählen Sie das Stammverzeichnis Ihrer Site aus](/help/sites-cloud/authoring/sites-console/introduction.md#selecting-resources).
1. Sobald das Stammverzeichnis ausgewählt ist, tippen oder klicken Sie auf das Symbol [**Eigenschaften** in der Symbolleiste.](/help/sites-cloud/authoring/sites-console/page-properties.md)
1. Notieren Sie sich den Wert im Feld **Cloud-Konfiguration** auf der Registerkarte **Erweitert** des Eigenschaftendialogfelds.
1. Wählen Sie im Hauptnavigationsmenü **Tools** > **Allgemein** > **Konfigurations-Browser** aus.
1. Wählen Sie im **[Konfigurations-Browser](/help/implementing/developing/introduction/configurations.md)** die Konfiguration aus, die Sie im vorherigen Schritt notiert haben, und tippen oder klicken Sie in der Symbolleiste auf **Eigenschaften**.
1. Aktivieren Sie im Fenster **Konfigurationseigenschaften** die Option **Bearbeitbare Vorlagen**.
1. Tippen oder klicken Sie auf **Speichern und schließen**.

Sobald die Konfiguration aktiviert ist, müssen Sie Vorlagen für Ihre Site zulassen.

1. Verwenden Sie die **Sites**-Konsole und [wählen Sie das Stammverzeichnis Ihrer Site aus](/help/sites-cloud/authoring/sites-console/introduction.md#selecting-resources).
1. Sobald das Stammverzeichnis ausgewählt ist, tippen oder klicken Sie auf das Symbol [&#128279;](/help/sites-cloud/authoring/sites-console/page-properties.md) **Eigenschaften** in der Symbolleiste.
1. Tippen oder klicken Sie auf der Registerkarte **Erweitert** des Eigenschaftsdialogs unter dem Abschnitt **Vorlageneinstellungen** auf die Schaltfläche **Hinzufügen**.
1. Fügen Sie in dem neuen, leeren Feld, das unter **Zulässige Vorlagen** angezeigt wird, den Pfad `/conf/<site>/settings/wcm/templates/.*` hinzu.
1. Tippen oder klicken Sie auf **Speichern und schließen**.

Sie können jetzt Vorlagen verwenden, um Seiten für Ihre Site zu erstellen. Diese Aufgabe muss nur einmal für jede Website/Konfiguration ausgeführt werden, wo Sie Vorlagen verwenden möchten, um Seiten zu erstellen, die mit dem universellen Editor bearbeitet werden können.

## Erstellen neuer Vorlagen {#create-new}

Sie können entweder [eine neue Seite erstellen](/help/sites-cloud/authoring/sites-console/creating-pages.md), die als Vorlage dienen soll, oder eine vorhandene Seite als Grundlage für eine Vorlage verwenden.

1. Verwenden Sie die Konsole **Sites**, um [zu der neuen oder vorhandenen Seite zu navigieren](/help/sites-cloud/authoring/sites-console/introduction.md#selecting-resources), die Sie als Vorlage verwenden möchten, und tippen oder klicken Sie darauf, um sie auszuwählen.

1. Sobald die Seite ausgewählt ist, tippen Sie auf das Symbol [**Eigenschaften** in der Symbolleiste oder klicken Sie auf das Symbol ](/help/sites-cloud/authoring/sites-console/page-properties.md).

1. Wählen Sie unter dem Abschnitt **Vorlageneinstellungen** im Dialogfeld „Eigenschaften“ auf der Registerkarte **Erweitert** den Umschalter **Seite als Vorlage verwenden** aus.

1. Tippen oder klicken Sie auf **Speichern und schließen**.

Ihre neue Seite kann jetzt beim Erstellen neuer Seiten als Vorlage verwendet werden.

## Erstellen einer Seite aus einer Vorlage {#creating-from-template}

Das Erstellen einer Seite aus einer Vorlage, die mit dem universellen Editor bearbeitet werden kann, entspricht demselben Workflow wie bei der [Erstellung jeder anderen Seite](/help/sites-cloud/authoring/sites-console/creating-pages.md).

1. Verwenden Sie die **Sites**-Konsole, um [zu dem Speicherort zu navigieren](/help/sites-cloud/authoring/sites-console/introduction.md#selecting-resources), an dem Sie die neue Seite erstellen möchten.

1. Tippen oder klicken Sie auf **Erstellen** > **Seite**.

1. Auf der Registerkarte **Vorlage** des Assistenten zum **Erstellen einer Seite** können Sie auswählen, auf welcher Vorlage die neue Seite basieren soll. Tippen oder klicken Sie auf die gewünschte Vorlage, um sie auszuwählen, und tippen oder klicken Sie dann auf **Weiter**.

Schließen Sie den Assistenten wie bei jeder anderen Seite ab. Jetzt haben Sie die neue Seite auf Basis der ausgewählten Vorlage erstellt.

## Seiten und Vorlagen {#pages-vs-templates}

Seitenvorlagen definieren nur den anfänglichen Inhalt von Seiten. Seiten können dann mit dem universellen Editor vollständig bearbeitet werden.

* Seiten, die aus Seitenvorlagen erstellt wurden, sind unabhängige Kopien der Vorlage.
* Wenn sich die Vorlage ändert, bleiben die vorhandenen Seiten, die auf dieser Vorlage basieren, unverändert.
* Die Inhaltsautorin bzw. der Inhaltsautor kann den Inhalt der resultierenden Seite nach Bedarf ändern und aktualisieren, ohne Einschränkungen durch die Vorlage zu unterliegen.

## Bearbeitbare Vorlagen {#editable-templates}

Mit dem [Seiteneditor](/help/sites-cloud/authoring/page-editor/introduction.md) erstellte Seiten können ebenfalls auf Vorlagen basieren. Vorlagen, die zum Erstellen von Seiten für den universellen Editor und den Seiteneditor verwendet werden, nutzen die [bearbeitbaren Vorlagen](/help/implementing/developing/components/templates.md) von AEM.

Vorlagen, mit denen mit dem Seiteneditor bearbeitbare Seiten erstellt werden, nutzen alle Funktionen bearbeitbarer Vorlagen. Vorlagen, die zum Erstellen von mit dem universellen Editor bearbeitbaren Seiten verwendet werden, verwenden nur die anfängliche Inhaltsfunktion.
