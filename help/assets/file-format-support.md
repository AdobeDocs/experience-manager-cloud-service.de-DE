---
title: Unterstützte Dateiformate und MIME-Typen
description: Von [!DNL Experience Manager Assets] as a [!DNL Cloud Service] unterstützte Dateiformate und MIME-Typen.
contentOwner: AG
feature: Asset Management, Renditions
role: User, Admin
exl-id: e848aa77-7829-4adc-8b88-0279791a4525
source-git-commit: 0129bf13301a208b777b61f65623222cdf2b4b18
workflow-type: tm+mt
source-wordcount: '1082'
ht-degree: 94%

---

# Von [!DNL Assets] unterstützte Dateiformate {#supported-file-formats}

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] unterstützt grundlegende Content-Management-Funktionen – wie Speicherung, Online-Verwaltung von Metadaten, Versionierung, Uploads und Downloads – für jede Binärdatei unabhängig vom Format. [!DNL Adobe Experience Manager Assets] unterstützt eine Vielzahl von Dateiformaten. Jede Produktfunktion bietet unterschiedliche Unterstützung für verschiedene Formate.

Darüber hinaus bietet [!DNL Experience Manager Assets] erweiterte Unterstützung zum Generieren von Vorschauen und Ausgabedarstellungen sowie zum Extrahieren von Metadaten und Text für die Volltextindizierung. Diese erweiterte Unterstützung wird mithilfe von [Asset-Microservices](asset-microservices-configure-and-use.md) bereitgestellt.

Zu den Highlights für die Asset-Konversion mithilfe von Asset-Mircoservices zählen:

