---
title: Versionshinweise für Cloud Manager 2026.3.0
description: Erfahren Sie mehr über Version 2026.3.0 von Cloud Manager in Adobe Experience Manager as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: eb3e826e27e14b8b1da534440f11d43e973130ec
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 23%

---

# Versionshinweise für Cloud Manager 2026.3.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

<!-- https://wiki.corp.adobe.com/display/DMSArchitecture/%5BKT%5D+Cloud+Manager+2025.08.0+Release -->

Erfahren Sie mehr über Version 2026.3.0 von Cloud Manager in AEM (Adobe Experience Manager) as a Cloud Service.

Hier finden Sie die [aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Veröffentlichungsdaten {#release-date}

Die Version 2026.3.0 von Cloud Manager in AEM as a Cloud Service wurde am Donnerstag, dem Freitag, 5. März 2026 veröffentlicht.

Die Veröffentlichung der nächsten Version ist für Donnerstag, den Freitag, 2. April 2026 geplant.


## Neue Funktionen - Cloud Manager {#cloud-manager-whats-new}

* **Cloud Manager unterstützt jetzt eine Option** Löschen **für** Inhaltskopie **-Importe**

  Wenn Sie **Löschen** aktivieren, löscht Cloud Manager den vorhandenen Inhalt am Ziel, bevor Sie mit dem Import beginnen, sodass Sie von vorne anfangen und Konflikte mit bereits vorhandenen Inhalten vermeiden können. Wenn Sie **Löschen** deaktiviert lassen, importiert Cloud Manager den neuen Inhalt zusätzlich zum vorhandenen Zielinhalt. Bevor das Löschen beginnt, wird eine Bestätigungsaufforderung angezeigt, und Cloud Manager protokolliert die Löschaktion und Importdetails, um die Rückverfolgbarkeit zu gewährleisten.

  Siehe auch [Inhalt kopieren](/help/implementing/developing/tools/content-copy.md#copy-content).

* **Unterstützung der Erweiterbarkeit der Benutzeroberfläche in AEM Experience Hub**
Die Unterstützung für Benutzeroberflächenerweiterungen in [AEM Experience Hub](https://experience.adobe.com/experiencemanager) ist jetzt aktiviert, sodass Entwicklerinnen und Entwickler die Benutzeroberfläche mit benutzerdefinierten Funktionen und Widgets erweitern können, die mit Adobe App Builder erstellt wurden.

  Weitere Informationen finden Sie unter [AEM Experience Hub](https://developer.adobe.com/uix/docs/services/aem-experience-hub/).

* **Verbesserte Stabilität, Leistung und Zuverlässigkeit**

  Diese Version umfasst Optimierungs- und Wartungsaktualisierungen, die die Stabilität, Leistung und Zuverlässigkeit von Cloud Manager verbessert haben.


## Beta-Programme {#private-beta-program}

Nehmen Sie am Beta-Programm von Cloud Manager teil, um exklusiven Zugriff auf bevorstehende Funktionen vor ihrer regulären Veröffentlichung zu erhalten.

>[!IMPORTANT]
>
>Beta-Versionen können Mängel enthalten und werden „wie besehen“ ohne Gewährleistung jeglicher Art bereitgestellt. Adobe ist nicht verpflichtet, die Beta-Versionen zu pflegen, zu korrigieren, zu aktualisieren, zu ändern oder anderweitig zu unterstützen (durch Adobe Support Services oder anderweitig). Adobe empfiehlt Kunden, Vorsicht walten zu lassen und sich nicht auf die ordnungsgemäße Funktionsweise oder Leistung von Beta-Versionen oder auf begleitende Dokumentationen oder Materialien zu verlassen. Funktionen und APIs in der Beta-Version können ohne Vorankündigung geändert werden. Jede Nutzung der Beta-Versionen erfolgt daher ausschließlich auf eigene Gefahr des Kunden.

Siehe auch [AEM Beta-Programme](/help/release-notes/release-notes-cloud/release-notes-current.md#aem-beta-programs)

Derzeit stehen die folgenden Möglichkeiten zur Verfügung:
<!--
### Support for Custom Author Domains in Cloud Service

AEM Cloud Service is going to soon support one custom domain per Author environment.-->

### Cloud Manager MCP-Server für KI-gestützte IDEs{#mcp-server-for-cm}

Sie können jetzt einen MCP-Server (Model Context Protocol) ausprobieren, der öffentliche Cloud Manager-APIs als Tools für KI-aktivierte IDEs (z. B. Cursor) verfügbar macht. Nach dem Verbinden können Sie Konversationsaufforderungen verwenden, um Programme, Pipelines, Umgebungen und Repositorys aufzulisten und zu verwalten, sodass Sie schneller arbeiten können, ohne den Editor zu verlassen.

Siehe die Dokumentation [Verwenden von MCP mit AEM as a Cloud Service](/help/ai-in-aem/mcp-support/using-mcp-with-aem-as-a-cloud-service.md).

Siehe das Tutorial [Cloud Manager MCP Server](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/ai/mcp-server/cloud-manager#).

Sie interessieren sich für die Beta-Version? Senden Sie eine E-Mail an [0}GRP-AEM-CM-MCP-FEEDBACK@adobe.com&quot; mit Ihrer Adobe-OrgID und Programm-ID.](mailto:GRP-AEM-CM-MCP-FEEDBACK@adobe.com)


<!--
### Experience Hub Extensibility and Customization {#exp-hub-extensibility}

[Experience Hub](/help/experience-hub.md) serves as your entry point to AEM, customized for your organization's needs. Tell Adobe about your existing AEM UI Extensions so they can help you enable them in Experience Hub with minimal effort.

![Diagram of Experience Hub extensibility and customization workflow](/help/implementing/cloud-manager/release-notes/assets/experience-hub-extensibility-customization.png)

Embed custom experiences in Experience Hub to extend and personalize your organization's dashboard. In addition to Adobe's built-in widgets, add your own using the [UI Extensibility](https://developer.adobe.com/uix/docs/) framework. Build JavaScript-based UI apps and surface them to your users to meet business-specific requirements and workflows. 

Interested in the beta? Email [beta_exphubextensibility@adobe.com](mailto:beta_exphubextensibility@adobe.com) with your Adobe OrgID and a short description of the customization you intend to create.
-->

### Schnellere Builds mit Modul-Caching {#quick-build-cm-pipelines}

Ein neues Build-Modell kompiliert nur geänderte Module (nicht das gesamte Repository) mithilfe des Caching auf Modulebene, um die Erstellungszeiten zu verkürzen. Es kann für Code-Qualitäts-, Full-Stack- und reine Staging-Pipelines angewendet werden.

![Dialogfeld „Produktionsfremde Pipeline bearbeiten“ mit den beiden Optionen für die Build-Strategie „Vollständiger Build“ und „Intelligenter Build“](/help/implementing/cloud-manager/release-notes/assets/non-production-pipeline-edit.png)
*Dialogfeld „Produktionsfremde Pipeline bearbeiten“ mit den beiden Optionen für die Build-Strategie „Vollständiger Build“ und „Intelligenter Build“.*

Im Dialogfeld **Pipeline hinzufügen/bearbeiten** auf der Registerkarte **Source-Code** können Sie mit dem Abschnitt **Erstellen-Strategie** eine der folgenden Build-Optionen auswählen:

* **Vollständiger Build** - Erstellt bei jeder Ausführung alle Module im Repository.
* **Smarter Build** - Erstellt nur Module, die seit dem letzten Commit geändert wurden, was die Erstellungszeit insgesamt verkürzt.

Sie steuern, welche Pipelines „Smart **Build“**. Während der Beta-Phase wird diese Option nur für Pipelines **Code-Qualität** und **Bereitstellung durch Entwicklung** angezeigt.

Sie sind interessiert? Senden Sie eine E-Mail an [beta_quickbuild_cmpipelines@adobe.com](mailto:beta_quickbuild_cmpipelines@adobe.com) mit Ihrer Adobe-OrgID und Programm-ID.

<!-- You can deactivate incremental builds at the pipeline level by setting the property `CM_BUILD_DISABLE_MODULE_CACHING` to `true` (effective during the `BUILD` step). For how to add pipeline variables, see [Pipeline Variables in Cloud Manager](/help/implementing/cloud-manager/configuring-pipelines/pipeline-variables.md).-->

## Fehlerbehebungen {#bug-fixes}

* Es wurde ein Problem behoben, bei dem die Wiederherstellungspunkte-API beim Abrufen von Wiederherstellungspunkten einen 500-Fehler zurückgeben konnte. Der Endpunkt verarbeitet jetzt Nullwerte korrekt, was konsistente und zuverlässige Antworten gewährleistet. (CMGR-72963)
* Cloud Manager akzeptiert jetzt GitHub-Repository-URLs mit oder ohne `.git` Suffix, ordnet das API-Verhalten an der Benutzeroberfläche an und macht das Repository-Onboarding flexibler. (CMGR-73296)
* Bei der Namensvalidierung von Produktprofilen wird jetzt nicht mehr zwischen Groß- und Kleinschreibung unterschieden. Dadurch werden Fehler beim Erstellen von Profilen mit Namen verhindert, die sich nur durch die Groß-/Kleinschreibung unterscheiden. (CMGR-74075)
* Sie können jetzt mehrere Wiederherstellungsvorgänge von derselben Pipeline-Ausführung aus durchführen, was sequenzielle Wiederherstellungen für Umgebungen wie Staging und Produktion ermöglicht, ohne dass eine neue Pipeline ausgeführt werden muss. (CMGR-73538)


<!-- ## Known issues {#known-issues} -->

