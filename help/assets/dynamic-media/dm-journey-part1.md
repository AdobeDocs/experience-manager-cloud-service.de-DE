---
title: Dynamic Media-Tour, Teil 1
description: Die Dynamic Media-Tour behandelt die Grundlagen von Dynamic Media, wie es funktioniert, was es für Sie tun kann und welchen Nutzen es für Ihre Arbeit und Ihre Kunden bringt.
contentOwner: Rick Brough
products: Experience Manager as a Cloud Service
topic-tags: introduction,administering
content-type: reference
feature: Image Profiles,Best Practices
role: User, Admin
mini-toc-levels: 4
hide: false
hidefromtoc: false
exl-id: f3472006-d5ae-4f70-af3e-44e73aee85cc
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '3615'
ht-degree: 100%

---

# Dynamic Media-Tour: Grundlagen, Teil 1 {#dm-journey-part1}

{{see-also-dm}}

Willkommen bei der Dynamic Media-Tour.

Diese Tour behandelt die Grundlagen von Dynamic Media, wie es funktioniert, was es für Sie tun kann und welchen Nutzen es für Ihre Arbeit und Ihre Kunden bringt.

**_Voraussetzungen_**

* Grundlegendes zu Bild- und Videoformaten
* Grundlegendes zu HTML und CSS
* Grundlegendes zu Designtools wie Adobe Illustrator, Adobe Photoshop, Adobe XD
* Der Zugriff auf Dynamic Media in Experience Manager ist hilfreich, ist jedoch nicht erforderlich.

**_Was Sie in der Tour lernen können_**

_Teil 1_

* Was ist Dynamic Media und wie kann es Ihnen helfen?
* Anwendungsbeispiele für Dynamic Media
* Fluss eines Assets durch das Dynamic Media-System

_Teil 2_

* Anatomie einer Dynamic Media-URL und wie Dynamic Media Inhalte bereitstellt
* Grundlagen zum Erstellen von Bildvorgaben zum Rendern von Assets
* Bild-Sets, Rotations-Sets und Sets mit gemischten Medien

**_Zielgruppe_**
Die Zielgruppe, die am besten zu den Lesern dieser Tour passt, sind die folgenden Personen, die noch nicht mit Dynamic Media in Experience Manager vertraut sind:

* Administrator
* Geschäftsanalyst
* Inhaltsarchitekt
* Inhaltsautor
* Designer
* Entwickler
* Marketing
* Produkt-Manager/-Verantwortlicher

>[!TIP]
>
>Um die bestmöglichen Ergebnisse zu erzielen, empfiehlt Adobe, diese Dynamic Media-Tour auf einem Desktop-Computer zu lesen und anzuzeigen.

## Was ist Dynamic Media und wie kann es Ihnen helfen? {#dm-journey-a}

Mit Dynamic Media können Sie visuell ansprechende Merchandising- und Marketing-Assets nach Bedarf bereitstellen. Außerdem können Sie damit interaktive Anzeigeerlebnisse wie Zoom, Drehen um 360 Grad und Videos erstellen und bereitstellen. Ihre Assets werden für die Verwendung auf Web-, Mobile- und Social-Media-Websites dynamisch skaliert. Mit einer Reihe von Assets aus Primärquellen – wie Bildern, Videos und 3D – generiert und liefert Dynamic Media mehrere Varianten dieser vielfältigen Inhalte in Echtzeit über sein globales, skalierbares, leistungsoptimiertes Content Delivery Network (CDN).

Dynamic Media bindet die Workflows der Adobe Experience Manager-Lösung für Digital Asset Management ein, um das Management digitaler Kampagnen zu vereinfachen und zu optimieren.

### Eine Datei mit endlosen Möglichkeiten

Einer der Hauptpunkte, um Dynamic Media zu verstehen, ist das Konzept der _Einen primären Asset-Datei mit unendlichen Möglichkeiten_.

Um dieses Konzept besser zu verstehen, sollten Sie sich vor Augen führen, wie Sie herkömmlicherweise mit einem einzelnen Asset arbeiten, z. B. mit einem Bild oder Video. Normalerweise erstellen Sie ein primäres Asset. Anschließend erstellen Sie manuell Versionen desselben Assets für jedes Erlebnis, jedes erforderliche Gerät, jede Webseite und jede Eigenschaft, in der es verwendet wird. Mit der Zeit kann dieses einzelne Asset auf 20, 30 oder mehr Versionen wachsen, ohne dass ein Versionsverlauf an sie angehängt ist. Stellen Sie sich das für jedes Bild oder Video vor, das Sie haben. Die Anzahl der Asset-Versionen würde schnell zu groß werden, um sie zu pflegen und zu aktualisieren, ganz zu schweigen von den steigenden Speicherkosten.

