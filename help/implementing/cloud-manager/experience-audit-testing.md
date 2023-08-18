---
title: Testen mit Experience Audit
description: Erfahren Sie, wie Experience Audit Ihren Implementierungsprozess validiert und sicherstellt, dass die bereitgestellten Änderungen den Grundstandards für Leistung, Barrierefreiheit, Best Practices und SEO entsprechen.
exl-id: 8d31bc9c-d38d-4d5b-b2ae-b758e02b7073
source-git-commit: 9f305e1127957fdba6dae978da4ac5fce4d3a776
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 82%

---


# Testen mit Experience Audit {#experience-audit-testing}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_expaudittesting"
>title="Testen mit Experience Audit"
>abstract="Erfahren Sie, wie Experience Audit Ihren Implementierungsprozess validiert und sicherstellt, dass die bereitgestellten Änderungen den Grundstandards für Leistung, Barrierefreiheit, Best Practices und SEO entsprechen."

Erfahren Sie, wie Experience Audit Ihren Implementierungsprozess validiert und sicherstellt, dass die bereitgestellten Änderungen den Grundstandards für Leistung, Barrierefreiheit, Best Practices und SEO entsprechen.

## Übersicht {#overview}

Experience Audit ist eine Funktion, die in Cloud Manager Sites-Produktions-Pipelines verfügbar ist und den Implementierungsprozess validiert sowie dabei hilft, sicherzustellen, dass Änderungen bereitgestellt werden:

1. Erfüllen Sie Grundanforderungen an Leistung, Barrierefreiheit, Best Practices, SEO (Suchmaschinenoptimierung) und PWA (Progressive Web App).

1. Führen Sie keine Regressionen ein.

Experience Audit in Cloud Manager stellt sicher, dass das Erlebnis der Endbenutzenden auf der Site höchsten Standards entspricht.

Die Ergebnisse des Audits sind rein informativ und ermöglichen es dem Bereitstellungs-Manager, die Bewertungen sowie die Unterschiede zwischen aktuellen und vorherigen Bewertungen anzuzeigen. Diese Einblicke sind nützlich, um festzustellen, ob es eine Regression gibt, die mit der aktuellen Implementierung eingeführt wurde.

Experience Audit basiert auf Google Lighthouse, einem Open-Source-Tool von Google, und ist in allen Cloud Manager-Produktions-Pipelines aktiviert.

>[!INFO]
>
>Mit Wirkung vom 31. August 2023 wechselt Experience Audit zur Anzeige der Ergebnisse, die für die mobile Plattform spezifisch sind. Beachten Sie, dass die Leistungsmetriken für Mobilgeräte in der Regel niedriger sind als die für Desktop. Daher sollten Sie nach dieser Änderung eine Verschiebung der gemeldeten Leistung erwarten.

>[!TIP]
>
>Sie konfigurieren, welche Seiten bei der Erlebnisprüfung einbezogen werden sollen [Einrichten der Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#full-stack-code).

## Verstehen der Ergebnisse von Experience Audit {#understanding-experience-audit-results}

Experience Audit bietet aggregierte und detaillierte Testergebnisse auf Seitenebene über die [Ausführungsseite der Produktions-Pipeline](/help/implementing/cloud-manager/deploy-code.md).

* Aggregierte Metriken messen den durchschnittlichen Wert für alle Seiten, die auf Leistung, Barrierefreiheit, Best Practices und SEO (Suchmaschinenoptimierung) hin geprüft wurden.
* Die Werte auf der Ebene einzelner Seiten sind auch per Drilldown verfügbar.
* Die Ergebnisse der einzelnen Tests können im Detail eingesehen werden, zusammen mit Hinweisen zur Behebung von Problemen, die festgestellt wurden.
* Ein Verlauf der Testergebnisse wird innerhalb von Cloud Manager persistiert, um festzustellen, ob Änderungen, die in der Pipeline-Ausführung eingeführt werden, Regressionen aus der vorherigen Ausführung enthalten.

### Aggregierte Werte {#aggregate-scores}

Der aggregierte Wert entspricht dem Durchschnittswert der Seiten, die in der Ausführung enthalten sind. Die Änderung auf der Aggregatebene stellt den Durchschnittswert der Seiten in der aktuellen Ausführung im Vergleich zum Durchschnittswert der Ergebnisse aus der vorherigen Ausführung dar, selbst wenn die Sammlung der Seiten, die für die Aufnahme konfiguriert wurden, zwischen den Ausführungen geändert wurde.

Für jeden Testtyp wie Leistung, Barrierefreiheit, SEO und Best Practices gibt es einen aggregierten Wert.

Die Änderungsmetrik kann einen der folgenden Werte haben.

* **Positiver Wert** – Die Seite(n) hat sich seit der letzten Ausführung der Produktions-Pipeline beim ausgewählten Test verbessert.

* **Negative Werte** – Die Seite(n) hat sich seit seit der letzten Ausführung der Produktions-Pipeline beim ausgewählten Test verschlechtert.

* **Keine Änderung** – Die Seite(n) hat seit der letzten Ausführung der Produktions-Pipeline denselben Wert erreicht.

* **K/A** – Es gab keinen vorherigen Wert zum Vergleich.

![Experience Audit-Ergebnisse](/help/implementing/cloud-manager/assets/exp-audit-1.png)

### Werte auf Seitenebene {#page-level-scores}

Durch das Aufrufen der Details in einem Test kann eine detailliertere Bewertung auf Seitenebene angezeigt werden. Sie können sehen, wie die einzelnen Seiten für den jeweiligen Test bewertet wurden, zusammen mit der Änderung im Vergleich zum vorherigen Testlauf.

Wenn Sie auf die Details einer einzelnen Seite klicken, erhalten Sie Informationen zu den bewerteten Elementen der Seite sowie Anleitungen zum Beheben von Problemen, falls Verbesserungsmöglichkeiten erkannt werden.

![Werte auf Seitenebene](/help/implementing/cloud-manager/assets/exp-audit-2.png)
