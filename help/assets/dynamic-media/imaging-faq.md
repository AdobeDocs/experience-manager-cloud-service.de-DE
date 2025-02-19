---
title: Intelligente Bildbearbeitung
description: 'Erfahren Sie, wie die intelligente Bildbearbeitung mithilfe von Adobe Sensei-KI die individuellen anzeigebezogenen Anwendermerkmale anwendet, um automatisch die richtigen Bilder für ein optimiertes individuelles Erlebnis zu präsentieren. Das Ergebnis: mehr Leistung und Interaktion.'
contentOwner: Rick Brough
feature: Asset Management,Renditions,Best Practices
role: User
mini-toc-levels: 2
exl-id: 863784d9-0c91-4deb-8edd-1354a21581c3
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: ht
source-wordcount: '3243'
ht-degree: 100%

---

# Intelligente Bildbearbeitung {#smart-imaging}

Erfahren Sie, wie die intelligente Bildbearbeitung mithilfe von Adobe Sensei-KI die individuellen anzeigebezogenen Anwendermerkmale anwendet, um automatisch die richtigen Bilder für ein optimiertes individuelles Erlebnis zu präsentieren. Das Ergebnis: mehr Leistung und Interaktion.


## Über die intelligente Bildbearbeitung {#about-smart-imaging}

Die intelligente Bildbearbeitung wendet KI-Funktionen von Adobe Sensei an und arbeitet mit vorhandenen „Bildvorgaben“. Sie optimiert auf Grundlage der Browserfunktionen automatisch das Format, die Größe und die Qualität eines Bildes und stellt so hochwertige Bilder bereit.

Jetzt erhalten Sie auch eine bessere Google Core Web Vital-Bewertung für LCP (Largest Contentful Paint) mit verbesserter intelligenter Bildbearbeitung, die jetzt sowohl AVIF- als auch WebP-Unterstützung bietet.

>[!IMPORTANT]
>
>Für die intelligente Bildbearbeitung müssen Sie das im Lieferumfang von Adobe Experience Manager Dynamic Media enthaltene vorkonfigurierte CDN (Content Delivery Network) verwenden. Andere benutzerdefinierte CDN werden von dieser Funktion nicht unterstützt.

