---
title: SLA-Berichte
description: Erfahren Sie, wie Sie die Leistung Ihrer Produktionsumgebung AEM der vertraglich vereinbarten Service Level Agreement anzeigen können.
exl-id: 03932415-a029-4703-b44a-f86a87edb328
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: c46b6df488722fe750e524ad2bb383f25bf00b0f
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 23%

---


# SLA-Berichte {#sla-reporting}

Erfahren Sie, wie Sie die Leistung Ihrer Produktionsumgebung AEM der vertraglich vereinbarten SLA (Service Level Agreement) anzeigen können.

## Anzeigen eines SLA-Berichts {#introduction}

SLA-Berichtsdaten verfolgen Leistungsmetriken für zwei Produktionsstufen: Autorenebene und Publish-Ebene.

Das Liniendiagramm eines ausgewählten Jahres enthält Datenpunkte für jeden Monat von Januar bis Dezember. Die folgenden Metriken werden verfolgt.

| Verfolgte Metrik | Linienfarbe | Beschreibung |
| --- | --- | --- |
| Erstellungsebene Ist | Hellgrün | Die gemessene Betriebszeit der Factoring-Vorfälle auf der Produktionsautoren-Ebene, die durch Adobe oder Adobe vendors verursacht wurden. |
| Erstellungsebene Soll | Dunkelblau | Die in Ihrem Vertrag mit Adobe definierte SLA für die Autorenebene. |
| Veröffentlichungsebene Ist | Orangefarben | Die gemessene Produktionszeit der Publish-Produktionsstufe, Factoring-Vorfälle durch Adobe oder Adobe vendors. |
| Veröffentlichungsebene Soll | Rot | Die in Ihrem Vertrag mit Adobe definierte SLA für die Publish-Ebene. |

**Anzeigen eines SLA-Berichts:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus.

1. Klicken Sie auf der Seite **Programmübersicht** im linken Navigationsbereich auf **Berichte**.

1. Klicken Sie auf **SLA-Berichte**.

   ![SLA-Berichtszeilendiagramm](/help/implementing/cloud-manager/assets/cm-sla-report.png)

1. Klicken Sie auf das gewünschte Jahr, um ein Liniendiagramm der SLA-Daten anzuzeigen.

1. (Optional) Führen Sie einen der folgenden Schritte aus:

   * Bewegen Sie den Cursor über einen Datenpunkt im Liniendiagramm, um die spezifischen Werte für diesen Punkt anzuzeigen.
   * Klicken Sie unter dem Jahr des Liniendiagramms auf das Symbol Herunterladen , um eine PNG-Bilddatei des Liniendiagramms zu speichern.
   * Klicken Sie auf einen Metriknamen, um nur die Daten dieser Metrik anzuzeigen. Oder drücken Sie auf der Tastatur `Shift` , während Sie einen oder mehrere Metriknamen auswählen oder deaktivieren.

   ![Anzeigen von detaillierten Daten](/help/implementing/cloud-manager/assets/cm-sla-download.png)

## Ereignisanalyse {#event-analysis}

Der Abschnitt **Ereignisanalyse** unter dem Diagramm zeigt die Anzahl der Vorfälle, die im ausgewählten Jahr für das Programm aufgetreten sind.

Für jeden Vorfall werden Zeitraum und Ursache mitsamt Kommentaren angegeben.

![Beispiel für eine Ereignisanalyse](assets/sla-reporting-c.png)

## Aktualisierungsintervall von SLA-Berichten {#refresh}

Die SLA-Berichterstattung gibt Ihnen einen Einblick in die Leistung Ihrer AEM-Produktionsumgebung und ist aktuell, aber nicht sofort verfügbar. Die Erstellung von SLA-Berichten erfolgt monatlich und wird für neue Programme generiert, die als `Production previous month` gekennzeichnet sind. Die Berichterstellung erfolgt nicht sofort. Beachten Sie daher bei der Überprüfung Ihres SLA-Berichts Folgendes:

* Die gemeldete SLA ist die , die zu Monatsbeginn existierte, selbst wenn sich SLA in diesem Monat änderte.
* Wenn zu Monatsbeginn keine SLA vorhanden war, da das Programm nicht existierte, gilt die zum Zeitpunkt der Programmerstellung bestehende SLA.

## Vorschau von Umgebungen {#preview}

Die Vorschau-Umgebung ist als Tool für Autorinnen und Autoren von Inhalten gedacht, um das endgültige Erlebnis des Inhalts vor der Veröffentlichung zu überprüfen. Aufgrund dieser Funktionalität sind Vorschauumgebungen nicht mit hoher Verfügbarkeit konzipiert und verfügen nicht über eine zugehörige SLA.
