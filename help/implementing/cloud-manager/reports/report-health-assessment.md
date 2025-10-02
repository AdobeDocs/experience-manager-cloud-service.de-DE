---
title: Health Assessment für Produktions- und Staging-Umgebungen
description: Erfahren Sie, wie Sie Cloud Manager Health Assessment verwenden. Sie können AEM-Umgebungen scannen, Berichte ausführen und überprüfen, Problemdetails anzeigen, PDFs exportieren und frühere Ausführungen verwalten.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 5f9d53958076b77cd333a042003c83853594db87
workflow-type: tm+mt
source-wordcount: '1406'
ht-degree: 8%

---


# Konsistenzprüfung {#about-health-assessment}

Die Konsistenzbewertung ist eine automatisierte, unterbrechungsfreie Prüfung für Produktions- und Staging-Umgebungen in Cloud Manager innerhalb von AEM as a Cloud Service. Es bewertet Inhalte, Code und Konfigurationen, um Anti-Muster und Abweichungen von Best Practices zu finden und so die Sicherheit und Leistung zu verbessern.

Der Health Assessment Service hat folgende Aufgaben:

* Durchsucht Umgebungen und deckt Leistungsengpässe, Ineffizienzen und Risiken auf.
* Analysiert Inhaltsstrukturen wie Blueprints, Live Copies und Kundenkonfigurationen.
* Erkennt veraltete Abhängigkeiten, einschließlich AEM SDK und Drittanbieterbibliotheken.
* Kennzeichnet Probleme mit der Code-Qualität, z. B. falsche Anmerkungen und ineffiziente Muster.
* Stellt verwertbare Anleitungen in Dashboards bereit (z. B. im Action Center).
* Fördert die proaktive Behebung, um die Systemleistung zu verbessern.

Bei jeder Ausführung werden Probleme nach Schweregrad, Links zu Anleitungen und empfohlenen Fehlerbehebungen aufgelistet und ein PDF-Export des Berichts unterstützt. Sie können die Ansicht **Neuester Bericht** für den aktuellen Status und **vergangene Berichte)**, um Ausführungen zu vergleichen.

