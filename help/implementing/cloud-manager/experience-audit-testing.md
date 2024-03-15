---
title: Testen mit Experience Audit
description: Erfahren Sie, wie Experience Audit Ihren Implementierungsprozess validiert und sicherstellt, dass die bereitgestellten Änderungen den Grundstandards für Leistung, Barrierefreiheit, Best Practices und SEO entsprechen.
exl-id: 8d31bc9c-d38d-4d5b-b2ae-b758e02b7073
source-git-commit: 3ba5184275e539027728ed134c47f66fa4746d9a
workflow-type: tm+mt
source-wordcount: '890'
ht-degree: 68%

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

Experience Audit in Cloud Manager stellt sicher, dass das Erlebnis der Benutzenden auf der Site höchsten Standards entspricht.

Die Ergebnisse des Audits sind rein informativ und ermöglichen es dem Bereitstellungs-Manager, die Bewertungen sowie die Unterschiede zwischen aktuellen und vorherigen Bewertungen anzuzeigen. Diese Erkenntnis ist wertvoll, um festzustellen, ob es eine Regression gibt, die mit der aktuellen Bereitstellung eingeführt wurde.

Experience Audit basiert auf Google Lighthouse, einem Open Source-Tool von Google.

>[!INFO]
>
>Mit Wirkung vom 31. August 2023 wechselt Experience Audit zur Anzeige der Ergebnisse, die für die mobile Plattform spezifisch sind. Beachten Sie, dass die Leistungsmetriken für Mobilgeräte in der Regel niedriger sind als für Desktop-Computer. Daher sollten Sie nach dieser Änderung eine Verschiebung der gemeldeten Leistung erwarten.

## Verfügbarkeit {#availability}

Experience Audit ist für Cloud Manager verfügbar:

* Sites-Produktions-Pipelines, standardmäßig.
* Front-End-Entwicklungs-Pipelines, optional.

Siehe [Konfigurationsabschnitt](#configuration) Weitere Informationen zum Konfigurieren der Prüfung für die optionalen Umgebungen.

## Konfiguration {#configuration}

Experience Audit ist standardmäßig für Produktions-Pipelines verfügbar. Sie kann optional für Front-End-Entwicklungs-Pipelines aktiviert werden. In allen Fällen müssen Sie definieren, welche Inhaltspfade während der Pipeline-Ausführung ausgewertet werden.

Sie konfigurieren beim Einrichten der Pipeline, welche Seiten in der Erlebnisprüfung enthalten sind.

1. Je nach Pipeline-Typ, den Sie konfigurieren möchten, befolgen Sie die folgenden Anweisungen:

   * Hinzufügen neuer [Produktions-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) , wenn Sie die Pfade definieren möchten, die von der Prüfung bewertet werden sollen.
   * Hinzufügen neuer [produktionsfremde Pipeline,](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) , wenn Sie die Prüfung in einer Front-End- oder Entwicklungs-Full-Stack-Pipeline aktivieren möchten.
   * Oder Sie können [eine vorhandene Pipeline bearbeiten,](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md) und aktualisieren Sie die vorhandenen Optionen.

1. Wenn Sie eine produktionsfremde Pipeline hinzufügen oder bearbeiten, für die Sie Experience Audit verwenden möchten, müssen Sie die **Erlebnisprüfung** Kontrollkästchen auf der **Quellcode** Registerkarte.

   ![Erlebnisprüfung aktivieren](assets/experience-audit-enable.jpg)

   * Dies ist nur für produktionsfremde Pipelines erforderlich.
   * Die **Erlebnisprüfung** angezeigt, wenn das Kontrollkästchen aktiviert ist.

1. Für Produktions- und Nicht-Produktions-Pipelines definieren Sie die Pfade, die im Experience Audit auf der Seite **Erlebnisprüfung** Registerkarte.

   * Seitenpfade müssen mit `/` und sind relativ zu Ihrer Site.
   * Wenn Ihre Site beispielsweise `wknd.site` und möchte `https://wknd.site/us/en/about-us.html` Geben Sie im Experience Audit den Pfad ein. `/us/en/about-us.html`.

   ![Definieren eines Pfads für das Experience Audit](assets/experience-audit-add-page.png)

1. Tippen oder klicken **Seite hinzufügen** und der Pfad wird automatisch mit der Adresse Ihrer Umgebung ausgefüllt und der Pfadtabelle hinzugefügt.

   ![Speichern des Pfads zur Tabelle](assets/experience-audit-page-added.png)

1. Fügen Sie weitere Pfade hinzu, indem Sie die vorherigen beiden Schritte wiederholen.

   * Sie können maximal 25 Pfade hinzufügen.
   * Wenn Sie keine Pfade definieren, wird die Startseite der Site standardmäßig in das Experience Audit einbezogen.

1. Klicken Sie auf **Speichern**, um die Pipeline zu speichern.

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

* **Positiver Wert** – Die Seiten wurden seit der letzten Ausführung der Produktions-Pipeline beim ausgewählten Test verbessert.

* **Negativer Wert** – Die Seiten haben sich seit der letzten Ausführung der Produktions-Pipeline beim ausgewählten Test verschlechtert.

* **Keine Veränderung** – Die Seiten haben seit der letzten Ausführung der Produktions-Pipeline denselben Wert erreicht.

* **K/A** – Es gab keinen vorherigen Wert zum Vergleich.

![Experience Audit-Ergebnisse](/help/implementing/cloud-manager/assets/exp-audit-1.png)

### Werte auf Seitenebene {#page-level-scores}

Durch das Aufrufen der Details in einem Test kann eine detailliertere Bewertung auf Seitenebene angezeigt werden. Sie können sehen, wie die einzelnen Seiten für den jeweiligen Test bewertet wurden, zusammen mit der Änderung im Vergleich zum vorherigen Testlauf.

Wenn Sie auf die Details einer einzelnen Seite klicken, erhalten Sie Informationen zu den bewerteten Elementen der Seite sowie Anleitungen zur Problembehebung, falls Verbesserungsmöglichkeiten erkannt werden.

![Werte auf Seitenebene](/help/implementing/cloud-manager/assets/exp-audit-2.png)
