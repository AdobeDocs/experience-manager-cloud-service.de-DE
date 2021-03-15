---
title: Interaktive Bilder
description: Erfahren Sie, wie Sie in Dynamic Media mit interaktiven Bildern arbeiten.
translation-type: tm+mt
source-git-commit: dfd225bbef6d3244130aca2f18dbef4006f2ae65
workflow-type: tm+mt
source-wordcount: '4245'
ht-degree: 47%

---


# Interaktive Bilder {#interactive-images}

Sie können statische Bilder ganz einfach ansprechende Erlebnisse für Kunden machen, indem Sie Hotspots auf ein Bild ziehen und dort ablegen. Shoppable-Hotspots kombinieren zusätzliche Informationen über ein Produkt oder eine Dienstleistung mit einer Direktverbindung, einem Point-of-Sale &quot;Hinzufügen in den Einkaufswagen&quot; oder der Funktion &quot;Kaufen&quot;. Kunden können auf diese Hotspots tippen, die direkt auf das Produkt oder den Dienst verweisen, sie einem Warenkorb hinzufügen oder mit einer Webseite verknüpft werden. Direkte Erlebnisse wie diese erhöhen die Kundenbindung und Konversionen auf Ihrer Website.

Im Folgenden sehen Sie ein Banner mit einem Popup-Fenster für die schnelle Ansicht. Ein Benutzer aktiviert die Schnelldatei, indem er auf den Kreis oder den Hotspot im Ansicht tippt.

![chlimage_1-152](assets/chlimage_1-368.png)

Siehe [Interaktive Bilder in Aktion](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion-QVzoom/index2-shoppable.html) auf der oben abgebildeten Web-Seite.

## Sehen Sie sich an, wie interaktive Bildbanner erstellt werden {#watch-how-interactive-image-banners-are-created}

