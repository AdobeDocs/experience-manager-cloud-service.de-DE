---
title: 'Best Practices für die Optimierung der Bildqualität  '
description: Erfahren Sie mehr über Best Practices zur Optimierung der Qualität Ihrer Bild-Assets mit Dynamic Media.
contentOwner: Rick Brough
feature: Asset Management, Best Practices
role: User
exl-id: 2efc4a27-01d7-427f-9701-393497314402
source-git-commit: c82f84fe99d8a196adebe504fef78ed8f0b747a9
workflow-type: tm+mt
source-wordcount: '1694'
ht-degree: 98%

---

# Best Practices für die Optimierung der Bildqualität {#best-practices-for-optimizing-the-quality-of-your-images}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime und Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b>AEM Assets-Integration mit Edge Delivery Services</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>Erweiterbarkeit der Benutzeroberfläche</b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b>Aktivieren von Dynamic Media Prime und Ultimate</b></a>
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b>Best Practices für die Suche</b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b>Best Practices für Metadaten</b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b>Content Hub</b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b>Dynamic Media mit OpenAPI-Funktionen</b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b>Entwicklerdokumentation zu AEM Assets</b></a>
        </td>
    </tr>
</table>

{{work-with-dynamic-media}}

Die Bildqualität zu optimieren, kann zeitaufwendig sein. Denn viele Faktoren tragen dazu bei, akzeptable Ergebnisse zu erzielen. Die Ergebnisse sind teilweise subjektiv, da jeder Mensch die Bildqualität unterschiedlich wahrnimmt. Daher ist strukturiertes Experimentieren entscheidend.

Adobe Experience Manager umfasst mehr als 100 Bildbereitstellungsbefehle für Dynamic Media, mit denen Bilder angepasst und optimiert und Ergebnisse gerendert werden können. Mit den folgenden Richtlinien können Sie den Prozess anhand von einigen wesentlichen Befehlen und Best Practices optimieren und schnell angemessene Ergebnisse erzielen.

<!-- ADDED THE FOLLOWING TOPIC AS PER CQDOC-21594 -->

## Aktivieren der intelligenten Bildbearbeitung in Dynamic Media {#bp-enable-smart-imaging}

**Intelligente Bildbearbeitung:**

