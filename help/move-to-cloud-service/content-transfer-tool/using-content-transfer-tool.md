---
title: Verwenden des Content Transfer-Tools
description: Verwenden des Content Transfer-Tools
translation-type: tm+mt
source-git-commit: 01ffc349891ac1e11af4f4bc8a539069b8f6cd5e
workflow-type: tm+mt
source-wordcount: '1617'
ht-degree: 97%

---


# Verwenden des Content Transfer-Tools {#using-content-transfer-tool}

## Wichtige Überlegungen zur Verwendung des Content Transfer-Tools {#pre-reqs}

Im folgenden Abschnitt finden Sie wichtige Überlegungen zur Verwendung des Content Transfer-Tools:

* Die Mindest-Systemanforderungen für das Content Transfer-Tool sind AEM 6.3 + und JAVA 8. Wenn Sie eine niedrigere AEM-Version verwenden, müssen Sie Ihr Content-Repository auf AEM 6.5 aktualisieren, um das Content Transfer-Tool verwenden zu können.

* Das Content Transfer Tool kann mit den folgenden Arten des Datenspeichers verwendet werden: Dateidatenspeicher, S3-Datenspeicher und freigegebener S3-Datenspeicher. Derzeit unterstützt es keine Azurblase Store Data Store.

* Wenn Sie eine *Sandbox-Umgebung* verwenden, stellen Sie sicher, dass Ihre Umgebung auf die Version vom 10. Juni 2020 oder höher aktualisiert ist. Wenn Sie eine *Produktionsumgebung* verwenden, wird diese automatisch aktualisiert.

* Um das Content Transfer-Tool verwenden zu können, müssen Sie ein Administrator-Benutzer in Ihrer Quellinstanz sein und zur AEM-Administratorengruppe in der Cloud Service-Instanz gehören, an die Sie Inhalte übertragen. Unberechtigte Benutzer können das Zugriffs-Token zur Verwendung des Content Transfer-Tools nicht abrufen.

* Während der Extraktionsphase wird das Content Transfer-Tool in einer aktiven AEM-Quellinstanz ausgeführt.

* In der *Aufnahmephase* für die Autoreninstanz wird die gesamte Autorenimplementierung herabgesetzt. In anderen Worten, die Autoreninstanz von AEM ist während des gesamten Aufnahmevorgangs nicht verfügbar.

* Die empfohlene Obergrenze für die Repository-Größe, die das Content Transfer-Tool gleichzeitig unterstützen kann, beträgt 20 GB.

## Verfügbarkeit {#availability}

Das Content Transfer-Tool kann als ZIP-Datei (Content Transfer Tool v1.0.0) vom Software Distribution-Portal heruntergeladen werden. Sie können das Paket über Package Manager in Ihrer Quelldistanz von Adobe Experience Manager (AEM) installieren.

>[!NOTE]
>Laden Sie das Content Transfer-Tool vom [Software Distribution-Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) herunter.

## Ausführen des Content Transfer-Tools {#running-tool}

>[!VIDEO](https://video.tv.adobe.com/v/35460/?quality=12&learn=on)

In diesem Abschnitt erfahren Sie, wie Sie mit dem Content Transfer-Tool Inhalte zu AEM as a Cloud Service (Autor/Veröffentlichung) migrieren:

1. Wählen Sie Adobe Experience Manager aus und navigieren Sie zu Tools > **Vorgänge** > **Inhaltstransfer**.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/content1.png)

1. Klicken Sie auf **Migrationssatz erstellen**, um einen neuen Migrationssatz zu erstellen. Die **Details zum Inhaltsmigrationssatz** werden angezeigt.

   >[!NOTE]
   >Auf diesem Bildschirm sehen Sie die vorhandenen Migrationssätze mit ihrem aktuellen Status.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ctt-img4.png)

