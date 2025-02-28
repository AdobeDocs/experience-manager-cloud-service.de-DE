---
title: 'Extrahieren von Inhalten aus der Quelle  '
description: Erfahren Sie, wie Sie Inhalte aus einer Adobe Experience Manager(AEM)-Quellinstanz extrahieren, um sie später in eine Cloud Service-AEM-Instanz zu übertragen.
exl-id: c5c08c4e-d5c3-4a66-873e-96986e094fd3
feature: Migration
role: Admin
source-git-commit: d568619bd8ebb42a6914211401df680352c921ab
workflow-type: tm+mt
source-wordcount: '789'
ht-degree: 92%

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
>Wenn Amazon S3, Azure Data Store oder File Data Store als Typ des Datenspeichers verwendet wird, können Sie den optionalen Schritt einer Vorabkopie ausführen, um die Extraktionsphase zu beschleunigen. Der Schritt der Vorabkopie ist am effektivsten bei der ersten vollständigen Extraktion und Aufnahme. Weitere Informationen finden Sie unter [Handhabung großer Inhalts-Repositorys](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md).

1. Wählen Sie im Assistenten zur **Inhaltsübertragung** einen Migrationssatz aus und klicken Sie auf **Extrahieren**, um die Extraktion zu starten.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam12.png)

   >[!TIP]
   >Eine Aufnahme kann nun so geplant werden, dass sie unmittelbar nach erfolgreichem Abschluss einer Extraktion automatisch startet. Siehe [Aufnehmen von Inhalten in das Ziel](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md) für weitere Informationen.

   >[!IMPORTANT]
   >
   >Vergewissern Sie sich, dass der Extraktionsschlüssel gültig und nicht kurz vor seinem Ablaufdatum ist. Wenn das Ablaufdatum kurz bevorsteht, können Sie den Extraktionsschlüssel verlängern, indem Sie den Migrationssatz auswählen und auf „Eigenschaften“ klicken. Klicken Sie auf **Verlängern**. Dies führt Sie zum Cloud Acceleration Manager, wo Sie auf **Extraktionsschlüssel kopieren** klicken können. Jedes Mal, wenn Sie auf **Extraktionsschlüssel kopieren** klicken, wird ein neuer Extraktionsschlüssel generiert, der ab Erstellung 14 Tage lang gültig ist.
   >![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/migrationSetDetails.png)

1. Dadurch wird das Dialogfeld „Extraktion“ angezeigt. Klicken Sie auf **Extrahieren**, um die Extraktionsphase zu starten.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/migrationSetExtraction.png)

   >[!NOTE]
   >Sie haben die Option, Staging-Container während der Extraktionsphase zu überschreiben. Wenn **Staging-Container überschreiben** deaktiviert ist, kann dies die Extraktion für nachfolgende Migrationen beschleunigen, bei denen die Einstellungen für Inhaltspfade oder eingeschlossene Versionen nicht geändert wurden. Wenn sich jedoch die Einstellungen für Inhaltspfade oder eingeschlossene Versionen geändert haben, dann sollte **Staging-Container überschreiben** aktiviert sein.

1. Im Feld **EXTRAKTION** wird jetzt der Status **WIRD AUSGEFÜHRT** angezeigt, um anzugeben, dass die Extraktion ausgeführt wird.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam15.png)

   Sie können auf **Fortschritt anzeigen** klicken, um einen detaillierten Überblick über die laufende Extraktion zu erhalten.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/viewProgress.png)

   Sie können auch den Fortschritt der Extraktionsphase von Cloud Acceleration Manager überwachen, indem Sie die Seite für den Inhaltstransfer aufrufen und ihn sich durch Klicken auf **…** > **Details anzeigen** anzeigen lassen.

   ![Bild](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam17.png)

1. Wenn die Extraktion abgeschlossen ist, überprüfen Sie die anderen Spalten wie **Quelle** und **Pfade** für Details zum Migrationssatz, den Sie ausgefüllt haben. Klicken Sie auf **…** > **Details anzeigen**, um Details anzuzeigen, einschließlich der Dauer jedes Extraktionsschritts. Rufen Sie dieses Dialogfeld während der Extraktion auf, um sich über den Fortschritt der einzelnen Schritte zu informieren.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam18b.png)


## Auffüllextraktion {#top-up-extraction-process}

Das Content Transfer Tool verfügt über eine Funktion, die die differenzielle Auffüllung von Inhalten unterstützt, wobei es möglich ist, nur Änderungen zu übertragen, die seit dem vorherigen Inhaltstransfer vorgenommen wurden.

>[!NOTE]
>Nach dem ersten Transfer von Inhalten wird empfohlen, häufige differenzielle Auffüllungen des Inhalts durchzuführen, um den Zeitraum für das Einfrieren des Inhalts für den endgültigen differenziellen Inhaltstransfer zu verkürzen, bevor er in Cloud Service live geschaltet wird. Falls Sie den Schritt der Vorabkopie für die erste vollständige Extraktion verwendet haben, können Sie die Vorabkopie für nachfolgende Auffüllextraktionen überspringen (sofern die Größe des Auffüllmigrationssatzes weniger als 200 GB beträgt). Dadurch kann sich nämlich der gesamte Vorgang verlängern.
>Darüber hinaus ist es wichtig, dass die Inhaltsstruktur vorhandener Inhalte von dem Zeitpunkt an nicht geändert wird, zu dem die erste Extraktion erfolgt, bis zum Zeitpunkt der Ausführung der Auffüllextraktion. Für Inhalte, deren Struktur seit der ersten Extraktion geändert wurde, können keine Auffüllungen ausgeführt werden. Achten Sie darauf, dies während des Migrationsprozesses entsprechend einzuschränken.

>[!NOTE]
>Nachdem Inhaltspfade in den Staging-Container migriert wurden, können diese Pfade oder alle darin enthaltenen Unterpfade nicht mehr entfernt oder von nachfolgenden Auffüllmigrationen ausgeschlossen werden.
>Beispiel: Erstmigration: content/dam/weRetail,
>Nächster Versuch eines Auffüllausschlusses: content/dam/weRetail/ab.
>In diesem Szenario ist das Ausschließen von content/dam/weRetail/ab nicht möglich, da die Daten bereits in den Staging-Container migriert wurden.

Sobald die Extraktion abgeschlossen ist, können Sie Delta-Inhalte mithilfe der Auffüllextraktion übertragen.

Führen Sie dazu folgende Schritte durch:

1. Gehen Sie zur Seite **Inhaltsübertragung** und wählen Sie den Migrationssatz aus, für den Sie die Auffüllextraktion durchführen möchten. Klicken Sie auf **Extrahieren**, um die Auffüllextraktion zu starten.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam19.png)

1. Das Dialogfeld **Extraktion des Migrationssatzes** wird angezeigt. Klicken Sie auf **Extrahieren**.

   >[!IMPORTANT]
   >Sie sollten die Option **Überschreiben des Staging-Containers während der Extraktion** deaktivieren.
   >![image](/help/journey-migration/content-transfer-tool/assets-ctt/overwriteStagingContainer.png)


## Wie geht es weiter {#whats-next}

Nachdem Sie sich mit dem Extrahieren von Inhalten aus einer Quelle im Content Transfer Tool vertraut gemacht haben, sind Sie nun bereit, den Aufnahmeprozess im Content Transfer Tool zu erlernen. Unter [Aufnehmen von Inhalten in das ZIel](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md) erfahren Sie, wie Sie Ihren Migrationssatz mit dem Content Transfer Tool aufnehmen können.
