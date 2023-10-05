---
title: Versionshinweise für Cloud Manager 2023.10.0 in Adobe Experience Manager as a Cloud Service
description: Dies sind die Versionshinweise für Cloud Manager 2023.10.0 in AEM as a Cloud Service.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: 661eac787439e6e696574a6973afa7e39eeb443e
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 15%

---


# Versionshinweise für Cloud Manager 2023.10.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise zu Cloud Manager 2023.10.0 in AEM as a Cloud Service.

>[!NOTE]
>
>Siehe [diese Seite](/help/release-notes/release-notes-cloud/release-notes-current.md) für die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service.

## Veröffentlichungsdatum {#release-date}

Die Version 2023.10.0 von Cloud Manager in AEM as a Cloud Service wurde am 5. Oktober 2023 veröffentlicht. Die nächste Version ist für den 2. November 2023 geplant.

## Neue Funktionen {#what-is-new}

* [Sie können eine Pipeline jetzt sicher abbrechen](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#cancel) in den Schritten zum Validieren und Erstellen von Bildern.
* Verbesserungen bei [Indizierung](/help/operations/indexing.md) die Pipeline-Dauer bei der Bereitstellung neuer Indizes verkürzt haben.
   * Verbesserungen variieren je nach Inhaltsprofil.
* Automatisch [Aktualisierungen für Entwicklungsumgebungen](/help/implementing/cloud-manager/manage-environments.md#updating-environments) sind standardmäßig für neue Programme aktiviert, sodass Sie Zeit haben, Aktualisierungen manuell auszuführen.
   * Diese Aktualisierung wird schrittweise durchgeführt.
* Mit der Cloud Manager-Version vom Oktober 2023 werden die Java- und Maven-Versionen schrittweise aktualisiert.
   * Apache Maven wird auf Version 3.8.8 aktualisiert.
   * Die Java-Versionen werden auf Oracle JDK 8u371 und Oracle JDK 11.0.20 aktualisiert.
   * Standardmäßig wird die Variable `JAVA_HOME` Umgebungsvariable wird aktualisiert auf `/usr/lib/jvm/jdk1.8.0_371` enthält Oracle JDK 8u371.
   * Siehe Dokument . [Build-Umgebung](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md) für weitere Details.
   * [Siehe OpenJDK-Beratung](https://openjdk.org/groups/vulnerability/advisories/) für Details zur Sicherheit und zu Fehlerbehebungen in diesen JDK-Updates.

## Frühzeitige Annahme des Programms {#early-adoption}

Nehmen Sie an unserem Programm teil und haben Sie die Möglichkeit, einige bevorstehende Funktionen zu testen.

### Benutzerdefinierte Berechtigungen {#custom-permissions}

[Benutzerdefinierte Berechtigungen für Cloud Manager](/help/implementing/cloud-manager/custom-permissions.md) können Sie neue benutzerdefinierte Berechtigungsprofile mit konfigurierbaren Berechtigungen erstellen, um den Zugriff auf Programme, Pipelines und Umgebungen für Cloud Manager-Benutzer zu beschränken.

Wenn Sie diese neue Funktion testen und Ihr Feedback teilen möchten, senden Sie bitte eine E-Mail `Grp-CloudManager-custom-permissions@adobe.com` von Ihrer mit Ihrer Adobe ID verknüpften E-Mail-Adresse aus.

### Self-Service Content Restore {#content-restore}

[Neue Funktion zur Wiederherstellung von Self-Service-Inhalten](/help/operations/restore.md) bietet jetzt eine Backup-Wiederherstellung für bis zu sieben Tage und steht frühen Anwendern zu Auswertungszwecken zur Verfügung:

* Point-in-Time-Backup-Wiederherstellung für die letzten 24 Stunden
* Feste Zeitwiederherstellung für bis zu sieben Tage

Wenn Sie diese neue Funktion testen und Ihr Feedback teilen möchten, senden Sie bitte eine E-Mail an `aemcs-restorefrombackup-adopter@adobe.com` aus Ihrer mit Ihrer Adobe ID verknüpften E-Mail. Hinweis:

* Das Programm für den frühen Anwender ist auf Entwicklungsumgebungen beschränkt.
* Die Verfügbarkeit des frühen Adopter-Programms dieser Funktion ist begrenzt.
* Diese Funktion dient zum Wiederherstellen versehentlich gelöschter Inhalte und ist nicht für die Notfallwiederherstellung vorgesehen.

### Experience Audit-Dashboard {#experience-audit-dashboard}

[Das Dashboard &quot;Experience Audit&quot;von Cloud Manager](/help/implementing/cloud-manager/experience-audit-dashboard.md) enthält eine Trendansicht Ihrer Seitenleistungsbewertungen sowie Einblicke und Empfehlungen, die Sie bei der Verbesserung unterstützen. Experience Audit ist ein Schritt in der Produktions-Pipeline von Cloud Manager.

Das Dashboard nutzt Google Lighthouse, ein Open-Source-Tool zur Verbesserung der Qualität Ihrer Web-Apps. Sie können sie für jede Web-Seite ausführen, öffentlich oder authentifizierungspflichtig. Sie enthält Prüfungen zu Leistung, Barrierefreiheit, progressiven Web-Apps, SEO und mehr.

Möchten Sie das neue Dashboard testen? Bitte senden Sie eine E-Mail an `aem-lighthouse-pilot@adobe.com` von Ihrer mit Ihrer Adobe ID verknüpften E-Mail aus und wir können Ihnen den Einstieg erleichtern.
