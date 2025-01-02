---
title: Verwalten von Bildvorgaben
description: Erweitern Sie Ihr Verständnis von Bildvorgaben und erfahren Sie mehr darüber, wie sie erstellt, bearbeitet und verwaltet werden.
contentOwner: Rick Brough
feature: Image Presets,Viewers,Renditions
role: User
exl-id: a53f40ab-0e27-45f8-9142-781c077a04cc
source-git-commit: baffc15d482ad3b57337c1ee5fe3e622253ae8cb
workflow-type: ht
source-wordcount: '3550'
ht-degree: 100%

---

# Verwalten von Bildvorgaben{#managing-image-presets}

Anhand von Bildvorgaben kann Adobe Experience Manager Assets Bilder mit unterschiedlichen Größen, Formaten oder Bildeigenschaften dynamisch bereitstellen. Jede Bildvorgabe stellt eine vordefinierte Sammlung von Größenangaben und Formatierungsbefehlen für die Anzeige von Bildern dar. Wenn Sie eine Bildvorgabe erstellen, wählen Sie eine Größe für die Bildbereitstellung aus. Sie wählen auch Formatierungsbefehle, damit das Erscheinungsbild des Bildes optimiert wird, wenn das Bild zur Anzeige bereitgestellt wird.

Admins können Vorgaben für den Asset-Export erstellen. Benutzer können eine Vorgabe auswählen, wenn sie Bilder exportieren, sodass die Bilder entsprechend den Spezifikationen des Administrators umformatiert werden.

Sie können auch responsive Bildvorgaben erstellen. Wenn Sie eine responsive Bildvorgabe auf Assets anwenden, werden diese je nach Gerät oder Bildschirmgröße bei der Anzeige geändert. Sie können Bildvorgaben konfigurieren, um im Farbraum zusätzlich zu RGB oder Graustufen auch CMYK zu verwenden.

In diesem Abschnitt wird beschrieben, wie Bildvorgaben erstellt, geändert und allgemein verwaltet werden. Sie können bei der Vorschau eines Bildes jederzeit eine Bildvorgabe darauf anwenden. Siehe [Anwenden von Bildvorgaben](/help/assets/dynamic-media/image-presets.md).

>[!NOTE]
>
>Die intelligente Bildbearbeitung arbeitet mit bestehenden Bildvorgaben und reduziert im letzten Moment abhängig vom Browser oder der Geschwindigkeit der Netzverbindung die Größe der Bilddatei intelligent noch weiter. Weitere Informationen finden Sie unter [Intelligente Bildbearbeitung](/help/assets/dynamic-media/imaging-faq.md).

## Informationen zu Bildvorgaben {#understanding-image-presets}

Wie ein Makro ist eine Bildvorgabe eine vordefinierte Sammlung aus Größenangaben und Formatierungsbefehlen, die unter einem Namen gespeichert wird. Stellen Sie sich folgendes Szenario vor, um ein besseres Verständnis von Bildvorgaben zu erlangen: Für Ihre Website muss jedes Produktbild in unterschiedlichen Größen, Formaten und Kompressionsraten auf Desktop- und Mobilgeräten angezeigt werden.

Sie können zwei Bildvorgaben erstellen: eine mit 500 x 500 Pixel für die Desktop-Version und die andere mit 150 x 150 Pixel für Mobilgeräte. Sie können zwei Bildvorgaben erstellen: `Enlarge` (Vergrößern) dient der Anzeige von Bildern mit einer Auflösung von 500 x 500 Pixel und `Thumbnail` (Miniatur) der Anzeige von Bildern mit einer Auflösung von 150 x 150 Pixel. Zum Übermitteln von Bildern mit der Größe `Enlarge` und `Thumbnail` sucht Adobe Experience Manager nach der Definition von `Enlarge Image Preset` und `Thumbnail Image Preset`. Experience Manager generiert anschließend dynamisch ein Bild anhand der Größen- und Formatierungsspezifikationen der jeweiligen Bildvorgabe.

Bilder, die bei der dynamischen Bereitstellung verkleinert werden, können an Schärfe und Detailgenauigkeit verlieren. Aus diesem Grund enthält jede Bildvorgabe Formatierungssteuerelemente zum Optimieren eines Bildes, wenn es in einer bestimmten Größe bereitgestellt wird. Dadurch wird sichergestellt, dass die Bilder scharf und deutlich auf der Website oder im Programm angezeigt werden.

Admins können Bildvorgaben erstellen. Sie können völlig neue Bildvorgaben erstellen oder eine vorhandene Vorgabe bearbeiten und unter einem neuen Namen speichern.

## Verwalten von Bildvorgaben {#managing-image-presets-1}

Sie können Bildvorgaben in Experience Manager verwalten, indem Sie auf das Adobe Experience Manager-Logo klicken, um auf die globale Navigationskonsole zuzugreifen. Klicken Sie dann auf das Werkzeugsymbol und gehen Sie zu **[!UICONTROL Assets]** > **[!UICONTROL Bildvorgaben]**.

![6_5_tools-assets-imagepresets](assets/6_5_tools-assets-imagepresets.png)

