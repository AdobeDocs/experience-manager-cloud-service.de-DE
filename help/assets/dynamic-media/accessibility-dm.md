---
title: Zugänglichkeit in [!DNL Dynamic Media]
description: Erfahren Sie, wie Sie in Dynamic Media mit 3D-Assets arbeiten.
contentOwner: Rick Brough
topic-tags: introduction
content-type: reference
translation-type: tm+mt
source-git-commit: 7af8ddda4aee093b22147db9be9f65cd0c131c04
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 3%

---


# Accessibility in Dynamic Media {#working-with-three-d-assets-dm}

Dynamische Medien unterstützen Tastatursteuerungs- und Hilfstechnologien wie JAWS- und NVDA-Bildschirmlesehilfen in der Authoring-Benutzeroberfläche.



## Unterstützung der Barrierefreiheit von Tastaturen in dynamischen Medien

Tastenanschläge, die von einzelnen Benutzeroberflächenelementen unterstützt werden, sind in den meisten Fällen offensichtlich und leicht zu entdecken. Die Tastatursteuerung in dynamischen Medien umfasst Folgendes:

* Möglichkeit zur Verwendung `Tab` und `Shift+Tab` Verwendung von Tastenanschlägen zum Navigieren zwischen interaktiven Elementen auf der Seite.
Durch Verwendung `Tab` wird der Eingabefokus auf das nächste Element der Benutzeroberfläche in der Tab-Reihenfolge weitergeleitet. Durch die Verwendung `Shift+Tab` wird der Eingabefokus wieder auf das vorherige Element der Benutzeroberfläche zurückgesetzt.
Der Fokusdurchlauf folgt der natürlichen Elementposition der Benutzeroberfläche auf dem Bildschirm und bewegt sich in der Reihenfolge von links nach rechts und von oben nach unten.
* Möglichkeit, mit der `Spacebar` und- `Enter` Taste Standard-Benutzeroberflächenelemente wie Schaltflächen, Dropdown-Listen usw. zu aktivieren.
* Möglichkeit, die Tastaturfokushervorhebung auf dem aktiven Element anzuzeigen. Das Element der Benutzeroberfläche mit Eingabefokus erhält möglicherweise eine visuelle Fokusanzeige als Rahmen, der um das Element der Benutzeroberfläche gerendert wird.
* Möglichkeit, einige benutzerdefinierte Tastenanschläge zu verwenden, um mit komplexen Benutzeroberflächenelementen wie Pfeiltasten im Hotspot-Editor zu interagieren. Im Bildzuschneide-/Smart-Zuschneideeditor haben Sie die Möglichkeit, mithilfe der Pfeiltasten die Rahmengröße zu beschneiden oder das Bild neu zu positionieren oder beides.

Da Dynamic Media ein Plug-in für AEM Assets ist, ist das Verhalten der Tastatursteuerung im Wesentlichen dasselbe wie in AEM Assets. Beispielsweise hat die `Cancel` Schaltfläche in dynamischen Medien dieselbe Fokushervorhebung wie in AEM Assets und reagiert auf die `Spacebar` Taste wie in AEM Assets. Siehe [Tastaturbefehle in Assets](/help/assets/accessibility.md#keyboard-shortcuts). Ausnahmen hiervon sind der Hotspot-Editor und die Editoren für das Zuschneiden und Zuschneiden von Bildern.

<!-- Keyboarding is the same because Dynamic Media is using the same UI library (Coral 3 (AEM 6.5) or Coral Spectrum (in Skyline)) as entire AEM Assets.  -->

Im Hotspot-Editor können Sie mit dynamischen Medien die Position eines Hotspots mithilfe von Pfeiltasten steuern. Siehe [Karussell-Banner](/help/assets/dynamic-media/carousel-banners.md##adding-hotspots-or-image-maps-to-an-image-banner) oder [Interaktive Bilder](/help/assets/dynamic-media/interactive-images.md#adding-hotspots-to-an-image-banner)

Verwenden Sie im Bildzuschneideeditor die Pfeiltasten, um die Rahmengröße zu beschneiden oder das Bild neu zu positionieren. See [Editing the smart crop or smart swatch of a single image](/help/assets/dynamic-media/image-profiles.md#editing-the-smart-crop-or-smart-swatch-of-a-single-image)

<!-- I think we should definitely mention this in the DM-specific area of documentation for keyboard support. -->

<!-- I would not get into much of details of specific keyboard support logic of these editors. One of the reasons - chances are that accessibility support will receive Phase2-like attention, with more holistic approach. -->

## Barrierefreiheitsunterstützung für dynamische Medien-Viewer {#keyboard-accessibility-for-dm-viewers}

Alle vordefinierten Komponenten von Dynamic Media Viewern unterstützen die Barrierefreiheit der Tastatur für Ihre Kunden.

Siehe [Tastaturzugriff und Navigation](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/c-keyboard-accessibility.html) im Viewer-Referenzhandbuch für dynamische Medien.

## Unterstützung von Technologien für Dynamische Medien-Viewer {#assistive-technology=support-for-dm-viewers}

Alle Viewer-Komponenten in Dynamic Media unterstützen ARIA-Rollen und -Attribute (Accessible Rich Internet Applications), um die Integration mit Hilfstechnologien wie Bildschirmlesehilfen zu verbessern.

Weitere Informationen finden Sie im Hilfethema zur Unterstützung **der** unterstützenden Technologie in einem Viewer-Thema zum Anpassen im Referenzhandbuch für Dynamische Medien-Viewer. Weitere Informationen finden Sie unter [Unterstützung](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/r-html5-video-viewer-20-assistive.html) der Technologie für den Video-Viewer oder Unterstützung [der](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/c-html5-aem-interactive-image-assistive.html?lang=en#viewers-for-aem-assets-only) Technologie für den Viewer für interaktive Bilder.

>[!MORELIKETHIS]
>
>* [Zugänglichkeit für Adoben](https://www.adobe.com/accessibility.html)
>* [Barrierefreiheit in Experience Manager Assets](/help/assets/dynamic-media/accessibility-dm.md)

