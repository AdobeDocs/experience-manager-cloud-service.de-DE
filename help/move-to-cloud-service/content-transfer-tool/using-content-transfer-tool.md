---
title: Verwenden des Content Transfer-Tools
description: Verwenden des Content Transfer-Tools
translation-type: tm+mt
source-git-commit: f3a4fdf57dc84bba9811530fccb2fe6a4404376f
workflow-type: tm+mt
source-wordcount: '1902'
ht-degree: 70%

---


# Verwenden des Content Transfer-Tools {#using-content-transfer-tool}

## Wichtige Überlegungen zur Verwendung des Content Transfer-Tools {#pre-reqs}

Im folgenden Abschnitt finden Sie wichtige Überlegungen zur Verwendung des Content Transfer-Tools:

* Die Mindest-Systemanforderungen für das Content Transfer-Tool sind AEM 6.3 + und JAVA 8. Wenn Sie eine niedrigere AEM-Version verwenden, müssen Sie Ihr Content-Repository auf AEM 6.5 aktualisieren, um das Content Transfer-Tool verwenden zu können.

* Java muss auf der AEM Umgebung konfiguriert werden, damit der `java` Befehl von dem Benutzer ausgeführt werden kann, der Beginn AEM.

* Das Content Transfer Tool kann mit den folgenden Arten des Datenspeichers verwendet werden: Dateidatenspeicher, S3-Datenspeicher, freigegebener S3-Datenspeicher und Datenspeicher für die Blase.

* Wenn Sie eine *Sandbox-Umgebung* verwenden, stellen Sie sicher, dass Ihre Umgebung aktuell ist und auf die neueste Version aktualisiert wird. Wenn Sie eine *Produktionsumgebung* verwenden, wird diese automatisch aktualisiert.

* Um das Content Transfer Tool verwenden zu können, müssen Sie Administrator Ihrer Quellinstanz sein und zur lokalen Gruppe der AEM in der Cloud Service-Instanz gehören, an die Sie Inhalte übertragen. Unberechtigte Benutzer können das Zugriffs-Token zur Verwendung des Content Transfer-Tools nicht abrufen.

* Derzeit beträgt die Standardgröße von MongoDB für eine AEM als Cloud Service-Autoreninstanz 32 GB. Es wird empfohlen, dass Sie für eine Segmentspeichergröße von mehr als 20 GB ein Support-Ticket einreichen, um die MongoDB-Größe zu erhöhen.

* Die vom Content Transfer Tool übertragenen Benutzer und Gruppen sind nur diejenigen, die vom Inhalt zur Erfüllung der Berechtigungen benötigt werden. Der *Extraktion* -Prozess kopiert den gesamten `/home` Migrationssatz und der *Ingestion* -Prozess kopiert alle Benutzer und Gruppen, auf die in den ACLs für migrierte Inhalte verwiesen wird.

* Während der Extraktionsphase wird das Content Transfer-Tool in einer aktiven AEM-Quellinstanz ausgeführt.

* Nachdem Sie die *Extraktion* des Inhaltsübermittlungsprozesses abgeschlossen haben und bevor Sie die *Übergangsphase* starten, um Inhalte in Ihre AEM als Cloud Service- *Stage* - oder *Produktionsinstanz* zu übernehmen, müssen Sie ein Support-Ticket protokollieren, um die Adobe über Ihre Absicht zu informieren, *Ingestion* ** auszuführen, damit die Adobe sicherstellen kann, dass während desIngestionProcess keine Unterbrechungen auftreten. Sie müssen das Support-Ticket 1 Woche vor dem geplanten *Ingestion* -Datum einloggen. Nachdem Sie das Support-Ticket übermittelt haben, gibt das Supportteam Ihnen Anleitungen zu den nächsten Schritten.
   * Protokollieren Sie ein Support-Ticket mit den folgenden Details:
      * Genaues Datum und voraussichtliche Uhrzeit (mit Ihrer Zeitzone), zu der Sie die *Ingestion* -Phase Beginn beabsichtigen.
      * Umgebung-Typ (Phase oder Produktion), in den Sie Daten erfassen möchten.
      * Programm-ID.

* In der *Aufnahmephase* für die Autoreninstanz wird die gesamte Autorenimplementierung herabgesetzt. In anderen Worten, die Autoreninstanz von AEM ist während des gesamten Aufnahmevorgangs nicht verfügbar. Bitte stellen Sie außerdem sicher, dass während der *Engpass* -Phase keine Cloud Manager-Pipelines ausgeführt werden.


## Verfügbarkeit {#availability}

Das Content Transfer Tool kann als ZIP-Datei vom Software Distribution Portal heruntergeladen werden. Sie können das Paket über Package Manager in Ihrer Quelldistanz von Adobe Experience Manager (AEM) installieren. Laden Sie unbedingt die neueste Version herunter. Weitere Informationen zur neuesten Version finden Sie in den [Versionshinweisen](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html).

