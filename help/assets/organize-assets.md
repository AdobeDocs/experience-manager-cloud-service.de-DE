---
title: Digitale Assets organisieren
description: Organisieren Sie Ihre digitalen Assets, Bilder, Dateien, Ordner usw. mithilfe von Experience Manager.
contentOwner: AG
feature: Asset Management, Search
role: User
exl-id: 6b3ce076-2dd9-47f6-9b68-4fa52bfedd42
source-git-commit: 843d6660fc2a2048d138601b4b74ee9f2faa54c9
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 5%

---

# Digitale Assets organisieren {#organize-digital-assets}

Alle digitalen Assets, Metadaten und Inhalte von Microsoft® Office- und PDF-Dokumenten werden extrahiert und durchsuchbar gemacht. Die Suche ermöglicht ein ausgefeiltes Filtern von Assets und respektiert vollständig die entsprechenden Berechtigungen. Metadaten werden in „Metadaten in Digital Asset Management“ ausführlich behandelt.

[!DNL Experience Manager Assets] unterstützt mehrere Möglichkeiten der Organisation von Inhalten. Sie können sie hierarchisch mithilfe von Ordnern organisieren oder ungeordnet und ad hoc organisieren, z. B. Tags. Benutzer können Tags im DAM-Asset-Editor bearbeiten, in dem Unter-Assets, Ausgabedarstellungen und Metadaten angezeigt werden.

<!-- Commenting to pull down the existing content before applying changes wrt CQDOC-15930
## Create folders {#create-folders}

When organizing a collection of assets, for example, all *Nature* images, you can create folders to keep them together. You can use folders to categorize and organize your assets. [!DNL Assets] does not require you to organize assets in folders to work better.

>[!NOTE]
>
>Sharing an Assets folder (in Marketing Cloud) of the type `sling:OrderedFolder`, is not supported. If you want to share a folder, do not select Ordered when creating a folder.

1. Navigate to the place in your digital assets folder where you want to create a new folder.
1. In the menu, click **[!UICONTROL Create]**. Select **[!UICONTROL New Folder]**.
1. In the **[!UICONTROL Title]** field, provide a folder name. By default, DAM uses the title that you provided as the folder name. Once the folder is created, you can override the default and specify another folder name.
1. Click **[!UICONTROL Create]**. Your folder is displayed in the digital assets folder.

## Add CUG properties to folders {#add-cug-properties-to-folders}

You can limit who can access certain folders in Assets by making the folder part of a closed user group (CUG). To make a folder part of a CUG:

1. In Assets, right-click the folder you want to add closed user group properties for and select **Properties**.  
1. Click the **CUG** tab.
1. Select the **Enabled** check box to make the folder and its assets available only to a closed user group.  
1. Browse to the login page, if there is one, to add that information. Add admitted groups by clicking **Add item**. If necessary, add the realm. Click **OK** to save your changes.

## Use tags to organize assets {#use-tags-to-organize-assets}

You can use folders or tags or both to organize assets. Adding tags to assets makes them more easy to retrieve during a search. To add tags to an asset, follow these steps:

1. In the Digital Asset Manager, double-click the asset to open it.
1. In the **Tags** area, open the menu to reveal the available tags. Select tags as appropriate. To delete a tag, hover the pointer over the tag and click `X` to delete it.
1. Click **Save** to save any tags you added.

Date24/08/2021
-->

## Organisieren von Assets in Ordnern {#organize-using-folders}

Die einfachste Möglichkeit zum Organisieren von Assets besteht darin, die Assets in Ordnern zu speichern. Dies entspricht dem Organisieren von Dateien in Ordnern in Ihrem lokalen Dateisystem. Weitere Informationen zum Erstellen und Verwalten von Ordnern finden Sie unter [Verwalten von Assets](manage-digital-assets.md). Wie Sie Dateien und Ordner benennen, wie Sie Unterordner anordnen und wie Sie die Dateien in diesen Ordnern verarbeiten, kann erhebliche Auswirkungen auf die Verarbeitung dieser Assets haben. Durch die Verwendung konsistenter und angemessener Strategien für die Datei- und Ordnernamen sowie guter Metadatenpraktiken können Sie das gesamte digitale Asset-Repository optimal nutzen.

