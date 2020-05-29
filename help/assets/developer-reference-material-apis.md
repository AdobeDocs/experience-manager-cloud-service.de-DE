---
title: 'Assets-APIs für Digital Asset Management in Adobe Experience Manager as a Cloud Service '
description: Asset-APIs ermöglichen grundlegende CRUD-Operationen (Create-Read-Update-Delete – Erstellen-Lesen-Aktualisieren-Löschen) zur Verwaltung von Assets, einschließlich Binär- und Metadaten, Ausgabeformaten, Kommentaren und Inhaltsfragmenten.
contentOwner: AG
translation-type: ht
source-git-commit: 27e72bbc0d852eb2c2eb059967c91e6108613965
workflow-type: ht
source-wordcount: '0'
ht-degree: 100%

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
Den Client-Code, der diesen Ansatz implementiert, können Sie in der Open-Source-Bibliothek [aem-upload](https://github.com/adobe/aem-upload) einsehen.

### Initiieren des Uploads {#initiate-upload}

Der erste Schritt besteht darin, eine HTTP-POST-Anfrage an den Ordner zu senden, in dem das Asset erstellt oder aktualisiert werden soll. Schließen Sie den Selektor `.initiateUpload.json` ein, um anzugeben, dass die Anfrage darin besteht, einen binären Upload zu starten. Der Pfad zum Ordner, in dem das Asset erstellt werden soll, lautet beispielsweise `/assets/folder`:

```
POST https://[aem_server]/content/dam/assets/folder.initiateUpload.json
```

Der Content-Typ des Anfragetexts sollte `application/x-www-form-urlencoded`-Formulardaten sein, die die folgenden Felder enthalten:

* `(string) fileName`: Erforderlich. Der Name des Assets, wie er in der Instanz angezeigt wird.
* `(number) fileSize`: Erforderlich. Die Gesamtlänge der hochzuladenden Binärdatei in Byte.

Eine einzige Anfrage kann dazu verwendet werden, Uploads für mehrere Binärdateien zu initiieren, solange jede Binärdatei die erforderlichen Felder enthält. Bei Erfolg wird die Anfrage mit einem `201`-Status-Code und einem Text mit JSON-Daten im folgenden Format beantwortet:

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

* `completeURI` (Zeichenfolge): Diese URI aufrufen, wenn das Hochladen der Binärdatei abgeschlossen ist. Die URI kann eine absolute oder relative URI sein. Clients sollten in der Lage sein, beide Fälle zu handhaben. Das heißt, dass der Wert `"https://author.acme.com/content/dam.completeUpload.json"` oder `"/content/dam.completeUpload.json"` sein kann. Siehe [Abschließen des Hochladens ](#complete-upload).
* `folderPath` (Zeichenfolge): Vollständiger Pfad zum Ordner, in den die Binärdatei hochgeladen wird.
* `(files)` (Array): Eine Liste der Elemente, deren Länge und Reihenfolge mit der Länge und Reihenfolge der Liste der binären Informationen übereinstimmen, die in der Anfrage zum Initiieren bereitgestellt werden.
* `fileName` (Zeichenfolge): Der Name der entsprechenden Binärdatei, wie in der Anfrage zum Initiieren angegeben. Dieser Wert sollte in der vollständigen Anfrage enthalten sein.
* `mimeType` (Zeichenfolge): Der Mime-Typ der entsprechenden Binärdatei, wie in der Initiierungsanforderung angegeben. Dieser Wert sollte in der vollständigen Anfrage enthalten sein.
* `uploadToken` (Zeichenfolge): Ein Upload-Token für die entsprechende Binärdatei. Dieser Wert sollte in der vollständigen Anfrage enthalten sein.
* `uploadURIs` (Array): Eine Liste der Zeichenfolgen, deren Werte vollständige URIs sind, in die der binäre Inhalt hochgeladen werden soll (siehe [Hochladen der Binärdatei](#upload-binary)).
* `minPartSize` (Zahl): Die Mindestlänge (in Bytes) der Daten, die für einen der Upload-URIs bereitgestellt werden können, wenn mehr als ein URI vorhanden ist.
* `maxPartSize` (Zahl): Die maximale Länge (in Bytes) der Daten, die für einen der Upload-URIs bereitgestellt werden können, wenn mehr als ein URI vorhanden ist.

### Hochladen der Binärdatei {#upload-binary}

Die Ausgabe beim Initiieren eines Uploads umfasst einen oder mehrere Upload-URI-Werte. Wenn mehr als eine URI angegeben wird, ist es die Verantwortung des Clients, die Binärdatei in Teile zu „teilen“ und jeden Teil in der richtigen Reihenfolge zu den URIs zu posten. Alle URIs müssen verwendet werden. Jeder Teil muss größer als die Mindestgröße und kleiner als die maximale Größe sein, wie in der Initiierungsantwort angegeben. Diese Anfragen werden von CDN-Edge-Knoten unterstützt, um das Hochladen von Binärdateien zu beschleunigen.

Eine Möglichkeit, dies zu erreichen, besteht darin, die Teilegröße basierend auf der Anzahl der von der API bereitgestellten Upload-URIs zu berechnen. Beispiel unter der Annahme, dass die Gesamtgröße der Binärdatei 20.000 Bytes und die Anzahl der Upload-URIs 2 beträgt:

* Berechnen Sie die Teilegröße, indem Sie die Gesamtgröße durch die Anzahl der URIs teilen: 20.000 / 2 = 10.000
* POST-Byte-Bereich 0-9.999 der Binärdatei zur ersten URI in der Liste der Upload-URIs
* POST-Byte-Bereich 10.000-19.999 der Binärdatei zum zweiten URI in der Liste der Upload-URIs

Bei erfolgreicher Ausführung antwortet der Server auf jede Anfrage mit Status-Code `201`.

### Abschließen des Hochladens {#complete-upload}

Nachdem alle Teile einer Binärdatei hochgeladen wurden, senden Sie eine HTTP-POST-Anfrage an den vollständigen URI, der von den Initiierungsdaten bereitgestellt wird. Der Content-Typ des Anfragetexts sollte `application/x-www-form-urlencoded`-Formulardaten sein, die die folgenden Felder enthalten.

| Felder | Typ | Erforderlich | Beschreibung |
|---|---|---|---|
| `fileName` | Zeichenfolge | Erforderlich | Der Name des Assets, wie in den Initiierungsdaten angegeben. |
| `mimeType` | Zeichenfolge | Erforderlich | Der HTTP-Content-Typ der Binärdatei, wie in den Initiierungsdaten angegeben. |
| `uploadToken` | Zeichenfolge | Erforderlich | Upload-Token für die Binärdatei, wie in den Initiierungsdaten angegeben. |
| `createVersion` | Boolesch | Optional | Wenn `True` und ein Asset mit dem angegebenen Namen bereits existiert, erstellt die Instanz eine neue Version des Assets. |
| `versionLabel` | Zeichenfolge | Optional | Wenn eine neue Version erstellt wird, die Bezeichnung, die der neuen Version eines Assets zugeordnet ist. |
| `versionComment` | Zeichenfolge | Optional | Wenn eine neue Version erstellt wird, die Kommentare, die der Version zugeordnet sind. |
| `replace` | Boolesch | Optional | Wenn `True` und ein Asset mit dem angegebenen Namen bereits existiert, löscht Experience Manager das Asset und erstellt es dann erneut. |

>!![NOTE]
>
> Wenn das Asset bereits existiert und weder `createVersion` noch `replace` angegeben ist, aktualisiert Experience Manager die aktuelle Version des Assets mit der neuen Binärdatei.

Wie beim Initiierungsprozess können die vollständigen Anfragedaten Informationen zu mehr als einer Datei enthalten.

Das Hochladen einer Binärdatei wird erst durchgeführt, wenn die vollständige URL für die Datei aufgerufen wurde. Selbst wenn die Binärdatei einer Datei vollständig hochgeladen wird, wird das Asset erst nach Abschluss des Upload-Vorgangs von der Instanz verarbeitet.

Bei erfolgreicher Ausführung antwortet der Server mit Status-Code `200`.

### Open-Source-Upload-Bibliothek {#open-source-upload-library}

Um mehr über die Upload-Algorithmen zu erfahren oder eigene Upload-Skripte und -Tools zu erstellen, stellt Adobe Open-Source-Bibliotheken und -Tools als Ausgangspunkt bereit:

* [Open-Source-AEM-Upload-Bibliothek](https://github.com/adobe/aem-upload)
* [Open-Source-Befehlszeilen-Tool](https://github.com/adobe/aio-cli-plugin-aem)

### Veraltete APIs zum Hochladen von Assets {#deprecated-asset-upload-api}

<!-- #ENGCHECK review / update the list of deprecated APIs below. -->

Für Adobe Experience Manager as a Cloud Service werden nur die neuen Upload-APIs unterstützt. Die APIs aus Adobe Experience Manager 6.5 werden nicht mehr unterstützt. Die Methoden im Zusammenhang mit dem Hochladen oder Aktualisieren von Assets oder Ausgabeformaten (alle binären Uploads) werden in den folgenden APIs nicht mehr unterstützt:

* [AEM Assets-HTTP-API](mac-api-assets.md)
* `AssetManager` Java-API, z. B. `AssetManager.createAsset(..)`

>[!MORELIKETHIS]
* [Open-Source-AEM-Upload-Bibliothek](https://github.com/adobe/aem-upload).
* [Open-Source-Befehlszeilen-Tool](https://github.com/adobe/aio-cli-plugin-aem).


## Asset-Verarbeitungs- und Nachbearbeitungs-Workflows {#post-processing-workflows}

In Experience Manager basiert die Asset-Verarbeitung auf der Konfiguration von **[!UICONTROL Verarbeitungsprofilen]**, die [Asset-Microservices](asset-microservices-configure-and-use.md#get-started-using-asset-microservices) verwendet. Für die Verarbeitung sind keine Entwicklererweiterungen erforderlich.

Verwenden Sie die standardmäßigen Workflows mit Erweiterungen mit benutzerdefinierten Schritten für die Konfiguration des Nachbearbeitungs-Workflows.

## Unterstützung von Workflow-Schritten im Nachbearbeitungs-Workflow {#post-processing-workflows-steps}

Kunden, die von früheren Versionen auf Experience Manager as a Cloud Service aktualisieren, können Asset-Microservices für die Verarbeitung von Assets verwenden. Die Cloud-nativen Asset-Microservices sind bedeutend einfacher zu konfigurieren und zu verwenden. Einige Workflow-Schritte, die im [!UICONTROL DAM-Update-Asset]-Workflow in der vorherigen Version verwendet wurden, werden nicht unterstützt.

Die folgenden Workflow-Schritte werden in Experience Manager as a Cloud Service unterstützt.

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
