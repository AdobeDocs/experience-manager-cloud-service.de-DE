---
title: Extrahieren von Inhalten aus der Quelle
description: Extrahieren von Inhalten aus der Quelle
exl-id: c5c08c4e-d5c3-4a66-873e-96986e094fd3
source-git-commit: 5075482f48bf9aaf2c7386af74c14a50b4469840
workflow-type: tm+mt
source-wordcount: '765'
ht-degree: 56%

---

# Extrahieren von Inhalten aus der Quelle {#extracting-content}

## Extraktionsvorgang im Content Transfer Tool {#extraction-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_extraction"
>title="Inhaltsextraktion"
>abstract="Extraktion bezieht sich auf das Extrahieren von Inhalten aus der AEM-Quellinstanz in einen temporären Bereich, der als Migrationssatz bezeichnet wird. Ein Migrationssatz ist ein Cloud-Speicherplatzbereich, der von Adobe bereitgestellt wird, um die übertragenen Inhalte vorübergehend zwischen der AEM-Quellinstanz und der Cloud Service-AEM-Instanz zu speichern."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=de#top-up-extraction-process" text="Auffüllextraktion"


Gehen Sie wie folgt vor, um den Migrationssatz aus dem Content Transfer Tool zu extrahieren:

>[!NOTE]
>Wenn Amazon S3, Azure Data Store oder File Data Store als Datenspeichertyp verwendet wird, können Sie den optionalen Vorkopieschritt ausführen, um die Extraktionsphase erheblich zu beschleunigen. Der Schritt zum Vorauskopieren ist am effektivsten für die erste vollständige Extraktion und Aufnahme. Dazu müssen Sie eine `azcopy.config`-Datei konfigurieren, bevor Sie die Extraktion ausführen. Weitere Informationen finden Sie unter [Umgang mit großen Inhalts-Repositorys](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=de).

>[!IMPORTANT]
>Sie sollten das Tool für die Benutzerzuordnung ausführen, bevor Sie Inhalte aus der Quelle extrahieren. Weitere Informationen finden Sie unter [Verwendung des Tools für die Benutzerzuordnung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/user-mapping-tool/using-user-mapping-tool.html?lang=de).

1. Wählen Sie im Assistenten zur **Inhaltsübertragung** einen Migrationssatz aus und klicken Sie auf **Extrahieren**, um die Extraktion zu starten.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam12.png)

   >!![IMPORTANT]
   Vergewissern Sie sich, dass der Extraktionsschlüssel gültig ist und nicht kurz vor seinem Ablauf liegt. Wenn das Ablaufdatum näher liegt, können Sie die Extraktionstaste verlängern, indem Sie den Migrationssatz auswählen und auf Eigenschaften klicken. Klicken Sie auf **Verlängern**. Dadurch gelangen Sie zum Cloud Acceleration Manager, auf den Sie klicken können. **Extraktionsschlüssel kopieren**. Jedes Mal, wenn Sie auf **Extraktionsschlüssel kopieren**, wird ein neuer Extraktionsschlüssel generiert, der 14 Tage nach der Erstellung gültig ist.
   [!image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam13.png)

1. Dadurch wird das Dialogfeld Extraktion angezeigt. Klicken Sie auf **Extract** zur Einleitung der Extraktionsphase.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam14.png)

   >[!NOTE]
Sie können den Staging-Container während der Extraktionsphase überschreiben. Wenn **Staging-Container überschreiben** deaktiviert ist, kann es die Extraktion für nachfolgende Migrationen beschleunigen, bei denen die Einstellungen für Inhaltspfade oder Include-Versionen nicht geändert wurden. Wenn sich die Inhaltspfade oder Einstellungen für Include-Versionen jedoch geändert haben, dann **Staging-Container überschreiben** sollte aktiviert sein.

   >[!IMPORTANT]
Wenn die Benutzerzuordnung nicht für diese Migration ausgeführt wurde, bevor Inhalte aus einer Quelle extrahiert wurden, wird eine Warnung mit dem Hinweis angezeigt, dass der Schritt &quot;Benutzerzuordnung&quot;aussteht, wie in der obigen Abbildung dargestellt. Klicken Sie auf **Benutzer zuordnen**, um das Tool für die Benutzerzuordnung auszuführen.

1. Im Feld **EXTRAKTION** wird jetzt der Status **WIRD AUSGEFÜHRT** angezeigt, um anzugeben, dass die Extraktion ausgeführt wird.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam15.png)

   Sie können auf **Fortschritt anzeigen** um einen detaillierten Überblick über die laufende Extraktion zu erhalten.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam16.png)

   Sie können den Fortschritt der Extraktionsphase auch über Cloud Acceleration Manager überwachen, indem Sie die Seite Inhaltstransfer aufrufen.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam17.png)

1. Überprüfen Sie nach Abschluss der Extraktion die anderen Spalten wie **Quelle** und **Pfade** für Details zum Migrationssatz, den Sie durch Klicken auf **...** und dann **Details anzeigen**.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam18.png)


## Auffüllextraktion {#top-up-extraction-process}

Das Content Transfer Tool verfügt über eine Funktion, die die differenzielle Auffüllung von Inhalten unterstützt, wobei es möglich ist, nur Änderungen zu übertragen, die seit dem vorherigen Inhaltstransfer vorgenommen wurden.

>[!NOTE]
Nach dem ersten Transfer von Inhalten wird empfohlen, häufige differenzielle Auffüllungen des Inhalts durchzuführen, um den Zeitraum für das Einfrieren des Inhalts für den endgültigen differenziellen Inhaltstransfer zu verkürzen, bevor er in Cloud Service live geschaltet wird. Wenn Sie den Schritt zum Vorauskopieren für die erste vollständige Extraktion verwendet haben, können Sie die Vorkopie für nachfolgende Auffüllextraktionen überspringen (wenn die Größe des Auffüllmigrationssatzes kleiner als 200 GB ist), da dies dem gesamten Prozess Zeit hinzufügen kann.
Darüber hinaus ist es wichtig, dass die Inhaltsstruktur vorhandener Inhalte von dem Zeitpunkt an nicht geändert wird, zu dem die erste Extraktion erfolgt, bis zum Zeitpunkt der Ausführung der Auffüllextraktion. Für Inhalte, deren Struktur seit der ersten Extraktion geändert wurde, können keine Auffüllungen ausgeführt werden. Stellen Sie sicher, dass Sie dies während des Migrationsprozesses einschränken.

Sobald die Extraktion abgeschlossen ist, können Sie Delta-Inhalte mithilfe der Auffüllextraktion übertragen.

Führen Sie dazu folgende Schritte durch:

1. Gehen Sie zur Seite **Inhaltsübertragung** und wählen Sie den Migrationssatz aus, für den Sie die Auffüllextraktion durchführen möchten. Klicken Sie auf **Extrahieren**, um die Auffüllextraktion zu starten.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam19.png)

1. Das Dialogfeld **Extraktion des Migrationssatzes** wird angezeigt. Klicken Sie auf **Extrahieren**.

   >[!IMPORTANT]
Sie sollten die Option **Überschreiben des Staging-Containers während der Extraktion** deaktivieren.
   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam20.png)


## Wie geht es weiter {#whats-next}

Sobald Sie das Extrahieren von Inhalten aus einer Quelle im Content Transfer Tool gelernt haben, können Sie jetzt etwas über den Aufnahmevorgang im Content Transfer Tool erfahren. Unter [Aufnahme von Inhalten in Target](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md) erfahren Sie, wie Sie Ihren Migrationssatz mit dem Content Transfer Tool aufnehmen können.
