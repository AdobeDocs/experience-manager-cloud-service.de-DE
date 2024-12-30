---
title: Dynamic Media-Bildprofile
description: Erfahren Sie, wie Sie Dynamic Media-Bildprofile erstellen, die Einstellungen für Unschärfemasken, smartes Zuschneiden oder smarte Farb-/Bildmuster (oder beides) enthalten. Wenden Sie dann das Profil auf einen Ordner mit Bild-Assets an.
contentOwner: Rick Brough
feature: Asset Management,Image Profiles,Renditions,Best Practices
role: User
exl-id: 0856f8a1-e0a9-4994-b338-14016d2d67bd
source-git-commit: 0ad506fc72cb73d3a6a8cdd9eee50f213b52665e
workflow-type: tm+mt
source-wordcount: '3518'
ht-degree: 100%

---

# Dynamic Media-Bildprofile {#image-profiles}

Wenn Sie Bilder hochladen, können Sie das Bild nach dem Hochladen automatisch zuschneiden, indem Sie ein neues Bildprofil auf den Ordner anwenden.

>[!IMPORTANT]
>
>Bildprofile können nicht auf PDF-, animierte GIF- oder INDD-Dateien (Adobe InDesign) angewendet werden.

## Option „Unscharf maskieren“ {#unsharp-mask}

Beim Erstellen eines Bildprofils können Sie die Option **[!UICONTROL Unscharf maskieren]** verwenden, um einen Scharfzeichnungsfiltereffekt für das endgültige, heruntergesampelte Bild fein abzustimmen. Sie können die Intensität des Effekts, den Radius des Effekts (gemessen in Pixel) und einen Schwellenwert für den Kontrast festlegen, der ignoriert werden soll. Dieser Effekt verwendet dieselben Optionen wie der Adobe Photoshop-Filter „Unscharf maskieren“.

>[!NOTE]
>
>„Unscharf maskieren“ wird nur auf neu berechnete Ausgabedarstellungen im PTIFF (Pyramiden-TIFF) angewendet, die um mehr als 50 % heruntergerechnet sind. Der Filter „Unscharf maskieren“ wirkt sich nicht auf die größten Ausgabedarstellungen im PTIFF aus. Kleinere Ausgabedarstellungen wie Miniaturen werden allerdings geändert (und hierbei wird die Unschärfemaske angezeigt).

In **[!UICONTROL Unschärfemaske]** sind die folgenden Filteroptionen verfügbar:

<table>
 <tbody>
  <tr>
   <td><strong>Option</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>Stärke</td>
   <td>Steuert die Stärke des Kontrasts, der auf Kanten-Pixel angewendet wird. Der Standardwert ist 1,75. Bei hochauflösenden Bildern können Sie ihn auf bis zu 5 erhöhen. Stellen Sie sich die Stärke als ein Maß für die Filterintensität vor. Der Bereich ist 0–5.</td>
  </tr>
  <tr>
   <td>Radius</td>
   <td>Bestimmt die Anzahl der Pixel um die Kanten-Pixel, auf die sich die Scharfzeichnung auswirkt. Bei hochauflösenden Bildern geben Sie einen Wert zwischen 1 und 2 ein. Bei einem niedrigen Wert werden lediglich die Kanten-Pixel scharf gezeichnet, bei einem hohen Wert werden mehr Pixel scharf gezeichnet. Der korrekte Wert hängt von der Bildgröße ab. Der Standardwert ist 0,2. Der Bereich liegt zwischen 0 und 250.</td>
  </tr>
  <tr>
   <td>Schwellenwert</td>
   <td><p>Bestimmt den Kontrastbereich, der bei Anwendung des Filters „Unscharf maskieren“ ignoriert werden soll. Diese Option steuert, wie stark sich die scharf gezeichneten Pixel vom Umgebungsbereich unterschieden müssen, damit sie als Kantenpixel eingestuft werden. Es werden nur die Pixel scharf gezeichnet, die diesen Schwellenwert erreichen. Um Rauschen zu vermeiden, experimentieren Sie mit Ganzzahlwerten zwischen 0 und 255.</p> </td>
  </tr>
 </tbody>
</table>

Das Scharfzeichnen wird unter [Scharfzeichnen von Bildern](/help/assets/dynamic-media/assets/sharpening_images.pdf) beschrieben.

## Optionen für das Zuschneiden {#crop-options}

Wenn Sie smartes Zuschneiden für Bilder implementieren, empfiehlt Adobe die folgende Best Practice und erzwingt die folgende Beschränkung:

