---
title: Indizierung nach der Migration von Inhalten
description: Erfahren Sie, wie der Migrationsprozess den aufgenommenen Inhalt auf der Cloud Service-Zielinstanz indiziert.
exl-id: a13d5df4-b351-410a-9336-1b34a8af21b6
feature: Migration
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 100%

---

# Indizierung nach der Migration von Inhalten {#Indexing-content}

## Indizierung {#aem-indexing-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_indexing"
>title="Inhaltsindizierung"
>abstract="Die Indizierung bei AEM bezieht sich auf die Indizierung des Inhalts auf der Cloud Service-Instanz nach der Migration der Inhalte dorthin. Eine Indizierung ist erforderlich, um die Suche nach Inhalten in dieser Instanz zu unterstützen."

Sobald der Cloud Acceleration Manager die Aufnahme von Inhalten in Ihre Cloud Service-Instanz abgeschlossen hat, kann er verwendet werden. Zunächst wird der Inhalt nicht indiziert, was wahrscheinlich zu einer instabilen Umgebung führt, in der Probleme wie nicht durchsuchbare Inhalte und eine beeinträchtigte Leistung erwartet werden können. Um eine optimale Leistung auf der Instanz zu erzielen, startet der Migrationsprozess automatisch mit der Indizierung des Inhalts. Es gibt dabei nichts zu tun, außer den Indizierungsfortschritt zu überwachen.

> Informationen zum Starten einer Aufnahme finden Sie unter [Aufnehmen von Inhalten in Cloud Service](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md).

Die folgenden Schritte zeigen den allgemeinen Fluss, den Sie während der Indizierung auf der Benutzeroberfläche erwarten können. Einige Beschriftungen bieten hilfreichen Kontext in Tool-Tipps. Bewegen Sie den Mauszeiger daher über Elemente, um mehr über den aktuellen Indizierungsstatus zu erfahren.

Um zu beginnen, gehen Sie zu Cloud Acceleration Manager. Klicken Sie auf Ihre Projektkarte und dann auf die Karte „Content Transfer“. Navigieren Sie zu **Aufnahmevorgänge** und sehen Sie sich die aufgelisteten Vorgänge an.

>[!NOTE]
>Sie können die Indizierungsprotokolle mithilfe der Aktionen des Aufnahmevorgangs über die Dropdown-Liste „…“ anzeigen oder herunterladen. Die Protokolle sind verfügbar im
> Aktionsabschnitt „Indizierungsprotokoll“, nachdem der Indizierungsvorgang abgeschlossen ist.

### Ausstehend

So wird die Zeile des Aufnahmevorgangs angezeigt, wenn die Aufnahme ausgeführt wird, bevor der Indizierungsvorgang gestartet wurde. Die Benutzenden brauchen keine Aktionen durchzuführen. Wenn die Aufnahme aus irgendeinem Grund fehlschlägt, wird die Warteschlange des Indizierungsvorgangs zurückgesetzt und nicht gestartet.

![Bild](/help/journey-migration/content-transfer-tool/assets-indexing/pending.png)

### Wird ausgeführt

Wenn die Aufnahme erfolgreich ist, wird der Indizierungsvorgang automatisch initiiert. In der Zeile mit dem Aufnahmevorgang wird ein Fortschrittssymbol für den AEM-Indizierungsstatus angezeigt. Sie können das Dialogfeld „Dauer“ öffnen, um den Fortschritt des Vorgangs anzuzeigen.

![Bild](/help/journey-migration/content-transfer-tool/assets-indexing/running.png)

### Abgeschlossen

Wenn der Indizierungsvorgang erfolgreich ausgeführt wird, kann die Instanz bei optimaler Leistung verwendet werden. An dieser Stelle stehen die Indizierungsvorgangsprotokolle zum Anzeigen oder Herunterladen zur Überprüfung zur Verfügung.

![Bild](/help/journey-migration/content-transfer-tool/assets-indexing/complete.png)

### Fehler

Die Indizierung der Cloud Service-Zielinstanz wird höchstwahrscheinlich erfolgreich sein. Sie kann in einigen Fällen fehlschlagen und die Zeile mit dem Aufnahmevorgang wird wie folgt angezeigt. Sie können in jedem Fall einige Details des Fehlers herausfinden, indem Sie den Mauszeiger über den Fehlerstatus bewegen. Außerdem werden dort möglicherweise weitere Informationen bereitgestellt, die Ihnen bei der Ermittlung der nächsten Schritte helfen. An dieser Stelle stehen die Indizierungsvorgangsprotokolle zur Ansicht oder zum Herunterladen zur Verfügung, um die Fehlerquelle zu ermitteln. Wenn der nächste Schritt nicht klar ist, wenden Sie sich an den Adobe-Support mit Details zur Aufnahme und zum Indizierungsprotokoll.

>[!TIP]
>
> Wenn der Indizierungsauftrag zu lange zu dauern scheint, stellen Sie sicher, dass keine [IP-Zulassungsliste](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) über Cloud Manager angewendet wurde, da diese den Cloud Acceleration Manager daran hindert, den Migrationsdienst zu erreichen.

![image](/help/journey-migration/content-transfer-tool/assets-indexing/failed.png)

## Wie geht es weiter {#whats-next}

Sobald die Cloud Service-Zielinstanz indiziert wurde, können Sie die Protokolle der Indizierungsvorgänge anzeigen und nach Details und Fehlern suchen.

Die Migration ist abgeschlossen. Das Testen und Validieren der Cloud Service-Zielinstanz kann beginnen.
