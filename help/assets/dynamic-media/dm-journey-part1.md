---
title: Dynamic Media Journey, Teil I
description: Die Dynamic Media-Journey behandelt die Grundlagen von Dynamic Media, wie es funktioniert, was es für Sie tun kann und welchen Nutzen es für Ihre Arbeit und Ihre Kunden bringt.
contentOwner: Rick Brough
products: Experience Manager as a Cloud Service
topic-tags: introduction,administering
content-type: reference
feature: Image Profiles
role: User, Admin
mini-toc-levels: 4
hide: false
hidefromtoc: false
exl-id: f3472006-d5ae-4f70-af3e-44e73aee85cc
source-git-commit: 69d2121323d8a8ab54db3fb0a56195a1271e6112
workflow-type: tm+mt
source-wordcount: '3585'
ht-degree: 2%

---

# Dynamic Media Journey: Grundlagen, Teil I {#dm-journey-part1}

Willkommen bei der Dynamic Media Journey.

Diese Journey behandelt die Grundlagen von Dynamic Media, wie es funktioniert, was es für Sie tun kann und welchen Nutzen es für Ihre Arbeit und Ihre Kunden bringt.

**_Voraussetzungen_**

* Grundlegendes zu Bild- und Videoformaten
* Grundlegendes zu HTML und CSS
* Grundlegendes zu Designtools wie Adobe Illustrator, Adobe Photoshop, Adobe XD
* Der Zugriff auf Dynamic Media auf Experience Manager ist hilfreich, ist jedoch nicht erforderlich

**_Wissenswertes_**

_Teil I_

* Was ist Dynamic Media und wie kann es Ihnen helfen?
* Anwendungsbeispiele für Dynamic Media
* Fluss eines Assets durch das Dynamic Media-System

_Teil II_

* Anatomie einer Dynamic Media-URL und wie Dynamic Media Inhalte bereitstellt
* Grundlagen zum Erstellen von Bildvorgaben zum Rendern von Assets
* Bildsets, Rotationssets und Sets für gemischte Medien

**_Zielgruppe_**
Die Zielgruppe, die für Leser dieser Journey am besten geeignet ist, sind die folgenden, die neu bei Dynamic Media on Experience Manager sind:

* Administrator
* Geschäftsanalyst
* Inhaltsarchitekt
* Inhaltsautor
* Designer
* Entwickler
* Marketing
* Produkt-Manager/Eigentümer

>[!TIP]
>
>Um die bestmöglichen Ergebnisse zu erzielen, empfiehlt Adobe, die Dynamic Media-Journey auf einem Desktop-Computer zu lesen und anzuzeigen.

## Was ist Dynamic Media und wie kann es Ihnen helfen? {#dm-journey-a}

Mit Dynamic Media können Sie visuell ansprechende Merchandising- und Marketing-Assets nach Bedarf bereitstellen. Außerdem können Sie damit interaktive Anzeigeerlebnisse wie Zoom, Drehen um 360 Grad und Videos erstellen und bereitstellen. Ihre Assets werden für die Verwendung auf Web-, Mobile- und Social-Media-Sites dynamisch skaliert. Mit einer Reihe von Assets aus Primärquellen - wie Bildern, Videos und 3D - generiert und liefert Dynamic Media mehrere Varianten dieses umfangreichen Inhalts in Echtzeit über sein globales, skalierbares, leistungsoptimiertes CDN (Content Delivery Network).

Dynamic Media umfasst die Workflows der Digital Asset Management-Lösung Adobe Experience Manager Assets, um den Digital-Campaign-Verwaltungsprozess zu vereinfachen und zu optimieren.

### Eine Datei mit endlosen Möglichkeiten

Einer der Hauptpunkte, um Dynamic Media zu verstehen, ist das Konzept der _Eine primäre Asset-Datei mit unendlichen Möglichkeiten_.

