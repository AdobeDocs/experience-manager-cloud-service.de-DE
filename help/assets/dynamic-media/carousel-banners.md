---
title: Karussellbanner
description: Informationen zum Arbeiten mit Karussellbannern in Dynamic Media.
translation-type: tm+mt
source-git-commit: f5627a6e885a556700fbf56c4c63f0f4d6a89da0
workflow-type: tm+mt
source-wordcount: '4576'
ht-degree: 50%

---


# Karussellbanner {#carousel-banners}

Mit Karussellbannern können Marketingexperten die Konversionsrate steigern, indem sie auf einfache Art Drehbanner mit Promo-Inhalten erstellen, die auf beliebigen Bildschirmen bereitgestellt werden können.

Das Erstellen und Ändern von Inhalten auf Werbebannern kann zeitaufwendig sein und Ihre Fähigkeit beeinträchtigen, neue Inhalte schnell zu veröffentlichen oder zielgerichteter zu gestalten. Karussell-Banner ermöglichen Ihnen das schnelle Erstellen oder Ändern rotierender Banner und das Hinzufügen von Interaktivität wie Hotspot-Verknüpfungen zu Produktdetails oder verwandten Ressourcen. Sie können sie für jeden Bildschirm bereitstellen und so neue Werbeinhalte schneller auf den Markt bringen.

Karussellbanner sind Banner, die durch die Bezeichnung **[!UICONTROL CAROUSELSET]** gekennzeichnet sind:

![chlimage_1-438](assets/chlimage_1-438.png)

Auf Ihrer Website kann ein Karussellbanner wie folgt aussehen:

![chlimage_1-439](assets/chlimage_1-439.png)

Hier können Sie durch die Bilder navigieren, indem Sie auf die Zahlen klicken. Zusätzlich drehen sich die Folien automatisch basierend auf einem Intervall, das Sie anpassen können. Bilder, die Sie im Karussell-Banner hinzufügen, unterstützen sowohl Hotspots als auch Imagemaps. Die Benutzer können entweder auf einen Hyperlink tippen, zu einem Hyperlink wechseln oder auf ein Quick Ansicht-Fenster zugreifen.

In diesem Beispiel hat ein Benutzer auf eine Imagemap getippt oder geklickt und für Handschuhe auf das Fenster &quot;Schnelle Ansicht&quot;zugegriffen:

![chlimage_1-440](assets/chlimage_1-440.png)

## Video zur Erstellung von Karussellbannern {#watch-how-carousel-banners-are-created}

