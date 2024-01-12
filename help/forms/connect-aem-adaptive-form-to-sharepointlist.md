---
title: Verbinden eines adaptiven AEM-Formulars mit der Microsoft® SharePoint-Liste?
description: Verbinden Sie ein adaptives Formular mit der Microsoft® SharePoint-Liste.  Erfahren Sie, wie Sie die Microsoft® SharePoint-Liste konfigurieren und ein Formulardatenmodell mithilfe der Konfiguration erstellen. Erfahren Sie zudem, wie Sie das FDM in Ihr adaptives Formular integrieren.
role: User, Developer
keywords: Verbinden des adaptiven AEM-Formulars mit der Microsoft SharePoint-Liste, Verbinden des adaptiven Formulars mit der Microsoft SharePoint-Liste, Integrieren des adaptiven AEM-Formulars in die Microsoft SharePoint-Liste, Integrieren des adaptiven Formulars in Microsoft SharePoint-Liste, Senden von Daten aus einem adaptiven Formular an die SharePoint-Liste, Senden des AEM-Workflows an die SharePoint-Liste.
hide: true
hidefromToC: true
source-git-commit: e2505c0fec1da8395930f131bfc55e1e2ce05881
workflow-type: ht
source-wordcount: '539'
ht-degree: 100%

---


# Verbinden eines adaptiven Formulars mit der Microsoft® SharePoint-Liste

