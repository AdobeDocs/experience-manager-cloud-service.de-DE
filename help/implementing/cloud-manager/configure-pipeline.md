---
title: Konfigurieren der CI/CD-Pipeline – Cloud Services
description: Konfigurieren der CI/CD-Pipeline – Cloud Services
exl-id: d2024b42-9042-46a0-879e-110b214c7285
source-git-commit: 16e3280d7eaf53d8f944a60ec93b21c6676f0133
workflow-type: tm+mt
source-wordcount: '1063'
ht-degree: 64%

---

# Konfigurieren der CI/CD-Pipeline {#configure-ci-cd-pipeline}

In Cloud Manager gibt es zwei Arten von Pipelines:

* **Produktions-Pipeline**:

   Eine Produktions-Pipeline kann erst hinzugefügt werden, nachdem ein Satz aus Produktions- und Staging-Umgebung erstellt wurde.

   Weitere Informationen finden Sie unter [Einrichten einer Produktions-Pipeline](configure-pipeline.md#setting-up-the-pipeline).

* **Produktionsfremde Pipeline**

   Auf der Seite **Überblick** der Benutzeroberfläche von Cloud Manager kann eine produktionsfremde Pipeline hinzugefügt werden.

   Weitere Informationen finden Sie unter [Produktionsfremde Pipelines und Pipelines für Tests der Code-Qualität](configure-pipeline.md#non-production-pipelines).

   >[!NOTE]
   >Zur Konfiguration der Pipeline müssen Sie:
   > * den Auslöser festlegen, der die Pipeline startet,
   > * Parameter zur Steuerung der Produktionsimplementierung festlegen,
   > * Leistungstestparameter konfigurieren.


## Einrichten einer Produktions-Pipeline {#setting-up-production-pipeline}

Der Implementierungs-Manager ist für die Einrichtung der Produktions-Pipeline verantwortlich.

>[!NOTE]
>Eine Produktions-Pipeline kann erst eingerichtet werden, wenn die Erstellung eines Programms abgeschlossen wurde, das Git-Repository über mindestens eine Verzweigung verfügt und ein Satz aus Produktions- und Staging-Umgebung erstellt wurde.

Bevor Sie Code bereitstellen, müssen Sie Ihre Pipelineeinstellungen über [!UICONTROL Cloud Manager] konfigurieren.

>[!NOTE]
>
>Sie können die Pipelineeinstellungen nach der Ersteinrichtung ändern.

## Konfigurieren der Pipeline-Einstellungen in [!UICONTROL Cloud Manager] {#configuring-the-pipeline-settings-from-cloud-manager}

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

### Bearbeiten einer Produktions-Pipeline {#editing-prod-pipeline}

Sie können die Pipelinekonfigurationen auf der Seite **Programmübersicht** bearbeiten.

Gehen Sie wie folgt vor, um die konfigurierte Pipeline zu bearbeiten:

1. Navigieren Sie auf der Seite **Programmübersicht** zur Karte **Pipelines** .

1. Klicken Sie auf **...** aus der Karte **Pipelines** und klicken Sie auf **Bearbeiten**, wie in der folgenden Abbildung dargestellt.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-edit1.png)

1. Das Dialogfeld **Produktions-Pipeline bearbeiten** wird angezeigt.

   1. Auf der Registerkarte **Configuration** können Sie den **Pipeline-Namen**, **Deployment Trigger** und **Wichtiges Verhalten bei Metrikfehlern** aktualisieren.

      >[!NOTE]
      >Informationen zum Hinzufügen und Verwalten von Repositorys in Cloud Manager finden Sie unter [Hinzufügen und Verwalten von Repositorys](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) .

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-edit2.png)


   1. Auf der Registerkarte **Quelle** können Sie die Option **Pause vor der Bereitstellung in der Produktion** und die Option **Geplant** unter **Produktionsbereitstellungsoptionen** aktivieren oder deaktivieren.

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/prod-pipeline-editnotier.png)

   1. Mit der Option **Erlebnisprüfung** können Sie neue Seiten aktualisieren oder hinzufügen.

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-edit4.png)