Regeldefinitionen und Details zur [ finden Sie unter ](#ha-patterns)Konsistenzbewertungsmuster“.

## Zugriff auf die Seite „Konsistenzbewertung“ {#access-health-assessment}

1. Melden Sie sich bei Cloud Manager unter [experience.adobe.com](https://experience.adobe.com) an.
1. Klicken Sie **Abschnitt „Schnellzugriff** auf **Experience Manager**.
1. Klicken Sie im linken Bedienfeld auf **Cloud Manager**.
1. Wählen Sie die gewünschte Organisation aus. Die Abbildung unten dient zur Veranschaulichung. Wählen Sie Ihren eigenen Organisationsnamen aus.

   ![Organisation in Cloud Manager auswählen](/help/implementing/cloud-manager/reports/assets/ha-org.png)

1. Klicken Sie in **Konsole** Meine Programme“ auf das Programm, für das Sie den Bericht anzeigen möchten.

1. Führen Sie eine der folgenden Aktionen aus:
   * Klicken Sie auf **Karte** Umgebungen“ rechts neben einem Umgebungsnamen auf das Symbol ![Auslassungspunkte oder Mehr](https://spectrum.adobe.com/static/icons/ui_18/More.svg) und wählen Sie dann **Konsistenzbewertung** aus dem Menü aus.

     ![Auswahl der Konsistenzbewertung aus dem Menü mit den Auslassungspunkten auf der Karte Umgebungen](/help/implementing/cloud-manager/reports/assets/ha-myprograms-environments-card.png)

   * Klicken Sie im linken Menü unter **Services** auf ![Datensymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Data_18_N.svg) **Umgebungen**. Klicken Sie auf der Seite „Umgebungen“ rechts neben einem Umgebungsnamen auf ![Ellipsensymbol oder Mehr-Symbol](https://spectrum.adobe.com/static/icons/ui_18/More.svg) und wählen Sie dann **** aus dem Menü aus.

     ![Auswahl der Konsistenzbewertung aus dem Menü mit den Auslassungspunkten auf der Seite Umgebungen](/help/implementing/cloud-manager/reports/assets/ha-environments-page.png)

## Neuen Bericht für eine ausgewählte Umgebung ausführen {#run-report}

1. [Zugriff auf die Seite „Konsistenzbewertung“](#access-health-assessment).
1. Bestätigen Sie oben rechts auf der Seite **Konsistenzbewertung** die Zielumgebung, die Sie bewerten möchten.

   Wenn die Umgebung falsch ist, klicken Sie auf ![Pfeil nach unten oder Dropdown-Menü, um eine andere Umgebung auszuwählen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ChevronDown_18_N.svg) um die richtige Umgebung aus der Liste auszuwählen.

1. Klicken Sie auf **Bericht ausführen**.

   ![Klicken Sie auf der Seite „Konsistenzbewertung“ auf die Schaltfläche „Neuen Bericht erstellen“](/help/implementing/cloud-manager/reports/assets/ha-run-report.png)

   Während ein Bericht für die ausgewählte Umgebung ausgeführt wird, bleibt **Bericht ausführen** deaktiviert, bis er abgeschlossen ist.

   ![Bericht wird gerade ausgeführt](/help/implementing/cloud-manager/reports/assets/ha-running-report.png)

   Nach Abschluss des Berichts wird der Bericht auf der Seite **Gesundheitsbewertung** im Abschnitt **Neuester Bericht** angezeigt.

## Anzeigen des neuesten Berichts {#view-latest-report}

* Lesen Sie auf **Seite &quot;**&quot; den Abschnitt **Neuester Bericht** mit den folgenden Informationen:

   * Ergebnisse des letzten Durchgangs.
   * Ausführungsdatum und -uhrzeit
   * Gesamtzahl der Probleme.
   * Die wichtigsten kritischen Probleme
   * Aktionen: **[Details anzeigen](#view-report-details)** oder **[PDF herunterladen](#download-pdf-report)** aller Probleme

  ![Die Seite Neueste Bewertung im Anschluss an die Erstellung eines neuen Berichts für eine ausgewählte Umgebung](/help/implementing/cloud-manager/reports/assets/ha-latest-report-page.png)

### Anzeigen der neuesten Berichtsdetails {#view-report-details}

* Klicken Sie auf **Seite &quot;**&quot; rechts neben dem Titel **Neuester Bericht** auf das Symbol ![Auslassungspunkte oder Mehr“](https://spectrum.adobe.com/static/icons/ui_18/More.svg) und klicken Sie dann auf **Details anzeigen** oder **Herunterladen**.

  Die **Details anzeigen** Option zeigt Folgendes an:

   * Eine umfassende Liste von Problemen.
   * Möglichkeit, Ergebnisse und Problembeschreibungen anzuzeigen.
   * Möglichkeit, die Dokumentation mit potenziellen Fehlerbehebungen anzuzeigen.

     ![Problembeschreibungen und -erkennung](/help/implementing/cloud-manager/reports/assets/ha-issue-descriptions-and-findings.png)

   * Die **Download**-Option bietet Ihnen die Möglichkeit, individuelle Problemberichte in PDF herunterzuladen.

     ![Herunterladen von PDF mit individuellen Problemberichten](/help/implementing/cloud-manager/reports/assets/ha-details-page-doc-links.png)


### PDF des gesamten Berichts herunterladen {#download-pdf-report}

* Klicken Sie oben rechts auf der Berichtseite auf &quot;**&quot;**.

  Es wird eine ZIP-Datei generiert, die PDFs für alle in diesem Bericht festgestellten Probleme enthält.

  ![Laden Sie PDF mit allen in einem Bericht gefundenen Problemen herunter](/help/implementing/cloud-manager/reports/assets/ha-download-pdf.png)


## Überprüfen früherer Berichte {#review-past-reports}

Überprüfen Sie auf **Seite &quot;**&quot; den Abschnitt **Vergangene Berichte** mit den folgenden Informationen:

* Details eines vorherigen Berichts anzeigen.
* Das Datum jedes Durchgangs anzeigen.
* Laden Sie eine PDF für einen beliebigen Bericht herunter.
* Sortieren Sie nach Datum, Anzahl der Probleme oder Umgebung.

![Vergangene Berichte überprüfen](/help/implementing/cloud-manager/reports/assets/ha-past-reports.png)

* Klicken Sie rechts neben der Überschrift **Frühere Berichte** auf ![Pfeil nach unten oder Dropdown-Menü, um eine andere Umgebung auszuwählen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ChevronDown_18_N.svg), um vergangene Berichte nach Datum zu sortieren.
* Ganz rechts neben einem Bericht auf das Symbol mit ![ Auslassungspunkten oder das Symbol Mehr ](https://spectrum.adobe.com/static/icons/ui_18/More.svg) und dann auf **Details anzeigen** oder **Herunterladen**.


## Muster der Gesundheitsbewertung {#ha-patterns}

Im Folgenden finden Sie eine vollständige Liste der Anti-Muster und -Probleme, die von Health Assessment in AEM as a Cloud Service erkannt werden. In der Tabelle werden Elemente in drei Typen unterteilt: Inhaltsanalyse, Codeanalyse und Anti-Muster von Cloud Service Optimizer mit jeweils einer Erklärung.

| Mustername | Kategorie | Typ | Beschreibung | Auswirkungen | Automatisch korrigiert? |
| --- | --- | --- | --- | --- | --- |
| Benutzerdefinierte AEM-Gruppen mit direkten Benutzerhinzufügungen | Sicherheit | Inhaltsanalyse | Benutzende haben AEM-Gruppen direkt hinzugefügt, anstatt IMS-Gruppen als Mitglieder hinzuzufügen. | Berechtigungsverwaltung und Sicherheitsverwaltung können kompliziert werden. [IMS-Unterstützung](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/security/ims-support) | Nein |
| Fehlender JCR-Inhaltsknoten in Seiten | Repository-Struktur | Inhaltsanalyse | Fehlender `jcr:content` auf der Seite. | Funktionale Einschränkungen in Experience Manager as a Cloud Service. [Mustererkennung - ACV](https://experienceleague.adobe.com/de/docs/experience-manager-pattern-detection/table-of-contents/acv) | Nein |
| Fehlender Sling-Ressourcentyp auf Seiten | Repository-Struktur | Inhaltsanalyse | Fehlende `sling:resourceType` auf der Seite. | Funktionale Einschränkungen in Experience Manager as a Cloud Service. [Mustererkennung - ACV](https://experienceleague.adobe.com/de/docs/experience-manager-pattern-detection/table-of-contents/acv) | Nein |
| Seiten mit übermäßiger Knotenanzahl | Leistung | Inhaltsanalyse | Seiten enthalten eine große Anzahl von Knoten in ihrer Struktur. | Langsame Seitenladezeiten und schlechtes Benutzererlebnis. [Mustererkennung - PCX](https://experienceleague.adobe.com/de/docs/experience-manager-pattern-detection/table-of-contents/pcx) | Nein |
| Zu viele laufende Workflow-Instanzen | Leistung | Inhaltsanalyse | Zu viele Workflow-Instanzen werden ausgeführt. | Verschlechterung der Gesamtsystemleistung. [Wartungsaufgaben](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/operations/maintenance) | Nein |
| Bereinigung von abgeschlossenen Workflow-Instanzen aufgehoben | Leistung | Inhaltsanalyse | Ältere abgeschlossene Workflow-Instanzen werden nicht gelöscht. | Geringere Systemeffizienz und höhere Speicherkosten. [Wartungsaufgaben](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/operations/maintenance) | Nein |
| Statistiken zur Verwendung von Inhaltsfragmenten | Statistiken | Inhaltsanalyse | Verfolgt die Anzahl der verwendeten Inhaltsfragmente. | Nicht zutreffend | Nicht zutreffend |
| Nutzungsstatistiken des Inhaltsfragmentmodells | Statistiken | Inhaltsanalyse | Verfolgt die Anzahl der verwendeten Inhaltsfragmentmodelle. | Nicht zutreffend | Nicht zutreffend |
| MSM - Große Anzahl von Blueprints | Statistiken | Inhaltsanalyse | Verfolgt die Anzahl der Blueprints. | Dies kann die Komplexität des Managements erhöhen und die Inhaltsverwaltung erschweren. | Nicht zutreffend |
| MSM-Seiten pro Blueprint | Statistiken | Inhaltsanalyse | Verfolgt die Anzahl der Seiten pro Blueprint. | Dies kann die Komplexität des Managements erhöhen und die Inhaltsverwaltung erschweren. | Nicht zutreffend |
| Zu viele MSM-Live Copies | Statistiken | Inhaltsanalyse | Verfolgt die Anzahl der Live Copies. | Dies kann zu Leistungsproblemen während Rollouts führen und die Inhaltssynchronisierung komplizieren. | Nicht zutreffend |
| Zu viele MSM-Live Copies pro Blueprint | Statistiken | Inhaltsanalyse | Verfolgt die Anzahl der Live Copies pro Blueprint. | Dies kann zu Leistungsproblemen während Rollouts führen und die Inhaltssynchronisierung komplizieren. | Nicht zutreffend |
| Anzahl der Assets | Statistiken | Inhaltsanalyse | Verfolgt die Anzahl der Assets. | Nicht zutreffend | Nicht zutreffend |
| Anzahl der Sites | Statistiken | Inhaltsanalyse | Verfolgt die Anzahl der Sites. | Nicht zutreffend | Nicht zutreffend |
| Anzahl der Forms | Statistiken | Inhaltsanalyse | Verfolgt die Anzahl der Formulare. | Nicht zutreffend | Nicht zutreffend |
| Formularfragmente | Statistiken | Inhaltsanalyse | Verfolgt die Anzahl der Formularfragmente. | Nicht zutreffend | Nicht zutreffend |
| Interaktionskommunikation | Statistiken | Inhaltsanalyse | Verfolgt die Anzahl der Interaktionen mit der Formularkommunikation. | Nicht zutreffend | Nicht zutreffend |
| FDMs | Statistiken | Inhaltsanalyse | Verfolgt die Anzahl der Formulardatenmodelle. | Nicht zutreffend | Nicht zutreffend |
| Veraltete Abhängigkeiten | Abhängigkeiten | Codeanalyse | Zeigt veraltete Abhängigkeiten im Kunden-Repository an. | Inkompatibilität mit neueren AEM-Versionen; potenzielle Sicherheitslücken. | Nein |
| AEM SDK-Versionskonflikt | Abhängigkeiten | Codeanalyse | Versionen älter als (n-2) im Vergleich zur Cloud Manager-Umgebungsversion. | Dies kann Build-Fehler in Cloud Manager und Probleme in lokalen Entwicklungsumgebungen verursachen. | Nein |
| Veraltete Mockito-Core-Abhängigkeit | Abhängigkeiten | Codeanalyse | Versionen unter 4.x.x gelten für AEM as a Cloud Service als veraltet. | Dies kann Build-Fehler in Cloud Manager und Probleme in lokalen Entwicklungsumgebungen verursachen. | Nein |
| Nicht unterstützte Anmerkungen | Abhängigkeiten | Codeanalyse | Nicht unterstützte Anmerkungen im Cloud Manager-Repository des Kunden. | Potenzielle Anwendungsfehler und verminderte Leistung. | Nein |
| @Inject in Sling-Modellen | Abhängigkeiten | Codeanalyse | Veraltete `@Inject`. | Verringerte Anwendungsleistung aufgrund des Overheads für die Injektionsauflösung. | Nein |
| Ausgehende HTTP-Anfragen | Leistung | Cloud Service Optimizer - Antimuster | Problematische Verwendung im Anfragekontext, hohe Zeitüberschreitungen oder das Schließen von Verbindungen. | Verschlechterung der Gesamtsystemleistung und mögliche Ausfälle. | Ja |
| Langsame Abfragen | Leistung | Cloud Service Optimizer - Antimuster | Langsame Abfragen im Kunden-Code. | Beeinträchtigte Systemleistung und potenzielle Zeitüberschreitungen. | Ja |

### Kategorien {#ha-patterns-categories}

| Kategorie | Beschreibung |
| --- | --- |
| Sicherheit | Muster im Zusammenhang mit Sicherheitspraktiken, Benutzerverwaltung und Zugriffssteuerung. |
| Leistung | Muster, die sich auf die Anwendungs- und Systemleistung auswirken. |
| Repository-Struktur | Muster in Bezug auf JCR-Repository-Organisation und -Struktur. |
| Abhängigkeiten | Muster in Bezug auf Codeabhängigkeiten und Versionsverwaltung. |
| Statistiken | Muster, die Nutzungsstatistiken und Metriken darstellen. |