Um dieses Konzept besser zu verstehen, sollten Sie darüber nachdenken, wie Sie herkömmlicherweise mit einem einzelnen Asset arbeiten, z. B. mit einem Bild oder Video. Normalerweise erstellen Sie ein primäres Asset. Anschließend erstellen Sie manuell Versionen desselben Assets für jedes Erlebnis, jedes erforderliche Gerät, jede Webseite und jede Eigenschaft, in der es verwendet wird. Mit der Zeit kann dieses einzelne Asset auf 20, 30 oder mehr Versionen wachsen, ohne dass ein Versionsverlauf an sie angehängt ist. Stellen Sie sich das für jedes Bild oder Video vor, das Sie haben. The number of asset versions would quickly become overwhelming to maintain and update, not to mention the increase in storage costs.

Dynamic Media, however, is fundamentally different from other systems because you use it to deliver your media _dynamically_ from single, primary assets, and from URL calls. Die von Ihnen angeforderten Dynamic Media-URL-Pfade enthalten Anweisungen, die dem Adobe-Veröffentlichungsserver mitteilen, wie das Asset angezeigt werden soll, wenn es auf dem Bildschirm eines Kunden bereitgestellt wird. Wenn Sie beispielsweise dasselbe primäre Asset verwenden, können Sie es sofort in unbegrenzten Ausgabeformaten bereitstellen lassen, indem Sie Größe, Format, Auflösung, Gewichtung, Farbe, Zuschneiden und Effekte wie eine Zoom-Ansicht ändern.

Mit dieser einzigartigen Bereitstellungsmethode wird sichergestellt, dass unabhängig von Größe und Bandbreite konsistente Erlebnisse auf jedem Bildschirm angezeigt werden. Full-size videos are also optimized for all screen types and adaptively streamed to also ensure a consistent, quality user experience.

<!-- As part of building and publishing assets with Dynamic Media, you visually configure the effects that you want to apply to assets. In so doing, you are literally building the URL that correctly tells the publish server how to deliver your primary asset to the screen.  -->

![Adobe Dynamic Media liefert dasselbe Primärbild für verschiedene Medien in unterschiedlichen Größen und Formaten.](/help/assets/dynamic-media/assets/dm-oneasset-multioutput.png)
_Adobe Dynamic Media stellt sicher, dass unabhängig von Größe und Bandbreite für jeden Bildschirm konsistente, qualitativ hochwertige Erlebnisse bereitgestellt werden._

As you read on, you are going to learn more about why this concept of &quot;one primary asset file, endless possibilities&quot; is important.

### The Content Delivery Network

Wenn Sie bereit sind, mit einem Bild-Asset oder einem Video-Asset live zu gehen, wird dies durch das Backbone von Dynamic Media unterstützt, das aus einem leistungsstarken, erstklassigen Bereitstellungsnetzwerk besteht. Das Netzwerk bedient täglich Hunderte von Kunden auf der ganzen Welt. Die Assets werden im Content Delivery Network (CDN) bereitgestellt, das von Akamai gehostet wird. Das CDN ist ein System von Computerdiensten, die miteinander vernetzt sind und transparent zusammenarbeiten, um Endbenutzern Inhalte, insbesondere große Rich-Media-Inhalte, bereitzustellen.

Im CDN-System werden Web-Inhalte in Web-Caches im Internet gespeichert. Anschließend wird sie aus dem Web-Cache an Endbenutzer gesendet, um eine schnellere Bereitstellung zu ermöglichen. Wenn also zum ersten Mal jemand eine Webseite herunterlädt, werden die angezeigten Assets an einen CDN-Cache gesendet. Sie werden auf dem Server gespeichert, sodass beim nächsten Zugriff eines Benutzers im selben Bereich auf die Webseite derselbe Cache-Inhalt schneller bereitgestellt wird. Der Inhalt wird schneller bereitgestellt, da er sich näher am Endbenutzer befindet. A CDN makes for faster web page displays, and yet it decreases bandwidth demands on the central server because content is delivered from a cache network, not from a central server in every instance. Dieser optimierte Fluss bedeutet ein besseres Benutzererlebnis, was zu höheren Umsätzen führt.

<!-- USE AN IMAGE HERE? ![Content delivery network](/help/assets/assets-dm/cdn.png) -->

