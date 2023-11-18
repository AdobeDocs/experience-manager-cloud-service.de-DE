---
title: Anleitung zum Bearbeiten oder Hinzufügen von Metadaten
description: Erfahren Sie mehr über Asset-Metadaten in [!DNL Experience Manager Assets] und lernen Sie die verschiedenen Bearbeitungsmöglichkeiten kennen.
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: 464a97ce-da3e-47b5-9879-fafaf2f2378c
source-git-commit: bc3c054e781789aa2a2b94f77b0616caec15e2ff
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 69%

---

# Anleitung zum Bearbeiten oder Hinzufügen von Metadaten {#how-to-edit-or-add-metadata}

Metadaten sind zusätzliche Informationen zum Asset, die durchsucht werden können. Beim Hochladen eines Bildes werden sie automatisch extrahiert. Sie können die vorhandenen Metadaten bearbeiten oder vorhandenen Feldern neue Metadateneigenschaften hinzufügen (etwa wenn ein Metadatenfeld leer ist).

Da Unternehmen gesteuertes und zuverlässiges Metadatenvokabular benötigen, lässt [!DNL Experience Manager Assets] das Adhoc-Hinzufügen von neuen Metadateneigenschaften nicht zu. Autoren und Autorinnen können zwar keine neuen Metadatenfelder für Assets hinzufügen, Entwickler oder Entwicklerinnen können dies jedoch tun. Siehe [Erstellen neuer Metadateneigenschaften für Assets](meta-edit.md#editing-metadata-schema).

## Bearbeiten von Metadaten für ein Asset {#editing-metadata-for-an-asset}

So bearbeiten Sie Metadaten:

1. Führen Sie einen der folgenden Schritte aus:

   * Wählen Sie in der Assets-Benutzeroberfläche das Asset aus und wählen Sie die **[!UICONTROL Eigenschaften anzeigen]** in der Symbolleiste.
   * Wählen Sie die Schnellaktion **[!UICONTROL Eigenschaften anzeigen]** aus der Miniatur des Assets aus.
   * Wählen Sie auf der Asset-Seite **[!UICONTROL Eigenschaften anzeigen]** aus der Symbolleiste.

   Auf der Asset-Seite werden die Metadaten des Assets angezeigt. Diese Metadaten wurden beim Hochladen (Aufnehmen) in Adobe Experience Manager Assets automatisch extrahiert.

1. Nehmen Sie die gewünschten Änderungen an den Metadaten auf den verschiedenen Registerkarten vor und wählen Sie nach Abschluss **[!UICONTROL Speichern]** aus der Symbolleiste, um Ihre Änderungen zu speichern. Auswählen **[!UICONTROL Schließen]** , um zur Assets-Web-Oberfläche zurückzukehren.

   >[!NOTE]
   >
   >Ein leeres Textfeld gibt an, dass kein Metadatenset vorhanden ist. Sie können einen Wert in das Feld eingeben und speichern, um diese Metadateneigenschaft hinzuzufügen.

Alle Änderungen an den Metadaten eines Assets werden als Teil der XMP-Daten in die ursprüngliche Binärdatei zurückgeschrieben. Dies geschieht über den Writeback-Workflow der Adobe Experience Manager-Metadaten. Änderungen an den vorhandenen Eigenschaften (z. B. `dc:title`) überschrieben und neu erstellte Eigenschaften (einschließlich benutzerdefinierter Eigenschaften wie `cq:tags`) werden zusammen mit dem Schema hinzugefügt.

<!-- XMP write-back is supported and enabled for the platforms and file formats described in technical requirements. -->

## Bearbeiten von Metadatenschemata {#editing-metadata-schema}

Weitere Informationen zur Bearbeitung von Metadatenschemata finden Sie unter [Bearbeiten von Metadaten-Schemaformularen](metadata-schemas.md#edit-metadata-schema-forms).

## Registrieren eines anwenderdefinierten Namespace in Experience Manager {#registering-a-custom-namespace-within-aem}

Sie können eigene Namespaces in Adobe Experience Manager hinzufügen. Es gibt vordefinierte Namespaces wie cq, jcr und sling. Sie können aber auch einen Namespace für Ihre Repository-Metadaten und die XML-Verarbeitung hinzufügen.

1. Wechseln Sie zur Seite für die Verwaltung des Knotentyps *https://&lt;Host>:&lt;Port>/crx/explorer/nodetypes/index.jsp*.
1. Auswählen **[!UICONTROL Namespaces]** oben auf der Seite. Die Seite zur Namespace-Verwaltung wird in einem Fenster angezeigt.

1. Um einen Namespace hinzuzufügen, wählen Sie **[!UICONTROL Neu]** unten.
1. Geben Sie einen benutzerdefinierten Namespace in der XML-Namespace-Konvention an (geben Sie die ID in Form eines URI und ein verknüpftes Präfix für die ID an) und wählen Sie **[!UICONTROL Speichern]**.

**Siehe auch**

* [Assets übersetzen](translate-assets.md)
* [Assets-HTTP-API](mac-api-assets.md)
* [Von AEM Assets unterstützte Dateiformate](file-format-support.md)
* [Suchen von Assets](search-assets.md)
* [Connected Assets](use-assets-across-connected-assets-instances.md)
* [Asset-Berichte](asset-reports.md)
* [Metadatenschemata](metadata-schemas.md)
* [Herunterladen von Assets](download-assets-from-aem.md)
* [Verwalten von Metadaten](manage-metadata.md)
* [Suchfacetten](search-facets.md)
* [Verwalten von Sammlungen](manage-collections.md)
* [Massenimport von Metadaten](metadata-import-export.md)
