---
title: Konfigurieren von vorkonfigurierten Microsoft Dynamics 365- und Salesforce-Formulardatenmodellen für adaptive Formulare
description: Erfahren Sie, wie Sie Microsoft Dynamics 365 und Salesforce mit adaptiven Formularen integrieren.
exl-id: 2a43b2db-2dfb-4c79-88be-ea770b44dac1
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '936'
ht-degree: 100%

---

# Konfigurieren von [!DNL Microsoft Dynamics 365] und [!DNL Salesforce]-Cloud-Services {#configure-azure-storage}

[[!DNL Experience Manager Forms] Data Integration](data-integration.md) bietet [!DNL Microsoft Dynamics 365] und [!DNL Salesforce]-Cloud-Services zur Integration adaptiver Formulare in vordefinierte Formulardatenmodelle. Die adaptiven Formulare können dann mit [!DNL Microsoft Dynamics 365]- und [!DNL Salesforce]-Servern interagieren, um Geschäfts-Workflows zu ermöglichen. Zum Beispiel:

* Schreiben von Daten in [!DNL Microsoft Dynamics 365] und [!DNL Salesforce] bei Übermittlung von adaptiven Formularen
* Schreiben von Daten in [!DNL Microsoft Dynamics 365] und [!DNL Salesforce] durch benutzerdefinierte Entitäten, die im Formulardatenmodell definiert sind, und umgekehrt
* Abfragen eines [!DNL Microsoft Dynamics 365]- und [!DNL Salesforce]-Servers nach Daten und Befüllen adaptiver Formulare
* Lesen von Daten vom [!DNL Microsoft Dynamics 365]- und [!DNL Salesforce]-Server

