---
title: Nach der Live-Schaltung
description: Erfahren Sie, wie Sie Probleme erkennen und die Leistung verbessern können.
exl-id: 487f0b51-501b-48fc-a796-3cb8a6d64462
source-git-commit: 1b9d49ce1ef8ad4b0a11400b41d8c9b880cbf884
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 76%

---

# Nach der Live-Schaltung {#post-go-live}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_troubleshooting"
>title="Beheben von Fehlern in AEM"
>abstract="Lesen Sie die Best Practices für die kontinuierliche Entwicklung und verwalten Sie Protokolle zusammen mit Tools wie der Entwicklerkonsole und CRXDE Lite, um Probleme mit AEM zu beheben."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-logs.html?lang=de" text="Zugreifen auf und Verwalten von Protokollen"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines.html?lang=de#aem-as-a-cloud-service-development-tools" text="Entwicklungs-Tools für AEM as a Cloud Service"

Diese Journey ist der letzte Teil, daher lernen Sie, wie Sie nach Abschluss der Migration auf Probleme überwachen und die Leistung verbessern können. In der Phase nach der Migration sollten Sie die Bereinigung temporärer Dateien sicherstellen, die Best Practices für die kontinuierliche Entwicklung überprüfen und die Protokolle verwalten.

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
>Das Schreiben in unveränderliche Repositorys wie zum Beispiel `/libs` und `/apps` führt zur Laufzeit zu Fehlern. Außerdem haben Sie keinen Zugriff auf Entwickler-Tools für Staging- und Produktionsumgebungen.

Siehe [Entwickeln mit CRXDE Lite](/help/implementing/developing/tools/crxde.md) für weitere Informationen zur Entwicklung Ihrer AEM-Anwendung mit CRXDE Lite.

## Verwalten von Protokollen {#managing-logs}

Benutzerinnen und Benutzer können auf eine Liste der verfügbaren Protokolldateien für die ausgewählte Umgebung zugreifen.

Siehe [Zugreifen auf und Verwalten von Protokollen](/help/implementing/cloud-manager/manage-logs.md) , um zu erfahren, wie Sie über die Benutzeroberfläche oder die API über Cloud Manager auf Protokolle zugreifen und diese verwalten können.

## Kontaktieren des Supports {#contacting-support}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_support"
>title="Hilfe und Support"
>abstract="Wenden Sie sich an Adobe AEM-Support, um Klärungen zu erhalten oder Probleme anzusprechen."
>additional-url="https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html" text="Experience Cloud-Support"

Wenn Sie Fragen zum Zugriff auf Cloud Service haben, wenden Sie sich an Ihren Adobe Kundenbetreuer oder den [Support für Experience Cloud](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html), um weitere Informationen zu erhalten.

## Dokumentieren von Erkenntnissen {#document-learnings}

Nachdem die Migration abgeschlossen ist, dokumentieren Sie die während dieses Prozesses gewonnenen Erkenntnisse. Einige Fragen, die möglicherweise den Dokumentationsprozess unterstützen könnten, sind:

* Was hat gut funktioniert und was nicht?
* Was waren die größten Herausforderungen?
* Recommendations , wenn eine zukünftige Migration vorliegt.

Geben Sie diese Nachmigrationserfahrungen für Interessengruppen und Teams in Ihrer Organisation frei.

## Die Tour ist (fast) zu Ende {#journey-ends}

Herzlichen Glückwunsch! Sie haben die Tour zur Migration zu AEM as a Cloud Service abgeschlossen! Sie sollten jetzt mit folgenden Themen vertraut sein:

* Erste Schritte mit der Migration zu AEM as a Cloud Service
* Bestimmen, ob Ihre Bereitstellung bereit für die Migration zu AEM as a Cloud Service ist
* Ihren Code und Ihre Inhalte Cloud-fähig machen
* Die Migration durchführen
* Probleme erkennen und die Leistung verbessern
