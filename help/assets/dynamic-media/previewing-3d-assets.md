---
title: Vorschau von 3D-Assets
description: Erfahren Sie, wie Sie eine Vorschau von 3D-Elementen in Experience Manager erstellen.
contentOwner: Rick Brough
feature: 3D Assets
role: User
exl-id: e873bd25-f841-4063-824f-7e48f40bb678
source-git-commit: c82f84fe99d8a196adebe504fef78ed8f0b747a9
workflow-type: tm+mt
source-wordcount: '667'
ht-degree: 95%

---

# Vorschau von 3D-Assets in Adobe Experience Manager {#previewing-3d-assets}

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

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/previewing-3d-assets.html?lang=de) |
| AEM as a Cloud Service | Dieser Artikel |

Experience Manager Assets unterstützt die Aufnahme, Verwaltung, Vorschau und Bereitstellung von 3D-Assets.

Sie können eine Vorschau von 3D-Assets mit den automatisch generierten Miniaturansichten oder dem interaktiven 3D-Viewer anzeigen lassen. Der interaktive 3D-Viewer ist auf der Seite „Asset-Details“ in Experience Manager verfügbar. Der Viewer enthält unter anderem eine Reihe von interaktiven Kamerasteuerungen, mit denen Sie die 3D-Szene drehen, zoomen und schwenken können.

<!-- See also [Working with 3D assets in Dynamic Media](/help/assets/dynamic-media/assets-3d.md). -->

## Unterstützte Formate für die Miniaturvorschau in Experience Manager{#supported-thumbnail-previewing-assets}

Experience Manager generiert standardmäßig Miniaturansichten für die folgenden Dateiformate:

| 3D-Dateierweiterung | Dateiformat | MIME-Typ | Anmerkungen |
|---|---|---|---|
| GLB | Binäre GL-Übertragung | model/gltf-binary |  |
| FBX | Autodesk FBX | application/octet-stream |  |
| OBJ | WaveFront 3D-Objektdatei | application/x-tgif |  |
| 3DS | 3D Studio-Modell | application/x-3ds |  |
| USDz | Universelle Szenenbeschreibung | model/vnd.usdz+zip |  |

## Unterstützte Formate für die interaktive 3D-Vorschau in Experience Manager{#supported-3d-previewing-assets}

Experience Manager unterstützt die interaktive 3D-Vorschau für die folgenden Dateiformate nativ:

| 3D-Dateierweiterung | Dateiformat | MIME-Typ | Anmerkungen |
|---|---|---|---|
| GLB | Binäre GL-Übertragung | model/gltf-binary |  |
| GLTF | GL-Übertragungsformat | model/gltf+json | Siehe den **Hinweis** unten. |
| OBJ | WaveFront 3D-Objektdatei | application/x-tgif |  |
| STL | Stereolithografie | application/vnd.ms-pki.stl |  |


>[!NOTE]
>
>Wenn Materialien nicht in der Vorschau eines gLTF-Modells wiedergegeben werden, stellen Sie sicher, dass sie ordnungsgemäß benannt sind und sich in einem `textures`-Ordner befinden, der sich im selben Stammordner wie das Modell befindet, ähnlich wie im Folgenden beschrieben:

    Asset (folder)
    model.gltf
    model.bin
    textures (folder)
    material_0_baseColor.jpeg
    material_0_normal.jpeg

## Leistungsaspekte bei der Vorschau von 3D-Assets in Experience Manager {#performance-3d-previewing-assets}

Die Zeit, die zum Öffnen eines 3D-Assets auf der Seite mit den Asset-Details benötigt wird, hängt von verschiedenen Faktoren ab, z. B. Bandbreite, Bildkomplexität und Latenzen zum Server.

Wenn Sie die Kamera interaktiv handhaben, muss darüber hinaus die Kapazität des Client-Computers – etwa Workstation, Notebook oder Mobilgerät mit Touch-Funktion – berücksichtigt werden. Ein relativ leistungsfähiges System mit guten Grafikfähigkeiten unterstützt eine weichere, angenehmere interaktive 3D-Anzeige.

**So erstellen Sie eine Vorschau von 3D-Assets in Experience Manager:**

1. Stellen Sie sicher, dass Sie 3D-Assets in Adobe Experience Manager hochgeladen haben.
Siehe [Unterstützte Formate für die 3D-Vorschau](#supported-3d-previewing-assets) und [Hochladen von Assets](/help/assets/manage-digital-assets.md#uploading-assets).
1. Gehen Sie in Adobe Experience Manager auf der Seite **[!UICONTROL Navigation]** zu **[!UICONTROL Assets]** > **[!UICONTROL Dateien]**.

   ![Navigationsseite](/help/assets/dynamic-media/assets/navigation-assets.png)

1. Klicken Sie rechts oben auf der Seite in der Dropdown-Liste „Ansicht“ auf **[!UICONTROL Kartenansicht]** und gehenn Sie dann zu einem 3D-Asset, das Sie in der Vorschau anzeigen möchten.

   ![Auswahl der 3D-Karte](/help/assets/dynamic-media/assets/3d-card-select.png)
   _Wählen Sie in der Kartenansicht die Karte des 3D-Assets aus, das Sie in der Vorschau anzeigen möchten._

1. Klicken Sie auf die Karte des 3D-Assets.

   ![Interaktive 3D-Vorschau](/help/assets/dynamic-media/assets/3d-preview.png)
   _Interaktive Vorschau eines 3D-Assets auf der Seite mit der Detailansicht des Assets._
1. Führen Sie auf der Seite mit der Detailansicht des Assets für das 3D-Asset einen der folgenden Schritte aus:

   | Anzeigen | Beschreibung | Mausaktion | Touchscreen-Aktion |
   | --- | --- | --- | --- |
   | **Kamera drehen** | Drehen Sie die Ansicht um die 3D-Szene und Objekte. | Klicken und ziehen Sie mit der linken Maustaste. | Drücken und ziehen Sie mit einem Finger. |
   | **Kamera schwenken** | Schwenken Sie nach links, rechts, oben oder unten. | Klicken und ziehen Sie mit der rechten Maustaste. | Drücken und ziehen Sie mit zwei Fingern. |
   | **Kamera zoomen** | Bewegen Sie sich in Bereiche der 3D-Szene und wieder heraus. | Scrollen Sie mit dem Mausrad. | Ziehen Sie per Pinch mit zwei Fingern. |
   | **Kamera neu zentrieren** | Zentrieren Sie die Kamera neu auf einen Punkt an einem Objekt in der 3D-Szene. | Doppelklicken. | Doppelt auswählen. |
   | **Zurücksetzen** | Wählen Sie in der unteren rechten Ecke der Seite das Symbol „Zurücksetzen“, um den Zielpunkt der Ansicht wieder in die Mitte des 3D-Assets zu setzen. Durch das Zurücksetzen wird die Kamera auch näher heran oder weiter weg bewegt, um das Asset in seiner Gesamtheit und in einer angemessenen Betrachtungsgröße zu zeigen. |   |   |
   | **Vollbildmodus** | Um in den Vollbildmodus zu gelangen, wählen Sie in der unteren rechten Ecke der Seite das Symbol „Vollbild“. |   |   |

1. Klicken Sie zum Abschluss unten rechts auf der Seite auf **[!UICONTROL Schließen]**.
