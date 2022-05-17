---
title: Dynamic Media Journey, Teil II
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
exl-id: cdca41ad-a2cd-4f68-aaa4-5eec33c30f0b
source-git-commit: e16d107dff1817e8b62de86e295590b13d853bf0
workflow-type: tm+mt
source-wordcount: '2877'
ht-degree: 1%

---

# Dynamic Media Journey: Grundlagen, Teil II  {#dm-journey-part2}

Willkommen bei Dynamic Media Journey: Grundlagen, Teil II, wo Sie Folgendes erfahren können:

* Anatomie einer Dynamic Media-URL und wie Dynamic Media Inhalte bereitstellt
* Grundlagen zum Erstellen von Bildvorgaben zum Rendern von Assets
* Bildsets, Rotationssets und Sets für gemischte Medien

Siehe auch [Dynamic Media Journey; Grundlagen, Teil I](/help/assets/dynamic-media/dm-journey-part1.md).

>[!TIP]
>
>Um die bestmöglichen Ergebnisse zu erzielen, empfiehlt Adobe, diese Dynamic Media-Journey auf einem Desktop-Computer zu lesen und anzuzeigen.

## Anatomie einer Dynamic Media-URL und wie Dynamic Media Inhalte bereitstellt {#dm-journey-d}

Nachdem Ihre Dynamic Media-Assets hochgeladen und veröffentlicht wurden, können Sie die generierte URL eines Assets kopieren und in Ihren Browser einfügen, um zu sehen, wie das Asset einem Kunden angezeigt wird. Die folgende kopierte URL für ein Überwachungsbild ist farblich unterteilt, um das Lesen und Verstehen zu vereinfachen.

![Anatomie einer Dynamic Media-URL](/help/assets/dynamic-media/assets/dm-colored-url.png)
_Anatomie einer Dynamic Media-URL._

Der erste Teil der URL in Rot verweist auf die Serverdomäne selbst. In diesem Fall wird Dynamic Media auf einer generischen Serverdomäne ausgeführt, d. h. `https://s7d1.scene7.com/is/image/`. Es ist einfach, eine Reihe von Bildern anzuzeigen und zu verstehen, ob sie von Dynamic Media bereitgestellt werden, indem man sich nur die Serverdomäne ansieht. Die URL wird ziemlich konsistent sein. Es gibt jedoch einige Dynamic Media-Kunden, die zu einer dedizierten Serverdomäne gewechselt haben, in der sie möglicherweise `name-of-your-company.scene7.com`. Für die intelligente Bildbearbeitung ist eine dedizierte Server-Domäne erforderlich.

Der Kontoname ist der lilafarbene Teil. In diesem Fall wird das Konto aufgerufen `jpearldemo`.

Die Asset-ID oder der Name, `AdobeStock_28563982` ist grün. Beachten Sie, dass das Asset _no_ Dateierweiterung wie `.png` oder `.jpg`. Wenn Assets in Dynamic Media aufgenommen werden, wird die Dateierweiterung entfernt und eine andere Art von Datei erstellt: eine Pyramid-TIFF-Datei. Mit der Pyramic-TIFF können Dynamic Media schnell Ausgabeformate erstellen.

Und schließlich gibt es einige Bildverarbeitungsparameter, `?wid=1000&fmt=jpeg&qlt=85`, wird am Ende gelb angezeigt.

Der gesamte URL-Pfad ist live. [Jetzt testen](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock_28563982?wid=1000&amp;fmt=jpeg&amp;qlt=85).

Wenn Ihr Browserfenster immer noch für die Dynamic Media-URL und das Überwachungsbild geöffnet ist, schauen wir uns näher an, wie Sie Bildausgabeformate erstellen können, indem Sie einfach die URL ändern.

### Rendern des überwachten Bildes über die URL

Beginnen Sie, indem Sie nur die Bildverarbeitungsregeln im URL-Pfad manuell löschen. Behalten Sie den Servernamen, den Kontonamen und die Asset-ID oder den Bildnamen bei. [Jetzt testen](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock_28563982).

Fügen Sie nun am Ende der URL einen Bildverarbeitungsparameter hinzu. Geben Sie im Feld URL rechts neben dem Bildnamen `?wid=500`und drücken Sie dann **[!UICONTROL Eingabe]**. [Jetzt testen](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock%5F28563982?wid=500).

