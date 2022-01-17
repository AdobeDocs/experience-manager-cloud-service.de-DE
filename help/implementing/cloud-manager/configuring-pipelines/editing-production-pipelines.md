---
title: Bearbeiten einer Produktions-Pipeline
description: Bearbeiten einer Produktions-Pipeline
index: true
source-git-commit: d090329c46155d77a7b132583c777c09555a03c9
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 96%

---


# Bearbeiten einer Produktions-Pipeline {#edit-prod-pipeline}

Sie können die Pipeline-Konfigurationen über die Seite **Programm-Überblick** bearbeiten.

>[!IMPORTANT]
>Sie können eine ausgeführte Pipeline nicht bearbeiten.

Gehen Sie wie folgt vor, um die konfigurierte Pipeline zu bearbeiten:

1. Gehen Sie von der Seite **Programm-Überblick** zur Karte **Pipelines**.

1. Klicken Sie von der Karte **Pipelines** aus auf **...** und klicken Sie auf **Bearbeiten**, wie in der folgenden Abbildung dargestellt.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-edit1.png)

1. Das Dialogfeld **Produktions-Pipeline bearbeiten** erscheint.

   1. Von der Registerkarte **Konfiguration** aus können Sie den **Pipeline-Namen**, den **Implementierungs-Trigger** und das **Verhalten bei Ausfällen von wichtigen Metriken** ändern.

      >[!NOTE]
      >Siehe [Hinzufügen und Verwalten von Repositorys](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md), um zu erfahren, wie Sie Repositorys in Cloud Manager hinzufügen und verwalten.

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-edit2.png)


   1. Auf der Registerkarte **Quelle** können Sie die Optionen **Pause vor Bereitstellung in Produktion** und **Geplant** aus den **Optionen für die Produktionsimplementierung** aktivieren oder deaktivieren.

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/prod-pipeline-editnotier.png)

   1. Mit der Option **Experience Audit** können Sie Seiten ändern oder neue Seiten hinzufügen.

      ![](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-edit4.png)

1. Klicken Sie auf **Aktualisieren**, nachdem Sie die Pipeline bearbeitet haben.

## Zusätzliche Produktions-Pipeline-Aktionen {#additional-prod-actions}

### Ausführen einer Produktions-Pipeline {#run-prod}

Sie können die Produktions-Pipeline über die Karte „Pipelines“ ausführen:

1. Gehen Sie von der Seite **Programm-Überblick** zur Karte **Pipelines**.

1. Klicken Sie von der Karte **Pipelines** aus auf **...** und klicken Sie auf **Ausführen**, wie in der folgenden Abbildung dargestellt.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/prod-run.png)

### Löschen einer Produktions-Pipeline {#delete-prod}

Sie können die Produktions-Pipeline von der Karte „Pipelines“ aus löschen:

1. Gehen Sie von der Seite **Programm-Überblick** zur Karte **Pipelines**.

1. Klicken Sie von der Karte **Pipelines** aus auf **...** und klicken Sie auf **Löschen**, wie in der folgenden Abbildung dargestellt.

   ![](/help/implementing/cloud-manager/assets/configure-pipeline/prod-delete.png)

   >[!NOTE]
   >Ein Benutzer in der Rolle des Implementierungs-Managers kann die Produktions-Pipeline jetzt im Selbstbedienungsmodus über die Option **Löschen** auf der Karte „Pipeline“ löschen.