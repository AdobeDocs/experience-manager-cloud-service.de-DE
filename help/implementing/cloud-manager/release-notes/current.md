---
title: Versionshinweise für Cloud Manager 2023.7.0 in Adobe Experience Manager as a Cloud Service
description: Dies sind die Versionshinweise für Cloud Manager 2023.7.0 in AEM as a Cloud Service.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: 2721cb20083eeda7546513817f1ddfe12e9cb43a
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 32%

---


# Versionshinweise für Cloud Manager 2023.7.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise zu Cloud Manager 2023.7.0 in AEM as a Cloud Service.

>[!NOTE]
>
>Siehe [diese Seite](/help/release-notes/release-notes-cloud/release-notes-current.md) für die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service.

## Veröffentlichungsdatum {#release-date}

Die Cloud Manager -Version 2023.7.0 in AEM as a Cloud Service Version wurde am 29. Juni 2023 veröffentlicht. Die nächste Version ist für den 10. August 2023 geplant.

## Neue Funktionen {#what-is-new}

* Auf den Karten der Landingpage von Cloud Manager wird jetzt angegeben, ob [erweiterte Sicherheit](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) für die Programme aktiviert ist.
* Wenn eine Entwicklung [Pipeline](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) keine Testschritte enthält, können Benutzer jetzt Testschritte einbeziehen, wenn sie [Starten Sie die Pipeline.](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#running-pipelines)
   * Diese wird schrittweise eingeführt.
* Wann [die Ausführung abbrechen,](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#view-details) Im Schritt zur Pipelineausführungsgenehmigung wird der Benutzer jetzt aufgefordert, einen Grund für den Abbruch anzugeben.
   * Diese wird schrittweise eingeführt.
* Benutzer können jetzt auf [Protokolle aus dem Prozess zum Kopieren des Inhalts.](/help/implementing/developing/tools/content-copy.md#accessing-logs)
   * Diese Option ist nur verfügbar, wenn sowohl die Quell- als auch die Zielumgebung AEM Version sind `2023.7.12549` oder höher.

## Fehlerbehebungen {#bug-fixes}

* Die Navigation von Cloud Manager zur Authoring-Benutzeroberfläche schlägt nach der Anmeldung nicht mehr fehl, um zur Unified Shell weiterzuleiten.
* Beim Bearbeiten des Live-Datums über das Widget &quot;Go-Live&quot;wird jetzt zum **Live-Schaltung** anstatt der **Verbesserte Sicherheit** Registerkarte.
* Beim Starten eines Kopiervorgangs kann ein Benutzer keine Umgebung mehr auswählen, in der bereits ein Kopiervorgang aufgerufen wurde.
