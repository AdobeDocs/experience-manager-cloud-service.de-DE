---
title: Bereitstellung von Inhalten per HTTP/2 – Häufig gestellte Fragen (FAQ)
description: Erfahren Sie mehr über die Bereitstellung von Inhalten per HTTP/2.
role: Administrator,Business Practitioner
exl-id: 0a8a5fd8-a341-4e7f-84a5-409e2de97efe
source-git-commit: 1ad89be4ebddec0705c6f557fed3d697b9f1f3a7
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 69%

---

# Bereitstellung von Inhalten per HTTP/2 – Häufig gestellte Fragen (FAQ) {#http-delivery-of-content-faq}

Adobe freut sich, die Verfügbarkeit der HTTP/2-Bereitstellung von Inhalten bekannt zu geben. Bei Verwendung von HTTP/2 wird die Gesamtleistung gesteigert.

>[!NOTE]
>
>Für diese Funktion müssen Sie das native Inhaltsbereitstellungsnetzwerk verwenden, das zum Lieferumfang von Adobe Experience Manager - Dynamic Media gehört. Mit dieser Funktion wird kein anderes benutzerdefiniertes Netzwerk zur Inhaltsbereitstellung unterstützt.

## Was ist HTTP/2? {#what-is-http}

HTTP/2 verbessert die Kommunikation zwischen Browsern und Servern, ermöglicht eine schnellere Übertragung von Informationen und verringert den Verarbeitungsaufwand.

Der Website-Artikel [Was Sie über HTTP/2](https://www.engadget.com/2015-02-24-what-you-need-to-know-about-http-2.html) wissen müssen, beschreibt HTTP/2 und seine Vorteile kurz und einfach.

## Was sind die wichtigsten Vorteile der Umstellung auf die Bereitstellung von Inhalt über HTTP/2? {#what-are-the-key-benefits-of-moving-to-http-for-content-delivery}

Die Leistungsverbesserung unterscheidet sich stark, da sie auf verschiedenen Faktoren basiert. Beispielsweise der Code Ihrer Website, die Verwendung von Dynamic Media, das Gerät, den Bildschirm und den Standort des Verbrauchers.

Von Adobe durchgeführte Prüfungen führten zu folgenden Ergebnissen:

* Bei Bildern wurde die Reaktionszeit je nach Gerät und Browser um 7–28 % verbessert. Die bedeutendste Leistungssteigerung war bei iOS-Geräten zu beobachten.
* Die Ladezeitleistung für Viewer wurde um 15 % verbessert.

Die folgende Demonstration zeigt den Unterschied zwischen Laden mit HTTP/1 und Laden mit HTTP/2:

[https://http2.akamai.com/demo](https://http2.akamai.com/demo)

## Bin ich berechtigt, auf HTTP/2 umzustellen?  {#am-i-eligible-to-switch-over-to-http}

Um HTTP/2 verwenden zu können, müssen Sie die folgenden Voraussetzungen erfüllen:

* Sie verwenden sicheres HTTPS für Ihre Rich Media-Anforderungen.
* Verwenden Sie das im Adobe-Bundle enthaltene CDN (Content Delivery Network) als Teil Ihrer Dynamic Media Classic-Lizenz.
* Verwenden Sie eine dedizierte Domain (d. h. `images.company.com` oder `mycompany.scene7.com`), keine generische Dynamic Media-Domain (d. h. `s7d1.scene7.com`, `s7d2.scene7.com` oder `s7d13.scene7.com`).

   Öffnen Sie das [Dynamic Media Classic-Desktop-Programm](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html?lang=de#getting-started) und melden Sie sich bei Ihrem Konto an, um Ihre Domains zu finden.

   Klicken Sie auf **[!UICONTROL Einstellungen > Anwendungseinstellungen > Allgemeine Einstellungen]**. Suchen Sie nach dem Feld **Veröffentlichungs-Server-Name**. Wenn Sie derzeit eine generische Dynamic Media-Domain verwenden, können Sie im Zuge dieser Umstellung einen Wechsel zu Ihrer eigenen benutzerdefinierten Domain beantragen.

## Wie verläuft der Prozess für die Aktivierung von HTTP/2 für mein Dynamic Media-Konto? {#what-is-the-process-for-enabling-http-for-my-dm-account}

[Verwenden Sie die Admin Console, um einen Support-](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) Fall zu erstellen und den Wechsel zu HTTP/2 anzufordern. wird nicht automatisch für Sie durchgeführt.

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
   1. Wenn Adobe zur Bearbeitung Ihrer Anfrage bereit ist, kontaktiert Sie die Kundenunterstützung, um die Umstellung zu koordinieren und ein Zieldatum festzulegen.
   1. Nach Abschluss werden Sie benachrichtigt, wonach Sie prüfen können, ob die Umstellung auf HTTP/2 erfolgreich durchgeführt wurde.



## Wann kann ich mit der Umstellung auf HTTP/2 rechnen? {#when-can-i-expect-to-be-transitioned-over-to-http}

Anfragen werden in der Reihenfolge verarbeitet, in der sie beim technischen Support eingehen.

>[!NOTE]
>
>Es gibt eine lange Vorlaufzeit, da der Übergang zu HTTP/2 das Löschen des Caches beinhaltet. Es können daher nur wenige Umstellungen zugleich durchgeführt werden.

## Welche Risiken sind mit der Umstellung auf HTTP/2 verbunden?   {#what-are-the-risks-with-moving-to-http}

Durch die Umstellung auf HTTP/2 wird Ihr Cache im CDN gelöscht, da eine neue CDN-Konfiguration erforderlich ist.

Der nicht zwischengespeicherte Inhalt wird direkt an die ursprünglichen Server von Adobe übertragen, bis der Cache neu aufgebaut wird. Aufgrund dieser Aktion plant Adobe, einige Kundenübergänge gleichzeitig zu handhaben. Diese Methode stellt sicher, dass beim Abrufen von Anforderungen aus der Quelle eine akzeptable Leistung erzielt wird.

## Wie kann festgestellt werden, ob eine URL oder eine Website mit HTTP/2 aktiviert wurde?   {#how-can-you-verify-whether-a-url-or-website-is-activated-with-http}

Laden Sie eine Erweiterung herunter, die mit Ihrem Webbrowser verwendet werden soll. Für Firefox und Chrome gibt es eine Erweiterung namens **[!UICONTROL HTTP/2 und SPDY Indicator]**. Da Browser HTTP/2 nur bei sicheren Verbindungen unterstützen, muss für die Verifizierung eine URL mit HTTPS aufgerufen werden. Wenn HTTP/2 unterstützt wird, wird dies durch die Erweiterung in Form eines blauen Flash-Symbols und der Kopfzeile &quot;X-Firefox-Spdy&quot;angezeigt: &quot;h2&quot;.
