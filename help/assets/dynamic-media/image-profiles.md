---
title: Dynamic Media-Bildprofile
description: Erfahren Sie, wie Sie Dynamic Media-Bildprofile erstellen, die Einstellungen für Unschärfemasken, smartes Zuschneiden oder smarte Farb-/Bildmuster (oder beides) enthalten. Wenden Sie dann das Profil auf einen Ordner mit Bild-Assets an.
feature: Asset Management,Image Profiles,Renditions
role: User
exl-id: 0856f8a1-e0a9-4994-b338-14016d2d67bd
source-git-commit: f5758056565286015fe115677800310f6bf43e69
workflow-type: tm+mt
source-wordcount: '3219'
ht-degree: 76%

---

# Dynamic Media-Bildprofile {#image-profiles}

Wenn Sie Bilder hochladen, können Sie das Bild nach dem Hochladen automatisch zuschneiden, indem Sie ein neues Bildprofil auf den Ordner anwenden.

>[!IMPORTANT]
>
>Bildprofile können nicht auf PDF-, animierte GIF- oder INDD-Dateien (Adobe InDesign) angewendet werden.

## Option &quot;Unschärfemaske&quot; {#unsharp-mask}

Beim Erstellen eines Bildprofils können Sie die **[!UICONTROL Unschärfemaske]** Option zum Optimieren eines Scharfzeichnungsfiltereffekts für das endgültige heruntergesampelte Bild. Sie können die Intensität des Effekts, den Radius des Effekts (gemessen in Pixel) und einen Schwellenwert für den Kontrast festlegen, der ignoriert werden soll. Dieser Effekt verwendet dieselben Optionen wie der Adobe Photoshop-Filter „Unscharf maskieren“.

>[!NOTE]
>
>Die Unschärfemaske wird nur auf herunterskalierte Ausgabedarstellungen im PTIFF (Pyramiden-TIFF) angewendet, die mehr als 50 % heruntergesampelt sind. Daher werden die größten Ausgabeformate im PTIFF nicht durch die Unschärfemaske beeinflusst. Kleinere Ausgabedarstellungen wie Miniaturen werden allerdings geändert (und hierbei wird die Unschärfemaske angezeigt).

In **[!UICONTROL Unschärfemaske]** sind die folgenden Filteroptionen verfügbar:

<table>
 <tbody>
  <tr>
   <td><strong>Option</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>Stärke</td>
   <td>Steuert den auf die Kantenpixel angewendeten Kontrastwert. Der Standardwert ist 1,75. Bei hochauflösenden Bildern können Sie ihn auf bis zu 5 erhöhen. Der Wert dient hierbei als ein Maß für die Filterintensität. Bereich: 0-5.</td>
  </tr>
  <tr>
   <td>Radius</td>
   <td>Bestimmt die Anzahl der Pixel um die Kantenpixel, auf die sich die Scharfzeichnung auswirkt. Bei hochauflösenden Bildern geben Sie einen Wert zwischen 1 und 2 ein. Bei einem niedrigen Wert werden lediglich die Kantenpixel scharfgezeichnet, bei einem hohen Wert werden mehr Pixel scharfgezeichnet. Der korrekte Wert hängt von der Bildgröße ab. Der Standardwert ist 0,2. Bereich: 0-250.</td>
  </tr>
  <tr>
   <td>Schwelle</td>
   <td><p>Bestimmt den Kontrastbereich, der bei der Anwendung des Filters „Unschärfemaske“ ignoriert werden soll. In anderen Worten: Die Option bestimmt, wie stark sich die scharfgezeichneten Pixel vom Umgebungsbereich unterscheiden müssen, damit sie als Kantenpixel eingestuft und scharfgezeichnet werden. Um Rauschen zu vermeiden, experimentieren Sie mit Werten zwischen 0 und 255.</p> </td>
  </tr>
 </tbody>
</table>

Das Scharfzeichnen wird unter [Scharfzeichnen von Bildern](/help/assets/dynamic-media/assets/sharpening_images.pdf) beschrieben.

## Optionen für das Zuschneiden {#crop-options}

<!-- CQDOC-16069 for the paragraph directly below -->

Die Koordinaten für das smarte Zuschneiden hängen vom Seitenverhältnis ab. Für die verschiedenen Einstellungen zum smarten Zuschneiden in einem Bildprofil wird dasselbe Seitenverhältnis an Dynamic Media gesendet, wenn es den hinzugefügten Abmessungen im Bildprofil entspricht. Adobe empfiehlt, denselben Zuschneidebereich zu verwenden. Dadurch werden die im Bildprofil verwendeten verschiedenen Abmessungen nicht beeinträchtigt.

