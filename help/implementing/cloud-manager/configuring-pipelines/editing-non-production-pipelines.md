---
title: Bearbeiten einer produktionsfremden Pipeline
description: Bearbeiten einer produktionsfremden Pipeline
index: true
source-git-commit: 7dc9f9a189927f3522445fac36a1606521f410b2
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---


# Bearbeiten einer produktionsfremden Pipeline {#edit-non-prod-pipeline}

Sie können die Pipeline-Konfigurationen über die **Pipelines-Karte** von **Programmübersicht** Seite.

>[!IMPORTANT]
>Sie können eine ausgeführte Pipeline nicht bearbeiten.

Gehen Sie wie folgt vor, um die konfigurierte Nicht-Produktions-Pipeline zu bearbeiten:

1. Navigieren Sie zu **Pipelines** der Karte **Programmübersicht** Seite.

1. Wählen Sie die produktionsfremde Pipeline aus und klicken Sie auf **...**. Klicken Sie auf **Bearbeiten**, wie in der folgenden Abbildung dargestellt.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-edit1.png)

1. Die **Produktions-Pipeline bearbeiten** angezeigt.

   1. Die **Konfiguration** -Tab können Sie die **Pipeline-Name**, **Deployment Trigger** und **Verhalten bei wichtigen Metrikfehlern**.

      >[!NOTE]
      >Siehe [Hinzufügen und Verwalten von Repositorys](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) , um zu erfahren, wie Sie Repositorys in Cloud Manager hinzufügen und verwalten.

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-edit2.png)


   1. Die **Quellcode** -Tab bietet Ihnen die Möglichkeit, die **Repository** und **Git-Verzweigung**.

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-edit3.png)

1. Klicken Sie auf **Aktualisieren** nach Abschluss der Bearbeitung der produktionsfremden Pipeline.

## Zusätzliche produktionsfremde Pipelineaktionen {#additional-nonprod-actions}

### Ausführen einer produktionsfremden Pipeline {#run-nonprod}

Sie können die Produktions-Pipeline über die Pipelines-Karte ausführen:

1. Navigieren Sie zu **Pipelines** der Karte **Programmübersicht** Seite.

1. Klicken Sie auf **...** von **Pipelines** Karte und klicken Sie auf **Ausführen**, wie in der folgenden Abbildung dargestellt.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-run1.png)

### Löschen einer produktionsfremden Pipeline {#delete-nonprod}

Sie können die Produktions-Pipeline aus der Pipelines-Karte löschen:

1. Navigieren Sie zu **Pipelines** der Karte **Programmübersicht** Seite.

1. Klicken Sie auf **...** von **Pipelines** Karte und klicken Sie auf **Löschen**, wie in der folgenden Abbildung dargestellt.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-delete.png)
