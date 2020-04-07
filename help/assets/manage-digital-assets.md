---
title: Digitale Assets in Experience Manager verwalten
description: Erfahren Sie mehr über verschiedene Methoden zur Asset-Verwaltung und -Bearbeitung.
contentOwner: AG
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: 26833f59f21efa4de33969b7ae2e782fe5db8a14

---


# Verwalten von Assets {#manage-assets}

In diesem Artikel wird das Verwalten und Bearbeiten von Assets in Adobe Experience Manager (AEM) beschrieben. Informationen zum Verwalten von Inhaltsfragmenten finden Sie unter [Inhaltsfragmente](content-fragments/content-fragments.md) -Assets.

## Erstellen von Ordnern {#creating-folders}

When organizing a collection of assets, for example, all `Nature` images, you can create folders to keep them together. Mit Ordnern können Sie Assets kategorisieren und organisieren. Bei AEM Assets müssen Sie Assets nicht in Ordner organisieren, um besser zu arbeiten.

>[!NOTE]
>
>* Die Freigabe eines Asset-Ordners vom Typ `sling:OrderedFolder` wird bei der Weitergabe an Marketing Cloud nicht unterstützt. If you want to share a folder, do not select [!UICONTROL Ordered] when creating a folder.
>* Experience Manager lässt die Verwendung von `subassets` Wort als Ordnername nicht zu. Es ist ein Schlüsselwort, das für Knoten reserviert ist, die Teilassets für zusammengesetzte Assets enthalten


1. Navigieren Sie zu dem Ort in Ihrem Ordner „Digitale Assets“, an dem Sie einen neuen Ordner erstellen möchten. Klicken Sie im Menü auf **[!UICONTROL Erstellen]**. Select **[!UICONTROL New Folder]**.
1. In the **[!UICONTROL Title]** field, provide a folder name. DAM verwendet standardmäßig den Titel, den Sie als Ordnernamen angegeben haben. Wenn der Ordner erstellt wurde, können Sie die Standardeinstellung außer Kraft setzen und einen anderen Ordnernamen angeben.
1. Klicken Sie auf **[!UICONTROL Erstellen]**. Ihr Ordner wird im Ordner „Digitale Assets“ angezeigt.

Die folgenden Zeichen (in der Liste durch Leerzeichen getrennt) werden nicht unterstützt:

* Der Name einer Asset-Datei darf keines der folgenden Zeichen enthalten: `* / : [ \\ ] | # % { } ? &`
* Der Name eines Asset-Ordners darf keines der folgenden Zeichen enthalten: `* / : [ \\ ] | # % { } ? \" . ^ ; + & \t`

## Upload assets {#uploading-assets}

Detaillierte Informationen finden Sie unter [Hinzufügen digitaler Assets zu Experience Manager](add-assets.md).

## Vorschauen {#previewing-assets}

Gehen Sie wie folgt vor, um ein Asset Vorschau.

1. Navigieren Sie in der Benutzeroberfläche &quot;Assets&quot;zum Speicherort des Assets, das Sie Vorschau haben möchten.
1. Tippen Sie auf das gewünschte Asset, um es zu öffnen.

1. Im Vorschaumodus ist eine Zoom-Funktion für [unterstützte Bildtypen](/help/assets/file-format-support.md) verfügbar (mit interaktiver Bearbeitung).

   To zoom into an asset, tap/click `+` (or tap/click the magnifying glass on the asset). To zoom out, tap/click `-`. Beim Heranzoomen können Sie beliebige Bildbereiche durch Schwenken genauer untersuchen. Mit dem Zurücksetzen-Zoom-Pfeil kehren Sie zur ursprünglichen Ansicht zurück.

   Tap **[!UICONTROL Reset]** to reset the view to the original size.

## Eigenschaften bearbeiten {#editing-properties}

1. Navigieren Sie zum Speicherort des Assets, dessen Metadaten Sie bearbeiten möchten.

1. Select the asset, and tap/click **[!UICONTROL Properties]** from the toolbar to view asset properties. Wählen Sie alternativ die Schnellaktion **[!UICONTROL Eigenschaften]** auf der Asset-Karte aus.

   ![properties_quickaction](assets/properties_quickaction.png)

1. In the [!UICONTROL Properties] page, edit the metadata properties under various tabs. Zum Beispiel bearbeiten Sie auf der Registerkarte **[!UICONTROL Allgemein]** den Titel, die Beschreibung usw.

   >[!NOTE]
   >
   >The layout of the [!UICONTROL Properties] page and the metadata properties available depend on the underlying metadata schema. To learn how to modify the layout of the [!UICONTROL Properties] page, see [Metadata Schemas](/help/assets/metadata-schemas.md).

1. Um ein bestimmtes Datum/eine bestimmte Uhrzeit für die Aktivierung des Assets zu planen, verwenden Sie die Datumsauswahl neben dem Feld **[!UICONTROL Zeit]**.

   ![chlimage_1-217](assets/chlimage_1-217.png)

1. To deactivate the asset after a particular duration, choose the deactivation date/time from the date picker beside the **[!UICONTROL Off Time]** field. Das Deaktivierungsdatum sollte später als das Aktivierungsdatum für ein Asset sein. Nach der [!UICONTROL Abschaltzeit]sind ein Asset und seine Darstellungen weder über die Assets-Weboberfläche noch über die HTTP-API verfügbar.

   ![chlimage_1-218](assets/chlimage_1-218.png)

