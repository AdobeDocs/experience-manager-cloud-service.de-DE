---
title: Nach der Live-Schaltung
description: Erfahren Sie, wie Sie Probleme erkennen und die Leistung verbessern können.
exl-id: 487f0b51-501b-48fc-a796-3cb8a6d64462
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 100%

---

# Nach der Live-Schaltung {#post-go-live}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_troubleshooting"
>title="Beheben von Fehlern in AEM"
>abstract="Lesen Sie die Best Practices für die kontinuierliche Entwicklung und verwalten Sie Protokolle zusammen mit Tools wie der Entwicklerkonsole und CRXDE Lite, um Probleme mit AEM zu beheben."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-logs.html?lang=de" text="Zugreifen auf und Verwalten von Protokollen"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=de#aem-as-a-cloud-service-development-tools" text="Entwicklungs-Tools für AEM as a Cloud Service"

Dies ist der letzte Teil der Tour. Sie lernen, wie Sie Probleme erkennen und die Leistung verbessern, nachdem die Migration abgeschlossen ist. In der Phase nach der Migration sollten Sie die Bereinigung temporärer Dateien sicherstellen, die Best Practices für die kontinuierliche Entwicklung überprüfen und die Protokolle verwalten.

## Die bisherige Entwicklung {#story-so-far}

Im vorherigen Schritt der Tour haben Sie gelernt, wie die Migration und die [Live-Schaltung](/help/journey-migration/go-live.md) durchgeführt werden, sobald der Code und die Inhalte bereit waren, zu AEM as a Cloud Service verschoben zu werden.

## Ziel {#objective}

In diesem Dokument werden die Tools beschrieben, die zur Fehlerbehebung in AEM as a Cloud Service-Umgebungen verfügbar sind:

* **Entwicklerkonsole**
* **CRXDE Lite**
* **Verwalten von Protokollen**

## Entwicklerkonsole {#developer-console}

Die Fehlerbehebung für Entwicklerumgebungen von AEM as a Cloud Service ist in der Entwicklerkonsole für Entwicklungs-, Staging- und Produktionsumgebung verfügbar.

Weitere Informationen zu Entwicklungs-Tools finden Sie unter [Implementierung für AEM as a Cloud Service](/help/implementing/developing/introduction/development-guidelines.md#aem-as-a-cloud-service-development-tools).

## CRXDE Lite {#crxde-lite}

Als Benutzer können Sie in der Entwicklungsumgebung auf CRXDE Lite zugreifen, jedoch nicht in der Staging- oder Produktionsumgebung.

>[!IMPORTANT]
>Das Schreiben in unveränderliche Repositorys wie zum Beispiel `/libs` und `/apps` führt zur Laufzeit zu Fehlern. Weiterhin haben Kunden keinen Zugriff auf Entwickler-Tools für Staging- und Produktionsumgebung.

Weitere Informationen zum Entwickeln Ihres AEM-Programms mit CRXDE Lite finden Sie unter [Entwickeln mit CRXDE Lite](/help/implementing/developing/tools/crxde.md).

## Verwalten von Protokollen {#managing-logs}

Benutzer können auf eine Liste der verfügbaren Protokolldateien für die ausgewählte Umgebung zugreifen.

Unter [Zugreifen auf und Verwalten von Protokollen](/help/implementing/cloud-manager/manage-logs.md) erfahren Sie, wie Sie über die Benutzeroberfläche oder über die API über Cloud Manager auf Protokolle zugreifen und diese verwalten.

## Kontaktieren des Supports {#contacting-support}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_support"
>title="Hilfe und Support"
>abstract="Wenden Sie sich an unser AEM-Supportteam, um nähere Informationen zu erhalten oder um Bedenken auszuräumen."
>additional-url="https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html" text="Experience Cloud-Support"

Wenn Sie Fragen zum Zugriff auf Cloud Service haben, wenden Sie sich an Ihren Adobe Kundenbetreuer oder den [Support für Experience Cloud](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html), um weitere Informationen zu erhalten.

## Dokumentieren von Erkenntnissen {#document-learnings}

Sobald die Migration abgeschlossen ist, sollten Sie die während dieses Prozesses gewonnenen Erkenntnisse dokumentieren. Einige Fragen, die möglicherweise den Dokumentationsprozess unterstützen könnten, sind:

* Was hat gut funktioniert und was nicht?
* Was waren die größten Herausforderungen?
* Empfehlungen im Falle einer zukünftigen Migration.

Sie sollten diese Erkenntnisse nach der Migration dann mit Projektbeteiligten und Teams innerhalb Ihrer Organisation teilen.

## Die Tour ist (fast) zu Ende {#journey-ends}

Herzlichen Glückwunsch! Sie haben die Tour zur Migration zu AEM as a Cloud Service abgeschlossen! Sie sollten jetzt mit folgenden Themen vertraut sein:

* Erste Schritte mit der Migration zu AEM as a Cloud Service
* Bestimmen, ob Ihre Bereitstellung bereit für die Migration zu AEM as a Cloud Service ist
* Ihren Code und Ihre Inhalte Cloud-fähig machen
* Die Migration durchführen
* Probleme erkennen und die Leistung verbessern
