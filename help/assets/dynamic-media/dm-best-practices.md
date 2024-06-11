---
title: Best Practices in Dynamic Media
description: Erfahren Sie mehr über Best Practices in Dynamic Media beim Arbeiten mit Bildern und Videos.
contentOwner: Rick Brough
products: Experience Manager as a Cloud Service
topic-tags: introduction,administering
content-type: reference
feature: Video,Renditions, Configuration, Asset Management, Best Practices
role: User, Admin
mini-toc-levels: 4
hide: false
hidefromtoc: false
source-git-commit: 8c05fecf6bd82eebd529c826d6767e3366f3ec71
workflow-type: tm+mt
source-wordcount: '3574'
ht-degree: 0%

---

# Informationen zu Best Practices in Dynamic Media{#about-dm-best-practices}

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

Unternehmen stehen vor einer Explosion von Kanälen und Geräten zur Interaktion mit Benutzern. Die Journey umfasst physische Stores, Web, Mobilgeräte, Social Media, E-Mails und Commerce. Um diese Nachfrage zu decken, bietet Dynamic Media on Adobe Experience Manager (AEM) eine umfassende Lösung. Sie optimiert die Asset-Bereitstellung, handhabt die Personalisierung und sorgt für konsistente, leistungsfähige und markenorientierte Erlebnisse über Kanäle und Geräte hinweg.

Zu den wichtigsten Grundsätzen von Dynamic Media gehören:

* **Einzeldateiansatz:** Mit Dynamic Media speichern Sie eine Primärquelldatei. Alle Größenvarianten und visuellen Effekte werden zum Zeitpunkt der Bereitstellung dynamisch erstellt und optimiert. Dieser Ansatz spart Speicherkosten und beseitigt die Komplexität des Workflows.
* **Wirklich global:** Die intelligente Bildbearbeitung, die während der Inhaltsbereitstellung angewendet wird, reduziert die Bildgröße und Seitengröße erheblich, ohne die visuelle Qualität zu beeinträchtigen. Sie ist für Netzwerkbandbreite und Gerätepixelverhältnisse optimiert.
* **KI-gestützt:** Smartes Zuschneiden, eine KI-gesteuerte Funktion, automatisiert das Zuschneiden von Bild- und Videopunkten. Dadurch entfällt manueller Aufwand und skaliert effizient für die Verwendung in Unternehmen.
* **Einfaches Video:** Laden Sie Primärvideos in Dynamic Media hoch und streamen Sie sie mit beschreibendem Audio über mehrere Sprachen hinweg adaptiv an.
* **Experience Viewer-Bibliothek:** Anpassen und Markieren von Erlebnis-Viewern für Bilder und Videos. Diese Viewer lassen sich nahtlos in Ihre digitalen Erlebnisse integrieren.
* **Unterstützung neuer Formate:** Dynamic Media ermöglicht die Bereitstellung von 3D- und Panoramamedien.

Während Sie die [Dynamic Media Journey](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/dm-journey/dm-journey-part1)können Sie die unten stehende konsolidierte Liste mit Best Practices überprüfen, um die Funktionen optimal zu nutzen. Passen Sie diese Best Practices für Dynamic Media an Ihre spezifischen Kontext- und Projektanforderungen an, damit Sie Ihre Erlebnisse kanalübergreifend und geräteübergreifend optimieren können.

<!-- In Dynamic Media on AEM, there are sets of methods, techniques, and guidelines that can help you maximize the potential of your rich media content. These best practices can lead to optimal results and increase efficiency in your use of Dynamic Media. They represent the most efficient and effective courses of action in a particular situation. They also unlock high value for your audience and deliver high-quality, engaging content. -->

>[!IMPORTANT]
>
>Die Best Practices der Dynamic Media in diesem Artikel können sich im Laufe der Zeit weiterentwickeln, wenn neue Technologien in Dynamic Media entstehen. Die folgenden Informationen beziehen sich auf die neueste Version von Dynamic Media.


## Aufnehmen von Assets in Dynamic Media

**Geschäftsfall:** *Effiziente Verwaltung großer Asset-Volumen und Sicherstellung, dass nur relevante, genehmigte Inhalte an Endbenutzer bereitgestellt werden.*

Optimieren Sie die Verwaltung einer großen Anzahl von Assets effizient. Stellen Sie sicher, dass nur die entsprechenden autorisierten Inhalte Ihre Endbenutzer erreichen, indem Sie die von Dynamic Media verwendete **Selektive Synchronisierung** und **Selektive Veröffentlichung** Funktionen.

* **Selektive Synchronisierung:**
Eine proaktive Funktion, mit der Sie auswählen können, welche Assets mit Dynamic Media synchronisiert werden sollen. Sie können beispielsweise nur die Ordner synchronisieren, die Assets enthalten, für die die endgültige Genehmigung erteilt wurde. Dieser Workflow hilft Ihnen dabei, die Kontrolle darüber zu behalten, welche Assets für die Bereitstellung an Ihre Kunden vorbereitet werden.

* **Selektive Veröffentlichung:**
Nach der Synchronisierung Ihrer Assets können Sie durch die selektive Veröffentlichung steuern, welche Assets für Ihre Kunden sichtbar sind. Auf diese Weise können Sie steuern, welche genehmigten Assets tatsächlich über Ihre Kanäle bereitgestellt werden, und sicherstellen, dass Ihre Kunden nur die besten und relevantesten Inhalte sehen.

