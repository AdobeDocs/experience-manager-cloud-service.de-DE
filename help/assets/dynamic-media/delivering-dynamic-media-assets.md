---
title: Bereitstellen von Dynamic Media-Assets
description: Informationen zum Bereitstellen von Dynamic Media-Assets.
feature: Asset-Verwaltung
topic: Geschäftspraktiker
translation-type: tm+mt
source-git-commit: 69c865dbc87ca021443e53b61440faca8fa3c4d4
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 77%

---


# Bereitstellen von Dynamic Media-Assets{#delivering-dynamic-media-assets}

Wie Sie Dynamic Media-Assets (sowohl Videos als auch Bilder) bereitstellen können, ist davon abhängig, wie Ihre Website implementiert ist.

Dynamic Media bietet mehrere Optionen:

* Wenn Ihre Website auf AEM gehostet wird, möchten Sie die Dynamic Media-Assets direkt zu Ihrer Seite hinzufügen.
* Wenn sich Ihre Website nicht in AEM befindet, können Sie eine der folgenden Aktionen ausführen:

   * Betten Sie Ihr Video oder Bild auf Ihrer Website ein.
   * Verknüpfen Sie URLs mit Ihrer Web-Anwendung. Verwenden Sie die Verknüpfung, wenn Sie einen Video-Player als Popup- oder modales Fenster bereitstellen möchten.
   * Wenn Ihre Website dynamisch ist, können Sie [optimierte Bilder bereitstellen](/help/assets/dynamic-media/responsive-site.md).

>[!NOTE]
>
>Intelligente Bildbearbeitung funktioniert mit Ihren vorhandenen Bildvorgaben. Es verwendet Intelligenz in der letzten Millisekunde des Versands, um die Dateigröße je nach Browser- oder Netzwerkverbindungsgeschwindigkeit weiter zu reduzieren. Weitere Informationen finden Sie unter [Intelligente Bildbearbeitung](/help/assets/dynamic-media/imaging-faq.md).

Weitere Informationen finden Sie in den folgenden Themen:

* [Hinzufügen von Dynamic Media-Assets zu Web-Seiten](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md)
* [Einbetten des Video- oder Bild-Viewers auf einer Web-Seite](/help/assets/dynamic-media/embed-code.md)
* [Aktivieren des Hotlink-Schutzes in Dynamic Media](/help/assets/dynamic-media/hotlink-protection.md)
* [Verknüpfen von URLs mit einer Web-Anwendung](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md)
* [Bereitstellen von optimierten Bildern für eine responsive Site](/help/assets/dynamic-media/responsive-site.md)
* [Bereitstellung von Inhalt über HTTP/2 ](/help/assets/dynamic-media/http2faq.md)
* [Invalidierung des CDN-Cache über Dynamic Media](/help/assets/dynamic-media/invalidate-cdn-cache-dynamic-media.md)
* [Invalidierung des CDN-Cache über von Dynamic Media Classic](/help/assets/dynamic-media/invalidate-cdn-cache-dm-classic.md)
* [Verwenden von Regelsätzen zum Konvertieren von URLs](/help/assets/dynamic-media/using-rulesets-to-transform-urls.md)

## Bereitstellung von Dynamic Media-Assets über HTTP/2  {#http-delivery-of-dynamic-media-assets}

AEM unterstützt jetzt die Bereitstellung aller Dynamic Media-Inhalte (Bilder und Videos) über HTTP/2. Das heißt, dass eine veröffentlichte URL oder ein eingebetteter Code für ein Bild oder Video verfügbar ist und in beliebige Programme integriert werden kann, die gehostete Assets akzeptiert. Dieses veröffentlichte Asset wird dann über das HTTP/2-Protokoll bereitgestellt. Dieses Bereitstellungsverfahren verbessert die Kommunikation zwischen Browser und Server und verbessert die Antwort- und Ladezeiten aller Dynamic Media-Assets.

Weitere Informationen finden Sie unter [HTTP/2 Versand of Content Frequently Asked Questions](/help/assets/dynamic-media/http2faq.md).
