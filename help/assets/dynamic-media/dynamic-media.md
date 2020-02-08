---
title: Arbeiten mit dynamischen Medien
description: Informationen zur Verwendung dynamischer Medien zum Bereitstellen von Assets für den Gebrauch in Web, Mobile und Social Media
translation-type: tm+mt
source-git-commit: 6224d193adfb87bd9b080f48937e0af1f03386d6

---


# Arbeiten mit dynamischen Medien {#working-with-dynamic-media}

Mit [dynamischen Medien](https://www.adobe.com/solutions/web-experience-management/dynamic-media.html) können Sie visuell ansprechende Merchandising- und Marketing-Assets nach Bedarf bereitstellen, die automatisch für die Anzeige auf Web- sowie Mobile- und Social-Media-Sites skaliert werden. Anhand eines Sets aus Master-Assets können Sie mit Dynamic Media mehrere Varianten ansprechender Inhalte in Echtzeit über das globale, skalierbare und leistungsoptimierte Netzwerk generieren und bereitstellen.

Dynamic Media ermöglicht interaktive Anzeigeerlebnisse wie Zoom, Drehen um 360 Grad und Videos. Dynamic Media bindet die Workflows der Adobe Experience Manager-Lösung für die Verwaltung digitaler Assets (Assets) auf einzigartige Weise ein, um das Management digitaler Kampagnen zu vereinfachen und zu optimieren.

>[!NOTE]
>
>Es gibt einen Community-Artikel zum Thema [Arbeiten mit Adobe Experience Manager und Dynamic Media](https://helpx.adobe.com/experience-manager/using/aem_dynamic_media.html).

## Einsatzmöglichkeiten für Dynamic Media {#what-you-can-do-with-dynamic-media}

Mit dynamischen Medien können Sie Assets vor ihrer Veröffentlichung verwalten. Eine ausführliche Beschreibung der allgemeinen Arbeit mit digitalen Assets finden Sie in [Arbeiten mit digitalen Assets](/help/assets/manage-digital-assets.md). Die allgemeinen Themen umfassen das Hochladen, Herunterladen, Bearbeiten und Veröffentlichen von Assets, das Anzeigen und Bearbeiten von Eigenschaften und die Suche nach Assets.

Zu den Funktionen, die nur für dynamische Medien vorgesehen sind, zählen:

* [Karussellbanner](carousel-banners.md)
* [Bildsets](image-sets.md)
* [Interaktive Bilder](interactive-images.md)
* [Interaktive Videos](interactive-videos.md)
* [Gemischte Mediensets](mixed-media-sets.md)
* [Panoramabilder](panoramic-images.md)

* [Rotationssets](spin-sets.md)
* [Video](video.md)
* [Bereitstellen von Dynamic Media Assets](delivering-dynamic-media-assets.md)
* [Verwalten von Assets](managing-assets.md)
* [Verwenden von Schnellansichten zum ERstellen von benutzerdefinierten Popups](custom-pop-ups.md) 

Siehe auch [Einrichten dynamischer Medien](administering-dynamic-media.md).

<!-- 

OBSOLETE UNTIL INTEGRATING SCENE7 TOPIC GETS A MAJOR UPDATE
>[!NOTE]
>
>To understand the differences between using Dynamic Media and integrating Dynamic Media Classic with AEM, see [Dynamic Media Classic integration versus Dynamic Media](/help/sites-cloud/administering/integrating-scene7.md#aem-scene-integration-versus-dynamic-media).

-->

## Dynamische Medien aktiviert und Dynamische Medien deaktiviert {#dynamic-media-on-versus-dynamic-media-off}

Sie können anhand der folgenden Eigenschaften feststellen, ob dynamische Medien aktiviert (aktiviert) sind:

* Dynamische Darstellungen sind beim Herunterladen oder Anzeigen einer Vorschau von Assets verfügbar.
* Bildsätze, Rotationssets und gemischte Mediensets sind verfügbar.
* PTIFF-Ausgabeformate werden erstellt.

Wenn Sie auf ein Bild-Asset klicken, unterscheidet sich die Ansicht des Assets von der Anzeige für dynamische Medien. Dynamic Media nutzt die On-Demand-HTML5-Viewer.

### Dynamic renditions {#dynamic-renditions}

Dynamische Ausgabeformate wie Bild- und Viewer-Vorgaben (unter **[!UICONTROL Dynamisch]**) sind verfügbar, wenn Dynamic Media aktiviert ist.

![chlimage_1-358](assets/chlimage_1-358.png)

### Bildsets, Rotationssets und Sets für gemischte Medien {#image-sets-spins-sets-mixed-media-sets}

Bildsets, Rotationssets und Sets für gemischte Medien sind verfügbar, wenn Dynamic Media aktiviert ist.

![chlimage_1-359](assets/chlimage_1-359.png)

### PTIFF renditions {#ptiff-renditions}

Dynamic media enabled assets include `pyramid.tiffs`.

![chlimage_1-360](assets/chlimage_1-360.png)

### Änderung der Asset-Ansichten {#asset-views-change}

With Dynamic Media enabled, you can zoom in and out by clicking the `+` and `-` buttons. You can also click/tap to zoom into certain area. Revert brings you to the original version and you can make the image full screen by clicking the diagonal arrows. Dynamic Media enabled looks like this:

![chlimage_1-361](assets/chlimage_1-361.png)

Bei deaktivierten dynamischen Medien können Sie ein- und auszoomen und die Originalgröße wiederherstellen:

![chlimage_1-362](assets/chlimage_1-362.png)
