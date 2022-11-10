---
title: Verwalten Sie Ihre PDF-Dokumente in [!DNL Adobe Experience Manager].
description: Verwalten von PDF-Dokumenten in [!DNL Adobe Experience Manager] as a [!DNL Cloud Service].
feature: Asset Management
role: User,Admin
source-git-commit: 9a600fb744c7064274fb4d849a5e01de2b83f575
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 0%

---

# Verwalten von PDF-Dokumenten in Experience Manager Assets as a Cloud Service {#add-assets-to-experience-manager}

Experience Manager Assets ist nahtlos mit dem Document Cloud PDF Viewer integriert, mit dem Sie mehrere Seiten eines PDF-Dokuments in der Vorschau anzeigen können. Darüber hinaus können Sie erweiterte Viewer-Funktionen für das Document Cloud-PDF verwenden, wie z. B. Anmerkungen, Suchtext, das Navigieren im PDF-Dokument mithilfe von Lesezeichen und Miniaturansichten und vieles mehr unter demselben Dach. Mit Experience Manager Assets können Sie auch Dokumente in anderen unterstützten Formaten hochladen und als PDF-Vorschau anzeigen.

Document Cloud PDF Viewer bietet AEM Assets auf folgende Weise:
* [Unterstützung für PDF Document Cloud-Viewer-Komponenten](#pdf-doc-cloud)
* [Unterstützung für die Vorschau mehrerer Seiten und Anmerkungen für PDF-Asset](#multi-page)
* [Unterstützung der Vorschau mehrerer Seiten für Dokumente in anderen Formaten](#multi-format)

> Tipp
> Wenn Sie die Vorschau eines zuvor hochgeladenen PDF-Dokuments nicht für mehrere Seiten anzeigen können, wählen Sie die PDF aus und klicken Sie auf **![Neuverarbeitung](/help/assets/assets/Reprocess.svg) Assets erneut verarbeiten**.

## Unterstützung für PDF Document Cloud-Viewer-Komponenten {#pdf-doc-cloud}

Der native PDF Doc Cloud-Viewer verfügt in AEM Assets über die folgenden Komponenten:

* **PDF-Viewer mit Seitenminiaturansichten** Die Miniaturansicht ist eine kleine Vorschau der Seiten eines PDF-Dokuments. Mithilfe von Miniaturansichten können Sie direkt zur gewünschten Seite springen. Sie können über die ![thumbnail](/help/assets/assets/thumbnail.svg) im linken Bereich.

* **PDF-Viewer mit Lesezeichen** Lesezeichen ist ein direkter Link, der Sie zum Inhalt des Dokuments führt. Sie können über Lesezeichen des ausgewählten PDF-Dokuments auf ![Lesezeichen](/help/assets/assets/bookmark.svg) im linken Bereich.

* **Suchen in PDF** Sie können die Suche ![suchen](/help/assets/assets/Search.svg) , um den Text im PDF-Dokument nachzuschlagen.

* **Seitenaufwärts/Seitenrückwärts** Seite nach oben verwenden ![Page Up](/help/assets/assets/ArrowUp.svg) oder Seitenrücklauf ![Bild nach unten](/help/assets/assets/ArrowDown.svg) , um durch das Dokument zu scrollen.

* **Auszoomen/Einzoomen** Auszoomen verwenden ![Auszoomen](/help/assets/assets/ZoomOut.svg) oder Einzoomen ![Einzoomen](/help/assets/assets/ZoomIn.svg) , um das Dokument zu durchlaufen.

* **Seitengröße** Verwenden Sie die Breite oder Höhe, um das Dokument entsprechend der Bildschirmgröße anzupassen.

* **Dock/Undock-PDF** Mit dieser Option können Sie die Komponenten des nativen PDF-Viewers andocken oder abdocken.

## Unterstützung für die Vorschau mehrerer Seiten und Anmerkungen für PDF-Asset {#multi-page}

Mit Adobe Experience Manager Assets können Sie eine Vorschau des PDF-Dokuments anzeigen, das aus mehreren Seiten besteht. Gehen Sie wie folgt vor, um mehrere Seiten eines PDF-Dokuments in der Vorschau anzuzeigen:

1. Führen Sie die Schritte aus, um [Hochladen von Assets in AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/add-assets.html?lang=en).
1. Durchsuchen Sie das PDF-Dokument, das Sie hochladen und in der Vorschau anzeigen möchten.
1. Öffnen Sie das Dokument.
1. Der PDF-Dokument-Viewer wird standardmäßig geladen. Sie können auch die PDF-Ausgabedarstellung im Ausgabedarstellungsbereich auswählen.
1. Wählen Sie in der Dropdown-Liste Ausgabeformate die Option **Alle Ausgabeformate**.

Sie können auch [Anmerkungen](#pdf-annotations) zum PDF-Dokument in einer mehrseitigen Vorschau.

> HINWEIS
> Die maximale Größe eines Assets, das Sie in der Vorschau anzeigen können, beträgt bis zu 100 MB.

>[!VIDEO](https://video.tv.adobe.com/v/3409355)

<!--
![Multi-page Preview](/help/assets/assets/multi-page.png)
-->

**PDF-Anmerkungen{#pdf-annotations}**

Mit Experience Manager Assets können Sie einem PDF-Dokument Kommentare hinzufügen. Ein PDF-Dokument kann mehrere Anmerkungen enthalten.

Um ein PDF-Dokument zu kommentieren, führen Sie die folgenden Schritte aus:
1. Navigieren Sie zur Assets-Benutzeroberfläche zum PDF-Dokument, das Sie kommentieren möchten. Der native PDF-Viewer wird rechts mit der Vorschau des ausgewählten PDF-Dokuments geöffnet.
1. Klicken **Anmerken** aus dem oberen Menü.
Im Folgenden finden Sie die Anmerkungen, die auf ein PDF-Dokument angewendet werden können:

<table>
        <tr>
             <th> Anmerkung </th>
            <th> Beschreibung </th>
        </tr>
        <tr>
           <td> <img src="/help/assets/assets/Comment.svg"> Kommentar </td>
            <td> Wählen Sie Kommentar aus, um eine Beobachtung auszudrücken. </td>
        </tr>
        <tr>
            <td> <img src="/help/assets/assets/Text.svg"> Textbox </td>
            <td> Wählen Sie Textfeld aus, um den Text einzugeben. </td>
        </tr>
        <tr>
            <td> <img src="/help/assets/assets/Note.svg"> Fixierbare Hinweise </td>
            <td> Fügen Sie einen kleinen Text oder eine Erinnerung hinzu, den Sie einem bestimmten Bereich auf der PDF hinzufügen können. </td>
        </tr>
        <tr>
            <td> <img src="/help/assets/assets/Comment.svg"> Textmarkierung </td>
            <td> Wählen Sie den Text aus, der in verschiedenen Farben hervorgehoben werden soll. </td>
        </tr>
        <tr>
            <td> <img src="/help/assets/assets/TextUnderline.svg"> Textunterstrich </td>
            <td> Wählen Sie den Text aus, den Sie unterstreichen möchten. </td>
        </tr>
        <tr>
            <td> <img src="/help/assets/assets/TextStrikethrough.svg"> Durchstreichen </td>
            <td> Wählen Sie den Text aus, der durchkreuzt werden soll. </td>
        </tr>
        <tr>
            <td> <img src="/help/assets/assets/Draw.svg"> Zeichnen </td>
            <td> Fügen Sie eine visuelle Grafik in die PDF ein. </td>
        </tr>
        <tr>
            <td> <img src="/help/assets/assets/Erase.svg"> Zeichnen löschen </td>
             <td> Zeichnung entfernen oder rückgängig machen. </td>
        </tr>
    </table>

## Unterstützung der Vorschau mehrerer Seiten für Dokumente in anderen Formaten {#multi-format}

Zusätzlich zu den PDF-Dokumenten können Sie auch eine Vorschau mehrerer Seiten für Dokumente in anderen Formattypen anzeigen. Die unterstützten Dokumentformattypen sind TXT, RTF, DOC, DOCX, PPT, PPTX, XLS und XLSX. Experience Manager Assets konvertiert diese Dokumentenformate automatisch in ein PDF-Format und stellt sie für die Vorschau bereit.

![Mehrseitige Vorschau von Dokumenten in anderen Formaten](/help/assets/assets/multi-page-other-formats.png)

Für die mehrseitige Vorschau anderer unterstützter Dokumentformate führen Sie die folgenden Schritte aus:
1. Führen Sie die Schritte aus, um [Hochladen von Assets in AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/add-assets.html?lang=en).
1. Durchsuchen Sie das Dokument, das Sie hochladen und in der Vorschau anzeigen möchten.
1. Öffnen Sie das Dokument.
1. Wählen Sie im linken Bereich unter dem Abschnitt &quot;Statisch&quot;die Option PDF aus. Das rechte Bedienfeld zeigt die mehrseitige Vorschau eines Assets an. Wählen Sie im linken Bedienfeld die Option Miniaturansicht aus, um die Seite auszuwählen, die Sie in der Vorschau anzeigen möchten.

> HINWEIS
> * Die maximale Größe eines Assets, das Sie in der Vorschau anzeigen können, beträgt bis zu 100 MB.
> * Die maximale Größe von XLS- oder XLSX-Dateien für die Vorschau beträgt 20 MB.
> 

