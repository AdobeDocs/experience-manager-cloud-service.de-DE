---
title: Ausführen des Content Transfer Tool auf einer Veröffentlichungsinstanz
description: Ausführen des Content Transfer Tool auf einer Veröffentlichungsinstanz
source-git-commit: 27e68cd282414da4cc23c3ba276b0fb3c330d49c
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 42%

---


# Ausführen des Content Transfer Tool auf einer Veröffentlichungsinstanz {#run-content-transfer-tool-publish-instance}

## Einführung {#introduction}

Das Content Transfer Tool führt keine Inhaltsanalyse durch, bevor Inhalte von der Quellinstanz zur Zielinstanz übertragen werden. Beispielsweise unterscheidet CTT nicht zwischen veröffentlichten und unveröffentlichten Inhalten, wenn Inhalte in eine Veröffentlichungsumgebung aufgenommen werden. Der im Migrationssatz angegebene Inhalt wird in die ausgewählte Zielinstanz aufgenommen. Der Benutzer kann einen Migrationssatz in eine Autoreninstanz oder eine Veröffentlichungsinstanz oder in beide aufnehmen. Es wird empfohlen, beim Verschieben von Inhalten in eine Produktionsinstanz CTT in der Quellautoreninstanz zu installieren, um Inhalte in die Zielautoreninstanz zu verschieben, und CTT in ähnlicher Weise in der Quell-Veröffentlichungsinstanz zu installieren, um Inhalte in die Ziel-Veröffentlichungsinstanz zu verschieben.

>[!NOTE]
>Es wird empfohlen, beim Verschieben von Inhalten auf eine Veröffentlichungsinstanz das Tool Inhaltstransfer auf der Veröffentlichungsinstanz der Quelle zu installieren, um Inhalte in die Veröffentlichungsinstanz der Zielgruppe zu verschieben. Weitere Informationen finden Sie unten im Abschnitt [Empfohlener Ansatz](#recommended-approach) .

## Empfohlener Ansatz {#recommended-approach}

Befolgen Sie den unten beschriebenen empfohlenen Ansatz:

* Verwenden Sie dieselbe CTT-Version, die in der -Autoreninstanz verwendet wurde.

* Es muss nur ein einzelner Veröffentlichungsknoten migriert werden. Sie sollte vor Beginn der Extraktion aus dem Lastenausgleich entfernt werden.

* Verwenden Sie beim Erstellen des Migrationssatzes die URL der Autorenumgebung AEMaaCS.

* Während der Aufnahme zur Veröffentlichung wird die Veröffentlichungsstufe NICHT herunterskaliert (im Gegensatz zum Autor). Vermeiden Sie als Vorsichtsmaßnahme von Benutzern initiierte Schreibvorgänge wie:

   * Inhaltsverteilung von AEM as a Cloud Service Autoren- zur Veröffentlichungsumgebung
   * Benutzersynchronisierung zwischen Veröffentlichungsinstanzen
