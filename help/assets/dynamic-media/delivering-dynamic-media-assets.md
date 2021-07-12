---
title: Bereitstellen von Dynamic Media-Assets
description: Informationen zum Bereitstellen von Dynamic Media-Assets.
feature: Asset-Management
role: User
exl-id: 4557b561-b3c4-4d6f-8044-2069bda41613
source-git-commit: 24a4a43cef9a579f9f2992a41c582f4a6c775bf3
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 100%

---

# Bereitstellen von Dynamic Media-Assets{#delivering-dynamic-media-assets}

Wie Sie Dynamic Media-Assets (sowohl Videos als auch Bilder) bereitstellen können, ist davon abhängig, wie Ihre Website implementiert ist.

Mit Dynamic Media haben Sie mehrere Optionen:

* Wenn Ihre Website auf Adobe Experience Manager gehostet wird, können Sie die Dynamic Media-Assets direkt zu Ihrer Seite hinzufügen.
* Wenn sich Ihre Website nicht in Experience Manager befindet, können Sie eine der folgenden Aktionen ausführen:

   * Betten Sie Ihr Video oder Bild auf Ihrer Website ein.
   * Verknüpfen Sie URLs mit Ihrer Web-Anwendung. Verwenden Sie die Verknüpfung, wenn Sie einen Video-Player als Popup- oder modales Fenster bereitstellen möchten.
   * Wenn Ihre Website dynamisch ist, können Sie [optimierte Bilder bereitstellen](/help/assets/dynamic-media/responsive-site.md).

>[!NOTE]
>
>Die intelligente Bildbearbeitung funktioniert mit Ihren vorhandenen Bildvorgaben. Sie nutzt die intelligenten Funktionen ganz zum Schluss, um die Größe der Bilddatei abhängig vom Browser oder der Geschwindigkeit der Netzverbindung noch weiter zu verringern. Weitere Informationen finden Sie unter [Intelligente Bildbearbeitung](/help/assets/dynamic-media/imaging-faq.md).

Weitere Informationen finden Sie in den folgenden Themen:

* [Hinzufügen von Dynamic Media-Assets zu Web-Seiten](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md)
* [Einbetten des Video- oder Bild-Viewers auf einer Web-Seite](/help/assets/dynamic-media/embed-code.md)
* [Aktivieren des Hotlink-Schutzes in Dynamic Media](/help/assets/dynamic-media/hotlink-protection.md)
* [Verknüpfen von URLs mit einer Web-Anwendung](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md)
* [Bereitstellen von optimierten Bildern für eine responsive Website](/help/assets/dynamic-media/responsive-site.md)
* [Bereitstellung von Inhalt über HTTP/2 ](/help/assets/dynamic-media/http2faq.md)
* [Invalidierung des CDN-Cache über Dynamic Media](/help/assets/dynamic-media/invalidate-cdn-cache-dynamic-media.md)
* [Invalidierung des CDN-Cache mithilfe von Dynamic Media Classic](/help/assets/dynamic-media/invalidate-cdn-cache-dm-classic.md)
* [Verwenden von Regelsätzen zum Konvertieren von URLs](/help/assets/dynamic-media/using-rulesets-to-transform-urls.md)

## Bereitstellung von Dynamic Media-Assets über HTTP/2   {#http-delivery-of-dynamic-media-assets}

Experience Manager unterstützt jetzt die Bereitstellung aller Dynamic Media-Inhalte (Bilder und Videos) über HTTP/2. Das heißt, dass eine veröffentlichte URL oder ein eingebetteter Code für ein Bild oder Video verfügbar ist und in beliebige Programme integriert werden kann, die gehostete Assets akzeptiert. Dieses veröffentlichte Asset wird dann über das HTTP/2-Protokoll bereitgestellt. Dieses Bereitstellungsverfahren verbessert die Kommunikation zwischen Browser und Server und verbessert die Antwort- und Ladezeiten aller Dynamic Media-Assets.

Weitere Informationen finden Sie unter [Bereitstellung von Inhalten per HTTP/2 – Häufig gestellte Fragen (FAQ)](/help/assets/dynamic-media/http2faq.md).
