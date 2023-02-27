---
title: Einführung in  [!DNL AEM Forms]  as a Cloud Service
description: Entdecken Sie AEM Forms und erfahren Sie, wie Sie damit geschäftsbereite Dokumente und Formularinhalte erstellen können. Erfahren Sie mehr über Platform-as-a-Service (PaaS) und darüber, wie Sie digitale Formulare und Geschäftsprozesse der Unternehmensklasse verwalten und Forms mit aktuellen Datenquellen verbinden können.
landing-page-description: Erfahren Sie, wie Sie Formulare in AEM as a Cloud Service verwenden.
exl-id: aa5ef10c-ba78-4a9d-8b2b-a72a7a306888
source-git-commit: 37274b28ab2343fd3cdfb4747c9dee701c699b46
workflow-type: tm+mt
source-wordcount: '1312'
ht-degree: 23%

---

# Einführung  {#introduction}

Adobe [!DNL Experience Manager Forms as a Cloud Service] bietet eine Cloud-native Platform as a Service (PaaS)-Lösung für Unternehmen zum Erstellen, Verwalten, Veröffentlichen und Aktualisieren komplexer digitaler Formulare, wobei gleichzeitig die gesendeten Daten in Back-End-Prozesse und Geschäftsregeln integriert sowie Daten in einem externen Datenspeicher gespeichert werden. Der Service ist immer aktuell, immer verfügbar und lernt ständig dazu.

Mithilfe dieses Service können Sie interaktive und ansprechende digitale Formulare erstellen und bereitstellen. Beispiel: Ein Unternehmen möchte die Journey seiner Kundenanmeldung digitalisieren. Es verfügt über mehrere Datenquellen mit Kundendaten. Die Formulare sollen vorausgefüllt und elektronisch unterzeichnet und die vom Kunden ausgefüllten Formulare anschließend als PDF-Dateien archiviert werden. Darüber hinaus verfügt das Unternehmen über etliche Druckformulare (PDF-Formulare), die allesamt in digitale Formulare konvertiert werden sollen.



Das Unternehmen kann mithilfe von [!DNL AEM Forms] as a Cloud Service digitale Formulare erstellen, Formulare mit vorhandenen Datenquellen verbinden, Formulare in [!DNL Adobe Sign] integrieren und elektronisch unterzeichnen sowie Datensatzdokumente (DoR) zur Archivierung gesendeter Formulare als PDF-Dateien generieren. Darüber hinaus kann das Unternehmen den Service dazu verwenden, seine bestehenden PDF-Formulare in digitale Formulare zu konvertieren.

Das Unternehmen kann [!DNL AEM Forms] as a Cloud Service verwenden und alle diese Funktionen in der Cloud nutzen, ohne dass eine lokale Infrastruktur erforderlich ist. Der Service erspart Unternehmen zudem komplexe Upgrade-Zyklen, da er stets mit den neuesten Funktionen aktualisiert wird.

## Wichtigste Funktionen {#key-features}