1. Wählen Sie im Feld **[!UICONTROL Tags]** ein oder mehrere Tags aus. Um ein benutzerdefiniertes Tag hinzuzufügen, geben Sie den Namen des Tags in das Feld ein und drücken Sie die Eingabetaste. Das neue Tag wird in AEM gespeichert.

   YouTube erfordert Tags zur Veröffentlichung und einen YouTube-Link (wenn ein geeigneter Link gefunden werden kann).

   >[!NOTE]
   >
   >Um Tags zu erstellen, müssen Sie über Schreibberechtigung für `/content/cq:tags/default` den Pfad im CRX-Repository verfügen.

1. To view usage usage statistics for the asset, click/tap the **[!UICONTROL Insights]** tab.

   Nutzungsstatistiken umfassen folgende Metriken:

   * Anzahl der Aufrufe oder Downloads des Assets
   * Kanäle/Geräte, über die das Asset genutzt wurde
   * Kreativlösungen, in denen das Asset kürzlich verwendet wurde
   Weitere Informationen finden Sie unter [Asset Insights](assets-insights.md).

1. Tippen oder klicken Sie auf **[!UICONTROL Speichern und schließen]**.

1. Navigieren Sie zur Benutzeroberfläche &quot;Assets&quot;. Die bearbeiteten Metadateneigenschaften, einschließlich Titel, Beschreibung und Tags, werden auf der Elementkarte in der Ansicht &quot;Karte&quot;und unter den entsprechenden Spalten in der Ansicht &quot;Liste&quot;angezeigt.

## Kopieren von Assets {#copying-assets}

Beim Kopieren eines Assets oder eines Ordners wird das gesamte Asset bzw. der Ordner mitsamt seiner Inhaltsstruktur kopiert. Ein kopiertes Asset oder ein kopierter Ordner wird am Zielspeicherort dupliziert. Das Asset am Quellspeicherort bleibt unverändert.

Einige wenige, für eine bestimmte Kopie eines Assets eindeutige Attribute werden nicht übertragen. Beispiele:

* Asset-ID, Erstellungsdatum und -zeit sowie Versionen und Versionsverlauf. Some of these properties are indicated by the properties `jcr:uuid`, `jcr:created`, and `cq:name`.

* Der Erstellungszeitpunkt und referenzierte Pfade sind für jedes Asset und jede seiner Wiedergaben eindeutig.

Die übrigen Eigenschaften und Metadateninformationen werden beibehalten. Eine Teilkopie wird beim Kopieren eines Assets nicht erstellt.

1. From the Assets UI, select one or more assets, and then tap/click the **[!UICONTROL Copy]** icon from the toolbar. Alternativ können Sie die Schnellaktion **[!UICONTROL Copy]** ![copy_icon](assets/copy_icon.png) auf der Asset-Karte auswählen.

   >[!NOTE]
   >
   >If you use the [!UICONTROL Copy] quick action, you can only copy one asset at a time.

1. Navigieren Sie zum Speicherort, in den Sie die Assets kopieren möchten.

   >[!NOTE]
   >
   >Wenn Sie ein Asset in denselben Speicherort kopieren, generiert AEM automatisch eine Variation des Namens. For example, if you copy an asset titled `Square`, AEM automatically generates the title for its copy as `Square1`.

1. Click the **[!UICONTROL Paste]** asset icon from the toolbar. Assets werden an diesen Speicherort kopiert.

   ![chlimage_1-219](assets/chlimage_1-219.png)

   >[!NOTE]
   >
   >The **[!UICONTROL Paste]** icon is available in the toolbar until the paste operation is completed.

### Verschieben oder Umbenennen von Assets {#moving-or-renaming-assets}

1. Navigieren Sie zum Speicherort des Assets, das Sie verschieben möchten.

1. Select the asset, and tap/click the **[!UICONTROL Move]** icon ![move_icon](assets/move_icon.png) from the toolbar.

1. Führen Sie im Assistenten „Assets verschieben“ eine der folgenden Aktionen aus:

   * Geben Sie nach dem Verschieben den Namen für das Asset an. Then tap/click **[!UICONTROL Next]** to proceed.

   * Tap/click **[!UICONTROL Cancel]** to stop the process.
   >[!NOTE]
   >
   >* Sie können denselben Namen für das Asset angeben, wenn sich am neuen Speicherort kein Asset mit diesem Namen befindet. Sie sollten jedoch einen anderen Namen verwenden, wenn Sie das Asset an einen Speichertort verschieben, an dem bereits ein Asset mit demselben Namen vorhanden ist. Wenn Sie denselben Namen verwenden, generiert das System automatisch eine Variante dieses Namens. Wenn Sie beispielsweise ein Asset mit dem Namen „Quadrat“ kopieren, generiert das System den Namen „Quadrat1“ für die Kopie.
   >* Beim Umbenennen sind keine Leerzeichen in Dateinamen zulässig.


1. On the **[!UICONTROL Select Destination]** dialog, do one of the following:

   * Navigate to the new location for the assets, and then tap/click **[!UICONTROL Next]** to proceed.

   * Tap/click **[!UICONTROL Back]** to return to the **[!UICONTROL Rename]** screen.

1. If the assets being moved have any referencing pages, assets, or collections, the **[!UICONTROL Adjust References]** tab appears beside the **[!UICONTROL Select Destination]** tab.

   Do one of the following in the **[!UICONTROL Adjust References]** screen:

   * Specify the references to be adjusted based on the new details, and then tap/click **[!UICONTROL Move]** to proceed.

   * Aktivieren/deaktivieren Sie in der Spalte **[!UICONTROL Anpassen]** Referenzen zu den Assets.
   * Tap/click **[!UICONTROL Back]** to return to the **[!UICONTROL Select Destination]** screen.

   * Tap/click **[!UICONTROL Cancel]** to stop the move operation.
   Wenn Sie Verweise nicht aktualisieren, verweisen sie weiterhin auf den vorherigen Pfad des Assets. Wenn Sie die Verweise aktualisieren, werden sie an den neuen Asset-Pfad angepasst.

