---
title: Konfigurieren einer Übermittlungsaktion für ein adaptives Formular
description: Ein adaptives Formular bietet verschiedene Übermittlungsaktionen. Eine Übermittlungsaktion bestimmt die Verarbeitung eines adaptiven Formulars nach dem Senden. Sie können integrierte Übermittlungsaktionen verwenden oder eigene erstellen.
keywords: Auswählen einer Übermittlungsaktion für ein adaptives Formular, Verbinden eines adaptiven Formulars mit einer SharePoint-Liste, Verbinden eines adaptiven Formulars mit einer SharePoint-Dokumentbibliothek und Verbinden eines adaptiven Formulars mit einem Formulardatenmodell (FDM)
feature: Adaptive Forms, Edge Delivery Services
role: User, Developer
source-git-commit: c0df3c6eaf4e3530cca04157e1a5810ebf5b4055
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 22%

---


# Übermittlungsaktionen für Edge Delivery Services Forms

| Version | Link zum Artikel |
|---------|-----------------------------|
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/configuring-submit-actions.html?lang=de) |
| AEM as a Cloud Service (Foundation-Komponenten) | [Hier klicken](/help/forms/configuring-submit-actions.md) |
| AEM as a Cloud Service (Kernkomponenten) | [Hier klicken](/help/forms/configure-submit-actions-core-components.md) |
| AEM as a Cloud Service (Edge Delivery Services) | Dieser Artikel |

Übermittlungsaktionen definieren, was passiert, wenn ein Benutzer ein Formular übermittelt, z. B. Daten speichert, Workflows auslöst oder mit Drittanbietersystemen integriert. Der Typ der Übermittlungsaktionen, die Sie konfigurieren können, hängt von der Authoring-Methode ab, die zum Erstellen von Edge Delivery Services Forms verwendet wurde.

Sie können Edge Delivery Services Forms entweder mit dem [universellen Editor](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) oder mit der [dokumentbasierten Forms](/help/edge/docs/forms/overview.md)-Bearbeitung erstellen und die Formulare mit verschiedenen Übermittlungsaktionen entsprechend konfigurieren.

## Übermittlungsaktionen für Forms, die im universellen Editor erstellt wurden

Die folgenden Übermittlungsaktionen werden von [im universellen Editor verfassten adaptiven Forms&quot; unterstützt](/help/edge/docs/forms/universal-editor/create-forms.md):

* [E-Mail senden](/help/forms/configure-submit-action-send-email.md)
* [Power Automate-Fluss aufrufen](/help/forms/forms-microsoft-power-automate-integration.md)
* [An SharePoint senden](/help/forms/configure-submit-action-sharepoint.md)
* [Aufrufen von Workfront Fusion](/help/forms/submit-adaptive-form-to-workfront-fusion.md)
* [Senden mit Formulardatenmodell (FDM)](/help/forms/using-form-data-model.md)
* [An Azure Blob Storage senden](/help/forms/configure-submit-action-azure-blob-storage.md)
* [An REST-Endpunkt übermitteln](/help/forms/configure-submit-action-restpoint.md)
* [An OneDrive senden](/help/forms/configure-submit-action-onedrive.md)
* [Aufrufen eines AEM-Workflows](/help/forms/configure-submit-action-workflow.md)
* [An Marketo Engage senden](/help/forms/submit-adaptive-form-to-marketo-engage.md)
* [An Adobe Experience Platform (AEP) senden](/help/forms/aem-forms-aep-connector.md)
* [An Arbeitsblatt übermitteln](/help/forms/forms-submission-service.md)

<!--You can also submit an Adaptive Form in the Universal Editor to other storage or CRM integrations:

* [Connect Adaptive Form to Salesforce](/help/forms/aem-forms-salesforce-integration.md)
* [Connect an Adaptive Form to Microsoft&reg; Dynamics OData](/help/forms/ms-dynamics-odata-configuration.md)-->

Sie können die Übermittlungsaktion für Formulare, die im universellen Editor erstellt wurden, über die Registerkarte **Übermittlung** der Erweiterung **Formulareigenschaften bearbeiten** konfigurieren.

<!--**How to Configure Submit Action for Forms authored in Universal Editor?**
You can configure the submit action for forms created in the Universal Editor using the **Submission** tab of the **Edit Form Properties** extension.

![Form properties icon](/help/forms/assets/ue-form-properties-icon.png)

![Universal Editor Form Properties](/help/forms/assets/ue-form-properties.png)-->

>[!NOTE]
>
> * Wenn das Symbol **Formulareigenschaften bearbeiten** in der Benutzeroberfläche des universellen Editors nicht angezeigt wird, aktivieren Sie die Erweiterung **Formulareigenschaften bearbeiten** in der Extension Manager.
> * Informationen zum Aktivieren oder Deaktivieren von Erweiterungen im universellen Editor finden [ im Artikel ](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions)Extension Manager-Feature-Highlights&rbrace;.

## Übermittlungsaktionen für dokumentbasierte Forms

Dokumentbasierte Forms-Unterstützung nur für die Übermittlung an Tabellen. Informationen dazu, wie Sie Ihre Kalkulationstabelle für den Empfang gesendeter Daten einrichten, finden Sie in den Anweisungen im Artikel [Einrichten von Google Sheets oder Microsoft Excel-Dateien, um mit dem Akzeptieren von Daten ](/help/edge/docs/forms/submit-forms.md) beginnen“.

## Siehe auch {#see-also}

{{af-submit-action}}

