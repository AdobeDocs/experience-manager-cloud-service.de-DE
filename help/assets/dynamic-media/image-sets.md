---
title: Bildsets
description: Erfahren Sie, wie Sie in Dynamic Media mit Bildsets arbeiten..
feature: Bildsets
role: Business Practitioner
exl-id: 2eb71f24-73d9-4b5c-8605-923a0e3d1505
source-git-commit: d3ee23917eba4a2e4ae1f2bd44f5476d2ff7dce1
workflow-type: tm+mt
source-wordcount: '2050'
ht-degree: 64%

---

# Bildsets {#image-sets}

Über Bildsets erhalten Benutzer ein integriertes Anzeigeerlebnis, bei dem sie unterschiedliche Ansichten eines Elements durch Klicken auf eine Miniaturansicht anzeigen können. Mit Bildsets können Sie alternative Ansichten eines Elements darstellen. Dabei enthält der Viewer Zoomtools, mit denen Bilder genauer betrachtet werden können.

Bildsets werden durch ein Banner mit dem Wort `IMAGESET` gekennzeichnet. Darüber hinaus wird bei veröffentlichten Bildsets das Veröffentlichungsdatum (durch das Symbol **[!UICONTROL Welt]** gekennzeichnet) im Banner angezeigt. Außerdem wird das Datum der letzten Änderung angezeigt, wie durch das Symbol **[!UICONTROL Bleistift]** angegeben.

![chlimage_1-133](assets/chlimage_1-339.png)

Innerhalb des Bildsets können Sie auch Muster erstellen, indem Sie ein Bildset erstellen und Miniaturansichten hinzufügen.

Diese Anwendung ist nützlich, wenn Sie ein Element in einer anderen Farbe, einem anderen Muster oder einer anderen Oberfläche anzeigen möchten. Um ein Bildset mit Farbmustern zu erstellen, benötigen Sie ein Bild für jede Farbe, jedes Muster oder jede Fertigstellung, die/das den Benutzern angezeigt werden soll. Außerdem benötigen Sie eine Farb-, Muster- oder Endverarbeitungsvorlage für alle Farben, Muster oder Endverarbeitungen.

Beispiel: Sie möchten Bilder von Kappen darstellen, deren Schirme unterschiedliche Farben aufweisen: rot, grün und blau. In diesem Fall benötigen Sie drei Aufnahmen der gleichen Kappe. Sie brauchen eine Aufnahme mit einem roten Schirm, eine mit einem grünen Schirm und eine mit einem blauen Schirm. Außerdem brauchen Sie ein rotes, grünes und blaues Farbmuster. Die Farbmuster dienen als Miniaturansichten, auf die Benutzer im Musterset-Viewer klicken, um die Kappe mit rotem, grünem oder blauem Schirm anzuzeigen.

>[!NOTE]
>
>Weitere Informationen zur Assets-Benutzeroberfläche finden Sie unter [Verwalten von Assets mit der Touch-Benutzeroberfläche](/help/assets/manage-digital-assets.md).

## Schnellstart: Bildsets  {#quick-start-image-sets}

So schaffen Sie einen schnellen Einstieg:

1. Optional. [Erstellen Sie eine Stapelsatzvorgabe ](/help/assets/dynamic-media/batch-set-presets-dm.md) und wenden Sie sie auf einen neuen Ordner an, in den Ihre Rotationsset-Bilder hochgeladen werden.

   Eine Stapelsatzvorgabe kann Ihnen dabei helfen, die Erstellung Ihres Bild-Sets zu automatisieren.

   >[!IMPORTANT]
   >
   >Stapelsätze werden vom IPS (Image Production System) bei der Asset-Erfassung erstellt.