Jeder von Ihnen erstellte smarte Zuschnitt erfordert zusätzliche Verarbeitungsschritte. Das Hinzufügen von mehr als fünf Seitenverhältnissen für smartes Zuschneiden kann beispielsweise zu einer langsamen Asset-Erfassungsrate führen. Dies kann auch zu einer erhöhten Belastung der Systeme führen. Da Sie smartes Zuschneiden auf Ordnerebene anwenden können, empfiehlt Adobe, es *nur* in Ordnern anzuwenden, in denen es erforderlich ist.

Es stehen zwei Optionen für das Zuschneiden zur Auswahl. Sie können auch die Erstellung von Farb- und Bildmustern automatisieren oder den Zuschnittinhalt über Zielauflösungen hinweg beibehalten.

>[!IMPORTANT]
>
>Adobe empfiehlt, alle erzeugten Zuschnitte und Farb-/Bildmuster zu überprüfen, um sicherzustellen, dass sie für Ihre Marke und Ihre Werte angemessen und relevant sind.

| Option | Wann ist sie einzusetzen? | Beschreibung |
| --- | --- | --- |
| **[!UICONTROL Pixelzuschnitt]** | Nur Massenzuschnitt von Bildern basierend auf Dimensionen. | Aus dem **[!UICONTROL Zuschnittsoptionen]** Dropdown-Liste auswählen **[!UICONTROL Pixelzuschnitt]**.<br>Um von den Seiten eines Bildes zu beschneiden, geben Sie die Anzahl der Pixel ein, die von einer beliebigen Seite oder von jeder Seite des Bildes abgeschnitten werden sollen. Wie viel des Bildes beschnitten wird, hängt von der ppi-Einstellung (Pixel pro Zoll) in der Bilddatei ab.<br>Ein Bildprofil-Pixelzuschnitt wird wie folgt gerendert:<br>・ Die Werte sind oben, unten, links und rechts.・ Oberer links wird berücksichtigt `0,0` und der Pixelzuschnitt von dort berechnet wird.<br>・ Ausgangspunkt des Zuschnitts: Links ist X und oben ist Y<br>・ Horizontale Berechnung: horizontale Pixelgröße des Originalbilds abzüglich links und dann abzüglich rechts.<br>• Vertikale Berechnung: Die vertikale Pixelhöhe abzüglich des Werts für oben und dann abzüglich des Werts für unten.<br>Beispiel: Sie haben ein Bild in der Größe 4000 x 3000 Pixel. Sie verwenden folgende Werte: Oben = 250, Unten = 500, Links = 300, Rechts = 700.<br>Schneiden Sie von oben links (300, 250) aus mit dem Füllraum 4000-300-700, 3000-250-500 oder 3000, 2250. |
| **[!UICONTROL Smartes Zuschneiden]** | Massenzuschnitt von Bildern basierend auf ihrem visuellen Fokus. | Smartes Zuschneiden nutzt die Möglichkeiten künstlicher Intelligenz in Adobe Sensei, um den Massenzuschnitt von Bildern schnell zu automatisieren. Smartes Zuschneiden erkennt automatisch den Fokus in jedem Bild und schneidet es entsprechend zu, um das Haupt-Bildmotiv richtig zu erfassen – unabhängig von der Bildschirmgröße.<br>Aus dem **[!UICONTROL Zuschnittsoptionen]** Dropdown-Liste auswählen **[!UICONTROL Smartes Zuschneiden]**, dann rechts von **[!UICONTROL Responsive Bildbeschneidung]**, aktivieren Sie die Funktion .<br>Die standardmäßigen Breakpoint-Größen (**[!UICONTROL Groß]**, **[!UICONTROL Mittel]**, **[!UICONTROL Klein]**) decken alle Größen ab, die die meisten Bilder auf Mobilgeräten, Tablets, Desktops und Bannern verwenden. Sie können die Standardnamen „Groß“, „Mittel“ und „Klein“ beliebig anpassen.<br>Um weitere Breakpoints hinzuzufügen, wählen Sie **[!UICONTROL Zuschnitt hinzufügen]** aus. Wenn Sie einen Zuschnitt löschen möchten, klicken Sie auf das Papierkorb-Symbol. |
| **[!UICONTROL Farb- und Bildmuster]** | Massenweise Erstellung von Bildmustern für die einzelnen Bilder. | **Hinweis:** Smarte Muster werden in Dynamic Media Classic nicht unterstützt.<br>Erkennen und generieren Sie automatisch hochwertige Bildmuster aus Produktbildern, die Farbe oder Material zeigen.<br>Aus dem **[!UICONTROL Zuschnittsoptionen]** Dropdown-Liste auswählen **[!UICONTROL Smartes Zuschneiden]**. Dann rechts von **[!UICONTROL Farb- und Bildmuster]**, aktivieren Sie die Funktion . Geben Sie einen Pixelwert in die **[!UICONTROL Breite]** und **[!UICONTROL Höhe]** Textfelder.<br>Zwar sind alle Bildzuschnitte über die Leiste „Ausgabedarstellungen“ verfügbar, jedoch können Farb- und Bildmuster nur über die Funktion „URL kopieren“ verwendet werden. **** Verwenden Sie Ihre eigene Ansichtskomponente, um den Musterabschnitt Farbfeld auf Ihrer Site zu rendern. Hiervon ausgenommen sind Karussellbanner. Dynamic Media bietet die Anzeigekomponente für in entsprechenden Bannern verwendete Farb-/Bildmuster.<br><br>**Verwenden von Bildmustern**<br> Die URL für Bildmuster ist einfach:<br>`/is/image/company/&lt;asset_name&gt;:Swatch`<br>Wo `:Swatch` an die Asset-Anfrage angehängt.<br><br>**Verwenden von Farbmustern**<br> Um Farbmuster zu verwenden, erstellen Sie eine `req=userdata` Anfrage mit folgendem Inhalt:<br>`/is/image/&lt;company_name&gt;/&lt;swatch_asset_name&gt;:Swatch?req=userdata`<br><br>Folgendes ist beispielsweise ein Farbmuster-Asset in Dynamic Media Classic:<br>`https://my.company.com:8080/is/image/DemoCo/Sleek:Swatch`<br>Hier finden Sie die zugehörigen Informationen zum Farbmuster-Asset. `req=userdata` URL:<br>`https://my.company.com:8080/is/image/DemoCo/Sleek:Swatch?req=userdata`<br>Die `req=userdata` Antwort wie folgt:<br>`SmartCropDef=Swatch`<br>`SmartCropHeight=200.0`<br>`SmartCropRect=0.421671,0.389815,0.0848564,0.0592593,200,200`<br>`SmartCropType=Swatch`<br>`SmartCropWidth=200.0`<br>`SmartSwatchColor=0xA56DB2`<br>Sie können auch eine `req=userdata` Antwort im XML- oder JSON-Format wie in den folgenden URL-Beispielen gezeigt:<br>・`https://my.company.com</code>:8080/is/image/DemoCo/Sleek:Swatch?req=userdata,json`<br>・`https://my.company.com:8080/is/image/DemoCo/Sleek:Swatch?req=userdata,xml`<br><br>**Hinweis**: Sie müssen eine eigene WCM-Komponente erstellen, um ein Farbmuster anzufordern und die `SmartSwatchColor` -Attribut, dargestellt durch einen 24-Bit-RGB-Hexadezimalwert.<br>Siehe auch [`userdata`](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/req/r-userdata.html)„“ im Viewer-Referenzhandbuch. |
| **[!UICONTROL Zugeschnittene Inhalte für alle Zielauflösungen beibehalten]** | So halten Sie den Zuschnittinhalt über das gleiche Seitenverhältnis | Verwenden Sie diese Option, wenn Sie ein Profil für smartes Zuschneiden erstellen.<br>Wenn Sie dieses Kontrollkästchen deaktivieren, wird für ein bestimmtes Seitenverhältnis über verschiedene Auflösungen hinweg ein neuer Zuschnittinhalt erstellt, wobei der Fokuspunkt beibehalten wird.<br>Wenn Sie dieses Kontrollkästchen deaktivieren, stellen Sie sicher, dass die Originalbildauflösung größer ist als die für Ihr Profil für smartes Zuschneiden definierten Auflösungen.<br><br>Angenommen, Sie haben die Seitenverhältnisse auf 600 x 600 (groß), 400 x 400 (mittel) und 300 x 300 (klein) eingestellt. <br>Mit **[!UICONTROL Bewahren Sie den Zuschnittinhalt über Zielauflösungen hinweg auf]** option *aktiviert* würde derselbe Zuschnitt für alle drei Auflösungen angezeigt, was zur folgenden Ausgabe führte:<br>![Option aktiviert](/help/assets/dynamic-media/assets/preserve-checked.png)<br><br>Mit **[!UICONTROL Bewahren Sie den Zuschnittinhalt über Zielauflösungen hinweg auf]** option *deaktiviert*, ist der Zuschnittinhalt für alle drei Auflösungen neu, was zur folgenden Ausgabe führt:<br>![Option deaktiviert](/help/assets/dynamic-media/assets/preserve-unchecked.png) |

