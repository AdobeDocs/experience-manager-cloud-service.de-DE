---
title: Bausteine für WYSIWYG-Authoring und dokumentbasiertes Authoring
description: Erfahren Sie, wie Sie Bausteine erstellen können, die sowohl für das WYSIWYG-Authoring als auch für das dokumentbasierte Authoring verwendet werden können.
feature: Edge Delivery Services
role: User
source-git-commit: 3419fa943eb865d87467443527ea97fcd64909c2
workflow-type: ht
source-wordcount: '235'
ht-degree: 100%

---


# Bausteine für WYSIWYG-Authoring und dokumentbasiertes Authoring {#wysiwyg-and-doc-blocks}

Erfahren Sie, wie Sie Bausteine erstellen können, die sowohl für das WYSIWYG-Authoring als auch für das dokumentbasierte Authoring verwendet werden können.

## Überblick {#overview}

Bei bestimmten Projekten möchten Sie möglicherweise sowohl das [WYSIWYG-Authoring mit dem universellen Editor](/help/edge/wysiwyg-authoring/authoring.md) als auch das [dokumentbasierte Authoring unterstützen.](/help/edge/docs/authoring.md) Um die Entwicklungszeit zu minimieren und dasselbe Site-Erlebnis sicherzustellen, können Sie einen Satz von Bausteinen erstellen, um beide Anwendungsfälle zu unterstützen.

Dazu müssen Sie sowohl für Ihre WYSIWYG-Authoring-Einrichtung als auch für Ihre dokumentbasierte Authoring-Einrichtung denselben Inhaltsmodellierungsansatz verwenden.

## Ansatz {#approach}

Im WYSIWYG-Authoring in AEM [deklarieren Sie ein Modell](/help/edge/wysiwyg-authoring/content-modeling.md) und geben Namenskonventionen an. Die Daten werden dann mit Edge Delivery in tabellenähnlichen Bausteinstrukturen auf die gleiche Weise gerendert wie bei der manuellen Erstellung der Tabelle mithilfe des dokumentbasierten Authoring.

Um dies zu erreichen, werden bestimmte Annahmen getroffen, zum Beispiel, dass für einen einfachen Baustein wie einen Teaser alle Eigenschaften und Gruppen von Eigenschaften in 1..n Zeilen mit jeweils einer Spalte gerendert werden. Bei Bausteinen mit 1..n Elementen (wie Karussell und Karten) werden die Elemente nach diesen Zeilen jeweils mit einer Zeile und einer Spalte für jede Eigenschaft/Gruppe von Eigenschaften angehängt.

Wenn Sie beim dokumentbasierten Authoring denselben Ansatz verfolgen, können Sie Ihre WYSIWYG-Bausteine wiederverwenden.
