---
title: Einbetten des Dynamic Media-Video- oder Bild-Viewers auf einer Web-Seite
description: Erfahren Sie, wie Sie Dynamic Media-Video- oder -Bild-Assets in eine Web-Seite einbetten.
feature: Asset-Verwaltung
role: Business Practitioner
exl-id: 76335781-e39f-4aae-967f-5af8634d8f61
source-git-commit: 1ad89be4ebddec0705c6f557fed3d697b9f1f3a7
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 90%

---

# Einbetten des Dynamic Media-Video-, Bild- oder Dimensional-Viewers auf einer Web-Seite {#embedding-the-video-or-image-viewer-on-a-web-page}

Verwenden Sie die Funktion **[!UICONTROL Einbettungs-Code]**, wenn Sie ein Video wiedergeben oder ein Asset anzeigen möchten, das auf einer Web-Seite eingebettet wurde. Kopieren Sie den Einbettungs-Code in die Zwischenablage, damit Sie ihn in die Web-Seiten einfügen können. Der Code kann im Dialogfeld **[!UICONTROL Einbettungs-Code]** nicht bearbeitet werden.

Sie betten URLs nur ein, wenn Sie _nicht_ Adobe Experience Manager als WCM verwenden. Wenn Sie Experience Manager als WCM verwenden, [fügen Sie die Assets direkt auf Ihrer Seite](adding-dynamic-media-assets-to-pages.md) hinzu.

Siehe [Verknüpfen von URLs mit einer Web-Anwendung](linking-urls-to-yourwebapplication.md).

Siehe [Bereitstellen von optimierten Bildern für eine responsive Site](responsive-site.md).

>[!NOTE]
>
>Der eingebettete Code kann erst kopiert werden, nachdem Sie das ausgewählte Asset veröffentlicht haben. Darüber hinaus müssen Sie die Viewer-Vorgabe oder die Bildvorgabe veröffentlichen.
>
>Siehe [Veröffentlichen von Assets](publishing-dynamicmedia-assets.md).
>
>Siehe [Veröffentlichen von Viewer-Vorgaben](managing-viewer-presets.md#publishing-viewer-presets).
>
>Siehe [Veröffentlichen von Bildvorgaben](managing-image-presets.md#publishing-image-presets).

**So betten Sie den Dynamic Media-Video- oder Bild-Viewer auf einer Web-Seite ein:**

1. Navigieren Sie zum *veröffentlichten* Video- oder Bild-Asset, dessen Einbettungs-Code Sie kopieren möchten.

   Denken Sie daran, dass der Einbettungscode nur *nach* der ersten *Veröffentlichung* der Assets kopiert werden können. Darüber hinaus müssen die Viewer-Vorgabe oder die Bildvorgabe ebenfalls veröffentlicht werden.

   Siehe [Veröffentlichen von Assets](publishing-dynamicmedia-assets.md).

   Siehe [Veröffentlichen von Viewer-Vorgaben](managing-viewer-presets.md#publishing-viewer-presets).

   Siehe [Veröffentlichen von Bildvorgaben](managing-image-presets.md#publishing-image-presets).

1. Wählen Sie in der linken Leiste die Dropdown-Liste aus und tippen Sie auf **[!UICONTROL Viewer]**.
1. Tippen Sie auf der linken Schiene auf den Namen einer Viewer-Vorgabe. Die Viewer-Vorgabe wird auf das Asset angewendet.
1. Tippen Sie auf **[!UICONTROL Einbetten]**.
1. Kopieren Sie im Dialogfeld **[!UICONTROL Einbettungs-Code]** den gesamten Code in die Zwischenablage und tippen Sie dann auf **[!UICONTROL Schließen]**.
1. Fügen Sie den Integrations-Code in die Web-Seiten ein.

## Verwendung von HTTP/2 zur Bereitstellung von Dynamic Media-Assets {#using-http-to-deliver-your-dynamic-media-assets}

HTTP/2 ist das neue, aktualisierte Web-Protokoll, das die Kommunikation zwischen Browser und Servern verbessert. Es beschleunigt die Übertragung von Informationen und reduziert die erforderliche Prozessorleistung. Es ist jetzt möglich, Dynamic Media-Assets über HTTP/2 bereitzustellen, das schnellere Reaktions- und Ladezeiten bietet.

Vollständige Informationen zu den ersten Schritten mit HTTP/2 und Ihrem Dynamic Media-Konto finden Sie unter [Bereitstellung von Inhalt über HTTP/2](http2faq.md).
