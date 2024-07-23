---
title: Versionshinweise für Cloud Manager 2024.7.0 in Adobe Experience Manager as a Cloud Service
description: Dies sind die Versionshinweise für Cloud Manager 2024.7.0 in AEM as a Cloud Service.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
role: Admin
source-git-commit: 12e19fe771c0b70ec471949944141f4d6858cbfd
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 62%

---


# Versionshinweise für Cloud Manager 2024.7.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise zu Cloud Manager 2024.7.0 in AEM as a Cloud Service.

>[!NOTE]
>
>Auf [dieser Seite](/help/release-notes/release-notes-cloud/release-notes-current.md) finden Sie die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service.

## Veröffentlichungsdatum {#release-date}

Die Cloud Manager-Version 2024.7.0 in AEM as a Cloud Service wurde am 18. Juli 2024 veröffentlicht. Die nächste Version ist für den 8. August 2024 geplant.

## Neue Funktionen {#what-is-new}

* Für [Produktions-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#adding-production-pipeline) und [produktionsfremde Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#adding-non-production-pipeline) ist jetzt der Trigger **Bei Git-Änderungen** für [private Repositorys](/help/implementing/cloud-manager/managing-code/private-repositories.md) verfügbar, um die Pipeline bei einem Commit zu starten.
   * Diese wird schrittweise eingeführt und bis Mitte August abgeschlossen sein.
* Beim Hinzufügen eines [Adobe-verwalteten DV-Zertifikats, ](/help/implementing/cloud-manager/managing-ssl-certifications/domain-validated-certificates.md) können Sie jetzt ein einzelnes Zertifikat hinzufügen, das mehrere Domänen abdeckt, anstatt für jede Domäne ein Zertifikat zu erstellen.
* Lösungen ohne [zusätzliche Veröffentlichungsbereiche](/help/operations/additional-publish-regions.md) können jetzt einem Programm hinzugefügt werden, sofern das Programm mindestens über eine Sites- oder Forms-Lösung verfügt.
* Lösungen ohne SLA](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#sla) von [99,99 % können jetzt einem Programm hinzugefügt werden, solange das Programm mindestens über eine Sites- oder Forms-Lösung verfügt.
* Das Dashboard [Erlebnisprüfung](/help/implementing/cloud-manager/experience-audit-dashboard.md) wurde auf verschiedene Weise verbessert.
   * Prüfungen werden jetzt mit `.com` -Endpunkten über CDN ausgeführt, wobei der vorherige `.net` -Ansatz ersetzt wird.
      * Diese Änderung simuliert reale Benutzererlebnisse genauer und hilft Ihnen, fundiertere Entscheidungen über die Verwaltung und Optimierung Ihrer Website zu treffen.
   * An der Benutzeroberfläche von Experience Audit wurden mehrere Verbesserungen vorgenommen, darunter:
      * Eine Trendansicht von Leistung, Best Practices, SEO und Barrierefreiheit wurde hinzugefügt.
      * Der Rohbericht-Link &quot;Lighthouse&quot;ist jetzt intuitiver sichtbar, direkt im Bereich mit den Scan-Momentaufnahmen-Details.
      * Der Abschnitt mit Empfehlungen für Lighthouse wurde verbessert.
   * Die PWA-Metrik wurde in Übereinstimmung mit der Lighthouse-Version 12.0.0 entfernt, die diese Metrik eliminierte.
* [Der AEM Projektarchetyp](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de) wurde auf Version 49 von [aktualisiert.](https://github.com/adobe/aem-project-archetype/tree/aem-project-archetype-49)

## Early-Adopter-Programm {#early-adoption}

Um einige bevorstehende Funktionen testen zu können, müssen Sie Teil des Early-Adopter-Programms von Adobe sein.

### Edge Delivery Services-Unterstützung in Cloud Manager {#edge-delivery-services}

Wenn Sie Edge Delivery Services als Teil von Adobe Experience Manager Sites lizenziert haben, [können Sie nun Ihre Site mit Edge Delivery Services direkt in Cloud Manager integrieren](/help/implementing/cloud-manager/edge-delivery-services.md) und mit einem geführten Self-Service-Erlebnis die Live-Schaltung vornehmen.

Dies ermöglicht ein einheitliches Erlebnis für alle AEM-Eigenschaften und gewährleistet die Konsistenz mit allen wichtigen Workflows, einschließlich Domain-Namensverwaltung, SSL-Zertifikatverwaltung und CDN-Zuordnungen.

Wenn Sie diese neue Funktion testen und Ihr Feedback teilen möchten, senden Sie bitte über die mit Ihrer Adobe ID verknüpfte E-Mail-Adresse eine E-Mail an `aemcs-cmedgedelsvs-program-adopter@adobe.com`.

### DV-Zertifikate (Domain Validated)

Mit Cloud Manager können Sie jetzt [Self-Service-SSL-Zertifikate mit Domain-Validierung (DV) erstellen und verwalten.](/help/implementing/cloud-manager/managing-ssl-certifications/domain-validated-certificates.md) Dadurch erhalten Sie die schnellste, einfachste und kostengünstigste Lösung, um eine sichere Website für Ihr Online-Business zu erstellen.

Wenn Sie diese neue Funktion testen und Ihr Feedback teilen möchten, senden Sie bitte über die mit Ihrer Adobe ID verknüpfte E-Mail-Adresse eine E-Mail an `Grp-aemcs-dv-dert-adopter@adobe.com`.

### Experience Audit-Dashboard {#experience-audit-dashboard}

[Das Experience Audit-Dashboard von Cloud Manager](/help/implementing/cloud-manager/experience-audit-dashboard.md) enthält eine Trend-Ansicht Ihrer Seitenleistungsbewertungen sowie Einblicke und Empfehlungen, die Sie verwenden können, um Verbesserungen vorzunehmen. Experience Audit ist ein Schritt in der Produktions-Pipeline von Cloud Manager.

Das Dashboard verwendet Google Lighthouse, ein automatisiertes Open-Source-Tool zur Verbesserung der Qualität Ihrer Web-Anwendungen. Sie können es für jede Web-Seite ausführen, egal ob öffentlich oder authentifizierungspflichtig. Es enthält Prüfungen für Leistung, Barrierefreiheit, progressive Web-Apps, SEO und mehr.

Möchten Sie das neue Dashboard testen? Senden Sie dazu eine E-Mail an `aem-lighthouse-pilot@adobe.com` von der E-Mail-Adresse, die mit Ihrer Adobe ID verknüpft ist.
