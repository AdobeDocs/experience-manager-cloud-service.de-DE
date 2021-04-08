---
title: Intelligente Bildbearbeitung
description: '"Erfahren Sie, wie bei der intelligenten Bildbearbeitung die individuellen Anzeigeeigenschaften der einzelnen Benutzer angewendet werden, um automatisch die richtigen Bilder bereitzustellen, die für ihr Erlebnis optimiert wurden, was zu einer besseren Leistung und Interaktion führt."'
feature: Asset-Verwaltung, Darstellungen
topic: Geschäftspraktiker
role: Business Practitioner
exl-id: 863784d9-0c91-4deb-8edd-1354a21581c3
translation-type: tm+mt
source-git-commit: 6b232ab512a6faaf075faa55c238dfb10c00b100
workflow-type: tm+mt
source-wordcount: '1924'
ht-degree: 46%

---

# Intelligente Bildbearbeitung {#smart-imaging}

## Was ist die intelligente Bildbearbeitung? {#what-is-smart-imaging}

Die Smart Imaging-Technologie nutzt Adobe Sensei AI-Funktionen und arbeitet mit vorhandenen &quot;Bildvorgaben&quot;. Es verbessert die Leistung von Image Versand durch die automatische Optimierung von Bildformat, -größe und -qualität je nach Browserfunktionen des Clients.

>[!NOTE]
>
>Für diese Funktion ist es erforderlich, dass Sie das vordefinierte CDN (Content Versand Network) verwenden, das zum Lieferumfang von Adobe Experience Manager Dynamic Media gehört. Andere benutzerdefinierte CDN werden von dieser Funktion nicht unterstützt.

Smart Imaging profitiert auch von der zusätzlichen Leistungssteigerung durch die vollständige Integration mit dem erstklassigen CDN-Dienst (Content Versand Network) der Adobe. Dieser Dienst findet die optimale Internetverbindung zwischen Servern, Netzwerken und Peering Points. Es findet eine Route mit der niedrigsten Latenz und der niedrigsten Paketverlustrate statt der Standardroute im Internet.

Die folgenden Beispiele für Bild-Assets veranschaulichen die Optimierungen durch die intelligente Bildbearbeitung:

| Bild<br>(URL) | Miniaturansicht | Größe<br> (JPEG) | Größe (WebP)<br> (mit intelligenter Bildbearbeitung) | Reduzierung in % |
|---|---|---|---|---|
| [Bild 1](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_6?hei=500&amp;fmt=jpg&amp;qlt=85&amp;resmode=bisharp&amp;op_usm=5,0.125,5,0) | ![picture1](/help/assets/assets-dm/picture1.png) | 73,75 KB | 45,92 KB | 38 % |
| [Bild 2](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_3?hei=500&amp;fmt=jpg&amp;qlt=85&amp;resmode=bisharp&amp;op_usm=5,0.125,5,0) | ![picture2](/help/assets/assets-dm/picture2.png) | 191 KB | 70,66 KB | 63 % |
| [Bild 3](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_2?hei=500&amp;fmt=jpg&amp;qlt=85&amp;resmode=bisharp&amp;op_usm=5,0.125,5,0) | ![picture3](/help/assets/assets-dm/picture3.png) | 96,64 KB | 39,44 KB | 59 % |
| [Bild 4](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_1?hei=500&amp;qlt=85&amp;resmode=bisharp&amp;op_usm=5,0.125,5,0) | ![picture4](/help/assets/assets-dm/picture4.png) | 315,80 KB | 178,19 KB | 44 % |
|  |  |  |  | Durchschnitt = 51 % |

Ähnlich wie oben führte Adobe auch einen Test mit 7009 URLs von Live-Kunden-Sites durch. Sie konnten im Durchschnitt 38 % mehr Dateigrößenoptimierung für JPEG erzielen. Für PNG mit WebP-Format konnten sie eine weitere Optimierung der Dateigröße um durchschnittlich 31 % erzielen. Diese Optimierung ist möglich, weil Smart Imaging in der Lage ist.

## Was sind die Hauptvorteile der intelligenten Bildbearbeitung? {#what-are-the-key-benefits-of-smart-imaging}

Bilder stellen den Großteil der Ladezeit einer Seite dar. Daher kann jede Leistungsverbesserung tief greifende Auswirkungen auf höhere Konversionsraten, die Besuchszeit auf einer Site und niedrigere Absprungraten auf der Site haben.

