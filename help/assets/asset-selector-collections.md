---
title: Sammlungen im Asset-Wähler
description: Arbeiten mit Sammlungen im Asset-Wähler
role: Admin,User
exl-id: 1687e7d5-eb7e-4eb7-8747-e5dc6afacd5b
source-git-commit: 9c1104f449dc2ec625926925ef8c95976f1faf3d
workflow-type: ht
source-wordcount: '449'
ht-degree: 100%

---

# Sammlungen im Asset-Wähler {#asset-selector-collections}

Eine Sammlung ist ein Satz von Assets, Ordnern oder sonstigen Sammlungen innerhalb des Asset-Wählers. Anhand von Sammlungen können Assets von mehreren Benutzern gemeinsam verwendet werden. Im Gegensatz zu Ordnern kann eine Sammlung Assets von verschiedenen Speicherorten enthalten.

Die Mikro-Frontend-Sammlungen im Asset-Wähler sind im schreibgeschützten Modus standardmäßig verfügbar. Assets und Sammlungen werden direkt aus dem [!DNL Experience Manager Assets]-Repository abgerufen, auf das Sie Zugriff haben.

>[!NOTE]
>
>Stellen Sie sicher, dass Sie über die Berechtigungen für den Zugriff auf eine [!DNL Experience Manager Assets] [imsOrg](/help/assets/asset-selector-properties.md) und auf Sammlungen verfügen.

Die Mikro-Frontend-Sammlungen im Asset-Wähler sind im schreibgeschützten Modus standardmäßig verfügbar. Assets und Sammlungen werden direkt aus dem Experience Manager Assets-Repository abgerufen, auf das Sie Zugriff haben, wobei die Eigenschaften öffentlicher und privater Ordner aus Ihrem Experience Manager Assets-Repository übernommen werden. Lesen Sie mehr über das [Erstellen einer öffentlichen oder privaten Sammlung in der Assets-Ansicht](/help/assets/manage-collections-assets-view.md#create-collection).

Sie können Sammlungen im Asset-Wähler sowohl in der Leistenansicht als auch in der modalen Ansicht anzeigen.

![Sammlungen in der Leistenansicht](assets/collections-rail-modal-view.png)

<!--
Additionally, you can [customize](/help/assets/asset-selector-customization.md) the `featureSet` property to enable or disable collections in Asset Selector. See [enable or disable Collections tab](#enable-disable-collections-tab).-->

Darüber hinaus können Sie die Auswahl von Assets auf der Registerkarte „Sammlungen“ anpassen. Zum Anpassen können Sie `handleSelection` verwenden. Weitere Informationen finden Sie unter [Umgang mit der Auswahl von Assets mithilfe des Objektschemas](/help/assets/asset-selector-customization.md#handling-selection).

## Anzeigen von Sammlungen {#view-collections}

Mit dem Asset-Wähler können Sie Sammlungen entweder in einer ![Listenansicht](assets/do-not-localize/list-view.png) Listenansicht oder in einer ![Rasteransicht](assets/do-not-localize/grid-view.png) Rasteransicht anzeigen. Weitere Informationen finden Sie unter [Ansichtstypen im Asset-Wähler](overview-asset-selector.md#types-of-view).

## Ziehen und Ablegen von Assets in eine Sammlung {#collection-drag-and-drop}

Sie können ein Asset per Drag-and-Drop direkt aus der [!DNL Assets as a Cloud Service]-Ansicht in der Autorenumgebung in Sammlungen ziehen. Ziehen Sie dazu das Asset von der Registerkarte „Assets“ in den Arbeitsbereich „Sammlungen“ der Asset-Wähler-Anwendung, um umfangreiche Anwendungen zu erstellen.

>[!NOTE]
>
>* Das Ziehen und Ablegen eines Assets ist nur in der Leistenansicht möglich.
>* Sie können nur Dateien (Assets) und nicht die Ordner per Drag-and-Drop verschieben.

Alternativ können Sie das [Ziehen und Ablegen von Assets auch direkt in den Sammlungen aktivieren oder deaktivieren](asset-selector-customization.md#enable-disable-drag-and-drop).

## Deaktivieren der Auswahl von Assets in Sammlungen {#disable-selection-collection}

Die Funktion „disableSelection“ wird verwendet, um die Möglichkeit zur Auswahl der Assets oder Ordner auszublenden bzw. zu deaktivieren. Dabei wird das Kontrollkästchen „Auswählen“ auf der Karte oder im Asset ausgeblendet und eine Auswahl verhindert. Weitere Informationen finden Sie unter [Deaktivieren der Auswahl](/help/assets/asset-selector-customization.md#disable-selection).

## Aktivieren und Deaktivieren der Registerkarte „Sammlungen“ {#enable-disable-collections-tab}

Mit dem Asset-Wähler können Sie die Komponenten entsprechend den Anforderungen und der Benutzerfreundlichkeit anpassen. Sie können die Registerkarte „Sammlungen“ im Asset-Wähler wie folgt mit der Eigenschaft `featureSet` aktivieren oder deaktivieren:

* **Registerkarte „Sammlungen“ aktivieren:** Um die Registerkarte „Sammlungen“ zu aktivieren, müssen Sie `collections` als Wert für das Array angeben. Die Registerkarte „Sammlungen“ ist standardmäßig für alle Benutzenden aktiviert. Zum Beispiel: `featureSet:["collections"]`
* **Registerkarte „Sammlungen“ deaktivieren:** Um die Registerkarte „Sammlungen“ zu deaktivieren, müssen Sie ein leeres Array als Wert angeben. Zum Beispiel: `featureSet:[ ]`

>[!MORELIKETHIS]
>
>* [Anpassungen des Asset-Wählers](/help/assets/asset-selector-customization.md)
>* [Integrieren des Asset-Wählers in verschiedene Anwendungen](/help/assets/integrate-asset-selector.md)
>* [Eigenschaften des Asset-Wählers](/help/assets/asset-selector-properties.md)
