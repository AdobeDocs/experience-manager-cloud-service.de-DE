---
title: Konfigurieren von vorkonfigurierten Salesforce-Formulardatenmodellen für adaptive Forms
description: Erfahren Sie, wie Sie Salesforce mit Adaptive Forms integrieren.
feature: Adaptive Forms, Form Data Model
role: User, Developer
source-git-commit: 3a12fff170f521f6051f0c24a4eb28a12439eec1
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 71%

---


# Konfigurieren von Salesforce für AEM Forms {#configure-azure-storage}

[[!DNL Experience Manager Forms] Datenintegration](data-integration.md) bietet [!DNL Salesforce] Cloud-Services zur Integration von Adaptive Forms mit dem vorkonfigurierten Formulardatenmodell (OOTB Form Data Model, FDM). Das adaptive Forms kann dann mit [!DNL Salesforce]-Servern interagieren, um Unternehmens-Workflows zu ermöglichen. Zum Beispiel:

* Schreiben von Daten in [!DNL Salesforce] bei Übermittlung von adaptiven Formularen.
* Schreiben von Daten in [!DNL Salesforce] durch benutzerdefinierte Entitäten, die im Formulardatenmodell (FDM) definiert sind, und umgekehrt.
* Abfragen eines [!DNL Salesforce]-Servers nach Daten und Auffüllen adaptiver Formulare.
* Lesen Sie Daten vom [!DNL Salesforce]-Server.

[!DNL Salesforce] Cloud-Services und das Formulardatenmodell (FDM) sind vorkonfiguriert auf dem [!DNL AEM Forms]-Server verfügbar, nachdem Sie [ein Entwicklungsprojekt für Forms auf der Grundlage des Experience Manager-Archetyps eingerichtet &#x200B;](setup-local-development-environment.md#forms-cloud-service-local-development-environment).

>[!NOTE]
>
>[!DNL Salesforce] Cloud-Services und das Formulardatenmodell (FDM) sind nur dann vorkonfiguriert verfügbar, wenn Sie ein [!DNL Experience Manager Forms] as a [!DNL Cloud Service]-Projekt einrichten, das auf [AEM-Archetyp 30](https://github.com/adobe/aem-project-archetype/releases/tag/aem-project-archetype-30) oder höher basiert.

## Konfigurieren von [!DNL Salesforce]-Cloud-Services {#configure-salesforce-cloud-service}

Stellen Sie vor dem Konfigurieren von [!DNL Salesforce]-Cloud-Services sicher, dass Sie die folgenden Aufgaben ausführen:

* [Erstellen Sie eine verbundene OAuth-fähige  [!DNL Salesforce] Anwendung](https://help.salesforce.com/s/articleView?id=sf.connected_app_create_api_integration.htm&type=5). Wenn Sie die verbundene [!DNL Salesforce]-Anwendung erstellen, geben Sie die Callback-URL im folgenden Format an:

  ```
  https://'[server]:[port]'/libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices.html
  ```

  Server und Port beziehen sich hier auf den Host-Namen bzw. die Port-Nummer des [!DNL AEM Forms]-Servers.

* Geben Sie beim Erstellen der verbundenen [!DNL Salesforce]-Anwendung `full` und `offline_access` als Werte für den OAuth-Umfang an.

* Notieren Sie sich die Werte für die Client-ID (als Consumer Key bezeichnet) und das Client-Geheimnis (als Consumer Secret bezeichnet) für die verbundene Anwendung.

Führen Sie die folgenden Schritte aus, um den [!DNL Salesforce]-Cloud-Service zu konfigurieren:

1. Navigieren Sie auf [!DNL AEM Forms] Autoreninstanz zu **[!UICONTROL Tools]** ![hammer](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Data Sources]**.
2. Wählen Sie den Ordnernamen und dann **[!UICONTROL Salesforce Cloud Config]** aus, und wählen Sie anschließend **[!UICONTROL Eigenschaften]**.
3. Auf der Registerkarte **[!UICONTROL Authentifizierungseinstellungen]**:
   1. Geben Sie die [!DNL Salesforce]-Domain-URL im Feld **[!UICONTROL Host]** an. Beispiel: [Domain-name].my.salesforce.com.
   2. Geben Sie die Client-ID (als Consumer Key bezeichnet) und das Client-Geheimnis (als Consumer Secret bezeichnet) für die verbundene Anwendung an.
   3. Geben Sie **full offline_access** (`full`- und `offine_access` -Werte, durch ein Leerzeichen getrennt) im Feld **[!UICONTROL Autorisierungsumfang]** an.
   4. Wählen Sie **[!UICONTROL Verbindung zu OAuth herstellen]**. Sie werden zur Anmeldungsseite von [!DNL Salesforce] umgeleitet.
   5. Melden Sie sich mit Ihren [!DNL Salesforce]-Anmeldeinformationen an und lassen Sie zu, dass die Cloud-Service-Konfiguration eine Verbindung zum [!DNL Salesforce]-Service herstellt. Wenn die Verbindung erfolgreich hergestellt wurde, werden Sie zur Seite „[!DNL Salesforce]-Cloud-Service-Konfiguration“ weitergeleitet, auf der eine Erfolgsmeldung angezeigt wird.
4. Wählen Sie **[!UICONTROL Speichern und schließen]**, um die Konfiguration abzuschließen.

### Zugreifen auf das vorkonfigurierte [!DNL Salesforce]-Formulardatenmodell (FDM)

Ein vorkonfiguriertes [!DNL Salesforce]-Formulardatenmodell (FDM) ist auf dem [!DNL AEM Forms]-Server verfügbar, nachdem Sie [ein Entwicklungsprojekt für Forms basierend auf einem Experience Manager-Archetyp eingerichtet haben](setup-local-development-environment.md#forms-cloud-service-local-development-environment).

So greifen Sie auf das Formulardatenmodell (FDM) zu:
1. Navigieren Sie zu **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Datenintegrationen]**.
1. Wählen Sie den Ordnernamen und dann das **[!UICONTROL Salesforce-Datenmodell]** aus, und wählen Sie anschließend das Symbol „Bearbeiten“ ![Bearbeiten](assets/edit.png), um das Formulardatenmodell (FDM) anzuzeigen.

Nach der Konfiguration des [[!DNL Salesforce] Cloud Config-Services](#configure-salesforce-cloud-service) können Sie adaptive Formulare mit dem vordefinierten [!DNL Salesforce]-Datenmodell integrieren.

>[!MORELIKETHIS]
>
>* [Konfigurieren von Datenquellen für AEM Forms](/help/forms/configure-data-sources.md)
>* [Konfigurieren von Azure Storage für AEM-Formulare](/help/forms/configure-azure-storage.md)
>  [Hinzufügen des Formularportals zu einer AEM Sites-Seite](/help/forms/configure-forms-portal.md)
