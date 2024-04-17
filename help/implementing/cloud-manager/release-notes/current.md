---
title: Versionshinweise für Cloud Manager 2024.4.0 in Adobe Experience Manager as a Cloud Service
description: Dies sind die Versionshinweise für Cloud Manager 2024.4.0 in AEM as a Cloud Service.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: f1d8778f3cfb6868740141d008fd0217839e9103
workflow-type: ht
source-wordcount: '706'
ht-degree: 100%

---


# Versionshinweise für Cloud Manager 2024.4.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise zu Cloud Manager 2024.4.0 in AEM as a Cloud Service.

>[!NOTE]
>
>Auf [dieser Seite](/help/release-notes/release-notes-cloud/release-notes-current.md) finden Sie die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service.

## Veröffentlichungsdatum {#release-date}

Die Version 2024.4.0 von Cloud Manager in AEM as a Cloud Service wurde am 10. April 2024 veröffentlicht. Die nächste Version ist für den 9. Mai 2024 geplant.

## Neue Funktionen {#what-is-new}

* Der Löschvorgang wurde für [Edge Delivery](/help/edge/overview.md)-Websites verbessert, indem die Domain-Zuordnungen aus dem Programm aktualisiert wurden, das mit dieser Site verbunden ist.
   * Wenn keine weiteren Sites zugeordnet sind, wird die Zuordnung gelöscht.
* Das Implementierungs-Tracking wurde durch die Bereitstellung von Echtzeit-Status-Updates während der kritischen Startphase einer AEM-Instanz verbessert.
   * Diese Funktion stellt die vollständige Sichtbarkeit Ihres Implementierungsfortschritts sicher, was eine bessere Entscheidungsfindung und operative Effizienz ermöglicht.
* Die Auflistung der [Netzwerkinfrastruktur](/help/security/configuring-advanced-networking.md) wurde insofern verbessert, als alle verbundenen Umgebungen jetzt ohne regionsbasierte Filterung angezeigt werden, um eine umfassendere Ansicht zu erhalten.
* Optimierte Fehlermeldungen für Probleme beim Erstellen von Code ermöglichen eine einfachere Identifizierung der Hauptursachen und der nächsten möglichen Schritte.

## Early-Adopter-Programm {#early-adoption}

Um einige bevorstehende Funktionen testen zu können, müssen Sie Teil des Early-Adopter-Programms von Adobe sein.

### Client-seitige Sammlung über Real User Monitoring (RUM) {#rum}

Sie können den [Datendienst Real User Monitoring (RUM)](/help/implementing/cloud-manager/content-requests.md#cliendside-collection) nutzen, um die Client-seitige Sammlung für AEM as a Cloud Service zu aktivieren.

Der Datendienst Real User Monitoring (RUM) bietet eine präzisere Darstellung der Benutzerinteraktionen und stellt so eine zuverlässige Messung der Website-Interaktionen sicher. Dies ist eine großartige Gelegenheit, erweiterte Einblicke in Ihre Seitenleistung zu erhalten. Dies ist nützlich für Kundinnen und Kunden, die entweder ein von Adobe verwaltetes CDN oder ein nicht von Adobe verwaltetes CDN verwenden. Für diejenigen, die ein nicht von Adobe verwaltetes CDN verwenden, kann die automatisierte Traffic-Berichterstellung jetzt für sie aktiviert werden, sodass keine Traffic-Berichte mehr für Adobe freigegeben werden müssen.

Wenn Sie diese neue Funktion testen und Ihr Feedback teilen möchten, senden Sie bitte über die mit Ihrer Adobe ID verknüpfte E-Mail-Adresse eine E-Mail an `aemcs-rum-adopter@adobe.com`. Geben Sie in Ihrer E-Mail den Domain-Namen für die Produktions-, Staging- und Entwicklungsumgebungen an.  Die Verfügbarkeit des Early-Adopter-Programms für diese Funktion ist begrenzt.

### Bringen Sie Ihren eigenen GitHub mit {#byo-github}

Wenn Sie Ihre Repositorys mit GitHub verwalten, [können Sie jetzt Code direkt in Ihren GitHub-Repositorys über Cloud Manager validieren.](/help/implementing/cloud-manager/managing-code/byo-github.md) Durch diese Integration entfällt die Notwendigkeit, Code ständig mit dem Adobe-Repository zu synchronisieren, und Sie können Pull-Anfragen überprüfen, bevor Sie sie in den Hauptverzweigungen zusammenführen. Diese Funktion ist nur für öffentliche GitHub-Repositorys verfügbar. Unterstützung für selbstgehostetes GitHub-Repository ist nicht verfügbar.

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

* Es wurde ein Fehler behoben, durch den Cloud Manager Artefakte mit dem falschen Commit-Hash wiederverwendet hat.
