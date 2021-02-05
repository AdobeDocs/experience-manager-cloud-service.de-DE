---
title: Unterstützte Dateiformate und MIME-Typen
description: Dateiformate und MIME-Typen, die von [!DNL Experience Manager Assets] als [!DNL Cloud Service] unterstützt werden.
contentOwner: AG
translation-type: tm+mt
source-git-commit: ceaa9546be160e01b124154cc827e6b967388476
workflow-type: tm+mt
source-wordcount: '818'
ht-degree: 86%

---


# [!DNL Assets] unterstützte Dateiformate  {#supported-file-formats}

[!DNL Adobe Experience Manager] as a unterstützt grundlegende Content-Management-Funktionen – wie Speicherung, Online-Verwaltung von Metadaten, Versionierung, Uploads und Downloads – für jede Binärdatei unabhängig vom Format. [!DNL Cloud Service] [!DNL Adobe Experience Manager Assets] unterstützt eine Vielzahl von Dateiformaten. Jede Produktfunktion bietet unterschiedliche Unterstützung für verschiedene Formate.

Darüber hinaus bietet [!DNL Experience Manager Assets] erweiterte Unterstützung zum Generieren von Vorschauen und Darstellungen sowie zum Extrahieren von Metadaten und Text für die Indexierung im Volltext. Diese erweiterte Unterstützung wird mithilfe von [Asset-Microservices](asset-microservices-configure-and-use.md) bereitgestellt.

Zu den Highlights für die Asset-Konvertierung mithilfe von Asset-Mikrodiensten zählen:

* Schlüsseldateiformate [Adobe, die von Adobe-Anwendungen und -Diensten erstellt werden, einschließlich [!DNL Adobe Photoshop], [!DNL Adobe InDesign], [!DNL Adobe Illustrator], [!DNL Adobe XD], [!DNL Adobe Dimension] und [!DNL Adobe Acrobat] oder PDF.](#adobe-formats)
* Gängige [Bildformate](#image-formats).
* [Camera Raw-Dateiformate](#camera-raw-formats) für eine Vielzahl von Kameras von Herstellern wie Canon, Nikon, Fujifilm und Olympus (unterstützt von Adobe Camera Raw).
* Häufig verwendete [Dokumentenformate](#document-formats) wie Microsoft Office sowie Open Document-Formate.
* Ein breites Spektrum an [Video-](#video-formats) und [Audioformaten](#audio-formats).

In der folgenden Legende wird beschrieben, wie gut die einzelnen Formate unterstützt werden.

| Unterstützungsebene | Beschreibung |
| ------------- | --------------------------- |
| ✓ | Unterstützt |
| * | Siehe Anmerkungen unterhalb der Tabelle |
| - | Nicht zutreffend |

## Adobe-Formate {#adobe-formats}

| Dateiformat | Generierung von Miniaturansichten | Extraktion im Volltext | Metadatenextraktion | Breite/Höhe |
| ----------- | -------------------- | ------------------- | ------------------- | ------------ |
| AI | they | - | they | they |
| COLLAGE | - | - | they | - |
| DN | they | - | they | they |
| IDEAS | - | - | they | - |
| INDD | they | - | they | ✓ * |
| INDT | - | - | they | - |
| PDF | they | they | they | they |
| PROTO | - | - | they | - |
| PSB | they | - | they | they |
| PSD | they | - | they | they |
| XD | they | - | they | they |

\* Bei [!DNL Adobe InDesign]-Dateien (INDD) wird die Größe der Ausgabedarstellung durch die in die INDD-Datei eingebettete Vorschau bestimmt. Konfigurieren Sie die Voreinstellungen unter [!DNL InDesign] (**[!UICONTROL Voreinstellungen > Dateiverarbeitung > Vorschaubilder immer mit Dokumenten speichern, Vorschaugröße]**), um eine größere Ausgabedarstellung einzubetten.

## Bildformate {#image-formats}

| Dateiformat | Generierung von Miniaturansichten | Metadatenextraktion | Breite/Höhe | Zuschneiden |
| ----------- | -------------------- | ------------------- | ------------ | -------- |
| BMP | they | - | they | they |
| EPS | - | they | - | - |
| GIF | they | they | they | they |
| JPEG | they | they | they | they |
| PNG | they | they | they | they |
| RGB | they | they | they | they |
| RGBA | they | they | they | they |
| SGI | they | they | they | they |
| SVG | they | - | they | they |
| TIFF | they | they | they | - |

## Bildformate in [!DNL Dynamic Media] {#image-support-dynamic-media}

| Format | Hochladen (Eingabeformat) | Bildvorgabe erstellen (Ausgabeformat) | Vorschau von dynamischer Ausgabedarstellung anzeigen | Dynamische Ausgabedarstellung bereitstellen | Dynamische Ausgabedarstellung herunterladen |
| ------- | --------------------- | ----------------------------------- | ------------------------- | ------------------------- | -------------------------- |
| BMP | they | - | - | - | - |
| EPS | they | they | they | they | they |
| GIF | they | they | they | they | they |
| JPEG | they | they | they | they | they |
| PICT | they | - | - | - | - |
| PNG | they | they | they | they | they |
| PSD ‡ | they | - | - | - | - |
| TIFF | they | they | they | they | they |

‡ Das zusammengeführte Bild wird aus der PSD-Datei extrahiert. Dabei handelt es sich um ein von [!DNL Adobe Photoshop] generiertes Bild, das in der PSD enthalten ist. Je nach den Einstellungen kann dieses Bild das eigentliche Bild sein oder nicht.

Die folgenden Untertypen von Rasterbilddateiformaten, die in [!DNL Dynamic Media] nicht unterstützt werden:

* PNG-Dateien mit einer IDAT-Blockgröße größer als 100 MB.
* PSB-Dateien.
* PSD-Dateien mit einem anderen Farbraum als CMYK, RGB, Graustufen oder Bitmap werden nicht unterstützt. DuoTone-, Lab- und indizierte Farbräume werden nicht unterstützt.
* PSD-Dateien mit einer Bittiefe größer als 16.
* TIFF-Dateien mit Gleitkommadaten.
* TIFF-Dateien mit Lab-Farbraum.

## 3D-Formate {#support-3d-formats}

Die folgenden 3D-Formate werden unterstützt.

Siehe [Arbeiten mit 3D-Assets in Dynamic Media](/help/assets/dynamic-media/assets-3d.md).

| Format | Speicherung | Versionierung | Workflow | Veröffentlichung | Zugriffssteuerung | Miniaturansicht, Vorschau | 3D-Vorschau | Bereitstellung von Dynamic Media |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| DN | they | they | they | - | they | they | - | - |
| gLB | they | they | they | they | they | - | they | they |
| gLTF | they | they | they | - | they | - | they | - |
| OBJ | they | they | they | they | they | - | they | they |
| STL | they | they | they | they | they | - | they | they |
| USDz | they | they | they | they | they | - | - | they |

## [!DNL Camera RAW]-Formate {#camera-raw-formats}

| Dateiformat | Generierung von Miniaturansichten | Metadatenextraktion | Breite/Höhe |
| ----------- | -------------------- | ------------------- | ------------ |
| 3FR | they | they | they |
| ARW | they | they | they |
| CR2 | they | they | they |
| CR3 | they | they | they |
| CRW | they | they | they |
| DCR | they | they | they |
| DNG | they | they | they |
| ERF | they | they | they |
| FFF | they | they | they |
| GPR | they | they | they |
| IIQ | they | they | they |
| KDC | they | they | they |
| MEF | they | they | they |
| MFW | they | they | they |
| MOS | they | they | they |
| MRW | they | they | they |
| NEF | they | they | they |
| NRW | they | they | they |
| ORF | they | they | they |
| PEF | they | they | they |
| RAF | they | they | they |
| RAW | they | they | they |
| RW2 | they | they | they |
| RWL | they | they | they |
| SRF | they | they | they |
| SRW | they | they | they |
| X3F | they | they | they |

## Dokumentenformate {#document-formats}

Folgende Dokumentenformate werden für Asset-Management-Funktionen unterstützt.

| Dateiformat | Generierung von Miniaturansichten | Extraktion im Volltext | Breite/Höhe | Metadatenverwaltung | [Connected Assets](use-assets-across-connected-assets-instances.md) |
| ----------- | -------------------- | ------------------- | ------------ | ------------------- | ---------------- |
| DOC | - | - | - | they | they |
| DOCX | they | they | they | they | they |
| EPUB | - | they | - | - | - |
| HTML | - | they | - | they | they |
| ODF | they | they | they | - | - |
| ODM | they | they | they | - | - |
| ODP | they | they | they | - | - |
| ODS | they | they | they | - | - |
| ODT | they | they | they | they | they |
| OFG | they | they | they | - | - |
| PDF | they | they | they | they | they |
| PPT | - | - | - | they | they |
| PPTX | they | they | they | they | they |
| PS | - | - | they | - | - |
| RTF | - | they | - | they | they |
| TXT | - | they | - | they | they |
| XLS | - | - | - | they | they |
| XLSX | they | they | they | they | they |
| XML | - | they | - | - | - |

## Dokumentenformate in [!DNL Dynamic Media] {#document-support-dynamic-media}

| Format | Hochladen (Eingabeformat) | Bildvorgabe erstellen (Ausgabeformat) | Vorschau von dynamischer Ausgabedarstellung anzeigen | Dynamische Ausgabedarstellung bereitstellen | Dynamische Ausgabedarstellung herunterladen |
| ------ | --------------------- | ----------------------------------- | ------------------------- | ------------------------- | -------------------------- |
| AI | they | - | - | - | - |
| INDD | they | - | - | - | - |
| PDF | they | they | they | they | they |

## Videoformate {#video-formats}

| Dateiformat | Generierung von Miniaturansichten | Metadatenextraktion | Breite/Höhe |
| ----------- | -------------------- | ------------------- | ------------ |
| 3G2 | - | they | - |
| 3GP | - | they | - |
| AVI | they | they | they |
| DIVX | they | - | they |
| F4V | they | they | they |
| FLV | they | they | they |
| M2T | they | - | they |
| M2TS | they | - | they |
| M2V | they | - | they |
| M4V | they | they | they |
| MKV | they | - | they |
| MOV | they | they | they |
| MP4 | they | they | they |
| MPEG | they | they | they |
| MPG | they | they | they |
| MTS | they | - | they |
| MXF | they | - | they |
| OGV | they | - | they |
| QT | they | - | they |
| R3D | - | they | they |
| SWF | they | - | they |
| WebM | they | - | they |
| WMV | they | they | they |

## Videoformate in [!DNL Dynamic Media] zum Transcodieren {#video-dynamic-media-transcoding}

| Videodateierweiterung | Container | Empfohlene Video-Codecs | Nicht unterstützte Video-Codecs |
|------------------------|--------------------|--------|-------|
| MP4 | MPEG-4 | H264/AVC (alle Profile) | - |
| MOV, QT | Apple QuickTime | H264/AVC, Apple ProRes422 &amp; HQ, Sony XDCAM, Sony DVCAM, HDV, Panasonic DVCPro, Apple DV (DV25), Apple PhotoJPEG, Sorenson, Avid DNxHD, Avid AVR | Apple Intermediate, Apple Animation |
| FLV, F4V | Adobe Flash | H264/AVC, Flix VP6, H263, Sorenson | SWF (Vektoranimationsdateien) |
| WMV | Windows Media 9 | WMV3 (v9), WMV2 (v8), WMV1 (v7), GoToMeeting (G2M2, G2M3, G2M4) | Microsoft Screen (MSS2), Microsoft Photo Story (WVP2) |
| MPG, VOB, M2V, MP2 | MPEG-2 | MPEG-2 | - |
| M4V | Apple iTunes | H264/AVC | - |
| AVI | A/V Interleave | XVID, DIVX, HDV, MiniDV (DV25), Techsmith Camtasia, Huffyuv, Fraps, Panasonic DVCPro | Indeo3 (IV30), MJPEG, Microsoft Video 1 (MS-CRAM) |
| WebM | WebM | Google VP8 | - |
| OGV, OGG | Ogg | Theora, VP3, Dirac | - |
| MXF | MXF | Sony XDCAM, MPEG-2, MPEG-4, Panasonic DVCPro | - |
| MTS | AVCHD | H264/AVC | - |
| MKV | Matroska | H264/AVC | - |
| R3D, RM | Red Raw Video | MJPEG 2000 | - |
| RAM, RM | RealVideo | Nicht unterstützt | Real G2 (RV20), Real 8 (RV30), Real 10 (RV40) |
| FLAC | Native Flac | Free Lossless Audio Codec | - |
| MJ2 | Motion JPEG2000 | Motion JPEG 2000 Codec | - |

## Audioformate {#audio-formats}

[!DNL Assets] as a unterstützt die XMP-Metadatenextraktion für die Audioformate AIF, ASF, M4A, MP3, WAV und WMA.[!DNL Cloud Service]

## Tipps und Einschränkungen {#limitations-and-tips}

* Derzeit beträgt die maximale Dateigröße für die Extraktion von Metadaten etwa 10 GB. Beim Hochladen sehr großer Assets schlägt der Vorgang der Metadaten-Extraktion manchmal fehl.

>[!MORELIKETHIS]
>
>* [Asset-Verarbeitung mithilfe von Asset-Microservices](asset-microservices-overview.md)
>* [Unterstützte Dateiformate für intelligentes Tagging textbasierter Assets](/help/assets/smart-tags.md#smart-tags-supported-file-formats)

