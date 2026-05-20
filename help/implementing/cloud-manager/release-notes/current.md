---
title: Versionshinweise für Cloud Manager 2026.5.0
description: Erfahren Sie mehr über die Version Cloud Manager 2026.5.0 in Adobe Experience Manager as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: 6de869b0633bb372da8502e45f0956a896aef00b
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 10%

---

# Versionshinweise für Cloud Manager 2026.5.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

<!-- https://wiki.corp.adobe.com/display/DMSArchitecture/%5BKT%5D+Cloud+Manager+2025.08.0+Release -->

Erfahren Sie mehr über die Version Cloud Manager 2026.5.0 in AEM (Adobe Experience Manager) as a Cloud Service.

Hier finden Sie die [aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Veröffentlichungsdaten {#release-date}

Cloud Manager 2026.5.0 wurde in AEM as a Cloud Service am Donnerstag, 7. Mai 2026 veröffentlicht.

Die nächste geplante Version ist Donnerstag, der 4. Juni 2026.


## Neue Funktionen - Cloud Manager {#cloud-manager-whats-new}

* **Soft Delete für ein Produktionsprogramm**

  Cloud Manager ermöglicht es Kunden jetzt, Produktionsprogramme mithilfe eines Soft-Delete-Workflows zu löschen. Sie können gelöschte Programme innerhalb von 30 Tagen wiederherstellen und erhalten so ein zusätzliches Sicherheitsfenster vor dem endgültigen Löschen. Diese Funktion wird im Laufe des Monats Mai schrittweise eingeführt.

  Siehe [Markieren eines Produktionsprogramms zum Löschen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md#delete-production-program).

## Beta-Programme {#private-beta-program}

Nehmen Sie am Beta-Programm von Cloud Manager teil, um exklusiven Zugriff auf bevorstehende Funktionen vor ihrer regulären Veröffentlichung zu erhalten.

>[!IMPORTANT]
>
>Beta-Versionen können Mängel enthalten und werden „wie besehen“ ohne Gewährleistung jeglicher Art bereitgestellt. Adobe ist nicht verpflichtet, die Beta-Versionen zu pflegen, zu korrigieren, zu aktualisieren, zu ändern oder anderweitig zu unterstützen (durch Adobe Support Services oder anderweitig). Adobe empfiehlt Kunden, Vorsicht walten zu lassen und sich nicht auf die ordnungsgemäße Funktionsweise oder Leistung von Beta-Versionen oder auf begleitende Dokumentationen oder Materialien zu verlassen. Funktionen und APIs in der Beta-Version können ohne Vorankündigung geändert werden. Jede Nutzung der Beta-Versionen erfolgt daher ausschließlich auf eigene Gefahr des Kunden.

Siehe auch [AEM Beta-Programme](/help/release-notes/release-notes-cloud/release-notes-current.md#aem-beta-programs)

Die folgenden Möglichkeiten des Beta-Programms sind derzeit verfügbar:

### Edge Delivery Services mit AEM-Authoring und flexibler Veröffentlichungsstufenkonfiguration {#eds-with-aem-authoring}

Cloud Manager führt zwei Funktionen ein, die moderne Bereitstellungsarchitekturen unterstützen.

* **Edge Delivery Services mit AEM-Authoring**
Sie können jetzt Sites mit Edge Delivery Services bereitstellen, während Sie weiterhin Inhalte im AEM-Autorenmodus erstellen. Je nach Ihren Workflow-Voreinstellungen können Sie zwischen den folgenden Authoring-Ansätzen wählen:

   * Dokumentenbasiertes Authoring
   * AEM Author-based Authoring

Weitere Informationen finden Sie unter [Erstellen einer Edge Delivery-Site in Cloud Manager](/help/implementing/cloud-manager/edge-delivery/create-edge-delivery-site.md#one-click-edge-delivery-site).

* **Flexible Konfiguration der Veröffentlichungsebene**

Mit Cloud Manager können Sie jetzt konfigurieren, ob für Ihr Programm eine Veröffentlichungsebene erforderlich ist. Diese Flexibilität ermöglicht die Einrichtung von Umgebungen, die besser zu Ihrer gewählten Bereitstellungsarchitektur passen.

Weitere Informationen finden Sie unter [Flexible Veröffentlichungsebene (Beta)](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#flexible-publish-tier).

Um sich der Beta anzuschließen, senden Sie eine E-Mail an [](mailto:grp-beta_xwalk-publish_config@adobe.com)grp-beta_xwalk-publish_config@adobe.com) mit Ihrer Adobe Organisations-ID und Programm-ID.

### Schnellere Builds mit Modul-Caching {#quick-build-cm-pipelines}

Ein neues Build-Modell kompiliert nur geänderte Module (nicht das gesamte Repository) mithilfe des Caching auf Modulebene, um die Erstellungszeiten zu verkürzen. Dies gilt für Produktions-Pipelines. Sie steuern, welche Produktions-Pipelines &quot;**Build“**.

Weitere Informationen finden Sie in den folgenden Themen:

* [Verwenden von Smart Build in einer Produktions-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#about-smart-build).
* [Produktions-Pipeline ](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#full-stack-code).

Um sich der Beta anzuschließen, senden Sie eine E-Mail an [](mailto:beta_quickbuild_cmpipelines@adobe.com)beta_quickbuild_cmpipelines@adobe.com) mit Ihrer Adobe Organisations-ID und Programm-ID.

<!-- 
OLD
### Experience Hub Extensibility and Customization {#exp-hub-extensibility}

[Experience Hub](/help/experience-hub.md) serves as your entry point to AEM, customized for your organization's needs. Tell Adobe about your existing AEM UI Extensions so they can help you enable them in Experience Hub with minimal effort.

![Diagram of Experience Hub extensibility and customization workflow](/help/implementing/cloud-manager/release-notes/assets/experience-hub-extensibility-customization.png)

Embed custom experiences in Experience Hub to extend and personalize your organization's dashboard. In addition to Adobe's built-in widgets, add your own using the [UI Extensibility](https://developer.adobe.com/uix/docs/) framework. Build JavaScript-based UI apps and surface them to your users to meet business-specific requirements and workflows. 

Interested in the beta? Email [beta_exphubextensibility@adobe.com](mailto:beta_exphubextensibility@adobe.com) with your Adobe OrgID and a short description of the customization you intend to create.
-->

<!-- 
OLD
### Support for Custom Author Domains in Cloud Service

AEM Cloud Service is going to soon support one custom domain per Author environment.
-->



## Fehlerbehebungen {#bug-fixes}

Es gibt keine signifikanten Fehlerbehebungen in der Cloud Manager-Version vom Mai 2026.

<!-- ## Known issues {#known-issues} -->

