---
title: Konfigurieren der CI/CD-Pipeline – Cloud Services
description: Konfigurieren der CI/CD-Pipeline – Cloud Services
exl-id: d2024b42-9042-46a0-879e-110b214c7285
source-git-commit: eb8fb1f4134ceb9117773d01f4d97c68bd8c41a2
workflow-type: tm+mt
source-wordcount: '1407'
ht-degree: 40%

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

### Hinzufügen einer neuen Produktions-Pipeline {#adding-production-pipeline}

Sobald Sie Ihr Programm eingerichtet haben und über mindestens eine Umgebung mit der [!UICONTROL Cloud Manager] -Benutzeroberfläche verfügen, können Sie eine Produktions-Pipeline hinzufügen.

Führen Sie die folgenden Schritte aus, um das Verhalten und die Voreinstellungen für Ihre Produktions-Pipeline zu konfigurieren:

1. Navigieren Sie auf der Seite **Programmübersicht** zur Karte **Pipelines** .
Klicken Sie auf **+Add** und wählen Sie **Produktions-Pipeline hinzufügen** aus.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-1.png)

1. **Das Dialogfeld &quot;** Produktions-Pipelineform hinzufügen&quot;wird angezeigt. Geben Sie den Pipeline-Namen ein.

   Darüber hinaus können Sie **Deployment Trigger** und **Verhalten bei wichtigen Metrikfehlern** unter **Bereitstellungsoptionen** einrichten. Klicken Sie auf **Weiter**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/prod-pipeline-add2.png)


   Sie können die Bereitstellungs-Trigger definieren, um die Pipeline zu starten.

   * **Manuell**: Die Pipeline wird über die Benutzeroberfläche manuell gestartet.
   * **Bei Git-Änderungen**: Startet die CI/CD-Pipeline, wenn zur konfigurierten Git-Verzweigung Commits hinzugefügt werden. Wenn Sie diese Option auswählen, können Sie die Pipeline weiterhin manuell starten.

      Bei der Einrichtung oder Bearbeitung der Pipeline kann der Implementierungsmanager festlegen, wie sich die Pipeline verhält, wenn bei einem der Quality Gates (Test der Code-Qualität, Sicherheitstest und Leistungstest) ein wichtiger Fehler auftritt.

      Das ist für Kunden nützlich, die die Prozesse stärker automatisieren möchten. Die verfügbaren Optionen sind:
   Sie können das wichtige Verhalten von Fehlermetriken definieren, um die Pipeline zu starten.

   * **Jedes Mal fragen**: Das ist die Standardeinstellung und erfordert manuelles Eingreifen bei einem wichtigen Fehler.
   * **Sofort**  fehlschlagen - Wenn diese Option ausgewählt ist, wird die Pipeline bei einem wichtigen Fehler abgebrochen. Damit wird im Grunde ein Benutzer simuliert, der manuell jeden Fehler ablehnt.
   * **Sofort fortfahren**  - Wenn diese Option aktiviert ist, wird die Pipeline bei einem wichtigen Fehler automatisch fortgesetzt. Damit wird im Grunde ein Anwender simuliert, der manuell jeden Fehler genehmigt.


1. Das Dialogfeld **Produktions-Pipeline hinzufügen** enthält eine zweite Registerkarte mit der Bezeichnung **Quellcode**. **Vollständiger Stack-** Code ausgewählt. Sie können **Repository** und die **Git-Verzweigung** auswählen. Wählen Sie die Produktionsbereitstellungsoptionen wie unten beschrieben aus. Klicken Sie auf **Weiter**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/prod-fullstack1.png)

   Produktionsbereitstellungsoptionen:

   * **Anhalten vor der Bereitstellung für die Produktion**: Diese Option ermöglicht die Pause der Bereitstellung vor der Produktion.
   * **Geplant**: Mit dieser Option kann der Benutzer die geplante Produktionsbereitstellung aktivieren.

1. Das Dialogfeld **Produktions-Pipeline hinzufügen** enthält eine dritte Registerkarte mit der Bezeichnung **Experience Audit**. Diese Option enthält eine Tabelle der URL-Pfade, die im Experience Audit stets enthalten sein sollten.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit.png)

   >[!IMPORTANT]
   >Sie müssen auf **Seite hinzufügen** klicken, um Ihren eigenen benutzerspezifischen Link zu definieren. Der Seitenpfad muss mit `/` beginnen.
   >![](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit2.png)


   Klicken Sie auf **Neue Seite hinzufügen**, um einen URL-Pfad anzugeben, der in die Erlebnisprüfung aufgenommen werden soll.

   Wenn Sie zum Beispiel `https://wknd.site/us/en/about-us.html` in die Erlebnisprüfung einschließen möchten, geben Sie den Pfad `/us/en/about-us.html` in dieses Feld ein und klicken Sie auf **Speichern**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit3.png)

   Die in der Tabelle angezeigte URL lautet:

   `https://publish-p14253-e43686.adobeaemcloud.com/us/en/about-us.html`

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit4.png)

   Es können maximal 25 Zeilen eingefügt werden. Wenn der Benutzer in diesem Abschnitt keine Seiten übermittelt hat, wird die Startseite der Site standardmäßig in die Erlebnisprüfung einbezogen.

   Weitere Informationen finden Sie unter [Verstehen der Ergebnisse von Experience Audit](/help/implementing/cloud-manager/experience-audit-testing.md).

   >[!NOTE]
   > Die konfigurierten Seiten werden an den Service gesendet und gemäß den Tests für Leistung, Barrierefreiheit, SEO (Suchmaschinenoptimierung), Best Practice und PWA (Progressive Web App) bewertet.

