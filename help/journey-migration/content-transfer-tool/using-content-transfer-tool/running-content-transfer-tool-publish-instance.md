---
title: Ausführen des Content Transfer Tools in einer Veröffentlichungsinstanz
description: Ausführen des Content Transfer Tools in einer Veröffentlichungsinstanz
exl-id: 01faab94-a939-4004-b094-e9eb8f67b96e
feature: Migration
role: Admin
source-git-commit: 4408f15ef85d0fc2c6a0e2b45038dc900d212187
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 100%

---

# Ausführen des Content Transfer Tools in einer Veröffentlichungsinstanz {#run-content-transfer-tool-publish-instance}

## Einführung {#introduction}

Das Content Transfer Tool führt keine Inhaltsanalyse durch, bevor Inhalte von der Quellinstanz zur Zielinstanz übertragen werden. Beispielsweise unterscheidet CTT nicht zwischen veröffentlichten und unveröffentlichten Inhalten, wenn Inhalte in eine Veröffentlichungsumgebung aufgenommen werden. Alle Inhalte, die im Migrationssatz angegeben sind, werden in die gewählte Zielinstanz aufgenommen. Benutzende können einen Migrationssatz in eine Autoreninstanz oder eine Veröffentlichungsinstanz oder in beide aufnehmen.

>[!NOTE]
>Es wird empfohlen, beim Verschieben von Inhalten in eine Produktionsinstanz das Content Transfer Tool in der Quellautoreninstanz zu installieren, um Inhalte in die Zielautoreninstanz zu verschieben, und das Content Transfer Tool in ähnlicher Weise in der Quell-Veröffentlichungsinstanz zu installieren, um Inhalte in die Ziel-Veröffentlichungsinstanz zu verschieben. Weitere Einzelheiten finden Sie im Abschnitt [Empfohlener Ansatz](#recommended-approach) weiter unten.

## Empfohlener Ansatz {#recommended-approach}

Befolgen Sie den unten beschriebenen empfohlenen Ansatz:

* Verwenden Sie dieselbe Version des Content Transfer Tools, die in der Autoreninstanz verwendet wurde.

* Es muss nur ein einzelner Veröffentlichungsknoten migriert werden. Er sollte vor Beginn der Extraktion aus dem Lastenausgleich entfernt werden.

* Während der Aufnahme zur Veröffentlichung wird die Veröffentlichungsebene nicht herunterskaliert (im Gegensatz zur Autorenebene).

  >[!IMPORTANT]
  >Vermeiden Sie vorsichtshalber alle benutzerseitig initiierten Schreibvorgänge, z. B.:
  > * Inhaltsverteilung von der AEM as a Cloud Service-Autoren- zur Veröffentlichungsumgebung
  > * Benutzersynchronisierung zwischen Veröffentlichungsinstanzen
