---
title: Gemischte Mediensets
description: In diesem Abschnitt erfahren Sie, wie Sie gemischte Mediensets in Dynamic Media verwenden..
feature: Gemischte Mediensets
topic: Geschäftspraktiker
translation-type: tm+mt
source-git-commit: 0f2b7176b44bb79bdcd1cecf6debf05bd652a1a1
workflow-type: tm+mt
source-wordcount: '1469'
ht-degree: 75%

---


# Gemischte Mediensets {#mixed-media-sets}

Mit gemischten Mediensets können Sie eine Mischung aus Bildern, Bildsets, Rotationssets und Videos in einer Präsentation bereitstellen.

Gemischte Mediensets werden durch ein Banner mit dem Wort **[!UICONTROL MixedMediaSet]** gekennzeichnet. Darüber hinaus wird bei veröffentlichten Sets für gemischte Medien das Veröffentlichungsdatum (durch das **[!UICONTROL Welt]**-Symbol gekennzeichnet) zusammen mit dem Datum der letzten Änderung (durch das **[!UICONTROL Bleistift]**-Symbol gekennzeichnet) im Banner angezeigt.

![chlimage_1-137](assets/chlimage_1-348.png)

>[!NOTE]
>
>Weitere Informationen zur Assets-Benutzeroberfläche finden Sie unter [Verwalten von Assets mit der Touch-Benutzeroberfläche](/help/assets/manage-digital-assets.md).

## Schnellstartanleitungen: Gemischte Mediensets {#quick-start-mixed-media-sets}

Führen Sie die folgenden Schritte aus, um den schnellen Einstieg in die Arbeit mit gemischten Mediensets zu schaffen:

