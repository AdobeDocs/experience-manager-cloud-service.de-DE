---
title: Architektur von Experience Manager [!DNL AEM Forms] as a Cloud Service
description: Machen Sie sich mit der Architektur von [!DNL AEM Forms] as a Cloud Service vertraut, um mehr über die Skalierbarkeit, Widerstandsfähigkeit und Leistung der Plattform zu erfahren.
source-git-commit: 494e37b24ab1c8432613d6a62a4c3a1d48d216ee
workflow-type: tm+mt
source-wordcount: '1049'
ht-degree: 25%

---


# [!DNL AEM] as a Cloud Service Architektur von Forms {#architecture}

[!DNL Adobe Experience Manager Forms] as a Cloud Service ist eine Cloud-native Lösung, mit der Unternehmen komplexe digitale Formulare und Kommunikationen erstellen, verwalten, veröffentlichen und aktualisieren und gleichzeitig gesendete Daten in Back-End-Prozesse, Geschäftsregeln und Daten in einem externen Datenspeicher integrieren können. Er erweitert [!DNL Adobe Experience Manager as a Cloud Service]. Weitere Informationen zu Skalierung, Bereitstellung, Umgebungen und anderen Infrastrukturen finden Sie unter [Einführung in die Architektur von [!DNL Adobe Experience Manager as a Cloud Service]](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/core-concepts/architecture.html?lang=de).

AEM Forms as a Cloud Service unterstützt zwei Hauptanwendungsfälle: Digitale Registrierung und Kundenkommunikation. Die folgenden Abbildungen zeigen die Architektur für beide Anwendungsfälle.

## Architektur- und Flussdiagramme

|  |  |
|---|---|
| **Digitale Forms-Registrierung** | ![Forms-digitale Einschreibung](assets/forms-cloud-service-architecture-forms-digital-enrollment.svg) |
| **Forms-Kommunikation** | ![Forms-Kommunikation](assets/forms-cloud-service-architecture-forms-communications.svg) |

## Komponenten

Forms as a Cloud Service umfasst mehrere Komponenten:

### CDN (Content Delivery Network)

Jedes as a Cloud Service AEM Forms-Programm hat Zugriff auf [integrierter CDN-Dienst](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn.html). Sie ist in der Lizenz von Forms as a Cloud Services enthalten.

### Autor

Ein Autor ist eine as a Cloud Service AEM Forms-Instanz, die im standardmäßigen Autorenmodus ausgeführt wird. Sie ist für interne Benutzer, Formularentwickler und Entwickler gedacht. Eine Autorenumgebung ermöglicht die folgenden Funktionen:

* Erstellen und Verwalten von Formularen
* Herstellen einer Verbindung zum Automated forms conversion-Dienst, um ein PDF- oder XDP-Formular in ein adaptives Formular zu konvertieren.
* Erstellen und Ausführen von Forms-orientierten Workflows.
* Verwalten von Assets für adaptive Formulare
* Verwalten von Kommunikations-Assets.
* Synchrone RESTful-APIs (Echtzeit-APIs) und Batch-APIs zum Erstellen, Zusammenstellen und Bereitstellen markenorientierter und personalisierter Kommunikation.
* Synchrone APIs zum Kombinieren, Neuanordnen und Überprüfen von PDF-Dokumenten.

### Veröffentlichen  

Eine Veröffentlichungsinstanz ist ein AEM Forms-as a Cloud Service, der im standardmäßigen Veröffentlichungsmodus ausgeführt wird. Veröffentlichungsinstanzen sind für Endbenutzer von formularbasierten Anwendungen vorgesehen, z. B. Benutzer, die auf eine öffentliche Website zugreifen und Formulare senden. Ermöglicht werden folgende Funktionen:

* Wiedergabe und Senden von Formularen für Endbenutzer
* Transport von Formularrohdaten zur weiteren Verarbeitung und Speicherung im endgültigen Aufzeichnungssystem.
* Herstellen einer Verbindung zum kundenverwalteten Speicher, um Daten zu speichern.
* Herstellen einer Verbindung mit Adobe Sign zum e-Signieren eines Datensatzes für die Übermittlung adaptiver Formulare.
* Synchronisieren Sie APIs, um markenorientierte und personalisierte Kommunikation zu erstellen, zusammenzustellen und bereitzustellen.
* Synchronisieren Sie APIs zum Kombinieren, Neuanordnen und Überprüfen von PDF-Dokumenten.

