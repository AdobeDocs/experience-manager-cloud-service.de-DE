---
title: Vorlagen zum Erstellen von Seiten, die mit dem universellen Editor bearbeitbar sind
description: Erfahren Sie, wie Sie Vorlagen erstellen, die zum Erstellen von Seiten verwendet werden können, die mit dem universellen Editor bearbeitbar sind. So sparen Sie Zeit und gewährleisten ein konsistentes Branding.
solution: Experience Manager Sites
feature: Authoring
role: User
exl-id: f0d60086-e92e-4492-ad50-bef84fed2a82
source-git-commit: 33eb71b2828314ee2c75206ef7034313e2638360
workflow-type: tm+mt
source-wordcount: '778'
ht-degree: 3%

---


# Vorlagen zum Erstellen von Seiten, die mit dem universellen Editor bearbeitbar sind {#page-templates}

Erfahren Sie, wie Sie Vorlagen erstellen, die zum Erstellen von Seiten verwendet werden können, die mit dem universellen Editor bearbeitbar sind. So sparen Sie Zeit und gewährleisten ein konsistentes Branding.

>[!NOTE]
>
>Diese Funktion wird in einer kommenden Version von AEM as a Cloud Service verfügbar sein.

>[!NOTE]
>
>[Vorlagen sind auch für das Erstellen von Seiten verfügbar, die mit dem Seiteneditor bearbeitet werden können.](/help/sites-cloud/authoring/page-editor/templates.md)

## Was sind Seitenvorlagen? {#what-are}

Branding- und Marketingrichtlinien schreiben häufig bestimmte Layouts für Ihre Inhaltsseiten vor. Es ist auch oft eine praktische Realität, dass viele Ihrer Seiten dieselbe Struktur und Layout aufweisen. Um die Zeit Ihrer Inhaltsautoren zu sparen, können Seiten aus Vorlagen erstellt werden.

Seitenvorlagen dienen als Masterkopien Ihrer Seitenlayouts. Wenn Sie eine Seite aus einer Vorlage erstellen, wird der anfängliche Inhalt der Vorlage auf die neue Seite kopiert, was dazu beiträgt, das grundlegende Layout und den Inhalt der Seite für den Inhaltsautor vorzudefinieren und so Zeit zu sparen.

## Aktivieren von Seitenvorlagen {#enabling-templates}

Um Vorlagen zum Erstellen von Seiten zu verwenden, die mit dem universellen Editor bearbeitet werden können, müssen Sie die Option aktivieren.

Aktivieren Sie zunächst bearbeitbare Vorlagen für die Konfiguration Ihrer Site.

