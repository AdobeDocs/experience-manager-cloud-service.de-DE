---
title: Nach der Live-Schaltung
description: Erfahren Sie, wie Sie Probleme erkennen und die Leistung verbessern können.
exl-id: 487f0b51-501b-48fc-a796-3cb8a6d64462
feature: Migration
role: Admin
source-git-commit: f3cd1bc761c513ebb85351185e7aa0b6f6eb6f33
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 100%

---

# Nach der Live-Schaltung {#post-go-live}

<!-- Alexandru: contextual help links are broken, temporarily comminting this out until they,re fixed.

>[!CONTEXTUALHELP]
>id="aemcloud_golive_troubleshooting"
>title="Troubleshooting AEM"
>abstract="Review best practices for continuous development and management of logs. Learn about tools like Developer Console and CRXDE Lite to help with troubleshooting issues with AEM."
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-logs" text="Accessing and Managing Logs"
>additional-url="https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines#aem-as-a-cloud-service-development-tools" text="AEM as a Cloud Service Development tools"

-->

Diese Tour ist der letzte Teil. Sie lernen, wie Sie Probleme erkennen und die Leistung verbessern, nachdem die Migration abgeschlossen ist. Stellen Sie die Bereinigung temporärer Dateien sicher, lesen Sie die Best Practices für die kontinuierliche Entwicklung und verwalten Sie Protokolle.

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

Als Benutzerin oder Benutzer können Sie in der Entwicklungsumgebung auf CRXDE Lite zugreifen, jedoch nicht in der Staging- oder Produktionsumgebung.

>[!IMPORTANT]
>Das Schreiben in unveränderliche Repositorys wie zum Beispiel `/libs` und `/apps` führt zur Laufzeit zu Fehlern. Außerdem haben Kundinnen und Kunden keinen Zugriff auf Entwickler-Tools für Staging- und Produktionsumgebung.

Weitere Informationen zum Entwickeln Ihrer AEM-Anwendung mit CRXDE Lite finden Sie unter [Entwickeln mit CRXDE Lite](/help/implementing/developing/tools/crxde.md).

## Verwalten von Protokollen {#managing-logs}

Benutzerinnen und Benutzer können auf eine Liste der verfügbaren Protokolldateien für die ausgewählte Umgebung zugreifen.

Unter [Zugriff und Verwaltung von Protokollen](/help/implementing/cloud-manager/manage-logs.md) erfahren Sie, wie Sie über die Benutzeroberfläche oder über die API via Cloud Manager auf Protokolle zugreifen und diese verwalten können.

## Kontaktieren des Supports {#contacting-support}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_support"
>title="Hilfe und Support"
>abstract="Wenden Sie sich an Adobe AEM-Support, um Klärungen zu erhalten oder Probleme anzusprechen."
>additional-url="https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html" text="Experience Cloud-Support"

Wenn Sie Fragen zum Zugriff auf Cloud Service haben, wenden Sie sich an Ihren Adobe Kundenbetreuer oder den [Support für Experience Cloud](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html), um weitere Informationen zu erhalten.

## Dokumentieren von Erkenntnissen {#document-learnings}

Dokumentieren Sie die während dieses Prozesses gewonnenen Erkenntnisse, sobald die Migration abgeschlossen ist. Einige Fragen, die möglicherweise den Dokumentationsprozess unterstützen könnten, sind:

* Was hat gut funktioniert und was nicht?
* Was waren die größten Herausforderungen?
* Empfehlungen im Falle einer zukünftigen Migration.

Teilen Sie diese Erkenntnisse nach der Migration dann mit Projektbeteiligten und Teams innerhalb Ihres Unternehmens.

## Die Tour ist (fast) zu Ende {#journey-ends}

Herzlichen Glückwunsch! Sie haben die Tour zur Migration zu AEM as a Cloud Service abgeschlossen! Sie sollten jetzt mit folgenden Themen vertraut sein:

* Erste Schritte mit der Migration zu AEM as a Cloud Service
* Bestimmen, ob Ihre Bereitstellung bereit für die Migration zu AEM as a Cloud Service ist
* Ihren Code und Ihre Inhalte Cloud-fähig machen
* Die Migration durchführen
* Probleme erkennen und die Leistung verbessern