Historisch betrachtet liefert das CDN monatlich 3,5 Petabyte Traffic an Kunden. Das System kann an einem Tag 52 Milliarden Assets bereitstellen. That number equates to 864,000 images and videos successfully delivered to customers, _every second_.

### Intelligente Bildbearbeitung

Dynamic Media leistet bereits eine hervorragende Arbeit bei der Optimierung von Assets und der Sicherstellung, dass jedes Asset über das CDN schnell auf mobilen und Desktop-Systemen geladen wird. Dazu werden Bildvorgaben in Dynamic Media verwendet, um die Bildqualität zu definieren. Sie definieren auch den Typ des Bildes, das Sie senden, seine Schärfe und andere Teile für verschiedene Teile Ihrer Erlebnisse oder Seiten.

Um Dynamic Media jedoch über Bildvorgaben hinaus noch wertvoller zu machen, gibt es _Intelligente Bildbearbeitung_.

Die intelligente Bildbearbeitung bietet eine noch bessere Leistung bei der Bereitstellung von Bild-Assets, indem das Format und die Dateigröße automatisch auf der Grundlage der Browserfunktionen eines Kunden optimiert werden. Es funktioniert mit Ihren vorhandenen Bildvorgaben (Bildvorgaben werden in Teil II dieser Journey erläutert) und verwendet intelligente Funktionen bei der Bereitstellung.

Durch diese intelligente Funktion wird die Größe der Bilddatei je nach Browser- und Netzwerkverbindungsgeschwindigkeit weiter reduziert. Da Bild-Assets den größten Teil der Ladezeit einer Seite ausmachen, kann sich die Leistungsverbesserung grundlegend auf wichtige Geschäftsindikatoren auswirken, z. B.:

* Höhere Konversion
* Besuchszeit pro Site
* Absprungrate der unteren Site

Insgesamt können Sie mit intelligenter Bildbearbeitung abhängig von Ihren vorhandenen Bildvorgabeneinstellungen und spezifischen Endbenutzermerkmalen eine Leistungsverbesserung von 22 % bis 47 % erwarten. All dies unter Beibehaltung der Bildqualität, als ob es nie berührt würde.

![Intelligente Bildbearbeitung](/help/assets/dynamic-media/assets/dm-smart-imaging.png)
_Die intelligente Bildbearbeitung optimiert automatisch das Format und die Dateigröße eines Bildes basierend auf der Browserfunktion und Netzwerkgeschwindigkeit eines Kunden._

Intelligente Bildbearbeitung ist nicht standardmäßig aktiviert, da dies einen koordinierten Ansatz zwischen Ihnen und dem technischen Support von Adobe Dynamic Media erfordert. Außerdem erfordert die Aktivierung der intelligenten Bildbearbeitung das vollständige Löschen Ihres CDN-Cache, der dann mit der Zeit erneut aufgefüllt wird. Wenn Sie an der Verwendung der intelligenten Bildbearbeitung interessiert sind, können Sie mit Adobe zusammenarbeiten, um sie zu aktivieren, indem Sie ein Ticket beim technischen Support einreichen. Der technische Support bietet Ihnen dann einen URL-Parameter, mit dem Sie vorab intelligente Bildbearbeitung ausprobieren können. Sie können es auf jeder Ihrer Webseiten oder Bilder testen, damit Sie die Leistung und die Einsparungen sehen können. Anschließend können Sie die intelligente Bildbearbeitung für Ihre gesamte Site aktivieren lassen.

### Adaptive Videosets

Wenn ein Video auf einer Seite oder Hauptseite vorhanden ist, tendieren Ihre Kunden dazu, länger mit diesem Inhalt zu interagieren und länger auf der Seite zu bleiben, was normalerweise gut ist. Dieses Verhalten wurde durch Analysen gezeigt, die von Adobe durchgeführt wurden. Videos können jedoch komplex sein. Zum einen haben Sie oft eine große Primärdatei. Es ist kompliziert, die Größe und Bereitstellung von Videos zu bestimmen, um sicherzustellen, dass das Erlebnis unabhängig vom Gerät, auf dem es angezeigt wird, und unabhängig von der Bandbreite reibungslos ausgeführt wird.

