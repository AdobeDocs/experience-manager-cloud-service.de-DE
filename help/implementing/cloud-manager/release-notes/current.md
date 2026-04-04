---
title: Versionshinweise für Cloud Manager 2026.4.0
description: Erfahren Sie mehr über Version 2026.4.0 von Cloud Manager in Adobe Experience Manager as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: aa8aba7f798e251c8a25ee247402e23517707e88
workflow-type: tm+mt
source-wordcount: '634'
ht-degree: 23%

---

# Versionshinweise für Cloud Manager 2026.4.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

<!-- https://wiki.corp.adobe.com/display/DMSArchitecture/%5BKT%5D+Cloud+Manager+2025.08.0+Release -->

Erfahren Sie mehr über Version 2026.4.0 von Cloud Manager in AEM (Adobe Experience Manager) as a Cloud Service.

Hier finden Sie die [aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Veröffentlichungsdaten {#release-date}

Die Version 2026.4.0 von Cloud Manager in AEM as a Cloud Service wurde am Donnerstag, dem Freitag, 2. April 2026 veröffentlicht.

Die Veröffentlichung der nächsten Version ist für Donnerstag, den Freitag, 7. Mai 2026 geplant.


## Neue Funktionen - Cloud Manager {#cloud-manager-whats-new}

* **Cloud Manager MCP-Server für KI-gestützte IDEs**

  Sie können jetzt einen MCP-Server (Model Context Protocol) verwenden, der öffentliche Cloud Manager-APIs als Tools für KI-aktivierte IDEs (z. B. Cursor) verfügbar macht. Nach dem Verbinden können Sie Konversationsaufforderungen verwenden, um Programme, Pipelines, Umgebungen und Repositorys aufzulisten und zu verwalten, sodass Sie schneller arbeiten können, ohne den Editor zu verlassen.

  Siehe die Dokumentation [Verwenden von MCP mit AEM as a Cloud Service](/help/ai-in-aem/mcp-support/using-mcp-with-aem-as-a-cloud-service.md).

  Siehe das Tutorial [Cloud Manager MCP Server](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/ai/mcp-servers/cloud-manager#).

* **Schnellere Builds mit Modul-Caching**

  Ein neues Build-Modell kompiliert nur geänderte Module (nicht das gesamte Repository) mithilfe des Caching auf Modulebene, um die Erstellungszeiten zu verkürzen. Sie gilt für produktionsfremde Code-Qualitäts-Pipelines und produktionsfremde Full-Stack-Entwicklungs-Pipelines.

  Siehe [Informationen zur Verwendung von Smart Build in einer produktionsfremden Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#about-smart-build) und [Hinzufügen einer produktionsfremden Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#full-stack-code).

* **Prüfung der Serverkonnektivität durch Self-Service**

  Mit Cloud Manager können Sie jetzt Self-Service-Prüfungen in Ihrer Umgebung durchführen. Diese Prüfungen überprüfen die Erreichbarkeit des Hosts und des Ports und bestätigen die DNS-Auflösung mithilfe des konfigurierten Netzwerkpfads Ihres Programms, einschließlich Ausgang. Mit dieser Funktion können Sie erweiterte Netzwerkfunktionen validieren und Integrationsprobleme schneller beheben, ohne Support-Fälle öffnen oder auf Pods zugreifen zu müssen. <!-- SKYOPS-23640 -->

  Siehe [Netzwerkverbindungstest](/help/security/network-connectivity-test.md)

* **Verbesserte Stabilität, Leistung und Zuverlässigkeit**

  Diese Version umfasst Optimierungs- und Wartungsaktualisierungen, die die Stabilität, Leistung und Zuverlässigkeit von Cloud Manager verbessert haben.


## Beta-Programme {#private-beta-program}

Nehmen Sie am Beta-Programm von Cloud Manager teil, um exklusiven Zugriff auf bevorstehende Funktionen vor ihrer regulären Veröffentlichung zu erhalten.

>[!IMPORTANT]
>
>Beta-Versionen können Mängel enthalten und werden „wie besehen“ ohne Gewährleistung jeglicher Art bereitgestellt. Adobe ist nicht verpflichtet, die Beta-Versionen zu pflegen, zu korrigieren, zu aktualisieren, zu ändern oder anderweitig zu unterstützen (durch Adobe Support Services oder anderweitig). Adobe empfiehlt Kunden, Vorsicht walten zu lassen und sich nicht auf die ordnungsgemäße Funktionsweise oder Leistung von Beta-Versionen oder auf begleitende Dokumentationen oder Materialien zu verlassen. Funktionen und APIs in der Beta-Version können ohne Vorankündigung geändert werden. Jede Nutzung der Beta-Versionen erfolgt daher ausschließlich auf eigene Gefahr des Kunden.

Siehe auch [AEM Beta-Programme](/help/release-notes/release-notes-cloud/release-notes-current.md#aem-beta-programs)

Derzeit stehen die folgenden Möglichkeiten zur Verfügung:

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

Um der Beta beizutreten, senden Sie eine E-Mail an [](mailto:beta_quickbuild_cmpipelines@adobe.com)beta_quickbuild_cmpipelines@adobe.com) mit Ihrer Adobe-OrgID und Programm-ID.

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

In der Cloud Manager-Version vom April 2026 gibt es keine signifikanten Fehlerbehebungen.

<!-- ## Known issues {#known-issues} -->

