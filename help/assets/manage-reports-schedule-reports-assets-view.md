---
title: Verwalten von Berichten in Assets-Ansicht
description: Greifen Sie auf die Daten im Abschnitt „Berichte“ der Assets-Ansicht zu, um die Produkt- und Funktionsnutzung zu bewerten und Erkenntnisse zu wichtigen Erfolgsmetriken zu erhalten.
exl-id: 26d0289e-445a-4b8e-a5a1-b02beedbc3f1
feature: Asset Insights, Asset Reports
role: User, Admin, Developer
source-git-commit: 1103ed766eb17aa984831b6213e7e15671ead536
workflow-type: tm+mt
source-wordcount: '1200'
ht-degree: 38%

---

# Verwalten von Berichten {#manage-reports}

| [Best Practices für die Suche](/help/assets/search-best-practices.md) | [Best Practices für Metadaten](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [Dynamic Media mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md) | [Entwicklerdokumentation zu AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

Das Asset-Reporting bietet Admins Einblicke in die Aktivitäten in der Ansichtsumgebung von Adobe Experience Manager Assets. Diese Daten liefern nützliche Informationen darüber, wie Benutzende mit Inhalten und dem Produkt interagieren. Alle Benutzenden können auf das Insights-Dashboard zugreifen, und diejenigen, die dem Produktprofil der Admins zugewiesen sind, können benutzerdefinierte Berichte erstellen.

## Zugreifen auf Berichte {#access-reports}

Alle Benutzenden, die dem Produktprofil Assets-Ansicht-Admins zugeordnet sind, können in der Assets-Ansicht auf das Insights-Dashboard zugreifen oder benutzerdefinierte Berichte erstellen.

Navigieren Sie unter **[!UICONTROL Einstellungen]** zu **[!UICONTROL Berichte]**, um auf Berichte zuzugreifen.

![Berichte](assets/reports.png)

<!--
In the **[!UICONTROL Reports]** screen, various components are shown in the tabular format which includes the following:

* **Title**: Title of the report
* **Type**: Determines whether the report is uploaded or downloaded to the repository
* **Description**: Provide details of the report that was given during uploading/downloading the report
* **Status**: Determines whether the report is completed, under progress, or deleted.
* **Author**: Provides email of the author who has uploaded/downloaded the report.
* **Created**: Gives information of the date when the report was generated.
-->

## Erstellen eines Berichts {#create-report}

Die AEM Assets-Ansichtsumgebung bietet umfassende Berichterstellungsfunktionen über das Berichte-Dashboard. Mit dieser Funktion können Benutzer CSV-Berichte erstellen und herunterladen, die Details zu Asset-Uploads und -Downloads innerhalb eines bestimmten Zeitraums anzeigen, der von ein- bis täglichen, wöchentlichen, monatlichen oder jährlichen Intervallen reicht.

**So erstellen Sie einen Bericht:**

1. Navigieren Sie zu **Berichte** und klicken Sie auf **Bericht erstellen** (oben rechts). Im Dialogfeld **Bericht erstellen** werden die folgenden Felder angezeigt:
   ![create-report](/help/assets/assets/executed-reports1.svg)

   **Auf der Registerkarte &quot;Konfiguration&quot;:**

   1. **Berichtstyp:** Wählen Sie zwischen dem Upload- und dem Download-Typ aus.
   1. **Titel:** Fügen Sie dem Bericht einen Titel hinzu.
   1. **Beschreibung:** Fügen Sie dem Bericht eine optionale Beschreibung hinzu.
   1. **Ordnerpfad auswählen:** Wählen Sie einen Ordnerpfad aus, um den Bericht der hochgeladenen und heruntergeladenen Assets in diesem bestimmten Ordner zu generieren. Wenn Sie beispielsweise den Bericht mit Assets benötigen, die in einen Ordner hochgeladen wurden, geben Sie den Pfad zu diesem Ordner an.
   1. **Datumsintervall auswählen:** Wählen Sie den Datumsbereich aus, um die Upload- oder Download-Aktivität im Ordner anzuzeigen.
   <br>

   >[!NOTE]
   >
   > Die Assets-Ansicht konvertiert alle lokalen Zeitzonen in die koordinierte Weltzeit (UTC).

   **Auf der Registerkarte &quot;Spalten&quot;:** Wählen Sie die Spaltennamen aus, die im Bericht angezeigt werden sollen. In der folgenden Tabelle wird die Verwendung aller Spalten erläutert:

   <table>
    <tbody>
     <tr>
      <th><strong>Spaltenname</strong></th>
      <th><strong>Beschreibung</strong></th>
      <th><strong>Berichtstyp</strong></th>
     </tr>
     <tr>
      <td>Titel</td>
      <td>Der Titel des Assets.</td>
      <td>Hochladen und Herunterladen</td>
     </tr>
     <tr>
      <td>Pfad</td>
      <td>Der Ordnerpfad, in dem das Asset in der Assets-Ansicht verfügbar ist.</td>
      <td>Hochladen und Herunterladen</td>
     </tr>
     <tr>
      <td>MIME-Typ</td>
      <td>Der MIME-Typ für das Asset.</td>
      <td>Hochladen und Herunterladen</td>
     </tr>
     <tr>
      <td>Größe</td>
      <td>Die Größe des Assets in Bytes.</td>
      <td>Hochladen und Herunterladen</td>
     </tr>
     <tr>
      <td>Heruntergeladen von</td>
      <td>Die E-Mail-ID des Benutzers, der das Asset heruntergeladen hat.</td>
      <td>Herunterladen</td>
     </tr>
     <tr>
      <td>Herunterladen-Datum</td>
      <td>Das Datum, an dem die Aktion zum Herunterladen des Assets durchgeführt wurde.</td>
      <td>Herunterladen</td>
     </tr>
     <tr>
      <td>Autor</td>
      <td>Der Autor des Assets.</td>
      <td>Hochladen und Herunterladen</td>
     </tr>
     <tr>
      <td>Erstellungsdatum</td>
      <td>Das Datum, an dem das Asset in die Assets-Ansicht hochgeladen wurde.</td>
      <td>Hochladen und Herunterladen</td>
     </tr>
     <tr>
      <td>Änderungsdatum</td>
      <td>Das Datum der letzten Änderung des Assets.</td>
      <td>Hochladen und Herunterladen</td>
     </tr>
     <tr>
      <td>Abgelaufen</td>
      <td>Der Ablaufstatus des Assets.</td>
      <td>Hochladen und Herunterladen</td>
     </tr>
     <tr>
      <td>Heruntergeladen von Benutzername</td>
      <td>Der Name der Benutzerin oder des Benutzers, die/der das Asset heruntergeladen hat.</td>
      <td>Herunterladen</td>
     </tr>           
    </tbody>
   </table>

## Vorhandenen Bericht anzeigen und herunterladen {#View-and-download-existing-report}

Vorhandene Berichte werden auf der Registerkarte **Ausgeführte Berichte** angezeigt. Klicken Sie auf &quot;**Berichte**&quot;und wählen Sie &quot;**Ausgeführte Berichte**&quot;, um alle erstellten Berichte mit dem Status &quot;**Abgeschlossen**&quot;anzuzeigen und anzugeben, dass sie zum Herunterladen bereit sind. Um den Bericht im CSV-Format herunterzuladen oder zu löschen, wählen Sie die Berichtszeile aus. Wählen Sie dann **CSV herunterladen** oder **Löschen** aus.
![ Anzeigen und Herunterladen vorhandener Berichte](/help/assets/assets/view-download-existing-report.png)

## Planen eines Berichts {#schedule-report}

In der Benutzeroberfläche der AEM Assets-Ansicht richtet **Bericht planen** eine automatische Generierung von Berichten in bestimmten zukünftigen Intervallen ein, z. B. täglich, wöchentlich, monatlich oder jährlich. Diese Funktion hilft, die wiederkehrenden Berichtsanforderungen zu optimieren und stellt zeitnahe Datenaktualisierungen sicher. Während **Bericht erstellen** Berichte für vergangene Daten generiert. Abgeschlossene Berichte werden unter **Ausgeführte Berichte** aufgelistet und bevorstehende Berichte finden Sie unter **Terminierte Berichte**.

Gehen Sie wie folgt vor, um einen Bericht zu planen:

1. Klicken Sie im linken Bereich auf Berichte und dann oben rechts auf Bericht erstellen .
1. Im Dialogfeld &quot;Bericht&quot;werden die folgenden Informationen angezeigt:
   1. **Berichtstyp:** Wählen Sie zwischen dem Upload- und dem Download-Typ aus.
   1. **Titel:** Fügen Sie dem Bericht einen Titel hinzu.
   1. **Beschreibung**: Fügen Sie dem Bericht eine optionale Beschreibung hinzu.
   1. **Ordnerpfad auswählen:** Wählen Sie einen Ordnerpfad aus, um einen Bericht für Assets zu generieren, die in diesen bestimmten Ordner hochgeladen oder von diesem heruntergeladen werden.
   1. Umschalten zwischen **Bericht planen:** Umschalten, um den Bericht für einen späteren Zeitpunkt oder für sein wiederholtes Auftreten zu planen.
      ![Bericht planen](/help/assets/assets/schedule-reports1.svg)

   1. **Häufigkeit auswählen:** Geben Sie das Intervall für die Generierung des Berichts an (z. B. täglich, wöchentlich, monatlich, jährlich oder einmal) und legen Sie Datum und Uhrzeit für die Ausführung des Berichts zusammen mit dem Enddatum für die Wiederholung fest. Wählen Sie für einen einmaligen Bericht den Datumsbereich für den Bericht über den ausgewählten Aktivitätstyp in der AEM Umgebung aus. Wenn Sie beispielsweise einen Bericht zu heruntergeladenen Assets vom 10. bis zum 29. (zukünftigen) eines bestimmten Monats benötigen, wählen Sie diese Daten im Feld **Datumsintervall auswählen** aus.

   >[!NOTE]
   >
   > Die Assets-Ansicht konvertiert alle lokalen Zeitzonen in die koordinierte Weltzeit (UTC).

## Geplante Berichte anzeigen {#view-scheduled-reports}

Geplante Berichte werden systematisch organisiert auf der Registerkarte **Terminierte Berichte** angezeigt. Alle abgeschlossenen Berichte für jeden terminierten Bericht werden in einem einzigen Berichtsordner gespeichert. Klicken Sie auf![Erweitern Sie Reduzieren](/help/assets/assets/expand-icon1.svg) , um die abgeschlossenen Berichte anzuzeigen. Wenn Sie beispielsweise einen täglichen Bericht geplant haben, werden alle abgeschlossenen Berichte in einem Ordner zusammengefasst. Diese Organisation vereinfacht die Navigation und Erkennung von Berichten. Um terminierte Berichte anzuzeigen, klicken Sie auf **Berichte** und dann auf **Terminierte Berichte**. Alle terminierten Berichte werden angezeigt, wobei ihr Status fortlaufend oder abgeschlossen ist. Die abgeschlossenen Berichte können heruntergeladen werden.\
![terminierter Bericht](/help/assets/assets/scheduled-reports-tab.png)

## Terminierte Berichte bearbeiten und abbrechen {#edit-cancel-scheduled-reports}

1. Navigieren Sie zur Registerkarte **Terminierte Berichte** .
1. Wählen Sie die Berichtszeile aus.
1. Klicken Sie auf **Bearbeiten**.
1. Klicken Sie auf **Zeitplan abbrechen** und dann auf **Bestätigen**, um den terminierten Bericht abzubrechen. Bei abgebrochenen Berichten wird die nächste Laufzeit leer und der Status zeigt abgebrochen an.
   ![terminierten Bericht bearbeiten und abbrechen](/help/assets/assets/cancel-edit-scheduled-reports.png)

### Zeitplan fortsetzen {#resume-schedule}

Um den abgebrochenen Zeitplan wieder aufzunehmen, wählen Sie die Berichtszeile aus und klicken Sie auf **Zeitplan fortsetzen**. Nach der Wiederaufnahme werden die nächsten Laufzeiteinträge erneut angezeigt und der Status zeigt &quot;Laufend&quot;an.
![Zeitplan für die Wiederaufnahme ](/help/assets/assets/resume-schedule.png)

>[!NOTE]
>
> Wenn Sie einen abgebrochenen Bericht vor dem geplanten Enddatum fortsetzen, werden automatisch die Berichte vom Abbruchsdatum bis zum Wiederaufnahmedatum generiert.

## Anzeigen von Insights {#view-live-statistics}

In der Assets-Ansicht können Sie mit dem Insights-Dashboard Echtzeitdaten für Ihre Assets Essentials-Umgebung anzeigen. Sie können Echtzeit-Ereignismetriken für die letzten 30 Tage oder für die letzten 12 Monate anzeigen.

<!--![Toolbar options when you select an asset](assets/assets-view-live-statistics.png)-->

Klicken Sie auf **[!UICONTROL Erkenntnisse]** im linken Navigationsbereich, um die folgenden automatisch generierten Diagramme anzuzeigen:

* **Downloads**: Die Anzahl der Assets, die in den letzten 30 Tagen oder 12 Monaten aus der Assets-Ansichtsumgebung heruntergeladen wurden, dargestellt als Liniendiagramm.
  ![insights-downloads](/help/assets/assets/insights-downloads2341.svg)

* **Uploads**: Die Anzahl der Assets, die in den letzten 30 Tagen oder 12 Monaten in die Assets-Ansichtsumgebung hochgeladen wurden, dargestellt als Liniendiagramm.
  ![insights-uploads](/help/assets/assets/insights-uplods2.svg)
  <!--* **Asset Count by Size**: The division of count of assets based on their range of various sizes from 0 MB to 100 GB.-->

* **Speichernutzung**: Darstellung der Speichernutzung in Byte für die Assets-Ansicht-Umgebung mithilfe eines Balkendiagramms.
  ![insights-uploads](/help/assets/assets/insights-storage-usage1.svg)
  <!--* **Delivery**: The graph depicts the count of assets as the delivery dates.-->

<!--* **Asset Count by Asset Type**: Represents count of various MIME types of the available assets. For example, application/zip, image/png, video/mp4, application/postscripte.-->

* **Top-Suchvorgänge**: Zeigt die in den letzten 30 Tagen oder 12 Monaten am häufigsten gesuchten Begriffe zusammen mit der Anzahl der Suchvorgänge dieser Begriffe in Ihrer Assets-Ansichtsumgebung an, dargestellt in tabellarischem Format.
  ![insights-uploads](/help/assets/assets/insights-top-search.svg)
  <!--
   ![Insights](assets/insights1.png)
   ![Insights](assets/insights2.png)
   -->
* **Asset-Anzahl nach Größe:** Segmentiert die gesamte Asset-Anzahl in Ihrer Assets-Ansicht-Umgebung in unterschiedliche Größenbereiche und hebt die Anzahl und den Prozentsatz der Assets in jedem Größenbereich hervor, dargestellt durch ein Ringdiagramm.
  ![insights-assets-count-by-size](/help/assets/assets/insights-assets-count-by-size.svg)
* **Asset-Anzahl nach Asset-Typ:** Segmentiert die Gesamtanzahl der Assets in Ihrer Assets-Ansichtsumgebung und hebt die Anzahl und den Prozentsatz der Assets anhand ihrer Dateitypen hervor, dargestellt durch ein Ringdiagramm.
  ![insights-assets-count-by-size](/help/assets/assets/insights-assest-count-by-asset-type1.svg)