---
title: Entwicklerverweise für [!DNL Assets]
description: '[!DNL Assets] APIs and developer reference content lets you manage assets, including binary files, metadata, renditions, comments, and [!DNL Content Fragments].'
contentOwner: AG
translation-type: tm+mt
source-git-commit: 8b1cc8af67c6d12d7e222e12ac4ff77e32ec7e0e
workflow-type: tm+mt
source-wordcount: '1218'
ht-degree: 51%

---


# [!DNL Assets] APIs und Referenzmaterial für Entwickler {#assets-cloud-service-apis}

Der Artikel enthält Referenzmaterial und Ressourcen für Entwickler von [!DNL Assets] als Cloud Service. Es enthält eine neue Upload-Methode, API-Referenz und Informationen zur Unterstützung, die in der Workflows nach der Verarbeitung bereitgestellt wird.

## Asset-Upload {#asset-upload-technical}

[!DNL Experience Manager] als Cloud Service eine neue Methode zum Hochladen von Assets in das Repository bereitstellt. Die Benutzer können die Assets mit der HTTP-API direkt in die Cloud-Datenspeicherung hochladen. Die Schritte zum Hochladen einer Binärdatei sind:

1. [Senden Sie eine HTTP-Anforderung](#initiate-upload). Es informiert Sie [!DNL Experience Manage]bzw. die Bereitstellung Ihrer Absicht, eine neue Binärdatei hochzuladen.
1. [Posten des Inhalts der Binärdatei an einen oder mehrere URIs, die von der Initiierungsanfrage bereitgestellt werden.](#upload-binary)
1. [Senden einer HTTP-Anfrage, um den Server darüber zu informieren, dass der Inhalt der Binärdatei erfolgreich hochgeladen wurde.](#complete-upload)

![Übersicht über das direkte binäre Upload-Protokoll](assets/add-assets-technical.png)

Der Ansatz bietet eine skalierbare und leistungsfähigere Handhabung von Asset-Uploads. Die Unterschiede gegenüber [!DNL Experience Manager] 6.5 sind:

* Binaries do not go through [!DNL Experience Manager], which is now simply coordinating the upload process with the binary cloud storage configured for the deployment.
* Die Binary Cloud-Datenspeicherung funktioniert mit einem Content Versand Network (CDN) oder Edge-Netzwerk. Ein CDN wählt einen Upload-Endpunkt aus, der für einen Client näher liegt. Wenn Daten einen kürzeren Abstand zu einem nahe gelegenen Endpunkt zurücklegen, verbessern sich die Upload-Leistung und die Benutzerfreundlichkeit, insbesondere für geografisch verteilte Teams.

>[!NOTE]
>
>Siehe Clientcode zur Implementierung dieses Ansatzes in der Open-Source-Bibliothek [für AEM-Uploads](https://github.com/adobe/aem-upload).

### Initiieren des Uploads {#initiate-upload}

Senden Sie eine HTTP-POST an den gewünschten Ordner. Assets werden in diesem Ordner erstellt oder aktualisiert. Schließen Sie die Auswahl ein, `.initiateUpload.json` um anzugeben, dass die Anforderung darin besteht, den Upload einer Binärdatei zu starten. Der Pfad zum Ordner, in dem das Asset erstellt werden soll, lautet beispielsweise `/assets/folder`. Die POST wird angefordert `POST https://[aem_server]:[port]/content/dam/assets/folder.initiateUpload.json`.

Der Content-Typ des Anfragetexts sollte `application/x-www-form-urlencoded`-Formulardaten sein, die die folgenden Felder enthalten:

* `(string) fileName`: Erforderlich. Der Name des Assets, wie er in angezeigt wird [!DNL Experience Manager].
* `(number) fileSize`: Erforderlich. Die Dateigröße des hochgeladenen Assets in Byte.

Eine einzige Anfrage kann dazu verwendet werden, Uploads für mehrere Binärdateien zu initiieren, solange jede Binärdatei die erforderlichen Felder enthält. Bei Erfolg wird die Anfrage mit einem `201`-Status-Code und einem Text mit JSON-Daten im folgenden Format beantwortet:

```json
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

* `completeURI` (Zeichenfolge): Rufen Sie diesen URI auf, wenn das Hochladen der Binärdatei abgeschlossen ist. Die URI kann eine absolute oder relative URI sein. Clients sollten in der Lage sein, beide Fälle zu handhaben. Das heißt, dass der Wert `"https://author.acme.com/content/dam.completeUpload.json"` oder `"/content/dam.completeUpload.json"` sein kann. Siehe [Abschließen des Hochladens ](#complete-upload).
* `folderPath` (Zeichenfolge): Vollständiger Pfad zum Ordner, in den die Binärdatei hochgeladen wird.
* `(files)` (Array): Eine Liste von Elementen, deren Länge und Reihenfolge mit der Liste der binären Informationen übereinstimmen, die in der Initiierungsanforderung bereitgestellt werden.
* `fileName` (Zeichenfolge): Der Name der entsprechenden Binärdatei, wie in der Anfrage zum Initiieren angegeben. Dieser Wert sollte in der vollständigen Anfrage enthalten sein.
* `mimeType` (Zeichenfolge): Der Mime-Typ der entsprechenden Binärdatei, wie der Initiierungsanforderung angegeben. Dieser Wert sollte in der vollständigen Anfrage enthalten sein.
* `uploadToken` (Zeichenfolge): Ein Upload-Token für die entsprechende Binärdatei. Dieser Wert sollte in der vollständigen Anfrage enthalten sein.
* `uploadURIs` (Array): Eine Liste der Zeichenfolgen, deren Werte vollständige URIs sind, in die der binäre Inhalt hochgeladen werden soll (siehe [Hochladen der Binärdatei](#upload-binary)).
* `minPartSize` (Zahl): Die Mindestlänge (in Bytes) der Daten, die für einen der Upload-URIs bereitgestellt werden können, wenn mehr als ein URI vorhanden ist.
* `maxPartSize` (Zahl): Die maximale Länge (in Bytes) der Daten, die für einen der Upload-URIs bereitgestellt werden können, wenn mehr als ein URI vorhanden ist.

### Hochladen der Binärdatei {#upload-binary}

Die Ausgabe beim Initiieren eines Uploads umfasst einen oder mehrere Upload-URI-Werte. Wenn mehr als eine URI angegeben ist, teilt der Client die Binärdatei in Teile auf und fordert die POST jedes Teils in jeder URI in der Reihenfolge an. Verwenden Sie alle URIs. Stellen Sie sicher, dass die Größe der einzelnen Teile innerhalb der Mindest- und Höchstgrößen liegt, die in der initiativen Antwort angegeben sind. CDN-Edge-Knoten helfen, den angeforderten Upload von Binärdateien zu beschleunigen.

Eine mögliche Methode hierfür ist die Berechnung der Bauteilgröße anhand der Anzahl der Upload-URIs, die von der API bereitgestellt werden. Angenommen, die Gesamtgröße der Binärdatei beträgt 20.000 Byte und die Anzahl der Upload-URIs ist 2. Führen Sie dann die folgenden Schritte aus:

* Berechnen Sie die Teilegröße, indem Sie die Gesamtgröße durch die Anzahl der URIs teilen: 20.000 / 2 = 10.000.
* POST-Byte-Bereich 0-9.999 der Binärdatei zur ersten URI in der Liste der Upload-URIs.
* POST-Byte-Bereich 10.000-19.999 der Binärdatei zum zweiten URI in der Liste der Upload-URIs.

If the upload is successful, the server responds to each request with a `201` status code.

### Abschließen des Hochladens {#complete-upload}

Nachdem alle Teile einer Binärdatei hochgeladen wurden, senden Sie eine HTTP-POST-Anfrage an den vollständigen URI, der von den Initiierungsdaten bereitgestellt wird. Der Content-Typ des Anfragetexts sollte `application/x-www-form-urlencoded`-Formulardaten sein, die die folgenden Felder enthalten.

| Felder | Typ | Erforderlich | Beschreibung |
|---|---|---|---|
| `fileName` | Zeichenfolge | Erforderlich | Der Name des Assets, wie in den Initiierungsdaten angegeben. |
| `mimeType` | Zeichenfolge | Erforderlich | Der HTTP-Content-Typ der Binärdatei, wie in den Initiierungsdaten angegeben. |
| `uploadToken` | Zeichenfolge | Erforderlich | Upload-Token für die Binärdatei, wie in den Initiierungsdaten angegeben. |
| `createVersion` | Boolesch | Optional | If `True` and an asset with the specified name exists, then [!DNL Experience Manager] creates a new version of the asset. |
| `versionLabel` | Zeichenfolge | Optional | Wenn eine neue Version erstellt wird, die Bezeichnung, die der neuen Version eines Assets zugeordnet ist. |
| `versionComment` | Zeichenfolge | Optional | Wenn eine neue Version erstellt wird, die Kommentare, die der Version zugeordnet sind. |
| `replace` | Boolesch | Optional | If `True` and an asset with the specified name exists, [!DNL Experience Manager] deletes the asset then re-create it. |

>!![NOTE]
If the asset exists and neither `createVersion` nor `replace` is specified, then [!DNL Experience Manager] updates the asset&#39;s current version with the new binary.

Wie beim Initiierungsprozess können die vollständigen Anfragedaten Informationen zu mehr als einer Datei enthalten.

Das Hochladen einer Binärdatei wird erst durchgeführt, wenn die vollständige URL für die Datei aufgerufen wurde. Ein Asset wird verarbeitet, nachdem der Upload-Vorgang abgeschlossen ist. Die Verarbeitung wird nicht Beginn, auch wenn die Binärdatei des Assets vollständig hochgeladen wurde, der Upload-Vorgang jedoch nicht abgeschlossen ist.

Bei erfolgreicher Ausführung antwortet der Server mit Status-Code `200`.

### Open-Source-Upload-Bibliothek {#open-source-upload-library}

Um mehr über die Upload-Algorithmen zu erfahren oder eigene Upload-Skripten und -Tools zu erstellen, bietet Adobe Open-Source-Bibliotheken und -Tools:

* [Open-Source-AEM-Upload-Bibliothek](https://github.com/adobe/aem-upload).
* [Open-Source-Befehlszeilen-Tool](https://github.com/adobe/aio-cli-plugin-aem).

### Veraltete APIs zum Hochladen von Assets {#deprecated-asset-upload-api}

<!-- #ENGCHECK review / update the list of deprecated APIs below. -->

Die neue Upload-Methode wird nur [!DNL Adobe Experience Manager] als Cloud Service unterstützt. The APIs from [!DNL Adobe Experience Manager] 6.5 are deprecated. Die Methoden im Zusammenhang mit dem Hochladen oder Aktualisieren von Assets oder Ausgabeformaten (alle binären Uploads) werden in den folgenden APIs nicht mehr unterstützt:

* [Experience Manager Assets HTTP API](mac-api-assets.md)
* `AssetManager` Java-API, z. B. `AssetManager.createAsset(..)`

>[!MORELIKETHIS]
* [Open-Source-AEM-Upload-Bibliothek](https://github.com/adobe/aem-upload).
* [Open-Source-Befehlszeilen-Tool](https://github.com/adobe/aio-cli-plugin-aem).


## Asset-Verarbeitungs- und Nachbearbeitungs-Workflows {#post-processing-workflows}

In [!DNL Experience Manager], the asset processing is based on **[!UICONTROL Processing Profiles]** configuration that uses [asset microservices](asset-microservices-configure-and-use.md#get-started-using-asset-microservices). Für die Verarbeitung sind keine Entwicklererweiterungen erforderlich.

Verwenden Sie die standardmäßigen Workflows mit Erweiterungen mit benutzerdefinierten Schritten für die Konfiguration des Nachbearbeitungs-Workflows.

## Unterstützung von Workflow-Schritten im Nachbearbeitungs-Workflow {#post-processing-workflows-steps}

Kunden, die ein Upgrade von früheren Versionen von Assets durchführen, [!DNL Experience Manager] können Asset-Mikrodienste zur Verarbeitung von Assets verwenden. Die Cloud-nativen Asset-Microservices sind bedeutend einfacher zu konfigurieren und zu verwenden. Einige Workflow-Schritte, die im [!UICONTROL DAM-Update-Asset]-Workflow in der vorherigen Version verwendet wurden, werden nicht unterstützt.

[!DNL Experience Manager] als Cloud Service die folgenden Arbeitsablaufschritte unterstützen:

* `com.day.cq.dam.similaritysearch.internal.workflow.process.AutoTagAssetProcess`
* `com.day.cq.dam.core.impl.process.CreateAssetLanguageCopyProcess`
* `com.day.cq.wcm.workflow.process.CreateVersionProcess`
* `com.day.cq.dam.similaritysearch.internal.workflow.smarttags.StartTrainingProcess`
* `com.day.cq.dam.similaritysearch.internal.workflow.smarttags.TransferTrainingDataProcess`
* `com.day.cq.dam.core.impl.process.TranslateAssetLanguageCopyProcess`
* `com.day.cq.dam.core.impl.process.UpdateAssetLanguageCopyProcess`
* `com.adobe.cq.workflow.replication.impl.ReplicationWorkflowProcess`
* `com.day.cq.dam.core.impl.process.DamUpdateAssetWorkflowCompletedProcess`

Die folgenden technischen Workflow-Modelle werden entweder durch Asset-Microservices ersetzt oder es ist kein Support verfügbar:

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

>[!MORELIKETHIS]
* [Das Experience Cloud als Cloud Service-SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md).

