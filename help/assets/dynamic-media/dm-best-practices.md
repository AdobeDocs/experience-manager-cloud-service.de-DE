---
title: Best Practices für Dynamic Media
description: Erfahren Sie mehr über Best Practices in Dynamic Media beim Arbeiten mit Bildern und Videos sowie über Best Practices für Dynamic Media-Viewer.
contentOwner: Rick Brough
products: Experience Manager as a Cloud Service
topic-tags: introduction,administering
content-type: reference
feature: Adaptive Streaming, Best Practices, Smart Imaging, Image Profiles, Rulesets, Viewers, Smart Crop, SEO Optimization, Publishing, Video, Renditions, Asset Management
role: User, Admin
mini-toc-levels: 4
exl-id: 39e491bb-367d-4c72-b4ca-aab38d513ac5
source-git-commit: c82f84fe99d8a196adebe504fef78ed8f0b747a9
workflow-type: tm+mt
source-wordcount: '4117'
ht-degree: 99%

---

# Best Practices für Dynamic Media{#about-dm-best-practices}

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

<!--**Organizations today must connect with their customers through an ever-growing array of channels and devices.** The customer experience spans physical stores, websites, mobile apps, social media, email, and e-commerce platforms. This diversity requires organizations to create many more versions of each piece of content. Personalization adds complexity by increasing the number of variations needed for each item. Despite budget constraints for content creation, there's still a need to produce more campaigns in the same timeframe, on a global scale. AEM Dynamic Media offers a comprehensive set of tools to meet these challenges, providing consistent, personalized, high-performance, and optimized brand experiences across all channels and devices. 

Key Features of AEM Dynamic Media:

* **Single File Approach:** Save on storage costs by storing just one master file. AEM Dynamic Media generates all size variations and visual effects on-demand, at the time of delivery, eliminating workflow complexity and last-minute creative changes.
* **Global Reach:** With Smart Imaging, images are automatically optimized during delivery, significantly reducing file size and page weight without sacrificing visual quality. This optimization is tailored for network bandwidth and device pixel ratio.
* **AI-Powered Efficiency:** Smart Crop uses AI to automate the cropping of images and videos, focusing on points of interest. This feature saves countless hours of manual editing and is designed for large-scale enterprise production.
* **Video Made Simple:** Upload a master video file and AEM Dynamic Media will adaptively stream it in multiple languages and with descriptive audio, ensuring a broad reach.
* **Customizable Experience Viewer:** Select, customize, and brand the experience viewers for images and videos with ease. These viewers can be seamlessly integrated into any digital experience.
* **Support for Emerging Formats:** AEM Dynamic Media is also your solution for delivering immersive 3D and panoramic experiences.

In the accompanying guide, you'll find a comprehensive list of best practices for maximizing the benefits of AEM Dynamic Media. As you embark on your Dynamic Media journey, make sure to consult these expert recommendations and resources.

Stage Business Problem Best Practice Recommendation: This section will outline specific business challenges and provide targeted best practices and recommendations to address them effectively. -->

{{see-also-dm}}

Organisationen müssen sich für die Interaktion mit Benutzenden mit zahlreichen Kanälen und Geräten auseinandersetzen. Die Customer Journey umfasst Ladengeschäfte, das Internet, Mobilgeräte, Social Media, E-Mails und Commerce. Um diesen Anforderungen gerecht zu werden, bietet Dynamic Media für Adobe Experience Manager (AEM) eine umfassende Lösung. Sie optimiert die Bereitstellung von Assets, handhabt die Personalisierung und sorgt für konsistente, leistungsfähige und markenorientierte Erlebnisse über Kanäle und Geräte hinweg.

Zu den wichtigsten Grundsätzen von Dynamic Media gehören die Folgenden:

* **Einzeldatei-Ansatz:** Mit Dynamic Media speichern Sie eine primäre Quelldatei. Alle Größenvarianten und visuellen Effekte werden zum Zeitpunkt der Bereitstellung dynamisch erstellt und optimiert. Dieser Ansatz spart Speicherkosten und beseitigt die Komplexität von Workflows.
* **Wirklich global:** Die intelligente Bildbearbeitung, die während der Inhaltsbereitstellung angewendet wird, reduziert die Bild- und Seitengröße erheblich, ohne die visuelle Qualität zu beeinträchtigen. Sie ist für Netzwerkbandbreite und gerätespezifische Pixelverhältnisse optimiert.
* **KI-gestützt:** Das intelligente Zuschneiden, eine KI-gesteuerte Funktion, automatisiert auf Bildern und in Videos das Zuschneiden entsprechend den Interessenschwerpunkten. Die Funktion macht manuelles Arbeiten überflüssig und skaliert effizient für die Verwendung in Unternehmen.
* **Einfaches Video:** Laden Sie Primärvideos in Dynamic Media hoch und streamen Sie sie mit beschreibendem Audio adaptiv über mehrere Sprachen hinweg.
* **Erlebnis Viewer-Bibliothek:** Passen Sie Erlebnis-Viewer für Bilder und Videos an und versehen Sie sie mit ihrer Marke. Diese Viewer lassen sich nahtlos in Ihre digitalen Erlebnisse integrieren.
* **Unterstützung neuer Formate:** Dynamic Media ermöglicht die Bereitstellung von 3D- und Panoramaerlebnissen.

Während der Erkundung der [Dynamic Media Journey](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/dynamicmedia/dm-journey/dm-journey-part1) können Sie sich die unten stehende, konsolidierte Liste mit Best Practices ansehen, um die Funktionen optimal zu nutzen. Passen Sie diese Best Practices für Dynamic Media an Ihre spezifischen Kontext- und Projektanforderungen an, damit Sie Ihre Erlebnisse kanal- und geräteübergreifend optimieren können.

<!-- In Dynamic Media on AEM, there are sets of methods, techniques, and guidelines that can help you maximize the potential of your rich media content. These best practices can lead to optimal results and increase efficiency in your use of Dynamic Media. They represent the most efficient and effective courses of action in a particular situation. They also unlock high value for your audience and deliver high-quality, engaging content. -->

>[!IMPORTANT]
>
>Die Best Practices für Dynamic Media in diesem Artikel können sich im Laufe der Zeit weiterentwickeln, wenn neue Technologien in Dynamic Media eingeführt werden. Die nachfolgenden Informationen beziehen sich auf die neueste Version von Dynamic Media.


## Aufnehmen von Assets in Dynamic Media

