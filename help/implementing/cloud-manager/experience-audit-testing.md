---
title: Testen mit Experience Audit
description: Erfahren Sie, wie Experience Audit Ihren Implementierungsprozess validiert und sicherstellt, dass die bereitgestellten Änderungen den Grundstandards für Leistung, Barrierefreiheit, Best Practices und SEO entsprechen.
exl-id: 8d31bc9c-d38d-4d5b-b2ae-b758e02b7073
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: ht
source-wordcount: '890'
ht-degree: 100%

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

Die Erlebnisprüfung basiert auf Google Lighthouse, einem Open-Source-Tool von Google.

>[!INFO]
>
>Seit dem 31. August 2023 wechselt die Erlebnisprüfung zur Anzeige der Ergebnisse, die für die mobile Plattform spezifisch sind. Beachten Sie, dass die Leistungsmetriken für Mobilgeräte in der Regel niedriger sind als für Desktop-Computer. Daher sollten Sie nach dieser Änderung eine Verschiebung der gemeldeten Leistung erwarten.

## Verfügbarkeit {#availability}

Die Erlebnisprüfung ist für folgende Cloud Manager-Pipelines verfügbar:

* Sites-Produktions-Pipelines, standardmäßig.
* Frontend-Entwicklungs-Pipelines, optional.

Im [Abschnitt „Konfiguration“](#configuration) finden Sie weitere Informationen zum Konfigurieren der Prüfung für die optionalen Umgebungen.

## Konfiguration {#configuration}

Die Erlebnisprüfung ist standardmäßig für Produktions-Pipelines verfügbar. Sie kann optional für Frontend-Entwicklungs-Pipelines aktiviert werden. In allen Fällen müssen Sie definieren, welche Inhaltspfade während der Pipeline-Ausführung ausgewertet werden.

Sie konfigurieren, welche Seiten bei der Erlebnisprüfung einbezogen werden sollen, wenn Sie Ihre Pipeline einrichten.

1. Je nach Pipeline-Typ, der konfiguriert werden soll, befolgen Sie die Anweisungen für diese Vorgänge:

   * Fügen Sie eine neue [Produktions-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) hinzu, wenn Sie die Pfade definieren möchten, die von der Prüfung bewertet werden sollen.
   * Fügen Sie eine neue [produktionsfremde Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) hinzu, wenn Sie die Prüfung für eine Frontend- oder Full-Stack-Entwicklungs-Pipeline aktivieren möchten.
   * Oder Sie können [eine vorhandene Pipeline bearbeiten,](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md) und die vorhandenen Optionen aktualisieren.

1. Wenn Sie eine produktionsfremde Pipeline hinzufügen oder bearbeiten, für die Sie die Erlebnisprüfung verwenden möchten, müssen Sie das Kontrollkästchen **Erlebnisprüfung** auf der Registerkarte **Quell-Code** auswählen.

   ![Aktivieren der Erlebnisprüfung](assets/experience-audit-enable.jpg)

   * Dies ist nur für produktionsfremde Pipelines erforderlich.
   * Die Registerkarte **Erlebnisprüfung** wird beim Auswählen des Kontrollkästchens angezeigt.

1. Die Pfade für Produktions-Pipelines und produktionsfremde Pipelines, die in die Erlebnisprüfung aufgenommen werden sollen, werden auf der Registerkarte **Erlebnisprüfung** definiert.

   * Seitenpfade müssen mit `/` beginnen und sind relativ zu Ihrer Site.
   * Wenn Ihre Site beispielsweise `wknd.site` ist und Sie `https://wknd.site/us/en/about-us.html` in die Erlebnisprüfung aufnehmen möchten, geben Sie den Pfad `/us/en/about-us.html` ein.

   ![Definieren eines Pfads für die Erlebnisprüfung](assets/experience-audit-add-page.png)

1. Wenn Sie auf **Seite hinzufügen** tippen oder klicken, wird der Pfad automatisch mit der Adresse Ihrer Umgebung ausgefüllt und der Pfadtabelle hinzugefügt.

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
