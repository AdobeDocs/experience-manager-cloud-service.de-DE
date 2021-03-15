---
title: Bereitstellung von Inhalten per HTTP/2 – Häufig gestellte Fragen (FAQ)
description: Erfahren Sie mehr über die Bereitstellung von Inhalten per HTTP/2.
translation-type: tm+mt
source-git-commit: 20e37c385c2d3df91e37095bcf8a630fbfccbd16
workflow-type: tm+mt
source-wordcount: '786'
ht-degree: 73%

---


# Bereitstellung von Inhalten per HTTP/2 – Häufig gestellte Fragen (FAQ) {#http-delivery-of-content-faq}

Adobe freut sich, die Verfügbarkeit der HTTP/2-Bereitstellung von Inhalten bekannt zu geben. Bei Verwendung von HTTP/2 wird die Gesamtleistung gesteigert.

>[!NOTE]
>
>Für diese Funktion müssen Sie das im Lieferumfang von Adobe Experience Manager Dynamic Media enthaltene Out-of-the-Box-CDN verwenden. Andere benutzerdefinierte CDN werden von dieser Funktion nicht unterstützt.

## Was ist HTTP/2? {#what-is-http}

HTTP/2 verbessert die Kommunikation zwischen Browsern und Servern, ermöglicht eine schnellere Übertragung von Informationen und verringert den Verarbeitungsaufwand.

Auf der folgenden Website werden HTTP/2 und seine Vorteile kurz und einfach beschrieben:

