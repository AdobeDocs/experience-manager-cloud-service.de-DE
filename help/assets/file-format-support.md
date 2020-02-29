---
title: Dateiformate und MIME-Typen, die von Experience Manager Assets als Cloud-Dienst unterstützt werden
description: Dateiformate und MIME-Typen, die von Experience Manager Assets als Cloud-Dienst unterstützt werden.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 9a7d2cff969a7920eb4fa3597846c11aa16392d9

---


# Assets supported file formats {#supported-file-formats}

Adobe Experience Manager als Cloud-Dienst unterstützt grundlegende Inhaltsverwaltungsfunktionen — Speicherung, Online-Verwaltung von Metadaten, Versionierung, Upload und Download usw. — für jede Binärdatei, unabhängig vom Format. Adobe Experience Manager Assets unterstützt eine breite Palette von Dateiformaten und jede Produktfunktion unterstützt unterschiedliche Formate.

Darüber hinaus bietet Experience Manager Assets erweiterte Unterstützung zum Generieren von Vorschauen und Darstellungen sowie zum Extrahieren von Metadaten und Text für die Indexierung im Volltext. Diese erweiterte Unterstützung wird mithilfe von [Asset-Mikrodiensten](asset-microservices-configure-and-use.md)bereitgestellt.

In der folgenden Legende wird der Grad der Unterstützung beschrieben.

| Unterstützungsebene | Beschreibung |
| ------------------------------------------------------------ | --------------------------- |
| ✓ | Unterstützt |
| * | Siehe Bemerkungen unter der Tabelle |
| - | Nicht zutreffend |

## Asset-Konvertierung mithilfe von Asset-Mikrodiensten {#asset-microservices-supported-formats}

Hier einige der Highlights:

* Wichtige [Adobe-Dateiformate](#adobe-formats) , die von Adobe-Anwendungen und -Diensten produziert werden, einschließlich Adobe Fotoshop, InDesign, Illustrator, XD, Dimension und Acrobat/PDF.
* Wichtige [Bilddateiformate](#image-formats).
* [Camera Raw-Dateiformate](#camera-raw-formats) für eine Vielzahl von Kameras, darunter Canon, Nikon, Fujifilm, Olympus und andere Hersteller (powered by Adobe Camera Raw).
* Allgemeine [Dokumentformate](#document-formats), einschließlich der Formate [Microsoft Office](#microsoft-office-formats) (Word, Excel, PowerPoint) und [Open Document](#opendocument-formats) .
* Umfassendes Spektrum an [Video](#video-formats)- und [Audio](#audio-formats) formaten.

Die Spalten der folgenden Tabellen enthalten folgende Informationen:

| Spalte | Beschreibung |
| ------------ | --------------------------------------------------------------- |
| Format | Dateiformat (Dateierweiterung) des Assets, Original-Binärdatei |
| GIF | GIF-Format für die Generierung von Darstellungen |
| JPEG | JPEG-Format für die Generierung von Darstellungen |
| PNG | PNG-Format für die Generierung von Darstellungen |
| XMP | Extrahieren von Metadaten aus der ursprünglichen Binärdatei |
| TXT | Extrahieren von Text aus einem Dokument zur Indizierung |
| Breite/Höhe | Unterstützung für das Definieren der Breite und Höhe einer Darstellung (Pixel) |

### Adobe-Formate {#adobe-formats}

| Dateiformat | GIF | JPEG | PNG | TXT | XMP | Breite/Höhe |
| ----------- | --- | ---- | --- | --- | --- | ------------ |
| AI | ✓ | ✓ | ✓ | - | ✓ | ✓ |
| SPALTE | - | - | - | - | ✓ | - |
| DN | ✓ | ✓ | ✓ |  | ✓ | ✓ |
| IDEEN | - | - | - | - | ✓ | - |
| INDD | ✓ | ✓ | ✓ | - | ✓ | ✓* |
| INDT | - | - | - | - | ✓ | - |
| PDF | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| PROTO | - | - | - | - | ✓ | - |
| PSB | ✓ | ✓ | ✓ | - | ✓ | ✓ |
| PSD | ✓ | ✓ | ✓ | - | ✓ | ✓ |
| XD | ✓ | ✓ | ✓ | - | ✓ | ✓ |

\* Bei INDD (InDesign-Dateien) wird die Größe der Darstellung durch die in die INDD-Datei eingebettete Vorschau bestimmt. Konfigurieren Sie die Voreinstellungen in InDesign (**[!UICONTROL Voreinstellungen > Dateihandhabung > Vorschaubilder immer mit Dokumenten speichern, Vorschaugröße]**), um eine größere Darstellung einzubetten.

### Bildformate {#image-formats}

| Dateiformat | GIF | JPEG | PNG | XMP | Breite/Höhe |
| ----------- | --- | ---- | --- | --- | ------------ |
| BMP | ✓ | ✓ | ✓ | - | ✓ |
| EPS | - | - | - | ✓ | - |
| GIF | ✓ | ✓ | ✓ | ✓ | ✓ |
| JPEG | ✓ | ✓ | ✓ | ✓ | ✓ |
| PNG | ✓ | ✓ | ✓ | ✓ | ✓ |
| SVG | - | - | - | ✓ | - |
| TIFF | ✓ | ✓ | ✓ | ✓ | ✓ |

### Camera RAW-Formate {#camera-raw-formats}

| Dateiformat | GIF | JPEG | PNG | XMP | Breite/Höhe |
| ----------- | --- | ---- | --- | --- | ------------ |
| 3FR | ✓ | ✓ | ✓ | ✓ | ✓ |
| ARW | ✓ | ✓ | ✓ | ✓ | ✓ |
| CR2 | ✓ | ✓ | ✓ | ✓ | ✓ |
| CR3 | ✓ | ✓ | ✓ | ✓ | ✓ |
| CRW | ✓ | ✓ | ✓ | ✓ | ✓ |
| DCR | ✓ | ✓ | ✓ | ✓ | ✓ |
| DNG | ✓ | ✓ | ✓ | ✓ | ✓ |
| EFF | ✓ | ✓ | ✓ | ✓ | ✓ |
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

### Dokumentformate {#document-formats}

| Dateiformat | TXT | XMP |
| ----------- | --- | --- |
| EPUB | ✓ | - |
| HTML | ✓ | - |
| PS | - | ✓ |
| RTF | ✓ | - |
| TEXT | ✓ | - |
| XML | ✓ | - |

### Microsoft Office-Formate {#microsoft-office-formats}

| Dateiformat | GIF | JPEG | PNG | TEXT | Breite/Höhe |
| ----------- | --- | ---- | --- | ---- | ------------ |
| DOCX | ✓ | ✓ | ✓ | ✓ | ✓ |
| PPTX | ✓ | ✓ | ✓ | ✓ | ✓ |
| XLSX | ✓ | ✓ | ✓ | ✓ | ✓ |

### OpenDocument-Formate {#opendocument-formats}

| Dateiformat | GIF | JPEG | PNG | TEXT | Höhe |
| ----------- | --- | ---- | --- | ---- | ------ |
| ODF | ✓ | ✓ | ✓ | ✓ | ✓ |
| OFG | ✓ | ✓ | ✓ | ✓ | ✓ |
| ODM | ✓ | ✓ | ✓ | ✓ | ✓ |
| ODP | ✓ | ✓ | ✓ | ✓ | ✓ |
| ODS | ✓ | ✓ | ✓ | ✓ | ✓ |
| ODT | ✓ | ✓ | ✓ | ✓ | ✓ |

### Videoformate {#video-formats}

| Dateiformat | GIF | JPEG | PNG | XMP | Breite/Höhe |
| ----------- | --- | ---- | --- | --- | ------------ |
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

Assets als Cloud-Dienst bietet XMP-Unterstützung für die folgenden Audioformate: AIF, ASF, M4A, MP3, WAV und WMA.

## Unterstützte Dokumentformate {#doc-formats}

Die folgenden Dokumentformate werden für Asset-Verwaltungsfunktionen unterstützt:

| Dateiformat | Speicher | Metadatenverwaltung | [Connected Assets](use-assets-across-connected-assets-instances.md) |
|---|---|---|---|
| DOC | ✓ | ✓ | ✓ |
| DOCX | ✓ | ✓ | ✓ |
| ODT | ✓ | ✓ | ✓ |
| PDF | ✓ | ✓ | ✓ |
| HTML | ✓ | ✓ | ✓ |
| RTF | ✓ | ✓ | ✓ |
| TXT | ✓ | ✓ | ✓ |
| XLS | ✓ | ✓ | ✓ |
| XLSX | ✓ | ✓ | ✓ |
| PPT | ✓ | ✓ | ✓ |
| PPTX | ✓ | ✓ | ✓ |

>[!MORELIKETHIS]
>
>* [Asset-Verarbeitung mithilfe von Asset-Mikrodiensten](asset-microservices-overview.md)

