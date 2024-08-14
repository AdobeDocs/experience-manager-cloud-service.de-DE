---
title: Versionshinweise für Cloud Manager 2024.8.0 in Adobe Experience Manager as a Cloud Service
description: Erfahren Sie mehr über die Versionshinweise für Cloud Manager 2024.8.0 in AEM as a Cloud Service.
feature: Release Information
role: Admin
source-git-commit: bf8bab5a195dde6cf15a2fd52e51d58c0215fdf3
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 31%

---


# Versionshinweise für Cloud Manager 2024.8.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise zu Cloud Manager 2024.8.0 in AEM as a Cloud Service.

>[!NOTE]
>
>Auf [dieser Seite](/help/release-notes/release-notes-cloud/release-notes-current.md) finden Sie die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service.

## Veröffentlichungsdatum {#release-date}

Die Version 2024.8.0 von Cloud Manager in AEM as a Cloud Service wurde am Dienstag, 12. August 2024 veröffentlicht. Die nächste Version wird am 9. September 2021 veröffentlicht.

## Neuerungen {#what-is-new}

* [Zusätzliche Veröffentlichungsbereiche](/help/operations/additional-publish-regions.md) und eine SLA](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#sla) (Service Level Agreement) von [99,99 % sind jetzt für AEM Forms as a Cloud Service verfügbar.
   * Durch diese Verbesserung können Sie höhere SLAs mit erhöhter Betriebszeit und geringerer Latenz erzielen und so optimale Erlebnisse für global verteilte Benutzer sicherstellen.

## Frühzeitige Annahme {#early-adoption}

Um einige bevorstehende Funktionen testen zu können, müssen Sie Teil des Early-Adopter-Programms von Adobe sein.

### Edge Delivery Services-Unterstützung in Cloud Manager {#edge-delivery-services}

Wenn Sie Edge Delivery Services als Teil von AEM Sites lizenziert haben, können Sie Ihre Site jetzt mit Edge Delivery Services direkt in Cloud Manager](/help/implementing/cloud-manager/edge-delivery-services.md) einbinden und mithilfe eines geleiteten Self-Service-Erlebnisses live gehen.[

Diese Funktion bietet ein einheitliches Erlebnis für alle AEM Eigenschaften. Sie stellt die Konsistenz wichtiger Workflows wie Domain-Namensverwaltung, SSL-Zertifikatverwaltung und CDN-Zuordnungen sicher.

Wenn Sie diese neue Funktion testen und Ihr Feedback teilen möchten, senden Sie eine E-Mail an `aemcs-cmedgedelsvs-program-adopter@adobe.com` aus der E-Mail-Adresse, die Ihrer Adobe ID zugeordnet ist.

### DV-Zertifikate (Domain Validated)

Mit Cloud Manager können Sie jetzt [Self-Service-SSL-Zertifikate für die validierte Domain (DV) generieren und verwalten](/help/implementing/cloud-manager/managing-ssl-certifications/domain-validated-certificates.md). Diese Funktion bietet Ihnen die schnellste, einfachste und kostengünstigste Lösung, um eine sichere Website für Ihr Online-Geschäft zu erstellen.

Wenn Sie diese neue Funktion testen und Feedback geben möchten, senden Sie eine E-Mail an `Grp-aemcs-dv-dert-adopter@adobe.com`, indem Sie die mit Ihrer Adobe ID verknüpfte E-Mail-Adresse verwenden.

### Experience Audit-Dashboard {#experience-audit-dashboard}

[Das Experience Audit-Dashboard von Cloud Manager](/help/implementing/cloud-manager/experience-audit-dashboard.md) enthält eine Trend-Ansicht Ihrer Seitenleistungsbewertungen sowie Einblicke und Empfehlungen, die Sie verwenden können, um Verbesserungen vorzunehmen. Experience Audit ist ein Schritt in der Produktions-Pipeline von Cloud Manager.

Das Dashboard verwendet Google Lighthouse, ein automatisiertes Open-Source-Tool zur Verbesserung der Qualität Ihrer Web-Anwendungen. Sie können sie verwenden, um jede Webseite zu prüfen, ob öffentlich oder authentifizierungspflichtig. Es bietet Bewertungen der Leistung, Barrierefreiheit, progressiven Web-Apps, SEO und mehr.

Möchten Sie das neue Dashboard ausprobieren? Senden Sie zunächst eine E-Mail an `aem-lighthouse-pilot@adobe.com`, indem Sie die mit Ihrer Adobe ID verknüpfte E-Mail verwenden.

## Fehlerbehebung

* Ein seltenes Problem wurde behoben, bei dem Pipeline-Schritte nach dem Löschen der Pipeline ausgeführt wurden.
* In seltenen Fällen wurde ein Problem behoben, durch das in Konfigurations-Pipelines fälschlicherweise der Status &quot;`FAILED`&quot;angezeigt wurde.
