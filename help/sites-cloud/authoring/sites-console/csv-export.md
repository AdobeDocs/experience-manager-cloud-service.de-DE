---
title: Exportieren in CSV
description: Exportieren von Informationen zu Ihren Seiten in eine CSV-Datei auf Ihrem lokalen System
exl-id: 818e927e-40b2-4ccb-bfb3-88284ad49829
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 100%

---

# Exportieren in CSV {#export-to-csv}

Mit **CSV-Bericht erstellen** können Sie Informationen über Ihre Seiten in eine CSV-Datei auf Ihrem lokalen System exportieren.

* Die heruntergeladene Datei erhält den Namen `export.csv`.
* Der Inhalt der Datei hängt davon ab, welche Eigenschaften Sie für den Export auswählen.
* Sie können den Pfad zusammen mit der Tiefe des Exports definieren.

>[!NOTE]
>
>Die Download-Funktion (und der Standard-Zielordner) Ihres Browsers werden verwendet.

Mit dem Assistenten zum **Erstellen eines CSV-Exports** können Sie Folgendes auswählen:

* Zu exportierende Eigenschaften
   * Metadaten
      * Name
      * Geändert
      * Veröffentlicht
      * Vorlage
      * Workflow
   * Übersetzung
      * Übersetzt
   * Analyse
      * Seitenansichten
      * Unique Visitors
      * Zeit auf Seite
* Tiefe
   * Übergeordneter Pfad
   * Nur direkte untergeordnete Elemente
   * Zusätzliche Ebenen von untergeordneten Elementen
   * Ebenen

Die resultierende Datei `export.csv` kann in Excel (oder einer anderen kompatiblen Anwendung) geöffnet werden.

So erstellen Sie einen CSV-Export:

1. Öffnen Sie die **Sites-Konsole** und wechseln Sie zum gewünschten Verzeichnis, falls erforderlich.
   * Die Option **CSV-Bericht erstellen** ist verfügbar, wenn Sie (in der Listenansicht) durch die **Sites**-Konsole navigieren.
   * Es handelt sich um eine Option im Dropdown-Menü **Erstellen**:

     ![Option „CSV-Bericht erstellen“](/help/sites-cloud/authoring/assets/csv-create.png)

1. Wählen Sie in der Symbolleiste **Erstellen** und dann **CSV-Bericht** aus, um den Assistenten zu öffnen:

   ![CSV-Exportoptionen](/help/sites-cloud/authoring/assets/csv-options.png)

1. Wählen Sie die zu exportierenden Eigenschaften aus.
1. Wählen Sie **Erstellen**.
   ![Resultierender CSV-Export in Excel](/help/sites-cloud/authoring/assets/csv-example.png)
