---
title: Verwenden des Content Transfer Tools
description: Verwenden des Content Transfer Tools
exl-id: a19b8424-33ab-488a-91b3-47f0d3c8abf5
source-git-commit: e0c6a79e6a088423cbc47046f285fb1ac241c476
workflow-type: tm+mt
source-wordcount: '2721'
ht-degree: 66%

---

# Verwenden des Content Transfer Tools {#using-content-transfer-tool}

## Wichtige Überlegungen zur Verwendung des Content Transfer Tools {#pre-reqs}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_prereqs"
>title="Wichtige Überlegungen zur Verwendung des Content Transfer Tool"
>abstract="Beachten Sie die wichtigen Aspekte, um das Content Transfer-Tool zu verwenden, einschließlich Java- und AEM-Versionen, unterstützte Datastore-Typen, Überlegungen zu Benutzergruppen und mehr."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?lang=en#best-practices" text="Best Practices und Leitlinien"

Im folgenden Abschnitt finden Sie wichtige Überlegungen zur Verwendung des Content Transfer Tools:

* Die Mindest-Systemanforderungen für das Content Transfer Tool sind AEM 6.3 + und JAVA 8. Wenn Sie eine niedrigere AEM Version verwenden, müssen Sie Ihr Inhalts-Repository auf AEM 6.5 aktualisieren, um das Content Transfer Tool verwenden zu können.

* Java muss auf der AEM Umgebung konfiguriert werden, damit der Befehl `java` von dem Benutzer ausgeführt werden kann, der Beginn AEM.

* Es wird empfohlen, ältere Versionen des Content Transfer Tool bei der Installation der Version 1.3.0 zu deinstallieren, da es eine wesentliche architektonische Änderung im Tool gab. Mit 1.3.0 sollten Sie außerdem neue Migrationssets erstellen und die Extraktion und Erfassung der neuen Migrationssätze erneut ausführen.

* Das Content Transfer Tool kann mit den folgenden Arten von Datenspeicher genutzt werden: Dateispeicher, S3-Datenspeicher, freigegebener S3-Datenspeicher und Azure Blob-Datenspeicher.

* Wenn Sie eine *Sandbox-Umgebung* verwenden, müssen Sie dafür sorgen, dass Ihre Umgebung aktuell ist bzw. auf die neueste Version aktualisiert wird. Wenn Sie eine *Produktionsumgebung* nutzen, wird diese automatisch aktualisiert.

* Um das Content Transfer Tool verwenden zu können, müssen Sie Administrator Ihrer Quellinstanz sein und der lokalen AEM **administrators** in der Cloud Service-Instanz angehören, an die Sie Inhalte übertragen. Unberechtigte Benutzer können das Zugriffs-Token zur Verwendung des Content Transfer Tools nicht abrufen.

* Wenn die Option **Vorhandenen Inhalt in der Cloud-Instanz vor der Erfassung löschen aktiviert ist, wird das gesamte vorhandene Repository gelöscht und ein neues Repository erstellt, in das Inhalte erfasst werden.** Das bedeutet, dass alle Einstellungen einschließlich der Berechtigungen für die Cloud Service-Zielinstanz zurückgesetzt werden. Dies gilt auch für Administratoren, die der Gruppe **administrators** hinzugefügt werden. Der Benutzer muss der Gruppe **administratoren** erneut hinzugefügt werden, um das Zugriffstoken für CTT abzurufen.

* Das Zugriffs-Token kann gelegentlich ablaufen, entweder nach einem bestimmten Zeitraum oder nach einem Upgrade der Cloud Service-Umgebung. Wenn das Zugriffstoken abgelaufen ist, können Sie keine Verbindung zur Cloud Service-Instanz herstellen und müssen das neue Zugriffstoken abrufen. Als Statussymbol für einen vorhandenen Migrationssatz wird eine rote Wolke angezeigt. Wenn Sie mit dem Mauszeiger darauf zeigen, wird eine Meldung eingeblendet.

* Das Content Transfer Tool (CTT) führt keine Content-Analyse durch, bevor Inhalte von der Quellinstanz in die Zielgruppe-Instanz übertragen werden. Beispielsweise unterscheidet CTT nicht zwischen veröffentlichten und unveröffentlichten Inhalten, wenn Inhalte in eine Publish-Umgebung eingefügt werden. Der Inhalt, der im Migrationsset angegeben ist, wird in die ausgewählte Instanz der Zielgruppe aufgenommen. Benutzer haben die Möglichkeit, einen Migrationssatz in einer Autorinstanz oder Veröffentlichungsinstanz oder in beiden Instanzen zu erfassen. Es wird empfohlen, beim Verschieben von Inhalten in eine Produktionsinstanz die CTT auf der Quellautorinstanz zu installieren, um Inhalte in die Zielgruppe Author-Instanz zu verschieben. Installieren Sie auf ähnliche Weise die CTT auf der Quell-Veröffentlichungsinstanz, um Inhalte in die Zielgruppe Publish-Instanz zu verschieben.