* Gängige [Adobe-Dateiformate](#adobe-formats), die von Adobe-Programmen und -Services erstellt werden, einschließlich [!DNL Adobe Photoshop], [!DNL Adobe InDesign], [!DNL Adobe Illustrator], [!DNL Adobe XD], [!DNL Adobe Dimension] und [!DNL Adobe Acrobat] oder PDF.
* Gängige [Bildformate](#image-formats).
* [Camera Raw-Dateiformate](#camera-raw-formats) für eine Vielzahl von Kameras von Herstellern wie Canon, Nikon, Fujifilm und Olympus (unterstützt von Adobe Camera Raw).
* Häufig verwendete [Dokumentenformate](#document-formats) wie Microsoft Office® sowie Open Document-Formate.
* Ein breites Spektrum an [Video-](#video-formats) und [Audioformaten](#audio-formats).

Der folgenden Legende können Sie entnehmen, inwieweit ein Format unterstützt wird.

| Unterstützungsebene | Beschreibung |
| ------------- | --------------------------- |
| ✓ | Unterstützt |
| * | Siehe Anmerkungen unterhalb der Tabelle |
| - | Nicht zutreffend |

>[!IMPORTANT]
>
>[!DNL Adobe Experience Manager Assets] unterstützt nur die in diesem Artikel aufgeführten Dateiformate.
>&#x200B;>Einige Funktionen scheinen möglicherweise mit anderen Formaten zu funktionieren, diese Formate werden jedoch nicht offiziell unterstützt. Die Ergebnisse können inkonsistent sein, und die Funktionen funktionieren möglicherweise nicht wie erwartet.
>&#x200B;>Verwenden Sie nur die unterstützten Formate, um konsistente und zuverlässige Ergebnisse zu gewährleisten.

## Adobe-Formate {#adobe-formats}

| Dateiformat | Generierung von Miniaturen | Volltextextraktion | Metadatenextraktion | Breite/Höhe |
| ----------- | -------------------- | ------------------- | ------------------- | ------------ |
| AI | ✓ | – | ✓ | ✓ |
| COLLAGE | - | – | ✓ | – |
| DN | ✓ | – | ✓ | ✓ |
| SBSAR | ✓ | – | ✓ | ✓ |
| IDEAS | - | – | ✓ | - |
| INDD | ✓ | – | ✓ | ✓ * |
| INDT | - | – | ✓ | - |
| PDF | ✓ | ✓ | ✓ | ✓ |
| PROTO | - | – | ✓ | – |
| PSB | ✓ | – | ✓ | ✓ |
| PSD | ✓ | – | ✓ | ✓ |
| XD | ✓ | – | ✓ | ✓ |

\* Bei [!DNL Adobe InDesign]-Dateien (INDD) wird die Größe der Ausgabedarstellung durch die in die INDD-Datei eingebettete Vorschau bestimmt. Konfigurieren Sie die Voreinstellungen in [!DNL InDesign] (**[!UICONTROL Voreinstellungen > Dateiverarbeitung > Vorschaubilder immer mit Dokumenten speichern, Vorschaugröße]**), damit Sie größere Ausgabedarstellungen einbetten können.

## Bildformate {#image-formats}

| Dateiformat | Generierung von Miniaturen | Metadatenextraktion | Breite/Höhe | Zuschneiden |
| ----------- | -------------------- | ------------------- | ------------ | -------- |
| BMP | ✓ | - | ✓ | ✓ |
| EPS | ✓ | ✓ | – | - |
| GIF | ✓ | ✓ | ✓ | ✓ |
| JPEG | ✓ | ✓ | ✓ | ✓ |
| PNG | ✓ | ✓ | ✓ | ✓ |
| RGB | ✓ | ✓ | ✓ | ✓ |
| RGBA | ✓ | ✓ | ✓ | ✓ |
| SGI™ | ✓ | ✓ | ✓ | ✓ |
| SVG | ✓ | - | ✓ | ✓ |
| TIFF | ✓ | ✓ | ✓ | – |
| WebP | ✓ | ✓ | ✓ | ✓ |

## 3D-Formate {#support-3d-formats}

Die folgenden 3D-Formate werden unterstützt:

Weitere Informationen finden Sie unter [Arbeiten mit 3D-Assets in Dynamic Media](/help/assets/dynamic-media/assets-3d.md).

| Format | Speicherung | Versionierung | Workflow | Veröffentlichung | Zugriffssteuerung | Miniatur, Vorschau | 3D-Vorschau | Bereitstellung von Dynamic Media |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| DN | ✓ | ✓ | ✓ | – | ✓ | ✓ | – | - |
| gLB | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| gLTF | ✓ | ✓ | ✓ | – | ✓ | – | ✓ | – |
| OBJ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| STL | ✓ | ✓ | ✓ | ✓ | ✓ | – | ✓ | ✓ |
| FBX | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | – | – |
| 3DS | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | – | – |
| USDz | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | – | ✓ |
| SBSAR | ✓ | ✓ | ✓ | – | ✓ | ✓ | – | – |

## [!DNL Camera Raw]-Formate {#camera-raw-formats}

| Dateiformat | Generierung von Miniaturen | Metadatenextraktion | Breite/Höhe |
| ----------- | -------------------- | ------------------- | ------------ |
| 3FR | ✓ | ✓ | ✓ |
| ARW | ✓ | ✓ | ✓ |
| CR2 | ✓ | ✓ | ✓ |
| CR3 | ✓ | ✓ | ✓ |
| CRW | ✓ | ✓ | ✓ |
| DCR | ✓ | ✓ | ✓ |
| DNG | ✓ | ✓ | ✓ |
| ERF | ✓ | ✓ | ✓ |
| FFF | ✓ | ✓ | ✓ |
| GPR | ✓ | ✓ | ✓ |
| IIQ | ✓ | ✓ | ✓ |
| KDC | ✓ | ✓ | ✓ |
| MEF | ✓ | ✓ | ✓ |
| MFW | ✓ | ✓ | ✓ |
| MOS | ✓ | ✓ | ✓ |
| MRW | ✓ | ✓ | ✓ |
| NEF | ✓ | ✓ | ✓ |
| NRW | ✓ | ✓ | ✓ |
| ORF | ✓ | ✓ | ✓ |
| PEF | ✓ | ✓ | ✓ |
| RAF | ✓ | ✓ | ✓ |
| RAW | ✓ | ✓ | ✓ |
| RW2 | ✓ | ✓ | ✓ |
| RWL | ✓ | ✓ | ✓ |
| SRF | ✓ | ✓ | ✓ |
| SRW | ✓ | ✓ | ✓ |
| X3F | ✓ | ✓ | ✓ |

## Dokumentenformate {#document-formats}

Folgende Dokumentenformate werden für Asset-Management-Funktionen unterstützt.

| Dateiformat | Generierung von Miniaturen | Volltextextraktion | Breite/Höhe | Metadatenverwaltung | [Connected Assets](use-assets-across-connected-assets-instances.md) | Vollständige Dokumentvorschau |
| ----------- | -------------------- | ------------------- | ------------ | ------------------- | ---------------- |--------|
| DOC | - | – | – | ✓ | ✓ | ✓ |
| DOCX | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| EPUB | – | ✓ | – | – | – | - |
| HTML | – | ✓ | – | ✓ | ✓ | – |
| ODF | ✓ | ✓ | ✓ | – | – | - |
| ODM | ✓ | ✓ | ✓ | – | – | - |
| ODP | ✓ | ✓ | ✓ | – | – | - |
| ODS | ✓ | ✓ | ✓ | – | – | - |
| ODT | ✓ | ✓ | ✓ | ✓ | ✓ | – |
| OFG | ✓ | ✓ | ✓ | – | – | - |
| PDF | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| PPT | - | – | – | ✓ | ✓ | ✓ |
| PPTX | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| PS | - | – | ✓ | – | – | - |
| RTF | – | ✓ | – | ✓ | ✓ | ✓ |
| TXT | ✓ | ✓ | – | ✓ | ✓ | ✓ |
| XLS | - | – | – | ✓ | ✓ | ✓ |
| XLSX | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| XML | – | ✓ | – | – | – | – |

## Videoformate {#video-formats}

| Dateiformat | Generierung von Miniaturen | Metadatenextraktion | Breite/Höhe | Vorschau | Ausgabe |
| ----------- | -------------------- | ------------------- | ------------ | ------- | ------- |
| 3G2 | – | ✓ | – | – | – |
| 3GP | – | ✓ | – | – | – |
| AVI | ✓ | ✓ | ✓ | ✓ | – |
| DIVX | ✓ | – | ✓ | ✓ | – |
| F4V | ✓ | ✓ | ✓ | ✓ | – |
| FLV | ✓ | ✓ | ✓ | ✓ | – |
| M2T | ✓ | – | ✓ | ✓ | – |
| M2TS | ✓ | – | ✓ | ✓ | – |
| M2V | ✓ | – | ✓ | ✓ | – |
| M4V | ✓ | ✓ | ✓ | ✓ | - |
| MKV | ✓ | – | ✓ | ✓ | – |
| MOV | ✓ | ✓ | ✓ | ✓ | – |
| MP4 | ✓ | ✓ | ✓ | ✓ | ✓ |
| MPEG | ✓ | ✓ | ✓ | ✓ | – |
| MPG | ✓ | ✓ | ✓ | ✓ | - |
| MTS | ✓ | – | ✓ | ✓ | – |
| MXF | ✓ | – | ✓ | ✓ | – |
| OGV | ✓ | – | ✓ | ✓ | – |
| QT | ✓ | – | ✓ | ✓ | – |
| R3D | – | ✓ | ✓ | ✓ | – |
| SWF | ✓ | – | ✓ | ✓ | – |
| WebM | ✓ | – | ✓ | ✓ | ✓ |
| WMV | ✓ | ✓ | ✓ | ✓ | - |

## Audioformate {#audio-formats}

[!DNL Assets] as a [!DNL Cloud Service] unterstützt die XMP-Metadatenextraktion für die Audioformate AIF, ASF, M4A, MP3, WAV und WMA.

## Unterstützte Eingabeformate für Audio- und Videotranskription {#audio-video-transcription-formats}

* FLV (mit H.264- und AAC-Codecs) (.flv)
* MXF (.mxf)
* MPEG2-PS, MPEG2-TS, 3GP (.ts, .ps, .3gp, .3gpp, .mpg)
* Windows Media Video (WMV)/ASF (.wmv, .asf)
* AVI (unkomprimiert, 8 Bit/10 Bit) (.avi)
* MP4 (.mp4, .m4a, .m4v)
* Microsoft® Digital Video Recording (DVR-MS) (.dvr-ms)
* Matroska/WebM (.mkv)
* WAVE/WAV (.wav)
* QuickTime (.mov)

## Tipps und Einschränkungen {#limitations-and-tips}

* Derzeit beträgt die maximale Dateigröße für die Extraktion von Metadaten etwa 15 GB. Beim Hochladen großer Assets schlägt die Metadatenextraktion manchmal fehl.

## Dynamic Media – Unterstützte Eingabevideoformate für die Transkodierung {#video-dynamic-media-transcoding}

| Videodateierweiterung | Container | Empfohlene Video-Codecs | Nicht unterstützte Video-Codecs |
| --- | --- | --- | --- |
| AVI | A/V Interleave | XVID, DIVX, HDV, MiniDV (DV25), Techsmith Camtasia, Huffyuv, Fraps, Panasonic DVCPro | Indeo3 (IV30), MJPEG, Microsoft® Video 1 (MS-CRAM) |
| FLV, F4V | Adobe Flash | H264/AVC, Flix VP6, H263, Sorenson | SWF (Vektoranimationsdateien) |
| M4V | Apple iTunes | H264/AVC | − |
| MKV | Matroska | H264/AVC | − |
| MOV, QT | Apple QuickTime | H264/AVC, Apple ProRes422 &amp; HQ, Sony XDCAM, Sony DVCAM, HDV, Panasonic DVCPro, Apple DV (DV25), Apple PhotoJPEG, Sorenson, Avid DNxHD, Avid AVR | Apple Intermediate, Apple Animation |
| MP4 | MPEG-4 | H264/AVC (alle Profile) | − |
| MPG, VOB, M2V, MP2 | MPEG-2 | MPEG-2 | − |
| MXF ‡ | MXF | Sony XDCAM, MPEG-2, MPEG-4, Panasonic DVCPro | − |
| OGV, OGG | OGG | Theora, VP3, Dirac | − |
| WebM | WebM | Google VP8 | − |
| WMV | Windows Media 9 | WMV3 (v9), WMV2 (v8), WMV1 (v7), GoToMeeting (G2M2, G2M3, G2M4) | Microsoft® Screen (MSS2), Microsoft® Photo Story (WVP2) |

‡ Dieses Videoformat kann nicht mit interaktiven Videos in Dynamic Media oder mit Anmerkungen in Experience Manager Assets verwendet werden, da es hierfür noch nicht unterstützt wird.

## Dynamic Media – Unterstützte Dokumentformate {#document-support-dynamic-media}

| Format | Hochladen (Eingabeformat) | Bildvorgabe erstellen (Ausgabeformat) | Vorschau von dynamischer Ausgabedarstellung anzeigen | Dynamische Ausgabedarstellung bereitstellen | Dynamische Ausgabedarstellung herunterladen |
| ------ | --------------------- | ----------------------------------- | ------------------------- | ------------------------- | -------------------------- |
| AI | ✓ | – | – | – | - |
| INDD | ✓ | – | – | – | – |
| PDF (siehe Hinweis unten) | ✓ | ✓ | ✓ | ✓ | ✓ |

>[!NOTE]
>
>Bei sicheren PDF wird nur das Hochladen unterstützt.

## Dynamic Media – Unterstützte Rasterbildformate {#image-support-dynamic-media}

| Format | Hochladen (Eingabeformat) | Bildvorgabe erstellen (Ausgabeformat) | Vorschau von dynamischer Ausgabedarstellung anzeigen | Dynamische Ausgabedarstellung bereitstellen | Dynamische Ausgabedarstellung herunterladen | Festlegen von Typen, die dieses Format unterstützen |
|---|:---:|:---:|:---:|:---:|:---:| --- |
| AVIF | − | − | − | ✓ | − | − |
| BMP | ✓ | − | − | − | − | [Bild](/help/assets/dynamic-media/image-sets.md), [Gemischte Medien](/help/assets/dynamic-media/mixed-media-sets.md) und [Drehung](/help/assets/dynamic-media/spin-sets.md) |
| [EPS](/help/assets/dynamic-media/managing-image-presets.md#adobe-illustrator-ai-postscript-eps-and-pdf-file-formats) | ✓ | ✓ | ✓ | ✓ | ✓ | − |
| GIF | ✓ | ✓ | ✓ | ✓ | ✓ | − |
| HEIC | − | − | − | ✓ | − | − |
| JPEG | ✓ | ✓ | ✓ | ✓ | ✓ | [Bild](/help/assets/dynamic-media/image-sets.md), [Gemischte Medien](/help/assets/dynamic-media/mixed-media-sets.md) und [Drehung](/help/assets/dynamic-media/spin-sets.md) |
| PICT | ✓ | − | − | − | − | − |
| PNG | ✓ | ✓ | ✓ | ✓ | ✓ | [Bild](/help/assets/dynamic-media/image-sets.md), [Gemischte Medien](/help/assets/dynamic-media/mixed-media-sets.md) und [Drehung](/help/assets/dynamic-media/spin-sets.md) |
| PSD ‡ | ✓ | − | − | − | − | − |
| TIFF | ✓ | ✓ | ✓ | ✓ | ✓ | [Bild](/help/assets/dynamic-media/image-sets.md), [Gemischte Medien](/help/assets/dynamic-media/mixed-media-sets.md) und [Spin](/help/assets/dynamic-media/spin-sets.md) |
| WEBP | − | − | − | ✓ | − | − |

<!-- AVIF, HEIC, and WebP added to table above on March 4, 2024 based on CQDOC-21294 -->

‡ Das zusammengeführte Bild wird aus der PSD-Datei extrahiert. Dabei handelt es sich um ein von [!DNL Adobe Photoshop] generiertes Bild, das in der PSD enthalten ist. Je nach den Einstellungen kann dieses Bild das eigentliche Bild sein oder nicht.

## Dynamic Media – Nicht unterstützte Rasterbildformate {#unsupported-raster-image-formats-dm}

Die folgenden Untertypen von Rastergrafikdateiformaten, die *nicht* in [!DNL Dynamic Media] unterstützt werden:

* PNG-Dateien mit einer IDAT-Blockgröße größer als 100 MB.
* PSB-Dateien.
* PSD-Dateien mit einem anderen Farbraum als CMYK, RGB, Graustufen oder Bitmap werden nicht unterstützt. DuoTone-, Lab- und indizierte Farbräume werden nicht unterstützt.
* PSD-Dateien mit einer Bittiefe größer als 16.
* TIFF-Dateien mit Gleitkommadaten.
* TIFF-Dateien mit Lab-Farbraum.

## Dynamic Media – Unterstützte 3D-Dateiformate {#support-3d-formats-dynamic-media}

Siehe auch [Unterstützte 3D-Formate](/help/assets/file-format-support.md#support-3d-formats)

| 3D-Dateierweiterung | Dateiformat | MIME-Typ | Anmerkungen |
|---|---|---|---|
| GLB | Binäre GL-Übertragung | model/gltf-binary | Umfasst die Materialien und Texturen als ein Asset. |
| OBJ | WaveFront 3D-Objektdatei | application/x-tgif | |
| STL | Stereolithografie | application/vnd.ms-pki.stl | |
| USDZ | Universelles Scene Description-Zip-Archiv | model/vnd.usdz+zip | *Unterstützung der Erfassung und Erstellung von Miniaturansichten; 3D-Vorschau wird noch nicht unterstützt.* USDZ ist ein 3D-Format, das von Safari oder iOS nativ angezeigt werden kann. |

**Siehe auch**

* [Assets übersetzen](translate-assets.md)
* [Assets-HTTP-API](mac-api-assets.md)
* [Suchen von Assets](search-assets.md)
* [Connected Assets](use-assets-across-connected-assets-instances.md)
* [Asset-Berichte](asset-reports.md)
* [Metadatenschemata](metadata-schemas.md)
* [Herunterladen von Assets](download-assets-from-aem.md)
* [Verwalten von Metadaten](manage-metadata.md)
* [Suchfacetten](search-facets.md)
* [Verwalten von Sammlungen](manage-collections.md)
* [Massenimport von Metadaten](metadata-import-export.md)
* [Veröffentlichen von Assets in AEM und Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

>[!MORELIKETHIS]
>
>* [Asset-Verarbeitung mithilfe von Asset-Microservices](asset-microservices-overview.md).
>* [Unterstützte Dateiformate für das Tagging textbasierter Assets mit Smart-Tags](/help/assets/smart-tags.md#smart-tags-supported-file-formats)
