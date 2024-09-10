---
title: Versionshinweise für Cloud Manager 2024.9.0 in Adobe Experience Manager as a Cloud Service
description: Erfahren Sie mehr über die Versionshinweise für Cloud Manager 2024.9.0 in AEM as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: 610ae004b6da2f7fc0dae2baa613cb363fe9fb00
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 20%

---

# Versionshinweise für Cloud Manager 2024.9.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise zu Cloud Manager 2024.9.0 in AEM as a Cloud Service.

>[!NOTE]
>
>Siehe [aktuelle Versionshinweise für Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Veröffentlichungsdatum {#release-date}

Die Version 2024.9.0 von Cloud Manager in AEM as a Cloud Service wurde am Freitag, 5. September 2024 veröffentlicht. Die nächste Version ist für den Freitag, 3. Oktober 2024 geplant.

## Neue Funktionen {#what-is-new}

* **Dashboard &quot;Erlebnisprüfung&quot;:**

  Das [erweiterte Experience Audit-Dashboard von Adobe Cloud Manager](/help/implementing/cloud-manager/experience-audit-dashboard.md), das auf Google Lighthouse basiert, bietet Einblicke in die Qualität und Leistung von AEM Sites, indem es die wichtigsten Metriken für Web-Vitals, SEO und Barrierefreiheit auswertet. Es hilft Benutzern, Bereiche zu identifizieren, die verbessert werden können, indem umsetzbare Empfehlungen angeboten werden, sodass Teams das Benutzererlebnis, die Seitenladezeiten und die Site-Compliance verbessern können. Dieses Dashboard vereinfacht die Überwachung kritischer Site-Metriken und stellt sicher, dass AEM Anwendungen hohe Leistungs- und Barrierefreiheitsstandards erfüllen.

* **Von Adobe generierte und verwaltete Domain-Validierungszertifikate:**

  Mit Cloud Manager können Sie jetzt [durch Self-Service-Adobe generierte und verwaltete DV-SSL-Zertifikate (Domain Validation)](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) verwenden. Diese Funktion bietet Ihnen die schnellste, einfachste und kostengünstigste Lösung, um eine sichere Website für Ihre Online-Organisation oder Ihr Unternehmen zu erstellen. <!-- CMGR-52403 -->

  >[!NOTE]
  >
  >[Content Hub](/help/assets/product-overview.md) -Kunden sollen diese Funktion schrittweise im Rahmen eines schrittweisen Rollouts erhalten.

* **Edge Delivery Services-Unterstützung in Cloud Manager:**

  Wenn Sie über eine Edge Delivery Services-Lizenz als Teil von AEM Sites verfügen, können Sie Ihre Site jetzt mit Edge Delivery Services direkt über Cloud Manager](/help/implementing/cloud-manager/edge-delivery-services.md) integrieren. [ Diese Funktion ermöglicht ein geführtes Self-Service Go Live-Erlebnis. Außerdem werden wichtige Workflows wie Domain-Namensverwaltung, SSL-Zertifikate und CDN-Zuordnungen über alle AEM hinweg vereinheitlicht, sodass Konsistenz und Effizienz gewährleistet sind. <!-- CMGR-49859 -->

  >[!NOTE]
  >
  >[Content Hub](/help/assets/product-overview.md) -Kunden sollen diese Funktion schrittweise im Rahmen eines schrittweisen Rollouts erhalten.

* Kunden, die GitHub-Repositorys verwenden, können jetzt Web-Tier-Konfigurations-Pipelines erstellen und verwenden. <!--( KEEP IN? SP: YES CMGR-59046 and Slack https://cq-dev.slack.com/archives/C07LFP5BZ2L/p1725407057847379 ) -->

<!--
## Early adoption program {#early-adoption}

For a chance to test some upcoming features, be a part of Adobe's early adoption program. -->


## Fehlerbehebungen

* Die Paginierung der Tabellenansicht für SSL-Zertifikate funktioniert jetzt erwartungsgemäß. <!-- (CMGR-60804 - [UI] Pagination doesn't work for ssl certificates) -->
* Die falsche Artefaktversion wurde beworben, wenn die Schaltfläche **Build bewerben** von einer Ausführung verwendet wird. <!-- ( KEEP IN? SP: YES CMGR-59519 and Slack https://cq-dev.slack.com/archives/C07LFPN2R08/p1725408253474129 ) -->

<!-- * Slack message says next release? SP: REMOVE (Leave in for now) SSL Certificates table in Cloud Manager now enables pagination in the user experience. ( https://jira.corp.adobe.com/browse/CMGR-61041 and Slack https://cq-dev.slack.com/archives/C07LFRE9QJU/p1725408553760009 ) --<>