Dynamic Media unterscheidet sich jedoch grundlegend von anderen Systemen, da Sie damit Ihre Medien _dynamisch_ aus einzelnen, primären Assets und aus URL-Aufrufen bereitstellen können. Die von Ihnen angefragten Dynamic Media-URL-Pfade enthalten Anweisungen, die dem Adobe-Veröffentlichungsserver mitteilen, wie das Asset angezeigt werden soll, wenn es auf dem Bildschirm eines Kunden bereitgestellt wird. So können Sie z. B. ein und dasselbe primäre Asset sofort in einer unbegrenzten Anzahl von Ausgabedarstellungen bereitstellen und dabei Größe, Format, Auflösung, Gewicht, Farbe, Zuschnitt und Effekte wie eine Zoomansicht ändern.

Diese einzigartige Bereitstellungsmethode stellt sicher, dass unabhängig von Größe und Bandbreite auf jedem Bildschirm eine gleichbleibend hohe Qualität geboten wird. Videos in voller Größe werden außerdem für alle Bildschirmtypen optimiert und adaptiv gestreamt, um ein einheitliches, hochwertiges Benutzererlebnis zu gewährleisten.

<!-- As part of building and publishing assets with Dynamic Media, you visually configure the effects that you want to apply to assets. In so doing, you are literally building the URL that correctly tells the publish server how to deliver your primary asset to the screen.  -->

![Adobe Dynamic Media stellt dasselbe Primärbild für verschiedene Medien in unterschiedlichen Größen und Formaten bereit](/help/assets/dynamic-media/assets/dm-oneasset-multioutput.png)
_Adobe Dynamic Media stellt sicher, dass unabhängig von Größe und Bandbreite für jeden Bildschirm konsistente, qualitativ hochwertige Erlebnisse bereitgestellt werden._

Wenn Sie weiterlesen, erfahren Sie mehr darüber, warum dieses Konzept der „Einen primären Asset-Datei mit unendlichen Möglichkeiten“ wichtig ist.

### Das Content Delivery Network (CDN)

Wenn Sie bereit sind, ein Bild- oder Video-Asset live zu schalten, wird es durch das Backbone von Dynamic Media unterstützt, das aus einem leistungsstarken, erstklassigen Bereitstellungsnetzwerk besteht. Das Netzwerk bedient täglich Hunderte von Kunden auf der ganzen Welt. Die Assets werden im Content Delivery Network (CDN), das von Akamai gehostet wird, verteilt. Das CDN ist ein System von Computer-Services, die miteinander vernetzt sind und transparent zusammenarbeiten, um Endbenutzern Inhalte, insbesondere große Rich-Media-Inhalte, bereitzustellen.

Im CDN-System werden Web-Inhalte in Web-Caches im Internet gespeichert. Dann werden sie vom Web-Cache an die Endbenutzer geliefert, was eine schnellere Bereitstellung ermöglicht. Wenn also jemand zum ersten Mal eine Webseite herunterlädt, werden die angezeigten Inhalte an einen CDN-Cache geliefert. Sie werden auf dem Server gespeichert, sodass beim nächsten Zugriff auf die Web-Seite in derselben Region derselbe Cache-Inhalt schneller bereitgestellt wird. Die Inhalte werden schneller bereitgestellt, da sie sich näher an den Benutzenden befinden. Ein CDN sorgt für eine schnellere Anzeige von Webseiten und verringert gleichzeitig die Bandbreitenanforderungen an den zentralen Server, da die Inhalte nicht in jedem Fall von einem zentralen Server, sondern von einem Cache-Netzwerk geliefert werden. Dieser optimierte Fluss bedeutet ein besseres Benutzererlebnis, was zu höheren Umsätzen führt.

<!-- USE AN IMAGE HERE? ![Content delivery network](/help/assets/assets-dm/cdn.png) -->

Historisch betrachtet liefert das CDN monatlich 3,5 Petabyte Traffic an die Kundschaft. Das System kann an einem Tag 52 Milliarden Assets bereitstellen. Diese Zahl entspricht 864.000 Bildern und Videos, die _jede Sekunde_ erfolgreich an Kunden bereitgestellt werden.

