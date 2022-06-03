---
title: Erste Schritte mit dem Content Transfer Tool
description: Erste Schritte mit dem Content Transfer Tool
exl-id: c0cecf65-f419-484b-9d55-3cbd561e8dcd
source-git-commit: e7e3ec89d5e7b43b8c6dfb10f5dc966768ab0af1
workflow-type: tm+mt
source-wordcount: '1242'
ht-degree: 43%

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

* Die AEM as a Cloud Service-Zielumgebung: `author-p<program_id>-e<env_id>.adobeaemcloud.com`
* Der Azure Blob Datenspeicherungs-Service: `*.blob.core.windows.net`
* Der IO-Endpunkt der Benutzerzuordnung: `usermanagement.adobe.io`

Um die Konnektivität mit der AEM as a Cloud Service-Zielumgebung zu testen, geben Sie den folgenden cURL-Befehl in der Shell der Quellinstanz ein (ersetzen Sie `program_id`, `environment_id`, und `migration_token`):

`curl -i https://author-p<program_id>-e<environment_id>.adobeaemcloud.com/api/migration/migrationSet -H "Authorization: Bearer <migration_token>"`

>[!NOTE]
>Wenn eine `HTTP/2 200` empfangen wurde, war eine Verbindung zu AEM as a Cloud Service erfolgreich.

## Ausführen des Content Transfer Tools {#running-tool}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_demo"
>title="Ausführen des Content Transfer Tools"
>abstract="In diesem Abschnitt erfahren Sie, wie Sie mit dem Content Transfer Tool Inhalte zu AEM as a Cloud Service (Autor/Veröffentlichung) migrieren."
>additional-url="https://video.tv.adobe.com/v/35460/?quality=12&amp;learn=on" text=" Siehe Demo"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/content-transfer-tool.html?lang=de#migration" text="Tutorial – Verwenden des Content Transfer Tools"

>[!VIDEO](https://video.tv.adobe.com/v/35460/?quality=12&learn=on)
<!-- Need to remove the video -->

Der folgende Abschnitt gilt für die neue Version des Content Transfer Tool. In diesem Abschnitt erfahren Sie, wie Sie mit dem Content Transfer Tool Inhalte auf AEM as a Cloud Service migrieren:

### Phase der Extraktionseinrichtung {#extraction-setup-phase}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_extraction_setup"
>title="Phase der Extraktionseinrichtung"
>abstract="Erfahren Sie, wie Sie einen Migrationssatz erstellen und den Extraktionsschlüssel kopieren."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/content-transfer-tool.html?lang=en#migration" text="Tutorial – Verwenden des Content Transfer Tools"

<!-- Contextualhelp id "aemcloud_ctt_extraction_setup" needs to be added here -->

1. Melden Sie sich bei Cloud Acceleration Manager (CAM) an und klicken Sie auf das zuvor erstellte CAM-Projekt, um Ihre Bereitschaft zu AEM as a Cloud Service zu beurteilen. Wenn Sie kein CAM-Projekt erstellt haben, lesen Sie den Abschnitt Erstellen und Verwalten eines Projekts in CAM.

1. Klicken Sie auf **Inhaltstransfer** Karte. Dadurch gelangen Sie zur Ansicht &quot;Migrationssatzliste&quot;.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam1.png)

1. Erstellen Sie einen Migrationssatz, indem Sie auf **Migrationssatz erstellen**.

   >[!NOTE]
   >
   >In Cloud Acceleration Manager können maximal fünf Migrationssätze pro Projekt erstellt werden.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam2.png)

   ![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam3.png)

1. Ihre Migrationsliste sollte jetzt in der Listenansicht angezeigt werden. Klicken Sie auf das Drei-Punkte-Symbol (**...**), um das Dropdown-Menü zu öffnen, und klicken Sie auf **Extraktionsschlüssel kopieren**. Sie benötigen diesen Schlüssel während der Extraktionsphase. Kopieren Sie diesen Extraktionsschlüssel.

   >[!NOTE]
   >
   >Der Extraktionsschlüssel ermöglicht es Ihrer AEM, eine sichere Verbindung zum Migrationssatz herzustellen. Bitte behandeln Sie diesen Schlüssel mit der gleichen Sorgfalt wie ein Passwort und geben Sie ihn nie über ein unsicheres Medium wie E-Mail weiter.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam4.png)

