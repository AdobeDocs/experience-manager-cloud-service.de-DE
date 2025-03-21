---
title: Wie werden Dynamic Media-Vorlagen verwaltet?
description: Erfahren Sie, wie Sie Dynamic Media-Vorlagen mit einem WYSIWYG-Vorlageneditor erstellen und mehrere Bilder und Textebenen einschließen, um Banner und Flyer schnell zu erstellen und in nachgelagerten Programmen zu verwenden.
hide: true
role: User
exl-id: 07de648e-4ae2-4524-8e05-3cf10bb6006d
source-git-commit: c82f84fe99d8a196adebe504fef78ed8f0b747a9
workflow-type: tm+mt
source-wordcount: '2834'
ht-degree: 99%

---

# Dynamic Media-Vorlagen{#dynamic-media-templates}

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

Erstellen Sie Dynamic Media-Vorlagen mit einem WYSIWYG-Vorlageneditor und schließen Sie mehrere Bilder und Textebenen ein, um Banner und Flyer schnell zu erstellen und in nachgelagerten Anwendungen zu verwenden. Sie können auch Parameter zu den Bildern und Textebenen in der Vorlage hinzufügen und [Dynamic Media-URLs](https://experienceleague.adobe.com/de/docs/commerce-admin/content-design/wysiwyg/storage/catalog-urls-dynamic-media) verwenden, um die Werte für diese Ebenen in Echtzeit zu aktualisieren.

Zu den Hauptfunktionen gehören:

* **Dynamic Media WYSIWYG-Vorlageneditor:** Erstellen Sie anpassbare Banner mit Bild- und Textebenen.
* **Ebenenparametrisierung:** Definieren Sie dynamische Schlüssel-Wert-Paare für Ebenen, um Aktualisierungen in Echtzeit zu ermöglichen.
* **Dynamic Media-URL-Unterstützung:** Verwenden Sie Dynamic Media-URLs für Vorlagen und integrieren Sie personalisierte Werte aus Anwendungen von Erst- oder Drittanbietern.
* **Steuerung der Ebenensichtbarkeit:** Blenden Sie Ebenen nach Bedarf dynamisch aus oder ein.
* **Intelligente Textgrößenänderung:** Passen Sie die Textgröße automatisch an bestimmte Bereiche an.

Zu den wichtigsten Vorteilen von Dynamic Media-Vorlagen gehören:

* **1:1-Optimierung von der Personalisierung:** Passen Sie Inhalte an Echtzeit-Kundensignale an.
* **Weniger manueller Aufwand:** Automatisieren und beschleunigen Sie die Inhaltserstellung und -verwaltung.
* **Sicherstellung konsistenter Omni-Channel-Erlebnisse:** Gewährleisten Sie die Markenkonsistenz kanalübergreifend.
* **Effektive Wiederverwendung von Inhalten:** Vermeiden Sie Inhalte für die einmalige Verwendung und skalieren Sie mit dynamischen, parametrisierten Vorlagen.
* **Minderung von Risiken:** Aktualisieren Sie Preise, Rabatte und Links in Echtzeit.
* **Verbesserung der Kundeninteraktion:** Fördern Sie interaktive, kontextuell relevante Erlebnisse.

>[!NOTE]
>
>Kundinnen und Kunden mit Abonnements für die SKU für erweiterte Sicherheit können in diesem Cloud Service-Programm keine Dynamic Media-Funktionen, einschließlich Dynamic Media-Vorlagen, verwenden.

## Voraussetzungen{#prerequisites-for-dynamic-media-wysiwyg-template}

Um eine Dynamic Media-Vorlage zu erstellen, benötigen Sie Folgendes:

1. Zugriff auf Dynamic Media.
1. [Die in Ihrer AEM Assets-Instanz verfügbaren Bilder müssen mit Dynamic Media synchronisiert worden sein, um sie für die Erstellung der Vorlage verwenden zu können](/help/assets/dynamic-media/config-dm.md).
1. Überprüfen Sie Folgendes in der Touch-optimierten Benutzeroberfläche:
   * Auf der Seite **[!UICONTROL Dynamic Media-Konfiguration bearbeiten]** wird **[!UICONTROL Synchronisierungsmodus für Dynamic Media]**, der auf **[!UICONTROL Standardmäßig deaktiviert]** festgelegt ist, nicht auf alle AEM-Ordner angewendet (**[!UICONTROL Alle Inhalte synchronisieren]** ist deaktiviert). Weitere Informationen Sie unter [Konfigurieren von Dynamic Media Cloud Services](/help/assets/dynamic-media/config-dm.md).
   * **[!UICONTROL Synchronisierungsmodus für Dynamic Media]** ist für den Zielordner oder den Unterordner, in dem Sie die Vorlage nach der Erstellung speichern, auf **[!UICONTROL Für Unterordner aktivieren]** festgelegt. Weitere Informationen finden Sie unter [Konfigurieren von Dynamic Media Cloud Services](/help/assets/dynamic-media/config-dm.md).

## Erstellen einer Dynamic Media-WYSIWYG-Vorlage{#how-to-create-dynamic-media-wysiwyg-template}

Um eine Dynamic Media-Vorlage zu erstellen, führen Sie die folgenden Schritte aus:

1. [Erstellen einer leeren Arbeitsfläche](#create-a-canvas)
1. [Hinzufügen von Bildern zur Arbeitsfläche](#add-images-to-the-canvas)
1. [Hinzufügen von Textebenen zur Arbeitsfläche](#add-text-to-the-canvas)
1. [Bearbeiten oder Löschen einer Ebene](#edit-or-delete-a-layer)
1. [Parametrisieren von Ebenen](#parameterise-a-layer)

### Erstellen einer leeren Arbeitsfläche{#create-a-canvas}

Führen Sie die folgenden Schritte aus, um eine leere Arbeitsfläche zu erstellen:

1. Navigieren Sie zur Assets-Ansicht und klicken Sie im linken Bedienfeld auf **[!UICONTROL Dynamic Media-Assets]**.

   ![Dynamic Media-Vorlagen](/help/assets/assets/DM-Assets1.png)

1. Klicken Sie auf **[!UICONTROL Vorlage erstellen]**, um die Vorlage unter Dynamic Media-Assets zu speichern, oder navigieren Sie zu einem Ordner und klicken Sie auf **[!UICONTROL Vorlage erstellen]**, um die Vorlage in diesem Ordner zu speichern. Das Dialogfeld **[!UICONTROL Neue Vorlage]** wird angezeigt.
   ![So erstellen Sie dynamische Vorlagen, die in Echtzeit angepasst werden können:](/help/assets/assets/new-template.png)
Zum [Erstellen eines Ordners](/help/assets/add-delete-assets-view.md) unter **[!UICONTROL Dynamic Media-Assets]** müssen Sie einen Ordner unter **[!UICONTROL Assets]** erstellen. Die Ordnerstruktur unter **[!UICONTROL Assets]** wird unter **[!UICONTROL Dynamic Media-Assets]** repliziert.
1. Geben Sie einen Namen für die Vorlage an, definieren Sie die Breite und Höhe der Arbeitsfläche und klicken Sie auf **[!UICONTROL Erstellen]**. Es wird eine leere Arbeitsfläche mit Menüoptionen auf beiden Seiten angezeigt, die zum Erstellen der Vorlage verwendet werden können. Bewegen Sie den Mauszeiger über die Menüoptionen, um deren QuickInfo anzuzeigen.
   ![In Echtzeit anpassbare Vorlage](/help/assets/assets/blank-canvas-page.png)

>[!NOTE]
>
> Der zulässige Breiten- und Höhenbereich liegt zwischen 50 und 5.000.

**Menüoptionen im rechten Bereich:** Verwenden Sie diese Optionen, um der Arbeitsfläche die erforderlichen Bilder und Textebenen hinzuzufügen.

* ![DM-Vorlagen](/help/assets/assets/add-image.svg): Klicken Sie, um der Arbeitsfläche Bilder hinzuzufügen.
* ![Anpassbare Vorlagen](/help/assets/assets/add-text.svg): Klicken Sie, um der Arbeitsfläche Texte hinzuzufügen.
* ![Anpassbare Vorlagen](/help/assets/assets/show-layers-list.svg): Klicken Sie, um die Liste aller Ebenen (Bild und Text) auf der Arbeitsfläche anzuzeigen. Jedes Bild und jeder Text, das bzw. der der Arbeitsfläche hinzugefügt wird, wird als separate Ebene dargestellt.

**Menüoptionen im linken Bereich:** Verwenden Sie diese Optionen für allgemeine Editoraktionen, wie unten beschrieben.

* ![DM-Vorlagen](/help/assets/assets/layer-selector.svg): Wählen Sie eine Ebene aus.
* ![Vorlagen, die Anpassungen unterstützen](/help/assets/assets/bring-forward.svg): Klicken Sie, um eine ausgewählte Ebene in den Vordergrund zu bringen, oder drücken Sie **Strg**+**]** (Windows) bzw. **Befehlstaste**+**]** (Mac).
* ![Erstellen einer Vorlage, die einfach angepasst werden kann](/help/assets/assets/send-backward.svg): Klicken Sie, um eine ausgewählte Ebene nach hinten zu senden, oder drücken Sie **Strg**+**[** (Windows) bzw. **Befehlstaste**+**[** (Mac).
* ![Erstellen einer Vorlage, die sofort angepasst werden kann](/help/assets/assets/undo.svg): Klicken Sie, um die letzte Aktion rückgängig zu machen, oder drücken Sie **Strg**+**Z** (Windows) bzw. **Befehlstaste**+**Z** (Mac).
* ![Vorlage zum schnellen Erstellen von Bannern](/help/assets/assets/redo.svg): Klicken Sie, um die letzte Aktion wiederherzustellen, oder drücken Sie **Strg**+**Y** (Windows) bzw. **Befehlstaste**+**Y** (Mac).
* ![Vorlage zum schnellen Erstellen von Flyern](/help/assets/assets/zoom-in.svg): Klicken Sie, um die Arbeitsfläche zu vergrößern, oder drücken Sie **Strg**+**+** (Windows) bzw. Befehlstaste+**+** (Mac).
* ![Vorlage zum schnellen Erstellen von Bannern](/help/assets/assets/Zoom-out.svg): Klicken Sie, um die Arbeitsfläche zu verkleinern, oder drücken Sie **Strg**+**-** (Windows) oder **Befehlstaste**+**-** (Mac).
* Drücken Sie die **Rücktaste** oder **Entf**, um die ausgewählte Ebene zu löschen, wenn kein Text oder keine Eigenschaft bearbeitet wird.

Klicken Sie in der Arbeitsflächenebene auf ![Vorlage zum schnellen Erstellen von Flyern](/help/assets/assets/show-layers-list.svg) **>** Weitere Optionen (![](/help/assets/assets/three-dots.svg)), um die Abmessungen der Arbeitsfläche jederzeit beim Erstellen der Vorlage zu bearbeiten.
![](/help/assets/assets/edit-canvas1.png)

>[!NOTE]
>
> Vorlagen lassen maximal 20 Ebenen zu, einschließlich der Arbeitsfläche.

### Hinzufügen von Bildern zur Arbeitsfläche{#add-images-to-the-canvas}

Führen Sie die folgenden Schritte aus, um der Arbeitsfläche Bilder hinzuzufügen:

1. Klicken Sie auf ![Banner im Handumdrehen erstellen](/help/assets/assets/add-image.svg), um das Bedienfeld [Asset-Wähler](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/manage/asset-selector/overview-asset-selector) anzuzeigen. Das Bedienfeld zeigt die Bilder in Ihrer AEM Assets-Instanz an, die mit Dynamic Media synchronisiert werden.
1. Durchsuchen Sie das Bedienfeld oder verwenden Sie Keywords in der Suchleiste, um nach einem bestimmten Bild zu suchen.
1. Ziehen Sie ein Bild per Drag-and-Drop auf die Arbeitsfläche, um es zu verwenden. Zum Ändern der Größe oder Neupositionieren einer Ebene auf der Arbeitsfläche gehen Sie zum [**[!UICONTROL Bedienfeld „Eigenschaften“]**](#reposition-resize-delete-a-layer).
   ![Erstellen eines Banners innerhalb von Sekunden](/help/assets/assets/add-image-to-canvas.png)

### Hinzufügen von Textebenen zur Arbeitsfläche{#add-text-to-the-canvas}

Führen Sie die folgenden Schritte aus, um der Arbeitsfläche Textebenen hinzuzufügen:

1. Klicken Sie auf ![Schnelles Erstellen neuer Banner](/help/assets/assets/add-text.svg), um der Arbeitsfläche eine Textebene hinzuzufügen und das Bedienfeld „Eigenschaften“ zu öffnen.
1. Wählen Sie die Ebene aus und klicken Sie zum Aktualisieren auf den Text.
1. Aktivieren Sie Option zur **[!UICONTROL intelligenten Textgrößenänderung]** im Bedienfeld „Eigenschaften“, um die Textlänge und den Schriftgrad automatisch und optimal an den vorgesehenen Bereich anzupassen.
   ![Optimal anpassbare Banner](/help/assets/assets/add-text-layer.png)

Zum Neupositionieren, Ändern der Größe, Drehen oder Löschen der Ebene gehen Sie zum [**[!UICONTROL Bedienfeld „Eigenschaften“]**](#reposition-resize-delete-a-layer). Formatieren Sie Schriftart, Größe, Farbe, Stil und Ausrichtung (auf der Ebene) des Textes nach Ihren Wünschen, indem Sie die Werte in den entsprechenden Feldern unter dem Abschnitt **[!UICONTROL Text]** des Bedienfelds ändern.

>[!NOTE]
>
> Um eine andere Schriftart als die standardmäßige Schriftfamilie Adobe Sans F2 zu verwenden, müssen Sie die Schriftartdatei hochladen und für AEM Assets und Dynamic Media veröffentlichen. Wenn einige alte Schriftarten in Ihrer Instanz vorhanden sind, führen Sie eine [erneute Verarbeitung](/help/assets/reprocessing-assets-view.md) durch, damit sie im Vorlageneditor angezeigt werden.

### Bearbeiten oder Löschen einer Ebene {#edit-or-delete-a-layer}

Führen Sie die folgenden Schritte aus, um eine Arbeitsflächenebene zu bearbeiten oder zu löschen:

1. Klicken Sie auf ![Vorlagen mit Unterstützung für dynamische Aktualisierungen](/help/assets/assets/show-layers-list.svg) und wählen Sie die Ebene entweder auf der Arbeitsfläche oder über die Liste „Ebenen“ aus.
1. Klicken Sie auf **Weitere Optionen** (![Vorlagen mit Unterstützung für Echtzeitaktualisierungen](/help/assets/assets/three-dots.svg)), um die Ebene zu bearbeiten oder zu löschen.
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

Formatieren Sie Schriftart, Größe, Farbe, Stil und Ausrichtung (auf der Ebene) des Textes nach Ihren Wünschen, indem Sie die Werte in den entsprechenden Feldern unter dem Abschnitt **[!UICONTROL Text]** des Bedienfelds ändern.

**[!UICONTROL Intelligente Textgrößenänderung:]** Schließen Sie **[!UICONTROL Intelligente Textgrößenänderung]** ([Copyfit](https://experienceleague.adobe.com/de/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/text-formatting/r-copy-fitting)) ein, um einen beliebigen Text im vorgesehenen Bereich durch die intelligente Anpassung von Schriftgröße und -länge optimal anzupassen. Diese Funktion verhindert einen Textüberlauf und minimiert zusätzliche Leerzeichen am unteren Rand des Textes.
![Inhaltserstellung im Handumdrehen](/help/assets/assets/smart-text-resize.png)

### Parametrisieren von Ebenen {#parameterise-a-layer}

Nachdem Sie eine Vorlage mit mehreren Bild- und Textebenen erstellt haben, parametrisieren Sie die ausgewählten Ebenen. Wenn eine Ebene oder ihre Eigenschaft parametrisiert wird, erhält sie ein Schlüssel-Wert-Paar (auch als Parameter bezeichnet). Dieser Parameter kann in die Vorlagen-URL aufgenommen werden, um Position, Größe oder Inhalt der Ebene in Echtzeit zu aktualisieren, wodurch die Vorlage in kürzester Zeit angepasst wird.

So parametrisieren Sie eine Ebene:

1. Klicken Sie auf ![Sofortige Inhaltserstellung](/help/assets/assets/show-layers-list.svg), wählen Sie eine Ebene aus und klicken Sie auf **[!UICONTROL Parameter]**. Das Bedienfeld **[!UICONTROL Parameter]** wird angezeigt.
1. Schalten Sie **[!UICONTROL Parameter einschließen]** um, um eine Eigenschaft zu parametrisieren. Informationen zum Verhalten der Eigenschaft nach der Parametrisierung finden Sie [hier](#parameterisation-options-or-allowed-parameters).
1. **Optional:** Benennen Sie den Parameter um. Ein Parametername hat einen Ebenennamen, gefolgt von einem Suffix. Für eine ausgewählte Ebene verwenden alle parametrisierten Eigenschaften denselben Ebenennamen, gefolgt von einem variierenden Suffix. Benennen Sie den Ebenennamen um, indem Sie der semantischen Namenskonvention folgen, sodass bei Aufnahme des Parameters in die URL der Parametername selbst den Inhalt oder den Zweck der Ebene erklärt.
1. Klicken Sie auf **[!UICONTROL Speichern]**.
   ![Sofortige Inhaltserstellung](/help/assets/assets/parameterise-a-layer.png)
Um zwischen dem Bedienfeld „Parameter“ eines Bildes und der Textebene zu wechseln, wählen Sie die Ebene auf der Arbeitsfläche aus und klicken Sie auf **[!UICONTROL Parameter]**.

#### Option des Bedienfelds „Parameter“ {#parameterisation-options-or-allowed-parameters}

Die parametrisierten Eigenschaften können als URL-Parameter in die Vorlagen-URL aufgenommen werden, um die Vorlage mithilfe der URL in Echtzeit zu bearbeiten.

**Bildparameter:**

**X:** Fügen Sie dies ein, um die Ebene horizontal entlang ihrer Mittellinie parallel zur x-Achse der Vorlagenebene zu verschieben, indem der Wert des Parameters in der URL geändert wird.
**Y:** Fügen Sie dies ein, um die Ebene vertikal entlang ihrer Mittellinie parallel zur y-Achse der Vorlagenebene zu verschieben, indem der Wert des Parameters in der URL geändert wird.
**Breite:** Fügen Sie dies ein, um die Breite der Ebene anzupassen, indem der Wert des Parameters in der URL geändert wird.
**Höhe** Fügen Sie dies ein, um die Höhe der Ebene anzupassen, indem der Wert des Parameters in der URL geändert wird.
**Ausblenden:** Fügen Sie dies ein, um die Ebene in der Vorlage mit 0 (Anzeigen) und 1 (Ausblenden) ein- oder auszublenden.
**Quelle:** Fügen Sie dies ein, um das Bild der Ebene durch ein neues Bild zu ersetzen, indem der Bildpfad im Wert des Parameters in der URL geändert wird.

**Textformatierungsparameter:**

Schließen Sie die folgenden Parameter ein, um den Text, seine Schriftart, Farbe und Größe aus der URL zu bearbeiten, indem Sie die Werte des Parameters in der URL aktualisieren.

**Text:** Fügen Sie dies ein, um Text in der URL zu aktualisieren.
**Schriftfamilie:** Fügen Sie dies ein, um die Schriftart des Textes in der URL zu aktualisieren.
**Schriftgröße:** Fügen Sie dies ein, um die Schriftgröße des Textes in der URL zu aktualisieren.
**Textfarbe:** Fügen Sie dies ein, um die Schriftfarbe des Textes in der URL zu aktualisieren.

### Gruppieren von Ebenen für die gleichzeitige Steuerung Ihrer Sichtbarkeit{#group-layers}

Eine weitere Möglichkeit, Ihre Vorlagen flexibel zu halten, besteht in der Verwendung eines einzelnen Parameternamens, um mehrere Ebenen zu steuern. Diese Strategie ist hilfreich für den Parameter „Sichtbarkeit“ (Ebenen ausblenden oder anzeigen), um das Design oder die Grafiken aus einer einzigen Vorlage zu aktualisieren.

Führen Sie diese Schritte aus, um den Ausblendungsparametern (![schnelle Inhaltserstellung](/help/assets/assets/Visibility-icon.svg)) mehrerer Ebenen denselben Namen zuzuweisen, sodass Sie sie gleichzeitig ausblenden oder anzeigen können.

1. Navigieren Sie zum [**[!UICONTROL Bedienfeld „Eigenschaften“]**](#parameterise-a-layer) einer Ebene.
1. Schalten Sie den Parameter **[!UICONTROL Ausblenden]** ein, falls er nicht zuvor parametrisiert wurde.
1. **Optional:** Benennen Sie den Parameter „Ausblenden“ um.
1. Kopieren Sie den Namen „Parameter ausblenden“.
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
1. Wählen Sie den Parameter „Ausblenden“ für [gruppierte Ebenen](#group-layers) aus der Liste aus, um sie zusammen in der Vorlage ein- oder auszublenden.
1. **Optional:** Ändern Sie den Wert des Parameters **[!UICONTROL Ausblenden]** von 0 auf 1 oder umgekehrt und klicken Sie auf **[!UICONTROL Aktualisieren]**, um die Änderungen anzuzeigen. Ebenen mit demselben Parameter „Ausblenden“ werden zusammen ausgeblendet oder angezeigt. Auf ähnliche Weise können Sie die Sichtbarkeit der Ebenen über die URL steuern.

   ![Inhalt spontan erstellen](/help/assets/assets/dm-templates-publish-status.png)
Sie können auch **[!UICONTROL Alle Parameter einbeziehen]** umschalten, um alle angezeigten Parameterwerte zu bearbeiten und die Aktualisierungen in der Vorlagenvorschau anzuzeigen.
   <br>
1. Um die Vorlage auf der Vorschauseite zu veröffentlichen, klicken Sie auf **[!UICONTROL Veröffentlichen]** und bestätigen Sie die Veröffentlichung. Es wird die Meldung „Veröffentlichung abgeschlossen“ angezeigt, und der Veröffentlichungsstatus wird auf „Veröffentlicht“ aktualisiert.

>[!NOTE]
>
>Zum Veröffentlichen der Vorlage müssen zuerst die Bilder der Vorlage veröffentlicht werden.

### Kopieren der Bereitstellungs-URL

Die ausgewählten Parameter auf der Seite **[!UICONTROL Vorschau]** werden zu den URL-Parametern in der Vorlagen-URL.

So kopieren Sie die in der Vorschau angezeigte URL der veröffentlichten Vorlage:

1. Klicken Sie auf **[!UICONTROL URL kopieren]**. Das Dialogfeld **[!UICONTROL URL kopieren]** wird angezeigt. Wählen Sie die angezeigte URL aus und kopieren Sie sie. Beachten Sie, dass der erste Parameter in der URL nach einem Fragezeichen (**?)** beginnt, während ein Schlüssel-Wert-Paar mit **$** beginnt und mit **&amp;** endet. Schlüssel und Wert werden durch ein Gleichheitszeichen (**=**) getrennt, wobei sich der Schlüssel links und der Wert rechts befindet.
1. Fügen Sie diese URL in Ihre Browser-Registerkarte ein und sehen Sie sich Ihre Live-Vorlage an. Passen Sie die Vorlage in Echtzeit an, indem Sie den erforderlichen Parameterwert (Schlüsselwert) in der URL direkt aktualisieren, wie in [Schritt 2](#preview-and-publish-template-and-copy-template-deliver-url) des Abschnitts **Vorschau und Veröffentlichung** gezeigt.
1. Verwenden Sie diese URL für das schnelle Merchandising Ihrer Produkte oder Services. Sie können diese URL für Ihre Kundschaft freigeben oder in Ihre Website oder eine nachgelagerte Drittanbieteranwendung integrieren, um das Banner anzuzeigen und Aktualisierungen daran in Echtzeit vorzunehmen, sodass die laufenden Angebote widergespiegelt werden.

In diesem Video erfahren Sie, wie Sie Schritt für Schritt eine Dynamic Media-Vorlage erstellen.
>[!VIDEO](https://video.tv.adobe.com/v/3443281)

## Vornehmen von Aktualisierungen an der Vorlage in Echtzeit über die URL{#update-the-template-from-the-url}

Das direkte Bearbeiten von Parametern in der URL kann mühsam sein. Zur Vereinfachung können Sie wie folgt vorgehen:

1. Kopieren Sie die URL und fügen Sie sie in einen Editor ein.
1. Verwenden Sie Befehlstaste+F (Mac) bzw. Strg+F (Windows), um die Parameterwerte zu finden und zu bearbeiten. Beispiel:
   * Ersetzen von Bildpfaden für Bildebenen.
   * Passen Sie die Dimensionen und Positionen von Ebenen an (falls sie [parametrisiert](#parameterise-a-layer) sind).
   * Bearbeiten Sie Text, Schriftart, Farbe, Größe oder Ausrichtung für Textebenen.
   * Ändern Sie die Sichtbarkeitswerte zwischen 0 und 1.

Fügen Sie diese aktualisierte URL in Ihren Browser ein, um die Änderungen anzuzeigen.

## Bearbeiten der Vorlage{#edit-the-template}

Gehen Sie wie folgt vor, um die Vorlage zu bearbeiten:

1. Klicken Sie in der Assets-Ansicht auf die Option für **[!UICONTROL Dynamic Media-Assets]**.
2. Navigieren Sie zum Speicherort der Vorlage.
3. Wählen Sie die Vorlage aus.
4. Klicken Sie auf **[!UICONTROL Vorlage bearbeiten]**. Auf der Vorlagenarbeitsfläche werden die Vorlage und die Liste aller zugehörigen Ebenen im Bedienfeld „Ebenen“ angezeigt. Bearbeiten Sie Ihre Vorlage gemäß Ihren Anforderungen.

## Wichtige Hinweise {#important-points-to-note}

* Nachdem Sie eine Vorlage mit parametrisierten Bildebenen für dynamische Aktualisierungen erstellt haben, stellen Sie sicher, dass die für zukünftige Aktualisierungen vorgesehenen Bilder dieselben Abmessungen wie die parametrisierten Bilder aufweisen. Dadurch passen die Bilder perfekt in die Ebenen, ohne Überlauf oder leere Räume. Derzeit unterstützt die Vorlage keine automatischen Anpassungen der Abmessungen, um Bilder in die Ebenen einzupassen.
* In einer Textebene werden keine Unterzeichenfolgen unterstützt. Benutzende können auf die Unterzeichenfolge einer Textebene keine anderen Schrifteigenschaften anwenden.
* Die Unterstützung mehrerer Dynamic Media-Unternehmen ist bei Dynamic Media-Vorlagen derzeit nicht verfügbar.
* Beim Kopieren oder Verschieben zeigt die Zielauswahl alle Ordner an (einschließlich nicht mit Dynamic Media synchronisierter Ordner). Außerdem werden derzeit nicht die Dynamic Media-Vorlagen-Assets angezeigt (beides sind Einschränkungen der Zielauswahl).
* Jeder Aktualisierungsvorgang für einen Ordner (z. B. Veröffentlichen oder Löschen) über den Abschnitt „Assets“ wirkt sich auf die in diesem Ordner verfügbaren Dynamic Media-Vorlagen aus.
* Der Papierkorb kann für Dynamic Media-Vorlagen nicht verwendet werden. Wenn ein Asset in den Papierkorb verschoben und dann wiederhergestellt wird, wird das Asset in AEM wiederhergestellt, aber nicht in Dynamic Media. Dasselbe gilt für Dynamic Media-Vorlagen.

## Siehe auch

1. Erkunden von [Dynamic Media und seinen Funktionen](/help/assets/dynamic-media/dynamic-media.md)
1. Erkunden von [Dynamic Media mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md)