### Intelligente Bildbearbeitung

Dynamic Media leistet bereits hervorragende Arbeit bei der Optimierung von Assets und stellt sicher, dass jedes Asset auf mobilen und Desktop-Systemen schnell geladen wird, und zwar mit Hilfe des CDN. Dazu werden Bildvorgaben in Dynamic Media verwendet, um die Bildqualität zu definieren. Sie definieren auch die Art des Bildes, das Sie senden, seine Schärfe und andere Elemente für verschiedene Teile Ihrer Erlebnisse oder Seiten.

Um aber Dynamic Media über die Bildvorgaben hinaus einen weiteren Mehrwert zu verleihen, gibt es _Intelligente Bildbearbeitung_.

Die intelligente Bildbearbeitung sorgt für eine noch bessere Leistung bei der Bereitstellung von Bild-Assets, indem sie das Format und die Dateigröße eines Bildes automatisch auf der Grundlage der Browser-Fähigkeiten des Kunden optimiert. Sie funktioniert mit Ihren vorhandenen Bildvorgaben (Bildvorgaben werden in Teil 2 dieser Tour besprochen) und nutzt Intelligenz bei der Bereitstellung.

Durch diese Intelligenz wird die Größe der Bilddateien je nach Browser und Geschwindigkeit der Netzwerkverbindung weiter reduziert. Da Bild-Assets den größten Teil der Ladezeit einer Seite ausmachen, kann sich die Leistungsverbesserung entscheidend auf wichtige Geschäftsindikatoren auswirken, wie z. B.:

* Höhere Konversion
* Auf der Website verbrachte Zeit
* Geringere Absprungrate für die Website

Insgesamt können Sie mit der intelligenten Bildbearbeitung eine Leistungsverbesserung von 22 % bis 47 % erwarten, je nach den vorhandenen Bildvorgaben und den spezifischen Merkmalen des Endbenutzers. Und das alles bei einer Bildqualität, als hätte man sie nie angerührt.

![Intelligente Bildbearbeitung](/help/assets/dynamic-media/assets/dm-smart-imaging.png)
_Die intelligente Bildbearbeitung optimiert automatisch das Format und die Dateigröße eines Bildes auf der Grundlage der Browser-Fähigkeiten und der Netzwerkgeschwindigkeit des Kunden._

Die intelligente Bildbearbeitung ist nicht standardmäßig aktiviert, da sie eine koordinierte Zusammenarbeit zwischen Ihnen und dem technischen Support von Adobe Dynamic Media erfordert. Außerdem erfordert die Aktivierung der intelligenten Bildbearbeitung eine vollständige Löschung des CDN-Caches, der dann mit der Zeit wieder aufgefüllt wird. Wenn Sie an der Verwendung der intelligenten Bildbearbeitung interessiert sind, können Sie diese in Zusammenarbeit mit Adobe aktivieren, indem Sie ein Ticket für den technischen Support einreichen. Der technische Support stellt Ihnen dann einen URL-Parameter zur Verfügung, mit dem Sie die intelligente Bildbearbeitung vorab testen können. Sie können sie auf jeder Ihrer Webseiten oder Bilder ausprobieren, damit Sie die Leistung und die Einsparungen sehen können, die Sie erhalten. Anschließend können Sie die intelligente Bildbearbeitung für Ihre gesamte Website aktivieren lassen.

### Adaptive Videosets

Wenn eine Seite oder eine Hauptseite ein Video enthält, beschäftigen sich Ihre Kunden in der Regel länger mit diesem Inhalt und bleiben länger auf der Seite, was in der Regel eine gute Sache ist. Dieses Verhalten zeigt sich in den von Adobe durchgeführten Analysen. Videos können jedoch komplex sein. Zum einen sind sie oft mit einer großen Primärdatei verbunden. Es ist kompliziert, die Größe und Bereitstellung von Videos zu bestimmen, um sicherzustellen, dass das Erlebnis unabhängig von dem Gerät, auf dem es angezeigt wird, und unabhängig von der Bandbreite reibungslos abläuft.

Um dieses Problem zu lösen, bietet Ihnen Dynamic Media die Möglichkeit, _adaptive Video-Sets_ zu erstellen.

Ein adaptives Video-Set gruppiert Versionen desselben Videos, die mit unterschiedlichen Bitraten und Formaten kodiert sind.