Um dieses Problem zu lösen, bietet Ihnen Dynamic Media die Möglichkeit, _Adaptive Videosets_.

![Adaptives Videoset](/help/assets/dynamic-media/assets/dm-smart-imaging.png)
_Ein adaptives Videoset gruppiert Versionen desselben Videos, die mit unterschiedlichen Bitraten und Formaten kodiert wurden._

Sie beginnen mit Ihrem ursprünglichen, primären Video, das Sie in das System hochladen. Dynamic Media-Größen automatisch oder _transcodes_, dieses Video in mehrere Videos. Zum Zeitpunkt des Versands bestimmt er dann intelligent, welcher Videobildschirm, welche Qualität und welches Format verwendet werden soll, und stellt ihn entweder für Smartphones, Tablets oder Desktop-Computer bereit.

Auf einem iOS-Mobilgerät wird beispielsweise die Bandbreite 4G, 5G oder WLAN erkannt. Dann wird automatisch das richtig kodierte Video aus den verschiedenen Video-Bitraten im adaptiven Videoset ausgewählt. Das Video wird an Mobilgeräte, Tablets oder Desktop-Computer gestreamt.

Darüber hinaus wird die Videoqualität bei Änderung der Netzwerkbedingungen automatisch geändert. Und wenn ein Kunde auf einem Desktop in den Vollbildmodus wechselt, reagiert das adaptive Videoset mit einer besseren Auflösung, wodurch das Anzeigeerlebnis des Kunden verbessert wird.

Adaptive Videosets bieten eine reibungslose, hochwertige Wiedergabe für Kunden, die Dynamic Media-Videos auf mehreren Bildschirmen und Geräten wiedergeben. Es nimmt die Komplexität des Videos wirklich weg.

## Anwendungsbeispiele für Dynamic Media {#dm-journey-b}

Im Folgenden finden Sie häufige Probleme bei Anwendungsfällen und Lösungen, mit denen Dynamic Media Sie bei der Förderung von positiver Kundeninteraktion, Treue, Konversion und erhöhtem ROI unterstützen kann.

### Anwendungsfall: Primärer Dateiansatz

Einer der wichtigsten Anwendungsfälle für Dynamic Media ist ebenfalls einer der offensichtlichsten. Das bedeutet, dass die Gewichtung von Seiten und Erlebnissen und die Größe des Inhalts, ob es sich um ein Bild oder ein Video handelt, reduziert wird.

Im Folgenden sehen Sie ein typisches Erlebnis oder eine Webseite. Etwa 90 % einer Seite bestehen aus Rich-Media-Daten wie Bildern und Videos, bei denen es sich häufig um viel schwerere Dateien handelt.

![Inhaltsseitengröße](/help/assets/dynamic-media/assets/dm-content-page-weight.png)
_Inhaltsseitengewichtung einer normalen Webseite._

Die restlichen 10 % sind HTML, CSS-Code und bestimmte Tags. Sie möchten die 90-prozentige Gewichtung dieser Seite optimieren, und Dynamic Media hilft dabei. Sie haben vorhin über das Konzept der _Eine primäre Asset-Datei mit unendlichen Möglichkeiten_. Dieser Ansatz ist für die Reduzierung des Seitengewichts insgesamt von Bedeutung. Die Möglichkeit, ein primäres Asset auf einer Produktdetailseite, einer Miniaturseite, Ihrem Warenkorb und Ihrem Suchraster zu verwenden, ist eine großartige Zeiteinsparung. Und es sorgt auch für Konsistenz über Erlebnisse hinweg.

![Primärer Dateiansatz](/help/assets/dynamic-media/assets/dm-onefile.png)
_Die Uhr ist eine primäre Asset-Datei, die jedoch mit mehreren Ausgabeformaten - nicht Kopien - direkt erstellt wird._

Sehen wir uns nun die Probleme an, die Dynamic Media mit der einen Datei und einigen Lösungen für diesen Ansatz löst.

