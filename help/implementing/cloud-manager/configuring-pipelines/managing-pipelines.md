---
title: Verwalten von Pipelines
description: Erfahren Sie, wie Sie Ihre vorhandenen Pipelines verwalten, einschließlich Bearbeiten, Ausführen und Löschen.
index: true
exl-id: 4aff5a84-134a-43fa-8de8-8d564f4edd16
source-git-commit: 5ad33f0173afd68d8868b088ff5e20fc9f58ad5a
workflow-type: tm+mt
source-wordcount: '516'
ht-degree: 97%

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

## Ausführen von Pipelines {#running-pipelines}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie von der Seite **Programmübersicht** zur Karte **Pipelines**, klicken Sie auf die Schaltfläche mit den Auslassungspunkten neben der Pipeline, die Sie ausführen, und wählen Sie im Menü **Ausführen** aus.

1. Der Pipeline-Ausführung beginnt und wird durch die Spalte **Status** angezeigt.

Sie können die Details der Ausführung sehen, indem Sie erneut auf die Schaltfläche mit den Auslassungspunkten klicken und **[Details anzeigen](#view-details)** auswählen.

Je nach Pipeline-Typ können Sie die Ausführung möglicherweise abbrechen, indem Sie erneut auf die Schaltfläche mit den Auslassungspunkten klicken und **Abbrechen** auswählen.

## Bearbeiten von Pipelines {#editing-pipelines}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie von der Seite **Programmübersicht** zur Karte **Pipelines**, klicken Sie auf die Schaltfläche mit den Auslassungspunkten neben der Pipeline, die Sie bearbeiten möchten, und wählen Sie im Menü **Bearbeiten** aus.

1. Daraufhin wird das Dialogfeld **Produktions-Pipeline bearbeiten** oder **Produktionsfremde Pipeline bearbeiten** angezeigt, sodass Sie die Details bearbeiten können, die Sie beim Erstellen der Pipeline eingegeben haben.

   * Auf den folgenden Seiten finden Sie Details zu allen Feldern und Konfigurationsoptionen, die für Pipelines verfügbar sind.
      * [Konfigurieren von Produktions-Pipelines](configuring-production-pipelines.md)
      * [Konfigurieren von produktionsfremden Pipelines](configuring-non-production-pipelines.md)

1. Klicken Sie auf **Aktualisieren**, nachdem Sie die Pipeline bearbeitet haben.

>[!NOTE]
>
>Eine laufende Pipeline kann nicht bearbeitet werden.

## Löschen von Pipelines {#deleting-pipelines}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie von der Seite **Programmübersicht** zur Karte **Pipelines**, klicken Sie auf die Schaltfläche mit den Auslassungspunkten neben der Pipeline, die Sie löschen möchten, und wählen Sie im Menü **Löschen** aus.

>[!NOTE]
>
>Eine laufende Pipeline kann nicht gelöscht werden.

## Details anzeigen {#view-details}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie von der Seite **Programmübersicht** zur Karte **Pipelines**, klicken Sie auf die Schaltfläche mit den Auslassungspunkten neben der Pipeline, die Sie ausführen, und wählen Sie **Details anzeigen** aus dem Menü.

1. Sie gelangen zur Detailseite der Pipeline, die gerade ausgeführt wird.

![Pipeline-Details](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-running-details.png)

Von hier aus können Sie den Status der verschiedenen Schritte der Pipeline einsehen und Build-Protokolle zu Diagnosezwecken abrufen. Weitere Informationen finden Sie im Dokument [Bereitstellen des Codes](/help/implementing/cloud-manager/deploy-code.md).

>[!NOTE]
>
>Sie können nur Details einer Pipeline anzeigen, die gerade ausgeführt wird oder mindestens einmal ausgeführt worden ist.
