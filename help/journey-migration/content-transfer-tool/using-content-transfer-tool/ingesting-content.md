---
title: Aufnahme von Inhalten in Target
description: Aufnahme von Inhalten in Target
exl-id: d8c81152-f05c-46a9-8dd6-842e5232b45e
source-git-commit: 0a5b74427bedfa7b1e802a91632b0765adfb8248
workflow-type: tm+mt
source-wordcount: '908'
ht-degree: 74%

---

# Aufnahme von Inhalten in Target {#ingesting-content}

## Aufnahme-Prozess im Content Transfer Tool {#ingestion-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion"
>title="Inhaltsaufnahme"
>abstract="Aufnahme bezieht sich auf die Aufnahme von Inhalten aus dem Migrationssatz in die Cloud Service-Zielinstanz. Das Content Transfer Tool verfügt über eine Funktion, die die differenzielle Auffüllung von Inhalten unterstützt, wobei es möglich ist, nur Änderungen zu übertragen, die seit dem vorherigen Inhaltstransfer vorgenommen wurden."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=de#top-up-ingestion-process" text="Auffüllaufnahme"

Gehen Sie wie folgt vor, um den Migrationssatz aus dem Content Transfer Tool aufzunehmen:
>[!NOTE]
>Sie können den optionalen Vorabkopie-Schritt ausführen, um die Aufnahmephase erheblich zu beschleunigen. Der Schritt der Vorabkopie ist am effektivsten für die erste vollständige Extraktion und Aufnahme. Weitere Informationen finden Sie unter [Aufnehmen mit AzCopy](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md#ingesting-azcopy).

1. Gehen Sie zum Cloud Acceleration Manager. Klicken Sie auf Ihre Projektkarte und dann auf die Karte „Inhaltstransfer“. Gehen Sie zu **Aufnahmevorgänge** und klicken Sie auf **Neue Aufnahme**

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-01.png)

1. Geben Sie die erforderlichen Informationen ein, um eine neue Aufnahme zu erstellen.

   * Wählen Sie den soeben als Quelle extrahierten Migrationssatz aus.
   * Wählen Sie die Zielumgebung aus. Hier werden die Inhalte des Migrationssatzes aufgenommen. Wählen Sie die Ebene aus. (Autoren- / und Veröffentlichungsinstanz).

   >[!NOTE]
   >
   >Wenn die Quelle die Autoreninstanz war, wird empfohlen, sie in die Autorenebene auf dem Ziel aufzunehmen. Wenn die Quelle die Veröffentlichungsinstanz war, sollte das Ziel ebenfalls „Veröffentlichung“ sein.

   >[!NOTE]
   >
   >Sie können den optionalen Vorabkopie-Schritt ausführen, um die Aufnahmephase erheblich zu beschleunigen. Weitere Informationen finden Sie unter [Aufnehmen mit AzCopy](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md#ingesting-azcopy).
   > 
   >Wenn die Aufnahme mit einer Vorkopie verwendet wird (für den S3- oder Azure Data Store), wird empfohlen, die Autorenaufnahme zuerst allein auszuführen. Dadurch wird die Aufnahme der Veröffentlichung beschleunigt, wenn sie später ausgeführt wird.

   >[!IMPORTANT]
   >
   >Sie können eine Aufnahme nur dann in die Zielumgebung starten, wenn Sie zum lokalen **AEM Administratoren** auf dem Ziel-Cloud Service-Autorendienst. Wenn Sie eine Aufnahme nicht starten können, lesen Sie den Abschnitt [Aufnahme kann nicht gestartet werden](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#unable-to-start-ingestion) für weitere Details.

   >[!IMPORTANT]
   >
   >Wenn die Einstellung **Löschen** vor der Aufnahme aktiviert ist, wird das gesamte vorhandene Repository gelöscht und ein neues Repository erstellt, in das die Inhalte aufgenommen werden. Das bedeutet, dass alle Einstellungen einschließlich der Berechtigungen für die Cloud Service-Zielinstanz zurückgesetzt werden. Dies gilt auch für Administratoren, die der Gruppe **Administratoren** hinzugefügt werden. Sie müssen der Administratorgruppe erneut hinzugefügt werden, um eine Aufnahme starten zu können.

1. Klicken Sie auf **Aufnehmen**.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam22.png)

1. Sie können dann die Aufnahmephase in der Listenansicht „Aufnahmevorgänge“ überwachen.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam23.png)

1. Sobald die Aufnahme abgeschlossen ist, klicken Sie auf die Schaltfläche (i) in der oberen rechten Ecke des Bildschirms, um weitere Informationen über den Aufnahmeauftrag zu erhalten.

<!-- Alexandru: hiding temporarily, until it's reviewed 

