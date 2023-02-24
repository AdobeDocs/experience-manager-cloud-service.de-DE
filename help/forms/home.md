---
title: Einführung in  [!DNL AEM Forms]  as a Cloud Service
description: Entdecken Sie AEM Forms und erfahren Sie, wie Sie damit geschäftsbereite Dokumente und Formularinhalte erstellen können. Erfahren Sie mehr über Platform-as-a-Service (PaaS) und darüber, wie Sie digitale Formulare und Geschäftsprozesse der Unternehmensklasse verwalten und Forms mit aktuellen Datenquellen verbinden können.
landing-page-description: Erfahren Sie, wie Sie Formulare in AEM as a Cloud Service verwenden.
exl-id: aa5ef10c-ba78-4a9d-8b2b-a72a7a306888
source-git-commit: f8e229820bb7aef3923e955c928033ef7d3d9460
workflow-type: tm+mt
source-wordcount: '1108'
ht-degree: 26%

---

# Einführung  {#introduction}

Adobe [!DNL Experience Manager Forms as a Cloud Service] bietet eine Cloud-native Platform as a Service (PaaS)-Lösung für Unternehmen zum Erstellen, Verwalten, Veröffentlichen und Aktualisieren komplexer digitaler Formulare, wobei gleichzeitig die gesendeten Daten in Back-End-Prozesse und Geschäftsregeln integriert sowie Daten in einem externen Datenspeicher gespeichert werden. Der Service ist immer aktuell, immer verfügbar und lernt ständig dazu.

Mithilfe dieses Service können Sie interaktive und ansprechende digitale Formulare erstellen und bereitstellen. Beispiel: Ein Unternehmen möchte die Journey seiner Kundenanmeldung digitalisieren. Es verfügt über mehrere Datenquellen mit Kundendaten. Die Formulare sollen vorausgefüllt und elektronisch unterzeichnet und die vom Kunden ausgefüllten Formulare anschließend als PDF-Dateien archiviert werden. Darüber hinaus verfügt das Unternehmen über etliche Druckformulare (PDF-Formulare), die allesamt in digitale Formulare konvertiert werden sollen.

Das Unternehmen kann mithilfe von [!DNL AEM Forms] as a Cloud Service digitale Formulare erstellen, Formulare mit vorhandenen Datenquellen verbinden, Formulare in [!DNL Adobe Sign] integrieren und elektronisch unterzeichnen sowie Datensatzdokumente (DoR) zur Archivierung gesendeter Formulare als PDF-Dateien generieren. Darüber hinaus kann das Unternehmen den Service dazu verwenden, seine bestehenden PDF-Formulare in digitale Formulare zu konvertieren.

Das Unternehmen kann [!DNL AEM Forms] as a Cloud Service verwenden und alle diese Funktionen in der Cloud nutzen, ohne dass eine lokale Infrastruktur erforderlich ist. Der Service erspart Unternehmen zudem komplexe Upgrade-Zyklen, da er stets mit den neuesten Funktionen aktualisiert wird.

## Wichtigste Funktionen {#key-features}

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


>[!ENDTABS] -->

| Adaptive Formulare | Service zur automatischen Formularkonvertierung | Kommunikations-APIs | Forms Analytics |
|---|---|---|---|
| Adaptive Forms ermöglicht es Unternehmen, interaktive, datengesteuerte Formulare für ihre Websites und anderen digitalen Kanälen zu erstellen und zu verwalten. Responsive, für Mobilgeräte geeignete Formulare. | Mit automated forms conversion Service können Unternehmen ältere PDF-basierte Formulare in interaktive, digitale Formulare konvertieren, die einfach verwaltet und online verteilt werden können. | Kommunikations-APIs sind eine Reihe von RESTful-APIs (Application Programming Interfaces), mit denen Unternehmen die Erstellung, Verwaltung und Bereitstellung personalisierter, datengesteuerter Kommunikation automatisieren können. | Der Dienst bietet OOTB-Unterstützung für die Verbindung mit Adobe Analytics. Die Verbindung von Formularen mit Adobe Analytics bietet Unternehmen mehrere Vorteile, darunter ein besseres Verständnis des Benutzerverhaltens, eine bessere Ausrichtung der Marketing-Maßnahmen, ein reduzierter Fehlerstatus und ein verbesserter ROI. |

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

