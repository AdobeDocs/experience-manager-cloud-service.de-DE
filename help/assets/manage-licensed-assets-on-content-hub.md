---
title: Verwalten lizenzierter Assets in Content Hub
description: Erfahren Sie, wie Sie ein Lizenzfeld zum Metadatenformular für Assets hinzufügen, die Metadateneigenschaft „Lizenz“ auf Asset-Ordner anwenden und Assets mit Lizenzen zur Nutzung genehmigen.
exl-id: ac3aad9f-c7b3-47a7-9314-a2f8277f0d3e
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 100%

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
