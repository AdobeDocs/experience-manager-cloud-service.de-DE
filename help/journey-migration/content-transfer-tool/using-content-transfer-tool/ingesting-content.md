---
title: Aufnahme von Inhalten in Target
description: Aufnahme von Inhalten in Target
exl-id: d8c81152-f05c-46a9-8dd6-842e5232b45e
source-git-commit: 7854a0217c5d2e7d260a6fbe893aef1e6d4a4c72
workflow-type: tm+mt
source-wordcount: '1687'
ht-degree: 89%

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
>Haben Sie ein Support-Ticket für diesen Aufnahmevorgang erstellt? Weitere Informationen zu diesen und anderen Überlegungen zur erfolgreichen Aufnahme finden Sie unter [Wichtige Überlegungen vor Verwendung des Content Transfer Tools](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=de#important-considerations).

1. Gehen Sie zum Cloud Acceleration Manager. Klicken Sie auf Ihre Projektkarte und dann auf die Karte „Inhaltstransfer“. Gehen Sie zu **Aufnahmevorgänge** und klicken Sie auf **Neue Aufnahme**

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-01.png)

1. Überprüfen Sie die Checkliste für die Aufnahme und stellen Sie sicher, dass alle Schritte ausgeführt wurden. Dies sind die erforderlichen Schritte, um eine erfolgreiche Aufnahme sicherzustellen. Sie können mit dem **nächsten** Schritt nur fortfahren, wenn die Checkliste abgeschlossen wurde.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/Ingestion-checklist.png)