Sie beginnen mit Ihrem ursprünglichen, primären Video, das Sie in das System hochladen. Dynamic Media skaliert bzw. _transkodiert_ dieses Video automatisch in mehrere Videos. Zum Zeitpunkt der Bereitstellung wird dann auf intelligente Weise bestimmt, welcher Videobildschirm, welche Qualität und welches Format verwendet werden soll, und die Daten werden entweder an das Smartphone, das Tablet oder den Desktop-Computer übertragen.

Auf einem iOS-Mobilgerät wird beispielsweise die Bandbreite 4G, 5G oder WLAN erkannt. Dann wird automatisch das richtig kodierte Video aus den verschiedenen Video-Bitraten im adaptiven Videoset ausgewählt. Das Video wird an Mobilgeräte, Tablets oder Desktop-Computer gestreamt.

Außerdem wird die Videoqualität automatisch dynamisch umgeschaltet, wenn sich die Netzbedingungen ändern. Wenn darüber hinaus eine Kundin oder ein Kunde den Vollbildmodus auf einem Desktop aktiviert, reagiert das adaptive Video-Set, indem eine bessere Auflösung verwendet wird, um das Anzeigeerlebnis zu verbessern.

Adaptive Videosets bieten Ihnen bestmögliche Wiedergabe für Kunden, die das Dynamic Media-Video auf unterschiedlichen Bildschirmen und Geräten wiedergeben. Damit wird die Komplexität von Videos tatsächlich beseitigt.

## Anwendungsbeispiele für Dynamic Media {#dm-journey-b}

Im Folgenden finden Sie häufige Anwendungsfälle und Lösungen, bei denen Dynamic Media Ihnen helfen kann, die Kundenbindung, Treue, Konversion und den ROI zu erhöhen.

### Anwendungsfall: Ansatz der primären Datei

Einer der wichtigsten Anwendungsfälle für Dynamic Media ist auch einer der offensichtlichsten. Das heißt, dass der Umfang von Seiten und Erlebnissen sowie die Größe der bereitgestellten Inhalte, seien es Bilder oder Videos, reduziert werden.

Im Folgenden sehen Sie ein typisches Erlebnis oder eine Webseite. Etwa 90 % einer Seite bestehen aus Rich-Media-Inhalten wie Bildern und Videos, bei denen es sich in der Regel um sehr umfangreiche Dateien handelt.

![Inhaltsseitengröße](/help/assets/dynamic-media/assets/dm-content-page-weight.png)
_Inhaltsseitengröße einer typischen Webseite._

Die restlichen 10 % sind HTML, CSS-Code und bestimmte Tags. Sie wollen den Umfang der 90 % der Seite optimieren, und Dynamic Media hilft Ihnen dabei. Vorhin haben Sie über das Konzept der _Einen primären Bestandsdatei mit unendlichen Möglichkeiten_ gelesen. Dieser Ansatz trägt wesentlich zur Verringerung der Gesamtseitengröße bei. Die Möglichkeit, ein primäres Asset auf einer Produktdetailseite, einer Miniaturansichtsseite, Ihrem Warenkorb und Ihrem Suchraster zu verwenden, bedeutet eine große Zeitersparnis. Und sie sorgt auch für Konsistenz über Erlebnisse hinweg.

![Ansatz der primären Datei](/help/assets/dynamic-media/assets/dm-onefile.png)
_Bei der Uhr handelt es sich um eine primäre Asset-Datei, von der jedoch spontan mehrere Ausgabedarstellungen – keine Kopien – erstellt werden._

Sehen wir uns die Probleme näher an, die Dynamic Media mit der einen Datei löst, und einige der Lösungen für diesen Ansatz.

| **Problem** | **Dynamic Media-Lösung** |
|---|---|
| Erstellen und Speichern jedes Assets. | Verwenden einer einzelnen Bilddatei und automatisches Erstellen der erforderlichen Ausgabedarstellungen erst zum Zeitpunkt der Bereitstellung. |
| Hohe Speicherkosten. | Beseitigt die Notwendigkeit, mehrere Kopien eines Assets zu erstellen und zu speichern. |
| Schwierigkeiten bei der Aufrechterhaltung der Produktkette. | Gewährleistet die Bereitstellung von geräteoptimierten und konsistenten Erlebnissen. |
| Kein Versionsverlauf. | |
| Inkonsistente Markenerlebnisse über Geräte hinweg. | |
| Unnötige Kosten für die Erstellung doppelter Assets. | |

