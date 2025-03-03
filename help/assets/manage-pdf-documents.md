---
title: Verwalten Ihrer PDF-Dokumente in  [!DNL Adobe Experience Manager].
description: Verwalten von PDF-Dokumenten in  [!DNL Adobe Experience Manager]  as a  [!DNL Cloud Service].
feature: Asset Management
role: User, Admin
exl-id: 29660869-6902-4093-845b-cd629be59d4d
source-git-commit: 1652df9e774d8212b1bcc2898ca5d57e2a0d13bc
workflow-type: ht
source-wordcount: '853'
ht-degree: 100%

---

# Verwalten von PDF-Dokumenten in Experience Manager Assets as a Cloud Service {#add-assets-to-experience-manager}

| [Best Practices für die Suche](/help/assets/search-best-practices.md) | [Best Practices für Metadaten](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [Dynamic Media mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md) | [Entwicklerdokumentation zu AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

Experience Manager Assets ist nahtlos mit dem Document Cloud PDF Viewer integriert, mit dem Sie mehrere Seiten eines PDF-Dokuments in der Vorschau anzeigen können. Darüber hinaus können Sie erweiterte PDF-Viewer-Funktionen für Document Cloud verwenden, wie z. B. Anmerkungen, das Durchsuchen nach Texten, das Navigieren im PDF-Dokument mithilfe von Lesezeichen und Miniaturansichten und vieles mehr. Mit Experience Manager Assets können Sie auch Dokumente in anderen unterstützten Formaten hochladen und als PDF-Vorschau anzeigen.

Document Cloud PDF Viewer bietet AEM Assets folgende Vorteile:

* [Unterstützung von PDF Document Cloud Viewer-Komponenten](#pdf-doc-cloud)
* [Unterstützung der Vorschau mehrerer Seiten und Anmerkungen für PDF-Assets](#multi-page)
* [Unterstützung der Vorschau mehrerer Seiten von Dokumenten in anderen Formaten](#multi-format)

>[!TIP]
>
> Wenn Sie die Vorschau eines zuvor hochgeladenen PDF-Dokuments nicht für mehrere Seiten anzeigen können, wählen Sie die PDF-Datei aus und klicken Sie auf ![Erneut verarbeiten](/help/assets/assets/Reprocess.svg) **Assets erneut verarbeiten**.

## Unterstützung von PDF Document Cloud Viewer-Komponenten {#pdf-doc-cloud}

Der native PDF Doc Cloud-Viewer verfügt in AEM Assets über die folgenden Komponenten:

* **PDF-Viewer unter Verwendung von Seitenminiaturansichten** Die Miniaturansicht ist eine kleine Vorschau der Seiten eines PDF-Dokuments. Mithilfe von Miniaturansichten können Sie direkt zur gewünschten Seite springen. Sie können über die ![Miniaturansicht](/help/assets/assets/thumbnail.svg) im linken Bereich auf die Miniaturansicht des ausgewählten PDF-Dokuments zugreifen.

* **PDF-Viewer unter Verwendung von Lesezeichen** Lesezeichen ist ein direkter Link, der Sie zum Inhalt des Dokuments führt. Sie können über ![Lesezeichen](/help/assets/assets/bookmark.svg) im linken Bereich auf Lesezeichen des ausgewählten PDF-Dokuments aufzugreifen.

* **Suchen in PDF** Sie können die Suche verwenden, um Text im PDF-Dokument zu ![suchen](/help/assets/assets/Search.svg).

* **Seite nach oben / Seite nach unten** Verwenden Sie ![Seite nach oben](/help/assets/assets/ArrowUp.svg) oder ![Seite nach unten](/help/assets/assets/ArrowDown.svg), um durch das Dokument zu scrollen.

* **Auszoomen/Einzoomen** Verwenden Sie ![Auszoomen](/help/assets/assets/Zoom-out.svg) oder ![Einzoomen](/help/assets/assets/zoom-in.svg), um das Dokument zu verkleinern oder zu vergrößern.

* **Seitengröße** Verwenden Sie die Breite und Höhe, um das Dokument entsprechend der Bildschirmgröße anzupassen.

* **PDF andocken/abdocken** Mit dieser Option können Sie die Komponenten des nativen PDF-Viewers andocken oder wieder lösen.

## Unterstützung der Vorschau mehrerer Seiten und Anmerkungen für PDF-Assets {#multi-page}

Mit Adobe Experience Manager Assets können Sie eine Vorschau eines PDF-Dokuments anzeigen, das aus mehreren Seiten besteht. Gehen Sie wie folgt vor, um mehrere Seiten eines PDF-Dokuments in der Vorschau anzuzeigen:

1. Folgen Sie diesen Schritten, um [Assets in AEM hochzuladen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/add-assets.html?lang=de).
1. Durchsuchen Sie das PDF-Dokument, das Sie hochladen und in der Vorschau anzeigen möchten.
1. Öffnen Sie das Dokument.
1. Der PDF-Dokument-Viewer wird standardmäßig geladen. Sie können auch die PDF-Ausgabedarstellung im Ausgabedarstellungsbereich auswählen.
1. Wählen Sie in der Dropdown-Liste „Ausgabeformate“ die Option **Alle Ausgabeformate**.

Sie können auch [Anmerkungen](#pdf-annotations) zum PDF-Dokument in einer mehrseitigen Vorschau anwenden.

>[!NOTE]
>
> Die maximale Größe eines Assets, das Sie in der Vorschau anzeigen können, beträgt 100 MB.

>[!VIDEO](https://video.tv.adobe.com/v/3409355)

<!--
![Multi-page Preview](/help/assets/assets/multi-page.png)
-->

**PDF-Anmerkungen{#pdf-annotations}**

Mit Experience Manager Assets können Sie einem PDF-Dokument Kommentare hinzufügen. Ein PDF-Dokument kann mehrere Anmerkungen enthalten.

Um einem PDF-Dokument Anmerkungen hinzuzufügen, führen Sie die folgenden Schritte aus:

1. Gehen Sie zur Assets-Benutzeroberfläche und navigieren zum PDF-Dokument, dem Sie Anmerkungen hinzufügen möchten. Der native PDF-Viewer wird rechts mit der Vorschau des ausgewählten PDF-Dokuments geöffnet.
1. Klicken Sie oben im Menü auf **Anmerken**.
Im Folgenden finden Sie die Anmerkungen, die auf ein PDF-Dokument angewendet werden können:

<table>
        <tr>
             <th> Anmerkung </th>
            <th> Beschreibung </th>
        </tr>
        <tr>
           <td> <img src="/help/assets/assets/Comment.svg"> Kommentar </td>
            <td> Wählen Sie Kommentar aus, um eine Bemerkung hinzuzufügen. </td>
        </tr>
        <tr>
            <td> <img src="/help/assets/assets/Text.svg"> Textfeld </td>
            <td> Wählen Sie „Textfeld“ aus, um den Text einzugeben. </td>
        </tr>
        <tr>
            <td> <img src="/help/assets/assets/Note.svg"> Haftnotizen </td>
            <td> Fügen Sie einen kurzen Text oder eine Erinnerung einem bestimmten Bereich der PDF-Datei hinzu. </td>
        </tr>
        <tr>
            <td> <img src="/help/assets/assets/Comment.svg"> Textmarkierung </td>
            <td> Wählen Sie den Text aus, der in verschiedenen Farben hervorgehoben werden soll. </td>
        </tr>
        <tr>
            <td> <img src="/help/assets/assets/TextUnderline.svg"> Text unterstreichen </td>
            <td> Wählen Sie den Text aus, den Sie unterstreichen möchten. </td>
        </tr>
        <tr>
            <td> <img src="/help/assets/assets/TextStrikethrough.svg"> Durchstreichen </td>
            <td> Wählen Sie den Text aus, der durchgestrichen werden soll. </td>
        </tr>
        <tr>
            <td> <img src="/help/assets/assets/Draw.svg"> Zeichnen </td>
            <td> Fügen Sie der PDF-Datei eine Zeichnung hinzu. </td>
        </tr>
        <tr>
            <td> <img src="/help/assets/assets/Erase.svg"> Zeichnung löschen </td>
             <td> Entfernen Sie eine Zeichnung oder machen Sie sie rückgängig. </td>
        </tr>
    </table>

>[!NOTE]
>
>Die Anmerkungen, die Sie zum PDF-Dokument hinzufügen, sind im Vorschaumodus verfügbar. Die Anmerkungen werden jedoch nicht angezeigt, wenn Sie das PDF-Dokument herunterladen oder ausdrucken.

## Unterstützung der Vorschau mehrerer Seiten von Dokumenten in anderen Formaten {#multi-format}

Zusätzlich zu den PDF-Dokumenten können Sie auch eine Vorschau mehrerer Seiten von Dokumenten in anderen Formattypen anzeigen. Die unterstützten Dokumentformattypen sind TXT, RTF, DOC, DOCX, PPT, PPTX, XLS und XLSX. Experience Manager Assets konvertiert diese Dokumentenformate automatisch in ein PDF-Format und stellt sie für die Vorschau bereit.

![Mehrseitige Vorschau von Dokumenten in anderen Formaten](/help/assets/assets/multi-page-other-formats.png)

Für die mehrseitige Vorschau anderer unterstützter Dokumentenformate führen Sie die folgenden Schritte aus:

1. Folgen Sie diesen Schritten, um [Assets in AEM hochzuladen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/add-assets.html?lang=de).
1. Durchsuchen Sie das Dokument, das Sie hochladen und in der Vorschau anzeigen möchten.
1. Öffnen Sie das Dokument.
1. Wählen Sie im linken Bereich unter dem Abschnitt „Statisch“ die Option PDF aus. Das rechte Bedienfeld zeigt die mehrseitige Vorschau eines Assets an. Wählen Sie im linken Bedienfeld die Option Miniaturansicht aus, um die Seite auszuwählen, die Sie in der Vorschau anzeigen möchten.

>[!NOTE]
>
> * Die maximale Größe eines Assets, das Sie in der Vorschau anzeigen können, beträgt 100 MB.
> * Die maximale Größe von XLS- oder XLSX-Dateien für die Vorschau beträgt 20 MB.

**Siehe auch**

* [Assets übersetzen](translate-assets.md)
* [Assets-HTTP-API](mac-api-assets.md)
* [Von AEM Assets unterstützte Dateiformate](file-format-support.md)
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
