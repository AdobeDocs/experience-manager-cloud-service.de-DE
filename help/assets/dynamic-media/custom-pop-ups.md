---
title: Erstellen benutzerdefinierter Popup-Ansichten
description: '"Erfahren Sie, wie die standardmäßige Quick-Ansicht in E-Commerce-Erlebnissen verwendet wird, wobei ein Popup-Fenster mit Produktinformationen angezeigt wird, um einen Kauf zu veranlassen. Sie können benutzerspezifischen Trigger zur Anzeige in den Popup-Fenstern verwenden."'
feature: Interaktive Bilder,Interaktive Videos,Karussell-Banner
role: Administrator,Business Practitioner
exl-id: c2bc6ec8-d46e-4681-ac3e-3337b9e6ae5c
translation-type: tm+mt
source-git-commit: e94289bccc09ceed89a2f8b926817507eaa19968
workflow-type: tm+mt
source-wordcount: '1034'
ht-degree: 44%

---

# Verwenden von Quick-Ansichten zum Erstellen benutzerdefinierter Popup-Fenster {#using-quickviews-to-create-custom-pop-ups}

Die standardmäßige Quick-Ansicht wird in E-Commerce-Erlebnissen verwendet, bei denen ein Popup mit Produktinformationen angezeigt wird, um einen Kauf zu fördern. Sie können jedoch benutzerdefinierte Inhalte auslösen, die in Popups angezeigt werden. Abhängig vom verwendeten Viewer können Kunden auf einen Hotspot, ein Miniaturbild oder eine Imagemap tippen, um Informationen oder verwandte Inhalte anzuzeigen.

Schnellere Ansichten werden von den folgenden Viewern in Dynamic Media unterstützt:

* Interaktive Bilder (klickbare Hotspots)
* Interaktives Video (klickbare Miniaturbilder während der Videowiedergabe)
* Karussellbanner (klickbare Hotspots oder Imagemaps)

Während die Funktionen der einzelnen Viewer unterschiedlich sind, erfolgt die Erstellung einer Quick-Ansicht in allen drei unterstützten Viewern gleich.

**So erstellen Sie benutzerdefinierte Popup-Fenster mit den Schnelleinstellungen**

1. Erstellen Sie eine Quick-Ansicht für ein hochgeladenes Asset.

   Normalerweise erstellen Sie eine Quick-Ansicht, wenn Sie ein Asset zur Verwendung mit dem verwendeten Viewer bearbeiten.

   <table>
    <tbody>
    <tr>
    <td><strong>Derzeit verwendeter Viewer</strong></td>
    <td><strong>Führen Sie die folgenden Schritte aus, um die Schnellste Ansicht zu erstellen</strong></td>
    </tr>
    <tr>
    <td>Interaktive Bilder</td>
    <td><a href="/help/assets/dynamic-media/interactive-images.md#adding-hotspots-to-an-image-banner" target="_blank">Hinzufügen von Hotspots zu einem Bildbanner</a>.</td>
    </tr>
    <tr>
    <td>Interaktive Videos</td>
    <td><a href="/help/assets/dynamic-media/interactive-videos.md#adding-interactivity-to-your-video" target="_blank">Hinzufügen von Interaktivität zum Video</a>.</td>
    </tr>
    <tr>
    <td>Karussellbanner</td>
    <td><a href="/help/assets/dynamic-media/carousel-banners.md#adding-hotspots-or-image-maps-to-an-image-banner" target="_blank">Hinzufügen von Hotspots oder Imagemaps zu einem Bildbanner</a>.<br /> </td>
    </tr>
    </tbody>
   </table>

1. Rufen Sie den Einbettungs-Code für den Viewer ab, um den Viewer in Ihre Website zu integrieren.

   <table>
    <tbody>
    <tr>
    <td><strong>Derzeit verwendeter Viewer</strong><br /> </td>
    <td><strong>Führen Sie die folgenden Schritte aus, um den Viewer in Ihre Website zu integrieren</strong></td>
    </tr>
    <tr>
    <td>Interaktives Bild</td>
    <td><a href="/help/assets/dynamic-media/interactive-images.md#integrating-an-interactive-image-with-your-website" target="_blank">Integrieren eines interaktiven Bildes auf Ihrer Website</a>.<br /> </td>
    </tr>
    <tr>
    <td>Interaktives Video<br /> </td>
    <td><a href="/help/assets/dynamic-media/interactive-videos.md#integrating-an-interactive-video-with-your-website" target="_blank">Integrieren eines interaktiven Videos mit Ihrer Website</a>.<br /> </td>
    </tr>
    <tr>
    <td>Karussellbanner</td>
    <td><a href="/help/assets/dynamic-media/carousel-banners.md#adding-a-carousel-banner-to-your-website-page" target="_blank">Hinzufügen eines Karussellbanners zu Ihrer Website</a>.<br /> </td>
    </tr>
    </tbody>
   </table>

