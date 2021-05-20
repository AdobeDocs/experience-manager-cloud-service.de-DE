---
title: Entwicklerreferenzen für  [!DNL Assets]
description: '[!DNL Assets] APIs and developer reference content lets you manage assets, including binary files, metadata, renditions, comments, and [!DNL Content Fragments].'
contentOwner: AG
feature: APIs,Assets-HTTP-API
role: Developer,Architect,Administrator
exl-id: c75ff177-b74e-436b-9e29-86e257be87fb
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '1394'
ht-degree: 92%

---

# [!DNL Adobe Experience Manager Assets] Anwendungsfälle, APIs und Referenzmaterial für Entwickler  {#assets-cloud-service-apis}

Der Artikel enthält Empfehlungen, Referenzmaterialien und Ressourcen für Entwickler von [!DNL Assets] as a [!DNL Cloud Service]. Er enthält ein neues Modul für den Asset-Upload, eine API-Referenz und Informationen über die Unterstützung, die in Nachbearbeitungs-Workflows bereitgestellt wird.

## [!DNL Experience Manager Assets]-APIs und -Vorgänge {#use-cases-and-apis}

[!DNL Assets] as a [!DNL Cloud Service] bietet mehrere APIs für die programmgesteuerte Interaktion mit digitalen Assets. Jede API unterstützt spezifische Anwendungsfälle, wie in der folgenden Tabelle beschrieben. Die [!DNL Assets]-Benutzeroberfläche, das [!DNL Experience Manager]-Desktop-Programm und [!DNL Adobe Asset Link] unterstützen alle oder einige der Vorgänge.

>[!CAUTION]
>
>Einige APIs existieren weiterhin, werden jedoch nicht aktiv unterstützt (mit einem × gekennzeichnet). Verwenden Sie diese APIs nach Möglichkeit nicht.

| Unterstützungsebene | Beschreibung |
| ------------- | --------------------------- |
| ✓ | Unterstützt |
| × | Nicht unterstützt. Nicht verwenden. |
| - | Nicht verfügbar |

