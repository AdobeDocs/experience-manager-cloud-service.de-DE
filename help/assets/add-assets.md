---
title: Hinzufügen digitaler Assets zu Adobe Experience Manager
description: Hinzufügen digitaler Assets zu Adobe Experience Manager as a Cloud Service
translation-type: ht
source-git-commit: 114bc678fc1c6e3570d6d2a29bc034feb68aa56d

---


# Hinzufügen digitaler Assets zu Adobe Experience Manager {#add-assets-to-experience-manager}

In Adobe Experience Manager wird der binäre Inhalt der hochgeladenen digitalen Dateien mit Rich-Metadaten, Smart-Tags, Ausgabeformaten und anderen DAM (Digital Asset Management)-Diensten erweitert. Sie können verschiedene Arten von Dateien (z. B. Bilder, Dokumente und Raw-Dateien) von Ihrem lokalen Ordner oder Netzlaufwerk in Experience Manager Assets hochladen.

Es steht eine Reihe von Upload-Methoden zur Verfügung. Neben dem am häufigsten verwendeten Browserupload gibt es noch weitere Methoden zum Hinzufügen von Assets zum Experience Manager-Repository, einschließlich Desktop-Clients wie Adobe Asset Link oder Experience Manager-Desktop-Programm, Upload- und Erfassungsskripte, die Kunden erstellen, und automatisierte Erfassungsintegrationen, die als AEM-Erweiterungen hinzugefügt werden.

Wir werden uns hier auf die Upload-Methoden für Endbenutzer konzentrieren und Links zu Artikeln bereitstellen, die technische Aspekte des Hochladens und der Erfassung von Assets mithilfe von Experience Manager-APIs und SDKs beschreiben.

Sie können zwar jede beliebige Binärdatei in Experience Manager hochladen und verwalten, aber die am häufigsten verwendeten Dateiformate bieten Unterstützung für zusätzliche Dienste, wie z. B. die Extraktion von Metadaten oder die Vorschau/Ausgabegenerierung. Weitere Informationen finden Sie unter [Unterstützte Dateiformate](file-format-support.md).

