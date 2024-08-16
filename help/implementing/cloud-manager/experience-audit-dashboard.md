---
title: Experience Audit-Dashboard
description: Erfahren Sie, wie Experience Audit Ihren Implementierungsprozess validiert und sicherstellt, dass die Änderungen den Grundstandards für Leistung, Barrierefreiheit, Best Practices und SEO entsprechen. Es bietet eine klare und informative Dashboard-Oberfläche zum Verfolgen dieser Metriken.
exl-id: 6d33c3c5-258c-4c9c-90c2-d566eaeb14c0
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 72868ab808ebbd99c5e81805e7669083c5c754fb
workflow-type: tm+mt
source-wordcount: '1927'
ht-degree: 47%

---


# Dashboard &quot;Erlebnisprüfung&quot; {#experience-audit-dashboard}

Erfahren Sie, wie Experience Audit Ihren Implementierungsprozess validiert und sicherstellt, dass die Änderungen den Grundstandards für Leistung, Barrierefreiheit, Best Practices und SEO entsprechen. Es bietet eine klare und informative Dashboard-Oberfläche zum Verfolgen dieser Metriken.

>[!NOTE]
>
>Diese Funktion steht nur [dem frühen Adopter-Programm](/help/implementing/cloud-manager/release-notes/current.md#early-adoption) zur Verfügung.
>
>Weitere Informationen zur vorhandenen Experience Audit-Funktion für AEM as a Cloud Service finden Sie unter [Testen mit Experience Audit](/help/implementing/cloud-manager/experience-audit-testing.md).

## Überblick {#overview}

Mit Experience Audit wird der Bereitstellungsprozess validiert und sichergestellt, dass die Änderungen bereitgestellt werden:

1. Erfüllen Sie Grundanforderungen an Leistung, Barrierefreiheit, Best Practices, SEO (Suchmaschinenoptimierung) und PWA (Progressive Web App).

1. Führen Sie keine Regressionen ein.

Experience Audit in Cloud Manager stellt sicher, dass das Erlebnis der Benutzenden auf der Site höchsten Standards entspricht.

Die Ergebnisse des Audits sind rein informativ und ermöglichen es dem Bereitstellungs-Manager, die Bewertungen sowie die Unterschiede zwischen aktuellen und vorherigen Bewertungen anzuzeigen. Diese Erkenntnis ist wertvoll, um festzustellen, ob es eine Regression gibt, die mit der aktuellen Bereitstellung eingeführt wurde.

Die Erlebnisprüfung basiert auf [Google Lighthouse](https://developer.chrome.com/docs/lighthouse/overview/), einem Open-Source-Tool von Google, und ist in allen Cloud Manager-Produktions-Pipelines aktiviert.

## Verfügbarkeit {#availability}

Die Erlebnisprüfung ist für folgende Cloud Manager-Pipelines verfügbar:

* (Standard) Produktions-Pipelines für Sites
* (Optional) Entwicklung von Vollstapelpipelines
* (Optional) Entwicklung von Front-End-Pipelines

Weitere Informationen zum Konfigurieren der Prüfung für die optionalen Umgebungen finden Sie im [Konfigurationsabschnitt](#configuration).

Prüfungen werden als Teil der Pipeline ausgeführt. Prüfungen können auch [bei Bedarf](#on-demand) außerhalb von Pipelines ausgeführt werden.

## Konfiguration {#configuration}

Die Erlebnisprüfung ist standardmäßig für Produktions-Pipelines verfügbar. Sie kann optional für die Entwicklung von Full-Stack- und Front-End-Pipelines aktiviert werden. In allen Fällen müssen Sie definieren, welche Inhaltspfade während der Pipeline-Ausführung ausgewertet werden.

1. Je nach Pipeline-Typ, der konfiguriert werden soll, befolgen Sie die Anweisungen für diese Vorgänge:

   * Fügen Sie eine neue [Produktions-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) hinzu, um die Pfade zu definieren, die die Prüfung auswerten soll.
   * Fügen Sie eine neue [produktionsfremde Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) hinzu, wenn Sie die Prüfung für eine Frontend- oder Full-Stack-Entwicklungs-Pipeline aktivieren möchten.
   * Oder Sie können [eine vorhandene Pipeline bearbeiten,](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md) und die vorhandenen Optionen aktualisieren.

1. Um beim Hinzufügen oder Bearbeiten einer Nicht-Produktions-Pipeline Experience Audit zu verwenden, aktivieren Sie das Kontrollkästchen **Erlebnisprüfung** . Diese Option finden Sie auf der Registerkarte **Source-Code** .

   ![Aktivieren der Erlebnisprüfung](assets/experience-audit-enable.jpg)

   * Nur für produktionsfremde Pipelines erforderlich.
   * Die Registerkarte **Erlebnisprüfung** wird beim Auswählen des Kontrollkästchens angezeigt.

1. Die Pfade für Produktions-Pipelines und produktionsfremde Pipelines, die in die Erlebnisprüfung aufgenommen werden sollen, werden auf der Registerkarte **Erlebnisprüfung** definiert.

   * Seitenpfade müssen mit `/` beginnen und sind relativ zu Ihrer Site.
   * Wenn Ihre Site beispielsweise `wknd.site` ist und Sie `https://wknd.site/us/en/about-us.html` in die Erlebnisprüfung aufnehmen möchten, geben Sie den Pfad `/us/en/about-us.html` ein.

   ![Definieren eines Pfads für die Erlebnisprüfung](assets/experience-audit-add-page.png)

1. Wenn Sie auf **Seite hinzufügen** klicken, wird der Pfad automatisch mit der Adresse Ihrer Umgebung ausgefüllt und der Pfadtabelle hinzugefügt.

   ![Speichern des Pfads zur Tabelle](assets/experience-audit-page-added.png)

1. Fügen Sie weitere Pfade hinzu, indem Sie die vorherigen beiden Schritte wiederholen.

   * Sie können maximal 25 Pfade hinzufügen.
   * Wenn Sie keine Pfade definieren, wird die Startseite der Site standardmäßig in das Experience Audit einbezogen.

1. Klicken Sie auf **Speichern**.

## Experience Audit-Ergebnisse {#results}

Die Ergebnisse des Experience Audit werden im Schritt **Staging-Tests** der Produktions-Pipeline über die [Ausführungsseite der Produktions-Pipeline](/help/implementing/cloud-manager/deploy-code.md) präsentiert.

![Dashboard in der Pipeline](assets/experience-audit-dashboard.jpg)

Die Erlebnisprüfung gibt die mittleren Google-Lighthouse-Bewertungen für die [konfigurierten Seiten](#configuration) und die Differenz zwischen dem Ergebnis und dem vorherigen Scan an.

Über diese Zusammenfassungsansicht in der Phase **Stage-Testing** der Pipeline haben Sie zwei Optionen:

* **[Anzeigen der langsamsten Seiten](#view-slowest-pages)**
* **[Vollständigen Bericht anzeigen](#view-full-report)**

Sie können auf die vollständigen Prüfergebnisse zugreifen, indem Sie im Cloud Manager-Dashboard auf die Registerkarte **Berichte** klicken. Zusätzlich zur Zusammenfassung, die in den Details der Pipeline-Ausführung angezeigt wird, können Sie [den vollständigen Bericht](#view-full-report) direkt anzeigen.

>[!TIP]
>
>In den folgenden Abschnitten wird beschrieben, wie Sie die Ergebnisse der Erlebnisprüfung anzeigen.
>
>* Weitere Informationen zur Funktionsweise der Prüfung finden Sie unter [Bewertungsdetails für Erlebnisprüfungen](#details).
>* Informationen zum Ausführen einer Erlebnisprüfung bei Bedarf finden Sie unter [On-Demand-Audit-Berichte](#on-demand).
>* Wenn bei der Prüfung Probleme auftreten, finden Sie weitere Informationen unter [Probleme mit der Erlebnisprüfung](#issues).
>* Allgemeine Tipps zur Leistung finden Sie unter [Allgemeine Tipps zur Leistung](#performance-tips).

### Anzeigen der langsamsten Seiten {#view-slowest-pages}

Klicken Sie auf **Langsamste Seiten anzeigen** , um das Dialogfeld **Langsamste 5 Seiten** zu öffnen. Die fünf Seiten mit der niedrigsten Leistung, die Sie [für die Prüfung](#configuration) konfiguriert haben, werden angezeigt.

![Die langsamsten fünf](assets/experience-audit-slowest-five.png)

Cloud Manager schlüsselt die Bewertungen nach **Leistung**, **Barrierefreiheit**, **Best Practices** und **SEO** auf und zeigt die Abweichung der einzelnen Metriken von der vorherigen Prüfung an.

Standardmäßig wird das Dialogfeld mit den Bewertungen für Mobilgeräte geöffnet. Mit dem Umschalter **Geräte** oben im Dialogfeld können Sie Desktop-Bewertungen anzeigen.

Das Dialogfeld bietet einen schnellen Überblick. Um alle Details anzuzeigen, klicken Sie auf **Vollständigen Bericht anzeigen**.

### Gesamten Bericht anzeigen {#view-full-report}

Sie können den vollständigen Experience Audit-Bericht wie folgt anzeigen:

* Klicken Sie im Dialogfeld **[Langsamste 5 Seiten](#view-slowest-pages)** auf **`View full report`**.
* Klicken Sie beim Anzeigen der [Ausführung einer Pipeline](#results) auf **`View full report`**.
* Klicken Sie in Cloud Manager auf die Registerkarte **Berichte** .

Die Registerkarte **Berichte** von Cloud Manager wird geöffnet und zeigt den **Erlebnisaudit** an.

![Experience Audit-Berichte](assets/experience-audit-reports.png)

Der Bericht ist in zwei Bereiche unterteilt:

* **[Seitenergebnisse - Trend](#trend)**
* **[Prüfergebnisse der Erlebnisprüfung](#results)**

#### Seitenergebnisse - Trend {#trend}

Standardmäßig ist die ausgewählte Ansicht für **Seitenergebnisse — Trend** **Medianwerte** für die **letzten 6 Monate**.

Verwenden Sie die Dropdown-Listen **Auswählen** und **Anzeigen** oben und unten im Diagramm, um seitenspezifische Details bzw. unterschiedliche Zeitrahmen auszuwählen. Klicken Sie oben im Diagramm auf **Trend aktualisieren** , um die Auswahl anzuwenden und das Diagramm zu aktualisieren.

Wenn Sie den Mauszeiger über das Diagramm bewegen, zeigt eine QuickInfo die Werte für die Google Lighthouse-Kategorien zu bestimmten Zeitpunkten an.

![Trend-Details](assets/experience-audit-trend-details.png)

Wenn Sie zu einem bestimmten Zeitpunkt auf das Diagramm klicken, wird ein Popup mit Details zu dieser Prüfung geöffnet. Klicken Sie auf **Erlebnisprüfungsprüfung öffnen** , um die Überprüfungsergebnisse in den Abschnitt **[Ergebnisse der Erlebnisprüfung prüfen](#scan-results)** zu laden.

![Anderen Scan auswählen](assets/experience-audit-open-scan.png)

#### Ergebnisse des Erlebnis-Audit-Scans {#scan-results}

Im Abschnitt **Ergebnisse der Prüfung mit Erlebnisprüfungen** finden Sie Empfehlungen zur Verbesserung Ihrer Punktzahl und der Details aller gescannten Seiten. Er ist in zwei Abschnitte unterteilt:

* **[Empfehlungen](#recommendations)**
* **[Gescannte Seiten](#scanned-pages)**

##### Empfehlungen {#recommendations}

Der Abschnitt **Empfehlungen** zeigt einen aggregierten Satz von Einblicken. Standardmäßig werden Empfehlungen für **Leistung** angezeigt. Verwenden Sie das Dropdown-Menü neben der Überschrift **Empfehlungen**, um zu einer anderen Kategorie zu wechseln.

![Empfehlungen](assets/experience-audit-recommendations.png)

Klicken Sie auf den Pfeil für eine Empfehlung, um Details dazu anzuzeigen.

![Empfehlungsdetails](assets/experience-audit-recommendations-details.png)

Sofern verfügbar, enthalten die erweiterten Empfehlungsdetails auch den Prozentsatz der Auswirkungen der Empfehlungen, damit Sie sich auf die wirkungsvollsten Änderungen konzentrieren können.

Klicken Sie in der Detailansicht auf den Link **Seiten anzeigen** , um die Seiten anzuzeigen, für die die Empfehlung gilt.

![Seiten für die Empfehlungsdetails](assets/experience-audit-details-pages.png)

##### Gescannte Seiten {#scanned-pages}

Der Abschnitt **Gescannte Seiten** enthält Details zu den Ergebnissen auf allen gescannten Seiten. Verwenden Sie die Schaltflächen **Prev** und **Next** , um die Ergebnisse zu durchblättern, und wählen Sie aus, wie viele Anzeigen paginiert werden sollen.

![Gescannte Seiten](assets/experience-audit-scanned-pages.png)

Klicken Sie auf den Link einer bestimmten Seite, um den Filter **Auswählen** des Abschnitts [**Seitenergebnisse — Trend**](#trend) zu aktualisieren und die Registerkarte **Bewertungen und Empfehlungen** für die ausgewählte Seite anzuzeigen.

![Seitenergebnisse](assets/experience-audit-page-results.png)

Die Registerkarte **Rohberichte** gibt Bewertungen für jede Prüfung der Seite an. Klicken Sie auf das Berichtsdatum in der Spalte **Leuchtturmbericht** , um eine JSON-Datei der Rohdaten abzurufen.

![Rohberichte](assets/experience-audit-raw-reports.png)

In Ihrem Browser wird eine neue Registerkarte geöffnet, die Sie zu `https://googlechrome.github.io/lighthouse/viewer/` leitet. Er lädt automatisch eine signierte URL, die den Lighthouse-JSON-Rohbericht für die ausgewählte Seite enthält, und ermöglicht so eine detaillierte Überprüfung.

![Anzeigen des Rohberichts](assets/experience-audit-view-raw-report.png)

## On-Demand-Prüfberichte {#on-demand}

Experience Audit-Berichte werden nicht nur während der Pipelineausführung ausgeführt, sondern können auch bei Bedarf generiert werden. Diese Option ist eine gute Lösung, um Ihre Seiten schnell zu scannen, ohne eine Pipeline ausführen zu müssen.

Um eine On-Demand-Prüfung auszuführen, navigieren Sie zur Registerkarte **Berichte** , um den vollständigen Prüfbericht anzuzeigen, und klicken Sie dann auf die Schaltfläche **Scan ausführen** .

![On-Demand-Scan](assets/experience-audit-on-demand.png)

Die Schaltfläche **Scan durchführen** ist dann nicht mehr verfügbar und wird mit einem Uhrensymbol gekennzeichnet, wenn bereits ein On-Demand-Scan läuft.

![Laufender On-Demand-Scan](assets/experience-audit-on-demand-running.png)

On-Demand-Scans lösen eine Erlebnisprüfung für die letzten 25 [konfigurierten Seiten](#configuration) aus und werden in der Regel innerhalb weniger Minuten abgeschlossen.

Nach Abschluss des Vorgangs wird das Scores-Diagramm automatisch aktualisiert und Sie können die Ergebnisse genau wie bei einer Pipeline-Ausführungsprüfung überprüfen.

Sie können das Bewertungsdiagramm nach dem Trigger-Typ filtern, indem Sie die Auswahl **Trigger** auswählen.

![Trigger-Filter](assets/experience-audit-on-demand-trigger.png)

>[!NOTE]
>
>Ein On-Demand-Scan kann nur gestartet werden, wenn die Umgebung nicht gelöscht wird und es keine weiteren ausstehenden Scans in derselben Umgebung gibt.

## Probleme bei der Erlebnisprüfung {#issues}

Wenn [Seiten, die Sie für die Prüfung konfiguriert haben,](#configuration) nicht verfügbar waren oder bei der Prüfung andere Fehler aufgetreten sind, spiegelt Experience Audit diese Tatsache wider.

Die Pipeline präsentiert einen erweiterbaren Fehlerabschnitt, um die relativen URL-Pfade anzuzeigen, wenn kein Zugriff möglich war.

![Bei der Erlebnisprüfung aufgetretene Probleme](assets/experience-audit-issues.jpg)

Beim Anzeigen des vollständigen Berichts werden Details im Abschnitt **[Ergebnisse der Erlebnisprüfung](#results)** angezeigt, der ebenfalls erweiterbar ist.

![Vollständiger Bericht – Probleme](assets/experience-audit-issues-report.png)

Die Seiten können beispielsweise aus folgenden Gründen nicht verfügbar sein:

* Der Zugriff wird durch die Konfiguration blockiert.
* Die Seite ist nicht vorhanden.
* Die Seite wird umgeleitet, wofür die Standardauthentifizierung nicht ausreicht.
* Es ist ein internes Problem aufgetreten.
* usw.

>[!TIP]
>
>Indem Sie die [Rohberichte für eine Seite aufrufen](#scanned-pages), können Sie Einzelheiten darüber erfahren, warum die Seite nicht geprüft werden konnte.

## Allgemeine Tipps zur Leistung {#performance-tips}

Zwei der am häufigsten auftretenden Probleme, die einfach zu beheben sind, beziehen sich auf die Metriken „Cumulative Layout Shifts (CLS)“ und „Largest Contentful Paint (LCP)“.

Sie können diese Bereiche wie folgt verbessern:

* Das Laden der Bilder über der Kante ist nicht faul - der Inhalt, der im Browser sichtbar ist, ohne nach unten scrollen zu müssen.
* Ordnungsgemäße Priorisierung der Art und Weise, wie Ressourcen geladen werden (z. B. durch asynchrones Laden der Bilder unterhalb der Kante nach dem Laden des Dokuments).
* Vorabrufen von JavaScript- und CSS-Dateien, die verwendet werden, um Inhalte über der Falz zu rendern (falls erforderlich).
* Reservieren des vertikalen Bereichs durch Zuweisen eines Seitenverhältnisses zu Containern, die entweder langsam geladen oder später gerendert werden.
* Konvertieren der Bilder in das WebP-Format, um ihre Größe zu reduzieren.
* Verwenden von `<picture>` und Bild-`srcset` mit unterschiedlichen Bildgrößen für verschiedene Viewport-Größen (und Sicherstellen, dass die Größenanpassung funktioniert).

## Auswertungsdetails bei der Erlebnisprüfung {#details}

Die folgenden Details liefern zusätzliche Informationen darüber, wie Ihre Site von der Erlebnisprüfung ausgewertet wird. Sie sind für die allgemeine Nutzung der Funktion nicht erforderlich und werden hier der Vollständigkeit halber bereitgestellt.

* Die Prüfung scannt die Ursprungsdomäne (`.com`) aus den [konfigurierten Pfaden der Experience Audit-Seite](#configuration) des Herausgebers, um reale Benutzererlebnisse zu simulieren, sodass Sie bessere Entscheidungen über die Verwaltung und Optimierung Ihrer Websites treffen können.
* In Produktions-Vollstapelpipelines wird die Staging-Umgebung gescannt. Um sicherzustellen, dass die Prüfung relevante Details während der Prüfung liefert, sollte der Inhalt der Staging-Umgebung der Produktionsumgebung so nahe wie möglich sein.
* Die Seiten, die in der Dropdown-Liste **Auswählen** im Abschnitt [**Seitenergebnisse — Trend**](#trend) angezeigt werden, sind alle bekannten Seiten, die der Experience Audit in der Vergangenheit gescannt hat.
* [Eine Empfehlung](#recommendations) kann einen potenziellen Gewinn und einen Unterschied zum vorherigen Scan aufweisen.
* Experience Audit schätzt potenzielle Verbesserungen, indem der Rohbericht für jede Seite verarbeitet wird. Er ordnet verschwendete Bytes oder Millisekunden mit Einblicken zu, wodurch eine gewichtete Auswirkung auf den Leistungswert zugewiesen wird. Die Prüfung enthält diese Informationen und die betroffenen Seiten, um bei der Entscheidung zu helfen, welche Empfehlung weiterverfolgt werden soll.
Weitere Informationen finden Sie im Abschnitt [Allgemeine Tipps zur Leistung](#performance-tips) .
* Eine Frontend-Pipeline kann in einer vorhandenen Umgebung bereitgestellt werden und mehrere Frontend-Pipelines können für dieselbe Umgebung verwendet werden. Da die Scan-Ergebnisse auf Umgebungsebene aggregiert werden, sind die Bewertungen, Trends und Empfehlungen konsistent. Diese Ergebnisse werden in der ausgewählten Umgebung angezeigt, unabhängig davon, welche Pipeline die Prüfung ausgelöst hat.
