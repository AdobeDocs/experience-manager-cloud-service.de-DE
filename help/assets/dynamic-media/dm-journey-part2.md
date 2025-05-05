---
title: Tour durch Dynamic Media, Teil II
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
exl-id: cdca41ad-a2cd-4f68-aaa4-5eec33c30f0b
source-git-commit: 36ab36ba7e14962eba3947865545b8a3f29f6bbc
workflow-type: tm+mt
source-wordcount: '2621'
ht-degree: 100%

---

# Dynamic Media-Tour: Grundlagen, Teil II  {#dm-journey-part2}

{{see-also-dm}}

Willkommen bei der Dynamic Media-Tour: Grundlagen, Teil II, bei der Sie Folgendes lernen können:

* Anatomie einer Dynamic Media-URL und wie Dynamic Media Inhalte bereitstellt.
* Grundlagen zum Erstellen von Bildvorgaben zum Rendern von Assets.
* Bildsets, Rotationssets und Sets mit gemischten Medien.

Siehe auch [Dynamic Media-Tour; Grundlagen, Teil I](/help/assets/dynamic-media/dm-journey-part1.md).

>[!TIP]
>
>Um die bestmöglichen Ergebnisse zu erzielen, empfiehlt Adobe, diese Dynamic Media-Tour auf einem Desktop-Computer zu lesen und anzuzeigen.

## Anatomie einer Dynamic Media-URL und wie Dynamic Media Inhalte bereitstellt {#dm-journey-d}

Nachdem Ihre Dynamic Media-Assets hochgeladen und veröffentlicht wurden, können Sie die erzeugte URL eines Assets kopieren und in Ihren Browser einfügen, um zu sehen, wie das Asset einem Kunden angezeigt wird. Die folgende kopierte URL für das Bild einer Armbanduhr ist farblich unterteilt, um das Lesen und Verstehen zu vereinfachen.

![Anatomie einer Dynamic Media-URL](/help/assets/dynamic-media/assets/dm-colored-url.png)
_Anatomie einer Dynamic Media-URL._

Der erste Teil der URL in Rot verweist auf die Serverdomain selbst. In diesem Fall wird Dynamic Media auf einer generischen Serverdomain ausgeführt, und zwar `https://s7d1.scene7.com/is/image/`. Das einfache Betrachten der Serverdomain macht es einfach, eine Reihe von Bildern anzuzeigen und zu verstehen, ob sie von Dynamic Media bereitgestellt werden. Die URL wird ziemlich konsistent sein. Es gibt jedoch einige Dynamic Media-Kunden, die zu einer dedizierten Serverdomain gewechselt haben, die möglicherweise wie `name-of-your-company.scene7.com` aussieht. Für die intelligente Bildbearbeitung ist eine dedizierte Serverdomain erforderlich.

Der lilafarbene Teil ist der Kontoname. In diesem Fall heißt das Konto `jpearldemo`.

Die Asset-ID oder der Name, `AdobeStock_28563982`, ist grün. Beachten Sie, dass das Asset _keine_ Dateierweiterung wie `.png` oder `.jpg` hat. Wenn Assets in Dynamic Media aufgenommen werden, wird die Dateierweiterung entfernt und eine andere Art von Datei erstellt: eine Pyramid-TIFF-Datei. Mit der Pyramic-TIFF können Dynamic Media schnell Ausgabedarstellungen erstellen.

Und schließlich gibt es einige Bildverarbeitungsparameter, `?wid=1000&fmt=jpeg&qlt=85`, die am Ende in gelb angezeigt werden.

Der gesamte URL-Pfad ist live. [Jetzt ausprobieren](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock_28563982?wid=1000&amp;fmt=jpeg&amp;qlt=85){target="_blank"}.

Wenn Ihr Browserfenster immer noch für die Dynamic Media-URL und das Bild der Armbanduhr geöffnet ist, schauen wir uns näher an, wie Sie Bildausgabedarstellungen erstellen können, indem Sie einfach die URL ändern.

### Rendern des Bildes der Armbanduhr über die URL

Beginnen Sie, indem Sie nur die Bildverarbeitungsregeln im URL-Pfad manuell löschen. Behalten Sie den Servernamen, den Kontonamen und die Asset-ID oder den Bildnamen bei. [Jetzt ausprobieren](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock_28563982){target="_blank"}.

Fügen Sie nun am Ende der URL einen Bildverarbeitungsparameter hinzu. Geben Sie im Feld URL rechts neben dem Bildnamen `?wid=500` ein und drücken Sie dann die **[!UICONTROL Eingabetaste]**. [Jetzt ausprobieren](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock%5F28563982?wid=500){target="_blank"}.

