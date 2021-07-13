---
title: Bildsets
description: Erfahren Sie, wie Sie in Dynamic Media mit Bildsets arbeiten..
feature: Bildsets
role: User
exl-id: 2eb71f24-73d9-4b5c-8605-923a0e3d1505
source-git-commit: 1d42305b6a597dc95bff8b34eee8279eb0e511f3
workflow-type: tm+mt
source-wordcount: '2044'
ht-degree: 76%

---

# Bildsets {#image-sets}

Über Bildsets erhalten Benutzer ein integriertes Anzeigeerlebnis, bei dem sie unterschiedliche Ansichten eines Elements durch Klicken auf eine Miniaturansicht anzeigen können. Mit Bildsets können Sie alternative Ansichten eines Elements darstellen. Dabei enthält der Viewer Zoomtools, mit denen Bilder genauer betrachtet werden können.

Bildsets werden durch ein Banner mit dem Wort `IMAGESET` gekennzeichnet. Bei veröffentlichten Bildsets befindet sich das Veröffentlichungsdatum, das durch das Symbol **[!UICONTROL Welt]** gekennzeichnet wird, im Banner. Außerdem wird das letzte Änderungsdatum angezeigt, das durch das Symbol **[!UICONTROL Bleistift]** gekennzeichnet wird.

![chlimage_1-133](assets/chlimage_1-339.png)

Innerhalb des Bildsets können Sie auch Muster erstellen, indem Sie ein Bildset erstellen und Miniaturansichten hinzufügen.

Dies ist nützlich, wenn Sie einen Artikel in einer anderen Farbe, einem anderen Muster oder mit anderer Endverarbeitung darstellen möchten. Um ein Bildset mit Farbmustern zu erstellen, benötigen Sie ein Bild für alle Farben, Muster oder Endverarbeitungen, die den Benutzern dargestellt werden sollen. Außerdem benötigen Sie eine Farb-, Muster- oder Endverarbeitungsvorlage für alle Farben, Muster oder Endverarbeitungen.

Beispiel: Sie möchten Bilder von Kappen darstellen, deren Schirme unterschiedliche Farben aufweisen: rot, grün und blau. In diesem Fall benötigen Sie drei Aufnahmen der gleichen Kappe. Sie brauchen eine Aufnahme mit einem roten Schirm, eine mit einem grünen Schirm und eine mit einem blauen Schirm. Außerdem brauchen Sie ein rotes, grünes und blaues Farbmuster. Die Farbmuster dienen als Miniaturansichten, auf die Benutzer im Musterset-Viewer klicken, um die Kappe mit rotem, grünem oder blauem Schirm anzuzeigen.

>[!NOTE]
>
>Informationen zur Benutzeroberfläche &quot;Assets&quot;finden Sie unter [Verwalten von Assets mit der Touch-Benutzeroberfläche](/help/assets/manage-digital-assets.md).

## Schnellstart: Bildsets   {#quick-start-image-sets}

So schaffen Sie einen schnellen Einstieg:

1. Optional. [Erstellen Sie eine Stapelsatzvorgabe](/help/assets/dynamic-media/batch-set-presets-dm.md) und wenden Sie sie auf einen neuen Ordner an, in den Ihre Rotationsset-Bilder hochgeladen werden.

   Eine Stapelsatzvorgabe kann Ihnen dabei helfen, die Erstellung Ihres Bildsets zu automatisieren.

   >[!IMPORTANT]
   >
   >Stapelsätze werden vom IPS (Image Production System) bei der Asset-Erfassung erstellt.

