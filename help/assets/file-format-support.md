---
title: Dateiformate und MIME-Typen, die von Experience Manager Assets als Cloud-Dienst unterstützt werden
description: Dateiformate und MIME-Typen, die von Experience Manager Assets als Cloud-Dienst unterstützt werden.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 26833f59f21efa4de33969b7ae2e782fe5db8a14

---


# Assets supported file formats {#supported-file-formats}

Adobe Experience Manager als Cloud-Dienst unterstützt grundlegende Content-Management-Funktionen — Datenspeicherung, Online-Verwaltung von Metadaten, Versionierung, Hochladen und Herunterladen usw. — für jede Binärdatei, unabhängig von ihrem Format. Adobe Experience Manager Assets unterstützt eine breite Palette von Dateiformaten und jede Produktfunktion unterstützt unterschiedliche Formate.

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
* Allgemeine [Dokument-Formate](#document-formats), einschließlich [Microsoft Office](#microsoft-office-formats) - (Word, Excel, PowerPoint) und [Open Dokument](#opendocument-formats) -Formate.
* Umfassendes Spektrum an [Video](#video-formats)- und [Audio](#audio-formats) formaten.

Die Spalten der folgenden Tabellen enthalten die folgenden Informationen:

| Spalte | Beschreibung |
| ------------ | --------------------------------------------------------------- |
| Format | Dateiformat (Dateierweiterung) des Assets, Original-Binärdatei |
| GIF | GIF-Format für die Generierung von Darstellungen |
| JPEG | JPEG-Format für die Generierung von Darstellungen |
| PNG | PNG-Format für die Generierung von Darstellungen |
| XMP | Extraktion von Metadaten aus der ursprünglichen Binärdatei |
| TXT | Extraktion von Texten aus Dokument zur Indizierung |
| Breite/Höhe | Unterstützung für das Definieren der Breite und Höhe einer Darstellung (Pixel) |

### Adobe-Formate {#adobe-formats}

| Dateiformat | GIF | JPEG | PNG | TXT | XMP | Breite/Höhe |
| ----------- | --- | ---- | --- | --- | --- | ------------ |
| AI | ✓ | ✓ | ✓ | - | ✓ | ✓ |
| COLLAGE | - | - | - | - | ✓ | - |
| DN | ✓ | ✓ | ✓ |  | ✓ | ✓ |
| IDEEN | - | - | - | - | ✓ | - |
| INDD | ✓ | ✓ | ✓ | - | ✓ | ✓* |
| INDT | - | - | - | - | ✓ | - |
| PDF | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| PROTO | - | - | - | - | ✓ | - |
| PSB | ✓ | ✓ | ✓ | - | ✓ | ✓ |
| PSD | ✓ | ✓ | ✓ | - | ✓ | ✓ |
| XD | ✓ | ✓ | ✓ | - | ✓ | ✓ |

\* Bei INDD (InDesign-Dateien) wird die Größe der Darstellung durch die in der INDD-Datei eingebettete Vorschau bestimmt. Konfigurieren Sie die Voreinstellungen in InDesign (&quot;**[!UICONTROL Voreinstellungen&quot;> &quot;Dateihandhabung&quot;> &quot;Vorschau immer mit Dokumenten speichern&quot;, &quot;Vorschau-Größe]**&quot;), um eine größere Darstellung einzubetten.

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

### Dokument-Formate {#document-formats}

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

Folgende Dokument-Formate werden für Asset-Management-Funktionen unterstützt:

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