* Die vom Content Transfer Tool übertragenen Benutzer und Gruppen sind nur diejenigen, die vom Content zur Erfüllung der Berechtigungen benötigt werden. Der *Extraktions*-Vorgang kopiert das gesamte `/home` in den Migrationssatz und der *Aufnahme*-Vorgang kopiert alle Benutzer und Gruppen, auf die in den ACLs der migrierten Inhalte verwiesen wird. Informationen zum automatischen Zuordnen der vorhandenen Benutzer und Gruppen zu ihren IMS-IDs finden Sie unter [Verwenden des User Mapping Tools](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=de#cloud-migration).

* Während der Extraktionsphase wird das Content Transfer Tool in einer aktiven AEM-Quellinstanz ausgeführt.

* Nachdem die *Extraktionsphase* des Inhaltstransfers abgeschlossen und die *Aufnahmephase* zur Aufnahme von Inhalt in Ihre *Staging*- oder *Produktionsinstanzen* von AEM as a Cloud Service begonnen wird, müssen Sie ein Support-Ticket erstellen, um Adobe über Ihre Absicht zu informieren, eine *Aufnahme* auszuführen, damit Adobe sicherstellen kann, dass der *Aufnahmevorgang* nicht unterbrochen wird. Erstellen Sie das Support-Ticket 1 Woche vor dem geplanten *Aufnahmedatum*. Sobald Sie das Support-Ticket eingereicht haben, wird Sie das Support-Team über die nächsten Schritte informieren.
   * Erstellen Sie ein Support-Ticket mit den folgenden Details:
      * Genaues Datum und geschätzte Uhrzeit (mit Ihrer Zeitzone), zu der Sie die *Aufnahmephase* starten möchten.
      * Umgebungstyp (Phase oder Produktion), in den Sie Daten aufnehmen möchten.
      * Programm-ID.

* Die *Ingestion Phase* für den Autor skaliert die gesamte Autorenbereitstellung. In anderen Worten, die Autoreninstanz von AEM ist während des gesamten Aufnahmevorgangs nicht verfügbar. Stellen Sie auch sicher, dass keine Cloud Manager-Pipelines ausgeführt werden, während Sie die *Aufnahmephase* ausführen.

* Bei Verwendung von `Amazon S3` oder `Azure` als Datenspeicher auf dem AEM-Quellsystem sollte der Datenspeicher so konfiguriert werden, dass die gespeicherten Blobs nicht gelöscht werden können (Garbage Collector). Auf diese Weise wird die Integrität der Indexdaten sichergestellt, und ein Fehler bei der Konfiguration dieser Art kann zu fehlerhaften Extraktionen führen, da diese Indexdaten nicht einwandfrei sind.

* Wenn Sie benutzerdefinierte Indizes verwenden, müssen Sie sicherstellen, dass die benutzerdefinierten Indizes mit dem Knoten `tika` konfiguriert werden, bevor Sie Content Transfer Tool ausführen. Weitere Informationen finden Sie unter [Vorbereiten der neuen Indexdefinition](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=en#preparing-the-new-index-definition).

## Verfügbarkeit {#availability}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_download"
>title="Download"
>abstract="Das Content Transfer Tool kann als ZIP-Datei aus dem Software Distribution-Portal heruntergeladen werden. Sie können das Paket über Package Manager in Ihrer Quellinstanz von Adobe Experience Manager (AEM) installieren. Laden Sie unbedingt die neueste Version herunter."
>additional-url="https://docs.adobe.com/content/help/en/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html" text="Versionshinweise"
>additional-url="https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html" text="Software Distribution Portal"

Das Content Transfer Tool kann als ZIP-Datei aus dem Software Distribution-Portal heruntergeladen werden. Sie können das Paket über Package Manager in Ihrer Quellinstanz von Adobe Experience Manager (AEM) installieren. Laden Sie unbedingt die neueste Version herunter. Weitere Informationen zur neuesten Version finden Sie in den [Versionshinweisen](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html).

>[!NOTE]
>Laden Sie das Content Transfer Tool vom [Software Distribution-Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) herunter.

## Ausführen des Content Transfer Tools {#running-tool}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_demo"
>title="Ausführen des Inhaltsübermittlungstools"
>abstract="Erfahren Sie, wie Sie mit dem Inhaltsübermittlungstool Inhalte als Cloud Service (Autor/Veröffentlichen) in AEM migrieren können."
>additional-url="https://video.tv.adobe.com/v/35460/?quality=12&amp;learn=on" text=" Siehe Demo"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/content-transfer-tool.html?lang=de#migration" text="Übung - Verwenden des Inhaltsübermittlungstools"

>[!VIDEO](https://video.tv.adobe.com/v/35460/?quality=12&learn=on)


In diesem Abschnitt erfahren Sie, wie Sie mit dem Content Transfer Tool Inhalte zu AEM as a Cloud Service (Autor/Veröffentlichung) migrieren:

1. Wählen Sie das Adobe Experience Manager und navigieren Sie zu Tools -> **Vorgänge** -> **Inhaltsmigration**.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ctt-entry-card01.png)

1. Wählen Sie im Assistenten **Inhaltsmigration** die Option **Inhaltsübertragung**.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/ctt-entry-card02.png)


1. Die Konsole unten wird angezeigt, wenn Sie den ersten Migrationssatz erstellen. Klicken Sie auf **Migrationssatz erstellen**, um einen neuen Migrationssatz zu erstellen.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/01-create-migrationset.png)


   >[!NOTE]
   >Wenn Sie bereits über Migrationssätze verfügen, zeigt die Konsole die Liste der vorhandenen Migrationssätze mit ihrem aktuellen Status an.

   Klicken Sie außerdem auf **Konfiguration der Benutzerzuordnung erstellen**, um auf das [Tool für die Benutzerzuordnung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=en#using-user-mapping-tool) zuzugreifen.

1. Füllen Sie die Felder im Bildschirm **Migrationsset erstellen** aus, wie unten beschrieben.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/migration-set-creation-04.png)

   1. **Name**: Geben Sie den Namen des Migrationssatzes ein.
      >[!NOTE]
      >Beim Namen des Migrationssatzes sind keine Sonderzeichen zulässig.

   1. **Cloud Service-Konfiguration**: Geben Sie die Ziel-URL der Autoreninstanz von AEM as a Cloud Service an.

      >[!NOTE]
      >Sie können während der Aktivität der Inhaltsübertragung maximal zehn Migrationssätze gleichzeitig erstellen und verwalten.
      >Darüber hinaus müssen Sie für jede der spezifischen Umgebungen – *Staging*, *Entwicklung* und *Produktion* – eine separate Migration erstellen.

   1. **Zugriffs-Token**: Geben Sie das Zugriffs-Token ein.

      >[!NOTE]
      >Sie können das Zugriffs-Token über die Schaltfläche **Zugriffs-Token öffnen** abrufen. Sie müssen sicherstellen, dass Sie in der Zielgruppe Cloud Service-Instanz zur Gruppe AEM Administratoren gehören.

   1. **Parameter**: Wählen Sie die folgenden Parameter aus, um den Migrationssatz zu erstellen:

      1. **Version einschließen**: Aktivieren Sie die Option.

      1. **Zuordnung von IMS-Benutzern und -Gruppen** einschließen: Wählen Sie die Option, um die Zuordnung aus IMS-Benutzern und -Gruppen einzuschließen.
