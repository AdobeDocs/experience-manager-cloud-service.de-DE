---
title: Sets für gemischte Medien
description: In diesem Abschnitt erfahren Sie, wie Sie Sets für gemischte Medien in Dynamic Media verwenden.
contentOwner: Rick Brough
feature: Mixed Media Sets
role: User
exl-id: 7ccde741-38d2-44c9-9378-f2721384aab7
source-git-commit: 36ab36ba7e14962eba3947865545b8a3f29f6bbc
workflow-type: tm+mt
source-wordcount: '1507'
ht-degree: 100%

---

# Sets für gemischte Medien{#mixed-media-sets}

Mit gemischten Mediensets können Sie eine Mischung aus Bildern, Bildsets, Rotationssets und Videos in einer Präsentation bereitstellen.

Gemischte Mediensets werden durch ein Banner mit dem Wort **[!UICONTROL MixedMediaSet]** gekennzeichnet. Darüber hinaus wird bei veröffentlichten Sets für gemischte Medien das Veröffentlichungsdatum (durch das **[!UICONTROL Welt]**-Symbol gekennzeichnet) zusammen mit dem Datum der letzten Änderung (durch das **[!UICONTROL Bleistift]**-Symbol gekennzeichnet) im Banner angezeigt.

![chlimage_1-137](assets/chlimage_1-348.png)

>[!NOTE]
>
>Weitere Informationen zur Assets-Benutzeroberfläche finden Sie in [Verwalten von Assets mit der Touch-optimierten Benutzeroberfläche](/help/assets/manage-digital-assets.md).

## Schnellstartanleitungen: Gemischte Mediensets {#quick-start-mixed-media-sets}

Führen Sie die folgenden Schritte aus, um den schnellen Einstieg in die Arbeit mit Sets für gemischte Medien zu schaffen:

1. [Laden Sie die Assets hoch](#uploading-assets).

   Laden Sie zunächst die Bilder und Videos für Ihre gemischten Mediensets hoch. Erstellen Sie bei Bedarf [Bildsets](/help/assets/dynamic-media/image-sets.md) und [Rotationssets](/help/assets/dynamic-media/spin-sets.md). Berücksichtigen Sie das Zoomen bei der Auswahl von Bildern, da Benutzer Bilder im Viewer für das gemischte Medienset zoomen können. Achten Sie darauf, dass die längste Seite der Bilder mindestens 2.000 Pixel aufweist.

   Unter [Dynamic Media – Unterstützte Rasterbildformate](/help/assets/file-format-support.md#image-support-dynamic-media) finden Sie eine Liste der Formate, die von gemischten Medien-Sets unterstützt werden.

1. [Erstellen von gemischten Medien-Sets](#creating-mixed-media-sets).

   Zum Erstellen eines gemischten Mediensets klicken Sie auf der Seite „Assets“ auf **[!UICONTROL Erstellen]** > **[!UICONTROL Gemischtes Medienset]** und benennen Sie dann das Set, wählen Sie die Assets aus und wählen Sie die Reihenfolge der Bilder.

   Siehe [Arbeiten mit Selektoren](/help/assets/dynamic-media/working-with-selectors.md).

1. Richten Sie bei Bedarf [Viewer-Vorgaben für das gemischte Medienset](/help/assets/dynamic-media/managing-viewer-presets.md) ein.

   Administratoren können Viewer-Vorgaben für gemischte Mediensets erstellen oder ändern. Um die gemischten Medien mit einer Viewer-Vorgabe anzuzeigen, wählen Sie das gemischte Medienset aus und wählen Sie im Dropdown-Menü in der linken Seitenleiste die Option **[!UICONTROL Viewer]** aus.

   Um Viewer-Vorgaben zu erstellen oder zu bearbeiten, gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Viewer-Vorgaben]**.

   Siehe [Hinzufügen und Bearbeiten von Viewer-Vorgaben](/help/assets/dynamic-media/managing-viewer-presets.md).

1. [Zeigen Sie eine Vorschau der gemischten Mediensets an](#previewing-mixed-media-sets).

   Wenn Sie das gemischte Medienset auswählen, können Sie eine Vorschau davon anzeigen. Um Ihr gemischtes Medienset im ausgewählten Viewer zu betrachten, wählen Sie die Miniatursymbole aus. Sie können verschiedene Viewer aus dem Menü **[!UICONTROL Viewer]** wählen, das Sie links in der Leiste über die Dropdown-Liste aufrufen können.

1. [Veröffentlichen Sie gemischte Mediensets](#publishing-mixed-media-sets).

   Beim Veröffentlichen eines gemischten Mediensets wird die URL- und Integrationszeichenfolge aktiviert. Außerdem müssen Sie [die Viewer-Vorgabe veröffentlichen](/help/assets/dynamic-media/managing-viewer-presets.md#publishing-viewer-presets).

1. [Verknüpfen Sie URLs mit einer Web-Anwendung](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) oder [betten Sie den Video- oder Bild-Viewer ein](/help/assets/dynamic-media/embed-code.md).

   Adobe Experience Manager Assets erstellt URL-Aufrufe für gemischte Mediensets und aktiviert diese nach deren Veröffentlichung. Sie können diese URLs während der Asset-Vorschau kopieren. Alternativ dazu können Sie sie in Ihre Website einbetten.

   Markieren Sie dazu das gemischte Medienset und klicken Sie dann im Dropdown-Menü in der linken Seitenleiste auf **[!UICONTROL Viewer]**.

   Siehe [Verknüpfen eines gemischten Mediensets mit einer Web-Seite](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) und [Einbetten des Video- oder Bild-Viewers](/help/assets/dynamic-media/embed-code.md).

Bei Bedarf können Sie die [gemischten Mediensets](#editing-mixed-media-sets) bearbeiten. Darüber hinaus können Sie [Eigenschaften von gemischten Mediensets](/help/assets/manage-digital-assets.md#editing-properties) anzeigen und ändern.

>[!NOTE]
>
>Unterstützung beim Erstellen von Sets erhalten Sie unter [Problembehandlung in Dynamic Media](/help/assets/dynamic-media/troubleshoot-dm.md).

## Hochladen von Assets {#uploading-assets}

Laden Sie zunächst die Bilder und Videos für Ihre gemischten Mediensets hoch. Denken Sie daran, dass Benutzer die Bilder im Viewer für gemischte Mediensets zoomen können. Wählen Sie daher Bilder mit dieser Zoom-Möglichkeit aus. Achten Sie darauf, dass die längste Seite der Bilder mindestens 2.000 Pixel aufweist.

Wenn Sie außerdem Rotationssets oder Bildsets zum Set für gemischte Medien hinzufügen möchten, müssen Sie auch diese erstellen.

Unter [Dynamic Media – Unterstützte Rasterbildformate](/help/assets/file-format-support.md#image-support-dynamic-media) finden Sie eine Liste der Formate, die von gemischten Medien-Sets unterstützt werden.

## Erstellen Sie gemischte Mediensets {#creating-mixed-media-sets}

Sie können Ihrem gemischten Medienset Bilder, Bildsets, Rotationssets und Videos hinzufügen. Achten Sie darauf, dass die Dateien, Bildsets und Rotationssets veröffentlicht werden können, bevor Sie diese dem Set für gemischte Medien hinzufügen.

Assets, die Sie Ihrem Set hinzufügen, werden automatisch in alphanumerischer Reihenfolge hinzugefügt. Sie können die Anordnung oder Sortierung der Assets manuell ändern, nachdem sie hinzugefügt wurden.

**So erstellen Sie gemischte Mediensets:**

1. Gehen Sie in „Assets“ zu der Stelle, an der Sie ein gemischtes Medienset erstellen möchten, klicken Sie auf **[!UICONTROL Erstellen]** und wählen Sie **[!UICONTROL Gemischtes Medienset]**. Sie können das Set auch in einem Ordner erstellen, der die gewünschten Assets enthält. Der Editor für gemischte Mediensets wird angezeigt.

   ![chlimage_1-138](assets/chlimage_1-349.png)

1. Geben Sie im Editor für gemischte Mediensets im Feld **[!UICONTROL Titel]** einen Namen für das gemischte Medienset ein. Der Name wird im Banner über dem Set für gemischte Medien angezeigt. Geben Sie optional eine Beschreibung ein.

   ![chlimage_1-139](assets/chlimage_1-350.png)

   >[!NOTE]
   >
   >Beim Erstellen des gemischten Mediensets können Sie die entsprechende Miniatur ändern oder zulassen, dass Experience Manager die Miniatur automatisch basierend auf den Assets im gemischten Medienset auswählt. Um eine Miniatur auszuwählen, klicken Sie auf **[!UICONTROL Miniatur ändern]** und wählen Sie ein beliebiges Bild aus (Sie können auch zu anderen Ordnern gehen, um Bilder zu suchen). Wenn Sie eine Miniatur ausgewählt haben und möchten, dass Experience Manager eine Miniatur aus dem gemischten Medienset generiert, wählen Sie **[!UICONTROL Zu automatischer Miniatur wechseln]** aus.

1. Um Assets auszuwählen, die Sie in Ihr gemischtes Medienset aufnehmen möchten, wählen Sie die Asset-Auswahl. Wählen Sie sie aus und klicken Sie auf **[!UICONTROL Auswählen]**.

   Mit der Asset-Auswahl können Sie nach Assets suchen, indem Sie einen Suchbegriff eingeben und die **[!UICONTROL Eingabetaste]** drücken. Sie können auch Filter anwenden, um Ihre Suchergebnisse genauer abzustimmen. Sie können nach Pfad, Sammlung, Dateityp und Tag filtern. Wählen Sie den Filter aus und klicken Sie dann in der Symbolleiste auf das Symbol **[!UICONTROL Filter]**. Ändern Sie die Ansicht, indem Sie das Symbol **[!UICONTROL Ansicht]** und dann die **[!UICONTROL Listenansicht]**, **[!UICONTROL Spaltenansicht]** oder **[!UICONTROL Kartenansicht]** auswählen.

   Siehe [Arbeiten mit Selektoren](/help/assets/dynamic-media/working-with-selectors.md).

   ![chlimage_1-140](assets/chlimage_1-351.png)

1. Ordnen Sie die Bilder neu an, indem Sie sie in der Liste nach Bedarf nach oben oder unten ziehen. (Sie müssen dazu das Symbol für die **[!UICONTROL Neuanordnung]** auswählen.)

   ![chlimage_1-141](assets/chlimage_1-352.png)

   Wenn Sie Miniaturen hinzufügen möchten, klicken Sie neben dem Bild auf das Symbol **+** **[!UICONTROL Miniatur]** und gehen Sie zur gewünschten Miniatur. Wenn Sie alle Miniaturen ausgewählt haben, klicken Sie auf **[!UICONTROL Speichern]**.

   >[!NOTE]
   >
   >Wenn Sie Assets hinzufügen möchten, wählen Sie **[!UICONTROL Asset hinzufügen]**.

1. Um ein Asset zu löschen, aktivieren Sie das entsprechende Kontrollkästchen und klicken Sie auf **[!UICONTROL Asset löschen]**.
1. Um eine Vorgabe anzuwenden, klicken Sie in der rechten oberen Ecke auf **[!UICONTROL Vorgabe]** und wählen Sie eine Vorgabe aus, die auf die Assets angewendet werden soll.
1. Wählen Sie **[!UICONTROL Speichern]** aus. Das erstellte gemischte Medien-Set wird in dem Ordner angezeigt, in dem es erstellt wurde.

## Bearbeiten von gemischten Mediensets {#editing-mixed-media-sets}

Sie können direkt auf der Benutzeroberfläche verschiedene Bearbeitungsaufgaben für Assets in gemischten Mediensets ausführen, [genauso wie bei allen anderen Assets in Assets](/help/assets/manage-digital-assets.md). Sie können außerdem die folgenden Aktionen in gemischten Mediensets ausführen:

* Fügen Sie dem gemischten Medienset Assets hinzu.
* Ordnen Sie Assets im gemischten Medienset neu an.
* Löschen Sie Assets im gemischten Medienset.
* Wenden Sie Viewer-Vorgaben an.
* Ändern Sie die Standardminiatur.

**So bearbeiten Sie gemischte Mediensets:**

1. Führen Sie einen der folgenden Schritte aus:

   * Bewegen Sie den Mauszeiger über ein Asset in einem gemischten Medienset und klicken Sie auf **[!UICONTROL Bearbeiten]** (Stiftsymbol).
   * Bewegen Sie den Mauszeiger über ein Asset in einem gemischten Medienset und klicken Sie auf **[!UICONTROL Auswählen]** (Häkchensymbol) und dann auf **[!UICONTROL Bearbeiten]** in der Symbolleiste.

   * Klicken Sie auf ein Asset in einem gemischten Medienset und dann auf **[!UICONTROL Bearbeiten]** (Stiftsymbol) in der Symbolleiste.

1. Führen Sie im Editor für gemischte Mediensets einen der folgenden Schritte aus:

   * Um Assets neu anzuordnen, klicken Sie im linken Bereich auf **[!UICONTROL Assets]** (Bildsymbol) und ziehen Sie das Asset an eine neue Position.
   * Um Assets hinzuzufügen, klicken Sie in der Symbolleiste auf **[!UICONTROL Asset hinzufügen]**. Navigieren Sie zu den Assets. Bewegen Sie bei jedem Asset, das Sie hinzufügen möchten, den Mauszeiger über dem Bild des Assets (nicht über dem Namen des Assets) und klicken Sie auf das Häkchensymbol. Klicken Sie in der oberen rechten Ecke auf **[!UICONTROL Auswählen]**.

   * Um ein Asset zu löschen, klicken Sie im linken Bereich auf **[!UICONTROL Assets]** (Bildsymbol) und wählen dann das Asset aus. Wählen Sie in der Symbolleiste **[!UICONTROL Asset löschen]**.

   * Um Assets anhand des Namens in aufsteigender oder absteigender Reihenfolge zu sortieren, klicken Sie im linken Bereich auf **[!UICONTROL Assets]** (Bildsymbol). Klicken Sie rechts neben der Überschrift **[!UICONTROL Assets]** auf das Caret-Zeichen nach oben oder unten.

     >[!NOTE]
     >
     >* Um ein komplettes gemischtes Medienset aus einem Anzeigemodus zu löschen (z. B. **[!UICONTROL Kartenansicht]** oder **[!UICONTROL Spaltenansicht]**), navigieren Sie zum gemischten Medienset. Bewegen Sie den Mauszeiger über das Asset und klicken Sie dann auf das Häkchensymbol, um es auszuwählen. Drücken Sie die **[!UICONTROL Rücktaste]** auf der Tastatur oder klicken Sie auf **[!UICONTROL Mehr]** (drei Punkte) in der Symbolleiste und dann auf **[!UICONTROL Löschen]**.
     >
     >* Sie können die Assets in einem gemischten Medienset bearbeiten, indem Sie zum Set navigieren. Wählen Sie in der linken Leiste die Option **[!UICONTROL Set-Mitglieder]** und wählen Sie dann das **[!UICONTROL Stiftsymbol]** bei einem einzelnen Asset, um das Bearbeitungsfenster zu öffnen.

1. Klicken Sie auf **[!UICONTROL Speichern]**, wenn Sie mit der Bearbeitung fertig sind.

   >[!NOTE]
   >
   >* Um die Assets in einem gemischten Medienset zu bearbeiten, navigieren Sie zum gemischten Medienset. Wählen Sie das Set (nicht auswählen), um es auf der Seite „Experience Manager-Set-Vorschau“ zu öffnen. Klicken Sie in der linken Leiste auf das Caret-Zeichen nach unten, um die Dropdown-Liste zu öffnen, und klicken Sie dann auf **[!UICONTROL Set-Mitglieder]**. Bewegen Sie den Mauszeiger auf der Seite „Set-Mitglieder“ über ein Asset und klicken Sie dann auf **[!UICONTROL Bearbeiten]** (Stiftsymbol), um die Bearbeitungsseite zu öffnen.
   >
   >* Um ein komplettes gemischtes Medienset aus einem Anzeigemodus zu löschen (z. B. Karten- oder Spaltenansicht), navigieren Sie zum gemischten Medienset. Bewegen Sie den Mauszeiger über das Set und klicken Sie dann auf **[!UICONTROL Auswählen]** (Häkchensymbol). Drücken Sie die **[!UICONTROL Rücktaste]** oder klicken Sie auf **[!UICONTROL Mehr]** (Reihe von drei Punkten) und dann auf **[!UICONTROL Löschen]**.

## Zeigen Sie eine Vorschau der gemischten Mediensets an {#previewing-mixed-media-sets}

Weitere Informationen zum Aufrufen der Vorschau von gemischten Mediensets finden Sie in [Asset-Vorschau](/help/assets/dynamic-media/previewing-assets.md).

## Veröffentlichen von gemischten Mediensets {#publishing-mixed-media-sets}

Weitere Informationen zum Veröffentlichen von gemischten Mediensets finden Sie in [Veröffentlichen von Assets](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

>[!NOTE]
>
>Wenn das gemischte Medienset bei der ersten Veröffentlichung nicht vollständig an den Bereitstellungs-Service übertragen wird, veröffentlichen Sie das gemischte Medienset erneut.