Mithilfe dieser beiden Best Practices können Sie eine bessere Kontrolle, Verwaltung und Produktivität Ihrer Rich-Media-Inhalte erzielen.

Möchten Sie mehr erfahren? Navigieren Sie zu [Konfigurieren der selektiven Veröffentlichung auf Ordnerebene in Dynamic Media](/help/assets/dynamic-media/selective-publishing.md).


## Vorbereiten von Assets für die Bereitstellung

### Organisieren von Assets

**Geschäftsfall:** *Effiziente Organisation von Assets zur Optimierung von Workflows.*

Verwenden Sie für eine effiziente Asset-Organisation, die Workflows optimiert, eine oder mehrere der folgenden Best Practices:

* **Organisieren von Assets in Ordnern:**
Die effektive Organisation von Assets besteht darin, sie in Ordner zu kategorisieren, ähnlich wie bei der Dateiorganisation auf einem Computer. Ordnungsgemäße Benennung, Strukturierung von Unterordnern und Dateiverwaltung innerhalb dieser Ordner sind für eine effiziente Asset-Verarbeitung von entscheidender Bedeutung. Durch die Implementierung systematischer Benennungskonventionen und Metadatenpraktiken wird die Nützlichkeit Ihres digitalen Asset-Repositorys maximiert.
Möchten Sie mehr erfahren? Navigieren Sie zu [Organisieren von Assets in Ordnern](/help/assets/organize-assets.md#organize-using-folders).
* **Organisieren Sie Assets mithilfe von Tags:**
Das Tagging von Assets verbessert die Suchbarkeit, Sammlungserstellung und Suchranking. Adobe Senseis KI verwendet einen selbstlernenden Algorithmus für präzises Tagging, der den schnellen Abruf von Assets ermöglicht. Adobe Sensei erkennt und weist relevante Tags, einschließlich benutzerdefinierter Tags, Assets zu, vereinfacht die Asset-Verwaltung durch automatisches, beschreibendes Tagging.
Möchten Sie mehr erfahren? Navigieren Sie zu [Organisieren von Assets mit Tags](/help/assets/organize-assets.md#use-tags-to-organize-assets).
* **Organisieren von Assets als Sammlungen:**
Dynamic Media und Experience Manager Assets ermöglichen die effiziente Erstellung, Bearbeitung und Freigabe von Asset-Sammlungen für Benutzer. Sie können verschiedene Sammlungstypen einrichten, einschließlich statische Listen und dynamische, suchbasierte Kompilierungen. Diese Sammlungstypen können an verschiedenen Standorten mit anpassbaren Zugriffs- und Bearbeitungsrechten freigegeben werden.
Möchten Sie mehr erfahren? Navigieren Sie zu [Organisieren von Assets als Sammlungen](/help/assets/manage-collections.md).
* **Organisieren von Assets mit Profilen:**
Ein Verarbeitungsprofil automatisiert die Asset-Verarbeitung in angegebenen Ordnern und optimiert so die Organisation. Durch die Standardisierung von Metadaten, Dateinamen und Ordnerstrukturen können diese Profile konsistent und präzise angewendet werden, wenn sich Ihre digitale Asset-Sammlung erweitert.
Möchten Sie mehr erfahren? Navigieren Sie zu [Organisieren von Assets mit Profilen](/help/assets/organize-assets.md#organize-to-use-profiles).

### Bildqualität optimieren

**Geschäftsfall:** *Erhalten Sie hochwertige Bilder von Dynamic Media.*

Die Verbesserung der Bildqualität erfordert eine sorgfältige Berücksichtigung verschiedener Faktoren. Dies kann ein zeitintensiver Prozess sein. Es gibt jedoch einige bewährte Vorgehensweisen, die Ihnen dabei helfen können, wünschenswerte Ergebnisse zu erzielen. Zu diesen Best Practices gehören u. a. das Abrufen einer optimalen Bildgröße, das Scharfzeichnen von Bildern und die besten zu verwendenden Bildformate.

Möchten Sie mehr erfahren? Navigieren Sie zu [Best Practices zur Optimierung der Bildqualität](/help/assets/dynamic-media/best-practices-for-optimizing-the-quality-of-your-images.md).

Da die Wahrnehmung der Bildqualität von Mensch zu Mensch variiert, ist manchmal ein systematischer Experimentationsansatz unerlässlich, um erwünschte Ergebnisse zu erzielen. Adobe Experience Manager unterstützt diesen Prozess mit mehr als 100 Dynamic Media-Befehlen zur Bildverbesserung.

Möchten Sie mehr erfahren? Watch [Dynamic Media-Schnappschuss](https://experienceleague.adobe.com/en/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-snapshot) (3 Minuten, 17 Sekunden).

Um die Auswirkungen dieser verschiedenen Befehle auf die Bildqualität zu bewerten, können Sie ein Bild in Dynamic Media hochladen, die Benutzeroberfläche des Tools unter der angegebenen URL verwenden und die Befehle anwenden, die Sie ausprobieren möchten.

Willst du es ausprobieren? Launch [Dynamic Media-Schnappschuss](https://snapshot.scene7.com/)

### Standardisierung der Stile, die auf Bilder angewendet werden

**Geschäftsfall:** *Standardisieren Sie effizient den Stil und die Transformation, die auf meine Bild-Assets angewendet werden.*

Verwenden Sie Bildvorgaben regelmäßig in Dynamic Media, damit Sie Bildgrößen, Formate und Eigenschaften konsistent und dynamisch anpassen können. Stellen Sie sich eine Bildvorgabe als Makro vor: Es handelt sich um einen benannten Satz von Befehlen zur Größenanpassung und Formatierung. Wenn Ihre Site beispielsweise Produktbilder in verschiedenen Größen und Formaten benötigt, mit spezifischer Komprimierung für Desktop und Mobilgeräte, automatisieren Bildvorgaben diesen Prozess effizient.

Willst du es ausprobieren? Navigieren Sie zu [Grundlagen zum Erstellen von Bildvorgaben zum Rendern von Assets](/help/assets/dynamic-media/dm-journey-part2.md#dm-journey-e)

### Fokus und Frame von Bildern und Videos anpassen

**Geschäftsfall:** *Stellen Sie sicher, dass der Hauptzielpunkt meiner Bilder oder Videos geräteübergreifend im Fokus bleibt.*

Smartes Zuschneiden ist ein Feature-Tool in Dynamic Media, das Adobe Sensei, Adobe AI und maschinelles Lernen verwendet, um das Zuschneiden von Bildern und Videos zu automatisieren. Intelligente Erkennung und Fokussierung des Hauptbetreffs oder Zielpunkts eines Bildes oder Videos. Mit dieser intelligenten Funktion wird sichergestellt, dass der Fokus auf Desktop-Computern und Mobilgeräten über verschiedene Bildschirmgrößen hinweg aufrechterhalten wird.

Es empfiehlt sich, ein Bildprofil mit smartem Zuschneiden zu erstellen. Im Profil können Sie verschiedene Bildschirmgrößen definieren und Adobe Sensei den Rest erledigen lassen. So stellen Sie sicher, dass Ihre Bilder und Videos immer für das Gerät des Viewers optimiert sind.

Möchten Sie mehr erfahren? Watch [Verwenden von smartem Zuschneiden mit AEM Assets Dynamic Media](https://experienceleague.adobe.com/en/docs/experience-manager-learn/assets/dynamic-media/images/smart-crop-feature-video-use) (6 Minuten, 35 Sekunden) und [Verwenden von smartem Zuschneiden für Dynamic Media für Videos](https://experienceleague.adobe.com/en/docs/experience-manager-learn/assets/dynamic-media/video/dynamic-media-smart-crop-video) (6 Minuten, 22 Sekunden).

### Verbessern der SEO-Ranglisten

**Geschäftsfall:** *Konfigurieren Sie Dynamic Media, um ein verbessertes SEO-Ranking zu erhalten.*

Verwenden Sie die folgenden Empfehlungen regelmäßig, um sicherzustellen, dass Ihre Bilder effektiv zu Ihrer gesamten SEO-Strategie beitragen.

* **Bedeutungstragende Namen von Bilddateien:**
Verwenden Sie beschreibende Dateinamen, die den Bildinhalt widerspiegeln. Zum Beispiel:
   * Verwenden Sie `myCompany-Silver-Wrist-Watch`
   * *vermeiden* `myCompany_Silver_Wrist_Watch` oder `myCompanySilverWristWatch`

  Dies hilft Suchmaschinen dabei, den Bildkontext zu verstehen, und verbessert SEO. Google bevorzugt Bindestriche gegenüber Unterstrichen oder Leerzeichen in einem Dateinamen. Vermeiden Sie auch die Verkettung von Wörtern in einem Dateinamen.
* **Benutzerdefinierte Domäne:**
Implementieren Sie eine benutzerdefinierte Domäne, die Ihren Unternehmens- oder Markennamen enthält, um die Markenerkennung und das Vertrauen zu stärken. Zum Beispiel:

   * Verwenden Sie `http://images.mycompany.com/is/image/companyname/`
   * *vermeiden* `https://s7d1.scene7.com/is/image/folder/AdobeStock_28563982`
* **SEO-freundliche Ordnerstruktur:**
Organisieren Sie Ihre Bilder in einer Ordnerstruktur, die Ihren Firmennamen oder Ihre Marke enthält, um eine bessere Indizierung zu erzielen, z. B. `http://images.mycompany.com/is/image/companyname/`.
* **Dynamic Media-Regelsätze:**
Erfahren Sie, wie Sie URLs bedingt basierend auf verschiedenen Faktoren transformieren können, um SEO und Benutzererlebnis zu verbessern.
Möchten Sie mehr erfahren? Navigieren Sie zu [Verwenden Sie Regelsätze zum Konvertieren von URLs](/help/assets/dynamic-media/using-rulesets-to-transform-urls.md).
* **Intelligente Bildbearbeitung und smartes Zuschneiden:**
Verwenden Sie die Funktionen für intelligente Bildbearbeitung und smartes Zuschneiden in Dynamic Media, um optimierte und responsive Bilder bereitzustellen. Dies verbessert nicht nur die Seitenladezeiten, sondern trägt auch positiv zum SEO-Ranking bei.
Möchten Sie mehr erfahren? Navigieren Sie zu [Intelligente Bildbearbeitung](/help/assets/dynamic-media/imaging-faq.md)oder beobachten [Verwenden von smartem Zuschneiden mit AEM Assets Dynamic Media](https://experienceleague.adobe.com/en/docs/experience-manager-learn/assets/dynamic-media/images/smart-crop-feature-video-use) (6 Minuten, 35 Sekunden).

Beachten Sie, dass diese Best Practices gut mit den Best Practices für Google Image SEO übereinstimmen. Solche Verfahren unterstreichen, wie wichtig es ist, Suchmaschinen durch ordnungsgemäße Benennungskonventionen, strukturierte Daten und eine optimierte Bildbereitstellung Kontext und Klarheit zu bieten.

Möchten Sie mehr erfahren? Navigieren Sie zu [Best Practices für die URL-Struktur von Google](https://developers.google.com/search/docs/crawling-indexing/url-structure) und [Best Practices für Google Image SEO](https://developers.google.com/search/docs/appearance/google-images)


### Dynamische Verbesserung von Bildern und Erstellung visueller Effekte mithilfe von Befehlen

**Geschäftsfall:** *Rich visuelle Effekte auf Bilder anwenden.*

Dynamic Media bietet eine Reihe von Befehlen zum dynamischen Verbessern von Bildern und Erstellen visueller Effekte, ohne dass mehrere statische Assets erforderlich sind. Im Folgenden finden Sie einige kurze Erklärungen zu einigen dieser Prozesse und einige Beispiele, die Sie leiten sollten:

#### Effekte innerhalb des Quellbilds

| Aufgabe | Vorgehensweise |
| --- | --- |
| **Hochladen und Veröffentlichen des Originalbilds** | ・ Laden Sie zunächst das Originalbild in Dynamic Media hoch.<br>・ Vergewissern Sie sich, dass sie veröffentlicht ist und über eine URL zugänglich ist.<br>・ In diesem Beispiel wird ein Lagerbild einer Uhr mit weißem Hintergrund (nennen wir es &quot;Bild X&quot;) in Dynamic Media hochgeladen.<br>[https://s7g2.scene7.com/is/image/genaibeta/watch-silver-offer](https://s7g2.scene7.com/is/image/genaibeta/watch-silver-offer) |
| **Erstellen von Masken** | ・ Entwickeln Sie eine Maske, die das Thema (den Bereich, in dem Sie Effekte anwenden möchten) und den Hintergrund (den Bereich, den Sie ändern möchten) definiert.<br>[https://s7g2.scene7.com/is/image/genaibeta/watch-silver-offer-maskps](https://s7g2.scene7.com/is/image/genaibeta/watch-silver-offer-maskps)<br>・ Masken sind in der Regel Graustufenbilder, wobei Weiß den Betreff darstellt und Schwarz den Hintergrund. Sie können Masken mit Tools wie Adobe Photoshop erstellen.<br>Möchten Sie mehr erfahren? Navigieren Sie zu [Schnellmaske in Photoshop erstellen und bearbeiten](https://helpx.adobe.com/in/photoshop/using/create-temporary-quick-mask.html).<br>・ Erstellen Sie für &quot;Bild X&quot;eine Maske, die genau den Betreff beschreibt, den Sie erweitern möchten. Beispiel: eine Person, ein Objekt usw. |
| **Anwenden von Dynamic Media-URL-Befehlen für Effekte** | Nachdem Sie Ihre Maske haben, verwenden Sie URL-Befehle, um Effekte wie Schlagschatten anzuwenden oder die Hintergrundfarbe auf &quot;Bild X&quot;zu ändern. Im Folgenden finden Sie zwei Beispiele:<br><br> ・ **Schlagschatten-Effekt:**<br> Um einen Schlagschatteneffekt entlang der Betreffgrenze hinzuzufügen, bearbeiten Sie die URL wie folgt:<br>[https://s7g10.scene7.com/is/image/genaibeta/watch-silver-offer?mask=watch-silver-offer-maskps&amp;maskUse=invert&amp;effect=-1&amp;pos=100,100&amp;op_blur=75&amp;op_grow=1&amp;opac=25](https://s7g10.scene7.com/is/image/genaibeta/watch-silver-offer?mask=watch-silver-offer-maskps&amp;maskUse=invert&amp;effect=-1&amp;pos=100,100&amp;op_blur=75&amp;op_grow=1&amp;opac=25)<br>In dieser URL wird die `$shadow$` -Parameter erstellt den Schatteneffekt und `color=0,0,0` setzt die Schattenfarbe auf schwarz.<br>・ **Hintergrundfarbänderung:**<br> Um die Hintergrundfarbe zu ändern, verwenden Sie die URL mit einem anderen Wert für die Hintergrundfarbe:<br>[https://s7g10.scene7.com/is/image/genaibeta/watch-silver-offer?mask=watch-silver-offer-maskps&amp;maskUse=invert&amp;maskUse=invert&amp;color=255,255,0](https://s7g10.scene7.com/is/image/genaibeta/watch-silver-offer?mask=watch-silver-offer-maskps&amp;maskUse=invert&amp;maskUse=invert&amp;color=255,255,0)<br> In diesem Beispiel `color=255,255,0` setzt die Hintergrundfarbe auf Gelb. Bearbeiten Sie den Hintergrund für visuelle Auswirkungen in eine bestimmte Farbe. |

#### Bildrahmen hinzufügen

Mit Dynamic Media können Sie Bilder direkt über URLs bearbeiten, wodurch es zu einem leistungsstarken Tool für die Erstellung dynamischer digitaler Erlebnisse wird. Im Folgenden finden Sie einige Beispiele. Beginnen wir mit der folgenden URL des Originalbilds: [https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel](https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel).

| Aufgabe | Vorgehensweise |
| --- | --- |
| **Weißer Rand** | Verwenden Sie die folgende URL, um einen weißen Rahmen hinzuzufügen:<br>[https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel?size=400,400&amp;extend=10,10,10,10](https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel?size=400,400&amp;extend=10,10,10,10)<br>In dieser URL wird die `extend=10,10,10,10` gibt die Rahmengröße von zehn Pixel an allen Seiten an. |
| **Weichzeichnen entlang des weißen Rands** | Um einen Weichzeicheneffekt entlang des weißen Rands hinzuzufügen, können Sie die URL wie folgt bearbeiten:<br>[https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel?size=400,400&amp;extend=10,10,10,10&amp;effect=-1&amp;op_blur=60&amp;color=0,0,0](https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel?size=400,400&amp;extend=10,10,10,10&amp;effect=-1&amp;op_blur=60&amp;color=0,0,0)<br>In dieser URL wird die `effect=-1` -Parameter wendet den Weichzeicheneffekt an und `op_blur=60` steuert die Intensität der Weichzeichnung. |
| **Schlagschatteneffekt entlang der äußeren Grenze** | Verwenden Sie diese URL, um einen Schlagschatteneffekt entlang der äußeren Grenze hinzuzufügen:<br>[https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel?size=400,400&amp;extend=10,10,10,10&amp;effect=-1&amp;$shadow$&amp;color=0,0,0](https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel?size=400,400&amp;extend=10,10,10,10&amp;effect=-1&amp;$shadow$&amp;color=0,0,0)<br>Die `$shadow$` -Parameter erstellt den Schatteneffekt und `color=0,0,0` setzt die Schattenfarbe auf schwarz. |

Experimentieren Sie mit diesen URLs, um die gewünschten visuellen Effekte zu erzielen.

#### Erstellen von Bildüberlagerungen

Wenn Sie ein Logo oder Symbol auf einem vorhandenen Bild platzieren möchten, bietet Dynamic Media eine einfache Möglichkeit, dies mithilfe von URL-Befehlen zu erreichen. Lasst uns die Schritte unterbrechen.

| Schritt | Vorgehensweise |
| --- | --- |
| **Hochladen und Veröffentlichen des Basisbilds** | Laden Sie zunächst das Basisbild hoch und veröffentlichen Sie es, auf dem Sie das Logo oder Symbol überlagern möchten. Sie können jedes Bild als Basis verwenden.<br>Hier ist beispielsweise ein Basisbild:<br>[https://s7g2.scene7.com/is/image/genaibeta/decorative-room-sofa](https://s7g2.scene7.com/is/image/genaibeta/decorative-room-sofa). |
| **Hochladen und Veröffentlichen des Logos oder Symbolbilds** | Laden Sie anschließend das Bild hoch und veröffentlichen Sie es, das Sie über das Basisbild platzieren möchten. Dieses Bild sollte ein transparentes PNG mit dem Logo oder Symbol sein, das Sie überlagern möchten.<br>Hier ist das transparente PNG-Bild eines Sternobjekts mit Transparenzeffekten, das überlagert werden soll:<br>[https://s7g2.scene7.com/is/image/genaibeta/decorate-star](https://s7g2.scene7.com/is/image/genaibeta/decorate-star) |
| **Anwenden der Dynamic Media-URL** | Erstellen Sie jetzt eine Dynamic Media-URL, die das Basisbild mit dem Logo oder Symbolbild kombiniert. Sie können URL-Befehle verwenden, um diesen Effekt zu erzielen.<br>Die URL-Struktur sieht in etwa so aus:<br>[https://s7g2.scene7.com/is/image/genaibeta/decorative-room-sofa?layer=1&amp;src=decorate-star&amp;scale=1.25&amp;posN=0.33,-.25&amp;fmt=png](https://s7g2.scene7.com/is/image/genaibeta/decorative-room-sofa?layer=1&amp;src=decorate-star&amp;scale=1.25&amp;posN=0.33,-.25&amp;fmt=png)<br>where<br>・ `hotspotRetailBaseImage` ist das Basisbild.<br>・ `starxp` ist das Logo-/Symbolbild.<br>・ `layer=1` gibt an, dass das Logo oder Symbol über dem Basisbild platziert werden soll.<br>・ `scale=1.25` passt die Größe des Logos/Symbols an.<br>・ `posN=0.33,-.25` bestimmt die Position des Logos/Symbols relativ zum Basisbild.<br>・ `fmt=png` stellt sicher, dass die Ausgabe im PNG-Format vorliegt. |

Weitere Infos? Navigieren Sie zu [src](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-src) Weitere Informationen zu `src` und anderen Dynamic Media-URL-Befehlen.


#### Überlagern von Werbetext

Im Folgenden finden Sie die Schritte zum Überlagern einer Werbetext-Nachricht auf einem Bild mithilfe von HTML und CSS.

| Schritt | Vorgehensweise |
| --- | --- |
| **Hochladen und Veröffentlichen des Basisbilds** | Laden Sie zunächst das Basisbild hoch und veröffentlichen Sie es, für das Sie den Text überlagern möchten. Sie können jedes beliebige Bild verwenden. Hier finden Sie beispielsweise ein Beispiel für ein Basisbild:<br>[https://s7g2.scene7.com/is/image/genaibeta/leather-sofa](https://s7g2.scene7.com/is/image/genaibeta/leather-sofa)<br> |
| **Anwenden von Dynamic Media-Textoperatoren** | Mit Dynamic Media können Sie Textoperatoren anwenden, um dynamischen Text direkt auf das Bild zu überlagern. Die folgende Beispiel-URL zeigt diese Fähigkeit:<br>[https://s7g10.scene7.com/is/image/genaibeta/leather-sofa?layer=1&amp;posN=-0.3,-0.455&amp;text=%7b\rtf1\ansi%7b\fonttbl%7b\f0+Arial;%7d%7b\colortbl+\red255\green255\blue255;%7d\copyfit1000\vertalc\qc%7b\cf0\fs42+New+Collection%7d%7d&amp;size=370,70&amp;textAttr=130&amp;bgcolor=FF3 333&amp;wid=600&amp;hei=600](https://s7g10.scene7.com/is/image/genaibeta/leather-sofa?layer=1&amp;posN=-0.3,-0.455&amp;text=%7b\rtf1\ansi%7b\fonttbl%7b\f0+Arial;%7d%7b\colortbl+\red255\green255\blue255;%7d\copyfit1000\vertalc\qc%7b\cf0\fs42+New+Collection%7d%7d&amp;size=370,70&amp;textAttr=130&amp;bgcolor=FF3 333&amp;wid=600&amp;hei=600) |

#### Größenanpassung und Zuschnitt für verschiedene Anwendungsfälle

##### Grundlagen zur Bildgröße

Die Bildgröße ändert die Abmessungen, Auflösung und Dateigröße eines Bildes. Im Folgenden finden Sie einige wichtige Punkte, die zu beachten sind:

* **Pixelzusammensetzung:**
Digitale Bilder bestehen aus winzigen Punkten, die Pixel genannt werden. Wenn ein Bild erstellt wird, hat es eine bestimmte Anzahl Pixel. Bei der Größenanpassung werden Pixel hinzugefügt oder abgezogen, um die Abmessungen, Auflösung und Dateigröße des Bildes zu ändern.
* **Seitenverhältnis:**
Die Beibehaltung des Seitenverhältnisses (das Verhältnis zwischen Breite und Höhe) ist entscheidend, um Verzerrungen zu vermeiden. Unabhängig davon, ob Sie ein Bild vergrößern (Hochskalieren) oder verkleinern (Downskalieren), wird durch die Beibehaltung des Seitenverhältnisses die visuelle Konsistenz gewährleistet.
* **Qualitätsaspekte:**
Die Größenanpassung kann sich auf die Bildqualität auswirken. Vermeiden Sie drastische Vergrößerungen, da dies zu einer Verpixelung führen kann. Ziehen Sie stattdessen in Erwägung, das Bild in einer größeren Größe und Auflösung zu reproduzieren. Verwenden Sie für kleinere Bilder die entsprechenden Tools, um die Auflösung beizubehalten.

##### Zuschneiden versus Größenanpassung

Zuschneiden und Größenanpassung sind Verfahren in Dynamic Media, mit denen Sie Bilder für verschiedene Anwendungsfälle transformieren können, unabhängig davon, ob es um das Erstellen von Miniaturansichten, Produktanzeigebildern oder Bannern geht.

* **Zuschneiden:**
Umfasst das Entfernen eines Teils eines Bildes, um dessen Komposition und Framing zu ändern. Die Gesamtdimensionen werden nicht geändert, sondern auf einen bestimmten Bereich konzentriert.
* **Größenänderung:**
Passt die Abmessungen, Auflösung und Dateigröße des gesamten Bildes an und behält dabei das Seitenverhältnis bei.

Sehen wir uns einen Anwendungsfall an, der das folgende Bild des Wohnzimmers umfasst:

* **Original Wohnzimmerbild:**
  [https://s7g2.scene7.com/is/image/genaibeta/decorative-room-sofa](https://s7g2.scene7.com/is/image/genaibeta/decorative-room-sofa)
* **Miniaturansicht (200 Pixel x 200 Pixel):**
Eine kleinere Version, die für schnelles Laden oder Anzeigen geeignet ist.
  [https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=200&amp;hei=200&amp;fit=crop](https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=200&amp;hei=200&amp;fit=crop)
* **Miniaturansicht mit Zuschnitt (200 x 200 Pixel):**
Zum Fokussieren auf den Sofa-Bereich geschnitten.
  [https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=200&amp;hei=200&amp;cropN=.24,.24,.6,.72&amp;fit=crop](https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=200&amp;hei=200&amp;cropN=.24,.24,.6,.72&amp;fit=crop)
* **Produktanzeigebild (800 Pixel x 600 Pixel):**
Zum Anzeigen des Sofas zugeschnitten und in der Größe angepasst.
  [https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=800&amp;hei=600&amp;cropN=.24,.24,.6,.72&amp;fit=crop](https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=800&amp;hei=600&amp;cropN=.24,.24,.6,.72&amp;fit=crop)
* **Banner (1720 Pixel x 820 Pixel):**
Abgeleitet vom Originalbild, wobei der Raum betont wird.
  [https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=1720&amp;hei=820&amp;cropN=0,.1,1,1&amp;fit=crop](https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=1720&amp;hei=820&amp;cropN=0,.1,1,1&amp;fit=crop)

Entdecken Sie diese Varianten für Ihre spezifischen Anforderungen.
Möchten Sie mehr über die Befehle erfahren, die in einer URL verfügbar sind? Navigieren Sie zu [Befehlsreferenz](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference).

### Veröffentlichen eines Videos für meine Website

**Geschäftsfall:** *Veröffentlichen Sie schnell ein Video für eine Marketing-Site.*

* **Wählen Sie ein Videoprofil aus:**
Zunächst sollten Sie in Dynamic Media ein geeignetes Videoprofil auswählen. Sie können die *Adaptive Videokodierung* Profil, das in AEM Assets unter &quot;Videoprofile&quot;verfügbar ist. Diese vordefinierten Kodierungseinstellungen stellen sicher, dass Ihr Video für die Wiedergabe auf verschiedenen Geräten und unter verschiedenen Bandbreitenbedingungen optimiert ist. Alternativ können Sie Ihr eigenes Profil für adaptive Videos erstellen.
* **Weisen Sie das Profil zu:**
Weisen Sie das ausgewählte Videoprofil den Ordnern zu, in die das Video hochgeladen werden soll. Dieser Schritt stellt sicher, dass die richtigen Kodierungseinstellungen während des Upload-Prozesses angewendet werden.
* **Laden Sie das Originalvideo hoch:**
Laden Sie die Originalvideodatei hoch. Stellen Sie sicher, dass es sich um ein hochauflösendes Video mit guter Qualität handelt. Je besser das Quellvideo, desto besser das Endergebnis.
* **Vorschau erstellen und veröffentlichen:**
Zeigen Sie eine Vorschau des Videos an, um sicherzustellen, dass alles wie erwartet aussieht. Sobald Sie zufrieden sind, veröffentlichen Sie sie. Dadurch wird das Video für Ihre Zielgruppe verfügbar.
* **Link oder Einbettung:**
Nach der Veröffentlichung haben Sie zwei Optionen.
   * **Direkte Verknüpfung:**
Verwenden Sie die bereitgestellte URL, um direkt mit dem Video zu verknüpfen. Verknüpfen Sie ihn entsprechend auf Ihrer Marketing-Site.
   * **Betten Sie das Video ein:**
Kopieren Sie den bereitgestellten Einbettungscode und fügen Sie ihn in die HTML Ihrer Web-Seite ein, auf der das Video angezeigt werden soll. Dadurch kann das Video direkt auf Ihrer Site wiedergegeben werden.

Möchten Sie mehr erfahren? Navigieren Sie zu [Video](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/video).

### Videos für optimale Qualität und Interaktion konfigurieren

**Geschäftsfall:** *Richten Sie Videos für die beste Qualität und Interaktion ein.*

Um die bestmögliche Qualität und Interaktion Ihrer Videos sicherzustellen, sollten Sie eine Kombination der folgenden Best Practices-Strategien implementieren:

* **Verwenden Sie den integrierten HTML5-Video-Viewer:**
Die Dynamic Media HTML5-Video-Viewer-Vorgaben sind robuste Video-Player. Verwenden Sie diese, um allgemeine Probleme im Zusammenhang mit der HTML5-Videowiedergabe und Mobilgeräten zu vermeiden.
Diese Vorgaben decken Herausforderungen wie die Bereitstellung von Streaming mit adaptiven Bitraten und die eingeschränkte Reichweite des Desktop-Browsers ab.
Möchten Sie mehr erfahren? Navigieren Sie zu [Best Practice: Verwenden des HTML 5-Video-Viewers](/help/assets/dynamic-media/video.md#best-practice-using-the-html-video-viewer).

* **Dynamic Media-Videoprofile verwenden:**
Videoprofile in Dynamic Media unterstützen Sie bei effizienter Videomanagement, konsistenter Qualität und adaptivem Streaming.
Möchten Sie mehr erfahren? Navigieren Sie zu [Dynamic Media-Videoprofile](/help/assets/dynamic-media/video-profiles.md).

* **Befolgen Sie die Best Practices für die Videokodierung:**
Wenden Sie Videokodierungsprofile an, die die Originalvideoqualität ohne übermäßige Downskalierung während der Kodierung beibehalten.
Möchten Sie mehr erfahren? Navigieren Sie zu [Best Practices für die Kodierung von Videos](/help/assets/dynamic-media/video.md#best-practices-for-encoding-videos).

* **Adaptives Streaming anstelle von progressivem Streaming:**
Beim adaptiven Streaming wird die Videoqualität basierend auf der Internetverbindungsgeschwindigkeit und den Gerätefunktionen des Viewers angepasst.
Es verwendet Protokolle wie HLS (HTTP Live Streaming) oder DASH (`Dynamic Adaptive Streaming over HTTP`), um eine optimale Wiedergabequalität sicherzustellen.
Im Gegensatz zu progressivem Streaming, das Videos linear bereitstellt, minimiert adaptives Streaming die Pufferung und bietet ein nahtloses Anzeigeerlebnis.

* **Aktivieren Sie DASH in Ihrem Konto (digitales adaptives Streaming über HTTP):**
DASH stellt Videoinhalte dynamisch über adaptives Streaming bereit.
Um DASH zu aktivieren, erstellen Sie ein Support-Ticket für Ihre Umgebung.
Möchten Sie mehr erfahren? Navigieren Sie zu [DASH in Ihrem Dynamic Media-Konto aktivieren](/help/assets/dynamic-media/video.md#enable-dash).

### Internationalisierung von Videos für den mehrsprachigen Gebrauch

**Geschäftsfall:** *Machen Sie Videos für den mehrsprachigen Gebrauch bereit.*

Die Internationalisierung von Videos für den mehrsprachigen Gebrauch ist für das Erreichen eines globalen Publikums von entscheidender Bedeutung. Dynamic Media bietet Funktionen, die Ihnen bei der Erreichung dieses Ziels helfen können.

* **Videos hochladen:**
   * Erstellen Sie zunächst ein Videokodierungsprofil. Sie können entweder das vordefinierte Profil &quot;Adaptive Videoverschlüsselung&quot;im Lieferumfang von Dynamic Media verwenden oder Ihr eigenes benutzerdefiniertes Profil erstellen.
   * Verknüpfen Sie das Videoverarbeitungsprofil mit einem oder mehreren Ordnern, in die Sie die Primärvideos hochladen.
   * Laden Sie die Primärvideos in diese Ordner hoch. Dynamic Media kodiert sie basierend auf dem zugewiesenen Videoverarbeitungsprofil.
   * Dynamic Media unterstützt in erster Linie Kurzformvideos (bis zu 30 Minuten) mit einer Mindestauflösung größer als 25 × 25. Videodateien mit einer Größe von bis zu 15 GB können hochgeladen werden1.

* **Verwalten Sie Ihre Videos:**
   * Organisieren, Durchsuchen und Durchsuchen von Video-Assets in AEM
   * Vorschau erstellen und Video-Assets veröffentlichen
   * Zeigen Sie das Quellvideo und die kodierten Ausgabeformate zusammen mit den zugehörigen Miniaturen an.
   * Bearbeiten Sie Videoeigenschaften wie Titel, Beschreibung und Tags2.

* **Lokalisierung:**
   * Erstellen Sie für jede Zielregion/Sprache Audiospuren und Untertitel.
   * Fügen Sie diese Audio- und Untertitelspuren Ihren Videos über die AEM-Oberfläche hinzu.
   * Wenn Benutzer die Videos abspielen, können sie ihre bevorzugte Sprache für Audio und Untertitel auswählen.

* **Publishing:**
   * Wenn Sie AEM als Web Content Management (WCM)-System verwenden, können Sie Ihren Webseiten direkt Videos hinzufügen.
   * Wenn Sie ein WCM-System eines Drittanbieters verwenden, können Sie Videos mithilfe von URLs oder Einbettungscodes auf Ihren Webseiten verknüpfen oder einbetten.

Möchten Sie mehr erfahren? Navigieren Sie zu [Über die Unterstützung mehrerer Untertitel und Audiospuren für Videos in Dynamic Media](/help/assets/dynamic-media/video.md#about-msma) oder beobachten [Hinzufügen mehrerer Untertitel und Audiospuren zu einem Video](https://delivery-p106302-e1008131.adobeaemcloud.com/adobe/assets/urn:aaid:aem:daf9a222-9f7f-4333-b167-98cb4c63a1f8/play) (1 Minuten, 41 Sekunden).


## Bereitstellen von Assets für Kunden

### Bildgrößen optimieren und Seitenladezeiten minimieren

**Geschäftsfall:** *Optimieren Sie die Bildgröße für Browser oder Bildschirm und reduzieren Sie die Seitenladezeit.*

Die intelligente Bildbearbeitung von Dynamic Media ist ein leistungsstarkes Tool, das die Leistung bei der Bildbereitstellung verbessert, indem Format, Größe und Qualität des Bildes automatisch auf der Grundlage der Browserfunktionen des Kunden optimiert werden.

Adobe empfiehlt, die Funktionen der intelligenten Bildbearbeitung zu verwenden, anstatt das Bildformat manuell auf `webp` oder `avif`. Dies ist der Grund:

* **Browserkompatibilität:**
Die intelligente Bildbearbeitung stellt sicher, dass das bereitgestellte Bildformat mit dem Browser des Benutzers kompatibel ist.
* **Optimale Komprimierung:**
Es wird das beste Komprimierungsformat basierend auf dem jeweiligen Browser, den Netzwerkbedingungen und der Bildschirmauflösung ausgewählt.
* **Moderne Formate:**
while `avif` ist ein neueres Format, das eine bessere Komprimierung bietet. Es wird noch nicht in allen Browsern allgemein unterstützt.
* **Best Practices:**
Um das beste Web-optimierte Format zu gewährleisten, können Sie darauf vertrauen, dass die intelligente Bildbearbeitung die Formatauswahl vornimmt, anstatt die Befehle manuell zu verwenden `fmt=webp` oder `fmt=avif`.

Mithilfe der intelligenten Bildbearbeitung können Sie sicherstellen, dass Ihre Bilder möglichst effizient und auf die Browser-Umgebung des jeweiligen Benutzers zugeschnitten bereitgestellt werden. Dieser Ansatz vereinfacht den Prozess und kann zu einer verbesserten Leistung in Bezug auf die Ladezeiten von Bildern und das gesamte Benutzererlebnis führen.

Möchten Sie mehr erfahren? Navigieren Sie zu [Intelligente Bildbearbeitung](/help/assets/dynamic-media/imaging-faq.md).

