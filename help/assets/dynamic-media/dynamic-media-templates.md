---
title: Wie werden Vorlagen  [!DNL Dynamic Media] ?
description: Erfahren Sie, wie Sie  [!DNL Dynamic Media]  Vorlagen mit einem WYSIWYG-Vorlageneditor erstellen und mehrere Bilder und Textebenen enthalten können, um Banner und Flyer schnell zu erstellen und sie in nachgelagerten Anwendungen zu verwenden.
hide: true
role: User
exl-id: 07de648e-4ae2-4524-8e05-3cf10bb6006d
source-git-commit: f3dea4724f757090a504c3144e17fca7075acc52
workflow-type: tm+mt
source-wordcount: '3165'
ht-degree: 52%

---

# Vorlagen [!DNL Dynamic Media]{#dynamic-media-templates}

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

Erstellen Sie in Echtzeit anpassbare Vorlagen für Ihre Banner und Flyer mithilfe [!DNL Dynamic Media] Vorlagen, eines WYSIWYG-Vorlageneditors. Veröffentlichen Sie Ihre [!DNL Dynamic Media] Vorlage und verwenden Sie sie in nachgelagerten Anwendungen. Eine [!DNL Dynamic Media]-Vorlage enthält Bild- und Textebenen. Fügen Sie den Bild- und Textebenen der Vorlage Parameter hinzu und verwenden Sie [[!DNL Dynamic Media] URLs](https://experienceleague.adobe.com/de/docs/commerce-admin/content-design/wysiwyg/storage/catalog-urls-dynamic-media), um die Ebene neu zu positionieren, ihre Größe zu ändern und ihren Inhalt in Echtzeit zu aktualisieren.

Zu den Hauptfunktionen gehören:

* **[!DNL Dynamic Media]WYSIWYG-Vorlageneditor:** Sie anpassbare Banner mit Bild- und Textebenen.
* **Ebenenparametrisierung:** Definieren Sie dynamische Schlüssel-Wert-Paare für Ebenen, um Aktualisierungen in Echtzeit zu ermöglichen.
* Unterstützung für **[!DNL Dynamic Media]-URLs** Verwenden Sie [!DNL Dynamic Media]-URLs für Vorlagen und integrieren Sie personalisierte Werte aus Programmen von Erstanbietern oder Drittanbietern.
* **Steuerung der Ebenensichtbarkeit:** Blenden Sie Ebenen nach Bedarf dynamisch aus oder ein.
* **Intelligente Textgrößenänderung:** Passen Sie die Textgröße automatisch an bestimmte Bereiche an.

Zu den wichtigsten Vorteilen [!DNL Dynamic Media] Vorlagen gehören:

* **1:1-Optimierung von der Personalisierung:** Passen Sie Inhalte an Echtzeit-Kundensignale an.
* **Weniger manueller Aufwand:** Automatisieren und beschleunigen Sie die Inhaltserstellung und -verwaltung.
* **Sicherstellung konsistenter Omni-Channel-Erlebnisse:** Gewährleisten Sie die Markenkonsistenz kanalübergreifend.
* **Effektive Wiederverwendung von Inhalten:** Vermeiden Sie Inhalte für die einmalige Verwendung und skalieren Sie mit dynamischen, parametrisierten Vorlagen.
* **Minderung von Risiken:** Aktualisieren Sie Preise, Rabatte und Links in Echtzeit.
* **Verbesserung der Kundeninteraktion:** Fördern Sie interaktive, kontextuell relevante Erlebnisse.

>[!NOTE]
>
>Kunden mit Abonnements für die SKU für erweiterte Sicherheit können in diesem Cloud Services-Programm keine [!DNL Dynamic Media]-Funktionen, einschließlich [!DNL Dynamic Media]-Vorlagen, verwenden.

## Voraussetzungen{#prerequisites-for-dynamic-media-wysiwyg-template}

Sie müssen folgende Voraussetzungen erfüllen, um eine [!DNL Dynamic Media] Vorlage zu erstellen und ihre Versand-URL zu generieren:

1. Zugriff auf [!DNL Dynamic Media].
1. Auf der [!DNL Assets View] Homepage befindet sich ein Ordner in **[!UICONTROL Dynamic Media Assets]** zum Speichern der Vorlage. [Erstellen eines Ordners](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/assets-view/add-delete-assets-view) in ![Assets](/help/assets/assets/Asset-icon.svg)**[!UICONTROL Assets ]**, um diesen Ordner in**[!UICONTROL  Dynamic Media Assets ]**zu replizieren.
1. [Synchronisieren Sie die in Ihrer  [!DNL AEM Assets] -Instanz verfügbaren Bilder mit [!DNL Dynamic Media] , um sie für die Erstellung der Vorlage zu verwenden](/help/assets/dynamic-media/config-dm.md).
1. Veröffentlichen Sie die Bilder, die bei der Erstellung der Vorlage verwendet werden sollen, um nach der Erstellung die Versand-URL der Vorlage zu generieren. Die Versand-URL kann in nachgelagerten Anwendungen verwendet werden.
1. Um eine andere Schriftart als die standardmäßige [!UICONTROL Adobe Sans F2]-Schriftart in der Textebene der Vorlage zu verwenden, [ Sie die Schriftartdatei gleichzeitig in AEM und Dynamic Media hoch und ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/assets-view/publish-assets-to-aem-and-dm?lang=en#dynamic-media-publish-mode-set-to-upon-activation). [Folgende Schriftartformate werden unterstützt: AFM, OTF, PFB, PFM, FotoFont, TTC, TTF](https://experienceleague.adobe.com/en/docs/dynamic-media-classic/using/upload-publish/uploading-files#supported-asset-file-formats). Stellen Sie außerdem sicher[ dass ](/help/assets/reprocessing-assets-view.md) vorhandenen Schriftarten (erneut) verarbeitet werden, um sie zu verwenden. Weitere Informationen finden [ unter ](https://experienceleague.adobe.com/en/docs/dynamic-media-classic/using/support-files/fonts).<!--(On [!DNL Assets View] home page, click ![Assets](/help/assets/assets/Asset-icon.svg)**[!UICONTROL Assets]**, navigate to the font file location, select the font file one at a time and click ![Reprocess](/help/assets/assets/Refresh-docs.svg)**[!UICONTROL Reprocess]**)-->
1. Überprüfen Sie Folgendes in der Touch-optimierten Benutzeroberfläche:
   * Auf der **[!UICONTROL Seite &quot;[!DNL Dynamic Media] bearbeiten]** wird **[!UICONTROL [!DNL Dynamic Media]Synchronisierungsmodus]** der standardmäßig auf **[!UICONTROL Deaktiviert]** festgelegt ist, nicht auf alle AEM-Ordner angewendet (**[!UICONTROL Alle Inhalte synchronisieren]** ist deaktiviert). Weitere Informationen Sie unter [Konfigurieren von Dynamic Media Cloud Services](/help/assets/dynamic-media/config-dm.md).
   * **[!UICONTROL [!DNL Dynamic Media]Synchronisierungsmodus]** für den Zielordner oder Unterordner, in **[!UICONTROL Sie die Vorlage nach]** Erstellung speichern, auf Aktivieren für Unterordner) festgelegt. Weitere Informationen [ Sie unter  [!DNL Dynamic Media] ](/help/assets/dynamic-media/config-dm.md)Cloud Service konfigurieren.

## Erstellen [!DNL Dynamic Media] Vorlage{#how-to-create-dynamic-media-template}

Führen Sie die folgenden Schritte aus, um eine [!DNL Dynamic Media] Vorlage zu erstellen:
<!--
1. Navigate to your [!DNL Assets View] and [create a folder](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/assets-view/add-delete-assets-view) in ![Assets](/help/assets/assets/Asset-icon.svg)**[!UICONTROL Assets]**. The folder tree in ![Assets](/help/assets/assets/Asset-icon.svg)**[!UICONTROL Assets]** replicates in **[!UICONTROL Dynamic Media Assets]**. Save your [!DNL Dynamic Media] template in this [!UICONTROL Dynamic Media Assets] folder.
1. Select ![Assets](/help/assets/assets/Asset-icon.svg)**[!UICONTROL Assets]** and [upload and publish your images to [!DNL AEM] and [!DNL Dynamic Media] simultaneously](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/assets-view/publish-assets-to-aem-and-dm#dynamic-media-publish-mode-set-to-upon-activation) to use them in creating the template. Publishing images is required to generate the template's delivery URL, after creating the template. The delivery URL can be used in downstream applications.
1. [Execute these asset uploading and publishing steps](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/assets-view/publish-assets-to-aem-and-dm?lang=en#dynamic-media-publish-mode-set-to-upon-activation) to upload and publish a font file to AEM and Dynamic Media simultaneously to use it in creating the template. [!UICONTROL Adobe Sans F2] is the only default font available in the text layer. [The supported font file formats are, AFM, OTF, PFB, PFM, PhotoFont, TTC, TTF](https://experienceleague.adobe.com/en/docs/dynamic-media-classic/using/upload-publish/uploading-files#supported-asset-file-formats). Ensure to [reprocess](/help/assets/reprocessing-assets-view.md) the existing fonts to use them in creating the template (On [!DNL Assets View] home page, click ![Assets](/help/assets/assets/Asset-icon.svg)**[!UICONTROL Assets]**, navigate to the font file location, select the font file one at a time and click ![Reprocess](/help/assets/assets/Refresh-docs.svg)**[!UICONTROL Reprocess]**). See [Fonts](https://experienceleague.adobe.com/en/docs/dynamic-media-classic/using/support-files/fonts) to know more about fonts.
-->
1. [Erstellen einer leeren Arbeitsfläche](#create-a-canvas)
1. [Hinzufügen von Bildern zur Arbeitsfläche](#add-images-to-the-canvas)
1. [Hinzufügen von Textebenen zur Arbeitsfläche](#add-text-to-the-canvas)
1. [Bearbeiten oder Löschen einer Ebene](#edit-or-delete-a-layer)
1. [Parametrisieren von Ebenen](#parameterise-a-layer)

### Erstellen einer leeren Arbeitsfläche{#create-a-canvas}

Führen Sie die folgenden Schritte aus, um eine leere Arbeitsfläche zu erstellen:

1. Navigieren Sie zu [!DNL Assets View], wählen Sie **[!UICONTROL Dynamic Media Assets]** im linken Bereich aus und navigieren Sie zu Ihrem Ordner, um Ihre Vorlage in diesem Ordner zu speichern.

   ![Dynamic Media-Vorlagen](/help/assets/assets/DM-Assets1.png)

1. Wählen Sie **[!UICONTROL Vorlage erstellen]** aus. Das Dialogfeld **[!UICONTROL Neue Vorlage]** wird angezeigt.
   ![Erstellen dynamischer Vorlagen, die in Echtzeit angepasst werden können](/help/assets/assets/new-template.png)
   >[!NOTE]
   >
   >  Die Vorlage wird an dem Ort gespeichert, an dem Sie sie erstellen. Wählen Sie auf [!DNL Assets View] Startseite **[!UICONTROL Dynamic Media Assets]** und klicken Sie auf **[!UICONTROL Vorlage erstellen]**, um die Vorlage im Stammordner **[!UICONTROL Dynamic Media Assets]** zu speichern.

1. Geben Sie einen Namen für die Vorlage an, definieren Sie die Breite und Höhe der Arbeitsfläche und klicken Sie auf **[!UICONTROL Erstellen]**. Es wird eine leere Arbeitsfläche mit Menüoptionen auf beiden Seiten angezeigt, die zum Erstellen der Vorlage verwendet werden können. Bewegen Sie den Mauszeiger über die Menüoptionen, um deren QuickInfo anzuzeigen.
   ![In Echtzeit anpassbare Vorlage](/help/assets/assets/blank-canvas-page.png)

   >[!NOTE]
   >
   > Der zulässige Breiten- und Höhenbereich liegt zwischen 50 und 5.000.

**Menüoptionen im rechten Bereich:** Verwenden Sie diese Optionen, um der Arbeitsfläche die erforderlichen Bilder und Textebenen hinzuzufügen.

* ![DM-Vorlagen](/help/assets/assets/add-image.svg): Klicken Sie, um der Arbeitsfläche Bilder hinzuzufügen.
* ![Anpassbare Vorlagen](/help/assets/assets/add-text.svg): Klicken Sie, um der Arbeitsfläche Texte hinzuzufügen.
* ![Anpassbare Vorlagen](/help/assets/assets/show-layers-list.svg): Klicken Sie, um die Liste aller Ebenen (Bild und Text) auf der Arbeitsfläche anzuzeigen. Jedes Bild und jeder Text, das bzw. der der Arbeitsfläche hinzugefügt wird, wird als separate Ebene dargestellt.

**Menüoptionen im linken Bereich:** Sie diese Optionen für die folgenden allgemeinen Editor-Aktionen.

* ![DM-Vorlagen](/help/assets/assets/layer-selector.svg): Wählen Sie ![DM-Vorlagen](/help/assets/assets/layer-selector.svg) und klicken Sie auf eine Ebene auf der Arbeitsfläche, um sie auszuwählen.
* ![Vorlagen, die Anpassungen unterstützen](/help/assets/assets/bring-forward.svg): Klicken Sie auf ![Vorlagen, die Anpassungen unterstützen](/help/assets/assets/bring-forward.svg) oder verwenden Sie den Tastaturbefehl **Strg** + **]** (Windows) oder **Cmd** + **]** (Mac), um eine ausgewählte Ebene nach vorne zu bringen.
* ![So erstellen Sie eine Vorlage, die einfach angepasst werden kann](/help/assets/assets/send-backward.svg): Klicken Sie auf ![So erstellen Sie eine Vorlage, die einfach angepasst werden kann](/help/assets/assets/send-backward.svg) oder verwenden Sie den Tastaturbefehl **Strg** + **[** (Windows) oder **Cmd** + **[** (Mac), um eine ausgewählte Ebene rückwärts zu senden.
* ![Erstellen einer Vorlage, die sofort angepasst werden kann](/help/assets/assets/undo.svg): Klicken Sie auf ![Erstellen einer Vorlage, die sofort angepasst werden kann](/help/assets/assets/undo.svg) oder verwenden Sie den Tastaturbefehl **Strg** + **Z** (Windows) oder **Cmd** + **Z** (Mac), um die letzte Aktion rückgängig zu machen.
* ![Vorlage, um Banner schnell zu erstellen](/help/assets/assets/redo.svg): Klicken Sie auf ![Vorlage, um Banner schnell zu erstellen](/help/assets/assets/redo.svg) oder verwenden Sie den Tastaturbefehl **Strg** + **Y** (Windows) oder **Cmd** + **Y** (Mac), um die letzte Aktion wiederherzustellen.
* ![Vorlage, um schnell Flyer zu erstellen](/help/assets/assets/zoom-in.svg): Klicken Sie auf ![Vorlage, um schnell Flyer zu erstellen](/help/assets/assets/zoom-in.svg) oder verwenden Sie den Tastaturbefehl **Strg** + **+** (Windows) oder **Cmd** + **+** (Mac), um die Arbeitsfläche zu zoomen.
* ![Vorlage, um Banner schnell zu erstellen](/help/assets/assets/Zoom-out.svg): Klicken Sie auf ![Vorlage, um Banner schnell zu erstellen](/help/assets/assets/Zoom-out.svg) oder verwenden Sie den Tastaturbefehl **Strg** + **-** (Windows) oder **Cmd** + **-** (Mac), um die Arbeitsfläche auszuzoomen.
* Drücken Sie die **Rücktaste** oder **Entf**, um die ausgewählte Ebene zu löschen, wenn kein Text oder keine Eigenschaft bearbeitet wird.

Klicken Sie auf ![Vorlage, um Flyer schnell zu erstellen](/help/assets/assets/show-layers-list.svg) und wählen Sie weitere Optionen (![](/help/assets/assets/three-dots.svg)) auf der Arbeitsflächen-Ebene aus, um die Arbeitsflächen-Dimensionen jederzeit beim Erstellen der Vorlage zu bearbeiten.
![](/help/assets/assets/edit-canvas1.png)

>[!NOTE]
>
> Vorlagen lassen maximal 20 Ebenen zu, einschließlich der Arbeitsfläche.

### Hinzufügen von Bildern zur Arbeitsfläche{#add-images-to-the-canvas}

Führen Sie die folgenden Schritte aus, um der Arbeitsfläche Bilder hinzuzufügen:

1. Klicken Sie auf ![Banner im Handumdrehen erstellen](/help/assets/assets/add-image.svg), um das Bedienfeld [Asset-Auswahl](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/manage/asset-selector/overview-asset-selector) zu öffnen. Das Bedienfeld zeigt die Bilder in Ihrer AEM Assets-Instanz an, die mit [!DNL Dynamic Media] synchronisiert werden.
1. Durchsuchen Sie das Bedienfeld oder verwenden Sie Keywords in der Suchleiste, um nach einem bestimmten Bild zu suchen.
1. Ziehen Sie ein Bild per Drag-and-Drop auf die Arbeitsfläche, um es zu verwenden. Zum Ändern der Größe oder Neupositionieren einer Ebene auf der Arbeitsfläche gehen Sie zum [**[!UICONTROL Bedienfeld „Eigenschaften“]**](#reposition-resize-delete-a-layer).
   ![Erstellen eines Banners innerhalb von Sekunden](/help/assets/assets/add-image-to-canvas.png)

### Hinzufügen von Textebenen zur Arbeitsfläche{#add-text-to-the-canvas}

Führen Sie die folgenden Schritte aus, um der Arbeitsfläche Textebenen hinzuzufügen:

1. Klicken Sie auf ![Schnelles Erstellen neuer Banner](/help/assets/assets/add-text.svg), um der Arbeitsfläche eine Textebene hinzuzufügen und das Bedienfeld „Eigenschaften“ zu öffnen.
1. Wählen Sie die Ebene aus und klicken Sie zum Aktualisieren auf den Text.
1. Wählen Sie **[!UICONTROL Smart Text Resize]** im Bedienfeld Eigenschaften aus, um die Textlänge und Schriftgröße automatisch so anzupassen, dass sie in den vorgesehenen Bereich optimal passen.
   ![Optimal anpassbare Banner](/help/assets/assets/add-text-layer.png)

Zum Neupositionieren, Ändern der Größe, Drehen oder Löschen der Ebene gehen Sie zum [**[!UICONTROL Bedienfeld „Eigenschaften“]**](#reposition-resize-delete-a-layer). Formatieren Sie Ihren Text in der erforderlichen Schriftart, Größe, Farbe, Stil und Ausrichtung (in der Ebene), indem Sie deren Werte in den entsprechenden Feldern unter dem Abschnitt **[!UICONTROL Text]** des Bedienfelds ändern. Das Feld **[!UICONTROL Schriftfamilie]** zeigt die Standardschriftart [!UICONTROL Adobe Sans F2], die neu verarbeiteten vorhandenen Schriftarten sowie die neu hochgeladenen und veröffentlichten Schriftarten an. Weitere Informationen finden Sie unter [ 5 ](#prerequisites-for-dynamic-media-wysiwyg-template) Abschnitt „Bevor Sie beginnen“.

### Bearbeiten oder Löschen einer Ebene {#edit-or-delete-a-layer}

Führen Sie die folgenden Schritte aus, um eine Arbeitsflächenebene zu bearbeiten oder zu löschen:

1. Klicken Sie auf ![Vorlagen mit Unterstützung für dynamische Aktualisierungen](/help/assets/assets/show-layers-list.svg) und wählen Sie die Ebene entweder auf der Arbeitsfläche oder über die Liste „Ebenen“ aus.
1. Klicken Sie auf **[!UICONTROL Weitere Optionen]** (![Vorlagen mit Unterstützung für Echtzeitaktualisierungen](/help/assets/assets/three-dots.svg)), um die Ebene zu bearbeiten oder zu löschen.
1. Klicken Sie auf **[!UICONTROL Löschen]**, um die Ebene zu löschen.
1. Klicken Sie auf **[!UICONTROL Bearbeiten]**, um die Ebene mithilfe des [**[!UICONTROL Bedienfelds „Eigenschaften“]**](#reposition-resize-delete-a-layer) zu bearbeiten.
   ![Schnelle Bannererstellung](/help/assets/assets/dm-templates/edit-delete-layer.png)

### Bedienfeld „Eigenschaften“{#properties-panel}

So navigieren Sie zum Bedienfeld „Eigenschaften“ einer Ebene:

1. Klicken Sie auf ![Schnelle Inhaltserstellung](/help/assets/assets/show-layers-list.svg).
1. Wählen Sie die Ebene aus der Liste aus.

In diesem Bedienfeld werden die Position des Mittelpunkts der Ebene auf der Arbeitsflächenebene (X- und Y-Werte) und die Abmessungen (Breite und Höhe) der Ebene zusammen mit Optionen für die Textformatierung angezeigt.

![Schnelle Inhaltserstellung](/help/assets/assets/properties-panel.png)

Wählen Sie im Bedienfeld „Eigenschaften“ einer Ebene eine andere Ebene auf der Arbeitsfläche aus, um zum zugehörigen Bedienfeld „Eigenschaften“ zu navigieren.


#### Neupositionieren, Ändern der Größe, Drehen oder Löschen einer Ebene{#reposition-resize-delete-a-layer}

Sehen Sie sich die folgenden allgemeinen Ebenenbearbeitungsaktionen an, um eine Text- oder Bildebene zu bearbeiten:

* **Ebene neu positionieren:** Ziehen Sie die Ebene, um sie an eine beliebige Stelle auf der Arbeitsfläche zu verschieben. Diese Aktion aktualisiert die X- und Y-Werte im Bedienfeld „Eigenschaften“.
* **Größe der Ebene ändern:** Wählen Sie die Ebene aus und ziehen Sie die Kantengriffe, um die Größe zu ändern. Diese Aktion aktualisiert die Werte „W“ (Breite) und „H“ (Höhe) im Bedienfeld „Eigenschaften“.
* **Ebene drehen:** Ziehen Sie den quadratischen, vertikal über der Ebene platzierten Griff, um sie ihren Mittelpunkt zu drehen. Diese Aktion aktualisiert die Werte der Winkel im Bedienfeld „Eigenschaften“.
* **Ebene löschen:** Drücken Sie die **Rücktaste** oder die **Löschtaste** und klicken Sie dann auf **[!UICONTROL Bestätigen]**, um eine ausgewählte Ebene zu löschen.

#### Optionen für die Textformatierung{#text-formatting-options-on-properties-panel}

Formatieren Sie Ihren Text in die erforderliche Schriftart, Größe, Farbe, Stil, Ausrichtung (innerhalb der Ebene), indem Sie deren Werte in den entsprechenden Feldern unter dem Abschnitt **[!UICONTROL Text]** des Bedienfelds ändern.
Stellen Sie sicher, **[!UICONTROL einzuschließen (Smart Text Resize]**. [!UICONTROL Smart Text Resize] arbeitet mit dem [Copyfit](https://experienceleague.adobe.com/de/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/text-formatting/r-copy-fitting)-Algorithmus, um Text im Textbereich optimal auszufüllen, Textüberlauf zu verhindern und zusätzlichen Platz am unteren Rand des Textes zu minimieren.

![Inhaltserstellung im Handumdrehen](/help/assets/assets/smart-text-resize.png)

### Parametrisieren von Ebenen {#parameterise-a-layer}

Nachdem Sie eine Vorlage mit mehreren Bild- und Textebenen erstellt haben, parametrisieren Sie die ausgewählten Ebenen. Wenn eine Ebene oder ihre Eigenschaft parametrisiert wird, erhält sie ein Schlüssel-Wert-Paar (auch als Parameter bezeichnet). Dieser Parameter kann in die Vorlagen-URL aufgenommen werden, um Position, Größe oder Inhalt der Ebene in Echtzeit zu aktualisieren, wodurch die Vorlage in kürzester Zeit angepasst wird.

So parametrisieren Sie eine Ebene:

1. Klicken Sie auf ![Sofortige Inhaltserstellung](/help/assets/assets/show-layers-list.svg), wählen Sie eine Ebene aus und klicken Sie auf **[!UICONTROL Parameter]**. Das Bedienfeld **[!UICONTROL Parameter]** wird angezeigt.
1. Schalten Sie **[!UICONTROL Parameter einschließen]** um, um eine Eigenschaft zu parametrisieren. Siehe [Option für das Bedienfeld „Parameter](#parameterisation-options-or-allowed-parameters), um das Verhalten der Eigenschaft nach der Parametrisierung zu erfahren.
1. **Optional:** Benennen Sie den Parameter um. Ein Parametername hat einen Ebenennamen, gefolgt von einem Suffix. Für eine ausgewählte Ebene verwenden alle parametrisierten Eigenschaften denselben Ebenennamen, gefolgt von einem variierenden Suffix. Benennen Sie den Ebenennamen um, indem Sie der semantischen Namenskonvention folgen, sodass bei Aufnahme des Parameters in die URL der Parametername selbst den Inhalt oder den Zweck der Ebene erklärt.
1. Klicken Sie auf **[!UICONTROL Speichern]**.
   ![Sofortige Inhaltserstellung](/help/assets/assets/parameterise-a-layer.png)
Um zwischen dem Bedienfeld „Parameter“ eines Bildes und der Textebene zu wechseln, wählen Sie die Ebene auf der Arbeitsfläche aus und klicken Sie auf **[!UICONTROL Parameter]**.

#### Option des Bedienfelds „Parameter“ {#parameterisation-options-or-allowed-parameters}

Die parametrisierten Eigenschaften können als URL-Parameter in die Vorlagen-URL aufgenommen werden, um die Vorlage mithilfe der URL in Echtzeit zu bearbeiten.

**Bildparameter:**

**[!UICONTROL X]:** Einfügen, um die Ebene horizontal entlang ihrer Mittellinie parallel zur X-Achse der Vorlagenebene zu verschieben, indem der Parameterwert in der URL geändert wird.
**[!UICONTROL Y]:** Einfügen, um die Ebene vertikal entlang ihrer Mittellinie parallel zur Y-Achse der Vorlagenebene zu verschieben, indem der Parameterwert in der URL geändert wird.
**[!UICONTROL Breite]:** Sie ein, um die Breite der Ebene anzupassen, indem Sie den Wert des Parameters in der URL ändern.
**[!UICONTROL Höhe]:** Sie ein, um die Höhe der Ebene anzupassen, indem Sie den Parameterwert in der URL ändern.
**[!UICONTROL Ausblenden]:** Einschließen, um die Ebene in der Vorlage mit 0 (Anzeigen) und 1 (Ausblenden) ein- oder auszublenden.
**[!UICONTROL Source]:** Include, um das Ebenenbild durch ein neues Bild zu ersetzen, indem der Bildpfad im Parameterwert in der URL geändert wird.

**Textformatierungsparameter:**

Schließen Sie die folgenden Parameter ein, um den Text, seine Schriftart, Farbe und Größe aus der URL zu bearbeiten, indem Sie die Werte des Parameters in der URL aktualisieren.

**[!UICONTROL Text]:** Include , um Text aus der URL zu aktualisieren.
**[!UICONTROL Schriftfamilie]:** Include , um die Schriftart des Textes in der URL zu aktualisieren.
**[!UICONTROL Schriftgröße]:** Einschließen, um die Schriftgröße des Textes in der URL zu aktualisieren.
**[!UICONTROL Textfarbe]:** Einfügen, um die Schriftfarbe des Textes in der URL zu aktualisieren.

### Gruppieren von Ebenen für die gleichzeitige Steuerung Ihrer Sichtbarkeit{#group-layers}

Eine weitere Möglichkeit, Ihre Vorlagen flexibel zu halten, besteht in der Verwendung eines einzelnen Parameternamens, um mehrere Ebenen zu steuern. Diese Strategie ist hilfreich für den Parameter „Sichtbarkeit“ (Ebenen ausblenden oder anzeigen), um das Design oder die Grafiken aus einer einzigen Vorlage zu aktualisieren.

Führen Sie diese Schritte aus, um den Ausblendungsparametern (![schnelle Inhaltserstellung](/help/assets/assets/Visibility-icon.svg)) mehrerer Ebenen denselben Namen zuzuweisen, sodass Sie sie gleichzeitig ausblenden oder anzeigen können.

1. Navigieren Sie zum [**[!UICONTROL Bedienfeld „Eigenschaften“]**](#parameterise-a-layer) einer Ebene.
1. Schalten Sie den Parameter **[!UICONTROL Ausblenden]** ein, falls er nicht zuvor parametrisiert wurde.
1. **Optional:** Benennen Sie den Parameter **[!UICONTROL Ausblenden]** um.
1. Kopieren Sie den **[!UICONTROL Hide]**-Parameternamen.
1. Wechseln Sie zum Bedienfeld „Parameter“ anderer Ebenen, indem Sie sie auf der Arbeitsfläche auswählen und ihren Parameter **[!UICONTROL Ausblenden]** umschalten, falls er nicht parametrisiert ist.
1. Ersetzen Sie den Namen **[!UICONTROL Parameter ausblenden]** durch den kopierten Namen.
1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Ebenen zu gruppieren.
1. Führen Sie Schritt 3 und dann Schritt 4 im Abschnitt [**[!UICONTROL Vorschau und Veröffentlichung]**](#preview-and-publish-template-and-copy-template-deliver-url) aus, um Ihre Änderungen anzuzeigen.

## Anzeigen der Vorlage in der Vorschau und Veröffentlichen der Vorlage zum Kopieren der Bereitstellungs-URL{#preview-and-publish-template-and-copy-template-deliver-url}

Führen Sie die folgenden Schritte aus, um die Vorlage in der Vorschau anzuzeigen und zu veröffentlichen und die Bereitstellungs-URL zu kopieren:

1. Klicken Sie auf der Seite „Arbeitsfläche“ auf **[!UICONTROL Vorschau]**. Sie können auch zu **[!UICONTROL Assets-Ansicht]** **>** **[!UICONTROL Dynamic Media-Assets]** **** navigieren, Ihre Vorlage suchen und auswählen und dann **** auf **** Vorlage bearbeiten **** sowie auf **[!UICONTROL Vorschau]** klicken. Auf der Seite „Vorschau“ werden die Vorlage, ihre Parameter (parametrisierte Ebenen und Eigenschaften), der Veröffentlichungsstatus und die Option **[!UICONTROL Veröffentlichen]** angezeigt.
1. Wählen Sie Parameter aus dem Bedienfeld **[!UICONTROL Vorlagenparameter]** aus, um ihre Werte zu bearbeiten und den Inhalt, die Größe, die Position oder die Textformatierung der entsprechenden Vorlagenebene in der Vorschau sofort zu aktualisieren. Zum Beispiel:
   1. Auswählen einer Textebene und Bearbeiten ihres Textes oder
   1. Wählen Sie eine Bildebene aus, klicken Sie auf ![Inhalt spontan erstellen](/help/assets/assets/add-image.svg), wählen Sie ein Bild aus der Asset-Auswahl aus und klicken Sie auf **[!UICONTROL Aktualisieren]**.

   Die Vorlage wird sofort aktualisiert, wobei der bearbeitete Text angezeigt und das vorherige Bild durch das neue Bild ersetzt wird. Darüber hinaus spiegelt der Bildparameterwert den neuen Bildpfad wider. Auf ähnliche Weise können Sie die Größe einer Ebene ändern, indem Sie ihre Werte anpassen. Die Änderungen werden dann in Echtzeit auf die Vorlage angewendet.
1. Wählen Sie den **[!UICONTROL Ausblenden]** für [gruppierte Ebenen](#group-layers) aus der Liste aus, um sie zusammen in der Vorlage ein- oder auszublenden.
1. **Optional:** Ändern Sie den Wert des Parameters **[!UICONTROL Ausblenden]** von 0 auf 1 oder umgekehrt und klicken Sie auf **[!UICONTROL Aktualisieren]**, um die Änderungen anzuzeigen. Ebenen mit demselben Parameter **[!UICONTROL Ausblenden]** werden zusammen ausgeblendet oder angezeigt. Auf ähnliche Weise können Sie die Sichtbarkeit der Ebenen über die URL steuern.

   ![Inhalt spontan erstellen](/help/assets/assets/dm-templates-publish-status.png)
Sie können auch **[!UICONTROL Alle Parameter einbeziehen]** umschalten, um alle angezeigten Parameterwerte zu bearbeiten und die Aktualisierungen in der Vorlagenvorschau anzuzeigen.
   <br>
1. Um die Vorlage auf der Vorschauseite zu veröffentlichen, klicken Sie auf **[!UICONTROL Veröffentlichen]** und bestätigen Sie die Veröffentlichung. Eine **[!UICONTROL Veröffentlichen abgeschlossen]** wird angezeigt und der Veröffentlichungsstatus wird in &quot;**[!UICONTROL &quot;]**.

### Kopieren der Bereitstellungs-URL

Die ausgewählten Parameter auf der Seite **[!UICONTROL Vorschau]** werden zu den URL-Parametern in der Vorlagen-URL.

Stellen Sie sicher, dass die Bilder in der Vorlage bereits in AEM und Dynamic Media veröffentlicht wurden, um die Bereitstellungs-URL der Vorlage zu generieren.

Führen Sie die folgenden Schritte aus, um die Versand-URL der Vorlage zu kopieren:

1. Klicken Sie auf **[!UICONTROL URL kopieren]**. Das Dialogfeld **[!UICONTROL URL kopieren]** wird angezeigt. Wählen Sie die angezeigte URL aus und kopieren Sie sie. Der erste Parameter in der URL beginnt nach einem Fragezeichen **([!UICONTROL ?])** und ein Schlüssel-Wert-Paar beginnt mit **[!UICONTROL $]** und endet mit **[!UICONTROL &amp;]**. Schlüssel und Wert werden durch ein Gleichheitszeichen **([!UICONTROL =])** getrennt, wobei der Schlüssel links und der Wert rechts liegen.
1. Fügen Sie diese URL in Ihre Browser-Registerkarte ein und sehen Sie sich Ihre Live-Vorlage an. Passen Sie die Vorlage in Echtzeit an, indem Sie den erforderlichen Parameterwert (Schlüsselwert) in der URL direkt aktualisieren, wie in [Schritt 2](#preview-and-publish-template-and-copy-template-deliver-url) des Abschnitts **Vorschau und Veröffentlichung** gezeigt.
1. Verwenden Sie diese URL für das schnelle Merchandising Ihrer Produkte oder Services. Sie können diese URL für Ihre Kundschaft freigeben oder in Ihre Website oder eine nachgelagerte Drittanbieteranwendung integrieren, um das Banner anzuzeigen und Aktualisierungen daran in Echtzeit vorzunehmen, sodass die laufenden Angebote widergespiegelt werden.

In diesem Video erfahren Sie, wie Sie Schritt für Schritt eine [!DNL Dynamic Media] erstellen.
>[!VIDEO](https://video.tv.adobe.com/v/3443281)

## Vornehmen von Aktualisierungen an der Vorlage in Echtzeit über die URL{#update-the-template-from-the-url}

Das direkte Bearbeiten von Parametern in der URL kann mühsam sein. Zur Vereinfachung können Sie wie folgt vorgehen:

1. Kopieren Sie die URL und fügen Sie sie in einen Editor ein.
1. Verwenden Sie Befehlstaste+F (Mac) bzw. Strg+F (Windows), um die Parameterwerte zu finden und zu bearbeiten. Beispiel:
   * Suchen und Ersetzen von Bildpfaden für Bildebenen.
   * Finden Sie die [parametrisierten) Koordinaten, Breite und Höhe ](#parameterise-a-layer) Ebene, um ihre Werte anzupassen.
   * Bearbeiten Sie Text, Schriftart, Farbe, Größe oder Ausrichtung für Textebenen.
   * Ändern Sie die Sichtbarkeitswerte zwischen 0 und 1.

Fügen Sie diese aktualisierte URL in Ihren Browser ein, um die Änderungen anzuzeigen.

## Bearbeiten der Vorlage{#edit-the-template}

Gehen Sie wie folgt vor, um die Vorlage zu bearbeiten:

1. Klicken Sie [!DNL Assets view] auf **[!UICONTROL Dynamic Media Assets]**.
2. Navigieren Sie zum Speicherort der Vorlage.
3. Wählen Sie die Vorlage aus.
4. Klicken Sie auf **[!UICONTROL Vorlage bearbeiten]**. Auf der Vorlagenarbeitsfläche werden die Vorlage und die Liste aller zugehörigen Ebenen im Bedienfeld „Ebenen“ angezeigt. Bearbeiten Sie Ihre Vorlage gemäß Ihren Anforderungen.

## Fügen Sie einen Link für Aktionsaufrufe (CTA) zu Ihrer Vorlagenebene hinzu{#add-CTA-in-dynamic-media-templates}

Wandeln Sie eine Bild- oder Textebene Ihrer [!DNL Dynamic Media] in einen Hyperlink um, indem Sie einen CTA-Link hinzufügen, der Benutzer zu einer Zielseite weiterleitet.

Führen Sie die folgenden Schritte aus, um einer Ebene einen CTA-Link hinzuzufügen:

1. Navigieren Sie zu Ihrem Vorlagenspeicherort, wählen Sie die Vorlage aus und klicken Sie auf ![Bearbeiten](/help/assets/assets/edit-pen-icon.svg) **[!UICONTROL Vorlage bearbeiten]**. Die Vorlage wird auf der Arbeitsfläche angezeigt.
1. Wählen Sie die Vorlagenebene aus und [navigieren Sie zum Eigenschaften](#edit-or-delete-a-layer), um ihr einen CTA-Link hinzuzufügen.
1. Wählen Sie im Bedienfeld Eigenschaften die Option **[!UICONTROL CTA hinzufügen]**, geben Sie die Ziel-URL in das Feld **[!UICONTROL URL]** ein und klicken Sie auf **[!UICONTROL Speichern]**.

   ![CTA hinzufügen](/help/assets/assets/add-cta.png)

1. Klicken Sie auf **[!UICONTROL Vorschau]** und wählen Sie **[!UICONTROL Veröffentlichen]** aus, um Ihre Vorlage zu veröffentlichen, falls sie nicht zuvor veröffentlicht wurde.
1. Navigieren Sie zu dem Ordner, in dem diese Vorlage gespeichert ist, wählen Sie diese Vorlage aus und klicken Sie auf ![Detailseite](/help/assets/assets/details-page-icon.svg) **[!UICONTROL Details]**.
1. Klicken Sie auf **[!UICONTROL Optionen kopieren]** und wählen Sie **[!UICONTROL Einbettungs-Code kopieren]** aus. Stellen Sie sicher, dass Sie die Vorlagenbilder in [!DNL AEM and Dynamic Media] veröffentlichen, um den Einbettungs-Code zu kopieren.

   ![Einbettungs-Code kopieren](/help/assets/assets/copy-options1.png)

   Im Folgenden finden Sie ein Beispiel für den Einbettungs-Code:

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

Sehen Sie sich dieses Video Schritt für Schritt an, um zu erfahren, wie Sie einen CTA-Link zu einer Vorlagenebene hinzufügen.

>[!VIDEO](https://video.tv.adobe.com/v/3457616)

## Wichtige Hinweise {#important-points-to-note}

* Nachdem Sie eine Vorlage mit parametrisierten Bildebenen für dynamische Aktualisierungen erstellt haben, stellen Sie sicher, dass die für zukünftige Aktualisierungen vorgesehenen Bilder dieselben Abmessungen wie die parametrisierten Bilder aufweisen. Dadurch passen die Bilder perfekt in die Ebenen, ohne Überlauf oder leere Räume. Derzeit unterstützt die Vorlage keine automatischen Anpassungen der Abmessungen, um Bilder in die Ebenen einzupassen.
* In einer Textebene werden keine Unterzeichenfolgen unterstützt. Benutzende können auf die Unterzeichenfolge einer Textebene keine anderen Schrifteigenschaften anwenden.
* Die Unterstützung mehrerer [!DNL Dynamic Media] Unternehmen ist derzeit nicht mit [!DNL Dynamic Media] Vorlagen verfügbar.
* Bei Kopieren oder Verschieben zeigt der Zielselektor alle Ordner an (einschließlich nicht [!DNL Dynamic Media] synchronisierter Ordner). Außerdem werden derzeit nicht die Assets der [!DNL Dynamic Media]-Vorlage angezeigt (beides sind Einschränkungen der Zielauswahl).
* Jeder Aktualisierungsvorgang eines Ordners (z. B. Veröffentlichen oder Löschen) aus dem Abschnitt Assets wirkt sich auf die in diesem Ordner verfügbaren [!DNL Dynamic Media] aus.
* Papierkorb funktioniert nicht für [!DNL Dynamic Media] Vorlagen. Wenn ein Asset in den Papierkorb verschoben und dann wiederhergestellt wird, wird das Asset in AEM wiederhergestellt, jedoch nicht in [!DNL Dynamic Media]. Dasselbe gilt für [!DNL Dynamic Media] Vorlagen.

## Siehe auch

1. Erkunden Sie [[!DNL Dynamic Media] und seine Möglichkeiten](/help/assets/dynamic-media/dynamic-media.md)
1. Erkunden Sie [[!DNL Dynamic Media] mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md)