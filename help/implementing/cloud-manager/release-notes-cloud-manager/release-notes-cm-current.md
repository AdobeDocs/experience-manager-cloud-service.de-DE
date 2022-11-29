---
title: Versionshinweise für Cloud Manager 2022.12.0 in Adobe Experience Manager as a Cloud Service
description: Dies sind die Versionshinweise für Cloud Manager 2022.12.0 in AEM as a Cloud Service.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: aa7f2175e2a43a318a6171e622d292ed3a8e958b
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 38%

---


# Versionshinweise für Cloud Manager 2022.12.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Cloud Manager 2022.12.0 in AEM as a Cloud Service.

>[!NOTE]
>
>Auf [dieser Seite](/help/release-notes/release-notes-cloud/release-notes-current.md) finden Sie die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service.

## Veröffentlichungsdatum {#release-date}

Die Cloud Manager -Version 2022.12.0 AEM as a Cloud Service wurde am 29. November 2022 veröffentlicht. Die nächste Version ist für den 19. Januar 2023 geplant.

## Neue Funktionen {#what-is-new}

* Benachrichtigungen für [AEM Wartungsaktualisierungen](/help/overview/what-is-new-and-different.md#aem-updates) wird in der Benutzeroberfläche von Cloud Manager angezeigt. Diese Änderung wird in den Wochen nach der Version 2022.12.0 schrittweise eingeführt.
* Wenn eine Aufnahme über die [Content Transfer Tool (CTT)](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/overview-content-transfer-tool.md) läuft, wird der Umgebungsstatus sowohl in der Entwicklerkonsole als auch in Cloud Manager angezeigt als `Ingestion in Progress`.
* Verbesserung der Verfügbarkeit und Zuverlässigkeit von [Cloud Manager-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) wurden hergestellt.

## Fehlerbehebungen {#bug-fixes}

* Es wurde eine Änderung vorgenommen, um [Front-End-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) nicht ausgeführt werden, während eine Pipeline-Ausführung in derselben Umgebung ausgeführt wird.
* Es wurde eine Änderung vorgenommen, um eine `PATCH /program//environment//variables` -Anfrage für -Umgebungen mit der `FAILED` Status.
