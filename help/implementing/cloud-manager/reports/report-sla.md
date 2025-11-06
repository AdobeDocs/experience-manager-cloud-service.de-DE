---
title: SLA-Berichte
description: Erfahren Sie, wie Sie die Leistungsdaten einer AEM-Produktionsumgebung mit dem vertraglich vereinbarten Service Level Agreement vergleichen können.
exl-id: 03932415-a029-4703-b44a-f86a87edb328
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 89%

---


# SLA-Berichte {#sla-reporting}

Erfahren Sie, wie Sie die Leistungsdaten Ihrer AEM-Produktionsumgebung mit dem vertraglich vereinbarten SLA (Service Level Agreement) vergleichen können.

## Anzeigen eines SLA-Berichts {#introduction}

SLA-Berichtsdaten verfolgen Leistungsmetriken für zwei Produktionsstufen: Autorenebene und Veröffentlichungsebene.

Das Liniendiagramm eines ausgewählten Jahres enthält Datenpunkte für jeden Monat von Januar bis Dezember. Die folgenden Metriken werden verfolgt.

| Verfolgte Metrik | Linienfarbe | Beschreibung |
| --- | --- | --- |
| Autorenebene aktuell | Hellgrün | Die gemessene Verfügbarkeit der produktionsbezogenen Erstellungsebene unter Berücksichtigung der von Adobe oder unseren Anbietern verursachten Vorfälle. |
| Autorenebene Vertrag | Dunkelblau | Das SLA, das in Ihrem Vertrag mit Adobe für die Erstellungsebene definiert ist. |
| Veröffentlichungsebene antuell | Orangefarben | Die gemessene Betriebszeit der Produktions-Veröffentlichungsebene, Factoring-Vorfälle, die von Adobe oder den Anbietern von Adobe verursacht wurden. |
| Veröffentlichungsebene Vertrag | Rot | Die SLA, die in Ihrem Vertrag mit Adobe für die Veröffentlichungsebene definiert ist. |

**So zeigen Sie einen SLA-Bericht an:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus.

1. Klicken Sie auf der Seite **Programmübersicht** im linken Menü auf **Berichte**.

1. Klicken Sie auf **SLA-Berichte**.

   ![Liniendiagramm des SLA-Berichts](/help/implementing/cloud-manager/reports/assets/cm-sla-report2.png)

1. Klicken Sie auf das gewünschte Jahr, um ein Liniendiagramm der SLA-Daten anzuzeigen.

1. (Optional) Führen Sie einen der folgenden Schritte aus:

   * Bewegen Sie den Cursor über einen Datenpunkt im Liniendiagramm, um die spezifischen Werte für diesen Punkt anzuzeigen.
   * Klicken Sie unter dem Jahr des Liniendiagramms auf das Symbol **Herunterladen**, um eine PNG-Bilddatei des Liniendiagramms zu speichern.
   * Klicken Sie auf den Namen einer Metrik, um nur die Daten dieser Metrik anzuzeigen. Oder drücken Sie auf der Tastatur auf `Shift`, während Sie einen oder mehrere Metriknamen auswählen oder die Auswahl für Metriknamen aufheben.

## Ereignisanalyse {#event-analysis}

Der Abschnitt **Ereignisanalyse** unter diesem Diagramm zeigt die Anzahl von Vorfällen, die im ausgewählten Jahr beim Programm aufgetreten sind.

Für jeden Vorfall werden Zeitraum und Ursache mitsamt Kommentaren angegeben.

![Beispiel für eine Ereignisanalyse](/help/implementing/cloud-manager/reports/assets/sla-reporting-c.png)

## Aktualisierungsintervall von SLA-Berichten {#refresh}

Die SLA-Berichterstellung gibt Ihnen einen Einblick in die Leistung Ihrer AEM-Produktionsumgebung und ist aktuell, aber nicht sofort verfügbar. Die Erstellung von SLA-Berichten erfolgt monatlich und wird für neue Programme generiert, die als `Production previous month` gekennzeichnet sind. Die Berichterstellung erfolgt nicht sofort. Beachten Sie aufgrund dieser Verzögerung bei der Überprüfung Ihres SLA-Berichts Folgendes:

* Das SLA, zu dem der Bericht erstellt wird, ist dasjenige, das zu Beginn des Monats bestand, auch wenn sich das SLA im Laufe des Monats geändert hat.
* Wenn es zu Beginn des Monats kein SLA gab, weil das Programm nicht existierte, gilt das SLA, das zum Zeitpunkt der Erstellung des Programms existierte.

## Vorschau-Umgebungen {#preview}

Die Vorschau-Umgebung ist als Tool für Autorinnen und Autoren von Inhalten gedacht, um das endgültige Erlebnis des Inhalts vor der Veröffentlichung zu überprüfen. Aufgrund dieser Funktionalität sind Vorschau-Umgebungen nicht mit hoher Verfügbarkeit konzipiert und verfügen nicht über ein zugehöriges SLA.

