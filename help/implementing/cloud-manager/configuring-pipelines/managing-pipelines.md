---
title: Verwalten von Pipelines
description: Erfahren Sie, wie Sie Ihre vorhandenen Pipelines verwalten, einschließlich ihrer Bearbeitung, Ausführung und Löschung.
index: true
exl-id: 4aff5a84-134a-43fa-8de8-8d564f4edd16
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: f7a8e823f058115f11241f0864517432a7dea5ab
workflow-type: tm+mt
source-wordcount: '1164'
ht-degree: 34%

---


# Verwalten von Pipelines {#managing-pipelines}

Erfahren Sie, wie Sie Ihre vorhandenen Pipelines verwalten, einschließlich ihrer Bearbeitung, Ausführung und Löschung.

## Pipeline-Karte {#pipeline-card}

Die Karte **Pipelines** auf der Seite **Programmübersicht** in Cloud Manager bietet Ihnen einen Überblick über alle Ihre Pipelines und deren aktuellen Status.

![Pipelines-Karte in Cloud Manager](/help/implementing/cloud-manager/assets/configure-pipeline/pipelines-card.png)

Wenn Sie auf ![Ellipse - Weitere Symbole](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) neben jeder Pipeline klicken, können Sie die folgenden Aktionen ausführen:

* [Pipeline ausführen](#running-pipelines)
* [Pipeline abbrechen](#cancel)
* [Bearbeiten einer Pipeline](#editing-pipelines)
* [Pipeline löschen](#deleting-pipelines)
* [Letzte Ausführungsdetails einer Pipeline anzeigen](#view-details)

Am unteren Rand der Pipelineliste befinden sich die folgenden allgemeinen Optionen:

* **Hinzufügen** - Fügen Sie [eine neue Produktions-Pipeline hinzu](configuring-production-pipelines.md) oder fügen Sie [ eine neue Nicht-Produktions-Pipeline hinzu](configuring-non-production-pipelines.md)
* **Alle anzeigen**: Leitet den Anwender zum Bildschirm „Pipelines“, wo alle Pipelines in einer detaillierteren Tabelle angezeigt werden.
* **Zugriff auf Repo Info**: Zeigt die Informationen an, die für den Zugriff auf das Cloud Manager-Git-Repository erforderlich sind
* **Weitere Infos**: Navigiert zu den Dokumentationsressourcen zur CI/CD-Pipeline.

## Pipelines-Seite {#pipelines}

Auf der Seite **Pipelines** wird eine vollständige Liste aller Pipelines für das ausgewählte Programm angezeigt. Diese Informationen sind nützlich, da sie umfassendere Informationen enthalten, als auf der [Pipeline-Karte](#pipeline-card) verfügbar sind.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus.

1. Klicken Sie auf der Seite **Programmübersicht** auf die Registerkarte ![Pipeline - Workflow-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Workflow_18_N.svg) **Pipelines** .

1. Auf der Seite **Pipelines** können Sie eine Liste aller Pipelines für das Programm sehen und die Pipelineausführung starten und stoppen, wie Sie es auf der **Pipelines Card** tun würden.

Wenn eine Pipeline ausgeführt wird, klicken Sie in der Spalte **Status** auf ![Info - Medium icon](https://spectrum.adobe.com/static/icons/ui_18/InfoMedium.svg) , um ein Popup mit Details zur Ausführung anzuzeigen. Klicken Sie im Popup-Fenster auf **Details anzeigen** , um die [Details der Pipeline-Ausführung anzuzeigen](#view-details).

![Details zur Pipeline-Ausführung](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-status.png)


Sie können auch auf das Symbol &quot;![Ellipse - Mehr&quot;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) neben der Pipeline klicken, um zusätzliche Aktionen durchzuführen, die dem Pipeline-Status entsprechen, z. B. [Bearbeiten](#editing-pipelines) oder [Abbrechen der Ausführung](#cancel).

![Pipeline-Aktionen](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-actions.png)

## Aktivitätsseite {#activity}

Die Seite **Aktivität** enthält eine vollständige Liste aller Pipelines, die für das ausgewählte Programm ausgeführt werden, sowie weitere wichtige Programmereignisse.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Klicken Sie auf der Seite **Programmübersicht** im Seitenmenü auf das Symbol ![Glockensymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Bell_18_N.svg) **Aktivität**.

1. Auf der Seite **Aktivität** können Sie eine Liste aller Pipeline-Ausführungen für das Programm sehen, einschließlich aktueller und historischer Ausführungen.

Wenn eine Pipeline ausgeführt wird, können Sie in der Spalte **Status** auf &quot;![Info - Medium&quot;](https://spectrum.adobe.com/static/icons/ui_18/InfoMedium.svg) klicken, um ein Popup mit Informationen zur Ausführung anzuzeigen.

![Details zur Pipeline-Ausführung](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-activity.png)

Klicken Sie auf die Zeile, die die Pipeline-Ausführung darstellt, um die [Details der Pipeline-Ausführung](#view-details) anzuzeigen.

Sie können auch auf das Symbol &quot;![Auslassungspunkte - Mehr&quot;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) klicken, um zusätzliche Maßnahmen bei der Pipelineausführung zu ergreifen, z. B. die Details der Pipeline anzuzeigen oder das Protokoll herunterzuladen, über das Sie zur Seite &quot;[Pipeline-Details&quot;](#view-details) gelangen.

![Aktionen zur Pipeline-Ausführung](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-execution-actions.png)

## Pipeline ausführen {#running-pipelines}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Navigieren Sie von der Seite **Programmübersicht** aus zur Karte **Pipelines**.

1. Klicken Sie neben der von Ihnen ausgeführten Pipeline auf das Symbol ![Auslassungspunkte - Mehr .](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)

1. Klicken Sie im Dropdown-Menü auf ![Ausführen - Wiedergabe-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_PlayCircle_18_N.svg) **Ausführen**.

   Die Pipeline wird gestartet und die Spalte **Status** zeigt den Fortschritt an.

Sie können die Details der Ausführung sehen, indem Sie erneut auf das Symbol ![Auslassungspunkte - Mehr](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) klicken und auf **[Details anzeigen](#view-details)** klicken.

Je nach Pipeline-Typ können Sie die Ausführung möglicherweise abbrechen, indem Sie erneut auf das Symbol ![Auslassungspunkte - Mehr](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) klicken und auf **Abbrechen** klicken.

## Bearbeiten einer Pipeline {#editing-pipelines}

Sie können eine Pipeline bearbeiten, wenn sie nicht ausgeführt wird.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Navigieren Sie von der Seite **Programmübersicht** aus zur Karte **Pipelines**.

1. Klicken Sie neben der Pipeline, die Sie bearbeiten möchten, auf das Symbol &quot;![Ellipse - Mehr&quot;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg).

1. Klicken Sie im Dropdownmenü auf **Bearbeiten**.

1. Bearbeiten Sie im Dialogfeld **Produktions-Pipeline bearbeiten** oder **Nicht-Produktions-Pipeline bearbeiten** dieselben Details, die Sie beim Erstellen der Pipeline eingegeben haben.

   Auf den folgenden Seiten finden Sie Details zu den Feldern und Konfigurationsoptionen, die für Pipelines verfügbar sind.
   * [Konfigurieren einer Produktions-Pipeline](configuring-production-pipelines.md)
   * [Konfigurieren einer produktionsfremden Pipeline](configuring-non-production-pipelines.md)

1. Wenn Sie fertig sind, klicken Sie auf **Aktualisieren**.

>[!NOTE]
>
>Pipelines auf Web-Ebene und Konfigurations-Pipelines werden bei privaten Repositorys nicht unterstützt. Weitere Informationen und die vollständige Liste der Einschränkungen finden Sie unter [Hinzufügen eines privaten GitHub-Repositorys in Cloud Manager](/help/implementing/cloud-manager/managing-code/private-repositories.md) .

## Pipeline löschen {#deleting-pipelines}

Sie können eine Pipeline löschen, wenn sie nicht ausgeführt wird.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Navigieren Sie von der Seite **Programmübersicht** aus zur Karte **Pipelines**.

1. Klicken Sie neben der von Ihnen ausgeführten Pipeline auf das Symbol ![Auslassungspunkte - Mehr .](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)

1. Klicken Sie im Dropdownmenü auf **Löschen**.


## Letzte Ausführungsdetails einer Pipeline anzeigen {#view-details}

Sie können die Details einer Pipeline überprüfen, um den Status und die Protokolle der letzten Ausführung anzuzeigen. Sie können jedoch nur auf die Details zugreifen, wenn die Pipeline derzeit ausgeführt wird oder mindestens einmal ausgeführt wurde.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Navigieren Sie von der Seite **Programmübersicht** aus zur Karte **Pipelines**.

1. Klicken Sie im Dropdown-Menü neben der von Ihnen ausgeführten Pipeline auf das Symbol ![Ellipsis - More](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) .

1. Klicken Sie im Dropdown-Menü auf **Letzte Ausführung anzeigen**.

   Sie gelangen zur Detailseite der Pipeline, die gerade ausgeführt wird.

   ![Pipeline-Details](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-running-details.png)

   Von hier aus können Sie den Status der verschiedenen Schritte der Pipeline einsehen und Build-Protokolle zu Diagnosezwecken abrufen. Weitere Informationen zur Codebereitstellung und zur Ausführung von Tests finden Sie unter [Bereitstellen Ihres Codes](/help/implementing/cloud-manager/deploy-code.md) .

   Es werden alle Schritte einer Pipeline-Ausführung angezeigt, wobei die Schritte, die noch nicht gestartet wurden, ausgegraut sind. Die abgeschlossenen Schritte werden mit ihrer jeweiligen Dauer angezeigt.

   Nach Abschluss eines Pipelineschritts wird eine Zusammenfassung angezeigt.

   ![Schrittzusammenfassung](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-step.png)

1. Klicken Sie auf **Details anzeigen** , um den Abschnitt **Dauer** zu erweitern, in dem Sie die durchschnittliche Dauer der Pipeline basierend auf den historischen Trends des Programms anzeigen können.

   ![Dauer](/help/implementing/cloud-manager/assets/configure-pipeline/duration.png)

1. Wenn Ihre Pipeline einen Schritt **Codescan** enthält, der Probleme markiert, klicken Sie auf **Download Details** , um auf eine Liste mit [Code-Qualitätstests](/help/implementing/cloud-manager/code-quality-testing.md) zuzugreifen, die nicht bestanden werden konnten.

   ![Fehler bei der Code-Qualität](assets/managing-pipelines-code-quality-issues.png)

   Die CSV-Datei enthält eine Spalte **Speicherort der Projektdatei**, die den Pfad zum problematischen Code relativ zum Projekt anzeigt. Im Gegensatz dazu spiegelt die Spalte **Dateispeicherort** den vom Maven generierten Pfad wider.

   ![Details zu Problemen beim Scannen des Projekt-Codes](assets/managing-pipelines-code-quality-details.png)

## Pipeline abbrechen {#cancel}

Sie können die Pipeline-Ausführung sicher abbrechen, wenn sie sich in der Validierungs- oder Build-Bildphase befindet.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Klicken Sie auf der Seite mit der Programmübersicht auf das Symbol ![Ellipse - Weitere Zeichen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) der Pipeline, die Sie auf der Karte **Pipelines** abbrechen möchten.

   ![ Abbrechen einer Pipeline](/help/implementing/cloud-manager/assets/cancel-pipeline.png)

1. Klicken Sie auf **Abbrechen**.

Alternativ können Sie eine Pipeline auf der Seite mit den Pipeline-Details abbrechen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Navigieren Sie auf der Seite **Programmübersicht** zur Registerkarte ![Pipelines - Workflow-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Workflow_18_N.svg) **Pipelines** und wählen Sie die Pipeline aus, die Sie abbrechen möchten.

   Sie gelangen zur Detailseite der Pipeline, die gerade ausgeführt wird.

   ![Details zum Abbrechen der Pipeline](/help/implementing/cloud-manager/assets/cancel-pipeline-details.png)

1. Klicken Sie auf **Abbrechen**.