1. Füllen Sie die Felder im Bildschirm **Details zum Inhaltsmigrationssatz** aus, wie nachfolgend beschrieben.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/content-3.png)


   1. **Name**: Geben Sie den Namen des Migrationssatzes ein.
      >[!NOTE]
      >Beim Namen des Migrationssatzes sind keine Sonderzeichen zulässig.

   1. **Cloud Service-Konfiguration**: Geben Sie die Ziel-URL der Autoreninstanz von AEM as a Cloud Service an.

      >[!NOTE]
      >Sie können während der Inhaltstransferaktivität maximal vier Migrationssätze gleichzeitig erstellen und verwalten.
      >Darüber hinaus müssen Sie für jede der spezifischen Umgebungen – *Staging*, *Entwicklung* und *Produktion* – eine separate Migration erstellen.

   1. **Zugriffs-Token**: Geben Sie das Zugriffs-Token ein.

      >[!NOTE]
      >Sie können das Zugriffs-Token aus der Autoreninstanz abrufen, indem Sie zu `/libs/granite/migration/token.json` navigieren. Das Zugriffs-Token wird aus der Cloud Service-Autoreninstanz abgerufen.

   1. **Parameter**: Wählen Sie die folgenden Parameter aus, um den Migrationssatz zu erstellen:

      1. **Version einschließen**: Aktivieren Sie die Option.

      1. **Einzuschließende Pfade**: Verwenden Sie den Pfad-Browser, um zu migrierende Pfade auszuwählen.

         >[!IMPORTANT]
         >Die folgenden Pfade sind beim Erstellen eines Migrationssatzes eingeschränkt:
         >* `/apps`
         >* `/libs`
         >* `/home`
         >* `/etc`


1. Klicken Sie auf **Speichern**, nachdem Sie alle Felder im Bildschirm **Details zum Inhaltsmigrationssatz** ausgefüllt haben.

1. Der Migrationssatz erscheint auf der Seite *Übersicht*.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ctt-img4.png)

   Alle auf diesem Bildschirm vorhandenen Migrationssätze werden auf der Seite *Übersicht* mit ihren aktuellen Statusinformationen angezeigt.

   * Eine *rote Wolke* bedeutet, dass Sie den Extraktionsvorgang nicht abschließen können.
   * Eine *grüne Wolke* bedeutet, dass Sie den Extraktionsvorgang abschließen können.
   * Ein *gelbes Symbol* weist darauf hin, dass Sie den vorhandenen Migrationssatz nicht erstellt haben und dass der betreffende Migrationssatz von einem anderen Benutzer in derselben Instanz erstellt wurde.

1. Wählen Sie auf der Übersichtsseite einen Migrationssatz aus und klicken Sie auf **Eigenschaften**, um die Migrationssatzeigenschaften anzuzeigen oder zu bearbeiten.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ctt-img6.png)

### Extraktionsvorgang beim Inhaltstransfer {#extraction-process}

Gehen Sie wie folgt vor, um den Migrationssatz aus dem Content Transfer-Tool zu extrahieren:

1. Wählen Sie auf der Seite *Übersicht* einen Migrationssatz aus und klicken Sie auf **Extrahieren**, um die Extraktion zu starten.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/extraction-img1.png)

1. Das Dialogfeld **Extraktion des Migrationssatzes** wird angezeigt. Klicken Sie auf **Extrahieren**, um die Extraktion abzuschließen.

   >[!NOTE]
   >Sie haben die Möglichkeit, Staging-Container während der Extraktion zu überschreiben.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/extract-2.png)

1. Im Feld **EXTRAKTION** wird jetzt der Status **WIRD AUSGEFÜHRT** für die Extraktion angezeigt, die derzeit ausgeführt wird.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/extract-3.png)

   Sobald die Extraktion abgeschlossen ist, wird der Status des Migrationssatzes auf **BEENDET** aktualisiert und unter dem Feld *INFO* wird ein **grünes** Wolkensymbol angezeigt.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/extract-4.png)

   >[!NOTE]
   >Sie müssen die Seite aktualisieren, um den aktualisierten Status anzuzeigen.
   >Beim Starten der Extraktionsphase wird die Schreibsperre aktiviert und nach *60 Sekunden* wieder aufgehoben. Wenn also eine Extraktion gestoppt wird, müssen Sie eine Minute warten, bis die Sperre aufgehoben wird, bevor Sie die Extraktion erneut starten können.

#### Auffüllextraktion {#top-up-extraction-process}

Das Content Transfer-Tool verfügt über eine Funktion, die die differenzielle Auffüllung von Inhalten unterstützt, wobei es möglich ist, nur Änderungen zu übertragen, die seit dem vorherigen Inhaltstransfer vorgenommen wurden.

>[!NOTE]
>Nach dem ersten Transfer von Inhalten wird empfohlen, häufige differenzielle Auffüllungen des Inhalts durchzuführen, um den Zeitraum für das Einfrieren des Inhalts für den endgültigen differenziellen Inhaltstransfer zu verkürzen, bevor er in Cloud Service live geschaltet wird.