| Asset – Art des Grenzwerts | Best Practice | Erzwungene Begrenzung |
| --- | --- | --- |
| **Bild**: Anzahl der smarten Zuschnitte pro Bild | 5 | 100 |

Siehe auch [Dynamic Media-Beschränkungen](/help/assets/dynamic-media/limitations.md).

<!-- CQDOC-16069 for the paragraph directly below -->

Die Koordinaten für das smarte Zuschneiden hängen vom Seitenverhältnis ab. Für die verschiedenen Einstellungen zum smarten Zuschneiden in einem Bildprofil wird dasselbe Seitenverhältnis an Dynamic Media gesendet, wenn es den hinzugefügten Abmessungen im Bildprofil entspricht. Adobe empfiehlt, denselben Zuschneidebereich zu verwenden. Dadurch werden die im Bildprofil verwendeten verschiedenen Abmessungen nicht beeinträchtigt.

Jeder von Ihnen erstellte smarte Zuschnitt erfordert eine zusätzliche Verarbeitung. Beispielsweise kann das Hinzufügen von mehr als fünf Seitenverhältnissen für das smarte Zuschneiden eine verlangsamte Aufnahme von Assets zur Folge haben. Dies kann auch zu einer erhöhten Belastung der Systeme führen. Da der intelligente Zuschnitt auf Ordnerebene angewendet werden kann, empfiehlt Adobe, die Option nur für Ordner zu verwenden, bei denen dies erforderlich ist.

**Richtlinien zum Definieren von intelligentem Zuschneiden in einem Bildprofil**
Um die Verwendung von intelligentem Zuschneiden unter Kontrolle zu halten und die Verarbeitungszeit und die Speicherung von Zuschnitten zu optimieren, empfiehlt Adobe Folgendes:

* Für Bild-Assets, auf die ein smartes Zuschneiden angewendet wird, muss mindestens 50 x 50 Pixel groß sein.
* Idealerweise sollten Sie pro Bild 10 bis 15 smarte Zuschnitte vornehmen, um das Bildschirmverhältnis und die Verarbeitungszeit zu optimieren.
* Benennen Sie smarte Zuschnitte basierend auf Zuschnittdimensionen und nicht auf der Endverwendung. Dies hilft bei der Optimierung für Duplikate, bei denen eine einzelne Dimension auf mehreren Seiten verwendet wird.
* Erstellen Sie Bildprofile per Seite oder per Asset für spezifische Ordner und Unterordner anstatt eines gemeinsamen Profils für smartes Zuschneiden, das auf alle Ordner oder alle Assets angewendet wird.
* Ein Bildprofil, das Sie auf Unterordner anwenden, überschreibt ein Bildprofil, das auf den Ordner angewendet wird.
* Ein Bildprofil, das doppelte smarte Zuschnittdimensionen enthält, ist nicht zulässig.
* Duplizierte Bildprofile mit Namen, für die Optionen für das smarte Zuschneiden festgelegt sind, sind nicht zulässig.

Sie können zwischen zwei Optionen zum Zuschneiden von Bildern wählen: Pixelzuschnitt und intelligenter Zuschnitt. Sie können auch die Erstellung von Farb- und Bildmustern automatisieren oder einen zugeschnittenen Inhalt über Zielauflösungen hinweg beibehalten.

>[!IMPORTANT]
>
>Adobe empfiehlt, alle erzeugten Zuschnitte und Farbfelder zu überprüfen, um sicherzustellen, dass sie für Ihre Marke und Ihre Werte angemessen und relevant sind.

