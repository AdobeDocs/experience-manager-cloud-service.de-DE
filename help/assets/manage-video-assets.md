---
title: Verwalten von Video-Assets
description: Hochladen, Anzeigen einer Vorschau, Kommentieren und Veröffentlichen von Video-Assets in [!DNL Adobe Experience Manager].
contentOwner: AG
feature: Asset Management, Publishing, Collaboration, Video
role: User
exl-id: 91edce4a-dfa0-4eca-aba7-d41ac907b81e
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: tm+mt
source-wordcount: '4983'
ht-degree: 100%

---

# Verwalten von Video-Assets  {#manage-video-assets}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/managing-video-assets.html?lang=de) |
| AEM as a Cloud Service | Dieser Artikel |

Das Videoformat ist ein wichtiger Bestandteil der digitalen Assets eines Unternehmens. [!DNL Adobe Experience Manager] bietet ausgereifte Produkte und Funktionen, mit denen Sie den gesamten Lebenszyklus von Video-Assets nach deren Erstellung verwalten können.

Lernen Sie, wie Sie die Video-Assets in [!DNL Adobe Experience Manager Assets] verwalten und bearbeiten. Videokodierung und -transkodierung, z. B. FFmpeg-Transkodierung, ist mit Verarbeitungsprofilen und [!DNL Dynamic Media]-Integration möglich. Ohne [!DNL Dynamic Media]-Lizenz bietet [!DNL Experience Manager] grundlegende Unterstützung für Videos, z. B. die Transkodierung mit FFmpeg, die Extraktion von Miniaturbildern für die unterstützten Dateiformate und die Vorschau in der Benutzeroberfläche für Formate, die direkt im Browser wiedergegeben werden.

## Hochladen und Anzeigen der Vorschau von Video-Assets {#upload-and-preview-video-assets}

Sie können Video-Assets im unterstützten Format auf [!DNL Experience Manager Assets] hochladen und eine Vorschau anzeigen.
<!-- It generates previews for video assets with the extension MP4. -->

### Hochladen von Video-Assets

Gehen Sie wie folgt vor, um ein Video-Asset hochzuladen:

