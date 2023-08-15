---
title: Experience Audit-Dashboard
description: Erfahren Sie, wie Experience Audit Ihren Implementierungsprozess validiert und sicherstellt, dass die bereitgestellten Änderungen über eine klare, informative Dashboard-Oberfläche den Grundstandards für Leistung, Barrierefreiheit, Best Practices und SEO entsprechen.
source-git-commit: 5ad33f0173afd68d8868b088ff5e20fc9f58ad5a
workflow-type: tm+mt
source-wordcount: '844'
ht-degree: 17%

---


# Experience Audit-Dashboard {#experience-audit-dashboard}


Erfahren Sie, wie Experience Audit Ihren Implementierungsprozess validiert und sicherstellt, dass die bereitgestellten Änderungen über eine klare, informative Dashboard-Oberfläche den Grundstandards für Leistung, Barrierefreiheit, Best Practices und SEO entsprechen.

>[!NOTE]
>
>Diese Funktion steht nur für [das Programm für den frühen Anwender.](/help/implementing/cloud-manager/release-notes/current.md#early-adoption)
>
>Weitere Informationen zur vorhandenen Funktion &quot;Experience Audit&quot;für AEM as a Cloud Service finden Sie im Dokument [Testen von Experience Audit.](/help/implementing/cloud-manager/experience-audit-testing.md)

## Übersicht {#overview}

Experience Audit ist eine Funktion, die in Cloud Manager Sites-Produktions-Pipelines verfügbar ist und den Implementierungsprozess validiert sowie dabei hilft, sicherzustellen, dass Änderungen bereitgestellt werden:

1. Erfüllen Sie Grundanforderungen an Leistung, Barrierefreiheit, Best Practices, SEO (Suchmaschinenoptimierung) und PWA (Progressive Web App).

1. Führen Sie keine Regressionen ein.

Experience Audit in Cloud Manager stellt sicher, dass das Erlebnis der Endbenutzenden auf der Site höchsten Standards entspricht.

Die Ergebnisse des Audits sind rein informativ und ermöglichen es dem Bereitstellungs-Manager, die Bewertungen sowie die Unterschiede zwischen aktuellen und vorherigen Bewertungen anzuzeigen. Diese Einblicke sind nützlich, um festzustellen, ob es eine Regression gibt, die mit der aktuellen Implementierung eingeführt wurde.

Experience Audit basiert auf [Google Lighthouse,](https://developer.chrome.com/docs/lighthouse/overview/) ein Open-Source-Tool aus Google ist und in allen Cloud Manager-Produktions-Pipelines aktiviert ist.

>[!TIP]
>
>Sie konfigurieren, welche Seiten bei Experience Audit einbezogen werden sollen, wenn Sie das [Einrichten Ihrer Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#full-stack-code) vornehmen.

## Das Dashboard &quot;Erlebnisprüfung&quot; {#dashboard}

Die Ergebnisse der Erlebnisprüfung werden im Abschnitt **Staging-Tests** Phase der Produktions-Pipeline über die [Ausführungsseite der Produktions-Pipeline.](/help/implementing/cloud-manager/deploy-code.md)

![Dashboard in der Pipeline](assets/dashboard.png)

Experience Audit bietet aggregierte und detaillierte Testergebnisse auf Seitenebene, die auf vier Registerkarten zusammengefasst sind:

* **[Insights](#insights)** Geben Sie eine kurze Beschreibung der umsetzbaren Empfehlungen zur Verbesserung der Leistung Ihrer Site.
* **[Lighthouse-Bewertungen](#lighthouse)** sind eine Zusammenfassung der Lighthouse-Werte für den Code, der in dieser Pipeline-Ausführung bereitgestellt wird.
* **[Seiten](#pages)** ist eine Zusammenfassung der Leistung von Seiten, die speziell für die Analyse konfiguriert wurden.
* **[Probleme](#issues)** fasst alle Leistungsprobleme zusammen, die im Code dieser Pipeline-Ausführung erkannt wurden.

### Insights {#insights}

Die **Insights** -Tab enthält eine kurze Beschreibung der umsetzbaren Empfehlungen zur Verbesserung der Leistung Ihrer Site.

![Erkenntnisse](assets/insights.png)

Tippen oder klicken Sie auf **Mehr anzeigen** -Schaltfläche, um das vollständige Dashboard zu öffnen.

Im **Einblicke und Empfehlungen** finden Sie eine detaillierte Liste der umsetzbaren Empfehlungen mit einem klaren Wertindikator, der an die bei der Performance zu erwartenden Gewinne gebunden ist, sowie den betroffenen Prozentsatz der Seiten. Auf diese Weise können Sie diese Empfehlungen einfach für Ihre Teams priorisieren.

![Einblicke und Empfehlungen](assets/insights-recommendations.png)

Um zur Ausführungsseite der Produktions-Pipeline zurückzukehren, wählen Sie einfach den Pfeil nach hinten im Browser aus.

### Lighthouse-Werte {#lighthouse}

Die **Lighthouse-Bewertungen** tab eine Zusammenfassung der Lighthouse-Werte für den Code, der in dieser Pipeline-Ausführung bereitgestellt wird.

![Lighthouse-Bewertungen](assets/lighthouse.png)

Tippen oder klicken Sie auf **Mehr anzeigen** -Schaltfläche, um das vollständige Dashboard zu öffnen.

Im **Lighthouse-Bewertungen** finden Sie eine Trendansicht der verschiedenen Bewertungen. Auswählen **Leistung**, **Zugänglichkeit**, **PWA** oder **SEO** um die monatliche Trendansicht für diese Werte anzuzeigen.

![Diagramme für Lighthouse-Bewertungen](assets/lighthouse-scores.png)

Beachten Sie, dass jeder Punkt im Diagramm der Durchschnitt aller Implementierungen im Monat des Interesses ist.

Um zur Ausführungsseite der Produktions-Pipeline zurückzukehren, wählen Sie einfach den Pfeil nach hinten im Browser aus.

### Seiten {#pages}

Die **Seiten** -Tab ist eine Zusammenfassung der Leistung von Seiten, die speziell für die Analyse konfiguriert wurden.

![Registerkarte &quot;Seiten&quot;](assets/pages.png)

Tippen oder klicken Sie auf **Mehr anzeigen** -Schaltfläche, um das vollständige Dashboard zu öffnen.

Die **Seiten** bietet eine Liste der getesteten Seiten mit den aktuellsten Lighthouse-Leistungsbewertungen und der Aufschlüsselung.

![Seitenansicht](assets/pages-view.png)

Sie konfigurieren, welche Seiten bei Experience Audit einbezogen werden sollen, wenn Sie das [Einrichten Ihrer Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#full-stack-code) vornehmen.

Um zur Ausführungsseite der Produktions-Pipeline zurückzukehren, wählen Sie einfach den Pfeil nach hinten im Browser aus.

### Probleme {#issues}

Die **Probleme** in diesem Tab werden alle Leistungsprobleme zusammengefasst, die im Code dieser Pipeline-Ausführung erkannt wurden.

![Registerkarte &quot;Probleme&quot;](assets/issues.png)

Tippen oder klicken Sie auf **Mehr anzeigen** -Schaltfläche, um das vollständige Dashboard zu öffnen.

Im **Einblicke und Empfehlungen** finden Sie eine detailliertere Liste der umsetzbaren Empfehlungen mit einem klaren Wertindikator, der an die bei der Performance zu erwartenden Gewinne gebunden ist, sowie den betroffenen Prozentsatz der Seiten. Auf diese Weise können Sie diese Empfehlungen einfach für Ihre Teams priorisieren.

![Einblicke und Empfehlungen](assets/insights-recommendations.png)

Um zur Ausführungsseite der Produktions-Pipeline zurückzukehren, wählen Sie einfach den Pfeil nach hinten im Browser aus.

### Seitendetails {#page-detail}

Wenn Sie auf den Link einer Seite auf einer der Registerkarten des **Erlebnisprüfung** auf der Registerkarte &quot;Pipeline-Ausführungsseite&quot;oder im **Seiten** im vollständigen Dashboard von Experience Audit können Sie die Details einer bestimmten Seite anzeigen.

![Seitendaten](assets/page-data.png)

Sie können sehen, wie die einzelnen Seiten für den jeweiligen Test bewertet wurden, zusammen mit der Änderung im Vergleich zum vorherigen Testlauf.

Wenn Sie auf die Details einer einzelnen Seite klicken, erhalten Sie Informationen zu den bewerteten Elementen der Seite sowie Anleitungen zum Beheben von Problemen, falls Verbesserungsmöglichkeiten erkannt werden.

Um zur Ausführungsseite der Produktions-Pipeline zurückzukehren, wählen Sie einfach den Pfeil nach hinten im Browser aus.
