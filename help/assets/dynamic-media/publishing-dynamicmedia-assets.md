---
title: Veröffentlichen von Dynamic Media-Assets
description: Anleitung zum Veröffentlichen von Asset mit dynamischen Medien
contentOwner: Rick Brough
translation-type: tm+mt
source-git-commit: d84a6692f2d0aae496bd2bd98ac99c2663f3fe52
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 77%

---


# Veröffentlichen von Dynamic Media-Assets  {#publishing-dynamic-media-assets}

Sie veröffentlichen Ihre Assets für dynamische Medien, indem Sie die bereits hochgeladenen Assets auswählen und auf **[!UICONTROL Veröffentlichen]** oder **[!UICONTROL Schnelle Veröffentlichung]** tippen. Nachdem Sie Ihre dynamischen Medien-Assets veröffentlicht haben, können Sie sie über eine URL oder durch Einbetten von Code auf der Seite in eine Webseite einfügen.

Sie können hochgeladene Assets auch umgehend und ohne Benutzerinteraktion veröffentlichen. Sie können diese Assets auch selektiv veröffentlichen. Informationen hierzu finden Sie unter [Konfigurieren von Dynamic Media](config-dm.md).

In der Ansicht **[!UICONTROL &quot;]** Karte&quot;wird ein kleines Globussymbol direkt unter dem Namen des Assets sowie links neben dem Datum und der Uhrzeit angezeigt, um anzugeben, dass es veröffentlicht wurde. In der **[!UICONTROL Listenansicht]** gibt eine Spalte **[!UICONTROL Veröffentlicht]** an, welche Assets veröffentlicht sind.

>[!NOTE]
>
>Wenn Sie ein bereits veröffentlichtes Asset in AEM in einen anderen Ordner verschieben und anschließend aus dem neuen Speicherort erneut veröffentlichen, ist der ursprünglich veröffentlichte Asset-Speicherort weiterhin zusammen mit dem neu veröffentlichten Asset verfügbar. Das ursprünglich veröffentlichte Asset ist allerdings für AEM nicht mehr zugänglich. Daher kann dessen Veröffentlichung nicht rückgängig gemacht werden. Deshalb wird empfohlen, dass Sie die Veröffentlichung von Assets zunächst rückgängig machen, bevor Sie sie in einen anderen Ordner verschieben.

Wenn Sie Video-Assets sofort nach der Kodierung veröffentlichen möchten, achten Sie darauf, dass die Kodierung komplett abgeschlossen ist. Wenn Videos noch kodiert werden, erhalten Sie eine Systemmeldung, dass ein Videoverarbeitungs-Workflow aktiv ist. Nach Abschluss der Videokodierung sollte eine Vorschau der Videoausgabeformate möglich sein. Jetzt können Sie die Videos veröffentlichen, ohne dass Publishing-Fehler auftreten.

Siehe auch [Verknüpfen von URLs mit einer Web-Anwendung](linking-urls-to-yourwebapplication.md).

See also [Embedding the Dynamic Media Video viewer or Image viewer on a web page.](embed-code.md)

>[!NOTE]
>
>* Assets müssen zunächst veröffentlicht werden, bevor Sie die URL verwenden können. Wenn Assets nicht veröffentlicht sind, können Sie die URL nicht kopieren und in einen Webbrowser einfügen.
>* Bild- und Viewer-Vorgaben müssen für die Live-Bereitstellung aktiviert und veröffentlicht sein.
>



Ausführliche Informationen zum Veröffentlichen von Sets oder des Assets finden Sie unter [Veröffentlichen von Assets](/help/assets/manage-digital-assets.md). 

## Bereitstellung von Dynamic Media-Assets über HTTP/2  {#http-delivery-of-dynamic-media-assets}

AEM unterstützt jetzt die Bereitstellung aller Dynamic Media-Inhalte (Bilder und Videos) über HTTP/2. Das heißt, dass eine veröffentlichte URL oder ein eingebetteter Code für ein Bild oder Video verfügbar ist und in beliebige Anwendungen integriert werden kann, die gehostete Assets akzeptiert. Dieses veröffentlichte Asset wird dann über das HTTP/2-Protokoll bereitgestellt. Dieses Bereitstellungsverfahren verbessert die Kommunikation zwischen Browser und Server und verbessert die Antwort- und Ladezeiten aller Dynamic Media-Assets.

Weitere Informationen finden Sie unter [Häufig gestellte Fragen zur Bereitstellung von Inhalten über HTTP/2](/help/assets/dynamic-media/http2faq.md).
<!--this md file used to reside under sites-administering-->