|  |  |
|---|---|
| Adaptive Formulare | Erstellen und verwalten Sie interaktive, dynamische, responsive, mobilfreundliche und datengesteuerte Formulare für Ihre Websites, Apps und anderen digitalen und Druckkanälen. Lesen Sie Folgendes, um zu beginnen, zu verstehen und Registrierungserlebnisse zu implementieren: <ul><li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form.html"> Erstellen eines adaptiven Formulars </a></li><li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/create-an-adaptive-form-on-forms-cs/themes.html">Adaptives Formular formatieren</a></li><li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/configuring-submit-actions.html#enabling-server-side-validation-br"> Senden von Daten an einen Datenspeicher oder einen Workflow</a></li><li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/generate-document-of-record-for-non-xfa-based-adaptive-forms.html"> Datensatz des Formulars für die langfristige Archivierung erstellen</a></li></ul> |
| Kommunikations-APIs | Automatisieren Sie die Erstellung, Verwaltung und Bereitstellung personalisierter, datengesteuerter Kommunikation mit RESTful-APIs bei Bedarf oder in terminierten Intervallen wie Monatsabschlüssen und Kontomitteilungen. Lesen Sie Folgendes, um zu beginnen, zu verstehen und zu erstellen: <ul><li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction.html?#document-generation"> Personalisierte Kommunikation generieren </a> </li><li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction.html?#document-manipulation"> Zusammenführen oder Aufteilen von PDF-Dokumenten </a> </li><li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction.html?#convert-to-and-validate-pdf%2Fa-compliant-documents">Erstellen von PDF/A-kompatiblen Dokumenten </a></li></ul> |
| Service zur automatischen Formularkonvertierung | Konvertieren Sie ältere PDF-basierte Formulare in adaptive Forms, die einfach verwaltet und online verteilt werden können. Lesen Sie für die ersten Schritte Folgendes: <ul><li><a href="https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/configure-service.html?lang=de">Automated forms conversion Service konfigurieren</a></li><li><a href="https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/convert-existing-forms-to-adaptive-forms.html?lang=de">Konvertieren von PDF-Formularen in adaptive Formulare</a></li></ul> |
| Forms Workflow | Automatisieren Sie Geschäftsprozesse mit Formularen und Document Services. Weisen Sie Formulare und Dokumente zu, leiten Sie sie weiter, überprüfen Sie sie und genehmigen Sie sie, während sie sich durch verschiedene Phasen eines Geschäftsprozesses bewegen. Lesen Sie für die ersten Schritte Folgendes:  <ul><li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/create-reviews-forms.html">Formular oder Dokument zur Überprüfung senden</a></li><li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/create-form-centric-workflows/aem-forms-workflow-step-reference.html?#assign-task-step">Erstellen eines Workflows zur Validierungsablehnung</a></li><li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/create-form-centric-workflows/aem-forms-workflow-step-reference.html?#generate-document-of-record-step">Datensatzdokument hinzufügen </a> oder <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/create-form-centric-workflows/aem-forms-workflow-step-reference.html?#sign-document-step"> e-sign </a> Schritte zum Business-Workflow</a></li></ul> |
| E-Signaturen | Integrieren Sie in Adobe Sign und DocuSign, um Forms und Dokumente einfach zur elektronischen Signatur an Benutzer zu senden. <ul><li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/use-adobe-sign/working-with-adobe-sign.html">E-Signieren eines adaptiven Formulars mit Adobe Sign </a></li><li></a> <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/services/integrate-docusign-adaptive-forms.html">E-Signieren eines adaptiven Formulars mit DocuSign </a></li></ul> |
| Forms Analytics | Verwenden Sie Adobe Analytics, um wertvolle Einblicke in das Benutzerverhalten und die Voreinstellungen zu erhalten. <ul><li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/services/integrate-aem-forms-with-adobe-analytics.html?lang=en">Verbinden eines adaptiven Formulars mit Adobe Analytics</a></li></ul> |
| Datenquellen | Verknüpfen Sie Ihre Formulare und Dokumente einfach mit externen Datenquellen, um Daten bereitzustellen und zu senden. <ul><li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/configure-data-sources.html?lang=en">Herstellen einer Verbindung zu einem RDBMS- oder REST-Endpunkt</a></li><li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/configure-msdynamics-salesforce.html?lang=en">Verbindung zu Microsoft Dynamics 365- oder Salesforce-Cloud-Service herstellen</a></li><li><a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/configure-azure-storage.html?lang=en">Verbindung zum Microsoft Azure-Blob-Speicher herstellen</a></li></ul> |


<!-- 
>[!BEGINTABS]

>[!TAB Adaptive Forms]

Adaptive Forms allows businesses to create and manage interactive, data-driven forms for their websites and other digital channels responsive, mobile-friendly forms without. </br> </br> Adaptive Forms in AEM also include a drag-and-drop form builder, which enables non-technical users to easily create and customize forms using pre-built form components such as text boxes, dropdown menus, and date pickers. This enables faster form creation and eliminates the need for extensive coding and development. </br> </br> In addition, AEM Adaptive Forms offer several other features, including: <ul><li>Advanced workflows for routing, approval, and submission of form data Real-time validation and error checking to ensure data accuracy </li><li>Integration with third-party data sources and APIs for pre-filling form fields or validating data </li><li>Advanced analytics and reporting capabilities to track form usage, conversion rates, and other key metrics </li><li>Integration with Adobe Sign and DocuSign for e-signatures </li>

