---
title: Wie richte ich eine  [!DNL AEM Forms]  as a Cloud Service-Umgebung ein?
description: Erfahren Sie, wie Sie eine  [!DNL AEM Forms]  as a Cloud Service-Umgebung einrichten und konfigurieren.
role: Admin, Developer, User
feature: Adaptive Forms
exl-id: 42f53662-fbcf-4676-9859-bf187ee9e4af
source-git-commit: 81951a9507ec3420cbadb258209bdc8e2b5e2942
workflow-type: tm+mt
source-wordcount: '610'
ht-degree: 100%

---

# Einstieg in [!DNL AEM Forms] as a Cloud Service {#overview}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/install-aem-forms/osgi-installation/installing-configuring-aem-forms-osgi.html?lang=de) |
| AEM as a Cloud Service | Dieser Artikel |


## Bestimmung von Benutzertypen {#personas-aem-forms-project}

<!-- When you sign up for the service, Adobe creates an Organization identifier for your company in the Adobe Identity Management System (IMS), where your users and their permissions can be managed. So, --> Legen Sie vor dem Einstieg in eine Adobe Experience Manager (AEM) Forms as a Cloud Service-Umgebung Rollen fest und strukturieren Sie ein Team für Ihr Projekt. Eine typisches Projekt-Team in [!DNL AEM Forms] verfügt über die folgenden Rollen:

* **Anwendererlebnis(UX)-Designer**: Designerinnen und Designer für das Anwendererlebnis (UX) definieren Stil, Layout und Branding für [!DNL AEM Forms]-Assets.

* **Formular-Fachkraft**: Eine Formular-Fachkraft erstellt adaptive Formulare, Designs und Vorlagen gemäß den Stil-, Layout- und Branding-Definitionen der UX-Designerin bzw. des UX-Designers. Außerdem erstellt und integriert die Fachkraft adaptive Formulare mit einem Formulardatenmodell (FDM) und AEM-Workflows. Eine Formular-Fachkraft führt in der Regel Frontend-Aufgaben aus.

* **Formularentwickelnde**: Formularentwickelnde erstellen eine benutzerdefinierte Formularlösung. Eine Formularentwicklerin bzw. ein Formularentwickler entwickelt in der Regel Backend-Anwendungen wie benutzerdefinierte Komponenten, AEM-Workflows, Vorbefüllungs-Services und mehr.

* **AEM-Administrator**: Der AEM-Administrator unterstützt bei der Konfiguration insgesamt, z. B. beim Einrichten von Benutzerinnen und Benutzern, beim Härten der Umgebung, beim Konfigurieren von Datenquellen, beim Konfigurieren von E-Mail-Nachrichten und bei Software von Drittanbietern. AEM-Admins unterstützen auch die Integration von Lösungen wie Adobe Analytics, Adobe Target und Adobe Sign.

* **Endbenutzende**: Endbenutzende interagieren mit dem veröffentlichten Formular und senden es ab, unterzeichnen gesendete Formulare, verfolgen gesendete Anträge über ein Web-Portal und empfangen personalisierte Mitteilungen.

<!-- While onboarding to the service, assign the following AEM groups to [!DNL AEM Forms] as a Cloud Service based on their role:

| User type | AEM group |
|---|---|
| Form Practitioner | forms-users (AEM Forms Users), template-authors, workflow-user, workflow-editors, and fdm-author  |
| UX Designer| forms-users, template-authors|
| End-User| <ul> <li>When a user must login to view and submit an Adaptive Form, add such users to forms-users group. </li> <li>When no user authentication is required to access Adaptive Forms, do not assign any group to such users. </li> </ul>| -->

## Einführung in den Service {#onboarding}

* [Lernen Sie](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/overview.html?lang=de) [!DNL Adobe Experience Manager] as a Cloud Service kennen.

* (Nur für Sandboxes) Nach der Einführung in den Service [erstellen](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/using/pipelines/production-pipelines.html?lang=de) und [nutzen](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/using/code-deployment.html?lang=de) Sie Produktions- und Nicht-Produktions-Pipelines. Dadurch wird Ihre Umgebung um die neuesten Funktionen von [!DNL AEM Forms] as a Cloud Service erweitert.

Sie können Forms as a Cloud Service verwenden, um ein adaptives Formular (digitale Registrierung) zu erstellen oder eine Kundenkommunikation zu generieren. Führen Sie nach Abschluss des [Onboardings](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/overview.html?lang=de) bei [!DNL Adobe Experience Manager] as a Cloud Service eine der folgenden Aktionen aus, um die Funktionen für die digitale Registrierung oder die Kundenkommunikation zu aktivieren. <!--You can also enable both the features-->:

