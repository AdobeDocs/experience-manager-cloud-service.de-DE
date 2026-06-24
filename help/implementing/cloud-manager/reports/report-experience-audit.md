---
title: Erlebnis-Audit-Dashboard
description: Erfahren Sie, wie der Erlebnis-Audit Ihren Implementierungsprozess validiert und sicherstellt, dass die Änderungen den Grundstandards für Leistung, Barrierefreiheit, Best Practices und SEO entsprechen. Es bietet eine klare und informative Dashboard-Oberfläche zum Verfolgen dieser Metriken.
exl-id: 6d33c3c5-258c-4c9c-90c2-d566eaeb14c0
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
source-git-commit: f0562cd812c89aad5af468f4839f068ed26eada1
workflow-type: tm+mt
source-wordcount: 1551
ht-degree: 66%

---


# Erlebnis-Audit-Dashboard {#experience-audit-dashboard}

<!-- Engineer architect over this feature was Bogdan Anton; scrum master Alexandru Nica -->

Erfahren Sie, wie der Erlebnis-Audit Ihren Implementierungsprozess validiert und sicherstellt, dass die Änderungen den Grundstandards für Leistung, Barrierefreiheit, Best Practices und SEO (Suchmaschinen-Optimierung) entsprechen. Es bietet eine klare und informative Dashboard-Oberfläche zum Verfolgen dieser Metriken.

## Überblick {#overview}

Der Erlebnis-Audit validiert den Bereitstellungsprozess und stellt sicher, dass die Änderungen bereitgestellt werden:

1. Die Grundanforderungen an Leistung, Barrierefreiheit, Best Practices und SEO (Suchmaschinenoptimierung) werden erfüllt.
1. Es werden keine Regressionen eingeführt.

Experience Audit in Cloud Manager stellt sicher, dass das Benutzererlebnis auf der Site höchsten Standards entspricht.

Die Ergebnisse des Audits sind rein informativ und ermöglichen es dem Bereitstellungs-Manager, die Bewertungen sowie die Unterschiede zwischen aktuellen und vorherigen Bewertungen anzuzeigen. Diese insight ist nützlich, um festzustellen, ob durch die aktuelle Bereitstellung eine Regression eingeführt wurde.

