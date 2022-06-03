---
title: Aufnahme von Inhalten in Target
description: Aufnahme von Inhalten in Target
exl-id: d8c81152-f05c-46a9-8dd6-842e5232b45e
source-git-commit: 05765bdaa681502b60fc5a7c943e2265c09764ec
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 40%

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
>Sie können den optionalen Pre-Copy-Schritt ausführen, um die Aufnahmephase erheblich zu beschleunigen. Der Schritt zum Vorauskopieren ist am effektivsten für die erste vollständige Extraktion und Aufnahme. Weitere Informationen finden Sie unter [Aufnehmen mit AzCopy](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md#ingesting-azcopy).

1. Rufen Sie Cloud Acceleration Manager auf. Klicken Sie auf Ihre Projektkarte und dann auf die Karte Inhaltstransfer . Navigieren Sie zu **Aufnahmevorgänge** und klicken Sie auf **Neue Erfassung**

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-01.png)

1. Geben Sie die erforderlichen Informationen ein, um eine neue Aufnahme zu erstellen.

   * Wählen Sie den soeben als Quelle extrahierten Migrationssatz aus
   * Wählen Sie die Zielumgebung aus. Hier wird der Inhalt des Migrationssatzes erfasst. Wählen Sie die Ebene aus. (Autor/Veröffentlichung).

   >[!NOTE]
   >
   >Wenn die Quelle &quot;Autor&quot;war, wird empfohlen, sie in die Autorenstufe auf dem Ziel aufzunehmen. Wenn die Quelle &quot;Veröffentlichen&quot;war, sollte das Ziel ebenfalls &quot;Veröffentlichen&quot;sein.

   >[!NOTE]
   >
   >Sie können den optionalen Pre-Copy-Schritt ausführen, um die Aufnahmephase erheblich zu beschleunigen. Weitere Informationen finden Sie unter [Aufnehmen mit AzCopy](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md#ingesting-azcopy).
   > 
   >Wenn die Aufnahme mit einer Vorkopie verwendet wird (für den S3- oder Azure Data Store), wird empfohlen, die Autorenaufnahme zuerst allein auszuführen. Dadurch wird die Aufnahme der Veröffentlichung beschleunigt, wenn sie später ausgeführt wird.

   >[!IMPORTANT]
   >
   >Sie können eine Aufnahme nur dann in die Zielumgebung starten, wenn Sie zum lokalen **AEM Administratoren** -Gruppe in der Cloud Service-Instanz, in die Sie Inhalte übertragen. Wenn Sie nicht zur Gruppe der AEM-Administratoren gehören, wird beim Versuch, eine Aufnahme zu starten, ein Fehler wie unten dargestellt angezeigt.
   >![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam21.png)

   >[!IMPORTANT]
   >
   >Wenn die Einstellung **Wischen** vor der Erfassung aktiviert ist, löscht er das gesamte vorhandene Repository und erstellt ein neues Repository, in das Inhalte aufgenommen werden können. Das bedeutet, dass alle Einstellungen einschließlich der Berechtigungen für die Cloud Service-Zielinstanz zurückgesetzt werden. Dies gilt auch für Administratoren, die der Gruppe **Administratoren** hinzugefügt werden. Sie müssen der Administratorgruppe erneut hinzugefügt werden, um eine Aufnahme starten zu können.

1. Klicken Sie auf **Aufnehmen**

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam22.png)

1. Sie können dann die Aufnahmephase in der Listenansicht &quot;Aufnahmevorgänge&quot;überwachen

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam23.png)

1. Klicken Sie nach Abschluss der Aufnahme auf die Schaltfläche (i) oben rechts im Bildschirm, um weitere Informationen zum Erfassungsauftrag zu erhalten.

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
>abstract="Verwenden Sie die Auffüllfunktion, um geänderte Inhalte seit der vorherigen Aktivität zur Inhaltstransfer zu verschieben. Überprüfen Sie nach Abschluss der Aufnahme die Protokolle auf Fehler/Warnungen. Etwaige Fehler sollten sofort behoben werden, indem Sie entweder die gemeldeten Probleme behandeln oder sich an die Kundenunterstützung von Adobe wenden."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/viewing-logs.html?lang=en" text="Anzeigen von Protokollen"

Das Content Transfer Tool verfügt über eine Funktion, die die differenzielle *Auffüllung* von Inhalten unterstützt, wobei es möglich ist, nur Änderungen zu übertragen, die seit dem vorherigen Inhaltstransfer vorgenommen wurden.

>[!NOTE]
>Nach dem ersten Transfer von Inhalten wird empfohlen, häufige differenzielle Auffüllungen des Inhalts durchzuführen, um den Zeitraum für das Einfrieren des Inhalts für den endgültigen differenziellen Inhaltstransfer zu verkürzen, bevor er in Cloud Service live geschaltet wird. Wenn Sie den Vorab-Kopierschritt für die erste vollständige Erfassung verwendet haben, können Sie die Vorkopie für nachfolgende Auffüllaufnahme überspringen (wenn die Größe des AuffüllMigrationssatzes kleiner als 200 GB ist), da dies dem gesamten Prozess Zeit hinzufügen kann.

Nachdem der Aufnahmevorgang abgeschlossen ist, müssen Sie zum Erfassen des Delta-Inhalts eine [Auffüllextraktion](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process) und verwenden Sie dann die Auffüllaufnahme-Methode.

Erstellen Sie dazu einen neuen Aufnahmeauftrag und stellen Sie sicher, dass **Wischen** ist während der Aufnahmephase deaktiviert, wie unten dargestellt:

![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam24.png)



## Wie geht es weiter {#whats-next}

Wenn Sie sich mit der Aufnahme von Inhalten in das Zielsystem im Content Transfer Tool vertraut gemacht haben, können Sie die Protokolle nach Abschluss der einzelnen Schritte (Extraktion und Aufnahme) einsehen und nach Fehlern suchen. Weitere Informationen finden Sie unter [Anzeigen von Protokollen für einen Migrationssatz](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/viewing-logs.html?lang=de).