>[!NOTE]
>Laden Sie das Content Transfer-Tool vom [Software Distribution-Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) herunter.

## Ausführen des Content Transfer-Tools {#running-tool}

>[!VIDEO](https://video.tv.adobe.com/v/35460/?quality=12&learn=on)


In diesem Abschnitt erfahren Sie, wie Sie mit dem Content Transfer-Tool Inhalte zu AEM as a Cloud Service (Autor/Veröffentlichung) migrieren:

1. Wählen Sie Adobe Experience Manager aus und navigieren Sie zu Tools > **Vorgänge** > **Inhaltstransfer**.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/content1.png)

1. Die Konsole unten wird angezeigt, wenn Sie den ersten Migrationssatz erstellen. Klicken Sie auf **Migrationssatz erstellen**, um einen neuen Migrationssatz zu erstellen.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/01-migration-set-overview.png)

   >[!NOTE]
   >Wenn Sie bereits Migrationssätze haben, zeigt die Konsole die Liste der vorhandenen Migrationssätze mit ihrem aktuellen Status an.

1. Füllen Sie die Felder im Bildschirm **Details zum Inhaltsmigrationssatz** aus, wie nachfolgend beschrieben.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/02-migration-set-creation.png)


   1. **Name**: Geben Sie den Namen des Migrationssatzes ein.
      >[!NOTE]
      >Beim Namen des Migrationssatzes sind keine Sonderzeichen zulässig.

   1. **Cloud Service-Konfiguration**: Geben Sie die Ziel-URL der Autoreninstanz von AEM as a Cloud Service an.

      >[!NOTE]
      >Sie können während der Inhaltstransferaktivität maximal vier Migrationssätze gleichzeitig erstellen und verwalten.
      >Darüber hinaus müssen Sie für jede der spezifischen Umgebungen – *Staging*, *Entwicklung* und *Produktion* – eine separate Migration erstellen.

   1. **Zugriffs-Token**: Geben Sie das Zugriffs-Token ein.

      >[!NOTE]
      >Sie können das Zugriffstoken über die Schaltfläche **Zugriffstoken** öffnen abrufen. Sie müssen sicherstellen, dass Sie in der Zielgruppe Cloud Service-Instanz zur Gruppe AEM Administratoren gehören.

   1. **Parameter**: Wählen Sie die folgenden Parameter aus, um den Migrationssatz zu erstellen:

      1. **Version einschließen**: Aktivieren Sie die Option.

      1. **Einzuschließende Pfade**: Verwenden Sie den Pfad-Browser, um zu migrierende Pfade auszuwählen. Die Pfadauswahl akzeptiert Eingaben durch Eingabe oder Auswahl.

         >[!IMPORTANT]
         >Die folgenden Pfade sind beim Erstellen eines Migrationssatzes eingeschränkt:
         >* `/apps`
         >* `/libs`
         >* `/home`
         >* `/etc`


1. Klicken Sie auf **Speichern**, nachdem Sie alle Felder im Bildschirm **Details zum Inhaltsmigrationssatz** ausgefüllt haben.

1. Der Migrationssatz erscheint auf der Seite *Übersicht*.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/04-item-selection-and-quick-actions.png)

   Alle auf diesem Bildschirm vorhandenen Migrationssätze werden auf der Seite *Übersicht* mit ihren aktuellen Statusinformationen angezeigt. Sie können einige der unten beschriebenen Symbole sehen.

   * Eine *rote Wolke* bedeutet, dass Sie den Extraktionsvorgang nicht abschließen können.
   * Eine *grüne Wolke* bedeutet, dass Sie den Extraktionsvorgang abschließen können.
   * Ein *gelbes Symbol* weist darauf hin, dass Sie den vorhandenen Migrationssatz nicht erstellt haben und dass der betreffende Migrationssatz von einem anderen Benutzer in derselben Instanz erstellt wurde.

1. Wählen Sie auf der Übersichtsseite einen Migrationssatz aus und klicken Sie auf **Eigenschaften**, um die Migrationssatzeigenschaften anzuzeigen oder zu bearbeiten. Beim Bearbeiten von Eigenschaften ist es nicht möglich, den Namen des Containers oder die Dienst-URL zu ändern.



### Extraktionsvorgang beim Inhaltstransfer {#extraction-process}

Gehen Sie wie folgt vor, um den Migrationssatz aus dem Content Transfer-Tool zu extrahieren:

1. Wählen Sie auf der Seite *Übersicht* einen Migrationssatz aus und klicken Sie auf **Extrahieren**, um die Extraktion zu starten. The **Migration Set extraction** dialog box displays and click on **Extract** to start the extraction phase.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/06-content-extraction.png)

   >[!NOTE]
   >Sie haben die Möglichkeit, Staging-Container während der Extraktion zu überschreiben.


