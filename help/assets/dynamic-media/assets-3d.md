---
title: Arbeiten mit 3D-Assets in Dynamic Media
description: Erfahren Sie, wie Sie in Dynamic Media mit 3D-Assets arbeiten.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS and Experience Manager as a Cloud Service
topic-tags: introduction
content-type: reference
feature: 3D Assets
role: User
exl-id: 82084ba7-1302-4cbd-8626-d77b3aaa4ed1
source-git-commit: c82f84fe99d8a196adebe504fef78ed8f0b747a9
workflow-type: tm+mt
source-wordcount: '2298'
ht-degree: 98%

---

# Arbeiten mit 3D-Assets in Dynamic Media {#working-with-three-d-assets-dm}

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

Mit Dynamic Media können Sie 3D-Assets hochladen, verwalten, anzeigen und als eindrucksvolle Erlebnisse bereitstellen.

* Veröffentlichen von 3D-Assets mit einem Klick (mithilfe von **[!UICONTROL Quick Publish]** in der Symbolleiste) zum Generieren einer URL.
* Optimierte Unterstützung für die Anzeige von 3D-Assets mit der hochwertigen, interaktiven Viewer-Vorgabe „Dimensional“, bereitgestellt von Adobe Dimension.
* Mit der WCM-Komponente „3D Media“ können Sie auf einfache Weise 3D-Assets zu Ihren [!DNL Adobe Experience Manager Sites]-Seiten hinzufügen.

Für die Verwendung von 3D-Assets in Dynamic Media ist keine zusätzliche Installation erforderlich.

![Schuh in 3D](/help/assets/dynamic-media/assets/3d-dimensional-viewer-quickpublish-url-embed2a.png)

<!-- See also [Dynamic Media 3D Release Notes](/help/release-notes/aem3d-release-notes.md). -->

## Unterstützte 3D-Formate in Dynamic Media {#supported-three-d-file-formats-in-dm}

Dynamic Media unterstützt die folgenden 3D-Dateiformate.

