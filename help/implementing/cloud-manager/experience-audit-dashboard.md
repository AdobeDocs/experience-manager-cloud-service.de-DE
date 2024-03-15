---
title: Experience Audit-Dashboard
description: Erfahren Sie, wie Experience Audit Ihren Implementierungsprozess validiert und durch eine klare, informative Dashboard-Oberfläche sicherstellt, dass die bereitgestellten Änderungen den Grundstandards für Leistung, Barrierefreiheit, Best Practices und SEO entsprechen.
exl-id: 6d33c3c5-258c-4c9c-90c2-d566eaeb14c0
source-git-commit: 3ba5184275e539027728ed134c47f66fa4746d9a
workflow-type: tm+mt
source-wordcount: '1958'
ht-degree: 11%

---


# Experience Audit-Dashboard {#experience-audit-dashboard}

Erfahren Sie, wie Experience Audit Ihren Implementierungsprozess validiert und durch eine klare, informative Dashboard-Oberfläche sicherstellt, dass die bereitgestellten Änderungen den Grundstandards für Leistung, Barrierefreiheit, Best Practices und SEO entsprechen.

>[!NOTE]
>
>Diese Funktion ist nur für das [Early-Adopter-Programm](/help/implementing/cloud-manager/release-notes/current.md#early-adoption) verfügbar.
>
>Weitere Informationen zur vorhandenen Funktion &quot;Experience Audit&quot;für AEM as a Cloud Service finden Sie im Dokument [Testen mit Experience Audit](/help/implementing/cloud-manager/experience-audit-testing.md)

## Übersicht {#overview}

Mit Experience Audit wird der Bereitstellungsprozess validiert und sichergestellt, dass die bereitgestellten Änderungen bereitgestellt werden:

1. Erfüllen Sie Grundanforderungen an Leistung, Barrierefreiheit, Best Practices, SEO (Suchmaschinenoptimierung) und PWA (Progressive Web App).

1. Führen Sie keine Regressionen ein.

Experience Audit in Cloud Manager stellt sicher, dass das Erlebnis der Benutzenden auf der Site höchsten Standards entspricht.

Die Ergebnisse des Audits sind rein informativ und ermöglichen es dem Bereitstellungs-Manager, die Bewertungen sowie die Unterschiede zwischen aktuellen und vorherigen Bewertungen anzuzeigen. Diese Erkenntnis ist wertvoll, um festzustellen, ob es eine Regression gibt, die mit der aktuellen Bereitstellung eingeführt wurde.

Experience Audit basiert auf [Google Lighthouse](https://developer.chrome.com/docs/lighthouse/overview/), ein Open-Source-Tool von Google, und ist in allen Cloud Manager-Produktions-Pipelines aktiviert.

## Verfügbarkeit {#availability}

Experience Audit ist für Cloud Manager verfügbar:

* Sites-Produktions-Pipelines, standardmäßig
* Entwickeln von Vollstapelpipelines, optional
* Entwicklung von Front-End-Pipelines, optional

Siehe [Konfigurationsabschnitt](#configuration) Weitere Informationen zum Konfigurieren der Prüfung für die optionalen Umgebungen.

Prüfungen werden als Teil der Pipeline ausgeführt. Prüfungen können auch [On-Demand ausführen](#on-demand) außerhalb von Pipelines.

## Konfiguration {#configuration}

Experience Audit ist standardmäßig für Produktions-Pipelines verfügbar. Sie kann optional für die Entwicklung von Full-Stack- und Front-End-Pipelines aktiviert werden. In allen Fällen müssen Sie definieren, welche Inhaltspfade während der Pipeline-Ausführung ausgewertet werden.

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

## Experience Audit-Ergebnisse {#results}

Die Ergebnisse der Erlebnisprüfung werden im Abschnitt **Staging-Tests** Phase der Produktions-Pipeline über die [Ausführungsseite der Produktions-Pipeline.](/help/implementing/cloud-manager/deploy-code.md)

![Dashboard in der Pipeline](assets/experience-audit-dashboard.jpg)

Experience Audit bietet die Median-Google-Lighthouse-Bewertungen für die [konfigurierte Seiten](#configuration) und die Differenz zwischen dem Ergebnis und dem vorherigen Scan.

Aus dieser Zusammenfassungsansicht im **Staging-Tests** -Phase der Pipeline haben Sie zwei Optionen:

* **[Niedrigste Seiten anzeigen](#view-slowest-pages)**
* **[Vollständigen Bericht anzeigen](#view-full-report)**

Zusätzlich zu der in den Details eines Pipeline-Laufs dargestellten Zusammenfassung können Sie auch direkt auf die vollständigen Ergebnisse der Prüfung zugreifen, indem Sie die **Berichte** Registerkarte des Cloud Manager-Dashboards, um auf [den vollständigen Bericht](#view-full-report) direkt.

>[!TIP]
>
>In den folgenden Abschnitten wird beschrieben, wie Sie die Ergebnisse des Experience Audit anzeigen.
>
>* Weitere Informationen zur Funktionsweise der Prüfung finden Sie im Abschnitt . [Details zur Erlebnisprüfung.](#details)
>* Wenn Sie wissen möchten, wie Sie eine Erlebnisprüfung bei Bedarf durchführen, lesen Sie den Abschnitt . [On-Demand-Audit-Berichte.](#on-demand)
>* Wenn bei der Prüfung Probleme auftreten, lesen Sie bitte den Abschnitt . [Beim Erlebnisaudit treten Probleme auf.](#issues)
>* Allgemeine Tipps zur Leistung finden Sie im Abschnitt . [Allgemeine Tipps zur Leistung.](#performance-tips)

### Langsamste Seiten anzeigen {#view-slowest-pages}

Tippen oder Klicken **Niedrigste Seiten anzeigen** öffnet die **Langsam 5 Seiten** Dialogfeld mit den fünf Seiten mit der niedrigsten Leistung, die Sie [zur Prüfung konfiguriert.](#configuration)

![Weniger als fünf](assets/experience-audit-slowest-five.jpg)

Die Punktzahl wird nach **Leistung**, **Zugänglichkeit**, **Best Practices**, und **SEO** zusammen mit der Abweichung der einzelnen Metriken von der letzten Prüfung.

Standardmäßig wird das Dialogfeld mit den Bewertungen für Mobilgeräte geöffnet. Sie können dies mithilfe des **Geräte** -Umschalter am oberen Rand des Dialogfelds.

Das Dialogfeld soll einen schnellen Überblick verschaffen. Für vollständige Details tippen oder klicken Sie auf **Vollständigen Bericht anzeigen**.

### Vollständigen Bericht anzeigen {#view-full-report}

Sie können den vollständigen Experience Audit-Bericht anzeigen, indem Sie:

* Tippen oder Klicken **Vollständigen Bericht anzeigen** im **[Langsam 5 Seiten](#view-slowest-pages)** angezeigt.
* Tippen oder Klicken **Vollständigen Bericht anzeigen** beim Anzeigen der [Ausführung einer Pipeline.](#results)
* Tippen oder klicken Sie auf **Berichte** in Cloud Manager.

Die **Berichte** -Registerkarte von Cloud Manager geöffnet ist, wird die **Erlebnisprüfung**.

![Berichte zur Erlebnisprüfung](assets/experience-audit-reports.png)

Der Bericht ist in zwei Bereiche unterteilt:

* **[Seitenergebnisse - Trend](#trend)**
* **[Prüfergebnisse der Erlebnisprüfung](#results)**

#### Seitenbewertungen – Trend {#trend}

Standardmäßig wird die ausgewählte Ansicht für **Seitenergebnisse - Trend** is **Medianwerte** für die **Letzte 6 Monate**.

Verwenden Sie die **Auswählen** und **Ansicht** oben und unten in der Diagrammschaltfläche angezeigt, um seitenspezifische Details bzw. unterschiedliche Zeitrahmen auszuwählen. Tippen oder klicken Sie auf und die **Aktualisierungstrend** -Schaltfläche am oberen Rand des Diagramms, um die Auswahl anzuwenden und das Diagramm zu aktualisieren.

Wenn Sie den Mauszeiger über das Diagramm bewegen, zeigt eine QuickInfo die Werte für die Google Lighthouse-Kategorien zu bestimmten Zeitpunkten an.

![Trend-Details](assets/experience-audit-trend-details.png)

Wenn Sie zu einem bestimmten Zeitpunkt auf das Diagramm tippen oder darauf klicken, wird ein Popup mit Details zu dieser Prüfung geöffnet. Tippen oder klicken Sie auf **Prüfung der offenen Erlebnis** , um diese Überprüfungsergebnisse in die **[Prüfergebnisse der Erlebnisprüfung](#scan-results)** Abschnitt.

![Andere Prüfung auswählen](assets/experience-audit-open-scan.png)

#### Prüfergebnisse der Experience Audit-Prüfung {#scan-results}

Die **Prüfergebnisse der Erlebnisprüfung** gibt Empfehlungen dazu, wie Sie Ihre Punktzahl und Details aller gescannten Seiten verbessern können. Er ist in zwei Abschnitte unterteilt:

* **[Empfehlungen](#recommendations)**
* **[Gescannte Seiten](#scanned-pages)**

##### Empfehlungen {#recommendations}

Die **Recommendations** zeigt einen aggregierten Satz von Einblicken. Standardmäßig werden Empfehlungen für **Leistung** angezeigt werden. Verwenden Sie das Dropdown-Menü neben dem **Recommendations** -Überschrift zu einer anderen Kategorie wechseln.

![Empfehlungen](assets/experience-audit-recommendations.png)

Tippen oder klicken Sie auf den Pfeil, um eine Empfehlung anzuzeigen.

![Empfehlungsdetails](assets/experience-audit-recommendation-details.png)

Sofern verfügbar, enthalten die erweiterten Empfehlungsdetails auch den Prozentsatz der Auswirkungen der Empfehlungen, um sich auf die wirkungsvollsten Änderungen zu konzentrieren.

Tippen oder klicken Sie auf **Seiten anzeigen** in der Detailansicht, um die Seiten anzuzeigen, für die die Empfehlung gilt.

![Seiten für die Empfehlungsdetails](assets/experience-audit-details-pages.png)

##### Gescannte Seiten {#scanned-pages}

Die **Gescannte Seiten** enthält Detailbewertungen für alle gescannten Seiten. Sie können die **Prev** und **Nächste** -Schaltflächen, um die Ergebnisse zu durchblättern, und wählen Sie aus, wie viele Anzeigen paginiert werden sollen.

![Gescannte Seiten](assets/experience-audit-scanned-pages.png)

Durch Tippen oder Klicken auf den Link einer bestimmten Seite wird die **Auswählen** des [**Seitenergebnisse - Trend** Abschnitt](#trend) und zeigt die **Bewertungen und Empfehlungen** Registerkarte für die ausgewählte Seite.

![Seitenergebnisse](assets/experience-audit-page-results.png)

Die **Rohberichte** -Tab gibt Ihnen Werte für jede Prüfung der Seite. Tippen oder klicken Sie auf **Herunterladen** -Symbol, um eine JSON-Datei der Rohdaten abzurufen.

![Rohbericht](assets/experience-audit-raw-reports.png)

Dadurch wird eine neue Registerkarte in Ihrem Browser geöffnet, die auf Folgendes verweist: `https://googlechrome.github.io/lighthouse/viewer/` mit einer signierten URL des Berichts &quot;Lighthouse Raw JavaScript Object Notation (JSON)&quot;für die ausgewählte Seite, der automatisch für die detaillierte Überprüfung geöffnet wird

![Rohbericht anzeigen](assets/experience-audit-view-raw-report.png)

## On-Demand-Audit-Berichte {#on-demand}

Experience Audit-Berichte werden nicht nur während der Pipelineausführung ausgeführt, sondern können auch bei Bedarf generiert werden. Dies ist eine gute Lösung, um Ihre Seiten schnell zu überprüfen, ohne eine Pipeline ausführen zu müssen.

Um eine On-Demand-Prüfung auszuführen, navigieren Sie zum  **Berichte** Registerkarte, um den vollständigen Prüfungsbericht anzuzeigen, und tippen oder klicken Sie auf **Ausführen einer Prüfung** Schaltfläche.

![On-Demand-Abtastung](assets/experience-audit-on-demand.png)

On-Demand scannt Trigger und Erlebnisprüfung auf die letzten 25 [konfigurierte Seiten](#configuration) und in der Regel in wenigen Minuten abgeschlossen werden.

Nach Abschluss des Vorgangs wird das Scores-Diagramm automatisch aktualisiert und Sie können die Ergebnisse genau wie bei einer Pipeline-Ausführungsprüfung überprüfen.

Sie können das Punktdiagramm nach dem Trigger-Typ filtern, indem Sie die **Trigger** auswählen.

![Trigger-Filter](assets/experience-audit-on-demand-trigger.png)

>[!NOTE]
>
>Eine On-Demand-Prüfung kann nur gestartet werden, wenn die Umgebung nicht gelöscht wird und es keine weiteren ausstehenden Prüfungen in derselben Umgebung gibt.

## Probleme mit Experience Audit-Ergebnissen {#issues}

Wenn [von Ihnen konfigurierte Seiten](#configuration) nicht verfügbar waren, wurde dies durch Experience Audit widergespiegelt.

Die Pipeline zeigt einen erweiterbaren Fehlerabschnitt an, um die relativen URL-Pfade anzuzeigen, auf die sie nicht zugreifen konnte.

![Bei Experience Audit aufgetretene Probleme](assets/experience-audit-issues.jpg)

Wenn Sie sich den vollständigen Bericht ansehen, finden Sie Details im **[Prüfergebnisse der Erlebnisprüfung](#results)** Abschnitt.

![Vollständige Berichtsprobleme](assets/experience-audit-issues-reports.jpeg)

Einige Gründe, aus denen die Seiten möglicherweise nicht verfügbar sind, sind:

* Die Konfiguration blockiert den Zugriff.
* Die Seite ist nicht vorhanden.
* Die Seite wird umgeleitet, für die eine andere Authentifizierung als die einfache erforderlich ist.
* Es ist ein internes Problem aufgetreten.
* usw.

>[!TIP]
>
>[Rohberichte aufrufen](#scanned-pages) für eine Seite können Details dazu enthalten, warum die Seite nicht geprüft werden konnte.

## Allgemeine Tipps zur Leistung {#performance-tips}

Zwei der am häufigsten auftretenden Probleme, die einfach zu beheben sind, beziehen sich auf kumulative Layoutverschiebungen (CLS) und die größte inhaltsreiche Farbe (LCP).

Diese können folgendermaßen verbessert werden:

* Das Laden der Bilder über der Kante (der Inhalt, der im Browser sichtbar ist, ohne nach unten scrollen zu müssen) ist nicht hinfällig.
* Ordnungsgemäße Priorisierung der Art und Weise, wie Ressourcen geladen werden (z. B. durch asynchrones Laden der Bilder unterhalb der Kante nach dem Laden des Dokuments).
* Vorabruf von JavaScript- und CSS-Dateien, die verwendet werden, um Inhalte über der Kante zu rendern (falls erforderlich).
* Reservieren des vertikalen Bereichs durch Zuweisen eines Seitenverhältnisses zu Containern, die entweder langsam geladen werden oder später gerendert werden.
* Bilder in das WebP-Format konvertieren, um ihre Größe zu reduzieren.
* Verwenden `<picture>` und Bild `srcset` mit unterschiedlichen Bildgrößen für verschiedene Darstellungsfeldgrößen (und sicherstellen, dass die Größenanpassung funktioniert).

## Bewertungsdetails für Experience Audit {#details}

Die folgenden Details enthalten zusätzliche Informationen darüber, wie Experience Audit Ihre Site bewertet. Sie sind für die allgemeine Nutzung der Funktion nicht erforderlich und werden hier zur Vollständigkeit bereitgestellt.

* Obwohl die Variable [konfigurierte Seitenpfade für Experience Audit](#configuration) zeigen Sie `.com` Domäne des Herausgebers, prüft die Prüfung den Ursprung (`.net`), um sicherzustellen, dass während der Entwicklung auftretende Probleme erkannt werden.
   * Die `.com` -Domäne verwendet ein CDN und könnte bessere Ergebnisse liefern oder zwischengespeicherte Ergebnisse enthalten.
* In Produktions-Vollstapelpipelines wird die Staging-Umgebung gescannt.
   * Um sicherzustellen, dass die Prüfung während der Prüfung relevante Details liefert, sollte der Inhalt der Staging-Umgebung so nah wie möglich an der Produktionsumgebung liegen.
* Die in der Variablen **Auswählen** Dropdown im [**Seitenergebnisse - Trend** Abschnitt](#trend) sind alle bekannten Seiten, die in der Vergangenheit vom Experience Audit gescannt wurden.
* [Eine Empfehlung](#recommendations) kann einen potenziellen Gewinn und einen Unterschied zum vorherigen Scan aufweisen.
   * Experience Audit schätzt den potenziellen Gewinn, indem der Rohbericht für jede Seite verarbeitet und die verschwendeten Bytes oder Millisekunden mit einem Einblick korreliert werden, der sich auf das Leistungsergebnis auswirkt.
   * Die Prüfung enthält diese Informationen (sowie die betroffenen Seiten), um zu entscheiden, welche Empfehlung weiterverfolgt werden soll.
   * Weitere Informationen finden Sie im [Allgemeine Tipps zur Leistung](#performance-tips)
* Da eine Frontend-Pipeline in einer bestehenden Umgebung bereitgestellt werden kann (oder es mehrere Frontend-Pipelines für dieselbe Umgebung geben kann) und die Überprüfungsergebnisse auf Umgebungsebene aggregiert werden, werden die Bewertungen, Trends und Empfehlungen in derselben ausgewählten Umgebung angezeigt, unabhängig von der Pipeline-Ausführung, die den Scan ausgelöst hat.