1. Der von Ihnen verwendete Viewer muss wissen, wie die Quick-Ansicht zu verwenden ist.

   Der Viewer verwendet einen Handler mit dem Namen `QuickViewActive`.

   **Beispiel**
Angenommen, Sie verwenden auf Ihrer Web-Seite für ein interaktives Bild den folgenden Einbettungs-Code:

   ![chlimage_1-291](assets/chlimage_1-291.png)

   Der Handler wird mit `setHandlers` in den Viewer geladen:

   `*viewerInstance*.setHandlers({ *handler 1*, *handler 2*}, ...`

   **Mithilfe des obigen Beispiel für Einbettungscode haben Sie folgenden Code:**

   ```xml
   s7interactiveimageviewer.setHandlers({
       quickViewActivate": function(inData) {
           var sku=inData.sku;
           var genericVariable1=inData.genericVariable1;
           var genericVariable2=inData.genericVariable2;
          loadQuickView(sku,genericVariable1,genericVariable2);
       }
   })
   ```

   Hier finden Sie weitere Informationen zur Methode `setHandlers()`:

   * Interaktiver Bild-Viewer: [Sethandler](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/jsapi-interactive-image/r-html5-aem-int-image-viewer-javascriptapiref-sethandlers.html?lang=de)
   * Interaktiver Video-Viewer: [Sethandler](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/jsapi-interactive-video/r-html5-aem-int-video-javascriptapiref-sethandlers.html?lang=de)

1. Konfigurieren Sie jetzt den `quickViewActivate`-Handler.

   Der `quickViewActivate`-Handler steuert die Quick-Ansichten im Viewer. Der Handler enthält die Variablenaufrufe und Funktionsaufrufe zur Verwendung mit der Quick-Ansicht. Der Einbettungscode stellt eine Zuordnung für die SKU-Variable bereit, die in der Quick-Ansicht festgelegt wurde. Es führt auch einen Funktionsaufruf mit dem Muster `loadQuickView` durch.

   **Variablenzuordnung**
Zuordnen von Variablen zur Verwendung auf Ihrer Webseite zum SKU-Wert und zu generischen Variablen in der Quick-Ansicht:

   `var *variable1*= inData.*quickviewVariable*`

   Der bereitgestellte Einbettungs-Code enthält ein Zuordnungsbeispiel für die SKU-Variable:

   `var sku=inData.sku`

   Ordnen Sie auch andere Variablen aus der Quick-Ansicht zu, wie im Folgenden:

   ```
   var <i>variable2</i>= inData.<i>quickviewVariable2</i>
    var <i>variable3</i>= inData.<i>quickviewVariable3</i>
   ```

   **Funktionsaufruf**
Der Handler erfordert auch einen Funktionsaufruf, damit die Quick-Ansicht funktioniert. Die Host-Seite muss auf diese Funktion zugreifen können. Der Einbettungs-Code bietet ein Beispiel für einen Funktionsaufruf:

   `loadQuickView(sku)`

   Im Beispiel für einen Funktionsaufruf wird davon ausgegangen, dass die Funktion `loadQuickView()` vorhanden und verfügbar ist.

   Hier finden Sie weitere Informationen zur Methode `quickViewActivate`:

   * Interaktiver Bild-Viewer – [Ereignisrückrufe](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/c-html5-aem-interactive-image-event-callbacks.html?lang=de)
   * Interaktiver Video-Viewer – [Ereignisrückrufe](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/c-html5-aem-int-video-event-callbacks.html?lang=de)
   * Unterstützung interaktiver Daten im interaktiven Video-Viewer – [Unterstützung interaktiver Daten](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/c-html5-aem-int-video-int-data-support.html?lang=de)

1. Gehen Sie folgendermaßen vor:

   * Entfernen Sie im Einbettungs-Code die Auskommentierung des Abschnitts „setHandlers“.
   * Ordnen Sie alle weiteren Variablen zu, die in der Quick-Ansicht enthalten sind.

      * Aktualisieren Sie den `loadQuickView(sku,*var1*,*var2*)`-Aufruf, wenn Sie weitere Variablen hinzufügen.
   * Erstellen Sie auf der Seite eine einfache `loadQuickView` ()-Funktion außerhalb des Viewers.

      Beispielsweise schreibt der Wert von SKU in die Browser-Konsole:

   ```xml
   function loadQuickView(sku){
       console.log ("quickview sku value is " + sku);
   }
   ```

   * Laden Sie eine HTML-Testseite auf einen Webserver hoch und öffnen Sie sie.

      Die Variablen aus der Quick-Ansicht werden zugeordnet. Der Funktionsaufruf ist vorhanden. Und die Browser-Konsole schreibt den Variablenwert in die Browser-Konsole. Dies erfolgt mithilfe der bereitgestellten Beispielfunktion.