| **Problem** | **Dynamic Media-Lösung** |
|---|---|
| Erstellen und speichern Sie jedes Asset. | Verwenden Sie eine einzelne Bilddatei und erstellen Sie die erforderlichen Ausgabedarstellungen automatisch erst zum Zeitpunkt der Bereitstellung. |
| Hohe Speicherkosten. | Ermöglicht das Erstellen und Speichern mehrerer Kopien eines Assets. |
| Schwierigkeiten bei der Aufrechterhaltung des Sorgerechts. | Gewährleistet die Bereitstellung geräteoptimierter und konsistenter Erlebnisse. |
| No version history. |  |
| Inconsistent brand experiences across devices. |  |
| Unnecessary cost of duplicate asset creation. |  |

Wenn Sie an eine Datei denken, erstellen Sie ein Asset für jedes Erlebnis. Möglicherweise haben Sie ein Startbild, und dann müssen Sie 20, 30 oder 40 Varianten dieses Bildes erstellen, die Sie schließlich speichern und für diesen Speicher bezahlen müssen.

Dann müssen Sie sicherstellen, dass das richtige Bild verwendet wird, was sich auf Ihre Fähigkeit auswirken kann, Markenkonsistenz zu gewährleisten. And, if you cannot find an image, you have to go back in and duplicate those assets.

Mit Dynamic Media können Sie spontan Varianten von Bildern aus diesem Startbild erstellen. It lets you be creative with that primary asset and not have to go back and forth with your graphic design artist or photo studio to create additional content. Und das ist Geld und Zeit gespart.

Bei der Eindatei-Methode verwenden Sie eine einzelne primäre Datei. Erstellen Sie dann die Versionen oder Ausgabedarstellungen, die für Ihre Sites, Eigenschaften und Erlebnisse erforderlich sind, erst zum Zeitpunkt, zu dem sie von einem Kunden bereitgestellt oder angesehen werden. Diese Effizienz kann den Speicherbedarf für Ihre Assets erheblich verringern und die Gesamtkomplexität Ihres Workflows verringern. Mit dem Bereitstellungssystem von Dynamic Media wird sichergestellt, dass alle Bilder und Videos optimiert, schnell geladen und auf allen Bildschirmen und Geräten optimal dargestellt werden.

### Use case: Video

Ein weiterer Anwendungsfall, den Dynamic Media löst, ist Video. Video ist komplex. Das ist schwer zu handhaben. Videodateien sind wegen ihrer inhärenten Dateigrößen schwierig zu speichern und zu verschieben.

| **Problem** | **Dynamic Media-Lösung** |
|---|---|
| Schwierigkeiten bei der Verwaltung und Bereitstellung von für verschiedene Geräte optimierten Videos. | Verwenden Sie ein einzelnes Video, das automatisch für alle Geräte Größen enthält. |
| Videos werden aufgrund der verfügbaren Bandbreite des Endbenutzers angehalten oder in schlechter Qualität wiedergegeben. | Stellen Sie Videos über einen HTML-Player bereit, der die verfügbare Bandbreite automatisch erkennt und die Qualität anpasst, um hohe Wiedergabetreue und reibungslose Wiedergabe zu gewährleisten. |
| Es ist nicht machbar und zeitaufwendig, alle Versionen eines Videos manuell zu erstellen, um eine gute Anzeige und Wiedergabe auf allen Geräten sicherzustellen. | Dank eines vereinfachten Workflows können Sie mühevolle Transkodierungsarbeiten vermeiden. |
|  | Kostenlose Zeit für wertvollere Arbeit. |

Kunden kommen mit dem folgenden Problem nach Dynamic Media, das sie hoffen zu lösen:

&quot;_Wir haben das Video, und wir haben viel Geld ausgegeben, um es zu erstellen. Aber wir haben uns davon abgehalten, es auf Seiten zu platzieren oder zu liefern, denn durch unsere Tests können wir wirklich nicht die Qualität des Videos garantieren, oder ob es wirklich spielen wird. Und das wirkt sich letztendlich auf unsere Marken aus und potenziell auch auf unsere Rolle bei der Konversion._&quot;