### Darstellungen verwalten {#managing-renditions}

1. Sie können Wiedergabeformate für ein Asset hinzufügen oder entfernen, mit Ausnahme des Originals. Navigieren Sie zum Speicherort des Assets, für das Sie Ausgabeformate hinzufügen oder entfernen möchten.

1. Tippen oder klicken Sie auf das Asset, um die Asset-Seite zu öffnen.

   ![chlimage_1-220](assets/chlimage_1-220.png)

1. Tap/click the GlobalNav icon, and select **[!UICONTROL Renditions]** from the list.

   ![renditions_menu](assets/renditions_menu.png)

1. Im Bereich **[!UICONTROL Wiedergabeformate]** wird die Liste der für das Asset generierten Wiedergabeformate angezeigt.

   ![renditions_panel](assets/renditions_panel.png)

   >[!NOTE]
   >
   >Standardmäßig zeigt AEM Assets im Vorschaumodus nicht das ursprüngliche Wiedergabeformat des Assets an. Wenn Sie ein Administrator sind, können Sie Überlagerungen verwenden, um AEM Assets so zu konfigurieren, dass ursprüngliche Wiedergabeformate im Vorschaumodus angezeigt werden.

1. Wählen Sie ein Ausgabeformat aus, um es anzuzeigen oder zu löschen.

   **Löschen eines Ausgabeformats**

   Select a rendition from the **[!UICONTROL Renditions]** panel, and then tap/click the **[!UICONTROL Delete Rendition]** icon from the toolbar.

   ![delete_renditionicon](assets/delete_renditionicon.png)

   **Ein neues Ausgabeformat hochladen**

   Navigieren Sie zur Seite mit den Asset-Details und tippen/klicken Sie auf das Symbol **[!UICONTROL Ausgabedarstellung hinzufügen]** in der Symbolleiste, um eine neue Ausgabedarstellung für das Asset hochzuladen.

   ![chlimage_1-221](assets/chlimage_1-221.png)

   >[!NOTE]
   >
   >Wenn Sie eine Ausgabedarstellung aus dem Bedienfeld **[!UICONTROL Ausgabedarstellungen]** auswählen, ändert sich der Kontext in der Symbolleiste und zeigt nur die Aktionen an, die für die Ausgabedarstellung relevant sind. Optionen wie das Symbol „Ausgabedarstellung hochladen“ werden nicht angezeigt. Um diese Optionen in der Symbolleiste anzuzeigen, navigieren Sie zur Detailseite für das Asset.

   Sie können die Dimensionen für das anzuzeigende Ausgabeformat auf der Detailseite des entsprechenden Bild- oder Video-Assets konfigurieren. AEM Assets zeigt anhand der von Ihnen angegebenen Abmessungen das Ausgabeformat mit den genauen oder möglichst genauen Abmessungen an.

   Um die Ausgabedarstellungsdimensionen eines Bildes auf der Stufe der Asset-Details zu konfigurieren, überlagern Sie den `renditionpicker`-Knoten (`libs/dam/gui/content/assets/assetpage/jcr:content/body/content/content/items/assetdetail/items/col1/items/assetview/renditionpicker`) und konfigurieren Sie den Wert der Eigenschaft „width“. Konfigurieren Sie die Eigenschaft **[!UICONTROL Größe (lang) in KB]** anstelle der Breite, um die Ausgabedarstellung auf der Seite mit den Asset-Details basierend auf der Bildgröße anzupassen. Bei der größenbasierten Anpassung weist die Eigenschaft `preferOriginal` dem Original die Voreinstellung zu, wenn die Größe der übereinstimmenden Ausgabedarstellung größer als das Original ist.

   Ebenso können Sie das Bild der Anmerkungsseite durch Überlagern anpassen `libs/dam/gui/content/assets/annotate/jcr:content/body/content/content/items/content/renditionpicker`.

   ![chlimage_1-222](assets/chlimage_1-222.png)

   To configure rendition dimensions for a video asset, navigate to the `videopicker` node in the CRX repository at the location `/libs/dam/gui/content/assets/assetpage/jcr:content/body/content/content/items/assetdetail/items/col1/items/assetview/videopicker`, overlay the node, and then edit the appropriate property.

   >[!NOTE]
   >
   >Videoanmerkungen werden nur für Browser mit HTML5-kompatiblen Videoformaten unterstützt. Darüber hinaus werden je nach Browser unterschiedliche Videoformate unterstützt.

## Löschen von Assets {#delete-assets}

Um die eingehenden Verweise von anderen Seiten aufzulösen oder zu entfernen, aktualisieren Sie die entsprechenden Verweise, bevor Sie ein Asset löschen.

Deaktivieren Sie außerdem die Schaltfläche „Löschen erzwingen“ mithilfe einer Überlagerung, um zu verhindern, dass Benutzer referenzierte Assets löschen und fehlerhafte Links hinterlassen.

1. Navigieren Sie zum Speicherort der Assets, die Sie löschen möchten.

1. Select the asset, and tap/click the **[!UICONTROL Delete]** icon from the toolbar.

   ![delete_icon](assets/delete_icon.png)