### Unterstützte Bilddateiformate für smartes Zuschneiden und Farbmuster

Die maximal unterstützte Auflösung der Eingabedatei beträgt 16K.

| Bildformat | Dateierweiterung ohne Berücksichtigung der Groß-/Kleinschreibung | MIME-Typ | Unterstützter Eingabefarbraum | Maximale unterstützte Größe der Eingabedatei | Unterstütztes Bildformat? |
| --- | --- | --- | --- | --- | --- |
| BMP | `.bmp` | image/bmp | sRGB | 4 GB | Ja |
| EPS |  |  |  |  | Nein |
| GIF | `.gif` | image/gif | sRGB | 15 GB | Ja; Der erste Frame des animierten GIF wird für die Ausgabedarstellung verwendet. Sie können den ersten Frame weder konfigurieren noch ändern. |
| JPEG | `.jpg` und `.jpeg` | image/jpeg | sRGB | 15 GB | Ja |
| PNG | `.png` | image/png | sRGB | 15 GB | Ja |
| PSD | `.psd` | image/vnd.adobe.photoshop | sRGB<br>CMYK | 2 GB | Ja |
| SVG |  |  |  |  | Nein |
| TIFF | `.tif` und `.tiff` | image/tiff | sRGB<br>CMYK | 4 GB | Ja |
| WebP/Animated WebP |  |  |  |  | Nein |

