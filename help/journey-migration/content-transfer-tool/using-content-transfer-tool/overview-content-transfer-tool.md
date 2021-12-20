---
title: Übersicht über das Content Transfer Tool
description: Übersicht über das Content Transfer Tool
source-git-commit: a6d225943c5d23ebd960fda0b0912a81f1f80014
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 77%

---

# Übersicht {#overview-content-transfer-tool}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_overview"
>title="Übersicht"
>abstract="Das Content Transfer Tool ist ein von Adobe entwickeltes Tool, mit dem Sie vorhandene Inhalte von einer AEM-Quellinstanz (On-Premise oder AMS) in die Zielinstanz in AEM Cloud Service verschieben können. Dieses Tool überträgt auch Prinzipale (Benutzer oder Gruppen) automatisch."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=de#extraction-process" text="Extraktionsvorgang"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=de#ingestion-process" text="Aufnahmevorgang"

Das Content Transfer Tool ist ein von Adobe entwickeltes Tool, mit dem Sie vorhandene Inhalte von einer AEM-Quellinstanz (On-Premise oder AMS) in die Zielinstanz in AEM Cloud Service verschieben können.

Dieses Tool überträgt auch Prinzipale (Benutzer oder Gruppen) automatisch.

## Phasen im Content Transfer Tool {#phases-content-transfer-tool}

Beim Inhaltstransfer gibt es zwei Phasen:

1. **Extraktion**: Extraktion bezieht sich auf das Extrahieren von Inhalten aus der AEM-Quellinstanz in einen temporären Bereich, der als *Migrationssatz* bezeichnet wird. Ein *Migrationssatz* ist ein Cloud-Speicherplatzbereich, der von Adobe bereitgestellt wird, um die übertragenen Inhalte vorübergehend zwischen der AEM-Quellinstanz und der Cloud Service-AEM-Instanz zu speichern.

   Weitere Informationen finden Sie unter [Extraktionsvorgang beim Inhaltstransfer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/extracting-content.html).

   >[!NOTE]
   > Es wird empfohlen, das User Mapping Tool als Teil der Extraktion auszuführen. Siehe [Verwenden des Benutzerzuordnungs-Tools](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/user-mapping-tool/using-user-mapping-tool.html) für weitere Details.

1. **Aufnahme**: Aufnahme bezieht sich auf die Aufnahme von Inhalten aus dem *Migrationssatz* in die Cloud Service-Zielinstanz.

   Siehe [Aufnahmevorgang beim Inhaltstransfer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/ingesting-content.html) für weitere Details.

## Attribute eines Migrationssatzes {#attributes-migration-set}

Ein Migrationssatz hat die folgenden Attribute:

* Während der Aktivität zum Content-Transfer können maximal zehn Migrationssätze erstellt und verwaltet werden.
* Jeder Migrationssatz sollte einen eindeutigen Namen haben.
* Wenn ein Migrationssatz länger als 30 Tage inaktiv war, wird er automatisch gelöscht.
* Wenn Sie einen Migrationssatz erstellen, wird er einer bestimmten Umgebung zugeordnet. Sie können nur in eine Autoren- oder Veröffentlichungsinstanz derselben Umgebung aufnehmen.


Das Content Transfer Tool verfügt über eine Funktion, die die differenzielle Auffüllung von Inhalten unterstützt, wobei es möglich ist, nur Änderungen zu übertragen, die seit dem vorherigen Inhaltstransfer vorgenommen wurden.

>[!NOTE]
>Nach dem ersten Transfer von Inhalten wird empfohlen, häufige differenzielle Auffüllungen des Inhalts durchzuführen, um den Zeitraum für das Einfrieren des Inhalts für den endgültigen differenziellen Inhaltstransfer zu verkürzen, bevor er in Cloud Service live geschaltet wird.

In der Extraktionsphase muss die Option ***Überschreiben*** deaktiviert werden, um einen vorhandenen Migrationssatz *aufzufüllen*. Weitere Informationen finden Sie unter [Auffüllextraktion](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/extracting-content.html?lang=en#top-up-extraction-process).

In der Aufnahmephase muss die *Löschoption* deaktiviert werden, damit der Delta-Inhalt zusätzlich zum aktuellen Inhalt angewendet wird. Weitere Informationen finden Sie unter [Auffüllaufnahme](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/ingesting-content.html?lang=en#top-up-ingestion-process).

## Wie geht es weiter {#whats-next}

Nachdem Sie sich mit dem Content Transfer Tool und seiner Übersicht, die dieses Tool beschreibt, vertraut gemacht haben, können Sie vorhandene Inhalte von einer Quell-AEM-Instanz (On-Premise oder AMS) in die Ziel-AEM Cloud Service-Instanz verschieben. Lesen Sie dazu [Voraussetzungen für das Content Transfer Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/prerequisites-content-transfer-tool.html?lang=en).

