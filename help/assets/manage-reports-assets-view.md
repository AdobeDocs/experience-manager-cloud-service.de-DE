---
title: Verwalten von Berichten in Assets-Ansicht
description: Greifen Sie auf die Daten im Abschnitt „Berichte“ der Assets-Ansicht zu, um die Produkt- und Funktionsnutzung zu bewerten und Erkenntnisse zu wichtigen Erfolgsmetriken zu erhalten.
exl-id: 26d0289e-445a-4b8e-a5a1-b02beedbc3f1
source-git-commit: 6dc6b3e4ec9d6a816d92152cb535cd9a5d56a3b0
workflow-type: tm+mt
source-wordcount: '884'
ht-degree: 88%

---

# Verwalten von Berichten {#manage-reports}

Die Asset-Berichterstellung bietet Administratoren einen Einblick in die Aktivität der Adobe Experience Manager Assets-Ansichtsumgebung. Diese Daten liefern nützliche Informationen darüber, wie Benutzende mit Inhalten und dem Produkt interagieren. Alle Benutzenden können auf das Insights-Dashboard zugreifen, und diejenigen, die dem Produktprofil der Admins zugewiesen sind, können benutzerdefinierte Berichte erstellen.

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

## Anzeigen von Insights {#view-live-statistics}

In der Assets-Ansicht können Sie mit dem Insights-Dashboard Echtzeitdaten für Ihre Assets Essentials-Umgebung anzeigen. Sie können Echtzeit-Ereignismetriken für die letzten 30 Tage oder für die letzten 12 Monate anzeigen.

<!--![Toolbar options when you select an asset](assets/assets-essentials-live-statistics.png)-->

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

* **Asset-Anzahl nach Größe:** Segmentiert die gesamte Asset-Anzahl in Ihrer Assets-Ansichtsumgebung in unterschiedliche Größenbereiche, wodurch die Anzahl und der Prozentsatz der Assets in jedem Größenbereich hervorgehoben werden, die mithilfe eines Ringdiagramms dargestellt werden.
  ![insights-assets-count-by-size](/help/assets/assets/insights-assets-count-by-size.svg)
* **Asset-Anzahl nach Asset-Typ:** Segmentiert die Gesamtanzahl der Assets in Ihrer Assets-Ansichtsumgebung und hebt die Anzahl und den Prozentsatz der Assets anhand ihrer Dateitypen hervor, dargestellt durch Ringdiagramm.
  ![insights-assets-count-by-size](/help/assets/assets/insights-assest-count-by-asset-type1.svg)

## Erstellen eines Herunterladen-Berichts {#create-download-report}

So erstellen Sie einen Herunterladen-Bericht:

1. Navigieren Sie zu **[!UICONTROL Einstellungen]** > **[!UICONTROL Berichte]** und klicken Sie auf **[!UICONTROL Bericht erstellen]**.

1. Gehen Sie zur Registerkarte [!UICONTROL Konfiguration] und spezifizieren Sie den Berichtstyp als **[!UICONTROL Herunterladen]**.

1. Geben Sie einen Titel und optional eine Beschreibung für den Bericht an.

1. Wählen Sie über das Feld **[!UICONTROL Ordnerpfad auswählen]** den Ordnerpfad aus, der die Assets enthält, für die der Bericht ausgeführt werden soll.

1. Wählen Sie das Datumsintervall für den Bericht.

   >[!NOTE]
   >
   > Die Assets-Ansicht konvertiert alle lokalen Zeitzonen in die koordinierte Weltzeit (UTC).

1. Im [!UICONTROL Spalten] die Spaltennamen, die Sie im Bericht anzeigen möchten.

1. Klicken Sie auf **[!UICONTROL Erstellen]**.

   ![Bericht herunterladen](assets/download-reports-config.png)

In der folgenden Tabelle wird die Verwendung aller Spalten erläutert, die Sie dem Bericht hinzufügen können:

<table>
    <tbody>
     <tr>
      <th><strong>Spaltenname</strong></th>
      <th><strong>Beschreibung</strong></th>
     </tr>
     <tr>
      <td>Titel</td>
      <td>Der Titel des Assets.</td>
     </tr>
     <tr>
      <td>Pfad </td>
      <td>Der Ordnerpfad, in dem das Asset in der Assets-Ansicht verfügbar ist.</td>
     </tr>
     <tr>
      <td>MIME-Typ</td>
      <td>Der MIME-Typ für das Asset.</td>
     </tr>
     <tr>
      <td>Größe</td>
      <td>Die Größe des Assets in Bytes.</td>
     </tr>
     <tr>
      <td>Heruntergeladen von</td>
      <td>Die E-Mail-ID des Benutzers, der das Asset heruntergeladen hat.</td>
     </tr>
     <tr>
      <td>Herunterladen-Datum</td>
      <td>Das Datum, an dem die Aktion zum Herunterladen des Assets durchgeführt wurde.</td>
     </tr>
     <tr>
      <td>Autor</td>
      <td>Der Autor des Assets.</td>
     </tr>
     <tr>
      <td>Erstellungsdatum</td>
      <td>Das Datum, an dem das Asset in die Assets-Ansicht hochgeladen wurde.</td>
     </tr>
     <tr>
      <td>Änderungsdatum</td>
      <td>Das Datum der letzten Änderung des Assets.</td>
     </tr>
     <tr>
      <td>Abgelaufen</td>
      <td>Der Ablaufstatus des Assets.</td>
     </tr>
     <tr>
      <td>Heruntergeladen von Benutzername</td>
      <td>Der Name der Benutzerin oder des Benutzers, die/der das Asset heruntergeladen hat.</td>
     </tr>           
    </tbody>
   </table>

