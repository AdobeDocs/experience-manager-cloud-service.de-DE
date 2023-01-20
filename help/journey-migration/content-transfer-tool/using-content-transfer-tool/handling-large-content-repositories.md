---
title: Handhabung großer Content-Repositorys
description: In diesem Abschnitt wird die Handhabung großer Content-Repositorys beschrieben.
exl-id: 21bada73-07f3-4743-aae6-2e37565ebe08
source-git-commit: 7a9c601dd42aed9fbd0113e71c1c7a58b5bba8f7
workflow-type: ht
source-wordcount: '1732'
ht-degree: 100%

---

# Handhabung großer Content-Repositorys {#handling-large-content-repositories}

## Übersicht {#overview}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_precopy"
>title="Handhabung großer Content-Repositorys"
>abstract="Um die Extraktions- und Aufnahmephasen der Aktivität zum Content-Transfer erheblich zu beschleunigen und Inhalte zu Adobe Experience Manager as a Cloud Service zu verschieben, kann das Content Transfer Tool (CTT) AzCopy als optionalen Vorkopieschritt nutzen. Sobald dieser Vorschritt konfiguriert ist, kopiert AzCopy Blobs aus Amazon S3 oder Azure Blob Storage in den Migrationssatz-Blob-Speicher. In der Aufnahmephase kopiert AzCopy Blobs aus dem Migrationssatz-Blob-Speicher in den Ziel-Blob-Speicher von Adobe Experience Manager as a Cloud Service."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=de#setting-up-pre-copy-step" text="Erste Schritte mit AzCopy als Vorkopieschritt"

