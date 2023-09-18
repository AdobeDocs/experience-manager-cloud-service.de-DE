---
title: Versionshinweise für Cloud Manager 2023.9.0 in Adobe Experience Manager as a Cloud Service
description: Dies sind die Versionshinweise für Cloud Manager 2023.9.0 in AEM as a Cloud Service.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: 8bf2ffe8b1d3780f4ad3f6972fea4f8281945abb
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 19%

---


# Versionshinweise für Cloud Manager 2023.9.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise zu Cloud Manager 2023.9.0 in AEM as a Cloud Service.

>[!NOTE]
>
>Siehe [diese Seite](/help/release-notes/release-notes-cloud/release-notes-current.md) für die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service.

## Veröffentlichungsdatum {#release-date}

Die Version 2023.9.0 von Cloud Manager in AEM as a Cloud Service wurde am 14. September 2023 veröffentlicht. Die Veröffentlichung der nächsten Version ist für den 5. Oktober 2023 geplant.

## Neue Funktionen {#what-is-new}

* CDN-Protokolle können, sofern verfügbar, über die Cloud Manager-Benutzeroberfläche heruntergeladen werden.
* Benutzer können sich jetzt dafür entscheiden, Experience Audit-Tests mit Google LightHouse in produktionsfremden, vollständigen Stapel-Pipelines einzubeziehen.

## Frühzeitige Annahme des Programms {#early-adoption}

Nehmen Sie an unserem Programm teil und haben Sie die Möglichkeit, einige bevorstehende Funktionen zu testen.

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

## Fehlerbehebungen {#bug-fixes}

* Wenn ein Programm gelöscht wird, werden auch alle verknüpften, laufenden Pipelines gelöscht, um sicherzustellen, dass die Pipeline nicht fälschlicherweise als fehlgeschlagen gekennzeichnet ist.
* Die Schaltfläche Aufschalten zum Vervollständigen ist deaktiviert und informiert den Benutzer darüber, warum eine Pipeline ausgeführt wird.
* Wenn alle Schritte einer Pipeline-Ausführung &quot;abgeschlossen&quot;sind, wird der Status der Pipeline gelegentlich als &quot;ausgeführt&quot;betrachtet, sodass sie sich in einem blockierten Zustand zu befinden scheint. Es wird nun als &quot;vollständig&quot;bezeichnet.