1. Klicken Sie auf **Aktualisieren** , sobald Sie die Pipeline bearbeitet haben.

## Produktionsfremde Pipelines und Pipelines für Tests der Code-Qualität {#non-production-pipelines}

Zusätzlich zur Haupt-Pipeline, die für die Staging- und Produktionsumgebung bereitgestellt wird, können Kunden weitere Pipelines einrichten, die als **Produktionsfremde Pipelines** bezeichnet werden. Diese Pipelines führen immer die Schritte Build-Erstellung und Tests der Code-Qualität aus. Sie können optional auch für AEM as a Cloud Service Umgebung bereitgestellt werden.

Auf dem Startbildschirm werden diese Pipelines in einer neuen Karte aufgeführt:

1. Greifen Sie über den Cloud Manager-Startbildschirm auf die Karte **Pipelines** zu. Klicken Sie auf **+Add** und wählen Sie **Add Non-Production Pipeline** aus.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add1.png)

1. **Das Dialogfeld Nicht-Produktions-**  Pipelineprojekt hinzufügen wird angezeigt. Wählen Sie den Pipeline-Typ aus, den Sie erstellen möchten, entweder **Code Quality Pipeline** oder **Deployment Pipeline**.

   Darüber hinaus können Sie **Deployment Trigger** und **Wichtiges Fehlerverhalten** unter **Bereitstellungsoptionen** einrichten. Klicken Sie auf **Weiter**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add2.png)

1. **Vollständiger Stack-** Code ausgewählt. Sie können **Repository** und die **Git-Verzweigung** auswählen. Klicken Sie auf **Save**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add3.png)

1. Die neu erstellte Nicht-Produktions-Pipeline wird jetzt auf der Karte **Pipelines** angezeigt.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add4.png)


   Die Pipeline wird auf der Karte auf dem Startbildschirm mit drei Aktionen angezeigt, wie unten dargestellt:

   * **Hinzufügen**  - ermöglicht das Hinzufügen einer neuen Pipeline.
   * **Auf Repository-Informationen zugreifen**: Ermöglicht es dem Benutzer, die für den Zugriff auf das Cloud Manager-Git-Repository erforderlichen Informationen abzurufen.
   * **Weitere Informationen**: Führt zu weiteren Informationen über die Dokumentation zur CI/CD-Pipeline.

### Bearbeiten einer produktionsfremden Pipeline {#editing-nonprod-pipeline}

Sie können die Pipeline-Konfigurationen auf der Seite **Pipelines-Karte** von **Programmübersicht** bearbeiten.

Gehen Sie wie folgt vor, um die konfigurierte Nicht-Produktions-Pipeline zu bearbeiten:

1. Navigieren Sie auf der Seite **Programmübersicht** zur Karte **Pipelines** .

1. Wählen Sie die produktionsfremde Pipeline aus und klicken Sie auf **...**. Klicken Sie auf **Bearbeiten**, wie in der folgenden Abbildung dargestellt.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-edit1.png)

1. Das Dialogfeld **Produktions-Pipeline bearbeiten** wird angezeigt.

   1. Auf der Registerkarte **Configuration** können Sie den **Pipeline-Namen**, **Deployment Trigger** und **Wichtiges Verhalten bei Metrikfehlern** aktualisieren.

      >[!NOTE]
      >Informationen zum Hinzufügen und Verwalten von Repositorys in Cloud Manager finden Sie unter [Hinzufügen und Verwalten von Repositorys](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) .

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-edit2.png)


   1. Auf der Registerkarte **Quellcode** können Sie das **Repository** und die **Git-Verzweigung** aktualisieren.

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-edit3.png)

1. Klicken Sie auf **Aktualisieren** , sobald Sie die Bearbeitung der produktionsfremden Pipeline abgeschlossen haben.


## Die nächsten Schritte {#the-next-steps}

Nachdem die Konfiguration der Pipeline abgeschlossen ist, müssen Sie Ihren Code bereitstellen.

Weitere Informationen finden Sie unter [Bereitstellen Ihres Codes](deploy-code.md).