1. Klicken Sie im Bestätigungsdialogfeld auf:

   * **[!UICONTROL Abbrechen]**, um die Aktion abzubrechen.
   * **[!UICONTROL Löschen]**, um die Aktion zu bestätigen:

      * Wenn das Asset keine Referenzen aufweist, wird es gelöscht.
      * Wenn die Seite Referenzen aufweist, wird eine Fehlermeldung angezeigt mit dem Hinweis **Es wird auf ein oder mehrere Asset(s) verwiesen.** Sie können **[!UICONTROL Löschen erzwingen]** oder **[!UICONTROL Abbrechen]** auswählen.
   >[!NOTE]
   >
   >Zum Löschen eines Assets benötigen Sie die Berechtigung zum Löschen eines Dammes/Assets. Wenn Sie nur eine Änderungsberechtigung haben, haben Sie nur die Möglichkeit, die Asset-Metadaten zu bearbeiten und Notizen zum Asset hinzuzufügen. Sie können jedoch das Asset oder dessen Metadaten nicht löschen.

   >[!NOTE]
   >
   >Um die eingehenden Verweise von anderen Seiten aufzulösen oder zu entfernen, aktualisieren Sie die entsprechenden Verweise, bevor Sie ein Asset löschen.
   >
   >
   >Deaktivieren Sie außerdem die Schaltfläche „Löschen erzwingen“ mithilfe einer Überlagerung, um zu verhindern, dass Benutzer referenzierte Assets löschen und fehlerhafte Links hinterlassen.

## Herunterladen von Assets {#download-assets}

Siehe [Herunterladen von Assets aus AEM](/help/assets/download-assets-from-aem.md).

## Publish assets {#publish-assets}

<!--
>[!NOTE]
>
>For more information specific to Dynamic Media, see [Publishing Dynamic Media Assets.](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md)
-->

1. Navigieren Sie zum Speicherort der Assets/Ordner, die Sie veröffentlichen möchten.

1. Wählen Sie entweder per Schnellzugriff **[!UICONTROL Veröffentlichen]** auf der Asset-Karte aus oder wählen Sie das Asset aus und tippen/klicken Sie in der Symbolleiste auf das Symbol **[!UICONTROL Schnell veröffentlichen]**.
1. Wenn das Asset andere Assets referenziert, werden die Verweise im Assistenten aufgelistet. Es werden nur Verweise angezeigt, die entweder unveröffentlicht sind oder seit der letzten Veröffentlichung/Aufhebung der Veröffentlichung geändert wurden. Wählen Sie die Referenzen aus, die Sie veröffentlichen möchten.

   ![chlimage_1-225](assets/chlimage_1-225.png)

   >[!NOTE]
   >
   >Wenn der Ordner, den Sie veröffentlichen möchten, einen leeren Ordner enthält, wird der leere Ordner nicht veröffentlicht.

1. Tippen oder klicken Sie auf **[!UICONTROL Veröffentlichen]**, um die Aktivierung für die Assets zu bestätigen.

>[!CAUTION]
>
>Wenn Sie ein Asset veröffentlichen, das momentan verarbeitet wird, wird nur der ursprüngliche Inhalt veröffentlicht. Die Wiedergabeformate fehlen. Warten Sie entweder bis, die Verarbeitung abgeschlossen ist, und veröffentlichen Sie das Asset erst dann bzw. veröffentlichen Sie es erneut, wenn die Verarbeitung abgeschlossen ist.

## Rückgängigmachen der Veröffentlichung von Assets {#unpublishing-assets}

1. Navigieren Sie zum Speicherort des Assets/Asset-Ordners, das bzw. den Sie aus der Veröffentlichungsumgebung entfernen möchten (Veröffentlichung rückgängig machen).

1. Select the asset/folder to unpublish, and tap/click the **[!UICONTROL Manage Publication]** icon from the toolbar.

   ![manage_publication](assets/manage_publication.png)

1. Select the **[!UICONTROL Unpublish]** action from the list.

   ![unpublish_action](assets/unpublish_action.png)

1. Um die Veröffentlichung des Assets später rückgängig zu machen, wählen Sie **[!UICONTROL Veröffentlichung später rückgängig machen]** und anschließend ein Datum aus, an dem die Veröffentlichung des Assets rückgängig gemacht werden soll.
1. Legen Sie ein Datum fest, an dem die Assets aus der Veröffentlichungsumgebung entfernt werden sollen.
1. Wenn das Asset andere Assets referenziert, wählen Sie die Verweise aus, deren Veröffentlichung Sie rückgängig machen möchten. Tap/click **[!UICONTROL Unpublish]**.
1. Tippen oder klicken Sie im Bestätigungsdialogfeld auf:

   * **[!UICONTROL Abbrechen]**, um die Aktion abzubrechen.
   * **[!UICONTROL Rückgängigmachen der Veröffentlichung]** , um zu bestätigen, dass die Veröffentlichung der Assets am angegebenen Umgebung rückgängig gemacht wurde (sie sind nicht mehr auf der Veröffentlichungsseite verfügbar).
   >[!NOTE]
   >
   >Wenn Sie die Veröffentlichung eines komplexen Assets rückgängig machen, machen Sie die Veröffentlichung des Assets rückgängig. Vermeiden Sie es, die Veröffentlichung der Verweise aufzuheben, da sie möglicherweise von anderen veröffentlichten Assets referenziert werden.

## Closed user group {#closed-user-group}

Eine geschlossene Benutzergruppe (Closed User Group, CUG) wird verwendet, um den Zugriff auf bestimmte aus AEM veröffentlichte Asset-Ordner zu beschränken. Wenn Sie eine CUG für einen Ordner erstellen, wird der Zugriff auf diesen Ordner (einschließlich Ordner-Assets und Unterordnern) auf zugewiesene Mitglieder und Gruppen beschränkt. Um auf einen Ordner zuzugreifen, müssen Benutzer mit ihren Sicherheitsanmeldedaten angemeldet sein.

CUGs stellen eine zusätzliche Möglichkeit dar, den Zugang zu Ihren Assets zu beschränken. Sie können auch eine Anmeldeseite für den Ordner konfigurieren.