Sobald die Extraktion abgeschlossen ist, können Sie Delta-Inhalte mithilfe der Auffüllextraktion übertragen. Führen Sie dazu folgende Schritte durch:

1. Navigieren Sie zur Seite *Übersicht* und wählen Sie den Migrationssatz aus, für den Sie die Auffüllextraktion durchführen möchten.

1. Klicken Sie auf **Extrahieren**, um die Auffüllextraktion zu starten.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/extraction-img1.png)

1. Das Dialogfeld **Extraktion des Migrationssatzes** wird angezeigt.

   >[!IMPORTANT]
   >Sie sollten die Option **Überschreiben des Staging-Containers während der Extraktion** deaktivieren.
   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/extract-topup-1.png)

### Aufnahmevorgang beim Inhaltstransfer {#ingestion-process}

Gehen Sie wie folgt vor, um den Migrationssatz aus dem Content Transfer-Tool aufzunehmen:

1. Wählen Sie auf der Seite *Übersicht* einen Migrationssatz aus und klicken Sie auf **Aufnehmen**, um die Aufnahme zu starten.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ingest-1.png)

1. Das Dialogfeld **Aufnahme des Migrationssatzes** wird angezeigt.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ingest-2.png)

   Zu Demonstrationszwecken ist die Option **Inhalt in Autoreninstanz aufnehmen** deaktiviert. Es ist möglich, Inhalte gleichzeitig in der Autoren- und Veröffentlichungsinstanz aufzunehmen.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ingest-3.png)

   Klicken Sie auf **Aufnehmen**, um die Aufnahmephase abzuschließen.

1. Sobald die Aufnahme abgeschlossen ist, wird der Status im Feld **AUFNAHME IN AUTOR** in **BEENDET** aktualisiert und unter **INFO** wird ein grünes Wolkensymbol angezeigt.
   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ingest-4.png)

   >[!NOTE]
   > Sie müssen die Seite aktualisieren, um den aktualisierten Status anzuzeigen.

#### Auffüllaufnahme {#top-up-ingestion-process}

Das Content Transfer-Tool verfügt über eine Funktion, die die differenzielle *Auffüllung* von Inhalten unterstützt, wobei es möglich ist, nur Änderungen zu übertragen, die seit dem vorherigen Inhaltstransfer vorgenommen wurden.

>[!NOTE]
>Nach dem ersten Transfer von Inhalten wird empfohlen, häufige differenzielle Auffüllungen des Inhalts durchzuführen, um den Zeitraum für das Einfrieren des Inhalts für den endgültigen differenziellen Inhaltstransfer zu verkürzen, bevor er in Cloud Service live geschaltet wird.

Sobald die Aufnahme abgeschlossen ist, können Sie Delta-Inhalte mithilfe der Auffüllaufnahme übertragen. Führen Sie dazu folgende Schritte durch:

1. Navigieren Sie zur Seite *Übersicht* und wählen Sie den Migrationssatz aus, für den Sie die Auffüllaufnahme durchführen möchten.

1. Klicken Sie auf **Aufnehmen**, um die Auffüllaufnahme zu starten.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ingest-1.png)

1. Das Dialogfeld **Aufnahme des Migrationssatzes** wird angezeigt.

   >[!NOTE]
   >Sie sollten die Option *Löschen* deaktivieren, um zu verhindern, dass der vorhandene Inhalt aus der vorherigen Aktivität gelöscht wird.
   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ingest-topup-1.png)

### Anzeigen von Protokollen für einen Migrationssatz {#viewing-logs-migration-set}

Auf der Seite *Übersicht* können Sie die Protokolle für einen vorhandenen Migrationssatz anzeigen.
Führen Sie dazu folgende Schritte durch:

1. Navigieren Sie zur Seite *Übersicht*, wählen Sie den zu löschenden Migrationssatz aus und klicken Sie in der Aktionsleiste auf **Protokoll anzeigen**.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/view-log1.png)

1. Das Dialogfeld **Protokolle** wird angezeigt. Klicken Sie auf **Extraktionsprotokolle**, um die Protokolle in einer neuen Registerkarte anzuzeigen.

   ![Abbildung](/help/move-to-cloud-service/content-transfer-tool/assets/view-log2.png)