1. Melden Sie sich bei Cloud Manager an und öffnen Sie Ihre AEM Forms as a Cloud Service-Instanz.
1. Öffnen Sie die Option „Programm bearbeiten“ und navigieren Sie zur Registerkarte „Lösungen und Add-ons“:

   * Wenn Sie über eine Produktionsumgebung verfügen, wählen Sie die Option **[!UICONTROL Forms – Kommunikation]** aus, um das Add-On „Forms – Digitale Anmeldung“ und „Forms – Kommunikation“ zu aktivieren.

     ![Kommunikationen](assets/communications.png)

   <!-- If you have already enabled the **[!UICONTROL Forms - Digital Enrollment]** option, then select the **[!UICONTROL Forms - Communications Add-On]** option. ![Addon](assets/add-on.png) -->

   * Wenn Sie über eine Sandbox-Umgebung verfügen, wählen Sie **[!UICONTROL Forms]** aus, um das Add-On „Forms – Digitale Anmeldung“ und „Forms – Kommunikation“ zu aktivieren.

     ![Auswahl von „Forms – Digitale Anmeldung“](assets/forms-digital-enrollment1.png)


1. Klicken Sie auf **[!UICONTROL Aktualisieren]**.
1. Führen Sie die Build-Pipeline aus. Nachdem die Build-Pipeline erfolgreich ausgeführt wurde, wird die ausgewählte Lösung für Ihre Umgebung aktiviert.

