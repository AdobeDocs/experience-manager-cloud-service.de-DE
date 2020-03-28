---
title: Hinzufügen Ihrer digitalen Assets mit Adobe Experience Manager
description: Hinzufügen Ihrer digitalen Assets als Cloud-Dienst an Adobe Experience Manager
translation-type: tm+mt
source-git-commit: 068195919c4bf73c41b1156eadb47544e4c41e65

---


# Digitale Assets in Adobe Experience Manager Hinzufügen {#add-assets-to-experience-manager}

Durch das Hochladen Ihrer digitalen Dateien in Adobe Experience Manager wird der binäre Inhalt der Datei mit Rich-Metadaten, Smart-Tags, Darstellungen und anderen DAM-Diensten (Digital Asset Management) erweitert. Sie können verschiedene Dateitypen (z. B. Bilder, PDF-Dateien, Rohdateien usw.) aus Ihrem lokalen Ordner oder einem Netzlaufwerk in Experience Manager Assets hochladen.

Es stehen eine Reihe von Upload-Methoden zur Verfügung. Neben dem am häufigsten verwendeten Browser-Upload gibt es noch weitere Methoden zum Hinzufügen von Assets zum Experience Manager-Repository, einschließlich Desktop-Clients wie Adobe Asset Link oder Experience Manager Desktop-App, Upload- und Erfassungsskripten, die Kunden erstellen würden, und automatisierte Erfassungsintegrationen, die als AEM-Erweiterungen hinzugefügt werden.

Wir konzentrieren uns hier auf Upload-Methoden für Endbenutzer und stellen Links zu Artikeln bereit, die technische Aspekte des Hochladeens und der Erfassung von Assets mit Experience Manager-APIs und -SDKs beschreiben.

Während Sie in Experience Manager Binärdateien hochladen und verwalten können, unterstützen die am häufigsten verwendeten Dateiformate zusätzliche Dienste wie Metadaten-Extraktion oder Vorschau-/Darstellungsgenerierung. Weitere Informationen finden Sie unter [Unterstützte Dateiformate](file-format-support.md) .