[Google Lighthouse](https://developer.chrome.com/docs/lighthouse/overview/), ein Open-Source-Tool von Google, unterstützt Experience Audit, und Cloud Manager aktiviert es in allen Produktions-Pipelines.

## Verfügbarkeit {#availability}

Das Erlebnis-Audit ist für folgende Cloud Manager-Pipelines verfügbar:

* (Standard) Produktions-Pipelines für Sites
* (Optional) Entwicklung von Full-Stack-Pipelines
* (Optional) Entwicklung von Frontend-Pipelines

Weitere Informationen zum Konfigurieren der Prüfung für die optionalen Umgebungen finden Sie im [Konfigurationsabschnitt](#configuration).

Prüfungen werden als Teil der Pipeline ausgeführt. Audits können auch [On-Demand) &#x200B;](#on-demand) Pipelines ausgeführt werden.

## Konfiguration {#configuration}

Das Erlebnis-Audit ist standardmäßig für Produktions-Pipelines verfügbar. Sie kann optional für Full-Stack- und Frontend-Pipelines aktiviert werden. In allen Fällen müssen Sie definieren, welche Inhaltspfade während der Pipeline-Ausführung ausgewertet werden.

1. Führen Sie je nach Typ der Pipeline, die konfiguriert werden soll, einen der folgenden Schritte aus:

   * Um die Pfade zu definieren, die vom Audit ausgewertet werden sollen, [&#x200B; Sie eine Produktions-Pipeline &#x200B;](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md).
   * [Hinzufügen einer produktionsfremden Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) wenn Sie die Prüfung für eine Frontend- oder Full-Stack-Pipeline aktivieren möchten.
   * Sie können [eine vorhandene Pipeline bearbeiten](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md) und die vorhandenen Optionen aktualisieren.

1. Um den Erlebnis-Audit beim Hinzufügen oder Bearbeiten einer Nicht-Produktions-Pipeline zu verwenden, aktivieren Sie das Kontrollkästchen **Erlebnis-Audit**. Diese Option finden Sie auf der Registerkarte **Quell-Code**.

   ![Aktivieren des Erlebnis-Audits](/help/implementing/cloud-manager/reports/assets/experience-audit-enable.jpg)

   * Nur für produktionsfremde Pipelines erforderlich.
   * Die Registerkarte **Erlebnis-Audit** wird beim Auswählen des Kontrollkästchens angezeigt.

1. Die Pfade für Produktions-Pipelines und produktionsfremde Pipelines, die in das Erlebnis-Audit aufgenommen werden sollen, werden auf der Registerkarte **Erlebnis-Audit** definiert.

   * Seitenpfade müssen mit `/` beginnen und sind relativ zu Ihrer Site.
   * Wenn Ihre Site beispielsweise `wknd.site` ist und Sie `https://wknd.site/us/en/about-us.html` (nur Beispiel-URL) in das Experience Audit aufnehmen, geben Sie den Pfad `/us/en/about-us.html` ein.

   ![Definieren eines Pfads für das Erlebnis-Audit](/help/implementing/cloud-manager/reports/assets/experience-audit-add-page.png)

1. Wenn Sie auf **Seite hinzufügen** klicken, wird der Pfad automatisch mit der Adresse Ihrer Umgebung ausgefüllt und der Pfadtabelle hinzugefügt.

   ![Speichern des Pfads zur Tabelle](/help/implementing/cloud-manager/reports/assets/experience-audit-page-added.png)

1. Fügen Sie weitere Pfade hinzu, indem Sie die vorherigen beiden Schritte wiederholen.

   * Sie können maximal 25 Pfade hinzufügen.
   * Wenn Sie keine Pfade definieren, umfasst Experience Audit standardmäßig die Homepage der Site.

1. Klicken Sie auf **Speichern**.

## Ergebnisse des Erlebnis-Audits {#results}

Die Ergebnisse des Erlebnis-Audits werden im Schritt **Staging-Tests** der Produktions-Pipeline über die Seite [Ausführung der Produktions-Pipeline](/help/implementing/cloud-manager/deploy-code.md) dargestellt.

![Dashboard in der Pipeline](/help/implementing/cloud-manager/reports/assets/experience-audit-dashboard.png)

Das Erlebnis-Audit gibt die mittleren Google-Lighthouse-Bewertungen für die [konfigurierten Seiten](#configuration) und die Differenz zwischen dem Ergebnis und dem vorherigen Scan an.

Über diese Zusammenfassungsansicht in der Phase **Stage-Testing** der Pipeline haben Sie zwei Optionen:

* **[Langsamste Seiten anzeigen](#view-slowest-pages)**
* **[Vollständigen Bericht anzeigen](#view-full-report)**

Sie können auf die vollständigen Prüfergebnisse zugreifen, indem Sie im Cloud Manager-Dashboard auf die Registerkarte **Berichte** klicken. Zusätzlich zur Zusammenfassung, die in den Details der Pipeline-Ausführung angezeigt wird, können Sie [den vollständigen Bericht](#view-full-report) direkt anzeigen.

>[!TIP]
>
>In den folgenden Abschnitten wird beschrieben, wie Sie die Ergebnisse des Erlebnis-Audits anzeigen.
>
>* Weitere Informationen zur Funktionsweise der Prüfung finden Sie unter [Auswertungsdetails beim Erlebnis-Audit](#details).
>* Informationen zum Ausführen eines Erlebnis-Audits nach Bedarf finden Sie unter [On-Demand-Auditberichte](#on-demand).
>* Wenn beim Audit Probleme auftreten, lesen Sie [Beim Erlebnis-Audit treten Probleme auf](#issues).

### Anzeigen der langsamsten Seiten {#view-slowest-pages}

Um das Dialogfeld **Langsamste 5 Seiten** zu öffnen, klicken Sie auf **Langsamste Seiten anzeigen**. Die fünf Seiten mit der niedrigsten Leistung, die Sie [für den Audit konfiguriert haben](#configuration), werden angezeigt.

![Die langsamsten fünf](/help/implementing/cloud-manager/reports/assets/experience-audit-slowest-five.png)

Cloud Manager schlüsselt die Bewertungen nach **Leistung**, **Barrierefreiheit**, **Best Practices** und **SEO** auf und zeigt die Abweichung der einzelnen Metriken im Vergleich zur vorherigen Prüfung an.

Standardmäßig wird das Dialogfeld mit den Bewertungen für Mobilgeräte geöffnet. Sie können mithilfe des Umschalters **Geräte** am oberen Rand des Dialogfelds die Desktop-Bewertungen anzeigen.

Das Dialogfeld bietet einen schnellen Überblick. Für die vollständigen Details klicken Sie auf **Vollständigen Bericht anzeigen**.

### Anzeigen des vollständigen Berichts {#view-full-report}

Sie können den vollständigen Bericht zum Erlebnis-Audit wie folgt anzeigen:

* Klicken Sie im Dialogfeld **[Langsamste 5 Seiten](#view-slowest-pages)** auf **`View full report`**.
* Klicken Sie beim Anzeigen der [Ausführung einer Pipeline](#results) auf **`View full report`**.
* Klicken Sie in Cloud Manager auf die Registerkarte **Berichte**.

Die Registerkarte **Berichte** von Cloud Manager wird geöffnet und zeigt den **Erlebnis-Audit** an.

![Berichte zum Erlebnis-Audit](/help/implementing/cloud-manager/reports/assets/experience-audit-reports.png)

Der Bericht ist in zwei Bereiche unterteilt:

* **[Seitenbewertungen – Trend](#trend)**
* **[Ergebnisse des Erlebnis-Audit-Scans](#results)**

#### Seitenbewertungen – Trend {#trend}

Standardmäßig zeigt die ausgewählte Ansicht für **Seitenbewertungen – Trend** die **Medianwerte** für das **letzte Jahr**.

Sie können die Trends für bestimmte Lighthouse-Kategorien anzeigen, indem Sie in der Legende auf den Kategorienamen klicken.

![Auswählbarer Trend](/help/implementing/cloud-manager/reports/assets/experience-audit-trend-selectable.png)

Verwenden Sie das Dropdown-Menü **Auswählen** oben im Diagramm, um seitenspezifische Details auszuwählen, und die **Anzeigen** und **Trigger** Dropdown-Listen unten, um unterschiedliche Zeitrahmen und den Trigger-Typ auszuwählen.

In der Dropdown-Liste **Anzeigen** können Sie einen voreingestellten Zeitrahmen oder ein benutzerdefiniertes Intervall für eine spezifischere Ansicht auswählen.

![Trend-Ansicht](/help/implementing/cloud-manager/reports/assets/experience-audit-trend-view.png)

Wenn Sie den Mauszeiger über das Diagramm bewegen, zeigt eine QuickInfo die Werte für die Google Lighthouse-Kategorien zu bestimmten Zeitpunkten an.

![Trend-Details](/help/implementing/cloud-manager/reports/assets/experience-audit-trend-details.png)

Wenn Sie zu einem bestimmten Zeitpunkt auf das Diagramm klicken, wird ein Popup mit Details zu diesem Scan geöffnet. Klicken Sie auf **Experience Audit-Scan öffnen** um diese Scan-Ergebnisse in den Abschnitt **[Experience Audit-Scan-Ergebnisse](#scan-results)** zu laden.

![Anderen Scan auswählen](/help/implementing/cloud-manager/reports/assets/experience-audit-open-scan.png)

#### Ergebnisse des Erlebnis-Audit-Scans {#scan-results}

Der Abschnitt **Ergebnisse des Erlebnis-Audit-Scans** enthält Detailbewertungen für alle gescannten Seiten. Verwenden Sie die Schaltflächen **Prev** und **Next**, um durch die Ergebnisse zu navigieren und auszuwählen, wie viele angezeigt werden sollen.

![Gescannte Seiten](/help/implementing/cloud-manager/reports/assets/experience-audit-scanned-pages.png)

Wenn Sie auf den Link einer bestimmten Seite klicken, wird der Filter **Auswählen** des Abschnitts [**Seitenbewertungen -**) &#x200B;](#trend) und die Registerkarte **Rohberichte** angezeigt, auf der Sie Bewertungen für jede Prüfung der Seite finden. Klicken Sie in der Spalte **Lighthouse-Bericht** auf das Berichtsdatum, um eine JSON-Datei der Rohdaten abzurufen.

![Rohberichte](/help/implementing/cloud-manager/reports/assets/experience-audit-raw-reports.png)

Eine neue Registerkarte, die in Ihrem Browser geöffnet wird, führt Sie zu `https://googlechrome.github.io/lighthouse/viewer/`. Er lädt automatisch eine signierte URL, die den Lighthouse-JSON-Rohbericht für die ausgewählte Seite enthält, und ermöglicht so eine detaillierte Überprüfung.

![Anzeigen des Rohberichts](/help/implementing/cloud-manager/reports/assets/experience-audit-view-raw-report.png)

## On-Demand-Scan-Audit-Berichte {#on-demand}

Experience Audit-Berichte werden nicht nur während der Pipeline-Ausführung ausgeführt, sondern können auch bei Bedarf erstellt werden. Diese Option ist eine effektive Lösung, um Ihre Seiten schnell zu scannen, ohne eine Pipeline ausführen zu müssen.

Navigieren Sie zum Ausführen eines Scans auf Anforderung zur Registerkarte **Berichte**, damit Sie den vollständigen Auditbericht sehen können, und klicken Sie dann auf die Schaltfläche **Scan ausführen**.

![On-Demand-Scan](/help/implementing/cloud-manager/reports/assets/experience-audit-on-demand.png)

Die Schaltfläche **Scan ausführen** wird nicht mehr verfügbar und zeigt ein Uhrensymbol an, wenn bereits ein Scan auf Anforderung ausgeführt wird.

![Laufender On-Demand-Scan](/help/implementing/cloud-manager/reports/assets/experience-audit-on-demand-running.png)

On-Demand-Scans lösen ein Erlebnis-Audit für die letzten 25 [konfigurierten Seiten](#configuration) aus und werden in der Regel innerhalb weniger Minuten abgeschlossen.

Nach Abschluss des Vorgangs wird das Bewertungsdiagramm automatisch aktualisiert und Sie können die Ergebnisse genau wie bei einem Pipeline-Ausführungs-Scan überprüfen.

Sie können das Bewertungsdiagramm nach dem Trigger-Typ filtern, indem Sie die Auswahl **Trigger** auswählen.

![Trigger-Filter](/help/implementing/cloud-manager/reports/assets/experience-audit-on-demand-trigger.png)

>[!NOTE]
>
>Ein Scan auf Anforderung kann nur gestartet werden, wenn die Umgebung nicht gelöscht wurde und es keine weiteren ausstehenden Scans in derselben Umgebung gibt.

## Probleme beim Erlebnis-Audit {#issues}

Wenn [Seiten, die Sie für den Audit konfiguriert haben](#configuration), nicht verfügbar waren oder beim Audit andere Fehler aufgetreten sind, spiegelt der Erlebnis-Audit dies wider.

Die Pipeline zeigt einen erweiterbaren Fehlerabschnitt an, um die relativen URL-Pfade anzuzeigen, auf die sie nicht zugreifen kann.

![Beim Erlebnis-Audit aufgetretene Probleme](/help/implementing/cloud-manager/reports/assets/experience-audit-issues.png)

Wenn Sie den vollständigen Bericht anzeigen, finden Sie Details dazu im erweiterbaren Abschnitt **[Ergebnisse des Erlebnis-Audit-Scans](#results)**.

![Vollständiger Bericht – Probleme](/help/implementing/cloud-manager/reports/assets/experience-audit-issues-report.png)

Einige Gründe dafür, dass die Seiten nicht verfügbar sind, sind die folgenden:

* Der Zugriff wird durch die Konfiguration blockiert.
* Die Seite ist nicht vorhanden.
* Die Seite wird umgeleitet, wofür die Standardauthentifizierung nicht ausreicht.
* Es ist ein internes Problem aufgetreten.

>[!TIP]
>
>[Zugriff auf die Rohberichte](#scan-results) für eine Seite liefert Details dazu, warum die Seite nicht geprüft wurde.

## Auswertungsdetails beim Erlebnis-Audit {#details}

Die folgenden Details liefern zusätzliche Informationen darüber, wie Ihre Site vom Erlebnis-Audit ausgewertet wird. Sie sind für die allgemeine Nutzung der Funktion nicht erforderlich und werden hier der Vollständigkeit halber bereitgestellt.

* Die Prüfung scannt die Ursprungs-(`.com`-)Domain aus den [konfigurierten Experience Audit-](#configuration) des Herausgebers, um echte Benutzererlebnisse zu simulieren und Ihnen dabei zu helfen, fundierte Entscheidungen über die Verwaltung und Optimierung Ihrer Websites zu treffen.
* In Produktions-Full-Stack-Pipelines wird die Staging-Umgebung gescannt. Um sicherzustellen, dass der Audit beim Audit relevante Details liefert, ist der Inhalt der Staging-Umgebung so nah wie möglich an der Produktionsumgebung.
* Die im Dropdown-Menü **Auswählen** im Abschnitt [**Seitenbewertungen - Trend** angezeigten Seiten &#x200B;](#trend) alle bekannte Seiten, die in der Vergangenheit vom Experience Audit gescannt wurden.
