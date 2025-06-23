---
title: 'Erste Schritte mit dem Content Transfer Tool  '
description: Erfahren Sie mehr über die ersten Schritte mit dem Content Transfer Tool
exl-id: c0cecf65-f419-484b-9d55-3cbd561e8dcd
feature: Migration
role: Admin
source-git-commit: 0c76419b5efa6d45cf4db51990633fea3b489063
workflow-type: ht
source-wordcount: '1654'
ht-degree: 100%

---


# Erste Schritte mit dem Content Transfer Tool {#getting-started-content-transfer-tool}


## Verfügbarkeit {#availability}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_download"
>title="Download"
>abstract="Das Content Transfer Tool kann als ZIP-Datei aus dem Software Distribution-Portal heruntergeladen werden. Sie können das Paket über Package Manager in Ihrer Quellinstanz von Adobe Experience Manager (AEM) installieren. Laden Sie unbedingt die neueste Version herunter."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/release-notes/release-notes-current.html?lang=de" text="Versionshinweise"
>additional-url="https://experience.adobe.com/#/downloads/content/software-distribution/de/aemcloud.html" text="Software Distribution-Portal"

Das Content Transfer Tool kann als ZIP-Datei aus dem Software Distribution-Portal heruntergeladen werden. Sie können das Paket über [Package Manager](/help/implementing/developing/tools/package-manager.md) in Ihrer Quellinstanz von Adobe Experience Manager (AEM) installieren. Laden Sie unbedingt die neueste Version herunter. Weitere Informationen zur neuesten Version finden Sie in den [Versionshinweisen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/release-notes/release-notes-current.html?lang=de).

Nur Version 2.0.0 und höher wird unterstützt, und es wird empfohlen, die neueste Version zu verwenden.

>[!NOTE]
>Laden Sie das Content Transfer Tool vom [Software Distribution-Portal](https://experience.adobe.com/#/downloads/content/software-distribution/de/aemcloud.html) herunter.

## Konnektivität der Quellumgebung {#source-environment-connectivity}

>[!NOTE]
>
>Ein Verbindungsfehler kann auch auftreten, wenn ein Migrationssatz aus Cloud Acceleration Manager gelöscht wurde.

Die Quell-AEM-Instanz wird möglicherweise hinter einer Firewall ausgeführt, wo sie nur bestimmte Hosts erreichen kann, die zu einer Zulassungsliste hinzugefügt wurden. Damit eine Extraktion erfolgreich durchgeführt werden kann, muss von der Instanz, auf der AEM ausgeführt wird, auf die folgenden Endpunkte zugegriffen werden können:

* Der Azure Blob Storage-Service: `casstorageprod.blob.core.windows.net`

>[!NOTE]
>Wenn die Extraktion aufgrund des Fehlers „javax.net.ssl.SSLHandshakeException: sun.security.validator.ValidatorException: PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target“ fehlschlägt, kann dies durch Importieren des entsprechenden CA-Zertifikats behoben werden.

### Aktivieren der SSL-Protokollierung {#enable-ssl-logging}

SSL-/TLS-Verbindungsprobleme zu verstehen kann manchmal schwierig sein. Um Verbindungsprobleme während eines Extraktionsprozesses zu beheben, können Sie die SSL-Protokollierung über die Systemkonsole der AEM-Quellumgebung aktivieren, indem Sie die folgenden Schritte ausführen:

1. Navigieren Sie zur Adobe Experience Manager Web-Konsole in Ihrer Quellinstanz, indem Sie zu **Tools > Vorgänge > Web-Konsole** gehen oder direkt zur URL unter *https://serveraddress:serverport/system/console/configMgr*
1. Suchen Sie nach **Konfiguration des Content Transfer Tool-Extrahierungs-Service**
1. Über die Schaltfläche mit dem Stiftsymbol können Sie die Konfigurationswerte bearbeiten
1. Aktivieren Sie die **SSL-Protokollierung für Extraktion aktivieren** Einstellung festlegen, und drücken Sie dann **Speichern**:

   ![image](/help/journey-migration/content-transfer-tool/assets/enable_ssl_logging.png)

>[!NOTE]
>Diese Markierung dient nur zum Debugging von SSL-Problemen. Stellen Sie sicher, dass die Markierung vor dem Ausführen der Extraktion deaktiviert ist, da sie möglicherweise eine große Menge an Festplattenspeicher erfordert. Dies könnte potenziell die Laufwerkskapazität überfüllen und dazu führen, dass der Extraktionsprozess fehlschlägt.

## Ausführen des Content Transfer Tools {#running-tool}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_demo"
>title="Ausführen des Content Transfer Tools"
>abstract="In diesem Abschnitt erfahren Sie, wie Sie mit dem Content Transfer Tool Inhalte zu AEM as a Cloud Service (Autor/Veröffentlichung) migrieren."
>additional-url="https://video.tv.adobe.com/v/327075/?quality=12&amp;learn=on&amp;captions=ger&captions=ger" text=" Siehe Demo"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/content-transfer-tool.html?lang=de#migration" text="Tutorial – Verwenden des Content Transfer Tools"

Der folgende Abschnitt gilt für die neue Content Transfer Tool-Version. In diesem Abschnitt erfahren Sie, wie Sie mit dem Content Transfer Tool Inhalte zu AEM as a Cloud Service migrieren:

### Phase der Extraktionseinrichtung {#extraction-setup-phase}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_extraction_setup"
>title="Phase der Extraktionseinrichtung"
>abstract="Erfahren Sie, wie Sie einen Migrationssatz erstellen und verwalten und den Extraktionsschlüssel kopieren."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/content-transfer-tool.html?lang=de#migration" text="Tutorial – Verwenden des Content Transfer Tools"

<!-- Contextualhelp id "aemcloud_ctt_extraction_setup" must be added here -->

1. Melden Sie sich bei Cloud Acceleration Manager (CAM) an und klicken Sie auf das zuvor erstellte CAM-Projekt, um zu beurteilen, ob Sie für den Wechsel zu AEM as a Cloud Service bereit sind. Wenn Sie kein CAM-Projekt erstellt haben, lesen Sie den Abschnitt über das Erstellen und Verwalten eines Projekts in CAM.

1. Klicken Sie auf die Karte **Inhaltsübertragung**, um die Listenansicht der Migrationssätze zu öffnen.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam1.png)

