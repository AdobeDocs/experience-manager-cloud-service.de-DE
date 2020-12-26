---
title: Hinzufügen digitaler Assets zu [!DNL Adobe Experience Manager].
description: hinzufügen Sie Ihre digitalen Assets auf [!DNL Adobe Experience Manager] als [!DNL Cloud Service].
translation-type: tm+mt
source-git-commit: 6f5b6ba7da4c0d3161b9f34602b0256c319b191f
workflow-type: tm+mt
source-wordcount: '1903'
ht-degree: 37%

---


# Hinzufügen digitaler Assets zu Adobe Experience Manager {#add-assets-to-experience-manager}

[!DNL Adobe Experience Manager]In wird der binäre Inhalt der hochgeladenen digitalen Dateien mit Rich-Metadaten, Smart-Tags, Ausgabedarstellungen und anderen DAM (Digital Asset Management)-Services erweitert. Sie können verschiedene Arten von Dateien (z. B. Bilder, Dokumente und Raw-Dateien) von Ihrem lokalen Ordner oder Netzlaufwerk in [!DNL Experience Manager Assets] hochladen.

Es steht eine Reihe von Upload-Methoden zur Verfügung. Neben dem am häufigsten verwendeten Browser-Upload gibt es noch weitere Methoden zum Hinzufügen von Assets zum [!DNL Experience Manager]-Repository, einschließlich Desktop-Clients wie Adobe Asset Link oder [!DNL Experience Manager] Desktop-App, Upload- und Erfassungsskripten, die von Kunden erstellt werden, und automatisierte Erfassungsintegrationen, die als [!DNL Experience Manager]-Erweiterungen hinzugefügt werden.

Wir werden uns hier auf Upload-Methoden für Endbenutzer konzentrieren und Links zu Artikeln bereitstellen, die technische Aspekte des Hochladevorgangs und der Erfassung von Assets mit [!DNL Experience Manager]-APIs und -SDKs beschreiben.

Während Sie Binärdateien in [!DNL Experience Manager] hochladen und verwalten können, unterstützen die am häufigsten verwendeten Dateiformate zusätzliche Dienste wie Metadaten-Extraktion oder Vorschau-/Darstellungsgenerierung. Weitere Informationen finden Sie unter [Unterstützte Dateiformate](file-format-support.md).