1. The **Migration Set ingestion** dialog box displays. Content can be ingested to either Author instance or Publish instance at a time. Select the instance to ingest content to. Click on **Ingest** to start the ingestion phase. 

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-02.png)

   >[!IMPORTANT]
   >If ingesting with pre-copy is used (for S3 or Azure Data Store), it is recommended to run Author ingestion first alone. This will speed up the Publish ingestion when it is run later. 

   >[!IMPORTANT]
   >When the **Wipe existing content on Cloud instance before ingestion** option is enabled, it deletes the entire existing repository and creates a new repository to ingest content into. This means that it resets all settings including permissions on the target Cloud Service instance. This is also true for an admin user added to the **administrators** group.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-03.png)

   Additionally, click on **Customer Care** to log a ticket, as shown in the figure below. 

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-04.png)
   
   Also, refer to [Important Considerations for Using Content Transfer Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=en#important-considerations) to learn more.

1. Once the ingestion is complete, the status under **Author ingestion** updates to **FINISHED**.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-05.png) -->

## Auffüllaufnahme {#top-up-ingestion-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion_topup" title="Top Up Ingestion"
>abstract="Verwenden Sie die Funktion „Auffüllen“, um geänderte Inhalte seit der letzten Inhaltsübertragungsaktivität zu verschieben. Überprüfen Sie nach Abschluss der Aufnahme die Protokolle auf Fehler/Warnungen. Alle Fehler sollten sofort behoben werden, indem Sie sich entweder mit den gemeldeten Problemen befassen oder die Adobe-Kundenunterstützung kontaktieren."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/viewing-logs.html?lang=de" text="Anzeigen von Protokollen"

Das Content Transfer Tool verfügt über eine Funktion, die die differenzielle *Auffüllung* von Inhalten unterstützt, wobei es möglich ist, nur Änderungen zu übertragen, die seit dem vorherigen Inhaltstransfer vorgenommen wurden.

>[!NOTE]
>Nach dem ersten Transfer von Inhalten wird empfohlen, häufige differenzielle Auffüllungen des Inhalts durchzuführen, um den Zeitraum für das Einfrieren des Inhalts für den endgültigen differenziellen Inhaltstransfer zu verkürzen, bevor er in Cloud Service live geschaltet wird. Wenn Sie den Schritt der Vorabkopie für die erste vollständige Aufnahme verwendet haben, können Sie die Vorabkopie für nachfolgende Auffüllaufnahmen überspringen (wenn die Größe des Auffüllmigrations-Sets weniger als 200 GB beträgt), da dies den gesamten Prozess verlängern kann.

Sobald der Aufnahmeprozess abgeschlossen ist, müssen Sie eine [Auffüllextraktion](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process) durchführen, um den Delta-Inhalt aufzunehmen, und dann die Methode der Auffüllaufnahme verwenden.

Sie können dies tun, indem Sie einen neuen Aufnahmeauftrag erstellen und sicherstellen, dass **Löschen** während der Aufnahmephase deaktiviert ist, wie unten gezeigt:

![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam24.png)

## Fehlerbehebung {#troubleshooting}

### CAM kann das Migrationstoken nicht abrufen {#cam-unable-to-retrieve-the-migration-token}

Der automatische Abruf des Migrationstokens kann aus verschiedenen Gründen fehlschlagen, einschließlich Ihnen [Einrichten einer IP-Zulassungsliste über Cloud Manager](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) in der Ziel-Cloud Service-Umgebung.  In solchen Fällen sehen Sie das folgende Dialogfeld, wenn Sie versuchen, eine Aufnahme zu starten:

![image](/help/journey-migration/content-transfer-tool/assets-ctt/troubleshooting-token.png)

Sie müssen das Migrationstoken manuell abrufen, indem Sie im Dialogfeld auf den Link &quot;Token abrufen&quot;klicken. Dadurch wird eine weitere Registerkarte geöffnet, auf der das Token angezeigt wird. Sie können das Token dann kopieren und in die **Eingabe des Migrationstokens** -Feld. Jetzt sollten Sie in der Lage sein, mit der Aufnahme zu beginnen.

>[!NOTE]
>
>Das Token steht Benutzern zur Verfügung, die zur lokalen **AEM Administratoren** auf dem Ziel-Cloud Service-Autorendienst.

### Aufnahme kann nicht gestartet werden {#unable-to-start-ingestion}

Sie können eine Aufnahme nur dann in die Zielumgebung starten, wenn Sie zum lokalen **AEM Administratoren** auf dem Ziel-Cloud Service-Autorendienst. Wenn Sie nicht zur Gruppe der AEM-Administratoren gehören, wird beim Versuch, eine Aufnahme zu starten, ein Fehler wie unten dargestellt angezeigt. Sie können Ihren Administrator bitten, Sie entweder zum lokalen **AEM Administratoren** oder fragen Sie nach dem Token selbst, das Sie dann in die **Eingabe des Migrationstokens** -Feld.

![image](/help/journey-migration/content-transfer-tool/assets-ctt/error_nonadmin_ingestion.png)

## Wie geht es weiter {#whats-next}

Wenn Sie sich mit der Aufnahme von Inhalten in das Zielsystem im Content Transfer Tool vertraut gemacht haben, können Sie die Protokolle nach Abschluss der einzelnen Schritte (Extraktion und Aufnahme) einsehen und nach Fehlern suchen. Weitere Informationen finden Sie unter [Anzeigen von Protokollen für einen Migrationssatz](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/viewing-logs.html?lang=de).