>[!TIP]
>
>Probieren Sie die Vorteile von Dynamic Media-Bildmodifikatoren und der intelligenten Bildbearbeitung mithilfe von Dynamic Media [_Momentaufnahme_ aus](https://snapshot.scene7.com/).
>
>„Momentaufnahme“ ist ein visuelles Demonstrationswerkzeug, das die Leistungsfähigkeit von Dynamic Media für eine optimierte und dynamische Bildbereitstellung veranschaulicht. Experimentieren Sie mit Testbildern oder Dynamic Media-URLs, um die Ausgabe verschiedener Dynamic Media-Bildmodifikatoren visuell zu beobachten, und optimieren Sie die intelligente Bildbearbeitung auf Folgendes:
>
>* Dateigröße (mit WebP- und AVIF-Bereitstellung)
>* Netzwerkbandbreite
>* DPR (Gerätepixelverhältnis)
>
>Um zu erfahren, wie einfach es ist, „Momentaufnahme“ zu verwenden, spielen Sie das Video [Schulungsvideo zu Momentaufnahmen](https://experienceleague.adobe.com/de/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-snapshot) (3 Minuten und 17 Sekunden) ab.

Die intelligente Bildbearbeitung profitiert auch von der zusätzlichen Leistungssteigerung durch die vollständige Integration mit dem erstklassigen Premium-CDN-Dienst (Content Delivery Network) von Adobe. Dieser Service ermittelt die optimale Internetroute zwischen Servern, Netzwerken und Austauschpunkten. Er findet die Route mit der niedrigsten Latenz und der niedrigsten Paketverlustrate, anstatt die Standardroute im Internet zu verwenden.

Die folgenden Beispiele für Bild-Assets veranschaulichen die Optimierungen durch die intelligente Bildbearbeitung:

| Bild (URL) | Miniaturansicht | Größe (JPEG) | Größe (WebP) mit intelligenter Bildbearbeitung | Größe (AVIF) mit intelligenter Bildbearbeitung | Reduktion in % mit WebP | Reduktion in % mit AVIF |
|---|---|---|---|---|---|---|
| [Bild 1](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_6?hei=500&amp;fmt=jpg&amp;qlt=85&amp;resmode=bisharp&amp;op_usm=5,0.125,5,0) | ![picture1](/help/assets/assets-dm/picture1.png) | 145 KB | 106 KB | 90,2 KB | 26,89 % | 37,79 % |
| [Bild 2](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_3?hei=500&amp;fmt=jpg&amp;qlt=85&amp;resmode=bisharp&amp;op_usm=5,0.125,5,0) | ![picture2](/help/assets/assets-dm/picture2.png) | 412 KB | 346 KB | 113 KB | 16,01 % | 72,57 % |
| [Bild 3](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_2?hei=500&amp;fmt=jpg&amp;qlt=85&amp;resmode=bisharp&amp;op_usm=5,0.125,5,0) | ![picture3](/help/assets/assets-dm/picture3.png) | 221 KB | 189 KB | 87,1 KB | 14,47 % | 60,58 % |
| [Bild 4](https://techsupport.scene7.com/is/image/TechSupport/SmartImaging_1?hei=500&amp;qlt=85&amp;resmode=bisharp&amp;op_usm=5,0.125,5,0) | ![picture4](/help/assets/assets-dm/picture4.png) | 594 KB | 545 KB | 286 KB | 8,25 % | 51,85 % |

Ähnlich wie oben führte Adobe auch einen Test mit einem größeren Stichprobensatz durch. Das Format AVIF bot eine zusätzliche Größenreduzierung von 20 % gegenüber WebP, das eine Reduzierung von 27 % gegenüber JPEG ermöglichte. Alles bei der gleichen visuellen Qualität. Insgesamt ermöglicht AVIF im Vergleich zu JPEG eine Reduzierung der durchschnittlichen Größe um bis zu 41 %.

Im Vergleich mit PNG können Sie eine Reduzierung der Größe um 84 % mit WebP und 87 % mit AVIF feststellen. Da sowohl WebP als auch AVIF Transparenz und mehrere Bildanimationen unterstützen, ist dies ein guter Ersatz für transparente PNG- und GIF-Dateien.

Siehe auch [Bildoptimierung mit Bildformaten der nächsten Generation (WebP und AVIF)](https://blog.developer.adobe.com/image-optimisation-with-next-gen-image-formats-webp-and-avif-248c75afacc4)

<!-- HIDDEN ON MAY 19, 2022 BASED ON CQDOC-19280 On the mobile web, the challenges are compounded by two factors:

* Large variety of devices with different form factors and high-resolution displays.
* Constrained network bandwidth.

In terms of images, the goal is to serve the best quality images as efficiently as possible. -->

**Vorteile der intelligenten Bildbearbeitung**

Die intelligente Bildbearbeitung sorgt für eine bessere Bildübertragung, indem sie die Größe der Dateien automatisch auf der Grundlage des Benutzer-Browsers, der Geräteanzeige und der Netzwerkbedingungen optimiert. Dieser Ansatz ermöglicht kürzere Ladezeiten und ein besseres Anwendererlebnis in verschiedenen Umgebungen. Da Bilder einen Großteil der Seitenladezeit ausmachen, kann die Leistungssteigerung einen enormen Einfluss auf geschäftsbezogene KPIs wie die folgenden haben:

* Höhere Konversionsraten.
* Auf der Site verbrachte Zeit.
* Niedrigere Absprungraten einer Site.

Die Hauptvorteile der neuen intelligenten Bildbearbeitung sind:

* Sie unterstützt das Bildformat der nächsten Generation, AVIF.
* Verlustbehaftete Konvertierungen von PNG zu WebP und AVIF werden jetzt unterstützt. Da PNG ein verlustfreies Format ist, waren frühere Bereitstellungen von WebP und AVIF verlustfrei.
* [Browser-Formatkonvertierung](#bfc)
* [Gerätepixelverhältnis](#dpr)
* [Netzwerkbandbreite](#bandwidth)

### Über die Browser-Formatkonvertierung {#bfc}

Durch Aktivieren der Browser-Formatkonvertierung durch Anhängen von `bfc=on` an die Bild-URL werden JPEG und PNG für verschiedene Browser automatisch in verlustbehaftetes AVIF, WebP, JPEGXR oder JPEG2000 konvertiert. Bei Browsern, die diese Formate nicht unterstützen, stellt die intelligente Bildbearbeitung weiterhin JPEG oder PNG bereit. Bei der intelligenten Bildbearbeitung wird die Qualität des neuen Formats zusammen mit der Formatänderung neu berechnet.

Sie können die intelligente Bildbearbeitung deaktivieren, indem Sie `bfc=off` an die Bild-URL anhängen.

Siehe auch [bfc](https://experienceleague.adobe.com/de/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-bfc) in der Bildbereitstellungs- und Rendering-API von Dynamic Media.

### Informationen zur Optimierung des Gerätepixelverhältnisses {#dpr}

Das Gerätepixelverhältnis (Device Pixel Ratio, DPR), auch als CSS-Pixelverhältnis bezeichnet, ist das Verhältnis zwischen den physischen und den logischen Pixeln eines Geräts. Mit dem Aufkommen von Retina-Anzeigen nimmt die Pixelauflösung moderner Mobilgeräte schnell zu.

Durch Aktivieren der Optimierung des Gerätepixelverhältnisses wird das Bild in der nativen Bildschirmauflösung gerendert, sodass es gestochen scharf erscheint.

Derzeit stammt die Display-Pixeldichte aus den CDN-Kopfzeilenwerten von Akamai.

| Zulässige Werte in der URL eines Bildes | Beschreibung |
|---|---|
| `dpr=off` | Deaktivieren Sie die DPR-Optimierung auf Ebene der einzelnen Bild-URLs. |
| `dpr=on,dprValue` | Überschreiben Sie den von der intelligenten Bildbearbeitung erkannten DPR-Wert mit einem benutzerdefinierten Wert (wie von einer beliebigen Client-seitigen Logik oder auf andere Weise erkannt). Der zulässige Wert für `dprValue` ist eine beliebige Zahl, die größer ist als 0. |

>[!NOTE]
>
>* Sie können `dpr=on,dprValue` auch dann verwenden, wenn die DPR-Einstellung auf Unternehmensebene deaktiviert ist.
>* Aufgrund der DPR-Optimierung wird die MaxPix-Breite immer erkannt, wenn das resultierende Bild größer ist als die Dynamic Media-Einstellung für MaxPix, indem das Seitenverhältnis des Bilds beibehalten wird. -->

| Angefragte Bildgröße | Wert für Gerätepixelverhältnis (Device Pixel Ratio, DPR) | Bereitgestellte Bildgröße |
|---|---|---|
| 816 x 500 | 1 | 816 x 500 |
| 816 x 500 | 2 | 1632 x 1000 |

Siehe auch [Arbeiten mit Bildern](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md#when-working-with-images) und [Bei der Arbeit mit smartem Zuschneiden](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md#when-working-with-smart-crop).

### Über die Optimierung der Netzwerkbandbreite {#bandwidth}

Beim Aktivieren der Netzwerkbandbreite wird die Bildqualität automatisch an die tatsächliche Netzwerkbandbreite angepasst. Bei geringer Netzwerkbandbreite wird die Optimierung des Gerätepixelverhältnisses (Device Pixel Ratio, DPR) automatisch deaktiviert, auch wenn sie bereits aktiviert ist.

Ihr Unternehmen kann die Optimierung der Netzwerkbandbreite für einzelne Bilder deaktivieren, indem `network=off` an die Bild-URL angehängt wird.

| Zulässiger Wert in der URL eines Bilds | Beschreibung |
|---|---|
| `network=off` | Deaktiviert die Netzwerkoptimierung auf Ebene der einzelnen Bild-URLs. |

Die Werte für das Gerätepixelverhältnis und die Netzwerkbandbreite basieren auf den erkannten Client-seitigen Werten des im Bundle enthaltene CDN. Diese Werte sind mitunter ungenau. Beispielsweise wird für iPhone 5 mit DPR = 2 und iPhone 12 mit `dpr=3` jeweils `dpr=2` angezeigt. Bei Geräten mit hoher Auflösung ist es jedoch besser, `dpr=2` zu senden als `dpr=1`. Die beste Möglichkeit, diese Ungenauigkeit zu überwinden, besteht jedoch darin, das Client-seitige Gerätepixelverhältnis zu verwenden. Nur dann sind die Werte 100 % genau. Und es funktioniert für jedes Gerät, ob Apple oder ein anderes Gerät, das gestartet wurde. Siehe [Verwenden der intelligenten Bildbearbeitung mit dem Client-seitigen Gerätepixelverhältnis (Device Pixel Ratio)](/help/assets/dynamic-media/client-side-dpr.md).

**Weitere wichtige Vorteile der intelligenten Bildbearbeitung**

* Das Google SEO-Ranking für Web-Seiten mit der neuesten intelligenten Bildbearbeitung wurde verbessert.
* Stellt optimierte Inhalte sofort (zur Laufzeit) bereit.
* Verwendet Adobe Sensei-Technologie zur Konvertierung gemäß der in der Bildanfrage angegebenen Qualität (`qlt`).
* TTL (Time To Live)-unabhängig. Zuvor war eine TTL von mindestens 12 Stunden erforderlich, damit die intelligente Bildbearbeitung funktioniert.
* Zuvor wurden sowohl das Originalbild als auch abgeleitete Bilder zwischengespeichert. Ein zweistufiger Prozess war erforderlich, um den Cache ungültig zu machen. In der neusten Version der intelligenten Bildbearbeitung werden nur die Ableitungen zwischengespeichert, was einen einstufigen Cache-Invalidierungsprozess ermöglicht.
* Kundinnen und Kunden, die benutzerdefinierte Kopfzeilen in ihrem Regelsatz verwenden, profitieren von der neuesten intelligenten Bildbearbeitung, da diese Kopfzeilen im Gegensatz zur vorherigen Version der intelligenten Bildbearbeitung nicht blockiert werden. Beispielsweise profitieren „Timing Allow Origin“ oder „X-Robot“, wie unter [Hinzufügen einer benutzerdefinierten Kopfzeile zu Bildantworten | Dynamic Media Classic](https://helpx.adobe.com/de/experience-manager/scene7/kb/base/scene7-rulesets/add-custom-header-val-image.html) vorgeschlagen, von der neuesten Version der intelligenten Bildbearbeitung.

## Funktionsweise der intelligenten Bildbearbeitung{#how-smart-imaging-works}

Wenn eine Verbraucherin oder ein Verbraucher ein Bild anfragt, analysiert die intelligente Bildbearbeitung die Benutzermerkmale und führt basierend auf dem Browser eine Konvertierung in das passende Bildformat durch. Diese Formatkonvertierungen werden so durchgeführt, dass die visuelle Wiedergabetreue nicht beeinträchtigt wird. Die intelligente Bildbearbeitung konvertiert Bilder basierend auf den Browser-Funktionen auf folgende Weise automatisch in verschiedene Formate.

* Automatische Konvertierung in AVIF, wenn der Browser das Format unterstützt
* Automatische Konvertierung in WebP, wenn die AVIF-Konvertierung nicht vorteilhaft war oder der Browser AVIF nicht unterstützt
* Automatische Konvertierung in JPEG2000, wenn Safari WebP nicht unterstützt
* Automatische Konvertierung in JPEGXR für IE9+ oder wenn Edge WebP nicht unterstützt

  | Bildformat | Unterstützte Browser |
  |---|---|
  | AVIF | [https://caniuse.com/avif](https://caniuse.com/avif) |
  | WebP | [https://caniuse.com/webp](https://caniuse.com/webp) |
  | JPEG 2000 | [https://caniuse.com/jpeg2000](https://caniuse.com/jpeg2000) |
  | JPEGXR | [https://caniuse.com/jpegxr](https://caniuse.com/jpegxr) |

* Bereitstellung des ursprünglich angeforderten Bildformats für Browser, die diese Formate nicht unterstützen.

Wenn die Originalbildgröße kleiner ist als die von der intelligente Bildbearbeitung erzeugte, wird das Originalbild bereitgestellt.

## Unterstützung von Bildformaten in der intelligenten Bildbearbeitung{#image-format-support}

Die folgenden Bildformate werden für die intelligente Bildbearbeitung unterstützt:

* JPEG
* PNG

Die intelligente Bildbearbeitung berechnet die Qualität der JPEG-Bilddatei bei der Konvertierung in ein neues Format neu.

Für Bilddateiformate, die Transparenz unterstützen, wie PNG, können Sie die intelligente Bildbearbeitung so konfigurieren, dass verlustbehaftete AVIF- und WebP-Dateien bereitgestellt werden. Für die verlustreiche Formatkonvertierung verwendet die intelligente Bildbearbeitung die in der URL des Bildes erwähnte Qualität oder ansonsten die im Dynamic Media-Unternehmenskonto konfigurierte Qualität.

## Unterstützung für Bildbereitstellungs-Befehle in der intelligenten Bildbearbeitung{#imaging-serving-command-support}

Die Bildbereitstellungs-Befehle `fmt` und `qlt` werden nicht unterstützt; alle anderen Befehle werden unterstützt.

## Häufig gestellte Fragen zur intelligenten Bildbearbeitung{#smart-imaging-faq}

+++**Ist die intelligente Bildbearbeitung mit Lizenzkosten verbunden?**

Nein. Sie sind berechtigt, die intelligente Bildbearbeitung mit Ihrer Lizenz zu nutzen. Dies gilt für Dynamic Media Classic oder Experience Manager Dynamic Media (On-Premise, AMS und Experience Manager as a Cloud Service).

>[!IMPORTANT]
>
>Die intelligente Bildbearbeitung ist nicht für Dynamic Media-Hybrid-Kunden verfügbar.

+++

+++**Kann die intelligente Bildbearbeitung für eine beliebige Anfrage deaktiviert werden?**

Ja. Sie können die intelligente Bildbearbeitung deaktivieren, indem Sie einen der folgenden Modifikatoren hinzufügen:

* `bfc=off`, um die Browser-Formatkonvertierung zu deaktivieren. Siehe auch [Browser-Formatkonvertierung](#bfc).
* `dpr=off`, um das Gerätepixelverhältnis zu deaktivieren. Siehe auch [Gerätepixelverhältnis](#dpr).
* `network=off`, um die Netzwerkbandbreite zu deaktivieren. Siehe auch [Netzwerkbandbreite](#network).

+++

+++**Ist es möglich, die intelligente Bildbearbeitung zu „optimieren“?**

Ja. Die intelligente Bildbearbeitung bietet drei Optionen, die Sie aktivieren oder deaktivieren können.

* [Browser-Formatkonvertierung](#bfc)
* [Gerätepixelverhältnis](#dpr)
* [Netzwerkbandbreite](#network)

+++

+++**Funktioniert die intelligente Bildbearbeitung mit meinen vorhandenen Bildvorgaben?**

Die intelligente Bildbearbeitung ist nahtlos mit vorhandenen Bildvorgaben integriert und respektiert alle Bildeinstellungen.

Die einzigen Anpassungen betreffen das Bildformat, die Qualität oder beides. Bei der Formatkonvertierung bleibt die Wiedergabetreue gemäß den von Ihnen gewählten Vorgabeeinstellungen vollständig erhalten – jedoch bei kleinerer Dateigröße. Aktivieren Sie dies einfach, indem Sie `bfc=on`, `dpr=on,dprValue` oder `network=on` oder alle drei Parametereinstellungen zu Ihren vorhandenen URLs oder Vorgaben hinzufügen.

Angenommen, eine Bildvorgabe gibt ein JPEG-Format von 500 × 500 Pixel mit „`quality=85`“ und „`unsharp mask=0.1,1,5`“ vor. Die intelligente Bildbearbeitung erkennt, ob ein Chrome-Browser verwendet wird. Anschließend wird das Bild in WebP mit denselben Abmessungen (500 × 500) und einer Unschärfemaske, die den Einstellungen der JPEG entspricht, konvertiert. Anschließend vergleicht das System die Dateigröße der WebP- und JPEG-Version und stellt der Benutzerin bzw. dem Benutzer die kleinere Version bereit.

+++

<!-- OLD VERSION BELOW AS PER CQDOC-22085>
Yes. Smart Imaging works with your existing image presets and observes all your image settings. What changes is the image format, or the quality setting, or both. For format conversion, Smart Imaging maintains full visual fidelity as defined by your image preset settings, but at a smaller file size.

For example, suppose that an image preset is defined with JPEG format, size 500 x 500, quality=85, and unsharp mask=0.1,1,5. When Smart Imaging detects that a user is on a Chrome browser, the image is converted to WebP format, with size 500 x 500. And, unsharp mask=0.1,1,5 is at a WebP quality that matches a JPEG quality of 85 as close as possible. The footprint of that WebP conversion is compared with the JPEG, and the smaller of the two is returned. -->

<!-- QUESTION BELOW WAS REMOVED AS PER CQDOC-22085

+++**Do I have to change any URLs, image presets, or deploy new code on my site?**

No. Smart Imaging works seamlessly with your existing image URLs and image presets. In addition, Smart Imaging does not require you to add code to your website to detect a user's browser. All of this functionality is handled automatically.

<!-- Smart Imaging works seamlessly with your existing image URLs and image presets if you configure Smart Imaging on your existing custom domain. In addition, Smart Imaging does not require you to add any code on your website to detect a user's browser. It is all handled automatically.

In case you must configure a new custom domain to use Smart Imaging, the URLs must be updated to reflect this custom domain.

To understand pre-requisites for Smart Imaging, see [Am I eligible to use Smart Imaging?](#am-i-eligible-to-use-smart-imaging) -->

<!-- OLD As mentioned earlier, Smart Imaging supports only JPEG and PNG image formats. For other formats, you need to append the `bfc=off` modifier to the URL as described earlier. 

-->

+++**Funktioniert die intelligente Bildbearbeitung mit HTTPS? Und mit HTTP/2?**

Ja, zu beiden Fragen. Die intelligente Bildbearbeitung funktioniert bei Bildern, die über HTTP, HTTPS oder HTTP/2 bereitgestellt wurden.
+++

+++**Bin ich zur Verwendung der intelligenten Bildbearbeitung berechtigt?**

Die intelligente Bildbearbeitung kann sofort von allen Kundinnen und Kunden verwendet werden. Um die Vorteile zu nutzen, fügen Sie einfach `bfc=on`, `dpr=on,dprValue` oder `network=on` oder alle drei Parametereinstellungen zu Ihren vorhandenen URLs oder Vorgaben hinzu.

Um die intelligente Bildbearbeitung zu aktivieren, muss Dynamic Media Classic bzw. Dynamic Media im Experience Manager-Konto Ihres Unternehmens das mit Adobe gebündelte CDN (Content Delivery Network) als Teil der Lizenz umfassen.

+++

+++**Wie kann ich die intelligente Bildbearbeitung für mein Konto aktivieren?**

Um die intelligente Bildbearbeitung zu verwenden, fügen Sie einfach `bfc=on`, `dpr=on,dprValue` oder `network=on` oder alle drei Parametereinstellungen zu Ihren vorhandenen URLs oder Vorgaben hinzu. Wenn Sie diese Änderungen nicht manuell vornehmen möchten, können Sie die intelligente Bildbearbeitung standardmäßig aktivieren lassen, indem Sie einen Support-Fall erstellen.

Geben Sie beim Erstellen des Support-Falles an, welche Funktionen der intelligenten Bildbearbeitung für Ihr Konto aktiviert werden sollen:

* Browser-Formatkonvertierung (WebP oder AVIF)
* Optimierung der Netzwerkbandbreite

>[!NOTE]
>
>Die DPR erfordert Client-seitige Anpassungen, um den korrekten `dprValue` zu ermitteln. Daher empfiehlt Adobe die Aktivierung der DPR über URLs durch Anhängen von `dpr=on,dprValue`.

**So erstellen Sie einen Support-Fall, um die intelligente Bildbearbeitung in Ihrem Konto zu aktivieren:**

1. [Verwenden Sie die Admin Console, um mit der Erstellung eines neuen Support-Falles zu beginnen.](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html).
1. Geben Sie in Ihrem Support-Fall die folgenden Informationen an:

   * **Kontaktdetails des Hauptansprechpartners:**

      * Geben Sie Ihren Name, Ihre E-Mail-Adresse und Ihre Telefonnummer an.

   * **Zu aktivierende Funktionen der intelligenten Bildbearbeitung:**

      * Geben Sie die für Ihr Konto gewünschten Funktionen an:

         * Browser-Formatkonvertierung: WebP oder AVIF
         * Optimierung der Netzwerkbandbreite
         * DPR: Die DPR erfordert Client-seitige Anpassungen, um den korrekten `dprValue` zu ermitteln. Daher empfiehlt Adobe die Aktivierung der DPR über URLs durch Anhängen von `dpr=on,dprValue`.

   * **Domain für intelligente Bildbearbeitung:**

      * Liste aller relevanten Domains, z. B. *`company.com`* oder *`mycompany.scene7.com`*
      * Die intelligente Bildbearbeitung unterstützt sowohl generische als auch benutzerdefinierte Domains.
      * Öffnen Sie die [Dynamic Media Classic-Desktop-Anwendung](https://experienceleague.adobe.com/de/docs/dynamic-media-classic/using/getting-started/signing-out#getting-started) und melden Sie sich bei Ihrem Unternehmenskonto an, um Ihre Domains zu ermitteln.

         1. Wählen Sie **[!UICONTROL Einstellungen]** > **[!UICONTROL Anwendungseinrichtung]** > **[!UICONTROL Allgemeine Einstellungen]**.
         1. Suchen Sie nach dem Feld **[!UICONTROL Veröffentlichungs-Server-Name]**, um Ihre Domain zu bestätigen.
         1. Vergewissern Sie sich, dass Sie das CDN von Adobe anstelle eines CDN von einem anderen Anbieter verwenden.

   * **Angabe der HTTP/2-Unterstützung:**

      * Geben Sie an, ob Sie auf eine Nutzung der intelligenten Bildbearbeitung über HTTP/2 angewiesen sind.

1. Der Adobe-Kundendienst aktiviert standardmäßig die angeforderten Funktionen der intelligenten Bildbearbeitung, sodass Parameter nicht manuell an URLs angehängt werden müssen.
1. Adobe empfiehlt, die Time-to-Live (TTL) auf mindestens 24 Stunden festzulegen, um die Leistung durch das Zwischenspeichern zu maximieren.
So passen Sie die TTL an:

   1. **Für Dynamic Media Classic:**
      1. Wechseln Sie zu **[!UICONTROL Einstellungen]** > **[!UICONTROL Anwendungseinstellungen]** > **[!UICONTROL Veröffentlichungseinstellungen]** > **[!UICONTROL Image-Server]**.
      1. Stellen Sie den Wert **[!UICONTROL Standard-Gültigkeitsdauer für Client-Cache]** auf mindestens 24 Stunden ein.
   1. **Für Dynamic Media in Adobe Experience Manager:**
      1. Befolgen Sie [diese Anweisungen](/help/assets/dynamic-media/config-dm.md).
      1. Stellen Sie den Wert **[!UICONTROL Gültigkeit]** auf mindestens 24 Stunden ein.

+++

+++**Wann ist mein Konto für die intelligente Bildbearbeitung aktiviert?**

Der Support bearbeitet Anfragen in der Reihenfolge ihres Eingangs gemäß der Warteliste.

>[!NOTE]
>
>Die Vorlaufzeit kann lang sein, da zum Aktivieren der Funktion „Intelligente Bildbearbeitung“ der Cache von Adobe gelöscht werden muss. Daher kann nur jeweils eine geringe Anzahl von Kunden gleichzeitig umgestellt werden.

+++

+++**Gibt es Risiken bei der Verwendung der intelligenten Bildbearbeitung?**

Es besteht kein Risiko für eine Kunden-Web-Seite. Die Umstellung auf die intelligente Bildbearbeitung löscht jedoch Ihren CDN-Cache. Dieser Vorgang umfasst die Umstellung auf eine neue Konfiguration von Dynamic Media Classic oder Dynamic Media in Experience Manager.

Zu Beginn der Übergangsphase werden die nicht im Cache gespeicherten Bilder direkt an die ursprünglichen Server von Adobe übertragen, bis der Cache neu aufgebaut wurde. Aus diesem Grund führt Adobe nur wenige Umstellungen gleichzeitig durch, wodurch eine akzeptable Leistung aufrechterhalten werden kann, wenn Anforderungen aus der Quelle abgerufen werden. Bei den meisten Kundinnen und Kunden ist der CDN-Cache innerhalb von ein bis zwei Tagen wieder vollständig neu aufgebaut.

+++

+++**Kann ich überprüfen, ob die intelligente Bildbearbeitung funktioniert?**

Ja. Sie können Folgendes tun:

1. Laden Sie nach der Konfiguration Ihres Kontos mit der intelligenten Bildbearbeitung eine Dynamic Media-Bild-URL von Dynamic Media Classic oder Adobe Experience Manager in den Browser.
1. Öffnen Sie den Chrome-Entwicklerbereich, indem Sie im Browser zu **[!UICONTROL Anzeigen]** > **[!UICONTROL Entwickler]** > **[!UICONTROL Entwickler-Tools]** wechseln. Selbstverständlich können Sie auch ein anderes Browser-Entwickler-Tool Ihrer Wahl verwenden.

1. Stellen Sie sicher, dass der Cache deaktiviert ist, wenn die Entwickler-Tools geöffnet sind.

   * Gehen Sie unter Windows® im Bereich der Entwickler-Tools zu den Einstellungen und wählen Sie dann das Kontrollkästchen **[!UICONTROL Cache deaktivieren]** aus (während DevTools geöffnet ist).
   * Gehen Sie unter macOS im Entwicklerbereich zur Registerkarte **[!UICONTROL Netzwerk]** und wählen Sie die Option **[!UICONTROL Cache deaktivieren]** aus.

1. Sie werden feststellen, dass der Content-Typ in das entsprechende Format umgewandelt wird. Der folgende Screenshot zeigt ein PNG-Bild, das in Chrome dynamisch ins WebP-Format konvertiert wird. Wenn für Ihre Domain AVIF aktiviert ist, wird AVIF auch im Inhaltstyp angezeigt.
1. Wiederholen Sie diesen Test auf verschiedenen Browsern und bei unterschiedlichen Benutzerbedingungen.

>[!NOTE]
>
>Nicht alle Bilder werden konvertiert. Die intelligente Bildbearbeitung entscheidet, ob die Konvertierung die Leistung verbessern kann. In einigen Fällen, in denen kein Leistungsgewinn erwartet wird oder das Format nicht JPEG oder PNG ist, wird das Bild nicht konvertiert.

![image2017-11-14_15398](assets/image2017-11-14_15398.png)

+++

+++**Gibt es eine Möglichkeit, die Vorteile der intelligenten Bildbearbeitung zu erkennen?**

Ja. Der Header der intelligenten Bildbearbeitung bestimmt die Vorteile der intelligenten Bildbearbeitung. Wenn die intelligente Bildbearbeitung aktiviert ist, wird nach der Anforderung eines Bildes unter der Überschrift **[!UICONTROL Antwort-Header]** wie im folgenden hervorgehobenen Beispiel `-X-Adobe-Smart-Imaging` angezeigt:

![Header der intelligenten Bildbearbeitung](/help/assets/dynamic-media/assets/smartimagingheader.png)

Aus diesem Header geht Folgendes hervor:

* Die intelligente Bildbearbeitung funktioniert für das Unternehmen.
* Ein positiver Wert bedeutet, dass die Konvertierung erfolgreich war. In diesem Fall wird ein neues WebP-Bild zurückgegeben.
* Ein negativer Wert bedeutet, dass die Konvertierung nicht erfolgreich war. In diesem Fall wird das ursprünglich angeforderte Bild zurückgegeben (standardmäßig JPEG, falls nicht angegeben).
* Ein positiver Wert gibt den Byte-Unterschied zwischen dem angeforderten Bild und dem neuen Bild an. Im obigen Beispiel wurden `75048` Byte oder ca. 75 KB für ein Bild eingespart.
* Ein negativer Wert bedeutet, dass das angeforderte Bild kleiner als das neue Bild ist. Die negative Größendifferenz wird angezeigt, aber es wird nur das ursprünglich angeforderte Bild bereitgestellt.

>[!NOTE]
>
>**X-Adobe-Smart-Imaging = -1, WebP bereitgestellt**
>
>Wenn `X-Adobe-Smart-Imaging` den Wert -1 hat und WebP weiterhin bereitgestellt wird, ist die intelligente Bildbearbeitung aktiv. Die Größenvorteile wurden jedoch aufgrund von veraltetem Cache nicht berechnet. Sie können `cache=update` (nur einmal) in der URL des Bildes verwenden, um dieses Problem zu beheben.
>Beispiel für die Verwendung des Modifikators:
>`https://smartimaging.scene7.com/is/image/SmartImaging/sample1?cache=update`
>Um den gesamten Cache ungültig zu machen, müssen Sie einen Support-Fall erstellen.

+++

+++**Kann ich die AVIF-Optimierung in der intelligenten Bildbearbeitung deaktivieren?**

Ja. Wenn Sie zur standardmäßigen Bereitstellung von WebP zurückwechseln möchten, erstellen Sie einen entsprechenden Support-Fall. Wie üblich können Sie die intelligente Bildbearbeitung deaktivieren, indem Sie den Modifikator `bfc=off` zur Bild-URL hinzufügen. Sie können jedoch weder WebP noch AVIF im URL-Modifikator für die intelligente Bildbearbeitung auswählen. Diese Funktion wird auf der Ebene Ihres Unternehmenskontos gepflegt.

+++

+++**Warum schlägt meine Anfrage fehl, wenn ich im Chrome-Webbrowser eine URL mit „fmt=tif“ habe?**

Dieser Fehler tritt nicht auf, wenn die intelligente Bildbearbeitung in Ihrem Konto nicht aktiviert ist. Die intelligente Bildbearbeitung funktioniert nur für das JPEG- und das PNG-Format.

Um diesen Fehler zu vermeiden, haben Sie folgende Möglichkeiten:

* Geben Sie JPEG oder PNG an oder
* verwenden Sie den Modifikator `fmt` überhaupt nicht oder
* verwenden Sie das vom Browser bevorzugte Format, das von der intelligenten Bildbearbeitung definiert wird. Sie können beispielsweise WebP für den Chrome-Webbrowser verwenden.

+++

+++**Kann ich ein TIFF-Bild von der URL eines Bildes herunterladen?**

Ja. Fügen Sie `fmt=tif` und `bfc=off` zum URL-Pfad des Bildes hinzu.

+++

+++**Verwaltet die intelligente Bildbearbeitung die Einstellungen für Bildformat und Bildqualität?**

Ja. Die intelligente Bildbearbeitung verwendet sowohl Format als auch Qualität. Die übrigen Parameter bleiben unverändert, wenn sie in der URL des Bildes angefordert werden.

+++

+++**Kann ich eine minimale und maximale Qualitätseinstellung festlegen?**

Nein. Derzeit ist dies nicht vorgesehen.

+++

+++**Passt die intelligente Bildbearbeitung die Einstellung für die prozentuale Ausgabequalität an?**

Ja. Die intelligente Bildbearbeitung passt den Qualitätsprozentsatz automatisch an. Diese Qualität wird mithilfe eines maschinellen Lernalgorithmus ermittelt, der von Adobe entwickelt wurde. Er ist nicht bereichsspezifisch.

+++

+++**Wird nur JPEG und PNG durch die intelligente Bildbearbeitung ersetzt?**

Ja. Diese Funktion funktioniert nur für JPEG und PNG.

+++

+++**Warum wird manchmal JPEG anstelle von WebP an Chrome zurückgegeben?**

Die intelligente Bildbearbeitung entscheidet, ob die Konvertierung vorteilhaft ist. Das neue Bild wird nur zurückgegeben, wenn die Konvertierung von Vorteil ist.

+++

+++**Warum funktioniert das Geräte-Pixel-Verhältnis (DPR) bei zusammengesetzten Bildern nicht wie erwartet?**

Wenn ein zusammengesetztes Bild zu viele Ebenen umfasst, kann die DPR-Funktionalität bei Verwendung eines Positionsmodifikators beeinträchtigt sein. Dieses Problem ist bekannt und wird in künftigen Versionen der intelligenten Bildbearbeitung behoben. Wenn andere Funktionen der intelligenten Bildbearbeitung nicht wie erwartet funktionieren, können Sie einen Support-Fall erstellen, um das Problem zu melden.

+++

+++**Warum wird PNG durch die intelligente Bildbearbeitung in verlustfreies WebP/AVIF konvertiert?**

Da PNG ein verlustfreies Format ist, wurden frühere WebP- und AVIF-Bereitstellungen verlustfrei durchgeführt, was zu einer höheren Größe als erwartet führte. Die intelligente Bildbearbeitung unterstützt jetzt verlustreiche Konvertierungen. Sie können den Modifikator `cache=update` in einer Bildanforderung verwenden (nur einmal), um dieses Problem zu beheben. Ein Beispiel für die Verwendung dieses Modifikators:

`https://smartimaging.scene7.com/is/image/SmartImaging/sample1?cache=update`

Um den gesamten Cache ungültig zu machen, müssen Sie einen entsprechenden Support-Fall erstellen.

+++

+++**Kann ich die verlustfreie Konvertierung von PNG in der intelligenten Bildbearbeitung weiterhin verwenden?**

Ja. Die intelligente Bildbearbeitung unterstützt jetzt verlustreiche Konvertierungen basierend auf der Qualitätsstufe. Um die verlustfreie Konvertierung weiterhin zu verwenden, legen Sie die Qualität auf 100 fest, entweder über die Einstellungen Ihres Unternehmens oder indem Sie dem URL-Pfad des Bildes `qlt=100` hinzufügen.

+++







<!-- ## If Smart Imaging manages the quality settings, are there minimums and maximums I can set? For example, is it possible to set "no lower than 60" and "no greater than 80 quality"? {#minimum-maximum}

There is no such provisioning ability in the current Smart Imaging. -->

<!-- ## Sometimes a JPEG image is returned to Chrome instead of a WebP image. Why does that change happen? {#jpeg-webp}

Smart Imaging determines if the conversion is beneficial or not. It returns the new image only if the conversion results in a smaller file size with comparable quality.

How does Smart Imaging DPR optimization work with Adobe Experience Manager Sites components and Dynamic Media viewers?

* Experience Manager Sites Core Components are configured by default for DPR optimization. To avoid oversized images owing to server-side Smart Imaging DPR optimization, `dpr=off` is always added to Experience Manager Sites Core Components Dynamic Media images.
* Given Dynamic Media Foundation Component is configured by default for DPR optimization, to avoid oversized images owing to server-side Smart Imaging DPR optimization, `dpr=off` is always added to Dynamic Media Foundation Component images. Even if customer deselects DPR optimization in DM Foundation Component, server-side Smart Imaging DPR does not kick in. In summary, in the DM Foundation Component, DPR optimization comes into effect based on DM Foundation Component level setting only.
* Any viewer side DPR optimization works in tandem with server-side Smart Imaging DPR optimization, and does not result in over-sized images. In other words, wherever DPR is handled by the viewer, such as the main view only in a zoom-enabled viewer, the server-side Smart Imaging DPR values are not triggered. Likewise, wherever viewer elements, such as swatches and thumbnails, do not have DPR handling, the server-side Smart Imaging DPR value is triggered.

See also [When working with images](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md#when-working-with-images) and [When working with Smart Crop](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md#when-working-with-smart-crop).

>[!MORELIKETHIS]
>
>* [Image optimization with next generation image formats WebP and AVIF](https://medium.com/adobetech/image-optimisation-with-next-gen-image-formats-webp-and-avif-248c75afacc4). 
-->
