---
title: Wie speichert man das auf der Kernkomponente basierende adaptive Formular als Entwurf?
description: Erfahren Sie, wie Sie ein auf Kernkomponenten basierendes adaptives Formular als Entwurf speichern, ein Forms-Portal erstellen und vordefinierte Kernkomponenten auf einer AEM Sites-Seite verwenden.
feature: Adaptive Forms, Core Components
exl-id: c0653bef-afeb-40c1-b131-7d87ca5542bc
role: User, Developer, Admin
source-git-commit: 52b87073cad84705b5dc0c6530aff44d1e686609
workflow-type: tm+mt
source-wordcount: '1053'
ht-degree: 15%

---


# Speichern von Kernkomponenten-basierten adaptiven Formularen als Entwurf {#save-af-form}

Das Speichern des adaptiven Formulars als Entwurf ist eine wesentliche Funktion, die die Effizienz und Genauigkeit der Benutzer verbessert. Mit dieser Funktion können Benutzer den Fortschritt speichern und zu einem späteren Zeitpunkt zurückkehren, um die Aufgaben abzuschließen, ohne die eingegebenen Informationen zu verlieren. Die Bereitstellung einer &quot;`save-as-draft`&quot;-Option ermöglicht eine flexible Verwaltung der Zeit, reduziert das Risiko von Datenverlusten und bewahrt die Genauigkeit von Übermittlungen. Sie können Formulare als Entwürfe speichern, um sie später abzuschließen.

## Überlegungen

* [Aktivieren Sie die adaptiven Forms-Kernkomponenten für Ihre Umgebung.](/help/forms/enable-adaptive-forms-core-components.md)