| Option | Wann ist sie einzusetzen? | Beschreibung |
| --- | --- | --- |
| **[!UICONTROL Pixel-Zuschnitt]** | Nur Massenzuschnitt von Bildern basierend auf Dimensionen. | Wählen Sie in der Dropdown-Liste **[!UICONTROL Zuschnittsoptionen]** die Option **[!UICONTROL Pixel-Zuschnitt]**.<br> Um ein Bild an den Seiten zuzuschneiden, geben Sie die Anzahl der Pixel ein, die von einer Seite oder jeder Seite des Bildes abgeschnitten werden sollen. Wieviel von dem Bild abgeschnitten wird, hängt von der ppi-Einstellung (Pixel pro Zoll) in der Bilddatei ab.<br>Ein Pixel-Zuschnitt im Bildprofil wird folgendermaßen dargestellt:<br>• Die Werte sind oben, unten, links und rechts.<br>• links oben wird als `0,0` betrachtet, und der Pixel-Zuschnitt wird von dort aus berechnet.<br>• Ausgangspunkt des Zuschnitts: Links ist X und oben ist Y<br>• Horizontale Berechnung: horizontale Pixel-Größe des Originalbilds abzüglich links und dann abzüglich rechts.<br>• Vertikale Berechnung: Die vertikale Pixel-Höhe abzüglich des Werts für oben und dann abzüglich des Werts für unten.<br>Beispiel: Sie haben ein Bild in der Größe 4000 x 3000 Pixel. Sie verwenden folgende Werte: Oben = 250, Unten = 500, Links = 300, Rechts = 700.<br>Schneiden Sie von oben links (300, 250) aus mit dem Füllraum 4000-300-700, 3000-250-500 oder 3000,2250. |
| **[!UICONTROL Smartes Zuschneiden]** | Massenzuschnitt von Bildern basierend auf ihrem visuellen Fokus. | Der intelligente Zuschnitt nutzt die Leistungsfähigkeit der künstlichen Intelligenz in Adobe Sensei, um das Zuschneiden von Bildern in großen Mengen schnell zu automatisieren. Der intelligente Zuschnitt erkennt automatisch den Fokus in jedem Bild und schneidet es entsprechend zu, um das Haupt-Bildmotiv richtig zu erfassen – unabhängig von der Bildschirmgröße.<br>Wählen Sie aus der Dropdown-Liste **[!UICONTROL Zuschnittsoptionen]** die Option **[!UICONTROL Smartes Zuschneiden]** aus und aktivieren Sie dann die Funktion rechts neben **[!UICONTROL Responsive Bildbeschneidung]** (schalten Sie sie ein).<br>Die standardmäßigen Breakpoint-Größen (**[!UICONTROL Groß]**, **[!UICONTROL Mittel]**, **[!UICONTROL Klein]**) decken alle Größen ab, in denen die meisten Bilder auf Smartphones, Tablets, Desktops und in Bannern verwendet werden. Sie können die Standardnamen „Groß“, „Mittel“ und „Klein“ beliebig anpassen.<br>Um weitere Breakpoints hinzuzufügen, wählen Sie **[!UICONTROL Zuschnitt hinzufügen]** aus. Wenn Sie einen Zuschnitt löschen möchten, klicken Sie auf das Papierkorb-Symbol. |
| **[!UICONTROL Farb- und Bildmuster]** | Massenweise Erstellung von Bildmustern für die einzelnen Bilder. | **Hinweis:** Smarte Muster werden in Dynamic Media Classic nicht unterstützt.<br>Erkennen und generieren Sie automatisch hochwertige Bildmuster aus Produktbildern, die Farbe oder Textur zeigen.<br>Wählen Sie in der Dropdown-Liste **[!UICONTROL Zuschneideoptionen]** die Option **[!UICONTROL Smartes Zuschneiden]**. Aktivieren Sie dann rechts neben **[!UICONTROL Farb- und Bildmuster]** die Funktion (schalten Sie sie ein). Geben Sie in die Textfelder **[!UICONTROL Breite]** und **[!UICONTROL Höhe]** einen Wert in Pixel ein.<br>Zwar sind alle Bildzuschnitte über die Leiste „Ausgabedarstellungen“ verfügbar, jedoch können Farbfelder nur über die Funktion **[!UICONTROL URL kopieren]** verwendet werden. Verwenden Sie Ihre eigene Ansichtskomponente, um den Musterabschnitt Farbfeld auf Ihrer Site zu rendern. Hiervon ausgenommen sind Karussellbanner. Dynamic Media bietet die Anzeigekomponente für in entsprechenden Bannern verwendete Farb-/Bildmuster.<br><br>**Verwenden von Bildmustern**<br> Die URL für Bildmuster ist einfach<br>`/is/image/company/&lt;asset_name&gt;:Swatch`<br>, wobei `:Swatch` an die Asset-Anfrage angehängt wird.<br><br>**Verwenden von Farbmustern**<br> Um Farbmuster zu verwenden, erstellen Sie eine Anfrage `req=userdata` mit folgendem Inhalt:<br>`/is/image/&lt;company_name&gt;/&lt;swatch_asset_name&gt;:Swatch?req=userdata`<br><br>Das Folgende ist beispielsweise ein Farbmuster-Asset in Dynamic Media Classic:<br>`https://my.company.com:8080/is/image/DemoCo/Sleek:Swatch`<br>Hier finden Sie die zugehörige `req=userdata`-URL zum Farbmuster-Asset:<br>`https://my.company.com:8080/is/image/DemoCo/Sleek:Swatch?req=userdata`<br>Die Antwort von `req=userdata` lautet wie folgt:<br>`SmartCropDef=Swatch`<br>`SmartCropHeight=200.0`<br>`SmartCropRect=0.421671,0.389815,0.0848564,0.0592593,200,200`<br>`SmartCropType=Swatch`<br>`SmartCropWidth=200.0`<br>`SmartSwatchColor=0xA56DB2`<br>Sie können auch eine Antwort von `req=userdata` im XML- oder JSON-Format anfordern wie in den folgenden URL-Beispielen gezeigt:<br>•`https://my.company.com</code>:8080/is/image/DemoCo/Sleek:Swatch?req=userdata,json`<br>•`https://my.company.com:8080/is/image/DemoCo/Sleek:Swatch?req=userdata,xml`<br><br>**Hinweis**: Sie müssen Ihre eigene WCM-Komponente erstellen, um ein Farbmuster anzufordern, und das Attribut `SmartSwatchColor` auswerten, das durch einen 24-Bit-RGB-Hexadezimalwert dargestellt wird.<br>Siehe auch [`userdata`](https://experienceleague.adobe.com/de/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/req/r-userdata) im Viewer-Referenzhandbuch. |
| **[!UICONTROL Beibehalten von zugeschnittenen Inhalten für alle Zielauflösungen]** | So behalten Sie den zugeschnittenen Inhalt im gleichen Seitenverhältnis bei | Verwenden Sie diese Option, wenn Sie ein Profil für smartes Zuschneiden erstellen.<br>Um neue Inhalte für das Zuschneiden zu generieren, während der Fokus beibehalten wird, deaktivieren Sie diese Option, um ein bestimmtes Seitenverhältnis über verschiedene Auflösungen hinweg zu erhalten <br>Wenn Sie dieses Kontrollkästchen deaktivieren, sollten Sie sicherstellen, dass die Originalbildauflösung größer ist als die für Ihr Profil für den intelligenten Zuschnitt definierten Auflösungen.<br><br>Angenommen, Sie haben die Seitenverhältnisse auf 600 x 600 (groß), 400 x 400 (mittel) und 300 x 300 (klein) eingestellt.<br>Wenn die Option **[!UICONTROL Zugeschnittene Inhalte über alle Zielauflösungen hinweg beibehalten]** *aktiviert ist* ist, sehen Sie den gleichen Zuschnitt über alle drei Auflösungen hinweg, ähnlich wie in der folgenden Beispielausgabe von Bildern (nur zu Illustrationszwecken): <br>![Option aktiviert](/help/assets/dynamic-media/assets/preserve-checked.png)<br><br>Wenn die Option **[!UICONTROL Zugeschnittene Inhalte in allen Zielauflösungen beibehalten]** *nicht aktiviert* ist, ist der zugeschnittene Inhalt für alle drei Auflösungen neu, ähnlich wie in der folgenden Beispielausgabe von Bildern (nur zur Veranschaulichung):<br>![Option nicht aktiviert](/help/assets/dynamic-media/assets/preserve-unchecked.png) |

### Unterstützte Bilddateiformate für smartes Zuschneiden und Farbfelder

Die maximal unterstützte Auflösung der Eingabedatei beträgt 16K.

>[!NOTE]
>
>Die 16K-Auflösung ist eine Anzeigeauflösung mit etwa 16.000 Pixel horizontal. Die am häufigsten besprochene 16K-Auflösung ist 15360 × 8640, was die Pixel-Anzahl von 8K UHD in jeder Dimension verdoppelt, also insgesamt viermal so viele Pixel ergibt. Diese Auflösung hat 132,7 Megapixel, 16-mal so viele Pixel wie die 4K-Auflösung und 64-mal so viele Pixel wie die 1080p-Auflösung.

| Bildformat | Dateierweiterung ohne Berücksichtigung der Groß-/Kleinschreibung | MIME-Typ | Unterstützter Eingabefarbraum | Maximale unterstützte Größe der Eingabedatei | Unterstütztes Bildformat? |
| --- | --- | --- | --- | --- | --- |
| BMP | `.bmp` | image/bmp | sRGB | 4 GB | Ja |
| CMYK | | | | | Ja |
| EPS | | | | | Nein |
| GIF | `.gif` | image/gif | sRGB | 15 GB | Ja. Der erste Frame des animierten GIF wird für die Ausgabedarstellung verwendet. Sie können den ersten Frame weder konfigurieren noch ändern. |
| JPEG | `.jpg` und `.jpeg` | image/jpeg | sRGB | 15 GB | Ja |
| PNG | `.png` | image/png | sRGB | 15 GB | Ja |
| PSD | `.psd` | image/vnd.adobe.photoshop | sRGB<br>CMYK | 2 GB | Ja |
| SVG | | | | | Nein |
| TIFF | `.tif` und `.tiff` | image/tiff | sRGB<br>CMYK | 4 GB | Ja |
| WebP/Animated WebP | | | | | Nein |

## Erstellen von Dynamic Media-Bildprofilen {#creating-image-profiles}

Informationen zur Definition von erweiterten Verarbeitungsparametern für andere Asset-Typen finden Sie unter [Konfigurieren der Asset-Verarbeitung](config-dm.md#configuring-asset-processing).

Siehe [Informationen zu Dynamic Media – Bildprofile und Videoprofile](/help/assets/dynamic-media/about-image-video-profiles.md).

Informationen hierzu finden Sie auch im Thema über die [Best Practices für die Organisation Ihrer digitalen Assets zur Verwendung von Verarbeitungsprofilen](/help/assets/organize-assets.md).

**So erstellen Sie Bildprofile für Dynamic Media:**

1. Wählen Sie das Adobe Experience Manager-Logo aus und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Bildprofile]**.
1. Um ein Bildprofil hinzuzufügen, wählen Sie **[!UICONTROL Erstellen]** aus.
1. Geben Sie einen Profilnamen und Werte für Unschärfemasken, Zuschneiden oder Farb-/Bildmuster (oder beides) an.

   >[!TIP]
   >
   >Verwenden Sie einen für den Verwendungszweck spezifischen Profilnamen. Angenommen, Sie möchten ein Profil erstellen, das nur Farb-/Bildmuster generiert. Das heißt, dass der intelligente Zuschnitt deaktiviert (ausgeschaltet) und „Farb- und Bildmuster“ aktiviert (eingeschaltet) ist. In solchen Fällen können Sie den Profilnamen „Intelligentes Farbfeld“ verwenden.

   Siehe auch Optionen für [Smartes Zuschneiden und smarte Farb-/Bildmuster](#crop-options) sowie [Unscharf maskieren](#unsharp-mask).

   ![Zuschneiden](assets/crop.png)

1. Wählen Sie **[!UICONTROL Speichern]** aus. Das erstellte Profil wird in der Liste der verfügbaren Profile angezeigt.

## Bearbeiten oder Erstellen von Dynamic Media-Bildprofilen {#editing-or-deleting-image-profiles}

1. Wählen Sie das Adobe Experience Manager-Logo aus und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Bildprofile]**.
1. Wählen Sie das Bildprofil aus, das Sie bearbeiten oder entfernen möchten. Wählen Sie **[!UICONTROL Bildverarbeitungsprofil bearbeiten]** aus, um es zu bearbeiten. Wählen Sie **[!UICONTROL Bildverarbeitungsprofil löschen]** aus, um es zu entfernen.

   ![chlimage_1-254](assets/chlimage_1-254.png)

1. Speichern Sie die Änderungen, wenn Sie es bearbeiten. Wenn Sie ein Profil löschen möchten, bestätigen Sie, dass Sie es entfernen möchten.

## Anwenden eines Dynamic Media-Bildprofils auf Ordner {#applying-an-image-profile-to-folders}

Wenn Sie einem Ordner ein Bildprofil zuweisen, übernehmen automatisch alle Unterordner das Profil vom übergeordneten Ordner. Demzufolge können Sie einem Ordner nur ein Bildprofil zuweisen. Daher sollten Sie die Ordnerstruktur sorgfältig planen, in der Sie Assets hochladen, speichern, verwenden und archivieren.

Wenn Sie einem Ordner ein anderes Bildprofil zugewiesen haben, überschreibt das neue das vorherige Profil. Die zuvor vorhandenen Ordner-Assets verbleiben unverändert. Das neue Profil wird auf die Assets angewendet, die dem Ordner später hinzugefügt werden.

Für Ordner mit einem zugewiesenen Profil wird der Profilname auf der Karte angezeigt.

<!-- When you add smart crop to an existing Image Profile, you need to re-trigger the [DAM Update Asset workflow](assets-workflow.md) if you want to generate crops for existing assets in your asset repository. -->

Sie können Bildprofile auf bestimmte Ordner oder global auf alle Assets anwenden.

Sie können Assets in einem Ordner erneut verarbeiten, der bereits über ein vorhandenes Bildprofil verfügt, das Sie nachträglich geändert haben. Informationen hierzu finden Sie unter [Erneutes Verarbeiten von Assets in einem Ordner nach Bearbeitung des zugehörigen Verarbeitungsprofils](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets).

### Anwenden von Dynamic Media-Bildprofilen auf bestimmte Ordner {#applying-image-profiles-to-specific-folders}

Sie können ein Bildprofil über das Menü **[!UICONTROL Tools]** oder, wenn Sie sich im Ordner befinden, über **[!UICONTROL Eigenschaften]** auf einen Ordner anwenden.

Für Ordner mit zugewiesenem Profil wird der Name des Profils direkt unter dem Ordnernamen angezeigt.

Sie können Assets in einem Ordner erneut verarbeiten, der bereits über ein vorhandenes Videoprofil verfügt, das Sie nachträglich geändert haben. Informationen hierzu finden Sie unter [Erneutes Verarbeiten von Assets in einem Ordner nach Bearbeitung des zugehörigen Verarbeitungsprofils](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets).

#### Anwenden von Dynamic Media-Bildprofilen auf Ordner über die Benutzeroberfläche „Profile“ {#applying-image-profiles-to-folders-from-profiles-user-interface}

1. Wählen Sie das Adobe Experience Manager-Logo aus und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Bildprofile]**.
1. Wählen Sie ein Bildprofil aus, das Sie auf einen oder mehrere Ordner anwenden möchten.

   ![chlimage_1-255](assets/chlimage_1-255.png)

