---
title: Versionshinweise für Cloud Manager 2022.6.0 in Adobe Experience Manager as a Cloud Service
description: Dies sind die Versionshinweise für Cloud Manager 2022.6.0 in AEM as a Cloud Service.
feature: Release Information
source-git-commit: 5200ee315ad88dae4b52c0ea904489e73f62a8a0
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 52%

---


# Versionshinweise für Cloud Manager 2022.6.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für Cloud Manager 2022.6.0 in AEM as a Cloud Service.

>[!NOTE]
>
>Auf [dieser Seite](/help/release-notes/release-notes-cloud/release-notes-current.md) finden Sie die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service.

## Veröffentlichungsdatum {#release-date}

Die Cloud Manager -Version 2022.6.0 in AEM as a Cloud Service Version wurde am 9. Juni 2022 veröffentlicht. Die nächste Version ist für den 30. Juni 2022 geplant.

## Neue Funktionen {#what-is-new}

* Die Benutzeroberfläche von Cloud Manager ermöglicht jetzt Folgendes: [Wiederherstellung von Self-Service-Inhalten](/help/operations/backup.md) in einen zweifelsfrei funktionierenden Zustand der AEM Cloud-Umgebung.
   * Diese Funktion wird in den Wochen nach der Version 2022.06.0 schrittweise eingeführt.
* Eine neue Willkommenskarte auf der Landingpage von Cloud Manager bietet Benutzern schnellen Zugriff auf Onboarding-Tutorials und Fortschrittsmetriken zum Mandanten.
   * Diese Funktion wird in der Woche nach der Veröffentlichung von 2022.06.0 schrittweise eingeführt.
* Benutzer mit den erforderlichen Berechtigungen können auf eine neue [Lizenz-Dashboard](/help/implementing/cloud-manager/license-dashboard.md) auf der Landingpage von Cloud Manager , um Details zu den für den Mandanten verfügbaren Berechtigungen anzuzeigen.
   * AEM Sites ist die erste Lösung, für die Verfügbarkeit und Nutzung über das Cloud Manager-Dashboard bereitgestellt werden.
   * Diese Funktion wird in den Wochen nach der Version 2022.06.0 schrittweise eingeführt.
* [Neues relatives Unterkonto und Self-Service-Benutzerverwaltung](/help/implementing/cloud-manager/user-access-new-relic.md) ist jetzt über die Cloud Manager -Benutzeroberfläche verfügbar.
   * Diese Funktion wird in den Wochen nach der Version 2022.06.0 schrittweise eingeführt.
* Ein neues Go Live-Widget auf der Startseite von Cloud Service-Produktionsprogrammen bietet jetzt Anleitungen zur Vorbereitung auf ein erfolgreiches Live-Erlebnis.
* [Build-Artefakte können jetzt bei Verwendung der Git-Spiegelung wiederverwendet werden](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#build-artifact-reuse).

## API-Änderungen {#api-changes}

* Die [`List Programs`](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/getPrograms)-API wird nicht mehr unterstützt und stattdessen sollte [`List Programs for Tenant`](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/getProgramsForTenant) verwendet werden.
   * `List Programs` funktioniert weiterhin, aber die Verwendung führt zu Warnmeldungen in den Protokollen.
   * Es wird nach Ablauf von drei Monaten nicht mehr unterstützt.

