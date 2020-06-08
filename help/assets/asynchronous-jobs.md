---
title: Asynchrone Vorgänge
description: AEM Assets optimiert die Leistung, durch das asynchrone Ausführen ressourcenintensiver Vorgänge.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 26833f59f21efa4de33969b7ae2e782fe5db8a14
workflow-type: tm+mt
source-wordcount: '677'
ht-degree: 100%

---


# Asynchrone Vorgänge {#asynchronous-operations}

Um negative Auswirkungen auf die Leistung einzuschränken, werden bestimmte lang laufende und ressourcenintensive Asset-Vorgänge in Adobe Experience Manager (AEM) Assets asynchron verarbeitet.

Zu diesen Vorgängen gehören u. a.:

* Löschen vieler Assets
* Verschieben vieler Assets oder Assets mit vielen Verweisen
* Exportieren/Importieren von Asset-Metadaten in großen Mengen.
* Abrufen von Assets, die über dem festgelegten Schwellenwert liegen, aus einer Remote-AEM-Bereitstellung.

Die asynchrone Verarbeitung umfasst den Aufbau einer Warteschlange mit mehreren Aufträgen und schließlich deren serielle Ausführung gemäß der Verfügbarkeit von Systemressourcen.

Sie können den Status asynchroner Aufträge auf der Seite **[!UICONTROL Async-Auftragsstatus]** einsehen.