1. Wählen Sie **[!UICONTROL Verarbeitungsprofil auf Ordner anwenden]** und mindestens einen Ordner aus, den Sie verwenden möchten, um neu hochgeladene Assets zu empfangen. Wählen Sie dann **[!UICONTROL Anwenden]**. Für Ordner mit zugewiesenem Profil wird der Name des Profils direkt unter dem Ordnernamen angezeigt.

#### Anwenden von Dynamic Media-Bildprofilen auf Ordner über „Eigenschaften“ {#applying-image-profiles-to-folders-from-properties}

1. Klicken Sie auf das Experience Manager-Logo und navigieren Sie zu **[!UICONTROL Assets]**.
1. Navigieren Sie zu einem *Ordner* (nicht zu einem Asset), auf den Sie ein Bildprofil anwenden möchten.
1. Führen Sie je nach gewählter Ansicht eine der folgenden Aktionen aus:
   * Bewegen Sie in der Kartenansicht den Mauszeiger auf den Ordner und wählen Sie dann das Häkchen, um ihn auszuwählen.
   * Aktivieren Sie in der Spaltenansicht oder Listenansicht das Kontrollkästchen links neben dem Ordnernamen.
1. Wählen Sie in der Symbolleiste **[!UICONTROL Eigenschaften]** aus.
1. Wechseln Sie zur Registerkarte **[!UICONTROL Dynamic Media-Verarbeitung]**.
1. Wählen Sie unter **[!UICONTROL Bildprofil]** das anzuwendende Profil aus der Dropdown-Liste **[!UICONTROL Profilname]** aus.
1. Wählen Sie oben rechts auf der Seite **[!UICONTROL Speichern und schließen]** aus. Für Ordner mit zugewiesenem Profil wird der Name des Profils direkt unter dem Ordnernamen angezeigt.

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
>Adobe empfiehlt, alle erzeugten smarten Zuschnitte und smarten Farbfelder zu überprüfen, um sicherzustellen, dass sie für Ihre Marke und Ihre Werte angemessen und relevant sind.