### Füllen des Migrationssatzes {#populating-the-migration-set}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_populate_migrationset"
>title="Füllen Sie den Migrationssatz&quot; abstract=&quot;Nach dem Erstellen eines Migrationssatzes muss er mit dem Inhalt aus der Quellinstanz gefüllt werden, der in die AEM as a Cloud Service Umgebung verschoben werden muss. Dazu muss das Content Transfer Tool auf der Quellinstanz installiert sein."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/extracting-content.html" text="Extrahieren von Inhalten"

Um den von Ihnen im Cloud Acceleration Manager erstellten Migrationssatz zu füllen, müssen Sie die neueste Version des Content Transfer Tool auf Ihrer Adobe Experience Manager (AEM)-Quellinstanz installieren. In diesem Abschnitt erfahren Sie, wie Sie den Migrationssatz füllen.

1. Nachdem Sie die neueste Version (v2.0.10) des Content Transfer Tool auf Ihrer Adobe Experience Manager-Quellinstanz installiert haben, navigieren Sie zu **Vorgänge - Inhaltsmigration**

1. Klicken Sie auf **Migrationssatz erstellen**

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam5.png)

1. Fügen Sie den zuvor von CAM kopierten Extraktionsschlüssel in das Eingabefeld Extraktionsschlüssel von ein. **Migrationssatz erstellen** Formular. Danach werden die Felder Migrationssatzname und Cloud Acceleration Manager (CAM)-Projektname automatisch ausgefüllt. Diese sollten mit dem Migrationssatznamen in CAM und dem von Ihnen erstellten CAM-Projektnamen übereinstimmen. Sie können jetzt Inhaltspfade hinzufügen. Nachdem Sie Inhaltspfade hinzugefügt haben, können Sie den Migrationssatz speichern. Sie können die Extraktion mit eingeschlossenen oder ausgeschlossenen Versionen ausführen.

   >[!NOTE]
   >
   >Vergewissern Sie sich, dass der Extraktionsschlüssel gültig ist und nicht nahe an seinem Ablauf liegt. Diese Informationen finden Sie im Abschnitt **Migrationssatz erstellen** angezeigt, nachdem Sie den Extraktionsschlüssel eingefügt haben. Wenn Sie einen Verbindungsfehler erhalten, lesen Sie [Verbindung der Quellumgebung](#source-environment-connectivity) für weitere Informationen.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam6.png)

1. Wählen Sie anschließend die folgenden Parameter aus, um einen Migrationssatz zu erstellen:

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
* Stellen Sie fest, ob im `crx-quickstart` -Unterverzeichnis, um die Extraktion erfolgreich abzuschließen.
* Bestimmen Sie, ob die Größe des Migrationssatzes unter die unterstützten Produktbeschränkungen fällt, und vermeiden Sie fehlgeschlagene Inhaltsaufnahmen.

Gehen Sie wie folgt vor, um eine Größenüberprüfung durchzuführen:

1. Wählen Sie einen Migrationssatz aus und klicken Sie auf **Größe überprüfen**.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam8.png)

1. Dadurch wird die **Größe überprüfen** angezeigt.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam9.png)

1. Klicken Sie auf **Größe überprüfen** , um den Prozess zu starten. Sie kehren dann zur Listenansicht des Migrationssatzes zurück und sollten eine Meldung mit dem Hinweis erhalten, dass **Größe überprüfen** läuft.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam10.png)

1. Einmal **Größe überprüfen** -Prozess abgeschlossen ist, ändert sich der Status in **FERTIG**. Wählen Sie denselben Migrationssatz aus und klicken Sie auf **Größe überprüfen** , um Ergebnisse anzuzeigen. Nachfolgend finden Sie ein Beispiel für **Größe überprüfen** Ergebnisse ohne Warnungen.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam11.png)

1. Wenn die Variable **Größe überprüfen** die Ergebnisse zeigen, dass entweder nicht genügend Speicherplatz vorhanden ist und/oder der Migrationssatz die Produktbeschränkungen überschreitet, **WARNUNG** wird angezeigt.

<!--   ![image](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image6.png)
   
   Below is an example of **Check Size** results with warnings.
 
   ![image](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image7.png) -->


## Wie geht es weiter {#whats-next}

Nachdem Sie gelernt haben, wie Sie einen Migrationssatz erstellen, können Sie im Content Transfer Tool jetzt mehr über Extraktions- und Aufnahmeprozesse erfahren. Bevor Sie diese Prozesse erlernen, müssen Sie sich mit dem [Umgang mit großen Inhalts-Repositorys](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=de) befassen, um die Extraktions- und Aufnahmephasen der Inhaltsübertragungsaktivität zum Verschieben von Inhalten zu AEM as a Cloud Service erheblich zu beschleunigen.
