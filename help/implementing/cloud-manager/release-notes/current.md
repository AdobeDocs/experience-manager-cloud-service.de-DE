---
title: Versionshinweise für Cloud Manager 2026.7.0
description: Erfahren Sie mehr über die Version Cloud Manager 2026.7.0 in Adobe Experience Manager as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: dea8a3df29876df1c97454a97602045eb50121ad
workflow-type: tm+mt
source-wordcount: '932'
ht-degree: 3%

---

# Versionshinweise für Cloud Manager 2026.7.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

Erfahren Sie mehr über die Version Cloud Manager 2026.7.0 in AEM (Adobe Experience Manager) as a Cloud Service.

Hier finden Sie die [aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Veröffentlichungsdaten {#release-date}

Cloud Manager 2026.7.0 wurde in AEM as a Cloud Service am Donnerstag, 9. Juli 2026 veröffentlicht.

Die nächste geplante Version ist Donnerstag, der 6. August 2026.


## Neue Funktionen - Cloud Manager {#cloud-manager-whats-new}

* **Bring Your Own Git (BYOG) — Geheime Authentifizierung für Git-Klon**

  Sie können jetzt Git-Klon-Anfragen an Ihr [!DNL Bring Your Own Git]-Repository authentifizieren, indem Sie zusätzlich zu einem IMS-Token das von Cloud Manager generierte Byogit-Geheimnis verwenden. Mit dieser Funktion können [!DNL Edge Delivery Services] Kunden dieselben Anmeldeinformationen verwenden, die helix-admin bereits für die Code-Synchronisierung speichert. Bestehende Workflows für IMS-authentifizierte Klone sind davon nicht betroffen.

  Siehe [Authentifizieren von Git-Klon-Anfragen](/help/implementing/cloud-manager/edge-delivery/config-edge-delivery-site-with-byog.md#authenticate-git-clone-requests).

* **VPN-Netzwerkinfrastruktur - BGP-Routing und mehrere Verbindungen**\
  Die VPN-Netzwerkinfrastruktur-API für erweiterte Netzwerke unterstützt jetzt neben dem vorhandenen statischen Routing auch das dynamische BGP (Border Gateway Protocol)-Routing. Teams können die BGP pro Verbindung konfigurieren, indem sie die kundenseitige BGP-Autonomous-System-Nummer und Peering-Adresse angeben. Cloud Manager verwaltet das Routenlernen dynamisch - keine statischen Präfixe erforderlich.

  Die vorherige Beschränkung von einer VPN-Verbindung pro Infrastruktur wurde ebenfalls entfernt. Innerhalb derselben Infrastruktur werden jetzt mehrere Verbindungen unterstützt, und statische und BGP-Verbindungen können nebeneinander bestehen. Dadurch erhalten Netzwerk-Teams in Unternehmen mehr Flexibilität beim Entwerfen von VPN-Topologien für AEM Cloud Service-Umgebungen.

* **Verbesserte Build-Leistung mit Modul-Caching**
Ein neues Build-Modell kompiliert nur geänderte Module (und nicht das gesamte Repository) mithilfe des Caching auf Modulebene, um die Build-Leistung zu verbessern. Dies gilt für Produktions-Pipelines. Sie steuern, welche Produktions-Pipelines &quot;**Build“**.

  Weitere Informationen finden Sie in den folgenden Themen:

   * [Über die Verwendung von Smart Build in einer Produktions](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#about-smart-build)Pipeline und [Über die Verwendung von Smart Build in einer produktionsfremden Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#about-smart-build-non-production-pipeline)
   * [Produktions-Pipeline hinzufügen](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#full-stack-code) und [produktionsfremde Pipeline hinzufügen](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#configuring-non-production-pipelines).

* **Inhaltskopie: Programmübergreifender und Vorwärtsfluss**\
  Cloud Manager **Inhaltskopie** ermöglicht es Teams, Inhalte ohne Bereitstellung zwischen AEM-Umgebungen zu kopieren, und bietet zwei Funktionen, die für alle Programme verfügbar sind. Die programmübergreifende Unterstützung ermöglicht das Kopieren von Inhalten über verschiedene Cloud Manager-Programme hinweg, nicht nur innerhalb desselben Programms. Der Vorwärtsfluss entfernt die gerichtete Einschränkung, sodass Inhalte von jeder Umgebung in jede andere kopiert werden können - auch von niedrigeren Umgebungen nach oben.


## Beta-Programme {#private-beta-program}

Um vor der allgemeinen Veröffentlichung exklusiven Zugriff auf bevorstehende Funktionen zu erhalten, können Sie an den Beta-Programmen von Cloud Manager teilnehmen.

>[!IMPORTANT]
>
>Beta-Versionen enthalten Mängel und werden ohne Mängelgewähr und ohne Gewährleistung jeglicher Art bereitgestellt. Adobe ist nicht verpflichtet, die Beta-Versionen zu pflegen, zu korrigieren, zu aktualisieren, zu ändern oder anderweitig zu unterstützen. Kundinnen und Kunden verwenden Beta-Versionen auf eigenes Risiko. Verlassen Sie sich nicht auf die korrekte Funktionsweise oder Leistung von Beta-Versionen oder auf begleitende Dokumentationen oder Materialien. Funktionen und APIs in der Beta-Version können ohne Vorankündigung geändert werden. Jede Nutzung der Beta-Versionen erfolgt ausschließlich auf eigene Gefahr des Kunden.

Siehe auch [AEM Beta-Programme](/help/release-notes/release-notes-cloud/release-notes-current.md#aem-beta-programs)

Die folgenden Möglichkeiten des Beta-Programms sind derzeit verfügbar:

### Edge Delivery Services mit AEM-Authoring und flexibler Veröffentlichungsstufenkonfiguration {#eds-with-aem-authoring}

Cloud Manager führt zwei Funktionen ein, die moderne Bereitstellungsarchitekturen unterstützen.

* **Edge Delivery Services mit AEM-Authoring**
Sie können jetzt Sites mit Edge Delivery Services bereitstellen, während Sie weiterhin Inhalte im AEM-Autorenmodus erstellen. Je nach Ihren Workflow-Voreinstellungen können Sie aus den folgenden Authoring-Ansätzen wählen:

   * Dokumentenbasiertes Authoring
   * AEM-basiertes Authoring

Weitere Informationen finden Sie unter [Erstellen einer Edge Delivery-Site in Cloud Manager](/help/implementing/cloud-manager/edge-delivery/create-edge-delivery-site.md#one-click-edge-delivery-site).

* **Flexible Konfiguration der Veröffentlichungsebene**

Mit Cloud Manager können Sie jetzt konfigurieren, ob für Ihr Programm eine Veröffentlichungsebene erforderlich ist. Diese Flexibilität ermöglicht die Einrichtung von Umgebungen, die besser zu Ihrer gewählten Bereitstellungsarchitektur passen.

Weitere Informationen finden Sie unter [Flexible Veröffentlichungsebene (Beta)](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#flexible-publish-tier).

Um an der Beta teilzunehmen, senden Sie eine E-Mail an [](mailto:grp-beta_xwalk-publish_config@adobe.com)grp-beta_xwalk-publish_config@adobe.com) mit Ihrer Adobe Organisations-ID und Programm-ID.

<!-- 
OLD
### Improved build performance with module caching {#quick-build-cm-pipelines}

A new build model compiles only changed modules (rather than the entire repository) using module-level caching to improve build performance. It applies to production pipelines. You control which production pipelines use **Smart Build**.

For more information, see the following:

* [Using Smart Build in a production pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#about-smart-build).
* [Add a production pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#full-stack-code).

To join the Beta, email [beta_quickbuild_cmpipelines@adobe.com](mailto:beta_quickbuild_cmpipelines@adobe.com) with your Adobe Organization ID and Program ID.

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

* Kerngutschriften werden nicht freigegeben, wenn beide Produktgruppenumgebungen gleichzeitig einen Soft Delete abschließen. Dieses Problem wurde behoben. Credits werden jetzt korrekt freigegeben, unabhängig von der Reihenfolge, in der gleichzeitige Löschungen abgeschlossen sind. (CMGR-77845)

* Content Hub-Gutschrift verwaist nach Soft Delete der Umgebung, gefolgt von Harddelete. Cloud Manager gibt jetzt die Content Hub-Gutschrift korrekt frei, wenn die zugehörige Umgebung vollständig entfernt wurde. (CMGR-77585)

* aio CloudManager:tail-log CLI-Befehl trennt die Verbindung bei Protokollrotation, anstatt erneut eine Verbindung herzustellen. Der Befehl stellt jetzt automatisch eine neue Verbindung her, wenn eine Protokollrotation erkannt wird. (CMGR-76557)

* Vollständiger Dialogfeldinhalt für die Live-Schaltung kann in der Programmübersicht nicht gescrollt werden. Das Dialogfeld scrollt jetzt korrekt, um sicherzustellen, dass alle Inhalte unabhängig von der Bildschirmgröße zugänglich sind. (CMGR-76405)

* Die benutzerdefinierte Domain-Zuordnung schlägt in neu erstellten RDE-Umgebungen fehl. Nach der Erstellung einer neuen schnellen Entwicklungsumgebung (RDE) trat beim Versuch, unmittelbar nach der Bereitstellung eine benutzerdefinierte Domain-Zuordnung hinzuzufügen, der Fehler „Umgebungsstatus ist für Änderung der Domain-Konfiguration nicht gültig“ auf.Cloud Manager spiegelt nun den Bereitschaftsstatus der Umgebung korrekt wider, bevor eine Domain-Zuordnung versucht wird. (CMGR-75904)

* Das Löschen eines DV-Zertifikats und dessen Neuerstellung für dieselbe Domain schlägt mit dem Fehler „Vorhandenes Zertifikat“ fehl. Als Kundinnen und Kunden ein Domain-validiertes (DV) Zertifikat gelöscht und dann versucht haben, ein neues für dieselbe Domain zu erstellen, hat Cloud Manager den Fehler „Es gibt ein vorhandenes Zertifikat, das alle Domains abdeckt“ zurückgegeben. Infolgedessen wurde die Ausstellung des neuen Zertifikats blockiert. Die Löschung war in der Benutzeroberfläche offensichtlich erfolgreich, aber das Zertifikat wurde intern nicht vollständig entfernt, sodass die Domain gesperrt blieb. Dieses Problem wurde nun behoben. (CMGR-72784)

<!-- There are no significant bug fixes in the July 2026 Cloud Manager release. -->

<!-- ## Known issues {#known-issues} -->

