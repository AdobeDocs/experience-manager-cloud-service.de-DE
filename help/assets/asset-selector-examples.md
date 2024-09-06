---
title: Asset-Selektor für [!DNL Adobe Experience Manager] als ein [!DNL Cloud Service]
description: Beispiele zur Verwendung des Asset-Selektors zur Anpassung gemäß Anforderungen.
role: Admin, User
source-git-commit: fb1350c91468f9c448e34b66dc938fa3b5a3e9a9
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 90%

---


# Beispiele zur Verwendung der Asset-Selektor-Eigenschaften {#usage-examples}

Sie können die Asset-Selektor-[Eigenschaften](#asset-selector-properties.md) in der Datei `index.html` definieren, um die Anzeige des Asset-Selektors in Ihrer Applikation anzupassen.

## Beispiel 1: Asset-Selektor in der Leistenansicht

![rail-view-example](assets/rail-view-example-vanilla.png)

Wenn der Wert `rail` des Asset-Wählers auf `false` gesetzt ist oder in den Eigenschaften nicht erwähnt wird, wird der Asset-Wähler standardmäßig in der Modal-Ansicht angezeigt. Die Eigenschaft `acvConfig` ermöglicht einige tief greifende Konfigurationen wie etwa Drag-and-Drop. Lesen Sie [Aktivieren oder Deaktivieren von Drag-and-Drop](asset-selector-customization.md#enable-disable-drag-and-drop), um zu erfahren, wie die Eigenschaft `acvConfig` verwendet wird.

<!--
### Example 2: Use selectedAssets property in addition to the path property

Use the `path` property to define the folder name that displays automatically when the Asset Selector is rendered. In addition, use the `selectedAssets` property to define the IDs for the assets that you need to select within the folder. Moreover, when you want to display assets that are pre-defined within the folder, you can use selectedAssets property.

   ![selected-assets-example](assets/selected-assets-example-vanilla.png)
-->

## Beispiel 2: Metadaten-Popover

Verwenden Sie verschiedene Eigenschaften, um Metadaten eines Assets zu definieren, das Sie mit einem Informationssymbol anzeigen möchten. Das Info-Popover bietet die Sammlung von Informationen über das Asset oder den Ordner, einschließlich Titel, Abmessungen, Änderungsdatum, Speicherort und Beschreibung eines Assets. Im folgenden Beispiel werden verschiedene Eigenschaften verwendet, um Metadaten eines Assets anzuzeigen, z. B. gibt die Eigenschaft `repo:path` den Speicherort eines Assets an. <!--`repo` represents the repository from where the asset is showing, whereas, `path` represents the route from where the asset or folder is rendered.-->

![metadata-popover-example](assets/metadata-popover.png)

## Beispiel 3: Benutzerdefinierte Filtereigenschaft in der Leistenansicht

Zusätzlich zur Facettensuche können Sie mit dem Asset-Selektor verschiedene Attribute anpassen, um Ihre Suche von [!DNL Adobe Experience Manager] als eine [!DNL Cloud Service]-Anwendung zu verfeinern. Fügen Sie den folgenden Code hinzu, um benutzerdefinierte Suchfilter zu Ihrer Anwendung hinzuzufügen. Im folgenden Beispiel ist die `Type Filter`-Suche, die den Asset-Typ nach Bildern, Dokumenten oder Videos filtert, oder der Filtertyp, den Sie für die Suche hinzugefügt haben.

![custom-filter-example-vanilla](assets/custom-filter-example-vanilla.png)

<!--

## Customization after integrating Asset Selector 

### Custom metadata

Assets display panel shows the out of the box metadata that can be displayed in the info of the asset. In addition to this, [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] application allows configuration of the asset selector by adding custom metadata that is shown in info panel of the asset.
-->


>[!MORELIKETHIS]
>
>* [Anpassung der Asset-Auswahl](/help/assets/asset-selector-customization.md)
>* [Eigenschaften des Asset-Wählers](/help/assets/asset-selector-properties.md)
>* [Integrieren der APIs zum Öffnen dynamischer Medien in der Asset-Auswahl](/help/assets/integrate-asset-selector-dynamic-media-open-api.md)

