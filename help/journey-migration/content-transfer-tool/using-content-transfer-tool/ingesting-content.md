---
title: Aufnahme von Inhalten in Target
description: Aufnahme von Inhalten in Target
exl-id: d8c81152-f05c-46a9-8dd6-842e5232b45e
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '527'
ht-degree: 97%

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
>Sie können den optionalen Pre-Copy-Schritt ausführen, um die Aufnahmephase erheblich zu beschleunigen. Weitere Informationen finden Sie unter [Aufnehmen mit AzCopy](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=de#ingesting-azcopy).

1. Wählen Sie auf der Seite **Inhaltstransfer** einen Migrationssatz aus und klicken Sie auf **Aufnehmen**, um die Aufnahme zu starten.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-01.png)

1. Das Dialogfeld **Aufnahme des Migrationssatzes** wird angezeigt. Inhalte können gleichzeitig in die Autoren- oder Veröffentlichungsinstanz aufgenommen werden. Wählen Sie die Instanz aus, in die Inhalte aufgenommen werden sollen. Klicken Sie auf **Aufnehmen**, um die Aufnahmephase zu starten.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-02.png)

   >[!IMPORTANT]
   >Wenn die Aufnahme mit einer Vorkopie verwendet wird (für den S3- oder Azure Data Store), wird empfohlen, die Autorenaufnahme zuerst allein auszuführen. Dadurch wird die Aufnahme der Veröffentlichung beschleunigt, wenn sie später ausgeführt wird.

   >[!IMPORTANT]
   >Wenn die Option **Vorhandene Inhalte in der Cloud-Instanz vor der Erfassung löschen** aktiviert ist, wird das gesamte vorhandene Repository gelöscht und ein neues Repository erstellt, in dem Inhalte erfasst werden. Das bedeutet, dass alle Einstellungen einschließlich der Berechtigungen für die Cloud Service-Zielinstanz zurückgesetzt werden. Dies gilt auch für Administratoren, die der Gruppe **Administratoren** hinzugefügt werden.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-03.png)

   Klicken Sie außerdem auf **Kundenunterstützung**, um ein Ticket zu erstellen, wie in der Abbildung unten dargestellt.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-04.png)

   Weitere Informationen finden Sie unter [Wichtige Überlegungen zur Verwendung des Content Transfer Tools](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=de#important-considerations).

1. Sobald die Aufnahme abgeschlossen ist, wird der Status unter **Aufnahme durch Autor** auf **BEENDET** aktualisiert.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ingestion-05.png)

## Auffüllaufnahme {#top-up-ingestion-process}

Das Content Transfer Tool verfügt über eine Funktion, die die differenzielle *Auffüllung* von Inhalten unterstützt, wobei es möglich ist, nur Änderungen zu übertragen, die seit dem vorherigen Inhaltstransfer vorgenommen wurden.

>[!NOTE]
>Nach dem ersten Transfer von Inhalten wird empfohlen, häufige differenzielle Auffüllungen des Inhalts durchzuführen, um den Zeitraum für das Einfrieren des Inhalts für den endgültigen differenziellen Inhaltstransfer zu verkürzen, bevor er in Cloud Service live geschaltet wird.

Sobald die Aufnahme abgeschlossen ist, können Sie Delta-Inhalte mithilfe der Auffüllaufnahme übertragen. Führen Sie dazu folgende Schritte durch:

1. Gehen Sie zum Assistenten **Inhaltstransfer** und wählen Sie den Migrationssatz aus, für den Sie die Auffüllaufnahme durchführen möchten. Klicken Sie auf **Aufnehmen**, um die Auffüllaufnahme zu starten.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/topup-ingest1.png)


1. Das Dialogfeld **Aufnahme des Migrationssatzes** wird angezeigt.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/topup-ingest2.png)

   >[!IMPORTANT]
   >Sie sollten die Option **Vorhandenen Inhalt in der Cloud-Instanz vor der Aufnahme löschen** deaktivieren, um zu verhindern, dass der vorhandene Inhalt aus der vorherigen Aufnahmeaktivität gelöscht wird. Klicken Sie außerdem auf **Kundenunterstützung**, um ein Ticket zu erstellen, wie in der vorherigen Abbildung dargestellt.

## Wie geht es weiter {#whats-next}

Wenn Sie sich mit der Aufnahme von Inhalten in das Zielsystem im Content Transfer Tool vertraut gemacht haben, können Sie die Protokolle nach Abschluss der einzelnen Schritte (Extraktion und Aufnahme) einsehen und nach Fehlern suchen. Weitere Informationen finden Sie unter [Anzeigen von Protokollen für einen Migrationssatz](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/viewing-logs.html?lang=de).
