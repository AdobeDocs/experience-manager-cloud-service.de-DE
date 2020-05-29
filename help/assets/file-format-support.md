---
title: Von Adobe Experience Manager Assets as a Cloud Service unterstützte Dateiformate und MIME-Typen
description: Von Adobe Experience Manager Assets as a Cloud Service unterstützte Dateiformate und MIME-Typen
contentOwner: AG
translation-type: ht
source-git-commit: 2830c1cb2a9a0c06e6f8a4a765420706f5ceb093
workflow-type: ht
source-wordcount: '0'
ht-degree: 100%

---


# Von AEM Assets unterstützte Dateiformate {#supported-file-formats}

Adobe Experience Manager as a Cloud Service unterstützt grundlegende Content-Management-Funktionen – wie Speicherung, Online-Verwaltung von Metadaten, Versionierung, Uploads und Downloads – für jede Binärdatei unabhängig vom Format. Adobe Experience Manager Assets unterstützt eine Vielzahl von Dateiformaten. Jede Produktfunktion bietet unterschiedliche Unterstützung für verschiedene Formate.

Darüber hinaus bietet Experience Manager Assets erweiterte Unterstützung zum Generieren von Vorschauen und Darstellungen sowie zum Extrahieren von Metadaten und Text für die Volltextindizierung. Diese erweiterte Unterstützung wird mithilfe von [Asset-Microservices](asset-microservices-configure-and-use.md) bereitgestellt.

Zu den Highlights für die Asset-Konversion mithilfe von Asset-Mircoservices zählen:

* Gängige [Adobe-Dateiformate](#adobe-formats), die von Adobe-Programmen und -Services erstellt werden, einschließlich Adobe Photoshop, Adobe InDesign, Adobe Illustrator, Adobe XD, Adobe Dimension und Adobe Acrobat oder PDF.
* Gängige [Bildformate](#image-formats).
* [Camera Raw-Dateiformate](#camera-raw-formats) für eine Vielzahl von Kameras von Herstellern wie Canon, Nikon, Fujifilm und Olympus (unterstützt von Adobe Camera Raw).
* Häufig verwendete [Dokumentenformate](#document-formats) wie Microsoft Office sowie Open Document-Formate.
* Ein breites Spektrum an [Video-](#video-formats) und [Audioformaten](#audio-formats).

In der folgenden Legende wird der Grad der Unterstützung beschrieben.

| Unterstützungsebene | Beschreibung |
| ------------- | --------------------------- |
| ✓ | Unterstützt |
| * | Siehe Anmerkungen unterhalb der Tabelle |
| - | Nicht zutreffend |

## Adobe-Formate {#adobe-formats}

| Dateiformat | Generierung von Miniaturansichten | Volltextextraktion | Metadatenextraktion | Breite/Höhe |
| ----------- | -------------------- | ------------------- | ------------------- | ------------ |
| AI | ✓ | - | ✓ | ✓ |
| COLLAGE | - | - | ✓ | - |
| DN | ✓ |  | ✓ | ✓ |
| IDEAS | - | - | ✓ | - |
| INDD | ✓ | - | ✓ | ✓ * |
| INDT | - | - | ✓ | - |
| PDF | ✓ | ✓ | ✓ | ✓ |
| PROTO | - | - | ✓ | - |
| PSB | ✓ | - | ✓ | ✓ |
| PSD | ✓ | - | ✓ | ✓ |
| XD | ✓ | - | ✓ | ✓ |

\* Bei [!DNL Adobe InDesign]-Dateien (INDD) wird die Größe des Ausgabeformats durch die in die INDD-Datei eingebettete Vorschau bestimmt. Konfigurieren Sie die Voreinstellungen unter [!DNL InDesign] (**[!UICONTROL Voreinstellungen > Dateiverarbeitung > Vorschaubilder immer mit Dokumenten speichern, Vorschaugröße]**), um ein größeres Ausgabeformat einzubetten.

## Bildformate {#image-formats}

| Dateiformat | Generierung von Miniaturansichten | Metadatenextraktion | Breite/Höhe | Zuschneiden |
| ----------- | -------------------- | ------------------- | ------------ | -------- |
| BMP | ✓ | - | ✓ | ✓ |
| EPS | - | ✓ | - | - |
| GIF | ✓ | ✓ | ✓ | ✓ |
| JPEG | ✓ | ✓ | ✓ | ✓ |
| PNG | ✓ | ✓ | ✓ | ✓ |
| SVG | - | ✓ | - | - |
| TIFF | ✓ | ✓ | ✓ | - |

## Bildformate in [!DNL Dynamic Media] {#image-support-dynamic-media}

| Format | Hochladen (Eingabeformat) | Bildvorgabe erstellen (Ausgabeformat) | Vorschau von dynamischem Ausgabeformat anzeigen | Dynamisches Ausgabeformat bereitstellen | Dynamisches Ausgabeformat herunterladen |
| ------- | --------------------- | ----------------------------------- | ------------------------- | ------------------------- | -------------------------- |
| PNG | ✓ | ✓ | ✓ | ✓ | ✓ |
| GIF | ✓ | ✓ | ✓ | ✓ | ✓ |
| TIFF | ✓ | ✓ | ✓ | ✓ | ✓ |
| JPEG | ✓ | ✓ | ✓ | ✓ | ✓ |
| BMP | ✓ | - | - | - | - |
| PSD   ‡ | ✓ | - | - | - | - |
| EPS | ✓ | ✓ | ✓ | ✓ | ✓ |
| PICT | ✓ | - | - | - | - |

‡ Das zusammengeführte Bild wird aus der PSD-Datei extrahiert. Dabei handelt es sich um ein von [!DNL Adobe Photoshop] generiertes Bild, das in der PSD enthalten ist. Je nach den Einstellungen kann dieses Bild das eigentliche Bild sein oder nicht.

Die folgenden Untertypen von Rasterbilddateiformaten, die in [!DNL Dynamic Media] nicht unterstützt werden:

* PNG-Dateien mit einer IDAT-Blockgröße größer als 100 MB.
* PSB-Dateien.
* PSD-Dateien mit einem anderen Farbraum als CMYK, RGB, Graustufen oder Bitmap werden nicht unterstützt. DuoTone-, Lab- und indizierte Farbräume werden nicht unterstützt.
* PSD-Dateien mit einer Bittiefe größer als 16.
* TIFF-Dateien mit Gleitkommadaten.
* TIFF-Dateien mit Lab-Farbraum.

## [!DNL Camera RAW]-Formate {#camera-raw-formats}

| Dateiformat | Generierung von Miniaturansichten | Metadatenextraktion | Breite/Höhe |
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

| Dateiformat | Generierung von Miniaturansichten | Volltextextraktion | Breite/Höhe | Metadatenverwaltung | [Connected Assets](use-assets-across-connected-assets-instances.md) |
| ----------- | -------------------- | ------------------- | ------------ | ------------------- | ---------------- |
| PDF | ✓ | ✓ | ✓ | ✓ | ✓ |
| DOCX | ✓ | ✓ | ✓ | ✓ | ✓ |
| DOC | - | - | - | ✓ | ✓ |
| PPTX | ✓ | ✓ | ✓ | ✓ | ✓ |
| PPT | - | - | - | ✓ | ✓ |
| XLSX | ✓ | ✓ | ✓ | ✓ | ✓ |
| XLS | - | - | - | ✓ | ✓ |
| ODF | ✓ | ✓ | ✓ | - | - |
| OFG | ✓ | ✓ | ✓ | - | - |
| ODM | ✓ | ✓ | ✓ | - | - |
| ODP | ✓ | ✓ | ✓ | - | - |
| ODS | ✓ | ✓ | ✓ | - | - |
| ODT | ✓ | ✓ | ✓ | ✓ | ✓ |
| EPUB | - | ✓ | - | - | - |
| HTML | - | ✓ | - | ✓ | ✓ |
| PS | - | - | ✓ | - | - |
| RTF | - | ✓ | - | ✓ | ✓ |
| TXT | - | ✓ | - | ✓ | ✓ |
| XML | - | ✓ | - | - | - |

## Dokumentenformate in [!DNL Dynamic Media] {#document-support-dynamic-media}

| Format | Hochladen (Eingabeformat) | Bildvorgabe erstellen (Ausgabeformat) | Vorschau von dynamischem Ausgabeformat anzeigen | Dynamisches Ausgabeformat bereitstellen | Dynamisches Ausgabeformat herunterladen |
| ------ | --------------------- | ----------------------------------- | ------------------------- | ------------------------- | -------------------------- |
| AI | ✓ | - | - | - | - |
| PDF | ✓ | ✓ | ✓ | ✓ | ✓ |
| INDD | ✓ | - | - | - | - |

## Videoformate {#video-formats}

| Dateiformat | Generierung von Miniaturansichten | Metadatenextraktion | Breite/Höhe |
| ----------- | -------------------- | ------------------- | ------------ |
| 3G2 | - | ✓ | - |
| 3GP | - | ✓ | - |
| AVI | ✓ | ✓ | ✓ |
| DIVX | ✓ |  | ✓ |
| F4V | ✓ | ✓ | ✓ |
| FLV | ✓ | ✓ | ✓ |
| M2T | ✓ | - | ✓ |
| M2TS | ✓ | - | ✓ |
| M2V | ✓ | - | ✓ |
| M4V | ✓ | ✓ | ✓ |
| MKV | ✓ | - | ✓ |
| MOV | ✓ | ✓ | ✓ |
| MP4 | ✓ | ✓ | ✓ |
| MPEG | ✓ | ✓ | ✓ |
| MPG | ✓ | ✓ | ✓ |
| MTS | ✓ | - | ✓ |
| OGV | ✓ | - | ✓ |
| QT | ✓ | - | ✓ |
| R3D | ✓ | - | ✓ |
| SWF | ✓ | - | ✓ |
| WEBM | ✓ | - | ✓ |
| WMV | ✓ | ✓ | ✓ |

## Videoformate in [!DNL Dynamic Media] zum Transcodieren {#video-dynamic-media-transcoding}

| Videodateierweiterung | Container | Empfohlene Video-Codecs | Nicht unterstützte Video-Codecs |
|------------------------|--------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------|
| MP4 | MPEG-4 | H264/AVC (alle Profile) |  |
| MOV, QT | Apple QuickTime | H264/AVC, Apple ProRes422 &amp; HQ, Sony XDCAM, Sony DVCAM, HDV, Panasonic DVCPro, Apple DV (DV25), Apple PhotoJPEG, Sorenson, Avid DNxHD, Avid AVR | Apple Intermediate, Apple Animation |
| FLV, F4V | Adobe Flash | H264/AVC, Flix VP6, H263, Sorenson | SWF (Vektoranimationsdateien) |
| WMV | Windows Media 9 | WMV3 (v9), WMV2 (v8), WMV1 (v7), GoToMeeting (G2M2, G2M3, G2M4) | Microsoft Screen (MSS2), Microsoft Photo Story (WVP2) |
| MPG, VOB, M2V, MP2 | MPEG-2 | MPEG-2 |  |
| M4V | Apple iTunes | H264/AVC |  |
| AVI | A/V Interleave | XVID, DIVX, HDV, MiniDV (DV25), Techsmith Camtasia, Huffyuv, Fraps, Panasonic DVCPro | Indeo3 (IV30), MJPEG, Microsoft Video 1 (MS-CRAM) |
| WebM | WebM | Google VP8 |  |
| OGV, OGG | Ogg | Theora, VP3, Dirac |  |
| MXF | MXF | Sony XDCAM, MPEG-2, MPEG-4, Panasonic DVCPro |  |
| MTS | AVCHD | H264/AVC |  |
| MKV | Matroska | H264/AVC |  |
| R3D, RM | Red Raw Video | MJPEG 2000 |  |
| RAM, RM | RealVideo | Nicht unterstützt | Real G2 (RV20), Real 8 (RV30), Real 10 (RV40) |
| FLAC | Native Flac | Free Lossless Audio Codec |  |
| MJ2 | Motion JPEG2000 | Motion JPEG 2000 Codec |  |

## Audioformate {#audio-formats}

Assets as a Cloud Service unterstützt die XMP-Metadatenextraktion für die Audioformate AIF, ASF, M4A, MP3, WAV und WMA.

>[!MORELIKETHIS]
>
>* [Asset-Verarbeitung mithilfe von Asset-Microservices](asset-microservices-overview.md)

