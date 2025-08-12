---
title: Konfigurieren einer Übermittlungsaktion für ein adaptives Formular
description: Ein adaptives Formular bietet verschiedene Übermittlungsaktionen. Eine Übermittlungsaktion bestimmt die Verarbeitung eines adaptiven Formulars nach dem Senden. Sie können integrierte Übermittlungsaktionen verwenden oder eigene erstellen.
keywords: Auswählen einer Übermittlungsaktion für ein adaptives Formular, Verbinden eines adaptiven Formulars mit einer SharePoint-Liste, Verbinden eines adaptiven Formulars mit einer SharePoint-Dokumentbibliothek und Verbinden eines adaptiven Formulars mit einem Formulardatenmodell (FDM)
feature: Adaptive Forms, Edge Delivery Services
role: User, Developer
exl-id: beee9be7-8215-496b-9fb9-61fba000a055
source-git-commit: bf35f847f6f00d21915dfedb10cf38ea74344988
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 63%

---

# Übermittlungsaktion für adaptive Formulare

| Version | Link zum Artikel |
|---------|-----------------------------|
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/forms/adaptive-forms-basic-authoring/configuring-submit-actions) |
| AEM as a Cloud Service (Foundation-Komponenten) | [Hier klicken](/help/forms/configuring-submit-actions.md) |
| AEM as a Cloud Service (Kernkomponenten) | [Hier klicken](/help/forms/configure-submit-actions-core-components.md) |
| AEM as a Cloud Service (Edge Delivery Services) | Dieser Artikel |


Die Formularübermittlung ist der wichtige letzte Schritt der Benutzer-Journey. Dort werden die erfassten Daten verarbeitet und Aktionen durchgeführt. Dieses Dokument enthält eine umfassende Anleitung zum Konfigurieren und Verwalten von Übermittlungsaktionen für adaptive Formulare im universellen Editor.

## Lerninhalte

Am Ende dieses Dokuments werden Sie Folgendes beherrschen:

- Konfigurieren verschiedener Arten von Übermittlungsaktionen für Ihre Formulare
- Einrichten von REST-Endpunktübermittlungen für die Integration mit externen Systemen
- Konfigurieren von E-Mail-Sendungen für Formularantworten
- Implementieren benutzerdefinierter Übermittlungsaktionen für bestimmte Unternehmensanforderungen
- Bearbeitung der Formularvalidierung und Fehlerszenarien bei der Übermittlung

## Zielgruppe

Dieses Handbuch wurde für folgende Rollen entwickelt:

- **Formularentwicklerinnen und -entwickler**, die Übermittlungslogik implementieren
- **Systemintegratorinnen und -integratoren**, die Formulare mit Backend-Systemen verknüpfen
- **Geschäftsanalystinnen und -analysten**, die Formular-Workflows definieren
- **Technische Architektinnen und Architekten**, die Formularübermittlungsprozesse erstellen

## Übermittlungsaktionen für Forms, die im universellen Editor erstellt wurden

Die folgenden Übermittlungsaktionen werden von [im universellen Editor verfassten adaptiven Forms&quot; unterstützt](/help/edge/docs/forms/universal-editor/create-forms.md):

- [E-Mail senden](/help/forms/configure-submit-action-send-email.md)
- [Power Automate-Fluss aufrufen](/help/forms/forms-microsoft-power-automate-integration.md)
- [An SharePoint senden](/help/forms/configure-submit-action-sharepoint.md)
- [Aufrufen von Workfront Fusion](/help/forms/submit-adaptive-form-to-workfront-fusion.md)
- [Senden mit Formulardatenmodell (FDM)](/help/forms/integrate-adaptive-form-with-fdm.md)
- [An Azure Blob Storage senden](/help/forms/configure-submit-action-azure-blob-storage.md)
- [An REST-Endpunkt übermitteln](/help/forms/configure-submit-action-restpoint.md)
- [An OneDrive senden](/help/forms/configure-submit-action-onedrive.md)
- [Aufrufen eines AEM-Workflows](/help/forms/configure-submit-action-workflow.md)
- [An Marketo Engage senden](/help/forms/submit-adaptive-form-to-marketo-engage.md)
- [An Adobe Experience Platform (AEP) senden](/help/forms/aem-forms-aep-connector.md)
- [An Arbeitsblatt übermitteln](/help/forms/forms-submission-service.md)

<!--You can also submit an Adaptive Form in the Universal Editor to other storage or CRM integrations:

* [Connect Adaptive Form to Salesforce](/help/forms/aem-forms-salesforce-integration.md)
* [Connect an Adaptive Form to Microsoft&reg; Dynamics OData](/help/forms/ms-dynamics-odata-configuration.md)-->

Sie können die Übermittlungsaktion für Formulare, die im universellen Editor erstellt wurden, über die Registerkarte **Übermittlung** der Erweiterung **Formulareigenschaften bearbeiten** konfigurieren.

**Wie wird die Übermittlungsaktion für Forms konfiguriert, das im universellen Editor erstellt wurde?**
Sie können die Übermittlungsaktion für Formulare, die im universellen Editor erstellt wurden, über die Registerkarte **Übermittlung** der Erweiterung **Formulareigenschaften bearbeiten** konfigurieren.

![Symbol für Formulareigenschaften](/help/forms/assets/ue-form-properties-icon.png)

![Formulareigenschaften des universellen Editors](/help/forms/assets/ue-form-properties.png)

>[!NOTE]
>
> - Wenn das Symbol **Formulareigenschaften bearbeiten** in der Benutzeroberfläche des universellen Editors nicht angezeigt wird, aktivieren Sie die Erweiterung **Formulareigenschaften bearbeiten** im Extension Manager.
> - Informationen zum Aktivieren und Deaktivieren von Erweiterungen im universellen Editor finden Sie im Artikel [Extension Manager – Highlights der Funktionen](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions).
