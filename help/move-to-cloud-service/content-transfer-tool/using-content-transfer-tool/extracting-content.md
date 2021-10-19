---
title: Extrahieren von Inhalten aus der Quelle
description: Extrahieren von Inhalten aus der Quelle
source-git-commit: 5cdfa5a84e74563245d95661dc6875e16982d941
workflow-type: tm+mt
source-wordcount: '601'
ht-degree: 45%

---


# Extrahieren von Inhalten aus der Quelle {#extracting-content}

## Extraktionsprozess im Content Transfer Tool {#extraction-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_extraction"
>title="Inhaltsextraktion"
>abstract="Extraktion bezieht sich auf das Extrahieren von Inhalten aus der AEM-Quellinstanz in einen temporären Bereich, der als Migrationssatz bezeichnet wird. Ein Migrationssatz ist ein Cloud-Speicherplatzbereich, der von Adobe bereitgestellt wird, um die übertragenen Inhalte vorübergehend zwischen der AEM-Quellinstanz und der Cloud Service-AEM-Instanz zu speichern."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=de#top-up-extraction-process" text="Auffüllextraktion"


Gehen Sie wie folgt vor, um den Migrationssatz aus dem Content Transfer Tool zu extrahieren:
>[!NOTE]
>Wenn Amazon S3 oder Azure Data Store als Datenspeichertyp verwendet wird, können Sie den optionalen Vorkopieschritt ausführen, um die Extraktionsphase erheblich zu beschleunigen. Dazu müssen Sie eine `azcopy.config` Datei vor der Extraktion. Siehe [Umgang mit großen Inhaltsverzeichnissen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=en) für weitere Details.

**Vor dem Extrahieren von Inhalt aus der Quelle**
Sie sollten das Tool zur Benutzerzuordnung ausführen, bevor Sie Inhalte aus der Quelle extrahieren. Siehe [Verwenden des Benutzerzuordnungstools](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/user-mapping-tool/using-user-mapping-tool.html?lang=en) für weitere Details.

1. Wählen Sie einen Migrationssatz aus **Inhaltstransfer** Assistent und klicken Sie auf **Extract** um die Extraktion zu starten.

   ![Bild](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/extraction-01.png)

1. Das Dialogfeld **Extraktion des Migrationssatzes** wird angezeigt. Klicken Sie auf **Extrahieren**, um die Extraktion zu starten.

   ![Bild](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/extraction-02.png)

   >[!NOTE]
   >Sie haben die Möglichkeit, Staging-Container während der Extraktion zu überschreiben.

   >[!IMPORTANT]
   >Wenn die Benutzerzuordnung nicht vor dem Extrahieren von Inhalt aus einer Quelle für diesen Migrationssatz ausgeführt wurde, wird eine Warnung mit dem Hinweis angezeigt, dass der Schritt &quot;Benutzerzuordnung&quot;aussteht, wie in der folgenden Abbildung dargestellt. Klicken Sie auf **Benutzer zuordnen** , um das Tool zur Benutzerzuordnung auszuführen.
   >![Bild](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/user-mapping-extract.png)

1. Die **Extraktion** -Feld zeigt nun die **AUSFÜHRUNG** -Status, um anzugeben, dass die Extraktion ausgeführt wird.

   ![Bild](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/extraction-03.png)

   Sobald die Extraktion abgeschlossen ist, wird der Status des Migrationssatzes auf **BEENDET** aktualisiert und unter dem Feld *INFO* wird ein **grünes** Wolkensymbol angezeigt.

   ![Bild](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/extraction-04.png)

   >[!IMPORTANT]
   >Die Benutzeroberfläche verfügt über eine Funktion zum automatischen Neuladen, mit der die **Inhaltstransfer** Assistent alle 30 Sekunden.
   >Beim Starten der Extraktionsphase wird die Schreibsperre aktiviert und nach *60 Sekunden* wieder aufgehoben. Wenn also eine Extraktion gestoppt wird, müssen Sie eine Minute warten, bis die Sperre aufgehoben wird, bevor Sie die Extraktion erneut starten können.

## Auffüllextraktion {#top-up-extraction-process}

Das Content Transfer Tool verfügt über eine Funktion, die die differenzielle Auffüllung von Inhalten unterstützt, wobei es möglich ist, nur Änderungen zu übertragen, die seit dem vorherigen Inhaltstransfer vorgenommen wurden.

>[!NOTE]
>Nach dem ersten Transfer von Inhalten wird empfohlen, häufige differenzielle Auffüllungen des Inhalts durchzuführen, um den Zeitraum für das Einfrieren des Inhalts für den endgültigen differenziellen Inhaltstransfer zu verkürzen, bevor er in Cloud Service live geschaltet wird.
>Darüber hinaus ist es wichtig, dass die Inhaltsstruktur vorhandener Inhalte nicht von dem Zeitpunkt an geändert wird, zu dem die erste Extraktion erfolgt, bis zum Zeitpunkt der Auffüllextraktion. Auffüllungen können nicht für Inhalte ausgeführt werden, deren Struktur seit der ersten Extraktion geändert wurde. Bitte stellen Sie sicher, dass Sie dies während des Migrationsprozesses einschränken.

Sobald die Extraktion abgeschlossen ist, können Sie Delta-Inhalte mithilfe der Auffüllextraktion übertragen.

Führen Sie dazu folgende Schritte durch:

1. Navigieren Sie zum **Inhaltstransfer** und wählen Sie den Migrationssatz aus, für den Sie die Auffüllextraktion durchführen möchten. Klicken Sie auf **Extrahieren**, um die Auffüllextraktion zu starten.

   ![image](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/extraction-05.png)

1. Die **Extraktion des Migrationssatzes** angezeigt. Klicken Sie auf **Extract**.

   >[!IMPORTANT]
   >Sie sollten die Option **Überschreiben des Staging-Containers während der Extraktion** deaktivieren.
   >![Bild](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/extraction-06.png)


## Wie geht es weiter {#whats-next}

Sobald Sie das Extrahieren von Inhalt aus einer Quelle im Content Transfer Tool gelernt haben, können Sie jetzt den Aufnahmevorgang im Content Transfer Tool erlernen. Siehe [Erfassen von Inhalten in Target](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool/ingesting-content.md) , um zu erfahren, wie Sie Ihren Migrationssatz über das Content Transfer Tool aufnehmen.
