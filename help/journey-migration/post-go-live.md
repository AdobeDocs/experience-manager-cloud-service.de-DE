---
title: Nach der Live-Schaltung
description: Erfahren Sie, wie Sie Probleme überwachen und die Leistung verbessern können.
source-git-commit: c9143d77e70476beb7f7dd162c36aeda8d1be506
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 44%

---


# Nach der Live-Schaltung {#post-go-live}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_troubleshooting"
>title="Beheben von Fehlern in AEM"
>abstract="Lesen Sie die Best Practices für die kontinuierliche Entwicklung und verwalten Sie Protokolle zusammen mit Tools wie der Entwicklerkonsole und CRXDE Lite, um Probleme mit AEM zu beheben."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-logs.html?lang=de" text="Zugreifen auf und Verwalten von Protokollen"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=de#aem-as-a-cloud-service-development-tools" text="Entwicklungs-Tools für AEM as a Cloud Service"

Dies ist der letzte Teil der Journey, sodass Sie lernen, wie Sie nach Abschluss der Migration auf Probleme überwachen und die Leistung verbessern können. Sie sollten die Bereinigung temporärer Dateien sicherstellen, Best Practices für die kontinuierliche Entwicklung überprüfen und Protokolle verwalten.

## Die bisherige Entwicklung {#story-so-far}

Im vorherigen Schritt des Journey haben Sie gelernt, wie die Migration durchgeführt wird und [Live-Schaltung](/help/journey-migration/go-live.md) sobald der Code und der Inhalt bereit waren, auf AEM as a Cloud Service verschoben zu werden.

## Ziel {#objective}

In diesem Dokument werden die Tools beschrieben, die zur Fehlerbehebung in AEM as a Cloud Service Umgebungen verfügbar sind:

* **Entwicklerkonsole**
* **CRXDE Lite**
* **Verwalten von Protokollen**

## Entwicklerkonsole {#developer-console}

Das Debuggen AEM as a Cloud Service Entwicklungsumgebungen ist in der Entwicklerkonsole für Entwicklungs-, Staging- und Produktionsumgebungen verfügbar.

Weitere Informationen zu Entwicklungs-Tools finden Sie unter [Implementieren für AEM as a Cloud Service](/help/implementing/developing/introduction/development-guidelines.md#aem-as-a-cloud-service-development-tools).

## CRXDE Lite {#crxde-lite}

Als ein Benutzer können Sie in der Entwicklungsumgebung auf CRXDE Lite zugreifen, jedoch nicht in der Staging- oder Produktionsumgebung.

>[!IMPORTANT]
>Schreiben in unveränderliche Repositorys wie `/libs` und `/apps` zur Laufzeit führt zu Fehlern. Darüber hinaus haben Sie keinen Zugriff auf Entwickler-Tools für Staging- und Produktionsumgebungen.

Informationen zum Entwickeln Ihrer AEM-Anwendung mit CRXDE Lite finden Sie unter [Entwickeln mit CRXDE Lite](/help/implementing/developing/tools/crxde.md).

## Verwalten von Protokollen {#managing-logs}

Benutzer können auf eine Liste der verfügbaren Protokolldateien für die ausgewählte Umgebung zugreifen.

Unter [Zugreifen auf und Verwalten von Protokollen](/help/implementing/cloud-manager/manage-logs.md) erfahren Sie, wie Sie über die Benutzeroberfläche oder über die API über Cloud Manager auf Protokolle zugreifen und diese verwalten.

## Support kontaktieren {#contacting-support}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_support"
>title="Hilfe und Support"
>abstract="Wenden Sie sich an unser AEM-Supportteam, um nähere Informationen zu erhalten oder um Bedenken auszuräumen."
>additional-url="https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html" text="Experience Cloud-Support"

Wenn Sie Fragen zum Zugriff auf Cloud Service haben, wenden Sie sich an Ihren Adobe Kundenbetreuer oder den [Support für Experience Cloud](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html), um weitere Informationen zu erhalten.

## Dokumenteinträge {#document-learnings}

Sobald die Migration abgeschlossen ist, sollten Sie die während dieses Prozesses gewonnenen Erkenntnisse dokumentieren. Einige Fragen, die den Dokumentationsprozess unterstützen könnten, sind:

* Was funktionierte gut und was nicht?
* Was waren die größten Schmerzpunkte?
* Recommendations im Falle einer zukünftigen Migration.

Sie sollten diese Nachmigrationslernergebnisse dann mit Stakeholdern und Teams in Ihrer Organisation teilen.

## Die Tour ist (fast) zu Ende {#journey-ends}

Herzlichen Glückwunsch! Sie haben die AEM as a Cloud Service Migration Journey abgeschlossen! Sie sollten Folgendes verstehen:

* Erste Schritte mit dem Umstieg auf AEM as a Cloud Service
* Bestimmen Sie, ob Ihre Bereitstellung bereit für die Verschiebung auf AEM as a Cloud Service ist.
* Bereiten Sie Code und Content Cloud bereit
* Migrieren
* Problemüberwachung und Leistungsverbesserung
