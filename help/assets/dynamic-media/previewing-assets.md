---
title: Anzeigen von Assets in einer Vorschau
description: Erfahren Sie, wie Sie Assets in Dynamic Media in einer Vorschau anzeigen.
translation-type: ht
source-git-commit: 6224d193adfb87bd9b080f48937e0af1f03386d6

---


# Anzeigen von Assets in einer Vorschau{#previewing-assets}

Mit der Vorschau können Sie prüfen, wie ein von Ihnen hochgeladenes digitales Asset aussieht, wenn es von einem Kunden im eigenen Webbrowser angezeigt wird. Die Vorschau erfolgt über den eingebetteten, geräteübergreifenden Standard-Viewer, der dem Asset zugewiesen ist.

Ein Viewer ist eine Sammlung aus verschiedenen Einstellungen oder „Vorgaben“, wie die Viewer-Anzeigegröße, das Zoom-Verhalten, die Farbschemata, Rahmen, Schriftarten usw., die bestimmen, wie Rich-Media-Assets auf den Computerbildschirmen und Mobilgeräten der Benutzer angezeigt werden.

Sie können die dedizierte Vorschaufunktion für Videos, Rotationssets und Bildsets verwenden, Assets aber auch über von Ihnen erstellte Viewer-Vorgaben in der Vorschau anzeigen. Alternativ dazu können Sie auch Bildvorgaben verwenden, um Ausgabeformate von Bildern anzuzeigen.

* [Anwenden von Bildvorgaben](/help/assets/dynamic-media/image-presets.md)
* [Anwenden von Viewer-Vorgaben](/help/assets/dynamic-media/viewer-presets.md)

>[!NOTE]
>
>Auf einer Webseite (Sites) in AEM können Sie Assets im Modus **Bearbeiten** nicht in einer Vorschau anzeigen. Navigieren Sie in den **Vorschaumodus**, indem Sie in der oberen rechten Ecke auf **Vorschau** klicken.

Informationen zum Aktivieren oder Deaktivieren von Viewer-Vorgaben in der Benutzeroberfläche finden Sie in [Verwalten von Viewer-Vorgaben](/help/assets/dynamic-media/managing-viewer-presets.md).

**So zeigen Sie die Asset-Vorschau an**