1. Geben Sie die erforderlichen Informationen ein, um eine neue Aufnahme zu erstellen.

   * Wählen Sie als Quelle den Migrationssatz aus, der die extrahierten Daten enthält.
      * Migrationssätze laufen nach einem längeren Zeitraum der Inaktivität ab. Daher wird erwartet, dass die Aufnahme relativ bald nach der Extraktion erfolgt. Überprüfen [Ablauf des Migrationssatzes](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/overview-content-transfer-tool.md#migration-set-expiry) für Details.
   * Wählen Sie die Zielumgebung aus. Hier werden die Inhalte des Migrationssatzes aufgenommen. Wählen Sie die Ebene aus. (Autoren- / und Veröffentlichungsinstanz). Rapid Development Environments werden nicht unterstützt.

   >[!NOTE]
   >
   >Wenn die Quelle die Autoreninstanz war, wird empfohlen, sie in die Autorenebene auf dem Ziel aufzunehmen. Wenn die Quelle die Veröffentlichungsinstanz war, sollte das Ziel ebenfalls „Veröffentlichung“ sein.

   >[!NOTE]
   >
   >Wenn die Zielebene `Author` ist, wird die Autoreninstanz während der Aufnahmedauer heruntergefahren und steht Benutzern (wie beispielsweise Autoren oder anderen, die z. B. Wartungsarbeiten durchführen) nicht zur Verfügung. Dadurch soll das System geschützt werden, und es sollen Änderungen verhindert werden, die verloren gehen oder einen Aufnahmekonflikt verursachen könnten. Bitte stellen Sie sicher, dass Ihr Team sich dieser Tatsache bewusst ist. Beachten Sie außerdem, dass sich die Umgebung während der Autorenaufnahme im Ruhezustand befindet.

   >[!NOTE]
   >
   >Sie können den optionalen Vorabkopie-Schritt ausführen, um die Aufnahmephase erheblich zu beschleunigen. Weitere Informationen finden Sie unter [Aufnehmen mit AzCopy](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md#ingesting-azcopy).
   > 
   >Wenn die Aufnahme mit einer Vorkopie verwendet wird (für den S3- oder Azure Data Store), wird empfohlen, die Autorenaufnahme zuerst allein auszuführen. Dadurch wird die Aufnahme der Veröffentlichung beschleunigt, wenn sie später ausgeführt wird.

   >[!NOTE]
   >
   >Einstiege unterstützen kein RDE-Ziel (Rapid Development Environment). Sie werden nicht als mögliche Zielauswahl angezeigt, selbst wenn der Benutzer Zugriff darauf hat.

   >[!IMPORTANT]
   >
   >Sie können eine Aufnahme nur dann in die Zielumgebung starten, wenn Sie zum lokalen **AEM Administratoren** auf dem Ziel-Cloud Service-Autorendienst. Wenn Sie eine Aufnahme nicht starten können, lesen Sie den Abschnitt [Aufnahme kann nicht gestartet werden](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#unable-to-start-ingestion) für mehr Details.

   >[!IMPORTANT]
   >
   >Wenn die Einstellung **Löschen** vor der Aufnahme aktiviert ist, wird das gesamte vorhandene Repository gelöscht und ein neues Repository erstellt, in das die Inhalte aufgenommen werden. Das bedeutet, dass alle Einstellungen einschließlich der Berechtigungen für die Cloud Service-Zielinstanz zurückgesetzt werden. Dies gilt auch für Administratoren, die der Gruppe **Administratoren** hinzugefügt werden. Sie müssen der Administratorgruppe erneut hinzugefügt werden, um eine Aufnahme starten zu können.

1. Klicken Sie auf **Aufnehmen**.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam22.png)

1. Sie können dann die Aufnahmephase in der Listenansicht „Aufnahmevorgänge“ überwachen. Verwenden Sie das Aktionsmenü der Aufnahme, um das Protokoll im Verlauf der Aufnahme anzuzeigen.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam23.png)

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
   
   Also, refer to [Important Considerations for Using Content Transfer Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html#important-considerations) to learn more.

1. Once the ingestion is complete, the status under **Author ingestion** updates to **FINISHED**.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-05.png) -->

## Auffüllaufnahme {#top-up-ingestion-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion_topup"
>title="Auffüllaufnahme"
>abstract="Verwenden Sie die Funktion „Auffüllen“, um geänderte Inhalte seit der letzten Inhaltsübertragungsaktivität zu verschieben. Überprüfen Sie nach Abschluss der Aufnahme die Protokolle auf Fehler/Warnungen. Alle Fehler sollten sofort behoben werden, indem Sie sich entweder mit den gemeldeten Problemen befassen oder die Adobe-Kundenunterstützung kontaktieren."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/viewing-logs.html" text="Anzeigen von Protokollen"

Das Content Transfer Tool verfügt über eine Funktion, die die differenzielle *Auffüllung* von Inhalten unterstützt, wobei es möglich ist, nur Änderungen zu übertragen, die seit dem vorherigen Inhaltstransfer vorgenommen wurden.

>[!NOTE]
>Nach dem ersten Transfer von Inhalten wird empfohlen, häufige differenzielle Auffüllungen des Inhalts durchzuführen, um den Zeitraum für das Einfrieren des Inhalts für den endgültigen differenziellen Inhaltstransfer zu verkürzen, bevor er in Cloud Service live geschaltet wird. Wenn Sie den Schritt der Vorabkopie für die erste vollständige Aufnahme verwendet haben, können Sie die Vorabkopie für nachfolgende Auffüllaufnahmen überspringen (wenn die Größe des Auffüllmigrations-Sets weniger als 200 GB beträgt), da dies den gesamten Prozess verlängern kann.

Sobald der Aufnahmeprozess abgeschlossen ist, müssen Sie eine [Auffüllextraktion](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process) durchführen, um den Delta-Inhalt aufzunehmen, und dann die Methode der Auffüllaufnahme verwenden.

Sie können dies tun, indem Sie einen neuen Aufnahmeauftrag erstellen und sicherstellen, dass **Löschen** während der Aufnahmephase deaktiviert ist, wie unten gezeigt:

![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam24.png)

## Fehlerbehebung {#troubleshooting}

### CAM kann das Migrations-Token nicht abrufen {#cam-unable-to-retrieve-the-migration-token}

Der automatische Abruf des Migrations-Tokens kann aus verschiedenen Gründen fehlschlagen, wie z. B. wenn Sie in der Cloud Service-Zielumgebung [eine IP-Zulassungsliste über Cloud Manager einrichten](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md). In solchen Fällen sehen Sie den folgende Dialog, wenn Sie versuchen, eine Aufnahme zu starten:

![image](/help/journey-migration/content-transfer-tool/assets-ctt/troubleshooting-token.png)

Sie müssen das Migrations-Token manuell abrufen, indem Sie im Dialog auf den Link „Token abrufen“ klicken. Dadurch wird eine weitere Registerkarte geöffnet, auf der das Token angezeigt wird. Sie können dann das Token kopieren und in das Feld **Migrations-Token-Eingabefeld** einfügen. Jetzt sollten Sie in der Lage sein, die Aufnahme zu starten.

>[!NOTE]
>
>Das Token steht Benutzern zur Verfügung, die zur lokalen **AEM Administratoren**-Gruppe im dem anvisierten Cloud Service-Autorenservice gehören.

### Aufnahme kann nicht gestartet werden {#unable-to-start-ingestion}

Sie können eine Aufnahme nur dann in die Zielumgebung starten, wenn Sie zum lokalen **AEM Administratoren** auf dem Ziel-Cloud Service-Autorendienst. Wenn Sie nicht zur Gruppe der AEM-Administratoren gehören, wird beim Versuch, eine Aufnahme zu starten, ein Fehler wie unten dargestellt angezeigt. Sie können Ihren Administrator bitten, Sie entweder zu den lokalen **AEM Administratoren** hinzuzufügen oder ihn nach dem Token selbst fragen, das Sie dann in das Feld **Eingabefeld für das Migrations-Token** einfügen können.

![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/error_nonadmin_ingestion.png)

### Migrationsdienst kann nicht erreicht werden {#unable-to-reach-migration-service}

Nachdem eine Aufnahme angefordert wurde, kann dem Benutzenden eine Nachricht wie die folgende angezeigt werden: „Der Migrationsdienst in der Zielumgebung ist derzeit nicht erreichbar. Bitte versuchen Sie es später erneut oder kontaktieren Sie Adobe-Support.“

![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/error_cannot_reach_migser.png)

Dies weist darauf hin, dass der Cloud Acceleration Manager nicht in der Lage war, den Migrationsdienst der Zielumgebung zu erreichen, um die Aufnahme zu starten. Dies kann aus verschiedenen Gründen geschehen.

>[!NOTE]
> 
> Das Feld „Migrations-Token“ wird angezeigt, da in einigen Fällen das Abrufen dieses Tokens tatsächlich nicht zulässig ist. Durch die manuelle Bereitstellung kann die Benutzerin oder der Benutzer die Aufnahme schnell und ohne zusätzliche Hilfe starten. Wenn der Token bereitgestellt wird und die Nachricht weiterhin angezeigt wird, war das Abrufen des Tokens nicht das Problem.

* AEM as a Cloud Service verwaltet den Umgebungsstatus und muss den Migrationsdienst gelegentlich aus einer Reihe von normalen Gründen neu starten. Wenn der Dienst gerade neu gestartet wird, ist er nicht erreichbar, wird aber bald wieder verfügbar sein.
* Möglicherweise wird ein anderer Prozess in der Instanz ausgeführt. Wenn z. B. der Release Orchestrator ein Update durchführt, ist das System möglicherweise ausgelastet und der Migrationsdienst ist regelmäßig nicht verfügbar. Aus diesem Grund und wegen der Möglichkeit, die Stage- oder Produktionsinstanz zu beschädigen, wird dringend empfohlen, die Aktualisierungen während einer Aufnahme anzuhalten.
* Wenn eine [IP-Zulassungsliste über Cloud Manager angewendet wurde](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md), blockiert sie den Cloud Acceleration Manager beim Erreichen des Migrationsdienstes. Eine IP-Adresse kann nicht für die Aufnahme hinzugefügt werden, da diese Adresse sehr dynamisch ist. Derzeit besteht die einzige Lösung darin, die IP-Zulassungsliste während der Aufnahme zu deaktivieren.
* Es kann andere Gründe geben, die untersucht werden müssen. Wenn die Aufnahme weiterhin fehlschlägt, wenden Sie sich an die Kundenunterstützung von Adobe.

### Automatische Aktualisierungen über Release Orchestrator sind weiterhin aktiviert

Release Orchestrator hält Umgebungen durch die automatische Anwendung von Aktualisierungen automatisch auf dem aktuellen Stand. Wenn während eines Aufnahmevorgangs eine Aktualisierung ausgelöst wird, kann dies zu unvorhersehbaren Ergebnissen führen, einschließlich der Beschädigung der Umgebung. Dies ist einer der Gründe, warum vor dem Start eines Aufnahmevorgangs ein Support-Ticket erstellt werden sollte (siehe „Hinweis“ oben), sodass eine zeitweilige Deaktivierung von Release Orchestrator geplant werden kann.

Wenn Release Orchestrator beim Start einer Aufnahme noch ausgeführt wird, zeigt die Benutzeroberfläche diese Fehlermeldung an. Sie können trotzdem fortfahren und das Risiko eingehen, indem Sie das Feld markieren und die Taste erneut drücken.

![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/error_releaseorchestrator_ingestion.png)

### Fehler bei Auffüllaufnahme

Eine häufige Ursache für einen [Auffüllaufnahme](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process)-Fehler ist ein Konflikt bei Knoten-IDs. Um den Fehler zu identifizieren, laden Sie das Aufnahmeprotokoll über die Benutzeroberfläche von Cloud Acceleration Manager herunter und suchen Sie nach einem Eintrag wie dem Folgenden:

>java.lang.RuntimeException: org.apache.jackrabbit.oak.api.CommitFailedException: OakConstraint0030: Uniqueness constraint violated property [jcr:uuid] having value a1a1a1a1-b2b2-c3c3-d4d4-e5e5e5e5e5e5: /some/path/jcr:content, /some/other/path/jcr:content

Jeder Knoten in AEM muss über eine eindeutige UUID verfügen. Dieser Fehler weist darauf hin, dass ein aufgenommener Knoten dieselbe UUID hat wie ein Knoten, der bereits an einem anderen Pfad in der Zielinstanz vorhanden ist.
Dies kann vorkommen, wenn ein Knoten an der Quelle zwischen einer Extraktion und einer nachfolgenden [Auffüllextraktion](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process) verschoben wird.
Es kann auch vorkommen, wenn ein Knoten am Ziel zwischen einer Aufnahme und einer nachfolgenden Auffüllaufnahme verschoben wird.

Dieser Konflikt muss manuell behoben werden. Dabei muss eine Person, die mit dem Inhalt vertraut ist, entscheiden, welche der beiden Knoten gelöscht werden muss, wobei andere Inhalte, die darauf verweisen, zu berücksichtigen sind. Zur Lösung des Problems kann es erforderlich sein, dass die Auffüllextraktion ohne den fehlerhaften Knoten wiederholt wird.

## Wie geht es weiter {#whats-next}

Nachdem Sie die Aufnahme von Inhalten in die Target-Komponente abgeschlossen haben, können Sie die Protokolle jedes Schritts (Extraktion und Aufnahme) anzeigen und nach Fehlern suchen. Weitere Informationen finden Sie unter [Anzeigen von Protokollen für einen Migrationssatz](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/viewing-logs.html).