* Die Aktivierung der intelligenten Bildbearbeitung in Dynamic Media ermöglicht eine automatische Optimierung von Format, Größe und Qualität eines Bildes auf Grundlage der Client-Browser-Funktionen.
Möchten Sie mehr erfahren?  Navigieren Sie zu [Intelligente Bildbearbeitung](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/dynamicmedia/imaging-faq)
* Sie verbessert die Leistung bei der Bildbereitstellung durch die dynamische Anpassung dieser Parameter.
* Sie können die intelligente Bildbearbeitung mit dem Tool zur Selbstbewertung [Snapshot](https://snapshot.scene7.com/) bewerten.

**Bildformate:**

* Vermeiden Sie die Verwendung expliziter Befehle `fmt=webp` oder `fmt=avif` in einer URL, es sei denn, sie sind für einen Anwendungsfall speziell erforderlich.
* Die intelligente Bildbearbeitung wählt automatisch das beste Format aus, was zu optimalen Bandbreiteneinsparungen führt.

**Standardverhalten:**

* Wenn in der URL kein Formatbefehl angegeben und die intelligente Bildbearbeitung nicht aktiviert ist, wird bei der Bildbereitstellung von Dynamic Media standardmäßig das JPEG-Format verwendet.

Indem Sie fundierte Entscheidungen bezüglich der Bildformate treffen und die intelligente Bildbearbeitung aktivieren, können Sie die Performance und das Anwendererlebnis erheblich beeinflussen.


<!-- ADDED THE FOLLOWING TOPIC AS PER CQDOC-21594 -->

## Best Practices für die Auswahl des Quellbilds {#bp-select-source-image}

Wichtige Überlegungen zum Arbeiten mit Quellbildern:

* **Format des Quellbilds:**
   * Durch die Verwendung verlustfreier Formate wie PNG, TIFF oder PSD wird sichergestellt, dass die Bildqualität keine Komprimierungsartefakte enthält und hoch bleibt.
   * In diesen Formaten bleiben alle ursprünglichen Daten erhalten, wodurch sie sich ideal für die Bearbeitung und Weiterverarbeitung eignen.
* **Größe des Quellbilds:**
   * Der Start mit einem hochauflösenden Bild bietet mehr Details und Flexibilität.
   * Wenn Bilder in unterschiedlichen Größen angezeigt werden müssen (z. B. geräteübergreifend oder über Bildschirmauflösungen hinweg), ermöglicht die Anzeige eines größeren Quellbilds eine bessere Skalierung.
   * Bei Bildern, die Zoomen unterstützen (wie Produktfotos), sollten Sie auf der längsten Seite Abmessungen von etwa 2.000 Pixel oder mehr anvisieren.
   * Logos oder Banner, die nicht vergrößert werden müssen, können in der für den vorgesehenen Zweck benötigten Größe hochgeladen werden.

Wenn Sie diese umsichtigen Entscheidungen auf Quellebene treffen, können Sie erheblich zur Gesamtqualität Ihres visuellen Inhalts beitragen.

<!-- REMOVED TOPIC AS PER CQDOC-21594
## Best practices for image format (`&fmt=`) {#best-practices-for-image-format-fmt}

* JPG or PNG are the best choices to deliver images in good quality and with manageable size and weight.
* If no format command is supplied in the URL, Dynamic Media Image Delivery defaults to JPG for delivery.
* JPG compresses at a ratio of 10:1 and usually produces smaller image file sizes. PNG compresses at a ratio of about 2:1, except when images contain a white background. Typically though, PNG file sizes are larger than JPG files.
* JPG uses lossy compression, meaning that picture elements (pixels) are dropped during compression. PNG on the other hand uses lossless compression.
* JPG often compresses photographic images with better fidelity than synthetic images with sharp edges and contrast.
* If your images contain transparency, use PNG because JPG does not support transparency.

As a best practice for image format, start with the most common setting `&fmt=JPG`. -->

## Best Practices für die Bildgröße {#best-practices-for-image-size}

Eine der häufigsten Aufgaben betrifft die dynamische Reduzierung der Bildgröße. Dabei wird die Größe angegeben sowie (optional), welcher Downsampling-Modus für die Verkleinerung des Bilds verwendet wird.

* Für die Bildgröße ist es am besten und einfachsten, `&wid=<value>` und `&hei=<value>,` oder nur `&hei=<value>` zu verwenden. Mit diesen Parametern wird die Bildbreite automatisch entsprechend dem Seitenverhältnis festgelegt.
* `&resMode=<value>` steuert den Algorithmus für das Downsampling. Beginnen Sie mit `&resMode=sharp2`. Mit diesem Wert erreichen Sie die beste Bildqualität. Der Downsampling-Wert `value =bilin` ist zwar schneller, führt aber auch oft zum Aliasing von Artefakten.

Verwenden Sie als Best Practice für die Bildgröße `&wid=<value>&hei=<value>&resMode=sharp2` oder `&hei=<value>&resMode=sharp2`.

## Best Practices für Bild-Scharfzeichnung {#best-practices-for-image-sharpening}

Die Bild-Scharfzeichnung stellt den komplexesten Aspekt bei der Kontrolle von Bildern auf Websites dar. Hier werden viele Fehler gemacht. Nehmen Sie sich die Zeit und machen Sie sich mit der Funktionsweise von Scharfzeichnung und Unschärfemaske in Experience Manager vertraut, indem Sie die folgenden nützlichen Ressourcen lesen:

* Das Whitepaper [Best Practices für Adobe Dynamic Media Classic – Bildqualität und Scharfzeichnen](/help/assets/dynamic-media/assets/sharpening_images.pdf) gilt auch für Experience Manager.

* Sehen Sie sich das Video [Verwenden von Bildscharfzeichnung mit Experience Manager – Dynamic Media](https://experienceleague.adobe.com/de/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-image-sharpening-feature-video-use#dynamic-media) an.

Mit Experience Manager können Sie Bilder bei der Aufnahme, bei der Ausgabe oder bei beidem scharfzeichnen. Normalerweise ist es jedoch am besten, Bilder mit nur einer oder der anderen Methode scharfzuzeichnen, jedoch nicht mit beiden. Normalerweise erhalten Sie die besten Ergebnisse beim Scharfzeichnen von Bildern bei der Bereitstellung mit einer URL.

Es gibt zwei Methoden zum Scharfzeichnen von Bildern:

* Einfache Scharfzeichnung (`&op_sharpen`): Dies ähnelt dem in Photoshop verwendeten Scharfzeichnungsfilter und wendet einfache Scharfzeichnung auf die endgültige Ansicht des Bildes nach der dynamischen Skalierung an. Diese Methode kann aber nicht vom Benutzer konfiguriert werden. Als Best Practice wird empfohlen, `&op_sharpen` nur zu verwenden, wenn es unbedingt erforderlich ist.
* Unschärfemaske (`&op_USM`): Die Unschärfemaske ist ein dem Branchenstandard entsprechender Scharfzeichnungsfilter. Als Best Bractice wird empfohlen, Bilder anhand der folgenden Richtlinien mit der Unschärfemaske scharfzuzeichnen. Bei Verwendung der Unschärfemaske können Sie die drei folgenden Parameter steuern:

   * `&op_sharpen=`amount,radius,threshold

      * **[!UICONTROL amount]** (0-5, Stärke des Effekts)
      * **[!UICONTROL radius]** (0-250, Breite der „Scharfzeichnungslinien“ um das scharfgezeichnete Objekt, in Pixel gemessen)

     Denken Sie daran, dass sich die Parameter „radius“ und „amount“ gegenseitig beeinflussen.  Wenn Sie „radius“ reduzieren, können Sie dies durch eine Erhöhung von „amount“ kompensieren.  Der Radius ermöglicht eine genauere Kontrolle, da mit einem niedrigeren Wert nur die Kantenpixel scharfgezeichnet werden, während mit einem höheren Wert mehr Pixel scharfgezeichnet werden.

      * **[!UICONTROL threshold]** (0-255, Sensitivität des Effekts)

     Dieser Parameter bestimmt, wie stark sich die scharfgezeichneten Pixel vom Umgebungsbereich unterscheiden müssen, damit sie als Kantenpixel eingestuft und vom Filter scharfgezeichnet werden. Mit dem Parameter **[!UICONTROL threshold]** können Sie die übermäßige Scharfzeichnung von Bereichen mit ähnlichen Farben, wie Hauttönen, vermeiden. Bei einem Schwellenwert von 12 werden beispielsweise leichte Variationen der Hauttonhelligkeit ignoriert, um kein „Rauschen“ zu erzeugen, trotzdem wird bei kontrastreichen Bereichen, z. B. wo Wimpern auf die Haut treffen, Kantenkontrast hinzugefügt.

     Weitere Informationen zum Festlegen dieser drei Parameter, einschließlich Best Practices für den Filter, finden Sie in den folgenden Ressourcen:

      * Das Whitepaper [Best Practices für Adobe Dynamic Media Classic – Bildqualität und Scharfzeichnen](/help/assets/dynamic-media/assets/sharpening_images.pdf) gilt auch für Experience Manager.

      * Sehen Sie sich das Video [Verwenden von Bildscharfzeichnung mit Experience Manager – Dynamic Media](https://experienceleague.adobe.com/de/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-image-sharpening-feature-video-use#dynamic-media) an.

      * In Experience Manager können Sie auch einen vierten Parameter steuern: monochrome (0,1). Dieser Parameter bestimmt, ob eine Unschärfemaske auf jede Farbkomponente separat (mit dem Wert 0) oder auf die Bildhelligkeit/-intensität (mit dem Wert 1) angewendet wird.

Es wird empfohlen, mit dem Unschärfemasken-Parameter für den Radius zu beginnen. Sie können zu Beginn die folgenden Radiuseinstellungen verwenden:

* **[!UICONTROL Website]**: 0,2–0,3 Pixel
* **[!UICONTROL Fotodruck (250–300 ppi)]**: 0,3–0,5 Pixel
* **[!UICONTROL Offset-Druck (266–300 ppi)]**: 0,7–1,0 Pixel
* **[!UICONTROL Leinwanddruck (150 ppi)]**: 1,5–2,0 Pixel

Erhöhen Sie den Wert schrittweise von 1,75 auf maximal 4. Wenn die Scharfzeichnung noch immer nicht Ihren Wünschen entspricht, erhöhen Sie den Radius um einen Dezimalschritt und setzen Sie den Wert erneut von 1,75 auf 4 herauf. Wiederholen Sie diesen Vorgang nach Bedarf.

Belassen Sie die Einstellung des Parameters „monochrome“ auf 0.

### Best Practices für JPEG-Komprimierung (`&qlt=`) {#best-practices-for-jpef-compression-qlt}

* Dieser Parameter steuert die Qualität der JPG-Kodierung. Ein höherer Wert führt zu einer höheren Bildqualität, aber auch zu einer größeren Datei. Ein niedrigerer Wert dagegen bedeutet eine niedrigere Bildqualität, aber auch eine kleinere Datei. Der Bereich für diesen Parameter liegt zwischen 0 und 100.
* Um die Qualität zu optimieren, setzen Sie den Parameterwert nicht auf 100. Der Unterschied zwischen einer Einstellung von 90 oder 95 und 100 ist fast nicht wahrnehmbar.  Und trotzdem wird mit 100 die Größe der Bilddatei auf unnötige Weise erhöht. Um die Qualität zu optimieren, aber zu vermeiden, dass Bilddateien zu groß werden, setzen Sie daher den Wert von `qlt= value` auf 90 oder 95.
* Erstellen Sie eine Bilddatei mit geringer Dateigröße bei akzeptabler Bildqualität, indem Sie `qlt= value` auf 80 setzen. Werte unter 70 bis 75 führen zu einer erheblichen Verschlechterung der Bildqualität.
* Als Best Practice wird empfohlen, einen Kompromiss zu wählen: Setzen Sie `qlt= value` dazu auf 85.
* Verwendung der Chroma-Markierung in `qlt=`

   * Der Parameter `qlt=` verfügt über eine zweite Einstellung, mit der Sie das RGB-Chromatizitäts-Downsampling aktivieren (mit dem Wert `,1`) oder deaktivieren (mit dem Wert `,0`) können.
   * Beginnen Sie der Einfachheit halber mit ausgeschaltetem RGB-Chromatizitäts-Downsampling (`,0`). Diese Einstellung führt normalerweise zu einer höheren Bildqualität, insbesondere bei synthetischen Bildern mit vielen scharfen Kanten und Kontrasten.

Verwenden Sie als Best Practice für die JPG-Komprimierung `&qlt=85,0`.

## Best Practices für die JPEG-Skalierung (`&jpegSize=`) {#best-practices-for-jpeg-sizing-jpegsize}

Der Parameter `jpegSize` ist nützlich, wenn Sie garantieren möchten, dass ein Bild eine bestimmte Größe für die Bereitstellung an Geräten mit begrenztem Speicher nicht übersteigt.

* Dieser Parameter wird in Kilobyte festgelegt (`jpegSize=&lt;size_in_kilobytes&gt;`). Damit wird die maximal zulässige Größe für die Bildbereitstellung definiert.
* `&jpegSize=` interagiert mit dem JPG-Komprimierungsparameter `&qlt=`. Wenn die JPG-Antwort mit dem angegebenen JPG-Komprimierungsparameter (`&qlt=`) nicht den Wert von jpegSize überschreitet, wird das Bild mit dem definierten Wert für `&qlt=` zurückgegeben. Andernfalls wird `&qlt=` schrittweise reduziert, bis das Bild der maximal zulässigen Größe entspricht. Oder bis das System feststellt, dass die Anpassung nicht möglich ist, und einen Fehler zurückgibt.

Legen Sie als Best Practice `&jpegSize=` fest und fügen Sie den Parameter `&qlt=` hinzu, wenn Sie JPG-Bilder an Geräte mit begrenztem Speicher bereitstellen.

## Zusammenfassung der Best Practices {#best-practices-summary}

Um eine hohe Bildqualität und kleine Dateien zu erreichen, wird als Best Practice empfohlen, mit der folgenden Kombination aus Parametern zu beginnen:

`fmt=jpg&qlt=85,0&resMode=sharp2&op_usm=1.75,0.3,2,0`

Diese Einstellungskombination sorgt in den meisten Fällen für hervorragende Ergebnisse.

Wenn das Bild weiter optimiert werden muss, passen Sie die Parameter für die Scharfzeichnung (Unschärfemaske) schrittweise an, beginnend mit einem Radius von 0,2 oder 0,3. Erhöhen Sie dann den Wert schrittweise von 1,75 auf maximal 4 (entspricht 400 % in Photoshop). Prüfen Sie, ob das gewünschte Ergebnis erreicht wird.

Wenn die Scharfzeichnungsergebnisse noch immer nicht zufriedenstellend sind, erhöhen Sie den Radius in Dezimalschritten. Beginnen Sie den Wert bei jedem Dezimalschritt bei 1,75 und erhöhen Sie diesen schrittweise auf 4. Wiederholen Sie diesen Vorgang, bis Sie das gewünschte Ergebnis erzielen. Die oben genannten Werte stellen zwar einen von Kreativstudios anerkannten Ansatz dar, Sie können aber auch mit anderen Werten beginnen und andere Strategien verfolgen. Sie entscheiden subjektiv, wann die Ergebnisse zufriedenstellend sind. Daher ist strukturiertes Experimentieren entscheidend.

Beim Experimentieren sind die folgenden allgemeinen Vorschläge hilfreich, um Ihren Workflow zu optimieren:

* Testen Sie verschiedene Parameter in Echtzeit direkt auf einer URL.
* Denken Sie daran, dass Sie Dynamic Media-Bildverarbeitungsbefehle in einer Bildvorgabe zusammenfassen können. Eine Bildvorgabe besteht im Grunde aus URL-Befehlsmakros mit benutzerspezifischen Vorgabenamen (wie `$thumb_low$` und `&product_high$`). Der benutzerdefinierte Vorgabenname in einem URL-Pfad ruft diese Vorgaben auf. Mit dieser Funktion können Sie Befehle und Qualitätseinstellungen für verschiedene Nutzungsmuster von Bildern auf Ihrer Website verwalten und die Gesamtlänge von URLs reduzieren.
* Experience Manager bietet außerdem erweiterte Funktionen für die Optimierung der Bildqualität, wie das Scharfzeichnen von Bildern bei der Aufnahme. Um die Rendering-Ergebnisse zu verfeinern und zu optimieren, können die [Consulting Services](https://business.adobe.com/de/customers/consulting-services/main.html) von Adobe Sie mit individuellen Einblicken und Best Practices unterstützen.
