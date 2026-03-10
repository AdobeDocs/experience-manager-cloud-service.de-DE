---
title: Verwalten lizenzierter Assets in Content Hub
description: Erfahren Sie, wie Sie ein Lizenzfeld zum Metadatenformular für Assets hinzufügen, die Metadateneigenschaft „Lizenz“ auf Asset-Ordner anwenden und Assets mit Lizenzen zur Nutzung genehmigen.
badgeSaas: label="AEM Assets" type="Positive" tooltip="Gilt für AEM Assets)."
exl-id: ac3aad9f-c7b3-47a7-9314-a2f8277f0d3e
source-git-commit: 59f97fc6ded4274c27400f56b50b4a3329cc471a
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 40%

---

# Verwalten lizenzierter Assets in Content Hub {#manage-licensed-assets-on-content-hub}

Als Admin bearbeiten Sie das Metadatenformular, um das Feld für die Asset-Lizenz einzuschließen, damit es in den Asset-Eigenschaften in der AEM-Autorenumgebung angezeigt wird. Anschließend können Sie das Asset sowie seine Lizenz genehmigen, um das Asset in Content Hub zu lizenzieren und verfügbar zu machen.

Führen Sie die folgenden Schritte aus:

1. Bearbeiten Sie das Metadatenformular, um ein neues Textfeld für die Lizenzdetails hinzuzufügen. Ordnen Sie das Textfeld der Eigenschaft `dc:license` zu. Weitere Informationen zum Hinzufügen von Feldern zu einem Metadatenformular und zum Definieren von Eigenschaften finden Sie unter [Einrichten von Metadatenformularen](/help/assets/metadata-assets-view.md#metadata-forms).
   ![ZIP-Extraktion](/help/assets/assets/metadata-form-edit.png)
1. Wenden Sie das Metadatenformular auf den Asset-Ordner an, um die Einstellungen aus Schritt 1 anzuwenden. Informationen zum Zuweisen von Metadatenformularen zum Asset-Ordner finden Sie unter [Zuweisen von Metadatenformularen zu einem Ordner](/help/assets/metadata-assets-view.md#metadata-forms).
1. [Genehmigen Sie die lizenzierte PDF](/help/assets/manage-organize-assets-view.md#set-asset-status)
1. Wählen Sie das Asset aus und klicken Sie auf **Details**, um seine Eigenschaften anzuzeigen. Definieren Sie im in Schritt 1 hinzugefügten Lizenzfeld den absoluten Pfad für die Asset-Lizenz, die in Schritt 3 oder bereits zuvor genehmigt wurde. Der absolute Pfad zu Content Hub folgt diesem Standardmuster: `/content/dam/(The asset's folder hierarchy within the DAM repository)/(asset_name).(file_extension)`. Zum Beispiel: /content/dam/teamA/projects/documents/file1.pdf
   ![Absoluter Pfad](/help/assets/assets/absolute-path.png)
1. Genehmigen Sie das Asset, um es in Content Hub verfügbar zu machen, und klicken Sie auf **Speichern**. Informationen zum Genehmigen eines Assets finden Sie unter [Festlegen des Asset-Status](/help/assets/manage-organize-assets-view.md#set-asset-status).

## Häufig gestellte Fragen {#faqs-manage-licensed-assets-content-hub}

### Welchen Zweck hat die Verwaltung lizenzierter Assets in AEM Assets Content Hub?

Durch die Verwaltung lizenzierter Assets in AEM Assets Content Hub können Administratoren sicherstellen, dass nur genehmigte Assets mit gültigen Lizenzen verwendet werden können. Dies gewährleistet die Einhaltung von Richtlinien und eine ordnungsgemäße Metadatenverfolgung in der AEM-Autorenumgebung.

### Wie kann ich in Experience Manager as a Cloud Service ein Lizenzfeld zu den Asset-Eigenschaften hinzufügen?

In der AEM Assets-Ansicht können Sie ein Lizenzfeld zu den Asset-Eigenschaften hinzufügen, indem Sie das Metadatenformular bearbeiten, um ein neues Textfeld einzuschließen, das der `dc:license`-Eigenschaft zugeordnet ist. Dieses Feld wird dann in den Asset-Eigenschaften in der AEM Assets-Autorenumgebung angezeigt.

### Wie wird ein Metadatenformular auf einen Asset-Ordner angewendet, um das Lizenzfeld in die Asset-Eigenschaften in AEM Assets aufzunehmen?

Bearbeiten Sie in der AEM Assets-Ansicht das Metadatenformular, um das Lizenzfeld einzuschließen. Wenden Sie dieses Metadatenformular auf den gewünschten Asset-Ordner an, um sicherzustellen, dass die neuen Einstellungen für alle Assets in diesem Ordner integriert werden.

### Wie gebe ich die Lizenzdetails für ein Asset in der AEM Assets-Ansicht an?

Um die Lizenzdetails anzugeben, wählen Sie das Asset aus **klicken Sie auf „Details**, um seine Eigenschaften anzuzeigen, und geben Sie den absoluten Pfad der genehmigten Asset-Lizenz in das Lizenzfeld ein, das zum Metadatenformular hinzugefügt wurde.

### Welches Format muss der absolute Pfad von AEM Assets Content Hub für eine Asset-Lizenz haben?

Der absolute Pfad von Content Hub sollte dem Muster folgen: /content/dam/(Die Ordnerhierarchie des Assets im DAM-Repository)/(asset_name).(file_extension). Beispiel: `/content/dam/teamA/projects/documents/file1.pdf`.

### Warum ist es wichtig, sowohl das Asset als auch seine Lizenz zu genehmigen, um sie in AEM Assets Content Hub verfügbar zu machen?

Durch die Genehmigung von sowohl Asset als auch Lizenz wird sichergestellt, dass nur ordnungsgemäß lizenzierte und autorisierte Assets in AEM Assets Content Hub verfügbar sind, wodurch die Compliance und die korrekten Verwendungsrechte gewährleistet bleiben.

### Wie stelle ich ein Asset in AEM Assets Content Hub nach der Genehmigung seiner Lizenz zur Verfügung?

Nachdem Sie den Lizenzpfad in den Eigenschaften des Assets definiert haben, genehmigen Sie das Asset und klicken Sie auf Speichern . Durch diese Aktion wird das lizenzierte Asset in AEM Assets Content Hub verfügbar gemacht.

### Wer ist für die Verwaltung lizenzierter Assets in AEM Assets Content Hub verantwortlich?

Admins sind in AEM Assets Content Hub für die Bearbeitung von Metadatenformularen, die Zuweisung zu Asset-Ordnern und die Genehmigung von Assets und deren Lizenzen verantwortlich.
