---
title: Bearbeiten einer Produktions-Pipeline
description: Bearbeiten einer Produktions-Pipeline
index: false
source-git-commit: b9d28088ad18a389108ebfb81aa750c63e637922
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---


# Bearbeiten einer Produktions-Pipeline {#edit-prod-pipeline}

Sie können die Pipeline-Konfigurationen über die **Programmübersicht** Seite.

Gehen Sie wie folgt vor, um die konfigurierte Pipeline zu bearbeiten:

1. Navigieren Sie zu **Pipelines** der Karte **Programmübersicht** Seite.

1. Klicken Sie auf **...** von **Pipelines** Karte und klicken Sie auf **Bearbeiten**, wie in der folgenden Abbildung dargestellt.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-edit1.png)

1. Die **Produktions-Pipeline bearbeiten** angezeigt.

   1. Die **Konfiguration** -Tab können Sie die **Pipeline-Name**, **Deployment Trigger** und **Verhalten bei wichtigen Metriken mit Fehlern**.

      >[!NOTE]
      >Siehe [Hinzufügen und Verwalten von Repositorys](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) , um zu erfahren, wie Sie Repositorys in Cloud Manager hinzufügen und verwalten.

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-edit2.png)


   1. Die **Quelle** bietet Ihnen die Möglichkeit, die Option **Anhalten vor der Bereitstellung in der Produktion** und **Geplant** Optionen aus **Produktionsbereitstellungsoptionen**.

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/prod-pipeline-editnotier.png)

   1. Die **Erlebnisprüfung** können Sie neue Seiten aktualisieren oder hinzufügen.

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-edit4.png)

1. Klicken Sie auf **Aktualisieren** nachdem Sie die Pipeline bearbeitet haben.

## Zusätzliche Produktions-Pipeline-Aktionen {#additional-prod-actions}

### Ausführen einer Produktions-Pipeline {#run-prod}

Sie können die Produktions-Pipeline über die Pipelines-Karte ausführen:

1. Navigieren Sie zu **Pipelines** der Karte **Programmübersicht** Seite.

1. Klicken Sie auf **...** von **Pipelines** Karte und klicken Sie auf **Ausführen**, wie in der folgenden Abbildung dargestellt.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/prod-run.png)

### Löschen einer Produktions-Pipeline {#delete-prod}

Sie können die Produktions-Pipeline aus der Pipelines-Karte löschen:

1. Navigieren Sie zu **Pipelines** der Karte **Programmübersicht** Seite.

1. Klicken Sie auf **...** von **Pipelines** Karte und klicken Sie auf **Löschen**, wie in der folgenden Abbildung dargestellt.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/prod-delete.png)

   >[!NOTE]
   >Ein Benutzer mit der Rolle &quot;Bereitstellungsmanager&quot;kann die Produktions-Pipeline jetzt auf Self-Service-Weise über die **Löschen** -Option auf der Pipeline-Karte aus.