---
title: Versionshinweise für Cloud Manager 2023.12.0 in Adobe Experience Manager as a Cloud Service
description: Dies sind die Versionshinweise für Cloud Manager 2023.12.0 in AEM as a Cloud Service.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: 3e7d3113b25e9b4058130bf3352a612f36ef5c63
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 17%

---


# Versionshinweise für Cloud Manager 2023.12.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise zu Cloud Manager 2023.12.0 in AEM as a Cloud Service.

>[!NOTE]
>
>Auf [dieser Seite](/help/release-notes/release-notes-cloud/release-notes-current.md) finden Sie die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service.

## Veröffentlichungsdatum {#release-date}

Die Cloud Manager -Version 2023.12.0 in AEM as a Cloud Service wurde am 14. Dezember 2023 veröffentlicht. Die nächste Version ist für den 18. Januar 2024 geplant.

## Neue Funktionen {#what-is-new}

* [Benutzerdefinierte Berechtigungen für Cloud Manager](/help/implementing/cloud-manager/custom-permissions.md) Sie können benutzerdefinierte Berechtigungsprofile mit konfigurierbaren Berechtigungen erstellen, um den Zugriff auf Programme, Pipelines und Umgebungen für Cloud Manager-Benutzer zu beschränken.
   * Diese Funktion wird schrittweise eingeführt und mit der für Februar 2024 erwarteten Cloud Manager-Version abgeschlossen.
   * Bitte senden Sie eine E-Mail an `Grp-CloudManager-custom-permissions@adobe.com` von der mit Ihrer Adobe ID verknüpften E-Mail-Adresse aus, wenn Sie eher aktiviert werden möchten.
* Build-Container unterstützen jetzt Node.js, Version 18 für [Frontend-Pipelines](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md)
* Für neu erstellte Cloud Manager-Programme: [das zugehörige New Relic-Unterkonto](/help/implementing/cloud-manager/user-access-new-relic.md) ist nicht standardmäßig aktiviert.
   * Bei bestehenden Programmen, bei denen der Zugriff auf das New Relic-Unterkonto nicht länger als 90 Tage dauert, wird es deaktiviert.
   * Wenn Sie das New Relic-Unterkonto verwenden möchten, müssen Sie sich über Cloud Manager anmelden.
* Die Rollouts von Nebenversionen für Java 8 und 11 und Updates für Maven [bekannt gegeben und mit der Oktober-Version von Cloud Manager begonnen](/help/implementing/cloud-manager/release-notes/2023/2023-10-0.md) wurden abgeschlossen.
   * Unterstützung für Node 18 wurde für Frontend- und vollständige Stapel-Pipelines hinzugefügt.
   * Die untergeordnete Java 8-Version wurde aktualisiert auf `jdk1.8.0_371`.
   * Die untergeordnete Java 11-Version wurde auf `jdk-11.0.20`.
   * Unterstützung für Java 17 wurde hinzugefügt.
   * Maven wurde auf Version 3.8.8 aktualisiert.
   * Das Basisbild des Build-Containers wurde auf Ubuntu 22.04 aktualisiert.

## Early-Adopter-Programm {#early-adoption}

Um einige bevorstehende Funktionen testen zu können, sollten Sie Teil des frühzeitigen Adoptionsprogramms von Adobe sein.

### Clientseitige Erfassung über die Echtzeit-Benutzerüberwachung (RUM) {#rum}

