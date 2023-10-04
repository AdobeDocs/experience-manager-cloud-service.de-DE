---
title: Video in Dynamic Media
description: Erfahren Sie, wie Sie in Dynamic Media mit Video arbeiten. Lesen Sie die Best Practices für die Codierung von Videos, die Veröffentlichung von Videos auf YouTube, das Anzeigen von Videoberichten und das Hinzufügen von Untertiteln, verdeckten Untertiteln oder Kapitelmarken zu Videos.
contentOwner: Rick Brough
feature: Video Profiles
role: User
exl-id: 0d5fbb3e-b763-415f-8c69-ea36445f882b
source-git-commit: 00cd62aa64c183a0560326feaacda1db70627858
workflow-type: tm+mt
source-wordcount: '9448'
ht-degree: 64%

---

# Video {#video}

In diesem Abschnitt wird die Arbeit mit Videos in Dynamic Media beschrieben.

## Schnellstartanleitungen: Videos {#quick-start-videos}

Die folgende schrittweise Workflow-Beschreibung soll Ihnen den schnellen Einstieg in adaptive Videosets in Dynamic Media erleichtern. Nach jedem Schritt finden Sie Querverweise auf Themenüberschriften, unter denen Sie weitere Informationen erhalten.

>[!NOTE]
>
>Stellen Sie vor der Arbeit mit Videos in Dynamic Media sicher, dass der Adobe Experience Manager-Administrator Dynamic Media Cloud Services bereits aktiviert und konfiguriert hat.
>
>* Siehe [Konfiguration von Dynamic Media Cloud Services](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services) in „Konfigurieren von Dynamic Media“ und [Fehlerbehebung in Dynamic Media](/help/assets/dynamic-media/troubleshoot-dm.md).
>

