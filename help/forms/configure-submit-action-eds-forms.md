---
title: Wie wird eine Übermittlungsaktion für ein adaptives Formular konfiguriert?
description: Ein adaptives Formular bietet verschiedene Übermittlungsaktionen. Eine Übermittlungsaktion bestimmt die Verarbeitung eines adaptiven Formulars nach dem Senden. Sie können integrierte Übermittlungsaktionen verwenden oder eigene erstellen.
keywords: Anleitung zum Auswählen einer Übermittlungsaktion für ein adaptives Formular, Verbinden eines adaptiven Formulars mit einer SharePoint-Liste, Verbinden eines adaptiven Formulars mit einer SharePoint-Dokumentbibliothek, Verbinden eines adaptiven Formulars mit einem Formulardatenmodell (FDM)
feature: Adaptive Forms, Edge Delivery Services
role: User, Developer
badgeSaas: label="AEM Forms" type="Positive" tooltip="Gilt für AEM Forms)."
exl-id: 3f8950c3-9022-4e9f-b3ed-723245201e45
source-git-commit: 89b0f2a8ca9d2f60365a5c3962b0b4e826f79b3e
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 66%

---

# Übermittlungsaktionen für Edge Delivery Services Forms

| Version | Artikel-Link |
|---------|-----------------------------|
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/forms/adaptive-forms-basic-authoring/configuring-submit-actions) |
| AEM as a Cloud Service (Foundation-Komponenten) | [Hier klicken](/help/forms/configuring-submit-actions.md) |
| AEM as a Cloud Service (Kernkomponenten) | [Hier klicken](/help/forms/configure-submit-actions-core-components.md) |
| AEM as a Cloud Service (Edge Delivery Services) | Dieser Artikel |

Übermittlungsaktionen definieren, was passiert, wenn ein Benutzer ein Formular übermittelt, z. B. Daten speichert, Workflows auslöst oder mit Drittanbietersystemen integriert. Der Typ der Übermittlungsaktionen, die Sie konfigurieren können, hängt von der Authoring-Methode ab, die zum Erstellen von Edge Delivery Services Forms verwendet wurde.

Sie können Edge Delivery Services Forms entweder mit dem [universellen Editor](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) oder mit der [dokumentbasierten Forms](/help/edge/docs/forms/overview.md)-Bearbeitung erstellen und die Formulare mit verschiedenen Übermittlungsaktionen entsprechend konfigurieren.

## Übermittlungsaktionen für Forms, die im universellen Editor erstellt wurden

Die folgenden Übermittlungsaktionen werden von[im universellen Editor verfassten adaptiven Formularen](/help/edge/docs/forms/universal-editor/create-forms.md) unterstützt:

* [E-Mail senden](/help/forms/configure-submit-action-send-email.md)
* [Power Automate-Fluss aufrufen](/help/forms/forms-microsoft-power-automate-integration.md)
* [An SharePoint senden](/help/forms/configure-submit-action-sharepoint.md)
* [Workfront Fusion aufrufen](/help/forms/submit-adaptive-form-to-workfront-fusion.md)
* [Senden mit Formulardatenmodell (FDM)](/help/forms/integrate-adaptive-form-with-fdm.md)
* [An Azure Blob Storage senden](/help/forms/configure-submit-action-azure-blob-storage.md)
* [An REST-Endpunkt senden](/help/forms/configure-submit-action-restpoint.md)
* [An OneDrive senden](/help/forms/configure-submit-action-onedrive.md)
* [Aufrufen eines AEM-Workflows](/help/forms/configure-submit-action-workflow.md)
* [An Marketo Engage senden](/help/forms/submit-adaptive-form-to-marketo-engage.md)
* [An Adobe Experience Platform (AEP) senden](/help/forms/aem-forms-aep-connector.md)
* [An Tabelle senden](/help/forms/forms-submission-service.md)

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
> * Wenn das Symbol **Formulareigenschaften bearbeiten** in der Benutzeroberfläche des universellen Editors nicht angezeigt wird, aktivieren Sie die Erweiterung **Formulareigenschaften bearbeiten** im Extension Manager.
> * Informationen zum Aktivieren und Deaktivieren von Erweiterungen im universellen Editor finden Sie im Artikel [Extension Manager – Highlights der Funktionen](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions).

## Übermittlungsaktionen für dokumentbasierte Forms

Dokumentbasierte Forms-Unterstützung nur für die Übermittlung an Tabellen. Informationen dazu, wie Sie Ihre Kalkulationstabelle für den Empfang gesendeter Daten einrichten, finden Sie in den Anweisungen im Artikel [Einrichten von Google Sheets oder Microsoft Excel-Dateien, um mit dem Akzeptieren von Daten ](/help/edge/docs/forms/submit-forms.md) beginnen“.

## Siehe auch {#see-also}

{{af-submit-action}}
