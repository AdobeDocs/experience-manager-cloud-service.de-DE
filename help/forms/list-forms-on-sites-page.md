---
title: Auflisten von Formularen auf einer Adobe Experience Manager Sites-Seite mithilfe der Forms Portal-Komponente
description: Erfahren Sie, wie Sie Formulare auf einer AEM Sites-Seite auflisten.
feature: Adaptive Forms, Core Components
role: User, Developer
exl-id: 37e3ddd9-b20d-4156-b52e-64e36c455184
source-git-commit: 16b1e7ffa4e3812e9207bb283c63029939f7d14e
workflow-type: tm+mt
source-wordcount: '675'
ht-degree: 35%

---

# Auflisten von Formularen auf der Sites-Seite

Stellen Sie sich vor, ein Benutzer besucht die Website der Bank auf der Suche nach einem Formular zur Kontoeröffnung. Die Bank verwendet die Forms-Portalkomponente, um Benutzende dabei zu unterstützen, das Formular schnell zu finden, indem sie bestimmte Keywords eingeben oder nach Kategorien wie „Neue Konten“ oder „Personal Banking“ filtern. Außerdem können Benutzende das gewünschte Formular einfach finden, ohne durch lange Listen scrollen zu müssen.

Mit **Komponente „Search &amp; Lister** des Forms-Portals können Sie Formulare auf einer Sites-Seite anzeigen und auflisten. Benutzer können anhand spezifischer Kriterien eine umfassende Liste von Formularen konfigurieren und präsentieren, um die Anforderungen des Unternehmens zu erfüllen. Anonyme Benutzer können die Sites-Seite besuchen, um die verfügbaren Formulare anzuzeigen und zu durchsuchen. Die aufgelisteten Formulare können mithilfe der Dropdown-Option **Sortieren nach“ in aufsteigender** absteigender Reihenfolge in der oberen rechten Ecke des Bildschirms sortiert werden.

![Symbol für Suche und Auflister](assets/search-and-lister-component.png)

## Voraussetzung

Bevor Sie die verschiedenen Funktionen einer Formularportal-Komponente erkunden, stellen Sie sicher, dass Kernkomponenten für Ihre Umgebung aktiviert sind. Installieren Sie die neueste Version von , um adaptive Forms-Kernkomponenten für Ihre AEM Cloud Service-Umgebung zu aktivieren.

<!--
## Enable Forms Portal components for your existing environment

To enable out-of-the-box Forms Portal components on existing AEM Forms as a Cloud Service, perform the following steps:

