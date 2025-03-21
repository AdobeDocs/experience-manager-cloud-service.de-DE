---
title: Unterstützte Dateiformate
description: Unterstützte Dateiformate für die verschiedenen Anwendungsfälle von  [!DNL Assets view]
role: User, Leader, Admin, Architect, Developer
contentOwner: AG
exl-id: 5936ace2-318e-4888-9ad4-23e6f6bfb857
feature: Asset Management, Publishing, Collaboration, Asset Processing
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 95%

---

# Unterstützte Dateiformate in [!DNL Assets view] {#file-format-support}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime und Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b>AEM Assets-Integration mit Edge Delivery Services</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>Erweiterbarkeit der Benutzeroberfläche</b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b>Aktivieren von Dynamic Media Prime und Ultimate</b></a>
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b>Best Practices für die Suche</b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b>Best Practices für Metadaten</b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b>Content Hub</b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b>Dynamic Media mit OpenAPI-Funktionen</b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b>Entwicklerdokumentation zu AEM Assets</b></a>
        </td>
    </tr>
</table>

[!DNL Assets view] unterstützt eine breite Palette von Dateiformaten, und jede Funktionalität bietet unterschiedliche Unterstützung für verschiedene Dateitypen.

* ![Symbol für Bilddateityp](assets/image-icon.svg) Bilder: JPG, PNG, GIF, TIFF und andere
* ![Symbol für Creative Cloud-Typ](assets/creative-cloud-files.svg) Creative Cloud-Dateien: PSD, PSB, AI und INDD
* ![Symbol für Kameratyp](assets/camera-icon.svg) Camera Raw-Dateien: CR2/CR3, NEF, SRW/SRF und andere
* ![document file type icon](assets/document-icon.svg) Dokument-Typen: DOCX, PDF, PPTX und XLSX
* ![video file type icon](assets/video-icon.svg) Video-Typen: MP4

[!DNL Assets view] unterstützt alle binären Dateiformate mit grundlegenden Services wie Speichern, Hochladen, Kopieren, Verschieben, Löschen und Hinzufügen von Metadaten.

[!DNL Assets view] unterstützt auch Camera Raw-Dateien von einer Vielzahl führender Kamerahersteller, darunter Canon (CR2/CR3), Nikon (NEF), Sony (SRW/SRF), Fujifilm (RAF), Olympus (ORF) und andere, unterstützt durch Adobe Camera Raw.

Die verschiedenen Dateitypen werden, wie unten beschrieben, in unterschiedlichem Maße von den Anwendungsfällen und Funktionen unterstützt. Die Legende gibt den Grad der Unterstützung an.

| Unterstützungsebene | Beschreibung |
|-------------------|-------------------------|
| ✓ | Unterstützt |
| ✓ ‡ | Bedingt unterstützt |
| − | Nicht zutreffend |

## Hinzufügen, Hochladen und Anzeigen von Assets {#support-to-upload-view}

<!-- TBD: For AEM, AI files require the PDF option to be selected when saving the AI file.
-->