**Business-Case:** *Effizientes Verwalten großer Asset-Volumen und Sicherstellung, dass nur relevante, genehmigte Inhalte an Endbenutzende bereitgestellt werden.*

Optimieren Sie die Verwaltung einer großen Anzahl von Assets effizient. Stellen Sie sicher, dass nur die entsprechenden autorisierten Inhalte Ihre Endbenutzenden erreichen, indem Sie die Funktionen **Selektive Synchronisierung** und **Selektive Veröffentlichung** in Dynamic Media verwenden.

* **Selektive Synchronisierung:**
Eine proaktive Funktion, mit der Sie auswählen können, welche Assets mit Dynamic Media synchronisiert werden sollen. Sie können beispielsweise nur diejenigen Ordner mit Assets synchronisieren, für die die endgültige Genehmigung erteilt wurde. Dieser Workflow hilft Ihnen dabei, die Kontrolle darüber zu behalten, welche Assets für die Bereitstellung an Ihre Kundschaft vorbereitet werden.

* **Selektive Veröffentlichung:**
Nach der Synchronisierung Ihrer Assets können Sie durch die selektive Veröffentlichung steuern, welche Assets für Ihre Kundinnen und Kunden sichtbar sind. Auf diese Weise können Sie steuern, welche genehmigten Assets tatsächlich über Ihre Kanäle bereitgestellt werden, und sicherstellen, dass Ihre Kundinnen und Kunden nur die besten und relevantesten Inhalte sehen.

Mithilfe dieser beiden Best Practices können Sie eine bessere Kontrolle, Verwaltung und Produktivität Ihrer Rich-Media-Inhalte erzielen.

Möchten Sie mehr erfahren? Navigieren Sie zu [Konfigurieren einer selektiven Veröffentlichung auf der Ordnerebene in Dynamic Media:](/help/assets/dynamic-media/selective-publishing.md).


## Dynamic Media-Viewer

Die Best Practices für den Dynamic Media-Viewer sind wichtige Richtlinien zum Optimieren der Leistung, Funktionalität und des Anwendererlebnisses von Dynamic Media-Assets in AEM. Diese Verfahren stellen sicher, dass Assets ordnungsgemäß synchronisiert, veröffentlicht und konfiguriert werden, um alle Funktionen von Dynamic Media nutzen zu können.

Durch Befolgen dieser Best Practices können Sie eine nahtlose Integration, ein effizientes Asset-Management und verbesserte Viewer-Interaktionen erzielen. Die Synchronisierung von Assets, die Verwendung des intelligenten Zuschnitts und die Einhaltung der JavaScript-Dateieinschlussrichtlinien sind wichtige Vorgehensweisen. Diese Empfehlungen tragen dazu bei, die Integrität und Zuverlässigkeit der Medienbereitstellung über verschiedene Plattformen und Geräte hinweg aufrechtzuerhalten.

