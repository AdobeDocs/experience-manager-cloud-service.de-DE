---
title: Wie integriere ich Salesforce-Integration in AEM Forms mithilfe des OAuth 2.0-Client-Anmeldedatenflusses?
seo-title: Salesforce integration with AEM Forms using OAuth 2.0 client credential flow
description: Schritte zur Integration von Salesforce mit AEM Forms mithilfe des OAuth 2.0-Client-Anmeldedatenflusses
seo-description: Steps to integrate Salesforce integration with AEM Forms using OAuth 2.0 client credential flow
Keywords: Integration of Salesforce using OAuth 2.0 client credential flow, salesforce integration with oauth2 using client credential flow, salesforce and client credential integration
source-git-commit: 2c0a816b61cfc17a83b24b28be1f317e9681c6c5
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 3%

---


# Integration der Salesforce-Anwendung mit dem OAuth 2.0-Client-Anmeldefluss {#configure-salesforce-with-ouath-2.0-client-credential}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/oauth2-client-credentials-flow-for-server-to-server-integration.html) |
| AEM as a Cloud Service | Dieser Artikel |

Sie können OAuth 2.0-Client-Anmeldeinformationen verwenden, um AEM Forms in die Salesforce-Anwendung zu integrieren. OAuth 2.0-Client-Anmeldeinformationen sind eine standardmäßige und sichere Methode für die direkte Kommunikation ohne Benutzerbeteiligung.

![Workflow beim Festlegen der Kommunikation zwischen AEM Forms und Salesforce](/help/forms/assets/salesforce-workflow.png)
AEM Forms tauscht die in der Salesforce Connect-Anwendung definierten Client-Anmeldeinformationen (Consumer Key und Consumer Secret) aus, um ein Zugriffstoken zu erhalten.

Die Verwendung von OAuth 2.0-Client-Anmeldeinformationen für die Authentifizierung über die Authentifizierung für die Flussauthentifizierung des Autorisierungscodes bietet mehrere Vorteile:

* Die Authentifizierung mit OAuth 2.0-Client-Anmeldeinformationen ermöglicht mehr als fünf Verbindungen pro Benutzer.
* AEM Datenquellenkonfiguration arbeitet weiterhin an der Deaktivierung, Zugriffsänderungen und Kennwortaktualisierung für einen AEM Benutzer.

## Voraussetzungen {#prerequisites}

Bevor Sie die Kommunikation zwischen einer Salesforce-Anwendung und einer AEM Umgebung einrichten:

* Erstellen Sie eine [Salesforce-verbundene App mit OAuth 2.0-Client-Anmeldefluss](https://help.salesforce.com/s/articleView?id=sf.connected_app_client_credentials_setup.htm&amp;type=5) und einen reinen API-Benutzer für Ihr Unternehmen erstellen und das Consumer-Schlüssel- und das Consumer-Geheimnis für die App abrufen.

* Stellen Sie sicher, dass Ihre Swagger-Datei entsprechend den APIs Ihres Unternehmens konfiguriert ist. Alternativ können Sie auch [Swagger-Datei erstellen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/forms/integrate-with-salesforce/describe-rest-api.html) von Grund auf neu, auf die Nutzung in Ihrer AEM-Umgebung zugeschnitten.


## Salesforce-Anwendung mithilfe des OAuth 2.0 Client Credential-Flusses konfigurieren {#steps-to-create-aem-datasource-configuration}

Führen Sie die folgenden Schritte aus, um die Salesforce-Anwendung mit den Authentifizierungseinstellungen für Client-Anmeldedaten von OAuth 2.0 in ein adaptives Formular zu integrieren:

1. Melden Sie sich bei Ihrer -Autoreninstanz an.
1. Navigieren Sie zu **[!UICONTROL Instrumente]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Data Sources]**.
1. Wählen Sie den Konfigurationsordner aus.
1. Klicks **[!UICONTROL Erstellen]** und **[!UICONTROL Erstellen der Datenquellenkonfiguration]** angezeigt.
1. Geben Sie die **[!UICONTROL Titel]** und wählen Sie die **[!UICONTROL Diensttyp]** as **[!UICONTROL RESTful-Dienst]**.
1. Klicken Sie auf **[!UICONTROL Weiter]**.
1. Wählen Sie die **[!UICONTROL Swagger Source]** as **[!UICONTROL Datei].**

   >[!NOTE]
   >
   > Wenn die Swagger-Datei ausgewählt ist, werden das Schema, der Hostname und der Basispfad automatisch ausgefüllt.

1. Laden Sie die erstellte Swagger-Datei von Ihrem lokalen Computer hoch, indem Sie auf **[!UICONTROL Durchsuchen]**.
1. Wählen Sie die **[!UICONTROL Authentifizierungstyp]** as **[!UICONTROL OAuth 2.0]** und **[!UICONTROL Authentifizierungseinstellungen]** angezeigt.
1. Wählen Sie die **[!UICONTROL Fördertyp]** as **[!UICONTROL Client Credential]**.
1. Geben Sie die **[!UICONTROL Client-ID]** und **[!UICONTROL Client Secret]** von der Salesforce Connect-App abgerufen.
1. Geben Sie die **[!UICONTROL Zugriffstoken-URL]** im Format
   `https://[MyDomainName].my.salesforce.com/services/oauth2/token`.

   >[!NOTE]
   >
   > Jede Organisation hat einen eigenen spezifischen Domänennamen.

1. Klicks **[!UICONTROL Verbindung testen]**.
1. Wenn die Verbindung erfolgreich hergestellt wurde, klicken Sie auf die Schaltfläche **[!UICONTROL Erstellen]** Schaltfläche.

Jetzt können Sie [Formulardatenmodell erstellen](/help/forms/create-form-data-models.md) , um die konfigurierte Datenquelle in Ihr adaptives Formular zu integrieren.
