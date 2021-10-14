---
title: Erfassen von Inhalten in Target im Content Transfer Tool
description: Erfassen von Inhalten in Target im Content Transfer Tool
source-git-commit: d638fe0f4711bd152bd9c4be99a68662f12072e6
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 63%

---


# Erfassen von Inhalten in Target im Content Transfer Tool {#ingesting-content}

## Aufnahmevorgang im Content Transfer Tool {#ingestion-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_ingestion"
>title="Inhaltsaufnahme"
>abstract="Aufnahme bezieht sich auf die Aufnahme von Inhalten aus dem Migrationssatz in die Cloud Service-Zielinstanz. Das Content Transfer Tool verfügt über eine Funktion, die die differenzielle Auffüllung von Inhalten unterstützt, wobei es möglich ist, nur Änderungen zu übertragen, die seit dem vorherigen Inhaltstransfer vorgenommen wurden."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#top-up-ingestion-process" text="Auffüllaufnahme"

Gehen Sie wie folgt vor, um den Migrationssatz aus dem Content Transfer Tool aufzunehmen:
>[!NOTE]
>Wenn Amazon S3 oder Azure Data Store als Datenspeichertyp verwendet wird, können Sie den optionalen Pre-Copy-Schritt ausführen, um die Aufnahmephase erheblich zu beschleunigen. Weitere Informationen finden Sie unter [Erfassen mit AzCopy](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=en#ingesting-azcopy) .

1. Wählen Sie auf der Seite **Inhaltstransfer** einen Migrationssatz aus und klicken Sie auf **Aufnehmen** , um die Aufnahme zu starten.

   ![Bild](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ingestion-01.png)

1. Das Dialogfeld **Aufnahme des Migrationssatzes** wird angezeigt. Inhalte können gleichzeitig in der Autoren- oder Veröffentlichungsinstanz aufgenommen werden. Wählen Sie die Instanz aus, in der Inhalte aufgenommen werden sollen. Klicken Sie auf **Aufnehmen**, um die Aufnahmephase zu starten.

   ![Bild](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ingestion-02.png)

   >[!IMPORTANT]
   >Wenn die Aufnahme mit einer Vorkopie verwendet wird (für den S3- oder Azure-Datenspeicher), wird empfohlen, die Autorenaufnahme zuerst allein auszuführen. Dadurch wird die Aufnahme der Veröffentlichung beschleunigt, wenn sie später ausgeführt wird.

   >[!IMPORTANT]
   >Wenn die Option **Vorhandenen Inhalt in der Cloud-Instanz vor der Erfassung löschen** aktiviert ist, wird das gesamte vorhandene Repository gelöscht und ein neues Repository erstellt, in dem Inhalte erfasst werden. Das bedeutet, dass alle Einstellungen einschließlich der Berechtigungen für die Cloud Service-Zielinstanz zurückgesetzt werden. Dies gilt auch für Administratoren, die der Gruppe **Administratoren** hinzugefügt werden.

   ![Bild](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ingestion-03.png)

   Klicken Sie außerdem auf **Kundenunterstützung** , um ein Ticket zu protokollieren, wie in der folgenden Abbildung dargestellt.

   ![Bild](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/ingestion-04.png)

   Weitere Informationen finden Sie unter [Wichtige Überlegungen zur Verwendung des Content Transfer Tools](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=en#important-considerations).

1. Sobald die Aufnahme abgeschlossen ist, wird der Status unter **Autorenaufnahme** in **FINISHED** aktualisiert.

   ![Bild](/help/move-to-cloud-service/content-transfer-tool/assets/15-ingestion-complete.png)

## Auffüllaufnahme {#top-up-ingestion-process}

Das Content Transfer Tool verfügt über eine Funktion, die die differenzielle *Auffüllung* von Inhalten unterstützt, wobei es möglich ist, nur Änderungen zu übertragen, die seit dem vorherigen Inhaltstransfer vorgenommen wurden.

>[!NOTE]
>Nach dem ersten Transfer von Inhalten wird empfohlen, häufige differenzielle Auffüllungen des Inhalts durchzuführen, um den Zeitraum für das Einfrieren des Inhalts für den endgültigen differenziellen Inhaltstransfer zu verkürzen, bevor er in Cloud Service live geschaltet wird.

Sobald die Aufnahme abgeschlossen ist, können Sie Delta-Inhalte mithilfe der Auffüllaufnahme übertragen. Führen Sie dazu folgende Schritte durch:

1. Navigieren Sie zur Seite *Übersicht* und wählen Sie den Migrationssatz aus, für den Sie die Auffüllaufnahme durchführen möchten. Klicken Sie auf **Aufnehmen**, um die Auffüllaufnahme zu starten. Das Dialogfeld **Aufnahme des Migrationssatzes** wird angezeigt.

   ![Bild](/help/move-to-cloud-service/content-transfer-tool/assets/content-ingestion-02.png)

   >[!IMPORTANT]
   >Sie sollten die Option **Vorhandenen Inhalt in der Cloud-Instanz vor der Aufnahme löschen** deaktivieren, um zu verhindern, dass der vorhandene Inhalt aus der vorherigen Aufnahmeaktivität gelöscht wird. Klicken Sie außerdem auf **Kundenunterstützung**, um ein Ticket zu erstellen, wie in der vorherigen Abbildung dargestellt.
