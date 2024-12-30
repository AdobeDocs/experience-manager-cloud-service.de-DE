---
title: Anleitung zum Bearbeiten oder Hinzufügen von Metadaten
description: Erfahren Sie mehr über Asset-Metadaten in [!DNL Experience Manager Assets] und lernen Sie die verschiedenen Bearbeitungsmöglichkeiten kennen.
contentOwner: AG
feature: Metadata
role: User, Admin
exl-id: 464a97ce-da3e-47b5-9879-fafaf2f2378c
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 100%

---

# Anleitung zum Bearbeiten oder Hinzufügen von Metadaten {#how-to-edit-or-add-metadata}

| [Best Practices für die Suche](/help/assets/search-best-practices.md) | [Best Practices für Metadaten](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [Dynamic Media mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md) | [Entwicklerdokumentation zu AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

Metadaten sind zusätzliche Informationen zum Asset, die durchsucht werden können. Beim Hochladen eines Bildes werden sie automatisch extrahiert. Sie können die vorhandenen Metadaten bearbeiten oder vorhandenen Feldern neue Metadateneigenschaften hinzufügen (etwa wenn ein Metadatenfeld leer ist).

Da Unternehmen gesteuertes und zuverlässiges Metadatenvokabular benötigen, lässt [!DNL Experience Manager Assets] das Hinzufügen von neuen Metadateneigenschaften nach Bedarf nicht zu. Autoren und Autorinnen können zwar keine neuen Metadatenfelder für Assets hinzufügen, Entwickler oder Entwicklerinnen können dies jedoch tun. Siehe [Erstellen neuer Metadateneigenschaften für Assets](meta-edit.md#editing-metadata-schema).

## Bearbeiten von Metadaten für ein Asset {#editing-metadata-for-an-asset}

So bearbeiten Sie Metadaten:

1. Führen Sie einen der folgenden Schritte aus:

   * Wählen Sie in der Assets-Benutzeroberfläche das Asset und anschließend in der Symbolleiste das Symbol **[!UICONTROL Eigenschaften anzeigen]** aus.
   * Wählen Sie über die Miniaturansicht des Assets die Schnellaktion **[!UICONTROL Eigenschaften anzeigen]** aus.
   * Wählen Sie auf der Asset-Seite das Symbol **[!UICONTROL Eigenschaften anzeigen]** in der Symbolleiste aus.

   Auf der Asset-Seite werden die Metadaten des Assets angezeigt. Diese Metadaten wurden beim Hochladen (Aufnehmen) in Adobe Experience Manager Assets automatisch extrahiert.

1. Nehmen Sie auf den verschiedenen Registerkarten bei Bedarf Änderungen an den Metadaten vor. Wählen Sie anschließend in der Symbolleiste die Option **[!UICONTROL Speichern]** aus, um die Änderungen zu speichern. Wählen Sie **[!UICONTROL Schließen]** aus, um zur Assets-Web-Oberfläche zurückzukehren.

   >[!NOTE]
   >
   >Ein leeres Textfeld gibt an, dass kein Metadatenset vorhanden ist. Sie können einen Wert in das Feld eingeben und speichern, um diese Metadateneigenschaft hinzuzufügen.

Alle Änderungen an den Metadaten eines Assets werden als Teil der XMP-Daten in die ursprüngliche Binärdatei zurückgeschrieben. Dies geschieht über den Writeback-Workflow der Adobe Experience Manager-Metadaten. Änderungen an den vorhandenen Eigenschaften (z. B. `dc:title`) werden überschrieben und erstellte Eigenschaften (einschließlich von benutzerdefinierten Eigenschaften wie `cq:tags`) werden zusammen mit dem Schema hinzugefügt.

<!-- XMP write-back is supported and enabled for the platforms and file formats described in technical requirements. -->

## Bearbeiten von Metadatenschemata {#editing-metadata-schema}

Weitere Informationen zur Bearbeitung von Metadatenschemata finden Sie unter [Bearbeiten von Metadaten-Schemaformularen](metadata-schemas.md#edit-metadata-schema-forms).

## Registrieren eines anwenderdefinierten Namespace in Experience Manager {#registering-a-custom-namespace-within-aem}

Sie können eigene Namespaces in Adobe Experience Manager hinzufügen. Es gibt vordefinierte Namespaces wie cq, jcr und sling. Sie können aber auch einen Namespace für Ihre Repository-Metadaten und die XML-Verarbeitung hinzufügen.

1. Wechseln Sie zur Seite für die Verwaltung des Knotentyps *https://&lt;Host>:&lt;Port>/crx/explorer/nodetypes/index.jsp*.
1. Wählen Sie am oberen Rand der Seite **[!UICONTROL Namespaces]** aus. Die Seite zur Namespace-Verwaltung wird in einem Fenster angezeigt.

1. Wählen Sie zum Hinzufügen eines Namespace am unteren Rand auf **[!UICONTROL Neu]** aus.
1. Geben Sie einen benutzerdefinierten Namespace gemäß der XML-Namespace-Konvention ein (ID in Form einer URI und verknüpftes Präfix für die ID). Wählen Sie **[!UICONTROL Speichern]** aus.

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
* [Veröffentlichen von Assets in AEM und Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)