<span class="preview"> Dies ist eine Vorabveröffentlichungsfunktion, auf die über unseren [Vorabveröffentlichungskanal](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=de#new-features) zugegriffen werden kann. </span>

**Microsoft® SharePoint**: Microsoft® SharePoint ermöglicht die Zusammenarbeit durch die Bereitstellung dynamischer und effizienter Teamsites für alle Teams, Bereiche und Abteilungen. Es wird verwendet, um Informationen von jedem Gerät mithilfe eines beliebigen Webbrowsers wie Microsoft® Edge, Internet Explorer, Chrome oder Firefox zu speichern, zu organisieren, freizugeben und darauf zuzugreifen. Die beiden Hauptkomponenten von **Microsoft® SharePoint** sind:

* **Microsoft® SharePoint-Dokumentbibliothek**: Die Microsoft® SharePoint-Dokumentbibliothek zeigt eine Liste von Dateien und Ordnern mit ihren Schlüsselinformationen an, z. B. das Datum der letzten Änderung und die Eigentümer bzw. den Eigentümer einer Datei. Diese Funktion erleichtert die Organisation von und die Navigation in Dateien.
Anweisungen zur Integration einer **Microsoft® SharePoint-Dokumentbibliothek** mit einem adaptiven Formular finden Sie im Artikel [Übermittlungsaktion für adaptive Formulare](/help/forms/configuring-submit-actions.md#submit-to-sharepoint).

* **Microsoft® SharePoint-Liste**: Die Microsoft® SharePoint-Liste ist eine Sammlung von Daten.  Sie können Spalten für verschiedene Datentypen hinzufügen und Ansichten für eine effektive Datenanzeige erstellen. Sie können Listen ganz einfach gruppieren, filtern, sortieren und formatieren.

>[!VIDEO](https://video.tv.adobe.com/v/3424820/connect-aem-adaptive-form-to-sharepointlist/?quality=12&learn=on)

## Voraussetzungen für das Verbinden eines adaptiven Formulars mit der Microsoft® SharePoint-Liste {#prerequisites}

Führen Sie die folgenden Schritte aus, bevor Sie ein adaptives Formular mit der Microsoft® SharePoint-Liste verbinden:

1. [Konfigurieren von Microsoft](/help/forms/configure-data-sources.md#configure-microsoft-sharepoint-list)
1. [Erstellen eines Formulardatenmodells mithilfe von Microsoft](/help/forms/create-form-data-models.md)
1. [Konfigurieren des Formulardatenmodells zum Abrufen und Senden von Daten](/help/forms/work-with-form-data-model.md#configure-services)
1. [Erstellen eines adaptiven Formulars](/help/forms/creating-adaptive-form-core-components.md)

Jetzt haben Sie folgende Möglichkeiten:

* [Verbinden von Microsoft](#connect-an-adaptive-form-to-microsoft-sharepoint-list-connect-af-sharepoint-list)
* [Verbinden von Microsoft](#connect-sharepoint-list-workflow)

## Verbinden eines adaptiven Formulars mit der Microsoft® SharePoint-Liste {#connect-af-sharepoint-list}

[Konfigurieren eines adaptiven Formulars zur Verwendung eines Formulardatenmodells](/help/forms/creating-adaptive-form-core-components.md#configure-a-schema-or-form-data-model-for-an-adaptive-formconfigure-schema-or-data-model-for-form) zum Integrieren der Microsoft® SharePoint-Liste in Ihr adaptives Formular

Nach der Konfiguration eines adaptiven Formulars für die Verwendung eines Formulardatenmodells haben Sie folgende Möglichkeiten:

* [Konfigurieren einer Übermittlungsaktion mit einem Formulardatenmodell](/help/forms/configuring-submit-actions.md#submit-using-form-data-model)
* [Konfigurieren des Regeleditors zum Aufrufen eines Formulardatenmodells](/help/forms/rule-editor.md#invoke-form-data-model-service-invoke)

## Verbinden der Microsoft® SharePoint-Liste mit einem AEM-Workflow {#connect-sharepoint-list-workflow}

Integrieren der Microsoft® SharePoint-Liste in einen AEM-Workflow:

1. [Erstellen eines Workflows zum Aufrufen eines Formulardatenmodells](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=de)

   <!--
    To create a workflow with the editor:
    1.  Go to your **AEM Forms Author** instance > **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
    1.  Click **[!UICONTROL Create]** > **[!UICONTROL Create Model]**. The Add Workflow Model dialog appears. 
    1. Specify **[!UICONTROL Title]** and **[!UICONTROL Name (optional)]**.
    1. Click **[!UICONTROL Done]**. The new model is listed in the Workflow Models console.
    1. Select your new workflow, then use **[!UICONTROL Edit]** to open it for configuration.
    1. Add **[!UICONTROL Invoke Form Data Model Service]** step to your workflow.
    1. Confirm the changes with Sync (editor toolbar) to generate the runtime model.
    -->

1. [Konfigurieren der Übermittlungsaktion zum Aufrufen eines AEM-Workflows](/help/forms/configuring-submit-actions.md#invoke-an-aem-workflow)


Erfahren Sie, wie Sie einen [AEM-Workflow verwenden](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/workflow/use-workflow.html?lang=de), um zusammenzuarbeiten und Inhalte in einem adaptiven Formular zu verwalten und zu verarbeiten.

## Best Practices {#best-practices}

<!-- * For storing data in a tabular format or implementing data permissions, it is advisable to use Microsoft&reg; SharePoint List rather than Microsoft&reg; SharePoint Document Library. -->
* Die folgenden Spaltentypen werden in der Microsoft® SharePoint-Liste nicht unterstützt:
   * Bildspalte
   * Metadatenspalte
   * Personenspalte
   * Externe Datenspalte

## Siehe auch {#see-also}

* [Erstellen eines auf einer Kernkomponente basierenden adaptiven Formulars](/help/forms/creating-adaptive-form-core-components.md)
* [Konfigurieren von Datenquellen](/help/forms/configuring-submit-actions.md)
* [Erstellen des Formulardatenmodells](/help/forms/create-form-data-models.md)
* [Verwenden von Formular-orientierten AEM-Workflows – Schrittreferenz zur Automatisierung von Geschäftsprozessen](/help/forms/aem-forms-workflow-step-reference.md)
* [Erstellen einer benutzerdefinierten Übermittlungsaktion für adaptive Formulare](/help/forms/custom-submit-action-form.md)
* [Erstellen oder Hinzufügen eines adaptiven Formulars zur AEM Sites-Seite](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)
* [Einbetten eines adaptiven Formulars in eine AEM Sites-Seite](/help/forms/embed-adaptive-form-aem-sites.md)
* [Erstellen, Verwenden und Anpassen von Designs in einem adaptiven Formular](/help/forms/using-themes-in-core-components.md)