1. Sie können jetzt eine Funktion verwenden, um ein einfaches Popup in der Quick-Ansicht aufzurufen. Im folgenden Beispiel wird ein `DIV` für ein Popup verwendet.
1. Gestalten Sie das Popup-`DIV` wie folgt. hinzufügen Sie den gewünschten zusätzlichen Stil.

   ```xml
   <style type="text/css">
       #quickview_div{
           position: absolute;
           z-index: 99999999;
           display: none;
       }
   </style>
   ```

1. Platzieren Sie das Popup-`DIV` im Body-Bereich Ihrer HTML-Seite.

   Eines der Elemente wird mit einer ID festgelegt, die mit dem SKU-Wert aktualisiert wird, wenn der Benutzer eine Quick-Ansicht aufruft. Das Beispiel beinhaltet auch eine einfache Schaltfläche, um das Popup-Fenster wieder auszublenden.

   ```xml
   <div id="quickview_div" >
       <table>
           <tr><td><input id="btnClosePopup" type="button" value="Close"        onclick='document.getElementById("quickview_div").style.display="none"' /><br /></td></tr>
           <tr><td>SKU</td><td><input type="text" id="txtSku" name="txtSku"></td></tr>
       </table>
   </div>
   ```

1. Um den SKU-Wert im Popup-Fenster zu aktualisieren, fügen Sie eine Funktion hinzu. Machen Sie das Popup-Fenster sichtbar, indem Sie die in Schritt 5 erstellte einfache Funktion durch folgende ersetzen:

   ```xml
   <script type="text/javascript">
       function loadQuickView(sku){
           document.getElementById("txtSku").setAttribute("value",sku); // write sku value
           document.getElementById("quickview_div").style.display="block"; // show popup
       }
   </script>
   ```

1. Laden Sie eine HTML-Testseite auf Ihren Webserver hoch und öffnen Sie sie. Der Viewer zeigt das Popup `DIV` an, wenn ein Benutzer eine Quick-Ansicht aufruft.
1. **Anzeigen des benutzerdefinierten Popup-Fensters im Vollbildmodus**

   Einige Viewer, wie der interaktive Video-Viewer, unterstützen die Anzeige im Vollbildmodus. Wenn Sie das Popup-Fenster jedoch verwenden, wie in den vorherigen Schritten beschrieben, wird es im Vollbildmodus hinter dem Viewer angezeigt.

   Damit das Popup-Fenster im Standard- und Vollbildmodus angezeigt wird, hängen Sie das Popup-Fenster an den Viewer-Container an. Verwenden Sie in diesem Fall eine zweite Handler-Methode, `initComplete`.

   Der `initComplete`-Handler wird aufgerufen, nachdem der Viewer initialisiert wurde.

   ```xml
   "initComplete":function() { code block }
   ```

   Hier finden Sie weitere Informationen zur Methode `init()`:

   * Interaktiver Bild-Viewer – [init](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/jsapi-interactive-image/r-html5-aem-int-image-viewer-javascriptapiref-init.html?lang=de)
   * Interaktiver Video-Viewer – [init](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/jsapi-interactive-video/r-html5-aem-int-video-javascriptapiref-init.html?lang=de)

1. Um das in den vorherigen Schritten beschriebene Popup-Fenster mit dem Viewer zu verbinden, verwenden Sie den folgenden Code:

   ```xml
   "initComplete":function() {
       var popup = document.getElementById('quickview_div');
       popup.parentNode.removeChild(popup);
       var sdkContainerId = s7interactivevideoviewer.getComponent("container").getInnerContainerId();
       var inner_container = document.getElementById(sdkContainerId);
       inner_container.appendChild(popup);
   }
   ```

   Im obigen Code haben Sie Folgendes ausgeführt:

   * Das benutzerdefinierte Popup-Fenster wurde identifiziert.
   * Es aus dem DOM entfernt.
   * Den Viewer-Container identifiziert.
   * Das Popup mit dem Viewer-Container verbunden.

1. Ihr gesamter setHandlers-Code ähnelt dem folgenden (Interaktiver Video-Viewer wurde verwendet):

   ```xml
   s7interactivevideoviewer.setHandlers({
       "quickViewActivate": function(inData) {
           var sku=inData.sku;
           loadQuickView(sku);
   
       },
       "initComplete":function() {
           var popup = document.getElementById('quickview_div'); // get custom quick view container
           popup.parentNode.removeChild(popup); // remove it from current DOM
           var sdkContainerId = s7interactivevideoviewer.getComponent("container").getInnerContainerId();
           var inner_container = document.getElementById(sdkContainerId);
           inner_container.appendChild(popup);
       }
   });
   ```

1. Nachdem die Handler geladen wurden, initialisieren Sie den Viewer:

   `*viewerInstance.*init()`

   **Beispiel**
Dieses Beispiel verwendet den interaktiven Bild-Viewer.

   `s7interactiveimageviewer.init()`

   Nachdem Sie den Viewer in Ihre Hostseite eingebettet haben, stellen Sie sicher, dass die Viewer-Instanz erstellt wurde. Stellen Sie außerdem sicher, dass die Handler geladen werden, bevor der Viewer mit `init()` aufgerufen wird.
