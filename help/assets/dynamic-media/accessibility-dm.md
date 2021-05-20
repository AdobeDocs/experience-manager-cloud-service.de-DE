---
title: Barrierefreiheit in Dynamic Media
description: Erfahren Sie mehr über Barrierefreiheit in Dynamic Media und Dynamic Media-Viewern.
contentOwner: Rick Brough
topic-tags: introduction
content-type: reference
feature: Erreichbarkeit
role: Administrator,Business Practitioner
source-git-commit: e94289bccc09ceed89a2f8b926817507eaa19968
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 67%

---


# Barrierefreiheit in Dynamic Media {#accessibility-in-dm}

Dynamic Media unterstützt Tastatursteuerungs- und Hilfstechnologien wie JAWS- und NVDA-Bildschirmlesehilfen in der Authoring-Benutzeroberfläche.

## Unterstützung der Tastaturbedienung in Dynamic Media {#keyboard-support-in-dm}

Da Dynamic Media ein Plug-in für Experience Manager Assets ist, ist das meiste Tastatursteuerungsverhalten mit dem von Experience Manager Assets identisch. Beispielsweise weist die Schaltfläche `Cancel` in Dynamic Media dieselbe Fokushervorhebung auf wie in Experience Manager Assets. Sie reagiert auch auf den `Spacebar`-Schlüssel wie in Experience Manager Assets. Siehe [Tastaturbefehle in Assets](/help/assets/accessibility.md#keyboard-shortcuts).

Tastenanschläge, die von einzelnen Benutzeroberflächenelementen in Dynamic Media unterstützt werden, sind in den meisten Fällen offensichtlich und leicht zu finden. Die Tastatursteuerung in Dynamic Media umfasst Folgendes:

* Möglichkeit zur Verwendung von `Tab`- und `Shift+Tab`-Tastenkombinationen zum Navigieren zwischen interaktiven Elementen auf der Seite.
Mithilfe von `Tab` wird der Eingabefokus auf das nächste Element der Benutzeroberfläche in der Tabulatorreihenfolge weitergeschaltet. Durch die Verwendung von `Shift+Tab` wird der Eingabefokus wieder auf das vorherige Element der Benutzeroberfläche zurückgesetzt.
Die Fokusverschiebung folgt der natürlichen Position der Elemente der Benutzeroberfläche auf dem Bildschirm und bewegt sich in einer Reihenfolge von links nach rechts und dann von oben nach unten. Wenn in einem Feld ein Fehler auftritt, können Sie außerdem `Tab` drücken, um den Fokus darauf zu verschieben.
* Möglichkeit zur Verwendung der `Spacebar`- und `Enter`-Taste zum Aktivieren standardmäßiger Elemente der Benutzeroberfläche, wie z. B. Schaltflächen und Dropdown-Listen.
* Möglichkeit, die Tastaturfokushervorhebung auf dem aktiven Element anzuzeigen. Das Element der Benutzeroberfläche, das den Eingabefokus hat, erhielt eine visuelle Fokusanzeige als Rahmen, der um das Element der Benutzeroberfläche gerendert wird.
* Im Hotspot-Editor können Sie einige benutzerdefinierte Tastenkombinationen wie Pfeiltasten verwenden, um mit komplexen Elementen der Benutzeroberfläche zu interagieren und Hotspots neu zu positionieren.
* Im interaktiven Video-Editor können Sie mit dem `Spacebar` ein Bild auswählen und es einem Segment hinzufügen. Darüber hinaus können Sie die `Backspace`-Taste verwenden, um das ausgewählte Element aus der Registerkarte **[!UICONTROL Inhalt]** zu löschen. Drücken Sie nach Wunsch auch die Taste `Tab`, um zwischen interaktiven Elementen auf der Seite zu navigieren.
* Im Editor &quot;Bildbeschneiden/Smartes Zuschneiden&quot;haben Sie folgende Möglichkeiten:
   * Verwenden Sie die Pfeiltasten, um die Rahmengröße zu beschneiden, das Bild neu zu positionieren oder beides.
   * Der erste `Tab`-Stopp markiert den gesamten Bildrahmen. Sie können den Rahmen dann mithilfe der Pfeiltasten auf der Tastatur neu positionieren.
   * Die folgenden vier `Tab`-Stopps sind die vier Ecken des Rahmens. Wenn der Fokus auf eine Rahmenecke gelegt wird, wird die Ecke hervorgehoben. Auch hier können Sie die fokussierte Ecke mit den Pfeiltasten auf der Tastatur verschieben.
Weitere Informationen finden Sie unter [Bearbeiten von smarten Zuschnitten oder smarten Farb-/Bildmustern eines einzelnen Bildes](/help/assets/dynamic-media/image-profiles.md#editing-the-smart-crop-or-smart-swatch-of-a-single-image).

<!-- Keyboarding is the same because Dynamic Media is using the same UI library (Coral 3 (AEM 6.5) or Coral Spectrum (in Skyline)) as entire AEM Assets.  -->

<!-- In the Hotspot editor, Dynamic Media lets you use arrow keys to control the position of a hot spot. See [Carousel Banners](/help/assets/dynamic-media/carousel-banners.md##adding-hotspots-or-image-maps-to-an-image-banner) or [Interactive Images](/help/assets/dynamic-media/interactive-images.md#adding-hotspots-to-an-image-banner)  -->

<!-- I think we should definitely mention this in the DM-specific area of documentation for keyboard support. -->

<!-- I would not get into much of details of specific keyboard support logic of these editors. One of the reasons - chances are that accessibility support will receive Phase2-like attention, with more holistic approach. -->

## Unterstützung der Hilfstechnologien in Dynamic Media {#assistive-technology=support-for-dm}

Die Elemente der Dynamic Media-Benutzeroberfläche arbeiten mit Hilfstechnologien wie Bildschirmlesehilfen. Beispielsweise erkennt es Landmarkierungen auf einer Seite, wenn Sie mithilfe des Tastaturbefehls `D` durch Landmarken navigieren, oder Bereiche mit dem Tastaturbefehl `R`. Außerdem wird die Überschrift vorgelesen, wenn Sie mit dem Tastaturbefehl für Überschriften `H` navigieren.

## Unterstützung der Tastaturbedienung in Dynamic Media-Viewern {#keyboard-accessibility-for-dm-viewers}

Alle vordefinierten Dynamic Media-Viewer-Komponenten unterstützen die Tastaturbedienung für Ihre Kunden.

Siehe [Barrierefreiheit und Navigation über die Tastatur](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/c-keyboard-accessibility.html?lang=de) im Dynamic Media Viewer-Referenzhandbuch.

## Unterstützung der Hilfstechnologien in Dynamic Media-Viewern {#assistive-technology=support-for-dm-viewers}

Alle Dynamic Media-Viewer-Komponenten unterstützen ARIA-Rollen und -Attribute (Accessible Rich Internet Applications), um die Integration mit Hilfstechnologien wie Bildschirmlesehilfen zu verbessern.
Weitere Informationen finden Sie im Hilfethema **Unterstützung für Hilfstechnologien** im Dynamic Media Viewer-Referenzhandbuch. Sehen Sie beispielsweise [Unterstützung für Hilfstechnologien](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/r-html5-video-viewer-20-assistive.html?lang=de) für den Video-Viewer oder [Unterstützung für Hilfstechnologien](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/c-html5-aem-interactive-image-assistive.html?lang=de#viewers-for-aem-assets-only) für den interaktiven Bild-Viewer.

>[!MORELIKETHIS]
>
>* [Barrierefreiheit für Adobe-lösungen](https://www.adobe.com/accessibility.html)
>* [Barrierefreiheit in Experience Manager Assets](/help/assets/dynamic-media/accessibility-dm.md)

