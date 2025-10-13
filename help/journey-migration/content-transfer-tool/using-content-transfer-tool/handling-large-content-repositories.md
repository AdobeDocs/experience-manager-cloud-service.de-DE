---
title: Handhabung großer Content-Repositorys
description: In diesem Abschnitt wird die Handhabung großer Content-Repositorys beschrieben.
exl-id: 21bada73-07f3-4743-aae6-2e37565ebe08
feature: Migration
role: Admin
source-git-commit: b729c07c78519cd9b6536a0dd142aa8ed01d2a22
workflow-type: ht
source-wordcount: '1842'
ht-degree: 100%

---

# Handhabung großer Content-Repositorys {#handling-large-content-repositories}

## Überblick {#overview}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_precopy"
>title="Handhabung großer Content-Repositorys"
>abstract="Um die Extraktions- und Aufnahmephasen der Aktivität zur Inhaltsübertragung erheblich zu beschleunigen und Inhalte zu Adobe Experience Manager as a Cloud Service zu verschieben, kann das Content Transfer Tool (CTT) AzCopy als optionalen Schritt vor dem Kopieren nutzen. Sobald dieser Vorschritt konfiguriert ist, kopiert AzCopy in der Extraktionsphase Blobs aus Amazon S3 oder Azure Blob Storage in den Migrationssatz-Blob-Speicher. In der Aufnahmephase kopiert AzCopy Blobs aus dem Migrationssatz-Blob-Speicher in den Ziel-Blob-Speicher von Adobe Experience Manager as a Cloud Service."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=de#setting-up-pre-copy-step" text="Erste Schritte mit AzCopy als Vorkopieschritt"