Verbesserungen der neuesten Version der intelligenten Bildbearbeitung:

* Verbessertes Google SEO Ranking für Webseiten mit der neuesten Smart Imaging.
* Dient zum sofortigen Bereitstellen optimierter Inhalte (zur Laufzeit).
* Verwendet Adobe Sensei-Technologie, um die Konvertierung entsprechend der in der Bildanforderung angegebenen Qualität (`qlt`) durchzuführen.
* Smart Imaging kann mit dem URL-Parameter `bfc` deaktiviert werden.
* TTL (Time To Live)-unabhängig. Zuvor war eine TTL von mindestens 12 Stunden erforderlich, damit die intelligente Bildbearbeitung funktioniert.
* Zuvor wurden sowohl die Original- als auch die abgeleiteten Bilder zwischengespeichert, und es war ein zweistufiger Prozess, um den Cache zu ungültigen. Bei der neuesten Smart Imaging-Version werden nur die Derivate zwischengespeichert, was eine einmalige Cache-Ungültigmachung ermöglicht.
* Kunden, die benutzerdefinierte Header in ihrem Regelsatz verwenden, profitieren von der neuesten Smart Imaging-Version, da diese Header nicht blockiert werden, anders als die vorherige Version von Smart Imaging. Beispiel: &quot;Zeitliche Herkunft zulassen&quot;, &quot;X-Roboter&quot;, wie unter [Hinzufügen eines benutzerdefinierten Header-Werts zu Bildantworten|Dynamic Media Classic](https://helpx.adobe.com/de/experience-manager/scene7/kb/base/scene7-rulesets/add-custom-header-val-image.html) empfohlen.

## Ist intelligente Bildbearbeitung mit irgendwelchen Lizenzierungskosten verbunden? {#are-there-any-licensing-costs-associated-with-smart-imaging}

Nein. Smart Imaging ist im Lieferumfang Ihrer Lizenz enthalten. Diese Regel gilt für Dynamic Media Classic oder Experience Manager Dynamic Media (On-Prem, AMS und Experience Manager als Cloud Service).

>[!NOTE]
>
>Smart Imaging ist für Dynamic Media - Hybrid-Kunden nicht verfügbar.

## Wie funktioniert die intelligente Bildbearbeitung? {#how-does-smart-imaging-work}

Wenn ein Bild von einem Kunden angefordert wird, prüft Smart Imaging die Benutzereigenschaften und konvertiert es je nach verwendetem Browser in das entsprechende Bildformat. Diese Formatkonvertierungen werden so durchgeführt, dass die visuelle Wiedergabetreue nicht beeinträchtigt wird. Die intelligente Bildbearbeitung konvertiert Bilder basierend auf den Browser-Funktionen auf folgende Weise automatisch in verschiedene Formate.

<!--   * Safari 14.0 +
    * Safari 14 only with iOS 14.0 and above and macOS BigSur and above -->

* Automatische Konvertierung in WebP für die folgenden Browser:
   * Chrome
   * Firefox
   * Microsoft® Edge
   * Safari (unter iOS, macOS, iPadOS), bereitgestellte Browser- und Betriebssystemversion-Unterstützung für WebP
   * Android™
   * Opera
* Unterstützung älterer Browser:

   | Browser | Browser/OS-Version | Format |
   | --- | --- | --- |
   | Safari | Früher als iOS/iPad 14.0 oder macOS BigSur | JPEG2000 |
   | Edge | Früher als 18 | JPEGXR |
   | Internet Explorer | 9+ | JPEGXR |
* Bereitstellung des ursprünglich angeforderten Bildformats für Browser, die diese Formate nicht unterstützen.

Wenn die Originalbildgröße kleiner ist als die von der intelligente Bildbearbeitung erzeugte, wird das Originalbild bereitgestellt.

## Welche Bildformate werden unterstützt?  {#what-image-formats-are-supported}

Die folgenden Bildformate werden für die intelligente Bildbearbeitung unterstützt:

* JPEG
* PNG

<!-- For any other format mentioned in a URL, you should explicity turn off Smart Imaging.  Append modifier `bfc=off` to the URL for file formats other than JPEG and PNG. You can accomplish this by using either one of the following methods:

* Use a ruleset if the `fmt` modifier is mentioned in the URL. 
* Append in URL modifiers field of the presets concerned.

Adobe is working on a permanent fix that does not require you to append `bfc=off` for `fmt !=JPEG` or `fmt !=PNG`. This topic will be updated after the fix is delivered. -->

## Wie funktioniert Smart Imaging mit Ihren bereits verwendeten Bildvorgaben? {#how-does-smart-imaging-work-with-our-existing-image-presets-that-are-already-in-use}

Smart Imaging funktioniert mit Ihren vorhandenen &quot;Bildvorgaben&quot;. Alle Bildeinstellungen werden mit Ausnahme der Qualität (`qlt`) und des Formats (`fmt`) beachtet, wenn das angeforderte Dateiformat JPEG oder PNG ist. Bei der Formatkonvertierung behält Smart Imaging die vollständige visuelle Genauigkeit bei, wie sie durch Ihre Bildvorgabeeinstellungen definiert wird, jedoch bei einer kleineren Dateigröße. Wenn die Originalbildgröße kleiner ist als die von der intelligente Bildbearbeitung erzeugte, wird das Originalbild bereitgestellt.

<!-- In addition, if your image presets are used to return `fmt !=JPEG` or `fmt !=PNG`, be sure append `bfc=off` in the preset modifier field to return the requested file format. -->

## Muss ich URLs, Bildvorgaben oder neuen Code für Smart Imaging auf meiner Site ändern? {#will-i-have-to-change-any-urls-image-presets-or-deploy-any-new-code-on-my-site-for-smart-imaging}

Intelligente Bildbearbeitung funktioniert nahtlos mit Ihren vorhandenen Bild-URLs und Bildvorgaben, wenn Sie die intelligente Bildbearbeitung für Ihre vorhandenen benutzerdefinierten Domain konfigurieren. Darüber hinaus müssen Sie bei der intelligenten Bildbearbeitung keinen Code auf Ihrer Website hinzufügen, um den Browser eines Benutzers zu erkennen. Es wird alles automatisch verarbeitet.

Wenn Sie eine neue benutzerdefinierte Domäne für die Verwendung von Smart Imaging konfigurieren müssen, müssen die URLs aktualisiert werden, um diese benutzerdefinierte Domäne widerzuspiegeln.

Informationen zu den Voraussetzungen für Smart Imaging finden Sie unter [Bin ich berechtigt, Smart Imaging zu verwenden?](#am-i-eligible-to-use-smart-imaging)

<!-- No. Smart Imaging works seamlessly with your existing image URLs and image presets. In addition, Smart Imaging does not require you to add any code on your website to detect a user's browser. All of this is handled automatically. -->

<!-- As mentioned earlier, Smart Imaging supports only JPEG and PNG image formats. For other formats, you need to append the `bfc=off` modifier to the URL as described earlier. -->

## Funktioniert die intelligente Bildbearbeitung mit HTTPS? Und mit HTTP/2?   {#does-smart-imaging-working-with-https-how-about-http}

Die intelligente Bildbearbeitung funktioniert bei Bildern, die über HTTP, HTTPS oder HTTP/2 bereitgestellt wurden.

## Bin ich zur Verwendung der intelligenten Bildbearbeitung berechtigt? {#am-i-eligible-to-use-smart-imaging}

Um Smart Imaging verwenden zu können, müssen die Dynamic Media Classic oder Dynamic Media Ihrer Firma auf dem Experience Manager-Konto die folgenden Anforderungen erfüllen:

* Sie verwenden das im Adobe-Bundle enthaltene CDN (Content Delivery Network) im Rahmen Ihrer Lizenz.
* Sie verwenden eine dedizierte Domain (z. B. `images.company.com` oder `mycompany.scene7.com`), keine generische Domain (z. B. `s7d1.scene7.com`, `s7d2.scene7.com` oder `s7d13.scene7.com`).

Um Ihre Domänen zu finden, öffnen Sie die [Dynamic Media Classic Desktop-Anwendung](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html?lang=de#getting-started) und melden Sie sich dann bei Ihrem Firmen-Konto oder Ihren Konten an.

Tippen Sie auf **[!UICONTROL Einstellungen > Anwendungseinstellungen > Allgemeine Einstellungen]**. Suchen Sie nach dem Feld **[!UICONTROL Veröffentlichungs-Server-Name]**. Wenn Sie derzeit eine allgemeine Domäne verwenden, können Sie den Übergang zu Ihrer eigenen benutzerdefinierten Domäne anfordern. Fordern Sie diese Transition an, wenn Sie ein Ticket für den technischen Support einreichen.

Für Ihre erste benutzerdefinierte Domain fallen mit einer Dynamic Media-Lizenz keine zusätzlichen Kosten an.

## Wie kann ich die intelligente Bildbearbeitung für mein Konto aktivieren? {#what-is-the-process-for-enabling-smart-imaging-for-my-account}

Sie initiieren die Anforderung, intelligente Bildbearbeitung zu verwenden. nicht automatisch aktiviert ist.

1. [Verwenden Sie die Admin Console, um einen Support-Fall zu erstellen](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).
1. Geben Sie in Ihrem Support-Fall die folgenden Informationen an:

   1. Name des Hauptansprechpartners, E-Mail, Telefon.
   1. Geben Sie alle Domains an, für die intelligente Bildbearbeitung aktiviert werden soll (also `images.company.com` oder `mycompany.scene7.com`).

      Um Ihre Domänen zu finden, öffnen Sie die [Dynamic Media Classic Desktop-Anwendung](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started) und melden Sie sich dann bei Ihrem Firmen-Konto oder Ihren Konten an.

      Klicken Sie auf **[!UICONTROL Einstellungen > Anwendungseinstellungen > Allgemeine Einstellungen]**.

      Suchen Sie nach dem Feld **[!UICONTROL Veröffentlichungs-Server-Name]**.
   1. Vergewissern Sie sich, dass Sie CDN über Adobe und nicht verwaltet mit einer direkten Beziehung nutzen.
   1. Vergewissern Sie sich, dass Sie eine dedizierte Domain wie `images.company.com` oder `mycompany.scene7.com` und nicht eine generische Domain wie `s7d1.scene7.com`, `s7d2.scene7.com` oder `s7d13.scene7.com` verwenden.

      Um Ihre Domänen zu finden, öffnen Sie die [Dynamic Media Classic Desktop-Anwendung](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started) und melden Sie sich dann bei Ihrem Firmen-Konto oder Ihren Konten an.

      Klicken Sie auf **[!UICONTROL Einstellungen > Anwendungseinstellungen > Allgemeine Einstellungen]**.

      Suchen Sie nach dem Feld **[!UICONTROL Veröffentlichungs-Server-Name]**. Wenn Sie derzeit eine generische Dynamic Media Classic-Domain verwenden, können Sie im Zuge dieser Umstellung einen Wechsel zu Ihrer eigenen benutzerdefinierten Domain beantragen.
   1. Geben Sie an, ob es über HTTP/2 funktionieren soll.

1. Der Kundendienst von Adobe fügt Sie basierend auf der Reihenfolge, in der Anfragen gesendet werden, zur Wartezeit-Liste von Smart Imaging-Kunden hinzu.
1. Wenn die Adobe bereit ist, Ihre Anfrage zu bearbeiten, kontaktiert der Kundendienst Sie, um das Datum der Zielgruppe zu koordinieren und festzulegen.
1. **Optional**: Sie können die intelligente Bildbearbeitung optional in Staging testen, bevor die Adobe die neue Funktion in die Produktion schiebt.
1. Sie werden nach Abschluss der Anfrage vom Kundendienst benachrichtigt.
1. Zur maximalen Leistungsverbesserung der intelligenten Bildbearbeitung empfiehlt Adobe eine Time-to-Live (TTL)-Einstellung von mindestens 24 Stunden. Die TTL-Einstellung definiert, wie lange Assets vom CDN-Dienst im Cache gespeichert werden. So ändern Sie diese Einstellung:

   1. Klicken Sie bei Verwendung von Dynamic Media Classic auf **[!UICONTROL Einstellungen > Anwendungseinstellungen > Veröffentlichungseinstellungen > Image-Server]**. Stellen Sie den Wert **[!UICONTROL Standardeinstellung für Time-To-Live des Client-Cache]** auf mindestens 24 ein.
   1. Wenn Sie Dynamic Media verwenden, befolgen Sie [diese Anweisungen](config-dm.md). Stellen Sie den Wert **[!UICONTROL Gültigkeit]** auf mindestens 24 Stunden ein.

## Wann wird mein Konto voraussichtlich für die intelligente Bildbearbeitung aktiviert? {#when-can-i-expect-my-account-to-be-enabled-with-smart-imaging}

Anfragen werden in der Reihenfolge verarbeitet, in der sie vom Kundendienst empfangen werden, gemäß der Liste Warten.

>[!NOTE]
>
>Es kann eine lange Vorlaufzeit geben, da die Aktivierung von Smart Imaging eine Adobe beinhaltet, die den Cache löscht. Daher kann nur jeweils eine geringe Anzahl von Kunden gleichzeitig umgestellt werden.

## Welche Risiken bestehen bei der Umstellung auf die intelligente Bildbearbeitung? {#what-are-the-risks-with-switching-over-to-use-smart-imaging}

Es besteht kein Risiko für eine Kunden-Web-Seite. Die Transition zu Smart Imaging löscht jedoch Ihren CDN-Cache. Dieser Vorgang umfasst die Umstellung auf eine neue Konfiguration von Dynamic Media Classic oder Dynamic Media auf dem Experience Manager.

Während der ersten Transition treffen die nicht zwischengespeicherten Bilder direkt auf die Adoben-Server, bis der Cache erneut aufgebaut wird. Daher plant Adobe, mehrere Kundenanforderungen gleichzeitig zu bearbeiten, damit beim Abrufen von Anforderungen aus der Herkunft eine annehmbare Transition erhalten bleibt. Für die meisten Kunden wird der Cache innerhalb von etwa 1-2 Tagen erneut im CDN aufgebaut.

## Wie kann ich feststellen, ob die intelligente Bildbearbeitung erwartungsgemäß funktioniert? {#how-can-i-verify-whether-smart-imaging-is-working-as-expected}

1. Laden Sie nach der Konfiguration Ihres Kontos mit Smart Imaging eine Dynamic Media Classic- oder Adobe Experience Manager - Dynamic Media-Bild-URL in den Browser.
1. Öffnen Sie den Chrome-Entwicklerbereich, indem Sie im Browser auf **[!UICONTROL Anzeigen > Entwickler > Entwickler-Tools]** klicken. Selbstverständlich können Sie auch ein anderes Browser-Entwickler-Tool Ihrer Wahl verwenden.

1. Stellen Sie sicher, dass der Cache deaktiviert ist, wenn Entwicklerwerkzeuge geöffnet sind.

   * Navigieren Sie unter Windows® zu den Einstellungen im Tool-Bereich für Entwickler und aktivieren Sie dann das Kontrollkästchen **[!UICONTROL Cache deaktivieren (während devtools geöffnet ist)]**.
   * Wählen Sie unter macOS im Entwicklerbereich unter der Registerkarte **[!UICONTROL Netzwerk]** **[!UICONTROL Cache deaktivieren]**.

1. Sie werden feststellen, dass der Content-Typ in das entsprechende Format umgewandelt wird. Der folgende Screenshot zeigt ein PNG-Bild, das in Chrome dynamisch ins WebP-Format konvertiert wird.
1. Wiederholen Sie diesen Test auf verschiedenen Browsern und bei unterschiedlichen Benutzerbedingungen.

>[!NOTE]
>
>Nicht alle Bilder werden konvertiert. Smart Imaging entscheidet, ob die Konvertierung die Leistung verbessern kann. In Fällen, in denen keine Leistungssteigerung erwartet wird oder das Format nicht JPEG oder PNG ist, wird das Bild nicht konvertiert.

![image2017-11-14_15398](assets/image2017-11-14_15398.png)

## Kann die intelligente Bildbearbeitung für eine beliebige Anfrage deaktiviert werden?{#turning-off-smart-imaging}

Ja. Sie können die intelligente Bildbearbeitung deaktivieren, indem Sie den Modifikator `bfc=off` zur URL hinzufügen.

## Welche „Optimierungen“ sind verfügbar? Gibt es Einstellungen oder Verhaltensweisen, die definiert werden können? (#tuning-settings)

Derzeit können Sie die intelligente Bildbearbeitung optional aktivieren oder deaktivieren. Es stehen keine weiteren Optimierungen zur Verfügung.

## Wenn Smart Imaging die Qualitätseinstellungen verwaltet, kann ich dann die Mindestwerte und Höchstwerte festlegen? Ist es zum Beispiel möglich, eine Qualität „nicht kleiner als 60“ und „nicht größer als 80“ festzulegen? (#minimum-maximum)

Diese Funktionalität gibt es in der aktuellen intelligenten Bildbearbeitung nicht.

## Manchmal wird ein JPEG-Bild anstelle eines WebP-Bildes an Chrome zurückgegeben. Warum geschieht das? (#jpeg-webp)

Die intelligente Bildbearbeitung entscheidet, ob die Konvertierung vorteilhaft ist. Das neue Bild wird nur dann zurückgegeben, wenn die Konvertierung zu einer kleineren Dateigröße mit vergleichbarer Qualität führt.