>[!TAB Automated Forms Conversion Service]

Automated Forms Conversion Service allows businesses to convert legacy PDF-based forms into interactive, digital forms that can be easily managed and distributed online. The service helps: <ul><li>Save manual effort required to convert print forms to adaptive forms.</li><li>Applies patterns and appropriate validations during conversion</li><li>Generate Document of Record during conversion </li><li>Group commonly occurring fields into reusable form fragments </li> <li>Enables Adobe Analytics during conversion</li>

>[!TAB Communications API (Document Services)]

Communications APIs are a set of RESTful APIs (Application Programming Interfaces) that enable businesses to automate the creation, management, and delivery of personalized, data-driven communications. </br> </br> These APIs also enable businesses to integrate their communications workflows with third-party systems and data sources, allowing them to create highly targeted and personalized messages that are triggered by specific events or user behaviors. Some key features of AEM Forms Communications APIs include:<ul><li> Dynamic content delivery: The APIs allow businesses to create and deliver dynamic content that is tailored to individual users based on their preferences, behaviors, and past interactions with the business.</li> <li>Personalized messaging: The APIs enable businesses to personalize their communications by including user-specific data such as names, addresses, and purchase history.</li><li>Integration with back-end systems: The APIs can be integrated with a wide range of back-end systems, including CRMs, databases, and marketing automation platforms.</li><li> Generate Pixel Perfect PDF documents: The APIs generate pixel-perfect PDF documents that are customized with user-specific data and content. This feature enables businesses to create highly professional and polished documents, such as invoices, contracts, and statements, that are delivered to users in PDF format.

>[!TAB Advanced Analytics]

The service provides OOTB support to connect with Adobe Analytics. Connecting forms with Adobe Analytics provides several benefits for businesses, including: <ul><li> Improved understanding of user behavior: By connecting forms with Adobe Analytics, businesses can gain a deeper understanding of how users are interacting with their forms. This includes insights into user engagement, conversion rates, drop-off points, and other key metrics that can help businesses identify areas for improvement and optimize their forms for better user experiences. </li><li>Better targeting of marketing efforts: By analyzing user behavior on forms, businesses can gain valuable insights into user preferences and interests. This information can be used to better target marketing efforts and create more effective campaigns that drive engagement and conversions. </li><li> Reduced error rate: By integrating forms with Adobe Analytics, you can find insights about field with most errors and improve data quality, leading to better decision-making and more accurate insights. </li><li> Improved ROI: By optimizing forms based on insights gained from Adobe Analytics, businesses can improve conversion rates and drive more revenue from their digital channels. This can lead to a higher return on investment (ROI) for marketing and digital initiatives, helping businesses to achieve their goals and drive growth.</li>


>[!ENDTABS] 

| Adaptive Forms | Communications APIs  | Automated Forms Conversion Service | Forms Workflows | E-Sign | Forms Analytics | Data Model | 
|---|---|---|---|---|---| ---|
|Create and manage interactive, dynamic, responsive, mobile-friendly, and data-driven forms for your websites, apps, and other digital and Print channels. | Automate creation, management, and delivery of personalized, data-driven communications with RESTful APIs (Application Programming Interfaces) on-demand or at scheduled intervals. | Convert legacy PDF-based forms into Adaptive Forms that can be easily managed and distributed online. | Automate business processes involving forms and document services. Assign, route, review, and approve forms and document as these move through different stages of a business process.| Integrate with Adobe Sign and DocuSign to easliy send send Forms and documents to users for e-signatures. | Use Adobe Analytics to gain valuable insights into user behavior and preferences. | Easily connect your forms and documents with external data sources to retieve and send data. |
|<ul><li>Create an Adaptive Form</li><li>Style an Adaptive Form</li><li>Submit data to a data store or a workflow</li></ul>|<ul><li>Generate personalized communciations</li><li>Assemble or disassemble PDF documents</li><li>Create PDF/A-compliant documents</li></ul>|<ul><li>Configure Automated Forms Conversion Service</li><li>Convert PDF forms to adaptive forms</li></ul>|<ul><li>Send a form or document for review</li><li>Create an approval rejection Workflow</li><li>Add Document of Record or e-signatures to a business workflow</li></ul>|<ul><li>E-sign an Adaptive Form with Adobe Sign</li><li>E-sign an Adaptive Form with DocuSign</li></ul>|<ul><li>Connect an Adaptive Form with Adobe Analytics</li></ul>|<ul><li>Connect to a RDBMS or Rest endpoint</li><li>Connect to Microsoft Dynamics 365 or Salesforce cloud service</li><li>Connect to Microsoft&reg; Azure Blob Storage</li></ul>|

