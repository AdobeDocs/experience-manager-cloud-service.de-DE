---
title: Vorschau von 3D-Assets
description: Erfahren Sie, wie Sie eine Vorschau von 3D-Assets anzeigen können  in Dynamic Media.
source-git-commit: d3ee23917eba4a2e4ae1f2bd44f5476d2ff7dce1
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 55%

---


# Anzeigen einer Vorschau von 3D-Assets in Adobe Experience Manager{#previewing-3d-assets}

Experience Manager unterstützt das Hochladen, Bereitstellen und interaktive Anzeigen einer Vorschau von 3D-Assets als Teil des Authoring-Prozesses.

Der interaktive 3D-Viewer ist auf der Seite mit den Asset-Details in Experience Manager verfügbar. Der Viewer bietet unter anderem eine Reihe interaktiver Kamera-Steuerelemente, mit denen Sie die Kamera um das 3D-Asset drehen sowie Zoom- und Schwenkvorgänge durchführen können.

<!-- See also [Working with 3D assets in Dynamic Media](/help/assets/dynamic-media/assets-3d.md). -->

## Unterstützte Formate für die 3D-Vorschau in Experience Manager{#supported-3d-previewing-assets}

Die interaktive 3D-Vorschau in Experience Manager unterstützt die folgenden Dateiformate:

| 3D-Dateierweiterung | Dateiformat | MIME-Typ | Hinweise |
|---|---|---|---|
| GLB | Binäre GL-Übertragung | model/gltf-binary |  |
| GLTF | GL-Übertragungsformat | model/gltf+json | Siehe **Hinweis** weiter unten. |
| OBJ | WaveFront 3D-Objektdatei | application/x-tgif |  |
| STL | Stereolithografie | application/vnd.ms-pki.stl |  |
| DN | Adobe Dimension | model/x-adobe-dn | Unterstützung nur für die Erfassung; Vorschau nicht verfügbar. |
| USDZ | Universelles Scene Description-Zip-Archiv | model/vnd.usdz+zip | Unterstützung nur für die Erfassung; Vorschau nicht verfügbar. |

>[!NOTE]
>
>Wenn Materialien nicht in Vorschau eines gLTF-Modells wiedergegeben werden, vergewissern Sie sich, dass sie ordnungsgemäß benannt sind und sich in einem `textures`-Ordner im selben Stammordner wie das Modell befinden, ähnlich wie im Folgenden:

    Asset (folder)
    model.gltf
    model.bin
    textures (folder)
    material_0_baseColor.jpeg
    material_0_normal.jpeg

## Leistungsaspekte bei der Vorschau von 3D-Elementen in Experience Manager{#performance-3d-previewing-assets}

Die Zeit, die zum Öffnen eines 3D-Assets auf der Seite mit den Asset-Details benötigt wird, hängt von verschiedenen Faktoren ab, z. B. Bandbreite, Bildkomplexität und Latenzen zum Server.

Darüber hinaus sind die Funktionen des Client-Computers - wie eine Workstation, ein Notebook oder ein mobiles Touch-Gerät - auch bei einer interaktiven Manipulation der Kamera wichtig. Ein relativ leistungsfähiges System mit guten Grafikfähigkeiten unterstützt eine weichere, angenehmere interaktive 3D-Anzeige.

**Vorschau von 3D-Assets in Experience Manager:**

1. Stellen Sie sicher, dass Sie 3D-Assets in Adobe Experience Manager hochgeladen haben.
Siehe [Unterstützte Formate für die 3D-Vorschau](#supported-3d-previewing-assets) und [Hochladen von Assets](/help/assets/manage-digital-assets.md#uploading-assets).
1. Tippen Sie in Experience Manager auf der Seite **[!UICONTROL Navigation]** auf **[!UICONTROL Assets]** > **[!UICONTROL Dateien]**.

   ![Navigationsseite](/help/assets/dynamic-media/assets/navigation-assets.png)

1. Tippen Sie rechts oben auf der Seite in der Dropdown-Liste „Ansicht“ auf **[!UICONTROL Kartenansicht]** und navigieren Sie dann zu einem 3D-Asset, das Sie in der Vorschau anzeigen möchten.

   ![Auswahl der 3D-Karte](/help/assets/dynamic-media/assets/3d-card-select.png)
   _Tippen Sie in der Kartenansicht auf die Karte des 3D-Assets, das Sie in der Vorschau anzeigen möchten._

1. Tippen Sie auf die Karte des 3D-Assets.

   ![Interaktive 3D-Vorschau](/help/assets/dynamic-media/assets/3d-preview.png)
   _Interaktive Vorschau eines 3D-Assets auf der Seite mit der Detailansicht des Assets._
1. Führen Sie auf der Seite mit der Detailansicht des Assets für das 3D-Asset einen der folgenden Schritte aus:

   | Anzeigen | Beschreibung | Mausaktion | Touch-Screen-Aktion |
   | --- | --- | --- | --- |
   | **Kamera drehen** | Drehen Sie die Ansicht um die 3D-Szene und Objekte | Klicken Sie mit der linken Maustaste und ziehen Sie. | Drücken Sie mit einem Finger und ziehen Sie. |
   | **Kamera schwenken** | Schwenken Sie die Ansicht nach links, rechts, oben oder unten. | Klicken Sie mit der rechten Maustaste und ziehen Sie. | Drücken Sie die Zwei-Finger-Taste und ziehen Sie. |
   | **Zoomen der Kamera** | Verschieben Sie die Bereiche der 3D-Szene ein- und aus. | Bildlaufrad | Zweifinger-Pinch-Gesten. |
   | **Kamera neu einstellen** | Setzen Sie die Kamera auf einen Punkt auf einem Objekt in der 3D-Szene zurück. | Doppelklicken. | Doppeltippen. |
   | **Zurücksetzen** | Tippen Sie unten rechts auf der Seite auf das Symbol &quot;Zurücksetzen&quot;, um die Zielgruppe der Ansicht in der Mitte des 3D-Assets wiederherzustellen. Durch das Zurücksetzen wird die Kamera auch näher heran oder weiter weg bewegt, um das Asset in seiner Gesamtheit und in einer angemessenen Betrachtungsgröße zu zeigen. |  |  |
   | **Vollbildmodus** | Um in den Vollbildmodus zu wechseln, tippen Sie in der rechten unteren Ecke der Seite auf das Symbol &quot;Vollbild&quot;. |  |  |

1. Tippen Sie zum Abschluss unten rechts auf der Seite auf **[!UICONTROL Schließen]**.
