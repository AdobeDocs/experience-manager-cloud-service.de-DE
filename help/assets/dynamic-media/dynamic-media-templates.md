---
title: Wie werden Dynamic Media-Vorlagen verwaltet?
description: Erfahren Sie, wie Sie Dynamic Media-Vorlagen mit einem WYSIWYG-Vorlageneditor erstellen und mehrere Bilder und Textebenen einschließen, um Banner und Flyer schnell zu erstellen und in nachgelagerten Anwendungen zu verwenden.
hide: true
role: User
exl-id: 07de648e-4ae2-4524-8e05-3cf10bb6006d
source-git-commit: f5fa8f1f23d35d239f7bb0e22e104627f9f84317
workflow-type: tm+mt
source-wordcount: '2722'
ht-degree: 0%

---

# Dynamic Media-Vorlagen{#dynamic-media-templates}

| [Best Practices für die Suche](/help/assets/search-best-practices.md) | [Best Practices für Metadaten](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [Entwicklerdokumentation zu AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|-----|

Erstellen Sie Dynamic Media-Vorlagen mit einem WYSIWYG-Vorlageneditor und schließen Sie mehrere Bilder und Textebenen ein, um schnell Banner und Flyer zu erstellen und sie in nachgelagerten Anwendungen zu verwenden. Sie können auch Parameter zu den Bildern und Textebenen in der Vorlage hinzufügen und [Dynamic Media-URLs](https://experienceleague.adobe.com/en/docs/commerce-admin/content-design/wysiwyg/storage/catalog-urls-dynamic-media) verwenden, um die Werte für diese Ebenen in Echtzeit zu aktualisieren.

Zu den wichtigsten Funktionen gehören:

* **Dynamic Media WYSIWYG-Vorlageneditor:** Erstellen Sie anpassbare Banner mit Bild- und Textebenen.
* **Ebenenparametrisierung** Definieren Sie dynamische Schlüssel-Wert-Paare für Ebenen, um Echtzeit-Aktualisierungen zu ermöglichen.
* **Dynamic Media-URL-Unterstützung:** Verwenden Sie Dynamic Media-URLs für Vorlagen und integrieren Sie personalisierte Werte aus Programmen von Erstanbietern oder Drittanbietern.
* **Ebenensichtbarkeitssteuerung:** Ebenen nach Bedarf dynamisch aus- oder einblenden.
* **Größenanpassung für intelligenten Text:** Passen Sie die Textgröße automatisch an bestimmte Bereiche an.

Zu den wichtigsten Vorteilen von Dynamic Media-Vorlagen gehören:

* **1:1-Optimierung von Personalization:** Passen Sie Inhalte an Echtzeit-Kundensignale an.
* **Weniger manueller Aufwand:** Automatisierung und Beschleunigung der Inhaltserstellung und -verwaltung.
* **Konsistente Omni-Channel-Erlebnisse sicherstellen** Die Markenkonsistenz über alle Kanäle hinweg gewährleisten.
* **Inhalte effektiv wiederverwenden** Vermeiden Sie Inhalte zur einmaligen Verwendung und skalieren Sie sie mit dynamischen, parametrisierten Vorlagen.
* **Risiken mindern** Preise, Rabatte und Links in Echtzeit aktualisieren.
* **Kundeninteraktion verbessern:** interaktive, kontextuell relevante Erlebnisse fördern..

>[!NOTE]
>
>Kunden mit Abonnements für die Enhanced Security SKU können in diesem Cloud Service-Programm keine Dynamic Media-Funktionen, einschließlich Dynamic Media-Vorlagen, verwenden.

## Voraussetzungen{#prerequisites-for-dynamic-media-wysiwyg-template}

Um eine Dynamic Media-Vorlage zu erstellen, benötigen Sie Folgendes:

1. Zugriff auf Dynamic Media.
1. [Die in Ihrer AEM Assets-Instanz verfügbaren Bilder wurden mit Dynamic Media synchronisiert, um sie für die Erstellung der Vorlage zu verwenden](/help/assets/dynamic-media/config-dm.md).

## Erstellen einer Dynamic Media WYSIWYG-Vorlage{#how-to-create-dynamic-media-wysiwyg-template}

Gehen Sie wie folgt vor, um eine XDM-Vorlage zu erstellen:

1. [Erstellen einer leeren Arbeitsfläche](#create-a-canvas)
1. [Bilder zur Arbeitsfläche hinzufügen](#add-images-to-the-canvas)
1. [Hinzufügen von Textebenen zur Arbeitsfläche](#add-text-to-the-canvas)
1. [Bearbeiten oder Löschen einer Ebene](#edit-or-delete-a-layer)
1. [Parameterebenen](#parameterise-a-layer)

### Erstellen einer leeren Arbeitsfläche{#create-a-canvas}

Führen Sie die folgenden Schritte aus, um eine leere Arbeitsfläche zu erstellen:

1. Navigieren Sie zur Assets-Ansicht und klicken Sie auf **[!UICONTROL Dynamic Media Assets]** im linken Bereich.

   ![Dynamic Media-Vorlagen](/help/assets/assets/dm-templates/DM-Assets1.png)

1. Klicken Sie auf **[!UICONTROL Vorlage erstellen]**, um die Vorlage unter Dynamic Media Assets zu speichern, oder gehen Sie zu einem Ordner und klicken Sie auf **[!UICONTROL Vorlage erstellen]**, um die Vorlage in diesem Ordner zu speichern. Das **[!UICONTROL Neue Vorlage]** Dialogfeld wird angezeigt.
   ![Erstellen dynamischer Vorlagen, die in Echtzeit angepasst werden können](/help/assets/assets/dm-templates/new-template.png)
Um [Ordner zu erstellen](/help/assets/add-delete-assets-view.md) unter **[!UICONTROL Dynamic Media Assets]** erstellen Sie einen Ordner unter **[!UICONTROL Assets]**. Die Ordnerstruktur unter **[!UICONTROL Assets]** wird unter **[!UICONTROL Dynamic Media Assets]** repliziert.
1. Geben Sie einen Vorlagennamen an, definieren Sie die Breite und Höhe der Arbeitsfläche und klicken Sie auf **[!UICONTROL Erstellen]**. Eine leere Arbeitsfläche wird mit Menüoptionen auf beiden Seiten angezeigt, die zum Erstellen der Vorlage verwendet werden können. Bewegen Sie den Mauszeiger über die Menüoptionen, um deren QuickInfo anzuzeigen.
   ![Anpassbare Echtzeit-Vorlage](/help/assets/assets/dm-templates/blank-canvas-page.png)

>[!NOTE]
>
> Der zulässige Breiten- und Höhenbereich liegt zwischen 50 und 5.000.

**Menüoptionen im rechten Bereich:** Verwenden Sie diese Optionen, um die erforderlichen Bilder und Textebenen zur Arbeitsfläche hinzuzufügen.

* ![DM-Vorlagen](/help/assets/assets/dm-templates/add-image.svg): Klicken Sie, um Bilder zur Arbeitsfläche hinzuzufügen.
* ![Anpassbare Vorlagen](/help/assets/assets/dm-templates/add-text.svg): Klicken Sie, um der Arbeitsfläche Texte hinzuzufügen.
* ![Anpassbare Vorlagen](/help/assets/assets/dm-templates/show-layers-list.svg): Klicken Sie, um die Liste aller Ebenen (Bild und Text) auf der Arbeitsfläche anzuzeigen. Jedes Bild und jeder Text, der zur Arbeitsfläche hinzugefügt wird, wird als separate Ebene dargestellt.

**Menüoptionen im linken Bereich:** Sie diese Optionen für allgemeine Editor-Aktionen wie unten beschrieben.

* ![DM-Vorlagen](/help/assets/assets/dm-templates/layer-selector.svg): Wählen Sie eine Ebene aus.
* ![Vorlagen, die Anpassungen unterstützen](/help/assets/assets/dm-templates/bring-forward.svg): Klicken Sie, um eine ausgewählte Ebene nach vorne zu bringen, oder drücken Sie **Strg** + **]** (Windows) oder **Cmd** + **]** (Mac).
* ![So erstellen Sie eine Vorlage, die einfach angepasst werden kann](/help/assets/assets/dm-templates/send-backward.svg): Klicken Sie, um eine ausgewählte Ebene rückwärts zu senden, oder drücken Sie **Strg** + **[** (Windows) oder **Cmd** + **[** (Mac).
* ![Erstellen Sie eine Vorlage, die sofort angepasst werden kann](/help/assets/assets/dm-templates/undo.svg): Klicken Sie, um die letzte Aktion rückgängig zu machen, oder drücken Sie **Strg** + **Z** (Windows) oder **Befehl** + **Z** (Mac).
* ![Vorlage, um Banner schnell zu erstellen](/help/assets/assets/dm-templates/redo.svg): Klicken Sie, um die letzte Aktion wiederherzustellen, oder drücken Sie **Strg** + **Y** (Windows) oder **Cmd** + **Y** (Mac).
* ![Vorlage, um Flyer schnell zu erstellen](/help/assets/assets/dm-templates/zoomin.svg): Klicken Sie, um die Arbeitsfläche zu vergrößern, oder drücken Sie **Strg** + **+** (Windows) oder Befehl + **+** (Mac).
* ![Vorlage, um Banner schnell zu erstellen](/help/assets/assets/dm-templates/zoomout.svg): Klicken Sie, um die Arbeitsfläche auszuzoomen, oder drücken Sie **Strg** + **-** (Windows) oder **Befehlstaste** + **-** (Mac).
* Drücken Sie **Rücktaste** oder **Löschen**, um die ausgewählte Ebene zu löschen, wenn kein Text oder keine Eigenschaft bearbeitet wird.

Klicken Sie ![Vorlage, um Flyer schnell zu erstellen](/help/assets/assets/dm-templates/show-layers-list.svg) **>** weitere Optionen (![](/help/assets/assets/dm-templates/three-dots.svg)) auf der Arbeitsflächen-Ebene, um die Arbeitsflächen-Dimensionen jederzeit beim Erstellen der Vorlage zu bearbeiten.
![](/help/assets/assets/dm-templates/edit-canvas1.png)

>[!NOTE]
>
> Vorlagen erlauben maximal 20 Ebenen, einschließlich der Arbeitsfläche.

### Bilder zur Arbeitsfläche hinzufügen{#add-images-to-the-canvas}

Führen Sie die folgenden Schritte aus, um der Arbeitsfläche Bilder hinzuzufügen:

1. Klicken Sie auf ![Banner im Handumdrehen erstellen](/help/assets/assets/dm-templates/add-image.svg), um das Bedienfeld [Asset-Auswahl](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/manage/asset-selector/overview-asset-selector) anzuzeigen. Das Bedienfeld zeigt die Bilder in Ihrer AEM Assets-Instanz an, die mit Dynamic Media synchronisiert werden.
1. Durchsuchen Sie das Bedienfeld oder verwenden Sie Keywords in der Suchleiste, um ein bestimmtes Bild zu finden.
1. Ziehen Sie ein Bild per Drag-and-Drop auf die Arbeitsfläche, um es zu verwenden. Informationen zum Ändern [**[!UICONTROL  Größe einer Ebene auf ]**](#reposition-resize-delete-a-layer) Arbeitsfläche finden Sie im Bedienfeld „Eigenschaften“.
   ![Erstellen eines Banners innerhalb von Sekunden](/help/assets/assets/dm-templates/add-image-to-canvas.png)

### Hinzufügen von Textebenen zur Arbeitsfläche{#add-text-to-the-canvas}

Führen Sie die folgenden Schritte aus, um der Arbeitsfläche Textebenen hinzuzufügen:

1. Klicken Sie ![Schnelles Erstellen neuer Banner](/help/assets/assets/dm-templates/add-text.svg), um der Arbeitsfläche eine Textebene hinzuzufügen und das Bedienfeld Eigenschaften zu öffnen.
1. Wählen Sie die Ebene aus und klicken Sie auf den Text, um sie zu aktualisieren.
1. Aktivieren Sie **[!UICONTROL Smart Text Resize]** im Bedienfeld Eigenschaften , um die Textlänge und Schriftgröße automatisch an den vorgesehenen Bereich anzupassen.
   ![Beste anpassbare Banner](/help/assets/assets/dm-templates/add-text-layer.png)

Informationen [**[!UICONTROL  Neupositionieren, Ändern der Größe, Drehen oder Löschen der Ebene finden Sie ]**](#reposition-resize-delete-a-layer) „Eigenschaftenbereich“. Formatieren Sie den Text in der gewünschten Schriftart, Größe, Farbe, Stil und Ausrichtung (auf der Ebene), indem Sie die Werte in den entsprechenden Feldern unter dem Abschnitt **[!UICONTROL Text]** des Bedienfelds ändern.

>[!NOTE]
>
> Um eine andere Schriftart als die standardmäßige Adobe Sans F2-Schriftfamilie zu verwenden, müssen Sie die Schriftartdatei hochladen und in AEM Assets und Dynamic Media veröffentlichen. Wenn Sie einige alte Schriftarten in Ihrer Instanz haben, stellen Sie sicher, dass Sie [erneut verarbeiten](/help/assets/reprocessing-assets-view.md), um sie im Vorlageneditor anzuzeigen.

### Bearbeiten oder Löschen einer Ebene {#edit-or-delete-a-layer}

Führen Sie die folgenden Schritte aus, um eine Arbeitsflächen-Ebene zu bearbeiten oder zu löschen:

1. Klicken Sie ![Vorlagen mit Unterstützung für dynamische ](/help/assets/assets/dm-templates/show-layers-list.svg)) und wählen Sie die Ebene entweder auf der Arbeitsfläche oder in der Liste Ebenen aus.
1. Klicken Sie auf **Weitere Optionen** (![Vorlagen mit Unterstützung für Echtzeit-](/help/assets/assets/dm-templates/three-dots.svg)), um die Ebene zu bearbeiten oder zu löschen.
1. Klicken Sie **[!UICONTROL Löschen]**, um die Ebene zu löschen.
1. Klicken Sie **[!UICONTROL Bearbeiten]**, um die Ebene mithilfe des Bedienfelds [**[!UICONTROL Eigenschaften]**](#reposition-resize-delete-a-layer) zu bearbeiten.
   ![Schnelle Bannererstellung](/help/assets/assets/dm-templates/edit-delete-layer.png)

### Bedienfeld „Eigenschaften“{#properties-panel}

So navigieren Sie zum Bedienfeld „Eigenschaften“ einer Ebene:

1. Klicken Sie ![Schnelle Inhaltserstellung](/help/assets/assets/dm-templates/show-layers-list.svg).
1. Wählen Sie die Ebene aus der Liste aus.

In diesem Bedienfeld werden die Position des Mittelpunkts des Layers auf der Arbeitsflächen-Ebene (X- und Y-Werte) und die Abmessungen (Breite und Höhe) des Layers zusammen mit Textformatierungsoptionen angezeigt.

![Schnelle Inhaltserstellung](/help/assets/assets/dm-templates/properties-panel.png)

Wählen Sie im Eigenschaftenbedienfeld einer Ebene eine andere Ebene auf der Arbeitsfläche aus, um zum zugehörigen Eigenschaftenbedienfeld zu navigieren.


#### Ebene neu positionieren, skalieren, drehen oder löschen{#reposition-resize-delete-a-layer}

Sehen Sie sich die folgenden häufigen Ebenenbearbeitungsaktionen an, um einen Text oder eine Bildebene zu bearbeiten:

* **Ebene neu positionieren:** Ziehen Sie die Ebene, um sie an eine beliebige Stelle auf der Arbeitsfläche zu verschieben. Diese Aktion aktualisiert die X- und Y-Werte im Eigenschaftenbereich.
* **Größe der Ebene ändern** Wählen Sie die Ebene aus und ziehen Sie die Kantengriffe, um die Größe zu ändern. Diese Aktion aktualisiert die Werte „W“ (Breite) und „H“ (Höhe) im Eigenschaftenbereich.
* **Ebene drehen:** Ziehen Sie den quadratischen Ziehgriff vertikal über der Ebene, um sie um ihre Mitte zu drehen. Diese Aktion aktualisiert die Winkelwerte im Eigenschaftenbereich.
* **Ebene löschen:** Drücken Sie **Rücktaste** oder **Löschen** und klicken Sie dann auf **[!UICONTROL Bestätigen]**, um eine ausgewählte Ebene zu löschen.

#### Textformatierungsoptionen{#text-formatting-options-on-properties-panel}

Formatieren Sie den Text in der gewünschten Schriftart, Größe, Farbe, Stil und Ausrichtung (auf der Ebene), indem Sie die Werte in den entsprechenden Feldern unter dem Abschnitt **[!UICONTROL Text]** des Bedienfelds ändern.

**[!UICONTROL Größenanpassung für intelligenten Text]** Schließen Sie **[!UICONTROL Größenänderung für intelligenten Text]** ([Copyfit](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/text-formatting/r-copy-fitting)) ein, um einen beliebigen Text im vorgesehenen Bereich optimal anzupassen, indem Sie Schriftgröße und -länge intelligent anpassen. Diese Funktion verhindert einen Textüberlauf und minimiert zusätzliche Leerzeichen am unteren Rand des Textes.
![Inhaltserstellung im Handumdrehen](/help/assets/assets/dm-templates/smart-text-resize.png)

### Parameterebenen {#parameterise-a-layer}

Nachdem Sie eine Vorlage mit mehreren Bild- und Textebenen erstellt haben, parametrisieren Sie die ausgewählten Ebenen. Wenn eine Ebene oder ihre Eigenschaft parametrisiert wird, erhält sie ein Schlüssel-Wert-Paar (auch als Parameter bezeichnet). Dieser Parameter kann in die Vorlagen-URL aufgenommen werden, um Position, Größe oder Inhalt der Ebene in Echtzeit zu aktualisieren, was zu einer schnellen Anpassung der Vorlage führt.

So parametrisieren Sie eine Ebene:

1. Klicken Sie ![Instant Content Creation](/help/assets/assets/dm-templates/show-layers-list.svg), wählen Sie eine Ebene aus und klicken Sie auf **[!UICONTROL Parameter]**. Das **[!UICONTROL Parameter]** wird angezeigt.
1. Schalten Sie **[!UICONTROL Parameter einschließen]** um eine Eigenschaft zu parametrisieren. Siehe [this](#parameterisation-options-or-allowed-parameters), um das Verhalten der Eigenschaft nach der Parametrisierung zu erfahren.
1. **Optional:** Benennen Sie den Parameter um. Ein Parametername hat einen Ebenennamen, gefolgt von einem Suffix. Für eine ausgewählte Ebene verwenden alle parametrisierten Eigenschaften denselben Ebenennamen, gefolgt von einem variierenden Suffix. Benennen Sie den Ebenennamen um, indem Sie der semantischen Namenskonvention folgen, sodass, wenn Sie den Parameter in die URL aufnehmen, der Parametername selbst den Inhalt oder den Zweck der Ebene erklärt.
1. Klicken Sie auf **[!UICONTROL Speichern]**.
   ![Sofortige Inhaltserstellung](/help/assets/assets/dm-templates/parameterise-a-layer.png)
Um zwischen dem Bedienfeld Parameter eines Bildes und der Textebene zu wechseln, wählen Sie die Ebene auf der Arbeitsfläche aus und klicken Sie auf **[!UICONTROL Parameter]**.

#### Bedienfeld „Parameter“-Option {#parameterisation-options-or-allowed-parameters}

Die parametrisierten Eigenschaften können als URL-Parameter in die Vorlagen-URL aufgenommen werden, um die Vorlage mithilfe der URL in Echtzeit zu bearbeiten.

**Bildparameter:**

**X:** Einfügen, um die Ebene horizontal entlang ihrer Mittellinie parallel zur X-Achse der Vorlagenebene zu verschieben, indem der Parameterwert in der URL geändert wird.
**Y:** Einfügen, um die Ebene vertikal entlang ihrer Mittellinie parallel zur Y-Achse der Vorlagenebene zu verschieben, indem der Parameterwert in der URL geändert wird.
**Breite:** Einfügen, um die Breite der Ebene anzupassen, indem der Parameterwert in der URL geändert wird.
**Höhe** Mit dieser Option können Sie die Höhe der Ebene anpassen, indem Sie den Parameterwert in der URL ändern.
**Ausblenden:** Einschließen, um die Ebene in der Vorlage mit 0 (Anzeigen) und 1 (Ausblenden) ein- oder auszublenden.
**Source:** Include, um das Ebenenbild durch ein neues Bild zu ersetzen, indem der Bildpfad im Parameterwert in der URL geändert wird.

**Textformatierungsparameter:**

Schließen Sie die folgenden Parameter ein, um den Text, seine Schriftart, Farbe und Größe aus der URL zu bearbeiten, indem Sie die Parameterwerte in der URL aktualisieren.

**Text:** Include , um Text aus der URL zu aktualisieren.
**Schriftfamilie:** Include , um die Schriftart des Textes in der URL zu aktualisieren.
**Schriftgröße:** Einschließen, um die Schriftgröße des Textes über die URL zu aktualisieren.
**Textfarbe:** Einschließen, um die Schriftfarbe des Textes in der URL zu aktualisieren.

### Gruppieren Sie Ebenen, um ihre Sichtbarkeit gleichzeitig zu steuern{#group-layers}

Eine weitere Möglichkeit, Ihre Vorlagen flexibel zu halten, besteht darin, einen einzelnen Parameternamen zu verwenden, um mehrere Ebenen zu steuern. Diese Strategie ist hilfreich für den Parameter Sichtbarkeit (Ebenen ausblenden oder anzeigen), um das Design oder die Grafiken aus einer Vorlage zu aktualisieren.

Führen Sie diese Schritte aus, um den Ausblendungsparametern (![schnelle Inhaltserstellung) mehrerer Ebenen denselben Namen zuzuweisen, sodass Sie sie gleichzeitig ausblenden oder anzeigen ](/help/assets/assets/dm-templates/Visibility-icon.svg).

1. Navigieren Sie zum [**[!UICONTROL Eigenschaftenbereich]**](#parameterise-a-layer) einer Ebene.
1. Schalten Sie den Parameter **[!UICONTROL hide]** ein, wenn er nicht zuvor parametrisiert wurde.
1. **Optional:** Benennen Sie den Hide-Parameter um.
1. Kopieren Sie den Namen Parameter ausblenden .
1. Wechseln Sie zum Bedienfeld Parameter anderer Ebenen, indem Sie sie auf der Arbeitsfläche auswählen und ihren Parameter **[!UICONTROL Ausblenden]** umschalten, wenn er nicht parametrisiert ist.
1. Ersetzen Sie ihren **[!UICONTROL Parameter ausblenden]**-Namen durch den kopierten Namen.
1. Klicken Sie **[!UICONTROL Speichern]**, um die Ebenen zu gruppieren.
1. Führen Sie Schritt 3 und dann Schritt 4 im Abschnitt [**[!UICONTROL Vorschau und Publish]**](#preview-and-publish-template-and-copy-template-deliver-url) aus, um Ihre Änderungen anzuzeigen.

## Vorschau anzeigen und Vorlage veröffentlichen, um die Versand-URL zu kopieren{#preview-and-publish-template-and-copy-template-deliver-url}

Führen Sie die folgenden Schritte aus, um die Vorlage in der Vorschau anzuzeigen und zu veröffentlichen und die Versand-URL zu kopieren:

1. Klicken Sie auf der Arbeitsfläche auf **[!UICONTROL Vorschau]**. Sie können auch zu **[!UICONTROL Assets-Ansicht]** **>** **[!UICONTROL Dynamic Media Assets]** **>** navigieren, Ihre Vorlage suchen und auswählen **>** auf **** Vorlage bearbeiten **>** auf **[!UICONTROL Vorschau]** klicken. Auf der Vorschauseite werden die Vorlage, ihre Parameter (parametrisierte Ebenen und Eigenschaften), der Veröffentlichungsstatus und die Option **[!UICONTROL Publish]** angezeigt.
1. Wählen Sie Parameter **[!UICONTROL Bedienfeld]** Vorlagenparameter“ aus, um ihre Werte zu bearbeiten und den Inhalt, die Größe, die Position oder die Textformatierung der entsprechenden Vorlagenebene in der Vorschau sofort zu aktualisieren. Zum Beispiel:
   1. Auswählen einer Textebene und Bearbeiten ihres Textes oder
   1. Wählen Sie eine Bildebene aus, klicken Sie auf ![Inhalt im laufenden Betrieb erstellen](/help/assets/assets/dm-templates/add-image.svg) wählen Sie ein Bild aus der Asset-Auswahl aus und klicken Sie auf **[!UICONTROL Aktualisieren]**.

   Die Vorlage wird sofort aktualisiert, wobei der bearbeitete Text angezeigt und das vorherige Bild durch das neue Bild ersetzt wird. Darüber hinaus spiegelt der Bildparameterwert den neuen Bildpfad wider. Auf ähnliche Weise können Sie die Größe einer Ebene ändern, indem Sie ihre Werte anpassen. Die Änderungen werden dann in Echtzeit auf die Vorlage angewendet.
1. Wählen Sie den Parameter zum Ausblenden für [gruppierte Ebenen](#group-layers) aus der Liste aus, um sie zusammen in der Vorlage ein- oder auszublenden.
1. **Optional:** Ändern Sie den Parameterwert **[!UICONTROL Ausblenden]** zwischen 0 und 1 und klicken Sie auf **[!UICONTROL Aktualisieren]**, um die Änderungen anzuzeigen. Ebenen mit demselben Hide-Parameter werden zusammen ausgeblendet oder angezeigt. Auf ähnliche Weise können Sie die Sichtbarkeit der Ebenen über die URL steuern.

   ![Inhalte im laufenden Betrieb erstellen](/help/assets/assets/dm-templates-publish-status.png)
Sie können auch **[!UICONTROL Alle Parameter einschließen]** umschalten, um alle angezeigten Parameterwerte zu bearbeiten und die Aktualisierungen in der Vorlagenvorschau anzuzeigen.
   <br>
1. Um die Vorlage auf der Vorschauseite zu veröffentlichen, klicken Sie auf **[!UICONTROL Publish]** und bestätigen Sie die Veröffentlichung. Die Meldung Publish abgeschlossen wird angezeigt, und der Veröffentlichungsstatus wird auf Veröffentlicht aktualisiert.

>[!NOTE]
>
>Zum Veröffentlichen der Vorlage müssen die Vorlagenbilder zuerst veröffentlicht werden.

### Versand-URL kopieren

Die ausgewählten Parameter auf der Seite **[!UICONTROL Vorschau]** werden zu den URL-Parametern in der Vorlagen-URL.

So kopieren Sie die in der Vorschau angezeigte URL der veröffentlichten Vorlage:

1. Klicken Sie auf **[!UICONTROL URL kopieren]**. Das **[!UICONTROL URL kopieren]** wird angezeigt. Auswahl und Kopie der angezeigten URL Beachten Sie, dass der erste Parameter in der URL nach einem Fragezeichen **(?) beginnt** Schlüssel-Wert-Paar beginnt mit **$** und endet mit **&amp;**. Schlüssel und Wert werden durch ein Gleichheitszeichen **(=) getrennt** wobei der Schlüssel links und der Wert rechts liegen.
1. Fügen Sie diese URL in Ihre Browser-Registerkarte ein und sehen Sie sich Ihre Live-Vorlage an. Passen Sie die Vorlage in Echtzeit an, indem Sie den erforderlichen Parameterwert (Schlüsselwert) in der URL direkt aktualisieren, wie in [Schritt 2](#preview-and-publish-template-and-copy-template-deliver-url) des Abschnitts **Vorschau und Publish** gezeigt.
1. Verwenden Sie diese URL für schnelles Merchandising Ihrer Produkte oder Services. Sie können diese URL für Ihre Kunden freigeben oder in Ihre Website oder eine nachgelagerte Drittanbieteranwendung integrieren, um das Banner anzuzeigen und Echtzeitaktualisierungen daran vorzunehmen, um die laufenden Angebote widerzuspiegeln.

In diesem Video erfahren Sie, wie Sie eine Dynamic Media-Vorlage Schritt für Schritt erstellen.
>[!VIDEO](https://video.tv.adobe.com/v/3443281)

## Echtzeitaktualisierungen an der Vorlage über die URL vornehmen{#update-the-template-from-the-url}

Die Bearbeitung von Parametern direkt in der URL kann mühsam sein. Zur Vereinfachung:

1. Kopieren Sie die URL und fügen Sie sie in ein Notizbuch ein.
1. Verwenden Sie Befehlstaste+F (Mac) oder Strg+F (Windows), um die Parameterwerte zu finden und zu bearbeiten. Beispielsweise:
   * Ersetzen von Bildpfaden für Bildebenen.
   * Ebenenbemaßungen und -positionen anpassen (falls [parametrisiert](#parameterise-a-layer)).
   * Bearbeiten von Text, Schriftart, Farbe, Größe oder Ausrichtung für Textebenen.
   * Ändern Sie die Sichtbarkeitswerte zwischen 0 und 1.

Fügen Sie diese aktualisierte URL in Ihren Browser ein, um die Änderungen anzuzeigen.

## Vorlage bearbeiten{#edit-the-template}

Bearbeiten Sie die Vorlage, indem Sie folgende Schritte ausführen:

1. Klicken Sie in der Assets-Ansicht auf **[!UICONTROL Dynamic Media Assets]**.
2. Navigieren Sie zum Speicherort der Vorlage.
3. Wählen Sie die Vorlage.
4. Klicken Sie **[!UICONTROL Vorlage bearbeiten]**. Auf der Vorlagenarbeitsfläche werden die Vorlage und die Liste aller zugehörigen Ebenen im Ebenenbedienfeld angezeigt. Beginnen Sie mit der Bearbeitung Ihrer Vorlage gemäß Ihren Anforderungen.

## Wichtige Hinweise {#important-points-to-note}

* Nachdem Sie eine Vorlage mit parametrisierten Bildebenen für dynamische Aktualisierungen erstellt haben, stellen Sie sicher, dass die für zukünftige Aktualisierungen vorgesehenen Bilder dieselben Abmessungen wie die parametrisierten Bilder haben. Dadurch wird sichergestellt, dass die Bilder perfekt in die Ebenen passen, ohne zu überlaufen oder leere Räume zu hinterlassen. Derzeit unterstützt die Vorlage keine automatischen Dimensionsanpassungen, um Bilder in die Ebenen einzupassen.
* In einer Textebene werden keine Teilzeichenfolgen unterstützt. Benutzende können auf die Teilzeichenfolge einer Textebene keine anderen Schrifteigenschaften anwenden.
* Die Unterstützung mehrerer Dynamic Media-Unternehmen ist derzeit nicht in Dynamic Media-Vorlagen verfügbar.
* Beim Kopieren oder Verschieben zeigt der Zielselektor alle Ordner an (einschließlich nicht mit Dynamic Media synchronisierter Ordner). Außerdem werden derzeit nicht die Dynamic Media-Vorlagen-Assets angezeigt (beides sind Einschränkungen der Zielauswahl).
* Jeder Aktualisierungsvorgang für einen Ordner (z. B. Publish oder Löschen) aus dem Abschnitt Assets wirkt sich auf die in diesem Ordner verfügbaren Dynamic Media-Vorlagen aus.
* Papierkorb funktioniert nicht für Dynamic Media-Vorlagen. Wenn ein Asset in den Papierkorb verschoben und dann wiederhergestellt wird, wird das Asset in AEM wiederhergestellt, jedoch nicht in Dynamic Media. Dasselbe gilt für Dynamic Media-Vorlagen.

## Siehe auch

1. Erkunden von [Dynamic Media und seinen Funktionen](/help/assets/dynamic-media/dynamic-media.md)
1. Erkunden von [Dynamic Media mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md)
