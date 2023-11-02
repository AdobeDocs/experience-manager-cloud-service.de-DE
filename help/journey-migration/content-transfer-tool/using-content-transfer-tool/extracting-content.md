---
title: Extrahieren von Inhalten aus der Quelle
description: Erfahren Sie, wie Sie Inhalte aus einer Adobe Experience Manager (AEM)-Quellinstanz extrahieren, um sie später in eine Cloud Service-AEM-Instanz zu übertragen.
exl-id: c5c08c4e-d5c3-4a66-873e-96986e094fd3
source-git-commit: 858e10f99e2015a1488bb9e1d0990a553c5f6d04
workflow-type: tm+mt
source-wordcount: '735'
ht-degree: 43%

---

# Extrahieren von Inhalten aus der Quelle {#extracting-content}

## Extraktionsvorgang im Content Transfer Tool {#extraction-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_extraction"
>title="Inhaltsextraktion"
>abstract="Extraktion bezieht sich auf das Extrahieren von Inhalten aus der Quellinstanz von Adobe Experience Manager (AEM) in einen temporären Bereich, der als Migrationssatz bezeichnet wird. Ein Migrationssatz ist ein Cloud-Speicherplatzbereich, der von Adobe bereitgestellt wird, um die übertragenen Inhalte vorübergehend zwischen der AEM-Quellinstanz und der Cloud Service-AEM-Instanz zu speichern."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=de#top-up-extraction-process" text="Auffüllextraktion"


Gehen Sie wie folgt vor, um den Migrationssatz aus dem Content Transfer Tool zu extrahieren:

>[!NOTE]
>Wenn Amazon S3, Azure Data Store oder File Data Store als Datenspeichertyp verwendet wird, können Sie den optionalen Vorkopieschritt ausführen, um die Extraktionsphase zu beschleunigen. Der Schritt der Vorabkopie ist am effektivsten bei der ersten vollständigen Extraktion und Aufnahme. Weitere Informationen finden Sie unter [Handhabung großer Inhalts-Repositorys](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md).

1. Wählen Sie einen Migrationssatz aus dem **Content Transfer** Assistent und klicken Sie auf **Extract** , um die Extraktion zu starten.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam12.png)

   >[!TIP]
   >Eine Aufnahme kann nun so geplant werden, dass sie unmittelbar nach erfolgreichem Abschluss einer Extraktion automatisch startet. Siehe [Erfassen von Inhalten in Target](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md) für weitere Informationen.

   >[!IMPORTANT]
   >
   >Stellen Sie sicher, dass der Extraktionsschlüssel gültig ist und nicht in der Nähe seines Ablaufs liegt. Wenn das Ablaufdatum näher liegt, können Sie den Extraktionsschlüssel verlängern, indem Sie den Migrationssatz auswählen und auf Eigenschaften klicken. Klicks **Verlängern**. Dadurch gelangen Sie zum Cloud Acceleration Manager, in dem Sie auf Folgendes klicken können: **Extraktionsschlüssel kopieren**. Jedes Mal, wenn Sie auf **Extraktionsschlüssel kopieren**, wird ein neuer Extraktionsschlüssel generiert, der 14 Tage nach der Erstellung gültig ist.
   >![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam13.png)

1. Dadurch wird das Dialogfeld Extraktion angezeigt. Klicks **Extract** zur Einleitung der Extraktionsphase.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam14b.png)

   >[!NOTE]
   >Optional können Sie den Staging-Container während der Extraktionsphase überschreiben. Wenn **Staging-Container überschreiben** deaktiviert ist, kann es die Extraktion für nachfolgende Migrationen beschleunigen, bei denen die Einstellungen für Inhaltspfade oder Include-Versionen nicht geändert wurden. Wenn sich die Einstellungen für Inhaltspfade oder eingeschlossene Versionen jedoch geändert haben, dann sollte **Staging-Container überschreiben** aktiviert sein.

1. Im Feld **EXTRAKTION** wird jetzt der Status **WIRD AUSGEFÜHRT** angezeigt, um anzugeben, dass die Extraktion ausgeführt wird.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam15.png)

   Sie können auf **Fortschritt anzeigen** um einen detaillierten Überblick über die laufende Extraktion zu erhalten.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam16.png)

   Sie können auch den Fortschritt der Extraktionsphase von Cloud Acceleration Manager überwachen, indem Sie die Seite Inhaltstransfer aufrufen und sie durch Klicken auf **...** > **Details anzeigen**.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam17.png)

1. Wenn die Extraktion abgeschlossen ist, überprüfen Sie die anderen Spalten wie **Quelle** und **Pfade** für Details zum Migrationssatz, den Sie ausgefüllt haben. Klicken **...** > **Details anzeigen** um Details anzuzeigen, einschließlich der Dauer jedes Schritts der Extraktion. Zeigen Sie dieses Dialogfeld während der Extraktion an, damit Sie sehen können, wie die Schritte voranschreiten.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam18b.png)


## Auffüllextraktion {#top-up-extraction-process}

Das Content Transfer Tool verfügt über eine Funktion, die die differenzielle Auffüllung von Inhalten unterstützt, wobei es möglich ist, nur Änderungen zu übertragen, die seit dem vorherigen Inhaltstransfer vorgenommen wurden.

>[!NOTE]
>Nach dem ersten Transfer von Inhalten wird empfohlen, häufige differenzielle Auffüllungen des Inhalts durchzuführen, um den Zeitraum für das Einfrieren des Inhalts für den endgültigen differenziellen Inhaltstransfer zu verkürzen, bevor er in Cloud Service live geschaltet wird. Wenn Sie den Schritt zum Vorauskopieren für die erste vollständige Extraktion verwendet haben, können Sie die Vorkopie für nachfolgende Auffüllextraktionen überspringen (wenn die Größe des Auffüllmigrationssatzes kleiner als 200 GB ist). Dadurch kann sich nämlich der gesamte Vorgang verlängern.
>Außerdem ist es wichtig, dass die Inhaltsstruktur vorhandener Inhalte nicht von dem Zeitpunkt an geändert wird, zu dem die erste Extraktion erfolgt, bis zum Zeitpunkt der Auffüllextraktion. Für Inhalte, deren Struktur seit der ersten Extraktion geändert wurde, können keine Auffüllungen ausgeführt werden. Achten Sie darauf, dies während des Migrationsprozesses entsprechend einzuschränken.

Sobald die Extraktion abgeschlossen ist, können Sie Delta-Inhalte mithilfe der Auffüllextraktion übertragen.

Führen Sie dazu folgende Schritte durch:

1. Gehen Sie zur Seite **Inhaltsübertragung** und wählen Sie den Migrationssatz aus, für den Sie die Auffüllextraktion durchführen möchten. Klicken Sie auf **Extrahieren**, um die Auffüllextraktion zu starten.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam19.png)

1. Das Dialogfeld **Extraktion des Migrationssatzes** wird angezeigt. Klicks **Extract**.

   >[!IMPORTANT]
   >Sie sollten die Option **Überschreiben des Staging-Containers während der Extraktion** deaktivieren.
   >![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam20.png)


## Wie geht es weiter {#whats-next}

Nachdem Sie das Extrahieren von Inhalt aus einer Quelle im Content Transfer Tool gelernt haben, können Sie jetzt den Aufnahmevorgang im Content Transfer Tool erlernen. Siehe [Erfassen von Inhalten in Target](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md) wo Sie erfahren können, wie Sie Ihren Migrationssatz über das Content Transfer Tool aufnehmen.