Die Lösung von Dynamic Media besteht darin, diese eine primäre Videodatei zu verwenden und es Dynamic Media zu ermöglichen, alle Größen durch den Transkodierungsprozess zu erstellen. Verbinden Sie dies dann mit dem intelligenten Videoplayer von Dynamic Media. Dieser Workflow gewährleistet, dass das Video, unabhängig davon, ob es auf Ihrer Haupt-Landingpage oder auf einer Kategorie- oder Produktdetailseite verwendet wird, konsistent ist und von hoher Qualität bereitgestellt wird.

Im Folgenden finden Sie weitere Anwendungsbeispiele.

### Anwendungsfall: Einzelne Quelle der Wahrheit

| **Problem** | **Dynamic Media-Lösung** |
|---|---|
| Digitale Assets, die über das Unternehmen verteilt sind und in verschiedenen Teams oder Geschäftsbereichen siloliert werden. | Speichern und verwalten Sie alle digitalen Assets an einem zentralen Speicherort. |
| Team-Mitglieder laden lokale Versionen herunter und erstellen diese. | Team-Mitglieder verwenden eine einzelne primäre Datei zum Erstellen _und_ liefern alle erforderlichen Versionen über verschiedene Bildschirmgrößen und Geräte hinweg. |
| Einmalige Assets, die für jedes Erlebnis und jedes Gerät erstellt wurden. | Beseitigt einmalige Assets und spart Zeit und Geld beim Erstellen. |

### Anwendungsfall: KI-gestütztes smartes Zuschneiden für Rich-Media

| **Problem** | **Dynamic Media-Lösung** |
|---|---|
| Zeitaufwendige und aufwändige manuelle Zeichnung, Messung und Ausschneiden von Bildern oder Videos, um den Fokus hervorzuheben und über alle Bildschirmgrößen und Geräte hinweg angemessen anzuzeigen. | Verwendet smartes Zuschneiden in Dynamic Media, einer Adobe Sensei AI-Funktion, um den Fokus in einem Bild oder Video automatisch zu erkennen und zuzuschneiden, um ihn zu erhalten. |
| Time lost that could be better spent creating high-impact experiences. | Captures the intended point of interest regardless of screen size. |
| Single-use assets created for every experience and device. | Beseitigt aufwändige manuelle Aufgaben und liefert hochwertige, schnell ladende Bilder und Videos, die auf jedem Gerät oder Bildschirm gut aussehen. |

### Anwendungsfall: Authoring interaktiver Medien

| **Problem** | **Dynamic Media solution** |
|---|---|
| Einfache und statische Kundenerlebnisse, die nicht interagieren, die Treue fördern oder die Konversion fördern. | Ermöglicht es nichttechnischen Benutzern, interaktive Elemente wie Hotspots, Karussells und Rotationssets einfach und nahtlos hinzuzufügen, um ein dynamischeres und ansprechenderes Erlebnis zu erzielen. |
| Begrenzte Kapitalrendite aus digitalen Assets und glanzlose Kundenerlebnisse. | Ermöglicht Konvertierung und ROI aus Rich-Media-Erlebnissen. |

## Fluss eines Assets durch das Dynamic Media-System {#dm-journey-c}

Im Folgenden finden Sie einen typischen Workflow für Dynamic Media.

![Dynamic Media-Workflow](/help/assets/dynamic-media/assets/dm-workflow.png)
_Wie ein Asset durch das Dynamic Media-System fließt._

Sie beginnen mit der Erstellungsphase mit dem Hauptziel, Ihr primäres Asset am Ende zu haben. Diese primären Assets können von Fotoshoots oder Videoanbietern stammen, oder es können einige Audiodateien sein, die Sie erstellt haben. Sie können Creative Suite-Anwendungen von Adobe wie Adobe InDesign, Adobe Photoshop und Adobe Illustrator verwenden, um die Erstellung von Inhalten zu erleichtern.