1. Erstellen Sie einen Migrationssatz, indem Sie auf **Migrationssatz erstellen** klicken.

   >[!NOTE]
   >
   >In Cloud Acceleration Manager können pro Projekt maximal 10 Migrationssätze, einschließlich abgelaufener Sätze, erstellt werden.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam2.png)

   Das folgende Dialogfeld wird angezeigt. Beachten Sie, dass ein Migrationssatz nach einer längeren Inaktivitätsdauer abläuft. Nachdem entsprechende Warnungen auf der Projektkarte und in den Tabellenzeilen für den Migrationsvorgang über einen bestimmten Zeitraum angezeigt wurden, läuft der Migrationssatz ab, und die zugehörigen Daten sind nicht mehr verfügbar. Lesen Sie [Ablauf von Migrationssätzen](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/overview-content-transfer-tool.md#migration-set-expiry), um mehr darüber zu erfahren.

   Bei der Erstellung des Migrationssatzes können Sie die geografische Region auswählen, in der die temporären Migrationsdaten gespeichert werden.  Es wird empfohlen, die Region auszuwählen, die Ihrer Cloud-Zielumgebung am nächsten ist, um eine optimale Leistung bei der Aufnahme sicherzustellen.  Die Region kann nach der Erstellung des Migrationssatzes nicht mehr geändert werden. Um eine andere Region zu verwenden, müssen Sie einen neuen Migrationssatz erstellen.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam3.png)

   >[!NOTE]
   >
   >Der Name muss denselben Konventionen wie bei einem AEM-Knoten entsprechen, d. h., er darf keines der folgenden Zeichen enthalten: . / : [ ] | * &lt; > ^ ? { } % # `` oder ungewöhnliche Symbole oder Emojis.

1. Ihre Migrationsliste sollte jetzt in der Listenansicht angezeigt werden. Klicken Sie auf Drei-Punkte-Symbol (**…**), um die Dropdown-Liste zu öffnen, und wählen Sie **Extraktionsschlüssel kopieren** aus. Sie benötigen diesen Schlüssel während der Extraktionsphase. Kopieren Sie diesen Extraktionsschlüssel.

   >[!NOTE]
   >
   >Der Extraktionsschlüssel ermöglicht es Ihrer AEM-Quellumgebung, eine sichere Verbindung mit dem Migrationssatz herzustellen. Behandeln Sie diesen Schlüssel mit der gleichen Sorgfalt wie ein Kennwort und geben Sie ihn nie über ein unsicheres Medium wie E-Mail weiter.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam4.png)

### Füllen des Migrationssatzes {#populating-the-migration-set}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_populate_migrationset"
>title="Füllen des Migrationssatzes"
>abstract="Nach dem Erstellen eines Migrationssatzes muss er mit dem Inhalt aus der Quellinstanz gefüllt werden, die in die AEM as a Cloud Service-Umgebung verschoben werden muss. Dazu muss das Inhaltstransfer-Tool in der Quellinstanz installiert sein."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/extracting-content.html?lang=de" text="Extrahieren von Inhalten"