1. **Clone Cloud Manager Git repository on your local development instance:**  Your Cloud Manager Git repository contains a default AEM project. It is based on [AEM Archetype](https://github.com/adobe/aem-project-archetype/). Clone your Cloud Manager Git Repository using Self-Service Git Account Management from Cloud Manager UI to bring the project on your local development environment. For details on accessing the repository, see [Accessing Repositories](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/accessing-repos.html?lang=de).  

1. **Create [!DNL Experience Manager Forms] as a [Cloud Service] project:** Create [!DNL Experience Manager Forms] as a [Cloud Service] project based on [AEM Archetype 50](https://github.com/adobe/aem-project-archetype/releases/tag/aem-project-archetype-50) or later. The archetype help developers easily start developing for [!DNL AEM Forms] as a Cloud Service. It also includes some sample themes and templates to help you started quickly.

    To create [!DNL Experience Manager Forms] as a Cloud Service project, open the command prompt and run the below command. To include [!DNL Forms] specific configurations, themes, and templates, set `includeForms=y`.  

    ```shell
    mvn -B archetype:generate -DarchetypeGroupId=com.adobe.aem -DarchetypeArtifactId=aem-project-archetype -DarchetypeVersion=30 -DaemVersion="cloud" -DappTitle="My Site" -DappId="mysite" -DgroupId="com.mysite" -DincludeForms="y"
    ```

    Also, change `appTitle`, `appId`, and `groupId`, in the above command to reflect your environment.

    After the project is ready, update the `<core.forms.components.version>x.y.z</core.forms.components.version>` property in the top-level `pom.xml` of the Archetype project to reflect the latest version of [core-forms-components](https://github.com/adobe/aem-core-forms-components) in your `AEM Archetype` project. 
 
1. **Deploy the project to your local development environment:** You can use the following command to deploy to your local development environment

    `mvn -PautoInstallPackage clean install`

    For the complete list of commands, see [Building and Installing](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/using.html?lang=de#building-and-installing)

1. [Deploy the archetype to your [!DNL AEM Forms] as a Cloud Service environment](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html?lang=de#embeddeds). -->

Nach der Bereitstellung der neuesten Kernkomponenten in Ihrer Umgebung können Sie auf die Formularportal-Komponenten in Ihrer Authoring-Umgebung zugreifen.

## Auflisten von Formularen auf der Sites-Seite

Um die Portalkomponente **Search &amp; Lister** zu Ihrer Sites-Seite hinzuzufügen, führen Sie die folgenden Schritte aus:

1. Öffnen Sie die AEM Sites-Seite in einem **Bearbeitungsmodus**.
1. Navigieren Sie zu **[!UICONTROL Seiteninformationen]** > **[!UICONTROL Vorlage bearbeiten]**
   ![Richtlinie zum Bearbeiten von Vorlagen](/help/forms/assets/save-form-as-draft-edit-template.png)

1. Klicken Sie auf **[!UICONTROL Richtlinie]** und aktivieren Sie das Kontrollkästchen **[!UICONTROL Search &amp; Lister]** unter **[AEM Archetype Project Name] - Forms and Communications Portal**.

   ![Auswählen von Richtlinien](/help/forms/assets/search-lister-enable-policy.png)

1. Klicken Sie auf **[!UICONTROL Fertig]**.
1. Öffnen Sie die AEM Sites-Seite nun im Authoring-Modus erneut.
1. Suchen Sie im Seiteneditor nach dem Abschnitt, in dem Sie die Formularportal-Komponente hinzufügen können.

1. Klicken Sie auf das Symbol **Hinzufügen**. Das Symbol ist ein Pluszeichen (+). Es steht für die Option zum Hinzufügen neuer Komponenten.

   Wenn Sie auf das Symbol **Hinzufügen** klicken, wird das Dialogfeld **Neue Komponente einfügen** angezeigt, in dem verschiedene Komponenten zum Einfügen angezeigt werden.

   >[!NOTE]
   >
   > Alternativ können Sie die Komponente auch per Drag-and-Drop hinzufügen.

1. Durchsuchen Sie die verfügbaren Komponenten im Dialogfeld und wählen Sie die gewünschte Komponente aus der Liste aus. Wählen Sie beispielsweise die Komponente **Suche und Auflister** aus der Liste aus, um die Forms-Portalkomponente **Suche und Auflister** hinzuzufügen.

   ![Komponente „Search &amp; Lister“](/help/forms/assets/add-search-lister.png)

Konfigurieren Sie nun die Eigenschaften der Komponente **Suche und Auflister**.

## Verstehen der Eigenschaften der Komponente „Search und Lister“

Sie können die Komponenteneigenschaften **Suche und Auflister** einfach über das Dialogfeld „Konfigurieren“ anpassen, um ein nahtloses Benutzererlebnis zu gewährleisten. Wählen Sie zum Konfigurieren die Komponente und dann das ![Symbol „Konfigurieren“](assets/configure_icon.png) aus. Das Dialogfeld **[!UICONTROL Suche und Auflister]** wird geöffnet.

### Registerkarte „Anzeige“

![Registerkarte „Anzeige“](/help/forms/assets/search-and-lister-display-tab.png)

1. In **[!UICONTROL Titel]** geben Sie den Titel für die Komponente für Suche und Auflister an. Ein aussagekräftiger Titel ermöglicht es den Benutzenden, die Liste der Formulare schnell zu durchsuchen.
1. Wählen Sie in **[!UICONTROL Liste]** Layout“ das Layout aus, um die Formulare im Karten- oder Listenformat darzustellen.
1. Wählen Sie **[!UICONTROL Suche ausblenden]** und **[!UICONTROL Sortierung ausblenden]**, um die Suche und Sortierung nach Funktionen auszublenden.
1. Geben Sie unter **[!UICONTROL QuickInfo]** die QuickInfo ein, die angezeigt wird, wenn Sie den Mauszeiger über die Komponente bewegen.

### Registerkarte „Asset“

![Registerkarte „Asset“](/help/forms/assets/search-and-lister-asset-tab.png)

1. Geben **[!UICONTROL auf der Registerkarte]** Asset-Ordner“ den Speicherort an, von dem die Formulare abgerufen und auf der Seite aufgeführt werden.
1. Mithilfe von **[!UICONTROL Weiteren Speicherort hinzufügen]** können Sie mehrere Ordnerspeicherorte konfigurieren.

### Registerkarte „Ergebnisse“

![Registerkarte „Anzeige“](/help/forms/assets/search-and-lister-result-tab.png)

Konfigurieren Sie auf der Registerkarte **[!UICONTROL Ergebnisse]** die maximale Anzahl von Formularen, die pro Seite angezeigt werden sollen. Der Standardwert ist acht Formulare pro Seite.

## Anzeigen von Formularen auf der Sites-Seite mithilfe der Komponente „Search &amp; Lister“

Um die Liste der Formulare anzuzeigen, verwenden Sie die **Search &amp; Lister** Forms Portal-Komponente. Zeigen Sie eine Vorschau der AEM Sites-Seite an, um die Liste der Formulare aus dem Ordner **Assets** auf dem Bildschirm anzuzeigen. Sie können auch über die Suchleiste nach einem bestimmten Formular suchen.

![Symbol für Suche und Auflister](assets/search-and-lister-component.png)

<!--
## Configure Azure Storage for Adaptive Forms {#configure-azure-storage-adaptive-forms}

[[!DNL Experience Manager Forms] Data Integration](data-integration.md) provides [!DNL Azure] storage configuration to integrate forms with [!DNL Azure] storage services. The Form Data Model (FDM) can be used to create Adaptive Forms that interact with [!DNL Azure] server to enable business workflows.

### Create Azure Storage Configuration {#create-azure-storage-configuration}

Before executing these steps, ensure that you have an Azure storage account and an access key to authorize access to the [!DNL Azure] storage account.

1. Navigate to **[!UICONTROL Tools]** &gt; **[!UICONTROL Cloud Services]** &gt; **[!UICONTROL Azure Storage]**.
1. Select a folder to create the configuration and select **[!UICONTROL Create]**.
1. Specify a title for the configuration in the **[!UICONTROL Title]** field.
1. Specify the name of the [!DNL Azure] storage account in the **[!UICONTROL Azure Storage Account]** field.

### Configure Unified Storage Connector for Forms Portal {#configure-usc-forms-portal}

Perform the following steps to configure Unified Storage Connector for AEM Workflows:

1. Navigate to **[!UICONTROL Tools]** &gt; **[!UICONTROL Forms]** &gt; **[!UICONTROL Unified Storage Connector]**.
1. In the **[!UICONTROL Forms Portal]** section, select **[!UICONTROL Azure]** from the **[!UICONTROL Storage]** drop-down list.
1. Specify the [configuration path for the Azure storage configuration](#create-azure-storage-configuration) in the **[!UICONTROL Storage Configuration Path]** field.
1. Select **[!UICONTROL Publish]** and then select **[!UICONTROL Save]** to save the configuration.

## Enable Forms Portal Components {#enable-forms-portal-components}

To use any core component (including the out-of-the-box portal components) in an Adobe Experience Manager (AEM) site, you must create a proxy component and enable it for your site. For creating a proxy component and enabling portal components, see [Using Core Components](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/get-started/using.html?lang=de#create-proxy-components). 

Once a portal component is enabled, you can use it in the author instance of your sites page.

## Add and Configure Forms Portal Components {#configure-forms-portal-components}

You can create and customize Forms Portal on websites authored using AEM by adding and configuring the portal components. Ensure that the [components are enabled](#enable-forms-portal-components) before using them in the Forms Portal.

To add a component, either drag and drop the component from the Components pane to the layout container on the page, or select the add icon on the layout container and add the component from the [!UICONTROL Insert New Component] dialog.

### Configure Drafts & Submissions Component {#configure-drafts-submissions-component}

The Drafts & Submissions component displays forms that are saved as draft for completing later and submitted forms. To configure, select the component and then select the ![Configure icon](assets/configure_icon.png). In the [!UICONTROL Drafts and Submissions] dialog, specify the title to indicate the form listing as draft or submitted forms. Also select whether the component should list draft forms or submitted forms in card or list format.

![Drafts icon](assets/drafts-component.png)

![Submissions icon](assets/submission-listing.png)

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


## Nächste Schritte

Im nächsten Artikel erfahren Sie, [&#x200B; Sie Formulare als Entwürfe speichern und auf einer Sites-Seite mithilfe der Forms-Portalkomponente für Entwürfe und Übermittlungen auflisten](/help/forms/save-core-component-based-form-as-draft.md).

## Verwandte Artikel

{{forms-portal-see-also}}

## Siehe auch {#see-also}

{{see-also}}
