---
title: Verwalten von Berichten in Assets-Ansicht
description: Greifen Sie auf die Daten im Abschnitt „Berichte“ der Assets-Ansicht zu, um die Produkt- und Funktionsnutzung zu bewerten und Erkenntnisse zu wichtigen Erfolgsmetriken zu erhalten.
exl-id: 26d0289e-445a-4b8e-a5a1-b02beedbc3f1
feature: Asset Insights, Asset Reports
role: User, Admin, Developer
source-git-commit: c92fc95d7f2774b24664b457bf785120945fc966
workflow-type: tm+mt
source-wordcount: '1540'
ht-degree: 100%

---

# Verwalten von Berichten {#manage-reports}

| [Best Practices für die Suche](/help/assets/search-best-practices.md) | [Best Practices für Metadaten](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [Dynamic Media mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md) | [Entwicklerdokumentation zu AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

Das Asset-Reporting bietet Admins Einblicke in die Aktivitäten in der Ansichtsumgebung von Adobe Experience Manager Assets. Diese Daten liefern nützliche Informationen darüber, wie Benutzende mit Inhalten und dem Produkt interagieren. Alle Benutzenden können auf das Insights-Dashboard zugreifen, und diejenigen, die dem Produktprofil der Admins zugewiesen sind, können benutzerdefinierte Berichte erstellen.

## Zugreifen auf Berichte {#access-reports}

Alle Benutzenden, die dem Produktprofil „AEM-Admins“ zugeordnet sind, können in der Assets-Ansicht auf das Insights-Dashboard zugreifen oder benutzerdefinierte Berichte erstellen.

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

Die AEM Assets-Ansicht-Umgebung bietet über das Berichte-Dashboard umfassende Berichtsfunktionen. Mit dieser Funktion können Benutzende CSV-Berichte erstellen und herunterladen, die Details zu Asset-Uploads und -Downloads innerhalb eines bestimmten Zeitraums angeben. Die Intervalle können einmalig, täglich, wöchentlich, monatlich oder jährlich sein.

**So erstellen Sie einen Bericht:**

1. Navigieren Sie zu **Berichte** und klicken Sie auf **Bericht erstellen** (oben rechts). Im Dialogfeld **Bericht erstellen** werden die folgenden Felder angezeigt:
   ![create-report](/help/assets/assets/executed-reports1.svg)

   **Auf der Registerkarte „Konfiguration“:**

   1. **Berichtstyp:** Wählen Sie den Typ [!UICONTROL Upload], [!UICONTROL Download] oder [Dynamic Media Delivery Report](#dynamic-media-delivery-reports) aus.
   1. **Titel:** Fügen Sie dem Bericht einen Titel hinzu.
   1. **Beschreibung:** Fügen Sie dem Bericht eine optionale Beschreibung hinzu.
   1. **Ordnerpfad auswählen:** Wählen Sie einen Ordnerpfad aus, um den Bericht der hochgeladenen und heruntergeladenen Assets in diesem bestimmten Ordner zu generieren. Wenn Sie beispielsweise den Bericht der Assets benötigen, die in einen Ordner hochgeladen wurden, geben Sie den Pfad zu diesem Ordner an.
   1. **Datumsintervall auswählen:** Wählen Sie den Datumsbereich aus, für den die Upload- oder Download-Aktivität im Ordner angezeigt werden soll.
   <br>

   >[!NOTE]
   >
   > Die Assets-Ansicht konvertiert alle lokalen Zeitzonen in die koordinierte Weltzeit (UTC).

   **Auf der Registerkarte „Spalten“:** Wählen Sie die Spaltennamen aus, die im Bericht angezeigt werden sollen. In der folgenden Tabelle wird die Verwendung aller Spalten erläutert:

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
      <td>Hochladen, Herunterladen und Dynamic Media-Bereitstellung</td>
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
     <tr>
      <td>Referrer</td>
      <td>Die URL, unter der das Asset bereitgestellt bzw. einbezogen wird</td>
      <td>Dynamic Media-Bereitstellung</td>
     </tr>  
     <tr>
      <td>Treffer</td>
      <td>Die Anzahl der Bereitstellungen des Assets (Bereitstellungszählung)</td>
      <td>Dynamic Media-Bereitstellung</td>
     </tr>          
    </tbody>
   </table>

## Dynamic Media-Bereitstellungsberichte {#dynamic-media-delivery-reports}

Hier erhalten Sie Einblicke in die Bereitstellung von Assets, die mit Dynamic Media bereitgestellt werden, mit der Anzahl der Bereitstellungen auf Asset-Ebene, Referrer-Informationen, dem Asset-Pfad in AEM Assets und der eindeutigen Asset-ID. Berichte können entweder für alle Assets generiert werden, die über Dynamic Media für das AEM Assets-Repository bereitgestellt werden, oder für eine bestimmte Ordnerhierarchie in AEM Assets. Mithilfe von Dynamic Media-Bereitstellungsberichten können Sie den ROI der bereitgestellten Assets oder die Kanalleistung messen und fundierte Asset-Management-Aufgaben für Assets durchführen.

<!--
>[!NOTE]
> 
>To get early access to the Dynamic Media Delivery Report on your Dynamic Media account, [create and submit an Adobe Customer Support case](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html).
-->

### Voraussetzungen {#prereqs-dynamic-media-delivery-reports}

Sie sollten über eine Dynamic Media-Lizenz verfügen, um diesen Bericht zu erstellen und zu verwenden.

>[!IMPORTANT]
> 
>* Berichte werden für Assets bereitgestellt, die über Dynamic Media geliefert werden.
>* Berichte werden für die ersten 1 Million Zeilen erstellt. Wenn Sie alle Dateien innerhalb dieses Limits erfassen möchten, können Sie für kleinere Ordner die Referrer-Spalte mit einbeziehen.
>* Berichte können nur für die letzten 3 Monate erstellt werden.

### Erstellen eines Dynamic Media-Bereitstellungsberichts{#create-dynamic-media-delivery-report}

1. Erstellen Sie einen Dynamic Media-Bereitstellungsbericht mithilfe der Schritte, die unter [Erstellen eines Berichts](#create-report) beschrieben sind.

1. Wählen Sie **[!UICONTROL Dynamic Media-Bereitstellung]** aus der Dropdown-Liste **[!UICONTROL Berichtstyp]** aus.

   ![Dynamic Media-Bereitstellungsbericht – Dropdown-Liste](assets/dynamic-media-delivery-report-option.png)


1. Auf der Registerkarte **[!UICONTROL Spalten]** können Sie die Spalte **[!UICONTROL Referrer]** auswählen, um sie in Ihren Bericht aufzunehmen.

   ![Referrer](assets/referrer.png)

   Alle Spalten des heruntergeladenen Berichts sind schreibgeschützt, mit Ausnahme der Spalte **Referrer**, die Sie ändern können, um sie in den Bericht ein- oder aus ihm auszuschließen. <!--Choosing a referrer displays the number of visitors received from each referred report that directs traffic to the site. It offers insights into the sources of traffic and the origin of the visitors. Such insights help measure ROI of delivered assets, measure channel performance, and help take informed asset management tasks for assets.-->

### Aktionen, die mit Dynamic Media-Bereitstellungsberichten ausgeführt werden {#actions-performed-dynamic-media-delivery-reports}

Nach dem Erstellen des Berichts können Sie die folgenden Aktionen durchführen:

* **[!UICONTROL Löschen]**: Sie können den ausgewählten Bericht löschen.
* **[!UICONTROL CSV herunterladen]**: Sie können den ausgewählten Bericht im CSV-Format herunterladen. Der heruntergeladene Bericht enthält die Spalten „Name“, „Pfad“, „DynamicMediaID“, „Referrer“ und „Treffer“.
   * Die Spalte **Referrer** führt die URL auf, unter der das Asset bereitgestellt bzw. einbezogen wird.

   * Die Spalte **Treffer** gibt an, wie oft das Asset bereitgestellt wurde (Bereitstellungszählung).

Informationen zum Löschen oder Herunterladen des Dynamic Media-Bereitstellungsberichts als CSV-Datei finden Sie unter [Anzeigen und Herunterladen von vorhandenen Berichten](#View-and-download-existing-report).

![Heruntergeladene CSV-Datei eines Dynamic Media-Bereitstellungsberichts](assets/csv-dynamic-media-delivery-report.png)


## Anzeigen und Herunterladen von vorhandenen Berichten {#View-and-download-existing-report}

Vorhandene Berichte werden auf der Registerkarte **Ausgeführte Berichte** angezeigt. Klicken Sie auf **Berichte** und wählen Sie **Ausgeführte Berichte** aus, um alle erstellten Berichte mit dem Status **Abgeschlossen** anzuzeigen. Dieser Status bedeutet, dass sie zum Herunterladen bereit sind. Um den Bericht im CSV-Format herunterzuladen oder zu löschen, wählen Sie die Berichtszeile aus. Wählen Sie dann **CSV herunterladen** oder **Löschen** aus.
![Anzeigen und Herunterladen von vorhandenen Berichten](/help/assets/assets/view-download-existing-report.png)


## Planen eines Berichts {#schedule-report}

In der AEM Assets-Benutzeroberfläche wird durch **Bericht planen** eine automatische Generierung von Berichten in bestimmten zukünftigen Intervallen eingerichtet, z. B. täglich, wöchentlich, monatlich oder jährlich. Diese Funktion hilft, die wiederkehrenden Berichtsanforderungen zu optimieren, und stellt zeitnahe Datenaktualisierungen sicher. **Bericht erstellen** generiert dagegen Berichte für vergangene Daten. Abgeschlossene Berichte werden unter **Ausgeführte Berichte** aufgelistet, und die anstehenden Berichte finden Sie unter **Geplante Berichte**.

Gehen Sie wie folgt vor, um einen Bericht zu planen:

1. Klicken Sie im linken Bereich auf „Berichte“ und dann oben rechts auf „Bericht erstellen“.
1. Im Dialogfeld „Bericht“ werden die folgenden Informationen angezeigt:
   1. **Berichtstyp:** Wählen Sie zwischen dem Upload- und dem Download-Typ aus.
   1. **Titel:** Fügen Sie dem Bericht einen Titel hinzu.
   1. **Beschreibung**: Fügen Sie dem Bericht eine optionale Beschreibung hinzu.
   1. **Ordnerpfad auswählen**: Wählen Sie einen Ordnerpfad aus, um einen Bericht für Assets zu generieren, die in Zukunft in diesen bestimmten Ordner hochgeladen bzw. aus diesem Ordner heruntergeladen werden.
   1. Umschalter **Bericht planen**: Schalten Sie zwischen den beiden Optionen um, den Bericht entweder für einen späteren Zeitpunkt oder für ein wiederholtes Vorkommen zu planen.
      ![Bericht planen](/help/assets/assets/schedule-reports1.svg)

   1. **Häufigkeit auswählen**: Geben Sie das Intervall für die Generierung des Berichts an (z. B. täglich, wöchentlich, monatlich, jährlich oder einmalig) und legen Sie Datum und Uhrzeit für die Ausführung des Berichts zusammen mit dem Enddatum für das Intervall fest. Wählen Sie für einen einmaligen Bericht den Datumsbereich für den Bericht über den ausgewählten Aktivitätstyp in der AEM-Umgebung aus. Wenn Sie beispielsweise einen Bericht zu den vom 10. bis zum 29. (Datumsangaben in der Zukunft) eines bestimmten Monats heruntergeladenen Assets benötigen, wählen Sie diese Datumsangaben im Feld **Datumsintervall auswählen** aus.

   >[!NOTE]
   >
   > Die Assets-Ansicht konvertiert alle lokalen Zeitzonen in die koordinierte Weltzeit (UTC).

## Anzeigen geplanter Berichte {#view-scheduled-reports}

Geplante Berichte werden systematisch organisiert auf der Registerkarte **Geplante Berichte** angezeigt. Alle abgeschlossenen Berichte für jeden geplanten Bericht werden in einem einzigen Berichtsordner gespeichert. Klicken Sie auf ![Ein-/Ausblenden](/help/assets/assets/expand-icon1.svg), um die abgeschlossenen Berichte anzuzeigen. Wenn Sie beispielsweise einen täglichen Bericht geplant haben, werden alle abgeschlossenen Berichte in einem Ordner gruppiert. Diese Organisation vereinfacht die Navigation und die Erkennung von Berichten. Um geplante Berichte anzuzeigen, klicken Sie auf **Berichte** und dann auf **Geplante Berichte**. Alle geplanten Berichte werden angezeigt, wobei ihr Status entweder „Laufend“ oder „Abgeschlossen“ ist. Die abgeschlossenen Berichte können heruntergeladen werden.\
![Geplanter Bericht](/help/assets/assets/scheduled-reports-tab.png)

## Bearbeiten und Abbrechen von geplanten Berichten {#edit-cancel-scheduled-reports}

1. Navigieren Sie zur Registerkarte **Geplante Berichte**.
1. Wählen Sie die Berichtszeile aus.
1. Klicken Sie auf **Bearbeiten**.
1. Klicken Sie auf **Zeitplan abbrechen** und dann auf **Bestätigen**, um den geplanten Bericht abzubrechen. Bei abgebrochenen Berichten ist „Zeit der nächsten Ausführung“ leer und der Status ist „Abgebrochen“.
   ![Bearbeiten und Abbrechen eines geplanten Berichts](/help/assets/assets/cancel-edit-scheduled-reports.png)

### Zeitplan fortsetzen {#resume-schedule}

Um den abgebrochenen Zeitplan wieder aufzunehmen, wählen Sie die Berichtszeile aus und klicken Sie auf **Zeitplan fortsetzen**. Nach dem Fortsetzen werden die Einträge für die nächsten Ausführungen erneut angezeigt und der Status ist „Laufend“.
![Zeitplan fortsetzen](/help/assets/assets/resume-schedule.png)

>[!NOTE]
>
> Wenn Sie einen abgebrochenen Bericht vor dem geplanten Enddatum fortsetzen, werden die Berichte vom Abbruchdatum bis zum Fortsetzungsdatum automatisch generiert.

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
* **Asset-Anzahl nach Asset-Typ:** Segmentiert die gesamte Asset-Anzahl in Ihrer Assets-Ansicht-Umgebung und hebt die Anzahl und den Prozentsatz der Assets anhand ihrer Dateitypen hervor, dargestellt durch ein Ringdiagramm.
  ![insights-assets-count-by-size](/help/assets/assets/insights-assest-count-by-asset-type1.svg)