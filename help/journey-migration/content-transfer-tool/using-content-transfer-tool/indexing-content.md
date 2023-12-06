---
title: Indizierung nach der Migration von Inhalten
description: Erfahren Sie, wie der Migrationsprozess den aufgenommenen Cloud Service in der Zielinhaltsinstanz indiziert.
exl-id: a13d5df4-b351-410a-9336-1b34a8af21b6
source-git-commit: 58195fcb10312c89042f555665d4c8b3642f82ba
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 7%

---

# Indizierung nach der Migration von Inhalten {#Indexing-content}

## Indizierung {#aem-indexing-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_indexing"
>title="Inhaltsindizierung"
>abstract="Die Indizierung bei AEM bezieht sich auf die Indizierung des Inhalts auf der Cloud Service-Instanz nach der Migration der Inhalte dorthin.  Eine Indizierung ist erforderlich, um die Suche nach Inhalten in dieser Instanz zu unterstützen."

Sobald der Cloud Acceleration Manager die Aufnahme von Inhalten in Ihre Cloud Service-Instanz abgeschlossen hat, kann er verwendet werden. Zunächst wird der Inhalt nicht indiziert, was wahrscheinlich zu einer instabilen Umgebung führt, in der Probleme wie nicht durchsuchbare Inhalte und eine beeinträchtigte Leistung erwartet werden können. Um eine optimale Leistung auf der Instanz zu erzielen, startet der Migrationsprozess automatisch mit der Indizierung des Inhalts. Es gibt nichts zu tun, außer den Indizierungsfortschritt zu überwachen.

> Informationen zum Starten einer Aufnahme finden Sie unter [Erfassen von Inhalten in Cloud Service](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md).

Die folgenden Schritte zeigen den allgemeinen Fluss, den Sie während der Indizierung in der Benutzeroberfläche erwarten können. Einige Beschriftungen bieten hilfreichen Kontext in QuickInfos. Bewegen Sie daher den Mauszeiger über Elemente, um mehr über den aktuellen Indizierungsstatus zu erfahren.

Gehen Sie zunächst zu Cloud Acceleration Manager. Klicken Sie auf Ihre Projektkarte und dann auf die Karte Inhaltstransfer . Navigieren Sie zu **Aufnahmevorgänge** und sehen Sie sich die aufgelisteten Aufträge an.

>[!NOTE]
>Sie können die Indizierungsprotokolle mithilfe der Aktionen des Aufnahmeauftrags über die Dropdown-Liste ... anzeigen oder herunterladen. Die Protokolle sind im
> &quot;Indizierungslog&quot;-Aktionsabschnitt, nachdem der Indizierungsauftrag abgeschlossen ist

### Ausstehend

So wird die Zeile des Aufnahmeauftrags angezeigt, wenn die Aufnahme ausgeführt wird, bevor der Indizierungsauftrag gestartet wurde. Der Benutzer muss keine Aktion durchführen. Wenn die Aufnahme aus irgendeinem Grund fehlschlägt, wird die Warteschlange des Indexauftrags zurückgesetzt und nicht gestartet.

![Bild](/help/journey-migration/content-transfer-tool/assets-indexing/pending.png)

### Ausführung läuft

Wenn die Aufnahme erfolgreich ist, wird der Indizierungsauftrag automatisch initiiert. In der Zeile mit dem Aufnahmeauftrag wird ein Fortschrittssymbol für den AEM Indizierungsstatus angezeigt. Sie können das Dialogfeld Dauer öffnen, um den Fortschritt des Auftrags anzuzeigen.

![Bild](/help/journey-migration/content-transfer-tool/assets-indexing/running.png)

### Umfassend

Wenn der Indizierungsauftrag erfolgreich ausgeführt wird, kann die Instanz bei optimaler Leistung verwendet werden. An dieser Stelle stehen die Indizierungsauftragsprotokolle zum Anzeigen oder Herunterladen zur Überprüfung zur Verfügung.

![Bild](/help/journey-migration/content-transfer-tool/assets-indexing/complete.png)

### Fehler

Die Indizierung der Ziel-Cloud Service-Instanz wird höchstwahrscheinlich erfolgreich sein. In einigen Fällen kann sie fehlschlagen und die Zeile mit dem Aufnahmeauftrag wird wie folgt angezeigt. In allen Fällen können Sie einige Details des Fehlschlagens herausfinden, indem Sie mit dem Mauszeiger über den Fehlerstatus fahren. Außerdem können weitere Informationen bereitgestellt werden, die Ihnen bei der Ermittlung der nächsten Schritte helfen. An dieser Stelle stehen die Indizierungsauftragsprotokolle zur Ansicht oder zum Download zur Verfügung, um die Fehlerquelle zu ermitteln. Wenn der nächste Schritt nicht klar ist, wenden Sie sich an den Adobe-Support mit Details zur Aufnahme und zum Indizierungsprotokoll.

>[!TIP]
>
> Wenn der Indizierungsauftrag zu lange zu laufen scheint, stellen Sie sicher, dass ein [IP-Zulassungsliste wurde nicht angewendet](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) Cloud Manager verwenden, da Cloud Acceleration Manager daran gehindert wird, den Migrationsdienst zu erreichen.

![image](/help/journey-migration/content-transfer-tool/assets-indexing/failed.png)

## Wie geht es weiter {#whats-next}

Sobald die Ziel-Cloud-Service-Instanz indiziert wurde, können Sie die Protokolle der Indizierungsaufträge anzeigen und nach Details und Fehlern suchen.

Die Migration ist abgeschlossen. Das Testen und Validieren der Ziel-Cloud-Service-Instanz kann beginnen.
