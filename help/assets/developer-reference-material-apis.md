---
title: 'Assets-APIs für Digital Asset Management in Adobe Experience Manager as a Cloud Service '
description: Asset-APIs ermöglichen grundlegende CRUD-Operationen (Create-Read-Update-Delete – Erstellen-Lesen-Aktualisieren-Löschen) zur Verwaltung von Assets, einschließlich Binär- und Metadaten, Ausgabeformaten, Kommentaren und Inhaltsfragmenten.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0686acbc61b3902c6c926eaa6424828db0a6421a

---


# Assets as a Cloud Service-APIs {#assets-cloud-service-apis}

<!-- 
Give a list of and overview of all reference information available.
* New upload method
* Javadocs
* Assets HTTP API documented at [https://helpx.adobe.com/experience-manager/6-5/assets/using/mac-api-assets.html](https://helpx.adobe.com/experience-manager/6-5/assets/using/mac-api-assets.html)

-->

## Asset-Upload {#asset-upload-technical}

Experience Manager as a Cloud Service bietet eine neue Möglichkeit zum Hochladen von Assets in das Repository – das direkte binäre Hochladen in einen binären Cloud-Speicher. In diesem Abschnitt wird ein technischer Überblick bereitgestellt.

### Übersicht über das direkte binäre Hochladen {#overview-binary-upload}

Der allgemeine Algorithmus zum Hochladen einer Binärdatei lautet:

1. Senden einer HTTP-Anfrage, die AEM über die Absicht informiert, eine neue Binärdatei hochzuladen.
1. Posten des Inhalts der Binärdatei an einen oder mehrere URIs, die von der Initiierungsanfrage bereitgestellt werden.
1. Senden einer HTTP-Anfrage, um den Server darüber zu informieren, dass der Inhalt der Binärdatei erfolgreich hochgeladen wurde.

![Übersicht über das direkte binäre Upload-Protokoll](assets/add-assets-technical.png)

Wichtige Unterschiede im Vergleich zu früheren Versionen von AEM sind unter anderem:

* Binärdateien durchlaufen nicht AEM, das jetzt lediglich den Upload-Prozess mit dem für die Bereitstellung konfigurierten binären Cloud-Speicher koordiniert
* Die binäre Cloud-Speicherung wird von einem CDN (Content Delivery Network, Edge Network) unterstützt, das den Upload-Endpunkt näher an den Client heranführt und so zur Verbesserung der Upload-Leistung und des Benutzererlebnisses beiträgt, insbesondere für verteilte Teams, die Assets hochladen

Dieser Ansatz sollte eine skalierbarere und leistungsfähigere Handhabung von Asset-Uploads bieten.

> !![NOTE]
To review client code that implements this approach, refer to the open-source [aem-upload library](https://github.com/adobe/aem-upload)

### Initiieren des Uploads {#initiate-upload}

Der erste Schritt besteht darin, eine HTTP-POST-Anfrage an den Ordner zu senden, in dem das Asset erstellt oder aktualisiert werden soll. Schließen Sie den Selektor `.initiateUpload.json` ein, um anzugeben, dass die Anfrage darin besteht, einen binären Upload zu starten. Der Pfad zum Ordner, in dem das Asset erstellt werden soll, lautet beispielsweise `/assets/folder`:

```
POST https://[aem_server]/content/dam/assets/folder.initiateUpload.json
````

Der Content-Typ des Anfragetexts sollte `application/x-www-form-urlencoded`-Formulardaten sein, die die folgenden Felder enthalten:

* `(string) fileName`: Erforderlich. Der Name des Assets, wie er in der Instanz angezeigt wird.
* `(number) fileSize`: Erforderlich. Die Gesamtlänge der hochzuladenden Binärdatei in Byte.

Eine einzelne Anforderung kann verwendet werden, um Uploads für mehrere Binärdateien zu starten, sofern jede Binärdatei die erforderlichen Felder enthält. If successful, the request responds with a `201` status code and a body containing JSON data in the following format:

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
```

* `completeURI` (Zeichenfolge): Rufen Sie diesen URI auf, wenn das Hochladen der Binärdatei abgeschlossen ist. Der URI kann ein absoluter oder relativer URI sein, und Clients sollten in der Lage sein, beides zu handhaben. Das heißt, der Wert kann `"https://author.acme.com/content/dam.completeUpload.json"` oder `"/content/dam.completeUpload.json"` Siehe [vollständiger Upload](#complete-upload)sein.
* `folderPath` (Zeichenfolge): Vollständiger Pfad zu dem Ordner, in den die Binärdatei hochgeladen wird.
* `(files)` (Array): Eine Liste von Elementen, deren Länge und Reihenfolge mit der Liste der binären Informationen übereinstimmen, die in der Initiierungsanforderung bereitgestellt werden.
* `fileName` (Zeichenfolge): Der Name der entsprechenden Binärdatei, wie er in der Anfrage zum Initiieren angegeben ist. Dieser Wert sollte in der vollständigen Anfrage enthalten sein.
* `mimeType` (Zeichenfolge): Der Mime-Typ der entsprechenden Binärdatei, wie in der In-Initiierungsanforderung angegeben. Dieser Wert sollte in der vollständigen Anfrage enthalten sein.
* `uploadToken` (Zeichenfolge): Ein Upload-Token für die entsprechende Binärdatei. Dieser Wert sollte in der vollständigen Anfrage enthalten sein.
* `uploadURIs` (Array): Eine Liste von Zeichenfolgen, deren Werte vollständige URIs sind, auf die der binäre Inhalt hochgeladen werden soll (siehe Binärdatei [hochladen](#upload-binary)).
* `minPartSize` (Nummer): Die Mindestlänge (in Byte) der Daten, die für einen der uploadURIs bereitgestellt werden können, wenn mehrere URIs vorhanden sind.
* `maxPartSize` (Nummer): Die maximale Länge (in Byte) von Daten, die für einen der uploadURIs bereitgestellt werden können, wenn mehrere URIs vorhanden sind.

### Hochladen der Binärdatei {#upload-binary}

Die Ausgabe beim Initiieren eines Uploads umfasst einen oder mehrere Upload-URI-Werte. Wenn mehr als eine URI angegeben wird, ist es die Verantwortung des Clients, die Binärdatei in Teile zu „teilen“ und jeden Teil in der richtigen Reihenfolge zu den URIs zu posten. Alle URIs müssen verwendet werden. Jeder Teil muss größer als die Mindestgröße und kleiner als die maximale Größe sein, wie in der Initiierungsantwort angegeben. Diese Anfragen werden von CDN-Edge-Knoten unterstützt, um das Hochladen von Binärdateien zu beschleunigen.

Eine Möglichkeit, dies zu erreichen, besteht darin, die Teilegröße basierend auf der Anzahl der von der API bereitgestellten Upload-URIs zu berechnen. Beispiel unter der Annahme, dass die Gesamtgröße der Binärdatei 20.000 Bytes und die Anzahl der Upload-URIs 2 beträgt:

* Berechnen Sie die Teilegröße, indem Sie die Gesamtgröße durch die Anzahl der URIs teilen: 20.000 / 2 = 10.000
* POST-Byte-Bereich 0-9.999 der Binärdatei zur ersten URI in der Liste der Upload-URIs
* POST-Byte-Bereich 10.000-19.999 der Binärdatei zur zweiten URI in der Liste der Upload-URIs

Bei erfolgreicher Ausführung antwortet der Server auf jede Anfrage mit Status-Code `201`.

### Abschließen des Hochladens {#complete-upload}

Nachdem alle Teile einer Binärdatei hochgeladen wurden, senden Sie eine HTTP POST-Anforderung an den vollständigen URI, der von den Initiierungsdaten bereitgestellt wird. Der Content-Typ des Anfragetexts sollte `application/x-www-form-urlencoded`-Formulardaten sein, die die folgenden Felder enthalten.

| Felder | Typ | Erforderlich oder nicht | Beschreibung |
|---|---|---|---|
| `fileName` | Zeichenfolge | Erforderlich | Der Name des Assets, wie in den Initiierungsdaten angegeben. |
| `mimeType` | Zeichenfolge | Erforderlich | Der HTTP-Content-Typ der Binärdatei, wie in den Initiierungsdaten angegeben. |
| `uploadToken` | Zeichenfolge | Erforderlich | Upload-Token für die Binärdatei, wie in den Initiierungsdaten angegeben. |
| `createVersion` | Boolesch | Optional | If `True` and an asset with the specified name already exists, then Experience Manager creates a new version of the asset. |
| `versionLabel` | Zeichenfolge | Optional | Wenn eine neue Version erstellt wird, die mit der neuen Version eines Assets verknüpfte Beschriftung . |
| `versionComment` | Zeichenfolge | Optional | Wenn eine neue Version erstellt wird, die mit der Version verknüpften Kommentare. |
| `replace` | Boolesch | Optional | Wenn `True` und ein Asset mit dem angegebenen Namen bereits vorhanden ist, löscht Experience Manager das Asset und erstellt es dann erneut. |

>!![NOTE]
>
> If the asset already exists and neither `createVersion` nor `replace` is specified, then Experience Manager updates the asset&#39;s current version with the new binary.

Wie beim Initiierungsprozess können die vollständigen Anfragedaten Informationen zu mehr als einer Datei enthalten.

Das Hochladen einer Binärdatei wird erst durchgeführt, wenn die vollständige URL für die Datei aufgerufen wurde. Selbst wenn die Binärdatei einer Datei vollständig hochgeladen wird, wird das Asset erst nach Abschluss des Upload-Vorgangs von der Instanz verarbeitet.

Bei erfolgreicher Ausführung antwortet der Server mit Status-Code `200`.

### Open-Source-Upload-Bibliothek {#open-source-upload-library}

Um mehr über die Upload-Algorithmen zu erfahren oder eigene Upload-Skripten und -Tools zu erstellen, stellt Adobe Open-Source-Bibliotheken und -Tools als Ausgangspunkt bereit:

* [Open-Source-Bibliothek für AEM-Upload](https://github.com/adobe/aem-upload)
* [Open-Source-Befehlszeilenwerkzeug](https://github.com/adobe/aio-cli-plugin-aem)

### Veraltete APIs zum Hochladen von Assets {#deprecated-asset-upload-api}

<!-- #ENGCHECK review / update the list of deprecated APIs below. -->

Für Adobe Experience Manager als Cloud-Dienst werden nur die neuen Upload-APIs unterstützt. Die APIs von Adobe Experience Manager 6.5 werden nicht mehr unterstützt. Die Methoden zum Hochladen oder Aktualisieren von Assets oder Darstellungen (binärer Upload) werden in den folgenden APIs nicht mehr unterstützt:

* [AEM Assets-HTTP-API](mac-api-assets.md)
* `AssetManager` Java-API, z. B. `AssetManager.createAsset(..)`

>[!MORELIKETHIS]
* [Open-Source-Bibliothek](https://github.com/adobe/aem-upload)zum Hochladen von AEM-Dateien.
* [Open-Source-Befehlszeilenwerkzeug](https://github.com/adobe/aio-cli-plugin-aem).


## Asset-Verarbeitungs- und Nachbearbeitungs-Workflows {#post-processing-workflows}

In Experience Manager basiert die Asset-Verarbeitung auf der **[!UICONTROL Verarbeitungskonfiguration für Profil]** , die [Asset-Mikrodienste](asset-microservices-configure-and-use.md#get-started-using-asset-microservices)verwendet. Für die Verarbeitung sind keine Entwicklererweiterungen erforderlich.

Für die Konfiguration des Arbeitsablaufs nach der Verarbeitung verwenden Sie die standardmäßige Workflows mit Erweiterungen mit benutzerdefinierten Schritten.

## Unterstützung von Workflow-Schritten im Arbeitsablauf nach der Verarbeitung {#post-processing-workflows-steps}

Kunden, die von früheren Versionen von Experience Manager auf Experience Manager als Cloud-Dienst aktualisieren, können Asset-Mikrodienste zur Verarbeitung von Assets verwenden. Die Cloud-nativen Asset-Mikrodienste sind viel einfacher zu konfigurieren und zu verwenden. Einige Workflow-Schritte, die in der vorherigen Version im Arbeitsablauf [!UICONTROL DAM Update Asset] verwendet wurden, werden nicht unterstützt.

Die folgenden Arbeitsablaufschritte werden in Experience Manager als Cloud-Dienst unterstützt.

* `com.day.cq.dam.similaritysearch.internal.workflow.process.AutoTagAssetProcess`
* `com.day.cq.dam.core.impl.process.CreateAssetLanguageCopyProcess`
* `com.day.cq.wcm.workflow.process.CreateVersionProcess`
* `com.day.cq.dam.similaritysearch.internal.workflow.smarttags.StartTrainingProcess`
* `com.day.cq.dam.similaritysearch.internal.workflow.smarttags.TransferTrainingDataProcess`
* `com.day.cq.dam.core.impl.process.TranslateAssetLanguageCopyProcess`
* `com.day.cq.dam.core.impl.process.UpdateAssetLanguageCopyProcess`
* `com.adobe.cq.workflow.replication.impl.ReplicationWorkflowProcess`
* `com.day.cq.dam.core.impl.process.DamUpdateAssetWorkflowCompletedProcess`

Die folgenden technischen Workflow-Modelle werden entweder durch Asset-Microservices ersetzt oder es ist kein Support verfügbar.

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