Um den von Ihnen in Cloud Acceleration Manager erstellten Migrationssatz zu befüllen, müssen Sie die neueste Content Transfer Tool-Version auf Ihrer Adobe Experience Manager-Quellinstanz (AEM) installieren. In diesem Abschnitt erfahren Sie, wie Sie den Migrationssatz befüllen.

1. Nachdem Sie die neueste Version des Content Transfer Tools auf Ihrer Quellinstanz für Adobe Experience Manager installiert haben, navigieren Sie zu **Vorgänge – Inhaltsmigration**

1. Klicken Sie auf **Migrationssatz erstellen**.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam5.png)

1. Fügen Sie den zuvor aus CAM kopierten Extraktionsschlüssel in das Eingabefeld für den Extraktionsschlüssel im Formular **Migrationssatz erstellen** ein. Danach werden die Felder für den Migrationssatznamen und den Cloud Acceleration Manager(CAM)-Projektnamen automatisch ausgefüllt. Diese sollten mit dem Migrationssatznamen in CAM und dem von Ihnen erstellten CAM-Projektnamen übereinstimmen. Sie können jetzt Inhaltspfade hinzufügen. Speichern Sie den Migrationssatz, nachdem Sie Inhaltspfade hinzugefügt haben. Sie können die Extraktion mit eingeschlossenen oder ausgeschlossenen Versionen ausführen.

   >[!NOTE]
   >
   >Vergewissern Sie sich, dass der Extraktionsschlüssel gültig und nicht kurz vor seinem Ablaufdatum ist. Diese Informationen finden Sie im Dialogfeld **Migrationssatz erstellen**, nachdem Sie den Extraktionsschlüssel eingefügt haben. Wenn Sie einen Verbindungsfehler erhalten, finden Sie unter [Konnektivität der Quellumgebung](#source-environment-connectivity) weitere Informationen.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/createMigrationSet.png)

1. Wählen Sie dann die folgenden Parameter aus, um den Migrationssatz zu erstellen:

   1. **Version einschließen**: Aktivieren Sie die Option. Wenn Versionen enthalten sind, wird der Pfad `/var/audit` automatisch einbezogen, um Prüfereignisse zu migrieren.

      ![image](/help/journey-migration/content-transfer-tool/assets-ctt/includeVersion.png)

      >[!NOTE]
      >Wenn Sie beabsichtigen, Versionen als Teil eines Migrationssatzes einzubeziehen und Auffüllungen mit `wipe=false` durchzuführen, müssen Sie aufgrund einer aktuellen Einschränkung im Content Transfer Tool die Versionsbereinigung deaktivieren. Wenn Sie es vorziehen, die Versionsbereinigung aktiviert zu lassen und in einen Migrationssatz aufzufüllen, dann müssen Sie die Aufnahme als `wipe=true` durchführen.

      >[!NOTE]
      >Mit der CTT-Version (3.0.24) wurden neue Funktionen in das Content Transfer Tool aufgenommen, die das Ein- und Ausschließen von Pfaden optimieren. Zuvor mussten Pfade einzeln ausgewählt werden, was mühsam und zeitaufwändig war. Benutzende können jetzt Pfade direkt über die Benutzeroberfläche einschließen oder eine CSV-Datei entsprechend ihren Anforderungen hochladen.  Die CSV-Datei darf nur einen Pfad pro Zeile und keine Kommas enthalten.

   1. **Einzuschließende Pfade**: Verwenden Sie den Pfad-Browser, um zu migrierende Pfade auszuwählen. Die Pfadauswahl akzeptiert Eingaben durch Eingabe von Text oder Auswahl. Benutzende können nur eine Option zum Einfügen von Pfaden auswählen: entweder über die Benutzeroberfläche oder durch Hochladen einer CSV-Datei.
      >[!IMPORTANT]
      >Die folgenden Pfade sind beim Erstellen eines Migrationssatzes eingeschränkt:
      >* `/apps`
      >* `/libs`
      >* `/home`
      >* `/etc` (einige `/etc`-Pfade können in CTT ausgewählt werden)

      ![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/includeAndExcludePath.png)

      1. Nur die Pfadauswahl ist zulässig und mindestens ein Pfad muss vorhanden sein. Wenn kein Pfad ausgewählt ist, tritt ein Server-Fehler auf.

         ![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/ServerError.png)

      1. Bei Verwendung der **Option „CSV-Upload“** muss die CSV-Datei gültige Pfade enthalten.

         ![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/validCsvUpload.png)

      1. Um zur Pfadauswahl zurückzukehren, müssen Benutzende die Seite aktualisieren und von vorne beginnen.

      1. Wenn **ungültige Pfade** in der hochgeladenen CSV-Datei gefunden werden, werden die ungültigen Pfade in einem gesonderten Dialogfeld angezeigt.

         ![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/invalidPathsInCsv.png)

      1. Benutzende müssen die CSV-Datei korrigieren und erneut hochladen oder die Benutzeroberfläche aktualisieren, um Pfade über die Pfadauswahl auszuwählen.

   1. **Auszuschließende Pfade**: Eine neue Funktion ermöglicht es Benutzenden, bestimmte Pfade auszuschließen, wenn diese nicht eingeschlossen werden sollen. Wenn der Pfad im Abschnitt „Einschließen“ beispielsweise „/content/dam“ lautet, können Benutzende jetzt Pfade wie „/content/dam/catalogs“ ausschließen.

      ![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/excludePathHighlighted.png)

1. Klicken Sie auf **Speichern**, nachdem Sie alle Felder im Bildschirm **Migrationssatz erstellen** ausgefüllt haben.

<!-- 1. You will view your migration set in the **Content Transfer** wizard, as shown in the figure below.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ctt07.png)

   All the existing migration sets are displayed on the **Content Transfer** wizard with their current status and status information. You may see some of these icons described below.

   * A *red cloud* indicates that you cannot complete the extraction process.
   * A *green cloud* indicates that you can complete the extraction process.
   * A *yellow icon* indicates that you did not create the existing migration set and the specific one is created by some other user in the same instance.