Um den Fokus eines Bildes zu verfeinern, können Sie die Ausrichtung manuell anpassen oder die Größe des Fensters „Intelligenter Zuschnitt“ ändern.

Nachdem Sie einen intelligenten Zuschnitt bearbeitet und gespeichert haben, wird die Änderung überall dort angewendet, wo Sie den Zuschnitt für bestimmte Bilder verwenden.

>[!IMPORTANT]
>
>Wenn Sie das Fenster „Intelligenter Zuschnitt“ eines Assets manuell anpassen, werden Ihre Änderungen gespeichert. Diese Änderungen bleiben intakt, selbst wenn Sie das Asset später erneut verarbeiten. Wenn Sie jedoch die Breite, Höhe oder beides im Bereich **[!UICONTROL Responsive Bildbeschneidung]** des Bildprofils bearbeiten, muss dieses Asset erneut verarbeitet werden.
>Weitere Informationen finden Sie unter [Erneutes Verarbeiten von Dynamic Media-Assets in einem Ordner](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets).

Sie können einen smarten Zuschnitt erneut ausführen, um die zusätzlichen Zuschnitte erneut zu generieren, falls erforderlich.

Siehe auch [Bearbeiten von smarten Zuschnitten oder smarten Farb-/Bildmustern mehrerer Bilder](#editing-the-smart-crop-or-smart-swatch-of-multiple-images).

**So bearbeiten Sie smarte Zuschnitte oder smarte Farb-/Bildmuster eines einzelnen Bildes:**

1. Wählen Sie das Experience Manager-Logo aus und navigieren Sie zu **[!UICONTROL Assets]** und dann zu dem Ordner, auf den das Bildprofil „Smartes Zuschneiden“ oder „Smartes Farb-/Bildmuster“ angewendet wurde.
1. Öffnen Sie den Inhalt, indem Sie den Ordner auswählen.
1. Wählen Sie das Bild aus, dessen smarten Zuschnitt oder smarten Musterabschnitt Sie anpassen möchten.
1. Wählen Sie in der Symbolleiste **[!UICONTROL Intelligenter Zuschnitt]** aus.

   >[!TIP]
   >
   >Verwenden Sie den Hotkey `s`, um die intelligenten Zuschnitte oder Farbfelder zu bearbeiten.

1. Führen Sie einen der folgenden Schritte aus:

   * Ziehen Sie den Schieberegler in der rechten oberen Ecke der Seite nach links oder rechts, um die Bildanzeige zu erhöhen bzw. zu verringern.
   * Ziehen Sie auf dem Bild einen Eckpunkt, um die Größe des sichtbaren Bereichs des Zuschnitts oder Musterabschnitts anzupassen.
   * Ziehen Sie das Feld/den Musterabschnitt auf dem Bild an eine neue Position. Sie können nur Bildmuster bearbeiten. Musterabschnitte sind dagegen statisch.
   * Wählen Sie nahe der oberen rechten Bildecke **[!UICONTROL Zurücksetzen]** aus, um all Ihre Änderungen rückgängig zu machen und den ursprünglichen Zuschnitt oder das Farbfeld wiederherzustellen.
   * Mit den Pfeiltasten können Sie die Bildgröße zuschneiden oder das Bild neu positionieren (oder beides).

1. Wählen Sie in der oberen rechten Ecke der Seite **[!UICONTROL Speichern]** und anschließend **[!UICONTROL Schließen]** aus, um zum Asset-Ordner zurückzukehren.

## Bearbeiten von smarten Zuschnitten oder smarten Farb-/Bildmustern mehrerer Bilder {#editing-the-smart-crop-or-smart-swatch-of-multiple-images}

>[!IMPORTANT]
>
>Adobe empfiehlt, alle erzeugten smarten Zuschnitte und smarten Farbfelder zu überprüfen, um sicherzustellen, dass sie für Ihre Marke und Ihre Werte angemessen und relevant sind.

Nachdem Sie ein Bildprofil (das einen intelligenten Zuschnitt enthält) auf einen Ordner angewendet haben, wird der Zuschnitt auf alle Bilder in diesem Ordner angewendet. Bei Bedarf können Sie die Ausrichtung manuell anpassen oder die Größe des Fensters „Intelligenter Zuschnitt“ auf mehreren Bildern ändern, um die Fokuspunkte weiter anzupassen.

Nachdem Sie einen intelligenten Zuschnitt bearbeitet und gespeichert haben, wird die Änderung überall dort angewendet, wo Sie den Zuschnitt für bestimmte Bilder verwenden.

>[!IMPORTANT]
>
>Wenn Sie das Fenster „Intelligenter Zuschnitt“ mehrerer Assets manuell anpassen, werden Ihre Änderungen gespeichert. Diese Änderungen bleiben intakt, selbst wenn Sie die Assets später erneut verarbeiten. Wenn Sie jedoch die Breite, Höhe oder beides im Bereich **[!UICONTROL Responsive Bildbeschneidung]** des Bildprofils bearbeiten, müssen diese Assets erneut verarbeitet werden.
>Weitere Informationen finden Sie unter [Erneutes Verarbeiten von Dynamic Media-Assets in einem Ordner](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets).

Sie können einen smarten Zuschnitt erneut ausführen, um die zusätzlichen Zuschnitte erneut zu generieren, falls erforderlich.

**So bearbeiten Sie intelligente Zuschnitte oder intelligente Farb-/Bildmuster mehrerer Bilder:**

1. Wählen Sie das Experience Manager-Logo aus und navigieren Sie zu **[!UICONTROL Assets]** und dann zu einem Ordner, auf den das Bildprofil „Smartes Zuschneiden“ oder „Smartes Farb-/Bildmuster“ angewendet wurde.
1. Wählen Sie beim entsprechenden Ordner das Symbol **[!UICONTROL Mehr Aktionen]** (...) und anschließend **[!UICONTROL Smartes Zuschneiden]** aus.

1. Führen Sie auf der Seite **[!UICONTROL Smartes Zuschneiden bearbeiten]** eine der folgenden Aktionen durch:

   * Passen Sie die Anzeigegröße von Bildern auf der Seite an.

     Ziehen Sie den Schieberegler rechts neben der Dropdown-Liste mit Breakpoint-Namen nach links oder rechts, um den sichtbaren Bildbereich anzupassen.

     ![edit_smart_products-sliderbar](assets/edit_smart_crops-sliderbar.png)

   * Filtern Sie die Liste der sichtbaren Bilder anhand von Breakpoint-Namen. Im folgenden Beispiel werden die Bilder nach dem Breakpoint-Namen „Medium“ gefiltert. 

     Wählen Sie aus der Dropdown-Liste in der oberen rechten Ecke der Seite einen Breakpoint-Namen aus, um zu filtern, welche Bilder Ihnen angezeigt werden. (Siehe Abbildung oben.)

     ![edit_smart_products-dropdownlist](assets/edit_smart_crops-dropdownlist.png)

   * Ändern Sie die Rahmengröße für den smarten Zuschnitt. Führen Sie einen der folgenden Schritte aus:

      * Wenn das Bild nur über einen smarten Zuschnitt oder ein smartes Farb-/Bildmuster verfügt, ziehen Sie im Bild die Ecke des Zuschnittsfeldes, um die Größe des sichtbaren Bereichs des Zuschnitts anzupassen.
      * Wenn das Bild sowohl über einen smarten Zuschnitt als auch über ein smartes Farb-/Bildmuster verfügt, ziehen Sie im Bild die Ecke des Zuschnittsfeldes, um die Größe des sichtbaren Bereichs des Zuschnitts anzupassen. Oder wählen Sie das Farb-/Bildmuster unter dem Bild (Farbmuster sind statisch) aus und ziehen Sie die Ecke des Zuschnittsfelds. Passen Sie die Größe des sichtbaren Bereichs des Farb-/Bildmusters an.

     ![Größenänderung des smarten Zuschnitts eines Bildes](assets/edit_smart_crops-resize.png).

   * Verschieben Sie das Feld für den smarten Zuschnitt. Führen Sie einen der folgenden Schritte aus:

      * Wenn das Bild nur über entweder einen smarten Zuschnitt oder einen smarten Musterabschnitt verfügt, ziehen Sie das Zuschnittsfeld auf dem Bild an eine neue Position.
      * Wenn das Bild sowohl über einen smarten Zuschnitt als auch über einen smarten Musterabschnitt verfügt, ziehen Sie das Feld für den smarten Zuschnitt auf dem Bild an eine neue Position. Oder wählen Sie unter dem Bild das smarte Bildmuster (Farbmuster sind statisch) aus und ziehen Sie das smarte Zuschnittsfeld an eine neue Position.

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
1. Wählen Sie **[!UICONTROL Verarbeitungsprofil aus Ordnern entfernen]** und anschließend einen oder mehrere Ordner aus, aus denen das Profil entfernt werden soll. Wählen Sie dann **[!UICONTROL Entfernen]** aus.

   Sie können überprüfen, ob das Bildprofil nicht länger auf einen Ordner angewendet wird, da der Name in diesem Fall nicht mehr unter dem Ordner angezeigt wird.

### Entfernen von Dynamic Media-Bildprofilen aus Ordnern über „Eigenschaften“ {#removing-image-profiles-from-folders-via-properties}

1. Wählen Sie das Experience Manager-Logo aus und navigieren Sie zu **[!UICONTROL Assets]** und dann zu dem Ordner, aus dem Sie ein Bildprofil entfernen möchten.
1. Wählen Sie beim entsprechenden Ordner das Häkchen aus, um es zu aktivieren, und tippen Sie anschließend auf **[!UICONTROL Eigenschaften]**.
1. Wählen Sie die Registerkarte **[!UICONTROL Bildprofile]** aus.
1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Profilname]** die Option **[!UICONTROL Kein]** und dann **[!UICONTROL Speichern und schließen]** aus.

   Für Ordner mit zugewiesenem Profil wird der Name des Profils direkt unter dem Ordnernamen angezeigt.
