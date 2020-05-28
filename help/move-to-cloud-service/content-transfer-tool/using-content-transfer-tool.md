---
title: Verwenden des Inhaltsübertragungstools
description: Verwenden des Inhaltsübertragungstools
translation-type: tm+mt
source-git-commit: 3478827949356c4a4f5133b54c6cf809f416efef
workflow-type: tm+mt
source-wordcount: '1412'
ht-degree: 3%

---


# Verwenden des Inhaltsübertragungstools {#using-content-transfer-tool}

## Wichtige Überlegungen zur Verwendung des Inhaltsübermittlungstools {#pre-reqs}

Befolgen Sie den folgenden Abschnitt, um die wichtigen Überlegungen beim Ausführen des Content Transfer-Tools zu verstehen:

* Die Mindestsystemanforderung für das Content Transfer Tool ist AEM 6.3 + und JAVA 8. Wenn Sie eine niedrigere AEM-Version verwenden, müssen Sie Ihr Inhalts-Repository auf AEM 6.5 aktualisieren, um das Content Transfer Tool verwenden zu können.

* Wenn Sie eine *Sandbox-Umgebung* verwenden, stellen Sie sicher, dass Ihre Umgebung auf Version vom 29. Mai 2020 oder höher aktualisiert wird. Wenn Sie eine *Produktions-Umgebung* verwenden, wird diese automatisch aktualisiert.

* Während der Extraktion wird das Content Transfer Tool auf einer aktiven AEM-Quellinstanz ausgeführt.

* Die *Ingestion-Phase* für den Autor wird die gesamte Autorenbereitstellung reduzieren. Das bedeutet, dass der Autor AEM während des gesamten Erfassungsvorgangs nicht verfügbar ist.

## Verfügbarkeit {#availability}

Das Content Transfer Tool kann als ZIP-Datei vom Software Distribution Portal heruntergeladen werden. Sie können das Paket über Package Manager auf der Quell-Instanz von Adobe Experience Manager (AEM) installieren.

>[!NOTE]
>Weitere Informationen finden Sie unter [Zugriff auf AEM als Cloud-Dienst-SDK](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html#accessing-the-aem-as-a-cloud-service-sdk) .

## Ausführen des Inhaltsübermittlungstools {#running-tool}

In diesem Abschnitt erfahren Sie, wie Sie mit dem Content Transfer Tool Inhalte als Cloud-Dienst (Autor/Veröffentlichen) in AEM migrieren:

1. Wählen Sie Adobe Experience Manager und navigieren Sie zu Tools -> **Vorgänge** -> **Inhaltsübertragung**.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/content1.png)

1. Klicken Sie auf &quot;Migrationsset **erstellen&quot;** , um einen neuen Migrationssatz zu erstellen. Die Details zum **Content Migrations-Set werden angezeigt** .

   >[!NOTE]
   >Sie werden die vorhandenen Migrationssets auf diesem Bildschirm mit ihrem aktuellen Status Ansicht.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ctt-img4.png)

1. Füllen Sie die Felder im Bildschirm **Inhaltsmigrationsset-Details** aus, wie nachfolgend beschrieben.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/content-3.png)


   1. **Name**: Geben Sie den Namen des Migrationssatzes ein.
      >[!NOTE]
      >Für den Migrationssatznamen sind keine Sonderzeichen zulässig.

   1. **Cloud-Dienstkonfiguration**: Geben Sie das Ziel AEM als URL für den Autor des Cloud-Dienstes ein.

      >[!NOTE]
      >Sie können während der Aktivität der Inhaltsübertragung maximal vier Migrationssätze gleichzeitig erstellen und verwalten.
      >Darüber hinaus müssen Sie eine Migration für jede der spezifischen Umgebung - *Phase*, *Entwicklung* oder *Produktion*- separat erstellen.

   1. **Zugriffstoken**: Geben Sie das Zugriffstoken ein.

      >[!NOTE]
      >Sie können das Zugriffstoken aus der Autoreninstanz abrufen, indem Sie zu navigieren `/libs/granite/migration/token.json`.

   1. **Parameter**: Wählen Sie die folgenden Parameter aus, um den Migrationssatz zu erstellen:

      1. **Version** einschließen: Wählen Sie die gewünschte Option aus.

      1. **Einzuschließende** Pfade: Verwenden Sie den Pfadbrowser, um Pfade auszuwählen, die migriert werden müssen.

         >[!IMPORTANT]
         >Folgende Pfade sind beim Erstellen eines Migrationssatzes eingeschränkt:
         >* `/apps`
         >* `/libs`
         >* `/home`
         >* `/etc`