>[!NOTE]
>
> Um APIs zur Dokumentbearbeitung zu aktivieren und zu konfigurieren, fügen Sie die folgende Regel zur [Dispatcher-Konfiguration](setup-local-development-environment.md#forms-specific-rules-to-dispatcher) hinzu:
>
> `# Allow Forms Doc Generation requests`
> `/0062 { /type "allow" /method "POST" /url "/adobe/forms/assembler/*" }`

## Konfigurieren von Benutzern {#config-users}

Nach Abschluss der Einführung melden Sie sich bei Ihrer [!DNL AEM Forms] as a Cloud Service-Umgebung an, öffnen Autoren- und Veröffentlichungsinstanz und fügen den formularspezifischen [AEM-Gruppen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/aem-users-groups-and-permissions.html?lang=de#accessing) Benutzer je nach Benutzertyp hinzu. Die folgende Tabelle zeigt die formularspezifischen AEM-Gruppen, die standardmäßig verfügbar sind, sowie die entsprechenden Benutzertypen. Die Tabelle enthält außerdem den AEM-Instanztyp für jeden Benutzertyp:

| Benutzertypen (Personas) | Benutzergruppen | AEM-Instanz |
|---|---|---|
| Formularanwender/Formularentwickler | <ul> <li> [!DNL forms-users] </li><li> [!DNL template-author] </li><li> [!DNL workflow-users] </li><li> [!DNL workflow-editors] </li><li> [!DNL fdm-authors] </li></ul> | Autoreninstanz |
| User Experience(UX)-Designer | <ul> <li> [!DNL forms-users]</li><li> [!DNL template-author] </li></ul> | Autoreninstanz |
| AEM-Administrator | <ul> <li>[!DNL aem-administrators],</li> <li>[!DNL fd-administrators] </li> </ul> | Autoren- und Veröffentlichungsinstanz |
| Endanwender | <ul> <li>Wenn das Anzeigen und Übermitteln eines adaptiven Formulars nur für angemeldete Benutzende möglich sein soll, fügen Sie diese Benutzenden der Gruppe [!DNL forms-users] hinzu. </li> <li>Wenn für den Zugriff auf adaptive Formulare keine Benutzerauthentifizierung erforderlich ist, weisen Sie diesen Benutzern keine Gruppe zu. </li> </ul> | Autoren- und Veröffentlichungsinstanz |

Weitere Informationen zu formularspezifischen AEM-Gruppen und entsprechenden Berechtigungen finden Sie unter [Gruppen und Berechtigungen](forms-groups-privileges-tasks.md).

<!-- You can also create  [user groups](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/aem-users-groups-and-permissions.html?lang=de#accessing) specific  to your organization, assign policies, and [users](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/aem-users-groups-and-permissions.html?lang=de#accessing) to the groups. The policies help control permissions of the users that are part of the group. For information a -->

## Nächster Schritt {#next-steps}

[Einrichten einer lokalen AEM-Entwicklungsumgebung](setup-local-development-environment.md). Sie können eine lokale Entwicklungsumgebung verwenden, um ein adaptives Formular und zugehörige Assets (Designs, Vorlagen, benutzerdefinierte Sendeaktionen, Vorbefüllungs-Service usw.) zu erstellen. Und Sie können [PDF-Formulare in adaptive Formulare](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/introduction.html?lang=de) konvertieren, ohne sich bei einer Cloud-Entwicklungsumgebung anzumelden.

<!-- ### Business unit and end-users {#business-unit-and-end-users}

| Role| Organization| Description|
|-----|-------|-----|
| UX Designer                  | Customer/System Integrator/Partner | Defines user experience design (style, layout, branding) as per organizational requirements for Adaptive Forms to allow AEM Forms practitioners to design the corresponding themes and templates.                                     |
| Forms Practitioner           | Customer                           | Authors Adaptive Forms, creates Form Data Model integrations, and creates business workflows using the Experience Manager Workflows. Typically undertakes the front-end work.                                                         |
| Business Executive - Digital | Customer                           | Responsible for business unit's product marketing strategy and revenues, main business stakeholders for digital use cases, solutions, and service offerings for the end-users, signs off on the use case implementation and delivery. |
| Customer Experience Lead     | Customer                           | Business user persona. Authors, personalizes and updates Adaptive Forms fields/rules/styling, identifies, and prioritizes business needs. Validates business use-case with SI/Partner developers/practitioners during UAT.            |
| Forms Back-Office User       | Customer                           | End-user internal to organization filling forms, participating in back-office Forms workflows such as review/approval of applications and so on.                                                                                            |
| Forms End-User               | External to customer               | Interacts with and submits the published form as end customer or citizen, signs submitted forms, tracks her applications through web portal, receives personalized interactive communications.                                        |

### Project team {#project-team}

| Role | Org | Description|
|-----|-----|-----|
| Experience Manager Administrator | System Integrator /Partner/Customer | Helps with overall installation, configures SSL certificates, configures data sources, email, and other third-party software, integrations like Adobe Analytics, Adobe Target, Automated Forms Conversion Services with Experience Manager instance. |
| Project Manager                  | System Integrator /Partner/Customer | Converts customer use-case into technical requirements, manages schedule/cost/scope for overall project.                                                                                                                                             |
| Product Owner                    | System Integrator /Partner/Customer | Prioritizes and evaluates scrum team's work for high-quality delivery on time.                                                                                                                                                                       |
| Scrum Master                     | System Integrator /Partner/Customer | Ensures agile values and processes in place to deliver on defined requirements as per prioritization by PO.                                                                                                                                          |
| Infrastructure / security expert | System Integrator /Partner/Customer | Provisions and configures best possible infrastructure, security controls and infra processes to address current and projected RASP requirements.                                                                                                    |
| Technical Architect              | System Integrator /Partner/Customer | Provides best high-level architecture and infrastructure guidance for use-case implementation and address RASP (Reliability, Availability, Scalability, and Performance) and security challenges.                                                    | -->

<!-- ## Onboard to the service {#onboarding}

[Onboard](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/home.html?lang=de) to the [!DNL Adobe Experience Manager] as a Cloud Service. 

After you onboard the service, configure a [local development environment](setup-local-development-environment.md). 

Administrators are responsible for managing Adobe software and services for their organization. Administrators grant access to developers in their organization to connect and use your [!DNL AEM Forms] as a Cloud Service program. When an administrator is provisioned for an organization, the administrator receives an email with title 'You now have administrator rights to manage Adobe software and services for your organization'. If you are an administrator, check your mailbox for email with previously mentioned title and proceed to [add users](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html?lang=de#onboarding-users-in-admin-console) by way of IMS and assign [form-specific groups](forms-groups-privileges-tasks.md) to users based on their role.

## Next step {#next-steps} -->

<!-- ## Prerequisites {#prerequisites}

If you are new to AEM as a cloud service, contact your Adobe representative to create an organization identifier for your company in the Adobe Identity Management System (IMS). Once Adobe has created an organization for your company, your designated administrator is added as the first member of the organization. The administrator can setup an [!DNL AEM Forms] as a Cloud Service instance. 

## Onboard and set up a new environment {#onboard-and-setup-a-new-environment}

Log in to Cloud Manager and create a program. After the program is ready, create environments, add developers or users to environments, and run the pipeline to get the latest version of [!DNL AEM Forms] as a Cloud Service and start developing for your environment. The detailed steps are:

1. Contact your Adobe representative to create an organization identifier for your company in the Adobe Identity Management System (IMS) and provide access to an administrator in your organization.
1. Configure [Automated Forms Conversion Service](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/configure-service.html?lang=de). After a configuration is complete, a profile for Automated Forms Conversion Service is available in [Admin Console](https://adminconsole.adobe.com/).

    If the service is not available, log in to [Admin Console](https://adminconsole.adobe.com/). Use Adobe ID of administrator provisioned to use Automated Forms Conversion Service to login. Do not use any other ID or Federated ID to login.
    1. Click **[!UICONTROL Automated Forms Conversion Service]** option.
    1. Click **[!UICONTROL New Profile]** in the Products tab.
    1. Specify **[!UICONTROL Name]**, **[!UICONTROL Display Name]**, and **[!UICONTROL Description]** for the profile. Click **[!UICONTROL Done]**. A profile is created. 
1. Log in to [Cloud Manager](https://experience.adobe.com/#/@marketinghub/experiencemanager) and [create a program](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/creating-a-program.html) for your organization.
1. [Create environments](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html?lang=de#adding-environments) within your program.
1. Log in to [Admin console](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/what-is-required/add-users-roles.html) and add developers or users to your organization.
1. Run the [build pipeline](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-manager/using/how-to-use/deploying-code.html). It brings latest [!DNL Experience Manager Forms] as a Cloud Service features to your environment.
1. [Start developing](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) and creating Adaptive Forms on [!DNL Experience Manager Forms] as a Cloud Service environment.
1. Configure the [local development environment](setup-local-development-environment.md) for rapid development

## Configure dispatcher caching {#caching}

You can make dispatcher caching related configuration changes to code on your local development instance and deploy the changes to your [!DNL AEM Forms] as a Cloud Service instance. For details, see [update dispatcher configuration](setup-local-development-environment.md).
 -->