* Stellen Sie sicher, dass die [Kernkomponente auf Version 3.0.24 oder höher](https://github.com/adobe/aem-core-forms-components) eingestellt ist, um diese Funktion zu verwenden.
* Stellen Sie sicher, dass Sie über ein Azure-Speicherkonto und einen Zugriffsschlüssel ](https://learn.microsoft.com/en-us/azure/storage/common/storage-account-keys-manage?tabs=azure-portal) verfügen, um den Zugriff auf das Azure-Speicherkonto zu autorisieren.[

## Speichern eines adaptiven Formulars als Entwurf

[!DNL Experience Manager Forms] Die Datenintegration (data-integration.md) bietet eine [!DNL Azure] Speicherkonfiguration, um Formulare in [!DNL Azure] Speicherdienste zu integrieren. Das Formulardatenmodell (FDM) kann verwendet werden, um adaptive Forms zu erstellen, die mit dem [!DNL Azure] -Server interagieren, um Geschäftsabläufe zu ermöglichen.

Um Formulare als Entwurf zu speichern, stellen Sie sicher, dass Sie über ein Azure-Speicherkonto und einen Zugriffsschlüssel verfügen, um den Zugriff auf das Speicherkonto [!DNL Azure] zu autorisieren. Um Formulare als Entwurf zu speichern, führen Sie die folgenden Schritte aus:

1. [Erstellen der Azure-Speicherkonfiguration](#create-azure-storage-configuration)
1. [Konfigurieren von Unified Storage Connector für das Formularportal](#configure-usc-forms-portal)
1. [Erstellen einer Regel zum Speichern eines adaptiven Formulars als Entwurf](#rule-to-save-adaptive-form-as-draft)


### 1. Erstellen der Azure Storage-Konfiguration {#create-azure-storage-configuration}

Sobald Sie über ein Azure-Speicherkonto und einen Zugriffsschlüssel verfügen, um den Zugriff auf das [!DNL Azure] -Speicherkonto zu autorisieren, führen Sie die folgenden Schritte aus, um eine Azure Storage-Konfiguration zu erstellen:

1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Azure-Speicher]**.

   ![Auswahl der Azure Storage Card](/help/forms/assets/save-form-as-draft-azure-card.png)

1. Wählen Sie einen Konfigurationsordner aus, um die Konfiguration zu erstellen, und wählen Sie **[!UICONTROL Erstellen]** aus.

   ![Wählen Sie den Azure Storage Configuration Folder](/help/forms/assets/save-form-as-draft-select-config-folder.png) aus.

1. Geben Sie im Feld **[!UICONTROL Titel]** einen Titel für die Konfiguration an.
1. Geben Sie den Namen des Speicherkontos [!DNL Azure] in den Feldern **[!UICONTROL Azure Storage Account]** und **[!UICONTROL Azure Access Key]** an.

   ![Azure Storage-Konfiguration](/help/forms/assets/save-form-as-draft-azure-storage.png)

1. Klicken Sie auf **Speichern**.

>[!NOTE]
>
> Sie können das **[!UICONTROL Azure Storage Account]** und den **[!UICONTROL Azure Access Key]** aus dem [Microsoft Azure Portal](https://learn.microsoft.com/en-us/azure/storage/common/storage-account-keys-manage?tabs=azure-portal) abrufen.


### 2. Unified Storage Connector für Forms Portal konfigurieren {#configure-usc-forms-portal}

Nachdem Sie die Azure Storage-Konfiguration erfolgreich erstellt haben, konfigurieren Sie den Unified Storage Connector für Forms Portal wie folgt:

1. Gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Forms]** > **[!UICONTROL Unified Storage Connector]**.

   ![Einheitlicher Connector-Speicher](/help/forms/assets/save-form-as-draft-unified-connector.png)

1. Wählen Sie im Abschnitt **[!UICONTROL Formularportal]** den Eintrag **[!UICONTROL Azure]** aus der Dropdown-Liste **[!UICONTROL Speicher]** aus.
1. Geben Sie im Feld **[!UICONTROL Pfad für Speicherkonfiguration]** den [Konfigurationspfad für die Azure-Speicherkonfiguration](#create-azure-storage-configuration) an.

   ![Einstellung für den einheitlichen Connector-Speicher](/help/forms/assets/save-form-as-draft-unified-connector-storage.png)

1. Wählen Sie **[!UICONTROL Speichern]** und dann **[!UICONTROL Publish]** aus, um die Konfiguration zu veröffentlichen.

### 3. Erstellen Sie Regeln, um ein adaptives Formular als Entwurf zu speichern {#rule-to-save-adaptive-form-as-draft}

Um ein Formular als Entwurf zu speichern, erstellen Sie eine Regel **Formular speichern** für eine Formularkomponente, z. B. eine Schaltfläche. Wenn auf die Schaltfläche geklickt wird, wird der Trigger der Regel und das Formular als Entwurf gespeichert. Führen Sie die folgenden Schritte aus, um die Regel **Formular speichern** für eine Schaltflächenkomponente zu erstellen:

1. Öffnen Sie in der Autoreninstanz ein adaptives Formular im Bearbeitungsmodus.
1. Wählen Sie im linken Bereich das ![Symbol „Komponenten“](assets/components_icon.png) aus und ziehen Sie die Komponente **[!UICONTROL Schaltfläche]** auf das Formular.
1. Wählen Sie die Komponente **[!UICONTROL Schaltfläche]** und dann das ![Symbol „Konfigurieren“](assets/configure_icon.png) aus.
1. Wählen Sie das Symbol **[!UICONTROL Regeln bearbeiten]** aus, um den Regeleditor zu öffnen.
1. Wählen Sie **[!UICONTROL Erstellen]** aus, um die Regel zu konfigurieren und zu erstellen.
1. Wählen Sie im Abschnitt **[!UICONTROL Wenn]** die Option **ist geklickt** und wählen Sie im Abschnitt **[!UICONTROL Dann]** die Option **Formular speichern** aus.
1. Wählen Sie **[!UICONTROL Fertig]** aus, um die Regel zu speichern.

![Regel für Schaltfläche erstellen](/help/forms/assets/save-form-as-drfat-create-rule.png)

Wenn Sie ein adaptives Formular in der Vorschau anzeigen, ausfüllen und auf die Schaltfläche **Formular speichern** klicken, wird das Formular als Entwurf gespeichert und kann später verwendet werden.

## Komponente &quot;Drafts &amp; Submissions&quot;zur Auflistung von Entwürfen auf der AEM Sites-Seite

AEM Forms stellt die Portalkomponente &quot;**Entwürfe &amp; Sendungen**&quot;standardmäßig bereit, um gespeicherte Formulare auf AEM Sites-Seiten anzuzeigen. Die Komponente **Entwürfe &amp; Übermittlungen** enthält Formulare, die als Entwürfe gespeichert werden, um später ausgefüllt werden zu können, sowie gesendete Formulare. Diese Komponente bietet jedem angemeldeten Benutzer ein personalisiertes Erlebnis, indem die Entwürfe und Übermittlungen im Zusammenhang mit der vom Benutzer erstellten adaptiven Forms aufgelistet werden.

Sie können vordefinierte Forms Portal-Komponenten verwenden, um Formularentwürfe auf der AEM Sites-Seite aufzulisten. Führen Sie die folgenden Schritte aus, um die Portalkomponente **Entwürfe und Übermittlungen** zu verwenden:

1. [Aktivieren der Forms Portal-Komponente &quot;Drafts &amp; Submissions&quot;](#enable-component)
2. [Komponente &quot;Drafts and Submissions&quot;auf AEM Sites-Seite hinzufügen](#Add-drafts-submissions-component)
3. [Konfigurieren der Komponente für Entwürfe und Einsendungen](#configure-drafts-submissions-component)

### 1. Aktivieren der Forms Portal-Komponente &quot;Drafts &amp; Submissions&quot;{#enable-component}

Führen Sie die folgenden Schritte aus, um die Komponente **[!UICONTROL Entwürfe &amp; Sendungen]** in der Vorlagenrichtlinie zu aktivieren:

1. Öffnen Sie die AEM Sites-Seite im Modus **Bearbeiten** .
1. Navigieren Sie zu **[!UICONTROL Seiteninformationen]** => **[!UICONTROL Vorlage bearbeiten]**
   ![Vorlagenrichtlinie bearbeiten](/help/forms/assets/save-form-as-draft-edit-template.png)

1. Klicken Sie auf das Kontrollkästchen **[!UICONTROL Richtlinie]** und aktivieren Sie das Kontrollkästchen **[!UICONTROL Entwürfe &amp; Sendungen]** unter dem AEM **[Projektnamen des Archetyps] - Forms und Kommunikationsportal**.

   ![Richtlinienauswahl](/help/forms/assets/save-form-as-draft-enable-policy.png)

1. Klicken Sie auf **[!UICONTROL Fertig]**.

Sobald eine Portalkomponente aktiviert ist, können Sie sie in der Autoreninstanz Ihrer AEM Sites-Seite verwenden.

### 2. Komponente &quot;Drafts and Submissions&quot;auf AEM Sites-Seite hinzufügen{#Add-drafts-submissions-component}

Sie können das Formularportal auf mit AEM erstellten Websites erstellen und anpassen, indem Sie die Portalkomponenten hinzufügen und konfigurieren. Stellen Sie sicher, dass die Komponente [Entwürfe und Übermittlungen](#enable-component) aktiviert ist, bevor Sie sie auf der AEM Sites-Seite verwenden.

Um eine Komponente hinzuzufügen, ziehen Sie die Komponente entweder aus dem Komponentenbereich **Entwürfe &amp; Sendungen** in den Layout-Container auf der Seite oder wählen Sie das Symbol zum Hinzufügen im Layout-Container aus und fügen Sie die Komponente aus dem Dialogfeld **[!UICONTROL Neue Komponente einfügen]** hinzu.

![Komponente &quot;Entwurf und Übermittlung hinzufügen&quot;](/help/forms/assets/save-form-as-draft-add-dns.png)

### 3. Komponente &quot;Drafts and Submissions konfigurieren&quot; {#configure-drafts-submissions-component}

Die Komponente **Entwürfe &amp; Übermittlungen** zeigt Formulare an, die als Entwurf zum Ausfüllen späterer und gesendeter Formulare gespeichert wurden. Um **Entwürfe und Übermittlungen** zu konfigurieren, führen Sie die folgenden Schritte aus:
1. Wählen Sie die Komponente **Entwürfe &amp; Sendungen** aus.
1. Klicken Sie auf das Symbol ![Konfigurieren](assets/configure_icon.png) und das Dialogfeld wird angezeigt.
1. Geben Sie im Dialogfeld **[!UICONTROL Entwürfe und Übermittlungen]** Folgendes an:
   * **Titel** Um eine Komponente auf einer Sites-Seite zu identifizieren, wird standardmäßig der Titel über der Komponente angezeigt.
   * **Typ**: Gibt an, dass das Formular als Entwurf oder übermittelte Formulare aufgeführt wird.
   * **Layout**: Zum Anzeigen von Listenentwurfsformularen oder gesendeten Formularen im Karten- oder Listenformat.

   ![Eigenschaften der Entwurfs- und Übermittlungskomponente](/help/forms/assets/save-form-as-draft-dns-properties.png)

1. Klicken Sie auf **Fertig**.

Wenn **[!UICONTROL Typ auswählen]** als **Entwurf-Forms** ausgewählt ist, werden die als Entwürfe gespeicherten Formulare angezeigt:
![Symbol &quot;Entwürfe&quot;](assets/drafts-component.png)

Wenn **[!UICONTROL Typ auswählen]** als **Gesendete Forms** ausgewählt ist, werden die gesendeten Formulare angezeigt:

![Symbol für Einsendungen](assets/submission-listing.png)

Sie können das Formular öffnen, indem Sie auf das entsprechende Formular klicken.

<!--

### Configure Search & Lister Component {#configure-search-lister-component}

The Search & Lister component is used to list adaptive forms on a page and to implement search on the listed forms. 

![Search and Lister icon](assets/search-and-lister-component.png)

To configure, select the component and then select the ![Configure icon](assets/configure_icon.png). The [!UICONTROL Search and Lister] dialog opens.

1. In the [!UICONTROL Display] tab, configure the following:
    * In **[!UICONTROL Title]**, specify the title for the Search & Lister component. An indicative title enables the users perform quick search across the list of forms.
    * From the **[!UICONTROL Layout]** list, select the layout to represent the forms in card or list format.
    * Select **[!UICONTROL Hide Search]** and **[!UICONTROL Hide Sorting]** to hide the search and sort by features.
    * In **[!UICONTROL Tooltip]**, provide the tooltip that appears when you hover over the component. 
1. In the [!UICONTROL Asset Folder] tab, specify the location from where the forms are pulled and listed on the page. You can configure multiple folder locations.
1. In the [!UICONTROL Results] tab, configure the maximum number of forms to display per page. The default is eight forms per page.

### Configure Link Component {#configure-link-component}

The link component enables you to provide links to an adaptive form on the page. To configure, select the component and then select the ![Configure icon](assets/configure_icon.png). The [!UICONTROL Edit Link Component] dialog opens.

1. In the [!UICONTROL Display] tab, provide the link caption and tooltip to ease identification of the forms represented by the link.
1. In the [!UICONTROL Asset Info] tab, specify the repository path where the asset is stored. 
1. In the [!UICONTROL Query Params] tab, specify the additional parameters in the key-value pair format. When the link is clicked, these additional parameters and passed along with the form.

## Configure Asynchronous Form Submission Using Adobe Sign {#configure-asynchronous-form-submission-using-adobe-sign}

You can configure to submit an adaptive form only when all the recipients have completed the signing ceremony. Follow the steps below to configure the setting using Adobe Sign.

1. In the author instance, open an Adaptive Form in the edit mode.
1. From the left pane, select the Properties icon and expand the **[!UICONTROL ELECTRONIC SIGNTATURE]** option.
1. Select **[!UICONTROL Enable Adobe Sign]**. Various configuration options display. 
1. In the [!UICONTROL Submit the form] section, select the **[!UICONTROL after every recipient completes signing ceremony]** option to configure the Submit Form action, where the form is first sent to all the recipients for signing. Once all the recipients have signed the form, only then the form is submitted. 

## Save Adaptive Forms As Drafts {#save-adaptive-forms-as-drafts}

You can save forms as Drafts for completing them later. There are two ways in which a form is saved as a draft:

* Create a "Save Form" rule on a form component, for example, a button. On clicking the button, the rule triggers and the form are saved a draft.
* Enable Auto-Save feature, which saves the form as per the specified event or after a configured interval of time.

### Create Rules to Save an Adaptive Form as Draft {#rule-to-save-adaptive-form-as-draft}

To create a "Save Form" rule on a form component, for example, a button, follow the steps below:

1. In the author instance, open an Adaptive Form in edit mode.
1. From the left pane, select ![Components icon](assets/components_icon.png) and drag the [!UICONTROL Button] component to the form.
1. Select the [!UICONTROL Button] component and then select the ![Configure icon](assets/configure_icon.png). 
1. Select the [!UICONTROL Edit Rules] icon to open the Rule Editor. 
1. Select **[!UICONTROL Create]** to configure and create the rule.
1. In the [!UICONTROL When] section, select "is clicked" and in the [!UICONTROL Then] section, select the "Save Form" options.
1. Select **[!UICONTROL Done]** to save the rule.

### Enable Auto-save {#enable-auto-save}

You can configure the auto-save feature for an adaptive form as follows:

1. In the author instance, open an Adaptive Form in edit mode.
1. From the left pane, select the ![Properties icon](assets/configure_icon.png) and expand the [!UICONTROL AUTO-SAVE] option.
1. Select the **[!UICONTROL Enable]** check box to enable auto-save of the form. You can configure the following:
* By default, the [!UICONTROL Adaptive Form Event] is set to "true", which implies that the form is auto-saved after every event.
* In [!UICONTROL Trigger], configure to trigger auto-save based on the occurrence of an event or after a specific interval of time.
-->

## Siehe auch {#see-also}

{{see-also}}



<!--

>[!MORELIKETHIS]
>
>* [Configure data sources for AEM Forms](/help/forms/configure-data-sources.md)
>* [Configure Azure storage for AEM Forms](/help/forms/configure-azure-storage.md)
>* [Integrate Microsoft Dynamics 365 and Salesforce with Adaptive Forms](/help/forms/configure-msdynamics-salesforce.md)

-->