Wenn Sie an eine Datei denken, erstellen Sie ein Asset für jede Art von Erlebnis. Sie haben vielleicht ein Ausgangsbild, und dann müssen Sie 20, 30 oder 40 Variationen dieses Bildes erstellen, die Sie schließlich speichern und für deren Speicherung Sie bezahlen müssen.

Dann müssen Sie sicherstellen, dass das richtige Bild verwendet wird, und das kann sich auf Ihre Fähigkeit auswirken, die Konsistenz Ihrer Marken zu gewährleisten.  Und wenn Sie ein Bild nicht finden können, müssen Sie zurückgehen und diese Assets duplizieren.

Mit Dynamic Media können Sie ausgehend von einem Ausgangsbild in Echtzeit Variationen von Bildern erstellen. So können Sie mit diesem primären Asset kreativ sein und müssen nicht ständig mit Ihrem Grafikdesigner oder Fotostudio zusammenarbeiten, um zusätzliche Inhalte zu erstellen. Und das spart Geld und Zeit.

Beim Ein-Datei-Ansatz verwenden Sie eine einzige Primärdatei. Erstellen Sie dann die Versionen oder Ausgabedarstellungen, die für alle Ihre Websites, Eigenschaften und Erlebnisse erforderlich sind, nur in dem Moment, in dem sie bereitgestellt oder von einem Kunden gesehen werden. Eine solche Effizienz kann den Speicherbedarf für Ihre Assets erheblich reduzieren und die Komplexität Ihrer Workflows insgesamt verringern. Und mit dem Bereitstellungssystem von Dynamic Media ist gewährleistet, dass jedes Bild und Video optimiert ist, schnell geladen wird und auf allen Bildschirmen und Geräten gut aussieht.

### Anwendungsfall: Video

Ein weiterer Anwendungsfall, den Dynamic Media löst, ist Video. Video ist komplex. Es ist schwer zu handhaben. Videodateien sind wegen ihrer inhärenten Dateigrößen schwierig zu speichern und zu verschieben.

| **Problem** | **Dynamic Media-Lösung** |
|---|---|
| Schwierigkeiten bei der Verwaltung und Bereitstellung von für verschiedene Geräte optimierten Videos. | Verwenden eines einzelnen Videos, das die Größe automatisch für alle Geräte anpasst. |
| Videos bleiben aufgrund der verfügbaren Bandbreite der Benutzenden stehen oder werden in niedriger Qualität wiedergegeben. | Stellen Sie Videos über einen HTML-Player bereit, der die verfügbare Bandbreite automatisch erkennt und die Qualität anpasst, um eine originalgetreue und flüssige Wiedergabe zu gewährleisten. |
| Es ist nicht praktikabel und zu zeitaufwändig, alle Versionen eines Videos manuell zu erstellen, nur um eine gute Anzeige und Wiedergabe auf allen Geräten zu gewährleisten. | Dank eines vereinfachten Workflows entfällt die stundenlange, mühsame Transkodierung. |
| | Gewinnen Sie Zeit für höherwertige Aufgaben. |

Kundinnen und Kunden wenden sich mit folgendem Problem, das sie zu lösen hoffen, an Dynamic Media:

„_Mein Unternehmen hat das Video, und die Abteilung hat viel Geld für die Erstellung ausgegeben, sich aber nicht getraut, es auf den Seiten zu platzieren oder es auszuliefern. Der Grund dafür war, dass beim Testen die Qualität des Videos nicht garantiert werden konnte, und auch nicht, ob es wirklich abgespielt werden würde. Und das wirkt sich letztlich auf die Marke des Unternehmens und möglicherweise auf seine Rolle bei der Konversion aus._“

Die Lösung von Dynamic Media besteht darin, diese eine primäre Videodatei zu nehmen und Dynamic Media alle Größen durch seinen Transkodierungsprozess bestimmen zu lassen. Kombinieren Sie dies dann mit dem intelligenten Videoplayer von Dynamic Media. Dieser Workflow gewährleistet, dass das Video auf Ihrer Haupt-Landingpage oder auf einer Kategorie- oder Produktdetailseite konsistent ist und in hoher Qualität bereitgestellt wird.

Im Folgenden finden Sie weitere Anwendungsbeispiele.

### Anwendungsfall: Einzelne Quelle der Wahrheit