Oder:

   Sie können die Protokolle für Ihren Migrationssatz auch über den Bildschirm *Übersicht* anzeigen. Wählen Sie den Migrationssatz aus und klicken Sie unter **EXTRAKTION** auf den Status. Klicken Sie in diesem Fall auf **FERTIG**, um die Protokolle in einer neuen Registerkarte anzuzeigen.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/view-log3.png)

1. Um die Protokolle ohne Verwendung der Benutzeroberfläche zu verfolgen, können Sie SSH in Ihre AEM-Quellumgebung einbinden und die Datei `crx-quickstart/cloud-migration/extraction-XXXXX/output.log file` verfolgen.

### Löschen eines Migrationssatzes {#deleting-migration-set}

Sie können den Migrationssatz auf der Seite *Übersicht* löschen.
Führen Sie dazu folgende Schritte durch:

1. Navigieren Sie zur Seite *Übersicht*, wählen Sie den zu löschenden Migrationssatz aus und klicken Sie in der Aktionsleiste auf **Löschen**.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/delete-1.png)

1. Klicken Sie im Dialogfeld **Migrationssatz löschen** auf **Löschen**, um den Löschvorgang zu bestätigen.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/delete-3.png)

## Fehlerbehebung {#troubleshooting}

### Fehlende Blob-IDs {#missing-blobs}

Wenn, wie unten erwähnt, fehlende Blob-IDs gemeldet werden, müssen Sie eine Konsistenzprüfung im bestehenden Repository durchführen und die fehlenden Blobs wiederherstellen.
`ERROR o.a.j.o.p.b.AbstractSharedCachingDataStore - Error retrieving record [ba45c53f8b687e7056c85dceebf8156a0e6abc7e]`

Der folgende Befehl wird ausgeführt

>[!NOTE]
>
>`--verbose`-Markierung ist erforderlich, um die Knotenpfade zu melden, von denen aus auf die BLOBs verwiesen wird.

**Für Repositorys AEM 6.5 (Oak 1.8 und älter)**

```shell
java -jar oak-run.jar datastorecheck --consistency --store [<SEGMENT_STORE_PATH>|<MONGO_URI>] --[s3ds|fds] <DATASTORE_CFG> --verbose <OUT_DIR> --dump
```

**Für Repositorys mit Oak > 1.10**

```shell
java -jar oak-run.jar datastore --check-consistency [<SEGMENT_STORE_PATH>|<MONGO_URI>] --[s3ds|fds|azureds] <DATASTORE_CFG> --out-dir <OUT_DIR> --work-dir <TEMP_DIR> --verbose
```

Weitere Informationen finden Sie unter [Ausführbare Jar für Oak](https://github.com/apache/jackrabbit-oak/tree/trunk/oak-run).

Die Dateien, die im oben angegebenen Verzeichnis *OUT_DIR* erstellt wurden, um Konsistenz zu gewährleisten, können dann auf Pfade ohne Binärdateien überprüft werden. Anschließend können geeignete Maßnahmen ergriffen werden, wie das Wiederherstellen aus einer Sicherung, das Löschen der Pfade, die Neuindizierung usw.

### Verhalten der Benutzeroberfläche {#ui-behavior}

Als Benutzer sehen Sie möglicherweise die folgenden Verhaltensänderungen in der Benutzeroberfläche für das Content Transfer-Tool:

* Der Benutzer erstellt einen Migrationssatz für eine Autoren-URL (Entwicklung/Staging/Produktion) und führt Extraktion und Aufnahme erfolgreich durch.

* Der Benutzer erstellt dann einen neuen Migrationssatz für dieselbe Autoren-URL und führt Extraktion und Aufnahme für den neuen Migrationssatz durch. Die Benutzeroberfläche zeigt an, dass sich der Aufnahmestatus des ersten Migrationssatzes in **FEHLGESCHLAGEN** ändert und keine Protokolle verfügbar sind.

* Dies bedeutet nicht, dass die Aufnahme für den ersten Migrationssatz fehlgeschlagen ist. Dieses Verhalten tritt auf, weil beim Starten eines neuen Aufnahmevorgangs der vorherige Aufnahmevorgang gelöscht wird. Daher sollte der Änderungsstatus des ersten Migrationssatzes ignoriert werden.

* Die Symbole in der Benutzeroberfläche des Content Transfer-Tools unterscheiden sich möglicherweise von den in diesem Handbuch gezeigten Screenshots oder werden je nach Version der AEM-Quellinstanz überhaupt nicht angezeigt.