1. Klicken Sie auf **Speichern** , nachdem Sie alle Felder im Anzeigebereich &quot; **Inhaltsmigrationsset-Details** &quot;ausgefüllt haben.

1. Sie werden den Migrationssatz auf der Seite *Übersicht* Ansicht.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ctt-img4.png)

   Alle auf diesem Bildschirm vorhandenen Migrationssets werden auf der Seite *Übersicht* mit ihren aktuellen Status- und Statusinformationen angezeigt.

   * Eine *rote Cloud* bedeutet, dass Sie den Extraktion-Vorgang nicht abschließen können.
   * Eine *grüne Cloud* bedeutet, dass Sie den gesamten Vorgang der Extraktion abschließen können.
   * Ein *gelbes Symbol* weist darauf hin, dass Sie den vorhandenen Migrationssatz nicht erstellt haben und dass der betreffende Migrationssatz von einem anderen Benutzer in derselben Instanz erstellt wurde.

1. Wählen Sie auf der Übersichtsseite einen Migrationssatz aus und klicken Sie auf **Eigenschaften** , um die Migrationssatzeigenschaften Ansicht oder zu bearbeiten.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ctt-img6.png)

### Extraktion bei der Inhaltsübertragung {#extraction-process}

Gehen Sie wie folgt vor, um den Migrationssatz aus dem Content Transfer Tool zu extrahieren:

1. Wählen Sie auf der Seite &quot; *Übersicht* &quot;einen Migrationssatz aus und klicken Sie auf Extraktion &quot;Zu Beginn **extrahieren** &quot;.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/extraction-img1.png)

1. Das Dialogfeld &quot; **Migrationsset-Extraktion** &quot;wird angezeigt und Sie klicken auf &quot; **Extrahieren** &quot;, um die Extraktion abzuschließen.

   >[!NOTE]
   >Sie haben die Möglichkeit, Staging-Container während der Extraktion zu überschreiben.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/extract-2.png)

1. Im Feld &quot; **EXTRAKTION** &quot;wird jetzt der Status &quot; **AUSFÜHREN** &quot;für die Extraktion angezeigt, die derzeit ausgeführt wird.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/extract-3.png)

   Sobald die Extraktion abgeschlossen ist, wird der Status des Migrationssatzes auf **FINISHED** aktualisiert und unter dem Feld &quot; *INFO* &quot;wird ein **grünes** Cloud-Symbol angezeigt.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/extract-4.png)

   >[!NOTE]
   > Sie müssen die Seite aktualisieren, um den aktualisierten Status Ansicht.

#### Extraktion oben {#top-up-extraction-process}

Das Inhaltsübermittlungstool verfügt über eine Funktion, mit der das Aufstocken von differenziellen Inhalten unterstützt wird, wenn nur Änderungen übertragen werden können, die seit der vorherigen Aktivität der Inhaltsübertragung vorgenommen wurden.

>[!NOTE]
>Nach der ersten Inhaltsübertragung wird empfohlen, häufig differenzielle Inhaltsaufstockungen durchzuführen, um die Einfrierzeit für die endgültige Übertragung von differenziellen Inhalten zu verkürzen, bevor Sie mit Cloud Service live gehen.

Sobald die Extraktion abgeschlossen ist, können Sie Delta-Inhalte mithilfe der Top-up-Extraktion übertragen. Führen Sie dazu folgende Schritte durch:

1. Navigieren Sie zur Seite &quot; *Übersicht* &quot;und wählen Sie den Migrationssatz aus, für den Sie die Top-up-Extraktion durchführen möchten.

1. Klicken Sie auf **Extrahieren** , um die Extraktion oben Beginn.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/extraction-img1.png)

1. Das Dialogfeld &quot;Extraktion **des Migrationssatzes** &quot;wird angezeigt.

   >[!IMPORTANT]
   >Sie sollten den Staging-Container **überschreiben während der Extraktion** deaktivieren.
   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/extract-topup-1.png)

### Einbettungsvorgang bei der Inhaltsübertragung {#ingestion-process}

Gehen Sie wie folgt vor, um den Migrationssatz aus dem Content Transfer Tool zu erfassen:

1. Wählen Sie auf der Seite &quot; *Übersicht* &quot;einen Migrationssatz aus und klicken Sie auf &quot;Zu Beginn-Extraktion **aufnehmen** &quot;.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ingest-1.png)

1. Das Dialogfeld **Erfassung** des Migrationssatzes wird angezeigt.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ingest-2.png)

   Zu Demonstrationszwecken ist die Option Inhalt in Autoreninstanz **aufnehmen** deaktiviert. Es ist möglich, Inhalte gleichzeitig zu erstellen und zu veröffentlichen.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ingest-3.png)

   Klicken Sie auf **Erfassen** , um die Aufnahmephase abzuschließen.

1. Sobald die Erfassung abgeschlossen ist, wird der Status im Feld **AUTHOR INGESTION** auf **FINISHED** aktualisiert und unter dem **INFO**wird ein grünes Cloud-Symbol angezeigt.
   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ingest-4.png)

   >[!NOTE]
   > Sie müssen die Seite aktualisieren, um den aktualisierten Status Ansicht.

#### Aufnahme nach oben {#top-up-ingestion-process}

Das Inhaltsübermittlungstool verfügt über eine Funktion, mit der Differenzialinhalte *überholt* werden können, wenn nur Änderungen übertragen werden können, die seit der vorherigen Aktivität der Inhaltsübertragung vorgenommen wurden.

>[!NOTE]
>Nach der ersten Inhaltsübertragung wird empfohlen, häufig differenzielle Inhaltsaufstockungen durchzuführen, um die Einfrierzeit für die endgültige Übertragung von differenziellen Inhalten zu verkürzen, bevor Sie mit Cloud Service live gehen.

Nachdem der Erfassungsvorgang abgeschlossen ist, können Sie Delta-Inhalte verwenden, indem Sie die Erfassungsmethode verwenden. Führen Sie dazu folgende Schritte durch:

1. Navigieren Sie zur Seite &quot; *Übersicht* &quot;und wählen Sie den Migrationssatz aus, für den Sie die Erfassung nach oben durchführen möchten.

1. Klicken Sie auf **Erfassen** , um die Extraktion oben Beginn.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ingest-1.png)

1. Das Dialogfeld &quot; **Integration** des Migrationssatzes&quot;wird angezeigt.

   >[!NOTE]
   >Sie sollten die Option &quot; *Bereinigen* &quot;deaktivieren, um zu verhindern, dass der vorhandene Inhalt aus der vorherigen Aktivität gelöscht wird.
   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ingest-topup-1.png)

### Anzeigen von Protokollen für einen Migrationssatz {#viewing-logs-migration-set}

Auf der Seite &quot; *Übersicht* &quot;können Sie Protokolle für einen vorhandenen Migrationssatz erstellen.
Führen Sie dazu folgende Schritte durch:

1. Navigieren Sie zur Seite *Übersicht* , wählen Sie den zu löschenden Migrationssatz aus und klicken Sie in der Aktionsleiste auf **Ansichten-Protokoll** .

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/view-log1.png)