| **Problem** | **Dynamic Media-Lösung** |
|---|---|
| Digitale Ressourcen sind über das gesamte Unternehmen verstreut und befinden sich in verschiedenen Silos von Teams oder Geschäftsbereichen. | Speichern und verwalten Sie alle digitalen Assets an einem zentralen Ort. |
| Die Team-Mitglieder laden lokale Versionen herunter und erstellen sie. | Die Team-Mitglieder verwenden eine einzelne primäre Datei zum Erstellen _und_ stellen alle erforderlichen Versionen über verschiedene Bildschirmgrößen und Geräte hinweg bereit. |
| Assets zur einmaligen Verwendung, die für jedes Erlebnis und jedes Gerät erstellt werden. | Vermeidet Assets, die einmalig verwendet werden, und spart so Zeit und Geld bei deren Erstellung. |

### Anwendungsfall: KI-gestützter intelligenter Zuschnitt für Rich-Media

| **Problem** | **Dynamic Media-Lösung** |
|---|---|
| Es ist zeitaufwendig und arbeitsintensiv, Bilder oder Videos manuell zu zeichnen, zu messen und zuzuschneiden, um den Fokuspunkt hervorzuheben und auf allen Bildschirmgrößen und Geräten angemessen anzuzeigen. | Intelligenter Zuschnitt in Dynamic Media nutzt eine Adobe Sensei AI-Funktion, um den Fokus in einem Bild oder Video automatisch zu erkennen und zuzuschneiden, um ihn so zu erhalten. |
| Verlorene Zeit, die besser für die Erstellung wirkungsvoller Erlebnisse genutzt werden könnte. | Erfasst den gewünschten Blickpunkt unabhängig von der Bildschirmgröße. |
| Assets zur einmaligen Verwendung, die für jedes Erlebnis und jedes Gerät erstellt werden. | Vermeidet mühsame manuelle Aufgaben und liefert hochwertige, schnell ladende Bilder und Videos, die auf jedem Gerät oder Bildschirm gut aussehen. |

### Anwendungsfall: Bearbeiten interaktiver Medien

| **Problem** | **Dynamic Media-Lösung** |
|---|---|
| Flache und statische Kundenerlebnisse, die keine Interaktion auslösen, keine Treue erzeugen und die Konversion nicht fördern. | Ermöglicht es technisch nicht versierten Benutzern, interaktive Elemente wie Hotspots, Karussells und Rotations-Sets einfach und nahtlos einzufügen, um dynamische und ansprechende Erlebnisse zu schaffen. |
| Begrenzter ROI der Investitionen in digitale Ressourcen und unzureichende Kundenerlebnisse. | Steigert die Konversionsrate und den ROI von Rich-Media-Erlebnissen. |

## Fluss eines Assets durch das Dynamic Media-System {#dm-journey-c}

Im Folgenden finden Sie einen typischen Workflow für Dynamic Media.

![Dynamic Media-Workflow](/help/assets/dynamic-media/assets/dm-workflow.png)
_Fluss eines Assets durch das Dynamic Media-System._

Sie beginnen mit der Erstellungsphase mit dem Hauptziel, am Ende Ihr primäres Asset zu haben. Diese primären Assets können von Fotoshootings, von Videoanbietern oder von Audiodateien stammen, die Sie haben erstellen lassen. Sie können die Anwendungen der Creative Suite von Adobe wie Adobe InDesign, Adobe Photoshop und Adobe Illustrator für die Ausarbeitung der Inhalte verwenden.

Wenn der Erstellungsprozess abgeschlossen ist, fügen Sie das Asset in die Authoring-Lösung ein, indem Sie das Asset in Dynamic Media hochladen. Mit Dynamic Media stellen Sie sicher, dass Sie die richtigen Bildvorgaben und Viewer für Ihre verschiedenen Webseiten auf Ihrer Website bereitstellen.

Und schließlich optimieren Sie all diese Inhalte und veröffentlichen sie auf Dynamic Media-Servern, sodass sie für Web, Druck, E-Mail, Desktops und mobile Geräte verfügbar sind.

### Hochladen von Assets in Dynamic Media

Wenn Sie die Erstellung eines primären Assets abgeschlossen haben, laden Sie es in Dynamic Media hoch. Die Art der Datei, die Sie hochladen, sowie das Format und die Größe der Datei sind wichtige Attribute für Dynamic Media. Zum Zeitpunkt des Hochladens sollten Sie sicherstellen, dass Sie den maximalen Nutzen aus der Unterstützung für den Ein-Dateien-Ansatz ziehen.

