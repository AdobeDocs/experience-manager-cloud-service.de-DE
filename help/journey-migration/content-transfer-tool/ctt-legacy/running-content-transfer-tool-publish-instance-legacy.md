---
title: Ausführen des Content Transfer Tool auf einer Veröffentlichungsinstanz (veraltet)
description: Ausführen des Content Transfer Tools in einer Veröffentlichungsinstanz
hide: true
hidefromtoc: true
source-git-commit: 1fb4d0f2a3b3f9a27f5ab1228ec2d419149e0764
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 96%

---

# Ausführen des Content Transfer Tools in einer Veröffentlichungsinstanz (Veraltet) {#run-content-transfer-tool-publish-instance}

## Einführung {#introduction}

Das Content Transfer Tool führt keine Inhaltsanalyse durch, bevor Inhalte von der Quellinstanz zur Zielinstanz übertragen werden. Beispielsweise unterscheidet CTT nicht zwischen veröffentlichten und unveröffentlichten Inhalten, wenn Inhalte in eine Veröffentlichungsumgebung aufgenommen werden. Der im Migrationssatz angegebene Inhalt wird in die ausgewählte Zielinstanz aufgenommen. Der Benutzer kann einen Migrationssatz in eine Autoreninstanz oder eine Veröffentlichungsinstanz oder in beide aufnehmen.

>[!NOTE]
>Es wird empfohlen, beim Verschieben von Inhalten in eine Produktionsinstanz das Content Transfer Tool in der Quellautoreninstanz zu installieren, um Inhalte in die Zielautoreninstanz zu verschieben, und das Content Transfer Tool in ähnlicher Weise in der Quell-Veröffentlichungsinstanz zu installieren, um Inhalte in die Ziel-Veröffentlichungsinstanz zu verschieben. Weitere Einzelheiten finden Sie im Abschnitt [Empfohlener Ansatz](#recommended-approach) weiter unten.

## Empfohlener Ansatz {#recommended-approach}

Befolgen Sie den unten beschriebenen empfohlenen Ansatz:

* Verwenden Sie dieselbe Version des Content Transfer Tools, die in der Autoreninstanz verwendet wurde.

* Es muss nur ein einzelner Veröffentlichungsknoten migriert werden. Er sollte vor Beginn der Extraktion aus dem Lastenausgleich entfernt werden.

* Verwenden Sie beim Erstellen des Migrationssatzes die URL der Autoren-AEM as a Cloud Service-Umgebung.

* Während der Aufnahme zur Veröffentlichung wird die Veröffentlichungsebene nicht herunterskaliert (im Gegensatz zur Autorenebene).

   >[!IMPORTANT]
   >Vermeiden Sie vorsichtshalber alle vom Benutzer initiierten Schreibvorgänge, wie z. B.:
   > * Inhaltsverteilung von der AEM as a Cloud Service-Autoren- zur Veröffentlichungsumgebung
   > * Benutzersynchronisierung zwischen Veröffentlichungsinstanzen

