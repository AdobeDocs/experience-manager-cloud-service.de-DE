---
title: Assets Prime
description: Erfahren Sie mehr über die wichtigsten Aspekte von Assets Prime, wie z. B. die wichtigsten Vorteile, die Benutzertypen und ihre Berechtigungen.
feature: Asset Management
role: User, Admin
source-git-commit: f033efd954ea7f9d27a891bfb9c0226e9d9c1432
workflow-type: tm+mt
source-wordcount: '1073'
ht-degree: 3%

---

# [!DNL Assets] as a Cloud Service Prime  {#assets-prime}

| [Best Practices für die Suche](/help/assets/search-best-practices.md) | [Best Practices für Metadaten](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [Dynamic Media mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md) | [Entwicklerdokumentation zu AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

![AEM Assets Prime-Banner-Bild](/help/assets/assets/aem-assets-prime-package-banner.png)

Assets as a Cloud Service Prime includes a lightweight DAM that enables you to perform various key capabilities, such as:

* ****

* ****

* ****

* ****

* ****

* ****

* ****

* ****

[](/help/assets/assets-ultimate-overview.md)

This article provides an end-to-end workflow to enable Assets as a Cloud Service Prime.

## Assets as a Cloud Service Prime aktivieren{#enable-assets-prime}

Aktivieren Sie Assets Prime bei der Erstellung eines neuen Programms mit Cloud Manager. Führen Sie die folgenden Schritte aus:

1. Melden Sie sich als Systemadministrator bei Cloud Manager an. Stellen Sie sicher, dass Sie beim Anmelden die richtige Organisation auswählen.

   >[!NOTE]
   >
   >Ensure that you are added to the appropriate Cloud Manager product profile to add a new program. [](/help/onboarding/cloud-manager-introduction.md#role-based-permissions)

1. [Erstellen Sie ein neues Programm](/help/journey-onboarding/create-program.md).

   Wählen Sie beim Erstellen des neuen Programms auf der Registerkarte **[!UICONTROL Lösungen und Add-ons]** die Option **[!UICONTROL Assets Prime]**. Sie können auch **[!UICONTROL Assets Prime]** erweitern und **[!UICONTROL Content Hub]** auswählen, um [Content Hub](/help/assets/product-overview.md) für die Asset-Verteilung zu aktivieren.

   ![AEM Assets Ultimate](assets/aem-assets-prime.png)


1. Klicken Sie auf **[!UICONTROL Erstellen]** , um das Programm zu erstellen.

1. Klicken Sie auf die Programmkarte und dann auf **[!UICONTROL Umgebung hinzufügen]**.

1. ****

   ![](assets/aem-assets-prime-add-environment.png)

>[!NOTE]
>
>Assets Prime only allows you to create a production environment. The option to Add environment is no longer available once the production environment is created successfully.

Assets Prime is now enabled for Experience Manager Assets as a Cloud Service.

![](assets/aem-assets-prime-setup-complete.png)

System administrator is automatically entitled as AEM administrator and receives an email to navigate to Admin Console to manage product profiles.


Your AEM as a Cloud Service instance on Admin Console comprises the following product profiles:

* AEM Administrators

* AEM-Benutzende

* [AEM Assets Collaborator Users](#onboard-collaborator-users)

* [AEM Assets Power Users](#onboard-power-users)


![AEM Assets-Produktprofile](assets/aem-assets-product-profiles.png)

Sie können damit beginnen, Benutzer oder Benutzergruppen zu AEM Assets Collaborator-Benutzern und AEM Assets Power Users-Produktprofilen hinzuzufügen. Weitere Informationen finden Sie unter [Benutzer des AEM Assets-Mitwirkenden einbinden](#onboard-collaborator-users) und [Benutzer mit AEM Assets Power einbinden](#onboard-power-users).

`delivery`

![](assets/new-instance-content-hub.png)

>[!NOTE]
>
>`contenthub`

`author``publish`

`AEM Assets Limited Users`

![](assets/content-hub-product-profile.png)

You can start adding users or user groups to this product profile to provide them access to Content Hub.

>[!NOTE]
>
>`contenthub``Limited Users``delivery`

## Onboard AEM Assets Collaborator users {#onboard-collaborator-users}

AEM Assets Collaborator users can work with assets from Experience manager via integrations of Assets available to your organization in other Adobe products and non-Adobe applications, create and edit assets using built-in Adobe Express and Firefly leveraging professionally designed templates, brand kits, Adobe Stock assets, and so on, and access and leverage approved assets from your organization using AEM Assets Content Hub portal.

To onboard Collaborator users:

1. Access Experience Manager Assets product profiles by clicking the AEM as a Cloud Service product name in the list of products on Admin Console.

1. Click the production author instance for AEM as a Cloud Service:
   ![](assets/aem-cloud-service-instances.png)

1. Klicken Sie auf das Produktprofil Benutzer von Mitwirkenden und klicken Sie auf **[!UICONTROL Benutzer hinzufügen]** , um den Benutzer zum Produktprofil hinzuzufügen.
   ![Benutzerproduktprofil](assets/aem-assets-collaborator-user-permissions.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern.

Sie können auch auf die den Benutzern des Mitwirkenden zugewiesenen Dienste zugreifen und diese anzeigen, wie in der folgenden Abbildung dargestellt:

![](assets/aem-assets-collaborator-users.png)

Die Dienste `Adobe Express` und `AEM Assets Collaborator Users` sind standardmäßig aktiviert. Sie können den Umschalter entsprechend Ihren Anforderungen deaktivieren und aktivieren. Adobe empfiehlt jedoch, die für die Produktprofile aktivierten Standarddienste zu verwenden.

## Onboard AEM Assets Power-Benutzer {#onboard-power-users}

AEM Assets Power-Benutzer können über das AEM Assets Portal auf alle AEM Assets-Funktionen zugreifen, einschließlich der Verwaltung von Assets, Berechtigungen, Metadaten und der allgemeinen Verwaltung und Automatisierung digitaler Assets, der Arbeit mit Assets aus Experience Manager über Integrationen von Assets, die für Ihr Unternehmen in anderen Adobe- und Nicht-Adobe-Anwendungen verfügbar sind, der Erstellung und Bearbeitung von Assets mit integrierten Adobe Expressen und Firefly, mithilfe von professionell gestalteten Vorlagen, Markenkits, Adobe Stock-Assets usw. sowie des Zugriffs und der Nutzung genehmigter Assets aus Ihrem Unternehmen.

So integrieren Sie Power-Benutzer:

1. Greifen Sie auf Experience Manager Assets-Produktprofile zu, indem Sie in der Produktliste auf Admin Console auf den AEM as a Cloud Service-Produktnamen klicken.

1. Click the production author instance for AEM as a Cloud Service:
   ![](assets/aem-cloud-service-instances.png)

1. ****
   ![](assets/aem-assets-power-user-permissions.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern.

You can also access and view the services assigned to Power users, as depicted in the following image:

![](assets/aem-assets-power-users.png)

`Adobe Express``AEM Assets Power Users` You can turn the toggle off and on, as per your requirements, however, Adobe recommends to use the default services enabled for the product profiles.
