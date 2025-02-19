---
title: Konfigurieren von vorkonfigurierten Microsoft Dynamics 365-Formulardatenmodellen für adaptive Forms
description: Erfahren Sie, wie Sie Microsoft Dynamics 365 mit Adaptive Forms integrieren.
feature: Adaptive Forms, Form Data Model
role: User, Developer
exl-id: 29ee324c-cd4c-403b-bb3d-b1eda8e8ad88
source-git-commit: 76301ca614ae2256f5f8b00c41399298c761ee33
workflow-type: tm+mt
source-wordcount: '915'
ht-degree: 16%

---


# Konfigurieren von Microsoft® Dynamics 365 für AEM Forms

Adobe Experience Manager Forms-Datenintegration bietet eine Cloud-Service-Konfiguration für die Integration von Formularen mit dem Microsoft Dynamics-Server. Dies ermöglicht Ihnen das Erstellen von Formulardatenmodellen (FDM) basierend auf den im Microsoft Dynamics-Service definierten Entitäten, Attributen und Services. Das Formulardatenmodell (FDM) kann verwendet werden, um adaptive Forms zu erstellen, die mit dem Microsoft Dynamics-Server interagieren, um Unternehmens-Workflows zu ermöglichen. Zum Beispiel:
* Abfragen eines Microsoft Dynamics-Servers nach Daten und Auffüllen adaptiver Forms.
* Schreiben von Daten in Microsoft Dynamics bei Übermittlung von adaptiven Formularen
* Schreiben von Daten in Microsoft Dynamics durch benutzerdefinierte Entitäten, die im Formulardatenmodell (FDM) definiert sind.

AEM as a Cloud Service bietet verschiedene vordefinierte Übermittlungsaktionen für die Verarbeitung von Formularübermittlungen. Mehr über diese Optionen erfahren Sie in dem Artikel [Übermittlungsaktion für adaptive Formulare](/help/forms/configure-submit-actions-core-components.md).

<!-- 
[[!DNL Experience Manager Forms] Data Integration](data-integration.md) provides [!DNL Microsoft&reg; Dynamics 365] Cloud Services to integrate Adaptive Forms with out of the box Form Data Model (FDM). The Adaptive Forms can then interact with [!DNL Microsoft&reg; Dynamics 365] servers to enable business workflows. For example:

* Write data into [!DNL Microsoft&reg; Dynamics 365] on Adaptive Form submission.
* Write data in [!DNL Microsoft&reg; Dynamics 365] through custom entities defined in Form Data Model (FDM) and conversely.
* Query [!DNL Microsoft&reg; Dynamics 365]server for data and prepopulate Adaptive Forms.
* Read data from [!DNL Microsoft&reg; Dynamics 365] server.

