---
title: Handhabung großer Content-Repositorys
description: In diesem Abschnitt wird die Handhabung großer Content-Repositorys beschrieben.
exl-id: 21bada73-07f3-4743-aae6-2e37565ebe08
source-git-commit: 7260649eaab303ba5bab55ccbe02395dc8159949
workflow-type: tm+mt
source-wordcount: '1816'
ht-degree: 49%

---

# Handhabung großer Content-Repositorys {#handling-large-content-repositories}

## Übersicht {#overview}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_precopy"
>title="Handhabung großer Content-Repositorys"
>abstract="Um die Extraktions- und Aufnahmephasen der Inhaltstransferaktivität erheblich zu beschleunigen und Inhalte in AEM as a Cloud Service zu verschieben, kann das Content Transfer Tool (CTT) AzCopy als optionalen Vorkopieschritt verwenden. Sobald dieser Vorschritt konfiguriert ist, kopiert AzCopy Blobs aus Amazon S3 oder Azure Blob Storage in den Migrationssatz-Blob-Speicher. In der Aufnahmephase kopiert AzCopy Blobs aus dem Migrationssatz-Blob-Speicher in den Ziel-Blob-Speicher von Adobe Experience Manager as a Cloud Service."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/handling-large-content-repositories.html#setting-up-pre-copy-step" text="Erste Schritte mit AzCopy als Vorkopieschritt"

