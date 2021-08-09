---
title: Gemischte Mediensets
description: In diesem Abschnitt erfahren Sie, wie Sie gemischte Mediensets in Dynamic Media verwenden..
feature: Gemischte Mediensets
role: User
exl-id: 7ccde741-38d2-44c9-9378-f2721384aab7
source-git-commit: a11529886d4b158c19a97ccbcb7d004cf814178d
workflow-type: tm+mt
source-wordcount: '1470'
ht-degree: 60%

---

# Gemischte Mediensets{#mixed-media-sets}

Mit gemischten Mediensets können Sie eine Mischung aus Bildern, Bildsets, Rotationssets und Videos in einer Präsentation bereitstellen.

Gemischte Mediensets werden durch ein Banner mit dem Wort **[!UICONTROL MixedMediaSet]** gekennzeichnet. Darüber hinaus wird bei veröffentlichten Sets für gemischte Medien das Veröffentlichungsdatum (durch das **[!UICONTROL Welt]**-Symbol gekennzeichnet) zusammen mit dem Datum der letzten Änderung (durch das **[!UICONTROL Bleistift]**-Symbol gekennzeichnet) im Banner angezeigt.

![chlimage_1-137](assets/chlimage_1-348.png)

>[!NOTE]
>
>Informationen zur Benutzeroberfläche &quot;Assets&quot;finden Sie unter [Verwalten von Assets mit der Touch-Benutzeroberfläche](/help/assets/manage-digital-assets.md).

## Schnellstartanleitungen: Gemischte Mediensets {#quick-start-mixed-media-sets}

Führen Sie die folgenden Schritte aus, um den schnellen Einstieg in die Arbeit mit gemischten Mediensets zu schaffen:

1. [Laden Sie die Assets hoch.](#uploading-assets)

   Laden Sie zunächst die Bilder und Videos für Ihre gemischten Mediensets hoch. Erstellen Sie bei Bedarf [Bildsets](/help/assets/dynamic-media/image-sets.md) und [Rotationssets](/help/assets/dynamic-media/spin-sets.md). Berücksichtigen Sie das Zoomen bei der Auswahl von Bildern, da Benutzer Bilder im Viewer für das gemischte Medienset zoomen können. Achten Sie darauf, dass die längste Seite der Bilder mindestens 2.000 Pixel aufweist.

1. [Erstellen Sie gemischte Mediensets](#creating-mixed-media-sets).

   Um ein gemischtes Medienset zu erstellen, navigieren Sie auf der Seite &quot;Assets&quot;zu **[!UICONTROL Erstellen]** > **[!UICONTROL Gemischtes Medienset]** und benennen Sie dann das Set, wählen Sie die Assets und wählen Sie die Reihenfolge der Bilder aus.

   Siehe [Arbeiten mit Selektoren](/help/assets/dynamic-media/working-with-selectors.md).

1. Richten Sie bei Bedarf [Viewer-Vorgaben für das gemischte Medienset](/help/assets/dynamic-media/managing-viewer-presets.md) ein.

   Administratoren können Viewer-Vorgaben für gemischte Mediensets erstellen oder ändern. Um die gemischten Medien mit einer Viewer-Vorgabe anzuzeigen, wählen Sie das gemischte Medienset aus und wählen Sie im Dropdown-Menü in der linken Seitenleiste die Option **[!UICONTROL Viewer]** aus.

   Um Viewer-Vorgaben zu erstellen oder zu bearbeiten, navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Viewer-Vorgaben]**.

   Siehe [Hinzufügen und Bearbeiten von Viewer-Vorgaben](/help/assets/dynamic-media/managing-viewer-presets.md).

1. [Zeigen Sie eine Vorschau der gemischten Mediensets an](#previewing-mixed-media-sets).

   Wenn Sie das gemischte Medienset auswählen, können Sie eine Vorschau davon anzeigen. Um das gemischte Medienset im ausgewählten Viewer zu untersuchen, wählen Sie die Miniaturansichtssymbole aus. Sie können verschiedene Viewer aus dem Menü **[!UICONTROL Viewer]** wählen, das Sie links in der Leiste über die Dropdown-Liste aufrufen können.

1. [Veröffentlichen Sie gemischte Mediensets](#publishing-mixed-media-sets).

   Beim Veröffentlichen eines gemischten Mediensets wird die URL- und Integrationszeichenfolge aktiviert. Außerdem müssen Sie [die Viewer-Vorgabe veröffentlichen](/help/assets/dynamic-media/managing-viewer-presets.md#publishing-viewer-presets).

1. [Verknüpfen Sie URLs mit einer Web-Anwendung](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) oder [betten Sie den Video- oder Bild-Viewer ein](/help/assets/dynamic-media/embed-code.md).

   Adobe Experience Manager Assets erstellt URL-Aufrufe für gemischte Mediensets und aktiviert diese nach deren Veröffentlichung. Sie können diese URLs während der Asset-Vorschau kopieren. Alternativ dazu können Sie sie in Ihre Website einbetten.

   Markieren Sie dazu das gemischte Medienset und klicken Sie dann im Dropdown-Menü in der linken Seitenleiste auf **[!UICONTROL Viewer]**.

   Siehe [Verknüpfen eines gemischten Mediensets mit einer Web-Seite](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) und [Einbetten des Video- oder Bild-Viewers](/help/assets/dynamic-media/embed-code.md).

Bei Bedarf können Sie die [gemischten Mediensets](#editing-mixed-media-sets) bearbeiten. Darüber hinaus können Sie [Eigenschaften von gemischten Mediensets](/help/assets/manage-digital-assets.md#editing-properties) anzeigen und ändern.

>[!NOTE]
>
>Wenn Sie beim Erstellen von Sets Probleme haben, lesen Sie [Fehlerbehebung für Dynamic Media](/help/assets/dynamic-media/troubleshoot-dm.md).

## Hochladen von Assets {#uploading-assets}

Laden Sie zunächst die Bilder und Videos für Ihre gemischten Mediensets hoch. Denken Sie daran, dass Benutzer die Bilder im Viewer für gemischte Mediensets zoomen können. Wählen Sie daher Bilder mit dieser Zoom-Möglichkeit aus. Achten Sie darauf, dass die längste Seite der Bilder mindestens 2.000 Pixel aufweist.

Wenn Sie außerdem Rotationssets oder Bildsets zum Set für gemischte Medien hinzufügen möchten, müssen Sie auch diese erstellen.

## Erstellen Sie gemischte Mediensets {#creating-mixed-media-sets}

Sie können Ihrem gemischten Medienset Bilder, Bildsets, Rotationssets und Videos hinzufügen. Achten Sie darauf, dass die Dateien, Bildsets und Rotationssets veröffentlicht werden können, bevor Sie diese dem gemischten Medienset hinzufügen.

Assets, die Sie Ihrem Set hinzufügen, werden automatisch in alphanumerischer Reihenfolge hinzugefügt. Sie können die Anordnung oder Sortierung der Assets manuell ändern, nachdem sie hinzugefügt wurden.

**So erstellen Sie gemischte Mediensets:**

1. Navigieren Sie in Assets an die Stelle, an der Sie ein gemischtes Medienset erstellen möchten, wählen Sie **[!UICONTROL Erstellen]** und klicken Sie auf **[!UICONTROL Gemischtes Medienset]**. Sie können das Set auch in einem Ordner erstellen, der die gewünschten Assets enthält. Der Editor für gemischte Mediensets wird angezeigt.

   ![chlimage_1-138](assets/chlimage_1-349.png)

1. Geben Sie im Editor für gemischte Mediensets im Feld **[!UICONTROL Titel]** einen Namen für das gemischte Medienset ein. Der Name wird im Banner über dem Set für gemischte Medien angezeigt. Geben Sie optional eine Beschreibung ein.

   ![chlimage_1-139](assets/chlimage_1-350.png)

   >[!NOTE]
   >
   >Beim Erstellen des gemischten Mediensets können Sie die entsprechende Miniaturansicht ändern oder zulassen, dass Experience Manager die Miniaturansicht automatisch basierend auf den Assets im gemischten Medienset auswählt. Um eine Miniaturansicht auszuwählen, wählen Sie **[!UICONTROL Miniaturansicht ändern]** und wählen Sie ein beliebiges Bild aus (Sie können auch zu anderen Ordnern navigieren, um Bilder zu suchen). Wenn Sie eine Miniaturansicht ausgewählt haben und möchten, dass Experience Manager eine Miniaturansicht aus dem gemischten Medienset generiert, wählen Sie **[!UICONTROL Zu automatischer Miniatur wechseln]** aus.

1. Um Assets auszuwählen, die Sie in das gemischte Medienset aufnehmen möchten, wählen Sie die Asset-Auswahl aus. Wählen Sie sie aus und wählen Sie **[!UICONTROL Wählen Sie]** aus.

   Mit der Asset-Auswahl können Sie nach Assets suchen, indem Sie einen Suchbegriff eingeben und **[!UICONTROL Return]** auswählen. Sie können auch Filter anwenden, um Ihre Suchergebnisse genauer abzustimmen. Sie können nach Pfad, Sammlung, Dateityp und Tag filtern. Wählen Sie den Filter aus und wählen Sie dann in der Symbolleiste das Symbol **[!UICONTROL Filter]** aus. Ändern Sie die Ansicht, indem Sie das Symbol **[!UICONTROL Ansicht]** und dann die **[!UICONTROL Listenansicht]**, **[!UICONTROL Spaltenansicht]** oder **[!UICONTROL Kartenansicht]** auswählen.

   Siehe [Arbeiten mit Selektoren](/help/assets/dynamic-media/working-with-selectors.md).

   ![chlimage_1-140](assets/chlimage_1-351.png)

1. Ordnen Sie die Bilder neu an, indem Sie sie in der Liste nach Bedarf nach oben oder unten ziehen. (Sie müssen dazu das Symbol für die **[!UICONTROL Neuanordnung]** auswählen.)

   ![chlimage_1-141](assets/chlimage_1-352.png)

   Wenn Sie Miniaturansichten hinzufügen möchten, wählen Sie das Symbol **+** **[!UICONTROL Miniaturansicht]** neben dem Bild und navigieren Sie zur gewünschten Miniaturansicht. Wenn Sie alle Miniaturansichten ausgewählt haben, wählen Sie **[!UICONTROL Speichern]**.

   >[!NOTE]
   >
   >Wenn Sie Assets hinzufügen möchten, wählen Sie **[!UICONTROL Asset hinzufügen]** aus.

1. Um ein Asset zu löschen, aktivieren Sie das entsprechende Kontrollkästchen und wählen Sie **[!UICONTROL Asset löschen]** aus.
1. Um eine Vorgabe anzuwenden, wählen Sie **[!UICONTROL Vorgabe]** in der oberen rechten Ecke aus und wählen Sie eine Vorgabe aus, die auf die Assets angewendet werden soll.
1. Wählen Sie **[!UICONTROL Speichern]** aus. Das neu erstellte Set für gemischte Medien wird in dem Ordner angezeigt, in dem es erstellt wurde.

## Bearbeiten von gemischten Mediensets {#editing-mixed-media-sets}

Sie können direkt auf der Benutzeroberfläche verschiedene Bearbeitungsaufgaben für Assets in gemischten Mediensets ausführen, [genauso wie bei allen anderen Assets in Assets](/help/assets/manage-digital-assets.md). Sie können außerdem die folgenden Aktionen in gemischten Mediensets ausführen:

* Fügen Sie dem gemischten Medienset Assets hinzu.
* Ordnen Sie Assets im gemischten Medienset neu an.
* Löschen Sie Assets im gemischten Medienset.
* Wenden Sie Viewer-Vorgaben an.
* Ändern Sie die Standardminiatur.

**So bearbeiten Sie gemischte Mediensets:**

1. Führen Sie einen der folgenden Schritte aus:

   * Bewegen Sie den Mauszeiger über ein Asset in einem gemischten Medienset und wählen Sie **[!UICONTROL Bearbeiten]** (Stiftsymbol).
   * Bewegen Sie den Mauszeiger über ein Asset in einem gemischten Medienset, wählen Sie **[!UICONTROL Wählen Sie]** (Häkchensymbol) und klicken Sie dann in der Symbolleiste auf **[!UICONTROL Bearbeiten]**.

   * Wählen Sie ein Asset für gemischte Mediensets aus und klicken Sie dann in der Symbolleiste auf **[!UICONTROL Bearbeiten]** (Stiftsymbol).

1. Führen Sie im Editor für gemischte Mediensets einen der folgenden Schritte aus:

   * Um Assets neu anzuordnen: Wählen Sie im linken Bereich **[!UICONTROL Assets]** (Bildsymbol) aus und ziehen Sie ein Asset an eine neue Position.
   * Um Assets hinzuzufügen: Wählen Sie in der Symbolleiste **[!UICONTROL Asset hinzufügen]** aus. Navigieren Sie zu den Assets. Bewegen Sie für jedes Asset, das Sie hinzufügen möchten, den Mauszeiger über das Bild des Assets (nicht den Namen des Assets) und wählen Sie dann das Häkchen-Symbol aus. Wählen Sie in der oberen rechten Ecke **[!UICONTROL Select]** aus.

   * Um ein Asset zu löschen, wählen Sie im linken Bereich **[!UICONTROL Assets]** (Bildsymbol) aus und wählen Sie dann das Asset aus. Wählen Sie in der Symbolleiste **[!UICONTROL Asset löschen]** aus.

   * Um Assets nach ihrem Namen in auf- oder absteigender Reihenfolge zu sortieren, wählen Sie im linken Bereich **[!UICONTROL Assets]** (Bildsymbol) aus. Wählen Sie rechts neben der Überschrift **[!UICONTROL Assets]** die Caret-Symbole nach oben oder unten aus.

      >[!NOTE]
      >
      >* Um ein komplettes gemischtes Medienset aus einem Anzeigemodus zu löschen (z. B. **[!UICONTROL Kartenansicht]** oder **[!UICONTROL Spaltenansicht]**), navigieren Sie zum gemischten Medienset. Bewegen Sie den Mauszeiger über das Asset und wählen Sie dann das Häkchen-Symbol aus, damit Sie es auswählen können. Drücken Sie die Taste **[!UICONTROL Rücktaste]** auf der Tastatur oder wählen Sie **[!UICONTROL Mehr]** (drei Punkte) in der Symbolleiste und klicken Sie dann auf **[!UICONTROL Löschen]**.
         >
         >
      * Sie können die Assets in einem gemischten Medienset bearbeiten, indem Sie zum Set navigieren. Wählen Sie in der linken Leiste **[!UICONTROL Setmitglieder]** und klicken Sie dann auf das Symbol **[!UICONTROL Bleistift]** für ein einzelnes Asset, um das Bearbeitungsfenster zu öffnen.


1. Wählen Sie **[!UICONTROL Save]** aus, wenn Sie die Bearbeitung abgeschlossen haben.

   >[!NOTE]
   >
   >* Um die Assets in einem gemischten Medienset zu bearbeiten, navigieren Sie zum gemischten Medienset. Tippen Sie auf das Set (nicht auswählen), um es auf der Seite „Experience Manager-Set-Vorschau“ zu öffnen. Wählen Sie in der linken Leiste das Dropdownmenü aus, um die Dropdownliste zu öffnen, und wählen Sie dann **[!UICONTROL Mitglieder festlegen]** aus. Bewegen Sie auf der Seite Mitglieder des Sets den Mauszeiger über ein Asset und wählen Sie dann **[!UICONTROL Bearbeiten]** (Stiftsymbol) aus, um die Bearbeitungsseite zu öffnen.
      >
      >
   * Um ein komplettes gemischtes Medienset aus einem Anzeigemodus zu löschen (z. B. Karten- oder Spaltenansicht), navigieren Sie zum gemischten Medienset. Bewegen Sie den Mauszeiger über das Set und wählen Sie **[!UICONTROL Auswählen]** (Häkchensymbol). Drücken Sie **[!UICONTROL Rücktaste]** auf Ihrer Tastatur oder wählen Sie **[!UICONTROL Mehr]** (Zeile mit drei Punkten) und dann **[!UICONTROL Löschen]**.


## Zeigen Sie eine Vorschau der gemischten Mediensets an {#previewing-mixed-media-sets}

Weitere Informationen zur Vorschau von gemischten Mediensets finden Sie unter [Asset-Vorschau](/help/assets/dynamic-media/previewing-assets.md) .

## Veröffentlichen Sie gemischte Mediensets {#publishing-mixed-media-sets}

Weitere Informationen zum Veröffentlichen von gemischten Mediensets finden Sie unter [Veröffentlichen von Assets](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md) .

>[!NOTE]
>
>Wenn das Set für gemischte Medien bei der ersten Veröffentlichung nicht vollständig an den Bereitstellungs-Service übertragen wird, veröffentlichen Sie das Set für gemischte Medien erneut.