* **Synchronisieren von Viewer Assets:**
Stellen Sie sicher, dass alle Viewer-Assets mit Dynamic Media synchronisiert sind, bevor Sie den Player verwenden.

   * Greifen Sie auf die Seite des Beispiel-Managers unter `/libs/dam/gui/content/s7dam/samplemanager/samplemanager` zu. Auf dieser Seite können Sie die Assets eines Viewers neu synchronisieren, einschließlich vordefinierter Symbole, CSS-Dateien und Vorgaben.
   * Wenn Probleme mit dem Viewer auftreten, lesen Sie den Artikel [Fehlerbehebung bei Dynamic Media-Viewern](/help/assets/dynamic-media/troubleshoot-dm.md#viewers).

* **Veröffentlichen von Assets:**
Stellen Sie sicher, dass Assets veröffentlicht werden, bevor Sie sie in den Bereitstellungs-Viewern anzeigen.
* **Stummgeschaltete automatische Wiedergabe von Videos:**
Verwenden Sie für die automatische Wiedergabe in Videos stummgeschaltete Videoeinstellungen, da Browser die Wiedergabe von Videos mit Lautstärke einschränken.
* **Smartes Zuschneiden:**
Verwenden Sie die Image v3-Komponente für das smarte Zuschneiden, um die Darstellung von Bild-Assets zu verbessern.
* **JavaScript-Dateiaufnahme:**
Schließen Sie nur die primäre Viewer-JavaScript-Datei auf Ihrer Seite ein. Vermeiden Sie es, auf zusätzliche JavaScript-Dateien zu verweisen, die durch die Laufzeitlogik des Viewers heruntergeladen werden könnten. Stellen Sie insbesondere keine direkte Verknüpfung mit der HTML5 SDK `Utils.js`-Bibliothek aus dem Kontextpfad `/s7viewers` her (auch als konsolidiertes SDK-Include bezeichnet). Die Viewer-Logik verwaltet den Speicherort von `Utils.js` oder ähnlichen Laufzeit-Viewer-Bibliotheken, die sich zwischen Versionen ändern können. Adobe speichert ältere Versionen von sekundären Viewer-Includes nicht auf dem Server, sodass ein direkter Verweis auf diese die Viewer-Funktionalität in zukünftigen Updates beeinträchtigen kann.
* **Einbettungsrichtlinien:**
Verwenden Sie die Dokumentation zum Einbetten von Richtlinien, die für jeden Viewer spezifisch sind.
Möchten Sie mehr erfahren? Navigieren Sie zu [Viewer für AEM Assets](https://experienceleague.adobe.com/de/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/c-html5-s7-aem-asset-viewers).
* **SDK-Tutorial und Beispiele:**
Sehen Sie sich das [Viewer SDK-Tutorial](https://experienceleague.adobe.com/de/docs/dynamic-media-developer-resources/library/c-tutorial) und die [HTML5 SDK-Anwendungsbeispiele](https://s7d9.scene7.com/s7sdk/2024.5/docs/jsdoc/index.html) an, um sich mit den SDK-Komponenten-APIs vertraut zu machen.


## Vorbereiten von Assets für die Bereitstellung

### Organisieren Ihrer Assets

**Business-Case:** *Effizientes Organisieren von Assets, um Workflows zu optimieren.*

Verwenden Sie für eine effiziente Asset-Organisation, die Workflows optimiert, eine oder mehrere der folgenden Best Practices:

* **Organisieren von Assets in Ordnern:**
Eine effektive Organisation von Assets besteht darin, sie in Ordner zu kategorisieren, ähnlich wie bei der Organisation der Dateien auf einem Computer. Die ordnungsgemäße Benennung, Strukturierung von Unterordnern und Dateiverwaltung innerhalb dieser Ordner sind für eine effiziente Verarbeitung der Assets von entscheidender Bedeutung. Durch die Implementierung systematischer Benennungskonventionen und Metadatenpraktiken wird die Nützlichkeit Ihres digitalen Asset-Repositorys maximiert.
Möchten Sie mehr erfahren? Navigieren Sie zu [Organisieren von Assets in Ordnern](/help/assets/organize-assets.md#organize-using-folders).
* **Organisieren von Assets mithilfe von Tags:**
Das Tagging von Assets verbessert die Suchbarkeit, Sammlungserstellung und das Ranking von Suchen. Die KI von Adobe Sensei verwendet einen selbstlernenden Algorithmus für präzises Tagging, das den schnellen Abruf von Assets ermöglicht. Außerdem erkennt Adobe Sensei relevante Tags, einschließlich benutzerdefinierter Tags, und weist sie Assets zu, wodurch das Asset-Management mit automatischem, beschreibendem Tagging vereinfacht wird.
Möchten Sie mehr erfahren? Navigieren Sie zu [Organisieren von Assets mit Tags](/help/assets/organize-assets.md#use-tags-to-organize-assets).
* **Organisieren von Assets als Sammlungen:**
Dynamic Media- und Experience Manager-Assets ermöglichen Benutzenden die effiziente Erstellung, Bearbeitung und Freigabe von Asset-Sammlungen. Sie können verschiedene Sammlungstypen einrichten, einschließlich statischen Listen und dynamischen, suchbasierten Kompilierungen. Diese Sammlungstypen können über verschiedene Standorte hinweg mit anpassbaren Zugriffs- und Bearbeitungsrechten freigegeben werden.
Möchten Sie mehr erfahren? Navigieren Sie zu [Organisieren von Assets als Sammlungen](/help/assets/manage-collections.md).
* **Organisieren von Assets mit Profilen:**
Ein Verarbeitungsprofil automatisiert die Verarbeitung von Assets in angegebenen Ordnern und optimiert so deren Organisation. Durch die Standardisierung von Metadaten, Dateinamen und Ordnerstrukturen können diese Profile konsistent und präzise angewendet werden, wenn Sie Ihre digitale Asset-Sammlung erweitern.
Möchten Sie mehr erfahren? Navigieren Sie zu [Organisieren von Assets mit Profilen](/help/assets/organize-assets.md#organize-to-use-profiles).



### Optimieren der Bildqualität

**Business-Case:** *Erhalten hochwertiger Bilder über Dynamic Media.*

Das Verbessern der Bildqualität erfordert eine sorgfältige Berücksichtigung verschiedener Faktoren. Dies kann ein zeitintensiver Prozess sein. Es gibt jedoch einige bewährte Vorgehensweisen, die Ihnen dabei helfen können, die erwünschten Ergebnisse zu erzielen. Zu diesen Best Practices gehören u. a. der Erhalt einer optimalen Bildgröße, das Scharfzeichnen von Bildern und die Auswahl der bestgeeigneten Bildformate.

Möchten Sie mehr erfahren? Navigieren Sie zu [Best Practices für die Optimierung der Bildqualität](/help/assets/dynamic-media/best-practices-for-optimizing-the-quality-of-your-images.md).

Da die Wahrnehmung der Bildqualität von Mensch zu Mensch variiert, ist manchmal ein systematischer Versuchsansatz unerlässlich, um die erwünschten Ergebnisse zu erzielen. Adobe Experience Manager unterstützt diesen Prozess mit mehr als 100 Dynamic Media-Befehlen zur Bildverbesserung.

Möchten Sie mehr erfahren? Sehen Sie sich [Dynamic Media Snapshot](https://experienceleague.adobe.com/de/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-snapshot) an (3 Minuten, 17 Sekunden).

Um die Auswirkungen dieser verschiedenen Befehle auf die Bildqualität zu bewerten, können Sie ein Bild in Dynamic Media hochladen, die Benutzeroberfläche des Tools unter der angegebenen URL verwenden und die Befehle anwenden, die Sie ausprobieren möchten.

Möchten Sie es einmal ausprobieren? Starten Sie [Dynamic Media Snapshot](https://snapshot.scene7.com/)

### Standardisierung der auf Bilder angewendeten Stile

**Business-Case:** *Effizientes Standardisieren von Stil und Transformation, die auf meine Bild-Assets angewendet werden.*

Verwenden Sie Bildvorgaben regelmäßig in Dynamic Media, damit Sie Größe, Formate und Eigenschaften von Bildern konsistent und dynamisch anpassen können. Sie können sich eine Bildvorgabe als Makro vorstellen: Es handelt sich um einen benannten Satz von Befehlen zur Größenanpassung und Formatierung. Wenn Ihre Site beispielsweise Produktbilder in verschiedenen Größen und Formaten mit spezifischer Komprimierung für Desktop und Mobilgeräte benötigt, automatisieren Bildvorgaben diesen Prozess effizient.

Möchten Sie es einmal ausprobieren? Navigieren Sie zu [Grundlagen der Erstellung von Bildvorgaben zum Rendern von Assets](/help/assets/dynamic-media/dm-journey-part2.md#dm-journey-e)

### Anpassen des Fokus und Framing von Bildern und Videos

**Business-Case:** *Sicherstellen, dass der Zielpunkt meiner Bilder oder Videos geräteübergreifend im Fokus bleibt.*

„Intelligenter Zuschnitt“ ist eine Funktion in Dynamic Media, die Adobe Sensei, Adobes KI und ein Framework für maschinelles Lernen verwendet, um das Zuschneiden von Bildern und Videos zu automatisieren. Sie erkennt das Hauptmotiv oder den Zielpunkt eines Bildes oder Videos intelligent und fokussiert darauf. Mit dieser intelligenten Funktion wird sichergestellt, dass der Fokus auf Desktop-Computern und Mobilgeräten mit unterschiedlichen Bildschirmgrößen unverändert bleibt.

Es empfiehlt sich, mit dem „intelligenten Zuschnitt“ ein Bildprofil zu erstellen. Im Profil können Sie verschiedene Bildschirmgrößen definieren und Adobe Sensei den Rest erledigen lassen. So stellen Sie sicher, dass Ihre Bilder und Videos immer für das Gerät der Betrachtenden optimiert sind.

Möchten Sie mehr erfahren? Sehen Sie sich [Verwenden des intelligenten Zuschnitts mit AEM Assets Dynamic Media](https://experienceleague.adobe.com/de/docs/experience-manager-learn/assets/dynamic-media/images/smart-crop-feature-video-use) (6 Minuten, 35 Sekunden) und [Verwenden des intelligenten Zuschnitts von Dynamic Media für Videos](https://experienceleague.adobe.com/de/docs/experience-manager-learn/assets/dynamic-media/video/dynamic-media-smart-crop-video) (6 Minuten, 22 Sekunden) an.

### Verbessern von SEO-Rankings

**Business-Case:** *Konfigurieren von Dynamic Media, um verbesserte SEO-Rankings zu erhalten.*

Wenden Sie die folgenden Empfehlungen regelmäßig an, um sicherzustellen, dass Ihre Bilder effektiv zu Ihrer SEO-Gesamtstrategie beitragen.

* **Bedeutungstragende Namen von Bilddateien:**
Verwenden Sie beschreibende Dateinamen, die den Bildinhalt widerspiegeln. Zum Beispiel:

   * Verwenden Sie `myCompany-Silver-Wrist-Watch`
   * *vermeiden Sie* `myCompany_Silver_Wrist_Watch` oder `myCompanySilverWristWatch`

  Dies hilft Suchmaschinen dabei, den Bildkontext zu verstehen, und verbessert die SEO. Google bevorzugt in einem Dateinamen Bindestriche gegenüber Unterstrichen oder Leerzeichen. Vermeiden Sie in einem Dateinamen auch die Verkettung von Wörtern.
* **Benutzerdefinierte Domain:**
Implementieren Sie eine benutzerdefinierte Domain, die Ihren Unternehmens- oder Markennamen enthält, um die Markenerkennung und das Vertrauen in die Marke zu stärken. Zum Beispiel:

   * Verwenden Sie `http://images.mycompany.com/is/image/companyname/`
   * *vermeiden Sie* `https://s7d1.scene7.com/is/image/folder/AdobeStock_28563982`

* **SEO-freundliche Ordnerstruktur:**
Organisieren Sie Ihre Bilder in einer Ordnerstruktur, die Ihren Unternehmensnamen oder Ihre Marke enthält, um eine bessere Indizierung zu erzielen, z. B. `http://images.mycompany.com/is/image/companyname/`.
* **Regelsätze in Dynamic Media:**
Erfahren Sie, wie Sie URLs basierend auf verschiedenen Faktoren bedingt transformieren können, um die SEO und das Anwendererlebnis zu verbessern.
Möchten Sie mehr erfahren? Navigieren Sie zu [Verwenden von Regelsätzem zum Transformieren von URLs](/help/assets/dynamic-media/using-rulesets-to-transform-urls.md).
* **Intelligente Bildbearbeitung und intelligenter Zuschnitt:**
Verwenden Sie die Funktionen „Intelligente Bildbearbeitung“ und „Intelligenter Zuschnitt“ in Dynamic Media, um optimierte und responsive Bilder bereitzustellen. Dies verbessert nicht nur die Seitenladezeiten, sondern wirkt sich auch positiv auf SEO-Rankings aus.
Möchten Sie mehr erfahren? Navigieren Sie zu [Intelligente Bildbearbeitung](/help/assets/dynamic-media/imaging-faq.md) oder sehen Sie sich [Verwenden des intelligenten Zuschnitts mit AEM Assets Dynamic Media](https://experienceleague.adobe.com/de/docs/experience-manager-learn/assets/dynamic-media/images/smart-crop-feature-video-use) (6 Minuten, 35 Sekunden) an.

Beachten Sie, dass diese Best Practices besonders auf die Best Practices für die SEO der Bildersuche von Google ausgerichtet sind. Solche Verfahren unterstreichen, wie wichtig es ist, Suchmaschinen durch ordnungsgemäße Namenskonventionen, strukturierte Daten und eine optimierte Bildbereitstellung Kontext und Klarheit zu bieten.

Möchten Sie mehr erfahren? Navigieren Sie zu [Best Practices für die URL-Struktur von Google](https://developers.google.com/search/docs/crawling-indexing/url-structure?hl=de) und [Best Practices für die Bilder-SEO von Google](https://developers.google.com/search/docs/appearance/google-images?hl=de)

### Dynamische Verbesserung von Bildern und Erstellung visueller Effekte mithilfe von Befehlen

**Business-Case:** *Anwenden umfangreicher visueller Effekte auf Bilder.*

Dynamic Media bietet eine Reihe von Befehlen für die dynamische Verbesserung von Bildern und das Erstellen visueller Effekte, ohne dass mehrere statische Assets erforderlich sind. Im Folgenden finden Sie kurze Erklärungen zu einigen dieser Prozesse und mehrere Beispiele, die Sie anleiten sollten:

#### Effekte innerhalb des Quellbilds

| Aufgabe | Vorgehensweise |
| --- | --- |
| **Hochladen und Veröffentlichen des Originalbilds** | <ul><li> Laden Sie zunächst das Originalbild in Dynamic Media hoch.</li><li> Vergewissern Sie sich, dass es veröffentlicht wurde und über eine URL zugänglich ist.</li><li> In diesem Beispiel wird ein Stockbild einer Uhr mit weißem Hintergrund (nennen wir es „Bild X“) in Dynamic Media hochgeladen.<br>[https://s7g2.scene7.com/is/image/genaibeta/watch-silver-offer](https://s7g2.scene7.com/is/image/genaibeta/watch-silver-offer)</li></ul> |
| **Erstellen einer Maske** | <ul><li> Entwickeln Sie eine Maske, die das Motiv (den Bereich, in dem Sie Effekte anwenden möchten) und den Hintergrund (den Bereich, den Sie ändern möchten) definiert.<br>[https://s7g2.scene7.com/is/image/genaibeta/watch-silver-offer-maskps](https://s7g2.scene7.com/is/image/genaibeta/watch-silver-offer-maskps)</li><li> Masken sind in der Regel Graustufenbilder, wobei Weiß das Motiv und Schwarz den Hintergrund darstellt. Sie können Masken mit Tools wie Adobe Photoshop erstellen.<br>Möchten Sie mehr erfahren? Navigieren Sie zu [Erstellen und Bearbeiten einer schnellen Maske in Photoshop](https://helpx.adobe.com/de/photoshop/using/create-temporary-quick-mask.html).</li><li> Erstellen Sie für „Bild X“ eine Maske, die genau das Motiv konturiert, das Sie optimieren möchten. Beispiel: eine Person oder ein Objekt.</li></ul> |
| **Anwenden von URL-Befehlen in Dynamic Media für Effekte** | Nachdem Sie Ihre Maske erstellt haben, verwenden Sie URL-Befehle, um Effekte wie „Schein nach außen“ anzuwenden oder die Hintergrundfarbe auf „Bild X“ zu ändern. Im Folgenden finden Sie zwei Beispiele:<ul><li> **Effekt „Schein nach außen“:**<br> Um den Effekt „Schein nach außen“ entlang des Motivrands hinzuzufügen, bearbeiten Sie die URL wie folgt:<br>[https://s7g10.scene7.com/is/image/genaibeta/watch-silver-offer?mask=watch-silver-offer-maskps&amp;maskUse=invert&amp;effect=-1&amp;pos=100,100&amp;op_blur=75&amp;op_grow=1&amp;opac=25](https://s7g10.scene7.com/is/image/genaibeta/watch-silver-offer?mask=watch-silver-offer-maskps&amp;maskUse=invert&amp;effect=-1&amp;pos=100,100&amp;op_blur=75&amp;op_grow=1&amp;opac=25)<br>In dieser URL erzeugen die Parameter `op_blur`, `op_grow` und `opac` den Effekt „Schein nach außen“.</li><li> **Ändern der Hintergrundfarbe:**<br> Um die Hintergrundfarbe zu ändern, verwenden Sie die URL mit einem anderen Wert für die Hintergrundfarbe:<br>[https://s7g10.scene7.com/is/image/genaibeta/watch-silver-offer?mask=watch-silver-offer-maskps&amp;maskUse=invert&amp;maskUse=invert&amp;color=255,255,0](https://s7g10.scene7.com/is/image/genaibeta/watch-silver-offer?mask=watch-silver-offer-maskps&amp;maskUse=invert&amp;maskUse=invert&amp;color=255,255,0)<br> In diesem Beispiel setzt `color=255,255,0` die Hintergrundfarbe auf Gelb. Ändern Sie für visuelle Auswirkungen den Hintergrund in eine bestimmte Farbe.</li></ul> |

#### Hinzufügen eines Bildrands

Mit Dynamic Media können Sie Bilder direkt über URLs bearbeiten, wodurch es zu einem leistungsstarken Tool für die Erstellung dynamischer digitaler Erlebnisse wird. Im Folgenden finden Sie einige Beispiele. Beginnen wir mit der folgenden URL des Originalbilds: [https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel](https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel).

| Aufgabe | Vorgehensweise |
| --- | --- |
| **Weißer Rahmen** | Verwenden Sie die folgende URL, um einen weißen Rahmen hinzuzufügen:<br>[https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel?size=400,400&amp;extend=10,10,10,10](https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel?size=400,400&amp;extend=10,10,10,10)<br>Unter dieser URL legt der Parameter `extend=10,10,10,10` die Rahmengröße von zehn Pixeln an allen Seiten fest. |
| **Unschärfe entlang des weißen Rahmens** | Um einen Unschärfe-Effekt entlang des weißen Rahmens hinzuzufügen, können Sie die URL wie folgt bearbeiten:<br>[https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel?size=400,400&amp;extend=10,10,10,10&amp;effect=-1&amp;op_blur=60&amp;color=0,0,0](https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel?size=400,400&amp;extend=10,10,10,10&amp;effect=-1&amp;op_blur=60&amp;color=0,0,0)<br>Unter dieser URL wendet der Parameter `effect=-1` den Unschärfe-Effekt an und `op_blur=60` steuert die Intensität der Unschärfe. |
| **Schlagschatteneffekt entlang des äußeren Rands** | Verwenden Sie diese URL, um einen Schlagschatteneffekt entlang des äußeren Rands hinzuzufügen:<br>[https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel?size=400,400&amp;extend=10,10,10,10&amp;effect=-1&amp;$shadow$&amp;color=0,0,0](https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel?size=400,400&amp;extend=10,10,10,10&amp;effect=-1&amp;$shadow$&amp;color=0,0,0)<br> Der Parameter `$shadow$` erstellt den Schatteneffekt und `color=0,0,0` setzt die Schattenfarbe auf Schwarz. |

Experimentieren Sie mit diesen URLs, um die gewünschten visuellen Effekte zu erzielen.

#### Erstellen von Bildüberlagerungen

Wenn Sie ein Logo oder Symbol als Überlagerung auf einem vorhandenen Bild platzieren möchten, bietet Dynamic Media eine einfache Möglichkeit, dies mithilfe von URL-Befehlen zu erreichen. Sehen wir uns die einzelnen Schritte an.

| Schritt | Vorgehensweise |
| --- | --- |
| **Hochladen und Veröffentlichen des Basisbilds** | Laden Sie zunächst das Basisbild hoch, das Sie mit dem Logo oder Symbol überlagern möchten, und veröffentlichen Sie es. Sie können jedes Bild als Basis verwenden.<br>Hier ist beispielsweise ein Basisbild:<br>[https://s7g2.scene7.com/is/image/genaibeta/decorative-room-sofa](https://s7g2.scene7.com/is/image/genaibeta/decorative-room-sofa). |
| **Hochladen und Veröffentlichen des Logos oder Symbolbilds** | Laden Sie anschließend das Bild hoch, mit dem Sie das Basisbild überlagern möchten, und veröffentlichen Sie es. Dieses Bild sollte eine transparente PNG-Datei mit dem Logo oder Symbol sein, das Sie überlagern möchten.<br>Hier ist das transparente PNG-Bild eines Sternobjekts mit Transparenzeffekten, das überlagert werden soll:<br>[https://s7g2.scene7.com/is/image/genaibeta/decorate-star](https://s7g2.scene7.com/is/image/genaibeta/decorate-star) |
| **Anwenden der Dynamic Media-URL** | Erstellen Sie jetzt eine Dynamic Media-URL, die das Basisbild mit dem Logo oder Symbolbild kombiniert. Sie können URL-Befehle verwenden, um diesen Effekt zu erzielen.<br>Die URL-Struktur sieht etwa so aus:<br>[https://s7g2.scene7.com/is/image/genaibeta/decorative-room-sofa?layer=1&amp;src=decorate-star&amp;scale=1.25&amp;posN=0.33,-.25&amp;fmt=png](https://s7g2.scene7.com/is/image/genaibeta/decorative-room-sofa?layer=1&amp;src=decorate-star&amp;scale=1.25&amp;posN=0.33,-.25&amp;fmt=png)<br>wobei das Asset<ul><li> `hotspotRetailBaseImage` das Basisbild ist.</li><li> `starxp` ist das Logo/Symbolbild.</li><li> `layer=1` gibt an, dass das Logo oder Symbol über dem Basisbild platziert werden soll.</li><li> `scale=1.25` passt die Größe des Logos/Symbols an.</li><li> `posN=0.33,-.25` bestimmt die Position des Logos/Symbols relativ zum Basisbild.</li><li> `fmt=png` stellt sicher, dass die Ausgabe im PNG-Format vorliegt.</li></ul> |

Möchten Sie mehr erfahren? Navigieren Sie zu [src](https://experienceleague.adobe.com/de/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-src), um mehr über den `src`-Befehl und andere URL-Befehle in Dynamic Media zu erfahren.


#### Überlagern von Werbetext

Im Folgenden werden die Schritte zum Überlagern eines Bilds mit einer Werbetext-Nachricht mithilfe von HTML und CSS beschrieben.

| Schritt | Vorgehensweise |
| --- | --- |
| **Hochladen und Veröffentlichen des Basisbilds** | Laden Sie zunächst das Basisbild hoch, das Sie mit dem Text überlagern möchten, und veröffentlichen Sie es. Sie können jedes beliebige Bild verwenden. Hier finden Sie ein Beispiel für ein Basisbild:<br>[https://s7g2.scene7.com/is/image/genaibeta/leather-sofa](https://s7g2.scene7.com/is/image/genaibeta/leather-sofa)<br> |
| **Anwenden von Textoperatoren in Dynamic Media** | Mit Dynamic Media können Sie Textoperatoren anwenden, um das Bild direkt mit dynamischem Text zu überlagern. Die folgende Beispiel-URL zeigt diese Fähigkeit:<br>[https://s7g10.scene7.com/is/image/genaibeta/leather-sofa?layer=1&amp;posN=-0.3,-0.455&amp;text=%7b\rtf1\ansi%7b\fonttbl%7b\f0+Arial;%7d%7d%7b\colortbl+\red255\green255\blue255;%7d\copyfit1000\vertalc\qc%7b\cf0\fs42+New+Collection%7d%7d&amp;size=370,70&amp;textAttr=130&amp;bgcolor=FF3333&amp;wid=600&amp;hei=600](https://s7g10.scene7.com/is/image/genaibeta/leather-sofa?layer=1&amp;posN=-0.3,-0.455&amp;text=%7b\rtf1\ansi%7b\fonttbl%7b\f0+Arial;%7d%7d%7b\colortbl+\red255\green255\blue255;%7d\copyfit1000\vertalc\qc%7b\cf0\fs42+New+Collection%7d%7d&amp;size=370,70&amp;textAttr=130&amp;bgcolor=FF3333&amp;wid=600&amp;hei=600) |

#### Größenänderungen und Zuschneiden für verschiedene Anwendungsfälle

##### Grundlagen zum Ändern der Bildgröße

Das Ändern der Bildgröße umfasst das Ändern der Abmessungen, Auflösung und Dateigröße eines Bildes. Beachten Sie dabei Folgendes:

* **Pixelzusammensetzung:**
Digitale Bilder bestehen aus winzigen Punkten, die Pixel genannt werden. Wenn ein Bild erstellt wird, hat es eine bestimmte Anzahl Pixel. Bei der Größenanpassung werden Pixel hinzugefügt oder entfernt, um die Abmessungen, Auflösung und Dateigröße des Bildes zu ändern.
* **Seitenverhältnis:**
Die Beibehaltung des Seitenverhältnisses (das Verhältnis zwischen Breite und Höhe) ist entscheidend, um Verzerrungen zu vermeiden. Unabhängig davon, ob Sie ein Bild vergrößern (Upscaling) oder verkleinern (Downscaling), wird durch die Beibehaltung des Seitenverhältnisses die visuelle Konsistenz gewährleistet.
* **Aspekte bezüglich der Qualität:**
Die Größenanpassung kann sich auf die Bildqualität auswirken. Vermeiden Sie ein zu drastisches Vergrößern, da dieses zu einer Verpixelung führen kann. Ziehen Sie stattdessen in Erwägung, das Bild in einer größeren Größe und Auflösung zu reproduzieren. Verwenden Sie für kleinere Bilder die entsprechenden Tools, um die Auflösung beizubehalten.

##### Zuschneiden versus Größenanpassung

Zuschneiden und Größenanpassung sind zwei Techniken in Dynamic Media, mit denen Sie Bilder für verschiedene Anwendungsfälle transformieren können, zum Beispiel für das Erstellen von Miniaturansichten, Produktanzeigebildern oder Bannern.

* **Zuschneiden:**
Umfasst das Entfernen eines Teils eines Bildes, um dessen Komposition und Ausschnitt zu ändern. Die Gesamtdimensionen werden nicht geändert, sondern es wird auf einen bestimmten Bereich fokussiert.
* **Größenänderung:**
Passt die Abmessungen, Auflösung und Dateigröße des gesamten Bildes unter Beibehaltung des Seitenverhältnisses an.

Sehen wir uns einen Anwendungsfall mit folgendem Bild eines Wohnzimmers an:

* **Original-Wohnzimmerbild:**
  [https://s7g2.scene7.com/is/image/genaibeta/decorative-room-sofa](https://s7g2.scene7.com/is/image/genaibeta/decorative-room-sofa)
* **Miniaturansicht (200 Pixel x 200 Pixel):**
Eine kleinere Version, die für schnelles Laden/Anzeigen geeignet ist.
  [https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=200&amp;hei=200&amp;fit=crop](https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=200&amp;hei=200&amp;fit=crop)
* **Miniaturansicht mit Zuschnitt (200 x 200 Pixel):**
Mit Fokus auf den Bereich mit dem Sofa zugeschnitten.
  [https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=200&amp;hei=200&amp;cropN=.24,.24,.6,.72&amp;fit=crop](https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=200&amp;hei=200&amp;cropN=.24,.24,.6,.72&amp;fit=crop)
* **Produktanzeigebild (800 x 600 Pixel):**
Zum Präsentieren des Sofas zugeschnitten und in der Größe angepasst.
  [https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=800&amp;hei=600&amp;cropN=.24,.24,.6,.72&amp;fit=crop](https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=800&amp;hei=600&amp;cropN=.24,.24,.6,.72&amp;fit=crop)
* **Banner (1720 x 820 Pixel):**
Abgeleitet vom Originalbild, wobei der Raum betont wird.
  [https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=1720&amp;hei=820&amp;cropN=0,.1,1,1&amp;fit=crop](https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=1720&amp;hei=820&amp;cropN=0,.1,1,1&amp;fit=crop)

Probieren Sie diese Varianten für Ihre speziellen Anforderungen ruhig aus.
Möchten Sie mehr über die Befehle erfahren, die in einer URL verfügbar sind? Navigieren Sie zur [Befehlsreferenz](https://experienceleague.adobe.com/de/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference).

### Bereitstellen von GIF-Bildern

**Business-Case:** *Streamen von GIFs mit Dynamic Media*

Sie können GIFs über Dynamic Media hochladen und bereitstellen. Um ein animiertes GIF zu rendern, ersetzen Sie in der URL `is/image` durch `is/content`. Wenn Sie beispielsweise `abc.gif` hochgeladen haben, verwenden Sie Folgendes:

* Dieser URL-Pfad rendert eine statische Ansicht des GIF:

  ```
  https://your.domain.com/is/image/yourfolder/abc
  ```

* Dieser URL-Pfad rendert die Animationsansicht des GIF:

  ```
  https://your.domain.com/is/content/yourfolder/abc
  ```

>[!NOTE]
>
>Bei Verwendung von `is/content` im URL-Pfad werden Bildumwandlungsbefehle nicht auf das Asset angewendet.

### Veröffentlichen eines Videos für meine Website

**Business-Case:** *Veröffentlichen Sie schnell ein Video für eine Marketing-Site.*

* **Auswählen eines Videoprofils:**
Zunächst sollten Sie in Dynamic Media ein geeignetes Videoprofil auswählen. Sie können das Profil *Adaptive Videoverschlüsselung* auswählen, das in AEM Assets unter „Videoprofile“ verfügbar ist. Diese vordefinierten Verschlüsselungsseinstellungen stellen sicher, dass Ihr Video für die Wiedergabe auf verschiedenen Geräten und unter verschiedenen Bandbreitenbedingungen optimiert ist. Alternativ können Sie auch Ihr eigenes Profil für adaptive Videos erstellen.
* **Zuweisen des Profils:**
Weisen Sie das ausgewählte Videoprofil den Ordnern zu, in die das Video hochgeladen werden soll. Dieser Schritt stellt sicher, dass beim Hochladen die richtigen Verschlüsselungseinstellungen angewendet werden.
* **Hochladen des Originalvideos:**
Laden Sie die Originalvideodatei hoch. Stellen Sie sicher, dass es sich um ein hochauflösendes Video mit guter Qualität handelt. Je besser das Quellvideo, desto besser das Endergebnis.
* **Erstellen der Vorschau und Veröffentlichen:**
Erstellen Sie eine Vorschau des Videos, um sicherzustellen, dass alles wie erwartet aussieht. Sobald Sie zufrieden sind, veröffentlichen Sie das Video. Dadurch wird das Video für Ihre Zielgruppe zugänglich.
* **Verknüpfen oder Einbetten:**
Nach der Veröffentlichung haben Sie zwei Optionen.

   * **Direktes Verknüpfen:**
Verwenden Sie die bereitgestellte URL, um eine direkte Verknüpfung zum Video herzustellen. Verknüpfen Sie es entsprechend mit einem Hyperlink auf Ihrer Marketing-Site.
   * **Einbetten des Videos:**
Kopieren Sie den bereitgestellten Einbettungs-Code und fügen Sie ihn in das HTML Ihrer Web-Seite ein, auf der das Video angezeigt werden soll. Hierdurch kann das Video direkt auf Ihrer Site wiedergegeben werden.

Möchten Sie mehr erfahren? Navigieren Sie zu [Video](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/dynamicmedia/video).

### Konfigurieren von Videos für optimale Qualität und Interaktion

**Business-Case:** *Richten Sie Videos für die beste Qualität und Interaktion ein.*

Um die bestmögliche Qualität und Interaktion für Ihre Videos sicherzustellen, sollten Sie eine Kombination der folgenden Strategien implementieren, die Best Practices darstellen:

* **Verwenden des integrierten HTML5-Video-Viewers:**
Die HTML5-Video-Viewer-Vorgaben in Dynamic Media sind robuste Video-Player. Verwenden Sie diese, um häufig auftretende Probleme im Zusammenhang mit der Wiedergabe von HTML5-Videos und Mobilgeräten zu vermeiden.
Diese Vorgaben gehen Herausforderungen wie die Bereitstellung von adaptivem Bitrate-Streaming oder die eingeschränkte Reichweite eines Desktop-Browsers an.
Möchten Sie mehr erfahren? Navigieren Sie zu [Best Practice: Verwenden des HTML 5-Video-Viewers](/help/assets/dynamic-media/video.md#best-practice-using-the-html-video-viewer).

* **Verwenden von Dynamic Media-Videoprofilen:**
Videoprofile in Dynamic Media helfen Ihnen, eine effiziente Videoverwaltung und konsistente Qualität zu erzielen und adaptives Streaming anzuwenden.
Möchten Sie mehr erfahren? Navigieren Sie zu [Dynamic Media-Videoprofile](/help/assets/dynamic-media/video-profiles.md).

* **Befolgen der Best Practices für die Videoverschlüsselung:**
Wenden Sie Videoverschlüsselungsprofile an, die die Originalvideoqualität ohne übermäßiges Downscaling während der Kodierung beibehalten.
Möchten Sie mehr erfahren? Navigieren Sie zu [Best Practices für die Verschlüsselung von Videos](/help/assets/dynamic-media/video.md#best-practices-for-encoding-videos).

* **Anwenden von adaptivem Streaming anstelle von progressivem Streaming:**
Beim adaptiven Streaming wird die Videoqualität basierend auf der Geschwindigkeit der Internet-Verbindung und den Gerätefunktionen der Betrachtenden angepasst.
Es verwendet Protokolle wie HLS (HTTP Live Streaming) oder DASH (`Dynamic Adaptive Streaming over HTTP`), um eine optimale Wiedergabequalität sicherzustellen.
Im Gegensatz zu progressivem Streaming, bei dem Videos linear bereitgestellt werden, minimiert das adaptive Streaming die Pufferung und bietet ein nahtloses Zuschauererlebnis.

### Internationalisierung von Videos für den mehrsprachigen Gebrauch

**Business-Case:** *Richten Sie Videos auf den mehrsprachigen Gebrauch aus.*

Die Internationalisierung von Videos für den mehrsprachigen Gebrauch ist für das Erreichen einer globalen Zielgruppe von entscheidender Bedeutung. Dynamic Media bietet Funktionen, die Ihnen bei der Erreichung dieses Ziels helfen können.

* **Hochladen Ihrer Videos:**
   * Erstellen Sie zunächst ein Videoverschlüsselungsprofil. Sie können entweder das vordefinierte und bereits in Dynamic Media integrierte Profil „Adaptive Videoverschlüsselung“ verwenden oder Ihr eigenes benutzerdefiniertes Profil erstellen.
   * Verknüpfen Sie das Videoverarbeitungsprofil mit den Ordnern, in die Sie die Primärvideos hochladen.
   * Laden Sie die Primärvideos in diese Ordner hoch. Dynamic Media verschlüsselt sie basierend auf dem zugewiesenen Videoverarbeitungsprofil.
   * Dynamic Media unterstützt hauptsächlich Kurzvideos (bis zu 30 Minuten) und einer Mindestauflösung von 25 x 25. Es können Videodateien mit einer Größe von bis zu 15 GB hochgeladen werden1.

* **Verwalten von Videos:**
   * In AEM können Sie Video-Assets organisieren, suchen und durchsuchen.
   * Zeigen Sie Video-Assets in der Vorschau an und veröffentlichen Sie sie.
   * Zeigen Sie das Quellvideo und seine kodierten Ausgabeformate zusammen mit den zugehörigen Miniaturansichten an.
   * Bearbeiten Sie Videoeigenschaften wie Titel, Beschreibung und Tags2.

* **Lokalisierung:**
   * Erstellen Sie Audiospuren und Untertitel für jede Zielregion/Sprache.
   * Fügen Sie diese Audio- und Untertitelspuren über die AEM-Oberfläche zu Ihren Videos hinzu.
   * Wenn Benutzende die Videos abspielen, können sie ihre bevorzugte Sprache für Audio und Untertitel auswählen.

* **Veröffentlichen:**
   * Wenn Sie AEM als Ihr WCM-System (Web Content Management) verwenden, können Sie Ihren Web-Seiten direkt Videos hinzufügen.
   * Wenn Sie das WCM-System eines Drittanbieters verwenden, können Sie Videos mithilfe von URLs oder Einbettungs-Codes auf Ihren Web-Seiten verknüpfen oder einbetten.

Möchten Sie mehr erfahren? Navigieren Sie zu [Unterstützung für mehrfache Untertitel und Audiospuren bei Videos in Dynamic Media](/help/assets/dynamic-media/video.md#about-msma) oder sehen SIe sich [Hinzufügen mehrfacher Untertitel und Audiospuren zu einem Video](https://delivery-p106302-e1008131.adobeaemcloud.com/adobe/assets/urn:aaid:aem:daf9a222-9f7f-4333-b167-98cb4c63a1f8/play) an (1 Minute, 41 Sekunden).


## Bereitstellen von Assets an Kundinnen und Kunden

### Optimieren von Bildgrößen und Minimieren der Seitenladezeiten

**Business-Case:** *Optimieren Sie die Größe von Bildern für Browser oder Bildschirme und reduzieren Sie die Seitenladezeit.*

Die intelligente Bildbearbeitung in Dynamic Media ist ein leistungsstarkes Tool, das die Leistung bei der Bildbereitstellung verbessert, indem Format, Größe und Qualität des Bildes automatisch auf Grundlage der Browser-Funktionen der Kundin oder des Kunden optimiert werden.

Adobe empfiehlt, die Funktionen der intelligenten Bildbearbeitung zu verwenden, anstatt das Bildformat manuell auf `webp` oder `avif` zu setzen. Hier sind die Gründe:

* **Browser-Kompatibilität:**
Die intelligente Bildbearbeitung stellt sicher, dass das bereitgestellte Bildformat mit dem Browser der Benutzenden kompatibel ist.
* **Optimale Komprimierung:**
Basierend auf dem jeweiligen Browser, den Netzwerkbedingungen und der Bildschirmauflösung wird das beste Komprimierungsformat ausgewählt.
* **Moderne Formate:**
Zwar ist `avif` ist ein neueres Format, das eine bessere Komprimierung bietet, jedoch wird es noch nicht allgemein in allen Browsern unterstützt.
* **Best Practices:**
Um das beste Web-optimierte Format zu gewährleisten, können Sie auf die Auswahl der intelligenten Bildbearbeitung vertrauen, anstatt die Befehle `fmt=webp` oder `fmt=avif` manuell zu verwenden.

Mithilfe der intelligenten Bildbearbeitung können Sie sicherstellen, dass Ihre Bilder so effizient wie möglich und auf die Browser-Umgebung der jeweiligen Benutzenden zugeschnitten bereitgestellt werden. Dieser Ansatz vereinfacht den Prozess und kann zu einer verbesserten Leistung in Bezug auf die Ladezeiten von Bildern und das gesamte Anwendererlebnis führen.

Möchten Sie mehr erfahren? Navigieren Sie zu [Intelligente Bildbearbeitung](/help/assets/dynamic-media/imaging-faq.md).

### Änderungen nach der Bereitstellung von Assets an Kundinnen und Kunden

**Business-Case:** *Wie kann sichergestellt werden, dass die Änderungen sofort im CDN erscheinen, nachdem neue Inhalte veröffentlicht oder vorhandene Inhalte überschrieben wurden?*

Das CDN (Content Delivery Network) speichert Dynamic Media-Assets für die schnelle Bereitstellung an Kundinnen und Kunden zwischen. Wenn an diesen Assets Aktualisierungen vorgenommen werden, ist es wichtig, dass die Änderungen sofort auf der Website wirksam werden. Indem der CDN-Cache bereinigt oder ungültig gemacht wird, können von Dynamic Media bereitgestellte Assets schnell aktualisiert werden. Dadurch entfällt die Notwendigkeit, auf den Ablauf des Caches basierend auf dem TTL-Wert (Time To Live) zu warten, der normalerweise auf zehn Stunden festgelegt ist. Je nach Anwendungsfall können Sie die Einstellungen für den TTL-Wert (Time to Live) des CDN entsprechend aktualisieren.

Möchten Sie mehr erfahren? Navigieren Sie zu [Invalidierung des CDN-Cache mithilfe von Dynamic Media](/help/assets/dynamic-media/invalidate-cdn-cache-dynamic-media.md).