1. [Laden Sie die Assets hoch.](#uploading-assets)

   Laden Sie zunächst die Bilder und Videos für Ihre gemischten Mediensets hoch. Erstellen Sie bei Bedarf [Bildsets](/help/assets/dynamic-media/image-sets.md) und [Rotationssets](/help/assets/dynamic-media/spin-sets.md). Da die Benutzer im Viewer für gemischte Mediensets Bilder heranzoomen können, sollten Sie beim Auswählen von Bildern sicherstellen, dass das Zoomen berücksichtigt wird. Achten Sie darauf, dass die längste Seite der Bilder mindestens 2.000 Pixel hat.

1. [Erstellen Sie gemischte Mediensets.](#creating-mixed-media-sets)

   Zum Erstellen eines gemischten Mediensets tippen Sie auf der Seite „Assets“ auf **[!UICONTROL Erstellen > Gemischtes Medienset]**. Benennen Sie dann das Set, wählen Sie die Assets und die Reihenfolge der Bilder aus.

   Siehe [Arbeiten mit Selektoren](/help/assets/dynamic-media/working-with-selectors.md).

1. Richten Sie bei Bedarf [Viewer-Vorgaben für das gemischte Medienset](/help/assets/dynamic-media/managing-viewer-presets.md) ein.

   Administratoren können Viewer-Vorgaben für gemischte Mediensets erstellen oder ändern. Um die gemischten Medien mit einer Viewer-Vorgabe anzuzeigen, wählen Sie das gemischte Medienset aus und wählen Sie im Dropdown-Menü in der linken Seitenleiste die Option **[!UICONTROL Viewer]** aus.

   Informationen zum Erstellen oder Bearbeiten von Viewer-Vorgaben finden Sie unter **[!UICONTROL Werkzeuge > Assets > Viewer-Vorgaben]**.

   Siehe [Hinzufügen und Bearbeiten von Viewer-Vorgaben.](/help/assets/dynamic-media/managing-viewer-presets.md)

1. [Zeigen Sie eine Vorschau der gemischten Mediensets an.](#previewing-mixed-media-sets)

   Wenn Sie das gemischte Medienset auswählen, können Sie eine Vorschau davon anzeigen. Um Ihr gemischtes Medienset im ausgewählten Viewer zu überprüfen, klicken Sie auf die Miniaturansicht-Symbole. Sie können verschiedene Viewer aus dem Menü **[!UICONTROL Viewer]** wählen, das Sie links in der Leiste über die Dropdown-Liste aufrufen können.

1. [Veröffentlichen Sie gemischte Mediensets.](#publishing-mixed-media-sets)

   Beim Veröffentlichen eines gemischten Mediensets wird die URL- und Integrationszeichenfolge aktiviert. Außerdem müssen Sie [die Viewer-Vorgabe veröffentlichen](/help/assets/dynamic-media/managing-viewer-presets.md#publishing-viewer-presets).

1. [Verknüpfen Sie URLs mit einer Web-Anwendung](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) oder [betten Sie den Video- oder Bild-Viewer ein](/help/assets/dynamic-media/embed-code.md).

   Adobe Experience Manager Assets erstellt URL-Aufrufe für gemischte Mediensets und aktiviert sie, nachdem Sie die gemischten Mediensets veröffentlicht haben. Sie können diese URLs während der Asset-Vorschau kopieren. Alternativ dazu können Sie sie in Ihre Website einbetten.

   Markieren Sie dazu das gemischte Medienset und klicken Sie dann im Dropdown-Menü in der linken Seitenleiste auf **[!UICONTROL Viewer]**.

   Siehe [Verknüpfen von gemischten Mediensets mit Web-Seiten](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) und [Einbetten des Video- oder Bild-Viewers](/help/assets/dynamic-media/embed-code.md).

Bei Bedarf können Sie [Gemischte Mediensets](#editing-mixed-media-sets) bearbeiten. Darüber hinaus können Sie [Eigenschaften von gemischten Mediensets](/help/assets/manage-digital-assets.md#editing-properties) anzeigen und ändern.

>[!NOTE]
>
>Unterstützung beim Erstellen von Sets erhalten Sie unter [Problembehandlung in Dynamic Media](/help/assets/dynamic-media/troubleshoot-dm.md).

## Hochladen von Assets {#uploading-assets}

Laden Sie zunächst die Bilder und Videos für Ihre gemischten Mediensets hoch. Denken Sie daran, dass Benutzer Bilder im Viewer für gemischte Mediensets heranzoomen können. Wählen Sie daher Bilder mit dieser Zoommöglichkeit aus. Achten Sie darauf, dass die längste Seite der Bilder mindestens 2.000 Pixel hat.

Wenn Sie dem gemischten Medienset außerdem Rotationssets oder Bildsätze hinzufügen möchten, erstellen Sie diese ebenfalls.

## Erstellen von gemischten Mediensets  {#creating-mixed-media-sets}

Sie können Ihrem gemischten Medienset Bilder, Bildsets, Rotationssets und Videos hinzufügen. Achten Sie darauf, dass die Dateien, Bildsets und Rotationssets veröffentlicht werden können, bevor Sie diese dem gemischten Medienset hinzufügen.

Assets, die Sie Ihrem Set hinzufügen, werden automatisch in alphanumerischer Reihenfolge hinzugefügt. Sie können Assets nach dem Hinzufügen manuell neu anordnen oder sortieren.

**So erstellen Sie ein gemischtes Medienset**

1. Navigieren Sie in Assets an die Stelle, an der Sie ein gemischtes Medienset erstellen möchten, und klicken Sie auf **[!UICONTROL Erstellen]**. Wählen Sie dann **[!UICONTROL Gemischtes Medienset]** aus. Sie können das Set auch in einem Ordner erstellen, der die gewünschten Assets enthält. Der Editor für gemischte Mediensets wird angezeigt.

   ![chlimage_1-138](assets/chlimage_1-349.png)

1. Geben Sie im Editor für gemischte Mediensets im Feld **[!UICONTROL Titel]** einen Namen für das gemischte Medienset ein. Der Name wird im Banner über dem Set für gemischte Medien angezeigt. Geben Sie optional eine Beschreibung ein.

   ![chlimage_1-139](assets/chlimage_1-350.png)

   >[!NOTE]
   >
   >Beim Erstellen des gemischten Mediensets können Sie die Miniaturansicht des gemischten Mediensets ändern oder zulassen, dass Experience Manager die Miniaturansicht automatisch anhand der Assets im gemischten Mediensatz auswählen. Um eine Miniaturansicht auszuwählen, klicken Sie auf **[!UICONTROL Miniatur ändern]** und wählen Sie ein beliebiges Bild aus. (Sie können auch in anderen Ordnern nach Bildern suchen.) Wenn Sie eine Miniaturansicht ausgewählt haben und dann entscheiden möchten, dass Experience Manager eine aus dem gemischten Mediensatz generieren soll, wählen Sie **[!UICONTROL Zu Automatische Miniaturansicht]** wechseln.

1. Um Assets auszuwählen, die Sie in Ihr gemischtes Medienset aufnehmen möchten, tippen Sie auf die Asset-Auswahl. Wählen Sie sie aus und klicken Sie auf **[!UICONTROL Auswählen]**.

   Mit dem Asset-Selektor können Sie nach Assets suchen, indem Sie ein Keyword eingeben und auf **[!UICONTROL Eingabe]** tippen. Sie können auch Filter anwenden, um Ihre Suchergebnisse genauer abzustimmen. Sie können nach Pfad, Sammlung, Dateityp und Tag filtern. Wählen Sie den Filter aus und tippen Sie in der Symbolleiste auf das Symbol **[!UICONTROL Filter]**. Ändern Sie die Ansicht, indem Sie das Symbol **[!UICONTROL Ansicht]** und dann die **[!UICONTROL Listenansicht]**, **[!UICONTROL Spaltenansicht]** oder **[!UICONTROL Kartenansicht]** auswählen.

   Siehe [Arbeiten mit Selektoren](/help/assets/dynamic-media/working-with-selectors.md).

   ![chlimage_1-140](assets/chlimage_1-351.png)

1. Ordnen Sie die Assets nach Bedarf neu an, indem Sie sie in der Liste nach oben oder unten ziehen (müssen Sie das Symbol **[!UICONTROL Neu anordnen]** auswählen).

   ![chlimage_1-141](assets/chlimage_1-352.png)

   Wenn Sie Miniaturansichten hinzufügen möchten, klicken Sie auf das **Plussymbol** zum **[!UICONTROL Hinzufügen von Miniaturansichten]** neben dem Bild und navigieren Sie zur gewünschten Miniaturansicht. Wenn Sie alle Miniaturansichten ausgewählt haben, klicken Sie auf **[!UICONTROL Speichern]**.

   >[!NOTE]
   >
   >Wenn Sie Assets hinzufügen möchten, tippen Sie auf **[!UICONTROL Asset hinzufügen]**.

1. Um ein Asset zu löschen, aktivieren Sie das entsprechende Kontrollkästchen und tippen Sie auf **[!UICONTROL Asset löschen]**.
1. Um eine Vorgabe anzuwenden, tippen Sie in der rechten oberen Ecke auf **[!UICONTROL Vorgabe]** und wählen Sie eine Vorgabe aus, die auf die Assets angewendet werden soll.
1. Klicken Sie auf **[!UICONTROL Speichern]**. Das neu erstellte Set für gemischte Medien wird in dem Ordner angezeigt, in dem es erstellt wurde.

## Bearbeiten von gemischten Mediensets   {#editing-mixed-media-sets}

Sie können verschiedene Aufgaben an Assets in gemischten Mediensets direkt in der Benutzeroberfläche [durchführen, wie bei allen Assets in Assets](/help/assets/manage-digital-assets.md). Sie können außerdem die folgenden Aktionen in gemischten Mediensets ausführen:

* Fügen Sie dem gemischten Medienset Assets hinzu.
* Ordnen Sie Assets im gemischten Medienset neu an.
* Löschen Sie Assets im gemischten Medienset.
* Wenden Sie Viewer-Vorgaben an.
* Ändern Sie die Standardminiatur.

**So bearbeiten Sie ein gemischtes Medienset**

1. Führen Sie einen der folgenden Schritte aus:

   * Bewegen Sie den Mauszeiger über ein Asset in einem gemischten Medienset und tippen Sie auf **[!UICONTROL Bearbeiten]** (Stiftsymbol).
   * Bewegen Sie den Mauszeiger über ein Asset in einem gemischten Medienset und tippen Sie auf **[!UICONTROL Auswählen]** (Häkchensymbol) und dann auf **[!UICONTROL Bearbeiten]** in der Symbolleiste.

   * Tippen Sie auf ein Asset in einem gemischten Medienset und dann auf **[!UICONTROL Bearbeiten]** (Bleistiftsymbol) in der Symbolleiste.

1. Führen Sie im Editor für gemischte Mediensets einen der folgenden Schritte aus:

   * Um Assets neu anzuordnen, tippen Sie im linken Bereich auf **[!UICONTROL Assets]** (Bildsymbol) und ziehen Sie das Asset an eine neue Position.
   * Um Assets hinzuzufügen, tippen Sie in der Symbolleiste auf **[!UICONTROL Asset hinzufügen]**. Navigieren Sie zu den Assets. Bewegen Sie bei jedem Asset, das Sie hinzufügen möchten, den Mauszeiger über dem Bild des Assets (nicht über dem Namen des Assets) und tippen Sie auf das Häkchensymbol. Tippen Sie oben rechts auf **[!UICONTROL Auswählen]**.

   * Um ein Asset zu löschen, tippen Sie im linken Bereich auf **[!UICONTROL Assets]** (Bildsymbol) und wählen Sie das Asset aus. Tippen Sie in der Symbolleiste auf **[!UICONTROL Asset]** löschen.

   * Um Assets anhand des Namens in aufsteigender oder absteigender Reihenfolge zu sortieren, tippen Sie im linken Bereich auf **[!UICONTROL Assets]** (Bildsymbol). Klicken Sie rechts neben der Überschrift **[!UICONTROL Assets]** auf das Caret-Zeichen nach oben oder unten.

      >[!NOTE]
      >
      >* Um ein komplettes gemischtes Medienset aus einem Anzeigemodus zu löschen (z. B. **[!UICONTROL Kartenansicht]** oder **[!UICONTROL Spaltenansicht]**), navigieren Sie zum gemischten Medienset. Bewegen Sie den Mauszeiger über das Asset und klicken Sie dann auf das Häkchen-Symbol, um es auszuwählen. Drücken Sie die **[!UICONTROL Rücktaste]** oder klicken Sie in der Symbolleiste auf **[!UICONTROL Mehr]** (Ellipse) und dann auf **[!UICONTROL Löschen]**.
         >
         >
      * Sie können die Assets in einem gemischten Medienset bearbeiten, indem Sie zum Set navigieren. Tippen Sie in der linken Leiste auf **[!UICONTROL Mitglieder setzen]** und dann auf das Symbol **[!UICONTROL Stift]** für ein einzelnes Asset, um das Bearbeitungsfenster zu öffnen.


1. Tippen Sie auf **[!UICONTROL Speichern]**, wenn Sie die Bearbeitung abgeschlossen haben.

   >[!NOTE]
   >
   >* Um die Assets in einem gemischten Medienset zu bearbeiten, navigieren Sie zum gemischten Medienset. Tippen Sie auf (wählen Sie nicht aus) das Set, um es auf der Seite &quot;Vorschau für Experience Manager-Set&quot;zu öffnen. Klicken Sie in der linken Leiste auf das Caret-Symbol nach unten, um die Dropdown-Liste zu öffnen, und tippen Sie auf **[!UICONTROL Mitglieder des Sets]**. Bewegen Sie auf der Seite „Mitglieder des Sets“ den Mauszeiger auf ein Asset und tippen Sie auf **[!UICONTROL Bearbeiten]** (Stiftsymbol), um die Bearbeitungsseite zu öffnen.
      >
      >
   * Um ein komplettes gemischtes Medienset aus einem Anzeigemodus zu löschen (z. B. Karten- oder Spaltenansicht), navigieren Sie zum gemischten Medienset. Bewegen Sie den Mauszeiger über das Set und tippen Sie auf **[!UICONTROL Auswählen]** (Häkchensymbol). Drücken Sie die **[!UICONTROL Rücktaste]** oder tippen Sie auf **[!UICONTROL Mehr]** und dann auf **[!UICONTROL Löschen]**.


## Vorschau von gemischten Mediensets {#previewing-mixed-media-sets}

Weitere Informationen zum Aufrufen einer Vorschau von Sets für gemischte Medien finden Sie in [Asset-Vorschau](/help/assets/dynamic-media/previewing-assets.md).

## Veröffentlichen von gemischten Mediensets   {#publishing-mixed-media-sets}

Weitere Informationen zum Veröffentlichen von Sets für gemischte Medien finden Sie in [Veröffentlichen von Assets](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

>[!NOTE]
>
>Wenn das gemischte Medienset beim ersten Veröffentlichen nicht vollständig im Versand-Dienst landet, veröffentlichen Sie den gemischten Mediensatz erneut.