Beachten Sie, dass eine neue Ausgabe der Uhr generiert wird. Ein Schlüssel zum Verständnis aus dieser einfachen Übung der Änderung der Bildbreite ist, dass das angezeigte Bild 100 % dynamisch generiert wird.

Ändern Sie jetzt den Breitenwert von `500` Pixel zu `1000` Pixel und drücken Sie dann die **[!UICONTROL Eingabe]**. [Jetzt testen](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock%5F28563982?wid=1000).
Der Moment, in dem du drückst **[!UICONTROL Eingabe]**, kehrt der Browser zum Dynamic Media-Bildserver zurück. Es generiert eine brandneue Ausgabe der Uhr, basierend auf dem neuen Breitenwert, den Sie gerade eingegeben haben, und stellt dann das neue Bild zurück zum Browser bereit und speichert es im Cache.

Dynamic Media verfügt über zahlreiche Bildverarbeitungsparameter, mit denen Sie Ihre Bild-Assets auf Webseiten optimieren können. Sie können [Eine Liste davon finden Sie hier .](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html?lang=en).

Versuchen Sie jetzt, dem überwachten Bild einen Rotationsparameter hinzuzufügen. Und das Ende des URL-Pfads, unmittelbar nach `wid=1000`, Typ `&rotate=90`und drücken Sie dann **[!UICONTROL Eingabe]**. [Jetzt testen](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock%5F28563982?wid=1000&amp;rotate=90).

Die Uhr ist immer noch etwas nach links verzerrt. Ändern Sie den Drehwert von `90` nach `92`und drücken Sie dann **[!UICONTROL Eingabe]**. [Jetzt testen](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock%5F28563982?wid=1000&amp;rotate=9)

Wieder, wenn Sie drücken **[!UICONTROL Eingabe]**, wird fast sofort eine neue Ausgabe der Uhr erzeugt. Sie können die Art der Leistung sehen, die Sie erhalten. Dies erklärt, warum Dynamic Media mehr als 800.000 Bildanforderungen bereitstellen kann. _pro Sekunde_, an einem anstrengenden Wochenende oder in großen Feiertagen.

Es ist zwar möglich, Bildverarbeitungsparameter in einer URL auf Bild-für-Bild-Basis zu ändern, aber es ist keine effiziente Methode, insbesondere wenn Sie Zehntausende von Bildern auf Ihrer Website haben. Eine viel bessere Herangehensweise ist die Verwendung von Bildvorgaben.

## Grundlagen zum Erstellen von Bildvorgaben zum Rendern von Assets {#dm-journey-e}

Es gibt mehrere Möglichkeiten und Orte, an denen Sie ein Bild erstellen oder ein Bild verfügbar machen möchten. Traditionell fließt ein Kreativ in Adobe Photoshop und speichert jede dieser verschiedenen Ausgabedarstellungen als statische Bilder.

![Statische Bilder](/help/assets/dynamic-media/assets/dm-static-images.png)
_Gut: statische Bilder, jeweils manuell erstellt._

Stellen Sie sich vor, die Creative Director schaut sich die Bilder an und sagt:

_&quot;Ich wollte diesen Schuss wirklich, damit die große Hand auf die vier zeigt und die kleine Hand auf die 1 zeigt, um das Uhrendiagramm leichter zu sehen.&quot;_

Das Kreativteam müsste all diese neuen statischen Bilder erneut aufnehmen.

Mit Dynamic Media können Sie jedoch, wenn Sie verschiedene Bildvorgaben haben, diese Bilder überall dort verwenden, wo Sie sie benötigen. Mit den Bildvorgaben werden Standards erzwungen.

![Primärer Dateiansatz](/help/assets/dynamic-media/assets/dm-onefile.png)
_Best: eine Datei mit mehreren Ausgabeformaten, die dynamisch mithilfe von Bildvorgaben erstellt werden, z. B. `Search_Grid` und `Thumbnail`._

| **Wozu dienen Bildvorgaben?** |  |
|---|---|
| Standards | Bildvorgaben erzwingen eine standardmäßige Bildverarbeitung für alle Bilder, mit denen sie angefordert werden. |
| Änderungsverwaltung | Wenn Sie die Bildverarbeitung ändern müssen, bearbeiten Sie einfach den Parameter der vorhandenen Bildvorgabe. Die aktualisierte Definition wird automatisch für alle Anforderungen übernommen. |