Das nachstehende Bild einer Uhr hat zum Beispiel eine Größe von 4560 x 3020 Pixeln. Auch wenn Sie ein Bild in dieser Größe nie verwenden werden, können Sie es dennoch hochladen. Je größer das Bild ist, desto besser ist die Qualität, die Dynamic Media liefern kann, sogar bis hin zu einer Miniatur-Ausgabedarstellung. Denken Sie daran: Sie können die Auflösung eines vorhandenen Bildes problemlos _verringern_. Wenn Sie jedoch versuchen, die Auflösung eines Bildes zu _erhöhen_, wird das Ergebnis wahrscheinlich nicht zufriedenstellend sein.

![Empfohlene Formate zum Hochladen in Dynamic Media](/help/assets/dynamic-media/assets/dm-upload-formats.png)
_Überlegungen zum Hochladen von Assets._

Adobe empfiehlt, Assets in einem verlustfreien Format hochzuladen. Im Allgemeinen ist es am besten, JPEG zu vermeiden, da die Bildqualität mit der Zeit nachlässt, wenn man JPEG ausgibt oder fortgesetzt als JPEG speichert. Sie sollten mit den Bildern mit der höchsten Auflösung in einem verlustfreien Format beginnen, mit dem Sie leben können. Dieses Format ist normalerweise eine TIFF- oder PNG-Datei.

Was den Farbraum betrifft, so denkt man bei einem digitalen Kanal oder einer Webansicht normalerweise an RGB (Rot, Grün, Blau).

Die meisten würden nie auf die Idee kommen, etwas in CMYK zu liefern, oder warum man überhaupt in CMYK liefern sollte. Der Grund dafür ist, dass dieser Farbraum am häufigsten für die Lieferung von Druckerzeugnissen verwendet wird. Dynamic Media kann jedoch in beiden Farbräumen liefern.

Es gibt viele Kunden, die immer noch drucken, wie z. B. die Großhandelsclubs. Und es gibt Lebensmittelgeschäfte, die oft wöchentlich Flyer drucken. Diese Kunden verlangen, dass ihre Bilder in beiden Farbräumen vorliegen. Herkömmlicherweise wären dafür zwei verschiedene Bilder erforderlich: eines in RGB und eines in CMYK. Sie können jedoch CMYK-Assets direkt in Dynamic Media hochladen und RGB-Assets über eine Bildvorgabe oder ein Farbprofil automatisch von Dynamic Media bereitstellen lassen. Es besteht keine Notwendigkeit, mehrere Versionen einer Datei zu erstellen, sodass das Konzept der _Einen primären Asset-Datei mit unendlichen Möglichkeiten_ erhalten bleibt.

<!-- **The Value of Renditioning??? or Demo portion** -->

### Veröffentlichen und Anzeigen einer Vorschau von Assets

Nachdem Sie Assets in Dynamic Media hochgeladen haben, empfiehlt es sich, diese zu _veröffentlichen_, indem Sie die Assets auswählen und dann auf **[!UICONTROL Veröffentlichen]** oder **[!UICONTROL Quick Publish]** in Dynamic Media klicken. Das Veröffentlichen von Assets ist erforderlich, wenn Sie sie in einem Erlebnis verwenden möchten. Nach der Veröffentlichung stehen Ihnen die Assets zur Verfügung, um sie über eine von Dynamic Media generierte URL, die Sie kopieren, oder über das Einbetten von Code in die Seite in eine Webseite einzubinden.

Neben der manuellen Veröffentlichung von Assets können Sie Dynamic Media so konfigurieren, dass Sie Assets sofort – ohne Benutzereingriff – zum Zeitpunkt des Uploads veröffentlichen.

Nach dem Hochladen gibt es verschiedene Möglichkeiten, die Ausgabedarstellungen eines Assets in Dynamic Media in der Vorschau anzuzeigen. Die Vorschau von Ausgabedarstellungen kann Ihnen dabei helfen, eine Vorstellung davon zu erhalten, was ein Kunde sieht. Eine gängige Vorschaumethode besteht darin, ein Asset auszuwählen und dann seine Ausgabedarstellungen anzuzeigen, indem Sie eine _Bildvorgabe_ wie im Folgenden auswählen.

