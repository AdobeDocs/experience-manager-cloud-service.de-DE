---
title: Umgang mit großen Inhaltsverzeichnissen
description: In diesem Abschnitt wird die Handhabung von umfangreichen Inhalts-Repositorys beschrieben.
source-git-commit: a3a90868b64a0639f8a065c8c4d6ef6410094f3d
workflow-type: tm+mt
source-wordcount: '1082'
ht-degree: 2%

---


# Umgang mit großen Inhaltsverzeichnissen {#handling-large-content-repositories}

## Übersicht {#overview}

Das Kopieren einer großen Anzahl von Blobs mit dem Content Transfer Tool (CTT) kann mehrere Tage dauern.
Um die Extraktions- und Aufnahmephasen der Inhaltstransferaktivität erheblich zu beschleunigen und Inhalte als Cloud Service in AEM zu verschieben, kann die CTT [AzCopy](https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10) als optionalen Vorkopieschritt nutzen. Dieser Vorkopieschritt kann verwendet werden, wenn die Quell-AEM-Instanz für die Verwendung eines Amazon S3- oder Azure Blob Storage-Datenspeichers konfiguriert ist.  Sobald dieser Vorschritt konfiguriert ist, kopiert AzCopy Blobs aus Amazon S3 oder Azure Blob Storage in den Migrationsset-Blob-Speicher. In der Aufnahmephase kopiert AzCopy Blobs aus dem Migrationssatz-Blob-Speicher in den Ziel-AEM als Cloud Service-Blob-Store.

>[!NOTE]
> Diese Funktion wurde in der CTT-Version 1.5.4 eingeführt.

## Wichtige Überlegungen vor dem Start {#important-considerations}

Im folgenden Abschnitt finden Sie wichtige Überlegungen, bevor Sie beginnen:

* AEM Quellversion muss 6.3 - 6.5 sein.
* Der Quell-AEM-Datenspeicher ist für die Verwendung von Amazon S3 oder Azure Blob Storage konfiguriert. Weitere Informationen finden Sie unter [Konfigurieren von Knotenspeichern und Datenspeichern in AEM 6](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/data-store-config.html?lang=en).
* Der gesamte Datenspeicher wird während der Extraktion kopiert. Da mit der Übertragung von Daten sowohl aus dem Amazon S3- als auch aus Azure Blob Storage Kosten verbunden sind, werden die Übertragungskosten im Verhältnis zur Gesamtmenge der Daten im Speicher-Container (egal ob in AEM angegeben) stehen. Weitere Informationen finden Sie unter [Amazon S3](https://aws.amazon.com/s3/pricing/) und [Azure Blob Storage](https://azure.microsoft.com/en-us/pricing/details/bandwidth/) .
* Jeder Migrationssatz kopiert den gesamten Datenspeicher, sodass nur ein einziger Migrationssatz verwendet werden sollte.
* Sie benötigen Zugriff, um [AzCopy](https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10) auf der Instanz (oder VM) zu installieren, auf der die Quell-AEM-Instanz ausgeführt wird.
* Sie benötigen entweder ein Schlüssel-Schlüssel-Paar für Zugriffsschlüssel und geheime Schlüssel für den Quell-Amazon S3-Bucket oder einen SAS-URI für den Quell-Azure Blob Storage-Container (schreibgeschützter Zugriff ist in Ordnung).
* Die Datenspeicherbereinigung wurde innerhalb der letzten sieben Tage an der Quelle ausgeführt. Weitere Informationen finden Sie unter [Automatische Datenspeicherbereinigung](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/data-store-config.html?lang=en#data-store-garbage-collection).
* Der Großteil der Daten in der Quellinstanz wird in die Migration einbezogen.

## Einrichten der Verwendung von AzCopy als Pre-Copy-Schritt {#setting-up-pre-copy-step}

In diesem Abschnitt erfahren Sie, wie Sie mit dem Content Transfer Tool einrichten, um AzCopy als Vorkopieschritt zu verwenden und den Inhalt zu AEM als Cloud Service zu migrieren:

### 0. Bestimmen Sie die Gesamtgröße aller Inhalte im Datenspeicher. {#determine-total-size}

#### Azure Blob Storage-Datenspeicher

Verwenden Sie auf der Seite mit den Containereigenschaften im Azure-Portal die Schaltfläche **Größe berechnen** , um die Größe des gesamten Inhalts im Container zu bestimmen. Beispiel:

![Bild](/help/move-to-cloud-service/content-transfer-tool/assets/Azure-blob-storage-data-store.png)

#### Amazon S3-Datenspeicher

Sie können die Registerkarte Metriken des Containers verwenden, um die Größe des gesamten Inhalts im Container zu bestimmen. Beispiel:


![Bild](/help/move-to-cloud-service/content-transfer-tool/assets/amazon-s3-data-store.png)

### 1. Installieren Sie AzCopy {#install-azcopy}

[](https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10) AzCopyis ist ein von Microsoft bereitgestelltes Befehlszeilen-Tool, das in der Quellinstanz verfügbar sein muss, um diese Funktion zu aktivieren.

Kurz gesagt, Sie werden höchstwahrscheinlich die Linux x86-64-Binärdatei von der [AzCopy-Dokumentseite](https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10) herunterladen und sie an einen Speicherort wie /usr/bin enttar. Notieren Sie sich, wo Sie die Binärdatei platziert haben, da Sie in einem späteren Schritt den vollständigen Pfad dazu benötigen.

### 2. Installieren Sie eine Version des Content Transfer Tool (CTT) mit AzCopy-Unterstützung {#install-ctt-azcopy-support}

AzCopy-Unterstützung ist in der CTT-Version 1.5.4 enthalten. Sie können die neueste Version von CTT vom [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)-Portal herunterladen.

### 3. Konfigurieren einer Datei &quot;azcopy.config&quot; {#configure-azcopy-config-file}

Erstellen Sie in der AEM-Quellinstanz in crx-quickstart/cloud-migration eine neue Datei mit dem Namen azcopy.config .

Der Inhalt dieser Konfigurationsdatei hängt davon ab, ob Ihre AEM-Quellinstanz einen Azure- oder Amazon S3-Datenspeicher verwendet.

#### Azure Blob Storage-Datenspeicher

Ihre azcopy.config -Datei sollte die folgenden Eigenschaften enthalten (stellen Sie sicher, dass Sie den richtigen azCopyPath und azureSas für Ihre Instanz verwenden).

>[!NOTE]
>
> Wenn Sie lieber keinen Schreibzugriff auf den Blob-Speicher-Container gewähren möchten, können Sie einen neuen SAS-URI generieren, der nur über Lese- und Listenberechtigungen verfügt.

```
azCopyPath=/usr/bin/azcopy
azureSas=https://example-resource.blob.core.windows.net/example-container?sig=--REDACTED--
```

#### Amazon S3-Datenspeicher

Ihre Datei azcopy.config sollte die folgenden Eigenschaften enthalten (stellen Sie sicher, dass Sie die richtigen Werte für Ihre Instanz verwenden).

>[!NOTE]
>
> Wenn Ihre Instanz IAM-Rollen verwendet, um AEM Zugriff auf S3 zu ermöglichen, müssen Sie eine Richtlinie und einen Benutzer erstellen, für die die Aktionen ListBucket und GetObject für den S3-Bucket aktiviert sind. Verwenden Sie nach der Einrichtung den Zugriffsschlüssel und den geheimen Schlüssel dieses Benutzers.

```
azCopyPath=/usr/bin/azcopy
s3Bucket=aem-63
s3Region=us-west-2
s3AccessKey=--REDACTED--
s3SecretKey=--REDACTED--
```

### 4. Extrahieren mit AzCopy {#extracting-azcopy}

Wenn die oben beschriebene Konfigurationsdatei vorhanden ist, wird die AzCopy-Vorkopie-Phase als Teil jeder nachfolgenden Extraktion ausgeführt. Um die Ausführung zu verhindern, können Sie diese Datei umbenennen oder entfernen.

1. Starten Sie eine Extraktion über die CTT-Benutzeroberfläche. Weitere Informationen finden Sie unter [Ausführen des Content Transfer Tool](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#running-tool) und [Extraktionsprozess](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#extraction-process) .
1. Vergewissern Sie sich, dass die folgende Zeile im Extraktionsprotokoll gedruckt ist:

```
c.a.g.s.m.commons.ContentExtractor - *************** Beginning AzCopy Pre-Copy phase ***************
```

Herzlichen Glückwunsch! Dieser Protokolleintrag bedeutet, dass Ihre Konfiguration als gültig betrachtet wurde und dass AzCopy derzeit alle Blobs aus dem Quell-Container in den Migrationbehälter kopiert.

Die Protokolleinträge von AzCopy werden im Extraktionsprotokoll angezeigt und erhalten das Präfix c.a.g.s.m.c.azcopy.AzCopyBlobPreCopy - [AzCopy pre-copy]

>[!CAUTION]
>
> Achten Sie in den ersten Minuten einer Extraktion auf etwaige Anzeichen eines Problems in den Extraktionslogs. Beispiel: Hier wird protokolliert, wenn der Quell-Azure-Container nicht gefunden werden konnte:


```
[AzCopy pre-copy] failed to perform copy command due to error: cannot start job due to error: cannot list files due to reason -> github.com/Azure/azure-storage-blob-go/azblob.newStorageError, github.com/Azure/azure-storage-blob-go@v0.10.1-0.20210407023846-16cf969ec1c3/azblob/zc_storage_error.go:42
[AzCopy pre-copy] ===== RESPONSE ERROR (ServiceCode=ContainerNotFound) =====
[AzCopy pre-copy] Description=The specified container does not exist.
[AzCopy pre-copy] RequestId:5fb674b9-201e-001b-2a5b-527400000000
[AzCopy pre-copy] Time:2021-05-26T18:18:07.5931967Z, Details: 
[AzCopy pre-copy] Code: ContainerNotFound
```

Im Fall eines Problems mit AzCopy schlägt die Extraktion sofort fehl, und die Extraktionsprotokolle enthalten Details zum Fehler.

Blobs, die vor dem Fehler kopiert wurden, werden von AzCopy bei nachfolgenden Ausführungen automatisch übersprungen und müssen nicht erneut kopiert werden.

### 5. Erfassen mit AzCopy {#ingesting-azcopy}

Mit der Veröffentlichung des Content Transfer Tool 1.5.4 haben wir die AzCopy-Unterstützung zur Authoring-Erfassung hinzugefügt.

>[!NOTE]
>
> Es wird empfohlen, die Autorenaufnahme zuerst allein auszuführen. Dadurch wird die Aufnahme der Veröffentlichung beschleunigt, wenn sie später ausgeführt wird.

Um AzCopy während der Aufnahme nutzen zu können, müssen Sie eine AEM als Cloud Service-Version verwenden, die mindestens Version 2021.6.5561 ist.

Starten Sie die Autorenaufnahme über die CTT-Benutzeroberfläche. Weitere Informationen finden Sie im [Aufnahmeprozess](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool.md#ingestion-process).
Die Protokolleinträge von AzCopy werden im Aufnahmeprotokoll angezeigt. Sie sehen wie folgt aus:

```
*************** Beginning AzCopy pre-copy phase ***************
INFO: Scanning...
INFO: Failed to create one or more destination container(s). Your transfers may still succeed if the container already exists.
INFO: Any empty folders will not be processed, because source and/or destination doesn't have full folder support
INFO: azcopy: A newer version 10.11.0 is available to download
 
 
Job 419d98da-fc05-2a45-70cc-797fee632031 has started
Log file is located at: /root/.azcopy/419d98da-fc05-2a45-70cc-797fee632031.log
 
 
0.0 %, 0 Done, 0 Failed, 886 Pending, 0 Skipped, 886 Total,
 
 
Job 419d98da-fc05-2a45-70cc-797fee632031 summary
Elapsed Time (Minutes): 0.0334
Number of File Transfers: 886
Number of Folder Property Transfers: 0
Total Number of Transfers: 886
Number of Transfers Completed: 17
Number of Transfers Failed: 0
Number of Transfers Skipped: 869
TotalBytesTransferred: 248350
Final Job Status: CompletedWithSkipped
 
*************** Completed AzCopy pre-copy phase ***************
```