1. [Laden Sie die Primärquellen-Bilder für mehrere Ansichten hoch](#uploading-assets-in-image-sets).

   Laden Sie die Bilder für Ihre Bildsets hoch. Denken Sie daran, dass Benutzer im Bildset-Viewer auf Bilder zoomen können. Wählen Sie daher die Bilder sorgfältig aus. Achten Sie darauf, dass die längste Seite der Bilder mindestens 2000 Pixel hat. Experience Manager Assets unterstützt zahlreiche Bilddateiformate, empfohlen werden aber verlustfreie TIFF-, PNG- und EPS-Bilder.

1. [Erstellen Sie Bildsets](#creating-image-sets).

   In Bildsets klicken Benutzer im Bildset-Viewer auf Miniaturansichten.

   Um ein Bildset in Assets zu erstellen, wählen Sie **[!UICONTROL Erstellen]** > **[!UICONTROL Bildsets]** aus. Fügen Sie anschließend Bilder hinzu und klicken Sie auf **[!UICONTROL Speichern]**.

   Siehe [Vorbereiten von Bildset-Assets für das Hochladen und Hochladen Ihrer Dateien](#uploading-assets-in-image-sets).

   Siehe [Arbeiten mit Selektoren](/help/assets/dynamic-media/working-with-selectors.md).

1. Fügen Sie nach Bedarf [Bildset-Viewer-Vorgaben](/help/assets/dynamic-media/managing-viewer-presets.md) hinzu.

   Administratoren können Bildset-Viewer-Vorgaben erstellen oder ändern. Wählen Sie zum Anzeigen Ihres Bildsets mit einer Viewer-Vorgabe das Bildset und links in der Leiste über die Dropdown-Liste die Option **[!UICONTROL Viewer]**.

   Informationen zum Erstellen oder Bearbeiten von Viewer-Vorgaben finden Sie unter **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Viewer-Vorgaben]**.

1. (Optional) [Bildsets anzeigen](/help/assets/dynamic-media/image-sets.md#viewing-image-sets), die mit Stapelsatzvorgaben erstellt wurden.
1. [Zeigen Sie Bildsets in einer Vorschau an](/help/assets/dynamic-media/previewing-assets.md).

   Wählen Sie das Bildset aus, um dessen Vorschau anzuzeigen. Um das Bildset im ausgewählten Viewer zu untersuchen, wählen Sie die Miniaturansichtssymbole aus. Sie können verschiedene Viewer im Menü **[!UICONTROL Viewer]** auswählen, das Sie auf der linken Schiene über die Dropdown-Liste aufrufen können.

1. [Veröffentlichen Sie Bildsets](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

   Beim Veröffentlichen eines Bildsets wird die URL- und Einbettungszeichenfolge aktiviert. Darüber hinaus müssen Sie alle [benutzerdefinierten Viewer-Vorgaben veröffentlichen](/help/assets/dynamic-media/managing-viewer-presets.md), die Sie erstellt haben. Standardmäßig vorhandene Viewer-Vorgaben sind bereits veröffentlicht.

1. [Verknüpfen Sie URLs mit einer Web-Anwendung](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) oder [betten Sie den Video- oder Bild-Viewer ein](/help/assets/dynamic-media/embed-code.md).

   Experience Manager Assets erstellt URL-Aufrufe für Bildsets und aktiviert diese, nachdem Sie die Bildsets veröffentlicht haben. Sie können diese URLs während der Asset-Vorschau kopieren. Sie können sie alternativ in Ihre Website einbetten.

   Wählen Sie das Bildset und dann links auf der linken Schiene über die Dropdown-Liste die Option **[!UICONTROL Viewer]**.

   Siehe [Verknüpfen eines Bildsets mit einer Web-Seite](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) und [Einbetten des Video- oder Bild-Viewers](/help/assets/dynamic-media/embed-code.md).

Informationen zum Bearbeiten von Bildsets finden Sie unter [Bearbeiten von Bildsets](#editing-image-sets). Darüber hinaus können Sie [Eigenschaften von Bildsets](/help/assets/manage-digital-assets.md#editing-properties) anzeigen und bearbeiten.

Wenn Sie beim Erstellen von Sets Probleme haben, lesen Sie Bilder und Sets in [Fehlerbehebung für Dynamic Media](/help/assets/dynamic-media/troubleshoot-dm.md#images-and-sets).

## Hochladen von Assets für Bildsets {#uploading-assets-in-image-sets}

Laden Sie zunächst die Bild-Assets für die Bildsets hoch. Denken Sie daran, dass Benutzer im Bildset-Viewer auf Bilder zoomen können. Wählen Sie daher die Bilder sorgfältig aus. Achten Sie darauf, dass die längste Seite der Bilder mindestens 2.000 Pixel hat, um optimale Zoom-Details zu erzielen. Mit Dynamic Media können Bilder mit einer Auflösung von jeweils bis zu 25 Megapixel gerendert werden. Sie können beispielsweise ein Bild mit 5000 x 5000 Megapixel oder eine beliebige andere Größenkombination mit bis zu 25 Megapixel verwenden.

Bildsets unterstützen zahlreiche Bilddateiformate, empfohlen werden aber verlustfreie TIFF-, PNG- und EPS-Bilder.

Sie laden Bilder für Bild­Sets genauso wie [alle anderen Assets in Assets](/help/assets/manage-digital-assets.md#uploading-assets) hoch.

### Vorbereiten von Bildset-Assets für das Hochladen {#preparing-image-set-assets-for-upload}

Bevor Sie Bildsets erstellen, achten Sie darauf, dass die Bilder die richtige Größe und das richtige Format aufweisen.

Um ein Bildset mit mehreren Ansichten zu erstellen, benötigen Sie Bilder, die einen Artikel aus unterschiedlichen Blickwinkeln zeigen oder unterschiedliche Aspekte desselben Artikels darstellen. Ziel ist es, die wichtigen Merkmale eines Artikels so hervorzuheben, dass Benutzer einen umfassen Einblick in das Aussehen oder die Funktion des Gegenstands erhalten.

Stellen Sie sicher, dass die längste Seite der Bilder in Bildsets mindestens 2.000 Pixel hat, da Benutzer sie einzoomen können. Experience Manager Assets unterstützt zahlreiche Bilddateiformate, empfohlen werden aber verlustfreie TIFF-, PNG- und EPS-Bilder.

>[!NOTE]
>
>Wenn Sie Miniaturansichten verwenden, um Produktmuster anzuzeigen, führen Sie die folgenden Schritte aus:
>
>Erstellen Sie Vignetten oder unterschiedliche Aufnahmen desselben Bildes, in denen dieses in verschiedenen Farben, Mustern oder Endverarbeitungen dargestellt wird. Außerdem benötigen Sie Miniaturansichtsdateien, die den verschiedenen Farben, Mustern oder Endverarbeitungen entsprechen. Um beispielsweise Miniaturansichten in einem Bildset zu präsentieren, die eine Jacke in Schwarz, Braun und Grün anzeigen, benötigen Sie:
>
>* eine schwarze, braune und grüne Aufnahme der Jacke,
>* eine schwarze, braune und grüne Miniaturansicht


## Erstellen Sie Bildsets {#creating-image-sets}

Sie können Bildsets über die Benutzeroberfläche oder die API erstellen.

>[!NOTE]
>
>Sie können Bildsets auch automatisch über [Stapelsatzvorgaben](/help/assets/dynamic-media/batch-set-presets-dm.md) erstellen.
>**Wichtig:** Stapelsätze werden vom IPS (Image Production System) bei der Asset-Erfassung erstellt.

Assets, die Sie Ihrem Set hinzufügen, werden automatisch in alphanumerischer Reihenfolge hinzugefügt. Sie können die Anordnung oder Sortierung der Assets manuell ändern, nachdem sie hinzugefügt wurden.

>[!NOTE]
>
>Bildsets werden nicht unterstützt, wenn Assets im Dateinamen ein „,“ (Komma) enthalten.

**So erstellen Sie Bildsets:**

1. Wählen Sie in Adobe Experience Manager das Experience Manager-Logo aus, um auf die globale Navigationskonsole zuzugreifen.
1. Tippen Sie auf **[!UICONTROL Navigation]** > **[!UICONTROL Assets]**. Navigieren Sie zu der Stelle, an der Sie ein Bildset erstellen möchten, und navigieren Sie dann zu **[!UICONTROL Erstellen]** > **[!UICONTROL Bildset]** , um die Seite &quot;Bildset-Editor&quot;zu öffnen.

   Sie können das Set auch in einem Ordner erstellen, der die gewünschten Assets enthält.

   ![6_5_imagesets-createpulldown](assets/6_5_imagesets-createpulldown.png)

1. Geben Sie im Bildset-Editor im Feld **[!UICONTROL Titel]** einen Namen für das Bildset ein. Der Name wird im Banner über dem Bildset angezeigt. Geben Sie optional eine Beschreibung ein.

   ![6_5_imageset-creating-newset](assets/6_5_imageset-creatingnewset.png)

1. Nehmen Sie eine der folgenden Aktionen vor:

   * Wählen Sie links oben auf der Seite &quot;Bildset-Editor&quot;die Option **[!UICONTROL Asset hinzufügen]**.

   * Wählen Sie in der Mitte des Bildset-Editors die Option **[!UICONTROL Tippen, um die Asset-Auswahl]** zu öffnen.
   Tippen Sie, um die gewünschten Assets für das Bildset auszuwählen. Die ausgewählten Assets sind mit einem Häkchen versehen. Wenn Sie fertig sind, wählen Sie in der Nähe der oberen rechten Ecke der Seite **[!UICONTROL Auswählen]**.

   Mit der Asset-Auswahl können Sie nach Assets suchen, indem Sie einen Suchbegriff eingeben und **[!UICONTROL Return]** auswählen. Sie können auch Filter anwenden, um Ihre Suchergebnisse genauer abzustimmen. Sie können nach Pfad, Sammlung, Dateityp und Tag filtern. Wählen Sie den Filter aus und wählen Sie dann in der Symbolleiste das Symbol **[!UICONTROL Filter]** aus. Ändern Sie die Ansicht, indem Sie das Symbol Ansicht auswählen und **[!UICONTROL Spaltenansicht]**, **[!UICONTROL Kartenansicht]** oder **[!UICONTROL Listenansicht]** auswählen.

   Siehe [Arbeiten mit Selektoren](/help/assets/dynamic-media/working-with-selectors.md).

   ![6_5_imageset_addingassets](assets/6_5_imageset-addingassets.png)

1. Assets, die Sie Ihrem Set hinzufügen, werden automatisch in alphanumerischer Reihenfolge hinzugefügt. Sie können die Anordnung oder Sortierung der Assets manuell ändern, nachdem sie hinzugefügt wurden.

   Ziehen Sie gegebenenfalls das Symbol „Neu anordnen“ rechts neben den Dateinamen des Assets, um Bilder in der Setliste nach oben oder unten zu bewegen.

   ![6_5_imageset-reorderassets](assets/6_5_imageset-reorderassets.png)

   Wenn Sie Miniaturansichten oder Muster hinzufügen möchten, klicken Sie auf das **Plussymbol** zum **Hinzufügen von Miniaturansichten** neben dem Bild und navigieren Sie zur gewünschten Miniaturansicht oder zum gewünschten Muster. Wenn Sie alle Bilder ausgewählt haben, klicken Sie auf **[!UICONTROL Speichern]**.

1. (Optional) Führen Sie einen der folgenden Schritte aus:

   * Um ein Bild zu löschen, wählen Sie das Bild aus und klicken Sie auf **[!UICONTROL Asset löschen]**.

   * Um eine Vorgabe anzuwenden, wählen Sie rechts oben auf der Seite **[!UICONTROL Voreinstellung]** und dann eine Vorgabe aus, die auf alle Assets gleichzeitig angewendet werden soll.
   >[!NOTE]
   >
   >Beim Erstellen des Bildsets können Sie die Miniaturansicht des Bildsets ändern. Alternativ können Sie festlegen, dass Experience Manager die Miniaturansicht automatisch anhand der im Bildset enthaltenen Assets auswählt. Um eine Miniaturansicht auszuwählen, wählen Sie auf der Seite Bildset-Editor **[!UICONTROL Miniaturansicht ändern]** über dem Feld Titel aus. Wählen Sie dann ein beliebiges Bild aus (Sie können auch zu anderen Ordnern navigieren, um nach Bildern zu suchen). Wenn Sie eine Miniaturansicht ausgewählt haben und dann mit Experience Manager aus dem Bildset eine generieren möchten, wählen Sie **[!UICONTROL Zu automatischer]** **[!UICONTROL Miniatur wechseln]**.

1. Klicken Sie auf **[!UICONTROL Speichern]**. Das neu erstellte Bildset wird in dem Ordner angezeigt, in dem es erstellt wurde.

## Anzeigen von Bildsets {#viewing-image-sets}

Sie können Bildsets entweder in der Benutzeroberfläche oder automatisch über [Stapelsatzvorgaben](/help/assets/dynamic-media/batch-set-presets-dm.md) erstellen.

>[!IMPORTANT]
>
>Stapelsätze werden vom IPS [Image Production System] bei der Asset-Erfassung erstellt.

Mit Stapelsatzvorgaben erstellte Sets werden jedoch *nicht* in der Benutzeroberfläche angezeigt. Sie können diese Sets auf drei verschiedene Arten anzeigen. (Diese Methoden sind auch verfügbar, wenn Sie die Bildsets in der Benutzeroberfläche erstellt haben.)

* Öffnen Sie die Eigenschaften eines Assets. Die Eigenschaften zeigen an, auf welche Sets das ausgewählte Asset verweist oder welchen Sets es angehört. Um den gesamten Satz anzuzeigen, wählen Sie den Namen des Sets aus.

   ![6_5_imageset-assetproperties](assets/6_5_imageset-assetproperties.png)

* Von einem zugehörigen Bild eines beliebigen Sets. Wählen Sie das Menü **[!UICONTROL Sets]** aus, um die Sets anzuzeigen, denen das Asset angehört.

   ![6_5_imageset-setspulldownmenu](assets/6_5_imageset-setspulldownmenu.png)

* Über die Suche können Sie **[!UICONTROL Filter]** auswählen, dann **[!UICONTROL Dynamic Media]** erweitern und **[!UICONTROL Sets]** auswählen.

   Die Suche gibt als Ergebnis Sets zurück, die in der Benutzeroberfläche manuell oder mit Stapelsatzvorgaben automatisch erstellt wurden. Bei automatisierten Sets wird die Abfrage mit „Beginnt mit“ ausgeführt. Diese Suchkriterien unterscheiden sich von Experience Manager, der auf der Verwendung von „Enthält“ basiert. Automatisierte Sets können nur durchsucht werden, wenn der Filter auf **[!UICONTROL Sets]** eingestellt ist.

   ![chlimage_1-134](assets/chlimage_1-134.png)

>[!NOTE]
>
>Sets können über die Benutzeroberfläche angezeigt werden, wie unter [Bearbeiten von Bildsets](#editing-image-sets) beschrieben.

## Bearbeiten von Bildsets {#editing-image-sets}

Sie können mehrere Bearbeitungsaufgaben für Bildsets ausführen, z. B. die folgenden:

* Fügen Sie dem Bildset Bilder hinzu.
* Ordnen Sie Bilder im Bildset neu an.
* Löschen Sie Assets im Bildset.
* Wenden Sie Viewer-Vorgaben an.
* Löschen Sie das Bildset.

**So bearbeiten Sie Bildsets:**

1. Führen Sie einen der folgenden Schritte aus:

   * Bewegen Sie den Mauszeiger über ein Bildset-Asset und wählen Sie **[!UICONTROL Bearbeiten]** (Stiftsymbol).
   * Bewegen Sie den Mauszeiger über ein Bildset-Asset, wählen Sie **[!UICONTROL Auswählen]** (Häkchensymbol) und klicken Sie dann in der Symbolleiste auf **[!UICONTROL Bearbeiten]**.
   * Tippen Sie auf ein Bildset-Asset und wählen Sie dann **[!UICONTROL Bearbeiten]** (Bleistiftsymbol) in der Symbolleiste aus.

1. Führen Sie eine der folgenden Aktionen aus, um die Bilder im Bildset zu bearbeiten:

   * Ziehen Sie ein Bild, wenn Sie ein Asset an einer neuen Position anordnen möchten (zum Verschieben von Elementen wählen Sie das Symbol zum Neuanordnen).
   * Um Elemente in auf- oder absteigender Reihenfolge zu sortieren, klicken Sie auf die Spaltenüberschrift.
   * Um ein Asset hinzuzufügen oder ein vorhandenes Asset zu aktualisieren, klicken Sie auf **[!UICONTROL Asset hinzufügen]**. Navigieren Sie zu einem Asset, wählen Sie es aus und klicken Sie dann oben rechts auf der Seite auf **[!UICONTROL Auswählen]** .

      >[!NOTE]
      >
      >Wenn Sie das in Experience Manager als Miniaturansicht verwendete Bild löschen und durch ein anderes ersetzen, wird das Original-Asset weiterhin angezeigt.
   * Um ein Asset zu löschen, wählen Sie es aus und klicken Sie auf **[!UICONTROL Asset löschen]**.
   * Um eine Vorgabe anzuwenden, wählen Sie rechts oben auf der Seite **[!UICONTROL Vorgabe]** und dann eine Viewer-Vorgabe aus.
   * Um eine Miniaturansicht hinzuzufügen oder zu ändern, wählen Sie die Miniaturansicht rechts neben dem Asset. Navigieren Sie zur neuen Miniaturansicht oder zum neuen Musterasset, wählen Sie es aus und wählen Sie dann **[!UICONTROL Auswählen]** aus.
   * Um ein ganzes Bildset zu löschen, navigieren Sie zum Bildset, wählen Sie es aus und klicken Sie auf **[!UICONTROL Löschen]**.

   >[!NOTE]
   >
   >Sie können die Bilder in einem Bildset bearbeiten. Navigieren Sie zum Satz und wählen Sie in der linken Leiste **[!UICONTROL Setmitglieder]** aus. Um das Bearbeitungsfenster zu öffnen, wählen Sie das Stiftsymbol eines Assets aus.

1. Tippen Sie auf **[!UICONTROL Speichern]**, wenn Sie die Bearbeitung abgeschlossen haben.

## Zeigen Sie Bildsets in einer Vorschau an {#previewing-image-sets}

Siehe [Asset-Vorschau](/help/assets/dynamic-media/previewing-assets.md).

## Veröffentlichen von Bildsets   {#publishing-image-sets}

Siehe [Assets veröffentlichen](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).