Jeder Ort, an dem Sie einen bestimmten Bildtyp benötigen, z. B.

* eine Produktdetailseite,
* Suchraster,
* thumbnail,
* Einkaufskarte oder
* Hero-Bild

Sie möchten, dass das Bild mit denselben Parametern bereitgestellt wird, wo immer es verwendet werden soll.

Sehen wir uns kurz an, wie eine Bildvorgabe in Dynamic Media erstellt wird.

![Erstellen einer Bildvorgabe, die mit der Registerkarte &quot;Standard&quot;beginnt](/help/assets/dynamic-media/assets/dm-image-preset-basictab.png)
_Erstellen einer Bildvorgabe, die mit der Registerkarte Allgemein beginnt._

Im obigen Beispiel können Sie sehen, dass eine neue Bildvorgabe mit dem Namen erstellt wurde _Mittel_. Dynamic Media verwendet ein natives Beispielbild - den Rucksack -, um Ihnen bei der Erstellung die Eigenschaften der Bildvorgabe anzuzeigen.

Die _Mittel_ Die Bildvorgabe hat eine Breite von 500 Pixel und eine Höhe von 800 Pixel. In Teil I dieser Journey erfahren Sie mehr über die Bereitstellung von Assets in verschiedenen Formaten. Aus dem **[!UICONTROL Format]** Pulldown-Menü können Sie Assets als JPEG, PNG, TIFF oder mehrere andere Formate bereitstellen. Du hast hier Flexibilität.

Auswählen der **[!UICONTROL Erweitert]** bietet Optionen für den Farbraum des Assets. Je nach dem Format, das Sie im **[!UICONTROL Allgemein]** Registerkarte - im obigen Beispiel wurde JPEG ausgewählt - Sie können Assets in RGB, Graustufen oder CMYK bereitstellen. Aus dem **[!UICONTROL Farbprofil]** Pulldown-Menü können Sie auswählen, wie ein CMYK-Bild-Asset zum Drucken bereitgestellt werden soll. Beachten Sie auch, dass es zusätzliche Parameter gibt, die Sie für das Scharfzeichnen Ihrer Bilder anwenden können. In diesem Fall **[!UICONTROL Unschärfemaske]** angewendet wurde.

![Erstellen einer Bildvorgabe durch Auswahl von Optionen auf der Registerkarte Erweitert](/help/assets/dynamic-media/assets/dm-image-preset-advancedtab.png)
_Erstellen einer Bildvorgabe durch Auswahl von Optionen auf der Registerkarte Erweitert ._

