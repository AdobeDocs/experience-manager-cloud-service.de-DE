---
title: Von Adobe Experience Manager Assets as a Cloud Service unterstützte Dateiformate und MIME-Typen
description: Von Adobe Experience Manager Assets as a Cloud Service unterstützte Dateiformate und MIME-Typen
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0686acbc61b3902c6c926eaa6424828db0a6421a

---


# Von AEM Assets unterstützte Dateiformate {#supported-file-formats}

Adobe Experience Manager als Cloud-Dienst unterstützt grundlegende Content-Management-Funktionen — Datenspeicherung, Online-Verwaltung von Metadaten, Versionierung, Hochladen und Herunterladen usw. — für jede Binärdatei, unabhängig von ihrem Format. Adobe Experience Manager Assets unterstützt eine breite Palette von Dateiformaten und jede Produktfunktion unterstützt unterschiedliche Formate.

Darüber hinaus bietet Experience Manager Assets erweiterte Unterstützung zum Generieren von Vorschauen und Darstellungen sowie zum Extrahieren von Metadaten und Text für die Indexierung im Volltext. Diese erweiterte Unterstützung wird mithilfe von [Asset-Microservices](asset-microservices-configure-and-use.md) bereitgestellt.

In der folgenden Legende wird der Grad der Unterstützung beschrieben.

| Unterstützungsebene | Beschreibung |
| ------------- | --------------------------- |
| ✓ | Unterstützt |
| * | Siehe Anmerkungen unterhalb der Tabelle |
| - | Nicht zutreffend |

## Asset conversion using asset microservices {#asset-microservices-supported-formats}

Hier einige der Highlights:

* Key [Adobe file formats](#adobe-formats) produced by Adobe applications and services, including Adobe Photoshop, Adobe InDesign, Adobe Illustrator, Adobe XD, Adobe Dimension, and Adobe Acrobat or PDF.
* Gängige [Bildformate](#image-formats).
* [Camera Raw-Dateiformate](#camera-raw-formats) für eine Vielzahl von Kameras von Herstellern wie Canon, Nikon, Fujifilm und Olympus (unterstützt von Adobe Camera Raw).
* Common [document formats](#document-formats), including Microsoft Office and Open Document formats.
* Ein breites Spektrum an [Video-](#video-formats) und [Audioformaten.](#audio-formats)

Die Spalten der folgenden Tabellen enthalten die folgenden Informationen:

| Spalte | Beschreibung |
| ------------ | --------------------------------------------------------------- |
| Format | Dateiformat (Dateierweiterung) der ursprünglichen Binärdatei des Assets. |
| GIF | GIF-Format für die Generierung von Ausgabeformaten. |
| JPEG | JPEG-Format für die Generierung von Ausgabeformaten. |
| PNG | PNG-Format für die Generierung von Ausgabeformaten. |
| Breite/Höhe | Unterstützung zur Definition der Breite und Höhe einer Darstellung in Pixel. |

### Adobe-Formate {#adobe-formats}

| Dateiformat | GIF | JPEG | PNG | Volltextextraktion | Metadatenextraktion | Breite/Höhe |
| ----------- | -------- | -------- | -------- | ------------------- | ------------------- | ------------ |
| AI | ✓ | ✓ | ✓ | - | ✓ | ✓ |
| COLLAGE | - | - | - | - | ✓ | - |
| DN | ✓ | ✓ | ✓ |  | ✓ | ✓ |
| IDEAS | - | - | - | - | ✓ | - |
| INDD | ✓ | ✓ | ✓ | - | ✓ | ✓* |
| INDT | - | - | - | - | ✓ | - |
| PDF | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| PROTO | - | - | - | - | ✓ | - |
| PSB | ✓ | ✓ | ✓ | - | ✓ | ✓ |
| PSD | ✓ | ✓ | ✓ | - | ✓ | ✓ |
| XD | ✓ | ✓ | ✓ | - | ✓ | ✓ |

\* Bei INDD (InDesign-Dateien) wird die Größe des Ausgabeformats durch die in die INDD-Datei eingebettete Vorschau bestimmt. Konfigurieren Sie die Voreinstellungen in InDesign (**[!UICONTROL Voreinstellungen > Dateiverarbeitung > Vorschaubilder immer mit Dokumenten speichern, Vorschaugröße]**), um ein größeres Ausgabeformat einzubetten.

### Bildformate {#image-formats}

| Dateiformat | GIF | JPEG | PNG | Metadatenextraktion | Breite/Höhe |
| ----------- | -------- | -------- | -------- | ------------------- | ------------ |
| BMP | ✓ | ✓ | ✓ | - | ✓ |
| EPS | - | - | - | ✓ | - |
| GIF | ✓ | ✓ | ✓ | ✓ | ✓ |
| JPEG | ✓ | ✓ | ✓ | ✓ | ✓ |
| PNG | ✓ | ✓ | ✓ | ✓ | ✓ |
| SVG | - | - | - | ✓ | - |
| TIFF | ✓ | ✓ | ✓ | ✓ | ✓ |

### Camera RAW-Formate {#camera-raw-formats}

| Dateiformat | GIF | JPEG | PNG | Metadatenextraktion | Breite/Höhe |
| ----------- | -------- | -------- | -------- | ------------------- | ------------ |
| 3FR | ✓ | ✓ | ✓ | ✓ | ✓ |
| ARW | ✓ | ✓ | ✓ | ✓ | ✓ |
| CR2 | ✓ | ✓ | ✓ | ✓ | ✓ |
| CR3 | ✓ | ✓ | ✓ | ✓ | ✓ |
| CRW | ✓ | ✓ | ✓ | ✓ | ✓ |
| DCR | ✓ | ✓ | ✓ | ✓ | ✓ |
| DNG | ✓ | ✓ | ✓ | ✓ | ✓ |
| ERF | ✓ | ✓ | ✓ | ✓ | ✓ |
| FFF | ✓ | ✓ | ✓ | ✓ | ✓ |
| GPR | ✓ | ✓ | ✓ | ✓ | ✓ |
| IIQ | ✓ | ✓ | ✓ | ✓ | ✓ |
| KDC | ✓ | ✓ | ✓ | ✓ | ✓ |
| MEF | ✓ | ✓ | ✓ | ✓ | ✓ |
| MFW | ✓ | ✓ | ✓ | ✓ | ✓ |
| MOS | ✓ | ✓ | ✓ | ✓ | ✓ |
| MRW | ✓ | ✓ | ✓ | ✓ | ✓ |
| NEF | ✓ | ✓ | ✓ | ✓ | ✓ |
| NRW | ✓ | ✓ | ✓ | ✓ | ✓ |
| ORF | ✓ | ✓ | ✓ | ✓ | ✓ |
| PEF | ✓ | ✓ | ✓ | ✓ | ✓ |
| RAF | ✓ | ✓ | ✓ | ✓ | ✓ |
| RAW | ✓ | ✓ | ✓ | ✓ | ✓ |
| RW2 | ✓ | ✓ | ✓ | ✓ | ✓ |
| RWL | ✓ | ✓ | ✓ | ✓ | ✓ |
| SRF | ✓ | ✓ | ✓ | ✓ | ✓ |
| SRW | ✓ | ✓ | ✓ | ✓ | ✓ |
| X3F | ✓ | ✓ | ✓ | ✓ | ✓ |

### Dokumentenformate {#document-formats}

Die folgenden Dokument-Formate werden für Asset-Management-Funktionen unterstützt:

|  | GIF | JPEG | PNG | Volltextextraktion | Breite/Höhe | Metadatenverwaltung | [Connected Assets](use-assets-across-connected-assets-instances.md) |
| ---- | -------- | -------- | -------- | ------------------- | ------------ | ------------------- | ---------------- |
| PDF | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| DOCX | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| DOC | - | - | - | - | - | ✓ | ✓ |
| PPTX | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| PPT | - | - | - | - | - | ✓ | ✓ |
| XLSX | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| XLS | - | - | - | - | - | ✓ | ✓ |
| ODF | ✓ | ✓ | ✓ | ✓ | ✓ | - | - |
| OFG | ✓ | ✓ | ✓ | ✓ | ✓ | - | - |
| ODM | ✓ | ✓ | ✓ | ✓ | ✓ | - | - |
| ODP | ✓ | ✓ | ✓ | ✓ | ✓ | - | - |
| ODS | ✓ | ✓ | ✓ | ✓ | ✓ | - | - |
| ODT | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| EPUB | - | - | - | ✓ | - | - | - |
| HTML | - | - | - | ✓ | - | ✓ | ✓ |
| PS | - | - | - | - | ✓ | - | - |
| RTF | - | - | - | ✓ | - | ✓ | ✓ |
| TXT | - | - | - | ✓ | - | ✓ | ✓ |
| XML | - | - | - | ✓ | - | - | - |

### Videoformate {#video-formats}

| Dateiformat | GIF | JPEG | PNG | Metadatenextraktion | Breite/Höhe |
| ----------- | -------- | -------- | -------- | ------------------- | ------------ |
| 3G2 | - | - | - | ✓ | - |
| 3GP | - | - | - | ✓ | - |
| AVI | ✓ | ✓ | ✓ | ✓ | ✓ |
| DIVX | ✓ | ✓ | ✓ |  | ✓ |
| F4V | ✓ | ✓ | ✓ | ✓ | ✓ |
| FLV | ✓ | ✓ | ✓ | ✓ | ✓ |
| M2T | ✓ | ✓ | ✓ | - | ✓ |
| M2TS | ✓ | ✓ | ✓ | - | ✓ |
| M2V | ✓ | ✓ | ✓ | - | ✓ |
| M4V | ✓ | ✓ | ✓ | ✓ | ✓ |
| MKV | ✓ | ✓ | ✓ | - | ✓ |
| MOV | ✓ | ✓ | ✓ | ✓ | ✓ |
| MP4 | ✓ | ✓ | ✓ | ✓ | ✓ |
| MPEG | ✓ | ✓ | ✓ | ✓ | ✓ |
| MPG | ✓ | ✓ | ✓ | ✓ | ✓ |
| MTS | ✓ | ✓ | ✓ | - | ✓ |
| OGV | ✓ | ✓ | ✓ | - | ✓ |
| QT | ✓ | ✓ | ✓ | - | ✓ |
| R3D | ✓ | ✓ | ✓ | - | ✓ |
| SWF | ✓ | ✓ | ✓ | - | ✓ |
| WEBM | ✓ | ✓ | ✓ | - | ✓ |
| WMV | ✓ | ✓ | ✓ | ✓ | ✓ |

### Audioformate {#audio-formats}

Assets als Cloud-Dienst bietet Unterstützung für XMP-Metadaten-Extraktionen für die Audioformate AIF, ASF, M4A, MP3, WAV und WMA.

>[!MORELIKETHIS]
>
>* [Asset-Verarbeitung mithilfe von Asset-Microservices](asset-microservices-overview.md)