Sie können sich auch dafür entscheiden, die hochgeladenen Assets zusätzlich zu bearbeiten. Für den Ordner, in den die Assets hochgeladen werden, kann eine Reihe von Asset-Verarbeitungsprofilen konfiguriert werden, um spezifische Metadaten, Ausgabedarstellungen oder Bildbearbeitungs-Service hinzuzufügen. Siehe [Prozesselemente beim Hochladen](#process-when-uploaded).

>[!NOTE]
>
>[!DNL Experience Manager] als  [!DNL Cloud Service] neue Möglichkeit zum Hochladen von Assets - direkter binärer Upload. Es wird standardmäßig von den vordefinierten Produktfunktionen und Clients unterstützt, wie [!DNL Experience Manager]-Benutzeroberfläche, [!DNL Adobe Asset Link], [!DNL Experience Manager] Desktop-App und somit für die Endbenutzer transparent.
>
>Uploadcode, der von den technischen Teams des Kunden angepasst oder erweitert wird, muss die neuen Upload-APIs und Protokolle verwenden.

Assets als [!DNL Cloud Service] stellen die folgenden Upload-Methoden bereit. Adobe empfiehlt, dass Sie Ihre Verwendungsart und Anwendbarkeit einer Upload-Option verstehen, bevor Sie sie verwenden.

| Upload-Methode | Verwendungsbereiche? | Primär Persona |
|---------------------|----------------|-----------------|
| [Benutzeroberfläche der Assets Console](#upload-assets) | Gelegentliches Hochladen, einfache Drücken und Ziehen, Finder-Upload. Verwenden Sie diese Option nicht, um eine große Anzahl von Assets hochzuladen. | Alle Benutzer |
| [Upload-API](#upload-using-apis) | Für dynamische Entscheidungen beim Hochladen. | Entwickler |
| [[!DNL Experience Manager] Desktop-App](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html) | Asset-Erfassung mit niedrigem Volumen, jedoch zur Migration. | Administrator, Marketer |
| [[!DNL Adobe Asset Link]](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/adobe-asset-link.ug.html) | Nützlich, wenn Kreative und Marketingexperten mit Assets aus den unterstützten [!DNL Creative Cloud]-Desktop-Apps arbeiten. | Kreativ, Marketer |
| [Asset-Masseneingabe](#asset-bulk-ingestor) | Empfohlen für umfangreiche Migrationen und gelegentliche Massenvorgänge. Nur für unterstützte Datenspeicher. | Administrator, Entwickler |

## Hochladen von Assets {#upload-assets}

<!-- #ENGCHECK do we support pausing? I couldn't get pause to show with 1.5GB upload.... If not, this should be removed#

   You can pause the uploading of large assets (greater than 500 MB) and resume it later from the same page. Tap the **[!UICONTROL Pause]** icon beside progress bar that appears when an upload starts.

   ![chlimage_1-211](assets/chlimage_1-211.png)

   The size above which an asset is considered a large asset is configurable. For example, you can configure the system to consider assets above 1000 MB (instead of 500 MB) as large assets. In this case, **[!UICONTROL Pause]** appears on the progress bar when assets of size greater than 1000 MB are uploaded.

   The Pause button does not show if a file greater than 1000 MB is uploaded with a file less than 1000 MB. However, if you cancel the less than 1000 MB file upload, the **[!UICONTROL Pause]** button appears.

   To modify the size limit, configure the `chunkUploadMinFileSize` property of the `fileupload`node in the CRX repository.

   When you click the **[!UICONTROL Pause]** icon, it toggles to a **[!UICONTROL Play]** icon. To resume uploading, click the **[!UICONTROL Play]** icon.

   ![chlimage_1-212](assets/chlimage_1-212.png)
-->

<!-- #ENGCHECK do we support pausing? I couldn't get pause to show with 1.5GB upload.... If not, this should be removed#
   The ability to resume uploading is especially helpful in low-bandwidth scenarios and network glitches, where it takes a long time to upload a large asset. You can pause the upload operation and continue later when the situation improves. When you resume, uploading starts from the point where you paused it.
-->

<!-- #ENGCHECK assuming this is not relevant? remove after confirming#
   During the upload operation, [!DNL Experience Manager] saves the portions of the asset being uploaded as chunks of data in the CRX repository. When the upload completes, [!DNL Experience Manager] consolidates these chunks into a single block of data in the repository.

   To configure the cleanup task for the unfinished chunk upload jobs, go to `https://[aem_server]:[port]/system/console/configMgr/org.apache.sling.servlets.post.impl.helper.ChunkCleanUpTask`.
-->

Um eine Datei (oder mehrere Dateien) hochzuladen, können Sie diese auf Ihrem Desktop auswählen und in der Benutzeroberfläche (Webbrowser) in den Zielordner ziehen. Sie können den Upload auch über die Benutzeroberfläche starten.

1. Navigieren Sie in der [!DNL Assets]-Benutzeroberfläche zu dem Speicherort, an dem Sie digitale Assets hinzufügen möchten.
1. Führen Sie einen der folgenden Schritte aus, um die Assets hochzuladen:

   * Klicken Sie in der Symbolleiste auf **[!UICONTROL Erstellen]** > **[!UICONTROL Dateien]**. Sie können die Datei im angezeigten Dialogfeld bei Bedarf umbenennen.
   * Ziehen Sie die Assets in einem Browser, der HTML5 unterstützt, direkt auf die [!DNL Assets]-Benutzeroberfläche. Das Dialogfeld zum Umbenennen der Datei wird nicht angezeigt.

   ![create_menu](assets/create_menu.png)

   Um mehrere Dateien auszuwählen, wählen Sie die `Ctrl`- oder die `Command`-Taste aus und wählen Sie die Assets im Dialogfeld &quot;Dateiauswahl&quot;aus. Bei Verwendung eines iPads können Sie jeweils nur eine Datei auswählen.

1. Um einen laufenden Upload abzubrechen, klicken Sie auf „Schließen“ (`X`) neben der Fortschrittsleiste. Wenn Sie den Upload abbrechen, löscht [!DNL Assets] den teilweise hochgeladenen Teil des Assets.
Wenn Sie einen Upload-Vorgang abbrechen, bevor die Dateien hochgeladen werden, beendet [!DNL Assets] das Hochladen der aktuellen Datei und aktualisiert den Inhalt. Dateien, die bereits hochgeladen wurden, werden jedoch nicht gelöscht.

1. Das Dialogfeld für den Upload-Fortschritt in [!DNL Assets] zeigt die Anzahl der erfolgreich hochgeladenen Dateien und die der Dateien an, die nicht hochgeladen werden konnten.
Darüber hinaus zeigt die [!DNL Assets]-Benutzeroberfläche das letzte hochgeladene Asset oder den Ordner an, den Sie zuerst erstellt haben.

>[!NOTE]
>
>Informationen zum Hochladen verschachtelter Ordnerhierarchien finden Sie unter [Massen-Upload von Assets](#bulk-upload).

<!-- #ENGCHECK I'm assuming this is no longer relevant.... If yes, this should be removed#

### Serial uploads {#serialuploads}

Uploading numerous assets in bulk consumes significant I/O resources, which may adversely impact the performance of [!DNL Assets]. In particular, if you have a slow internet connection, the time to upload drastically increases due to a spike in disk I/O. Moreover, your web browser may introduce additional restrictions to the number of POST requests [!DNL Assets] can handle for concurrent asset uploads. As a result, the upload operation fails or terminate prematurely. In other words, [!DNL Assets] may miss some files while ingesting a bunch of files or altogether fail to ingest any file.

To overcome this situation, [!DNL Assets] ingests one asset at a time (serial upload) during a bulk upload operation, instead of the concurrently ingesting all the assets.

Serial uploading of assets is enabled by default. To disable the feature and allow concurrent uploading, overlay the `fileupload` node in Crx-de and set the value of the `parallelUploads` property to `true`.

### Streamed uploads {#streamed-uploads}

If you upload many assets to [!DNL Experience Manager], the I/O requests to server increase drastically, which reduces the upload efficiency and can even cause some upload task to time out. [!DNL Assets] supports streamed uploading of assets. Streamed uploading reduces the disk I/O during the upload operation by avoiding asset storage in a temporary folder on the server before copying it to the repository. Instead, the data is transferred directly to the repository. This way, the time to upload large assets and the possibility of timeouts is reduced. Streamed upload is enabled by default in [!DNL Assets].

>[!NOTE]
>
>Streaming upload is disabled for [!DNL Experience Manager] running on JEE server with servlet-api version lower than 3.1.
-->

### Handhabung von Uploads, wenn das Asset bereits vorhanden ist {#handling-upload-existing-file}

Sie können ein Asset mit demselben Pfad hochladen (demselben Namen und demselben Speicherort) wie ein vorhandenes Asset. Es wird jedoch ein Warndialogfeld mit den folgenden Optionen angezeigt:

* Vorhandenes Asset ersetzen: Wenn Sie ein vorhandenes Asset ersetzen, werden die Metadaten für das Asset sowie alle zuvor vorgenommenen Änderungen (z. B. Anmerkungen, Zuschneiden usw.) gelöscht.
* Eine andere Version erstellen: Eine neue Version des vorhandenen Assets wird im Repository erstellt. Sie können die beiden Versionen im Ordner [!UICONTROL Zeitschiene] Ansicht und bei Bedarf zur bereits vorhandenen Version zurückkehren.
* Beibehalten: Wenn Sie beide Assets beibehalten möchten, wird das neue Asset mit der Zahl `1` umbenannt, die an seinen Namen angehängt wird.

>[!NOTE]
>
>Wenn Sie im Dialogfeld [!UICONTROL Namenskonflikt] die Option **[!UICONTROL Ersetzen]** auswählen, wird die Asset-ID für das neue Asset neu generiert. Diese ID unterscheidet sich von der ID des vorherigen Assets.
>
>Wenn Asset Insights aktiviert ist, um Impressionen oder Klicks mit [!DNL Adobe Analytics] zu verfolgen, werden die für das Asset erfassten Daten mit der neu generierten Asset-ID ungültig.[!DNL Analytics]

Um das doppelte-Asset in [!DNL Assets] beizubehalten, klicken Sie auf **[!UICONTROL Behalten]**. Tippen oder klicken Sie auf **[!UICONTROL Löschen]**, um das doppelte Asset zu löschen, das Sie gerade hochgeladen haben.

### Behandlung von Dateinamen und unzulässige Zeichen {#filename-handling}

[!DNL Experience Manager Assets] versucht zu verhindern, dass Assets mit den verbotenen Zeichen in ihren Dateinamen hochgeladen werden. Wenn Sie versuchen, ein Asset mit einem Dateinamen mit einem oder mehreren nicht zulässigen Zeichen hochzuladen, zeigt [!DNL Assets] eine Warnmeldung an und stoppt den Upload, bis Sie diese Zeichen entfernen oder mit einem zulässigen Namen hochladen. Einige Methoden zum Hochladen halten Sie nicht daran, Assets mit verbotenen Zeichen in den Dateinamen hochzuladen, sondern ersetzen die Zeichen durch `-`.

Um bestimmte Dateibenennungskonventionen für Ihre Organisation einzuhalten, können Sie im Dialogfeld [!UICONTROL Assets hochladen] lange Namen für die Dateien angeben, die Sie hochladen möchten. Die folgenden Zeichen (in der Liste durch Leerzeichen getrennt) werden nicht unterstützt:

* Ungültige Zeichen für den Asset-Dateinamen `* / : [ \\ ] | # % { } ? &`
* Ungültige Zeichen für den Asset-Ordnernamen `* / : [ \\ ] | # % { } ? \" . ^ ; + & \t`

## Massen-Upload von Assets {#bulk-upload}

Die Massenaufnahme von Assets kann sehr viele Assets effizient handhaben. Eine groß angelegte Erfassung ist jedoch nicht nur eine umfangreiche Datei-Deponie oder eine gelegentliche Migration. Damit eine umfangreiche Erfassung ein aussagekräftiges Projekt ist, das Ihrem Geschäftszweck entspricht und effizient ist, planen Sie die Migration und kuratieren Sie die Organisation der Assets. Alle Einträge sind unterschiedlich, sodass statt zu verallgemeinern, Faktor in der nuancierten Repository Zusammensetzung und geschäftlichen Anforderungen. Im Folgenden finden Sie einige übergreifende Vorschläge zur Planung und Ausführung einer Massenverarbeitung:

* Assets kuratieren: Entfernen Sie Assets, die im DAM nicht benötigt werden. Sie sollten nicht verwendete, veraltete oder Duplikat-Assets entfernen. Dadurch werden die übertragenen Daten und die erfassten Assets reduziert, was zu schnelleren Datensätzen führt.
* Assets organisieren: Sie sollten den Inhalt in einer logischen Reihenfolge organisieren, z. B. nach Dateigröße, Dateiformat, Anwendungsfall oder Priorität. Im Allgemeinen erfordern große komplexe Dateien mehr Verarbeitung. Sie können auch die separate Erfassung großer Dateien mit der Filteroption für die Dateigröße in Betracht ziehen (siehe Beschreibung unten).
* Stärkere Eingaben: Erwägen Sie, Ihre Erfassung in mehrere Massenaufnahmen zu unterteilen. Auf diese Weise können Sie Inhalte früher anzeigen und Ihre Erfassung nach Bedarf aktualisieren. So können Sie beispielsweise verarbeitende, intensive Assets zu Zeiten ohne Spitzen oder allmählich in mehreren Abschnitten erfassen. Sie können jedoch kleinere und einfachere Assets erfassen, für die in einem Schritt keine große Verarbeitungsleistung erforderlich ist.

Um eine größere Anzahl von Dateien hochzuladen, führen Sie einen der folgenden Schritte aus. Siehe auch [Anwendungsfälle und Methoden](#upload-methods-comparison)

* [Asset-Upload-APIs](developer-reference-material-apis.md#asset-upload-technical): Verwenden Sie ein benutzerdefiniertes Upload-Skript oder -Tool, das APIs nutzt, um bei Bedarf zusätzliche Verarbeitungsschritte für Assets hinzuzufügen (z. B. Metadaten übersetzen oder Dateien umbenennen).
* [[!DNL Experience Manager] Desktop-App](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html): Nützlich für Kreativprofis und Marketingexperten, die Assets aus ihrem lokalen Dateisystem hochladen. Verwenden Sie diese Option, um verschachtelte Ordner hochzuladen, die lokal verfügbar sind.
* [Masseningenieurswerkzeug](#asset-bulk-ingestor): Wird zum Erfassen großer Mengen von Assets bei der Bereitstellung gelegentlich oder anfänglich verwendet  [!DNL Experience Manager].

### Asset-Masseningeting-Tool {#asset-bulk-ingestor}

Das Tool wird nur der Administratorgruppe zur Verfügung gestellt, um Assets in großem Maßstab aus Azurblaus- oder S3-Datenspeichern zu verwenden. Sehen Sie sich einen Video-Durchgang der Konfiguration und Erfassung an.

>[!VIDEO](https://video.tv.adobe.com/v/329680/?quality=12&learn=on)

Gehen Sie wie folgt vor, um das Tool zu konfigurieren:

1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Massenimport]**. Wählen Sie die Option **[!UICONTROL Erstellen]**.

![Konfiguration des Massen-Importeurs](assets/bulk-import-config.png)

1. Geben Sie auf der Seite [!UICONTROL Massenimportkonfiguration] die erforderlichen Werte ein.

   * [!UICONTROL Titel]: Ein beschreibender Titel.
   * [!UICONTROL Quelle] importieren: Wählen Sie die entsprechende Datenquelle aus.
   * [!UICONTROL Nach Mindestgröße] filtern: Geben Sie die Mindestdateigröße für Assets in MB an.
   * [!UICONTROL Nach Maximalgröße] filtern: Geben Sie die maximale Dateigröße von Assets in MB an.
   * [!UICONTROL Mime-Typen] ausschließen: Kommagetrennte Liste von MIME-Typen, die von der Erfassung ausgeschlossen werden sollen. Beispiel: `image/jpeg, image/.*, video/mp4`.
   * [!UICONTROL Mime-Typen] einschließen: Kommagetrennte Liste von MIME-Typen, die in die Erfassung einbezogen werden sollen. Siehe [alle unterstützten Dateiformate](/help/assets/file-format-support.md).
   * [!UICONTROL Importmodus]: Wählen Sie Überspringen, Ersetzen oder Version erstellen. Der Modus &quot;Überspringen&quot;ist der Standardmodus. In diesem Modus überspringt der Benutzer den Import eines Assets, sofern es bereits vorhanden ist. Siehe die Bedeutung von [Ersetzen und Erstellen von Versionsoptionen](#handling-upload-existing-file).
   * [!UICONTROL Asset Zielgruppe Folder]: Importieren Sie Ordner in DAM, in den Assets importiert werden sollen. Beispiel: `/content/dam/imported_assets`

1. Sie können Ihre erstellten Ingestor-Konfigurationen löschen, ändern, ausführen und mehr tun. Wenn Sie eine Konfiguration für den Massenimport auswählen, steht die folgende Option in der Symbolleiste zur Verfügung.

   * [!UICONTROL Bearbeiten]: Bearbeiten Sie die ausgewählte Konfiguration.
   * [!UICONTROL Löschen]: Löscht die ausgewählte Konfiguration.
   * [!UICONTROL Überprüfen]: Überprüfen Sie die Verbindung zum Datenspeicher.
   * [!UICONTROL Trockenausführung]: Rufen Sie einen Testlauf der Massenaufnahme auf.
   * [!UICONTROL Ausführen]: Führen Sie die ausgewählte Konfiguration aus.
   * [!UICONTROL Stopp]: Beenden Sie eine aktive Konfiguration.
   * [!UICONTROL Auftragsstatus]: Ansicht des Konfigurationsstatus, wenn er in einem laufenden Importauftrag verwendet oder für einen abgeschlossenen Auftrag verwendet wird.
   * [!UICONTROL Ansicht Assets]: Ansicht des Zielgruppen-Ordners, falls vorhanden.

## Hochladen von Assets mit Desktop-Clients {#upload-assets-desktop-clients}

Neben der Webbrowser-Benutzeroberfläche unterstützt [!DNL Experience Manager] auch andere Clients auf dem Desktop. Sie bieten außerdem ein Upload-Erlebnis, ohne dass der Browser aufgerufen werden muss.

* [[!DNL Adobe Asset Link]](https://helpx.adobe.com/de/enterprise/using/adobe-asset-link.html) bietet den Zugriff auf Assets aus [!DNL Experience Manager] in Adobe Photoshop-, Adobe Illustrator- und Adobe InDesign-Desktop-Anwendungen. Sie können das aktuell geöffnete Dokument direkt über die Adobe Asset Link-Benutzeroberfläche in diesen Desktop-Anwendungen in [!DNL Experience Manager] hochladen.
* [[!DNL Experience Manager] Desktop ](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html) vereinfacht die Arbeit mit Assets auf dem Desktop, unabhängig vom Dateityp oder der nativen Anwendung, die diese verarbeitet. Es ist besonders nützlich, um Dateien in verschachtelten Ordnerhierarchien aus Ihrem lokalen Dateisystem hochzuladen, da der Browserupload nur das Hochladen flacher Dateilisten unterstützt.

## Verarbeiten von Assets beim Hochladen von {#process-when-uploaded}

Um die hochgeladenen Assets weiter zu verarbeiten, können Sie Verarbeitungsordner auf die hochgeladenen Profil anwenden. Die Profil sind auf der Seite **[!UICONTROL Eigenschaften]** eines Ordners unter [!DNL Assets] verfügbar.

![assets-folder-properties](assets/assets-folder-properties.png)

Die folgenden Registerkarten stehen zur Verfügung:

* Mit [Metadatenprofilen](metadata-profiles.md) können Sie Standardeigenschaften für Metadaten auf Assets anwenden, die in diesen Ordner hochgeladen wurden.
* Mit [Verarbeitungsprofilen](asset-microservices-configure-and-use.md) können Sie mehr Ausgabedarstellungen generieren, als standardmäßig möglich sind.

Wenn [!DNL Dynamic Media] in Ihrer Bereitstellung aktiviert ist, stehen außerdem die folgenden Registerkarten zur Verfügung:

* Mit [Dynamic Media-Bildprofilen](dynamic-media/image-profiles.md) können Sie bestimmte Zuschneidefunktionen (**[!UICONTROL Smarter Zuschnitt]** und Pixelzuschnitt) und Scharfzeichnungskonfigurationen auf die hochgeladenen Assets anwenden.
* Mit [Dynamic Media-Videoprofilen](dynamic-media/video-profiles.md) können Sie bestimmte Videokodierungsprofile (Auflösung, Format, Parameter) anwenden.

>[!NOTE]
>
>Das von Dynamic Media unterstützte Zuschneiden und andere Operationen an Assets sind zerstörungsfrei, d. h. sie ändern nicht das hochgeladene Original, sondern stellen Parameter für das Zuschneiden oder die Medientransformation bereit, die bei der Bereitstellung der Assets durchgeführt werden müssen.

Für Ordner mit zugewiesenem Verarbeitungsprofil wird der Profilname in der Miniaturansicht der Kartenansicht angezeigt. In der Listenansicht wird der Profilname in der Spalte **[!UICONTROL Verarbeitungsprofil]** angezeigt.

## Hochladen oder Aufnehmen von Assets mit APIs {#upload-using-apis}

Technische Details zu den Upload-APIs und dem Protokoll sowie Links zu Open-Source-SDK und Beispiel-Clients finden Sie im Abschnitt zum [Asset-Upload](developer-reference-material-apis.md#asset-upload-technical) in der Entwicklerreferenz.

>[!MORELIKETHIS]
>
>* [[!DNL Adobe Experience Manager] Desktop-App](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html)
>* [Info [!DNL Adobe Asset Link]](https://www.adobe.com/de/creativecloud/business/enterprise/adobe-asset-link.html)
>* [[!DNL Adobe Asset Link] Dokumentation](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html)
>* [Technische Referenz zum Asset-Upload](developer-reference-material-apis.md#asset-upload-technical)