1. Das Dialogfeld **Protokolle** wird angezeigt. Klicken Sie auf **Extraktion Logs** , um die Protokolle in einer neuen Registerkarte Ansicht.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/view-log2.png)or,

   Sie können auch Protokolle für die Ansicht Ihres Migrationssatzes im Anzeigebereich &quot; *Übersicht* &quot;erstellen. Wählen Sie den Migrationssatz aus und klicken Sie unter &quot; **EXTRAKTION** &quot;auf den Status. Klicken Sie in diesem Fall auf **FERTIG** , um Ansichten in einer neuen Registerkarte anzuzeigen.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/view-log3.png)

### Löschen eines Migrationssatzes {#deleting-migration-set}

Sie können den Migrationssatz auf der Seite *Übersicht* löschen.
Führen Sie dazu folgende Schritte durch:

1. Navigieren Sie zur Seite *Übersicht* , wählen Sie den zu löschenden Migrationssatz aus und klicken Sie in der Aktionsleiste auf **Löschen** .

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/delete-1.png)

1. Klicken Sie auf **Löschen** aus **Löschen des Migrationssatzes** , um den Löschvorgang zu bestätigen.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/delete-3.png)

## Fehlerbehebung {#troubleshooting}

### Fehlende Blob-IDs {#missing-blobs}

Wenn, wie unten erwähnt, fehlende Blob-IDs gemeldet werden, müssen Sie eine Konsistenzprüfung im vorhandenen Repository durchführen und die fehlenden Blobs wiederherstellen.
`ERROR o.a.j.o.p.b.AbstractSharedCachingDataStore - Error retrieving record [ba45c53f8b687e7056c85dceebf8156a0e6abc7e]`

Der folgende Befehl wird ausgeführt

>[!NOTE]
> `--verbose` -Flag erforderlich ist, um die Knotenpfade zu melden, von denen aus auf die Blobs verwiesen wird.

**Für Repositorys AEM 6.5 (Oak 1.8 und höher)**

```shell
java -jar oak-run.jar datastorecheck --consistency --store [<SEGMENT_STORE_PATH>|<MONGO_URI>] --[s3ds|fds] <DATASTORE_CFG> --verbose <OUT_DIR> --dump
```

**Für Repositorys mit Oak > 1.10**

```shell
java -jar oak-run.jar datastore --check-consistency [<SEGMENT_STORE_PATH>|<MONGO_URI>] --[s3ds|fds|azureds] <DATASTORE_CFG> --out-dir <OUT_DIR> --work-dir <TEMP_DIR> --verbose
```

Weitere Informationen finden Sie unter [Oak Runnable Jar](https://github.com/apache/jackrabbit-oak/tree/trunk/oak-run) .

Die Dateien, die in der oben angegebenen *OUT_DIR* erstellt wurden, um Konsistenz zu gewährleisten, können dann auf Pfade überprüft werden, bei denen Binärdateien fehlen und geeignete Maßnahmen ergriffen werden, wie z. B. Wiederherstellung aus einer Sicherung, Löschen der Pfade, Neuindizierung usw.

### Verhalten der Benutzeroberfläche {#ui-behavior}

Als Benutzer sehen Sie möglicherweise die folgenden Verhaltensänderungen in der Benutzeroberfläche (UI) für das Content Transfer Tool:

1. Der Benutzer erstellt einen Migrationssatz für eine Autor-URL (Entwicklung/Stage/Produktion) und führt erfolgreich Extraktion und Erfassung durch.

1. Der Benutzer erstellt dann einen neuen Migrationssatz für dieselbe Autor-URL und führt Extraktion und Erfassung für den neuen Migrationssatz durch. Die Benutzeroberfläche zeigt an, dass der Erfassungsstatus des ersten Migrationssatzes auf &quot; **FEHLGESCHLAGEN** &quot;geändert wird und keine Protokolle verfügbar sind.

1. Dies bedeutet nicht, dass die Erfassung für den ersten Migrationssatz fehlgeschlagen ist. Dieses Verhalten wird angezeigt, da beim Starten eines neuen Erfassungsauftrags der vorherige Erfassungsauftrag gelöscht wird. Daher sollte der Änderungsstatus für den ersten Migrationssatz ignoriert werden.