Das Kopieren vieler Blobs mit dem Content Transfer Tool (CTT) kann mehrere Tage dauern.
Um die Extraktions- und Aufnahmephasen der Inhaltstransferaktivität zu beschleunigen und Inhalte auf AEM as a Cloud Service zu verschieben, kann die CTT [AzCopy](https://learn.microsoft.com/de-de/azure/storage/common/storage-use-azcopy-v10) als optionalen Schritt zum Vorauskopieren. Dieser Schritt für eine Vorabkopie kann erfolgen, wenn die AEM-Quellinstanz für die Verwendung eines Amazon S3-Datenspeichers, Azure Blob Storage-Datenspeichers oder Dateidatenspeichers konfiguriert ist. Der Schritt &quot;Vorab-Kopieren&quot;ist am effektivsten für die erste vollständige Extraktion und Aufnahme. Die Verwendung der Vorabkopie für nachfolgende Auffüllungen wird jedoch nicht empfohlen (wenn die Auffüllgröße weniger als 200 GB beträgt), da dies den gesamten Prozess verlängern kann. Sobald dieser Vorschritt konfiguriert ist, kopiert AzCopy in der Extrahierungsphase Blobs aus dem Amazon S3-, Azure Blob Storage- oder Dateidatenspeicher in den Migrationssatz-Blob-Speicher. In der Aufnahmephase kopiert AzCopy Blobs aus dem Migrationssatz-Blob-Speicher in den Ziel-Blob-Speicher von Adobe Experience Manager as a Cloud Service.

## Wichtige Vorüberlegungen {#important-considerations}

Im folgenden Abschnitt finden Sie wichtige Überlegungen, die Sie berücksichtigen sollten, bevor Sie beginnen:

* Ab Version 2.0.16 von CTT wird die Prepy-Einrichtung automatisch durchgeführt, wenn das Bundle installiert wird. Wenn die Größe des Migrationssatzes größer als 200 GB ist, verwendet der Extraktionsvorgang automatisch die Funktion &quot;Prepy&quot;. Die Datei „azcopy.config“ wird im Verzeichnis „crx-quickstart/cloud-migration/“ erstellt. Wenn Sie CTT-Version 2.0.16 oder höher verwenden, müssen Sie das Precopy-Setup nicht manuell durchführen.

* AEM Quellversion muss 6.3 bis 6.5 sein.

* Der AEM-Quelldatenspeicher ist für die Verwendung von Amazon S3 oder Azure Blob Storage konfiguriert. Weitere Informationen finden Sie unter [Konfigurieren von Knotenspeichern und Datenspeichern in AEM 6](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/data-store-config.html?lang=de).

* Jeder Migrationssatz kopiert den gesamten Datenspeicher, sodass nur ein einziger Migrationssatz verwendet werden sollte.

* Sie benötigen Zugriff auf die Installation [AzCopy](https://learn.microsoft.com/de-de/azure/storage/common/storage-use-azcopy-v10) auf der Instanz (oder VM), die die AEM-Quellinstanz ausführt.

* Die Datenspeicherbereinigung wurde innerhalb der letzten sieben Tage an der Quelle ausgeführt. Weitere Informationen finden Sie unter [Speicherbereinigung](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/data-store-config.html?lang=de#data-store-garbage-collection).

### Weitere Aspekte, falls die AEM-Quellinstanz für die Verwendung eines Amazon S3- oder Azure Blob Storage-Datenspeichers konfiguriert ist {#additional-considerations-amazons3-azure}

* Mit der Übertragung von Daten aus Amazon S3 und Azure Blob Storage sind Kosten verbunden. Die Übertragungskosten beziehen sich auf die Gesamtmenge der Daten in Ihrem vorhandenen Speicher-Container (unabhängig davon, ob in AEM darauf verwiesen wird oder nicht). Weitere Informationen finden Sie unter [Amazon S3](https://aws.amazon.com/s3/pricing/) und [Azure Blob-Speicher](https://azure.microsoft.com/de-de/pricing/details/bandwidth/).

* Sie benötigen entweder ein Zugriffs- und ein geheimes Schlüsselpaar für den vorhandenen Amazon S3-Quell-Bucket oder einen SAS-URI für den vorhandenen Azure Blob Storage-Quell-Container (schreibgeschützter Zugriff ist in Ordnung).

### Weitere Aspekte, falls die AEM-Quellinstanz für die Verwendung des Dateidatenspeichers konfiguriert ist {#additional-considerations-aem-instance-filedatastore}

* Das lokale System muss über freien Speicherplatz verfügen, der zwingend größer als 1/256 der Größe des Quelldatenspeichers ist. Wenn die Größe des Datenspeichers beispielsweise 3 Terabyte beträgt, muss im `crx-quickstart/cloud-migration` -Ordner auf der Quelle, damit AzCopy funktioniert. Das Quellsystem sollte mindestens über 1 GB freien Speicherplatz verfügen. Freier Speicherplatz kann mit `df -h` auf Linux®-Instanzen und dem Befehl dir in den Windows-Instanzen.

* Bei jeder Extraktion mit aktiviertem AzCopy wird der gesamte Dateidatenspeicher reduziert und in den Cloud-Migrations-Container kopiert. Wenn Ihr Migrationssatz kleiner als die Größe Ihres Datenspeichers ist, ist die AzCopy-Extraktion nicht der optimale Ansatz.

* Wenn die AzCopy-Funktion zum Kopieren über den vorhandenen Datenspeicher verwendet wurde, deaktivieren Sie diese für Delta- oder Auffüllextraktionen.

## Einrichten zur Verwendung von AzCopy als Vorkopieschritt {#setting-up-pre-copy-step}

>[!NOTE]
>Ab Version 2.0.16 von CTT wird die Prepy-Einrichtung automatisch durchgeführt, wenn das Bundle installiert wird. Wenn die Größe des Migrationssatzes größer als 200 GB ist, verwendet der Extraktionsvorgang automatisch die Funktion &quot;Prepy&quot;. Die Datei „azcopy.config“ wird im Verzeichnis „crx-quickstart/cloud-migration/“ erstellt. Wenn Sie die Konfiguration der Datei manuell aktualisieren möchten, lesen Sie die folgenden Abschnitte.

In diesem Abschnitt erfahren Sie, wie Sie mit dem Content Transfer Tool einrichten, um AzCopy als Vorkopieschritt zu verwenden und den Inhalt AEM as a Cloud Service zu migrieren:

### 0. Bestimmen der Gesamtgröße aller Inhalte im Datenspeicher {#determine-total-size}

Es ist aus zwei Gründen wichtig, die Gesamtgröße des Datenspeichers zu bestimmen:

* Wenn die AEM-Quelle für die Verwendung des Dateidatenspeichers konfiguriert ist, muss das lokale System über freien Speicherplatz verfügen, der zwingend größer als 1/256 des Quelldatenspeichers ist.

#### Azure Blob-Speicher – Datenspeicher {#azure-blob-storage}

Verwenden Sie auf der Seite mit den Container-Eigenschaften im Azure-Portal die Schaltfläche **Größe berechnen**, um die Gesamtgröße aller Container-Inhalte zu bestimmen. Beispiel:

![image](/help/journey-migration/content-transfer-tool/assets/Azure-blob-storage-data-store.png)

#### Amazon S3-Datenspeicher {#amazon-data}

Auf der Registerkarte zu den Metriken des Containers können Sie die Gesamtgröße der Inhalte des Containers bestimmen. Beispiel:


![image](/help/journey-migration/content-transfer-tool/assets/amazon-s3-data-store.png)

#### Dateidatenspeicher {#file-data-store-determine-size}

* Führen Sie bei Mac- und UNIX®-Systemen den Befehl du im Datenspeicherverzeichnis aus, um dessen Größe zu erhalten:
  `du -sh [path to datastore on the instance]`. Wenn Ihr Datenspeicher beispielsweise unter `/mnt/author/crx-quickstart/repository/datastore`, erhält der folgende Befehl die Größe: `du -sh /mnt/author/crx-quickstart/repository/datastore`.

* Für Windows verwenden Sie den Befehl „dir“ im Datenspeicherverzeichnis, um dessen Größe zu erhalten:
  `dir /a/s [location of datastore]`.

### 1. Installieren von AzCopy {#install-azcopy}

[AzCopy](https://learn.microsoft.com/de-de/azure/storage/common/storage-use-azcopy-v10) ist ein von Microsoft® bereitgestelltes Befehlszeilen-Tool, das in der Quellinstanz verfügbar sein muss, um diese Funktion zu aktivieren.

Kurz gesagt, Sie möchten die Linux® x86-64-Binärdatei von der [AzCopy-Dokumentseite](https://learn.microsoft.com/de-de/azure/storage/common/storage-use-azcopy-v10) und entschlüsseln Sie sie an einem Speicherort wie /usr/bin.

>[!IMPORTANT]
>Notieren Sie sich, wo Sie die Binärdatei platziert haben, da Sie den vollständigen Pfad zu ihr in einem späteren Schritt benötigen.

### 2. Installieren einer Version des Content Transfer Tool (CTT) mit AzCopy-Unterstützung {#install-ctt-azcopy-support}

>[!IMPORTANT]
>Es sollte die neueste Version von CTT verwendet werden.

AzCopy-Unterstützung für Amazon S3, Azure Blob Storage und File Data Store ist in der neuesten CTT-Version enthalten.
Sie können die neueste Version von CTT vom [Software Distribution-Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) herunterladen.
Es ist zu beachten, dass nur die Versionen 2.0.0 und höher unterstützt werden. Es wird empfohlen, die neueste Version zu verwenden.

### 3. Konfigurieren der Datei „azcopy.config“ {#configure-azcopy-config-file}

In der Quell-AEM-Instanz in `crx-quickstart/cloud-migration`erstellen Sie eine Datei mit dem Namen `azcopy.config`.

>[!NOTE]
>Der Inhalt dieser Konfigurationsdatei ist unterschiedlich, je nachdem, ob Ihre AEM-Instanz einen Azure- oder Amazon S3-Datenspeicher oder einen Dateidatenspeicher verwendet.

#### Azure Blob Storage-Datenspeicher {#azure-blob-storage-data}

Ihre Datei „azcopy.config“ sollte die folgenden Eigenschaften enthalten (stellen Sie sicher, dass Sie den richtigen AzCopyPath- und AzureSas-Parameter für Ihre Instanz verwenden).

>[!NOTE]
>
> Wenn Sie keinen Schreibzugriff auf den Blob-Speicher-Container gewähren möchten, können Sie einen neuen SAS-URI generieren, der nur über Lese- und Listenberechtigungen verfügt.

```
azCopyPath=/usr/bin/azcopy
azureSas=https://example-resource.blob.core.windows.net/example-container?sig=--REDACTED--
```

#### Amazon S3-Datenspeicher {#amazon-sdata-store}

Ihre Datei „azcopy.config“ sollte die folgenden Eigenschaften enthalten (stellen Sie sicher, dass Sie die richtigen Werte für Ihre Instanz verwenden).

>[!NOTE]
>
> Wenn Ihre Instanz IAM-Rollen verwendet, um AEM Zugriff auf S3 zu ermöglichen, müssen Sie eine Richtlinie und einen Benutzer erstellen, für die die Aktionen ListBucket und GetObject für den S3-Bucket aktiviert sind. Verwenden Sie nach der Einrichtung den Zugriffsschlüssel und den geheimen Schlüssel dieses Anwenders.

```
azCopyPath=/usr/bin/azcopy
s3Bucket=aem-63
s3Region=us-west-2
s3AccessKey=--REDACTED--
s3SecretKey=--REDACTED--
```

#### Dateidatenspeicher {#file-data-store-azcopy-config}

Ihre `azcopy.config`-Datei muss die Eigenschaft „azcopyPath“ und eine optionale Eigenschaft „repository.home“ enthalten, die auf den Speicherort des Dateidatenspeichers verweist. Verwenden Sie die richtigen Werte für Ihre Instanz.
Dateidatenspeicher

```
azCopyPath=/usr/bin/azcopy
repository.home=/mnt/crx/author/crx-quickstart/repository/datastore
```

Die Eigenschaft azCopyPath muss den vollständigen Pfad des Speicherorts enthalten, an dem das Befehlszeilen-Tool azCopy auf der Quell-AEM-Instanz installiert ist. Wenn die azCopyPath -Eigenschaft fehlt, wird der Blob-Prepy-Schritt nicht ausgeführt.

Wenn `repository.home` -Eigenschaft fehlt in azcopy.config, dann ist der standardmäßige Datenspeicherort `/mnt/crx/author/crx-quickstart/repository/datastore` wird verwendet, um eine Vorab-Bearbeitung durchzuführen.

### 4. Extrahieren mit AzCopy {#extracting-azcopy}

Mit der oben genannten Konfigurationsdatei wird die AzCopy-Vorkopie-Phase im Rahmen jeder nachfolgenden Extraktion ausgeführt. Um die Ausführung zu verhindern, können Sie diese Datei umbenennen oder entfernen.

>[!NOTE]
>Wenn AzCopy nicht richtig konfiguriert ist, wird die folgende Meldung in den Protokollen angezeigt:
>`INFO c.a.g.s.m.c.a.AzCopyCloudBlobPreCopy - Blob pre-copy is not supported`.

1. Starten Sie eine Extraktion über die CTT-Benutzeroberfläche. Weitere Informationen finden Sie unter [Erste Schritte mit dem Content Transfer Tool](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/getting-started-content-transfer-tool.md) und [Extraktionsvorgang](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md).

1. Vergewissern Sie sich, dass die folgende Zeile im Extraktionsprotokoll gedruckt ist:

```
c.a.g.s.m.commons.ContentExtractor - *************** Beginning AzCopy Pre-Copy phase ***************
```

Herzlichen Glückwunsch! Dieser Protokolleintrag bedeutet, dass Ihre Konfiguration als gültig betrachtet wurde und dass AzCopy alle Blobs aus dem Quell-Container in den Migrationbehälter kopiert.

Die Protokolleinträge von AzCopy werden im Extraktionsprotokoll angezeigt und erhalten das Präfix c.a.s.m.c.azcopy.AzCopyBlobPreCopy - [AzCopy-Vorkopie]

>[!CAUTION]
>
> Achten Sie in den ersten Minuten einer Extraktion auf etwaige Anzeichen eines Problems in den Extraktionsprotokollen. Das folgende Beispiel zeigt, was protokolliert wird, wenn der Azure-Quellcontainer nicht gefunden werden kann:

```
[AzCopy pre-copy] failed to perform copy command due to error: cannot start job due to error: cannot list files due to reason -> github.com/Azure/azure-storage-blob-go/azblob.newStorageError, github.com/Azure/azure-storage-blob-go@v0.10.1-0.20210407023846-16cf969ec1c3/azblob/zc_storage_error.go:42
[AzCopy pre-copy] ===== RESPONSE ERROR (ServiceCode=ContainerNotFound) =====
[AzCopy pre-copy] Description=The specified container does not exist.
[AzCopy pre-copy] RequestId:5fb674b9-201e-001b-2a5b-527400000000
[AzCopy pre-copy] Time:2021-05-26T18:18:07.5931967Z, Details: 
[AzCopy pre-copy] Code: ContainerNotFound
```

Wenn bei AzCopy ein Problem auftritt, schlägt die Extraktion sofort fehl, und die Extraktionsprotokolle enthalten Details zum Fehler.

Blobs, die vor dem Fehler kopiert wurden, werden von AzCopy bei nachfolgenden Ausführungen automatisch übersprungen und müssen nicht erneut kopiert werden.

#### Für Dateidatenspeicher {#file-data-store-extract}

Wenn AzCopy für „dataStore“ der Quelldatei benutzt wird, sollten Meldungen wie diese in den Protokollen angezeigt werden, die darauf hinweisen, dass Ordner verarbeitet werden:
`c.a.g.s.m.c.a.AzCopyFileSourceBlobPreCopy - [AzCopy pre-copy] Processing folder (1/24) crx-quickstart/repository/datastore/5d`

### 5. Aufnehmen mit AzCopy {#ingesting-azcopy}

Siehe [Erfassen von Inhalten in Target](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md)
mit allgemeinen Informationen zur Aufnahme von Inhalten in das Ziel vom Cloud Acceleration Manager (CAM), einschließlich 
Anweisungen zur Verwendung von AzCopy (Vor-Kopie) – oder nicht – im Dialogfeld „Neue Aufnahme“

Um AzCopy während der Erfassung nutzen zu können, müssen Sie für Adobe eine AEM as a Cloud Service Version verwenden, die mindestens Version 2021.6.5561 ist.

Sehen Sie sich die Liste &quot;Aufnahmevorgänge&quot;im Cloud Acceleration Manager und die Protokolle der Aufnahme an, um den Fortschritt anzuzeigen. Die Protokolleinträge für die erfolgreichen AzCopy-Aufgaben werden wie folgt angezeigt (wobei einige Unterschiede berücksichtigt werden). Wenn Sie die Protokolle gelegentlich überprüfen, können sie 
frühzeitig Probleme aufzeigen und es kann Ihnen helfen, eine schnelle Lösung für alle Probleme zu finden.

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

## So geht es weiter {#whats-next}

Sie haben jetzt über den Umgang mit großen Inhaltsverzeichnissen gelernt, um die Extraktions- und Aufnahmephasen der Inhaltstransferaktivität zu beschleunigen und Inhalte auf AEM as a Cloud Service zu verschieben. Sie können jetzt den Extraktionsvorgang mit dem Content Transfer Tool erlernen. Siehe [Extrahieren von Inhalt aus einer Quelle im Content Transfer Tool](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md) , damit Sie erfahren können, wie Sie Ihren Migrationssatz aus dem Content Transfer Tool extrahieren.
