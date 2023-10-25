---
title: Wie integrieren Sie Salesforce mithilfe des OAuth 2.0-Client-Anmeldedatenflusses in AEM Forms?
description: Erfahren Sie, wie Sie Salesforce mit AEM Forms mithilfe des OAuth 2.0-Client-Anmeldedatenflusses integrieren können.
Keywords: Integration of Salesforce using OAuth 2.0 client credential flow, salesforce integration with oauth2 using client credential flow, salesforce and client credential integration
exl-id: 2c2029ab-6fb4-41a6-846c-175c3a79d921
source-git-commit: f70e18b1c21fd530587694f91c3969e831cfc640
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 33%

---

# Verbinden des adaptiven Formulars mit Salesforce mithilfe des OAuth 2.0-Client-Anmeldedatenflusses {#configure-salesforce-with-ouath-2.0-client-credential}

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

* Stellen Sie sicher, dass Ihre Swagger-Datei entsprechend den APIs Ihres Unternehmens konfiguriert ist. Alternativ können Sie auch [Swagger-Datei erstellen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/forms/integrate-with-salesforce/describe-rest-api.html?lang=de) von Grund auf neu, auf die Nutzung in Ihrer AEM-Umgebung zugeschnitten.


## Salesforce-Anwendung mithilfe des OAuth 2.0 Client Credential-Flusses konfigurieren {#steps-to-create-aem-datasource-configuration}

So verbinden Sie das adaptive Formular mit der Salesforce-Anwendung mithilfe der Authentifizierungseinstellungen für Client-Anmeldedaten von OAuth 2.0:

1. Melden Sie sich bei Ihrer Authoring-Instanz an.
1. Wechseln Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Datenquellen]**.
1. Wählen Sie den Konfigurationsordner aus.
1. Klicken Sie auf **[!UICONTROL Erstellen]** und das Bedienfeld **[!UICONTROL Datenquellenkonfiguration erstellen]** erscheint.
1. Geben Sie den **[!UICONTROL Titel]** an und wählen Sie den **[!UICONTROL Diensttyp]** als **[!UICONTROL RESTful-Dienst]**.
1. Klicken Sie auf **[!UICONTROL Weiter]**.
1. Wählen Sie **[!UICONTROL Swagger Source]** als **[!UICONTROL Datei].**

   >[!NOTE]
   >
   > Wenn die Swagger-Datei ausgewählt ist, werden das Schema, der Hostname und der Basispfad automatisch ausgefüllt.

1. Laden Sie die erstellte Swagger-Datei von Ihrem lokalen Computer hoch, indem Sie auf **[!UICONTROL Durchsuchen]** klicken.
1. Wählen Sie **[!UICONTROL Authentifizierungstyp]** als **[!UICONTROL OAuth 2.0]** und das Bedienfeld **[!UICONTROL Authentifizierungs-Einstellungen]** erscheint.
1. Wählen Sie die **[!UICONTROL Fördertyp]** as **[!UICONTROL Client Credential]**.
1. Geben Sie die **[!UICONTROL Client-ID]** und das **[!UICONTROL Client-Geheimnis]** an, das Sie von der mit Salesforce verbundenen App erhalten haben.
1. Geben Sie die **[!UICONTROL Zugriffstoken-URL]** im folgenden Format an:
   `https://[MyDomainName].my.salesforce.com/services/oauth2/token`.

   >[!NOTE]
   >
   > Jede Organisation hat einen eigenen, spezifischen Domain-Namen.

1. Klicken Sie auf **[!UICONTROL Verbindung testen]**.
1. Wenn die Verbindung erfolgreich hergestellt wurde, klicken Sie auf die Schaltfläche **[!UICONTROL Erstellen]**.

Jetzt können Sie [Formulardatenmodell erstellen](/help/forms/create-form-data-models.md) , um das adaptive Formular an die Salesforce-Anwendung zu senden.