1. Navigieren Sie im Ordner „Digitale Assets“ (oder dessen Unterordnern) zum Speicherort, an dem Sie das Asset hinzufügen möchten.
1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Erstellen]** und wählen Sie **[!UICONTROL Dateien]**. <br>Alternativ können Sie eine Datei auf die Benutzeroberfläche ziehen.
In [!DNL Experience Manager Assets] finden Sie weitere Informationen zum [Hochladen von Assets](manage-digital-assets.md#uploading-assets).

<!-- 1. To preview a video in the card view, click the **[!UICONTROL Play]** ![play option](assets/do-not-localize/play.png) option on the video asset. You can pause or play video in the card view only. The [!UICONTROL Play] and [!UICONTROL Pause] options are not available in the list view.
1. To preview the video in the asset details page, select **[!UICONTROL Edit]** on the card. The video plays in the native video player of the browser. You can play, pause, control the volume, and zoom the video to full screen. -->

### Vorschau von Video-Assets

Sie können in der [!DNL Assets]-Benutzeroberfläche eine Vorschau der Videos in den unterstützten Ausgabedarstellungen anzeigen. Gehen Sie wie folgt vor, um eine Vorschau für ein Video-Asset anzuzeigen:

1. Laden Sie ein Video-Asset in einem unterstützten Format auf [!DNL Experience Manager Assets] hoch. Weitere Informationen zu [unterstützten Videoformaten](file-format-support.md#video-formats). <br>Nach dem Hochladen wird das Video-Asset verarbeitet und eine Vorschau-Ausgabedarstellung generiert.
1. Klicken Sie auf das Asset und wählen Sie die Option ![Details](assets/do-not-localize/details_icon.svg) **[!UICONTROL Details]** in der oberen Symbolleiste. Das Video-Asset wird im Video-Viewer geöffnet.
1. Klicken Sie auf das Symbol ![Wiedergabeoption](assets/do-not-localize/play.png) auf der Miniaturansicht des Videos. <br>Sie können das Video wiedergeben und anhalten, die Lautstärke regeln und in den Vollbildmodus wechseln.

Für vorhandene Video-Assets in [!DNL Experience Manager Assets] müssen Sie die Assets in [!DNL Experience Manager] **[!UICONTROL neu verarbeiten]**, um die Videovorschau-Funktion zu aktivieren. Erfahren Sie, wie Sie [digitale Assets in [!DNL Experience Manager] erneut verarbeiten](reprocessing.md) können.

### Einschränkungen der Videovorschau

* MXF-Dateien zeigen keine Videovorschau an, obwohl die Ausgabedarstellung generiert wurde.
* WebM-Dateien generieren keine Vorschauausgabedarstellungen, da sie von Webbrowsern systemintern wiedergegeben werden können.

## Veröffentlichen von Video-Assets {#publish-video-assets}

Nach der Veröffentlichung können Sie die Video-Assets als URL in eine Web-Seite einbeziehen oder die Assets direkt einbetten. Details finden Sie unter [Veröffentlichen von [!DNL Dynamic Media] -Assets](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

## Veröffentlichen von Videos auf YouTube {#publishing-videos-to-youtube}

Sie können in Experience Manager Assets verwaltete Video-Assets direkt in einem zuvor erstellten YouTube-Kanal veröffentlichen.

Um Video-Assets auf YouTube zu veröffentlichen, versehen Sie sie in Experience Manager Assets mit Tags. Diese Tags verknüpfen Sie mit einem YouTube-Kanal. Wenn das Tag eines Video-Assets mit dem Tag eines YouTube-Kanals übereinstimmt, wird das Video auf YouTube veröffentlicht. Die Veröffentlichung auf YouTube erfolgt neben einer normalen Veröffentlichung des Videos, solange ein entsprechendes Tag verwendet wird.

YouTube verwendet eine eigene Kodierung. Daher wird die ursprüngliche Videodatei, die in Experience Manager hochgeladen wurde, auf YouTube veröffentlicht und nicht das Videoausgabeformat, das durch die Codierung von Dynamic Media erstellt wurde. Die Verarbeitung von Videos mit Dynamic Media ist zwar nicht erforderlich, wird aber für den Fall vorausgesetzt, dass eine Viewer-Vorgabe für die Wiedergabe benötigt wird.

Wenn Sie das Videoverarbeitungsprofil umgehen und Videos direkt auf YouTube veröffentlichen, bedeutet das einfach, dass das Video-Asset in Experience Manager Asset keine anzeigbare Miniatur erhält. Das bedeutet auch, dass nicht kodierte Videos mit keinem der Asset-Typen für Dynamic Media funktionieren.

Für das Veröffentlichen von Video-Assets auf YouTube-Servern müssen folgende Aufgaben abgeschlossen werden, damit eine sichere Server-zu-Server-Authentifizierung mit YouTube möglich ist:

1. [Konfigurieren von Google Cloud-Einstellungen](#configuring-google-cloud-settings)
1. [Erstellen eines YouTube-Kanals](#creating-a-youtube-channel)
1. [Hinzufügen von Tags zur Veröffentlichung](#adding-tags-for-publishing)
1. [Einrichten von YouTube in Experience Manager](#setting-up-youtube-in-aem)
1. [(Optional) Automatisieren der Einstellung von YouTube-Standardeigenschaften für hochgeladene Videos](#optional-automating-the-setting-of-default-youtube-properties-for-your-uploaded-videos)
1. [Veröffentlichen von Videos in Ihrem YouTube-Kanal](#publishing-videos-to-your-youtube-channel)
1. [(Optional) Überprüfen des auf YouTube veröffentlichten Videos](/help/assets/dynamic-media/video.md#optional-verifying-the-published-video-on-youtube)
1. [Verknüpfen von YouTube-URLs mit einer Web-Anwendung](#linking-youtube-urls-to-your-web-application)

Sie können auch [die Veröffentlichung von Videos aufheben, um diese von YouTube zu entfernen](#unpublishing-videos-to-remove-them-from-youtube).

### Konfigurieren von Google Cloud-Einstellungen {#configuring-google-cloud-settings}

Um Inhalte auf YouTube zu veröffentlichen, benötigen Sie ein Google-Konto. Wenn Sie über ein Gmail-Konto verfügen, besitzen Sie bereits ein Google-Konto. Wenn Sie noch nicht über ein Google-Konto verfügen, können Sie einfach eines erstellen. Sie benötigen das Konto, um über Anmeldeinformationen für die Veröffentlichung von Video-Assets auf YouTube zu verfügen. <!-- hidden March 3 2022 If you have an account already created, then skip this task and proceed directly to [Create a YouTube channel](#creating-a-youtube-channel). -->

Das mit Google Cloud verwendete Konto und das für YouTube verwendete Google-Konto müssen nicht übereinstimmen.

Google ändert regelmäßig seine Benutzeroberfläche. Daher können die Schritte zum Veröffentlichen von Videos auf YouTube leicht von der folgenden Dokumentation abweichen. Dieser Hinweis gilt auch für YouTube, wenn Sie prüfen möchten, ob Videos hochgeladen wurden.

>[!NOTE]
>
>Zum Zeitpunkt des Verfassens dieses Artikels waren die folgenden Schritte korrekt. Google aktualisiert jedoch regelmäßig ohne Vorankündigung seine Cloud-Webseiten. Daher können einige Konfigurationsoptionen in der Google-Benutzeroberfläche etwas anders benannt sein als der in den Schritten verwendete Name.

**So konfigurieren Sie Google Cloud-Einstellungen:**

1. Erstellen Sie ein Google-Konto.

   Wenn Sie bereits über ein Google-Konto verfügen, können Sie direkt zum nächsten Schritt gehen.

1. Rufen Sie [https://cloud.google.com/](https://cloud.google.com/) auf.
1. Klicken Sie auf der **[!UICONTROL Google Cloud]**-Seite rechts oben auf **[!UICONTROL Konsole]**.

   Sie müssen sich möglicherweise mit den Anmeldedaten für Ihr Google-Konto **[!UICONTROL Anmelden]**, um die Option **[!UICONTROL Konsole]** anzuzeigen.

1. Klicken Sie auf der **[!UICONTROL Dashboard]**-Seite rechts neben **[!UICONTROL Google Cloud Platform]** auf die Dropdown-Liste **[!UICONTROL Projekt]**, um das Dialogfeld **[!UICONTROL Projekt auswählen]** zu öffnen.
1. Wählen Sie im Dialogfeld zum **[!UICONTROL Projekt auswählen]** **[!UICONTROL Neues Projekt]** aus.
1. Geben Sie im Dialogfeld **[!UICONTROL Neues Projekt]** in das Feld **[!UICONTROL Projektname]** den Namen Ihres neuen Projekts ein.

   Ihre Projekt-ID basiert auf dem Projektnamen. Wählen Sie daher den Projektnamen sorgfältig. Er kann nach seiner Erstellung nicht geändert werden. Sie müssen dieselbe Projekt-ID erneut eingeben, wenn Sie später YouTube in Experience Manager einrichten. Schreiben Sie sie daher auf.

1. Wählen Sie **[!UICONTROL Erstellen]** aus.

1. Führen Sie eine der folgenden Aktionen aus:

   * Wählen Sie im Dashboard Ihres Projekts auf der Karte **[!UICONTROL Erste Schritte]** die Option **[!UICONTROL APIs erforschen und aktivieren]**.
   * Wählen Sie im Projekt-Dashboard auf der **[!UICONTROL API]**-Karte die Option zum **[!UICONTROL Aufrufen der API-Übersicht]** aus.

1. Wählen Sie oben auf der Seite mit den **[!UICONTROL APIs und Services]** die Option zum **[!UICONTROL Aktivieren von APIs und Services]** aus.<!-- NEXT STEP BELOW IS STEP 10 -->
1. Wählen Sie auf der Seite mit der **[!UICONTROL API-Bibliothek]** auf der linken Seite unter **[!UICONTROL Kategorie]** **[!UICONTROL YouTube]** aus. Wählen Sie rechts auf der Seite **[!UICONTROL YouTube]** aus.
1. Wählen Sie auf der Seite **[!UICONTROL YouTube]** **[!UICONTROL YouTube-Daten-API v3]** aus.
1. Wählen Sie auf der Seite **[!UICONTROL YouTube-Daten-API v3]** die Option **[!UICONTROL Verwalten]** aus.

   ![6_5_googleaccount-apis-manage](/help/assets/dynamic-media/assets/6_5_googleaccount-apis-manage.png)

1. Um die API zu verwenden, benötigen Sie Anmeldeinformationen. Falls erforderlich, wählen Sie links auf der Seite **[!UICONTROL APIs und Services]** die Option **[!UICONTROL Anmeldedaten]** aus.
1. Wählen Sie auf der Seite **[!UICONTROL Anmeldedaten]** Seite oben **[!UICONTROL Anmeldedaten erstellen]** und anschließend **[!UICONTROL OAuth-Client-ID]** aus.
1. Wählen Sie auf der Seite **[!UICONTROL OAuth-Client-ID erstellen]** in der Dropdown-Liste **[!UICONTROL Anwendungstyp]** die Option **[!UICONTROL Webanwendung]** aus.

   ![6_5_googleaccount-apis-applicationtype](/help/assets/dynamic-media/assets/6_5_googleaccount-apis-applicationtype.png)

1. Führen Sie einen der folgenden Schritte aus:

   * Geben Sie im Feld **[!UICONTROL Name]** einen eindeutigen Namen für Ihren OAuth 2.0-Client ein.
   * Verwenden Sie den Standardnamen, den Google bereits im Feld **[!UICONTROL Name]** vorgegeben hat.

1. Wählen Sie unter der Überschrift **[!UICONTROL Autorisierte JavaScript-Herkünfte]** die Option **[!UICONTROL URI hinzufügen]** aus.

   ![6_5_googleaccount-apis-namauthorizations](/help/assets/dynamic-media/assets/6_5_googleaccount-apis-nameauthorizations.png)

1. Geben Sie im Textfeld **[!UICONTROL URIs]** den folgenden Pfad ein, ersetzen Sie Ihre eigene Domain und Port-Nummer im Pfad und drücken Sie dann die **[!UICONTROL Eingabetaste]**, um den Pfad der Liste hinzuzufügen:

   `https://<servername.domain>:<port_number>`

   Beispiel: `https://1a2b3c.mycompany.com:4321`

   >[!NOTE]
   >
   >Das obige Beispiel für einen URI-Pfad ist hypothetisch und dient nur zu Erläuterungszwecken.

1. Wählen Sie unter der Überschrift **[!UICONTROL Autorisierte Umleitungs-URIs]** die Option „URI hinzufügen“ aus.
1. Geben Sie im Textfeld **[!UICONTROL URIs]** den folgenden Pfad ein, ersetzen Sie Ihre eigene Domain und Port-Nummer im Pfad und drücken Sie dann die **[!UICONTROL Eingabetaste]**, um den Pfad der Liste hinzuzufügen:

   `https://<servername.domain>:<port_number>/etc/cloudservices/youtube.youtubecredentialcallback.json`

   Beispiel: `https://1a2b3c.mycompany.com:4321/etc/cloudservices/youtube.youtubecredentialcallback.json`

   >[!NOTE]
   >
   >Das obige Beispiel für einen URI-Pfad ist hypothetisch und dient nur zu Erläuterungszwecken.

1. Klicken Sie unten auf der Seite **[!UICONTROL OAuth-Client-ID erstellen]** auf **[!UICONTROL Erstellen]**.
1. Gehen Sie im Dialogfeld **[!UICONTROL Erstellter OAuth-Client]** wie folgt vor:

   * (Optional) Kopieren Sie die Werte in den Feldern **[!UICONTROL Ihre Client-ID]** und **[!UICONTROL Ihr Client-Geheimnis]** und speichern Sie.
   * Wählen Sie **[!UICONTROL JSON herunterladen]** aus und speichern Sie dann die JSON-Datei.

   Sie benötigen diese heruntergeladene JSON-Datei beim späteren Einrichten von YouTube in Adobe Experience Manager.

   ![6_5_googleaccount-apis-oauthclientcreated](/help/assets/dynamic-media/assets/6_5_googleaccount-apis-oauthclientcreated.png)

1. Klicken Sie im Dialogfeld **[!UICONTROL Erstellter OAuth-Client]** auf **[!UICONTROL OK]**.
1. Melden Sie sich von Ihrem Google-Konto ab. Erstellen Sie jetzt einen YouTube-Kanal.

### Erstellen eines YouTube-Kanals {#creating-a-youtube-channel}

Für das Veröffentlichen von Videos auf YouTube benötigen Sie mindestens einen Kanal. Wenn Sie bereits einen YouTube-Kanal erstellt haben, können Sie diese Aufgabe überspringen und zur Aufgabe [Hinzufügen von Tags für die Veröffentlichung](/help/assets/dynamic-media/video.md#adding-tags-for-publishing) wechseln.

>[!CAUTION]
>
>Sie müssen mindestens einen Kanal in YouTube eingerichtet haben, *bevor* Sie unter den YouTube-Einstellungen in Experience Manager (siehe [Einrichten von YouTube in Experience Manager](#setting-up-youtube-in-aem) unten) Kanäle hinzufügen. Wenn Sie den Kanal nicht einrichten, erhalten Sie eine Warnung, dass keine Kanäle vorhanden sind. Beim Hinzufügen eines Kanals wird allerdings weiterhin eine Google-Authentifizierung vorgenommen. Es kann jedoch nicht ausgewählt werden, an welchen Kanal das Video gesendet wird.

**So erstellen Sie einen YouTube-Kanal:**

1. Rufen Sie [https://www.youtube.com](https://www.youtube.com/) auf und melden Sie sich mithilfe Ihrer Google-Kontoanmeldeinformationen an.
1. Klicken Sie in der rechten oberen Ecke der YouTube-Seite auf Ihr Profilbild (kann auch als Buchstabe in einem einfarbigen Kreis angezeigt werden). Klicken Sie dann auf **[!UICONTROL YouTube-Einstellungen]** (Zahnradsymbol).
1. Klicken Sie auf der Seite „Überblick“ unter der Überschrift „Zusätzliche Funktionen“ auf **[!UICONTROL Alle meine Kanäle anzeigen oder neuen Kanal erstellen]**.
1. Klicken Sie auf der Seite „Kanäle“ auf **[!UICONTROL Neuen Kanal erstellen]**.
1. Geben Sie auf der Seite „Markenkonto“ im Feld „Name des Markenkontos“ einen Unternehmensnamen oder den Namen eines anderen beliebigen Kanals ein, in dem Ihre Video-Assets veröffentlicht werden sollen. Klicken Sie dann auf **[!UICONTROL Erstellen]**.

   Merken Sie sich den hier eingegebenen Namen. Sie müssen ihn erneut eingeben, wenn Sie YouTube in Experience Manager einrichten müssen.

1. (Optional) Fügen Sie gegebenenfalls weitere Kanäle hinzu.

   Fügen Sie nun die Tags für die Veröffentlichung hinzu.

### Hinzufügen von Tags zur Veröffentlichung {#adding-tags-for-publishing}

Um Ihre Videos auf YouTube zu veröffentlichen, werden Tags von Experience Manager einem oder mehreren YouTube-Kanälen zugeordnet. Informationen zum Hinzufügen von Tags für die Veröffentlichung finden Sie unter [Verwalten von Tags](/help/sites-cloud/authoring/sites-console/tags.md).

Falls Sie die Standard-Tags in Experience Manager verwenden möchten, können Sie diese Aufgabe überspringen und zu [Einrichten von YouTube in Experience Manager](#setting-up-youtube-in-aem) wechseln.

>[!NOTE]
>
>Nach der Konfiguration des Cloud-Service ist keine weitere Konfiguration nötig, um den Replikationsagenten für die YouTube-Veröffentlichung zu aktivieren. Dieser wurde bereits beim Speichern der Cloud Service-Konfiguration aktiviert.

<!-- ### Enabling the YouTube Publish replication agent {#enabling-the-youtube-publish-replication-agent}

After you enable the YouTube Publish replication agent, if you want to test the connection to the Google Cloud account, select **[!UICONTROL Test Connection]**. A browser tab displays the connection results. If you have added YouTube Channels, then a listing of those is displayed as part of the test.

1. In the upper-left corner of Experience Manager, select the Experience Manager logo, then in the left rail, navigate to **[!UICONTROL Tools]** > **[!UICONTROL Deployment]** > **[!UICONTROL Replication]** > **[!UICONTROL Agents on Author]**.
1. On the Agents of Author page, select **[!UICONTROL YouTube Publish (youtube)]**.
1. On the toolbar, to the right of Settings, select **[!UICONTROL Edit]**.
1. Select the **[!UICONTROL Enabled]** checkbox to turn on the replication agent.
1. Select **[!UICONTROL OK]**. -->

### Einrichten von YouTube in Experience Manager {#setting-up-youtube-in-aem}

Mit Experience Manager 6.4 wurde eine neue Methode für die Touch-Benutzeroberfläche eingeführt, um die YouTube-Veröffentlichung in Experience Manager einzurichten. Führen Sie je nach der installierten Experience Manager-Instanz, die Sie verwenden, einen der folgenden Schritte aus:

* Informationen zum Konfigurieren von YouTube in Experience Manager vor 6.4 finden Sie unter [Einrichten von YouTube in Experience Manager vor 6.4](/help/assets/dynamic-media/video.md#setting-up-youtube-in-aem-before).
* Informationen zum Konfigurieren von YouTube in Experience Manager 6.4 oder höher finden Sie im Abschnitt zum [Einrichten von YouTube in Experience Manager 6.4 oder höher](#setting-up-youtube-in-aem-and-later).

#### Einrichten von YouTube in Experience Manager 6.4 oder höher {#setting-up-youtube-in-aem-and-later}

1. Melden Sie sich als Administrator bei Ihrer Dynamic Media-Instanz an.
1. Klicken Sie oben links in Experience Manager auf das Experience Manager-Logo und gehen Sie dann in der linken Leiste zu **[!UICONTROL Tools]** (Hammersymbol) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Konfiguration der YouTube-Veröffentlichung]**.
1. Klicken Sie auf **[!UICONTROL global]** (nicht auswählen).

1. Klicken Sie oben rechts auf der globalen Seite auf **[!UICONTROL Erstellen]**.
1. Geben Sie auf der Seite „YouTube-Veröffentlichungskonfiguration erstellen“ unter „Google Cloud Platform-Einstellungen“ im Feld **[!UICONTROL Anwendungsname]** die Google-Projekt-ID ein.

   Sie haben die Projekt-ID bereits während der Konfiguration der Google Cloud-Einstellungen angegeben.
Lassen Sie die Seite „YouTube-Konfiguration erstellen“ geöffnet. Sie kehren gleich zu ihr zurück.

   ![6_5_youtubepublish-createyoutubeconconfiguration](/help/assets/dynamic-media/assets/6_5_youtubepublish-createyoutubeconfiguration.png)

1. Öffnen Sie die in der vorherigen Aufgabe zum [Konfigurieren von Google Cloud-Einstellungen](/help/assets/dynamic-media/video.md#configuring-google-cloud-settings) heruntergeladene und gespeicherte JSON-Datei in einem Nur-Text-Editor.
1. Markieren und kopieren Sie den gesamten JSON-Text.
1. Kehren Sie zum Dialogfeld „YouTube-Kontoeinstellungen“ zurück. Fügen Sie im Feld **[!UICONTROL JSON-Konfiguration]** den JSON-Text ein.
1. Klicken Sie oben rechts auf der Seite auf **[!UICONTROL Speichern]**.

   Richten Sie jetzt YouTube-Kanäle in Experience Manager ein.

1. Klicken Sie auf **[!UICONTROL Kanal hinzufügen]**.
1. Geben Sie im Dialogfeld „Kanalname“ den Namen des Kanals ein, den Sie zuvor in der Aufgabe zum **[!UICONTROL Hinzufügen von Kanälen zu YouTube]** erstellt haben.

   Sie können optional eine Beschreibung hinzufügen.

1. Klicken Sie auf **[!UICONTROL Hinzufügen]**.
1. Die YouTube-/Google-Authentifizierung wird angezeigt. Wenn Sie nicht bereits beim Google Cloud-Konto angemeldet sind, überspringen Sie diesen Schritt.

   * Geben Sie den Google-Benutzernamen und das -Kennwort ein, der bzw. das mit der Google-Projekt-ID und dem obigen JSON-Text verknüpft ist.
   * In Abhängigkeit davon, über wie viele Kanäle Ihr Konto verfügt, werden mindestens zwei Elemente angezeigt. Wählen Sie einen Kanal aus. Wählen Sie keine E-Mail-Adresse aus, da es sich hierbei nicht um einen Kanal handelt.
   * Klicken Sie auf der nächsten Seite auf **[!UICONTROL Akzeptieren]**, um Zugriff auf diesen Kanal zu gewähren.

1. Klicken Sie auf **[!UICONTROL Zulassen]**.

   Richten Sie jetzt Tags für die Veröffentlichung ein.

1. **[!UICONTROL Einrichten von Tags für die Veröffentlichung]**: Klicken Sie auf der Seite „Cloud Services“ > „YouTube“ auf das Stiftsymbol, um die Liste der Tags zu bearbeiten, die Sie verwenden möchten.
1. Um die Liste der verfügbaren Tags in Experience Manager anzuzeigen, klicken Sie auf das Dropdown-Listen-Symbol (umgekehrtes Caret-Zeichen).
1. Um sie hinzuzufügen, wählen Sie auf ein oder mehrere Tags aus.

   Wählen Sie zum Löschen eines von Ihnen hinzugefügten Tags das Tag aus und klicken Sie auf **[!UICONTROL X]**.

1. Wenn Sie alle gewünschten Tags hinzugefügt haben, klicken Sie auf **[!UICONTROL Speichern]**.

   Nun können Sie Videos in Ihrem YouTube-Kanal veröffentlichen.

#### Einrichten von YouTube in Experience Manager vor 6.4 {#setting-up-youtube-in-aem-before}

1. Melden Sie sich als Administrator bei Ihrer Dynamic Media-Instanz an.

1. Klicken Sie in der linken oberen Ecke von Experience Manager auf das Experience Manager-Logo und gehen Sie dann in der linken Leiste zu **[!UICONTROL Tools]** (Hammersymbol) > **[!UICONTROL Bereitstellung]** > **[!UICONTROL Cloud-Services]**.
1. Klicken Sie unter der Überschrift „Services von Drittanbietern“ unter „YouTube“ auf **[!UICONTROL Jetzt konfigurieren]**.
1. Geben Sie im Dialogfeld „Konfiguration erstellen“ einen Titel (obligatorisch) und einen Namen (optional) in die entsprechenden Felder ein.
1. Wählen Sie **[!UICONTROL Erstellen]**.
1. Geben Sie im Dialogfeld „YouTube-Kontoeinstellungen“ im Feld **[!UICONTROL Anwendungsname]** die Google-Projekt-ID ein.

   Sie haben die Projekt-ID bereits während der [Konfiguration der Google Cloud-Einstellungen](/help/assets/dynamic-media/video.md#configuring-google-cloud-settings) angegeben.
Lassen Sie das Dialogfeld „YouTube-Kontoeinstellungen“ geöffnet, da Sie gleich zu ihm zurückkehren werden.

1. Öffnen Sie die in der vorherigen Aufgabe zum Konfigurieren von Google Cloud-Einstellungen heruntergeladene und gespeicherte JSON-Datei in einem Nur-Text-Editor.
1. Markieren und kopieren Sie den gesamten JSON-Text.
1. Kehren Sie zum Dialogfeld „YouTube-Kontoeinstellungen“ zurück. Fügen Sie im Feld **[!UICONTROL JSON-Konfiguration]** den JSON-Text ein.
1. Klicken Sie auf **[!UICONTROL OK]**.

   Richten Sie jetzt YouTube-Kanäle in Experience Manager ein.

1. Klicken Sie rechts neben **[!UICONTROL Verfügbare Kanäle]** auf **+** (Pluszeichen).
1. Geben Sie im Dialogfeld „Einstellungen für YouTube-Kanal“ im Feld „Titel“ den Namen des Kanals ein, den Sie zuvor in der Aufgabe **[!UICONTROL Hinzufügen von Kanälen zu YouTube]** erstellt haben.

   Sie können optional eine Beschreibung hinzufügen.

1. Klicken Sie auf **[!UICONTROL OK]**.
1. Die YouTube-/Google-Authentifizierung wird angezeigt. Wenn Sie nicht bereits beim Google Cloud-Konto angemeldet sind, überspringen Sie diesen Schritt.

   * Geben Sie den Google-Benutzernamen und das -Kennwort ein, der bzw. das mit der Google-Projekt-ID und dem obigen JSON-Text verknüpft ist.
   * In Abhängigkeit davon, über wie viele Kanäle Ihr Konto verfügt, werden mindestens zwei Elemente angezeigt. Wählen Sie einen Kanal aus. Wählen Sie keine E-Mail-Adresse aus, da es sich hierbei nicht um einen Kanal handelt.
   * Klicken Sie auf der nächsten Seite auf **[!UICONTROL Akzeptieren]**, um Zugriff auf diesen Kanal zu gewähren.

1. Klicken Sie auf **[!UICONTROL Zulassen]**.

   Richten Sie jetzt Tags für die Veröffentlichung ein.

1. **[!UICONTROL Einrichten von Tags für die Veröffentlichung]**: Klicken Sie auf der Seite „Cloud Services“ > „YouTube“ auf das Stiftsymbol, um die Liste der Tags zu bearbeiten, die Sie verwenden möchten.
1. Um die Liste der verfügbaren Tags in Experience Manager anzuzeigen, klicken Sie auf das Dropdown-Listen-Symbol (umgekehrtes Caret-Zeichen).
1. Um sie hinzuzufügen, wählen Sie auf ein oder mehrere Tags aus.

   Wählen Sie zum Löschen eines von Ihnen hinzugefügten Tags das Tag aus und klicken Sie auf **X**.

1. Wenn Sie mit dem Hinzufügen der gewünschten Tags fertig sind, klicken Sie auf **[!UICONTROL OK]**. 

   Nun können Sie Videos in Ihrem YouTube-Kanal veröffentlichen.

### (Optional) Automatisieren der Einstellung von YouTube-Standardeigenschaften für hochgeladene Videos {#optional-automating-the-setting-of-default-youtube-properties-for-your-uploaded-videos}

Sie können die Einstellung von YouTube-Eigenschaften beim Hochladen Ihrer Videos auch automatisieren. Erstellen Sie ein Metadaten-Verarbeitungsprofil in Experience Manager.

Um das Metadaten-Verarbeitungsprofil zu erstellen, kopieren Sie zunächst die Werte aus den Feldern **[!UICONTROL Feldbezeichnung]**, **[!UICONTROL Zuordnung zu Eigenschaft]** und **[!UICONTROL Auswahl]**, die alle in den Metadatenschemata für Videos enthalten sind. Anschließend erstellen Sie Ihr YouTube-Metadaten-Verarbeitungsprofil, indem Sie ihm diese Werte hinzufügen.

**So automatisieren Sie die Einstellung von YouTube-Standardeigenschaften für hochgeladene Videos:**

1. Klicken Sie in der linken oberen Ecke von Experience Manager auf das Experience Manager-Logo und gehen Sie dann in der linken Leiste zu **[!UICONTROL Tools]** (Hammersymbol) > **[!UICONTROL Assets]** > **[!UICONTROL Metadatenschemas]**.
1. Klicken Sie auf **[!UICONTROL standard]**. (Aktiveren Sie nicht das Auswahlfeld links neben „Standard“.)
1. Aktivieren Sie auf der Seite **[!UICONTROL Standard]** das Kontrollkästchen links neben **[!UICONTROL Video]** und klicken Sie dann auf **[!UICONTROL Bearbeiten]**.
1. Klicken Sie auf der Seite „Metadatenschema-Editor“ auf die Registerkarte **[!UICONTROL Erweitert]**.
1. Klicken Sie unter der Überschrift „Veröffentlichen auf YouTube“ auf **[!UICONTROL YouTube-Kategorie]**.
1. Führen Sie auf der Registerkarte **[!UICONTROL Einstellungen]** rechts auf der Seite folgende Schritte aus:

   * Wählen Sie den Wert im Textfeld **[!UICONTROL Zu Eigenschaft zuordnen]** aus und kopieren Sie ihn.
Fügen Sie den kopierten Wert in den geöffneten Texteditor ein. Sie benötigen diesen Wert später, wenn Sie das Metadaten-Verarbeitungsprofil erstellen. Lassen Sie den Texteditor geöffnet.

   * Wählen Sie unter **[!UICONTROL Wahlen]** den Standardwert aus, den Sie verwenden möchten (beispielsweise „Personen und Blogs“ oder „Wissenschaft und Technik“).
Fügen Sie den kopierten Wert in den geöffneten Texteditor ein. Sie benötigen diesen Wert später, wenn Sie das Metadaten-Verarbeitungsprofil erstellen. Lassen Sie den Texteditor geöffnet.

1. Klicken Sie unter der Überschrift „Veröffentlichen auf YouTube“ auf **[!UICONTROL YouTube-Datenschutz]**.
1. Führen Sie auf der Registerkarte **[!UICONTROL Einstellungen]** rechts auf der Seite folgende Schritte aus:

   * Wählen Sie den Wert im Textfeld **[!UICONTROL Zu Eigenschaft zuordnen]** aus und kopieren Sie ihn.
Fügen Sie den kopierten Wert in den geöffneten Texteditor ein. Sie benötigen diesen Wert später, wenn Sie das Metadaten-Verarbeitungsprofil erstellen. Lassen Sie den Texteditor geöffnet.

   * Wählen Sie unter **[!UICONTROL Wahlen]** den Standardwert aus, den Sie verwenden möchten, und kopieren Sie ihn. Beachten Sie, dass unter „Wahlen“ Paare von jeweils zwei Werten vorliegen. Das untere Feld des Wertepaars ist der Standardwert, den Sie kopieren müssen, beispielsweise „Öffentlich“, „Nicht aufgeführt“ oder „Privat“.
Fügen Sie den kopierten Wert in den geöffneten Texteditor ein. Sie benötigen diesen Wert später, wenn Sie das Metadaten-Verarbeitungsprofil erstellen. Lassen Sie den Texteditor geöffnet.

1. Klicken Sie nahe der rechten oberen Ecke der Seite „Metadatenschema-Editor“ auf **[!UICONTROL Abbrechen]**.
1. Klicken Sie in der linken oberen Ecke von Experience Manager auf das Experience Manager-Logo und gehen Sie dann in der linken Leiste zu **[!UICONTROL Tools]** (Hammersymbol) > **[!UICONTROL Assets]** > **[!UICONTROL Metadatenprofile]**.

1. Klicken Sie auf der Seite „Metadatenprofile“ nahe der rechten oberen Ecke der Seite auf **[!UICONTROL Erstellen]**.
1. Geben Sie im Dialogfeld „Metadatenprofil hinzufügen“ im Textfeld **[!UICONTROL Profiltitel]** den Namen `YouTube Video` ein. Klicken Sie danach auf **[!UICONTROL Erstellen]**.
1. Klicken Sie auf der Seite „Metadatenprofil-Editor“ auf die Registerkarte **[!UICONTROL Erweitert]**.
1. Fügen Sie die kopierten YouTube-Publishing-Werte dem Profil hinzu, indem Sie folgende Schritte ausführen:

   * Klicken Sie rechts auf der Seite auf die Registerkarte **[!UICONTROL Formular erstellen]**.
   * (Optional) Ziehen Sie die Komponente mit der Beschriftung **[!UICONTROL Bereichs-Kopfzeile]** nach links und legen Sie sie im Formularbereich ab.
   * (Optional) Klicken Sie auf **[!UICONTROL Feldbezeichnung]**, um die Komponente auszuwählen.
   * (Optional) Geben Sie rechts auf der Seite auf der Registerkarte „Einstellungen“ im Textfeld „Feldbezeichnung“ den Text `YouTube Publishing` ein.
   * Klicken Sie auf die Registerkarte **[!UICONTROL Formular erstellen]**. Ziehen Sie dann die Komponente mit der Bezeichnung **[!UICONTROL Mehrfachwert-Text]** und legen Sie sie unter der Überschrift **[!UICONTROL YouTube-Veröffentlichung]** ab, die Sie gerade erstellt haben.

   * Um die Komponente auszuwählen, klicken Sie auf **[!UICONTROL Feldbezeichnung]**.
   * Fügen Sie die zuvor kopierten YouTube-Publishing-Werte („Feldbezeichnung“ und „Zu Eigenschaft zuordnen“) in die entsprechenden Felder des Formulars ein, das sich rechts auf der Seite „Formular bearbeiten“ auf der Registerkarte „Einstellungen“ befindet. Fügen Sie den Wert für „Wahlen“ in das Feld „Standardwert“ ein.

1. Fügen Sie die kopierten YouTube-Datenschutzwerte dem Profil hinzu, indem Sie folgende Schritte ausführen:

   * Klicken Sie rechts auf der Seite auf die Registerkarte **[!UICONTROL Formular erstellen]**.
   * (Optional) Ziehen Sie die Komponente mit der Beschriftung **[!UICONTROL Bereichs-Kopfzeile]** nach links und legen Sie sie im Formularbereich ab.
   * (Optional) Klicken Sie auf **[!UICONTROL Feldbezeichnung]**, um die Komponente auszuwählen.
   * (Optional) Geben Sie rechts auf der Seite auf der Registerkarte „Einstellungen“ im Textfeld „Feldbezeichnung“ den Text `YouTube Privacy` ein.
   * Klicken Sie auf die Registerkarte **[!UICONTROL Formular erstellen]**. Ziehen Sie dann die Komponente mit der Bezeichnung **[!UICONTROL Mehrfachwert-Text]** und legen Sie sie unter der Überschrift **[!UICONTROL YouTube-Datenschutz]** ab, die Sie gerade erstellt haben.

   * Um die Komponente auszuwählen, klicken Sie auf **[!UICONTROL Feldbezeichnung]**.
   * Fügen Sie die zuvor kopierten YouTube-Publishing-Werte („Feldbezeichnung“ und „Zu Eigenschaft zuordnen“) in die entsprechenden Felder des Formulars ein, das sich rechts auf der Seite „Formular bearbeiten“ auf der Registerkarte „Einstellungen“ befindet. Fügen Sie den Wert für „Wahlen“ in das Feld „Standardwert“ ein.

1. Klicken Sie oben rechts auf der Seite auf **[!UICONTROL Speichern]**.
1. Wenden Sie das Metadatenprofil für YouTube Publishing auf die Ordner an, in die Sie Videos hochladen möchten. Sie müssen sowohl das Metadatenprofil als auch das Videoprofil festlegen.

   Siehe [Metadatenprofile](/help/assets/metadata-profiles.md) und [Videoprofile](/help/assets/dynamic-media/video-profiles.md).

### Veröffentlichen von Videos in Ihrem YouTube-Kanal {#publishing-videos-to-your-youtube-channel}

Nun verknüpfen Sie die Tags, die Sie den Video-Assets zuvor hinzugefügt haben. Dieser Prozess teilt Experience Manager mit, welche Assets in Ihrem YouTube-Kanal veröffentlicht werden sollen.

>[!NOTE]
>
>Beachten Sie, dass eine sofortige Veröffentlichung nicht automatisch für eine Veröffentlichung auf YouTube sorgt. Beim Einrichten von Dynamic Media stehen zwei Veröffentlichungsoptionen zur Auswahl: **[!UICONTROL Sofort]** oder **[!UICONTROL Bei Aktivierung]**.
>
>**[!UICONTROL Sofort veröffentlichen]** bedeutet, dass das hochgeladene Asset nach dem Synchronisieren mit IPS automatisch im Bereitstellungssystem veröffentlicht wird. Das gilt zwar für Dynamic Media, aber nicht für YouTube. Um auf YouTube zu veröffentlichen, müssen Sie über die Experience Manager-Autorenumgebung veröffentlichen.

>[!NOTE]
>
>Um Inhalte über YouTube zu veröffentlichen, verwendet Experience Manager den Workflow **[!UICONTROL In YouTube veröffentlichen]**, mit dem Sie den Fortschritt überwachen und Fehlerinformationen anzeigen können.
>
>Siehe [Überwachen der Videokodierung und des YouTube-Veröffentlichungs-Fortschritts](#monitoring-video-encoding-and-youtube-publishing-progress).
>
>Ausführlichere Fortschrittsinformation können Sie dem YouTube-Protokoll unter „Replikation“ entnehmen. Hinweis: Für die Überwachung solcher Informationen benötigen Sie Administratorzugriff.

**So veröffentlichen Sie Videos in Ihrem YouTube-Kanal:**

1. Gehen Sie in Experience Manager zu einem Video-Asset, das Sie in Ihrem YouTube-Kanal veröffentlichen möchten.
1. Wählen Sie das Video-Asset aus (das adaptive Videoset).
1. Wählen Sie in der Symbolleiste **[!UICONTROL Eigenschaften]** aus.
1. Klicken Sie auf der Registerkarte „Allgemein“ unter der Überschrift „Metadaten“ rechts neben dem Feld „Tags“ auf **[!UICONTROL Auswahl-Dialogfeld öffnen]**.
1. Navigieren Sie auf der Seite „Tags auswählen“ zu den Tags, die Sie verwenden möchten, und wählen Sie ein oder mehrere Tags aus.

   Denken Sie daran, dass die Tags mit dem YouTube-Kanal verknüpft werden müssen.

1. Klicken Sie oben rechts auf der Seite auf **[!UICONTROL Auswählen]**.
1. Klicken Sie in der rechten oberen Ecke der Seite „Video-Eigenschaften“ auf **[!UICONTROL Speichern und schließen]**.
1. Wählen Sie in der Symbolleiste **[!UICONTROL Quick Publish]** aus.

   Siehe auch [Verwalten von Veröffentlichungen mit Experience Manager Sites](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/page-authoring/publication-management-feature-video-use.html?lang=de#page-authoring).

   Optional können Sie das veröffentlichte Video in Ihrem YouTube-Kanal überprüfen.

### (Optional) Überprüfen des auf YouTube veröffentlichten Videos {#optional-verifying-the-published-video-on-youtube}

Sie können auch den Fortschritt der YouTube-Veröffentlichung (oder des Aufhebens der Veröffentlichung) überwachen.

Siehe [Überwachen der Videokodierung und des YouTube-Veröffentlichungs-Fortschritts](#monitoring-video-encoding-and-youtube-publishing-progress).

Publishing-Zeiten können abhängig von zahlreichen Faktoren erheblich variieren, einschließlich Format des Primärvideos, Dateigröße und Upload-Datenverkehr. Der Publishing-Prozess kann einige Minuten bis zu mehrere Stunden dauern. Außerdem werden Formate mit höherer Auflösung viel langsamer gerendert. Bei 720p und 1080p beispielsweise dauert es sehr viel länger als bei 480p, bis das Video erscheint.

Wenn nach acht Stunden noch immer die Statusmeldung **[!UICONTROL Hochgeladen (Verarbeitung läuft, bitte warten)]** angezeigt wird, entfernen Sie das Video von Ihrer Website und laden Sie es erneut hoch.

### Verknüpfen von YouTube-URLs mit Ihrer Web-Anwendung {#linking-youtube-urls-to-your-web-application}

Sie können nach dem Veröffentlichen des Videos eine YouTube-URL-Zeichenfolge abrufen, die durch Dynamic Media generiert wird. Wenn Sie die YouTube-URL kopieren, wird sie in der Zwischenablage abgelegt, sodass Sie sie nach Bedarf in Seiten einer Website oder einem Programm einfügen können.

>[!NOTE]
>
>Die YouTube-URL kann erst kopiert werden, wenn Sie das Video-Asset in YouTube veröffentlicht haben.

So verknüpfen Sie YouTube-URLs mit einer Web-Anwendung:

1. Navigieren Sie zum *auf YouTube veröffentlichten* Video-Asset, dessen URL Sie kopieren möchten, und wählen Sie es aus.

   Denken Sie daran, dass YouTube-URLs erst kopiert werden können, *nachdem* Sie die Video-Assets in YouTube *veröffentlicht* haben.

1. Wählen Sie in der Symbolleiste **[!UICONTROL Eigenschaften]** aus.
1. Wählen Sie die Registerkarte **[!UICONTROL Erweitert]**.
1. Wählen und kopieren Sie unter der Überschrift „YouTube-Veröffentlichung“ in der YouTube-URL-Liste den URL-Text in Ihren Webbrowser, um das Asset in einer Vorschau anzuzeigen oder der Seite mit den Web-Inhalten hinzuzufügen.

### Rückgängigmachen der Veröffentlichung von Videos, damit sie aus YouTube entfernt werden können {#unpublishing-videos-to-remove-them-from-youtube}

Wenn Sie die Veröffentlichung eines Video-Assets in Experience Manager aufheben, wird das Video aus YouTube entfernt.

>[!CAUTION]
>
>Videos, die Sie direkt in YouTube entfernen, erkennt Experience Manager nicht als gelöscht und verhält sich so, als wären sie auf YouTube weiterhin veröffentlicht. Heben Sie die Veröffentlichung von Video-Assets in YouTube immer über Experience Manager auf.

>[!NOTE]
>
>Um Inhalte aus YouTube zu entfernen, verwendet Experience Manager den Workflow **[!UICONTROL Veröffentlichung auf YouTube rückgängig machen]**, mit dem Sie den Fortschritt überwachen und Fehlerinformationen anzeigen können.
>
>Siehe [Überwachen der Videokodierung und des YouTube-Veröffentlichungs-Fortschritts](#monitoring-video-encoding-and-youtube-publishing-progress).

**So heben Sie die Veröffentlichung von Videos auf, um sie aus YouTube zu entfernen:**

1. Navigieren Sie zu den Video-Assets, deren Veröffentlichung in Ihrem YouTube-Kanal Sie aufheben möchten.
1. Wählen Sie in einem Asset-Auswahlmodus eines oder mehrere der veröffentlichten Video-Assets aus.
1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Veröffentlichung verwalten]**. Klicken Sie ggf. auf das Symbol mit den drei Punkten (`. . .`) in der Symbolleiste, um **[!UICONTROL Veröffentlichung verwalten]** anzuzeigen.
1. Klicken Sie auf der Seite „Veröffentlichung verwalten“ auf **[!UICONTROL Veröffentlichung rückgängig machen]**.
1. Klicken Sie oben rechts auf der Seite auf **[!UICONTROL Weiter]**.
1. Klicken Sie oben rechts auf der Seite auf **[!UICONTROL Veröffentlichung rückgängig machen]**.

## Überwachen des Fortschritts von Videokodierung und YouTube-Veröffentlichung {#monitoring-video-encoding-and-youtube-publishing-progress}

Wenn Sie ein neues Video in einen Ordner hochladen, auf den Videokodierung angewendet wird, oder Ihr Video auf YouTube veröffentlichen, haben Sie vielfältige Möglichkeiten, den Fortschritt (oder die aufgetretenen Fehler) der Videokodierung/YouTube-Veröffentlichung zu überwachen. Der tatsächliche Veröffentlichungsfortschritt bei YouTube ist nur über die Protokolle verfügbar. Ob die Veröffentlichung jedoch fehlschlägt oder erfolgreich ist, wird im folgenden Verfahren auf andere Weise beschrieben. Darüber hinaus können Sie in einer E-Mail-Benachrichtigung darüber informiert werden, ob ein Workflow zur YouTube-Veröffentlichung oder Videokodierung abgeschlossen oder unterbrochen wurde.

### Überwachen des Fortschritts {#monitoring-progress}

Sie können den Fortschritt und auch die fehlgeschlagene Kodierung/YouTube-Veröffentlichung überwachen.

1. Fortschritt der Videocodierung in Ihrem Asset-Ordner anzeigen:

   * In der Kartenansicht wird der Fortschritt der Videokodierung in Prozent auf dem Asset angezeigt. Falls ein Fehler auftritt, werden diese Informationen ebenfalls für das Asset angezeigt.

   ![chlimage_1-429](/help/assets/dynamic-media/assets/chlimage_1-429.png)

   * In der Listenansicht wird der Fortschritt der Videokodierung in der Spalte **[!UICONTROL Verarbeitungsstatus]** angezeigt. Bei einem Fehler wird die Nachricht in derselben Spalte angezeigt.

   ![chlimage_1-430](/help/assets/dynamic-media/assets/chlimage_1-430.png)

   Diese Spalte wird standardmäßig nicht angezeigt. Um die Spalte zu aktivieren, wählen Sie aus dem Dropdown-Menü der Anzeige **[!UICONTROL Anzeigeeinstellungen]** und fügen Sie die Spalte **[!UICONTROL Verarbeitungsstatus]** hinzu und klicken Sie auf **[!UICONTROL Aktualisieren]**.

   ![chlimage_1-431](/help/assets/dynamic-media/assets/chlimage_1-431.png)

1. Anzeigen des Fortschritts in den Asset-Details. Wenn Sie ein Asset auswählen, öffnen Sie das Dropdown-Menü und wählen Sie die Option **[!UICONTROL Zeitleiste]**. Um die Ergebnisse auf Workflow-Aktivitäten wie Kodierung oder YouTube-Veröffentlichung zu begrenzen, wählen Sie **[!UICONTROL Workflows]**.

   ![chlimage_1-432](/help/assets/dynamic-media/assets/chlimage_1-432.png)

   Workflow-Informationen – z. B. zur Kodierung – werden in der Zeitleistensegment angezeigt. Bei YouTube-Veröffentlichungen enthält die Workflow-Zeitleistensegment auch den Namen des YouTube-Kanals und die URL zum YouTube-Video. In der Workflow-Zeitleistensegment werden Sie nach der Veröffentlichung auch über eventuelle Fehler benachrichtigt.

   >[!NOTE]
   >
   >Die endgültige Aufzeichnung von Fehlschlag-/Fehlernachrichten kann länger dauern, da für **[!UICONTROL Wiederholungen]**, **[!UICONTROL Wiederholungsverzögerung]** und **[!UICONTROL Zeitüberschreitung]** unter [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr) mehrere Workflow-Konfigurationen vorliegen, beispielsweise:
   >
   >* Konfiguration der Warteschlange für Apache Sling-Aufträge
   >* Handler für externe Prozessaufträge im Adobe Granite-Workflow
   >* Granite-Workflow – Zeitlimit-Warteschlange
   >
   >In diesen Konfigurationen können Sie die Eigenschaften für **[!UICONTROL Wiederholungen]**, **[!UICONTROL Wiederholungsverzögerung]** und **[!UICONTROL Zeitüberschreitung]** anpassen.

1. Informationen zu gestarteten Workflows finden Sie anhand der Workflow-Instanzen unter **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Instanzen]**.

   >[!NOTE]
   >
   >Sie benötigen Administratorrechte, um auf das Menü **[!UICONTROL Tools]** zugreifen zu können.

   ![chlimage_1-433](/help/assets/dynamic-media/assets/chlimage_1-433.png)

   Wählen Sie die Instanz aus und klicken Sie auf **[!UICONTROL Verlauf öffnen]**.

   ![chlimage_1-434](/help/assets/dynamic-media/assets/chlimage_1-434.png)

   Im Bereich „Workflow-Instanzen“ können Sie Workflows auch aussetzen, beenden oder umbenennen. Weitere Informationen finden Sie unter [Workflows verwalten](/help/sites-cloud/authoring/workflows/overview.md).

1. Fehlgeschlagene Aufträge finden Sie unter „Workflowfehler“ unter **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Fehler]**. Unter **[!UICONTROL Workflowfehler]** werden alle fehlgeschlagenen Workflowaktivitäten aufgelistet.

   >[!NOTE]
   >
   >Sie benötigen Administratorrechte, um auf das Menü **[!UICONTROL Tools]** zugreifen zu können.

   ![chlimage_1-435](/help/assets/dynamic-media/assets/chlimage_1-435.png)

   >[!NOTE]
   >
   >Die endgültige Aufzeichnung von Fehlernachrichten kann länger dauern, da für **[!UICONTROL Wiederholungen]**, **[!UICONTROL Wiederholungsverzögerung]** und **[!UICONTROL Zeitüberschreitung]** unter [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr) mehrere Workflow-Konfigurationen vorliegen, beispielsweise:
   >
   >* Konfiguration der Warteschlange für Apache Sling-Aufträge
   >* Handler für externe Prozessaufträge im Adobe Granite-Workflow
   >* Granite-Workflow – Zeitlimit-Warteschlange
   >
   >In diesen Konfigurationen können Sie die Eigenschaften für **[!UICONTROL Wiederholungen]**, **[!UICONTROL Wiederholungsverzögerung]** und **[!UICONTROL Zeitüberschreitung]** anpassen.

1. Informationen zu abgeschlossenen Workflows finden Sie im Workflow-Archiv, das unter **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Archiv]** zur Verfügung steht. Im **[!UICONTROL Workflow-Archiv]** sind alle abgeschlossenen Workflow-Aktivitäten aufgeführt.

   >[!NOTE]
   >
   >Sie benötigen Administratorrechte, um auf das Menü **[!UICONTROL Tools]** zugreifen zu können.

   ![chlimage_1-436](/help/assets/dynamic-media/assets/chlimage_1-436.png)

1. Sie erhalten E-Mail-Benachrichtigungen über abgebrochene oder fehlgeschlagene Workflow-Aufträge. Diese E-Mail-Benachrichtigungen können von einem Administrator konfiguriert werden. Siehe [Konfigurieren von E-Mail-Benachrichtigungen](#configuring-e-mail-notifications).

<!-- EMAIL NOT AVAILABLE IN SKYLINE

#### Configuring e-mail notifications {#configuring-e-mail-notifications}

>[!NOTE]
>
>You may need administrative rights to access the **[!UICONTROL Tools]** menu.

How you configure notification depends on whether you want notifications for YouTube publishing jobs.

* For encoding jobs, you can access the configuration page for all Experience Manager workflow email notifications at **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]** and by searching for **[!UICONTROL Day CQ Workflow Email Notification Service]**. You can select or clear the check boxes for **[!UICONTROL Notify on Abort]** or **[!UICONTROL Notify on Complete]** accordingly.

For YouTube publishing jobs, do the following:

1. In Experience Manager, navigate to **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
1. On the Workflow Models page, select **[!UICONTROL Publish to YouTube]**, then select **[!UICONTROL Edit]** on the toolbar.
1. Near the upper-right corner of the Publish to YouTube workflow page, select **[!UICONTROL Edit]**.
1. Hover the mouse pointer on the YouTube Upload component, then select once to display the inline toolbar.

   ![6_5_publishtoyoutubeworkflow](assets/6_5_publishtoyoutubeworkflow.png)

1. On the inline toolbar, select the Configuration icon (wrench). Select the **[!UICONTROL Arguments]** tab.

   ![6_5_publishtoyoutubeworkflow-configurationicon](assets/6_5_publishtoyoutubeworkflow-configurationicon.png)

1. In the YouTube Upload Process - Step Properties dialog box, select the **[!UICONTROL Arguments]** tab.

   ![6_5_publishtoyoutubeworkflow-arguments-tab](assets/6_5_publishtoyoutubeworkflow-arguments-tab.png)

1. You can select or clear the following check boxes:

    * Publish Start
    * Publish Failure
    * Publish Completion - includes information on channels and URLs

   Clearing a check box means that you will not receive the specified email notification from the YouTube Publish workflow.

   >[!NOTE]
   >
   >These emails are specific to YouTube and are in addition to the generic workflow email notifications. As a result, you may receive two sets of email notification - the generic notification available in the **[!UICONTROL Day CQ Workflow Email Notification Service]** and one specific to YouTube depending on your configuration settings.

1. When you are finished, near the upper-right corner of the dialog box, select the **[!UICONTROL Done]** icon (check mark).
1. On the Publish to YouTube workflow page, near the upper-right corner, select **[!UICONTROL Sync]**.

-->

## Transkodieren mit Verarbeitungsprofil {#transcode-video}

[!DNL Experience Manager] as a [!DNL Cloud Service] erlaubt Ihnen, mithilfe von Verarbeitungsprofilen eine grundlegende Transkodierung von MP4-Videodateien durchführen. Die Funktion ermöglicht Ihnen nicht nur das Hochladen, sondern auch das Anzeigen einer Vorschau und Skalieren einer MP4-Videodatei.

![Erstellen von Verarbeitungsprofilen zum Transkodieren von Videos in [!DNL Experience Manager]](assets/video-processing-profile-for-mp4.png)

*Abbildung: Ein Verarbeitungsprofil zur Videotranskodierung in [!DNL Experience Manager].*

Wenn Sie nur die Breite oder Höhe angeben und das andere Feld leer lassen, wird das Seitenverhältnis bei den Ausgabedarstellungen beibehalten. Der H.264-Video-Codec ist für die Transkodierung verfügbar.

Um Assets mit einem Verarbeitungsprofil zu verarbeiten, fügen Sie einem Ordner ein Profil hinzu. Siehe [Verwenden von Verarbeitungsprofilen zur Verarbeitung von Assets](/help/assets/asset-microservices-configure-and-use.md#use-profiles).

## Hinzufügen von Anmerkungen zu Video-Assets {#annotate-video-assets}

Sie können Anmerkungen zu Video-Assets hinzufügen. Während Videos mit Anmerkungen versehen werden, wird der Player angehalten, damit Sie einem Frame eine Anmerkung hinzufügen können. Details finden Sie unter [Verwalten von Video-Assets](manage-video-assets.md).

>[!NOTE]
>
>Anmerkungen zu Video-Assets im MXF-Videoformat werden noch nicht unterstützt.

1. Wählen Sie in der [!DNL Assets]-Konsole auf der Asset-Karte die Option **[!UICONTROL Bearbeiten]**, um die Seite mit den Asset-Details anzuzeigen.
1. Um das Video wiederzugeben, klicken Sie auf **[!UICONTROL Vorschau]**.
1. Um das Video zu kommentieren, klicken Sie auf **[!UICONTROL Kommentieren]**. Zu dem jeweiligen Zeitpunkt (Frame) im Video wird eine Anmerkung hinzugefügt. Beim Hinzufügen von Anmerkungen können Sie auf der Arbeitsfläche zeichnen und einen Kommentar zur Zeichnung aufnehmen. Kommentare werden automatisch gespeichert. Um den Anmerkungsassistenten zu schließen, klicken Sie auf **[!UICONTROL Schließen]**.
1. Suchen Sie nach einem bestimmten Punkt im Video, indem Sie die Zeit in Sekunden in das **Textfeld** eingeben und auf **Springen** klicken. Um beispielsweise die ersten 20 Sekunden des Videos zu überspringen, geben Sie „20“ in das Textfeld ein.
1. Klicken Sie auf eine Anmerkung, um sie in der Zeitleiste anzuzeigen. Um die Anmerkung aus der Zeitleiste zu löschen, klicken Sie auf **[!UICONTROL Löschen]**.

## Best Practices und Einschränkungen {#tips-limitations}

* Ohne [!DNL Dynamic Media]-Lizenz können Sie MP4-Dateien nur mit Verarbeitungsprofilen verarbeiten.
* Beim Transkodieren von MP4-Dateien mit Verarbeitungsprofilen gelten die folgenden Richtlinien und Einschränkungen:

   * Apple ProRes-Dateien können nur bis zu einer maximalen Auflösung von 1080p transkodiert werden.
   * Wenn die Quelldatei eine Bitrate von mehr als 200 Mbit/s aufweist, können Sie nur bis zu einer maximalen Auflösung von 1080p transkodieren.
   * Wenn die Quelldatei >=60 FPS ist, gelten folgende Maximalgrößen für die Quelldatei:

      * 400 MB für 4k-Transkodierung
      * 800 MB für 1080p-Transkodierung
      * 8 GB für 720p-Transkodierung

   * Die maximale Dateigröße für die Transkodierung mit 4k-Auflösung liegt bei 2,55 GB für eine MP4-Datei mit 4k-Auflösung, einer Bitrate von 12 Mbit/s und 23 FPS.

  **Siehe auch**

* [Assets übersetzen](translate-assets.md)
* [Assets-HTTP-API](mac-api-assets.md)
* [Von AEM Assets unterstützte Dateiformate](file-format-support.md)
* [Suchen von Assets](search-assets.md)
* [Connected Assets](use-assets-across-connected-assets-instances.md)
* [Asset-Berichte](asset-reports.md)
* [Metadatenschemata](metadata-schemas.md)
* [Herunterladen von Assets](download-assets-from-aem.md)
* [Verwalten von Metadaten](manage-metadata.md)
* [Suchfacetten](search-facets.md)
* [Verwalten von Sammlungen](manage-collections.md)
* [Massenimport von Metadaten](metadata-import-export.md)
* [Veröffentlichen von Assets in AEM und Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

>[!MORELIKETHIS]
>
>* [Dokumentation zu Dynamic Media-Videos](/help/assets/dynamic-media/video.md).
>* [Erfahren Sie mehr über die Verwendung, Typen und Konfiguration von Verarbeitungsprofilen](/help/assets/asset-microservices-configure-and-use.md).