[!DNL Microsoft Dynamics 365]- und [!DNL Salesforce]-Cloud-Services und Formulardatenmodelle sind vorkonfiguriert auf dem [!DNL AEM Forms]-Server verfügbar, nachdem Sie [ein Entwicklungsprojekt für Forms auf der Grundlage des Experience Manager-Archetyps eingerichtet haben](setup-local-development-environment.md##forms-cloud-service-local-development-environment).

>[!NOTE]
>
>Microsoft Dynamics 365- und [!DNL Salesforce]-Cloud-Services und Formulardatenmodelle sind nur dann vorkonfiguriert verfügbar, wenn Sie ein [!DNL Experience Manager Forms] as a [!DNL Cloud Service]-Projekt einrichten, das auf [AEM-Archetyp 30](https://github.com/adobe/aem-project-archetype/releases/tag/aem-project-archetype-30) oder höher basiert.

## Konfigurieren von [!DNL Salesforce]-Cloud-Services {#configure-salesforce-cloud-service}

Stellen Sie vor dem Konfigurieren von [!DNL Salesforce]-Cloud-Services sicher, dass Sie die folgenden Aufgaben ausführen:

* [Erstellen Sie eine verbundene OAuth-fähige  [!DNL Salesforce] Anwendung](https://help.salesforce.com/s/articleView?id=sf.connected_app_create_api_integration.htm&amp;type=5). Wenn Sie die verbundene [!DNL Salesforce]-Anwendung erstellen, geben Sie die Callback-URL im folgenden Format an:

   ```
   https://'[server]:[port]'/libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices.html
   ```

   Server und Port beziehen sich auf den Host-Namen und die Port-Nummer des [!DNL AEM Forms]-Servers.

* Geben Sie beim Erstellen der verbundenen [!DNL Salesforce]-Anwendung `full` und `offline_access` als Werte für den OAuth-Umfang an.

* Notieren Sie sich die Werte für die Client-ID (als Consumer Key bezeichnet) und das Client-Geheimnis (als Consumer Secret bezeichnet) für die verbundene Anwendung.

Führen Sie die folgenden Schritte aus, um den [!DNL Salesforce]-Cloud-Service zu konfigurieren:

1. Gehen Sie in der [!DNL AEM Forms]-Autoreninstanz zu **[!UICONTROL Tools]** ![hammer](assets/hammer.png) > **[!UICONTROL Cloud-Services]** > **[!UICONTROL Data Sources]**. Die Liste der verfügbaren Wrapper-Ordner enthält einen Ordner mit dem Titel, der beim [Erstellen des AEM-Archetyp-Projekts](setup-local-development-environment.md##forms-cloud-service-local-development-environment) für `DappTitle` angegeben wurde.
1. Tippen Sie auf den Ordnernamen, wählen Sie **[!UICONTROL Salesforce Cloud Config]** aus, und tippen Sie auf **[!UICONTROL Eigenschaften]**.
1. Auf der Registerkarte **[!UICONTROL Authentifizierungseinstellungen]**:
   1. Geben Sie die [!DNL Salesforce]-Domain-URL im Feld **[!UICONTROL Host]** an. Beispiel: [Domain-name].my.salesforce.com.
   1. Geben Sie die Client-ID (als Consumer Key bezeichnet) und das Client-Geheimnis (als Consumer Secret bezeichnet) für die verbundene Anwendung an.
   1. Geben Sie **full offline_access** (`full`- und `offine_access` -Werte, durch ein Leerzeichen getrennt) im Feld **[!UICONTROL Autorisierungsumfang]** an.
   1. Tippen Sie auf **[!UICONTROL Verbindung zu OAuth herstellen]**. Sie werden zur Anmeldungsseite von [!DNL Microsoft Dynamics] umgeleitet.
   1. Melden Sie sich mit Ihren [!DNL Salesforce]-Anmeldeinformationen an und lassen Sie zu, dass die Cloud-Service-Konfiguration eine Verbindung zum [!DNL Salesforce]-Service herstellt. Wenn die Verbindung erfolgreich hergestellt wurde, werden Sie zur Seite „[!DNL Salesforce]-Cloud-Service-Konfiguration“ weitergeleitet, auf der eine Erfolgsmeldung angezeigt wird.
1. Tippen Sie auf **[!UICONTROL Speichern und schließen]**, um die Konfiguration abzuschließen.

### Zugreifen auf das vorkonfigurierte [!DNL Salesforce]-Formulardatenmodell

Ein vorkonfiguriertes [!DNL Salesforce]-Formulardatenmodell ist auf dem [!DNL AEM Forms]-Server verfügbar, nachdem Sie [ein Entwicklungsprojekt für Forms basierend auf dem Experience Manager-Archetyp eingerichtet haben](setup-local-development-environment.md##forms-cloud-service-local-development-environment).

Um auf das Formulardatenmodell zuzugreifen, gehen Sie zu **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Datenintegrationen]**. Die Liste der verfügbaren Ordner enthält einen Ordner mit dem Titel, der beim [Erstellen des AEM-Archetyp-Projekts](setup-local-development-environment.md##forms-cloud-service-local-development-environment) für `DappTitle` angegeben wurde. Tippen Sie auf den Ordnernamen, wählen Sie das **[!UICONTROL Salesforce-Datenmodell]** aus, und tippen Sie auf das Symbol „Bearbeiten“ ![Bearbeiten](assets/edit.png), um das Formulardatenmodell anzuzeigen.

Nach der Konfiguration des [[!DNL Salesforce] Cloud Config-Services](#configure-salesforce-cloud-service) können Sie adaptive Formulare mit dem vordefinierten [!DNL Salesforce]-Datenmodell integrieren.

## Konfigurieren von [!DNL Microsoft Dynamics 365]-Cloud-Services {#configure-dynamics-cloud-service}

Stellen Sie vor dem Konfigurieren des [!DNL Microsoft Dynamics 365]-Cloud-Services sicher, dass Sie die folgenden Aufgaben ausführen:

* [Registrieren Sie eine Anwendung für [!DNL Microsoft Dynamics 365] mit Azure Active Directory](https://docs.microsoft.com/de-de/powerapps/developer/data-platform/walkthrough-register-app-azure-active-directory). Wenn Sie die verbundene [!DNL Microsoft Dynamics 365]-Anwendung erstellen, geben Sie die Antwort-URLs im folgenden Format an:

   ```
   https://'[server]:[port]'/libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices.html
   ```

   Server und Port beziehen sich auf den Host-Namen und die Port-Nummer des [!DNL AEM Forms]-Servers.

* Notieren Sie sich die Werte für die Client-ID (die auch als Anwendungs-ID bezeichnet wird) und das Client-Geheimnis für die verbundene Anwendung.

Führen Sie die folgenden Schritte aus, um den [!DNL Microsoft Dynamics 365]-Cloud-Service zu konfigurieren:

1. Gehen Sie in der [!DNL AEM Forms]-Autoreninstanz zu **[!UICONTROL Tools]** ![hammer](assets/hammer.png) > **[!UICONTROL Cloud-Services]** > **[!UICONTROL Data Sources]**. Die Liste der verfügbaren Wrapper-Ordner enthält einen Ordner mit dem Titel, der beim [Erstellen des AEM-Archetyp-Projekts](setup-local-development-environment.md##forms-cloud-service-local-development-environment) für `DappTitle` angegeben wurde.
1. Tippen Sie auf den Ordnernamen, wählen Sie **[!UICONTROL Microsoft Dynamics 365 Cloud Config]** aus, und tippen Sie auf **[!UICONTROL Eigenschaften]**.
1. Auf der Registerkarte **[!UICONTROL Authentifizierungseinstellungen]**:
   1. Geben Sie den Wert für das Feld **[!UICONTROL Service-Stamm]** ein. Wechseln Sie zur Dynamics-Instanz und navigieren Sie zu [Entwickler-Ressourcen](https://docs.microsoft.com/de-de/powerapps/developer/data-platform/view-download-developer-resources), um den Wert für das Feld „Service-Stamm“ anzuzeigen. Zum Beispiel: `https://<tenant-name>.dynamics.com/api/data/v9.1/`
   1. Geben Sie die Client-ID (als Anwendungs-ID bezeichnet) und das Client-Geheimnis für die verbundene Anwendung an.
   1. Ersetzen Sie `{tenant}` durch eine Mandantenkennung in den Feldern **[!UICONTROL OAuth-URL]**, **[!UICONTROL Aktualisierungstoken-URL]** und **[!UICONTROL Zugriffstoken-URL]**.
   1. Sie müssen die Dynamics-Instanz-URL im Feld **[!UICONTROL Ressource]** angeben, um [!UICONTROL Microsoft Dynamics] mit einem Formulardatenmodell zu konfigurieren. Verwenden Sie die Service-Stamm-URL, um die URL der Dynamics-Instanz abzuleiten. Zum Beispiel `https://<tenant-name>.dynamics.com`.

   1. Geben Sie die `openid` im Feld **[!UICONTROL Autorisierungsumfang]** für den Autorisierungsprozess in [!DNL Microsoft Dynamics 365] an.
   1. Melden Sie sich mit Ihren [!DNL Microsoft Dynamics 365]-Anmeldeinformationen an und lassen Sie zu, dass die Cloud-Service-Konfiguration eine Verbindung zum [!DNL Microsoft Dynamics 365]-Service herstellt. Wenn die Verbindung erfolgreich hergestellt wurde, werden Sie zur Seite „[!DNL Microsoft Dynamics 365]-Cloud-Service-Konfiguration“ weitergeleitet, auf der eine Erfolgsmeldung angezeigt wird.
1. Tippen Sie auf **[!UICONTROL Speichern und schließen]**, um die Konfiguration abzuschließen.

### Zugreifen auf das vorkonfigurierte [!DNL Microsoft Dynamics 365]-Formulardatenmodell

Ein vorkonfiguriertes [!DNL Microsoft Dynamics 365]-Formulardatenmodell ist auf dem [!DNL AEM Forms]-Server verfügbar, nachdem Sie [ein Entwicklungsprojekt für Forms basierend auf dem Experience Manager-Archetyp eingerichtet haben](setup-local-development-environment.md##forms-cloud-service-local-development-environment).

Um auf das Formulardatenmodell zuzugreifen, gehen Sie zu **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Datenintegrationen]**. Die Liste der verfügbaren Ordner enthält einen Ordner mit dem Titel, der beim [Erstellen des AEM-Archetyp-Projekts](setup-local-development-environment.md##forms-cloud-service-local-development-environment) für `DappTitle` angegeben wurde. Tippen Sie auf den Ordnernamen, wählen Sie das **[!UICONTROL Microsoft Dynamics 365-Datenmodell]** aus, und tippen Sie auf das Symbol „Bearbeiten“ ![Bearbeiten](assets/edit.png), um das Formulardatenmodell anzuzeigen.

Nach der Konfiguration des [[!DNL Microsoft Dynamics 365] Cloud Config-Services](#configure-dynamics-cloud-service) können Sie adaptive Formulare mit dem vordefinierten [!DNL Microsoft Dynamics 365]-Datenmodell integrieren.