Hier erhalten Sie eine Einführung (10 Min., 33 Sek.) in die [Erstellung interaktiver Bildbanner](https://s7d5.scene7.com/s7viewers/html5/VideoViewer.html?videoserverurl=https://s7d5.scene7.com/is/content/&amp;emailurl=https://s7d5.scene7.com/s7/emailFriend&amp;serverUrl=https://s7d5.scene7.com/is/image/&amp;config=Scene7SharedAssets/Universal_HTML5_Video_social&amp;contenturl=https://s7d5.scene7.com/skins/&amp;asset=S7tutorials/InteractiveCarouselBanner). Außerdem erfahren Sie, wie interaktive Bildbanner Vorschau, bearbeitet und bereitgestellt werden.

## Schnellstart: Interaktive Bilder {#quick-start-interactive-images}

Die folgende schrittweise Workflow-Beschreibung soll Ihnen den schnellen Einstieg in die Arbeit mit interaktiven Bildern in AEM Assets ermöglichen.

Suchen Sie nach der Überschrift **Beispiele** in einigen der Schnellstartaufgaben. Hier finden Sie ein kurzes Tutorial, das auf der folgenden [Beispiel-Web-Seite basiert, der noch keine interaktiven Bilder hinzugefügt wurden](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-0.html).



Das Tutorial veranschaulicht die Schritte zur Integration von interaktiven Bildern auf Ihrer eigenen Website.

Schritte zum Erstellen interaktiver Bilder:

1. **(Optional) Ermitteln von Hotspot-Variablen**. Wenn Sie Adobe Experience Manager Assets und Dynamic Media standalone verwenden, identifizieren Sie dynamische Variablen, die in Ihrer vorhandenen Quick Ansicht-Implementierung verwendet werden. Dadurch wird sichergestellt, dass Sie beim Erstellen des interaktiven Bildes Hotspot-Daten eingeben können. Siehe [(Optional) Ermitteln von Hotspot-Variablen](#optional-identifying-hotspot-variables).
Wenn Sie jedoch AEM Sites, AEM eCommerce oder beides verwenden, ist dieser Schritt nicht erforderlich.

1. **(Optional) Erstellen einer Viewer-Vorgabe** für interaktive Bilder Passen Sie das Grafik-Bild an, das als Hotspots verwendet wird. Die Erstellung Ihrer eigenen Viewer-Vorgabe für interaktive Bilder ist nicht erforderlich, wenn Sie stattdessen die standardmäßig bereitgestellte Viewer-Vorgabe für interaktive Bilder namens `Shoppable_Banner` (Banner mit Shopping-Funktion) verwenden möchten.
Siehe [(Optional) Erstellen einer Viewer-Vorgabe für interaktive Bilder](/help/assets/dynamic-media/managing-viewer-presets.md#creating-a-new-viewer-preset).

1. **Hochladen eines Bildbanners**. Laden Sie Bildbanner hoch, die Sie interaktiv gestalten möchten. Siehe  [Hochladen eines Bildbanners](#uploading-an-image-banner).

1. **Hinzufügen von Hotspots zu einem Bildbanner**. hinzufügen einen oder mehrere Hotspots zu einem Bildbanner. Verknüpfen Sie die einzelnen Elemente mit einer Aktion wie einem Hyperlink, einer Quick-Ansicht oder einem Erlebnisfragment. Nachdem Sie Hotspots hinzugefügt haben, schließen Sie diese Aufgabe ab, indem Sie das interaktive Bild veröffentlichen.
Siehe [Hinzufügen von Hotspots zu einem Bildbanner](#adding-hotspots-to-an-image-banner).
Siehe [(Optional) Anzeigen einer Vorschau für interaktive Bilder](#optional-previewing-interactive-images). Bei Bedarf können Sie eine Darstellung des Banners mit Shopping-Funktion anzeigen und dessen Interaktivität testen.
Weitere Informationen zum Veröffentlichen von interaktiven Bild-Assets finden Sie unter [Veröffentlichen von Assets](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

1. **Hinzufügen eines interaktiven Bildes zu Ihrer Website oder Ihrer Website in Experience Manager**. Wenn Sie Sites, E-Commerce oder beides verwenden, können Sie interaktive Bilder direkt zu einer Webseite in Experience Manager hinzufügen. Ziehen Sie die Komponente Interaktive Medien auf die Seite. Siehe [Hinzufügen von Dynamic Media-Assets zu Seiten.](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md)
Wenn Sie Experience Manager Assets und Dynamic Media standalone verwenden, kopieren Sie den Einbettungscode auf Ihrer Website. Integrieren Sie es dann in Ihre vorhandene Quick-Ansicht. Siehe [Integrieren eines interaktiven Bildes auf Ihrer Website](#integrating-an-interactive-image-with-your-website).
Wenn Sie einen WCM (Web Content Manager) eines Drittanbieters verwenden, integrieren Sie das neue interaktive Video in die vorhandene Quick-Ansicht, die auf Ihrer Website verwendet wird. Siehe [Integrieren eines interaktiven Bildes in eine vorhandene Quick-Ansicht](#integrating-an-interactive-image-with-an-existing-quickview).

## (Optional) Ermitteln von Hotspot-Variablen {#optional-identifying-hotspot-variables}

>[!NOTE]
>
>Diese Aufgabe ist nur erforderlich, wenn Folgendes zutrifft:
>
>* Sie möchten Interaktivität zu Ihrem Bild hinzufügen, indem Sie Quick-Ansichten aktivieren.
>* Bei Ihrer Implementierung von Experience Manager wird *nicht* ein eCommerce-Integrationsframework verwendet, um Produktdaten aus einer beliebigen eCommerce-Lösung in den Experience Manager zu ziehen. Zu diesen Lösungen gehören IBM WebSphere® Commerce, Elastic Path, hybris oder Intershop.

>
>
Wenn Ihre AEM-Implementierung E-Commerce nutzt, können Sie diese Aufgabe überspringen und mit der nächsten Aufgabe fortfahren.

Beginn durch Identifizieren dynamischer Variablen, die von Ihrer vorhandenen Quick Ansicht-Implementierung verwendet werden, sodass Sie Hotspot-Daten eingeben können, um das interaktive Bild zu erstellen.

Wenn Sie Hotspots zu einem Bannerbild in Experience Manager Assets hinzufügen, weisen Sie eine SKU (Stock Keeping Unit) zu. Die SKU ist eine eindeutige ID für jedes einzelne Produkt oder jede Dienstleistung, die Sie Angebot haben. Fügen Sie jedem Hotspot weitere optionale Variablen hinzu. Solche Hotspot-Variablen werden später verwendet, um Hotspots mit Quick Ansicht-Inhalten abzugleichen.

Sie müssen die Anzahl und den Typ der Variablen für die Verknüpfung mit Hotspot-Daten korrekt identifizieren. Jeder dem Bannerbild hinzugefügte Hotspot muss ausreichend Informationen enthalten, um das Produkt im vorhandenen Backend-System eindeutig zu identifizieren.

Sie können ein Set aus Variablen für Hotspot-Daten auf mehrere Arten ermitteln.

Manchmal reicht es aus, sich mit IT-Spezialisten zu beraten, die für die Implementierung der Quick Ansicht zuständig sind. Diese Personen wissen wahrscheinlich, welche Daten mindestens erforderlich sind, um eine schnelle Ansicht im System zu identifizieren. Es ist jedoch auch möglich, das bestehende Verhalten des Front-End-Codes einfach zu analysieren.

Bei den meisten Implementierungen der schnellen Ansicht wird das folgende Paradigma verwendet:

* Benutzer aktiviert ein Benutzeroberflächenelement auf der Website. Klicken Sie beispielsweise auf die Schaltfläche &quot;Schnellere Ansicht&quot;.
* Die Website sendet eine Ajax-Anforderung an das Backend, um die Daten oder den Inhalt der Schnelldatei bei Bedarf zu laden.
* Die Daten zur schnellen Ansicht werden in den Inhalt übersetzt, um die Wiedergabe auf der Webseite vorzubereiten.
* Schließlich zeigt der Frontend-Code diesen Inhalt visuell auf dem Bildschirm an.

Der Ansatz besteht dann darin, verschiedene Bereiche der bestehenden Website zu besuchen, in denen die Schnellfunktion zur Ansicht implementiert ist. Trigger dann die Quick-Ansicht und erfassen Sie die Ajax-URL, die von einer Webseite zum Laden der Quick-Ansicht-Daten oder -Inhalte gesendet wird.

Normalerweise müssen Sie keine speziellen Debugging-Tools verwenden. Moderne Webbrowser verfügen über Web-Inspektoren, die dafür ausreichend sind. Die folgenden Webbrowser beispielsweise umfassen Web-Inspektoren:

* Um alle ausgehenden HTTP-Anfragen in Google Chrome anzuzeigen, drücken Sie F12, um den Bereich für Entwickler-Tools zu öffnen; klicken Sie dann auf die Registerkarte „Netzwerk“.
Drücken Sie bei einem Mac Befehlstaste+Wahltaste+I, um den Bereich für Entwickler-Tools zu öffnen, und klicken Sie dann auf die Registerkarte „Netzwerk“.

* In Firefox können Sie das Firebug-Plugin aktivieren, indem Sie F12 drücken und die Registerkarte &quot;Net&quot;verwenden. Sie können auch das integrierte Inspektor-Tool und dessen Registerkarte &quot;Netzwerk&quot;verwenden.
Drücken Sie bei einem Mac Befehlstaste+Wahltaste+I, um den Bereich für Entwickler-Tools zu öffnen, und klicken Sie dann auf die Registerkarte „Inspektor“.

Wenn die Netzwerküberwachung im Browser aktiviert ist, Trigger die Schnellseite der Ansicht.

Suchen Sie nun die Ajax-URL der Schnellversion im Netzwerkprotokoll und kopieren Sie die aufgezeichnete URL für die zukünftige Analyse. Normalerweise werden beim Trigger der Quick-Ansicht zahlreiche Anfragen an den Server gesendet. Normalerweise ist die Ajax-URL für die schnelle Ansicht eine der ersten in der Liste. Sie weist einen Teil oder Pfad mit einer komplexen Abfragezeichenfolge auf und ihr MIME-Typ lautet entweder `text/xml`, `text/html` oder `text/javascript`.

Dabei ist es wichtig, verschiedene Bereiche Ihrer Website mit unterschiedlichen Kategorien und Typen zu besuchen. Der Grund dafür ist, dass Quick Ansicht-URLs Teile enthalten können, die für eine bestimmte Website-Kategorie häufig verwendet werden. Sie ändern sich jedoch nur, wenn Sie einen anderen Bereich der Website besuchen.

Im einfachsten Fall ist die Produkt-SKU der einzige Variablenteil in der Quick Ansicht-URL. In diesem Fall ist der SKU-Wert das einzige Datenelement, das Sie zum Hinzufügen von Hotspots zum Bannerbild benötigen.

In komplexen Fällen enthält die URL der Schnellkorrektur jedoch zusätzlich zur SKU verschiedene Variablenelemente. Variierende Elemente können beispielsweise Kategorien-ID, Farbcode und Größencode enthalten. In solchen Fällen ist jedes Element eine separate Variable in Ihrer Hotspot-Datendefinition in der interaktiven Bildfunktion in Experience Manager Assets.

Betrachten Sie die folgenden Beispiele für URLs zur schnellen Ansicht und die sich daraus ergebenden Hotspot-Variablen:

<table>
  <tbody>
  <tr>
    <td><p>Einzelne SKU, befindet sich in der Abfragezeichenfolge.</p> </td>
    <td><p>Zu den aufgezeichneten URLs für die schnelle Ansicht gehören:</p>
    <ul>
      <li><p><code>https://server/json?productId=866558&amp;source=100</code></p> </li>
      <li><p><code>https://server/json?productId=1196184&amp;source=100</code></p> </li>
      <li><p><code>https://server/json?productId=1081492&amp;source=100</code></p> </li>
      <li><p><code>https://server/json?productId=1898294&amp;source=100</code></p> </li>
    </ul> <p>Der einzige variable Teil der URL ist der Wert des Abfrageparameters „productId=“ und ist offensichtlich ein SKU-Wert. Daher benötigen die Hotspots nur SKU-Felder mit Werten wie <strong><code>866558</code></strong>, <strong><code>1196184</code></strong>, <strong><code>1081492</code></strong>, <strong><code>1898294</code></strong>.</p> </td>
  </tr>
  <tr>
    <td><p>Einzelne SKU, befindet sich im URL-Pfad.</p> </td>
    <td><p>Zu den aufgezeichneten URLs für die schnelle Ansicht gehören:</p>
    <ul>
      <li><p><code>https://server/product/6422350843</code></p> </li>
      <li><p><code>https://server/product/1607745002</code></p> </li>
      <li><p><code>https://server/product/0086724882</code></p> </li>
    </ul> <p>Der variable Teil befindet sich im letzten Abschnitt des Pfads und wird zum SKU-Wert der Hotspots: <strong><code>6422350843</code></strong>, <strong><code>1607745002</code></strong>, <strong><code>0086724882</code></strong>.</p> </td>
  </tr>
  <tr>
    <td><p>SKU und Kategorie-ID in der Abfragezeichenfolge.</p> </td>
    <td><p>Zu den aufgezeichneten URLs für die schnelle Ansicht gehören:</p>
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

Die Demo-Webseite enthält mehrere Produktminiaturen, von denen jede über eine Schaltfläche für die schnelle Ansicht mit der Bezeichnung &quot;Weitere Informationen&quot;verfügt. Wenn das Debugging-Tool Ihres Webbrowsers noch aktiviert ist, klicken Sie auf jede Schaltfläche und notieren Sie sich die aufgezeichneten Quick Ansicht-URLs. Nachdem Sie alle vier Quick-Ansichten aktiviert haben, die auf der Seite verfügbar sind, haben Sie die folgende Liste von Anfragen zur schnellen Ansicht an das Backend:

* `/datafeed/Men-Windbreaker.json`
* `/datafeed/Men-SimpleHenley.json`
* `/datafeed/Men-CamoPullover.json`
* `/datafeed/Women-QuiltedDownJacket.json`

Wenn Sie sich die Server-Aufrufe ansehen, können Sie sehen, dass produktspezifische Informationen nur im Anforderungspfad vorhanden sind. Beachten Sie außerdem, dass die Abfragezeichenfolge überhaupt nicht verwendet wird und zwei unterschiedliche Typen von Datenteilen beteiligt sind:

* Der erste Typ ist „Männer“ oder „Frauen“. Dies kann als „Produktkategorie“ bezeichnet werden.
* Der zweite Typ ist der Produktname, z. B. CamoPullover, bei dem es sich wahrscheinlich um die Produkt-SKU handelt.

Aufgrund dieser Informationen hat die gesamte URL der Schnellkorrektur das folgende Muster:

`/datafeed/$categoryId$-$SKU$.json`

Auf Grundlage einer solchen Analyse würden Sie `categoryId` und `SKU` für Hotspots verwenden.

Jetzt können Sie ein Bildbanner hochladen und diesem Hotspots mit der Funktion für interaktive Bilder mit Shopping-Funktion in AEM Assets hinzufügen.

## (Optional) Erstellen einer Viewer-Vorgabe für interaktive Bilder  {#optional-creating-an-interactive-image-viewer-preset}

Sie können die standardmäßige Viewer-Vorgabe für interaktive Bilder mit dem Namen `Shoppable_Banner` verwenden, die in AEM Assets integriert ist. Sie können auch eine eigene benutzerdefinierte Viewer-Vorgabe für interaktive Bilder erstellen.

Wenn Sie eine benutzerdefinierte Viewer-Vorgabe für interaktive Bilder erstellen, können Sie das Erscheinungsbild von Hotspots auf dem Bildbanner bestimmen. Bei der Erstellung der Viewer-Vorgabe können Sie eine Hotspot-Grafik aus einer Galerie mit vordefinierten Bildern verwenden.

Nachdem Sie die Viewer-Vorgabe gespeichert haben, wird sie automatisch auf der Seite mit der Liste der „Viewer-Vorgaben“ in AEM Assets aktiviert (eingeschaltet). Diese Funktionalität bedeutet, dass sie in der interaktiven Medienkomponente sowie dann sichtbar ist, wenn Sie ein Asset anzeigen. Um *jedoch ein interaktives Banner mit dieser Viewer-Vorgabe bereitzustellen,* veröffentlichen *auch Ihre Viewer-Vorgabe.* Diese Regel gilt für benutzerdefinierte oder vordefinierte Viewer-Vorgaben.

**So erstellen Sie eine Viewer-Vorgabe für interaktive Bilder**

1. Tippen Sie links in der Leiste auf **[!UICONTROL Tools > Assets > Viewer-Vorgaben]**.
1. Tippen Sie in der Nähe der rechten oberen Ecke der Seite auf **[!UICONTROL Erstellen]**.
1. Geben Sie im Dialogfeld „Neue Viewer-Vorgabe“ einen Namen ein, um die Viewer-Vorgabe für interaktive Banner zu beschreiben.

   Dieser Titel wird nach dem Speichern in der Liste &quot;Viewer-Vorgaben&quot;angezeigt.

1. Wählen Sie im Pulldown-Menü „Rich-Media-Typ“ die Option **[!UICONTROL Interaktives Bild]** aus.
1. Tippen Sie auf **[!UICONTROL Erstellen]**.
1. Tippen Sie auf der Seite „Viewer-Vorgabe bearbeiten“ auf die Registerkarte **[!UICONTROL Erscheinungsbild]**.
1. Führen Sie einen der folgenden Schritte aus:

   * Um ein eigenes Hotspot-Bild hochzuladen, das Sie für Bilder verwenden möchten, tippen Sie auf das Symbol für die Asset-Auswahl. Navigieren Sie auf der Seite &quot;Inhalt auswählen&quot;zum gewünschten Hotspot-Bild und wählen Sie es aus. Tippen Sie oben rechts auf das Häkchen-Symbol.
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

Wenn Sie Hotspots hinzufügen, können Sie sie als Popup-Ansicht, als Hyperlink oder als Erlebnisfragment definieren.

Weitere Informationen finden Sie unter [Experience Fragments](/help/sites-cloud/authoring/fundamentals/experience-fragments.md).

>[!NOTE]
>
>Die Werkzeuge zum Freigeben von sozialen Medien in interaktivem Bild werden nicht unterstützt, wenn Sie den Viewer in ein Erlebnisfragment einbetten. Verwenden oder erstellen Sie stattdessen Viewer-Vorgaben, die keine Social Media Sharing-Werkzeuge haben. Mit diesen Viewer-Vorgaben können Sie sie erfolgreich in Experience Fragments einbetten.

Die Optionen „Rückgängig“ und „Wiederholen“ in der Nähe der oberen rechten Ecke der Seite werden während der aktuellen Erstellungs-/Bearbeitungssitzung unterstützt.

Wenn Sie mit der Erstellung des interaktiven Bildes fertig sind, können Sie mit der Vorschau eine Darstellung der Darstellung des interaktiven Bildes für Ihre Kunden anzeigen.

Siehe [(Optional) Anzeigen einer Vorschau für interaktive Bilder](#optional-previewing-interactive-images).

>[!NOTE]
>
>Wenn Sie einem Bild in einem interaktiven Bild oder einem Karussell-Banner Hotspots hinzufügen, werden die Hotspot-Informationen am selben Metadatenspeicherort gespeichert. Diese Position ist relativ zur Position des Bildes, unabhängig davon, ob es sich um ein interaktives Bild oder ein Karussell-Banner handelt. Dank dieser Funktion können Sie dasselbe Bild - zusammen mit den definierten Hotspot-Daten - in beiden Viewern problemlos wiederverwenden.
Beachten Sie jedoch, dass Karussellbanner Imagemaps auf Bildern unterstützen, die auch Hotspots enthalten können. Bei interaktiven Bildern wird dies dagegen nicht unterstützt. Denken Sie daran, wenn Sie ein interaktives Bild oder ein Karussell-Banner erstellen möchten, das dasselbe Bild verwendet. Sie können interaktive Bilder und Karussell-Banner stattdessen mit separaten Kopien desselben Bildes erstellen.
Weitere Informationen finden Sie unter [Karussellbanner](/help/assets/dynamic-media/carousel-banners.md).

>[!NOTE]
Wenn Sie interaktive Bilder mit Hotspots bearbeiten, um das Bild zu beschneiden, werden die Hotspots entfernt.

**So fügen Sie einem Bildbanner Hotspots hinzu**

1. Navigieren Sie in der Ansicht „Assets“ zu dem Bildbanner, das interaktiv sein soll.
1. Führen Sie einen der folgenden Schritte aus:

   * Bewegen Sie den Mauszeiger über das Bild und tippen Sie auf **[!UICONTROL Auswählen]** (Häkchensymbol). Tippen Sie in der Symbolleiste auf **[!UICONTROL Bearbeiten]**.

   * Bewegen Sie den Mauszeiger über das Bild und tippen Sie dann auf **[!UICONTROL Mehr Aktionen]** (Ellipsensymbol) > **[!UICONTROL Bearbeiten]**.

   * Um das Bild auf der Seite &quot;Ansicht der Details&quot;zu öffnen, tippen Sie auf das Bild. Tippen Sie in der Symbolleiste auf **[!UICONTROL Bearbeiten]**.

1. Tippen Sie oben links auf der Seite auf **[!UICONTROL Hotspot hinzufügen]** (Fingertipp-Symbol), um die Hotspot-Verwaltungsseite zu öffnen.
1. Tippen Sie in der Nähe der rechten oberen Ecke der Seite auf **[!UICONTROL Hotspot]**.

   1. Tippen Sie in der rechten oberen Ecke der Seite „Hotspot-Verwaltung“ auf **[!UICONTROL Hotspot]**.
   1. Tippen Sie im Bild auf eine Stelle, an der der Hotspot angezeigt werden soll. Ziehen Sie bei Bedarf den Hotspot, um seine Position anzupassen. Sie können auch die Pfeiltasten verwenden, um die Position eines ausgewählten Hotspots zu steuern.
   1. hinzufügen Sie nach Bedarf weitere Hotspots, indem Sie die Schritte a und b wiederholen.
   1. (Optional) Um einen Hotspot zu löschen, wählen Sie ihn im Bild aus und tippen Sie dann unter der Überschrift **[!UICONTROL Hotspots]** auf **[!UICONTROL Löschen]** (Papierkorbsymbol).

1. Geben Sie im Textfeld „Name“ den Namen des Hotspots ein. Dieser Name wird auch in der Dropdownliste „Ausgewählter Hotspot“ angezeigt.
1. Führen Sie einen der folgenden Schritte aus:

   * Tippen Sie auf **[!UICONTROL Schnellere Ansicht]**.

      * Wenn Sie AEM Sites- oder eCommerce-Kunde sind, tippen oder klicken Sie auf das Produktauswahlsymbol (Lupe), um die Seite „Produkt wählen“ zu öffnen. Tippen Sie auf das gewünschte Produkt und dann auf **Wählen Sie** in der oberen rechten Ecke der Seite. Sie werden zur Hotspot-Verwaltungsseite zurückgeleitet.
      * Wenn Sie *keinen* Experience Manager-Sites oder E-Commerce-Kunden sind

         * Siehe [Identifizieren von Hotspot-Variablen](#optional-identifying-hotspot-variables); Sie müssen diese Variablen definieren.
         * Geben Sie anschließend manuell den SKU-Wert ein. Geben Sie im Textfeld SKU-Wert die SKU des Produkts ein. Der eingegebene SKU-Wert füllt automatisch den Variablenteil der Quick Ansicht-Vorlage aus. Dadurch wird sichergestellt, dass das System den getippten Hotspot mit der Quick-Ansicht einer bestimmten SKU verknüpfen kann.
         * (Optional) Wenn es andere Variablen in der Quick-Ansicht gibt, die zur weiteren Identifizierung eines Produkts verwendet werden, tippen Sie auf **[!UICONTROL Hinzufügen Generische Variable]**. Geben Sie im Textfeld eine zusätzliche Variable an. Beispielsweise ist `category=Mens` eine hinzugefügte Variable.
   * Tippen Sie auf **[!UICONTROL Hyperlink]**.

      * Wenn Sie Experience Manager-Sites-Kunde sind, tippen Sie auf das Symbol &quot;Site-Selektor&quot;(Ordner). Navigieren Sie zu einer URL. Die URL-basierte Linkmethode ist nicht möglich, wenn der interaktive Inhalt Links mit relativen URLs, insbesondere Links zu Experience Manager-Siteseiten, enthält.
      * Wenn Sie Einzelkunde sind, geben Sie im Textfeld „HREF“ den vollständigen URL-Pfad zu einer verknüpften Web-Seite an.

   Vergessen Sie nicht anzugeben, ob der Link auf einer neuen Browser-Registerkarte (empfohlener Standard) oder auf derselben Registerkarte geöffnet werden soll.

   Weitere Informationen finden Sie unter [Arbeiten mit Selektoren](/help/assets/dynamic-media/working-with-selectors.md).

   * Tippen Sie auf **[!UICONTROL Experience Fragment]**.

      * Wenn Sie AEM Sites-Kunde sind, tippen oder klicken Sie auf das Suchsymbol (Lupe), um die Seite „Experience Fragment“ zu öffnen. Tippen Sie auf das Erlebnisfragment, das Sie verwenden möchten. Tippen Sie dann auf **[!UICONTROL Select]** in der oberen rechten Ecke der Seite. Sie werden zur Hotspot-Verwaltungsseite zurückgeleitet.
Weitere Informationen finden Sie unter [Experience Fragments](/help/sites-cloud/authoring/fundamentals/experience-fragments.md).

      * Geben Sie die Breite und Höhe des Erlebnisfragments so an, wie sie auf dem Banner angezeigt werden sollen.

         >[!NOTE]
         Die Werkzeuge zum Freigeben von sozialen Medien in interaktivem Bild werden nicht unterstützt, wenn Sie den Viewer in ein Erlebnisfragment einbetten. Verwenden oder erstellen Sie stattdessen Viewer-Vorgaben, die keine Social Media Sharing-Werkzeuge haben. Mit diesen Viewer-Vorgaben können Sie sie erfolgreich in Experience Fragments einbetten.



1. Tippen Sie auf **[!UICONTROL Speichern]**, um Ihre Änderungen zu speichern, und kehren Sie zur Seite „Durchsuchen“ zurück.
1. Veröffentlichen Sie das interaktive Bild. Beim Veröffentlichen wird das Banner über die Cloud bereitgestellt und es wird auch Einbettungscode generiert, mit dem Sie sich in eine Website eines Drittanbieters integrieren können.

   Siehe [Veröffentlichen von Assets](/help/assets/manage-digital-assets.md#publish-assets).

   Nachdem Sie Hotspots hinzugefügt und das interaktive Bild veröffentlicht haben, können Sie es jetzt einer vorhandenen Website hinzufügen.

   Siehe [Integrieren eines interaktiven Bildes auf Ihrer Website](#integrating-an-interactive-image-with-your-website).

   >[!NOTE]
   Wenn Sie interaktive Bilder mit Hotspots bearbeiten, um das Bild zu beschneiden, werden die Hotspots entfernt.

### (Optional) Anzeigen einer Vorschau für interaktive Bilder   {#optional-previewing-interactive-images}

Sie können Vorschau verwenden, um eine Darstellung des Erscheinungsbilds Ihres interaktiven Bildes zu sehen. Mit der Vorschau können Sie auch die Hotspots des Bildes testen, um sicherzustellen, dass sie sich wie erwartet verhalten.

Wenn das interaktive Bild Ihren Vorstellungen entspricht, können Sie es veröffentlichen.
Siehe [Einbetten des Video- oder Bild-Viewers auf einer Web-Seite](/help/assets/dynamic-media/embed-code.md).
Siehe [Verknüpfen von URLs mit einer Web-Anwendung](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md). Die URL-basierte Verknüpfungsmethode ist nicht möglich, wenn Ihr interaktiver Inhalt über Links mit relativen URLs verfügt, insbesondere über Links zu Seiten in AEM Sites.
Siehe [Hinzufügen von Dynamic Media-Assets zu Seiten](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md).

**So zeigen Sie eine Vorschau für interaktive Bilder an**

1. Navigieren Sie in der Ansicht „Assets“ zu einem vorhandenen interaktiven Bild, das Sie erstellt haben, um es in der Vorschau zu öffnen.
1. Tippen Sie in der Nähe der linken oberen Ecke der Seite „Vorschau“ in der Dropdown-Liste „Inhalt“ auf **[!UICONTROL Viewer]**.
1. Tippen Sie in der Liste „Viewer“ auf **[!UICONTROL Shoppable_Banner]** oder auf den Namen der von Ihnen erstellten Viewer-Vorgabe für interaktive Bilder.
1. Um die zugehörigen Aktionen von Hotspots zu testen, tippen Sie auf Hotspots im Bild.

## Veröffentlichen von interaktiven Bild-Assets {#publishing-interactive-image-assets}

Weitere Informationen zum Veröffentlichen von interaktiven Bild-Assets finden Sie unter [Veröffentlichen von Assets](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

## Integrieren eines interaktiven Bildes auf Ihrer Website {#integrating-an-interactive-image-with-your-website}

Nachdem Sie ein Bannerbild hochgeladen, Hotspots hinzugefügt und das interaktive Bild veröffentlicht haben, können Sie es Ihrer Webseite hinzufügen.

Wenn Sie AEM Sites-Kunde sind, können Sie das interaktive Bild hinzufügen, indem Sie die interaktive Medienkomponente auf Ihre Seite ziehen. Siehe [Hinzufügen von Dynamic Media-Assets zu Seiten](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md).

Wenn Sie nur AEM Assets verwenden, können Sie das interaktive Bild Ihrer Website manuell hinzufügen, wie in diesem Abschnitt beschrieben.

1. Kopieren Sie den Einbettungs-Code des veröffentlichten interaktiven Bildes.
Siehe [Einbetten des Video- oder Bild-Viewers auf einer Web-Seite](/help/assets/dynamic-media/embed-code.md).

1. Fügen Sie den kopierten Einbettungs-Code auf dem gewünschten Bereich innerhalb der Web-Seite hinzu.
Der kopierte Einbettungscode wird für eine responsive Umgebung eingestellt, damit er automatisch in den zugewiesenen Bereich passt.

**Beispiel**

Beachten Sie, dass die [demo-Website als Beispiel](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-0.html) das Bild der drei Personen ein statisches `IMG`-Tag ist:

```xml
<img class="img-responsive" width="100%" title="Hero Image 2" alt="Hero Image 2" src="images/shoppable-banner.jpg">
```

Die Integration ist so einfach wie das Entfernen des `IMG`-Tags und dessen entsprechende Ersetzung durch den kopierten Integrations-Code aus AEM Assets. Sie können sehen, dass das Ergebnis [das einkaufbare interaktive Bild auf der Seite mit drei kreisförmigen Hotspots](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-1.html) zeigt.

>[!NOTE]
Die Hotspots auf dem interaktiven Bild der Demo-Website dienen daher nur zur Anzeige. Sie sind noch nicht in die Quick-Ansichten integriert.

Um ein &quot;Beschneiden&quot;auf ein interaktives Bild für eine interaktive Umgebung anzuwenden, fügen Sie dem Pfad das Konfigurationsattribut Interaktives Bild `ZoomView.iscommand` hinzu. In diesem Fall wird die Komponente `ZoomView` aufgerufen und `iscommand` ist der Befehl zum Entfernen von Bildern, den Sie anwenden.

Informationen hierzu finden Sie im Thema über das Konfigurationsattribut [ZoomView.iscommand](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/command-reference-configuration-attributes-interactive-images/r-html5-aem-interactive-image-config-attrib-zoomview-iscommand.html?lang=de).

Informationen finden Sie unter [Image-Serving-Befehl](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-crop.html?lang=de).

Sie können das interaktive Bild jetzt mit einer vorhandenen Quick-Ansicht auf Ihrer Website integrieren.

## Interaktives Bild mit einer vorhandenen Quick-Ansicht {#integrating-an-interactive-image-with-an-existing-quickview} integrieren

>[!NOTE]
Diese Aufgabe ist nur relevant, wenn Sie die Standalone-Version von AEM Assets verwenden.

Der letzte Schritt in diesem Prozess ist die Integration des interaktiven Bildes in eine vorhandene Quick Ansicht-Implementierung auf Ihrer Website. Es gibt keine Lösung für die Integration, die für alle Fälle funktioniert. Jede Implementierung der Schnellfunktion ist eindeutig und erfordert einen spezifischen Ansatz. Daher ist es hilfreich, die Unterstützung durch eine IT-Mitarbeiterin am Front-End einzubeziehen.

Die vorhandene Quick-Ansicht-Implementierung stellt normalerweise eine Kette miteinander verknüpfter Aktionen dar, die auf der Webseite in der folgenden Reihenfolge ausgeführt werden:

1. Ein Benutzer löst ein Element auf der Benutzeroberfläche Ihrer Website aus.
1. Der Front-End-Code ruft eine URL für die schnelle Ansicht basierend auf dem Element der Benutzeroberfläche ab, das in Schritt 1 ausgelöst wurde.
1. Der Frontend-Code sendet mithilfe der in Schritt 2 abgerufenen URL eine Ajax-Anfrage.
1. Die Backend-Logik gibt die entsprechenden Quick-Ansicht-Daten oder -Inhalte zurück zum Front-End-Code.
1. Der Front-End-Code lädt die Daten oder den Inhalt der Quick-Ansicht.
1. Optional konvertiert der Front-End-Code die geladenen Quick-Ansicht-Daten in eine HTML-Darstellung.
1. Der Frontend-Code zeigt ein modales Dialogfeld an und rendert den HTML-Inhalt auf dem Bildschirm für den Endbenutzer.

Diese Aufrufe stellen nicht unbedingt unabhängige öffentliche API-Aufrufe dar, die von der Webseitenlogik aus einem beliebigen Schritt aufgerufen werden. Vielmehr handelt es sich um einen verketteten Aufruf, in dem der jeweils nächste Schritte in der letzten Phase (Callback) des vorherigen Schritts ausgeblendet ist.

Wenn das interaktive Bild Schritt 1 und teilweise Schritt 2 ersetzt, tippt ein Benutzer auf einen Hotspot im kaufbaren Bild. Diese Benutzerinteraktion wird vom Viewer verarbeitet. Der Viewer gibt der Web-Seite ein Ereignis zurück, das alle zuvor zu AEM Assets hinzugefügten Hotspot-Daten aufweist.

In einem solchen Ereignis-Handler nimmt der Frontend-Code Folgendes vor:

* Er lauscht am Ereignis, das durch das interaktive Bild mit Shopping-Funktion ausgegeben wurde.
* Erstellt eine URL für die schnelle Ansicht basierend auf den Hotspot-Daten.
* Trigger des Ladevorgangs der Quick-Ansicht vom Backend und der Wiedergabe auf dem Bildschirm zur Anzeige.

Der von Experience Manager Assets zurückgegebene Einbettungscode verfügt über einen einsatzbereiten Ereignis-Handler, der auskommentiert wird, wie im folgenden hervorgehobenen Codefragment dargestellt:

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

Die Erstellung der URL für die schnelle Ansicht erfolgt anders als bei der Identifizierung der zuvor behandelten Hotspot-Variablen.

Informationen hierzu finden Sie unter [Ermitteln von Hotspot-Variablen](#optional-identifying-hotspot-variables).

Anhand der vorherigen URL-Beispiele für die Schnellere Ansicht können Sie in den folgenden Beispielen sehen, wie die URL für die schnelle Ansicht in jedem Fall aufgebaut wird:

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

Der letzte Schritt zum Trigger der URL für die schnelle Ansicht und zur Aktivierung des Bedienfelds für die schnelle Ansicht erfordert die Unterstützung eines IT-Mitarbeiters in Ihrem Unternehmen. Sie verfügen über die nötigen Kenntnisse, um die Implementierung der Quick-Ansicht mit einer benutzerfreundlichen URL für die schnelle Ansicht vom richtigen Schritt aus genau Trigger.

Sie können sehen, wie diese Schritte auf die Demo-Website angewendet werden, um ein einkaufbares interaktives Bild vollständig in den Quick Ansicht-Code zu integrieren. Zuvor wurde die Struktur der URL für die schnelle Ansicht wie folgt identifiziert:

```xml
/datafeed/$categoryId$-$SKU$.json
```

Um diese URL im `quickViewActivate`-Handler zu rekonstruieren, können Sie die Felder `categoryId` und `SKU` verwenden. Diese Felder sind im `inData`-Objekt verfügbar, das vom Code des Viewers an den Handler übergeben wird:

```xml
var sku=inData.sku;
var categoryId=inData.categoryId;
var quickViewUrl = "datafeed/" + categoryId + "-" + sku + ".json";
```

Die Demo-Website löst das Dialogfeld &quot;Schnellere Ansicht&quot;mit einem einfachen Funktionsaufruf aus. `loadQuickView()` Diese Funktion akzeptiert nur ein Argument, nämlich die Daten-URL der Quick Ansicht. Daher ist der letzte Schritt zur Integration des interaktiven Bilds, die folgende Codezeile zum `quickViewActivate`-Handler hinzuzufügen:

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

## Verwenden von Quick-Ansichten zum Erstellen benutzerdefinierter Popups {#using-quickviews-to-create-custom-pop-ups}

Siehe [Verwenden von Quick-Ansichten zum Erstellen benutzerdefinierter Popup-Fenster](/help/assets/dynamic-media/custom-pop-ups.md).