Sie können die [Datendienst für die Echtzeit-Benutzerüberwachung (RUM)](/help/implementing/cloud-manager/content-requests.md#cliendside-collection) , um die clientseitige Erfassung für AEM as a Cloud Service zu aktivieren.

Der Real User Monitoring (RUM) Data Service bietet eine präzisere Darstellung der Benutzerinteraktionen und stellt so eine zuverlässige Messung der Website-Interaktion sicher. Dies ist eine großartige Gelegenheit, erweiterte Einblicke in Ihre Seitenleistung zu erhalten. Dies ist nützlich für Kunden, die entweder Adobe-verwaltetes CDN oder nicht-Adobe verwaltetes CDN verwenden. Für Kunden, die ein nicht von Adobe verwaltetes CDN verwenden, kann die automatisierte Traffic-Berichterstellung jetzt für sie aktiviert werden, sodass keine Traffic-Berichte mehr für Adobe freigegeben werden müssen.

Wenn Sie diese neue Funktion testen und Ihr Feedback teilen möchten, senden Sie bitte eine E-Mail an `aemcs-rum-adopter@adobe.com` von der mit Ihrer Adobe ID verknüpften E-Mail-Adresse aus. Geben Sie den Domänennamen für die Produktions-, Staging- und Entwicklungsumgebungen in Ihre E-Mail ein.  Die Verfügbarkeit des frühen Adopter-Programms dieser Funktion ist begrenzt.

### Bringen Sie Ihren eigenen GitHub mit {#byo-github}

Wenn Sie Ihre Repositorys mit GitHub verwalten, [können Sie jetzt Code direkt in Ihren GitHub-Repositorys über Cloud Manager validieren.](/help/implementing/cloud-manager/managing-code/byo-github.md) Durch diese Integration entfällt die Notwendigkeit, Code ständig mit dem Adobe-Repository zu synchronisieren, und Sie können Pull-Anfragen überprüfen, bevor Sie sie in den Hauptverzweigungen zusammenführen.

Wenn Sie diese neue Funktion testen und Ihr Feedback teilen möchten, senden Sie eine E-Mail an `Grp-CloudManager_BYOG@adobe.com` von Ihrer mit Ihrer Adobe ID verknüpften E-Mail-Adresse aus.

### Self-Service Content Restore {#content-restore}

[Neue Funktion zur Wiederherstellung von Self-Service-Inhalten](/help/operations/restore.md) bietet jetzt eine Backup-Wiederherstellung für bis zu sieben Tage und steht frühen Anwendern zu Auswertungszwecken zur Verfügung:

* Point-in-Time-Backup-Wiederherstellung für die letzten 24 Stunden
* Feste Zeitwiederherstellung für bis zu sieben Tage

Wenn Sie diese neue Funktion testen und Ihr Feedback teilen möchten, senden Sie eine E-Mail an `aemcs-restorefrombackup-adopter@adobe.com` aus Ihrer mit Ihrer Adobe ID verknüpften E-Mail.

* Das Programm für den frühen Anwender ist auf Entwicklungsumgebungen beschränkt.
* Die Verfügbarkeit des frühen Adopter-Programms dieser Funktion ist begrenzt.
* Diese Funktion dient zum Wiederherstellen versehentlich gelöschter Inhalte und ist nicht für die Notfallwiederherstellung vorgesehen.

### Experience Audit-Dashboard {#experience-audit-dashboard}

[Das Dashboard &quot;Experience Audit&quot;von Cloud Manager](/help/implementing/cloud-manager/experience-audit-dashboard.md) enthält eine Trendansicht Ihrer Seitenleistungsbewertungen sowie Einblicke und Empfehlungen, die Sie bei der Verbesserung unterstützen. Experience Audit ist ein Schritt in der Produktions-Pipeline von Cloud Manager.

Das Dashboard verwendet Google Lighthouse, ein Open-Source-automatisiertes Tool zur Verbesserung der Qualität Ihrer Webanwendungen. Sie können sie für jede Webseite, jede öffentliche Seite oder jede Webseite ausführen, für die eine Authentifizierung erforderlich ist. Sie enthält Prüfungen zu Leistung, Barrierefreiheit, progressiven Web-Apps, SEO und mehr.

Möchten Sie das neue Dashboard testen? Senden Sie zunächst eine E-Mail an `aem-lighthouse-pilot@adobe.com` aus Ihrer mit Ihrer Adobe ID verknüpften E-Mail.