Wenn der Erstellungsabschnitt abgeschlossen ist, platzieren Sie das Asset in die Erstellungslösung, indem Sie es in Dynamic Media hochladen. In Dynamic Media stellen Sie sicher, dass Sie über die richtigen Bildvorgaben und Viewer für die verschiedenen Webseiten auf Ihrer Site verfügen.

Letztendlich optimieren Sie all diese Inhalte und veröffentlichen sie auf Dynamic Media-Servern, damit sie für Web-, Druck-, E-Mail-, Desktop- und Mobilgeräte verfügbar sind.

### Uploading assets into Dynamic Media

Wenn Sie die Erstellung eines primären Assets abgeschlossen haben, laden Sie es in Dynamic Media hoch. Die Art der hochgeladenen Datei sowie Format und Größe der Datei sind wichtige Attribute für Dynamic Media. Zum Zeitpunkt des Uploads möchten Sie sicherstellen, dass Sie den maximalen Nutzen aus der einzigen Dateiunterstützung ziehen.

For example, the watch image below is 4560 x 3020 pixels. And while you may never use an image that size, you can still upload it. The larger the image, the better the quality that Dynamic Media can deliver, even down to a thumbnail rendition. Denken Sie daran: Sie können _reduzieren_ Auflösung eines vorhandenen Bildes. Aber wenn Sie versuchen _Anstieg_ Wenn ein Bild aufgelöst wird, ist das Ergebnis wahrscheinlich nicht zufriedenstellend.

![Empfohlene Formate zum Hochladen in Dynamic Media](/help/assets/dynamic-media/assets/dm-upload-formats.png)
_Überlegungen zum Hochladen von Assets._

Adobe empfiehlt, Assets in verlustfreiem Format hochzuladen. Generally, it is best to avoid JPEG because when you deliver JPEG or when you continue to save JPEG, you start to lose image quality over time. You want to start with the highest resolution images in a lossless format that you can live with. That format is typically a TIFF or PNG file.

Was den Farbraum angeht, denken Sie bei digitalen Kanälen oder Webansichten normalerweise an RGB (Rot, Grün, Blau).

Die meisten würden nie daran denken, etwas in CMYK zu liefern oder warum Sie es vielleicht sogar in CMYK versenden möchten. Der Grund dafür ist, dass dieser Farbraum am häufigsten für die Bereitstellung gedruckter Artikel verwendet wird. Dynamic Media kann jedoch in beiden Farbräumen bereitstellen.

Es gibt viele Kunden, die noch drucken, wie z.B. Lager Großhandelsvereine. Und es gibt Lebensmittelgeschäfte, die oft wöchentlich Flyer drucken. Solche Kunden benötigen, dass ihre Bilder beide Farbräume aufweisen. Dazu sind traditionell zwei verschiedene Bilder erforderlich: eine in RGB und eine in CMYK. Sie können jedoch CMYK-Assets direkt in Dynamic Media hochladen und Dynamic Media-RGB-Assets automatisch über eine Bildvorgabe oder über ein Farbprofil bereitstellen lassen. Es ist nicht erforderlich, mehrere Versionen einer Datei zu erstellen, sodass das Konzept der _Eine primäre Asset-Datei mit unendlichen Möglichkeiten_.

<!-- **The Value of Renditioning??? or Demo portion** -->

### Veröffentlichen und Anzeigen einer Vorschau von Assets

Nach dem Hochladen von Assets in Dynamic Media empfiehlt es sich, _publish_ durch Auswahl der Assets und anschließendes Klicken auf **[!UICONTROL Veröffentlichen]** oder **[!UICONTROL Quick Publish]** in Dynamic Media. Das Veröffentlichen von Assets ist erforderlich, wenn Sie sie in einem beliebigen Erlebnis verwenden möchten. Nachdem Assets veröffentlicht wurden, können Sie sie mithilfe einer von Dynamic Media generierten URL, die Sie kopieren, in eine Webseite aufnehmen oder indem Sie Code auf der Seite einbetten.

Neben der manuellen Veröffentlichung von Assets können Sie Dynamic Media so konfigurieren, dass Sie Assets zum Zeitpunkt des Uploads sofort - ohne Benutzereingriff - veröffentlichen.

