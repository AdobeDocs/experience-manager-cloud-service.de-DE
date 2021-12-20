---
title: Erfassen von Inhalten in Target
description: Erfassen von Inhalten in Target
source-git-commit: bcbf4e4ba1330bef9f2c8c473419903e40ac0e58
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 70%

---


# Erfassen von Inhalten in Target {#ingesting-content}

## Aufnahmevorgang im Content Transfer Tool {#ingestion-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion"
>title="Inhaltsaufnahme"
>abstract="Aufnahme bezieht sich auf die Aufnahme von Inhalten aus dem Migrationssatz in die Cloud Service-Zielinstanz. Das Content Transfer Tool verfügt über eine Funktion, die die differenzielle Auffüllung von Inhalten unterstützt, wobei es möglich ist, nur Änderungen zu übertragen, die seit dem vorherigen Inhaltstransfer vorgenommen wurden."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=de#top-up-ingestion-process" text="Auffüllaufnahme"

Gehen Sie wie folgt vor, um den Migrationssatz aus dem Content Transfer Tool aufzunehmen:
>[!NOTE]
>Wenn Amazon S3 oder Azure Data Store als Datenspeichertyp verwendet wird, können Sie den optionalen Vorkopierschritt ausführen, um die Aufnahmephase erheblich zu beschleunigen. Weitere Informationen finden Sie unter [Aufnehmen mit AzCopy](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=de#ingesting-azcopy).

1. Wählen Sie einen Migrationssatz aus **Inhaltstransfer** Seite und klicken Sie auf **Aufnehmen** , um die Aufnahme zu starten.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-01.png)

1. Das Dialogfeld **Aufnahme des Migrationssatzes** wird angezeigt. Inhalte können gleichzeitig in der Autoren- oder Veröffentlichungsinstanz aufgenommen werden. Wählen Sie die Instanz aus, in der Inhalte aufgenommen werden sollen. Klicken Sie auf **Aufnehmen**, um die Aufnahmephase zu starten.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-02.png)

   >[!IMPORTANT]
   >Wenn die Aufnahme mit einer Vorkopie verwendet wird (für den S3- oder Azure Data Store), wird empfohlen, die Autorenaufnahme zuerst allein auszuführen. Dadurch wird die Aufnahme der Veröffentlichung beschleunigt, wenn sie später ausgeführt wird.

   >[!IMPORTANT]
   >Wenn die Option **Vorhandene Inhalte in der Cloud-Instanz vor der Erfassung löschen** aktiviert ist, wird das gesamte vorhandene Repository gelöscht und ein neues Repository erstellt, in dem Inhalte erfasst werden. Das bedeutet, dass alle Einstellungen einschließlich der Berechtigungen für die Cloud Service-Zielinstanz zurückgesetzt werden. Dies gilt auch für Administratoren, die der Gruppe **Administratoren** hinzugefügt werden.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-03.png)

   Klicken Sie außerdem auf **Kundenunterstützung** um ein Ticket zu protokollieren, wie in der folgenden Abbildung dargestellt.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-04.png)

   Weitere Informationen finden Sie unter [Wichtige Überlegungen zur Verwendung des Content Transfer Tools](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=en#important-considerations).

1. Sobald die Aufnahme abgeschlossen ist, wird der Status unter **Autorenaufnahme** Aktualisierungen in **FERTIG**.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-05.png)

## Auffüllaufnahme {#top-up-ingestion-process}

Das Content Transfer Tool verfügt über eine Funktion, die die differenzielle *Auffüllung* von Inhalten unterstützt, wobei es möglich ist, nur Änderungen zu übertragen, die seit dem vorherigen Inhaltstransfer vorgenommen wurden.

>[!NOTE]
>Nach dem ersten Transfer von Inhalten wird empfohlen, häufige differenzielle Auffüllungen des Inhalts durchzuführen, um den Zeitraum für das Einfrieren des Inhalts für den endgültigen differenziellen Inhaltstransfer zu verkürzen, bevor er in Cloud Service live geschaltet wird.

Sobald die Aufnahme abgeschlossen ist, können Sie Delta-Inhalte mithilfe der Auffüllaufnahme übertragen. Führen Sie dazu folgende Schritte durch:

1. Navigieren Sie zum **Inhaltstransfer** und wählen Sie den Migrationssatz aus, für den Sie die Auffüllaufnahme durchführen möchten. Klicken Sie auf **Aufnehmen**, um die Auffüllaufnahme zu starten.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/topup-ingest1.png)


1. Das Dialogfeld **Aufnahme des Migrationssatzes** wird angezeigt.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/topup-ingest2.png)

   >[!IMPORTANT]
   >Sie sollten die Option **Vorhandenen Inhalt in der Cloud-Instanz vor der Aufnahme löschen** deaktivieren, um zu verhindern, dass der vorhandene Inhalt aus der vorherigen Aufnahmeaktivität gelöscht wird. Klicken Sie außerdem auf **Kundenunterstützung**, um ein Ticket zu erstellen, wie in der vorherigen Abbildung dargestellt.

## Wie geht es weiter {#whats-next}

Nachdem Sie die Erfassung von Inhalten in Target im Content Transfer Tool gelernt haben, können Sie nach Abschluss jedes Schritts (Extraktion und Aufnahme) Protokolle anzeigen und nach Fehlern suchen. Siehe [Anzeigen von Protokollen für einen Migrationssatz](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/viewing-logs.html?lang=en) , um mehr zu erfahren.
