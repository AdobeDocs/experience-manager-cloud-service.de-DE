---
title: Experience Audit-Dashboard
description: Erfahren Sie, wie Experience Audit Ihren Implementierungsprozess validiert und durch eine klare, informative Dashboard-Oberfläche sicherstellt, dass die bereitgestellten Änderungen den Grundstandards für Leistung, Barrierefreiheit, Best Practices und SEO entsprechen.
exl-id: 6d33c3c5-258c-4c9c-90c2-d566eaeb14c0
source-git-commit: 2d4ffd5518d671a55e45a1ab6f1fc41ac021fd80
workflow-type: ht
source-wordcount: '824'
ht-degree: 100%

---

# Experience Audit-Dashboard {#experience-audit-dashboard}


Erfahren Sie, wie Experience Audit Ihren Implementierungsprozess validiert und durch eine klare, informative Dashboard-Oberfläche sicherstellt, dass die bereitgestellten Änderungen den Grundstandards für Leistung, Barrierefreiheit, Best Practices und SEO entsprechen.

>[!NOTE]
>
>Diese Funktion ist nur für das [Early-Adopter-Programm](/help/implementing/cloud-manager/release-notes/current.md#early-adoption) verfügbar.
>
>Weitere Informationen zur vorhandenen Experience Audit-Funktion für AEM as a Cloud Service finden Sie unter [Testen mit Experience Audit](/help/implementing/cloud-manager/experience-audit-testing.md).

## Übersicht {#overview}

Experience Audit ist eine Funktion, die in Cloud Manager Sites-Produktions-Pipelines verfügbar ist und den Implementierungsprozess validiert sowie dabei hilft, sicherzustellen, dass Änderungen bereitgestellt werden:

1. Erfüllen Sie Grundanforderungen an Leistung, Barrierefreiheit, Best Practices, SEO (Suchmaschinenoptimierung) und PWA (Progressive Web App).

1. Führen Sie keine Regressionen ein.

Experience Audit in Cloud Manager stellt sicher, dass das Erlebnis der Benutzenden auf der Site höchsten Standards entspricht.

Die Ergebnisse des Audits sind rein informativ und ermöglichen es dem Bereitstellungs-Manager, die Bewertungen sowie die Unterschiede zwischen aktuellen und vorherigen Bewertungen anzuzeigen. Diese Erkenntnis ist wertvoll, um festzustellen, ob es eine Regression gibt, die mit der aktuellen Bereitstellung eingeführt wurde.

Experience Audit basiert auf [Google Lighthouse](https://developer.chrome.com/docs/lighthouse/overview/), einem Open-Source-Tool von Google, und ist in allen Cloud Manager-Produktions-Pipelines aktiviert.

>[!TIP]
>
>Sie konfigurieren, welche Seiten bei Experience Audit einbezogen werden sollen, wenn Sie das [Einrichten Ihrer Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#full-stack-code) vornehmen.

## Das Experience Audit-Dashboard {#dashboard}

Die Ergebnisse des Experience Audit werden im Schritt **Staging-Tests** der Produktions-Pipeline über die [Ausführungsseite der Produktions-Pipeline](/help/implementing/cloud-manager/deploy-code.md) präsentiert.

![Dashboard in der Pipeline](assets/dashboard.png)

Experience Audit bietet aggregierte und detaillierte Testergebnisse auf Seitenebene, die auf vier Registerkarten zusammengefasst sind:

* **[Einblicke](#insights)** geben eine kurze Beschreibung der umsetzbaren Empfehlungen zur Verbesserung der Leistung Ihrer Site.
* **[Lighthouse-Bewertungen](#lighthouse)** sind eine Zusammenfassung der Lighthouse-Bewertungen für den Code, der in dieser Pipeline-Ausführung bereitgestellt wird.
* **[Seiten](#pages)** ist eine Zusammenfassung der Leistung von Seiten, die speziell für die Analyse konfiguriert wurden.
* **[Probleme](#issues)** fasst alle Leistungsprobleme zusammen, die im Code dieser Pipeline-Ausführung erkannt wurden.

### Einblicke {#insights}

Die Registerkarte **Einblicke** enthält eine kurze Beschreibung der umsetzbaren Empfehlungen zur Verbesserung der Leistung Ihrer Site.

![Einblicke](assets/insights.png)

Wählen Sie die Schaltfläche **Mehr anzeigen** aus, um das vollständige Dashboard zu öffnen.

Im Abschnitt **Einblicke und Empfehlungen** finden Sie eine detaillierte Liste der umsetzbaren Empfehlungen mit einem klaren Wertindikator, der an Gewinne gebunden ist, die bei der Leistung zu erwarten sind, sowie den betroffenen Prozentsatz der Seiten. Auf diese Weise können Sie diese Empfehlungen für Ihre Teams einfach priorisieren.

![Einblicke und Empfehlungen](assets/insights-recommendations.png)

Um zur Ausführungsseite der Produktions-Pipeline zurückzukehren, wählen Sie einfach den Zurück-Pfeil im Browser aus.

### Lighthouse-Bewertungen {#lighthouse}

Die Registerkarte **Lighthouse-Bewertungen** ist eine Zusammenfassung der Lighthouse-Bewertungen für den Code, der in dieser Pipeline-Ausführung bereitgestellt wird.

![Lighthouse-Bewertungen](assets/lighthouse.png)

Wählen Sie die Schaltfläche **Mehr anzeigen** aus, um das vollständige Dashboard zu öffnen.

Im Abschnitt **Lighthouse-Bewertungen** finden Sie eine Trend-Ansicht der verschiedenen Bewertungen. Wählen Sie **Leistung**, **Zugänglichkeit**, **PWA** oder **SEO** aus, um die monatliche Trend-Ansicht für diese Werte anzuzeigen.

![Diagramme zu Lighthouse-Bewertungen](assets/lighthouse-scores.png)

Jeder Punkt im Diagramm ist der Durchschnitt aller Implementierungen im jeweiligen Monat.

Um zur Ausführungsseite der Produktions-Pipeline zurückzukehren, wählen Sie einfach den Zurück-Pfeil im Browser aus.

### Seiten {#pages}

Die Registerkarte **Seiten** ist eine Zusammenfassung der Leistung von Seiten, die speziell für die Analyse konfiguriert wurden.

![Registerkarte „Seiten“](assets/pages.png)

Wählen Sie die Schaltfläche **Mehr anzeigen** aus, um das vollständige Dashboard zu öffnen.

Der Abschnitt **Seiten** bietet eine Liste der getesteten Seiten mit den aktuellsten Lighthouse-Leistungsbewertungen und der Aufschlüsselung.

![Seiten-Ansicht](assets/pages-view.png)

Sie konfigurieren, welche Seiten bei Experience Audit einbezogen werden sollen, wenn Sie Ihre [Pipeline einrichten](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#full-stack-code).

Um zur Ausführungsseite der Produktions-Pipeline zurückzukehren, wählen Sie einfach den Zurück-Pfeil im Browser aus.

### Probleme {#issues}

Die Registerkarte **Probleme** in diesem Tab fasst alle Leistungsprobleme zusammen, die im Code dieser Pipeline-Ausführung erkannt wurden.

![Registerkarte „Probleme“](assets/issues.png)

Wählen Sie die Schaltfläche **Mehr anzeigen** aus, um das vollständige Dashboard zu öffnen.

Im Abschnitt **Einblicke und Empfehlungen** finden Sie eine detailliertere Liste der umsetzbaren Empfehlungen mit einem klaren Wertindikator, der an Gewinne gebunden ist, die bei der Leistung zu erwarten sind, sowie den betroffenen Prozentsatz der Seiten. Auf diese Weise können Sie diese Empfehlungen für Ihre Teams einfach priorisieren.

![Einblicke und Empfehlungen](assets/insights-recommendations.png)

Um zur Ausführungsseite der Produktions-Pipeline zurückzukehren, wählen Sie einfach den Zurück-Pfeil im Browser aus.

### Seitendetails {#page-detail}

Wenn Sie den Link einer Seite auf einer Registerkarte des Abschnitts **Experience Audit** der Registerkarte „Pipeline-Ausführungsseite“ oder im Abschnitt **Seiten** des vollständigen Dashboards von Experience Audit auswählen, können Sie die Details einer bestimmten Seite anzeigen.

![Seitendaten](assets/page-data.png)

Sie können sehen, wie die einzelnen Seiten für den jeweiligen Test bewertet wurden, zusammen mit der Änderung im Vergleich zum vorherigen Testlauf.

Wenn Sie auf die Details einer einzelnen Seite klicken, erhalten Sie Informationen zu den bewerteten Elementen der Seite sowie Anleitungen zur Problembehebung, falls Verbesserungsmöglichkeiten erkannt werden.

Um zur Ausführungsseite der Produktions-Pipeline zurückzukehren, wählen Sie einfach den Zurück-Pfeil im Browser aus.
