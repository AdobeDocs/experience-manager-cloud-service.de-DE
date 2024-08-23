---
title: Verwenden von Seitenvorlagen mit dem universellen Editor
description: Erfahren Sie, wie Sie mit dem universellen Editor Seitenvorlagen erstellen und verwenden.
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 773ce75975f4dcc2c5310422bcc377b487ebec25
workflow-type: tm+mt
source-wordcount: '648'
ht-degree: 2%

---


# Verwenden von Seitenvorlagen mit dem universellen Editor {#page-templates}

Erfahren Sie, wie Sie mit dem universellen Editor Seitenvorlagen erstellen und verwenden.

>[!NOTE]
>
>Diese Funktion wird in einer kommenden Version von AEM as a Cloud Service verfügbar sein.

## Was sind Seitenvorlagen? {#what-are}

Branding- und Marketingrichtlinien schreiben häufig bestimmte Layouts für Ihre Inhaltsseiten vor. Es ist auch oft eine praktische Realität, dass viele Ihrer Seiten dieselbe Struktur und Layout aufweisen. Um die Zeit Ihrer Inhaltsautoren zu sparen, können Seiten aus Vorlagen erstellt werden.

Seitenvorlagen dienen als Masterkopien Ihrer Seitenlayouts. Wenn Sie eine Seite aus einer Vorlage erstellen, wird der Inhalt der Vorlage auf die neue Seite kopiert, was dazu beiträgt, das Layout und den anfänglichen Inhalt der Seite für den Inhaltsautor vorzudefinieren und so Zeit zu sparen.

## Erstellen einer Seitenvorlage {#creating}

Sie können eine Seitenvorlage erstellen, indem Sie eine neue Seite erstellen oder eine vorhandene Seite als Vorlage verwenden. In beiden Fällen verwenden Sie die Konsole [**Sites**.](/help/sites-cloud/authoring/sites-console/introduction.md)

### Erstellen neuer Vorlagen {#create-new}

1. Verwenden Sie die Konsole **Sites** , um zu dem Speicherort zu navigieren, an dem Sie die neue Seite erstellen möchten, die als Vorlage dienen soll, und [erstellen Sie die Seite wie jede andere.](/help/sites-cloud/authoring/sites-console/creating-pages.md)

1. Nachdem die Seite erstellt wurde und Sie zur Konsole zurückkehren, wählen Sie die Seite aus und tippen oder klicken Sie in der Symbolleiste auf das Symbol [**Eigenschaften**](/help/sites-cloud/authoring/sites-console/page-properties.md) .

1. Wählen Sie auf der Registerkarte **Erweitert** des Eigenschaftendialogs im Abschnitt **Vorlageneinstellungen** den Umschalter **Als Vorlage verwenden** aus.

1. Geben Sie im Feld **Vorlagenname** einen beschreibenden Namen ein.

   * Dies ist der Name, der anzeigt, dass neue Inhaltsseiten erstellt werden, und Sie wählen eine Vorlage aus, auf der die neue Seite basieren soll.

1. Tippen oder klicken Sie auf **Speichern und schließen**.

Ihre neue Seite kann jetzt beim Erstellen neuer Seiten als Vorlage verwendet werden.

### Verwenden einer vorhandenen Seite als Vorlage {#existing-page}

1. Verwenden Sie die Konsole **Sites** , um zu [zum Speicherort der Seite](/help/sites-cloud/authoring/sites-console/introduction.md#selecting-resources) zu navigieren, die Sie als Vorlage verwenden möchten.

1. Wählen Sie die Seite aus und tippen oder klicken Sie dann in der Symbolleiste auf das Symbol [**Eigenschaften**](/help/sites-cloud/authoring/sites-console/page-properties.md) .

1. Wählen Sie auf der Registerkarte **Erweitert** des Eigenschaftendialogs im Abschnitt **Vorlageneinstellungen** den Umschalter **Als Vorlage verwenden** aus.

1. Geben Sie im Feld **Vorlagenname** einen beschreibenden Namen ein.

   * Dies ist der Name, der anzeigt, dass neue Inhaltsseiten erstellt werden, und Sie wählen eine Vorlage aus, auf der die neue Seite basieren soll.

1. Tippen oder klicken Sie auf **Speichern und schließen**.

Die ausgewählte Seite kann jetzt beim Erstellen neuer Seiten als Vorlage verwendet werden.

## Erstellen einer Seite aus einer Vorlage {#creating-from-template}

Das Erstellen einer Seite aus einer Vorlage für die Verwendung mit dem universellen Editor ist derselbe Workflow wie das Erstellen der Seite durch [ und das Erstellen anderer Seiten.](/help/sites-cloud/authoring/sites-console/creating-pages.md)

1. Verwenden Sie die Konsole **Sites** , um [zu dem Ort](/help/sites-cloud/authoring/sites-console/introduction.md#selecting-resources) zu navigieren, an dem Sie die neue Seite erstellen möchten.

1. Tippen oder klicken Sie auf **Erstellen** > **Seite**.

1. Auf der Registerkarte **Vorlage** des Assistenten **Seite erstellen** können Sie auswählen, auf welcher Vorlage Sie die neue Seite basieren möchten. Tippen oder klicken Sie auf die gewünschte Vorlage, um sie auszuwählen, und tippen oder klicken Sie dann auf **Weiter**.

Schließen Sie den Assistenten wie bei jeder anderen Seite aus und erstellen Sie die neue Seite auf der Basis der ausgewählten Vorlage.

## Universal Editor und Seiten-Editor {#page-vs-universal}

Seitenvorlagen für den universellen Editor lösen dasselbe Problem wie [Seitenvorlagen für den AEM Seiteneditor:](/help/sites-cloud/authoring/page-editor/templates.md), um Inhalte wiederzuverwenden und Seiten schnell basierend auf einer Reihe vordefinierter Layouts zu erstellen. Sie lösen das Problem jedoch auf sehr unterschiedliche Weise. Wenn Sie Benutzer des Seiteneditors sind, beachten Sie diese Unterschiede.

* Seiten, die aus Seitenvorlagen für den universellen Editor erstellt wurden, sind unabhängige Kopien der Vorlage.
* Wenn sich die Vorlage ändert, bleiben die resultierenden Seiten unverändert.
* Der Inhaltsautor kann den Inhalt der resultierenden Seite bei Bedarf ändern und aktualisieren, ohne dass Einschränkungen von der Vorlage ausgehen.