## Erstellen von Dynamic Media-Bildprofilen {#creating-image-profiles}

Informationen zur Definition von erweiterten Verarbeitungsparametern für andere Asset-Typen finden Sie unter [Konfigurieren der Asset-Verarbeitung](config-dm.md#configuring-asset-processing).

Siehe [Informationen zu Dynamic Media – Bildprofile und Videoprofile](/help/assets/dynamic-media/about-image-video-profiles.md).

Informationen hierzu finden Sie auch im Thema über die [Best Practices für die Organisation Ihrer digitalen Assets zur Verwendung von Verarbeitungsprofilen](/help/assets/organize-assets.md).

**So erstellen Sie Bildprofile für Dynamic Media:**

1. Wählen Sie das Adobe Experience Manager-Logo aus und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Bildprofile]**.
1. Um ein Bildprofil hinzuzufügen, wählen Sie **[!UICONTROL Erstellen]** aus.
1. Geben Sie einen Profilnamen und Werte für Unschärfemasken, Zuschneiden oder Farb-/Bildmuster (oder beides) an.

   Tipp: Verwenden Sie einen für den Verwendungszweck spezifischen Profilnamen. Angenommen, Sie möchten ein Profil erstellen, das nur Farb-/Bildmuster generiert. Das heißt, dass „Smartes Zuschneiden“ deaktiviert und „Farb- und Bildmuster“ aktiviert ist. In solchen Fällen können Sie den Profilnamen „Smarte Muster“ verwenden.

   Siehe auch Optionen für [Smartes Zuschneiden und smarte Farb-/Bildmuster](#crop-options) sowie [Unscharf maskieren](#unsharp-mask).

   ![Zuschneiden](assets/crop.png)

1. Wählen Sie **[!UICONTROL Speichern]** aus. Das neu erstellte Profil wird in der Liste der verfügbaren Profile angezeigt.

## Bearbeiten oder Erstellen von Dynamic Media-Bildprofilen {#editing-or-deleting-image-profiles}

1. Wählen Sie das Adobe Experience Manager-Logo aus und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Bildprofile]**.
1. Wählen Sie das Bildprofil aus, das Sie bearbeiten oder entfernen möchten. Um es zu bearbeiten, wählen Sie **[!UICONTROL Bildverarbeitungsprofil bearbeiten]**. Wählen Sie **[!UICONTROL Bildverarbeitungsprofil löschen]** aus, um es zu entfernen.

   ![chlimage_1-254](assets/chlimage_1-254.png)

1. Wenn Sie das Profil bearbeitet haben, speichern Sie die Änderungen. Wenn Sie das Profil löschen, bestätigen Sie, dass Sie es entfernen möchten.