Die Rückwärtsreplikation ist auf AEM as a Cloud Service nicht verfügbar, um Inhalte/Daten vom Veröffentlichungsdienst an den Autorendienst zu senden. Sie können jedoch eine auf der Veröffentlichungsinstanz ausgeführte adaptive Forms konfigurieren, um Daten an einen Workflow auf einer Autoreninstanz zu senden (Workflows können nur auf der Autoreninstanz ausgeführt werden). Dies ist in Anwendungsfällen für die Genehmigung hilfreich.

#### Dispatcher

[Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/disp-overview.html) ist das Caching- und/oder Lastenausgleichstool von Adobe Experience Manager, das mit einem Webserver der Unternehmensklasse verwendet werden kann.

### Adobe Services

**automated forms conversion-Dienst**

[automated forms conversion-Dienst](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/introduction.html?lang=de) konvertiert Ihre PDF- und XFA-Formulare automatisch in gerätefreundliche, responsive und HTML5-basierte adaptive Formulare.

**Adobe Sign**

Adobe Sign ist ein Cloud-basierter e-Signaturdienst, mit dem der Benutzer Signaturprozesse mithilfe eines Browsers oder Mobilgeräts senden, signieren, tracken und verwalten kann. Sie können Adobe Sign in ein adaptives Formular integrieren, um Signierungs-Workflows zu automatisieren, Prozesse mit einer und mehreren Signaturen zu vereinfachen und adaptive Formulare elektronisch zu signieren.

<!-- **PDF Service API**
Adobe’s PDF Services API lets create, combine, export, and extract data from PDFs through powerful and flexible cloud-based APIs. -->

### Vom Kunden verwalteter Speicher

Forms as a Cloud Service bietet Optionen zum Speichern von Inhalten in einem externen Speichersystem wie Blob Store, Datenbank oder einem Speicherdienst. Sie können auch in Verarbeitung befindliche Workflow-Daten (AEM Workflow-Variablen-Daten) speichern, die sensible personenbezogene Daten (EPPD) enthalten, in einem kundenverwalteten Repository zur sicheren Verarbeitung. Adobe empfiehlt, vertrauliche Daten nur in kundenverwalteten Speichern zu speichern.

Sie können die **Unified Storage Connector** zur Verbindung mit Blob Storage und **Formulardatenmodell** , um eine Verbindung zu Datenbanken oder Backend-Services herzustellen (RESTful, SOAP, Azure Blob Storage usw.).

### Document Services

Document Services umfasst Folgendes:

* **Output Service (Communications - Document Generation APIs)** hilft bei der Erstellung von markengenehmigten, personalisierten und standardisierten Dokumenten wie Geschäftskorrespondenzen, Anweisungen, Anforderungsverarbeitungsbriefen, Leistungsbenachrichtigungen, monatlichen Rechnungen oder Willkommenskits.

* **Assembler-Dienst (Communications - Document Manipulation APIs)** hilft beim Kombinieren, Neuanordnen und Überprüfen von PDF-Dokumenten.

* **DoR-Dienst (Document of Record)** hilft beim Generieren des Datensatzdokuments (DoR). Der Dienst wird in eigenen Pods ausgeführt, die von der Autoren- und Veröffentlichungsinstanz von Forms as a Cloud Service getrennt sind. Sie bietet eine bessere Leistung und skaliert die Pods unabhängig von der Last.

### Cloud Manager 

Cloud Manager ist eine wesentliche Komponente von [AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/introduction.html). Es ist der zentrale Einstiegspunkt für die Vorgänge und Entwickler unserer Kunden. Es ist der Ort, an dem AEM-Programme und -Umgebungen verwaltet werden. Cloud Manager hat sich zu einem Selbstbedienungsportal entwickelt, in dem die Hauptkomponenten von AEM as a Cloud Service erstellt und konfiguriert werden können:

* Erstellen und Verwalten von Programmen
* Erstellen und Verwalten von AEM-Umgebungen in diesen Programmen
* Erstellen und Verwalten der Pipelines für die Bereitstellung des Kunden-Codes und der zugehörigen Konfiguration in einer bestimmten Umgebung
* Benachrichtigung über wichtige Lebenszyklusereignisse für diese Komponenten (z. B. Produktaktualisierungen). Weitere Informationen zu Cloud Manager finden Sie unter [Grundlegendes zu Adobe Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/cloud-manager/understand-cloud-manager-for-aem.html?lang=de) und [Einführung in Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html?lang=de).

### Entwicklerkonsole

Eine Entwicklerkonsole bietet verschiedene Details zu den einzelnen ausgeführten Forms as a Cloud Service-Umgebungen. Diese Details sind beim Debugging der Umgebung hilfreich. Weitere Informationen finden Sie unter [Debugging von AEM as a Cloud Service mit der Developer Console](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/developer-console.html?lang=de).

<!--

+++CDN (Content Delivery Network):

Every AEM Forms as a Cloud Service program has access to Fastly CDN service. It is included in the licence of Forms as a Cloud Services.

+++

+++Adaptive Forms
Adaptive Forms enable customers to author web-friendly reflowable web forms and fragments that are used by the customers for their data capture needs. This feature enables customers to manage their complex data capture needs easily, by leveraging multiple integrations with Adobe Sign, Document Services, Form Data Model, Automated Forms Conversion service, and more.

+++

+++Automated Forms Conversion Service (AFCS)
Automated Forms Conversion service helps accelerate digitization and modernization of data capture experience through automated conversion of PDF forms to adaptive forms. The service, powered by Adobe Sensei, automatically converts your PDF forms to device-friendly, responsive, and HTML5-based adaptive forms. While leveraging the existing investments in PDF Forms and XFA, the service also applies appropriate validations, styling, and layout to adaptive form fields during conversion.

+++

+++Form Data Model
The Form Data Model (FDM) feature is the standard way of creating data integrations with external/internal data sources and using them across the different Forms as a Cloud Service features. FDM provides a rich editor for customers to integrate, define, and manage relationships between the different entities and data sources and perform operations on them. Form data is stored in a data store hosted on the customer premises. Organizations can also use blob store hosted by the cloud provider and Adobe Experince Platform to store data.

+++

+++Forms Workflows
Forms-centric workflows is an extension to the default AEM Workflow and provides our customers with additional workflow capabilities like Form Data review, task assignment, and document services invocation.

+++

+++Communications
Forms as a Cloud Service offering consists of multiple services tailored specifically for document processing.

+++

+++Document of Record
A Document of Record is a PDF version of a form. It provides an ability to keep a record of the information  that you provide and submit in an Adaptive Form in PDF fromat. The service provides a default DoR template and tools to develop a custom template.

+++

## Terminologies

<!-- ## Cloud Manager{#cloud-manager}

Cloud Manager is an essential component to [AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/introduction.html?lang=en). Each new tenant of the [!DNL AEM Forms] as a Cloud Service is first provisioned for Cloud Manager access. Cloud Manager is the single-entry point for the operations and developer persona of our customers. It is the place from where the AEM programs and environments can be managed. Cloud Manager has evolved as a self-service portal where the main components of the AEM as a Cloud Service can be created and configured:

* Creating and managing programs
* Creating and managing the AEM environments within the programs
* Creating and managing the pipelines for deploying the customer code and configuration to a particular environment
* Getting notified of important lifecycle events for these components (e.g. product updates)
For more information about Cloud Manager, see [Understand Adobe Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/cloud-manager/understand-cloud-manager-for-aem.html) and [Introduction to Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html).

## Users and Authentication {#users-and-authentication}

