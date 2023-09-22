---
title: Farb-Tags für Bilder
description: Mit Adobe Experience Manager Assets können Sie zwischen Farben in einem Bild unterscheiden und diese automatisch als Tags anwenden. Sie können diese Tags dann verwenden, um Bilder zu suchen und zu filtern.
exl-id: 3afa949b-ea1b-4b8e-ac94-06566e2c7147
source-git-commit: 57d6b50ef5256bf6e8fce84100eed4690b77cb87
workflow-type: tm+mt
source-wordcount: '1220'
ht-degree: 67%

---

# Farb-Tags für Bilder {#color-tag-images}

![Farb-Tagging-Banner](assets/banner-image.png)

Adobe Experience Manager (AEM) Assets verwendet Adobe Sensei AI-Funktionen, um zwischen Farben in einem Bild zu unterscheiden und diese bei der Aufnahme automatisch als Tags anzuwenden. Diese Tags ermöglichen ein verbessertes Sucherlebnis, das auf der Bildfarbkomposition basiert.

Sie können festlegen, wie viele Farben innerhalb eines Bereichs von 1 bis 40 mit einem Bild versehen werden, damit Sie später anhand dieser Farben nach Bildern suchen können. Experience Manager Assets wendet die Tags auf Grundlage der Farbabdeckung eines Bildes an. Sie können auch das Anzeigeformat für ein Farb-Tag konfigurieren.

Die folgende Abbildung zeigt die Abfolge von Aufgaben zum Konfigurieren und Verwalten des Farb-Tagging für Bilder in Experience Manager Assets:

![Farb-Tagging](assets/color-tagging-dfd.gif)

## Unterstützte Dateiformate {#supported-file-formats-color-tags}

| Dateiformat | Erweiterung | MIME-Typ | Eingabe-Farbraum | Maximal unterstützte Größe der Quelldatei | Maximale unterstützte Dateigrößenauflösung |
|---|---|---|---|---|---|
| JPEG | .jpg und .jpeg | image/jpeg | sRGB | 15 GB | 20000 × 20000 Pixel |
| PNG | .png | image/png | sRGB | 15 GB | 20000 × 20000 Pixel |
| TIFF | .tif und .tiff | image/tiff | sRGB | 4 GB (begrenzt durch Formatspezifikationen) | 20000 × 20000 Pixel |
| PSD | .psd | image/vnd.adobe.photoshop | sRGB | 2 GB (begrenzt durch Formatspezifikationen) | 20000 × 20000 Pixel |
| GIF | .gif | image/gif | sRGB | 15 GB | 20000 × 20000 Pixel |
| BMP | .bmp | image/bmp | sRGB | 4 GB (begrenzt durch Formatspezifikationen) | 20000 × 20000 Pixel |

## Verwalten von Farb-Tagging-Eigenschaften {#manage-color-tagging-properties}

So verwalten Sie die Farb-Tagging-Eigenschaften für Bilder:

1. Navigieren Sie zu **[!UICONTROL Tools > Assets > Farb-Tagging]**.

   ![Farb-Tagging-Eigenschaften](assets/color-tag-settings.png)

1. Geben Sie ein Anzeigeformat für das Farb-Tag im Feld **[!UICONTROL Anzeigeformat]** an. Zu den möglichen Optionen gehören der Farbname, das RGB- oder HEX-Format.

1. Geben Sie die Anzahl der Farben an, die Sie für die Bilder taggen möchten, im **[!UICONTROL Limit]** -Feld. Diese Farben werden angezeigt, wenn Sie die Eigenschaften für ein Bild anzeigen. In diesem Feld können Sie eine Zahl zwischen 1 und 40 definieren. Der Standardwert für dieses Feld ist zehn Farben.

1. Geben Sie im Feld **[!UICONTROL Schwellenwert für Abdeckung/Dominanz %]** den minimalen Farbabdeckungsprozentsatz an, um ein Farb-Tag in die Suchergebnisse einzufügen. Wenn die Abdeckung der roten Farbe in einem Bild beispielsweise 10 Prozent beträgt und Sie in diesem Feld neun Prozent definieren, wird das Bild bei der Suche nach Bildern mit roter Farbe einbezogen. Wenn die rote Farbabdeckung in einem Bild jedoch 10 % beträgt und Sie in diesem Feld 11 % definieren, wird das Bild bei der Suche nach Bildern mit roter Farbe nicht einbezogen.

   In diesem Feld können Sie eine beliebige Zahl zwischen 5 und 100 angeben. Der Standardwert ist 11.

   >[!NOTE]
   >
   >Adobe empfiehlt die Verwendung eines Werts, der dem Standardwert in diesem Feld nahe kommt. Wenn Sie einen für dieses Feld festgelegten Wert mit hoher Zahl festlegen (z. B. größer als 25), werden möglicherweise nur wenige Suchergebnisse zurückgegeben. Auf ähnliche Weise kann die Festlegung eines niedrigen Zahlenwerts (z. B. unter 6) zu vielen Suchergebnissen führen, was möglicherweise nicht nützlich ist.