Nach dem Hochladen gibt es verschiedene Möglichkeiten, die Ausgabeformate eines Assets in Dynamic Media in der Vorschau anzuzeigen. Die Vorschau von Ausgabedarstellungen kann Ihnen dabei helfen, eine Vorstellung davon zu erhalten, was ein Kunde sieht. Eine gängige Vorschaumethode besteht darin, ein Asset auszuwählen und dann seine Ausgabeformate anzuzeigen, indem Sie eine *Bildvorgabe* wie im Folgenden gezeigt.

![Anzeigen einer Asset-Ausgabedarstellung basierend auf der Bildvorgabe &quot;Groß&quot;](/help/assets/dynamic-media/assets/dm-image-preset-with-url.png)
_Vorschau eines Ausgabeformats eines Assets basierend auf der ausgewählten Bildvorgabe &quot;Groß&quot;. Auf die Schaltfläche URL wurde geklickt. Der resultierende URL-Pfad enthält den Namen der Bildvorgabe &quot;Groß&quot; und kann auf einer Webseite verwendet werden._

Die obige URL ist live! [Jetzt testen](http://s7d1.scene7.com/is/image/jpearldemo/AdobeStock_28563982?$Large$).

Eine weitere Methode zur Vorschau eines Assets besteht darin, das Bild-Asset auszuwählen und anschließend eine *Viewer* -Vorgabe, wie im Folgenden gezeigt.

![Vorschau eines Assets basierend auf der Viewer-Vorgabe &quot;Vertikales Licht zoomen&quot;](/help/assets/dynamic-media/assets/dm-viewer-preset.png)
_Vorschau eines Assets basierend auf der ausgewählten Viewer-Vorgabe &quot;ZoomVertical_light&quot;. Der Mauszeiger (`+`) wurde über die Uhr verschoben, um hineinzuzoomen. Beachten Sie die Schaltflächen URL und Einbetten ._

Die obige Ausgabe ist live! [Jetzt testen](https://s7d1.scene7.com/s7viewers/html5/ZoomVerticalViewer.html?asset=jpearldemo/AdobeStock_28563982&amp;config=jpearldemo/ZoomVertical_light).

Let&#39;s examine these URLs a little closer so you can better understand what is going on. Take me to [Dynamic Media Journey: The Basics, Part II](/help/assets/dynamic-media/dm-journey-part2.md#dm-journey-d).

## Weitere Informationen

_Dynamic Media-Themen_

* [Arbeiten mit Dynamic Media](/help/assets/dynamic-media/dynamic-media.md)
* [Intelligente Bildbearbeitung](/help/assets/dynamic-media/imaging-faq.md)
* [Adaptive Videosets](/help/assets/dynamic-media/video.md)
* [Best Practices für die Optimierung der Bildqualität](/help/assets/dynamic-media/best-practices-for-optimizing-the-quality-of-your-images.md)
* [Hochladen von Assets](/help/assets/add-assets.md#upload-assets)
* [Vorschau von Medienelementen](/help/assets/dynamic-media/previewing-assets.md)
* [Vorschau von 3D-Assets](/help/assets/dynamic-media/previewing-3d-assets.md)
* [Bereitstellen von Dynamic Media-Assets](/help/assets/dynamic-media/delivering-dynamic-media-assets.md)
* [Veröffentlichen von Assets](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md)
* [Arbeiten mit selektiver Veröffentlichung in Dynamic Media](/help/assets/dynamic-media/selective-publishing.md)

_Dynamic Media-Tutorials_

* [Verwenden von Dynamic Media mit Experience Manager Assets](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/dynamic-media-overview-feature-video-use.html)
* [Adobe Experience Manager-Inhaltsbibliothek](https://experienceleague.adobe.com/?lang=en#recommended/solutions/experience-manager) (Suchen Sie nach *Dynamic Media*)

_Dynamic Media-Viewer_

* [Live-Demos](https://landing.adobe.com/en/na/dynamic-media/ctir-2755/live-demos.html)