1. Wählen Sie in der Assets-Benutzeroberfläche einen Ordner aus und tippen oder klicken Sie in der Symbolleiste auf das Symbol „Eigenschaften“, um die Eigenschaftsseite anzuzeigen.
1. Fügen Sie auf der Registerkarte **[!UICONTROL Berechtigungen]** unter **[!UICONTROL Geschlossene Benutzergruppe]** Mitglieder oder Gruppen hinzu.

   ![add_user](assets/add_user.png)

1. Um einen Anmeldebildschirm anzuzeigen, wenn Benutzer auf den Ordner zugreifen, wählen Sie die Option **[!UICONTROL Aktivieren]** aus. Wählen Sie anschließend den Pfad zur Anmeldeseite in AEM aus und speichern Sie die Änderungen.

   ![login_page](assets/login_page.png)

   >[!NOTE]
   >
   >Wenn Sie den Pfad zur Anmeldeseite nicht angeben, zeigt AEM die standardmäßige Anmeldeseite in der Veröffentlichungsinstanz an.

1. Veröffentlichen Sie den Ordner und versuchen Sie, über die Veröffentlichungsinstanz darauf zuzugreifen. Es wird ein Anmeldebildschirm angezeigt.
1. Wenn Sie Mitglied der CUG sind, geben Sie Ihre Anmeldedaten ein. Nachdem Sie von AEM authentifiziert wurden, wird der Ordner angezeigt.

## Suchen nach Assets {#search-assets}

Die Suche nach Assets ist ein zentraler Faktor für die Nutzung eines digitalen Asset-Managements – sowohl für eine weitere Verwendung durch kreative Elemente als auch für eine robuste Verwaltung von Assets durch die Geschäftsbenutzer und Marketingexperten oder für die Verwaltung durch DAM-Administratoren.

Einfache, erweiterte und benutzerdefinierte Suchen zur Erkennung und Verwendung der am besten geeigneten Assets finden Sie unter [Assets in AEM suchen](/help/assets/search-assets.md).

## Schnellaktionen {#quick-actions}

Schnellaktion-Symbole sind jeweils nur für ein Asset verfügbar. Führen Sie je nach Gerät folgende Aktionen durch, um die Symbole der Schnellaktionen anzuzeigen:

* Touch-Geräte: Tippen und halten. Beispielsweise können Sie auf einem iPad auf ein Asset tippen und halten, damit die Schnellaktionen angezeigt werden.
* Non-Touch-Geräte: Mit Mauszeiger darüberfahren. Beispielsweise wird auf einem Desktop-Gerät die Schnellaktion angezeigt, wenn Sie den Mauszeiger über die Asset-Miniaturansicht bewegen.

## Bilder bearbeiten {#editing-images}

Mit den Bearbeitungswerkzeugen in der Oberfläche von AEM Assets können Sie kleine Bearbeitungsaktionen in Bild-Assets durchführen. Sie können Bilder beschneiden, drehen, spiegeln und auf andere Arten bearbeiten. Sie können auch Imagemaps zu den Assets hinzufügen.

>[!NOTE]
>
>Bei manchen Komponenten sind für den Vollbildmodus zusätzliche Optionen verfügbar.

1. Führen Sie einen der folgenden Schritte aus, um ein Element im Bearbeitungsmodus zu öffnen:

   * Select the asset and then click/tap the **[!UICONTROL Edit]** icon in the toolbar.
   * Tap/click the **[!UICONTROL Edit]** icon that appears on an asset in the Card view.
   * In the asset page, tap/click the **[!UICONTROL Edit]** icon in the toolbar.
   ![edit_icon](assets/edit_icon.png)

1. To crop the image, tap/click the **Crop** icon.

   ![chlimage_1-226](assets/chlimage_1-226.png)

1. Wählen Sie die gewünschte Option aus der Liste aus. Der Zuschneidebereich wird auf dem Bild je nach gewählter Option angezeigt. Mit der Option **Freihand** können Sie das Bild ohne Einschränkungen des Seitenverhältnisses zuschneiden.

   ![chlimage_1-227](assets/chlimage_1-227.png)

1. Wählen Sie den zuzuschneidenden Bereich und ändern Sie die Größe oder Position auf dem Bild.
1. Verwenden Sie das Symbol **Fertig** (in der rechten oberen Ecke), um das Bild zu beschneiden. Durch Klicken auf **Fertigstellen** wird auch die Neuerstellung von Ausgabeformaten ausgelöst.

   ![chlimage_1-228](assets/chlimage_1-228.png)

1. Verwenden Sie die Symbole **Rückgängig** und **Wiederholen** oben rechts, um zum nicht zugeschnittenen Bild zurückzukehren oder das nicht geschnittene Bild beizubehalten.

   ![chlimage_1-229](assets/chlimage_1-229.png)

1. Tippen oder klicken Sie auf das entsprechende Drehsymbol, um das Bild im oder entgegen dem Uhrzeigersinn zu drehen.

   ![chlimage_1-230](assets/chlimage_1-230.png)

1. Tippen oder klicken Sie auf das entsprechende Spiegelsymbol, um das Bild horizontal oder vertikal zu spiegeln.

   ![chlimage_1-231](assets/chlimage_1-231.png)

1. Tap/click the **Finish** icon to save the changes.

   ![chlimage_1-232](assets/chlimage_1-232.png)

>[!NOTE]
>
>Bildbearbeitung wird für die Dateiformate BMP, GIF, PNG und JPEG unterstützt.

<!-- You can also add image maps using the image editor. For details, see [Adding Image Maps](/help/assets/image-maps.md). -->

