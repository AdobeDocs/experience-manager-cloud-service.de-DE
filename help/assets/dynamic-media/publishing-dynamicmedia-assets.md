---
title: Veröffentlichen von Assets mit dynamischen Medien
description: Anleitung zum Veröffentlichen von Asset mit dynamischen Medien
translation-type: tm+mt
source-git-commit: c8f8598e3e476af529a87b056e66ddb619a2da0a

---


# Veröffentlichen von Assets mit dynamischen Medien {#publishing-dynamic-media-assets}

You publish your Dynamic Media assets by selecting the assets and tapping **[!UICONTROL Publish]**. Nachdem Sie Ihre dynamischen Medien-Assets veröffentlicht haben, können Sie sie über URL oder Einbettung in eine Webseite einbetten.

Sie können Assets, die Sie hochladen, auch sofort veröffentlichen - ohne Benutzereingriff. Sie können diese Assets auch selektiv veröffentlichen. Informationen hierzu finden Sie unter [Konfigurieren von dynamischen Medien](config-dm.md).

In der **[!UICONTROL Kartenansicht]** wird ein kleines Globussymbol direkt unter dem Namen eines Assets angezeigt, um anzuzeigen, dass es veröffentlicht wurde. In der **[!UICONTROL Listenansicht]** gibt die Spalte **[!UICONTROL Veröffentlicht]** an, welche Assets veröffentlicht wurden und welche nicht.

>[!NOTE]
>
>Wenn ein Asset bereits veröffentlicht wurde, dann verwenden Sie AEM, um das Asset in einen anderen Ordner zu verschieben und erneut zu veröffentlichen, dann ist der ursprüngliche Speicherort des veröffentlichten Assets zusammen mit dem neu veröffentlichten Asset weiterhin verfügbar. Das ursprünglich veröffentlichte Asset geht jedoch an AEM verloren und kann nicht rückgängig gemacht werden. Daher sollten Sie die Veröffentlichung von Assets zuerst rückgängig machen, bevor Sie sie in einen anderen Ordner verschieben.

Wenn Sie Video-Assets unmittelbar nach der Kodierung veröffentlichen möchten, stellen Sie sicher, dass die Kodierung abgeschlossen ist. Wenn Videos noch kodiert werden, informiert das System Sie darüber, dass ein Videoverarbeitungsvorgang läuft. Wenn die Videokodierung abgeschlossen ist, sollten Sie die Videodarstellungen Vorschau haben. An diesem Punkt können Sie die Videos ohne Veröffentlichungsfehler veröffentlichen.

Siehe auch [Verknüpfen von URLs mit einer Webanwendung](linking-urls-to-yourwebapplication.md).

Informationen hierzu finden Sie unter [Einbetten des Video-Viewers auf einer Webseite](embed-code.md).

>[!NOTE]
>
>* Assets müssen zunächst veröffentlicht werden, bevor Sie die URL verwenden können. Wenn Assets nicht veröffentlicht sind, können Sie die URL nicht kopieren und in einen Webbrowser einfügen.
>* Bild- und Viewer-Vorgaben müssen für die Live-Bereitstellung aktiviert und veröffentlicht sein.
>



Ausführliche Informationen zum Veröffentlichen von Sets oder des Assets finden Sie unter [Veröffentlichen von Assets](/help/assets/manage-digital-assets.md). 

## Bereitstellung von Dynamic Media-Assets über HTTP/2 {#http-delivery-of-dynamic-media-assets}

AEM unterstützt jetzt die Bereitstellung aller Dynamic Media-Inhalte (Bilder und Videos) über HTTP/2. Das heißt, dass eine veröffentlichte URL oder ein eingebetteter Code für ein Bild oder Video verfügbar ist und in beliebige Anwendungen integriert werden kann, die gehostete Assets akzeptiert. Dieses veröffentlichte Asset wird dann über das HTTP/2-Protokoll bereitgestellt. Dieses Bereitstellungsverfahren verbessert die Kommunikation zwischen Browser und Server und verbessert die Antwort- und Ladezeiten aller Dynamic Media-Assets.

See [HTTP/2 delivery of content frequently asked questions](/help/assets/dynamic-media/http2faq.md) to learn more.
<!--this md file used to reside under sites-administering-->