1. [Laden Sie die Primärquellen-Bilder für mehrere Ansichten hoch](#uploading-assets-in-image-sets).

   Laden Sie die Bilder für Ihre Bild-Sets hoch. Beachten Sie, dass Benutzer Bilder im Bildset-Viewer einzoomen können. Wählen Sie daher Ihre Bilder sorgfältig aus. Achten Sie darauf, dass die längste Seite der Bilder mindestens 2000 Pixel hat. Experience Manager Assets unterstützt viele Bilddateiformate. Es werden jedoch verlustfreie TIFF-, PNG- und EPS-Bilder empfohlen.

1. [Erstellen Sie Bildsets](#creating-image-sets).

   In Bildsets klicken Benutzer im Bildset-Viewer auf Miniaturansichten.

   Tippen oder klicken Sie zum Erstellen eines Bildsets in Assets auf **[!UICONTROL Erstellen > Bildsets]**. Fügen Sie anschließend Bilder hinzu und klicken Sie auf **[!UICONTROL Speichern]**.

   Siehe [Vorbereiten von Bildset-Assets auf das Hochladen und Hochladen von Dateien](#uploading-assets-in-image-sets).

   Siehe [Arbeiten mit Selektoren](/help/assets/dynamic-media/working-with-selectors.md).

1. Fügen Sie nach Bedarf [Bildset-Viewer-Vorgaben](/help/assets/dynamic-media/managing-viewer-presets.md) hinzu.

   Administratoren können Bildset-Viewer-Vorgaben erstellen oder ändern. Um das Bildset mit einer Viewer-Vorgabe anzuzeigen, wählen Sie das Bildset aus und wählen Sie in der Dropdownliste links die Option **[!UICONTROL Viewer]** aus.

   Informationen zum Erstellen oder Bearbeiten von Viewer-Vorgaben finden Sie unter **[!UICONTROL Tools > Assets > Viewer-Vorgaben]**.

1. (Optional) [Anzeigen von Bildsets](/help/assets/dynamic-media/image-sets.md#viewing-image-sets), die mit Stapelsatzvorgaben erstellt wurden.
1. [Zeigen Sie Bildsets in einer Vorschau an](/help/assets/dynamic-media/previewing-assets.md).

   Wählen Sie das Bildset aus, um dessen Vorschau anzuzeigen. Um das Bildset im ausgewählten Viewer zu untersuchen, tippen Sie auf die Miniaturansichtssymbole. Sie können verschiedene Viewer aus dem Menü **[!UICONTROL Viewer]** wählen, das in der Dropdown-Liste der linken Seitenleiste verfügbar ist.

1. [Veröffentlichen Sie Bildsets](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

   Beim Veröffentlichen eines Bildsets wird die URL- und Einbettungszeichenfolge aktiviert. Darüber hinaus müssen Sie alle [benutzerdefinierten Viewer-Vorgaben veröffentlichen](/help/assets/dynamic-media/managing-viewer-presets.md), die Sie erstellt haben. Standardmäßig vorhandene Viewer-Vorgaben sind bereits veröffentlicht.

1. [Verknüpfen Sie URLs mit einer Web-Anwendung](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) oder [betten Sie den Video- oder Bild-Viewer ein](/help/assets/dynamic-media/embed-code.md).

   Experience Manager Assets erstellt URL-Aufrufe für Bildsets und aktiviert diese, nachdem Sie die Bildsets veröffentlicht haben. Sie können diese URLs während der Asset-Vorschau kopieren. Alternativ können Sie sie auf Ihrer Website einbetten.

   Wählen Sie das Bildset und dann in der Dropdown-Liste der linken Leiste **[!UICONTROL Viewer]** aus.

   Siehe [Verknüpfen von Bildsets mit Web-Seiten](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) und [Einbetten des Video- oder Bild-Viewers](/help/assets/dynamic-media/embed-code.md).

Informationen zum Bearbeiten von Bildsets finden Sie unter [Bearbeiten von Bildsets](#editing-image-sets). . Darüber hinaus können Sie [Eigenschaften von Bildsets](/help/assets/manage-digital-assets.md#editing-properties) anzeigen und bearbeiten.

Wenn Sie beim Erstellen von Sets Probleme haben, lesen Sie den Abschnitt zu Bildern und Sets unter [Problembehandlung in Dynamic Media](/help/assets/dynamic-media/troubleshoot-dm.md#images-and-sets).

## Hochladen von Assets für Bild-Sets {#uploading-assets-in-image-sets}

Laden Sie zunächst die Bild-Assets für die Bild-Sets hoch. Beachten Sie, dass Benutzer Bilder im Bildset-Viewer einzoomen können. Wählen Sie daher Ihre Bilder sorgfältig aus. Stellen Sie sicher, dass die Bilder mindestens 2000 Pixel in der größten Größe haben, um optimale Zoomdetails zu erzielen. Mit Dynamic Media können Bilder mit einer Auflösung von jeweils bis zu 25 Megapixel gerendert werden. Sie können beispielsweise ein Bild mit 5000 x 5000 Megapixel oder eine beliebige andere Größenkombination mit bis zu 25 Megapixel verwenden.

Bildsets unterstützen zahlreiche Bilddateiformate, empfohlen werden aber verlustfreie TIFF-, PNG- und EPS-Bilder.

Sie laden Bilder für Bild­Sets genauso wie [alle anderen Assets in Assets](/help/assets/manage-digital-assets.md#uploading-assets) hoch.

### Vorbereiten von Bildset-Assets auf das Hochladen {#preparing-image-set-assets-for-upload}

Bevor Sie Bildsets erstellen, achten Sie darauf, dass die Bilder die richtige Größe und das richtige Format aufweisen.

Um ein Bildset mit mehreren Ansichten zu erstellen, benötigen Sie Bilder, die einen Artikel aus unterschiedlichen Blickwinkeln zeigen oder unterschiedliche Aspekte desselben Artikels darstellen. Das Ziel besteht darin, die wichtigen Funktionen eines Elements hervorzuheben, damit die Betrachter ein vollständiges Bild davon erhalten, wie es aussieht oder was es bewirkt.

Da Benutzer Bilder in Bildsets zoomen können, stellen Sie sicher, dass die Bilder mindestens 2000 Pixel in der größten Größe aufweisen. Experience Manager Assets unterstützt viele Bilddateiformate. Es werden jedoch verlustfreie TIFF-, PNG- und EPS-Bilder empfohlen.

>[!NOTE]
>
>Wenn Sie Miniaturansichten verwenden, um Produktmuster anzugeben, gehen Sie wie folgt vor:
>
>Erstellen Sie Vignetten oder andere Aufnahmen desselben Bildes, die es in verschiedenen Farben, Mustern oder Endverarbeitungen zeigen. Außerdem benötigen Sie Miniaturansichtsdateien, die den verschiedenen Farben, Mustern oder Endverarbeitungen entsprechen. Um beispielsweise Miniaturansichten in einem Bildset zu präsentieren, die eine Jacke in Schwarz, Braun und Grün anzeigen, benötigen Sie:
>
>* eine schwarze, braune und grüne Aufnahme der Jacke,
>* eine schwarze, braune und grüne Miniaturansicht


## Erstellen von Bildsets   {#creating-image-sets}

Sie können Bildsets über die Benutzeroberfläche oder die API erstellen.

>[!NOTE]
>
>Sie können Bildsets auch automatisch über [Stapelsatzvorgaben](/help/assets/dynamic-media/batch-set-presets-dm.md) erstellen.
>**Wichtig:** Stapelsätze werden vom IPS (Image Production System) bei der Asset-Erfassung erstellt.

Assets, die Sie Ihrem Set hinzufügen, werden automatisch in alphanumerischer Reihenfolge hinzugefügt. Sie können Assets nach dem Hinzufügen manuell neu anordnen oder sortieren.

>[!NOTE]
>
>Bildsets werden für Assets mit &quot;,&quot;(Komma) im Dateinamen nicht unterstützt.

**So erstellen Sie ein Bildset:**

1. Tippen Sie in Adobe Experience Manager auf das Experience Manager-Logo, um auf die globale Navigationskonsole zuzugreifen.
1. Tippen Sie auf **[!UICONTROL Navigation > Assets]**. Navigieren Sie zu dem Verzeichnis, an dem Sie ein Bildset erstellen möchten, und tippen Sie dann auf **[!UICONTROL Erstellen > Bildset]**, um die Seite mit dem Bildset-Editor zu öffnen.

   Sie können das Set auch in einem Ordner erstellen, der die gewünschten Assets enthält.

   ![6_5_imagesets-createpulldown](assets/6_5_imagesets-createpulldown.png)

1. Geben Sie im Bildset-Editor im Feld **[!UICONTROL Titel]** einen Namen für das Bildset ein. Der Name wird im Banner über dem Bildset angezeigt. Geben Sie optional eine Beschreibung ein.

   ![6_5_imageset-creating-newset](assets/6_5_imageset-creatingnewset.png)

1. Nehmen Sie eine der folgenden Aktionen vor:

   * Tippen Sie oben links auf der Seite des Bildset-Editors auf **[!UICONTROL Asset hinzufügen]**.

   * Tippen Sie in der Mitte des Bildset-Editors auf **[!UICONTROL Tippen, um die Asset-Auswahl zu öffnen]**.
   Tippen Sie, um die gewünschten Assets für das Bildset auszuwählen. Die ausgewählten Assets sind mit einem Häkchen versehen. Wenn Sie fertig sind, tippen Sie oben rechts auf der Seite auf **[!UICONTROL Wählen Sie]**.

   Mit der Asset-Auswahl können Sie nach Assets suchen, indem Sie ein Keyword eingeben und auf **[!UICONTROL Zurück]** tippen/klicken. Sie können auch Filter anwenden, um Ihre Suchergebnisse genauer abzustimmen. Sie können nach Pfad, Sammlung, Dateityp und Tag filtern. Wählen Sie den Filter aus und tippen Sie dann in der Symbolleiste auf das Symbol **[!UICONTROL Filter]** . Ändern Sie die Ansicht, indem Sie das Symbol „Ansicht“ tippen und dann **[!UICONTROL Spaltenansicht]**, **[!UICONTROL Kartenansicht]** oder **[!UICONTROL Listenansicht]** wählen.

   Siehe [Arbeiten mit Selektoren](/help/assets/dynamic-media/working-with-selectors.md).

   ![6_5_imageset_addingassets](assets/6_5_imageset-addingassets.png)

1. Assets, die Sie Ihrem Set hinzufügen, werden automatisch in alphanumerischer Reihenfolge hinzugefügt. Sie können Assets nach dem Hinzufügen manuell neu anordnen oder sortieren.

   Ziehen Sie bei Bedarf das Symbol Neu anordnen eines Assets rechts vom Dateinamen des Assets, um die Bilder in der Setliste nach oben oder unten anzuordnen.

   ![6_5_imageset-reorderassets](assets/6_5_imageset-reorderassets.png)

   Wenn Sie Miniaturansichten oder Muster hinzufügen möchten, klicken Sie auf das **Plussymbol** zum **Hinzufügen von Miniaturansichten** neben dem Bild und navigieren Sie zur gewünschten Miniaturansicht oder zum gewünschten Muster. Wenn Sie alle Bilder ausgewählt haben, klicken Sie auf **[!UICONTROL Speichern]**.

1. (Optional) Führen Sie einen der folgenden Schritte aus:

   * Wenn Sie ein Bild löschen möchten, wählen Sie das Bild aus und tippen Sie auf **[!UICONTROL Asset löschen]**.

   * Wenn Sie eine Vorgabe anwenden möchten, tippen Sie oben rechts auf **[!UICONTROL Voreingestellt]**. Wählen Sie anschließend eine Vorgabe aus, um sie auf alle Elemente gleichzeitig anzuwenden.
   >[!NOTE]
   >
   >Beim Erstellen des Bildsets können Sie die Miniaturansicht des Bildsets ändern. Alternativ können Sie Experience Manager die Miniaturansicht automatisch anhand der Assets im Bildset auswählen lassen. Um eine Miniaturansicht auszuwählen, tippen Sie auf der Seite &quot;Bildset-Editor&quot;über dem Feld &quot;Titel&quot;auf **[!UICONTROL Miniaturansicht ändern]**. Wählen Sie dann ein beliebiges Bild aus (Sie können auch zu anderen Ordnern navigieren, um nach Bildern zu suchen). Wenn Sie eine Miniaturansicht ausgewählt haben und möchten, dass der Experience Manager eine Miniaturansicht aus dem Bildset generiert, wählen Sie **[!UICONTROL Wechseln zu]** **[!UICONTROL Automatische Miniatur]**.

1. Klicken Sie auf **[!UICONTROL Speichern]**. Das neu erstellte Bildset wird in dem Ordner angezeigt, in dem es erstellt wurde.

## Anzeigen von Bildsets   {#viewing-image-sets}

Sie können Bildsets entweder in der Benutzeroberfläche oder automatisch über [Stapelsatzvorgaben](/help/assets/dynamic-media/batch-set-presets-dm.md) erstellen.

>[!IMPORTANT]
>
>Stapelsätze werden vom IPS [Image Production System] bei der Asset-Erfassung erstellt.

Mit Stapelsatzvorgaben erstellte Sets werden jedoch *nicht* in der Benutzeroberfläche angezeigt. Sie können diese Sets auf drei verschiedene Arten anzeigen. (Diese Methoden sind auch verfügbar, wenn Sie die Bildsets in der Benutzeroberfläche erstellt haben.)

* Öffnen Sie die Eigenschaften eines Assets. Die Eigenschaften zeigen an, auf welche Sets das ausgewählte Asset verweist oder welchen Sets es angehört. Um das gesamte Set anzuzeigen, tippen Sie auf den Namen des Sets.

   ![6_5_imageset-assetproperties](assets/6_5_imageset-assetproperties.png)

* Von einem zugehörigen Bild eines beliebigen Sets. Wählen Sie das Menü **[!UICONTROL Sets]** aus, um die Sets anzuzeigen, denen das Asset angehört.

   ![6_5_imageset-setspulldownmenu](assets/6_5_imageset-setspulldownmenu.png)

* Über die Suche können Sie **[!UICONTROL Filter]** auswählen, dann **[!UICONTROL Dynamic Media]** erweitern und **[!UICONTROL Sets]** auswählen.

   Die Suche gibt als Ergebnis Sets zurück, die in der Benutzeroberfläche manuell oder mit Stapelsatzvorgaben automatisch erstellt wurden. Bei automatisierten Sets wird die Suchabfrage mit &quot;Beginnt mit&quot;durchgeführt. Diese Suchkriterien unterscheiden sich von Experience Manager, der auf der Verwendung von &quot;Enthält&quot;basiert. Automatisierte Sets können nur durchsucht werden, wenn der Filter auf **[!UICONTROL Sets]** eingestellt ist.

   ![chlimage_1-134](assets/chlimage_1-134.png)

>[!NOTE]
>
>Sets können über die Benutzeroberfläche angezeigt werden, wie unter [Bearbeiten von Bildsets](#editing-image-sets) beschrieben.

## Bearbeiten von Bildsets   {#editing-image-sets}

Sie können verschiedene Bearbeitungsaufgaben für Bildsets ausführen, z. B. die folgenden:

* Fügen Sie dem Bildset Bilder hinzu.
* Ordnen Sie Bilder im Bildset neu an.
* Löschen Sie Assets im Bildset.
* Wenden Sie Viewer-Vorgaben an.
* Löschen Sie das Bildset.

**So bearbeiten Sie Bildsets:**

1. Führen Sie einen der folgenden Schritte aus:

   * Zeigen Sie mit der Maus auf ein Bildset-Asset und tippen Sie auf **[!UICONTROL Bearbeiten]** (Bleistiftsymbol).
   * Bewegen Sie den Mauszeiger über ein Bildset-Asset, tippen Sie auf **[!UICONTROL Auswählen]** (Häkchensymbol) und dann auf **[!UICONTROL Bearbeiten]** in der Symbolleiste.
   * Tippen Sie auf ein Bildset-Asset und dann in der Symbolleiste auf **[!UICONTROL Bearbeiten]** (Stiftsymbol).

1. Führen Sie eine der folgenden Aktionen aus, um die Bilder im Bildset zu bearbeiten:

   * Ziehen Sie ein Bild, wenn Sie ein Asset an einer neuen Position anordnen möchten (zum Verschieben von Elementen wählen Sie das Symbol zum Neuanordnen).
   * Um Elemente in auf- oder absteigender Reihenfolge zu sortieren, klicken Sie auf die Spaltenüberschrift.
   * Um ein Asset hinzuzufügen oder ein vorhandenes Asset zu aktualisieren, klicken Sie auf **[!UICONTROL Asset hinzufügen]**. Navigieren Sie zu einem Asset, wählen Sie es aus und tippen Sie oben rechts auf **[!UICONTROL Auswählen]**.

      >[!NOTE]
      >
      >Wenn Sie das Bild löschen, das der Experience Manager für die Miniaturansicht verwendet, indem er es durch ein anderes ersetzt, wird das Original-Asset weiterhin angezeigt.
   * Klicken oder tippen Sie zum Löschen eines Assets auf **[!UICONTROL Asset löschen]**.
   * Um eine Vorgabe anzuwenden, tippen Sie oben rechts auf der Seite auf **[!UICONTROL Vorgabe]** und wählen Sie eine Viewer-Vorgabe aus.
   * Um eine Miniaturansicht hinzuzufügen oder zu ändern, wählen Sie die Miniaturansicht rechts neben dem Asset. Navigieren Sie zur neuen Miniaturansicht oder zum neuen Farbmuster-Asset, wählen Sie es aus und tippen Sie dann auf **[!UICONTROL Auswählen]**.
   * Um ein ganzes Bildset zu löschen, navigieren Sie zum Bildset, wählen Sie es aus und klicken Sie auf **[!UICONTROL Löschen]**.

   >[!NOTE]
   >
   >Sie können die Bilder in einem Bildset bearbeiten. Navigieren Sie zum Satz und tippen Sie in der linken Leiste auf **[!UICONTROL Setmitglieder]** . Um das Bearbeitungsfenster zu öffnen, tippen Sie auf das Stiftsymbol eines Assets.

1. Tippen Sie auf **[!UICONTROL Speichern]**, wenn Sie die Bearbeitung abgeschlossen haben.

## Anzeigen von Bildsets in einer Vorschau   {#previewing-image-sets}

Weitere Informationen finden Sie im Abschnitt [Asset-Vorschau](/help/assets/dynamic-media/previewing-assets.md).

## Veröffentlichen von Bildsets   {#publishing-image-sets}

Siehe [Veröffentlichen von Assets](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).
