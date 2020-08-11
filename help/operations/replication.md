---
title: Replikation
description: Distribution und Fehlerbehebung bei der Replikation.
translation-type: tm+mt
source-git-commit: abb45225e880f3d08b9d26c29e243037564acef0
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 3%

---


# Replikation {#replication}

Adobe Experience Manager als Cloud Service verwendet die [Sling Content Distribution](https://sling.apache.org/documentation/bundles/content-distribution.html) -Funktion, um den Inhalt zu verschieben, um ihn in einen Pipelineservice zu replizieren, der auf einer Adobe-I/O ausgeführt wird, die sich außerhalb der AEM Laufzeitumgebung befindet.

>[!NOTE]
>
>Lesen Sie [Distribution](/help/core-concepts/architecture.md#content-distribution) für weitere Informationen.

## Methoden zum Veröffentlichen von Inhalten {#methods-of-publishing-content}

### Schnelle Veröffentlichung rückgängig machen/planen - Veröffentlichung rückgängig machen/veröffentlichen {#publish-unpublish}

Diese Standard-AEM-Funktionen für die Autoren ändern sich nicht mit AEM Cloud Service.

### An- und Ausschalten - Konfiguration auslösen {#on-and-off-times-trigger-configuration}

Die zusätzlichen Möglichkeiten für **An- und** Ausschaltzeit **sind auf der Registerkarte** Grundeinstellungen der Seiteneigenschaften [](/help/sites-cloud/authoring/fundamentals/page-properties.md#basic)verfügbar.

Um die automatische Replizierung dafür zu realisieren, müssen Sie die **automatische Replizierung** in der [OSGi-Konfiguration](/help/implementing/deploying/configuring-osgi.md) **On Off Trigger-Konfiguration** aktivieren:

![OSGi-On-Off-Auslöserkonfiguration](/help/operations/assets/replication-on-off-trigger.png)

### Aktivieren eines Baumes {#tree-activation}

To perform a tree activation:

1. From the AEM Start Menu navigate to **Tools > Deployment > Distribution**
2. Select the card **forwardPublisher**
3. Once in the forwardPublisher Web console UI, **select Distribute**

   ![Distribute](assets/distribute.png "Distribute")
4. Select the path in the path browser, choose to add a node, tree or delete as required and select **Submit**

## Fehlerbehebung {#troubleshooting}

To troubleshoot replication, navigate to the Replication Queues in the AEM Author Service Web UI:

1. From the AEM Start Menu navigate to **Tools > Deployment > Distribution**
2. Select the card **forwardPublisher**
   ![Status](assets/status.png "Status")
3. Check the queue status which should be green
4. You can test the connection to the replication service
5. Select the **Logs** tab which shows the history of content publications

![](assets/logs.png "LogsLogs")

Wenn der Inhalt nicht veröffentlicht werden konnte, wird die gesamte Veröffentlichung vom AEM Publish-Dienst zurückgesetzt.
In diesem Fall sollten die Warteschlangen überprüft werden, um festzustellen, welche Elemente die Löschung der Veröffentlichung verursacht haben. Wenn Sie auf eine Warteschlange mit einem roten Status klicken, wird die Warteschlange mit ausstehenden Elementen angezeigt, von der aus einzelne oder alle Elemente bei Bedarf gelöscht werden können.
