---
title: Versionshinweise für Cloud Manager 2026.6.0
description: Erfahren Sie mehr über die Version Cloud Manager 2026.6.0 in Adobe Experience Manager as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: 3c78dbcbc453eaaaab3904b83f22744eef60080c
workflow-type: tm+mt
source-wordcount: '726'
ht-degree: 4%

---

# Versionshinweise für Cloud Manager 2026.6.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

Erfahren Sie mehr über die Version Cloud Manager 2026.6.0 in AEM (Adobe Experience Manager) as a Cloud Service.

Hier finden Sie die [aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Veröffentlichungsdaten {#release-date}

Cloud Manager 2026.6.0 wurde in AEM as a Cloud Service am Donnerstag, 4. Juni 2026 veröffentlicht.

Die nächste geplante Version ist Donnerstag, der 9. Juli 2026.


## Neue Funktionen - Cloud Manager {#cloud-manager-whats-new}

* **Self-Service für kundenverwaltete Schlüssel (CMK)**
Kunden können jetzt kundenverwaltete Schlüssel direkt in Cloud Manager konfigurieren, ohne dass der Adobe-Support einbezogen werden muss. Eine neue CMK-Option ist während der Programmerstellung in den Einstellungen zur Programmbearbeitung und auf der Seite „Umgebungsdetails“ verfügbar.

  Der CMK-Status wird auf den Karten Meine Programme und im Lizenz-Dashboard angezeigt, sodass Administratoren einen klaren Einblick in die Verschlüsselungskonfiguration in allen Umgebungen erhalten. Dieser Ansatz vereinfacht Compliance-Workflows für Unternehmen, die die Kontrolle über ihre eigenen Verschlüsselungsschlüssel benötigen.

  ![Karte „Meine Programme“ mit dem Symbol „Kundenverwalteter Schlüssel“](/help/implementing/cloud-manager/release-notes/assets/cmk-status-on-program-card.png)
  *Meine Programmkarte*

  ![Dialogfeld „Für Produktion einrichten“ mit ausgewählter Option „Kundenseitig verwaltete Schlüssel“ auf der Registerkarte „Sicherheit“](/help/implementing/cloud-manager/release-notes/assets/cmk-security-tab-in-set-up-for-production-dlg.png)
  *Vom Kunden verwaltete Schlüssel auf der Registerkarte „Sicherheit“ im Dialogfeld „Für Produktion einrichten“ ausgewählt*

  ![Anzeige der Anzahl der im Lizenz-Dashboard verfügbaren kundenverwalteten Schlüssel](/help/implementing/cloud-manager/release-notes/assets/cmk-license-dashboard.png)
  *Anzeige der Anzahl der im Lizenz-Dashboard verfügbaren kundenverwalteten Schlüssel*

* **Umgebungsvariablenlimit wurde auf 400 erhöht**
Cloud Manager unterstützt jetzt bis zu 400 Umgebungsvariablen pro Umgebung, doppelt so viel wie zuvor (200).

  Pipeline-Variablen bleiben auf 200 begrenzt. Die Benutzeroberfläche erzwingt die richtige Begrenzung pro Kontext und verhindert Ergänzungen über den zulässigen Schwellenwert hinaus.

  Durch diese Änderung werden Kunden mit komplexeren Bereitstellungskonfigurationen unterstützt, für die eine größere Anzahl umgebungsspezifischer Einstellungen erforderlich ist.

<!--CMGR-76755 · CMGR-76753 -->


## Beta-Programme {#private-beta-program}

Um vor der allgemeinen Veröffentlichung exklusiven Zugriff auf bevorstehende Funktionen zu erhalten, können Sie an den Beta-Programmen von Cloud Manager teilnehmen.

>[!IMPORTANT]
>
>Beta-Versionen enthalten Mängel und werden ohne Mängelgewähr und ohne Gewährleistung jeglicher Art bereitgestellt. Adobe ist nicht verpflichtet, die Beta-Versionen zu pflegen, zu korrigieren, zu aktualisieren, zu ändern oder anderweitig zu unterstützen. Kundinnen und Kunden verwenden Beta-Versionen auf eigenes Risiko und sollten sich nicht auf die korrekte Funktionsweise oder Leistung von Beta-Versionen oder auf begleitende Dokumentationen oder Materialien verlassen. Funktionen und APIs in der Beta-Version können ohne Vorankündigung geändert werden. Jede Nutzung der Beta-Versionen erfolgt ausschließlich auf eigene Gefahr des Kunden.

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

Um sich der Beta anzuschließen, senden Sie eine E-Mail an [](mailto:grp-beta_xwalk-publish_config@adobe.com)grp-beta_xwalk-publish_config@adobe.com) mit Ihrer Adobe Organisations-ID und Programm-ID.

### Schnellere Builds mit Modul-Caching {#quick-build-cm-pipelines}

Ein neues Build-Modell kompiliert nur geänderte Module (und nicht das gesamte Repository) mithilfe des Caching auf Modulebene, um die Build-Leistung zu verbessern. Dies gilt für Produktions-Pipelines. Sie steuern, welche Produktions-Pipelines &quot;**Build“**.

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

* **Umgebung bleibt beim Aktualisieren ohne aktiven Vorgang hängen**
Es wurde ein Problem behoben, bei dem Umgebungen dauerhaft in einem Aktualisierungsstatus feststecken, selbst wenn keine Pipeline-Ausführung oder Konfigurationsänderung ausgeführt wird. Betroffene Umgebungen können jetzt normal verwaltet werden, ohne dass der Adobe-Support manuell eingreifen muss. (CMGR-77133)
* **Erweiterte Netzwerke - Falsche Regel für die Port-Weiterleitung an doppelten Quell-Ports gelöscht**
Wenn zwei Regeln für die Port-Weiterleitung im erweiterten Netzwerk denselben Quell-Port (portOrg) verwenden, wird beim Löschen einer Regel fälschlicherweise die andere entfernt. Cloud Manager identifiziert und entfernt jetzt korrekt nur die beabsichtigte Regel. (CMGR-77019)

<!-- There are no significant bug fixes in the June 2026 Cloud Manager release. -->

<!-- ## Known issues {#known-issues} -->