1. Im Feld **EXTRAKTION** wird jetzt der Status **AUSGEFÜHRT** angezeigt, um anzuzeigen, dass die Extraktion ausgeführt wird.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/07-extraction-job-running.png)

   Sobald die Extraktion abgeschlossen ist, wird der Status des Migrationssatzes auf **BEENDET** aktualisiert und unter dem Feld *INFO* wird ein **grünes** Wolkensymbol angezeigt.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/10-extraction-complete.png)

   >[!NOTE]
   >Die Benutzeroberfläche verfügt über eine Funktion zum automatischen Neuladen, mit der die Übersichtsseite alle 30 Sekunden neu geladen wird.
   >Beim Starten der Extraktionsphase wird die Schreibsperre aktiviert und nach *60 Sekunden* wieder aufgehoben. Wenn also eine Extraktion gestoppt wird, müssen Sie eine Minute warten, bis die Sperre aufgehoben wird, bevor Sie die Extraktion erneut starten können.

#### Auffüllextraktion {#top-up-extraction-process}

Das Content Transfer-Tool verfügt über eine Funktion, die die differenzielle Auffüllung von Inhalten unterstützt, wobei es möglich ist, nur Änderungen zu übertragen, die seit dem vorherigen Inhaltstransfer vorgenommen wurden.

>[!NOTE]
>Nach dem ersten Transfer von Inhalten wird empfohlen, häufige differenzielle Auffüllungen des Inhalts durchzuführen, um den Zeitraum für das Einfrieren des Inhalts für den endgültigen differenziellen Inhaltstransfer zu verkürzen, bevor er in Cloud Service live geschaltet wird.

Sobald die Extraktion abgeschlossen ist, können Sie Delta-Inhalte mithilfe der Auffüllextraktion übertragen. Führen Sie dazu folgende Schritte durch:

1. Navigieren Sie zur Seite *Übersicht* und wählen Sie den Migrationssatz aus, für den Sie die Auffüllextraktion durchführen möchten. Klicken Sie auf **Extrahieren**, um die Auffüllextraktion zu starten. Das Dialogfeld **Extraktion des Migrationssatzes** wird angezeigt.

   >[!IMPORTANT]
   >
   >Sie sollten die Option **Überschreiben des Staging-Containers während der Extraktion** deaktivieren.
   >
   >![image](/help/move-to-cloud-service/content-transfer-tool/assets/11-topup-extraction.png)

### Aufnahmevorgang beim Inhaltstransfer {#ingestion-process}

Gehen Sie wie folgt vor, um den Migrationssatz aus dem Content Transfer-Tool aufzunehmen:

1. Wählen Sie auf der Seite *Übersicht* einen Migrationssatz aus und klicken Sie auf **Aufnehmen**, um die Aufnahme zu starten. Das Dialogfeld **Aufnahme des Migrationssatzes** wird angezeigt. Click on **Ingest** to start the ingestion phase. Zu Demonstrationszwecken ist die Option **Inhalt in Autoreninstanz aufnehmen** deaktiviert. Es ist möglich, Inhalte gleichzeitig in der Autoren- und Veröffentlichungsinstanz aufzunehmen.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/12-content-ingestion.png)

1. Sobald die Erfassung abgeschlossen ist, wird der Status im Feld **PUBLISH INGESTION** auf **FINISHED** aktualisiert.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/15-ingestion-complete.png)

#### Auffüllaufnahme {#top-up-ingestion-process}

Das Content Transfer-Tool verfügt über eine Funktion, die die differenzielle *Auffüllung* von Inhalten unterstützt, wobei es möglich ist, nur Änderungen zu übertragen, die seit dem vorherigen Inhaltstransfer vorgenommen wurden.

>[!NOTE]
>
>Nach dem ersten Transfer von Inhalten wird empfohlen, häufige differenzielle Auffüllungen des Inhalts durchzuführen, um den Zeitraum für das Einfrieren des Inhalts für den endgültigen differenziellen Inhaltstransfer zu verkürzen, bevor er in Cloud Service live geschaltet wird.

Sobald die Aufnahme abgeschlossen ist, können Sie Delta-Inhalte mithilfe der Auffüllaufnahme übertragen. Führen Sie dazu folgende Schritte durch:

1. Navigieren Sie zur Seite *Übersicht* und wählen Sie den Migrationssatz aus, für den Sie die Auffüllaufnahme durchführen möchten. Klicken Sie auf **Aufnehmen**, um die Auffüllaufnahme zu starten. Das Dialogfeld **Aufnahme des Migrationssatzes** wird angezeigt.

   >[!IMPORTANT]
   >
   >Sie sollten die Option &quot;Vorhandenen Inhalt vor der Erfassung **löschen&quot;in der Cloud-Instanz deaktivieren, um zu verhindern, dass der vorhandene Inhalt aus der vorherigen Aktivität gelöscht wird** .
   >
   >![image](/help/move-to-cloud-service/content-transfer-tool/assets/16-topup-ingestion.png)

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


