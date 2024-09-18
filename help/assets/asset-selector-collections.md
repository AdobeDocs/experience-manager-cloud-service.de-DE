---
title: Asset-Selektor für [!DNL Adobe Experience Manager] als ein [!DNL Cloud Service]
description: Verwenden Sie den Asset-Selektor, um die Metadaten und Ausgabeformate von Assets in Ihrer Applikation zu suchen, zu finden und abzurufen.
role: Admin,User
source-git-commit: 63174176c944195ed21e481264e0a50062fd34f3
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 15%

---


# Asset-Selektor-Sammlungen {#asset-selector-collections}

Eine Sammlung ist ein Satz von Assets, Ordnern oder anderen Sammlungen in der Asset-Auswahl. Anhand von Sammlungen können Assets von mehreren Benutzern gemeinsam verwendet werden. Im Gegensatz zu Ordnern kann eine Sammlung Assets von verschiedenen Speicherorten enthalten.

Die Micro Front-End-Sammlungen in der Asset-Auswahl sind im schreibgeschützten Modus standardmäßig verfügbar. Ruft Assets und Sammlungen direkt aus dem [!DNL Experience Manager Assets]-Repository ab, auf das Sie Zugriff haben.

>[!NOTE]
>
>Stellen Sie sicher, dass Sie über Berechtigungen für den Zugriff auf eine [!DNL Experience Manager Assets] [imsOrg](/help/assets/asset-selector-properties.md) und Sammlungen verfügen.

Die Micro Front-End-Sammlungen in der Asset-Auswahl sind im schreibgeschützten Modus standardmäßig verfügbar. Ruft Assets und Sammlungen direkt aus dem Experience Manager Assets-Repository ab, auf das Sie Zugriff haben, und übernimmt die Eigenschaften öffentlicher und privater Ordner aus Ihrem Experience Manager Assets-Repository. Weitere Informationen zum Erstellen einer öffentlichen oder privaten Sammlung finden Sie in der Assets-Ansicht](/help/assets/manage-collections-assets-view.md#create-collection).[

Sie können Sammlungen in der Asset-Auswahl sowohl in der Schienenansicht als auch in der modalen Ansicht anzeigen.

![Sammlungen in der Schienenansicht](assets/collections-rail-modal-view.png)

<!--
Additionally, you can [customize](/help/assets/asset-selector-customization.md) the `featureSet` property to enable or disable collections in Asset Selector. See [enable or disable Collections tab](#enable-disable-collections-tab).-->

Darüber hinaus können Sie die Auswahl von Assets auf der Registerkarte Sammlungen anpassen. Dazu können Sie sie mit `handleSelection` anpassen. Siehe [ Umgang mit der Auswahl von Assets mithilfe des Objektschemas](/help/assets/asset-selector-customization.md#handling-selection).

## Anzeigen von Sammlungen {#view-collections}

Mit der Asset-Auswahl können Sie Sammlungen entweder in einer ![Listenansicht](assets/do-not-localize/list-view.png) oder in einer ![Rasteransicht](assets/do-not-localize/grid-view.png) Rasteransicht anzeigen. Siehe [Ansichtstypen in der Asset-Auswahl](overview-asset-selector.md#types-of-view).

## Ziehen und Ablegen von Assets in die Sammlung {#collection-drag-and-drop}

Sie können ein Asset per Drag-and-Drop direkt aus der Ansicht [!DNL Assets as a Cloud Service] in der Autorenumgebung in Sammlungen ziehen. Ziehen Sie dazu das Asset aus der Registerkarte Assets in den Arbeitsbereich Sammlungen der Asset-Auswahl-Anwendung, um Rich-Apps zu erstellen.

>[!NOTE]
>
>* Das Ziehen und Ablegen eines Assets ist nur in der Schienenansicht möglich.
>* Sie können Dateien nur (Assets) und nicht die Ordner per Drag-and-Drop verschieben.

Andererseits können Sie auch [das Ziehen und Ablegen von Assets in die Sammlungen](asset-selector-customization.md#enable-disable-drag-and-drop) direkt aktivieren oder deaktivieren.

## Deaktivieren der Asset-Auswahl in Sammlungen {#disable-selection-collection}

Die Funktion „disableSelection“ wird verwendet, um die Möglichkeit zur Auswahl der Assets oder Ordner auszublenden bzw. zu deaktivieren. Dabei wird das Kontrollkästchen „Auswählen“ auf der Karte oder im Asset ausgeblendet und eine Auswahl verhindert. Siehe [Auswahl deaktivieren](/help/assets/asset-selector-customization.md#disable-selection).

## Registerkarte &quot;Sammlungen&quot;aktivieren oder deaktivieren {#enable-disable-collections-tab}

Mit der Asset-Auswahl können Sie die Komponenten entsprechend den Anforderungen und der Benutzerfreundlichkeit anpassen. Um die Registerkarte &quot;Sammlungen&quot;in der Asset-Auswahl zu aktivieren oder zu deaktivieren, können Sie die Eigenschaft &quot;`featureSet`&quot;wie folgt verwenden:

* **Registerkarte &quot;Sammlungen aktivieren&quot;:** Um die Registerkarte &quot;Sammlungen&quot;zu aktivieren, müssen Sie dem Array den Wert `collections` als angeben. Standardmäßig ist die Registerkarte Sammlungen für alle Benutzer standardmäßig aktiviert. Zum Beispiel: `featureSet:["collections"]`
* **Registerkarte &quot;Sammlungen deaktivieren&quot;:** Um die Registerkarte &quot;Sammlungen&quot;zu deaktivieren, müssen Sie ein leeres Array als Wert angeben. Zum Beispiel: `featureSet:[ ]`

>[!MORELIKETHIS]
>
>* [Anpassung der Asset-Auswahl](/help/assets/asset-selector-customization.md)
>* [Integrieren der Asset-Auswahl in verschiedene Anwendungen](/help/assets/integrate-asset-selector.md)
>* [Eigenschaften des Asset-Wählers](/help/assets/asset-selector-properties.md)