Eine große Anzahl von Blobs mit dem Content Transfer Tool (CTT) zu kopieren, kann mehrere Tage dauern.
Um die Extraktions- und Aufnahmephasen des Inhaltstransfers zu beschleunigen und Inhalte zu AEM as a Cloud Service zu verschieben, kann CTT [AzCopy](https://learn.microsoft.com/de-de/azure/storage/common/storage-use-azcopy-v10) als optionalen Schritt vor dem Kopiervorgang nutzen. Dieser Schritt für eine Vorabkopie kann erfolgen, wenn die AEM-Quellinstanz für die Verwendung eines Amazon S3-Datenspeichers, Azure Blob Storage-Datenspeichers oder Dateidatenspeichers konfiguriert ist. Der Schritt der Vorabkopie ist am effektivsten bei der ersten vollständigen Extraktion und Aufnahme. Die Verwendung der Vorabkopie für nachfolgende Auffüllungen wird jedoch nicht empfohlen (wenn die Auffüllgröße weniger als 200 GB beträgt), da dies den gesamten Prozess verlängern kann. Sobald dieser Vorschritt konfiguriert ist, kopiert AzCopy in der Extraktionsphase Blobs aus dem Amazon S3-, Azure Blob Storage- oder Dateidatenspeicher in den Migrationssatz-Blob-Speicher. In der Aufnahmephase kopiert AzCopy Blobs aus dem Migrationssatz-Blob-Speicher in den Ziel-Blob-Speicher von Adobe Experience Manager as a Cloud Service.

## Wichtige Vorüberlegungen {#important-considerations}

Im folgenden Abschnitt finden Sie wichtige Überlegungen, die Sie berücksichtigen sollten, bevor Sie beginnen:

* Ab Version 2.0.16 von CTT erfolgt die Einrichtung der Vorabkopie-Funktion automatisch, wenn das Paket installiert wird. Wenn der Migrationssatz größer als 200 GB ist, nutzt der Extraktionsprozess außerdem automatisch die Vorabkopie-Funktion. Die Datei „azcopy.config“ wird im Verzeichnis „crx-quickstart/cloud-migration/“ erstellt. Wenn Sie CTT-Version 2.0.16 oder höher verwenden, müssen Sie das Precopy-Setup nicht manuell durchführen.

* Die AEM-Quellversion muss 6.3 bis 6.5 sein.

* Der AEM-Quelldatenspeicher ist für die Verwendung von Amazon S3 oder Azure Blob Storage konfiguriert. Weitere Informationen finden Sie unter [Konfigurieren von Knotenspeichern und Datenspeichern in AEM 6](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/data-store-config.html?lang=de).

* Jeder Migrationssatz kopiert den gesamten Datenspeicher. Daher sollte nur ein einziger Migrationssatz verwendet werden.

* Sie benötigen Zugriffsrechte, um [AzCopy](https://learn.microsoft.com/de-de/azure/storage/common/storage-use-azcopy-v10) in der Instanz (oder VM) zu installieren, auf der die AEM-Quellinstanz ausgeführt wird.

* Die Datenspeicherbereinigung wurde innerhalb der letzten sieben Tage für die Quelle ausgeführt. Weitere Informationen finden Sie unter [Datenspeicherbereinigung](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/data-store-config.html?lang=de#data-store-garbage-collection).

### Weitere Aspekte, falls die AEM-Quellinstanz für die Verwendung eines Amazon S3- oder Azure Blob Storage-Datenspeichers konfiguriert ist {#additional-considerations-amazons3-azure}

* Mit der Übertragung von Daten aus Amazon S3 und Azure Blob Storage sind Kosten verbunden. Die Übertragungskosten hängen von der Gesamtmenge der Daten in Ihrem vorhandenen Speicher-Container ab (unabhängig davon, ob in AEM darauf verwiesen wird oder nicht). Weitere Informationen finden Sie unter [Amazon S3](https://aws.amazon.com/s3/pricing/) und [Azure Blob Storage](https://azure.microsoft.com/de-de/pricing/details/bandwidth/).

* Sie benötigen entweder einen Zugriffsschlüssel und ein geheimes Schlüsselpaar für den vorhandenen Amazon S3-Bucket oder einen SAS-URI für den vorhandenen Azure Blob Storage-Container (Lesezugriff ist ausreichend).

### Weitere Aspekte, falls die AEM-Quellinstanz für die Verwendung des Dateidatenspeichers konfiguriert ist {#additional-considerations-aem-instance-filedatastore}

* Das lokale System muss über freien Speicherplatz verfügen, der zwingend größer als 1/256 der Größe des Quelldatenspeichers ist. Wenn die Größe des Datenspeichers zum Beispiel 3 Terabyte beträgt, muss quellseitig im Ordner `crx-quickstart/cloud-migration` mehr als 11,72 GB freier Speicher vorhanden sein, damit AzCopy funktioniert. Das Quellsystem sollte mindestens über 1 GB freien Speicherplatz verfügen. Freier Speicherplatz kann mit dem Befehl `df -h` in Linux®-Instanzen und dem Befehl „dir“ in Windows-Instanzen geschaffen werden.

* Bei jeder Extraktion mit aktiviertem AzCopy wird der gesamte Dateidatenspeicher reduziert und in den Cloud-Migrations-Container kopiert. Wenn Ihr Migrationssatz kleiner ist Ihr Datenspeicher, ist die AzCopy-Extraktion nicht der optimale Ansatz.

* Wenn die AzCopy-Funktion zum Kopieren über den vorhandenen Datenspeicher verwendet wurde, deaktivieren Sie diese für Delta- oder Auffüllextraktionen.

## Einrichten zur Verwendung von AzCopy als Vorkopieschritt {#setting-up-pre-copy-step}

>[!NOTE]
>Ab Version 2.0.16 von CTT erfolgt die Einrichtung der Vorabkopie-Funktion automatisch, wenn das Paket installiert wird. Wenn der Migrationssatz größer als 200 GB ist, nutzt der Extraktionsprozess außerdem automatisch die Vorabkopie-Funktion. Die Datei „azcopy.config“ wird im Verzeichnis „crx-quickstart/cloud-migration/“ erstellt. Wenn Sie die Konfiguration der Datei manuell aktualisieren möchten, finden Sie nachstehend weitere Informationen dazu.

In diesem Abschnitt erfahren Sie, wie Sie bei der Einrichtung vorgehen müssen, um AzCopy als Vorabkopieschritt mit dem Content Transfer Tool zu verwenden und Inhalte zu AEM as a Cloud Service migrieren:

### &#x200B;0. Bestimmen der Gesamtgröße aller Inhalte im Datenspeicher {#determine-total-size}

Es ist aus zwei Gründen wichtig, die Gesamtgröße des Datenspeichers zu bestimmen:

* Wenn die AEM-Quelle für die Verwendung des Dateidatenspeichers konfiguriert ist, muss das lokale System über freien Speicherplatz verfügen, der zwingend größer als 1/256 des Quelldatenspeichers ist.

#### Azure Blob-Speicher – Datenspeicher {#azure-blob-storage}

Verwenden Sie auf der Seite mit den Container-Eigenschaften im Azure-Portal die Schaltfläche **Größe berechnen**, um die Gesamtgröße aller Container-Inhalte zu bestimmen. Beispiel:

![image](/help/journey-migration/content-transfer-tool/assets/Azure-blob-storage-data-store.png)

#### Amazon S3-Datenspeicher {#amazon-data}

Auf der Registerkarte zu den Metriken des Containers können Sie die Gesamtgröße der Inhalte des Containers bestimmen. Beispiel:


![image](/help/journey-migration/content-transfer-tool/assets/amazon-s3-data-store.png)

#### Dateidatenspeicher {#file-data-store-determine-size}

* Führen Sie bei Mac- und UNIX®-Systemen den Befehl „du“ im Datenspeicherverzeichnis aus, um dessen Größe abzurufen:
  `du -sh [path to datastore on the instance]`. Wenn sich Ihr Datenspeicher beispielsweise unter `/mnt/author/crx-quickstart/repository/datastore` befindet, liefert der folgende Befehl dessen Größe: `du -sh /mnt/author/crx-quickstart/repository/datastore`.

* Für Windows verwenden Sie den Befehl „dir“ im Datenspeicherverzeichnis, um dessen Größe zu erhalten:
  `dir /a/s [location of datastore]`.

### &#x200B;1. Installieren von AzCopy {#install-azcopy}

[AzCopy](https://learn.microsoft.com/de-de/azure/storage/common/storage-use-azcopy-v10) ist ein von Microsoft® bereitgestelltes Befehlszeilen-Tool, das in der Quellinstanz verfügbar sein muss, um diese Funktion zu aktivieren.

Es empfiehlt sich also, die Linux® x86-64-Binärdatei von der [Seite mit der AzCopy-Dokumentation](https://learn.microsoft.com/de-de/azure/storage/common/storage-use-azcopy-v10) herunterzuladen und sie an einem Speicherort wie „/usr/bin“ zu entpacken.

>[!IMPORTANT]
>Notieren Sie sich, wo Sie die Binärdatei gespeichert haben, da Sie in einem späteren Schritt den vollständigen Speicherpfad benötigen.

### &#x200B;2. Installieren einer Version des Content Transfer Tool (CTT) mit AzCopy-Unterstützung {#install-ctt-azcopy-support}

>[!IMPORTANT]
>Es sollte die neueste Version von CTT verwendet werden.

AzCopy-Unterstützung für Amazon S3, Azure Blob Storage und Dateidatenspeicher ist in der neuesten CTT-Version enthalten.
Sie können die neueste Version von CTT vom [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)-Portal herunterladen.
Beachten Sie, dass nur die Versionen 2.0.0 und höher unterstützt werden und es ratsam ist, die neueste Version zu verwenden.

### &#x200B;3. Konfigurieren der Datei „azcopy.config“ {#configure-azcopy-config-file}

Erstellen Sie eine neue Datei mit dem Namen `azcopy.config` in der AEM-Quellinstanz unter `crx-quickstart/cloud-migration`.

>[!NOTE]
>Der Inhalt dieser Konfigurationsdatei unterscheidet sich, je nachdem, ob Ihre AEM-Quellinstanz einen Azure- bzw. Amazon S3-Datenspeicher oder einen Dateidatenspeicher verwendet.

#### Azure Blob Storage-Datenspeicher {#azure-blob-storage-data}

Ihre Datei „azcopy.config“ sollte die folgenden Eigenschaften enthalten (stellen Sie sicher, dass Sie den richtigen AzCopyPath- und AzureSas-Parameter für Ihre Instanz verwenden).

>[!NOTE]
>
> Wenn Sie keinen Schreibzugriff auf den vorhandenen Blob-Speicher-Container gewähren möchten, können Sie einen neuen SAS-URI generieren, der nur über Lese- und Listenberechtigungen verfügt.

```
azCopyPath=/usr/bin/azcopy
azureSas=https://example-resource.blob.core.windows.net/example-container?sig=--REDACTED--
```

#### Amazon S3-Datenspeicher {#amazon-sdata-store}

Ihre Datei „azcopy.config“ sollte die folgenden Eigenschaften enthalten (stellen Sie sicher, dass Sie die richtigen Werte für Ihre Instanz verwenden).

>[!NOTE]
>
> Wenn Ihre Instanz IAM-Rollen verwendet, um AEM Zugriff auf S3 zu ermöglichen, müssen Sie eine Richtlinie und eine Benutzerin bzw. einen Benutzer erstellen. Dabei müssen die ListBucket- und GetObject-Aktionen für den S3-Bucket aktiviert sein. Verwenden Sie nach der Einrichtung den Zugriffsschlüssel und den geheimen Schlüssel dieser Benutzerin bzw. dieses Benutzers.

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

Die Eigenschaft „azCopyPath“ muss den vollständigen Pfad des Speicherorts enthalten, an dem das Befehlszeilen-Tool „azCopy“ in der AEM-Quellinstanz installiert ist. Wenn die Eigenschaft „azCopyPath“ fehlt, wird der Schritt „blob precopy“ nicht ausgeführt.

Wenn die Eigenschaft `repository.home` in „azcopy.config“ fehlt, wird der standardmäßige Datenspeicherort `/mnt/crx/author/crx-quickstart/repository/datastore` verwendet, um eine Vorabkopie durchzuführen.

### &#x200B;4. Extrahieren mit AzCopy {#extracting-azcopy}

Mit der obigen Konfigurationsdatei wird die AzCopy-Vorabkopierphase als Teil aller nachfolgenden Extraktionen ausgeführt. Um die Ausführung zu verhindern, können Sie diese Datei umbenennen oder entfernen.

>[!NOTE]
>Wenn AzCopy nicht richtig konfiguriert ist, wird folgende Meldung in den Protokollen angezeigt:
>>`INFO c.a.g.s.m.c.a.AzCopyCloudBlobPreCopy - Blob pre-copy is not supported`.

1. Starten Sie eine Extraktion über die CTT-Benutzeroberfläche. Weitere Informationen finden Sie unter [Erste Schritte mit dem Content Transfer Tool](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/getting-started-content-transfer-tool.md) und [Extraktionsvorgang](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md).

1. Vergewissern Sie sich, dass das Extraktionsprotokoll die folgende Zeile aufweist:

```
c.a.g.s.m.commons.ContentExtractor - *************** Beginning AzCopy Pre-Copy phase ***************
```

Herzlichen Glückwunsch! Dieser Protokolleintrag bedeutet, dass Ihre Konfiguration als gültig betrachtet wird und dass AzCopy alle Blobs aus dem Quell-Container in den Migrations-Container kopiert.

Die Protokolleinträge von AzCopy werden im Extraktionsprotokoll angezeigt und sind mit dem Präfix „c.a.g.s.m.c.azcopy.AzCopyBlobPreCopy – [AzCopy pre-copy]“ versehen.

>[!CAUTION]
>
> Achten Sie in den ersten Minuten einer Extraktion auf etwaige Anzeichen eines Problems in den Extraktionsprotokollen. Das folgende Beispiel zeigt, was protokolliert wird, wenn der Azure-Quellcontainer nicht gefunden werden kann:

```
[AzCopy pre-copy] failed to perform copy command due to error: cannot start job due to error: cannot list files due to reason > github.com/Azure/azure-storage-blob-go/azblob.newStorageError, github.com/Azure/azure-storage-blob-go@v0.10.1-0.20210407023846-16cf969ec1c3/azblob/zc_storage_error.go:42
[AzCopy pre-copy] ===== RESPONSE ERROR (ServiceCode=ContainerNotFound) =====
[AzCopy pre-copy] Description=The specified container does not exist.
[AzCopy pre-copy] RequestId:5fb674b9-201e-001b-2a5b-527400000000
[AzCopy pre-copy] Time:2021-05-26T18:18:07.5931967Z, Details: 
[AzCopy pre-copy] Code: ContainerNotFound
```

Bei einem Prolem mit AzCopy schlägt die Extraktion sofort fehl. Die Extraktionsprotokolle enthalten in diesem Fall Details zu dem Fehler.

Blobs, die vor Auftreten des Fehlers kopiert wurden, werden von AzCopy bei nachfolgenden Ausführungen automatisch übersprungen und müssen nicht erneut kopiert werden.

>[!TIP]
>Eine Aufnahme kann nun so geplant werden, dass sie unmittelbar nach erfolgreichem Abschluss einer Extraktion automatisch startet. Siehe [Aufnehmen von Inhalten in das Ziel](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md) für weitere Informationen.

>[!TIP]
>Wenn die Blob-Übertragung mit AzCopy eine Weile ausgeführt wird, dann aber nur für einige Blobs fehlschlägt, führen Sie die Extraktion bei deaktivierten Optionen „PreCopy“ und „Staging-Container überschreiben“ aus. Dadurch werden nur die verbleibenden Blobs migriert, die zuvor nicht übertragen wurden.

#### Für Dateidatenspeicher {#file-data-store-extract}

Wenn AzCopy für „dataStore“ der Quelldatei benutzt wird, sollten Meldungen wie diese in den Protokollen angezeigt werden, die darauf hinweisen, dass Ordner verarbeitet werden:
`c.a.g.s.m.c.a.AzCopyFileSourceBlobPreCopy - [AzCopy pre-copy] Processing folder (1/24) crx-quickstart/repository/datastore/5d`

### &#x200B;5. Aufnehmen mit AzCopy {#ingesting-azcopy}

Unter [Aufnehmen von Inhalten in das Ziel](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md) finden Sie allgemeine Informationen zum Aufnehmen von Inhalten in das Ziel über das Dialogfeld „Neue Aufnahme“ in Cloud Acceleration Manager (CAM), darunter Anweisungen zum Verwenden von AzCopy (Vorabkopie).

Um AzCopy während der Aufnahme nutzen zu können, müssen Sie gemäß Adobe-Anforderungen mindestens Version 2021.6.5561 von AEM as a Cloud Service verwenden.

In der Liste „Aufnahmevorgänge“ in Cloud Acceleration Manager und in den Aufnahmeprotokollen finden Sie Informationen zum Fortschritt. Die Protokolleinträge für erfolgreiche
AzCopy-Aufgaben werden wie folgt angezeigt (gewisse Unterschiede möglich). Wenn Sie die Protokolle gelegentlich überprüfen, können sie 
frühzeitig Probleme aufzeigen und es kann Ihnen helfen, eine schnelle Lösung für alle Probleme zu finden.

```
*************** Beginning AzCopy pre-copy phase ***************
INFO: Scanning...
INFO: Failed to create one or more destination container(s). Your transfers may still succeed if the container already exists.
INFO: Any empty folders will not be processed, because source and/or destination does not have full folder support
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

Sie haben sich jetzt mit der Handhabung großer Inhalts-Repositorys vertraut gemacht, um die Extraktions- und Aufnahmephasen der Inhaltsübertragung zum Verschieben von Inhalten zu AEM as a Cloud Service zu beschleunigen. Sie sind nun bereit, den Extraktionsvorgang mit dem Content Transfer Tool kennenzulernen. Unter [Extrahieren von Inhalten aus der Quelle im Content Transfer Tool](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md) erfahren Sie, wie Sie Ihren Migrationssatz aus dem Content Transfer Tool extrahieren können.
