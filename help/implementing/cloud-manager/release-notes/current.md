---
title: Versionshinweise für Cloud Manager 2024.6.0 in Adobe Experience Manager as a Cloud Service
description: Dies sind die Versionshinweise für Cloud Manager 2024.6.0 in AEM as a Cloud Service.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
role: Admin
source-git-commit: 8eaf2b70734cec1fedace64d74059ee161785b39
workflow-type: ht
source-wordcount: '548'
ht-degree: 100%

---


# Versionshinweise für Cloud Manager 2024.6.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise zu Cloud Manager 2024.6.0 in AEM as a Cloud Service.

>[!NOTE]
>
>Auf [dieser Seite](/help/release-notes/release-notes-cloud/release-notes-current.md) finden Sie die aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service.

## Veröffentlichungsdatum {#release-date}

Die Version 2024.6.0 von Cloud Manager in AEM as a Cloud Service wurde am 6. Juni 2024 veröffentlicht. Die nächste Version ist für den 11. Juli 2024 geplant.

## Neue Funktionen {#what-is-new}

* Nun ist die [Verwendung Ihrer eigenen GitHub-Repositorys](/help/implementing/cloud-manager/managing-code/private-repositories.md) als Quellen für sowohl Full-Stack- als auch Frontend-Pipelines möglich.
   * Darüber hinaus können Sie GitHub-Repositorys mit [Git-Untermodulen](/help/implementing/cloud-manager/managing-code/git-submodules.md) nutzen. So haben Sie mehr Kontrolle über die automatisch generierten Pipelines, die zur Prüfung von Pull-Anfragen verwendet werden, und können das Verhalten für wichtige Metriken während der Code-Scan-Phase definieren.
   * [Sie haben auch die Möglichkeit](/help/implementing/cloud-manager/managing-code/github-check-config.md), den Berichtsverlauf auf GitHub beizubehalten, die Pipeline zu benennen und Pipeline-Variablen entsprechend Ihren Anforderungen festzulegen.
* Die [Wiederherstellung von Self-Service-Inhalten](/help/operations/restore.md) bietet eine Backup-Wiederherstellung für bis zu sieben Tage und außerdem:
   * Zeitpunktgenaue Backup-Wiederherstellung für die letzten 24 Stunden
   * Wiederherstellung zu einem festen Zeitpunkt für bis zu sieben Tage
* Es wurden [neue OakPal-Regeln](/help/implementing/cloud-manager/custom-code-quality-rules.md#oakpal-ui-content-package) zur Code-Qualitätsprüfung von Cloud Manager hinzugefügt.
   * Jede neue Regel, die ab Juni 2024 hinzugefügt wurde, ist eine unterbrechungsfreie Änderung.
   * Sie werden dringend aufgefordert, sich dieser so bald wie möglich anzunehmen, da diese neuen Regeln dazu führen, dass Pipelines ab der Cloud Manager-Version August 2024 fehlschlagen.

## Early-Adopter-Programm {#early-adoption}

Um einige bevorstehende Funktionen testen zu können, müssen Sie Teil des Early-Adopter-Programms von Adobe sein.

### Edge Delivery Services-Unterstützung in Cloud Manager {#edge-delivery-services}

Wenn Sie Edge Delivery Services als Teil von Adobe Experience Manager Sites lizenziert haben, [können Sie nun Ihre Site mit Edge Delivery Services direkt in Cloud Manager integrieren](/help/implementing/cloud-manager/edge-delivery-services.md) und mit einem geführten Self-Service-Erlebnis die Live-Schaltung vornehmen.

Dies ermöglicht ein einheitliches Erlebnis für alle AEM-Eigenschaften und gewährleistet die Konsistenz mit allen wichtigen Workflows, einschließlich Domain-Namensverwaltung, SSL-Zertifikatverwaltung und CDN-Zuordnungen.

Wenn Sie diese neue Funktion testen und Ihr Feedback teilen möchten, senden Sie bitte über die mit Ihrer Adobe ID verknüpfte E-Mail-Adresse eine E-Mail an `aemcs-cmedgedelsvs-program-adopter@adobe.com`.

### DV-Zertifikate (Domain Validated)

Mit Cloud Manager können Sie jetzt [Self-Service-SSL-Zertifikate mit Domain-Validierung (DV) erstellen und verwalten.](/help/implementing/cloud-manager/managing-ssl-certifications/domain-validated-certificates.md) Dadurch erhalten Sie die schnellste, einfachste und kostengünstigste Lösung, um eine sichere Website für Ihr Online-Business zu erstellen.

Wenn Sie diese neue Funktion testen und Ihr Feedback teilen möchten, senden Sie bitte über die mit Ihrer Adobe ID verknüpfte E-Mail-Adresse eine E-Mail an `Grp-aemcs-dv-dert-adopter@adobe.com`.

<!-- RICK: REMOVED THIS SECTION AS PER EMAIL REQUEST TO DL-AEM-DOCS FROM SHWETA DUA, WEDNESDAY, JUNE 12, 2024 ### Client-Side Collection via Real Use Monitoring (RUM) {#rum}

You can leverage the [Real Use Monitoring (RUM) Data Service](/help/implementing/cloud-manager/content-requests.md#cliendside-collection) to enable client-side collection for AEM as a Cloud Service.

Real Use Monitoring (RUM) Data Service offers a more precise reflection of user interactions, ensuring a reliable measure of website engagement. It is a great opportunity to gain advanced insights into your page performance. This is beneficial for customers who use either Adobe-managed CDN or non-Adobe managed CDN. For customers using a non-Adobe managed CDN, automated traffic reporting can now be enabled for them, thus removing the need to share any traffic report with Adobe.

If you are interested in testing this new feature and sharing your feedback, please send an email to `aemcs-rum-adopter@adobe.com` from the email address associated with your Adobe ID. Please include the domain name for production, stage, and dev environments in your email.  Availability of the early adopter program of this feature is limited.-->

### Experience Audit-Dashboard {#experience-audit-dashboard}

[Das Experience Audit-Dashboard von Cloud Manager](/help/implementing/cloud-manager/experience-audit-dashboard.md) enthält eine Trend-Ansicht Ihrer Seitenleistungsbewertungen sowie Einblicke und Empfehlungen, die Sie verwenden können, um Verbesserungen vorzunehmen. Experience Audit ist ein Schritt in der Produktions-Pipeline von Cloud Manager.

Das Dashboard verwendet Google Lighthouse, ein automatisiertes Open-Source-Tool zur Verbesserung der Qualität Ihrer Web-Anwendungen. Sie können es für jede Web-Seite ausführen, egal ob öffentlich oder authentifizierungspflichtig. Es enthält Prüfungen für Leistung, Barrierefreiheit, progressive Web-Apps, SEO und mehr.

Möchten Sie das neue Dashboard testen? Senden Sie dazu eine E-Mail an `aem-lighthouse-pilot@adobe.com` von der E-Mail-Adresse, die mit Ihrer Adobe ID verknüpft ist.
