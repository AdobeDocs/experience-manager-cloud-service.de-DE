---
title: 'Exportieren in CSV  '
description: Exportieren von Informationen zu Ihren Seiten in eine CSV-Datei auf Ihrem lokalen System
exl-id: 818e927e-40b2-4ccb-bfb3-88284ad49829
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 100%

---

# Exportieren in CSV   {#export-to-csv}

Mit **CSV-Bericht erstellen** können Sie Informationen über Ihre Seiten in eine CSV-Datei auf Ihrem lokalen System exportieren.

* Die heruntergeladene Datei erhält den Namen `export.csv`.
* Der Inhalt der Datei hängt davon ab, welche Eigenschaften Sie für den Export auswählen.
* Sie können den Pfad zusammen mit der Tiefe des Exports definieren.

>[!NOTE]
>
>Die Download-Funktion (und der Standard-Zielordner) Ihres Browsers werden verwendet.

**** Der Assistent zum Erstellen von CSV-Exporten bietet Ihnen folgende Auswahlmöglichkeiten:

* Zu exportierende Eigenschaften
   * Metadaten  
      * Name
      * Geändert
      * Veröffentlicht
      * Vorlage
      * Workflow
   * Übersetzung
      * Übersetzt
   * Analytics
      * Seitenansichten
      * Individuelle Besucher
      * Zeit auf Seite
* Depth
   * Übergeordneter Pfad
   * Nur direkte untergeordnete Elemente
   * Zusätzliche Ebenen von untergeordneten Elementen
   * Levels

Die resultierende Datei `export.csv` kann in Excel (oder einer anderen kompatiblen Anwendung) geöffnet werden.

So erstellen Sie einen CSV-Export: 

1. Öffnen Sie die **Sites-Konsole** und wechseln Sie zum gewünschten Verzeichnis, falls erforderlich.
   * Die Option **CSV-Bericht erstellen** ist verfügbar, wenn Sie durch die Konsole **Sites** (in der Listenansicht) navigieren.
   * Es handelt sich um eine Option im Dropdown-Menü **Erstellen**:

      ![Option „CSV-Bericht erstellen“](/help/sites-cloud/authoring/assets/csv-create.png)

1. Wählen Sie in der Symbolleiste **Erstellen** und dann **CSV-Bericht** aus, um den Assistenten zu öffnen:

   ![CSV-Exportoptionen](/help/sites-cloud/authoring/assets/csv-options.png)

1. Wählen Sie die gewünschten Eigenschaften aus, die Sie exportieren möchten.
1. Wählen Sie **Erstellen**.
   ![Resultierender CSV-Export in Excel](/help/sites-cloud/authoring/assets/csv-example.png)
