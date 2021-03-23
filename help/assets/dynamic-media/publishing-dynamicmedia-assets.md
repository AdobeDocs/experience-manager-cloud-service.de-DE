---
title: Veröffentlichen von Dynamic Media-Assets
description: Informationen zum Veröffentlichen von Dynamic Media-Assets.
contentOwner: Rick Brough
feature: Asset-Verwaltung
topic: Geschäftspraktiker
translation-type: tm+mt
source-git-commit: 15cf59ccc5cef515bfbda2da790fa5eaf0247721
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 59%

---


# Veröffentlichen von Dynamic Media-Assets  {#publishing-dynamic-media-assets}

Sie veröffentlichen Ihre Dynamic Media-Assets, indem Sie die bereits hochgeladenen Assets auswählen und auf **[!UICONTROL Veröffentlichen]** oder **[!UICONTROL Quick Publish]** tippen. Nach dem Veröffentlichen Ihrer Dynamic Media-Assets können diese auf einer Web-Seite über eine URL eingebunden oder mittels Code eingebettet werden.

Sie können hochgeladene Assets auch umgehend und ohne Benutzerinteraktion veröffentlichen. Sie können diese Assets auch selektiv veröffentlichen. Informationen hierzu finden Sie unter [Konfigurieren von Dynamic Media.](config-dm.md) Sie können Assets auch selektiv auf Dynamic Media oder Adobe Experience Manager veröffentlichen und sich gegenseitig ausschließen, indem Sie auf Ordnerebene  **[!UICONTROL Selektive]** Veröffentlichung verwenden. Siehe [Arbeiten mit selektiver Veröffentlichung in Dynamic Media](/help/assets/dynamic-media/selective-publishing.md).

In der **[!UICONTROL Kartenansicht]** wird ein kleines Globussymbol direkt unter dem Namen eines Assets und links von Datum und Uhrzeit angezeigt, um anzuzeigen, dass es veröffentlicht wurde. In der **[!UICONTROL Listenansicht]** gibt eine Spalte **[!UICONTROL Veröffentlicht]** an, welche Assets veröffentlicht sind.

>[!NOTE]
>
>Wenn ein Asset bereits veröffentlicht ist, verschieben Sie das Asset in einen anderen Ordner und veröffentlichen Sie es erneut von seinem neuen Speicherort aus. Der ursprüngliche Speicherort des veröffentlichten Assets sowie das neu veröffentlichte Asset sind weiterhin verfügbar. Das ursprünglich veröffentlichte Asset geht jedoch an den Experience Manager verloren und kann nicht rückgängig gemacht werden. Daher sollten Sie die Veröffentlichung von Assets zuerst rückgängig machen, bevor Sie sie in einen anderen Ordner verschieben.

Wenn Sie Video-Assets unmittelbar nach der Kodierung veröffentlichen möchten, stellen Sie sicher, dass die Kodierung abgeschlossen ist. Wenn Videos kodiert werden, informiert das System Sie darüber, dass ein Arbeitsablauf zur Videoverarbeitung ausgeführt wird. Nach Abschluss der Videokodierung können Sie die Videodarstellungen Vorschau haben. Jetzt können Sie die Videos veröffentlichen, ohne dass Publishing-Fehler auftreten.

Siehe auch [Verknüpfen von URLs mit einer Web-Anwendung](linking-urls-to-yourwebapplication.md).

Siehe auch [Einbetten des Dynamic Media-Video- oder Bild-Viewers auf einer Web-Seite.](embed-code.md)

>[!NOTE]
>
>* Assets müssen veröffentlicht werden, um die URL verwenden zu können. Wenn die Assets nicht veröffentlicht werden, funktioniert das Kopieren und Einfügen der URL in einen Webbrowser nicht.
>* Bild- und Viewer-Vorgaben müssen für die Live-Bereitstellung aktiviert und veröffentlicht sein.

>



Ausführliche Informationen zum Veröffentlichen von Sets oder des Assets finden Sie unter [Veröffentlichen von Assets](/help/assets/manage-digital-assets.md).

## Bereitstellung von Dynamic Media-Assets über HTTP/2   {#http-delivery-of-dynamic-media-assets}

Experience Manager unterstützt jetzt den Versand aller Dynamic Media-Inhalte (Bilder und Videos) über HTTP/2. Das heißt, dass eine veröffentlichte URL oder ein eingebetteter Code für ein Bild oder Video verfügbar ist und in beliebige Programme integriert werden kann, die gehostete Assets akzeptiert. Dieses veröffentlichte Asset wird dann über das HTTP/2-Protokoll bereitgestellt. Dieses Bereitstellungsverfahren verbessert die Kommunikation zwischen Browser und Server und verbessert die Antwort- und Ladezeiten aller Dynamic Media-Assets.

Siehe [HTTP/2 Versand des Inhalts Häufig gestellte Fragen](/help/assets/dynamic-media/http2faq.md).

<!--this md file used to reside under sites-administering-->
