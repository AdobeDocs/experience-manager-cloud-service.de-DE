---
title: Stapelweises Importieren und Exportieren von Asset-Metadaten
description: Dieser Artikel beschreibt, wie Sie Metadaten in Massen importieren und exportieren können.
contentOwner: AG
feature: 'Metadaten  '
role: Business Practitioner,Administrator
exl-id: fb70a068-3ba3-4459-952d-79155d286c42
source-git-commit: 1dc639265570b54c42d04f61178d8d2faec1b433
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 93%

---

# Stapelweises Importieren und Exportieren von Asset-Metadaten  {#import-and-export-asset-metadata-in-bulk}

Mit AEM Assets können Sie Asset-Metadaten mithilfe einer CSV-Datei in Massen importieren. Sie können für die kürzlich hochgeladenen Assets oder die vorhandenen Assets eine Massenaktualisierung durchführen, indem Sie eine CSV-Datei importieren. Außerdem können Sie Asset-Metadaten von Drittanbietersystemen mithilfe des CSV-Formats in Batches erfassen.

## Importieren von Metadaten   {#import-metadata}

Die Metadaten werden asynchron importiert, sodass der Import die Systemleistung nicht beeinträchtigt. Die gleichzeitige Aktualisierung der Metadaten für mehrere Assets kann ressourcenintensiv sein, da die Metadaten-Writeback-Aktivität Asset-Microservices verwendet. Adobe empfiehlt, dass Sie alle Massenvorgänge bei geringer Serverauslastung planen, damit die Leistung für andere Benutzer nicht beeinträchtigt wird.

>[!NOTE]
>
>Um Metadaten in benutzerdefinierte Namespaces zu importieren, registrieren Sie zunächst die Namespaces.

1. Navigieren Sie zur Benutzeroberfläche „Assets“ und tippen/klicken Sie in der Symbolleiste auf **[!UICONTROL Erstellen]**.
1. Wählen Sie aus dem Menü **[!UICONTROL Metadaten]** aus.
1. Tippen/klicken Sie auf der Seite **[!UICONTROL Metadaten-Import]** auf **[!UICONTROL Datei auswählen]**. Wählen Sie die CSV-Datei mit den Metadaten aus.
1. Geben Sie die folgenden Parameter an:

   | Parameter | Beschreibung |
   | ---------------------- | ------- |
   | Batch-Größe | Anzahl der Assets in einem Batch, für die Metadaten importiert werden sollen. Der Standardwert ist 50. Der Wert darf maximal 100 betragen. |
   | Feldtrennzeichen | Der Standardwert ist `,` (ein Komma). Sie können jedoch ein beliebiges anderes Zeichen eingeben. |
   | Mehrfachtrennzeichen | Trennzeichen für Metadatenwerte. Der Standardwert ist `|`. |
   | Workflows starten | Lautet standardmäßig „False“. Wenn auf `true` gesetzt, sind die standardmäßigen Launcher-Einstellungen für den Workflow &quot;DAM-Metadaten-WriteBack&quot;aktiv (der Metadaten in die binären XMP schreibt). Die Aktivierung von Start-Workflows verlangsamt das System. |
   | Asset-Pfad-Spaltenname | Definiert den Namen der Spalte in der CSV-Datei, die die Assets enthält. |

1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Importieren]**. Nachdem die Metadaten importiert wurden, wird eine Benachrichtigung an Ihren Benachrichtigungs-Posteingang gesendet. Navigieren Sie zur Asset-Eigenschaftsseite und überprüfen Sie, ob die Metadatenwerte richtig in die entsprechenden Assets importiert wurden.

Um beim Importieren von Metadaten Datum und Zeitstempel hinzuzufügen, verwenden Sie das `YYYY-MM-DDThh:mm:ss.fff-00:00`-Format für Datum und Uhrzeit. Datum und Uhrzeit werden durch `T` getrennt angegeben. `hh` ist Stunden im 24-Stunden-Format, `fff` ist Nanosekunden und `-00:00` ist der Zeitzonenversatz. Zum Beispiel ist `2020-03-26T11:26:00.000-07:00` der 26. März 2020 um 11:26:00.000 Uhr (PST).

>[!CAUTION]
>
>Wenn das Datumsformat nicht mit `YYYY-MM-DDThh:mm:ss.fff-00:00` übereinstimmt, werden die Datumswerte nicht eingestellt. Die Datumsformate der exportierten Metadaten-CSV-Datei entsprechen dem Format `YYYY-MM-DDThh:mm:ss-00:00`. Wenn Sie das Datum importieren möchten, konvertieren Sie es in das akzeptable Format, indem Sie den mit `fff` angegebenen Nanosekundenwert hinzufügen.

## Exportieren von Metadaten {#export-metadata}

Sie können Metadaten für mehrere Assets in einem CSV-Format exportieren. Die Metadaten werden asynchron exportiert, sodass der Export die Systemleistung nicht beeinträchtigt. Wenn Sie Metadaten exportieren, durchsucht AEM die Eigenschaften des Asset-Knotens `jcr:content/metadata` und der untergeordneten Knoten und exportiert die Metadateneigenschaften in eine CSV-Datei.

Einige Anwendungsfälle für den Massenexport von Metadaten:

* Importieren Sie die Metadaten in ein Drittanbietersystem, wenn Sie Assets migrieren.
* Geben Sie Asset-Metadaten für ein breiteres Projektteam frei.
* Testen oder prüfen Sie die Metadaten auf Ihre Konformität.
* Externalisieren Sie die Metadaten für eine separate Lokalisierung.

1. Wählen Sie einen Asset-Ordner aus, der Assets enthält, für die Sie Metadaten exportieren möchten. Wählen Sie in der Symbolleiste **[!UICONTROL Metadaten exportieren]** aus.
1. Geben Sie im Dialogfeld „Metadatenexport“ einen Namen für die CSV-Datei an. Um Metadaten von Assets in Unterordnern zu exportieren, wählen Sie **[!UICONTROL Assets in Unterordnern einschließen]**.

   ![Benutzeroberfläche und Optionen zum Exportieren von Metadaten aller Assets in einem Ordner](assets/export_metadata_page.png "Benutzeroberfläche und Optionen zum Exportieren von Metadaten aller Assets in einem Ordner")

1. Wählen Sie die gewünschten Optionen aus. Geben Sie einen Dateinamen und ggf. ein Datum an.

1. Geben Sie im Feld **[!UICONTROL Zu exportierende Eigenschaften]** an, ob Sie alle oder nur bestimmte Eigenschaften exportieren wollen. Wenn Sie für den Export „Selektive Eigenschaften“ auswählen, fügen Sie die gewünschten Eigenschaften hinzu.

1. Tippen oder klicken Sie in der Symbolleiste auf **[!UICONTROL Exportieren]**. Sie erhalten eine Meldung, die bestätigt, dass die Metadaten exportiert wurden. Schließen Sie die Meldung.
1. Öffnen Sie die Posteingangsbenachrichtigung für den Exportauftrag. Wählen Sie den Auftrag aus und klicken Sie in der Symbolleiste auf **[!UICONTROL Öffnen]**. Um die CSV-Datei mit den Metadaten herunterzuladen, tippen/klicken Sie in der Symbolleiste auf **[!UICONTROL CSV-Download]**. Klicken Sie auf **[!UICONTROL Schließen]**.

   ![Dialogfeld zum Herunterladen der CSV-Datei mit Metadaten, die stapelweise exportiert wurden](assets/csv_download.png)

   *Abbildung: Dialogfeld zum Herunterladen der CSV-Datei mit Metadaten, die stapelweise exportiert wurden.*