## Anwenden eines Dynamic Media-Bildprofils auf Ordner {#applying-an-image-profile-to-folders}

Wenn Sie ein Bildprofil einem Ordner zuweisen, übernehmen automatisch alle Unterordner das Profil vom übergeordneten Ordner. Demzufolge können Sie einem Ordner nur ein Bildprofil zuweisen. Daher sollten Sie die Ordnerstruktur sorgfältig planen, in der Sie Assets hochladen, speichern, verwenden und archivieren.

Wenn Sie einem Ordner ein anderes Bildprofil zugewiesen haben, überschreibt das neue das vorherige Profil. Die zuvor vorhandenen Ordner-Assets verbleiben unverändert. Das neue Profil wird auf die Assets angewendet, die dem Ordner später hinzugefügt werden.

Ordner, denen ein Profil zugewiesen ist, werden in der Benutzeroberfläche mit dem Namen des Profils aufgelistet, das in der Karte angezeigt wird.

<!-- When you add smart crop to an existing Image Profile, you need to re-trigger the [DAM Update Asset workflow](assets-workflow.md) if you want to generate crops for existing assets in your asset repository. -->

Sie können Bildprofile auf bestimmte Ordner oder global auf alle Assets anwenden.

Sie können Assets in einem Ordner erneut verarbeiten, der bereits über ein vorhandenes Bildprofil verfügt, das Sie nachträglich geändert haben. Informationen hierzu finden Sie unter [Erneutes Verarbeiten von Assets in einem Ordner nach Bearbeitung des zugehörigen Verarbeitungsprofils](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets).

### Anwenden von Dynamic Media-Bildprofilen auf bestimmte Ordner {#applying-image-profiles-to-specific-folders}

Sie können im Menü **[!UICONTROL Tools]** oder, wenn Sie sich im Ordner befinden, über **[!UICONTROL Eigenschaften]** ein Bildprofil auf einen Ordner anwenden.

Ordner, denen bereits ein Profil zugewiesen ist, werden durch die Anzeige des Profilnamens direkt unter dem Ordnernamen gekennzeichnet.

Sie können Assets in einem Ordner erneut verarbeiten, der bereits über ein vorhandenes Videoprofil verfügt, das Sie nachträglich geändert haben. Informationen hierzu finden Sie unter [Erneutes Verarbeiten von Assets in einem Ordner nach Bearbeitung des zugehörigen Verarbeitungsprofils](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets).

#### Anwenden von Dynamic Media-Bildprofilen auf Ordner über die Benutzeroberfläche „Profile“ {#applying-image-profiles-to-folders-from-profiles-user-interface}

1. Wählen Sie das Adobe Experience Manager-Logo aus und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Bildprofile]**.
1. Wählen Sie ein Bildprofil aus, das Sie auf einen oder mehrere Ordner anwenden möchten.

   ![chlimage_1-255](assets/chlimage_1-255.png)

1. Wählen Sie **[!UICONTROL Profil auf Ordner anwenden]** und mindestens einen Ordner aus, den Sie verwenden möchten, um neu hochgeladene Assets zu empfangen. Wählen Sie dann **[!UICONTROL Anwenden]**. Ordner, denen bereits ein Profil zugewiesen ist, werden durch die Anzeige des Profilnamens direkt unter dem Ordnernamen gekennzeichnet.

#### Anwenden von Dynamic Media-Bildprofilen auf Ordner über „Eigenschaften“ {#applying-image-profiles-to-folders-from-properties}

1. Tippen Sie auf das Experience Manager-Logo und navigieren Sie zu **[!UICONTROL Assets]**.
1. Navigieren Sie zu einem *Ordner* (kein Asset), auf den Sie ein Bildprofil anwenden möchten.
1. Führen Sie je nach gewählter Ansicht eine der folgenden Aktionen aus:
   * Bewegen Sie in der Kartenansicht den Mauszeiger auf den Ordner und wählen Sie dann das Häkchen, um ihn auszuwählen.
   * Aktivieren Sie in der Spaltenansicht oder Listenansicht das Kontrollkästchen links neben dem Ordnernamen.
1. Wählen Sie in der Symbolleiste **[!UICONTROL Eigenschaften]** aus.
1. Wechseln Sie zur Registerkarte **[!UICONTROL Dynamic Media-Verarbeitung]**.
1. Wählen Sie unter **[!UICONTROL Bildprofil]** das anzuwendende Profil aus der Dropdown-Liste **[!UICONTROL Profilname]** aus.
1. Wählen Sie oben rechts auf der Seite **[!UICONTROL Speichern und schließen]** aus. Ordner, denen bereits ein Profil zugewiesen ist, werden durch die Anzeige des Profilnamens direkt unter dem Ordnernamen gekennzeichnet.

   ![chlimage_1-256](assets/chlimage_1-256.png)