AEM as a Cloud Service includes Admin Console support for AEM instances and Adobe Identity Management System (IMS) based authentication. The Admin Console allows administrators to centrally manage all Experience Cloud users. Users and Groups can be assigned to product profiles associated with AEM as a Cloud Service instances, allowing them to log in to that instance. For more information about users, authentication, and, and accessing an instance of AEM as a Cloud Service, see [IMS Support for [!DNL Adobe Experience Manager] as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html?lang=en#introduction).

Various personas are involved in a typical [!DNL AEM Forms] project. After you log in to your [!DNL AEM Forms] as a Cloud Service instance, you can [add users in admin console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html) for personas applicable to your organization or project and [assign users to built-in groups](forms-groups-privileges-tasks.md) to provide them required privileges.

To learn various in-built [!DNL AEM Forms] specific user groups and privileges available on [!DNL AEM Forms] as a Cloud Services instance, see [Configure, user, roles and groups](forms-groups-privileges-tasks.md). 

## Developer Experience {#developer-experience}

The new architecture supporting AEM as a Cloud Service brings some key changes to the overall developer experience. One of the major goals for the changes to developer experience is to allow migration to AEM as a Cloud Service as quickly as possible, with little modifications to existing custom code.

## Cloud development {#cloud-development}

Here are the guidelines to run your existing code smoothly on AEM as a Cloud Service environment:

* Store your code and configurations to the Git repository of the associated Cloud Manager program. It makes managing and integrating code with CI/CD a breeze.  
* Make application code and configuration compatible with the baseline [!DNL AEM Forms] images. Using the latest APIs helps to build faster and secure applications.
* Use the Cloud Manager pipeline associated with the Cloud Manager environment to build and deploy applications. It helps you bring the latest features and bug fixed for [!DNL AEM Forms] as a Cloud Service to your environment.
* Try that your custom applications pass all the code quality, security, and performance gates enforced in the pipeline. It helps build secure and better performing applications which leads to better customer experience. You can always use Cloud Manager UI to skip some checks.
This process is commonly referred to as cloud-first development. [!DNL AEM Forms] as a Cloud Service also provides an SDK to support rapid development before the pending code and configuration changes are attempted in the cloud.
Some interfaces that were previously part of the AEM QuickStart are no longer available to the users of the AEM as a Cloud Service environment. For instance, the Web Console where OSGI bundles and their associated configuration are managed. The CRXDE Lite content repository browser becomes only accessible on non-production environment types. A subset of the Web Console functionalities that developers require, especially when it comes to diagnostics and status purposes, is made available via a new developer console.
Also, one of the most common requirements for developers is quick access to the log files of the various environments. With [!DNL AEM Cloud Service], the log files of the different nodes in the Author, Publish are made available via the Cloud Manager, either in the form of files that can be downloaded or via APIs for tailing the logs. Due to the clear separation of code and content, developers can leverage a particular process for updating content as part of a deployment. The typical use cases for mutable content are:
* Standard “default” content that is part of the customer project (e.g. folders, templates, workflows...)
* Search index definitions
* ACLs and permissions
* Service users and user groups
Set up your development environment, [Configure your CI/CD Pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html), and learn to [deploy your code](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html) on the environment. -->

### Authoring adaptiver Formulare {#local-development}

Wenn Sie eine [!DNL AEM Forms] as a Cloud Service-Umgebung einrichten und konfigurieren, richten Sie eigene Umgebungen für Entwicklung, Staging und Produktion ein. Richten Sie außerdem eine lokale Entwicklungsumgebung für schnelle Iterationen und Entwicklungsprozesse ein und konfigurieren Sie sie. Sie können das AEM SDK und das [!DNL AEM Forms]-Add-on-Funktionsarchiv herunterladen und einrichten, um eine lokale Entwicklungsumgebung für [!DNL Forms] as a Cloud Service bereitzustellen.  Detaillierte Anweisungen finden Sie unter [Einrichten einer lokalen Entwicklungsumgebung](setup-local-development-environment.md).

## Debugging {#debugging}

AEM as a Cloud Service wird auf einer skalierbaren Self-Service-Cloud-Infrastruktur ausgeführt. AEM Entwickler müssen verschiedene Facetten von AEM as a Cloud Service verstehen und debuggen, vom Erstellen und Bereitstellen bis hin zum Abrufen von Details zu laufenden AEM. Weitere Informationen finden Sie unter [Debugging von AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/overview.html).