<!--
| | |
|---|---|
| Adaptive Forms | Adaptive Forms allows businesses to create and manage interactive, data-driven forms for their websites and other digital channels responsive, mobile-friendly forms without. </br> </br> Adaptive Forms in AEM also include a drag-and-drop form builder, which enables non-technical users to easily create and customize forms using pre-built form components such as text boxes, dropdown menus, and date pickers. This enables faster form creation and eliminates the need for extensive coding and development. </br> </br> In addition, AEM Adaptive Forms offer several other features, including: <ul><li>Advanced workflows for routing, approval, and submission of form data Real-time validation and error checking to ensure data accuracy </li><li>Integration with third-party data sources and APIs for pre-filling form fields or validating data </li><li>Advanced analytics and reporting capabilities to track form usage, conversion rates, and other key metrics </li><li>Integration with Adobe Sign and DocuSign for e-signatures </li>|
| Automated Forms Conversion Service | Automated Forms Conversion Service allows businesses to convert legacy PDF-based forms into interactive, digital forms that can be easily managed and distributed online. The service helps: <ul><li>Save manual effort required to convert print forms to adaptive forms.</li><li>Applies patterns and appropriate validations during conversion</li><li>Generate Document of Record during conversion </li><li>Group commonly occurring fields into reusable form fragments </li> <li>Enables Adobe Analytics during conversion</li>|
| Communications API (Document Services) | Communications APIs are a set of RESTful APIs (Application Programming Interfaces) that enable businesses to automate the creation, management, and delivery of personalized, data-driven communications. </br> </br> These APIs also enable businesses to integrate their communications workflows with third-party systems and data sources, allowing them to create highly targeted and personalized messages that are triggered by specific events or user behaviors. Some key features of AEM Forms Communications APIs include:<ul><li> Dynamic content delivery: The APIs allow businesses to create and deliver dynamic content that is tailored to individual users based on their preferences, behaviors, and past interactions with the business.</li> <li>Personalized messaging: The APIs enable businesses to personalize their communications by including user-specific data such as names, addresses, and purchase history.</li><li>Integration with back-end systems: The APIs can be integrated with a wide range of back-end systems, including CRMs, databases, and marketing automation platforms.</li><li> Generate Pixel Perfect PDF documents: The APIs generate pixel-perfect PDF documents that are customized with user-specific data and content. This feature enables businesses to create highly professional and polished documents, such as invoices, contracts, and statements, that are delivered to users in PDF format.|
|Advanced Analytics| The service provides OOTB support to connect with Adobe Analytics. Connecting forms with Adobe Analytics provides several benefits for businesses, including: <ul><li> Improved understanding of user behavior: By connecting forms with Adobe Analytics, businesses can gain a deeper understanding of how users are interacting with their forms. This includes insights into user engagement, conversion rates, drop-off points, and other key metrics that can help businesses identify areas for improvement and optimize their forms for better user experiences. </li><li>Better targeting of marketing efforts: By analyzing user behavior on forms, businesses can gain valuable insights into user preferences and interests. This information can be used to better target marketing efforts and create more effective campaigns that drive engagement and conversions. </li><li> Reduced error rate: By integrating forms with Adobe Analytics, you can find insights about field with most errors and improve data quality, leading to better decision-making and more accurate insights. </li><li> Improved ROI: By optimizing forms based on insights gained from Adobe Analytics, businesses can improve conversion rates and drive more revenue from their digital channels. This can lead to a higher return on investment (ROI) for marketing and digital initiatives, helping businesses to achieve their goals and drive growth.</li>|

-->

## Neueste Innovationen {#latest-innovations}

>[!BEGINTABS]