Sie können auch festlegen, dass für die hochgeladenen Assets zusätzliche Verarbeitungsschritte ausgeführt werden. Für den Ordner, in den Assets hochgeladen werden, können mehrere Profil zur Asset-Verarbeitung konfiguriert werden, um bestimmte Metadaten, Darstellungen oder Bildverarbeitungsdienste hinzuzufügen. Weitere Informationen finden Sie unter [Zusätzliche Verarbeitung](#additional-processing) weiter unten.

> [!NOTE]
>
> Experience Manager als Cloud-Dienst nutzt eine neue Methode zum Hochladen von Assets - direktes binäres Hochladen. Es wird standardmäßig von den vordefinierten Produktfunktionen und Clients wie AEM-Benutzeroberfläche, Adobe Asset Link, AEM-Desktop-App und somit für die Endbenutzer transparent unterstützt.
>
> Hochladecode, der von technischen Teams des Kunden angepasst oder erweitert wird, muss die neuen Upload-APIs und -Protokolle verwenden.

## Upload assets {#upload-assets}

Um eine Datei (oder mehrere Dateien) hochzuladen, können Sie sie entweder auf Ihrem Desktop auswählen und per Drag &amp; Drop in die Benutzeroberfläche (Webbrowser) in den Zielordner ziehen. Sie können den Upload auch über die Benutzeroberfläche starten.

1. Navigieren Sie in der Benutzeroberfläche &quot;Assets&quot;zu dem Speicherort, an dem Sie digitale Assets hinzufügen möchten.
1. Führen Sie einen der folgenden Schritte aus, um die Assets hochzuladen:

   * On the toolbar, tap the **[!UICONTROL Create]** icon. Tippen Sie dann im Menü auf **[!UICONTROL Dateien]**. Sie können die Datei im angezeigten Dialogfeld bei Bedarf umbenennen.
   * Ziehen Sie die Assets in einem Browser, der HTML5 unterstützt, direkt auf die Benutzeroberfläche &quot;Assets&quot;. Das Dialogfeld zum Umbenennen der Datei wird nicht angezeigt.
   ![create_menu](assets/create_menu.png)

   Um mehrere Dateien auszuwählen, drücken Sie die Strg- oder Befehlstaste und wählen Sie die Assets im Dateiauswahl-Dialogfeld aus. Bei Verwendung eines iPads können Sie jeweils nur eine Datei auswählen.

<!-- #ENGCHECK do we support pausing? I couldn't get pause to show with 1.5GB upload.... If not, this should be removed#

   You can pause the uploading of large assets (greater than 500 MB) and resume it later from the same page. Tap the **[!UICONTROL Pause]** icon beside progress bar that appears when an upload starts.

   ![chlimage_1-211](assets/chlimage_1-211.png)

   The size above which an asset is considered a large asset is configurable. For example, you can configure the system to consider assets above 1000 MB (instead of 500 MB) as large assets. In this case, **[!UICONTROL Pause]** appears on the progress bar when assets of size greater than 1000 MB are uploaded.

   The Pause button does not show if a file greater than 1000 MB is uploaded with a file less than 1000 MB. However, if you cancel the less than 1000 MB file upload, the **[!UICONTROL Pause]** button appears.

   To modify the size limit, configure the `chunkUploadMinFileSize` property of the `fileupload`node in the CRX repository.

   When you click the **[!UICONTROL Pause]** icon, it toggles to a **[!UICONTROL Play]** icon. To resume uploading, click the **[!UICONTROL Play]** icon.

   ![chlimage_1-212](assets/chlimage_1-212.png)
-->

1. To cancel an ongoing upload, click close (`X`) next to the progress bar. Wenn Sie den Upload abbrechen, löscht AEM Assets den teilweise hochgeladenen Teil des Assets.

   Wenn Sie den Upload abbrechen, bevor die Dateien hochgeladen sind, unterbricht AEM Assets den Upload der aktuellen Datei und aktualisiert den Inhalt. Dateien, die bereits hochgeladen wurden, werden jedoch nicht gelöscht.


<!-- #ENGCHECK do we support pausing? I couldn't get pause to show with 1.5GB upload.... If not, this should be removed#
   The ability to resume uploading is especially helpful in low-bandwidth scenarios and network glitches, where it takes a long time to upload a large asset. You can pause the upload operation and continue later when the situation improves. When you resume, uploading starts from the point where you paused it.
-->

<!-- #ENGCHECK assuming this is not relevant? remove after confirming#
   During the upload operation, AEM saves the portions of the asset being uploaded as chunks of data in the CRX repository. When the upload completes, AEM consolidates these chunks into a single block of data in the repository.

   To configure the cleanup task for the unfinished chunk upload jobs, go to `https://[aem_server]:[port]/system/console/configMgr/org.apache.sling.servlets.post.impl.helper.ChunkCleanUpTask`.
-->


1. Das Dialogfeld „Upload-Fortschritt“ in AEM Assets zeigt die Anzahl der erfolgreich hochgeladenen Dateien und die der Dateien an, die nicht hochgeladen werden konnten.

Darüber hinaus zeigt die Assets-Benutzeroberfläche das zuletzt hochgeladene Asset oder den Ordner, den Sie zuerst erstellt haben.

> [!NOTE]
>
> Informationen zum Hochladen verschachtelter Ordnerhierarchien in AEM finden Sie unter [Massen-Upload von Assets](#bulk-upload).

<!-- #ENGCHECK I'm assuming this is no longer relevant.... If yes, this should be removed#

### Serial uploads {#serialuploads}

Uploading numerous assets in bulk consumes significant I/O resources, which may adversely impact the performance of your AEM Assets instance. In particular, if you have a slow internet connection, the time to upload drastically increases due to a spike in disk I/O. Moreover, your web browser may introduce additional restrictions to the number of POST requests AEM Assets can handle for concurrent asset uploads. As a result, the upload operation fails or terminate prematurely. In other words, AEM assets may miss some files while ingesting a bunch of files or altogether fail to ingest any file.

To overcome this situation, AEM Assets ingests one asset at a time (serial upload) during a bulk upload operation, instead of the concurrently ingesting all the assets.

Serial uploading of assets is enabled by default. To disable the feature and allow concurrent uploading, overlay the `fileupload` node in Crx-de and set the value of the `parallelUploads` property to `true`.

### Streamed uploads {#streamed-uploads}

If you upload many assets to AEM, the I/O requests to server increase drastically, which reduces the upload efficiency and can even cause some upload task to time out. AEM Assets supports streamed uploading of assets. Streamed uploading reduces the disk I/O during the upload operation by avoiding asset storage in a temporary folder on the server before copying it to the repository. Instead, the data is transferred directly to the repository. This way, the time to upload large assets and the possibility of timeouts is reduced. Streamed upload is enabled by default in AEM Assets.

>[!NOTE]
>
>Streaming upload is disabled for AEM running on JEE server with servlet-api version lower than 3.1.
-->

### Verarbeiten von Uploads, wenn Asset bereits vorhanden ist {#handling-upload-existing-file}

Wenn Sie ein Asset unter einem Namen hochladen, der bereits für ein Asset verwendet wird, das sich am Zielort befindet, wird eine Warnmeldung angezeigt.

Sie können festlegen, ob ein vorhandenes Asset ersetzt, eine neue Version erstellt oder beide Assets beibehalten werden sollen, indem Sie das neue hochgeladene Asset umbenennen. Wenn Sie ein vorhandenes Asset ersetzen, werden die Metadaten für das Asset sowie alle zuvor vorgenommenen Änderungen (z. B. Anmerkungen, Zuschneiden usw.) gelöscht. If you choose to keep both assets, the new asset is renamed with the number `1` appended to its name.

>[!NOTE]
>
>When you select **[!UICONTROL Replace]** in the [!UICONTROL Name Conflict] dialog, the asset ID is regenerated for the new asset. Diese ID unterscheidet sich von der ID des vorherigen Assets.
>
>Wenn Asset Insights in Adobe Analytics zur Verfolgung von Impressionen/Klicks aktiviert ist, werden die für das Asset in Analytics erfassten Daten mit der neu generierten Asset-ID ungültig.

Um das Duplikat-Asset in AEM Assets beizubehalten, tippen/klicken Sie auf &quot; **[!UICONTROL Behalten]**&quot;. Um das hochgeladene Duplikat-Asset zu löschen, tippen/klicken Sie auf **[!UICONTROL Löschen]**.

### Behandlung von Dateinamen und verbotene Zeichen {#filename-handling}

AEM Assets verhindert, dass Sie Assets mit den verbotenen Zeichen in ihren Dateinamen hochladen. Wenn Sie versuchen, ein Asset mit einem Dateinamen mit einem nicht zulässigen Zeichen oder mehr hochzuladen, zeigt AEM Assets eine Warnmeldung an und stoppt den Upload, bis Sie diese Zeichen entfernen oder mit einem zulässigen Namen hochladen.

To suit specific file naming conventions for your organization, the [!UICONTROL Upload Assets] dialog lets you specify long names for the files that you upload.

Allerdings werden die folgenden Zeichen (in der Liste durch Leerzeichen getrennt) nicht unterstützt:

* asset file name must not contain `* / : [ \\ ] | # % { } ? &`
* asset folder name must not contain `* / : [ \\ ] | # % { } ? \" . ^ ; + & \t`

## Bulk upload of assets {#bulk-upload}

Um eine größere Anzahl von Dateien hochzuladen, insbesondere wenn diese in einer verschachtelten Ordnerhierarchie auf dem Datenträger vorhanden sind, können die folgenden Vorgehensweisen verwendet werden:

* Verwenden Sie ein benutzerdefiniertes Upload-Skript oder -Tool, das [Asset-Upload-APIs](developer-reference-material-apis.md#asset-upload-technical)nutzt. Ein solches benutzerdefiniertes Tool kann bei Bedarf zusätzliche Verarbeitungsschritte für Assets hinzufügen (z. B. Metadaten übersetzen oder Dateien umbenennen).
* Verwenden Sie die [Experience Manager-Desktop-App](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html) , um verschachtelte Ordnerhierarchien hochzuladen.

> [!NOTE]
>
> Für das Hochladen von Massen als Teil der Inhaltsmigration von anderen Systemen bei der Einrichtung und Bereitstellung in Experience Manager ist eine sorgfältige Planung, Prüfung und Auswahl der Werkzeuge erforderlich. Anleitungen zu Ansätzen zur Inhaltsmigration finden Sie im [Implementierungshandbuch](/help/implementing/deploying/overview.md) .

## Hochladen von Assets mit Desktop-Clients {#upload-assets-desktop-clients}

Zusätzlich zur Webbrowser-Benutzeroberfläche unterstützt Experience Manager auch andere Clients auf dem Desktop. Sie bieten außerdem ein Upload-Erlebnis, ohne dass Sie zum Webbrowser wechseln müssen.

* [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) bietet Zugriff auf Assets aus AEM in Adobe Fotoshop-, Adobe Illustrator- und Adobe InDesign-Desktopanwendungen. Sie können das derzeit geöffnete Dokument direkt von der Benutzeroberfläche von Adobe Asset Link aus in diese Desktop-Anwendungen hochladen.
* [Die Experience Manager-Desktop-App](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html) vereinfacht die Arbeit mit Assets auf dem Desktop, unabhängig vom Dateityp oder der nativen Anwendung, in der sie verarbeitet werden. Es ist besonders nützlich, Dateien in verschachtelten Ordnerhierarchien aus Ihrem lokalen Dateisystem hochzuladen, da der Browser-Upload nur das Hochladen von Listen mit einfachen Dateien unterstützt.

## Zusätzliche Verarbeitung {#additional-processing}

Um eine zusätzliche Verarbeitung der hochgeladenen Assets durchzuführen, können Sie die Asset-Verarbeitungs-Profil-Profil im Ordner verwenden, in die Assets hochgeladen werden. Sie sind im Dialogfeld **[!UICONTROL Eigenschaften]** des Ordners verfügbar.

![assets-folder-properties](assets/assets-folder-properties.png)

Die folgenden Profile stehen zur Verfügung:

* [Mit Metadaten-Profilen](metadata-profiles.md) können Sie standardmäßige Metadateneigenschaften auf in diesen Ordner hochgeladene Assets anwenden
* [Mit Profilen](asset-microservices-configure-and-use.md#processing-profiles) zur Verarbeitung können Sie die Darstellungsverarbeitung anwenden und neben den Standarddarstellungen auch Darstellungen generieren.

Wenn in Ihrer Umgebung zusätzlich Dynamic Media aktiviert ist:

* Mit [Bildprofilen](dynamic-media/image-profiles.md) können Sie bestimmte Zuschneidefunktionen (**[!UICONTROL Smart Cropping]** und Pixelzuschnitt) sowie Scharfzeichnungskonfigurationen auf die hochgeladenen Assets anwenden.
* [Mit Video-Profilen](dynamic-media/video-profiles.md) können Sie bestimmte Videokodierungs-Profil (Auflösung, Format, Parameter) anwenden

> [!NOTE]
>
> Das Zuschneiden von dynamischen Medien und andere Vorgänge auf Assets sind nicht destruktiv, d. h. sie ändern nicht das hochgeladene Original, sondern stellen Parameter für das Zuschneiden oder die Medientransformation bereit, die bei der Bereitstellung der Assets durchgeführt werden müssen.

Für Ordner mit zugewiesenem Verarbeitungsprofil wird der Profilname in der Miniaturansicht der Kartenansicht angezeigt. In der Listenansicht wird der Profilname in der Spalte **[!UICONTROL Verarbeitungsprofil]** angezeigt.

## Hochladen oder Erfassen von Assets mit APIs {#upload-using-apis}

Technische Details zu den Upload-APIs und dem Protokoll sowie Links zu Open-Source-SDK- und Beispielclients finden Sie im Abschnitt zum [Hochladen](developer-reference-material-apis.md#asset-upload-technical) von Assets in der Developer-Referenz.

>[!MORELIKETHIS]
>
>* [Adobe Experience Manager-Desktop-Programm](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/introduction.html)
>* [Adobe Asset Link](https://www.adobe.com/creativecloud/business/enterprise/adobe-asset-link.html)
>* [Dokumentation zu Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html)
>* [Technische Referenz zum Hochladen von Assets](developer-reference-material-apis.md#asset-upload-technical)