>[!NOTE]
>
>Alle erstellten Bildvorgaben sind auch als dynamische Ausgabedarstellungen verfügbar, wenn Sie eine Vorschau von Assets anzeigen oder Assets bereitstellen.
>
>Sie müssen Bildvorgaben *nicht* veröffentlichen, da die Veröffentlichung von Bildvorgaben automatisch erfolgt.
>
>Siehe [Veröffentlichen von Bildvorgaben](#publishing-image-presets).

>[!NOTE]
>
>Das System zeigt verschiedene Ausgabedarstellungen, wenn Sie **[!UICONTROL Ausgabedarstellungen]** in der Detailansicht eines Assets auswählen. Sie können die Anzahl der angezeigten Bildvorgaben erhöhen oder verringern. Siehe [Erhöhen der Anzahl der angezeigten Bildvorgaben](#increasing-or-decreasing-the-number-of-image-presets-that-display).

### Dateiformate Adobe Illustrator (AI), PostScript® (EPS) und PDF {#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats}

Wenn Sie die Aufnahme von AI-, EPS- und PDF-Dateien unterstützen möchten, um aus diesen Dateiformaten dynamische Ausgabedarstellungen zu generieren, lesen Sie die folgenden Informationen, bevor Sie Bildvorgaben erstellen.

Das Dateiformat von Adobe Illustrator ist eine Variante von PDF. Dies sind die wichtigsten Unterschiede im Hinblick auf Experience Manager Assets:

* Adobe Illustrator-Dokumente bestehen aus einer einzelnen Seite mit mehreren Ebenen. Jede Ebene wird als PNG-Teil-Asset unter dem Illustrator-Haupt-Asset extrahiert.
* PDF-Dokumente bestehen aus einer oder mehreren Seiten. Jede Seite wird als einseitiges PDF-Teil-Asset unter dem mehrseitigen PDF-Hauptdokument extrahiert.

Die `Create Sub Asset process`-Komponente erstellt die Teil-Assets im gesamten `DAM Update Asset`-Workflow. Um diese Prozesskomponente innerhalb des Workflows anzuzeigen, klicken Sie auf **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]** > **[!UICONTROL DAM-Update-Asset]** > **[!UICONTROL Bearbeiten]**.

<!-- See also [Viewing pages of a multi-page file](/help/assets/manage-linked-subassets.md#view-pages-of-a-multi-page-file). -->

Sie können die Teil-Assets oder die Seiten anzeigen, wenn Sie das Asset öffnen, auf das Menü „Inhalt“ klicken und **[!UICONTROL Teil-Assets]** oder **[!UICONTROL Seiten]** auswählen. Teil-Assets sind echte Assets. Die Workflow-Komponente `Create Sub Asset` extrahiert die PDF-Seiten. Die Seiten werden dann unter dem Haupt-Asset als `page1.pdf`, `page2.pdf` usw. gespeichert. Nach dem Speichern werden sie vom Workflow `DAM Update Asset` verarbeitet.

Um Dynamic Media zu verwenden und dynamische Ausgabedarstellungen für AI-, EPS- oder PDF-Dateien als Vorschau anzuzeigen oder zu generieren, sind folgende Verarbeitungsschritte erforderlich:

1. Im Workflow `DAM Update Asset` wird die erste Seite des ursprünglichen Assets mithilfe der konfigurierten Auflösung von der Prozesskomponente `Rasterize PDF/AI Image Preview Rendition` in einem Ausgabeformat `cqdam.preview.png` gerastert.

1. Die Prozesskomponente `Dynamic Media Process Image Assets` innerhalb des Workflows optimiert die `cqdam.preview.png`-Ausgabedarstellung in ein PTIFF.

>[!NOTE]
>
>Im Workflow „DAM Update Asset“ generiert der Schritt **[!UICONTROL EPS-Miniaturen]** Miniaturen für EPS-Dateien.

#### Metadateneigenschaften von PDF-/AI-/EPS-Assets {#pdf-ai-eps-asset-metadata-properties}

| **Metadateneigenschaft** | **Beschreibung** |
|---|---|
| `dam:Physicalwidthininches` | Dokumentbreite in Zoll. |
| `dam:Physicalheightininches` | Dokumenthöhe in Zoll. |

Sie können `Rasterize PDF/AI Image Preview Rendition`-Prozesskomponentenoptionen über den Workflow `DAM Update Asset` aufrufen.

Klicken Sie links oben auf „Adobe Experience Manager“ und gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]**.  Wählen Sie auf der Seite „Workflow-Modelle“ die Option **[!UICONTROL DAM-Update-Asset]** aus und dann in der Symbolleiste **[!UICONTROL Bearbeiten]**. Wählen Sie auf der Seite „Workflow DAM-Update-Asset“ die Prozesskomponente `Rasterize PDF/AI Image Preview Rendition` doppelt aus, um das Dialogfeld „Schritteigenschaften“ zu öffnen.

#### PDF-/AI-Bildvorschau-Ausgabedarstellung rastern – Optionen {#rasterize-pdf-ai-image-preview-rendition-options}

![Argumente zum Rastern von PDF- oder AI-Workflows](assets/rasterize_pdf_ai_image_preview.png)

Argumente zum Rastern von PDF- oder AI-Workflows

| Prozessargument | Standardeinstellung | Beschreibung |
|---|---|---|
| MIME-Typen | application/pdf<br>application/postscript<br>application/illustrator | Liste der Dokument-MIME-Typen, die als PDF- oder Illustrator-Dokumente gelten. |
| Max. Breite | 2048 | Maximale Breite der generierten Vorschaudarstellung in Pixel. |
| Max. Höhe | 2048 | Maximale Höhe der generierten Vorschaudarstellung in Pixel. |
| Auflösung | 72 | Auflösung zum Rastern der ersten Seite in ppi (Pixel pro Zoll). |

Bei Verwendung der standardmäßigen Prozessargumente wird die erste Seite eines PDF/AI-Dokuments mit 72 ppi gerastert und das generierte Vorschaubild hat eine Größe von 2048 x 2048 Pixel. Für eine typische Bereitstellung können Sie die Auflösung auf einen Mindestwert von 150 ppi oder mehr erhöhen. Für ein US Letter-Dokument ist z. B. für 300 ppi eine maximale Breite und Höhe von 2550 x 3300 Pixel erforderlich.

Die max. Breite und die max. Höhe beschränken die Auflösung, in der die Rasterung erfolgt. Wenn beispielsweise die Maximalwerte unverändert bleiben und die Auflösung auf 300 ppi eingestellt ist, wird ein US-Letter-Dokument auf 186 ppi gerastert. Das heißt, das Dokument hat 1581 x 2046 Pixel.

Für die Prozesskomponente `Rasterize PDF/AI Image Preview Rendition` ist ein Maximalwert definiert, um sicherzustellen, dass im Arbeitsspeicher keine zu großen Bilder erstellt werden. Zu große Bilder können zu einem Überlauf des für die JVM (Java™ Virtual Machine) bereitgestellten Speichers führen. Achten Sie darauf, der JVM ausreichend Arbeitsspeicher zur Verwaltung der konfigurierten Anzahl paralleler Workflows zur Verfügung zu stellen, da jeder Workflow potenziell ein Bild in der konfigurierten Maximalgröße erstellen kann.

### InDesign-Dateiformat (INDD) {#indesign-indd-file-format}

Wenn Sie die Aufnahme von INDD-Dateien unterstützen möchten, um aus diesem Dateiformat dynamische Ausgabedarstellungen zu generieren, lesen Sie die folgenden Informationen, bevor Sie Bildvorgaben erstellen.

Für InDesign-Dateien werden nur dann Teil-Assets extrahiert, wenn der Adobe InDesign Server in Experience Manager integriert ist. Referenzierte Assets werden basierend auf ihren Metadaten verknüpft. Für die Verknüpfung ist InDesign Server nicht erforderlich. Die referenzierten Assets müssen jedoch in Experience Manager vorhanden sein, bevor die InDesign-Dateien verarbeitet werden, damit die Verknüpfungen zwischen den InDesign-Dateien und den referenzierten Assets erstellt werden können.

<!-- See [Integrate Experience Manager Assets with InDesign Server](/help/assets/indesign.md). -->

Die Prozesskomponente zum Extrahieren von Medien im Workflow `DAM Update Asset` führt mehrere vorkonfigurierte ExtendScript-Skripte aus, um InDesign-Dateien zu verarbeiten.

![Die ExtendScript-Pfade in den Argumenten des Prozesses zum Extrahieren von Medien](/help/assets/dynamic-media/assets/6_5_mediaextractionprocess.png)

Die ExtendScript-Pfade in den Argumenten der Prozesskomponente zum Extrahieren von Medien im Workflow „DAM-Update-Asset“

Die folgenden Skripte werden von der Dynamic Media-Integration verwendet:


| ExtendScript-Name | Standard | Beschreibung |
|---|---|---|
| ThumbnailExport.jsx | Ja | Erstellt eine 300 ppi große `thumbnail.jpg`-Ausgabedarstellung, die von der Prozesskomponente `Dynamic Media Process Image Assets` optimiert und in eine PTIFF-Ausgabedarstellung umgewandelt wird. |
| JPEGPagesExport.jsx | Ja | Generiert für jede Seite ein 300 ppi großes JPEG-Teil-Asset. Das JPEG-Teil-Asset ist ein echtes Asset, das unter dem InDesign-Asset gespeichert wird. Der Workflow `DAM Update Asset` optimiert und wandelt sie in eine PTIFF-Datei um. |
| PDFPagesExport.jsx | Nein | Generiert für jede Seite ein PDF-Teil-Asset. Das PDF-Teil-Asset wird wie zuvor beschrieben verarbeitet. Da das PDF-Asset nur eine Seite enthält, werden keine Teil-Assets generiert. |

### Konfigurieren der Größe von Miniaturbildern {#configuring-image-thumbnail-size}

Sie können die Größe von Miniaturen über die Einstellungen im Workflow **[!UICONTROL DAM-Update-Asset]** konfigurieren. Im Workflow sind zwei Schritte enthalten, in denen Sie die Größe der Miniaturen von Bild-Assets konfigurieren können. Einer (**[!UICONTROL Bild-Assets-Prozess für Dynamic Media]**) wird für dynamische Bild-Assets verwendet. Der andere (**[!UICONTROL Prozessminiaturen]**) wird für die Generierung statischer Miniaturen verwendet oder wenn alle anderen Prozesse keine Miniaturen generieren. Unabhängig davon müssen *beide* dieselben Einstellungen haben.

Im Schritt **[!UICONTROL Dynamic Media Process Image Assets]** wird der Bild-Server verwendet, um Miniaturen zu generieren, unabhängig von der Konfiguration, die auf den Schritt **[!UICONTROL Miniaturansichten verarbeiten]** angewendet wird. Das Generieren von Miniaturen mit dem Schritt **[!UICONTROL Miniaturen verarbeiten]** ist das langsamste und speicherintensivste Verfahren zum Erstellen von Miniaturen.

Die Größe der Miniaturen wird im folgenden Format definiert: **[!UICONTROL width:height:center]**, z. B. `80:80:false`. Die Breite und die Höhe legen die Größe der Miniatur in Pixel fest. Für den center-Wert ist entweder false oder true festgelegt. Wenn true festgelegt ist, hat das Miniaturbild exakt die in der Konfiguration festgelegte Größe. Wenn das in der Größe angepasste Bild kleiner ist, wird es im Miniaturbildfenster zentriert.

>[!NOTE]
>
>* Die Größe der Miniaturen für EPS-Dateien wird im Schritt **[!UICONTROL EPS-Miniaturen]** auf der Registerkarte **[!UICONTROL Argumente]** unter „Miniaturen“ konfiguriert.
>
>* Die Größe der Miniaturen für Videos wird im Schritt **[!UICONTROL FFmpeg-Miniaturen]** auf der Registerkarte **[!UICONTROL Prozess]** unter **[!UICONTROL Argumente]** konfiguriert.
>

**So konfigurieren Sie die Größe von Miniaturbildern:**

1. Gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]** > **[!UICONTROL DAM-Update-Asset]** > **[!UICONTROL Bearbeiten]**.
1. Wählen Sie den Schritt **[!UICONTROL Dynamic Media Process Image-Assets]** und dann die Registerkarte **[!UICONTROL Miniaturen]** aus. Ändern Sie bei Bedarf die Größe der Miniaturen und klicken Sie auf **[!UICONTROL OK]**.

   ![6_5_dynamicmediaprocessimageassets-thumbnailstab](assets/6_5_dynamicmediaprocessimageassets-thumbnailstab.png)