1. Klicken Sie auf **[!UICONTROL Speichern]**.


   >[!VIDEO](https://video.tv.adobe.com/v/340108)


### Deaktivieren des Farb-Taggings {#disable-color-tagging}

Das Farb-Tagging für Bilder ist standardmäßig aktiviert. Sie können das Farb-Tagging auf Ordnerebene deaktivieren. Alle untergeordneten Ordner übernehmen die Farb-Tagging-Eigenschaften des übergeordneten Ordners.

So deaktivieren Sie das Farb-Tagging auf Ordnerebene:

1. Navigieren Sie zu **[!UICONTROL Adobe Experience Manager > Assets > Dateien]**.

1. Wählen Sie den Ordner aus und klicken Sie dann auf **[!UICONTROL Eigenschaften]**.

1. Navigieren Sie auf der Registerkarte **[!UICONTROL Asset-Verarbeitung]** zum Ordner **[!UICONTROL Farb-Tags für Bilder]**. Wählen Sie einen der folgenden Werte aus der Dropdown-Liste aus:

   * Vererbt – Der Ordner übernimmt die Optionen zum Aktivieren oder Deaktivieren vom übergeordneten Ordner.

   * Aktivieren – Aktiviert das Farb-Tagging für den ausgewählten Ordner.

   * Deaktivieren – Deaktiviert das Farb-Tagging für den ausgewählten Ordner.

   ![Farb-Tagging-Einstellungen](assets/color-tags-folder.png)

## Konfigurieren des Metadatenschemas zum Hinzufügen der Smart-Color-Tags-Komponente {#configure-metadata-schema}

Metadaten-Schemata enthalten bestimmte Felder für bestimmte einzutragende Informationen. Es enthält auch Layout-Informationen, um Metadatenfelder benutzerfreundlich anzuzeigen. Zu den Metadaten-Eigenschaften zählen u. a. Titel, Beschreibung, MIME-Typen, Tags usw. Mit dem Editor für [!UICONTROL Metadatenschema-Formulare] können Sie vorhandene Schemata ändern oder benutzerdefinierte Metadatenschemata hinzufügen.

>[!NOTE]
>
>Das Feld Smart Color Tag ist im Standard-Metadatenschema verfügbar. Wenn Sie ein benutzerdefiniertes Metadatenschema verwenden, konfigurieren Sie Ihr Schema so, dass ein Smart-Color-Tag-Feld hinzugefügt wird.

So fügen Sie die Smart-Farb-Tags-Komponente zum Metadatenschema-Formular-Editor hinzu:

1. Navigieren Sie zu **[!UICONTROL Tools > Assets > Metadatenschemata]**.

1. Wählen Sie den Schemanamen aus und klicken Sie auf **[!UICONTROL Bearbeiten]**.

1. Ziehen Sie **[!UICONTROL Smart-Farb-Tags]** von der Registerkarte **[!UICONTROL Formular erstellen]** in den **[!UICONTROL Metadatenschema-Formulareditor]**.

1. Klicken Sie auf das **[!UICONTROL Smart-Farb-Tag-Feld]** im **[!UICONTROL Metadatenschema-Formular-Editor]**.

1. Geben Sie den entsprechenden Wert im Feld **[!UICONTROL Feldbezeichnung]** auf der Registerkarte **[!UICONTROL Einstellungen]** ein.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

   >[!VIDEO](https://video.tv.adobe.com/v/340124)

## Farb-Tags für vorhandene Bilder in DAM {#color-tags-existing-images}

Die vorhandenen Bilder in DAM werden nicht automatisch mit Farbfeldern versehen. [!UICONTROL Assets erneut verarbeiten] manuell erstellen, um Farb-Tags für sie zu generieren.

Gehen Sie wie folgt vor, um Tag-Bilder oder Ordner (einschließlich Unterordner) von Assets zu farbig zu kennzeichnen, die im Assets-Repository vorhanden sind:

1. Klicken oder tippen Sie auf das [!DNL Adobe Experience Manager]-Logo und wählen Sie dann Assets auf der [!UICONTROL Navigationsseite] aus.

1. Auswählen [!UICONTROL Dateien].

1. Navigieren Sie in der Assets-Benutzeroberfläche zu dem Ordner, auf den Sie Farb-Tags anwenden möchten.

1. Wählen Sie den gesamten Ordner oder nur bestimmte Bilder aus.

1. Klicken oder tippen Sie auf das Symbol ![Assets erneut verarbeiten](assets/do-not-localize/reprocess-assets-icon.png) [!UICONTROL Assets erneut verarbeiten] und wählen Sie die Option [!UICONTROL Vollständiger Prozess] aus.

Navigieren Sie nach Abschluss des Prozesses zum [!UICONTROL Eigenschaften] -Seite eines beliebigen Bildes im Ordner. Die automatisch hinzugefügten Tags werden im [!UICONTROL Smart Color Tags] im Abschnitt [!UICONTROL Allgemein] Registerkarte.


## Anzeigen von Smart-Farb-Tags für Bilder {#view-color-tags}

So zeigen Sie Smart-Farb-Tags für Bilder an:

1. Navigieren Sie zu **[!UICONTROL Adobe Experience Manager > Assets > Dateien]**.

1. Klicken Sie auf den entsprechenden Ordner und wählen Sie das Bild aus.

1. Wählen Sie **[!UICONTROL Eigenschaften]** aus und zeigen Sie die Tags im Feld **[!UICONTROL Smart-Farb-Tags]** an.

   ![Anzeigen von Farb-Tags](assets/view-color-tags.png)

   Bewegen Sie die Maus über ein Farbtag, damit Sie die **[!UICONTROL Schwellenwert für Abdeckung/Dominanz %]** einer Farbe in einem Bild.

## Konfigurieren eines AEM Assets-Farbprädikats {#configure-search-predicate}

Sie können einen Suchfilter für Bilder konfigurieren. Anschließend können Sie Ihre Suchkriterien auf einer bestimmten Farbe basieren, um die Ergebnisse zu filtern.

>[!NOTE]
>
>Konfigurieren Sie das AEM Assets-Farbprädikat nur, wenn Sie das Standardsuchformular nicht verwenden.

Um den Suchfilter zu konfigurieren, erstellen Sie mit der Asset-Admin-Suchschiene ein Asset-Farbprädikat.

So konfigurieren Sie den Suchfilter:

1. Navigieren Sie zu **[!UICONTROL Tools > Allgemein > Suchformulare]**.

1. Wählen Sie **[!UICONTROL Asset-Admin-Suchschiene]** und klicken Sie auf **[!UICONTROL Bearbeiten]**.

1. Ziehen Sie **[!UICONTROL Asset-Farbprädikat]** von der Registerkarte **[!UICONTROL Prädikat auswählen]** zum **[!UICONTROL Suchformular-Editor]**.

1. Geben Sie den entsprechenden Wert im Feld **[!UICONTROL Feldbezeichnung]** auf der Registerkarte **[!UICONTROL Einstellungen]** ein.

1. Klicken Sie auf **[!UICONTROL Fertig]**, um die Einstellungen zu speichern.

   >[!VIDEO](https://video.tv.adobe.com/v/340110)

## Suchen nach Bildern anhand von Farben {#search-images-based-on-colors}

>[!VIDEO](https://video.tv.adobe.com/v/340761)

Nach dem Konfigurieren aller Farb-Tagging-Eigenschaften und [Konfigurieren des Assets-Farbprädikats](#search-images-based-on-colors)können Sie Bilder basierend auf einer Farbe als Filter suchen.

So suchen Sie Bilder basierend auf Farben:

1. Gehen Sie zu **[!UICONTROL Assets > Dateien]**.

1. Wählen Sie **[!UICONTROL Filter]** in der Dropdown-Liste aus.
   ![Filtern von Assets](assets/filter-assets.png)

1. Wählen Sie das [AEM Assets-Farbprädikat](#configure-search-predicate) aus.

1. Ziehen Sie die Farbauswahl, um die gewünschte Farbe auszuwählen. Die ausgewählte Farbe wird im schreibgeschützten Feld angezeigt, das unter der Farbauswahl verfügbar ist. Sie können RGB oder HEX als Anzeigeformat für die Farbe auswählen.

   ![Farbauswahl](assets/color-picker-color-tags.png)

   Sie können Bilder anhand der Auswahl von nur einer Farbe filtern. Die Bilder, die die ausgewählte Farbe als eines der Smart-Farb-Tags und über dem [Schwellenwert für Abdeckung/Dominanz %](#manage-color-tagging-settings) haben, werden im rechten Bereich angezeigt.

1. Löschen Sie den Filter, indem Sie in der Suchleiste auf X klicken.

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