[https://www.engadget.com/2015/02/24/what-you-need-to-know-about-http-2/](https://www.engadget.com/2015/02/24/what-you-need-to-know-about-http-2/)

## Was sind die wichtigsten Vorteile der Umstellung auf die Bereitstellung von Inhalt über HTTP/2? {#what-are-the-key-benefits-of-moving-to-http-for-content-delivery}

Die Leistungsverbesserung variiert stark, da sie auf verschiedenen Faktoren basiert. Beispielsweise den Code Ihrer Website, die Verwendung von Dynamic Media, das Gerät, den Bildschirm und den Standort des Verbrauchers.

Von Adobe durchgeführte Prüfungen führten zu folgenden Ergebnissen:

* Bei Bildern wurde die Reaktionszeit je nach Gerät und Browser um 7–28 % verbessert. Die bedeutendste Leistungssteigerung war bei iOS-Geräten zu beobachten.
* Die Ladezeitleistung für Viewer wurde um 15 % verbessert.

Die folgende Demonstration zeigt den Unterschied zwischen Laden mit HTTP/1 und Laden mit HTTP/2:

[https://http2.akamai.com/demo](https://http2.akamai.com/demo)

## Bin ich berechtigt, auf HTTP/2 umzustellen?  {#am-i-eligible-to-switch-over-to-http}

Um HTTP/2 verwenden zu können, müssen Sie die folgenden Voraussetzungen erfüllen:

* Sie verwenden sicheres HTTPS für Ihre Rich Media-Anforderungen.
* Verwenden Sie das Adobe-Bundle CDN (Content Versand Network) als Teil Ihrer Dynamic Media Classic-Lizenz.
* Verwenden Sie eine dedizierte Domain (d. h. `images.company.com` oder `mycompany.scene7.com`), keine generische Dynamic Media-Domain (d. h. `s7d1.scene7.com`, `s7d2.scene7.com` oder `s7d13.scene7.com`).

   Öffnen Sie das [Dynamic Media Classic-Desktop-Programm](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html?lang=de#getting-started) und melden Sie sich bei Ihrem Konto an, um Ihre Domains zu finden.

   Klicken Sie auf **[!UICONTROL Einstellungen > Anwendungseinstellungen > Allgemeine Einstellungen]**. Suchen Sie nach dem Feld **Veröffentlichungs-Server-Name**. Wenn Sie derzeit eine generische Dynamic Media-Domain verwenden, können Sie im Zuge dieser Umstellung einen Wechsel zu Ihrer eigenen benutzerdefinierten Domain beantragen.

## Wie verläuft der Prozess für die Aktivierung von HTTP/2 für mein Dynamic Media-Konto? {#what-is-the-process-for-enabling-http-for-my-dm-account}

[Verwenden Sie die Admin Console, um einen Support-](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) Fall zu erstellen, und fordern Sie den Umstieg auf HTTP/2 an. es wird nicht automatisch für Sie durchgeführt.

1. Geben Sie in Ihrem Support-Fall die folgenden Informationen an:

   * Name, E-Mail-Adresse und Telefonnummer des Primärkontakts
   * Alle Domains, die auf HTTP/2 umgestellt werden sollen. Das heißt, `images.company.com` oder `mycompany.scene7.com`.

   Öffnen Sie das [Dynamic Media Classic-Desktop-Programm](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started) und melden Sie sich bei Ihrem Konto an, um Ihre Domains zu finden.

   Klicken Sie auf **[!UICONTROL Einstellungen > Anwendungseinstellungen > Allgemeine Einstellungen]**. Suchen Sie nach dem Feld **[!UICONTROL Veröffentlichungs-Server-Name]**.

   * Vergewissern Sie sich, dass Sie sicheres HTTPS für Rich Media-Anforderungen verwenden.
   * Stellen Sie sicher, dass Sie das CDN über Adobe und nicht über eine direkte Beziehung verwenden.
   * Stellen Sie sicher, dass Sie eine dedizierte Domain verwenden. Das heißt, `images.company.com` oder `mycompany.scene7.com`, nicht eine generische Dynamic Media-Domain wie `s7d1.scene7.com`, `s7d2.scene7.com`, `s7d13.scene7.com`.

   Öffnen Sie das [Dynamic Media Classic-Desktop-Programm](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started) und melden Sie sich bei Ihrem Konto an, um Ihre Domains zu finden.

   Klicken Sie auf **[!UICONTROL Einstellungen > Anwendungseinstellungen > Allgemeine Einstellungen]**. Suchen Sie nach dem Feld **[!UICONTROL Veröffentlichungs-Server-Name]**. Wenn Sie derzeit eine generische Dynamic Media-Domain verwenden, können Sie im Zuge dieser Umstellung einen Wechsel zu Ihrer eigenen benutzerdefinierten Domain beantragen.

   1. Der technische Support fügt Sie entsprechend der Reihenfolge der eingegangenen Anfragen der HTTP/2-Kundenwarteschlange hinzu.
   1. Wenn die Adobe bereit ist, Ihre Anfrage zu bearbeiten, kontaktiert der Kundendienst Sie, um die Transition zu koordinieren und ein Datum für die Zielgruppe festzulegen.
   1. Nach Abschluss werden Sie benachrichtigt, wonach Sie prüfen können, ob die Umstellung auf HTTP/2 erfolgreich durchgeführt wurde.



## Wann kann ich mit der Umstellung auf HTTP/2 rechnen? {#when-can-i-expect-to-be-transitioned-over-to-http}

Anfragen werden in der Reihenfolge verarbeitet, in der sie beim technischen Support eingehen.

>[!NOTE]
>
>Es gibt eine lange Vorlaufzeit, da bei der Transition zu HTTP/2 der Cache gelöscht werden muss. Es können daher nur wenige Umstellungen zugleich durchgeführt werden.

## Welche Risiken sind mit der Umstellung auf HTTP/2 verbunden?   {#what-are-the-risks-with-moving-to-http}

Durch die Umstellung auf HTTP/2 wird Ihr Cache im CDN gelöscht, da eine neue CDN-Konfiguration erforderlich ist.

Der nicht zwischengespeicherte Inhalt wird direkt an die ursprünglichen Server von Adobe übertragen, bis der Cache neu aufgebaut wird. Aufgrund dieser Aktion plant Adobe, mehrere Transitionen gleichzeitig zu bearbeiten. Auf diese Weise wird sichergestellt, dass beim Abrufen von Anforderungen aus der Herkunft eine annehmbare Leistung gewährleistet ist.

## Wie kann festgestellt werden, ob eine URL oder eine Website mit HTTP/2 aktiviert wurde?   {#how-can-you-verify-whether-a-url-or-website-is-activated-with-http}

Laden Sie eine Erweiterung herunter, die mit Ihrem Webbrowser verwendet werden soll. Für Firefox und Chrome gibt es die Erweiterung **[!UICONTROL HTTP/2 und SPDY Indicator]**. Da Browser HTTP/2 nur bei sicheren Verbindungen unterstützen, muss für die Verifizierung eine URL mit HTTPS aufgerufen werden. Wenn HTTP/2 unterstützt wird, wird es durch die Erweiterung in Form eines blauen Flashs und einer Kopfzeile &quot;X-Firefox-Spdy&quot; angezeigt: &quot;h2&quot;.
