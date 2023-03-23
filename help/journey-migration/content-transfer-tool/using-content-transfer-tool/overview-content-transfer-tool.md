---
title: Übersicht über das Content Transfer-Tool
description: Übersicht über das Content Transfer Tool
exl-id: cfc0366a-2139-4d9d-b5bc-0b65bef4013c
source-git-commit: ac35bbe5ad78e07cc5292e089f3d71c6a8ed6ccc
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 79%

---

# Übersicht {#overview-content-transfer-tool}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_overview"
>title="Übersicht"
>abstract="Das Content Transfer Tool ist ein von Adobe entwickeltes Tool, mit dem Sie vorhandene Inhalte von einer AEM-Quellinstanz (On-Premise oder AMS) in die Zielinstanz in AEM Cloud Service verschieben können. Dieses Tool überträgt auch Prinzipale (Benutzer oder Gruppen) automatisch."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=de" text="Richtlinien und Best Practices"

Das Content Transfer Tool ist ein von Adobe entwickeltes Tool, mit dem Sie vorhandene Inhalte von einer AEM-Quellinstanz (On-Premise oder AMS) in die Zielinstanz in AEM Cloud Service verschieben können.

Dieses Tool überträgt auch Prinzipale (Benutzer oder Gruppen) automatisch.

Es ist eine neue Version des Content Transfer Tool verfügbar, die den Inhaltstransferprozess mit Cloud Acceleration Manager integriert. Es wird dringend empfohlen, zu dieser neuen Version zu wechseln, um alle Vorteile nutzen zu können, die sie bietet:

* Self-Service-Methode zur einmaligen Extraktion eines Migrationssatzes und zur gleichzeitigen Aufnahme in mehrere Umgebungen
* Verbessertes Benutzererlebnis durch bessere Ladezustände, Limits und Fehlerbehandlung
* Aufnahmeprotokolle bleiben erhalten und stehen immer zur Fehlerbehebung zur Verfügung.

Um die neue Version verwenden zu können, müssen Sie ältere Versionen des Inhaltsübertragungs-Tools deinstallieren, da es eine größere Änderung in der Architektur des Tools gab.

>[!NOTE]
>
> In Situationen, in denen bereits eine Migration in Bearbeitung ist, können Sie die vorherige CTT-Version weiter verwenden, bis die Migration abgeschlossen ist. Die Dokumentation für die Vorgängerversion des CTT finden Sie in der [Dokumentation zu den Vorgängerversionen](/help/journey-migration/content-transfer-tool/ctt-legacy/overview-content-transfer-tool-legacy.md).

## Phasen im Content Transfer Tool {#phases-content-transfer-tool}

Beim Inhaltstransfer gibt es zwei Phasen:

1. **Extraktion**: Extraktion bezieht sich auf das Extrahieren von Inhalten aus der AEM-Quellinstanz in einen temporären Bereich, der als *Migrationssatz* bezeichnet wird. Ein *Migrationssatz* ist ein Cloud-Speicherplatzbereich, der von Adobe bereitgestellt wird, um die übertragenen Inhalte vorübergehend zwischen der AEM-Quellinstanz und der Cloud Service-AEM-Instanz zu speichern.

   Weitere Informationen finden Sie unter [Extraktionsvorgang beim Inhaltstransfer](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md).

   >[!NOTE]
   >Die Benutzerzuordnung wird jetzt automatisch im Rahmen der Extraktionsphase beim Autor ausgeführt (kann aber optional beim Autor deaktiviert oder bei der Veröffentlichung aktiviert werden). Siehe [Benutzerzuordnung und Hauptmigration](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/user-mapping-and-migration.md) für weitere Details.

1. **Aufnahme**: Aufnahme bezieht sich auf die Aufnahme von Inhalten aus dem *Migrationssatz* in die Cloud Service-Zielinstanz.

   Weitere Informationen finden Sie unter [Aufnahmevorgang beim Inhaltstransfer](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md).

## Attribute eines Migrationssatzes {#attributes-migration-set}

Ein Migrationssatz hat die folgenden Attribute:

* Mit der neuen Version können Sie maximal fünf Migrationssätze in einem Projekt erstellen, das in Cloud Acceleration Manager erstellt wurde.
* Jeder Migrationssatz sollte einen eindeutigen Namen haben.

Das Content Transfer Tool verfügt über eine Funktion, die die differenzielle Auffüllung von Inhalten unterstützt, wobei es möglich ist, nur Änderungen zu übertragen, die seit dem vorherigen Inhaltstransfer vorgenommen wurden.

>[!NOTE]
>Nach dem ersten Transfer von Inhalten wird empfohlen, häufige differenzielle Auffüllungen des Inhalts durchzuführen, um den Zeitraum für das Einfrieren des Inhalts für den endgültigen differenziellen Inhaltstransfer zu verkürzen, bevor er in Cloud Service live geschaltet wird.

In der Extraktionsphase muss die Option ***Überschreiben*** deaktiviert werden, um einen vorhandenen Migrationssatz *aufzufüllen*. Weitere Informationen finden Sie unter [Auffüllextraktion](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process).

In der Aufnahmephase muss die *Löschoption* deaktiviert werden, damit der Delta-Inhalt zusätzlich zum aktuellen Inhalt angewendet wird. Weitere Informationen finden Sie unter [Auffüllaufnahme](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process).

## Ablauf des Migrationssatzes {#migration-set-expiry}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_migrationset_expiry"
>title="Gültigkeit eines Migrationssatzes"
>abstract="Erfahren Sie mehr über den Ablauf der Gültigkeit eines Migrationssatzes."

Alle Migrationssätze laufen nach einer verlängerten Inaktivitätsdauer von etwa 90 Tagen ab. Nachdem Indikatoren auf der Projektkarte und den Tabellenzeilen für den Migrationsauftrag für einen bestimmten Zeitraum angezeigt wurden, läuft der Migrationssatz ab und die zugehörigen Daten sind nicht mehr verfügbar. Die Verfallszeit kann einfach verlängert werden, indem auf die eingestellte Migration reagiert wird:

* Bearbeiten der Beschreibung
* Extraktionsschlüssel abrufen
* Durchführung einer Extraktion
* Durchführen einer Aufnahme daraus

Der Ablauf eines Migrationssatzes kann in der Zeile Migrationssatz überwacht werden. Ein hilfreicher visueller Hinweis darauf, dass ein Migrationssatz sich seinem Ablaufdatum nähert, wurde auch die Karte des Projekts hinzugefügt.

![image](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam29.png)


## Wie geht es weiter {#whats-next}

Nun, da Sie sich mit dem Content Transfer Tool und seiner Übersicht, die dieses Tool beschreibt, vertraut gemacht haben, können Sie vorhandene Inhalte von einer Quell-AEM-Instanz (On-Premise oder AMS) in die AEM Cloud Service-Zielinstanz verschieben. Lesen Sie dazu [Voraussetzungen für das Content Transfer Tool](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/prerequisites-content-transfer-tool.md).
