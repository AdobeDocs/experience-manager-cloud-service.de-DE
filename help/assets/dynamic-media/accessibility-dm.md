---
title: Barrierefreiheit in Dynamic Media
description: Erfahren Sie mehr über Barrierefreiheit in Dynamic Media und Dynamic Media-Viewern.
contentOwner: Rick Brough
topic-tags: introduction
content-type: reference
topic: Geschäftspraktiker
translation-type: tm+mt
source-git-commit: 0f2b7176b44bb79bdcd1cecf6debf05bd652a1a1
workflow-type: tm+mt
source-wordcount: '613'
ht-degree: 66%

---


# Barrierefreiheit in Dynamic Media {#accessibility-in-dm}

Dynamic Media unterstützt Tastatursteuerungs- und Hilfstechnologien wie JAWS- und NVDA-Bildschirmlesehilfen in der Authoring-Benutzeroberfläche.

## Unterstützung der Tastaturbedienung in Dynamic Media {#keyboard-support-in-dm}

Da es sich bei Dynamic Media um ein Plug-in für Experience Manager Assets handelt, ist das Verhalten der Tastatursteuerung im Wesentlichen dasselbe wie bei Experience Manager Assets. Beispielsweise hat die Schaltfläche `Cancel` in Dynamic Media dieselbe Fokushervorhebung wie in Experience Manager Assets. Es reagiert auch auf den Schlüssel `Spacebar` wie in Experience Manager Assets. Siehe [Tastaturbefehle in Assets](/help/assets/accessibility.md#keyboard-shortcuts).

Tastenanschläge, die von einzelnen Benutzeroberflächenelementen in Dynamic Media unterstützt werden, sind in den meisten Fällen offensichtlich und leicht zu finden. Die Tastatursteuerung in Dynamic Media umfasst Folgendes:

* Möglichkeit zur Verwendung von `Tab`- und `Shift+Tab`-Tastenkombinationen zum Navigieren zwischen interaktiven Elementen auf der Seite.
Mithilfe von `Tab` wird der Eingabefokus auf das nächste Element der Benutzeroberfläche in der Tabulatorreihenfolge weitergeschaltet. Durch die Verwendung von `Shift+Tab` wird der Eingabefokus wieder auf das vorherige Element der Benutzeroberfläche zurückgesetzt.
Die Fokusverschiebung folgt der natürlichen Position der Elemente der Benutzeroberfläche auf dem Bildschirm und bewegt sich in einer Reihenfolge von links nach rechts und dann von oben nach unten. Wenn in einem Feld ein Fehler auftritt, können Sie außerdem `Tab` drücken, um den Fokus darauf zu verschieben.
* Möglichkeit zur Aktivierung standardmäßiger Benutzeroberflächenelemente wie Schaltflächen und Dropdown-Listen mit den Tasten `Spacebar` und `Enter`.
* Möglichkeit, die Tastaturfokushervorhebung auf dem aktiven Element anzuzeigen. Das Element der Benutzeroberfläche, das den Eingabefokus hat, erhielt eine visuelle Fokusanzeige als Rahmen, der um das Element der Benutzeroberfläche gerendert wird.
* Im Hotspot-Editor können Sie einige benutzerdefinierte Tastenkombinationen wie Pfeiltasten verwenden, um mit komplexen Elementen der Benutzeroberfläche zu interagieren und Hotspots neu zu positionieren.
* Im interaktiven Video-Editor können Sie mit dem `Spacebar` ein Bild auswählen und es einem Segment hinzufügen. Darüber hinaus können Sie mit der Taste `Backspace` das ausgewählte Element aus der Registerkarte **[!UICONTROL Inhalt]** löschen. Drücken Sie nach Wunsch auch die Taste `Tab`, um zwischen interaktiven Elementen auf der Seite zu navigieren.
* Im Editor für Bildzuschneiden/intelligente Zuschneiden können Sie Folgendes ausführen:
   * Verwenden Sie die Pfeiltasten, um die Rahmengröße zu beschneiden oder das Bild neu zu positionieren.
   * Der erste `Tab`-Stopp markiert den gesamten Bildrahmen. Mit den Pfeiltasten auf der Tastatur können Sie den Rahmen dann neu positionieren.
   * Die folgenden vier `Tab`-Stopps sind die vier Ecken des Rahmens. Wenn der Fokus auf eine Rahmenecke gelegt wird, wird die Ecke hervorgehoben. Auch hier können Sie die fokussierte Ecke mit den Pfeiltasten auf der Tastatur verschieben.
Weitere Informationen finden Sie unter [Bearbeiten von smarten Zuschnitten oder smarten Farb-/Bildmustern eines einzelnen Bildes](/help/assets/dynamic-media/image-profiles.md#editing-the-smart-crop-or-smart-swatch-of-a-single-image).

<!-- Keyboarding is the same because Dynamic Media is using the same UI library (Coral 3 (AEM 6.5) or Coral Spectrum (in Skyline)) as entire AEM Assets.  -->

<!-- In the Hotspot editor, Dynamic Media lets you use arrow keys to control the position of a hot spot. See [Carousel Banners](/help/assets/dynamic-media/carousel-banners.md##adding-hotspots-or-image-maps-to-an-image-banner) or [Interactive Images](/help/assets/dynamic-media/interactive-images.md#adding-hotspots-to-an-image-banner)  -->

<!-- I think we should definitely mention this in the DM-specific area of documentation for keyboard support. -->

<!-- I would not get into much of details of specific keyboard support logic of these editors. One of the reasons - chances are that accessibility support will receive Phase2-like attention, with more holistic approach. -->

## Unterstützung der Hilfstechnologien in Dynamic Media {#assistive-technology=support-for-dm}

Die Elemente der Dynamic Media-Benutzeroberfläche arbeiten mit Hilfstechnologien wie Bildschirmlesehilfen. Beispielsweise werden Landmarks auf einer Seite erkannt, wenn Sie mithilfe des Tastaturbefehls `D` oder mit dem Tastaturbefehl `R` durch Bereiche navigieren. Außerdem wird die Überschrift vorgelesen, wenn Sie mit dem Tastaturbefehl für Überschriften `H` navigieren.

## Unterstützung der Tastaturbedienung in Dynamic Media-Viewern {#keyboard-accessibility-for-dm-viewers}

Alle vordefinierten Dynamic Media-Viewer-Komponenten unterstützen die Tastaturbedienung für Ihre Kunden.

Siehe [Tastaturzugriff und Navigation](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/c-keyboard-accessibility.html?lang=de) im Dynamic Media Viewer-Referenzhandbuch.

## Unterstützung der Hilfstechnologien in Dynamic Media-Viewern {#assistive-technology=support-for-dm-viewers}

Alle Dynamic Media-Viewer-Komponenten unterstützen ARIA-Rollen und -Attribute (Accessible Rich Internet Applications), um die Integration mit Hilfstechnologien wie Bildschirmlesehilfen zu verbessern.
Weitere Informationen finden Sie im Hilfethema **Unterstützung für Hilfstechnologien** im Dynamic Media Viewer-Referenzhandbuch. Sehen Sie beispielsweise [Unterstützung für Hilfstechnologien](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/r-html5-video-viewer-20-assistive.html?lang=de) für den Video-Viewer oder [Unterstützung für Hilfstechnologien](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/c-html5-aem-interactive-image-assistive.html?lang=de#viewers-for-aem-assets-only) für den interaktiven Bild-Viewer.

>[!MORELIKETHIS]
>
>* [Barrierefreiheit für Adobe-lösungen](https://www.adobe.com/accessibility.html)
>* [Barrierefreiheit in Experience Manager Assets](/help/assets/dynamic-media/accessibility-dm.md)

