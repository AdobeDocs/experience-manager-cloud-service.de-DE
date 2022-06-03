---
title: Extrahieren von Inhalten aus der Quelle (Veraltet)
description: Extrahieren von Inhalten aus der Quelle
hide: true
hidefromtoc: true
source-git-commit: 1fb4d0f2a3b3f9a27f5ab1228ec2d419149e0764
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 100%

---

# Extrahieren von Inhalten aus der Quelle (Veraltet) {#extracting-content}

## Extraktionsvorgang im Content Transfer Tool {#extraction-process}

Gehen Sie wie folgt vor, um den Migrationssatz aus dem Content Transfer Tool zu extrahieren:
>[!NOTE]
>Wenn Amazon S3 oder Azure Data Store als Datenspeichertyp verwendet wird, können Sie den optionalen Vorkopierschritt ausführen, um die Extraktionsphase erheblich zu beschleunigen. Dazu müssen Sie eine `azcopy.config`-Datei konfigurieren, bevor Sie die Extraktion ausführen. Weitere Informationen finden Sie unter [Umgang mit großen Inhalts-Repositorys](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=de).

>[!IMPORTANT]
>Sie sollten das Tool für die Benutzerzuordnung ausführen, bevor Sie Inhalte aus der Quelle extrahieren. Weitere Informationen finden Sie unter [Verwendung des Tools für die Benutzerzuordnung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/user-mapping-tool/using-user-mapping-tool.html?lang=de).

1. Wählen Sie im Assistenten zur **Inhaltsübertragung** einen Migrationssatz aus und klicken Sie auf **Extrahieren**, um die Extraktion zu starten.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/extraction-01.png)

1. Das Dialogfeld **Extraktion des Migrationssatzes** wird angezeigt. Klicken Sie auf **Extrahieren**, um die Extraktion zu starten.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/extraction-02.png)

   >[!NOTE]
   >Sie haben die Möglichkeit, Staging-Container während der Extraktion zu überschreiben.

   >[!IMPORTANT]
   >Wenn die Benutzerzuordnung nicht vor dem Extrahieren von Inhalten aus einer Quelle für diesen Migrationssatz ausgeführt wurde, wird eine Warnung mit dem Hinweis angezeigt, dass der Schritt „Benutzerzuordnung“ aussteht, wie in der folgenden Abbildung dargestellt. Klicken Sie auf **Benutzer zuordnen**, um das Tool für die Benutzerzuordnung auszuführen.
   >![image](/help/journey-migration/content-transfer-tool/assets-ctt/user-mapping-extract.png)

1. Im Feld **EXTRAKTION** wird jetzt der Status **WIRD AUSGEFÜHRT** angezeigt, um anzugeben, dass die Extraktion ausgeführt wird.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/extraction-03.png)

   Sobald die Extraktion abgeschlossen ist, wird der Status des Migrationssatzes auf **BEENDET** aktualisiert und unter dem Feld *INFO* wird ein **grünes** Wolkensymbol angezeigt.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/extraction-04.png)

   >[!IMPORTANT]
   >Die Benutzeroberfläche verfügt über eine Funktion zum automatischen Neuladen, die den Assistenten für die **Inhaltsübertragung** alle 30 Sekunden neu lädt.
   >Beim Starten der Extraktionsphase wird die Schreibsperre aktiviert und nach *60 Sekunden* wieder aufgehoben. Wenn also eine Extraktion gestoppt wird, müssen Sie eine Minute warten, bis die Sperre aufgehoben wird, bevor Sie die Extraktion erneut starten können.

## Auffüllextraktion {#top-up-extraction-process}

Das Content Transfer Tool verfügt über eine Funktion, die die differenzielle Auffüllung von Inhalten unterstützt, wobei es möglich ist, nur Änderungen zu übertragen, die seit dem vorherigen Inhaltstransfer vorgenommen wurden.

>[!NOTE]
>Nach dem ersten Transfer von Inhalten wird empfohlen, häufige differenzielle Auffüllungen des Inhalts durchzuführen, um den Zeitraum für das Einfrieren des Inhalts für den endgültigen differenziellen Inhaltstransfer zu verkürzen, bevor er in Cloud Service live geschaltet wird.
>Darüber hinaus ist es wichtig, dass die Inhaltsstruktur vorhandener Inhalte von dem Zeitpunkt an nicht geändert wird, zu dem die erste Extraktion erfolgt, bis zum Zeitpunkt der Ausführung der Auffüllextraktion. Für Inhalte, deren Struktur seit der ersten Extraktion geändert wurde, können keine Auffüllungen ausgeführt werden. Stellen Sie sicher, dass Sie dies während des Migrationsprozesses einschränken.

Sobald die Extraktion abgeschlossen ist, können Sie Delta-Inhalte mithilfe der Auffüllextraktion übertragen.

Führen Sie dazu folgende Schritte durch:

1. Gehen Sie zur Seite **Inhaltsübertragung** und wählen Sie den Migrationssatz aus, für den Sie die Auffüllextraktion durchführen möchten. Klicken Sie auf **Extrahieren**, um die Auffüllextraktion zu starten.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/extraction-05.png)

1. Das Dialogfeld **Extraktion des Migrationssatzes** wird angezeigt. Klicken Sie auf **Extrahieren**.

   >[!IMPORTANT]
   >Sie sollten die Option **Überschreiben des Staging-Containers während der Extraktion** deaktivieren.
   >![image](/help/journey-migration/content-transfer-tool/assets-ctt/extraction-06.png)


## Wie geht es weiter {#whats-next}

Sobald Sie das Extrahieren von Inhalten aus einer Quelle im Content Transfer Tool gelernt haben, können Sie jetzt etwas über den Aufnahmevorgang im Content Transfer Tool erfahren. Unter [Aufnahme von Inhalten in Target](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md) erfahren Sie, wie Sie Ihren Migrationssatz mit dem Content Transfer Tool aufnehmen können.
