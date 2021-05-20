---
title: Unterstützte Dateiformate und MIME-Typen
description: Von [!DNL Experience Manager Assets] as a [!DNL Cloud Service] unterstützte Dateiformate und MIME-Typen.
contentOwner: AG
feature: Asset-Management,Ausgabeformate
role: Business Practitioner,Administrator
exl-id: e848aa77-7829-4adc-8b88-0279791a4525
source-git-commit: 6b232ab512a6faaf075faa55c238dfb10c00b100
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 99%

---

# Von [!DNL Assets] unterstützte Dateiformate {#supported-file-formats}

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] unterstützt grundlegende Content-Management-Funktionen – wie Speicherung, Online-Verwaltung von Metadaten, Versionierung, Uploads und Downloads – für jede Binärdatei unabhängig vom Format. [!DNL Adobe Experience Manager Assets] unterstützt eine Vielzahl von Dateiformaten. Jede Produktfunktion bietet unterschiedliche Unterstützung für verschiedene Formate.

Darüber hinaus bietet [!DNL Experience Manager Assets] erweiterte Unterstützung zum Generieren von Vorschauen und Ausgabedarstellungen sowie zum Extrahieren von Metadaten und Text für die Volltextindizierung. Diese erweiterte Unterstützung wird mithilfe von [Asset-Microservices](asset-microservices-configure-and-use.md) bereitgestellt.

Zu den Highlights für die Asset-Konversion mithilfe von Asset-Mircoservices zählen:

