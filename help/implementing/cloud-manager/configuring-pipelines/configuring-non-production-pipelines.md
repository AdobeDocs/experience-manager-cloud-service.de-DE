---
title: Konfigurieren von Nicht-Produktions-Pipelines
description: Auf dieser Seite erfahren Sie mehr über das Konfigurieren einer produktionsfremden Pipeline in Cloud Manager
index: true
source-git-commit: 2ac65af4cf410491d1196b9e20f67647e0a1b4d1
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 33%

---


# Konfigurieren von Nicht-Produktions-Pipelines {#configure-non-production-pipeline}

Zusätzlich zur Haupt-Pipeline, die für die Staging- und Produktionsumgebung bereitgestellt wird, können Kunden weitere Pipelines einrichten, die als Produktionsfremde Pipelines bezeichnet werden.

Es gibt zwei Arten von produktionsfremden Pipelines:

1. Codequalität: Führt Code-Qualitätsprüfungen für den Code in einer Git-Verzweigung durch. Diese Pipeline führt die Build- und Codequalitätsschritte aus.
1. Implementierung: Diese Pipeline führt nicht nur die Build- und Codequalitätsschritte aus, sondern stellt den Code auch für die ausgewählte Nicht-Produktions-Umgebung in AEM as a Cloud Service Umgebung bereit.

## Hinzufügen einer neuen produktionsfremden Pipeline {#adding-non-production-pipeline}

Auf dem Startbildschirm werden diese Pipelines in einer neuen Karte aufgeführt:

1. Zugriff auf **Pipelines** -Karte vom Cloud Manager-Startbildschirm aus. Klicken Sie auf **+Hinzufügen** und wählen Sie **Hinzufügen einer produktionsfremden Pipeline**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add1.png)

1. **Hinzufügen einer produktionsfremden Pipeline**  angezeigt. Wählen Sie den Pipeline-Typ aus, den Sie erstellen möchten, entweder **Code-Qualitäts-Pipeline** oder **Bereitstellungs-Pipeline**.

   >[!NOTE]
   >Für Bereitstellungs-Pipelines müssen Sie die Bereitstellungsumgebung auswählen.

   Darüber hinaus können Sie auch **Deployment Trigger** und **Verhalten bei wichtigen Metrikfehlern** von **Bereitstellungsoptionen**. Klicken Sie auf **Weiter**.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add2.png)

   Sie können die folgenden Bereitstellungs-Trigger definieren, um die Pipeline zu starten.

   * **Manuell**: Die Pipeline wird über die Benutzeroberfläche manuell gestartet.
   * **Bei Git-Änderungen**: Startet die CI/CD-Pipeline, wenn zur konfigurierten Git-Verzweigung Commits hinzugefügt werden. Wenn Sie diese Option auswählen, können Sie die Pipeline weiterhin manuell starten.

      Bei der Einrichtung oder Bearbeitung der Pipeline kann der Implementierungsmanager festlegen, wie sich die Pipeline verhält, wenn bei einem der Quality Gates (Test der Code-Qualität, Sicherheitstest und Leistungstest) ein wichtiger Fehler auftritt.

      Das ist für Kunden nützlich, die die Prozesse stärker automatisieren möchten. Die verfügbaren Optionen sind:
   Sie können das wichtige Verhalten von Fehlermetriken definieren, um die Pipeline zu starten.

   * **Jedes Mal fragen**: Das ist die Standardeinstellung und erfordert manuelles Eingreifen bei einem wichtigen Fehler.
   * **Sofort scheitern** - Wenn diese Option aktiviert ist, wird die Pipeline bei einem wichtigen Fehler abgebrochen. Damit wird im Grunde ein Benutzer simuliert, der manuell jeden Fehler ablehnt.
   * **Sofort fortfahren** - Wenn diese Option aktiviert ist, wird die Pipeline bei einem wichtigen Fehler automatisch fortgesetzt. Damit wird im Grunde ein Anwender simuliert, der manuell jeden Fehler genehmigt.


1. Auswählen **[Vollständiger Stack-Code](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#full-stack-pipeline)** oder **[Frontend-Code](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end)**.

   Wenn Sie **Frontend-Code**, müssen Sie die **Repository**, **Git-Verzweigung** und **Code-Speicherort**, wie in der folgenden Abbildung dargestellt:

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-confignew1.png)

   Wenn Sie **Vollständiger Stack-Code**, müssen Sie die **Repository** und **Git-Verzweigung**, wie in der Abbildung dargestellt:
   ![](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-fullstack1.png)

   >[!IMPORTANT]
   >Wenn für die ausgewählte Umgebung bereits eine Pipeline mit vollständigem Stack-Code vorhanden ist, wird diese Auswahl deaktiviert.

   >[!NOTE]
   >Bevor Sie mit der Konfiguration der Front-End-Pipelines beginnen, lesen Sie [Journey zur AEM SchnellSite-Erstellung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites-journey/quick-site/overview.html) für einen End-to-End-Workflow mit dem einfach zu verwendenden AEM Tool zur schnellen Site-Erstellung. Diese Dokumentations-Website hilft Ihnen, die Front-End-Entwicklung Ihrer AEM-Site zu optimieren und Ihre Site ohne AEM Backend-Wissen schnell anzupassen.

1. Die neu erstellte Nicht-Produktions-Pipeline wird jetzt im **Pipelines** Karte.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-fullstack2.png)


   Die Pipeline wird auf der Karte auf dem Startbildschirm mit vier Aktionen angezeigt, wie unten dargestellt:

   * **Hinzufügen** - ermöglicht das Hinzufügen einer neuen Pipeline.
   * **Alle anzeigen** - ermöglicht dem Benutzer, alle Pipelines anzuzeigen.
   * **Auf Repository-Informationen zugreifen**: Ermöglicht es dem Benutzer, die für den Zugriff auf das Cloud Manager-Git-Repository erforderlichen Informationen abzurufen.
   * **Weitere Informationen**: Führt zu weiteren Informationen über die Dokumentation zur CI/CD-Pipeline.