Das Kopieren einer großen Anzahl von Blobs mit dem CTT kann mehrere Tage dauern.
Um die Extraktions- und Aufnahmephasen der Aktivität zum Content-Transfer erheblich zu beschleunigen und Inhalte zu Adobe Experience Manager as a Cloud Service zu verschieben, kann das CTT [AzCopy](https://docs.microsoft.com/de-de/azure/storage/common/storage-use-azcopy-v10) als optionalen Vorkopieschritt nutzen. Dieser Schritt für eine Vorabkopie kann erfolgen, wenn die AEM-Quellinstanz für die Verwendung eines Amazon S3-Datenspeichers, Azure Blob Storage-Datenspeichers oder Dateidatenspeichers konfiguriert ist. Der Schritt der Vorabkopie ist am effektivsten für die erste vollständige Extraktion und Aufnahme. Die Verwendung der Vorabkopie für nachfolgende Auffüllungen wird jedoch nicht empfohlen (wenn die Auffüllgröße weniger als 200 GB beträgt), da dies den gesamten Prozess verlängern kann. Sobald dieser Vorschritt konfiguriert ist, kopiert AzCopy in der Extrahierungsphase Blobs aus dem Amazon S3-, Azure Blob Storage- oder Dateidatenspeicher in den Migrationssatz-Blob-Speicher. In der Aufnahmephase kopiert AzCopy Blobs aus dem Migrationssatz-Blob-Speicher in den Ziel-Blob-Speicher von Adobe Experience Manager as a Cloud Service.

## Wichtige Vorüberlegungen {#important-considerations}

Im folgenden Abschnitt finden Sie wichtige Überlegungen, die Sie berücksichtigen sollten, bevor Sie beginnen:

* Die AEM-Quellversion muss 6.3 bis 6.5 sein..

* Der AEM-Quelldatenspeicher ist für die Verwendung von Amazon S3 oder Azure Blob Storage konfiguriert. Weitere Informationen finden Sie unter [Konfigurieren von Knotenspeichern und Datenspeichern in AEM 6](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/data-store-config.html?lang=de).

* Jeder Migrationssatz kopiert den gesamten Datenspeicher. Daher sollte nur ein einziger Migrationssatz verwendet werden.

* Sie benötigen Zugriffsrechte, um [AzCopy](https://docs.microsoft.com/de-de/azure/storage/common/storage-use-azcopy-v10) in der Instanz (oder VM) zu installieren, auf der die AEM-Quellinstanz ausgeführt wird.

* Die Speicherbereinigung wurde innerhalb der letzten sieben Tage für die Quelle ausgeführt. Weitere Informationen finden Sie unter [Speicherbereinigung](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/data-store-config.html?lang=de#data-store-garbage-collection).


### Weitere Aspekte, falls die AEM-Quellinstanz für die Verwendung eines Amazon S3- oder Azure Blob Storage-Datenspeichers konfiguriert ist {#additional-considerations-amazons3-azure}

* Da mit der Übertragung von Daten sowohl aus dem Amazon S3- als auch dem Azure Blob-Speicher Kosten verbunden sind, hängen die Übertragungskosten von der Gesamtmenge der Daten im Speicher-Container ab (unabhängig davon, ob dieser in AEM referenziert ist). Weitere Informationen finden Sie unter [Amazon S3](https://aws.amazon.com/s3/pricing/) und [Azure Blob-Speicher](https://azure.microsoft.com/de-de/pricing/details/bandwidth/).

* Sie benötigen entweder einen Zugriffsschlüssel und ein geheimes Schlüsselpaar für den Amazon S3-Bucket oder einen SAS-URI für den Azure Blob-Speicher-Container (Lesezugriff ist ausreichend).

### Weitere Aspekte, falls die AEM-Quellinstanz für die Verwendung des Dateidatenspeichers konfiguriert ist {#additional-considerations-aem-instance-filedatastore}

* Das lokale System muss über freien Speicherplatz verfügen, der zwingend größer als 1/256 der Größe des Quelldatenspeichers ist. Wenn die Größe des Datenspeichers zum Beispiel 3 TB beträgt, muss im `crx-quickstart/cloud-migration`-Ordner mehr als 11,72 GB freier Speicher auf der Quelle vorhanden sein, damit AzCopy funktioniert. Das Quellsystem sollte mindestens über 1 GB freien Speicherplatz verfügen. Freier Speicherplatz kann mit dem `df -h`-Befehl in Linux-Instanzen und dem dir-Befehl in den Windows-Instanzen geschaffen werden.

* Bei jeder Extraktion mit aktiviertem AzCopy wird der gesamte Dateidatenspeicher reduziert und in den Cloud-Migrations-Container kopiert. Wenn Ihr Migrationssatz erheblich kleiner ist als die Größe Ihres Datenspeichers, ist die AzCopy-Extraktion nicht der optimale Ansatz.

* Wenn die AzCopy-Funktion zum Kopieren über den vorhandenen Datenspeicher verwendet wurde, deaktivieren Sie diese für Delta- oder Auffüllextraktionen.

## Einrichten zur Verwendung von AzCopy als Vorkopieschritt {#setting-up-pre-copy-step}

In diesem Abschnitt erfahren Sie, wie Sie bei der Einrichtung vorgehen müssen, um AzCopy als Vorkopieschritt mit dem Content Transfer Tool zu verwenden und Inhalte zu AEM as a Cloud Service migrieren:

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

* Bei Mac- und UNIX-Systemen führen Sie den Befehl „du“ auf dem Datenspeicherordner aus, um dessen Größe zu erhalten:
   `du -sh [path to datastore on the instance]`. Wenn sich Ihr Datenspeicher beispielsweise unter `/mnt/author/crx-quickstart/repository/datastore` befindet, liefert der folgende Befehl dessen Größe: `du -sh /mnt/author/crx-quickstart/repository/datastore`.

* Für Windows verwenden Sie den Befehl „dir“ im Datenspeicherverzeichnis, um dessen Größe zu erhalten:
   `dir /a/s [location of datastore]`.

### 1. Installieren von AzCopy {#install-azcopy}

[AzCopy](https://docs.microsoft.com/de-de/azure/storage/common/storage-use-azcopy-v10) ist ein von Microsoft bereitgestelltes Befehlszeilen-Tool, das in der Quellinstanz verfügbar sein muss, um diese Funktion zu aktivieren.

Es empfiehlt sich also, die Linux-x86-64-Binärdatei von der [AzCopy-Dokumentationsseite](https://docs.microsoft.com/de-de/azure/storage/common/storage-use-azcopy-v10) herunterzuladen und sie an einem Speicherort wie z. B. /usr/bin zu entpacken.

>[!IMPORTANT]
>Notieren Sie sich, wo Sie die Binärdatei gespeichert haben, da Sie in einem späteren Schritt den vollständigen Speicherpfad benötigen.

### 2. Installieren einer Version des Content Transfer Tool (CTT) mit AzCopy-Unterstützung {#install-ctt-azcopy-support}

>[!IMPORTANT]
>Es sollte die neueste Version von CTT verwendet werden.

AzCopy-Unterstützung für Amazon S3, Azure Blob-Speicher und Dateidatenspeicher ist in der neuesten CTT-Version enthalten.
Sie können die neueste Version von CTT vom [Software Distribution-Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) herunterladen.


### 3. Konfigurieren der Datei „azcopy.config“ {#configure-azcopy-config-file}

Erstellen Sie eine neue Datei mit dem Namen `azcopy.config` in der AEM-Quellinstanz unter `crx-quickstart/cloud-migration`.

>[!NOTE]
>Der Inhalt dieser Konfigurationsdatei unterscheidet sich, je nachdem, ob Ihre AEM-Quellinstanz einen Azure- oder Amazon S3-Dateidatenspeicher verwendet.

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
> Wenn Ihre Instanz IAM-Rollen verwendet, um AEM Zugriff auf S3 zu ermöglichen, müssen Sie eine Richtlinie und einen Anwender erstellen, für die die ListBucket- und GetObject-Aktionen für den S3-Bucket aktiviert sind. Verwenden Sie nach der Einrichtung den Zugriffsschlüssel und den geheimen Schlüssel dieses Anwenders.

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

Die Eigenschaft „azcopyPath“ muss den vollständigen Pfad des Speicherorts enthalten, an dem das Befehlszeilen-Tool „azCopy“ auf der AEM-Quellinstanz installiert ist. Wenn die Eigenschaft „azcopyPath“ fehlt, wird kein Schritt „blob precopy“ ausgeführt.

Wenn die Eigenschaft `repository.home` in „azcopy.config“ fehlt, wird der standardmäßige Datenspeicherort `/mnt/crx/author/crx-quickstart/repository/datastore` verwendet, um eine Vorabbearbeitung durchzuführen.

### 4. Extrahieren mit AzCopy {#extracting-azcopy}

Mit der obigen Konfigurationsdatei wird die AzCopy-Vorkopierphase als Teil aller nachfolgenden Extraktionen ausgeführt. Um die Ausführung zu verhindern, können Sie diese Datei umbenennen oder entfernen.

>[!NOTE]
>Wenn AzCopy nicht richtig konfiguriert ist, wird diese Meldung in den Protokollen angezeigt:
>`INFO c.a.g.s.m.c.a.AzCopyCloudBlobPreCopy - Blob pre-copy is not supported`.

1. Starten Sie eine Extraktion über die CTT-Benutzeroberfläche. Weitere Informationen finden Sie unter [Erste Schritte mit dem Content Transfer Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=de) und [Extraktionsvorgang](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/extracting-content.html?lang=de).

1. Vergewissern Sie sich, dass das Extraktionsprotokoll die folgende Zeile aufweist:

```
c.a.g.s.m.commons.ContentExtractor - *************** Beginning AzCopy Pre-Copy phase ***************
```

Herzlichen Glückwunsch! Dieser Protokolleintrag bedeutet, dass Ihre Konfiguration als gültig betrachtet wurde und dass AzCopy derzeit alle Blobs aus dem Quell-Container in den Migration-Container kopiert.

Die Protokolleinträge von AzCopy werden im Extraktionsprotokoll angezeigt und sind mit dem Präfix „c.a.g.s.m.c.azcopy.AzCopyBlobPreCopy - [AzCopy pre-copy]“ versehen.

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

Im Fall eines Problems mit AzCopy schlägt die Extraktion sofort fehl, und die Extraktionsprotokolle enthalten Details zum Fehler.

Blobs, die vor Auftreten des Fehlers kopiert wurden, werden von AzCopy bei nachfolgenden Ausführungen automatisch übersprungen und müssen nicht erneut kopiert werden.

#### Für Dateidatenspeicher {#file-data-store-extract}

Wenn AzCopy für „dataStore“ der Quelldatei benutzt wird, sollten Meldungen wie diese in den Protokollen angezeigt werden, die darauf hinweisen, dass Ordner verarbeitet werden:
`c.a.g.s.m.c.a.AzCopyFileSourceBlobPreCopy - [AzCopy pre-copy] Processing folder (1/24) crx-quickstart/repository/datastore/5d`

### 5. Aufnehmen mit AzCopy {#ingesting-azcopy}

Siehe [Erfassen von Inhalten in Target](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/ingesting-content.html?lang=de)
mit allgemeinen Informationen zur Aufnahme von Inhalten in das Ziel vom Cloud Acceleration Manager (CAM), einschließlich 
Anweisungen zur Verwendung von AzCopy (Vor-Kopie) – oder nicht – im Dialogfeld „Neue Aufnahme“

Um AzCopy während der Aufnahme nutzen zu können, müssen Sie eine Version von AEM as a Cloud Service ab Version 2021.6.5561 verwenden.

In der Liste „Aufnahmen von Aufträgen“ im Cloud Acceleration Manager finden Sie Informationen zum Fortschritt in den Protokollen der Aufnahme.  Die Protokolleinträge für die erfolgreichen
 AzCopy-Aufgaben werden wie folgt angezeigt (wobei einige Unterschiede berücksichtigt werden). Wenn Sie die Protokolle gelegentlich überprüfen, können sie 
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

Nun, da Sie mit dem Umgang mit großen Content-Repositorys vertraut sind, um die Extraktions- und Aufnahmephasen der Aktivität „Inhaltsübertragung“ erheblich zu beschleunigen und Inhalte auf AEM as a Cloud Service zu verschieben, können Sie jetzt den Extraktionsprozess unter Verwendung des Content-Übertragungs-Tools erlernen. Unter [Extrahieren von Inhalten aus der Quelle im Content Transfer Tool](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md) erfahren Sie, wie Sie Ihren Migrationssatz aus dem Content Transfer Tool extrahieren können.