[Headless Adaptive Forms](https://experienceleague.corp.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html) ist eine Lösung zum Erstellen und Verwalten von Headless-Web-Formularen auf der Adobe Experience Manager-Plattform. Mit dieser Funktion können Unternehmen interaktive Formulare erstellen, veröffentlichen und verwalten, auf die über APIs und nicht über eine herkömmliche grafische Benutzeroberfläche zugegriffen und mit denen interagiert werden kann. AEM Headless Adaptive Forms ermöglicht größere Flexibilität und Skalierbarkeit bei der Formularentwicklung und -implementierung sowie ein verbessertes Benutzererlebnis durch die Möglichkeit, Formulardesign und -funktionalität an spezifische Anforderungen anzupassen. Durch die Nutzung der Funktionen von AEM und Headless-Technologie bietet diese Lösung eine robuste Plattform für die Erstellung, Verwaltung und Bereitstellung von Webformularen für verschiedene Anwendungsfälle und Anwendungen.


>[!TAB Kernkomponenten]

Die [Adaptive Forms-Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html#features) sind eine Gruppe von 24 Open-Source-BEM-kompatiblen Komponenten, die auf der Grundlage der Adobe Experience Manager WCM-Kernkomponenten erstellt wurden. Sie sind speziell für die Erstellung von Adaptive Forms entwickelt worden. Hierbei handelt es sich um Formulare, die sich an Gerät, Browser und Bildschirmgröße des Benutzers anpassen.

Diese Komponenten können verwendet werden, um außergewöhnliche Datenerfassungs- und Registrierungserlebnisse zu schaffen, indem sie eine breite Palette von Formularfeldoptionen bereitstellen, darunter Textfelder, Kontrollkästchen, Dropdownmenüs und mehr. Sie umfassen auch Funktionen wie Validierung, Bedingungslogik und responsives Design, die zum Erstellen benutzerfreundlicher und benutzerfreundlicher Formulare verwendet werden können.

Da es sich bei diesen Komponenten um Open-Source-Komponenten handelt, können Entwickler die Komponenten einfach anpassen und erweitern, um sie an die spezifischen Anforderungen ihrer Organisation anzupassen. Und diese Komponenten basieren auf der BEM-Methode, die sicherstellt, dass sie skalierbar und wartbar sind.


>[!TAB Microsoft PowerAutomate Connector-&#x200B;]

Microsoft Power Automate Connector für AEM Forms ist ein Connector, mit dem Sie Adobe Experience Manager (AEM) Forms mit Microsoft Power Automate integrieren können (früher als Microsoft Flow bekannt). Power Automate ist ein Cloud-basierter Dienst, mit dem Sie automatisierte Workflows zwischen verschiedenen Anwendungen und Diensten erstellen können.

Mit dem Power Automate Connector für AEM Formular können Sie Workflows erstellen, die basierend auf der Übermittlung eines adaptiven Formulars automatisch Trigger werden. Sie können beispielsweise einen Workflow erstellen, der automatisch eine E-Mail-Benachrichtigung an eine bestimmte Person sendet, wenn ein Benutzer ein Formular sendet, oder eine Aufgabe in Microsoft Planer erstellt, wenn ein Benutzer ein Formular ausfüllt.

Die Verwendung des Power Automate Connectors für AEM Forms bietet viele Vorteile, darunter:

* **Automatisierung**: Sie können Routineaufgaben automatisieren, Prozesse optimieren, Zeit sparen und Fehler reduzieren.

* **Integration**: Der Connector ermöglicht Ihnen die Integration von Adobe Experience Manager Forms mit anderen Anwendungen und Diensten, sodass Sie mit einer breiteren Palette von Tools arbeiten können.

* **Anpassung**: Sie können Workflows erstellen, die auf Ihre spezifischen Anforderungen zugeschnitten sind und benutzerdefinierte Aktionen, Bedingungen und Trigger hinzufügen.

* **Analytics**: Power Automate bietet detaillierte Analysen und Berichte, mit denen Sie Ihre Workflows im Laufe der Zeit überwachen und optimieren können.

Der Power Automate Connector für AEM Forms ist ein leistungsstarkes Tool, mit dem Sie Ihre AEM Forms automatisieren und mit anderen Anwendungen und Diensten integrieren und so Effizienz und Produktivität steigern können.

>[!TAB Microsoft Storage Connectors: OneDrive und Sharepoint]

AEM Forms Microsoft Storage Connectors für OneDrive und SharePoint sind Connectoren, mit denen Sie Adobe Experience Manager (AEM) Forms in Microsoft OneDrive und SharePoint integrieren können. Mit diesen Connectoren können Sie AEM Forms-Daten und -Dokumente in den Cloud-basierten Speicherlösungen von Microsoft speichern und verwalten.

Mit diesen Connectoren können Sie AEM Forms-Daten und -Dokumente in Microsoft OneDrive speichern und verwalten. Mit diesem Connector können Sie Datendateien und Anhänge direkt von AEM Forms in OneDrive und SharePoint hochladen.

Die Verwendung von AEM Forms Microsoft Storage Connectors für OneDrive und SharePoint bietet verschiedene Vorteile:

* **Integration**: Diese Connectoren ermöglichen Ihnen die Integration von AEM Forms in die Cloud-basierten Speicherlösungen von Microsoft, sodass Sie die Leistungsfähigkeit dieser Plattformen nutzen können.

* **Zusammenarbeit**: OneDrive und SharePoint sind Kooperationsplattformen, mit denen Teammitglieder an Dateien und Dokumenten zusammenarbeiten können. Durch die Integration von AEM Forms mit diesen Plattformen können Sie die Zusammenarbeit und Teamarbeit verbessern.

* **Sicherheit**: OneDrive und SharePoint bieten zuverlässige Sicherheitsfunktionen, mit denen sichergestellt wird, dass Ihre Daten und Dokumente sicher gespeichert und aufgerufen werden.

AEM Forms Microsoft Storage Connectors für OneDrive und SharePoint sind leistungsstarke Tools, mit denen Sie AEM Forms-Daten und -Dokumente in den Cloud-basierten Speicherlösungen von Microsoft speichern und verwalten und so die Zusammenarbeit und Sicherheit verbessern können.

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