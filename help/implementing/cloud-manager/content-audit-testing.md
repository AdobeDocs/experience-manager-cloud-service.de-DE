---
title: Content Audit-Tests - Cloud Services
description: Content Audit-Tests - Cloud Services
translation-type: tm+mt
source-git-commit: ce25ec1472dc349937fdbd5f7265d4295fe111e8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Content Audit-Tests {#content-audit-testing}

Content Audit ist eine Funktion, die in Cloud Manager-Sites-Produktionsleitungen verfügbar ist, die von Lighthouse, einem Open-Source-Tool von Google, betrieben werden. Diese Funktion ist in allen Cloud Manager-Produktionsleitungen aktiviert.

Er validiert den Bereitstellungsprozess und stellt sicher, dass die bereitgestellten Änderungen

1. Erfüllen Sie Grundstandards für Leistung, Barrierefreiheit, Best Practices, SEO (Suchmaschinenoptimierung) und PWA (Progressive Web App).

1. Schließen Sie keine Regressionen in diese Dimensionen ein.

Content Audit in Cloud Manager stellt sicher, dass das digitale Erlebnis der Endbenutzer auf der Site auf höchstem Niveau gehalten wird. Die Ergebnisse sind informativ und ermöglichen es dem Benutzer, die Ergebnisse und die Änderung zwischen den aktuellen und vorherigen Bewertungen zu sehen. Diese Erkenntnis ist nützlich, um festzustellen, ob es eine Regression gibt, die mit der aktuellen Bereitstellung eingeführt wird.

## Informationen zu den Ergebnissen der Inhaltsprüfung {#understanding-content-audit-results}

Content Audit bietet Aggregat- und detaillierte Testergebnisse auf Seitenebene über die Seite zur Ausführung der Produktionspipeline.

* Metriken auf Aggregat-Ebene messen den Durchschnittswert der geprüften Seiten.
* Einzelne Seitenergebnisse sind auch per Drilldown verfügbar.
* Details zu den Ergebnissen der einzelnen Tests sowie Hinweise zur Behebung von Problemen, die bei der Inhaltsprüfung festgestellt wurden, sind verfügbar.
* Der Verlauf der Testergebnisse wird innerhalb von Cloud Manager beibehalten, damit Kunden sehen können, ob Änderungen, die in der Pipeline-Ausführung vorgenommen werden, Regressionen aus der vorherigen Ausführung enthalten.

### Aggregat-Ergebnisse {#aggregate-scores}

Für jeden Testtyp (Leistung, Barrierefreiheit, SEO, Best Practices und PWA) gibt es einen Aggregat-Level-Wert.

Das Aggregat-Level-Ergebnis entspricht dem Durchschnittswert der Seiten, die in der Ausführung enthalten sind. Die Änderung auf Aggregat-Ebene stellt den Durchschnittswert der Seiten in der aktuellen Ausführung im Vergleich zum Durchschnittswert der Ergebnisse aus der vorherigen Ausführung dar, selbst wenn die Seitenerfassung, die für die Aufnahme konfiguriert wurde, zwischen den Ausführungen geändert wurde.

Der Wert der Änderungsmetrik kann einer der folgenden sein:

* **Positiver Wert** : Die Seite(n) wurde(n) seit dem letzten Produktionsablauf beim ausgewählten Test verbessert.

* **Negativer Wert** : Die Seite(n) ist/sind seit dem letzten Produktionszyklus auf dem ausgewählten Test zurückgekehrt

* **Keine Änderung** - die Seite(n) hat/haben seit dem letzten Produktionszyklus denselben Wert erreicht

* **K/A** - Es gab keine vorherige Punktzahl zum Vergleich

   ![](/help/implementing/developing/introduction/assets/content-audit-test1.png)

### Bewertungen auf Seitenebene {#page-level-scores}

Durch das Bohren in einem der Tests kann eine detailliertere Bewertung auf Seitenniveau angezeigt werden. Der Benutzer kann sehen, wie die einzelnen Seiten für den jeweiligen Test bewertet wurden, zusammen mit der Änderung gegenüber der vorherigen Ausführung des Tests.

Wenn Sie auf die Details einer einzelnen Seite klicken, erhalten Sie Informationen zu den bewerteten Elementen der Seite sowie Anleitungen zur Problembehebung, falls Verbesserungsmöglichkeiten festgestellt werden. Die Details der Tests und die damit verbundenen Anleitungen werden von Google Lighthouse bereitgestellt.

![](/help/implementing/developing/introduction/assets/page-level-scores.png)