* Normalerweise wächst Ihr Digital-Asset-Repository immer. Daher ist es wichtig, die Metadatenverwendung, die Ordnerstruktur und die Dateibenennung frühzeitig im Erstellungszyklus des Inhalts zu formalisieren.
* Verwenden Sie Ordner, um eine konsistente Speicherstruktur für die digitalen Assets durchzusetzen. Diese Konsistenz hilft Ihrem Prozess und verwaltet Ihre Assets besser. Beispielsweise können Assets, die in den folgenden Ordnertypen platziert werden, Ihnen dabei helfen, Ihre Assets zu trennen:

   * **Entwicklungsordner**: enthält digitale Assets, an denen Sie derzeit arbeiten.
   * **Client-Ordner**: enthält digitale Assets basierend auf Kunden oder Projektnamen.
   * **Primäre Ordner**: enthält digitale Quell-Assets in Originalform.
   * **Ausgabeformatordner**: enthält Ausgabeformate und Kopien der digitalen Quell-Assets in Originalform.
   * **Dateigrößenordner**: enthält digitale Assets basierend auf kleinen, mittleren oder großen Dateigrößen.
   * **Staging-Ordner**: enthält digitale Assets, die zur Veröffentlichung auf Ihrer Website bereit sind.
   * **MIME-Typ-Ordner**: enthält digitale Assets, die für MIME-Typen spezifisch sind, z. B. Bilder, Dokumente und Multimedia.
   * **Archivordner**: enthält veraltete digitale Assets.
   * **Datumsbasierte Ordner**: digitale Assets basierend auf einem Erstellungsdatum oder dem Datum der letzten Änderung enthält.

* Erstellen Sie einen Ordner mit Ordnern, die sich wahrscheinlich nicht ändern werden, damit Anpassungen oder Automatisierungen weiterhin funktionieren. Beispielsweise funktionieren die zugewiesenen Verarbeitungsprofile weiterhin.
* Wenn ein Asset bereits veröffentlicht ist, verwenden Sie [!DNL Experience Manager], um das Asset in einen anderen Ordner zu verschieben, und veröffentlichen Sie es erneut von seinem neuen Speicherort aus. Der ursprünglich veröffentlichte Asset-Speicherort ist weiterhin zusammen mit dem neu veröffentlichten Asset verfügbar. Das ursprünglich veröffentlichte Asset ist jedoch *lost* bis [!DNL Experience Manager] und kann nicht rückgängig gemacht werden. Daher empfiehlt es sich, zunächst die Veröffentlichung eines Assets rückgängig zu machen und es dann in einen anderen Ordner zu verschieben.

## Organisieren von Assets mit Tags {#use-tags-to-organize-assets}

Mithilfe von Tags als Metadaten können Sie mühelos Assets suchen, Sammlungen mithilfe der Suchergebnisse erstellen, das Suchangebot für einige Assets verbessern und KI-Algorithmen von Adobe Sensei zur Asset-Erkennung anwenden.

[!DNL Adobe Experience Manager Assets] verwendet einen selbstlernenden Algorithmus, um hochgradig beschreibende Tags zu erstellen, mit denen Sie das richtige Asset in nur wenigen Klicks finden können. Smart-Tagging nutzt Adobe Sensei, künstliche Intelligenz und maschinelles Lernen-Framework, das trainiert werden kann, um standardmäßige und geschäftsspezifische Tags zu erkennen und auf Bilder anzuwenden. Smart-Tags können auch Inhalte, einzelne Wörter oder Ausdrücke identifizieren und automatisch beschreibende Tags auf Assets anwenden

Weitere Informationen finden Sie in den folgenden Artikeln:

* [Bearbeiten von Asset-Metadaten](meta-edit.md)
* [Smart-Tags in Assets](smart-tags.md)

## Organisieren als Sammlungen {#organize-as-collections}

Mit Asset-Sammlungen in [!DNL Experience Manager Assets] können Sie die Möglichkeit optimieren, Assets zu erstellen, zu bearbeiten und zwischen Benutzern freizugeben. Erstellen Sie verschiedene Arten von Sammlungen basierend auf ihrer Verwendung, einschließlich Sammlungen, die eine statische Referenzliste von Assets, Ordnern und Sammlungen enthalten, und Sammlungen, die Assets basierend auf Suchkriterien abrufen. Sie können Sammlungen mit Assets aus verschiedenen Speicherorten erstellen und sie für mehrere Benutzer mit unterschiedlichen Zugriffs-, Anzeige- und Bearbeitungsberechtigungen freigeben.

Weitere Informationen finden Sie unter [Verwalten von Sammlungen](manage-collections.md)


## Verwenden von Profilen zum Organisieren von Assets {#organize-to-use-profiles}

Ein Verarbeitungsprofil enthält [!DNL Assets] Verarbeitungsbefehle, die für Assets gelten, die in vordefinierte Ordner hochgeladen werden. Profile werden verwendet, um die Verarbeitung von Inhalten eines Ordners oder von neu hochgeladenen Assets zu automatisieren. Sie können Profile verwenden, um Ihre Assets besser zu organisieren.

Durch die Standardisierung der Metadatennutzung, Dateibenennung und Ordnerstruktur wird sichergestellt, dass Sie bei einem wachsenden Pool digitaler Assets Verarbeitungsprofile präziser und konsistenter auf Ordner anwenden können.

>[!MORELIKETHIS]
>
>* [Asset-Microservices und Verarbeitungsprofile verwenden](asset-microservices-configure-and-use.md)
>* [Metadatenprofile](metadata-profiles.md)
>* [Videoprofile](/help/assets/dynamic-media/video-profiles.md)
>* [Dynamic Media-Bildprofile](/help/assets/dynamic-media/image-profiles.md)


