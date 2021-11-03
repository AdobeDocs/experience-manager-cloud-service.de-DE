---
title: Konfigurieren von Nicht-Produktions-Pipelines
description: Auf dieser Seite erfahren Sie mehr über das Konfigurieren einer produktionsfremden Pipeline in Cloud Manager
index: false
source-git-commit: fe3bd08e32cef20403d3d2799d027b3ed03e6d36
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 20%

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

1. Auswählen **[Vollständiger Stack-Code](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#full-stack-pipeline)** oder **[Frontend-Code](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end)**. Sie können die **Repository** und **Git-Verzweigung**. Klicken Sie auf **Speichern**.

   >[!IMPORTANT]
   >Wenn für die ausgewählte Umgebung bereits eine Pipeline mit vollständigem Stack-Code vorhanden ist, wird diese Auswahl deaktiviert.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add3.png)

   >[!NOTE]
   >Bevor Sie mit der Konfiguration der Front-End-Pipelines beginnen, lesen Sie AEM Journey zur schnellen Site-Erstellung , um einen End-to-End-Workflow mit dem einfach zu verwendenden AEM Tool zur schnellen Site-Erstellung zu erhalten. Diese Dokumentations-Website hilft Ihnen, die Front-End-Entwicklung Ihrer AEM-Site zu optimieren und Ihre Site ohne AEM Backend-Wissen schnell anzupassen.

1. Die neu erstellte Nicht-Produktions-Pipeline wird jetzt im **Pipelines** Karte.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add4.png)


   Die Pipeline wird auf der Karte auf dem Startbildschirm mit drei Aktionen angezeigt, wie unten dargestellt:

   * **Hinzufügen** - ermöglicht das Hinzufügen einer neuen Pipeline.
   * **Auf Repository-Informationen zugreifen**: Ermöglicht es dem Benutzer, die für den Zugriff auf das Cloud Manager-Git-Repository erforderlichen Informationen abzurufen.
   * **Weitere Informationen**: Führt zu weiteren Informationen über die Dokumentation zur CI/CD-Pipeline.