>[!NOTE]
>
>To edit a TXT file, set **Day CQ Link Externalizer** from Configuration Manager.

## Zeitleiste {#timeline}

In der Timeline können Sie diverse Ereignisse für ein ausgewähltes Objekt ansehen, wie z. B. aktive Workflows für ein Asset, Kommentare/Anmerkungen, Aktivitätsprotokolle und Versionen.

![Sortieren von Zeitleisteneinträgen für ein Asset](assets/sort_timeline.gif)*Abbildung: Sortieren von Zeitleisteneinträgen für ein Asset*

>[!NOTE]
>
>In der [Konsole für Sammlungen](/help/assets/manage-collections.md#navigate-the-collections-console) bietet die Liste **[!UICONTROL Alle anzeigen]** Optionen, um nur Kommentare und Workflows anzuzeigen. Darüber hinaus wird die Timeline nur für Sammlungen auf der höchsten Ebene angezeigt, die in der Konsole aufgelistet sind. Sie wird nicht angezeigt, wenn Sie in einer der Sammlungen navigieren.

>[!NOTE]
>
>Die Timeline enthält mehrere [inhaltsfragmentspezifische Optionen](content-fragments/content-fragments.md).

## Anmerken {#annotating}

Anmerkungen sind Kommentare oder erläuternde Hinweise, die Bildern oder Videos hinzugefügt werden. Anmerkungen bieten Marketern die Möglichkeit, zusammenzuarbeiten und Feedback zu Assets bereitzustellen.

Videoanmerkungen werden nur für Browser mit HTML5-kompatiblen Videoformaten unterstützt. Videoformate, die von AEM Assets unterstützt werden, hängen vom Browser ab.

>[!NOTE]
>
>Bei Inhaltsfragmenten werden [Anmerkungen im Fragment-Editor erstellt](content-fragments/content-fragments.md).

1. Navigieren Sie zum Speicherort des Assets, dem Sie Anmerkungen hinzufügen möchten.
1. Tap/click the **[!UICONTROL Annotate]** icon from one of the following:

   * [Schnellaktionen](#quick-actions)
   * In der Symbolleiste, nachdem Sie das Asset ausgewählt haben     oder zur Asset-Seite navigiert sind
   ![chlimage_1-233](assets/chlimage_1-233.png)

1. Fügen Sie im Feld **[!UICONTROL Kommentar]** am unteren Rand der Timeline einen Kommentar hinzu. Alternativ können Sie einen Bildbereich markieren und eine Anmerkung im Dialogfeld **[!UICONTROL Anmerkung hinzufügen]** hinzufügen.

   ![chlimage_1-234](assets/chlimage_1-234.png)

<!--
1. To notify a user about an annotation, specify the email address of the user and add the comment. For example, to notify Aaron MacDonald about an annotation, enter @aa. Hints for all matching users is displayed in a list. Select Aaron's email address from the list to tag her with the comment. Similarly, you can tag more users anywhere within the annotation or before or after it.
-->

>[!NOTE]
>
>For a non-administrator user, suggestions appear only if the user has Read permissions at `/home` in CRXDE.

![chlimage_1-235](assets/chlimage_1-235.png)

1. Nachdem Sie die Anmerkung hinzugefügt haben, klicken Sie auf **[!UICONTROL Hinzufügen]**, um sie zu speichern. Eine Benachrichtigung über die Anmerkung wird an Aaron gesendet.

   ![chlimage_1-236](assets/chlimage_1-236.png)

   >[!NOTE]
   >
   >Sie können mehrere Anmerkungen hinzufügen, bevor Sie diese speichern.

1. Tippen oder klicken Sie auf **[!UICONTROL Schließen]**, um den Anmerkungsmodus zu verlassen.
1. To view the notification, log in to AEM Assets with Aaron MacDonald&#39;s credentials and click the **[!UICONTROL Notifications]** icon to view the notification.

   >[!NOTE]
   >
   >Sie können Video-Assets auch Anmerkungen hinzufügen. Während Videos mit Anmerkungen versehen werden, wird der Player angehalten, damit Sie einem Frame eine Anmerkung hinzufügen können. For details, see [managing video assets](manage-video-assets.md).

1. Wenn Sie eine andere Farbe auswählen möchten, um zwischen Benutzern zu unterscheiden, klicken/tippen Sie auf das Symbol „Profil“. Anschließend klicken/tippen Sie auf **[!UICONTROL Eigene Voreinstellungen]**.

   ![chlimage_1-237](assets/chlimage_1-237.png)

   Geben Sie die gewünschte Farbe im Feld **[!UICONTROL Anmerkungsfarbe]** an und klicken Sie dann auf **[!UICONTROL Akzeptieren]**.

   ![chlimage_1-238](assets/chlimage_1-238.png)

>[!NOTE]
>
>Sie können auch Anmerkungen zu einer Sammlung hinzufügen. Wenn eine Sammlung jedoch untergeordnete Sammlungen enthält, können Sie nur der übergeordneten Sammlung Anmerkungen/Kommentare hinzufügen. Die Option „Anmerken“ ist nicht für untergeordnete Sammlungen verfügbar.

### Ansicht gespeicherte Anmerkungen {#viewing-saved-annotations}

1. Um die gespeicherten Anmerkungen zu einem Asset anzuzeigen, navigieren Sie zum Speicherort des Assets und öffnen Sie die Asset-Seite für dieses Asset.

1. Tap/click the GlobalNav icon, and choose **[!UICONTROL Timeline]** from the list.

   ![chlimage_1-239](assets/chlimage_1-239.png)

1. Wählen Sie in der Timeline in der Liste **[!UICONTROL Alle anzeigen]** die Option **[!UICONTROL Kommentare]**, um die Ergebnisse auf der Grundlage von Anmerkungen zu filtern.

   ![chlimage_1-240](assets/chlimage_1-240.png)

   Tippen oder klicken Sie im Bedienfeld **[!UICONTROL Timeline]** auf einen Kommentar, um die entsprechende Anmerkung auf dem Bild anzuzeigen.

   ![chlimage_1-241](assets/chlimage_1-241.png)

   Tippen oder klicken Sie auf **[!UICONTROL Löschen]**, um einen bestimmten Kommentar zu löschen.

### Drucken von Anmerkungen {#printing-annotations}

Wenn ein Asset Anmerkungen enthält oder einem Review-Arbeitsablauf unterzogen wurde, können Sie das Asset zusammen mit Anmerkungen drucken und den Review-Status als PDF-Datei für die Offline-Überprüfung prüfen.

Sie können auch nur die Anmerkungen oder nur den Prüfungsstatus drucken.

Zum Drucken der Anmerkungen und des Prüfungsstatus tippen/klicken Sie auf das Symbol **[!UICONTROL Drucken]** und folgen Sie den Anweisungen im Assistenten. The **[!UICONTROL Print]** icon appears in the toolbar only when the asset has at least one annotation or review status assigned to it.

1. Öffnen Sie von der Assets-Benutzeroberfläche aus die Vorschauseite für ein Asset.
1. Führen Sie einen der folgenden Schritte aus:

   * Zum Drucken aller Anmerkungen und des Prüfungsstatus überspringen Sie Schritt 3. Dann fahren Sie direkt mit Schritt 4 fort.
   * To print specific annotations and review status, open the [timeline](/help/assets/manage-digital-assets.md#timeline) and then go to step 3.

1. Zum Drucken bestimmter Anmerkungen wählen Sie die Anmerkungen aus der Timeline aus.

   ![chlimage_1-242](assets/chlimage_1-242.png)

   Um nur den Prüfungsstatus zu drucken, wählen Sie ihn aus der Timeline aus.

   ![chlimage_1-243](assets/chlimage_1-243.png)

1. Tippen/klicken Sie in der Symbolleiste auf das Symbol **[!UICONTROL Drucken]**.

   ![chlimage_1-244](assets/chlimage_1-244.png)

1. Wählen Sie im Dialogfeld „Drucken“ die Position, deren Anmerkungen/Prüfungsstatus in der PDF-Datei angezeigt werden sollen. For example, if you want the annotations/status to be printed at the top-right of the page that contains the printed image, use the **Top-Left** setting. Sie ist standardmäßig aktiviert.

   ![chlimage_1-245](assets/chlimage_1-245.png)

   Sie können je nach Position, an der Anmerkungen/Status in der gedruckten PDF-Datei angezeigt werden sollen, andere Einstellungen auswählen. Wenn Anmerkungen/Status auf einer Seite angezeigt werden sollen, die vom gedruckten Asset getrennt ist, wählen Sie **[!UICONTROL Nächste Seite]**.

   >[!NOTE]
   >
   >Längere Anmerkungen werden in der PDF-Datei möglicherweise nicht richtig gerendert. Für optimales Rendering wird empfohlen, Anmerkungen auf 50 Wörter zu begrenzen.

1. Tippen/Klicken Sie auf **[!UICONTROL Drucken]**. Basierend auf der in Schritt 2 gewählten Option zeigt die erstellte PDF-Datei die Anmerkungen/den Status an der angegebenen Position an. Wenn Sie z. B. mit der Einstellung **Oben links** sowohl Anmerkungen als auch Prüfungsstatus drucken möchten, entspricht die generierte Ausgabe der hier dargestellten PDF-Datei.

   ![chlimage_1-246](assets/chlimage_1-246.png)

1. Laden Sie die PDF-Datei herunter oder drucken Sie sie mithilfe der Optionen in der rechten oberen Ecke.

   ![chlimage_1-247](assets/chlimage_1-247.png)

   Um das Erscheinungsbild der gerenderten PDF-Datei zu ändern, z. B. Schriftfarbe, Größe, Stil und Hintergrundfarbe der Kommentare und Status, öffnen Sie in Configuration Manager die **[!UICONTROL Konfiguration für PDF-Anmerkungen]** und ändern Sie die gewünschten Optionen. Um beispielsweise die Anzeigefarbe des Status „Bestätigt“ zu ändern, modifizieren Sie im entsprechenden Feld den Farbcode. Informationen zum Ändern der Schriftfarbe von Anmerkungen finden Sie unter [Anmerken](/help/assets/manage-digital-assets.md#annotating).

   ![chlimage_1-248](assets/chlimage_1-248.png)

   Kehren Sie zu der gerenderten PDF-Datei zurück und aktualisieren Sie sie. Der aktualisierte PDF-Datei spiegelt die von Ihnen vorgenommenen Änderungen wider.

## Asset versioning {#asset-versioning}

Bei der Versionierung wird eine Momentaufnahme von digitalen Assets zu einem bestimmten Zeitpunkt aufgezeichnet. Sie hilft Ihnen bei der späteren Wiederherstellung eines vorherigen Asset-Zustands. Wenn Sie etwa eine Änderung an einem Asset rückgängig machen wollen, stellen Sie die unbearbeitete Version des Assets wieder her.

In folgenden Szenarien werden Versionen erstellt:

* Sie ändern ein Bild in einer anderen Anwendung und laden es in AEM Assets hoch. Es wird eine Version des Bildes erstellt, damit das Original nicht überschrieben wird.
* Sie können die Metadaten eines Assets bearbeiten.
* Mit der AEM-Desktop-App können Sie ein vorhandenes Asset auschecken und Ihre Änderungen speichern. Es wird nicht bei jedem Speichern des Assets eine neue Version erstellt.

Sie können mithilfe eines Workflows die automatische Versionierung einstellen. Wenn Sie eine Version für ein Asset erstellen, werden die Metadaten und Darstellungen zusammen mit der Version gespeichert. Ausgabeformate sind gerenderte Alternativen für dieselben Bilder, z. B. ein PNG-Ausgabeformat einer hochgeladenen JPEG-Datei.

Die Versionierungsfunktion bietet folgende Möglichkeiten:

* Erstellen einer Version eines Assets
* Anzeigen der aktuellen Version eines Assets
* Zurücksetzen des Assets auf eine frühere Version

1. Navigieren Sie zum Speicherort des Assets, von dem Sie eine Version erstellen möchten, und klicken/tippen Sie es an, um seine Asset-Seite zu öffnen.

1. Tippen oder klicken Sie auf das GlobalNav-Symbol und wählen Sie **[!UICONTROL Timeline]** aus dem Menü aus.

   ![Zeitschiene](assets/timeline.png)

1. Tap/click the **[!UICONTROL Actions]** (arrow) icon at the bottom to view the available actions you can perform on the asset.

   ![chlimage_1-249](assets/chlimage_1-249.png)

1. Tippen oder klicken Sie auf **[!UICONTROL Als Version speichern]**, um eine Version für das Asset zu erstellen.

   ![chlimage_1-250](assets/chlimage_1-250.png)

1. Add a label and comment, and then click **[!UICONTROL Create]** to create a version. Alternatively, tap/click **Cancel** to exit the operation.

   ![chlimage_1-251](assets/chlimage_1-251.png)

1. Um die neue Version anzuzeigen, öffnen Sie auf der Seite mit den Asset-Details oder in der Benutzeroberfläche „Assets“ die Liste **[!UICONTROL Alle anzeigen]** und wählen Sie **[!UICONTROL Versionen]** aus. Alle für ein Asset erstellten Versionen werden auf der Registerkarte „Timeline“ aufgeführt. Sie können die Liste filtern, um Versionen anzuzeigen, indem Sie auf den Pfeil klicken und in der Liste **[!UICONTROL Versionen]** auswählen.

   ![versions_option](assets/versions_option.png)

1. Wählen Sie eine bestimmte Version für das Asset aus, um sie in der Vorschau anzuzeigen, oder aktivieren Sie sie, damit sie in der Assets-Benutzeroberfläche angezeigt wird.

   ![select_version](assets/select_version.png)

1. Fügen Sie eine Beschriftung und Kommentare für die Version hinzu, um in der Assets-Benutzeroberfläche auf diese bestimmte Version zurückzusetzen.

   ![save_version](assets/save_version.png)

1. Um eine Vorschau für die Version zu generieren, tippen/klicken Sie auf **[!UICONTROL Versionsvorschau anzeigen]**.
1. To display this version in the Assets UI, select **[!UICONTROL Revert to this Version]**.
1. Um zwei Versionen miteinander zu vergleichen, gehen Sie zur Asset-Seite des Assets und tippen oder klicken Sie auf die Version, die mit der aktuellen Version verglichen werden soll.

   ![select_version_toVergleich](assets/select_version_tocompare.png)

1. Wählen Sie in der Timeline die Version aus, die Sie vergleichen wollen, und ziehen Sie den Schieberegler nach links, um diese Version über die aktuelle Version zu setzen.

   ![Compar_versions](assets/compare_versions.png)

### Starte a workflow on an asset {#starting-a-workflow-on-an-asset}

1. Navigieren Sie zum Speicherort des Assets, für das Sie einen Workflow beginnen möchten, und tippen/klicken Sie auf das Asset, um die Asset-Seite zu öffnen.
1. Tap/click the GlobalNav icon, and the choose **[!UICONTROL Timeline]** from the menu to display the timeline.

   ![timeline-1](assets/timeline-1.png)

1. Tap/click the **[!UICONTROL Actions]** (arrow) icon at the bottom to open the list of actions available for the asset.

   ![chlimage_1-252](assets/chlimage_1-252.png)

1. Tap/click **[!UICONTROL Start Workflow]** from the list.

   ![chlimage_1-253](assets/chlimage_1-253.png)

1. Wählen Sie im Dialogfeld **[!UICONTROL Workflow beginnen]** ein Workflow-Modell aus der Liste.

   ![chlimage_1-254](assets/chlimage_1-254.png)

1. (Optional) Geben Sie einen Titel für den Workflow an, der für den Verweis auf die Workflow-Instanz verwendet werden kann.

   ![chlimage_1-255](assets/chlimage_1-255.png)

1. Tippen/klicken Sie auf **[!UICONTROL Launch]** und dann zur Bestätigung auf **[!UICONTROL Fortfahren]**. Jeder Schritt des Workflows wird in der Timeline als Ereignis angezeigt.

   ![chlimage_1-256](assets/chlimage_1-256.png)

## Sammlungen {#collections}

Bei einer Sammlung handelt es sich um eine sortierte Gruppe von Assets. Anhand von Sammlungen können Assets von mehreren Benutzern gemeinsam verwendet werden.

* Eine Sammlung kann Assets aus verschiedenen Speicherorten enthalten, da sie nur Verweise zu diesen Assets aufweisen. Jede Sammlung hält die referenzielle Integrität von Assets aufrecht.
* Sie können Sammlungen für mehrere Benutzer mit unterschiedlichen Berechtigungsstufen wie Bearbeiten, Anzeigen usw. freigeben.

See [Managing Collections](/help/assets/manage-collections.md) for details on collection management.
