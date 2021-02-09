---
title: Barrierefreiheit in  [!DNL Dynamic Media]
description: Erfahren Sie mehr über Barrierefreiheit in Dynamic Media und Dynamic Media-Viewern.
contentOwner: Rick Brough
topic-tags: introduction
content-type: reference
translation-type: tm+mt
source-git-commit: c3ada59105cad7c2fc3b36b032d045b91f86b495
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 97%

---


# Barrierefreiheit in Dynamic Media {#working-with-three-d-assets-dm}

Dynamic Media unterstützt Tastatursteuerungs- und Hilfstechnologien wie JAWS- und NVDA-Bildschirmlesehilfen in der Authoring-Benutzeroberfläche.

## Unterstützung der Tastaturbedienung in Dynamic Media

Da es sich bei Dynamic Media um ein Plug-in für Experience Manager Assets handelt, ist das Verhalten der Tastatursteuerung im Wesentlichen mit dem von Experience Manager Assets identisch. Beispielsweise hat die Schaltfläche `Cancel` in Dynamic Media dieselbe Fokushervorhebung wie in Experience Manager Assets und reagiert auf die Taste `Spacebar` wie in Experience Manager Assets. Weitere Informationen finden Sie in [Tastaturbefehle in Assets](/help/assets/accessibility.md#keyboard-shortcuts).

Tastenkombinationen, die von einzelnen Elementen der Benutzeroberfläche in Dynamic Media unterstützt werden, sind – in den meisten Fällen – offensichtlich und leicht zu erkennen. Die Tastatursteuerung in Dynamic Media umfasst Folgendes:

* Möglichkeit zur Verwendung von `Tab`- und `Shift+Tab`-Tastenkombinationen zum Navigieren zwischen interaktiven Elementen auf der Seite.
Mithilfe von `Tab` wird der Eingabefokus auf das nächste Element der Benutzeroberfläche in der Tabulatorreihenfolge weitergeschaltet. Durch die Verwendung von `Shift+Tab` wird der Eingabefokus wieder auf das vorherige Element der Benutzeroberfläche zurückgesetzt.
Die Fokusverschiebung folgt der natürlichen Position der Elemente der Benutzeroberfläche auf dem Bildschirm und bewegt sich in einer Reihenfolge von links nach rechts und dann von oben nach unten. Wenn in einem Feld ein Fehler auftritt, können Sie außerdem `Tab` drücken, um den Fokus darauf zu verschieben.
* Möglichkeit, mit den Tasten `Spacebar` und `Enter` Standardelemente der Benutzeroberfläche zu aktivieren, z. B. Schaltflächen, Dropdown-Listen usw.
* Möglichkeit, die Tastaturfokushervorhebung auf dem aktiven Element anzuzeigen. Das Benutzeroberflächenelement mit Eingabefokus erhält möglicherweise eine visuelle Fokusanzeige als Rand, der um das Benutzeroberflächenelement gerendert wird.
* Im Hotspot-Editor können Sie einige benutzerdefinierte Tastenkombinationen wie Pfeiltasten verwenden, um mit komplexen Elementen der Benutzeroberfläche zu interagieren und Hotspots neu zu positionieren.
* Im interaktiven Video-Editor können Sie mit dem `Spacebar` ein Bild auswählen und es einem Segment hinzufügen. Darüber hinaus haben Sie die Möglichkeit, das ausgewählte Element mit der Taste `Backspace` aus der Registerkarte **[!UICONTROL Inhalt]** zu löschen. Drücken Sie nach Wunsch auch die Taste `Tab`, um zwischen interaktiven Elementen auf der Seite zu navigieren.
* Im Editor zum Bildbeschneiden/intelligenten Zuschneiden haben Sie folgende Möglichkeiten:
   * Mit den Pfeiltasten können Sie die Bildgröße zuschneiden oder das Bild neu positionieren oder beides.
   * Der erste `Tab`-Stopp markiert den gesamten Bildrahmen. Mit den Pfeiltasten auf der Tastatur können Sie den Rahmen dann neu positionieren.
   * Die folgenden vier `Tab`-Stopps sind die vier Ecken des Rahmens. Wenn der Fokus auf eine Rahmenecke gelegt wird, wird die Ecke hervorgehoben. Auch hier können Sie die fokussierte Ecke mit den Pfeiltasten auf der Tastatur verschieben.
Weitere Informationen finden Sie unter [Bearbeiten von smarten Zuschnitten oder smarten Farb-/Bildmustern eines einzelnen Bildes](/help/assets/dynamic-media/image-profiles.md#editing-the-smart-crop-or-smart-swatch-of-a-single-image).

<!-- Keyboarding is the same because Dynamic Media is using the same UI library (Coral 3 (AEM 6.5) or Coral Spectrum (in Skyline)) as entire AEM Assets.  -->

<!-- In the Hotspot editor, Dynamic Media lets you use arrow keys to control the position of a hot spot. See [Carousel Banners](/help/assets/dynamic-media/carousel-banners.md##adding-hotspots-or-image-maps-to-an-image-banner) or [Interactive Images](/help/assets/dynamic-media/interactive-images.md#adding-hotspots-to-an-image-banner)  -->

<!-- I think we should definitely mention this in the DM-specific area of documentation for keyboard support. -->

<!-- I would not get into much of details of specific keyboard support logic of these editors. One of the reasons - chances are that accessibility support will receive Phase2-like attention, with more holistic approach. -->

## Unterstützung der Hilfstechnologien in Dynamic Media {#assistive-technology=support-for-dm}

Die Elemente der Dynamic Media-Benutzeroberfläche arbeiten mit Hilfstechnologien wie Bildschirmlesehilfen. Beispielsweise werden Orientierungspunkte auf einer Seite erkannt, wenn Sie mithilfe des Tastaturbefehls `D` durch Orientierungspunkte oder mithilfe des Tastaturbefehls `R` durch Regionen navigieren. Außerdem wird die Überschrift vorgelesen, wenn Sie mit dem Tastaturbefehl für Überschriften `H` navigieren.

## Unterstützung der Tastaturbedienung in Dynamic Media-Viewern {#keyboard-accessibility-for-dm-viewers}

Alle vordefinierten Dynamic Media-Viewer-Komponenten unterstützen die Tastaturbedienung für Ihre Kunden.

Weitere Informationen finden Sie unter [Tastaturbedienung und Navigation](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/c-keyboard-accessibility.html) im Dynamic Media Viewer-Referenzhandbuch.

## Unterstützung der Hilfstechnologien in Dynamic Media-Viewern {#assistive-technology=support-for-dm-viewers}

Alle Dynamic Media-Viewer-Komponenten unterstützen ARIA-Rollen und -Attribute (Accessible Rich Internet Applications), um die Integration mit Hilfstechnologien wie Bildschirmlesehilfen zu verbessern.
Weitere Informationen finden Sie im Hilfethema **Unterstützung für Hilfstechnologien** im Dynamic Media Viewer-Referenzhandbuch. Sehen Sie beispielsweise [Unterstützung für Hilfstechnologien](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/r-html5-video-viewer-20-assistive.html) für den Video-Viewer oder [Unterstützung für Hilfstechnologien](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/c-html5-aem-interactive-image-assistive.html?lang=de#viewers-for-aem-assets-only) für den interaktiven Bild-Viewer.

>[!MORELIKETHIS]
>
>* [Barrierefreiheit für Adobe-lösungen](https://www.adobe.com/accessibility.html)
>* [Barrierefreiheit in Experience Manager Assets](/help/assets/dynamic-media/accessibility-dm.md)

