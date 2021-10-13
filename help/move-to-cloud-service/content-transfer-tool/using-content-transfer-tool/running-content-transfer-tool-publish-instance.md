---
title: Ausführen des Content Transfer Tool auf einer Veröffentlichungsinstanz
description: Ausführen des Content Transfer Tool auf einer Veröffentlichungsinstanz
source-git-commit: 5ae76fbc3926f5e2cd7ed5597a9d4521adc9ddb1
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 29%

---


# Ausführen des Content Transfer Tool auf einer Veröffentlichungsinstanz {#run-content-transfer-tool-publish-instance}

## Einführung {#introduction}

Das Content Transfer Tool führt keine Inhaltsanalyse durch, bevor Inhalte von der Quellinstanz zur Zielinstanz übertragen werden. Beispielsweise unterscheidet CTT nicht zwischen veröffentlichten und unveröffentlichten Inhalten, wenn Inhalte in eine Veröffentlichungsumgebung aufgenommen werden. Der im Migrationssatz angegebene Inhalt wird in die ausgewählte Zielinstanz aufgenommen. Der Benutzer kann einen Migrationssatz in eine Autoreninstanz oder eine Veröffentlichungsinstanz oder in beide aufnehmen.

>[!NOTE]
>Es wird empfohlen, beim Verschieben von Inhalten auf eine Produktionsinstanz das Content Transfer Tool auf der Quell-Autoreninstanz zu installieren, um Inhalte in die Ziel-Autoreninstanz zu verschieben, und auf ähnliche Weise das Content Transfer Tool auf der Quell-Veröffentlichungsinstanz zu installieren, um Inhalte in die Ziel-Veröffentlichungsinstanz zu verschieben. Weitere Informationen finden Sie unten im Abschnitt [Empfohlener Ansatz](#recommended-approach) .

## Empfohlener Ansatz {#recommended-approach}

Befolgen Sie den unten beschriebenen empfohlenen Ansatz:

* Verwenden Sie dieselbe CTT-Version, die in der -Autoreninstanz verwendet wurde.

* Es muss nur ein einzelner Veröffentlichungsknoten migriert werden. Sie sollte vor Beginn der Extraktion aus dem Lastenausgleich entfernt werden.

* Verwenden Sie beim Erstellen des Migrationssatzes die URL der Autorenumgebung AEMaaCS.

* Während der Aufnahme zur Veröffentlichung wird die Veröffentlichungsstufe NICHT herunterskaliert (im Gegensatz zum Autor). Vermeiden Sie als Vorsichtsmaßnahme von Benutzern initiierte Schreibvorgänge wie:

   * Inhaltsverteilung von AEM as a Cloud Service Autoren- zur Veröffentlichungsumgebung
   * Benutzersynchronisierung zwischen Veröffentlichungsinstanzen
