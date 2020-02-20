---
title: Bereitstellen von Dynamic Media Assets
description: Informationen zum Bereitstellen von Dynamic Media Assets
translation-type: tm+mt
source-git-commit: 218afb360ec3a13f2f4562a703ca3184083fa7f6

---


# Bereitstellen von Dynamic Media Assets{#delivering-dynamic-media-assets}

Wie Sie Dynamic Media Assets (sowohl Videos als auch Bilder) bereitstellen können, ist davon abhängig, wie Ihre Website implementiert ist.

Mit Dynamic Media haben Sie mehrere Optionen:

* Wenn Ihre Website auf AEM gehostet ist, können Sie die Dynamic Media Assets direkt zu Ihrer Seite hinzufügen.
* Wenn sich Ihre Website nicht auf AEM befindet, können Sie eine der folgenden Aktionen ausführen:

   * Betten Sie Ihr Video oder Bild auf Ihrer Website ein.
   * Verknüpfen Sie URLs mit Ihrer Webanwendung. Verwenden Sie die Verknüpfung, wenn Sie einen Videoplayer als Popup- oder modales Fenster bereitstellen möchten.
   * Wenn Ihre Website dynamisch ist, können Sie [optimierte Bilder bereitstellen](/help/assets/dynamic-media/responsive-site.md).

>[!NOTE]
>
>Die intelligente Bildbearbeitung arbeitet mit bestehenden Bildvorgaben und reduziert in der letzten Sekunde abhängig vom Browser oder der Geschwindigkeit der Netzverbindung die Größe der Bilddatei intelligent noch weiter. See [Smart Imaging](/help/assets/dynamic-media/imaging-faq.md) for more information.

Weitere Informationen finden Sie in den folgenden Themen:

* [Hinzufügen von Dynamic Media Assets zu Webseiten](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md)
* [Einbetten des Video- oder Bild-Viewers auf einer Webseite](/help/assets/dynamic-media/embed-code.md)
* [Aktivieren des Hotlink-Schutzes in Dynamic Media](/help/assets/dynamic-media/hotlink-protection.md)
* [Verknüpfen von URLs mit einer Webanwendung](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md)
* [Bereitstellen von optimierten Bildern für eine responsive Site](/help/assets/dynamic-media/responsive-site.md)
* [Bereitstellung von Inhalten per HTTP/2 – Häufig gestellte Fragen ()](/help/assets/dynamic-media/http2faq.md)
* [Ungültigmachen von Inhalten im CDN-Cache](/help/assets/dynamic-media/invalidate-cdn-cached-content.md)
* [Regelsätze zum Konvertieren von URLs](/help/assets/dynamic-media/using-rulesets-to-transform-urls.md) 

## Bereitstellung von Dynamic Media-Assets über HTTP/2 {#http-delivery-of-dynamic-media-assets}

AEM unterstützt jetzt die Bereitstellung aller Dynamic Media-Inhalte (Bilder und Videos) über HTTP/2. Das heißt, dass eine veröffentlichte URL oder ein eingebetteter Code für ein Bild oder Video verfügbar ist und in beliebige Anwendungen integriert werden kann, die gehostete Assets akzeptiert. Dieses veröffentlichte Asset wird dann über das HTTP/2-Protokoll bereitgestellt. Dieses Bereitstellungsverfahren verbessert die Kommunikation zwischen Browser und Server und verbessert die Antwort- und Ladezeiten aller Dynamic Media-Assets.

Weitere Informationen finden Sie in den [Häufig gestellten Fragen zur Bereitstellung von Inhalten über HTTP/2](/help/assets/dynamic-media/http2faq.md).