[!DNL Microsoft&reg; Dynamics 365] cloud services and Form Data Model (FDM) are available out of the box on the [!DNL AEM Forms] Server after you [set up a development project for Forms based on Experience Manager archetype](setup-local-development-environment.md#forms-cloud-service-local-development-environment).

>[!NOTE]
>
>Microsoft&reg; Dynamics 365 cloud services and Form Data Model (FDM) are available out of the box only if you set up an [!DNL Experience Manager Forms] as a [!DNL Cloud Service] project based on [AEM Archetype 30](https://github.com/adobe/aem-project-archetype/releases/tag/aem-project-archetype-30) or later.-->

## Voraussetzungen

Stellen Sie vor der Integration von [!DNL Microsoft® Dynamics 365] mit AEM Forms as a Cloud Service sicher, dass Sie die folgenden Schritte ausgeführt haben:


1. **Einrichten des Kontos in Microsoft Dynamics 365**

   Gehen Sie wie im Video beschrieben vor, um ein Microsoft Dynamics 365-Konto einzurichten. In diesem Video wird zu Demonstrationszwecken ein Testkonto erstellt.

   >[!VIDEO](https://video.tv.adobe.com/v/3444389/)

1. **Erstellen Sie ein Konto im Power Platform Admin Center**
Erstellen Sie ein Konto im **Power Platform Admin Center**, um:
   * Dataverse hinzufügen
   * Aktivieren von Microsoft Dynamics 365-Anwendungen

   Gehen Sie wie im Video beschrieben vor, um ein Konto im Power Platform Admin Center zu erstellen. In diesem Video wurde zu Demonstrationszwecken ein Testkonto erstellt.

   >[!VIDEO](https://video.tv.adobe.com/v/3444388)

1. **Registrieren einer Anwendung für [!DNL Microsoft® Dynamics 365] in Azure Active Directory**

   Gehen Sie wie im Video beschrieben vor, um eine Anwendung für die [!DNL Microsoft® Dynamics 365] in Azure Active Directory zu registrieren.

   >[!VIDEO](https://video.tv.adobe.com/v/3444369/dynamics365integration-microsoftdynamics-apiaccess-azuread-appregistration)

   >[!NOTE]
   >
   > * Um die verbundene [!DNL Microsoft® Dynamics 365]-Anwendung zu erstellen, wählen Sie **Web** als Plattform aus und geben Sie den **Umleitungs-URI** im folgenden Format an: `https://'[server]:[port]'/libs/fd/fdm/gui/components/admin/fdmcloudservice/fdm.html`.
   > * Speichern Sie die Client-ID (auch als Anwendungs-ID bezeichnet) und das Client-Geheimnis, um später darauf Bezug nehmen zu können.

## Forms mit Microsoft® Dynamics 365 verbinden

Nachdem Sie die oben genannten Voraussetzungen konfiguriert haben, können Sie mit der Integration von Adaptive Forms in Microsoft® Dynamics 365 fortfahren. Gehen Sie wie folgt vor, um bei der Übermittlung des Formulars Daten an Microsoft® Dynamics 365 zu senden:

[1. Konfigurieren der Cloud Service-Konfiguration für Microsoft Dynamics](#1-configure-cloud-service-configuration-for-microsoft-dynamics)

[2. Erstellen eines Formulardatenmodells (FDM)](#2-create-form-data-model-fdm)

### 1. Konfigurieren der Cloud Service-Konfiguration für Microsoft Dynamics

>[!VIDEO](https://video.tv.adobe.com/v/3444370/cloudconfiguration-dataintegration-adobeexperiencemanager-aemforms-microsoftdynamics)

Führen Sie die folgenden Schritte aus, um die [!DNL Microsoft® Dynamics 365] Cloud Service-Konfiguration zu konfigurieren:

1. Navigieren Sie auf [!DNL AEM Forms] Autoreninstanz zu **[!UICONTROL Tools]** ![hammer](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Datenquellen]**.

   ![Cloud Data-Source auswählen](/help/forms/assets/dynamics-data-source.png)
1. Wählen Sie einen Konfigurations-Container aus. Die Konfiguration wird im ausgewählten Konfigurations-Container gespeichert.
1. Klicken Sie auf **[!UICONTROL Erstellen]**.

   ![Erstellen einer Cloud-Konfiguration](/help/forms/assets/dynamics-select-configuration.png)

   Der Konfigurationsassistent **Erstellen einer Daten** Source-Konfiguration“ wird angezeigt.

   ![Konfigurationsassistent für Data Source erstellen](/help/forms/assets/dynamics-create-data-configuration.png)

1. Geben Sie **[!UICONTROL Titel]** und **[!UICONTROL Name]** an und wählen Sie **[!UICONTROL Diensttyp]** als **OData-Dienst**.
1. Klicken Sie auf **[!UICONTROL Weiter]**. Die **Authentifizierung** wird angezeigt.

   ![Registerkarte „Authentifizierung](/help/forms/assets/dynamics-authentication-tab.png)

1. Geben Sie den Wert für das Feld **[!UICONTROL Service-Stamm]** an.

   Wechseln Sie zu Ihrer Dynamics-Instanz im **Power Platform Admin Center** und navigieren Sie zu [Entwicklerressourcen](https://docs.microsoft.com/de-de/powerapps/developer/data-platform/view-download-developer-resources), um den Wert des **Dienststamms** anzuzeigen. Der **Web-API** Endpunkt) stellt den **Service-Stamm**-Wert für die Dynamics-Instanz dar, die Sie in adaptive Forms integrieren möchten. Die **Service-Stamm**-URL hat folgendes Format: `https://<tenant-name>.dynamics.com/api/data/v9.1/`

   ![Feld „Service-Stamm](/help/forms/assets/dynamics-service-root.png)

1. Wählen Sie **[!UICONTROL Authentifizierungstyp]** als **OAuth2.0** aus.
1. Geben Sie **Client-ID** (als Anwendungs-ID bezeichnet) und **Client-Geheimnis** für die verbundene Anwendung an.
Sie können die **Client-ID** und **Client-Geheimnis** aus der Azure Active Directory-Anwendung abrufen.

   ![Client-ID und Client-Geheimnis](/help/forms/assets/dynamics-azure-app-resgistration.png)

1. Geben Sie Folgendes in den Feldern **[!UICONTROL OAuth-]**, **[!UICONTROL Aktualisierungstoken-URL]** und **[!UICONTROL Zugriffstoken-URL]** an.
Sie können die **[!UICONTROL OAuth]**, **[!UICONTROL Aktualisierungstoken-URL]** und **[!UICONTROL Zugriffstoken-URL]** aus dem Abschnitt **Endpunkte** Ihrer Azure Active Directory-Anwendung abrufen.

   ![Azure-App-Endpunkte](/help/forms/assets/dynamics-azure-app-endpoints.png)

1. Geben Sie die `openid` im Feld **[!UICONTROL Autorisierungsumfang]** für den Autorisierungsprozess in [!DNL Microsoft® Dynamics 365] an.
1. Geben Sie die Dynamics-Instanz-URL im Feld **[!UICONTROL Ressource]** an, um [!DNL Microsoft® Dynamics 365] mit einem Formulardatenmodell (FDM) zu konfigurieren.
Sie können die **Umgebungs-URL** aus dem **Power Platform Admin Center** kopieren oder die Dynamics-Instanz-URL mithilfe der **Service-Stamm**-URL ableiten. Die Ressourcen-URL hat folgendes Format: `https://<tenant-name>.dynamics.com`.

   ![Power App-Ressourcenfeld](/help/forms/assets/dynamics-resource-field.png)

1. Melden Sie sich mit Ihren [!DNL Microsoft® Dynamics 365]-Anmeldeinformationen an und lassen Sie zu, dass die Cloud-Service-Konfiguration eine Verbindung zum [!DNL Microsoft® Dynamics 365]-Service herstellt. Wenn die Verbindung erfolgreich hergestellt wurde, werden Sie zur Seite „[!DNL Microsoft® Dynamics 365]-Cloud-Service-Konfiguration“ weitergeleitet, auf der eine Erfolgsmeldung angezeigt wird.
1. Wählen **[!UICONTROL Erstellen]**, um die Konfiguration zu speichern.

### 2. Erstellen eines Formulardatenmodells (FDM)

>[!VIDEO](https://video.tv.adobe.com/v/3444367/aemforms-adobeexperiencemanager-formdatamodel--dataintegration-digitalforms)

Sie können das Formulardatenmodell (FDM) mithilfe der erstellten [!DNL Microsoft® Dynamics 365]-Cloud-Konfiguration erstellen. Führen Sie die folgenden Schritte aus, um das Formulardatenmodell zu erstellen:

1. Navigieren Sie zu **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Datenintegrationen]**.
   ![Erstellen von Formulardatenmodellen](/help/forms/assets/dynamics-create-fdm.png)

1. Klicken Sie **[!UICONTROL Erstellen]** und wählen Sie **[!UICONTROL Formulardatenmodell]** aus.
   ![Formulardatenmodell auswählen](/help/forms/assets/dynamics-select-fdm.png)

   Der **„Formulardatenmodell erstellen** wird angezeigt.
1. Klicken Sie auf **[!UICONTROL Weiter]**.
1. Wählen Sie die erstellte Cloud-Konfiguration auf der Registerkarte **Datenquelle**.
   ![Cloud-Konfiguration auswählen](/help/forms/assets/dynamics-select-cloud-config.png)

1. Klicken Sie auf das Symbol ![Bearbeiten](assets/edit.png), um das Formulardatenmodell (FDM) anzuzeigen und zu konfigurieren.

Als Nächstes können Sie [Formulardatenmodell (FDM) konfigurieren](/help/forms/work-with-form-data-model.md#configure-services) und es in verschiedenen Anwendungsfällen für adaptive Formulare verwenden, z. B.:

* Befüllen eines adaptiven Formulars durch Abfragen von Informationen aus [!DNL Microsoft Dynamics]-Entitäten und -Diensten
* Aufrufen von [!DNL Microsoft Dynamics]-Server-Vorgängen, die in einem Formulardatenmodell (FDM) definiert sind, mithilfe von adaptiven Formularregeln
* Schreiben übermittelter Formulardaten in [!DNL Microsoft Dynamics]-Entitäten
* Sie können die Übermittlungsaktion für Formulardatenmodelle für ein adaptives Formular konfigurieren, um Daten an [!DNL Microsoft Dynamics] zu senden.

Anschließend können Sie die Option [Senden mit Formulardatenmodell (FDM)](/help/forms/using-form-data-model.md) in einem **adaptiven Formular** verwenden, um Daten aus Ihrem Formular an die konfigurierte [!DNL Microsoft® Dynamics 365] zu übertragen.


>[!MORELIKETHIS]
>
>* [Konfigurieren von Datenquellen für AEM Forms](/help/forms/configure-data-sources.md)
>* [Konfigurieren von Azure Storage für AEM-Formulare](/help/forms/configure-azure-storage.md)
>  [Hinzufügen des Formularportals zu einer AEM Sites-Seite](/help/forms/configure-forms-portal.md)