Sie können sich auch dafür entscheiden, die hochgeladenen Assets zusätzlich zu bearbeiten. Für den Ordner, in den die Assets hochgeladen werden, kann eine Reihe von Asset-Verarbeitungsprofilen konfiguriert werden, um spezifische Metadaten, Ausgabeformate oder Bildbearbeitungsdienste hinzuzufügen. Weitere Informationen finden Sie unten unter [Zusätzliche Verarbeitung](#additional-processing).

>[!NOTE]
>
> Experience Manager as a Cloud Service nutzt eine neue Methode zum Hochladen von Assets: das direkte binäre Hochladen. Sie wird standardmäßig von den vordefinierten Produktfunktionen und Clients wie AEM-Benutzeroberfläche, Adobe Asset Link, AEM-Desktop-Programm und somit für die Endbenutzer transparent unterstützt.
>
> Uploadcode, der von den technischen Teams des Kunden angepasst oder erweitert wird, muss die neuen Upload-APIs und Protokolle verwenden.

## Hochladen von Assets {#upload-assets}

Um eine Datei (oder mehrere Dateien) hochzuladen, können Sie diese auf Ihrem Desktop auswählen und per Drag-and-Drop in der Benutzeroberfläche (Webbrowser) in den Zielordner ziehen. Sie können den Upload auch über die Benutzeroberfläche starten.

1. Navigieren Sie in der Assets-Benutzeroberfläche zu dem Speicherort, an dem Sie digitale Assets hinzufügen möchten.
1. Führen Sie einen der folgenden Schritte aus, um die Assets hochzuladen:

   * Tippen Sie in der Symbolleiste auf das Symbol **[!UICONTROL Erstellen]**. Tippen Sie dann im Menü auf **[!UICONTROL Dateien]**. Sie können die Datei im angezeigten Dialogfeld bei Bedarf umbenennen.
   * Ziehen Sie die Assets in einem Browser, der HTML5 unterstützt, direkt auf die Assets-Benutzeroberfläche. Das Dialogfeld zum Umbenennen der Datei wird nicht angezeigt.
   ![create_menu](assets/create_menu.png)

   Wenn Sie die Assets im Dialogfeld für die Dateiauswahl bei gedrückter Strg-/Befehlstaste markieren, können Sie mehrere Dateien auswählen. Bei Verwendung eines iPads können Sie jeweils nur eine Datei auswählen.

<!-- #ENGCHECK do we support pausing? I couldn't get pause to show with 1.5GB upload.... If not, this should be removed#

   You can pause the uploading of large assets (greater than 500 MB) and resume it later from the same page. Tap the **[!UICONTROL Pause]** icon beside progress bar that appears when an upload starts.

   ![chlimage_1-211](assets/chlimage_1-211.png)

   The size above which an asset is considered a large asset is configurable. For example, you can configure the system to consider assets above 1000 MB (instead of 500 MB) as large assets. In this case, **[!UICONTROL Pause]** appears on the progress bar when assets of size greater than 1000 MB are uploaded.

   The Pause button does not show if a file greater than 1000 MB is uploaded with a file less than 1000 MB. However, if you cancel the less than 1000 MB file upload, the **[!UICONTROL Pause]** button appears.

   To modify the size limit, configure the `chunkUploadMinFileSize` property of the `fileupload`node in the CRX repository.

   When you click the **[!UICONTROL Pause]** icon, it toggles to a **[!UICONTROL Play]** icon. To resume uploading, click the **[!UICONTROL Play]** icon.

   ![chlimage_1-212](assets/chlimage_1-212.png)
-->

1. Um einen laufenden Upload abzubrechen, klicken Sie auf „Schließen“ (`X`) neben der Fortschrittsleiste. Wenn Sie den Upload abbrechen, löscht AEM Assets den teilweise hochgeladenen Teil des Assets.

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

>[!NOTE]
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

### Handhabung von Uploads, wenn das Asset bereits vorhanden ist {#handling-upload-existing-file}

Wenn Sie ein Asset unter einem Namen hochladen, der bereits für ein Asset verwendet wird, das sich am Zielort befindet, wird eine Warnmeldung angezeigt.

Sie können festlegen, ob ein vorhandenes Asset ersetzt, eine neue Version erstellt oder beide Assets beibehalten werden sollen, indem Sie das neue hochgeladene Asset umbenennen. Wenn Sie ein vorhandenes Asset ersetzen, werden die Metadaten für das Asset und sämtliche vorherigen Änderungen daran (z. B. Anmerkungen, Zuschnitte usw.) gelöscht. Wenn Sie sich dafür entscheiden, beide Assets zu behalten, wird das neue Asset umbenannt und die Ziffer `1` an den Namen angehängt.

>[!NOTE]
>
>Wenn Sie im Dialogfeld [!UICONTROL Namenskonflikt] die Option **[!UICONTROL Ersetzen]** auswählen, wird die Asset-ID für das neue Asset neu generiert. Diese ID unterscheidet sich von der ID des vorherigen Assets.
>
>Wenn Asset Insights zur Verfolgung von Impressions/Klicks mit Adobe Analytics aktiviert ist, werden die für das Asset in Analytics erfassten Daten durch die erneut generierte Asset-ID ungültig.

Tippen oder klicken Sie auf **[!UICONTROL Behalten]**, um das doppelte Asset in AEM Assets beizubehalten. Tippen oder klicken Sie auf **[!UICONTROL Löschen]**, um das doppelte Asset zu löschen, das Sie gerade hochgeladen haben.

### Behandlung von Dateinamen und unzulässige Zeichen {#filename-handling}

AEM Assets verhindert, dass Sie Assets hochladen, deren Dateinamen unzulässige Zeichen enthalten. Wenn Sie versuchen, ein Asset mit einem Dateinamen mit einem oder mehreren nicht zulässigen Zeichen hochzuladen, zeigt AEM Assets eine Warnmeldung an und stoppt den Upload, bis Sie diese Zeichen entfernen oder mit einem zulässigen Namen hochladen.

Um bestimmte Dateibenennungskonventionen für Ihre Organisation einzuhalten, können Sie im Dialogfeld [!UICONTROL Assets hochladen] lange Namen für die Dateien angeben, die Sie hochladen möchten.

Allerdings werden die folgenden Zeichen (in der Liste durch Leerzeichen getrennt) nicht unterstützt:

* Der Asset-Dateiname darf nicht enthalten: `* / : [ \\ ] | # % { } ? &`
* Der Asset-Ordnername darf nicht enthalten: `* / : [ \\ ] | # % { } ? \" . ^ ; + & \t`

## Massen-Upload von Assets {#bulk-upload}

Um eine größere Anzahl von Dateien hochzuladen, insbesondere wenn diese in einer verschachtelten Ordnerhierarchie auf dem Datenträger vorhanden sind, können die folgenden Vorgehensweisen verwendet werden:

* Verwenden Sie ein benutzerdefiniertes Upload-Skript oder -Tool, das [Asset-Upload-APIs](developer-reference-material-apis.md#asset-upload-technical) nutzt. Ein solches benutzerdefiniertes Tool kann bei Bedarf zusätzliche Verarbeitungsschritte für Assets hinzufügen (z. B. Metadaten übersetzen oder Dateien umbenennen).
* Verwenden Sie das [Experience Manager-Desktop-Programm](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html), um verschachtelte Ordnerhierarchien hochzuladen.

>[!NOTE]
>
> Der Massen-Upload als Teil der Migration von Inhalten aus anderen Systemen bei der Einrichtung und Bereitstellung in Experience Manager erfordert eine sorgfältige Planung, Abwägung und Auswahl der Tools. Anleitungen zu den Ansätzen zur Inhaltsmigration finden Sie im [Implementierungshandbuch](/help/implementing/deploying/overview.md).

## Hochladen von Assets mit Desktop-Clients {#upload-assets-desktop-clients}

Zusätzlich zur Webbrowser-Benutzeroberfläche unterstützt Experience Manager auch andere Clients auf dem Desktop. Sie bieten außerdem ein Upload-Erlebnis, ohne dass der Browser aufgerufen werden muss.

* [Adobe Asset Link](https://helpx.adobe.com/de/enterprise/using/adobe-asset-link.html) bietet den Zugriff auf Assets aus AEM in Adobe Photoshop-, Adobe Illustrator- und Adobe InDesign-Desktop-Anwendungen. Sie können das derzeit geöffnete Dokument direkt von der Benutzeroberfläche von Adobe Asset Link in diesen Desktop-Anwendungen zu AEM hochladen.
* Das [Experience Manager-Desktop-Programm](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html) vereinfacht die Arbeit mit Assets auf dem Desktop, unabhängig vom Dateityp oder der nativen Anwendung, die diese verarbeitet. Es ist besonders nützlich, um Dateien in verschachtelten Ordnerhierarchien aus Ihrem lokalen Dateisystem hochzuladen, da der Browserupload nur das Hochladen flacher Dateilisten unterstützt.

## Zusätzliche Verarbeitung {#additional-processing}

Um eine zusätzliche Verarbeitung der hochgeladenen Assets zu ermöglichen, können Sie die Verarbeitungsprofile von Assets im Ordner verwenden, in den die Assets hochgeladen werden. Sie sind im Dialogfeld **[!UICONTROL Eigenschaften]** des Ordners verfügbar.

![assets-folder-properties](assets/assets-folder-properties.png)

Die folgenden Profile sind verfügbar:

* Mit [Metadatenprofilen](metadata-profiles.md) können Sie Standardeigenschaften für Metadaten auf Assets anwenden, die in diesen Ordner hochgeladen wurden.
* Mit [Verarbeitungsprofilen](asset-microservices-configure-and-use.md#processing-profiles) können Sie neben den Standarddarstellungen auch die Darstellungsverarbeitung anwenden und Ausgabeformate generieren

Wenn Dynamic Media in Ihrer Umgebung aktiviert ist:

* Mit [Bildprofilen](dynamic-media/image-profiles.md) können Sie bestimmte Zuschneidefunktionen (**[!UICONTROL Smarter Zuschnitt]** und Pixelzuschnitt) und Scharfzeichnungskonfigurationen auf die hochgeladenen Assets anwenden.
* Mit [Videoprofilen](dynamic-media/video-profiles.md) können Sie bestimmte Videokodierungsprofile (Auflösung, Format, Parameter) anwenden.

>[!NOTE]
>
> Das von Dynamic Media unterstützte Zuschneiden und andere Operationen an Assets sind zerstörungsfrei, d. h. sie ändern nicht das hochgeladene Original, sondern stellen Parameter für das Zuschneiden oder die Medientransformation bereit, die bei der Bereitstellung der Assets durchgeführt werden müssen.

Für Ordner mit zugewiesenem Verarbeitungsprofil wird der Profilname in der Miniaturansicht der Kartenansicht angezeigt. In der Listenansicht wird der Profilname in der Spalte **[!UICONTROL Verarbeitungsprofil]** angezeigt.

## Hochladen oder Aufnehmen von Assets mit APIs {#upload-using-apis}

Technische Details zu den Upload-APIs und dem Protokoll sowie Links zu Open-Source-SDK und Beispiel-Clients finden Sie im Abschnitt zum [Asset-Upload](developer-reference-material-apis.md#asset-upload-technical) in der Entwicklerreferenz.

>[!MORELIKETHIS]
>
>* [Adobe Experience Manager-Desktop-Programm](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/introduction.html)
>* [Adobe Asset Link](https://www.adobe.com/de/creativecloud/business/enterprise/adobe-asset-link.html)
>* [Adobe Asset Link-Dokumentation](https://helpx.adobe.com/de/enterprise/using/adobe-asset-link.html)
>* [Technische Referenz zum Asset-Upload](developer-reference-material-apis.md#asset-upload-technical)