1. Tippen Sie in **Adobe Experience Manager** auf der Seite **Navigation** auf **[!UICONTROL Assets]** und **[!UICONTROL Dateien]**, um auf Assets zuzugreifen.
1. Tippen Sie rechts oben auf der Seite in der Dropdown-Liste **[!UICONTROL Ansicht]** auf **[!UICONTROL Listenansicht]**.
1. (Optional) Sortieren Sie in der Spalte **[!UICONTROL Typ]** die Assets nach dem Typ, den Sie in einer Vorschau anzeigen möchten.
1. Klicken Sie in der Spalte **[!UICONTROL Titel]** auf den Namen des Titels (nicht auf die Miniaturansicht) des Assets, das Sie in der Vorschau anzeigen möchten.
1. Führen Sie je nach ausgewähltem Asset eine der folgenden Aktionen aus:

   <table>
    <tbody>
      <tr>
      <td><strong>Per Klick ausgewählter Asset-Typ</strong><br /> </td>
      <td><strong>Asset-Vorschau in bestimmtem Ausgabeformat möglich?</strong></td>
      <td><strong>Asset-Vorschau in bestimmtem Viewer möglich?</strong></td>
      </tr>
      <tr>
      <td><p>Bild</p> </td>
      <td>Ja</td>
      <td>Ja</td>
      <td><p><strong>Asset-Vorschau in bestimmtem Ausgabeformat</strong></p>
        <ul>
        <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdownliste angezeigt wird. Klicken Sie in der Liste auf <strong>Ausgabeformate</strong> und wählen Sie dann das Ausgabeformat, das Sie in einer Vorschau anzeigen möchten.</li>
        </ul> <p><strong>Asset-Vorschau in bestimmtem Viewer</strong></p>
        <ul>
        <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdownliste angezeigt wird. Klicken Sie in der Liste auf <strong>Viewer</strong>. Wählen Sie dann einen Viewer aus, den Sie auf das Asset anwenden möchten.</li>
        </ul> <p>Mit den Symbolen <strong>+</strong> und <strong>-</strong> können Sie den Zoom des gewählten Bildes erhöhen bzw. verkleinern. Klicken Sie auf <strong>Zurücksetzen</strong>, um den Original-Zoom des Bildes wiederherzustellen.<br /> Mit einem Mobilgerät können Sie durch Doppeltippen auf das Bild in Schritten einzoomen. Wenn Sie den maximalen Zoom erreicht haben, doppeltippen Sie erneut auf das Bild, um den Zoomstatus zurückzusetzen. Streichen Sie mit dem Finger über das Bild, um es zu schwenken.</p> </td>
      </tr>
      <tr>
      <td>Multimedia</td>
      <td>Ja</td>
      <td>Ja</td>
      <td><p><strong>Asset-Vorschau in bestimmtem Ausgabeformat</strong></p>
        <ul>
        <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdownliste angezeigt wird. Klicken Sie in der Liste auf <strong>Ausgabeformate</strong> und wählen Sie dann das Ausgabeformat, das Sie in einer Vorschau anzeigen möchten.</li>
        </ul> <p>Wenn Sie ein Videoausgabeformat mit einer höheren Auflösung für die Vorschau auswählen, kann das Video abgeschnitten werden. Dies liegt daran, dass in der Vorschau des Ausgabeformats die genaue Auflösung angezeigt wird, die auch die Kunden sehen, und zwar im Kontext des eingebetteten Viewers, über den die Vorschau erfolgt.</p> <p>Wenn Sie die Vorschau eines adaptiven Videosets auf Asset-Ebene anzeigen, werden die Ausgabeformate in ein Wiedergabeerlebnis zusammengefasst. Das heißt, das adaptive Video wird entsprechend für die Anzeige skaliert und mit der optimalen Auflösung im Kontext des Anzeigegeräts und der Verbindungsgeschwindigkeit wiedergegeben.<br /> </p> <p><strong>Vorschau eines Assets in einem bestimmten Viewer anzeigen</strong></p>
        <ul>
        <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdownliste angezeigt wird. Klicken Sie in der Liste auf <strong>Viewer</strong>. Wählen Sie dann einen Viewer aus, den Sie auf das Asset anwenden möchten.</li>
        </ul> </td>
      </tr>
      <tr>
      <td>Bildset</td>
      <td>Nein</td>
      <td>Ja</td>
      <td><p><strong>Vorschau eines Assets in einem bestimmten Viewer anzeigen</strong></p>
        <ul>
        <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdownliste angezeigt wird. Klicken Sie in der Liste auf <strong>Viewer</strong>. Wählen Sie dann einen Viewer aus, den Sie auf das Asset anwenden möchten.</li>
        </ul> <p>Mit den Symbolen <strong>+</strong> und <strong>-</strong> können Sie den Zoom des gewählten Bildes erhöhen bzw. verkleinern. Klicken Sie auf <strong>Zurücksetzen</strong>, um den Original-Zoom des Bildes wiederherzustellen.<br /> Mit einem Mobilgerät können Sie durch Doppeltippen auf das Bild in Schritten einzoomen. Wenn Sie den maximalen Zoom erreicht haben, doppeltippen Sie erneut auf das Bild, um den Zoomstatus zurückzusetzen. Streichen Sie mit dem Finger über das Bild, um es zu schwenken.</p> </td>
      </tr>
      <tr>
      <td>Rotationsset</td>
      <td>Nein</td>
      <td>Ja</td>
      <td><p><strong>Vorschau eines Assets in einem bestimmten Viewer anzeigen</strong></p>
        <ul>
        <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdownliste angezeigt wird. Klicken Sie in der Liste auf <strong>Viewer</strong>. Wählen Sie dann einen Viewer aus, den Sie auf das Asset anwenden möchten.</li>
        </ul> <p>Mit den Symbolen <strong>+</strong> und <strong>-</strong> können Sie den Zoom des gewählten Bildes erhöhen bzw. verkleinern. Klicken Sie auf <strong>Zurücksetzen</strong>, um den Original-Zoom des Bildes wiederherzustellen.<br /> Mit einem Mobilgerät können Sie durch Doppeltippen auf das Bild in Schritten einzoomen. Wenn Sie den maximalen Zoom erreicht haben, doppeltippen Sie erneut auf das Bild, um den Zoomstatus zurückzusetzen. Streichen Sie mit dem Finger über das Bild, um es zu schwenken.</p> </td>
      </tr>
      <tr>
      <td>Sets für gemischte Medien</td>
      <td>Nein</td>
      <td>Ja</td>
      <td><p><strong>Vorschau eines Assets in einem bestimmten Viewer anzeigen</strong></p>
        <ul>
        <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdownliste angezeigt wird. Klicken Sie in der Liste auf <strong>Viewer</strong>. Wählen Sie dann einen Viewer aus, den Sie auf das Asset anwenden möchten.</li>
        </ul> <p>Mit den Symbolen <strong>+</strong> und <strong>-</strong> können Sie den Zoom des gewählten Bildes erhöhen bzw. verkleinern. Klicken Sie auf <strong>Zurücksetzen</strong>, um den Original-Zoom des Bildes wiederherzustellen.<br /> Mit einem Mobilgerät können Sie durch Doppeltippen auf das Bild in Schritten einzoomen. Wenn Sie den maximalen Zoom erreicht haben, doppeltippen Sie erneut auf das Bild, um den Zoomstatus zurückzusetzen. Streichen Sie mit dem Finger über das Bild, um es zu schwenken.</p> </td>
      </tr>
      <tr>
      <td>Karussell-Set</td>
      <td>Nein</td>
      <td>Ja</td>
      <td><strong>Asset-Vorschau in bestimmtem Viewer</strong>
        <ul>
        <li>Klicken Sie oben links auf der Seite auf das Symbol, damit die Dropdownliste angezeigt wird. Wählen Sie einen Viewer aus, den Sie auf das Asset anwenden möchten.</li>
        </ul> </td>
      </tr>
      <tr>
      <td>360-Grad-Video<br /> </td>
      <td>Ja</td>
      <td>Ja</td>
      <td><p><strong>Asset-Vorschau in bestimmtem Ausgabeformat</strong></p>
        <ul>
        <li>Tippen Sie oben links auf der Seite auf das Symbol, damit die Dropdownliste angezeigt wird. Wählen Sie <strong>Ausgabeformate</strong> und dann das Ausgabeformat aus, das Sie in der Vorschau anzeigen möchten.</li>
        </ul> <p><strong>Asset-Vorschau in bestimmtem Viewer</strong></p>
        <ul>
        <li>Tippen Sie oben links auf der Seite auf das Symbol, damit die Dropdownliste angezeigt wird. Wählen Sie <strong>Viewer</strong> und dann einen Viewer aus, den Sie auf das Asset anwenden möchten.</li>
        </ul> <p>Mit den Symbolen <strong>+</strong> und <strong>-</strong> können Sie den Zoom des gewählten Bildes erhöhen bzw. verkleinern. Klicken Sie auf <strong>Zurücksetzen</strong>, um den Original-Zoom des Bildes wiederherzustellen.<br /> Mit einem Mobilgerät können Sie durch Doppeltippen auf das Bild in Schritten einzoomen. Wenn Sie den maximalen Zoom erreicht haben, doppeltippen Sie erneut auf das Bild, um den Zoomstatus zurückzusetzen. Streichen Sie mit dem Finger über das Bild, um es zu schwenken.</p> </td>
      </tr>
    </tbody>
    </table>