1. Klicken Sie auf **Save**. Die neu erstellte Produktions-Pipeline wird jetzt auf der Karte **Pipelines** angezeigt.

   Die Pipeline wird auf der Karte auf dem Startbildschirm mit drei Aktionen angezeigt, wie unten dargestellt:

   * **Hinzufügen**  - ermöglicht das Hinzufügen einer neuen Pipeline.
   * **Auf Repository-Informationen zugreifen**: Ermöglicht es dem Benutzer, die für den Zugriff auf das Cloud Manager-Git-Repository erforderlichen Informationen abzurufen.
   * **Weitere Informationen**: Führt zu weiteren Informationen über die Dokumentation zur CI/CD-Pipeline.

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

### Zusätzliche Produktions-Pipeline-Aktionen {#additional-prod-actions}

#### Ausführen einer Produktions-Pipeline {#run-prod}

Sie können die Produktions-Pipeline über die Pipelines-Karte ausführen:

1. Navigieren Sie auf der Seite **Programmübersicht** zur Karte **Pipelines** .

1. Klicken Sie auf **...** aus der Karte **Pipelines** und klicken Sie auf **Ausführen**, wie in der folgenden Abbildung dargestellt.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/prod-run.png)

#### Löschen einer Produktions-Pipeline {#delete-prod}

Sie können die Produktions-Pipeline aus der Pipelines-Karte löschen:

1. Navigieren Sie auf der Seite **Programmübersicht** zur Karte **Pipelines** .

1. Klicken Sie auf **...** aus der Karte **Pipelines** und klicken Sie auf **Löschen**, wie in der folgenden Abbildung dargestellt.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/prod-delete.png)

   >[!NOTE]
   >Ein Benutzer mit der Rolle &quot;Bereitstellungsmanager&quot;kann die Produktions-Pipeline jetzt über die Option **Löschen** auf der Pipeline-Karte selbstständig löschen.


## Produktionsfremde Pipelines und Pipelines für Tests der Code-Qualität {#non-production-pipelines}

Zusätzlich zur Haupt-Pipeline, die für die Staging- und Produktionsumgebung bereitgestellt wird, können Kunden weitere Pipelines einrichten, die als **Produktionsfremde Pipelines** bezeichnet werden. Diese Pipelines führen immer die Schritte Build-Erstellung und Tests der Code-Qualität aus. Sie können optional auch für AEM as a Cloud Service Umgebung bereitgestellt werden.

### Hinzufügen einer neuen produktionsfremden Pipeline {#adding-non-production-pipeline}

Auf dem Startbildschirm werden diese Pipelines in einer neuen Karte aufgeführt:

1. Greifen Sie über den Cloud Manager-Startbildschirm auf die Karte **Pipelines** zu. Klicken Sie auf **+Add** und wählen Sie **Add Non-Production Pipeline** aus.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add1.png)

1. **Das Dialogfeld Nicht-Produktions-**  Pipelineprojekt hinzufügen wird angezeigt. Wählen Sie den Pipeline-Typ aus, den Sie erstellen möchten, entweder **Code Quality Pipeline** oder **Deployment Pipeline**.

   Darüber hinaus können Sie **Deployment Trigger** und **Verhalten bei wichtigen Metrikfehlern** unter **Bereitstellungsoptionen** einrichten. Klicken Sie auf **Weiter**.

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

   1. Auf der Registerkarte **Configuration** können Sie den **Pipeline-Namen**, **Deployment Trigger** und **Verhalten bei wichtigen Metrikfehlern** aktualisieren.

      >[!NOTE]
      >Informationen zum Hinzufügen und Verwalten von Repositorys in Cloud Manager finden Sie unter [Hinzufügen und Verwalten von Repositorys](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) .

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-edit2.png)


   1. Auf der Registerkarte **Quellcode** können Sie das **Repository** und die **Git-Verzweigung** aktualisieren.

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-edit3.png)

1. Klicken Sie auf **Aktualisieren** , sobald Sie die Bearbeitung der produktionsfremden Pipeline abgeschlossen haben.

### Zusätzliche produktionsfremde Pipelineaktionen {#additional-nonprod-actions}

#### Ausführen einer produktionsfremden Pipeline {#run-nonprod}

Sie können die Produktions-Pipeline über die Pipelines-Karte ausführen:

1. Navigieren Sie auf der Seite **Programmübersicht** zur Karte **Pipelines** .

1. Klicken Sie auf **...** aus der Karte **Pipelines** und klicken Sie auf **Ausführen**, wie in der folgenden Abbildung dargestellt.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-run1.png)

#### Löschen einer produktionsfremden Pipeline {#delete-nonprod}

Sie können die Produktions-Pipeline aus der Pipelines-Karte löschen:

1. Navigieren Sie auf der Seite **Programmübersicht** zur Karte **Pipelines** .

1. Klicken Sie auf **...** aus der Karte **Pipelines** und klicken Sie auf **Löschen**, wie in der folgenden Abbildung dargestellt.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-delete.png)


## Die nächsten Schritte {#the-next-steps}

Nachdem die Konfiguration der Pipeline abgeschlossen ist, müssen Sie Ihren Code bereitstellen.

Weitere Informationen finden Sie unter [Bereitstellen Ihres Codes](deploy-code.md).
