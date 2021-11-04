---
title: Konfigurieren von Produktions-Pipelines
description: Konfigurieren von Produktions-Pipelines
index: true
source-git-commit: f25e26c84a87cf793f9c8a5ac53009034e6cd2e9
workflow-type: tm+mt
source-wordcount: '764'
ht-degree: 45%

---


# Konfigurieren einer Produktions-Pipeline {#configure-production-pipeline}

Der Bereitstellungsmanager ist für die Konfiguration der Produktions-Pipeline verantwortlich.

>[!NOTE]
>Eine Produktions-Pipeline kann erst eingerichtet werden, wenn die Erstellung eines Programms abgeschlossen wurde, das Git-Repository über mindestens eine Verzweigung verfügt und ein Satz aus Produktions- und Staging-Umgebung erstellt wurde.

Bevor Sie Code bereitstellen, müssen Sie Ihre Pipelineeinstellungen über [!UICONTROL Cloud Manager] konfigurieren.

>[!NOTE]
>Sie können die Pipelineeinstellungen nach der Ersteinrichtung ändern.

## Hinzufügen einer neuen Produktions-Pipeline {#adding-production-pipeline}

Sobald Sie Ihr Programm eingerichtet haben und mindestens eine Umgebung mit [!UICONTROL Cloud Manager] -Benutzeroberfläche können Sie eine Produktions-Pipeline hinzufügen.

Führen Sie die folgenden Schritte aus, um das Verhalten und die Voreinstellungen für Ihre Produktions-Pipeline zu konfigurieren:

1. Navigieren Sie zum **Pipelines** der Karte **Programmübersicht** Seite.
Klicken Sie auf **+Hinzufügen** und wählen Sie **Produktions-Pipeline hinzufügen**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-1.png)

1. **Produktions-Pipeline hinzufügen** angezeigt. Geben Sie den Pipeline-Namen ein.

   Darüber hinaus können Sie auch **Deployment Trigger** und **Verhalten bei wichtigen Metrikfehlern** von **Bereitstellungsoptionen**. Klicken Sie auf **Weiter**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/prod-pipeline-add2.png)


   Sie können die Bereitstellungs-Trigger definieren, um die Pipeline zu starten.

   * **Manuell**: Die Pipeline wird über die Benutzeroberfläche manuell gestartet.
   * **Bei Git-Änderungen**: Startet die CI/CD-Pipeline, wenn zur konfigurierten Git-Verzweigung Commits hinzugefügt werden. Wenn Sie diese Option auswählen, können Sie die Pipeline weiterhin manuell starten.

      Bei der Einrichtung oder Bearbeitung der Pipeline kann der Implementierungsmanager festlegen, wie sich die Pipeline verhält, wenn bei einem der Quality Gates (Test der Code-Qualität, Sicherheitstest und Leistungstest) ein wichtiger Fehler auftritt.

      Das ist für Kunden nützlich, die die Prozesse stärker automatisieren möchten. Die verfügbaren Optionen sind:
   Sie können das wichtige Verhalten von Fehlermetriken definieren, um die Pipeline zu starten.

   * **Jedes Mal fragen**: Das ist die Standardeinstellung und erfordert manuelles Eingreifen bei einem wichtigen Fehler.
   * **Sofort scheitern** - Wenn diese Option aktiviert ist, wird die Pipeline bei einem wichtigen Fehler abgebrochen. Damit wird im Grunde ein Benutzer simuliert, der manuell jeden Fehler ablehnt.
   * **Sofort fortfahren** - Wenn diese Option aktiviert ist, wird die Pipeline bei einem wichtigen Fehler automatisch fortgesetzt. Damit wird im Grunde ein Anwender simuliert, der manuell jeden Fehler genehmigt.


