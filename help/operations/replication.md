---
title: Replikation
description: Distribution und Fehlerbehebung bei der Replikation.
translation-type: tm+mt
source-git-commit: 23349f3350631f61f80b54b69104e5a19841272f
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 4%

---


# Replikation {#replication}

Adobe Experience Manager als Cloud Service verwendet die [Sling Content Distribution](https://sling.apache.org/documentation/bundles/content-distribution.html) -Funktion, um den Inhalt in einen Pipelineservice zu verschieben, der auf Adobe I/O ausgeführt wird und sich außerhalb der AEM-Laufzeit befindet.

>[!NOTE]
>
>Lesen Sie [Distribution](/help/core-concepts/architecture.md#content-distribution) für weitere Informationen.

## Methoden zum Veröffentlichen von Inhalten {#methods-of-publishing-content}

### Schnelle Veröffentlichung rückgängig machen/planen - Veröffentlichung rückgängig machen/veröffentlichen {#publish-unpublish}

Diese AEM-Standardfunktionen für Autoren ändern sich nicht mit AEM Cloud Service.

### Aktivieren eines Baumes {#tree-activation}

So führen Sie eine Baumstruktur-Aktivierung durch:

1. Navigieren Sie im Menü AEM Beginn zu **Tools > Bereitstellung > Verteilung**
2. Wählen Sie die Karte **forwardPublisher aus**
3. Wählen Sie in der Benutzeroberfläche der Web-Konsole &quot;forwardPublisher&quot;die **Option &quot;Verteilen&quot;.**

   ![](assets/distribute.png "DistributeDistribute")
4. Wählen Sie den Pfad im Pfadbrowser aus, fügen Sie einen Knoten, eine Struktur oder löschen Sie ihn nach Bedarf und wählen Sie **Senden**

## Fehlerbehebung {#troubleshooting}

Zur Fehlerbehebung bei der Replikation navigieren Sie zu den Replikationswarteschlangen in der Web-Benutzeroberfläche des AEM Author-Dienstes:

1. Navigieren Sie im Menü AEM Beginn zu **Tools > Bereitstellung > Verteilung**
2. Wählen Sie die Karte **forwardPublisher aus**
   ![](assets/status.png "StatusStatus")
3. Überprüfen des Warteschlangenstatus, der grün sein sollte
4. Sie können die Verbindung zum Replizierungsdienst testen
5. Wählen Sie die Registerkarte &quot; **Protokolle** &quot;aus, auf der der Verlauf der Veröffentlichungen angezeigt wird

![](assets/logs.png "LogsLogs")

Wenn die Inhalte nicht veröffentlicht werden konnten, wird die gesamte Veröffentlichung vom AEM Publish-Dienst zurückgesetzt.
In diesem Fall sollten die Warteschlangen überprüft werden, um festzustellen, welche Elemente die Löschung der Veröffentlichung verursacht haben. Wenn Sie auf eine Warteschlange mit einem roten Status klicken, wird die Warteschlange mit ausstehenden Elementen angezeigt, von der aus einzelne oder alle Elemente bei Bedarf gelöscht werden können.
