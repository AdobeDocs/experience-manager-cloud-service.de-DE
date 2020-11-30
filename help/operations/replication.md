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

Adobe Experience Manager als Cloud Service verwendet die [Sling Content Distribution](https://sling.apache.org/documentation/bundles/content-distribution.html) -Funktion, um die Inhalte zu verschieben, um sie in einen Pipeline-Dienst zu replizieren, der auf Adobe I/O ausgeführt wird, das sich außerhalb der AEM Laufzeit befindet.

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

Wenn der Inhalt nicht veröffentlicht werden konnte, wird die gesamte Veröffentlichung vom AEM Publish-Dienst zurückgesetzt.
In diesem Fall sollten die Warteschlangen überprüft werden, um festzustellen, welche Elemente die Löschung der Veröffentlichung verursacht haben. Wenn Sie auf eine Warteschlange mit einem roten Status klicken, wird die Warteschlange mit ausstehenden Elementen angezeigt, von der aus einzelne oder alle Elemente bei Bedarf gelöscht werden können.
