---
title: SLA-Berichte
description: Erfahren Sie, wie Sie die Leistung Ihrer Produktionsumgebung im Vergleich zum vertraglich vereinbarten Service Level Agreement (SLA) AEM.
exl-id: 03932415-a029-4703-b44a-f86a87edb328
source-git-commit: bc3c054e781789aa2a2b94f77b0616caec15e2ff
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 9%

---


# SLA-Berichte {#sla-reporting}

Erfahren Sie, wie Sie die Leistung Ihrer Produktionsumgebung im Vergleich zum vertraglich vereinbarten Service Level Agreement (SLA) AEM.

## Einführung {#introduction}

SLA-Berichtsdaten sind für jedes Produktionsprogramm über die **Berichte** Registerkarte. Führen Sie die folgenden Schritte aus, um auf zuzugreifen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie zum **Berichte** Registerkarte aus **Übersicht** Seite.

1. Klicken Sie auf das gewünschte Jahr, um die SLA-Daten grafisch darzustellen.

![Beispiel eines SLA-Diagramms](assets/sla-reporting-1.png)

Bewegen Sie den Cursor über einen Datenpunkt, um die spezifischen Werte für diesen Punkt anzuzeigen.

![Detaillierte Daten anzeigen](assets/sla-reporting-b.png)

## SLA-Metriken {#sla-metrics}

Das Diagramm des ausgewählten Jahres enthält mehrere Datensätze.

* **Veröffentlichen von Tier-Verträgen** - Dies ist der SLA, der in Ihrem Vertrag mit Adobe für die Veröffentlichungsstufe definiert ist.

* **Tatsächliche Veröffentlichungsebene** - Dies ist die gemessene Produktionszeit der Factoring-Vorfälle auf der Produktionsveröffentlichungsstufe, die durch Adobe oder Adobe vendors verursacht wurden.

* **Autoren-Stufenvertrag** - Dies ist der SLA, der in Ihrem Vertrag mit Adobe für die Autorenstufe definiert ist.

* **Autorenebene - realisiert** - Dies ist die gemessene Produktionszeit der Factoring-Vorfälle auf der Produktionsautorenstufe, die durch Adobe oder Adobe vendors verursacht wurden.

## Ereignisanalyse {#event-analysis}

Die **Ereignisanalyse** im Diagramm zeigt die Anzahl der Vorfälle, die im ausgewählten Jahr im Rahmen des Programms aufgetreten sind.

Jeder Vorfall hat einen Zeitraum, eine Ursache und eine Reihe von Kommentaren.

![Beispiel für eine Ereignisanalyse](assets/sla-reporting-c.png)
