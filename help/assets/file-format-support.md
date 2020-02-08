---
title: Dateiformate und MIME-Typen, die von Experience Manager Assets als Cloud-Dienst unterstützt werden
description: Dateiformate und MIME-Typen, die von Experience Manager Assets als Cloud-Dienst unterstützt werden.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 776b089a322cc4f86fdcb9ddf1c3cc207fc85d39

---


# Assets supported file formats {#supported-file-formats}

Adobe Experience Manager als Cloud-Dienst unterstützt grundlegende Inhaltsverwaltungsfunktionen - Speicherung, Online-Verwaltung von Metadaten, Versionierung, Hochladen und Herunterladen usw. - für jede Binärdatei unabhängig vom Format. Darüber hinaus bietet es erweiterte Unterstützung für häufig verwendete Dateiformate wie Bilder, Adobe-proprietäre Formate, Dokumente und Videos, um Vorschauen und Darstellungen zu generieren und Metadaten und Text für die Indexierung im Volltext zu extrahieren. Diese erweiterte Unterstützung wird mithilfe von [Asset-Mikrodiensten](asset-microservices-configure-and-use.md)bereitgestellt.

Zu den wichtigsten Dateiformaten mit erweiterter Unterstützung zählen:

* Wichtige [Adobe-Dateiformate](#adobe-formats) , die von Adobe-Anwendungen und -Diensten produziert werden, einschließlich Adobe Fotoshop, InDesign, Illustrator, XD, Dimension und Acrobat/PDF.
* Wichtige [Bildformate](#image-formats)
* [Dateiformate](#camera-raw-formats) für eine Vielzahl von Kameras, darunter Canon, Nikon, Fujifilm, Olympus und andere Hersteller (mit Adobe Camera Raw)
* Allgemeine [Dokumentformate](#document-formats), einschließlich der Formate [Microsoft Office](#microsoft-office-formats) (Word, Excel, PowerPoint) und [Open Document](#opendocument-formats)
* Umfassendes Spektrum an [Video](#video-formats) - und [Audioformaten](#audio-formats)

## Legende für detaillierte Support-Informationen {#legend-for-detailed-support-information}

In der folgenden Legende wird die Unterstützung für eine Funktion beschrieben:

| Unterstützungsebene | Beschreibung |
| ------------------------------------------------------------ | --------------------------- |
| ✓ | Unterstützt |
| * | Siehe Bemerkungen unter der Tabelle |
| - | Nicht zutreffend |

Die Spalten der Unterstützungstabellen enthalten die folgenden Informationen:

| Spalte | Beschreibung |
| ------------ | --------------------------------------------------------------- |
| Format | Dateiformat (Dateierweiterung) des Assets, Original-Binärdatei |
| GIF | GIF-Format für die Generierung von Darstellungen |
| JPEG | JPEG-Format für die Generierung von Darstellungen |
| PNG | PNG-Format für die Generierung von Darstellungen |
| XMP | Extrahieren von Metadaten aus der ursprünglichen Binärdatei |
| TXT | Extrahieren von Text aus einem Dokument zur Indizierung |
| Breite/Höhe | Unterstützung für das Definieren der Breite und Höhe einer Darstellung (Pixel) |

<!-- Adding this checkmark icon ✓ does not look good in table. The icon's shade and size has to be toned down for good readability and less clutter.
@gklebus: I suggest using a checkmark character, either U+2713 ✓ CHECK MARK or U+2714 ✔ HEAVY CHECK MARK
-->

## Adobe-Formate {#adobe-formats}

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

## Bildformate {#image-formats}

| Dateiformat | GIF | JPEG | PNG | XMP | Breite/Höhe |
| ----------- | --- | ---- | --- | --- | ------------ |
| BMP | ✓ | ✓ | ✓ | - | ✓ |
| EPS | - | - | - | ✓ | - |
| GIF | ✓ | ✓ | ✓ | ✓ | ✓ |
| JPEG | ✓ | ✓ | ✓ | ✓ | ✓ |
| PNG | ✓ | ✓ | ✓ | ✓ | ✓ |
| SVG | - | - | - | ✓ | - |
| TIFF | ✓ | ✓ | ✓ | ✓ | ✓ |


## Camera RAW-Formate {#camera-raw-formats}

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

## Dokumentformate {#document-formats}

| Dateiformat | TXT | XMP |
| ----------- | --- | --- |
| EPUB | ✓ | - |
| HTML | ✓ | - |
| PS | - | ✓ |
| RTF | ✓ | - |
| TEXT | ✓ | - |
| XML | ✓ | - |

## Microsoft Office-Formate {#microsoft-office-formats}

| Dateiformat | GIF | JPEG | PNG | TEXT | Breite/Höhe |
| ----------- | --- | ---- | --- | ---- | ------------ |
| DOCX | ✓ | ✓ | ✓ | ✓ | ✓ |
| PPTX | ✓ | ✓ | ✓ | ✓ | ✓ |
| XLSX | ✓ | ✓ | ✓ | ✓ | ✓ |

## OpenDocument-Formate {#opendocument-formats}

| Dateiformat | GIF | JPEG | PNG | TEXT | Höhe |
| ----------- | --- | ---- | --- | ---- | ------ |
| ODF | ✓ | ✓ | ✓ | ✓ | ✓ |
| OFG | ✓ | ✓ | ✓ | ✓ | ✓ |
| ODM | ✓ | ✓ | ✓ | ✓ | ✓ |
| ODP | ✓ | ✓ | ✓ | ✓ | ✓ |
| ODS | ✓ | ✓ | ✓ | ✓ | ✓ |
| ODT | ✓ | ✓ | ✓ | ✓ | ✓ |

## Videoformate {#video-formats}

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

## Audioformate {#audio-formats}

Assets als Cloud-Dienst bietet XMP-Unterstützung für die folgenden Audioformate: AIF, ASF, M4A, MP3, WAV und WMA.

<!-- TBD: Some items from https://helpx.adobe.com/experience-manager/6-5/assets/using/assets-formats.html#SupportedinputvideoformatsforDynamicMediatranscoding may be applicable.

Bring more parity with https://helpx.adobe.com/experience-manager/6-5/assets/using/assets-formats.html#SupportedMIMEtypes.
https://helpx.adobe.com/experience-manager/6-5/assets/using/assets-formats.html#Supportedmultimediaformats
-->

>[!MORELIKETHIS]
>
>* [Asset-Verarbeitung mithilfe von Asset-Mikrodiensten](asset-microservices-overview.md)