* Gängige [Adobe-Dateiformate](#adobe-formats), die von Adobe-Programmen und -Services erstellt werden, einschließlich [!DNL Adobe Photoshop], [!DNL Adobe InDesign], [!DNL Adobe Illustrator], [!DNL Adobe XD], [!DNL Adobe Dimension] und [!DNL Adobe Acrobat] oder PDF.
* Gängige [Bildformate](#image-formats).
* [Camera Raw-Dateiformate](#camera-raw-formats) für eine Vielzahl von Kameras von Herstellern wie Canon, Nikon, Fujifilm und Olympus (unterstützt von Adobe Camera Raw).
* Häufig verwendete [Dokumentenformate](#document-formats) wie Microsoft Office sowie Open Document-Formate.
* Ein breites Spektrum an [Video-](#video-formats) und [Audioformaten](#audio-formats).

Der folgenden Legende können Sie entnehmen, inwieweit ein Format unterstützt wird.

| Unterstützungsebene | Beschreibung |
| ------------- | --------------------------- |
| ✓ | Unterstützt |
| * | Siehe Anmerkungen unterhalb der Tabelle |
| - | Nicht zutreffend |

## Adobe-Formate {#adobe-formats}

| Dateiformat | Generierung von Miniaturansichten | Volltextextraktion | Metadatenextraktion | Breite/Höhe |
| ----------- | -------------------- | ------------------- | ------------------- | ------------ |
| AI | verwalten | - | verwalten | verwalten |
| COLLAGE | - | - | verwalten | - |
| DN | verwalten | - | verwalten | verwalten |
| IDEAS | - | - | verwalten | - |
| INDD | verwalten | - | verwalten | ✓ * |
| INDT | - | - | verwalten | - |
| PDF | verwalten | verwalten | verwalten | verwalten |
| PROTO | - | - | verwalten | - |
| PSB | verwalten | - | verwalten | verwalten |
| PSD | verwalten | - | verwalten | verwalten |
| XD | verwalten | - | verwalten | verwalten |

\* Bei [!DNL Adobe InDesign]-Dateien (INDD) wird die Größe der Ausgabedarstellung durch die in die INDD-Datei eingebettete Vorschau bestimmt. Konfigurieren Sie die Voreinstellungen unter [!DNL InDesign] (**[!UICONTROL Voreinstellungen > Dateiverarbeitung > Vorschaubilder immer mit Dokumenten speichern, Vorschaugröße]**), um eine größere Ausgabedarstellung einzubetten.

## Bildformate {#image-formats}

| Dateiformat | Generierung von Miniaturansichten | Metadatenextraktion | Breite/Höhe | Zuschneiden |
| ----------- | -------------------- | ------------------- | ------------ | -------- |
| BMP | verwalten | - | verwalten | verwalten |
| EPS | - | verwalten | - | - |
| GIF | verwalten | verwalten | verwalten | verwalten |
| JPEG | verwalten | verwalten | verwalten | verwalten |
| PNG | verwalten | verwalten | verwalten | verwalten |
| RGB | verwalten | verwalten | verwalten | verwalten |
| RGBA | verwalten | verwalten | verwalten | verwalten |
| SGI | verwalten | verwalten | verwalten | verwalten |
| SVG | verwalten | - | verwalten | verwalten |
| TIFF | verwalten | verwalten | verwalten | - |

## Bildformate in [!DNL Dynamic Media] {#image-support-dynamic-media}

| Format | Hochladen (Eingabeformat) | Bildvorgabe erstellen (Ausgabeformat) | Vorschau von dynamischer Ausgabedarstellung anzeigen | Dynamische Ausgabedarstellung bereitstellen | Dynamische Ausgabedarstellung herunterladen |
| ------- | --------------------- | ----------------------------------- | ------------------------- | ------------------------- | -------------------------- |
| BMP | verwalten | - | - | - | - |
| EPS | verwalten | verwalten | verwalten | verwalten | verwalten |
| GIF | verwalten | verwalten | verwalten | verwalten | verwalten |
| JPEG | verwalten | verwalten | verwalten | verwalten | verwalten |
| PICT | verwalten | - | - | - | - |
| PNG | verwalten | verwalten | verwalten | verwalten | verwalten |
| PSD ‡ | verwalten | - | - | - | - |
| TIFF | verwalten | verwalten | verwalten | verwalten | verwalten |

‡ Das zusammengeführte Bild wird aus der PSD-Datei extrahiert. Dabei handelt es sich um ein von [!DNL Adobe Photoshop] generiertes Bild, das in der PSD enthalten ist. Je nach den Einstellungen kann dieses Bild das eigentliche Bild sein oder nicht.

Die folgenden Untertypen von Rasterbilddateiformaten, die in [!DNL Dynamic Media] nicht unterstützt werden:

* PNG-Dateien mit einer IDAT-Blockgröße größer als 100 MB.
* PSB-Dateien.
* PSD-Dateien mit einem anderen Farbraum als CMYK, RGB, Graustufen oder Bitmap werden nicht unterstützt. DuoTone-, Lab- und indizierte Farbräume werden nicht unterstützt.
* PSD-Dateien mit einer Bittiefe größer als 16.
* TIFF-Dateien mit Gleitkommadaten.
* TIFF-Dateien mit Lab-Farbraum.

## 3D-Formate {#support-3d-formats}

Die folgenden 3D-Formate werden unterstützt:

Siehe [Arbeiten mit 3D-Assets in Dynamic Media](/help/assets/dynamic-media/assets-3d.md).

| Format | Speicherung | Versionierung | Workflow | Veröffentlichung | Zugriffssteuerung | Miniaturansicht, Vorschau | 3D-Vorschau | Bereitstellung von Dynamic Media |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| DN | verwalten | verwalten | verwalten | - | verwalten | verwalten | - | - |
| gLB | verwalten | verwalten | verwalten | verwalten | verwalten | - | verwalten | verwalten |
| gLTF | verwalten | verwalten | verwalten | - | verwalten | - | verwalten | - |
| OBJ | verwalten | verwalten | verwalten | verwalten | verwalten | - | verwalten | verwalten |
| STL | verwalten | verwalten | verwalten | verwalten | verwalten | - | verwalten | verwalten |
| USDz | verwalten | verwalten | verwalten | verwalten | verwalten | - | - | verwalten |

## [!DNL Camera RAW]-Formate {#camera-raw-formats}

| Dateiformat | Generierung von Miniaturansichten | Metadatenextraktion | Breite/Höhe |
| ----------- | -------------------- | ------------------- | ------------ |
| 3FR | verwalten | verwalten | verwalten |
| ARW | verwalten | verwalten | verwalten |
| CR2 | verwalten | verwalten | verwalten |
| CR3 | verwalten | verwalten | verwalten |
| CRW | verwalten | verwalten | verwalten |
| DCR | verwalten | verwalten | verwalten |
| DNG | verwalten | verwalten | verwalten |
| ERF | verwalten | verwalten | verwalten |
| FFF | verwalten | verwalten | verwalten |
| GPR | verwalten | verwalten | verwalten |
| IIQ | verwalten | verwalten | verwalten |
| KDC | verwalten | verwalten | verwalten |
| MEF | verwalten | verwalten | verwalten |
| MFW | verwalten | verwalten | verwalten |
| MOS | verwalten | verwalten | verwalten |
| MRW | verwalten | verwalten | verwalten |
| NEF | verwalten | verwalten | verwalten |
| NRW | verwalten | verwalten | verwalten |
| ORF | verwalten | verwalten | verwalten |
| PEF | verwalten | verwalten | verwalten |
| RAF | verwalten | verwalten | verwalten |
| RAW | verwalten | verwalten | verwalten |
| RW2 | verwalten | verwalten | verwalten |
| RWL | verwalten | verwalten | verwalten |
| SRF | verwalten | verwalten | verwalten |
| SRW | verwalten | verwalten | verwalten |
| X3F | verwalten | verwalten | verwalten |

## Dokumentenformate {#document-formats}

Folgende Dokumentenformate werden für Asset-Management-Funktionen unterstützt.

| Dateiformat | Generierung von Miniaturansichten | Volltextextraktion | Breite/Höhe | Metadatenverwaltung | [Connected Assets](use-assets-across-connected-assets-instances.md) |
| ----------- | -------------------- | ------------------- | ------------ | ------------------- | ---------------- |
| DOC | - | - | - | verwalten | verwalten |
| DOCX | verwalten | verwalten | verwalten | verwalten | verwalten |
| EPUB | - | verwalten | - | - | - |
| HTML | - | verwalten | - | verwalten | verwalten |
| ODF | verwalten | verwalten | verwalten | - | - |
| ODM | verwalten | verwalten | verwalten | - | - |
| ODP | verwalten | verwalten | verwalten | - | - |
| ODS | verwalten | verwalten | verwalten | - | - |
| ODT | verwalten | verwalten | verwalten | verwalten | verwalten |
| OFG | verwalten | verwalten | verwalten | - | - |
| PDF | verwalten | verwalten | verwalten | verwalten | verwalten |
| PPT | - | - | - | verwalten | verwalten |
| PPTX | verwalten | verwalten | verwalten | verwalten | verwalten |
| PS | - | - | verwalten | - | - |
| RTF | - | verwalten | - | verwalten | verwalten |
| TXT | - | verwalten | - | verwalten | verwalten |
| XLS | - | - | - | verwalten | verwalten |
| XLSX | verwalten | verwalten | verwalten | verwalten | verwalten |
| XML | - | verwalten | - | - | - |

## Dokumentenformate in [!DNL Dynamic Media] {#document-support-dynamic-media}

| Format | Hochladen (Eingabeformat) | Bildvorgabe erstellen (Ausgabeformat) | Vorschau von dynamischer Ausgabedarstellung anzeigen | Dynamische Ausgabedarstellung bereitstellen | Dynamische Ausgabedarstellung herunterladen |
| ------ | --------------------- | ----------------------------------- | ------------------------- | ------------------------- | -------------------------- |
| KI | verwalten | - | - | - | - |
| INDD | verwalten | - | - | - | - |
| PDF | verwalten | verwalten | verwalten | verwalten | verwalten |

## Videoformate {#video-formats}

| Dateiformat | Generierung von Miniaturansichten | Metadatenextraktion | Breite/Höhe |
| ----------- | -------------------- | ------------------- | ------------ |
| 3G2 | - | verwalten | - |
| 3GP | - | verwalten | - |
| AVI | verwalten | verwalten | verwalten |
| DIVX | verwalten | - | verwalten |
| F4V | verwalten | verwalten | verwalten |
| FLV | verwalten | verwalten | verwalten |
| M2T | verwalten | - | verwalten |
| M2TS | verwalten | - | verwalten |
| M2V | verwalten | - | verwalten |
| M4V | verwalten | verwalten | verwalten |
| MKV | verwalten | - | verwalten |
| MOV | verwalten | verwalten | verwalten |
| MP4 | verwalten | verwalten | verwalten |
| MPEG | verwalten | verwalten | verwalten |
| MPG | verwalten | verwalten | verwalten |
| MTS | verwalten | - | verwalten |
| MXF | verwalten | - | verwalten |
| OGV | verwalten | - | verwalten |
| QT | verwalten | - | verwalten |
| R3D | - | verwalten | verwalten |
| SWF | verwalten | - | verwalten |
| WebM | verwalten | - | verwalten |
| WMV | verwalten | verwalten | verwalten |

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

[!DNL Assets] as a [!DNL Cloud Service] unterstützt die XMP-Metadatenextraktion für die Audioformate AIF, ASF, M4A, MP3, WAV und WMA.

## Tipps und Einschränkungen {#limitations-and-tips}

* Derzeit beträgt die maximale Dateigröße für die Extraktion von Metadaten etwa 10 GB. Beim Hochladen sehr großer Assets schlägt die Metadatenextraktion manchmal fehl.

>[!MORELIKETHIS]
>
>* [Asset-Verarbeitung mithilfe von Asset-Microservices](asset-microservices-overview.md)
* [Unterstützte Dateiformate für das Tagging textbasierter Assets mit Smart-Tags](/help/assets/smart-tags.md#smart-tags-supported-file-formats)