Weitere Informationen finden Sie unter [Tool für die Benutzerzuordnung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=de).

      1. **Einzuschließende Pfade**: Verwenden Sie den Pfad-Browser, um zu migrierende Pfade auszuwählen. Die Pfadauswahl akzeptiert Eingaben durch Eingabe von Text oder Auswahl.

         >[!IMPORTANT]
         >Die folgenden Pfade sind beim Erstellen eines Migrationssatzes eingeschränkt:
         >* `/apps`
         >* `/libs`
         >* `/home`
         >* `/etc` (einige  `/etc` Pfade dürfen in CTT ausgewählt werden)


1. Klicken Sie auf **Speichern**, nachdem Sie alle Felder im Detailbildschirm **Migrationsset erstellen** ausgefüllt haben.

1. Der Migrationssatz erscheint auf der Seite *Übersicht*.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/04-item-selection-and-quick-actions.png)

   Alle auf diesem Bildschirm vorhandenen Migrationssets werden auf der Seite *Übersicht* mit ihren aktuellen Status- und Statusinformationen angezeigt. Ggf. sehen Sie einige der unten beschriebenen Symbole.

   * Eine *rote Wolke* bedeutet, dass Sie den Extraktionsvorgang nicht abschließen können.
   * Eine *grüne Cloud* gibt an, dass Sie die Extraktion abschließen können.
   * Ein *gelbes Symbol* weist darauf hin, dass Sie den vorhandenen Migrationssatz nicht erstellt haben und dass der betreffende Migrationssatz von einem anderen Benutzer in derselben Instanz erstellt wurde.