## Erstellen eines Hochladen-Berichts {#create-upload-report}

So erstellen Sie einen Hochladen-Bericht:

1. Navigieren Sie zu **[!UICONTROL Einstellungen]** > **[!UICONTROL Berichte]** und klicken Sie auf **[!UICONTROL Bericht erstellen]**.

1. Gehen Sie zur Registerkarte [!UICONTROL Konfiguration] und spezifizieren Sie den Berichtstyp als **[!UICONTROL Hochladen]**.

1. Geben Sie einen Titel und optional eine Beschreibung für den Bericht an.

1. Wählen Sie über das Feld **[!UICONTROL Ordnerpfad auswählen]** den Ordnerpfad aus, der die Assets enthält, für die der Bericht ausgeführt werden soll.

1. Wählen Sie das Datumsintervall für den Bericht.

1. Wählen Sie auf der Registerkarte [!UICONTROL Spalten] die Spaltennamen aus, die Sie im Bericht anzeigen möchten.

1. Klicken Sie auf **[!UICONTROL Erstellen]**.

   ![Hochladen-Bericht](assets/upload-reports-config.png)

In der folgenden Tabelle wird die Verwendung aller Spalten erläutert, die Sie dem Bericht hinzufügen können:

<table>
    <tbody>
     <tr>
      <th><strong>Spaltenname</strong></th>
      <th><strong>Beschreibung</strong></th>
     </tr>
     <tr>
      <td>Titel</td>
      <td>Der Titel des Assets.</td>
     </tr>
     <tr>
      <td>Pfad </td>
      <td>Der Ordnerpfad, in dem das Asset in der Assets-Ansicht verfügbar ist.</td>
     </tr>
     <tr>
      <td>MIME-Typ</td>
      <td>Der MIME-Typ für das Asset.</td>
     </tr>
     <tr>
      <td>Größe</td>
      <td>Die Größe des Assets.</td>
     </tr>
     <tr>
      <td>Autor</td>
      <td>Der Autor des Assets.</td>
     </tr>
     <tr>
      <td>Erstellungsdatum</td>
      <td>Das Datum, an dem das Asset in die Assets-Ansicht hochgeladen wurde.</td>
     </tr>
     <tr>
      <td>Änderungsdatum</td>
      <td>Das Datum der letzten Änderung des Assets.</td>
     </tr>
     <tr>
      <td>Abgelaufen</td>
      <td>Der Ablaufstatus des Assets.</td>
     </tr>              
    </tbody>
   </table>

## Anzeigen vorhandener Berichte {#view-report-list}

Nach der [Erstellung des Berichts](#create-download-report) können Sie die Liste der Berichte einsehen und auswählen, ob Sie sie im CSV-Format herunterladen oder löschen möchten.

Um die Liste der Berichte anzuzeigen, navigieren Sie zu **[!UICONTROL Einstellungen]** > **[!UICONTROL Berichte]**.

Für jeden Bericht können Sie den Berichtstitel, die Art des Berichts, die bei der Erstellung des Berichts angegebene Beschreibung, den Status des Berichts, die E-Mail-ID des Autors, der den Bericht erstellt hat, und das Erstellungsdatum des Berichts einsehen.

Der Berichtstatus `Completed ` bedeutet, dass der Bericht zum Herunterladen bereit ist.

![Liste der Berichte](assets/list-of-reports.png)


## Herunterladen eines CSV-Berichts {#download-csv-report}

So laden Sie einen Bericht im CSV-Format herunter:

1. Navigieren Sie zu **[!UICONTROL Einstellungen]** > **[!UICONTROL Berichte]**.

1. Wählen Sie einen Bericht aus und klicken Sie auf **[!UICONTROL CSV herunterladen]**.

Der ausgewählte Bericht wird im CSV-Format heruntergeladen. Welche Spalten im CSV-Bericht angezeigt werden, hängt von den Spalten ab, die Sie beim [Erstellen des Berichts](#create-download-report) auswählen.

## Löschen eines Berichts {#delete-report}

So löschen Sie einen Bericht:

1. Navigieren Sie zu **[!UICONTROL Einstellungen]** > **[!UICONTROL Berichte]**.

1. Wählen Sie einen Bericht aus und klicken Sie auf **[!UICONTROL Löschen]**.

1. Zum Bestätigen erneut auf **[!UICONTROL Löschen]** klicken.
