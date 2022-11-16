---
title: Erste Schritte mit dem Content Transfer Tool
description: Erste Schritte mit dem Content Transfer Tool
exl-id: c0cecf65-f419-484b-9d55-3cbd561e8dcd
source-git-commit: 1dfef0f1157ead7f1240e9a41794436197136daa
workflow-type: tm+mt
source-wordcount: '1327'
ht-degree: 95%

---

# Erste Schritte mit dem Content Transfer Tool {#getting-started-content-transfer-tool}


## Verfügbarkeit {#availability}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_download"
>title="Download"
>abstract="Das Content Transfer Tool kann als ZIP-Datei aus dem Software Distribution-Portal heruntergeladen werden. Sie können das Paket über Package Manager in Ihrer Quellinstanz von Adobe Experience Manager (AEM) installieren. Laden Sie unbedingt die neueste Version herunter."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html" text="Versionshinweise"
>additional-url="https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html" text="Software Distribution-Portal"

Das Content Transfer Tool kann als ZIP-Datei aus dem Software Distribution-Portal heruntergeladen werden. Sie können das Paket über [Package Manager](/help/implementing/developing/tools/package-manager.md) in Ihrer Quellinstanz von Adobe Experience Manager (AEM) installieren. Laden Sie unbedingt die neueste Version herunter. Weitere Informationen zur neuesten Version finden Sie in den [Versionshinweisen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=de).

>[!NOTE]
>Laden Sie das Content Transfer Tool vom [Software Distribution-Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) herunter.

## Konnektivität der Quellumgebung {#source-environment-connectivity}

>[!NOTE]
>
>Ein Verbindungsfehler kann auch auftreten, wenn ein Migrationssatz aus Cloud Acceleration Manager gelöscht wurde.

Die Quell-AEM-Instanz wird möglicherweise hinter einer Firewall ausgeführt, wo sie nur bestimmte Hosts erreichen kann, die zu einer Zulassungsliste hinzugefügt wurden. Damit eine Extraktion erfolgreich durchgeführt werden kann, muss von der Instanz, auf der AEM ausgeführt wird, auf die folgenden Endpunkte zugegriffen werden können:

* Der Azure Blob Datenspeicherungs-Service: `casstorageprod.blob.core.windows.net`
* Der IO-Endpunkt der Benutzerzuordnung: `usermanagement.adobe.io`

>[!NOTE]
>Wenn die Extraktion aufgrund des folgenden Fehlers fehlschlägt: &quot;javax.net.ssl.SSLHandshakeException: sun.security.validator.ValidatorException: PKIX-Pfadaufbau fehlgeschlagen: sun.security.provider.certpath.SunCertPathBuilderException: kein gültiger Zertifizierungspfad zur angeforderten Zielgruppe gefunden werden kann&quot;, kann dies durch Importieren des entsprechenden Zertifizierungsstellenzertifikats behoben werden.

### Aktivieren der SSL-Protokollierung {#enable-ssl-logging}

SSL-/TLS-Verbindungsprobleme zu verstehen kann manchmal schwierig sein. Um Verbindungsprobleme während eines Extraktionsprozesses zu beheben, können Sie die SSL-Protokollierung über die Systemkonsole der AEM-Quellumgebung aktivieren, indem Sie die folgenden Schritte ausführen:

1. Sie gelangen zur Adobe Experience Manager Web-Konsole in Ihrer Quellinstanz, indem Sie zu **Tools – Vorgänge – Web-Konsole** gehen oder direkt zur URL unter *https://serveraddress:serverport/system/console/configMgr*
1. Suchen Sie nach **Konfiguration des Content Transfer Tool-Extrahierungs-Service**
1. Über die Schaltfläche mit dem Stiftsymbol können Sie die Konfigurationswerte bearbeiten
1. Aktivieren Sie die **SSL-Protokollierung für Extraktion aktivieren** Einstellung festlegen, und drücken Sie dann **Speichern**:

   ![image](/help/journey-migration/content-transfer-tool/assets/enable_ssl_logging.png)


## Ausführen des Content Transfer Tools {#running-tool}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_demo"
>title="Ausführen des Content Transfer Tools"
>abstract="In diesem Abschnitt erfahren Sie, wie Sie mit dem Content Transfer Tool Inhalte zu AEM as a Cloud Service (Autor/Veröffentlichung) migrieren."
>additional-url="https://video.tv.adobe.com/v/35460/?quality=12&amp;learn=on&amp;captions=ger" text=" Siehe Demo"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/content-transfer-tool.html?lang=de#migration" text="Tutorial – Verwenden des Content Transfer Tools"

Der folgende Abschnitt gilt für die neue Content Transfer Tool-Version. In diesem Abschnitt erfahren Sie, wie Sie mit dem Content Transfer Tool Inhalte zu AEM as a Cloud Service migrieren:

