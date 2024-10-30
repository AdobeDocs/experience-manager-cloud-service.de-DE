---
title: Verwalten lizenzierter Assets auf Content Hub
description: Erfahren Sie mehr über verschiedene Methoden zur Metadatenverwaltung und -bearbeitung
source-git-commit: 541d5819e19c67eb3f961e41000106178bff66de
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 2%

---


# Verwalten lizenzierter Assets auf Content Hub {#manage-licensed-assets-on-content-hub}

Als Administrator bearbeiten Sie das Metadatenformular, um das Feld für die Asset-Lizenz einzuschließen, damit es in den Asset-Eigenschaften in AEM Autorenumgebung angezeigt wird. Anschließend können Sie das Asset sowie seine Lizenz genehmigen, um das Asset in Content Hub lizenzieren und verfügbar zu machen.

Führen Sie die folgenden Schritte aus:

1. Bearbeiten Sie das Metadatenformular, um ein neues Textfeld einzuschließen und die Lizenzdetails einzuschließen. Ordnen Sie das Textfeld der Eigenschaft `dc:license` zu. Weitere Informationen zum Hinzufügen von Feldern zu einem Metadatenformular und zum Definieren von Eigenschaften finden Sie unter [Einrichten von Metadaten-Forms](/help/assets/metadata-assets-view.md#metadata-forms).
   ![ZIP-Extraktion](/help/assets/assets/metadata-form-edit.png)
1. Wenden Sie das Metadatenformular auf den Asset-Ordner an, um die in Schritt 1 enthaltenen Einstellungen anzuwenden. Informationen zum Zuweisen von Metadatenformularen zum Asset-Ordner finden Sie unter [Zuweisen von Metadatenformularen zu einem Ordner](/help/assets/metadata-assets-view.md#metadata-forms).
1. [Lizenzierte PDF genehmigen](/help/assets/manage-organize-assets-view.md#set-asset-status)
1. Wählen Sie das Asset aus und klicken Sie auf **Details** , um seine Eigenschaften anzuzeigen. Definieren Sie im in Schritt 1 hinzugefügten Lizenzfeld den absoluten Pfad für die Asset-Lizenz, die in Schritt 3 genehmigt oder bereits zuvor genehmigt wurde. Der absolute Pfad zu Content Hub folgt diesem Standardmuster: `/content/dam/(The asset's folder hierarchy within the DAM repository)/(asset_name).(file_extension)`. Beispiel: /content/dam/teamA/projects/documents/file1.pdf
   ![absoluter Pfad](/help/assets/assets/absolute-path.png)


