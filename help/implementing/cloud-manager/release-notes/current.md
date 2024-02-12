---
title: Versionshinweise für Cloud Manager 2024.1.0 in Adobe Experience Manager as a Cloud Service
description: Dies sind die Versionshinweise für Cloud Manager 2024.1.0 in AEM as a Cloud Service.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: b81c2bd5c339bce97fe5774572bf1532fc8e04df
workflow-type: tm+mt
source-wordcount: '687'
ht-degree: 94%

---


# Versionshinweise für Cloud Manager 2024.1.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise zu Cloud Manager 2024.1.0 in AEM as a Cloud Service.

>[!NOTE]
>
>Auf [dieser Seite](/help/release-notes/release-notes-cloud/release-notes-current.md) finden Sie die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service.

## Veröffentlichungsdatum {#release-date}

Die Version 2024.1.0 von Cloud Manager in AEM as a Cloud Service wurde am 18. Januar 2024 veröffentlicht. Die nächste Version wird voraussichtlich am 16. Februar 2024 veröffentlicht.

## Neue Funktionen {#what-is-new}

* Cloud Manager validiert jetzt nicht nur die Ablaufdaten für das [Hauptzertifikat](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md), sondern auch die der Zwischenzertifikate.
* CDN-[Protokolle](/help/implementing/cloud-manager/manage-logs.md) werden nun in einem komprimierten Format zurückgegeben.

## Early-Adopter-Programm {#early-adoption}

Um einige bevorstehende Funktionen testen zu können, müssen Sie Teil des Early-Adopter-Programms von Adobe sein.

### Client-seitige Sammlung über Real User Monitoring (RUM) {#rum}

Sie können den [Datendienst Real User Monitoring (RUM)](/help/implementing/cloud-manager/content-requests.md#cliendside-collection) nutzen, um die Client-seitige Sammlung für AEM as a Cloud Service zu aktivieren.

Der Datendienst Real User Monitoring (RUM) bietet eine präzisere Darstellung der Benutzerinteraktionen und stellt so eine zuverlässige Messung der Website-Interaktionen sicher. Dies ist eine großartige Gelegenheit, erweiterte Einblicke in Ihre Seitenleistung zu erhalten. Dies ist nützlich für Kundinnen und Kunden, die entweder ein von Adobe verwaltetes CDN oder ein nicht von Adobe verwaltetes CDN verwenden. Für diejenigen, die ein nicht von Adobe verwaltetes CDN verwenden, kann die automatisierte Traffic-Berichterstellung jetzt für sie aktiviert werden, sodass keine Traffic-Berichte mehr für Adobe freigegeben werden müssen.

Wenn Sie diese neue Funktion testen und Ihr Feedback teilen möchten, senden Sie bitte über die mit Ihrer Adobe ID verknüpfte E-Mail-Adresse eine E-Mail an `aemcs-rum-adopter@adobe.com`. Geben Sie in Ihrer E-Mail den Domain-Namen für die Produktions-, Staging- und Entwicklungsumgebungen an. Die Verfügbarkeit des Early-Adopter-Programms für diese Funktion ist begrenzt.

### Bringen Sie Ihren eigenen GitHub mit {#byo-github}

Wenn Sie Ihre Repositorys mit GitHub verwalten, [können Sie jetzt Code direkt in Ihren GitHub-Repositorys über Cloud Manager validieren.](/help/implementing/cloud-manager/managing-code/byo-github.md) Durch diese Integration entfällt die Notwendigkeit, Code konsistent mit dem Adobe-Repository zu synchronisieren, und Sie können Pull-Anforderungen überprüfen, bevor Sie sie in die Hauptverzweigungen zusammenführen. Diese Funktion ist nur für öffentliche GitHub-Anwendungen verfügbar. Unterstützung für selbstgehostetes GitHub ist nicht verfügbar.

Wenn Sie diese neue Funktion testen und Ihr Feedback teilen möchten, senden Sie über die mit Ihrer Adobe ID verknüpfte E-Mail-Adresse eine E-Mail an `Grp-CloudManager_BYOG@adobe.com`.

### Self-Service-Inhaltswiederherstellung {#content-restore}

[Eine neue Self-Service-Funktion zur Inhaltswiederherstellung](/help/operations/restore.md) bietet jetzt eine Backup-Wiederherstellung für bis zu sieben Tage und steht Early-Adopters zu Bewertungszwecken zur Verfügung:

* Zeitpunktgenaue Backup-Wiederherstellung für die letzten 24 Stunden
* Wiederherstellung zu festen Zeiten für bis zu sieben Tage

Wenn Sie diese neue Funktion testen und Ihr Feedback teilen möchten, senden Sie über die mit Ihrer Adobe-ID verknüpfte E-Mail-Adresse eine E-Mail an `aemcs-restorefrombackup-adopter@adobe.com`.

* Das Early-Adopter-Programm ist auf Entwicklungsumgebungen beschränkt.
* Die Verfügbarkeit des Early-Adopter-Programms für diese Funktion ist begrenzt.
* Diese Funktion dient zum Wiederherstellen versehentlich gelöschter Inhalte und ist nicht für die Notfallwiederherstellung vorgesehen.

### Experience Audit-Dashboard {#experience-audit-dashboard}

[Das Experience Audit-Dashboard von Cloud Manager](/help/implementing/cloud-manager/experience-audit-dashboard.md) enthält eine Trend-Ansicht Ihrer Seitenleistungsbewertungen sowie Einblicke und Empfehlungen, die Sie verwenden können, um Verbesserungen vorzunehmen. Experience Audit ist ein Schritt in der Produktions-Pipeline von Cloud Manager.

Das Dashboard verwendet Google Lighthouse, ein automatisiertes Open-Source-Tool zur Verbesserung der Qualität Ihrer Web-Anwendungen. Sie können es für jede Web-Seite ausführen, egal ob öffentlich oder authentifizierungspflichtig. Es enthält Prüfungen für Leistung, Barrierefreiheit, progressive Web-Apps, SEO und mehr.

Möchten Sie das neue Dashboard testen? Senden Sie dazu eine E-Mail an `aem-lighthouse-pilot@adobe.com` von der E-Mail-Adresse, die mit Ihrer Adobe ID verknüpft ist.

## Fehlerbehebungen {#bug-fixes}

* Es wurde ein Fehler behoben, bei dem Konfigurations-Pipelines beim Build-Schritt fehlschlugen und eine unklare Fehlermeldung angezeigt wurde, wenn der Speicherort der Konfigurationsdateien nicht ordnungsgemäß festgelegt wurde. Die Fehlermeldung ist jetzt klar und weist darauf hin, dass die Person prüfen sollte, ob der Speicherort der Konfigurationsdateien korrekt ist.
* Wenn ein Build-Schritt aufgrund eines `BUILD_MAVEN_TRANSFER_ARTIFACT_ERROR` mit dem Status `FAILED` abgeschlossen wird, wird dies nun ordnungsgemäß als Fehler aufgrund von Zusammenführungskonflikten mit der Zielverzweigung beschrieben.