### Phase der Extraktionseinrichtung {#extraction-setup-phase}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_extraction_setup"
>title="Phase der Extraktionseinrichtung"
>abstract="Erfahren Sie, wie Sie einen Migrationssatz erstellen und den Extraktionsschlüssel kopieren."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/content-transfer-tool.html?lang=en#migration" text="Tutorial – Verwenden des Content Transfer Tools"

<!-- Contextualhelp id "aemcloud_ctt_extraction_setup" needs to be added here -->

1. Melden Sie sich bei Cloud Acceleration Manager (CAM) an und klicken Sie auf das zuvor erstellte CAM-Projekt, um zu beurteilen, ob Sie für den Wechsel zu AEM as a Cloud Service bereit sind. Wenn Sie kein CAM-Projekt erstellt haben, lesen Sie den Abschnitt über das Erstellen und Verwalten eines Projekts in CAM.

1. Klicken Sie auf die Karte **Inhaltsübertragung**. Dadurch gelangen Sie zur Listenansicht der Migrationssätze.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam1.png)

1. Erstellen Sie einen Migrationssatz, indem Sie auf **Migrationssatz erstellen** klicken.

   >[!NOTE]
   >
   >In Cloud Acceleration Manager können maximal fünf Migrationssätze pro Projekt erstellt werden.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam2.png)

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam3.png)

1. Ihre Migrationsliste sollte jetzt in der Listenansicht angezeigt werden. Klicken Sie auf die drei Punkte (**...**), um das Dropdown-Menü zu öffnen, und klicken Sie auf **Extraktionsschlüssel kopieren**. Sie benötigen diesen Schlüssel während der Extraktionsphase. Kopieren Sie diesen Extraktionsschlüssel.

   >[!NOTE]
   >
   >Der Extraktionsschlüssel ermöglicht es Ihrer AEM-Quellumgebung, eine sichere Verbindung mit dem Migrationssatz herzustellen. Behandeln Sie diesen Schlüssel mit der gleichen Sorgfalt wie ein Kennwort und geben Sie ihn nie über ein unsicheres Medium wie E-Mail weiter.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam4.png)

### Füllen des Migrationssatzes {#populating-the-migration-set}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_populate_migrationset"
>title="Füllen Sie den Migrationssatz &quot; abstract=&quot;Nach dem Erstellen eines Migrationssatzes muss er mit dem Inhalt aus der Quellinstanz gefüllt werden, der in die AEM as a Cloud Service-Umgebung verschoben werden muss. Dazu muss das Content Transfer Tool auf der Quellinstanz installiert sein."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/extracting-content.html?lang=de" text="Extrahieren von Inhalten"

Um den von Ihnen in Cloud Acceleration Manager erstellten Migrationssatz zu füllen, müssen Sie die neueste Content Transfer Tool-Version auf Ihrer Adobe Experience Manager-Quellinstanz (AEM) installieren. In diesem Abschnitt erfahren Sie, wie Sie den Migrationssatz füllen.

1. Nachdem Sie die neueste Version des Content Transfer Tool auf Ihrer Adobe Experience Manager-Quellinstanz installiert haben, navigieren Sie zu **Vorgänge - Inhaltsmigration**

1. Klicken Sie auf **Migrationssatz erstellen**.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam5.png)

1. Fügen Sie den zuvor aus CAM kopierten Extraktionsschlüssel in das Eingabefeld für den Extraktionsschlüssel im Formular **Migrationssatz erstellen** ein. Danach werden die Felder für den Migrationssatznamen und den Cloud Acceleration Manager-Projektnamen (CAM) automatisch ausgefüllt. Diese sollten mit dem Migrationssatznamen in CAM und dem von Ihnen erstellten CAM-Projektnamen übereinstimmen. Sie können jetzt Inhaltspfade hinzufügen. Nachdem Sie Inhaltspfade hinzugefügt haben, können Sie den Migrationssatz speichern. Sie können die Extraktion mit eingeschlossenen oder ausgeschlossenen Versionen ausführen.

   >[!NOTE]
   >
   >Vergewissern Sie sich, dass der Extraktionsschlüssel gültig ist und nicht kurz vor seinem Ablaufdatum ist. Diese Informationen finden Sie im Dialogfeld **Migrationssatz erstellen**, nachdem Sie den Extraktionsschlüssel eingefügt haben. Wenn Sie einen Verbindungsfehler erhalten, finden Sie unter [Konnektivität der Quellumgebung](#source-environment-connectivity) weitere Informationen.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam6.png)

1. Wählen Sie dann die folgenden Parameter aus, um den Migrationssatz zu erstellen:

   1. **Version einschließen**: Aktivieren Sie die Option. Wenn Versionen enthalten sind, wird der Pfad `/var/audit` automatisch einbezogen, um Prüfereignisse zu migrieren.

      ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam7.png)

      >[!NOTE]
      >Wenn Sie beabsichtigen, Versionen als Teil eines Migrationssatzes einzubeziehen und Auffüllungen mit `wipe=false` durchzuführen, müssen Sie aufgrund einer aktuellen Einschränkung im Content Transfer Tool die Versionsbereinigung deaktivieren. Wenn Sie es vorziehen, die Versionsbereinigung aktiviert zu lassen und in einen Migrationssatz aufzufüllen, dann müssen Sie die Aufnahme als `wipe=true` durchführen.


   1. **Einzuschließende Pfade**: Verwenden Sie den Pfad-Browser, um zu migrierende Pfade auszuwählen. Die Pfadauswahl akzeptiert Eingaben durch Eingabe von Text oder Auswahl.

      >[!IMPORTANT]
      >Die folgenden Pfade sind beim Erstellen eines Migrationssatzes eingeschränkt:
      >* `/apps`
      >* `/libs`
      >* `/home`
      >* `/etc` (einige `/etc`-Pfade können in CTT ausgewählt werden)


