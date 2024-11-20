---
title: Asset-Wähler für [!DNL Adobe Experience Manager] as a [!DNL Cloud Service]
description: Beispiele zur Verwendung des Asset-Wählers für Anpassungen gemäß den Anforderungen.
role: Admin, User
exl-id: 7a393a96-f2a2-4a25-922c-577271cafc57
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: ht
source-wordcount: '275'
ht-degree: 100%

---

# Beispiele zur Verwendung der Asset-Selektor-Eigenschaften {#usage-examples}

| [Best Practices für die Suche](/help/assets/search-best-practices.md) | [Best Practices für Metadaten](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [Dynamic Media mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md) | [Entwicklerdokumentation zu AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

Sie können die Asset-Wähler-[Eigenschaften](/help/assets/asset-selector-properties.md) in der Datei **index.html** definieren, um die Anzeige des Asset-Wählers in Ihrer Anwendung anzupassen.

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
>* [Anpassungen des Asset-Wählers](/help/assets/asset-selector-customization.md)
>* [Hochladen des Asset-Wählers](/help/assets/asset-selector-upload.md)
>* [Eigenschaften des Asset-Wählers](/help/assets/asset-selector-properties.md)
>* [Integrieren des Asset-Wählers in Dynamic Media mit OpenAPI-Funktionen](/help/assets/integrate-asset-selector-dynamic-media-open-api.md)