1. Select a migration set and click **Properties** to view or edit the migration set properties. While editing properties, it is not possible to change the **Migration Set name** or the **Service URL**. 

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ctt06.png) -->

### Bestimmen der Größe des Migrationssatzes {#migration-set-size}

Nach dem Erstellen eines Migrationssatzes wird dringend empfohlen, eine Größenüberprüfung des Migrationssatzes durchzuführen, bevor ein Extraktionsprozess gestartet wird.
Durch eine Größenüberprüfung des Migrationssatzes können Sie:

* feststellen, ob im `crx-quickstart`-Unterverzeichnis genügend Festplattenspeicher vorhanden ist, um die Extraktion erfolgreich abzuschließen.
* bestimmen, ob die Größe des Migrationssatzes unter die unterstützten Produktbeschränkungen fällt, und fehlgeschlagene Inhaltsaufnahmen vermeiden.

Gehen Sie wie folgt vor, um eine Größenüberprüfung durchzuführen:

1. Wählen Sie einen Migrationssatz aus und klicken Sie auf **Größe überprüfen**.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam8.png)

1. Dadurch wird das Dialogfeld **Größe überprüfen** angezeigt.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/checkMigrationSetSize.png)

1. Klicken Sie auf **Größe überprüfen**, um den Prozess zu starten. Sie kehren dann zur Listenansicht des Migrationssatzes zurück und sollten eine Meldung sehen, die besagt, dass eine **Größenprüfung** ausgeführt wird.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam10.png)

1. Sobald der Prozess **Größe überprüfen** abgeschlossen ist, ändert sich der Status in **BEENDET**. Wählen Sie denselben Migrationssatz aus und klicken Sie auf **Größe überprüfen**, um die Ergebnisse anzuzeigen. Nachfolgend finden Sie ein Beispiel für Ergebnisse des Prozesses **Größe überprüfen** ohne Warnungen.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/checkSizeAfterFinished.png)

1. Wenn die Ergebnisse des Prozesses **Größe überprüfen** darauf hindeuten, dass entweder nicht genügend Speicherplatz vorhanden ist und/oder der Migrationssatz die Produktbeschränkungen überschreitet, wird der Status **WARNUNG** angezeigt.

<!--   ![image](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image6.png)
   
   Below is an example of **Check Size** results with warnings.
 
   ![image](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image7.png) -->


## Wie geht es weiter {#whats-next}

Nachdem Sie gelernt haben, wie Sie einen Migrationssatz erstellen, können Sie im Content Transfer Tool jetzt mehr über Extraktions- und Aufnahmeprozesse erfahren. Bevor Sie diese Prozesse erlernen, müssen Sie sich mit dem [Umgang mit großen Inhalts-Repositorys](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md) befassen, um die Extraktions- und Aufnahmephasen der Inhaltsübertragungsaktivität zum Verschieben von Inhalten zu AEM as a Cloud Service erheblich zu beschleunigen.