1. Verwenden Sie die Konsole **Sites** und wählen Sie [den Stamm Ihrer Site aus.](/help/sites-cloud/authoring/sites-console/introduction.md#selecting-resources)
1. Sobald der Site-Stamm ausgewählt ist, tippen oder klicken Sie in der Symbolleiste auf das Symbol [**Eigenschaften**](/help/sites-cloud/authoring/sites-console/page-properties.md) .
1. Notieren Sie sich auf der Registerkarte **Erweitert** des Eigenschaftendialogfelds den Wert im Feld **Cloud-Konfiguration** .
1. Wählen Sie im Hauptnavigationsmenü **Tools** -> **Allgemein** -> **Konfigurationsbrowser** aus.
1. Wählen Sie im **[Konfigurations-Browser](/help/implementing/developing/introduction/configurations.md)** die Konfiguration aus, die Sie im vorherigen Schritt notiert haben, und tippen oder klicken Sie in der Symbolleiste auf **Eigenschaften** .
1. Aktivieren Sie im Fenster **Konfigurationseigenschaften** die Option **Bearbeitbare Vorlagen**.
1. Tippen oder klicken Sie auf **Speichern und schließen**.

Sobald die Konfiguration aktiviert ist, müssen Sie Vorlagen für Ihre Site zulassen.

1. Verwenden Sie die Konsole **Sites** und wählen Sie [den Stamm Ihrer Site aus.](/help/sites-cloud/authoring/sites-console/introduction.md#selecting-resources)
1. Sobald der Site-Stamm ausgewählt ist, tippen oder klicken Sie in der Symbolleiste auf das Symbol [**Eigenschaften**](/help/sites-cloud/authoring/sites-console/page-properties.md) .
1. Tippen oder klicken Sie auf der Registerkarte **Erweitert** des Eigenschaftendialogfelds im Abschnitt **Vorlageneinstellungen** auf die Schaltfläche **Hinzufügen** .
1. Fügen Sie in dem neuen, leeren Feld, das unter **Zulässige Vorlagen** angezeigt wird, den Pfad `/conf/<site>/settings/wcm/templates/.*` hinzu.
1. Tippen oder klicken Sie auf **Speichern und schließen**.

Sie können jetzt Vorlagen verwenden, um Seiten für Ihre Site zu erstellen. Diese Aufgabe darf nur einmal für jede Site/Konfiguration ausgeführt werden, in der Sie Vorlagen verwenden möchten, wenn Sie mit dem universellen Editor bearbeitbare Seiten erstellen.

## Erstellen neuer Vorlagen {#create-new}

Sie können entweder [eine neue Seite erstellen](/help/sites-cloud/authoring/sites-console/creating-pages.md), die als Vorlage dienen soll, oder eine vorhandene Seite als Grundlage für eine Vorlage verwenden.

1. Verwenden Sie die Konsole **Sites** , um zu [zur neuen oder vorhandenen Seite](/help/sites-cloud/authoring/sites-console/introduction.md#selecting-resources) zu navigieren, die Sie als Vorlage verwenden möchten, und tippen oder klicken Sie darauf, um sie auszuwählen.

1. Nachdem die Seite ausgewählt wurde, tippen oder klicken Sie in der Symbolleiste auf das Symbol [**Eigenschaften**](/help/sites-cloud/authoring/sites-console/page-properties.md) .

1. Wählen Sie auf der Registerkarte **Erweitert** des Eigenschaftendialogs im Abschnitt **Vorlageneinstellungen** den Umschalter **Seite als Vorlage verwenden** aus.

1. Tippen oder klicken Sie auf **Speichern und schließen**.

Ihre neue Seite kann jetzt beim Erstellen neuer Seiten als Vorlage verwendet werden.

## Erstellen einer Seite aus einer Vorlage {#creating-from-template}

Das Erstellen einer Seite aus einer Vorlage, die mit dem universellen Editor bearbeitet werden kann, entspricht dem Erstellen einer beliebigen anderen Seite durch [.](/help/sites-cloud/authoring/sites-console/creating-pages.md)

1. Verwenden Sie die Konsole **Sites** , um [zu dem Ort](/help/sites-cloud/authoring/sites-console/introduction.md#selecting-resources) zu navigieren, an dem Sie die neue Seite erstellen möchten.

1. Tippen oder klicken Sie auf **Erstellen** > **Seite**.

1. Auf der Registerkarte **Vorlage** des Assistenten **Seite erstellen** können Sie auswählen, auf welcher Vorlage Sie die neue Seite basieren möchten. Tippen oder klicken Sie auf die gewünschte Vorlage, um sie auszuwählen, und tippen oder klicken Sie dann auf **Weiter**.

Schließen Sie den Assistenten wie bei jeder anderen Seite aus und erstellen Sie die neue Seite auf der Basis der ausgewählten Vorlage.

## Seiten und Vorlagen {#pages-vs-templates}

Seitenvorlagen definieren nur den anfänglichen Inhalt von Seiten. Seiten können dann mit dem universellen Editor vollständig bearbeitet werden.

* Aus Seitenvorlagen erstellte Seiten sind unabhängige Kopien der Vorlage.
* Wenn sich die Vorlage ändert, ändern sich die vorhandenen Seiten, die auf dieser Vorlage basieren, nicht.
* Der Inhaltsautor kann den Inhalt der resultierenden Seite bei Bedarf ändern und aktualisieren, ohne dass Einschränkungen von der Vorlage ausgehen.

## Bearbeitbare Vorlagen {#editable-templates}

Mit dem [Seiten-Editor](/help/sites-cloud/authoring/page-editor/introduction.md) erstellte Seiten können ebenfalls auf Vorlagen basieren. Vorlagen, die zum Erstellen von Seiten für den universellen Editor und den Seiten-Editor verwendet werden, nutzen beide AEM [bearbeitbaren Vorlagen.](/help/implementing/developing/components/templates.md)

Vorlagen, mit denen mit dem Seiteneditor bearbeitbare Seiten erstellt werden, nutzen alle Funktionen bearbeitbarer Vorlagen. Vorlagen zum Erstellen von Seiten, die mit dem universellen Editor bearbeitbar sind, verwenden nur die Funktion für den anfänglichen Inhalt.
