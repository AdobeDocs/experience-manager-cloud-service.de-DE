---
title: Verwalten von Pipelines
description: Erfahren Sie, wie Sie Ihre vorhandenen Pipelines verwalten, einschließlich Bearbeiten, Ausführen und Löschen.
index: true
exl-id: 4aff5a84-134a-43fa-8de8-8d564f4edd16
source-git-commit: bc3c054e781789aa2a2b94f77b0616caec15e2ff
workflow-type: tm+mt
source-wordcount: '938'
ht-degree: 45%

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
* [Details anzeigen](#view-details)

Am Ende der Pipeline-Liste befinden sich allgemeine Optionen.

* **Hinzufügen**: Dient zum [Hinzufügen einer neuen Produktions-Pipeline](configuring-production-pipelines.md) oder [Hinzufügen einer neuen produktionsfremden Pipeline](configuring-non-production-pipelines.md)
* **Alle anzeigen**: Leitet den Anwender zum Bildschirm „Pipelines“, wo alle Pipelines in einer detaillierteren Tabelle angezeigt werden.
* **Zugriff auf Repo Info**: Zeigt die Informationen an, die für den Zugriff auf das Cloud Manager-Git-Repository erforderlich sind
* **Weitere Infos**: Navigiert zu den Dokumentationsressourcen zur CI/CD-Pipeline.

## Pipelines Window {#pipelines}

Die **Pipelines** zeigt eine vollständige Liste aller Pipelines für das ausgewählte Programm an. Dies ist nützlich, da es umfassendere Informationen enthält, als im Abschnitt [Pipeline-Karte.](#pipeline-card)

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Aus dem **Programmübersicht** Seite, wählen Sie die **Pipelines** Registerkarte, um zu der **Pipelines** Fenster.

1. Hier sehen Sie eine Liste aller Pipelines für das Programm sowie die Ausführung der Pipeline wie im **Pipelines Card**.

Wenn eine Pipeline ausgeführt wird, bewegen Sie den Mauszeiger über die **Status** enthält Details zur Ausführung.

![Details zur Pipelineausführung](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-status.png)

Tippen oder Klicken **Details anzeigen** bringt Sie zu [Details zur Pipelineausführung.](#view-details)

## Aktivitätsfenster {#activity}

Die **Tätigkeiten** zeigt eine vollständige Liste aller Pipelines-Ausführungen für das ausgewählte Programm an.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Aus dem **Programmübersicht** Seite, wählen Sie die **Aktivität** Registerkarte, um zu der **Aktivität** Fenster.

1. Hier sehen Sie eine Liste aller Pipeline-Ausführungen für das Programm, einschließlich aktueller und historischer Ausführungen.

Wenn eine Pipeline ausgeführt wird, bewegen Sie den Mauszeiger über die **Status** enthält Details zur Ausführung.

![Details zur Pipelineausführung](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-activity.png)

Tippen oder Klicken **Details anzeigen** bringt Sie zu [Details zur Pipelineausführung.](#view-details)

## Ausführen von Pipelines {#running-pipelines}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie zum **Pipelines** Karte aus der **Programmübersicht** und klicken Sie auf die Suchschaltfläche neben der Pipeline, die Sie ausführen, wählen Sie **Ausführen** aus dem Menü.

1. Der Pipeline-Ausführung beginnt und wird durch die Spalte **Status** angezeigt.

Sie können die Details der Ausführung sehen, indem Sie erneut auf die Schaltfläche mit den Auslassungspunkten klicken und **[Details anzeigen](#view-details)** auswählen.

Je nach Pipeline-Typ können Sie die Ausführung möglicherweise abbrechen, indem Sie erneut auf die Schaltfläche mit den Auslassungspunkten klicken und **Abbrechen** auswählen.

## Bearbeiten von Pipelines {#editing-pipelines}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie zum **Pipelines** Karte aus der **Programmübersicht** und klicken Sie auf die Suchschaltfläche neben der Pipeline, die Sie bearbeiten möchten, und wählen Sie **Bearbeiten** aus dem Menü.

1. Daraufhin wird das Dialogfeld **Produktions-Pipeline bearbeiten** oder **Produktionsfremde Pipeline bearbeiten** angezeigt, sodass Sie die Details bearbeiten können, die Sie beim Erstellen der Pipeline eingegeben haben.

   * Auf den folgenden Seiten finden Sie Details zu den Feldern und Konfigurationsoptionen, die für Pipelines verfügbar sind.
      * [Konfigurieren von Produktions-Pipelines](configuring-production-pipelines.md)
      * [Konfigurieren von produktionsfremden Pipelines](configuring-non-production-pipelines.md)

1. Klicks **Aktualisieren** nachdem Sie die Pipeline bearbeitet haben.

>[!NOTE]
>
>Eine laufende Pipeline kann nicht bearbeitet werden.

## Löschen von Pipelines {#deleting-pipelines}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie zum **Pipelines** Karte aus der **Programmübersicht** und klicken Sie auf die Suchschaltfläche neben der Pipeline, die Sie ausführen, wählen Sie **Löschen** aus dem Menü.

>[!NOTE]
>
>Eine laufende Pipeline kann nicht gelöscht werden.

## Pipeline-Details anzeigen {#view-details}

Sie können die Details einer Pipeline anzeigen, um den Status und die Protokolle ihrer letzten Ausführung anzuzeigen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie zum **Pipelines** Karte aus der **Programmübersicht** und klicken Sie auf die Suchschaltfläche neben der Pipeline, die Sie ausführen, wählen Sie **Details anzeigen** aus dem Menü.

1. Sie gelangen zur Detailseite der Pipeline, die gerade ausgeführt wird.

![Pipeline-Details](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-running-details.png)

Von hier aus können Sie den Status der verschiedenen Schritte der Pipeline einsehen und Build-Protokolle zu Diagnosezwecken abrufen. Siehe Dokument . [Bereitstellen des Codes](/help/implementing/cloud-manager/deploy-code.md) für weitere Informationen zur Codebereitstellung und zur Ausführung von Tests.

Alle Schritte in einer Pipeline-Ausführung werden angezeigt, wobei die Schritte, die noch nicht gestartet wurden, ausgegraut sind. Die abgeschlossenen Schritte zeigen ihre Dauer an.

Sobald ein Pipeline-Schritt abgeschlossen ist, wird eine Zusammenfassung angezeigt.

![Schrittzusammenfassung](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-step.png)

Wählen Sie die **Details anzeigen** -Link, um die **Dauer** Abschnitt. Dies umfasst die durchschnittliche Dauer der Pipeline basierend auf dem historischen Trend für dieses Programm.

![Dauer](/help/implementing/cloud-manager/assets/configure-pipeline/duration.png)

>[!NOTE]
>
>Sie können nur Details einer Pipeline anzeigen, die gerade ausgeführt wird oder mindestens einmal ausgeführt worden ist.

## Pipelines abbrechen {#cancel}

Wenn sich eine Pipeline in der Validierungs- oder Build-Bildphase befindet, können Sie den Pipeline-Ausführen sicher abbrechen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Klicken Sie auf der Programmübersichtsseite auf die Suchschaltfläche der Pipeline, die Sie abbrechen möchten. **Pipelines** Karte.

   ![Abbruch einer Pipeline](/help/implementing/cloud-manager/assets/cancel-pipeline.png)

1. Auswählen **Abbrechen**.

Alternativ können Sie eine Pipeline auf der Seite mit den Pipeline-Details abbrechen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie zum **Pipelines** Registerkarte aus **Programmübersicht** und wählen Sie die Pipeline aus, die Sie abbrechen möchten.

1. Sie gelangen zur Detailseite der Pipeline, die gerade ausgeführt wird.

   ![Pipeline-Details abbrechen](/help/implementing/cloud-manager/assets/cancel-pipeline-details.png)

1. Auswählen **Abbrechen**.