Sehen Sie sich eine exemplarische Vorgehensweise (10 Minuten und 33 Sekunden) zur [Erstellung von Karussellbannern](https://s7d5.scene7.com/s7viewers/html5/VideoViewer.html?videoserverurl=https://s7d5.scene7.com/is/content/&amp;emailurl=https://s7d5.scene7.com/s7/emailFriend&amp;serverUrl=https://s7d5.scene7.com/is/image/&amp;config=Scene7SharedAssets/Universal_HTML5_Video_social&amp;contenturl=https://s7d5.scene7.com/skins/&amp;asset=S7tutorials/InteractiveCarouselBanner) an. Außerdem erfahren Sie, wie Karussell-Banner Vorschau, bearbeitet und bereitgestellt werden.

>[!NOTE]
>
>Benutzer, die keine Administratoren sind, müssen der Gruppe **[!UICONTROL dam-users]** hinzugefügt werden, damit sie Karussellbanner erstellen oder bearbeiten können. Wenn Sie Probleme beim Erstellen oder Bearbeiten haben, wenden Sie sich an Ihren Systemadministrator, der Sie zur Gruppe **d[!UICONTROL am-users]** hinzufügen kann.

## Schnellstart: Karussellbanner {#quick-start-carousel-banners}

So schaffen Sie einen schnellen Einstieg:

1. [Identifizieren Sie Hotspot- und Imagemap-Variablen](#identifying-hotspot-and-image-map-variables)  (nur für Kunden, die Adobe Experience Manager Assets + Dynamic Media verwenden).

   Beginn durch Identifizieren der dynamischen Variablen, die von der vorhandenen Quick Ansicht-Implementierung verwendet werden. Auf diese Weise können Sie Hotspots und Imagemap-Daten während der Erstellung von Karussellbannern in Experience Manager Assets ordnungsgemäß eingeben.

<!-- LEAVE; COMMERCE BEING ADDED AGAIN IN THE FUTURE

   >[!NOTE]
   >
   >If you are an AEM Sites or Ecommerce customer, you can use the built-in feature to navigate to product pages and lookup the existing skus in the product catalog. You do not need to manually enter hotspot or image map variables.
   >
   >
   >If you are an AEM Assets and Dynamic Media customer, you will manually enter data for hotspots and image maps, and then integrate the published URL or Embed code with your third-party content management system.

-->

1. Optional: [Erstellen Sie eine Viewer-Vorgabe für Karussellsets](/help/assets/dynamic-media/managing-viewer-presets.md) bei Bedarf.

   Wenn Sie ein Administrator sind, können Sie das Verhalten und das Erscheinungsbild des Karussells anpassen, indem Sie eine eigene Karussell-Viewer-Vorgabe erstellen. Der Hauptvorteil besteht darin, dass Sie diese benutzerdefinierte Viewer-Vorgabe für mehrere Karussells wiederverwenden können. Benutzer können das Verhalten und Erscheinungsbild des Karussells jedoch optional direkt beim Authoring des Karussells anpassen. Dieser Ansatz wird bevorzugt, wenn Sie ein bestimmtes Design für ein bestimmtes Karussell wünschen.

1. [Laden Sie ein Bildbanner hoch](#uploading-image-banners).

   Laden Sie Bildbanner hoch, die interaktiv sein sollen.

1. [Erstellen Sie ein Karussellset](#creating-carousel-sets).

   In Karussellsets navigieren Benutzer durch Bannerbilder und tippen auf Hotspots oder Imagemaps, um auf relevante Inhalte zuzugreifen.

   Um ein Karussellset in Assets zu erstellen, tippen Sie auf **[!UICONTROL Erstellen]** und wählen Sie dann **[!UICONTROL Karussellsets]**. Fügen Sie den Folien dann Assets hinzu und tippen Sie auf **[!UICONTROL Speichern]**. Sie können das Erscheinungsbild und Verhalten des Karussells auch direkt im Editor bearbeiten.

1. [Fügen Sie Hotspots oder Imagemaps in einem Bildbanner hinzu.](#adding-hotspots-or-image-maps-to-an-image-banner)

   hinzufügen einem oder mehreren Hotspots oder Imagemaps zu einem Bildbanner. Verknüpfen Sie dann jede der beiden Aktionen mit einem Link, einer Quick-Ansicht oder einem Erlebnisfragment. Nachdem Sie Hotspots oder Imagemaps hinzugefügt haben, schließen Sie diese Aufgabe ab, indem Sie das Karussellset veröffentlichen. Durch das Veröffentlichen wird der Einbettungs-Code erstellt, den Sie kopieren und auf die Landingpage Ihrer Website anwenden können.

   Siehe [(Optional) Anzeigen einer Vorschau für Karussellbanner](#optional-previewing-carousel-banners) – Optional. Bei Bedarf können Sie eine Darstellung des Karussellsets anzeigen und dessen Interaktivität testen.

1. [Veröffentlichen Sie Karussellbanner](#publishing-carousel-banners).

   Sie veröffentlichen ein Karussellset wie jedes andere Asset. Navigieren Sie in Assets zum Karussellset, wählen Sie es aus und tippen Sie auf **[!UICONTROL Veröffentlichen]**. Durch Veröffentlichen eines Karussellsets wird die URL und die Einbettungszeichenfolge aktiviert.

1. Führen Sie einen der folgenden Schritte aus:

   * [Fügen Sie ein Karussellbanner zu Ihrer Website-Seite hinzu.](#adding-a-carousel-banner-to-your-website-page)Sie können die Karussellbanner-URL oder den Einbettungs-Code hinzufügen, die oder den Sie auf die Website-Seite kopiert haben.

      * [Integrieren Sie das Karussellbanner in eine vorhandene Quick-Ansicht](#integrating-the-carousel-banner-with-an-existing-quickview). Wenn Sie ein Drittanbieter-Web-Content-Management-System verwenden, müssen Sie das neue Karussell-Banner in die vorhandene Quick Ansicht-Implementierung auf Ihrer Website integrieren.
   * [hinzufügen eines Karussellbanners auf Ihrer Website in Experience ](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md) ManagerWenn Sie ein Experience Manager-Sites-Kunde sind, können Sie das Karussellset mithilfe der Komponente &quot;Interaktive Medien&quot;direkt zur Experience Manager-Seite hinzufügen.


Wenn Sie Karussell-Sets bearbeiten müssen, lesen Sie [Karussell-Sets bearbeiten.](#editing-carousel-sets). Darüber hinaus können Sie [Eigenschaften von Karussellsets](/help/assets/manage-digital-assets.md#editing-properties) anzeigen und bearbeiten.

## Ermitteln von Hotspot- und Imagemap-Variablen {#identifying-hotspot-and-image-map-variables}

Beginn durch Identifizieren der dynamischen Variablen, die von der vorhandenen Quick Ansicht-Implementierung verwendet werden. Auf diese Weise können Sie Hotspots oder Imagemap-Daten während der Karussellsatzerstellung in Experience Manager Assets ordnungsgemäß eingeben.

Wenn Sie Hotspots oder Imagemaps zu einem Bannerbild hinzufügen, weisen Sie jedem Hotspot oder jeder Imagemap eine SKU und optional zusätzliche Variablen zu. Diese Variablen werden später verwendet, um Hotspots oder Imagemaps mit Quick Ansicht-Inhalten abzugleichen.

<!-- LEAVE; COMMERCE BEING ADDED LATER

>[!NOTE]
>
>If you are an AEM Sites and/or AEM Ecommerce customer, skip this step. You do not need to manually identify hotspot or image map variables; you can use the integration with Ecommerce for product integration. See information on [setting up eCommerce](/help/sites-cloud/administering/generic.md). In addition, you can use the Interactive component and add it to your web page.
>
>If you are an AEM Assets or Media customer, you publish the URL or Embed code and then integrate with your third-party content management system and identify hotspots and image maps manually.

-->

Es ist wichtig, die Anzahl und den Typ der Variablen, denen Hotspot- oder Imagemap-Daten zugewiesen werden sollen, korrekt zu ermitteln. Jeder Hotspot oder jede Imagemap, die einem Bannerbild hinzugefügt wird, muss genügend Informationen enthalten, um das Produkt im bestehenden Back-End-System eindeutig zu identifizieren. Gleichzeitig sollten Sie sicherstellen, dass jeder Hotspot oder jede Imagemap nicht mehr Daten enthält, als erforderlich sind. Dies würde die Dateneingabe unnötig erschweren und bei der Verwaltung von Hotspots und Imagemaps könnten leichter Fehler auftreten.

Es gibt verschiedene Möglichkeiten, den für Hotspot- oder Imagemap-Daten zu verwendenden Variablensatz zu ermitteln,

Manchmal reicht es aus, sich mit IT-Spezialisten zu beraten, die für die Implementierung der Quick Ansicht zuständig sind. Sie wissen wahrscheinlich, was der Mindestsatz an Daten ist, um eine schnelle Ansicht im System zu identifizieren. Es ist jedoch möglich, das bestehende Verhalten des Front-End-Codes einfach zu analysieren.

Bei den meisten Implementierungen der schnellen Ansicht wird das folgende Paradigma verwendet:

* Benutzer aktiviert ein Benutzeroberflächenelement auf der Website. Beispielsweise durch Klicken auf die Schaltfläche für eine **[!UICONTROL Schnellansicht]**.
* Die Website sendet eine Ajax-Anforderung an das Backend, um die Daten oder den Inhalt der Quick-Ansicht zu laden, falls erforderlich.
* Die Daten zur schnellen Ansicht werden in den Inhalt übersetzt, um die Wiedergabe auf der Webseite vorzubereiten.
* Schließlich zeigt der Frontend-Code diesen Inhalt visuell auf dem Bildschirm an.

Der Ansatz besteht dann darin, verschiedene Bereiche der bestehenden Website zu besuchen, in denen die Schnellfunktion zur Ansicht implementiert ist. Trigger dann die Quick-Ansicht und erfassen Sie die Ajax-URL, die von der Webseite zum Laden der Quick-Ansicht-Daten oder -Inhalte gesendet wird.

Normalerweise müssen Sie keine speziellen Debugging-Tools verwenden. Moderne Webbrowser verfügen über Web-Inspektoren, die dafür ausreichend sind. Die folgenden Webbrowser beispielsweise umfassen Web-Inspektoren:

* Um alle ausgehenden HTTP-Anfragen in Google Chrome anzuzeigen, drücken Sie F12 (Windows) oder Command-Option-I (Mac), um das Developer Tool-Bedienfeld zu öffnen. Tippen Sie auf die Registerkarte Netzwerk.
* In Firefox können Sie das Firebug-Plug-in entweder durch Drücken von F12 (Windows) oder Befehl-Option-I (Mac) aktivieren. Verwenden Sie die Registerkarte &quot;Netzwerk&quot;oder das integrierte Inspektor-Tool und dessen Registerkarte &quot;Netzwerk&quot;.

Wenn die Netzwerküberwachung im Browser aktiviert ist, Trigger die Schnellseite der Ansicht.

Suchen Sie nun die Ajax-URL der Schnellversion im Netzwerkprotokoll und kopieren Sie die aufgezeichnete URL für die zukünftige Analyse. Normalerweise werden beim Trigger der Quick-Ansicht zahlreiche Anfragen an den Server gesendet. Normalerweise ist die Ajax-URL für die schnelle Ansicht eine der ersten in der Liste. Sie weist einen Teil oder Pfad mit einer komplexen Abfragezeichenfolge auf und ihr MIME-Typ lautet entweder `text/xml`, `text/html` oder `text/javascript`.

Dabei ist es wichtig, verschiedene Bereiche Ihrer Website mit unterschiedlichen Kategorien und Typen zu besuchen. Der Grund dafür ist, dass die URLs der schnellen Ansicht Teile enthalten, die für eine bestimmte Website-Kategorie häufig vorkommen, sich aber nur ändern, wenn Sie einen anderen Bereich der Website besuchen.

Im einfachsten Fall ist die Produkt-SKU der einzige Variablenteil in der Quick Ansicht-URL. In diesem Fall ist der SKU-Wert der einzige Datenteil, den Sie benötigen, um dem Bannerbild Hotspots oder Imagemaps hinzuzufügen.

In komplexen Fällen enthält die URL der Schnellkorrektur jedoch zusätzlich zur SKU unterschiedliche Elemente wie Kategorien-ID, Farbcode, Größencode usw. In diesen Fällen ist jedes Element eine separate Variable in der Hotspot- oder Imagemap-Datendefinition innerhalb der Karussellbanner-Funktion.

Betrachten Sie die folgenden Beispiele für URLs für die schnelle Ansicht und die sich daraus ergebenden Hotspot- oder Imagemap-Variablen:

<table>
 <tbody>
  <tr>
   <td>Einzelne SKU, befindet sich in der Abfragezeichenfolge.</td>
   <td><p>Zu den aufgezeichneten URLs für die schnelle Ansicht gehören:</p>
    <ul>
     <li><p><code>https://server/json?productId=866558&amp;source=100</code></p> </li>
     <li><p><code>https://server/json?productId=1196184&amp;source=100</code></p> </li>
     <li><p><code>https://server/json?productId=1081492&amp;source=100</code></p> </li>
     <li><p><code>https://server/json?productId=1898294&amp;source=100</code></p> </li>
    </ul> <p>Der einzige variable Teil der URL ist der Wert des Abfrageparameters <code>productId=</code> und es ist offensichtlich ein SKU-Wert. Daher benötigen Hotspots oder Imagemaps nur SKU-Felder, die mit Werten wie <code>866558,</code> <code>1196184,</code> <code>1081492,</code> <code>1898294.</code></p> </td>
  </tr>
  <tr>
   <td>Einzelne SKU, befindet sich im URL-Pfad.</td>
   <td><p>Zu den aufgezeichneten URLs für die schnelle Ansicht gehören:</p>
    <ul>
     <li><p><code>https://server/product/6422350843</code></p> </li>
     <li><p><code>https://server/product/1607745002</code></p> </li>
     <li><p><code>https://server/product/0086724882</code></p> </li>
    </ul> <p>Der variable Teil befindet sich im letzten Abschnitt des Pfads und wird zum SKU-Wert der Hotspots/Imagemaps:<strong><code>6422350843</code>, <code>1607745002,</code> </strong><code>0086724882.</code></p> </td>
  </tr>
  <tr>
   <td>SKU und Kategorie-ID in der Abfragezeichenfolge.</td>
   <td><p>Zu den aufgezeichneten URLs für die schnelle Ansicht gehören:</p>
    <ul>
     <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=305466</code></p> </li>
     <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=310181</code></p> </li>
     <li><p><code>https://server/quickView/product/?category=1740148&amp;prodId=308706</code></p> </li>
    </ul> <p>In diesem Fall liegen zwei abweichende Teile in der URL vor. Die SKU wird im Parameter <code>prodId</code> gespeichert, während die Kategorie-ID im Parameter <code>category=</code> gespeichert wird.</p> <p>Bei den Hotspot- oder Imagemap-Definitionen selbst handelt es sich um Paare. Das heißt, ein SKU-Wert und eine zusätzliche Variable namens <code>categoryId</code>. Die resultierenden Paare lauten wie folgt:</p>
    <ul>
     <li><p>Die SKU lautet <strong><code>305466</code></strong> und <code>categoryId</code> lautet <code>1100004</code>.</p> </li>
     <li><p>Die SKU lautet <strong><code>310181</code></strong> und <code>categoryId</code> lautet <strong><code>1100004</code></strong>.</p> </li>
     <li><p>Die SKU lautet <strong><code>308706</code></strong> und <code>categoryId</code> lautet <strong><code>1740148</code></strong>.</p> </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## Hochladen von Bildbannern {#uploading-image-banners}

Wenn Sie bereits die Bilder hochgeladen haben, die Sie verwenden möchten, fahren Sie mit dem nächsten Schritt [Erstellen von Karussellsets](#creating-carousel-sets) fort. Die im Karussell verwendeten Bilder müssen nach der Aktivierung von Dynamic Media hochgeladen werden.

Informationen zum Hochladen von Bildbannern finden Sie unter [Hochladen von Assets](/help/assets/manage-digital-assets.md).

## Erstellen von Karussellsets  {#creating-carousel-sets}

>[!NOTE]
>
>Benutzer, die keine Administratoren sind, müssen der Gruppe **[!UICONTROL dam-users]** hinzugefügt werden, damit sie Karussellbanner erstellen oder bearbeiten können. Wenn Sie Probleme beim Erstellen oder Bearbeiten haben, wenden Sie sich an Ihren Systemadministrator, der Sie der Gruppe **[!UICONTROL dam-users]** hinzufügen kann.

**So erstellen Sie ein Karussellset**

1. Navigieren Sie in Assets zu dem Ordner, in dem Sie das Karussellset erstellen möchten, und tippen Sie auf **[!UICONTROL Erstellen > Karussellset]**.
1. Tippen Sie im Karussellbanner-Editor auf **[!UICONTROL Tippen, um die Asset-Auswahl zu öffnen]**, um das Bild für die erste Folie auszuwählen.

   Führen Sie im Karussellbanner-Editor eine der folgenden Aktionen aus:

   * Tippen Sie oben links auf **[!UICONTROL Folie hinzufügen]**.

   * Tippen Sie in der Mitte der Seite auf **[!UICONTROL Tippen, um die Asset-Auswahl zu öffnen]**.
   Tippen Sie zur Auswahl von Assets, die Sie in das Karussellset aufnehmen möchten. Die ausgewählten Assets sind mit einem Häkchen versehen. Wenn Sie fertig sind, tippen Sie rechts oben auf der Seite auf **[!UICONTROL Auswahl]**.

   Mit der Asset-Auswahl können Sie nach Assets suchen, indem Sie ein Keyword eingeben und auf **[!UICONTROL Zurück]** tippen/klicken. Sie können auch Filter anwenden, um Ihre Suchergebnisse genauer abzustimmen. Sie können nach Pfad, Sammlung, Dateityp und Tag filtern. Wählen Sie den Filter aus und tippen Sie dann in der Symbolleiste auf das Symbol **[!UICONTROL Filter]**. Ändern Sie die Ansicht, indem Sie das Symbol „Ansicht“ tippen und dann **[!UICONTROL Spaltenansicht]**, **[!UICONTROL Kartenansicht]** oder **[!UICONTROL Listenansicht]** wählen.

   Weitere Informationen finden Sie unter [Arbeiten mit Selektoren](/help/assets/dynamic-media/working-with-selectors.md).

1. Fügen Sie weitere Folien hinzu, bis Sie alle gewünschten Bilder für das Karussellset ausgewählt haben.
1. (Optional) Führen Sie einen der folgenden Schritte aus:

   * Ziehen Sie bei Bedarf die Folios, um die Anordnung der Bilder in der Liste zu ändern.
   * Um ein Bild zu löschen, wählen Sie das Bild aus und tippen Sie dann in der Symbolleiste auf **[!UICONTROL Folie]** löschen.

   * Um eine Vorgabe anzuwenden, tippen Sie oben rechts auf die Dropdown-Liste mit den Vorgaben. Wählen Sie anschließend eine Vorgabe aus, um sie auf das ganze Set anzuwenden.
   Um eine Folie zu löschen, tippen oder klicken Sie auf die Folie und tippen und klicken Sie auf **[!UICONTROL Folie löschen]** in der Symbolleiste. Um eine Folie zu verschieben, tippen Sie auf das Symbol &quot;Neu anordnen&quot;, halten Sie die Taste gedrückt und verschieben Sie sie an die gewünschte Position.

1. Nachdem Sie die Bilder in den Folien hinzugefügt haben, können Sie einen Hotspot, eine Imagemap oder beides in die Bilder einfügen. Siehe [Hinzufügen von Hotspots oder Imagemaps](#adding-hotspots-or-image-maps-to-an-image-banner).
1. Sie können das visuelle Design und das Verhalten von Karussellsätzen ändern, indem Sie auf die Registerkarten &quot;Verhalten&quot;und &quot;Erscheinungsbild&quot;tippen oder darauf klicken und das Aussehen Ihres Karussellbanners oder das Verhalten bestimmter Komponenten anpassen. Weitere Informationen zum Verwenden des Viewer-Editors finden Sie unter [Verwalten von Viewer-Vorgaben](/help/assets/dynamic-media/viewer-presets.md).

   >[!NOTE]
   >
   >Für Karussellbanner können Sie Folgendes anpassen:
   >    * Dauer der Anzeige eines Bildes Standardmäßig wird jedes Bild für 9 Sekunden angezeigt.
   >    * Animation. Standardmäßig sind alle Folienübergänge Überblendungen. Sie können einen anderen Übergang auswählen.
   >    * Stil der Schaltflächen Benutzer können die Banner durchlaufen, indem sie auf die jeweiligen Punkte oder Zahlen tippen. Sie können ändern, wo die Set-Indikatoren angezeigt werden (und ob es sich um einen numerischen oder Punktstil handelt). Sie können auch ihre Größe bestimmen.
   >    * Ändern des Markierungsstils einer Imagemap oder des Symbols für Hotspots.
   >    * Bevor Sie eine Viewer-Vorgabe bearbeiten, wählen Sie den Stil, auf dem die Vorgabe basieren soll. Wenn Sie keinen Stil auswählen und die Viewer-Vorgabe bearbeiten möchten, gehen alle Änderungen verloren, wenn Sie zu einer anderen Vorgabe wechseln.


   Sie können auch Vorschauen darüber vornehmen, wie das Karussell-Banner aussieht. Siehe [(Optional) Anzeigen einer Vorschau für Karussellbanner](#optional-previewing-carousel-banners).

1. Tippen Sie auf **[!UICONTROL Speichern]**, wenn Sie fertig sind.

## Hinzufügen von Hotspots oder Imagemaps in einem Bildbanner {#adding-hotspots-or-image-maps-to-an-image-banner}

Sie können einem Banner mithilfe des Karussellset-Editors Hotspots oder Imagemaps hinzufügen.

Wenn Sie Hotspots oder Imagemaps hinzufügen, können Sie diese als Popup-Ansicht, als Hyperlink oder als Erlebnisfragment definieren.

Siehe [Experience Fragment](/help/sites-cloud/authoring/fundamentals/experience-fragments.md).

>[!NOTE]
>
>Die Social-Media-Freigabe-Werkzeuge im Karussell-Banner werden nicht unterstützt, wenn Sie den Viewer in ein Erlebnisfragment einbetten.
>
>Um dieses Problem zu umgehen, können Sie Viewer-Vorgaben verwenden oder erstellen, für die keine Social Media-Sharing-Werkzeuge zur Verfügung stehen. Mit diesen Viewer-Vorgaben können Sie sie erfolgreich in Experience Fragments einbetten.

Vergessen Sie nicht, Ihre Arbeit zu speichern, wenn Sie einem Bild Hotspots oder Imagemaps hinzufügen. Die Optionen „Rückgängig“ und „Wiederholen“ in der Nähe der oberen rechten Ecke der Seite werden während der aktuellen Erstellungs-/Bearbeitungssitzung unterstützt.

Wenn Sie mit der Erstellung des Karussellbanners fertig sind, können Sie optional mit der Vorschau eine Darstellung der Darstellung Ihres Karussellbanners für Ihre Kunden anzeigen.

Siehe [(Optional) Anzeigen einer Vorschau für Karussellbanner](#optional-previewing-carousel-banners).

>[!NOTE]
>
>Wenn Sie Hotspots zu einem Bild in einem [Interaktiven Bild](/help/assets/dynamic-media/interactive-images.md) oder einem Karussell-Banner hinzufügen, werden die Hotspot-Informationen relativ zum Speicherort des Bilds am selben Metadatenspeicherort gespeichert. Dieser Punkt trifft zu, unabhängig davon, ob es sich um ein interaktives Bild oder ein Karussell-Banner handelt. Dank dieser Funktion können Sie dasselbe Bild - zusammen mit den definierten Hotspot-Daten - in beiden Viewern problemlos wiederverwenden.
Beachten Sie jedoch, dass Karussellbanner Imagemaps auf Bildern unterstützen, die auch Hotspots enthalten können. Bei interaktiven Bildern wird dies dagegen nicht unterstützt. Beachten Sie diese Hinweise, wenn Sie ein interaktives Bild oder ein Karussell-Banner erstellen möchten, das dasselbe Bild verwendet. Sie sollten stattdessen interaktive Bilder und Karussell-Banner mit separaten Kopien desselben Bildes erstellen.

>[!NOTE]
Wenn Sie interaktive Bilder mit Hotspots bearbeiten, um das Bild zu beschneiden, werden die Hotspots entfernt.

<!-- See also [Adding Image Maps](/help/assets/image-maps.md). -->

**So fügen Sie Hotspots oder Imagemaps in einem Bildbanner hinzu**

1. Navigieren Sie in Assets zu dem Karussellset, das interaktiv werden soll.
1. Wählen Sie das Karussellset aus und tippen Sie auf **[!UICONTROL Bearbeiten]**. Der Karussell-Viewer-Editor wird geöffnet.
1. Wählen Sie die Folie aus, die interaktiv sein soll.
1. Tippen Sie in der Nähe der linken oberen Ecke der Seite auf **[!UICONTROL Hotspot]** oder **[!UICONTROL Imagemap]**.
1. Führen Sie einen der folgenden Schritte aus:

   * Hotspots: Tippen Sie auf dem Bild auf eine Stelle, an der der Hotspot angezeigt werden soll.
   * Für Imagemaps: Klicken Sie im Bild auf und ziehen Sie dann von oben links nach unten rechts, um den Imagemap-Bereich zu erstellen. Sie können die Größe der Imagemap anpassen, indem Sie an den Ecken ziehen.

   Ziehen Sie den Hotspot oder die Imagemap ggf. an eine neue Position. Sie können auch die Pfeiltasten verwenden, um die Position eines ausgewählten Hotspots zu steuern. hinzufügen Sie nach Bedarf weitere Hotspots oder Imagemaps.

   Um einen Hotspot oder eine Image Map zu löschen, tippen Sie auf die Registerkarte **[!UICONTROL Aktionen]**. Wählen Sie unter der Überschrift **[!UICONTROL Karten und Hotspots]** aus der Dropdown-Liste **[!UICONTROL Ausgewählter Typ]** den Namen des Hotspots oder der Imagemap, den Sie entfernen möchten. Tippen Sie auf das **[!UICONTROL Papierkorb]**-Symbol neben dem Menü und dann auf **[!UICONTROL Löschen]**.

1. Geben Sie im Textfeld „Name“ den Namen des Hotspots oder der Imagemap ein. Dieser Name wird auch in der Dropdown-Liste **[!UICONTROL Karten und Hotspots]** angezeigt. Wenn Sie einen Namen angeben, können Sie den Hotspot oder die Imagemap leicht identifizieren, wenn Sie ihn in Zukunft ändern möchten.
1. Führen Sie einen der folgenden Schritte auf der Registerkarte **[!UICONTROL Aktion]** aus:

   * Tippen Sie auf **[!UICONTROL Schnellere Ansicht]**.

      * Wenn Sie Experience Manager-Sites <!-- and Ecommerce--> sind, tippen Sie auf das Symbol &quot;Produktauswahl&quot;(Lupe), um die Seite &quot;Produkt auswählen&quot;zu öffnen. Um zum Karussell-Banner-Editor zurückzukehren, tippen Sie auf das gewünschte Produkt und dann auf das Häkchen in der oberen rechten Ecke der Seite.
      * Wenn Sie kein Experience Manager sind Sites <!-- or Ecommerce --> Kunde:

         * Variablen definieren. Informationen hierzu finden Sie unter [Ermitteln von Hotspot-Variablen](#identifying-hotspot-and-image-map-variables).
         * Geben Sie anschließend manuell den SKU-Wert ein. Geben Sie im Textfeld „SKU-Wert“ die Bestandseinheit (Stock Keeping Unit, SKU) des Produkts ein. Hierbei handelt es sich um eine eindeutige Kennung für die jeweiligen von Ihnen angebotenen Produkte oder Services. Der eingegebene SKU-Wert füllt automatisch den Variablenbereich der Quick Ansicht-Vorlage, damit das System den getippten Hotspot mit der Quick-Ansicht einer bestimmten SKU verknüpfen kann.
         * (Optional) Wenn sich in der Quick-Ansicht noch andere Variablen befinden, die Sie zur weiteren Identifizierung eines Produkts verwenden müssen, tippen Sie auf **[!UICONTROL Hinzufügen Generische Variable]**. Geben Sie im Textfeld eine zusätzliche Variable an. Beispielsweise ist category=Men eine hinzugefügte Variable.

         * Weitere Informationen finden Sie unter [Arbeiten mit Selektoren](/help/assets/dynamic-media/working-with-selectors.md).
   * Tippen Sie auf **[!UICONTROL Hyperlink]**.

      * Wenn Sie AEM Sites-Kunde sind, tippen Sie auf das Symbol zur Site-Auswahl (Ordner), um zu einer URL zu navigieren.

         >[!NOTE]
         Die URL-basierte Verknüpfungsmethode ist nicht möglich, wenn Ihr interaktiver Inhalt über Links mit relativen URLs verfügt, insbesondere über Links zu Seiten in AEM Sites.

      * Wenn Sie ein eigenständiger Kunde sind, geben Sie im Textfeld &quot;href&quot;den vollständigen URL-Pfad zu einer verknüpften Webseite an.

   Vergessen Sie nicht anzugeben, ob der Link auf einer neuen Browser-Registerkarte (empfohlener Standard) oder auf derselben Registerkarte geöffnet werden soll.

   Weitere Informationen finden Sie unter [Arbeiten mit Selektoren](/help/assets/dynamic-media/working-with-selectors.md).

   * Tippen Sie auf **[!UICONTROL Experience Fragment]**.

      * Wenn Sie AEM Sites-Kunde sind, tippen Sie auf das Suchsymbol (Lupe), um die Seite „Experience Fragment“ zu öffnen. Um zur Hotspot-Verwaltungsseite zurückzukehren, tippen oder klicken Sie auf das zu verwendende Erlebnisfragment und tippen Sie dann oben rechts auf der Seite auf Auswählen.
Weitere Informationen finden Sie unter [Experience Fragments](/help/sites-cloud/authoring/fundamentals/experience-fragments.md).

      * Geben Sie die Breite und Höhe des Erlebnisfragments so an, wie es auf dem Banner angezeigt wird.

         >[!NOTE]
         Die Social-Media-Freigabe-Werkzeuge im Karussell-Banner werden nicht unterstützt, wenn Sie den Viewer in ein Erlebnisfragment einbetten.
         Um diesen Punkt zu umgehen, können Sie Viewer-Vorgaben verwenden oder erstellen, für die keine Social Media-Sharing-Werkzeuge zur Verfügung stehen. Mit diesen Viewer-Vorgaben können Sie sie erfolgreich in Experience Fragments einbetten.
   ![experience_fragment-carouselbanner](assets/experience_fragment-carouselbanner.png)

   Sie können auch Vorschauen darüber vornehmen, wie das Karussell-Banner aussieht. Siehe [(Optional) Anzeigen einer Vorschau für Karussellbanner](#optional-previewing-carousel-banners).

1. Tippen Sie auf **[!UICONTROL Speichern]**.
1. Veröffentlichen Sie das Karussellset. Durch das Veröffentlichen wird der Einbettungs-Code oder die URL erstellt, den/die Sie auf der Web-Seite verwenden können. Wenn Sie Experience Manager-Sites sind, fügen Sie das Karussellset direkt zu Ihrer Webseite hinzu.

   Siehe [Veröffentlichen von Assets](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

   Siehe [Hinzufügen eines Karussellsets zur Landingpage Ihrer Website](#adding-a-carousel-banner-to-your-website-page).

## Bearbeiten von Karussellsets   {#editing-carousel-sets}

>[!NOTE]
Benutzer, die keine Administratoren sind, müssen der Gruppe **[!UICONTROL dam-users]** hinzugefügt werden, damit sie Karussellbanner erstellen oder bearbeiten können. Wenn Sie Probleme beim Erstellen oder Bearbeiten haben, wenden Sie sich an Ihren Systemadministrator, der Sie der Gruppe **[!UICONTROL dam-users]** hinzufügen kann.

Sie können verschiedene Aufgaben zum Bearbeiten von Karussellsätzen durchführen, z. B.:

* einem Karussellset Folien hinzufügen. Siehe auch [Arbeiten mit Selektoren](/help/assets/dynamic-media/working-with-selectors.md).
* Ordnen Sie die Folien im Karussellsatz neu an.
* Assets im Karussellset löschen
* Viewer-Vorgaben anwenden.
* das Karussellset löschen.
* Hotspots und Imagemaps hinzufügen oder bearbeiten. Siehe auch [Arbeiten mit Selektoren](/help/assets/dynamic-media/working-with-selectors.md).

**So bearbeiten Sie ein Karussellset**

1. Führen Sie einen der folgenden Schritte aus:

   * Bewegen Sie den Mauszeiger über ein Karussell-Set-Asset und tippen Sie dann auf **[!UICONTROL Bearbeiten]** (Stiftsymbol).
   * Bewegen Sie den Mauszeiger über ein Karussell-Set-Asset, tippen Sie auf **[!UICONTROL Wählen Sie]** (Häkchensymbol) und dann auf **[!UICONTROL Bearbeiten]** in der Symbolleiste.

   * Tippen Sie auf ein Karussell-Asset und dann links oben auf der Seite auf **[!UICONTROL Bearbeiten]** (Bleistiftsymbol).

1. Um das Karussellset zu bearbeiten, führen Sie einen der folgenden Schritte aus:

   * Um eine Folie hinzuzufügen, tippen Sie auf das Symbol **[!UICONTROL Hinzufügen Folie]**, navigieren Sie dann zu dem Asset, das Sie der Folie hinzufügen möchten, und tippen oder klicken Sie auf das Häkchen.
   * Um die Folios neu anzuordnen, ziehen Sie eine Folie an eine neue Position (klicken Sie auf das Symbol &quot;Neu anordnen&quot;, um Elemente zu verschieben).
   * Um einen Hotspot oder eine Imagemap hinzuzufügen, klicken Sie auf die Hotspot- oder Imagemap-Symbole und lesen Sie [Hinzufügen von Hotspots und Imagemaps](#adding-hotspots-or-image-maps-to-an-image-banner).
   * Um das Erscheinungsbild und das Verhalten des Karussellsets zu bearbeiten, tippen Sie auf die Registerkarte **[!UICONTROL Erscheinungsbild]** oder **[!UICONTROL Verhalten]** und legen Sie dann die gewünschten Optionen fest.
   * Um Hotspots oder Imagemaps zu bearbeiten, wählen Sie auf der entsprechenden Folie einen Hotspot oder eine Imagemap aus. Nehmen Sie unter der Registerkarte **[!UICONTROL Aktionen]** Ihre Änderungen vor.
   * Um eine Folie zu löschen, wählen Sie sie aus und tippen Sie dann in der Symbolleiste auf **[!UICONTROL Folie]** löschen.
   * Um eine Vorgabe anzuwenden, tippen Sie oben rechts auf der Seite auf die Dropdown-Liste **[!UICONTROL Vorgaben]** und wählen Sie eine Viewer-Vorgabe aus.
   * Um ein ganzes Karussellset zu löschen, navigieren Sie zum Karussellset, wählen Sie es aus und tippen Sie auf **[!UICONTROL Löschen]**.

   >[!NOTE]
   Wenn Sie interaktive Bilder mit Hotspots bearbeiten, um das Bild zu beschneiden, werden die Hotspots entfernt.

## (Optional) Anzeigen einer Vorschau für Karussellbanner {#optional-previewing-carousel-banners}

Sie können Vorschau verwenden, um zu sehen, wie das Karussell-Banner für Kunden aussieht, und um die Hotspots und Imagemaps für Karussellbanner zu testen, um sicherzustellen, dass sie sich wie erwartet verhalten.

Wenn das Karussellbanner Ihren Vorstellungen entspricht, können Sie es veröffentlichen.
Siehe [Einbetten des Video- oder Bild-Viewers auf einer Web-Seite](/help/assets/dynamic-media/embed-code.md).
Siehe [Verknüpfen von URLs mit einer Web-Anwendung](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md). Die URL-basierte Verknüpfungsmethode ist nicht möglich, wenn Ihr interaktiver Inhalt über Links mit relativen URLs verfügt, insbesondere über Links zu Seiten in AEM Sites.
Siehe [Hinzufügen von Dynamic Media-Assets zu Seiten](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md).

Um eine Vorschau für ein Karussellbanner anzuzeigen, verwenden Sie entweder den Karusselleditor (bevorzugte Methode) oder die **[!UICONTROL Viewer]**-Liste.

**So erstellen Sie eine Vorschau von Karussellbannern**

1. In **[!UICONTROL Assets]** navigieren Sie zu einem vorhandenen Karussellbanner, das Sie erstellt haben, und tippen Sie darauf, um das Banner zu öffnen.
1. Tippen Sie auf **[!UICONTROL Bearbeiten]**.
1. Wählen Sie in der Liste &quot;Viewer-Vorgaben&quot;rechts in der Symbolleiste einen Viewer aus, um das Karussell-Banner Vorschau.

   ![experience_fragment-carouselbanner-viewerdropdown](assets/experience_fragment-carouselbanner-viewerdropdown.png)

1. Tippen Sie auf **[!UICONTROL Vorschau]**.
1. Um die zugehörigen Aktionen zu testen, tippen Sie auf die Hotspots oder Imagemaps im Bild.

**So zeigen Sie eine Vorschau für Karussellbanner über die Viewer-Liste an**

1. In **[!UICONTROL Assets]** navigieren Sie zu einem vorhandenen Karussellbanner, das Sie erstellt haben, und tippen Sie darauf, um das Banner zu öffnen.
1. Klicken Sie in der linken oberen Ecke der Seite „Vorschau“ auf das Symbol „Inhalt“.
1. Tippen Sie in der Liste **[!UICONTROL Viewer]** im Bedienfeld auf der linken Seite auf den Namen der Karussell-Banner-Viewer-Vorgabe, die Sie verwenden möchten.
1. Um die zugehörigen Aktionen zu testen, tippen Sie auf die Hotspots oder Imagemaps im Bild.

## Veröffentlichen von Karussellbannern {#publishing-carousel-banners}

Veröffentlichen Sie das Karussell, um es zu verwenden. Durch Veröffentlichen eines Karussellsets werden die URL und der Einbettungs-Code aktiviert. Außerdem wird das Karussell in der Dynamic Media-Cloud veröffentlicht, die für skalierbare und leistungsfähige Bereitstellung in ein CDN integriert ist.

>[!NOTE]
Wenn Sie ein vorhandenes interaktives Bild mit Hotspots für Ihr Karussellbanner verwenden, müssen Sie das interaktive Bild separat veröffentlichen, nachdem Sie das Karussellbanner veröffentlicht haben.
Wenn Sie ein bereits vorhandenes und veröffentlichtes interaktives Bild ändern, das Sie in einem Karussellbanner verwenden, müssen Sie das interaktive Bild veröffentlichen, bevor die Änderungen im Karussellbanner sichtbar werden.

Unter [Veröffentlichen von Dynamic Media-Assets](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md) finden sie Informationen zum Veröffentlichen von Karussellbannern.

## Hinzufügen eines Karussellbanners zu Ihrer Website {#adding-a-carousel-banner-to-your-website-page}

Nachdem Sie Bannerbilder hochgeladen haben, um ein Karussell zu erstellen, Hotspots oder Imagemaps oder beides zum Banner hinzugefügt haben. Karussellsatz veröffentlicht. Sie können sie jetzt Ihrer vorhandenen Website-Seite hinzufügen.

>[!NOTE]
Wenn Sie AEM Sites-Kunde sind, können Sie das Karussellbanner direkt Ihrer Seite hinzufügen, indem Sie die interaktive Medienkomponente auf die Seite ziehen. Siehe [Hinzufügen von Dynamic Media-Assets zu Seiten](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md).

Wenn Sie ein eigenständiger Experience Manager-Asset-Kunde sind, können Sie das Karussell-Banner manuell zu Ihrer Website-Landingpage hinzufügen, wie in diesem Thema beschrieben.

1. Kopieren Sie den Einbettungs-Code des veröffentlichten Karussellsets.
Siehe [Einbetten des Video- oder Bild-Viewers auf einer Web-Seite](/help/assets/dynamic-media/embed-code.md).

1. hinzufügen Sie den Einbettungscode, den Sie von Experience Manager Assets auf Ihre Webseite kopiert haben.
Der kopierte Einbettungscode reagiert schnell und passt automatisch in den Einbettungsbereich der Seite.

## Karussell-Banner mit einer vorhandenen Quick-Ansicht {#integrating-the-carousel-banner-with-an-existing-quickview} integrieren

Hinweis: Dieser Schritt gilt nur, wenn Sie ein eigenständiger AEM Assets-Kunde sind.

Der letzte Schritt in diesem Prozess ist die Integration des Karussell-Banners in eine vorhandene Quick Ansicht-Implementierung auf Ihrer Website. Jede Implementierung der Schnellfunktion ist einzigartig und es ist ein spezifischer Ansatz erforderlich, der in der Regel die Unterstützung eines IT-Mitarbeiters im Front-End umfasst.

Die vorhandene Quick-Ansicht-Implementierung stellt normalerweise eine Kette miteinander verknüpfter Aktionen dar, die auf der Webseite in der folgenden Reihenfolge ausgeführt werden:

1. Ein Benutzer löst ein Element auf der Benutzeroberfläche Ihrer Website aus.
1. Der Front-End-Code ruft eine URL für die schnelle Ansicht basierend auf dem Element der Benutzeroberfläche ab, das in Schritt 1 ausgelöst wurde.
1. Der Frontend-Code sendet mithilfe der in Schritt 2 abgerufenen URL eine Ajax-Anfrage.
1. Die Backend-Logik gibt die entsprechenden Quick-Ansicht-Daten oder -Inhalte zurück zum Front-End-Code.
1. Der Front-End-Code lädt die Daten oder den Inhalt der Quick-Ansicht.
1. Optional konvertiert der Front-End-Code die geladenen Quick-Ansicht-Daten in eine HTML-Darstellung.
1. Der Frontend-Code zeigt ein modales Dialogfeld an und rendert den HTML-Inhalt auf dem Bildschirm für den Endbenutzer.

Diese Aufrufe stellen keine unabhängigen öffentlichen API-Aufrufe dar, die von der Webseitenlogik aus einem beliebigen Schritt aufgerufen werden können. Vielmehr handelt es sich um einen verketteten Aufruf, in dem der jeweils nächste Schritte in der letzten Phase (Callback) des vorherigen Schritts ausgeblendet ist.

Sobald das interaktive Karussellbanner Schritt 1 und teilweise Schritt 2 ersetzt, sofern ein Benutzer auf einen Hotspot oder eine Imagemap im Karussellbanner klickt, wird eine solche Benutzerinteraktion durch den Viewer verarbeitet. Der Viewer gibt ein Ereignis an die Web-Seite zurück, das die gesamten Hotspot- oder Imagemap-Daten enthält, die zuvor hinzugefügt wurden.

In einem solchen Ereignis-Handler nimmt der Frontend-Code Folgendes vor:

* Er lauscht am Ereignis, das durch das Karussellbanner ausgegeben wird.
* Erstellt eine URL für die schnelle Ansicht basierend auf den Hotspot- oder Imagemap-Daten.
* Trigger des Ladevorgangs der Quick-Ansicht vom Back-End und der Wiedergabe auf dem Bildschirm zur Anzeige.

Der von AEM Assets zurückgegebene Einbettungs-Code verfügt über einen einsatzbereiten Ereignis-Handler, der auskommentiert ist.

Daher ist es nur erforderlich, die Auskommentierung des Codes aufzuheben und den Platzhalter-Handlertext durch den Code zu ersetzen, der für die bestimmte Web-Seite spezifisch ist.

Die Erstellung der URL für die schnelle Ansicht erfolgt anders als bei der Identifizierung von Hotspot- und Imagemap-Variablen, die zuvor behandelt wurden.

Siehe [Ermitteln von Hotspot- und Imagemap-Variablen](#identifying-hotspot-and-image-map-variables).

Der letzte Schritt zum Trigger der URL für die schnelle Ansicht und zur Aktivierung des Bedienfelds für die schnelle Ansicht erfordert höchstwahrscheinlich die Unterstützung eines IT-Mitarbeiters von Ihrer IT-Abteilung. Sie verfügen über die nötigen Kenntnisse, um die Implementierung der Quick-Ansicht mit einer benutzerfreundlichen URL für die schnelle Ansicht vom richtigen Schritt aus genau Trigger.

## Verwenden von Quick-Ansichten zum Erstellen benutzerdefinierter Popup-Fenster {#using-quickviews-to-create-custom-pop-ups}

Siehe [Verwenden von Quick-Ansichten zum Erstellen benutzerdefinierter Popup-Fenster](/help/assets/dynamic-media/custom-pop-ups.md).