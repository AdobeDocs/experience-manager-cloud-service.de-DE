---
title: Extrahieren von Inhalten aus der Quelle
description: Extrahieren von Inhalten aus der Quelle
exl-id: c5c08c4e-d5c3-4a66-873e-96986e094fd3
source-git-commit: 5075482f48bf9aaf2c7386af74c14a50b4469840
workflow-type: tm+mt
source-wordcount: '765'
ht-degree: 100%

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
>Wenn Amazon S3, Azure Data Store oder File Data Store als Typ des Datenspeichers verwendet wird, können Sie den optionalen Schritt der Vorabkopie ausführen, um die Extraktionsphase erheblich zu beschleunigen. Der Schritt der Vorabkopie ist am effektivsten für die erste vollständige Extraktion und Aufnahme. Dazu müssen Sie eine `azcopy.config`-Datei konfigurieren, bevor Sie die Extraktion ausführen. Weitere Informationen finden Sie unter [Umgang mit großen Inhalts-Repositorys](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=de).

>[!IMPORTANT]
>Sie sollten das Tool für die Benutzerzuordnung ausführen, bevor Sie Inhalte aus der Quelle extrahieren. Weitere Informationen finden Sie unter [Verwendung des Tools für die Benutzerzuordnung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/user-mapping-tool/using-user-mapping-tool.html?lang=de).

1. Wählen Sie im Assistenten zur **Inhaltsübertragung** einen Migrationssatz aus und klicken Sie auf **Extrahieren**, um die Extraktion zu starten.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam12.png)

   >!![IMPORTANT]
   Vergewissern Sie sich, dass der Extraktionsschlüssel gültig ist und nicht kurz vor seinem Ablaufdatum ist. Wenn das Ablaufdatum kurz bevorsteht, können Sie den Extraktionsschlüssel verlängern, indem Sie den Migrationssatz auswählen und auf Eigenschaften klicken. Klicken Sie auf **Verlängern**. Dies führt Sie zum Cloud Acceleration Manager, wo Sie auf **Extraktionsschlüssel kopieren** klicken können. Jedes Mal, wenn Sie auf **Extraktionsschlüssel kopieren** klicken, wird ein neuer Extraktionsschlüssel generiert, der ab Erstellung 14 Tage lang gültig ist.
   [!image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam13.png)

1. Dadurch wird das Dialogfeld „Extraktion“ angezeigt. Klicken Sie auf **Extrahieren**, um die Extraktionsphase zu starten.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam14.png)

   >[!NOTE]
Sie haben die Option, Staging-Container während der Extraktionsphase zu überschreiben. Wenn **Staging-Container überschreiben** deaktiviert ist, kann es die Extraktion für nachfolgende Migrationen beschleunigen, bei denen die Einstellungen für Inhaltspfade oder eingeschlossene Versionen nicht geändert wurden. Wenn sich die Einstellungen für Inhaltspfade oder eingeschlossene Versionen jedoch geändert haben, dann sollte **Staging-Container überschreiben** aktiviert sein.

   >[!IMPORTANT]
Wenn die Benutzerzuordnung nicht vor dem Extrahieren von Inhalten aus einer Quelle für diesen Migrationssatz ausgeführt wurde, wird eine Warnung mit dem Hinweis angezeigt, dass der Schritt „Benutzerzuordnung“ aussteht, wie in der folgenden Abbildung dargestellt. Klicken Sie auf **Benutzer zuordnen**, um das Tool für die Benutzerzuordnung auszuführen.

1. Im Feld **EXTRAKTION** wird jetzt der Status **WIRD AUSGEFÜHRT** angezeigt, um anzugeben, dass die Extraktion ausgeführt wird.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam15.png)

   Sie können auf **Fortschritt anzeigen** klicken, um einen detaillierten Überblick über die laufende Extraktion zu erhalten.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam16.png)

   Sie können den Fortschritt der Extraktionsphase auch über den Cloud Acceleration Manager überwachen, indem Sie die Seite „Inhaltsübertragung“ besuchen.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam17.png)

1. Sobald die Extraktion abgeschlossen ist, können Sie in den anderen Spalten wie **Quelle** und **Pfade** die Details des von Ihnen eingegebenen Migrationssatzes überprüfen, indem Sie auf **...** und dann auf **Details anzeigen** klicken.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam18.png)


## Auffüllextraktion {#top-up-extraction-process}

Das Content Transfer Tool verfügt über eine Funktion, die die differenzielle Auffüllung von Inhalten unterstützt, wobei es möglich ist, nur Änderungen zu übertragen, die seit dem vorherigen Inhaltstransfer vorgenommen wurden.

>[!NOTE]
Nach dem ersten Transfer von Inhalten wird empfohlen, häufige differenzielle Auffüllungen des Inhalts durchzuführen, um den Zeitraum für das Einfrieren des Inhalts für den endgültigen differenziellen Inhaltstransfer zu verkürzen, bevor er in Cloud Service live geschaltet wird. Wenn Sie den Schritt der Vorabkopie für die erste vollständige Extraktion verwendet haben, können Sie die Vorabkopie für nachfolgende Auffüllextraktionen überspringen (wenn die Größe des Auffüllmigrationssatzes weniger als 200 GB beträgt), da dies den gesamten Prozess verlängern kann.
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
