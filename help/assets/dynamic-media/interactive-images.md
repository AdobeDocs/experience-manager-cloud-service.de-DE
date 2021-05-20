---
title: Interaktive Bilder
description: Erfahren Sie, wie Sie in Dynamic Media mit interaktiven Bildern arbeiten.
feature: Interaktive Bilder
role: Business Practitioner
exl-id: 89eef5e6-d508-4f33-b54e-24d4df49f8c3
source-git-commit: d3ee23917eba4a2e4ae1f2bd44f5476d2ff7dce1
workflow-type: tm+mt
source-wordcount: '4263'
ht-degree: 40%

---

# Interaktive Bilder {#interactive-images}

Sie können statische Bilder einfach für ansprechende, ansprechende Erlebnisse für Kunden gestalten, indem Sie Hotspots mit Shopping-Funktion per Drag-and-Drop auf ein Bild ziehen. Hotspots mit Shopping-Funktion kombinieren zusätzliche Informationen über ein Produkt oder einen Service mit einer direkten Point-of-Sale-Funktion &quot;Zum Warenkorb hinzufügen&quot;oder &quot;Kaufen&quot;. Kunden können auf diese Hotspots tippen, die direkt auf das Produkt oder den Dienst verweisen, es zu einem Warenkorb hinzufügen oder mit einer Webseite verknüpft werden. Direkte Erlebnisse wie diese erhöhen die Kundeninteraktion und Konversionen auf Ihrer Website.

Im Folgenden finden Sie ein Banner mit Shopping-Funktion und einem Popup-Fenster für Schnellansichten. Ein Benutzer aktiviert die Schnellansicht, indem er auf den Kreis oder &quot;Hotspot&quot;im Modell tippt.

![chlimage_1-152](assets/chlimage_1-368.png)

Siehe [Interaktive Bilder in Aktion](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion-QVzoom/index2-shoppable.html) auf der oben abgebildeten Web-Seite.

## Sehen Sie sich an, wie interaktive Bildbanner erstellt werden {#watch-how-interactive-image-banners-are-created}