1. Die **Produktions-Pipeline hinzufügen** Das Dialogfeld enthält eine zweite Registerkarte mit der Bezeichnung **Quellcode**. Sie können entweder **[Vollständiger Stack-Code](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#full-stack-pipeline)** oder **[Frontend-Code](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end)**. Sie können die **Repository** und **Git-Verzweigung**. Wählen Sie die Produktionsbereitstellungsoptionen wie unten beschrieben aus. Klicken Sie auf **Weiter**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/prodpipeline-fullstack1.png)

   Wenn Sie **Frontend-Code**, müssen Sie die **Repository**, **Git-Verzweigung** und **Code-Speicherort**, wie in der folgenden Abbildung dargestellt:
   ![](/help/implementing/cloud-manager/assets/configure-pipeline/prodpipeline-fullstack1.png)

   Wenn Sie **Vollständiger Stack-Code**, müssen Sie die **Repository**, **Git-Verzweigung** und **Produktionsbereitstellungsoptionen**, wie in der folgenden Abbildung dargestellt:
   ![](/help/implementing/cloud-manager/assets/configure-pipeline/prodpipeline-fullstack2.png)

   **Optionen für die Produktionsimplementierung:**

   * **Anhalten vor der Bereitstellung für die Produktion**: Mit dieser Option kann die Bereitstellung vor der Produktion angehalten werden.
   * **Geplant**: Mit dieser Option kann der Benutzer die geplante Produktionsbereitstellung aktivieren.

   >[!IMPORTANT]
   >Wenn für die ausgewählte Umgebung bereits eine Pipeline mit vollständigem Stack-Code vorhanden ist, wird diese Auswahl deaktiviert.
   >![](/help/implementing/cloud-manager/assets/configure-pipeline/full-stack-disabled.png)

   >[!NOTE]
   >Bevor Sie mit der Konfiguration der Front-End-Pipelines beginnen, lesen Sie [Journey zur AEM SchnellSite-Erstellung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites-journey/quick-site/overview.html) für einen End-to-End-Workflow mit dem einfach zu verwendenden AEM Tool zur schnellen Site-Erstellung. Diese Dokumentations-Website hilft Ihnen, die Front-End-Entwicklung Ihrer AEM-Site zu optimieren und Ihre Site ohne AEM Backend-Wissen schnell anzupassen.





1. Die **Produktions-Pipeline hinzufügen** Das Dialogfeld enthält eine dritte Registerkarte mit der Bezeichnung **Erlebnisprüfung**. Diese Option enthält eine Tabelle der URL-Pfade, die im Experience Audit stets enthalten sein sollten.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit.png)

   >[!IMPORTANT]
   >Sie müssen auf **Seite hinzufügen** um einen eigenen benutzerspezifischen Link zu definieren. Der Seitenpfad muss mit `/`.
   >![](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit2.png)


   Klicken Sie auf **Neue Seite hinzufügen**, um einen URL-Pfad anzugeben, der in die Erlebnisprüfung aufgenommen werden soll.

   Wenn Sie zum Beispiel `https://wknd.site/us/en/about-us.html` in die Erlebnisprüfung einschließen möchten, geben Sie den Pfad `/us/en/about-us.html` in dieses Feld ein und klicken Sie auf **Speichern**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit3.png)

   Die in der Tabelle angezeigte URL lautet:

   `https://publish-p12361-e112003.adobeaemcloud.com/us/en/about-us.html`

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit4.png)

   Es können maximal 25 Zeilen eingefügt werden. Wenn der Benutzer in diesem Abschnitt keine Seiten übermittelt hat, wird die Startseite der Site standardmäßig in die Erlebnisprüfung einbezogen.

   Weitere Informationen finden Sie unter [Verstehen der Ergebnisse von Experience Audit](/help/implementing/cloud-manager/experience-audit-testing.md).

   >[!NOTE]
   > Die konfigurierten Seiten werden an den Service gesendet und gemäß den Tests für Leistung, Barrierefreiheit, SEO (Suchmaschinenoptimierung), Best Practice und PWA (Progressive Web App) bewertet.

1. Klicken Sie auf **Speichern**. Die neu erstellte Produktions-Pipeline wird jetzt im **Pipelines** Karte.

   Die Pipeline wird auf der Karte auf dem Startbildschirm mit drei Aktionen angezeigt, wie unten dargestellt:

   * **Hinzufügen** - ermöglicht das Hinzufügen einer neuen Pipeline.
   * **Auf Repository-Informationen zugreifen**: Ermöglicht es dem Benutzer, die für den Zugriff auf das Cloud Manager-Git-Repository erforderlichen Informationen abzurufen.
   * **Weitere Informationen**: Führt zu weiteren Informationen über die Dokumentation zur CI/CD-Pipeline.