1. **Konfigurieren Sie Videos in Dynamic Media** anhand der folgenden Schritte:

   * Erstellen Sie ein eigenes Videokodierungsprofil. Alternativ Sie können einfach das vordefinierte Profil für _adaptive Videoverschlüsselung_ verwenden, das mit Dynamic Media geliefert wird.

      * [Erstellen eines Videokodierungsprofils](/help/assets/dynamic-media/video-profiles.md#creating-a-video-encoding-profile-for-adaptive-streaming).
      * Erfahren Sie mehr über die [Best Practices für Videokodierung](#best-practices-for-encoding-videos).

   * Verknüpfen Sie das Videoverarbeitungsprofil mit den Ordnern, in die Sie die Primärvideos hochladen.

      * [Anwenden eines Videoprofils auf Ordner](/help/assets/dynamic-media/video-profiles.md#applying-a-video-profile-to-folders).
      * Weitere Informationen zum [Organisieren digitaler Assets](/help/assets/organize-assets.md)

   * Laden Sie die Primärvideos in die Ordner hoch. Wenn Sie dem Ordner Videos hinzufügen, werden diese gemäß dem diesem Ordner zugewiesenen Videoverarbeitungsprofil kodiert.

      * Dynamic Media unterstützt hauptsächlich Kurzvideos mit einer maximalen Länge von 30 Minuten und einer Mindestauflösung von 25 x 25.
      * Sie können Videodateien mit bis zu 15 GB pro Datei hochladen.
      * [Videos hochladen](/help/assets/manage-video-assets.md#upload-and-preview-video-assets).
      * Weitere Informationen zu [Unterstützten Eingabedateiformaten](/help/assets/file-format-support.md).

   * [Fortschritt der Videokodierung](#monitoring-video-encoding-and-youtube-publishing-progress) in der Asset- oder Workflow-Ansicht überwachen.

1. **Verwalten Sie die Videos in Dynamic Media** anhand der folgenden Schritte:

   * Video-Assets organisieren und durchsuchen

      * [Organisieren von digitalen Assets](/help/assets/organize-assets.md)
      * [Nach Video-Assets suchen](/help/assets/search-assets.md#custompredicates) oder [Assets suchen](/help/assets/manage-digital-assets.md#search-assets)

   * Video-Assets vorab anzeigen und veröffentlichen

      * Zeigen Sie das Quellvideo und die kodierten Ausgabedarstellungen des Videos zusammen mit den zugehörigen Miniaturen an:
        [Vorschau von Videos anzeigen](/help/assets/manage-video-assets.md#upload-and-preview-video-assets) oder [Vorschau von Assets anzeigen](/help/assets/dynamic-media/previewing-assets.md)
        [Verwalten von Videoausgabedarstellungen](/help/assets/manage-digital-assets.md#managing-renditions)

      * [Verwalten von Viewer-Vorgaben](/help/assets/dynamic-media/managing-viewer-presets.md)
      * [Veröffentlichen von Assets](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md)

   * Arbeiten mit Videometadaten

      * Bearbeiten Sie die Eigenschaften von Videos, beispielsweise Titel, Beschreibung, Tags und benutzerdefinierte Metadatenfelder:
        [Bearbeiten von Videoeigenschaften](/help/assets/manage-digital-assets.md#editing-properties)

      * [Verwalten von Metadaten für digitale Assets](/help/assets/manage-metadata.md)
      * [Metadatenschemas](/help/assets/metadata-schemas.md)

   * Videos prüfen, genehmigen und mit Anmerkungen versehen und die vollständige Versionskontrolle behalten

      * [Anmerkungen zu Videos](/help/assets/manage-video-assets.md#annotate-video-assets) oder [Anmerkungen zu Assets](/help/assets/manage-digital-assets.md#annotating)

      * [Erstellen einer Version](/help/assets/manage-digital-assets.md#asset-versioning)
      * [Starten eines Workflows für ein Asset](/help/assets/manage-digital-assets.md#starting-a-workflow-on-an-asset)

      * [Prüfen von Ordner-Assets](/help/assets/bulk-approval.md)
      * [Projekte](/help/sites-cloud/authoring/projects/overview.md)

1. **Veröffentlichen Sie die Videos in Dynamic Media** anhand der folgenden Schritte:

   * Wenn Sie Experience Manager als Web-Content-Management-System (WCM) verwenden, können Sie Ihren Web-Seiten direkt Videos hinzufügen.

      * [Hinzufügen von Videos zu Ihren Web-Seiten](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md).

   * Wenn Sie das Web-Content-Management-System eines Drittanbieters verwenden, können Sie Videos mit Web-Seiten verknüpfen oder darin einbetten.

      * Integrieren von Videos mithilfe der URL:
        [Verknüpfen von URLs mit Ihrer Web-Anwendung](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md).

      * Integrieren von Videos mithilfe von Einbettungs-Code auf der Web-Seite:
        [Einbetten des Video-Viewer auf einer Web-Seite](/help/assets/dynamic-media/embed-code.md).

   * [Erzeugen von Videoberichten](#viewing-video-reports).

   * [Hinzufügen von Untertiteln zu Videos](#adding-captions-to-video).

## Arbeiten mit Video in Dynamic Media {#working-with-video-in-dynamic-media}

„Video“ in Dynamic Media ist eine durchgehende Lösung, die das Veröffentlichen von qualitativ hochwertigen adaptiven Videos für das Streaming auf mehreren Bildschirmen vereinfacht, einschließlich Desktop-PCs, Tablets und Mobilgeräten. Ein adaptives Video-Set umfasst Versionen desselben Videos, die mit unterschiedlichen Bit-Raten und Formaten codiert wurden, wie 400 kBit/s, 800 kBit/s und 1000 kBit/s. Der Desktop-Computer oder das Mobilgerät erkennt die verfügbare Bandbreite.

Auf einem iOS-Mobilgerät wird beispielsweise die Bandbreite 3G, 4G oder WLAN erkannt. Dann wird automatisch das richtig kodierte Video aus den verschiedenen Video-Bitraten im adaptiven Videoset ausgewählt. Das Video wird auf Desktops, Mobilgeräten oder Tablets gestreamt.

Außerdem wird die Videoqualität automatisch geändert, wenn sich die Netzwerkbedingungen am Desktop oder Mobilgerät ändern. Wenn eine Kundin oder ein Kunde an einem Desktop-Computer in den Vollbildmodus wechselt, verwendet das adaptive Video-Set eine höhere Auflösung und sorgt so für ein besseres Wiedergabeerlebnis. Adaptive Videosets bieten Ihnen bestmögliche Wiedergabe für Kunden, die das Dynamic Media-Video auf unterschiedlichen Bildschirmen und Geräten wiedergeben.

Die Logik, mit der Video-Player bestimmen, welches kodierte Video wiedergegeben oder während der Wiedergabe ausgewählt werden soll, basiert auf dem folgenden Algorithmus:

1. Video-Player lädt das erste Videofragment auf Basis der Bitrate, die am nächsten an dem Wert liegt, der im Player selbst als „erste Bitrate“ festgelegt wurde.
1. Video-Player wechselt auf Basis von Änderungen an der Bandbreitengeschwindigkeit anhand der folgenden Kriterien:

   1. Player wählt den höchsten Bandbreitenstrom aus, der kleiner als die geschätzte Bandbreite oder gleich dieser ist.
   1. Player berücksichtigt nur 80 % der verfügbaren Bandbreite. Beim Wechseln nach oben ist der Player mit nur 70 % konservativer, um Überschätzungen zu vermeiden und sofort zurückzuwechseln.

Detaillierte technische Informationen zum Algorithmus finden Sie unter [https://android.googlesource.com/platform/frameworks/av/+/master/media/libstagefright/httplive/LiveSession.cpp](https://android.googlesource.com/platform/frameworks/av/+/master/media/libstagefright/httplive/LiveSession.cpp)

Für das Verwalten von einzelnen Videos und adaptiven Videosets wird Folgendes unterstützt:

* Hochladen von Videos in zahlreichen unterstützten Video- und Audioformaten und Codieren von Videos in das MP4 H.264-Format für die Wiedergabe auf mehreren Bildschirmen. Sie können vordefinierte adaptive Videovorgaben oder einzelne Videokodierungsvorgaben verwenden bzw. Ihre eigene Kodierung anpassen, um die Qualität und Größe der Videos zu steuern.

   * Wenn ein adaptives Videoset generiert wird, umfasst es MP4-Videos.
   * **Hinweis**: Primär-/Quellvideos werden einem adaptiven Videoset nicht hinzugefügt.

* Videountertitelung in allen HTML5-Video-Viewern
* Organisieren und Durchsuchen von Videos mit kompletter Metadatenunterstützung für die effiziente Verwaltung von Video-Assets
* Bereitstellen von adaptiven Videosets für das Internet und Desktop-PCs, Tablets und Mobilgeräte.

Das adaptive Video-Streaming wird auf verschiedenen iOS-Plattformen unterstützt. Siehe [Dynamic Media Viewers-Referenzhandbuch](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/c-html5-video-reference.html?lang=de).

<!-- OUTDATED 2/28/22 BASED ON CQDOC-18692 Dynamic Media supports mobile video playback for MP4 H.264 video. You can find BlackBerry&reg; devices that support this video format at the following: [Supported video formats on BlackBerry&reg;](https://support.blackberry.com/kb/articleDetail?ArticleNumber=000005482).

OUTDATED 2/28/22 BASED ON CQDOC-18692 You can find Windows&reg; devices that support this video format at the following [Supported video formats on Windows&reg; Phone](https://docs.microsoft.com/en-us/windows/uwp/audio-video-camera/supported-codecs). -->

* Wiedergabe von Videos mit Video-Viewer-Vorgaben aus Dynamic Media, einschließlich der folgenden:

   * Einzelvideo-Viewer
   * Viewer für gemischte Medien, die sowohl Video- als auch Bildinhalte kombinieren

* Konfigurieren von Video-Playern entsprechend Ihren Branding-Anforderungen
* Integrieren von Videos in Websites, mobile Sites oder Mobile Apps mit einer einfachen URL oder mit Integrations-Code

Sehen Sie das Beispiel für [Dynamische Videowiedergabe](https://s7d9.scene7.com/s7/uvideo.jsp?asset=GeoRetail/Mop_AVS&amp;config=GeoRetail/Universal_Video1&amp;stageSize=640,480) an.

Weitere Informationen über [Viewer für Experience Manager Assets und Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/c-html5-s7-aem-asset-viewers.html?lang=de#viewers-aem-assets-dmc) und [Viewer nur für Experience Manager Assets](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/c-html5-aem-asset-viewers.html?lang=de#viewers-for-aem-assets-only) finden Sie im [Dynamic Media Viewers-Referenzhandbuch](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources.html?lang=de).

## Best Practice: Verwenden des HTML5-Video-Viewers {#best-practice-using-the-html-video-viewer}

Die HTML5-Video-Viewer-Vorgaben von Dynamic Media sind robuste Video-Player. Sie können sie verwenden, um viele häufige Probleme im Zusammenhang mit der HTML5-Videowiedergabe und mit Mobilgeräten verbundene Probleme zu vermeiden. Beispiele dafür sind die fehlende Bereitstellung von adaptivem Bit-Rate-Streaming und die eingeschränkte Reichweite eines Desktop-Browsers.

Mithilfe standardmäßiger Webentwicklungs-Tools können Sie die Funktionen des Video-Players entwerfen. Sie können beispielsweise die Schaltflächen, die Steuerelemente und den benutzerdefinierten Poster-Hintergrund mit HTML5 und CSS entwerfen, um Ihre Kundinnen und Kunden mit einem angepassten Erscheinungsbild anzusprechen.

Bei der Wiedergabe wird die Videofähigkeit des Browsers automatisch erkannt. Das Video wird dann per HLS oder DASH, auch als adaptives Video-Streaming bekannt, bereitgestellt. Wenn diese Bereitstellungsmethoden nicht verfügbar sind, wird stattdessen der progressive HTML5-Download verwendet.

>[!NOTE]
>
>Um DASH für Ihre Videos verwenden zu können, muss es zunächst vom technischen Support von Adobe für Ihr Konto aktiviert werden. Siehe [Aktivieren von DASH in Ihrem Konto](#enable-dash).

Sie können die Möglichkeit, die Wiedergabekomponenten mithilfe von HTML5 und CSS zu erstellen, in einen einzelnen Player integrieren. Je nach den verfügbaren Browser-Funktionen kann das Video eingebettete Wiedergabe bieten und adaptives und progressives Streaming verwenden. Dank dieser Funktion können Sie die Reichweite Ihrer Rich-Media-Inhalte sowohl auf Desktop- als auch auf Mobilgeräte ausdehnen und ein optimiertes Videoerlebnis sicherstellen.

Siehe auch [Viewer nur für Experience Manager Assets](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/c-html5-aem-asset-viewers.html?lang=de#viewers-for-aem-assets-only) im [Dynamic Media Viewers-Referenzhandbuch](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources.html?lang=de).


### Wiedergabe von Videos auf Desktops und mobilen Geräten mit dem HTML5-Video-Viewer {#playback-of-video-on-desktop-computers-and-mobile-devices-using-the-html-video-viewer}

Beim adaptiven Video-Streaming auf Desktop und Mobilgeräten basieren die für den Bit-Ratenwechsel verwendeten Videos auf allen MP4-Videos im adaptiven Videoset.

Die Videowiedergabe erfolgt entweder per HLS oder DASH oder als progressiver Video-Download. In früheren Versionen von Experience Manager, z. B. 6.0, 6.1 und 6.2, wurden Videos über HTTP gestreamt.

In Experience Manager 6.3 und neueren Versionen werden die Videos nun über HTTPS gestreamt (d. h. HLS oder DASH), da die DM-Gateway-Service-URL ebenfalls immer HTTPS verwendet. Beachten Sie, dass es bei diesem Standardverhalten keine Auswirkung auf den Kunden gibt. Video-Streaming wird immer über HTTPS ausgeführt, wenn es nicht durch den Browser unterstützt wird. Siehe folgende Tabelle.

Daher:

* Wenn Sie eine HTTPS-Website mit HTTPS-Video-Streaming haben, ist das Streaming gut.
* Wenn Sie eine HTTP-Website mit HTTPS-Video-Streaming haben, ist das Streaming gut und es gibt keine Probleme mit gemischten Inhalten im Webbrowser.

DASH ist der internationale Standard und HLS ist ein Apple-Standard. Beide werden für adaptives Video-Streaming verwendet. Außerdem passen beide Technologien die Wiedergabe automatisch an die Netzwerkbandbreite an. Darüber hinaus können Kundinnen und Kunden einen beliebigen Punkt im Video „suchen“, ohne auf den Download des restlichen Videos zu warten.

Progressives Video wird bereitgestellt, indem das Video lokal auf ein Desktop-System oder Mobilgerät einer Benutzerin bzw. eines Benutzers heruntergeladen und gespeichert wird.

Die folgende Tabelle beschreibt das Gerät, den Browser und die Wiedergabemethode für Videos auf Desktop-Computern und Mobilgeräten mit [Dynamic Media HTML5 Video Viewer](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/c-html5-aem-int-video.html?lang=de#interactive-video).

<table>
 <tbody>
  <tr>
   <td><strong>Gerät</strong></td>
   <td><strong>Browser</strong></td>
   <td><strong>Videowiedergabemodus</strong></td>
  </tr>
  <tr>
   <td>Desktop</td>
   <td>Internet Explorer 9 und 10</td>
   <td>Progressiver Download.</td>
  </tr>
  <tr>
   <td>Desktop</td>
   <td>Internet Explorer 11+</td>
   <td>Unter Windows® 8 und Windows® 10 – HTTPS wird bei Anfragen von DASH oder HLS erzwungen. Bekannte Einschränkung: HTTP kann in dieser Kombination von Browser/Betriebssystem nicht mit DASH oder HLS verwendet werden<br /> <br /> Unter Windows® 7 – progressiver Download. Verwendet Standardlogik zur Auswahl von HTTP vs. HTTPS.</td>
  </tr>
  <tr>
   <td>Desktop</td>
   <td>Firefox 23-44</td>
   <td>Progressiver Download.</td>
  </tr>
  <tr>
   <td>Desktop</td>
   <td>Firefox 45 oder höher</td>
   <td>HLS oder DASH*-Streaming mit adaptiver Bit-Rate</td>
  </tr>
  <tr>
   <td>Desktop</td>
   <td>Chrome</td>
   <td>HLS oder DASH*-Streaming mit adaptiver Bit-Rate</td>
  </tr>
  <tr>
   <td>Desktop</td>
   <td>Safari (Mac)</td>
   <td>HLS adaptives Bit-Rate-Streaming</td>
  </tr>
  <tr>
   <td>Mobilgerät</td>
   <td>Chrome (Android™ 6 oder früher)</td>
   <td>Progressiver Download.</td>
  </tr>
  <tr>
   <td>Mobilgerät</td>
   <td>Chrome (Android 7™ oder neuer)</td>
   <td>HLS oder DASH*-Streaming mit adaptiver Bit-Rate/td&gt;
  </tr>
  <tr>
   <td>Mobilgerät</td>
   <td>Android™ (Standard-Browser)</td>
   <td>Progressiver Download.</td>
  </tr>
  <tr>
   <td>Mobilgerät</td>
   <td>Safari (iOS)</td>
   <td>HLS adaptives Bit-Rate-Streaming</td>
  </tr>
  <tr>
   <td>Mobilgerät</td>
   <td>Chrome (iOS)</td>
   <td>HLS adaptives Bit-Rate-Streaming</td>
  </tr>
 </tbody>
</table>

>[!IMPORTANT]
>
>*Um DASH für Ihre Videos zu verwenden, muss es zunächst vom technischen Support von Adobe für Ihr Konto aktiviert werden. Siehe [Aktivieren von DASH in Ihrem Konto](#enable-dash).)

<!--  THIS LINE WAS REMOVED FROM THE TABLE ABOVE ON FEB 28, 2022 BASED ON CQDOC 18692 -RSB <tr>
   <td>Mobile</td>
   <td>BlackBerry&reg;</td>
   <td>HLS or DASH</td>
  </tr>
 -->

## Architektur der Dynamic Media-Videolösung {#architecture-of-dynamic-media-video-solution}

Die folgende Grafik zeigt den allgemeinen Bearbeitungs-Workflow für Videos, die über DMGateway (im Hybridmodus von Dynamic Media) hochgeladen und kodiert sowie für die öffentliche Anzeige verfügbar gemacht werden.

![chlimage_1-427](assets/chlimage_1-427.png)

## Hybride Veröffentlichungsarchitektur für Videos {#hybrid-publishing-architecture-for-videos}

![chlimage_1-428](assets/chlimage_1-428.png)

## Best Practices für die Kodierung von Videos {#best-practices-for-encoding-videos}

Der Workflow für **Dynamic Media-Videokodierung** kodiert Videos, wenn Dynamic Media aktiviert und Video-Cloud-Services eingerichtet sind. Dieser Workflow erfasst den Verlauf der Workflow-Prozesse und Informationen zu Fehlern. Wenn Sie Dynamic Media aktiviert und Video-Cloud Services eingerichtet haben, wird der Workflow für die **[!UICONTROL Videokodierung mit Dynamic Media]** automatisch beim Hochladen eines Videos wirksam. (Wenn Sie Dynamic Media nicht verwenden, wird der Workflow **[!UICONTROL DAM Update Asset]** wirksam.)

Beachten Sie die folgenden Best Practice-Tipps für die Kodierung von Quellvideodateien.

<!-- For advice about video encoding, see the following:

* [Streaming 101: The Basics — Codecs, Bandwidth, Data Rate, and Resolution](https://www.adobe.com/go/learn_s7_streaming101_en).
* [Video Encoding Basics](https://www.adobe.com/go/learn_s7_encoding_en). -->

### Quellvideodateien {#source-video-files}

Verwenden Sie zum Kodieren einer Videodatei eine Quellvideodatei mit der höchstmöglichen Qualität. Verwenden Sie keine zuvor kodierten Videodateien, da diese Dateien bereits komprimiert wurden und die weitere Kodierung zu mangelhafter Videoqualität führen würde.

* Dynamic Media unterstützt hauptsächlich Kurzvideos mit einer maximalen Länge von 30 Minuten und einer Mindestauflösung von 25 x 25.
* Sie können Videodateien mit einer Größe von bis zu 15 GB als Primärquelle hochladen.

Die folgende Tabelle beschreibt die empfohlenen Werte für Größe, Seitenverhältnis und Mindest-Bitrate, die Quellvideos vor der Kodierung aufweisen sollten:

| Größe | Seitenverhältnis | Mindest-Bitrate |
|--- |--- |--- |
| 1.024 X 768 | 4:3 | 4500 kBit/s für die meisten Videos |
| 1.280 X 720 | 16:9 | 3000–6000 kBit/s, je nachdem, wie viel Bewegung im Video vorkommt |
| 1920 X 1080 | 16:9 | 6000–8000 kBit/s, je nachdem, wie viel Bewegung im Video vorkommt |

### Abrufen der Metadaten von Dateien {#obtaining-a-file-s-metadata}

Sie können die Metadaten einer Datei abrufen, indem Sie diese mit einem Bearbeitungs-Tool für Videos anzeigen oder eine Anwendung verwenden, die zum Abrufen von Metadaten entwickelt wurde. Im Folgenden wird die Nutzung von MediaInfo, einem Drittanbieterprogramm, zum Abrufen der Metadaten einer Videodatei beschrieben:

1. Gehen Sie zu [MediaInfo Download](https://mediaarea.net/de/MediaInfo/Download).
1. Wählen Sie das Installationsprogramm für die GUI-Version aus, laden Sie es herunter und befolgen Sie die Installationsanweisungen.
1. Klicken Sie nach der Installation mit der rechten Maustaste auf die Videodatei (nur Windows®) und wählen Sie MediaInfo oder öffnen Sie MediaInfo und ziehen Sie die gewünschte Videodatei in die Anwendung. Alle mit der Videodatei verknüpften Metadaten werden angezeigt, einschließlich Breite, Höhe und fps.

### Seitenverhältnis {#aspect-ratio}

Wenn Sie eine Videokodierungsvorgabe für die Primär-Videodatei auswählen oder erstellen, achten Sie darauf, dass die Vorgabe dasselbe Seitenverhältnis wie die Primär-Videodatei aufweist. Das Seitenverhältnis ist das Verhältnis zwischen Breite und Höhe des Videos.

Um das Seitenverhältnis einer Videodatei zu ermitteln, rufen Sie die Metadaten der Datei ab und notieren Sie die Breite und Höhe der Datei (siehe Abrufen der Metadaten einer Datei oben). Verwenden Sie dann diese Formel, um das Seitenverhältnis zu ermitteln:

Breite/Höhe = Seitenverhältnis

Anhand der folgenden Tabelle können Sie die Formelergebnisse in gängige Seitenverhältnisoptionen umwandeln:

| Formelergebnis | Seitenverhältnis |
|--- |--- |
| 1,33 | 4:3 |
| 0,75 | 3:4 |
| 1,78 | 16:9 |
| 0,56 | 9:16 |

Beispiel: Ein Video mit einer Breite von 1440 und einer Höhe von 1080 hat ein Seitenverhältnis von 1440:1080 bzw. 1,33. In diesem Fall wählen Sie eine Videokodierungsvorgabe mit einem Seitenverhältnis von 4:3 aus, um die Videodatei zu kodieren.

### Bitrate {#bitrate}

Die Bitrate ist die kodierte Menge an Daten für eine Videowiedergabe von einer einzigen Sekunde Dauer. Die Bitrate wird in Kilobit pro Sekunde (kBit/s) gemessen.

>[!NOTE]
>
>Da alle Codecs verlustreiche Komprimierung verwenden, ist die Bitrate der wichtigste Faktor für die Videoqualität. Bei verlustreicher Komprimierung wird die Datenqualität schlechter, je mehr Sie eine Videodatei komprimieren. Wenn alle anderen Merkmale wie Auflösung, Framerate und Codec gleich sind, gilt daher, dass eine niedrigere Bitrate zu einer niedrigeren Qualität der komprimierten Datei führt.

Sie können zwischen zwei Arten der Bitraten-Kodierung wählen:

* **[!UICONTROL Konstante Bitraten-Kodierung]** (CBR): Während der CBR-Kodierung bleibt die Bitrate oder Anzahl der Bits pro Sekunde während des Kodierungsvorgangs gleich. Die CBR-Kodierung speichert die festgelegte Datenrate für das gesamte Video in Ihrer Einstellung. Die CBR-Kodierung optimiert nicht die Qualität von Mediendateien, spart jedoch Speicherplatz.
Verwenden Sie CBR, wenn Ihr Video im gesamten Video ein ähnliches Bewegungsniveau enthält. CBR wird hauptsächlich zum Streaming von Videoinhalten verwendet. Siehe auch [Verwenden von benutzerdefinierten Videokodierungsparametern](/help/assets/dynamic-media/video-profiles.md#using-custom-added-video-encoding-parameters).

* **[!UICONTROL Variable Bit-Raten-Codierung]** (VBR): Bei der VBR-Codierung wird die Datenrate auf der Grundlage der vom Kompressor benötigten Daten nach unten und an die von Ihnen festgelegte Obergrenze angepasst. Diese Funktionalität bedeutet, dass die Bitrate der Mediendatei während eines VBR-Kodierungsprozesses je nach der benötigten Bitrate der Mediendateien dynamisch erhöht oder reduziert wird.
VBR benötigt mehr Zeit für die Kodierung, liefert jedoch die besten Ergebnisse. Die Qualität der Mediendatei ist besonders gut. VBR wird meist für die progressive HTTP-Übermittlung von Videoinhalten verwendet.

Verwendung von VBR vs. CRB
Wenn es um die Auswahl von VBR oder CBR geht, wird für Ihre Mediendateien meist VBR empfohlen. VBR bietet Dateien mit besserer Qualität bei wettbewerbsfähigen Bitraten. Verwenden Sie bei VBR auf jeden Fall eine Kodierung mit zwei Durchgängen und stellen Sie die maximale Bitrate so ein, dass sie 1,5-mal größer ist als die Ziel-Video-Bitrate.

Berücksichtigen Sie bei Auswahl einer Videocodierungsvorgabe unbedingt die Verbindungsgeschwindigkeit des Zielgruppen-Endbenutzers. Wählen Sie eine Vorgabe mit einer Datenrate, die 80 % dieser Geschwindigkeit beträgt. Beispiel: Wenn die Verbindungsgeschwindigkeit der Zielperson 1000 kBit/s beträgt, hat die optimale Vorgabe eine Videodatenrate von 800 kBit/s.

Diese Tabelle enthält die Datenraten von typischen Verbindungsgeschwindigkeiten.

| Geschwindigkeit (kBit/s) | Verbindungstyp |
|--- |--- |
| 256 | Einwahlverbindung |
| 800 | Typische Mobilverbindung Für diese Verbindung eignet sich eine Datenrate von 400 bis maximal 800 für 3G-Verbindungen. |
| 2.000 | Typische Breitband-Desktop-Verbindung. Für diese Verbindung eignet sich eine Datenrate zwischen 800 und 2.000 kBit/s, wobei die meisten Ziele im Durchschnitt zwischen 1.200 und 1.500 kBit/s aufweisen. |
| 5.000 | Typische Hochbreitband-Desktopverbindung Die Kodierung in diesem oberen Bereich wird nicht empfohlen, da die Videobereitstellung in dieser Geschwindigkeit für die meisten Benutzer nicht verfügbar ist. |

### Auflösung {#resolution}

Die **Auflösung** bezeichnet die Höhe und Breite einer Videodatei in Pixel. Die meisten Quellvideos werden mit hoher Auflösung gespeichert (z. B. 1920 x 1080). Zu Streaming-Zwecken werden Quellvideos in eine niedrigere Auflösung komprimiert (640 x 480 oder weniger).

Auflösung und Datenrate stellen zwei eng miteinander verknüpfte Faktoren der Videoqualität dar. Um dieselbe Videoqualität beizubehalten gilt: Je höher die Anzahl Pixel in einer Videodatei (also je höher die Auflösung), desto höher muss auch die Datenrate sein. Betrachten Sie z. B. die Anzahl Pixel pro Frame in einer Videodatei mit der Auflösung 320 x 240 und einer Datei mit der Auflösung 640 x 480:

| Auflösung | Pixel pro Frame |
|--- |--- |
| 320 x 240 | 76.800 |
| 640 x 480 | 307.200 |

Die Datei mit 640 x 480 enthält viermal so viele Pixel pro Frame. Um dieselbe Datenrate für diese beiden Auflösungen zu erreichen, wenden Sie eine vierfache Komprimierung auf die Datei mit 640 x 480 an, was zu einer schlechteren Videoqualität führen kann. Daher führt eine Videodatenrate von 250 kBit/s zu einer hohen Anzeigequalität bei einer Auflösung von 320 x 240, aber nicht bei einer Auflösung von 640 x 480.

Im Allgemeinen gilt: Je höher die verwendete Datenrate, desto besser sieht das Video aus, und je höher die verwendete Auflösung, desto höher ist die benötigte Datenrate, um die Anzeigequalität aufrechtzuerhalten (im Vergleich zu niedrigeren Auflösungen).

Da Auflösung und Datenrate miteinander verknüpft sind, haben Sie beim Kodieren von Videos zwei Optionen:

* Wählen Sie eine Datenrate und kodieren Sie dann mit der höchsten Auflösung, die mit der gewählten Datenrate eine gute Qualität erzeugt.
* Wählen Sie eine Auflösung und kodieren Sie dann mit der erforderlichen Datenrate, um hohe Videoqualität mit der gewählten Auflösung zu erreichen.

Orientieren Sie sich beim Auswählen (oder Erstellen) einer Videokodierungsvorgabe für die Primär-Videodatei an der folgenden Tabelle, um die richtige Auflösung auszuwählen.

| Auflösung | Höhe (Pixel) | Bildschirmgröße |
|--- |--- |--- |
| 240p | 240 | Winziger Bildschirm |
| 300p | 300 | Kleiner Bildschirm, wie er bei Mobilgeräten typisch ist |
| 360p | 360 | Kleiner Bildschirm |
| 480p | 480 | Mittlerer Bildschirm |
| 720p | 720 | Großer Bildschirm |
| 1.080p | 1.080 | Großer Bildschirm mit High-Definition |

### Fps (Frames pro Sekunde) {#fps-frames-per-second}

In den USA und Japan werden die meisten Videos mit 29,97 Frames pro Sekunde (fps) aufgenommen, in Europa mit 25 fps. Filme werden mit 24 fps aufgenommen.

Wählen Sie eine Videokodierungsvorgabe aus, die der fps-Rate der jeweiligen Primär-Videodatei entspricht. Wenn das Primärvideo beispielsweise 25 fps aufweist, wählen Sie eine Kodierungsvorgabe mit 25 fps. Standardmäßig wird bei jeder benutzerdefinierten Codierung der fps-Wert der Primär-Videodatei verwendet. Daher müssen Sie die fps-Einstellung nicht explizit angeben, wenn Sie eine Videokodierungsvorgabe erstellen.

### Abmessungen bei der Videokodierung {#video-encoding-dimensions}

Wählen Sie für optimale Ergebnisse Kodierungsabmessungen so aus, dass das Quellvideo ein ganzes Mehrfaches aller kodierten Videos ist.

Um dieses Verhältnis zu berechnen, teilen Sie die Quellbreite durch die kodierte Breite, um das Breitenverhältnis zu ermitteln. Dann teilen Sie die Quellhöhe durch die kodierte Höhe, um das Höhenverhältnis zu ermitteln.

Wenn das resultierende Verhältnis eine Ganzzahl ist, hat das Video die optimale Skalierung. Wenn das errechnete Verhältnis keine Ganzzahl ist, wird die Videoqualität beeinträchtigt, da übrig gebliebene Pixelartefakte auf der Anzeige verbleiben. Dieser Effekt ist am auffälligsten, wenn das Video Text enthält.

Im folgenden Beispiel hat das Quellvideo Abmessungen von 1920 x 1080. Die drei kodierten Videos in der folgenden Tabelle geben die optimalen Kodierungseinstellungen an.

| Videotyp | Breite x Höhe | Breitenverhältnis | Höhenverhältnis |
|--- |--- |--- |--- |
| Quelle | 1920 x 1080 | 1 | 1 |
| Kodiert | 960 x 540 | 2 | 2 |
| Kodiert | 640 x 360 | 3 | 3 |
| Kodiert | 480 x 270 | 4 | 4 |

### Kodiertes Videodateiformat {#encoded-video-file-format}

In Dynamic Media wird empfohlen, MP4 H.264-Videokodierungsvorgaben zu verwenden. Da MP4-Dateien den H.264-Video-Codec nutzen, erhalten Sie damit hohe Videoqualität, aber auch eine komprimierte Dateigröße.

## Anzeigen von Videoberichten {#viewing-video-reports}

>[!NOTE]
>
>Videoberichte sind nur verfügbar, wenn Sie Dynamic Media im Hybridmodus ausführen.

Videoberichte enthalten mehrere aggregierte Metriken für einen angegebenen Zeitaum, anhand derer Sie überwachen können, ob *veröffentlichte* individuelle und aggregierte Videos die erwartete Leistung zeigen. Die folgenden Top-Metrikdaten werden für alle veröffentlichten Videos auf der gesamten Website aggregiert:

* Videostarts
* Abschlussrate
* Durchschnittliche Zeit im Video
* Gesamtzeit im Video
* Videos pro Besuch

Eine Tabelle mit allen *veröffentlichten* Videos wird ebenfalls angezeigt, damit Sie die am häufigsten angezeigten Videos auf der Website basierend auf insgesamt gestarteten Videos verfolgen können.

Wenn Sie in der Liste einen Videonamen auswählen, wird der Bericht zur Zielgruppentreue (Abfallrate) in Form eines Liniendiagramms angezeigt. Das Diagramm enthält die Anzahl der Ansichten für jeden einzelnen Moment während der Videowiedergabe. Wenn Sie das Video wiedergeben, bewegt sich die vertikale Leiste synchron mit der Zeitanzeige im Player. Abfälle in den Liniendiagrammdaten geben an, wo die Zielgruppe das Video aus Desinteresse abbricht.

Wenn das Video außerhalb von Adobe Experience Manager für Dynamic Media kodiert wurde, sind das Diagramm zur Zielgruppentreue (Abbruch) und die Daten zur Wiedergabe in Prozent in der Tabelle nicht verfügbar.

>[!NOTE]
>
>Nachverfolgungs- und Berichtsdaten basierend ausschließlich auf der Nutzung des Video-Players von Dynamic Media und den zugehörigen Video-Player-Vorgaben. Daher können Sie keine Videos nachverfolgen und in Berichte aufnehmen, die mit anderen Video-Playern wiedergegeben werden.

Wenn Sie die Funktion „Videoberichte“ zum ersten Mal aufrufen, enthält der Bericht standardmäßig Videodaten für den Zeitraum vom ersten Tag des aktuellen Monats bis zum aktuellen Datum. Sie können den standardmäßigen Datumsbereich aber außer Kraft setzen, indem Sie Ihren eigenen Datumsbereich angeben. Wenn Sie „Videoberichte“ das nächste Mal aufrufen, wird der angegebene Datumsbereich verwendet.

Damit Videoberichte ordnungsgemäß funktionieren, wird automatisch eine Report Suite-ID erstellt, wenn Dynamic Media Cloud Services konfiguriert wurde. Gleichzeitig wird die Report Suite-ID an den Veröffentlichungs-Server übergeben, damit sie für die Funktion „URL kopieren“ bei der Asset-Vorschau verfügbar ist. Dafür muss der Veröffentlichungs-Server aber bereits eingerichtet sein. Wenn der Veröffentlichungs-Server nicht eingerichtet ist, können Sie dennoch veröffentlichen, um den Videobericht anzuzeigen. Sie müssen jedoch zur Konfiguration von Dynamic Media Cloud zurückkehren und auf **[!UICONTROL OK]** klicken.

**So zeigen Sie Videoberichte an:**

1. Klicken Sie in der linken oberen Ecke von Experience Manager auf das Experience Manager-Logo und gehen Sie dann in der linken Leiste zu **[!UICONTROL Tools]** (Hammersymbol) > **[!UICONTROL Assets]** > **[!UICONTROL Videoberichte]**.
1. Führen Sie auf der Seite „Videoberichte“ eine der folgenden Aktionen aus:

   * Klicken Sie in der Nähe der oberen rechten Ecke auf das Symbol **[!UICONTROL Videobericht aktualisieren]**.
Sie müssen nur dann aktualisieren, wenn das Enddatum des Berichts der aktuelle Tag ist. Dadurch wird sichergestellt, dass Sie das Video-Tracking sehen, das seit der letzten Ausführung des Berichts vorgenommen wurde.

   * Klicken Sie in der Nähe der oberen rechten Ecke auf das Symbol **[!UICONTROL Datumsauswahl]**.
Geben Sie den Anfang und das Ende des Datumsbereichs an, für den Sie Videodaten anzeigen möchten, und klicken Sie dann auf **[!UICONTROL Bericht ausführen]**.

   Im Gruppenfeld „Top-Metriken“ werden verschiedene aggregierte Messungen für alle *veröffentlichten* Videos auf der Site angegeben.

1. Wählen Sie in der Tabelle mit den am häufigsten veröffentlichten Videos einen Videonamen aus, um das Video abzuspielen und den Bericht zur Zielgruppentreue (Abfallrate) des Videos anzuzeigen.

<!-- OBSOLETE CONTENT OBSOLETE CONTENT - SDK ONLY AVAILABLE INTERNALLY NOW 
### Viewing video reports based on a video viewer that you created using the Dynamic Media HTML5 Viewer SDK {#viewing-video-reports-based-on-a-video-viewer-that-you-created-using-the-scene-hmtl-viewer-sdk}

If you are using an out-of-box video viewer provided by Dynamic Media, or if you created a custom viewer preset based off of an out-of-box video viewer, then no additional steps are required to view video reports. However, if you have created your own video viewer based off the Dynamic Media HTML5 Viewer SDK, then use the following steps to ensure the your video viewer is sending tracking events to Dynamic Media Video Reports.

Use the Dynamic Media Viewers Reference and the Dynamic Media HTML5 Viewers SDK to create your own video viewers.

See [Dynamic Media Viewers Reference Guide](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/home.html).

Download the Scene7 HTML Viewer SDK from Adobe Developer Connection.

See [Adobe Developer Connection](https://help.adobe.com/en_US/scene7/using/WSef8d5860223939e2-43dedf7012b792fc1d5-8000.html).

**To view Video Reports based on a video viewer that you created using the Dynamic Media HTML5 Viewer SDK:**

1. Navigate to any published video asset.
1. Near the upper-left corner of the asset's page, from the drop-down list, select **[!UICONTROL Viewers]**.
1. Select any video viewer preset and copy the embed code.
1. In the embed code, find the line with the following:

   `videoViewer.setParam("config2", "<value>");`

   The `config2` parameter enables tracking in HTML5 Viewers. It is also a company-specific preset that contains the configuration information for Video Reporting, and for customer-specific Adobe Analytics configurations.

   The correct value for the config2 parameter is found in both the **[!UICONTROL Embed Code]** and in the copy **[!UICONTROL URL]** function. In the URL from the copy **[!UICONTROL URL]** command, the parameter to look for is `&config2=<value>` . The value is almost always `companypreset`, but in some instances it can also be `companypreset-1`, `companypreset-2`, and so forth.

1. In your custom video viewer code, add AppMeasurementBridge .jsp to the viewer page by doing the following:

    * First, determine if you need the `&preset` parameter.
      If the `config2` parameter is `companypreset`, you do *not *need `&preset=parameter`.
      If `config2` is anything else, set the preset parameter the same as the `config2` parameter. For example, if `config2=companypreset-2`, add `&param2=companypreset-2` to the AppMeasurmentBridge.jsp URL.

    * Then, add the AppMeasurementBridge.jsp script:
      `<script language="javascript" type="text/javascript" src="https://s7d1.scene7.com/s7viewers/AppMeasurementBridge.jsp?company=robindallas&preset=companypreset-2"></script>`

1. Create the TrackingManager component by doing the following:

    * After calling `s7sdk.Utils.init();` create a TrackingManager instance to track events by adding the following:
      `var trackingManager = new s7sdk.TrackingManager();`

    * Connect components to TrackingManager by doing the following:
      In the `s7sdk.Event.SDK_READY` event handler, attach the component you want to track to the TrackingManager.
      For example, if the component is `videoPlayer`, add
      `trackingManager.attach(videoPlayer);`
      to attach the component to the trackingManager. To track multiple viewers on a page, use multiple tracking mangaer components.

    * Create the AppMeasurementBridge object by adding the following:

      ```
      var appMeasurementBridge = new AppMeasurementBridge(); appMeasurementBridge.setVideoPlayer(videoPlayer);
      ```

    * Add the tracking function by adding the following:

      ```
      trackingManager.setCallback(appMeasurementBridge.track,
       appMeasurementBridge);
      ```

   The appMeasurementBridge object has a built-in track function. OBSOLETE However, you can provide your own to support multiple tracking systems or other functionality.

   For more information, see *Using the TrackingManager Component* in the *Scene7 HTML5 Viewer SDK User Guide* available for download from [Adobe Developer Connection](https://help.adobe.com/en_US/scene7/using/WSef8d5860223939e2-43dedf7012b792fc1d5-8000.html).
 -->





### DASH-, Multi-Subtitle- und Multi-Audio-Track-Unterstützung für Ihr Dynamic Media-Konto aktivieren {#enable-dash}

**Informationen zum Aktivieren der DASH-Unterstützung für Ihr Konto**
DASH (Digital Adaptive Streaming über HTTP) ist der internationale Standard für Video-Streaming und wird in verschiedenen Video-Viewern auf breiter Front verwendet. Wenn DASH in Ihrem Konto aktiviert ist, können Sie entweder DASH oder HLS für adaptives Video-Streaming auswählen. Sie können auch beide Optionen beim automatischen Wechseln zwischen Playern wählen, wenn **[!UICONTROL auto]** als Wiedergabetyp in der Viewer-Vorgabe ausgewählt ist.

Zu den wichtigsten Vorteilen der Aktivierung von DASH in Ihrem Konto zählen die folgenden:

* Verpacken der DASH-Stream-Videos für das Streaming mit adaptiver Bit-Rate. Diese Methode führt zu einer höheren Effizienz der Bereitstellung. Adaptives Streaming gewährleistet das beste Zuschauererlebnis für Ihre Kundinnen und Kunden.
* Browser-optimiertes Streaming mit Dynamic Media-Playern wechselt zwischen HLS und DASH-Streaming, um eine optimale Service-Qualität zu gewährleisten. Der Videoplayer wechselt automatisch zu HLS, wenn ein Safari-Browser verwendet wird.
* Sie können Ihre bevorzugte Streaming-Methode (HLS oder DASH) konfigurieren, indem Sie die Video-Viewer-Vorgabe bearbeiten.
* Optimierte Videocodierung stellt sicher, dass während der Aktivierung der DASH-Funktion kein zusätzlicher Speicher verwendet wird. Für HLS und DASH wird ein einziger Satz von Videocodierungen erstellt, um die Kosten für die Videospeicherung zu optimieren.
* Hilft Ihnen, die Bereitstellung von Videos für Ihre Kundinnen und Kunden leichter zugänglich zu machen.
* Rufen Sie die Streaming-URL auch über APIs ab.

Die Aktivierung der DASH-Unterstützung für Ihr Konto erfolgt über einen Adobe-Support-Vorgang, den Sie erstellen und senden.

**Über die Aktivierung der Unterstützung für Multiuntertitel und Multiaudio-Track in Ihrem Konto**

Gleichzeitig erstellen Sie ein Adobe-Support-Szenario, bei dem DASH für Ihr Konto aktiviert wird. Außerdem profitieren Sie auch von der automatischen Aktivierung der Unterstützung für mehrere Untertitel und Multiaudio-Track. Nach der Aktivierung werden alle nachfolgenden Videos, die Sie hochladen, mit einer neuen Backend-Architektur verarbeitet, die Unterstützung für das Hinzufügen von Multiuntertiteln und Multiaudio-Tracks zu Ihren Videos enthält.

>[!IMPORTANT]
>
>Alle hochgeladenen Videos *before* Aktivierung der Unterstützung für mehrere Untertitel und Multiaudio-Track in Ihrem Dynamic Media-Konto, [muss erneut verarbeitet werden](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets). Dieser Schritt zur erneuten Verarbeitung des Videos ist erforderlich, damit mehrere Untertitel und Multiaudio-Track verfügbar sind. Die Video-URLs funktionieren nach der erneuten Verarbeitung weiterhin und werden wie gewohnt wiedergegeben.

**So aktivieren Sie die Unterstützung von DASH-, Multi-Subtitle- und Multi-Audio-Track für Ihr Dynamic Media-Konto:**

1. [Verwenden Sie Admin Console, um mit der Erstellung eines neuen Support-Falls zu beginnen](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html).
1. Um einen Support-Fall zu erstellen, befolgen Sie die Anweisungen und stellen Sie dabei sicher, dass Sie die folgenden Informationen bereitstellen:

   * Name des Hauptansprechpartners, E-Mail, Telefon.
   * Ihre Programm-ID und Umgebungs-ID.
   * Name Ihres Dynamic Media-Kontos.
   * Geben Sie an, dass in Ihrem Dynamic Media-Konto in Experience Manager 6.5 DASH-, Multi-Subtitle- und Multi-Audio-Track-Unterstützung aktiviert werden soll.

1. Der Adobe-Kundensupport fügt Sie basierend auf der Reihenfolge, in der Anfragen gesendet werden, zur Kundenwarteschlange hinzu.
1. Wenn Adobe bereit ist, Ihre Anfrage zu bearbeiten, kontaktiert der Kundensupport Sie, um ein Zieldatum für die Aktivierung zu koordinieren und festzulegen.
1. Nach Abschluss werden Sie durch den Support benachrichtigt.
1. Jetzt können Sie eine der folgenden Aktionen ausführen:

   * Erstellen Sie Ihre [Video-Viewer-Vorgabe](/help/assets/dynamic-media/managing-viewer-presets.md#creating-a-new-viewer-preset) wie gewohnt.
   * [Mehrere Untertitel und Multiaudio-Tracks hinzufügen](#add-msma) zu Ihrem Video.


## Über die Unterstützung von Multiuntertiteln und Multiaudio-Track für Videos in Dynamic Media{#about-msma}

Mit der Funktion für mehrere Untertitel und mehrere Audiospuren in Dynamic Media können Sie einem Hauptvideo mühelos mehrere Untertitel und Audiospuren hinzufügen. Diese Funktion bedeutet, dass Ihre Videos für eine globale Zielgruppe zugänglich sind. Sie können ein einzelnes veröffentlichtes primäres Video für eine globale Zielgruppe in mehreren Sprachen anpassen und die Richtlinien zur Barrierefreiheit für verschiedene geografische Regionen einhalten. Autorinnen und Autoren können die Untertitel und Audiospuren auch über eine einzige Registerkarte in der Benutzeroberfläche verwalten.

![Registerkarte &quot;Untertitel und Audiospuren&quot;in Dynamic Media zusammen mit einer Tabelle mit hochgeladenen .VTT-Untertiteldateien und hochgeladenen .MP3-Audiospur-Dateien für ein Video.](/help/assets/dynamic-media/assets/msma-subtitle-audiotracks-tab.png)

Zu den Nutzungsszenarios für das Hinzufügen von Multiuntertiteln und Multi-Audio-Tracks zu Ihrem primären Video zählen unter anderem die folgenden:

| Typ | Nutzungsszenario |
|--- |--- |
| **Untertitel** | Unterstützung mehrerer Sprachen |
|  | Beschreibender Text für Barrierefreiheit |
| **Audiospuren** | Unterstützung mehrerer Sprachen |
|  | Kommentarspuren |
|  | Beschreibendes Audio |

Alle [Unterstützte Videoformate in Dynamic Media](/help/assets/file-format-support.md) und alle Dynamic Media-Video-Viewer mit Ausnahme der Dynamic Media *Video_360* Viewer: werden für die Verwendung mit mehreren Untertiteln und mehreren Audiospuren unterstützt.

Die Funktion für mehrere Untertitel und mehrere Audiospuren ist für Ihr Dynamic Media-Konto über einen Funktionsumschalter verfügbar, der vom Adobe-Support aktiviert werden muss.

### Hinzufügen von Multiuntertiteln und Multiaudio-Tracks zu Ihrem Video {#add-msma}

Bevor Sie Ihrem Video mehrere Untertitel- und Multiaudio-Tracks hinzufügen, stellen Sie sicher, dass Sie bereits die folgenden integrierten Funktionen haben:

* Dynamic Media ist in einer AEM-Umgebung eingerichtet.
* A [Das Dynamic Media-Videoprofil wird auf den Ordner angewendet, in dem Ihre Videos aufgenommen werden](/help/assets/dynamic-media/video-profiles.md#applying-a-video-profile-to-folders).
* [Multi-Untertitel und Multi-Audio-Track sind in Ihrem Dynamic Media-Konto aktiviert.](#enable-dash).

Hinzugefügte Untertitel und Beschriftungen werden in den Formaten WebVTT und Adobe VTT unterstützt. Hinzugefügte Audio-Track-Dateien werden mit dem MP3-Format unterstützt.

>[!IMPORTANT]
>
>Alle hochgeladenen Videos *before* Aktivierung der Unterstützung für mehrere Untertitel und Multiaudio-Track in Ihrem Dynamic Media-Konto, [muss erneut verarbeitet werden](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets). Dieser Schritt zur erneuten Verarbeitung des Videos ist erforderlich, damit mehrere Untertitel und Multiaudio-Track verfügbar sind. Die Video-URLs funktionieren nach der erneuten Verarbeitung weiterhin und werden wie gewohnt wiedergegeben.

**So fügen Sie Ihrem Video mehrere Untertitel und Multiaudio-Tracks hinzu:**

1. [Hochladen des Primärvideos in einen Ordner](/help/assets/manage-video-assets.md#upload-and-preview-video-assets) , dem bereits ein Videoprofil zugewiesen ist.
1. Navigieren Sie zum hochgeladenen Video-Asset, dem Sie mehrere Untertitel und Audiospuren hinzufügen möchten.
1. Wählen Sie im Asset-Auswahlmodus entweder in der Listenansicht oder in der Kartenansicht das Video-Asset aus.
1. Wählen Sie in der Symbolleiste das Symbol Eigenschaften aus (ein Kreis mit einem darin enthaltenen &quot;i&quot;).
   ![Ausgewähltes Video-Asset mit Häkchen über dem Videominiaturbild und Eigenschaften anzeigen in der Symbolleiste hervorgehoben.](/help/assets/dynamic-media/assets/msma-selectedasset-propertiesbutton.png)*Ausgewähltes Video-Asset in der Kartenansicht.*
1. Wählen Sie auf der Seite Eigenschaften des Videos die **[!UICONTROL Untertitel und Audio-Tracks]** Registerkarte.

   >[!TIP]
   >Wenn die Variable **[!UICONTROL Untertitel und Audio-Tracks]** -Tab, bedeutet dies eine von zwei Dingen:
   >
   >* Dem Ordner, in dem sich das ausgewählte Video befindet, wird kein Videoprofil zugewiesen. In diesem Fall siehe [Anwenden eines Videoprofils auf den Ordner](/help/assets/dynamic-media/video-profiles.md#applying-video-profiles-to-specific-folders)
   >* Oder das Video muss von Dynamic Media erneut verarbeitet werden. In diesem Fall siehe [Dynamic Media-Assets in einem Ordner erneut verarbeiten](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets).
   >
   >Wenn Sie eine der oben genannten Aufgaben ausgeführt haben, kehren Sie zu diesen Schritten zurück.

   ![Registerkarte &quot;Untertitel und Audiospuren&quot;auf der Seite &quot;Eigenschaften&quot;.](/help/assets/dynamic-media/assets/msma-audiotracks.png)*Registerkarte &quot;Untertitel und Audiospuren&quot;auf der Seite &quot;Eigenschaften&quot;des Videos.*

1. (Optional) Gehen Sie wie folgt vor, um einem Video eine oder mehrere Untertiteldateien (oder Untertiteldateien) hinzuzufügen:
   * Auswählen **[!UICONTROL Hochladen von Untertiteln]**.
   * Navigieren Sie zu einer oder mehreren VTT-Dateien (Video Text Tracks), wählen Sie diese aus und öffnen Sie sie.
   * Damit Untertitel im Medienplayer angezeigt werden, müssen Sie *must* Hinzufügen erforderlicher Details (Metadaten) zu *each* -Untertiteldatei, die Sie hochgeladen haben. Wählen Sie das Stiftsymbol rechts neben dem Namen einer Untertiteldatei aus. Im **Untertitel bearbeiten** Geben Sie die folgenden erforderlichen Details zur Datei ein und wählen Sie **[!UICONTROL Speichern]**. Wiederholen Sie diesen Vorgang für jede hochgeladene Untertiteldatei:

     | Metadaten für Untertitel | Beschreibung |
     |--- |--- |
     | Dateiname | Der Standarddateiname wird aus dem Originaldateinamen abgeleitet. Der Dateiname kann nur beim Hochladen geändert werden und kann später nicht mehr geändert werden. Die Zeichenanforderungen für Dateinamen entsprechen denen für AEM Assets.<br>Derselbe Dateiname kann nicht für zusätzliche Untertiteldateien und Audio-Track-Dateien verwendet werden. |
     | Sprache | Wählen Sie die Sprache des Untertitels aus. |
     | Typ | Wählen Sie den Typ des verwendeten Untertitels aus.<br>**Untertitel** - Der Untertiteltext, der mit dem Video angezeigt wird, das das Dialogfeld übersetzt oder umschreibt.<br>**Beschriftung** - Der Beschriftungstext enthält auch Hintergrundgeräusche, Sprachdifferenzierung und andere relevante Informationen, zusammen mit der Übersetzung oder Transkription des Dialogfelds, wodurch der Inhalt für Personen, die taub oder schwerhörig sind, leichter zugänglich ist. |
     | Bezeichnung | Der Text, der für den Namen des Untertitels im **[!UICONTROL Audio oder Beschriftung auswählen]** Popup-Liste im Medienplayer. Die Beschriftung wird einem Kunden angezeigt, die einem Untertitel- oder Untertitel-Tracking entspricht. Zum Beispiel: `English (CC)`. |

     Sie können Metadaten von Untertiteln bei Bedarf später ändern oder bearbeiten. Wenn das Video veröffentlicht wird, werden diese Details in öffentlichen URLs in veröffentlichten Videos angezeigt.

1. (Optional) Gehen Sie wie folgt vor, um einem Video mindestens eine Audiospur hinzuzufügen:
   * Auswählen **[!UICONTROL Hochladen von Audio-Tracks]**.
   * Navigieren Sie zu einer oder mehreren .mp3-Dateien, wählen Sie sie aus und öffnen Sie sie.
   * Für Audiospuren, die im **[!UICONTROL Audio oder Beschriftung auswählen]** Popup-Liste im Medienplayer, *must* Hinzufügen erforderlicher Details *each* die von Ihnen hinzugefügte Audio-Track-Datei. Wählen Sie das Stiftsymbol rechts neben dem Namen einer Audio-Track-Datei aus. Im **Bearbeiten von Audiospuren** Geben Sie die folgenden erforderlichen Details ein und wählen Sie **[!UICONTROL Speichern]**. Wiederholen Sie diesen Vorgang für jede Audio-Track-Datei, die Sie hochgeladen haben.

     | Audio-Track-Metadaten | Beschreibung |
     |--- |--- |
     | Dateiname | Der Standarddateiname wird aus dem Originaldateinamen abgeleitet. Der Dateiname kann nur beim Hochladen geändert werden und kann später nicht mehr geändert werden. Die Zeichenanforderungen für Dateinamen entsprechen denen für AEM Assets.<br>Derselbe Dateiname kann nicht für zusätzliche Audio-Track-Dateien oder Untertiteldateien verwendet werden. |
     | Sprache | Wählen Sie die Sprache des Audiotracks aus. |
     | Typ | Wählen Sie den Typ des verwendeten Audiotracks aus.<br>**Original** - Der ursprünglich an das Video angehängte und als `[Original]` im Titel mit `English` Sprache, die standardmäßig ausgewählt ist. while **[!UICONTROL Titel]** und **[!UICONTROL Sprache]** kann im Abschnitt **[!UICONTROL Bearbeiten von Audiospuren]** verwendet, werden standardmäßig die ursprünglichen Werte verwendet, wenn das primäre Video erneut verarbeitet wird.<br>**Standard** - Ein zusätzlicher Audio-Track für eine andere Sprache als das Original.<br>**Audiobeschreibung** - Ein Audio-Track, der auch eine beschreibende Darstellung nichtverbaler Aktionen und Gesten im Video enthält, wodurch Inhalte für Personen mit Sehbehinderungen leichter zugänglich sind. |
     | Bezeichnung | Der Text, der im **[!UICONTROL Audio oder Beschriftung auswählen]** Popup-Liste im Medienplayer. Die Bezeichnung ist das, was ein Kunde sieht, das einem Audio-Track entspricht. Beispiel: `English [Original]`. Der Titel der an ein Video angehängten Audiodatei ist auf `[Original|` Standardmäßig. |

     Sie können diese Audio-Track-Metadaten bei Bedarf später ändern oder bearbeiten. Wenn das Video veröffentlicht wird, werden diese Details in öffentlichen URLs in veröffentlichten Videos angezeigt.

1. In der rechten oberen Ecke der Seite können Sie über das **[!UICONTROL Speichern und schließen]** Dropdown-Liste auswählen **[!UICONTROL Speichern]**. Die Dateien werden hochgeladen und die Metadatenverarbeitung beginnt, wie in der **Status** -Spalte der Schnittstelle.

   >[!NOTE]
   >
   >Je nach den Cacheeinstellungen Ihrer Instanz kann die Metadatenverarbeitung mehrere Minuten dauern, bis sie in der Vorschau und in veröffentlichten URLs angezeigt wird.

1. (Optional) Wenn Sie **[!UICONTROL Speichern und schließen]** im vorherigen Schritt anstatt **[!UICONTROL Speichern]** können Sie weiterhin den Verarbeitungsstatus der hochgeladenen Dateien anzeigen. Siehe [Anzeigen des Lebenszyklusstatus hochgeladener Untertitel- und Audio-Track-Dateien](#lifecycle-status-video).
1. (Optional) Zeigen Sie eine Vorschau des Videos vor der Veröffentlichung an, um sicherzustellen, dass die Untertitel und Audio erwartungsgemäß funktionieren. Siehe [Vorschau eines Videos mit mehreren Untertiteln und Audiospuren](#preview-video-audio-subtitle)
1. Veröffentlichen Sie das Video. Siehe [Veröffentlichen von Assets](publishing-dynamicmedia-assets.md).

#### Über das Hinzufügen von Untertiteln und Audio-Track-Dateien zu einem bereits veröffentlichten Video

Wenn Sie zusätzliche Untertiteldateien oder Audiotrack-Dateien in ein bereits veröffentlichtes Video hochladen, bedeutet dies, dass diese Dateien über eine `Processed` Status nach der Vorbereitung, nach dem Hochladen. An diesem Punkt können Sie eine Videovorschau in Dynamic Media anzeigen, um die neu hochgeladenen Dateien anzuzeigen oder zu hören.

Die folgende Vorschau muss jedoch *publish* das Video erneut für die neu hinzugefügten Untertitel- oder Audio-Track-Dateien, die ebenfalls veröffentlicht werden sollen. Nach der Veröffentlichung sind die Untertitel oder Audioinhalte mit der öffentlichen Dynamic Media-URL verfügbar.

>[!NOTE]
>
>Je nach den Cacheeinstellungen Ihrer Instanz kann es mehrere Minuten dauern, bis Metadaten in der Vorschau und in veröffentlichten URLs aktualisiert werden.

In dem Szenario, in dem Sie Dynamic Media für die sofortige Veröffentlichung konfiguriert haben, wird beim Hochladen zusätzlicher Untertitel- oder Audiodateien sofort eine Veröffentlichung des Videos nach dem Hochladen von Untertitel- oder Audiodateien Trigger.

>[!CAUTION]
>
>Wenn Sie Untertiteldateien oder Audiodateien in ein Video hochladen, das entweder veröffentlicht ist oder dessen Veröffentlichung rückgängig gemacht wird, werden die Dateien gelöscht, wenn Sie [*reprocess*](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets) das Video. Nur das ursprüngliche Audio des Videos bleibt intakt. In solchen Fällen müssen Sie die Untertiteldateien und Audio-Track-Dateien erneut in das Video hochladen.

#### Hinzufügen mehrerer Beschriftungen zu einem Video, das über eine vorhandene URL mit dem Beschriftungs-Modifikator verfügt

Dynamic Media unterstützt das Hinzufügen einer einzelnen Beschriftung mit Video über einen URL-Modifikator. Siehe [Hinzufügen von Untertiteln zu Videos](#adding-captions-to-video).

Mehrere Beschriftungsänderungen haben Vorrang vor einer Beschriftung, die über einen URL-Modifikator für veröffentlichte Videos hinzugefügt wird.

**So fügen Sie einem Video mit einer vorhandenen URL mit einem Untertitelmodifikator mehrere Untertitel hinzu:**

1. Laden Sie die Untertiteldatei hoch, die dem Video bereits als Modifikator hinzugefügt wurde, damit Sie die Datei explizit verwalten können.
1. Laden Sie bei Bedarf weitere Untertitel-/Untertiteldateien hoch.
1. Veröffentlichen Sie das Video wie gewohnt.
Die vorhandene URL mit dem Beschriftungs-Modifikator kann jetzt mehrere Beschriftungen laden.

### Anzeigen des Lebenszyklusstatus hochgeladener Untertitel- und Audio-Track-Dateien{#lifecycle-status-video}

Sie können den Lebenszyklusstatus jeder Untertitel- oder Audio-Track-Datei feststellen, die von der **Untertitel und Audio-Tracks** Tab von **Eigenschaften**.

**So zeigen Sie den Lebenszyklusstatus eines Videos an:**

1. Navigieren Sie zum Video-Asset, dessen Lebenszyklusstatus Sie anzeigen möchten.
1. Wählen Sie im Asset-Auswahlmodus entweder in der Listenansicht oder in der Kartenansicht das Video-Asset aus.
1. Wählen Sie in der Symbolleiste das Symbol Eigenschaften aus (ein Kreis mit einem darin enthaltenen &quot;i&quot;).
1. Wählen Sie auf der Seite Eigenschaften die **[!UICONTROL Untertitel und Audio-Tracks]** Registerkarte. Notieren Sie in der Spalte Status den Status der einzelnen Untertitel oder Audiodateien.

| Untertitel oder Audio-Track-Status | Beschreibung |
| --- | --- |
| Verarbeitung | Wenn ein neuer Untertitel oder eine neue Audio-Track-Datei hinzugefügt und gespeichert wird, erhält sie den Status &quot;Verarbeitung&quot;. Dynamic Media verarbeitet die Datei, indem das Streaming-Manifest an das Hauptvideo angehängt wird. |
| Verarbeitet | Nach Abschluss der Verarbeitung wird der Untertitel oder die Audiospur-Datei bzw. der mit dem primären Video verknüpfte ursprüngliche Audio-Track in einem &quot;verarbeiteten&quot;Status angezeigt. Sie können eine Vorschau der Untertitel- und Audiotrack-Dateien anzeigen, die als &quot;Verarbeitet&quot;angezeigt werden. *before* Sie veröffentlichen das Video live. |
| Veröffentlicht | Der Status &quot;Veröffentlicht&quot;stellt einen ähnlichen Status wie &quot;Veröffentlicht&quot;für ein primäres Video dar. Assets werden veröffentlicht, wenn das Hauptvideo veröffentlicht wird, und sind in der öffentlichen Dynamic Media-URL verfügbar. |
| Fehlgeschlagen | Der Status &quot;Fehlgeschlagen&quot;bedeutet, dass die Verarbeitung eines Untertitels oder einer Audiotrack-Datei nicht abgeschlossen wurde. Löschen Sie den Untertitel oder die Audio-Track-Datei und laden Sie sie erneut hoch. |
| Unveröffentlicht | Wenn die Veröffentlichung eines veröffentlichten primären Videos explizit rückgängig gemacht wird, werden auch alle Untertitel- oder Audiotrack-Dateien, die Sie zum Video hinzugefügt haben, depubliziert. |

![Spalte Status für die Felder Untertitel und Audiospuren hervorgehoben.](/help/assets/dynamic-media/assets/msma-lifecycle-status.png)*Lebenszyklusstatus jedes hochgeladenen Untertitels und jeder Audio-Track-Datei.*

### Festlegen der Standardaudio für ein Video mit mehreren Audiospuren

Standardmäßig wird das ursprüngliche Audio eines Videos als Standardaudio festgelegt, das abgespielt werden soll.

Alle hochgeladenen Audio-Track-Dateien können jedoch als Standardaudio festgelegt werden, das nach dem Laden eines Videos in den Viewer abgespielt wird. In der Benutzeroberfläche &quot;Eigenschaften&quot;unter **Untertitel und Audio-Tracks** Registerkarte, die `Default` wird auf die rechte Seite der Audio-Track-Datei für die Videowiedergabe angewendet.

>[!NOTE]
>
>Die Wiedergabe des Standardaudioinhalts kann auch davon abhängen, was in den folgenden Browsern festgelegt ist:
>
>* Chrome: Das Standardaudio, das im Video festgelegt ist, wird wiedergegeben.
* Safari: Wenn die Standardsprache in Safari festgelegt ist, wird Audio mit der festgelegten Standardsprache wiedergegeben, sofern mit dem Manifest des Videos verfügbar. Andernfalls wird das Standardaudio abgespielt, das als Teil der Eigenschaften eines Videos festgelegt wird.

**So legen Sie die Standardaudio für ein Video mit mehreren Audiospuren fest:**

1. Navigieren Sie zum Video-Asset, dessen standardmäßiger Audiotrack Sie festlegen möchten.
1. Wählen Sie im Asset-Auswahlmodus entweder in der Listenansicht oder in der Kartenansicht das Video-Asset aus.
1. Wählen Sie in der Symbolleiste das Symbol Eigenschaften aus (ein Kreis mit einem darin enthaltenen &quot;i&quot;).
1. Wählen Sie auf der Seite Eigenschaften die **[!UICONTROL Untertitel und Audio-Tracks]** Registerkarte.
1. Unter dem **Audio-Tracks** -Überschrift die Audiotrack-Datei auswählen, die Sie als Standard für das Video festlegen möchten.
1. Auswählen **[!UICONTROL Als Standard festlegen]**.
Im **Als Standard festlegen** Dialogfeld auswählen **[!UICONTROL Ersetzen]**.

   ![Die Überschrift &quot;Audiospuren&quot;mit dem Namen der ausgewählten Audiospur-Datei und der hervorgehobenen Schaltfläche &quot;Als Standard festlegen&quot;.](/help/assets/dynamic-media/assets/msma-defaultaudiotrack.png)*Festlegen des Standard-Audio-Trackings für ein Video.*

1. Wählen Sie oben rechts **[!UICONTROL Speichern und schließen]**.
1. Veröffentlichen Sie das Video. Siehe [Veröffentlichen von Assets](publishing-dynamicmedia-assets.md).

### Vorschau eines Videos mit mehreren Untertiteln und Audiospuren{#preview-video-audio-subtitle}

Nachdem Untertiteldateien und Audio-Track-Dateien in ein Video hochgeladen und verarbeitet wurden, können Sie mit dem Dynamic Media-Video-Viewer eine Vorschau aller verschiedenen Spuren anzeigen. Auf diese Weise können Sie sehen, wie Ihr Video aussieht und wie es für Kunden klingt, und stellen sicher, dass es sich wie erwartet verhält.

Wenn Sie mit dem Video zufrieden sind, können Sie [Veröffentlichen](publishing-dynamicmedia-assets.md) eine der folgenden Methoden verwenden.

Siehe [Einbetten des Video- oder Bild-Viewers auf einer Web-Seite](/help/assets/dynamic-media/embed-code.md).
Siehe [Verknüpfen von URLs mit einer Web-Anwendung](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md). Die URL-basierte Verknüpfungsmethode ist nicht möglich, wenn Ihr interaktiver Inhalt über Links mit relativen URLs verfügt, insbesondere über Links zu Seiten in Adobe Experience Manager Sites.
Siehe [Hinzufügen von Dynamic Media-Assets zu Seiten](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md).

>[!NOTE]
>
Auf der Standardregisterkarte für die Vorschau von Experience Managern werden nicht mehrere Untertitel- und Audiospuren angezeigt. Der Grund dafür ist, dass diese Tracks mit Dynamic Media verknüpft sind und nur mit der Dynamic Media-Viewer-Vorschau angezeigt werden können.

**So zeigen Sie die Vorschau eines Videos an, das mehrere Untertitel und Audiospuren aufweist:**

1. In **[!UICONTROL Assets]**, navigieren Sie zu einem vorhandenen Video, dem Sie mehrere Untertitel und Audiospuren hinzugefügt haben.
1. Klicken Sie auf das Video-Asset, damit Sie es im Vorschaumodus öffnen können.
1. Klicken Sie links oben auf der Vorschauseite auf die Dropdown-Liste und wählen Sie **[!UICONTROL Viewer]** aus.

   ![Dropdown-Liste mit der Option Viewer .](/help/assets/dynamic-media/assets/msma-selectviewers.png)

1. Wählen Sie in der Liste &quot;Viewer&quot;einen Viewer aus, den Sie für die Videovorschau verwenden möchten. Der folgende Screenshot zeigt beispielsweise die **[!UICONTROL Video]** ausgewählter Viewer.

   ![Auswahl des Video-Viewers aus der Dropdownliste &quot;Viewer&quot;.](/help/assets/dynamic-media/assets/msma-dmviewerselected.png)

1. Wählen Sie in der rechten unteren Ecke links neben dem Lautstärkesymbol das Sprechblasensymbol aus und wählen Sie dann die Audio- oder Untertitel aus, die Sie hören oder sehen oder beides. Bei Bedarf können Sie unter Untertitel **[!UICONTROL Aus]** um keine Untertitel oder Untertitel anzuzeigen.

   ![Die Popup-Liste Audio und Untertitel im Video-Viewer.](/help/assets/dynamic-media/assets/msma-selectaudiosubtitle.png)*Simulation eines Benutzers, der Audio und Untertitel für die Videowiedergabe auswählt.*

1. Um mit der Wiedergabe zu beginnen, wählen Sie die Schaltfläche **[!UICONTROL Wiedergabe]** des Videos.
Beachten Sie die **[!UICONTROL URL]** und **[!UICONTROL Einbetten]** -Schaltflächen in der unteren linken Ecke. Verwenden Sie diese Schaltflächen, um [die URL des Videos mit Ihrer Webanwendung verknüpfen](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) oder [Einbetten des Videos auf einer Webseite](/help/assets/dynamic-media/embed-code.md), bzw.
1. Wählen Sie rechts oben auf der Vorschauseite die Option **[!UICONTROL Schließen]**.

### Löschen von Untertitel- oder Audio-Track-Dateien aus einem Video

Sie können Untertitel- oder Audio-Track-Dateien aus einem Video löschen. Das Löschen veröffentlichter Untertitel- oder Audio-Track-Dateien wird automatisch in der veröffentlichten URL des Videos widergespiegelt.

Der ursprüngliche Audio-Track, der aus einem primären Video extrahiert wurde, kann nicht gelöscht werden.

**So löschen Sie Untertitel- oder Audio-Track-Dateien aus einem Video:**

1. Navigieren Sie zum Video-Asset, dessen standardmäßiger Audiotrack Sie festlegen möchten.
1. Wählen Sie im Asset-Auswahlmodus entweder in der Listenansicht oder in der Kartenansicht das Video-Asset aus.
1. Wählen Sie in der Symbolleiste das Symbol Eigenschaften aus (ein Kreis mit einem darin enthaltenen &quot;i&quot;).
1. Wählen Sie auf der Seite Eigenschaften die **[!UICONTROL Untertitel und Audio-Tracks]** Registerkarte.
1. Führen Sie eine der folgenden Aktionen aus:

   * Untertitel - unter dem **Untertitel** -Überschrift eine oder mehrere Untertiteldateien auswählen, die Sie aus dem Video löschen möchten, und wählen Sie dann **[!UICONTROL Löschen]**.
   * Audiospuren - unter dem **Audio-Tracks** -Überschrift eine oder mehrere Audiotrack-Dateien auswählen, die Sie aus dem Video löschen möchten, und dann auswählen **[!UICONTROL Löschen]**.

1. Wählen Sie im Dialogfeld Löschen die Option **[!UICONTROL OK]**.
1. Veröffentlichen Sie das Video.

### Herunterladen von Untertiteln oder Audio-Track-Dateien, die in ein Video hochgeladen wurden

Sie können eine oder mehrere Untertitel- oder Audio-Track-Dateien herunterladen, die Sie zur Verwendung mit einem Video hochgeladen haben. Sie haben die Möglichkeit, entweder alle ausgewählten Dateien als ZIP-Datei herunterzuladen oder für jede Datei einen separaten Download-Ordner zu erstellen.

Der ursprüngliche Audio-Track, der aus einer Primärdatei extrahiert wurde, kann nicht heruntergeladen werden.

**So laden Sie Untertitel- oder Audio-Track-Dateien aus einem Video herunter:**

1. Navigieren Sie zum Video-Asset, dessen standardmäßiger Audiotrack Sie festlegen möchten.
1. Wählen Sie im Asset-Auswahlmodus entweder in der Listenansicht oder in der Kartenansicht das Video-Asset aus.
1. Wählen Sie in der Symbolleiste das Symbol Eigenschaften aus (ein Kreis mit einem darin enthaltenen &quot;i&quot;).
1. Wählen Sie auf der Seite Eigenschaften die **[!UICONTROL Untertitel und Audio-Tracks]** Registerkarte.
1. Führen Sie eine der folgenden Aktionen aus:

   * Untertitel - unter dem **Untertitel** -Überschrift eine oder mehrere Untertiteldateien aus, die Sie aus dem Video herunterladen möchten, und wählen Sie dann **[!UICONTROL Herunterladen]**.
   * Audiospuren - unter dem **Audio-Tracks** -Überschrift eine oder mehrere Audio-Track-Dateien, die Sie aus dem Video herunterladen möchten, auswählen und dann **[!UICONTROL Herunterladen]**.

1. Legen Sie im Dialogfeld Download die folgenden Optionen fest:

   | Option | Beschreibung |
   |--- |--- |
   | Speichern unter | Verwenden Sie den im Textfeld &quot;Speichern unter&quot;angegebenen Standarddateinamen oder geben Sie Ihren eigenen Namen an. |
   | Erstellen Sie einen separaten Ordner für jedes Asset | Erstellen Sie einen Ordner für jede Untertiteldatei oder Audiotrack-Datei, die Sie zum Herunterladen ausgewählt haben. |
   | E-Mail | Verwenden Sie Ihr Standard-E-Mail-Programm, um die ZIP-Datei an eine angegebene E-Mail-Adresse zu senden. |
   | Assets | Gibt die Anzahl der heruntergeladenen Dateien und die Gesamtgröße aller ausgewählten Dateien an. Wenn Sie diese Option deaktivieren, wird die **[!UICONTROL Herunterladen]** -Schaltfläche, sodass Sie keine Dateien herunterladen können. |
1. Auswählen **[!UICONTROL Herunterladen]**.
1. Veröffentlichen Sie das Video. Siehe [Veröffentlichen von Assets](publishing-dynamicmedia-assets.md).






## Hinzufügen von Untertiteln zu Videos {#adding-captions-to-video}

>[!IMPORTANT]
>
Adobe empfiehlt, dass Sie [Multiuntertitel- und Multiaudio-Track-Funktion aktivieren](#enable-dash) auf Ihrem Dynamic Media-Konto. Auf diese Weise können Sie die neueste Dynamic Media-Backend-Architektur und einen vereinfachten Workflow zum Hinzufügen von Untertiteln, Untertiteln und Audiospuren zu Ihren Videos nutzen.

Sorgen Sie dafür, dass Ihre Videos Märkte auf der ganzen Welt erreichen, indem Sie Untertitel zu einzelnen Videos oder adaptiven Videosets hinzufügen. Wenn Sie verdeckte Untertitel hinzufügen, müssen Sie die Audiodaten nicht synchronisieren oder Muttersprachler bzw. Muttersprachlerinnen damit beauftragen, das Audio in einer anderen Sprache neu aufzuzeichnen. Das Video wird in der Sprache, in der es aufgenommen wurde, wiedergegeben. Fremdsprachliche Untertitel werden angezeigt, sodass auch Nutzer anderer Sprachen den Audioteil verstehen können.

Geschlossene Untertitel ermöglichen auch einen besseren Zugang für Personen, die taub oder schwerhörig sind.

>[!NOTE]
>
Der verwendete Video-Player muss die Anzeige von Untertiteln unterstützen.

Weitere Informationen finden Sie unter [Barrierefreiheit in Dynamic Media](/help/assets/dynamic-media/accessibility-dm.md).

Dynamic Media kann Untertiteldateien in das JSON-Format (JavaScript Object Notation) konvertieren. Diese Konvertierung bedeutet, dass Sie den JSON-Text als verborgenes, aber vollständiges Transkript des Videos einfügen können. Suchmaschinen können dann den Inhalt durchsuchen und indizieren, damit Kunden die Videos leichter finden können und zusätzliche Details zum Videoinhalt erhalten.

Weitere Informationen zur Verwendung der JSON-Funktion in einer URL erhalten Sie unter [Serving static (non-image) contents](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/c-serving-static-nonimage-contents.html?lang=de#image-serving-api).

**So fügen Sie einem Video Untertitel hinzu:**

1. Verwenden Sie ein Drittanbieterprogramm bzw. einen Service, um Ihre Untertiteldatei für ein Video zu erstellen.

   Stellen Sie sicher, dass die erstellte Datei dem WebVTT-Standard (Web Video Text Tracks) entspricht. Die Erweiterung der Untertiteldatei lautet .VTT. Weitere Informationen zum WebVTT-Untertitelstandard erhalten Sie auf der folgenden Seite.

   Siehe [WebVTT: The Web Video Text Tracks format](https://w3c.github.io/webvtt/).

   Es gibt sowohl kostenlose als auch Premium-Tools und -Services, die Sie verwenden können, um Untertiteldateien außerhalb von Dynamic Media zu erstellen. Um beispielsweise eine Videountertiteldatei ohne Stile zu erstellen, können Sie das folgende kostenlose Online-Tool für die Erstellung und Bearbeitung von Untertiteln verwenden:

   [WebVTT Caption Maker](https://testdrive-archive.azurewebsites.net/Graphics/CaptionMaker/Default.html)

   Für optimale Ergebnisse verwenden Sie das Tool in Internet Explorer 9 oder höher, Google Chrome oder Safari.

   Fügen Sie im Tool im Feld **[!UICONTROL URL der Videodatei eingeben]** die kopierte URL Ihrer Videodatei ein und klicken Sie dann auf **[!UICONTROL Laden]**. Lesen Sie [Erhalten einer URL für ein Asset](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md#obtaining-a-url-for-an-asset), um die URL für die Videodatei zu erhalten, die Sie dann in das Feld **[!UICONTROL URL der Videodatei eingeben]** einfügen können. Internet Explorer, Chrome oder Safari können das Video dann nativ wiedergeben.

   Folgen Sie jetzt auf der Website den Anweisungen auf dem Bildschirm, um Ihre WebVTT-Datei zu erstellen und zu speichern. Wenn Sie fertig sind, kopieren Sie den Inhalt der Untertiteldatei und fügen Sie ihn in einen Texteditor ein. Speichern Sie ihn dann mit der Dateierweiterung .vtt.

   >[!NOTE]
   >
   Für globale Unterstützung von Videountertiteln in verschiedenen Sprachen ist zu beachten, dass der WebVTT-Standard separate .vtt-Dateien und Abrufe für jede Sprache benötigt, die Sie unterstützen möchten.

   Im Allgemeinen sollte die VTT-Untertiteldatei denselben Namen haben wie die Videodatei, an den jedoch ein Kürzel für die Sprache wie -EN, -FR oder -DE angehängt ist. Dies kann Ihnen helfen, die Generierung von Video-URLs mit Ihrem vorhandenen Web-Content-Management-System zu automatisieren.

1. Laden Sie in Experience Manager Ihre WebVTT-Untertiteldatei in das DAM hoch.
1. Navigieren Sie zum *veröffentlichten* Video-Asset, das Sie mit der hochgeladenen Untertiteldatei verbinden möchten.

   Denken Sie daran, dass URLs erst kopiert werden können, *nachdem* Sie die Assets *veröffentlicht* haben.

   Siehe [Veröffentlichen von Assets](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

1. Führen Sie einen der folgenden Schritte aus:

   * Zur Wiedergabe des Videos in einem Popup-Fensterwählen Sie **[!UICONTROL URL]** aus. Wählen Sie im Dialogfeld „URL“ die URL aus, kopieren Sie sie in die Zwischenablage und fügen Sie sie dann in einen einfachen Texteditor ein. Hängen Sie die kopierte URL des Videos mit der folgenden Syntax an:

     `&caption=<server_path>/is/content/<path_to_caption.vtt_file,1>`

     Notieren Sie den Wert `,1` am Ende des Untertitelpfads. Unmittelbar im Anschluss an die Dateierweiterung VTT haben Sie bei der Angabe des Pfads die Möglichkeit, die Schaltfläche für Untertitel durch Festlegen von `,1` bzw. `,0` in der Video-Player-Leiste zu aktivieren oder zu deaktivieren.

   * Um das Video in einem eingebetteten Viewer anzuzeigen, klicken Sie auf **[!UICONTROL Einbettungs-Code]**. Wählen Sie im Dialogfeld „Einbettungs-Code“ den Einbettungs-Code aus, kopieren Sie den Code in die Zwischenablage und fügen Sie ihn dann in einen einfachen Texteditor ein. Hängen Sie den kopierten Einbettungs-Code mit der folgenden Syntax an:

     `videoViewer.setParam("caption","<path_to_caption.vtt_file,1>");`

     Notieren Sie den Wert `,1` am Ende des Untertitelpfads. Unmittelbar im Anschluss an die Dateierweiterung VTT haben Sie bei der Angabe des Pfads die Möglichkeit, die Schaltfläche für Untertitel durch Festlegen von `,1` bzw. `,0` in der Video-Player-Leiste zu aktivieren oder zu deaktivieren.

## Hinzufügen von Kapitelmarken zu Videos {#adding-chapter-markers-to-video}

Um das Ansehen von und Navigieren in langformatigen Videos zu vereinfachen, können Sie einzelnen Videos oder adaptiven Videosets Kapitelmarken hinzufügen. Wenn ein Benutzer das Video abspielt, kann er auf die Kapitelmarken in der Video-Zeitleiste (auch als Video-Scrubber bezeichnet) klicken. Er kann einfach zu seinem Zielpunkt gehen oder sofort zu neuen Inhalten, Schulungen und Demonstrationen springen.

>[!NOTE]
>
Der verwendete Video-Player muss die Verwendung von Kapitelmarken unterstützen. Dynamic Media-Video-Player unterstützten Kapitelmarken, Video-Player von Drittanbietern jedoch möglicherweise nicht.

<!-- OBSOLETE CONTENT OBSOLETE CONTENT If desired, you can create and brand your own custom video viewer with chapters instead of using a video viewer preset. For instructions on creating your own HTML5 viewer with chapter navigation, in the Adobe Scene7 Viewer SDK for HTML5 guide, reference the heading "Customizing Behavior Using Modifiers" under the classes `s7sdk.video.VideoPlayer` and `s7sdk.video.VideoScrubber`. The Adobe Scene7 Viewer SDK is available as a download from [Adobe Developer Connection](https://help.adobe.com/en_US/scene7/using/WSef8d5860223939e2-43dedf7012b792fc1d5-8000.html). -->

Die Kapitelliste für Videos wird auf die gleiche Weise erstellt wie Untertitel. Das heißt, Sie erstellen eine WebVTT-Datei. Diese Datei muss jedoch getrennt von der WebVTT-Untertiteldatei erstellt werden. Untertitel und Kapitel dürfen nicht in derselben WebVTT-Datei enthalten sein.

Orientieren Sie sich bei der Erstellung einer WebVTT-Datei mit Kapitelnavigation am Format des folgenden Beispiels:

### WebVTT-Datei mit Videokapitelnavigation {#webvtt-file-with-video-chapter-navigation}

```xml {.line-numbers}
WEBVTT
Chapter 1
00:00.000 --> 01:04.364
The bicycle store behind it all.
Chapter 2
01:04.364 --> 02:00.944
Creative Cloud.
Chapter 3
02:00.944 --> 03:02.937
Ease of management for a working solution.
Chapter 4
03:02.937 --> 03:35.000
Cost-efficient access to rapidly evolving technology.
```

Im obigen Beispiel ist `Chapter 1` der Cue-Point-Bezeichner. Diese Angabe ist optional. Die Cue-Point-Zeit `00:00:000 --> 01:04:364` gibt die Start- und Endzeit des Kapitels im Format `00:00:000` an. Die letzten drei Ziffern geben die Millisekunden an und können bei `000` belassen werden. Der Kapiteltitel `The bicycle store behind it all` ist die tatsächliche Beschreibung des Kapitelinhalts. Die Cue-Point-Kennung, die Cue-Point-Zeit und der Kapiteltitel werden im Video-Player in einem Popup-Fenster angezeigt, wenn Benutzer mit dem Mauszeiger auf einen visuellen Cue-Point in der Video-Zeitleiste zeigen.

Da Sie einen HTML5-Video-Viewer verwenden, stellen Sie sicher, dass die erstellte Kapiteldatei dem WebVTT (Web Video Text Tracks)-Standard entspricht. Die Erweiterung des Kapiteldateinamens lautet .VTT. Weitere Informationen zum WebVTT-Untertitelstandard erhalten Sie auf der folgenden Seite.

Siehe [WebVTT: The Web Video Text Tracks format](https://w3c.github.io/webvtt/).

**So fügen Sie Kapitelmarken zu Videos hinzu:**

1. Speichern Sie die VTT-Datei mit UTF-8-Kodierung, um Problemen mit der Zeichendarstellung im Text der Kapiteltitel vorzubeugen.

   Grundsätzlich sollte die Kapitel-VTT-Datei denselben Namen haben wie die Videodatei und über den Dateinamenanhang „chapters“ verfügen. Dies kann Ihnen helfen, die Generierung von Video-URLs mit Ihrem vorhandenen Web-Content-Management-System zu automatisieren.
1. Laden Sie die WebVTT-Kapiteldatei in Experience Manager hoch.

   Siehe [Hochladen von Assets](/help/assets/manage-digital-assets.md#uploading-assets).

1. Führen Sie einen der folgenden Schritte aus:

   <table>
     <tbody>
      <tr>
       <td>Zur Wiedergabe des Videos in einem Popup-Fenster</td>
       <td>
       <ol>
       <li>Navigieren Sie zum <i>veröffentlichten</i> Video-Asset, das Sie mit der hochgeladenen Kapiteldatei verbinden möchten. Denken Sie daran, dass URLs erst kopiert werden können, <i>nachdem</i> Sie die Assets <i>veröffentlicht</i> haben. Siehe <a href="/help/assets/dynamic-media/publishing-dynamicmedia-assets.md">Veröffentlichen von Assets</a>.</li>
       <li>Wählen Sie dann aus dem Dropdown-Menü <strong>Viewer</strong> aus.</li>
       <li>Wählen Sie in der linken Leiste den Namen der Video-Viewer-Vorgabe aus. Auf einer separaten Seite wird eine Vorschau des Videos geöffnet.</li>
       <li>Klicken Sie auf der linken Leiste unten auf <strong>URL</strong>.</li>
       <li>Wählen Sie im Dialogfeld „URL“ die URL aus, kopieren Sie sie in die Zwischenablage und fügen Sie sie dann in einen einfachen Texteditor ein.</li>
       <li>Hängen Sie die kopierte URL des Videos mit der folgenden Syntax an, um sie mit der kopierten URL Ihrer Kapiteldatei zu verknüpfen:<br /> <br /> <code>&navigation=<<i>full_copied_URL_path_to_chapter_file</i>.vtt></code><br /> </li>
       </ol> </td>
      </tr>
      <tr>
       <td>Für ein Erlebnis mit eingebettetem Video-Viewer<br /> </td>
       <td>
       <ol>
       <li>Navigieren Sie zum <i>veröffentlichten</i> Video-Asset, das Sie mit der hochgeladenen Kapiteldatei verbinden möchten. Denken Sie daran, dass URLs erst kopiert werden können, <i>nachdem</i> Sie die Assets <i>veröffentlicht</i> haben. Siehe <a href="/help/assets/dynamic-media/publishing-dynamicmedia-assets.md">Veröffentlichen von Assets</a>.</li>
       <li>Wählen Sie dann aus dem Dropdown-Menü <strong>Viewer</strong> aus.</li>
       <li>Wählen Sie in der linken Leiste den Namen der Video-Viewer-Vorgabe aus. Auf einer separaten Seite wird eine Vorschau des Videos geöffnet.</li>
       <li>Klicken Sie in der linken Leiste unten auf <strong>Einbetten</strong>.</li>
       <li>Wählen Sie im Dialogfeld „Einbettungs-Code“ den Einbettungs-Code aus, kopieren Sie den gesamten Code in die Zwischenablage und fügen Sie ihn dann in einen einfachen Texteditor ein.</li>
       <li>Hängen Sie den Einbettungs-Code des Videos mit der folgenden Syntax an, um ihn mittels der kopierten URL mit Ihrer Kapiteldatei zu verknüpfen:<br /> <br /> <code>videoViewer.setParam("navigation","&lt;<i>full_copied_URL_path_to_chapter_file</i>.vtt>"</code></li>
       </ol> </td>
      </tr>
     </tbody>
   </table>



## Über Videominiaturen {#about-video-thumbnails}

Eine Videominiatur ist eine verkleinerte Version eines Videoframes oder eines Bild-Assets, in dem das Video dem Kunden vorgestellt wird. Die Miniaturansicht sollte dazu dienen, einen Kunden zur Auswahl des Videos zu ermutigen.

Alle Videos in Experience Manager müssen ein zugehöriges Miniaturbild enthalten. Sie können ein Miniaturbild nicht löschen, ohne es zu ersetzen. Wenn Sie ein Video in Experience Manager hochladen, wird standardmäßig der erste Frame als Miniaturansicht verwendet. Sie können jedoch die Miniaturansicht anpassen, z. B. für Branding oder visuelle Suche. Wenn Sie eine Videominiatur anpassen, können Sie entweder das Video abspielen und den Frame anhalten, den Sie verwenden möchten. Sie können auch ein Bild-Asset auswählen, das Sie bereits in Ihrem Digital Asset Manager hochgeladen und *veröffentlicht* haben.

Wenn die Miniaturansicht für ein Video geändert wird, wird die Erstellung von Miniaturbildern über den Asset compute-Service bei der erneuten Verarbeitung des Videos übersprungen.

Die Möglichkeit, eine Videominiaturansicht anzupassen, ist erst verfügbar, nachdem Sie ein Videoprofil auf den Ordner angewendet haben, in dem sich das Video befindet.

### Hinzufügen einer benutzerdefinierten Videominiatur {#adding-a-custom-video-thumbnail}

1. Vergewissern Sie sich, dass Sie bereits Folgendes getan haben:

   * Ein Ordner für Ihre Video-Assets wurde erstellt.
   * [Anwenden eines Videoprofils auf den Ordner](/help/assets/dynamic-media/video-profiles.md#applying-a-video-profile-to-folders).

   * [Ihre Videos wurden in den Ordner hochgeladen](/help/assets/manage-video-assets.md#upload-and-preview-video-assets).

1. Navigieren Sie zu einem hochgeladenen Video-Asset, dessen Miniaturbild Sie ändern möchten.
1. Im Asset-Auswahlmodus können Sie **[!UICONTROL Listenansicht]** oder **[!UICONTROL Kartenansicht]**, wählen Sie das Video-Asset aus.
1. Wählen Sie in der Symbolleiste die **[!UICONTROL Eigenschaften]** -Symbol (ein Kreis mit einem &quot;i&quot; darin).
1. Wählen Sie auf der Seite &quot;Eigenschaften&quot;des Videos die Option **[!UICONTROL Miniatur ändern]**.
1. Befolgen Sie folgende Schritte auf der Seite „Ändern der Miniaturansicht“: 

   * So verwenden Sie einen Frame aus dem Video als neue Miniaturansicht:

      * Wählen Sie in der Symbolleiste **[!UICONTROL Frame aus Video auswählen]**.
      * Wählen Sie die Schaltfläche Abspielen und dann die Schaltfläche Pause auf dem Frame, den Sie als neue Miniaturansicht des Videos erfassen möchten.

   * So verwenden Sie ein Bild-Asset als neue Miniaturansicht:

      * Wählen Sie in der Symbolleiste **[!UICONTROL Auswählen einer Miniatur aus Assets]**.
      * Auswählen **[!UICONTROL Miniaturansicht auswählen]**.
      * Navigieren Sie zu einem zuvor hochgeladenen und veröffentlichten Bild-Asset, das Sie verwenden möchten. Das Asset wird automatisch skaliert, damit es als Miniaturbild für das Video verwendet werden kann.
      * Wählen Sie das Bild-Asset aus und wählen Sie dann **[!UICONTROL Auswählen]**.

1. Wählen Sie auf der Seite &quot;Miniatur ändern&quot;die Option **[!UICONTROL Änderung speichern]**.
1. Wählen Sie auf der Seite &quot;Eigenschaften&quot;des Videos in der oberen rechten Ecke die Option **[!UICONTROL Speichern und schließen]**.



<!--

## About video thumbnails in Dynamic Media Hybrid mode{#about-video-thumbnails-in-dynamic-media-hybrid-mode}

You can choose from one of ten thumbnail images automatically generated by Dynamic Media to add to your video. The video player displays your selected thumbnail when a video asset is used with the Dynamic Media component in the authoring environment of Experience Manager Sites, Experience Manager Mobile, or Experience Manager Screens. The thumbnail serves as a static picture that best represents the contents of your entire video and further encourages users to select the Play button.

Based on the total time of the video, Dynamic Media captures ten (default) thumbnail images at 1%, 11%, 21%, 31%, 41%, 51%, 61%, 71%, 81%, and 91% into the video. The ten thumbnails persist meaning that if you decide to choose a different thumbnail later on, you do not need to regenerate the series. You preview the ten thumbnail images and then select the one you want to use with your video. If you want to change to default you can use CRXDE Lite to configure the time interval that thumbnail images are generated. For example, if you only wanted to generate a series of four evenly spaced thumbnail images from your video, you can configure the interval time at 24%, 49%, 74%, and 99%.

Ideally, you can add a video thumbnail anytime after you upload your video but before you publish the video on your website.

If you prefer, you can choose to upload a custom thumbnail to represent your video instead of using a thumbnail generated by Dynamic Media. For example, you could create a custom thumbnail image that has the title of your video, an eye-catching opening image, or a very specific image captured from your video. The custom video thumbnail image that you upload should have a maximum resolution of 1280 x 720 pixels (minimum width of 640 pixels) and be no larger than 2MB.

See also [About video thumbnails](/help/assets/dynamic-media/video.md#about-video-thumbnails-in-dynamic-media-scene-mode).

-->

<!--

### Adding a video thumbnail {#adding-a-video-thumbnail}

1. Navigate to an uploaded video asset that you want to add a video thumbnail.
1. In asset selection mode either from the List View or the Card View, select the video asset.
1. On the toolbar, select the **[!UICONTROL View Properties]** icon (a circle with an "i" in it).
1. On the video's Properties page, select **[!UICONTROL Change Thumbnail]**.
1. On the Change Thumbnail page, on the toolbar, select **[!UICONTROL Select Frame]**.

   Dynamic Media generates a series thumbnail images from your video, based on the default time interval or time interval you customized.

1. Preview the generated thumbnail images, then select the one you want to add to your video.
1. Select **[!UICONTROL Save Change]**.

   The video's thumbnail image is updated to use the thumbnail you selected. If you later decide to change the thumbnail image, you can return to the **[!UICONTROL Change Thumbnail]** page and select a new one.

   If you configured new default time intervals, or you uploaded a new video to replace the existing video, you will need to have Dynamic Media regenerate the thumbnails.

   See [Configuring the default time interval that video thumbnails are generated](#configuring-the-default-time-interval-that-video-thumbnails-are-generated).

-->

<!--

#### Configuring the default time interval that video thumbnails are generated {#configuring-the-default-time-interval-that-video-thumbnails-are-generated}

When you configure and save the new default time interval, your change automatically applies only to videos that you upload in the future. It does not automatically apply the new default to videos that you previously uploaded. For existing videos, you must regenerate the thumbnails.

See [Adding a video thumbnail](#adding-a-video-thumbnail).

**To configure the default time interval that video thumbnails are generated,**

1. In Experience Manager, navigate to **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL CRXDE Lite]**.

1. In the CRXDE Lite page, in the directory panel on the left, navigate t `o etc/dam/imageserver/configuration/jcr:content/settings.`

   if the directory panel is not visible, you may need to select the >> icon to the left of the Home tab.

1. On the lower-right panel, in the Properties tab, double-tap `thumbnailtime`.
1. In the Edit thumbnailtime dialog box, use the text fields to enter interval values as percentages.

    * Select the plus sign (+) icon to add one or more interval value fields. You may need to scroll to the bottom of the dialog box to see the icon.
    * Select the minus sign (-) icon to the right of an interval value field to delete it from the list.
    * Select the up arrow icon and the down arrow icon to reorder the interval values.

1. Select **[!UICONTROL OK]** to return to the Properties tab.
1. Near the upper-left corner of the CRXDE Lite page, select **[!UICONTROL Save All]**, then select the Back Home icon in the upper-left corner to return to Experience Manager.

   See [Adding a video thumbnail](#adding-a-video-thumbnail).

-->

<!--

### Adding a custom video thumbnail {#adding-a-custom-video-thumbnail-1}

These steps apply only to Dynamic Media running in Hybrid mode.

T**o add a custom video thumbnail**,

1. Navigate to an uploaded video asset that you want to add a custom video thumbnail.
1. In asset selection mode either from the List View or the Card View, select the video asset.
1. On the toolbar, select the **[!UICONTROL View Properties]** icon (a circle with an "i" in it).
1. On the video's Properties page, select **[!UICONTROL Change Thumbnail]**.
1. On the Change Thumbnail page, on the toolbar, select **[!UICONTROL Upload New Thumbnail]**.
1. Navigate to a thumbnail image you want to use, select it, then select **[!UICONTROL Open]** to begin uploading the image into Experience Manager. Following the upload, be sure you publish the image.
1. After you have successfully uploaded and published the image, in the Change Thumbnail page, select **[!UICONTROL Save Changes]**.

   The custom thumbnail is added to your video.

-->

## Ändern der Dynamic Media-URL für Dynamic Media-Assets

In Dynamic Media verarbeitete Videos können über vordefinierte Viewer sowie durch direkten Zugriff auf die Manifest-URLs und die Wiedergabe über eigene benutzerdefinierte Viewer verwendet werden. Im Folgenden finden Sie die API zum Abrufen von Manifest-URLs für ein Video.

### Über die getVideoManifestURI-API

Die `getVideoManifestURI`API wird über c bereitgestellt`q-scene7-api:com.day.cq.dam.scene7.api` und kann verwendet werden, um die folgenden Manifest-URLs zu generieren:

```java
/**   
* Returns the manifest url for videos 
* @param resource video resource 
* @param manifestType type of video streaming manifest being requested 
* @param onlyIfPublished return a manifest only if the video is published 
* @return the manifest url for videos 
* 
* @throws Exception 
*/
@Nullable 
String getVideoManifestURI(Resource resource, ManifestType manifestType, boolean onlyIfPublished) throws Exception;
```

#### getVideoManifestURI-API-Parameter

Diese API akzeptiert die folgenden drei Parameter:

| Parameter | Beschreibung |
| --- | --- |
| `resource` | Die Ressource, die dem Video entspricht, das von Dynamic Media aufgenommen wurde. |
| `manifestType` | Kann entweder `ManifestType.DASH` oder `ManifestType.HLS` sein |
| `onlyIfPublished` | Auf „true“ gesetzt, wenn der Manifest-URI nur generiert wird, wenn er veröffentlicht und auf der Bereitstellungsebene verfügbar ist. |

Um die Manifest-URLs für Videos mit der oben genannten Methode abzurufen, fügen Sie ein [Videocodierungsprofil](/help/assets/dynamic-media/video-profiles.md#creating-a-video-encoding-profile-for-adaptive-streaming) in den Ordner „Videos hochladen“ hinzu. Dynamic Media verarbeitet diese Videos basierend auf den Codierungen in der Videocodierungsdatei, die dem Ordner zugewiesen wurde. Jetzt können Sie die oben genannte API aufrufen, um Manifest-URLs für die hochgeladenen Videos abzurufen.

### Fehlerszenarien

Die API gibt bei Fehlern „null“ zurück. Ausnahmen werden in Experience Manager-Fehlerprotokollen verzeichnet. Alle solcherart protokollierten Fehler beginnen mit `Could not generate Video Manifest URI`. In den folgenden Szenarien können solche Fehler auftreten:

* Eine `IllegalArgumentException` wird für eine der folgenden Aktionen protokolliert:

   * Der übergebene Parameter `resource` ist „null“.
   * Der übergebene Parameter `resource` ist kein Video.
   * Der übergebene Parameter `manifestType` ist „null“.
   * Der Parameter `onlyIfPublished` wird als „true“ übergeben, aber das Video ist nicht veröffentlicht.
   * Das Video wurde nicht mit einem adaptiven Video-Set aus Dynamic Media aufgenommen.

* `IOException` wird protokolliert, wenn ein Problem beim Herstellen einer Verbindung mit Dynamic Media besteht.
* `UnsupportedOperationException` wird protokolliert, wenn ein `manifestType` übergebener Parameter `ManifestType.DASH` ist, während das Video nicht im DASH-Format verarbeitet wurde.

<!-- THE REMAINING SECTION IS FOR 6.5 ONLY 

The following is an example of the above API using servlets written in *HTTPWhiteBoard* specification. Select each tab for the code syntax.

>[!BEGINTABS]

>[!TAB Add dependency in pom.xml]

+++**Add dependency in pom.xml** 

```java
dependency> 
     <groupId>com.day.cq.dam</groupId> 
     <artifactId>cq-scene7-api</artifactId> 
     <version>5.12.64</version> 
     <scope>provided</scope> 
</dependency> 
```

+++

>[!TAB Sample servlet]

+++**Sample servlet** 

```java
@Component
        service = Servlet.class 
) 
@HttpWhiteboardServletPattern(value = ManifestServlet.SERVLET_PATTERN) 
@HttpWhiteboardContextSelect(value = Constants.SERVLET_CONTEXT_SELECTOR) 
public class ManifestServlet extends HttpServlet { 

   private static final Logger LOGGER = LoggerFactory.getLogger(ManifestServlet.class); 

   private final ObjectMapper objectMapper; 

    @Reference 
    private Scene7Service scene7Service; 

   public static final String SERVLET_PATTERN = Constants.VIDEO_API_PREFIX + "/manifestUrl"; 

   public ManifestServlet() {
         this.objectMapper = new ObjectMapper(); 
         objectMapper.setSerializationInclusion(JsonInclude.Include.NON_NULL); 
   }

   @Override 

   protected void doGet(HttpServletRequest request, HttpServletResponse response) throws IOException {
        final ResourceResolver resolver = getResourceResolver(request); 
        String assetPath = request.getParameter("assetPath"); 
        String manifest = request.getParameter("manifestType"); 
        String onlyIfPublished = request.getParameter("onlyIfPublished"); 
        Resource resource = resolver.getResource(assetPath); 
        response.setCharacterEncoding(StandardCharsets.UTF_8.toString()); 
        response.setContentType("application/json"); 
        if(resource == null) { 
            LOGGER.info("could not retrieve the resource from JCR"); 
            error("could not retrieve the resource from JCR", response); 
            return; 
        }

        String manifestUri = null; 

        try{ 
            ManifestType manifestType =  ManifestType.DASH; 
            if(manifest != null) { 
                manifestType = ManifestType.valueOf(manifest); 
            } 
            manifestUri = scene7Service.getVideoManifestURI(resource, manifestType, onlyIfPublished != null); 
            objectMapper.writeValue(response.getWriter(), new ManifestUrl(manifestUri)); 
            response.setContentType("application/json"); 
        } catch (Exception e) { 
            LOGGER.error(e.getMessage(), e); 
            error(String.format("Unable to get the manifest url for %s. %s", assetPath, e.getMessage()), response); 
        } 
    } 

    private ResourceResolver getResourceResolver(HttpServletRequest request) { 
        Object rr = request.getAttribute(AuthenticationSupport.REQUEST_ATTRIBUTE_RESOLVER); 
        if (!(rr instanceof ResourceResolver)) { 
            throw new IllegalStateException( 
                    "The request does not seem to have been created via Apache Sling's authentication mechanism."); 
        } else { 
            return (ResourceResolver) rr; 
        } 
    } 

    private void error(String errorMessage, HttpServletResponse response) throws IOException { 
        ManifestUrl errorManifest = new ManifestUrl(null); 
        errorManifest.setErrorMessage(errorMessage); 
        response.setStatus(HttpServletResponse.SC_INTERNAL_SERVER_ERROR); 
        objectMapper.writeValue(response.getWriter(), errorManifest); 
    } 
} 
```

+++

>[!TAB Response Class for servlet]

+++**Response Class for servlet** 

```java
public class ManifestUrl extends VideoResponse { 
     String manifestUrl; 
     public ManifestUrl(String manifestUrl) { 
         this.manifestUrl = manifestUrl; 
     } 
     public String getManifestUrl() { 
         return manifestUrl; 
     } 
} 

public abstract class VideoResponse { 
     String errorString; 

     public String getErrorString() { 
         return errorString; 
     } 

     public void setErrorMessage(String errorString) { 
         this.errorString = errorString; 
     } 
} 
```

+++

>[!TAB Constants file referenced in servlet]

+++**Constants file referenced in servlet** 

```java
public final class Constants { 

     private Constants() { 
     } 

     public static final String VIDEO_API_PREFIX = "/dynamicmedia/video"; 
     public static final String SERVLET_CONTEXT_SELECTOR = "(" + HttpWhiteboardConstants.HTTP_WHITEBOARD_CONTEXT_NAME + "=" + 
             DMSampleApiHttpContext.CONTEXT_NAME + ")"; 

 } 
```

+++

>[!TAB ServletContext]

+++**ServletContext** 

Mount the above servlet using a `servletContext`. The following is an example of `servletContext`. 

```java
public class DMSampleApiHttpContext extends ServletContextHelper { 

 public static final String CONTEXT_NAME = "com.adobe.dmSample"; 
 public static final String CONTEXT_PATH = "/dmSample"; 

 private final MimeTypeService mimeTypeService; 

 private final AuthenticationSupport authenticationSupport; 

 /** 
  * Constructs a new context that will use the given dependencies. 
  * 
  * @param mimeTypeService Used when providing mime type of requests. 
  * @param authenticationSupport Used to authenticate requests with sling. 
  */ 
 @Activate 
 public DMSampleApiHttpContext(@Reference final MimeTypeService mimeTypeService, 
                               @Reference final AuthenticationSupport authenticationSupport) { 
     this.mimeTypeService = mimeTypeService; 
     this.authenticationSupport = authenticationSupport; 
 } 

 // ---------- HttpContext interface ---------------------------------------- 
 /** 
  * Returns the MIME type as resolved by the <code>MimeTypeService</code> or 
  * <code>null</code> if the service is not available. 
  */ 
 @Override 
 public String getMimeType(String name) { 
     MimeTypeService mtservice = mimeTypeService; 
     if (mtservice != null) { 
         return mtservice.getMimeType(name); 
     } 
     return null; 
 } 

 /** 
  * Returns the real context path that is used to mount this context. 
  * @param req servlet request 
  * @return the context path 
  */ 
 public static String getRealContextPath(HttpServletRequest req) { 
     final String path = req.getContextPath(); 
     if (path.equals(CONTEXT_PATH)) { 
         return ""; 
     } 
     return path.substring(CONTEXT_PATH.length()); 
 } 

 /** 
  * Returns a request wrapper that transforms the context path back to the original one 
  * @param req request 
  * @return the request wrapper 
  */ 
 public static HttpServletRequest createContextPathAdapterRequest(HttpServletRequest req) { 
     return new HttpServletRequestWrapper(req) { 

         @Override 
         public String getContextPath() { 
             return getRealContextPath((HttpServletRequest) getRequest()); 
         } 

     }; 

 } 

 /** 
  * Always returns <code>null</code> because resources are all provided 
  * through individual endpoint implementations. 
  */ 
 @Override 
 public URL getResource(String name) { 
     return null; 
 } 

 /** 
  * Tries to authenticate the request using the 
  * <code>SlingAuthenticator</code>. If the authenticator or the Repository 
  * is missing this method returns <code>false</code> and sends a 503/SERVICE 
  * UNAVAILABLE status back to the client. 
  */ 
 @Override 
 public boolean handleSecurity(HttpServletRequest request, 
                               HttpServletResponse response) throws IOException { 

     final AuthenticationSupport authenticator = this.authenticationSupport; 
     if (authenticator != null) { 
         return authenticator.handleSecurity(createContextPathAdapterRequest(request), response); 
     } 

     // send 503/SERVICE UNAVAILABLE, flush to ensure delivery 
     response.sendError(HttpServletResponse.SC_SERVICE_UNAVAILABLE, 
             "AuthenticationSupport service missing. Cannot authenticate request."); 
     response.flushBuffer(); 

     // terminate this request now 
     return false; 
 } 
}
```

+++

>[!ENDTABS]



### Use the sample servlet

You invoke the servlet by performing a `GET` operation at `/dmSample/dynamicmedia/video/manifestUrl`. The following query parameters are passed: 

| Query parameter | Description |
| --- | --- |
| `assetPath` | Mandatory. The path to the video for which `manifestUrl` is generated. |
| `manifestType` | Optional. Parameter can be DASH or HLS. If it is not passed, it defaults to DASH. |
| `onlyIfPublished` | Optional. If passed, the `manifestUrl` is returned only if the video is published.  |

In this example, let us assume the following setup: 

* The company is `samplecompany`.
* The authoring instance is `http://sample-aem-author.com`.
* The folder `/content/dam/video-example` has a video encoding profile applied to it. 
* The video `scenery.mp4` is uploaded to the folder `/content/dam/video-example`.

You can invoke the servlet in following ways: 
     
| Type | Description |
| :--- | --- |
| HLS | `http://sample-aem-author.com/dmSample/dynamicmedia/video/manifestUrl?manifestType=HLS&assetPath=/content/dam/video-example/scenery.mp4`<br><br>In case DASH delivery is enabled:<br>`{"manifestUrl":"https://s7d1.scene7.com/is/content/samplecompany/scenery-AVS.m3u8?packagedStreaming=true"}`<br><br>In case DASH delivery is disabled:<br>`{"manifestUrl":"https://s7d1.scene7.com/is/content/samplecompany/scenery-AVS.m3u8"}` |
| DASH | `http://sample-aem-author.com/dmSample/dynamicmedia/video/manifestUrl?manifestType=DASH&assetPath=/content/dam/video-example/scenery.mp4`<br><br>In case DASH delivery is enabled:<br>`{"manifestUrl":"https://s7d1.scene7.com/is/content/samplecompany/scenery-AVS.mpd"}`<br><br>In case DASH delivery is disabled:<br>`{}` |
| Error: asset path is wrong | `http://sample-aem-author.com/dmSample/dynamicmedia/video/manifestUrl?manifestType=DASH&assetPath=/content/dam/video-example/scennnnnnery.mp4`<br><br>`{"errorString":"could not retrieve the resource from JCR"}` |

-->





