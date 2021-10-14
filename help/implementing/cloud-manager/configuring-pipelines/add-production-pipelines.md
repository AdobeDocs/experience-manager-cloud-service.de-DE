---
title: Hinzufügen von Produktions-Pipelines
description: Hinzufügen von Produktions-Pipelines
index: false
source-git-commit: 16e3280d7eaf53d8f944a60ec93b21c6676f0133
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 97%

---


# Erstellen einer Produktions-Pipeline {#create-production-pipeline}

Sobald Sie Ihr Programm eingerichtet haben und über mindestens eine Umgebung mit der [!UICONTROL Cloud Manager]-Benutzeroberfläche verfügen, können Sie Ihre Implementierungs-Pipeline einrichten.

Führen Sie folgende Schritte aus, um das Verhalten und die Voreinstellungen für Ihre Pipeline zu konfigurieren:

1. Klicken Sie auf **Pipeline einrichten**, um Ihre Pipeline einzurichten und zu konfigurieren.

   ![](assets/set-up-pipeline1.png)

1. Der Bildschirm **Pipeline einrichten** wird angezeigt. Wählen Sie die Verzweigung aus und klicken Sie auf **Weiter**.

   ![](assets/setup-1.png)

1. Konfigurieren Sie die Implementierungsoptionen.

   ![](assets/setup-pipeline.png)

   Sie können den Auslöser definieren, mit dem die Pipeline gestartet wird:

   * **Manuell**: Die Pipeline wird über die Benutzeroberfläche manuell gestartet.
   * **Bei Git-Änderungen**: Startet die CI/CD-Pipeline, wenn zur konfigurierten Git-Verzweigung Commits hinzugefügt werden. Wenn Sie diese Option auswählen, können Sie die Pipeline weiterhin manuell starten.

   Bei der Einrichtung oder Bearbeitung der Pipeline kann der Implementierungsmanager festlegen, wie sich die Pipeline verhält, wenn bei einem der Quality Gates (Test der Code-Qualität, Sicherheitstest und Leistungstest) ein wichtiger Fehler auftritt.

   Das ist für Kunden nützlich, die die Prozesse stärker automatisieren möchten. Die verfügbaren Optionen sind:

   * **Jedes Mal fragen**: Das ist die Standardeinstellung und erfordert manuelles Eingreifen bei einem wichtigen Fehler.
   * **Sofort abbrechen**: Wenn diese Option ausgewählt ist, wird die Pipeline bei einem wichtigen Fehler abgebrochen. Damit wird im Grunde ein Benutzer simuliert, der manuell jeden Fehler ablehnt.
   * **Sofort genehmigen**: Wenn diese Option ausgewählt ist, wird die Pipeline bei einem wichtigen Fehler automatisch fortgesetzt. Damit wird im Grunde ein Anwender simuliert, der manuell jeden Fehler genehmigt.


1. Die Einstellungen für die Produktions-Pipeline enthalten eine dritte Registerkarte mit der Bezeichnung **Experience Audit**. Diese Option enthält eine Tabelle der URL-Pfade, die im Experience Audit stets enthalten sein sollten.

   >[!NOTE]
   >Sie müssen auf **Neue Seite hinzufügen** klicken, um einen eigenen benutzerspezifischen Link zu definieren.

   ![](assets/setup-3.png)

   Klicken Sie auf **Neue Seite hinzufügen**, um einen URL-Pfad anzugeben, der in die Erlebnisprüfung aufgenommen werden soll.

   Wenn Sie zum Beispiel `https://wknd.site/us/en/about-us.html` in die Erlebnisprüfung einschließen möchten, geben Sie den Pfad `us/en/about-us.html` in dieses Feld ein und klicken Sie auf **Speichern**.

   ![](assets/exp-audit4.png)

   Die in der Tabelle angezeigte URL lautet:

   `https://publish-p14253-e43686.adobeaemcloud.com/us/en/about-us.html`

   ![](assets/exp-audit5.png)

   Es können maximal 25 Zeilen eingefügt werden. Wenn der Benutzer in diesem Abschnitt keine Seiten übermittelt hat, wird die Startseite der Site standardmäßig in die Erlebnisprüfung einbezogen.

   Weitere Informationen finden Sie unter [Verstehen der Ergebnisse von Experience Audit](/help/implementing/cloud-manager/experience-audit-testing.md).

   >[!NOTE]
   > Die konfigurierten Seiten werden an den Service gesendet und gemäß den Tests für Leistung, Barrierefreiheit, SEO (Suchmaschinenoptimierung), Best Practice und PWA (Progressive Web App) bewertet.

1. Klicken Sie im Bildschirm **Pipeline bearbeiten** auf **Speichern**. Auf der Seite **Übersicht** wird nun die Karte **Ihr Programm bereitstellen** angezeigt. Klicken Sie auf **Bereitstellen**, um das Programm bereitzustellen.

   ![](assets/configure-pipeline5.png)

