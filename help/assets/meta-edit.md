---
title: Anleitung zum Bearbeiten oder Hinzufügen von Metadaten
description: Erfahren Sie mehr über Asset-Metadaten in AEM Assets und lernen Sie die verschiedenen Bearbeitungsmöglichkeiten kennen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# Anleitung zum Bearbeiten oder Hinzufügen von Metadaten {#how-to-edit-or-add-metadata}

Metadaten sind zusätzliche Informationen zum Element, die durchsucht werden können. Beim Hochladen eines Bildes werden sie automatisch extrahiert. Sie können die vorhandenen Metadaten bearbeiten oder neue Metadateneigenschaften vorhandenen Feldern hinzufügen (etwa wenn ein Metadatenfeld leer ist).

Da Unternehmen kontrollierte und zuverlässige Metadaten-Vokabeln benötigen, ist das AEM Assets-Hinzufügen neuer Metadateneigenschaften nicht zulässig. Autoren können keine neuen Metadatenfelder für Assets hinzufügen, Entwickler hingegen schon. Informationen finden Sie unter [Erstellen neuer Metadateneigenschaften für Assets](meta-edit.md#editing-metadata-schema).

## Bearbeiten von Metadaten für ein Asset {#editing-metadata-for-an-asset}

So bearbeiten Sie Metadaten:

1. Führen Sie einen der folgenden Schritte aus:

   * From the Assets UI, select the asset and click/tap the **[!UICONTROL View Properties]** icon from the toolbar.
   * From the asset thumbnail, select the **[!UICONTROL View Properties]** quick action.
   * From the asset page, click/tap **[!UICONTROL View Properties]** from the toolbar.
   Auf der Asset-Seite werden alle Metadaten des Assets angezeigt. Diese Metadaten wurden beim Hochladen (Erfassen) in AEM Assets automatisch extrahiert.

1. Make edits to the metadata under the various tabs, as required, and when completed, click/tap **[!UICONTROL Save]** from the toolbar to save your changes. Click/tap **[!UICONTROL Close]** to return to the Assets web interface.

   >[!NOTE]
   >
   >Ein leeres Textfeld gibt an, dass kein Metadatenset vorhanden ist. Sie können einen Wert in das Feld eingeben und speichern, um diese Metadateneigenschaft hinzuzufügen. 

Änderungen an den Metadaten eines Assets werden als Teil der XMP-Daten in die ursprüngliche Binärdatei zurückgeschrieben. Dies erfolgt über den AEM-Metadaten-Schreib-Workflow. Änderungen an den vorhandenen Eigenschaften (z. B. `dc:title`) werden überschrieben und neu erstellte Eigenschaften (einschließlich benutzerdefinierten Eigenschaften wie `cq:tags`) werden zusammen mit dem Schema hinzugefügt.

<!-- XMP write-back is supported and enabled for the platforms and file formats described in technical requirements. -->

## Bearbeiten von Metadatenschemata {#editing-metadata-schema}

Weitere Informationen zur Bearbeitung von Metadatenschemata finden Sie unter [Bearbeiten von Metadaten-Schemaformularen](metadata-schemas.md#edit-metadata-schema-forms).

## Registrieren eines benutzerdefinierten Namespace in AEM {#registering-a-custom-namespace-within-aem}

Sie können eigene Namespaces in AEM hinzufügen. Es gibt vordefinierte Namespaces wie cq, jcr und sling. Sie können aber auch einen Namespace für Ihre Repository-Metadaten und die XML-Verarbeitung hinzufügen.

1. Go to the node type administration page *https://&lt;host>:&lt;port>/crx/explorer/nodetypes/index.jsp*.
1. Click or tap **[!UICONTROL Namespaces]** at the top of the page. Die Seite zur Namespace-Verwaltung wird in einem Fenster angezeigt. 

1. To add a namespace, click or tap **[!UICONTROL New]** at the bottom.
1. Specify a custom namespace in the XML namespace convention (Specify the id in the form of a URI and an associated prefix for the id), and click or tap **[!UICONTROL Save]**.
