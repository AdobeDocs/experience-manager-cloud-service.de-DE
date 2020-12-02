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

Adobe Experience Manager als Cloud Service verwendet die Funktion [Sling Content Distribution](https://sling.apache.org/documentation/bundles/content-distribution.html), um den Inhalt zu verschieben, um ihn in einen Pipelineservice zu replizieren, der auf Adobe I/O ausgeführt wird, der sich außerhalb der AEM Laufzeit befindet.

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Distribution](/help/core-concepts/architecture.md#content-distribution).

## Methoden zum Veröffentlichen von Inhalten {#methods-of-publishing-content}

### Schnelles Aufheben/Veröffentlichen - Geplante Aufhebung/Veröffentlichung {#publish-unpublish}

Diese Standard-AEM-Funktionen für die Autoren ändern sich nicht mit AEM Cloud Service.

### An- und Ausschalten - Auslöserkonfiguration {#on-and-off-times-trigger-configuration}

Die zusätzlichen Möglichkeiten von **On Time** und **Off Time** sind auf der Registerkarte [Einfach unter Seiteneigenschaften](/help/sites-cloud/authoring/fundamentals/page-properties.md#basic) verfügbar.

Um die automatische Replizierung zu diesem Zweck zu realisieren, müssen Sie die Option **Automatische Replizierung** in der [OSGi-Konfiguration](/help/implementing/deploying/configuring-osgi.md) **An-Aus-Auslöserkonfiguration** aktivieren:

![OSGi-On-Off-Auslöserkonfiguration](/help/operations/assets/replication-on-off-trigger.png)

### Aktivieren eines Baumes {#tree-activation}

So führen Sie eine Baumstruktur-Aktivierung durch:

1. Navigieren Sie im Menü AEM Beginn zu **Tools > Bereitstellung > Distribution**
2. Wählen Sie die Karte **forwardPublisher**
3. Wählen Sie in der Benutzeroberfläche der Web-Konsole &quot;forwardPublisher&quot;die Option **Distribute**

   ![](assets/distribute.png "DistributeDistribute")
4. Wählen Sie den Pfad im Pfadbrowser aus, fügen Sie einen Knoten, eine Struktur oder löschen Sie ihn nach Bedarf und wählen Sie **Senden**

## Fehlerbehebung {#troubleshooting}

Zur Fehlerbehebung bei der Replikation navigieren Sie zu den Replikationswarteschlangen in der Web-Benutzeroberfläche des AEM Author-Dienstes:

1. Navigieren Sie im Menü AEM Beginn zu **Tools > Bereitstellung > Distribution**
2. Wählen Sie die Karte **forwardPublisher**
   ![](assets/status.png "StatusStatus")
3. Überprüfen des Warteschlangenstatus, der grün sein sollte
4. Sie können die Verbindung zum Replizierungsdienst testen
5. Wählen Sie die Registerkarte **Protokolle**, auf der der Verlauf der Veröffentlichungen angezeigt wird.

![](assets/logs.png "LogsLogs")

Wenn der Inhalt nicht veröffentlicht werden konnte, wird die gesamte Veröffentlichung vom AEM Publish-Dienst zurückgesetzt.
In diesem Fall sollten die Warteschlangen überprüft werden, um festzustellen, welche Elemente die Löschung der Veröffentlichung verursacht haben. Wenn Sie auf eine Warteschlange mit einem roten Status klicken, wird die Warteschlange mit ausstehenden Elementen angezeigt, von der aus einzelne oder alle Elemente bei Bedarf gelöscht werden können.
