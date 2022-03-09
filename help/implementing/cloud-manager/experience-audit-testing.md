---
title: Testen mit Experience Audit
description: Erfahren Sie, wie Experience Audit Ihren Implementierungsprozess validiert und sicherstellt, dass die bereitgestellten Änderungen den Grundstandards für Leistung, Barrierefreiheit, Best Practices und SEO entsprechen.
exl-id: 8d31bc9c-d38d-4d5b-b2ae-b758e02b7073
source-git-commit: 15de47e28e804fd84434d5e8e5d2fe8fe6797241
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 26%

---


# Testen mit Experience Audit {#experience-audit-testing}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_expaudittesting"
>title="Testen mit Experience Audit"
>abstract="Erfahren Sie, wie Experience Audit Ihren Implementierungsprozess validiert und sicherstellt, dass die bereitgestellten Änderungen den Grundstandards für Leistung, Barrierefreiheit, Best Practices und SEO entsprechen."

Erfahren Sie, wie Experience Audit Ihren Implementierungsprozess validiert und sicherstellt, dass die bereitgestellten Änderungen den Grundstandards für Leistung, Barrierefreiheit, Best Practices und SEO entsprechen.

## Übersicht {#overview}

Experience Audit ist eine Funktion, die in Cloud Manager Sites-Produktions-Pipelines verfügbar ist und den Implementierungsprozess validiert und dabei hilft, sicherzustellen, dass Änderungen bereitgestellt werden:

1. Erfüllen Sie Grundanforderungen an Leistung, Barrierefreiheit, Best Practices, SEO (Suchmaschinenoptimierung) und PWA (Progressive Web App).

1. Keine Regressionen einführen.

Experience Audit in Cloud Manager stellt sicher, dass das Erlebnis des Endbenutzers auf der Site höchsten Standards entspricht.

Die Prüfergebnisse sind informativ und ermöglichen es dem Implementierungsmanager, die Bewertungen und die Änderung zwischen den aktuellen und vorherigen Bewertungen zu sehen. Diese Erkenntnis ist nützlich, um festzustellen, ob es eine Regression gibt, die mit der aktuellen Implementierung eingeführt wird.

Experience Audit wird von Google Lighthouse unterstützt, einem Open-Source-Tool von Google, und ist in allen Cloud Manager-Produktions-Pipelines aktiviert.

## Verstehen der Ergebnisse von Experience Audit {#understanding-experience-audit-results}

Experience Audit bietet aggregierte und detaillierte Testergebnisse auf Seitenebene über die [Ausführungsseite der Produktions-Pipeline.](/help/implementing/cloud-manager/deploy-code.md)

* Aggregate Metriken messen die durchschnittlichen Werte auf den Seiten, die auf Leistung, Barrierefreiheit, Best Practices, SEO (Suchmaschinenoptimierung) hin geprüft wurden.
* Die Werte auf der Ebene einzelner Seiten sind auch per Drilldown verfügbar.
* Details zu den Werten sind verfügbar, um die Ergebnisse der einzelnen Tests sowie Anleitungen zur Behebung der identifizierten Probleme anzuzeigen.
* Ein Verlauf der Testergebnisse wird in Cloud Manager persistiert, um zu bestimmen, ob Änderungen, die in die Pipeline eingeführt werden, Regressionen aus der vorherigen Ausführung enthalten.

### Aggregierte Werte {#aggregate-scores}

Der aggregierte Wert entspricht dem Durchschnittswert der Seiten, die in der Ausführung enthalten sind. Die Änderung auf der Aggregatebene stellt den Durchschnittswert der Seiten in der aktuellen Ausführung im Vergleich zum Durchschnittswert der Ergebnisse aus der vorherigen Ausführung dar, selbst wenn die Sammlung der Seiten, die für die Aufnahme konfiguriert wurden, zwischen den Ausführungen geändert wurde.

Für jeden Testtyp wie Leistung, Barrierefreiheit, SEO und Best Practices gibt es einen aggregierten Wert.

Die Änderungsmetrik kann einen der folgenden Werte aufweisen.

* **Positiver Wert** - Die Seiten wurden seit der letzten Ausführung der Produktions-Pipeline beim ausgewählten Test verbessert.

* **Negativer Wert** - die Seite(n) seit der letzten Ausführung der Produktions-Pipeline beim ausgewählten Test regressiert wurde/sind.

* **Keine Änderung** - Die Seiten wurden seit der letzten Ausführung der Produktions-Pipeline gleich bewertet.

* **Nicht zutreffend** - Es war kein vorheriges Ergebnis zum Vergleich verfügbar.

![Experience Audit-Ergebnisse](/help/implementing/cloud-manager/assets/exp-audit-1.png)


### Werte auf Seitenebene {#page-level-scores}

Durch die Untersuchung eines beliebigen Tests ist eine detailliertere Bewertung auf Seitenebene verfügbar. Sie können sehen, wie die einzelnen Seiten für den jeweiligen Test bewertet wurden, zusammen mit der Änderung aus dem vorherigen Testlauf.

Wenn Sie auf die Details einzelner Seiten klicken, erhalten Sie Informationen zu den bewerteten Elementen der Seite sowie Hinweise zur Problembehebung, falls Verbesserungsmöglichkeiten erkannt werden.

![Werte auf Seitenebene](/help/implementing/cloud-manager/assets/exp-audit-2.png)