1. Wählen Sie den Schritt **[!UICONTROL Miniaturen verarbeiten]** und dann die Registerkarte **[!UICONTROL Miniaturen]** aus. Ändern Sie bei Bedarf die Größe der Miniaturen und klicken Sie auf **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Die Werte im Argument „Miniaturen“ im Schritt **[!UICONTROL Miniaturen verarbeiten]** müssen mit dem Argument „Miniaturen“ im Schritt **[!UICONTROL Bild-Assets-Verarbeitung für Dynamic Media]** übereinstimmen.

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Änderungen am Workflow zu speichern.

### Erhöhen oder Verringern der Anzahl angezeigter Bildvorgaben {#increasing-or-decreasing-the-number-of-image-presets-that-display}

Erstellte Bildvorgaben sind auch als dynamische Ausgabedarstellungen verfügbar, wenn Sie eine Vorschau von Assets anzeigen. Experience Manager zeigt verschiedene dynamische Ausgabedarstellungen an, wenn ein Asset über **[!UICONTROL Detailansicht > Ausgabedarstellungen]** angezeigt wird. Sie können die Anzahl der angezeigten Ausgabedarstellungen erhöhen oder verringern.

**So erhöhen oder verringern Sie die Anzahl angezeigter Bildvorgaben:**

1. Navigieren Sie zu CRXDE Lite ([https://localhost:4502/crx/de](https://localhost:4502/crx/de)).
1. Navigieren Sie zum Knoten für die Bildvorgabenliste unter `/libs/dam/gui/coral/content/commons/sidepanels/imagepresetsdetail/imgagepresetslist`.

   ![increase_decreasethenumberofimagepresetsthatdisplay](assets/increase_decreasethenumberofimagepresetsthatdisplay.png)

1. Ändern Sie für die Eigenschaft **[!UICONTROL limit]** den **[!UICONTROL Wert]**, für den standardmäßig 15 festgelegt ist, in einen höheren Wert.
1. Navigieren Sie zur Datenquelle der Bildvorgabe unter `/libs/dam/gui/coral/content/commons/sidepanels/imagepresetsdetail/imgagepresetslist/datasource`

   ![chlimage_1-495](assets/chlimage_1-495.png)

1. Ändern Sie in der Eigenschaft „limit“ den Wert auf die gewünschte Zahl, z. B. `{empty requestPathInfo.selectors[1] ? "20" : requestPathInfo.selectors[1]}`.
1. Klicken Sie auf **[!UICONTROL Alle speichern]**.

### Erstellen von Bildvorgaben {#creating-image-presets}

Erstellen Sie Bildvorgaben, damit Sie bei der Vorschau oder Veröffentlichung Einstellungen konsistent auf alle Bilder anwenden können.

>[!NOTE]
>
>Bei Verwendung von Internet Explorer 9 wird die Erstellung einer Vorgabe nicht sofort nach dem Speichern in der Vorgabenliste angezeigt. Um dieses Problem zu umgehen, deaktivieren Sie den Cache für IE9.

Wenn Sie die Aufnahme von AI-, PDF- und EPS-Dateien unterstützen möchten, um aus diesen Dateiformaten dynamische Ausgabedarstellungen zu generieren, lesen Sie die folgenden Informationen, bevor Sie Bildvorgaben erstellen.

Siehe [Dateiformate Adobe Illustrator (AI), PostScript® (EPS) und PDF](#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats).

Wenn Sie die Aufnahme von INDD-Dateien unterstützen möchten, um aus diesem Dateiformat dynamische Ausgabedarstellungen zu generieren, lesen Sie die folgenden Informationen, bevor Sie Bildvorgaben erstellen.

Siehe [Dateiformat InDesign (INDD)](#indesign-indd-file-format).

**So erstellen Sie Bildvorgaben:**

1. Klicken Sie in Experience Manager auf das Adobe Experience Manager-Logo, um auf die globale Navigationskonsole zuzugreifen, und dann auf **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Bildvorgaben]**.
1. Wählen Sie **[!UICONTROL Erstellen]**.

   ![chlimage_1-496](assets/chlimage_1-496.png)

   >[!NOTE]
   >
   >Damit diese Bildvoreinstellung responsiv wird, löschen Sie die Werte in den Feldern **[!UICONTROL Breite]** und **[!UICONTROL Höhe]** und lassen Sie sie leer.

1. Geben Sie auf der Seite **[!UICONTROL Bildvorgabe bearbeiten]** auf den Registerkarten **[!UICONTROL Allgemein]** und **[!UICONTROL Erweitert]** die entsprechenden Werte (einschließlich eines Namens) ein. Die Optionen werden unter [Bildvoreinstellungsoptionen](#image-preset-options) beschrieben. Vorgaben werden im linken Bereich angezeigt und können nur zusammen mit anderen Assets verwendet werden.

   ![6_5_imagepreset-edit](assets/6_5_imagepreset-edit.png)

1. Wählen Sie **[!UICONTROL Speichern]** aus.

### Erstellen von responsiven Bildvorgaben {#creating-a-responsive-image-preset}

Um eine responsive Bildvorgabe zu erstellen, führen Sie die im Abschnitt [Erstellen von Bildvorgaben](#creating-image-presets) beschriebenen Schritte durch. Löschen Sie die Werte für Höhe und Breite im Fenster **[!UICONTROL Bildvorgabe bearbeiten]** und lassen Sie sie leer.

Dadurch wird diese Vorgabe in Experience Manager als responsiv erkannt. Sie können die anderen Werte nach Bedarf anpassen.

>[!NOTE]
>
>Um die Schaltflächen **[!UICONTROL URL]** und **[!UICONTROL RESS]** beim Anwenden einer Bildvorgabe auf ein Asset anzuzeigen, muss das Asset veröffentlicht werden.
>
>![chlimage_1-79](assets/chlimage_1-498.png)
>
>Die Bildvorgaben und Bild-Assets werden automatisch veröffentlicht.

### Optionen für Bildvorgaben {#image-preset-options}

Die in diesem Abschnitt beschriebenen Optionen sind beim Erstellen oder Bearbeiten von Bildvorgaben verfügbar. Adobe empfiehlt zudem für den Anfang als Best Practice die Auswahl der folgenden Optionen:

* **[!UICONTROL Format]** (Registerkarte **[!UICONTROL Allgemein]**) – Wählen Sie **[!UICONTROL JPEG]** oder ein anderes Format, das Ihren Anforderungen entspricht. Alle Webbrowser unterstützen das JPEG-Bildformat; es bietet eine gute Balance zwischen Dateigröße und Bildqualität. Bilder im JPEG-Format nutzen jedoch ein verlustbehaftetes Komprimierungsschema, das unerwünschte Bildartefakte hervorrufen kann, wenn die Komprimierungseinstellung zu niedrig ist. Aus diesem Grund empfiehlt Adobe, die Komprimierungsqualität auf 75 einzustellen. Diese Einstellung bietet einen angemessenen Ausgleich zwischen Bildqualität und kleiner Dateigröße.

* **[!UICONTROL Einfaches Scharfzeichnen aktivieren]**: Aktivieren Sie nicht die Option **[!UICONTROL Einfaches Scharfzeichnen aktivieren]** (dieser Scharfzeichnungsfilter bietet weniger Kontrolle als die Einstellungen für „Unschärfemaske“).

* **[!UICONTROL Scharfzeichnen: Resampling-Modus]**: Wählen Sie **[!UICONTROL Scharf2]** aus.

#### Optionen auf der Registerkarte „Standard“ {#basic-tab-options}

| Feld | Beschreibung |
| --- | --- |
| **Name** | Geben Sie einen aussagekräftigen Namen ohne Leerzeichen ein. Um den Benutzern die Identifizierung dieser Bildvorgabe zu erleichtern, nehmen Sie die Angabe der Bildgröße in den Namen auf. |
| **Breite und Höhe** | Geben Sie die Größe in Pixel ein, in der das Bild übermittelt wird. Breite und Höhe müssen größer als 0 Pixel sein. Wenn einer der beiden Werte 0 ist, wird keine Vorgabe erstellt. Wenn beide Werte leer sind, wird eine responsive Bildvorgabe erstellt. |
| **Format** | Wählen Sie im Menü ein Format aus.<br>Bei Auswahl von **JPEG** stehen die folgenden anderen Optionen zur Verfügung:<br>• **Qualität**: Die JPEG-Qualitätsskala ist 1–100. Die Skala ist sichtbar, wenn Sie den Schieberegler bewegen.<br>• **PG-Chrominanz-Downsampling aktivieren**: Da das menschliche Auge weniger empfindlich gegenüber hochfrequenten Farbinformationen als gegenüber hochfrequenter Luminanz ist, teilen JPEG-Bilder die Bildinformationen in Luminanz- und Farbkomponenten auf. Wenn ein JPEG-Bild komprimiert wird, bleibt die Luminanzkomponente in der vollen Auflösung erhalten, während bei den Farbkomponenten ein Downsampling anhand einer Durchschnittsbildung von Pixelgruppen erfolgt. Durch Downsampling wird das Datenvolumen auf die Hälfte oder ein Drittel reduziert, wobei die wahrgenommene Qualität nur minimal beeinträchtigt wird. Das Downsampling ist nicht auf Graustufenbilder anwendbar. Mit dieser Methode wird der Komprimierungsgrad für Bilder mit hohem Kontrast (z. B. Bilder mit überlagertem Text) reduziert.<br><br>Wenn Sie **GIF** oder **GIF mit Alpha** auswählen, erhalten Sie die folgenden zusätzlichen Optionen für die **GIF-Farbquantifizierungsoptionen**:<br>• **Typ**: Wählen Sie **Adaptiv** (Standard), **Web** oder **Macintosh** aus. Wenn Sie **GIF mit Alpha** auswählen, ist die Option „Macintosh“ nicht verfügbar.<br>• **Dithering**: Wählen Sie **Diffus** oder **Aus**.<br>• **Anzahl Farben**: Geben Sie eine Zahl von 2 bis 256 ein.<br>• **Farbliste**: Geben Sie eine kommagetrennte Liste ein. Geben Sie beispielsweise für Weiß, Grau und Schwarz „`000000,888888,ffffff`“ ein.<br><br>Wenn Sie **PDF**, **TIFF** oder **TIFF mit Alpha** auswählen, erhalten Sie die folgende zusätzliche Option:<br>• **Komprimierung**: Wählen Sie einen Komprimierungsalgorithmus. Die Algorithmusoptionen für PDF lauten **Kein**, **ZIP** und **JPEG**. Für TIFF lauten sie **Kein**, **LZW**, **JPEG** und **ZIP**. Für TIFF mit Alpha lauten sie **Kein**, **LZW** und **ZIP**.<br><br>Die Auswahl **PNG**, **PNG mit Alpha** oder **EPS** ergibt keine zusätzlichen Optionen. |
| **Scharfzeichnen** | Wählen Sie die Option **Einfaches Scharfzeichnen aktivieren**, um einen einfachen Scharfzeichnungsfilter auf das Bild anzuwenden, nachdem die Skalierung abgeschlossen wurde. Mit der Scharfzeichnung können Sie unter Umständen Weichzeichnung kaschieren, die durch die Anzeige eines Bildes in einer anderen Größe entsteht. |

#### Optionen auf der Registerkarte „Erweitert“ {#advanced-tab-options}

<table>
 <tbody>
  <tr>
   <td><strong>Feld</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td><strong>Farbraum</strong></td>
   <td>Wählen Sie <strong>RGB, CMYK</strong> oder <strong>Graustufen</strong> als Farbraum aus.</td>
  </tr>
  <tr>
   <td><strong>Farbprofil</strong></td>
   <td>Wählen Sie das Profil des Ausgabefarbraums aus, in den das Asset konvertiert werden soll, sofern dieser sich von dem des Arbeitsprofils unterscheidet.</td>
  </tr>
  <tr>
   <td><strong>Rendering-Intent</strong></td>
   <td>Sie können den standardmäßigen Rendering-Intent überschreiben. Der Rendering-Intent legt fest, was mit Farben passiert, die im Farbprofil des Ziels nicht wiedergegeben werden können (außerhalb der Farbskala). Der Rendering-Intent wird ignoriert, wenn er nicht mit dem ICC-Profil kompatibel ist.
    <ul>
     <li>Wählen Sie <strong>Wahrnehmungsoptimiert</strong> aus, damit die gesamte Farbskala von einem Farbraum in einen anderen Farbraum komprimiert wird, wenn eine oder mehrere Farben im Originalbild außerhalb der Farbskala des Zielfarbraums liegen.</li>
     <li>Wählen Sie <strong>Relativ farbmetrisch</strong> aus, wenn eine Farbe im aktuellen Farbraum im Zielfarbraum außerhalb der Farbskala liegt. Und Sie solltten sie dem nächsten Zielfarbraum zuordnen, ohne andere Farben zu verändern. </li>
     <li>Wählen Sie <strong>Sättigung</strong> aus, um die Sättigung des Originalbilds beim Konvertieren in den Zielfarbraum zu übernehmen. </li>
     <li>Wählen Sie <strong>Absolut farbmetrisch</strong> aus, um Farben exakt und ohne Weißpunkt- oder Schwarzpunktanpassung abzubilden, wodurch die Helligkeit verändert würde.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Tiefenkompensierung</strong></td>
   <td>Wählen Sie diese Option aus, wenn das Ausgabeprofil diese Funktion unterstützt. Die Tiefenkompensierung wird ignoriert, wenn sie nicht mit dem angegebenen ICC-Profil kompatibel ist.</td>
  </tr>
  <tr>
   <td><strong>Dithering</strong></td>
   <td>Wählen Sie diese Option aus, um Farbstreifen-Artefakte möglichst zu vermeiden oder zu reduzieren. </td>
  </tr>
  <tr>
   <td><strong>Scharfzeichnungstyp</strong></td>
   <td><p>Wählen Sie <strong>Kein</strong>, <strong>Scharfzeichnen</strong> oder <strong>Unschärfemaske</strong> aus. </p>
    <ul>
     <li>Wählen Sie <strong>Kein</strong> aus, wenn Sie das Scharfzeichnen deaktivieren möchten.</li>
     <li>Aktivieren Sie <strong>Scharfzeichnen</strong>, um einen einfachen Scharfzeichnungsfilter auf das Bild anzuwenden, nachdem die Skalierung abgeschlossen ist. Mit der Scharfzeichnung können Sie unter Umständen Weichzeichnung kaschieren, die durch die Anzeige eines Bildes in einer anderen Größe entsteht. </li>
     <li>Wählen Sie <strong>Unscharf maskieren</strong> aus, um einen Scharfzeichnungsfiltereffekt für das endgültige Bild nach dem Downsampling zu optimieren. Sie können die Intensität des Effekts, den Radius des Effekts (gemessen in Pixel) und einen Schwellenwert festlegen, ab dem der Kontrast ignoriert werden soll. Dieser Effekt verwendet dieselben Optionen wie der Photoshop-Filter „Unscharf maskieren“.</li>
    </ul> <p>In <strong>Unschärfemaske</strong> sind die folgenden Optionen verfügbar:</p>
    <ul>
     <li><strong>Betrag</strong>: Steuert den auf die Kantenpixel angewendeten Kontrastwert. Der Standardwert für die reelle Zahl ist 1,0. Bei hochauflösenden Bildern können Sie ihn auf bis zu 5,0 erhöhen. Der Wert dient hierbei als ein Maß für die Filterintensität.</li>
     <li><strong>Radius</strong>: Bestimmt die Anzahl der Pixel um die Kantenpixel, die sich auf die Scharfzeichnung auswirken. Geben Sie bei hochauflösenden Bildern eine reale Zahl zwischen 1 und 2 ein. Mit einem niedrigeren Wert werden nur die Kantenpixel scharfgezeichnet, während mit einem höheren Wert mehr Pixel scharfgezeichnet werden. Der richtige Wert hängt von der Bildgröße ab.</li>
     <li><strong>Schwellenwert</strong>: Bestimmt den Kontrastbereich, der bei Anwendung des Filters „Unscharf maskieren“ ignoriert werden soll. Mit anderen Worten: Diese Option definiert, wie viele scharf gezeichnete Pixel sich vom Umgebungsbereich unterscheiden müssen, um als Kantenpixel eingestuft und scharf gezeichnet zu werden. Um Rauschen zu vermeiden, experimentieren Sie mit Ganzzahlwerten von 2 bis 20. </li>
     <li><strong>Anwenden auf</strong>: Bestimmt, ob die Unscharfzeichnung für jede Farbe oder Helligkeit gilt.</li>
    </ul>
    <div>
      Scharfzeichnen wird im Video
     <a href="https://experienceleague.adobe.com/de/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-image-sharpening-feature-video-use#dynamic-media">Verwenden des Scharfzeichnens von Bildern mit Experience Manager Dynamic Media</a>, im Online-Hilfethema <a href="https://experienceleague.adobe.com/de/docs/dynamic-media-classic/using/master-files/sharpening-image#master-files">Scharfzeichnen eines Bildes</a> und im herunterladbaren PDF <a href="https://experienceleague.adobe.com/docs/dynamic-media-classic/assets/s7_sharpening_images.pdf">Best Practices zum Scharfzeichnen von Bildern in Dynamic Media Classic</a>.
    </div> </td>
  </tr>
  <tr>
   <td><strong>Resampling-Modus</strong></td>
   <td>Wählen Sie eine Option für den <strong>Resampling-Modus</strong>. Diese Optionen sorgen dafür, dass das Bild beim Neuberechnen scharf bleibt:
    <ul>
     <li><strong>Bilinear</strong>: Die schnellste Resampling-Methode. Einige Aliasing-Artefakte sind sichtbar.</li>
     <li><strong>Bikubisch</strong>: Erhöht die CPU-Auslastung, bietet jedoch schärfere Bilder mit weniger deutlichen Aliasing-Artefakten.</li>
     <li><strong>Scharf2</strong>: Kann im Vergleich zu „Bikubisch“ etwas schärfere Ergebnisse erzeugen, ist jedoch CPU-intensiver.</li>
     <li><strong>Bi-Sharp</strong>: Wählt den Standard-Resampler in Photoshop zum Reduzieren der Bildgröße aus, was in Adobe Photoshop als <strong>bikubisch schärfer</strong> bezeichnet wird.</li>
     <li><strong>Jede Farbe</strong> und <strong>Helligkeit</strong> – jede Methode kann auf Farbe oder Helligkeit basieren. Standardmäßig ist <strong>Jede Farbe</strong> ausgewählt.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Druckauflösung</strong></td>
   <td>Wählen Sie eine Auflösung für den Druck dieses Bildes. Der Standardwert beträgt 72 Pixel.</td>
  </tr>
  <tr>
   <td><strong>Bildmodifikator</strong></td>
   <td><p>Neben den allgemeinen Bildeinstellungen in der Benutzeroberfläche unterstützt Dynamic Media zahlreiche erweiterte Bearbeitungsoptionen für Bilder, die Sie im Feld <strong>Bild-Modifikatoren</strong> festlegen können. Diese Parameter werden in der <a href="https://experienceleague.adobe.com/de/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/syntax-and-features/image-serving-http/c-command-overview">Befehlsreferenz für das Image Server-Protokoll</a> definiert.</p> <p>Wichtig: Die folgenden in der API aufgelisteten Funktionen werden nicht unterstützt:</p>
    <ul>
     <li>Grundlegende Befehle zur Vorlagenerstellung und Textdarstellung: <code>text= textAngle= textAttr= textFlowPath= textFlowXPath= textPath=</code> und <code>textPs=</code></li>
     <li>Lokalisierungsbefehle: <code>locale=</code> und <code>req=xlate</code></li>
     <li><code>req=set</code> ist nicht für die allgemeine Anwendung verfügbar.</li>
     <li><code>req=mbrset</code></li>
     <li><code>req=saveToFile</code></li>
     <li><code>req=targets</code></li>
     <li><code>template=</code></li>
     <li>Dynamic Media-Neben-Services: SVG, Rendering von Bildern und Web-to-Print</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

### Definieren von Bildvorgabenoptionen mit Bildmodifikatoren {#defining-image-preset-options-with-image-modifiers}

Zusätzlich zu den auf den Registerkarten „Allgemein“ und „Erweitert“ verfügbaren Optionen können Sie Bildmodifikatoren definieren, damit Sie beim Definieren von Bildvorgaben über mehr Optionen verfügen. Das Rendern von Bildern basiert auf der Dynamic Media Image Rendering-API und wird ausführlich in der [HTTP-Protokollreferenz](https://experienceleague.adobe.com/de/docs/dynamic-media-developer-resources/image-serving-api/image-rendering-api/http-protocol-reference/c-ir-introduction#image-rendering-api) beschrieben.

Im Folgenden finden Sie einige einfache Beispiele für die Nutzung von Bild-Modifikatoren.

>[!NOTE]
>
>Einige Bildmodifikatoren [können nicht in Experience Manager verwendet werden](#advanced-tab-options).

* [op_invert](https://experienceleague.adobe.com/de/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-op-invert): Invertiert jede Farbkomponente für einen negativen Bildeffekt.

  ```xml {.line-numbers}
  &op_invert=1
  ```

  ![6_5_imagepreset-edit-invert](assets/6_5_imagepreset-edit-invert.png)

* [op_blur](https://experienceleague.adobe.com/de/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-op-blur): Wendet einen Weichzeichenfilter auf das Bild an.

  ```xml {.line-numbers}
  &op_blur=7
  ```

  ![6_5_imagepreset-edit-blur](assets/6_5_imagepreset-edit-blur.png)

* Kombinierte Befehle - op_blur und op-invert

  ```xml {.line-numbers}
  &op_invert=1&op_blur=7
  ```

  ![chlimage_1-80](assets/chlimage_1-501.png)

* [Op_brightness](https://experienceleague.adobe.com/de/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-op-brightness): Verringert oder erhöht die Helligkeit.

  ```xml {.line-numbers}
  &op_brightness=58
  ```

  ![6_5_imagepreset-edit-brightness](assets/6_5_imagepreset-edit-brightness.png)

* [opac](https://experienceleague.adobe.com/de/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-opac): Passt die Bilddeckkraft an. Ermöglicht das Reduzieren der Vordergrunddeckkraft.

  ```xml {.line-numbers}
  opac=29
  ```

  ![6_5_imagepreset-edit-opacity](assets/6_5_imagepreset-edit-opacity.png)

### Bearbeiten von Bildvorgaben {#modifying-image-presets}

1. Klicken Sie in Experience Manager auf das Adobe Experience Manager-Logo, um auf die globale Navigationskonsole zuzugreifen, und dann auf **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Bildvorgaben]**.

   ![6_5_imagepreset-editpreset](assets/6_5_imagepreset-editpreset.png)

1. Wählen Sie eine Vorgabe aus und klicken Sie dann auf **[!UICONTROL Bearbeiten]**. Das Fenster **[!UICONTROL Bildvorgabe bearbeiten]** wird geöffnet.
1. Nehmen Sie Änderungen vor und klicken Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern, oder auf **[!UICONTROL Abbrechen]**, um sie zu verwerfen.

### Veröffentlichen von Bildvorgaben {#publishing-image-presets}

Bildvorgaben werden automatisch veröffentlicht.

### Löschen von Bildvorgaben {#deleting-image-presets}

1. Klicken Sie in Experience Manager auf das Adobe Experience Manager-Logo, um auf die globale Navigationskonsole zuzugreifen, und klicken Sie dann auf das Werkzeugsymbol.
1. Gehen Sie zu **[!UICONTROL Assets]** > **[!UICONTROL Bildvorgaben]**.
1. Wählen Sie eine Vorgabe aus und klicken Sie dann auf **[!UICONTROL Löschen]**. Dynamic Media bestätigt Ihre Löschabsicht. Klicken Sie auf **[!UICONTROL Löschen]**, um sie zu entfernen oder auf **[!UICONTROL Abbrechen]**, um zu den Bildvorgaben zurückzukehren.