1. Wählen Sie auf der Übersichtsseite einen Migrationssatz aus und klicken Sie auf **Eigenschaften**, um die Migrationssatzeigenschaften anzuzeigen oder zu bearbeiten. Beim Bearbeiten von Eigenschaften ist es nicht möglich, den Namen des Containers oder die Service-URL zu ändern.


### Extraktionsvorgang beim Inhaltstransfer {#extraction-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_extraction"
>title="Content Extraktion"
>abstract="Extraktion bezieht sich auf das Extrahieren von Inhalten aus der Quell-AEM-Instanz in einen temporären Bereich, der als Migrationssatz bezeichnet wird. Ein Migrationssatz ist ein Cloud-Speicherplatzbereich, der von Adobe bereitgestellt wird, um die übertragenen Inhalte vorübergehend zwischen der AEM-Quellinstanz und der Cloud Service-AEM-Instanz zu speichern."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#top-up-extraction-process" text="Extraktion oben"

Gehen Sie wie folgt vor, um den Migrationssatz aus dem Content Transfer Tool zu extrahieren:

1. Wählen Sie auf der Seite *Übersicht* einen Migrationssatz aus und klicken Sie auf **Extrahieren**, um die Extraktion zu starten. Das Dialogfeld **Extraktion des Migrationssatzes** wird angezeigt. Klicken Sie auf **Extrahieren**, um die Extraktion zu starten.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/06-content-extraction.png)

   >[!NOTE]
   >Sie haben die Möglichkeit, Staging-Container während der Extraktion zu überschreiben.


1. Im Feld **EXTRAKTION** wird jetzt der Status **WIRD AUSGEFÜHRT** angezeigt, um anzugeben, dass die Extraktion ausgeführt wird.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/07-extraction-job-running.png)

   Sobald die Extraktion abgeschlossen ist, wird der Status des Migrationssatzes auf **BEENDET** aktualisiert und unter dem Feld *INFO* wird ein **grünes** Wolkensymbol angezeigt.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/10-extraction-complete.png)

   >[!NOTE]
   >Die Benutzeroberfläche verfügt über eine Funktion zum automatischen Neuladen, mit der die Übersichtsseite alle 30 Sekunden neu geladen wird.
   >Beim Starten der Extraktionsphase wird die Schreibsperre aktiviert und nach *60 Sekunden* wieder aufgehoben. Wenn also eine Extraktion gestoppt wird, müssen Sie eine Minute warten, bis die Sperre aufgehoben wird, bevor Sie die Extraktion erneut starten können.

#### Auffüllextraktion {#top-up-extraction-process}

Das Content Transfer Tool verfügt über eine Funktion, die die differenzielle Auffüllung von Inhalten unterstützt, wobei es möglich ist, nur Änderungen zu übertragen, die seit dem vorherigen Inhaltstransfer vorgenommen wurden.

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

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion"
>title="Inhaltsaufnahme"
>abstract="&quot;Einschluss&quot;bezieht sich auf die Inhaltsaufnahme aus der Migration, die in der Zielgruppe Cloud Service-Instanz festgelegt ist. Das Content Transfer Tool verfügt über eine Funktion, die die differenzielle Auffüllung von Inhalten unterstützt, wobei es möglich ist, nur Änderungen zu übertragen, die seit dem vorherigen Inhaltstransfer vorgenommen wurden."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#top-up-ingestion-process" text="Auffüllaufnahme"

Gehen Sie wie folgt vor, um den Migrationssatz aus dem Content Transfer Tool aufzunehmen:

1. Wählen Sie auf der Seite *Übersicht* einen Migrationssatz aus und klicken Sie auf **Aufnehmen**, um die Aufnahme zu starten. Das Dialogfeld **Aufnahme des Migrationssatzes** wird angezeigt. Klicken Sie auf **Aufnehmen**, um die Aufnahmephase zu starten. Es ist möglich, Inhalte gleichzeitig in der Autoren- und Veröffentlichungsinstanz aufzunehmen.

   >[!IMPORTANT]
   >Wenn die Option **Vorhandenen Inhalt in der Cloud-Instanz vor der Erfassung löschen** aktiviert ist, wird das gesamte vorhandene Repository gelöscht und ein neues Repository erstellt, in dem Inhalte erfasst werden. Das bedeutet, dass alle Einstellungen einschließlich der Berechtigungen für die Cloud Service-Zielinstanz zurückgesetzt werden. Dies gilt auch für Administratoren, die der Gruppe **administrators** hinzugefügt werden.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/content-ingestion-01.png)

   Klicken Sie außerdem auf **Kundendienst**, um ein Ticket zu protokollieren, wie in der Abbildung oben dargestellt. Weitere Informationen finden Sie unter [Wichtige Überlegungen zur Verwendung des Inhaltsübermittlungstools](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#pre-reqs).

1. Sobald die Aufnahme abgeschlossen ist, wird der Status im Feld **AUFNAHME VERÖFFENTLICHEN** in **BEENDET** aktualisiert.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/15-ingestion-complete.png)

#### Auffüllaufnahme {#top-up-ingestion-process}

Das Content Transfer Tool verfügt über eine Funktion, die die differenzielle *Auffüllung* von Inhalten unterstützt, wobei es möglich ist, nur Änderungen zu übertragen, die seit dem vorherigen Inhaltstransfer vorgenommen wurden.

>[!NOTE]
>
>Nach dem ersten Transfer von Inhalten wird empfohlen, häufige differenzielle Auffüllungen des Inhalts durchzuführen, um den Zeitraum für das Einfrieren des Inhalts für den endgültigen differenziellen Inhaltstransfer zu verkürzen, bevor er in Cloud Service live geschaltet wird.

Sobald die Aufnahme abgeschlossen ist, können Sie Delta-Inhalte mithilfe der Auffüllaufnahme übertragen. Führen Sie dazu folgende Schritte durch:

1. Navigieren Sie zur Seite *Übersicht* und wählen Sie den Migrationssatz aus, für den Sie die Auffüllaufnahme durchführen möchten. Klicken Sie auf **Aufnehmen**, um die Auffüllaufnahme zu starten. Das Dialogfeld **Aufnahme des Migrationssatzes** wird angezeigt.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets/content-ingestion-01.png)

   >[!IMPORTANT]
   >Sie sollten die Option **Vorhandenen Inhalt in der Cloud-Instanz vor der Aufnahme löschen** deaktivieren, um zu verhindern, dass der vorhandene Inhalt aus der vorherigen Aufnahmeaktivität gelöscht wird. Klicken Sie außerdem auf **Kundendienst**, um ein Ticket zu protokollieren, wie in der Abbildung oben dargestellt.


### Anzeigen von Protokollen für einen Migrationssatz {#viewing-logs-migration-set}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_logs"
>title="Anzeigen von Protokollen"
>abstract="Nach Abschluss der Extraktion der Ingestion überprüfen Sie die Protokolle auf Fehler/Warnungen. Eventuelle Fehler sollten sofort behoben werden, entweder durch Behandlung der gemeldeten Probleme oder durch Kontaktaufnahme mit der Adobe."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#troubleshooting" text="Fehlerbehebung"
>additional-url="https://helpx.adobe.com/ca/enterprise/admin-guide.html/ca/enterprise/using/support-for-experience-cloud.ug.html" text="Kontaktaufnahme mit dem Adobe-Support"

Überprüfen Sie nach Abschluss der einzelnen Schritte (Extraktion und Erfassung) die Protokolle und suchen Sie nach Fehlern.  Eventuelle Fehler sollten sofort behoben werden, entweder durch Behandlung der gemeldeten Probleme oder durch Kontaktaufnahme mit der Adobe.

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

Wenn, wie unten erwähnt, fehlende Blob-IDs gemeldet werden, müssen Sie eine Konsistenzprüfung im bestehenden Repository durchführen und die fehlenden BLOBs wiederherstellen.
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

Als Benutzer sehen Sie möglicherweise die folgenden Verhaltensänderungen in der Benutzeroberfläche für das Content Transfer Tool:

* Die Symbole in der Benutzeroberfläche des Content Transfer Tools unterscheiden sich möglicherweise von den in diesem Handbuch gezeigten Screenshots oder werden je nach Version der AEM-Quellinstanz überhaupt nicht angezeigt.
