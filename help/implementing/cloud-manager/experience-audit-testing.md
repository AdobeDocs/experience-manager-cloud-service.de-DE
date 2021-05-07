---
title: Testen mit Experience Audit – Cloud Services
description: Testen mit Experience Audit – Cloud Services
exl-id: 8d31bc9c-d38d-4d5b-b2ae-b758e02b7073
translation-type: tm+mt
source-git-commit: f6c700f82bc5a1a3edf05911a29a6e4d32dd3f72
workflow-type: tm+mt
source-wordcount: '577'
ht-degree: 100%

---

# Testen mit Experience Audit {#experience-audit-testing}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_expaudittesting"
>title="Testen mit Experience Audit"
>abstract="Experience Audit ist eine Funktion, die in Cloud Manager-Sites-Produktions-Pipelines verfügbar ist, und wird von Google Lighthouse, einem Open-Source-Tool von Google, unterstützt. Die Funktion ist in allen Cloud Manager-Produktions-Pipelines aktiviert."

Experience Audit ist eine Funktion, die in Cloud Manager-Sites-Produktions-Pipelines verfügbar ist, und wird von Google Lighthouse, einem Open-Source-Tool von Google, unterstützt. Die Funktion ist in allen Cloud Manager-Produktions-Pipelines aktiviert.

Sie validiert den Implementierungsprozess und stellt sicher, dass Änderungen implementiert werden:

1. Erfüllen Sie Grundanforderungen an Leistung, Barrierefreiheit, Best Practices, SEO (Suchmaschinenoptimierung) und PWA (Progressive Web App).

1. Schließen Sie in diese Dimensionen keine Regressionen ein.

Mit Experience Audit in Cloud Manager wird sichergestellt, dass digitale Erlebnisse der Endbenutzer auf der Site höchsten Standards entsprechen. Die Ergebnisse sind informativ und ermöglichen es dem Benutzer, die Bewertungen sowie die Unterschiede zwischen aktuellen und vorherigen Bewertungen anzuzeigen. Diese Erkenntnis ist nützlich, um festzustellen, ob es eine Regression gibt, die mit der aktuellen Implementierung eingeführt wird.

## Verstehen der Ergebnisse von Experience Audit {#understanding-experience-audit-results}

Experience Audit bietet aggregierte und detaillierte Testergebnisse auf Seitenebene über die Ausführungsseite der Produktions-Pipeline.

* Metriken auf der Aggregatebene messen den durchschnittlichen Wert auf allen Seiten, die auf Leistung, Barrierefreiheit, Best Practices und SEO (Suchmaschinenoptimierung) hin geprüft wurden.
   >[!NOTE]
   >Der Wert für Progressive Web App (PWA) ist nicht im Zusammenfassungswert enthalten und wird nur im Bildschirm für Berichtdetails auf Seitenebene angezeigt.
* Die Werte auf der Ebene einzelner Seiten sind auch per Drilldown verfügbar.
* Es gibt Details zu den Werten der einzelnen Tests sowie Hinweise zur Behebung von Problemen, die bei der Erlebnisprüfung ermittelt wurden.
* Ein Verlauf der Testergebnisse wird innerhalb von Cloud Manager persistiert, damit Kunden sehen können, ob Änderungen, die in der Pipeline-Ausführung eingeführt werden, Regressionen aus der vorherigen Ausführung enthalten.

### Aggregierte Werte {#aggregate-scores}

Für jeden Testtyp wie Leistung, Barrierefreiheit, SEO und Best Practices gibt es einen aggregierten Wert.
>[!NOTE]
>Der Wert für Progressive Web App (PWA) ist nicht im Zusammenfassungswert enthalten und wird nur im Bildschirm für Berichtdetails auf Seitenebene angezeigt.

Der aggregierte Wert entspricht dem Durchschnittswert der Seiten, die in der Ausführung enthalten sind. Die Änderung auf der Aggregatebene stellt den Durchschnittswert der Seiten in der aktuellen Ausführung im Vergleich zum Durchschnittswert der Ergebnisse aus der vorherigen Ausführung dar, selbst wenn die Sammlung der Seiten, die für die Aufnahme konfiguriert wurden, zwischen den Ausführungen geändert wurde.

Der Wert der Änderungsmetrik kann einer der folgenden sein:

* **Positiver Wert**: Die Seiten wurden seit der letzten Ausführung der Produktions-Pipeline beim ausgewählten Test verbessert.

* **Negativer Wert**: Die Seiten wurden seit der letzten Ausführung der Produktions-Pipeline beim ausgewählten Test regrediert.

* **Keine Änderung**: Die Seiten haben seit der letzten Ausführung der Produktions-Pipeline denselben Wert erreicht.

* **K/A**: Es gab keinen vorherigen Wert zum Vergleich.

   ![](/help/implementing/cloud-manager/assets/exp-audit-1.png)


### Werte auf der Seitenebene {#page-level-scores}

Durch das Aufrufen der Details in einem Test kann eine detailliertere Bewertung auf Seitenebene angezeigt werden. Der Benutzer kann sehen, wie die einzelnen Seiten beim jeweiligen Test bewertet wurden, und Änderungen im Vergleich zur vorherigen Ausführung des Tests anzeigen.

Wenn Sie auf die Details einer einzelnen Seite klicken, erhalten Sie Informationen zu den bewerteten Elementen der Seite sowie Anleitungen zur Problembehebung, falls Verbesserungsmöglichkeiten erkannt werden. Die Details der Tests und damit verbundene Anleitungen werden von Google Lighthouse bereitgestellt.

![](/help/implementing/cloud-manager/assets/exp-audit-2.png)