![Anzeigen einer Asset-Ausgabedarstellung basierend auf der Bildvorgabe „Groß“](/help/assets/dynamic-media/assets/dm-image-preset-with-url.png)
_Vorschau einer Asset-Ausgabedarstellung basierend auf der ausgewählten Bildvorgabe „Groß“. Es wurde auf die Schaltfläche „URL“ geklickt. Der resultierende URL-Pfad enthält den Namen der Bildvorgabe „Groß“ und kann in einer Webseite verwendet werden._

Die obige URL ist jetzt live! [Jetzt testen](http://s7d1.scene7.com/is/image/jpearldemo/AdobeStock_28563982?$Large$){target="_blank"}.

Eine andere Methode zur Vorschau eines Assets besteht darin, das Bild-Asset auszuwählen und dann eine _Viewer_-Vorgabe zu wählen, wie im Folgenden dargestellt.

![Vorschau eines Assets basierend auf der Viewer-Vorgabe „Vertikales Licht zoomen“](/help/assets/dynamic-media/assets/dm-viewer-preset.png)
_Vorschau eines Assets basierend auf der ausgewählten Viewer-Vorgabe „Vertikales Licht zoomen“. Der Mauszeiger (`+`) wurde über die Uhr bewegt, um hineinzuzoomen. Beachten Sie die Schaltflächen „URL“ und „Einbetten“._

Die obige Ausgabedarstelleung ist jetzt live! [Jetzt testen](https://s7d1.scene7.com/s7viewers/html5/ZoomVerticalViewer.html?asset=jpearldemo/AdobeStock_28563982&config=jpearldemo/ZoomVertical_light){target="_blank"}.

## Optional – Weitere Informationen

In Teil 1 dieser Journey wurden die Grundlagen verschiedener Dynamic Media-Themen behandelt. Wenn Sie mehr über das Gelesene erfahren möchten, nutzen Sie die folgenden Materialien, um die Konzepte zu vertiefen. Andernfalls können Sie mit Teil 2 Ihrer Tour fortfahren. Siehe [Nächste Schritte in dieser Dynamic Media-Tour](#whats-next).

<!--
_Dynamic Media Help topics_

* [Work with Dynamic Media in Experience Manager](/help/assets/dynamic-media/dynamic-media.md)
* [About Smart Imaging](/help/assets/dynamic-media/imaging-faq.md)
* [How to create Adaptive Video Sets](/help/assets/dynamic-media/video.md)
* [Best practices for optimizing the quality of your images](/help/assets/dynamic-media/best-practices-for-optimizing-the-quality-of-your-images.md)
* [How to upload assets](/help/assets/add-assets.md#upload-assets)
* [How to preview assets](/help/assets/dynamic-media/previewing-assets.md)
* [How to preview 3D assets](/help/assets/dynamic-media/previewing-3d-assets.md)
* [How to deliver Dynamic Media Assets](/help/assets/dynamic-media/delivering-dynamic-media-assets.md)
* [How to publish assets](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md)
* [Work with Selective Publish in Dynamic Media](/help/assets/dynamic-media/selective-publishing.md) -->

_Dynamic Media-Tutorials_

* [Verwenden von Dynamic Media mit Experience Manager Assets](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/dynamic-media-overview-feature-video-use.html?lang=de)
* [Adobe Experience Manager-Inhaltsbibliothek](https://experienceleague.adobe.com/de?lang=de#recommended/solutions/experience-manager) (Suche in _Dynamic Media_)

_Dynamic Media-Viewer_

* [Live-Demos](https://landing.adobe.com/en/na/dynamic-media/ctir-2755/live-demos.html) jedes Viewers

## Nächste Schritte in dieser Dynamic Media-Tour {#whats-next}

In Teil 2 dieser Journey werden Sie Dynamic Media-URLs näher untersuchen, um besser zu verstehen, was passiert, wenn ein Asset bereitgestellt wird. Außerdem erfahren Sie mehr über die Grundlagen der Erstellung von Bildvorgaben zum Rendern von Assets und lernen etwas über Bild-Sets, Rotations-Sets und Sets mit gemischten Medien und darüber, wie sie erstellt werden.

Hier geht es zu [Dynamic Media-Tour: Grundlagen, Teil 2](/help/assets/dynamic-media/dm-journey-part2.md#dm-journey-d).

<!-- Live as of April 28 2022. LEAVE IN HERE https://landing.adobe.com/en/na/dynamic-media/ctir-2755/index.html -->