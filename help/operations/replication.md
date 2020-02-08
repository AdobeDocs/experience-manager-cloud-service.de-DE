---
title: Replikation
description: Distribution und Fehlerbehebung bei der Replikation.
translation-type: tm+mt
source-git-commit: 8fba31951276d7e0de1f3bd079e42e431edaff4e

---


# Replikation {#replication}

Adobe Experience Manager als Cloud-Dienst verwendet die [Sling Content Distribution](https://sling.apache.org/documentation/bundles/content-distribution.html) -Funktion, um den Inhalt in einen Pipelineservice zu verschieben, der auf einer Adobe-E/A-Verbindung ausgeführt wird, die sich außerhalb der AEM-Laufzeit befindet.

>[!NOTE]
>
> Lesen Sie [Distribution](/help/core-concepts/architecture.md#content-distribution) für weitere Informationen.

## Methoden zum Veröffentlichen von Inhalten {#methods-of-publishing-content}

### Schnelle Veröffentlichung rückgängig machen/planen - Veröffentlichung rückgängig machen/veröffentlichen {#publish-unpublish}

Diese AEM-Standardfunktionen für Autoren ändern sich nicht mit dem AEM Cloud-Dienst.

### Aktivieren eines Baumes {#tree-activation}

So führen Sie eine Strukturaktivierung durch:

1. Navigieren Sie im AEM-Startmenü zu **Tools > Bereitstellung > Verteilung**
2. Wählen Sie die Karte **forwardPublisher aus**
3. Wählen Sie in der Benutzeroberfläche der Web-Konsole &quot;forwardPublisher&quot;die **Option Verteilen**
   ![](assets/distribute.png "DistributeDistribute")
4. Wählen Sie den Pfad im Pfadbrowser aus, fügen Sie einen Knoten, eine Struktur oder löschen Sie ihn nach Bedarf und wählen Sie **Senden**

## Fehlerbehebung {#troubleshooting}

Zur Fehlerbehebung bei der Replikation navigieren Sie zu den Replikationswarteschlangen in der Web-Benutzeroberfläche des AEM Author-Dienstes:

1. Navigieren Sie im AEM-Startmenü zu **Tools > Bereitstellung > Verteilung**
2. Wählen Sie die Karte **forwardPublisher aus**
   ![](assets/status.png "StatusStatus")
3. Überprüfen des Warteschlangenstatus, der grün sein sollte
4. Sie können die Verbindung zum Replizierungsdienst testen
5. Wählen Sie die Registerkarte &quot; **Protokolle** &quot;aus, auf der der Verlauf der Veröffentlichungen angezeigt wird

![](assets/logs.png "LogsLogs")

Wenn der Inhalt nicht veröffentlicht werden konnte, wird die gesamte Veröffentlichung vom AEM Publish-Dienst zurückgesetzt.
In diesem Fall sollten die Warteschlangen überprüft werden, um festzustellen, welche Elemente die Löschung der Veröffentlichung verursacht haben. Wenn Sie auf eine Warteschlange mit einem roten Status klicken, wird die Warteschlange mit ausstehenden Elementen angezeigt, von der aus einzelne oder alle Elemente bei Bedarf gelöscht werden können.