>[!TAB Headless Adaptive Forms &#x200B;]

|| |—|—| |![](https://experienceleague.corp.adobe.com/docs/experience-manager-headless-adaptive-forms/assets/how-headless-adaprive-forms-work.png?)| Erstellen und Verwalten [Headless Adaptive Forms](https://experienceleague.corp.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html) innerhalb der Adobe Experience Manager-Plattform. Ermöglichen es Entwicklern, interaktive Formulare zu erstellen, zu veröffentlichen und zu verwalten, auf die über APIs und nicht über eine herkömmliche grafische Benutzeroberfläche zugegriffen und mit denen interagiert werden kann. <br/> <br/> Diese Formulare sind für die Übermittlung konzipiert, ohne dass eine herkömmliche HTML-Formular-Oberfläche erforderlich ist. Mit anderen Worten: Sie ermöglichen es Ihnen, Formulardaten programmgesteuert über eine API oder einen Backend-Code zu senden, ohne dass sichtbare Formularelemente am Front-End erforderlich sind. <br/> <br/> Headless-Formulare sind in verschiedenen Szenarien nützlich, z. B. beim Erstellen von Einzelseitenanwendungen, progressiven Web-Apps oder mobilen Anwendungen, bei denen eine herkömmliche HTML-Formular-Oberfläche möglicherweise nicht erforderlich oder praktisch ist. Durch die Möglichkeit, dass Entwickler Formulardaten direkt über APIs oder Backend-Code senden können, helfen Headless-Formulare bei der Optimierung von Workflows und der Verbesserung der Gesamtleistung von Webanwendungen.|




>[!TAB Kernkomponenten]

|| |—|—| |![](https://experienceleague.corp.adobe.com/docs/experience-manager-cloud-service/assets/sample-core-components-based-adaptive-form.png?) | Die [Adaptive Forms-Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html#features) sind eine Gruppe von 24 Open-Source-BEM-kompatiblen Komponenten, die auf der Grundlage der Adobe Experience Manager WCM-Kernkomponenten erstellt wurden. Sie sind speziell für die Erstellung von Adaptive Forms entwickelt worden. Hierbei handelt es sich um Formulare, die sich an Gerät, Browser und Bildschirmgröße des Benutzers anpassen. <br/> <br/> Diese Komponenten können verwendet werden, um außergewöhnliche Datenerfassungs- und Registrierungserlebnisse zu schaffen, indem sie eine breite Palette von Formularfeldoptionen bereitstellen, darunter Textfelder, Kontrollkästchen, Dropdownmenüs und mehr. Sie umfassen auch Funktionen wie Validierung, Bedingungslogik und responsives Design, die zum Erstellen benutzerfreundlicher und benutzerfreundlicher Formulare verwendet werden können. <br/> <br/>  Da es sich bei diesen Komponenten um Open-Source-Komponenten handelt, können Entwickler die Komponenten einfach anpassen und erweitern, um sie an die spezifischen Anforderungen ihrer Organisation anzupassen. Und diese Komponenten basieren auf der BEM-Methode, die sicherstellt, dass sie skalierbar und wartbar sind.|



>[!TAB Microsoft PowerAutomate Connector-&#x200B;]

|| |—|—| |![](https://powerusers.microsoft.com/t5/image/serverpage/image-id/182924i17C4BEA1C045D731/image-size/large/is-moderation-mode/true?v=1.0&amp;px=999)| AEM Forms Power Automate Connector ermöglicht Ihnen die Integration von Adobe Experience Manager (AEM) Forms mit Microsoft Power Automate (früher bekannt als Microsoft Flow). Power Automate ist ein Cloud-basierter Dienst, mit dem Sie automatisierte Workflows zwischen verschiedenen Anwendungen und Diensten erstellen können.  <br/> <br/> Mit AEM Power Automate Connector für Formulare können Sie Workflows erstellen, die basierend auf der Übermittlung eines adaptiven Formulars automatisch Trigger werden. Sie können beispielsweise einen Workflow erstellen, der automatisch eine E-Mail-Benachrichtigung an eine bestimmte Person sendet, wenn ein Benutzer ein Formular sendet, oder eine Aufgabe in Microsoft Planer erstellt, wenn ein Benutzer ein Formular ausfüllt.  <br/> <br/> Der AEM Forms Power Automate Connector ist ein leistungsstarkes Tool, mit dem Sie Ihre adaptive Forms automatisieren und mit anderen Anwendungen und Diensten integrieren können, die mit Microsoft Power Automate verbunden sind, sodass Sie mit einer größeren Palette von Tools arbeiten können. Sie können Workflows erstellen, die auf Ihre spezifischen Anforderungen zugeschnitten sind und benutzerdefinierte Aktionen, Bedingungen und Trigger hinzufügen. Zusätzlich bietet Power Automate detaillierte Analysen und Berichte, mit denen Sie Ihre Workflows im Laufe der Zeit überwachen und optimieren können.|


>[!TAB Microsoft Storage Connectors: OneDrive und Sharepoint]

|| |—|—| |![](/help/forms/assets/onedrive-and-sharepoint.jpg)|AEM Forms Microsoft Storage Connectors für OneDrive und SharePoint sind Connectoren, mit denen Sie Adobe Experience Manager (AEM) Forms in Microsoft OneDrive und SharePoint integrieren können. Mit diesem Connector können Sie Datendateien und Anhänge direkt von Adaptive Forms in OneDrive und SharePoint hochladen. |


>[!ENDTABS]

<!--

| | |
|---|---|
| Adaptive Forms | Adaptive Forms allows businesses to create and manage interactive, data-driven forms for their websites and other digital channels responsive, mobile-friendly forms without. </br> </br> Adaptive Forms in AEM also include a drag-and-drop form builder, which enables non-technical users to easily create and customize forms using pre-built form components such as text boxes, dropdown menus, and date pickers. This enables faster form creation and eliminates the need for extensive coding and development. </br> </br> In addition, AEM Adaptive Forms offer several other features, including: <ul><li>Advanced workflows for routing, approval, and submission of form data Real-time validation and error checking to ensure data accuracy </li><li>Integration with third-party data sources and APIs for pre-filling form fields or validating data </li><li>Advanced analytics and reporting capabilities to track form usage, conversion rates, and other key metrics </li><li>Integration with Adobe Sign and DocuSign for e-signatures </li>|
| Automated Forms Conversion Service | Automated Forms Conversion Service allows businesses to convert legacy PDF-based forms into interactive, digital forms that can be easily managed and distributed online. The service helps: <ul><li>Save manual effort required to convert print forms to adaptive forms.</li><li>Applies patterns and appropriate validations during conversion</li><li>Generate Document of Record during conversion </li><li>Group commonly occurring fields into reusable form fragments </li> <li>Enables Adobe Analytics during conversion</li>|
| Communications API (Document Services) | Communications APIs are a set of RESTful APIs (Application Programming Interfaces) that enable businesses to automate the creation, management, and delivery of personalized, data-driven communications. </br> </br> These APIs also enable businesses to integrate their communications workflows with third-party systems and data sources, allowing them to create highly targeted and personalized messages that are triggered by specific events or user behaviors. Some key features of AEM Forms Communications APIs include:<ul><li> Dynamic content delivery: The APIs allow businesses to create and deliver dynamic content that is tailored to individual users based on their preferences, behaviors, and past interactions with the business.</li> <li>Personalized messaging: The APIs enable businesses to personalize their communications by including user-specific data such as names, addresses, and purchase history.</li><li>Integration with back-end systems: The APIs can be integrated with a wide range of back-end systems, including CRMs, databases, and marketing automation platforms.</li><li> Generate Pixel Perfect PDF documents: The APIs generate pixel-perfect PDF documents that are customized with user-specific data and content. This feature enables businesses to create highly professional and polished documents, such as invoices, contracts, and statements, that are delivered to users in PDF format.|
|Advanced Analytics| The service provides OOTB support to connect with Adobe Analytics. Connecting forms with Adobe Analytics provides several benefits for businesses, including: <ul><li> Improved understanding of user behavior: By connecting forms with Adobe Analytics, businesses can gain a deeper understanding of how users are interacting with their forms. This includes insights into user engagement, conversion rates, drop-off points, and other key metrics that can help businesses identify areas for improvement and optimize their forms for better user experiences. </li><li>Better targeting of marketing efforts: By analyzing user behavior on forms, businesses can gain valuable insights into user preferences and interests. This information can be used to better target marketing efforts and create more effective campaigns that drive engagement and conversions. </li><li> Reduced error rate: By integrating forms with Adobe Analytics, you can find insights about field with most errors and improve data quality, leading to better decision-making and more accurate insights. </li><li> Improved ROI: By optimizing forms based on insights gained from Adobe Analytics, businesses can improve conversion rates and drive more revenue from their digital channels. This can lead to a higher return on investment (ROI) for marketing and digital initiatives, helping businesses to achieve their goals and drive growth.</li>|

Adaptive Forms enable organizations to quickly design and deploy responsive, mobile-friendly forms without the need for extensive coding or development. With Adaptive Forms, businesses can create complex, multi-step forms with conditional logic, validations, and integrations with back-end systems such as CRMs and databases.

Adaptive Forms in AEM also include a drag-and-drop form builder, which enables non-technical users to easily create and customize forms using pre-built form components such as text boxes, dropdown menus, and date pickers. This enables faster form creation and eliminates the need for extensive coding and development.

In addition, AEM Adaptive Forms offer several other features, including:

Advanced workflows for routing, approval, and submission of form data
Real-time validation and error checking to ensure data accuracy
Integration with third-party data sources and APIs for pre-filling form fields or validating data
Advanced analytics and reporting capabilities to track form usage, conversion rates, and other key metrics
Overall, AEM Adaptive Forms provide businesses with a powerful tool for creating and managing complex, interactive forms that can be easily integrated into their digital experiences. |




| Feature/Capability | [!DNL AEM Forms] as a Cloud Service | AEM 6.5 Forms  | 
|---|---|---|
| Cloud-native architecture | &#x2611;  | &#x2612; |
| Auto-scaling based on load | &#x2611;  | &#x2612; |
| Zero downtime for upgrades | &#x2611;  | &#x2612; |
| Feature roll-out frequency | Agile*  | Quarterly |
| CDN (content delivery network) included | &#x2611;  | &#x2612; | 
| Topologies optimized for maximum resilience and efficiency| &#x2611;  | &#x2612; | 
| Cloud-native development environment | &#x2611;  | &#x2612; | 
| Self-Service via Cloud Manager | &#x2611;  | &#x2612; | 
| Automated upgrades with Continuous Integration and Continuous Delivery (CI/CD) | &#x2611;  | &#x2612; | 
| Adaptive Forms | &#x2611; | &#x2611; | 
| Data Integration with multiple data sources| &#x2611; | &#x2611; | 
| Communications APIs (Document Services) | &#x2611;* | &#x2611; | 
| Automated Forms Conversion Service | &#x2611; | &#x2611; | 
| Integration with [!DNL Micosoft Power Automate] | &#x2611; | &#x2612; | 
| Integration with [!DNL Adobe Sign] | &#x2611; | &#x2611; | 
| Integration with [!DNL AEM Sites] | &#x2611; | &#x2611; | 
| Integration with [!DNL Adobe Launch] | &#x2611; | &#x2611; | 
| Integration with [!DNL Adobe Analytics] | &#x2611; | &#x2611; | 
| Easy connectivity with Microsoft Dynamics and Salesforce | &#x2611; | &#x2612; |
| Custom submit action for with [!DNL DocuSign] | &#x2611; | &#x2612; | 
| Microsoft Azure data store connector | &#x2611; | &#x2612; |
| Hardened Rule editor | &#x2611; | &#x2612; | 
| Forms Portal | &#x2611; | &#x2611; | 
| AEM Workflows | &#x2611; | &#x2611; | 
| Document of Record | &#x2611; | &#x2611; | 
| Adaptive Forms Wizard | &#x2611; | &#x2612; | 
| Custom XCI for Document of Record| &#x2611; | &#x2612; |
| Invisible Captcha | &#x2611; | &#x2611; |
| Reusable Form Data Model configurations | &#x2611; | &#x2611; |
| Acroform-based Document of Record | &#x2611; | &#x2611; | 
| Government ID based identity authentication for Adobe Sign enabled Adaptive Forms | &#x2611; | &#x2611; | 
| Document Security | &#x2612; | &#x2611; |


* [Notable changes in comparison to AEM 6.5 Forms](notable-changes.md)
* [Frequently asked questions](faq.md)

-->