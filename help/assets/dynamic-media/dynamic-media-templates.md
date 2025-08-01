---
title: Verwalten der Vorlagen von [!DNL Dynamic Media] ?
description: Erfahren Sie, wie Sie  [!DNL Dynamic Media]  Vorlagen mit einem WYSIWYG-Vorlageneditor erstellen und mehrere Bild-, Text- und Formebenen einschließen, um Banner und Flyer schnell zu erstellen und in nachgelagerten Anwendungen zu verwenden.
hide: true
role: User
exl-id: 07de648e-4ae2-4524-8e05-3cf10bb6006d
source-git-commit: 69e6b5a50f4625b9ef868216f6e44381771bf05b
workflow-type: tm+mt
source-wordcount: '3415'
ht-degree: 78%

---


# [!DNL Dynamic Media]-Vorlagen{#dynamic-media-templates}

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

Erstellen Sie in Echtzeit anpassbare Vorlagen für Ihre Banner und Flyer mithilfe von [!DNL Dynamic Media]-Vorlagen in einem WYSIWYG-Vorlageneditor. Veröffentlichen Sie Ihre [!DNL Dynamic Media]-Vorlage und verwenden Sie sie in nachgelagerten Anwendungen. Eine [!DNL Dynamic Media]-Vorlage enthält Bild- und Textebenen. Fügen Sie den Bild- und Textebenen der Vorlage Parameter hinzu und verwenden Sie [[!DNL Dynamic Media] URLs](https://experienceleague.adobe.com/de/docs/commerce-admin/content-design/wysiwyg/storage/catalog-urls-dynamic-media), um die Ebene neu zu positionieren, ihre Größe zu ändern und ihren Inhalt in Echtzeit zu aktualisieren.

Zu den Hauptfunktionen gehören:

* **[!DNL Dynamic Media]-WYSIWYG-Vorlageneditor:** Erstellen Sie anpassbare Banner mit Bild- und Textebenen.
* **Ebenenparametrisierung:** Definieren Sie dynamische Schlüssel-Wert-Paare für Ebenen, um Aktualisierungen in Echtzeit zu ermöglichen.
* **[!DNL Dynamic Media]-URL-Unterstützung:** Verwenden Sie [!DNL Dynamic Media]-URLs für Vorlagen und integrieren Sie personalisierte Werte aus Anwendungen von Erst- oder Drittanbietern.
* **Steuerung der Ebenensichtbarkeit:** Blenden Sie Ebenen nach Bedarf dynamisch aus oder ein.
* **Intelligente Textgrößenänderung:** Passen Sie die Textgröße automatisch an bestimmte Bereiche an.

Zu den wichtigsten Vorteilen von [!DNL Dynamic Media]-Vorlagen gehören:

* **Optimieren 1:1 Personalization:** Passen Sie Inhalte an Echtzeit-Kundensignale an.
* **Weniger manueller Aufwand:** Automatisieren und beschleunigen Sie die Inhaltserstellung und -verwaltung.
* **Sicherstellung konsistenter Omni-Channel-Erlebnisse:** Gewährleisten Sie die Markenkonsistenz kanalübergreifend.
* **Effektive Wiederverwendung von Inhalten:** Vermeiden Sie Inhalte für die einmalige Verwendung und skalieren Sie mit dynamischen, parametrisierten Vorlagen.
* **Minderung von Risiken:** Aktualisieren Sie Preise, Rabatte und Links in Echtzeit.
* **Verbesserung der Kundeninteraktion:** Fördern Sie interaktive, kontextuell relevante Erlebnisse.

>[!NOTE]
>
>Kundinnen und Kunden mit Abonnements für die SKU für erweiterte Sicherheit können in diesem Cloud Services-Programm keine [!DNL Dynamic Media]-Funktionen, einschließlich [!DNL Dynamic Media]-Vorlagen, verwenden.

In diesem Video erfahren Sie, wie Sie Schritt für Schritt eine [!DNL Dynamic Media]-Vorlage erstellen.
>[!VIDEO](https://video.tv.adobe.com/v/3443281)

## Bevor Sie beginnen{#prerequisites-for-dynamic-media-wysiwyg-template}

Sie müssen folgende Voraussetzungen erfüllen, um eine [!DNL Dynamic Media]-Vorlage zu erstellen und ihre Versand-URL zu generieren:

1. Sie haben Zugriff auf [!DNL Dynamic Media].
1. Auf der [!DNL Assets View]-Homepage befindet sich ein Ordner in **[!UICONTROL Dynamic Media Assets]** zum Speichern der Vorlage. [Erstellen Sie einen Ordner](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/assets-view/add-delete-assets-view) in ![Assets](/help/assets/assets/Asset-icon.svg)**[!UICONTROL Assets &#x200B;]**, um diesen Ordner in&#x200B;**[!UICONTROL &#x200B; Dynamic Media Assets &#x200B;]**&#x200B;zu replizieren.
1. [Die in Ihrer Instanz von  [!DNL AEM Assets]  verfügbaren Bilder müssen mit  [!DNL Dynamic Media]  synchronisiert worden sein, damit sie für die Erstellung der Vorlage verwendet werden können](/help/assets/dynamic-media/config-dm.md).
1. Veröffentlichen Sie die Bilder, die bei der Erstellung der Vorlage verwendet werden sollen, um nach der Erstellung die Versand-URL der Vorlage zu generieren. Die Bereitstellungs-URL kann in nachgelagerten Anwendungen verwendet werden.
1. Um eine andere als die standardmäßige Schriftart [!UICONTROL Adobe Sans F2] in der Textebene der Vorlage zu verwenden, [laden Sie die Schriftartdatei gleichzeitig in AEM und Dynamic Media hoch](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/assets-view/publish-assets-to-aem-and-dm?lang=en#dynamic-media-publish-mode-set-to-upon-activation). [Folgende Schriftformate werden unterstützt: AFM, OTF, PFB, PFM, FotoFont, TTC und TTF](https://experienceleague.adobe.com/de/docs/dynamic-media-classic/using/upload-publish/uploading-files#supported-asset-file-formats). Stellen Sie außerdem sicher, dass vorhandene Schriftarten [erneut verarbeitet](/help/assets/reprocessing-assets-view.md) werden, um sie zu verwenden. Weitere Informationen finden Sie unter [Schriftarten](https://experienceleague.adobe.com/de/docs/dynamic-media-classic/using/support-files/fonts).<!--(On [!DNL Assets View] home page, click ![Assets](/help/assets/assets/Asset-icon.svg)**[!UICONTROL Assets]**, navigate to the font file location, select the font file one at a time and click ![Reprocess](/help/assets/assets/Refresh-docs.svg)**[!UICONTROL Reprocess]**)-->
1. Überprüfen Sie Folgendes im Touch-UI:
   * Auf der Seite **[!UICONTROL [!DNL Dynamic Media]-Konfiguration bearbeiten]** wird der **[!UICONTROL [!DNL Dynamic Media]-Synchronisierungsmodus]**, der auf **[!UICONTROL Standardmäßig deaktiviert]** festgelegt ist, nicht auf alle AEM-Ordner angewendet (die Option **[!UICONTROL Alle Inhalte synchronisieren]** ist deaktiviert). Weitere Informationen Sie unter [Konfigurieren von Dynamic Media Cloud Services](/help/assets/dynamic-media/config-dm.md).
   * Der **[!UICONTROL [!DNL Dynamic Media]-Synchronisierungsmodus]** ist für den Zielordner oder den Unterordner, in dem Sie die Vorlage nach der Erstellung speichern, auf **[!UICONTROL Für Unterordner aktivieren]** festgelegt. Weitere Informationen finden Sie unter [Konfigurieren von [!DNL Dynamic Media] Cloud Services](/help/assets/dynamic-media/config-dm.md).

## Erstellen einer [!DNL Dynamic Media]-Vorlage{#how-to-create-dynamic-media-template}

Führen Sie die folgenden Schritte aus, um eine [!DNL Dynamic Media]-Vorlage zu erstellen:
<!--
1. Navigate to your [!DNL Assets View] and [create a folder](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/assets-view/add-delete-assets-view) in ![Assets](/help/assets/assets/Asset-icon.svg)**[!UICONTROL Assets]**. The folder tree in ![Assets](/help/assets/assets/Asset-icon.svg)**[!UICONTROL Assets]** replicates in **[!UICONTROL Dynamic Media Assets]**. Save your [!DNL Dynamic Media] template in this [!UICONTROL Dynamic Media Assets] folder.
1. Select ![Assets](/help/assets/assets/Asset-icon.svg)**[!UICONTROL Assets]** and [upload and publish your images to [!DNL AEM] and [!DNL Dynamic Media] simultaneously](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/assets-view/publish-assets-to-aem-and-dm#dynamic-media-publish-mode-set-to-upon-activation) to use them in creating the template. Publishing images is required to generate the template's delivery URL, after creating the template. The delivery URL can be used in downstream applications.
1. [Execute these asset uploading and publishing steps](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/assets-view/publish-assets-to-aem-and-dm?lang=en#dynamic-media-publish-mode-set-to-upon-activation) to upload and publish a font file to AEM and Dynamic Media simultaneously to use it in creating the template. [!UICONTROL Adobe Sans F2] is the only default font available in the text layer. [The supported font file formats are, AFM, OTF, PFB, PFM, PhotoFont, TTC, TTF](https://experienceleague.adobe.com/de/docs/dynamic-media-classic/using/upload-publish/uploading-files#supported-asset-file-formats). Ensure to [reprocess](/help/assets/reprocessing-assets-view.md) the existing fonts to use them in creating the template (On [!DNL Assets View] home page, click ![Assets](/help/assets/assets/Asset-icon.svg)**[!UICONTROL Assets]**, navigate to the font file location, select the font file one at a time and click ![Reprocess](/help/assets/assets/Refresh-docs.svg)**[!UICONTROL Reprocess]**). See [Fonts](https://experienceleague.adobe.com/de/docs/dynamic-media-classic/using/support-files/fonts) to know more about fonts.
-->
1. [Erstellen einer leeren Arbeitsfläche](#create-a-canvas)
1. [Hinzufügen von Bildern zur Arbeitsfläche](#add-images-to-the-canvas)
1. [Hinzufügen von Textebenen zur Arbeitsfläche](#add-text-to-the-canvas)
1. [Hinzufügen von Shapes zur Arbeitsfläche](#add-shapes-to-the-canvas)
1. [Bearbeiten oder Löschen einer Ebene](#edit-or-delete-a-layer)
1. [Parametrisieren von Ebenen](#parameterise-a-layer)

### Erstellen einer leeren Arbeitsfläche{#create-a-canvas}

Führen Sie die folgenden Schritte aus, um eine leere Arbeitsfläche zu erstellen:

1. Navigieren Sie zu [!DNL Assets View], wählen Sie im linken Panel die Option **[!UICONTROL Dynamic Media Assets]** aus und navigieren Sie zu Ihrem Ordner, um Ihre Vorlage in diesem Ordner zu speichern.

   ![Dynamic Media-Vorlagen](/help/assets/assets/DM-Assets1.png)

1. Wählen Sie **[!UICONTROL Vorlage erstellen]** aus. Das Dialogfeld **[!UICONTROL Neue Vorlage]** wird angezeigt.
   ![Erstellen dynamischer Vorlagen, die in Echtzeit angepasst werden können](/help/assets/assets/new-template.png)
   >[!NOTE]
   >
   >  Die Vorlage wird an dem Speicherort gespeichert, an dem Sie sie erstellen. Wählen Sie auf der [!DNL Assets View]-Startseite **[!UICONTROL Dynamic Media Assets]** und klicken Sie auf **[!UICONTROL Vorlage erstellen]**, um die Vorlage im Stammordner **[!UICONTROL Dynamic Media Assets]** zu speichern.

1. Geben Sie einen Namen für die Vorlage an, definieren Sie die Breite und Höhe der Arbeitsfläche und klicken Sie auf **[!UICONTROL Erstellen]**. Es wird eine leere Arbeitsfläche mit Menüoptionen auf beiden Seiten angezeigt, die zum Erstellen der Vorlage verwendet werden können. Bewegen Sie den Mauszeiger über die Menüoptionen, um deren QuickInfo anzuzeigen.
   ![In Echtzeit anpassbare Vorlage](/help/assets/assets/blank-canvas-page.png)

   >[!NOTE]
   >
   > Der zulässige Breiten- und Höhenbereich liegt zwischen 50 und 5.000.

**Menüoptionen im rechten Bereich:** Verwenden Sie diese Optionen, um der Arbeitsfläche die erforderlichen Bilder und Textebenen hinzuzufügen.

* ![DM-Vorlagen](/help/assets/assets/add-image.svg): Klicken Sie, um der Arbeitsfläche Bilder hinzuzufügen.
* ![Anpassbare Vorlagen](/help/assets/assets/add-text.svg): Klicken Sie, um der Arbeitsfläche Texte hinzuzufügen.
* ![Anpassbare Vorlagen](/help/assets/assets/show-layers-list.svg): Klicken Sie, um die Liste aller Ebenen (Bild und Text) auf der Arbeitsfläche anzuzeigen. Jedes Bild und jeder Text, das bzw. der der Arbeitsfläche hinzugefügt wird, wird als separate Ebene dargestellt.

**Menüoptionen im linken Bereich:** Verwenden Sie diese Optionen für die folgenden gängigen Editoraktionen.

* ![DM-Vorlagen](/help/assets/assets/layer-selector.svg): Wählen Sie ![DM-Vorlagen](/help/assets/assets/layer-selector.svg) aus und klicken Sie auf eine Ebene auf der Arbeitsfläche, um sie auszuwählen.
* ![Vorlagen, die Anpassungen unterstützen](/help/assets/assets/bring-forward.svg): Klicken Sie auf ![Vorlagen, die Anpassungen unterstützen](/help/assets/assets/bring-forward.svg) oder verwenden Sie den Tastaturbefehl **Strg**+**&rbrack;** (Windows) bzw. **Befehlstaste**+**&rbrack;** (Mac), um eine ausgewählte Ebene nach vorne zu bringen.
* ![Erstellen einer Vorlage, die einfach angepasst werden kann](/help/assets/assets/send-backward.svg): Klicken Sie auf ![Erstellen einer Vorlage, die einfach angepasst werden kann](/help/assets/assets/send-backward.svg) oder verwenden Sie den Tastaturbefehl **Strg**+**&lbrack;** (Windows) bzw. **Befehlstaste**+**&lbrack;** (Mac), um eine ausgewählte Ebene nach hinten zu bringen.
* ![Erstellen einer Vorlage, die sofort angepasst werden kann](/help/assets/assets/undo.svg): Klicken Sie auf ![Erstellen einer Vorlage, die sofort angepasst werden kann](/help/assets/assets/undo.svg) oder verwenden Sie den Tastaturbefehl **Strg**+**Z** (Windows) bzw. **Befehlstaste**+**Z** (Mac), um die letzte Aktion rückgängig zu machen.
* ![Vorlage zum schnellen Erstellen von Bannern](/help/assets/assets/redo.svg): Klicken Sie auf ![Vorlage zum schnellen Erstellen von Bannern](/help/assets/assets/redo.svg) oder verwenden Sie den Tastaturbefehl **Strg**+**Y** (Windows) bzw. **Befehlstaste**+**Y** (Mac), um die letzte Aktion wiederherzustellen.
* ![Vorlage zum schnellen Erstellen von Flyern](/help/assets/assets/zoom-in.svg): Klicken Sie auf ![Vorlage zum schnellen Erstellen von Flyern](/help/assets/assets/zoom-in.svg) oder verwenden Sie den Tastaturbefehl **Strg**+**+** (Windows) bzw. **Befehlstaste**+**+** (Mac), um die Arbeitsfläche heranzuzoomen.
* ![Vorlage zum schnellen Erstellen von Bannern](/help/assets/assets/Zoom-out.svg): Klicken Sie auf ![Vorlage zum schnellen Erstellen von Bannern](/help/assets/assets/Zoom-out.svg) oder verwenden Sie den Tastaturbefehl **Strg**+**-** (Windows) bzw. **Befehlstaste**+**-** (Mac), um die Arbeitsfläche herauszuzoomen.
* Drücken Sie **Rücktaste** oder **Löschen**, um die ausgewählte Ebene zu löschen, wenn kein Text oder keine Eigenschaft bearbeitet wird.

Klicken Sie in der Arbeitsflächenebene auf ![Vorlage zum schnellen Erstellen von Flyern](/help/assets/assets/show-layers-list.svg) und wählen Sie weitere Optionen (![](/help/assets/assets/three-dots.svg)) aus, um die Abmessungen der Arbeitsfläche jederzeit beim Erstellen der Vorlage zu bearbeiten.
![](/help/assets/assets/edit-canvas1.png)

>[!NOTE]
>
> Vorlagen lassen maximal 20 Ebenen zu, einschließlich der Arbeitsfläche.

### Hinzufügen von Bildern zur Arbeitsfläche{#add-images-to-the-canvas}

Führen Sie die folgenden Schritte aus, um der Arbeitsfläche Bilder hinzuzufügen:

1. Klicken Sie auf ![Banner im Handumdrehen erstellen](/help/assets/assets/add-image.svg), um das Panel [Asset-Wähler](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/manage/asset-selector/overview-asset-selector) zu öffnen. Das Panel zeigt die Bilder in Ihrer AEM Assets-Instanz an, die mit Dynamic Media synchronisiert werden.[!DNL Dynamic Media]
1. Durchsuchen Sie das Bedienfeld oder verwenden Sie Keywords in der Suchleiste, um nach einem bestimmten Bild zu suchen.
1. Ziehen Sie ein Bild per Drag-and-Drop auf die Arbeitsfläche, um es zu verwenden. Zum Ändern der Größe oder Neupositionieren einer Ebene auf der Arbeitsfläche gehen Sie zum [**[!UICONTROL Bedienfeld „Eigenschaften“]**](#reposition-resize-delete-a-layer).
   ![Erstellen eines Banners innerhalb von Sekunden](/help/assets/assets/add-image-to-canvas.png)
1. Aktivieren Sie den **[!UICONTROL Einheitlicher Radius]** und passen Sie mit dem **[!UICONTROL Eckenradius]**-Schieberegler die Rundung aller vier Ecken eines Bildes gleichmäßig an. Deaktivieren Sie den Umschalter, um die Eckenrundung anzupassen, indem Sie jeder Ecke bestimmte Radiuswerte zuweisen.
   ![Eckenrundung des Bildes anpassen](/help/assets/assets/enable-uniform-radius-image.png)

### Hinzufügen von Textebenen zur Arbeitsfläche{#add-text-to-the-canvas}

Führen Sie die folgenden Schritte aus, um der Arbeitsfläche Textebenen hinzuzufügen:

1. Klicken Sie auf ![Schnelles Erstellen neuer Banner](/help/assets/assets/add-text.svg), um der Arbeitsfläche eine Textebene hinzuzufügen und das Bedienfeld „Eigenschaften“ zu öffnen.
1. Wählen Sie die Ebene aus und klicken Sie zum Aktualisieren auf den Text.
1. Wählen Sie im Panel „Eigenschaften“ die Option **[!UICONTROL Intelligente Textgrößenänderung]** aus, um die Textlänge und den Schriftgrad automatisch und optimal an den vorgesehenen Bereich anzupassen.
   ![Optimal anpassbare Banner](/help/assets/assets/add-text-layer.png)

Zum Neupositionieren, Ändern der Größe, Drehen oder Löschen der Ebene gehen Sie zum [**[!UICONTROL Bedienfeld „Eigenschaften“]**](#reposition-resize-delete-a-layer). Formatieren Sie Schriftart, Größe, Farbe, Stil und Ausrichtung (auf der Ebene) des Textes wie erforderlich, indem Sie die Werte in den entsprechenden Feldern unter dem Abschnitt **[!UICONTROL Text]** des Panels ändern. Das Feld **[!UICONTROL Schriftfamilie]** zeigt die Standardschriftart [!UICONTROL Adobe Sans F2], die neu verarbeiteten vorhandenen Schriftarten sowie die neu hochgeladenen und veröffentlichten Schriftarten an. Weitere Informationen finden Sie unter Punkt 5 im Abschnitt [Bevor Sie beginnen](#prerequisites-for-dynamic-media-wysiwyg-template).

### Hinzufügen von Shapes zur Arbeitsfläche {#add-shapes-to-the-canvas}

Führen Sie die folgenden Schritte aus, um der Arbeitsfläche Formen hinzuzufügen:

1. Klicken Sie ![Formen erstellen](/help/assets/assets/Shapes.svg) und wählen Sie eine Form (Rechteck oder Kreis) aus, um sie der Arbeitsfläche hinzuzufügen. Verwenden Sie das Bedienfeld [[!UICONTROL Eigenschaften“ des Shapes]](#reposition-resize-delete-a-layer) um die Ebene neu zu positionieren, zu skalieren, zu drehen oder zu löschen.
1. Scrollen Sie zum Abschnitt **[!UICONTROL Stil]** des Bedienfelds, definieren Sie einen Hexadezimalcode im Feld **[!UICONTROL Formfarbe]** oder verwenden Sie die Farbauswahl, um die Farbe in der ausgewählten Form zu füllen.
1. Aktivieren Sie den **[!UICONTROL Einheitlicher Radius]** und passen Sie mit dem **[!UICONTROL Eckenradius]**-Schieberegler die Rundung aller vier Ecken des Rechtecks gleichmäßig an. Deaktivieren Sie den Umschalter, um die Eckenrundung anzupassen, indem Sie jeder Ecke bestimmte Radiuswerte zuweisen.
   ![Eckenrundung von Shapes anpassen](/help/assets/assets/enable-uniform-radius-shape.png)
1. [Fügen Sie den Parameter **[!UICONTROL Ausblenden]** zur ausgewählten Ebene hinzu](#parameterise-a-layer) um die Ebene in der Vorlage mithilfe der Vorlagen-URL in Echtzeit ein- oder auszublenden.
1. Wählen Sie die Ebene aus[ auf die Sie einen [!UICONTROL CTA]-Link ](#add-CTA-in-dynamic-media-templates) möchten, damit Benutzer auf die Form als Hyperlink in der Live-Vorlage klicken können.

### Bearbeiten oder Löschen einer Ebene {#edit-or-delete-a-layer}

Führen Sie die folgenden Schritte aus, um eine Arbeitsflächenebene zu bearbeiten oder zu löschen:

1. Klicken Sie auf ![Vorlagen mit Unterstützung für dynamische Aktualisierungen](/help/assets/assets/show-layers-list.svg) und wählen Sie die Ebene entweder auf der Arbeitsfläche oder über die Liste „Ebenen“ aus.
1. Klicken Sie auf **[!UICONTROL Weitere Optionen]** (![Vorlagen mit Unterstützung für Echtzeitaktualisierungen](/help/assets/assets/three-dots.svg)), um die Ebene zu bearbeiten oder zu löschen.
1. Klicken Sie auf **[!UICONTROL Löschen]**, um die Ebene zu löschen.
1. Klicken Sie auf **[!UICONTROL Bearbeiten]**, um die Ebene mithilfe des [**[!UICONTROL Bedienfelds „Eigenschaften“]**](#reposition-resize-delete-a-layer) zu bearbeiten.
   ![Schnelle Bannererstellung](/help/assets/assets/dm-templates/edit-delete-layer.png)

### Bedienfeld „Eigenschaften“{#properties-panel}

[!UICONTROL Eigenschaften] enthält Abschnitte zum [ (](#reposition-resize-delete-a-layer)), [Größenanpassung](#reposition-resize-delete-a-layer) und [Drehen](#reposition-resize-delete-a-layer) einer Ebene.  Es bietet auch Farbfülloptionen für [Formebenen](#add-shapes-to-the-canvas), [Textformatierungsoptionen](#text-formatting-options-on-properties-panel) für [Textebenen](#add-text-to-the-canvas) und eine Option zum [Hinzufügen eines [!UICONTROL CTA]-Links](#add-CTA-in-dynamic-media-templates) zu einer beliebigen ausgewählten Ebene.
Um zum Eigenschaftenbereich einer Ebene zu navigieren, klicken Sie auf ![Schnelle Inhaltserstellung](/help/assets/assets/show-layers-list.svg) und wählen Sie die Ebene aus der Liste aus, um den zugehörigen [!UICONTROL Eigenschaften] anzuzeigen.

![Schnelle Inhaltserstellung](/help/assets/assets/properties-panel.png)

Wählen [!UICONTROL &#x200B; im Bedienfeld &#x200B;]Eigenschaften“ einer Ebene eine andere Ebene auf der Arbeitsfläche aus, um zum zugehörigen Bedienfeld [!UICONTROL Eigenschaften] zu navigieren.

#### Neupositionieren, Ändern der Größe, Drehen oder Löschen einer Ebene{#reposition-resize-delete-a-layer}

Sehen Sie sich die folgenden allgemeinen Ebenenbearbeitungsaktionen an, um eine Text- oder Bildebene zu bearbeiten:

* **Ebene neu positionieren:** Ziehen Sie die Ebene, um sie an eine beliebige Stelle auf der Arbeitsfläche zu verschieben. Diese Aktion aktualisiert die X- und Y-Werte im Eigenschaftenbereich. X und Y sind die Koordinaten der Mitte des Layers auf der Leinwandebene.
* **Größe der Ebene ändern:** Wählen Sie die Ebene aus und ziehen Sie die Kantengriffe, um die Größe zu ändern. Diese Aktion aktualisiert die Werte „W“ (Breite) und „H“ (Höhe) im Bedienfeld „Eigenschaften“.
* **Ebene drehen:** Ziehen Sie den quadratischen, vertikal über der Ebene platzierten Griff, um sie ihren Mittelpunkt zu drehen. Diese Aktion aktualisiert die Werte der Winkel im Bedienfeld „Eigenschaften“.
* **Ebene löschen:** Drücken Sie die **Rücktaste** oder die **Löschtaste** und klicken Sie dann auf **[!UICONTROL Bestätigen]**, um eine ausgewählte Ebene zu löschen.

#### Optionen für die Textformatierung{#text-formatting-options-on-properties-panel}

Formatieren Sie Ihren Text in der erforderlichen Schriftart, Größe, Farbe, Stil und Ausrichtung (innerhalb der Ebene), indem Sie deren Werte in den entsprechenden Feldern unter dem Abschnitt **[!UICONTROL Text]** des Bedienfelds ändern.
Achten Sie darauf, **[!UICONTROL Intelligente Textgrößenänderung]** einzuschließen. Die Option [!UICONTROL Intelligente Textgrößenänderung] nutzt den [Texteinpassungsalgorithmus](https://experienceleague.adobe.com/de/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/text-formatting/r-copy-fitting), um Text optimal in den Textbereich einzupassen, Textüberlauf zu verhindern und zusätzliche Leerzeichen am unteren Rand des Textes zu minimieren.

![Inhaltserstellung im Handumdrehen](/help/assets/assets/smart-text-resize.png)

### Parametrisieren von Ebenen {#parameterise-a-layer}

Nachdem Sie eine Vorlage mit mehreren Bild-, Text- und Formebenen erstellt haben, parametrisieren Sie die ausgewählten Ebenen. Wenn eine Ebene oder ihre Eigenschaft parametrisiert wird, erhält sie ein Schlüssel-Wert-Paar (auch als Parameter bezeichnet). Dieser Parameter kann in die Vorlagen-URL aufgenommen werden, um Position, Größe oder Inhalt der Ebene in Echtzeit zu aktualisieren, wodurch die Vorlage in kürzester Zeit angepasst wird.

So parametrisieren Sie eine Ebene:

1. Klicken Sie auf ![Sofortige Inhaltserstellung](/help/assets/assets/show-layers-list.svg), wählen Sie eine Ebene aus und klicken Sie auf **[!UICONTROL Parameter]**. Das Bedienfeld **[!UICONTROL Parameter]** wird angezeigt.
1. Schalten Sie **[!UICONTROL Parameter einschließen]** um, um eine Eigenschaft zu parametrisieren. Siehe die Option [Bedienfeld „Parameter](#parameterisation-options-or-allowed-parameters), um das Verhalten der Eigenschaft nach der Parametrisierung zu erfahren.
1. **Optional:** Benennen Sie den Parameter um. Ein Parametername hat einen Ebenennamen, gefolgt von einem Suffix. Für eine ausgewählte Ebene verwenden alle parametrisierten Eigenschaften denselben Ebenennamen, gefolgt von einem variierenden Suffix. Benennen Sie den Ebenennamen um, indem Sie der semantischen Namenskonvention folgen, sodass bei Aufnahme des Parameters in die URL der Parametername selbst den Inhalt oder den Zweck der Ebene erklärt.
1. Klicken Sie auf **[!UICONTROL Speichern]**.
   ![Sofortige Inhaltserstellung](/help/assets/assets/parameterise-a-layer.png)
Um zwischen dem Bedienfeld „Parameter“ eines Bildes und der Textebene zu wechseln, wählen Sie die Ebene auf der Arbeitsfläche aus und klicken Sie auf **[!UICONTROL Parameter]**.

#### Option des Bedienfelds „Parameter“ {#parameterisation-options-or-allowed-parameters}

Die parametrisierten Eigenschaften können als URL-Parameter in die Vorlagen-URL aufgenommen werden, um die Vorlage mithilfe der URL in Echtzeit zu bearbeiten.

**Bildparameter:**

**[!UICONTROL X]:** Einfügen, um die Ebene horizontal entlang ihrer Mittellinie parallel zur X-Achse der Vorlagenebene zu verschieben, indem der Parameterwert in der URL geändert wird.
**[!UICONTROL Y]:** Einfügen, um die Ebene vertikal entlang ihrer Mittellinie parallel zur Y-Achse der Vorlagenebene zu verschieben, indem der Parameterwert in der URL geändert wird.
**[!UICONTROL Breite]:** Fügen Sie dies ein, um die Breite der Ebene anzupassen, indem der Wert des Parameters in der URL geändert wird.
**[!UICONTROL Höhe]:** Fügen Sie dies ein, um die Höhe der Ebene anzupassen, indem der Wert des Parameters in der URL geändert wird.
**[!UICONTROL Ausblenden]:** Fügen Sie dies ein, um die Ebene in der Vorlage mit 0 (Einblenden) und 1 (Ausblenden) ein- oder auszublenden.
**[!UICONTROL Source]:** Include, um das Ebenenbild durch ein neues Bild zu ersetzen, indem der Bildpfad im Parameterwert in der URL geändert wird.

**Textformatierungsparameter:**

Schließen Sie die folgenden Parameter ein, um den Text, seine Schriftart, Farbe und Größe aus der URL zu bearbeiten, indem Sie die Parameterwerte in der URL aktualisieren.

**[!UICONTROL Text]:** Fügen Sie dies ein, um Text in der URL zu aktualisieren.
**[!UICONTROL Schriftfamilie]:** Fügen Sie dies ein, um die Schriftart des Textes in der URL zu aktualisieren.
**[!UICONTROL Schriftgröße]:** Fügen Sie dies ein, um die Schriftgröße des Textes in der URL zu aktualisieren.
**[!UICONTROL Textfarbe]:** Fügen Sie dies ein, um die Schriftfarbe des Textes in der URL zu aktualisieren.

### Gruppieren von Ebenen für die gleichzeitige Steuerung Ihrer Sichtbarkeit{#group-layers}

Eine weitere Möglichkeit, Ihre Vorlagen flexibel zu halten, besteht darin, mehrere Ebenen mit einem einzigen Parameternamen zu steuern. Diese Strategie ist hilfreich für den Parameter „Sichtbarkeit“ (Ebenen ausblenden oder anzeigen), um das Design oder die Grafiken aus einer einzigen Vorlage zu aktualisieren.

Führen Sie diese Schritte aus, um den Parametern [!UICONTROL Ausblenden] (![schnelle Inhaltserstellung](/help/assets/assets/Visibility-icon.svg)) mehrerer Ebenen denselben Namen zuzuweisen, sodass Sie sie gleichzeitig ausblenden oder anzeigen können.

1. Navigieren Sie zum [**[!UICONTROL Bedienfeld „Eigenschaften“]**](#parameterise-a-layer) einer Ebene.
1. Schalten Sie den Parameter **[!UICONTROL Ausblenden]** ein, falls er nicht zuvor parametrisiert wurde.
1. **Optional:** Benennen Sie den Parameter **[!UICONTROL Ausblenden]** um.
1. Kopieren Sie den Namen des Parameters **[!UICONTROL Ausblenden]**.
1. Wechseln Sie zum Bedienfeld „Parameter“ anderer Ebenen, indem Sie sie auf der Arbeitsfläche auswählen und ihren Parameter **[!UICONTROL Ausblenden]** umschalten, falls er nicht parametrisiert ist.
1. Ersetzen Sie den Namen **[!UICONTROL Parameter ausblenden]** durch den kopierten Namen.
1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Ebenen zu gruppieren.
1. Führen Sie Schritt 3 und dann Schritt 4 im Abschnitt [**[!UICONTROL Vorschau und &#x200B;]**](#preview-and-publish-template-and-copy-template-deliver-url)&quot; aus, um Ihre Änderungen anzuzeigen.

## Anzeigen der Vorlage in der Vorschau und Veröffentlichen der Vorlage zum Kopieren der Bereitstellungs-URL{#preview-and-publish-template-and-copy-template-deliver-url}

Führen Sie die folgenden Schritte aus, um die Vorlage in der Vorschau anzuzeigen und zu veröffentlichen und die Bereitstellungs-URL zu kopieren:

1. Klicken Sie auf der Seite „Arbeitsfläche“ auf **[!UICONTROL Vorschau]**. Sie können auch zu **[!UICONTROL Assets-Ansicht]** **>** **[!UICONTROL Dynamic Media-Assets]** **&#x200B;**&#x200B;navigieren, Ihre Vorlage suchen und auswählen und dann **&#x200B;**&#x200B;auf **&#x200B;**&#x200B;Vorlage bearbeiten **&#x200B;**&#x200B;sowie auf **[!UICONTROL Vorschau]** klicken. Auf der Seite „Vorschau“ werden die Vorlage, ihre Parameter (parametrisierte Ebenen und Eigenschaften), der Veröffentlichungsstatus und die Option **[!UICONTROL Veröffentlichen]** angezeigt.
1. Wählen Sie Parameter aus dem Bedienfeld **[!UICONTROL Vorlagenparameter]** aus, um ihre Werte zu bearbeiten und den Inhalt, die Größe, die Position oder die Textformatierung der entsprechenden Vorlagenebene in der Vorschau sofort zu aktualisieren. Zum Beispiel:
   1. Auswählen einer Textebene und Bearbeiten ihres Textes oder
   1. Wählen Sie eine Bildebene aus, klicken Sie auf ![Inhalt spontan erstellen](/help/assets/assets/add-image.svg), wählen Sie ein Bild aus der Asset-Auswahl aus und klicken Sie auf **[!UICONTROL Aktualisieren]**.

   Die Vorlage wird sofort aktualisiert, wobei der bearbeitete Text angezeigt und das vorherige Bild durch das neue Bild ersetzt wird. Darüber hinaus spiegelt der Bildparameterwert den neuen Bildpfad wider. Auf ähnliche Weise können Sie die Größe einer Ebene ändern, indem Sie ihre Werte anpassen. Die Änderungen werden dann in Echtzeit auf die Vorlage angewendet.
1. Wählen Sie den Parameter **[!UICONTROL Ausblenden]** für [gruppierte Ebenen](#group-layers) aus der Liste aus, um sie zusammen in der Vorlage ein- oder auszublenden.
1. **Optional:** Ändern Sie den Wert des Parameters **[!UICONTROL Ausblenden]** von 0 auf 1 oder umgekehrt und klicken Sie auf **[!UICONTROL Aktualisieren]**, um die Änderungen anzuzeigen. Ebenen mit demselben Parameter **[!UICONTROL Ausblenden]** werden zusammen aus- oder eingeblendet. Auf ähnliche Weise können Sie die Sichtbarkeit der Ebenen über die URL steuern.

   ![Inhalt spontan erstellen](/help/assets/assets/dm-templates-publish-status.png)
Sie können auch **[!UICONTROL Alle Parameter einbeziehen]** umschalten, um alle angezeigten Parameterwerte zu bearbeiten und die Aktualisierungen in der Vorlagenvorschau anzuzeigen.
   <br>
1. Um die Vorlage auf der Vorschauseite zu veröffentlichen, klicken Sie auf **[!UICONTROL Veröffentlichen]** und bestätigen Sie die Veröffentlichung. Es wird die Meldung **[!UICONTROL Veröffentlichung abgeschlossen]** angezeigt und der Veröffentlichungsstatus wird auf **[!UICONTROL Veröffentlicht]** aktualisiert.

### Kopieren der Bereitstellungs-URL

Die ausgewählten Parameter auf der Seite **[!UICONTROL Vorschau]** werden zu den URL-Parametern in der Vorlagen-URL.

Stellen Sie sicher, dass die Bilder bereits in der Vorlage in AEM und Dynamic Media veröffentlicht sind, um eine Bereitstellungs-URL der veröffentlichten Vorlage zu generieren.

Führen Sie die folgenden Schritte aus, um die Bereitstellungs-URL der Vorlage zu kopieren:

1. Klicken Sie auf **[!UICONTROL URL kopieren]**. Das Dialogfeld **[!UICONTROL URL kopieren]** wird angezeigt. Wählen Sie die angezeigte URL aus und kopieren Sie sie. Der erste Parameter in der URL beginnt nach einem Fragezeichen **([!UICONTROL ?])**, während ein Schlüssel-Wert-Paar mit **[!UICONTROL $]** beginnt und mit **[!UICONTROL &amp;]** endet. Schlüssel und Wert werden durch ein Gleichheitszeichen **([!UICONTROL =])** getrennt, wobei sich der Schlüssel links und der Wert rechts befindet.
1. Fügen Sie diese URL in Ihre Browser-Registerkarte ein und sehen Sie sich Ihre Live-Vorlage an. Passen Sie die Vorlage in Echtzeit an, indem Sie den erforderlichen Parameterwert (Schlüsselwert) in der URL direkt aktualisieren, wie in [Schritt 2](#preview-and-publish-template-and-copy-template-deliver-url) des Abschnitts **Vorschau und Veröffentlichung** gezeigt.
1. Verwenden Sie diese URL für das schnelle Merchandising Ihrer Produkte oder Services. Sie können diese URL für Ihre Kundschaft freigeben oder in Ihre Website oder eine nachgelagerte Drittanbieteranwendung integrieren, um das Banner anzuzeigen und Aktualisierungen daran in Echtzeit vorzunehmen, sodass die laufenden Angebote widergespiegelt werden.

## Vornehmen von Aktualisierungen an der Vorlage in Echtzeit über die URL{#update-the-template-from-the-url}

Das direkte Bearbeiten von Parametern in der URL kann mühsam sein. Zur Vereinfachung können Sie wie folgt vorgehen:

1. Kopieren Sie die URL und fügen Sie sie in einen Editor ein.
1. Verwenden Sie Befehlstaste+F (Mac) bzw. Strg+F (Windows), um die Parameterwerte zu finden und zu bearbeiten. Beispiel:
   * Suchen und ersetzen Sie Bildpfade für Bildebenen.
   * Findet die (parametrisierten[ Koordinaten, Breite und Höhe ](#parameterise-a-layer) Ebene, um ihre Werte anzupassen.
   * Bearbeiten Sie Text, Schriftart, Farbe, Größe oder Ausrichtung für Textebenen.
   * Ändern Sie die Sichtbarkeitswerte zwischen 0 und 1.

Fügen Sie diese aktualisierte URL in Ihren Browser ein, um die Änderungen anzuzeigen.

## Bearbeiten der Vorlage{#edit-the-template}

Gehen Sie wie folgt vor, um die Vorlage zu bearbeiten:

1. Klicken Sie in der [!DNL Assets view] auf **[!UICONTROL Dynamic Media Assets]**.
2. Navigieren Sie zum Speicherort der Vorlage.
3. Wählen Sie die Vorlage aus.
4. Klicken Sie auf **[!UICONTROL Vorlage bearbeiten]**. Auf der Vorlagenarbeitsfläche werden die Vorlage und die Liste aller zugehörigen Ebenen im Bedienfeld „Ebenen“ angezeigt. Bearbeiten Sie Ihre Vorlage gemäß Ihren Anforderungen.

## Hinzufügen eines CTA-Links zu Ihrer Vorlagenebene{#add-CTA-in-dynamic-media-templates}

Wandeln Sie eine Bild-, Text- oder Formebene Ihrer [!DNL Dynamic Media] in einen Hyperlink um, indem Sie einen CTA-Link hinzufügen, der Benutzer zu einer Zielseite weiterleitet.

Führen Sie die folgenden Schritte aus, um einer Ebene einen CTA-Link hinzuzufügen:

1. Navigieren Sie zu Ihrem Vorlagenspeicherort, wählen Sie die Vorlage aus und klicken Sie auf ![Bearbeiten](/help/assets/assets/edit-pen-icon.svg) **[!UICONTROL Vorlage bearbeiten]**. Die Vorlage wird auf der Arbeitsfläche angezeigt.
1. Wählen Sie die Vorlagenebene aus und [navigieren Sie zum zugehörigen Panel „Eigenschaften“](#edit-or-delete-a-layer), um ihr einen CTA-Link hinzuzufügen.
1. Wählen Sie im Panel „Eigenschaften“ die Option **[!UICONTROL CTA hinzufügen]** aus, geben Sie die Ziel-URL in das Feld **[!UICONTROL URL]** ein und klicken Sie auf **[!UICONTROL Speichern]**.

   ![CTA hinzufügen](/help/assets/assets/add-cta.png)

1. Klicken Sie auf **[!UICONTROL Vorschau]** und wählen Sie **[!UICONTROL Veröffentlichen]** aus, um Ihre Vorlage zu veröffentlichen, sofern sie nicht schon zuvor veröffentlicht wurde.
1. Navigieren Sie zu dem Ordner, in dem diese Vorlage gespeichert ist, wählen Sie die Vorlage aus und klicken Sie auf ![Detailseite](/help/assets/assets/details-page-icon.svg) **[!UICONTROL Details]**.
1. Klicken Sie auf **[!UICONTROL Optionen kopieren]** und wählen Sie **[!UICONTROL Einbettungs-Code kopieren]** aus. Stellen Sie sicher, dass Sie die Vorlagenbilder in [!DNL AEM and Dynamic Media] veröffentlichen, um den Einbettungs-Code zu kopieren.

   ![Einbettungs-Code kopieren](/help/assets/assets/copy-options1.png)

   Nachstehend finden Sie ein Beispiel für einen Einbettungs-Code:

   ```json
    <div class="adobe-dynamicmedia-template-embed-container">
    <img id="<Image ID>>" src="<Image Source>>" alt="adobe dynamicmedia template" usemap="#adobe-dynamicmedia-template-map" width="800" height="300">
    <map name="adobe-dynamicmedia-template-map">
    <area shape="rect" coords="417,-60,817,340" href="https://business.adobe.com/products.html" alt="Layer with CTA" title="https://business.adobe.com/products.html" target="_blank">
    <area shape="rect" coords="6,206.57,129,231.43" href="https://business.adobe.com/products.html" alt="Layer with CTA" title="https://business.adobe.com/products.html" target="_blank">
    </map>
    </div>
   ```

1. Fügen Sie den kopierten Einbettungs-Code zur HTML-Datei Ihrer Site hinzu und führen Sie ihn in Ihrem Browser aus, um die Vorlage anzuzeigen.

Klicken Sie auf das CTA-Element in der Vorlage, um zur Zielseite zu navigieren.

Sehen Sie sich dieses Schritt-für-Schritt-Video an, um zu erfahren, wie Sie einer Vorlagenebene einen CTA-Link hinzufügen.

>[!VIDEO](https://video.tv.adobe.com/v/3457616)

## Wichtige Hinweise {#important-points-to-note}

* Nachdem Sie eine Vorlage mit parametrisierten Bildebenen für dynamische Aktualisierungen erstellt haben, stellen Sie sicher, dass die für zukünftige Aktualisierungen vorgesehenen Bilder dieselben Abmessungen wie die parametrisierten Bilder aufweisen. Dadurch passen die Bilder perfekt in die Ebenen, ohne Überlauf oder leere Räume. Derzeit unterstützt die Vorlage keine automatischen Anpassungen der Abmessungen, um Bilder in die Ebenen einzupassen.
* In einer Textebene werden keine Unterzeichenfolgen unterstützt. Der/die Benutzende kann auf die Teilzeichenfolge einer Textebene keine anderen Schrifteigenschaften anwenden.
* Die Unterstützung mehrerer [!DNL Dynamic Media]-Unternehmen ist bei [!DNL Dynamic Media]-Vorlagen derzeit nicht verfügbar.
* Beim Kopieren oder Verschieben zeigt die Zielauswahl alle Ordner an (einschließlich der nicht mit [!DNL Dynamic Media] synchronisierten Ordner). Außerdem werden derzeit nicht die Assets der [!DNL Dynamic Media]-Vorlage angezeigt (beides sind Einschränkungen des Zielselektors).
* Jeder Aktualisierungsvorgang für einen Ordner (z. B. Veröffentlichen oder Löschen) über den Abschnitt „Assets“ wirkt sich auf die in diesem Ordner verfügbaren [!DNL Dynamic Media]-Vorlagen aus.
* Der Papierkorb kann für [!DNL Dynamic Media]-Vorlagen nicht verwendet werden. Wenn ein Asset in den Papierkorb verschoben und dann wiederhergestellt wird, wird das Asset zwar in AEM wiederhergestellt, aber nicht in [!DNL Dynamic Media]. Dasselbe gilt für [!DNL Dynamic Media]-Vorlagen.

## Siehe auch

1. Erkunden von[[!DNL Dynamic Media] und seinen Funktionen](/help/assets/dynamic-media/dynamic-media.md)
1. Erkunden von[[!DNL Dynamic Media] mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md)