Beachten Sie, dass eine neue Ausgabedarstellung der Uhr erzeugt wird. Eine wichtige Erkenntnis aus dieser einfachen Übung, die Breite des Bildes zu ändern, ist, dass das betrachtete Bild zu 100 % dynamisch erzeugt wird.

Ändern Sie jetzt den Breitenwert von `500` Pixel zu `1000` Pixel und drücken Sie dann die **[!UICONTROL Eingabe]**. [Jetzt ausprobieren](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock%5F28563982?wid=1000){target="_blank}.
In dem Moment, in dem Sie die **[!UICONTROL Eingabetaste]** drücken, kehrt der Browser zum Dynamic Media-Bildserver zurück. Er erzeugt eine brandneue Ausgabedarstellung der Uhr, basierend auf dem neuen Breitenwert, den Sie gerade eingegeben haben, und stellt dann das neue Bild zurück zum Browser bereit und speichert es im Cache.

Dynamic Media verfügt über zahlreiche Bildverarbeitungsparameter, mit denen Sie Ihre Bild-Assets auf Webseiten optimieren können. [Eine Liste davon können Sie hier einsehen](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html?lang=de).

Versuchen Sie jetzt, dem Bild der Uhr einen Rotationsparameter hinzuzufügen. Geben Sie am Ende des URL-Pfads, unmittelbar nach `wid=1000`, `&rotate=90` ein, und drücken Sie die **[!UICONTROL Eingabetaste]**. [Jetzt ausprobieren](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock%5F28563982?wid=1000&amp;rotate=90){target="_blank"}.

Die Uhr ist immer noch leicht nach links geneigt. Ändern Sie den Drehwert von `90` nach `92`und drücken Sie dann die **[!UICONTROL Eingabetaste]**. [Jetzt probieren](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock%5F28563982?wid=1000&amp;rotate=9){target="_blank"}.

Auch hier wird in dem Moment, in dem Sie die **[!UICONTROL Eingabetaste]** drücken, fast augenblicklich eine neue Ausgabedarstellung der Uhr erzeugt. Sie können die Leistung, die Sie erhalten, nachvollziehen, wenn Sie verstehen, dass Dynamic Media an einem arbeitsreichen Wochenende oder an einem großen Feiertag mehr als 800.000 Bildanfragen _pro Sekunde_ liefern kann.

Es ist zwar möglich, Bildverarbeitungsparameter in einer URL auf Bild-für-Bild-Basis zu ändern, aber das ist keine effiziente Methode, insbesondere wenn Sie Zehntausende von Bildern auf Ihrer Website haben. Eine viel bessere Herangehensweise ist die Verwendung von Bildvorgaben.

## Grundlagen zum Erstellen von Bildvorgaben zum Rendern von Assets {#dm-journey-e}

Es gibt mehrere Möglichkeiten und Orte, an denen Sie ein Bild erstellen oder ein Bild verfügbar machen sollten. Traditionell geht ein Kreativer in Adobe Photoshop und speichert jede dieser verschiedenen Ausgabedarstellungen als statisches Bild ab.

![Statische Bilder](/help/assets/dynamic-media/assets/dm-static-images.png)
_Gut: statische Bilder, jeweils manuell erstellt._

Stellen Sie sich vor, wie der Creative Director sich die Bilder anschaut und sagt:

_„Bei dieser Aufnahme wollte ich unbedingt, dass der große Zeiger auf die Vier und der kleine Zeiger auf die 1 zeigt, damit das Zifferblatt besser zu erkennen ist.“_

Das Kreativ-Team müsste alle neuen statischen Bilder erneut aufnehmen.

Mit Dynamic Media können Sie jedoch, wenn Sie verschiedene Bildvorgaben haben, diese Bilder überall dort verwenden, wo Sie sie benötigen. Mit den Bildvorgaben werden Standards durchgesetzt.

![Ansatz der primären Datei](/help/assets/dynamic-media/assets/dm-onefile.png)
_Best Practice: eine Datei mit mehreren Ausgabedarstellungen, z. B. `Search_Grid` und `Thumbnail`, die dynamisch mithilfe von Bildvorgaben erstellt werden._

| **Wozu dienen Bildvorgaben?** | |
|---|---|
| Standards | Bildvorgaben erzwingen eine Standardbildbearbeitung für jedes Bild, für das sie angefordert wird. |
| Änderungsverwaltung | Wenn Sie die Bildverarbeitung ändern müssen, bearbeiten Sie einfach den Parameter der vorhandenen Bildvorgabe. Die aktualisierte Definition wird automatisch für alle Anfragen übernommen. |

Überall dort, wo Sie eine bestimmte Art von Bild benötigen, z. B. auf

* einer Produktdetailseite,
* Suchmaske,
* Miniaturansicht,
* Einkaufskarte oder
* Hero-Bild,

Sie möchten, dass diese Bilder mit denselben Parametern bereitgestellt werden, wo auch immer sie verwendet werden.

Sehen wir uns kurz an, wie man in Dynamic Media eine Bildvorgabe erstellt.

![Erstellen einer Bildvorgabe ausgehend von der Registerkarte „Allgemein“](/help/assets/dynamic-media/assets/dm-image-preset-basictab.png)
_Erstellen einer Bildvorgabe ausgehend von der Registerkarte „Allgemein“._

Im obigen Beispiel können Sie sehen, dass eine neue Bildvorgabe mit dem Namen _Medium_ erstellt wurde. Dynamic Media verwendet ein vorkonfiguriertes Beispielbild – den Rucksack –, damit Sie die Merkmale der Bildvorgabe bei der Erstellung sehen können.

Die Bildvorgabe _Medium_ hat eine Breite von 500 Pixel und eine Höhe von 800 Pixel. In Teil I dieser Tour erfahren Sie mehr über die Bereitstellung von Assets in verschiedenen Formaten. Aus dem Pulldown-Menü **[!UICONTROL Format]** können Sie Assets als JPEG, PNG, TIFF oder in mehreren anderen Formaten bereitstellen. Hier haben Sie Flexibilität.

Wenn Sie die Registerkarte **[!UICONTROL Erweitert]** wählen, erhalten Sie Optionen für den Farbraum des Assets. Je nach dem Format, das Sie in der Registerkarte **[!UICONTROL Allgemein]** ausgewählt haben – im obigen Beispiel wurde JPEG ausgewählt – können Sie Assets in RGB, Graustufen oder CMYK bereitstellen. Aus dem Pulldown-Menü **[!UICONTROL Farbprofil]** können Sie auswählen, wie ein CMYK-Bild-Asset zum Drucken bereitgestellt werden soll. Beachten Sie auch, dass es zusätzliche Parameter gibt, die Sie für das Scharfzeichnen Ihrer Bilder anwenden können. In diesem Fall wurde die **[!UICONTROL Unschärfemaske]** angewendet.

![Erstellen einer Bildvorgabe durch Auswahl von Optionen auf der Registerkarte „Erweitert“](/help/assets/dynamic-media/assets/dm-image-preset-advancedtab.png)
_Erstellen einer Bildvorgabe durch Auswahl von Optionen auf der Registerkarte „Erweitert“._

Sie erinnern sich, dass Sie in [Anatomie einer Dynamic Media URL](#dm-journey-d) bereits über die Dynamic Media URL gelesen haben und darüber, wie diese aufgebaut ist. In das Textfeld **[!UICONTROL Bildmodifikator]** können Sie alle gewünschten zusätzlichen Bildverarbeitungsparameter eingeben. Wenn Ihre Bilder bereitgestellt werden, werden die Parameter unter Verwendung der Vorgabe in den Vorgabenamen der URL aufgenommen. Im obigen Screenshot wurde der Parameter `bgc=451B15` hinzugefügt. Das heißt, es wurde eine dunkelbraune Hintergrundfarbe hinzugefügt.

Sie können sich eine Bildvorgabe als Rezept für Ihre Bilder vorstellen. Alle Bilder, die diese Vorgabe verwenden, werden konsistent und jedes Mal gleich aussehen. Der Parameter `&op_brightness=+10` wurde hinzugefügt, um die Helligkeit etwas zu erhöhen.

Wenn Sie fertig sind, speichern Sie die Vorgabe. Jetzt ist sie für alle Bilder verfügbar, die Sie haben. In diesem Fall möchten Sie die Bildvorgabe _Medium_ auf das Bild einer Schüssel mit flüssiger Schokolade anwenden.

![Anwenden der Bildvorgabe *Medium*, um eine Ausgabedarstellung eines Bildes zu erzeugen](/help/assets/dynamic-media/assets/dm-medium-image-preset.png)
_Anwenden der Bildvorgabe „Medium“, um eine Ausgabedarstellung eines Bildes zu erzeugen._

Kopieren Sie die URL und fügen Sie sie dann in Ihren Browser ein, um das Erscheinungsbild des Bildes zu überprüfen. [Jetzt ausprobieren](http://s7d1.scene7.com/is/image/jpearldemo/AdobeStock_74043302?$Medium$){target="_blank"}.

Beachten Sie in Ihrem Browser den Namen der Bildvorgabe _Medium_ im vollständigen URL-Pfad.

Sie können die Art der Helligkeit sehen, die im Bild angezeigt wird. Diese Qualität ist teilweise auf die Art und Weise zurückzuführen, wie die Schokolade aufgenommen wurde. Das liegt zum Teil auch daran, dass Sie mit Dynamic Media größere Bilder speichern können als die, die über digitale Kanäle bereitgestellt werden.

Wenn alles für Ihre Schale Schokolade zufriedenstellend aussieht, fügen Sie die URL in Ihre Webseiten ein, wo das Bild auf Ihrer Website erscheinen soll.

Wenn Sie sich das Bild der Uhr noch einmal ansehen, können Sie sehen, dass es eine `Cart`-Bildvorgabe, eine `Grid`-Vorgabe, eine `Large`-Vorgabe, eine `PDP-page`-Vorgabe (Produktdetailseite) und mehrere andere gibt.

![Statische und dynamische Bildvorgaben](/help/assets/dynamic-media/assets/dm-image-presets.png)
_Statische und dynamische Bildvorgaben. Das Bild der Uhr wurde mit der `PDP-page`-Bildvorgabe gerendert._

Aber was ist, wenn Sie ein Bild auf Ihrer Website ändern müssen? Angenommen, Sie haben einige Tests durchgeführt und festgestellt, dass Sie das Bild von 120 x 120 (die `Cart`-Bildvorgabe) nicht so erhalten, wie Sie dachten. Sie müssen das Bild vergrößern, indem Sie die Breite und die Höhe auf 175 Pixel erhöhen. Traditionell müssten Sie in Adobe Photoshop gehen und all diese Warenkorbbilder neu erstellen. Mit Dynamic Media bearbeiten Sie jedoch einfach die Bildvorgabe, indem Sie die Werte für Breite und Höhe auf 175 ändern und die Vorgabe speichern, wie im folgenden Beispiel gezeigt.

![Bearbeiten einer Bildvorgabe](/help/assets/dynamic-media/assets/dm-edit-image-preset.png)
_Bearbeiten der Breite und Höhe des `Cart` Bildvorgabe._

Nachdem Sie Ihre Bildvorgabe geändert und den Cache geleert haben, werden alle Bilder aktualisiert, und alle URLs, die mit dieser Vorgabe verwendet werden, ändern sich _nicht_ mehr. Das bedeutet, dass keine fehlerhaften Links und keine Umleitungen auf Webseiten erforderlich sind.

## Bildsets, Rotationssets und Sets mit gemischten Medien {#dm-journey-f}

Zu den beliebtesten Einsatzbereichen von Dynamic Media gehört die Möglichkeit, Bildsets, Rotationssets und Sets mit gemischten Medien zu erstellen.

Bildsets bestehen normalerweise aus einer Reihe von Bild-Assets, die als einzelne Entität dargestellt werden. Diese Art von Sets bietet Benutzerinnen und Benutzern ein integriertes Betrachtungserlebnis, bei dem die Benutzerinnen und Benutzer durch Klicken auf ein Miniaturbild verschiedene Ansichten eines Elements sehen können. Mit Bildsets können Sie alternative Ansichten eines Elements darstellen. Dabei bietet der Viewer Zoomtools, mit denen Bilder genauer betrachtet werden können. [Anzeigen eines Bildsets namens „Laufen“, das den Flyout-Viewer verwendet](https://s7d1.scene7.com/s7viewers/html5/FlyoutViewer.html?asset=jpearldemo/Running).

Hier in Dynamic Media können Sie mehrere Bilder von Laufschuhen sehen. Es handelt sich um eine Produktserie, von der Vertrieb und Marketing wollen, dass die Kundinnen und Kunden sie als eine einzige Präsentation sehen, als ein Bildset.

![Erstellen eines Bildsets](/help/assets/dynamic-media/assets/dm-create-image-set.png)
_Der Beginn der Erstellung eines Bildsets._

Um das Bildset zu erstellen, wählen Sie **[!UICONTROL Bildset]** aus dem Pulldown-Menü **[!UICONTROL Erstellen]**. Beachten Sie, dass im Menü auch Optionen zum Erstellen eines **[!UICONTROL Sets mit gemischten Medien]**, **[!UICONTROL Rotationssets]** und **[!UICONTROL Karussellsets]** vorhanden sind. Sie erstellen diese Sets auf ähnliche Weise wie Bildsets.

Ein Set mit gemischten Medien kann Bilder, Mustersets, Rotationssets, Videos und Sets mit adaptiven Videos enthalten. [Probieren Sie es jetzt aus](https://s7d9.scene7.com/s7viewers/html5/MixedMediaViewer.html?asset=Scene7SharedAssets/Mixed_Media_Set_Sample). Ein Rotationsset simuliert das Drehen eines Gegenstands zur genaueren Untersuchung. Rotationssets ermöglichen es, wichtige visuelle Details aus jedem Blickwinkel anzuzeigen. [Jetzt ausprobieren](https://s7d9.scene7.com/s7viewers/html5/SpinViewer.html?asset=Scene7SharedAssets/SpinSet_Sample&amp;stagesize=500,400){target="_blank"}.

Das Erstellen eines Bildsets ist unkompliziert. Fügen Sie einfach die Bild-Assets hinzu, die Sie in das Set aufnehmen möchten.

![Erstellen eines Bildsets](/help/assets/dynamic-media/assets/dm-create-image-set-add-assets.png)
_Mit dem Bildset-Editor können Sie Bild-Assets hinzufügen und ihre Darstellung im Set neu anordnen._

Sie müssen dem Set einen Namen geben. Wählen Sie den Namen sorgfältig aus, da Sie ihn später nicht mehr bearbeiten können! Im obigen Beispiel wird der Satz `Running` genannt. Wenn Sie fertig sind, speichern Sie das Set.

Und hier ist das Bildset `Running` in Experience Manager Assets.

![Das Bildset „Laufen“ in Experience Manager Assets, Kartenansicht](/help/assets/dynamic-media/assets/dm-image-set.png)
_Das Bildset `Running` in Experience Manager Assets, Kartenansicht._

Unabhängig davon, ob Sie ein Bildset, ein Set mit gemischten Medien, ein Rotationsset oder ein anderes interaktives Medium erstellt haben, sollten Sie sehen, wie es nach dem Erstellen des Sets aussieht und sich für einen Kunden verhält. Dynamic Media verfügt über zahlreiche integrierte Viewer, mit denen Sie genau das tun können.

Wählen Sie zunächst das erstellte Bildset aus, um es wie im folgenden Beispiel in einer Vorschau zu öffnen.

![Das Bildset „Laufen“ in der Vorschau, mit ausgewählter Option „Viewer“](/help/assets/dynamic-media/assets/dm-image-set-viewer.png)
_Das Bildset `Running` in der Vorschau, mit ausgewählter Option „Viewer“._

Beachten Sie in der Vorschau, dass Sie die Muster für Laufschuhe auswählen und die Schuhe vergrößern und verkleinern können. Um einen Viewer auf das Set anzuwenden, wählen Sie aus dem Pulldown-Menü **[!UICONTROL Viewer]** aus.

![Das Bildset „Laufen“, auf das der Flyout-Viewer angewendet wurde](/help/assets/dynamic-media/assets/dm-image-set-flyout-viewer.png)
_Das Bildset `Running`, auf das der Flyout-Viewer angewendet wurde._

In diesem Fall wurde der Viewer `Flyout` ausgewählt. An dieser Stelle können Sie eine Vorschau des Bildsets im Viewer anzeigen. Es ist jedoch am besten, es in Ihrem Browser zu sehen, soe wie es auch ein Kunde sieht. Wählen Sie **[!UICONTROL URL]** in der linken unteren Ecke aus, kopieren Sie die URL und fügen Sie sie in Ihren Browser ein. [Jetzt ausprobieren](https://s7d1.scene7.com/s7viewers/html5/FlyoutViewer.html?asset=jpearldemo/Running&amp;config=jpearldemo/Flyout){target="_blank"}.

Mit der einzelnen URL können Sie das Bildset und den Viewer verwenden, wo Sie sie auf Ihrer Website benötigen. Im vorherigen Beispiel haben Sie möglicherweise bemerkt, dass **[!UICONTROL Einbetten]** rechts neben der URL-Schaltfläche steht. Durch Auswahl von **[!UICONTROL Einbetten]** können Sie den Code für dieses Bildset / diesen Viewer kopieren und zu einer Web-Seite oder Experience Manager Sites-Komponente hinzufügen.

Der Flyout-Viewer ist ein standardmäßiger, vorkonfigurierter Viewer, dessen Eigenschaften Sie bearbeiten können. Sie können aber auch, genau wie bei der Erstellung einer Bildvorlage, einen eigenen, benutzerdefinierten Viewer erstellen.

Angenommen, Ihrem Verkaufs- und Marketing-Team gefällt der Flyout-Viewer nicht. Sie mögen die Zoom-Funktion, möchten aber, dass Kunden den Zoom-Effekt direkt über den Schuhen sehen. In diesem Fall wenden Sie einfach den Viewer InlineZoom auf das Bildset an und kopieren und fügen die URL in Ihren Browser ein, um zu sehen, wie es sich verhält. [Jetzt ausprobieren](https://s7d1.scene7.com/s7viewers/html5/FlyoutViewer.html?asset=jpearldemo/Running&amp;config=jpearldemo/InlineZoom){target="_blank"}.

Wenn Sie den Mauszeiger über den Schuh bewegen, zoomen Sie in das Bild ein, und Sie können mehr Details sehen, wenn Sie den Mauszeiger hin und her bewegen. Der Grund dafür ist einfach die Größe des Bildes, das ursprünglich in Dynamic Media hochgeladen wurde.

Wenn man über sein Leben als Verbraucher nachdenkt, oder wenn man in seiner täglichen Rolle arbeitet, und wenn man auf verschiedene Websites geht, sieht man Dinge wie diese. Denken Sie darüber nach, wie das gemacht wird und wie Sie die Leistung von Dynamic Media in Ihrer eigenen Arbeit und auf der Website Ihres Unternehmens nutzen können.

Sie haben sich gerade über Bildsätze und Viewer informiert. Sehen wir uns einige andere Viewer an und probieren sie für einzelne Assets aus. Um den Viewer zurückzusetzen, klicken Sie auf die Schaltfläche **[!UICONTROL Aktualisieren]** in der linken unteren Ecke.

<!-- LEAVE THIS HIDDEN PATH IN THE DOCUMENTATION FOR DEMO PURPOSES [Flyout viewer with image set](http://www.partycity.com/girls-little-old-lady-costume-P750948.html) -->

* Viewer `ZoomVertical_dark`, der auf ein Bild-Asset angewendet wwurde. [Jetzt ausprobieren](https://s7d1.scene7.com/s7viewers/html5/ZoomVerticalViewer.html?asset=jpearldemo/AdobeStock_96311480&amp;config=jpearldemo/ZoomVertical_dark){target="_blank"}.
* Viewer `Zoom_light`, der auf ein Bild angewendet wurde. [Jetzt ausprobieren](https://s7d1.scene7.com/s7viewers/html5/BasicZoomViewer.html?asset=jpearldemo/AdobeStock_38827423&amp;config=jpearldemo/Zoom_light){target="_blank"}.

## Optional – Weitere Informationen

Wenn Sie mehr darüber erfahren möchten, was Sie gerade gelesen haben, nutzen Sie die unten stehenden Materialien, um Konzepte genauer zu erkunden. Ansonsten ist Ihre Dynamic Media-Tour abgeschlossen!

<!--
_Dynamic Media Help topics_

* [How to create image presets](/help/assets/dynamic-media/image-presets.md)
* A list of [image processing parameters](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html?lang=de) that you can use in the Image Modifier field when you create an image preset
* [How to preview assets](/help/assets/dynamic-media/previewing-assets.md)
* [How to preview 3D assets](/help/assets/dynamic-media/previewing-3d-assets.md)
* [How to create Image sets](/help/assets/dynamic-media/image-sets.md)
* [How to create Spin sets](/help/assets/dynamic-media/spin-sets.md)
* [How to create Mixed Media sets](/help/assets/dynamic-media/mixed-media-sets.md) -->

_Dynamic Media-Tutorials_

* [Verwenden von Dynamic Media mit Experience Manager Assets](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/dynamic-media-overview-feature-video-use.html?lang=de)
* [Adobe Experience Manager-Inhaltsbibliothek](https://experienceleague.adobe.com/de?lang=de#recommended/solutions/experience-manager) (Suche in _Dynamic Media_)

_Dynamic Media-Viewer_

* [Live-Demos](https://landing.adobe.com/en/na/dynamic-media/ctir-2755/live-demos.html) jedes Viewers

<!-- Live as of April 28 2022. LEAVE IN HERE https://landing.adobe.com/en/na/dynamic-media/ctir-2755/index.html -->