Sie erinnern sich an [Anatomie einer Dynamic Media-URL](#dm-journey-d) vorhin, dass Sie über die Dynamic Media-URL und deren Aufbau gelesen haben. Die **[!UICONTROL Bild-Modifikator]** in das Textfeld eingeben, wo Sie beliebige zusätzliche Bildverarbeitungsparameter eingeben können. Die Parameter werden mithilfe der Vorgabe in den Vorgabennamen der URL aufgenommen, wenn die Bilder bereitgestellt werden. Im obigen Screenshot wird der Parameter `bgc=451B15` hinzugefügt wurde. Das heißt, es wurde eine dunkelbraune Hintergrundfarbe hinzugefügt.

Sie können sich eine Bildvorgabe als Rezept für Ihre Bilder vorstellen. Es werden alle Bilder bereitgestellt, die die Vorgabe konsistent und jedes Mal verwenden. es wird gleich sein. Der Parameter `&op_brightness=+10` wurde hinzugefügt, um die Helligkeit etwas zu erhöhen.

Wenn Sie fertig sind, speichern Sie die Vorgabe und jetzt ist sie für alle Bilder verfügbar, die Sie haben. In diesem Fall möchten wir die _Mittel_ Bildvorgabe auf ein Bild einer Schüssel mit flüssiger Schokolade.

![Anwenden der Bildvorgabe *Mittel* , um eine Bilddarstellung zu generieren](/help/assets/dynamic-media/assets/dm-medium-image-preset.png)
_Anwenden der Bildvorgabe &quot;Medium&quot;, um eine Ausgabe eines Bildes zu generieren._

Kopieren Sie die URL und fügen Sie sie dann in Ihren Browser ein, um das Erscheinungsbild des Bildes zu überprüfen. [Jetzt testen](http://s7d1.scene7.com/is/image/jpearldemo/AdobeStock_74043302?$Medium$). Beachten Sie in Ihrem Browser den Namen der Bildvorgabe. _Mittel_ im vollständigen URL-Pfad.

Sie können die Art der Klarheit sehen, die im Bild angezeigt wird. Diese Qualität ist teilweise auf die Art und Weise zurückzuführen, wie die Schokolade geschossen wurde. Dies liegt auch daran, dass Sie mit Dynamic Media größere Bilder speichern können, als für digitale Kanäle bereitgestellt werden.

Wenn alles für Ihre Schokoladenschale zufriedenstellend aussieht, fügen Sie die URL in Ihre Webseiten ein, auf denen das Bild auf Ihrer Website erscheinen soll.

Wenn Sie sich das nachfolgende Bild erneut ansehen, können Sie sehen, dass es eine `Cart` Bildvorgabe, eine `Grid` -Vorgabe, eine `Large` -Vorgabe, eine `PDP-page` Voreinstellung (Produktdetailseite) und einige andere.

![Statische und dynamische Bildvorgaben](/help/assets/dynamic-media/assets/dm-image-presets.png)
_Statische und dynamische Bildvorgaben. Das überwachte Bild wurde mit dem `PDP-page` Bildvorgabe._

Aber was ist, wenn Sie ein Bild auf Ihrer Website ändern müssen? Angenommen, Sie haben einige Tests durchgeführt und festgestellt, dass das Bild von 120 x 120 (das `Cart` -Bildvorgabe) nicht so erhalten, wie Sie dachten. Sie müssen das Bild vergrößern, indem Sie die Breite auf 175 Pixel erhöhen und die Höhe auf 175 Pixel erhöhen. Traditionell müssten Sie in Adobe Photoshop gehen und all diese Warenkorbbilder neu erstellen. Mit Dynamic Media bearbeiten Sie jedoch einfach die Bildvorgabe, indem Sie die Werte für Breite und Höhe auf 175 aktualisieren und Ihre Vorgabe speichern, wie im folgenden Beispiel gezeigt.

![Bearbeiten von Bildvorgaben](/help/assets/dynamic-media/assets/dm-edit-image-preset.png)
_Bearbeiten der Breite und Höhe des `Cart` Bildvorgabe._

Nachdem Sie die Bildvorgabe geändert und den Cache geleert haben, werden alle Bilder aktualisiert und alle URLs, die mit dieser Vorgabe verwendet werden, führen Sie die Schritte aus. _not_ an einer beliebigen Stelle ändern. Das bedeutet, dass keine fehlerhaften Links und keine Umleitungen auf Webseiten erforderlich sind.

## Bildsets, Rotationssets und Sets für gemischte Medien {#dm-journey-f}

Zu den beliebtesten Einsatzbereichen von Dynamic Media gehört die Möglichkeit, Bildsets, Rotationssets und Sets für gemischte Medien zu erstellen.

Bildsets bestehen normalerweise aus einer Reihe von Bild-Assets, die als einzelne Entität dargestellt werden. Diese Arten von Sets bieten Benutzern ein integriertes Anzeigeerlebnis, bei dem Benutzer verschiedene Ansichten eines Elements sehen können, indem sie auf eine Miniaturansicht klicken. Mit Bildsets können Sie alternative Ansichten von etwas darstellen und der Viewer bietet Zoomwerkzeuge, um Bilder genau zu untersuchen. [Anzeigen eines Bildsets namens &quot;Wird ausgeführt&quot;, das den Flyout-Viewer verwendet](https://s7d1.scene7.com/s7viewers/html5/FlyoutViewer.html?asset=jpearldemo/Running).

Hier in Dynamic Media können Sie mehrere Bilder von Laufschuhen sehen. Es handelt sich um eine Produktreihenfolge, die Kunden für Vertrieb und Marketing als eine Präsentation ansehen sollen. ein Bildset.

![Erstellen eines Bildsets](/help/assets/dynamic-media/assets/dm-create-image-set.png)
_Der Beginn der Erstellung eines Bildsets._

Um das Bildset zu erstellen, wählen Sie **[!UICONTROL Bildset]** von **[!UICONTROL Erstellen]** Pulldown-Menü. Beachten Sie im Menü, dass es auch Optionen zum Erstellen einer **[!UICONTROL gemischtes Medienset]**, **[!UICONTROL Rotationsset]** und **[!UICONTROL Karussellset]**. Sie erstellen diese Sets auf ähnliche Weise wie Bildsets.

Ein Set für gemischte Medien kann Bilder, Mustersets, Rotationssets, Videos und adaptive Videosets enthalten. [Jetzt testen](https://s7d9.scene7.com/s7viewers/html5/MixedMediaViewer.html?asset=Scene7SharedAssets/Mixed_Media_Set_Sample). Ein Rotationsset simuliert den realen Vorgang, ein Objekt zu drehen, um es zu untersuchen. Rotationssets ermöglichen es, wichtige visuelle Details aus jedem Blickwinkel anzuzeigen. [Jetzt testen](https://s7d9.scene7.com/s7viewers/html5/SpinViewer.html?asset=Scene7SharedAssets/SpinSet_Sample&amp;stagesize=500,400).

Das Erstellen eines Bildsets ist unkompliziert. Fügen Sie einfach die Bild-Assets hinzu, die Sie in das Set aufnehmen möchten.

![Erstellen eines Bildsets](/help/assets/dynamic-media/assets/dm-create-image-set-add-assets.png)
_Mit dem Bildset-Editor können Sie Bild-Assets hinzufügen und ihre Darstellung im Set neu anordnen._

Sie müssen dem Set einen Namen geben. Wählen Sie den Namen sorgfältig aus, da Sie ihn nicht später bearbeiten können! Im obigen Beispiel wird der Satz `Running`. Wenn Sie fertig sind, speichern Sie das Set.

Und hier ist die `Running` Bildset in Experience Manager Assets.

![Das laufende Bildset in Experience Manager Assets, Kartenansicht](/help/assets/dynamic-media/assets/dm-image-set.png)
_Die `Running` Bildset in Experience Manager Assets, Kartenansicht._

Unabhängig davon, ob Sie ein Bildset, ein Set für gemischte Medien, ein Rotationsset oder ein anderes interaktives Medium erstellt haben, möchten Sie sehen, wie es nach dem Erstellen des Sets aussieht und sich für einen Kunden verhält. Dynamic Media verfügt über zahlreiche integrierte Viewer, mit denen Sie genau das tun können.

Wählen Sie zunächst das erstellte Bildset aus, um es wie im folgenden Beispiel in einer Vorschau zu öffnen.

![Das Bildset in der Vorschau, für das die Option &quot;Viewer&quot;ausgewählt ist](/help/assets/dynamic-media/assets/dm-image-set-viewer.png)
_Die `Running` Bildset in der Vorschau mit ausgewählter Option Viewer ._

Beachten Sie in der Vorschau, dass Sie die laufenden Schuhmuster auswählen und die Schuhe vergrößern und verkleinern können. Um einen Viewer auf das Set anzuwenden, wählen Sie **[!UICONTROL Viewer]** aus dem Pulldown-Menü.

![Das Bildset, auf das der Flyout-Viewer angewendet wurde](/help/assets/dynamic-media/assets/dm-image-set-flyout-viewer.png)
_Die `Running` Bildset mit angewendetem Flyout-Viewer._

In diesem Fall wird die `Flyout` wurde ausgewählt. An dieser Stelle können Sie eine Vorschau des Bildsets im Viewer anzeigen. Es ist jedoch am besten, es in Ihrem Browser zu sehen, wie es ein Kunde sieht. Wählen Sie **[!UICONTROL URL]** in der linken unteren Ecke, kopieren Sie die URL und fügen Sie sie in Ihren Browser ein. [Jetzt testen](https://s7d1.scene7.com/s7viewers/html5/FlyoutViewer.html?asset=jpearldemo/Running&amp;config=jpearldemo/Flyout).

Mit der einzelnen URL können Sie das Bildset und den Viewer verwenden, wo Sie sie auf Ihrer Website benötigen. Im vorherigen Beispiel haben Sie möglicherweise bemerkt, dass **[!UICONTROL Einbetten]** rechts neben der URL-Schaltfläche. Durch Auswahl **[!UICONTROL Einbetten]** können Sie den Code für diesen Bildset/Viewer kopieren und zu einer Web-Seite oder Experience Manager Sites-Komponente hinzufügen.

Der Flyout-Viewer ist ein standardmäßiger, vordefinierter Viewer, dessen Eigenschaften Sie bearbeiten können. Oder Sie können, genau wie eine Bildvorgabe erstellen, einen eigenen, benutzerdefinierten Viewer erstellen.

Angenommen, Ihr Verkaufs- und Marketingteam mag den Flyout-Viewer nicht. Sie mögen die Zoom-Funktion, möchten aber, dass Kunden den Zoom-Effekt direkt über den Schuhen sehen. In diesem Fall wenden Sie einfach den InlineZoom-Viewer auf das Bildset an und kopieren und fügen die URL in Ihren Browser ein, um zu sehen, wie es sich verhält. [Jetzt testen](https://s7d1.scene7.com/s7viewers/html5/FlyoutViewer.html?asset=jpearldemo/Running&amp;config=jpearldemo/InlineZoom).

Wenn Sie den Mauszeiger über den Schuh bewegen, zoomen Sie in das Bild ein, und Sie können mehr Details sehen, wenn Sie den Mauszeiger bewegen. Der Grund dafür ist einfach die Größe des Bildes, das ursprünglich in Dynamic Media hochgeladen wurde.

Wenn man bedenkt, wie man als Verbraucher lebt, oder wie man in seiner täglichen Rolle arbeitet, und wenn man auf verschiedene Websites geht, sieht man solche Dinge. Denken Sie darüber nach, wie dies geschieht und wie Sie die Leistungsfähigkeit von Dynamic Media in Ihrer eigenen Arbeit und auf der Website Ihres Unternehmens nutzen können.

Sie haben nur ein wenig über Bildsets und Viewer gelesen. Sehen wir uns einige andere Viewer an und probieren Sie sie für einzelne Assets aus. Um den Viewer zurückzusetzen, klicken Sie auf die **[!UICONTROL Aktualisieren]** in der linken unteren Ecke.

<!-- LEAVE THIS HIDDEN PATH IN THE DOCUMENTATION FOR DEMO PURPOSES [Flyout viewer with image set](http://www.partycity.com/girls-little-old-lady-costume-P750948.html) -->

* `ZoomVertical_dark` Viewer, der auf ein Bild-Asset angewendet wird. [Jetzt testen](https://s7d1.scene7.com/s7viewers/html5/ZoomVerticalViewer.html?asset=jpearldemo/AdobeStock_96311480&amp;config=jpearldemo/ZoomVertical_dark).
* `Zoom_light` Viewer auf ein Bild angewendet. [Jetzt testen](https://s7d1.scene7.com/s7viewers/html5/BasicZoomViewer.html?asset=jpearldemo/AdobeStock_38827423&amp;config=jpearldemo/Zoom_light).

## Optional - Weitere Informationen

Wenn Sie mehr darüber erfahren möchten, was Sie gerade lesen, nutzen Sie die unten stehenden Materialien, um Konzepte genauer zu untersuchen. Andernfalls ist Ihre Dynamic Media-Journey abgeschlossen!

_Dynamic Media-Hilfethemen_

* [Erstellen von Bildvorgaben](/help/assets/dynamic-media/image-presets.md)
* Eine Liste von [Bildverarbeitungsparameter](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html) , die Sie beim Erstellen einer Bildvorgabe im Feld Bildmodifikator verwenden können
* [Asset-Vorschau](/help/assets/dynamic-media/previewing-assets.md)
* [Vorschau von 3D-Assets anzeigen](/help/assets/dynamic-media/previewing-3d-assets.md)
* [Erstellen von Bildsets](/help/assets/dynamic-media/image-sets.md)
* [Erstellen von Rotationssets](/help/assets/dynamic-media/spin-sets.md)
* [Erstellen von Sets für gemischte Medien](/help/assets/dynamic-media/mixed-media-sets.md)

_Dynamic Media-Tutorials_

* [Verwenden von Dynamic Media mit Experience Manager Assets](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/dynamic-media-overview-feature-video-use.html)
* [Adobe Experience Manager-Inhaltsbibliothek](https://experienceleague.adobe.com/?lang=en#recommended/solutions/experience-manager) (Suchen Sie nach _Dynamic Media_)

_Dynamic Media-Viewer_

* [Live-Demos](https://landing.adobe.com/en/na/dynamic-media/ctir-2755/live-demos.html) jedes Viewers

<!-- Live as of April 28 2022. LEAVE IN HERE https://landing.adobe.com/en/na/dynamic-media/ctir-2755/index.html -->