Siehe auch [Unterstützte 3D-Formate in Experience Manager Assets](/help/assets/file-format-support.md#support-3d-formats)

| 3D-Dateierweiterung | Dateiformat | MIME-Typ | Anmerkungen |
|---|---|---|---|
| GLB | Binäre GL-Übertragung | model/gltf-binary | Umfasst die Materialien und Texturen als ein Asset. |
| OBJ | WaveFront 3D-Objektdatei | application/x-tgif |  |
| STL | Stereolithografie | application/vnd.ms-pki.stl |  |
| USDZ | Universelles Scene Description-Zip-Archiv | model/vnd.usdz+zip | *Nur Erfassung unterstützt, keine Anzeige oder Interaktion möglich.* USDZ ist ein proprietäres 3D-Format, das von Safari oder iOS nativ angezeigt werden kann. |

Die 3D-Medien-WCM-Komponente und die 3D-Vorschau auf der Detailseite eines Assets sind nicht mit der neuesten Version von Chrome (97.x) kompatibel. Verwenden Sie stattdessen Firefox oder Safari oder eine frühere Version von Chrome (96.x), um mit 3D-Assets zu arbeiten.

## Schnellstart: Arbeiten mit 3D-Assets in Dynamic Media {#quick-start-three-d}

Die folgende schrittweise Workflow-Beschreibung soll Ihnen dabei helfen, 3D-Assets in Dynamic Media einzurichten und schnell auszuführen.

Stellen Sie vor der Arbeit mit 3D-Assets in Dynamic Media sicher, dass der [!DNL Experience Manager]-Administrator Dynamic Media Cloud Services bereits aktiviert und konfiguriert hat.

Siehe [Konfigurieren von Dynamic Media Cloud Services](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services).

1. **Hochladen von 3D-Assets**

   * [Hochladen von 3D-Assets zur Verwendung in Dynamic Media](/help/assets/add-assets.md#upload-assets)
   * [Unterstützte 3D-Dateiformate zum Hochladen in Dynamic Media](#supported-three-d-file-formats-in-dm)

1. **Verwalten von 3D-Assets**

   * Organisieren und Suchen von 3D-Assets

      * [Organisieren digitaler Assets](/help/assets/organize-assets.md)
      * [Suchen von 3D-Assets](/help/assets/search-assets.md)

   * Anzeigen von 3D-Assets

      * [Anzeigen von und Interagieren mit 3D-Assets](#viewing-three-d-assets)
      * [Verwalten der Dimensional-Viewer-Vorgabe](/help/assets/dynamic-media/managing-viewer-presets.md)

   * Arbeiten mit 3D-Asset-Metadaten

      * [Verwalten von Metadaten für digitale Assets](/help/assets/manage-digital-assets.md#editing-properties)
      * [Metadatenschemata](/help/assets/metadata-schemas.md)

1. **Veröffentlichen von 3D-Assets**

   * [Veröffentlichen von statischen Dynamic Media-3D-Assets](#publishing-three-d-assets)
   * [Alternative Methoden zum Veröffentlichen von Dynamic Media-3D-Assets mit dem Dimensional-Viewer](#alternate-publish-methods)

## Wissenswertes über das Anzeigen von und Interagieren mit 3D-Assets {#viewing-three-d-assets}

In diesem Abschnitt wird beschrieben, wie Sie 3D-Assets auf zwei verschiedene Arten anzeigen und mit ihnen arbeiten können: auf der Seite „Asset-Details“ und in der 3D-Medien-Komponente in Sites.

Der interaktive 3D-Viewer bietet unter anderem eine Reihe interaktiver Kamera-Steuerelemente, mit denen Sie die Kamera um das 3D-Asset drehen sowie Zoom- und Schwenkvorgänge durchführen können.

Wie viel Zeit zum Öffnen eines 3D-Assets auf der Seite „Asset-Details“ benötigt wird, hängt von verschiedenen Faktoren ab. den folgenden Faktoren abhängt:

* Bandbreite zum Server.
* Latenzen zum Server.
* Komplexität des Bildes.

Wenn Sie die Kamera interaktiv bearbeiten, muss darüber hinaus die Kapazität des Client-Computers – etwa Workstation, Notebook oder Mobilgerät mit Touch-Funktion – berücksichtigt werden. Ein relativ leistungsfähiges System mit guten Grafikfähigkeiten unterstützt eine weichere, angenehmere interaktive 3D-Anzeige.

>[!TIP]
>
>Sie können die Viewer-Vorgabe „Dimensional“ im Viewer-Vorgabeneditor öffnen, um die Navigation in einem 3D-Asset zu üben, ohne 3D-Dateien hochzuladen. Die Viewer-Vorgabe „Dimensional“ verfügt über ein integriertes 3D-Asset, mit dem Sie interagieren können.
>
>Siehe [Verwalten von Viewer-Vorgaben](/help/assets/dynamic-media/managing-viewer-presets.md).

## Ansicht von und Interaktion mit einem 3D-Asset auf der Seite mit den Asset-Details {#viewing-three-d-assets-from-asset-details-page}

Siehe auch [Vorschau von Assets über die Software-Schnittstelle](/help/assets/dynamic-media/previewing-assets.md).

**Gehen Sie wie folgt vor, um ein 3D-Asset auf der Seite „Asset-Details“ anzuzeigen und damit zu interagieren:**

1. Stellen Sie sicher, dass Sie 3D-Assets in [!DNL Experience Manager] hochgeladen haben.

   Siehe [Hochladen von 3D-Assets zur Verwendung in Dynamic Media](/help/assets/add-assets.md#upload-assets).

1. Von [!DNL Experience Manager] auf der **[!UICONTROL Navigationsseite]** aus wählen Sie die Option **[!UICONTROL Assets > Dateien]**.
1. Klicken Sie in der rechten oberen Ecke der Seite in der Dropdown-Liste **[!UICONTROL Ansicht]** auf **[!UICONTROL Kartenansicht]**.
1. Navigieren Sie zu einem 3D-Asset, das Sie anzeigen möchten.
1. Um das Asset auf der Detailseite zu öffnen, wählen Sie die Karte des 3D-Assets.
1. Führen Sie auf der Seite mit den Details für das 3D-Asset einen der folgenden Schritte aus:

   | Anzeigen | Beschreibung | Mausaktion | Touchscreen-Aktion |
   | --- | --- | --- | --- |
   | **Kamera drehen** | Drehen Sie die Ansicht um die 3D-Szene und Objekte. | Klicken und ziehen Sie mit der linken Maustaste. | Drücken und ziehen Sie mit einem Finger. |
   | **Kamera schwenken** | Schwenken Sie nach links, rechts, oben oder unten. | Klicken und ziehen Sie mit der rechten Maustaste. | Drücken und ziehen Sie mit zwei Fingern. |
   | **Kamera zoomen** | Zoomen Sie mit der Kamera in Bereiche der 3D-Szene bzw. aus diesen Bereichen heraus. | Scrollen Sie mit dem Mausrad. | Ziehen Sie per Pinch mit zwei Fingern. |
   | **Kamera neu zentrieren** | Zentrieren Sie die Kamera neu auf einen Punkt an einem Objekt in der 3D-Szene. | Doppelklicken. | Doppelt auswählen. |
   | **Zurücksetzen** | Wählen Sie in der unteren rechten Ecke der Seite das Symbol „Zurücksetzen“, um den Zielpunkt der Ansicht wieder in die Mitte des 3D-Assets zu setzen. Durch das Zurücksetzen wird die Kamera auch näher heran oder weiter weg bewegt, um das Asset in seiner Gesamtheit und in einer angemessenen Betrachtungsgröße zu zeigen. |   |   |
   | **Vollbildmodus** | Um in den Vollbildmodus zu gelangen, wählen Sie in der unteren rechten Ecke der Seite das Symbol „Vollbild“. |   |   |

1. Wählen Sie in der oberen rechten Ecke der Seite **[!UICONTROL Schließen]**, um zur Seite „Assets“ zurückzukehren.

## Anzeigen von und Interagieren mit einem 3D-Asset innerhalb einer 3D-Medienkomponente {#interacting-with-asset-inside-three-d-media-component}

Wenn sich eine Web-Seite im **[!UICONTROL Bearbeitungsmodus]** befindet, ist keine Interaktion mit einem 3D-Asset möglich. Um das Asset interaktiv zu gestalten, können Sie die Web-Seite im Seiteneditor mithilfe der **[!UICONTROL Vorschaufunktion]** mit vollem Zugriff auf die Funktionen der 3D-Medien-Komponente anzeigen.

>[!IMPORTANT]
>
>Sie können diese Aufgabe erst ausführen, nachdem Sie einer Web-Seite eine 3D-Medien-Komponente hinzugefügt und der Komponente ein 3D-Asset zugewiesen haben. Siehe [Hinzufügen der 3D-Medienkomponente zu einer Web-Seite](#adding-the-three-d-media-component-to-a-web-page) und [Zuweisen eines 3D-Assets zu einer 3D-Medienkomponente](#assigning-a-three-d-asset-to-the-component).

Siehe auch [Vorschau von Assets über die Software-Schnittstelle](/help/assets/dynamic-media/previewing-assets.md).

**Anzeigen von und Interagieren mit einem 3D-Asset innerhalb einer 3D-Medien-Komponente:**

1. Führen Sie während sich die Web-Seite im **[!UICONTROL Bearbeitungsmodus]** befindet, einen der folgenden Schritte aus:

   * Klicken Sie rechts oben auf der Seite auf **[!UICONTROL Vorschau]**, um in den **[!UICONTROL Vorschaumodus]** zu wechseln.
   * Löschen Sie `/editor.html` aus der Seiten-URL im Browser.

   ![3D-Asset, das innerhalb der 3D-Medien-Komponente angezeigt wird](/help/assets/dynamic-media/assets/3d-asset-in-3d-mediaa.png)
Ein vollständig interaktives 3D-Asset, wie im **[!UICONTROL Vorschaumodus]** angezeigt.

1. Führen Sie im **[!UICONTROL Vorschaumodus]** einen der folgenden Schritte aus:

   | Anzeigen | Beschreibung | Mausaktion | Touchscreen-Aktion |
   | --- | --- | --- | --- |
   | **Kamera drehen** | Drehen Sie die Ansicht um die 3D-Szene und Objekte. | Klicken und ziehen Sie mit der linken Maustaste. | Drücken und ziehen Sie mit einem Finger. |
   | **Kamera schwenken** | Schwenken Sie nach links, rechts, oben oder unten. | Klicken und ziehen Sie mit der rechten Maustaste. | Drücken und ziehen Sie mit zwei Fingern. |
   | **Kamera zoomen** | Zoomen Sie mit der Kamera in Bereiche der 3D-Szene bzw. aus diesen Bereichen heraus. | Scrollen Sie mit dem Mausrad. | Ziehen Sie per Pinch mit zwei Fingern. |
   | **Kamera neu zentrieren** | Zentrieren Sie die Kamera neu auf einen Punkt an einem Objekt in der 3D-Szene. | Doppelklicken. | Doppelt auswählen. |
   | **Zurücksetzen** | Wählen Sie in der unteren rechten Ecke der Seite das Symbol „Zurücksetzen“, um den Zielpunkt der Ansicht wieder in die Mitte des 3D-Assets zu setzen. Durch das Zurücksetzen wird die Kamera auch näher heran oder weiter weg bewegt, um das Asset in seiner Gesamtheit und in einer angemessenen Betrachtungsgröße zu zeigen. |   |   |
   | **Vollbildmodus** | Um in den Vollbildmodus zu gelangen, wählen Sie in der unteren rechten Ecke der Seite das Symbol „Vollbild“. |   |   |

## Wissenswertes über die Arbeit mit der 3D-Medien-Komponente {#working-with-three-d-media-component}

Dynamic Media enthält eine Dynamic Media 3D-Medien-Komponente, die Sie in [!DNL Experience Manager Sites] verwenden können, um die interaktive Anzeige von 3D-Modellen auf Ihren Web-Seiten zu ermöglichen.

* [Hinzufügen der 3D-Medien-Komponente zur Seitenvorlage](#adding-three-d-media-component-to-page-template)
* [Hinzufügen der 3D-Medien-Komponente zu einer Web-Seite](#adding-the-three-d-media-component-to-a-web-page)
   * [Optional – Konfigurieren der 3D-Medien-Komponente](#configuring-the-three-d-component)
* [Zuweisen eines 3D-Assets zur 3D-Medienkomponente](#assigning-a-three-d-asset-to-the-component)

## Hinzufügen der 3D-Medien-Komponente zur Seitenvorlage {#adding-three-d-media-component-to-page-template}

1. Öffnen Sie **[!UICONTROL Tools]** > **[!UICONTROL Allgemein]** > **[!UICONTROL Vorlagen]**.
1. Navigieren Sie zu der Seitenvorlage, in der Sie die 3D-Komponente aktivieren möchten, und wählen Sie sie aus.
1. Um die Vorlage zu öffnen, klicken Sie auf **[!UICONTROL Bearbeiten]**.
1. Wählen Sie oben rechts auf der Seite im Dropdown-Menü dem Modus **[!UICONTROL Struktur]**, falls dieser noch nicht aktiv ist.

   ![3d-media-component-structure](/help/assets/dynamic-media/assets/3d-media-component-structurea.png)

1. Um einen leeren Bereich auszuwählen und die zugehörige Symbolleiste zu öffnen, wählen Sie den leeren Bereich in der Region **[!UICONTROL Layout-Container]** aus.
1. Klicken Sie in der Symbolleiste auf das Symbol **[!UICONTROL Richtlinie]**, um den **[!UICONTROL Richtlinien-Editor]** zu öffnen.
1. Scrollen Sie im Abschnitt **[!UICONTROL Eigenschaften]** auf der Registerkarte **[!UICONTROL Zulässige Komponenten]** zu **[!UICONTROL Dynamic Media]**, erweitern Sie dann die Liste und aktivieren Sie die Option **[!UICONTROL 3D-Medien]**.
1. Tippen Sie auf **[!UICONTROL Fertig]**, um die Änderungen zu speichern und den **[!UICONTROL Richtlinien-Editor]** zu schließen.

   Sie können jetzt die Dynamic Media-3D-Medien-Komponente auf allen Seiten platzieren, die diese Vorlage verwenden.

## Hinzufügen der 3D-Medien-Komponente zu einer Web-Seite {#adding-the-three-d-media-component-to-a-web-page}

Wenn Sie [!DNL Experience Manager] als Web-Content-Management-System verwenden, können Sie mit der Komponente „3D Media“ 3D-Assets zu Ihren Web-Seiten hinzufügen.

Siehe [Hinzufügen von Dynamic Media Assets zu Seiten](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md).

1. Öffnen Sie [!DNL Experience Manager Sites] und wählen Sie die Web-Seite aus, der Sie die Dynamic Media 3D-Medienkomponente hinzufügen möchten.
1. Um die Seite im Seiteneditor zu öffnen, klicken Sie auf das Symbol **[!UICONTROL Bearbeiten]** (Stift). Stellen Sie sicher, dass rechts oben auf der Seite der **[!UICONTROL Bearbeitungsmodus]** ausgewählt ist.

   ![3d-media-component-add](/help/assets/dynamic-media/assets/3d-media-component-edita.png)

1. Wählen Sie in der Symbolleiste das Symbol für das Seitenbedienfeld, um die Anzeige des Bedienfelds zu aktivieren bzw. zu aktivieren.

1. Wählen Sie im Seitenbedienfeld das Plus-Symbol, um die **[!UICONTROL Komponentenliste]** zu öffnen.

   ![3d-media-component-drag-drop](/help/assets/dynamic-media/assets/3d-assets-filtera.png)

1. Ziehen Sie die Komponente **[!UICONTROL 3D-Medien]** aus der Liste **[!UICONTROL Komponenten]** an die Stelle auf der Seite, an der der 3D-Viewer angezeigt werden soll.

Sie können der Komponente jetzt ein 3D-Asset zuweisen.

Siehe [Zuweisen eines 3D-Assets zur 3D-Medienkomponente](#assigning-a-three-d-asset-to-the-component)

### Optional – Konfigurieren der 3D-Medien-Komponente {#configuring-the-three-d-component}

1. Wählen Sie im [!DNL Experience Manager Sites]-Seiteneditor die Komponente **[!UICONTROL 3D-Medien-Viewer]** aus, die Sie zuvor der Seite hinzugefügt haben.
1. Um das Dialogfeld für die Komponentenkonfiguration zu öffnen, klicken Sie auf das Symbol **[!UICONTROL Konfiguration]** (Schraubenschlüssel).

   ![3d-media-component-config](/help/assets/dynamic-media/assets/3d-media-component-configa.png)

1. Wählen Sie im Dialogfeld „3D-Medien“ aus der Dropdown-Liste „Viewer-Vorgabe“ die Option **[!UICONTROL Dimensional]** aus, um der Komponente die Viewer-Vorgabe „Dimensional“ zuzuweisen.

   ![3d-media-component-edit-config](/help/assets/dynamic-media/assets/3d-media-component-edit-configa.png)

1. Setzen Sie in der oberen rechten Ecke das Häkchen, um Ihre Änderungen zu speichern.

## Zuweisen eines 3D-Assets zur 3D-Medienkomponente {#assigning-a-three-d-asset-to-the-component}

Nachdem Sie einer Web-Seite eine 3D-Medien-Komponente hinzugefügt haben, können Sie ihr ein 3D-Asset zuweisen.

Siehe [Hinzufügen der 3D-Medien-Komponente zu einer Web-Seite](#adding-the-three-d-media-component-to-a-web-page).

1. Klicken Sie im [!DNL Experience Manager Sites]-Seiten-Editor auf das Symbol **[!UICONTROL Assets]**, um die **[!UICONTROL Assets]** im Seitenbedienfeld zu öffnen.
1. Wählen Sie in der Dropdown-Liste **[!UICONTROL 3D]** aus, um nur 3D-Asset-Dateitypen anzuzeigen.
1. Suchen Sie im Seitenbedienfeld nach dem 3D-Asset, das Sie auf der entsprechenden Seite anzeigen möchten, oder scrollen Sie zu diesem.
1. Ziehen Sie das 3D-Asset aus dem Seitenbedienfeld „Assets“ und legen Sie es auf der Komponente **[!UICONTROL 3D-Medien]** ab, die Sie der Seite zuvor hinzugefügt haben.

   ![Zuweisen eines 3D-Assets zur 3D-Medien-Komponente](/help/assets/dynamic-media/assets/3d-asset-adda.png)

>[!NOTE]
>
>Während sich eine Web-Seite in [!DNL Experience Manager Sites] im Modus **[!UICONTROL Bearbeiten]** befindet, zeigt die 3D-Medien-Komponente das 3D-Asset an, jedoch ist keine Interaktion mit dem Asset möglich. Um das Asset interaktiv zu gestalten, können Sie die Web-Seite im Seiteneditor mithilfe der **[!UICONTROL Vorschaufunktion]** mit vollem Zugriff auf die Funktionen der 3D-Medien-Komponente anzeigen.

## Veröffentlichen von statischen Dynamic Media-3D-Assets {#publishing-three-d-assets}

Dynamic Media akzeptiert eine Vielzahl von 3D-Dateiformaten, die in Dynamic Media als *statische Inhalte* unterstützt werden. Statischer Inhalt bedeutet, dass Sie 3D-Assets hochladen und veröffentlichen können, aber es gibt keine Unterstützung für die *dynamische* Bildbearbeitung oder Bildnachbearbeitung, die mit dem 3D-Asset verbunden ist. Der Grund dafür ist, dass der Dynamic Media-Bildbearbeitungs-Server keine 3D-Formate erkennt. Nach der Veröffentlichung eines 3D-Assets in Dynamic Media haben Sie daher eine sofortige URL, die Sie kopieren können. Die URL für das 3D-Asset entspricht der üblichen URL-Struktur für Dynamic Media. Im Gegensatz zu herkömmlichen Bild-Assets in Dynamic Media können Sie jedoch keine Parameter in der URL des Assets bearbeiten.

Siehe auch [Abrufen einer URL für ein statisches Asset](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md#obtaining-a-url-for-a-static-asset).

In der **[!UICONTROL Kartenansicht]** wird ein kleines Globussymbol direkt unter dem Namen eines Assets und links von Datum und Uhrzeit angezeigt, um anzuzeigen, dass es veröffentlicht wurde. In der **[!UICONTROL Listenansicht]** gibt eine Spalte **[!UICONTROL Veröffentlicht]** an, welche Assets veröffentlicht sind.

Wenn Sie [!DNL Experience Manager] als WCM verwenden, verwenden Sie diese Veröffentlichungsmethode, um die Dynamic Media 3D-Assets direkt in Ihre Web-Seite einzufügen.

Siehe auch [Veröffentlichen von Dynamic Media-Assets](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

Siehe auch [Veröffentlichen von Seiten](/help/sites-cloud/authoring/sites-console/publishing-pages.md).

**Veröffentlichen von statischen Dynamic Media-3D-Assets:**

1. Öffnen Sie ein 3D-Asset (Dateiformat GLB, OBJ oder STL).
1. Wählen Sie auf der Seite „Details“ in der Symbolleiste **[!UICONTROL Quick Publish]**.

   ![3d-asset-quick-publish](/help/assets/dynamic-media/assets/3d-asset-quick-publisha.png)

1. Wählen Sie **[!UICONTROL Schließen]** aus, um das Dialogfeld zu verlassen und zur Seite „Asset-Details“ zurückzukehren.
1. Wählen Sie in der Dropdown-Liste links neben dem Dateinamen des 3D-Assets die Option **[!UICONTROL Ausgabedarstellungen]** aus.

   ![3d-asset-renditions](/help/assets/dynamic-media/assets/3d-asset-renditionsa.png)

1. Wählen Sie **[!UICONTROL original]** aus. Wenn ein 3D-Asset veröffentlicht (oder „aktiviert“) wird, wird die Schaltfläche **[!UICONTROL URL]** unten links auf der Seite angezeigt, wenn die folgenden Bedingungen für 3D-Assets erfüllt sind:
   * Das 3D-Asset ist ein unterstütztes Format (GLB, OBJ, STL und USDZ).
   * Das 3D-Asset wurde in das Dynamic Media Image Production System (IPS) erfasst.
   * Das 3D-Asset ist veröffentlicht.

   ![3d-asset-url](/help/assets/dynamic-media/assets/3d-asset-urla.png)

1. Um die direkte Produktions-URL des 3D-Assets anzuzeigen, die Sie kopieren und auf Web-Seiten verwenden können, wählen Sie **[!UICONTROL URL]**.

### Alternative Methoden zum Veröffentlichen von Dynamic Media-3D-Assets mit dem Dimensional-Viewer {#alternate-publish-methods}

Verwenden Sie die folgenden beiden Methoden zum Veröffentlichen von Dynamic Media-3D-Assets, wenn Sie [!DNL Experience Manager] *nicht* als WCM verwenden.

* **[!UICONTROL URL]** – Verwenden Sie **[!UICONTROL URL]**, wenn Sie ein Drittanbieter-Web-Content-Management-System verwenden und mit dem Dimensional-Viewer Dynamic Media-3D-Assets mit Ihren Web-Seiten verknüpfen möchten.

  Siehe [Verknüpfen von URLs mit einer Web-Anwendung](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md#obtaining-a-url-for-an-asset).

* **[!UICONTROL Einbetten]** – Verwenden Sie **[!UICONTROL Einbetten]**, wenn Sie ein in eine Web-Seite eingebettetes Dynamic Media-3D-Asset mit dem Dimensional-Viewer anzeigen möchten. Kopieren Sie den Einbettungs-Code in die Zwischenablage, damit Sie ihn in Ihre Web-Seiten einfügen können. Die Bearbeitung des Codes ist im Dialogfeld **[!UICONTROL Eingebettet]** nicht zulässig.

  Siehe [Einbetten von Dynamic Media-Videos, Bild-Viewern oder Dimensional-Viewern auf einer Web-Seite](/help/assets/dynamic-media/embed-code.md#embedding-the-video-or-image-viewer-on-a-web-page).