>[!NOTE]
>
>Standardmäßig werden Aufträge in AEM Assets parallel ausgeführt. Wenn N die Anzahl der CPU-Kerne ist, können standardmäßig N/2 Aufträge parallel ausgeführt werden. Um benutzerdefinierte Einstellungen für die Auftragswarteschlange festzulegen, passen Sie die Konfiguration **Async Operation Default Queue** über die Web-Konsole an. Weitere Informationen finden Sie unter [Warteschlangenkonfigurationen](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#queue-configurations).

## Überwachen des Status asynchroner Vorgänge {#monitoring-the-status-of-asynchronous-operations}

Jedes Mal, wenn AEM Assets einen Vorgang asynchron verarbeitet, erhalten Sie eine Benachrichtigung in Ihrem Posteingang <!-- and through email -->.

Um den Status der asynchronen Vorgänge detailliert anzuzeigen, navigieren Sie zur Seite **[!UICONTROL Async-Auftragsstatus]**.

1. Tippen/klicken Sie auf das AEM-Logo und navigieren Sie zu **[!UICONTROL Assets]** > **[!UICONTROL Aufträge]**.
1. Überprüfen Sie die Details für die Vorgänge auf der Seite **[!UICONTROL Async-Auftragsstatus]**.

   ![Auftragsstatus](assets/job_status.png)

   Den Fortschritt einzelner Vorgänge finden Sie in der Spalte **[!UICONTROL Status]**. Abhängig vom Fortschritt wird eine der folgenden Statusmeldungen angezeigt:

   **[!UICONTROL Aktiv]**: Der Vorgang wird verarbeitet

   **[!UICONTROL Erfolg]**: Der Vorgang wurde abgeschlossen

   **[!UICONTROL Fehlschlag]** oder **[!UICONTROL Fehler]**: Der Vorgang konnte nicht bearbeitet werden.

   **[!UICONTROL Geplant]**: Die Verarbeitung des Vorgangs ist für einen späteren Zeitpunkt geplant

1. Um einen aktiven Vorgang abzubrechen, wählen Sie ihn in der Liste aus und tippen/klicken Sie auf das Symbol **[!UICONTROL Stopp]** in der Symbolleiste.

   ![Stoppsymbol](assets/stop_icon.png)

1. Um zusätzliche Details anzuzeigen, beispielsweise eine Beschreibung und Protokolle, wählen Sie den Vorgang aus und tippen/klicken Sie auf das Symbol **[!UICONTROL Öffnen]** in der Symbolleiste.

   ![Öffnen-Symbol](assets/open_icon.png)

   Die Detailseite für den Auftrag wird angezeigt.

   ![Auftragsdetails](assets/job_details.png)

1. Um den Vorgang aus der Liste zu löschen, wählen Sie die Option **[!UICONTROL Löschen]** in der Symbolleiste aus. Um die Details als CSV-Datei herunterzuladen, tippen/klicken Sie auf das Symbol **[!UICONTROL Herunterladen]**.

   >[!NOTE]
   >
   >Sie können einen Auftrag nicht löschen, wenn er aktiv ist oder sich in der Warteschlange befindet.

## Bereinigen abgeschlossener Aufträge     {#purging-completed-jobs}

AEM Assets führt jeden Tag um 1:00 Uhr einen Bereinigungsauftrag aus, um abgeschlossene asynchrone Aufträge zu löschen, die älter als einen Tag sind.

Sie können den Zeitplan für den Bereinigungsauftrag bearbeiten. Außerdem können Sie anpassen, wie lange die Details zu abgeschlossenen Aufträgen gespeichert werden sollen, bevor sie gelöscht werden. Darüber hinaus können Sie die maximale Anzahl abgeschlossener Aufträge konfigurieren, deren Details zu einem beliebigen Zeitpunkt gespeichert werden.

1. Tippen/klicken Sie auf das AEM-Logo und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**.
1. Öffnen Sie den Auftrag **[!UICONTROL Adobe CQ DAM Async Jobs Purge Scheduled]**.
1. Geben Sie den Schwellenwert für die Anzahl der Tage ein, nach denen abgeschlossene Aufträge gelöscht werden sollen. Legen Sie außerdem die maximale Anzahl der Aufträge fest, deren Details im Verlauf gespeichert werden sollen.

   ![Konfiguration zum Planen der Bereinigung asynchroner Aufträge](assets/configmgr_purge_asyncjobs.png)
   *Abbildung: Konfiguration zum Planen der Bereinigung asynchroner Aufträge*

1. Speichern Sie die Änderungen.

## Konfigurieren von Schwellenwerten für die asynchrone Verarbeitung     {#configuring-thresholds-for-asynchronous-processing}

Sie können den Schwellenwert für Assets oder Verweise festlegen, damit AEM Assets einen bestimmten Vorgang asynchron verarbeitet.

### Konfigurieren der Schwellenwerte für asynchrone Löschvorgänge {#configuring-thresholds-for-asynchronous-delete-operations}

Wenn die Anzahl der Assets oder der zu löschenden Ordner den Schwellenwert überschreitet, wird der Löschvorgang asynchron ausgeführt.

1. Tippen/klicken Sie auf das AEM-Logo und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**.
1. Öffnen Sie in der Web-Konsole die Konfiguration **[!UICONTROL Async Delete Operation Job Processing]**.
1. Legen Sie im Feld **[!UICONTROL Schwellenwert für Assets]** den Schwellenwert für die Anzahl von Assets/Ordnern für die asynchrone Verarbeitung von Löschvorgängen an.

   ![Löschen-Schwellenwert](assets/delete_threshold.png)

1. Speichern Sie die Änderungen.

### Konfigurieren der Schwellenwerte für asynchrone Verschiebevorgänge     {#configuring-thresholds-for-asynchronous-move-operations}

Wenn die Anzahl der zu verschiebenden Anlagen/Ordner oder Referenzen den Schwellenwert übersteigt, wird der Verschiebevorgang asynchron ausgeführt.

1. Tippen/klicken Sie auf das AEM-Logo und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**.
1. Öffnen Sie in der Web-Konsole die Konfiguration **[!UICONTROL Async Move Operation Job Processing]**.
1. Legen Sie im Feld **[!UICONTROL Schwellenwert für Assets/Verweise]** den Schwellenwert für Assets/Ordner oder Verweise für die asynchrone Verarbeitung von Verschiebevorgängen fest.

   ![Verschieben-Schwellenwert](assets/move_threshold.png)

1. Speichern Sie die Änderungen.
