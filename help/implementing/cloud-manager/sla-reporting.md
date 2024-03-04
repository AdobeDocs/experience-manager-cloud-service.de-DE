---
title: SLA-Berichte
description: Erfahren Sie, wie Sie die Leistungsdaten einer AEM-Produktionsumgebung mit dem vertraglich vereinbarten Service Level Agreement (SLA) vergleichen können.
exl-id: 03932415-a029-4703-b44a-f86a87edb328
source-git-commit: f037f47f0b131c87301faf4458658224d1d62a43
workflow-type: ht
source-wordcount: '400'
ht-degree: 100%

---


# SLA-Berichte {#sla-reporting}

Erfahren Sie, wie Sie die Leistungsdaten einer AEM-Produktionsumgebung mit dem vertraglich vereinbarten Service Level Agreement (SLA) vergleichen können.

## Einführung {#introduction}

SLA-Berichtsdaten sind für jedes Produktionsprogramm über die Registerkarte **Berichte** verfügbar. Führen Sie die folgenden Schritte aus, um darauf zuzugreifen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Wählen Sie im Bildschirm **[Eigene Programme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md#my-programs)** das Programm aus.

1. Navigieren Sie von der Seite **Überblick** zur Karte **Umgebungen**.

1. Klicken Sie auf das gewünschte Jahr, um die SLA-Daten grafisch darzustellen.

![Beispiel für ein SLA-Diagramm](assets/sla-reporting-1.png)

Bewegen Sie den Cursor über einen Datenpunkt, um die spezifischen Werte für diesen Punkt anzuzeigen.

![Anzeigen von detaillierten Daten](assets/sla-reporting-b.png)

## SLA-Metriken {#sla-metrics}

Das Diagramm des ausgewählten Jahres enthält mehrere Datensätze.

* **Veröffentlichungsebene – Vertrag**: Dies ist das SLA, das in Ihrem Vertrag mit Adobe für die Veröffentlichungsebene definiert ist.

* **Veröffentlichungsebene – Tatsächlich**: Dies ist die gemessene Produktionszeit im Hinblick auf Factoring-Vorfälle in der Produktions-Veröffentlichungsebene, die von Adobe oder unseren Anbietern verursacht wurden.

* **Autorenebene – Vertrag**: Dies ist das SLA, das in Ihrem Vertrag mit Adobe für die Autorenebene definiert ist.

* **Autorenebene – Tatsächlich**: Dies ist die gemessene Produktionszeit im Hinblick auf Factoring-Vorfälle in der Produktions-Autorenebene, die von Adobe oder dessen Anbietern verursacht wurden.

## Ereignisanalyse {#event-analysis}

Der Abschnitt **Ereignisanalyse** unter diesem Diagramm zeigt die Anzahl von Vorfällen, die im aktuell ausgewählten Jahr beim Programm aufgetreten sind.

Für jeden Vorfall werden Zeitraum und Ursache mitsamt Kommentaren angegeben.

![Beispiel für eine Ereignisanalyse](assets/sla-reporting-c.png)

## Aktualisierungsintervall {#refresh}

Die SLA-Berichterstattung gibt Ihnen einen Einblick in die Leistung Ihrer AEM-Produktionsumgebung und ist aktuell, aber nicht sofort verfügbar. Die Erstellung von SLA-Berichten erfolgt monatlich und wird für neue Programme generiert, die als „Produktion im Vormonat“ gekennzeichnet sind. Die Berichterstellung erfolgt nicht sofort. Beachten Sie aufgrund dieser Verzögerung bei der Überprüfung Ihres SLA-Berichts Folgendes:

* Das SLA, zu dem der Bericht erstellt wird, ist dasjenige, das zu Beginn des Monats bestand, auch wenn sich das SLA im Laufe des Monats geändert hat.
* Wenn zu Beginn des Monats kein SLA existierte, weil das Programm nicht existierte, gilt das SLA, das zum Zeitpunkt der Erstellung des Programms existierte.

## Vorschau-Umgebungen {#preview}

Die Vorschau-Umgebung ist als Tool für Autorinnen und Autoren von Inhalten gedacht, um das endgültige Erlebnis des Inhalts vor der Veröffentlichung zu überprüfen. Aus diesem Grund sind Vorschau-Umgebungen nicht mit hoher Verfügbarkeit konzipiert und verfügen nicht über ein zugehöriges SLA.
