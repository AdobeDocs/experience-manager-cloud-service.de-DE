---
title: Übersicht über das Content Transfer-Tool
description: Übersicht über das Content Transfer Tool
exl-id: cfc0366a-2139-4d9d-b5bc-0b65bef4013c
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '645'
ht-degree: 82%

---

# Übersicht {#overview-content-transfer-tool}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_overview"
>title="Übersicht"
>abstract="Das Content Transfer Tool ist ein von Adobe entwickeltes Tool, mit dem die Migration vorhandener Inhalte von einer AEM-Quellinstanz (On-Premise oder AMS) in die Zielinstanz in AEM Cloud Service initiiert werden kann. Dieses Tool überträgt auch Prinzipale (Benutzer oder Gruppen) automatisch."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=de" text="Richtlinien und Best Practices"

Das Content Transfer Tool ist ein von Adobe entwickeltes Tool, mit dem die Migration vorhandener Inhalte von einer Quell-AEM-Instanz (On-Premise oder AMS) zur AEM Cloud Service-Zielinstanz initiiert werden kann.

Dieses Tool überträgt auch Prinzipale (Benutzer oder Gruppen) automatisch.  Siehe [Benutzerzuordnung und Hauptmigration](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/user-mapping-and-migration.md) für weitere Informationen.

Das Content Transfer Tool integriert den Inhaltstransferprozess in Cloud Acceleration Manager. Dadurch erhält der Benutzer alle Vorteile, die er bietet:

* Self-Service-Methode zur einmaligen Extraktion eines Migrationssatzes und zur gleichzeitigen Aufnahme in mehrere Umgebungen
* Verbessertes Benutzererlebnis durch verbesserte Ladezustände, Limits und Fehlerbehandlung
* Aufnahmeprotokolle bleiben erhalten und stehen immer zur Fehlerbehebung zur Verfügung.
* Validierungs- und Hauptmigrationsberichte stehen zur Validierung zur Verfügung

## Phasen im Content Transfer Tool {#phases-content-transfer-tool}

Beim Inhaltstransfer gibt es zwei Phasen:

1. **Extraktion**: Extraktion bezieht sich auf das Extrahieren von Inhalten aus der AEM-Quellinstanz in einen temporären Bereich, der als *Migrationssatz* bezeichnet wird. Ein *Migrationssatz* ist ein Cloud-Speicherplatzbereich, der von Adobe bereitgestellt wird, um die übertragenen Inhalte vorübergehend zwischen der AEM-Quellinstanz und der Cloud Service-AEM-Instanz zu speichern.

   Siehe [Extraktionsvorgang beim Inhaltstransfer](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md) für weitere Details.

   >[!NOTE]
   >Die Benutzerzuordnung wird jetzt automatisch im Rahmen der Extraktionsphase bei Author ausgeführt (kann aber optional bei Author deaktiviert oder bei Publish aktiviert werden). Weitere Informationen finden Sie unter [Benutzerzuordnung und Prinzipalmigration](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/user-mapping-and-migration.md).

1. **Aufnahme**: Aufnahme bezieht sich auf die Aufnahme von Inhalten aus dem *Migrationssatz* in die Cloud Service-Zielinstanz.

   Weitere Informationen finden Sie unter [Aufnahmevorgang beim Inhaltstransfer](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md).

## Attribute eines Migrationssatzes {#attributes-migration-set}

Ein Migrationssatz hat die folgenden Attribute:

* Mit der neuen Version können Sie maximal fünf Migrationssätze in einem Projekt erstellen, das in Cloud Acceleration Manager erstellt wurde.
* Jeder Migrationssatz sollte einen eindeutigen Namen haben.

Das Content Transfer Tool verfügt über eine Funktion, die die differenzielle Auffüllung von Inhalten unterstützt, wobei es möglich ist, nur Änderungen zu übertragen, die seit dem vorherigen Inhaltstransfer vorgenommen wurden.

>[!NOTE]
>Nach dem ersten Transfer von Inhalten wird empfohlen, häufige differenzielle Auffüllungen des Inhalts durchzuführen, um den Zeitraum für das Einfrieren des Inhalts für den endgültigen differenziellen Inhaltstransfer zu verkürzen, bevor er in Cloud Service live geschaltet wird.

In der Extraktionsphase muss die Option ***Überschreiben*** deaktiviert werden, um einen vorhandenen Migrationssatz *aufzufüllen*. Siehe [Auffüllextraktion](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process) für weitere Details.

In der Aufnahmephase muss die *Löschoption* deaktiviert werden, damit der Delta-Inhalt zusätzlich zum aktuellen Inhalt angewendet wird. Siehe [Auffüllaufnahme](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process) für weitere Details.

## Ablauf von Migrationssätzen {#migration-set-expiry}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_migrationset_expiry"
>title="Ende der Gültigkeit eines Migrationssatzes"
>abstract="Erfahren Sie mehr über das Ende der Gültigkeit eines Migrationssatzes."

Alle Migrationssätze laufen nach einer längeren Inaktivität von etwa 90 Tagen letztendlich ab. Nachdem entsprechende Hinweise auf der Projektkarte und in den Tabellenzeilen für den Migrationsvorgang über einen bestimmten Zeitraum angezeigt wurden, läuft der Migrationssatz ab, und die zugehörigen Daten sind nicht mehr verfügbar. Die Ablaufzeit kann einfach verlängert werden, indem mit dem Migrationssatz wie folgt verfahren wird:

* Die Beschreibung wird bearbeitet.
* Der Extraktionsschlüssel wird abgerufen.
* Eine Extraktion wird für ihn durchgeführt.
* Es werden Inhalte aus dem Migrationssatz aufgenommen.

Der Ablauf eines Migrationssatzes kann in der Zeile für den Migrationssatz überwacht werden. Ein hilfreicher visueller Hinweis darauf, dass ein Migrationssatz sich seinem Ablaufdatum nähert, ist auch auf der Projektkarte zu sehen.

![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam29.png)


## Wie geht es weiter {#whats-next}

Nun, da Sie sich mit dem Content Transfer Tool und seiner Übersicht, die dieses Tool beschreibt, vertraut gemacht haben, können Sie vorhandene Inhalte von einer Quell-AEM-Instanz (On-Premise oder AMS) in die AEM Cloud Service-Zielinstanz verschieben. Lesen Sie dazu [Voraussetzungen für das Content Transfer Tool](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/prerequisites-content-transfer-tool.md).