| Anwendungsfall | [aem-upload](https://github.com/adobe/aem-upload) | [AEM / Sling / JCR](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/index.html) Java-APIs | [Asset Compute Service](https://experienceleague.adobe.com/docs/asset-compute/using/extend/understand-extensibility.html?lang=de) | [[!DNL Assets] HTTP-API](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/admin/mac-api-assets.html?lang=de#create-an-asset) | Sling [GET](https://sling.apache.org/documentation/bundles/rendering-content-default-get-servlets.html)/[POST](https://sling.apache.org/documentation/bundles/manipulating-content-the-slingpostservlet-servlets-post.html) Servlets | [GraphQL](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html?lang=de) _(Vorschau)_ |
| ----------------|:---:|:---:|:---:|:---:|:---:|:---:|
| **Ursprüngliche Binärdatei** |  |  |  |  |  |  |
| Original erstellen | verwalten | × | - | × | × | - |
| Original lesen | - | × | verwalten | verwalten | verwalten | - |
| Original aktualisieren | verwalten | × | verwalten | × | × | - |
| Original löschen | - | verwalten | - | verwalten | verwalten | - |
| Original kopieren | - | verwalten | - | verwalten | verwalten | - |
| Original verschieben | - | verwalten | - | verwalten | verwalten | - |
| **Metadaten** |  |  |  |  |  |  |
| Metadaten erstellen | - | verwalten | verwalten | verwalten | verwalten | - |
| Metadaten lesen | - | verwalten | - | verwalten | verwalten | - |
| Metadaten aktualisieren | - | verwalten | verwalten | verwalten | verwalten | - |
| Metadaten löschen | - | verwalten | verwalten | verwalten | verwalten | - |
| Metadaten kopieren | - | verwalten | - | verwalten | verwalten | - |
| Metadaten verschieben | - | verwalten | - | verwalten | verwalten | - |
| **Inhaltsfragmente** |  |  |  |  |  |  |
| Inhaltsfragmente erstellen | - | verwalten | - | verwalten | - | - |
| Inhaltsfragmente lesen | - | verwalten | - | verwalten | - | verwalten |
| Inhaltsfragmente aktualisieren | - | verwalten | - | verwalten | - | - |
| Inhaltsfragmente löschen | - | verwalten | - | verwalten | - | - |
| Inhaltsfragmente kopieren | - | verwalten | - | verwalten | - | - |
| Inhaltsfragmente verschieben | - | verwalten | - | verwalten | - | - |
| **Versionen** |  |  |  |  |  |  |
| Version erstellen | verwalten | verwalten | - | - | - | - |
| Version lesen | - | verwalten | - | - | - | - |
| Version löschen | - | verwalten | - | - | - | - |
| **Ordner** |  |  |  |  |  |  |
| Ordner erstellen | verwalten | verwalten | - | verwalten | - | - |
| Ordner lesen | - | verwalten | - | verwalten | - | - |
| Ordner löschen | verwalten | verwalten | - | verwalten | - | - |
| Ordner kopieren | verwalten | verwalten | - | verwalten | - | - |
| Ordner verschieben | verwalten | verwalten | - | verwalten | - | - |

## Asset-Upload {#asset-upload-technical}

Unter [!DNL Experience Manager] als [!DNL Cloud Service] können Sie die Assets mithilfe der HTTP-API direkt in den Cloud-Speicher hochladen. Die Schritte zum Hochladen einer Binärdatei sind:

1. [Senden einer HTTP-Anfrage](#initiate-upload). Diese informiert die [!DNL Experience Manage]r-Implementierung über Ihre Absicht, eine neue Binärdatei hochzuladen.
1. [Posten des Inhalts der Binärdatei](#upload-binary) an einen oder mehrere URIs, die von der Initiierungsanfrage bereitgestellt werden.
1. [Senden einer HTTP-Anfrage](#complete-upload), um den Server darüber zu informieren, dass der Inhalt der Binärdatei erfolgreich hochgeladen wurde.

![Überblick über das direkte binäre Upload-Protokoll](assets/add-assets-technical.png)

Der Ansatz bietet eine skalierbare und leistungsfähigere Handhabung von Asset-Uploads. Die Unterschiede im Vergleich zu [!DNL Experience Manager] 6.5 sind:

* Binärdateien durchlaufen nicht [!DNL Experience Manager], das jetzt lediglich den Upload-Prozess mit dem für die Implementierung konfigurierten binären Cloud-Speicher koordiniert.
* Der binäre Cloud-Speicher funktioniert mit einem Content Delivery Network (CDN) oder einem Edge-Netzwerk. Ein CDN wählt einen Upload-Endpunkt aus, der für einen Client näher liegt. Wenn Daten eine kürzere Entfernung zu einem nahe gelegenen Endpunkt zurücklegen, verbessern sich die Upload-Leistung und das Benutzererlebnis, insbesondere für geografisch verteilte Teams.

>[!NOTE]
Informationen zum Implementieren dieses Ansatzes finden Sie im Client-Code in der Open-Source-Bibliothek [aem-upload](https://github.com/adobe/aem-upload).

### Initiieren des Uploads {#initiate-upload}

Senden Sie eine HTTP-POST-Anfrage an den gewünschten Ordner. Assets werden in diesem Ordner erstellt oder aktualisiert. Schließen Sie den Selektor `.initiateUpload.json` ein, um anzugeben, dass die Anfrage darin besteht, den Upload einer Binärdatei zu starten. Der Pfad zum Ordner, in dem das Asset erstellt werden soll, lautet beispielsweise `/assets/folder`. Die POST-Anfrage ist `POST https://[aem_server]:[port]/content/dam/assets/folder.initiateUpload.json`.

Der Content-Typ des Anfragetexts sollte `application/x-www-form-urlencoded`-Formulardaten sein, die die folgenden Felder enthalten:

* `(string) fileName`: Erforderlich. Der Name des Assets, wie er in [!DNL Experience Manager] angezeigt wird.
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

* `completeURI` (Zeichenfolge): Diese URI aufrufen, wenn das Hochladen der Binärdatei abgeschlossen ist. Die URI kann eine absolute oder relative URI sein. Clients sollten in der Lage sein, beide Fälle zu handhaben. Das heißt, dass der Wert `"https://author.acme.com/content/dam.completeUpload.json"` oder `"/content/dam.completeUpload.json"` sein kann. Siehe [Abschließen des Hochladens ](#complete-upload).
* `folderPath` (Zeichenfolge): Vollständiger Pfad zum Ordner, in den die Binärdatei hochgeladen wird.
* `(files)` (Array): Eine Liste der Elemente, deren Länge und Reihenfolge mit der Länge und Reihenfolge der Liste der binären Informationen übereinstimmen, die in der Anfrage zum Initiieren bereitgestellt werden.
* `fileName` (Zeichenfolge): Der Name der entsprechenden Binärdatei, wie in der Anfrage zum Initiieren angegeben. Dieser Wert sollte in der vollständigen Anfrage enthalten sein.
* `mimeType` (Zeichenfolge): Der Mime-Typ der entsprechenden Binärdatei, wie der Initiierungsanfrage angegeben. Dieser Wert sollte in der vollständigen Anfrage enthalten sein.
* `uploadToken` (Zeichenfolge): Ein Upload-Token für die entsprechende Binärdatei. Dieser Wert sollte in der vollständigen Anfrage enthalten sein.
* `uploadURIs` (Array): Eine Liste der Zeichenfolgen, deren Werte vollständige URIs sind, in die der binäre Inhalt hochgeladen werden soll (siehe [Hochladen der Binärdatei](#upload-binary)).
* `minPartSize` (Zahl): Die Mindestlänge (in Bytes) der Daten, die für eine der  `uploadURIs`bereitgestellt werden können, wenn mehr als eine URI vorhanden ist.
* `maxPartSize` (Zahl): Die maximale Länge (in Bytes) der Daten, die für eine der  `uploadURIs`bereitgestellt werden können, wenn mehr als eine URI vorhanden ist.

### Hochladen der Binärdatei {#upload-binary}

Die Ausgabe beim Initiieren eines Uploads umfasst einen oder mehrere Upload-URI-Werte. Wenn mehr als eine URI angegeben wird, teilt der Client die Binärdatei in Teile und sendet die POST-Anfrage jeden Teils in der richtigen Reihenfolge an jede URI. Verwenden Sie alle URIs. Stellen Sie sicher, dass die Größe der einzelnen Teile innerhalb der minimalen und maximalen Größe liegt, wie in der Initiierungsantwort angegeben. CDN-Edge-Knoten beschleunigen das angeforderte Hochladen von Binärdateien.

Eine Möglichkeit, dies zu erreichen, besteht darin, die Teilegröße basierend auf der Anzahl der von der API bereitgestellten Upload-URIs zu berechnen. Angenommen, die Gesamtgröße der Binärdatei beträgt 20.000 Bytes und die Anzahl der Upload-URIs beträgt 2. Führen Sie dann die folgenden Schritte aus:

* Berechnen Sie die Teilegröße, indem Sie die Gesamtgröße durch die Anzahl der URIs teilen: 20.000 : 2 = 10.000.
* POST-Byte-Bereich 0-9.999 der Binärdatei zum ersten URI in der Liste der Upload-URIs.
* POST-Byte-Bereich 10.000-19.999 der Binärdatei zum zweiten URI in der Liste der Upload-URIs.

Bei erfolgreicher Ausführung des Uploads antwortet der Server auf jede Anfrage mit Status-Code `201`.

### Abschließen des Uploads {#complete-upload}

Nachdem alle Teile einer Binärdatei hochgeladen wurden, senden Sie eine HTTP-POST-Anfrage an den vollständigen URI, der von den Initiierungsdaten bereitgestellt wird. Der Content-Typ des Anfragetexts sollte `application/x-www-form-urlencoded`-Formulardaten sein, die die folgenden Felder enthalten.

| Felder | Typ | Erforderlich | Beschreibung |
|---|---|---|---|
| `fileName` | Zeichenfolge | Erforderlich | Der Name des Assets, wie in den Initiierungsdaten angegeben. |
| `mimeType` | Zeichenfolge | Erforderlich | Der HTTP-Content-Typ der Binärdatei, wie in den Initiierungsdaten angegeben. |
| `uploadToken` | Zeichenfolge | Erforderlich | Upload-Token für die Binärdatei, wie in den Initiierungsdaten angegeben. |
| `createVersion` | Boolesch | Optional | Wenn `True` und ein Asset mit dem angegebenen Namen existiert, erstellt [!DNL Experience Manager] eine neue Version des Assets. |
| `versionLabel` | Zeichenfolge | Optional | Wenn eine neue Version erstellt wird, die Bezeichnung, die der neuen Version eines Assets zugeordnet ist. |
| `versionComment` | Zeichenfolge | Optional | Wenn eine neue Version erstellt wird, die Kommentare, die der Version zugeordnet sind. |
| `replace` | Boolesch | Optional | Wenn `True` und ein Asset mit dem angegebenen Namen existiert, löscht [!DNL Experience Manager] das Asset und erstellt es dann erneut. |

>[!NOTE]
Wenn das Asset existiert und weder `createVersion` noch `replace` angegeben ist, aktualisiert [!DNL Experience Manager] die aktuelle Version des Assets mit der neuen Binärdatei.

Wie beim Initiierungsprozess können die vollständigen Anfragedaten Informationen zu mehr als einer Datei enthalten.

Das Hochladen einer Binärdatei wird erst durchgeführt, wenn die vollständige URL für die Datei aufgerufen wurde. Ein Asset wird verarbeitet, nachdem der Upload-Vorgang abgeschlossen ist. Die Verarbeitung wird nicht gestartet, auch wenn die Binärdatei des Assets vollständig hochgeladen wurde, der Upload-Vorgang jedoch nicht abgeschlossen ist.

Bei erfolgreicher Ausführung antwortet der Server mit Status-Code `200`.

### Open-Source-Upload-Bibliothek {#open-source-upload-library}

Um mehr über die Upload-Algorithmen zu erfahren oder eigene Upload-Skripte und -Tools zu erstellen, stellt Adobe Open-Source-Bibliotheken und -Tools bereit:

* [Open-Source-AEM-Upload-Bibliothek](https://github.com/adobe/aem-upload).
* [Open-Source-Befehlszeilen-Tool](https://github.com/adobe/aio-cli-plugin-aem).

### Veraltete APIs zum Hochladen von Assets {#deprecated-asset-upload-api}

<!-- #ENGCHECK review / update the list of deprecated APIs below. -->

Die neue Upload-Methode wird nur für [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] unterstützt. Die APIs aus [!DNL Adobe Experience Manager] 6.5 werden nicht mehr unterstützt. Die Methoden im Zusammenhang mit dem Hochladen oder Aktualisieren von Assets oder Ausgabedarstellungen (alle binären Uploads) werden in den folgenden APIs nicht mehr unterstützt:

* [Experience Manager Assets-HTTP-API](mac-api-assets.md)
* `AssetManager` Java-API, z. B. `AssetManager.createAsset(..)`

>[!MORELIKETHIS]
* [Open-Source-AEM-Upload-Bibliothek](https://github.com/adobe/aem-upload).
* [Open-Source-Befehlszeilen-Tool](https://github.com/adobe/aio-cli-plugin-aem).


## Asset-Verarbeitungs- und Nachbearbeitungs-Workflows {#post-processing-workflows}

In [!DNL Experience Manager] basiert die Asset-Verarbeitung auf der Konfiguration von **[!UICONTROL Verarbeitungsprofilen]**, die [Asset-Microservices](asset-microservices-configure-and-use.md#get-started-using-asset-microservices) verwendet. Für die Verarbeitung sind keine Entwicklererweiterungen erforderlich.

Verwenden Sie die standardmäßigen Workflows mit Erweiterungen mit benutzerdefinierten Schritten für die Konfiguration des Nachbearbeitungs-Workflows.

## Unterstützung von Workflow-Schritten im Nachbearbeitungs-Workflow {#post-processing-workflows-steps}

Kunden, die ein Upgrade von früheren Versionen von [!DNL Experience Manager] durchführen, können Asset-Microservices zur Verarbeitung von Assets verwenden. Die Cloud-nativen Asset-Microservices sind bedeutend einfacher zu konfigurieren und zu verwenden. Einige Workflow-Schritte, die im [!UICONTROL DAM-Update-Asset]-Workflow in der vorherigen Version verwendet wurden, werden nicht unterstützt.

[!DNL Experience Manager] as a [!DNL Cloud Service] unterstützt die folgenden Workflow-Schritte:

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
* [[!DNL Experience Cloud] as a [!DNL Cloud Service] SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md).

