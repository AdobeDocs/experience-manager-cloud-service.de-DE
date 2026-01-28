---
title: Barrierefreiheit in Dynamic Media
description: Erfahren Sie, wie Sie in Dynamic Media mit Videos arbeiten, z. B. Best Practices für die Videokodierung und die Veröffentlichung von Videos in YouTube. Erfahren Sie außerdem, wie Sie Untertitel, verdeckte Untertitel oder Kapitelmarken zu Videos hinzufügen können.
contentOwner: Rick Brough
topic-tags: introduction
content-type: reference
feature: Accessibility
role: Admin,User
exl-id: f8d2dcbf-f61a-4b27-a3fc-406e3662adcb
source-git-commit: 4a09e74ae62dba40deb192b1dfe38860bdb43921
workflow-type: tm+mt
source-wordcount: '636'
ht-degree: 91%

---

# Barrierefreiheit in Dynamic Media {#accessibility-in-dm}

{{work-with-dynamic-media}}

Dynamic Media unterstützt Tastatursteuerungs- und Hilfstechnologien wie JAWS- und NVDA-Bildschirmlesehilfen in der Authoring-Benutzeroberfläche.

## Unterstützung der Tastaturbedienung in Dynamic Media {#keyboard-support-in-dm}

Da es sich bei Dynamic Media um ein Plug-in für [!DNL Experience Manager Assets] handelt, ist das Verhalten der Tastatursteuerung im Wesentlichen mit dem von [!DNL Experience Manager Assets] identisch. Beispielsweise verfügt die Schaltfläche `Cancel` in Dynamic Media über dieselbe Fokushervorhebung wie in [!DNL Experience Manager Assets]. Die Reaktion auf die Taste `Spacebar` ist ebenfalls mit der in [!DNL Experience Manager Assets] identisch. Weitere Informationen finden Sie in [Tastaturbefehle in Assets](/help/assets/accessibility.md#keyboard-shortcuts).

Tastenkombinationen, die von einzelnen Elementen der Benutzeroberfläche in Dynamic Media unterstützt werden, sind – in den meisten Fällen – offensichtlich und leicht zu finden. Die Tastatursteuerung in Dynamic Media umfasst Folgendes:

* Möglichkeit zur Verwendung von `Tab`- und `Shift+Tab`-Tastenkombinationen zum Navigieren zwischen interaktiven Elementen auf der Seite.
Mithilfe von `Tab` wird der Eingabefokus auf das nächste Element der Benutzeroberfläche in der Tabulatorreihenfolge weitergeschaltet. Durch die Verwendung von `Shift+Tab` wird der Eingabefokus wieder auf das vorherige Element der Benutzeroberfläche zurückgesetzt.
Der Fokusdurchlauf folgt der natürlichen Position der Elemente der Benutzeroberfläche auf dem Bildschirm und bewegt sich in einer Reihenfolge von links nach rechts und dann von oben nach unten. Wenn in einem Feld ein Fehler auftritt, können Sie außerdem `Tab` drücken, um den Fokus darauf zu verschieben.
* Möglichkeit, mit den Tasten `Spacebar` und `Enter` Standardelemente der Benutzeroberfläche zu aktivieren, z. B. Schaltflächen und Dropdown-Listen.
* Möglichkeit, die Tastaturfokushervorhebung auf dem aktiven Element anzuzeigen. Das Benutzeroberflächenelement mit Eingabefokus hat eine visuelle Fokusanzeige als Rand erhalten, der um das Benutzeroberflächenelement gerendert wird.
* Im Hotspot-Editor können Sie einige benutzerdefinierte Tastenkombinationen wie Pfeiltasten verwenden, um mit komplexen Elementen der Benutzeroberfläche zu interagieren und Hotspots neu zu positionieren.
* Im interaktiven Video-Editor können Sie mit dem `Spacebar` ein Bild auswählen und es einem Segment hinzufügen. Darüber hinaus haben Sie die Möglichkeit, das ausgewählte Element mit der Taste `Backspace` aus der Registerkarte **[!UICONTROL Inhalt]** zu löschen. Drücken Sie nach Wunsch auch die Taste `Tab`, um zwischen interaktiven Elementen auf der Seite zu navigieren.
* Im Editor für Bildzuschnitt/intelligenten Zuschnitt können Sie Folgendes ausführen:
   * Mit den Pfeiltasten können Sie die Bildgröße zuschneiden oder das Bild neu positionieren oder beides.
   * Der erste `Tab`-Stopp markiert den gesamten Bildrahmen. Sie können dann die Pfeiltasten auf der Tastatur verwenden, um den Rahmen neu zu positionieren.
   * Die folgenden vier `Tab`-Stopps sind die vier Ecken des Rahmens. Wenn der Fokus auf eine Rahmenecke gelegt wird, wird die Ecke hervorgehoben. Auch hier können Sie die fokussierte Ecke mit den Pfeiltasten auf der Tastatur verschieben.
Weitere Informationen finden Sie unter [Bearbeiten von smarten Zuschnitten oder intelligenten Farbfeldern eines einzelnen Bildes](/help/assets/dynamic-media/image-profiles.md#editing-the-smart-crop-or-smart-swatch-of-a-single-image).

<!-- Keyboarding is the same because Dynamic Media is using the same UI library (Coral 3 (Experience Manager 6.5) or Coral Spectrum (in Skyline)) as entire Experience Manager Assets.  -->

<!-- In the Hotspot editor, Dynamic Media lets you use arrow keys to control the position of a hot spot. See [Carousel Banners](/help/assets/dynamic-media/carousel-banners.md#adding-hotspots-or-image-maps-to-an-image-banner) or [Interactive Images](/help/assets/dynamic-media/interactive-images.md#adding-hotspots-to-an-image-banner)  -->

<!-- I think we should definitely mention this in the DM-specific area of documentation for keyboard support. -->

<!-- I would not get into much of details of specific keyboard support logic of these editors. One of the reasons - chances are that accessibility support will receive Phase2-like attention, with more holistic approach. -->

## Unterstützung der Hilfstechnologien in Dynamic Media {#assistive-technology=support-for-dm}

Die Elemente der Dynamic Media-Benutzeroberfläche arbeiten mit Hilfstechnologien wie Bildschirmlesehilfen. Beispielsweise werden Orientierungspunkte auf einer Seite erkannt, wenn Sie mithilfe des Tastaturbefehls `D` durch Orientierungspunkte oder mithilfe des Tastaturbefehls `R` durch Regionen navigieren. Außerdem wird die Überschrift vorgelesen, wenn Sie mit dem Tastaturbefehl für Überschriften `H` navigieren.

## Unterstützung der Tastaturbedienung in Dynamic Media-Viewern {#keyboard-accessibility-for-dm-viewers}

Alle vordefinierten Dynamic Media-Viewer-Komponenten unterstützen die Tastaturbedienung für Ihre Kunden.

Weitere Informationen finden Sie unter [Tastaturbedienung und Navigation](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/library/c-keyboard-accessibility#) im Dynamic Media Viewers-Referenzhandbuch.

## Unterstützung der Hilfstechnologien in Dynamic Media Viewers {#assistive-technology=support-for-dm-viewers}

Alle Dynamic Media-Viewer-Komponenten unterstützen ARIA-Rollen und -Attribute (Accessible Rich Internet Applications), um die Integration mit Hilfstechnologien wie Bildschirmlesehilfen zu verbessern.
Weitere Informationen finden Sie im Hilfethema **Unterstützung für Hilfstechnologien** im Dynamic Media Viewers-Referenzhandbuch. Sehen Sie beispielsweise [Unterstützung für Hilfstechnologien](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/r-html5-video-viewer-20-assistive#) für den Video-Viewer oder [Unterstützung für Hilfstechnologien](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/c-html5-aem-interactive-image-assistive#viewers-for-aem-assets-only) für den interaktiven Bild-Viewer.

## Unterstützung für Untertitel in [!DNL Dynamic Media] {#closed-caption-support}

Dynamic Media unterstützt die Bereitstellung von Videos und adaptiven Videosätzen mit Untertiteln. Die Untertitel müssen über dem Videoinhalt angezeigt werden.

Weitere Informationen finden Sie unter [Video in Dynamic Media – Hinzufügen von verdeckten Untertiteln zu Videos](/help/assets/dynamic-media/video.md#adding-captions-to-video).


>[!MORELIKETHIS]
>
>* [Barrierefreiheit für Adobe-lösungen](https://www.adobe.com/trust/accessibility.html)
>* [Barrierefreiheit in Experience Manager Assets](/help/assets/dynamic-media/accessibility-dm.md)