Sehen Sie sich eine exemplarische Vorgehensweise zu [wie interaktive Bildbanner erstellt werden](https://s7d5.scene7.com/s7viewers/html5/VideoViewer.html?videoserverurl=https://s7d5.scene7.com/is/content/&amp;emailurl=https://s7d5.scene7.com/s7/emailFriend&amp;serverUrl=https://s7d5.scene7.com/is/image/&amp;config=Scene7SharedAssets/Universal_HTML5_Video_social&amp;contenturl=https://s7d5.scene7.com/skins/&amp;asset=S7tutorials/InteractiveCarouselBanner) (10 Minuten und 33 Sekunden). Außerdem erfahren Sie, wie Sie interaktive Bildbanner in der Vorschau anzeigen, bearbeiten und bereitstellen.

## Schnellstart: Interaktive Bilder {#quick-start-interactive-images}

Die folgende schrittweise Workflow-Beschreibung soll Ihnen dabei helfen, interaktive Bilder in Adobe Experience Manager Assets einzurichten und schnell auszuführen.

Suchen Sie nach der Überschrift **Beispiele** in einigen der Schnellstartaufgaben. Hier finden Sie ein kurzes Tutorial, das auf der folgenden [Beispiel-Web-Seite basiert, der noch keine interaktiven Bilder hinzugefügt wurden](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-0.html).



Das Tutorial veranschaulicht die Schritte zur Integration von interaktiven Bildern auf Ihrer eigenen Website.

Schritte zum Erstellen interaktiver Bilder:

1. **(Optional) Ermitteln von Hotspot-Variablen**. Wenn Sie Adobe Experience Manager Assets und Dynamic Media eigenständig verwenden, ermitteln Sie die dynamischen Variablen, die in Ihrer vorhandenen Schnellansichtsimplementierung verwendet werden. Dadurch wird sichergestellt, dass Sie beim Erstellen des interaktiven Bildes Hotspot-Daten eingeben können. Siehe [(Optional) Ermitteln von Hotspot-Variablen](#optional-identifying-hotspot-variables).
Wenn Sie jedoch Experience Manager-Sites, Experience Manager-eCommerce oder beides verwenden, ist dieser Schritt nicht erforderlich.

1. **(Optional) Erstellen einer Viewer-Vorgabe für interaktive Bilder**. Passen Sie das Grafikbild an, das zur Darstellung von Hotspots verwendet wird. Die Erstellung Ihrer eigenen Viewer-Vorgabe für interaktive Bilder ist nicht erforderlich, wenn Sie stattdessen die standardmäßig bereitgestellte Viewer-Vorgabe für interaktive Bilder namens `Shoppable_Banner` (Banner mit Shopping-Funktion) verwenden möchten.
Siehe [(Optional) Erstellen einer Viewer-Vorgabe für interaktive Bilder](/help/assets/dynamic-media/managing-viewer-presets.md#creating-a-new-viewer-preset).

1. **Hochladen eines Bildbanners**. Laden Sie Bildbanner hoch, die interaktiv sein sollen. Siehe  [Hochladen eines Bildbanners](#uploading-an-image-banner).

1. **Hinzufügen von Hotspots zu einem Bildbanner**. Fügen Sie einem Bildbanner einen oder mehrere Hotspots hinzu. Ordnen Sie jede Aktion einer Aktion wie einem Hyperlink, einer Schnellansicht oder einem Experience Fragment zu. Nachdem Sie Hotspots hinzugefügt haben, schließen Sie diese Aufgabe ab, indem Sie das interaktive Bild veröffentlichen.
Siehe [Hinzufügen von Hotspots zu einem Bildbanner](#adding-hotspots-to-an-image-banner).
Siehe [(Optional) Anzeigen einer Vorschau für interaktive Bilder](#optional-previewing-interactive-images). Bei Bedarf können Sie eine Darstellung des Banners mit Shopping-Funktion anzeigen und dessen Interaktivität testen.
Weitere Informationen zum Veröffentlichen von interaktiven Bild-Assets finden Sie unter [Veröffentlichen von Assets](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

1. **Hinzufügen eines interaktiven Bildes zu Ihrer Website oder zu Ihrer Website in Experience Manager**. Wenn Sie Sites, eCommerce oder beides verwenden, können Sie interaktive Bilder direkt zu einer Web-Seite in Experience Manager hinzufügen. Ziehen Sie die Komponente Interaktive Medien auf die Seite. Siehe [Hinzufügen von Dynamic Media-Assets zu Seiten](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md).
Wenn Sie eigenständig Experience Manager Assets und Dynamic Media verwenden, kopieren Sie den Einbettungscode auf Ihre Website. Integrieren Sie sie dann in Ihre vorhandene Schnellansicht. Siehe [Integrieren eines interaktiven Bildes auf Ihrer Website](#integrating-an-interactive-image-with-your-website).
Wenn Sie einen Drittanbieter-WCM (Web Content Manager) verwenden, integrieren Sie das neue interaktive Video in die vorhandene Schnellansicht auf Ihrer Website. Siehe [Integrieren eines interaktiven Bildes in einer vorhandenen Schnellansicht](#integrating-an-interactive-image-with-an-existing-quickview).

## (Optional) Ermitteln von Hotspot-Variablen {#optional-identifying-hotspot-variables}

>[!NOTE]
>
>Diese Aufgabe ist nur erforderlich, wenn Folgendes zutrifft:
>
>* Sie möchten dem Bild Interaktivität hinzufügen, indem Sie Schnellansichten aktivieren.
>* Ihre Implementierung von Experience Manager verwendet *nicht* ein eCommerce-Integrations-Framework, um Produktdaten aus jeder eCommerce-Lösung in den Experience Manager zu ziehen. Zu diesen Lösungen gehören IBM® WebSphere® Commerce, Elastic Path, SAP Hybris oder Intershop.

>
>
Wenn Ihre Implementierung von Experience Manager eCommerce verwendet, können Sie diese Aufgabe überspringen und mit der nächsten Aufgabe fortfahren.

Ermitteln Sie zunächst die dynamischen Variablen, die von Ihrer vorhandenen Schnellansichtsimplementierung verwendet werden, damit Sie Hotspot-Daten eingeben können, um das interaktive Bild zu erstellen.

Wenn Sie einem Bannerbild in Experience Manager Assets Hotspots hinzufügen, weisen Sie eine SKU (Stock Keeping Unit, Stock Keeping Unit) zu. Die SKU ist eine eindeutige Kennung für jedes einzelne Produkt oder jeden von Ihnen angebotenen Dienst. Fügen Sie jedem Hotspot weitere optionale Variablen hinzu. Diese Hotspot-Variablen werden später verwendet, um Hotspots mit Schnellansichtsinhalten abzugleichen.

Sie müssen die Anzahl und den Typ der Variablen für die Verknüpfung mit Hotspot-Daten korrekt identifizieren. Jeder dem Bannerbild hinzugefügte Hotspot muss ausreichend Informationen enthalten, um das Produkt im vorhandenen Backend-System eindeutig zu identifizieren.

Sie können ein Set aus Variablen für Hotspot-Daten auf mehrere Arten ermitteln.

Manchmal ist es ausreichend, IT-Experten zu konsultieren, die für die vorhandene Schnellansichtsimplementierung verantwortlich sind. Diese Personen kennen wahrscheinlich den Mindestsatz an Daten, die erforderlich sind, um die Schnellansicht im System zu identifizieren. Es ist jedoch auch möglich, einfach das vorhandene Verhalten des Frontend-Codes zu analysieren.

Die meisten Schnellansichtsimplementierungen verwenden das folgende Paradigma:

* Benutzer aktiviert ein Benutzeroberflächenelement auf der Website. Beispielsweise durch Klicken auf die Schaltfläche &quot;Schnellansicht&quot;.
* Die Website sendet bei Bedarf eine Ajax-Anfrage an das Backend, um die Schnellansichtsdaten oder -inhalte zu laden.
* Die Schnellansichtsdaten werden in den Inhalt übersetzt, um für das Rendern auf der Webseite vorbereitet zu werden.
* Schließlich zeigt der Frontend-Code diesen Inhalt visuell auf dem Bildschirm an.

Dann werden verschiedene Bereiche der vorhandenen Website besucht, auf denen die Schnellansichtsfunktion implementiert ist. Trigger dann die Schnellansicht an und ruf die Ajax-URL, die von der Webseite zum Laden der Schnellansichtsdaten oder -inhalte gesendet wird.

Normalerweise müssen Sie keine speziellen Debugging-Tools verwenden. Moderne Webbrowser verfügen über Web-Inspektoren, die dafür ausreichend sind. Die folgenden Webbrowser beispielsweise umfassen Web-Inspektoren:

* Um alle ausgehenden HTTP-Anfragen in Google Chrome anzuzeigen, drücken Sie F12, um den Bereich für Entwickler-Tools zu öffnen; klicken Sie dann auf die Registerkarte „Netzwerk“.
Drücken Sie bei einem Mac Befehlstaste+Wahltaste+I, um den Bereich für Entwickler-Tools zu öffnen, und klicken Sie dann auf die Registerkarte „Netzwerk“.

* In Firefox können Sie das Firebug-Plug-in aktivieren, indem Sie F12 drücken und die Registerkarte Netz verwenden. Sie können auch das integrierte Inspektor-Tool und dessen Registerkarte &quot;Netzwerk&quot;verwenden.
Drücken Sie bei einem Mac Befehlstaste+Wahltaste+I, um den Bereich für Entwickler-Tools zu öffnen, und klicken Sie dann auf die Registerkarte „Inspektor“.

Wenn die Netzwerküberwachung im Browser aktiviert ist, Trigger die Schnellansicht auf der Seite.

Suchen Sie nun die Schnellansichts-Ajax-URL im Netzwerkprotokoll und kopieren Sie die aufgezeichnete URL für die zukünftige Analyse. Normalerweise werden beim Trigger der Schnellansicht zahlreiche Anfragen an den Server gesendet. In der Regel ist die Schnellansichts-Ajax-URL eine der ersten in der Liste. Sie weist einen Teil oder Pfad mit einer komplexen Abfragezeichenfolge auf und ihr MIME-Typ lautet entweder `text/xml`, `text/html` oder `text/javascript`.

Während dieses Prozesses ist es wichtig, verschiedene Bereiche Ihrer Website mit verschiedenen Produktkategorien und -typen zu besuchen. Der Grund dafür ist, dass Schnellansichts-URLs Teile aufweisen können, die für eine bestimmte Website-Kategorie häufig sind. Sie ändern sich jedoch nur, wenn Sie einen anderen Bereich der Website besuchen.

Im einfachsten Fall ist der einzige variable Teil der Schnellansichts-URL die Produkt-SKU. In diesem Fall ist der SKU-Wert das einzige Datenelement, das Sie zum Hinzufügen von Hotspots zum Bannerbild benötigen.

In komplexen Fällen verfügt die Schnellansichts-URL jedoch zusätzlich zur SKU über verschiedene Elemente. Variierende Elemente können beispielsweise Kategorie-ID, Farbcode und Größencode umfassen. In solchen Fällen ist jedes Element eine separate Variable in Ihrer Hotspot-Datendefinition in der Funktion für interaktive Bilder mit Shopping-Funktion in Experience Manager-Assets.

Sehen Sie sich die folgenden Beispiele für Schnellansichts-URLs und die resultierenden Hotspot-Variablen an:

<table>
  <tbody>
  <tr>
    <td><p>Einzelne SKU, befindet sich in der Abfragezeichenfolge.</p> </td>
    <td><p>Die aufgezeichneten Schnellansichts-URLs umfassen Folgendes:</p>
    <ul>
      <li><p><code>https://server/json?productId=866558&amp;source=100</code></p> </li>
      <li><p><code>https://server/json?productId=1196184&amp;source=100</code></p> </li>
      <li><p><code>https://server/json?productId=1081492&amp;source=100</code></p> </li>
      <li><p><code>https://server/json?productId=1898294&amp;source=100</code></p> </li>
    </ul> <p>Der einzige variable Teil der URL ist der Wert des Abfrageparameters „productId=“ und ist offensichtlich ein SKU-Wert. Daher müssen nur die SKU-Felder der Hotspots mit Werten wie <strong><code>866558</code></strong>, <strong><code>1196184</code></strong>, <strong><code>1081492</code></strong>, <strong><code>1898294</code></strong> ausgefüllt werden.</p> </td>
  </tr>
  <tr>
    <td><p>Einzelne SKU, befindet sich im URL-Pfad.</p> </td>
    <td><p>Die aufgezeichneten Schnellansichts-URLs umfassen Folgendes:</p>
    <ul>
      <li><p><code>https://server/product/6422350843</code></p> </li>
      <li><p><code>https://server/product/1607745002</code></p> </li>
      <li><p><code>https://server/product/0086724882</code></p> </li>
    </ul> <p>Der variable Teil befindet sich im letzten Abschnitt des Pfads und wird zum SKU-Wert der Hotspots: <strong><code>6422350843</code></strong>, <strong><code>1607745002</code></strong>, <strong><code>0086724882</code></strong>.</p> </td>
  </tr>
  <tr>
    <td><p>SKU und Kategorie-ID in der Abfragezeichenfolge.</p> </td>
    <td><p>Die aufgezeichneten Schnellansichts-URLs umfassen Folgendes:</p>
    <ul>
      <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=305466</code></p> </li>
      <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=310181</code></p> </li>
      <li><p><code>https://server/quickView/product/?category=1740148&amp;prodId=308706</code></p> </li>
    </ul> <p>In diesem Fall liegen zwei abweichende Teile in der URL vor. Die SKU wird im <code>prodId</code> Parameter gespeichert, während die Kategorie-ID<code></code> im <code>category=</code> Parameter gespeichert wird.</p> <p>Im eigentlichen Sinne handelt es sich bei Hotspot-Definitionen um Paare. Das heißt, ein SKU-Wert und eine zusätzliche Variable namens <code>categoryId</code>. Die resultierenden Paare lauten wie folgt:</p>
    <ul>
      <li><p>Die SKU lautet <strong><code>305466</code></strong> und <code>categoryId</code> lautet <code>1100004</code>.</p> </li>
      <li><p>Die SKU lautet <strong><code>310181</code></strong> und <code>categoryId</code> lautet <strong><code>1100004</code></strong>.</p> </li>
      <li><p>Die SKU lautet <strong><code>308706</code></strong> und <code>categoryId</code> lautet <strong><code>1740148</code></strong>.</p> </li>
    </ul> <p> </p> </td>
  </tr>
  </tbody>
</table>

**Beispiel**

Sie können den in den drei oben genannten Beispielen verwendeten Ansatz auch auf die [Demo-Web-Seite](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-0.html) anwenden.

Die Demo-Web-Seite enthält mehrere Produktminiaturansichten, von denen jede eine Schnellansichtsschaltfläche mit der Bezeichnung &quot;Weitere Informationen&quot;aufweist. Wenn das Debugging-Tool Ihres Webbrowsers noch aktiviert ist, klicken Sie auf jede Schaltfläche und notieren Sie sich die aufgezeichneten Schnellansichts-URLs. Nachdem Sie alle vier auf der Seite verfügbaren Schnellansichten des Produkts aktiviert haben, verfügen Sie über die folgende Liste von Schnellansichtsanforderungen, die an das Backend gesendet wurden:

* `/datafeed/Men-Windbreaker.json`
* `/datafeed/Men-SimpleHenley.json`
* `/datafeed/Men-CamoPullover.json`
* `/datafeed/Women-QuiltedDownJacket.json`

Wenn Sie sich die Server-Aufrufe ansehen, sehen Sie, dass produktspezifische Informationen nur im Anfragepfad vorhanden sind. Beachten Sie außerdem, dass die Abfragezeichenfolge überhaupt nicht verwendet wird und zwei unterschiedliche Typen von Datenteilen beteiligt sind:

* Der erste Typ ist „Männer“ oder „Frauen“. Dies kann als „Produktkategorie“ bezeichnet werden.
* Der zweite Typ ist der Produktname, z. B. CamoPullover, der wahrscheinlich die Produkt-SKU ist.

Aufgrund dieser Informationen weist die gesamte Schnellansichts-URL das folgende Muster auf:

`/datafeed/$categoryId$-$SKU$.json`

Auf Grundlage einer solchen Analyse würden Sie `categoryId` und `SKU` für Hotspots verwenden.

Sie können jetzt ein Bildbanner hochladen und ihm Hotspots mit der Funktion für interaktive Bilder mit Shopping-Funktion in Experience Manager Assets hinzufügen.

## (Optional) Erstellen einer Viewer-Vorgabe für interaktive Bilder  {#optional-creating-an-interactive-image-viewer-preset}

Sie können die standardmäßige Viewer-Vorgabe für interaktive Bilder mit dem Namen `Shoppable_Banner` verwenden, die im Lieferumfang von Experience Manager-Assets enthalten ist. Sie können auch eine eigene benutzerdefinierte Viewer-Vorgabe für interaktive Bilder erstellen.

Wenn Sie eine benutzerdefinierte Viewer-Vorgabe für interaktive Bilder erstellen, können Sie das Erscheinungsbild von Hotspots auf dem Bildbanner bestimmen. Bei der Erstellung der Viewer-Vorgabe können Sie eine Hotspot-Grafik aus einer Galerie mit vordefinierten Bildern verwenden.

Nachdem Sie die Viewer-Vorgabe gespeichert haben, wird sie automatisch auf der Listenseite &quot;Viewer-Vorgabe&quot;in Experience Manager-Assets aktiviert (aktiviert). Diese Funktionalität bedeutet, dass sie in der interaktiven Medienkomponente sowie dann sichtbar ist, wenn Sie ein Asset anzeigen. Um jedoch *ein interaktives Banner mit dieser Viewer-Vorgabe bereitzustellen,* veröffentlichen *auch Ihre Viewer-Vorgabe.* Diese Regel gilt für benutzerdefinierte oder vordefinierte Viewer-Vorgaben.

**So erstellen Sie eine Viewer-Vorgabe für interaktive Bilder**

1. Tippen Sie links in der Leiste auf **[!UICONTROL Tools > Assets > Viewer-Vorgaben]**.
1. Tippen Sie in der Nähe der rechten oberen Ecke der Seite auf **[!UICONTROL Erstellen]**.
1. Geben Sie im Dialogfeld „Neue Viewer-Vorgabe“ einen Namen ein, um die Viewer-Vorgabe für interaktive Banner zu beschreiben.

   Dieser Titel wird nach dem Speichern auf der Listenseite &quot;Viewer-Vorgabe&quot;angezeigt.

1. Wählen Sie im Pulldown-Menü „Rich-Media-Typ“ die Option **[!UICONTROL Interaktives Bild]** aus.
1. Tippen Sie auf **[!UICONTROL Erstellen]**.
1. Tippen Sie auf der Seite „Viewer-Vorgabe bearbeiten“ auf die Registerkarte **[!UICONTROL Erscheinungsbild]**.
1. Führen Sie einen der folgenden Schritte aus:

   * Um ein eigenes Hotspot-Bild hochzuladen, das Sie für Bilder verwenden möchten, tippen Sie auf das Symbol für die Asset-Auswahl. Navigieren Sie auf der Seite Inhalt auswählen zum Hotspot-Bild, das Sie verwenden möchten, und wählen Sie es aus. Tippen Sie oben rechts auf das Symbol &quot;Häkchen&quot;.
   * Um ein vordefiniertes Hotspot-Bild auszuwählen, tippen Sie auf das Symbol für die Hotspot-Galerie. Tippen Sie in der Palette &quot;Hotspot-Galerie&quot;auf das gewünschte Hotspot-Bild.

1. Tippen Sie oben rechts auf **[!UICONTROL Speichern]**.

   Stellen Sie sicher, die neue Viewer-Vorgabe zu veröffentlichen.

   Siehe [Veröffentlichen von Viewer-Vorgaben](/help/assets/dynamic-media/managing-viewer-presets.md#publishing-viewer-presets).

   Sie sind nun bereit, ein Bildbanner hochzuladen.

## Hochladen eines Bildbanners   {#uploading-an-image-banner}

Wenn Sie die gewünschten Bilder bereits hochgeladen haben, fahren Sie mit dem nächsten Schritt fort: [Hinzufügen von Hotspots zu einem Bildbanner](#adding-hotspots-to-an-image-banner).

**So laden Sie ein Bildbanner hoch**

1. Laden Sie Bildbanner hoch, die interaktiv sein sollen.

   Informationen hierzu finden Sie unter [Hochladen von Assets](/help/assets/manage-digital-assets.md#uploading-assets).

   Sie können jetzt dem Bildbanner Hotspots hinzuzufügen. Anweisungen dazu finden Sie in der folgenden Aufgabe.

## Hinzufügen von Hotspots zu einem Bildbanner   {#adding-hotspots-to-an-image-banner}

Sie können einem Bildbanner Hotspots hinzufügen, indem Sie den Editor auf der Seite „Hotspot-Verwaltung“ verwenden.

Beim Hinzufügen von Hotspots können Sie sie als Popup-Schnellansichtsanzeige, als Hyperlink oder als Experience Fragment definieren.

Weitere Informationen finden Sie unter [Experience Fragments](/help/sites-cloud/authoring/fundamentals/experience-fragments.md).

>[!NOTE]
>
>Die Tools zur Freigabe in Social Media im interaktiven Bild werden nicht unterstützt, wenn Sie den Viewer in ein Experience Fragment einbetten. Verwenden oder erstellen Sie stattdessen Viewer-Vorgaben, die keine Tools zur Freigabe in Social Media haben. Mit diesen Viewer-Vorgaben können Sie sie erfolgreich in Experience Fragments einbetten.

Die Optionen „Rückgängig“ und „Wiederholen“ in der Nähe der oberen rechten Ecke der Seite werden während der aktuellen Erstellungs-/Bearbeitungssitzung unterstützt.

Wenn Sie die Erstellung des interaktiven Bildes abgeschlossen haben, können Sie die Vorschau verwenden, um eine Darstellung der Darstellung des interaktiven Bildes für Kunden anzuzeigen.

Siehe [(Optional) Anzeigen einer Vorschau für interaktive Bilder](#optional-previewing-interactive-images).

>[!NOTE]
>
>Wenn Sie einem Bild in einem interaktiven Bild oder einem Karussellbanner Hotspots hinzufügen, werden die Hotspot-Informationen am selben Metadatenspeicherort gespeichert. Dieser Speicherort ist relativ zum Speicherort des Bildes, unabhängig davon, ob es sich um ein interaktives Bild oder ein Karussellbanner handelt. Diese Funktion bedeutet, dass Sie dasselbe Bild zusammen mit den definierten Hotspot-Daten in beiden Viewern einfach wiederverwenden können.
Beachten Sie jedoch, dass Karussellbanner Imagemaps auf Bildern unterstützen, die auch Hotspots enthalten können. Bei interaktiven Bildern wird dies dagegen nicht unterstützt. Denken Sie daran, wenn Sie ein interaktives Bild oder ein Karussellbanner erstellen möchten, das dasselbe Bild verwendet. Sie können interaktive Bilder und Karussellbanner stattdessen mit separaten Kopien desselben Bildes erstellen.
Weitere Informationen finden Sie unter [Karussellbanner](/help/assets/dynamic-media/carousel-banners.md).

>[!NOTE]
Wenn Sie interaktive Bilder mit Hotspots bearbeiten, um das Bild zu beschneiden, werden die Hotspots entfernt.

**So fügen Sie einem Bildbanner Hotspots hinzu**

1. Navigieren Sie in der Ansicht „Assets“ zu dem Bildbanner, das interaktiv sein soll.
1. Führen Sie einen der folgenden Schritte aus:

   * Bewegen Sie den Mauszeiger über das Bild und tippen Sie auf **[!UICONTROL Auswählen]** (Häkchensymbol). Tippen Sie in der Symbolleiste auf **[!UICONTROL Bearbeiten]**.

   * Bewegen Sie den Mauszeiger über das Bild und tippen Sie dann auf **[!UICONTROL Mehr Aktionen]** (Ellipsensymbol) > **[!UICONTROL Bearbeiten]**.

   * Um es auf der Seite &quot;Detailansicht&quot;zu öffnen, tippen Sie auf das Bild. Tippen Sie in der Symbolleiste auf **[!UICONTROL Bearbeiten]**.

1. Tippen Sie oben links auf der Seite auf **[!UICONTROL Hotspot hinzufügen]** (Fingertipp-Symbol), um die Hotspot-Verwaltungsseite zu öffnen.
1. Tippen Sie in der Nähe der rechten oberen Ecke der Seite auf **[!UICONTROL Hotspot]**.

   1. Tippen Sie in der rechten oberen Ecke der Seite „Hotspot-Verwaltung“ auf **[!UICONTROL Hotspot]**.
   1. Tippen Sie im Bild auf eine Stelle, an der der Hotspot angezeigt werden soll. Ziehen Sie bei Bedarf den Hotspot, um seine Position anzupassen. Sie können auch die Pfeiltasten verwenden, um die Position eines ausgewählten Hotspots zu steuern.
   1. Fügen Sie nach Bedarf weitere Hotspots hinzu, indem Sie die Schritte a und b wiederholen.
   1. (Optional) Um einen Hotspot zu löschen, wählen Sie ihn im Bild aus und tippen Sie dann unter der Überschrift **[!UICONTROL Hotspots]** auf **[!UICONTROL Löschen]** (Papierkorbsymbol).

1. Geben Sie im Textfeld „Name“ den Namen des Hotspots ein. Dieser Name wird auch in der Dropdownliste „Ausgewählter Hotspot“ angezeigt.
1. Führen Sie einen der folgenden Schritte aus:

   * Tippen Sie auf **[!UICONTROL Schnellansicht]**.

      * Wenn Sie Experience Manager Sites oder eCommerce-Kunde sind, tippen oder klicken Sie auf das Produktauswahlsymbol (Lupe), um die Seite &quot; auswählen&quot;zu öffnen. Tippen Sie auf das Produkt, das Sie verwenden möchten, und tippen Sie dann oben rechts auf der Seite auf **Auswählen** . Sie werden zur Seite Hotspot-Verwaltung zurückgeleitet.
      * Wenn Sie *nicht* ein Experience Manager Sites- oder eCommerce-Kunde sind

         * Siehe [Ermitteln von Hotspot-Variablen](#optional-identifying-hotspot-variables); müssen Sie diese Variablen definieren.
         * Geben Sie anschließend manuell den SKU-Wert ein. Geben Sie im Textfeld SKU-Wert die SKU des Produkts ein. Der variable Teil der Schnellansichtsvorlage wird automatisch mit dem eingegebenen SKU-Wert ausgefüllt. Dadurch wird sichergestellt, dass das System den Hotspot, auf den getippt wird, mit der Schnellansicht einer bestimmten SKU verknüpfen kann.
         * (Optional) Wenn andere Variablen in der Schnellansicht vorhanden sind, die zur weiteren Identifizierung eines Produkts verwendet werden, tippen Sie auf **[!UICONTROL Generische Variable hinzufügen]**. Geben Sie im Textfeld eine zusätzliche Variable an. Beispielsweise ist `category=Mens` eine hinzugefügte Variable.
   * Tippen Sie auf **[!UICONTROL Hyperlink]**.

      * Wenn Sie Experience Manager-Sites-Kunde sind, tippen Sie auf das Symbol &quot;Site-Selektor&quot;(Ordner). Navigieren Sie zu einer URL. Die URL-basierte Verknüpfungsmethode ist nicht möglich, wenn Ihr interaktiver Inhalt über Links mit relativen URLs verfügt, insbesondere über Links zu Experience Manager-Siteseiten.
      * Wenn Sie Einzelkunde sind, geben Sie im Textfeld „HREF“ den vollständigen URL-Pfad zu einer verknüpften Web-Seite an.

   Vergessen Sie nicht anzugeben, ob der Link auf einer neuen Browser-Registerkarte (empfohlener Standard) oder auf derselben Registerkarte geöffnet werden soll.

   Weitere Informationen finden Sie unter [Arbeiten mit Selektoren](/help/assets/dynamic-media/working-with-selectors.md).

   * Tippen Sie auf **[!UICONTROL Experience Fragment]**.

      * Wenn Sie Experience Manager Sites-Kunde sind, tippen oder klicken Sie auf das Suchsymbol (Lupe), um die Seite &quot;Experience Fragment&quot;zu öffnen. Tippen Sie auf das Experience Fragment, das Sie verwenden möchten. Tippen Sie dann oben rechts auf der Seite auf **[!UICONTROL Wählen Sie]** aus. Sie werden zur Seite Hotspot-Verwaltung zurückgeleitet.
Weitere Informationen finden Sie unter [Experience Fragments](/help/sites-cloud/authoring/fundamentals/experience-fragments.md).

      * Geben Sie die Breite und Höhe des Experience Fragment so an, wie es im Banner angezeigt werden soll.

         >[!NOTE]
         Die Tools zur Freigabe in Social Media im interaktiven Bild werden nicht unterstützt, wenn Sie den Viewer in ein Experience Fragment einbetten. Verwenden oder erstellen Sie stattdessen Viewer-Vorgaben, die keine Tools zur Freigabe in Social Media haben. Mit diesen Viewer-Vorgaben können Sie sie erfolgreich in Experience Fragments einbetten.



1. Tippen Sie auf **[!UICONTROL Speichern]**, um Ihre Änderungen zu speichern, und kehren Sie zur Seite „Durchsuchen“ zurück.
1. Veröffentlichen Sie das interaktive Bild. Beim Veröffentlichen wird das Banner über die Cloud bereitgestellt und es wird auch Einbettungs-Code generiert, mit dem Sie die Integration in eine Drittanbieter-Website durchführen können.

   Siehe [Veröffentlichen von Assets](/help/assets/manage-digital-assets.md#publish-assets).

   Nachdem Sie Hotspots hinzugefügt und das interaktive Bild veröffentlicht haben, können Sie es jetzt einer vorhandenen Website hinzufügen.

   Siehe [Integrieren eines interaktiven Bildes auf Ihrer Website](#integrating-an-interactive-image-with-your-website).

   >[!NOTE]
   Wenn Sie interaktive Bilder mit Hotspots bearbeiten, um das Bild zu beschneiden, werden die Hotspots entfernt.

### (Optional) Anzeigen einer Vorschau für interaktive Bilder   {#optional-previewing-interactive-images}

Mit der Vorschau können Sie eine Darstellung anzeigen, wie Ihr interaktives Bild für Kunden angezeigt wird. Mit der Vorschau können Sie auch die Hotspots des Bildes testen, um sicherzustellen, dass sie sich wie erwartet verhalten.

Wenn das interaktive Bild Ihren Vorstellungen entspricht, können Sie es veröffentlichen.
Siehe [Einbetten des Video- oder Bild-Viewers auf einer Web-Seite](/help/assets/dynamic-media/embed-code.md).
Siehe [Verknüpfen von URLs mit einer Web-Anwendung](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md). Die URL-basierte Verknüpfungsmethode ist nicht möglich, wenn Ihr interaktiver Inhalt über Links mit relativen URLs verfügt, insbesondere über Links zu Experience Manager-Siteseiten.
Siehe [Hinzufügen von Dynamic Media-Assets zu Seiten](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md).

**So zeigen Sie eine Vorschau für interaktive Bilder an**

1. Navigieren Sie in der Ansicht „Assets“ zu einem vorhandenen interaktiven Bild, das Sie erstellt haben, um es in der Vorschau zu öffnen.
1. Tippen Sie in der Nähe der linken oberen Ecke der Seite „Vorschau“ in der Dropdown-Liste „Inhalt“ auf **[!UICONTROL Viewer]**.
1. Tippen Sie in der Liste „Viewer“ auf **[!UICONTROL Shoppable_Banner]** oder auf den Namen der von Ihnen erstellten Viewer-Vorgabe für interaktive Bilder.
1. Um die zugehörigen Aktionen von Hotspots zu testen, tippen Sie auf Hotspots auf dem Bild.

## Veröffentlichen von interaktiven Bild-Assets {#publishing-interactive-image-assets}

Weitere Informationen zum Veröffentlichen von interaktiven Bild-Assets finden Sie unter [Veröffentlichen von Assets](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

## Integrieren eines interaktiven Bildes auf Ihrer Website {#integrating-an-interactive-image-with-your-website}

Nachdem Sie ein Bannerbild hochgeladen, Hotspots hinzugefügt und das interaktive Bild veröffentlicht haben, können Sie es Ihrer Website hinzufügen.

Wenn Sie Experience Manager Sites-Kunde sind, können Sie das interaktive Bild hinzufügen, indem Sie die interaktive Medienkomponente auf Ihre Seite ziehen. Siehe [Hinzufügen von Dynamic Media-Assets zu Seiten](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md).

Wenn Sie nur Experience Manager Assets verwenden, können Sie das interaktive Bild manuell zu Ihrer Website hinzufügen, wie in diesem Abschnitt beschrieben.

1. Kopieren Sie den Einbettungs-Code des veröffentlichten interaktiven Bildes.
Siehe [Einbetten des Video- oder Bild-Viewers auf einer Web-Seite](/help/assets/dynamic-media/embed-code.md).

1. Fügen Sie den kopierten Einbettungs-Code auf dem gewünschten Bereich innerhalb der Web-Seite hinzu.
Der kopierte Einbettungscode wird für eine responsive Umgebung festgelegt, sodass er automatisch dem zugewiesenen Bereich entspricht.

**Beispiel**

Beachten Sie bei Verwendung der [Demo-Website als Beispiel](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-0.html), dass das Bild der drei Personen ein statisches `IMG`-Tag ist:

```xml
<img class="img-responsive" width="100%" title="Hero Image 2" alt="Hero Image 2" src="images/shoppable-banner.jpg">
```

Die Integration ist so einfach wie das Entfernen des `IMG`-Tags und dessen Ersetzung durch den kopierten Einbettungscode aus Experience Manager Assets. Sie können sehen, dass das Ergebnis [das interaktive Bild mit Shopping-Funktion auf der Seite mit drei Kreis-Hotspots](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-1.html) anzeigt.

>[!NOTE]
An dieser Stelle dienen die Hotspots auf dem interaktiven Bild mit Shopping-Funktion auf der Demowebsite nur zu Anzeigezwecken. Sie sind noch nicht in die vorhandenen Schnellansichten integriert.

Um einen &quot;Zuschnitt&quot;auf ein interaktives Bild mit Shopping-Funktion für eine responsive Umgebung anzuwenden, fügen Sie dem Pfad das Konfigurationsattribut für interaktive Bilder `ZoomView.iscommand` hinzu. In diesem Fall wird die Komponente `ZoomView` aufgerufen und `iscommand` ist der von Ihnen angewendete Image-Serving-Befehl &quot;Zuschneiden&quot;.

Informationen hierzu finden Sie im Thema über das Konfigurationsattribut [ZoomView.iscommand](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/command-reference-configuration-attributes-interactive-images/r-html5-aem-interactive-image-config-attrib-zoomview-iscommand.html?lang=de).

Informationen finden Sie unter [Image-Serving-Befehl](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-crop.html?lang=de).

Jetzt können Sie das interaktive Bild in eine Schnellansicht auf Ihrer Website integrieren.

## Integrieren eines interaktiven Bildes in einer vorhandenen Schnellansicht {#integrating-an-interactive-image-with-an-existing-quickview}

>[!NOTE]
Diese Aufgabe ist nur relevant, wenn Sie nur Experience Manager Assets verwenden.

Der letzte Schritt in diesem Prozess ist die Integration des interaktiven Bildes in eine vorhandene Schnellansichtsimplementierung auf Ihrer Website. Es gibt keine Lösung für die Integration, die für alle Fälle funktioniert. Jede Schnellansichtsimplementierung ist einzigartig und es ist ein spezifischer Ansatz erforderlich. Daher ist es hilfreich, die Unterstützung eines Frontend-IT-Mitarbeiters einzubeziehen.

Die vorhandene Schnellansichtsimplementierung stellt normalerweise eine Kette von untereinander verknüpften Aktionen dar, die auf der Webseite in der folgenden Reihenfolge stattfinden:

1. Ein Benutzer löst ein Element auf der Benutzeroberfläche Ihrer Website aus.
1. Der Frontend-Code ruft anhand des in Schritt 1 ausgelösten Benutzeroberflächenelements eine Schnellansichts-URL auf.
1. Der Frontend-Code sendet mithilfe der in Schritt 2 abgerufenen URL eine Ajax-Anfrage.
1. Die Backend-Logik gibt die entsprechenden Schnellansichtsdaten oder -inhalte zurück zum Frontend-Code.
1. Der Frontend-Code lädt die Schnellansichtsdaten oder -inhalte.
1. Optional wandelt der Frontend-Code die geladenen Schnellansichtsdaten in eine HTML-Darstellung um.
1. Der Frontend-Code zeigt ein modales Dialogfeld an und rendert den HTML-Inhalt auf dem Bildschirm für den Endbenutzer.

Diese Aufrufe stellen nicht unbedingt unabhängige öffentliche API-Aufrufe dar, die von der Web-Seiten-Logik aus einem beliebigen Schritt aufgerufen werden. Vielmehr handelt es sich um einen verketteten Aufruf, in dem der jeweils nächste Schritte in der letzten Phase (Callback) des vorherigen Schritts ausgeblendet ist.

Wenn das interaktive Bild mit Shopping-Funktion Schritt 1 und teilweise Schritt 2 ersetzt, tippt ein Benutzer auf einen Hotspot innerhalb des Shop-fähigen Bildes. Diese Benutzerinteraktion wird vom Viewer verarbeitet. Der Viewer gibt ein Ereignis an die Webseite zurück, das alle Hotspot-Daten enthält, die zuvor zu Experience Manager Assets hinzugefügt wurden.

In einem solchen Ereignis-Handler nimmt der Frontend-Code Folgendes vor:

* Er lauscht am Ereignis, das durch das interaktive Bild mit Shopping-Funktion ausgegeben wurde.
* Erstellt eine Schnellansichts-URL basierend auf den Hotspot-Daten.
* Trigger des Ladevorgangs der Schnellansicht vom Backend und Rendern der Schnellansicht auf dem Bildschirm zur Anzeige.

Der von Experience Manager Assets zurückgegebene Einbettungscode verfügt über einen einsatzbereiten Ereignishandler, der auskommentiert ist, wie im folgenden hervorgehobenen Codefragment zu sehen ist:

```xml
        var s7interactiveimageviewer = new s7viewers.InteractiveImage({
            "containerId" : "s7interactiveimage_div",
            "params" : {
                "serverurl" : "https://aodmarketingna.assetsadobe.com/is/image",
                "contenturl" : "https://aodmarketingna.assetsadobe.com/",
                "config" : "/etc/dam/presets/viewer/Shoppable_Media",
                "asset" : "/content/dam/mac/aodmarketingna/shoppable-banner/shoppable-banner.jpg" }
        })
        /* // Example of interactive image event for Quickview.
             s7interactiveimageviewer.setHandlers({
                "quickViewActivate": function(inData) {
                    var sku=inData.sku; //SKU for product ID
                    //To pass other parameter from the hotspot, you will need to add custom parameter during the hotspot setup as parameterName=value
                    loadQuickView(sku); //Replace this call with your Quickview plugin
                    //Please refer to your Quickviewer plugin for the Quickview call
                 },
             });
        */
        s7interactiveimageviewer.init();
```

Daher ist es nur erforderlich, die Auskommentierung des Codes aufzuheben und den Platzhalter-Handlertext durch den Code zu ersetzen, der für die bestimmte Web-Seite spezifisch ist.

Der Prozess der Erstellung der Schnellansichts-URL ist das Gegenteil des Prozesses, der zur Identifizierung der zuvor behandelten Hotspot-Variablen verwendet wurde.

Informationen hierzu finden Sie unter [Ermitteln von Hotspot-Variablen](#optional-identifying-hotspot-variables).

Anhand der vorherigen Beispiele für Schnellansichts-URLs können Sie in den folgenden Beispielen sehen, wie die Schnellansichts-URL in jedem Fall erstellt wird:

<table>
 <tbody>
  <tr>
   <td><p>Einzelne SKU, befindet sich in der Abfragezeichenfolge.</p> </td>
   <td><code class="code">s7interactiveimageviewer.setHandlers({
      "quickViewActivate": function(inData) {
      var quickViewUrl = "https://server/json?productId=" + inData.sku + "&amp;amp;source=100";
      },
      });</code></td>
  </tr>
  <tr>
   <td><p>Einzelne SKU, befindet sich im URL-Pfad.</p> </td>
   <td><code class="code">s7interactiveimageviewer.setHandlers({
      "quickViewActivate": function(inData) {
      var quickViewUrl = "https://server/product/" + inData.sku;
      },
      });</code></td>
  </tr>
  <tr>
   <td><p>SKU und Kategorie-ID in der Abfragezeichenfolge.</p> </td>
   <td><code class="code">s7interactiveimageviewer.setHandlers({
      "quickViewActivate": function(inData) {
      var quickViewUrl = "https://server/quickView/product/?category=" + inData.categoryId + "&amp;amp;prodId=" + inData.sku;
      },
      });</code></td>
  </tr>
 </tbody>
</table>

Der letzte Schritt zum Trigger der Schnellansichts-URL und zum Aktivieren des Schnellansichtsbereichs erfordert die Unterstützung eines Frontend-IT-Mitarbeiters von Ihrer Arbeit. Sie verfügen über das beste Wissen, um die Schnellansichtsimplementierung aus dem richtigen Schritt heraus korrekt Trigger, indem sie über eine einsatzbereite Schnellansichts-URL verfügen.

Sie können sehen, wie diese Schritte auf die Demowebsite angewendet werden, um ein interaktives Bild mit Shopping-Funktion vollständig in den Schnellansichtscode zu integrieren. Zuvor wurde die Struktur der Schnellansichts-URL wie folgt identifiziert:

```xml
/datafeed/$categoryId$-$SKU$.json
```

Um diese URL innerhalb des Handlers `quickViewActivate` zu rekonstruieren, können Sie die Felder `categoryId` und `SKU` verwenden. Diese Felder sind im `inData`-Objekt verfügbar, das vom Code des Viewers an den Handler übergeben wird:

```xml
var sku=inData.sku;
var categoryId=inData.categoryId;
var quickViewUrl = "datafeed/" + categoryId + "-" + sku + ".json";
```

Die Demowebsite löst das Schnellansichtsdialogfeld mit einem einfachen `loadQuickView()` -Funktionsaufruf aus. Diese Funktion akzeptiert nur ein Argument, nämlich die Schnellansichtsdaten-URL. Daher besteht der letzte Schritt bei der Integration des interaktiven Bildes mit Shopping-Funktion darin, die folgende Codezeile zum Handler `quickViewActivate` hinzuzufügen:

```xml
loadQuickView(quickViewUrl);
```

Im Folgenden finden Sie den vollständigen Quell-Code:

```xml
 var s7interactiveimageviewer = new s7viewers.InteractiveImage({
  "containerId" : "s7interactiveimage_div",
  "params" : {
   "serverurl" : "https://aodmarketingna.assetsadobe.com/is/image",
   "contenturl" : "https://aodmarketingna.assetsadobe.com/",
   "config" : "/etc/dam/presets/viewer/Shoppable_Media",
   "asset" : "/content/dam/mac/aodmarketingna/shoppable-banner/shoppable-banner.jpg" }
 })
   s7interactiveimageviewer.setHandlers({
   "quickViewActivate": function(inData) {
     var sku=inData.sku;
     var categoryId=inData.categoryId;
    var quickViewUrl = "datafeed/" + categoryId + "-" + sku + ".json";
    loadQuickView(quickViewUrl);
    },
   });
 s7interactiveimageviewer.init();
```

Die [endgültige Demo-Website mit dem vollständig integrierten interaktiven Bild](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-3.html).

## Verwenden von Schnellansichten zum Erstellen benutzerdefinierter Popups {#using-quickviews-to-create-custom-pop-ups}

Siehe [Verwenden von Schnellansichten zum Erstellen eines benutzerdefinierten Popup-Windows®](/help/assets/dynamic-media/custom-pop-ups.md).