1. Klicken Sie auf **Speichern**, nachdem Sie alle Felder im Bildschirm **Migrationssatz erstellen** ausgefüllt haben.

<!-- 1. You will view your migration set in the **Content Transfer** wizard, as shown in the figure below.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ctt07.png)

   All the existing migration sets are displayed on the **Content Transfer** wizard with their current status and status information. You may see some of these icons described below.

   * A *red cloud* indicates that you cannot complete the extraction process.
   * A *green cloud* indicates that you can complete the extraction process.
   * A *yellow icon* indicates that you did not create the existing migration set and the specific one is created by some other user in the same instance.

1. Select a migration set and click on **Properties** to view or edit the migration set properties. While editing properties, it is not possible to change the **Migration Set name** or the **Service URL**. 

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ctt06.png) -->

### Bestimmen der Größe des Migrationssatzes {#migration-set-size}

Nach dem Erstellen eines Migrationssatzes wird dringend empfohlen, eine Größenüberprüfung des Migrationssatzes durchzuführen, bevor ein Extraktionsprozess gestartet wird.
Durch eine Größenüberprüfung des Migrationssatzes können Sie:
* feststellen, ob im `crx-quickstart`-Unterverzeichnis genügend Festplattenspeicher vorhanden ist, um die Extraktion erfolgreich abzuschließen.
* bestimmen, ob die Größe des Migrationssatzes unter die unterstützten Produktbeschränkungen fällt, und fehlgeschlagene Inhaltsaufnahmen vermeiden.

Gehen Sie wie folgt vor, um eine Größenüberprüfung durchzuführen:

1. Wählen Sie einen Migrationssatz aus und klicken Sie auf **Größe überprüfen**.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam8.png)

1. Dadurch wird das Dialogfeld **Größe überprüfen** angezeigt.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam9.png)

1. Klicken Sie auf **Größe überprüfen**, um den Prozess zu starten. Sie kehren dann zur Listenansicht des Migrationssatzes zurück und sollten eine Meldung mit dem Hinweis erhalten, dass der Prozess **Größe überprüfen** läuft.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam10.png)

1. Sobald der Prozess **Größe überprüfen** abgeschlossen ist, ändert sich der Status in **BEENDET**. Wählen Sie denselben Migrationssatz aus und klicken Sie auf **Größe überprüfen**, um die Ergebnisse anzuzeigen. Nachfolgend finden Sie ein Beispiel für Ergebnisse des Prozesses **Größe überprüfen** ohne Warnungen.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam11.png)

1. Wenn die Ergebnisse des Prozesses **Größe überprüfen** darauf hindeuten, dass entweder nicht genügend Speicherplatz vorhanden ist und/oder der Migrationssatz die Produktbeschränkungen überschreitet, wird er Status **WARNUNG** angezeigt.

<!--   ![image](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image6.png)
   
   Below is an example of **Check Size** results with warnings.
 
   ![image](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image7.png) -->


## Wie geht es weiter {#whats-next}

Nachdem Sie gelernt haben, wie Sie einen Migrationssatz erstellen, können Sie im Content Transfer Tool jetzt mehr über Extraktions- und Aufnahmeprozesse erfahren. Bevor Sie diese Prozesse erlernen, müssen Sie sich mit dem [Umgang mit großen Inhalts-Repositorys](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=de) befassen, um die Extraktions- und Aufnahmephasen der Inhaltsübertragungsaktivität zum Verschieben von Inhalten zu AEM as a Cloud Service erheblich zu beschleunigen.
