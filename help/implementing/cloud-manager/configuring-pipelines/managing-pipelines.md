---
title: Verwalten von Pipelines
description: Erfahren Sie, wie Sie Ihre vorhandenen Pipelines verwalten, einschließlich Bearbeiten, Ausführen und Löschen.
index: true
exl-id: 4aff5a84-134a-43fa-8de8-8d564f4edd16
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 500e1b78fb9688601848fc17f312fc23be83bcb0
workflow-type: tm+mt
source-wordcount: '1109'
ht-degree: 98%

---


# Verwalten von Pipelines {#managing-pipelines}

Erfahren Sie, wie Sie Ihre vorhandenen Pipelines verwalten, einschließlich Bearbeiten, Ausführen und Löschen.

## Pipeline-Karte {#pipeline-card}

Die Karte **Pipelines** auf der Seite **Programmübersicht** in Cloud Manager bietet Ihnen einen Überblick über alle Ihre Pipelines und deren aktuellen Status.

![Pipelines-Karte in Cloud Manager](/help/implementing/cloud-manager/assets/configure-pipeline/pipelines-card.png)

Wenn Sie auf die Schaltfläche mit den Auslassungspunkten neben jeder Pipeline klicken, können Sie die folgenden Aktionen ausführen.

* [Pipeline ausführen](#running-pipelines)
* [Pipeline bearbeiten](#editing-pipelines)
* [Pipeline löschen](#deleting-pipelines)
* [Anzeigen von Details](#view-details)

Am Ende der Pipeline-Liste befinden sich allgemeine Optionen.

* **Hinzufügen**: Dient zum [Hinzufügen einer neuen Produktions-Pipeline](configuring-production-pipelines.md) oder [Hinzufügen einer neuen produktionsfremden Pipeline](configuring-non-production-pipelines.md)
* **Alle anzeigen**: Leitet den Anwender zum Bildschirm „Pipelines“, wo alle Pipelines in einer detaillierteren Tabelle angezeigt werden.
* **Zugriff auf Repo Info**: Zeigt die Informationen an, die für den Zugriff auf das Cloud Manager-Git-Repository erforderlich sind
* **Weitere Infos**: Navigiert zu den Dokumentationsressourcen zur CI/CD-Pipeline.

## Fenster „Pipelines“ {#pipelines}

Das Fenster **Pipelines** zeigt eine vollständige Liste aller Pipelines für das ausgewählte Programm an. Dies ist nützlich, da es umfassendere Informationen enthält als der Abschnitt [Pipeline-Karte](#pipeline-card).

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus.

1. Wählen Sie auf der Seite **Programmübersicht** die Registerkarte **Pipelines** aus, um zum Fenster **Pipelines** zu wechseln.

1. Hier können Sie eine Liste aller Pipelines für das Programm sehen und die Ausführung von Pipelines starten und stoppen, wie Sie es in der **Pipelines-Karte** tun würden.

Wenn Sie während der Pipeline-Ausführung auf das Informationssymbol in der Spalte **Status** klicken, werden Details zur Ausführung angezeigt.

![Details zur Pipeline-Ausführung](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-status.png)

Klicken Sie auf **Details anzeigen**, um zu den [Details zur Pipeline-Ausführung](#view-details) zu gelangen.

Sie können auch auf die Schaltfläche mit den Auslassungspunkten für die Pipeline klicken, um zusätzliche Aktionen durchzuführen, die dem Pipeline-Status entsprechen, z. B. die Pipeline [bearbeiten](#editing-pipelines) oder die [Ausführung abbrechen](#cancel).

![Pipeline-Aktionen](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-actions.png)

## Fenster „Aktivität“ {#activity}

Das Fenster **Aktivität** zeigt eine vollständige Liste aller Pipeline-Ausführungen für das ausgewählte Programm sowie andere wichtige Programmereignisse an.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Wählen Sie auf der Seite **Programmübersicht** die Registerkarte **Aktivität** aus, um zum Fenster **Aktivität** zu wechseln.

1. Hier sehen Sie eine Liste aller Pipeline-Ausführungen für das Programm, einschließlich aktueller und vorheriger Ausführungen.

Wenn Sie während der Pipeline-Ausführung auf das Informationssymbol in der Spalte **Status** klicken, werden Details zur Ausführung angezeigt.

![Details zur Pipeline-Ausführung](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-activity.png)

Durch Tippen oder Klicken auf die Zeile für die Pipeline-Ausführung gelangen Sie zu den [Details zur Pipeline-Ausführung](#view-details).

Sie können auch auf die Schaltfläche mit den Auslassungspunkten klicken, um zusätzliche Aktionen für die Pipeline-Ausführung durchzuführen, z. B. Details anzeigen oder das Protokoll herunterladen, wodurch Sie zur [Seite mit den Pipeline-Details](#view-details) gelangen.

![Aktionen zur Pipeline-Ausführung](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-execution-actions.png)

## Ausführen von Pipelines {#running-pipelines}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Navigieren Sie von der Seite **Programmübersicht** zur Karte **Pipelines**, klicken Sie auf die Schaltfläche mit den Auslassungspunkten neben der Pipeline, die Sie ausführen, und wählen Sie im Menü **Ausführen** aus.

1. Der Pipeline-Ausführung beginnt. Dies wird in der Spalte **Status** angezeigt.

Sie können die Details der Ausführung sehen, indem Sie erneut auf die Schaltfläche mit den Auslassungspunkten klicken und **[Details anzeigen](#view-details)** auswählen.

Je nach Pipeline-Typ können Sie die Ausführung möglicherweise abbrechen, indem Sie erneut auf die Schaltfläche mit den Auslassungspunkten klicken und **Abbrechen** auswählen.

## Bearbeiten einer Pipeline {#editing-pipelines}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Navigieren Sie von der Seite **Programmübersicht** zur Karte **Pipelines**, klicken Sie auf die Schaltfläche mit den Auslassungspunkten neben der Pipeline, die Sie bearbeiten möchten, und wählen Sie im Menü **Bearbeiten** aus.

1. Daraufhin wird das Dialogfeld **Produktions-Pipeline bearbeiten** bzw. **Produktionsfremde Pipeline bearbeiten** angezeigt, sodass Sie die Details bearbeiten können, die Sie beim Erstellen der Pipeline eingegeben haben.

   * Auf den folgenden Seiten finden Sie Details zu den Feldern und Konfigurationsoptionen, die für Pipelines verfügbar sind.
      * [Konfigurieren von Produktions-Pipelines](configuring-production-pipelines.md)
      * [Konfigurieren von produktionsfremden Pipelines](configuring-non-production-pipelines.md)

1. Klicken Sie auf **Aktualisieren**, nachdem Sie die Pipeline bearbeitet haben.

>[!NOTE]
>
>Pipelines, die gerade ausgeführt werden, können nicht bearbeitet werden.

>[!NOTE]
>
>Pipelines auf Web-Ebene und Konfigurations-Pipelines werden bei privaten Repositorys nicht unterstützt. Weitere Informationen und die vollständige Liste der Einschränkungen finden Sie unter [Hinzufügen eines privaten Repositorys in Cloud Manager](/help/implementing/cloud-manager/managing-code/private-repositories.md) .

## Löschen von Pipelines {#deleting-pipelines}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Navigieren Sie von der Seite **Programmübersicht** zur Karte **Pipelines**, klicken Sie auf die Schaltfläche mit den Auslassungspunkten neben der Pipeline, die Sie löschen möchten, und wählen Sie im Menü **Löschen** aus.

>[!NOTE]
>
>Pipelines, die gerade ausgeführt werden, können nicht gelöscht werden.

## Pipeline-Details anzeigen {#view-details}

Sie können die Details einer Pipeline anzeigen, um den Status und die Protokolle der letzten Ausführung anzuzeigen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie von der Seite **Programmübersicht** zur Karte **Pipelines**, klicken Sie auf die Schaltfläche mit den Auslassungspunkten neben der Pipeline, die Sie ausführen, und wählen Sie **Details anzeigen** aus dem Menü aus.

1. Sie gelangen zur Detailseite der Pipeline, die gerade ausgeführt wird.

![Pipeline-Details](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-running-details.png)

Von hier aus können Sie den Status der verschiedenen Schritte der Pipeline einsehen und Build-Protokolle zu Diagnosezwecken abrufen. Weitere Informationen zur Bereitstellung von Code und Testläufen finden Sie im Dokument [Bereitstellen des Codes](/help/implementing/cloud-manager/deploy-code.md).

Es werden alle Schritte einer Pipeline-Ausführung angezeigt, wobei die Schritte, die noch nicht gestartet wurden, ausgegraut sind. Die abgeschlossenen Schritte werden mit ihrer jeweiligen Dauer angezeigt.

Sobald ein Pipeline-Schritt abgeschlossen ist, wird eine Zusammenfassung angezeigt.

![Schrittzusammenfassung](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-step.png)

Wählen Sie den Link **Details anzeigen** aus, um den Abschnitt **Dauer** anzuzeigen. Hier ist die durchschnittliche Dauer der Pipeline basierend auf dem Verlaufs-Trend für dieses Programm aufgeführt.

![Dauer](/help/implementing/cloud-manager/assets/configure-pipeline/duration.png)

Wenn Ihre Pipeline den Schritt **Code-Scan** umfasste, durch den Probleme aufgetreten sind, können Sie auf die Schaltfläche **Details herunterladen** tippen oder klicken, um eine Liste von [Code-Qualitätstests](/help/implementing/cloud-manager/code-quality-testing.md) anzuzeigen, die nicht bestanden wurden.

![Fehler bei der Code-Qualität](assets/managing-pipelines-code-quality-issues.png)

In der CSV-Datei ist eine Spalte **Speicherort der Projektdatei** verfügbar, die den Speicherort des fehlerhaften Codes angibt. Diese Spalte ist der projektrelative Pfad, während die Spalte **Dateispeicherort** von Maven generiert wird.

![Details zu Problemen beim Scannen des Projekt-Codes](assets/managing-pipelines-code-quality-details.png)

>[!NOTE]
>
>Sie können nur Details einer Pipeline anzeigen, die gerade ausgeführt wird oder schon mindestens einmal ausgeführt worden ist.

## Pipelines abbrechen {#cancel}

Wenn sich eine Pipeline in der Validierungs- oder Bildaufbau-Phase befindet, können Sie die Pipeline-Ausführung sicher abbrechen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Klicken Sie in der Programmübersichtsseite auf der Karte **Pipelines** auf die Schaltfläche mit den Auslassungspunkten der Pipeline, die Sie abbrechen möchten.

   ![Eine Pipeline abbrechen](/help/implementing/cloud-manager/assets/cancel-pipeline.png)

1. Wählen Sie **Abbrechen** aus.

Alternativ können Sie eine Pipeline auf der Pipeline-Detailseite abbrechen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie von der Seite **Programmübersicht** zur Karte **Pipelines** und wählen Sie die Pipeline aus, die Sie abbrechen möchten.

1. Sie gelangen zur Detailseite der Pipeline, die gerade ausgeführt wird.

   ![Details zum Abbrechen der Pipeline](/help/implementing/cloud-manager/assets/cancel-pipeline-details.png)

1. Wählen Sie **Abbrechen** aus.
