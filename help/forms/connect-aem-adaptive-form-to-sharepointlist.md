---
title: Wie verbindet AEM adaptive Formular mit der Microsoft® SharePoint-Liste?
description: Verbinden Sie ein adaptives Formular mit der Microsoft® SharePoint-Liste. Erfahren Sie, wie Sie die Microsoft® SharePoint-Liste konfigurieren und ein Formulardatenmodell mithilfe der Konfiguration erstellen. Außerdem erfahren Sie, wie Sie das FDM in Ihr adaptives Formular integrieren.
role: User, Developer
keywords: Verbinden Sie AEM adaptive Formular mit der Microsoft SharePoint-Liste, verbinden Sie das adaptive Formular mit der Microsoft SharePoint-Liste, integrieren Sie AEM adaptive Formular in die Microsoft SharePoint-Liste, integrieren Sie das adaptive Formular in Microsoft Liste, senden Sie Daten aus einem adaptiven Formular in SharePoint Liste, senden Sie AEM Workflow an SharePoint Liste.
source-git-commit: 6a8307cd5e53a9568d8fb87f6b2fc5945b6ed8c5
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 4%

---


# Verbinden eines adaptiven Formulars mit der Microsoft® SharePoint-Liste

<span class="preview"> Dies ist eine Vorabveröffentlichungsfunktion, auf die über unsere [Pre-Release-Kanal](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html#new-features). </span>

**Microsoft® SharePoint**: Microsoft® SharePoint ermöglicht die Zusammenarbeit durch die Bereitstellung dynamischer und effizienter Teamsites für alle Teams, Abteilungen und Abteilungen. Es wird verwendet, um Informationen von jedem Gerät mithilfe eines beliebigen Webbrowsers wie Microsoft® Edge, Internet Explorer, Chrome oder Firefox zu speichern, zu organisieren, freizugeben und darauf zuzugreifen. Die beiden Hauptkomponenten von **Microsoft® SharePoint** sind:

* **Microsoft® SharePoint Document Library**: Microsoft® SharePoint Document Library zeigt eine Liste von Dateien und Ordnern mit ihren Schlüsselinformationen an, z. B. das Datum der letzten Änderung und den Eigentümer einer Datei. Diese Funktion erleichtert die Organisation und Navigation von Dateien.
Anweisungen zur Integration einer **Microsoft® SharePoint Document Library** mit einem adaptiven Formular, siehe [Übermittlungsaktion für adaptive Formulare](/help/forms/configuring-submit-actions.md#submit-to-sharepoint) Artikel.

* **Microsoft® SharePoint-Liste**: Microsoft® SharePoint List ist eine Datenerfassung. Sie können Spalten für verschiedene Datentypen hinzufügen und Ansichten erstellen, um Daten effektiv anzuzeigen. Sie können Listen einfach gruppieren, filtern, sortieren und formatieren.

>[!VIDEO](https://video.tv.adobe.com/v/3424820/connect-aem-adaptive-form-to-sharepointlist/?quality=12&learn=on)

## Voraussetzungen für die Verbindung eines adaptiven Formulars mit der Microsoft® SharePoint-Liste {#prerequisites}

Führen Sie die folgenden Schritte aus, bevor Sie ein adaptives Formular mit der Microsoft® SharePoint-Liste verbinden:

1. [Microsoft® SharePoint-Liste konfigurieren](/help/forms/configure-data-sources.md#configure-microsoft-sharepoint-list)
1. [Erstellen eines Formulardatenmodells mit der Microsoft® SharePoint-Listenkonfiguration](/help/forms/create-form-data-models.md)
1. [Formulardatenmodell zum Abrufen und Senden von Daten konfigurieren](/help/forms/work-with-form-data-model.md#configure-services)
1. [Erstellen eines adaptiven Formulars](/help/forms/creating-adaptive-form-core-components.md)

Jetzt können Sie:

* [Verbinden der Microsoft® SharePoint-Liste mit einem adaptiven Formular](#connect-an-adaptive-form-to-microsoft-sharepoint-list-connect-af-sharepoint-list)
* [Verbinden einer Microsoft® SharePoint-Liste mit einem AEM Workflow](#connect-sharepoint-list-workflow)

## Verbinden eines adaptiven Formulars mit der Microsoft® SharePoint-Liste {#connect-af-sharepoint-list}

So integrieren Sie Microsoft® SharePoint List in Ihr adaptives Formular [Konfigurieren eines adaptiven Formulars zur Verwendung eines Formulardatenmodells](/help/forms/creating-adaptive-form-core-components.md#configure-a-schema-or-form-data-model-for-an-adaptive-formconfigure-schema-or-data-model-for-form)

Nachdem Sie ein adaptives Formular für die Verwendung eines Formulardatenmodells konfiguriert haben, haben Sie folgende Möglichkeiten:

* [Konfigurieren einer Sendeaktion mit einem Formulardatenmodell](/help/forms/configuring-submit-actions.md#submit-using-form-data-model)
* [Konfigurieren des Regeleditors zum Aufrufen eines Formulardatenmodells](/help/forms/rule-editor.md#invoke-form-data-model-service-invoke)

## Verbinden einer Microsoft® SharePoint-Liste mit einem AEM Workflow {#connect-sharepoint-list-workflow}

So integrieren Sie Microsoft® SharePoint List in einen AEM Workflow:

1. [Erstellen eines Workflows zum Aufrufen eines Formulardatenmodells](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=de)

   <!--
    To create a new workflow with the editor, perform the following steps:
    1.  Go to your **AEM Forms Author** instance > **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
    1.  Click **[!UICONTROL Create]** > **[!UICONTROL Create Model]**. The Add Workflow Model dialog appears. 
    1. Specify **[!UICONTROL Title]** and **[!UICONTROL Name (optional)]**.
    1. Click **[!UICONTROL Done]**. The new model is listed in the Workflow Models console.
    1. Select your new workflow, then use **[!UICONTROL Edit]** to open it for configuration.
    1. Add **[!UICONTROL Invoke Form Data Model Service]** step to your workflow.
    1. Confirm the changes with Sync (editor toolbar) to generate the runtime model.
    -->

1. [Konfigurieren der Sendeaktion zum Aufrufen eines AEM-Workflows](/help/forms/configuring-submit-actions.md#invoke-an-aem-workflow)


Erfahren Sie, wie [AEM-Workflow verwenden](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/workflow/use-workflow.html) , um Inhalte in einem adaptiven Formular zusammenzuarbeiten, zu verwalten und zu verarbeiten.

## Best Practices {#best-practices}

<!-- * For storing data in a tabular format or implementing data permissions, it is advisable to use Microsoft® SharePoint List rather than Microsoft® SharePoint Document Library. -->
* In der Microsoft® SharePoint-Liste werden die folgenden Spaltentypen nicht unterstützt:
   * Bildspalte
   * Metadatenspalte
   * Personenspalte
   * externe Datenspalte

## Siehe auch {#see-also}

* [Erstellen eines auf einer Kernkomponente basierenden adaptiven Formulars](/help/forms/creating-adaptive-form-core-components.md)
* [Konfigurieren von Datenquellen](/help/forms/configuring-submit-actions.md)
* [Erstellen des Formulardatenmodells](/help/forms/create-form-data-models.md)
* [Verwenden von Forms-orientierten AEM Workflows - Schrittreferenz zur Automatisierung von Geschäftsprozessen](/help/forms/aem-forms-workflow-step-reference.md)

## Zusätzliche Informationen

* [Erstellen oder Hinzufügen eines adaptiven Formulars zu einer AEM Sites-Seite](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)
* [Einbetten eines adaptiven Formulars in eine AEM Sites-Seite](/help/forms/embed-adaptive-form-aem-sites.md)
* [Erstellen, Verwenden und Anpassen von Designs in einem adaptiven Formular](/help/forms/using-themes-in-core-components.md)