### Globales Anwenden eines Dynamic Media-Bildprofils {#applying-an-image-profile-globally}

Sie können ein Profil nicht nur auf einen Ordner, sondern auch global anwenden. Das ausgewählte Profil wird auf alle Inhalte angewendet, die in Experience Manager Assets in einem beliebigen Ordner hochgeladen werden.

Sie können Assets in einem Ordner erneut verarbeiten, der bereits über ein vorhandenes Videoprofil verfügt, das Sie nachträglich geändert haben. Informationen hierzu finden Sie unter [Erneutes Verarbeiten von Assets in einem Ordner nach Bearbeitung des zugehörigen Verarbeitungsprofils](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets).

**So wenden Sie ein Dynamic Media-Bildprofil global an:**

1. Führen Sie einen der folgenden Schritte aus:

   * Navigieren Sie zu `https://&lt;AEM server&gt;/mnt/overlay/dam/gui/content/assets/foldersharewizard.html/content/dam` und wenden Sie das entsprechende Profil an und wählen Sie **[!UICONTROL Speichern]** aus.

      ![chlimage_1-257](assets/chlimage_1-257.png)

   * Navigieren Sie in CRXDE Lite zum folgenden Knoten: `/content/dam/jcr:content`.

      Fügen Sie die Eigenschaft `imageProfile:/conf/global/settings/dam/adminui-extension/imageprofile/<name of image profile>` hinzu und wählen Sie **[!UICONTROL Alle speichern]**.

      ![configure_image_profiles](assets/configure_image_profiles.png)

## Bearbeiten von smarten Zuschnitten oder smarten Farb-/Bildmustern eines einzelnen Bildes {#editing-the-smart-crop-or-smart-swatch-of-a-single-image}

>[!IMPORTANT]
>
>Adobe empfiehlt, alle erzeugten smarten Zuschnitte und smarten Farb-/Bildmuster zu überprüfen, um sicherzustellen, dass sie für Ihre Marke und Ihre Werte angemessen und relevant sind.

Sie können das Zuschnittsfenster eines Bildes manuell neu ausrichten oder die Größe ändern, um den Fokus präziser zu bestimmen.

Nachdem Sie einen smarten Zuschnitt bearbeitet und gespeichert haben, wird die Änderung überall dort angewendet, wo Sie den Zuschnitt für bestimmte Bilder verwenden.

>[!IMPORTANT]
>
>Wenn Sie das Fenster für das smarte Zuschneiden eines Assets manuell neu ausrichten oder seine Größe ändern, wird diese Bearbeitung beibehalten und beibehalten, auch wenn Sie das Asset später erneut verarbeiten möchten. Wenn Sie jedoch die Breite, Höhe oder beides im **[!UICONTROL Responsive Bildbeschneidung]** -Bereich des Bildprofils ein, kann dieses Asset erneut verarbeitet werden.
>Siehe [Dynamic Media-Assets in einem Ordner erneut verarbeiten](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets).

Sie können einen smarten Zuschnitt erneut ausführen, um die zusätzlichen Zuschnitte ggf. erneut zu generieren.

