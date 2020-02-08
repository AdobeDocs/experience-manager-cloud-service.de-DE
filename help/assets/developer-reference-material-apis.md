---
title: 'Assets-APIs für die Verwaltung digitaler Assets in Adobe Experience Manager als Cloud-Dienst '
description: Mithilfe von Assets-APIs können Sie grundlegende Vorgänge zum Erstellen, Lesen und Löschen (CRUD) zum Verwalten von Assets durchführen, einschließlich Binärdateien, Metadaten, Darstellungen, Kommentare und Inhaltsfragmenten.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# Assets als Cloud-Dienst-APIs {#assets-cloud-service-apis}

<!-- 
Give a list of and overview of all reference information available.
* New upload method
* Javadocs
* Assets HTTP API documented at [https://helpx.adobe.com/experience-manager/6-5/assets/using/mac-api-assets.html](https://helpx.adobe.com/experience-manager/6-5/assets/using/mac-api-assets.html)

-->

## Asset-Upload {#asset-upload-technical}

Experience Manager als Cloud-Dienst bietet eine neue Möglichkeit zum Hochladen von Assets in das Repository - direktes binäres Hochladen in binäre Cloud-Speicher. Dieser Abschnitt gibt einen technischen Überblick.

### Übersicht über das direkte binäre Hochladen {#overview-binary-upload}

Der allgemeine Algorithmus zum Hochladen einer Binärdatei lautet:

1. Senden Sie eine HTTP-Anforderung, die AEM über die Absicht informiert, eine neue Binärdatei hochzuladen.
1. POST den Inhalt der Binärdatei auf einen oder mehrere URIs, die von der Initiierungsanforderung bereitgestellt werden.
1. Senden Sie eine HTTP-Anforderung, um den Server darüber zu informieren, dass der Inhalt der Binärdatei erfolgreich hochgeladen wurde.

![Übersicht über das direkte Protokoll zum binären Hochladen](assets/add-assets-technical.png)

Wichtige Unterschiede zu früheren Versionen von AEM sind unter anderem:

* Binärdateien durchlaufen nicht AEM, das jetzt lediglich den Upload-Prozess mit dem für die Bereitstellung konfigurierten binären Cloud-Speicher koordiniert
* Die binäre Cloud-Speicherung wird von einem Content Delivery Network (CDN, Edge Network) vorgestellt, das den Upload-Endpunkt näher an den Client bringt und so die Upload-Leistung und Benutzerfreundlichkeit verbessert, insbesondere für verteilte Teams, die Assets hochladen, verbessert, insbesondere beim Hochladen von Assets durch verteilte Teams

Dieser Ansatz sollte eine skalierbarere und leistungsfähigere Handhabung von Asset-Uploads bieten.

> !![NOTE]
Informationen zum Überprüfen des Clientcodes, der diesen Ansatz implementiert, finden Sie in der Open-Source-Bibliothek [für AEM-Uploads](https://github.com/adobe/aem-upload)

### Hochladen starten {#initiate-upload}

Der erste Schritt besteht darin, eine HTTP POST-Anforderung an den Ordner zu senden, in dem das Asset erstellt oder aktualisiert werden soll. den Selektor einschließen, `.initiateUpload.json` um anzugeben, dass die Anforderung darin besteht, einen binären Upload zu starten. Der Pfad zum Ordner, in dem das Asset erstellt werden soll, lautet beispielsweise `/assets/folder`:

```
POST https://[aem_server]/content/dam/assets/folder.initiateUpload.json
````

Der Inhaltstyp des Anforderungstextes sollte `application/x-www-form-urlencoded` Formulardaten sein, die die folgenden Felder enthalten:

* `(string) fileName`: Erforderlich. Der Name des Assets, wie er in der Instanz angezeigt wird.
* `(number) fileSize`: Erforderlich. Die Gesamtlänge der hochzuladenden Binärdatei in Byte.

Beachten Sie, dass eine einzelne Anforderung zum Initiieren von Uploads für mehrere Binärdateien verwendet werden kann, sofern jede Binärdatei die erforderlichen Felder enthält.

Bei erfolgreichem Abschluss der Anforderung wird ein 201-Statuscode und ein Text mit JSON-Daten im folgenden Format angezeigt:

```
{
    "completeURI": "(string)",
    "folderPath": (string)",
    "files": [
        {
            "fileName": "(string)",
            "mimeType": "(string)",
            "uploadToken": "(string)",
            "uploadURIs": [
                "(string)"
            ]
        }
    ]
}
````

* `(string) completeURI`: Der URI, der aufgerufen werden sollte, wenn der Binärladevorgang abgeschlossen ist. Dies kann ein absoluter oder relativer URI sein, und Clients sollten in der Lage sein, beides zu handhaben. d. h. der Wert kann `"https://author.acme.com/content/dam.completeUpload.json"` oder `"/content/dam.completeUpload.json"` (siehe [Abschließen des Uploads](#complete-upload)) sein.
* `(string) folderPath`: Vollständiger Pfad zu dem Ordner, in den die Binärdatei hochgeladen wird.
* `(array) (files)`: Eine Liste der Elemente, deren Länge und Reihenfolge mit der Länge und Reihenfolge der Liste der binären Informationen übereinstimmen, die in der initiativen Anforderung bereitgestellt werden.
* `(string) fileName`: Der Name der entsprechenden Binärdatei, wie er in der Anfrage zum Initiieren angegeben ist. Dieser Wert sollte in der vollständigen Anforderung enthalten sein.
* `(string) mimeType`: Der Mime-Typ der entsprechenden Binärdatei, wie in der In-Initiierungsanforderung angegeben. Dieser Wert sollte in der vollständigen Anforderung enthalten sein.
* `(string) uploadToken`: Ein Upload-Token für die entsprechende Binärdatei. Dieser Wert sollte in der vollständigen Anforderung enthalten sein.
* `(array) uploadURIs`: Eine Liste der Zeichenfolgen, deren Werte vollständige URIs sind, auf die der binäre Inhalt hochgeladen werden soll (siehe Binärdatei [hochladen](#upload-binary)).
* `(number) minPartSize`: Die Mindestlänge (in Byte) der Daten, die für einen der uploadURIs bereitgestellt werden können, wenn mehrere URIs vorhanden sind.
* `(number) maxPartSize`: Die maximale Länge (in Byte) von Daten, die für einen der uploadURIs bereitgestellt werden können, wenn mehrere URIs vorhanden sind.

### Binärdatei hochladen {#upload-binary}

Die Ausgabe beim Initiieren eines Uploads umfasst einen oder mehrere Upload-URI-Werte. Wenn mehr als eine URI angegeben wird, ist es die Verantwortung des Clients, die Binärdatei in Teile zu &quot;teilen&quot; und POST jeden Teil, in der Reihenfolge, zu jedem URI, in der Reihenfolge. Es müssen alle URIs verwendet werden, und jedes Teil muss größer als die Mindestgröße und kleiner als die in der initiativen Antwort angegebene Maximalgröße sein. Diese Anforderungen werden von CDN-Edge-Knoten vorgestellt, um den Upload von Binärdateien zu beschleunigen.

Eine mögliche Möglichkeit hierfür ist die Berechnung der Bauteilgröße anhand der Anzahl der Upload-URIs, die von der API bereitgestellt werden. Beispiel unter der Annahme, dass die Gesamtgröße der Binärdatei 20.000 Byte und die Anzahl der Upload-URIs 2 beträgt:

* Berechnen Sie die Größe des Teils, indem Sie die Gesamtgröße durch die Anzahl der URIs teilen: 20.000 / 2 = 10.000
* POST-Bytebereich 0-9.999 der Binärdatei auf den ersten URI in der Liste der Upload-URIs
* POST-Bytebereich 10.000-19.999 der Binärdatei bis zum zweiten URI in der Liste der Upload-URIs

Bei erfolgreicher Ausführung antwortet der Server auf jede Anforderung mit einem `201` Statuscode.

### Hochladen {#complete-upload}

Sobald alle Teile einer Binärdatei hochgeladen wurden, besteht der letzte Schritt darin, eine HTTP POST-Anforderung an den vollständigen URI zu senden, der von den Initiierungsdaten bereitgestellt wird. Der Inhaltstyp des Anforderungstextes sollte Anwendungs-/`x-www-form-urlencoded` Formulardaten sein, die die folgenden Felder enthalten:

* `(string) fileName`: Erforderlich. Der Name des Assets, wie er in den Einleitungsdaten angegeben wurde.
* `(string) mimeType`: Erforderlich. Der HTTP-Inhaltstyp der Binärdatei, wie er von den Initiierungsdaten bereitgestellt wurde.
* `(string) uploadToken`: Erforderlich. Upload-Token für die Binärdatei, wie sie von den Initialisierungsdaten bereitgestellt wurde.
* `(bool) createVersion`: Optional. Wenn &quot;true&quot;und ein Asset mit dem angegebenen Namen bereits vorhanden ist, erstellt die Instanz eine neue Version des Assets.
* `(string) versionLabel`: Optional. Wenn eine neue Version erstellt wird, die Bezeichnung, die der Version zugeordnet wird.
* `(string) versionComment`: Optional. Wenn eine neue Version erstellt wird, Kommentare, die mit der Version verknüpft werden.
* `(bool) replace`: Optional: Wenn &quot;true&quot;und ein Asset mit dem angegebenen Namen bereits vorhanden ist, löscht die Instanz das Asset und erstellt es dann erneut.

>!![NOTE]
>
> Wenn das Asset bereits vorhanden ist und weder createVersion noch replace angegeben ist, aktualisiert die Instanz die aktuelle Version des Assets mit der neuen Binärdatei.

Wie beim Initiierungsprozess können die vollständigen Anforderungsdaten Informationen zu mehr als einer Datei enthalten.

Das Hochladen einer Binärdatei erfolgt erst, nachdem die vollständige URL für die Datei aufgerufen wurde. Selbst wenn die Binärdatei einer Datei vollständig hochgeladen wird, wird das Asset erst nach Abschluss des Upload-Vorgangs von der Instanz verarbeitet.

Bei erfolgreicher Ausführung antwortet der Server mit einem `200` Statuscode.

### Open-Source-Upload-Bibliothek {#open-source-upload-library}

Um mehr über die Upload-Algorithmen zu erfahren oder eigene Upload-Skripten und -Tools zu erstellen, stellt Adobe Open-Source-Bibliotheken und -Tools als Ausgangspunkt bereit:

* [Open-Source-Bibliothek für AEM-Uploads](https://github.com/adobe/aem-upload)
* [Open Source-Befehlszeilenwerkzeug](https://github.com/adobe/aio-cli-plugin-aem)

### Veraltete APIs zum Hochladen von Assets {#deprecated-asset-upload-api}

<!-- #ENGCHECK please review / update the list of deprecated APIs below -->

>[!NOTE]
Für Experience Manager als Cloud-Dienst werden nur die neuen Upload-APIs unterstützt. APIs aus Experience Manager 6.5 werden nicht mehr unterstützt.

Methoden zum Hochladen oder Aktualisieren von Assets oder Darstellungen (binärer Upload) werden in den folgenden APIs nicht mehr unterstützt:

* [AEM Assets HTTP API](mac-api-assets.md)
* `AssetManager` Java-API, z. B. `AssetManager.createAsset(..)`

>[!MORELIKETHIS]
* [Open-Source-Bibliothek für AEM-Uploads](https://github.com/adobe/aem-upload)
* [Open Source-Befehlszeilenwerkzeug](https://github.com/adobe/aio-cli-plugin-aem)


## Arbeitsabläufe für die Verarbeitung und Nachbearbeitung von Assets {#post-processing-workflows}

Die Verarbeitung der Assets erfolgt größtenteils auf der Grundlage der Konfiguration der **[!UICONTROL Verarbeitungsprofile]** durch [Asset-Mikrodienste](asset-microservices-configure-and-use.md#get-started-using-asset-microservices)und erfordert keine Entwicklererweiterungen.

Für die Konfiguration des Arbeitsablaufs nach der Verarbeitung können Sie standardmäßige AEM-Workflows mit Erweiterungen verwenden (z. B. können benutzerdefinierte Schritte verwendet werden). Lesen Sie den folgenden Unterabschnitt, um zu verstehen, welche Arbeitsablaufschritte in den Asset-Nachbearbeitungsabläufen verwendet werden können.

### Arbeitsablaufschritte im Arbeitsablauf nach der Verarbeitung {#post-processing-workflows-steps}

>[!NOTE]
Dieser Abschnitt betrifft hauptsächlich Kunden, die von früheren Versionen von AEM auf AEM als Cloud-Dienst aktualisieren.

Aufgrund eines neuen Bereitstellungsmodells, das mit Experience Manager als Cloud-Dienst eingeführt wurde, werden bestimmte Workflow-Schritte, die im Workflow vor der Einführung von Asset-Mikrodiensten verwendet werden, möglicherweise nicht mehr für Arbeitsabläufe nach der Verarbeitung unterstützt. `DAM Update Asset` Beachten Sie, dass die meisten von ihnen durch eine viel einfachere Konfiguration und Verwendung von Asset-Mikrodiensten ersetzt werden.

Im Folgenden finden Sie eine Liste mit Modellen für technische Arbeitsabläufe und deren Support in AEM als Cloud-Dienst:

### Unterstützte Workflow-Schritte {#supported-workflow-steps}

Die folgenden Arbeitsablaufschritte werden im Cloud-Dienst unterstützt.

* `com.day.cq.dam.similaritysearch.internal.workflow.process.AutoTagAssetProcess`
* `com.day.cq.dam.core.impl.process.CreateAssetLanguageCopyProcess`
* `com.day.cq.wcm.workflow.process.CreateVersionProcess`
* `com.day.cq.dam.similaritysearch.internal.workflow.smarttags.StartTrainingProcess`
* `com.day.cq.dam.similaritysearch.internal.workflow.smarttags.TransferTrainingDataProcess`
* `com.day.cq.dam.core.impl.process.TranslateAssetLanguageCopyProcess`
* `com.day.cq.dam.core.impl.process.UpdateAssetLanguageCopyProcess`
* `com.adobe.cq.workflow.replication.impl.ReplicationWorkflowProcess`
* `com.day.cq.dam.core.impl.process.DamUpdateAssetWorkflowCompletedProcess`

### Nicht unterstützte oder ersetzte Modelle {#unsupported-replaced-models}

Die folgenden Modelle des technischen Arbeitsablaufs werden entweder durch Asset-Mikrodienste ersetzt oder der Support ist nicht verfügbar.

* `com.day.cq.dam.core.impl.process.DamMetadataWritebackWorkflowCompletedProcess`
* `com.day.cq.dam.core.process.DeleteImagePreviewProcess`
* `com.day.cq.dam.s7dam.common.process.DMEncodeVideoWorkflowCompletedProcess`
* `com.day.cq.dam.core.process.GateKeeperProcess`
* `com.day.cq.dam.core.process.AssetOffloadingProcess`
* `com.day.cq.dam.core.process.MetadataProcessorProcess`
* `com.day.cq.dam.core.process.XMPWritebackProcess`
* `com.adobe.cq.dam.dm.process.workflow.DMImageProcess`
* `com.day.cq.dam.s7dam.common.process.S7VideoThumbnailProcess`
* `com.day.cq.dam.scene7.impl.process.Scene7UploadProcess`
* `com.day.cq.dam.s7dam.common.process.VideoProxyServiceProcess`
* `com.day.cq.dam.s7dam.common.process.VideoThumbnailDownloadProcess`
* `com.day.cq.dam.s7dam.common.process.VideoUserUploadedThumbnailProcess`
* `com.day.cq.dam.core.process.CreatePdfPreviewProcess`
* `com.day.cq.dam.core.process.CreateWebEnabledImageProcess`
* `com.day.cq.dam.video.FFMpegThumbnailProcess`
* `com.day.cq.dam.core.process.ThumbnailProcess`
* `com.day.cq.dam.cameraraw.process.CameraRawHandlingProcess`
* `com.day.cq.dam.core.process.CommandLineProcess`
* `com.day.cq.dam.pdfrasterizer.process.PdfRasterizerHandlingProcess`
* `com.day.cq.dam.core.process.AddPropertyWorkflowProcess`
* `com.day.cq.dam.core.process.CreateSubAssetsProcess`
* `com.day.cq.dam.core.process.DownloadAssetProcess`
* `com.day.cq.dam.word.process.ExtractImagesProcess`
* `com.day.cq.dam.word.process.ExtractPlainProcess`
* `com.day.cq.dam.video.FFMpegTranscodeProcess`
* `com.day.cq.dam.ids.impl.process.IDSJobProcess`
* `com.day.cq.dam.indd.process.INDDMediaExtractProcess`
* `com.day.cq.dam.indd.process.INDDPageExtractProcess`
* `com.day.cq.dam.core.impl.lightbox.LightboxUpdateAssetProcess`
* `com.day.cq.dam.pim.impl.sourcing.upload.process.ProductAssetsUploadProcess`
* `com.day.cq.dam.core.process.ScheduledPublishBPProcess`
* `com.day.cq.dam.core.process.ScheduledUnPublishBPProcess`
* `com.day.cq.dam.core.process.SendDownloadAssetEmailProcess`
* `com.day.cq.dam.core.impl.process.SendTransientWorkflowCompletedEmailProcess`

<!-- PPTX source: slide in add-assets.md - overview of direct binary upload section of 
https://adobe-my.sharepoint.com/personal/gklebus_adobe_com/_layouts/15/guestaccess.aspx?guestaccesstoken=jexDC5ZnepXSt6dTPciH66TzckS1BPEfdaZuSgHugL8%3D&docid=2_1ec37f0bd4cc74354b4f481cd420e07fc&rev=1&e=CdgElS
-->