| Asset-Typ | [Durchsuchen](/help/assets/navigate-assets-view.md) | Kopieren | [Hochladen](/help/assets/add-delete-assets-view.md) | Erstellen | [Löschen](/help/assets/add-delete-assets-view.md#delete-assets) | Details | Bild-Zoom | [Kürzlich angesehen](/help/assets/navigate-assets-view.md) |
|-------------------|----------|----------|----------|----------|----------|-------------------|------------|-----------------|
| Rasterbilder | ✓ | ✓ | ✓ | − | ✓ | ✓ | ✓ | ✓ |
| Raw-Dateien | ✓ | ✓ | ✓ | − | ✓ | ✓ | ✓ | ✓ |
| Ordner | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | − | − |
| MP4-Videos | ✓ | ✓ | ✓ | − | ✓ | ✓ ‡ | − | ✓ |
| PDF | ✓ | ✓ | ✓ | − | ✓ | ✓ | − | ✓ |
| PSD, PSB, AI und INDD | ✓ | ✓ | ✓ | − | ✓ | ✓ ‡ | − | ✓ |
| Andere Binärdateien | ✓ | ✓ | ✓ | − | ✓ | ✓ | − | ✓ |

<!-- Hiding CC Libraries (considered beta) as per PM feedback.
| CC Libraries  | &#10003; | &minus;  | &#10003; | &#10003; | &#10003; | &#10003; | &minus;    | &minus;         |
-->

## Suchen, Verwenden und Bearbeiten von Assets {#support-to-search-use-edit}

| Asset-Typ | [Download](/help/assets/manage-organize-assets-view.md#download) | Drag-and-Drop | [Bildeditor](/help/assets/edit-images-assets-view.md) | [Suchen](/help/assets/search-assets-view.md) | [Smart-Tags](/help/assets/metadata-assets-view.md#tags) | [Umbenennen](/help/assets/manage-organize-assets-view.md) | [Versionen](/help/assets/manage-organize-assets-view.md#versions-of-assets) |
|---------------|----------|---------------|--------------|----------|------------|----------|----------|
| Rasterbilder | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| Raw-Dateien | ✓ | ✓ | − | ✓ | ✓ | ✓ | ✓ | ✓ |
| Ordner | ✓ | ✓ | − | ✓ | − | ✓ | ✓ |
| Videos | ✓ | ✓ | − | ✓ | ✓ | ✓ | ✓ |
| CC-Bibliotheken | − | − | − | − | − | ✓ | ✓ |
| PDF | ✓ | ✓ | − | ✓ | ✓ | ✓ | ✓ |
| PSD und PSB | ✓ | ✓ | − | ✓ | ✓ | ✓ | ✓ |
| AI und INDD | ✓ | ✓ | − | ✓ | − | ✓ | ✓ |
| Andere Binärdateien | ✓ | ✓ | − | ✓ | − | ✓ | ✓ |


## Überprüfen von Assets und Zusammenarbeit {#support-to-review-collaborate}

| Asset-Typ | Anmerken | Kommentar | Erstellen von Aufgaben und Überprüfen |
|---------------|----------|----------|-------------------------|
| Rasterbilder | ✓ | ✓ | ✓ |
| Raw-Dateien | ✓ | ✓ | ✓ |
| Ordner | − | − | − |
| Videos | − | ✓ | ✓ |
| CC-Bibliotheken | − | − | − |
| PDF | − | ✓ | ✓ |
| PSD, PSB, AI und INDD | − | ✓ | ✓ |
| Andere Binärdateien | − | ✓ | ✓ |
| DOC | − | ✓ | ✓ |
| DOCX | − | ✓ | ✓ |
| PPT | − | ✓ | ✓ |
| PPTX | − | ✓ | ✓ |
| XLS | − | ✓ | ✓ |
| XLSX | − | ✓ | ✓ |
| TXT | − | ✓ | ✓ |
| RTF | − | ✓ | ✓ |

## Sonstige Asset-Management-Aufgaben {#support-to-manage-assets}

| Asset-Typ | [Metadaten](/help/assets/metadata-assets-view.md) | [Ausgabedarstellungen](/help/assets/add-delete-assets-view.md#renditions) | [Papierkorb](/help/assets/add-delete-assets-view.md#delete-assets) | Kopieren | Verschieben |
|---------------|-------------------|------------|----------|----------|----------|
| Rasterbilder | ✓ | ✓ | ✓ | ✓ | ✓ |
| Raw-Dateien | ✓ | ✓ | ✓ | ✓ | ✓ |
| Ordner | ✓ | − | ✓ | ✓ | ✓ |
| Videos | ✓ | − | ✓ | ✓ | ✓ |
| CC-Bibliotheken | ✓ | − | − | − | − |
| PDF | ✓ | − | ✓ | ✓ | ✓ |
| AI und INDD | ✓ | − | ✓ | ✓ | ✓ |
| PSD und PSB | ✓ | ✓ | ✓ | ✓ | ✓ |
| Andere Binärdateien | ✓ | − | ✓ | ✓ | ✓ |

Benutzer von [!DNL Adobe Asset Link] können Dateien aus den unterstützten Desktop-Programmen von [!DNL Adobe Creative Cloud] in das [!DNL Assets view]-Repository hochladen und einchecken (eine neue Version hochladen).

<!-- TBD: Saving the template table separately for later use.
| Asset type    | Features |
|---------------|----------|
| Raster images |          |
| Folders       |          |
| Videos        |          |
| CC Libraries  |          |
| PDF files     |          |
| PSD, PSB           |          |
| AI            |          |
| INDD          |          |

>[!MORELIKETHIS]
>
>* []()
-->

## Nächste Schritte {#next-steps}

* Geben Sie Produkt-Feedback über die Option [!UICONTROL Feedback] in der Benutzeroberfläche der Assets-Ansicht

* Geben Sie Feedback zur Dokumentation durch ![Bearbeiten der Seite](assets/do-not-localize/edit-page.png) über die Option [!UICONTROL Diese Seite bearbeiten] oder durch ![Erstellen eines GitHub-Themas](assets/do-not-localize/github-issue.png) über die Option [!UICONTROL Problem protokollieren] in der rechten Seitenleiste

* Kontaktieren Sie die [Kundenunterstützung](https://experienceleague.adobe.com/de?support-solution=General#support)