Siehe auch [Bearbeiten von smarten Zuschnitten oder smarten Farb-/Bildmustern mehrerer Bilder](#editing-the-smart-crop-or-smart-swatch-of-multiple-images).

**So bearbeiten Sie smarte Zuschnitte oder smarte Farb-/Bildmuster eines einzelnen Bildes:**

1. Wählen Sie das Experience Manager-Logo aus und navigieren Sie zu **[!UICONTROL Assets]** und dann zu dem Ordner, auf den das Bildprofil „Smartes Zuschneiden“ oder „Smartes Farb-/Bildmuster“ angewendet wurde.
1. Öffnen Sie den Inhalt, indem Sie den Ordner auswählen.
1. Wählen Sie das Bild aus, dessen smarten Zuschnitt oder smartes Farb-/Bildmuster Sie anpassen möchten.
1. Wählen Sie in der Symbolleiste **[!UICONTROL Smartes Zuschneiden]** aus.

1. Führen Sie einen der folgenden Schritte aus:

   * Ziehen Sie den Schieberegler in der oberen rechten Ecke der Seite nach links oder rechts, um die Bildanzeige zu erweitern oder zu reduzieren.
   * Ziehen Sie im Bild eine Ecke, um die Größe des sichtbaren Bereichs des Zuschnitts oder Farb-/Bildmusters anzupassen.
   * Ziehen Sie das Feld bzw. Farb-/Bildmuster im Bild an eine neue Position. Sie können nur Bildmuster bearbeiten. Farbmuster sind statisch.
   * Wählen Sie über dem Bild **[!UICONTROL Wiederherstellen]** aus, um all Ihre Änderungen rückgängig zu machen und den ursprünglichen Zuschnitt bzw. das Farb-/Bildmuster wiederherzustellen.
   * Mit den Pfeiltasten können Sie die Bildgröße zuschneiden oder das Bild neu positionieren (oder beides).

1. Wählen Sie in der oberen rechten Ecke der Seite **[!UICONTROL Speichern]** und anschließend **[!UICONTROL Schließen]** aus, um zum Asset-Ordner zurückzukehren.

## Bearbeiten von smarten Zuschnitten oder smarten Farb-/Bildmustern mehrerer Bilder {#editing-the-smart-crop-or-smart-swatch-of-multiple-images}

Nachdem Sie ein Bildprofil (mit der Funktion „Smartes Zuschneiden“) auf einen Ordner angewendet haben, wird der Zuschnitt auf alle Bilder in diesem Ordner angewendet. Sie können das Zuschnittsfenster in mehreren Bildern *manuell* neu ausrichten oder die Größe verändern, um den Fokus präziser zu bestimmen.

Nachdem Sie einen smarten Zuschnitt bearbeitet und gespeichert haben, wird die Änderung überall dort angewendet, wo Sie den Zuschnitt für bestimmte Bilder verwenden.

>[!IMPORTANT]
>
>Wenn Sie das smarte Zuschnittsfenster mehrerer Assets manuell neu ausrichten oder die Größe ändern, werden diese Bearbeitungen beibehalten und beibehalten, selbst wenn Sie sich später entscheiden, diese Assets erneut zu verarbeiten. Wenn Sie jedoch die Breite, Höhe oder beides im **[!UICONTROL Responsive Bildbeschneidung]** -Bereich des Bildprofils ein, können diese Assets erneut verarbeitet werden.
>Siehe [Dynamic Media-Assets in einem Ordner erneut verarbeiten](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets).

Sie können einen smarten Zuschnitt erneut ausführen, um die zusätzlichen Zuschnitte ggf. erneut zu generieren.

**So bearbeiten Sie smarte Zuschnitte oder smarte Farb-/Bildmuster mehrerer Bilder:**

1. Wählen Sie das Experience Manager-Logo aus und navigieren Sie zu **[!UICONTROL Assets]** und dann zu einem Ordner, auf den das Bildprofil „Smartes Zuschneiden“ oder „Smartes Farb-/Bildmuster“ angewendet wurde.
1. Wählen Sie beim entsprechenden Ordner das Symbol **[!UICONTROL Mehr Aktionen]** (...) und anschließend **[!UICONTROL Smartes Zuschneiden]** aus.

1. Führen Sie auf der Seite **[!UICONTROL Smartes Zuschneiden bearbeiten]** eine der folgenden Aktionen durch:

   * Passen Sie die Anzeigegröße von Bildern auf der Seite an.

      Ziehen Sie den Schieberegler rechts neben der Dropdown-Liste mit Breakpoint-Namen nach links oder rechts, um den sichtbaren Bildbereich anzupassen.

      ![edit_smart_products-sliderbar](assets/edit_smart_crops-sliderbar.png)

   * Filtern Sie die Liste sichtbarer Bilder basierend auf Breakpoint-Namen. Im unten stehenden Beispiel werden die Bilder nach dem Breakpoint-Namen „Mittel“ gefiltert.

      Wählen Sie aus der Dropdown-Liste in der oberen rechten Ecke der Seite einen Breakpoint-Namen aus, um zu filtern, welche Bilder Ihnen angezeigt werden. (Siehe Abbildung oben.)

      ![edit_smart_products-dropdownlist](assets/edit_smart_crops-dropdownlist.png)

   * Passen Sie die Größe des Zuschnittsfeldes an. Führen Sie einen der folgenden Schritte aus:

      * Wenn das Bild nur über einen smarten Zuschnitt oder ein smartes Farb-/Bildmuster verfügt, ziehen Sie im Bild die Ecke des Zuschnittsfeldes, um die Größe des sichtbaren Bereichs des Zuschnitts anzupassen.
      * Wenn das Bild sowohl über einen smarten Zuschnitt als auch über ein smartes Farb-/Bildmuster verfügt, ziehen Sie im Bild die Ecke des Zuschnittsfeldes, um die Größe des sichtbaren Bereichs des Zuschnitts anzupassen. Oder wählen Sie das Farb-/Bildmuster unter dem Bild (Farbmuster sind statisch) aus und ziehen Sie die Ecke des Zuschnittsfelds. Passen Sie die Größe des sichtbaren Bereichs des Farb-/Bildmusters an.

      ![Größenänderung des smarten Zuschnitts eines Bildes](assets/edit_smart_crops-resize.png).

   * Verschieben Sie das smarte Zuschnittsfeld. Führen Sie einen der folgenden Schritte aus:

      * Wenn das Bild nur über einen smarten Zuschnitt oder ein smartes Farb-/Bildmuster verfügt, ziehen Sie das Zuschnittsfeld im Bild an eine neue Position.
      * Wenn das Bild sowohl über einen smarten Zuschnitt als auch über ein smartes Farb-/Bildmuster verfügt, ziehen Sie das Zuschnittsfeld im Bild an eine neue Position. Oder wählen Sie unter dem Bild das smarte Bildmuster (Farbmuster sind statisch) aus und ziehen Sie das smarte Zuschnittsfeld an eine neue Position.

      ![edit_smart_cards-move](assets/edit_smart_crops-move.png)

   * Machen Sie all Ihre Änderungen rückgängig und stellen Sie den ursprünglichen smarten Zuschnitt bzw. das smarte Farb-/Bildmuster wieder her (gilt nur für die aktuelle Bearbeitungssitzung).

      Wählen Sie über dem Bild **[!UICONTROL Wiederherstellen]** aus.

      ![edit_smart_cards-revert](assets/edit_smart_crops-revert.png)



1. Wählen Sie in der oberen rechten Ecke der Seite **[!UICONTROL Speichern]** und anschließend **[!UICONTROL Schließen]** aus, um zum Asset-Ordner zurückzukehren.

## Entfernen eines Bildprofils aus Ordnern {#removing-an-image-profile-from-folders}

Wenn Sie ein Bildprofil aus einem Ordner entfernen, erben automatisch alle Unterordner das Entfernen des Profils aus dem übergeordneten Ordner. Die Verarbeitung der Dateien, die in den Ordnern stattgefunden hat, wird jedoch beibehalten.

Sie können im Menü **[!UICONTROL Tools]** oder, wenn Sie sich im Ordner befinden, über **[!UICONTROL Eigenschaften]** ein Bildprofil aus einem Ordner entfernen.

### Entfernen von Dynamic Media-Bildprofilen aus Ordnern über die Benutzeroberfläche „Profile“ {#removing-image-profiles-from-folders-via-profiles-user-interface}

1. Wählen Sie das Adobe Experience Manager-Logo aus und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Bildprofile]**.
1. Wählen Sie ein Bildprofil aus, das Sie aus einem Ordner oder mehreren Ordnern entfernen möchten.
1. Wählen Sie **[!UICONTROL Verarbeitungsprofil aus Ordner(n) entfernen]** und anschließend einen oder mehrere Ordner aus, aus denen das Profil entfernt werden soll. Wählen Sie dann **[!UICONTROL Entfernen]** aus.

   Sie können überprüfen, ob das Bildprofil nicht länger auf einen Ordner angewendet wird, da der Name in diesem Fall nicht mehr unter dem Ordner angezeigt wird.

### Entfernen von Dynamic Media-Bildprofilen aus Ordnern über „Eigenschaften“ {#removing-image-profiles-from-folders-via-properties}

1. Wählen Sie das Experience Manager-Logo aus und navigieren Sie zu **[!UICONTROL Assets]** und dann zu dem Ordner, aus dem Sie ein Bildprofil entfernen möchten.
1. Wählen Sie beim entsprechenden Ordner das Häkchen aus, um es zu aktivieren, und tippen Sie anschließend auf **[!UICONTROL Eigenschaften]**.
1. Wählen Sie die Registerkarte **[!UICONTROL Bildprofile]** aus.
1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Profilname]** die Option **[!UICONTROL Kein]** und dann **[!UICONTROL Speichern und schließen]** aus.

   Ordner, denen bereits ein Profil zugewiesen ist, werden durch die Anzeige des Profilnamens direkt unter dem Ordnernamen gekennzeichnet.
